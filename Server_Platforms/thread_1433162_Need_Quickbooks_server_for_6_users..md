---
title: "Need Quickbooks server for 6 users."
date: 2010-03-18
forum: Server Platforms
---

### Post by jesselander on 2010-03-18
I need to setup a simple server to make available Quickbooks accounting data to just a few stations.  Can this be done with Ubuntu desktop version? Would it be recommended due to the small number of users? Or should I use a server platform?
 
I have never used Linux before but have used command line interfaces and am looking forward to it. I installed Ubuntu Server 9.10 32 bit and have even gone as far as logging in. Amazing I know. I installed it on a separate disk so I can switch between Windows and Linux startup disks at boot via cmos.
 
I'm a complete newb here and as a first step into linux would like to be able to browse the web from Ubuntu Server 9.10 if the Server edition is in fact the route I should be taking.  I would also like a good source to help me learn not only command line commands but also all the stuff that I see after the commands, you know, all the stuff with - signs all over the place.
 
Thanks

---

### Post by jrssystemsnet on 2010-03-18
> **jesselander said:**
> I need to setup a simple server to make available Quickbooks accounting data to just a few stations.

Well, there's a problem with this - it "can be done" with Samba, but only partly.  The more recent versions of Quickbooks started using MS SQL Server for the user login, for some reason, even though the actual *data* is still sitting in flat files.

