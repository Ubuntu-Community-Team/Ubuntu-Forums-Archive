---
title: "Recording from sound card?"
date: 2009-04-05
forum: Ubuntu Studio
---

### Post by svivian on 2009-04-05
I asked this several months ago and was directed to here: [http://ubuntuforums.org/showthread.php?p=5817175#post5817175](http://ubuntuforums.org/showthread.php?p=5817175#post5817175)

I did have it set up and working so I could record from my sound card, however, the "sudo modprobe snd-aloop" command isn't working any more. I get an error, "FATAL: Module snd_aloop not found." Plus the method I was using was annoying (running several commands to record some sound, then opening that in Audacity).

Since I did this Ubuntu has been upgraded to Intrepid, so I'm wondering if there are better solutions around now? Hopefully a single program?

Very simply, I want to do two things:
* Record audio from my sound card (e.g. grab the audio from a video file).
* Edit the audio. I have Audacity for this but if there are better apps let me know.

---

### Post by markbuntu on 2009-04-05
try this for recording with audacity in Intrepid

[http://ubuntuforums.org/showthread.php?t=1005196](http://ubuntuforums.org/showthread.php?t=1005196)

if you want a better recording/editing app then you should consider ardour/jack or the Ubuntustudio but the learning curve is very steep. Also, Intrepid rt kernel is broken so results may be less than good. If you want to go to ubuntustudio and ardour it would be best to stay with 8.04 for now.

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

Excellent ardour tutorial here:

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

If you are wondering how to sync applications together through jack:

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

---

