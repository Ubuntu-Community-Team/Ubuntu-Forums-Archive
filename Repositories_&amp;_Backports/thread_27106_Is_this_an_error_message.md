---
title: "Is this an error message?"
date: 2005-04-14
forum: Repositories &amp; Backports
---

### Post by lmellen on 2005-04-14
I just finished installing Kubuntu, and during install I didn't change the hostname. After the install was finished I didn't like the length of the
 prompt, so I went back into /etc/hostname and changed it.
Now I'm getting this message:
"sudo:unable to lookup ubuntu via gethostbyname()"
Is this normal, or did I screw someting up?
I did "sudo apt-get update" and a bunch of files were downloaded.
At "sudo apt-get upgrade" nothing was changed? I do have a brand new install of course! Maybe everything is OK, I just keep thinking I'm screwing everything up!  Thanks -- Larry :neutral:

---

### Post by mendicant on 2005-04-15
For a new install, you won't have anything to upgrade.  No security updates yet.

For the gethostbyname() thing, I imagine it will disappear if you log out and log back in.  Usually, you would change the hostname using the hostname command.  Also check /etc/hosts, and make sure it doesn't have any stale entries.

---

### Post by heimo on 2005-04-15
If you have too long prompt, you don't need to change hostname (hostname is the name of your computer). You only need to edit ~/.bashrc (configuration for your shell). Sorry for short instructions (13 minutes to catch train..) but you can get more information with *man bash*.

Try changing the /etc/hostname back to what it was. Then try running *hostname *(not the file, command). It should not give any errors.

EDIT: Oh! And yes, you should use  ```
hostname [hostname]
``` to edit that file anyway. :D Hope you can get it fixed.

---

### Post by lmellen on 2005-04-15
:) That worked! I'm back to the long prompt, but I can fix that later. I'll use the hostname command from now on! Thanks -- Larry :)

---

