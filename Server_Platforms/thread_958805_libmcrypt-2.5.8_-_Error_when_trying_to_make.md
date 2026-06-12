---
title: "libmcrypt-2.5.8 - Error when trying to make"
date: 2008-10-25
forum: Server Platforms
---

### Post by zitcon on 2008-10-25
Hi

phpMyAdmin wants me to install the mcrypt plugin for PHP .

First I've tried the obvious ;
apt-get install mcrypt

- It said it was installed, but according to phpmyadmin it wasn't ( Yeah, I have restarted apache ) .

Then I went online , found [this](http://www.techsww.com/tutorials/libraries/libmcrypt/installation/installing_libmcrypt_on_ubuntu_linux.php) guide :
[http://www.techsww.com/tutorials/libraries/libmcrypt/installation/installing_libmcrypt_on_ubuntu_linux.php](http://www.techsww.com/tutorials/libraries/libmcrypt/installation/installing_libmcrypt_on_ubuntu_linux.php)

At first I got some errors , but then I installed gcc and g++ and everything seemed to go fine , but when I restarted apache , it still did not work , then I tried to install the libltdl package .
This time I restarted apache, then the whole server , and it was still not working ..

Anyone know what to do ?
Ubuntu Server 8.04 LTS

If you guys need some logfiles , just tell me wich one and I will upload them ..

Thanks

---

