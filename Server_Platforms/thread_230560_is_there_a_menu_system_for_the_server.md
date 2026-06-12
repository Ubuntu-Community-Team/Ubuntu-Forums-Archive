---
title: "is there a menu system for the server?"
date: 2006-08-06
forum: Server Platforms
---

### Post by Major-T on 2006-08-06
I am familiar with configuring systems but am more used to using a menu system rather than command line tools.

Is there a menu system can install on the server?

Regards, Major. (That is my Christian name ;-) ):confused:

---

### Post by chrisfay on 2006-08-06
[http://webmin.com](http://webmin.com) for a web based server manager.

---

### Post by Major-T on 2006-08-06
thanks for the information on webmin.
I used the link and downloaded the deb version. 
Could you tell me how to install it?
Regards, Major.

---

### Post by chrisfay on 2006-08-06
I wrote a basic howto on installing and configuring webmin (among other things):

[http://howtoforge.com/lamp_installation_ubuntu6.06](http://howtoforge.com/lamp_installation_ubuntu6.06)

It may help...

---

### Post by Major-T on 2006-08-06
thanks for that hint but when I went to the site I could not find the howto information.
Could you supply a direct URL for me?
Regards, Major.

---

### Post by chrisfay on 2006-08-06
You have to scroll down

---

### Post by Major-T on 2006-08-06
sorry about that. I can see it now.
I tried the apt-get install ubuntu-desktop and it came back with can't find package.
Is the ubuntu-desktop package part of the server distribtion?
Regards, Major.

---

### Post by chrisfay on 2006-08-06
I understand your problem now....I thought you already had a desktop and rather than using the command prompt you wanted something to help; sounds like you did the LAMP install and have nothing but the command prompt. 

Try this:

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

Then run the command to get the desktop. Did you use "sudo apt-get install ubuntu-desktop"? I don't think it would work without invoking root priveleges. 

Also, you may try editing your sources list to enable universe and multiverse repositories. I didn't think you had to though for the desktop, I did it using the apt-get and it pulled the desktop from my install cd.

---

