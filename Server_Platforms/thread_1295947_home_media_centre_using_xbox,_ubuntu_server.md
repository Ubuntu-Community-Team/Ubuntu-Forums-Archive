---
title: "home media centre using xbox, ubuntu server"
date: 2009-10-20
forum: Server Platforms
---

### Post by johnycage on 2009-10-20
Hello community,
I'm setting up Home server and creating Enterainment centre around my Xbox 360. The figure can help you understand my proposed setup. [http://twitpic.com/m59rz/full](http://twitpic.com/m59rz/full) This is something very similar to windows home server, except I dont want to use Windows for it... 
I know we can share media from Ubuntu based PC onto Xbox to watch it on TV. Still I've some doubts.

My proposed home server details: **OS= Ubuntu Server**. 
1.) I want to manage it remotely through my notebook/windows or other home network device.
2.) Hence I dont want to attach monitor, keyboard, mouse to it. (also no sound card, graphics card etc. Just a BIG hard disk)
3.) use it as File server (storage and backup device)
4.) use it as localhost (for testing purpose LAMP/ XAMPP)
5.) I expect it to be connected to DSL/broadband & ON-running whole day or even 24 hours some times.
6.) if possible want to use bittorrent apps.
 
**[COLOR="DarkRed"]Questions[/COLOR]** 
First of all: [LIST]
[*]Is it possible to streamline my media files, movies, folder, songs, _pictures to Xbox 360 on TV from Ubuntu_?
[*]There're quite a few articles/threads/howtos about Xbox 360 + Ubuntu, but I'm not sure whether I can do it on Ubuntu Server system (CLI based?). 
[*]Do I need to install GNOME on ubuntu server? 
[*]What other things I need install/add to make sure I can run it properly?
[/LIST][IMG]http://twitpic.com/m59rz/full[/IMG]

---

### Post by johnycage on 2009-10-21
any replies guys?

---

### Post by CharlesA on 2009-10-21
You can install the Gnome GUI by using:

```
sudo apt-get install ubuntu-desktop
```

As for connecting locally, you can just use VNC to get into the machine. I use SSH to connect to a terminial, and VNC to a virtual desktop if I need to.

TBH, I would include a video card, even if it's a really old/crappy one. There are times when I've had to actually get on the physical terminal to configure things and I have to attach a monitor/keyboard/mouse to it.


If you want to configure different services, you can do that from SSH at the terminal or use something like Webmin to configure them from a browser. I use a bit of both.

Help this helps. :-)

---

