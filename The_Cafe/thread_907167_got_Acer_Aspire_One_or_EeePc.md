---
title: "got Acer Aspire One? or EeePc?"
date: 2008-09-01
forum: The Cafe
---

### Post by Garratt on 2008-09-01
I bought a 'Acer Aspire One' today(payed for), pick it up from the shop tomorrow, and I'm wondering if anyone has one with ubuntu 7-8 installed?

I have the 120g(mehcanical hdd) xp version, as opposed to the 8gb(sd card) Linpus version, I took one quick look at that horrid website and pathetic excuse for a linux distro and very very very quickly rang up the supplier and changed to xp

My god... if you want a real good laugh, google linpus.

So do you have ubuntu working on it and how are the drivers? for things like internet.

---

### Post by in-dust-rial on 2008-09-01
ot: can you comment on the keyboard and display's outdoor performance in this topic, later on?
thanks! 

```
http://www.linux-community.de/Neues/story?storyid=26172
```
in this german page, they say they installed ubuntu and suse on the limpus-version-laptop(limpus was removed before), without problems while the install procress!
problems after install:
false resolution [solved] 
```
/etc/sysconfig/displaymanager 
line: DISPLAYMANAGER_RANDR_MODE_auto 
to: 1024x600 (without Modelines)
```
wireless LED doesnt work
no wiresless connection found [solved]
```
swith off and on wireless switch again
```
KDE and GNOME are 1 minute of boottime and somehow slow[512mbram, here], XFCE instead?
both cardreader doesn't work [solved]
```
/dev/mmcblk0p1 must be mounted by hand for the one cardreader!
=> if a card is in the cardreader while boottime, laptop doesn't boot!
the roight cardreader can be used via :
setpci -d 197b:2381 AE=47 
and 
PCIE-Hotplug-Modul: modprobe pciehp
[better use new kernels :O]
```

hf!

---

### Post by nicedude on 2008-09-01
You probably would have had better luck with the eeepc since they have been around longer and there are custom Ubuntu kernels for them etc. That said maybe once there are enough Aspire One users some people will come up with a custom kernel for it too and I bet someone will you might have to wait a bit though is the only problem I could see.

I have a question, how much did they charge extra for the XP vs Linpus ?

---

### Post by Garratt on 2008-09-01
yea, thanks guys...

after using my usb as a portable OS(slowest OS on earth), there was no way in hell I would ever buy an eeepc, or linux version of aspire one.

and linpus looks absolutely terrible in itself besides the fact its sitting on a 8g sd card.

so I guess i'll just run with xp for 6 months or so, and by then things should be sorted.

[QUOTE=in-dust-rial]can you comment on the keyboard and display's outdoor performance in this topic, later on?
thanks! [/QUOTE]
Yea i will do tomorrow, I will try to do a very objective pov,  faily needless to say though with atom processor being alot faster than the EeePc combined with 1gb ram and a real mechanical hdd, i'd say performance will be quite nice. (specs are in my sig)

I have heard the downside to the aspire one are:

# extremely hot bottom plate, to the point where it burns your gonads... I heard 42 degrees somewhere.(celcuis).
# small mouse trackpad: and buttons are on either side of the mouse plate instead of below.
# dwarfed 2200mAh battery, the eeepc 901 rules on this front.

Positives (compared to eee pc):

# larger buttons (tho not as large as the mSI wind with is 8 and aspire is 7.2 or thereabouts), and correct usa kb layout
# system performance.
# The 249 by 29 by 170mm chassis makes it approximately 25mm wider than an EeePC 901, but it's also marginally thinner. At 995g, it's also lighter than the 1.1kg Eee 901

[QUOTE=CCNet]By making the chassis wider than most netbooks, Acer has been able to incorporate a keyboard that's 95 per cent the size of a full laptop keyboard. Amazingly, you can actually touch-type on the One without much compromise in your speed. Sure, the enter button isn't as big as we'd like, but the rest of it is spot on. Both shift keys are large and even the Ctrl and Fn buttons are the right way around. Unfortunately, the mouse trackpad is extremely shallow and its remarkably skinny buttons live on either side instead of directly below. This takes a lot of getting used to.[/QUOTE]

[QUOTE=CCNet]Conclusion
In some respects, the Acer Aspire One is better than an EeePC 901. It has an excellent keyboard, solid performance and is highly portable. The EeePC 901 still has the edge in terms of battery life and mouse input, so it's a close call between the two machines.[/QUOTE]

