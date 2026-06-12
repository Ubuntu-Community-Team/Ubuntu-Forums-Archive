---
title: "Adding a user"
date: 2011-03-10
forum: Security
---

### Post by tidefan on 2011-03-10
so i set up a linux 10.10 desktop to run as a "server" for me. I then loaded Xrdp so that we can remote connect to the machine. My issue now is, i need to add users other than the initial account i created, but when i log into the desktop remotely, it will not let me add a new user. I cant seem to use any of the boxes in the User Settings command box. Does anyone have any suggestions?

---

### Post by mikewhatever on 2011-03-10
Do you get any error messages?

---

### Post by bodhi.zazen on 2011-03-10
Use webmin (or similar web interface).

Desktop environments (gnome / KDE / XFCE / Fluxbox) are of little value on a server.

Use ssh rather then VNC (or Xrdp).

---

### Post by tidefan on 2011-03-10
no, it just wont let me add them. I was able to add a user thru command line, and then Manage groups, but that was it. 

Now, i have created 2 other users, but i cannot remote connect using those 2 other accounts, just the initial account. When i remote in, it looks like it is going to connect with the other account, but then it says there is a password issue. I cant seem to find where i can allow remote desktop for the new accounts.

---

### Post by tidefan on 2011-03-10
> **bodhi.zazen said:**
> Use webmin (or similar web interface).

Desktop environments (gnome / KDE / XFCE / Fluxbox) are of little value on a server.

Use ssh rather then VNC (or Xrdp).

it isnt a true server, it is a desktop. It is a poor mans server that we have an application that is running on it, and i was going to create a share for my team to put stuff there if we needed. But i also wanted to see if they could log in to their own desktop, rather than everyone sharing the 1 desktop

we like having the GUI available to us.

---

### Post by bodhi.zazen on 2011-03-10
> **tidefan said:**
> it isnt a true server, it is a desktop. It is a poor mans server that we have an application that is running on it, and i was going to create a share for my team to put stuff there if we needed. But i also wanted to see if they could log in to their own desktop, rather than everyone sharing the 1 desktop

we like having the GUI available to us.

Each user can share a desktop or have a unique desktop depending on the vnc server (some share a single desktop, others use unique desktops).

For what you want I highly advise FreeNX or tunneling your VNC over ssh.

Configure your additional users from the desktop then.

---

### Post by tidefan on 2011-03-10
> **bodhi.zazen said:**
> Each user can share a desktop or have a unique desktop depending on the vnc server (some share a single desktop, others use unique desktops).

For what you want I highly advise FreeNX or tunneling your VNC over ssh.

Configure your additional users from the desktop then.

so i installed Freenx using your suggestion, but the authentication keeps failing whenever i try to launch it. I feel as though i followed the instructions off the Ubuntu site. Any suggestions as to why the auth keeps failing?

---

### Post by bodhi.zazen on 2011-03-10
What instructions did you use and what is the exact error message ?

Firewall ?

---

### Post by tidefan on 2011-03-10
i launch it, it says awaiting authentication, then comes back "Authentication failed for user XXXX"

I tried an ssh into the box with my username and it connected fine

a quick google search shows that a lot of people had that same problem, but i couldnt really find a thread that explained why or fixed it.

---

### Post by CharlesA on 2011-03-10
Are you using NX from nomachine.com, or something else?

---

