---
title: "Black background on Overview Gnome-shell 3.6.2."
date: 2012-11-27
forum: Ubuntu Development Version
---

### Post by serdotlinecho on 2012-11-27
Is this a default feature, black overview background on gnome-shell 3.6.2?

---

### Post by C@illou on 2012-12-02
Hi,

I have the exact same problem, a black background on Overview since I upgraded to Gnome 3.6.2, instead of having the greyed/shadowed desktop background. But sometimes it's working as expected, and it seems to mess up when I plug a second screen to my laptop. If it can be related to my graphic card, I have an Intel HD4000 integrated to the CPU.

EDIT: It's working fine when I juste booted, but as soon as I plug my external monitor, the oveview background is black.

---

### Post by serdotlinecho on 2012-12-02
But for me just black background, as i'm now using default ubuntu wallpaper and stock gnome-shell theme but still showing black background. I think it should show my wallpaper as a background.

---

### Post by VinDSL on 2012-12-02
In my experience, changing your Shell Theme will make a huge difference.

I'm running GS 3.7.2...

Here's how it looks with the Default Shell Theme


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-2-dec-2012-6(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-2-dec-2012-6.png")[/INDENT]


If I had a solid dark wall, instead of gradient greys, I'd be straining my eyeballs.

Now, here's the-same-everything, but I'm using "Elementary" for the Shell Theme


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-2-dec-2012-7(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-2-dec-2012-7.png")[/INDENT]


Big difference, eh what?  ;)

---

### Post by serdotlinecho on 2012-12-03
[OFFTOPIC] I use guayadeque too because it's lightweight and fast on my netbook :guitar:  
but on gnome-shell it doesn't show appmenu? Hmmm nevermind, I still love and use Unity. I hate gnome-shell big bottom system tray. Like when I want to use screencloud app and it's hidden at the bottom and really slow to access ](*,) where on Unity, it's there for me at the top panel, click and show drop down menu/settings! Fast! [/OFFTOPIC]

---

### Post by atreiju on 2012-12-13
I have the same problem with the black background! And it doesn't depened on the theme I'm using. For me, it looks like it has something to do with the opacity in the overview.

I can deactivate every extension (themes, too), and I still get the same black background.

Also, sometimes I do not have that "blackground" for a while, but after a short time, it's there again. Mostly it's there.

I also have an intel gpu.

Any ideas about this?

---

### Post by serdotlinecho on 2012-12-20
Still having the same bug with gnome-shell 3.7.3
Here's a video: [http://www.youtube.com/watch?v=mJlSI7Y4Lk0&feature=youtu.be](http://www.youtube.com/watch?v=mJlSI7Y4Lk0&feature=youtu.be)

Update: After installing ubuntu gnome desktop package, i have solved the problem, thanks to grahammechanical!

---

### Post by VinDSL on 2012-12-21
> **serdotlinecho said:**
> Still having the same bug with gnome-shell 3.7.3 [...]
Where did you find GS 3.7.3?!?!?

Gotta say, 3.7.2 is looking pretty sexy...  ;)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-21-dec-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-21-dec-2012-1.png")[/INDENT]

---

### Post by jeremi.thebeau on 2013-04-08
> **serdotlinecho said:**
> Still having the same bug with gnome-shell 3.7.3
Here's a video: [http://www.youtube.com/watch?v=mJlSI7Y4Lk0&feature=youtu.be](http://www.youtube.com/watch?v=mJlSI7Y4Lk0&feature=youtu.be)

Update: After installing ubuntu gnome desktop package, i have solved the problem, thanks to grahammechanical!

Hi, 

