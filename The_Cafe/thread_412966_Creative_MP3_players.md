---
title: "Creative MP3 players"
date: 2007-04-18
forum: The Cafe
---

### Post by maniacmusician on 2007-04-18
Does anyone here own a Create Vision:M or Creative Vision:W? My little brother is considering buying one, and he wanted to know how good the Linux support for it was. I think they would work with libmtp, but I haven't had a Creative player in a long time.

Most importantly, is you Creative experience with Linux positive? Is it easy to transfer songs back and forth? Any bugs?

Thanks.

---

### Post by FuturePilot on 2007-04-18
I have a Creative Zen MicroPhoto. It's an MTP player and I've gotten it to work with Gnomad2. I had to compile it though in order to get the MTP support. But in Feisty it works with Amarok out of the box. No need to compile anything.

There's another thing that I think is somewhat recent that I want to look into. It's called mtpfs. It allows you to view the contents of the player within any file manager.

---

### Post by urukrama on 2007-04-18
I have a Creative Zen Sleek Photo, which works perfect with Gnomad2 (there is a good howto on the forums to set this up properly). I haven't encountered any problems or bugs. Overall very happy, both with the player and its interaction with Ubuntu.

---

### Post by Biochem on 2007-04-18
I have a creative vision M and love it. And it work very well with Gnomad2 or Amarok.  And as FuturePilot pointed out they have to be compiled on version older than 7.04.

---

### Post by Swab on 2007-04-18
My sister has a Vision:M works fine with Gnomad2.. although I'm not sure if transferring video works.. It is however a very nice little player.

---

### Post by maniacmusician on 2007-04-18
> **Swab said:**
> My sister has a Vision:M works fine with Gnomad2.. although I'm not sure if transferring video works.. It is however a very nice little player.
Good point...how well does video transfer work? Is it as easy as music? Also, are there Linux-based tools to convert the video to whatever format is required by the Zen Vision?

---

### Post by picpak on 2007-04-18
I have a Creative MuVo V100...haven't tried it with any other apps, but it works great for copying files to it with Thunar.

---

### Post by macogw on 2007-04-19
I sync my Vision M with Gnomad2.  It works great.  I just tested video though, since you asked, and the .wmv I transferred wouldn't play the video (just sound).  I'm trying a .mpg now.  Okay .mpg works.

---

### Post by maniacmusician on 2007-04-19
> **macogw said:**
> I sync my Vision M with Gnomad2.  It works great.  I just tested video though, since you asked, and the .wmv I transferred wouldn't play the video (just sound).  I'm trying a .mpg now.  Okay .mpg works.
Good to know, thanks.

---

### Post by Biochem on 2007-04-19
Transfert of .avi and mpeg work well with gnomad but I couldn't figure out how to do it in amarok. However, while Creative's software will tell you if a video is supported or not, gnomad will not. So some video, like avi with ac3 sound or with higher definition will not play. In those cases, any video converter will do the job.

---

### Post by daynah on 2007-04-19
> **macogw said:**
> I sync my Vision M with Gnomad2.  It works great.  I just tested video though, since you asked, and the .wmv I transferred wouldn't play the video (just sound).  I'm trying a .mpg now.  Okay .mpg works.

I have put off buying a vision M due to the video worries. Now I want to upgrade my old creative!

---

### Post by macogw on 2007-04-19
I'm glad I tested that.  Now I can watch AFI music videos :D

---

### Post by forcesofhabit on 2007-04-19
I love my Creative Zen Microphoto... I just upgrade to Feisty though, and in the beta Gnomad2 worked right away, in the final however it just sits at "getting file metadata"

anyone having the same problem?

---

### Post by dday376 on 2007-04-30
> **forcesofhabit said:**
> I love my Creative Zen Microphoto... I just upgrade to Feisty though, and in the beta Gnomad2 worked right away, in the final however it just sits at "getting file metadata"

anyone having the same problem?

Same problem here.  Just installed from universe repo.  Here's what I'm getting on the command line:

```
Autodetected device "Creative Zen MicroPhoto" (VID=041e,PID=413c) is known.
PTP: Opening session
PTP ERROR IO: Trying again after resetting USB
inep: usb_get_endpoint_status(): Connection timed out
outep: usb_get_endpoint_status(): Connection timed out
usb_clear_halt() on IN endpoint: Connection timed out
usb_clear_halt() on OUT endpoint: Connection timed out
usb_clear_halt() on INTERRUPT endpoint: Connection timed out
usb_claim_interface(): Bad file descriptor
Connection error.
PDE device NULL.
```

Finally comes back saying no USB device detected.

---

### Post by deadlydeathcone on 2007-05-01
> **maniacmusician said:**
> Does anyone here own a Create Vision:M or Creative Vision:W? My little brother is considering buying one, and he wanted to know how good the Linux support for it was. I think they would work with libmtp, but I haven't had a Creative player in a long time.

