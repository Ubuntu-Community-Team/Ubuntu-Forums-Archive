---
title: "Problems with wine (slow)"
date: 2010-05-29
forum: Wine
---

### Post by banquo on 2010-05-29
I've run into to a problem that i don't really know why it occurs;
ive been running ubuntu since hardy, and installed wine back then.
It has never been any problems playing games until pretty recently thought, i noticed some moths ago how it took longer and longer to boot games (after i installed 9.10) and now under 10.04 it takes like *2-3 minutes to boot Starcraft* (!). 
the thing is that ive installed Civilization IV, and it just doesnt happen anything when i try to start it, and i dont know if something is completely wrong so it wont boot, or if its just very very slow.

I've got a pretty regular laptop, vaio w 1.6ghz dual-core, 2 gb ram and decent 3d-card 
and have'nt  had any hardware issues.

my current wine version is      1.2-rc1          but ive updated it a couple of times since the problems occured, and the updates didn't seem to affect the problems

Im pretty confident some1 here can help me, you ussually can:)

thanks in advance!  /Oskar
----------
(im sorry im aware that there probably are some grammar-errors, but i hope you'll understand what i mean anyway^^ )

---

### Post by banquo on 2010-05-29
any1 ? please =)

---

### Post by asdfoo on 2010-05-30
which 3d card and driver version?

I think you might want to try wine-1.2-rc2 as there are constant updates in areas affecting starcraft.

---

### Post by banquo on 2010-06-04
my 3d-card is a Geforce 8400M GT
and ive got the "NVIDIA accelerated graphics driver (version curren) [recommended]"
im sorry if it is a little inaccurate, but i dunno how to check the exact driver name

---

### Post by pedro_orange on 2010-06-04
```
lspci | grep VGA
```

Will give you information on your video card.

With regards to CIV IV, you need to download a couple of DLL files and pop them in ./wine/.../system32
You then need to add a number of library overrides in your winecfg.

The list is on appdb.winehq for CIV IV, along with a HOWTO installation guide.

Also pulseaudio doesn't work well with wine applications. Try killing the process and running wine with the ASLA driver.

---

### Post by McRat on 2010-06-04
Starcraft under Crossover rips on my ElCheapo AMD64 system running U32 10.04.  I made a Win98 bottle for it.

It does stop for 4 seconds every 10 minutes when running LAN peer-to-peer gaming with WinTel machines on the network.

You won't be able to do the Update to Starcraft through Battlenet, IIRC.  I had to download the patch and install it into the same bottle.

---

### Post by banquo on 2010-06-04
HI, thanks for your help,
just to clarify; i dont have any problems with Starcraft besides the slow startup, which 
started pretty resently - i just used Starcraft for reference for a program which shouldnt take long to boot (all wine programs does so)

My driver:
```

01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GT] (rev a1)

```

One more thing; I might have scr**ed up, i ran a directx-install along with CivIV and I read somewhere (in wine here on ubuntuforums i think) that that's something really stupid to do =/

---

### Post by pedro_orange on 2010-06-06
> One more thing; I might have scr**ed up, i ran a directx-install along with CivIV and I read somewhere (in wine here on ubuntuforums i think) that that's something really stupid to do =/

You don't need to install the DirectX that comes with CIV no. I'm not sure if it would effect the running of the application. You can always remove it anyway.

---

### Post by seventeenth_sunrise on 2010-07-11
Guys! Help here! My Warcraft 3 TFT has suddenly started lagging like hell... it never caused any problem until a recent update. I've been using the -opengl param all along so please help me with sth else. :)

My System: Core2Duo 2.33 ghz, 2GB RAM, Nvidia 8600GT

Thank you in advance.

---

### Post by seventeenth_sunrise on 2010-07-15
bump

---

