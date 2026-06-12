---
title: "HOWTO: Get your ESI MAYA 44 to work"
date: 2008-07-23
forum: Tutorials
---

### Post by Patryk Krawczyk on 2008-07-23
In This tutorial, I will describe how to install ESI MAYA 44 PCI under UBUNTU 8.04
   
ESI MAYA 44 driver was made by Rainer Zimmerman, thanks to initiative of Piotr Zaryk. I just made update, against new alsa-driver source code. Unfortunately, nobody knows if this patch whenever become official part of alsa, because Rainer didn't sign-off his driver and contact with him was lost. If you want see this patch merge, in the next release of alsa-driver, please write a message on [alsa-driver mailing list]("http://www.alsa-project.org/main/index.php/Mailing-lists").

Turn on terminal and type the following code:
```

cd; mkdir maya44; cd maya44
wget http://prl-quakewars.ovh.org/maya44patch-alsa-driver-1.0.17.diff.tar.gz
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.17.tar.bz2
```

Extract patch and alsa-driver-1.0.17:```

tar -xjf alsa-driver-1.0.17.tar.bz2
tar -xvzf maya44patch-alsa-driver-1.0.17.diff.tar.gz
``` 

Apply patch by typing:
```
patch -p0 < maya44patch-alsa-driver-1.0.17.diff
```

Download dependencies:
```
sudo apt-get install build-essential
```

Configure and make alsa-driver:```

cd alsa-driver-1.0.17
./configure --with-cards=ice1724 --with-sequencer=yes ; make
```

If everything goes well, you can install new driver by typing:
```

sudo make install
```

Restart your system and enjoy your ESI MAYA 44 sound card under Linux.

Forgive me my poor english

-----

Here's a patch for UBUNTU 8.10 beta against [alsa-driver-1.0.18rc3]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18rc3.tar.bz2"):

[esi_maya44-alsa-1.0.18rc3.diff.tar.gz]("http://prl-quakewars.ovh.org/esi_maya44-alsa-1.0.18rc3.diff.tar.gz")

In attachment, I add patch against current version of ALSA.

---

### Post by sonnet on 2008-08-07
Thank you very much!
I followed your card and it worked perfectly!
Thanks again I was waiting for more than one year.

---

### Post by Tobisc on 2008-08-16
Hello!
 I have the maya 44 card in my pc with Ubuntu Studio 8.4 64bit.
 I follow the tutorial but in the "Configure and make alsa-driver:" step, the kernell directory was wrong...
 Reading the INSTALL file of the alsa package, I find out the "Kernel Source Tree" option but i dont' now how carry on.
 Can you, Patryk or anyone help me?

PD: My knowledge in Linux & programming is cero! Je... But i really I want to use my mayya 44 in ubuntu.


Sorry for my terrible inglish and thanks!

---

### Post by Crafty Kisses on 2008-08-16
Awesome this really helped my friend out.

---

### Post by Patryk Krawczyk on 2008-08-16
> **Tobisc said:**
> Hello!
 I have the maya 44 card in my pc with Ubuntu Studio 8.4 64bit.
 I follow the tutorial but in the "Configure and make alsa-driver:" step, the kernell directory was wrong...

Are you sure that you have kernel-headers installed?

