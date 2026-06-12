---
title: "that generic euca-attach-volumes problem :)"
date: 2011-08-22
forum: Ubuntu Cloud and Juju
---

### Post by Dori922 on 2011-08-22
ive read through a few posts on this here  but havent found an answer :(

Im running UEC(11.04) with the newest version of Euca. I have a 2 machine topology and had it working fine on friday. The instance was up, volume was attached, mounted, items stored on it, detached and reattached again. Worked fine. 

Then i shut down the front end for the weekend and when i got back i ran an instance, SSH'd into it but then when i tried to attach a volume, it went from In Use to Available within a few seconds(2-4).

im posting log files for nc.log and cloud-error.log because reading the other threads, they seem to be the ones that matter :) if you need more please ask! and please help! ;D

NC:

[http://pastebin.com/xRfSyxKR](http://pastebin.com/xRfSyxKR)

CC-Error.log:

[http://pastebin.com/b45rmXyN](http://pastebin.com/b45rmXyN)


<3

Adam

---

### Post by Rusty au Lait on 2011-08-26
Here's what I'm getting.
You have 2 machines: machine 1;CLC,WC,SC,CC and machine 2; NC.
When you shut down the "front end" you mean machine 1.

If you had volumes attached to the instance when you shut down machine 1 those connections will have been broken.

I see it has been a few days. Is everything OK now?

---

### Post by Dori922 on 2011-08-30
Hey Rusty!

Thanks for the reply and yes thats my topology! :D I ended up reinstalling the system and then ran into a problem with the store tab in the cloudip website and working on that now! :p

 i also noticed i didn't have LVM installed which might have affected it.. im learning to create images now so will be testing that after(shutting down Machine 1 with volumes detached and then if that still works with them attached!). 

Just curious but what happens if the instance crashes with the volume attached, is there a way to recover data held on that volume? I want to eventually use this system as a backup! But am worried about what will happen if the SC /Machine1 loses power while the instance is up..

Yours,

Adam

---

