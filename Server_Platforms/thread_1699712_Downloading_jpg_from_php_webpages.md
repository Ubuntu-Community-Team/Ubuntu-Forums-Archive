---
title: "Downloading jpg from php webpages"
date: 2011-03-04
forum: Server Platforms
---

### Post by lifelike27 on 2011-03-04
Hey guys,

I have a problem. I'm trying to create an archive of a websites images because it tends to go offline now and then. 

The problem is, when going to the image in full view, it opens it on a php webpage.

I've tried using 'wget -m -A.jpg' but it only saves the thumbnails from the menu page instead of the actual images.

Any ideas?

Always nice to know someones there to help. :D

---

### Post by linuxbasiccommand on 2011-03-04
> **lifelike27 said:**
> Hey guys,

I have a problem. I'm trying to create an archive of a websites images because it tends to go offline now and then. 

The problem is, when going to the image in full view, it opens it on a php webpage.

I've tried using 'wget -m -A.jpg' but it only saves the thumbnails from the menu page instead of the actual images.

Any ideas?

Always nice to know someones there to help. :D
You add address image full in command

---

### Post by lifelike27 on 2011-03-04
If you mean for one specific image, I don't think that would help since I'm trying to download multiple images.

I've also tried specific folder that that images were in. Still doesn't work.

---

### Post by SeijiSensei on 2011-03-05
See if adding "-r" to the wget options helps.

---

### Post by lifelike27 on 2011-03-05
To make it recursive right? Yeah, did that too.

If I type in the whole link with the .jpg, it can pick it up...

---

