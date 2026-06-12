---
title: "A nice idea!! (read please)"
date: 2004-11-05
forum: The Cafe
---

### Post by iltommy on 2004-11-05
Recently on OSNEWS appeared a review of Ubuntu that deprecate the lack of an equivalent of K3B for Gnome.
Using K3B under GNome is not so great... really.
So, why don't work for a better and complete GnomeBaker ([http://www.gnomefiles.org/app.php?soft_id=291](http://www.gnomefiles.org/app.php?soft_id=291)) using the source (asking the author, of course) and an integration in Ubuntu??
It would be amazing!

 :-P

---

### Post by gamehack on 2004-11-05
I've joined Luke(the author of GnomeBaker) and helped him a little bit. I made a new splash screen(see atachment). I am also beta testing the upcoming 0.2 version, he has implemented D'n'D for Audio Files creation(you can drag mp3s from nautilus for example), new interface, new icons, save to ISO, write ISO image and many more :) If you're interested, please contact me on ICQ.

Cheers,
gamehack

---

### Post by iltommy on 2004-11-05
I'm interested...really!
But I've no ICQ...sadly  :-# 
Could you sende me a mail? I could help you a little!

---

### Post by diebels on 2004-11-05
This is very important work for the gnome and ubuntu desktop. Canonical should hire Luke to get a good version ready for hoary.  :D The only thing I miss in gnome is a k3b equilavent. The nautilus cd-burning thing is to limited. Having gnomebaker integrated into the filemenu in nautilus's burn: location would be nice.

---

### Post by Jspired on 2004-11-05
Some excellent ideas here.  I'd be willing to help.

---

### Post by iltommy on 2004-11-05
[QUOTE=Jspired]Some excellent ideas here.  I'd be willing to help.[/QUOTE]
me tooo....maybe beta-test? I'm not a skilled programmer!!  :cry:

---

### Post by FLeiXiuS on 2004-11-05
Excellent idea, I will reccomend this to higher staff.  If anyone has contact methods with the author please have them email me at [email]magnesix109@hotmail.com[/email] I would like to announce some good deeds.  Thankyou.

---

### Post by Lovechild on 2004-11-05
I'm more of a Coaster guy, it seems to be most in tune with GNOME2 ideals than anything I've seen thus far.

---

### Post by jdong on 2004-11-05
I want to see Nautilus CD Burner improvements. I think taking this Windows-XP-ish idea to the next level would be in our best interest. I want to see the cd creator show new menus for making audio CD's, copying cd's, etc. Hopefully GNOME 2.10 will have something of this sort.

---

### Post by diebels on 2004-11-06
Coaster looks very well integrated to nautilus. Looks almost like they're running [human theme](http://www.coaster-burn.org/coaster-gui/screenshots.html) too :)
Simpler interface. Maybe Gnomebaker isn't spatial enough for gnome. I like them both.

---

### Post by gamehack on 2004-11-06
I've contacted Luke and told him. Unfortunately, he was offline, so probably this night or these days he will contact FLeiXiuS and also come to this forum.

Cheers,
gamehack

---

### Post by im_ka on 2004-11-06
gnomebaker is a great app. 
needs some polishing, and if it'd incule dnd mp3/ogg audio cd burning, noone would mention k3b on this board anymore :)

---

### Post by FLeiXiuS on 2004-11-06
[QUOTE=gamehack]I've contacted Luke and told him. Unfortunately, he was offline, so probably this night or these days he will contact FLeiXiuS and also come to this forum.

Cheers,
gamehack[/QUOTE]

Thank you. :-)

---

