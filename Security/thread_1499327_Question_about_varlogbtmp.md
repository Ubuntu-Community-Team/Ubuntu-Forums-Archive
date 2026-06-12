---
title: "Question about /var/log/btmp"
date: 2010-06-01
forum: Security
---

### Post by styxcoverbnd on 2010-06-01
I opened the gui for log viewer today and received an error stating: /var/log/btmp You don't have enough permissions to read this file. 

After doing some research I see that the btmp file logs bad login attempts. I'm the only user setup on this particular machine and I do not have ssh,samba or any server type programs installed (actually my install is very basic). The btmp file has a size of 0, if I (personally) haven't had any failed login attempts what would create btmp file? Is this something to be worried about?

---

### Post by kampman on 2010-06-01
Mine is the same way on 9.10. Not sure what that log file is for but I don't think it's anything to worry about.

If you really want to look at it through the log file viewer, you can run "gksudo gnome-system-log" which will open the log viewer program as the root user so you can see any log files that you don't normally have permissions to view.

btmp will of course show up blank though since it's 0 bytes.

---

### Post by cariboo on 2010-06-01
Btmp is where the last bad login attempts are stored, it is not meant to be read as a normal log file. To read it, open a terminal and type:

```
sudo lastb
```

If there haven't been any bad login attempts the file will look something like this:

```
 sudo lastb
[sudo] password for me: 

btmp begins Tue Jun  1 08:19:42 2010
```

---

### Post by cdenley on 2010-06-02
[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/374320](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/374320)

---

### Post by styxcoverbnd on 2010-06-02
Thanks for the help/info guys. I'll marked this as solved

---

### Post by BobSands on 2010-06-09
Hey!,
Works fine for me too.

Thanks!!!

---

### Post by franciskyong on 2010-07-27
Typed in : sudo last -f /var/log/btmp and got this result:  

```
kyeu@kyeu-laptop:~$ sudo last -f /var/log/btmp 
[sudo] password for kyeu:  

kyeu     tty7         :0               Sun Jul 25 06:17   still logged in    
kyeu     tty7         :0               Fri Jul 23 05:42 - 06:17 (2+00:34)    
kyeu     tty7         :0               Thu Jul 15 09:30 - 05:42 (7+20:12)    
kyeu     tty7         :0               Tue Jul 13 23:27 - 09:30 (1+10:02)    
kyeu     tty7         :0               Sun Jul 11 19:38 - 23:27 (2+03:49)    
kyeu     tty7         :0               Sat Jul 10 05:14 - 19:38 (1+14:23)    
kyeu     tty7         :0               Wed Jul  7 19:23 - 05:14 (2+09:51)    
kyeu     tty7         :0               Fri Jul  2 06:57 - 19:23 (5+12:25)
btmp begins Fri Jul  2 06:57:54 2010 
kyeu@kyeu-laptop:~$
```   
Am I in trouble ? Somebody help !

---

### Post by cariboo on 2010-07-27
Theres nothing wrong there, what makes you think you have a problem?

---

### Post by franciskyong on 2010-07-27
Thank you Cariboo907, I was just concerned about the top line which read " still logged in " and if thats ok.

---

### Post by cariboo on 2010-07-27
From the looks of it you logged on, on the 25th, and haven't rebooted or logged out since then.

---

### Post by cdenley on 2010-07-28
> **franciskyong said:**
> Thank you Cariboo907, I was just concerned about the top line which read " still logged in " and if thats ok.

Of course you were still logged in! How would you run that command if you weren't?

---

### Post by franciskyong on 2010-07-28
Precisely, although I've shut down several times the last four days it's &quot;still logged in&quot;. Also tried logging off without shutting down, status quo remains unchanged !

---

### Post by franciskyong on 2010-07-28
Er, but still logged in since July 25,2010 ?

---

### Post by cariboo on 2010-07-29
Whats the problem, have you rebooted since posting? It's July 28, 2010 today.

---

### Post by franciskyong on 2010-07-29
Yes I've rebooted and yet ( till yesterday Jul 29 ) after each reboot it was "still logged in" since Jul 25  I've  re-installed Ubuntu and  problem's solved!. Thanks once again guys.

---

### Post by cariboo on 2010-07-29
It's to bad you reinstalled, it would have been nice to know what was causing the problem, you don't have auto login enabled by any chance?

---

### Post by franciskyong on 2010-07-31
Can't tell if I had enabled auto login, but now the log just shows the last login

---

