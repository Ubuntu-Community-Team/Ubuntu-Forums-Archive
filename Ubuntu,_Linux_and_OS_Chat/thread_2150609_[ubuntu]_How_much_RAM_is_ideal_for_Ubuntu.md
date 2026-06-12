---
title: "[ubuntu] How much RAM is ideal for Ubuntu?"
date: 2013-06-01
forum: Ubuntu, Linux and OS Chat
---

### Post by tech189 on 2013-06-01
Hi guys

I was just wondering how much RAM is ideal for Ubuntu to run smoothly.
I'm wondering because I installed it on an old Windows XP which has exactly a grand total of 1001 MB of RAM! (it's 6 years old)

tech189

---

### Post by 3mutts on 2013-06-01
I wouldn't run Ubuntu with that hardware (this must have been a pretty cheap PC for the time), I would run either Xubuntu or Lubuntu if you don't want to add more RAM. If you do add more RAM I would say at least 3GB.

---

### Post by monkeybrain2012 on 2013-06-01
3 G is plenty, I would say 2 G is fine. I think all the talks about how Unity is resource hungry is just overblown but in your case it  is probably too little.

---

### Post by deadflowr on 2013-06-01
A gig of ram is sufficient depending on how many programs you plan on running at one time.
Two gigs or more would provide a larger leeway, but one is most likely enough.

---

### Post by monkeybrain2012 on 2013-06-01
> **deadflowr said:**
> A gig of ram is sufficient depending on how many programs you plan on running at one time.
Two gigs or more would provide a larger leeway, but one is most likely enough.

It is true that one G will run Unity (provided the graphic card is right), but I suspect it is going to be slow. If I have only 1 G I will definitely use Lubuntu instead.

---

### Post by 3rdalbum on 2013-06-01
One gigabyte is perfectly okay.

---

### Post by Sam Mills on 2013-06-02
> **3rdalbum said:**
> One gigabyte is perfectly okay.
But we don't know what the OP does on his computer. Does he have 30 tabs open on firefox? While having 4 other apps going? IMHO, 2gb is a reasonable safe amount you should have. RAM is very cheap now, and unless you are *very* strapped for cash, it something that's attainable. 2gb gives you a comfortable cushion.

If adding ram is not an option, I agree with others that you should consider Lubuntu. Very light on resources, and obviously fast. I guess it depends on how much you do at any given moment.

---

### Post by tech189 on 2013-06-02
Thanks for all your answers! I've only put Ubuntu on it for fun so my budget is basically £0. Anyway it does run quite slow after opening more than one program. So I'll have a go at putting Lubuntu on it.

tech189

---

### Post by deadflowr on 2013-06-02
> **tech189 said:**
> Thanks for all your answers! I've only put Ubuntu on it for fun so my budget is basically £0. Anyway it does run quite slow after opening more than one program. So I'll have a go at putting Lubuntu on it.

tech189

You don't have to reinstall lubuntu.
You can install it on your existing system
```
sudo apt-get install lubuntu-desktop
```
or if feeling that the extra stuff isn't necessary
```
sudo apt-get --no-install-recommends lubuntu-desktop
``` 

Not sure which buntu version you have, but here's the list of [lubuntu-desktop packages for precise]("http://packages.ubuntu.com/precise/lubuntu-desktop").

when it's installed, to enter it, at login, in the login screen where you put your name, in the box is a small ubuntu icon, click on it and a dropdown will list the desktops on your system, choose lubuntu click and login.

---

### Post by mastablasta on 2013-06-02
> **Sam Mills said:**
>  RAM is very cheap now, and unless you are *very* strapped for cash, it something that's attainable. 

odl maschine - and DDR, DDR2 are not really that cheap. in fact here they costs twice as much as DDR3

---

### Post by houseworkshy on 2013-06-03
I've got 1.8 gig on a machine of similar age.  Whilst KDE and Unity do  run there isn't much room on top for more so it chugged a bit.  The  mepis distro has an older version of KDE and that runs very well on this  machine.  
The next step down is Xfce which is quite a nice  enviroment and fairly light, on top of Debian it is faster and needs  less RAM than on Ubuntu ( the Xubuntu distro is Xfce on top of Ubuntu ),  on top of Mint it seems about the same,  if one removes the Mint news  feeds, despite the other extras which have been included in Mints'  distro.  
Next down would be lxde ( the Lubuntu distro is lxde on top  of Ubuntu ) as mentioned above, which is a bit win95 looking and  involves typing if you want to to configure it.  
After that there  are a lot of very light GUI's such as razor-qt, enlightenment, etc.  You  can also choose to put in a file manager and windows manager  seperately.  Open box, fluxbox, thunar, midnight commander etc all do a  good jobs.  All the above, and many other, GUI's, windows managers and  file managers work on Ubuntu, and even some which don't come done  already on a 'buntu distro can be installed from the repositories and,  if you trust them, other repositories can be added anyway.  

Some  distros are specifically aimed at low specs, noteabley slitaz, antiX,  crunchbang, and bodhi ( an ubuntu underneath enlightenment on top distro  ).  These often expect a higher level of technical knowlage than heavy  distro's.  

