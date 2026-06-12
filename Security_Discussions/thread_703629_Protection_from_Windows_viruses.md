---
title: "Protection from Windows viruses?"
date: 2008-02-21
forum: Security Discussions
---

### Post by sergiodlc on 2008-02-21
I've moved to Ubuntu but Windows viruses keep chasing me. The big problem is that all the people around use Windows so when you plug your removable drive in their PCs your drive can get infected.

I recently inserted my MP3 flash memory in one Windows machine and now I can't see the files that were previously there. Both Windows and Ubuntu show that the flash memory has some space in use, but they show no files or folder and they are not shown even when you display hidden files. I just don't know how to recover those files.

I really need the information there and I would like to know if any of you have some sort of solution to avoid this to hapen again.

Thanks in advance,

Sergio

---

### Post by pytheas22 on 2008-02-21
In the repositories there's a program called photorec that you could use to recover the files on the mp3 drive if they have indeed been deleted by some Windows virus.

If you format your flash drive in NTFS you might be able to make it read-only in order to gain another level of protection, but even then you're not guaranteed to be safe.  You wouldn't have this option in FAT, which is probably what it's formatted as.  You could also try encrypting part of it to protect it from infected Windows machines, although it may still be vulnerable if you unencrypt it while connected, depending on how the virus works.

Otherwise, the best advice I can give is to make sure that if you're sticking your drive into Windows machines that are so badly messed up that they do things like erase all the files on it, make sure you've backed up the files first.  If you don't have control over the Windows machines, there's not much else you can do to protect yourself.  Of course, you should also understand that the Windows viruses won't be able to touch your Ubuntu machine, so there's no risk of getting infected that way.

---

### Post by sergiodlc on 2008-02-21
> **pytheas22 said:**
> In the repositories there's a program called photorec that you could use to recover the files on the mp3 drive if they have indeed been deleted by some Windows virus.

If you format your flash drive in NTFS you might be able to make it read-only in order to gain another level of protection, but even then you're not guaranteed to be safe.  You wouldn't have this option in FAT, which is probably what it's formatted as.  You could also try encrypting part of it to protect it from infected Windows machines, although it may still be vulnerable if you unencrypt it while connected, depending on how the virus works.

Otherwise, the best advice I can give is to make sure that if you're sticking your drive into Windows machines that are so badly messed up that they do things like erase all the files on it, make sure you've backed up the files first.  If you don't have control over the Windows machines, there's not much else you can do to protect yourself.  Of course, you should also understand that the Windows viruses won't be able to touch your Ubuntu machine, so there's no risk of getting infected that way.

Thanks a lot. I will try all this ASAP.

---

### Post by sergiodlc on 2008-03-04
> **pytheas22 said:**
> In the repositories there's a program called photorec that you could use to recover the files on the mp3 drive if they have indeed been deleted by some Windows virus.

If you format your flash drive in NTFS you might be able to make it read-only in order to gain another level of protection, but even then you're not guaranteed to be safe.  You wouldn't have this option in FAT, which is probably what it's formatted as.  You could also try encrypting part of it to protect it from infected Windows machines, although it may still be vulnerable if you unencrypt it while connected, depending on how the virus works.

Otherwise, the best advice I can give is to make sure that if you're sticking your drive into Windows machines that are so badly messed up that they do things like erase all the files on it, make sure you've backed up the files first.  If you don't have control over the Windows machines, there's not much else you can do to protect yourself.  Of course, you should also understand that the Windows viruses won't be able to touch your Ubuntu machine, so there's no risk of getting infected that way.

Hi, I've done what you suggested to me and I could recover some files. However, there are still some missing files and the directory structure was lost. Isn't there another way to better achieve this?

---

### Post by suibhne on 2008-03-04
"...some Linux machines definitely need anti-virus software. Samba or NFS servers, for instance, may store documents in undocumented, vulnerable Microsoft formats, such as Word and Excel, that contain and propagate viruses. Linux mail servers should run AV software in order to neutralize viruses before they show up in the mailboxes of Outlook and Outlook Express users."

'To mess up a Linux box, you need to work at it; to mess up your Windows box, you just need to work on it'

I like these quotes - implies we should save windows

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

---

### Post by pytheas22 on 2008-03-04
> I've done what you suggested to me and I could recover some files. However, there are still some missing files and the directory structure was lost. Isn't there another way to better achieve this?

Not that I know of.  There are commercial undelete tools available, if you're willing to spend a lot of money, that may or may not be able to do more for you than the open-source stuff I suggested, but I've never used them.  If the disk was formatted as NTFS these may be able to help you; if it was FAT, I'd say your chances are less, but you can still search around for terms like "ntfs undelete" or "fat file recovery."  If the virus deleted the partition as a whole (which could explain why the directories disappeared, but not necessarily), you could use testdisk, also in the repositories, to try to recover it.

Photorec works by scanning the disk bit-by-bit looking for file headers, which should still be intact if nothing has overwritten them.  However if the virus overwrote the headers (or parts of the files they were attached to), or you overwrote them later, you're out of luck, as the data is gone forever, as far as I know.  This is why you should never assume that deleting a file or even a whole partition gets rid of your data, because until you overwrite it all with new data, it stays on the disk.

---

