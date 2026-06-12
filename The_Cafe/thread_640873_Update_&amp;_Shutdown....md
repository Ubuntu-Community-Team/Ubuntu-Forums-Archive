---
title: "Update &amp; Shutdown..."
date: 2007-12-14
forum: The Cafe
---

### Post by Old Pink on 2007-12-14
[**HowTo: Update and Shutdown in Ubuntu | Topical Matt**](http://www.topicalmatt.com/14-12-2007/howto-update-and-shutdown-in-ubuntu)

Just finished that writeup on my blog, which results in a button launcher which will blank the screen, before checking for, downloading and installing updates, and finally turning off the computer.

Is there any better implementations of this? Or plans to? Like a button in update manager, or check box "Shutdown after completion" maybe? Or an option, like Windows, on the shutdown dialogue, to update and shutdown?

Also, what do you think of my writeup? I do appreciate comments. :)

---

### Post by SunnyRabbiera on 2007-12-14
I dont like this idea, windows is a pain in the butt when you have to shut down every time there is a small little update.
Only with kernel updates and such is where i see shutting down after update is valid.

---

### Post by MrFSL on 2007-12-14
> **SunnyRabbiera said:**
> I dont like this idea, windows is a pain in the butt when you have to shut down every time there is a small little update.
Only with kernel updates and such is where i see shutting down after update is valid.

Yes... but for the dialup users out there this could be very good. They could set there computer to get all updates and turn off the computer when they are done.

---

### Post by Tundro Walker on 2007-12-14
> **SunnyRabbiera said:**
> I dont like this idea, windows is a pain in the butt when you have to shut down every time there is a small little update.

I don't think that's what he's getting at, Sunny.  I think he's one of the folks that just habitually shuts down his computer when he's not using it.  So, instead of the Update Manager running when he's trying to use his comp, he'd like it to just silently check the repo's while he's on it, then, when he's done and shuts it down, he'd like it to go through the update process then.  Kind of like the AutoFSCK that Musther made.

Musther and I chatted about something like this a while back.  You can add a line to the shutdown script to have it check for and do updates there.  But, the ones I looked into (Synaptic, Update Manager, etc) all required user feedback (basically a dialogue box would pop up and sit there until you clicked "ok").  Wanted to steer clear of just CLI apt-get updating, because the GUI Update Manager tool takes other things into account.  Update Manager / Synaptic has the ability to run silently, checking repo's and automatically rolling in updates.  And, you can toggle it to just do Security updates (which are fairly safe) or all updates (which a few folks have had issues with after rolling in).  I just can't figure out how to utilize this "silent updater" through a script...I'm not sure what the CLI program is.

From hearing the OP talk, though, I think the idea of incorporating a "Update & Shutdown" button on the "Quit" pop-up is a pretty cool idea.  Reboot, Shutdown, or Update & Shutdown.  And, it would use whatever options you set in Synaptic / Update Manager.  (Meaning, if you just wanted Security updates, it would just do that.)  I like that idea, and I wish someone would explore this further.

---

### Post by Old Pink on 2007-12-15
> **Tundro Walker said:**
> From hearing the OP talk, though, I think the idea of incorporating a "Update & Shutdown" button on the "Quit" pop-up is a pretty cool idea.  Reboot, Shutdown, or Update & Shutdown.  And, it would use whatever options you set in Synaptic / Update Manager.  (Meaning, if you just wanted Security updates, it would just do that.)  I like that idea, and I wish someone would explore this further.That would be perfect, yes. That or a check box in update manager, something along the lines of "Shutdown after completion" 

