---
title: "xubuntu as server? or no gui?"
date: 2007-09-12
forum: Server Platforms
---

### Post by bone2006 on 2007-09-12
I have an old machine I wanted to setup as a server, so I was looking at as many tutorials as possible.  I have only been using ubuntu for less than a year, but really enjoy using ubuntu.

The problem is that my machine is really old and a liveCD even gave it problems.  I've seen that some people are against putting a gui on a server and I was wondering why?  Is it difficult to run a server without the gui or since I've never ran a linux server would I be better off installing xubuntu desktop instead of no gui at all?

I was following the directions from this link [http://tinyurl.com/2owvdo](http://tinyurl.com/2owvdo) and I was planning on just typeing in xubuntu for the desktop part instead of using ubuntu to help with resources, but after reading a few posts here I'm not sure if I'm better off with no gui or will that confuse me even more?  Like I said I haven't been using linux even a year yet

---

### Post by por100pre1 on 2007-09-12
Please post your machine specs so we can give you some good advice.

---

### Post by robert_pectol on 2007-09-12
How comfortable are you with the command line?  If it doesn't scare you too much, then it opens up a lot of possibilities if you are willing to use it exclusively.  There are several reasons people suggest doing away with a graphical environment on a server.  One of which is the un-necessary drain on available system resources.  Remember, it's a server.  There really shouldn't be any reason to be loading X.  If those resources aren't being tied up for graphical environment tasks, then they will be available for server tasks, which is what the box even exists for, right?  Another reason is stability, and yet another is security.

Being able to manage your server from the command line also makes it easier to manage it from a remote location.  A shell is a shell whether you are physically at the server, or in my case, several thousand miles away from it!  If you are going to set up a server, it's HIGHLY recommended that you get cozy with the command line!  Learn to use it and you'll truly unleash the power of your server!  Just my 2¢.  Good luck.

---

### Post by p_quarles on 2007-09-12
+1 for the previous poster's recommendations. 

Just a couple more reasons to set up the server as CLI only
1) Even if it's not truly a "remote" server, you'll save space. My server box is within an arm's reach from my desktop, but because it has no monitor or keyboard, it's completely inconspicuous. And it uses less power. 

2) By administering a system with the command line you'll become a Linux power user a lot more quickly

---

### Post by Carrot06 on 2007-09-12
I was in the same boat 6-9 months ago. I was very new to Linux and tried my hardest to stay away from the command line. I also had an old PII 350mhz pc that I was trying to setup as a desktop. Due to the many issues with X, I decided to try setting up a server as cli.

This machine now runs as a LAMP with Samba & NFS file sharing, Torrent Downloader, and is the gateway to the internet for my Desktop. All this using about 1% of cpu resources. I doubt that I could do this with a gui, and especially not in windows.

Administering the server via cli has gotten easier and has increased my linux knowledge, to the point where a lot of my desktop administration is done via the command line. So my sugestion is set it up as cli first and give it a go, you may be surprised at how easy it can be. If you struggle and have Apache installed, try webmin (which is a graphical admin app which using php through your web browser). Then if all else fails install a gui, with the simple command sudo aptitude install xubuntu-desktop.

---

### Post by bone2006 on 2007-09-12
I truly appreciate allt he responses and to my surprise so quickly.

The system I just booted up really quick is a 700mhz machine, I believe it has 128mb of ram, but I am not certain.  It had windows xp on there, so I believe it's 128mb as if I'm not mistaken that's the minimum.  

I would like to have this system using less power as possible and it's not that I'm afraid to use the CLI, but that I do not have the knowledge to set it up properly.  I don't see myself ever using this machine except for a server, is there any tutorials or something I can read that would help me setup the system?  
I've found a lot of tutorials on debian, but I really like the idea of ubuntu with 1 CD compared to 32CDS of deiban or 3 DVDs, and I'm really happy with ubuntu and absolutely love this community, so I wanted to give ubuntu server a try, problem was had a lot of trouble finding tutorials on the server.

So I'll give it a try but I'm guessing there's going to be a lot of learning.  I'm guessing even editing files I'm used to use mousepad or gedit and now I guess I'm going to have to use vi?  Which I know the hardcore linux fans love, but it's so different from everything else that I had a hardtime and fell in love with mousepad's speed.

Anyway thank you all for your responses and I'll give it a try without any gui and I'd appreciate it if you guys had any links so that I'm not guessing after putting the CD in, I already have it burned and ready to go.