Try this:
```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by Tobisc on 2008-08-16
Thank you very much!!! It works!
Now i go to play a wile whith my maya in linux!

Thanks again!

---

### Post by Tobisc on 2008-08-17
Someone have an idea of how i do to jack set the 4 inputs of the maya44? Only two are set as "capture_1" & "capture_2" but from the alsa mixer can hear fours.
When i try to configure four "inputs channels" in "setup", jack dont' start...
Apparently wh:0 are the two first inputs and hw:01 the others two (input device in jack setup) but two divaces at time is no possible.


Thanks for help!!!

---

### Post by Tobisc on 2008-08-17
Ha... Jack dont' see the midi usb controller...
some idea?

Thanks!

---

### Post by Patryk Krawczyk on 2008-08-17
I'm afraid that I can't help you with this. I think that the best what you can do is write a message on alsa-driver mailing list. Maybe there is somebody who can help you solve this problem(I'm afraid that driver doesn't support those function yet)

[http://www.alsa-project.org/main/index.php/Mailing-lists](http://www.alsa-project.org/main/index.php/Mailing-lists)

---

### Post by Tobisc on 2008-08-17
Thanks anyway for your help Patryk!
 You are talking about the "inputs" problem or the "midi controller" problem?

cheers!

---

### Post by Patryk Krawczyk on 2008-08-18
About both of them.

---

### Post by RIV@NVX on 2008-08-25
> **Patryk Krawczyk said:**
> I'm afraid that I can't help you with this. I think that the best what you can do is write a message on alsa-driver mailing list. Maybe there is somebody who can help you solve this problem(I'm afraid that driver doesn't support those function yet)
Speaking of MIDI, what is the output of "amidi -l"?

---

### Post by Patryk Krawczyk on 2008-08-25
> **RIV@NVX said:**
> Speaking of MIDI, what is the output of "amidi -l"?

```
patryk@patryk-desktop:~$ sudo amidi -l
Dir Device    Name
patryk@patryk-desktop:~$ 
```

Output is empty, but I don't have this add-on card:

[IMG]http://i27.photobucket.com/albums/c182/xselthor/midi1.jpg[/IMG]

---

### Post by cb951303 on 2008-09-30
does anyone know if "changing input from line in to mic" and "+48v phantom power" features work with this driver?

---

### Post by Sylvertwyst on 2008-10-05
hello all, 

i tried installing the maya44 using the howto posted here, and the install went pretty smooth, though i did have to install the kernel header like tobisc did.  however, after restarting i am not able to produce any audio, through the usb card or built in audio device whatever.

you probably need more information, like config settings and what not, but i don not know how to produce these, so if someone would tell me how to, i'llglady post htem :D

i'm pretty clueless as i only recently started exploring linux and ubuntu, and i rely heavily on power users like yourself that are kind enough to help the likes of me.

If the system cant be configured to be able to choose between in built and external soundcard at one time, i'd rather just have the inbuilt and leave audio production my windowsXP software.

thank you very much for your time in advance

Sylver

---

### Post by Patryk Krawczyk on 2008-10-06
I'm sorry Sylvertwyst, but this tutorial is about ESI MAYA 44 PCI not USB version.

---

### Post by Sylvertwyst on 2008-10-06
oh. that seems to be the problem... my bad, i should have read more carefully...  

in any case, could you tell me how to roll back to my original alsa configs? everything worked good right out of the box, so i thought about reinstalling alsa, but even after reinstalling every alsa related package that i could find in synaptic the problem still remains...

Thank you for replying though

Sylvertwyst

---

### Post by Patryk Krawczyk on 2008-10-08
Try this:
[link]("https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20the%20ALSA%20drivers%20from%20a%20*fresh*%20kernel")
> I installed alsa from source, and wanted to revert so I wouldn't have to reinstall alsa everytime the kernel moved. The above did not work for me. Here's a safer way that did.

sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

That re-grabs all of the alsa binaries and modules. You may also need to

ls -lt /lib/modules/`uname -r`/kernel/sound/

And delete anything from the day you manually installed alsa. 

---

### Post by musical-linux on 2008-10-17
Yesterday I try this HOWTO
but I did a mistake...
My card is the regular
Maya44 PCI and not the
ESI...this is a problem for
me since my ubuntu does not
see my old card anymore as well
as the Maya44.

I need to undo this change!!

---

### Post by fauri on 2008-11-02
Hi

In Ubuntu 8.04, this patch works perfectly, but in 8.10 I don't get good results... With patch for 1.0.17, a error occurs, and with patch for 1.0.18rc3, compiles fine, but don't works after restart the system. Any suggestions?

Thanks, and sorry for my poor english (I'm Brazilian).

---

### Post by Patryk Krawczyk on 2008-11-05
This is strange, because I'm using this patch with 8.10 and everything works good.

```
cd; mkdir maya44; cd maya44
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18rc3.tar.bz2
wget http://prl-quakewars.ovh.org/esi_maya44-alsa-1.0.18rc3.diff.tar.gz
tar -xjf alsa-driver-1.0.18rc3.tar.bz2
tar -xvzf esi_maya44-alsa-1.0.18rc3.diff.tar.gz
patch -p0 < esi_maya44-alsa-1.0.18rc3.diff
sudo apt-get install build-essential
cd alsa-driver-1.0.18rc3
./configure --with-cards=ice1724 --with-sequencer=yes ; make
sudo make install
```

---

### Post by fauri on 2008-11-06
Then there is a hope! :)

In the old version (8.04), I used the following line:
> sudo apt-get install linux-headers-`uname -r`

...Otherwise did not work

In Ubuntu 8.10 I'm still using this command, and the remainder is equal to your code.

I will try again! Thanks for the answer!

---

### Post by fauri on 2008-11-06
It worked! \\:D/

I installed Ubuntu again, and this time I not used the linux-headers in the process. Works fine!

Thanks for your attention, Patryk!

---

### Post by isaacctk on 2008-12-14
great work thanks a lot. 
when ubuntu updates the kernel (maybe alsa is updated also), it will tend to overwrite the driver, but i just follow the commands step again and it still works.

---

### Post by oldrust on 2008-12-29
hello. I have an Audiotrak Maya44 MkII. can you tell me if this procedure works also for my card?
thank you.

---

### Post by floydbarber on 2009-01-17
I also had an Audiotrak maya44mkII.
Is there anyone who get it works?
thank's

---

### Post by sonnet on 2009-01-23
How could install this patch if I have installed alsa 1.0.19? It's the procedure the same?

---

### Post by serg78 on 2009-03-04
I begin to make driver for my Audiotrak MAYA44MKII, but this is difficult for me. I found some info about this card:

It based on Envy24HT-S main chip, same as ESI MAYA44, but codec chips wm8731 used instead wm8776 on ESI MAYA44. 

His pci subdevice id is 0x30315441.

Driver developers, help!

---

### Post by Adaon on 2009-03-16
> **Patryk Krawczyk said:**
> Here's a patch for UBUNTU 8.10 beta against [alsa-driver-1.0.18rc3]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18rc3.tar.bz2"):

[esi_maya44-alsa-1.0.18rc3.diff.tar.gz]("http://prl-quakewars.ovh.org/esi_maya44-alsa-1.0.18rc3.diff.tar.gz")

Successfully works with 9.04 Jaunty alpha.

Thank Rainer and Patryk again.

---

### Post by Kramar Zaibatsu on 2009-03-18
I have tried to compile the 1.0.17 version and 1.0.18rc3 with a 2.6.27.19-3.2-default kernel and failed both times.

this is what I get upon make:

...
/usr/src/linux-2.6.27.19-3.2/include/asm-generic/memory_model.h:78:1: warning: this is the location of the previous definition
/home/kramar/maya44/alsa-driver-1.0.18rc3/acore/memory_wrapper.c: In function ‘snd_compat_vmalloc_to_page’:
/home/kramar/maya44/alsa-driver-1.0.18rc3/acore/memory_wrapper.c:44: error: implicit declaration of function ‘VMALLOC_VMADDR’
/home/kramar/maya44/alsa-driver-1.0.18rc3/acore/memory_wrapper.c:49: warning: passing argument 1 of ‘pmd_offset’ from incompatible pointer type
/home/kramar/maya44/alsa-driver-1.0.18rc3/acore/memory_wrapper.c:50: error: implicit declaration of function ‘pte_offset’
/home/kramar/maya44/alsa-driver-1.0.18rc3/acore/memory_wrapper.c:50: warning: assignment makes pointer from integer without a cast
make[4]: *** [/home/kramar/maya44/alsa-driver-1.0.18rc3/acore/memory_wrapper.o] Error 1
make[3]: *** [/home/kramar/maya44/alsa-driver-1.0.18rc3/acore] Error 2
make[2]: *** [_module_/home/kramar/maya44/alsa-driver-1.0.18rc3] Error 2
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.27.19-3.2'
make: *** [compile] Error 2


what could it be? :shock:

---

### Post by madforthenet on 2009-03-24
Hi guys I' Guido from Italy.
I have uninstalled a card similar from an old pc of a friend the model is the same MAYA M44-MKII but the manufacter is Audiotrack with pci connection.
Can you tell me if the two models is the same or similar ?
If yes can I use the same tips to install it on Ubuntu Studio 8.0.4.2 LTS with 2.6.24-23 RT Kernel ?
Thanks in advance for your answer and please be patience for my language.
BYE

---

### Post by madforthenet on 2009-03-25
Hello I have another question:this tutorial is valid also for the latest alsa driver 1.0.19 or not ?
I have read on web that Audiotrack is a division of ESI then two cards are the same ?!. At the moment AudioTrack has discontinued MAya 44 MKII PCI ,ESI this model is also available.
Bye

---

### Post by madforthenet on 2009-03-27
> **serg78 said:**
> I begin to make driver for my Audiotrak MAYA44MKII, but this is difficult for me. I found some info about this card:

It based on Envy24HT-S main chip, same as ESI MAYA44, but codec chips wm8731 used instead wm8776 on ESI MAYA44. 

His pci subdevice id is 0x30315441.

Driver developers, help!

Hi, refer to this post I have the same card.
I have just installed driver with tips in this tutorial , but seems to be not installed.
If I take a look into Ubuntu device manager card exist, but if I open a console and execute 
```

