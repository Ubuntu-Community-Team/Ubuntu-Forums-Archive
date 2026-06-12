---
title: "Was given old computer, will it work as a server"
date: 2008-05-07
forum: Server Platforms
---

### Post by phread59 on 2008-05-07
I was given an old Dell today.  I pulled it open and found the following:

Pentium III 1 gighz
320 meg ddr 100
200 watt power supply
20 gig hard drive(I have a 500 ready to drop in)
No ethernet (I also have a 10/100 card in another old machine to use)
2X AGP card (no on board video)
CD burner
100meg ZIP Drive
Floppy

Can I use it for a file server.  I was going to build one later on but this fell into my lap.  I realize it is at the low end of usable.  I just want it to download torrents and eventually I would like to hook up a few external hard drives for storage and have them accessable to this machine.  I would also like to store music in it.  I would pick up another 500 gig hard to flush it out.

Do I need more memory?  Will a 1 gig PIII have enough poop to do it.  I realize up front that this one will not have a GUI in it.  A full desktop would be too much for it with the server backend.  I have a cable modem so connections will be no problem.  It will get a wired router and switches as necessary.

Any one have feelings on this for it's suitability.  Only real bad part is the power supply is minimal and case cooling kinda sucks.  May need PSU updated.  Lemme know.

Mark Shuman

---

### Post by tamoneya on 2008-05-07
pop in the ethernet card and you should be set.  I would use xubuntu or puppy linux.

---

### Post by linuxisfree on 2008-05-07
> **phread59 said:**
> I was given an old Dell today.  I pulled it open and found the following:

Pentium III 1 gighz
320 meg ddr 100
200 watt power supply
20 gig hard drive(I have a 500 ready to drop in)
No ethernet (I also have a 10/100 card in another old machine to use)
2X AGP card (no on board video)
CD burner
100meg ZIP Drive
Floppy

Can I use it for a file server.  I was going to build one later on but this fell into my lap.  I realize it is at the low end of usable.  I just want it to download torrents and eventually I would like to hook up a few external hard drives for storage and have them accessable to this machine.  I would also like to store music in it.  I would pick up another 500 gig hard to flush it out.

Do I need more memory?  Will a 1 gig PIII have enough poop to do it.  I realize up front that this one will not have a GUI in it.  A full desktop would be too much for it with the server backend.  I have a cable modem so connections will be no problem.  It will get a wired router and switches as necessary.

Any one have feelings on this for it's suitability.  Only real bad part is the power supply is minimal and case cooling kinda sucks.  May need PSU updated.  Lemme know.

Mark Shuman

For a file server? Should be fine... and as said earlier Xubuntu or Puppy Linux would probably be the best choice of  OS (IMHO).

---

### Post by kerry_s on 2008-05-07
old! those are very decent specs, you can run what ever you want.
mines 450mhz 256mb ram. :(

---

### Post by netztier on 2008-05-08
> **phread59 said:**
> 
Pentium III 1 gighz
320 meg ddr 100
200 watt power supply
20 gig hard drive(I have a 500 ready to drop in)
No ethernet (I also have a 10/100 card in another old machine to use)
2X AGP card (no on board video)
CD burner
100meg ZIP Drive
Floppy


If your LAN supports it, make that NIC a gigabit card (Intel PRO/1000 desktop series adapters warmly recommended; server adapters are a lot more expensive), leave the 20Gig drive to hold the ubuntu root and swap partitions and then *add* the 500 gig drive for data, and then watch the thing fly!

Mine's a P-III 500 with 512MByte RAM, two S-ATA 500GB Disks (with software RAID-1 for mirroring). When serving with NFS, it shoves up to 60MByte/s onto the wire (with jumbo frames, all data cached ).

Of course, adding a bit of RAM will help - but the specs you gave are a very decent starting point.

regards

Marc

---

### Post by hyper_ch on 2008-05-08
if you want to use it as file server, you don't need a gui at all and 10 GB of root is more than enough... in the end you want to run as little as possible on a server so you don't want to install many applications and hence 10 GB is enough... even 4-5 GB should be sufficient.

---

### Post by CREEPING DEATH on 2008-05-08
The IDE controller on that old mobo probably won't support over 137 GB HDD.  Otherwise it sounds OK.  I've run full ubuntu-desktop on a machine with less CPU but a bit more RAM (384 MB).
Don't fear testing out Debian, it's a lot lighter but remarkably familiar.

CD

---

### Post by exaviorn on 2008-05-08
I run my server on half the specs you are posting!:lolflag:As long as you don't use it as a home computer as well that should be the perfect specs!!

---

### Post by rickh57 on 2008-05-08
I have an old Dell PII 400mhz computer with 384mb of RAM and it works fine as a server under Linux.

---

### Post by moonpup on 2008-05-08
I have an old PII 450 with 384mb of ram and it runs fantastic. It's running RHEL 5 with no gui and is strictly console. As a file/print, squid proxy and ssh server, it's awesome and still chugging along!

I wish I had the specs of the machine you got :)

