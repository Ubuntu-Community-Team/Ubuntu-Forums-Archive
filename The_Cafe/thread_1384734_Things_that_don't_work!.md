---
title: "Things that don't work!"
date: 2010-01-18
forum: The Cafe
---

### Post by Mahngiel on 2010-01-18
Okay, so I'm a little upset at the time being.  I fell in love with Karmic that day I installed it, which was about 3 days after it was released.  I've been able to overcome several hurdles, and have run into many more brick walls.  Perhaps I'm in need of a rant at the moment because my wife's camera won't mount and I can't get to the pics of the kids we took.  Perhaps I just want one OS that'll handle the simple and menial tasks that everyday users have come to expect in this generation of tech.  

I've combated the nay-sayers' taunts about linux never being anything more than a toy with ever more motivation to get things to work - In the end, only to fail.  Is it user error? Maybe.  But shouldn't our OS make our lives as easy as possible?  I shouldn't have to troll forums in search of a remedy to connect my camera, phone, or any of the other toys I have, but I do.

So, either by exhaustion or plain frustration, I'll leave my rant with a list of things that either don't work, or I had to work at getting to work.

1. Kodak C503Digital Camera
2. Samsung Trance Cell Phone
3. Digital Media Reader
4. Wireless Networking Card - BCM4306; hey, I got THAT to work
5. 300GB SimpleTech Extended HDD - sorry, it's not even recognized by fdisk
6. Webcam - Genx X-eye
7. Legit DVDs
8. Nostromo Gamepad

---

### Post by futz on 2010-01-18
> **Mahngiel said:**
> Perhaps I'm in need of a rant at the moment because my wife's camera won't mount
My new Canon T1i won't automount. The photo importer thing starts, but dies with an error and the camera unmounts. I have to use Nautilus and go to Computer and double-click the camera. Then it mounts and gives a couple more error messages which I ignore. Then I can dig down a couple levels of directories in the camera and just drag/drop the photos/movies off the camera myself. Would sure be nicer if it would work automatically, but this isn't so difficult.

Does yours show up in Nautilus' Computer screen?

---

### Post by toupeiro on 2010-01-18
1. Kodak C503Digital Camera
2. Samsung Trance Cell Phone
3. Digital Media Reader
4. Wireless Networking Card - BCM4306; hey, I got THAT to work
5. 300GB SimpleTech Extended HDD - sorry, it's not even recognized by fdisk
6. Webcam - Genx X-eye
7. Legit DVDs
8. Nostromo Gamepad

-----------------------------

1) [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)
2) [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)
3) [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)
4) Good on ya. ;)
5) [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)
6) [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)
7) [http://www.medibuntu.org](http://www.medibuntu.org)
8) [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

---

### Post by Mahngiel on 2010-01-18
> **toupeiro said:**
> 
1) [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)
2) [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)
3) [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)
4) Good on ya. ;)
5) [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)
6) [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)
7) [http://www.medibuntu.org](http://www.medibuntu.org)
8) [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

[quote=UbuntuHCL]
**Your search returned no results.**
[/quote]

Great place to look... but, as I say - no dice.

---

### Post by Mahngiel on 2010-01-18
> **futz said:**
> 
Does yours show up in Nautilus' Computer screen?

Sure does!  Oh wait, there's TWO of them... oh, and neither will mount or become accessible. :confused:

---

### Post by futz on 2010-01-18
> **Mahngiel said:**
> Sure does!  Oh wait, there's TWO of them... oh, and neither will mount or become accessible. :confused:
Hmm... Mine shows up twice sometimes too, but mine WILL mount.

---

### Post by k64 on 2010-01-18
> **Mahngiel said:**
> Okay, so I'm a little upset at the time being.  I fell in love with Karmic that day I installed it, which was about 3 days after it was released.  I've been able to overcome several hurdles, and have run into many more brick walls.  Perhaps I'm in need of a rant at the moment because my wife's camera won't mount and I can't get to the pics of the kids we took.  Perhaps I just want one OS that'll handle the simple and menial tasks that everyday users have come to expect in this generation of tech.  

I've combated the nay-sayers' taunts about linux never being anything more than a toy with ever more motivation to get things to work - In the end, only to fail.  Is it user error? Maybe.  But shouldn't our OS make our lives as easy as possible?  I shouldn't have to troll forums in search of a remedy to connect my camera, phone, or any of the other toys I have, but I do.

So, either by exhaustion or plain frustration, I'll leave my rant with a list of things that either don't work, or I had to work at getting to work.

1. Kodak C503Digital Camera
2. Samsung Trance Cell Phone
3. Digital Media Reader
4. Wireless Networking Card - BCM4306; hey, I got THAT to work
5. 300GB SimpleTech Extended HDD - sorry, it's not even recognized by fdisk
6. Webcam - Genx X-eye
7. Legit DVDs
8. Nostromo Gamepad

I got my SimpleDrive to work. In particular, I had to reformat it in Ext4.

As for the DVDs:

```
sudo apt-get install ubuntu-restricted-extras
``` in a terminal.

---

### Post by toupeiro on 2010-01-18
> **Mahngiel said:**
> Great place to look... but, as I say - no dice.

Then, perhaps it doesn't work in ubuntu?

hcl == hardware compatability list.

You know that little sticker on some PC's or devices that say "works with windows" or "windows <version> compatible"?  Yeah, will this hcl is sort of the equivalent to that.  If you're going to run linux, its usually good to find things like this before: 

a) you install linux
b) you buy new hardware if you already run linux.

EDIT:  PS, putting your versions out there that dont work is a very good way for support to start developing for them so that one day hopefully very soon, they are supported.

---

### Post by Mahngiel on 2010-01-18
This wasn't intended to be a "solve MY problems" thread.  This was more geared towards... what doesn't work for YOU?!

And, toupeiro, until they market computers designed for linux distros, you'll always have people who have problems converting.

---

### Post by toupeiro on 2010-01-18
I understand that, and since the beginning, HCL's have been there.  Redhat had one when I first used linux in the late 90's.  The difference is, they aren't as publicised today as they should be.  If you haven't seen it before, start using it, recommend that your friends trying linux use it, and there will be less frustrated people who have burnt hours trying to support something that simply may not have support yet.

---

### Post by sliketymo on 2010-01-18
> **Mahngiel said:**
> This wasn't intended to be a "solve MY problems" thread.  This was more geared towards... what doesn't work for YOU?!

And, toupeiro, until they market computers designed for linux distros, you'll always have people who have problems converting.

Dell,System76 for starters.

---

