---
title: "How Do You Learn To Read Log Files?"
date: 2011-04-30
forum: Security
---

### Post by TheNewbieGeek on 2011-04-30
I am gonna read them everyday and get a feel if something is out of the ordinary but that's the only idea I have....also I am using logwatch to help...if there is a easier way please let me know...thanks for the replies.

---

### Post by simonplexus on 2011-04-30
package hints: tripwire and snort

---

### Post by TheNewbieGeek on 2011-04-30
I know what trip wire is I want to read the log files...answer the question next time.

---

### Post by Rubi1200 on 2011-05-02
I don't think there is an easy way to do it. In general, the logs to watch are messages, auth.log, syslog, dmesg.

For more information see here:
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

What you could do to learn more about what is going on is either or both of the following ideas:

Open a terminal and run, for example, tail -F /var/log/auth.log then run a few things, maybe even open another terminal and run something as root and watch "live" as things are added to the log.

Another thing to do is grep the logs looking for certain things. This site has some information that might be useful:
[http://beginlinux.com/sec_train_m/sec_secure/777-logschecks](http://beginlinux.com/sec_train_m/sec_secure/777-logschecks)

---

### Post by jramshu on 2011-05-02
An easy way to view failed login attempts, for me anyway.

```
grep 'Failed' /var/log/auth.log | more
```

---

### Post by jramshu on 2011-05-02
> **Rubi1200 said:**
> 

Open a terminal and run, for example, tail -F /var/log/auth.log then run a few things, maybe even open another terminal and run something as root and watch "live" as things are added to the log.

This is definitely a noob question, but how do you stop the "live" feed? I used this and couldn't get it to stop. 

Thanks in advance.

---

### Post by Rubi1200 on 2011-05-02
> **jramshu said:**
> This is definitely a noob question, but how do you stop the "live" feed? I used this and couldn't get it to stop. 

Thanks in advance.
Use "Ctrl" + "C" to return to the prompt.

---

### Post by tgm4883 on 2011-05-02
> **TheNewbieGeek said:**
> I know what trip wire is I want to read the log files...answer the question next time.

You catch more flies with honey instead of vinegar.

Most log files are pretty easy to read as they are just text.

For the reading part, I learned that in Kindergarten/First grade.

For the text part, I use tail, cat, or gedit.

---

### Post by bodhi.zazen on 2011-05-02
It sounds like a circular argument, but, the only way to learn to read the logs is to read them.

That is the only way to get a sense of what is "normal".

This is why people use tools such a snort. Snort is a NIDS and will watch of activity you should pay attention to.

---

