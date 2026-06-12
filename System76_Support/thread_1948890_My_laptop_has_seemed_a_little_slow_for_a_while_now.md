---
title: "My laptop has seemed a little slow for a while now."
date: 2012-03-29
forum: System76 Support
---

### Post by NerdcoreSteve on 2012-03-29
For a while I'd been soured on this pangolin of mine. I guess I had underestimated just how much tweaking a linux machine required. For the longest time this thing was collecting dust while I used a mac mini.

But I've been going to school full-time for a few semester (CS degree) and with my newly acquired skills I am feeling up to the challenge of getting this rig running smoothly. If I can get this machine working to my satisfaction I'd much rather be using open source software than not.

Part of the "to my satisfaction" includes the fact that this machine seems just a little slower than it ought to be. Two examples that come to mind are that the cursor in Gimp drags visibly when I draw and flash games like [Dino run]("http://www.pixeljam.com/dinorun/") seem sluggish.

I suppose I could come up with other examples but perhaps just working on one of these problems specifically might lead to a more general solution.

Any ideas on how to start?

---

### Post by isantop on 2012-03-29
What type of Pangolin do you have?

The Gimp issue actually sounds like what happens when Gimp doesn't have enough RAM. How much RAM do you have, and what sort of image does it happen in?

---

### Post by NerdcoreSteve on 2012-03-30
How do I check what type of pangolin I have? After some googling I find that there is a model.py somewhere from System76 but I have yet to find it.


I have 4 gigs of RAM and the image in question was GIMP's native format, 640 x 480, with about 4 layers. I can edit much larger images in photoshop elements on my mac mini without any trouble.

I should note that since my reinstall I have yet to install the system76 driver and I'm not quite sure where to get that either. If memory serves, installing the driver didn't solve this issue but I am willing to try it.

---

### Post by smarmytime on 2012-03-30
> **NerdcoreSteve said:**
> How do I check what type of pangolin I have? 

I have a Pangolin Performance 7 (PanP7), and on the bottom of mine, there is a label that says the model and the number, so it may be as simple as just looking at the bottom.

FWIW, I have an i5 CPU with 4 GB RAM, and I had no lag issues with GIMP whatsoever.

---

### Post by marinara on 2012-03-31
just benchmark the pc with the phoronix suite until you figure out what subsystem (disk, video, cpu) is lagging
good luck

---

### Post by NerdcoreSteve on 2012-04-01
I have a panp4n.

I'm downloading phoronix as I write this but testing will have to wait until I'm done with my homework. :)

I should also probably note that I'm having refresh issues with my terminal [again]("http://ubuntuforums.org/showthread.php?t=1944893"). I suspect that it's all part of the same issue.

---

### Post by NerdcoreSteve on 2012-04-01
Well I ran the test but I don't know how to interpret it.
[URL="http://openbenchmarking.org/result/1204018-GR-STEVE787462"]
http://openbenchmarking.org/result/1204018-GR-STEVE787462[/URL]

---

### Post by marinara on 2012-04-01
something weird is happening.  I hate to make you look in your bios, to see if your ram is underclocked.  That would be very technical.
I guess you don't need to check your cpu clock, phoronix reported that also. (just thinking out loud)

Also can you open task manager and check to see if your CPU is at 100%.

are you running lubuntu? what version?

---

### Post by isantop on 2012-04-02
Did you install the proprietary drivers? Ubuntu (particularly the graphical aspects) will be very slow by default due to the Nvidia graphics. The proprietary drivers will fix that.

---

### Post by NerdcoreSteve on 2012-04-05
I'm running Ubuntu 11.10

System monitor says my cpu % is 96 for system monitor (it dropped to 32 but all I had to do was wiggle the mouse and it went up again) and, um, 26 for firefox? That doesn't add to 100. Hrm...

According to System Settings I have the most current Nvida driver.

Checking the bios seems like it might take a bit of time for me to figure out how to do. I think I'll wait for the weekend. Homework needs to get done. :)

---

### Post by NerdcoreSteve on 2012-04-11
Ok, now that I've actually looked at the bios, and assuming I've not missed something, it's less "time for me to figure out how to do" and more "time for me to be bothered to look at the bios". It's set to 4 gigs as far as I can see.

Now that I've been paying more attention to things, my netbook, with two gigs of ram, is a faster machine.

---

### Post by NerdcoreSteve on 2012-04-19
Got nothin' huh? That's cool mans.:guitar:

Any suggestions for where I can start figuring this out on my own? How, for example, would I learn to interpret my openbenchmark.org result?

Any other promising lines of inquiry I might pursue?

I'm willing to do some work but any tips or hints would not go unappreciated. :smile:

---

### Post by layolayo on 2012-04-19
Hi,

I've got a Lemur Ultra 3. No problems with it - but reading your posts thought I would take a look at Phoronix and OpenBenchMarking.

I ran option 3 (a complex system test) which ran 5 tests and installed Apache for me? I must also admit the results do not make much sense, but after clicking around on the OpenBenchMarking site, I was able to compare my results against others to see if my results were in the same ballpark as others with similar hardware.

I could only find one other person with System76 Lemur Ultra - and they had only run the Apache test.

Also, if you check the Performance Classification link when viewing your test results, that may give you some indication of performance across the board.

Hope this helps a little - even if it's just knowing someone else is finding the same sort of problems!!! :P

Layolayo

---

