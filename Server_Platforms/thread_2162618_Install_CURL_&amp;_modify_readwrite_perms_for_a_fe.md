---
title: "Install CURL &amp; modify read/write perms for a few files"
date: 2013-07-15
forum: Server Platforms
---

### Post by IceChessMeteor on 2013-07-15
Hey there,

I am currently assisting as a technician for a growing business that uses a Ubuntu server.
To help with enabling users to pay securely I have been asked to install an applications which requires installation of CURL.  This is to enable to run the WHMCS.
However, when trying to add install this application I get these following issues (screenshot below):

 - CHMOD: not a command
 - CURL not detected


I am happy to give any details required however I am needing help/support with this request.

Is this possible?  Any assistance would be greatly appreciated.

[IMG]http://f1716.mail.vip.ir2.yahoo.com/ya/download?mid=2%5f0%5f0%5f1%5f142237%5fAL5TfbwAAAYdUePviwAAAB2fgSM&pid=2.2&fid=Inbox&inline=1&appid=yahoomail[/IMG]

---

### Post by Cheesemill on 2013-07-15
To install curl for PHP run the following command...
```
sudo apt-get install php5-curl
```

The other error isn't saying that chmod isn't installed on your system (it is). It's telling you that you need to set the correct permissions on specific files to continue with the installation. For example...
```
sudo chmod 755 /path/to/configuration.php
```
Obviously replacing /path/to with the correct location for your filesystem.

---

### Post by IceChessMeteor on 2013-07-16
Thank you very much for your quick response
your advise was exceedingly helpful and I was able to get the application running smoothly :)

Thank you

---

