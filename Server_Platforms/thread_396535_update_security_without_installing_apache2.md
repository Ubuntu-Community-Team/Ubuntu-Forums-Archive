---
title: "update security without installing apache2"
date: 2007-03-29
forum: Server Platforms
---

### Post by waffe on 2007-03-29
Hi,

I have been using Ubuntu for a web server for over a year now. I update the security by going to /etc/apt/source.list and opening up this line deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted. I then use the commands:
Apt-get update
Apt-get upgrade 

All of this seems to work except when the process is done Apacahe 2 has been installed and then I have to unistall it and reinstall apache 1.3.

So, is there a way around this problem / is this the correct way to update Ubuntu?

Thanks,

waffe

---

### Post by huygens on 2007-03-29
You should look at aptitude instead of apt-get. It is a replacement of the second and you can force to keep a version of certain package while upgrading.
However, I'm not personally using it, so I cannot help you further, but you could use the man command the the Ubuntu documentation, the following entry is a good starting point: [https://help.ubuntu.com/community/AptitudeSurvivalGuide](https://help.ubuntu.com/community/AptitudeSurvivalGuide) eventhough it won't explain you your specific need, but it has further pointers...

---

### Post by waffe on 2007-03-30
Thanks huygens,

I will look into it!

waffe

---

