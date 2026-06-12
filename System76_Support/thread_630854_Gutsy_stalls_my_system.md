---
title: "Gutsy stalls my system"
date: 2007-12-03
forum: System76 Support
---

### Post by dgermann on 2007-12-03
Hi--

In several apps, since upgrading to Gutsy, the whole system will freeze or stall for no apparent reason.

The stall lasts for 15 seconds or so (I have not timed it, but it *seems* like hours!).

Then it will remember and execute whatever keystrokes or mouse movements I had made in the interim. Nice show to watch!

For instance, I might be in a word processing document (OOo), and when this happens I cannot move the mouse nor get any result from <esc>, nor scroll the page. Sometimes I cannot go ctrl-alt-arrow to switch to another desktop.

It has the same effect on Firefox and Evolution.

This is a production machine so I need to get it working all the time.

OK, it just did it while I was making this post. 27 seconds or so in the freeze state.

Oh, I see nothing particular going on in System Monitor while this is frozen, and I have stopped Trackerd and whatever the other disk search tool is that takes so much of the resources. The clock does run in the top panel.

Any ideas?

---

### Post by thomasaaron on 2007-12-04
What system do you have?

---

### Post by dgermann on 2007-12-04
Thomas--

Oops, sorry! Forgot to say that.

GAZV4.

---

### Post by thomasaaron on 2007-12-04
Thanks, Doug.

The problem is not Gutsy. It is a firmware problem with your cd drive.
Send me an email at support, and I'll send you directions to flash it.
Then all will be heavenly.

Best,
T

---

### Post by dgermann on 2007-12-04
Tom--

The fix looks like it may take me a couple days to get the stuff needed to implement it.

Is there a way to disable the cd/dvd in the meantime to stop this problem?

I found this but suspect it does not completely shut down the activity as I envision: [look at page 2 here]("http://ubuntuforums.org/showthread.php?t=623829&highlight=disable+dvd&page=2")

---

