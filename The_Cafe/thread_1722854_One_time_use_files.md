---
title: "One time use files?"
date: 2011-04-06
forum: The Cafe
---

### Post by cyb3r_sn4k3 on 2011-04-06
Is it possible to make a file which will only run once.(maybe deletes itself too :P) ?

---

### Post by Sporkman on 2011-04-06
Why, yes.

---

### Post by whiskeylover on 2011-04-06
Just put a 
```
rm $0 
```
at the end of the script... assuming its a bash script.

---

### Post by cyb3r_sn4k3 on 2011-04-06
What if its not a bash script ? What if its like a video or smthin?


> **Sporkman said:**
> Why, yes.


Can you tell us how? :)

---

### Post by Sporkman on 2011-04-06
> **cyb3r_sn4k3 said:**
> What if its not a bash script ? What if its like a video or smthin?





Can you tell us how? :)

If it's a C program, put "remove(<filename>);" as the last step. If not C, then use an equivalent function in whatever language it's written in.

You could make it smarter by writing a function called "self_destruct()" or something, which uninstalls itself, gives the user warning, whatever.

---

### Post by disabledaccount on 2011-04-06
It's impossible.
Self-deletion: You can just undelete/recover the file (if not just restore from trashcan)
Self-overwriting: more clever, but user may copy the file before using.
Bad-copy protection: never worked really.

One exception: It's relatively simple to implement such functionality for remote files - just simple modification to host software - but it works only for remote file, not for local copy.

So: files can't be really made as one-time-use. But when working in specialized environments implementation of one-time-use data is reletively simple - f.e. Video-On-Demand (VOD) - user can't save data stream in it's original version unless he will crack decoder firmware.

---

