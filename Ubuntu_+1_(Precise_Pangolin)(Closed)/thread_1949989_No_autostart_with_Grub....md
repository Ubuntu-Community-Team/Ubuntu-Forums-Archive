---
title: "No autostart with Grub..."
date: 2012-03-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2012-03-31
I've lost autostart in Grub.
I've checked 
/etc/default/grub (GRUB_TIMEOUT=2)
/boot/grub/grub.cfg (commented lines that test grubenv and left only one timeout=2)
/etc/grub.d/00_header (commented lines for testing status of grubenv and left only one timeout=2)
/boot/grub/grubenv (tried both grub-editenv and rm /boot/grub/grubenv)
tried „Native IDE“ and „IDE->AHCI“...
Any ideas?
It must be something simple that I'm overlooking...

---

### Post by Bucky Ball on 2012-03-31
ONLY edit /etc/default/grub. Change the others to what they were.

When you alter that file (change the timeout for instance) you must run:

```
sudo update-grub
```

... afterwards to implement those changes ...

---

### Post by dino99 on 2012-03-31
when things are borked on my side i often choose to purge then reinstall

---

### Post by Bucky Ball on 2012-03-31
> **dino99 said:**
> when things are borked on my side i often choose to purge then reinstall

Generally a last resort and no-where near that I wouldn't think.

---

### Post by zika on 2012-03-31
> **Bucky Ball said:**
> ONLY edit /etc/default/grub. Change the others to what they were.

When you alter that file (change the timeout for instance) you must run:

```
sudo update-grub
```... afterwards to implement those changes ...I did not write every step that I've tried... Yes, I've tried first in grub. Then I went to eliminate possible trouble-spots... Yes, I've used update-grub whenever I've changed some of files that are used in generating grub.cfg... Thank You...

---

### Post by zika on 2012-03-31
> **dino99 said:**
> when things are borked on my side i often choose to purge then reinstallTo small &#8222;bork&#8220; to use so big sledge-hammer... :)
Especially when Grub is a patient...

---

### Post by Bucky Ball on 2012-03-31
> **zika said:**
> to small &#8222;bork&#8220; to use so big sledge-hammer... :)
especially when grub is a patient...

+1 ...

... and considering Precise is not yet released and is still testing!

---

### Post by drs305 on 2012-03-31
It could be that your system is generating a 'recordfail' event that forces Grub to stop at the Grub menu and await a selection. 

Normally this event is triggered by a failed boot, but there are a variety of things that can trigger such behavior. You can check the contents of the 'marker file', /boot/grub/grubenv to see if anything is written there:
```
cat /boot/grub/grubenv
```
Normally it will just have # symbols unless you are using the 'saved' option.

If Ubuntu is working and you have a reliable  Internet connection, you can always restore the original settings by purging and reinstalling Grub (grub-pc). It only takes a minute and as long as your Internet connection doesn't fail is pretty safe to do. Of course, if you have tweaked your settings they would return to default.

---

### Post by dino99 on 2012-03-31
> **drs305 said:**
> you can always restore the original settings by purging and reinstalling Grub (grub-pc). It only takes a minute 

+1 and no need a so big sledge-hammer :) to do it

---

### Post by zika on 2012-03-31
> **drs305 said:**
> It could be that your system is generating a 'recordfail' event that forces Grub to stop at the Grub menu and await a selection. 

Normally this event is triggered by a failed boot, but there are a variety of things that can trigger such behavior. You can check the contents of the 'marker file', /boot/grub/grubenv to see if anything is written there:
```
cat /boot/grub/grubenv
```Normally it will just have # symbols unless you are using the 'saved' option.

If Ubuntu is working and you have a reliable  Internet connection, you can always restore the original settings by purging and reinstalling Grub (grub-pc). It only takes a minute and as long as your Internet connection doesn't fail is pretty safe to do. Of course, if you have tweaked your settings they would return to default.I am aware of recordfail and there are some suspicious entries in (new9 grub files about it... It is set to 1 as default in files in /etc/grub.d and I will investigate that more thoroughly when spare time occurs. File grubenv has been checked several times. I even have an alias for all that... I know ho it should look like since I've been using that trick for (now) years...
Once I have enough spare time to be sure I can repair possible damage I will do it... ;)
But, even though, I want to see what went wrong...

Update: On this machine:
1. rsyslog was stopped: I've restored it...
2. prelink was active: I've purged it (before that I've restored files to previous state)
Timeout now works. One of these two was a culprit... ;)

Update: No, neither rsyslog or prelink were to blame. It seems that (kernel) 3.3-daily (last day) and (now) 3.4-daily are having some issues with shutdown (again) and that messes up with Grub. It does not make grubenv to have recordfail but it is written somewhere else... Still searching...

---

