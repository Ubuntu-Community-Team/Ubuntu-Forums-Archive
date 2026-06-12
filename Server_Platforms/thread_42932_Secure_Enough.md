---
title: "Secure Enough?"
date: 2005-06-20
forum: Server Platforms
---

### Post by Linux_Noobie on 2005-06-20
Is Ubuntu Secure enough for a good Server? Possibly with a lot of important info that CANT be destroyed. I was Using My normal WinXpPro for a server and got horribly Hacked they deleted everything.Right down to The Os. So im gonna try to have A secure server now. But How can i make Ubuntu Secure enough For a **Good** Server that WONT get hacked. I dont want the Windows for a server thing to happen again. Please Help Me. People on a forum i go on a lot (My hosts forums) told me if i wanted a server Linux/Unix was a requirement but i did'nt listen. :roll:  ](*,)

---

### Post by defkewl on 2005-06-20
If you want a really secure server than I would recommend you [OpenBSD](http://openbsd.org) . :)

---

### Post by blind0wl on 2005-06-20
Well, youve got a long way to go...hehe.

WinXP can be ok for a server as long as the necessary security updates are performed and the obvious bad security related services disabled.

Linux/Unix can/is just as easy to get into if the administrator hasnt performed the required security functions that should be in place.

Most hacking problems can be resolved with a good firewall configuration (assuming the server is on the net).  Theres a lot of doco on how to best secure a server, which a google search will help with, but it all depends on what the server is doing primarily, where its located and who should be allowed to access it.

If you can elaborate on what its for, I may be able to help more....

A good backup system will make sure you never lose that info....I dont think anyone would place a definate bet on keeping data on a server thats not backed up or clustered in any way.

HTH

Blindy

---

### Post by ziggyboy on 2005-06-20
[QUOTE=Linux_Noobie]Is Ubuntu Secure enough for a good Server? Possibly with a lot of important info that CANT be destroyed. I was Using My normal WinXpPro for a server and got horribly Hacked they deleted everything.Right down to The Os. So im gonna try to have A secure server now. But How can i make Ubuntu Secure enough For a **Good** Server that WONT get hacked. I dont want the Windows for a server thing to happen again. Please Help Me. People on a forum i go on a lot (My hosts forums) told me if i wanted a server Linux/Unix was a requirement but i did'nt listen. :roll:  ](*,)[/QUOTE]
 I would just like to add that the security level of most Linux systems are similar. What you might want to know is how secure a **default installation** is. If you know how to configure a Linux server, you can turn even the most unsecure distro to a secure one (through upgrading packages, setting good firewall rules, disabling "fishy" services, etc.). Because honestly, most distros have the same packages anyway.

---

### Post by LordHunter317 on 2005-06-20
[QUOTE=ziggyboy] If you know how to configure a Linux server, you can turn even the most unsecure distro to a secure one (through upgrading packages, setting good firewall rules, disabling "fishy" services, etc.). Because honestly, most distros have the same packages anyway.[/QUOTE]It's not that simple.  Older versions of distributions can be impossible to secure without rebuilding everything from source by hand.

---

### Post by ziggyboy on 2005-06-20
[QUOTE=LordHunter317]It's not that simple.  Older versions of distributions can be impossible to secure without rebuilding everything from source by hand.[/QUOTE]
 I'm obviously referring to latest releases of each distro.

---

### Post by desdinova on 2005-06-20
I would first make yourself comfortable with Linux before thinking of making a publicly accessible server. Even though the basic install of Linux is easy, hardening any server is a complex task and can approach being a black art ;-) Even for things like OpenBSD, you still need to understand what you're doing....

---

### Post by mmealman on 2005-06-22
[QUOTE=Linux_Noobie]Is Ubuntu Secure enough for a good Server? Possibly with a lot of important info that CANT be destroyed. I was Using My normal WinXpPro for a server and got horribly Hacked they deleted everything.Right down to The Os. So im gonna try to have A secure server now. But How can i make Ubuntu Secure enough For a **Good** Server that WONT get hacked. I dont want the Windows for a server thing to happen again. Please Help Me. People on a forum i go on a lot (My hosts forums) told me if i wanted a server Linux/Unix was a requirement but i did'nt listen. :roll:  ](*,)[/QUOTE]
 Yes Ubuntu is secure enough. Just keep it up to date using apt-get, select a good password for yourself and leave root locked. A default Ubuntu install is more secure than most Linux distributions out there.

---

### Post by LordHunter317 on 2005-06-22
[QUOTE=mmealman]\ A default Ubuntu install is more secure than most Linux distributions out there.[/QUOTE]The problem is a lot of essential server stuff is in universe, so the bigger question is will it remain that way as time goes on?

---

### Post by mmealman on 2005-06-22
[QUOTE=LordHunter317]The problem is a lot of essential server stuff is in universe, so the bigger question is will it remain that way as time goes on?[/QUOTE]

I thought universe still saw updates, just not from Canonical. It always comes down to trusting your maintainers. If Debian, Red Hat or SUSE doesn't update quickly enough, you're just as screwed.

---