The video doesn't seem to be there anymore. I'm having this problem at the moment after updating my intel packages with the new intel graphic UI installer ([https://01.org/linuxgraphics/downloads/2013/intel-linux-graphics-installer](https://01.org/linuxgraphics/downloads/2013/intel-linux-graphics-installer)). Everything seems to be ok except that the normal semi-transparent overview overlay seem to be opaque. 

I've intalled the ubuntu-gnome-desktop pakage(s) and reboot but still getting the same. 
[COLOR=#000000]
@ [/COLOR]serdotlinecho, would you mind elaborating or explaining what [COLOR=#000000]grahammechanical is?
[/COLOR][COLOR=#000000]
thanks


[/COLOR]

---

### Post by dafero on 2013-04-08
> **jeremi.thebeau said:**
> Hi,   The video doesn't seem to be there anymore. I'm having this problem at the moment after updating my intel packages with the new intel graphic UI installer ([https://01.org/linuxgraphics/downloads/2013/intel-linux-graphics-installer](https://01.org/linuxgraphics/downloads/2013/intel-linux-graphics-installer)). Everything seems to be ok except that the normal semi-transparent overview overlay seem to be opaque.    Same here, right after updating the Intel driver, the Activities background turned black. I am using Ubuntu 12.10 + GS 3.6.2.  Any ideas?  Thank you!

---

### Post by ft_ on 2013-04-09
sorry, not a lot of time :
1) try reselect your background image
2) use lightdm instead of gdm for normal background
3) use lightdm instead of gdm for non-buggy multi-screen behaviour when unplugging the monitor
just my experience, dont blame me :-)

---

### Post by Kelkar on 2013-04-09
I have the same problem as mentioned above. :(

---

### Post by Kelkar on 2013-04-10
Ok, I finally found a solution for the black background bug. Just update your system to Ubuntu 13.04 and it should get back to normal.

---

### Post by zika on 2013-04-11
> **Kelkar said:**
> Ok, I finally found a solution for the black background bug. Just update your system to Ubuntu 13.04 and it should get back to normal.All of us here are on 13.04... Mostly from the very beginning of the cycle or even before that... ;)

---

### Post by dafero on 2013-04-11
> **Kelkar said:**
> Ok, I finally found a solution for the black background bug. Just update your system to Ubuntu 13.04 and it should get back to normal.

I don't wanna update, Ubuntu 13.04 is still a beta... is it the only solution?

---

### Post by zika on 2013-04-11
> **dafero said:**
> I don't wanna update, Ubuntu 13.04 is still a beta... is it the only solution?Then You will be better asking this question outside this U+1 room...

---

### Post by Xgen on 2013-04-11
Seems to work with.....gnome-tweak-tool-->Desktop-->Have file manager handle the desktop-->off. There are consequences, such as no context menu on the desktop and probably others. As a side note, wallpaper dimming works for me without modifications on gnome-shell 3.8.

---

### Post by Merri on 2013-06-20
> **Xgen said:**
> Seems to work with.....gnome-tweak-tool-->Desktop-->Have file manager handle the desktop-->off. There are consequences, such as no context menu on the desktop and probably others. As a side note, wallpaper dimming works for me without modifications on gnome-shell 3.8.


Ah thanks for this tip! Toggling this option on and off a few times fixed the problem for me without having to leave it disabled all the time. I'm running 13.04 with Gnome 3.6.3.

---

### Post by C@illou on 2013-06-21
> **Xgen said:**
> Seems to work with.....gnome-tweak-tool-->Desktop-->Have file manager handle the desktop-->off. There are consequences, such as no context menu on the desktop and probably others. As a side note, wallpaper dimming works for me without modifications on gnome-shell 3.8.

I had to do the same thing to get the background back to normal on Archlinux + Gnome, seems like having file manager handling the desktop breaks the wallpaper in the overview. Thanks.

---

### Post by Kow on 2013-06-23
I was trying out debian testing a few days ago and had this problem sporadically. If I logged-out and logged back in the background would appear. I guess the important thing here is that this is probably an upstream issue.

---

### Post by cariboo on 2013-06-23
> **Kow said:**
> I was trying out debian testing a few days ago and had this problem sporadically. If I logged-out and logged back in the background would appear. I guess the important thing here is that this is probably an upstream issue.

You should check out phillinux's post [here]("http://ubuntuforums.org/showthread.php?t=2142381&p=12701768&viewfull=1#post12701768"), it links to an explanation to what the Ubuntu devs have done to solve the problem.

---

