---
title: "Which is your fav CD/DVD Burner?"
date: 2012-02-02
forum: The Cafe
---

### Post by nrundy on 2012-02-02
With burners I look for these features:
1.) control over which File System (UDF vs ISO) is used to burn data discs.

2.) control of whether DiscAtOnce is used or not when making a data burn. 

3.) have the option to "Verify Data" after burning is completed. 

The only burner that I've found that meets these requirements to my satisfaction is NeroLinux. But it's not free and it's not open source. so it's a disappointment there.

Which burning software do you like best? If the one you like is not listed, please post it's name. I'm looking out for burners I'm not aware of.

---

### Post by CharlesA on 2012-02-02
Aww no ImgBurn.

I don't think I've actually burned a cd in Linux.

---

### Post by Simian Man on 2012-02-02
People still use CDs?

---

### Post by CharlesA on 2012-02-02
> **Simian Man said:**
> People still use CDs?
The only thing I use them for is music for my car, everything else is thumb drives/over the network.

---

### Post by TeoBigusGeekus on 2012-02-02
I don't trust any of these; they seem to work whenever they want.
I only use growisofs and wodim.

---

### Post by Perfect Storm on 2012-02-02
Added 'Other' to the poll. 


Voted NeroLinux. Never failed me which can't be said about the other options.

---

### Post by Linuxratty on 2012-02-02
Brasero works for me.

---

### Post by yetiman64 on 2012-02-02
I do like to use Brasero and XFBurn. Unfortunately never had any luck burning video dvds with them, so my vote has to go to NeroLinux (like AI mentions, never failed a burn for me, on any burn type as well).

Only problem for me with NeroLinux3 is it uses gtk2 libraries and now I'm on 11.10 only have the gtk3 stuff which the installer fails because of #-o. Ah well, time to spend about $15 to upgrade to NL4 by the looks of it ;).

---

### Post by wolfen69 on 2012-02-02
> **Artificial Intelligence said:**
> 


Voted NeroLinux. Never failed me which can't be said about the other options.

Voted K3B. Never failed me which can't be said about the other options. ;)

K3B has all of those options that the OP desires. But we all have our favorite. I just can't see paying for burning software, when there are *many* free options.

---

### Post by mips on 2012-02-03
K3B & NeroLinux.

---

### Post by nrundy on 2012-02-03
> **CharlesA said:**
> Aww no ImgBurn.

I don't think I've actually burned a cd in Linux.
ImgBurn is only avail on Windows, right?


> **TeoBigusGeekus said:**
> I don't trust any of these; they seem to work whenever they want.
I only use growisofs and wodim.
Does Wodim have a "Verify Data" option? I always have so much trouble trying to learn command line stuff though. I can never remember the dang commands. It ends up taking me a lot longer than using GUI stuff.

---

### Post by TeoBigusGeekus on 2012-02-03
> **nrundy said:**
> Does Wodim have a "Verify Data" option? I always have so much trouble trying to learn command line stuff though. I can never remember the dang commands. It ends up taking me a lot longer than using GUI stuff.
I don't think it does.