---

### Post by phread59 on 2008-05-08
Thank you fellas for the prompt responses.  Xubuntu it will be.  I thought of the 137 restiction this morning Creeping.  I may just stuff an ide or a sata card in it.  The card should have it's own controller so I can loose the 137 cap.  So far I don't have a penny into it.  I just robbed pieces from another old machine to get where I am.  I also see the gigabit lan.  But routers and so on in my price range are capped at 100.  So is my modem.  I may just do it anyway.  But right now I'm still setting things up.  BTW should I use the full Xubuntu with desk top.  Or just set up a (gulp) CLI only set up.  Gonna be a lot of typing to set it up.  Any suggestions on how to set up Xubuntu?

Mark Shuman

---

### Post by wdaniels on 2008-05-08
> **phread59 said:**
> Or just set up a (gulp) CLI only set up.  Gonna be a lot of typing to set it up.

Not really - I can't think of all that much in a typical desktop GUI that's helpful for configuring a server anyway.  You'd probably be better off with something like Webmin for that, which is a web interface but you don't need to run apache for it or anything - it has it's own mini http server built in.

Similarly, you might want to take a look at [firefly]("http://www.fireflymediaserver.org/") for sharing music through DAAP (rather than just sharing the music files) since it also has web-based configuration.

---

### Post by CREEPING DEATH on 2008-05-09
CLI ought to be fine, learn to use SWAT and CUPS, you realy don't even need webmin.  Install the OS, install SSH Server, and go!

CD

---

### Post by altonbr on 2008-05-09
Here is what I would do:

