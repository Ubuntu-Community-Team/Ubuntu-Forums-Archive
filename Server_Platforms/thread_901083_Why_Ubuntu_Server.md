---
title: "Why Ubuntu Server"
date: 2008-08-26
forum: Server Platforms
---

### Post by lynx_hanan on 2008-08-26
Hi Guys

i have been using Ubuntu As a desktop alternative for quite a while know. And the reasons for it are obvious like u all know. It just simply rocks. I have recently been hired by a company and my assignemnt is to choose an operating system for there servers. I want to recommended ubuntu server to them. But i have never used Ubuntu Server. I have some knowledge of Redhat EL 4 & 5. Can anyone plz tell me whats are the reasons that My company should shift to ubuntu for their servers . What are the benefits in terms of Support, Value for money, Security, reliability, Robustness, And Kernel and software tools available as compared to REDhat , suse server flavours, Thank you

---

### Post by sonicb00m on 2008-08-26
I actually use Debian 4 when it comes to the servers. I am not against Ubuntu Server at all (I actually use the server kernel on my desktop to get 4gb of ram in 32bit rather than 3gb with the desktop kernel).

The main reason I use Debian 4 is all the setup and configuration guides cater very well for this distro at howtoforge.com. Most are compatible with ubuntu server as well but there are some differences with drivers (when it comes to RAID as I read today) between U/S and Debian 4 (U/S lacking certain important raid features).

I would say if you are comfortable setting up a server using apt-get then that would be a big reason for going Debian or Ubuntu. I would actually struggle to change and setup another distro.

Debian is also more "stable" than Ubuntu Server and I would guess you would want to go to an LTS version for a stable server rather than the 6 month updates. 

I can't really add value to what is better over the OSs that you already mentioned.

If you feel that you can provide adequate support and configure their servers to their needs with any of the distros then chose the one you are most comfortable with in configuring and supporting.

---

### Post by gtdaqua on 2008-08-26
> **sonicb00m said:**
> I actually use Debian 4 when it comes to the servers. I am not against Ubuntu Server at all (I actually use the server kernel on my desktop to get 4gb of ram in 32bit rather than 3gb with the desktop kernel).

The main reason I use Debian 4 is all the setup and configuration guides cater very well for this distro at howtoforge.com. Most are compatible with ubuntu server as well but there are some differences with drivers (when it comes to RAID as I read today) between U/S and Debian 4 (U/S lacking certain important raid features).

I would say if you are comfortable setting up a server using apt-get then that would be a big reason for going Debian or Ubuntu. I would actually struggle to change and setup another distro.

Debian is also more "stable" than Ubuntu Server and I would guess you would want to go to an LTS version for a stable server rather than the 6 month updates. 

I can't really add value to what is better over the OSs that you already mentioned.

If you feel that you can provide adequate support and configure their servers to their needs with any of the distros then chose the one you are most comfortable with in configuring and supporting.

Ubuntu is rock-solid stable too; its not as compact as debian. So, this has advantages and disadvantages. For e.g. I couldnt get latest megaraid_sas driver compiled on debian. Ubuntu editions are more comfortable in getting these things working.

The LTS editions enjoy support for 5 years - ideal for mission critical servers which require minimal interruption. The other server editions are strong too helping you leverage the then latest kernels.

I am slowly moving from Debian Etch to Ubuntu Servers. Both are very good, but I prefer Ubuntu. Debian's documentation (much better than Ubuntu) is extensive and read by many admins and is useful for administering Ubuntu servers too as Ubuntu itself is based on Debian!

---

### Post by SpaceTeddy on 2008-08-26
i personally prefer the debian netinstalls to the ubuntu (it's smaller and more lightweight) when it comes to servers - but have you ever tried to get a domino server running on a debian ? I don't know what is different with the ubuntu server, but there is it only a minor pain. 
Apart from the Domino Server i usually still use the debian netinstall.

Also, i have never worked with RHEL (only with SuSE). Just thinking back to the SuSE times makes me shudder. The repositories are a mess, the Upgrade is non-existent, and why oh why does a SERVER need a full blown KDE Desktop environment with every gimmick and effect installed ? ... i never got that.
Since RHEL is based on the same packet structure i am inclined to think that RHEL is somehow the same... Up to SuSE 9 (thats when i stopped using it) it was impossible to upgrade the major version without reinstalling the whole system... or i was simply to stupid to figure it out.

---

### Post by ilrudie on 2008-08-26
I have used Redhat and centOS and they are both fine server distro's.  I found yum (redhat's apt) to be acceptable.  Kickstart ( I think thats what it was called ) is a cool tool if you have to build several identical servers.

