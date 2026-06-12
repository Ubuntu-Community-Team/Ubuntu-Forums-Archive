---
title: "sar, output to csv in one line?"
date: 2009-02-02
forum: Server Platforms
---

### Post by shebangs on 2009-02-02
I'm trying to do the equivalent of "sar -d -u -w 1 1"  then using tr, outputting it as a CSV.  So I can have a single csv file I can tail/process to get data.

The problem I am having is that It's outputting it in the following:

```

# sar -d -u -w 1 1 | grep -v Average | grep -v Linux | tr -s ' ' ','

12:58:56,AM,cswch/s
12:58:57,AM,24.00

12:58:56,AM,CPU,%user,%nice,%system,%iowait,%steal,%idle
12:58:57,AM,all,0.00,0.00,0.00,0.00,0.00,100.00

12:58:56,AM,DEV,tps,rd_sec/s,wr_sec/s,avgrq-sz,avgqu-sz,await,svctm,%util
12:58:57,AM,dev8-0,0.00,0.00,0.00,0.00,0.00,0.00,0.00,0.00



```

How can I convert it so it's all in one line?

```

*# sar -d -u -w 1 1 | grep -v Average | grep -v Linux | tr -s ' ' ','* 

12:58:56,AM,cswch/s,CPU,%user,%nice,%system,%iowait,%steal,%idle,DEV,tps,rd_sec/s,wr_sec/s,avgrq-sz,avgqu-sz,await,svctm,%util
12:58:57,AM,24.00,all,0.00,0.00,0.00,0.00,0.00,100.00,dev8-0,0.00,0.00,0.00,0.00,0.00,0.00,0.00,0.00

```

Thanks!!

---

### Post by friendyboy on 2009-05-08
Hi shebangs
I also have similar problem.did you get any solution for your problem?If so please post ur work around.or mail me : [EMAIL="friendyboy@gmail.com"]friendyboy@gmail.com[/EMAIL]

---

### Post by microthorne on 2011-01-13
Nevermind.

---

### Post by rubylaser on 2011-01-13
I'm not sure I understand what you want, but why don't you remove newlines?
```
sar -d -u -w 1 1 | grep -v Average | grep -v Linux | tr -s ' ' ',' | tr -d '\n'
```

That won't work especially on multicore boxes.  You'll probably want to write a script to get the output, then parse the pieces with cut, and then echo them back in the proper order to your csv file.

---

