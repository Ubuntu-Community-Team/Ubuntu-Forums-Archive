---
title: "help for restart in 2 different time"
date: 2013-01-18
forum: Server Platforms
---

### Post by bario22 on 2013-01-18
hi.
i have ubuntu 12.o4
is it possible to restart server in 2 different time (7oclock and 15h00)
thanks

---

### Post by SeijiSensei on 2013-01-18
Edit, as root with sudo, the file /etc/crontab and add these two lines:

```

0  7 * * * root /sbin/shutdown -r now
0 15 * * * root /sbin/shutdown -r now

```

---

### Post by bario22 on 2013-01-18
thanks

---

### Post by bario22 on 2013-01-20
good morning,
0  7 * * * root /sbin/shutdown -r now
0 15 * * * root /sbin/shutdown -r now
is it possible change now to +5
doest it make any difference ?
because my server restart only at 3 oclock but not at 7.00h

---

### Post by sudodus on 2013-01-20
> **bario22 said:**
> good morning,
0  7 * * * root /sbin/shutdown -r now
0 15 * * * root /sbin/shutdown -r now
is it possible change now to +5
doest it make any difference ?
because my server restart only at 3 oclock but not at 7.00h
```
0  7 * * * root /sbin/shutdown -r +5
```
should do the same as
```
5  7 * * * root /sbin/shutdown -r now
```
Is your computer busy with something else at 7 o'clock in the morning? And will that task finish before 7.05?

---

### Post by bario22 on 2013-01-20
no my computer is not busy with nothing, just want make sur that it will restart with the folowing command:
0  7 * * * root /sbin/shutdown -r now
0 15 * * * root /sbin/shutdown -r now
so im surprise that it restart only at 15.00h but not at 7.ooh

---

### Post by sudodus on 2013-01-20
> **bario22 said:**
> no my computer is not busy with nothing, just want make sur that it will restart with the folowing command:
0  7 * * * root /sbin/shutdown -r now
0 15 * * * root /sbin/shutdown -r now
so im surprise that it restart only at 15.00h but not at 7.ooh
I'm surprised too.

Are you sure that it did not reboot? Maybe it did, but you did not notice it (because you did not babysit the computer in the morning). Can you see from the logs, that it did not reboot?

---

### Post by Lars Noodén on 2013-01-20
Keeping the +5 might be nice, especially if you happen to be logged in when it should reboot and you want to have time to cancel the reboot order.  Using 'now' won't give you the chance.

---

### Post by sudodus on 2013-01-20
> **lars noodén said:**
> keeping the +5 might be nice, especially if you happen to be logged in when it should reboot and you want to have time to cancel the reboot order.  Using 'now' won't give you the chance.
+5 ;-)

---

### Post by bario22 on 2013-01-20
> **sudodus said:**
> I'm surprised too.
 
Are you sure that it did not reboot? Maybe it did, but you did not notice it (because you did not babysit the computer in the morning). Can you see from the logs, that it did not reboot?
 the server didnt reboot at 15h00 im home and waiting but nothing happened.
i use comand:  sudo nano /etc/rc.local
before i use:  shutdown -r +540 without problem
now the 2 comand:
0  7 * * * root /sbin/shutdown -r now
0 15 * * * root /sbin/shutdown -r now 
dont work

---

### Post by sudodus on 2013-01-20
Did your system ever reboot by ***cron***, or only from the terminal command (with root privileges)?
```
shutdown -r +540
``` 

Did you edit [FONT="Courier New"][SIZE="3"]/etc/crontab[/SIZE][/FONT] as suggested by SeijiSensei or [FONT="Courier New"][SIZE="3"]/etc/rc.local[/SIZE][/FONT] as in post #10?

Did you reboot the computer after editing the file?

---

### Post by bario22 on 2013-01-20
> **sudodus said:**
> Did your system ever reboot by ***cron***, or only from the terminal command (with root privileges)?
```
shutdown -r +540
``` 
 
Did you edit [FONT=Courier New][SIZE=3]/etc/crontab[/SIZE][/FONT] as suggested by SeijiSensei or [FONT=Courier New][SIZE=3]/etc/rc.local[/SIZE][/FONT] as in post #10?
 
Did you reboot the computer after editing the file?
[FONT=Courier New]etc/rc.local[/FONT] as in post #10
i didnt reboot after editing the file

---

### Post by sudodus on 2013-01-20
> **bario22 said:**
> [FONT=Courier New]etc/rc.local[/FONT] as in post #10
i didnt reboot after editing the file

That could be the problem. You should restore that file and do exactly what was suggested by SeijiSensei in post #2
and reboot.

---

### Post by bario22 on 2013-01-20
shoud i do leike that ?
sudo su
nano /etc/crontab
then add the comand..... and restart
sorry im new to linux :(

---

### Post by sudodus on 2013-01-20
> **bario22 said:**
> shoud i do leike that ?
sudo su
nano /etc/crontab
then add the comand..... and restart
sorry im new to linux :(

Run the command
```
sudo nano /etc/crontab
```
and add the command lines (cut and paste to avoid typing errors)
```
0  7 * * * root /sbin/shutdown -r now
0 15 * * * root /sbin/shutdown -r +5
```

Also restore [FONT="Courier New"][SIZE="3"]/etc/rc.local[/SIZE][/FONT] to its original content

Finally reboot!

Good luck :-)

---

### Post by bario22 on 2013-01-20
thanks all

---

