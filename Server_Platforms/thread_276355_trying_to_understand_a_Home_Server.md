---
title: "trying to understand a Home Server"
date: 2006-10-12
forum: Server Platforms
---

### Post by SirShaggy on 2006-10-12
OK, where to start.....I bought this: [http://www.geeks.com/details.asp?invtid=EG137AAR&cat=SYS](http://www.geeks.com/details.asp?invtid=EG137AAR&cat=SYS) to setup and use as a home server. I wiped out windows and am ready to install Ubuntu. I am not going to use the server edition as I need a complete graphical front end:( 
1) As a server, will the shared files be stored in the /home or /root partition? I need to know which partition needs to be biggest. This PC will not be used for daily use or surfing the Internet, but will have the ability to in case...
Anyway, I have 3 PC's (all Ubuntu) currently running at home and 1 printer. This new PC is my 4th and this is where the printer will be. 2) Can all of the PC's access this 1 printer? I want to put my 400GB media hard drive inside this new PC, so all of the PC's in my home can access the media. It is Music, Family Photo's and Home Video's. The 4 partitions on the 400GB drive are: 100GB /photos , 100GB /videos , 150GB /music and 24.?GB /backup. That is how I set them up, I am not going to change them. These need to be accessed from anywhere in the house. The /backup partition is just individual files I backed up that were important to me. I will install this hard drive before installing Ubuntu so that it can mount these partitions as /photos /videos /music and /backup during the install. I know not to reformat these partitions, I just have to remember to uncheck the boxes!!!
3) Can this PC, the server, be the firewall? Am I thinking straight here? This is all new to me, but I see possibilities here. Maybe someday I can configure it to send and receive mail for all of the users....Actually, I don't think I am smart enough to do that.

So basically, the new hard drive, 200GB needs to be partitioned. I was going to have 120MB /boot, 2GB /swap 15GB /home and 170GB /root. This is assuming all my shared files must be in root?!?! I can reverse the sizes of root and home if I am thinking backwards. Please let me know. That is my first and biggest question.
SirShaggy

---

### Post by sonic2000gr on 2006-10-12
To give you a short answer:

- Yes, you can connect the printer on this server, and every pc on the house will be able to print.
- Yes, the server could be used also as firewall for your network
- Setting up a server is more of a process than a fixed set of answers. Be prepared to experiment with your setup until you find one you are satisfied. Probably this means reformatting and rearranging partitions a couple of times.

Where to store the shared files: This is rather a matter of taste. Since these will be available to all users, I would not put them at /home (this is supposedly for users personal files). But then again you could mount these folders anywhere (and with mount --bind you can also make them appear mounted in multiple places if you want)
You can share via nfs (or samba, but I guess you will use nfs since you only have linux pcs) just about any folder you wish. So it all comes down to how you want your system. There is not a single true way. And yes you configure it to send and receive email. My home server is an email server, and it is not too difficult.
I believe you are serious in your quest - after all you bought a PC just for the purpose, believe me, I am geeky enough :-? and only have 3 PCs at home...

---

### Post by skymt on 2006-10-12
1. You can set it up however you like. The most common configuration is to use Samba to share the home folders over the network, in which case you would allocate extra space on /home. However, you have complete control. If you want to make a /shared partition, or a shared folder on the root partition, that's also fine.

2. Yes, you can share printers using Samba. That works with Linux, Mac, and Windows. However, the printer needs to be supported by Ubuntu.

3. Please don't make this your firewall machine. Your firewall is by definition accessible from the Internet. You don't want anything on a firewall system that doesn't have to do with firewalling. Samba is not 100% secure (no program is), so you don't want to give hackers (the bad kind) that kind of opportunity. Just buy a home router (I like Netgear) and use the NAT functionality as your firewall.

---