### Post by dmizer on 2009-10-21
I suggest starting here: [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by druhboruch on 2009-10-21
I am running xbmsd on headless machine:

[http://xbmsd.sourceforge.net/](http://xbmsd.sourceforge.net/)

I have been running this for years without a problem.

---

### Post by johnycage on 2009-10-21
> **CharlesA said:**
> You can install the Gnome GUI by using:

```
sudo apt-get install ubuntu-desktop
```

As for connecting locally, you can just use VNC to get into the machine. I use SSH to connect to a terminial, and VNC to a virtual desktop if I need to.

TBH, I would include a video card, even if it's a really old/crappy one. There are times when I've had to actually get on the physical terminal to configure things and I have to attach a monitor/keyboard/mouse to it.

Help this helps. :-)Of course I think I will need to use monitor, keyboard during the setup. But my question is:
 Do I need to install GNOME/KDE? (I know how to do install it, thanks for the code though.) Am I be good with CLI? I mean in order to have apps such as samba SSH do I need 'install ubuntu-desktop' ?

thanks

---

### Post by CharlesA on 2009-10-21
You can install them from the command line.

apt-get install samba
apt-get install ssh

---

### Post by johnycage on 2009-10-21
> **CharlesA said:**
> You can install them from the command line.

apt-get install samba
apt-get install ssh
c'mon! I know the commands sir, :)
I want to know do I really need GUI? or it's fine with CLI for such setup?

---

### Post by buntunoob on 2009-10-22
theres many choices for UPnP, I am under the impression that the xbox dosent quite follow that standard thou.
[[COLOR=blue]http://www.xbmc.org/wiki/?title=UPnP_Sharing#UPnP_MediaServer_software[/COLOR]]("http://www.xbmc.org/wiki/?title=UPnP_Sharing#UPnP_MediaServer_software")
 
I pulled this from XBMC wiki
 
**[COLOR=black][FONT=Arial][[COLOR=#002bb8]XBMC Media Center[/COLOR]]("http://xbmc.org/")[/FONT][/COLOR]**[COLOR=black][FONT=Arial] (Linux/Mac/Windows), XBMC builds have since the 24th of January 2007 had a built-in UPnP MediaServer.[/FONT][/COLOR]
**[COLOR=black][FONT=Arial][[COLOR=#002bb8]GeeXboX ushare[/COLOR]]("http://ushare.geexbox.org/")[/FONT][/COLOR]**[COLOR=black][FONT=Arial], a free open source UPnP MediaServer for Linux and [[COLOR=#002bb8]NSLU2[/COLOR]]("http://en.wikipedia.org/wiki/NSLU2"). [/FONT][/COLOR]
**[COLOR=black][FONT=Arial][[COLOR=#002bb8]GMediaServer[/COLOR]]("http://www.nongnu.org/gmediaserver/")[/FONT][/COLOR]**[COLOR=black][FONT=Arial], a free open source UPnP MediaServer for Linux. [/FONT][/COLOR]
**[COLOR=black][FONT=Arial][[COLOR=#002bb8]MediaTomb[/COLOR]]("http://mediatomb.sf.net/")[/FONT][/COLOR]**[COLOR=black][FONT=Arial], a free open source UPnP MediaServer for Linux. [/FONT][/COLOR]
**[COLOR=black][FONT=Arial][[COLOR=#002bb8]CyberMediaGate[/COLOR]]("http://www.cybergarage.org/net/index.html")[/FONT][/COLOR]**[COLOR=black][FONT=Arial], a free open source UPnP MediaServer for Windows/Macintosh/Linux/UNIX, (reference implementation of UPnP MediaServer integrates into [[COLOR=#002bb8]MythTV[/COLOR]]("http://www.mythtv.org/") PVR for Linux) [/FONT][/COLOR]
**[COLOR=black][FONT=Arial][[COLOR=#002bb8]PyMedS[/COLOR]]("http://resnet.uoregon.edu/~gurney_j/jmpc/pymeds.html")[/FONT][/COLOR]**[COLOR=black][FONT=Arial], a free open source Python UPnP MediaServer for Windows/Macintosh/Linux/UNIX. [/FONT][/COLOR]
**[COLOR=black][FONT=Arial][[COLOR=#002bb8]Cidero Internet Radio Server[/COLOR]]("http://www.cidero.com/radioServer.html")[/FONT][/COLOR]**[COLOR=black][FONT=Arial], a free open source Java UPnP MediaServer for Windows/Macintosh/Linux/UNIX (Internet Radio Server only, SHOUTcast by default). [/FONT][/COLOR]
**[COLOR=black][FONT=Arial][[COLOR=#002bb8]Platinum UPnP SDK[/COLOR]]("http://sourceforge.net/projects/platinum/")[/FONT][/COLOR]**[COLOR=black][FONT=Arial], a dual license open source/commercial UPnP Media Control/Renderer/Server SDK for Windows, Linux, Mac. This is what XBMC uses.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][[COLOR=blue][FONT=Verdana]Server[/FONT][/COLOR]]("http://en.wikipedia.org/wiki/PS3_Media_Server")[/FONT][/COLOR][COLOR=black][FONT=Verdana][[COLOR=blue][FONT=Verdana]PS3 Media [/FONT][/COLOR]]("http://en.wikipedia.org/wiki/PS3_Media_Server"), a free UPnP MediaServer with on-the-fly transcoding [/FONT][/COLOR][COLOR=black][FONT=Arial]for Windows/Macintosh/Linux.[/FONT][/COLOR][COLOR=black][FONT=Verdana] (uses java)[/FONT][/COLOR]
 
Edit:  I have a PS3 and use [[FONT=Arial][COLOR=#002bb8]**MediaTomb**[/COLOR][/FONT]]("http://mediatomb.sf.net/"), after compileing and editing the .cfg it will serve everything to the UPnP 
  I compiled mine with [[COLOR=#336699]HOWTO: compiling mediatomb + ffmpegthumbnailer + a...[/COLOR]]("http://juliensimon.blogspot.com/2008/12/howto-compiling-mediatomb.html")

---

### Post by dmizer on 2009-10-22
> **johnycage said:**
> c'mon! I know the commands sir, :)
I want to know do I really need GUI? or it's fine with CLI for such setup?

That will largely depend on your capabilities in the command line. If you are comfortable in the command line, then no ... you don't need a GUI to serve media to a network.

---

### Post by johnycage on 2009-10-22
> **dmizer said:**
> That will largely depend on your capabilities in the command line. If you are comfortable in the command line, then no ... you don't need a GUI to serve media to a network.

That's what I wanted to hear!
Basically, why would you need GUI for a ^headless machine^? that's my main concern. 
But I'd still need samba, ssh & webmin.

---

### Post by druhboruch on 2009-10-22
You don't really need all these packages.
All you need is a vehicle to transfer your media to the server.

I am using NFS to do that.  I also have ssh installed on the server since it is headless machine.

In the past I tried using UPNP to stream media to xbox/xbmc, but it was slow and it was freezing frequently.  Since I installed xbmsd I have no problems at all.  Installation is very simple and takes only 3 minutes.

---

### Post by mutrax on 2009-10-24
Hi,

Well I run a similar set up, see as described in [this]("http://ubuntuforums.org/showthread.php?t=1286445&page=2") thread. As far as I know , mediatomb should do just fine streaming to an xbox. I use torrentflux for a webbased torrent client (no need to keep pc/xbox running).

You absolutely don't need a desktop. A webbased ui to help you trough some basic settings comes in handy though.

Regards,
Ed

---

### Post by mutrax on 2009-10-24
Okay, since there's so much ask for streaming to a 360 I'm looking into it myself.. seems this isn't done so easely .....:mad:

Fuppes looks promising to... gotta try it out sometime

---

### Post by johnycage on 2009-10-24
> **mutrax said:**
> Okay, since there's so much ask for streaming to a 360 I'm looking into it myself.. seems this isn't done so easely .....:mad:

Fuppes looks promising to... gotta try it out sometime
I heard mediatomb is not supported to XBOX 360 (but it is for PS3!)  
Can Samba addresses the issue? like showing media content on xbox tv that is there on file server and shared with home network?

---

### Post by mutrax on 2009-10-26
> **johnycage said:**
> I heard mediatomb is not supported to XBOX 360 (but it is for PS3!)  
Can Samba addresses the issue? like showing media content on xbox tv that is there on file server and shared with home network?IF a Xbox can see windows shares, It should see samba shares to.

---

### Post by johnycage on 2010-02-24
Just discovered an old thread but wonder how I did not find it earlier. 
Is it something similar to what his thread asks?
 
[http://ubuntuforums.org/showthread.php?t=775906](http://ubuntuforums.org/showthread.php?t=775906)

---

### Post by dmizer on 2010-02-25
> **johnycage said:**
> Just discovered an old thread but wonder how I did not find it earlier. 
Is it something similar to what his thread asks?
 
[http://ubuntuforums.org/showthread.php?t=775906](http://ubuntuforums.org/showthread.php?t=775906)

Yes, but keep in mind that the thread is old. You should verify everything. Also, you'll probably only need to follow the "twonkymedia" sections under step 7 and 8.

Edit:
Looks like twonkymedia server is not an open source app. You'd have to pay for it.

---

### Post by BobVila on 2010-02-25
> **dmizer said:**
> Yes, but keep in mind that the thread is old. You should verify everything. Also, you'll probably only need to follow the "twonkymedia" sections under step 7 and 8.

Edit:
Looks like twonkymedia server is not an open source app. You'd have to pay for it.

Twonky is a paid app, which is sad, but I can say from experience that it's been the best of the bunch for me in streaming to my ps3s and xbox360s. 

Granted, I haven't taken a look at the competition in about six months...

---

### Post by Niksss on 2010-06-01
hey..

i hav mediatomb and cidero runnin on the same system.. 
  mediatomb is runnin fine.. but cidero is not detectin it.. :(
 
Wat changes are needed in net configurations to make it runnin..

Thaks in advance

---

### Post by spynappels on 2010-06-01
For a good, simple DLNA streamer, have a look at minidlna as well, I have that streaming to a few different laptops, as well as to an original XBox running XBMC and XBMC running on 2 Ubuntu Laptops too.

Not sure how it works with XB360, but it will install in 30 seconds and can be dumped in less time if it does not work. It runs completely selfcontained from you home folder if you want.

I run the exact same setup as the OP proposes, with the exception that my LAMP servers run on a separate Virtual Host. I use both Samba and DLNA (uPNP) to play media, but DLNA usually gives superior results.

---

### Post by srivo on 2010-06-01
I have been using XBMC on an old xbox with a ubuntu server for more than 2 years.

The server is running SAMBA and act as a file and print server also for 3 others laptop (kid, wife and me). All picture, music and video are on the server and available to the XBOX on the living room.

I use ssh and freeNX to manage the server.

---

### Post by Niksss on 2010-06-01
[SIZE=3]Hey all...
  Mediatomb is workin fine on my system.. but cidero is not detecting it... wat are the other media controllers that work  with mediatomb..?

mediatomb and the cidero are runnin on the same system.. So in the ip settings wat changes shud i make..? sorry for soundin such a newbie..:sad:

Thanks in advance[/SIZE]

---

