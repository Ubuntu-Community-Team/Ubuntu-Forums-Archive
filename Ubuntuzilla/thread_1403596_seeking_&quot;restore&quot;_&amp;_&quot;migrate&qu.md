---
title: "seeking &quot;restore&quot; &amp; &quot;migrate&quot; for Thunderbird &amp; Firefox"
date: 2010-02-10
forum: Ubuntuzilla
---

### Post by SaintDanBert on 2010-02-10
**[color=orange] How do I recover all of my mozilla stuff from "over there" into the working Karmic "over here?" [/color]** 
I cannot be the first person to have something like this happen. 
I cannot believe that there is not a good HOWTO for this sort of thing. I really REALLY need to get my historical messages and contacts back. Can someone please explain...

**_My Situation_**
Over there, I have a Firefox profile and a Thunderbird+Lightning profile *including me email messages* from a running Ubuntu Hardy (v8.04.3 LTS).

Over here, I have a new Ubuntu Karmic (v9.10) with everything installed from the repositories including Firefox and Thunderbird + Lightning (+Sunbird).

Between here and there is a drive created with Clonezilla that then became corrupted shortly afterwards because of a loose operator nut during an upgrade to Jaunty (v9.04).

I think that I have backup files of everything that matters in addition to readable folders at here, there and between.

This was supposed to be a straight forward, every day, replace the drive with new and larger until the operator nut became loose.

Cheers,
~~~ 0;-Dan

---

### Post by nanotube on 2010-02-10
hi
well, this is the ubuntuzilla subforum, for support specifically with the ubuntuzilla project... so if the below info doesn't help, you might have better luck in the general support forum which gets looked at by more people.

that said, here's the info:

the firefox profile gets stored in the ~/.mozilla directory, the thunderbird profile in the ~/.mozilla-thunderbird

so if you want to copy your profile from old drive to new drive, just copy those directories over into your home dir.

---

