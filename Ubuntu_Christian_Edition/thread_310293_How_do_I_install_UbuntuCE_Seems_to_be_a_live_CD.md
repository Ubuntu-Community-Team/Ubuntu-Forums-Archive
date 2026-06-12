---
title: "How do I install UbuntuCE? Seems to be a live CD"
date: 2006-12-01
forum: Ubuntu Christian Edition
---

### Post by Swakoo on 2006-12-01
Hi guys,

I bumped across this CE of ubuntu and thought it was very interesting and decided to try installing it on a old IBM thinkpad (192MB RAM, P3).

I boot using CD (of course, heh) and I selected "Start or Install Ubuntu CE". But it seems to be always running off the CD (cd drive reading very hard). How come it doesn't install.. am I missing something?

Also On running I keep getting GNOME Settings Daemon Error. 
Something about it not receiving a reply.

My laptop is not fantastically fast admit, but I was hoping to install it into the computer and run it, not from the CD.

Anyone can advice me?

Thanks!

---

### Post by mhancoc7 on 2006-12-01
> **Swakoo said:**
> Hi guys,

I bumped across this CE of ubuntu and thought it was very interesting and decided to try installing it on a old IBM thinkpad (192MB RAM, P3).

I boot using CD (of course, heh) and I selected "Start or Install Ubuntu CE". But it seems to be always running off the CD (cd drive reading very hard). How come it doesn't install.. am I missing something?

Also On running I keep getting GNOME Settings Daemon Error. 
Something about it not receiving a reply.

My laptop is not fantastically fast admit, but I was hoping to install it into the computer and run it, not from the CD.

Anyone can advice me?

Thanks!

I am not sure about the GNOME Settings Daemon Error.

If you want to install Ubuntu CE to your hard drive you just double click on the "Install" icon on the desktop. Then follow the steps. Keep in mind that if you choose the default installation your hard drive will be formated and you will lose all data on it. Let me know if you have any questions or problems.

Thanks, Jereme

---

### Post by doobit on 2006-12-01
> **Swakoo said:**
> Hi guys,

I bumped across this CE of ubuntu and thought it was very interesting and decided to try installing it on a old IBM thinkpad (192MB RAM, P3).

I boot using CD (of course, heh) and I selected "Start or Install Ubuntu CE". But it seems to be always running off the CD (cd drive reading very hard). How come it doesn't install.. am I missing something?

Also On running I keep getting GNOME Settings Daemon Error. 
Something about it not receiving a reply.

My laptop is not fantastically fast admit, but I was hoping to install it into the computer and run it, not from the CD.

Anyone can advice me?

Thanks!

Your RAM is pretty close to the bottom limit for the LiveCD. I think it really needs 256MB minimum to work well until you have a swap file on the hard drive. You might find it easier to get the Ubuntu Alternate install CD and use the text based installer first, then use the Ubuntu CE Convert script to install the other programs.

---

### Post by Darrious on 2006-12-01
That would probably be his best choice. As far as the GNOME Deamon problem. I'm not to sure about that. Maybe it will be fixed when he installs. Or possibly when he installs Edgy first then installs the Ubuntu CE convert_me_script.

---

### Post by dakotadare2b on 2006-12-01
I would agree with using the alternate text install, then use the convert script.

If the ubuntu alternate doesn't work,then use the xubuntu alternate. I had to do this with my laptop. I then installed ubuntu and did the ce convert script. This was the only way I could get ubuntu ce, on a P3 with 128MB RAM.

Randy

---

### Post by doobit on 2006-12-01
> **dakotadare2b said:**
> I would agree with using the alternate text install, then use the convert script.

If the ubuntu alternate doesn't work,then use the xubuntu alternate. I had to do this with my laptop. I then installed ubuntu and did the ce convert script. This was the only way I could get ubuntu ce, on a P3 with 128MB RAM.

Randy

I just ran the script on my Xubuntu install with a custom kernel and it works like a charm. Didn't break anything. :-D

---

### Post by leo1a0 on 2006-12-01
Did you say your prayers first?

:D

---

### Post by doobit on 2006-12-01
Fortunate for me God is taking care even when I don't pray.
Everything seems to be working fine on this old clunker. :)

---

### Post by leo1a0 on 2006-12-01
> **doobit said:**
> Fortunate for me God is taking care even when I don't pray.
Everything seems to be working fine on this old clunker. :)

You are so lucky!!!

I mean, for both things :-k

---

### Post by mhancoc7 on 2006-12-01
> **doobit said:**
> I just ran the script on my Xubuntu install with a custom kernel and it works like a charm. Didn't break anything. :-D

