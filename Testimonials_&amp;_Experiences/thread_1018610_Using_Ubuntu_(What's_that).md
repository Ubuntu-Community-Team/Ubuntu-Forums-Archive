---
title: "Using Ubuntu (What's that?)"
date: 2008-12-22
forum: Testimonials &amp; Experiences
---

### Post by solwic on 2008-12-22
Just wanted to drop a quick note to state my astonishment with this operating system.  

I've been through the process of setting Ubuntu up more times than I care to admit.  I've gotten into a routine - install OS, updates and video drivers, reboot, then add wine, rar, restricted extras, thunderbird, google earth, etc. - and everything works right away.

But I've always tried to tweak things up; install weird themes, try to get AWN to work *without* Compiz since Compiz is broken with ATI cards, installing KDE along side Gnome...always there was something to do, something to try, something to install.

Lately...I've just been cruising.  Everything is installed and working, and for likely the first time, I'm using Ubuntu...just using it, not *fixing* it or *tweaking* it.  And I must say...it's nice. :)

Surfing the web, checking e-mail, word processing (I'm a writer), xchat to stay in touch with friends, Amarok for music, VLC for video...it all is so easy, so intuitive, and so *free!*  

I enjoy setting up Ubuntu, but I really love just using it.  All the free apps to do whatever I want - backup DVD's, burn .iso's....I'm not sure I can take much more awesomeness in one lifetime.  :P

Cheers!

---

### Post by chrisamiller on 2008-12-22
If you do frequent reinstalls, here's a helpful trick that will backup all your packages and reinstall them for you:

To create the list (before reinstall):
```
dpkg --get-selections | grep -v deinstall > ubuntu-files
```

Stash that file somewhere safe (usb drive, email, another partition)

Then to install your packages:
```
sudo apt-get update
sudo apt-get dist-upgrade
dpkg &#8211;set-selections < ubuntu-files
sudo dselect
```

This will open up a dselect session. Type 'I' and allow dselect to
install of the the packages listed in your ubuntu-files document. When
it's finished, type 'Q' and hit the ENTER key to exit dselect.

---

### Post by mdsmedia on 2008-12-22
Now you're just trying to make his experience more boring ;).

Excellent tip BTW. I'm going to copy that, bookmark it, whatever, for next time I want to reinstall.

---

### Post by wolfen69 on 2008-12-22
great tip chrisamiller.

@jrock: just think, a few weeks ago you were on the verge of going back to windows. (at least that's what i recall) good to hear you're rockin' n rollin' with it. for those times you feel the need to tinker, just get another hard drive and play around with that. (just swap hard drives so your main drive doesn't get borked)

i used to love the eye candy and such, but now i keep it simple and install only what is necessary to get my work done.

---

### Post by gjoellee on 2008-12-22
> **wolfen69 said:**
> great tip chrisamiller.
i used to love the eye candy and such, but now i keep it simple and install only what is necessary to get my work done.

that's why i keep on using Arch Linux, you install only what you NEED and don't get a lot of things that you "DON'T NEED" which I find annoying. I use Xfce as well bacuse at the moment a feel that even gnome gives to much eye candy! (This also keeps my computer in great shape! I boot in 15 sec!)

---

### Post by stalkingwolf on 2008-12-23
> you install only what you NEED and don't get a lot of things that you "DON'T NEED" which I find annoying

First how do you determin what you NEED until you have tried it all?:P

Second it is usually less NEED than it is WANT.  For instance I did not 
necessarily NEED 7 computers, but I wanted them for different things.
:guitar::P:):lolflag:

---

### Post by solwic on 2008-12-23
> **wolfen69 said:**
> great tip chrisamiller.

@jrock: just think, a few weeks ago you were on the verge of going back to windows. (at least that's what i recall) good to hear you're rockin' n rollin' with it. for those times you feel the need to tinker, just get another hard drive and play around with that. (just swap hard drives so your main drive doesn't get borked)

i used to love the eye candy and such, but now i keep it simple and install only what is necessary to get my work done.

Yeah, I was pretty close to giving it up.  As for tinkering, I installed a copy of 8.10 in VirtualBox.  It's my guinea pig install. :)

And I'm with you on the eye candy...I still want AWN or some kind of dock that runs without Compiz, but for the most part, keeping it simple suits me just fine.  :)

---

### Post by Joeb454 on 2008-12-23
You can run AWN without compiz. If you're using Gnome just enable the Metacity compositor, and it'll run :) I've done this a couple of times on an older PC of mine :p

---

### Post by solwic on 2008-12-23
> **Joeb454 said:**
> You can run AWN without compiz. If you're using Gnome just enable the Metacity compositor, and it'll run :) I've done this a couple of times on an older PC of mine :p

Seriously? 

If I use fusion-icon to switch to Metacity, do I have to do that every time I boot up?  Or is there a way to automate it?

EDIT:  I guess I owe the people at Compiz an apology.  Here I thought that turning on desktop effects (required to run AWN) with an ATI card was impossible because Compiz (responsible for said desktop effects) was broken.  

Now I realize that's not the case...even when using Metacity, turning on desktop effects STILL breaks 3d and video playback with an ATI card, as well as lagging the system so badly it's barely usable.  

Which means that this isn't Compiz's fault...it's Ubuntu's fault.  And ATI's fault.  

So I apologize to Compiz loyalists...I was misinformed.  

P.S.:  AWN does run with Metacity, but if you've got an ATI card, turning on desktop effects breaks the whole gig.  AWN shows up, but 3d, video, and system performance all go down the toilet.  :(  Guess I'm still waiting for 9.04.  

Thanks anyway.  :)

---

### Post by farmerlee on 2008-12-24
> **chrisamiller said:**
> If you do frequent reinstalls, here's a helpful trick that will backup all your packages and reinstall them for you:

To create the list (before reinstall):
```
dpkg --get-selections | grep -v deinstall > ubuntu-files
```

Stash that file somewhere safe (usb drive, email, another partition)

Then to install your packages:
```
sudo apt-get update
sudo apt-get dist-upgrade
dpkg –set-selections < ubuntu-files
sudo dselect
```

This will open up a dselect session. Type 'I' and allow dselect to
install of the the packages listed in your ubuntu-files document. When
it's finished, type 'Q' and hit the ENTER key to exit dselect.

I just tried your backup trick and the resulting file is only like 34kb in size, Is that about right? Should it be that small?

---

### Post by wolfen69 on 2008-12-24
> **farmerlee said:**
> I just tried your backup trick and the resulting file is only like 34kb in size, Is that about right? Should it be that small?

that should be about right. after all, it's only a text file with a list of what apps to reinstall.

---

### Post by mkvnmtr on 2008-12-25
Wolfen as much as I reinstall that just might be the most valuable thing I have learned here on the forums. Thank you.

---

### Post by solwic on 2008-12-25
> **mkvnmtr said:**
> Wolfen as much as I reinstall that just might be the most valuable thing I have learned here on the forums. Thank you.

I used to reinstall all the time - with both Win XP and Ubuntu.  With Windows, it was kind of necessary if you expected a smoothly functional PC.  I think the habit sort of carried over to Ubuntu.  That and the fact that there are so many distros to try, it's hard to stick with one.

Now...I'm on a mission to see how long Ubuntu can stay installed and still work like it ought to.  If I get the urge to play with another distro, I use VirtualBox.  If I find myself in Virtual Box with a different OS more than Ubuntu...I may switch.  

Otherwise, I'm on a mission.  :P  Out of curiosity, is there a way to tell how long it's been since Ubuntu was installed?

---

### Post by Martje_001 on 2008-12-25
> **farmerlee said:**
> I just tried your backup trick and the resulting file is only like 34kb in size, Is that about right? Should it be that small?
Should be OK. Remember that's not a backup of your data, only a list of what programs you have installed / not installed.

And, 34kB is a lot! It's 34,000 bytes (272000 bits!!) :P

---

### Post by mkvnmtr on 2008-12-25
I used to reinstall a lot because I had fouled something up. Now it more often than not I want to try something new. I seem to always find a new to me app or something I didn't even know I could do. It is mostly playing. I am on a powerpc and the virtual boxes don't work very well for me. Haaving a list will really help. Lots of the best stuff is kind of obscure.

---

