---
title: "pulling out a pen drive"
date: 2009-10-26
forum: The Cafe
---

### Post by kpholmes on 2009-10-26
if i was running linux on a pen drive, and i pulled it out while linux was still running. what would happen? other then it stopping, would the computer just draw a blank?

---

### Post by Paqman on 2009-10-26
If the system was writing to a file on the stick at the time, you'd probably get a corrupted file. Otherwise nothing.

---

### Post by Exodist on 2009-10-26
NSA will break your doors down and arrest you..



lol, to be honest I am not 100% sure. Depends if it was in the middle of writing information or just sitting there. I have heard of it messing up the pin drive, but I havent had it screw up "yet". Best to always unmount the filesystem to be safe tho.

---

### Post by kpholmes on 2009-10-26
ya i the idea came to my mind today and i just had to ask.
haha

---

### Post by Bachstelze on 2009-10-26
Nothing really. It's not *BSD. :p

---

### Post by schauerlich on 2009-10-26
It'd be somewhat like rm'ing the whole drive. What's in RAM would try to go on, but in all likelihood, would crash after not being able to find something it needs. Such as, you know, a root partition.

> **Bachstelze said:**
> Nothing really. It's not *BSD. :p

You anti-BSD troll!

---

### Post by edin9 on 2009-10-26
Is this a euphemism?

---

### Post by The Real Dave on 2009-10-26
For me, ends up with a few corrupted files, and an icon stuck my desktop because no one un-mounted it :) Nothing killer

---

### Post by tom66 on 2009-10-26
I did it with Ubuntu and a 20 GB HDD. No swap. Kept running for almost 6 seconds and I was able to type into OpenOffice.org. But then, kernel panic and freeze.

---

### Post by hessiess on 2009-10-26
It would work until the OS needed to read something from the disk.

---

