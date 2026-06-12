---
title: "Virtual KVM"
date: 2008-11-27
forum: Virtualisation
---

### Post by ubernatural on 2008-11-27
Note that the following tip is from a newbie, so proceed with caution.

Here's a trick I just discovered to have a VM in fullscreen mode and still be able to switch back to the host with just a keystroke (like I would with a KVM).  I use this with VirtualBox, but I suspect it would work also with other virtualization software.

1.) When logged in to an X session, press Ctrl-Alt-F1.
2.) Log in to the virtual terminal with the same credentials as you're logged in as on your X session.
3.) Type the following:
```
startx -- :3
```
This will start up another X session on the fourth graphical virtual terminal (F10), and will switch you over to it automatically.
4.) From this new X session, start a VM and put it in fullscreen mode.

You can switch back to your original X session displaying the host by pressing Ctrl-Alt-F7.  To get back to the guest, still in fullscreen, press Ctrl-Alt-F10.  etc etc.

Note 1: Your original X session may actually be on the third virtual terminal (Ctrl-Alt-F9) - this can happen if you have multiple different logins active at the time.  Same idea though.

Note 2: The first time I logged in to another X session while the first was still active, Ubuntu's help system went bananas and opened up about a hundred of the "Ubuntu Help Center" windows before I could manage to log off.  When I did manage to log off, my session was changed to XFCE when I logged back in again (oddly).  I just logged off XFCE, switched my default session back to GNOME, and haven't seen the problem again.

---

### Post by bodhi.zazen on 2008-11-27
Yes, it is nice. You can use what I call Virtual X sessions for all kinds of things.  You can also have Vitrual X sessions within X as well.  [http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)   [http://ubuntuforums.org/showthread.php?p=3816948#post3816948](http://ubuntuforums.org/showthread.php?p=3816948#post3816948)

---

### Post by ubernatural on 2008-11-29
Wow.  That script is awesome.  Way better than startx...:)  Thanks!

---

### Post by bodhi.zazen on 2008-11-29
You are most welcome, glad you enjoyed it :)

Multiple X sessions are very cool indeed.

---

