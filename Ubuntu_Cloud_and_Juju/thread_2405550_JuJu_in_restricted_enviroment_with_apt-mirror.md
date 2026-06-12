---
title: "JuJu in restricted enviroment with apt-mirror"
date: 2018-11-07
forum: Ubuntu Cloud and Juju
---

### Post by theoharis on 2018-11-07
Hello 
 

I am following this link : [https://github.com/juju-solutions/bundle-canonical-kubernetes/wiki/Running-CDK-in-a-restricted-environment](https://github.com/juju-solutions/bundle-canonical-kubernetes/wiki/Running-CDK-in-a-restricted-environment)   to set up JuJu in an offline enviroment with the help of apt-mirror
My OS is ubuntu bionic server 18.04.1 and my final goal is to deploy kubernetes on the machines added via JuJu like the page is explaining 

I set up a bionic mirror with apt-mirror , yesterday and I added one machine

```
~$ juju machinesMachine  State    DNS           Inst id              Series  AZ  Message
0        started  192.168.1.91  manual:192.168.1.91  bionic      Manually provisioned machine
```

i have been trying to add more machines today but it never succeeds .  The machines that i want to add , show these errors as soon as i enter juju add-machine ssh:username@ip


```
: Failed to fetch http://192.168.1.93/ubuntu/pool/main/p/plymouth/plymouth_0.9.3-1ubuntu7.18.04.1_amd64.deb  File has unexpected size (97453 != 107808). Mirror sync in progress? [IP: 192.168.1.93 80]   Hashes of expected file:
    - SHA256:99c434fc49bb283c3d23012eb0d99db17604a161f29c45769d7c68cdbc4d81ff
    - SHA1:7a1dcaf4b740f821ab4a9dea642b0df978e9d4d1 [weak]
    - MD5Sum:30848041073edb5465040a2b87f0859f [weak]
    - Filesize:107808 [weak]
E: Failed to fetch http://192.168.1.93/ubuntu/pool/main/g/git/git-man_2.17.1-1ubuntu0.3_all.deb  File has unexpected size (171437 != 803016). Mirror sync in progress? [IP: 192.168.1.93 80]
   Hashes of expected file:
    - SHA256:a78f0f941932bab0c1d1ec8298a6113919f90a8527b079a2d07e4f47bb939f86
    - SHA1:f0d474273552a0e0be288bb7dfd5c231b6aa6e8e [weak]
    - MD5Sum:ab2c01aec46361a7f84391b53ef982c7 [weak]
    - Filesize:803016 [weak]
E: Failed to fetch http://192.168.1.93/ubuntu/pool/main/l/lxc/liblxc-common_3.0.2-0ubuntu1~18.04.1_amd64.deb  File has unexpected size (45101 != 415536). Mirror sync in progress? [IP: 192.168.1.93 80]
   Hashes of expected file:
    - SHA256:a2fc717e3be0e22681de75e4351d7e813d2ec6c58b4e74cf11f33f646cf5b86e
    - SHA1:1d21eed246d8412418d094be601fda86b840e683 [weak]
    - MD5Sum:29ade1f987df7f9e326ddf7efe3e17ea [weak]
    - Filesize:415536 [weak]
E: Failed to fetch http://192.168.1.93/ubuntu/pool/main/s/software-properties/software-properties-common_0.96.24.32.5_all.deb  File has unexpected size (3888 != 9912). Mirror sync in progress? [IP: 192.168.1.93 80]
   Hashes of expected file:
    - SHA256:cda0fd78df17c11093702131b65f342c4c1c55ed2b7c98f917a384b2e8902fe6
    - SHA1:1337c94b231f83bcd9b0e4b509ad9d051600cb55 [weak]
    - MD5Sum:f6f3479df983bc0d62501dc4e51edcb3 [weak]
    - Filesize:9912 [weak]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
^C
```




how do i continue ? what is the root cause of this ?

thanks :)

---

