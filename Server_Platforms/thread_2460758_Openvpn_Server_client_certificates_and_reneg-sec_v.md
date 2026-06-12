---
title: "Openvpn Server client certificates and reneg-sec value"
date: 2021-04-18
forum: Server Platforms
---

### Post by secooonder on 2021-04-18
Hi
I configured my own Vpn Server on Ubuntu 20.04 LTS.
OpenVpn Server version is 2.4.7
Easy-rsa version is 3.0.4


i created a user cert below
```
./easy-rsa gen-req client7
./easy-rsa sign-req client client7
```  
                     or
```
./easy-rsa build-client-full client7
```


Are these two the same process ? i think, yes ?
-----------------------------------------------
i have 3 problems.
*Firstly; *


_About cert._


But I was creating with pkcs.12  format on the previous server.
```
source ./vars
./build-key-pkcs12 client7
```



[list]Which is safer and fast ? pkcs12 or  ./easy-rsa build-client-full client7? Which one do you recommend ? 
When created with pkcs12, no need ca.crt and client7.crt ?
What type of certificate(pkcs10,pkcs11 vb) is produced with the above creating I made(./easy-rsa build-client-full client7)?
How to create pkcs12 with easy rsa? i could not find in the new version
[/list]



*Secondly; *


_About reneg-sec._
i know what is this.


Some of our branches should stay connected to the center 24/7 without interruption by OpenVpn.(I connected branches with iroute parameter to center)
1)What is the benefit of keeping this value low or high?
2)What is the harm of this value to be zero?


*Thirdly*
About common name.


isp blocked our Open Vpn server because of "common name".Didn't say what was wrong
How should common name be ?


Thank you very much for your help

---

