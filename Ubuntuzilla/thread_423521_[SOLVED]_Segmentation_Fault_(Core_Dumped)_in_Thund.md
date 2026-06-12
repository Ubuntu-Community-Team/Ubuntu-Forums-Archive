---
title: "[SOLVED] Segmentation Fault (Core Dumped) in Thunderbird"
date: 2007-04-25
forum: Ubuntuzilla
---

### Post by expatCM on 2007-04-25
I cannot deny ... the script runs.  However....  I have a tiny problem ... and since I do not know enough about Ubuntu it is hard for me to know where to look to fix ....  This is a new install and Thunderbird has not yet been running on this machine.

After running the script Thunderbird appears installed but it does not run.  If I select Applications / Internet / Thunderbird then I see the tab with Starting Thunderbird but that disappears after a few seconds.

If I open a command prompt and enter the command thunderbird I get the message "Segmentation fault (core dumped)"

---

### Post by nanotube on 2007-04-25
> **expatCM said:**
> I cannot deny ... the script runs.  However....  I have a tiny problem ... and since I do not know enough about Ubuntu it is hard for me to know where to look to fix ....  This is a new install and Thunderbird has not yet been running on this machine.

After running the script Thunderbird appears installed but it does not run.  If I select Applications / Internet / Thunderbird then I see the tab with Starting Thunderbird but that disappears after a few seconds.

If I open a command prompt and enter the command thunderbird I get the message "Segmentation fault (core dumped)"

that is a hard one to track down... could be a bad download. did you get gpg to verify the integrity of the downloaded archive?

---

### Post by aysiu on 2007-04-25
> **expatCM said:**
> If I open a command prompt and enter the command thunderbird I get the message "Segmentation fault (core dumped)" I have no idea what's wrong.

I did a Google search and found out [you're not alone](http://forums.mozillazine.org/viewtopic.php?t=542409&sid=176a4f21e74b860e0cf84270dc9ef046), but, unfortunately, I don't see a solution.

Do you get the same thing with ```
mozilla-thunderbird
``` as you get with ```
thunderbird
```?

By the way, I've moved this to its own thread, since I'm pretty sure it's not directly related to the script having run successfully or not. Still, if we can troubleshoot this post-install problem... all the better.

---

### Post by expatCM on 2007-04-26
Yes I got the same thing with the command thunderbird and mozilla-thunderbird.

No I did not check the gpg ...  I was running the install script and just stood back.   I have another very similar machine which I have just finished loading Ubuntu.   I will run the script on that machine and see what happens just as soon as I have posted this message...

---

### Post by nanotube on 2007-04-26
> **expatCM said:**
> Yes I got the same thing with the command thunderbird and mozilla-thunderbird.

No I did not check the gpg ...  I was running the install script and just stood back.   I have another very similar machine which I have just finished loading Ubuntu.   I will run the script on that machine and see what happens just as soon as I have posted this message...

ehrm, the script has built in gpg key checking. it just asks you whether you want to do it or not. so the question is, did you say "y" or "n" in response. :) if you aren't sure, just run the script again, and this time tell it "y" when it asks for gpg key verification.

---

### Post by expatCM on 2007-04-26
I have run the script again.  I did check Y when prompted to check the signature.  The message at the end of the script says that Thunderbird has been successfuly installed.

I select on the menu entry, the program tab appears and then disappears ... the program does not open.


I have now run the script on a second machine and everything else follows though but in this case Thunderbird will open on the Import Settings screen ...


Now it is time to tread into the unknown .......    I have asked myself what is different between the two machines.  All I can think of is scim and this may be relevant since it will automatically load every time a program is launched which supports an IME.  The machine with the successful install did not have scim configured at the time of install.  On the machine with the problem, it is already working.  So I am wondering if scim is stopping Thunderbird from installing ....

Do you happen to have any idea how I can stop scim from loading for a session so that I can test and see if I can run the install script without it being present?

---

### Post by nanotube on 2007-04-26
well, i've never done anything with scim, but if it's like most other things, it will have a daemon running in the background, so you can just kill the scim process?

