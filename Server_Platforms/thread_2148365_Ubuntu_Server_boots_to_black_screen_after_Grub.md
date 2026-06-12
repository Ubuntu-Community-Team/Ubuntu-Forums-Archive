---
title: "Ubuntu Server boots to black screen after Grub"
date: 2013-05-24
forum: Server Platforms
---

### Post by Scrumps on 2013-05-24
Well, I figured out my last problem. Now I am faced with a new one. 

After my most recent change I attempted to create a new mdadm array (a Raid 0) after which I restarted the machine. After restarting, I could boot to grub but I was presented with a black screen. There was no network activity (tested by pinging the static IP assigned to the machine). No response to keyboard commands (other than ctrl alt del), and no on screen notices by pressing esc. So I am not sure what happened. 

I was trying to verify if my OS was installed correctly (it was installed on a softraid using mdadm) but, I can't pick it up. Which would really suck. 

Some guidance at this point to where I need to go from here and how I should handle this without possibly breaking anything else would be great.

Thanks

EDIT:

After booting into a live cd and checking the raid, I am not sure what to do from here. Everything appears to be clean, but I still can't get it to boot. 

/var/log/ was not really of any use. Is there a good way to double check if grub has the right path? Though, I don't know why that would have been altered.

---

### Post by Vegan on 2013-05-25
do not use a software raid, its not worth the headaches

if you need more space, get a bigger disk, you can mount the other disk under the / file system

---

### Post by Vegan on 2013-05-25
do not use a software raid, its not worth the headaches

if you need more space, get a bigger disk, you can mount the other disk under the / file system

---

### Post by Scrumps on 2013-05-25
Yeah, eventually I gave up. 

Destroyed my one raid that I have with hardware raid (had a backup so no loss) and then just redid the OS drives.

---