### Post by SirShaggy on 2006-10-12
Great, this was what I was hoping for. If I do something I hate, I can re-do it. I am serious about it, although a little green and slow, it will get done. I do have a hardware firewall and a router with NAT, I am sure they will be fine, no need to setup the new machine as a firewall. I just wasn't sure if I should.  I was really struggling to decide weather to use the /home or /root partition for sharing, I think for the first attempt the /home partition will be easier for me. I am going to make my 400GB HD mount in the /home partition too. So it'll look like /home/music, /home/movies, /home/photos and /home/backup I guess. This should make it easier for all of the computers to read and write to these files. I just wonder now, what will keep people outside of my home from seeing everything? The hardware firewall and router?
The printer should work, I think. I have been using it with my computer for a year, with Ubuntu. Would there be different hardware requirements using it as a shared printer?

---

### Post by SirShaggy on 2007-07-29
OK, so this has been on the back burner for a long time. I have a PC with the Normal install of Ubuntu 7.04 and just the updates on it. No additional software at all. I wish to access this computer by Linux and Windows PC's. Only PC's on my home network though, at least for now. I will start out by only putting my media (Photos, Music and Videos) on it. My questions:
1st, do I install Samba so that windows and Linux can access these files? Or is it NFS?
2nd, Am I correct that I would next need to install Samba on my regular desktops?

3rd, You know how when you have a DSL modem, you can type 192,168.0.1 and get into the modem with a GUI? I want something similar to this. Is that possible? I want to use a browser to access the server, type the address and see the files.4th,  Do I have to have a static IP address to do this? I currently have DHCP.

Those answers should get me started, I hope. I am really brand new to servers and never used samba or nfs before. Any hints or tips would be appreciated. Currently this is very much over my head as I am new. I am very eager and teachable however. I will just take baby steps for now, I will learn more in time......

SirShaggy

---

### Post by sonic2000gr on 2007-07-29
1. Samba can be used by both Linux and Windows clients. NFS is typically Linux only. However there are Windows services for Unix (a download from Microsoft) that will allow a Windows PC to mount NFS Shares. Windows Vista also has this ability built in. In any case you are probably better off sticking with Samba and not add this unnecessary complexity.

2. You need to install the samba client, and not the complete samba server (unless you plan to share directories from these machines too). IIRC the samba client is preinstalled anyway.

3. Static IP is usually considered a must for a server, you should pick a static address for it. You can leave the rest of the network on DHCP if you wish. You may want to configure your router (I assume this is your DHCP server) so that DHCP uses a limited pool of addresses and you keep a few for machines that need a static IP. This will prevent the router from erroneously assigning your static address to another machine (It should not happen, but...)

As for viewing the files over a browser, this can also be done, but I am not sure what kind of interface you have in mind. You could for example run an apache server, feeding it from the directory you want to share, with directory indexes enabled. Then when you type the server's ip address you would get a list of files / folders as a web page. Files would be accessible in a way similar to a web page (i.e. you "download" them to your pc). If you choose this solution, make sure the Web server is not allowed to escape outside your lan (i.e. make sure port 80 on your router is not forwarded) otherwise anyone from the internet could download your files. Bear in mind also that with samba you will have the ability to view files and folders of the network in Nautilus windows, and this pretty much negates the need for the above setup. But as I said, I am not exactly certain why you would need such a setup. 

Basic samba setup is quite easy and so is NFS. Feel free to ask questions, we will guide you through it.

---

### Post by SirShaggy on 2007-07-31
> **sonic2000gr said:**
> 1. Samba can be used by both Linux and Windows clients. NFS is typically Linux only. However there are Windows services for Unix (a download from Microsoft) that will allow a Windows PC to mount NFS Shares. Windows Vista also has this ability built in. In any case you are probably better off sticking with Samba and not add this unnecessary complexity.

2. You need to install the samba client, and not the complete samba server (unless you plan to share directories from these machines too). IIRC the samba client is preinstalled anyway.

3. Static IP is usually considered a must for a server, you should pick a static address for it. You can leave the rest of the network on DHCP if you wish. You may want to configure your router (I assume this is your DHCP server) so that DHCP uses a limited pool of addresses and you keep a few for machines that need a static IP. This will prevent the router from erroneously assigning your static address to another machine (It should not happen, but...)

