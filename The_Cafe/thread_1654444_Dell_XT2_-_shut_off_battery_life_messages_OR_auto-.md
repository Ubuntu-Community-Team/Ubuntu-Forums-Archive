---
title: "Dell XT2 - shut off battery life messages OR auto-rotate screen"
date: 2010-12-28
forum: The Cafe
---

### Post by cadbrowne on 2010-12-28
The problem I have is actually a vista one, however, google keeps leading me to the Ubuntu forums, so -- who knows? -- maybe someone here can point me in the right direction. (I DO use Ubuntu at home, but at work, I can't). Please forgive me if this is not the proper place to ask this.
 
Here is my problem:
 
We support over 3,000 Dell XT2 tablets. When the battery life (NOT to be confused with battery CHARGE) dips to 75%, users start getting popups stating that their battery life is decreasing. There is a checkbox that is SUPPOSED to turn off this reminder, but it doesn't work. At 50% battery life, the message changes to one that says the battery is nearing the end of its usable life. By that time, however, most users are so used to ignoring the popups, they don't notice the change - OR they've gotten so annoyed with them, that they have already replaced the battery long before it was necessary. 
 
These messages are coming from Dell's "Control Point" software. If we turn that software off, the message stop. HOWEVER, the tablet screen will no longer auto-rotate.
 
Dell is telling me "it will be fixed in the next release". But with 3000+ annoyed users, that's not really what I want to hear. They also tell me that there is "no way" to either 
1) Turn off the battery messages without turning off other vital functions (not true - unless you consider Dell Control Point to be vital. Except for the screen auto-rotate function, I don't.)
2) Enable auto-rotate without using Dell Control Point to do it. 
 
Since it is possible to get an XT2 to auto-rotate in Ubuntu, then the auto-rotate function is NOT as proprietary as Dell would have me believe. The trouble is - how can it be done? THEY are not likely to tell me. GOOGLE thinks you folks are the experts on the subject. :-)
 
So, even though I am trying to do this on Vista machines... do any of you know where I could BEGIN to look for a way to do this?
 
Many thanks in advance!

---

### Post by Favux on 2010-12-28
Hi cadbrowne,

Welcome to Ubuntu forums!

See the N-trig HOW TO near the top:  [http://ubuntuforums.org/showthread.php?t=1252492](http://ubuntuforums.org/showthread.php?t=1252492)  for links.

Basically we are using the the dell-wmi/Dell Hotkeys for autorotation.  By establishing a device node (/dev/input/dell-wmi) we are able to read the node.  Linux tools like evtest and xxd can then read the output.  That's for our python Magick Rotation applet.  Rafi Rubin has a Perl script that does something similar.  They both require Rafi's modified dell-wmi because the one that comes with the linux kernel doesn't report the swivel hinge state.  Unfortunately when Rafi tried to submit patches for his modification they were declined because they didn't proactively poll the hinge state.  With the HP's we can get the info. from the BIOS, but not the Dell's.  So it will partly depend on whether the Windows dell-wmi does report the hinge switch state.

---