So, yes, you can store the Quickbooks company files on a Samba share, but one of your Windows machines is still going to have to act as a kind of "server" for the other ones to authenticate through.  It's pretty screwed up; but then, welcome to the wonderful world of small business accounting software; it's *all* pretty craptastic, bloated, and screwed up.  (I support several CPA firms.  I'm not bitter, just tangy.)

Whether using Linux and Samba for this is a good idea kind of depends on how determined you are to use Linux to begin with.  If you just thoroughly want to use Linux anyway - maybe you're enthused about open source, maybe you're enthused about the much lower potential for malware to infest your fileserver, maybe you're enthused about doing your own backup solution that's more transparent than the ones available for Windows, maybe you're excited about the OTHER things you could do with that Linux server (like hosting websites or running a mailserver or doing a local DNS server or, well, whatever) - then sure; knock yourself out, setting up Samba is quick and pretty easy and for the most part your QB will "just work", although you may have to futz around a bit with some settings regarding one of your Windows workstations being the "login host".

But if you're not really committed to Linux for some reason already... then you should probably just sigh bitterly, say some unkind words in your head to Intuit, and go buy a copy of Small Business Server and install Quickbooks on that.

---

### Post by jesselander on 2010-03-18
Thanks for your time and the extensive response. You have given me a lot of information and food for thought.  My reasons for looking into linux were firstly its reputaion as the server king and secondly to save about $1000. 
 
It sounds like I just might go with windows anyway then.  A lot of fussing, adjusting and tweaking is not something I look forward to doing unless it offers advantages.  
 
What I need is just a good stable server for my small buisness.  First I need to store accounting info but eventually it would need to store other information such as inventory, order processing... and maybe even host our website.  I just thought that linux would be the best choice given its rep. The money isn't the issue so much as getting it right.
 
So can windows server do all the things I mentioned above?  Or do I just need different accounting software?

However I would prefer to free myself of windows slavery.  So how do I load a web browser on ubuntu server? And then Samba.  The browser so I can access this forum and samba so i can host QB.

---

### Post by jrssystemsnet on 2010-03-18
Linux is certainly the better choice for hosting your website.  But for dealing with CPA applications... well, you're stuck with what's available, and that means you're stuck in the-cheapest-developers-we-could-hire he..ck, which means they think every PC in the world is running Windows and Internet Explorer.

There are folks who will tell you "just use Gnucash!", and maybe you could make that work for you... but it would be a LOT of work on your part, and would be more likely to work for someone who already had a really extensive level of Linux and basic development knowledge.  For "small business in the real world" and accounting, you are pretty much going to be stuck with Windows.

After all, one very real problem you're stuck with is that every town from huge to small is chock-FULL of "oh, I know Quickbooks!" small-biz accountant types on the cheap... not so much, anything else.  That's a very real consideration you need to deal with.

I'd recommend you grab a copy of Windows Server (OEM is around $800), install it on good hardware, set up your business on that... and save your Linux ventures for when or if you're ready to set up either a webserver, or possibly a bulk data server.  If you're going paperless or you otherwise expect to accumulate a LOT of data, you may very well eventually want a separate fileserver from your application server... and *then*, Linux and Samba will start making a heck of a lot of sense.  You might also eventually want to do backups across a network to a dedicated backup server (either on-site or off-site), and Linux is also great for that.

And in the meantime, gripe and complain and yell at Intuit's sales team about "why they don't have a Linux version"... after all, it's *their* fault that you're stuck with Windows. :)

> **jesselander said:**
> However I would prefer to free myself of windows slavery.  So how do I load a web browser on ubuntu server? And then Samba.  The browser so I can access this forum and samba so i can host QB.
The very basics?

Drop to a shell, and 

```
you@box:~$ sudo apt-get update
you@box:~$ sudo apt-get upgrade
you@box:~$ sudo tasksel install lamp-server
you@box:~$ sudo tasksel install samba-server
```

They're installed; now you've got to configure them.  Google around for some pointers; for the very basics, you're going to be looking at /etc/samba/smb.conf and /etc/apache2/sites_available to set up configurations.

For samba, you have to add system users, and you also have to add Samba users, and then you have to configure the share.  Take a look over in the Network thread, I just gave somebody some tips on setting up a basic Samba share a little earlier today.

For apache, it's a pretty big topic... if you just want to futz around for now, you can avoid configuring *anything* and just start dumping files in /var/www; the default config uses that as the webroot for any incoming HTTP connections.  There is a LOT more information to learn if you get into doing anything serious with web applications and virtual domains, but that'll get you started with something to go "hey, cool, it works!" in the meantime.

Oh, wait wait wait - you said load a *browser?*

Um, well, if you installed the Server distro, you probably don't have a desktop.  So you'll need that first.  If you *want* a desktop on a server... which you normally don't.  But, if you want to use it like a workstation as well as like a server...

```
you@box:~$ sudo apt-get update
you@box:~$ sudo apt-get upgrade
you@box:~$ sudo tasksel install ubuntu-desktop
```

With that done, **sudo shutdown -r now** and you'll be able to log in to a graphical desktop when the machine reboots.  You'll already have Firefox, along with a ton of other stuff; you should be able to navigate around pretty easily.

---

### Post by jesselander on 2010-03-22
Thanks jrssystemsnet for a piece of your seemingly infinite knowledge :)   So would 
 
you@box:~$ sudo apt-get update
you@box:~$ sudo apt-get upgrade
you@box:~$ sudo tasksel install ubuntu-desktop
 
allow you to run desktop within server or is it a seperate login?

---

