---
title: "Update apache's openssl"
date: 2012-01-23
forum: Server Platforms
---

### Post by niels_linux_forum on 2012-01-23
Hey everybody,

I running into a problem and thought maybe somebody has some advise.

I'm running a lucid instance of ubuntu server with apache 2.2.14, currently it is using OpenSSL 0.9.8k release but I'm trying to update it to 1.0.0g. Now because this version isn't available on the official sources of ubuntu lucid. I build them my self like this:

dpkg -r --ignore-depends=ca-certificates,ssl-cert openssl
wget -c openssl1.0.0.....
tar xzf openssl
./config --prefix=/usr
sudo checkinstall -D

then using openssl version I can see my machine is using the version I installed.
Then when I restarted the apache I'm running when I went to the browser I'm still running OpenSSL0.9.8k. 
How can I solved this. I installed apache with qpt-get so shouldn't it be dynamically linked to the openssl installed ? The same with mod_ssl. Or should I reinstall mod_ssl and specify the version?

I'm quite a noob when it comes to mod_ssl and apache so hopefully somebody can point me in the right direction.

Thanks a lot,

Regards Niels

---

### Post by gigo6000 on 2012-02-03
I'm having the same problem :S

---

### Post by niels_linux_forum on 2012-02-06
> **gigo6000 said:**
> I'm having the same problem :S

Did you already find a solutions or have any suggestions on how to solve this ?

---

### Post by hawkmage on 2012-02-06
Looking at the /usr/lib/apache2/modules/mod_ssl.so it is linked to libssl.so.1.0.0.  This would make me thing that it is compiled and linked agains a specific version of ssl.  

The only way I know of to "fix" this is to build and install both OpenSSL and Apache but that leads you into a whole other set of issues when you want to update things later.

---

