---
title: "How to disable shutdown for normal user?"
date: 2010-03-12
forum: Server Platforms
---

### Post by watgate on 2010-03-12
[FONT=Garamond]Dear All,
Hi, for security reasons, I want to disable shutdown for normal user, but the post [here]("http://embraceubuntu.com/2006/03/20/disable-shutdown-for-normal-users/") does not help me. It is because when I open the [/FONT][FONT=Garamond]/etc/X11/gdm/gdm.conf I just saw a blank file. I use the 9.10 version.Who can help me?
Best Wishes,
Chaut0:popcorn:
[/FONT]

---

### Post by watgate on 2010-03-14
[FONT=Garamond]Dear All,
Hi, for security reasons, I want to disable shutdown for normal user, but the post [here]("http://embraceubuntu.com/2006/03/20/disable-shutdown-for-normal-users/") does not help me. It is because when I open the [/FONT][FONT=Garamond]/etc/X11/gdm/gdm.conf I just saw a blank file. I use the 9.10 version.Who can help me?
Best Wishes,
Chaut0:popcorn:[/FONT]

---

### Post by joberly on 2010-03-14
You can always change the executable bit from the shutdown command to owner executable only (it is owned by root). However, I don't know the ramifications of this on other parts of the system. Example, if you are logged into an X11 session as a regular user and use the GUI shutdown command, if it will prompt you for the "sudo" password, or simply fail. In the latter case, you will have to enter a terminal and sudo shutdown.

---

### Post by jvdongen on 2010-04-28
Hi,

I'm in the same boat, trying to get rid of the "shutdown", "restart", "suspend" and "hibernate" options (for normal users) from the desktop menu in Karmic. Searched high and low, policykit, the article referenced by the OP etc. 

Any hints appreciated!

BTW: the option of disabling the executable bit for the shutdown command does not work.

Rgds,
Jeroen

---

### Post by windependence on 2010-04-28
Guys this should be in the desktop forums as Ubuntu server does not let a "normal" user shut down the box by default as there is no GUI and unless you sudo and know the password you are not going to shut down the server. 

The answer to your question lies in creating the user without shutdown privileges in their own login. This is why a GUI on a server is dangerous.

-Tim

---

### Post by AlsoDaniel on 2011-03-25
> **jvdongen said:**
> Hi,

I'm in the same boat, trying to get rid of the "shutdown", "restart", "suspend" and "hibernate" options (for normal users) from the desktop menu in Karmic. Searched high and low, policykit, the article referenced by the OP etc. 

Any hints appreciated!

BTW: the option of disabling the executable bit for the shutdown command does not work.

Rgds,
Jeroen

the helper that handles logout, shutdown, and restart is /usr/lib/indicator-sesson/gtk-logout-helper.
it calls /sbin/shutdown with -r now options in the case of restart and
it calls /sbin/shutdown with -h now options in the event of shutdown.

my solution to this was to <code> sudo mv /sbin/shutdown /sbin/shutoff </code>.
this leaves the normal user with the logout option only.
root may run <code> /sbin/shutoff -h now </code> to shutdown

Daniel

---

### Post by AlsoDaniel on 2011-03-25
oh and <code> sudo mv /usr/sbin/pm-hibernate /usr/sbin/hibernate </code>
will stop the hibernate button as well.


-daniel

---

