---
title: "How to use Firejail with Tor browser ?"
date: 2020-03-28
forum: Security
---

### Post by linuxyogi on 2020-03-28
I have downloaded Tor browser & extracted it to /home/username/Downloads.

I want to launch Tor browser inside Firejail sandbox. 

How to use Firejail with Tor browser ?

---

### Post by EuclideanCoffee on 2020-03-28
Here are instructions on how to run any application from firejail.

[https://www.linux.com/topic/desktop/lock-your-untrusted-applications-firejail/](https://www.linux.com/topic/desktop/lock-your-untrusted-applications-firejail/)

> 
 Say, for example, you want to run Firefox within a Firejail. To do this, open up a terminal and issue the command *firejail firefox*.  When you run the application, you will see that Firejail has initiated  the child process and Firefox will open&#8212;running within its own sandbox (Figure 1). 


Oh to run binaries outside of /usr/bin/ (binaries inside of this folder allow you to simply write a "command" in the terminal), you will need to use the full path.

~/Downloads/**filename**

---

### Post by linuxyogi on 2020-03-28
> **EuclideanCoffee said:**
>  Oh to run binaries outside of /usr/bin/ (binaries inside of this folder allow you to simply write a "command" in the terminal), you will need to use the full path.

~/Downloads/**filename**



```
ls /home/username/Downloads/tor-browser_en-US/
Browser  start-tor-browser.desktop

```

When I double click **start-tor-browser.desktop **the Tor browser starts.

---

### Post by EuclideanCoffee on 2020-03-28
Firejail must be used in the terminal unless you install firetools in the link above.

---

