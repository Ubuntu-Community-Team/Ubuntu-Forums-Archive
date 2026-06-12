---
title: "make a gui for Lamp desktop"
date: 2008-04-16
forum: Server Platforms
---

### Post by dsiembab on 2008-04-16
Good afternoon,
I am coming from using wampserver on windows and was wondering what programming language I would have to use to make a gui like wampserver. Something to start stop and look into my files that I have at the web root. I currently have ubuntu 7.10 desktop edition and lamp installed by tasksel the lamp installation seems to be in working order. I know there is already a gui for starting and stopping apache I was just wondering if someone could point me in the right direction. Thanks

---

### Post by fazavon on 2008-04-16
have you looked in to Webmin?

webmin.com I believe that new one is 1.410

I have used it for years and it has done all I needed and then some.

---

### Post by jpeddicord on 2008-04-16
> **fazavon said:**
> have you looked in to Webmin?

webmin.com I believe that new one is 1.410

I have used it for years and it has done all I needed and then some.

Webmin for me has been a love/hate relationship. There are some things that I find useful, but many others that really raise a stink on a server. If you use it, be sure to make sure only you can access it via iptables or Apache allow/deny trickery.

If I were to write my own, I would do it in Python, since so many Python libraries are already available for interacting with system services in addition to web frontends.

---

### Post by dsiembab on 2008-04-16
basically the lamp is set up to only be used for testing php and it will never be a production server. so i would just make a gui for scanning local files and directories with a couple of  buttons to run commands to autostart phpmyadmin and stuff like that my computer is a pentium 4 3.0ghz with 1.5 gb of ram so I am not worried about resources. thanks for the advice.8-)

---

### Post by dmizer on 2008-04-16
> **dsiembab said:**
> basically the lamp is set up to only be used for testing php and it will never be a production server. so i would just make a gui for scanning local files and directories with a couple of  buttons to run commands to autostart phpmyadmin and stuff like that my computer is a pentium 4 3.0ghz with 1.5 gb of ram so I am not worried about resources. thanks for the advice.8-)

then you don't need the server install.  you need to install the full version of ubuntu or xubuntu which have gui, and then install the apache, php, and mysql programs on that.

much safer (as far as system reliability is concerned) to install a lamp server on a gui than it is to install a gui on a server install.

---

### Post by dsiembab on 2008-04-16
yes I already have the full ubuntu on my computer I was just looking for a way to easily start apache and adjust the settings without using terminal. instead of /usr/sbin/apache2ctl stop or restart  or start a one click button to make these things happen a gui with an assortment of buttons one to view my files at www on to view my php information , apache information and one to view my mysql information not a desktop gui a user interface for the desktop where I just click an icon and a tiny control panel pops up and lets me check the status of my server and to restart or stop it. I mean why mouse type mouse type when you could just mouse mouse and then type Like I said I am a lazy man. When you go to a website through your browser and you had to type everything you wanted to do would you keep visiting that website or use one that was more user friendly. Personally I think an operating system should be made of gui's with terminal for a back up. in the real world if you are not user friendly and easy to pick up you usually sit by yourself no one is going to spend time trying to figure you out because there is always more than one to waste your time on.

---

### Post by dmizer on 2008-04-16
then you want a web based server management interface like [webmin](http://www.webmin.com/) or [virtualmin](http://www.virtualmin.com/) neither of which are available in the ubuntu repositories as far as i know.

webmin has severe security concerns, so it should never see the light of the internet. but, that shouldn't be a problem in your case.  i know nothing about virtualmin.

alternatively, you could go to:
administration > services

and start/stop apache from there.

---

### Post by dsiembab on 2008-04-17
thanks dmizer appreciate it:) I have tried webmin and I can see the security problems with opening up a port to command your server. I'm just going to play with python and glade and see if I can bring some fruition to a thought. Now the fun part of integrating the zend framework with the server. the other thing is if I want to keep my programming above the web root and bootstrap it.I might just keep a folder on my desktop and put it in their and make a folder in the desktop folder my document root.:-({|= now that is the worlds smallest violin and it's playing my song. thanks again for your help.

---

