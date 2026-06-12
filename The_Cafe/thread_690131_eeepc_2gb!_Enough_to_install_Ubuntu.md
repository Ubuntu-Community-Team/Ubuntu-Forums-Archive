---
title: "eeepc 2gb! Enough to install Ubuntu?"
date: 2008-02-07
forum: The Cafe
---

### Post by fatality_uk on 2008-02-07
I am tasked with getting 10+ of these little babies up and running for the sales dept.. My team are all Linux-Fobic (will be dealt with in this years training sessions, trust me) but am going to buy a 2GB version for test purposes. 

For consistency, I am running Gusty (7.10) and as such I want to be able to install Gusty onto theses machine. Is it possible with the 2GB version or will I just run into brick walls???

Anyone with experience of doing so please let me know.

---

### Post by frup on 2008-02-07
I wouldn't install Ubuntu on less than 4gb. I don't know if you would be doing linux a favour by installing gutsy, something lighter might be better. I had a look at a friends one and was actually a bit worried some new users might get a bad impression about linux (I don't particularly like xandros)

XFCE might be better.

---

### Post by p_quarles on 2008-02-07
I agree with frup: Ubuntu on a 2 gig HDD is really pushing things. I think the base installation takes up nearly that much.

I would suggest starting with a minimal installation image ([link](https://help.ubuntu.com/community/Installation/MinimalCD)) and adding exactly what you need. Once you have it configured as you like, it will be easy to clone this setup onto the other machines.

---

### Post by quinnten83 on 2008-02-07
there is on the interwebs an installation instruction for a special ubuntu EEE pc version.
Google it and install.
but i think that two GB is not enough.

[http://community.zdnet.co.uk/blog/0,1000000567,10006278o-2000331777b,00.htm](http://community.zdnet.co.uk/blog/0,1000000567,10006278o-2000331777b,00.htm)
[http://www.sampletheweb.com/2007/12/09/ubuntu-on-the-asus-eee-pc-part-1-or-how-to-run-a-functional-ubuntu-install-off-a-usb-drive/](http://www.sampletheweb.com/2007/12/09/ubuntu-on-the-asus-eee-pc-part-1-or-how-to-run-a-functional-ubuntu-install-off-a-usb-drive/)

these two links might provide options.

---

### Post by UbuWu on 2008-02-07
Not possible withouth any customization. You have several options:

1. start with a minimal installation and just add everything you need.
2. use a compressed filesystem (squashfs+unionfs), this will fit everything in about 1gb
3. mount the ssd as /usr which is about 1.9gb, put the rest on a sd disk

See this thread: [http://forum.eeeuser.com/viewtopic.php?id=9974](http://forum.eeeuser.com/viewtopic.php?id=9974)

---

### Post by original_jamingrit on 2008-02-07
Can I suggest Damn Small Linux (DSL) [http://damnsmalllinux.org/](http://damnsmalllinux.org/) ?  If you look around, there's probably a user-friendly derivative of it, if not you can try to roll your   Just keep it small, and keep it simple.

---

### Post by starcannon on 2008-02-07
I have both a 4g 701 and a 2g Surf.

The 2g Surf barely has enough room for the xandros linux that is already installed on it.

The 2g Surf is little more than a "web device", you can put a 16 gigabyte SDHC card in the MMC card slot, down side is that I have not found a way to get ACPI to behave in a useful fashion with the MMC Slot, it resumes with permissions all mucked up. 

You could try the "Full KDE Desktop Hack" at eeeuser.com forums, That would be my best advice on the 2G.

However, if your buying your team the 4g or 8g you'll be fine, On the 4G 701 I upgraded it to 2gb of ram, put in a 16gb SDHC card, and I'm running Ubuntu Gutsy 7.10 with compiz and a desktop cube and lots of effects with no trouble at all (with exception to suspend resume issues on the SDHC card, which is where I have /home installed to)

---

### Post by michaelzap on 2008-02-07
> **starcannon said:**
> I have both a 4g 701 and a 2g Surf.

The 2g Surf barely has enough room for the xandros linux that is already installed on it.

The 2g Surf is little more than a "web device", you can put a 16 gigabyte SDHC card in the MMC card slot, down side is that I have not found a way to get ACPI to behave in a useful fashion with the MMC Slot, it resumes with permissions all mucked up. 

You could try the "Full KDE Desktop Hack" at eeeuser.com forums, That would be my best advice on the 2G.

However, if your buying your team the 4g or 8g you'll be fine, On the 4G 701 I upgraded it to 2gb of ram, put in a 16gb SDHC card, and I'm running Ubuntu Gutsy 7.10 with compiz and a desktop cube and lots of effects with no trouble at all (with exception to suspend resume issues on the SDHC card, which is where I have /home installed to)

So did you really hate the installed version of Xandros (even with the full desktop enabled)? I'm planning on getting one of these, but I'm not sure if I should wait for the next generation in April. Did you try eeexubuntu and still have problems with the SDHC cards?

---

### Post by quinnten83 on 2008-02-07
I was just about to suggest [eeebuntu]("http://www.eeebuntu.org/"), but i got beaten to the punch!

---

### Post by fatality_uk on 2008-02-07
Managed to find the 4GB verion in PC World for just another £30
Am typing from the eeePC right now.
The keyboard is GREAT even for a fat fingered lardy like me,

All round great. Can't wait to get Ubuntu on it and clck it to 900Mhz :)

The xandrtos desktop isnt that bad actually ;)

---

### Post by phrostbyte on 2008-02-07
Try eeeXubuntu, it's Ubuntu with a more lightweight desktop environment and tweaked for the eeePC especially. It's full Ubuntu though with all the same repositories.

Edit: Sorry if someone mentioned it eariler.

---

### Post by fatality_uk on 2008-02-07
I'll look at that cheers
I am amazed at how good this is. I thought that it would be hard with this screen and keyboard but after 10 mins, can't fault it. Only thing is the XP-a-like styling ;)

---

### Post by HermanAB on 2008-02-07
I have installed Mandriva 2008.1 with IceWM and it took about 900MB.  With KDE, it took 1.8GB.  So you could install Linux on a 2GB Eee PC, provided that you use IceWM and you are very careful with what utilities you install.  However, I won't recommend doing so.

My present setup has 2GB RAM, 4GB SDD and 8GB SD Card, using all 4GB SDD for /, all 8GB SD Card for /home and no swap.  It works great that way.

---

### Post by jbonll05 on 2008-02-07
eeepc 2g big enough for Ubuntu;
 I just finished installing and 1st use of Xubuntu on a 4g Surf, The OS is 578 megs as I have set it up. Considering removing the Gimp, as I will not be doing advanced image processing on this little laptop. That would take the os down to about the size of the Xandros OS that came on the machine.
JB, Ubuntu since 4oct05

---

### Post by esaym on 2008-02-08
Would be alot better to run a custom set up of debian-testing from the net install cd.  Would give you the ability to instal only the stuff you needed and thus a major speed boost.

---

### Post by red_Marvin on 2008-02-08
I would think that something that is tailored for working on flash disks, or at least something working as a live cd, maybe with an extra partition for /home would be best.

My point is that to my knowledge linux by default constantly writes a number of logs etc, and that flash memory has a quite limited number of writing cycles per bit until the bit fails, and that a distro that takes this into consideration would be better fitted for this.

I'm not pointing at any distro at all, but I would recommend anyone wanting to put .+ on an eee (or any other flash based device) to read into if the intended distro is just slimmed down or is actually configured to run a flash device.

...I still want one though...

---

### Post by fatality_uk on 2008-02-08
One slight hitch. I am running rdesktop with seamlessRDP for access to our ERP system on my lappy. Forgot about the 800x480 screen res. The min for this is 800x460 bugger!!! I know there's a XP hack to bump the res. Don't need anything more than 800x600 though :( Don't wanna install it yuk

I'll keep pluggin away

---

### Post by markp1989 on 2008-02-09
i have ubuntu installed on my 4gb eee pc, started from the base install and built up from there, after i have everything as i want the OS takes up about 930mb

---

### Post by HermanAB on 2008-02-09
"I know there's a XP hack to bump the res. Don't need anything more than 800x600 though"

Try "-g 80%":

rdesktop -g 80% -A -s "c:\seamlessrdp\seamlessrdpshell.exe notepad"  windowsboxipaddress

Other than that, get used to Alt-Click-Drag.

Cheers,

Herman

---

### Post by Mateo on 2008-02-09
does standby/hibernate work in eeexubuntu?

---

### Post by fatality_uk on 2008-02-09
> **HermanAB said:**
> "I know there's a XP hack to bump the res. Don't need anything more than 800x600 though"

Try "-g 80%":

rdesktop -g 80% -A -s "c:\seamlessrdp\seamlessrdpshell.exe notepad"  windowsboxipaddress

Other than that, get used to Alt-Click-Drag.

Cheers,

Herman

Herman thanks. If that works, I may be forced to fly over and kiss you, in a manly way of course :lol:

---

### Post by fatality_uk on 2008-02-09
Greetings from eeexubuntu :D
I am SERIOUSLY thinking about this as my production machine.
Monitor, keyboard and mouse in the office and throw this in my jacket pocket when I go out and about

---

### Post by popch on 2008-02-09
> **fatality_uk said:**
> throw this in my jacket pocket when I go out and about

You must have some serious jacket pocket size, all the same.

---

### Post by fatality_uk on 2008-02-19
> **popch said:**
> You must have some serious jacket pocket size, all the same.

I do. I have a HUGE cord jacket from GAP. Sheepskin lined. Think cowboy type. And seeing as I am a "LITTLE" on the big size, the jacket is big :) hence the big pockets

---

### Post by derekr44 on 2008-02-19
Try Arch.

---

### Post by setinstone31 on 2008-02-20
NO! you can't install ubuntu, not even eeexubuntu without severly limiting capabilities.(-swap and other things)  Xandros version sucks, feels limited (even in full desktop mode+ couldn't get wifi to work)  I'd install windows xp, it's your best bet (all updates but .NET + better screen size), I know that's not a very popular option on a ubuntu forum , but it runs the best under eeepc 2G, or should I say 1.86Gig.  Yeah Also This thing is not under GPL, it's very closed source, can't change cpu, and ram is too hard to change.  So you freedom people might wanna stay away.  THIS is for eeepc 2G (surf) only.
I believe ubuntu will let you install on a sd card, and just boot from the 4 Gig card, and keep whatever on the HDD

Good luck

---

### Post by jken146 on 2008-02-20
If I had an eeepc I would install Arch.

---

### Post by fatality_uk on 2008-02-20
> **setinstone31 said:**
> NO! you can't install ubuntu, not even eeexubuntu without severly limiting capabilities.(-swap and other things)  Xandros version sucks, feels limited (even in full desktop mode+ couldn't get wifi to work)  I'd install windows xp, it's your best bet (all updates but .NET + better screen size), I know that's not a very popular option on a ubuntu forum , but it runs the best under eeepc 2G, or should I say 1.86Gig.  Yeah Also This thing is not under GPL, it's very closed source, can't change cpu, and ram is too hard to change.  So you freedom people might wanna stay away.  THIS is for eeepc 2G (surf) only.
I believe ubuntu will let you install on a sd card, and just boot from the 4 Gig card, and keep whatever on the HDD

Good luck
TROLL away little man, but guess what ,without wanting to insult you:
> NO! you can't install ubuntu, not even eeexubuntu without severly limiting capabilities
Is a crock of happy horse s**t :D Banter mods, just baner ;)

I bought a 4gb machine instead and it runs Ubuntu 7.10 **WITHOUT** fault.

The default xandros OS is what it is in easy mode, in advanced mode it's a full desktop, with any of Windows limitations ;)
> couldn't get wifi to workHow was that? It works out the box? perhaps you were looking for an XP driver to install. Ooops!!! :D

---

### Post by ssam on 2008-02-20
why not just leave them running the default install.

it boots fast, lauches built in apps fast, as all the basic apps that most people would need and it optimised for the small screen size.

---

### Post by michaelzap on 2008-02-20
> **ssam said:**
> why not just leave them running the default install.

it boots fast, lauches built in apps fast, as all the basic apps that most people would need and it optimised for the small screen size.

That's what I've been thinking. I don't own one yet, but when I buy one I'm at least going to try it out for a while with Xandros in full desktop mode. I love Ubuntu, but a 15-second boot time and everything optimized to your specific (and tiny) hardware is tough to beat...

---

### Post by phrostbyte on 2008-02-20
> **jken146 said:**
> If I had an eeepc I would install Arch.

For my own machine. But if I was running a business I'd stick with eeeXubuntu. Bleeding edge software and rolling updates on salespeople's PC? Scary I tell you.

---

### Post by fatality_uk on 2008-02-20
> **phrostbyte said:**
> For my own machine. But if I was running a business I'd stick with eeeXubuntu. Bleeding edge software and rolling updates on salespeople's PC? Scary I tell you.

It's scary enough letting them lose with this thing I can tell you :D
Trying to explain why there isn't a computer icon on the desktop was a fun 15 mins!

---

### Post by michaelzap on 2008-02-20
Although I guess if I wait just a little bit longer, there may be other even more enticing options. Like [this HP UMPC]("http://www.engadget.com/2008/02/19/hps-umpc-2133-revealed/") that's hit the rumor mill. At least the price of the current eeePCs should go down in April when the new ones are supposed to come out.

---

### Post by fatality_uk on 2008-02-20
> **michaelzap said:**
> Although I guess if I wait just a little bit longer, there may be other even more enticing options. Like [this HP UMPC]("http://www.engadget.com/2008/02/19/hps-umpc-2133-revealed/") that's hit the rumor mill. At least the price of the current eeePCs should go down in April when the new ones are supposed to come out.

Wow, looks nice, However, as 1 comment put it, will probably be 4 x the price of the eeePc ;)

---

### Post by markp1989 on 2008-02-20
i have a 4gb eee epc, and i have installed ubuntu , started from CLI and built up what i wanted, uses icewm, and the install takes up 700/800mb, total

---

### Post by michaelzap on 2008-02-20
> **fatality_uk said:**
> Wow, looks nice, However, as 1 comment put it, will probably be 4 x the price of the eeePc ;)

I've heard $630, but who knows? They haven't even specified whether it will have a regular hard drive or flash, what CPU it will use, how much RAM it will have, etc. For all I know it's actually just a hoax or some marketer's idea for generating a buzz.

---

### Post by Compucore on 2008-02-20
I would agree with Frup here. 2 gig is too small for gutsy gibson. I remember the earlier version of ubuntu you would be able to without a problem. I think it was Hoarty Hedghog used 2 gigs at that time. But if you can get at least a 10 gig drive to work with on the test machine you would be okay with that. Worste case scenario a computer recycling center may have some refurbished hard drives if it is for a workstation. And goes around $25 canadian for a 40 gig hard drive last I had checked.

Compucore

---

### Post by heiowge on 2008-04-14
i have a 2gsurf.  I'm running the default xandros, but I want to install and run ubuntu hardy when it comes out from my 8gb usb flash drive(in a similar way to mandriva flash).  I also have a 4 gb SDHC card - class 6 as an install option.

Complete linux noob (2 months only), any recomendations?

---

### Post by heiowge on 2008-04-19
Anyone know if can I install Gutsy to my Class6 4GB SDHC card, and put the swap partition on the ssd?

If so, how?

---

### Post by heiowge on 2008-04-19
bump

---

### Post by HermanAB on 2008-04-19
The problem is that a SD card or USB stick is much slower than the internal SSDD.  The SSDD is 10x faster than the SD card.  Therefore, you need to boot off the SSDD, but you can put /home of the SD card.

Cheers,

Herman

---

### Post by heiowge on 2008-04-20
With a 2GB machine, is this still possible?

---

### Post by furbuntu on 2008-07-07
I installed Ubuntu on my 2G surf and after some tinkering it's working great with 600MB free for files. But, it won't work out of the box...

The problem you'll face with the 2G is that the SSD isn't big enough for a full install. If you want to do it the way I did, you'll need a seperate 2GB flash drive, a 2GB partion on the flash drive you're installing from, or 2GB SD/MMC card to temporarily store the /usr partion for install.

In short, install Ubuntu as normal, except put /usr on the flash drive/card. Then boot and either (a) cull the installed packages until /usr is small enough to move back to the SSD, or (b) compress the /usr directory to the SSD. I recommend (b). See:

[http://po-ru.com/diary/linux-liposuction-or-xubuntu-in-under-a-gig-on-the-eee-pc/#c006780](http://po-ru.com/diary/linux-liposuction-or-xubuntu-in-under-a-gig-on-the-eee-pc/#c006780)

Doing it this way you can roughly expect the size of /usr to be cut in half, which should make for a comfortable fit on the SSD. Even so, you'll probably want to run updates, add needed applications, and delete any packages you don't plan on using before compressing /usr. Try:

sudo apt-get clean

before compressing too to clean out old unused packages.

Then just be sure to remove the flash drive/card from /etc/fstab and you're done. :)

P.S. Good luck.

---

### Post by fatality_uk on 2008-07-07
Ill let the admins explain about necromancy ;)
However, I went for the 4GB instead in the end. Fat lot of good that did me :lol:

---

