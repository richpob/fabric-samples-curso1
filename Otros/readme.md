# Imagenes del proyecto y logs del contrato
## Docker 

![image](https://github.com/user-attachments/assets/0a408048-85bc-402c-ad14-475a2432ceb6)

## Contrato

![image](https://github.com/user-attachments/assets/e15b7af2-85b5-42bb-a2c7-a09613f4d5e1)

## Objetos de CouchDB

![image](https://github.com/user-attachments/assets/9464b16a-17ed-4b8e-b8ce-ddcf82bfa854)


## CouchDB desplegando contrato y primer registro 

![image](https://github.com/user-attachments/assets/2f0f362b-1943-43b9-a4ea-323741bc3226)



## Resultado de proceso de compilacion, deploy y consulta de contrato
```javascript
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ cd chaincodes/
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7/chaincodes$ go mod tidy
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7/chaincodes$ GO111MODULE=on go mod vendor
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7/chaincodes$ go build
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7/chaincodes$ cd ..
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ peer lifecycle chaincode package tollchaincode.tar.gz --path chaincodes
/ --lang golang --label toll2.0 
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ peer lifecycle chaincode install tollchaincode.tar.gz 
2024-07-15 17:02:06.918 -04 [cli.lifecycle.chaincode] submitInstallProposal -> INFO 001 Installed remotely: response:<status:200 payload:"\nHtoll2.0:5a333a60ba99e11d3ae6aa5dd9dc8e665485a1deb20a3bb0876a7f50f1678b3b\022\007toll2.0" > 
2024-07-15 17:02:06.918 -04 [cli.lifecycle.chaincode] submitInstallProposal -> INFO 002 Chaincode code package identifier: toll2.0:5a333a60ba99e11d3ae6aa5dd9dc8e665485a1deb20a3bb0876a7f50f1678b3b
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ export FABRIC_CFG_PATH=${PWD}/../config
  export CORE_PEER_TLS_ENABLED=true
  export PEER0_MOP_CA=${PWD}/organizations/peerOrganizations/mop.autopistasmop.com/peers/peer0.mop.autopistasmop.com/tls/ca.crt
  export CORE_PEER_LOCALMSPID="MopMSP"
  export CORE_PEER_TLS_ROOTCERT_FILE=$PEER0_MOP_CA
  export CORE_PEER_MSPCONFIGPATH=${PWD}/organizations/peerOrganizations/mop.autopistasmop.com/users/Admin@mop.autopistasmop.com/msp
  export CORE_PEER_ADDRESS=localhost:7051
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ peer lifecycle chaincode install tollchaincode.tar.gz 
2024-07-15 17:03:03.198 -04 [cli.lifecycle.chaincode] submitInstallProposal -> INFO 001 Installed remotely: response:<status:200 payload:"\nHtoll2.0:5a333a60ba99e11d3ae6aa5dd9dc8e665485a1deb20a3bb0876a7f50f1678b3b\022\007toll2.0" > 
2024-07-15 17:03:03.198 -04 [cli.lifecycle.chaincode] submitInstallProposal -> INFO 002 Chaincode code package identifier: toll2.0:5a333a60ba99e11d3ae6aa5dd9dc8e665485a1deb20a3bb0876a7f50f1678b3b
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ peer list channel
Error: unknown command "list" for "peer"
Run 'peer --help' for usage.
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ export CC_PACKAGE_ID=toll2.0:5a333a60ba99e11d3ae6aa5dd9dc8e665485a1deb20a3bb0876a7f50f1678b3b
peer lifecycle chaincode approveformyorg -o localhost:7050 --ordererTLSHostnameOverride orderer.autopistasmop.com --channelID autopistachannel --signature-policy "OR('MopMSP.member','Ruta78MSP.member')" --name tollchaincode --version 2.0 --package-id $CC_PACKAGE_ID --sequence 1 --tls --cafile ${PWD}/organizations/ordererOrganizations/autopistasmop.com/orderers/orderer.autopistasmop.com/msp/tlscacerts/tlsca.autopistasmop.com-cert.pem
Error: proposal failed with status: 500 - channel 'autopistachannel' not found
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ peer lifecycle chaincode approveformyorg -o localhost:7050 --ordererTLSHostnameOverride orderer.autopistasmop.com --channelID autopistaschannel --signature-policy "OR('MopMSP.member','Ruta78MSP.member')" --name tollchaincode -
-version 2.0 --package-id $CC_PACKAGE_ID --sequence 1 --tls --cafile ${PWD}/organizations/ordererOrganizations/autopistasmop.com/orderers/orderer.autopist
asmop.com/msp/tlscacerts/tlsca.autopistasmop.com-cert.pem
2024-07-15 17:22:34.796 -04 [chaincodeCmd] ClientWait -> INFO 001 txid [5834bacdb96a243c4757cb0f5635cb6a3deb6167419721214f39f6e662c3f991] committed with status (VALID) at localhost:7051
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ ^[[200~export CORE_PEER_LOCALMSPID="MopMSP"
t CORE_PEER_TLS_ROOTCERT_FILE=$PEER0_MOP_CA
  export CORE_PEER_MSPCONFIGPATH=${PWD}/organizations/peerOrganizations/mop.autopistasmop.com/users/Admin@mop.autopistasmop.com/msp
  export CORE_PEER_ADDRESS=localhost:7051
peer lifecycle chaincode approveformyorg -o localhost:7050 --ordererTLSHostnameOverride orderer.autopistasmop.com --channelID autopistaschannel --signature-policy "OR('MopMSP.member','Ruta78MSP.member')" --name testt --version 1.0 --package-id $CC_PACKAGE_ID --sequence 1 --tls --cafile ${PWD}/organizations/ordererOrganizations/autopistasmop.com/orderers/orderer.autopistasmop.com/msp/tlscacerts/tlsca.autopistasmop.com-cert.pem
^[[201~export: command not found
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$   export CORE_PEER_TLS_ROOTCERT_FILE=$PEER0_MOP_CA
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$   export CORE_PEER_MSPCONFIGPATH=${PWD}/organizations/peerOrganizations/mop.autopistasmop.com/users/Admin@mop.autopistasmop.com/msp
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$   export CORE_PEER_ADDRESS=localhost:7051
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ peer lifecycle chaincode approveformyorg -o localhost:7050 --ordererTLSHostnameOverride orderer.autopistasmop.com --channelID autopistaschannel --signature-policy "OR('MopMSP.member','Ruta78MSP.member')" --name testt --version 1.0 --package-id $CC_PACKAGE_ID --sequence 1 --tls --cafile ${PWD}/organizations/ordererOrganizations/autopistasmop.com/orderers/orderer.autopistasmop.com/msp/tlscacerts/tlsca.autopistasmop.com-cert.pem
2024-07-15 17:25:46.665 -04 [chaincodeCmd] ClientWait -> INFO 001 txid [91a1f06012c2e6c7740c45376f2a9a709752d2691552d04e3c9da57817d1f2d7] committed with status (VALID) at localhost:7051
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ ^[[200~peer lifecycle chaincode checkcommitreadiness --channelID autopistaschannel --name testt --version 1.0 --sequence 1 --tls --cafile ${PWD}/organizations/ordererOrganizations/autopistasmop.com/orderers/orderer.autopistasmop.com/msp/tlscacerts/tlsca.autopistasmop.com-cert.pem --output json
^[[201~peer: command not found
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ peer lifecycle chaincode checkcommitreadiness --channelID autopistaschan
nel --name testt --version 1.0 --sequence 1 --tls --cafile ${PWD}/organizations/ordererOrganizations/autopistasmop.com/orderers/orderer.autopistasmop.com/
msp/tlscacerts/tlsca.autopistasmop.com-cert.pem --output json
{
        "approvals": {
                "MopMSP": false,
                "Ruta78MSP": false
        }
}
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ export CORE_PEER_LOCALMSPID="MopMSP"
  export CORE_PEER_TLS_ROOTCERT_FILE=$PEER0_MOP_CA
  export CORE_PEER_MSPCONFIGPATH=${PWD}/organizations/peerOrganizations/mop.autopistasmop.com/users/Admin@mop.autopistasmop.com/msp
  export CORE_PEER_ADDRESS=localhost:7051
peer lifecycle chaincode approveformyorg -o localhost:7050 --ordererTLSHostnameOverride orderer.autopistasmop.com --channelID autopistaschannel --signature-policy "OR('MopMSP.member','Ruta78MSP.member')" --name tollchaincode --version 1.0 --package-id $CC_PACKAGE_ID --sequence 1 --tls --cafile ${PWD}/organizations/ordererOrganizations/autopistasmop.com/orderers/orderer.autopistasmop.com/msp/tlscacerts/tlsca.autopistasmop.com-cert.pem
2024-07-15 17:40:00.131 -04 [chaincodeCmd] ClientWait -> INFO 001 txid [540b228de27160f6a8e2e37e907a3a919850f9debe77497cac440d58d69d1285] committed with status (VALID) at localhost:7051
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ peer lifecycle chaincode checkcommitreadiness --channelID autopistaschannel --name tollchaincode --version 1.0 --sequence 1 --tls --cafile ${PWD}/organizations/ordererOrganizations/autopistasmop.com/orderers/orderer.autopistasmop.com/msp/tlscacerts/tlsca.autopistasmop.com-cert.pem --output json
{
        "approvals": {
                "MopMSP": false,
                "Ruta78MSP": false
        }
}

ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ export CORE_PEER_LOCALMSPID="Ruta78MSP"
  export CORE_PEER_TLS_ROOTCERT_FILE=$PEER0_RUTA78_CA
  export CORE_PEER_MSPCONFIGPATH=${PWD}/organizations/peerOrganizations/ruta78.autopistasmop.com/users/Admin@ruta78.autopistasmop.com/msp
  export CORE_PEER_ADDRESS=localhost:9051

peer lifecycle chaincode approveformyorg -o localhost:7050 --ordererTLSHostnameOverride orderer.autopistasmop.com --channelID autopistaschannel --signature-policy "OR('MopMSP.member','Ruta78MSP.member')" --name tollchaincode --version 1.0 --package-id $CC_PACKAGE_ID --sequence 1 --tls --cafile ${PWD}/organizations/ordererOrganizations/autopistasmop.com/orderers/orderer.autopistasmop.com/msp/tlscacerts/tlsca.autopistasmop.com-cert.pem
2024-07-15 17:41:24.465 -04 [chaincodeCmd] ClientWait -> INFO 001 txid [b04fecd72b7123808dd1aa92362529dcb517657ffef7c31bebfe5c575a6d1b04] committed with status (VALID) at localhost:9051
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ peer lifecycle chaincode checkcommitreadiness --channelID autopistaschannel --name tollchaincode --version 1.0 --sequence 1 --tls --cafile ${PWD}/organizations/ordererOrganizations/autopistasmop.com/orderers/orderer.autopistasmop.com/msp/tlscacerts/tlsca.autopistasmop.com-cert.pem --output json
{
        "approvals": {
                "MopMSP": false,
                "Ruta78MSP": false
        }
}
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ peer lifecycle chaincode commit -o localhost:7050 --ordererTLSHostnameOverride orderer.autopistasmop.com --signature-policy "OR('MopMSP.member','Ruta78MSP.member')" --channelID autopistaschannel --name tollchaincode --version 1.0 --sequence 1 --tls --cafile ${PWD}/organizations/ordererOrganizations/autopistasmop.com/orderers/orderer.autopistasmop.com/msp/tlscacerts/tlsca.autopistasmop.com-cert.pem --peerAddresses localhost:7051 --tlsRootCertFiles ${PWD}/organizations/peerOrganizations/mop.autopistasmop.com/peers/peer0.mop.autopistasmop.com/tls/ca.crt --peerAddresses localhost:9051 --tlsRootCertFiles ${PWD}/organizations/peerOrganizations/ruta78.autopistasmop.com/peers/peer0.ruta78.autopistasmop.com/tls/ca.crt
2024-07-15 17:41:54.640 -04 [chaincodeCmd] ClientWait -> INFO 001 txid [a73eda7dca546b77da358ce67f53a869d45616df4909e0bf18bce06718887796] committed with status (VALID) at localhost:7051
2024-07-15 17:41:54.650 -04 [chaincodeCmd] ClientWait -> INFO 002 txid [a73eda7dca546b77da358ce67f53a869d45616df4909e0bf18bce06718887796] committed with status (VALID) at localhost:9051
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ peer lifecycle chaincode querycommitted --channelID autopistaschannel --name tollchaincode --cafile ${PWD}/organizations/ordererOrganizations/autopistasmop.com/orderers/orderer.autopistasmop.com/msp/tlscacerts/tlsca.autopistasmop.com-cert.pem
Committed chaincode definition for chaincode 'tollchaincode' on channel 'autopistaschannel':
Version: 1.0, Sequence: 1, Endorsement Plugin: escc, Validation Plugin: vscc, Approvals: [MopMSP: true, Ruta78MSP: true]

ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ peer chaincode query -C autopistaschannel -n tollchaincode -c '{"function":"QueryTollRecord","Args":["0xc83273f025ecEd0317f52DfE26d95C4638a10D7E"]}'
{"num_contrato_cliente":"0xc83273f025ecEd0317f52DfE26d95C4638a10D7E","placa_matricula":"HSGT62","fecha_hora_tx":"Tue Jul  9 18:21:58 -04 2024","num_portico":"P004","precio_clp":540}
ubuntu@ubuntu:~/Documents/GitHub/hyperledger-fabric/fabric-samples/autopistas_g7$ 
```javascript
