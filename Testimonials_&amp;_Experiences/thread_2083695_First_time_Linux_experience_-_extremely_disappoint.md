---
title: "First time Linux experience - extremely disappointed"
date: 2012-11-13
forum: Testimonials &amp; Experiences
---

### Post by Quittyband on 2012-11-13
Working around IT i've always heard about Linux but have never actually tried it - but my old Lenovo N100 laptop takes 20 minutes to boot winXP, can't install win7 and is, for lack of a better definition, a useless hunk-a-junk so i figured, why not?
Right?

Well. 
I gave Linux a tour and liked what i saw. It boots fast, it looks good, there's a lot of out of the box functionality...
So i installed and have been using it for 24 hours - and so far it feels more like a half-ported android in high resolution then an OS.

I remember being promised centralized account syncage. Impeccable stability. Customization beyond anything i've seen.
So far, it took 30 minutes to get thunderbird to recognize my gmail account and now it only syncs messages i haven't read on my mobile phone - not to mention that i don't understand why i have to register my account in the OS just so that i'd have to reregister it in the mail app.

another 30 minutes to set up the time and date because the time zones are all wrong, the +/- keys only work for minutes and if you close the window before you exit the textbox it won't save the values.

the language settings crashed on me twice trying to add a language, the OS manufactured a faux PS/2 mouse i had to disable via terminal on a computer that doesn't even have a darned PS/2 connection and i spent a long while looking for MyUnity only to discover it doesn't exist.

Chrome didn't install right but showed up when i rebooted. 'Show desktop' doesn't work no matter what. All cursors apart for the standard arrow are absolutely HUGE -
But hey, it sure does boot fast.


Anyway, now that my bitching and whining is all done, what am i missing?
My user experience so far is more akin to an alpha build from a college student than a full blown product and if that were the case i wouldn't have heard so much about Linux. What gives?
Is it the Unity GUI? is 12.10 just a glitchy build?
Is linux just not up to par anymore for the average user, with win7 out?

---

### Post by dannyboy79 on 2012-11-13
I would suggest trying out 12.04 (which is a long term support version)Xubuntu or Lubuntu which both don't use Unity. Just my 2 cents. Linux is certainly not for everyone and it's unfortunate these little issues have put a sour taste in your mouth.

I use Ubuntu 10.04.4 as my main workstation and have a headless file/LAMP/server running 10.0.4 as well which also doubles as a DVR running mythtv. WHen I need windows which is not often I run it in VirtualBox

---

### Post by cariboo on 2012-11-13
Moved to T&E, as this really isn't a support question.

---

### Post by ajgreeny on 2012-11-13
> **dannyboy79 said:**
> I would suggest trying out 12.04 (which is a long term support version)Xubuntu or Lubuntu which both don't use Unity. Just my 2 cents. Linux is certainly not for everyone and it's unfortunate these little issues have put a sour taste in your mouth.

I use Ubuntu 10.04.4 as my main workstation and have a headless file/LAMP/server running 10.0.4 as well which also doubles as a DVR running mythtv. WHen I need windows which is not often I run it in VirtualBox
+1

I also think that 12.04 is a better idea for you, and I suggest Xubuntu rather than Ubuntu with its, in my opinion, idiosyncratic DE, unity.

I do not use and do not like unity at all; I think it takes far too many of the computer's resources, and I don't have a machine that will run unity with 3D, so for me 12.10 ubuntu is a complete non-starter, as 2D unity has now disappeared, (not that it worries me personally, but it might other users).

I do not know what the detailed specs of your laptop are, but there were some of that model with only 512MB ram.  Even if you doubled that, it is not enough to run unity properly, and I would suggest you need 2GB or more.  Similarly  am not sure if the intel graphics are good enough for unity, assuming you have the intel integrated 945 that at least some models of that laptop have.

As far as thunderbird is concerned, your gmail account settings should have been added to the configuration automatically during its setup process the first time you start it.  The way you describe your problem re syncing sounds as if you have perhaps IMAP on one machine and pop3 on another, with one or more of them set to move messages from your inbox once read.  Go to your gmail setup in a web-browser and you can change the settings to allow you to do whatever you want.  I use both IMAP and pop3, so I know it is possible to use both without a problem, so come back again if you can't sort it and I'll check exactly how mine is setup.

Your time zone should have been set during install, so I have no idea why that is wrong for you, unless the CMOS battery has died.  Try setting up ntp and ntpdate to sync with web time servers, which should ensure the time is exactly right always.

---

### Post by mastablasta on 2012-11-13
gmail is porbably the fastest to setup in thunderbird. it takes me less than 3 minutes.

i also have it setup on thunderbird in Windows.

oh yes as it was mentione dtheer are a few other desktop environments if oyu findUnity strange - Xubuntu and Kubuntu (using XGFCE and KDE) are the best, LXDE (found in Lubuntu) is progressing nicely as is light and cute E17 (best viewd in Bodhi linux). there are also many others. some are made to use little resources. for example windows manager IceWM or Openbox.

