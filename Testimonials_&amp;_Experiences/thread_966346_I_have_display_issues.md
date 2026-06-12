---
title: "I have display issues"
date: 2008-11-01
forum: Testimonials &amp; Experiences
---

### Post by stalkingwolf on 2008-11-01
I say issues because in all 3 instances I have found work arounds
but not really solutions.

I have 3 computers with display issues, 1 a whitebox desk top with
onboard Via S3g unichrome pro adapter, 1 Toshiba Tecra 8200 with the
cyberblade xp adapter, and an everex stepnote with the Via S3G adapter.

All 3 get 800x600 initial resolution.  What I have found that works,

On the desk top I am running UbuntuEEE 8.04.1 and get all the resolution
choices I need.  Havent tried the "eyecandy"

On the Toshiba I am running 7.10 with all the res. choices.  Will try 
installing 8.04 and 8.10 shortly.

The everex is a morphadite.  It is as I have found out Part Winbook, part
fujitsu, and mostly paperweight.  I am running a custom 7.04 on it and the 
video works at least to 1024x768 res.  I made the Cd with remastersys on the Toshiba  and stripped it down to fit on a CD for work.

I have no clue why the particular editions work but they do.

I had hoped that the EEE version would work across the board but it does not.  Nor does the latest version work RE: display at all.

---

### Post by stalkingwolf on 2008-11-26
[SIZE="5"]UPDATE[/SIZE]

On the desktop the issue seems to have been fixed in 8.04.1
and in 8.10.  I installed both yesterday and both had proper
resolution OOTB.

Havent tried the toshiba yet.

I manually configured both the Toshiba and the everex and got 
1024x768 resolution.  I will try 8.04.1 and 8.10 on the toshiba later.

---

### Post by armandh on 2008-11-26
it is not the OS software if Ubuntu 

for the media box I am using 8.04 on an old P-III with a cast off nvidia chipped GTX? [restricted drivers loaded at boot][surplus when my son the gamer moved up to PCIe]

imagine my surprise when I plugged in the new widescreen via hdmi and got a screen full of resolution choices, with BIG numbers I have never seen B4

---

### Post by stalkingwolf on 2008-11-26
> it is not the OS software if Ubuntu 

I dont think I said it was The OS.  I did not even emply it was.
I stated as many others have that it was the chip.

I only updated this thread so others with this chip would know that at least on version of it now works OOTB.

On the many machines I have installed Ubuntu on ( somewhere around 20) I have only had problems with 2 video chips or cards. this Via and a cyberblade.
Both I have been able to manually configure.

I am going to try 8.04.1 and 8.10 on the machine with the cyberblade later
to see if the work OOTB.  If not oh well it still is configurable.

---

### Post by stalkingwolf on 2008-12-01
Still no joy with the cyberblade OOTB.

OH well.  I have it configured for the resolution I want
and everything else does what I want.

---

### Post by armandh on 2008-12-01
I have one monitor that will run a bunch of resolutions It just does not communicate that to the PC so a new Ubuntu would not display any other better than 600x800 until I pluged in a good monitor. I think there is a CL way to add choices that I once used.

---

### Post by stalkingwolf on 2008-12-02
What I did on the Toshiba might also work for you.

Open a terminal and put in
```
sudo displayconfig-gtk
```
a box will pop up, select screen, then click model on the right side.
another box will popup,
here you can select generic on the left and monitor with the resolution
you want on the right.

as the  toshiba is a laptop i chose Generic  and LCD 1024x768.
click the various OK's, log out and back in.  This gave me 1024x768
as the max resolution and several lesser ones.

I skipped a step or two because I think you said your video adapter is working.  if I am wrong let me know and I will post the whole enchilada.

---