If you are used to Ubuntu then going for another  Debian based disto,  will take you into more familiar territory.   [http://upload.wikimedia.org/wikipedia/commons/6/69/DebianFamilyTree1210.svg](http://upload.wikimedia.org/wikipedia/commons/6/69/DebianFamilyTree1210.svg)   

than something based on a differant branch of linux 
[http://www.linuxlinks.com/portal/news/staticpages/index.php?page=20070528113740321](http://www.linuxlinks.com/portal/news/staticpages/index.php?page=20070528113740321).  

After  distro hopping around testing things for weeks due to the impending end  of Lucid support I chose Debian with Xfce sitting on it,  which ( so  far ) is gorgeous, for the workhorse drive and Mint for the playdrive.    The decision was slighly forced as my Mum, who'd been happy with Ubuntu since 8.04, wasn't anymore and after a lot of live sessions testing wanted Mint and I have to answer questions when she rings up about things, and my sister, who's used Ubuntu since 7.10 has an old machine (only 512 ram )  which couldn't quite handle Xubuntu with programs running on top but is swift with Xfce on Debian plus the same programs.  There's a reason for that of course, the programs are all older versions as Debian are hyper strict about what can go into the stable repositories.  I rather like that as 'newist' is less to me than 'working';  it feels a little like running Ubuntu 8.04.1 ish.  The testing repositories, which is what Ubuntu is  based on, can of course be added ;  more up to date but slightly less stable and often ask more of a system.
   
Oddly it's the Mint I've had to fiddle around with in the post install  setup.    Debian, which is supposed to require more knowlage, just works. Partly because using Ubuntu for so many years has got me used to the  command line which is the same.  During the install I chose to  have a root account rather than use sudo just to see what it's like;   fill in root password for root account method, leave it blank to disable  root account and install sudo.   I've hardly needed the command line actually but it's  there.  Far more 'out of the box' than I'd expected.

So  whilst I no longer have pure Ubuntu on the system, though may again when hardware, allows as it's been a favorite for years,  ( huge  thanks to all developers and maintainers btw ), I've got it in  developmental brackets.

In short as this is linux you have a lot of choice.  You are not compelled to splash out on new hardware yet, as you would be if dependant on a comercial OS.  Try some live distros and see what fits you and runs best on your machine.

---

### Post by mastablasta on 2013-06-04
> **houseworkshy said:**
> I've got 1.8 gig on a machine of similar age. Whilst KDE and Unity do run there isn't much room on top for more so it chugged a bit. The mepis distro has an older version of KDE and that runs very well on this machine. 
.


latest KDE are faster than older ones.

the reason it chugged is akonadi and nepomuk which can bring down even a modern mashcine.

however after disabling these two services - about 290 MB ram on idle i believe and runs very fast on Dual core celeron with 1.3 GB old DDR ram. plenty of desktop effects enabled.

---

### Post by stalkingwolf on 2013-06-04
i have a hp mini and an asus eee ran zorin on the asus and am running 12.04 on the hp.  both have 1 gb ram and work well.  had UE on the asus .  it was a mite slow.

fwiw i ues the mate desktop.

---

### Post by VanillaMozilla on 2013-06-05
Way too many choices here.  Yes, Unity is slow, as you quickly discover on an older computer.  Lubuntu is great, and the lightest of the common Ubuntu derivatives.  Otherwise, you can try gnome-fallback (aka Gnome Classic with no effects) if your version will allow it.  This is close to Gnome 2 and works well, but it is a stopgap and won't be around forever.  Expect to spend a few hours configuring Lubuntu like you want it and getting used to it.  You can still run any and all Gnome programs on it (even file managers and that sort of thing.  No problem.

1 GB is as much as I have on ANY of my machines, and it's perfectly fine.  I even use it for video editing and DVD authoring.

Avoid bells and whistles such as Compiz, Mutter, etc.  Small and simple gets you a great system.

---

### Post by tech189 on 2013-06-09
ok im installing lubuntu

---

### Post by VanillaMozilla on 2013-06-09
Lubuntu (and LXDE) have some great tricks of their own, but it's a little do-it-yourself when you first install it.  Spend a few hours with it, and I believe it can be great.  Here are some great links someone gave me.  By the way, you should have no trouble running Gnome programs, or even KDE programs with it

[https://help.ubuntu.com/community/Lubuntu/Documentation/](https://help.ubuntu.com/community/Lubuntu/Documentation/)
[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides)
[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Workarounds](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Workarounds)
[https://help.ubuntu.com/community/Lubuntu/Documentation/UpgradeToLubuntu](https://help.ubuntu.com/community/Lubuntu/Documentation/UpgradeToLubuntu)
[http://ubuntuforums.org/showthread.php?t=1905408](http://ubuntuforums.org/showthread.php?t=1905408)
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)
[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)
[http://lxlinux.com/](http://lxlinux.com/)

---

### Post by Swappiness on 2013-06-10
> **mastablasta said:**
> odl maschine - and DDR, DDR2 are not really that cheap. in fact here they costs twice as much as DDR3

Where are you from? In Australia DDR and DDR2 is cheap depending on brand, Mhz and where you buy it. You can get cheaper on ebay if you look hard enough.

---

### Post by mastablasta on 2013-06-10
middle of Europe. 1GB DDR2 is about 25 EUR which is about 35 AUD. which might still sound cheap to you but our monthly salaries don't come close to Austrialian ones :-)

---

### Post by Swappiness on 2013-06-10
Yeah that sucks when the economy is crap.

---

### Post by andrew.46 on 2013-06-11
> **mastablasta said:**
> odl maschine - and DDR, DDR2 are not really that cheap. in fact here they costs twice as much as DDR3

Just bought 4gig of DDR2 for $100 Australian, 4gig DDR3 is about $80 from[ the same source]("http://www.ramcity.com.au/").

---

### Post by gigenieks on 2013-06-12
> **tech189]Hi guys!

I was just wondering how much RAM is ideal for Ubuntu to run smoothly.
I installed it on an old Windows XP (6 years old)
[/QUOTE]
[QUOTE=Sam Mills said:**
> 
But we don't know what the OP does on his computer. Does he have 30 tabs open on firefox? While having 4 other apps going? 
IMHO, 2GB is a reasonable safe amount you should have. 2GB gives you a comfortable cushion.

+1
I'm using Ubuntu 13.04 with 2GB's of RAM. As far as I noticed _my_ Ubuntu uses from 700 to 1400MB, so plenty of RAM left. IMO if you're going to use Ubuntu or Kubuntu you should have 2GB or more with default settings.
With 1GB RAM I would recommend **[COLOR="#2F4F4F"]Xubuntu.[/COLOR]** With 512MB or less - Lubuntu.

---

### Post by Raubhautz on 2013-06-15
Since you know you have an older system with lesser resources, you must not have big plans for this Ubuntu box. That being the case, you can easily use this machine with the 1GB. Of course you really do not have a lot of room for growth.

---

### Post by kurt18947 on 2013-06-15
I recently installed 32 bit Xubuntu 12.04 on a Dell Dimension w/ 512 MB.RAM.  The owner has zero tech savvy and just really wanted an web browsing/email appliance.  I put a Firefox launcher on the desktop and she was pleased as punch.:)  Xubuntu seems to use around 125-150 MB. RAM, maybe 20 MB. more with Firefox open.  A machine with 1 GB. RAM should be fine with Xubuntu or Lubuntu, just don't have too many apps open at the same time.  In addition to needing more RAM, Unity & Gnome-shell make more demands on the graphics subsystem.  Older machines using onboard graphics can have pretty uninspiring graphics chips plus they use system RAM.

---

### Post by TNFrank on 2013-06-16
According to Patrick Norton on TechZilla RAM for for computers is going to get harder to find and more expensive because all the major manufactures are focusing on RAM for phones and tablets and not producing as much for desktop or laptop computers. 
How much may depend on your system. My older nc8230 laptop will only support 2GB of RAM but other computers may support more.  I'm maxed out at 2GB and everything seems to be running pretty good, it wasn't bad a 1GB but the place where I bought my laptop said they'd swap my 1GB and $25 bucks for 2GB so I just couldn't pass up that deal. 
 I'd say if you can afford it stuff all the RAM into your system that you can, it's better to have it and not need it then to need it and not have it IMHO.

---

### Post by tech189 on 2013-07-10
Thanks for all your answers. As I've already said, I'm not going to add any ram since it's an old machine. Lubuntu works quickly but the downside is that it looks like Windows 95! As people have asked I do actually have about 20 tabs open while looking at emails and Skype!

Thanks again,
tech189

---

### Post by mastablasta on 2013-07-10
Lubuntu look can be customized a lot. you should check some desktops in their community.

---

### Post by black veils on 2013-07-11
> but the downside is that it looks like Windows 95! 

personally i would change the notifications system to xfce4-notifyd, and the window manager to xfwm4 (its still light). the rest can be configured from within the given GUI - panel placement, size and styles.

---

### Post by VanillaMozilla on 2013-07-11
> **black veils said:**
> personally i would change the ...window manager to xfwm4 (its still light).
I wouldn't, at least not without exploring Openbox first.  Openbox has some great tricks of its own that the others lack.

For example, if you set it to focus on whatever window is under the mouse, this can be a great convenience (some window managers can't even do this at all).  However, this is also treacherous on other window managers because it's difficult to avoid selecting the wrong window by accident if the menu is in another window.  In Openbox you can set a short time delay, so it's quite easy to avoid this problem.

Also, if you put the mouse over the desktop, you can switch desktop spaces with the mouse wheel.  You can also set it so a couple of pixels at the side of the window is always bare desktop.  So this is really fast, and a great convenience.

Plan to spend at least a couple of hours to explore and get LXDE to look like you want it.  It's a little primitive out of the box, but it's great after you set it up the way you want it.

---

### Post by vasa1 on 2013-07-11
> **black veils said:**
> personally i would change the notifications system to xfce4-notifyd, ....
That _is_ the default in Lubuntu 13.04.

---