Most importantly, is you Creative experience with Linux positive? Is it easy to transfer songs back and forth? Any bugs?

Thanks.

I've been thinking about buying a music player with good Linux support, and after looking around decided against the M because 1) the codec support is pretty bad (no ogg or flac support, and most videos have to be converted before they can be played) and 2) it uses the MTP protocol, which is still pretty experimental in Linux.

So far the best I've found is the [iAudio X5]("http://www.newegg.com/Product/Product.aspx?Item=N82E16855603828"), which is about the same price as the M but has much better codec support and is detected as an external drive when. The screen isn't as nice and it lacks the ability to sort files by id3 tag, but other than that it seems pretty great.

edit: I forgot the most important thing: the X5 runs [Rockbox]("http://www.rockbox.org/")! For this reason alone I'd go with the X5 or an iPod over the Creative.

edit 2: You might also want to check out [this site]("http://wiki.xiph.org/index.php/PortablePlayers").

---

### Post by lunarmelody on 2007-05-01
I've also had a problem with hanging.  I've started a thread about it here: [http://ubuntuforums.org/showthread.php?t=410634](http://ubuntuforums.org/showthread.php?t=410634)

---

### Post by ravanwin on 2007-06-03
> **Biochem said:**
> Transfert of .avi and mpeg work well with gnomad but I couldn't figure out how to do it in amarok. However, while Creative's software will tell you if a video is supported or not, gnomad will not. So some video, like avi with ac3 sound or with higher definition will not play. In those cases, any video converter will do the job.

Hi, I am a complete NEWBIE to Ubuntu and am using Ubuntu 7.04 Feisty Fawn and the GNOME desktop.

I am trying to get video to play on my vplus but, despite the fact that I can see video files I transfer via gonomad2 to my player, it always says, "file not supported". I thought the vplus supported .avi files? 

anyway, this post hints at a soloution so I make a plea for more explaination? Can you a good, user friendly, graphical converter? Also, how can I tell what files need converting? Should I assumer more typical .avi files need to be converted to a different type (?) of .avi file?

Thanks in advance for your help,
rvan

---

### Post by chombee on 2007-06-27
ravanwin -- ffmpeg and mplayer are two command-line programs for converting videos. As for graphical programs, there are several graphical interfaces for ffmpeg or mplayer, see this list of video conversion applications on gnomefiles:

[http://www.gnomefiles.org/subcategory.php?sub_cat_id=91](http://www.gnomefiles.org/subcategory.php?sub_cat_id=91)

I had a quick scan, avidemux looks like it may be the best.

But the problem is, what format are the videos you want to convert currently in? And what format do you want to convert them to?

---

### Post by macogw on 2007-06-27
> **deadlydeathcone said:**
> I've been thinking about buying a music player with good Linux support, and after looking around decided against the M because 1) the codec support is pretty bad (no ogg or flac support, and most videos have to be converted before they can be played) and 2) it uses the MTP protocol, which is still pretty experimental in Linux.

So far the best I've found is the [iAudio X5]("http://www.newegg.com/Product/Product.aspx?Item=N82E16855603828"), which is about the same price as the M but has much better codec support and is detected as an external drive when. The screen isn't as nice and it lacks the ability to sort files by id3 tag, but other than that it seems pretty great.

edit: I forgot the most important thing: the X5 runs [Rockbox]("http://www.rockbox.org/")! For this reason alone I'd go with the X5 or an iPod over the Creative.

edit 2: You might also want to check out [this site]("http://wiki.xiph.org/index.php/PortablePlayers").

The reason it can't sort by id3 tag is because it shows as an external drive.  Those just throw them into whatever folder you put them in.  MTP or whatever protocol iTunes uses exist because they interface with a database on player.  If it shows as an external drive, and you just copy and paste, there's either no database or if there is one, it's not going to be updated to let you sort.

Vive is a nice GUI for ffmpeg.

---

### Post by mendieta on 2007-11-04
Gutsy update: I have a bunch of avi's (some created from kmplayer when dumping radio, others created with a digital camera). In all cases, I fail to transfer them. 

Amarok sees the avi's . but when trying to copy them it gives an error message

```

Failed to copy track to media 
device: the_path_to_the_avi/FILENAME.AVI

```

GNomad2, OTOH, doesn't even show me my local avi's or mpg's in my local drive ... what am I doing wrong ?

Thank you!

---

### Post by mendieta on 2007-11-04
> **mendieta said:**
> 

GNomad2, OTOH, doesn't even show me my local avi's or mpg's in my local drive ... what am I doing wrong ?



Nevermind: I was looking in the "Music Transfer" Tab. The avi's only show in the "Data Transfer" Tab :)

---

