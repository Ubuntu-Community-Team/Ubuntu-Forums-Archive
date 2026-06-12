---
title: "Ubuntu One has a mind of it's own"
date: 2010-05-11
forum: Ubuntu One (CLOSED)
---

### Post by x-shaney-x on 2010-05-11
I have noticed a few times my desktop suddenly becomes choppy.
When dragging a window it jumps across the screen instead of smoothly gliding.
When closing/minimizing windows etc, they just vanish instead of displaying a nice smooth animation.
When moving through menus there are big delays when opening sub menus.  That kind of thing.

Every time this has happened I have opened gnome-system-monitor and sat there at the very top of the processes is ubuntuone-syncdaemon.
I kill the daemon and instantly my desktop is responsive again.

Now obviously this is annoying in it's own right but what makes it worse is that I DO NOT have ubuntu one enabled at the moment.

I'm not using it, it is not set to run on startup, the sync options in the preferences are all unchecked and the "Ubuntu One" folder has no files in it so why on earth is this process deciding to run at all, let alone eat all my resources?

I would rather not have to remove ubuntu one completely because I want to keep checking progress of it and would use it once certain issues are ironed out.

---

### Post by UnRkiSt on 2010-05-12
Have a look at rcconf

---

### Post by x-shaney-x on 2010-05-12
Nothing related to couch or ubuntu one in rcconf.

Checked twice earlier and the daemon wasn't running at all but started a session a few minutes ago and it's there again.

---

### Post by UnRkiSt on 2010-05-12
I expect this kind of BS from M$ Windows, but not linux.  Ubuntu needs to take a hard look at the direction it is going.

---

### Post by joshuahoover on 2010-05-12
> **x-shaney-x said:**
> I have noticed a few times my desktop suddenly becomes choppy.
When dragging a window it jumps across the screen instead of smoothly gliding.
When closing/minimizing windows etc, they just vanish instead of displaying a nice smooth animation.
When moving through menus there are big delays when opening sub menus.  That kind of thing.

Every time this has happened I have opened gnome-system-monitor and sat there at the very top of the processes is ubuntuone-syncdaemon.
I kill the daemon and instantly my desktop is responsive again.

Now obviously this is annoying in it's own right but what makes it worse is that I DO NOT have ubuntu one enabled at the moment.

I'm not using it, it is not set to run on startup, the sync options in the preferences are all unchecked and the "Ubuntu One" folder has no files in it so why on earth is this process deciding to run at all, let alone eat all my resources?

I would rather not have to remove ubuntu one completely because I want to keep checking progress of it and would use it once certain issues are ironed out.

I'm sorry to hear Ubuntu One has been causing you problems. I've been trying to reproduce this problem and chatting with the devs about it. On an all up-to-date 10.04 LTS environment, I can't get this problem to occur as you described it. (I tested on 10.04 since I wasn't sure what version you were using.) If I do the following, the ubuntuone-syncdaemon process stops and will not show up again, even after restarts:

[LIST=1]
[*]Open System->Preferences->Ubuntu One
[*]Click on the "Services" tab
[*]Click off the "File Synchronization" checkbox
[/LIST]
I can see the ubuntuone-syncdaemon process disappear from System Monitor immediately after I check off that checkbox.

Can you report a bug so that we can get some debug logs that might help us determine what the cause of the problem might be? 

[LIST=1]
[*][https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)  - Be sure to include the steps you're taking and the results you're seeing
[*]At a terminal session (Applications->Accessories->Terminal) run the following command (replacing ###### with the bug number from step 1): apport-collect -p ubuntuone-client ######
[/LIST]
Thank you,

Joshua

---

### Post by x-shaney-x on 2010-05-12
Yep, anything I can do to help.
One thing though, since nothing is enabled either in the settings OR startup it shouldn't be running at all so I'm not sure how running it to de-bug anything will help.
My computer is actually disconnected in the services too.

One thing that does spring to mind, the missus' laptop still has everything enabled and I'm wondering if her computer on the same network could be causing the daemon to fire up on mine?

---

### Post by joshuahoover on 2010-05-13
> **x-shaney-x said:**
> Yep, anything I can do to help.
One thing though, since nothing is enabled either in the settings OR startup it shouldn't be running at all so I'm not sure how running it to de-bug anything will help.
My computer is actually disconnected in the services too.

Filing a bug and using the apport command will at least give us some logs and config files that will tell us a bit more info on how things are setup on your computer. It's tough to troubleshoot this without some of that info since I can't reproduce the problem myself.

> One thing that does spring to mind, the missus' laptop still has everything enabled and I'm wondering if her computer on the same network could be causing the daemon to fire up on mine?

Another computer running Ubuntu One won't affect another computer not running it. If it does, that's a HUGE problem. :)

Thanks,

Joshua

---

### Post by x-shaney-x on 2010-05-14
An update on this.  I've got to the bottom of the problem :)

It's all very embarrassing...

I went into ubuntuone prefs, intending to remove the other computer to be on the safe side.  It was then I noticed all the sync options were CHECKED, even though I know 100% for certain I had disabled them but I disabled them again anyway.
Next time I booted I checked the prefs again and sure enough they were all enabled.
After some checking I realised a lot of files in my home directory were owned by root, so although I was disabling the options they weren't actually being saved
Now, a few days ago I did copy over some files and settings from another partition as root.
Presumably I either chown'd wrong or forgot to chown at all.

I have sorted out the permissions and after half a dozen reboots the syncdaemon has NOT been running at all.

So panic over and it was all my own fault so apologies for that :oops:

But hey, one less headache for the devs :D

---

### Post by joshuahoover on 2010-05-14
> **x-shaney-x said:**
> An update on this.  I've got to the bottom of the problem :)

It's all very embarrassing...

I went into ubuntuone prefs, intending to remove the other computer to be on the safe side.  It was then I noticed all the sync options were CHECKED, even though I know 100% for certain I had disabled them but I disabled them again anyway.
Next time I booted I checked the prefs again and sure enough they were all enabled.
After some checking I realised a lot of files in my home directory were owned by root, so although I was disabling the options they weren't actually being saved
Now, a few days ago I did copy over some files and settings from another partition as root.
Presumably I either chown'd wrong or forgot to chown at all.

I have sorted out the permissions and after half a dozen reboots the syncdaemon has NOT been running at all.

So panic over and it was all my own fault so apologies for that :oops:

But hey, one less headache for the devs :D

I greatly appreciate you following up with what went wrong! It was baffling me and some of the devs on the team as we racked our brains on what might be causing this problem to happen. :)

Thank you,

Joshua

---

### Post by louis_mallow on 2010-07-06
> **joshuahoover said:**
> It was baffling me and some of the devs on the team as we racked our brains on what might be causing this problem to happen... Joshua

Not so fast! I have the OP's problem as first reported.   Slow environment and disc-grind on boot-up. System monitor shows ubuntuone-syncdeamon using loads of cpu% and v-memory with status 'uninteruptable'.   U1 Prefs shows my machine isn't linked under 'devices' and no boxes checked under 'services'. Under 'account' all fields are 'unknown'.  U! sync folder is empty except for another empty flder called 'shared with me'.   After a few minutes the syncdaemon goes to sleep and I het my processor back.  I stopped using U1 until the bandwidth limit works. This is annoying though.  [edit: I see U1 is in rcconf despite being off at the setup menu. Removed - will edit again when I see how that works out.] [edit: prob contnues. Will bug it.]

---