On last question I was hoping not to have it connected with any monitor, keyboard or mouse as well.  I was thinking I would control the system via VNC, but since there's no gui I guess I'll be using ssh or something else?  

Thanks again

---

### Post by HermanAB on 2007-09-12
It used to be that X was considered a drain on resources, but with today's (or even yesteryear's) servers, that is not much of an issue anymore.  Also, the Linux scheduler is very good and if the server needs the memory and nobody s using X, then it will be swapped out.

The main reason for not installing X is that in the case of a server farm, there are no terminals connected to the servers, so X, if installed, will never be used.  Note that X is the thing that operates the keyboard, mouse and screen and if there aren't any, then what is the point?

If you are administering a server remotely over ssh, then you can still run any X utilities if you enable X forwarding, because the X server runs on your terminal machine - since that is where the screen and keyboard are.

However, if you plan to hook a screen, keyboard and mouse to a server, then by all means do install X and Xfce or IceWM.  Just make sure that the X port 6000, is blocked in your firewall settings to the public internet.

---

### Post by p_quarles on 2007-09-12
> **bone2006 said:**
> I've found a lot of tutorials on debian, but I really like the idea of ubuntu with 1 CD compared to 32CDS of deiban or 3 DVDs, and I'm really happy with ubuntu and absolutely love this community, so I wanted to give ubuntu server a try, problem was had a lot of trouble finding tutorials on the server.
First of all, the Debian tutorials will almost completely apply to the server edition of Ubuntu.

That said, you certainly don't need to download 32 CDs to get Debian. I'm running Debian 4 on my server, and I installed it from the ~180 MB "net install" CD. This allows you select the packages you wish to install and download them from the repos during the installation process. I chose this because it was the best way to get a minimal installation.
> On last question I was hoping not to have it connected with any monitor, keyboard or mouse as well.  I was thinking I would control the system via VNC, but since there's no gui I guess I'll be using ssh or something else? SSH is the best option for server administration. 

One word of caution, though: some BIOSes are set to fail without a monitor. In most cases, you can turn this off within the BIOS menu. Just be sure to check this out during the installation process.

---

### Post by bone2006 on 2007-09-13
For the installation I'm using an old old monitor, but I'm not planning on having the monitor, keyboard or mouse hooked up to it if I don't have to, so I'm hoping after it's up and running that it continues running stable and that anything I need to do to it I can do it from my other systems.  

It looks like there really isn't any point in having a gui if I'm not really going to be using the system for anything else except a server.

I'll have to look at some of the debian tutorials I found and just apply them
Thanks

---

### Post by HermanAB on 2007-09-13
So install X and Xfce desktop.  Then once you are done with the local admin, run "sudo init 3" to turn X off.  One day when you need to do something on the local terminal again, do "sudo init 5" to bring X back up.

Cheers,

H.

---

### Post by netlogic on 2007-09-13
Are there gui administrative tools for Ubuntu? I didn't even knew they existed. What GUI tools are you going to miss? Only thing I can think of top of my head is Synaptic and User Manager. Apt-GET is very simple to understand and adduser and groupadd are both simple to maintain by studying the man page. Applying folder and file permissions through natilus is not recommended. It will take you longer, because it doesn't have a recursive command through GUI. You are totally better off using the CLI. It isn't an uber geek thing. It is a must to maintain any UNIX based system. Also, think about why you believe UNIX based system is better. CLI and flat file system mean you can move things anywhere, mount anything, and automate anything through cron jobs. Anything you can do with the GUI, you can automate and do it twice it fast through the CLI.

---

### Post by p_quarles on 2007-09-13
> **HermanAB said:**
> So install X and Xfce desktop.  Then once you are done with the local admin, run "sudo init 3" to turn X off.  One day when you need to do something on the local terminal again, do "sudo init 5" to bring X back up.

Cheers,

H.
=non sequitur

---

### Post by bone2006 on 2007-09-13
One of the tutorials I'm reading actually recommended installing twm, with 
apt-get install x-windows-system twm

---

### Post by Brazen on 2007-09-13
> **HermanAB said:**
> So install X and Xfce desktop.  Then once you are done with the local admin, run "sudo init 3" to turn X off.  One day when you need to do something on the local terminal again, do "sudo init 5" to bring X back up.

Cheers,

H.

mmm, you might double check the inittab.  I seem to remember assuming what init 3 and init 5 would be, and then finding out that Ubuntu does something funky with their runlevels.

---

