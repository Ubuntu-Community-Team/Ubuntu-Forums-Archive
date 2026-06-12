---
title: "[SOLVED] virtualbox in ubuntu"
date: 2008-12-01
forum: Virtualisation
---

### Post by luckydeveloper on 2008-12-01
hi,

i am running ubuntu as the host OS and windows as the guest OS. just now i installed windows in virtual box. my keyboard is getting captured in the guest OS but my mouse is not getting captured.. please help

---

### Post by soloman498 on 2008-12-01
In Virtual box you click inside the box and a sign comes up telling you what to do

---

### Post by david819 on 2008-12-01
If I remember correctly, I had the same issue, and my solution was simple.  For me, when the little box comes up telling you about capturing the mouse and keyboard there was a little checkbox to make it not tell you that anymore, and by setting it to leave me alone, it worked in the future.  By clicking on the box to say "OK" you were clicking away from VBox, and that uncaptured or something.  I think.  I'm at work, so can't check.  Hope this helps, if it doesn't and no one else has solved your problem by the time I get home, I'll see what I can figure out.

---

### Post by axel206 on 2008-12-01
Install VirtualBox GuestAdditions. It will make it easier for you.

---

### Post by Lacasito on 2008-12-02
To free your mouse you just have to push Ctrl key on your right

If you want to integrate the mouse you should install LinuxAdditions or GuestAdditions (Dependoing on your guest system): There's no other way.

---

### Post by OldDirtyTurtle on 2008-12-02
My experience was the same as David's.  Works great - the popup window was just a little counterintuitive.

---

### Post by luckydeveloper on 2008-12-02
I just installed windows guest additions . my problem is solved. thanks

---

