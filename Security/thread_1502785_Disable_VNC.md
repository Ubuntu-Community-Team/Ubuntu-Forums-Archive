---
title: "Disable VNC"
date: 2010-06-06
forum: Security
---

### Post by joshedmonds on 2010-06-06
I understand that disabling VNC and SSH are basic desktop security measures (as long as you don't need to use them), however I noticed today that I have Vino installed, along with a couple of other VNC packages. The reason I noticed was an unbidden install of libvncserver0 by the update manager, **which is a new dependency for Virtualbox OSE**.

How can I ensure that VNC is not enabled on my desktop. Is it necessary (or sufficient) to remove Vino and/or other packages, or is VNC not enabled unless I set it up?

---

### Post by an0dos on 2010-06-06
> **joshedmonds said:**
> Is VNC not enabled unless I set it up?

Correct. The program needs to be running (not just having the packages installed) for it to listen / be accessible. Go to "Preferences" --> "Remote Desktop". If the bock "Allow other users to view your desktop" is unchecked, then you shouldn't have anything to worry about.

You can also check to see if it is running by typing the following command in the terminal ```
sudo netstat -tulnp
``` and seeing if it is listed there.

Virtualbox allows you (if you enable it on the VM settings) to access VMs via a remote desktop client. The files you saw were probably related to this and not something to worry about.

---

### Post by joshedmonds on 2010-06-06
Many thanks an0dos.

---

