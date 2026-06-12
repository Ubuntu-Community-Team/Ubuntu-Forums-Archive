---
title: "anyone else remove pulseaudio?"
date: 2008-12-31
forum: The Cafe
---

### Post by wolfen69 on 2008-12-31
i just installed intrepid on one of my computers and was having slight glitching of audio and video while streaming flash videos. i removed pulseaudio installed esound and went back to alsa. also reinstalled flash and every thing works great. 

anyone else give pulseaudio the boot?

---

### Post by MikeTheC on 2008-12-31
Haven't touched Pulse here, and all is working just fine.

---

### Post by Rokurosv on 2008-12-31
Tried it in Fedora 10, I had some problems with it and removed it.

---

### Post by NWAdawg on 2008-12-31
We had 5 Linux computers here. All 5 run Sound Blaster live cards. I've gutted pulseaudio's out of 3(all Ubuntu based) of the 5,and the 4th & 5th(#!) never had it. Alsa sound is so much better for our needs.

---

### Post by Riffer on 2008-12-31
there is a HOWTO on this forum explaining how to get rid of pulseaudio.  I've see threads going to OSS instead of ALSA.  It seems OSS is still in development and has matured quite abit.  Alas my linux skills and lack of desire prevents me from testing this out.

---

### Post by Zack McCool on 2008-12-31
There is no need to remove Pulse.  The best solution, IMO, is to fix your Pulse installation.  The default install that Ubuntu uses seems to be a much bigger problem than Pulse itself...

[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

This Howto should solve most problems people experience with Pulse.  It sure made a difference here...

---

### Post by MindFlayer on 2008-12-31
Got lots of problems with optical audio output, sound lag, excessive CPU usage and wine games. Now I'm running pure ALSA and everything works as expected, out of the box if I may say. Take the leap of faith if you don't *need* Pulseaudio!

---

### Post by urukrama on 2008-12-31
I don't install it, and use ALSA on my Debian and Ubuntu computers.

---

### Post by DMcA on 2008-12-31
I would if I had the time for more messing about. Pulse has been nothing but trouble since upgrading from gutsy

---

### Post by Swagman on 2008-12-31
Sound is a mess on this system.

Just scrolling web pages makes music glitch.

---

### Post by gn2 on 2008-12-31
Yes, I've removed it from my Ubuntu installations.

---

### Post by billgoldberg on 2008-12-31
> **wolfen69 said:**
> i just installed intrepid on one of my computers and was having slight glitching of audio and video while streaming flash videos. i removed pulseaudio installed esound and went back to alsa. also reinstalled flash and every thing works great. 

anyone else give pulseaudio the boot?

I never installed it in the first place.

---

### Post by Pekkalainen on 2008-12-31
I havent removed it but I do despise it. Just havent gotten around to removing it because Im too lazy to mess with it a the moment. 

Why does Pulseaudio suck? The previous sound system started working fine by Edgy or so, why fix something that isnt broken :(

---

### Post by Hells_Dark on 2008-12-31
Works fine on both of my computers.

---

### Post by glotz on 2008-12-31
I removed it, I have no use for the features it provides. ALSA is working nicely.

---

### Post by mamamia88 on 2008-12-31
seems like once a day i have to go to the terminal and kill pulse audio to get any sound at all i think i'll try uninstalling it to see if that fixes anything

---

### Post by jawinterton on 2009-01-24
I removed pulseaudio and am so happy that I did.  Now I've got sound again.  I recommend doing it if people aren't having any success getting it working after some time.

---

### Post by WatchingThePain on 2009-01-24
I found that secondlife audio would not work until I removed Pulseaudio.

Pulseaudio supposed to be good because it allows you to control the sound of each app individually or something. That was a real hassle so I dumped it.

---

### Post by RichardLinx on 2009-01-24
Pulse Audio worked fine for me in Ubuntu 8.10, no issues what so ever (It was a different matter with 8.04). So no, I haven't removed It. I'm using openSUSE with KDE at the moment however and have no Idea what sound server I'm using. (First proper trial of KDE4)

---

### Post by Polygon on 2009-01-24
this was the first release where pulseaudio actually worked perfectly, so i just leave it on

the idea of pulseaudio is good, but it still needs to be worked on. Soon it will take over alsa and everything will be good =)

---

### Post by asbesto on 2009-06-14
> **Riffer said:**
> there is a HOWTO on this forum explaining how to get rid of pulseaudio.  I've see threads going to OSS instead of ALSA.  It seems OSS is still in development and has matured quite abit.  Alas my linux skills and lack of desire prevents me from testing this out.



... WHERE IS this howto?!?!?

---

### Post by gradinaruvasile on 2009-06-14
> **wolfen69 said:**
> i just installed intrepid on one of my computers and was having slight glitching of audio and video while streaming flash videos. i removed pulseaudio installed esound and went back to alsa. also reinstalled flash and every thing works great. 

anyone else give pulseaudio the boot?

Oh  yes. On every ubuntu installed comp i touched... :))

Here is the all-out method:

[http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/")

---

