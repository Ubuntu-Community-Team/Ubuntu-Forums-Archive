---
title: "thunderbird 2 via script: lost audio notify"
date: 2007-08-07
forum: Ubuntuzilla
---

### Post by wilberfan on 2007-08-07
I've mentioned this problem in a couple of other forums (Beginners and General)--but haven't gotten very far.

I originally installed the 2.0.0.0 Thunderbird from a .deb I found somewhere, and I was able to set up the "audio notification" feature (plays a designated .wav file when new mail arrives).   

I then used the Ubuntuzilla script to update to 2.0.0.5, (and, now 2.0.0.6) but the audio notification no longer works.   All I hear on incomming mail is a system beep.   

I'm running a 64-bit Feisty install--but have 32-bit swiftfox and swiftweasels installed, and audio is fine on those...  (And seem to have the suggested 32bit libs already installed?)

I'm too new at this to know for certain it's an ubuntuzilla script problem--but I'm not having this issue on my Sidux (debian) install (admittedly a 32-bit install on a different box?).

---

### Post by nanotube on 2007-08-08
hey, it's me again. :)
so... if you go to edit->preferences in tbird, in the general tab, you select your audio file, and click the "play" button, do you hear the audio?

does the audio file you select play outside of thunderbird? 

do you hear other sounds fine? if you go to system-> pref-> multimedia systems selector, what do you have selected there? does the 'test' work?

well, that's all i can think of for now...

---

### Post by wilberfan on 2007-08-08
> **nanotube said:**
> hey, it's me again. :)

Welcome back!

>  so... if you go to edit->preferences in tbird, in the general tab, you select your audio file, and click the "play" button, do you hear the audio?

No, I don't, actually...

> does the audio file you select play outside of thunderbird?

Yessiree...it do! 

> do you hear other sounds fine? if you go to system-> pref-> multimedia systems selector, what do you have selected there? does the 'test' work? 

Yeah...everything else (auditory-wise) just seems fine and dandy.  It's the same .wav file that played BEFORE I upgraded to 2.0.0.5.    It really seems to be a TBird issue....  And/or the way TBird and the 64-bit OS play together??

---

### Post by nanotube on 2007-08-09
well, i'm pretty stumped, but here are a couple possibly-useful links:

[http://ubuntuforums.org/showthread.php?t=376106](http://ubuntuforums.org/showthread.php?t=376106)
these guys say that thunderbird has trouble playing certain wav files even though these same files play fine otherwise...

[http://ubuntu.philipcasey.com/06/02/2007/mail-alert-in-thunderbird-on-ubuntu-sound-problem-solved/](http://ubuntu.philipcasey.com/06/02/2007/mail-alert-in-thunderbird-on-ubuntu-sound-problem-solved/)
this guy used a workaround - he installed the mailbox alert extension, and that one played sounds just fine.

here's the link to the mailbox alert extension:
[https://addons.mozilla.org/en-US/thunderbird/addon/2610](https://addons.mozilla.org/en-US/thunderbird/addon/2610)

let me know if any of these end up of any use. 
good luck :)

---

### Post by wilberfan on 2007-08-09
Valiant effort, my motivated friend, but no...the plugin didn't help.     The visual popup part of the plugin worked, but still no audio.   No audio when I "test" the plugin, either.    (I DID get a lengthy error message from the plugin that was audio-related.  I couldn't copy/paste however, and it's not appeared since that first time I ran the plugin.)

The same version of Thunderbird works on my Sabayon install....    I even opened the .wav file in question in Audacity, trimmed it, resaved it...and still no go.

I even deleted and copied a TBird profile from my other box, but that didn't help either.

There must be something specific to my Feisty install that's borked?

{Sigh}  I'll just have to wait until Octobers clean-install of Gutsy?!     ;)

---

### Post by nanotube on 2007-08-10
ah, too bad... well, there's one last thing i can try...
install package "esound-clients"

then launch thunderbird with esddsp, from a terminal, like this:
```
esddsp thunderbird
```
and see if it plays your sample wav (and whatever else it needs to play) then.

---

### Post by wilberfan on 2007-08-10
> **nanotube said:**
> ah, too bad... well, there's one last thing i can try...
install package "esound-clients"

then launch thunderbird with esddsp, from a terminal, like this:
```
esddsp thunderbird
```
and see if it plays your sample wav (and whatever else it needs to play) then.

Negatory, Houston...   

I've attached a screenshot of the notify plugin error message I got before...

---

### Post by nanotube on 2007-08-10
gah... a tough nut of a problem...

say, what happens if you open up the error console - does anything interesting show up, as you try to play that wav file? (tools > error console)

---

### Post by wilberfan on 2007-08-10
> **nanotube said:**
> gah... a tough nut of a problem...

say, what happens if you open up the error console - does anything interesting show up, as you try to play that wav file? (tools > error console)

You don't give up easy--I'll give you that!   :)

> 
Error: uncaught exception: [Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsISound.play]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: chrome://messenger/content/preferences/general.js :: anonymous :: line 141"  data: no]

---

### Post by nanotube on 2007-08-10
> **wilberfan said:**
> You don't give up easy--I'll give you that!   :)

