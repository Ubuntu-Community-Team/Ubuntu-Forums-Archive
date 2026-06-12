---
title: "starling (star1) microphone problem"
date: 2011-04-09
forum: System76 Support
---

### Post by tlroche on 2011-04-09
summary: A star1 running maverick/10.10 has 2 users, both admin. The built-in mic only works for one user. How to fix?

details:

I'm trying to setup Skype for multiple users on a star1. I login as me and do

```
me@it ~ $ arecord -f cd /tmp/junk.wav
Recording WAVE '/tmp/junk.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
# speak in the direction of the mic
^CAborted by signal Interrupt...
me@it ~ $ totem /tmp/junk.wav &

```

and I get playback of what I spoke. I then restart and login as another user, but

```
gf@it ~ $ arecord -f cd /tmp/junk.wav
Recording WAVE '/tmp/junk.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
# speak in the direction of the mic
^CAborted by signal Interrupt...
gf@it ~ $ totem /tmp/junk.wav &

```

produces no sound. When logged in as the other user,

[LIST=1]
[*]I can play sounds, so I believe this is not an output problem.
[*]In Preferences>Sound>Hardware, profile="Analog Stereo Duplex".
[*]In Preferences>Sound>Input, there is only one device="Internal Audio Analog Stereo", and it is selected.
[*]In Administration>Users and Groups, both users have Account type=Administrator.
[/LIST]

How can I ensure all users can use the microphone (e.g., for skype) or debug the problem further?

---

### Post by tlroche on 2011-04-13
> **tlroche said:**
> star1 running maverick/10.10 has 2 users, both admin. The built-in mic only works for one user. How to fix?

Any ideas?

---

### Post by isantop on 2011-04-13
Can you check the individual permissions each user has? You can do this from System > Administration > Users and Groups, then click on each user and click on the User Privileges tab.

---

### Post by tlroche on 2011-04-13
> **tlroche said:**
> summary: A star1 running maverick/10.10 has 2 users, [...] In Administration>Users and Groups, both users have Account type=Administrator.

> **isantop said:**
> Can you check the individual permissions each user has?

The same: for both users, everything is selected. (Note that this appears to be the meaning of "Account type=Administrator": if you uncheck any item, "Account type" changes to "Custom".)

---

### Post by isantop on 2011-04-13
From the user with working sound go to System > Sound from the launcher, then open the Hardware and Input tabs. Make note of how everything is configured. Then, from the user without working sound, go to System > Sound and make sure the settings are identical.

---

