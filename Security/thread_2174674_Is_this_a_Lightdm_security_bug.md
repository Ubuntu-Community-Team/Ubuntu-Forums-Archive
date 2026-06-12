---
title: "Is this a Lightdm security bug?"
date: 2013-09-15
forum: Security
---

### Post by CaptainMark on 2013-09-15
I've been messing around with Lightdm a bit lately because I only just figured out how to customise the guest session so I've been logging in and out a lot today, that's how I noticed what I'm sure is a bug in lightdm's behaviour

I have a start-up script which sleeps for 30 seconds and then opens pidgin minimized, I kept noticing today that if I log in to my user account, then quickly log out and log in as a guest session (within the 30 secs) then pidgin would start as MY user but on the guest session, so with all of my accounts and contacts available but in the screen of the guest session

I've never noticed this until now, I've been using gdm.

Can anyone confirm this? And if so would this be a lighdm bug?

Not that this pidgin incidence is a huge deal to me but if this is reliably reproduced could lead to serious security risks is some setups

Regards
Mark

---

### Post by jamesisin on 2013-09-15
Are you switching users or are you logging out?

---

### Post by CaptainMark on 2013-09-16
Completely logging out and then logging back into either a guest session or another user from lightdm (result is the same), I confirmed the same behaviour on my netbook install of Xubuntu 13.04, and my desktop running Ubuntu 13.04, both now use lightdm hence the reason I jumped to blame that, I've never seen the same behaviour with Gdm, it only happens with pidgin that I can find so far but still there could be more risky applications that I haven't found that might act the same, this definitely shouldn't happen but the question is which package is responsible

EDIT: I just switched over to Gdm and I actually do see the same behaviour on Gdm so I putting this down to a fault with pidgin, I assume its sending the window to display:0 regardless of which user is logged in

---

### Post by mastablasta on 2013-09-16
is that data not in home folder? because guest is supposed to restrict that folder.

[https://wiki.ubuntu.com/DesktopTeam/Specs/Intrepid/GuestAccount](https://wiki.ubuntu.com/DesktopTeam/Specs/Intrepid/GuestAccount)

interesting find.

---

### Post by 3rdalbum on 2013-09-16
Wow, that's pretty bad. Does it happen for other programs? What about NON-GTK programs? This sounds like a real security flaw and you should report it to Ubuntu or even upstream if you can figure out the culprit.

---

### Post by jamesisin on 2013-09-16
I suppose it could be in the manner in which your script is running.  How are you triggering your script?

---

### Post by CaptainMark on 2013-09-16
I have an entry in startup scripts to run all scripts in ~/Documents/bash/login/ which contains a script that just sleeps for 30 secs and runs pidgin, but honestly it shouldn't matter should it, no scripts or programs should cross over to another user's session unless they've been explicitly programmed to do so

---

### Post by jamesisin on 2013-09-16
The terminal isn't the same as your X session, I believe.  That could be a contributor.  I would have guessed it would launch Pidgin as whatever user happened to be logged in at the time it was called, but if it's being called as you (from a background terminal)...

---

### Post by CaptainMark on 2013-09-17
Any terminal being called as a user (which this is being called by my login session) should not be crossed to another user space, regardless of how many child processes are started by it, the parent process is being called by user mark and should terminate with an error if it cant find a display to connect to belonging to that uer. I call many scripts (~15) this way and pidgin is the only one that behaves like this.

---

### Post by jamesisin on 2013-09-17
Hmmm... isn't the display of the window dependent on the X session and not a user session?  So the window/screen output is sent to Display 0 (or similar)?  For instance I can ssh into a machine and manipulate a running application if I can find it on a display.  Hmmm... (again) I don't think I can ssh in as user A and have an application launch in front of user B in the GUI.  (It may be possible, but I wouldn't know how.)

---

### Post by CaptainMark on 2013-09-17
Yeah it is possible but not by accident, this doesn't happen with any other application, and whilst the launching of Gui's is dependent on the X server the process is started in user space and should be terminated on logging out

---