### Post by gamehack on 2004-11-22
The release of 0.2 is out. D'n'D support was added, ogg support and a lot of things. You can read [here](http://www.biddell.co.uk/files/ChangeLog). Because we're searching for beta testers, please, can anyone interested send me an email at gamehack (at) 1nsp1r3d.co.uk

Thanks very much,
gamehack

---

### Post by salsafyren on 2004-11-23
[QUOTE=gamehack]I've joined Luke(the author of GnomeBaker) and helped him a little bit. I made a new splash screen(see atachment).

[/QUOTE]

Hi gamehack,

Your splash screen is nice. From a usability perspective, splash screens are not a goo d idea. They are often used when the underlying program is very slow (think Gnome startup, OpenOffice startup) and you want to make the user perceive that the program loads faster than it in reality is.

Please read this thread:

[http://mail.gnome.org/archives/usability/2004-October/msg00096.html](http://mail.gnome.org/archives/usability/2004-October/msg00096.html)

I want to help out on GnomeBaker, maybe adding DVD support, as I've heard that Luke does not own a DVD drive.

Regards,

Christoffer

---

### Post by mattyh on 2004-11-23
I finally took a look at the web site, and the screenshots look promising.  I'd like to help beta test if possible.  I had always wanted to look into programming a cd burning app for windows (a free one) since I'm interested in HCI (Human Centered Interface design) and even taking some classes on it.  So, if I could help in any aspect. I'd like to do so.

---

### Post by zenwhen on 2004-11-24
Until I can do this with GnomeBaker, I will need K3B:

---

### Post by tomtom on 2004-11-25
can anybody post a quick howto about installing gnomebaker.
i tried it yesterday..but i did not succeeded.
i got the message that libvorbis is missing, but actually its there..


thanks...

---

### Post by gamehack on 2004-11-25
The installation should be pretty straightforward...
```

./configure
make
make install

```

Probably I will make an Ubuntu package this weekend...

Cheers,
gamehack

---

### Post by tomtom on 2004-11-25
ok that would be nice ...thanks in advance:-)

---

### Post by gamehack on 2004-11-25
After I got back from school, I made a package. It's located at [http://www.1nsp1r3d.co.uk/files/](http://www.1nsp1r3d.co.uk/files/) It's compiled on the Hoary Development branch, so try to install it and tell me what happened.

Cheers,
gamehack

---

### Post by diebels on 2004-11-28
In current Hoary:
Burning an audiocd from wav files now. First it complained about a tmp directory not existing. So I made /tmp/GnomeBaker/$USER/create_audiocd/

Also asked me to insert blank cd when it was already inserted. Failed to start default(tao) writing mode. dao, raw96p, raw16 failed.

Run it with gksudo seems to work now. Same thing as with k3b.

Audio cd finished successfully, started burning the new gnoppix image now. Seems to work.

Would be smart to add raw96r too, think that mode is supported by lots of writers. My writer don't support raw96p or raw16.

---

### Post by lloyd on 2004-12-01
I tried the package, it worked like a charm. I could run Gnomebaker straight away. Unfortunately it seems that the cdrecord that it is based on is none too happy. It couldn't find my CD-drive. After mucking about for a bit with the README.ATAPI.setup, I thought I had found the solution to it by editing the /etc/default/cdrecord to contain

CDR_DEVICE=cdrw
cdrw=/dev/hdc

hdc being my cd-rom drive. The readme says that with this I should just be able to write 

sudo cdrecord -prcap

to get the drive working. Unfortunately, this doesn't work- (it says no CD-recorder specified) So I tried with an extra dev=hdc option, this got me this error message:

scsidev: 'hdc'
devname: 'hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
cdrecord: No such file or directory. Cannot open 'hdc'. Cannot open SCSI driver.

So the app can't find the drive, yet Nautilus manages the same just fine. I'm trying to burn a (test) music CD, so any help would be greatly appreciated. I am quite a newbie at linux so I hope that you can bear with the stupid questions. I have a sneaky suspicion that the answer to this may be quite simple.

Thanks,

Andreas

---

### Post by TravisNewman on 2004-12-01
OK the compiled version that I installed a while back works better than this package, I'm getting a couple of the same errors mentioned above by diebels. 

Could some of the issues be related to dependencies not being installed? Or were those just for compiling, and once compiled they're no longer needed?

However, when I compiled it myself, it didn't have the audio-cd tab. My question, gamehack, is do you know how to compile it with audio cd support? I really want to test it out and help make this work so maybe it can make it into Hoary, I just want a side by side comparison so I can see what messages are being spouted, etc. Thanks!

---

### Post by poofyhairguy on 2004-12-03
[QUOTE=gamehack]After I got back from school, I made a package. It's located at [http://www.1nsp1r3d.co.uk/files/](http://www.1nsp1r3d.co.uk/files/) It's compiled on the Hoary Development branch, so try to install it and tell me what happened.

Cheers,
gamehack[/QUOTE]

I tried your package, but even though I could get it to start, it wouldn't burn.

Gnomebaker needs more work. Its lack of menu options and right click options is a big deal. 

For now (as in the official Hoary release) I think Ubuntu should take a page out of Fedora's playbook:

Make an official K3B package and get it working as well as possible with the final version.

---

### Post by TravisNewman on 2004-12-03
Personally, I think Coaster would be a better burning solution, if you can burn Audio CDs. From the website, the feature set includes:
        * Audio cd sessions
        * Data cd sessions
        * File drag and drop from nautilus
        * Ability to save and restore sessions from file

However, no matter what I do I can't seem to get it to even start an audio cd session... I can't even find how to MAKE an audio cd, it just always seems to be in data mode. Other than that, it seems more mature and stable. If anyone has any clue how to burn audio cds, I'd love to know, and if it's possible, perhaps talking to the devs and getting them involved with Ubuntu, or getting Ubuntu devs involved with Coaster, would be a better way to go.

Just my opinion, and opinions are like noses, as they say, everyone has one.

---

### Post by gamehack on 2004-12-04
Well, I write Audio CDs without a problem. Check this [screenshot](http://www.biddell.co.uk/images/gnomebaker/gb02_02.jpg) out.  Do you have these dependencies?
```

It requires a recent version of cdtools (cdrecord, readcd, cdda2wav and mkisofs), version 2 or greater should be okay.
It needs mpg123, oggdec and sox for audio processing.
It also requires the libs libgnomeui-2.0 gtk+-2.0 libglade-2.0, libvorbis and libvorbisfile.

```

---

### Post by TravisNewman on 2004-12-04
Yeah in GnomeBurner I can burn audio cds, but I (and a few others) get funky errors sometimes.

What I was saying is that I think Coaster might be a better choice if it is possible to burn Audio CDs with Coaster.

But thinking about it now, any problems would get worked out long before an Ubuntu release, so it really doesn't matter.

---

### Post by leech on 2004-12-04
I just tried out the package, and while I could get it to run, it wouldn't detect my CD-ROM(S).  I ran it with gksudo and then it detected the CD-ROM(S) allright, but it also detected my hard drives... which is quite odd.  I have SCSI throughout my system (except for my external hard drive, which is an IDE drive inside a firewire case).  I didn't try burning anything with it yet though...  

I'm still trying to figure out how to get cdrecord to behave properly.  I'll also have to start a new thread on this... but I can't get Nautilus to do anything when I right-click on an ISO and select Write to disc.... 

Leech

---

### Post by kahping on 2004-12-04
not sure if this is related to the problems everyone is having:

[http://www.fokus.fhg.de/research/cc/glone/employees/joerg.schilling/private/cdrecord.html](http://www.fokus.fhg.de/research/cc/glone/employees/joerg.schilling/private/cdrecord.html)

... but it would seem to me that the root of all these problems lie in cdrecord and not the cdburning apps. says so on the official site: "Linux-2.6.8.1 breaks CD/DVD writing for suid root applications"

kahping

---

### Post by rwabel on 2004-12-18
thanks for the deb file. works also fine after starting it with gksudo and creating the needed tmp folders.

looks really great this tool. fast, simple and gnome ;-)

---

### Post by elocal on 2005-01-17
nice, I am trying burning some stuff right now...

---

### Post by elocal on 2005-01-17
[QUOTE=elocal]nice, I am trying burning some stuff right now...[/QUOTE]
 Cannot get audio working, I installed the dependencies except oggdec since it is not in ubuntu rep.

---

### Post by gamehack on 2005-01-18
[QUOTE=elocal]Cannot get audio working, I installed the dependencies except oggdec since it is not in ubuntu rep.[/QUOTE]
I will ask you to post all your experience and testing of gnomebaker on the mailing list. Or you can just file a bug  in the sf.net database. The site again is [http://gnomebaker.sf.net/](http://gnomebaker.sf.net/)

Cheers,
gamehack

---

### Post by nocturn on 2005-01-18
[QUOTE=diebels]This is very important work for the gnome and ubuntu desktop. Canonical should hire Luke to get a good version ready for hoary.  :D The only thing I miss in gnome is a k3b equilavent. The nautilus cd-burning thing is to limited. Having gnomebaker integrated into the filemenu in nautilus's burn: location would be nice.[/QUOTE]

Yes, it is very limited, and so far it has been the only component of my Ubuntu that frequently crashes...

---

