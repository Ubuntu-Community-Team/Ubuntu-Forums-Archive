---
title: "Portable Synaptic Idea"
date: 2008-08-03
forum: The Cafe
---

### Post by BGFG on 2008-08-03
Hi All,
Please take a look at this idea and tell me what you think. The more advanced people could indicate as to it's 'difficulty' of implementation.

Thanks for your time.

[http://brainstorm.ubuntu.com/idea/11772/](http://brainstorm.ubuntu.com/idea/11772/)

---

### Post by init1 on 2008-08-03
> **BGFG said:**
> Hi All,
Please take a look at this idea and tell me what you think. The more advanced people could indicate as to it's 'difficulty' of implementation.

Thanks for your time.

[http://brainstorm.ubuntu.com/idea/11772/](http://brainstorm.ubuntu.com/idea/11772/)
Interesting concept. You could always just download the .deb, but you would still need the dependencies. 
The way this could be implemented is you would supply a list of apps you want for this portable synaptic. Then, when you run it from a computer with internet, it reads the list of apps, and downloads the .debs and all the dependencies. This wouldn't be very hard to do, but it would require both Windows (unless the Internet cafe uses Linux) and Linux apps.

---

### Post by tamoneya on 2008-08-03
> **BGFG said:**
> Hi All,
Please take a look at this idea and tell me what you think. The more advanced people could indicate as to it's 'difficulty' of implementation.

Thanks for your time.

[http://brainstorm.ubuntu.com/idea/11772/](http://brainstorm.ubuntu.com/idea/11772/)

I think this is just APTonCD: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by BGFG on 2008-08-03
> **tamoneya said:**
> I think this is just APTonCD: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

You're wrong. I looked at APTonCD also. with that program a linux machine that HAS a connection can create a portable repo based on programs already installed and cached.
But users like myself, who don't have access to other linux users with net connections would be made self sufficient in the event that their only access is a cafe or work or a generous friend. 

This would have been a great tool back when i had no net.

---

### Post by BGFG on 2008-08-03
> **init1 said:**
> Interesting concept. You could always just download the .deb, but you would still need the dependencies. 
The way this could be implemented is you would supply a list of apps you want for this portable synaptic. Then, when you run it from a computer with internet, it reads the list of apps, and downloads the .debs and all the dependencies. This wouldn't be very hard to do, but it would require both Windows (unless the Internet cafe uses Linux) and Linux apps.

Yes, the portable version could store the existing library and dependancy info on the machine as an text or xml file. (or just an effecient format) and that file would be used to refer to when downloading from the repo's externally.
But i see that the main issue would be plug and play functionality in windows. I still believe it could be done :)

Imagine in all the developing countries where they are trying to implement a cheap computer using linux. One guy from a community could go to town, get updates then come back and update the entire town.

A stretch i know. But i hope you get what i mean.

---

### Post by bobbocanfly on 2008-08-03
I dont think it would be too difficult to do actually.

2 shell scripts would do it:

portable-synaptic-get <package> <package> would get the packages, download them and add them to an 'index' file which would list the packages in the order they need to be installed (dependencies first)

portable-synaptic-install <index-file> would get the index file and loop through it installing them in the correct order.

---

### Post by BGFG on 2008-08-03
I definitely think this would be beneficial to the community at large...

---

### Post by gn2 on 2008-08-03
Just buy a full set of Debian DVD's from one of the many suppliers?

---

### Post by BGFG on 2008-08-03
> **gn2 said:**
> Just buy a full set of Debian DVD's from one of the many suppliers?

Again, desperately missing the point. I'm from the caribbean. Please refer me to one such dealer in Trinidad and Tobago.
Or does one install a system, then get a sky-box, then order dvd's and wait several weeks for a dvd set.

OR

My proposed option.

---

### Post by alzie on 2008-08-03
So a small program to run on windows that can access the repositories and allow the download of packages.  Maybe a very small browser?

---

### Post by tom66 on 2008-08-03
Maybe it's me, but doesn't Synaptic's 'Generate download script' work for people? I guess you might need a copy of the database on the aforementioned computer, but you can do it. It uses a shell script and wget and grabs all dependancies.

---

### Post by dje on 2008-08-03
take a look at [APTonUSB]("http://aptonusb.sourceforge.net/") although it hasn't been released yet...

dje

---

### Post by BGFG on 2008-08-03
> **alzie said:**
> So a small program to run on windows that can access the repositories and allow the download of packages.  Maybe a very small browser?

something like that, but ideally something that would act as an extension of Synaptic. So that you could just plug your drive back into your machine and have your packages copied into 

/var/cache/apt/archives/

and install normally. seamless.

---

### Post by wilsonmuse on 2008-08-03
The way I've always done it manually is as follows:

1) "sudo apt-get install (application)" and note all of the package names it wants to download

2) Go to an internet connected machine and download the noted packages' .debs