guido@ENTERPRISE:~$ asoundconf list
Names of available sound cards:
Intel

guido@ENTERPRISE:~$ lspci
04:01.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
        Subsystem: Unknown device 3130:4154
        Flags: medium devsel, IRQ 17
        I/O ports at ec00 [size=32]
        I/O ports at e880 [size=128]
        Capabilities: <access denied>

guido@ENTERPRISE:~$ sudo lspci -d 1412:1724 -nvx 
[sudo] password for guido: 
04:01.0 0401: 1412:1724 (rev 01)
	Subsystem: 3130:4154
	Flags: medium devsel, IRQ 17
	I/O ports at ec00 [size=32]
	I/O ports at e880 [size=128]
	Capabilities: [80] Power Management version 1
00: 12 14 24 17 01 00 10 02 01 00 01 04 00 40 00 00
10: 01 ec 00 00 81 e8 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 30 31 54 41
30: 00 00 00 00 80 00 00 00 00 00 00 00 0a 01 00 00

```
the only device in list is Intel, that is on-board audio card of my mobo Intel P5K-SEand  system seems rcognized the card, but it doesn't work and I don't found any control panel for device
I try to repeat all step by step more times, but I haven't any positive result. I'm not able to find the panel where is possible adjust input and output of my Audiotrack maya44-MKII so I think:

-Do I make some errors ?t I don't know how to find it

- the esi and audiotrack maya44-mkII probably are not the same card how serg78 wrote on post I quote 
Can someone who can help me to found my errors if exist and solve this problem ?
Thanks 
Guido

---

### Post by floydbarber on 2009-03-29
Hi Guido, I also have tried some times ago with no results.
Audiotrak's Maya44 is not supported for now (this is my final opinion). I hope serg78 is able to help us, so, by the way, good luck serg!



P.s.: I am italian too. Please contact me if you find something interesting...

---

### Post by madforthenet on 2009-03-30
Hi floydbarber 
I'm happy to encounter you here "outside Italy" 
I hope too that someone help us to solve this or better that new alsa driver version support these cards officially!!
 have Audiotrack Mayy44MKII is it the same of ESI ?
Audiotrack is a division of ESI , but how can we sure ?
See later
bye

---

### Post by alexdsp on 2009-06-18
Hi guys! My name is Alex, i`m from Russia. Excuse for my english.

