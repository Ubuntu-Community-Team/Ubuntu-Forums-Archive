---
title: "Sony MD-Walkman and ubuntu?"
date: 2008-08-01
forum: The Cafe
---

### Post by Mzwo on 2008-08-01
hi all,

has anyone managed to make a sony md-walkman (MZ-NH900, to be precise) talk to ubuntu via usb?
i work in broadcasting, use the md-recorder daily and would quite like to import audio data directly for editing.

any tips? (greenhorn alert - hold the jargon, please)

much obliged,

Mzwo

---

### Post by hessiess on 2008-08-01
I have a MZ-NH600 and have had ABSOLUTLY NO sucksess at getting linux to reconise it. even mount as a disk drive. Which is why im planning on getting rid of it.

you may want to check this
[http://forums.minidisc.org/index.php?showtopic=16688](http://forums.minidisc.org/index.php?showtopic=16688)

---

### Post by speedwell68 on 2008-08-01
I have tried the SonicStage software under Wine and Crossover Office with zero success, I have a small Windows partition purely for putting music on an MD.  It is a PITA, but I only use it to record discs to listen to on my in car player.  So I am not that bothered really.

---

### Post by speedwell68 on 2008-08-02
Ok, I have got it working.  I used Sun VirtualBox to boot Windows XP.  I installed VirtualBox using the Deb file on Sun's website and then this how to, to get USB working under Windows.

[http://ubuntuforums.org/showpost.php?p=4617632&postcount=12](http://ubuntuforums.org/showpost.php?p=4617632&postcount=12)

---

### Post by speedwell68 on 2008-08-02
To follow on with this.  I had problems mounting an audio CD in Vitual XP, so I have found the easiest way is make an ISO image of the files you want to put on an MD, using **mkisofs** and the mounting that image as a Virtual CD under virtual box and then copying them to the Windows desktop.  I hope all of that makes sense.

---

### Post by Mzwo on 2008-08-09
making sense? erm, sort of :)

thanks for the suggestions, seems a little complicated. 
tried sonicstage under wine too, wouldn't even let me install. ah well. 

cheers,

Mzwo

---

