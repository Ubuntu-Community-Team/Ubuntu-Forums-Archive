---
title: "I have just installed Ubuntu Studio; Before I proceed ..."
date: 2010-03-15
forum: Ubuntu Studio
---

### Post by wizarddrummer on 2010-03-15
Hi all,

Thanks for all of your replies regarding my earlier post "Third time is a charm".

Before I wreck anything, I am looking for advice on how to proceed.

Please, be patient with the length of this post because this is one of those "an ounce of prevention is worth a pound of cure" posts.

This is a brand new install. I have not changed anything. 

Basically, I've opened Firefox for this post.

My experience with the current Linux is limited to what I have learned over the last three weeks with some "less than stellar" results.

Currently, my "what to do next", with regard to OS installs is what I would do with XP.

I would pop the mobo CD in or download stuff from the mobo manufacturer for sound, USB upgrades, etc.; video drivers; load Office and configure some basic programs like Outlook mail etc. [*this post is only about drivers and updtates I can figure out how to do Open Office and Mail etc.]

Very rarely would I do any Updates. Microsoft is notorious for breaking things in their updates.

First concern has to do with Nvidia video drivers. 

This machine has an Nvidia 6600 gt agp card.

Folks, I had a horrendous experience with this in my first regular Ubuntu install, so I want to get this right and it needs a little history and explanation.

With my first Ubuntu install I had to mess around with xorg.conf; Nvidia's program repeatedly had problems with "Save X Configuration" - it couldn't write to this or that file; 

I spent days in the terminal window; it was endless and I never got it to work properly. 

All I wanted to do was have the option to have the output from both DVI's on the card produce the same exact output (for a demo) and then be able to change it back to a more standard expanded desktop dual monitor functionality.

I NEVER could get both monitors to display the same thing unless the driver was not installed.

Then, sometimes when I started the system the video reverted back to thinking there was no driver present.

I can do this functionality in XP.

One very confusing aspect to this was that in the "Hardware Devices" Panel it showed the [Recommended] driver to be "Activated". In the Software Programs there was an entry for Nvidia 3D binary Graphics that was NOT checked; indicating that that utility thought the drivers were not installed.

Is there a binary driver that does not use the ascii xorg.conf files for it's information?

In other words; how do I best proceed with the video driver installation keeping in mind that I would like to have that sync'd dual monitor setup so I can give a demo with one monitor facing away from me. 

From what I've seen so far Nvidia does not seem to consider Linux a "favorite son"; its more  like a "serial killer step child" because the drivers are way out of date from what I am used to seeing in Windows.

I saw a reference to this: aptitude install nvidia-glx regarding (I think) installing nvidia drivers where it does not have to you xorg.conf.

Your thoughts?

Finally, what updates should I install?

None of these are familiar to me so I don't know which ones to de-select or select.

Thanks so very much for your help.

---

### Post by cchhrriiss121212 on 2010-03-15
Firstly you should remember that what you are now using is not XP. Your problem with dual display would be better off in the multimedia and video section as it's not really to do with studio. Explain exactly what is wrong and what driver you have installed. I don't think it will really matter whether the recommended driver (180) is out of date if you are using this for audio.
I haven't had any trouble with any updates I've installed breaking things, but others on this forum have said it occasionally happens. I just use security updates on mine.

---

### Post by rlameiro on 2010-03-15
its a ubuntustudio install so it has something to do, at leas a little bit.

wizarddrummer:

for the nVidia cards you can install the nvidia proprietary driver, and the nvidia control panel.

install envyng-qt -> this is a utility that helps you to choose the driver to install. just go to synaptics and search for it.
usually nvida cards are well supported so you will not have so much problems, but about the dual screen is always a little bit tricky.

search on synaptics also for nvidia-settings, try it and say how it goes.

---

### Post by wizarddrummer on 2010-03-15
> **cchhrriiss121212 said:**
> Firstly you should remember that what you are now using is not XP. Your problem with dual display would be better off in the multimedia and video section as it's not really to do with studio. Explain exactly what is wrong and what driver you have installed. I don't think it will really matter whether the recommended driver (180) is out of date if you are using this for audio.
I haven't had any trouble with any updates I've installed breaking things, but others on this forum have said it occasionally happens. I just use security updates on mine.

Thanks for the reply.

---

### Post by wizarddrummer on 2010-03-15
> **rlameiro said:**
> its a ubuntustudio install so it has something to do, at leas a little bit.

wizarddrummer:

for the nVidia cards you can install the nvidia proprietary driver, and the nvidia control panel.

install envyng-qt -> this is a utility that helps you to choose the driver to install. just go to synaptics and search for it.
usually nvida cards are well supported so you will not have so much problems, but about the dual screen is always a little bit tricky.

search on synaptics also for nvidia-settings, try it and say how it goes.

Thanks I'll try that.

---

