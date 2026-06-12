---
title: "Noob questions for Ubuntu Studio"
date: 2011-07-29
forum: Ubuntu Studio
---

### Post by rojaasensei on 2011-07-29
I have xubuntu installed and loving it.

Lately, I have enjoyed exploring some of the more advanced audio software available from the download manager.

I was considering installing Ubuntu Studio's audio package.  However, I am not sure if I am overreaching my hardware.

I use a Samsung N150 Plus with an extra gig of ram installed.  But will my audio system handle this mysterious "Jack?"  Do I need some kind of external audio card?

Your suggestions would be appreciated.

Thank you.

---

### Post by Pablo_F on 2011-07-29
I would say "give it a try". Not ideal but it doesn't hurt. Later you will see if you want or need better audio hardware.

When you install jack select YES you want rtprio and memlock privileges. Then add your user to the audio group and reboot. 

Note that non jack-aware audio apps won't produce sound when jack is running. You can modify this behaviour in a number of ways.

Cheers, Pablo

---

### Post by trulan on 2011-07-30
It should work, especially if you don't bother with the ubuntustudio-desktop metapackage (that will pull in all of gnome, or unity, depending on your Ubuntu, and you really don't need that.)  Just install the ubuntustudio-audio and ubuntustudio-audio-plugins metapackages, and maybe the -video and -graphics packages of you'd like them.

Your hda-intel sound card will work OK with jack, don't expect it to sound like a high-dollar card, but it will work.

Have fun!

---

### Post by rojaasensei on 2011-07-30
Yes, I installed the audio and plugins.  Everything went fine!

But, while some things worked "out of the box" others seemed to require fiddling around with JACK which I found confusing and often made mistakes.

So, I removed the studio packages.  Seems I need to wait until a simpler version is made.

Studio is great though. Thank you for your kind and considerate advice.

---

### Post by sgx on 2011-07-31
> **rojaasensei said:**
> Yes, I installed the audio and plugins.  Everything went fine!

But, while some things worked "out of the box" others seemed to require fiddling around with JACK which I found confusing and often made mistakes.

So, I removed the studio packages.  Seems I need to wait until a simpler version is made.

Studio is great though. Thank you for your kind and considerate advice.

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

Hi, these screenshots and tips explain the jackd connections gui, don't give up now, the gui makes it quite easy :popcorn:
Cheers

---

### Post by rojaasensei on 2011-07-31
for the encouragement.  The link you gave is to a page I did not see during my research on Jack.  Thanks, it is clearer than some other pages.

Now, it seems to indicate that the connections made will be transient, that is, I would have to follow the instructions each time I boot up and wish to use Jack.  

Pathage, I am guessing, does the same thing but reloads the setting at each session?  I tried Pathage before and got lost.  

I suppose what I need to figure out is all the settings I need for Studio and Jack, and a way to avoid having to do them over again.  LOL.

I think if I succeed in this then I will volunteer to help update all the help pages.  That is not a criticism.  I understand that the Studio team is not large, and very busy.  It would be nice to help out if I can things going the way I want.

Now, the various help pages seem somewhat disconnected from each other and some are apparently out of date when I compare the info to what I sometimes found in the forum.

Thanks again.

---

### Post by trulan on 2011-07-31
Unfortunately, Patchage won't save your connections.  It does give an excellent visual image of how jack connections are made, though.  If it looks confusing, click 'refresh' and then 'arrange' (in the Patchage menu) and that should make things easier to see.  Patchage is color-coded; blue boxes are audio, green boxes and red boxes are different types of MIDI (and MIDI in Studio is a bit confusing, unfortunately.)

And by all means, the documentation can use some more help, things tend to change pretty quickly in Linux and it's easy to let the help pages to get out of date.

---

### Post by rojaasensei on 2011-07-31
So, there is no way to preserve your settings session to session?

---

### Post by trulan on 2011-07-31
I mostly work with Ardour, and it saves all its own connections, that has been enough to meet my needs.

While I don't use this personally, I believe KXStudio has a pretty good setup for doing this:
[https://launchpad.net/~kxstudio-team/+archive/kxstudio](https://launchpad.net/~kxstudio-team/+archive/kxstudio)

There are several informative threads discussing the KXStudio packages here on the forums, here's one to get you started:
[http://ubuntuforums.org/showthread.php?t=1772602](http://ubuntuforums.org/showthread.php?t=1772602)

---

### Post by sgx on 2011-07-31
> **rojaasensei said:**
> So, there is no way to preserve your settings session to session?

qtractor is getting session improvements in that area, and is worth
learning to use, but there is a way to ease the pain, you can start a string of apps at one go, by preceding each one with  &

a2jmidid -j default &hydrogen &rakarrack &yoshimi

I start qjackctl first, then the list of apps I want to start. Commands are stored in .bash_history, and can be cycled through in
the terminal, with the up arrow key, so memorizing/typing isn't needed to launch the string of
apps you choose, and you can still edit the list before pressing the enter key.

(yoshimi crashes unless I start qjackctl separately, so if you
don't need yoshimi, you could do

qjackctl &a2jmidid -j default &hydrogen &rakarrack &phasex

many apps preferences or workflow let you choose parts of their startup, or saving state, which also can save steps. Experimenting will lead to efficiency, and session support itself, will improve
in the meantime.

Cheers

---

### Post by rojaasensei on 2011-08-01
Thanks again for everyone's kind help & encouragement.

I have added quite a few of the video packages from Studio. I have added some of the audio apps as well.

I'm moving one step at a time and having a great time!

Ubuntu Studio is superb.  Keep up the good work.

---

