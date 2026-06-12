---
title: "New Ubuntu User - Just saying..."
date: 2008-03-01
forum: Testimonials &amp; Experiences
---

### Post by Rangiora on 2008-03-01
Greetings & Salutations.

Three weeks ago I decided to give Ubuntu a try.  Being somewhat wary of burning an .iso image I took the coward's way out and actually purchased a book w/included disk (The Official Ubuntu Book 2nd Ed - Prentice/Hall).  So I'm running v7.04 (a.k.a. - Feisty).  I actually gave the OS a spin by running from the desktop CD and after a quick tour decided to go ahead and install.

For the most part, installation went rather smoothly.  Slow and smoothly.  I say slow because I kept referring to the book as to avoid any hasty decisions that would upset the process.  Upon completion of the install I noticed that I had an already established connection to the Internet via my broadband router without ever having to really do anything.  Nice.

Setting up my Canon Pixma iP3500 was a bit trickier as the printer was not listed as supported by I did get it to work using the iP3100 driver.  I can live with that.

I had no problem with the sound and do not plan on trying to find/load/configure SoundBlaster Live! specific drivers.  Hey, as long as I can play a CD I'm happy.

The next task on my list to tackle turned out to be more of a challenge.  I wanted to see if I could get my DVD player up and running.  Had I known how involved that was going to be, at the start, I may have just moved that task to the bottom of the list.  Being stubborn, I didn't.  I guess my main ??? (don't want to use the word 'complaint'), my main concern is that it should not have been quite as involved as it turned out to be.  It took me a week to figure it all out.  I can see where novices can become frustrated to the point of giving up and going back to Window$.  Had it not been that I got an early start, for me anyway, with computers when DOS ruled the world and having to edit config.sys and autoexec.bat files, again, I would have given up.  But I persevered and just before coming here I watched a favorite movie of mine (Top Gun) without experiencing any problems.

My next task will be to look into and gain an understanding of what is involved with getting drivers for my nVidia GeForce 7600 graphics card installed.  I would really prefer to be using a higher resolution than 1024x768, but it will do for now.

I still have tons to learn and I feel just like a newborn...almost helpless at this point but I'm going to push on.  My apologies for the long-winded dissertation.  Thanks.

Rangiora

---

### Post by wolfen69 on 2008-03-01
> The next task on my list to tackle turned out to be more of a challenge. I wanted to see if I could get my DVD player up and running
seeing how this is your first post, it is obvious you didnt come here for any help. taking 2 min to ask how would have saved you ***alot*** of time and effort. this is what the message boards are for. good luck.

---

### Post by seventhc on 2008-03-01
You may want to do the upgrade option which will bring 7.04 up to 7.10.
To do this is simple, go to *System>Administration>Update Manager* and you should see an option in the top part that says *Upgrade*.
Welcome to Ubuntu, have fun. :)

---

### Post by FrozenFox on 2008-03-01
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Envy is the easiest, most painless way to install video drivers for anything older than Hardy (envy-ng is being made for hardy, but its not ready yet). Download, install, run, pick which video card company and driver number, and let it do its thing. Come back in 10 mins, reboot, and all should be well and over with. However, mind the warning that if you upgrade your system's kernel or xserver via the update manager, you need to run envy and remove your video drivers first, then when upgrades are done, reinstall the drivers via envy.

---

### Post by Rangiora on 2008-03-02
Thank you for your kind response wolfen69.

You're right.  I could have saved some time but what would I have learned?  How many times have questions regarding setting up a DVD been asked and answered? By now, those of you with more extensive knowledge would be sick and tired of answering the same question one more time.  May I at least get a little credit for my perseverence?

At an AutoCAD forum I belong to we get the same thing.  A newbie comes along and asks, "How do I (fill in the blank)?"  Invariably someone will respond, "Asked and answered."  Or, the response will be, "Have you checked the FAQs?"  Too many of us take the shortest route and in the process, learn but one thing...how to take the easy way out.  We really should exercise our brains a bit more often first.  Don't you agree?

Regards.

---

### Post by seventhc on 2008-03-02
Here are two links that should get you playing DVD's.
[http://www.funnestra.org/ubuntu/gutsy/#multimedia](http://www.funnestra.org/ubuntu/gutsy/#multimedia)
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
You would most likely only need one of these, but I always like extra options. :) Hope this helps, or maybe you have it playing already.

---

