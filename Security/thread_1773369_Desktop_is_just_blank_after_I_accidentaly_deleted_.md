---
title: "Desktop is just blank after I accidentaly deleted login.keyring !"
date: 2011-06-02
forum: Security
---

### Post by Zeerots on 2011-06-02
Help ! Following bad instructions too fast to reset the default keyring password I deleted the file .gnome2/login.keyring !

I can still login and get to a terminal and do instructions from there. I can also still login with root and a guest account.

But my desktop is just blank and I can't, even as a root, access my files.

---

### Post by Zeerots on 2011-06-02
Please help. I can't access months of data. I've searched for hours.

Many sites ask to: sudo rm ~/.gnome2/keyrings/login.keyring to remake the login.keyring automatically. This is what i did.

Is it possible that my system couldn't remake it because I have an (I think) Encrypted Private Directory ?

I'm running Ubuntu 10.10 Maverick.

---

### Post by CandidMan on 2011-06-02
Not sure why you would need sudo for this command:
```
sudo rm ~/.gnome2/keyrings/login.keyring
```
If it's your own home directory. That "~" might have directed the command towards /root/.gnome2/keyrings/login.keyring
Just a thought

---

### Post by Zeerots on 2011-06-02
Thanks, the syntax can be better maybe, but the point is I deleted that file.

Which is a common solution for "2nd-keyring-logon" problem, that apparently is very dangerous ! Now all my data is unaccessible. A fresh install can not help.

It's incredible that Debian and Ubuntu still haven't solved that "2nd-keyring-logon" problem that everybody experiences. 

And when you let users log in without password then why not let users choose a 5-6 character password the GUI way !!

Now, after logging in I just get some error messages like "could not update ICEauthorithy" and could not make directories for Nautilus. Then a total blank desktop.

As root I can see my home directory unmounted, but still with 2 weird files in it; telling me to decrypt with a pass phrase. I found my pass phrase back on a piece op paper, but however I use the pass phrase, nothing changes.

---

### Post by Dave_L on 2011-06-02
Here's some info on how to mount an encrypted home directory:

[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)
[http://ubuntuforums.org/showthread.php?t=1597246](http://ubuntuforums.org/showthread.php?t=1597246)

I don't know how to fix the keyring problem.  I back up everything, so I can recover from my mistakes, but that doesn't help you.

---

### Post by Zeerots on 2011-06-02
Thanks Dave_L !
While trying this mounting of my home folder I discovered I had to use an older password. Strange.

So I just changed my general Ubuntu password to that older password and logged out and in, and BINGO ! Everything is back like before !

The encryption system clearly tries to use the login password first and then will create a new login.keyring file ;-)

I'll backup weekly now.

And later will check if I can help Ubuntu become truely "single sign on".

---

