---
title: "Mdadm periodic redundancy checks"
date: 2011-12-04
forum: Server Platforms
---

### Post by speed32219 on 2011-12-04
It seems mdadm schedules periodic redundancy checks of MD devices.

Every now and then, when I would observe it by the lights on my external hd array flashing, I would check to find mdadm running a check.

[=========>...........]  check = 45.3% (664706816/1465138496) finish=403.6min speed=33049K/sec

Not a resync or recovery from a failure but a check.  Searching I found that there is a cronjob that starts the first Sunday of every month that executes this redundancy check.  This is a video server that I write to and rarely remove files, I usually grow the array and I also use lvm2. 

Do I really need this, or at least schedule it for a 90-180 check.  I also found that fsck runs also, as I do shut the system down at least once a week for a couple of days while working, to save on power usage. I increased the values I believe on how often fsck runs after shutdown/reboots and haven't seen that run for a while.  Plus it was easy to spot when I truned on the server. DO I even need to run a fsck on a raid5 array?

During these checks, i have found that I am losing some video files (from 5-10 iso's 4-5GB sizes) that I was having no problems with as far as viewing they jsut disappear but the meta data remains. 

I do recover by loading the dvd and ripping it again, but it's a PIA to find the dvd in my library. (Not as organized as my video server, which is why I have a video server) Not to metnion I do not know where the file is put on the raid5. (Using space freed from loss of file to begin with) 

Also, when I run df -h even after losing 32GB of video files, it still displays available free space as if the files were still there. 

Here is the cronjob that chacks the first Sunday of the month.  What could I replace it with so it is only done every six months?

Or do I even need it, if I were having a problem wouldn't it just report an error and remove the drive from the array?

cat /etc/cron.d/mdadm

# By default, run at 01:06 on every Sunday, but do nothing unless the day of
# the month is less than or equal to 7. Thus, only run on the first Sunday of
# each month. crontab(5) sucks, unfortunately, in this regard; therefore this
# hack (see #380425).
6 1 * * 0 root [ -x /usr/share/mdadm/checkarray ] && [ $(date +\%d) -le 7 ] && /usr/share/mdadm/checkarray --cron --a
ll --quiet

---

### Post by CharlesA on 2011-12-04
I have a similar thing that runs on my RAID array. It's set to do a "verify" every 28th of the month. It takes around 12+ hours to complete, but I find it invaluable as it has found some bad sectors on the drives in the array.

That's strange that you are losing files during this check. I don't use mdadm, but maybe someone else can help you out?

---

### Post by rubylaser on 2011-12-04
You should not be losing files durning an mdadm check unless there is problems with the media.  Have you run smart tests, and checked the logfiles after the check runs?  Personally, I leave the check in place.  It's just one extra check that could potentially shed light on a problem before it becomes a real problem.

---

### Post by ian dobson on 2011-12-04
Hi,

You shouldn't lose files during a check. My main RAID5 array (5 2Tb drives) has never lost a file during th check.

If you find the check speed/IO bandwidth used is effecting your work flow you can adjust the min/max bandwith used by writing to the following files:-
echo 10000 > /proc/sys/dev/raid/speed_limit_min
echo 200000 > /proc/sys/dev/raid/speed_limit_max


Regards
Ian Dobson

---

### Post by speed32219 on 2011-12-05
Thank you for all your answers.  I do not know if losing the files were actually from a mdadm check, fsck, or something to do with lvm2.  I am interested in the verify feature though.  I am going to look into that instead of the checking that mdadm does.

I am going to try and narrow down why I am losing files though.

---