### Post by jrssystemsnet on 2010-03-22
That installs all the user-interface chunks that are part of the "desktop" release.  For most intents and purposes, at that point you *have* a "desktop" release (although the kernel itself is still the server kernel, and there are probably other differences I'm overlooking).

It's still your same "server" but now it's running X windows, the local console has the gdm (graphic display manager) login instead of the plain-text one, and everything normally installed in the way of user applications (like OpenOffice, etc) is now installed and sitting in menus when you log in graphically.

---

### Post by KB1JWQ on 2010-03-22
As usual, I find myself agreeing with jrssystemsnet.  

The application is the most important thing for what you're trying to do-- the underlying infrastructure shouldn't dictate that particular decision.  While there are Linux alternatives to Quickbooks, most of them aren't very polished and require extensive work to "get right."  

And desktop environments don't belong on servers! ](*,) :evil:

---

### Post by jesselander on 2010-03-22
> **KB1JWQ said:**
>  
And desktop environments don't belong on servers! ](*,) :evil:
 
Right. That's what I keep hearing. The thing is, is if I knew what I was doing I wouldn't need it. However I unfortuantely don't have every Linux command memorized among other things.  Hence, I would like a way to access certain recources such as google and experts like you guys while also being able to implement the solutions I find without having to switch systems or boot disks everytime.

---

### Post by jrssystemsnet on 2010-03-22
> **jesselander said:**
> Right. That's what I keep hearing. The thing is, is if I knew what I was doing I wouldn't need it. However I unfortuantely don't have every Linux command memorized among other things.  Hence, I would like a way to access certain recources such as google and experts like you guys while also being able to implement the solutions I find without having to switch systems or boot disks everytime.  The proper way to do that is to use your own desktop - which can easily be a Windows one, or it could be a Linux one, it doesn't matter - for things like Googling stuff and web browsing and what have you; you also use that desktop to open up an SSH connection to the server, which gives you a shell there that you use to issue commands.

You don't normally sit directly in front of a server, physically, unless something is deeply, DEEPLY wrong.

oh, and from a Windows machine, [PuTTY](www.chiark.greenend.org.uk/~sgtatham/putty/download.html) is the program you use to make an SSH connection to your server or servers.  Unless you prefer a different one, at any rate.

And if you haven't yet installed SSH on your server, **sudo apt-get install ssh-server** will do the trick.

---

### Post by jesselander on 2010-03-22
> **jrssystemsnet said:**
> The proper way to do that is to use your own desktop - which can easily be a Windows one, or it could be a Linux one, it doesn't matter - for things like Googling stuff and web browsing and what have you; you also use that desktop to open up an SSH connection to the server, which gives you a shell there that you use to issue commands.
 
You don't normally sit directly in front of a server, physically, unless something is deeply, DEEPLY wrong.
 
OOOOHHHhhh!...  I quess that should have been quite obvious but I guess I assumed that the only way you could have complete control over a server would be to have physical contact with the server.  But I guess now I understand that it makes sense that all you need is some kind of super admin id and password.

---

### Post by gordintoronto on 2010-03-23
> **jesselander said:**
> OOOOHHHhhh!...  I quess that should have been quite obvious but I guess I assumed that the only way you could have complete control over a server would be to have physical contact with the server.  But I guess now I understand that it makes sense that all you need is some kind of super admin id and password.

Yes, usually a server doesn't even have a monitor attached after it's set up. You log on from your desktop, and the display is on your monitor.

However, there's also no reason you can't run a light-duty server from a desktop machine.  For example, I test web site development on Apache/mysql running on my desktop, before FTPing the web pages to the real server 1,000 miles away.

---

### Post by KB1JWQ on 2010-03-23
RIght.  I test things locally before pushing them to other servers, and having a Linux desktop is intensely useful when I need to perform certain tasks, but the output of dpkg -l would be very, very different between my laptop and a production Ubuntu server*.


* I have no production Ubuntu servers at this time.  I'm a RedHat or FreeBSD guy in the server room so far.

---

### Post by jrssystemsnet on 2010-03-23
> **KB1JWQ said:**
> * I have no production Ubuntu servers at this time.  I'm a RedHat or FreeBSD guy in the server room so far.

Try it, you'll like it! ;)

I'm a long, long time FreeBSD guy (since 4.2-R); have done time on RH boxes but not enjoyed it.  Took me a bit to get used to the Debian server way of doing things (which is basically what Ubuntu Server is, really) but once I did... I approved, whoo boy did I ever approve.

I still deploy a fair amount of FreeBSD for ZFS, but ZFS is the only reason I have left to do so.  BSD used to outperform and out-uptime linux handily, but that is very definitely no longer the case, and the package management is hands DOWN better for Ubuntu.

---

### Post by KB1JWQ on 2010-03-23
Unfortunately any change that touches 400 nodes is a long time in the making. :-)

I have the same nick on freenode if you'd like to continue this conversation there; I think this thread has drifted far enough. :-)

