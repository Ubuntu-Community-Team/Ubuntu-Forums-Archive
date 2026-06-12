---
title: "Changing sudo timeout"
date: 2011-04-30
forum: Security
---

### Post by cat2005 on 2011-04-30
I have been using Ubuntu 9.04 for a long time.  I remember I did something that eliminated the "15 minute" grace period for entering the sudo password.  Whatever I did, I set some timeout, timestamp or something like that to "zero".  Doing so forced me to enter my sudo password everytime I needed sudo.

Unfortunately, I can't remember what it was I did to achieve that.  A quick google search is not yet yielding results.

I am switching to Ubuntu 10.10 and want to implement the same sudo "timeout" behavior.  In other words, I want to be forced to enter my sudo password everytime I need sudo.

There was some entry somewhere that I edited but I can't remember where it was or what I did.

Could anyone help me narrow it down?

Thanks.

---

### Post by Dave_L on 2011-04-30
According to "man sudoers", you would set the parameter timestamp_timeout to 0 in the file /etc/sudoers. But I'm not sure of the proper syntax, or if the location within the file matters.

You can also achieve this with the command "sudo -k", but that would have to be done every time you use the sudo command.

---

### Post by cat2005 on 2011-04-30
> **Dave_L said:**
> According to "man sudoers", you would set the parameter timestamp_timeout to 0 in the file /etc/sudoers. But I'm not sure of the proper syntax, or if the location within the file matters.

You can also achieve this with the command "sudo -k", but that would have to be done every time you use the sudo command.


Could I edit that file with "gksudo" then "nautilus"?

---

### Post by Dave_L on 2011-04-30
> **cat2005 said:**
> Could I edit that file with "gksudo" then "nautilus"?

Yes, "gksudo nautilus" will allow you to edit /etc/sudoers.  I suggest making a backup copy of the file before changing it.

---

### Post by ChrisWells on 2011-04-30
do sudo nano /etc/sudoers or gksu gedit /etc/sudoers  find the defaults line and add a comma then timestamp_timeout=0  mine looks like this: defaults,timestamp_timeout=0

---

### Post by cat2005 on 2011-05-01
> **ChrisWells said:**
> do sudo nano /etc/sudoers or gksu gedit /etc/sudoers  find the defaults line and add a comma then timestamp_timeout=0  mine looks like this: defaults,timestamp_timeout=0


So, I should edit the line so the final product looks like this:

defaults,timestamp_timeout=0

Correct or not?

Thanks!

---

### Post by CharlesA on 2011-05-01
Always use visudo to edit the sudoers file. It checks for syntax and whatnot before saving, so you don't accidentally mess something up.

See here too: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cat2005 on 2011-05-02
Thanks all - if I have problems again / still, then I will post another thread.

---

### Post by cariboo on 2011-05-02
Wouldn't it just be better to subscribe to this thread for future reference?

---

