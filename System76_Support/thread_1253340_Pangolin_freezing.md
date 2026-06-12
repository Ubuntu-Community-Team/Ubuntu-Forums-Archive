---
title: "Pangolin freezing"
date: 2009-08-30
forum: System76 Support
---

### Post by marshmallow1304 on 2009-08-30
Panp5, 64-bit Jaunty.

Two days ago, my Pangolin froze up three times, every time with the same symptoms.  Music stutters and the machine refuses any input from mouse or keyboard.  The only way to get it back is to do a hard reboot.

At first I thought it was Songbird, so I used Amarok.  Happened again.  Then I thought it might be Tracker, so I disabled indexing and purged tracker.  I thought this had solved it, as it didn't happen again.  Until today.

I saw that other people had similar freezes and solved them by installing linux-backports-[version], but backports is already installed.



On the plus side, it appears that UF has reimplemented marking threads as 'Solved'. :)

---

### Post by PGScooter on 2009-08-30
Hi marshmallow,

sounds like a frustrating problem. Thomas probably won't get to it until monday, so in the meantime...

to figure out which kind of freeze, does your caps like led light flicker during the freeze? If so, I think this indicates a kernel panick. Post the logs that your system76 software makes for you. I think you can do that by going to Administration> system76, but if that doesn't work look back in previous posts where Thomas explains the steps.

Make sure you backup your data just in case.

Best of luck!

---

### Post by marshmallow1304 on 2009-08-30
I'm not sure if the caps light flickered.  I'll check when/if it happens again.

I'm not sure it's worth posting the logs now, as the machine has been up for 2:45 without incident, but it can't hurt.

---

### Post by PGScooter on 2009-08-30
> **marshmallow1304 said:**
> I'm not sure if the caps light flickered.  I'll check when/if it happens again.

I'm not sure it's worth posting the logs now, as the machine has been up for 2:45 without incident, but it can't hurt.

I think you're right. Hopefully (I'll keep my fingers crossed for ya haha) you'll have a freeze today and that way you know what to look for and what to do immediately after.

---

### Post by thomasaaron on 2009-08-31
It's difficult to tell if those logs show the freeze (although there are some references to your wireless connection and one with your fingerprint reader).

Please re-create and post the logs immediately after rebooting after the next freeze.

And, PGScooter, thank you for jumping in there with good information. Much appreciated.

---

### Post by marshmallow1304 on 2009-09-03
Happened again, but a little differently this time.  The music didn't skip, though this may be because I was using Pandora instead of a local player.  The mouse didn't freeze up completely at first, but it did eventually.

None of the lights were flashing.  Logs are attached.

---

### Post by thomasaaron on 2009-09-04
What were you doing when it froze? Were you playing a game?

What nVidia driver do you have enabled? (System > Admin > Hardware Drivers)

---

### Post by marshmallow1304 on 2009-09-04
> **thomasaaron said:**
> What were you doing when it froze? Were you playing a game?

I had Pidgin, Skype, and Evolution in the tray.  Firefox with two tabs, one of which was Pandora.  Terminal with ssh on another workspace.  I was also using gedit and BlueJ.

It happened just as I clicked to switch workspaces.

> **thomasaaron said:**
> What nVidia driver do you have enabled? (System > Admin > Hardware Drivers)

180


Edit: It's actually never happened while playing a game.

---

### Post by marshmallow1304 on 2009-09-05
Happened again.  This time Pandora did stutter.  The caps light and the light to its right (I believe it's scroll lock) were flashing.  Logs are attached.


Other strange thing: I noticed that the indicator lights for caps lock and scroll lock don't work.  Caps lock works, but the light doesn't come on.  I've never actually used scroll lock, but its light doesn't work either.  Num lock's light works.

---

### Post by marshmallow1304 on 2009-09-06
Happened yet again.  I paused Pandora and locked the screen.  When I came back, the screensaver had frozen and the lights were flashing.  Logs are attached.

---

### Post by betrunkenaffe on 2009-09-06
This sounds like the problems I was having but I assumed it was Firefox. I downgraded to Intrepid and solved all issues.

Also, it seems an update causes the problem (for me) because on a fresh install, had no issues.

---

### Post by marshmallow1304 on 2009-09-10
I just had another bout of kernel panic.  Maybe I'll just put up with it for another couple months and do a clean install of Karmic, which I planned on doing anyway.  In the meantime, logs are yet again attached.

---

### Post by thomasaaron on 2009-09-11
There's a flurry of wireless networking activity occuring before the freeze.

Can you tell me more about your wireless set-up?
Does it ever freeze if you're connecting to a different router?
Do you have any large file downloads in progress when it freezes?
Do you have any other networking going on when it freezes (printer, etc...)?

---

### Post by marshmallow1304 on 2009-09-11
> **thomasaaron said:**
> Can you tell me more about your wireless set-up?

It's the wireless provided by my college.  All I know about it is that the router is in the basement (while I'm on the third floor) and the authentication is LEAP.

> **thomasaaron said:**
> Does it ever freeze if you're connecting to a different router?

Not that I know of, but I'm not often connected to other routers.  I know that it's never happened while on my home router, but I only use that once a week for a few hours.


> **thomasaaron said:**
> Do you have any large file downloads in progress when it freezes?

Sometimes, but usually not.  I'd say maybe during one or two of the freezes.

> **thomasaaron said:**
> Do you have any other networking going on when it freezes (printer, etc...)?

Just an SSH tunnel.

---

### Post by thomasaaron on 2009-09-11
I've seen several cases of freezing happening on college networks. Typically, it seems to happen when a DHCP lease is renewed while there is a download going on. SSH might play into it too.

It is probably a bug in Network Manager. Here is a post that describes what I've been seeing...

[http://ubuntuforums.org/showthread.php?t=551881](http://ubuntuforums.org/showthread.php?t=551881)

Try not keeping the ssh tunnel open unless you're actually using it.

---

### Post by marshmallow1304 on 2009-09-11
So would using
```
pci=noacpci
```
be prudent in this situation?


I use the SSH tunnel for all my browsing (I'm paranoid like that).

---

### Post by thomasaaron on 2009-09-14
You could try it, but I don't think it is related. However, you really should experiment without the ssh tunnel so that we can figure out if that's really causing the problem. Same with your observations on whether the freezes happen with downloads.

If we can reproduce the problem, we can report it as a bug to the upstream devs and get it fixed once and for all.

---

### Post by marshmallow1304 on 2009-09-14
> **thomasaaron said:**
> However, you really should experiment without the ssh tunnel so that we can figure out if that's really causing the problem. Same with your observations on whether the freezes happen with downloads.

Sounds good.  I just completed a fairly large download with no freezes, but I was on the wired network instead of wireless.  Maybe I'll experiment with downloading large files like the Ubuntu iso on both wired and wireless with and without SSH.

---

### Post by thomasaaron on 2009-09-15
That seems reasonable. One thing we need to look for in syslog is messages pertaining to DHCP lease renewal just before the freeze. That seems to be when it happens.

---

### Post by marshmallow1304 on 2009-09-15
Here's what I have so far:

Wired w/o SSH: 697.5 MB @ 250 - 350 KB/s - no problems
Wireless w/o SSH: 640.9 MB @ 8 - 12 KB/s - no problems (plugged into wired after 3 or 4 hours so the download wouldn't take all day)

---