if not, then you'd probably get more specific help in the general help forums, since this is a rather low-traffic area.

---

### Post by expatCM on 2007-04-26
I tried to kill all instances of scim.  There are five processes and four are easy to kill.   The core is a zombie and I have no idea how to remove it.   

I think there is a very strong correlation between the problem with the Thunderbird  installation script and scim though since I just ran the script again having first killed the four scim processes.  The script ran but ...  Thunderbird would not load.  What was very interesting is that scim had appeared in the system tray so the zombie process must have somehow been activated .....

I will open a fresh thread to see if there are any suggestions of how to stop scim.  The official scim website is not close enough to the mark here ...

---

### Post by nanotube on 2007-04-26
hmm, ok, well, please post back here if you figure this out...

---

### Post by expatCM on 2007-04-27
Yes, worked it out.

I removed scim using synaptic.  Then ran the install script.  Zero problems.   I am now trying to work out how to put back scim the way it was ...  but that is another issue ....

So the conclusion is that if scim is installed then the Thunderbird install script does not work completely.

---

### Post by nanotube on 2007-04-27
> **expatCM said:**
> Yes, worked it out.

I removed scim using synaptic.  Then ran the install script.  Zero problems.   I am now trying to work out how to put back scim the way it was ...  but that is another issue ....

So the conclusion is that if scim is installed then the Thunderbird install script does not work completely.

ok, thanks for playing around with this, and reporting your results. i will post this scim problem into our help section for others' reference.

---

### Post by seetho on 2007-04-28
I installed tb2 on a fresh dapper system manually.  It was worked fine initially.  It is beautiful!

Unfortunately it broke (segmentation fault) after I activated SCIM which I need for typing some Japanese.  Initially it did not occur to me that SCIM was the one that broke tb2, but after reading the posts here, it is the most likely suspect.

---

