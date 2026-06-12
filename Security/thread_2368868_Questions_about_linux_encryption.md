---
title: "Questions about linux encryption"
date: 2017-08-16
forum: Security
---

### Post by breitenbergbren on 2017-08-16
Disclaimer: Non-native, I’ve tried my best.
   
  I’m just started looking into linux, mainly for security and privacy  reasons. I’ve used LUKS and linux before, but I want to fully understand  how it works. Being sure my data is safe is crucial to me.
   
  When I install linux (ubuntu) I get 2 options: Full Disk Encryption  (FDE) and encryption of home folder-encryption. I’ve ticked both.

  Correct me if I’m wrong, but as far as I’ve understood FDE prevents  anybody with psychical access to my computer, when powered off, from  booting another OS onto it. If they do so, they would only see encrypted  data. Good so far.
   
  But as many other, my computer is almost never powered off. Either  it’s standing at my desk turned on or it’s in sleep mode, when the lid  is closed (laptop). Therefore I’ve set the screen to lock within minutes  of inactivity and to request user password when it wakes from sleep.  It’s now I’m in doubt:  IF someone stole my laptop when powered on, is it safe to trust the  screen lock? 
  Is it possible in anyway to boot another OS and access my data without having to power it off and therefore activate the FDE? 
  And what about passwords? I’ve always learned to use long (50+)  passphrases for encryption, so thats what I do for FDE. But would that  be necessary for my user too? 
  What exactly is it that home folder-encryption does? Is it any advantage on a single-user computer?

---

### Post by TheFu on 2017-08-17
There are weaknesses in all encryption when it isn't completely powered off.  Sleep/hibernate leave that door open. If you care about security, power it off. Yes, it is inconvenient.

HOME directory encryption has a number of weaknesses. The file sizes leak information. The tool used for it is slow.  It breaks automatic backups too - more accurately, it broke my method of performing automatic backups. I don't use HOME encryption.

To deal with the inconvenience, my rule of thumb is to shutdown the computer when I leave the house - that applies if the computer comes with me or not.  To make returning to the desktop easier, I wrote a script that opens all connections to other systems and launches, then places each GUI program where I like them.  

At some point, I might make it automatic at login, but it has been many, many, years that I've done this and still haven't bothers to make it automatic at login.  Of course, I'd need to check if each program were already running first.  Plus, I tend to run certain programs on other systems and ship the display back to my laptop.  That wouldn't make sense if the laptop isn't on the same network.   My laptop isn't very powerful, so running multiple browsers plus email is too much for it, but displaying the programs is pretty light, relatively.

So FDE = good.
Home directory encryption = not-as-good, slow.

And don't forget that FDE is susceptible to the evil maid attack, so you might want to take precautions against that by always booting from an external device that you keep with you when in not-so-friendly locations (hotels, shared living spaces, work and public places).

---

