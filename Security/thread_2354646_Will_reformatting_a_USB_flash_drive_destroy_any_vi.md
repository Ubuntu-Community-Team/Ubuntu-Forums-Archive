---
title: "Will reformatting a USB flash drive destroy any viruses on it?"
date: 2017-03-04
forum: Security
---

### Post by John_Patrick_Mason on 2017-03-04
Will reformating a USB flash drive destroy any viruses on it? And if so, which format should I use so that I can still use the USB stick on Ubuntu *and* Windows? What application in Ubuntu can I use to do the job?

---

### Post by T.J. on 2017-03-04
Yes, and no.  

If a USB device has had its firmware tampered with, reformatting the data area may have no direct effect.  The odds of that kind of tampering are not impossible, although I would personally rate it as unlikely on a day-to-day basis.  If a drive has just a garden variety virus, a FULL reformat - not a quick - will clear it.

A general rule of thumb is do not use USB drive to transfer data from computer to computer at all.  Many places simply do not permit you to bring in USB drives.  They are a security risk.

Linux understands many formats, but Windows only understands NTFS and VFAT/FAT32.  You will have to use the latter on your average thumb drive.  What application you use depends on your level of expertise.  If you are a newbie, I would use the Disks application.

---

### Post by John_Patrick_Mason on 2017-03-04
> **T.J. said:**
> Yes, and no.  

If a USB device has had its firmware tampered with, reformatting the data area may have no direct effect.  The odds of that kind of tampering are not impossible, although I would personally rate it as unlikely on a day-to-day basis.  If a drive has just a garden variety virus, a FULL reformat - not a quick - will clear it.

Does that also hold true when plugging in a USB stick that enables an infected computer like a desktop to connect to a wireless network?

> **T.J. said:**
> What application you use depends on your level of expertise.  If you are a newbie, I would use the Disks application.

You mean the one that already comes pre-installed in Ubuntu?

---

### Post by kurt18947 on 2017-03-05
How about running DBAN or similar on it? What are the risks if an infection did survive repeated overwrite? If the USB drive were being used around critical systems, the cost of a new USB drive may be trivial compared to the problems an infection could cause.  I'm quite certain that no malware, no matter how clever will survive its flash drive host being placed on an anvil and being struck repeatedly with a large hammer. If the drive in question is being used in  low risk/low value environment less extreme measures might be perfectly adequate.

---

### Post by John_Patrick_Mason on 2017-03-05
[QUOTE=kurt18947]I'm quite certain that no malware, no matter how clever will survive its  flash drive host being placed on an anvil and being struck repeatedly  with a large hammer.[/QUOTE]

I think you hit the nail on the head. Let's suppose a cracker somehow was able to design a cryptovirus, not the kind that encrypts your hard drive and asks for a ransom, I'm talking about the kind that *uses* encryption to prevent it from being *detected* by antiviruses. Even if a cracker were able to design such a virus, I doubt it would be able to survive repeated reformatting. It could avoid detection, but it could not survive being overwritten by random data. Please feel free to correct me if I'm wrong. Also, I still would like an answer to my above question.

---

### Post by sudodus on 2017-03-05
There is an internal microprocessor in a USB flash drive. It is possible (with special software) to modify the programming of that microprocessor, and the tools, that are available to regular users (like you and me) do not reach that part of the USB flash drive.

DBAN or other tools that overwrite the ordinary memory cells can do their job correctly and wipe what is there, but if the internal microprocessor is infected by malware, it will not help. So if you suspect that a USB flash drive is infected, destroy it.

---

### Post by John_Patrick_Mason on 2017-03-05
What if I put files on a DVD -- I'm not talking about creating a bootable DVD, I'm talking about just transferring files onto a DVD using an Ubuntu machine -- and then pop in the DVD into an infected Windows machine, install the files that are on the DVD on the Windows machine, and then remove the DVD from the tray and pop it back in my Ubuntu machine? Since DVDs have no firmware to speak of, I should be safe, right?

---

### Post by cariboo on 2017-03-05
Just because windows malware does not have any affect in Ubuntu, doesn't mean it won't transfer it to other mediums.

---

### Post by John_Patrick_Mason on 2017-03-05
[QUOTE=cariboo]Just because windows malware does not have any affect in Ubuntu, doesn't mean it won't transfer it to other mediums.[/QUOTE]

Yes, but I mean if we're dealing with a Windows virus exclusively -- and most viruses are -- using a DVD instead of a USB flash drive should allow the safe transfer of files between a Windows machine and an Ubuntu machine.

---

### Post by kurt18947 on 2017-03-05
> **John_Patrick_Mason said:**
> Yes, but I mean if we're dealing with a Windows virus exclusively -- and most viruses are -- using a DVD instead of a USB flash drive should allow the safe transfer of files between a Windows machine and an Ubuntu machine.

I'm no expert in this stuff but let's say there were an infectious MS Word macro as part of a .docx file. Why wouldn't that infected .docx file be written to the DVD along with other files? It wouldn't do anything to the Ubuntu machine - Ubuntu machines don't recognize Word macros - but if the DVD with the infected .docx file found its way to a Windows machine with MS Office installed, wouldn't the malicious macro try to run? I don't know, I'm trying to understand this stuff too.

