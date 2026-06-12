---
title: "NAS device OS be replaced with Linux LXDE distro?"
date: 2011-05-08
forum: Server Platforms
---

### Post by hyoumoku on 2011-05-08
Kindly move to other subforums if it's necessary as I'm not sure where I can post my question ^^;;

Is there a suggested and recommended NAS device (preferably only an enclosure which I can change the SATA HDs) in the market that the OS used in the NAS device can be changed by installing either Lubuntu or Mint LXDE?

These are the things I am looking for with the NAS device
> Accessible using Linux, Windows and OSX
> Low powered and power saving as it will be open 24/7 plugged into a UPS
> Has to have all of these programs: Dropbox, XChat, Chromium, JDownloader, utorrent (through Wine), VNC, TeamViewer, FreeNX
> can be remotely accessed by VNC, TeamViewer and FreeNX (though I'm having trouble setting up NX at the moment)
> Hopefully the price would be around more or less US$100? (And hopefully available in the Philippines where I live)

I have something similar going on with my relatively old (it's core 2 duo I think) monitor-busted laptop for around a year now. But the discspace of that is only 160GB and it's somewhat a pain to always migrate the files. I'm also thinking it would be good storage of lots of big pictures as my brother is a hobbyist turned professional photographer and I am an apprentice of his. It will also be stored with lots of videos and sound files that can be accessed at least through the network.

I'm thinking of at least having it 2TB but there currently are two problems with the current laptop namely: the USB plug of the laptop has serious problems that it disconnects the USB2 randomly then makes it USB1 speed. Secondly, it has bad heat management that it shut downs randomly without a word (or so I think it's because of that it shuts down).

As much as I would like to build from the junk of old computers we don't use, I don't think I have the time recently to make my own NAS and experiment (and even though I'm excited in learning and setting up RAID - I don't think I have that luxury of a time at the moment). 

I've been reading last night of devices like Buffalo Link Station and such but most if not all of them have their own preinstalled OS and Google searches doesn't stumble me to an. What I want actually is install Mint LXDE or Lubuntu as I prefer that it has the features and programs I'm currently using right now with the 160GB network storage.

Is there a NAS device in the market I can install Lubuntu or Mint LXDE (yeah, I think LXDE will be the best environment for the things I will do for it)? Or is it still better that I make some time and build my own NAS? Please advice *bows deeply*

PS: I've been checking for NAS devices available at a tipidpc.com (a very big local tech selling community) and found these:
Linksys Cisco NAS 200 dual SATA bay - [http://tipidpc.com/viewitem.php?iid=9699627](http://tipidpc.com/viewitem.php?iid=9699627)
Buffalo Link Station Duo LS-WXL/E - [http://tipidpc.com/viewitem.php?iid=9779871](http://tipidpc.com/viewitem.php?iid=9779871)
EtrayZ 2-bay [http://tipidpc.com/viewitem.php?iid=8525668](http://tipidpc.com/viewitem.php?iid=8525668)

Do any of the abovementioned devices can be installed with Linux LXDE distro?

---

### Post by kerry_s on 2011-05-08
you'll have to build your own to get what you want.

---

### Post by hyoumoku on 2011-05-08
So in other words, it is not possible to install a Linux LXDE distro in all NAS devices in the market? Buffalo if I'm not mistaken uses Linux as its OS but I am not sure if it's possible to install an LXDE distro in it. 

Any points where you can advice of a NAS device?

---

### Post by volkswagner on 2011-05-08
Most NAS devices don't have the needed horsepower to run a full blown OS, let alone one that has a GUI.

As mentioned you will need to build your own.  

As far as your failing laptop, you may be able to fix it to a reliable state.  Have you removed the fan to clean out the dust bunnies?  Also most heat shutdown issues can be resolved by removing the CPU cooler to clean and replace the thermal paste, along with cleaning the fan.

If the laptop has hardware issues with USB, you may be able to get an add on card if it has PCMCIA slot.  Perhaps a PCMCIA card with an [eSATA connection]("http://www.newegg.com/Product/Product.aspx?Item=N82E16839113007&cm_re=pcmcia_esata-_-39-113-007-_-Product") or firewire would give you better disk performance.

Or perhaps you can sell the laptop and use the money to get going on a unit like this [Atom barebones unit]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856119037").

---

