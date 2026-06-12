---
title: "sound on Windows under Virtualbox no Audio"
date: 2014-01-27
forum: Virtualisation
---

### Post by jhay2 on 2014-01-27
Hello , i am currently install Windows Xp inside Virtualbox 
I 'd set Audio drivers with Pulseaudio and ICH AC97 , and i installed Windows XP audio driver 
Windows Xp start with no error appears, 

Volume Icon is already there , but still i can't here sound. 


Please Help ,Sorry for my bad english

---

### Post by ajgreeny on 2014-01-27
Do you have the PUEL version of VB direct from Oracle, or the open-source version from the repos?
Do you have the VB Guest additions installed in VB?

---

### Post by jhay2 on 2014-01-27
My virtualbox was came from the oracle website it was actually Vbox 4.3.6 version. I'd already installed vbox guest addition . But still i can't hear any sound

---

### Post by ajgreeny on 2014-01-27
Have you set sound volume levels in both host and guest?

---

### Post by jhay2 on 2014-01-27
Yes i did that. 
my host ubuntu has sound but on my windows guest doesn't have any sound

---

### Post by jhay2 on 2014-01-28
:(

---

### Post by jhay2 on 2014-01-29
please help

---

### Post by QIII on 2014-01-29
Hello!

Are you using speakers attached to your onboard audio out, or a sound/video card?

---

### Post by jhay2 on 2014-01-29
No. i am using builtin speaker only

---

### Post by jhay2 on 2014-02-10
?/

---

### Post by vermontbear on 2014-11-13
Interesting that this thread is here, unresolved. All my experiments with Ubuntu and Virtualbox from Hardy through Precise tend to indicate that Ubuntu 12.04 has an unresolved bug. I've done 8 different test installs of 12.04 over the past two-and-a-half years; in all tests with all versions of Virtualbox guests running various Windows versions, the sound from VB back to the host is truncated. You get a half-second of music, done.  Bug seems to be there only with 12.04, no matter if you are running Unity, Mate, Gnome, Mint, Cinnamon.. whatever. 14.04 works fine. 10.04 works fine... and pretty much all versions in between. Just a bug in 12.04. 

Given that 12.04 is an LTS, might be nice if it did work rightly. But, in that this thread has 800-or-so views, doesn't look like a lot of people in the universe are bothered.

---

