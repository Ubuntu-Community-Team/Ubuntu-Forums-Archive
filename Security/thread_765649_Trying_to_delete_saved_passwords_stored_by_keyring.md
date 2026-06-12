---
title: "Trying to delete saved passwords stored by keyring."
date: 2008-04-24
forum: Security
---

### Post by gt_momo on 2008-04-24
I saved a password I didn't want to when I created a connection to an FTP server by going to the Places menu and then selecting Connect To Server...

How can I access the area this password is stored in and delete the password?

---

### Post by Oldsoldier2003 on 2008-04-25
if you have seahorse installed you can delete the key by right clicking and selecting delete this key. Can't remember offhand how to do it from the terminal

Seahorse is a really nice keyring manager. I recommend it.

---

### Post by Patsoe on 2008-04-25
Not sure, but I think the file is under ~/.gnome2/keyrings/

---

### Post by jphase on 2009-02-15
I had a similar issue. I just configured ubuntu server 64 bit with a gui and setup my login window to automatically login to my user (so I could restart my server remotely and have it connect to the internet on its own). I had the same keyring question when it booted before it could connect to the internet.

Here's how I fixed it for my wifi connection with WEP Password:

1) Right click  on the internet connection/signal icon near your clock, go to Edit Connections...
2) I clicked on Wireless tab, but an ethernet connection would obviously be the wired tab, and deleted my connection (with the password stored in it).
3) Open Terminal:
   cd ~/.gnome2/keyrings
   rm -rf *.keyrings
4) Reboot

   If it asks for a password for your connection on startup, put it in. Reboot again to see if the Unlock Keyring window prompts you again. If it does, repeat steps 3 and 4.

   Hope this works for you as easily as it did for me. :|

---

### Post by darkazurka on 2011-05-04
> **Oldsoldier2003 said:**
> if you have seahorse installed you can delete the key by right clicking and selecting delete this key. Can't remember offhand how to do it from the terminal

Seahorse is a really nice keyring manager. I recommend it.

CORRECT! WORKED!!

I finally managed to do it and I wanted to share it, although Oldsoldier2003 had already found the solution. Seahorse -> Passwords(tab) -> Right click on "Login" (or whatever you want to delete) -> select "Delete" -> Press "Delete" for confirmation.

All done in a graphical user interface. You don't need to touch the cli/terminal!

---

