---
title: "Ubuntu server gui"
date: 2010-11-21
forum: Server Platforms
---

### Post by metzy85 on 2010-11-21
Noobie here. Thought I would try out ubuntu server. I am ok at command line but not amazing by any means. I think I got the gui installed but how do you start it?

---

### Post by lisati on 2010-11-21
If the regular Gnome gui is there, the following often works wonders:
```
startx
```

---

### Post by rbishop on 2010-11-21
I wouldn't load the gui unless you absolutely had to.  I recommend using Webmin it is a web based utility for controlling most every aspect of your server without adding any major load to the CPU.

```

wget http://prdownloads.sourceforge.net/webadmin/webmin-1.450.tar.gz

tar -xvf webmin-1.450.tar.gz

cd webmin-1.450/

./setup.sh

(use defaults for most options)

```
Once installed just browse to your server ( [http://server-ip:10000](http://server-ip:10000))

---

### Post by Lloyd_mcse on 2010-11-21
Can I manage files through this, like editing Apache, courier-imap files etc.
Sorry I'm really new to this, but I'm loving working with ubuntu so want to get the most out of it.
Thanks for any info
regards
 
Lloyd

---

### Post by rbishop on 2010-11-21
> Can I manage files through this, like editing Apache, courier-imap files etc.Yes you can manage and edit most every file you need from Webmin.

---

### Post by Lloyd_mcse on 2010-11-21
> **rbishop said:**
> Yes you can manage and edit most every file you need from Webmin.
 
Exellent, thanks :D 
Do you know if I can use it with Plesk already installed?
Thanks once again

---

### Post by rbishop on 2010-11-21
I have never used Plesk so I couldn't say if it works with it or not.  When you setup Webmin you are able to specify what port you can use it on.

The default port is 10000

---

### Post by HermanAB on 2010-11-22
Howdy,

If you want a server GUI and you don't like Webmin on Ubuntu, install OpenSuse or Mandriva Linux, they have proper wizards for everything.

---

### Post by Spice Weasel on 2010-11-22
> **HermanAB said:**
> Howdy,

If you want a server GUI and you don't like Webmin on Ubuntu, install OpenSuse or Mandriva Linux, they have proper wizards for everything.

CentOS, Scientific Linux and RHEL have tools like this too. Great for newbies to the *nix server world. In the long term though, it is great if you can learn the CLI.

---

### Post by yettiman2208 on 2010-11-22
I recomend the Webmin interface. It is helpful enough when in a Jam, but not completely accessible where you will never learn the CLI.

I recomend doing all setup through the command line. SSH in to your box and run it headless.
It will hurt at first, but I promise, within a few hours you'll be all over the command line and have a better understanding of the way unix systems work.

I speak from experience, when I decided to set up a server I purposely chose to do everything through the CLI with very little actual CLI experience. It worked wonders. Furthermore, when Webmin doesn't act as I want, I generally know why, and how to accomplish the task without Webmin.

Go at it! you will learn. Google is your best friend to FAST question answering.

---

### Post by E-call on 2010-11-22
i also reccomend using Webmin its great for starters and likeprevious posters said you can edit most anythng that you need with it.
 
a great resource for starting with Webmin can be found at [http://www.woodel.com/](http://www.woodel.com/)
 
its a guide for use with Debian but most everything carries over.
 
good luck

---

### Post by kevinthecomputerguy on 2010-11-30
+1 to E-call
 
:- )
 
-KevinTheComputerGuy

---

