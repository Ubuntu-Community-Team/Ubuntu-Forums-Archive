---
title: "Need Help Now!!!"
date: 2009-01-02
forum: Security
---

### Post by unf4b1x on 2009-01-02
Even if linux is secure can a pc become compromised using the browser? or bittorrent? Coz I'm using firefox 3 and I have the showip extension and there were 4 tabs opened and I could see that the one ip that showed at the terminal while using **netstat -tap** is neither of them. Shouldn't it supposed to show the sites IPs that I opened instead of just 1 ip? If you're using a bittorrent application, can somebody gain access from the outside using the bittorrent port? Or while you are using a bittorrent application?

Usually, I don't opened the firestarter gui coz that was what some people here are saying but yesterday I tried opening it just so to see what was going on. Then now, I saw that there were several IPs who seemed to be scanning my box sequentially from port 44444 to 44473 using the icmp protocol with an unknown service but mostly came from one IP. I was so alarmed so I closed the browser immediately. What is going on? Can somebody please tell me what to do next? Well, I already installed chkrootkit, clamtk, and rkhunter?! What else do I need?

---

### Post by CLomax on 2009-01-02
For the first two questions. Yes and yes. See this: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

ClamTK only finds Windows viruses. You really don't need to worry about Linux viruses.

Chkrootkit and rkhunter do the same thing, only one is needed.

---

### Post by cdenley on 2009-01-02
If you have a port forwarded to your computer (or you don't use a router or firewall), and you have software listening on that port, and if the attacker can use that software to perform malicious actions because of a security vulnerability, then someone can gain access. Every time you open a connection over the internet, your security relies on the program making/allowing the connection regardless of what OS you're running.

If you are concerned about netstat output, I suggest you post it. It's probably an RSS feed or an update server or something. Somone running a port scan on your computer isn't really cause for concern. It does demonstrate why you should be careful what applications you allow to listen for connections.

---

### Post by hyper_ch on 2009-01-02
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.
__________________

---

### Post by unf4b1x on 2009-01-02
> **hyper_ch said:**
> It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.
__________________

Thanks for reminding me and sorry I wasn't able to think a better descriptive title because at the time all I could think of is how to get help immediately.  I'll try to remember the next time. ;)

---