This is on Digg, if anyone fancies getting this more into the public eye, could digg it up: [http://digg.com/linux_unix/HowTo_Update_and_Shutdown_option_in_Ubuntu](http://digg.com/linux_unix/HowTo_Update_and_Shutdown_option_in_Ubuntu)

---

### Post by Old Pink on 2007-12-17
Anyone else any ideas?

---

### Post by koenn on 2007-12-17
> **Tundro Walker said:**
> I don't think that's what he's getting at, Sunny.  I think he's one of the folks that just habitually shuts down his computer when he's not using it.  So, instead of the Update Manager running when he's trying to use his comp, he'd like it to just silently check the repo's while he's on it, then, when he's done and shuts it down, he'd like it to go through the update process then.  Kind of like the AutoFSCK that Musther made.

Musther and I chatted about something like this a while back.  You can add a line to the shutdown script to have it check for and do updates there.  But, the ones I looked into (Synaptic, Update Manager, etc) all required user feedback (basically a dialogue box would pop up and sit there until you clicked "ok").  Wanted to steer clear of just CLI apt-get updating, because the GUI Update Manager tool takes other things into account.  Update Manager / Synaptic has the ability to run silently, checking repo's and automatically rolling in updates.  And, you can toggle it to just do Security updates (which are fairly safe) or all updates (which a few folks have had issues with after rolling in).  I just can't figure out how to utilize this "silent updater" through a script...I'm not sure what the CLI program is.

From hearing the OP talk, though, I think the idea of incorporating a "Update & Shutdown" button on the "Quit" pop-up is a pretty cool idea.  Reboot, Shutdown, or Update & Shutdown.  And, it would use whatever options you set in Synaptic / Update Manager.  (Meaning, if you just wanted Security updates, it would just do that.)  I like that idea, and I wish someone would explore this further.

> **Old Pink said:**
> [**HowTo: Update and Shutdown in Ubuntu | Topical Matt**](http://www.topicalmatt.com/14-12-2007/howto-update-and-shutdown-in-ubuntu) ...which results in a button launcher which will blank the screen, before checking for, downloading and installing updates, and finally turning off the computer.


why not take this and turn it in to a blueprint / specification / feature request ? I think Launchpad is where you can do that. You already have specs and a few ideas on how to implement it  - "taking it further" can probably be done by ubuntu devs or so or whoever reads Launchpad.

---

### Post by 23meg on 2007-12-17
[QUOTE=koenn]"taking it further" can probably be done by ubuntu devs or so or whoever reads Launchpad.[/QUOTE]

While it *can* in theory, it's best to gather people around your specification actively yourself, and/or work on it yourself.

More on that [here]("https://wiki.ubuntu.com/FeatureSpecifications").

---

### Post by Old Pink on 2007-12-18
I won't create a launchpad feature request yet, as there isn't much interest around it, there's only been 7 (now 8) replies to this thread, and not all of them positive. 

But thanks, I am aware of launchpad. :)

---

### Post by blueturtl on 2007-12-18
Do go ahead with the feature request! Many times I leave updates till the evening when it's time to turn the computer off. Then I have to sit there and wait while the updates download and install before I can turn the computer off (and I am on a DSL line). This would be a very useful feature as I could just set the updates to install and go do evening chores without having to come back to see if the updates are done yet.

I'm in favour of the checkbox "shut down after updates" to Update Manager is what I'm saying.

---

### Post by K.Mandla on 2007-12-18
> **blueturtl said:**
> Do go ahead with the feature request!
+1. Don't stop working with an idea, or suggesting it, just because the initial response is less than enthusiastic. For every one person who disagrees with the idea, there are probably three or four more who agree, but don't say anything.

I thought it was pretty cool, anyway. ...

---

### Post by 23meg on 2007-12-18
Note that blueprints aren't for feature requests, in the sense that you're not requesting anyone to do something by just submitting a blueprint. They're for planning new features. Features such as this that affect the default Ubuntu installation directly need to be discussed extensively (on the development mailing lists) to get the blessing of the [Technical Board]("http://www.ubuntu.com/community/processes/techboard"), and the blueprint forms the basis of that discussion.

Also note that there's an approved blueprint on revamping the "Exit" dialogue for Hardy:

[https://blueprints.launchpad.net/ubuntu/+spec/exit-strategy](https://blueprints.launchpad.net/ubuntu/+spec/exit-strategy)

---

### Post by Old Pink on 2007-12-20
Thanks for all the feedback. :D 

I'll take a look into existing feature requests and whether or not creating another is reasonable tomorrow. :)

---

