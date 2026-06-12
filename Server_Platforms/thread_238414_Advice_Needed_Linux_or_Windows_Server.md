---
title: "Advice Needed: Linux or Windows Server?"
date: 2006-08-17
forum: Server Platforms
---

### Post by kabronkline on 2006-08-17
Hello everybody! I am currently working on a small project that will involve the implementation of a server that needs directory services capabilities (i.e., active directory/LDAP/FDS) along with file sharing (i.e., netbios/Samba) and a MySQL database for an internal application. I have debated many different ways to go about acheiving this goal. 

** Solution #1 (Not-So-Probable)**
My first instinct as a growingly avid Linux user is to setup either Debian or Ubuntu Server, install MySQL server to it, and then install something along the lines of LDAP or Fedora Directory Server along with Samba. However, I do not believe that my current abilites will prove sufficient enough to achieve proper configuration of LDAP/Fedora Directory Server to meet the needs of this small business. 

**Solution #2 (Probable)**
Considering that I was able to convince the business owner to go with a server equipped with 2 gigs of DDR2 ram along with 2 Dual-Core Dempsey 3.0 Ghz processors, my next instinct is to utilize this crazy amount of horse-power with VMWare. I beleive that I can achieve all my goals by running a host server (with a preference of either Ubuntu Server or Debian) running a guest Windows Server 2003. I made this conclusion because, as I said, I don't think I have the know-how to acheive all the same features of Windows Server with free Linux (please no flames, I'm sure it's entirely possible - it's just me).

So my question to all of you is this:
I've noticed that the Debian distro stays conservative with upgrades similar to Slackware. However, I prefer Debian way over Slackware because of the apt command. Further, I exclusively run Ubuntu for all my desktops, including laptop, and thus I am extremely familiar with it. So, what would you choose for the best native 64-bit host OS solution to my situation?

---

### Post by LordHunter317 on 2006-08-17
What exactly do you need the LDAP server for?  If it's for authenticating Windows clients on a Windows domain then just use Windows.

Otherwise, I see no reason to not use Linux.

In any event, I see no reason to run both operating systems, for sure.

---

### Post by cptnapalm on 2006-08-17
LDAP, in my very limited experience, was a serious pain.  I did finally get it up and running to the extent that logons authenticated with it, but doing anything else like changing anything such as a password, could not get it to work as I thought it would.

The reason I don't have more to add is that it was such an awful experience, that I just uninstalled it and have no interest in ever touching it again.

*IF* running Windows in a virtual server is genuinely plausible, then that might not be a bad idea.  Should anything happen to it, everything still works fine.  The MySQL part could be run natively, using the virtual networking to communicate with the Windows virtual machine.

Debian stable is, as it alwasy has been, VERY stable.  And the ability to apt-get is, of course, one of the best ways to keep up to date with security updates.

Since this is a business owner's server, who is going to be administering it?  If it is the owner, then it really would be a matter of what would be more advantageous to the owner.  If its you, then I'd say go for it with the virtual machine.  That way, as I said, if anything happens to the Windows virtual machine, the rock that is Debian stable will stay up, allowing for a speedy recovery.

---

### Post by LordHunter317 on 2006-08-17
The virtual server option is a real no good.  It's very excessive complication for no point.  You just increase your liability for no gain.

Frankly, if you don't have the time to properly learn how to setup a Linux LDAP solution, then just run Windows.  MySQL runs adequately there and AD is far eaiser to deal with, by and large.  Just make sure to properly secure it.

---

