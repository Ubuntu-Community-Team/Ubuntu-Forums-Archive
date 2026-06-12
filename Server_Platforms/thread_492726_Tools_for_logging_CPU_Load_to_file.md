---
title: "Tools for logging CPU Load to file?"
date: 2007-07-05
forum: Server Platforms
---

### Post by yellowtip on 2007-07-05
Hi,

We are experiencing some server load issues with a large software implementation.

To try and isolate when this load issue occurs, we would like to be able to log the CPU Load Average statistics from top (we use htop) to a log file. Like this we can put them into xls and make some charts of what happens when testing some routines in the software.

My question is:
Are there any tools that can do this for us?

Thanks in advance!

---

### Post by PaulFr on 2007-07-05
I've used ```
top -b > some_log_file
``` and Ctrl-C to stop logging. See man page of top if you want to customize the output.

---

### Post by yellowtip on 2007-07-05
Thank you very much for your quick reply. 

This is progress! As I can now get dumps of each top screen update into a txt file. However, this would be information overkill, and I fear it would also affect performance.

I read through the Man page, but can't find any parameters of how to log the following to a log file:

<date>;<time>;<Current Load Average>;< %CPU >

Like this I get a very simple CSV table that I can feed into Excel for analysis.

I can't believe I'm the only person that has ever tried doing this. There must be some tools or commands that allow me to do this.

Anybody? :confused:

---

### Post by dfreer on 2007-07-05
I believe you could use the top command along with some clever grep pipes.
Lemme play around with it (I'm not so good with grep) and I'll get back to you on logging the info you want into a file.

Also, other than the log file size I don't see top using very much system resources at all. The only thing would be to create a cron job to start/stop it so you don't have to keep the terminal open and kill it manually, but that's fluff I guess.

---

### Post by dfreer on 2007-07-05
Ok, so this will get you a running tally, although I can't seem to get it into an file:
```
top -b | grep -2 "load average"
```
So what you could do is schedule a cron job or whatever to run this next command as often as you like (say once every minute), and it will append the results to a log file. From there, you can grep it a bit more to create your excel chart/thingie.
```
top -b | head | grep -2 "load average" >> loadaverage.log
```
The main reason I used head, is that it will let the top command run only once, allowing for cron to handle how often you want to check the load average. Also, I couldn't get it to output to a file any other way.

I know the above poster already had it logging to a file, but it was creating too much information too quickly IMO, resulting in a large file if left unchecked.

---

### Post by yellowtip on 2007-07-05
> **dfreer said:**
> I believe you could use the top command along with some clever grep pipes.
Lemme play around with it (I'm not so good with grep) and I'll get back to you on logging the info you want into a file.

Also, other than the log file size I don't see top using very much system resources at all. The only thing would be to create a cron job to start/stop it so you don't have to keep the terminal open and kill it manually, but that's fluff I guess.

Thanks for the reply.

I have solved it in the following way:
I added to the cron (cron -e) the following line:
* * * * * uptime >> /var/log/load_avg

This writes the following info to a log file:
11:00:33 up 50 days, 44 min, 34 users, load average: 0.35, 0.37, 0.35  

Good enough for me ;)

Thanks everybody for your help!

---

### Post by PaulFr on 2007-07-05
If you only need system load, then you do not need top or htop. A simpler solution would be to run the command  ```
while :; do uptime; sleep 100; done > log_file
``` in a terminal. This runs the **uptime** command to get the system load, then runs the **sleep 100** to sleep for 100 seconds, then repeats till you kill it with Ctrl-C in that terminal. (The command assumes bash).

---

### Post by yellowtip on 2007-07-05
> **PaulFr said:**
> If you only need system load, then you do not need top or htop. A simpler solution would be to run the command  ```
while :; do uptime; sleep 100; done > log_file
``` in a terminal. This runs the **uptime** command to get the system load, then runs the **sleep 100** to sleep for 100 seconds, then repeats till you kill it with Ctrl-C in that terminal. (The command assumes bash).

Kewl! That means I can do it on demand too. Thanks!

---

### Post by Mr. C. on 2007-07-06
I believe **sar** is available and is always maintaining statistics.  Try:

```
sudo sar
```

for starts and **man sar** for more details.

MrC

---

