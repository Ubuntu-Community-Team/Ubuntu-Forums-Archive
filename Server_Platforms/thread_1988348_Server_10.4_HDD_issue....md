---
title: "Server 10.4 HDD issue..."
date: 2012-05-27
forum: Server Platforms
---

### Post by willystylee on 2012-05-27
So I've run a Minecraft server on a second machine in my room for over a year now, and this morning I wake up, see that the keyboard i use for the ubuntu server machine is flashing both the NUMLOCK and CAPSLOCK keys at the same time. I see this as an "uh oh", turn on my second display (actually my plasma tv) and switch the input to see whats up. I see the last line at the bottom of the screen says something like:

"xxxxxxxxxxxxxx  has failed! Attempting to kill init!"

That xxxxxxxxxxxxx being a series of numbers I can only guess might be a registry location? I don't know. I'm savvy but not in-depth savvy, I had an online friend actually set up my Minecraft server via TeamViewer, so my linux skill really doesn't go past installing the OS and making simple commands, cd, starting the server, i can do apt-gets, etc.

So to continue on with my experience this morning, when i saw that "Attempting to kill init!" line, i tried to see if the keyboard/typing responded, and it wasn't. So my only choice was to shut it off with the button, which is always painful. I turned it back on a few seconds later and immediately I could hear what sounded like the HDD looping. It just keeps making this sound every 4 or 5 seconds that loops continuously. Meanwhile, it's stuck on the blue HP post screen and after trying F9 and F12 or whatever key takes you to System Recovery or Diagnosis, i tried both. After hitting those keys, 10 seconds passes then finally I just see something like 

"Reboot and select proper boot device or insert boot media in selected boot device and press a key"
 
Then i try again for a 3rd or 4th time and this time i don't hear the HDD loop sound i did before, and it actually posts the ubuntu OS loading screen, then asks me if i want to fix errors. I hit F for yes, and it says /tmp isn't ready or something. It then just says 

"[        1.337125] Kernal Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"

Turned off then on again, am now hearing the looping sound again, got same message about boot device/media.


Obviously my HDD has failed (my best guess). My question though, is there any way to recover what's on the disk? Could i plug the HDD into my main machine and just locate the stuff on the disk like i could with a failed windows HDD?

---

### Post by willystylee on 2012-05-31
bump

---

### Post by rubylaser on 2012-05-31
I'd burn a liveCD and run from that in your other machine (just use the try ubuntu option and it won't hurt your Windows install).  Attach your failed hard drive, and hopefully you can recover the data from it.

---