Not sure about Ubuntu Server's support from Canonical.  I can't imagine its fantastic because Ubuntu's main focus is bringing Linux to the desktop but thats just a guess because I have no experience dealing with them.

---

### Post by Dragonbite on 2008-08-26
I've had luck so far with [[COLOR="Blue"]openSUSE [/COLOR]]("http://www.opensuse.org")and using Yast2 over an SSH connection.  The server doesn't have a desktop environment and Yast gives me all the same options it has in its GUI version.

This includes configuring devices, services, users and more.

---

### Post by HermanAB on 2008-08-26
Linux is Linux is Linux.

Deep down, there really isn't any difference between Ubuntu, Debian, Mandriva, Redhat, Suse and others.  Any perceived differences are mainly superficial.

If you were asking why to use Linux instead of Windows Server 2008 however...

---

### Post by rickyrockrat on 2008-10-06
I'd like to know about Ubuntu Server as well.  My first servers were using Red Hat...back in the old days, and I really like their init scripts.  Then on FC3, I got into a YUM repo nightmare and couldn't upgrade without breaking my system, so I looked around for an installer that would install on a software raid, but Suse was the only one that would install on a software raid, so I used it. What a mistake that was. I never did really figure out how to get Yast to work - it kept wanting me to put the CD in, and don't even get me started on the init scripts!!  They were broken (still are, but I hardly ever boot my system, so killing services manually is acceptable).

I tried Trustix (no software raid install support)
Ubuntu wasn't really out yet, but it didn't support the sofware raid install at the time (I think it does now), and I was exhausted by the time I got to CentOS.
I like RedHat's init system - it seems much better than the debian based one (but then I "grew up" on RH), but I hate yum.
apt-get, on the other hand has just blown me away at how incredibly fast and stable it is.

I don't get the impression the Ubuntu is all that stable since I see bugs on launchpad that are major and haven't been fixed for years. One of those almost completely wore out my laptop HDD by because it was starting-stopping it several times a second.

So I am torn between CentOS and Ubuntu Server. Yum is the only thing stopping me with CentOS.

---

### Post by cariboo on 2008-10-06
I started out using Redhat 6 desktop (I paid $50.00CDN for the box 2cd's and a manual), since then I have tried a few rpm based distro. The package management system does not seem to be as robust and reliable as apt. For that reason alone I would stay away from Redhat, Opensuse and Centos.

Oh Yeah. For the above mentioned $50.00 I also got a sticker!!! :)

Jim

---

### Post by lykwydchykyn on 2008-10-07
I also mostly use Debian on servers, unless I need something more cutting edge such as LTSP.  If I needed commercial support on something, obviously I would need to go with Ubuntu in that case as well.

The main reason I like Debian and Ubuntu is package management.  APT is the best by far, and I upgrade with confidence -- so much so that I script it on non-critical servers, and do it via cssh on the rest.  I also have to work with Novell SLES at my job, and upgrading it is a nightmare -- the package manager/updater is very confusing (it will show me patches then not allow me to install them, or tell me I'm not on a certain service pack after I've installed the service pack, all because it didn't update one package that is mysteriously not in the repositories, etc etc).  I dread updating SLES servers.  

Ubuntu server has a ways to go before it's a fully accepted Linux server (needs some more big name ISV certifications -- oracle, SAP, etc.), but I'm hoping someday I can dump the SLES and stick with ubuntu.

---

### Post by lazyart on 2008-10-07
I run a webserver and mail server and with both I went with Debian.  Lean and mean, hard as a rock.  Ubuntu is a wee bit heavier and I just didn't want that (even as a desktop it's comparatively heavy, but I understand the reasoning).

---

