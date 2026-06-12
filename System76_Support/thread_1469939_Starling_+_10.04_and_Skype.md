---
title: "Starling + 10.04 and Skype"
date: 2010-05-02
forum: System76 Support
---

### Post by Tart on 2010-05-02
Does any one having problem with skype after 10.04 upgrade? I have sound issues. I found older version - fixed sound, but it crashes often (for example every time I try to chat with some one)

---

### Post by thomasaaron on 2010-05-03
I've not tested Skype yet. But that latest version available for Skype is still the one optimized for Ubuntu 8.10. 

It seems development has ceased on it -- at least Ubuntu-optimized development. If I'm correct on this, it is going to become harder and harder to get Skype to work as Ubuntu progresses. 

It might be time to start looking for an alternative to Skype.

---

### Post by Tart on 2010-05-03
Previously we were able to resolve this problem by installing older vesrion. This time older version crashes when you try to chat. hmmmmmm.

---

### Post by bill516 on 2010-05-04
I have that same Skype problem with 10.04.  Solved it by just using one of my other distros (Linux Mint).

BTW, am I the only person who finds Linux implementations of sound to be a mess?  ALSA?? Pulse Audio??  Mix A, Mixer B, etc?

Not good, it seems to me.  And hardly a unique Ubuntu problem.

---

### Post by msrinath80 on 2010-05-04
bill516, you are not alone. Sound implementations were nothing short of *excellent* until this pulse audio crap kicked in. If one were to extrapolate using previous indications, chances are that the situation will improve as the pulse technology matures.

---

### Post by Tart on 2010-05-04
> **bill516 said:**
> I have that same Skype problem with 10.04.  Solved it by just using one of my other distros (Linux Mint).

Where can I find another version? There is Debian Lenny on skype website. But it crashes during chat. 
I also fund this post it seems to help to some people. Didn't work for me though :-(

[http://ubuntuforums.org/showpost.php?p=8364091&postcount=12]("http://ubuntuforums.org/showpost.php?p=8364091&postcount=12")

---

### Post by Tart on 2010-05-04
Magic happened and skype works now. Now I have to replicate it on my wife's Starling.  This post helped me although I'm not sure how

[http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html]("http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html")
I uninstalled pulseauio, installed esound, and was able to specify different audio device in skype. But the sound quality was terrible, and I couldn't even open "System > Sound". So I uninstalled esound and installed pulseaudio back, and now skype works.

I'll try to replicate it tomorrow, and figure out exactly what steps are needed.

---

### Post by cposs on 2010-05-05
My Starling is running the newest version of Skype from their website.  My audio output and even video were working fine, but not the audio input.  I found [this other thread from the forums]("http://ubuntuforums.org/showpost.php?p=9144905&postcount=17") after some googling.  It doesn't mater which channel you turn off, either worked for me.  Seems like something in Lucid's pulseaudio setup expects the mono microphone to be stereo or something like that.

---

### Post by kennedyjch on 2010-05-05
Had Skype running on 9.10 with audio, video and chat and no problems... Installed 10.04 and Skype fails to make test call - it immediately errors out. Test sound works fine, though... Any clues???

---

### Post by kennedyjch on 2010-05-05
> **kennedyjch said:**
> Had Skype running on 9.10 with audio, video and chat and no problems... Installed 10.04 and Skype fails to make test call - it immediately errors out. Test sound works fine, though... Any clues???

OK. I unstalled pulseaudio with synaptic and reinstalled and guess what??? Starts to work...

---

### Post by Tart on 2010-05-05
> **Tart said:**
> 
I'll try to replicate it tomorrow, and figure out exactly what steps are needed.

Hmmm cannot replicate :-(. Grrrrrrr. It is definitely pulse audio problems.
[URL="https://help.ubuntu.com/community/Skype"]
https://help.ubuntu.com/community/Skype[/URL] They describe possible solution. But then I set up input device to mono, volume drops so in skype test call I can hear only first word or two. You can see levels drop in real time.

Two links that may help someone to figure it out. Too tired today

[http://www.pulseaudio.org/wiki/PerfectSetup#Skype]("http://www.pulseaudio.org/wiki/PerfectSetup#Skype")

[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by powerofpi on 2010-05-05
> **cposs said:**
> My Starling is running the newest version of Skype from their website.  My audio output and even video were working fine, but not the audio input.  I found [this other thread from the forums]("http://ubuntuforums.org/showpost.php?p=9144905&postcount=17") after some googling.  It doesn't mater which channel you turn off, either worked for me.  Seems like something in Lucid's pulseaudio setup expects the mono microphone to be stereo or something like that.

You are my hero! Installing pavucontrol and then dragging one of the two microphone channels to zero solved my problem! Apparently the two channels must be about 90I now have Skype 2.1 working blissfully with Ubuntu 10.4. Thank you! I've been searching for answers for this forever!

---

### Post by Tart on 2010-05-05
got it working, not sure how :-)

---

### Post by gerowen on 2010-05-06
> **powerofpi said:**
> You are my hero! Installing pavucontrol and then dragging one of the two microphone channels to zero solved my problem! Apparently the two channels must be about 90I now have Skype 2.1 working blissfully with Ubuntu 10.4. Thank you! I've been searching for answers for this forever!

Yeah this fixed mine, for some reason it thinks my microphone is stereo, :p.

---

