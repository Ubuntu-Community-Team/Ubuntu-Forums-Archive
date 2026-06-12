---
title: "Yet another bloke with qjackctl/alsa/hydro problems"
date: 2009-04-03
forum: Ubuntu Studio
---

### Post by wdudley on 2009-04-03
Allow me to introduce myself to the forum, first post...whoo!

Anyhow, as of late I have been delving into Ubuntu (8.10) and playing with sound programs (JACK/Audacity/Hydrogen/etc). I'll tell you what, It has been driving me insane trying to get stuff to play nice.

First off, I am running qjackctl as gui, as well as Hydrogen; and am currently set up (I guess) to use ALSA. My sound card as seen from lspci reads:

> 00:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)


Now for the problems...

1. The big reoccurring problem is I cannot get any of these programs to make sound. It is nothing like my speaker cable is plugged in wrong because I do get sound from Audacity just fine. I followed jondecker76's guide from [this thread]("http://ubuntuforums.org/showthread.php?t=444824") to attemt to get a connection using Hydrogen, and for some reason it actually WORKED for the first 10 minuites or so. I was even able to use MeterBridge. However, after having bodged an attempt to patch in an effect with JackRack, I lost all sound. Hydro would not play a demo track, and JACK was erroring out the wazoo.

2. After having restarted my computer and reinstalling jackd/qjackctl/hydrogen from the Synaptic Package Manager gui, the only thing I am getting sound from is Audacity. AGAIN. At this point in time however, I can't seem to get anything to want to play nice again no matter what settings I seem to screw with. My general sound preferences are all set to ALSA. Audio system prefs under Hydro are set to JACK. When I start JACK first, then bring up Hydro, I do in fact see a connection from "Hydrogen-1" to "System" (no longer "alsa_pcm"?? was that changed at some point?). Lastly, JACK settings are all default and set to use the ALSA driver. Meterbridge does not see any signal.


 I have not even begun to delve into attempting to set up Audacity to play with JACK yet, at this point in time I would just like to keep playing with the above mentioned programs in order to gain some flexibility with JACK. However that may never happen if I can't get this mess sorted out! Thank you in advance and extra friend points to whoever helps me make this work.

Cheers,
Bill

---

### Post by wdudley on 2009-04-03
New Update...

Sometimes I also get this JACK server connection error; most likely because JACK hates me.

[IMG]http://i724.photobucket.com/albums/ww249/superhiquality87/Screenshot-Messages-JACKAudioConnec.png[/IMG]

Bill

---

### Post by sgx on 2009-04-04
Hi, try starting jackd with this

jackd -d alsa -r 44100

If it starts  without errors, open qjackctl, and try  your connections.
If it still fails, try reinstalling libjack, jackd, qjackctl, hydrogen, and remove ladspa, jack-rack, meterbridge, and all jackd related utilities.  Sometimes the wrong libjack is in place, secretly mucking things up. I have seen issues with jackd 1.09 when used with qjackctl 3.4 also, which maybe QT related, 'System' has a widget by it that expands/contracts to show/hide your alsa_pcm connectors.

Did you make a separate /home partition? This allows a full reinstall without reformatting /home/you-user, thus keeping your critical settings,
and eye-candy in place, making a fresh install trivial. Also, if on dial-up, synaptic allows  the option of saving the new  .deb files in your apt cache (/var/cache/apt/archives ) so you can bank them, and reuse  them as needed with dpkg -i filename.deb. Handy for large files and lists of dependancies.

---

### Post by Stochastic on 2009-04-04
> **sgx said:**
> Did you make a separate /home partition? This allows a full reinstall without reformatting /home/you-user, thus keeping your critical settings,
and eye-candy in place, making a fresh install trivial. Also, if on dial-up, synaptic allows  the option of saving the new  .deb files in your apt cache (/var/cache/apt/archives ) so you can bank them, and reuse  them as needed with dpkg -i filename.deb. Handy for large files and lists of dependancies.

Umm, there's no need to worry about a re-install of ubuntu in the OP's problems.  You're right that this is a handy setup technique, but mentioning it here seems out of place and confusing.

The OP did have jack working, but it looks like something went wrong.  Often a simple reboot (even just a log out/in) will refresh things and you'll be back to normal.

can you post the output of ```
lspci | grep audio
```

---

### Post by sgx on 2009-04-04
> **Stochastic said:**
> Umm, there's no need to worry about a re-install of ubuntu in the OP's problems.  You're right that this is a handy setup technique, but mentioning it here seems out of place and confusing.

The OP did have jack working, but it looks like something went wrong.  Often a simple reboot (even just a log out/in) will refresh things and you'll be back to normal.

can you post the output of ```
lspci | grep audio
```

Bill reinstalled his audio apps with synaptic. This didn't fix it, and a simple reboot is not likely to. People who think jack hates them may need an occasional reinstall, and I want it to be easy in the long run, it made a world of difference to me when I learned this :)
And there are always a few windows newcomers reading things, and storing
up info for the future.

---

### Post by markbuntu on 2009-04-05
Help with jack:

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


Audacity will use jack but it is not a jack app and so you may have problems with using audacity and jack apps together. You will have a smoother experience using ardour with hydrogen once you get it all figured out.

---

