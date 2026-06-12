---
title: "flash fullscreen mode works only once after firefox starts"
date: 2013-09-10
forum: Ubuntu Development Version
---

### Post by miobrad on 2013-09-10
dear forum,
on various sites, when watching flash videos and going to fullscreen, it will work well, 
but only the first time. that is, if i switch back and then try to go back to fullscreen it will not work.
it does not matter if it is the same or an other video (or on an other site). 
thanks for any hints/comments!!

---

### Post by miobrad on 2013-09-18
am i really the only one having this problem? how could that be? no one using 13.10 is watching flash videos?

---

### Post by cariboo on 2013-09-18
For me full screen videos work in both Firefox and chromium, have you tried creating a new Firefox profile, to see if the problem still occurs?

---

### Post by miobrad on 2013-09-19
worth a shot, i just tried it - but it did not work. just to make clear, this is what happens: i go to a site with flash player videos. i click on fullscreen. it works. i go back to normal view. i click on fullscreen again - it does not work. the video in the small video area freezes and if i click ALT-TAB i see that there is a plugin-container 'ghost window' that is basically not working..

---

### Post by amjjawad on 2013-09-20
> **miobrad said:**
> am i really the only one having this problem? how could that be? no one using 13.10 is watching flash videos?

Hi,

What Saucy system are you using? Ubuntu? or any other flavour?

Have you installed the restricted package?

sudo apt-get update && sudo apt-get install ubuntu-restricted-extras

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I haven't seen this issue with Lubuntu Saucy and Ubuntu GNOME Saucy as of now. I might double check, just in case.

If you are using this for day-to-day tasks, please understand Saucy is still under development and not suitable for day-to-day usage.
[http://fridge.ubuntu.com/2013/09/06/13-10-saucy-salamander-beta-1-released/](http://fridge.ubuntu.com/2013/09/06/13-10-saucy-salamander-beta-1-released/)

If you are helping us with testing then I'd suggest to download the latest daily build and re-install.

Very important part of the testing process is to test the installation :)

Thank you!

---

### Post by johanschutten on 2013-09-22
Got same problem on Ubuntu 13.10 with Gnome 3.8 installed. Fullscreen only works onces, after that, I need te restart the webbrowser to be able to view flash-vids in fullscreen.

---

### Post by t-pinhammer on 2013-10-27
I have the same problem, Flash videos are workling always, but fullscreen is only working one time, doesn´t matter which video site or which webbrowser (tested in Firefox and Chromium). When I try to open fullscreen a second time, sound is working and Video stays small but hangs. The small Video goes on when I open another window than the webbrowser one time.

Ubuntu Gnome 13.10 with gnome-next and gnome-staging ppa enabled

---

### Post by cariboo on 2013-10-27
@t-pinhammer, I'd suggest you start a thread in the Main support area of the forum, as this thread now has nothing to do With Trusty (14.04). Thread closed.

---