Great to hear!

Jereme

---

### Post by Darrious on 2006-12-01
How do you find your motherboard make and model  in ubuntu.

---

### Post by Swakoo on 2006-12-02
hi guys.. as of now i have used ubuntu 6.10 alternate cd to install and its ok. i guess the spec is indeed abit too low...

but some questions:

during installation it only asked me for user password (not userid)
so on login, what userid do I use? as of now.. i had to ctrl-alt F1 to go to shell, and create a user manually using useradd. Is that the way?

naturally my user don't have admin rights... as I used only Fedora and Redhat (runlevel 3 only) prior to this... how do I enable it? how do i allow my user to have basic admin rights (to toggle admin rights, networking options etc)? How do i allow root to login if i don't have rights to begin with?

thanks for helping guys!

---

### Post by Darrious on 2006-12-02
Well that is very odd that it did not ask you for a user id.

Users are not supposed to have root/admin rights. I beleive that if you add them to the  /root directory, or the root group, then you can edit files that require root access. But this is not a wise decision.

It is better just to issue a root password. 

Open up terminal

Type in this 
```
sudo passwd
```This should come up with a prompt for a password then you just type in your password and then what you want the password to be.

Then type this in too

```
su
```This is what makes you root.

---

### Post by doobit on 2006-12-04
> **Swakoo said:**
> hi guys.. as of now i have used ubuntu 6.10 alternate cd to install and its ok. i guess the spec is indeed abit too low...

but some questions:

during installation it only asked me for user password (not userid)
so on login, what userid do I use? as of now.. i had to ctrl-alt F1 to go to shell, and create a user manually using useradd. Is that the way?

naturally my user don't have admin rights... as I used only Fedora and Redhat (runlevel 3 only) prior to this... how do I enable it? how do i allow my user to have basic admin rights (to toggle admin rights, networking options etc)? How do i allow root to login if i don't have rights to begin with?

thanks for helping guys!

That sounds like you used the OEM mode to install instead of the text mode install. 
Once you have installed, booting into the recovery mode puts you in root. From there you can add users, or change passwords at will.

---

### Post by Swakoo on 2006-12-04
yah i did used the OEM mode.

retried using the text mode and it did ask me for userid. so what's oem mode for?

also.. now i can't get it to recognise my dlink pcmcia wireless card... ubuntu v5 was able to detect. weird. 

during installation it did detect.. but upon first boot, nothing. no wireless.

---

### Post by Darrious on 2006-12-04
That is strange. So what OS are you running again. 
Sorry, I'm just a little lost. Are we still on the topic.

---

### Post by Swakoo on 2006-12-05
oooh sorry. currentlyh installed ubuntu 6.10, which i will try to convert to CE later. but now wifi is not working.

gonna try ndiswrapper later.

---

### Post by Darrious on 2006-12-05
I noticed that there have been many problems with Edgy. Especially wifi.

---

### Post by Swakoo on 2006-12-11
hmm so its not just me huh
maybe i should revert to previous version first

---

### Post by Darrious on 2006-12-11
That might be an idea, but you might want to try to get you card to be recognized  in Edgy.

---

### Post by Swakoo on 2006-12-14
> **Darrious said:**
> That might be an idea, but you might want to try to get you card to be recognized  in Edgy.

is there an official channel i can submit to?

---

### Post by doobit on 2006-12-14
You didn't mention what chipset your card uses. Edgy has a slightly lighter kernel than Dapper had, so there are fewer drivers compiled in, but the modules may still be available. I have an old Netgear MA111 v1 , for example. The Prism2 drivers were in the 2.6.15 kernel, but not the 2.6.17 that's in Edgy. I just had to download and install the Wlan-ng drivers using Synaptic and I'm up an running.

---

### Post by Swakoo on 2006-12-18
I'm using a Dlink DWL-g650 xtreme Airplus. It was detected in v5. In edgy, during installation it asked me to enter wep password etc (it can detect the wireless network) but after completion, nothing.

Using Aetheros chipset.

Anyway I've tried using NDISWrapper and it worked instantly without me keyig in any WEP key for my AP. Apparently what values I have set during installation is stored. now is to see how do i get a wifi icon on the taskbar..

---

### Post by doobit on 2006-12-19
Atheros uses madwifi drivers, which are excellent. The kernel developers sometimes include them and sometimes don't, or include an incomplete set. You can download and install the modules, but anyway, if ndiswrapper is working for you that's great. Do a search in Synaptic. There are some choices. I tried the regular network applet, and it didn't work with my Prism2 card. I will keep looking and let you know.

---

