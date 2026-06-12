---
title: "what does my hda5 do ? (also info needed about partions)"
date: 2007-01-02
forum: The Cafe
---

### Post by Gargamella on 2007-01-02
I didn't remember how I did when I installed Dapper...really i don't

anyway I think I made a Root (/) and a HOME  (/home) partition...

I have a 9,8 GB partition called hda5 (you can see the screenshot) I don't use

only lost+found folder in it...

I know I may seem an idiot...however someone can explain me about it?

---

### Post by linuchsan on 2007-01-02
try df -h in a console, than you can see the mount points

---

### Post by Gargamella on 2007-01-02
andrea@andrea-laptop:~$ df -h
Filesystem            Dimens. Usati Disp. Uso% Montato su
/dev/hda6              64G   27G   34G  45% /
varrun                248M  152K  248M   1% /var/run
varlock               248M  4,0K  248M   1% /var/lock
udev                  248M  132K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   19M  230M   8% /lib/modules/2.6.15-27-686/volatile
/dev/hda5             9,7G  129M  9,0G   2% /media/hda5

---

### Post by linuchsan on 2007-01-02
try df -hT so you can see the hda5 fs, must be a fat32 or ntfs partition.
Can't see a /home

---

### Post by Gargamella on 2007-01-02
I will soon pass to edgy...with about 80GB HD (laptop)
How do you think I gotta partion it?

---

### Post by linuchsan on 2007-01-02
It depends if you like windows installed aswell.

---

### Post by Gargamella on 2007-01-02
nono, I am totally Ubuntu (sorry  I didn't tell ya)

---

### Post by linuchsan on 2007-01-02
swap must be on the first partition (faster access when the memory is full, maybe 2 gig)
/ (root system, lets say 12 gig)
and
/home (for users, desktop and data, the remaining space)

---

### Post by Gargamella on 2007-01-02
ok thank you.. ;D

but let me know...
how much important is swap?

---

### Post by linuchsan on 2007-01-02
just google about swap and virtual memory, than you know.

Good luck

---

