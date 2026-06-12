---
title: "Login drum sound"
date: 2012-03-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mykrob on 2012-03-05
How do I disable the drum sound on the login screen?
I looked at lightdm.conf but saw nothing regarding sound options.

thanks,
-myk

---

### Post by Harry33 on 2012-03-05
> **mykrob said:**
> How do I disable the drum sound on the login screen?
I looked at lightdm.conf but saw nothing regarding sound options.

thanks,
-myk

You probably mean system-ready sound.
At least you can force it to shut down by doing one of the following:

1. Delete the package gnome-session-canberra

2. Delete (or rename) the file /usr/share/sounds/freedesktop/stereo/system-ready.oga

---

### Post by 1roxtar on 2012-03-05
Simply open up the Dash (Ubuntu Button), search for Startup Applications and uncheck Gnome Login Sound.

---

### Post by mdurham on 2012-03-05
> **1roxtar said:**
> Simply open up the Dash (Ubuntu Button), search for Startup Applications and uncheck Gnome Login Sound.

The OP is not talking about the login sound.

---

### Post by mykrob on 2012-03-05
This    /usr/share/sounds/freedesktop/stereo/system-ready.oga doesn't seem to exist.

And, as the last post stated, I'm looking to disable the noise that plays when the login screen first shows.

Keep 'em coming, we're bound to figure it out :)

---

### Post by mc4man on 2012-03-05
> **mykrob said:**
> This    /usr/share/sounds/freedesktop/stereo/system-ready.oga doesn't seem to exist.


