---
title: "How do you change amount of &quot;fake video memory&quot; in wine?"
date: 2010-01-01
forum: Wine
---

### Post by s3a on 2010-01-01
The following comment tells me what is likely going to solve my problem with wine but I don't fully understand it:

"Try to lower the resolution. If that helps, you're running out of faked video memory, maybe because the card detection fails. You can override the amount of video memory we fake with a registry key**(HKEY_CURRENT_USER/Software/Wine/Videomemory)** I think. Set it to e.g. "512" to fake 512 MB of vidmem. (It is a string value, not a DWORD)."

My problem is I don't know how to get to the part that's bold so that I can edit it in the first place.

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by Soulcage on 2010-01-01
Go to [http://wiki.winehq.org/UsefulRegistryKeys]("http://wiki.winehq.org/UsefulRegistryKeys") read the top part then do a search for "VideoMemorySize" add that part like it says.

---

### Post by s3a on 2010-01-01
I don't see a Direct3D section under wine. (See attached screenshot)

---

### Post by AllRadioisDead on 2010-01-01
> **s3a said:**
> I don't see a Direct3D section under wine. (See attached screenshot)
 That's why you make one.

---

### Post by s3a on 2010-01-01
Am I doing it correctly now? (See attached screenshot)

---

### Post by Soulcage on 2010-01-01
Read the  instructions at [http://wiki.winehq.org/UsefulRegistryKeys]("http://wiki.winehq.org/UsefulRegistryKeys")

---

### Post by s3a on 2010-01-04
I did. In fact, that's how I got as far as I did. Sorry for being stupid :(

---

### Post by Soulcage on 2010-01-04
Right click in the window on the right and choose new -> string value
then paste in VideoMemorySize for the name and type in the your memory in megabytes.

---

### Post by s3a on 2010-01-04
Thanks!

---

