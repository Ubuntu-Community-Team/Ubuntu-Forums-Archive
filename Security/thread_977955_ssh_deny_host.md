---
title: "ssh deny host"
date: 2008-11-10
forum: Security
---

### Post by pcr2 on 2008-11-10
Hi.  I answered Deny by mistake when ssh localhost put up a dialog.  Now I cant reach localhost.  How do I correct this.
Thanks

---

### Post by cariboo on 2008-11-10
Could you explain what it is you were trying to do? Are you using denyhosts or fail2ban? More information please.

Jim

---

### Post by pcr2 on 2008-11-11
The long story is I backup by laptop to a desktop using scp -r from the desktop to bring over the laptop home directory.   ssh-server runs on the laptop, not the desktop.

When I upgraded to Intrepid Ibex ssh broke.  I ran ssh-keygen on each machine and copied the public key to an authorized_keys file on the other.  Still no joy so I tested the laptop with ssh localhost.  That brought up a gnome-keyring password dialog.  I had never used gnome-keyring before, so the password it asked for was undefined. Neither Enter nor my login pw worked. To make the dialog go away I clicked on Deny, which was a mistake.

I read online that removing a certain file would make the key
ring pw default to my login  I removed it (I don't recall the filename) on the laptop but not the desktop.

Now ssh localhost on the laptop skips the keyring dialog and gives me "permission denied (public key) while scp -r on the desktop still gives the keyring pw prompt.

cat /etc) /deny.hosts on either machine shows the default hosts.deny file with no hosts entered.

---

### Post by Dave_Connor on 2008-11-11
Have you tried entering the localhost ip 127.0.0.1 and 127.0.1.1 to hosts allow ? And restarting denyhosts ?

---

### Post by iponeverything on 2008-11-11
look under ~/.ssh/

---

### Post by pcr2 on 2008-11-13
Thanks, I decided to start over.

---