[LIST]
[*]Install Ubuntu 8.04 server: [http://releases.ubuntu.com/8.04/ubuntu-8.04-server-i386.iso](http://releases.ubuntu.com/8.04/ubuntu-8.04-server-i386.iso)
[*]Install SSH
You can still use NFS for file transfer, but this will allow you to connect to your computer without a monitor or keyboard attached :KS
```
sudo aptitude install ssh
```
[*]Configure SSH
Change the port from the default (to help avoid dictionary attacks) and do not allow 'root' to login...
```
sudo vim /etc/ssh/sshd_config
```
> # Port 22
Port 2222
# PermitRootLogin yes
PermitRootLogin no

[*]Restart SSH
```
sudo /etc/init.d/ssh restart
```
[*]Set a static IP address
```
sudo vim /etc/network/interfaces
```
Just becareful, your Class-C network may be 192.168.0.*, 192.168.1.* or 192.168.2.* so adjust accordingly
> #iface eth0 inet dhcp
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

[*]Restart your networking
```
sudo /etc/init.d/networking restart
```
[*]Check to make sure your IP address is set
```
ifconfig
```
[*]Connect to your server from your desktop
> #-p port
# Port to connect to on the remote host.  This can be specified on a per-host basis in the configuration file.
#-v      Verbose mode.
# Causes ssh to print debugging messages about its progress.  This is helpful in debugging connection, authentication, and configuration problems.  Multiple -v options increase the verbosity.  The maximum is 3.
```
ssh -v -p 2222 <username>@<ip_address>
```
[/LIST]

Good luck!

---

### Post by phread59 on 2008-05-09
Ok I guess the way to go would be just to load Xubuntu and remove the desktop.  Would that be right or is there a minimal desktop that basicly ony has cli on it.  If there is what is the package I need to install?  Never installed a distro without a desktop before.  I agree it really is not needed here.  And would take up too much resources.  Maybe Webmin?  Never heard of it.  I guess I'll take a look at it later.  I'll look into firefly as well.

Mark Shuman

---

### Post by altonbr on 2008-05-09
Did you feel comfortable running my commands above? That's all you need to run a server in CLI. It will enable you to have it running without a monitor/keyboard attached as well.

If you want webmin after you run my mini-tutorial, run this:

```
wget http://prdownloads.sourceforge.net/webadmin/webmin_1.410_all.deb && sudo dpkg -i webmin_1.410_all.deb
```

and that's it.

---

### Post by hyper_ch on 2008-05-09
changing port from 22 to 2222 won't help at brute-forcing....

better to use deny hosts or fail2ban

---

### Post by phread59 on 2008-05-09
Yea Altonbur that looks straightforward enough.  I'm defanatly NOT afraid of the big bad CLI.  I am just hoping the server edition is as light as I can get in the Ubuntu line.  I just want to stick with Ubuntu without doubt.  Puppy linux is tempting.  But the support for Ubuntu here is overwhelming and I want to stay here.  I realize the software needs to be lean with this machine.

One dumb question.  Will I need the network set up and ready to run to install the server software?  This is the first server I've even contemplated, let alone set up.  I may need my hand held some.

Mark Shuman

---

### Post by CREEPING DEATH on 2008-05-09
> **phread59 said:**
> One dumb question.  Will I need the network set up and ready to run to install the server software?  This is the first server I've even contemplated, let alone set up.  I may need my hand held some.

Webmin can install the needed software for you.  I'd seriously suggest straight Debian for a server, it's a lot lighter, Ubuntu mainly has the advantage of a beautifully configured desktop.  Webmin has it's own .deb repos as well.

CD

---

### Post by altonbr on 2008-05-09
> **phread59 said:**
> Yea Altonbur that looks straightforward enough.  I'm defanatly NOT afraid of the big bad CLI.  I am just hoping the server edition is as light as I can get in the Ubuntu line.  I just want to stick with Ubuntu without doubt.  Puppy linux is tempting.  But the support for Ubuntu here is overwhelming and I want to stay here.  I realize the software needs to be lean with this machine.

One dumb question.  Will I need the network set up and ready to run to install the server software?  This is the first server I've even contemplated, let alone set up.  I may need my hand held some.

Mark Shuman

I really think if you stayed with the default Ubuntu server you'd get the best support. I can't say if straight Debian is lighter or not (or even Xubuntu server), but I do know that Debian is different enough (just enough) that some help you get here may not work -- this is more so because the repositories are not 100% the same.

I run Ubuntu servers ranging from quad-core Xeons with 8GB of RAM to single-core Celerons with 256 MB of RAM and Ubuntu server runs on them just fine.

Also, your best bet for your server is to completely install Ubuntu on the 40 GB hard drive (even though you won't need that much at ALL) and use your external hard drives for /home or /var (which ever you're going to use to store your data).

---

### Post by CREEPING DEATH on 2008-05-10
Debian uses a specific kernel (486, 686, K7, bigmem, etc.) instead of the idiot-resistant 'generic' kernel Ubuntu uses.

CD

---

### Post by phread59 on 2008-05-11
Well I downloaded the Ubuntu server software to my desktop.  I will burn the CD later.  I do need to get a hardware drive controller to allow me to get past the 137gig barrier in my machine's bios.  I'm not even gonna try to find new bios settings for this thing.  I looked into Webmin and it looks just fine.  I think I will load the server edition and put Webmin into it.  As someone before noted this kernel is about idiot proof.  I think that is gonna be a big plus for me.  'Cause I'm an idiot:).

As in "Nothing is foolproof to the sufficiantly talented fool,,, for I am that fool!"