Try dialog-question.ogg (/usr/share/sounds/ubuntu/stereo

---

### Post by Script Warlock on 2012-03-05
there's an option to mute why not use it?.

---

### Post by mdurham on 2012-03-06
> **Script Warlock said:**
> there's an option to mute why not use it?.

Where is this option to mute the drum sounds?

The sound file is here: /usr/share/sounds/ubuntu/stereo/system-ready.oga
Cheers

---

### Post by Script Warlock on 2012-03-06
oh i was referring to this....

---

### Post by VinDSL on 2012-03-07
> **mykrob said:**
> How do I disable the drum sound on the login screen?
I like the login sounds, but there are times, such at my workplace, when I don't want to bring attention to myself with the Bongo Drum sound at login, et cetera.

Sorry, for being rudimentary, but...

What I do is mute the volume.  That's it.  :D

There will be no sounds, at all, until I unmute the volume, for instance: to watch a video, play music, or whatever.

Then, I simply mute the volume again, before log off/shut down.

---

### Post by VinDSL on 2012-03-07
> **Script Warlock said:**
> there's an option to mute why not use it?.
Oops!

I should have kept reading...  :oops:

---

### Post by Squonk07 on 2012-04-06
I finally broke down just now and did what I usually do, which is to generate in Audacity a tiny, 0.10 second audio file of silence, name it dialog-question.ogg, rename the original file in /usr/share/sounds/ubuntu/stereo to dialog-question.ogg.bak, and then move my generated file into that folder. I know I could just delete the original file, but somehow I don't like the idea of technically breaking the system. I'd rather just give it a silence file to play.

Every version of Ubuntu I hope that the devs will either:

A) remove this sound, or
B) at least offer some way of shutting it off in the UI (probably preferable as I'm sure some people appreciate the sound).

I've sort of given up hope on either of these happening, however.

---

### Post by t1497f35 on 2012-04-09
Hi,
Afaik Precise should ship with new system sounds (and probably already did) but the login sound is still the drum beat.
One can hardly think of a more annoying login sound than that.
**Any plans to change it by default to something chilling i.e. less annoying?**

---

### Post by mcellius on 2012-04-09
What would you suggest?  Bagpipes?  (I'm joking; I actually like bagpipes.)

---

### Post by craig10x on 2012-04-09
I'm not even getting it on my 12.04 beta 2 install...though sound works for everything else...and i have it ENABLED!

By the way, did you know you can turn it off altogether?...just hit the "cog wheel" icon on the upper right hand corner of your top panel...go to start up applications and uncheck the gnome log in sound bar that is shown on there...

---

### Post by Basher101 on 2012-04-09
they should add an option to place your own sounds...

---

### Post by sacridex on 2012-04-09
The more important question: **How to disable the unity-greeter drum sound?!**

---

### Post by mc4man on 2012-04-09
mv or rm /usr/share/sounds/ubuntu/stereo/dialog-question.ogg
Or replace with an appropriate .ogg you like
What's 'appropriate'?, wouldn't know without trying

---

### Post by Mr. Picklesworth on 2012-04-09
To silence the ready sound, you can change the volume level at the login screen. It should stick from then on.

---

### Post by mc4man on 2012-04-09
> **Mr. Picklesworth said:**
> To silence the ready sound, you can change the volume level at the login screen. It should stick from then on.
So there is some use of the things on the login screen

---

### Post by mc4man on 2012-04-09
In any event I took a short clip of some pleasing music, (.ogg) & replaced that file, works fine so you can do that if desired
(it only plays till you click enter after entering password so length isn't an apparent issue

---

### Post by Frogs Hair on 2012-04-09
The volume control in the login screen worked for me a few minutes ago . It was set to 100% by default I'll see if it stays that way after reboot .


Edit: The setting worked after reboot

---

### Post by emarkay on 2012-04-09
Surely there is an option to just disable this?

No messing with files or volume here-not-there, just a one time config setting and it's gone permanently?  

Surely...

---

### Post by Frogs Hair on 2012-04-09
I have not tested this and don't know if it will disable the drum sound . My goal was to reduce the volume.```
sudo apt-get install dconf-tools 
```

Open from dash by typing dcon. Proceed to org > gnome > desktop > sound and and disable event sounds.

---

### Post by Squonk07 on 2012-04-09
I just replaced it with a tiny .ogg file of silence. I agree that there should be some way of disabling this, either via GUI or else dconf or something. Expecting people to get in the habit of muting their sound before shutdown/reboot and then unmuting it once they've logged in (as I read in another thread about this) is not reasonable, nor is forcing them to aim for the volume control on the greeter screen in the miniscule amount of time they have at login.

---

### Post by arpanaut on 2012-04-09
> **Mr. Picklesworth said:**
> To silence the ready sound, you can change the volume level at the login screen. It should stick from then on.

Nice try..  It don't stick on my rig.
Alas, I was hoping there was an simple fix.

I disable system sounds immediately after installing, but if I have been listening to music loudly
the night before, those drums always make me jump on the first login in the AM.
I guess I gotta edit some config. files, this should be a simple click and forget option.

Not a biggie, just an irritation.

---

### Post by craig10x on 2012-04-09
> **emarkay said:**
> Surely there is an option to just disable this?

No messing with files or volume here-not-there, just a one time config setting and it's gone permanently?  

Surely...

Yes...in 12.04 you can...i described it in my post on the previous page...which was:

just hit the "cog wheel" icon on the upper right hand corner of your top panel...go to start up applications and uncheck the gnome log in sound bar that is shown on there...

that turns it off...you don't need to use the terminal or lower the volume...

---

### Post by Mr. Picklesworth on 2012-04-09
> **arpanaut said:**
> Nice try..  It don't stick on my rig.
Alas, I was hoping there was an simple fix.

I disable system sounds immediately after installing, but if I have been listening to music loudly
the night before, those drums always make me jump on the first login in the AM.
I guess I gotta edit some config. files, this should be a simple click and forget option.

Not a biggie, just an irritation.

I was noticing that at one point, and then it did stick and I decided it was a temporary hiccup. Maybe we can figure out the pattern for this and file a bug report&#8230;

I think there is some weird inconsistency in whether a session restores your personal last volume level or ALSA's (and I'm pretty sure that happens in a regular session, too), but I really have no idea how that works or what is going on so I could be speaking nonsense.

---

### Post by emarkay on 2012-04-09
See: [http://ubuntuforums.org/showthread.php?t=1955266](http://ubuntuforums.org/showthread.php?t=1955266)
Mods, please merge.

---

### Post by emarkay on 2012-04-09
> **craig10x said:**
> Yes...in 12.04 you can...i described it in my post on the previous page...which was:

just hit the "cog wheel" icon on the upper right hand corner of your top panel...go to start up applications and uncheck the gnome log in sound bar that is shown on there...

that turns it off...you don't need to use the terminal or lower the volume...


I did that, there is nothing listed... no programs no applications, just a pink box...

---

### Post by emarkay on 2012-04-09
Well IMHO, it's a Bug not a Feature ... 
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/977674](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/977674)

---

### Post by t1497f35 on 2012-04-10
> **Mr. Picklesworth said:**
> To silence the ready sound, you can change the volume level at the login screen. It should stick from then on.

As someone mentioned (and I can confirm) this mutes the whole desktop, and even more confusing - the desktop volume indicator doesn't show up as muted so you can't unmute it unless you revert it from the login screen.

In startup applications I don't have a "Gnome login sound" thingy, though it used to be there in the past but didn't work anyway.

As emarkay noted, this is an annoying bug:
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/977674](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/977674)

The works-for-all workaround is to remove or replace this file manually:
/usr/share/sounds/ubuntu/stereo/system-ready.ogg
which is a symlink to dialog-question.ogg

**Hopefully** this issue will finally be sorted out by Ubuntu 12.04.1 or by 12.10.

---

### Post by Mr. Picklesworth on 2012-04-10
> **t1497f35 said:**
> As someone mentioned (and I can confirm) this mutes the whole desktop, and even more confusing - the desktop volume indicator doesn't show up as muted so you can't unmute it unless you revert it from the login screen.

If it's muting the whole desktop, you've spotted a bug in the audio system. It should only be muting lightdm, and your session should restore its audio settings accordingly.

It might be specific to your hardware or your configuration, too.

---

### Post by t1497f35 on 2012-04-10
> **Mr. Picklesworth said:**
> If it's muting the whole desktop, you've spotted a bug in the audio system. It should only be muting lightdm, and your session should restore its audio settings accordingly.

It might be specific to your hardware or your configuration, too.

More likely there's multiple bugs in both the desktop and the audio system since on this thread people are reporting different "GUI" solutions and none of them works for all:

1) The "gnome login sound" - for some users it's there and it mutes the login sound by unchecking it. For others it doesn't work unchecking it. I don't even have it listed there though it used to be there in the past but didn't work anyway.

2) In previous versions of Ubuntu there was and still is the second way to mute the login sound: by checking the "mute" button in system sound as can be seen on attached screenshot, but with Ubuntu 12.04 it doesn't work any longer, though ALSA in Ubuntu 12.04 way better/newer version since I have no issues with playing stuff while there were plenty of issues with playing sounds in 11.10. So it's likely not a bug in 12.04's ALSA/sound system.

3) The third way is to mute the login sound from the lightdm login sound menu, which once again doesn't work for all.

So there's likely quite a few bugs and/or design issues with the login sound and its desktop integration in 12.04.

---

### Post by dcstar on 2012-04-10
> **emarkay said:**
> See: [http://ubuntuforums.org/showthread.php?t=1955266](http://ubuntuforums.org/showthread.php?t=1955266)
Mods, please merge.

Did **you** Report this thread so the "mods" actually know about it?

---

### Post by sacridex on 2012-04-10
> **Mr. Picklesworth said:**
> If it's muting the whole desktop, you've spotted a bug in the audio system. It should only be muting lightdm, and your session should restore its audio settings accordingly.

It might be specific to your hardware or your configuration, too.
If I disable the sound in unity-greeter, it disables the desktop sound too. :(

---

### Post by cariboo on 2012-04-10
Merged two similar threads.

---

### Post by craig10x on 2012-04-26
I just re-installed ubuntu 12.04....on my beta2 install, it listed the gnome start up sound in the menu which was unchecked...when i checked it i got the "jungle drum sound"...

On my re-install, gnome start up sound is not listed on the start up applications drop down...if i wanted to add it to my start up application drop down (so that i can check the box and make the sound come on) what should i enter into that start up window (using the "add" button)...?

Thanks...

---