As for viewing the files over a browser, this can also be done, but I am not sure what kind of interface you have in mind. You could for example run an apache server, feeding it from the directory you want to share, with directory indexes enabled. Then when you type the server's ip address you would get a list of files / folders as a web page. Files would be accessible in a way similar to a web page (i.e. you "download" them to your pc). If you choose this solution, make sure the Web server is not allowed to escape outside your lan (i.e. make sure port 80 on your router is not forwarded) otherwise anyone from the internet could download your files. Bear in mind also that with samba you will have the ability to view files and folders of the network in Nautilus windows, and this pretty much negates the need for the above setup. But as I said, I am not exactly certain why you would need such a setup. 

Basic samba setup is quite easy and so is NFS. Feel free to ask questions, we will guide you through it.

Thanks for the "Perfect Information!" This is what I was searching for. I am in the process of a move, will be a few more days before I get moved and set back up again. I will play with the IP address range in the router. I think I saw an option to set a particular PC to static and leave the others as DHCP. I'll report back what I find ASAP. This is really what I needed. I will be using SAMBA as I have 1 Windows machine that I still use now and again. Just like to have the ability..

SirShaggy

---

### Post by p_quarles on 2007-08-01
Another tool you might be interested in is Webmin. It is very similar to the configuration interface on a modem or router, and uses a secure socket layer web connection. It's a great tool for anyone new to server administration, as it clues you in on a lot of configuration options you probably wouldn't have thought to look for otherwise.

---

### Post by guilly on 2007-08-01
Another tool that you may be interested in is VNC. This will give you the remote desktop appeal that you can get in windows if you are familiar with it. Basically it will allow you to connect to ur server and bring an exact window as if you were physically in front of the machine allowing you to do whatever you would do if you were actually on the machine itself. However, i would recommend only using this inside your LAN since it is not secure, if you plan on using outside your home i would suggest using some type of encryption like SSH

---

### Post by SirShaggy on 2007-08-01
This is the exact information I was hoping to get posted here. I think I can get through this........
QUESTION: Will I be able to get away with 1 Gig of ram on this File/Media server? I have 4 sticks of 256MB of PC3200 that I'd like to use for now instaead of buying more memory. This move has been very costly for me and I've had to take time off work several times too. I realize this isn't an appropriate amount for a server but am a little broke for now. 8 months from now, maybe I can buy more ram.

I will check out VNC and Webmin right away, sounds like what I am after.
Thank You to all of you,
SirShaggy

*WOW* - I just installed Webmin off the net, Build 1.350 and think it is really cool! It has a lot of functionality in it. Much more than I need right now. I will get through this stuff somehow....................

---

### Post by p_quarles on 2007-08-01
RE: RAM

1 gig certainly isn't enough for an enterprise server (I mean, rarely is one *machine* enough for that). But for a home server linking with three computers? Plenty.

I converted my old desktop -- a P4 with 384 megs of RAM -- into my home server, and it does everything I ask of it without any hiccups. Once a computer is set up to run without a GUI or a video driver, it's amazing how much more performance you get out of it.

---

### Post by SirShaggy on 2007-08-04
> **p_quarles said:**
> RE: RAM

1 gig certainly isn't enough for an enterprise server (I mean, rarely is one *machine* enough for that). But for a home server linking with three computers? Plenty.

I converted my old desktop -- a P4 with 384 megs of RAM -- into my home server, and it does everything I ask of it without any hiccups. Once a computer is set up to run without a GUI or a video driver, it's amazing how much more performance you get out of it.

Great, that makes me feel better. I will have 4 computers hooked to the server, none at the same time I'd guess?!?!

It's just me at home, sometimes my kids too. I only use 1 PC at a time unless I am downloadin and burning a cd, then I'll play on another machine, so this should work out.

SirShaggy

---

