---
title: "Mouse"
date: 2011-11-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by matt_symes on 2011-11-25
Is anybody else having the occasional trouble with their mouse since the new kernel was installed ?

```
matthew@matthew-Aspire-7540:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Video WebCam                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
matthew@matthew-Aspire-7540:~$ 
```Every once in a while i have lost the mouse after booting. Nothing in any logs.

Unloading and reloading psmouse.ko solves the issue. 

Thinking of raising a bug as this will be a major show stopper for the average user, but wanted to see if i'm the only one here.

This install is an update from Natty->Oneiric->Precise (the other reason i want feedback).

```

matthew@matthew-Aspire-7540:~$ uname -a
Linux matthew-Aspire-7540 3.2.0-1-generic #3-Ubuntu SMP Tue Nov 22 11:17:48 UTC 2011 i686 athlon i386 GNU/Linux
matthew@matthew-Aspire-7540:~$ 
```

---

### Post by bluexrider on 2011-11-25
**Ubuntu +1 (Precise Pangolin)**
 This  forum is for the discussion of the development of the next version of  Ubuntu (Precise Pangolin). Precise is in development and will be  released in April 2012. Please note: Ubuntu Developers do not usually  read the forums, to report a problem found in Precise please report the  bug in [Launchpad]("https://launchpad.net/ubuntu/+filebug").

I think I would report it.

---

### Post by cariboo on 2011-11-25
> **bluexrider said:**
> **Ubuntu +1 (Precise Pangolin)**
 This  forum is for the discussion of the development of the next version of  Ubuntu (Precise Pangolin). Precise is in development and will be  released in April 2012. Please note: Ubuntu Developers do not usually  read the forums, to report a problem found in Precise please report the  bug in [Launchpad]("https://launchpad.net/ubuntu/+filebug").

I think I would report it.

What's your point, If you look, you'll see that matt_symes is running kernel version  3.2.0-1-generic #3, which is the kernel that Precise is currently using.

---

### Post by effenberg0x0 on 2011-11-25
> **matt_symes said:**
> Is anybody else having the occasional trouble with their mouse since the new kernel was installed ?

```
matthew@matthew-Aspire-7540:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Video WebCam                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
matthew@matthew-Aspire-7540:~$ 
```Every once in a while i have lost the mouse after booting. Nothing in any logs.

Unloading and reloading psmouse.ko solves the issue. 

Thinking of raising a bug as this will be a major show stopper for the average user, but wanted to see if i'm the only one here.

This install is an update from Natty->Oneiric->Precise (the other reason i want feedback).

```

matthew@matthew-Aspire-7540:~$ uname -a
Linux matthew-Aspire-7540 3.2.0-1-generic #3-Ubuntu SMP Tue Nov 22 11:17:48 UTC 2011 i686 athlon i386 GNU/Linux
matthew@matthew-Aspire-7540:~$ 
```