[http://www.cnet.com.au/laptops/laptops/0,239035649,339290036,00.htm]("http://www.cnet.com.au/laptops/laptops/0,239035649,339290036,00.htm")

---

### Post by Garratt on 2008-09-01
> **nicedude said:**
> You probably would have had better luck with the eeepc since they have been around longer and there are custom Ubuntu kernels for them etc. That said maybe once there are enough Aspire One users some people will come up with a custom kernel for it too and I bet someone will you might have to wait a bit though is the only problem I could see.

I have a question, how much did they charge extra for the XP vs Linpus ?

it was $580 for the xp (after cashback).

and $480 for the linpus (a-c).

Personally the way i see it is, I payed an extra $100 for an extra 110gb hdd, and extra 512mb ram. which isn't too bad. 

In reality i payed for xp, and got the ram and extra space for free... but ssshhhhh.

 I think linpus can be downloaded from the website If i really wanted to use it...

---

### Post by nolan- on 2008-09-02
> **Garratt said:**
> 

 I think linpus can be downloaded from the website If i really wanted to use it...

I don't think the downloadable Linpus lite is the version installed on the AA1. 
I should get mine today, ordered it yesterday. I went for Linpus version with 120hd and 1gig ram. XP version is [COLOR="Red"]*£50 MORE*[/COLOR] in UK! For a crappier OS! 
Linpus seems to be a decent little distro, it's based on Fedora. I'll give it a go but there are loads of howto's for installing Debian, Opensuse, Ubuntu etc...if you wish to do so.

Can't wait!!!!

Edit-

An Ubuntu based Distro made for the Acer Aspire One is available here :
[http://onelinux.org/index.php]("http://onelinux.org/index.php")

---

### Post by PHATSPEED7x on 2008-09-02
Nice write up. Now I know.

---

### Post by Garratt on 2008-09-02
> **nolan- said:**
> I don't think the downloadable Linpus lite is the version installed on the AA1. 
I should get mine today, ordered it yesterday. I went for Linpus version with 120hd and 1gig ram. XP version is [COLOR="Red"]*£50 MORE*[/COLOR] in UK! For a crappier OS! 
Linpus seems to be a decent little distro, it's based on Fedora. I'll give it a go but there are loads of howto's for installing Debian, Opensuse, Ubuntu etc...if you wish to do so.

Can't wait!!!!

Edit-

An Ubuntu based Distro made for the Acer Aspire One is available here :
[http://onelinux.org/index.php]("http://onelinux.org/index.php")

Wierd I didn't think you could choose the OS you wanted, my choices were either xp with 120g hdd 1g ram, or linpus with 512 ram and 8gb hdd.

price is about the same there as it is in Aus.

thanks for the link.

to be honest that os doesn't look like it's worth looking at, it's purely graffical like a tourist kiosk, or to be less vague a complete non-computer-user friendly nub kiosk for linux. 

After watching a couple demos of it, there didn't seem to be much software on it, like terminal would be handy...

but that opinion is PURELY based on a couple of demo's so it would be nice to know how you find it. 
eg. can you add/remove programs via a package manager, while connected to net?
do you have a desktop?
what is it like switching between tasks, and/or how many similtanious (sorry dictionary server is down :P) applications can you have?

---

### Post by in-dust-rial on 2008-09-02
> to be honest that os doesn't look like it's worth looking at, it's purely graffical like a tourist kiosk, or to be less vague a complete non-computer-user friendly nub kiosk for linux.
rofl^^ 

but when i was useing limpus in a store, i just pressed some combinations of control - alt and the numer keys ... like getting into another virtual console ... for some seconds i was freaking out, because nothing happend , but suddently there was a terminal!
SO there is a terminal!!!!!!!! there, is saw it my own eyes...

but i could not remember the dmidecode command and rtied something totally wrong... so

---

### Post by Garratt on 2008-09-02
> **in-dust-rial said:**
> rofl^^ 

but when i was useing limpus in a store, i just pressed some combinations of control - alt and the numer keys ... like getting into another virtual console ... for some seconds i was freaking out, because nothing happend , but suddently there was a terminal!
SO there is a terminal!!!!!!!! there, is saw it my own eyes...

but i could not remember the dmidecode command and rtied something totally wrong... so

theoretically would be an awesome setup if you could add programs, change the 4 different classes/or add more classes, customise the whole thing, I havn't really seen or heard much of it(besides the 4 menu items and biga$$ icons to click on) so here's hoping someone posts an objective review.
This guy looks like he's onto the same idea, but at least you can expect all the functionality of ubuntu.

[IMG]http://onelinux.org/images/screen1.png[/IMG]

---

### Post by Garratt on 2008-09-04
Well took me  a while to reply due to the wonderful phone company i'm with disconnecting me even tho i payed the bill 2 weeks ago...

so no net for a couple weeks :( at least now i can get voip phone through my isp instead of typical phone company.

Anyway down to business. The reviews on Acer Aspire from what I have read have all been a load of horse doodoo, like most reviews on products. The xp aspire one version is simply amazing, incredible power and more than easily run vista, with that said the graphics are not particularly great. but as for benchmarks i have no software so here is what i did.
loaded up:
media player playing music, netbeans, jcreator, dev c++, notepad++, daemon tools, 5 x W.explore, movie maker recording the webcam, help and support, msn, control panel, xcel, word, firefox and IE....

with all these programs open i was easily able to switch between them and type, and move windows around without any lag.

cpu indicated running at 50% and memory at about 65-70%
so that's the performance, other factors like 4 usb ports is incorrect, there's only 3, additionally there's 1 sd "storage expansion" on the left side, and a multi-card reader on the right.

the weight is slightly correct it weighs in at 0.9kg without the battery and 1.1kg with.

the mousepad is fine, moving from the top to bottom moves the mouse from the top of the screen to the bottom the way it's intended (if you have fat fingers this may be a problem additionally changing the settings helps).

the reported 'OVERHEATING' is a massive exaggeration. after using it for  over 5 hours the bottom was infact mildly warm - cool for it to overheat the way ccnet discribed they must have been covering every vent possible. I to had this sitting on my lap and even though I was covering up vents it still did not overheat. It is also possible that due to the reviewers having a non-release version the bugs have been ironed out.

I think thats about it, typing is easy on it and compared to the guy sitting next to me with a huge dell, keys are only slightly smaller on the aspire one. compared to the guy across the room with an Eee Pc 900 the keys are a greatly bigger. the eee pc has widescreen rectangular keys, Aspire keys are square and much like a normal notebook/laptop.

---

### Post by dada1958 on 2008-09-04
I got a blue AA1 this afternoon with 8 GB SSD and 512 MB RAM; it's a very nice little machine and I'm looking forward to get Ubuntu running on it ...

---

### Post by dada1958 on 2008-09-06
Yesterday, thanks to this [excellent how to]("https://help.ubuntu.com/community/AspireOne") I installed Ubuntu on my little machine ...

---

### Post by in-dust-rial on 2008-09-06
grats!

what is about writeing on this machine?
a lot of typeos?

and what is about the display reflexxxions with real sunlight around?

thx
hf

---

### Post by dada1958 on 2008-09-06
Keyboard is pretty decent, I have this little machine for 2 days. never tried it in full sunlight but when it's on, the reflections don't bother me.

---

### Post by him610 on 2008-09-06
> **dada1958 said:**
> I got a blue AA1 this afternoon with 8 GB SSD and 512 MB RAM; it's a very nice little machine and I'm looking forward to get Ubuntu running on it ...

I ordered the very same model yesterday from Newegg; I expect delivery on Tuesday. I had actually waited for the Dell Inspiron Mini 9, but the estimated shipping date for the Linux model was 9 October and I wanted one available for a trip I am planning on later this month.

Did anyone backup the included copy of Linpus to an external device before installing a _buntu distro?

Did anyone consider using or modifying Xubuntu to run on the Asus One?

> An Ubuntu based Distro made for the Acer Aspire One is available here :
[http://onelinux.org/index.php](http://onelinux.org/index.php)

Appreciate the posting of this link by nolan. I have downloaded the iso, burned it to a cd, and am in the process of installing it on one of my vintage machines just to see how works. 

Have fun, live long, and prosper.

---

### Post by dada1958 on 2008-09-06
> **hgh9mrp said:**
> 
Did anyone backup the included copy of Linpus to an external device before installing a _buntu distro?
A Linpus recovery cd was shipped with my Aspire One, though I have to say that I&#314;l probably never going to use that. It's a Fedora 8 derivate, quiet good but a kind of obsolete. And you have tweak to get full access to the xfce de.
Besides I'm a little bit overwhelmed by the Netbook Remix user experience, **wow**, that's a really great thing. For the first time I love the default theme.
Ubuntu is doing fine but my next step is going to be Xubuntu underneath that Netbook Remix, you can use the space.
I'm typing this on this amazing little machine which should have been shipped with whatever Buntu + Netbook Remix because Acer would have a MacBook Air killer imnsho :cool:

---

### Post by him610 on 2008-09-06
> **Garratt said:**
> I bought a 'Acer Aspire One' today(payed for), pick it up from the shop tomorrow, and I'm wondering if anyone has one with ubuntu 7-8 installed?
...
So do you have ubuntu working on it and how are the drivers? for things like internet.

What kind of wireless card, chip, and version does your Acer One have installed in it?

Does your model accept the SD or micro-SD memory card?

---

### Post by him610 on 2008-09-06
> **dada1958 said:**
> Besides I'm a little bit overwhelmed by the Netbook Remix user experience, **wow**, that's a really great thing. For the first time I love the default theme.
Ubuntu is doing fine but my next step is going to be Xubuntu underneath that Netbook Remix, you can use the space.

That's good to hear. Did you have any problems with the configuration of drivers when you installed Ubuntu, or did everything install smoothly?

Where did you download your Netbook Remix ISO from? I downloaded eeebuntu_nbr.1.0 yesterday but I had problems burning a good DVD.

---

### Post by dada1958 on 2008-09-06
> **hgh9mrp said:**
> That's good to hear. Did you have any problems with the configuration of drivers when you installed Ubuntu, or did everything install smoothly?

Where did you download your Netbook Remix ISO from? I downloaded eeebuntu_nbr.1.0 yesterday but I had problems burning a good DVD.

I used a regular Ubuntu 8.04.1 cd and I followed [these]("https://help.ubuntu.com/community/AspireOne") instructions.

See NETBOOK REMIX (Optional) ...

All went smoothly, though it's a time consuming job, but worth every minute :)

---

### Post by mudguts on 2008-09-06
i put 8.04 on my msi wind pretty easily.  keyboard is a little small but i really like the fit and finish of the notebook.  much better then the asus eee I had.  

though the msi wind may be a bit overkill in the price range..  as the asus eee and the aspire are both cheaper.

i'd stay away from the asus tho.   lousy keyboard, too clickity.

---

### Post by Garratt on 2008-09-09
> **hgh9mrp said:**
> What kind of wireless card, chip, and version does your Acer One have installed in it?

Does your model accept the SD or micro-SD memory card?

intel atom chip 1.6ghz, 1gb ram, 120gb hdd, and xp preinstalled.
yea, and yes

it has a multi card reader, and an ''sd' storage expansion slot', so really it has 2 seperate sd slots, the sd slot acts as a second hdd, just incase you need more than 120g...

i installed ubuntu 8.04 on it the day after i got it, havn't had net to tell you guys about it unfortunately, didn't follow any guides as it didn't seem to be necessary. i set the partitions on the hdd so xp has 57gb, and ubuntu 57gb, the extra space is scratch and sniff space.

because I installed ubuntu on a seperate partition (same hdd), it seemed to automatically pick up on the restricted drivers from XP, so i didn't need to do any tweaking or downloading,... works great.

typing is no problem at all, like already stated the keyboard is (almost) as big as a typicall laptop, the keys are quite large, and i would say even someone with big hands could get used to it.

I'm loving this, so glad I spent $580 on this sucker rather than spending $1000+ on a laptop. and I'm also glad i went for the xp version over linpus, why get a 8gb hdd, and 512mb ram, when you can get an extra 512mb ram, and 110gb  hdd for an extra $50-$100... 

I can easily delete xp and install whatever OS i like on it. but as i need it for uni at the moment this suits me fine.

As for using this outdoors, I do use it out on my front verandah but, there is not much "direct' sunlight. really shouldn't be that much of a problem unless you have your back to the sun whilst working outdoors...
the screen is not REALLY glossy, but does have a nice gloss feel about it, so yea unless you simply want this because you plan on working outdoors then do not go by my guide, but if you wish i can probably do some testing.

---

### Post by donec on 2008-09-09
> **hgh9mrp said:**
> Did anyone consider using or modifying Xubuntu to run on the Asus One?The Linpus AA1 comes with a restore DVD but since it doesn't come with a reader you have to make a USB flash memory stick to restore it or use an external USB DVD drive. I used my Acer 9300 to run the restore DVD and then created a restore USB stick to use with my AA1. It required a 2G USB stick but it works fine. 

There are 2 easy ways to get to the terminal. First you can just use alt+f2 and the run window will appear then type in the word terminal or you can go to any file window, right click and select open terminal.

**_[COLOR="Red"]Warning[/COLOR]_**: When running Linpus and adding software do not add the KDEUTILS they have something in them that messes up the display and the right click locking every thing so that a restore is required. I wanted to install the kdeutils because I wanted to use Kwrite and it is one of those utilities.

The keyboard is great I actually find it easier to type on it than a full size keyboard and I have large hands with long fingers. I use a mouse so I disable the track pad using the Fn+F7 combination so when I am typing I don't accidentally touch the track pad and move my cursor to a place other than where I want to be typing. The screen is the absolute best I have seen inside or out. It is bright, sharp and very easy to read even with my poor eyesight.

The only complaints I have is the software is anemic and you can't customize the desktop. Also some of the windows open and the bottom of the window is off the screen. Example I added GIMP and the bottom of the layer window disappears off the screen.

The 6 cell battery is now on sale in Canada so I am waiting for it to come here. If I remember it was for $129.00 so I am also hoping the price will drop some as the computer did as I got mine from Circuit City for $329.00.

---

### Post by him610 on 2008-09-09
My Acer One just arrived about an hour or so ago. Documented the unpacking with photos. I set it up; it is a fairly simple setup process. I am running the software update now as I type this.

So far, I am impressed with it including the physical size, the screen, the workmanship, and what little I have used the operating system. The boot time is truly impressive. It really is a neat little machine. I am glad I decided on the Acer One.

I have gotten used to running both Ubuntu on my more capable systems and Xubuntu on my vintage hardware; didn't much care for KDE interface. I figure I can get used to Linpus Linux (LL). I guess a person can be multi-versatile when it comes to Linux. I may eventually decide to install the latest NetBook Remix (NBR) on it.

Cheers.

---

### Post by hardran3 on 2008-09-09
I have the 8GB SSD, 512 MB RAM version of the AAO running Ubuntu 8.04.1 and it is a great little laptop. After a little tweaking it boots fast (27 seconds in bootchart), and has descent battery life considering the 2200 mAh battery size (2.5 hours life, lowest brightness, wifi on, browsing with Firefox, and compiz enabled).

Wifi, webcam, audio, and resume & suspend all work well, ALSA and madwifi needed the newest versions compiled though . It has a great screen, looks good even on lowest setting, and a well sized keyboard. I am very happy with it, especially for $329 Canadian.

---

### Post by dada1958 on 2008-09-09
> **hardran3 said:**
> After a little tweaking it boots fast (27 seconds in bootchart.)
Please share that little tweaking, 65 seconds boot time here ...

---

### Post by SlCKB0Y on 2008-09-09
> **Garratt said:**
> 

I'm loving this, so glad I spent $580 on this sucker rather than spending $1000+ on a laptop. and I'm also glad i went for the xp version over linpus, why get a 8gb hdd, and 512mb ram, when you can get an extra 512mb ram, and 110gb  hdd for an extra $50-$100... 



because the 8gb SSD has a number of advantages. It is quieter, cooler, less prone to damage. And I got mine from Office Works for $399 after cash back

---

### Post by Garratt on 2008-09-10
> **SlCKB0Y said:**
> because the 8gb SSD has a number of advantages. It is quieter, cooler, less prone to damage. And I got mine from Office Works for $399 after cash back

is the 512 less ram really an advantage?

quieter? i cannot hear it running at 3am when there is not a spec of sound anywhere, let alone normal running conditions.


cooler? like already stated fact... because im typing on it have been for over 13 hours now, the xp version doesn't run hot so therefore the 8gb sd is actually a fridge?

no but seriously the bottom and keypad are about the same temp and is running at about 32-34 degrees celcius. not even warm.

less prone to damage?
thats like saying you would prefer to use sd card rather than your 1tb hdd on your desktop.

I do understand your logic and can agree to a very limit extent, it's just seriously flawed imo...

you get a 1 year warrannty with this laptop and can hand in your cashback for an extra year., not that i choose this option because in a year time i can go out and buy the next gen version, and sell this for $200 on ebay.

how many people have complained about hdd's blowing up on the acer?
how many have lost tons of data, having to send back to manufacturer?
I have not heard any...

I have not heard any credible people say this thing overheats, or runs loud so...

---

### Post by Garratt on 2008-09-10
just face it dude your cheap :P


j/k's

---

### Post by Tux Aubrey on 2008-09-10
My 2 cents:

I got the Linpus Lite version and ditched Linpus for Xubuntu 8.04.1 with Enlightenment as the WM.  Wonderful.  Gorgeous.  

Everything works EXCEPT suspend/resume, mic/headphone sound and the wifi led (but I think there are fixes I haven't tried yet).

The version I got is the One with the _very_ slow Intel SD (there is a version with a faster Sony SD).  I'm in the process of replacing it with a fast CF card that should quadruple the write speed.

I upgraded the RAM to 1 GB because....well, I could and I wanted to.

All up, a great design but a real buqqer to upgrade - it is hard to take apart, everything has to be removed to get at the bits you need to tweak and the whole lot is so bl00dy small!

---

### Post by in-dust-rial on 2008-09-10
> 
Quote:
Originally Posted by SlCKB0Y View Post
because the 8gb SSD has a number of advantages. It is quieter, cooler, less prone to damage. And I got mine from Office Works for $399 after cash back
is the 512 less ram really an advantage?

quieter? i cannot hear it running at 3am when there is not a spec of sound anywhere, let alone normal running conditions.


cooler? like already stated fact... because im typing on it have been for over 13 hours now, the xp version doesn't run hot so therefore the 8gb sd is actually a fridge?

no but seriously the bottom and keypad are about the same temp and is running at about 32-34 degrees celcius. not even warm.

less prone to damage?
thats like saying you would prefer to use sd card rather than your 1tb hdd on your desktop.


well well well,
these oldschool HDs that dont turn there selfs into standby while being in shaking are much more effective than SSDs.

this is what i learned from ROBOTS playing FOOTBALL! they often crash into each other!
newer (laptop)harddiscs are a problem in general (make themselves standby all the time), desktop harddrives work good, and SSD cards mess up their filesystem -from time to time.
we have failed to find out why exactly they do it, but i think, you can consider SSD as "not very prone to damage".
(:KS from the overall, software included, site)
the life time of a SSD in heavy use is for me a BIG QUESTIONMARK... =)

good luck with your SSDs ... but i would not trust them...

---

### Post by whitefort on 2008-09-10
I'm passionately in love with my little eeepc 901.

I haven't yet taken the plunge and installed eeebuntu, but I run it regularly from a pendrive. 

To be honest, with the Xandros full desktop enabled, it does most of what I want, and I don't need to worry about fiddling with the eeebuntu version to get all my hardware to work.

I also use Backtrack 3 from thumbdrive an *awful* lot to demonstrate to my family * friends how lousy their security is!

I didn't think I'd use my eeepc *very* much, but really I'm now using it far, far more than my big powerful Lenovo.

---

### Post by donec on 2008-09-10
> **Tux Aubrey said:**
> I'm in the process of replacing it with a fast CF card that should quadruple the write speed.Would you expand on that as it sounds interesting?

---

### Post by ShakeyJake on 2008-09-10
Ive had an Eee PC 900 for a few months now and I love it. In fact, Im typing on it to answer this thread (and as such Firefox keeps putting little red lines under every single word, stupid typo-inducing keyboard ](*,))

Aside from the keyboard though its a dream to live with, I got the 900 in full view of the 901s because the 900 just seemed to be the Eee at its peak. No painfully slow atom chips here.

Pretty much as soon as it came out I installed Ubuntu Eee (not the netbook remix) and its fantastic.


Edit -oh and as for SSDs vs HDDs, there have been a handful of studies that show that the limited number of I/O operations on an SSD shouldnt be a problem for everyday use. And theyre smaller, lighter, quieter and faster than HDDs.

---

### Post by hardran3 on 2008-09-10
> **dada1958 said:**
> Please share that little tweaking, 65 seconds boot time here ...

First I installed Boot Up Manager

```
sudo apt-get install bum
```

and removed services I could live without. Your mileage may vary.

```
apport
rsync
nvidia-kernel
apmd
atd
avahi-daemon
cupsys
```

Then I made some changes to GRUB. Open /boot/grub/menu.lst in your favorite editor and find the "#defoption=quiet splash" line. I changed mine to read:

```
# defoptions=quiet elevator=noop clocksource=hpet vga=788
```

After that is saved run "sudo update-grub" and reboot.

On reboot hit the ESC key at the grub screen and press "e" on the first line. There will be a line now that starts with "kernel". highlight that line and press "e" again. Add the word "profile" to the end of the line, press enter and then press "b". This boot will take longer, but subsequent boots should be quicker.

---

### Post by Tux Aubrey on 2008-09-10
> Would you expand on that as it sounds interesting?

There's a long and winding thread about this hack (using a fast CF card instead of a SD) on the [aspireone user forums]("http://www.aspireoneuser.com/forum/viewtopic.php?f=43&t=59").

I had previously tried to install a 1.8" zif HDD (an "ipod harddisk") but the disk I bought cheap (off ebay) was faulty.  One day I will learn not buy cheap rubbish!

I'm not recommending hacks like these as I really think people who genuinely want a faster machine would be better off financially (and in terms of stress) buying the Windows XP machine (HDD) and replacing the OS. But, because I made an impulse purchase and am independently wealthy (/joke), I decided to do some "interesting" things with my Acer One.

---

### Post by oswaldkelso on 2008-09-11
> I'm not recommending hacks like these as I really think people who genuinely want a faster machine would be better off financially (and in terms of stress) buying the Windows XP machine (HDD) and replacing the OS. But, because I made an impulse purchase and am independently wealthy (/joke), I decided to do some "interesting" things with my Acer One.

How would you be better off? the XP machine costs more in most country's. I would remind you that just because a certain version is not available to you, does not mean its not available to someone else. Linux versions with a HD are available in many country's. I don't want to get on your case but any new user may think they have no choice.

[http://en.wikipedia.org/wiki/Aspire_One](http://en.wikipedia.org/wiki/Aspire_One)

---

### Post by rab4567 on 2008-09-11
Acer Aspire one prices

[http://www.justnetbooks.com/shop.php?a=aceraspireone&gclid=CPjW5KP405UCFQqdnAodOnd5jQ](http://www.justnetbooks.com/shop.php?a=aceraspireone&gclid=CPjW5KP405UCFQqdnAodOnd5jQ)

---

### Post by ceratophyllum on 2008-09-11
I got an aspire one (XP,1.6GHz, 120GB disk) at best buy for $337. It was a clearance open box item.

I used parted to shoe horn ubuntu into half the drive and left XP on the other half.  I hate XP, but feel the need to keep it around.

I set up Ubuntu as described in the instructions above.

The problem is that wake from suspend to RAM kills Wifi. You have to power off the machine to get the Wifi working. 

(Curiously, even if you restart and choose Windows XP in grub, the damn wifi still won't work. You have to turn it off!)

Is there a way to fix this? Losing Wifi on wake up really sucks.  It doesn't say anything about sleep messing up Wifi in the AspireOne howto...

Where are the scripts that run when you suspend/resume? Will unloading ath_pci, ath_hal before sleep help? After wake reload them?

---

### Post by ceratophyllum on 2008-09-11
It worked! Removing the modules before suspend and then manually modprobing ath_pci after wake did the trick! How to automate this? Which suspend/resume scripts should I edit? Can someone point me to some documentation or help?

---

### Post by dgrafix on 2008-09-12
I Just got an acer aspire one. Once you can unlock it and get yumex installed its not -too- bad. However i got stuck when trying to access NFS shares so kind of gave up on that one. Its a shame as this little distro would have been fine if only i could have accessed the shares.

I have installed Xubuntu but the wireless doesnt work :/
Its recognised the fact that its atheros as its loaded the restricted drivers for it.

---

### Post by Prefix100 on 2008-09-12
[http://onelinux.org]("http://onelinux.org")

---

### Post by t0p on 2008-09-12
I have an eeepc (4G SSD version).  I haven't installed ubuntu on it yet, but I shall soon - there are a few versions available, and they all get rave reviews in the relevant [online forums]("http://eeebuntu.org").

> **nicedude said:**
> You probably would have had better luck with the eeepc since they have been around longer and there are custom Ubuntu kernels for them etc. That said maybe once there are enough Aspire One users some people will come up with a custom kernel for it

Oh, definitely.  If you look at the early forum posts at [forum.eeeuser.com]("http://forum.eeeuser.com"), you'll see folk bemoaning the lack of available software.  Fast-forward 12 months and now there are loads of repos, customized versions of ubuntu and debian... the Linux community is so industrious!!

---

### Post by dada1958 on 2008-09-12
> **hardran3 said:**
> This boot will take longer, but subsequent boots should be quicker.
Thank you, boot time is 60 seconds now ...

---

### Post by Tux Aubrey on 2008-09-12
Re hacking the AcerOne
> How would you be better off? (with the Windows version)

The actual dollar cost of the HDD/CF hacks I am doing is more than the price difference between the Linux and Windows versions (at least in Australia). And while you can achieve excellent performance, it is not THAT much better than a straight HDD machine.  I have also voided my warranty just by opening the case!  The Acer is NOT an easy machine to open and work on - you (ie me) are very likely to struggle with any of these upgrades.

I only did these things because I had already bought the Linux version and ended up with one with a very slow SD (Intel).  I also find it hard to resist "having a go".  :popcorn:  

I do like the fact that the manufacturers are offering a choice of Linux or Windows machines but the lower spec Linux versions are not always as good a deal as they might seem.

---

### Post by SlCKB0Y on 2008-09-16
> **Garratt said:**
> just face it dude your cheap :P


j/k's

its ok. Im going to put an extra gig in here ($25) to have a total of 1.5, and swap out the ssd for a toshiba 1.8" zif and ill still spent less than you :p

---

### Post by Funk Phenomena on 2008-09-21
I have both the Xandros Eee 701 and Aspire One Linpus with 8gb ssd.  I'm content with both default operating systems.  The sub 20 second boot of Linpus is pretty sweet.  As is the size of the Eee, except for the bulking standard battery.  The Aspire was $70 cheaper than the $399 Eee with better specs... and a noticeably less-crowded keyboard.  I put Xubuntu on the Aspire just to see and so far I like it. The boot time is definitely slower than Linpus, but Linpus is kinda goofy in software updates and installs.  Like unresolved-software-dependencies goofy.  And I don't think it has near the level of support, both official and user, as the eee.  The Aspire has two sd card slots, one of which nicely, and automatically melds with the ssd versus the Eee prompting you at each boot if you leave it in.  I accidentally dropped the eee from about four feet onto concrete while it was on and nothing appears to have broken.

I don't see the need to upgrade the ram for the Aspire, no matter if it's Xubuntu or Linpus, though upgrading ram on the eee was super easy. Putting advanced mode on Linpus is easy enough and makes it easier to tweak (compiz and such).  They each have their tradeoffs, both operating systems and machines.  Putting XP on any of these is blasphemy.  I hope ye sinners are ashamed! :p

---

### Post by Funk Phenomena on 2008-09-21
> **Prefix100 said:**
> [http://onelinux.org]("http://onelinux.org")

sweet, bookmarked.  good luck.

---

### Post by freetonik on 2008-09-22
I got my blue windows-version of acer aspire one couple of weeks ago, installed ubuntu yesterday, it works great except for 2 things:

1) compiz eats ~30% of CPU even on medium settings. System works so much faster without it. What can you suggest? use xfce? or just disable compiz?

2) flash plugin (i've tried firefox 2, firefox 3 and opera) eats A LOT OF CPU RESOURCES! One youtube video in full screen got about 60-80%! What to do?!

Thanks!

---

### Post by saunders on 2008-09-23
Bought myself an AA One about a month ago. 

First thing to go was the original operating system, on went Ubuntu 8.04.1. For those wanting to do this, there are a couple of good tutorials...I recommend [this one]("https://help.ubuntu.com/community/AspireOne"). However, I couldn't get the wireless working using this tutorial. I had success following [Nicedudes instructions]("http://ubuntuforums.org/showthread.php?t=795984") to install the madwifi drivers, and [replacing the standard network manager with  WICD]("http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html"). One thing to note is, you may need to alter nicedude's instructions as the driver you download may have a newer version number...

I now have wireless working with Ubuntu!

First impressions are very good. Boot is pretty quick (about 30-40 sec from my memory). Battery time is good, not as bad as some reviews have said but not as good as the Eee 701. However, the keyboard is much better. My girlfriend has an Eee and the keyboard is just that bit too small for me to use quickly/accurately. I don't really notice any heat buildup, nor any problems with screen reflection.

I have cracked it open and installed another gig of RAM. That was easy enough, but for some reason the RAM is in a really awkward place (check out youtube to see). One thing to note though...it is unfortunately easy to put little dints in the case when you're taking it apart (though generally it's quite sturdy). Maybe that's just my general cack-handedness!

It's pretty nippy in general use, though sometimes slows on FF3, particularly if the pages are flash heavy. I have yet to determine if this is the fault of FF3, compiz or just the netbook in general.

Only problem yet unsolved is the speaker jack refuses to work...

Paid £199 in Currys and it's well worth it! OK, it's only 8Gb (~4.5Gb free with Ubuntu installed), but its size and portability more than make up for it.

---

### Post by miggols99 on 2008-09-23
> **freetonik said:**
> I got my blue windows-version of acer aspire one couple of weeks ago, installed ubuntu yesterday, it works great except for 2 things:

1) compiz eats ~30% of CPU even on medium settings. System works so much faster without it. What can you suggest? use xfce? or just disable compiz?

2) flash plugin (i've tried firefox 2, firefox 3 and opera) eats A LOT OF CPU RESOURCES! One youtube video in full screen got about 60-80%! What to do?!

Thanks!
1: Disable compiz or you can use Xfce's compositor if you want.
2: This is normal. Upgrade to flash player 10 to fix this (mostly...)

---

### Post by dgrafix on 2008-09-23
I have been modding around in mine (acer aspire one) and its now a vast improvement of its former self! 

I have installed Xubuntu and got (i think) everything working including the wireless. I have also switched the rubbish slow SSD drive for a 1.5" CF2ZIF converter with an industrial grade 16gb compact flash card and stuck in a gig of ddr2 ram. It is now flying :D

---

### Post by Garratt on 2008-09-26
> **Funk Phenomena said:**
> .  They each have their tradeoffs, both operating systems and machines.  Putting XP on any of these is blasphemy.  I hope ye sinners are ashamed! :p


i doubt anyone on this forum is "PUTTING" it on.

but fact is you are not buying an operating system, while you do get a aspire xp windows licence sticker with the xp version on the box, you don't get a xp cd. which i'm guessing is the extra $50 expense.
you get an extra 512mb ram, and 112g hhd space with the xp version which is nothing to scoff at..unless of course you dont need the  hdd space. and would prefer to stick your own ram in it. really boils down to personal preference both are great machines, 

many people who have bought the xp version have done so due to the extra hardware, and easily installed any OS out there, I actually installed vista SP1 for shits and giggles and it ran vista beautifully, mind you that only lasted a couple days before i got bored and removed it.
I currently have xp installed on a 30g part, and ubuntu on a 70g part.

Additionally you may have noticed theres no CD drive, thats is where the 120g SHINES the latest copy of daemon tools on xp, or of course simply create iso and mount iso on ubuntu(etc).
I have about 20 iso's on here that run whatever cd/dvd i need, and a few good movies as well.
You can buy a slim portable cd drive for the linpus version or eepc for $120 but wheres the fun in that.

G.
Peace.

---

### Post by smartboyathome on 2008-09-28
I've already got an external DVD burning drive (from before we had our desktop, as we couldn't burn DVDs without it). I'm thinking of reusing it with the Eee PC 1000. Does the Eee PC allow for booting up to CDs/DVDs from external drives? I am assuming it would.

---

### Post by mvsjes2 on 2008-10-02
At NCIX in Canada, there's an option to buy the 120G HDD with linux limpus for $339CDN. That's what I bought.

As others have alluded to, limpus is pretty much "Baby's First O/S". I immediately put Kubuntu Hardy on a separate partition using the AspireOne Ubuntu wiki and installed mythfrontend. It drives my 37" LCD TV out the VGA port and works great. (I bought this unit to double as a near silent front end and a portable device when I'm away from home.)

I have one major problem I haven't been able to solve however. While I'm watching recordings in myth, at some point (10s of minutes or up to some hours) the video suddenly scrambles or I get a blank screen and the system hangs.

I've gone through every log in /var/log and my myth frontend logs and I see absolutely no reason for this - no warnings, no errors, no nuttin.

It doesn't seem to be overheating since the case is only barely warm even after hours and hours of use.

So now I have a problem in that I don't know if this is flakey hardware or flakey software. I have all the latest updates installed.

Anyone have any ideas or suggestions on how I can track this one down? I love this little machine and I hope I can solve this since everything I have done with it so far has gone so very smoothly...

---

### Post by dgrafix on 2008-10-04
@smartbotathome

Yes, the aspire can boot from anything, usb cd/dvd, memory stick or using a network location. I used a portable cd drive to get Xubuntu going on it.

---

### Post by s.fox on 2008-10-05
I purchased an Acer Aspire One on Friday.  I have NOT removed the OS simply because I am going to give it a chance and also a little curious to see how it differs to Ubuntu.  Thus far I have managed to install several applications and also get the desktop switcher to work. 

The main problem I am experiencing is automatically running a terminal command on bootup.  In Ubuntu you would go System>Preferences>Session,  but unfortunately Linpus doesn't seem have a Preferences submenu.

I don't suppose anybody knows how to do this in Linpus?  If anyone could point me in the right direction I would be extremely grateful.


-Ash R

---

### Post by CumbrianTom on 2008-10-05
I have an EEE PC 900 with Ubuntu eee 8.04 installed on it. It's very quick and requires no tweaking to get everything working. I recommend all eee pc users to try it out.

---

### Post by s.fox on 2008-10-05
I managed to solve my problem :)

See [here]("http://ubuntuforums.org/showthread.php?p=5906270#post5906270") for details

---

### Post by dgrafix on 2008-10-07
> I purchased an Acer Aspire One on Friday. I have NOT removed the OS simply because I am going to give it a chance and also a little curious to see how it differs to Ubuntu. Thus far I have managed to install several applications and also get the desktop switcher to work.

The main problem I am experiencing is automatically running a terminal command on bootup. In Ubuntu you would go System>Preferences>Session, but unfortunately Linpus doesn't seem have a Preferences submenu.

I don't suppose anybody knows how to do this in Linpus? If anyone could point me in the right direction I would be extremely grateful.

xfce4-settings-(press tab)
brings up the xfce preferences. To load stuff automatically you need to edit one of the rc files in etc. but i cant remember which one off the top of my head.
I gave it a chance too, i got it doing almost everything i need, even a proper desktop, but unfortunately could not get it to access NFS shares as the kernel seems to have a lot removed. I guess this is to 'lighten' it.

---

### Post by uberdonkey5 on 2008-10-07
> **Garratt said:**
>  after using my usb as a portable OS(slowest OS on earth), there was no way in hell I would ever buy an eeepc, or linux version of aspire one.

well xp on eeepc is ridiculously slow, but xandros version of eeepc is not like running ubuntu off a usb pen (I agree, its a great idea, but doesn't really work well). Xandros boots in less than 30 secs on eee pc and shuts down in a matter of seconds (5?) Never had any problem with speed, though obviously its not for serious processing.

---

