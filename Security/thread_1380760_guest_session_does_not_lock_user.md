---
title: "guest session does not lock user"
date: 2010-01-14
forum: Security
---

### Post by kainalu on 2010-01-14
I noticed (the hard way) that enabling a guest session under 9.04 does not lock the source user. I enabled a guest session for someone and came back to find them rooting through my files. By quitting the guest session, it goes back to the source user's desktop without requiring a password. Shouldnt it go to gnome-screensaver automatically? Can this be changed? Is it a bug?

to replicate:

log into source user's account
use the menu to start a guest session
quit the guest session
root through files un-opposed.

---

### Post by Sarmacid on 2010-01-14
It presented me with the screensaver and required me to enter my password to get back to my session. Do you have passwordless login enabled?

However I did notice that the guest had read and execute access on the truecrypt volume I mounted from my session.

---

### Post by kainalu on 2010-01-14
Nah, it has regular login, needs user and pass. It usually locks screen when it goes to screensaver. weird.

---

### Post by running_rabbit07 on 2010-01-14
Create an actual guest account with an easy BS password. make it a restricted account with no privileges, then go to your home folder and make sure the permissions are set to none for other users. Then sign into that guest account and make sure it doesn't have access.

---

### Post by userid on 2010-01-14
I think the problem is you're entering the guest account from your user a/c, maybe you haven't got lock screen active. I think you should make a guest user, log out from your regular user a/c and then log in via gdm. It will then return to gdm won't it?

---

### Post by kainalu on 2010-01-14
OK, ill do that. I had thought of that, but wasnt sure if there was something I was missing about the builtin. Thanks!

---

### Post by kainalu on 2010-03-04
Just to let the Community know, This problem eventually rectified itself. Ive been doing updates, so maybe one addressed the problem. I did, however, create a permanent Guest account so I didnt have to be bothered with logging in myself just to let someone else use my pc.

---

