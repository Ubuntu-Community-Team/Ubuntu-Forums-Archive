---
title: "How can I remotely install Ubuntu on a server?"
date: 2006-08-15
forum: Server Platforms
---

### Post by sclough on 2006-08-15
Here's my problem.  I want to run ubuntu on a dedicated server, but the hosting company only supports Fedora, Centos, RHEL, and plain debian.  They mentioned a while back they did a basica Fedora install for a customer and then the customer did an ssh and was able to install the os they wanted.  I'm not quite sure how that would work, but what I'm wondering is if there is a way for me to have them do that and then install Ubuntu over it on an ssh connection?

I guess I'm confused about how I would run a Ubuntu install in a running Fedora (or other OS) instance?  Is this possible?

---

### Post by lvanderree on 2006-08-15
I think it is possible, 

the partition of Fedora should be small, or at a size you can re-use for an other mount in your new ubuntu installation.
( [https://help.ubuntu.com/community/forum/installation/Partitioning](https://help.ubuntu.com/community/forum/installation/Partitioning) )

Then I think you can do something as described here:
[https://help.ubuntu.com/community/Installation/FromKnoppix](https://help.ubuntu.com/community/Installation/FromKnoppix)

But I never have done this myself!

here are some more install options:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by BakCompat on 2006-08-15
Hmm, you can do a network install on a machine that you have local access to. This would be done via a floppy or versy small ISO on a cd.. It would load a minimal kernel and network access. Then you would be able to connect to various repositories to download the packages for the full install.. The only difference here is that you are getting the packages via network instead of from cd. It could be local netowkr or internet for that matter. 

Now, as to remote installations, sorry, not where you're looking. There is technically a way to do it with say a PIX server or something along those lines, but that is really for corporate environments.. kinda like a PXE network boot.. The machine just talks to another server that already has the files in a preconfigured setup and grabs them.

For remote connections, the best you can hope for would be to have them do a baseboard install of *any* distro, load SSH, and then you can SSH in and config to yer hearts content. That will allow you to customize whatever distro they install there for you. SSH would allow you to apt-get all yer updates. You could do something like webmin or CPanel type apps to give you remote gui access, but those are a bit more specific and geared towards managing certain aspects of the box.

Um, from whats stated above, you could give a try, but it tends to go above and beyond "true" remote installations. Still, if you are daring and your hoster is willing to give you that support, then i'd say go for it and give it a try. Me personally, i'd limit to local access as much as possible.

---

### Post by sclough on 2006-08-15
Actually, the instructions for [booting from Knoppix]("https://help.ubuntu.com/community/Installation/FromKnoppix") look like they would work.  My situation is that the machine will be booted into another OS, say Fedora, and I only have access to the box over the internet so I can't do any booting off of CDs, NFS, etc.

It seems like I could follow the Knoppix instructions, make sure I also ran apt-get for ssh and then I should be able to reboot into Ubuntu and just kill the original fedora partition and use it for something else later.

Can anybody confirm if the Knoppix instructions will work on Dapper?  This is basically the way you install Gentoo, so I've done something similar before, I just don't want to run into any bugs because if it doesn't work, the hosting provideris  probably not going to be a lot of help since they don't support the os.

---

### Post by stormblue on 2006-08-15
Why not just do a debian install?  Ubuntu is based on debian so the config files are going to where you expect them and the webhosting supports it.  This seems the way to go.

---

### Post by sclough on 2006-08-15
Now that actually makes sense and I feel kinda stupid for not thinking of that.](*,)   This is a really dumb question, but if I had them do a bare-bones install, what would it take to "convert" it to dapper server?

---

### Post by cofin on 2006-08-17
If it is a Debian install, I would assume that one would only need to change the sources.list over to the ubuntu repositories, and do apt-get dist-upgrade (I think that is the syntax, I am still learning things myself).  Hope that helps there, but I am also looking for a way to do a complete headless install.  This would be very convenient given the setup I have.  Anyone else actually install ubuntu this way?

---

### Post by sclough on 2006-08-17
One would think you could.  I installed Sarge on a VMWare machine and I'm currently trying.  I replaced the sources and did an apt-get update and then an apt-get dist-upgrade.  It replaced a lot of stuff and was running good until it got to the kernel and errored.  Oddly enough, it was there I discovered my sarge install used a 2.4 kernel (?) and I'm only seeing 2.4 kernels as options in apt-get.  I'm not sure why I'm not seeing the normal dapper 2.6 kernel.  Anyway, right now I'm trying to do an apt-get install ubuntu-base to make sure everything is set to ubuntu.  That install is overwriting a lot of stuff.  Hopefully, I can turn sarge into dapper, but we'll see.  Just to be honest, I'm doing everything over an ssh connection to the VM machine so I'm simulating doing this remotely.

---

### Post by sclough on 2006-08-17
For some reason I'm getting this:
```
(Reading database ... 14094 files and directories currently installed.)
Unpacking lvm2 (from .../lvm2_2.02.02-1ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/lvm2_2.02.02-1ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 10
Errors were encountered while processing:
 /var/cache/apt/archives/lvm2_2.02.02-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The problem is that I don't know if this package won't install because of my sarge-> ubuntu process or because of the VM Ware filesystem.  The install did ask me about starting raid and monitoring it and I said yes because I didn't know if the machine was thinking that VMWare was providing a raid set of disks.  Anyway, I guess I'm stuck here unless I can find a way to solve this.

---

### Post by sinaen on 2006-08-18
I would like to try to switch to ubuntu on my debian stable server in my closet. but, what repositories does it have, and how do i maintain so that it doesnt rewrite some configfiles about my network-shares?
then i would also gladly like to know about which packages that is installed when installing a ubuntu server? does anyone know that?

---

