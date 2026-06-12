---
title: "64 Studio vs Ubuntu Studio?"
date: 2009-07-07
forum: Ubuntu Studio
---

### Post by Jestersage on 2009-07-07
Have anyone tried out 64 Studio? If so, how is it, compared to Ubuntu Studio?

---

### Post by trulan on 2009-07-07
I had 64studio 2.1 installed on my laptop for a bit.  It was okay but as I am still very new to Linux I moved back to Ubuntu Studio Hardy.  I'll probably try out 64studio 3.0 beta sometime soon, though.

I know I saw a great summary of the pros and cons posted by Stochastic somewhere around here.  Basically, 64studio is said to be **very** stable, while Ubuntu Studio is more widely supported and has a simpler setup for installing programs and such.

Ubuntu Studio comes with Pulse Audio, great for all-around audio stuff but a bit too buggy for serious audio production.  64studio omits this.

Personally, the reason I ended up using Ubuntu Studio was because I needed the ffado firewire drivers and I couldn't quite see my way through installing them on 64studio.

I guess it really depends on what you want to do.  If you're more production-oriented, go with 64studio.  If you want to do a lot of different stuff, or are needing firewire audio support, I'd recommend Ubuntu Studio.

---

### Post by Jestersage on 2009-07-08
I see.

Also, Is 64 Studio and Ubuntu Studio the only two that have precompiled RT kernel, and CCRMA and MRG (for CentOS) that are well known patches for Fedora, while openSuSE's RT is a huge question mark?

---