Does anybody make capture audio from all 4 channels? Is it possible really? 
Recently, i have installed Esi Maya44 patch against alsa 1.0.19 drivers, and almost everything works, but capture from channels pair hw:1,1

---

### Post by ezio_rec on 2009-06-19
Hi guys, I'm Ezio, from Italy...
 
Ubuntu studio jaunty 9-04 on my pc...
 
musicante@lo-ez:~$ uname -r
2.6.28-3-rt
 
Alsa version : 1.0.18rc3
 
Patch for esi maya 44 pci works fine. Thanks a lot guys....
 
If you have usb devices i.e. midi keyboards or controllers, in order to preserve the snd-(usb) modules (snd-usb-audio, snd-usb-lib, snd, snd-pcm, ......)
 
$./configure --with-cards=ice1724,[COLOR=red]usb-audio[/COLOR] --with-sequencer=yes
 
I don't know how to preserve the "midi through" virtual ports but I don't need them now...
Byes,
Ezio.

---

### Post by Patryk Krawczyk on 2009-07-03
Hi everybody. There's hope.

This is message from alsa-devel mailing list:
> Since there is no progress regarding this, I hacked and almost
completely rewrote the code to support Maya44.

Dany, could you test alsa-driver-unstable snapshot tarball?
    [ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz)

Note that this is generated from sound-unstable GIT tree which
contains the patches in topic/maya44 branch:
    git://git.kernel.org/pub/scm/linux/kernel/git/tiwai/sound-unstable-2.6.git


If the driver is confirmed to work, I'm going to merge the patches to
the upstream.


Thanks,

Takashi

[link]("http://mailman.alsa-project.org/pipermail/alsa-devel/2009-May/017067.html"). 

[Alsa-devel -- Alsa-devel mailing list]("http://mailman.alsa-project.org/mailman/listinfo/alsa-devel")


If you can, please write a feedback on alsa-devel, maybe this is the end of our problems.

---

### Post by Tobisc on 2009-08-31
Alleluia! Alsa driver 1.0.21 Support Maya 44!!!!
 
Thanks Alsa developers and all that help with this.-