For cd burning, see this:
[https://wiki.archlinux.org/index.php/CD_Burning#Command-line_CD-burning]("https://wiki.archlinux.org/index.php/CD_Burning#Command-line_CD-burning")
For dvd burning, see this:
[https://wiki.archlinux.org/index.php/DVD_Burning]("https://wiki.archlinux.org/index.php/DVD_Burning")

---

### Post by m_duck on 2012-02-03
Wodim here too.

---

### Post by desnaike on 2012-02-08
k3b has never failed me.

---

### Post by Old_Grey_Wolf on 2012-02-08
I rarely burn a CD or DVD anymore. When I do I use Brasero. I tend to use USBs these days.

---

### Post by JustinR on 2012-02-08
Deepburner
k3b
Brasero

---

### Post by meduser on 2012-02-19
Well, I don't know what I am doing wrong. I am trying to burn a copy of a movie. The file is in AVI format. I have tried K3B, get instant error. I have tried Brasesro, same issue. I have tried NeroLinux, and get same issue. As soon as I click burn, I get an error, and the DVD ejects. I am trying to put family movies over to DVD. They play just fine in VLC as an AVI, but as soon as I try to burn..get an error. I am sure I am missing something that needs to be installed. any help is appreciated.
Nero says burn process failed. It doesn't even start to burn the file:p

Thanks

---

### Post by yetiman64 on 2012-02-19
> **meduser said:**
> Well, I don't know what I am doing wrong. I am trying to burn a copy of a movie. The file is in AVI format. I have tried K3B, get instant error. I have tried Brasesro, same issue. I have tried NeroLinux, and get same issue. As soon as I click burn, I get an error, and the DVD ejects. I am trying to put family movies over to DVD. They play just fine in VLC as an AVI, but as soon as I try to burn..get an error. I am sure I am missing something that needs to be installed. any help is appreciated.
Nero says burn process failed. It doesn't even start to burn the file:p

Thanks
You may need to look at a program like devede to make a video dvd. 

The video dvd format needs mpeg2 files in a size of 720x576 and if I recall correctly 25 fps (for PAL DVD). Devede can create the necessary format from other filetypes (avi, mkv etc) and create the dvd disk structure and save as a VIDEO_TS folder or as an iso image your software mentioned above can burn to a disc.

There are other apps for making dvds besides devede, it is what I use here.

---

### Post by infestor on 2012-02-20
> **desnaike said:**
> k3b has never failed me.

this^

---

### Post by TeoBigusGeekus on 2012-02-20
> **meduser said:**
> Well, I don't know what I am doing wrong. I am trying to burn a copy of a movie. The file is in AVI format. I have tried K3B, get instant error. I have tried Brasesro, same issue. I have tried NeroLinux, and get same issue. As soon as I click burn, I get an error, and the DVD ejects. I am trying to put family movies over to DVD. They play just fine in VLC as an AVI, but as soon as I try to burn..get an error. I am sure I am missing something that needs to be installed. any help is appreciated.
Nero says burn process failed. It doesn't even start to burn the file:p

Thanks

Do you want to create a video dvd or a data dvd with avi's in it so you can play it on a divx capable dvd player?

---

### Post by blueturtl on 2012-02-20
mkisofs, wodim & cdrdao

---

### Post by blueturtl on 2012-02-20
> **nrundy said:**
> Does Wodim have a "Verify Data" option? I always have so much trouble trying to learn command line stuff though. I can never remember the dang commands. It ends up taking me a lot longer than using GUI stuff.

Wouldn't you use md5sum on the ISO and also on the burnt disc to verify? I dunno, I usually don't bother with the verification part...

---

### Post by 14quartz on 2012-02-20
But my friend always saying DC/DVD cannot be burned successfully in ubuntu....Not sure. Need to give a try.

---

### Post by Erik1984 on 2012-02-20
K3B is very versatile. It' s good for burning but also for ripping audio.

---

### Post by zaentzpantz on 2012-02-20
I've used K3B once and it worked but after a lot of evaluation work I have taken all my audio/video applications back to Windows XP and just use Ubuntu for office, internet & email:
TMPGEnc
EAC
MP3tag
WinFF
Nero Express for most burning.

---

### Post by stalkingwolf on 2012-02-20
in windows i use nero.  in all linux distro's i use i use k3b. converting movies to iso i use devede.

---

### Post by odiseo77 on 2012-02-20
K3B. As others have said, it never fails. I even used it when I used Gnome.

---

### Post by pbpersson on 2012-02-20
> **odiseo77 said:**
> k3b. As others have said, it never fails. I even used it when i used gnome.

+1

---

### Post by CivilizationII on 2012-02-20
K3B, the reliability is impressive.

---

### Post by meduser on 2012-02-23
> **TeoBigusGeekus said:**
> Do you want to create a video dvd or a data dvd with avi's in it so you can play it on a divx capable dvd player?

I would like to make a video dvd. 

I try K3b, and it runs for all of 2 seconds, and I get an error. I also have tried Brasero. Same thing. I add the image which I created using ffmpegx. It plays just fine in VLC..sound and video is awesome. I have tried both AVI and ISO and get the same reaction each time.

My burner is a brand new..ok not brand new..I have used it twice since I bought it 2 weeks ago. It is a LG MODISC, supermulti. It can right DVD's just fine. It is a SATA drive also. Fully detected in Kubuntu...I have installed the "restricted " stuff after a clean install of Kubuntu 11.10. and still have the same issue. I have also tried Devede with the same result. It is like I don't have the right setting for it. 
I am a newbie with Linux, and have only been using it for 4 weeks.

Any, help getting this too work would be greatly appreciated.
 Thanks you in advance.
Med

---

### Post by TeoBigusGeekus on 2012-02-24
> **meduser said:**
> I would like to make a video dvd. 

I try K3b, and it runs for all of 2 seconds, and I get an error. I also have tried Brasero. Same thing. I add the image which I created using ffmpegx. It plays just fine in VLC..sound and video is awesome. I have tried both AVI and ISO and get the same reaction each time.

My burner is a brand new..ok not brand new..I have used it twice since I bought it 2 weeks ago. It is a LG MODISC, supermulti. It can right DVD's just fine. It is a SATA drive also. Fully detected in Kubuntu...I have installed the "restricted " stuff after a clean install of Kubuntu 11.10. and still have the same issue. I have also tried Devede with the same result. It is like I don't have the right setting for it. 
I am a newbie with Linux, and have only been using it for 4 weeks.

Any, help getting this too work would be greatly appreciated.
 Thanks you in advance.
Med

Open a terminal and try with this command
```
growisofs -Z /dev/sr0 -dvd-video /path/video1 /path/video2 /path/video3
```
etc.
Replace /dev/sr0 with whatever applies to your system (/dev/dvd/, /dev/cd, /dev/cdrw, etc.)

---

### Post by mihalybaci on 2012-02-24
I generally burn DVDs with Gnomebaker, but I use k9copy when ripping DVDs because you can shrink the size of the ISO to fit on cheap standard 4.7 GB DVDs.

---

### Post by -jay- on 2012-02-24
i voted other because everytime i burn a data cd of my flac files the file names end up being renamed

---

### Post by meduser on 2012-02-24
when I type:

 sudo hdparm -I /dev/dvd


it returns```

/dev/dvd:

ATAPI CD-ROM, with removable media
        Model Number:       HL-DT-ST DVDRAM GH22NS90                
        Serial Number:      KFGB9G85408         
        Firmware Revision:  HN00S300
        Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
        Likely used CD-ROM ATAPI-1
Configuration:
        DRQ response: 50us.                                                                                            
        Packet size: 12 bytes                                                                                          
        cache/buffer size  = unknown                                                                                   
Capabilities:                                                                                                          
        LBA, IORDY(can be disabled)                                                                                    
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    PACKET command feature set
           *    Look-ahead
           *    DEVICE_RESET command
           *    NOP cmd
                Removable Media Status Notification feature set
           *    64-bit World wide name
           *    Gen1 signaling speed (1.5Gb/s)
           *    Phy event counters
                Asynchronous notification (eg. media change)
           *    Software settings preservation

```

Is that right for my DVD burner. It is the only one hooked up to my pc.

It is definitely a burner. 

Thanks again. I think I should just start a new post, as I have hyjacked this one. So sorry.

\Med

---

### Post by TeoBigusGeekus on 2012-02-24
Have you tried with the command I gave you?

---

### Post by meduser on 2012-02-24
> **TeoBigusGeekus said:**
> Have you tried with the command I gave you?
yes I did, but it returned errors saying that it could not find the audio or video file. I checked the path location, and copied it over, and I tried an ISO of a movie, and got the same thing.

I am currently burning the iso with K3B, which is working for the first time. I converted the avi file using devede, and it seems happy. I'll see in a few minutes.

---

### Post by meduser on 2012-02-24
> **meduser said:**
> yes I did, but it returned errors saying that it could not find the audio or video file. I checked the path location, and copied it over, and I tried an ISO of a movie, and got the same thing.

I am currently burning the iso with K3B, which is working for the first time. I converted the avi file using devede, and it seems happy. I'll see in a few minutes.

Well, it seems to be burning, however, my DVD player (Sony BluRay) sees it as a DVD-r, but says it can play it. I know the DVD player can play burnt movies as I have kids and have backed up there DVD's. I let them watch their burnt copies, and the originals are put away. That way they don't get damaged. So I am stumped.

---

### Post by meduser on 2012-02-24
Hmmm...trying again, only this time I have NTSC checked instead of pal...

---

### Post by Bachstelze on 2012-02-24
Whatever the OS I'm using comes with. :p

*EDIT:* Well, no, not in Windows because Wndows's built-in burning thing is terrible, I use InfraRecorder or ImgBurn in it. But I don't use Windows often...

---

### Post by meduser on 2012-02-24
> **TeoBigusGeekus said:**
> Have you tried with the command I gave you?

This is what I get from that command when I try to burn from an Iso..:
```

Executing 'genisoimage -dvd-video /home/xxxxxxx/xxxxxxxxxxx/xxxxxxxxxxxx.iso | builtin_dd of=/dev/dvd obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Could not find correct 'VIDEO_TS' directory.
genisoimage: Unable to make a DVD-Video image.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents
:-( write failed: Input/output error

```

Am I at least on the right track?

When using K3B, is says Burning ISO image (2.2gib)

Is that right or is this making an image for the pc?

---

### Post by meduser on 2012-02-25
So, I started a new thread for my troubles.
The link is here if anyone feels the urge to help me out.

[http://ubuntuforums.org/showthread.php?p=11717284#post11717284](http://ubuntuforums.org/showthread.php?p=11717284#post11717284)

---

### Post by soryu on 2012-02-28
which one will also write track info so that it shows in the display when playing?
the song title.

---

### Post by meduser on 2012-03-08
Now that I have it working, I have been using both Devede for converting, and k3b to burn the disc. Works great.

---

### Post by MisterGaribaldi on 2012-03-09
A microscope, a flashlight, a really big and powerful magnifying glass, and a pair of steady hands.

Why? Doesn't *everyone* do it that way?

---

### Post by synaptix on 2012-03-09
My vote goes to K3B, it's an awesome and powerful burner that I use for all my DVDs. One of the first things I install on a fresh install of Ubuntu. :)

---

### Post by lewisgoddard on 2012-03-10
Most of my CD/DVD burning is either Live Disc ISOs (ubuntu, mint, etc.) or rendered DVD ISOs (from [DeVeDe]("http://www.devede.org/")). As such i use Braseo because of the simplicity. I think there is literally two buttons, then three if i haven't bothered to blank the disc (i usually don't).

In two click i've started.

K3B is my backup option, only complaints are the messy interface (not messy really, just not so clean cut) and having to install loads of KDE dependencies.

---