heh well... until now - because i'm out of ideas :(. i think you might have better luck if you contact the mozilla people with like a bug report with your sound problem - and that error console message. maybe they'll be able to tell you something.

---

### Post by wilberfan on 2007-08-10
I sincerely appreciate your efforts!   This kind of hand-holding is the reason Ubuntu is my "main" Linux installation!

Given that this all began with the Ubuntuzilla upgrade, I thought I'd start here....but, yes, it may be time to get the Mozilla Folks involved...

Thanks again!

---

### Post by nanotube on 2007-08-10
> **wilberfan said:**
> I sincerely appreciate your efforts!   This kind of hand-holding is the reason Ubuntu is my "main" Linux installation!

Given that this all began with the Ubuntuzilla upgrade, I thought I'd start here....but, yes, it may be time to get the Mozilla Folks involved...

Thanks again!

well, i'm glad you had fun, even though your problem is still unsolved. :)
please, if you get it solved with the help of mozilla people, post back here and let me know what you needed to do to get it fixed...
thanks for sticking with me and not giving up. :)

---

### Post by wilberfan on 2007-08-12
In the interest of thoroughness, I just tried running the uninstall feature of the Ubuntuzilla script, deleting ALL my Thunderbird files, and reinstalling TBird via the script.    Started a NEW profile, and tested the audio notify feature....

Zilch.

Still get this error console entry:

> Error: uncaught exception: [Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsISound.play]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: chrome://messenger/content/preferences/general.js :: anonymous :: line 141"  data: no]

Now [scratching head] which Mozilla guys do I report this to...?  :confused:

---

### Post by wilberfan on 2007-08-12
THIS JUST IN!

I ran the script in uninstall mode, then installed a (64-bit) .deb from here:  [http://ubuntu.iuculano.it/dists/feisty/thunderbird/](http://ubuntu.iuculano.it/dists/feisty/thunderbird/)

It was 'only' version 2.0.0.5...but the audio notify worked!!!     :guitar:  (Hey!  It just went off again!  :)   )

Doesn't this imply that there IS something in the 'zilla script that's causing this 'failure of audio notify' problem?

---

### Post by nanotube on 2007-08-12
> **wilberfan said:**
> 
Now [scratching head] which Mozilla guys do I report this to...?  :confused:

well, this site has a bunch of resources to look at: 
[http://developer.mozilla.org/en/docs/Developing_Mozilla](http://developer.mozilla.org/en/docs/Developing_Mozilla)
either try the irc channel, or one of the forums (choose the appropriate one). :)

---

### Post by nanotube on 2007-08-12
> **wilberfan said:**
> THIS JUST IN!

I ran the script in uninstall mode, then installed a (64-bit) .deb from here:  [http://ubuntu.iuculano.it/dists/feisty/thunderbird/](http://ubuntu.iuculano.it/dists/feisty/thunderbird/)

It was 'only' version 2.0.0.5...but the audio notify worked!!!     :guitar:  (Hey!  It just went off again!  :)   )

Doesn't this imply that there IS something in the 'zilla script that's causing this 'failure of audio notify' problem?

