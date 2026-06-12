---
title: "interpreting nmap output"
date: 2009-05-19
forum: Security
---

### Post by pytheas22 on 2009-05-19
I have a web server running on Ubuntu server edition, installed on a KVM virtual machine using bridged networking (i.e., the virtual machine has its own IP address directly on my network; there's no NAT).  I scanned the server with nmap, and it found the following ports open:

```

Starting Nmap 4.76 ( http://nmap.org ) at 2009-05-19 11:50 EDT
Initiating Ping Scan at 11:50
Scanning <IP address obfuscated> [2 ports]
Completed Ping Scan at 11:50, 0.05s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 11:50
Completed Parallel DNS resolution of 1 host. at 11:50, 12.03s elapsed
Initiating SYN Stealth Scan at 11:50
Scanning <IP address obfuscated> [1000 ports]
Discovered open port 443/tcp on <IP address obfuscated>
Discovered open port 80/tcp on <IP address obfuscated>
Discovered open port 10001/tcp on <IP address obfuscated>
Discovered open port 10000/tcp on <IP address obfuscated>
Discovered open port 1244/tcp on <IP address obfuscated>
Discovered open port 5800/tcp on <IP address obfuscated>
Discovered open port 84/tcp on <IP address obfuscated>
Discovered open port 1011/tcp on <IP address obfuscated>
Discovered open port 5004/tcp on <IP address obfuscated>
Discovered open port 4003/tcp on <IP address obfuscated>
Discovered open port 3986/tcp on <IP address obfuscated>
Discovered open port 1093/tcp on <IP address obfuscated>
Discovered open port 10025/tcp on <IP address obfuscated>
Discovered open port 2800/tcp on <IP address obfuscated>
Discovered open port 8180/tcp on <IP address obfuscated>
Discovered open port 17988/tcp on <IP address obfuscated>
Discovered open port 10616/tcp on <IP address obfuscated>
Discovered open port 8081/tcp on <IP address obfuscated>
Discovered open port 417/tcp on <IP address obfuscated>
Discovered open port 3809/tcp on <IP address obfuscated>
Discovered open port 7000/tcp on <IP address obfuscated>
Discovered open port 3920/tcp on <IP address obfuscated>
Discovered open port 1130/tcp on <IP address obfuscated>
Discovered open port 14442/tcp on <IP address obfuscated>
Discovered open port 1094/tcp on <IP address obfuscated>
Discovered open port 7625/tcp on <IP address obfuscated>
Discovered open port 259/tcp on <IP address obfuscated>
Discovered open port 82/tcp on <IP address obfuscated>
Discovered open port 8011/tcp on <IP address obfuscated>
Discovered open port 55055/tcp on <IP address obfuscated>
Discovered open port 1026/tcp on <IP address obfuscated>
Discovered open port 7676/tcp on <IP address obfuscated>
Discovered open port 32783/tcp on <IP address obfuscated>
Discovered open port 1839/tcp on <IP address obfuscated>
Discovered open port 4242/tcp on <IP address obfuscated>
Discovered open port 90/tcp on <IP address obfuscated>
Discovered open port 1107/tcp on <IP address obfuscated>
Discovered open port 3814/tcp on <IP address obfuscated>
Discovered open port 1720/tcp on <IP address obfuscated>
Discovered open port 1494/tcp on <IP address obfuscated>
Discovered open port 7920/tcp on <IP address obfuscated>
Discovered open port 6839/tcp on <IP address obfuscated>
Discovered open port 1087/tcp on <IP address obfuscated>
Discovered open port 8192/tcp on <IP address obfuscated>
Discovered open port 3017/tcp on <IP address obfuscated>
Discovered open port 1110/tcp on <IP address obfuscated>
Discovered open port 1309/tcp on <IP address obfuscated>
Discovered open port 514/tcp on <IP address obfuscated>
Discovered open port 1782/tcp on <IP address obfuscated>
Discovered open port 40193/tcp on <IP address obfuscated>
Discovered open port 2106/tcp on <IP address obfuscated>
Discovered open port 8651/tcp on <IP address obfuscated>
Discovered open port 5666/tcp on <IP address obfuscated>
Discovered open port 49165/tcp on <IP address obfuscated>
Discovered open port 7800/tcp on <IP address obfuscated>
Discovered open port 1658/tcp on <IP address obfuscated>
Discovered open port 1761/tcp on <IP address obfuscated>
Discovered open port 19/tcp on <IP address obfuscated>
Discovered open port 5962/tcp on <IP address obfuscated>
Discovered open port 3800/tcp on <IP address obfuscated>
Discovered open port 161/tcp on <IP address obfuscated>
Discovered open port 9003/tcp on <IP address obfuscated>
Discovered open port 7001/tcp on <IP address obfuscated>
Discovered open port 1148/tcp on <IP address obfuscated>
Discovered open port 5550/tcp on <IP address obfuscated>
Discovered open port 33/tcp on <IP address obfuscated>
Discovered open port 1065/tcp on <IP address obfuscated>
Discovered open port 911/tcp on <IP address obfuscated>
Discovered open port 407/tcp on <IP address obfuscated>
Discovered open port 1433/tcp on <IP address obfuscated>
Discovered open port 88/tcp on <IP address obfuscated>
Discovered open port 1187/tcp on <IP address obfuscated>
Discovered open port 1051/tcp on <IP address obfuscated>
Discovered open port 18040/tcp on <IP address obfuscated>
Discovered open port 668/tcp on <IP address obfuscated>
Discovered open port 8649/tcp on <IP address obfuscated>
Discovered open port 8082/tcp on <IP address obfuscated>
Discovered open port 4002/tcp on <IP address obfuscated>
Discovered open port 49159/tcp on <IP address obfuscated>
Discovered open port 43/tcp on <IP address obfuscated>
Discovered open port 3325/tcp on <IP address obfuscated>
Discovered open port 544/tcp on <IP address obfuscated>
Discovered open port 5002/tcp on <IP address obfuscated>
Discovered open port 60443/tcp on <IP address obfuscated>
Discovered open port 30951/tcp on <IP address obfuscated>
Discovered open port 1840/tcp on <IP address obfuscated>
Discovered open port 1068/tcp on <IP address obfuscated>
Discovered open port 1/tcp on <IP address obfuscated>
Discovered open port 1022/tcp on <IP address obfuscated>
Discovered open port 7004/tcp on <IP address obfuscated>
Discovered open port 2006/tcp on <IP address obfuscated>
Discovered open port 3737/tcp on <IP address obfuscated>
Discovered open port 1086/tcp on <IP address obfuscated>
Discovered open port 1048/tcp on <IP address obfuscated>
Discovered open port 406/tcp on <IP address obfuscated>
Discovered open port 993/tcp on <IP address obfuscated>
Discovered open port 8009/tcp on <IP address obfuscated>
Discovered open port 6003/tcp on <IP address obfuscated>
Discovered open port 425/tcp on <IP address obfuscated>
Discovered open port 8083/tcp on <IP address obfuscated>
Discovered open port 70/tcp on <IP address obfuscated>
Discovered open port 8652/tcp on <IP address obfuscated>
Discovered open port 8045/tcp on <IP address obfuscated>
Discovered open port 8087/tcp on <IP address obfuscated>
Discovered open port 2105/tcp on <IP address obfuscated>
Discovered open port 8090/tcp on <IP address obfuscated>
Discovered open port 8093/tcp on <IP address obfuscated>
Discovered open port 8600/tcp on <IP address obfuscated>
Discovered open port 9080/tcp on <IP address obfuscated>
Discovered open port 8888/tcp on <IP address obfuscated>
Discovered open port 4000/tcp on <IP address obfuscated>
Discovered open port 389/tcp on <IP address obfuscated>
Discovered open port 636/tcp on <IP address obfuscated>
Discovered open port 1723/tcp on <IP address obfuscated>
Discovered open port 21/tcp on <IP address obfuscated>
Discovered open port 113/tcp on <IP address obfuscated>
Discovered open port 22/tcp on <IP address obfuscated>
Discovered open port 554/tcp on <IP address obfuscated>
Discovered open port 8084/tcp on <IP address obfuscated>
Discovered open port 8007/tcp on <IP address obfuscated>
Discovered open port 1271/tcp on <IP address obfuscated>
Discovered open port 1063/tcp on <IP address obfuscated>
Discovered open port 1812/tcp on <IP address obfuscated>
Discovered open port 5222/tcp on <IP address obfuscated>
Discovered open port 2121/tcp on <IP address obfuscated>
Discovered open port 5414/tcp on <IP address obfuscated>
Discovered open port 9010/tcp on <IP address obfuscated>
Discovered open port 1311/tcp on <IP address obfuscated>
Discovered open port 1095/tcp on <IP address obfuscated>
Discovered open port 2170/tcp on <IP address obfuscated>
Discovered open port 8021/tcp on <IP address obfuscated>
Discovered open port 2033/tcp on <IP address obfuscated>
Discovered open port 8291/tcp on <IP address obfuscated>
Discovered open port 1028/tcp on <IP address obfuscated>
Discovered open port 1503/tcp on <IP address obfuscated>
Discovered open port 311/tcp on <IP address obfuscated>
Discovered open port 4111/tcp on <IP address obfuscated>
Discovered open port 7201/tcp on <IP address obfuscated>
Discovered open port 2179/tcp on <IP address obfuscated>
Discovered open port 900/tcp on <IP address obfuscated>
Discovered open port 42/tcp on <IP address obfuscated>
Discovered open port 1124/tcp on <IP address obfuscated>
Discovered open port 2608/tcp on <IP address obfuscated>
Discovered open port 1080/tcp on <IP address obfuscated>
Discovered open port 1102/tcp on <IP address obfuscated>
Discovered open port 1131/tcp on <IP address obfuscated>
Discovered open port 15660/tcp on <IP address obfuscated>
Discovered open port 3323/tcp on <IP address obfuscated>
Discovered open port 2605/tcp on <IP address obfuscated>
Discovered open port 1070/tcp on <IP address obfuscated>
Discovered open port 801/tcp on <IP address obfuscated>
Discovered open port 5555/tcp on <IP address obfuscated>
Discovered open port 1033/tcp on <IP address obfuscated>
Discovered open port 23502/tcp on <IP address obfuscated>
Discovered open port 1805/tcp on <IP address obfuscated>
Discovered open port 902/tcp on <IP address obfuscated>
Discovered open port 3371/tcp on <IP address obfuscated>
Discovered open port 24800/tcp on <IP address obfuscated>
Discovered open port 1059/tcp on <IP address obfuscated>
Discovered open port 10243/tcp on <IP address obfuscated>
Discovered open port 3001/tcp on <IP address obfuscated>
Discovered open port 3689/tcp on <IP address obfuscated>
Discovered open port 6100/tcp on <IP address obfuscated>
Discovered open port 8000/tcp on <IP address obfuscated>
Discovered open port 7921/tcp on <IP address obfuscated>
Discovered open port 27715/tcp on <IP address obfuscated>
Discovered open port 1666/tcp on <IP address obfuscated>
Discovered open port 89/tcp on <IP address obfuscated>
Discovered open port 65000/tcp on <IP address obfuscated>
Discovered open port 7627/tcp on <IP address obfuscated>
Discovered open port 1061/tcp on <IP address obfuscated>
Discovered open port 5679/tcp on <IP address obfuscated>
Discovered open port 38292/tcp on <IP address obfuscated>
Discovered open port 3827/tcp on <IP address obfuscated>
Discovered open port 3370/tcp on <IP address obfuscated>
Discovered open port 1058/tcp on <IP address obfuscated>
Discovered open port 6/tcp on <IP address obfuscated>
Discovered open port 2604/tcp on <IP address obfuscated>
Discovered open port 1036/tcp on <IP address obfuscated>
Discovered open port 56737/tcp on <IP address obfuscated>
Discovered open port 99/tcp on <IP address obfuscated>
Discovered open port 990/tcp on <IP address obfuscated>
Discovered open port 2009/tcp on <IP address obfuscated>
Discovered open port 3011/tcp on <IP address obfuscated>
Discovered open port 49152/tcp on <IP address obfuscated>
Discovered open port 3000/tcp on <IP address obfuscated>
Discovered open port 9050/tcp on <IP address obfuscated>
Discovered open port 3013/tcp on <IP address obfuscated>
Discovered open port 340/tcp on <IP address obfuscated>
Discovered open port 34571/tcp on <IP address obfuscated>
Discovered open port 10778/tcp on <IP address obfuscated>
Discovered open port 1974/tcp on <IP address obfuscated>
Discovered open port 1046/tcp on <IP address obfuscated>
Discovered open port 808/tcp on <IP address obfuscated>
Discovered open port 8333/tcp on <IP address obfuscated>
Discovered open port 2068/tcp on <IP address obfuscated>
Discovered open port 888/tcp on <IP address obfuscated>
Discovered open port 49176/tcp on <IP address obfuscated>
Discovered open port 1783/tcp on <IP address obfuscated>
Discovered open port 548/tcp on <IP address obfuscated>
Discovered open port 32779/tcp on <IP address obfuscated>
Discovered open port 6580/tcp on <IP address obfuscated>
Discovered open port 9618/tcp on <IP address obfuscated>
Discovered open port 3880/tcp on <IP address obfuscated>
Discovered open port 11111/tcp on <IP address obfuscated>
Discovered open port 5000/tcp on <IP address obfuscated>
Discovered open port 2045/tcp on <IP address obfuscated>
Discovered open port 1594/tcp on <IP address obfuscated>
Discovered open port 1069/tcp on <IP address obfuscated>
Discovered open port 6007/tcp on <IP address obfuscated>
Discovered open port 1088/tcp on <IP address obfuscated>
Discovered open port 11110/tcp on <IP address obfuscated>
Discovered open port 3268/tcp on <IP address obfuscated>
Discovered open port 6059/tcp on <IP address obfuscated>
Discovered open port 481/tcp on <IP address obfuscated>
Discovered open port 5961/tcp on <IP address obfuscated>
Discovered open port 5850/tcp on <IP address obfuscated>
Discovered open port 7402/tcp on <IP address obfuscated>
Discovered open port 144/tcp on <IP address obfuscated>
Discovered open port 8654/tcp on <IP address obfuscated>
Discovered open port 19101/tcp on <IP address obfuscated>
Discovered open port 3260/tcp on <IP address obfuscated>
Discovered open port 2046/tcp on <IP address obfuscated>
Discovered open port 515/tcp on <IP address obfuscated>
Discovered open port 9968/tcp on <IP address obfuscated>
Discovered open port 3211/tcp on <IP address obfuscated>
Discovered open port 1145/tcp on <IP address obfuscated>
Discovered open port 55056/tcp on <IP address obfuscated>
Discovered open port 16018/tcp on <IP address obfuscated>
Discovered open port 1149/tcp on <IP address obfuscated>
Discovered open port 143/tcp on <IP address obfuscated>
Discovered open port 21571/tcp on <IP address obfuscated>
Discovered open port 1001/tcp on <IP address obfuscated>
Discovered open port 19780/tcp on <IP address obfuscated>
Discovered open port 28201/tcp on <IP address obfuscated>
Discovered open port 1119/tcp on <IP address obfuscated>
Discovered open port 1089/tcp on <IP address obfuscated>
Discovered open port 427/tcp on <IP address obfuscated>
Discovered open port 52822/tcp on <IP address obfuscated>
Discovered open port 6000/tcp on <IP address obfuscated>
Discovered open port 1064/tcp on <IP address obfuscated>
Discovered open port 6123/tcp on <IP address obfuscated>
Discovered open port 1066/tcp on <IP address obfuscated>
Discovered open port 3300/tcp on <IP address obfuscated>
Discovered open port 5051/tcp on <IP address obfuscated>
Discovered open port 10002/tcp on <IP address obfuscated>
Discovered open port 2042/tcp on <IP address obfuscated>
Discovered open port 5718/tcp on <IP address obfuscated>
Discovered open port 135/tcp on <IP address obfuscated>
Discovered open port 1035/tcp on <IP address obfuscated>
Discovered open port 15004/tcp on <IP address obfuscated>
Discovered open port 2049/tcp on <IP address obfuscated>
Discovered open port 9898/tcp on <IP address obfuscated>
Discovered open port 2525/tcp on <IP address obfuscated>
Discovered open port 306/tcp on <IP address obfuscated>
Discovered open port 14441/tcp on <IP address obfuscated>
Discovered open port 1287/tcp on <IP address obfuscated>
Discovered open port 44442/tcp on <IP address obfuscated>
Discovered open port 6668/tcp on <IP address obfuscated>
Discovered open port 700/tcp on <IP address obfuscated>
Discovered open port 5050/tcp on <IP address obfuscated>
Discovered open port 2717/tcp on <IP address obfuscated>
Discovered open port 1072/tcp on <IP address obfuscated>
Discovered open port 3914/tcp on <IP address obfuscated>
Discovered open port 5544/tcp on <IP address obfuscated>
Discovered open port 7/tcp on <IP address obfuscated>
Discovered open port 44501/tcp on <IP address obfuscated>
Discovered open port 2323/tcp on <IP address obfuscated>
Discovered open port 3351/tcp on <IP address obfuscated>
Discovered open port 2702/tcp on <IP address obfuscated>
Discovered open port 3052/tcp on <IP address obfuscated>
Discovered open port 648/tcp on <IP address obfuscated>
Discovered open port 3261/tcp on <IP address obfuscated>
Discovered open port 9071/tcp on <IP address obfuscated>
Discovered open port 1900/tcp on <IP address obfuscated>
Discovered open port 5952/tcp on <IP address obfuscated>
Discovered open port 555/tcp on <IP address obfuscated>
Discovered open port 5911/tcp on <IP address obfuscated>
Discovered open port 1050/tcp on <IP address obfuscated>
Discovered open port 2381/tcp on <IP address obfuscated>
Discovered open port 464/tcp on <IP address obfuscated>
Discovered open port 1049/tcp on <IP address obfuscated>
Discovered open port 3030/tcp on <IP address obfuscated>
Discovered open port 5280/tcp on <IP address obfuscated>
Discovered open port 1721/tcp on <IP address obfuscated>
Discovered open port 783/tcp on <IP address obfuscated>
Discovered open port 9917/tcp on <IP address obfuscated>
Discovered open port 3527/tcp on <IP address obfuscated>
Discovered open port 2065/tcp on <IP address obfuscated>
Discovered open port 687/tcp on <IP address obfuscated>
Discovered open port 1935/tcp on <IP address obfuscated>
Discovered open port 5298/tcp on <IP address obfuscated>
Discovered open port 5904/tcp on <IP address obfuscated>
Discovered open port 1301/tcp on <IP address obfuscated>
Discovered open port 9415/tcp on <IP address obfuscated>
Discovered open port 1328/tcp on <IP address obfuscated>
Discovered open port 999/tcp on <IP address obfuscated>
Discovered open port 1700/tcp on <IP address obfuscated>
Discovered open port 10009/tcp on <IP address obfuscated>
Discovered open port 1972/tcp on <IP address obfuscated>
Discovered open port 49400/tcp on <IP address obfuscated>
Discovered open port 8899/tcp on <IP address obfuscated>
Discovered open port 7999/tcp on <IP address obfuscated>
Discovered open port 1121/tcp on <IP address obfuscated>
Discovered open port 4567/tcp on <IP address obfuscated>
Discovered open port 57294/tcp on <IP address obfuscated>
Discovered open port 2500/tcp on <IP address obfuscated>
Discovered open port 5080/tcp on <IP address obfuscated>
Discovered open port 616/tcp on <IP address obfuscated>
Discovered open port 6004/tcp on <IP address obfuscated>
Discovered open port 667/tcp on <IP address obfuscated>
Discovered open port 2190/tcp on <IP address obfuscated>
Discovered open port 51493/tcp on <IP address obfuscated>
Discovered open port 24/tcp on <IP address obfuscated>
Discovered open port 5200/tcp on <IP address obfuscated>
Discovered open port 6789/tcp on <IP address obfuscated>
Discovered open port 1999/tcp on <IP address obfuscated>
Discovered open port 6788/tcp on <IP address obfuscated>
Discovered open port 49154/tcp on <IP address obfuscated>
Discovered open port 1071/tcp on <IP address obfuscated>
Discovered open port 6543/tcp on <IP address obfuscated>
Discovered open port 50636/tcp on <IP address obfuscated>
Discovered open port 2005/tcp on <IP address obfuscated>
Discovered open port 8010/tcp on <IP address obfuscated>
Discovered open port 1461/tcp on <IP address obfuscated>
Discovered open port 5815/tcp on <IP address obfuscated>
Discovered open port 6502/tcp on <IP address obfuscated>
Discovered open port 9503/tcp on <IP address obfuscated>
Discovered open port 512/tcp on <IP address obfuscated>
Discovered open port 32/tcp on <IP address obfuscated>
Discovered open port 6001/tcp on <IP address obfuscated>
Discovered open port 3826/tcp on <IP address obfuscated>
Discovered open port 4899/tcp on <IP address obfuscated>
Discovered open port 18988/tcp on <IP address obfuscated>
Discovered open port 2099/tcp on <IP address obfuscated>
Discovered open port 1165/tcp on <IP address obfuscated>
Discovered open port 13783/tcp on <IP address obfuscated>
Discovered open port 903/tcp on <IP address obfuscated>
Discovered open port 35500/tcp on <IP address obfuscated>
Discovered open port 27356/tcp on <IP address obfuscated>
Discovered open port 5033/tcp on <IP address obfuscated>
Discovered open port 32785/tcp on <IP address obfuscated>
Discovered open port 7777/tcp on <IP address obfuscated>
Discovered open port 7103/tcp on <IP address obfuscated>
Discovered open port 1164/tcp on <IP address obfuscated>
Discovered open port 49157/tcp on <IP address obfuscated>
Discovered open port 1334/tcp on <IP address obfuscated>
Discovered open port 27000/tcp on <IP address obfuscated>
Discovered open port 2393/tcp on <IP address obfuscated>
Discovered open port 3784/tcp on <IP address obfuscated>
Discovered open port 1041/tcp on <IP address obfuscated>
Discovered open port 12174/tcp on <IP address obfuscated>
Discovered open port 2557/tcp on <IP address obfuscated>
Discovered open port 19350/tcp on <IP address obfuscated>
Discovered open port 4129/tcp on <IP address obfuscated>
Discovered open port 52848/tcp on <IP address obfuscated>
Discovered open port 2160/tcp on <IP address obfuscated>
Discovered open port 1030/tcp on <IP address obfuscated>
Discovered open port 1300/tcp on <IP address obfuscated>
Discovered open port 4445/tcp on <IP address obfuscated>
Discovered open port 2041/tcp on <IP address obfuscated>
Discovered open port 2383/tcp on <IP address obfuscated>
Discovered open port 1097/tcp on <IP address obfuscated>
Discovered open port 14238/tcp on <IP address obfuscated>
Discovered open port 16113/tcp on <IP address obfuscated>
Discovered open port 8181/tcp on <IP address obfuscated>
Discovered open port 3871/tcp on <IP address obfuscated>
Discovered open port 64680/tcp on <IP address obfuscated>
Discovered open port 4005/tcp on <IP address obfuscated>
Discovered open port 5915/tcp on <IP address obfuscated>
Discovered open port 49163/tcp on <IP address obfuscated>
Discovered open port 9/tcp on <IP address obfuscated>
Discovered open port 1096/tcp on <IP address obfuscated>
Discovered open port 2602/tcp on <IP address obfuscated>
Discovered open port 2638/tcp on <IP address obfuscated>
Discovered open port 1417/tcp on <IP address obfuscated>
Discovered open port 992/tcp on <IP address obfuscated>
Discovered open port 1998/tcp on <IP address obfuscated>
Discovered open port 7937/tcp on <IP address obfuscated>
Discovered open port 32775/tcp on <IP address obfuscated>
Discovered open port 1111/tcp on <IP address obfuscated>
Discovered open port 5190/tcp on <IP address obfuscated>
Discovered open port 625/tcp on <IP address obfuscated>
Discovered open port 705/tcp on <IP address obfuscated>
Discovered open port 280/tcp on <IP address obfuscated>
Discovered open port 6699/tcp on <IP address obfuscated>
Discovered open port 5925/tcp on <IP address obfuscated>
Discovered open port 32773/tcp on <IP address obfuscated>
Discovered open port 10012/tcp on <IP address obfuscated>
Discovered open port 5054/tcp on <IP address obfuscated>
Discovered open port 1039/tcp on <IP address obfuscated>
Discovered open port 7002/tcp on <IP address obfuscated>
Discovered open port 3703/tcp on <IP address obfuscated>
Discovered open port 26/tcp on <IP address obfuscated>
Discovered open port 49167/tcp on <IP address obfuscated>
Discovered open port 83/tcp on <IP address obfuscated>
Discovered open port 5901/tcp on <IP address obfuscated>
Discovered open port 2382/tcp on <IP address obfuscated>
Discovered open port 1862/tcp on <IP address obfuscated>
Discovered open port 16012/tcp on <IP address obfuscated>
Discovered open port 40911/tcp on <IP address obfuscated>
Discovered open port 1009/tcp on <IP address obfuscated>
Discovered open port 5822/tcp on <IP address obfuscated>
Discovered open port 50006/tcp on <IP address obfuscated>
Discovered open port 898/tcp on <IP address obfuscated>
Discovered open port 20/tcp on <IP address obfuscated>
Discovered open port 1002/tcp on <IP address obfuscated>
Discovered open port 8022/tcp on <IP address obfuscated>
Discovered open port 6547/tcp on <IP address obfuscated>
Discovered open port 9999/tcp on <IP address obfuscated>
Discovered open port 7025/tcp on <IP address obfuscated>
Discovered open port 2047/tcp on <IP address obfuscated>
Discovered open port 2522/tcp on <IP address obfuscated>
Discovered open port 1067/tcp on <IP address obfuscated>
Discovered open port 1047/tcp on <IP address obfuscated>
Discovered open port 4321/tcp on <IP address obfuscated>
Discovered open port 16080/tcp on <IP address obfuscated>
Discovered open port 1098/tcp on <IP address obfuscated>
Discovered open port 1108/tcp on <IP address obfuscated>
Discovered open port 8088/tcp on <IP address obfuscated>
Discovered open port 85/tcp on <IP address obfuscated>
Discovered open port 1984/tcp on <IP address obfuscated>
Discovered open port 1174/tcp on <IP address obfuscated>
Discovered open port 49175/tcp on <IP address obfuscated>
Discovered open port 7778/tcp on <IP address obfuscated>
Discovered open port 3/tcp on <IP address obfuscated>
Discovered open port 1056/tcp on <IP address obfuscated>
Discovered open port 1971/tcp on <IP address obfuscated>
Discovered open port 8194/tcp on <IP address obfuscated>
Discovered open port 3801/tcp on <IP address obfuscated>
Discovered open port 9101/tcp on <IP address obfuscated>
Discovered open port 2020/tcp on <IP address obfuscated>
Discovered open port 1117/tcp on <IP address obfuscated>
Discovered open port 5100/tcp on <IP address obfuscated>
Discovered open port 3476/tcp on <IP address obfuscated>
Discovered open port 5120/tcp on <IP address obfuscated>
Discovered open port 8086/tcp on <IP address obfuscated>
Discovered open port 1043/tcp on <IP address obfuscated>
Discovered open port 1027/tcp on <IP address obfuscated>
Discovered open port 50500/tcp on <IP address obfuscated>
Discovered open port 9595/tcp on <IP address obfuscated>
Discovered open port 1055/tcp on <IP address obfuscated>
Discovered open port 5101/tcp on <IP address obfuscated>
Discovered open port 2725/tcp on <IP address obfuscated>
Discovered open port 6510/tcp on <IP address obfuscated>
Discovered open port 1154/tcp on <IP address obfuscated>
Discovered open port 6901/tcp on <IP address obfuscated>
Discovered open port 2869/tcp on <IP address obfuscated>
Discovered open port 1104/tcp on <IP address obfuscated>
Discovered open port 3269/tcp on <IP address obfuscated>
Discovered open port 6389/tcp on <IP address obfuscated>
Discovered open port 79/tcp on <IP address obfuscated>
Discovered open port 5862/tcp on <IP address obfuscated>
Discovered open port 254/tcp on <IP address obfuscated>
Discovered open port 9081/tcp on <IP address obfuscated>
Discovered open port 15003/tcp on <IP address obfuscated>
Discovered open port 1054/tcp on <IP address obfuscated>
Discovered open port 1500/tcp on <IP address obfuscated>
Discovered open port 54328/tcp on <IP address obfuscated>
Discovered open port 2920/tcp on <IP address obfuscated>
Discovered open port 12345/tcp on <IP address obfuscated>
Discovered open port 49999/tcp on <IP address obfuscated>
Discovered open port 1213/tcp on <IP address obfuscated>
Discovered open port 5810/tcp on <IP address obfuscated>
Discovered open port 1583/tcp on <IP address obfuscated>
Discovered open port 32782/tcp on <IP address obfuscated>
Discovered open port 139/tcp on <IP address obfuscated>
Discovered open port 1082/tcp on <IP address obfuscated>
Discovered open port 7938/tcp on <IP address obfuscated>
Discovered open port 9091/tcp on <IP address obfuscated>
Discovered open port 8400/tcp on <IP address obfuscated>
Discovered open port 2030/tcp on <IP address obfuscated>
Discovered open port 3007/tcp on <IP address obfuscated>
Discovered open port 6881/tcp on <IP address obfuscated>
Discovered open port 1277/tcp on <IP address obfuscated>
Discovered open port 2003/tcp on <IP address obfuscated>
Discovered open port 32784/tcp on <IP address obfuscated>
Discovered open port 32772/tcp on <IP address obfuscated>
Discovered open port 6006/tcp on <IP address obfuscated>
Discovered open port 41511/tcp on <IP address obfuscated>
Discovered open port 1152/tcp on <IP address obfuscated>
Discovered open port 27353/tcp on <IP address obfuscated>
Discovered open port 1580/tcp on <IP address obfuscated>
Discovered open port 880/tcp on <IP address obfuscated>
Discovered open port 20828/tcp on <IP address obfuscated>
Discovered open port 211/tcp on <IP address obfuscated>
Discovered open port 3998/tcp on <IP address obfuscated>
Discovered open port 9102/tcp on <IP address obfuscated>
Discovered open port 1455/tcp on <IP address obfuscated>
Discovered open port 1052/tcp on <IP address obfuscated>
Discovered open port 20031/tcp on <IP address obfuscated>
Discovered open port 16000/tcp on <IP address obfuscated>
Discovered open port 1132/tcp on <IP address obfuscated>
Discovered open port 2010/tcp on <IP address obfuscated>
Discovered open port 9001/tcp on <IP address obfuscated>
Discovered open port 222/tcp on <IP address obfuscated>
Discovered open port 995/tcp on <IP address obfuscated>
Discovered open port 8292/tcp on <IP address obfuscated>
Discovered open port 1038/tcp on <IP address obfuscated>
Discovered open port 7496/tcp on <IP address obfuscated>
Discovered open port 981/tcp on <IP address obfuscated>
Discovered open port 7741/tcp on <IP address obfuscated>
Discovered open port 8402/tcp on <IP address obfuscated>
Discovered open port 34572/tcp on <IP address obfuscated>
Discovered open port 912/tcp on <IP address obfuscated>
Discovered open port 37/tcp on <IP address obfuscated>
Discovered open port 1234/tcp on <IP address obfuscated>
Discovered open port 901/tcp on <IP address obfuscated>
Discovered open port 6129/tcp on <IP address obfuscated>
Discovered open port 1556/tcp on <IP address obfuscated>
Discovered open port 3168/tcp on <IP address obfuscated>
Discovered open port 49161/tcp on <IP address obfuscated>
Discovered open port 1166/tcp on <IP address obfuscated>
Discovered open port 5560/tcp on <IP address obfuscated>
Discovered open port 1114/tcp on <IP address obfuscated>
Discovered open port 1947/tcp on <IP address obfuscated>
Discovered open port 4998/tcp on <IP address obfuscated>
Discovered open port 1218/tcp on <IP address obfuscated>
Discovered open port 10004/tcp on <IP address obfuscated>
Discovered open port 1076/tcp on <IP address obfuscated>
Discovered open port 3493/tcp on <IP address obfuscated>
Discovered open port 1000/tcp on <IP address obfuscated>
Discovered open port 1352/tcp on <IP address obfuscated>
Discovered open port 9418/tcp on <IP address obfuscated>
Discovered open port 1126/tcp on <IP address obfuscated>
Discovered open port 1175/tcp on <IP address obfuscated>
Discovered open port 9535/tcp on <IP address obfuscated>
Discovered open port 1037/tcp on <IP address obfuscated>
Discovered open port 3918/tcp on <IP address obfuscated>
Discovered open port 3517/tcp on <IP address obfuscated>
Discovered open port 8002/tcp on <IP address obfuscated>
Discovered open port 49155/tcp on <IP address obfuscated>
Discovered open port 8300/tcp on <IP address obfuscated>
Discovered open port 777/tcp on <IP address obfuscated>
Discovered open port 2013/tcp on <IP address obfuscated>
Discovered open port 4279/tcp on <IP address obfuscated>
Discovered open port 5030/tcp on <IP address obfuscated>
Discovered open port 6566/tcp on <IP address obfuscated>
Discovered open port 12000/tcp on <IP address obfuscated>
Discovered open port 6969/tcp on <IP address obfuscated>
Discovered open port 13782/tcp on <IP address obfuscated>
Discovered open port 1032/tcp on <IP address obfuscated>
Discovered open port 2103/tcp on <IP address obfuscated>
Discovered open port 4900/tcp on <IP address obfuscated>
Discovered open port 3301/tcp on <IP address obfuscated>
Discovered open port 17877/tcp on <IP address obfuscated>
Discovered open port 524/tcp on <IP address obfuscated>
Discovered open port 26214/tcp on <IP address obfuscated>
Discovered open port 1322/tcp on <IP address obfuscated>
Discovered open port 1057/tcp on <IP address obfuscated>
Discovered open port 5631/tcp on <IP address obfuscated>
Discovered open port 30718/tcp on <IP address obfuscated>
Discovered open port 6025/tcp on <IP address obfuscated>
Discovered open port 6106/tcp on <IP address obfuscated>
Discovered open port 1198/tcp on <IP address obfuscated>
Discovered open port 5003/tcp on <IP address obfuscated>
Discovered open port 8200/tcp on <IP address obfuscated>
Discovered open port 2967/tcp on <IP address obfuscated>
Discovered open port 4848/tcp on <IP address obfuscated>
Discovered open port 8099/tcp on <IP address obfuscated>
Discovered open port 9877/tcp on <IP address obfuscated>
Discovered open port 13/tcp on <IP address obfuscated>
Discovered open port 8500/tcp on <IP address obfuscated>
Discovered open port 10215/tcp on <IP address obfuscated>
Discovered open port 631/tcp on <IP address obfuscated>
Discovered open port 32781/tcp on <IP address obfuscated>
Discovered open port 44176/tcp on <IP address obfuscated>
Discovered open port 2998/tcp on <IP address obfuscated>
Discovered open port 125/tcp on <IP address obfuscated>
Discovered open port 45100/tcp on <IP address obfuscated>
Discovered open port 8100/tcp on <IP address obfuscated>
Discovered open port 3324/tcp on <IP address obfuscated>
Discovered open port 16016/tcp on <IP address obfuscated>
Discovered open port 666/tcp on <IP address obfuscated>
Discovered open port 720/tcp on <IP address obfuscated>
Discovered open port 10626/tcp on <IP address obfuscated>
Discovered open port 1310/tcp on <IP address obfuscated>
Discovered open port 19283/tcp on <IP address obfuscated>
Discovered open port 109/tcp on <IP address obfuscated>
Discovered open port 3050/tcp on <IP address obfuscated>
Discovered open port 9575/tcp on <IP address obfuscated>
Discovered open port 61900/tcp on <IP address obfuscated>
Discovered open port 13722/tcp on <IP address obfuscated>
Discovered open port 1533/tcp on <IP address obfuscated>
Discovered open port 416/tcp on <IP address obfuscated>
Discovered open port 9000/tcp on <IP address obfuscated>
Discovered open port 9103/tcp on <IP address obfuscated>
Discovered open port 7443/tcp on <IP address obfuscated>
Discovered open port 9090/tcp on <IP address obfuscated>
Discovered open port 1100/tcp on <IP address obfuscated>
Discovered open port 146/tcp on <IP address obfuscated>
Discovered open port 2910/tcp on <IP address obfuscated>
Discovered open port 50389/tcp on <IP address obfuscated>
Discovered open port 1091/tcp on <IP address obfuscated>
Discovered open port 5859/tcp on <IP address obfuscated>
Discovered open port 6567/tcp on <IP address obfuscated>
Discovered open port 10628/tcp on <IP address obfuscated>
Discovered open port 33899/tcp on <IP address obfuscated>
Discovered open port 10003/tcp on <IP address obfuscated>
Discovered open port 16992/tcp on <IP address obfuscated>
Discovered open port 2022/tcp on <IP address obfuscated>
Discovered open port 1073/tcp on <IP address obfuscated>
Discovered open port 6005/tcp on <IP address obfuscated>
Discovered open port 500/tcp on <IP address obfuscated>
Discovered open port 55555/tcp on <IP address obfuscated>
Discovered open port 1687/tcp on <IP address obfuscated>
Discovered open port 9593/tcp on <IP address obfuscated>
Discovered open port 3322/tcp on <IP address obfuscated>
Discovered open port 5900/tcp on <IP address obfuscated>
Discovered open port 3404/tcp on <IP address obfuscated>
sendto in send_ip_packet: sendto(5, packet, 44, 0, <IP address obfuscated>, 16) => Network is unreachable
Offending packet: TCP 192.168.1.45:53571 > <IP address obfuscated>:16993 S ttl=49 id=54887 iplen=44  seq=1338588651 win=2048 <mss 1460>
Sleeping 15 seconds then retrying
adjust_timeouts2: packet supposedly had rtt of 15023643 microseconds.  Ignoring time.
adjust_timeouts2: packet supposedly had rtt of 15023643 microseconds.  Ignoring time.
Completed SYN Stealth Scan at 11:52, 105.73s elapsed (1000 total ports)
Initiating Service scan at 11:52
Scanning 607 services on <IP address obfuscated>
Completed Service scan at 11:53, 41.64s elapsed (610 services on 1 host)
Initiating OS detection (try #1) against <IP address obfuscated>
WARNING:  RST from <IP address obfuscated> port 1 -- is this port really open?
WARNING:  RST from <IP address obfuscated> port 1 -- is this port really open?
WARNING:  RST from <IP address obfuscated> port 1 -- is this port really open?
WARNING:  RST from <IP address obfuscated> port 1 -- is this port really open?
WARNING:  RST from <IP address obfuscated> port 1 -- is this port really open?
WARNING:  RST from <IP address obfuscated> port 1 -- is this port really open?
Retrying OS detection (try #2) against <IP address obfuscated>
WARNING:  RST from <IP address obfuscated> port 1 -- is this port really open?
WARNING:  RST from <IP address obfuscated> port 1 -- is this port really open?
WARNING:  RST from <IP address obfuscated> port 1 -- is this port really open?
WARNING:  RST from <IP address obfuscated> port 1 -- is this port really open?
WARNING:  RST from <IP address obfuscated> port 1 -- is this port really open?
WARNING:  RST from <IP address obfuscated> port 1 -- is this port really open?
Initiating Traceroute at 11:53
<IP address obfuscated>: guessing hop distance at 27
Completed Traceroute at 11:56, 150.18s elapsed
Initiating Parallel DNS resolution of 3 hosts. at 11:56
Completed Parallel DNS resolution of 3 hosts. at 11:56, 10.04s elapsed
SCRIPT ENGINE: Initiating script scanning.
SCRIPT ENGINE: '/usr/share/nmap/scripts/dns-test-open-recursion.nse' threw a run time error and could not be loaded.
SCRIPT ENGINE: '/usr/share/nmap/scripts/skype_v2-version.nse' threw a run time error and could not be loaded.
SCRIPT ENGINE: error while initializing script rules:
/usr/share/nmap/scripts/script.db:20: rpcinfo.nse is not a file!
stack traceback:
	[C]: in function 'Entry'
	/usr/share/nmap/scripts/script.db:20: in main chunk
	[C]: ?
	[C]: ?

SCRIPT ENGINE: Aborting script scan.
Host <IP address obfuscated> appears to be up ... good.
Interesting ports on <IP address obfuscated>:
Not shown: 261 closed ports, 129 filtered ports
PORT      STATE SERVICE               VERSION
1/tcp     open  tcpmux?
3/tcp     open  compressnet?
6/tcp     open  unknown?
7/tcp     open  echo?
9/tcp     open  discard?
13/tcp    open  daytime?
19/tcp    open  chargen?
20/tcp    open  ftp-data?
21/tcp    open  ftp?
22/tcp    open  ssh?
24/tcp    open  priv-mail?
26/tcp    open  unknown?
32/tcp    open  unknown?
33/tcp    open  dsp?
37/tcp    open  time?
42/tcp    open  nameserver?
43/tcp    open  whois?
70/tcp    open  gopher?
79/tcp    open  finger?
80/tcp    open  http                  Apache httpd 2.2.8 ((Ubuntu) PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g)
82/tcp    open  xfer?
83/tcp    open  mit-ml-dev?
84/tcp    open  ctf?
85/tcp    open  mit-ml-dev?
88/tcp    open  kerberos-sec?
89/tcp    open  su-mit-tg?
90/tcp    open  dnsix?
99/tcp    open  metagram?
109/tcp   open  pop2?
113/tcp   open  auth?
125/tcp   open  locus-map?
135/tcp   open  msrpc?
139/tcp   open  netbios-ssn?
143/tcp   open  imap?
144/tcp   open  news?
146/tcp   open  iso-tp0?
161/tcp   open  snmp?
211/tcp   open  914c-g?
222/tcp   open  rsh-spx?
254/tcp   open  unknown?
259/tcp   open  esro-gen?
280/tcp   open  http-mgmt?
306/tcp   open  unknown?
311/tcp   open  asip-webadmin?
340/tcp   open  unknown?
389/tcp   open  ldap?
406/tcp   open  imsp?
407/tcp   open  timbuktu?
416/tcp   open  silverplatter?
417/tcp   open  onmux?
425/tcp   open  icad-el?
427/tcp   open  svrloc?
443/tcp   open  ssl/http              Apache httpd 2.2.8 ((Ubuntu) PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g)
464/tcp   open  kpasswd5?
481/tcp   open  dvs?
500/tcp   open  isakmp?
512/tcp   open  exec?
514/tcp   open  shell?
515/tcp   open  printer?
524/tcp   open  ncp?
544/tcp   open  kshell?
548/tcp   open  afp?
554/tcp   open  rtsp?
555/tcp   open  dsf?
616/tcp   open  unknown?
625/tcp   open  apple-xsrvr-admin?
631/tcp   open  ipp?
636/tcp   open  ldapssl?
648/tcp   open  unknown?
666/tcp   open  doom?
667/tcp   open  unknown?
668/tcp   open  unknown?
687/tcp   open  unknown?
700/tcp   open  unknown?
705/tcp   open  unknown?
720/tcp   open  unknown?
777/tcp   open  unknown?
783/tcp   open  spamassassin?
801/tcp   open  device?
808/tcp   open  ccproxy-http?
880/tcp   open  unknown?
888/tcp   open  accessbuilder?
898/tcp   open  sun-manageconsole?
900/tcp   open  unknown?
901/tcp   open  samba-swat?
902/tcp   open  iss-realsecure?
903/tcp   open  iss-console-mgr?
911/tcp   open  unknown?
912/tcp   open  unknown?
981/tcp   open  unknown?
990/tcp   open  ftps?
992/tcp   open  telnets?
993/tcp   open  imaps?
995/tcp   open  pop3s?
999/tcp   open  garcon?
1000/tcp  open  cadlock?
1001/tcp  open  unknown?
1002/tcp  open  windows-icfw?
1009/tcp  open  unknown?
1011/tcp  open  unknown?
1022/tcp  open  unknown?
1026/tcp  open  LSA-or-nterm?
1027/tcp  open  IIS?
1028/tcp  open  unknown?
1030/tcp  open  iad1?
1032/tcp  open  iad3?
1033/tcp  open  netinfo?
1035/tcp  open  unknown?
1036/tcp  open  unknown?
1037/tcp  open  unknown?
1038/tcp  open  unknown?
1039/tcp  open  unknown?
1041/tcp  open  unknown?
1043/tcp  open  boinc?
1046/tcp  open  unknown?
1047/tcp  open  unknown?
1048/tcp  open  unknown?
1049/tcp  open  unknown?
1050/tcp  open  java-or-OTGfileshare?
1051/tcp  open  unknown?
1052/tcp  open  unknown?
1054/tcp  open  unknown?
1055/tcp  open  unknown?
1056/tcp  open  unknown?
1057/tcp  open  unknown?
1058/tcp  open  nim?
1059/tcp  open  nimreg?
1061/tcp  open  unknown?
1063/tcp  open  unknown?
1064/tcp  open  unknown?
1065/tcp  open  unknown?
1066/tcp  open  unknown?
1067/tcp  open  instl_boots?
1068/tcp  open  instl_bootc?
1069/tcp  open  unknown?
1070/tcp  open  unknown?
1071/tcp  open  unknown?
1072/tcp  open  unknown?
1073/tcp  open  unknown?
1076/tcp  open  sns_credit?
1080/tcp  open  socks?
1082/tcp  open  unknown?
1086/tcp  open  unknown?
1087/tcp  open  unknown?
1088/tcp  open  unknown?
1089/tcp  open  unknown?
1091/tcp  open  unknown?
1093/tcp  open  unknown?
1094/tcp  open  unknown?
1095/tcp  open  unknown?
1096/tcp  open  unknown?
1097/tcp  open  unknown?
1098/tcp  open  unknown?
1100/tcp  open  unknown?
1102/tcp  open  unknown?
1104/tcp  open  unknown?
1107/tcp  open  unknown?
1108/tcp  open  unknown?
1110/tcp  open  nfsd-status?
1111/tcp  open  unknown?
1114/tcp  open  unknown?
1117/tcp  open  unknown?
1119/tcp  open  unknown?
1121/tcp  open  unknown?
1124/tcp  open  unknown?
1126/tcp  open  unknown?
1130/tcp  open  unknown?
1131/tcp  open  unknown?
1132/tcp  open  unknown?
1145/tcp  open  unknown?
1148/tcp  open  unknown?
1149/tcp  open  unknown?
1152/tcp  open  unknown?
1154/tcp  open  unknown?
1164/tcp  open  unknown?
1165/tcp  open  unknown?
1166/tcp  open  unknown?
1174/tcp  open  unknown?
1175/tcp  open  unknown?
1187/tcp  open  unknown?
1198/tcp  open  unknown?
1213/tcp  open  unknown?
1218/tcp  open  unknown?
1234/tcp  open  hotline?
1244/tcp  open  unknown?
1271/tcp  open  unknown?
1277/tcp  open  unknown?
1287/tcp  open  unknown?
1300/tcp  open  unknown?
1301/tcp  open  unknown?
1309/tcp  open  unknown?
1310/tcp  open  unknown?
1311/tcp  open  unknown?
1322/tcp  open  unknown?
1328/tcp  open  unknown?
1334/tcp  open  unknown?
1352/tcp  open  lotusnotes?
1417/tcp  open  timbuktu-srv1?
1433/tcp  open  ms-sql-s?
1455/tcp  open  esl-lm?
1461/tcp  open  ibm_wrless_lan?
1494/tcp  open  citrix-ica?
1500/tcp  open  vlsi-lm?
1503/tcp  open  imtc-mcs?
1533/tcp  open  virtual-places?
1556/tcp  open  unknown?
1580/tcp  open  unknown?
1583/tcp  open  unknown?
1594/tcp  open  unknown?
1658/tcp  open  unknown?
1666/tcp  open  netview-aix-6?
1687/tcp  open  unknown?
1700/tcp  open  unknown?
1720/tcp  open  H.323/Q.931?
1721/tcp  open  unknown?
1723/tcp  open  pptp?
1761/tcp  open  landesk-rc?
1782/tcp  open  unknown?
1783/tcp  open  unknown?
1805/tcp  open  unknown?
1812/tcp  open  unknown?
1839/tcp  open  unknown?
1840/tcp  open  unknown?
1862/tcp  open  unknown?
1900/tcp  open  upnp?
1935/tcp  open  rtmp?
1947/tcp  open  unknown?
1971/tcp  open  unknown?
1972/tcp  open  unknown?
1974/tcp  open  unknown?
1984/tcp  open  bigbrother?
1998/tcp  open  x25-svc-port?
1999/tcp  open  tcp-id-port?
2003/tcp  open  finger?
2005/tcp  open  deslogin?
2006/tcp  open  invokator?
2009/tcp  open  news?
2010/tcp  open  search?
2013/tcp  open  raid-am?
2020/tcp  open  xinupageserver?
2022/tcp  open  down?
2030/tcp  open  device2?
2033/tcp  open  glogger?
2041/tcp  open  interbase?
2042/tcp  open  isis?
2045/tcp  open  cdfunc?
2046/tcp  open  sdfunc?
2047/tcp  open  dls?
2049/tcp  open  nfs?
2065/tcp  open  dlsrpn?
2068/tcp  open  advocentkvm?
2099/tcp  open  unknown?
2103/tcp  open  unknown?
2105/tcp  open  eklogin?
2106/tcp  open  ekshell?
2121/tcp  open  ccproxy-ftp?
2160/tcp  open  unknown?
2170/tcp  open  unknown?
2179/tcp  open  unknown?
2190/tcp  open  unknown?
2323/tcp  open  unknown?
2381/tcp  open  unknown?
2382/tcp  open  unknown?
2383/tcp  open  unknown?
2393/tcp  open  unknown?
2500/tcp  open  rtsserv?
2522/tcp  open  unknown?
2525/tcp  open  unknown?
2557/tcp  open  unknown?
2602/tcp  open  ripd?
2604/tcp  open  ospfd?
2605/tcp  open  bgpd?
2608/tcp  open  unknown?
2638/tcp  open  sybase?
2702/tcp  open  unknown?
2717/tcp  open  unknown?
2725/tcp  open  unknown?
2800/tcp  open  unknown?
2869/tcp  open  unknown?
2910/tcp  open  unknown?
2920/tcp  open  unknown?
2967/tcp  open  unknown?
2998/tcp  open  iss-realsec?
3000/tcp  open  ppp?
3001/tcp  open  nessus?
3007/tcp  open  unknown?
3011/tcp  open  unknown?
3013/tcp  open  unknown?
3017/tcp  open  unknown?
3030/tcp  open  unknown?
3050/tcp  open  unknown?
3052/tcp  open  powerchute?
3168/tcp  open  unknown?
3211/tcp  open  unknown?
3260/tcp  open  unknown?
3261/tcp  open  unknown?
3268/tcp  open  globalcatLDAP?
3269/tcp  open  globalcatLDAPssl?
3300/tcp  open  unknown?
3301/tcp  open  unknown?
3322/tcp  open  unknown?
3323/tcp  open  unknown?
3324/tcp  open  unknown?
3325/tcp  open  unknown?
3351/tcp  open  unknown?
3370/tcp  open  unknown?
3371/tcp  open  unknown?
3404/tcp  open  unknown?
3476/tcp  open  unknown?
3493/tcp  open  unknown?
3517/tcp  open  unknown?
3527/tcp  open  unknown?
3689/tcp  open  rendezvous?
3703/tcp  open  unknown?
3737/tcp  open  unknown?
3784/tcp  open  unknown?
3800/tcp  open  unknown?
3801/tcp  open  unknown?
3809/tcp  open  unknown?
3814/tcp  open  unknown?
3826/tcp  open  unknown?
3827/tcp  open  unknown?
3871/tcp  open  unknown?
3880/tcp  open  unknown?
3914/tcp  open  unknown?
3918/tcp  open  unknown?
3920/tcp  open  unknown?
3986/tcp  open  mapper-ws_ethd?
3998/tcp  open  unknown?
4000/tcp  open  remoteanything?
4002/tcp  open  mlchat-proxy?
4003/tcp  open  unknown?
4005/tcp  open  unknown?
4111/tcp  open  unknown?
4129/tcp  open  unknown?
4242/tcp  open  unknown?
4279/tcp  open  unknown?
4321/tcp  open  rwhois?
4445/tcp  open  unknown?
4567/tcp  open  unknown?
4848/tcp  open  unknown?
4899/tcp  open  radmin?
4900/tcp  open  unknown?
4998/tcp  open  maybe-veritas?
5000/tcp  open  upnp?
5002/tcp  open  rfe?
5003/tcp  open  filemaker?
5004/tcp  open  unknown?
5030/tcp  open  unknown?
5033/tcp  open  unknown?
5050/tcp  open  mmcc?
5051/tcp  open  unknown?
5054/tcp  open  unknown?
5080/tcp  open  unknown?
5100/tcp  open  admd?
5101/tcp  open  admdog?
5120/tcp  open  unknown?
5190/tcp  open  aol?
5200/tcp  open  unknown?
5222/tcp  open  unknown?
5280/tcp  open  unknown?
5298/tcp  open  unknown?
5414/tcp  open  unknown?
5544/tcp  open  unknown?
5550/tcp  open  sdadmind?
5555/tcp  open  freeciv?
5560/tcp  open  isqlplus?
5631/tcp  open  pcanywheredata?
5666/tcp  open  unknown?
5679/tcp  open  activesync?
5718/tcp  open  unknown?
5800/tcp  open  vnc-http?
5810/tcp  open  unknown?
5815/tcp  open  unknown?
5822/tcp  open  unknown?
5850/tcp  open  unknown?
5859/tcp  open  unknown?
5862/tcp  open  unknown?
5900/tcp  open  vnc?
5901/tcp  open  vnc-1?
5904/tcp  open  unknown?
5911/tcp  open  unknown?
5915/tcp  open  unknown?
5925/tcp  open  unknown?
5952/tcp  open  unknown?
5961/tcp  open  unknown?
5962/tcp  open  unknown?
6000/tcp  open  X11?
6001/tcp  open  X11:1?
6003/tcp  open  X11:3?
6004/tcp  open  X11:4?
6005/tcp  open  X11:5?
6006/tcp  open  X11:6?
6007/tcp  open  X11:7?
6025/tcp  open  unknown?
6059/tcp  open  unknown?
6100/tcp  open  unknown?
6106/tcp  open  isdninfo?
6123/tcp  open  unknown?
6129/tcp  open  unknown?
6389/tcp  open  unknown?
6502/tcp  open  netop-rc?
6510/tcp  open  unknown?
6543/tcp  open  mythtv?
6547/tcp  open  powerchuteplus?
6566/tcp  open  unknown?
6567/tcp  open  unknown?
6580/tcp  open  unknown?
6668/tcp  open  irc?
6699/tcp  open  napster?
6788/tcp  open  unknown?
6789/tcp  open  unknown?
6839/tcp  open  unknown?
6881/tcp  open  bittorrent-tracker?
6901/tcp  open  unknown?
6969/tcp  open  acmsoda?
7000/tcp  open  afs3-fileserver?
7001/tcp  open  afs3-callback?
7002/tcp  open  afs3-prserver?
7004/tcp  open  afs3-kaserver?
7025/tcp  open  unknown?
7103/tcp  open  unknown?
7201/tcp  open  dlip?
7402/tcp  open  unknown?
7443/tcp  open  unknown?
7496/tcp  open  unknown?
7625/tcp  open  unknown?
7627/tcp  open  unknown?
7676/tcp  open  unknown?
7741/tcp  open  unknown?
7777/tcp  open  unknown?
7778/tcp  open  unknown?
7800/tcp  open  unknown?
7920/tcp  open  unknown?
7921/tcp  open  unknown?
7937/tcp  open  nsrexecd?
7938/tcp  open  lgtomapper?
7999/tcp  open  unknown?
8000/tcp  open  http-alt?
8002/tcp  open  unknown?
8007/tcp  open  ajp12?
8009/tcp  open  ajp13?
8010/tcp  open  unknown?
8011/tcp  open  unknown?
8021/tcp  open  ftp-proxy?
8022/tcp  open  unknown?
8045/tcp  open  unknown?
8081/tcp  open  blackice-icecap?
8082/tcp  open  blackice-alerts?
8083/tcp  open  unknown?
8084/tcp  open  unknown?
8086/tcp  open  unknown?
8087/tcp  open  unknown?
8088/tcp  open  unknown?
8090/tcp  open  unknown?
8093/tcp  open  unknown?
8099/tcp  open  unknown?
8100/tcp  open  unknown?
8180/tcp  open  unknown?
8181/tcp  open  unknown?
8192/tcp  open  unknown?
8194/tcp  open  unknown?
8200/tcp  open  unknown?
8291/tcp  open  unknown?
8292/tcp  open  unknown?
8300/tcp  open  unknown?
8333/tcp  open  unknown?
8400/tcp  open  unknown?
8402/tcp  open  unknown?
8500/tcp  open  unknown?
8600/tcp  open  unknown?
8649/tcp  open  unknown?
8651/tcp  open  unknown?
8652/tcp  open  unknown?
8654/tcp  open  unknown?
8888/tcp  open  sun-answerbook?
8899/tcp  open  unknown?
9000/tcp  open  unknown?
9001/tcp  open  unknown?
9003/tcp  open  unknown?
9010/tcp  open  unknown?
9050/tcp  open  tor-socks?
9071/tcp  open  unknown?
9080/tcp  open  unknown?
9081/tcp  open  unknown?
9090/tcp  open  zeus-admin?
9091/tcp  open  unknown?
9101/tcp  open  jetdirect?
9102/tcp  open  jetdirect?
9103/tcp  open  jetdirect?
9415/tcp  open  unknown?
9418/tcp  open  unknown?
9503/tcp  open  unknown?
9535/tcp  open  man?
9575/tcp  open  unknown?
9593/tcp  open  unknown?
9595/tcp  open  unknown?
9618/tcp  open  unknown?
9877/tcp  open  unknown?
9898/tcp  open  unknown?
9917/tcp  open  unknown?
9968/tcp  open  unknown?
9999/tcp  open  abyss?
10000/tcp open  snet-sensor-mgmt?
10001/tcp open  unknown?
10002/tcp open  unknown?
10003/tcp open  unknown?
10004/tcp open  unknown?
10009/tcp open  unknown?
10012/tcp open  unknown?
10025/tcp open  unknown?
10215/tcp open  unknown?
10243/tcp open  unknown?
10616/tcp open  unknown?
10626/tcp open  unknown?
10628/tcp open  unknown?
10778/tcp open  unknown?
11110/tcp open  unknown?
11111/tcp open  unknown?
12000/tcp open  cce4x?
12174/tcp open  unknown?
12345/tcp open  netbus?
13722/tcp open  netbackup?
13782/tcp open  netbackup?
13783/tcp open  netbackup?
14238/tcp open  unknown?
14441/tcp open  unknown?
14442/tcp open  unknown?
15003/tcp open  unknown?
15004/tcp open  unknown?
15660/tcp open  unknown?
16000/tcp open  unknown?
16012/tcp open  unknown?
16016/tcp open  unknown?
16018/tcp open  unknown?
16080/tcp open  osxwebadmin?
16113/tcp open  unknown?
16992/tcp open  unknown?
17877/tcp open  unknown?
17988/tcp open  unknown?
18040/tcp open  unknown?
18988/tcp open  unknown?
19101/tcp open  unknown?
19283/tcp open  unknown?
19350/tcp open  unknown?
19780/tcp open  unknown?
20031/tcp open  unknown?
20828/tcp open  unknown?
21571/tcp open  unknown?
23502/tcp open  unknown?
24800/tcp open  unknown?
26214/tcp open  unknown?
27000/tcp open  flexlm0?
27353/tcp open  unknown?
27356/tcp open  unknown?
27715/tcp open  unknown?
28201/tcp open  unknown?
30718/tcp open  unknown?
30951/tcp open  unknown?
32772/tcp open  sometimes-rpc7?
32773/tcp open  sometimes-rpc9?
32775/tcp open  sometimes-rpc13?
32779/tcp open  sometimes-rpc21?
32781/tcp open  unknown?
32782/tcp open  unknown?
32783/tcp open  unknown?
32784/tcp open  unknown?
32785/tcp open  unknown?
33899/tcp open  unknown?
34571/tcp open  unknown?
34572/tcp open  unknown?
35500/tcp open  unknown?
38292/tcp open  landesk-cba?
40193/tcp open  unknown?
40911/tcp open  unknown?
41511/tcp open  unknown?
44176/tcp open  unknown?
44442/tcp open  coldfusion-auth?
44501/tcp open  unknown?
45100/tcp open  unknown?
49152/tcp open  unknown?
49154/tcp open  unknown?
49155/tcp open  unknown?
49157/tcp open  unknown?
49159/tcp open  unknown?
49161/tcp open  unknown?
49163/tcp open  unknown?
49165/tcp open  unknown?
49167/tcp open  unknown?
49175/tcp open  unknown?
49176/tcp open  unknown?
49400/tcp open  compaqdiag?
49999/tcp open  unknown?
50006/tcp open  unknown?
50389/tcp open  unknown?
50500/tcp open  unknown?
50636/tcp open  unknown?
51493/tcp open  unknown?
52822/tcp open  unknown?
52848/tcp open  unknown?
54328/tcp open  unknown?
55055/tcp open  unknown?
55056/tcp open  unknown?
55555/tcp open  unknown?
56737/tcp open  unknown?
57294/tcp open  unknown?
60443/tcp open  unknown?
61900/tcp open  unknown?
64680/tcp open  unknown?
65000/tcp open  unknown?
No OS matches for host

TRACEROUTE (using port 25/tcp)
HOP RTT    ADDRESS
1   0.52   dslrouter (192.168.1.1)
2   ... 27 no response
28  23.35  <IP address obfuscated>

Read data files from: /usr/share/nmap
OS and Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 324.04 seconds
           Raw packets sent: 1732 (79.704KB) | Rcvd: 2116 (110.087KB
```

I think nmap may just be confused, because I definitely didn't open any of those ports besides the ones needed by ssh and apache, and I can't reach any services (including ssh) from the machine on which I ran the scan (which is separated from the web server by a firewall).  Is there any reason that I might want to worry more about this, or is it indeed not serious?

---

### Post by chiefbutz on 2009-05-19
I'm no expert, but could it be something with the virtual machine? I just ask because something has to be making nmap believe there are all those open ports. Also, did you explicitly close the ports that it thinks are open, or maybe close all but the ones you wanted? Not sure what is going on, but maybe an idea will be triggered.

---

### Post by pytheas22 on 2009-05-19
> I'm no expert, but could it be something with the virtual machine? I just ask because something has to be making nmap believe there are all those open ports. Also, did you explicitly close the ports that it thinks are open, or maybe close all but the ones you wanted? Not sure what is going on, but maybe an idea will be triggered.

Thanks for the thoughts.  I don't think it's the virtual machine, because as far as the outside world knows, this is a physical server, not a virtualized one.  But there could be something going on there that makes nmap think this.

The machine is closed (via ufw) to all traffic except from a handful of specific hosts (the computer from which I ran the scan is not on the whitelist), so I was a bit surprised that nmap could see it at all--I can't even ping it unless I ssh into one of the whitelisted hosts first.

---

### Post by The Cog on 2009-05-20
Are you scanning it from itself? Firewalls always allow a machine to talk to itself, so youneed to scan from a different machine to get meaningful results.

---

### Post by pytheas22 on 2009-05-20
> Are you scanning it from itself? Firewalls always allow a machine to talk to itself, so youneed to scan from a different machine to get meaningful results.

No, I was scanning from a remote machine on a completely separate network.  But I really think nmap was just confused about what was going on, and that the machine is probably fine.

---

### Post by cariboo on 2009-05-20
It looks like you were scanning your isp's server. I have seen similar output when I mistyped the ip address of a customer and ended up scanning his ips's server.

---

### Post by cprofitt on 2009-05-22
Are you able to post the nmap command you used to produce the output?

---

### Post by pytheas22 on 2009-05-22
> **cprofitt said:**
> Are you able to post the nmap command you used to produce the output?

Sure:
```

nmap -T Aggressive -A -v <IP address>
```

Just a standard scan...

---