[http://www.alsa-project.org/main/index.php/Changes_v1.0.20_v1.0.21#ICE1724_driver]("http://www.alsa-project.org/main/index.php/Changes_v1.0.20_v1.0.21#ICE1724_driver")

---

### Post by Adaon on 2009-09-02
Thank Gods

---

### Post by descendent87 on 2009-09-03
So the maya 44's now/will soon work out the box? Is this PCI/PCIe version or both?

---

### Post by Paleorama on 2009-09-23
Hi, I've got a Maya44 USB soundcard - any chance you would know how to get this to work on ubuntu?
I would really appreciate your help!

---

### Post by Tropcon on 2009-09-29
Paleorama,

I just read on a forum (link below) that the Maya44 USB is plug-&-play as of intrepid.

 [http://www.mixxx.org/forums/viewtopic.php?f=1&t=408]("http://www.mixxx.org/forums/viewtopic.php?f=1&t=408")
________________

I am looking to get the PCIe version of this card, but don't want to spend $150 without being sure that it's going to work.

Does anyone know if the Maya44e is supported?

---

### Post by cek on 2009-09-30
Also curious if this supports the PCIe version.

---

### Post by dson_asianhip on 2009-10-12
cd alsa-driver-1.0.17
./configure --with-cards=ice1724 --with-sequencer=yes ; make
After this code received "[compile] Error 2". Please help me

---

### Post by North-E on 2009-10-24
> **dson_asianhip said:**
> cd alsa-driver-1.0.17
./configure --with-cards=ice1724 --with-sequencer=yes ; make
After this code received "[compile] Error 2". Please help me
Hey, probably, try the later version of alsa-driver:
```
ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.19.tar.bz2
```and apply the first patch attached to the topic called [**esimaya44patch-alsa-1.0.19.diff.tar.gz**]("http://ubuntuforums.org/attachment.php?attachmentid=107276&d=1237745056").
I had the similar problem with alsa-driver-1.0.17 but this one works fine. ;)

---

### Post by ciroyo on 2009-10-24
hey,

i downloaded the files alsa-driver-1.0.19 tar.bz2 and esimaya44patch-alsa-driver-1.0.19.diff.tar.gz and afterwards i tried out to install it via TERMINAL under my ubuntu but it doesn't work. i'm completely new in the linux world and i'm sorry for perhaps stupid questions but i don't know the way to install the tar-files. i tried out the pathway, [_[COLOR=Black]Patryk Krawczyk  wrote on july 23th 2008 (with changed version 1.0.19) but it doesn't work after restart. [/COLOR]_]("http://ubuntuforums.org/member.php?u=629043")

now my question: what do i wrong? can someone help me with the installation? i really would like to use my ESI maya 44 E118 soundcard under ubuntu.

cheers ciroyo
[[COLOR=Black][/COLOR]]("http://ubuntuforums.org/member.php?u=629043")

---

### Post by Gliderfm on 2009-10-27
I have this card too. The internal Maya 44e. Worked fine on Vista with my DVR setup
but I upgraded to RTM Win 7 and now I can't get the vid and audio to sinc. I new I had a problem with this card on windows but I wonder what will happen when I put Ubuntu
on this box. I contacted ESI and they said drivers for 7 were being delveloped but when is another question. And that's for windows. I want it for Buntu so I'll try the above driver most likely.:-&

---

### Post by Tropcon on 2009-10-27
Cool. Please let us know how it works out. :)

(especially phantom power. Has anyone tested phantom power on these cards?)

---

### Post by sync_0 on 2009-11-02
Hi, All!
And what is about newest ubuntu 9.10? Here is my situation: I've upgraded from ubuntu 9.04 and it played sounds "out of box", but I have no input and only one output ( no line-in, no mic, no headphone out). As I uderstand, newest ubuntu comes with alsa 1.0.20, I've upgraded to alsa 1.0.21 (latest) compiled with ./configure --with-cards=ice1724 --with-sequencer=yes   options, with no result. Any ideas?

UPDATE: Now I found out, that I have all controls in alsamixer but not in gnome-volume-control, therefor the question is how to add these controllers to gnome.

---

### Post by Thomas1983 on 2009-11-09
Hello,

i (linux newbie) am trying to install the MAYA44 (Pci) version for 2 long nights...

Alsa (1.0.21)+lib+utils seems correctly installed, i checked out all the tips on several websites, 
got all the packages, no errors on compiling, compiled with the ice1724 drivers, got the modules loaded using modprobe... all fine, its just the card simply is NOT recognized at all!

[FONT=Fixedsys]cat /proc/asound/cards
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with ALC650F at irq 20[/FONT]

just my on-board card is seen (and is also configurable in alsaconf etc.).

[FONT=Arial][FONT=Fixedsys]lspci | grep audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
02:09.0 Multimedia audio controller: Hint Corp Unknown device 1012 (rev 01)
02:09.1 Multimedia audio controller: Hint Corp Unknown device 1013 (rev 01)[/FONT]
[/FONT]  
this last one seems like the maya 44 to me... but somehow alsa seems to have no clue!
Tried under ubuntu 8.04 and 9.10... same problem, tried different pci slots... nothing... card works ok under windows XP.

Help anybody?

thanks Thomas

---

### Post by Thomas1983 on 2009-11-09
Oops, I had to read the previous posts with more attention...
my card is also from Audiotrak, and now i understand it's not supported at all...
aiai, what a waste of time.... and good luck serg78 :)

---

### Post by Orange Kingdom on 2009-11-10
Hi,