### Post by nanotube on 2007-04-28
hi
here is a possible fix (found at [http://alvonsius.wordpress.com/2007/01/23/scim-and-sunbird/](http://alvonsius.wordpress.com/2007/01/23/scim-and-sunbird/))

in a terminal, to start thunderbird, try using this command line:
```
export GTK_IM_MODULE=scim-bridge; thunderbird
```

see if that works out for you, and please post back here with results.

---

### Post by drdreus on 2007-04-28
I had the same problem with Mozilla Sunbird.  It wasn't until someone here mentioned SCIM that I realised that had changed on mine too.

I've had problems with SCIM and programs before... apparently they don't play nice together.

Anyway, I found this mentioned in [http://www.ubuntuguide.org]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_PDF_Reader_.28Adobe_Reader.29_with_Plug-in_for_Mozilla_Firefox") regarding Adobe.  They suggested

```
gksudo gedit /usr/bin/acroread
```
And changing:

```
#!/bin/sh
#
```
to:

```
#!/bin/sh
#
GTK_IM_MODULE=xim
```
I'm not entirely sure what it's doing other than circumventing SCIM.  But after doing that I was able to start Sunbird.

If SCIM causes problems Adobe, Thunderbird and Sunbird (and who knows what else) this should probably be fixed in the future.

---

### Post by nanotube on 2007-04-28
> **drdreus said:**
> I had the same problem with Mozilla Sunbird.  It wasn't until someone here mentioned SCIM that I realised that had changed on mine too.

I've had problems with SCIM and programs before... apparently they don't play nice together.

Anyway, I found this mentioned in [http://www.ubuntuguide.org]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_PDF_Reader_.28Adobe_Reader.29_with_Plug-in_for_Mozilla_Firefox") regarding Adobe.  They suggested

```
gksudo gedit /usr/bin/acroread
```
And changing:

```
#!/bin/sh
#
```
to:

```
#!/bin/sh
#
GTK_IM_MODULE=xim
```
I'm not entirely sure what it's doing other than circumventing SCIM.  But after doing that I was able to start Sunbird.

If SCIM causes problems Adobe, Thunderbird and Sunbird (and who knows what else) this should probably be fixed in the future.

thanks for the info. :)

first question: so did you try doing this for thunderbird, and did it work?
second question: instead of editing the script, does using either of the following two commands to start thunderbird work:
```
export GTK_IM_MODULE=scim-bridge; thunderbird
export GTK_IM_MODULE=xim; thunderbird
```

---

### Post by drdreus on 2007-04-29
Oddly enough, my Thunderbird worked fine without any tinkering.  I installed it using Automatix2, so I don't know if that has anything to do with it.

However, typing ```
export GTK_IM_MODULE=scim-bridge; sunbird
export GTK_IM_MODULE=xim; sunbird
``` both allowed me to open the unaltered sunbird.

Is there a benefit to exporting settings vs manually editing files?

---

### Post by nanotube on 2007-04-29
> **drdreus said:**
> Oddly enough, my Thunderbird worked fine without any tinkering.  I installed it using Automatix2, so I don't know if that has anything to do with it.

However, typing ```
export GTK_IM_MODULE=scim-bridge; sunbird
export GTK_IM_MODULE=xim; sunbird
``` both allowed me to open the unaltered sunbird.

cool.

> Is there a benefit to exporting settings vs manually editing files?

well, not really. both do exactly the same job. if you are comfortable editing scripts, then you might as well edit. manual export makes for easier testing, and easier to tell users what to try. :)

---

### Post by expatCM on 2007-05-11
Well this is very interesting but I do not know what to do with the export commands for practical use ....

I entered 

export GTK_IM_MODULE=scim-bridge; thunderbird
and
export GTK_IM_MODULE=xim; thunderbird

individually at the command prompt and on both occasions Thunderbird launched as soon as I pressed enter.  Without use of the export command Thunderbird cannot be used.

So how do I incorporate this to open Thunderbird from an icon ......

---

### Post by drdreus on 2007-05-11
> **expatCM said:**
> Well this is very interesting but I do not know what to do with the export commands for practical use ....

I entered 

export GTK_IM_MODULE=scim-bridge; thunderbird
and
export GTK_IM_MODULE=xim; thunderbird

individually at the command prompt and on both occasions Thunderbird launched as soon as I pressed enter.  Without use of the export command Thunderbird cannot be used.

So how do I incorporate this to open Thunderbird from an icon ......

You may have to edit the command that runs the program.  To wit: ```
sudo gedit /usr/bin/thunderbird
``` and change: ```
#!/bin/sh
#
``` to: ```
#!/bin/sh
#
GTK_IM_MODULE=scim-bridge
``` and then try launching it.  See if that helps.

---

### Post by nanotube on 2007-05-11
drdreus gives a good suggestion
but it may get overwritten in the next thunderbird upgrade, so you'd have to edit it again.
i'd suggest writing a small text shellscript with the following content:
```
!#/bin/bash
export GTK_IM_MODULE=scim-bridge; thunderbird
```
save it as "thunderbirdstarter.sh" in your home dir,
change permissions to executable with
```
chmod u+x /home/yourusername/thunderbirdstarter.sh
```
and then point your menu item to /home/yourusername/thunderbirdstarter.sh, instead of "thunderbird". that should let you start thunderbird, and won't need any editing when they release a new version and you upgrade.

but... you could use drdreus suggestion just as well, if you prefer. they both do the same thing, basically. :)

---

### Post by drdreus on 2007-05-11
> **nanotube said:**
> drdreus gives a good suggestion
but it may get overwritten in the next thunderbird upgrade, so you'd have to edit it again.

Oh yeah, good point. I didn't think about future updates.

That being said, it would be nice of Ubuntu could play nicely with SCIM.  It appears to be all or nothing with it, i.e., as soon as you enable certain languages requiring complex entry, SCIM is always running.  That's not a problem if you use said language all the time.  But if you use it infrequently, it's a nuisance.  Especially because it conflicts with common aps.  But that's for a different thread I suppose.

---

### Post by expatCM on 2007-05-11
Two solutions .... I am so lucky :)