### Post by steveneddy on 2008-03-02
> **FrozenFox said:**
> [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Envy is the easiest, most painless way to install video drivers for anything older than Hardy (envy-ng is being made for hardy, but its not ready yet). Download, install, run, pick which video card company and driver number, and let it do its thing. Come back in 10 mins, reboot, and all should be well and over with. However, mind the warning that if you upgrade your system's kernel or xserver via the update manager, you need to run envy and remove your video drivers first, then when upgrades are done, reinstall the drivers via envy.

Actually, in 7.10 Gutsy there is a Restricted Drivers Manager that will give you the nVidia drivers from the repos that are a lot more stable that the one's in the Envy script.

If you install the drivers from the Envy script, if there is a new kernel in an update, you have to reinstall the video drivers.


It is safer and you get great performance from the video drivers in the repos than going with the latest/greatest from Envy.

Hardy will be out soon and Ubuntu will send you free CD's when Hardy gets here.

---

### Post by Tyke91 on 2008-03-02
7.04 should also have the restricted drivers manager. just go to System>Administration>Restricted Drivers Manager and check off the Nvidia one (it should autodetect)

welcome to ubuntu, and don't worry if you think your question is too basic... If we didn't want to answer those questions, we wouldn't be on these forums.

---

### Post by steveneddy on 2008-03-02
> **Tyke91 said:**
> 7.04 should also have the restricted drivers manager. just go to System>Administration>Restricted Drivers Manager and check off the Nvidia one (it should autodetect)

welcome to ubuntu, and don't worry if you think your question is too basic... If we didn't want to answer those questions, we wouldn't be on these forums.

I used 7.04 but I didn't realize that there was Restricted Driver Manager there, also.

RDM is the best way to go until you feel more comfortable with experimental software, like Envy, that installs the experimental software for your video card.

Better to stay safe and use the stock nvidia drivers, IMHO.

---

### Post by Rangiora on 2008-03-03
Thank you one and all for those suggestions.  I will certainly consider them.

---

### Post by Teber on 2008-03-03
when reading your report on installing ubuntu i nodded in approval. as to how you figured some things yourself: i respect you for it. perseverance and initiative are good qualities. 

i have little doubt that you did yourself a great favor opting for ubuntu. welcome aboard. 

and always remember: ubuntu rocks :guitar:

and if you seek help on here: this forums really rocks :guitar:

---

### Post by FrozenFox on 2008-03-03
In response to the restricted drivers manager comment:

That's true, I suppose, but I've found that practically every person I've ever had install ubuntu (out of about 7 people, 5 failed), it failed for one reason or another, including myself. I've actually found envy to be more stable than the restricted drivers manager (it's no surprise that it's included in linux mint, hehe). I suppose sound advice would be to try restricted first then if you have issues try envy.

Although, envy-ng (though not out yet) will not require you to reinstall the drivers and such every time you update the kernel from what I understand, it will fix that stuff for you automatically. Secondly, unless I'm mistaken, the kernels and such have been 'frozen' for quite some time in everything older than hardy, so that's not much of an issue. Anyone who knows how to update the kernel outside of the update manager surely would not have an issue with the video drivers needing to be reinstalled anyway. Though I'm completely unsure of that, I just never remember updating the kernel or whatnot for the entirety of the time i used the older versions.

---

### Post by Vadi on 2008-03-03
Hi and welcome.

Just a note to point out - there are more than half a million people on this forum. So, you will come across some negative / 'elitist' attitude at times, but generally, there are many more friendly people about :)

---

### Post by CaptainCabinet on 2008-03-03
> **FrozenFox said:**
> In response to the restricted drivers manager comment:

That's true, I suppose, but I've found that practically every person I've ever had install ubuntu (out of about 7 people, 5 failed), it failed for one reason or another, including myself. I've actually found envy to be more stable than the restricted drivers manager (it's no surprise that it's included in linux mint, hehe). I suppose sound advice would be to try restricted first then if you have issues try envy.

Although, envy-ng (though not out yet) will not require you to reinstall the drivers and such every time you update the kernel from what I understand, it will fix that stuff for you automatically. Secondly, unless I'm mistaken, the kernels and such have been 'frozen' for quite some time in everything older than hardy, so that's not much of an issue. Anyone who knows how to update the kernel outside of the update manager surely would not have an issue with the video drivers needing to be reinstalled anyway. Though I'm completely unsure of that, I just never remember updating the kernel or whatnot for the entirety of the time i used the older versions.

I use Envy and haven't had any problems with it. :)

---

### Post by agtownz on 2008-03-03
> My next task will be to look into and gain an understanding of what is involved with getting drivers for my nVidia GeForce 7600 graphics card installed. I would really prefer to be using a higher resolution than 1024x768, but it will do for now.
I'm running a 7600 gs myself, all it needed was the restricted drivers to be installed.

---

### Post by 3rdalbum on 2008-03-03
If you want DVD playback support to be easier to incorporate, you could always try lobbying your local congressman or congresswoman (assuming you're from the US). Give them some hassle about passing the DMCA.

---

