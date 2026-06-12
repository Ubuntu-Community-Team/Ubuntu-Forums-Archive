---
title: "Kernel Upgrade to 2.6.38-11 caused kernel panic?!"
date: 2011-08-25
forum: System76 Support
---

### Post by birdsarah on 2011-08-25
Hi all,

I received my Gazelle Pro yesterday - very exciting. Spent a day getting up to speed - all is well in the world - it's a wonderful thing.

Last night I did a Software Update (sudo apt-get update && sudo apt-get upgrade). It installed a few things including kernel version 2.6.38-11

Today I was getting kernel panics every few hours. I thought through all the different things it could be and this seemed like a potential source - and the easiest to test!

I uninstalled the kernel so am back to 3.6.38-10 - I've now been going 6 hours and haven't had a panic - which wasn't the case all day.

I don't know if this is actually the problem, but I just wanted to throw it out there in case anyone else sees something weird with this update.

Best,

Bird

---

### Post by birdsarah on 2011-08-25
Looks like I spoke too soon - just happened again. I really don't want it to be a hardware issue so will keep thinking. 6 hours was better than 2 on the upside.

---

### Post by isantop on 2011-08-25
Can you try reinstalling the .11 kernel? I'm thinking that was a red herring, or that it was possibly a corrupt download.

---

### Post by birdsarah on 2011-08-26
Hi,

it now seems like it was a hardware issue. I am running the -11 kernel again and it's working fine. Will post a new thread about the hardware problem.

Thanks,

Bird

---

### Post by Off Shore on 2011-08-26
Yes indeed there seems to be an issue with this particular upgrade. I believe it to be a dependency problem as my system steadfastly refuses to upgrade until everything is in place.

I always use "sudo aptitude update && sudo aptitude safe-upgrade"

---