Have you tried this driver?:
[http://www.intilinux.com/driver/942/scheda-audio-esi-maya44-driver-per-linux/](http://www.intilinux.com/driver/942/scheda-audio-esi-maya44-driver-per-linux/)

You have to patch it first.
Make sure you have the ALSA kernel driver compiled.

---

### Post by Thomas1983 on 2009-11-12
Orange,

do you mean this driver will also work for *audiotrak* MAYA44 (and not only for *esi* MAYA44, as the link says?)

greetings Thomas

---

### Post by Tropcon on 2009-11-12
Thomas1983,

That's an interesting question. I had never heard of Audiotrak before, but they are listed on the [ALSA compatible soundcard list]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-AudioTrak"). However, as you can see by following the link, there is no mention of Audiotrak having a MAYA44 card. I went to the Audiorak website, and sure enough, they *did* make a [MAYA44 MKII]("http://www.audiotrak.net/products/maya44mkii/") soundcard. However, at the bottom of of the Audiotrak page, it says: > MAYA44 MKII has since been replaced by the new ESI version of [MAYA44]("http://www.esi-audio.com/products/maya44/").The [ESI MAYA44]("http://www.esi-audio.com/products/maya44/") and the [Audiotrak MAYA44 MKII]("http://www.audiotrak.net/products/maya44mkii/") cards apear to be quite similar, but there are small differences (e.g. the Audiotrak has 12v phantom power, whereas the ESI has 48v.)
Both cards seem to have the same chipset though (ICE controller chipset), and with one simply being a newer version of the other, I find it quite possible to think that this ESI driver may work with the Audiotrak MAYA44 MKII (but it might require some tweaking.)

So did ESI just buy this card from Audiotrak, or what??

---

### Post by Thomas1983 on 2009-11-14
Tropcon,

It appears Audiotrak is a Korean subdivision of ESI.... 

> **Tropcon said:**
> . However, as you can see by following the link, there is no mention of Audiotrak having a MAYA44 card.

it seems they do have one: [COLOR=Indigo][[COLOR=DarkOrchid]Audiotrak Maya44[/COLOR]]("http://ixbtlabs.com/articles/audiotrakmaya44/index.html") (<--link) [/COLOR]
The card I have never mentioned "MKII" on the box, or in the drivers, still, my card looks on the outside much more like a MKII than the one seen in the link (maybe some transition-model???)

anyway. "normal MAYA44" or MKII,  it seems impossible (for me, that is) to run Audiotrak with the new alsa drivers (1.0.21 with MAYA44 support) or the older versions (with the patch), this was mentioned before in this tread....

> **floydbarber said:**
> Audiotrak's Maya44 is not supported for now (this is my final opinion).

Alsa simply won't recognise the card. Too bad, because, like you say, the ESI and Audiotrak cards appear very similar.

I gave up on it too, maybe there will be support in the future...

---

### Post by Tropcon on 2009-11-14
> It appears Audiotrak is a Korean subdivision of ESI...

Oh, okay. That makes sense.

> ..maybe there will be support in the future...

It's possible, but I wouldn't count on it. It looks to be quite discontinued. I wonder how easy, or hard, making it work would be though... the cards can't be *that* different.

That's what I love about Linux; anything's possible. You just have to wait for it to happen...

(just like how I'm still waiting for someone to tell me if the phantom power works on the PCIexpress version of the ESI...) :)

---

### Post by sonnet on 2009-11-16
Hi guys, I had the maya44 PCI card which worked out of teh box with Karmic.
The I replaced the card with the Maya44e (because of the midi output) but this doesn't work out of the box with Karmic. What can I do?
I had installed the alsa driver 1.0.21 but it seems that when I run alsaconf the card is not seen from the driver, as I can olny select 
ati hd driver (???)

---

### Post by Festern on 2009-12-08
Maya 44 works out-of-the-box with 9.10 Karmic Koala, but
I can't select both input and output devices
I've got "ESI Maya Analog Stereo" listed in input devices when switching to Analog Stereo Input mode, but it hides Maya from output devices.
In Analog Stereo Duplex should be listed both input & output
devices but they're not.

---

### Post by alexdsp on 2010-01-20
Hello! I can`t switch on phantom power +48v in the default kernel  2.6.32 driver.
Does anybody have such experience as me?
(And probably there some mess in the other mixer parameters)
All stuff working correctly only with the patch [esimaya44patch-alsa-1.0.19.diff.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=107276&d=1237745056") from this forum (page 1). But with current kernel driver do not work.

---

### Post by blackslide on 2010-03-01
Hello to all,

First post on the forum and allready I'm looking for help :/

I'm not sure what to do, I'm looking for a lightweight DAW suitable OS and at the moment I'm thinking of dumping 64studio and building it from scratch on debian 5.0 or the newest ubuntu release. I've got a basic P45 dualcore setup with the ESI Maya44 PCI card. I love the low latencies / price ratio on this unit :D

If anyone has any hints on how to get this working on 64studio 3.0 beta3 I would appreciate the help. Otherwise it looks like a swap to something that works out of the box...

So I installed the OS, everything else works fine but alsa doesn't find the sound device, I quickly found this thread and tried the help on page1, well, no go. Didn't have build-essential installed and I couldn't find it on the CD either... I went through all the trouble of connecting the unit to the internet and apt-get install build-essential, but no go. It complained about dependency issues, libc6-dev was conflicting with libc-dev, complains about '/usr/include/scsi/scsi.h' needing to be overwritten. I don't even want to know why and how that is possible. I got past that by dpkg --force-overwrite.

Now I have gcc g++ and make, so far so good. Nah, try to build alsa 1.0.17, complained about headers and the sorts, seems this OS uses the 2.6.29-1-multimedia kernel, I download the kernel and get the next error: "Makefile_32.cpu directory or file does not exist" Umm.. what? So I go into /usr/src/linux..... and there's absolutely nothing but a few folders in the whole headers package. So I went back to synaptics and got 2.6.26 common and multimedia and just plain copied everything from there manually. Still no go, now it starts doing something but it complains about wrong arguments and the sorts in the log and gives make [2] and make [1] errors. The errors mostly relate to memory wrapper and cpuinfo_x86 but I have no clue where to go from here. This all starts to seem like something impossible to do

I've tried compiling alsa 1.0.17, 1.0.22.1 and 1.0.17 with the .diff patch, all give the same errors. Something is amiss but I've dropped the ball.


Any help appreciated, and nice to join the forum!
Kristjan

---

### Post by blackslide on 2010-03-01
Thought of edit, but since this is kind of long.. here goes:

I went and rolled over the 64studio install with the 5.0.3 Lenny in hopes of getting the card to work.

I Built the ALSA 1.0.19 drivers, config and install both went through, rebooted unit.
Ran alsaconf, found a "ice1724 VIA technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel..." driver/card and it stopped in the end with: "/usr/sbin/alsactl: save_state:1497: No soundcards found..."
At the same time it still claims "Now ALSA is ready to use."
Well, it doesn't work, doesn't even find a soundcard..

Ran the 1.0.19.diff patch after this... and it didn't find the files to patch?
It was looking for 3 different folders and several makefiles under 'alsa-driver-1.0.19/alsa-kernel/' wich simply doesn't exist, renaming the 'alsa-firmware-1.0.19/' to the 'alsa-driver-1.0.19/', made no difference

Skipped the missing files with 'Enter' and built the driver
It looked like it worked like it should, restarted unit, still nothing.
Ran alsaconf, alsaconf finds the card "ice1724 VIA technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel..."
After it was ready to configure the sound levels etc, it gave the same error as before. No soundcards found...

I'm still in the same spot. I wonder what I'm doing wrong. It can't be that hard..
I dread the idea of going back to Windows 7 although I do have a legal copy of ultimate...

Any help appreciated,
Kristjan

Edit: Oookay, now I do feel dumb, downloaded the correct 'alsa-driver-1.0.19' package and all the headers for the 2.6.26-2 kernel and everythnig worked after a patch > build > install > restart..

Thanks for a great guide, hope someone learns from the mistakes I've made :/

---

### Post by sonnet on 2010-04-21
wan anybody able to make it  work the Maya44e (the new one which mounts in pcie slot)?

---

### Post by Dj_Tiago_D on 2010-07-22
hi i need help with the installation of my maya 44, when running make I got this error

 / Home/tiago/maya44/alsa-driver-1.0.18rc3/acore/info.c: In function 'snd_info_entry_prepare':
/ Home/tiago/maya44/alsa-driver-1.0.18rc3/acore/info.c: 161: error: 'struct proc_dir_entry' has no member named 'owner'
/ Home/tiago/maya44/alsa-driver-1.0.18rc3/acore/info.c: In function 'snd_info_register':
/ Home/tiago/maya44/alsa-driver-1.0.18rc3/acore/info.c: 1003: error: 'struct proc_dir_entry' has no member named 'owner'
make [3]: ** [/ home/tiago/maya44/alsa-driver-1.0.18rc3/acore/info.o] Error 1
make [2]: ** [/ home/tiago/maya44/alsa-driver-1.0.18rc3/acore] Error 2
make [1]: ** [_module_/home/tiago/maya44/alsa-driver-1.0.18rc3] Error 2
make [1]: Leaving directory `/ usr/src/linux-headers-2.6.31-22-generic '
make: ** [build] Error 2

someone help me?

---

### Post by Bag of Paper on 2010-07-28
> **Patryk Krawczyk said:**
> In This tutorial, I will describe how to install ESI MAYA 44 PCI under UBUNTU 8.04
   
ESI MAYA 44 driver was made by Rainer Zimmerman, thanks to initiative of Piotr Zaryk. I just made update, against new alsa-driver source code. Unfortunately, nobody knows if this patch whenever become official part of alsa, because Rainer didn't sign-off his driver and contact with him was lost. If you want see this patch merge, in the next release of alsa-driver, please write a message on [alsa-driver mailing list]("http://www.alsa-project.org/main/index.php/Mailing-lists").

Turn on terminal and type the following code:
```

cd; mkdir maya44; cd maya44
wget http://prl-quakewars.ovh.org/maya44patch-alsa-driver-1.0.17.diff.tar.gz
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.17.tar.bz2
```Extract patch and alsa-driver-1.0.17:```

tar -xjf alsa-driver-1.0.17.tar.bz2
tar -xvzf maya44patch-alsa-driver-1.0.17.diff.tar.gz
```Apply patch by typing:
```
patch -p0 < maya44patch-alsa-driver-1.0.17.diff
```Download dependencies:
```
sudo apt-get install build-essential
```Configure and make alsa-driver:```

cd alsa-driver-1.0.17
./configure --with-cards=ice1724 --with-sequencer=yes ; make
```If everything goes well, you can install new driver by typing:
```

sudo make install
```Restart your system and enjoy your ESI MAYA 44 sound card under Linux.

Forgive me my poor english

-----

Here's a patch for UBUNTU 8.10 beta against [alsa-driver-1.0.18rc3]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18rc3.tar.bz2"):

[esi_maya44-alsa-1.0.18rc3.diff.tar.gz]("http://prl-quakewars.ovh.org/esi_maya44-alsa-1.0.18rc3.diff.tar.gz")

In attachment, I add patch against current version of ALSA.

Hey guys, im new to Ubuntu and have no idea what any of this coding is, but i want to be able to use my Maya 44 USB with ubuntu, any help would be absolutely great as i really need to use it record mixes! thanks

---

### Post by Tropcon on 2010-07-28
Bag of Paper,

Good news! All the fancy code is for getting the Maya 44 *PCI* to work.
For the USB version, you just plug it in and it works fine (or, so I hear.) I've never used a USB audio device with Ubuntu, so I can't say where to go from there, but it should just work.

---

### Post by Bag of Paper on 2010-07-28
> **Tropcon said:**
> Bag of Paper,

Good news! All the fancy code is for getting the Maya 44 *PCI* to work.
For the USB version, you just plug it in and it works fine (or, so I hear.) I've never used a USB audio device with Ubuntu, so I can't say where to go from there, but it should just work.

I tried this the first time and it didnt work, i think its because i need the ASIO drivers. Are they available for Ubuntu? I did a google search but didnt have too much luck

---

### Post by Tropcon on 2010-07-29
ASIO? Are you trying to use it with a windows program running on WINE? If I remember correctly, ASIO is a windows driver that people have been able to mod to get low latency audio on WINE. Unless you're using a windows program, you shouldn't need ASIO. The inputs/outputs should just come right up in ALSA and JACK.

It might help to know what exactly you're trying to do with this thing, what programs you're trying to use and what your experience has been so far.

You may also want to try starting a new forum thread. All the people who want to help are usually looking for new threads. This one is rather old.
This thread is also for the PCI card. Talking about the USB one is a little off-topic. :)

---

### Post by Dj_Tiago_D on 2010-07-29
someone who makes a topic of how to install maya 44 usb because I think there are some doubts

---

### Post by Bag of Paper on 2010-07-29
> **Tropcon said:**
> ASIO? Are you trying to use it with a windows program running on WINE? If I remember correctly, ASIO is a windows driver that people have been able to mod to get low latency audio on WINE. Unless you're using a windows program, you shouldn't need ASIO. The inputs/outputs should just come right up in ALSA and JACK.

It might help to know what exactly you're trying to do with this thing, what programs you're trying to use and what your experience has been so far.

You may also want to try starting a new forum thread. All the people who want to help are usually looking for new threads. This one is rather old.
This thread is also for the PCI card. Talking about the USB one is a little off-topic. :)


