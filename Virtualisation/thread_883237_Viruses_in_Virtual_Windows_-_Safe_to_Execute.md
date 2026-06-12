---
title: "Viruses in Virtual Windows - Safe to Execute?"
date: 2008-08-07
forum: Virtualisation
---

### Post by OzzyFrank on 2008-08-07
Hi. Just wondering if it is safe to execute an infected exe in a virtual Windows (in VMware, though it shouldn't matter if it is that or Virtulbox or whatever)? I imagine it is fine, especially if the host is a Linux distro like Ubuntu, but would like the input of those more familiar with this type of thing. Also, is there a difference if the host is also Windows? I am thinking that if even if both host and guest are Windows, the host would be protected from anything malicious in the guest, but I wouldn't be surprised if I am wrong. Would like the input of the wise in these matters. Cheers.

---

### Post by HermanAB on 2008-08-08
It depends on what the virus does of course.  I would suggest pulling the network cable before you run it though.

---

### Post by tamoneya on 2008-08-08
You should be fine as long as you arent sharing any files between the guest and host OSes.  If you are the virus wont be able to do anything really malicious to the host OS itself but it could delete or steal the files that you have being shared.  As for running with windows host it shouldnt be able to get out of the virtual environment but I wouldnt bet on it.

---

### Post by OzzyFrank on 2008-08-08
They're basically common worms the ones I'm thinking of looking at. Actually, what I mean is that I want to look at these .exe files without worrying about worms, which is why I asked this. I can get specifics of what worms if it makes a difference. Cheers

---

### Post by tamoneya on 2008-08-08
> **OzzyFrank said:**
> They're basically common worms the ones I'm thinking of looking at. Actually, what I mean is that I want to look at these .exe files without worrying about worms, which is why I asked this. I can get specifics of what worms if it makes a difference. Cheers

As long as you arent sharing any files between host and guest you are all set.

---

### Post by OzzyFrank on 2008-08-11
Hmm... sharing files between host and guest... I guess if I have virtual Windows mapping the drive of my proper XP install, and that of Ubuntu, that counts as sharing? So I guess that means I should make another VM for a Windows that I can check these .exes in. For the record, the reason I would go to this hassle is coz of some keygen.exe files (yes, yes, naughty naughty, but hey, I've paid enough for my Windows software!). I've seen many come up as false positives in some AV apps, and even those that are infected with some minor worm usually still work and will generate a serial... which is why I'd like to run these in a safe environment.

Also, while we're on the subject, are you guys saying that if I was sharing with only the Ubuntu partition, that it would be subject to infection by a Windows virus? Let's forget about ones that, for example, wipe your MBR or mess with CMOS settings... just ones that mess up Windows and therefore should not be able (in my opinion) to do anything malicious to a completely different operating system and filesystem. Your thoughts?

On a side note, in one of these "Linux Desktop Readiness" threads someone brought up the thing of Linux being virus free, and one person who is admittedly a Linux user said that was rubbish, that there are Linux viruses, so no one is immune. Anyone want to share their thoughts on that one?

---