3) Come back to the original machine and place all of the .debs into /var/cache/apt/archives

4) execute "sudo apt-get install (application)"

I would guess that a basic portable synaptic would follow the same path. As for all of the other features of apt, still looking into that :)

---

### Post by BGFG on 2008-08-03
> **dje said:**
> take a look at [APTonUSB]("http://aptonusb.sourceforge.net/") although it hasn't been released yet...

dje

Sorry DJE missed your message earlier. That project may be exactly what i'm talking about. I'll definitely check it out when it's released.
thanks for the link!

---

### Post by BGFG on 2008-08-03
Tom66, wilsonmuse, great and sensible options. But for intermediate-advanced. 
Noobs though? I'm thinking of this tool as a community advancement.
APTonusb may well be it... I will keep track of the project.

Thanks!

---

### Post by the yawner on 2008-08-03
How about a Synaptic-like web front end on the official website that would enable you to select the packages with dependencies checked to build your USB repository. Lessens the need to port APTonCD to other operating systems.

---

### Post by gn2 on 2008-08-04
> **BGFG said:**
> Please refer me to one such dealer in Trinidad and Tobago.

Certainly, no problem, here you go: [http://tinyurl.com/5lgmz8](http://tinyurl.com/5lgmz8)

Not actually located in Trinidad and Tobago, but very affordable postage charges.

Once you have a set you can copy  them to your heart's content and share them among your friends, even invite them to contribute to the cost of purchase, could end up just costing you pennies.

Or think big and set yourself up as the Debian DVD distributor for Trinidad and Tobago.

---

### Post by Lexicon101 on 2008-08-04
try a live-usb version, which you plug in, it records your database information, you bring it along, and browse at your leisure. If you just used a list of the applications you want and download the .debs, you'll have no dependencies. with this method (which would require making a live-usb system, with a GUI frontend, if it's for novice users..) you could browse, check applications you didn't plan on beforehand.. anything you need, and it will have a record of what packages you have and don't have.
Of course, I may be looking at this the wrong way, but I think it'd work.

---

### Post by BGFG on 2008-08-04
> **gn2 said:**
> Certainly, no problem, here you go: [http://tinyurl.com/5lgmz8](http://tinyurl.com/5lgmz8)

Not actually located in Trinidad and Tobago, but very affordable postage charges.

Once you have a set you can copy  them to your heart's content and share them among your friends, even invite them to contribute to the cost of purchase, could end up just costing you pennies.

Or think big and set yourself up as the Debian DVD distributor for Trinidad and Tobago.

Ok Ok So i was being a bit short. Sorry.

I like the Yawner's idea, although i think in that case you would still need to export your machine's config and upload it to the site. something like that.
And Lexicon101, we should check out APTonUSB as posted by DJE. Project is incomplete but if we get in on it now i think we could really contribute and help out the developer...

---

### Post by BGFG on 2008-08-04
> **Lexicon101 said:**
> try a live-usb version, which you plug in, it records your database information, you bring it along, and browse at your leisure. If you just used a list of the applications you want and download the .debs, you'll have no dependencies. with this method (which would require making a live-usb system, with a GUI frontend, if it's for novice users..) you could browse, check applications you didn't plan on beforehand.. anything you need, and it will have a record of what packages you have and don't have.
Of course, I may be looking at this the wrong way, but I think it'd work.

