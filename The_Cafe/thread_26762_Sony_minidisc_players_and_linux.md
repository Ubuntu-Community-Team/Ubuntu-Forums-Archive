---
title: "Sony minidisc players and linux?"
date: 2005-04-13
forum: The Cafe
---

### Post by darkoptix on 2005-04-13
I have this sony minidisc playerthat i got for 25 bucks CANADIAN in fairly good shape. I've been tring to sell for awhile, and thought "hey, maybe i should use it." 

Now, using this device in windows was near impossible to use(maybe the reason i'm tring to sell it). Installing in windows took a long long time for some strange reason, and the program it installs is anti userfriendly. Man, sony doesn't know about making software. I tried to install through cxoffice with no luck.

Then I thought is there any open source projects that would let me record to it, or am i stuck tring to sell the beast.

---

### Post by dcast on 2005-04-13
It might work I have an mp3 player which just mounts as an external harddrive. Do minidiscs use mp3 or the sony compression because i doubt that linux has support for sony compression.

---

### Post by 23meg on 2005-04-13
they use ATRAC compression, and ATRAC is Sony's proprietary format, so us poor NetMD owners are out of luck.

your best bet is to try to run Sonicstage via WINE, but... you should know better that Sony's apps can hardly run on windows  :-D 

SONY = :evil:

---

### Post by MasonM on 2005-04-13
You'll probably have an easier time selling it than making it work.  :razz:

---

### Post by darkoptix on 2005-04-13
stupid me has never tried sonic stage... however does it need openMG to install?

---

### Post by 23meg on 2005-04-13
yes, it needs the openmg secure module, but not the openmg jukebox app. if you have vmware for linux you can give it a go. it will certainly run Sonicstage, but i've never tried using usb devices via vmware so i don't know if it would be able to handle the actual transfer of data correctly. and even if everything worked 100% well it would still be quite a hassle to boot a virtual machine just for one task.

---

### Post by totalshredder on 2005-04-13
how does sonic stage work on wine? I have an ATRAC player as well, and It'd be cool to get it to work.

Luke

---

### Post by TravisNewman on 2005-04-13
One thing you can do is just plug it into the line out of your sound card and do direct recording-- not as easy, and it takes as long to record as it would to play, but if that's the only way you can get it to work, it DOES work.

---

### Post by poofyhairguy on 2005-04-14
[QUOTE=panickedthumb]One thing you can do is just plug it into the line out of your sound card and do direct recording-- not as easy, and it takes as long to record as it would to play, but if that's the only way you can get it to work, it DOES work.[/QUOTE]


I second this. It isn't that bad. I used to do that in Windows when I messed with minidiscs. Better than Sony's software...

---

### Post by darkoptix on 2005-04-14
Well I just found out to get sonic stage requires downloading, however it's not one big package, just a download utility :(. Ill "attempt" to get it downloaded, however i'll do this on my windows partition because I'm on dialup. Getting the new sonicstage would be nice, so I could listen to some tunes at school...

I'll also check out vmware, because on some minidisc forum it said you could try it with sonicstage... Booting into a vm wouldn't be that hard as long as worked. Unlike windows.

The idea of just plugging into the line-out sounds great, as I do think there are linux programs that allow editing through usb(also read on minidisc forum). So setting spliting into tracks wouldn't be that bad.

I gave up tring to install OpenMG in linux, as the installers would not run, so I booted up windows... I installed everything on the cd that came with the player... and of course didn't work at all... that's windows combined with sony for you.

---

### Post by 23meg on 2005-04-14
sony is ridiculously bad when it comes to software. i mean, some other companies that keep their code closed are at least able to write software that works with their hardware products; it's *their* products after all, huh? but sony is unable to do that. if they opened their sources people would come up with many times better software than what sony has managed to make in three years within a few months.

---

### Post by kanem on 2005-04-14
maybe there's something useful here:

[http://tuxmobil.org/player_linux_survey_sony.html](http://tuxmobil.org/player_linux_survey_sony.html)

---

### Post by andlinux21 on 2005-06-30
Well I just bought a Sony NETMD NE410 for 40 bucks the 5 pack of discs for $8 at Frye's Electronics.  Man this little thing rocks and the battery life is great just wish it had DC in so you could plug it up while transferring songs.  The software sucks but I guess I will have to try VMware to see if I can use this on Ubuntu will let you know how it goes...

---

### Post by tristan on 2005-06-30
I used Minidiscs for a number of years, and while they are definitely nice hardware, the software absolutely sucks. Windows only, bloated and buggy. I've a HiMD which can be recognised as an external USB 1.1 HD under linux, but although files can be transferred (slowly) between linuxbox and MD, music definitely can't (and never will be knowing sony). 

In the end I got so sick of having to record everything in real time that I put the MD in the cupboard and bought a 2nd hand Zen Touch - perfect!

Sony have completely dropped the ball with MD by being to uptight about rights management and proprietary codecs. If they'd come up with a MD mounted as a USB2 drive and allowed any OS to drag and drop mp3, ogg, etc files and then play them, then I'd be tempted. They never will though, so I don't bother with it any more. 

A shame...

---

### Post by andlinux21 on 2005-06-30
tristan I understand but after my iPod died (firewire port problems) i wasn't about to spend another 200 bucks for a player. Creative has a couple of players out that are like 50 - 60 bucks US but I wanted more than 256M of space and to be able to have a variety of music without having to erase and load each time I wanted to hear pop, jazz, house/techno etc. so I have to try to get this to work in linux even if its vmware.

---

### Post by tristan on 2005-07-01
[QUOTE=andlinux21]tristan I understand but after my iPod died (firewire port problems) i wasn't about to spend another 200 bucks for a player. Creative has a couple of players out that are like 50 - 60 bucks US but I wanted more than 256M of space and to be able to have a variety of music without having to erase and load each time I wanted to hear pop, jazz, house/techno etc. so I have to try to get this to work in linux even if its vmware.[/QUOTE]

Sorry about the rant andlinux2, I just get crapped off with sony for not allowing me to properly utilise my preferred format under my preferred OS.

Best of luck getting things running under emulation. I guess if vmware, win4lin etc have decent USB support you actually stand a chance of getting it working. And they are cheaper than a new HD player (although you can get pretty amazing deals on 2nd hand stuff). The trouble is it's pretty substandard software even running natively...

---

### Post by andlinux21 on 2005-07-01
Yeah you are right about the software its crap times like this i wish i knew more about programming.

---

### Post by RastaMahata on 2005-07-01
I've HEARD that RealProducer records in ATRAC...
[http://www.realnetworks.com/products/producer/basic.html](http://www.realnetworks.com/products/producer/basic.html)

good luck

---

### Post by geokker on 2005-08-02
The very prospect of getting sonic stage to work on Linux shivers me timbers. Sony stuff is eye-wateringly proprietary which is a downer, as the NW-507 is lush.

---

### Post by mike998 on 2005-08-02
I have a MZ-N420D Net MD MiniDisc Player.
It's amazing!  The battery life is wonderful (I listen to it for about 3 hours a day, to and from work and in the gym) and I can store about 5 hours of music on each disc.
BUT...
I have spend a lot of time on and off trying to find a way to transfer music to the MiniDisc player.  The version I have does not have a line in, it's USB only, and thus I have to use SonicStage.
Real Player on Windows has a plugin that enables me to transfer music to it without using sonic stage, but as far as I can tell, it's windows only.

The Linux solutions as far as I can tell are, to pick a word, stinky.  They maybe allow for changing the TOC, and perhaps taking songs OFF the player (if the planets are in alignment, you have made the correct sacrifices and the gods are happy).  
It's not a slight on the developers, in fact they are to be applauded, they have managed to get Sony's god-awful proprietary solution and do something with it.  Sony seems to be listening to the audience's complaints as I have heard that newer devices will allow transfer of mp3s and allow the minidisc player to be mounted as a USB drive.  Doesn't help me much, eh?

Sorry for the rant, but I have really looked into this and haven't had much success at all.   ](*,)

---

### Post by geokker on 2005-08-02
I used to have an N10 Sony minidisc player. It was awesome. I sold it and bought an iRiver - I've never looked back - nothign beats plugging into *any* OS and dragging and dropping files.

(Having said that, I would have bought an iPod if they had a radio.)

---

### Post by zutronius on 2007-07-27
I love my minidisc players, but am frustrated about being unable to use them with Linux. I guess I'll have to build a Windows PC.

---