### Post by thomasaaron on 2007-12-05
The best way is to remove your battery and a/c adapter, use a paper clip to manually open the door of your drive (there's a little hole next to the button), remove the screw on the bottom that holds the drive in and just pull the drive out.

---

### Post by ajlewis2 on 2007-12-15
I am getting stalls/freezes since installing Gutsy and there is nothing in my cd/dvd drive.  I am getting this from the system log. I got the same thing 8 minutes before:

Dec 15 15:17:44 hopalong kernel: [ 4362.464000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 15 15:17:44 hopalong kernel: [ 4362.464000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 15 15:27:31 hopalong kernel: [ 4950.512000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Dec 15 15:27:31 hopalong kernel: [ 4950.512000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x25 data 8 in
Dec 15 15:27:31 hopalong kernel: [ 4950.512000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Dec 15 15:27:42 hopalong kernel: [ 4955.564000] ata1: port is slow to respond, please be patient (Status 0xd0)
Dec 15 15:27:42 hopalong kernel: [ 4960.560000] ata1: device not ready (errno=-16), forcing hardreset
Dec 15 15:27:42 hopalong kernel: [ 4960.560000] ata1: soft resetting port
Dec 15 15:27:42 hopalong kernel: [ 4960.920000] ata1.00: configured for UDMA/100
Dec 15 15:27:42 hopalong kernel: [ 4961.108000] ata1.01: configured for UDMA/25
Dec 15 15:27:42 hopalong kernel: [ 4961.108000] ata1: EH complete
Dec 15 15:27:42 hopalong kernel: [ 4961.124000] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
Dec 15 15:27:42 hopalong kernel: [ 4961.140000] sd 0:0:0:0: [sda] Write Protect is off
Dec 15 15:27:42 hopalong kernel: [ 4961.140000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 15 15:27:42 hopalong kernel: [ 4961.164000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 15 15:27:42 hopalong kernel: [ 4961.196000] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
Dec 15 15:27:42 hopalong kernel: [ 4961.212000] sd 0:0:0:0: [sda] Write Protect is off
Dec 15 15:27:42 hopalong kernel: [ 4961.212000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 15 15:27:42 hopalong kernel: [ 4961.244000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by ajlewis2 on 2007-12-15
I see a lot of this sort of problem in Ubuntu bugs.  For now I am running the old kernel and not having the problem. Whew.  Kind of bad when everything just stops working for 20-30 seconds every now and then--like 4 times per hour or more.

Does this connect with the fix for booting where I had to remove piix from blacklist-ata?  I did see some mention of ata_piix in some of the bug reports and comments.

Anita

---

### Post by thomasaaron on 2007-12-17
Hi, Anita.

Those errors are indicitave of a firmware problem in your cd drive.
Send me an email at support, and I'll send you directions for flashing your drive.
Then the freezes will cease.

Best,
Tom

---

### Post by ajlewis2 on 2007-12-17
Thanks, Tom.  I did see the post with the files for flashing using two jump drives.  

Can this be the problem when I have nothing in the drive?   I know that I had problems with Feisty when I had something in the drive from time to time, but this is happening when there is nothing in the drive.  Why is [sda] the device mentioned in the syslog?  That isn't the cdrom/dvd.

---

### Post by thomasaaron on 2007-12-17
Yes, Anita. It is the same problem.
I don't think the old work-around (disk in the drive) applies in Gutsy.

Best,
Tom

---

### Post by ajlewis2 on 2007-12-17
It looks like you are correct, Tom.  I did the fix about 45 minutes ago and I have not had the problem yet with the new kernel running.

Would you mind going to the bug report and telling them what the problem was for my system and why this fixed it?  I could try, but I really don't know what was going on.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/163675](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/163675)

Thanks again, Tom.

---

### Post by thomasaaron on 2007-12-18
Done.

---

### Post by vsanghvi on 2007-12-27
Hi, I'm not sure, but I think I'm having a similar problem. I did a clean install of ubuntu gutsy a week ago or so on an hp dv2000. Every ten minutes or so, usually when i'm doing something cpu heavy like video, my computer will stall, but the mouse will still move and audio will continue to play. It only lasts about 10 minutes, but is really frustrating, especially if you're trying to watch something or do work. I'm not really sure how this would relate to the CD Drive issue described in this thread, but its worth checking. It only seems to happen when compiz is enabled though, so that might be it. Anyways, any help is appreciated.

---

### Post by thomasaaron on 2007-12-27
Well, the CD drive firmware issue is unrelated to graphics. If you are sure your computer freezes (I'm reading "it gets really slow to the point of being vegetative only while doing heavy graphics-oriented stuff) then it might be a lack of RAM or just a slow processor. 

The firmware problem would make your system unresponsive regardless of what you are doing.

What kind of hardware configuration are you running?

---

### Post by vsanghvi on 2007-12-27
Actually, I think I said minutes instead of seconds. What happens is every ten minutes or so, my computer will stall for about 10 seconds, and then come back. During this time, the screen itself freezes, although I have control of the mouse and audio will play. I thought this generally happened during cpu intensive times, but it also happens just while surfing the web.

I have an amd turion x2 processor (1.8 ghz), 2 gb of ram, and nvidia graphics. I'm beginning to think that this isn't the issue because after disabling compiz, the problem always disappears, and like you said, the graphics shouldn't be connected to the cd rom drive.

---

### Post by thomasaaron on 2007-12-28
Well, with 2GB of RAM, compiz shouldn't be bogging down your system. (And that's a decent processor, so you've got enough power for compiz.)

So, let me just clarify one little thing:  Gutsy has a feature that causes open windows to go gray. It's Gutsy's way of saying, "Hold up, Slick, I'm busy here."
Is that what you are seeing? If so, it is normal.

If that's not the case, and disabling compiz fixes the problem, you might want to just run compiz on the "Normal" effects settings or mess around with it a bit and try to figure out if some particular feature is eating your lunch.

An interesting test would be to run...
top
...and see what is happening when you get the freezes. I'll bet compiz pops up.

Definitely not a firmware problem though.

---

### Post by vsanghvi on 2007-12-28
Nothing goes gray, the screen looks exactly the same (anything animated freezes) and stays that way for 10 secs. Any keystrokes or mouse clicks are still are processed once it comes back to life. I'll try playing around with the different settings a little more, but I think i enable less than 'Normal' and even reduced the frame rate, etc. Thanks for the ideas.

---

