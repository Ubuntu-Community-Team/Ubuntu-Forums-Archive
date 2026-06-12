---
title: "which version of samba should i use"
date: 2011-04-02
forum: Server Platforms
---

### Post by wlraider70 on 2011-04-02
I'm trying to do some new stuff with samba and im running into a lot of versions.


I have 3.4.7 and apt-get says this is the newest version. 
I have seen 3.5.x and also 4.x (is that a beta)

Which one should i go with? Do I have to build the newer ones from the code?

-----

Also I appear to have a conflict


luke@media:/etc/init.d$ smbclient --version
Version 3.4.7
luke@media:/etc/init.d$ sudo /etc/init.d/samba4 reload
[sudo] password for luke: 
Usage: /etc/init.d/samba {start|stop|restart|force-reload}
luke@media:/etc/init.d$ sudo /etc/init.d/samba4 stop
 * Stopping Samba 4 daemon samba                                                                                                                                 [ OK ] 
luke@media:/etc/init.d$ sudo /etc/init.d/samba4 start
 * Starting Samba 4 daemon samba                         

---
As I read it the version command it telling me i have 3.4, but i have the samba 4 daemon?
What do i do there?

---

### Post by pdwerryhouse on 2011-04-02
Unless you have a particular feature that is needed by either 3.5 or by the 4.0 beta - and this is highly unlikely - then you should use the version of Samba that is provided in the Ubuntu distribution.

This will make security management much easier, because when there is an upgrade, you'll be able to install the new version provided by Ubuntu simply with apt-get and you can be sure that the changes have been backported to the update and won't break anything on your system.

Take it from me; having to compile and install a new version of anything, every time it is released, is simply going to make your life far more complicated than it needs to be.

---

### Post by pdwerryhouse on 2011-04-02
Sorry, I also just noticed that Ubuntu provides both samba (3.4.7) and samba4 packages.

Again, unless you have a need for the features in samba4, go with 3.4.7.

---

### Post by Morbius1 on 2011-04-02
From Synaptic:
> These packages contain snapshot versions of Samba 4, the next-generation version of Samba. These should be considered _experimental_, and should not be used in production. In particular, no guarantees are made with regard to upgrades between versions.If you want to install Samb4 after reading that then you're a better man than I. :wink:

---

### Post by wlraider70 on 2011-04-06
I am not a better man than you.

Thanks for the info all.

---

