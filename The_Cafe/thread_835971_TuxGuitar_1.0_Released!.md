---
title: "TuxGuitar 1.0 Released!"
date: 2008-06-21
forum: The Cafe
---

### Post by isaacj87 on 2008-06-21
One of my favorite projects has finally reached 1.0 status! When I first got hooked onto Ubuntu/Linux, I had to let go of one of my favorite programs - Guitar Pro. So, I immediately went searching for a Linux alternative and I found TuxGuitar. This was about a year ago, and nothing was moving. I figured the project was dead (albeit, it had a lot of potential). I'm really glad that they are continuing to work on this fantastic program.

For the uninitiated... TuxGuitar will read *.gp3, *.gp4, and *.gp5 files (GuitarPro files) that contain guitar [tablature]("http://en.wikipedia.org/wiki/Tablature"). These file can be found on sites such as [http://ultimate-guitar.com/]("http://ultimate-guitar.com/"). This is great for people who want to learn how to play the guitar and/or learn how to play their favorite songs. Plus, *.gpx files can also contain tablature for other instruments (bass, vocals, drums, etc.). On top of that, TuxGuitar (the idea taken from GuitarPro), plays back the song in real-time midi (sounds pretty good) so the listener can hear the musical notes and read the score. Pretty cool stuff.

Oh, BTW, if your adventurous you can make your own tabs too. I think :)

For those who use TuxGuitar/know of it... It seems a lot of bugs have been fixed and there's a good deal of polish to the program now. Plus, the midi problem is not here anymore (not for me at least). You don't have to fiddle around with Timidity and run this and that program to get the sound working. Seems to be working out of the box now!

I encourage guitarists to check it out. Debs are readily available. Here's the link: [http://www.tuxguitar.com.ar/]("http://www.tuxguitar.com.ar/") 

I've included a screenshot for kicks.

:guitar:

---

### Post by zachtib on 2008-06-21
sweet... I like to download tabs, mute the guitar tracks, and play along :)

---

### Post by sonicb00m on 2008-06-21
Thanks for the heads up. I've been running GP in wine, which is ok.

JUst installed Tux 1.0 and it's looking very nice. Excellent GUI. Playing back gp files perfectly it seems.

Don't you just got a soft warm feeling inside when an open source project hits v1.0 and the functionality is awesome :D

---

### Post by isaacj87 on 2008-06-21
> **sonicb00m said:**
> Thanks for the heads up. I've been running GP in wine, which is ok.

JUst installed Tux 1.0 and it's looking very nice. Excellent GUI. Playing back gp files perfectly it seems.

Don't you just got a soft warm feeling inside when an open source project hits v1.0 and the functionality is awesome :D

Definitely :D

Hey, just a question (since I haven't used GuitarPro in quite some time), what are some noticeable difference between the two? Are there some features missing or is TuxGuitar pretty much on par?

---

### Post by LookTJ on 2008-06-21
I hope you don't mind. I don't know anything about tab programs. so I ask you to turn this into a tuxguitar file format. 

[http://www.ubuntuboxes.co.uk/looktj/files/music/cripplingmachine.txt](http://www.ubuntuboxes.co.uk/looktj/files/music/cripplingmachine.txt)

---

### Post by atomkarinca on 2008-06-21
> **isaacj87 said:**
> Hey, just a question (since I haven't used GuitarPro in quite some time), what are some noticeable difference between the two? Are there some features missing or is TuxGuitar pretty much on par?

First of all, they made a major change in the GUI. After GP5 hit, they added .gp5 support. There are a few additions to noting (like displaying chords). Now you can export to Lilypond, which makes it just delicious.

I love this application and recommend it to every Guitar Pro user I know because most of them pirate GP. This is better than GP (GP lacks Power Tab and Lilypond support) and it's free.

---

### Post by boomtisk on 2008-06-21
Does the team have any plans to include real drums/percussion notation? As it is, it's kind of like the way they did it in Power Tab. Other than that, it's a great program.

---

### Post by isaacj87 on 2008-06-21
> **boomtisk said:**
> Does the team have any plans to include real drums/percussion notation? As it is, it's kind of like the way they did it in Power Tab. Other than that, it's a great program.

My guess is no. I wouldn't be surprised if they did though. That's the beauty of open-source, being able to cater to the user's needs. :D

---

### Post by isaacj87 on 2008-06-21
> **Taylor said:**
> I hope you don't mind. I don't know anything about tab programs. so I ask you to turn this into a tuxguitar file format. 

[http://www.ubuntuboxes.co.uk/looktj/files/music/cripplingmachine.txt](http://www.ubuntuboxes.co.uk/looktj/files/music/cripplingmachine.txt)

I could give it a shot, but there isn't any discernible rhythm/count/etc. I'd have to hear it being played first.

---

### Post by RiceMonster on 2008-06-21
Awesome! I love this project as well. When I switched to Linux I thought I was going to have to live without Guitar Pro, which was pretty hard since I used it so much. Turns out I was wrong.

> GP lacks Power Tab and Lilypond support
In GP5 you can use .ptb files. I believe it has to change it to .gp5 format first though.

---

### Post by www.rzr.online.fr on 2008-06-24
FYI, you can use my repository to fetch deb with apt :

  [http://rzr.online.fr/q/tuxguitar](http://rzr.online.fr/q/tuxguitar)

---

### Post by Casper Hansen on 2008-07-18
I've installed it, but the sound doesn't work. Can anyone help?

---

### Post by atomkarinca on 2008-07-18
Install timidity:

```
sudo apt-get install timidity
```

now you should be able to select it from the preferences. If still you can't then before you start TuxGuitar do these on terminal:

```
sudo modprobe snd-seq
timidity -iA
```

---

### Post by Casper Hansen on 2008-07-18
> **atomkarinca said:**
> Install timidity:

```
sudo apt-get install timidity
```

now you should be able to select it from the preferences. If still you can't then before you start TuxGuitar do these on terminal:

```
sudo modprobe snd-seq
timidity -iA
```

Thanks it helped!

---

### Post by samuraiCat on 2008-08-18
Hi! I absolutely love Tuxguitar. I hate to resurrect such an old thread, but I'm having a couple of issues: First, when I choose some of the instruments, I don't get any sound. Second, I cannot seem to get it to work with Jack running unless I have it hooked up to ZynAddSubFX, and then it won't use Tuxguitar's samples (which are superior).

Any suggestions? Thanks!

---

### Post by eversor88 on 2008-08-20
ok so i downloaded this program, and it runs nicely but i can't hear the tab play. I downloaded the java soundbank from their website, and they directory the installation tells me to extract it to which is audio/lib doesn't exist. So i tried making it and it still doesn't work i get this error when i press play that says "MIDI SYSTEM IS UNAVAILABLE" 
Ne suggestions on how to get this thing to work?

---

### Post by Northsider on 2008-08-20
Sweet!  I never knew about this...I'll have to try it out

---