OP: Did you get all of your questions answered?

---

### Post by jesselander on 2010-03-23
> **KB1JWQ said:**
> 
 
OP: Did you get all of your questions answered?
  
I wish.  But not even close.  Like for instance, what is OP? When I run **sudo apt-get install ssh-server** where does the program come from? No url involved? Perhaps another thread would be more appropriate?  Am I getting annoying? How much do I owe you guys?....,...etc.  You guys have been a huge help though. I think I will stick with Linux and take it as far as I can.

---

### Post by jrssystemsnet on 2010-03-23
> **jesselander said:**
> what is OP?

Original Poster.

> When I run **sudo apt-get install ssh-server** where does the program come from? It comes from the Ubuntu repositories, which are configured (with URLs!) in /etc/apt/sources.list.  You can look for things in the repositories either by browsing them graphically using the Synaptic package manager (if you have a GUI) or **apt-cache search** if you're working from the command line.

Example, say you want to monitor network usage from the console, and you don't know what, if any, software is available from the repositories that does that.

```
you@box:~$ apt-cache search network usage monitor console
jmon - distributed resource monitor
nload - A realtime console network usage monitor
```

So you decide to install nload, and see if it fits your needs:

```
you@box:~$ **sudo apt-get install nload**
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  nload
0 upgraded, 1 newly installed, 0 to remove and 199 not upgraded.
Need to get 33.3kB of archives.
After this operation, 135kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy/universe nload 0.6.0-3 [33.3kB]
Fetched 33.3kB in 0s (34.6kB/s)
Selecting previously deselected package nload.
(Reading database ... 101481 files and directories currently installed.)
Unpacking nload (from .../nload_0.6.0-3_amd64.deb) ...
Setting up nload (0.6.0-3) ...
you@box:~$ 
```

Now you can try running it, and see what it does:

```
you@box:~$ sudo nload
Device eth0 (1/1):
================================================================================
Incoming:





                                                       Curr: 1.87 kBit/s
                                                       Avg: 32.80 kBit/s
                                                       Min: 0.93 kBit/s
                                                       Max: 930.18 kBit/s
              .|          . ..                         Ttl: 104100.38 MByte
Outgoing:
                            ##
                            ##
               |            ##
               #            ##
               #            ##
               #            ##                         Curr: 10.88 kBit/s
              |#          . ##                         Avg: 470.43 kBit/s
              ##          # ##                         Min: 3.31 kBit/s
              ##          # ##                         Max: 15800.91 kBit/s
              ##          #|##                         Ttl: 3060.22 MByte

```

Pretty neat, if you need that kind of thing.  (Incidentally, I didn't know about nload until right now, demonstrating searching the repositories to you.  And I kinda like it!)

But maybe you decide you don't need or want that after all.

```
you@box:~$ sudo apt-get remove nload
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  nload
0 upgraded, 0 newly installed, 1 to remove and 199 not upgraded.
After this operation, 135kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 101487 files and directories currently installed.)
Removing nload ...
you@box:~$
```

There, all gone.

Neat stuff, eh?

> Perhaps another thread would be more appropriate?Well, you might consider spending a little time in "General Help" or "Absolute Beginner Talk" and asking your really basic questions there.  A little grounding in the basics of what Ubuntu is and how it works would help you figure out what you need, and whether Ubuntu fits that bill or not, quite a bit. :)

---

### Post by jesselander on 2010-03-23
Yeah, seems real neat and convenient, except it didn't work for me. I tried running 
**sudo apt-get install ssh-server** and here's what I got:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package ssh-server is a virtual package provided by:
   lsh-server 2.0.4-dfsg-2build 1
   open ssh-server 1:5.1pl-6ubuntu2
You should explicitly select one to install
E: package ssh-server has no installation candidate
 
I don't know if it is automatic or what but I don't remember setting up an internet connection for my server boot disk. Might be the problem but I think it would have said something more like can't connect or simething.
 
Is there a forum for server newbs?

