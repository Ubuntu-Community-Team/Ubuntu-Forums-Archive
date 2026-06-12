---
title: "NVIDIA SUX. Please read to know why!"
date: 2006-03-20
forum: The Cafe
---

### Post by vnbuddy2002 on 2006-03-20
GLX_EXT_texture_from_pixmap will not be supported in the next release. that is an official announance from nvidia.


"NVIDIA Clarification
We have just been notified by NVIDIA's Aaron Plattner that there are a few corrections to be made when it comes to NVIDIA's upcoming Linux driver release. First off, the GLX_EXT_texture_from_pixmap extension has yet to be finalized, and thus it will not be supported in the upcoming Linux driver release. What this means is no AIGLX under NVIDIA for quite some time, unless things change. As NVIDIA's proprietary drivers do not use DRI, they are waiting upon the GLX_EXT_tfp extension to be finalized and upon the preceding driver release it will support the ability to run Compiz and the AIGLX project's updated version of Metacity. Other than the few clarifications to note, we are still working with the 1.0-8751 Linux display drivers."

---

### Post by mstlyevil on 2006-03-20
[QUOTE=vnbuddy2002]GLX_EXT_texture_from_pixmap will not be supported in the next release. that is an official announance from nvidia.


"NVIDIA Clarification
We have just been notified by NVIDIA's Aaron Plattner that there are a few corrections to be made when it comes to NVIDIA's upcoming Linux driver release. First off, the GLX_EXT_texture_from_pixmap extension has yet to be finalized, and thus it will not be supported in the upcoming Linux driver release. What this means is no AIGLX under NVIDIA for quite some time, unless things change. As NVIDIA's proprietary drivers do not use DRI, they are waiting upon the GLX_EXT_tfp extension to be finalized and upon the preceding driver release it will support the ability to run Compiz and the AIGLX project's updated version of Metacity. Other than the few clarifications to note, we are still working with the 1.0-8751 Linux display drivers."[/QUOTE]

They are still lightyears ahead of ATI in the Linux driver department.

---

### Post by GameGod on 2006-03-20
How can you blame NVIDIA for not implementing an unfinished specification?

**Edit:** My bad, it's a GLX extension, and has nothing to do with the OpenGL Consortium...

---

### Post by mega on 2006-03-20
it sucks, but is the spec done?


the alternative to nvidia sucks even more though

---

### Post by ssam on 2006-03-20
lets hope the open graphics card arrives soon.

i have an old radeon :-) good open source drivers.

---

### Post by chadwick359 on 2006-03-20
We're using linux. Graphic card driver suck period, but nVidia's are still by far the best.

And wait, why is this in the dapper forums? Shouldn't this be in the Cafe?

---

### Post by elanthis on 2006-03-20
AAgh!

(1) The ****ing specification isn't bloody done yet.  NVIDIA would be retarded to include a non-finalized spec in an official supported driver release.  I've said it before and I'll say it again: this XGL/Compiz crap is NOWHERE NEAR stable, and that includes THE TECHNOLOGY THEY ARE BUILT ON, get some patience and learn to wait until the developers finish everything off.

(2) The OpenGL consortium has NOTHING TO DO with this, so don't blame them either.  This extension is NOT an OpenGL extension, it's a GLX extension.

(3) GLX is not the same as XGL.  Nobody's made that confusion in this thread yet, but they have in almost every other related thread, so let's nip this in the bud right here.  GLX is "OpenGL on X" and XGL is "X on OpenGL."  The former allows OpenGL apps to operate on top of the X windowing environment, the second allows the X windowing environment backend to be based on GLX (like Xglx) or on EGL (like Xegl).

(4) Did I mention that XGL/Compiz ARE NOT READY FOR PRIME TIME YET and that you need to get some freakin' patience and wait several MONTHS for the requisite technologies to be hashed out and for the software to stabilize and for the underlying protocols to quit changing?

---

### Post by WildTangent on 2006-03-20
[QUOTE=elanthis]AAgh!

(1) The ****ing specification isn't bloody done yet.  NVIDIA would be retarded to include a non-finalized spec in an official supported driver release.  I've said it before and I'll say it again: this XGL/Compiz crap is NOWHERE NEAR stable, and that includes THE TECHNOLOGY THEY ARE BUILT ON, get some patience and learn to wait until the developers finish everything off.

(2) The OpenGL consortium has NOTHING TO DO with this, so don't blame them either.  This extension is NOT an OpenGL extension, it's a GLX extension.

(3) GLX is not the same as XGL.  Nobody's made that confusion in this thread yet, but they have in almost every other related thread, so let's nip this in the bud right here.  GLX is "OpenGL on X" and XGL is "X on OpenGL."  The former allows OpenGL apps to operate on top of the X windowing environment, the second allows the X windowing environment backend to be based on GLX (like Xglx) or on EGL (like Xegl).

(4) Did I mention that XGL/Compiz ARE NOT READY FOR PRIME TIME YET and that you need to get some freakin' patience and wait several MONTHS for the requisite technologies to be hashed out and for the software to stabilize and for the underlying protocols to quit changing?[/QUOTE]
And did I mention yet that you might want to stay on your meds? Seriously, calm down...

-Wild

---

### Post by briancurtin on 2006-03-20
yeah man they suck! never use their stuff! serenity now! 


nice thread...
i like nvidia and the nvidia drivers

---

### Post by DigitalDuality on 2006-03-20
My problem with nvidia is the same as my problem with ATI... and that's TCPA compliance.   that aside, Nvidia rocks my socks

---

### Post by jdong on 2006-03-20
No, no, NVidia blows. Choose ATI. They have a whole line of enterprise video chipsets specifically aimed at Linux animation customers, or has offered updated drivers that are ready for the latest and greatest. It's not like NVidia, which took several years to support the 2.6 kernels, and several more to get the message that everyone's moved to Xorg.

Oh wait, I might've gotten the two flipped....

---

### Post by Jedeye on 2006-03-20
Nvidia is OK in my book

---

### Post by ComplexNumber on 2006-03-20
i have been led to believe from everything that i've read so far that nvidia is the superior(ie to ATi). the reasoning being something along the lines that nvidia are better equipped and more powerful.
i have no idea how what is written by the OP has any impact on me as an nvidia user :confused:

---

### Post by dasunst3r on 2006-03-20
I have to disagree.  I took me 4 tries to get the ATi driver working on my laptop and some convoluted configuration while on my desktops, I had to install, change "nv" to "nvidia," and bring X back up.  The latter procedure was a lot easier, but I can do any of them easily in SUSE now.

---

### Post by psylence on 2006-03-20
[QUOTE=ssam]lets hope the open graphics card arrives soon.[/QUOTE]

Oh yeah, any day now I'm sure.

It'll also be 200% faster because it'll be powered by FREEDOM.

---

### Post by MetalMusicAddict on 2006-03-20
[QUOTE=psylence]Oh yeah, any day now I'm sure.

It'll also be 200% faster because it'll be powered by FREEDOM.[/QUOTE]

Damn you. Im sick and the laugh I got hurt. :)

---