### Post by billiejoex on 2005-06-22
The secret is the daily automatic-update. :) 
```

 $ sudo gedit /root/.autoupdates
----------------------------------------------------------------------------------------------------------------
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
/usr/bin/apt-get update
/usr/bin/apt-get -y upgrade
----------------------------------------------------------------------------------------------------------------

 $ sudo chmod 500 /root/.autoupdates
 $ EDITOR=vi  
 $ sudo crontab -e

set an hour:

 mm hh * * * /root/.autoupdates

```

---

### Post by LordHunter317 on 2005-06-23
That's not a good upgrade script.  Think for a second and you'll realise why.


Blindly answering yes to every option presented isn't a great idea.

---

### Post by billiejoex on 2005-06-23
Sorry. I'm not sure to understand. :\

---

### Post by jdonnell on 2005-06-23
Real security is constant work, it's not a switch you can flick, a product you can buy, or a distribution you can download. The most imortant thing is keeping your system updated and ubuntu makes this very easy. Then make sure you use really good passwords. LordHunter showed me in an earlier thread that passwords I thought were strong really aren't. Make a long password with numbers and speical characters and **change it frequently**. 

After that the real work begins. You have to learn a lot about security and system administration if you really want to keep it secure. I don't mean to make it sound so overwhelming, but it is if you REALLY want a secure server. I don't do all these things myself for my home server. I just keep it updated, use good passwords, and have it behind a firewall. This reduces the chances of it getting hacked, but it's still very possible. But if it does I'll just wipe the box and start over because I have backups of my important data that gets pushed to a different machine.

---

### Post by desdinova on 2005-06-23
[QUOTE=billiejoex]Sorry. I'm not sure to understand. :\[/QUOTE]

Blindly updating like that is a recipe for disaster - the trick is to monitor the updates and only install those that are relevant.

I'll second the thing about Security being a state of mind - and recommend the O'Reilly book Esssential System Administration as an excellent primer into what sysadmin'ing your own secure box is all about.

---

### Post by loon on 2005-06-23
Honestly,

There is no such thing as a 100% secured computer. 
Even if it isn't know the internet or lan, it can still be accessed through sneaker net (like that old school terms?? heh)

The main thing about setting up servers is such is how well you well secure, and have a disaster recovering plan. You have to have policies ready to go at anytime. You have to know it's gonna happen, but how are you going to recover the lost time or deal with the situation is what is key.

---

### Post by savage on 2005-06-27
I just wanted to add something into this conversation as someone who is in a similar situation. Being a linux newbie and trying to administer a webserver is hard business, there is alot of ground to cover. I would suggest that until you gain the knowledge that you may want to review using a solution that will help you learn linux, without being under the gun trying to become a sysadmin overnight.

Look around at all the virtual server type plans that you can host under now. You can get yourself a linux webserver for real cheap, under $20 per month. Now it doesn't have everything, and you can't always configure all the settings, some hosts allow more than others. However you don't have to worry about updates, and security. Make sure to get an account that uses SSH then you can still gain alot of knowledge for running a webserver, without all the pre-requisite know how. At the same time build a server that you absolutely don't care for, exclude it from the rest of your network if possible, and learn the ropes on it. Best case scenario is to find a host that has unlimited support email. Tap the host support for help when you absolutely get stuck, and now you're really stretching your training dollars.

There are many strategies you can use to approach learning linux. Jumping straight into administering a webserver for a newb is insanity. Starting with single locally networked system is probably much easier. Can anyone tell me how to escape this straight jacket?

---

### Post by sesstreets on 2005-07-01
I have to agree with him on that, although I learned linux a different way. I used Slax and used its wonderful live boot system to explore linux. Then I upgraded my experience to fedora 3 with a dedicated machine on my network, then I tried Gentoo, freeBSD, Debian, and now Im on Ubuntu

---

### Post by stilus on 2005-07-06
As you will read in every howto/ manual and has been said again here, securing any network, desktop, server or whatever is not a goal, but a path. Having said that, take a look at [http://www.debian.org/doc/user-manuals#securing](http://www.debian.org/doc/user-manuals#securing)

You might find some relevant info there...

Good luck and have fun!

---

### Post by nocturn on 2005-07-06
Some easy tips for a server.

Put /home /boot /tmp on seperate partitions.
/home can do with nodev, nosuid (run commands as root, without sudo).
/tmp is best with nosuid, nodev, noexec (do not allow executables there, this stops a lot of rootkits dead cold).

Mount /boot read only.  Remember to mount -o remount,rw when you need to update kernels!  

[quote=me]
/tmp can contain files from all users on the system. The sticky bit on a directory can be set to avoid the possibility of files in that directory being deleted by a user who has write permissions on the directory. The sticky bit limits file deletion to the file owner and root.

To set the sticky bit:

# chmod +t /tmp
[/quote]

---

### Post by LordHunter317 on 2005-07-06
[QUOTE=nocturn]Put /home /boot /tmp on seperate partitions.[/quote]This isn't necessarily a security gain.

> /tmp is best with nosuid, nodev, noexec (do not allow executables there, this stops a lot of rootkits dead cold).It also can stop other applications dead cold too.

> Mount /boot read only.  Remember to mount -o remount,rw when you need to update kernels!Having a /boot unless you're using somethign that requires it is silly.

---

