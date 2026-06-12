---
title: "Sound problems with LMMS and Hydrogen"
date: 2009-11-14
forum: Ubuntu Studio
---

### Post by Acradon on 2009-11-14
Hello!

Have recently upgraded my pc to 9.10 and today I downloaded LMMS and Hydrogen 0.9.3.

I first tried Hydrogen and it worked well enough except that the tracks became more and more clipped and jumpy over time. So I left that for the moment and tried LMMS. 

First of all I stared,then tried a couple of things and then went to Youtube. I tried to apply the knowledge provided there (mobilephpone2003), only to hear....nothing.  Its as if the play button isn't working 'cos the white line doesn't move, the green lights don't light and of course no music. And after that I tried Hydrogen just to see and it had stopped working altogether.
   
Sound card nVidia Realtech ALC6620 REV1

Any ideas?

Acradon

---

### Post by sgx on 2009-11-14
> **Acradon said:**
> Hello!

Have recently upgraded my pc to 9.10 and today I downloaded LMMS and Hydrogen 0.9.3.

I first tried Hydrogen and it worked well enough except that the tracks became more and more clipped and jumpy over time. So I left that for the moment and tried LMMS. 

First of all I stared,then tried a couple of things and then went to Youtube. I tried to apply the knowledge provided there (mobilephpone2003), only to hear....nothing.  Its as if the play button isn't working 'cos the white line doesn't move, the green lights don't light and of course no music. And after that I tried Hydrogen just to see and it had stopped working altogether.
   
Sound card nVidia Realtech ALC6620 REV1

Any ideas?

Acradon

Hi, I would use synaptic to reinstall your audio apps. Then try just hydrogen again. If it works, but still is choppy, the D110 kit is the smallest, so try that to see if it improves.
You may need the realtime kernel, so install that, and add this

@audio          -       rtprio           90
@audio          -       nice             -10
@audio          -       memlock          unlimited

 to the end of this textfile:

/etc/security/limits.conf

Then, make sure you are a member of the audio group, there is a configuration utility to help users/groups editing.

Then reboot, selecting the new rt kernel, and try again.
Its a great drum machine, and can host ladspa fx, or better, be routed to
rakarrack multi-fx, its EQs do wonders for hydrogen drums! 

At times, you may need to restart the hydrogen jackd connection from the menu:
tools preferences audio system 'restart output' button.
Lots of options to study, right and left click on things etc etc, the logic of adding/creating extra patterns, and placing them in your song grid, very flexible
google for extra drumkits.

see recent posts regarding jackd/audacity for recording drums in audacity.

ladspa fx include

tap, caps, vco, swh, rev, omins, and others

Cheers

---

