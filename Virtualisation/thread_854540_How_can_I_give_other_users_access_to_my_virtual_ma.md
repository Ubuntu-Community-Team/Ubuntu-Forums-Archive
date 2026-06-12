---
title: "How can I give other users access to my virtual machine?"
date: 2008-07-09
forum: Virtualisation
---

### Post by BetterSense on 2008-07-09
My wife and I were sharing an Ubuntu account, but I got tired of that and made her her own account. 

She can run Virtualbox from her account, but it says there are no virtual machines installed. 

I tried copying /home/chaz/.Virtualbox to /home/jami/.Virtualbox, but still the same thing. She is a sudoer and a member of vboxusers.

The virtualbox was her baby anyway so that she can run her windows programs, how can I give it to her?

---

### Post by tamoneya on 2008-07-09
have you tried symbolically linking the two .VirtualBox directories?


EDIT: Go into virtual box in here account and go file -> preferences,  Then point it at your directories instead of hers.

---

### Post by BetterSense on 2008-07-09
I did that, and it still doesn't work. It still works under my original user acount, but not after copying .Virtualbox to the new home directory and also not by pointing it to my old home directory. Is it a permissions issue with my old home directory?

---

### Post by tamoneya on 2008-07-10
most likely it is permissions.  Try adding jami to the group chaz.

---

### Post by SR_ELPIRATA on 2009-12-26
This made it for me, sharing a virtualbox machine with 4 users :) Thanks tamoneya!

---

