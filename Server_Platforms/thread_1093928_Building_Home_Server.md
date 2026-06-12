---
title: "Building Home Server"
date: 2009-03-12
forum: Server Platforms
---

### Post by Ianallan on 2009-03-12
I'm looking to build myself a home server and realized I wasn't really sure what to pick up. I don't have any unused PCs lying so buying new is probably the route to go,

So I was looking for some suggestions on what to buy (I've never run a server before and am unsure of what exactly its requirements would be)

Ideally the server would be centralising all my media files (Considering a smart raid 1) and allowing accessibility to audio and video to any other computer in the network, coupled with this would be heavy torrent use 

other than that it would likely be hosting a website ([http://www.diywebserver.com/](http://www.diywebserver.com/))

any help would be appreciated (the wikipedia page on "home server" can only take one so far)

---

### Post by Jimmy9pints on 2009-03-12
Hi Ianallan,

I am in the same boat as you, just looking to build/set-up a linux home server. 

If you are buying a new system it doesn't need to be high end at all. I used an old computer (that I picked up for around 75USD). I wish I had done the same as you now though because when I consider the cost of the new disks I need and the PCI>SATA cards I am gonna need it's going to cost more than a new, albeit low-end, system, which would have been faster and more upgradable. 

Anyway, as far as software choices go there are a lot, but the top contenders are:
[Ubuntu server edition]("http://www.ubuntu.com/products/whatisubuntu/serveredition")
[Clark Connect]("http://www.clarkconnect.com/")
[FreeNAS]("http://www.freenas.org/")
[Amahi]("http://www.amahi.org/")

There was an Ubuntu Home Server Edition project, but that failed unfortunately. 

So, I have tried Amahi, but as it's based on Fedora 9, it comes with a load of stuff you just don't need (like word processor, web browser etc.). It just weighs down your system and is needless. Also, I just couldn't be bothered to learn another distro after becoming so familiar with Ubuntu. Amahi operates as a server within the internal network, i.e.:
Internet----Router/Firewall----(Internal Network)-----Server----Clients
I would suggest you stick with what you are familiar with if you don't want to spend ages learning something new. Apparently they've got an Ubuntu version in the pipeline, which would make it first choice for me. 

FreeNAS is the most bare-bones of all of them. It's super light, so it'd suit an old system. It's based on BSD and apparently it's very intuitive to remotely administer but I haven't tried it so I can't be sure. To be honest, even the website doesn't look that user-friendly. Apparently it lacks all-singing-all-dancing features and support for NTFS. Though...it got rated very highly in reviews and polls I saw online. 

Clark Connect looks pretty business oriented and acts as a gateway as well as a server.
Internet---Gateway_Server/Firewall----Router/hub---(internal network)---Clients
Given the use of a $20 router/firewall, I don't think I need to mess around configuring a gateway server. If you're interested they do a free version look on [their website]("http://www.clarkconnect.com/"). 

I am going to go for Ubuntu. Set up on the internal network like the Amahi one. 

Hope this helps,

James.

---

### Post by lvleph on 2009-03-12
I actually have built a server as you described. One difference may be that mine is also my HTPC, so I required a good video card. For a basic server you wouldn't have to worry about much except the hard drive space, and that depends on how much data you have.

If you are looking into an HTPC then a good video card is a must. I have the ATI 4850, which will play 1080p movies with out too much issue. It was $160 and so I couldn't complain. However, support for ATI is not great, but is improving in the Linux World.

If you have a serious amount of data you may want to look into RAID. This way you can have all your data backed up and not worry too much about drive failures.

I think we would need a bit more information to provide you with any good suggestions.

As far as your network goes... If you are streaming data then Wireless N might be a necessity for those clients that are not wired. I don't stream data, so I am just using g. I am using an ASUS Wl500GP wireless router. This router is nice, because it has USB ports for a print server, file server, and web cam (but only two at a time). Also, it is hackable, meaning you can put OpenWRT on it and do some pretty fancy things with your router. In fact, you could turn the router into a headless server.

EDIT: I don't think buying any software is necessary. Any thing you need is in the repositories or is already packaged with Ubuntu Server.

---

### Post by hyper_ch on 2009-03-12
RAID is no backup method. RAID is a high-availability method.

---

### Post by BkkBonanza on 2009-03-12
For what you are doing I would be looking at low power boards like the Intel Atom board. For home file serving, torrents, small web site type use that kind of board is ideal. No fan or tiny fan = no noise, low power = low cost. People don't pay much attention but running a server 365/24/7 really adds to your electricty cost. 

Since your'e into Ubuntu already I'd go with Jeos (minimal install of Ubuntu server) and add the extras you need with apt-get. Samba probably for file sharing. Instead of installing Apache I'd try out Nginx. Much lower overhead and also easy to config and run. There are a few choices for a non-gui torrent client with web control but I don't recall off hand now. If you want to share a printer around your home then install cups.

For home backup RAID isn't really the best choice. I know it sounds cool but usually what you really need is off site copies. So a removable usb drive that you can rsync to and then take away is better. Raid will help you when you need to keep files online even during a failure but for anything other than a single drive fault you may be hosed. I'm talking about fire, theft, tree falling, nuclear blast etc.

---

### Post by Ianallan on 2009-03-14
Really I was considering raid because I have a ~1/2TB of video and audio, and I would rather not spend the time to reacquire. (I had had a 500gb drive die on me earier this year) I cant see using a usb drive to be as useful in that scenario, though I would likely use something similar for backing up term papers and the like.

My other question is that will the atom boards be able to handle streaming A/V to other computers? I've heard they have about 1/2 the effective power of a celeron but I'm not really sure what that would imply for mu uses.

---

### Post by LOG123 on 2009-03-14
if you have 3 drives i suggest doing RAID-5 because its redundant and will allow you to store more data than raid 1
If your talking about home media centers i suggest LINUX MCE, mythbuntu, mythdora, or knoppmyth i've tried all of them except knoppmyth.

Best of luck!:)


LOG123

---

### Post by Kluttz on 2009-03-15
Hello All

I just build a linux home server finally about 2 months ago (Its been up and running for about 65 days now)

I came from running a Win2k3 server for about 4 or 5 years.

I decided to use linux since my windows server was full of trojans and backdoors.

My goal was to replace my windows server plus more.

What I wanted...

- file/data storage (my files, MP3's, movies and pictures)
- stream movies to our xbox360's
- have a backup running every day
- centralized place to run my torrents
- ran a LAMP server (Linux Apache MySQL PHP)
- host my photo gallery locally on my server, rather then a web hosting account
- web proxy server for the household

I was able to successfully accomplish all of them.

My current server setup, (its been like this for 4 or 5 years now)

CPU: AMD 1700+
RAM: 768MB DDR
HDD: 200GB (OS drive)
HDD: 250GB (Data Drive) currently mounted as /data
HDD: 250GB (Backup drive) currently mounted as /data1
CDR: Basic 40x CDROM

This was my Win2k3 server with NTFS partitions.
Before I started I made sure both drives had mirrored each other.  

First what I did was install Ubuntu 8.10 server, with SSH.
Ran sudo apt-get ugdate and sudo apt-get upgrade

Installed Webmin.  Confirmed it was working.
From here on I moved server back to room (under the stairs) running headless (no monitor)

Booted back up and connected via SSH and webmin.

Next step I was was risky was because of potential HDD failure and data loss.  But I was OK.

Copied any important or crucial personal files to the 200GB OS drive.

I formated the first Data drive and mounted it as /data
Copied all the files I had on on my Backup drive to the new /data mount.

Then formatted and mounted the backup drive to /data1
Then copied files back from /data to /data1

Now I have my basic home server running with my data intacted and backup.

Now for my list of what I wanted to do.

- file/data storage (my files, MP3's, movies and pictures
For this I setup Samba from Webmin.  Now I ahve access to all my files again on my Windows PC (Vista64)


- stream movies to our xbox360's
Installed Ushare (sudo apt-get install ushare)
Edited the config file to tell ushare where my movies were located.

Restarted service, now I am streaming my videos to my xbox's

NOTE:
With Ushare I have to stop and start service everytime a movie is added/removed.  I do not know why.  

Also movies do sometimes stutter while watching.


- have a backup running every day
Wat I did was setup rsync to mirror data from /data to /data1 every day at 5am.
rsync -a --delete /data /data1 
i think that was the command I used


- centralized place to run my torrents
I installed utorrent (sudo apt-get install utorrent)
Now I can d/l all my TV episodes again.  And now I can access this website externally as well.

- ran a LAMP server (Linux Apache MySQL PHP)
If i remember correctly, this is all done.  I think i just had to setup MySQL and i also installed myphpadmin

- host my photo gallery locally on my server ran then a hosting account
For this I used zenphoto from zenphoto.org.  This is a great gallery software.  I have been using it for a couple years on my web hosting account, but now I have it running on my home server.
My favourite part is I can now have my images stored outside of the /var/www folder (pictures are part of my /data/media) and zenphoto can access those files and make them accessible on the website.  So its a one stop dump now.  Pics from camera got to /data/media/pictures.  So now they are stored, accessible via samba, backed up everynight, and also instantly accessible on the web galley.


- proxy server for the household
For this I installed Squid and also SARG, from Webmin.

Webmin is a great tool and I strongly suggest to use that.

Well, this is my setup at home.  I'm sorry for the lengthly post, but I hope this helps someone out there.  I under being lost as I was too when I first started.  

Before I started this I ran a vmware or vitrulbox session on my Windows PC and tested some of this stuff out before I implemented, mainly the ushare part, as I heard it was tricky sometimes.

Good luck!!

I am no linux guy by any means but feel free to PM me if you have any questions.  I can try to help.  

Andy

---

### Post by UncleAelfrich on 2009-03-16
If at all, I would suggest you run wired ethernet. Also, buy new hard drives for your data to put into a RAID array. I made the mistake of making do with old drives. Wish I hadn't now. I installed the basic ubuntu server, then added xubuntu. Also, I would suggest you install SSH to work from your regular computer via putty (assuming you use windows). I must warn you though, learning Linux and Ubuntu ceased to be fun some time ago. Everytime something breaks, I tell myself I never wanted to learn this much about linux.  If you can afford it, I would suggest you use online storage like mozy or amazon s3. It's much simpler.

---

### Post by cb951303 on 2009-03-16
If you're into green computing below thread will help you a lot :)
Home servers barely need serval performance so it's perfectly possible to make a <20W home server without a performance sacrifice. :popcorn:

[http://geekhack.org/showthread.php?t=1410](http://geekhack.org/showthread.php?t=1410)

---

### Post by ABDK on 2009-03-16
Any one done this with a laptop and an external HDD via USB 2.0 ??
I have this Fujistsu Siemens amilo pro V2040 that i'm considdering making a tiny server. not really a media-center, put for lamp and fun :-)

---

### Post by Ianallan on 2009-03-16
@ABDK I have something similar now, 500gb in an external though 2.0 usb to a laptop. It just feels shoddy to me, and Id rather build a machine for the express purpose of being a server then use something not designed for it.

@cb951303 Thanks, great info, though probably sticking with Atom, switching from x86 to ARM is more work then I want to contend with. Otherwise I really want to keep the wattage down.

[Probably start with something like this](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010030309%201577744505&name=Intel%20ATOM)

---

### Post by cb951303 on 2009-03-16
> **Ianallan said:**
> 
@cb951303 Thanks, great info, though probably sticking with Atom, switching from x86 to ARM is more work then I want to contend with. Otherwise I really want to keep the wattage down.

[Probably start with something like this](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010030309%201577744505&name=Intel%20ATOM)

Atom is fine. I found few embedded atom based boards that consume less then 10W under high load. You can see them all in that thread. There is also a Marvel one at the very end which I think revolutionary :)

You're right about the ARM though. x86 is easier to maintain and I believe cortex is pretty expensive.

---

### Post by papenpj on 2009-03-17
I used this [Guide]("http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html") when I originally setup my server because it was easy to follow.

Mainly I found that I really like torrentflux because it can be easily setup to be accessed from anywhere that has an internet connection and stuff will be waiting for you at home. You might want to look into seeing if any friends or relatives have an old computer they don't use anymore, because running a headless server doesn't require much of a computer.
I use a Pentium III 600MHz with 128Mb RAM from 2000. 320GB IDE harddrive.
But it is enough to simultaneously stream the same avi file to a Xbox360 and playstation 3 with Ushare and stream to a PC.

However, as some others have pointed out if your willing to spend money you can get much more function, or reliability

---

