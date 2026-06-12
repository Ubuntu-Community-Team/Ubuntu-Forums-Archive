---
title: "High Load when access to CIFS Mount"
date: 2013-08-01
forum: Server Platforms
---

### Post by luca2 on 2013-08-01
Hi, i would like to know what could be the problem if i've High Load when access to CIFS mount on my Ubuntu 12.04(kernel 3.9.0).
It's on ESXI 5, Q9400 and 4gb of RAM.

This is what happen:

[IMG]http://img838.imageshack.us/img838/8194/9bdm.png[/IMG]

When system executes these cron:

16.00-> [COLOR=#666699][FONT=Lucida Sans Unicode]rsync -avz /home/www_BK.tgz /mnt/WHSNAS2011/mycloudData/personal/Leen15/varie/BACKUP_UBUWEBSERVER.tgz 2>&1 >> /var/log/sync_bk_to_Winserver.log[/FONT][/COLOR]

16.30 -> [COLOR=#666699][FONT=Lucida Sans Unicode]rsync -avz /home/www_BK.tgz /mnt/ububackup/BACKUP_SITO_UBUNTU 2>&1 >> /var/log/backupUbu.log[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]
[FONT=Verdana]These mount are 2 different servers (Windows server 2012 the first, ubuntu NAS the second) in Gigabit LAN, the tgz is a file of about 530mb.

During the execution, CPU stays always below 10%.

I've also high load problem when the system tries to read large file (1-2GB) from the first mount for cloud downloading (ajaxplorer). 

Do you have some idea?

Maybe CIFS is not the best solution for this kind of jobs?

Thanks a lot.
[/FONT]

[FONT=Verdana]





[/FONT]

[/FONT][/COLOR]

---

### Post by tgalati4 on 2013-08-01
What is the load if you rsync the same file to a local disk?  The Q9400 is a quad core processor, so presumably 100% of the loaded cores will give you a load of 4.0 (4 x 1.0 or 100% for each CPU core).  So a load of 6 is not really high if there are other things going on, which on a server is probably the case.  What does *htop* look like when you perform the remote rsync?

---

### Post by luca2 on 2013-08-02
> **tgalati4 said:**
> What is the load if you rsync the same file to a local disk?  The Q9400 is a quad core processor, so presumably 100% of the loaded cores will give you a load of 4.0 (4 x 1.0 or 100% for each CPU core).  So a load of 6 is not really high if there are other things going on, which on a server is probably the case.  What does *htop* look like when you perform the remote rsync?


The situation is very strange.

First, today i found my VM at 2.0 of load, with nothing of special that was running.

So, this is the situation that i found:

[IMG]http://img708.imageshack.us/img708/356/ups0.png[/IMG]

I tried to run the remote rsync, and the load didn't go so high:

[IMG]http://img841.imageshack.us/img841/1600/dbl5.png[/IMG]

after this, i rebooted the VM and the load went down:

[IMG]http://img11.imageshack.us/img11/9905/u0lk.png[/IMG]

So, another try to remote rsync:

[IMG]http://img401.imageshack.us/img401/489/3led.png[/IMG]

the load is not high as expected. I don't understand.. :(

This is the last one test, rsync on local disk:

[IMG]http://img203.imageshack.us/img203/7755/di3z.png[/IMG]

My problem is when rsync is running, apache and mysql don't work as expected, and sometime one of them crash.

Is there a possibility to give a low priority to rsync so apache and mysql can work without problems?

Thanks

---

### Post by luca2 on 2013-08-02
After some search and tests, i found that i can replace rsync cron with:

ionice -c 3 nice -n 10 cp /FROM_FILE.tgz /TO_FILE.tgz --remove-destination

So with this i decreased the CPU and IO priority. From a couple of test, with this command the system doesn't go upper to 2.0 of load.

I'll keep monitoring the system for next days and see if the problem is solved! :)

---

### Post by tgalati4 on 2013-08-02
I was going to suggest* ionice*, but you already found it.  The purpose for running rsync locally is to isolate local IO performance through the VM versus remote IO.  

*Htop* is pretty, but *top* is another tool to use.  It provides the percentage of *nice* jobs (ni) and the percentage of IOWAITS (wa) which will also give you a clue as to the performance bottlenecks.

Some of these tools may not give accurate readings when running under a VM, as you have discovered.  So you have to look at performance from both inside the VM and at the dom0 (host OS) level to see where the bottlenecks are happening.  It's also helpful to have a bare-metal installation of your guest OS so you can compare bare-metal throughput versus running as a VM.

---

