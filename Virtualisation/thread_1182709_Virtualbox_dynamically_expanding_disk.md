---
title: "Virtualbox dynamically expanding disk"
date: 2009-06-09
forum: Virtualisation
---

### Post by MTO on 2009-06-09
Hello,
My Virtualbox dynamically expanding disk is not expanding.
I started out with only 10GB thinking it would expand when needed, but I ran out of space and don't see how to expand it.

Hopefully I didn't misunderstand this feature, and wont require to clone/ create new disk for it. 

Am I doing something wrong, or missing something? I see no option to expand it.

Thanks,

---

### Post by boof1988 on 2009-06-09
> **MTO said:**
> Hello,
My Virtualbox dynamically expanding disk is not expanding.
I started out with only 10GB thinking it would expand when needed, but I ran out of space and don't see how to expand it.

Hopefully I didn't misunderstand this feature, and wont require to clone/ create new disk for it. 

Am I doing something wrong, or missing something? I see no option to expand it.

Thanks,

The Virtualbox dynamically expanding disk will only expand up to the predetermined size limit (10GB in your case).  So it wont expand past the 10GB limit that is set.

Is the 10GB already filled?  Is the disk not expanding up to 10GB (stopping expansion before 10GB)?

---

### Post by MTO on 2009-06-09
I guess it stopped expanding at 10GB. :sad:

I guess this means I have to clone the partition into a bigger disk? Ouch!

---

### Post by HermanAB on 2009-06-09
Here is a thread for you:
[http://forums.virtualbox.org/viewtopic.php?t=585](http://forums.virtualbox.org/viewtopic.php?t=585)

---

### Post by boof1988 on 2009-06-10
One other option you could try...

[LIST=1]
[*]Create another virtual-disk (to be used to store data, documents, music, etc.) of whatever size you need.
[*]Format this new virtual-disk to your preferred file-system-type.
[*]Mount this partition at our preferred mount-point.
[*]Create any directories you need on the new virtual-disk and start using it.
[*]You could even transfer any of your existing media to the new virtual-disk (if needed).
[/LIST]

Hope this helps a bit.

---

