---
title: "Server Problems"
date: 2007-03-29
forum: Server Platforms
---

### Post by novice1 on 2007-03-29
I apologize in advance for the length this post is liable to be - I would rather give too much than not enough information. i am new to Linux but so far have managed to successfully install and set up a wireless workstation, and a Samba/DNS server.  I just finished installing  as second Ubuntu server (LAMP) which I am attempting to configure as a secure post office server -- following a HowTo at this link [http://flurdy.com/docs/postfix/#install_distro](http://flurdy.com/docs/postfix/#install_distro).  Using apt-get to install the the packages that were not installed during the basic LAMP server install. I also had Webmin and SSh server installed and was accessing the server by Webmin and sometimes Putty SSH to install and setup the various packages.  The first thing I needed to configure was the Shorewall and was using Webmin to begin the process.  I had the sample configuration files in the Shorewall directory and was going through the zones, interfaces, rules and permissions beginning to modify them to meet my network configuration and requirements. I realized that I had not installed a second Ethernet NIC -- so I shut the server down normally with out incident and installed the second NIC.  When I booted up the Server startup finished leaving me at the ROOT user prompt. It never asked me to login as it always had in the past. I can issue cd commands and go anywhere int he file system with ROOT power -- I found I could edit any file I wanted I can login by mu user name and password but I am very uncomfortable with the server starting up with no login required and at the ROOT. I also had to reinstall Webmin to get it to work and SSH connections with Putty fail -- I am not sure why that is.  

I said all the above to ask: what can I do to get the server to boot up as it did before to a user login prompt, that would not require a reinstall of the Server and all the other packages I have installed so far?  Any help would be appreciated.

[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

---

### Post by huygens on 2007-03-29
I won't be of any help :-( but I think I know why you're logged in as root without being prompt to log in.
There is a problem in the boot process which make it fails, and a safe mode session starts where you are automatically logged in as super user (a.k.a. root). Probably most services are not running (which could explain why you couldn't use SSH). The system is waiting for you to solve the problem so that it can boot normaly and show you the log-in prompt.

My bet would be that you go under /var/log and read the file messages:
```
cd /var/log
less messages
```
And check for error. If you found errors, you could post them here, and perhaps we could help you :-)

Good luck!

---

### Post by novice1 on 2007-03-29
> **huygens said:**
> I won't be of any help :-( but I think I know why you're logged in as root without being prompt to log in.
There is a problem in the boot process which make it fails, and a safe mode session starts where you are automatically logged in as super user (a.k.a. root). Probably most services are not running (which could explain why you couldn't use SSH). The system is waiting for you to solve the problem so that it can boot normaly and show you the log-in prompt.

My bet would be that you go under /var/log and read the file messages:
```
cd /var/log
less messages
```
And check for error. If you found errors, you could post them here, and perhaps we could help you :-)

Good luck!

You are right here. I rebooted and escaped to the Boot menu -- The is No selection for the server Kernel except the Recovery Mode and memory test.  I did the less message command and got so many lines it took me forever to read them -- at the moment I have not quite figured out how to copy them and post them -- I think I see a couple of obvious failures but I will have to re-run less messages and pick them out because I think the entire syslog is too long to replicate it here.  Thanks for the hint and I will be back with more info as after I gather it.

---

### Post by huygens on 2007-03-29
> **novice1 said:**
> I rebooted and escaped to the Boot menu -- The is No selection for the server Kernel except the Recovery Mode and memory test.

It seems that your grub menu is lacking some entries...
What you could do is: go under /boot/grub and re-view the menu.lst file. If you know how to edit it to add your missing entry, do so (but always with extreme precautions).
You could try also to recreate automatically the grub menu... I'm not sure how to do it, I would guess 'sudo dpkg-reconfigure grub' but before you execute this command, you should check in the [wiki]("https://help.ubuntu.com/community/") or [other places]("http://doc.gwos.org/") for confirmation ;-)

---

### Post by novice1 on 2007-03-29
Well in the final analysis I decided to wipe out the installation and reinstall Edgy Server -- it only took an hour to get back to where I was before I encountered the problem and the second Ethernet NIC came up just fine. I figured it would take hours for me to figure out what was wrong with the original installation and correct it so it was easier to cop out and just start over. The only sad thing is I missed out on a good learning opportunity!  Troubleshooting always teaches me something new.  

Thanks for the advice it was right on the money and i learned something too! So not a total loss.  This is a home network and for the moment I am not hurting any over this.

---

### Post by huygens on 2007-03-30
OK, I'm glad you have found a solution out of your problem, even though not the best one. In the end what matters is that it is working, isn't it? ;-)
Good luck with your server :-)

---

