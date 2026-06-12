---
title: "How To Get On Kazaa, Ares, Gift and Gnutella in one program"
date: 2006-06-18
forum: Tutorials
---

### Post by Johnsie on 2006-06-18
2008 UPDATE---

Hi folks, I originally started this thread in 2006. Sadly the method shown below wont work anymore. As far as I know the Apollon and Gift projects have been discontinued. I recommend that you try Frostwire instead or use more legit ways of getting free music. There's plenty of great unsigned artists out there just waiting to be discovered and many of them have free music. Don't limit yourself to the music the greedy industry has forced on us. Videos and apps can be found too :-)
-----

I'm using apollon with Ares, Gift, Kazzaa(Fasttrack) and Gnutella all at the same time. It takes a bit of configuration but I think it's worth it. Here's how I do it:


1. In the terminal type:
> sudo gedit /etc/apt/sources.list

2. Add the following to the bottom of the document in gedit:
> deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib
deb-src [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib

3. Save the file

4. In the terminal type:
> sudo apt-get update
sudo apt-get install gift libares-gift libfasttrack-gift apollon

5. The following instructions must be carried out by each individual user. In the termnial type:
> gift-setup


You'll get asked a bunch of questions:

***THE MOST IMPORTANT PART IN THIS BIT IS TO MAKE SURE YOU TYPE IN THE FOUR NETWORKS WHEN IT ASKS YOU WHICH PLUGINS TO USE****

> Ares:Gnutella:FastTrack:OpenFT

Remember that it's case sensitive you you have to have your capital letters in the right places.

In this setup prgram you might also want to **change the folder your completed downloads go into**. By default the files go into a hidden folder which is not to everyone's taste. So make sure you change that when you're asked where you wanted completed files to go.


After that you can just keep hitting return and then run apollon from the terminal by typing:
> apollon

(if apollon fails to connect the first time close it, type giftd in the terminal and try opening it again. You will only ever have to do that once)

Yes, it may take a few minutes to set up but in the long run it's definitely worth it because you have access to all the major filesharing networks and a pretty decent gui.

**A note about ares:** For some reason it doesn't give me the right information about ares. It says there are only 2 people connected to the ares network. That doesn't mean you are not connected properly to ares. Ares files will still come up when you do a search. I think it's just that the counter doesn't work and that's not a serious problem.

**Disclaimer: **Please only use the info in this howto to download legal files. I accept no responsibility for anything you use this howto for.

---

### Post by newlinux on 2006-07-07
This worked well for me. Lots of questions asked during setup, but I was able to connect to all 4 networks. I'll try Apollon out. Thank you!

---

### Post by Johnsie on 2006-07-12
You're welcome... This is my first howto so I'm glad it worked :-)

---

### Post by phizz on 2006-07-13
lots of questions. I got on there with all 4 nets working fine. it all seems to be porn and seinfeild. who knew. :)

---

### Post by papangul on 2006-07-18
Thanks,this how-to deserves to be on ubuntuguide.org.

I'm getting the following error on running apt-get update:
```
W: GPG error: [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A35A4E6EF00175CA
```

Edit: The above message seems to be just a warning not a showstopper.

---

### Post by greenbmw530i on 2006-07-19
I set it up correctly and forwarded all needed ports, but for some reason, Apollon only connects to the Gnutella, OpenFT, and FastTrack networks -- where did I go wrong with the Ares network?

Edit: disregard the above -- it just takes a little while for some of the networks to connect. For me, Gnutella and FastTrack connected first. Ten minutes after that, OpenFT connected, and about 5 minutes after that, Ares connected. So, to anybody who thinks the networks aren't connecting: be patient! ;)

---

### Post by newlinux on 2006-07-19
> **greenbmw530i said:**
> I set it up correctly and forwarded all needed ports, but for some reason, Apollon only connects to the Gnutella, OpenFT, and FastTrack networks -- where did I go wrong with the Ares network?

Edit: disregard the above -- it just takes a little while for some of the networks to connect. For me, Gnutella and FastTrack connected first. Ten minutes after that, OpenFT connected, and about 5 minutes after that, Ares connected. So, to anybody who thinks the networks aren't connecting: be patient! ;)

I get the same issues. sometimes some of networks take quite a while to connect. But everything works well with patience.

---

### Post by daedalusman on 2006-07-24
Nice guide, I'm using giftui under gnome and it's working great. I've been wanting a program like this for a while now. Thanks for posting this howto.

---

### Post by Kimm on 2006-07-25
I cant get this to work... could someone post their config file?

---

### Post by Lucidio on 2006-07-25
Where can i see some screenshots for apollon?
How it work?

---

### Post by IrishGangsta on 2006-07-27
I actually downlaoded Apollon a while ago, and couldn't find out how to activate it to make it connect. 

This is just what i needed.

Thank you

---

### Post by McDuff on 2006-07-28
i installed apollon following this howto, and configured it. when starting apollon i'm getting this:
```
Link points to "/tmp/ksocket-georg"
Link points to "/tmp/kde-georg"
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
apollon: [virtual void ApollonPreferencesDialog::readConfig(bool)] init = true

```

when starting giftd i get the following error:
```
*** ERROR: Your setup is incomplete ***

You will need to run gift-setup and be sure that you read absolutely
every configuration option (no, really).  Some default configuration
values are considered illegal, and will raise this error message.  If you
suspect that you have configured giFT properly, consult the conf files in
/home/georg/.giFT/ for diagnostic purposes.

If you are still having problems you should consult the QUICKSTART guide
available from the standard giFT distribution.

```

at the same time i installed kceasy (the windows-equivalent to apollon) on an other machine with the same settings, and it's working fine.
does anyone have an idea what i could do?

---

### Post by xolot1 on 2006-07-28
libares-gift and libfasttrack-gift dont seem to be in these repositories? or maybe i did something wrong, but i merely copy and pasted...

---

### Post by boast on 2006-07-28
I also get ```
Connection error
The giFT daemon, which is responsible for connecting to the various networks, appears to be down and I don't seem to able to start it.
Probably your giFT installation is corrupted. Try starting giFT manually by typing "giftd" on the command line. If this gives errors, there's likely some internal error in giFT or in your giFT configuration. Refer to the giFT homepage at http://giftproject.org for help.
```

---

### Post by jetpeach on 2006-08-08
After apollo starts, i'm also getting "Connection error
The giFT daemon, which is responsible for connecting to the various networks, appears to be down and I don't seem to able to start it.
Probably your giFT installation is corrupted. Try starting giFT manually by typing "giftd" on the command line. If this gives errors, there's likely some internal error in giFT or in your giFT configuration. Refer to the giFT homepage at [http://giftproject.org](http://giftproject.org) for help."

I'm run the config several times, can't find what's wrong.
Question: did people choose Y or N on the first question about preserving your defaults settings or something?  I chose N, maybe this was the problem.
edit: oh, when you choose no it just skips everything.  nevermind.  anybody have any ideas on the config file, or could they just post hteres?

---

### Post by jetpeach on 2006-08-08
Ok, I found the problem [most likely] for those of us with the error message at the beginning.  The first question of the gift-setup, you have to CHANGE from default of 0 to make it 1 or some number.  This makes me kinda pissed, because they say, "we put this in here just to make sure you read this." 
When they say, "this value must be non-zero blah blah" but really this is just a completely unnecessary config question that wastes are time and makes things "just NOT work".  arg, that's annoying, whose idea was that anyway?  plus, whose idea is a fricken 35 questions command line config with 3000 words?!  All for all the others (except the networks to connect to as mentioned in the howto) the default works.  But it would be nice to config all this graphically anyway... 
[/rant] Well, anyhow, now I get to test my Apollon!

Edit: anybody know which package is needed to get the preview/internal player working in Apollon?  it says the "kde multimedia-video" package is needed.  Searching the packages, couldn't find what they're talking about...

---

### Post by TFrog on 2006-08-10
I tried this once and couldn't get it working.  Went back later on when I'd gotten some sleep and attempted it again.  Works fine on Kubuntu 6.06 Dapper LTS.  Yes, even I got issues with the damn thing connecting to the Ares network (slow connecting and only showing 2 connected) but all and all an excellent How-To.  This means my desktop can now do P2P without Java whatsoever:-o   Limewire Pro and Frostwire would freeze up my desktop system randomly with any form of Java (open source or Sun):-( Now if I could just get the system to not lockup while playing Pysol solitaire I'd be very happy indeed.

---

### Post by Anonii on 2006-08-26
I only get connected to Gnutella, the others are just connecting for an eternity :/

---

### Post by brucevangeorge on 2006-08-28
Apollon uses KDE libraries. Wouldn't it be a performace hit to use KDE libs when running gome... since it also uses its own?

Anyone know of a gnome app that does multinetwork also?

---

### Post by blent07 on 2006-09-04
awesome! thanks johnsie!

---

### Post by picpak on 2006-09-04
> **brucevangeorge said:**
> Apollon uses KDE libraries. Wouldn't it be a performace hit to use KDE libs when running gome... since it also uses its own?

Anyone know of a gnome app that does multinetwork also?

giftoxic and giftui.

---

### Post by 3rr0r on 2006-09-05
I keep getting this error... any idea?


NOTE:
There may be another giFT daemon running on this host.  Check to see if the
interface port (1213) is currently in use by another process.

*** Often times more information can be found in the log file or with the -v command line switch.
*** GIFT-FATAL: Failed to load interface subsystem

NOTE:
There may be another giFT daemon running on this host.  Check to see if the
interface port (1213) is currently in use by another process.

*** Often times more information can be found in the log file or with the -v command line switch.
QGDict::hashKeyString: Invalid null key
kopete (irc - raw protocol): >> QUIT :bye

err0r@Lappy:~$ giftd
ICE default IO error handler doing an exit(), pid = 12291, errno = 0
apollon

---

### Post by 3rr0r on 2006-09-05
Now, here is the full readout of the error.


```

err0r@Lappy:~$ apollon
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not fo und
apollon: [virtual void ApollonPreferencesDialog::readConfig(bool)] init = true
err0r@Lappy:~$ *** GIFT-FATAL: Failed to load interface subsystem

NOTE:
There may be another giFT daemon running on this host.  Check to see if the
interface port (1213) is currently in use by another process.

*** Often times more information can be found in the log file or with the -v command line switch.
*** GIFT-FATAL: Failed to load interface subsystem

NOTE:
There may be another giFT daemon running on this host.  Check to see if the
interface port (1213) is currently in use by another process.
```

Then I tried
```
giftd
``` and it just sat there doing nothing ( i waited about 10 mins).  then I tried

```
giftd apollon 
```  with the same results.  Please help me.

---

### Post by 3rr0r on 2006-09-06
shameless bump because its still not working for me ](*,)

---

### Post by 3rr0r on 2006-09-06
still won't work

---

### Post by blent07 on 2006-09-06
just a kind wild guess, but it mentions that the port may be in use? so heck, my first idea would simply be to restart so it clears everything then try it.

---

### Post by 3rr0r on 2006-09-06
> **blent07 said:**
> just a kind wild guess, but it mentions that the port may be in use? so heck, my first idea would simply be to restart so it clears everything then try it.

I tried restarting with the same error.  I don't know how to manually configure the port so that nothing else is using it.  I really just want to uninstall the whole thing.

---

### Post by lokirulez on 2006-09-10
Everything installed fine for me. When I open Apollon, it connects right away, but it only shows Ares and FastTrack in the Info screen. Where is Gnutella and OpenFT? When I go to the options and look at the Plug-ins, all four of them are there. But they are not displayed in the Info screen. 

I thought maybe I was still connected to all 4 networks, and it was a problem with Apollon not displaying the other two networks. But when I run a search, I only get results for Ares and FastTrack. What is going on here? Anyone else encounter this?

---

### Post by alfzer0 on 2006-09-11
For anyone having troubles connecting to certain networks, don't forget to forward your ports if they are blocked.  I could only connect to the Gnutella network before opening these up.  Below is a list of the default ports for the different networks as setup by the gift-setup...

Ares:
59049

Gnutella:
4307

FastTrack:
1214

OpenFT:
1308
3074

-Jeff

---

### Post by sktfeelsdapper on 2006-10-08
This isn't working for me, the repositaries don't exist or something.

---

### Post by hikaricore on 2006-10-08
> **sktfeelsdapper said:**
> This isn't working for me, the repositaries don't exist or something.

aye the server for them seems to be down, I can't even ping it at the moment :/

---

### Post by hikaricore on 2006-10-08
::Update::

until the repos come back online I've got an alternate source to your missing packages here:

[http://ubuntu.cs.mtsu.edu/packages/multimedia/pool/main/gift-fasttrack/libfasttrack-gift_0.8.9-0.2_i386.deb](http://ubuntu.cs.mtsu.edu/packages/multimedia/pool/main/gift-fasttrack/libfasttrack-gift_0.8.9-0.2_i386.deb)
[http://ubuntu.cs.mtsu.edu/packages/multimedia/pool/main/gift-ares/libares-gift_0.3.0-1_i386.deb](http://ubuntu.cs.mtsu.edu/packages/multimedia/pool/main/gift-ares/libares-gift_0.3.0-1_i386.deb)

you'll have to manually install them with the gui or "sudo dpkg -i packagename.deb"

enjoy

---

### Post by guysmiley25 on 2006-10-10
Does anyone here know how to get giftd to run on boot?

---

### Post by guysmiley25 on 2006-10-11
Anyone? I have started a thread here

[http://ubuntuforums.org/showthread.php?t=275116](http://ubuntuforums.org/showthread.php?t=275116)

And I have started to make a init script for it but I dont really know what I am doing. Anyone got any ideas?

**Edit:** I sloved this goto my thread.

---

### Post by blent07 on 2006-10-13
Is anyone else having the following probelm with Apollon?

When I open the program, it takes the partition that it downloads to (I use this partition particularly for downloads, but with other programs as well) and it locks it so suddenly I can't write to it. Additionally, the program Pauses ALL the downloads and refuses to let me Resume them. I have to close Apollon, umount and re-mount my partition to gain write access back. PLUS, to make it weirder, it will radnomly stop doing that and work fine for a while, then suddenly go back to pausing and locking my partition. I can't see any pattern. 

????

---

### Post by stansaraczewski on 2006-10-14
Is there a definitive way to get apollon installed ? I've searched this and other threads and it seems to require experimenting... I've added the two repositories, did the update, and ended up with this:

W: GPG error: [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A35A4E6EF00175CA
W: You may want to run apt-get update to correct these problems
stan@stan-desktop:~$ sudo apt-get install gift libares-gift libfasttrack-gift apollon
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gift

---

### Post by hikaricore on 2006-10-15
or that's cool too, don't bother to read the numerous people posting that some of the repository servers are down and how to go about fixing it, just blindly post the dump of apt-get failing....

---

### Post by stansaraczewski on 2006-10-15
I did see your reference to two .deb files but they didn't get me very far...

"Error: Dependency not satisfiable: LIBGIFT0". 

I hunted around a bit for a solution to THAT, then decided to "blindly post".

---

### Post by hikaricore on 2006-10-15
eh sorry bout that, don't mind me, I didn't have any smokes last night :P  you should have seen the way I acted towards people I was actually around >.<  needless to say I slept on the couch.  so yea.. sorry bout that

anyway

make sure you have all of the universe and other such repositories enabled in your sources.list

after you do:
```
sudo apt-get install gift apollon
```

it *Should* install all gift dependancies without a fuss, I tried it on a fresh system and it worked fine.  *Then* I downloaded the other two DEB files for ares and fasttrack:

```

cd ~
wget http://ubuntu.cs.mtsu.edu/packages/multimedia/pool/main/gift-ares/libares-gift_0.3.0-1_i386.deb
wget http://ubuntu.cs.mtsu.edu/packages/multimedia/pool/main/gift-fasttrack/libfasttrack-gift_0.8.9-0.2_i386.deb
sudo dpkg -i libares-gift_0.3.0-1_i386.deb
sudo dpkg -i libfasttrack-gift_0.8.9-0.2_i386.deb

```

and ran: **gift-setup**

from that point everything went smoothly.

maybe just maybe I have something in my sources.list that you don't which is letting me access all of the extra files needed, so for the sake of arguement i'll post it here (i have alot of crap i don't need and I never remove things i just comment them out, I also don't have the keys for any of these you'll have to deal with the errors if needed):

***please don't replace your sources.list without backing it up first incase something goes wrong***

```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb http://wine.budgetdedicated.com/apt dapper main

## Debian Sarge (stable) users:
deb http://splashy.alioth.debian.org/debian stable main

## Debian Etch/Sid (testing/unstable) users:
deb http://splashy.alioth.debian.org/debian unstable main

## XMMS2
deb http://exodus.xmms.se/debian dapper main
deb http://xgl.compiz.info/ dapper main aiglx
deb-src http://xgl.compiz.info/ dapper main aiglx

## Debian Multimedia

deb http://mirror.home-dn.net/debian-multimedia stable main
deb-src http://mirror.home-dn.net/debian-multimedia stable main

deb http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia stable main
deb-src http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia stable main

deb http://floating3.ucd.ie/debian stable main
deb-src http://floating3.ucd.ie/debian stable main

deb http://debian-multimedia.dfoell.org/ stable main

## rem 101506 no rout ot host ##deb http://debian-multimedia.fx-services.com/ stable main
## rem 101506 no rout ot host ##deb-src http://debian-multimedia.fx-services.com/ stable main

deb http://debian-multimedia.gnali.org stable main
deb-src http://debian-multimedia.gnali.org stable main

deb http://debian-multimedia.informatik.uni-erlangen.de/ stable main

deb http://debian.dc-uoit.net/debian-multimedia/ stable main

deb http://mirrors.ecology.uni-kiel.de/debian/debian-multimedia stable main
deb-src http://mirrors.ecology.uni-kiel.de/debian/debian-multimedia stable main

deb http://debian-mirrors.sdinet.de/debian-multimedia stable main

deb http://ieso.gotdns.com/debian-multimedia/ stable main

deb http://debian.nsu.ru/debian-marillat/ stable main

deb http://ftp.mgts.by/debian-multimedia/ stable main
deb-src http://ftp.mgts.by/debian-multimedia/ stable main

## duplicate ## deb ftp://ftp.mgts.by/debian-multimedia/ stable main
## duplicate ## deb-src ftp://ftp.mgts.by/debian-multimedia/ stable main

deb http://debian.netcologne.de/debian-multimedia.org stable main
deb-src http://debian.netcologne.de/debian-multimedia.org stable main

## duplicate ## deb ftp://debian.netcologne.de/debian-multimedia.org stable main
## duplicate ## deb-src ftp://debian.netcologne.de/debian-multimedia.org stable main

deb http://debian.three-dimensional.net/debian-multimedia stable main
deb-src http://debian.three-dimensional.net/debian-multimedia stable main

# automatix

deb http://www.getautomatix.com/apt dapper main


# ???

deb http://se.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper main restricted


deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free

##deb http://exodus.xmms.se/debian dapper main

#deb http://apt.cerkinfo.be/ unstable main contrib
#deb-src http://apt.cerkinfo.be/ unstable main contrib

deb http://www.mclean.net.nz/debian stable contrib


##alacrost debian##
deb http://debian.ettin.org/allacrost unstable main
deb-src http://debian.ettin.org/allacrost/ unstable main

## The DarkMageZ Repo =D containing anything DarkMageZ Feels Like! v6.06 ##
## http://mirror.randumb.org/darkmagez/repo/dists/dapper-darkmagez/games/  ##
deb http://mirror.randumb.org/darkmagez/repo dapper-darkmagez games
deb-src http://mirror.randumb.org/darkmagez/repo dapper-darkmagez games
deb http://mirror.randumb.org/darkmagez/repo dapper-darkmagez all
deb-src http://mirror.randumb.org/darkmagez/repo dapper-darkmagez all

```

since I'm able to install with this list I don't see any reason you shouldn't be able to as well.

good luck,

--aaron

---

### Post by stansaraczewski on 2006-10-16
Thanks for the kind words. 

I managed to find what I needed and got it installed. This is the second go around, the first being on Breezy Badger a couple of months ago on a different machine.

---

### Post by hikaricore on 2006-11-01
Oddly after the edgy upgrade and a fresh install I can't seem to connect to anything with apollon.  My ports are open (even tested this from my work) and there isn't any firewall running at the time.  Very weird.  Ares connects for 5 seconds sometimes then goes back to connecting.  :/

---

### Post by turkenator on 2006-11-02
thanks alot really apriciated

---

### Post by La muerte del DIos on 2006-11-09
Update: I recently could connect to the Ares network but not to the others.

Same problem here. I could connect from dapper (although never to the ares network), but can't connect to anything with edgy. :confused:

---

### Post by hyperair on 2007-01-17
Someone save me.. I can only connect to the OpenFT network, but not the rest.

---

### Post by Rizado on 2007-01-17
Only OpenFT is working for me too. Can't make it connect anything eventhough I've forwarded ports. And really forwarding ports shouldn't be necessary right? Only when someone else tries to connect to you.

And when running giftd in verbose mode I get loads of these:
```
[17:50:52] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.224.5.150:2457
[17:50:52] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.122.50.217:1734, load: 50%
[17:50:52] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.38.42.227:1094
[17:50:52] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.224.139.156:3278, load: 50%
[17:50:52] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.202.251.202:3654
```

---

### Post by fang2415 on 2007-02-14
Not sure if this thread is dead, but I'll join the other voices of 2007 by saying that I can't connect to anything but OpenFT (I'm on Dapper).

I've taken the advice of people on this thread and been patient for a good old while to connect.  Like, days.  Still no luck.  I've Googled till my fingers hurt and found almost nothing about any tricks to try ("ubuntu ares" hardly turns up anything, surprisingly -- the people posting here can't be the only Ubuntu users using the Ares network?).

Weirder still, "grep -i ares .giFT/giftd.log" gets me *only* the following (even though giftd.log is 3396 lines long!):
```

[00:01:36] Plugin Ares (0.3.0) successfully loaded and initialized
[00:01:36] Ares: asp_plugin.c:230(asp_giftcb_start): Starting up.
[00:01:36] Ares: as_ares.c:88(as_init): Initializing Ares library...
[00:01:36] Ares: as_ares.c:50(port_change_cb): Moved http server to port 59049
[00:01:36] Ares: as_node_man.c:492(as_nodeman_load): Loaded 400 nodes from node 
file
[00:01:36] Ares: as_session_man.c:97(as_sessman_connect): Requested: 4, connecte
d: 0, connecting: 0

```
The port seems to be forwarding from my router just fine, although I'm not 100% sure I'm checking it right (does anybody know a surefire way to do this?).

The only thing I could deduce from this output is that my node file might be outdated.  This looks promising because nearly all of the values in the last_seen columns of ~/.giFT/Ares/nodes and /usr/share/giFT/Ares/nodes are timestamps from Febuary 2006.  There's just one that's different, in ~/.giFT/Ares/nodes, which has a timestamp from yesterday (?!).

Soo... does anybody know if I'm on the right track here?  Does anybody know where to get up-to-date node files?  Google shows me [this suspicious and very recent CVS checkin]("http://sourceforge.net/mailarchive/forum.php?thread_id=31648246&forum_id=8084"), but that's it.

There's also this worrying, recently added tidbit from Wikipedia's page on Ares:

> In addition, a giFT-Ares plug-in for giFT has been released to provide access the Ares network. However, there has been problems with the plugin regarding certain issues like connecting to the network.

Does the solution in this thread still work at all, or are we doomed?  Can anybody help?  Just in case, does anybody know any other solutions for getting Ares on Ubuntu?

F2

PS: Gnutella isn't working for me either, but I haven't had the chance to muck around with it yet.  I'll try to post details when I do.

---

### Post by gollybegully on 2007-02-19
Im having the same problem I posted on the other gift thread as well.  Can only connect to openFT.

---

### Post by myname on 2007-02-21
I'll throw my 2 cents in here too, I too can only connect to OpenFT with Edgy.  On Dapper, all worked fine.  I have all the correct ports open, and am about to put the machine on a DMZ to see if that will help.

Does anyone have a solution?

--Kevin

---

### Post by Soapbar on 2007-02-22
I feel so stupid at the moment. I tried out Ubuntu a couple of days ago and managed to get apollon connected to the ares network. Problem was when I decided that I liked Ubuntu and was going to ditch windows when I formatted my drive I figured I would just get back online and search the solution again. 

:( I'm having difficulty finding the solution again. However (yes there is good news coming) the issue with ares was that the node list was very out of date and I needed to download a updated version of the node list and replace it.

The file you need to replace is called nodes and resides in the /home/username/.gift/ares/

I hope that by posting this that if other people start looking for this updated nodes file we will all resolve this issue quicker.

---

### Post by Soapbar on 2007-02-22
:guitar: Happy days folks I found the updated nodes list :)


download the first nodes file from here [http://update.kceasy.com/update/ares/](http://update.kceasy.com/update/ares/)

and use that file to overwrite the preexisting nodes file in /home/username/.gift/ares

Wooohoooo

Also dont worry that it was only 2 people with 2 gigs are connected its a known issue and doesnt mean your not connected to the network.

---

### Post by myname on 2007-02-22
Sweetness... I will try this when I get home.

Any luck/ideas on getting Gnutella to work?

--Kevin

---

### Post by fang2415 on 2007-02-24
> **Soapbar said:**
> :guitar: Happy days folks I found the updated nodes list :)


download the first nodes file from here [http://update.kceasy.com/update/ares/](http://update.kceasy.com/update/ares/)

and use that file to overwrite the preexisting nodes file in /home/username/.gift/ares


Rad.  Interestingly, Ares did eventually connect for me with the old nodes file, but it took about a week.  I did replace it with the new nodes file just in case though (not sure if it really matters at this point, but hey).

Time to have a crack at gnutella...

---

### Post by Blario on 2007-02-26
Just to add my two cents.... I followed the instructions as originally posted, and the only network that connected for me was FastTrack.  After a few hours, I tried the new ares node list file, and am now waiting for any of the four to connect (its been 10 min. so far...)

The say way that the problem regarding Ares was found, is there a log file that we can check for information about openFT, FastTrack, and GNUtella?

::returns to looking for a good light-weight linux BT client::

---

### Post by gollybegully on 2007-02-26
> **Soapbar said:**
> :guitar: Happy days folks I found the updated nodes list :)


download the first nodes file from here [http://update.kceasy.com/update/ares/](http://update.kceasy.com/update/ares/)

and use that file to overwrite the preexisting nodes file in /home/username/.gift/ares

Wooohoooo

Also dont worry that it was only 2 people with 2 gigs are connected its a known issue and doesnt mean your not connected to the network.

You rule.

---

### Post by Blario on 2007-02-27
> **gollybegully said:**
> You rule.

Did you see if it worked yet?  Mine hasn't connected still.

---

### Post by DigiNeT on 2007-02-28
Damm it was so hard to set it up apollo, but look...

:popcorn: :popcorn:

---

### Post by DigiNeT on 2007-02-28
> **DigiNeT said:**
> Damm it was so hard to set it up apollo, but look...

:popcorn: :popcorn:

:( :( Only Fastrack online

---

### Post by gollybegully on 2007-03-01
> **Blario said:**
> Did you see if it worked yet?  Mine hasn't connected still.

Yea mine worked.  It connects every time.  Now I got openft and ares but for some reason I get really slow download speeds.  Too much hassle with this gift thing.

---

### Post by bodhi.zazen on 2007-03-02
Nice How-to

This thread has been added to the UDSF wiki.

[Appollon_P2P](http://doc.gwos.org/index.php/Appollon_P2P)

---

### Post by fang2415 on 2007-03-03
Okay, looks like I've got Gnutella working as well.

Open up ~/.giFT/Gnutella/gwebcaches in a text editor and paste any url with a score of 100 from the list at [http://gcachescan.jonatkins.com/](http://gcachescan.jonatkins.com/) into the end of the file.  (To understand what this means, look at [http://wiki.shareaza.com/static/G2ConnectingGuide](http://wiki.shareaza.com/static/G2ConnectingGuide).)  Save the file, restart the giftd daemon, and you should be good to go.

I figured this out after looking at the output of cat .giFT/giftd.log|grep Gnutella and noticing this sort of thing repeated every ten seconds:

```
[14:57:05] Gnutella: gt_web_cache.c:737(get_random_cache): couldn't find random cache
[14:57:05] Gnutella: gt_web_cache.c:797(access_gwebcaches): error looking up cache
[14:57:05] Gnutella: Retrying to connect to nodes...
[14:57:15] Gnutella: try_some_nodes() returned 0. node list len=0
[14:57:15] Gnutella: No hosts to try. Looking in gwebcaches...
[14:57:15] *** GIFT-WARNING: Gnutella: skipping webcache http://ophlh8ohnjhxfvnnkoalokd8vxc.xolox.nl/gwebcache/default.asp, in bad gwebcaches
[14:57:15] *** GIFT-WARNING: Gnutella: skipping webcache http://blogblogsoupdocwindowgluenewsuo.xolox.nl/gwebcache/default.asp, in bad gwebcaches
...

```

So I Googled for "gwebcaches" and got lucky.  Hopefully this will sort out anybody out there with a similar problem.

Gnutella is now working for me so much faster than Ares that I'm actually wondering if there is still something wrong with my Ares setup.  Does anybody know if giFT is just really slow with Ares or whether it's just that the network is lamer than I thought it was?

F2

---

### Post by Blario on 2007-03-03
> **gollybegully said:**
> Yea mine worked.  It connects every time.  Now I got openft and ares but for some reason I get really slow download speeds.  Too much hassle with this gift thing.

That's crazy... We're all using the same configuration and the only one that connects for me is FastTrack; nothing else.  Def don't have the two that you have.

---

### Post by Blario on 2007-03-03
> **fang2415 said:**
> Okay, looks like I've got Gnutella working as well.

Open up ~/.giFT/Gnutella/gwebcaches in a text editor and paste any url with a score of 100 from the list at [http://gcachescan.jonatkins.com/](http://gcachescan.jonatkins.com/) into the end of the file.  (To understand what this means, look at [http://wiki.shareaza.com/static/G2ConnectingGuide](http://wiki.shareaza.com/static/G2ConnectingGuide).)  Save the file, restart the giftd daemon, and you should be good to go.

I figured this out after looking at the output of cat .giFT/giftd.log|grep Gnutella and noticing this sort of thing repeated every ten seconds:

```
[14:57:05] Gnutella: gt_web_cache.c:737(get_random_cache): couldn't find random cache
[14:57:05] Gnutella: gt_web_cache.c:797(access_gwebcaches): error looking up cache
[14:57:05] Gnutella: Retrying to connect to nodes...
[14:57:15] Gnutella: try_some_nodes() returned 0. node list len=0
[14:57:15] Gnutella: No hosts to try. Looking in gwebcaches...
[14:57:15] *** GIFT-WARNING: Gnutella: skipping webcache http://ophlh8ohnjhxfvnnkoalokd8vxc.xolox.nl/gwebcache/default.asp, in bad gwebcaches
[14:57:15] *** GIFT-WARNING: Gnutella: skipping webcache http://blogblogsoupdocwindowgluenewsuo.xolox.nl/gwebcache/default.asp, in bad gwebcaches
...

```

So I Googled for "gwebcaches" and got lucky.  Hopefully this will sort out anybody out there with a similar problem.

Gnutella is now working for me so much faster than Ares that I'm actually wondering if there is still something wrong with my Ares setup.  Does anybody know if giFT is just really slow with Ares or whether it's just that the network is lamer than I thought it was?

F2

I followed these instructions and GNUtella connects INSTANTLY now.  Hotness!

---

### Post by fang2415 on 2007-03-03
> **Blario said:**
> That's crazy... We're all using the same configuration and the only one that connects for me is FastTrack; nothing else.  Def don't have the two that you have.

If you're still having trouble with the Ares plugin, you might want to try stopping the daemon (or disconnecting the Ares plugin), then replacing the nodes file, and then restarting the daemon/plugin, *in that order*.

When I was mucking around with Gnutella, I noticed that somehow my Ares nodes file had been cleared (nothing there but the header row) and that if I restored it and then killed the daemon, it would clear it again.  Don't know why, but it seems like the plugin might be a bit finicky about the daemon being restarted.  Might be worth a try if it's still not working.

Like I say though, I am getting way better results frum Gnutella, so maybe the Ares plugin or network just isn't quite up to snuff?...

---

### Post by Miguellint on 2007-03-04
Thanks Soapbar for the Ares nodes link and thanks fang2415 for sorting out gnutella.

Both fire up straight away now.

Now all I need is some clever type to get FastTrack working. A link to an up to date FastTrack nodes file maybe?

Cheers
Miguel

---

### Post by Rizado on 2007-03-04
> **Blario said:**
> That's crazy... We're all using the same configuration and the only one that connects for me is FastTrack; nothing else.  Def don't have the two that you have.How did you get FastTrack to work? Only OpenFt is working for me :confused: 

Have you opened any ports or done anything at all?

```
[14:49:54] *** GIFT-WARNING: FastTrack: Unsupported encryption: 0x5AE9F567
[14:50:08] *** GIFT-WARNING: FastTrack: Unsupported encryption: 0x19E99465
[14:50:43] *** GIFT-WARNING: FastTrack: Unsupported encryption: 0x4114580
[14:51:12] *** GIFT-WARNING: FastTrack: Unsupported encryption: 0x50BF20B7
[14:51:24] *** GIFT-WARNING: FastTrack: Unsupported encryption: 0xF829419A
```
Fasttrack not supported anymore?

---

### Post by Blario on 2007-03-04
> **Rizado said:**
> How did you get FastTrack to work? Only OpenFt is working for me :confused: 

Have you opened any ports or done anything at all?

```
[14:49:54] *** GIFT-WARNING: FastTrack: Unsupported encryption: 0x5AE9F567
[14:50:08] *** GIFT-WARNING: FastTrack: Unsupported encryption: 0x19E99465
[14:50:43] *** GIFT-WARNING: FastTrack: Unsupported encryption: 0x4114580
[14:51:12] *** GIFT-WARNING: FastTrack: Unsupported encryption: 0x50BF20B7
[14:51:24] *** GIFT-WARNING: FastTrack: Unsupported encryption: 0xF829419A
```
Fasttrack not supported anymore?

I didn't do anything other than what the howto directed to do.  FastTrack always connects for me, but usually after its open about a few hours.  The only room I see for differences is how we all decided to fill out our configuration files.  My FastTrack.conf is attached.

Like I said, its strange, cause openFT def doesn't work for me, nor Ares (gnutella does now thanks to the previous 4 posts or so :D ).

---

### Post by Rizado on 2007-03-04
```
[15:32:53] *** GIFT-WARNING: FastTrack: Unsupported encryption: 0xDA5C87C7
[15:34:08] *** GIFT-WARNING: FastTrack: Unsupported encryption: 0xC4B3E741
[15:34:20] *** GIFT-WARNING: FastTrack: Unsupported encryption: 0x497A2344
```

```
[15:25:41] FastTrack: fst_session.c:385(session_decrypt_packet): received insufficient data for calculating key, got 6 bytes, waiting for more...
[15:29:45] FastTrack: fst_session.c:385(session_decrypt_packet): received insufficient data for calculating key, got 7 bytes, waiting for more...
[15:30:26] FastTrack: fst_session.c:385(session_decrypt_packet): received insufficient data for calculating key, got 7 bytes, waiting for more...
[15:38:52] FastTrack: fst_session.c:446(session_decrypt_packet): remote network name is "KaZaA"
```After that remote network name is "KaZaA" i no longer get any decrypt errors. But it doesn't connect either. OpenFT disconnects all the time but Gnutella started working. Ares shows 2 users and 2gb but that is incorrect and it's working fine.

To get Gnutella working I had to empty bad_gwebcaches because every server was added there. Might be why it didn't work. Also I got new nodes. 
```
wget http://apollon.sf.net/gnutella/nodes -O ~/.giFT/Gnutella/nodes
```

---

### Post by Blario on 2007-03-04
> **Rizado said:**
> ```
[15:32:53] *** GIFT-WARNING: FastTrack: Unsupported encryption: 0xDA5C87C7
[15:34:08] *** GIFT-WARNING: FastTrack: Unsupported encryption: 0xC4B3E741
[15:34:20] *** GIFT-WARNING: FastTrack: Unsupported encryption: 0x497A2344
```

```
[15:25:41] FastTrack: fst_session.c:385(session_decrypt_packet): received insufficient data for calculating key, got 6 bytes, waiting for more...
[15:29:45] FastTrack: fst_session.c:385(session_decrypt_packet): received insufficient data for calculating key, got 7 bytes, waiting for more...
[15:30:26] FastTrack: fst_session.c:385(session_decrypt_packet): received insufficient data for calculating key, got 7 bytes, waiting for more...
[15:38:52] FastTrack: fst_session.c:446(session_decrypt_packet): remote network name is "KaZaA"
```After that remote network name is "KaZaA" i no longer get any decrypt errors. But it doesn't connect either. OpenFT disconnects all the time but Gnutella started working. Ares shows 2 users and 2gb but that is incorrect and it's working fine.

To get Gnutella working I had to empty bad_gwebcaches because every server was added there. Might be why it didn't work. Also I got new nodes. 
```
wget http://apollon.sf.net/gnutella/nodes -O ~/.giFT/Gnutella/nodes
```

Do you have encryption turned on for FastTrack somewhere?  I'd check my .conf files b/c:
$ cat giftd.log|grep encryption
returns nothing for me.

---

### Post by Rizado on 2007-03-04
> **Blario said:**
> Do you have encryption turned on for FastTrack somewhere?  I'd check my .conf files b/c:
$ cat giftd.log|grep encryption
returns nothing for me.Nope nothing like that, try decrypt to. But I have this one little theory...

The fasttrack protocol is encrypted (It is according to wikipedia) and some people decided to reverse engineer it. They managed to crack the encryption between clients and nodes but not between nodes, this much is certain.

Now maybe what the fasttrack plugin have to do is through bits and pieces it gets figure out something. And this is why it takes so much time. But when you've done it you wont have to do it again. Or maybe you do have to do it everytime you restart I don't know, i'll just leave it running for a while and see what will happen.

Maybe OpenFT isn't working because you haven't forwarded a port?

EDIT: Just tried, kazaa lite resurrection doesn't work either :/

Yay got everything working! Got it done by geting new nodes and stuff, will explain more later, I got to study right now.

---

### Post by Rizado on 2007-03-05
So how did I do? Well the nodes list that come with giFT is really outdated, probably none of them was working and that is why it didn't work. I then installed kazaa lite resurrection in XP in vmware but I had the same problem. After some searching came across [[color="RoyalBlue"]_snode._[/color]](http://snode.blogspot.com/) A application that updates your kazaa nodes list. Now it worked! Next problem was that it is somehow encrypted och something, it's not plain IPs. With kazaa a application called KaZuperNodes which you can use to get ip's of the nodes. With this I extracted it to a list and changed it alittle bit to be compatible with gift. I replaced nodes with this list and bam, within five minutes I was able to access 1.61 million GB kazaa material :)

The list I ended up with was:
```
24.205.202.148 1214 0 0 0 0 0 0
74.139.219.247 3739 0 0 0 0 0 0
72.45.30.215 1214 0 0 0 0 0 0
216.218.219.125 21795 0 0 0 0 0 0
66.214.68.221 1200 0 0 0 0 0 0
76.197.194.198 3747 0 0 0 0 0 0
216.218.184.162 50331 0 0 0 0 0 0
24.211.116.204 3312 0 0 0 0 0 0
216.218.219.121 25741 0 0 0 0 0 0
67.18.213.226 2594 0 0 0 0 0 0
64.71.178.133 2710 0 0 0 0 0 0
216.66.2.121 57359 0 0 0 0 0 0
70.77.47.85 32656 0 0 0 0 0 0
216.218.196.234 24838 0 0 0 0 0 0
216.66.31.17 59478 0 0 0 0 0 0
69.232.48.149 1576 0 0 0 0 0 0
69.31.223.67 1214 0 0 0 0 0 0
84.205.150.118 3387 0 0 0 0 0 0
216.218.210.21 9888 0 0 0 0 0 0
70.121.211.57 32656 0 0 0 0 0 0
24.33.232.91 1542 0 0 0 0 0 0
66.220.12.75 58279 0 0 0 0 0 0
65.19.131.38 22439 0 0 0 0 0 0
66.220.2.141 3673 0 0 0 0 0 0
62.163.122.120 3193 0 0 0 0 0 0
216.218.213.45 50730 0 0 0 0 0 0
24.187.45.143 2737 0 0 0 0 0 0
65.28.244.149 1884 0 0 0 0 0 0
66.220.12.94 10053 0 0 0 0 0 0
65.191.188.180 1479 0 0 0 0 0 0
216.66.23.42 56715 0 0 0 0 0 0
216.66.23.48 1871 0 0 0 0 0 0
75.74.124.100 2878 0 0 0 0 0 0
216.218.195.222 25449 0 0 0 0 0 0
70.126.227.31 3519 0 0 0 0 0 0
142.167.215.105 2686 0 0 0 0 0 0
216.66.2.120 37354 0 0 0 0 0 0
66.160.128.7 10863 0 0 0 0 0 0
66.220.2.134 45710 0 0 0 0 0 0
216.218.207.196 56392 0 0 0 0 0 0
66.192.126.188 3304 0 0 0 0 0 0
64.71.178.156 49637 0 0 0 0 0 0
66.192.126.178 2816 0 0 0 0 0 0
72.209.134.133 2857 0 0 0 0 0 0
68.106.133.136 3827 0 0 0 0 0 0
216.218.207.185 28796 0 0 0 0 0 0
129.64.171.86 2922 0 0 0 0 0 0
72.224.185.115 2638 0 0 0 0 0 0
71.196.247.153 1461 0 0 0 0 0 0
209.51.184.52 26539 0 0 0 0 0 0
75.65.35.98 2926 0 0 0 0 0 0
74.136.8.225 1214 0 0 0 0 0 0
24.253.208.25 3206 0 0 0 0 0 0
209.51.184.46 4220 0 0 0 0 0 0
216.218.193.205 45845 0 0 0 0 0 0
65.173.138.89 2040 0 0 0 0 0 0
64.62.206.189 45199 0 0 0 0 0 0
216.218.195.211 50986 0 0 0 0 0 0
68.225.64.247 3887 0 0 0 0 0 0
216.218.207.208 6330 0 0 0 0 0 0
216.66.31.10 32008 0 0 0 0 0 0
216.218.193.214 55699 0 0 0 0 0 0
66.160.128.6 41538 0 0 0 0 0 0
84.108.162.155 3535 0 0 0 0 0 0
66.160.133.137 25674 0 0 0 0 0 0
75.44.38.111 3555 0 0 0 0 0 0
68.37.88.254 1183 0 0 0 0 0 0
70.39.37.229 1517 0 0 0 0 0 0
74.134.102.79 1440 0 0 0 0 0 0
68.175.82.209 1419 0 0 0 0 0 0
64.71.178.130 13726 0 0 0 0 0 0
216.66.3.120 33598 0 0 0 0 0 0
24.91.115.208 1773 0 0 0 0 0 0
64.80.195.152 3232 0 0 0 0 0 0
216.66.3.109 52153 0 0 0 0 0 0
84.108.4.127 3535 0 0 0 0 0 0
66.131.112.147 2615 0 0 0 0 0 0
216.218.207.183 26538 0 0 0 0 0 0
74.192.56.163 2881 0 0 0 0 0 0
24.252.24.168 1808 0 0 0 0 0 0
24.1.214.62 3928 0 0 0 0 0 0
85.255.56.82 1214 0 0 0 0 0 0
68.43.69.46 2136 0 0 0 0 0 0
72.193.226.46 3463 0 0 0 0 0 0
216.218.196.60 63978 0 0 0 0 0 0
70.115.181.247 1214 0 0 0 0 0 0
72.224.164.192 2913 0 0 0 0 0 0
62.178.237.116 3992 0 0 0 0 0 0
216.218.220.254 10330 0 0 0 0 0 0
216.218.168.60 7977 0 0 0 0 0 0
80.237.211.49 1112 0 0 0 0 0 0
24.15.98.120 32656 0 0 0 0 0 0
65.19.131.55 57041 0 0 0 0 0 0
76.20.136.3 1549 0 0 0 0 0 0
24.167.53.70 1461 0 0 0 0 0 0
70.114.195.189 3333 0 0 0 0 0 0
75.108.100.201 3544 0 0 0 0 0 0
24.59.96.158 1924 0 0 0 0 0 0
66.220.12.82 57358 0 0 0 0 0 0
83.82.254.157 3627 0 0 0 0 0 0
71.202.52.63 3893 0 0 0 0 0 0
69.138.189.200 2312 0 0 0 0 0 0
216.218.133.101 56434 0 0 0 0 0 0
76.171.134.244 1214 0 0 0 0 0 0
216.66.3.106 53907 0 0 0 0 0 0
216.218.184.164 52248 0 0 0 0 0 0
68.107.218.195 1055 0 0 0 0 0 0
24.196.192.217 2927 0 0 0 0 0 0
84.197.64.138 2081 0 0 0 0 0 0
66.220.12.92 57907 0 0 0 0 0 0
216.218.219.126 9912 0 0 0 0 0 0
24.181.75.4 2375 0 0 0 0 0 0
216.218.220.231 60140 0 0 0 0 0 0
65.19.131.45 20173 0 0 0 0 0 0
24.59.250.191 1214 0 0 0 0 0 0
24.252.106.162 2439 0 0 0 0 0 0
216.218.196.48 54189 0 0 0 0 0 0
64.71.178.155 29574 0 0 0 0 0 0
216.232.224.210 3571 0 0 0 0 0 0
66.56.53.146 1239 0 0 0 0 0 0
216.66.23.37 33052 0 0 0 0 0 0
216.66.2.115 29898 0 0 0 0 0 0
216.66.23.34 57552 0 0 0 0 0 0
216.218.220.237 50364 0 0 0 0 0 0
216.66.31.7 49775 0 0 0 0 0 0
65.33.74.36 2649 0 0 0 0 0 0
216.66.3.108 31906 0 0 0 0 0 0
68.205.143.81 4185 0 0 0 0 0 0
87.244.136.69 2036 0 0 0 0 0 0
216.218.219.107 40211 0 0 0 0 0 0
209.51.186.214 27735 0 0 0 0 0 0
216.218.220.235 50540 0 0 0 0 0 0
69.249.240.140 3328 0 0 0 0 0 0
209.51.184.45 59444 0 0 0 0 0 0
200.104.28.58 32656 0 0 0 0 0 0
62.30.84.242 1214 0 0 0 0 0 0
24.174.236.42 1327 0 0 0 0 0 0
69.86.146.233 2961 0 0 0 0 0 0
216.66.2.98 61537 0 0 0 0 0 0
76.173.253.165 1214 0 0 0 0 0 0
72.36.231.170 2950 0 0 0 0 0 0
68.179.136.212 32656 0 0 0 0 0 0
84.108.116.215 2402 0 0 0 0 0 0
24.232.154.253 1214 0 0 0 0 0 0
216.218.193.220 50632 0 0 0 0 0 0
24.231.241.82 32656 0 0 0 0 0 0
68.83.234.78 3577 0 0 0 0 0 0
24.235.128.9 2609 0 0 0 0 0 0
216.218.207.179 62950 0 0 0 0 0 0
24.255.187.190 3053 0 0 0 0 0 0
216.66.32.109 64645 0 0 0 0 0 0
74.192.211.150 3993 0 0 0 0 0 0
69.137.160.187 3497 0 0 0 0 0 0
216.218.196.230 53973 0 0 0 0 0 0
77.98.14.118 1214 0 0 0 0 0 0
212.120.87.248 1957 0 0 0 0 0 0
75.128.203.67 1181 0 0 0 0 0 0
24.145.160.61 3623 0 0 0 0 0 0
216.66.31.28 41920 0 0 0 0 0 0
216.218.207.165 64486 0 0 0 0 0 0
82.232.81.244 3311 0 0 0 0 0 0
68.104.27.19 3110 0 0 0 0 0 0
72.128.10.189 2828 0 0 0 0 0 0
66.160.128.2 48486 0 0 0 0 0 0
74.33.171.205 1214 0 0 0 0 0 0
72.186.246.9 1591 0 0 0 0 0 0
74.67.95.91 2569 0 0 0 0 0 0
71.196.117.63 3954 0 0 0 0 0 0
68.204.193.91 1523 0 0 0 0 0 0
216.218.133.103 23710 0 0 0 0 0 0
82.32.140.214 2580 0 0 0 0 0 0
209.51.184.49 45355 0 0 0 0 0 0
24.158.185.199 1940 0 0 0 0 0 0
24.160.68.18 3852 0 0 0 0 0 0
209.51.189.174 1354 0 0 0 0 0 0
66.220.12.83 19307 0 0 0 0 0 0
66.220.2.158 64170 0 0 0 0 0 0
75.21.228.25 2428 0 0 0 0 0 0
75.85.216.186 2868 0 0 0 0 0 0
216.218.184.190 1756 0 0 0 0 0 0
216.66.31.12 48155 0 0 0 0 0 0
216.218.219.124 52904 0 0 0 0 0 0
65.19.131.52 30541 0 0 0 0 0 0
198.53.209.184 1536 0 0 0 0 0 0
209.51.189.166 29118 0 0 0 0 0 0
67.18.30.178 1931 0 0 0 0 0 0
216.218.163.106 26375 0 0 0 0 0 0
84.52.160.192 1214 0 0 0 0 0 0
216.218.213.47 4027 0 0 0 0 0 0
216.218.133.102 22940 0 0 0 0 0 0
216.218.210.24 37636 0 0 0 0 0 0
66.220.12.67 32611 0 0 0 0 0 0
68.103.122.195 1214 0 0 0 0 0 0
62.163.80.90 1214 0 0 0 0 0 0
71.17.79.34 1214 0 0 0 0 0 0
24.151.15.224 2380 0 0 0 0 0 0
216.218.210.16 22839 0 0 0 0 0 0
209.51.189.176 49716 0 0 0 0 0 0
83.85.2.166 3629 0 0 0 0 0 0
76.160.0.124 1087 0 0 0 0 0 0
```

Replace ~/.giFT/FastTrack/nodes with this and hopefully everything will be fine. Also I had to disable the NAT forwarding setting in fasttrack config even though I'm behind a router. It doesn't work, maybe it is the way I forward (dnat?) I don't know.

I'm not sure it's allowed to post this. If it's not please tell me and help me find a place to host it.

I can upload the Ares nodes list aswell, but it's to large to append here. Help me with hosting.

To get gnutella working I did ```
wget http://apollon.sf.net/gnutella/nodes -O ~/.giFT/Gnutella/nodes
```
This will replace Gnutella nodes with something newer. I also followed the instructions earlier as well as emptying ~/.giFT/Gnutella/bad_gwebcaches as it denyed all webcaches I had.

---

### Post by Rizado on 2007-03-05
Doublepost.

---

### Post by Blario on 2007-03-05
> **Rizado said:**
> So how did I do? Well the nodes list that come with giFT is really outdated, probably none of them was working and that is why it didn't work. I then installed kazaa lite resurrection in XP in vmware but I had the same problem. After some searching came across [[color="RoyalBlue"]_snode._[/color]](http://snode.blogspot.com/) A application that updates your kazaa nodes list. Now it worked! Next problem was that it is somehow encrypted och something, it's not plain IPs. With kazaa a application called KaZuperNodes which you can use to get ip's of the nodes. With this I extracted it to a list and changed it alittle bit to be compatible with gift. I replaced nodes with this list and bam, within five minutes I was able to access 1.61 million GB kazaa material :)

The list I ended up with was:
```
24.205.202.148 1214 0 0 0 0 0 0
74.139.219.247 3739 0 0 0 0 0 0
72.45.30.215 1214 0 0 0 0 0 0
216.218.219.125 21795 0 0 0 0 0 0
66.214.68.221 1200 0 0 0 0 0 0
76.197.194.198 3747 0 0 0 0 0 0
216.218.184.162 50331 0 0 0 0 0 0
24.211.116.204 3312 0 0 0 0 0 0
216.218.219.121 25741 0 0 0 0 0 0
67.18.213.226 2594 0 0 0 0 0 0
64.71.178.133 2710 0 0 0 0 0 0
216.66.2.121 57359 0 0 0 0 0 0
70.77.47.85 32656 0 0 0 0 0 0
216.218.196.234 24838 0 0 0 0 0 0
216.66.31.17 59478 0 0 0 0 0 0
69.232.48.149 1576 0 0 0 0 0 0
69.31.223.67 1214 0 0 0 0 0 0
84.205.150.118 3387 0 0 0 0 0 0
216.218.210.21 9888 0 0 0 0 0 0
70.121.211.57 32656 0 0 0 0 0 0
24.33.232.91 1542 0 0 0 0 0 0
66.220.12.75 58279 0 0 0 0 0 0
65.19.131.38 22439 0 0 0 0 0 0
66.220.2.141 3673 0 0 0 0 0 0
62.163.122.120 3193 0 0 0 0 0 0
216.218.213.45 50730 0 0 0 0 0 0
24.187.45.143 2737 0 0 0 0 0 0
65.28.244.149 1884 0 0 0 0 0 0
66.220.12.94 10053 0 0 0 0 0 0
65.191.188.180 1479 0 0 0 0 0 0
216.66.23.42 56715 0 0 0 0 0 0
216.66.23.48 1871 0 0 0 0 0 0
75.74.124.100 2878 0 0 0 0 0 0
216.218.195.222 25449 0 0 0 0 0 0
70.126.227.31 3519 0 0 0 0 0 0
142.167.215.105 2686 0 0 0 0 0 0
216.66.2.120 37354 0 0 0 0 0 0
66.160.128.7 10863 0 0 0 0 0 0
66.220.2.134 45710 0 0 0 0 0 0
216.218.207.196 56392 0 0 0 0 0 0
66.192.126.188 3304 0 0 0 0 0 0
64.71.178.156 49637 0 0 0 0 0 0
66.192.126.178 2816 0 0 0 0 0 0
72.209.134.133 2857 0 0 0 0 0 0
68.106.133.136 3827 0 0 0 0 0 0
216.218.207.185 28796 0 0 0 0 0 0
129.64.171.86 2922 0 0 0 0 0 0
72.224.185.115 2638 0 0 0 0 0 0
71.196.247.153 1461 0 0 0 0 0 0
209.51.184.52 26539 0 0 0 0 0 0
75.65.35.98 2926 0 0 0 0 0 0
74.136.8.225 1214 0 0 0 0 0 0
24.253.208.25 3206 0 0 0 0 0 0
209.51.184.46 4220 0 0 0 0 0 0
216.218.193.205 45845 0 0 0 0 0 0
65.173.138.89 2040 0 0 0 0 0 0
64.62.206.189 45199 0 0 0 0 0 0
216.218.195.211 50986 0 0 0 0 0 0
68.225.64.247 3887 0 0 0 0 0 0
216.218.207.208 6330 0 0 0 0 0 0
216.66.31.10 32008 0 0 0 0 0 0
216.218.193.214 55699 0 0 0 0 0 0
66.160.128.6 41538 0 0 0 0 0 0
84.108.162.155 3535 0 0 0 0 0 0
66.160.133.137 25674 0 0 0 0 0 0
75.44.38.111 3555 0 0 0 0 0 0
68.37.88.254 1183 0 0 0 0 0 0
70.39.37.229 1517 0 0 0 0 0 0
74.134.102.79 1440 0 0 0 0 0 0
68.175.82.209 1419 0 0 0 0 0 0
64.71.178.130 13726 0 0 0 0 0 0
216.66.3.120 33598 0 0 0 0 0 0
24.91.115.208 1773 0 0 0 0 0 0
64.80.195.152 3232 0 0 0 0 0 0
216.66.3.109 52153 0 0 0 0 0 0
84.108.4.127 3535 0 0 0 0 0 0
66.131.112.147 2615 0 0 0 0 0 0
216.218.207.183 26538 0 0 0 0 0 0
74.192.56.163 2881 0 0 0 0 0 0
24.252.24.168 1808 0 0 0 0 0 0
24.1.214.62 3928 0 0 0 0 0 0
85.255.56.82 1214 0 0 0 0 0 0
68.43.69.46 2136 0 0 0 0 0 0
72.193.226.46 3463 0 0 0 0 0 0
216.218.196.60 63978 0 0 0 0 0 0
70.115.181.247 1214 0 0 0 0 0 0
72.224.164.192 2913 0 0 0 0 0 0
62.178.237.116 3992 0 0 0 0 0 0
216.218.220.254 10330 0 0 0 0 0 0
216.218.168.60 7977 0 0 0 0 0 0
80.237.211.49 1112 0 0 0 0 0 0
24.15.98.120 32656 0 0 0 0 0 0
65.19.131.55 57041 0 0 0 0 0 0
76.20.136.3 1549 0 0 0 0 0 0
24.167.53.70 1461 0 0 0 0 0 0
70.114.195.189 3333 0 0 0 0 0 0
75.108.100.201 3544 0 0 0 0 0 0
24.59.96.158 1924 0 0 0 0 0 0
66.220.12.82 57358 0 0 0 0 0 0
83.82.254.157 3627 0 0 0 0 0 0
71.202.52.63 3893 0 0 0 0 0 0
69.138.189.200 2312 0 0 0 0 0 0
216.218.133.101 56434 0 0 0 0 0 0
76.171.134.244 1214 0 0 0 0 0 0
216.66.3.106 53907 0 0 0 0 0 0
216.218.184.164 52248 0 0 0 0 0 0
68.107.218.195 1055 0 0 0 0 0 0
24.196.192.217 2927 0 0 0 0 0 0
84.197.64.138 2081 0 0 0 0 0 0
66.220.12.92 57907 0 0 0 0 0 0
216.218.219.126 9912 0 0 0 0 0 0
24.181.75.4 2375 0 0 0 0 0 0
216.218.220.231 60140 0 0 0 0 0 0
65.19.131.45 20173 0 0 0 0 0 0
24.59.250.191 1214 0 0 0 0 0 0
24.252.106.162 2439 0 0 0 0 0 0
216.218.196.48 54189 0 0 0 0 0 0
64.71.178.155 29574 0 0 0 0 0 0
216.232.224.210 3571 0 0 0 0 0 0
66.56.53.146 1239 0 0 0 0 0 0
216.66.23.37 33052 0 0 0 0 0 0
216.66.2.115 29898 0 0 0 0 0 0
216.66.23.34 57552 0 0 0 0 0 0
216.218.220.237 50364 0 0 0 0 0 0
216.66.31.7 49775 0 0 0 0 0 0
65.33.74.36 2649 0 0 0 0 0 0
216.66.3.108 31906 0 0 0 0 0 0
68.205.143.81 4185 0 0 0 0 0 0
87.244.136.69 2036 0 0 0 0 0 0
216.218.219.107 40211 0 0 0 0 0 0
209.51.186.214 27735 0 0 0 0 0 0
216.218.220.235 50540 0 0 0 0 0 0
69.249.240.140 3328 0 0 0 0 0 0
209.51.184.45 59444 0 0 0 0 0 0
200.104.28.58 32656 0 0 0 0 0 0
62.30.84.242 1214 0 0 0 0 0 0
24.174.236.42 1327 0 0 0 0 0 0
69.86.146.233 2961 0 0 0 0 0 0
216.66.2.98 61537 0 0 0 0 0 0
76.173.253.165 1214 0 0 0 0 0 0
72.36.231.170 2950 0 0 0 0 0 0
68.179.136.212 32656 0 0 0 0 0 0
84.108.116.215 2402 0 0 0 0 0 0
24.232.154.253 1214 0 0 0 0 0 0
216.218.193.220 50632 0 0 0 0 0 0
24.231.241.82 32656 0 0 0 0 0 0
68.83.234.78 3577 0 0 0 0 0 0
24.235.128.9 2609 0 0 0 0 0 0
216.218.207.179 62950 0 0 0 0 0 0
24.255.187.190 3053 0 0 0 0 0 0
216.66.32.109 64645 0 0 0 0 0 0
74.192.211.150 3993 0 0 0 0 0 0
69.137.160.187 3497 0 0 0 0 0 0
216.218.196.230 53973 0 0 0 0 0 0
77.98.14.118 1214 0 0 0 0 0 0
212.120.87.248 1957 0 0 0 0 0 0
75.128.203.67 1181 0 0 0 0 0 0
24.145.160.61 3623 0 0 0 0 0 0
216.66.31.28 41920 0 0 0 0 0 0
216.218.207.165 64486 0 0 0 0 0 0
82.232.81.244 3311 0 0 0 0 0 0
68.104.27.19 3110 0 0 0 0 0 0
72.128.10.189 2828 0 0 0 0 0 0
66.160.128.2 48486 0 0 0 0 0 0
74.33.171.205 1214 0 0 0 0 0 0
72.186.246.9 1591 0 0 0 0 0 0
74.67.95.91 2569 0 0 0 0 0 0
71.196.117.63 3954 0 0 0 0 0 0
68.204.193.91 1523 0 0 0 0 0 0
216.218.133.103 23710 0 0 0 0 0 0
82.32.140.214 2580 0 0 0 0 0 0
209.51.184.49 45355 0 0 0 0 0 0
24.158.185.199 1940 0 0 0 0 0 0
24.160.68.18 3852 0 0 0 0 0 0
209.51.189.174 1354 0 0 0 0 0 0
66.220.12.83 19307 0 0 0 0 0 0
66.220.2.158 64170 0 0 0 0 0 0
75.21.228.25 2428 0 0 0 0 0 0
75.85.216.186 2868 0 0 0 0 0 0
216.218.184.190 1756 0 0 0 0 0 0
216.66.31.12 48155 0 0 0 0 0 0
216.218.219.124 52904 0 0 0 0 0 0
65.19.131.52 30541 0 0 0 0 0 0
198.53.209.184 1536 0 0 0 0 0 0
209.51.189.166 29118 0 0 0 0 0 0
67.18.30.178 1931 0 0 0 0 0 0
216.218.163.106 26375 0 0 0 0 0 0
84.52.160.192 1214 0 0 0 0 0 0
216.218.213.47 4027 0 0 0 0 0 0
216.218.133.102 22940 0 0 0 0 0 0
216.218.210.24 37636 0 0 0 0 0 0
66.220.12.67 32611 0 0 0 0 0 0
68.103.122.195 1214 0 0 0 0 0 0
62.163.80.90 1214 0 0 0 0 0 0
71.17.79.34 1214 0 0 0 0 0 0
24.151.15.224 2380 0 0 0 0 0 0
216.218.210.16 22839 0 0 0 0 0 0
209.51.189.176 49716 0 0 0 0 0 0
83.85.2.166 3629 0 0 0 0 0 0
76.160.0.124 1087 0 0 0 0 0 0
```

Replace ~/.giFT/FastTrack/nodes with this and hopefully everything will be fine. Also I had to disable the NAT forwarding setting in fasttrack config even though I'm behind a router. It doesn't work, maybe it is the way I forward (dnat?) I don't know.

I'm not sure it's allowed to post this. If it's not please tell me and help me find a place to host it.

:guitar: Let me be the first to applaud Rizado with GREAT PRAISE for all the hard work and diligency that he has put into this.  Who would have thought so much effort could be put into getting one application to work, versus all the other alternatives (perhaps we don't actually have any alternatives).

Don't want to get sappy here, but thanks for the great info!

---

### Post by myname on 2007-05-07
Just installed Apollon by following these directions, updated the Node files for Fasttrack and Ares, and still no go.  Even did the giftd then restarted, no go.

I recently got a DLINK DGL 4300 and opened the following ports, under Advanced/Special Applications and Advanced/Gaming:
1214
2176
3150
3982
59049

Still nothing connects, even let it sit for 15 minutes. nothing.

Any ideas what I need to do to get these to connect?

--Kevin

---

### Post by guysmiley25 on 2007-05-09
I'm also having problems with giFT.

I've been using giFT for along time, first discovered back in my windows days. And was one of the many reasons I moved over.

Never had any problems, but now I've justed upgraded to Feisty and I can not seem to get it to connect. It did manage to connect to OpenFT for a second.

Is there something happening here guys?

---

### Post by guysmiley25 on 2007-05-09
Well I got Gnutella working using [this]("http://ubuntuforums.org/showpost.php?p=2241045&postcount=60") post. Thanks fang2415.

I also tryed updated the nodes file for OpenFT, FastTrack, and Ares from [here]("http://update.kceasy.com/update/"). But it did not work. I remember back when I used KCeasy in windows, there was an option to update the nodes/banlist. Was this just from [http://update.kceasy.com/update/]("http://update.kceasy.com/update/") as well?

If anyone was wondering, you can get an updated copy of the banlist for FastTrack from [here]("http://www2.openmedia.info:8080/p23.html"): [http://www.openmedia.info/downloads/guarding.p2p.zip](http://www.openmedia.info/downloads/guarding.p2p.zip)

You have to unzip it, and rename it. After I had done that, I stopped getting lots of fakes in my search. It's meant to be updated every now and again.

So I was thinking maybe it's about time there was a script, that would go out and update these files for us. I might try start on one, however I need a good source to get the information from.

For Gnutella [http://gcachescan.jonatkins.com/]("http://gcachescan.jonatkins.com/") looks like a winner, but I'm not sure how i could extract the information from the webpage in a script. I'm sure there is a command available.

So to conclude, at the moment I'm only capable to make a script to update the banlist for FastTrack. For the other networks I need some help.

---

### Post by myname on 2007-05-14
After tinkering, and updating the nodes, I got Apollon to connect to Ares one time, and Fasttrack twice.  But since then, and whenever I run Apollon, all the networks just stay at "connecting". 

Do I have to do something special again to get the networks to connect?

--Kevin

---

### Post by guysmiley25 on 2007-05-14
I've had Gnutella and OpenFT up for a few days now! Still can not seem to connect to Ares or Fasttrack.

I'm sure it is just a nodes list thing, and that we need good node files!

Gnutella:
See [fang2415 post]("http://ubuntuforums.org/showpost.php?p=2241045&postcount=60").

Ares/FastTrack/OpenFT:
[http://www.kceasy.com/update/]("http://www.kceasy.com/update/").

---

### Post by pandanuma on 2007-05-14
fangs alot fang2415...
if only i had read thru all the posts weeks ago...
gnutella is now working...now to try your ares solution...

---

### Post by DriftShin on 2007-05-29
Couldn't figure out which ports to open coz during the setup, there were a few mentioned. I took note of the http, Gnutella and TCP but couldn't figure out how to open them using firestarter. Even when i turned it off completely, could only connect to Ares and not getting any traffic whatsoever. Even my searches are not returning anything, even for popular content. If only frostwire didn't use up all my resources when its running!

---

### Post by Mazehero55 on 2007-06-19
I've been having this trouble too but when I installed  giftoxic is says the gift daemon started but failed to connect.

---

### Post by mahasmb on 2007-06-26
Everything is just always "Connecting..." for me.

Would it be better to use Frostwire? (That substitute for Limewire)

---

### Post by Pheodax on 2007-07-01
> **mahasmb said:**
> Everything is just always "Connecting..." for me.

Would it be better to use Frostwire? (That substitute for Limewire)
I got both Frostwire and Apollon working today. Frostwire is way less buddy than Apollon and has a built-in media player. Apollon is working, but the hashing is very slow and buggy, e.g.: once the hashing is done, the program still says I'm sharing 0 files and 0MB. Almost all search results in Apollon are from the Gnutella network, which is the same Frostwire uses. There's no big disadvantage in using only the Gnutella network, IMO. Even when you're connected to all 4 networks, you'll get a weird status, e.g. 2 users connected on the Ares network.

Frostwire pro's: built-in media player, fast downloads, fast connecting to the Gnutella network.
Frostwire con's: only 1 supported network (Gnutella), virusses and SPAM in search results.

Apollon pro's: 4 supported networks, fast downloads.
Apollon con's: slow connecting to networks, buggy interface, virusses and SPAM in search results.

---

### Post by jetpeach on 2007-08-19
does anybody know why apollon's development seemed to just stop in 2005? the program is so close to being awsome, but as pheodax said, it is a bit buggy.

i really prefer it to frostwire, but it is a pain to set up (configuring gift is a pain. speaking of which, gift hasn't been worked on it seems since 2005 either!)

i've even set it up twice before, but just built a new computer and am trying to set it up again and still can't figure out why it's not connecting! i remember it took me a long time before as well... stupidstupid 

speaking of which, if anybody can help, my gift log file says the following:
```

[12:30:00] Gnutella: Retrying to connect to nodes...
[12:30:10] Gnutella: try_some_nodes() returned 0. node list len=0
[12:30:10] Gnutella: No hosts to try. Looking in gwebcaches...
[12:30:10] *** GIFT-WARNING: Gnutella: skipping webcache http://gwebcache.bearshare.net/gcache.php, in bad gwebcaches
[12:30:10] *** GIFT-WARNING: Gnutella: skipping webcache http://ygwc.y-0.net/ygwc.php, in bad gwebcaches
[12:30:10] *** GIFT-WARNING: Gnutella: skipping webcache http://gwebcache.bearshare.net/gcache.Php, in bad gwebcaches
[12:30:10] Gnutella: gt_web_cache.c:737(get_random_cache): couldn't find random cache
[12:30:10] Gnutella: gt_web_cache.c:797(access_gwebcaches): error looking up cache
[12:30:10] Gnutella: Retrying to connect to nodes...

```
so it seems something with gwebcaches isn't working right. now i'm not sure this is even a configuration problem on my part or something that has changed on the gnutella network but hasn't been updated for gift (i read that gwebcaches was getting used by spammers and hammered or something. another article said, "gwebcaches close to dead" so maybe it changed implementation or something)

thanks for any help,
jet

---

### Post by yowshi on 2007-12-18
yeeeeah ok 30 minutes later gnutella and the other default network hasnt connected noones links to the otherlibs for the other 2 networks work and i've given up on this over technical piece of junk

---

### Post by Johnsie on 2008-03-16
Hi, sorry for the late reply, it's been a while since I've used these forums. Unfortunately I'm not sure what the status of the Apollon plugins is, Last time I tried I had difficulty getting any of the networks to work.

My recommendation is that people use frostwire instead: [http://www.frostwire.com/](http://www.frostwire.com/)

Personally I would prefer top see Apollon back and someone making it easier to install.

---

### Post by Johnsie on 2008-03-16
Ok... After a bit of research. Neither  the Appollon of the gIFT projects have posted any news for years. Apollon is just an interface for gIFT and cannot work if giFT is obsolete. The networks gift used to connect to have moved on and work differently now. 

How to get it working again?
There is one project related to gift that is still active. KCEasy is a windows program that is also a frontend to gIFT. The guy behind that seems to have been able to get it working. If someone can find out how we did that maybe someone could apply the same technique to apollon.

[http://www.kceasy.com](http://www.kceasy.com)


I would also think about looking at the cvs version of giFT

---

### Post by catrevingts on 2008-06-08
Is this true??? "2008: the darkest shadows stand over mankind. giFT project has been discontinued. ONLY ONE MAN CAN SAVE..."

Damm. Where is the Will Smith of linux-blogging?

I would like to suggest that SOMEBODY launched a website dedicated to linux updated information. As a recent windows-emigrate, I believe the biggest issue in linux distros is to find working repositories (as they get more and more descentralized every day) and updated info on file-sharing networks. 

You seek info, read all the step-by-step tips, and keep having trouble and more, till one day you'll find the dream was all gone. So frustrating. It costed me a lot of work to read through the 3 years of conversation in this thread (Ok, next time, I'll check the most recent posts).

---

### Post by equity on 2008-06-28
I configured all this stuff. When it came to how many Supernodes I wanted to connect to, I chose 17 or 27 (not sure anymore) because the setup told me not to "overdo" it. Seems like I exceeded the limit.

When I start Apollon, the Info tells me:

> Connection error
The giFT daemon, which is responsible for connecting to the various networks, appears to be down and I don't seem to able to start it.
Probably your giFT installation is corrupted. Try starting giFT manually by typing "giftd" on the command line. If this gives errors, there's likely some internal error in giFT or in your giFT configuration. Refer to the giFT homepage at [http://giftproject.org](http://giftproject.org) for help.

But I do not want to re-run all this setup-procedure again, so can anyone tell me how to to change this value? The giftd.conf file in ~/.giFT does not seem to contain this setting.
Thanks in advance for suggestion.

---

### Post by napolperro on 2008-07-09
Well I also had the doubt with the supernodes at setup and the thing about not overdoing it, so I left it in 4.

I updated the nodes file with the updated one, and yet it still has not connected to the Ares network, so the thing I have to do is just wait?

Ok, so i'm hoping this works.. :-k

---

### Post by balanovich on 2008-07-11
I'm using Ubuntu 8.04 64 bits

I followed the instructions and it doesn't work.

When I get the updates, i get this message at the end:

W: GPG error: [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A35A4E6EF00175CA
W: You may want to run apt-get update to correct these problems

then I type :
 sudo apt-get install gift libares-gift libfasttrack-gift apollon 

and I get :
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libares-gift

What should I do ?
Is my linux version a problem ?
Should I have installed something else before? (I though this was how to install apollon but is it only to configure it ? )

---

### Post by s_spiff on 2008-07-15
same as above... anyone?

---

### Post by steve108 on 2008-08-13
I am also having this problem. I am very new to ubuntu and would really like to get this working. I have installed apollon and giftd, but I am getting the same error as the two posts above me.

Thanks,
Steve

---

### Post by test3 (on suse) on 2009-02-13
hi  

ares is working (feb 2009) with theese nodes : 

<ip> <port> <reports> <attempts> <connects> <first_seen> <last_seen> <last_attempt>
83.84.99.79 27917 2 43 22 1233929647 1234522576 1234522576
94.209.80.27 35047 3 52 16 1233932302 1234522576 1234522576
85.219.48.180 62082 1 12 12 1234303757 1234521093 1234521093
67.83.70.216 62869 3 40 13 1233883862 1234291368 1234522576
88.177.155.225 8844 2 1 1 1234521119 1234521131 1234521126
89.173.70.183 16809 1 1 1 1234521131 1234522576 1234522576
83.53.82.99 58743 2 6 4 1234122499 1234522576 1234522576
193.239.101.92 24628 1 1 1 1234521093 1234521109 1234521109
79.16.164.242 47488 1 1 1 1234521109 1234521110 1234521109
217.129.252.29 47783 1 1 1 1234521110 1234521115 1234521115
85.136.146.61 18232 1 1 1 1234521126 1234521131 1234521131
130.15.208.221 58397 1 0 0 1234522576 1234522576 0
85.137.147.112 61589 1 0 0 1234522576 1234522576 0
217.125.121.95 23952 1 0 0 1234522576 1234522576 0
200.109.191.192 50083 1 0 0 1234522576 1234522576 0
201.236.173.109 61751 1 0 0 1234522576 1234522576 0
186.14.33.177 63451 1 0 0 1234522576 1234522576 0
201.209.146.199 9771 1 0 0 1234522576 1234522576 0
85.84.184.77 19680 1 0 0 1234522576 1234522576 0
87.205.214.118 54331 1 0 0 1234522576 1234522576 0
72.145.33.16 18288 1 0 0 1234522576 1234522576 0
89.25.250.211 55639 1 0 0 1234522576 1234522576 0
190.177.221.230 45964 1 0 0 1234522576 1234522576 0
89.161.23.210 10040 1 0 0 1234522576 1234522576 0
83.34.34.27 9849 1 0 0 1234522576 1234522576 0
201.244.246.185 22299 1 0 0 1234522576 1234522576 0
69.125.157.244 32769 1 0 0 1234522576 1234522576 0
77.208.28.100 30697 1 0 0 1234522576 1234522576 0
190.138.24.63 21786 1 0 0 1234522576 1234522576 0
84.123.1.153 51755 1 0 0 1234522576 1234522576 0
201.215.85.228 18548 1 0 0 1234521093 1234521093 0
201.140.191.41 18012 1 0 0 1234521093 1234521093 0
212.159.19.193 40705 1 0 0 1234521093 1234521093 0
88.163.90.71 25711 1 0 0 1234521093 1234521093 0
85.87.13.76 35346 1 0 0 1234521093 1234521093 0
201.241.132.4 47427 1 0 0 1234521093 1234521093 0
190.74.27.231 47367 1 0 0 1234521093 1234521093 0
84.122.21.200 30937 1 0 0 1234521093 1234521093 0
190.75.142.19 14081 1 0 0 1234521093 1234521093 0
72.179.179.34 9057 1 0 0 1234521093 1234521093 0
88.156.198.202 41440 1 0 0 1234521109 1234521109 0
201.164.159.227 7842 1 0 0 1234521109 1234521109 0
83.144.108.91 17323 1 0 0 1234521109 1234521109 0
77.208.18.185 36760 1 0 0 1234521109 1234521109 0
130.79.99.167 52260 1 0 0 1234521109 1234521109 0
190.174.65.101 47280 1 0 0 1234521109 1234521109 0
190.201.127.89 13718 1 0 0 1234521109 1234521109 0
24.125.106.89 50238 1 0 0 1234521109 1234521109 0
80.102.149.34 49329 1 0 0 1234521109 1234521109 0
189.188.91.130 36378 1 0 0 1234521109 1234521109 0
190.84.131.179 29123 1 0 0 1234521110 1234521110 0
69.143.80.64 13950 1 0 0 1234521110 1234521110 0
62.57.180.6 6181 1 0 0 1234521110 1234521110 0
79.188.42.146 47204 1 0 0 1234521110 1234521110 0
62.120.37.101 16751 1 0 0 1234521110 1234521110 0
85.155.80.90 47673 1 0 0 1234521110 1234521110 0
201.231.252.222 30447 1 0 0 1234521110 1234521110 0
83.10.28.251 20037 1 0 0 1234521110 1234521110 0
190.205.96.118 30004 1 0 0 1234521110 1234521110 0
59.92.136.78 50992 1 0 0 1234521110 1234521110 0
200.93.88.214 36726 1 0 0 1234521115 1234521115 0
190.76.45.171 38937 1 0 0 1234521115 1234521115 0
201.232.31.84 32350 1 0 0 1234521115 1234521115 0
201.213.17.168 51350 1 0 0 1234521115 1234521115 0
156.34.213.130 22430 1 0 0 1234521115 1234521115 0
190.136.146.228 19919 1 0 0 1234521115 1234521115 0
85.152.188.131 27095 1 0 0 1234521115 1234521115 0
24.32.226.32 53607 1 0 0 1234521115 1234521115 0
98.203.67.243 56628 1 0 0 1234521115 1234521115 0
24.170.91.206 8541 1 0 0 1234521119 1234521119 0
24.212.84.217 54411 1 0 0 1234521119 1234521119 0
200.126.83.20 47936 1 0 0 1234521119 1234521119 0
87.111.0.39 8133 1 0 0 1234521119 1234521119 0
82.158.18.185 48277 1 0 0 1234521119 1234521119 0
99.161.129.75 40876 1 0 0 1234521119 1234521119 0
84.120.77.38 28837 1 0 0 1234521119 1234521119 0
196.206.192.160 16553 1 0 0 1234521119 1234521119 0
84.123.249.232 47515 1 0 0 1234521119 1234521119 0
98.219.92.67 61328 1 0 0 1234521126 1234521126 0
190.174.87.39 8906 1 0 0 1234521126 1234521126 0
200.90.239.1 12441 1 0 0 1234521126 1234521126 0
190.173.2.121 15525 1 0 0 1234521126 1234521126 0
89.228.86.204 20740 1 0 0 1234521126 1234521126 0
72.19.106.49 61156 1 0 0 1234521126 1234521126 0
93.105.174.209 32843 1 0 0 1234521126 1234521126 0
201.250.163.168 12004 1 0 0 1234521126 1234521126 0
82.236.153.202 18986 1 0 0 1234521126 1234521126 0
124.158.96.210 59418 1 0 0 1234521126 1234521126 0
190.46.141.112 20248 1 0 0 1234521131 1234521131 0
200.104.118.222 43493 1 0 0 1234521131 1234521131 0
89.128.254.238 52722 1 0 0 1234521131 1234521131 0
190.173.211.183 22772 1 0 0 1234521131 1234521131 0
79.150.118.44 36484 1 0 0 1234521131 1234521131 0
85.136.139.104 24879 1 0 0 1234521131 1234521131 0
83.38.235.110 34560 1 0 0 1234521131 1234521131 0
201.210.40.34 35864 1 0 0 1234521131 1234521131 0
83.45.129.195 5854 1 0 0 1234521131 1234521131 0
98.112.85.167 41091 1 0 0 1234521131 1234521131 0
80.219.233.44 21055 1 0 0 1234521131 1234521131 0
190.73.141.73 16699 1 0 0 1234519991 1234519991 0
190.203.6.112 21461 1 0 0 1234519991 1234519991 0
87.56.29.12 41089 1 0 0 1234519991 1234519991 0
201.92.52.213 47829 1 0 0 1234519991 1234519991 0
201.66.156.103 41647 1 0 0 1234519991 1234519991 0
83.28.25.191 48623 1 0 0 1234519991 1234519991 0
71.85.107.153 30203 1 0 0 1234519991 1234519991 0
69.14.157.237 35348 1 0 0 1234519991 1234519991 0
208.70.92.154 61582 1 0 0 1234519991 1234519991 0
189.47.114.223 29921 1 0 0 1234519991 1234519991 0
84.232.76.33 48985 1 0 0 1234519991 1234519991 0
200.93.60.115 23542 1 0 0 1234519991 1234519991 0
190.48.126.40 28311 1 0 0 1234519991 1234519991 0
91.145.132.29 9263 1 0 0 1234519991 1234519991 0
64.203.32.45 27021 1 0 0 1234519991 1234519991 0
201.42.160.101 13726 1 0 0 1234519991 1234519991 0
201.43.164.69 28766 1 0 0 1234519991 1234519991 0
69.81.59.113 7942 1 0 0 1234519991 1234519991 0
89.161.46.142 10244 1 0 0 1234519991 1234519991 0
190.77.101.137 53338 1 0 0 1234519991 1234519991 0
81.9.129.69 52379 1 0 0 1234519991 1234519991 0
87.217.125.236 64116 1 0 0 1234519991 1234519991 0
24.137.112.129 57517 1 0 0 1234519991 1234519991 0
190.44.54.219 34637 1 0 0 1234519991 1234519991 0
71.8.43.79 31904 1 0 0 1234519991 1234519991 0
200.93.109.133 46078 1 0 0 1234519991 1234519991 0
77.208.99.47 53716 1 0 0 1234519991 1234519991 0
201.236.2.237 46079 1 0 0 1234519991 1234519991 0
85.85.94.207 19177 1 0 0 1234519991 1234519991 0
190.65.52.174 36997 1 0 0 1234519991 1234519991 0
190.69.230.85 27797 1 0 0 1234519991 1234519991 0
201.132.242.235 29975 1 0 0 1234519991 1234519991 0
201.223.241.254 10526 1 0 0 1234519991 1234519991 0
190.51.24.211 8914 1 0 0 1234519991 1234519991 0
173.22.154.226 11308 1 0 0 1234519991 1234519991 0
75.185.56.171 48757 1 0 0 1234519991 1234519991 0
89.228.84.216 39597 1 0 0 1234519991 1234519991 0
217.64.181.137 51534 1 0 0 1234519991 1234519991 0
99.26.195.83 6543 1 0 0 1234519991 1234519991 0
98.227.68.101 9059 1 0 0 1234519991 1234519991 0
85.219.5.203 60087 1 0 0 1234519991 1234519991 0
217.145.11.246 39476 1 0 0 1234519991 1234519991 0
190.200.252.209 54934 1 0 0 1234519991 1234519991 0
190.157.130.65 52917 1 0 0 1234519991 1234519991 0
12.203.105.75 37357 1 0 0 1234519991 1234519991 0
62.30.67.241 11318 1 0 0 1234519991 1234519991 0
71.174.27.113 33794 1 0 0 1234519991 1234519991 0
67.86.239.248 16947 1 0 0 1234519991 1234519991 0
149.150.237.26 15325 1 0 0 1234519991 1234519991 0
200.92.198.123 13312 1 0 0 1234519991 1234519991 0
190.157.220.40 48461 1 0 0 1234519991 1234519991 0
189.164.131.235 64496 1 0 0 1234519991 1234519991 0
209.127.198.10 62481 1 0 0 1234519991 1234519991 0
24.45.26.224 64871 1 0 0 1234519991 1234519991 0
201.239.111.128 41833 1 0 0 1234519991 1234519991 0
190.201.129.245 38510 1 0 0 1234519991 1234519991 0
190.78.179.69 11357 1 0 0 1234519991 1234519991 0
201.233.240.88 23215 1 0 0 1234519991 1234519991 0
190.157.180.146 45438 1 0 0 1234519991 1234519991 0
88.23.26.171 58657 1 0 0 1234519991 1234519991 0
190.27.188.117 42121 1 0 0 1234519991 1234519991 0
201.43.128.183 35577 1 0 0 1234519991 1234519991 0
68.32.56.46 54712 1 0 0 1234519991 1234519991 0
72.181.53.188 22335 1 0 0 1234519991 1234519991 0
189.237.11.60 51964 1 0 0 1234519991 1234519991 0
201.235.223.35 12021 1 0 0 1234519991 1234519991 0
190.207.119.77 39538 1 0 0 1234519991 1234519991 0
201.252.140.132 42277 1 0 0 1234519991 1234519991 0
190.20.126.6 45523 1 0 0 1234519991 1234519991 0
189.107.145.10 8298 1 0 0 1234519991 1234519991 0
86.69.75.66 27001 1 0 0 1234519991 1234519991 0
83.86.53.28 34470 1 0 0 1234519994 1234519994 0
66.8.238.7 7457 1 0 0 1234519994 1234519994 0
189.156.243.242 50240 1 0 0 1234519994 1234519994 0
65.75.115.198 61274 1 0 0 1234519994 1234519994 0
174.33.201.171 34957 1 0 0 1234519994 1234519994 0
69.112.98.220 45959 1 0 0 1234519994 1234519994 0
190.36.223.231 52506 1 0 0 1234519994 1234519994 0
201.172.234.240 9846 1 0 0 1234519994 1234519994 0
174.48.197.167 51624 1 0 0 1234519994 1234519994 0
201.208.160.201 9312 1 0 0 1234519994 1234519994 0
201.222.252.95 9000 1 0 0 1234519994 1234519994 0
190.138.136.54 38988 1 0 0 1234519994 1234519994 0
70.188.168.115 25712 1 0 0 1234519994 1234519994 0
201.214.14.239 38654 1 0 0 1234519994 1234519994 0
75.21.123.30 12908 1 0 0 1234519994 1234519994 0
190.7.129.114 41403 1 0 0 1234519994 1234519994 0
189.104.176.220 55483 1 0 0 1234519994 1234519994 0
85.180.19.49 42614 1 0 0 1234519994 1234519994 0
74.79.89.123 52981 1 0 0 1234519994 1234519994 0
190.38.146.186 48315 1 0 0 1234519994 1234519994 0
200.116.177.64 19347 1 0 0 1234519994 1234519994 0
84.120.98.204 14044 1 0 0 1234519994 1234519994 0
190.174.10.237 15599 1 0 0 1234519994 1234519994 0
190.55.186.80 54711 1 0 0 1234519994 1234519994 0
24.139.156.192 15566 1 0 0 1234519994 1234519994 0
190.244.174.153 37198 1 0 0 1234519994 1234519994 0
77.224.59.184 5383 1 0 0 1234519994 1234519994 0
99.239.11.137 5826 1 0 0 1234519994 1234519994 0
201.208.51.73 55635 1 0 0 1234519994 1234519994 0
68.199.203.169 43196 1 0 0 1234519994 1234519994 0
75.111.145.9 57237 1 0 0 1234519994 1234519994 0
69.151.227.128 18121 1 0 0 1234519994 1234519994 0
200.84.133.157 60755 1 0 0 1234519994 1234519994 0
201.250.57.134 8941 1 0 0 1234519994 1234519994 0
76.177.83.118 5490 1 0 0 1234519994 1234519994 0
66.233.118.66 38236 1 0 0 1234519994 1234519994 0
201.243.236.146 56935 1 0 0 1234519994 1234519994 0
190.0.72.13 16546 1 0 0 1234519994 1234519994 0
24.144.55.153 13969 1 0 0 1234519994 1234519994 0
82.168.80.182 24269 1 0 0 1234519994 1234519994 0
190.79.96.23 48086 1 0 0 1234519994 1234519994 0
190.159.150.33 20304 1 0 0 1234519994 1234519994 0
87.239.172.222 8664 1 0 0 1234519994 1234519994 0
85.84.203.186 11296 1 0 0 1234519994 1234519994 0
201.245.251.129 24306 1 0 0 1234519994 1234519994 0
190.176.214.9 46348 1 0 0 1234519994 1234519994 0
200.119.37.179 29460 1 0 0 1234519994 1234519994 0
190.95.105.96 55430 1 0 0 1234519994 1234519994 0
201.255.119.247 19733 1 0 0 1234519994 1234519994 0
69.79.44.216 53753 1 0 0 1234519994 1234519994 0
83.213.38.187 25284 1 0 0 1234519994 1234519994 0
189.216.194.163 29471 1 0 0 1234519994 1234519994 0
190.18.84.160 32220 1 0 0 1234519994 1234519994 0
200.122.75.19 19974 1 0 0 1234519994 1234519994 0
189.105.34.159 12367 1 0 0 1234519420 1234519420 0
71.74.124.120 27168 1 0 0 1234519420 1234519420 0
75.49.38.65 13986 1 0 0 1234519420 1234519420 0
201.208.91.129 40337 1 0 0 1234519420 1234519420 0
200.119.34.129 37039 1 0 0 1234519420 1234519420 0
99.240.172.111 62911 1 0 0 1234519420 1234519420 0
82.147.57.240 32742 1 0 0 1234519420 1234519420 0
201.215.82.126 24159 1 0 0 1234519420 1234519420 0
24.179.199.213 27206 1 0 0 1234519420 1234519420 0
66.177.98.215 28438 1 0 0 1234519420 1234519420 0
74.193.2.94 46768 1 0 0 1234519420 1234519420 0
84.126.173.117 64402 1 0 0 1234519420 1234519420 0
201.132.157.8 24887 1 0 0 1234519420 1234519420 0
201.242.199.130 54511 1 0 0 1234519420 1234519420 0
79.163.0.4 22284 1 0 0 1234519420 1234519420 0
82.174.249.25 50625 1 0 0 1234519420 1234519420 0
41.250.232.103 32891 1 0 0 1234519420 1234519420 0
85.86.154.20 7865 1 0 0 1234519420 1234519420 0
190.49.167.61 53393 1 0 0 1234519420 1234519420 0
88.5.46.112 30168 1 0 0 1234519420 1234519420 0
97.101.137.25 61249 1 0 0 1234519420 1234519420 0
190.72.159.164 48561 1 0 0 1234519420 1234519420 0
99.230.107.81 63136 1 0 0 1234519420 1234519420 0
87.221.174.38 58745 1 0 0 1234519420 1234519420 0
98.226.234.75 22850 1 0 0 1234519441 1234519441 0
200.59.233.243 8518 1 0 0 1234519441 1234519441 0
71.90.26.143 50674 1 0 0 1234519441 1234519441 0
190.199.94.86 9576 1 0 0 1234519441 1234519441 0
92.97.187.178 52665 1 0 0 1234519441 1234519441 0
24.224.213.80 61825 1 0 0 1234519441 1234519441 0
98.243.86.232 28313 1 0 0 1234519441 1234519441 0
83.144.108.157 8946 1 0 0 1234519441 1234519441 0
190.176.156.206 30684 1 0 0 1234519441 1234519441 0
213.60.13.210 44941 1 0 0 1234519441 1234519441 0
85.155.235.178 30126 1 0 0 1234519441 1234519441 0
89.230.231.52 7943 1 0 0 1234519441 1234519441 0
68.84.201.90 17130 1 0 0 1234519441 1234519441 0
207.47.182.56 40214 1 0 0 1234519441 1234519441 0
85.178.148.76 10709 1 0 0 1234519441 1234519441 0
201.208.238.161 48829 1 0 0 1234519441 1234519441 0
83.30.172.197 26308 1 0 0 1234519441 1234519441 0
89.76.209.73 52727 1 0 0 1234519441 1234519441 0
85.55.59.91 37558 1 0 0 1234519441 1234519441 0
71.195.150.19 61203 1 0 0 1234519441 1234519441 0
190.188.65.56 50158 1 0 0 1234519441 1234519441 0
84.121.119.25 24209 1 0 0 1234519441 1234519441 0
76.175.82.67 20696 1 0 0 1234519441 1234519441 0
68.57.205.67 11312 1 0 0 1234519441 1234519441 0
68.14.87.129 30255 1 0 0 1234519441 1234519441 0
83.249.87.154 27010 1 0 0 1234519441 1234519441 0
190.176.205.202 25003 1 0 0 1234519441 1234519441 0
62.43.74.123 30042 1 0 0 1234519441 1234519441 0
190.49.53.113 25496 1 0 0 1234519441 1234519441 0
201.244.44.38 55993 1 0 0 1234519441 1234519441 0
82.237.65.99 42454 1 0 0 1234519441 1234519441 0
190.156.210.147 52283 1 0 0 1234519441 1234519441 0
75.181.90.207 24526 1 0 0 1234519441 1234519441 0
190.140.48.45 64246 1 0 0 1234519441 1234519441 0
71.230.200.83 36793 1 0 0 1234519441 1234519441 0
88.18.107.93 61074 1 0 0 1234519442 1234519442 0
70.117.246.54 14417 1 0 0 1234519442 1234519442 0
190.159.47.38 24476 1 0 0 1234519442 1234519442 0
190.208.124.152 43862 1 0 0 1234519442 1234519442 0
190.232.230.248 35866 1 0 0 1234519442 1234519442 0
75.1.86.147 42338 1 0 0 1234519442 1234519442 0
186.12.178.134 20605 1 0 0 1234519442 1234519442 0
60.48.168.59 59820 1 0 0 1234519442 1234519442 0
201.209.22.41 14853 1 0 0 1234519442 1234519442 0
76.125.35.127 54068 1 0 0 1234519442 1234519442 0
87.16.41.145 30683 1 0 0 1234519442 1234519442 0
84.122.176.241 30659 1 0 0 1234519442 1234519442 0
190.51.67.143 45033 1 0 0 1234519442 1234519442 0
190.24.104.150 47746 1 0 0 1234519442 1234519442 0
24.113.68.17 28117 1 0 0 1234519442 1234519442 0
201.248.71.189 15113 1 0 0 1234519442 1234519442 0
190.157.169.165 45440 1 0 0 1234519442 1234519442 0
190.176.195.145 19310 1 0 0 1234519442 1234519442 0
201.246.206.18 13013 1 0 0 1234519443 1234519443 0
83.44.44.131 5241 1 0 0 1234519443 1234519443 0
189.217.29.197 34078 1 0 0 1234519443 1234519443 0
201.226.241.101 54916 1 0 0 1234519443 1234519443 0
189.193.146.99 63166 1 0 0 1234519443 1234519443 0
201.167.120.203 12377 1 0 0 1234519443 1234519443 0
200.92.68.166 43251 1 0 0 1234519443 1234519443 0
76.23.163.185 26718 1 0 0 1234519443 1234519443 0
201.222.162.191 43423 1 0 0 1234519460 1234519460 0
85.84.15.252 53896 1 0 0 1234519460 1234519460 0
83.138.240.178 23797 1 0 0 1234519460 1234519460 0
190.21.119.194 22842 1 0 0 1234519460 1234519460 0
190.48.130.190 32784 1 0 0 1234519460 1234519460 0
190.17.7.38 57724 1 0 0 1234519460 1234519460 0
82.247.110.77 15639 1 0 0 1234519460 1234519460 0
81.202.164.67 14676 1 0 0 1234519460 1234519460 0
85.84.74.227 34995 1 2 1 1234521115 1234522576 1234522576
79.191.91.234 46339 1 2 1 1234519420 1234521093 1234521093
187.25.151.251 10652 1 2 1 1234519420 1234521093 1234521093
190.246.46.130 6974 1 2 1 1234519441 1234521093 1234521093
201.242.194.239 12552 1 2 1 1234519441 1234521093 1234521093
99.229.9.75 31511 1 2 1 1234519443 1234521093 1234521093
190.39.32.38 18569 1 2 1 1234519991 1234521093 1234521093
88.160.35.195 63927 1 2 1 1234519460 1234521109 1234521109
68.11.63.101 43058 1 2 1 1234519991 1234521110 1234521109
78.131.188.68 44796 1 2 1 1234519460 1234521115 1234521115
190.74.66.69 52471 1 2 1 1234519994 1234521119 1234521119
83.231.87.247 19481 1 2 1 1234519460 1234521126 1234521126
190.77.229.176 64990 1 2 1 1234519991 1234521131 1234521131
200.92.160.17 20343 2 1 0 1234519420 1234521109 1234521109
83.42.109.1 54300 2 1 0 1234519994 1234519994 1234519994
93.148.216.164 58897 1 1 0 1234521131 1234522576 1234522576
87.206.235.151 27829 1 1 0 1234521131 1234522576 1234522576
99.128.209.134 13106 1 1 0 1234521131 1234522576 1234522576
85.85.104.127 47300 1 1 0 1234521131 1234522576 1234522576
201.163.12.149 48375 1 1 0 1234521131 1234522576 1234522576
201.130.224.204 36262 1 1 0 1234521131 1234522576 1234522576
98.226.64.185 35724 1 1 0 1234521093 1234521109 1234521109
69.125.178.109 20610 1 1 0 1234521093 1234521109 1234521109
81.37.133.128 23604 1 1 0 1234521093 1234521109 1234521109
79.163.246.123 9689 1 1 0 1234521093 1234521109 1234521109
189.71.214.108 42710 1 1 0 1234521093 1234521109 1234521109
190.77.202.119 56624 1 1 0 1234521093 1234521109 1234521109
201.236.1.140 43946 1 1 0 1234521093 1234521109 1234521109
190.198.114.225 24154 1 1 0 1234521109 1234521110 1234521109
190.159.209.117 42162 1 1 0 1234521109 1234521110 1234521109
79.12.122.13 59208 1 1 0 1234521109 1234521110 1234521109
201.165.189.51 55568 1 1 0 1234521109 1234521110 1234521109
200.232.135.141 40646 1 1 0 1234521109 1234521110 1234521109
79.148.59.61 11118 1 1 0 1234521109 1234521110 1234521109
89.214.193.47 51683 1 1 0 1234521109 1234521110 1234521109
190.224.64.185 28013 1 1 0 1234521109 1234521110 1234521109
81.203.16.126 6853 1 1 0 1234521110 1234521115 1234521115
82.233.162.95 50864 1 1 0 1234521110 1234521115 1234521115
99.188.132.98 52176 1 1 0 1234521110 1234521115 1234521115
69.113.142.130 47028 1 1 0 1234521110 1234521115 1234521115
79.155.221.242 61714 1 1 0 1234521110 1234521115 1234521115
213.213.218.83 33721 1 1 0 1234521110 1234521115 1234521115
84.125.153.60 48141 1 1 0 1234521110 1234521115 1234521115
69.118.194.133 40076 1 1 0 1234521110 1234521115 1234521115
87.222.11.33 11362 1 1 0 1234521115 1234521115 1234521119
88.25.247.103 60749 1 1 0 1234521115 1234521119 1234521119
99.50.184.152 29395 1 1 0 1234521115 1234521119 1234521119
67.167.14.112 19588 1 1 0 1234521115 1234521119 1234521119
71.229.241.118 34368 1 1 0 1234521115 1234521119 1234521119
190.161.94.181 38582 1 1 0 1234521115 1234521119 1234521119
69.63.57.213 28442 1 1 0 1234521115 1234521119 1234521119
88.19.216.175 63162 1 1 0 1234521115 1234521119 1234521119
70.241.126.202 31047 1 1 0 1234521115 1234521119 1234521119
213.114.191.36 10836 1 1 0 1234521119 1234521119 1234521126
190.139.121.208 19315 1 1 0 1234521119 1234521126 1234521126
195.116.68.145 24908 1 1 0 1234521119 1234521126 1234521126
190.47.3.99 27463 1 1 0 1234521119 1234521126 1234521126
65.26.219.51 29400 1 1 0 1234521119 1234521126 1234521126
193.153.155.157 12261 1 1 0 1234521119 1234521126 1234521126
85.49.215.253 36183 1 1 0 1234521119 1234521126 1234521126
70.188.184.197 39970 1 1 0 1234521119 1234521126 1234521126
190.51.254.26 29925 1 1 0 1234521119 1234521126 1234521126
92.83.8.78 8082 1 1 0 1234521126 1234521131 1234521131
190.79.30.173 6026 1 1 0 1234521126 1234521131 1234521131
83.165.121.18 15387 1 1 0 1234521126 1234521131 1234521131
200.90.79.173 60313 1 1 0 1234521126 1234521131 1234521131
65.197.44.216 11329 1 1 0 1234521126 1234521131 1234521131
190.173.84.14 9291 1 1 0 1234521126 1234521131 1234521131
69.142.122.91 31790 1 1 0 1234521126 1234521131 1234521131
75.37.181.9 17219 1 1 0 1234521126 1234521131 1234521131
190.110.128.14 23681 1 1 0 1234519991 1234519994 1234519991
94.112.195.46 16550 1 1 0 1234519991 1234519994 1234519991
190.82.0.162 20923 1 1 0 1234519460 1234519994 1234519990
69.244.150.24 56223 1 1 0 1234519460 1234519994 1234519990
77.243.72.227 24232 1 1 0 1234519460 1234519994 1234519990
190.161.12.230 20035 1 1 0 1234519460 1234519994 1234519990
77.254.131.239 33951 1 1 0 1234519460 1234519994 1234519990
201.244.222.166 21607 1 1 0 1234519460 1234519994 1234519990
200.52.221.155 19020 1 1 0 1234519420 1234519420 1234519420
202.46.137.227 22751 1 1 0 1234519420 1234519420 1234519420
201.167.54.69 64153 1 1 0 1234519420 1234519420 1234519420
87.223.25.183 35549 1 1 0 1234519443 1234519443 1234519443
201.209.129.180 63347 1 1 0 1234519420 1234519420 1234519440
 





and gnutella with theese nodes : 

1234522692 72.210.67.225:15702 4096 0
1234522692 71.197.55.253:48654 4096 0
1234522692 64.231.73.204:38721 16384 5
1234520890 72.199.166.69:39646 262144 54
1234519736 68.6.225.58:14452 16384 8
1234519736 68.83.192.216:6337 16384 8
1234492771 76.111.164.162:38756 2097152 372
1234492771 142.162.219.48:24745 524288 96
1234489171 98.119.19.28:11309 524288 92
1234485571 71.238.217.19:36807 65536 11
1234477471 72.140.38.17:47305 131072 27
1234403503 74.216.63.5:50316 131072 30
1234403503 99.232.183.68:29601 262144 54
1234403503 98.21.69.38:19252 65536 16
1234392703 98.203.24.70:21254 8192 1
1234392703 24.188.23.56:2601 524288 62
1234391803 72.130.241.176:23290 2097152 1861
1234311530 71.30.69.189:8674 8192 1
1234311530 92.235.75.8:21460 65536 12
1234311530 75.65.120.34:31753 1048576 187
1234311167 24.21.212.152:34442 2097152 274
1234308467 24.46.160.240:8837 8 0
1234307567 74.210.64.243:44984 262144 63
1234303067 99.234.196.57:13735 1048576 271
1234302167 99.26.192.204:32933 1048576 194
1234302167 75.87.239.184:39904 2097152 370
1234299467 173.19.36.72:40999 4096 0
1234296767 68.149.231.43:3961 262144 89
1234294067 82.35.240.88:38123 4096 0
1234293167 98.233.70.222:24486 131072 71
1234273517 76.97.155.18:29204 2097152 1476
1234273517 90.203.13.239:35662 2097152 149
1234273517 69.136.177.224:31363 131072 33
1234268117 77.238.194.143:11654 524288 74
1234265417 99.236.72.45:46191 524288 167
1234140165 69.139.179.158:29867 524288 86
1234140165 98.238.63.43:8443 524288 70
1234125861 206.248.88.140:48043 8192 1
1234120461 66.190.8.19:47016 1048576 153
1234114161 91.106.17.135:36366 32768 11
1233961106 70.244.159.149:3708 262144 52
1233961106 82.30.229.168:36751 4096 2
1233961106 86.3.239.87:20468 131072 18
1233960206 76.110.28.243:10481 16384 3
1233960206 68.226.221.61:16083 2097152 2247
1233959158 99.254.96.172:7032 32768 8
1233958258 86.97.241.121:10050 524288 154
1233958258 72.140.3.138:37494 2097152 613
1233957358 72.137.210.118:19905 8192 1
1233955558 70.69.58.88:16169 524288 125
1233955558 207.171.202.163:41982 1048576 3
1233954658 85.164.103.220:15810 4096 0
1233951958 68.44.233.150:36527 8 0
1233951958 204.214.131.129:29683 2097152 980
1233951958 71.56.107.118:49869 524288 97
1233946558 75.202.80.51:39239 1048576 172
1233945658 85.154.150.225:31734 16384 0
1233937558 67.83.142.176:28236 262144 102
1233937558 75.75.68.161:7787 2097152 1400
1233935758 63.160.31.82:43646 2097152 27
1233933958 24.21.15.232:43277 1048576 172
1233933958 24.44.88.190:42057 4096 0
1233932158 124.104.10.224:28125 32768 5
1233927658 76.69.76.177:21281 524288 136
1233927658 99.232.231.37:16188 524288 120
1233887816 173.32.13.51:39262 65536 12
1233887816 98.228.41.243:47684 4096 0
1233887816 71.203.250.9:37720 131072 29
1233886660 24.56.213.193:41550 2097152 656
1233886555 142.68.245.31:27229 131072 23
1233886555 12.181.162.8:10591 1048576 234
1233881932 68.4.116.174:12406 65536 53
1233881932 68.103.131.24:36582 524288 137
1233880971 174.1.24.131:18503 2097152 2633
1233880971 99.25.185.249:39601 2097152 1737
1233879170 99.245.76.35:32689 16384 4
1233879170 76.197.8.204:41403 2097152 2329
1233878270 74.209.50.182:6154 1048576 261
1233876452 71.251.209.205:13770 8 0
1233876452 76.15.221.114:51958 2097152 1327
1233876445 61.4.101.70:38266 524288 59
1233876297 128.255.199.199:43172 131072 43
1233706121 70.109.122.34:19824 131072 30
1233706121 68.186.45.193:49860 131072 42
1233706121 69.205.168.204:35301 262144 78
1233704111 99.228.46.43:45958 4096 0
1233703211 99.237.94.160:43156 32768 7
1233685848 24.56.214.200:26064 262144 58
1233685038 218.251.50.92:32381 2097152 44
1233685038 87.102.35.112:47028 2097152 563
1233685038 212.159.119.232:50483 524288 135
1233684983 98.117.38.142:26350 2097152 138
1233684983 82.36.84.56:33049 524288 136
1233684983 206.188.133.71:8223 2097152 353
1233680278 68.148.22.139:47922 262144 83
1233679378 71.79.147.47:19610 16384 0
1233679378 24.151.49.79:18831 8192 2
1233672472 72.137.235.241:41738 2097152 40
1233672472 24.187.73.95:16125 65536 15
1233626666 24.23.236.164:9308 1048576 263
1233626666 24.170.227.95:17961 2097152 611
1233625827 75.131.129.120:43583 131072 36
1233623989 72.187.194.84:23914 4096 0
1233623989 99.245.175.162:13133 65536 8
1233622330 67.191.220.9:47314 262144 85
1233622325 187.25.141.241:22483 262144 36
1233622325 99.238.223.59:25833 262144 45
1233621182 96.30.144.43:37008 131072 35
1233621182 76.175.229.242:26677 1048576 267
1233621182 70.188.101.168:9401 1048576 51
1233617287 88.90.130.28:10068 2097152 635
1233616121 66.231.40.251:26518 2097152 700
1233616121 72.216.14.32:28526 2097152 469
1233615782 94.66.27.239:11332 2097152 121
1233615782 99.252.33.116:13108 1048576 170
1233615703 76.116.16.223:35953 131072 15
1233585679 202.156.83.123:48630 1048576 318
1233585679 65.32.123.2:39060 8 0
1233585679 72.47.23.113:43575 1048576 200
1233584904 205.237.172.64:30811 16384 2
1233584778 76.188.244.160:25008 65536 10
1233583334 84.72.11.102:4072 8192 1
1233583330 134.114.91.143:20651 16384 2
1233582977 75.70.120.212:44365 4096 0
1233582207 216.130.160.249:37777 4096 4
1233580822 66.65.38.128:49351 65536 9
1233580822 24.138.29.103:41583 262144 42
1233580822 209.183.169.71:25365 2097152 44
1233580576 99.224.74.243:12046 16384 3
1233577162 173.26.115.26:26059 1048576 30
1233395101 82.41.162.193:50540 32768 4
1233392929 24.44.168.134:49225 2048 1
1233392929 75.84.115.52:27990 2097152 502
1233362023 67.242.110.121:29949 1048576 187
1233359005 90.224.212.124:9748 8192 8
1233356788 96.42.64.246:28635 1048576 205
1233345195 216.12.80.104:34744 32768 48
1233345195 75.41.220.171:17819 2097152 165
1233345195 74.14.58.139:45375 65536 13
1233339810 97.116.77.42:42054 65536 20
1233339810 75.173.30.88:49302 524288 92
1233339810 72.187.167.196:27946 524288 123
1233338910 99.236.84.250:47273 2097152 306
1233338910 98.162.249.117:29583 2097152 35
1233333762 97.123.27.243:40181 1048576 332
1233333762 216.168.117.154:43827 1048576 20
1233333762 24.188.71.126:24033 1048576 291
1233322521 173.88.145.78:16249 2097152 493
1233322521 92.3.231.161:34569 1048576 17
1233322521 72.174.123.26:28888 4096 0
1233321630 24.181.45.160:8571 262144 71
1233321630 74.15.250.223:3183 2097152 2011
1233320987 210.49.196.165:6348 0 0
1233320987 114.48.29.238:6346 0 0
1233320987 87.20.118.34:6346 0 0
1233320987 122.133.206.63:6346 0 0
1233320987 72.196.17.63:6346 0 0
1233320987 59.171.133.190:6346 0 0
1233320987 72.199.102.234:6348 0 0
1233320987 221.37.11.69:6346 0 0
1233320987 89.161.9.134:6346 0 0
1233320987 24.79.1.109:6346 0 0
1233320987 71.65.199.85:6348 0 0
1233320987 220.104.10.219:6346 0 0
1233320987 203.165.164.73:6346 0 0
1233320987 89.102.133.161:6346 0 0
1233320987 121.58.129.99:6346 0 0
1233320987 173.20.154.128:6346 0 0
1233320987 70.177.69.170:6346 0 0
1233320987 220.24.3.203:6346 0 0
1233320987 121.117.78.204:6346 0 0
1233320987 76.125.89.44:6348 0 0
1233320987 68.52.46.139:6346 0 0
1233320987 61.27.69.190:6346 0 0
1233320987 83.20.226.151:6346 0 0
1233320987 114.189.147.125:6346 0 0
1233320987 91.123.168.218:6348 0 0
1233320987 83.6.137.121:6348 0 0
1233320987 125.14.152.169:6346 0 0
1233320987 83.1.56.80:6348 0 0
1233320987 65.26.193.89:6346 0 0
1233320987 85.222.44.190:6348 0 0
1234523601 98.165.89.61:27152 2097152 8
1234523601 76.104.162.207:43822 131072 33
1234523601 124.179.98.192:13733 2097152 231


there is also an IRC that can help : 
#gift  on irc  Freenode


bye & gl


/  please .. can anyone give me new nodes for openft and fastrack ?

---

### Post by test3 (on suse) on 2009-02-17
up


i need new nodes for fasttrack  please anyone ?  ty:)

---

### Post by andoni on 2012-01-26
In light of recent unfortunate news, I think we should clean the dust off this old thread and begin sharing files again :D.

Anyway, does anyone know how to share files on giftoxic?

---