### Post by SyL on 2009-07-08
You got a pretty good comparaison on this thread: [http://ubuntuforums.org/showpost.php?p=7445260&postcount=6](http://ubuntuforums.org/showpost.php?p=7445260&postcount=6)

HTH

---

### Post by cmay on 2009-07-08
i used 64studio up til recently. it is far superior to ubuntu studio in all ways if i have to be honest. 

right now i am using ubuntu studio because the dvd i have to install 64studio is corrupted and i cant get a good burn out of the new iso imags  been trying to download. 

when i get a fresh and good burn again i will resintall 64studio . i had to use the computer for open solaris so when i got back to making music the dvd i used was faulty. i installed ubuntu studo instead and i dont like it as much as i do 64studio. 

this is off course my opinion only. i still use regular ubuntu on my laptop and i dont care much for the derivatives.

---

### Post by trulan on 2009-07-08
> **cmay said:**
> i used 64studio up til recently. it is far superior to ubuntu studio in all ways if i have to be honest. 

right now i am using ubuntu studio because the dvd i have to install 64studio is corrupted and i cant get a good burn out of the new iso imags  been trying to download. 

when i get a fresh and good burn again i will resintall 64studio . i had to use the computer for open solaris so when i got back to making music the dvd i used was faulty. i installed ubuntu studo instead and i dont like it as much as i do 64studio. 

this is off course my opinion only. i still use regular ubuntu on my laptop and i dont care much for the derivatives.
You need to set your clock back a few years in BIOS.  It sounds crazy but there is nothing wrong with your install DVD's.  Just set the clock back and it will work.  (Install hangs at tetex.bin, right?)

I must admit this installer bug started me off with a bad taste in my mouth for 64studio.

---

### Post by cmay on 2009-07-08
> **trulan said:**
> You need to set your clock back a few years in BIOS.  It sounds crazy but there is nothing wrong with your install DVD's.  Just set the clock back and it will work.  (Install hangs at tetex.bin, right?)

I must admit this installer bug started me off with a bad taste in my mouth for 64studio.

thanks,. yes its right it does that everytime so i figured it was a bad burn. 
i used 64studio for a couple of years now i think.  i only reinstalled once so it was a surprise it was doing this . 

thanks a lot i will sure try this out.

---

### Post by trulan on 2009-07-08
Apparently one or more of the files 64studio 2.1 uses to install is about five years old, and is not compatible with dates higher than early-mid 2009.  I just rolled my date back to 2007 and it worked.  There's a thread about it on the 64studio forums IIRC.

It did make me wonder, though, what else might be seriously out of date in that distro.  Just my opinion.  I'm sure Ubuntu Studio has equivalent or worse issues, they just apparently haven't hit me.

---

### Post by raboofje on 2009-07-08
Perhaps take the much-more-recent 64studio 3 beta a spin?

It's even based on Ubuntu instead of Debian in this release.

---

### Post by vitaliiygoose on 2009-07-08
Apparently one or more of the files 64studio 2.1 uses to install is about five years old. I though it was 4.

---

### Post by trulan on 2009-07-08
Here's the thread about the installer/date bug, if anybody wants to know more:
[http://www.64studio.com/node/1176](http://www.64studio.com/node/1176)

Maybe it is time to give 64studio 3.0 beta a go.  I already have the ISO downloaded...

---

### Post by cmay on 2009-07-10
&op
why i like 64studio better is  when i installed the 64studio it found my emu1212m soundcard and evertime i plug a drummachine or other midi or usb instrument in it then it is found by 64studio. 

this is not the case wiht ubuntu studio which i have to find the emu1212m driver first. then when i want to make music some of my intruments does not get found by ubuntu studio. 

the real time kernel makes a little difference but from ordinary ubuntu to ubuntu studio i see little difference in terms of how useful it is for me to for audio recording. 

ubuntu studio is a choice of movie ,sound and you have to mingle wiht it first. 
64studio is all about being setuo to play music and still have the stuff needed to make some grafichs and even code a webpage for your stuff

i like 64studio much better because of these things. i did not record for along time now since i really dont make that much music anymore but i remeber that in 64studio i would plug in keyboard set track in ardour to record and record.

 in ubuntu i dont have the patience anymore to try get it work as user freindly as 64studio so i will try the trick wiht setting back the time to get it installed again once i made a giant back up and i need to make a other computer for media center first. 

i use this install of ubuntu studio for both programming and to watch movies and i have all my music on the disc along wiht the few songs i worked on last. i dont think i will record any on this install anyway. 

you should use the distribution that makes most sence to you .try them both if you can. 
and happy audio recording. :) 

&others in tread posting helpful advise. 
i am very greatful for hte links on how to do this and that is a bug present. i tried two disks before i gave up on the install.- next time i know how  that it can be installed-. 
 
thanks.

---

### Post by Capoeira on 2009-07-10
thats pretty much it

---

### Post by trulan on 2009-07-11
Well, I gave the beta a spin.  You never know what you might get...

Installed fine, but it has two problems:
1. raw1394 device seems to be missing.  I kind of need that.
2. NVIDIA drivers require building your own kernel and headers to install.  I don't think so.

Verdict:  With 800x600 resolution and no firewire audio, it's going to be a bit before this release meets my needs.

---

### Post by sgx on 2009-07-12
> **trulan said:**
> Well, I gave the beta a spin.  You never know what you might get...

Installed fine, but it has two problems:
1. raw1394 device seems to be missing.  I kind of need that.
2. NVIDIA drivers require building your own kernel and headers to install.  I don't think so.

Verdict:  With 800x600 resolution and no firewire audio, it's going to be a bit before this release meets my needs.

Hi, I got fed up with debian/kernel (?blame?) hardware detection  consistantly failing to properly interrogate my system, leaving me at a useless 800x600, with a clueless xorg.conf listing 'configured monitor', 'configured mouse' etc so I nuked it with a real xorg.conf from a properly working setup, and the gfx came up at 1280 x 1028 as they should. I think that elephant in the corner needs to be called out and
held to account, there are too many major faulty releases for this to be either ignorant programmers, or accidental blunders.
Cue the X-Files theme song any time now...

---

### Post by Pablo_F on 2009-09-05
@sgx: Please, don't be unfair. ubuntu is very good at graphics out of the box for not so linux-friendly video devices and 64studio is certainly not. 64studio is very good at audio OOTB for far more linux-friendly audio devices and ubuntu can't be proud of it. For other things, 64studio works very well although it is not as up-to-date as ubuntu is. Sometimes and depending on your system and your skills, what is OOTB is a a steep hill to climb but let's be fair, 64studio2.1 is one the best distros of all times in my very limited view and ranking. As stable as etch, and music-oriented. At first I liked that they moved to be ubuntu-based because etch was getting old and it was difficult to install new software and ubuntu was so easy and cool! But now I miss that the official 64studio is not lenny based (although you can build a lenny system and install outstanding software from 64studio lenny-backports). This is very biased and I am not and expert. I am a user who has suffered because of my own ignorance mixed with a few software bugs, infamously unsupported hardware and never-ending release promises. All in all, you can't blame developers when they work without being paid (except donations) and push their work up in the net for us to use and enjoy.  

Anyway, enjoy the Linux you like the most because we can be proud of freedom of choice thanks to the internet, GNU, Linux and thousands of people in the world.

Cheers! Pablo.

---

