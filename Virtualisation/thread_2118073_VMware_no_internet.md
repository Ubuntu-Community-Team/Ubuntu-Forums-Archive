---
title: "VMware no internet"
date: 2013-02-20
forum: Virtualisation
---

### Post by Namal23 on 2013-02-20
Hello, 

I have Ubuntu installed on the VMware. But suddenly I have no internet and it tells me that might be a network problem. My other two virtual machines (Xbuntu and Mint) have no such problems. I tried to search internet, restarted NAT etc but it didn't solve the problem. What can I do.

Sorry, I didn't notice that the network was disabled. I klicked enable auto ethernet and now it's fine again

---

### Post by Namal23 on 2013-02-20
Hello, strangly I still do not have internet. I can go to the browser and there it's allright. But I can't download anything with sudo apt-get or through the software manager :?

i get errors like

> Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/o/openjdk-7/openjdk-7-jre-lib_7u9-2.3.3-0ubuntu1~12.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/o/openjdk-7/openjdk-7-jre-lib_7u9-2.3.3-0ubuntu1~12.04.1_all.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.13.1.with.ckbi.1.88-1ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.13.1.with.ckbi.1.88-1ubuntu6.1_i386.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/o/openjdk-7/openjdk-7-jre-headless_7u9-2.3.3-0ubuntu1~12.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/o/openjdk-7/openjdk-7-jre-headless_7u9-2.3.3-0ubuntu1~12.04.1_i386.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/o/openjdk-7/openjdk-7-jre_7u9-2.3.3-0ubuntu1~12.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/o/openjdk-7/openjdk-7-jre_7u9-2.3.3-0ubuntu1~12.04.1_i386.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/o/openjdk-7/icedtea-7-jre-jamvm_7u9-2.3.3-0ubuntu1~12.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/o/openjdk-7/icedtea-7-jre-jamvm_7u9-2.3.3-0ubuntu1~12.04.1_i386.deb) 404  Not Found [IP: 91.189.92.200 80]

Edid: ok now I found the solution 

[http://askubuntu.com/questions/73997/how-do-i-fix-a-failed-to-download-package-files-error](http://askubuntu.com/questions/73997/how-do-i-fix-a-failed-to-download-package-files-error)

---

### Post by dcstar on 2013-02-22
> **Namal23 said:**
> 
.......
Edid: ok now I found the solution 


Then MARK the thread.

---

### Post by Namal23 on 2013-02-28
Sorry, but today I have same problem. Now absolutly nothing works. I do not know what to do.

---

### Post by Namal23 on 2013-02-28
Sorry, but today I have same problem. Now absolutly nothing works. I do not know what to do.

---