I'm not using a laptop anymore, so I don't have hardware to test a touchpad. However, I remember that during Oneiric pre-release stage, there were some users here with this touchpad sudden death thing happening frequently. I suggested something to wake up the mouse that seemed to work. See this thread:
[http://ubuntuforums.org/showthread.php?t=1852081&highlight=touchpad](http://ubuntuforums.org/showthread.php?t=1852081&highlight=touchpad)
It might be the same bug back again, whatever it is.

EDIT: Please do search launchpad for similar reports and report what you're seeing there. A bug in a vital input device shouldn't spread by two releases...

---

### Post by matt_symes on 2011-11-25
Hi

> **effenberg0x0 said:**
> I'm not using a laptop anymore, so I don't have hardware to test a touchpad. However, I remember that during Oneiric pre-release stage, there were some users here with this touchpad sudden death thing happening frequently. I suggested something to wake up the mouse that seemed to work. See this thread:
[http://ubuntuforums.org/showthread.php?t=1852081&highlight=touchpad](http://ubuntuforums.org/showthread.php?t=1852081&highlight=touchpad)
It might be the same bug back again, whatever it is.

EDIT: Please do search launchpad for similar reports and report what you're seeing there. A bug in a vital input device shouldn't spread by two releases...

Thanks for this effenberg0x0.

Kind regards

---

### Post by effenberg0x0 on 2011-11-25
> **matt_symes said:**
> Hi



Thanks for this effenberg0x0.

Kind regards
Just out of curiosity, did that command also worked for you?

---

### Post by mc4man on 2011-11-25
**If it's the cursor freeze** as mentioned by effenberg0x0 then that bug is still quite alive.
The most relevant bug is here - though there at least 2 separate bugs discussed there
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/868400](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/868400)

For the cursor freeze where the mentioned command works to 'unfreeze'
synclient TouchpadOff=0

then there are 3 current options
this should fix fairly well, though touchpad will remain active
```
gsettings set org.gnome.settings-daemon.peripherals.touchpad disable-while-typing true
```

This should be 100% effective, renders the above option moot so again the touchpad remains active
```
gsettings set org.gnome.settings-daemon.plugins.mouse active  false
```

Or if one needed/wanted the touchpad inactive while typing the just run the synclient command when it happens - can be loaded into the Alt+F2 history if not wanting to type out per occurrence

As usual with these behaviors hardware plays a factor.

---

### Post by matt_symes on 2011-11-25
Hi

> **effenberg0x0 said:**
> Just out of curiosity, did that command also worked for you?

I will have to wait for the bug to raise its head again. It's intermittent. 

I will post back when it happens again.

Kind regards

---

### Post by ventrical on 2011-11-25
Here is my config. All is working well with touchpad.


ventrical@ventrical-Extensa-4420:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB OPTICAL MOUSE                           id=10    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Acer CrystalEye webcam                      id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
ventrical@ventrical-Extensa-4420:~$ 

ventrical@ventrical-Extensa-4420:~$ uname -a
Linux ventrical-Extensa-4420 3.2.0-2-generic #4-Ubuntu SMP Fri Nov 25 10:47:30 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-Extensa-4420:~$

---

### Post by matt_symes on 2011-11-26
Thanks for the replies on this.

---

### Post by matt_symes on 2011-11-27
. Duplicate post.

---

### Post by matt_symes on 2011-11-27
Hi effenberg0x0

I can confirm that 

```
synclient TouchpadOff=0
```

fixes this issue with the touchpad. Basic things i checked before trying the above commands.

psmouse was loaded. Mouse was enabled with xinput. Logs were empty.

I have not tried the gsettings commands. I will try them after i next get a freeze.

This bug has obviously raised its head again. I will look on Launchpad for an existing bug when i get the time.

Do you think its worth me uploading the specs (logs etc) of my machine to Launchpad ? I am not interested in adding a "me to" comment to an existing bug unless i can add something to it.

Kind regards

---

### Post by mc4man on 2011-11-27
I'm not sure a new report will matter much, likely will end up duped to one I posted.

I've just taken to using the the 2nd gsetting command which has prevented the cursor freeze from ever occurring at the cost of having it active while typing

Taking a look back at my orig. report reminded of one additional option, disable the mouse thru gsettings, then enabling the option thru syncdaemon directly, as I remember that seemed to work ok. 
(an active touchpad while typing isn't an issue here so never gave it an extended test which here would have been at least a week of no occurances

You can try that by doing the gset, then Alt+F2
```
syndaemon -d -k -i 0.5s
```
Will last per session, can be made into a startup option if of value/success

---

### Post by effenberg0x0 on 2011-11-27
> **mc4man said:**
> I'm not sure a new report will matter much, likely will end up duped to one I posted.

I've just taken to using the the 2nd gsetting command which has prevented the cursor freeze from ever occurring at the cost of having it active while typing

Taking a look back at my orig. report reminded of one additional option, disable the mouse thru gsettings, then enabling the option thru syncdaemon directly, as I remember that seemed to work ok. 
(an active touchpad while typing isn't an issue here so never gave it an extended test which here would have been at least a week of no occurances

You can try that by doing the gset, then Alt+F2
```
syndaemon -d -k -i 0.5s
```Will last per session, can be made into a startup option if of value/success

@matt_symes there's a "This bug affects me" button in Launchpad. The higher that number, the hotter the bug is. In theory, this index should draw attention to it.

@mc4man
This is one that I strongly feel you should add to our upcoming bug thread here as there will be users opening support threads requesting help with it when PP is released, if it's not fixed before. These workarounds (syndaemon, gsettings) fit the workaround info field in the proposed bug thread structure. Doing it, you will ensure that all of us will test it and and follow up with this bug report, "+1" there to request it is fixed, etc. We will do our part of the thing as testers (keeping track that it still doesn't behave properly and push things) and developers should do theirs. I feel like we (I, at least) haven't sometimes pushed enough during OO cycle, but we can do it now.

---

### Post by mc4man on 2011-11-29
nv - I had modified something

---

### Post by effenberg0x0 on 2011-11-29
Unless this bug gets fixed in the next 150 days, I am very sure it will a frequent complain at General Help. We could spare the time every helper will take to to search Launchpad and browse the entire forum to find the workaround commands by putting this one in our BUG sticky :) I think this is a very important one.

---

### Post by matt_symes on 2011-11-29
No worries. I will add it to the bug thread (great idea BTW).

I am currently trying to find out when it started to affect me. 

In 10.04 the synaptics driver for my mouse pad was not loaded; only evdev. Therefore syndaemon was never running on my system and i never had the issue with the touchpad.

Now synaptic driver is being loaded for my mousepad, and hence syndaemon, and that is why i am now seeing this error.

I am trying to track down when the change happened and which package update caused it. I never saw the mouse freeze under 11.10 but that may be because i upgraded very quickly and i was not part of the testing phase (too busy at the time to really be of any useful help).

When i have found out what is causing it, i will update the bug thread.

---

