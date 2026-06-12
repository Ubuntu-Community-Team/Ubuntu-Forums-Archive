---
title: "Anonymous user on my system . . ."
date: 2008-10-16
forum: Server Platforms
---

### Post by siloko on 2008-10-16
Hello,

I have a strange anomaly between the users logged in (usually just me) and that reported by the system, heres some output:

** Notice 2 Users reported by uptime **

siloko@mango:/$ uptime
 22:30:04 up 22 days, 14:23,  2 users,  load average: 0.00, 0.00, 0.00

** but only one listed by who **

siloko@mango:/$ who
siloko pts/1        2008-10-16 22:27 (192.168.0.3)

** w combines both observations - showing me logged in over ssh **  

siloko@mango:/$ w
 22:35:51 up 22 days, 14:29,  2 users,  load average: 0.00, 0.00, 0.00
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
siloko pts/1    192.168.0.3          22:27    0.00s  0.30s  0.02s sshd: siloko [priv]

** users shows just me **

siloko@mango:/$ users
siloko

** last shows only one person logged currently logged in **

siloko@mango:/$ last -10
siloko pts/1        caspian          Thu Oct 16 22:27   still logged in   
siloko pts/1        caspian          Thu Oct 16 18:46 - 19:12  (00:25)    
siloko pts/1        haempc34.medschl Thu Oct 16 11:44 - 17:26  (05:42)    
siloko pts/1        caspian          Thu Oct 16 07:26 - 07:51  (00:25)    
siloko pts/1        caspian          Wed Oct 15 23:08 - 00:02  (00:53)    
siloko pts/1        caspian          Wed Oct 15 22:57 - 23:08  (00:11)    
root     tty1                          Wed Oct 15 22:55 - 22:58  (00:03)    
root     tty1                          Wed Oct 15 22:55 - 22:55  (00:00)    
siloko pts/1        caspian          Wed Oct 15 21:56 - 22:53  (00:57)    
siloko pts/1        haempc34.medschl Wed Oct 15 13:13 - 14:02  (00:49)   


Ok so the point is there is nowhere on my system I can find evidence of a second user. I'm pretty sure I haven't been hacked - quite a secure setup, diligent at checking my logs, no evidence of hacking (no password changes, no spurious connections to the outside world etc etc). I also have no X session running.

What's even stranger is if I logout of my ssh session and login to the actual box it shows just one user as expected. Then if I login as another user over ssh who/w/uptime show two users again this is to be expected. However if I then logout of the box (keeping the ssh session) 'w' still reports 2 users in the uptime line, but only lists one as shown in the output above. 

I would really like some help getting to the bottom of this . . .

Any insights gratefully received

Cheers

S

---

### Post by lykwydchykyn on 2008-10-16
Might want to run chkrootkit and rkhunter just to be sure, but it could just be a bug.

---

### Post by Sef on 2008-10-16
> ** Notice 2 Users reported by uptime **

siloko@mango:/$ uptime
 22:30:04 up 22 days, 14:23,  2 users,  load average: 0.00, 0.00, 0.00

** but only one listed by who **

Type in 'users' (without quotes) and see what names come up.

---

### Post by p_quarles on 2008-10-17
> **lykwydchykyn said:**
> Might want to run chkrootkit and rkhunter just to be sure, but it could just be a bug.
Or neither. For one thing, a rootkit that shows a logged in user would be a shameful piece of work. Think about it -- the bad guy has complete control over someone's computer, and they don't bother to hide that fact from every day system monitoring utilities? 

As for it being a "bug," there's no reason to think that. If you have any, feel free to provide them.

To get a more complete view of who/what is logged it to various TTYs and PTSs, run the following:
```
who -dlaH
```
You'll see that there's a lot more going on in your system than you probably realized, and it's nothing to worry about.

---

### Post by siloko on 2008-10-17
Hello,

> **Sef said:**
> Type in 'users' (without quotes) and see what names come up.

already done . . .

** users shows just me **

siloko@mango:/$ users
siloko

Both chkrootkit and tkhunter come up black. Other things to mention, I only allow ssh connections on an unprivileged port, and only by one user who is in group of his own without any permissions (meaning you need to su once logged in to actually do anything on my system).

Still slightly confused . . . .


S

---

### Post by siloko on 2008-10-17
Hello,

> To get a more complete view of who/what is logged it to various TTYs and PTSs, run the following:
```
who -dlaH
```
You'll see that there's a lot more going on in your system than you probably realized, and it's nothing to worry about.

```

root@mango:/# who -dlaH
NAME       LINE         TIME             IDLE          PID COMMENT  EXIT
           system boot  2008-09-24 08:06
           run-level 2  2008-09-24 08:06                   last=
LOGIN      tty4         2008-09-24 08:06              4292 id=4
LOGIN      tty5         2008-09-24 08:06              4293 id=5
LOGIN      tty2         2008-09-24 08:06              4297 id=2
LOGIN      tty3         2008-09-24 08:06              4298 id=3
LOGIN      tty6         2008-09-24 08:06              4301 id=6
           pts/0        2008-10-13 18:22              6657 id=ts/0  term=0 exit=0
LOGIN      tty1         2008-09-24 08:27              5296 id=1
siloko +   pts/1        2008-10-17 06:51   .         12985 (caspian)
LOGIN      tty1         2008-09-24 21:06              6655 id=1
           pts/2        2008-10-14 23:37              9830 id=ts/2  term=0 exit=0
LOGIN      tty1         2008-10-15 22:58             11509 id=1

```

Does this expain the 2 users !?

Cheers

S

---

### Post by p_quarles on 2008-10-17
The discrepancies have to do with how different applications count users. In fact, there are many accounts using your system at any time -- beyond human users, you have a number of system users that are responsible for owning processes such as SSHD or CUPS. The uptime command may be doing something like counting the SSH server as a user (since the one human user is logged in via SSH). 

Determining exactly what it's counting would take some research, but this is definitely no cause for worry.

---

### Post by cariboo on 2008-10-17
You are logged into the server twice, probably once when you booted up and another time when you accessed the server remotely. From your posting your server is named mango and you are accessing the server from caspian.

Jim

---

### Post by siloko on 2008-10-17
> **cariboo907 said:**
> You are logged into the server twice, probably once when you booted up and another time when you accessed the server remotely. From your posting your server is named mango and you are accessing the server from caspian.


Hello,

The thing is I am not actually logged into the server (other than through ssh), it has just booted up with the login screen awating input . . .

But yes the server is mango and my ssh client is on caspian . . .

Like I say this is not a worry as such I was just seeking to understand what was going on - other server's I have logged in to have always had a correlation  between the users stated in uptime and those listed by who . . . but this is not the case for mango!

Cheers

S

---

### Post by lykwydchykyn on 2008-10-17
> **p_quarles said:**
> Or neither. For one thing, a rootkit that shows a logged in user would be a shameful piece of work. Think about it -- the bad guy has complete control over someone's computer, and they don't bother to hide that fact from every day system monitoring utilities? 

As for it being a "bug," there's no reason to think that. If you have any, feel free to provide them.

Whoa there partner, how about not tearing into me for trying to help someone.  Are you saying it's a bad suggestion to scan for a rootkit when you see anomalies on a system?  

Sorry for suggesting that it might be a bug.  Didn't realize that required pages of documented proof.

---