Thanks for the help guys.  Like I said I'm going to get the hardware card soon.  I may pick up a second 500 gig drive too.  When I get all the pieces together I'll come back here for more help.  

I did consider Debian for a long time.  But I just keep coming back to the support that exists for Ubuntu.  So I'll give up some speed for the access to this wonderful community.  You guys are the greatest.  Thanks for taking a server noob by the hand.  I cannot thank you guys enough.

Mark Shuman

---

### Post by altonbr on 2008-05-11
> **phread59 said:**
> Well I downloaded the Ubuntu server software to my desktop.  I will burn the CD later.  I do need to get a hardware drive controller to allow me to get past the 137gig barrier in my machine's bios.  I'm not even gonna try to find new bios settings for this thing.  I looked into Webmin and it looks just fine.  I think I will load the server edition and put Webmin into it.  As someone before noted this kernel is about idiot proof.  I think that is gonna be a big plus for me.  'Cause I'm an idiot:).

As in "Nothing is foolproof to the sufficiantly talented fool,,, for I am that fool!"

Thanks for the help guys.  Like I said I'm going to get the hardware card soon.  I may pick up a second 500 gig drive too.  When I get all the pieces together I'll come back here for more help.  

I did consider Debian for a long time.  But I just keep coming back to the support that exists for Ubuntu.  So I'll give up some speed for the access to this wonderful community.  You guys are the greatest.  Thanks for taking a server noob by the hand.  I cannot thank you guys enough.

Mark Shuman

No problem, but I *think* you can use a 500GB hard drive if it's a USB external. Someone correct me if I'm wrong...

---

### Post by phread59 on 2008-05-11
I think I may be misleading somewhat.  I have an IDE 500gig internal drive I will put in the server box.  I want to get another as well. I would like 2 drives inside the server.  I may also take someone before's suggestion and use the current 20 gig to hold the op system. I need the card to access the full 500 gig.  I also have 2 external 500 gig drives.  These I use as storage on my main pc.  I would like at some time in the future to have them as network storage.  But for now they are going to be only storage for my main PC. 

Maybe a stupid question is in order.  Could I use externals instead of internals?  In other words instead of using internal drives to store the server's data should I use externals?  It would solve the 137 gig problem but would really slow down the machine.  It only has USB1's in it now,  I would have to add an USB 2 card anyway.  Suggestions?

Mark Shuman

---

### Post by altonbr on 2008-05-12
> **phread59 said:**
> I think I may be misleading somewhat.  I have an IDE 500gig internal drive I will put in the server box.  I want to get another as well. I would like 2 drives inside the server.  I may also take someone before's suggestion and use the current 20 gig to hold the op system. I need the card to access the full 500 gig.  I also have 2 external 500 gig drives.  These I use as storage on my main pc.  I would like at some time in the future to have them as network storage.  But for now they are going to be only storage for my main PC. 

Maybe a stupid question is in order.  Could I use externals instead of internals?  In other words instead of using internal drives to store the server's data should I use externals?  It would solve the 137 gig problem but would really slow down the machine.  It only has USB1's in it now,  I would have to add an USB 2 card anyway.  Suggestions?

Mark Shuman
If it was USB 2.0, I'd say do it, but since USB 1.1 only has a 1.5MB/s throughput compared to USB 2.0's 60MB/s, you're looking at VERY slow transfers for GB-sized material. I would try and update that BIOS and put them in internally or get a new mobo that supports USB 2.0 (which sort of defeats the purpose of using an older PC as a server).

I think you'd be surprised to find that your computer can read the 500GB hard drive. If you BIOS can read it, then you're laughing. I have a [HP Pavillion a200n](http://www.amazon.com/Pavilion-a200n-Desktop-2-40-GHz-Celeron/dp/B0000A276T) with an [Intel 845GL chipset](http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph07813&lc=en&cc=ro&product=329403&dlc=ro) and it was able to take a 500GB IDE drive quite easily.

---

### Post by lespaul_rentals on 2008-05-12
That will work.  You should put Debian on it.  :D

---

