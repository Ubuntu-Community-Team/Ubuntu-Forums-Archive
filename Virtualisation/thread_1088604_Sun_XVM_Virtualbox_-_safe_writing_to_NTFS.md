---
title: "Sun XVM Virtualbox - safe writing to NTFS?"
date: 2009-03-06
forum: Virtualisation
---

### Post by Sol401 on 2009-03-06
Hello, I have searched the sticky and looked through the threads here, but have found nothing about this concept.

I have as host Ubuntu 8.04 LTS (Hardy) and under the latest version of the Sun XVM Virtualbox, running as guest is Windows XP service pack 3. It works just fine, no complaints.

Preamble: I have enabled "shared folders" so that within my Windows XP guest, I can read and write to any folder on any partition (as I set a shared folder as / )

My question is, is it "safe" (from a data loss perspective, or file system corruption perspective, or any other perspective!) to use the guest OS to save and write either new files, or update existing files, in folders that are either Linux EXT3 formatted, or Windows NTFS formatted? I do both of these from Virtualbox under the guest OS, and suddenly I find myself worried if it's safe to do so.

Any feedback on this would be great, thanks! :popcorn:

---

### Post by howefield on 2009-03-06
I think the fact that you cannot find anyone else writing about  problems in this area should be reassuring :)

Certainly, I have never had a problem with file corruption between host/guest or vice versa, but it could happen just the same as manipulating files within the same system.

Just make sure you have a good backup system so you can roll back if needed, but this would be same on any system.

---

### Post by Sol401 on 2009-03-06
Hi, Thanks for the reply! You're right... I'm glad nobody else has reported this problem... Thanks again!:D

---

