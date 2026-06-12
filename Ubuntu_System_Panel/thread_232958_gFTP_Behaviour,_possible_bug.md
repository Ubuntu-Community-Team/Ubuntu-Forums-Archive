---
title: "gFTP Behaviour, possible bug?"
date: 2006-08-09
forum: Ubuntu System Panel
---

### Post by MarcDM on 2006-08-09
gFTP, when started from the "Main Menu", opens with my home directory on the local side. 

When started from USP, it opens with the root (/) directory on the local side. 

In the original menu, the command says ```
gftp %u
```, but in USP it only executes gftp.

If I add the %u to the USP execution string, gFTP opens, but asks for a username, and still reverts to /

I'm not sure what's going on here, but I suspect it could have something to do with the "current folder" as far as USP is concerned. 

Anyone else notice anything similar?

Or maybe I'm going crazy. :sad:

---

### Post by chanders on 2006-08-09
> **MarcDM said:**
> gFTP, when started from the "Main Menu", opens with my home directory on the local side. 

When started from USP, it opens with the root (/) directory on the local side. 

In the original menu, the command says ```
gftp %u
```, but in USP it only executes gftp.

If I add the %u to the USP execution string, gFTP opens, but asks for a username, and still reverts to /

I'm not sure what's going on here, but I suspect it could have something to do with the "current folder" as far as USP is concerned. 

Anyone else notice anything similar?

Or maybe I'm going crazy. :sad:


What version of USP are you running? This problem was fixed in 0.33

I have gFTP installed and when it is opened from USP (0.33) it opens in my home directory...

---

### Post by MarcDM on 2006-08-09
Yup, upgraded to 0.33 and now it works as expected. Excellent dude.

What caused it though?

---

### Post by chanders on 2006-08-09
> **MarcDM said:**
> Yup, upgraded to 0.33 and now it works as expected. Excellent dude.

What caused it though?

Previously USP caused all applications to be launched at / 
Now the user directory is the base before any applications are launched..

---

