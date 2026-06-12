---
title: "Pro Audio recording/composing"
date: 2011-11-30
forum: Ubuntu Studio
---

### Post by de Bacon on 2011-11-30
I have used the windows Cakewalk Pro Audio 9 on my old win 98 machine for many years now.  I would like to abolish that system and convert to an equivalent music recording system with Ubuntu Studio.  Problem is I don't know that there is such a thing. 

I record my own music using direct analog inputs, mixed with midi to create my music.  My goal is to do it with the Linux system rather than the clunky old P-III 500 Ghz machine.

Anyone know of the solution?

---

### Post by jejeman on 2011-11-30
I gues Muse is the closest to cakewalk.

---

### Post by de Bacon on 2011-11-30
jejeman, thanks,

I guess it might be too narrow in saying a cakewalk equivalent.  I should say that I want something that will give a like end result, mixing down midi/audio files into wave files suitable for putting on a CD to be played in any standard CD player or mix down to mp3 for net distribution.

Thanks again,

---

### Post by jejeman on 2011-12-01
Muse can mixdown midi & audio. 
Also with audio/midi capatibilities there are Qtractor, Rosegarden and Ardour 3 beta.

---

### Post by eric71 on 2011-12-02
Hi. Is music notation important to you? If so, Rosegarden is your best bet.

If not, you might try Qtractor - it's lighter and can handle all the midi and audio you throw at it.

But probably the best solution right now that would be able to match Cakewalk might be Reaper via Wine and Wineasio. This has the added bonus of still being able to use your Windows vst's and vsti's.

Soon enough (but not yet) Ardour 3 should give you everything you need natively in Linux.

---

### Post by de Bacon on 2012-05-01
> **eric71 said:**
> Hi. Is music notation important to you? If so, Rosegarden is your best bet.

If not, you might try Qtractor - it's lighter and can handle all the midi and audio you throw at it.

But probably the best solution right now that would be able to match Cakewalk might be Reaper via Wine and Wineasio. This has the added bonus of still being able to use your Windows vst's and vsti's.

Soon enough (but not yet) Ardour 3 should give you everything you need natively in Linux.


Eric,
Thanks for the info.  All this time later, I have yet to move on this desired project due to the technical issues involved in set-up.  For me it is very difficult to get many things to work in Linux due to my own ignorance with computing.  (I still use Cakewalk pro-audio 9 on a different and isolated (off line) system that runs win-98).  I know that old system will one day crash and burn as these computers don't last forever.  I really don't wish to use wine.  Maybe it is my experience with it in the past, trying to get cakewalk to work with it :/ , or just lazy. 

Does anyone think Ardour is currently a good solution.  In looking at the repository info (current today) in the dependencies tab it states that Ardour is in conflict with Ardour?  That doesn't make sense to me, causing me to wish to avoid an attempt to set it up, for the possibility of it being a total waste of energy/time.   

Any thoughts from anyone would be appreciated.  

Thanks,
Then Play On  :guitar:

---

### Post by sgx on 2012-05-01
Use reaper, with wineasio. Installs into one folder, 

wine reaper422-install.exe

then install wineasio, and run

regsvr32 wineasio

Using it since 2.xx
Cheers
get ardour3 beta, it is a binary install,
no repos, and qtractor has been improving a lot.

---