I have just implemented the solution from drdreus on one machine and it is fine.   In the morning I will put the other solution from nanotube on the other machine.

It really would be nice to see Ubuntu integrate Scim properly into the system .... I cannot imagine that my headache was not experienced by others.  So many users do not use English as a primary language,  our use is for simplified and traditional Chinese and Thai in the same system as well as English.   It is just fantastic IME.

---

### Post by nanotube on 2007-05-11
just to be clear, though, it is not a problem with ubuntu per se, but with the thunderbird official build - their default build for some reason doesn't play well with scim. i've heard that if you compile from source yourself, it is reputed to work...

---

### Post by Shoubidouw@@@ on 2007-06-04
GREATJOB GUYS !!!

I met that problem last nite after I installed SCIM on my laptop!! Couldn't run TB2 anymore!

No more prob!!

Thanks again!

---

### Post by AncientPC on 2007-06-04
Well they've narrowed down the problem but haven't really solved.

I can't get my fiancee to switch to Ubuntu completely because she needs to type in e-mails in Japanese.  Then again I could just set up Evolution, but ideally I would prefer Thunderbird because I can synch her local profiles cross-platform between Ubuntu and Windows.

---

### Post by nanotube on 2007-06-04
> **AncientPC said:**
> Well they've narrowed down the problem but haven't really solved.

I can't get my fiancee to switch to Ubuntu completely because she needs to type in e-mails in Japanese.  Then again I could just set up Evolution, but ideally I would prefer Thunderbird because I can synch her local profiles cross-platform between Ubuntu and Windows.

does [this approach]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#.5BThunderbird.2C_Firefox.5D_Thunderbird_doesn.27t_start_at_all._Segmentation_Fault_.28Core_Dumped.29_when_running_from_terminal") not work for you? what about the one posted by drdreus?

---

### Post by slon on 2007-08-02
I have the same problem "Segmentation fault (core dumped)" after setup System -> Administration -> Language support -> check some language.

When I uncheck checked languages back and restarted, Thunderbird start without problems!

Ubuntu 7.04, Thunderbird 2.0

---

### Post by wall0159 on 2009-05-07
> **nanotube said:**
> hi
in a terminal, to start thunderbird, try using this command line:
```
export GTK_IM_MODULE=scim-bridge; thunderbird
```


Thank you, nanotube, for this advice. I had been looking for a solution to this. Thunderbird would repeatedly seg fault, only to start up, then seg fault again shortly later. Purging config files, reinstalling and reconfiguring did not appear to help, but it looks like my problems are due to scim also, since it appears to be working when called in this way.

Cheers!

[EDIT]: oops - looks like I spoke too soon. seg faulting again.. I've also tried going into the language manager, as another poster suggested, but to no avail....

---

### Post by opto09 on 2009-07-01
> [EDIT]: oops - looks like I spoke too soon. seg faulting again.. I've also tried going into the language manager, as another poster suggested, but to no avail....

I have the same bug but found this in the ubuntu bugs site: [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/370008](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/370008)

It may be the lightning add-on that's causing it to crash. You can try this out by going into safe mode:

```
thunderbird -safe-mode
```

Disable Lightning, then restart thunderbird normally. I just tried it and it works for me.:p

Here's hoping someone will release a fix soon.

---

### Post by wall0159 on 2009-07-16
Yeah - thanks for that.

I have been using thunderbird without lightning and google-provider at the times when it is crashing. Rather inconvenient though, as I actually use the calendaring features..

I've been looking for alternatives, but I don't like Evolution (too buggy - seems to randomly drop emails, calendar appts, etc..), and there aren't too many other options..

I hope it's repaired soon too! I've even tried purging my thunderbird installation and deleting every thunderbird config file I could find, and then reinstall - to no avail...

---

### Post by cbender on 2009-11-17
I had the same Problem, I set the Spell-Checking from english to german and Thunderbird didn't start. 

with```
export GTK_IM_MODULE=scim-bridge; thunderbird
``` I could start Thunderbird and set the Spell-Checking back to english. Now it starts without any Problems.

---