well, my guess would really be that there's something in the mozilla's build of thunderbird, or the interaction between the 32bit build and the 64bit OS. the ubuntuzilla script itself really doesn't do anything besides download the release tar.gz, unzip it into /opt, and put in some symbolic links so you can launch it instead of the repositories version. nothing to do with sound, configuration, profiles, etc.

one thing you could try is just download the tar.gz from mozilla, unzip it manually into some directory in your home dir, and run it from there - see if that gives you audio notify or not. if not, then it's clearly just the mozilla build's interaction with your environment. if it does, then .. well then i'd be really surprised. :)

---

### Post by wilberfan on 2007-08-18
Just to update you with the latest:

I had been using an older version of the Ubuntuzilla script (4.1.1, I think.)   I tried the new script (4.3) on my Pentium 4, Feisty 32-bit:   The audio notify works fine.

I just tried the 4.3 script on the Feisty 64-bit, and the audio notify still does not work.   

Did I mention that a .deb from [here]("http://ubuntu.iuculano.it/dists/feisty/thunderbird/") installs and DOES have a working audio notify on the Feisty 64-bit?)

:confused:

[edit]  Ooops. I did mention that.    What would that .deb be doing differently than your script?

---

### Post by nanotube on 2007-08-18
> **wilberfan said:**
> Just to update you with the latest:

I had been using an older version of the Ubuntuzilla script (4.1.1, I think.)   I tried the new script (4.3) on my Pentium 4, Feisty 32-bit:   The audio notify works fine.

I just tried the 4.3 script on the Feisty 64-bit, and the audio notify still does not work.   

Did I mention that a .deb from [here]("http://ubuntu.iuculano.it/dists/feisty/thunderbird/") installs and DOES have a working audio notify on the Feisty 64-bit?)

:confused:

[edit]  Ooops. I did mention that.    What would that .deb be doing differently than your script?

well, the .deb from there is a native 64bit binary, whereas the ubuntuzilla version is the same 32bit binary, running through the 32bit compatibility libraries...

---

### Post by wilberfan on 2007-08-18
> **nanotube said:**
> well, the .deb from there is a native 64bit binary, whereas the ubuntuzilla version is the same 32bit binary, running through the 32bit compatibility libraries...

I'm too new at this to know how that might contribute to the Ubuntuzilla = No audio, but 64-bit.deb = Audio problem...

:shock:

Does it suggest anything to you?

---

### Post by nanotube on 2007-08-18
> **wilberfan said:**
> I'm too new at this to know how that might contribute to the Ubuntuzilla = No audio, but 64-bit.deb = Audio problem...

:shock:

Does it suggest anything to you?

hehe, it suggests that there may be something missing from the 32bit compatibility libraries... or something weird in the mozilla build of thunderbird...

---

### Post by mainely_linux on 2007-10-20
> **nanotube said:**
> well, i'm pretty stumped, but here are a couple possibly-useful links:
[http://ubuntu.philipcasey.com/06/02/2007/mail-alert-in-thunderbird-on-ubuntu-sound-problem-solved/](http://ubuntu.philipcasey.com/06/02/2007/mail-alert-in-thunderbird-on-ubuntu-sound-problem-solved/)
this guy used a workaround - he installed the mailbox alert extension, and that one played sounds just fine.
good luck :)

This one worked for me.  I found this forum after googleing for this same issue after upgrading to Gutsy Gibbon.  This particular add-on doesnt immediately fix the problem when selecting a wav to play.  However if you choose the "Run command" option it does.

I entered: /usr/bin/play /usr/share/sounds/KDE_Beep_Yo.wav in the run field and it works now :)

Problem solved for now, ideally thunderbird should be able to play a wav file on new message though!

---

### Post by nanotube on 2007-10-20
> **mainely_linux said:**
> This one worked for me.  I found this forum after googleing for this same issue after upgrading to Gutsy Gibbon.  This particular add-on doesnt immediately fix the problem when selecting a wav to play.  However if you choose the "Run command" option it does.

I entered: /usr/bin/play /usr/share/sounds/KDE_Beep_Yo.wav in the run field and it works now :)

Problem solved for now, ideally thunderbird should be able to play a wav file on new message though!

cool, thanks for sharing this workaround! :)

---

