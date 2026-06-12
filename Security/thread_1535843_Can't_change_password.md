---
title: "Can't change password"
date: 2010-07-21
forum: Security
---

### Post by feedmecereal on 2010-07-21
When I go the the Change Password dialog box and type my new password, the box seems to stall forever when I try to change my password. The Authenticate and Change password buttons are grayed out but the Close button still works and when I click on it the box will close without changing my password.

---

### Post by aphatak on 2010-07-21
I assume you are using the System -> Preferences -> About Me dialog, and then clicking on the Change Password button to get the change password dialog (attached).  Just to make sure - have you typed your current password in the box?  (Don't want to imply you missed this, but I have been known to overlook the obvious.)

---

### Post by feedmecereal on 2010-07-21
> **aphatak said:**
> I assume you are using the System -> Preferences -> About Me dialog, and then clicking on the Change Password button to get the change password dialog (attached).  Just to make sure - have you typed your current password in the box?  (Don't want to imply you missed this, but I have been known to overlook the obvious.)

That's the one I'm looking at right now that isn't doing anything as I'm typing this. I've tried both typing it in the box and typing it in gedit and then copy/pasting it. It doesn't work either way.

I've also tried the "Change User Password" box under "User Settings."

---

### Post by warda on 2010-07-21
hi there,

can you rahter use 

**sudo passwd username**   from terminal? I think in linux you should issue sudo comand to change passwords.
thanks

---

### Post by feedmecereal on 2010-07-21
> **warda said:**
> hi there,

can you rahter use 

**sudo passwd username**   from terminal? I think in linux you should issue sudo comand to change passwords.
thanks

I was reluctant to do that at first because I was afraid of typos (I was copying from gedit). But, yes, that worked. Thanks.

Edit: Actually, I guess I could have still copied from gedit. Oh, well.

---

### Post by warda on 2010-07-21
> **feedmecereal said:**
> 

Edit: Actually, I guess I could have still copied from gedit. Oh, well.

any way to success is good as long as it doesn't cause harm to others :p

happy to hear you got it sorted

---

