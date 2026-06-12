---
title: "Gui updating without authentication"
date: 2011-10-15
forum: Security
---

### Post by lovbuntu on 2011-10-15
In previous releases of Ubuntu, installing updates using the GUI required the user's password. In Ubuntu 11.10 this as change. Is there a specific reason for this change?

---

### Post by The Cog on 2011-10-16
Which desktop are you using. and which installer program?

I'm on xubuntu, and can confirm that I have to enter my password to start synaptic, or to actually install something from the software centre.

Note that there may be a timer that allows you to do things without re-entering your password for a while (15 minutes, IIRC) after already having entered it once. You may simply have been inside that timer window.

---

### Post by Larkspur on 2011-10-16
> **lovbuntu said:**
> In previous releases of Ubuntu, installing updates using the GUI required the user's password. In Ubuntu 11.10 this as change. Is there a specific reason for this change?

This is a change to Update Manager only.  I believe it was made because it was realised that you are updating programs you have previously given permission to install.  With programs that install new stuff (Software Centre and Synaptic), behaviour is unchanged.

---

### Post by The Cog on 2011-10-16
Ooh yes. I wonder if that's restricted to members of the admin group - I'll have to try and see. 

I'm not sure I like that change.

---

### Post by lovbuntu on 2011-10-16
> **The Cog said:**
> Which desktop are you using. and which installer program?

I'm on xubuntu, and can confirm that I have to enter my password to start synaptic, or to actually install something from the software centre.

Note that there may be a timer that allows you to do things without re-entering your password for a while (15 minutes, IIRC) after already having entered it once. You may simply have been inside that timer window.

I'm using the gnome version.

> **Larkspur said:**
> This is a change to Update Manager only.  I believe it was made because it was realised that you are updating programs you have previously given permission to install.  With programs that install new stuff (Software Centre and Synaptic), behaviour is unchanged.

Oh, I see. I'm a bit paranoid so i'll be updating from the cli from now on:)

---