Ok well i found a thread before about the USB maya 44 and there were no replies, so i figured this would be a better outlet to get some help, yes slightly off topic, but ive been trolling the internet for days trying to get this to work.

Basically I don't know what WINE, ALSA or JACK is. I've installed Ubuntu to use on my netbook for general use as well as at university and i'm in the process of building a PC for production (windows). I'm completely new to ubuntu and so i've got no idea how it works really, i'm running Ubuntu 10.4. 

In the meantime i want to use my ESI maya 44 USB to record mixes on Ubuntu. When i plug it in the lights come on internally but no sound comes out, i went to to system > sound > hardware and the maya 44 doesnt show up.

thanks

---

### Post by Tropcon on 2010-07-30
Well, you can always open a terminal and type in " lsusb ". This is short for "List USB," and it will give you a list of everything your computer sees plugged into your USB ports. " aplay -l " will also list all of your sound cards. You can also try getting JACK running and see if the inputs/outputs appear in there. Other than that, I don't know that I can help you much more. At this point it may be time to start a new thread and hope that someone else who actually has maya44usb finds you.

PS. I sent you a private message explaining WINE, JACK and ALSA.

I stumbled across another forum that might have the solution. It's here: [http://www.uluga.ubuntuforums.org/showthread.php?p=8887622](http://www.uluga.ubuntuforums.org/showthread.php?p=8887622)
Apparently, you just need to set the Maya 44 usb to be the default sound card so that ALSA will use it instead of the one inside your computer. If it's on-board, you can usually disable it in BIOS, if not you could always see what you can do with this forum: [http://www.linuxquestions.org/questions/linux-hardware-18/default-sound-card-in-ubuntu-564006/](http://www.linuxquestions.org/questions/linux-hardware-18/default-sound-card-in-ubuntu-564006/)