---

### Post by John_Patrick_Mason on 2017-03-05
[QUOTE=kurt18947]I'm no expert in this stuff but let's say there were an infectious MS  Word macro as part of a .docx file. Why wouldn't that infected .docx  file be written to the DVD along with other files? It wouldn't do  anything to the Ubuntu machine - Ubuntu machines don't recognize Word  macros - but if the DVD with the infected .docx file found its way to a  Windows machine with MS Office installed, wouldn't the malicious macro  try to run? I don't know, I'm trying to understand this stuff too.[/QUOTE]

These are good points, I would wait until somebody like T.J., Sudodus, cariboo, or somebody else chips in who is more experienced than both of us. I'm also wondering whether an infected file on a Windows machine like a .docx file or a .jpeg file can automatically copy itself to a blank dvd without physically copying the file yourself, just automatically. Does somebody know? Also, I would like to know if somebody could tell me whether my last comment was correct about using DVDs to copy files from an infected Windows machine instead of USB thumb drives was correct.

---

### Post by sudodus on 2017-03-06
> **John_Patrick_Mason said:**
> What if I put files on a DVD -- I'm not talking about creating a bootable DVD, I'm talking about just transferring files onto a DVD using an Ubuntu machine -- and then pop in the DVD into an infected Windows machine, install the files that are on the DVD on the Windows machine, and then remove the DVD from the tray and pop it back in my Ubuntu machine? Since DVDs have no firmware to speak of, I should be safe, right?

If you make a data DVD disk with 'clean' files in Ubuntu, it will be clean. If you close it for writing, it will be read-only. So if you move that DVD disk into a Windows machine, that is infected, I don't *think* it (the data DVD disk) will be infected. But I am *not sure*. There might malware that can overwrite the read-only status of the DVD disk and write something to it.

---

### Post by John_Patrick_Mason on 2017-03-06
I knew it, I knew it, I knew it. Isn't that why Windows 7 OEM install disks are R+/- only? My comment, though, had more to do about doing the reverse, transferring possibly infected files onto a DVD that are on a Windows machine, like music files and pictures, and then popping in the DVD into my Ubuntu machine, while running a Windows 7 virtual machine with a good antivirus program installed, such as Avira or Avast to scan the contents of the DVD in order to determine if any kind of malware has attached itself to any of those files, in order to determine what to keep and what not to keep. No firmware, no problem.

---

### Post by sudodus on 2017-03-06
I think that method should be good enough to use in your own computer.

---

### Post by bashiergui on 2017-03-09
> **T.J. said:**
> Yes, and no.  

A general rule of thumb is do not use USB drive to transfer data from computer to computer at all. Many places simply do not permit you to bring in USB drives. They are a security risk.Or perhaps it's more practical to buy sealed USB drives and avoid borrowed or found ones.

> **John_Patrick_Mason said:**
> Does that also hold true when plugging in a USB stick that enables an infected computer like a desktop to connect to a wireless network? You're referring to a dongle? This applies to any removable media that can be written to: USB drives, dvds, external drives. 
> **John_Patrick_Mason said:**
> Let's suppose a cracker somehow was able to design a cryptovirus, not the kind that encrypts your hard drive and asks for a ransom, I'm talking about the kind that *uses* encryption to prevent it from being *detected* by antiviruses. Even if a cracker were able to design such a virus, I doubt it would be able to survive repeated reformatting. It could avoid detection, but it could not survive being overwritten by random data.Malware does encrypt and obfuscate itself.  Typical Windows malware cannot survive being overwritten. Repeated passes are unnecessary- one overwrite is sufficient. 

> **John_Patrick_Mason said:**
> What if I put files on a DVD -- I'm not talking about creating a bootable DVD, I'm talking about just transferring files onto a DVD using an Ubuntu machine -- and then pop in the DVD into an infected Windows machine, install the files that are on the DVD on the Windows machine, and then remove the DVD from the tray and pop it back in my Ubuntu machine? Since DVDs have no firmware to speak of, I should be safe, right?You won't infect Ubuntu with Windows malware. But I would reformat the DVD (if it was read/write) if you plan on using it on other Windows machines.
> **John_Patrick_Mason said:**
> I knew it, I knew it, I knew it. Isn't that why Windows 7 OEM install disks are R+/- only? No, there's no need for writing on an installation disc so it's not included> My comment, though, had more to do about doing the reverse, transferring possibly infected files onto a DVD that are on a Windows machine, like music files and pictures, and then popping in the DVD into my Ubuntu machine, while running a Windows 7 virtual machine with a good antivirus program installed, such as Avira or Avast to scan the contents of the DVD in order to determine if any kind of malware has attached itself to any of those files, in order to determine what to keep and what not to keep. No firmware, no problem.
No, you can transfer infected files easily from Windows to a vm inside Ubuntu running a Windows guest. Scanning the DVD with a few AVs is a decent idea but not fool proof. Word and Excel documents with macros are always suspect. Any "free" music or videos you downloaded are suspect.

---

