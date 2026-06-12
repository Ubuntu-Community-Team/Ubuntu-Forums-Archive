---
title: "itunes in wine?"
date: 2010-10-28
forum: Wine
---

### Post by melinda on 2010-10-28
Hi  not sure if Gen Help is the right category or not...

I want itunes.  Does it run well in wine?  

How do i install??  i am clueless here. 

thanks

Melinda

---

### Post by aysiu on 2010-10-28
> **melinda said:**
> Hi  not sure if Gen Help is the right category or not...

I want itunes.  Does it run well in wine?  

How do i install??  i am clueless here. 

thanks

Melinda
iTunes does not run well in Wine. More details here:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

and here:
[http://www.psychocats.net/ubuntu/itunes](http://www.psychocats.net/ubuntu/itunes)

---

### Post by Verbeck on 2010-10-28
you can check the wine appdb for supported programs

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)


itunes doesn't seem to run well

---

### Post by jschall1 on 2010-10-28
I'm sorry, but itunes is the most horrific, bloated, slow piece of dung I have ever had the displeasure of using. So, I can't help but ask:
WHY? Why do you want it?
If you have an apple mp3 player, I believe there's support for loading music onto most or all of them. Granted, they change the hash code in their embedded music databases every other week in order to lock in itunes, so you might be out of luck depending on which week it is at the moment. If so, I've seen virtualbox work.
That or you can break your shackles, sell your device and buy one of the many mp3 players on the market, that, despite claims to the contrary by millions of ravenous apple ipod users, DO work well. Hell, you can probably come out of that deal with a better mp3 player AND some cash in your pocket.

If you want to use it for your music collection, you should try rhythmbox and amarok, and if neither of them suit your taste, you should probably go buy a mac.

---

### Post by melinda on 2010-10-28
I did read that it doesn't run well in wine.  

and as for jschall1:  

why itunes?  because with itunes I can reset my ipod, download firmware and updates.

Rhythmbox is the BIGGEST piece of DUNG I have had the unfortunate experience working with.  It does not sync and transfer playlists between ipod and library.  Cannot organize playlists via artists albums tracks. etc etc etc.  DRIVES ME BONKERS.  plus it adds playlists several times to my ipod so I have duplicate playlists, but doesn't show in program for me to delete duplicates. etc etc etc.  

if there is a way I can run itunes it would be soo much easier organizing my music and syncing with the thing. plus the hardware updates and restore options.


does anyone have another option to run itunes thru?

thanks
melinda

---

### Post by Elfy on 2010-10-28
So you read the rhythmbox option and decided to troll - did you see either the link in aysiu's post to the psychocat itunes page - and look? Jschall also offered amarok and a virtual machine.

The result of a search for itunes - [http://www.google.com/cse?cx=012285703143635244993:i9yr8qlpb18&q=itunes](http://www.google.com/cse?cx=012285703143635244993:i9yr8qlpb18&q=itunes)

Edit - moved to Wine forum

---

### Post by mastablasta on 2010-10-28
buy a Mac?

or run a virtual maschine (if you still want Linux)

seriously you are suing one of the most closed systems in the world (apple makes sure of that). they tie you to their devices and systems.

Who says you need to use rythmbox? there are plenty playlist editors/players out there. some can do with thousands of songs easily. there was one link here in a forum for a good and very fast one. can't remember where exactly.

edit: Found it download: [http://sourceforge.net/projects/guayadeque/](http://sourceforge.net/projects/guayadeque/)
website: [http://guayadeque.org/forums/index.php?p=/docs](http://guayadeque.org/forums/index.php?p=/docs)

---

### Post by melinda on 2010-10-28
@ mastablasta  

as for a mac, my sister has one, but she is not close, and I cannot afford a new system right now. 

I am trying to get some options of what to use as a player - if you can remember that link or names of other good players that are far better I would LOVE to know about them.  Like I said I am clueless as what to do -- other than try and run itunes in some type of windows simulator like wine.

@ forestpiskie

I tried amarok.. after I updated to the last Ubuntu 10.4 Lucid Linux update I could not get amarok for songbird to work.  Unable to sync music to the ipod whatsoever. 

Melinda

---

### Post by jschall1 on 2010-10-28
I think your options here are:
Run windows in a virtual machine.
Get a normal mp3 player. You know, the kind that acts like a normal USB storage device and you can just drag & drop your music onto it.
Figure out a way to make rhythmbox, amarok, or other music application sync to the ipod. This might take some screwing around.

---

### Post by maddy_in65 on 2010-10-28
There is a dedicated app called GTKipod, Ipod managment center which i use to transfer music from system to Ipod. You can find it Ubuntu software managment center

---

### Post by d10sfan on 2010-10-28
Ive had some success with Banshee in terms of iphone (ipod) syncing. It was able to see all my songs and I synced with it. However, for updates and the like, you are probably best off using a virtual machine to sync your ipod if you are trying to do anything fancy with it. 

If you want to do the VM route, you should be able to share your music folder with your vm and that way you wont have to have two copies of your music.

---

### Post by aysiu on 2010-10-28
I don't really see the point in bagging on iTunes. If you don't like it that's fine, but that doesn't really help the people who want its functionality.

I think the bottom line is that there are ways to get *most* of the functionality of an iPhone or iPod Touch on Linux but you won't get the ideal experience that way.

So your options are to put up with that inconvenience, use Windows or Mac, or get a different (more Linux-friendly) device. iTunes on Linux isn't going to do you much good if you can even get it installed via Wine.

---

### Post by TheAnachron on 2010-11-02
Just wait for [libimobiledevice]("http://www.libimobiledevice.org/") to finish.

Btw, I am currently using iTunes 10 in an emulated win7 enviroment.

---

### Post by sandyd on 2010-11-03
this is a offhand coment - depending on what ipod you have, you can install
rockbox ([http://rockbox.org](http://rockbox.org)) on it to enable drag-and-drop transfers of your music.

According to the rockbox manual, you will be able to go into both the origional ipod interface and the rockbox interface, but songs will be transfered seperately (i.e. music added to rockbox will not show up in the default ipod interface). Therefore, you might need to borrow a mac or a computer with windows, wipe the ipod, and install rockbox.

---

### Post by jlab on 2010-11-10
I have itunes successfully running right now on wine 1.2. The other catch is 8.2 seems to be the most stable version to run on wine and the store does not work. I'm not sure if iPod syncing works or not but genius does work

Here's what I did:
1. install itunes 7.2
2. install itunes 8.2

You will also have to recreate your library if it was created with a earlier verison of itunes

---