Bad memories of trying to use dual sound cards are staring to come back to me... good luck!

---

### Post by kokoshmusun on 2011-04-12
What is the recent situation?  I'm about to purchase the ESI Maya44 and I haven't been able to understand clearly whether it works completely (or partially, e.g., phantom power can't be switched on) or not in linux. Does anyone know for sure?

---

### Post by krzakx on 2011-07-28
> **kokoshmusun said:**
> What is the recent situation?  I'm about to purchase the ESI Maya44 and I haven't been able to understand clearly whether it works completely (or partially, e.g., phantom power can't be switched on) or not in linux. Does anyone know for sure?

I have similar questions but I want to get work MAYA 44 USB, this is recongized by ubuntu 9.10 plug and play.
How its works in real ?

---

### Post by Tropcon on 2011-07-28
Krzakx,

So, there are three MAYA44 devices. PCI, PCI-E and USB. The PCI version, apparently, works fine. The PCI-E version... well, I don't know. No one's said anything here yet.
Those two cards are the topic of this thread, and I believe the post you quoted was referring to the PCI-E edition.

The MAYA 44 USB is a different story. It's been plug & play for years (since Intrepid.) Shouldn't have a problem.

---

### Post by krzakx on 2011-08-14
> **Tropcon said:**
> 
The MAYA 44 USB is a different story. It's been plug & play for years (since Intrepid.) Shouldn't have a problem.

Ther is problem, check this please [http://ubuntuforums.org/showthread.php?t=1787616](http://ubuntuforums.org/showthread.php?t=1787616)

---

### Post by kokoshmusun on 2011-09-06
I got the ESI Maya44 PCI and it works under linux.  But I haven't been able to take advantage of it fully, as I found it difficult to set up a linux audio distro.  Right now, I'm trying xubuntu + KXStudio but there are still problems.

---

### Post by oldvelvet on 2012-05-12
well, thanks to this post, i will finally install ubuntu in my computer!!!!

Many thanks to all of you!

---

### Post by krzakx on 2012-05-13
> **oldvelvet said:**
> well, thanks to this post, i will finally install ubuntu in my computer!!!!

Many thanks to all of you!

Do you have MAYA PCI or USB?

---

### Post by realJedi on 2013-04-23
I have the Maya 44 XTe (PCIe) and didn't get it running yet. Still hope for solutions, because I really want to use Ubuntu, otherwise I have to keep using Windows :(

---