---

### Post by Quittyband on 2012-11-13
So, it would seem that this was indeed that simple.

I booted a fresh install of Xbuntu and am finally feeling like i'm getting that Linux experience. 
Surprisingly it doesn't feel as fast or fluid as ubuntu did but i chalk it up to less preloaded and autostarted items.
My laptop is indeed not up to spec for anything. It actually ran Unity surprisingly well, i really don't know what went wrong - 
I haven't used POP3 for years, so the Gmail thing isn't it, and neither is the login issue, the timezone issue or anything else for that matter.

Eh well. I guess my installation just went bananas over something.
Xbuntu, on the contrary, is working brilliantly right out of the box and i believe i've settled for an OS for my new, incoming laptop.

Thanks, everyone - your faith in Linux is, it would seem, well earned.

---

### Post by sffvba[e0rt on 2012-11-13
Glad you found what works for you.


404

---

### Post by MadmanRB on 2012-11-13
You may also want to fish out other linuxes too, there is nothing wrong with experimentation.

---

### Post by cariboo on 2012-11-14
> **Quittyband said:**
> So, it would seem that this was indeed that simple.

I booted a fresh install of Xbuntu and am finally feeling like i'm getting that Linux experience. 
Surprisingly it doesn't feel as fast or fluid as ubuntu did but i chalk it up to less preloaded and autostarted items.
My laptop is indeed not up to spec for anything. It actually ran Unity surprisingly well, i really don't know what went wrong - 
I haven't used POP3 for years, so the Gmail thing isn't it, and neither is the login issue, the timezone issue or anything else for that matter.

Eh well. I guess my installation just went bananas over something.
Xbuntu, on the contrary, is working brilliantly right out of the box and i believe i've settled for an OS for my new, incoming laptop.

Thanks, everyone - your faith in Linux is, it would seem, well earned.

I feel the same way about Xubuntu, I recently installed it and updated to the 13.04 development version, it doesn't feel as fast or as smooth as Ubuntu Raring on the same hardware. I installed Xubuntu in order to help with testing this development cycle, as during the last cycle, there were very few people even willing to test iso's as they came out.

---

### Post by Quittyband on 2012-11-14
I'm all for, but apart for Xbuntu, Kbuntu and Lbuntu is there anything out there?
I'm well aware of all the distros, but as far as i can tell all they do is preinstall software and/or multimedia - which i can do for myself.

---

### Post by mastablasta on 2012-11-14
well for exmaple linux mint uses Cinnamon desktop (based on Gnome3) they developed. they also fixes some bugs from Ubutnu "solutions". but as i was trying them they always used too much RAM and forced disk into swapping prematurely.
 
you can try Debian (Ubuntu's father) that is slightly different and for some reaosn it uses less ram and seem to be lighter on resources. A good version of it is Chrunchbang (i mean easy for new peopel to install) 
 
then you have the various rpm based distribution and each is a bit different. you have the Fedora (Red hat testing ground) that has plenty of latest stuff, OpenSUSE (used to have best KDE integration), Arch linux - build your own distro kind of thing (can be very light on resources if oyu know what you're doing), super stable very long temr support RHEL based linuxes (CentOS, Scientific Linux).
 
then you have the super small ones - Slitaz, DSL, Puppy, Tiny Core - some of them might even work on now ancient 486cpu...
 
then there are specialist ones - 
for example GUI server/NAS: Zentyal, Openmedia vault
or rescue, backup: rescue disk, gparted, redo backup
or "hide the user from regime": Liberte linux, Tails
 
then you have soem with different idea of OS behind it such as Turnkey Linux
 
so many of them out there. and plenty are interesitng just to try them.

---

### Post by tartalo on 2012-11-14
> **Quittyband said:**
> I'm all for, but apart for Xbuntu, Kbuntu and Lbuntu is there anything out there?
I'm well aware of all the distros, but as far as i can tell all they do is preinstall software and/or multimedia - which i can do for myself.

There are a couple of options available, but as you very well say they are  basically remixes of either Debian, RedHat, Slackware or Linux from Scratch, only with different software selections and configurations, for convenience:

[http://futurist.se/gldt/wp-content/uploads/12.10/gldt1210.png](http://futurist.se/gldt/wp-content/uploads/12.10/gldt1210.png)

If you can't make up your mind, try this:

[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)

---

### Post by stalkingwolf on 2012-11-14
im running the non-pae version of 12.04 on a dell d800, 1gb ram and a 2.0 or 2.2 mz processor.  Installed from the mini.iso as i recall. you have the choice to install what you want.

I just did the basic ubuntu install then installed mate later.  it runs fine.

I used it yesterday to replace this one while i did some work on it. more on that later in the proper place.

---

### Post by critin on 2012-11-15
> but my old Lenovo N100 laptop takes 20 minutes to boot winXP, can't  install win7 and is, for lack of a better definition, a useless  hunk-a-junk 

Yeah, I agree that linux has too many issues,  just send the laptop to me--I'll pay shipping.  thanks...

---

