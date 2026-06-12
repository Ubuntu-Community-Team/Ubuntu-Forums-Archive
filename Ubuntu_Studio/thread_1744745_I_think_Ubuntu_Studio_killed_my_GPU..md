---
title: "I think Ubuntu Studio killed my GPU."
date: 2011-04-30
forum: Ubuntu Studio
---

### Post by DanFerg on 2011-04-30
Hey all, I am a longtime windows user who, based on fantastic reviews, features, and a father-in-law who is a longtime linux user, I decided I wanted to replace my windows 7 laptop with an installation of Ubuntu Studio. I do a lot of audio recording so it seemed like a good fit.

The install went smooth as silk, nothing wrong at all. Booted up fine (10.10 64-bit), got to play with the interface for a while, the only thing wrong was that my wireless card would not work. I spent a lot of time researching why this might be, but finally decided to go to bed after shutting down the laptop.

I woke up today, turned on the laptop, and... The screen is blank. The laptop fans come on, disk drive whirrs for a second, keyboard lights come on, hard drive is even spinning, but the monitor gets absolutely NO signal. Not even a flicker. I tried turning it on several times to no avail, and even plugged my external monitor to the output on the laptop. Still nothing. So... Can anybody tell me what may have went wrong? Or if there is anything I can do to test if it really is broken?

---

### Post by rusty377 on 2011-04-30
Dan,

It sounds like my recent upgrade- it could be the video driver - I say that because that is when a new driver would start up -after a reboot- exactly as mine did. You might try using grub to pick either a recovery or older version and try an option that does not use the additional driver (you may or may not even have one though)- essentially using the default low-res driver to see if it is a driver issue. I am not a Linux expert- just mentioning because I had this only yesterday :0) Give it a try- it can't hurt.

---

### Post by trulan on 2011-04-30
The first time I installed Ubuntu Studio it killed my power supply...

Just kidding - but seriously, my power supply died the day after I installed US - no relation of course.

Try pressing 'shift' within the first few seconds of turning on your computer.  You should see the grub menu (provided it is a driver issue and not a fried GPU.)  Then, you can select 'recovery mode' and begin the process of getting the drivers set up properly.

---

### Post by DanFerg on 2011-04-30
I tried those things, but the problem is the screen itself does not come on at all. The display on the laptop simply stays off, as if unplugged. So I am really stuck, unless there is some way to access the computer from another computer perhaps via ethernet?

It seems like it could be a hardware malfunction, such as the sensor for the laptop lid being closed getting stuck, but is it possible that software could be responsible for not providing power to the display?

---

### Post by jejeman on 2011-04-30
Try live cd if you have any.

---

### Post by DanFerg on 2011-04-30
SOLVED!

Okay so it was not an ubuntu issue at all! Apparantly it was hardware. I found a post online that said this:

"I had the same problem with my HP DV6599. On power on the screen would stay black, no POST, nothing at all on the display. The HDD would spin up but the HDD indicator would not come on and would not boot. The DVD drive would spin up and attempt to read a disc if one was in the tray but still would not boot. I found an answer on another forum. Unplug the power, remove the battery and then hold the power button for 30 to 60 seconds. Then reattach the power and attempt a boot. It worked for me! Just shutdown, put the battery back in you're good to go. Worked for me so definitely worth a try."

link to original: [http://en.kioskea.net/forum/affich-24155-laptop-screen-blank-when-switched-on]("http://en.kioskea.net/forum/affich-24155-laptop-screen-blank-when-switched-on")

I tried it and it worked!

So if anyone has this problem with an HP, try this! Thanks guys for all the help. :)

---

### Post by trulan on 2011-04-30
Glad to hear you got it working!!

---

### Post by rusty377 on 2011-04-30
At least it wasn't a burnt GPU:P

---

