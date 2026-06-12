---
title: "Home Server Help!"
date: 2008-08-01
forum: Server Platforms
---

### Post by flatline on 2008-08-01
Posted this to the wrong forums before... I think this is the correct place for my questions...

So I am setting up a home server. I need a little guidance though, as A) This is my first DIY computer, and B) My linux experience is limited to basic desktop use.

The hardware I have coming in is this:

[LIST]
[*]Asus P5E WS PRO Server Motherboard
[*]4GB (2x2) Kingston DDR2-800 ECC RAM
[*]Xeon E3110 3.0GHz Wolfdale dual-core CPU
[*]2x 1TB Western Digital GP HDDs
[/LIST]

I saw on newegg that someone had 8.04 running on this mobo, so I am hoping that it will work. Unfortunately, I saw an older thread on here that suggested that the RAID controller built-in prevents Ubuntu from installing... *fingers crossed* If this mobo doesn't work, I will probably trade it in for the Asus P5BV-C.  Apparently, the WS PRO board is also affected by the whole Foxconn mess from the past week... lovely!

Here is what I want to use it for:

[LIST]
[*]File Server - My house uses Macs and XP (Samba?)
[*]Torrent Server - Using uTorrent or something similar, provide a Web-based GUI that I can set to download torrents.
[*]Print Server - Provide a tether for printing from laptops (CUPS?)
[*]Media Streaming - This is the tricky part. I want to be able to stream media to my X-Box 360/1080p TV. I am hoping Fuppes works, because I like the on-the-fly transcoding.
[/LIST]

I know I said that I am setting up a home server, but I'm wondering if Server Edition of Hardy is the right way to go, since I'm probably going to want a GUI. Yes, it will be running headless most of the time, but when I remote into it I would prefer to have an actual desktop. Also, I might be doing virtualization now and then. **So the question is, Desktop or Server Edition?** Follow-on: Should I stick with the 32-bit edition? I'm afraid I'll run into issues trying to get Fuppes running as it is, 64-bit compatibility seems like asking too much.

All (constructive) comments appreciated!

Matt

---

### Post by flytripper on 2008-08-01
if you get fuppes working on the transcode side of things please post a how to cao s i couldnt.

---

### Post by hrod beraht on 2008-08-01
> **flatline said:**
> Torrent Server - Using uTorrent or something similar, provide a Web-based GUI that I can set to download torrents.


The best torrent solution on a headless server is definitely **rTorrent + Screen** :)

Bob

---

### Post by kvizz on 2008-08-01
for headless torrent server i would recommend torrentflux

---

### Post by yeaitsdark on 2008-08-01
I would recommend the Server edition. It's just far faster a system. Samba isn't difficult at all to edit via command line. 

Webmin makes life really easy for administering your server with a nice little web gui. 

[http://www.webmin.com/](http://www.webmin.com/)

I use Azureus for my p2p client, and there's an great (really great and awesome) plugin for Azureus called "AzSMRC". 

If you choose Azureus:

[http://www.azureuswiki.com/index.php/HeadlessSwingUiHowTo](http://www.azureuswiki.com/index.php/HeadlessSwingUiHowTo)

[http://www.azureuswiki.com/index.php/ConsoleUI](http://www.azureuswiki.com/index.php/ConsoleUI)

Will teach you a way to set it up using the console. Also, it has a normal web based plug in if you prefer that. It does use java, but I find the performance issue negligible.

For media streaming, I use Tversity [http://tversity.com](http://tversity.com). Sadly, this is a Windows application. I only mention this because it works flawlessly out of the box with Xbox360 and does transcoding on the fly.

I personally do have a windows server machine, and it's job (among a few others) is to run Tversity. However, in "good" news some people have reported to get it running in a virtual machine. Your system may be able to pull it off. My server machine that runs Tversity is a dual p3 with 1gb of ram, and it only hangs here and there.

Read last post of this:
[http://forums.tversity.com/viewtopic.php?f=2&t=11328](http://forums.tversity.com/viewtopic.php?f=2&t=11328)

---

### Post by ultrarazen on 2008-08-05
I agree with kvizz, torrentflux-b4rt is the best piece of software I've used for managing torrent's on a server. It's controlled completely through a web based GUI.
You can get it here - [http://tf-b4rt.berlios.de/]("http://tf-b4rt.berlios.de/")

As for the printer, you can share it out with Samba as well as your file-shares.

---

### Post by flatline on 2008-08-05
Thanks for all the comments on the torrent app, but I'm afraid that will probably be the easiest obstacle to overcome.  

I didn't do my homework enough - the WS PRO mobo has no onboard video.  Any suggestions for a video card?  This board has 2 PCIe 2.0 x16 slots, a PCIe x1, a PCI-X, and two PCI slots.

I'm not up on all the new video cards (or even the old ones really).  I don't plan on gaming, obviously, as this is a server.  However, I did get a good deal on a SATA Blu-ray drive.  Therefore, I would like whatever card I end up getting to be HDCP (ugh!) compliant so I can play the blu-rays to my big TV (probably having to use windows in VM or something :( )

Thoughts?

---

### Post by hyper_ch on 2008-08-05
rtorrent + screen + openssh-server

do you have another video card that you can use temporarily? You just need to have a videocard in there while installing the server edition and setting network and install openssh-server...

afterwards you can connect from any computer through ssh and do the rest.

---

### Post by flatline on 2008-08-05
I thought of just dumping a crappy VGA card in there, but since I have this blu-ray drive, it would be nice to have an HDCP card so I can play 1080p content.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814125230](http://www.newegg.com/Product/Product.aspx?Item=N82E16814125230)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814102753](http://www.newegg.com/Product/Product.aspx?Item=N82E16814102753)

Was looking at those two.  Is it still a better bet to go with NVIDIA chipsets over ATI?

---