---

### Post by KB1JWQ on 2010-03-23
open ssh-server 1:5.1pl-6ubuntu2 is your boy.  I haven't got the foggiest what the other one is, are you using a custom source?

And yes, there is a forum for server noobs-- you're in it. :-)

Welcome aboard.

---

### Post by jesselander on 2010-03-23
Okay. Then I'll try 
 
**sudo apt-get install openssh-server**

That was easy. So I've got openssh installed on my server and PuTTY on my desktop.  Like I said before, both disks are on one system. I just switch boot disks at startup. I have an extra system sitting here on my desk that I plan to install my server disk on.  However, I don't have any extra monitors or keyboards to adjust the server locally so I want to make sure everything is set up before I switch the server over.  It seems like it should be pretty simple but if somebody could please verify that my procedure is sound I'll give you a bean. Here's my plan:
 
Step 1. Transfer Hard Disk with ubuntu server installed on it to new system.
Step 2. Connect desktop to server via ethernet and router.
Step 3. Startup both systems.
Step 4. Start PuTTY on desktop.
Step 5. Under "Specify the destination you want to connect to" and "Host Name" enter the name that I have given to my server as in the "you" part of you@box and then voila, I should be connected and ready to login through some commad line that magically pops up.
 
Am I missing anything or am I good to go?

---

### Post by KB1JWQ on 2010-03-23
Yeah.  That hostname won't magically talk to the DNS server and register itself unless you've got more to your infrastructure than you've mentioned.

Give it a static IP, or set DHCP and prepare to pingsweep the DHCP scope looking for it...

---

### Post by jesselander on 2010-03-26
Yeah, well vi explodes everytime I try to escape from an insert command and nano won't respond to currsor movement commands via arrow keys so I have been unable to set a static IP address.  Again, I am using 9.10 server. Maybe I should be using 8.04 (less bugs perhaps) since I'm a noob.  I think somehow I have corrupted my install so I am now going to do a fresh install of 8.04.  Is this what I should do?

---

### Post by Jive Turkey on 2010-03-27
> **jesselander said:**
> Yeah, well vi explodes everytime I try to escape from an insert command and nano won't respond to currsor movement commands via arrow keys so I have been unable to set a static IP address.  Again, I am using 9.10 server. Maybe I should be using 8.04 (less bugs perhaps) since I'm a noob.  I think somehow I have corrupted my install so I am now going to do a fresh install of 8.04.  Is this what I should do?

It sounds like your keyboard isn't mapped correctly, do your arrow keys work for anything?  Maybe try the numpad with num lock off too.

If you want to avoid quickbooks in favor of gnucash I recommend you look into compiling a later version from the gnucash website.  The latest version can use MySQL or PostgreSQL databases over a network instead of local xml.  I dislike intuit software as it seems to be designed for my grandmother with big silly buttons instead of letting me just dig right in to the journal like I can with gnucash.  gnucash will also never ever fire popup ads at you.  The only things in favor of quickbooks IMO are online banking support, and multiple concurrent users.

Welcome to the forums!

---

### Post by jesselander on 2010-03-29
Thanks. It's been very helpful. You guys are all great and I appreciate every reply. 
 
It may have been my keyboard but when I loaded ubuntu it had me press a bunch of keys and it decided I had a "us" keyboard which seemed reasonable. I did try everything even alternate keyboards. 
 
I went ahead anyway and successfully fresh installed 8.04 LTS server. Seems to work a lot better. Logs in with single entry of password everytime unlike with 9.10. It was also a breeze setting up a static IP. 
 
I now have the hard disk installed in a seperate system and PuTTY installed on my windows xp desktop. My ubuntu server system has no monitor/keyboard so I need to access it on my desktop via PuTTY. I verified that the static IP I set up on server is recognized by DHCP. Now to try to connect.

---

### Post by jesselander on 2010-03-30
Well, I've got my server online and I'm using PuTTY to connect to it from my windows desktop. Now to load quickbooks somehow...

---