Yeah, this is basically exactly what i meant. :)

---

### Post by Lexicon101 on 2008-08-04
> **BGFG said:**
> Yeah, this is basically exactly what i meant. :)

*nods* Glad to know I understood you a little better. I will check out APTonUSB, because I'd like to be a part of something like that... I was running a computer with no internet for a while, and it definitely makes installing Ubuntu a pain, because Ubuntu doesn't come with gstreamer or blender or anything, and those (among others...) are things I really need in a computer...
Basically, though, a record of your system's package info would be essential to making this thing work, and I don't think it'd be hard to implement. Synaptic already compiles it when you open up, and I think it wouldn't be a far stretch to make it output it to a file from there instead of just loading it up. Then you could put it on your USBS drive (USBsynaptic, of course), stick it in a usb drive in a connected computer, have it automatically only download the packages, then have it put them in a folder along with a file with stats such as installation order, and other various useful information, bring it home, and have synaptic load, instead of internet repositories, your USBSRep.

EDIT: Checked out APTonUSB. Not exactly what I think would work best, and it's for people with slow internet, not no internet.. But it did point out the need for a record of free space. Definitely useful. Not how I would do it.

---

### Post by BGFG on 2008-08-05
> **Lexicon101 said:**
> *nods* Glad to know I understood you a little better. I will check out APTonUSB, because I'd like to be a part of something like that... I was running a computer with no internet for a while, and it definitely makes installing Ubuntu a pain, because Ubuntu doesn't come with gstreamer or blender or anything, and those (among others...) are things I really need in a computer...
Basically, though, a record of your system's package info would be essential to making this thing work, and I don't think it'd be hard to implement. Synaptic already compiles it when you open up, and I think it wouldn't be a far stretch to make it output it to a file from there instead of just loading it up. Then you could put it on your USBS drive (USBsynaptic, of course), stick it in a usb drive in a connected computer, have it automatically only download the packages, then have it put them in a folder along with a file with stats such as installation order, and other various useful information, bring it home, and have synaptic load, instead of internet repositories, your USBSRep.

EDIT: Checked out APTonUSB. Not exactly what I think would work best, and it's for people with slow internet, not no internet.. But it did point out the need for a record of free space. Definitely useful. Not how I would do it.

USBsynaptic. like the name. I would'nt say ubuntu is net dependent but it's really a drag updating and installing without a net connection. 
When i first got Vista, i had the time of my life trekking up and down the road to the net cafe downloading updates and open-source software. Then to come home and install them. I mean, i got VistaSP1 in a net cafe in utorrent.
I think a tool like 'USBsynaptic' would be a powerful addition to Ubuntu. a system could be fully updated and bleeding edge, no connection required. Collect your updates anywhere and bring them home.

PS. I started teaching myself Blender a while back. But i've been horribly slacking off. not even through my first tutorial. Any new tutorials for 2.45 ?

---

### Post by Lexicon101 on 2008-08-05
Only problem is, I know how things should run, I can see how things need to happen.. but I don't know how to code. So I'm not much help unless I or someone else teaches me to code.. And even then, I have a full-time job consisting totally of manual labor, so.. I'm tired when I get home.

(Anyway, what part of blender are you looking to learn? There are tutorials for all kinds of things.. Modeling, texturing, nodes, rendering, lighting... And subcategories of said categories.. Check out [www.blenderartists.org](www.blenderartists.org). It's kind of like Ubuntu's community, but for blender instead.)

---

