---
title: "System hang"
date: 2015-06-19
forum: Security
---

### Post by Jijimon on 2015-06-19
My Ubuntu desktop was hanging frequently, I found my 2 GB Ram was filled 100 % on that time and load also 100 % in the system monitor. I installed Clam tk app and detected around 30 threats and quarantined. The hanging problem stopped but the memory and cache shows around 2 GB. I have only less knowledge in computer. Please help me to solve the problems. I am posting the screen shot of the Clam tk window of threats.

---

### Post by tgalati4 on 2015-06-19
Welcome to the forums.  Do you have a swap file?  Open a terminal and post the output of:

```
free
```

Running anything in Wine takes a lot of RAM.  The firefox cache threats can be deleted and you should be using some javascript blockers such as noscript and adblock edge.

---

### Post by cariboo on 2015-06-19
What you see, are false positives. The way to check what is using all your resources is to open a terminal and type the following command:

```
top
```

the output should look something similar to this:

[[img]http://i.imgur.com/VDPuJeMm.png[/img]](http://imgur.com/VDPuJeM)

Look for high resource usage under %CPU and %MEM.

---

### Post by Jijimon on 2015-06-19
Thank you, wine was there, now I removed it, ad blocker is there. swap file is there 5 GB

---

### Post by Jijimon on 2015-06-19
result of top

---

### Post by tgalati4 on 2015-06-19
Your system looks normal.  What is your definition of "hanging".  If it is running slow, then install *htop* and watch it in another desktop when the slowdown happens.  When you start hitting swap, things will slow down quite a bit.

```
sudo apt-get install htop
htop
```

Control-C to quit *htop*.

---

### Post by Jijimon on 2015-06-19
Hanging means, Mouse pointer will move, no keyboard, mouse activity, only hard disk led blinking. some time screen colour will go and become light black.
  How I can delete the firefox cache threats?
 Using javascript blockers such as noscript and adblock edge is not reliable?  Should I remove that?
Any recommended, RAM clearing software or system optimising software there?
If you feel my system looks normal, no need to worry?
Thank you for the help.

---

### Post by Jijimon on 2015-06-19
ClamTk, ClamAV antivirus using gtk2-perl is good or not for me?

---

### Post by cariboo on 2015-06-19
If you are using Ubuntu, your system may not have enough resources to run it properly, from what you have described, that's what the it looks like. You may be better off using either Xubuntu or Lubuntu. 

[Xubuntu]("http://xubuntu.org/getxubuntu/")
[Lubuntu]("http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/")

---

### Post by Jijimon on 2015-06-20
My system is Core 2 Duo, 2GB Ram, 5 GB Swap, 95 GB disk
Using 32 bit Ubuntu and Using a 100 GB partition to save LibreOffice documents.
Till march 2015 my system was fast, now only it goes slow.
Any application make problem?
After repeated freezing I installed Clam AV virus scanner, detected 30 threats, after deleting the threats, system is not freezing, but the RAM shows almost filled.

---

