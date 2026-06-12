---
title: "MIDI keyboard won't show up in my DAWs"
date: 2015-11-03
forum: Ubuntu Studio
---

### Post by yoshii on 2015-11-03
OK  I fixed this by first removing all the KXstudio PPA entries from the  Software Center.  Next, I followed somebody's instructions I found  online for removing KXstudio.  It involved "pinning" somethings related  to "Trusty Tahr".  I don't really know what that means, but it was mean  to prevent Ubuntu Trusty Tahr elements from being removed I think.  I  had to create some sort of prefs file also.  Sorry I can't remember the  details.  Anyways, next I removed KXstudio but it didn't remove  everything since it couldn't find some parts of KXstudio.  Then I  triggered software update which said there was some kind of error and it  offered me the chance to do a "partial upgrade" so I did that.   This  resulted in a lot of stuff getting removed and replaced by older  versions I think.  I think this is because KXstudio uses some newer  libraries and stuff than Ubuntu Studio.  All this stuff took about 15  minutes.  

Anyways, after that the MIDI throughputs were still  showing up in my DAWs and blocking access to my Q25 USB MIDI  controller.  So then I did an alsa reload command using "sudo alsa  reload".  
Then when I opened up my DAWs, everything was almost  back to normal except I had to re-select and re-enable my Q25 MIDI  controller.  Now everything is fixed.  

Oddly enough, Xchat was  reinstalled during this process and I don't use it so I had to remove it  again.  But I did that via Software Center.  So now everything is back  to normal.  
On the downside, I can't us all those updated KXstudio  things.  But since it was causing me no access to my USB MIDI inputs, it  was worth it to quit all that junk and go back to Ubuntu Studio.  

Also,  KXstudio had created a menu entry which spontaneously disappeared.  And  that's not good since that was the way to get to all those items  installed.  
So I won't be dabbling with KXstudio anymore. 

> 
I recently installed the KXstudio repositories over ubuntu  Studio v14.04.3 a few days ago and now all of a sudden my Q25 USB MIDI  keyboard is not showing up in any of my DAW programs.  
The computer sees it because it's a USB Class Compliant device (no drivers are needed) and because Patchage shows it.  

But I can't record anything from my keyboard because all of a sudden it's not showing up in my MIDI preferences for each DAW.  
Also, all of a sudden there are 16 MIDI through port for both input and output.  

Can somebody tell me how to get my Q25 back into the MIDI device lists?  
Also is there a way to get rid of all those through ports that I never use?

Alternatively, how could I remove KXstudio?
I tried aplay -l and it shows my Q25 as the last item in the list after all the unused (unneeded) MIDI through ports.


---

### Post by yoshii on 2015-11-03
OK, so I somehow managed to re-install KXstudio components again.  And this time the MIDI stayed normal;  my Q25 USB Controller wasn't lost inside a list of MIDI through ports.  

Part of what I did differently this time was to be selective about which components were installed during Software Update, and then I disabled the KXstudio repos after everything was done.  
I didn't need all of that stuff anyhow.  All I know is that whatever it was... it's subtle.  

All I really wanted was an update of LMMS and I had to enable the KXstudio repos to get that.  Since that's done, it's ok now.  

Also I think a factor was keeping my USB keyboard plugged in while doing all this stuff so that ALSA would've already had it listed.

---

