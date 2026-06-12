---
title: "Ubuntu Server setup &amp; configuration"
date: 2012-04-16
forum: Server Platforms
---

### Post by martago on 2012-04-16
I have been downloading all the documentation about setting up and configuring the Ubuntu Server edition, waiting for the upcoming 12.04 release.  What I have found so far is a lot of configuration definitions (networking, LDAP, firewall, etc.) that are supposed to be done by manual writing in several text files the different configuration options and information.

This type of information reminds me of the times of Novell setup and configuration, most of it had also to be done manually and involved a lot of knowledge and training.  I would expect in 2012 that Ubuntu servers had adopted the paradigm of visual and graphical setup of a server, by using wizards or whatever you may call it, to do most of time consuming tasks of putting in place a Linux server.

Tell me if I am wrong and that it is possible to find graphical tools to do most of the job of setting up a server using Ubuntu OS.

Thank you for your information.

---

### Post by lukeiamyourfather on 2012-04-16
Most see the setup with text files an advantage and a GUI as a disadvantage. This might interest you if you want a GUI to configure a server.

[http://www.webmin.com/](http://www.webmin.com/)

---

### Post by 2F4U on 2012-04-16
This is the way it works in Linux. Even if you find graphical tools, they just write in text files. And it is always good to know what text files to touch in case the graphical tools fails or doesn't provide the options you require.

---

### Post by HugoSerrano on 2012-04-16
Hello.

Ubuntu servers will never adopt the graphic paradigm... There's a lot of GUI tools around, but more packages more possible bugs, security faults, login areas to be cracked, etc! 
Those are some reasons why in 2012 Ubuntu it's still console based. And in 2012 [noparse](2008)[/noparse], MS it's going that way too... they got a powershell now! Hopefully in 2020 there will be no more GUI's!! ;-) Evolution!


Best regards!

---

### Post by martago on 2012-04-16
> **lukeiamyourfather said:**
> Most see the setup with text files an advantage and a GUI as a disadvantage. This might interest you if you want a GUI to configure a server.

[http://www.webmin.com/](http://www.webmin.com/)

Thank you for your helpful info.

---

### Post by d4m1r on 2012-04-16
Unix and linux servers have always been command line based and I don't this changed soon, if ever....Frankly, they don't need a UI anyway as you should know this stuff if you are responsible for a server anyway, and people don't see adding a UI as a potential improvement.

---

### Post by martago on 2012-04-17
> **d4m1r said:**
> Unix and linux servers have always been command line based and I don't this changed soon, if ever....Frankly, they don't need a UI anyway as you should know this stuff if you are responsible for a server anyway, and people don't see adding a UI as a potential improvement.

When one deals with Linux/Unix and nothing else, I think command line based may be the best choice.  For people like me that have to deal with several platforms, like IBM AS/400, Windows desktop and server OS with different versions, work with more than 10 computer languages, using a UI may be a good and quick way to setup a system without having to know all the intricacies of an OS as wide as Linux, at least at once and before setting up a new server.

I was always in favor of easing things to users and developers.  That's the way Canonical Software is doing with the Ubuntu project.  Until the time when we may program a computer just by talking to it, I am very in favor of graphical interfaces.

---

### Post by Jonathan L on 2012-04-17
Hi Martago

Quite a number of people are interested in graphical and web interfaces on top of the core.  A recent thread [http://ubuntuforums.org/showthread.php?t=1777965](http://ubuntuforums.org/showthread.php?t=1777965) mentions ebox and webmin, with various amounts of success, but also mentions ISPconfig.  You might be interested in following through on these
[http://www.ispconfig.org/ispconfig-3/](http://www.ispconfig.org/ispconfig-3/)

Hope that helps.

Kind regards,
Jonathan.

---

