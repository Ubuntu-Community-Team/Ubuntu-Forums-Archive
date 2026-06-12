---
title: "Fork bomb"
date: 2011-07-15
forum: Security
---

### Post by kirthi on 2011-07-15
I am new to learn about fork bomb. I saw in a website that limiting the number of process we can prevent fork bomb. What does it mean?

---

### Post by uRock on 2011-07-15
I haven't heard of many home users being hit with a fork bomb style DoS attack.

[http://en.wikipedia.org/wiki/Fork_bomb](http://en.wikipedia.org/wiki/Fork_bomb)

---

### Post by kirthi on 2011-07-15
In what way does fork bomb harm any system. Is it through the net we use or inbuilt in the system when we work on more applications?

---

### Post by uRock on 2011-07-15
The link I provided above explains Fork Bombs. If you are not running server applications and you are not forwarding ports at your router/firewall, then you have nothing to worry about. It is a Denial of Service(DoS) attack.

---

### Post by doas777 on 2011-07-15
a fork bomb is a denial of service attack, that is caused by a malicious program that keeps running fork() on itself infinitely. fork() causes a new process to spawn (usually a clone of the process calling fork). Fork is particularly needed for server services that listen on one port, but that then run established connections from a different port. 

the system has a list of running processes (the process table), but that list can be filled up. when it is, no other processes can be started.


the advice you are hearing, is telling you to make sure that you set a maximum number of processes that may run, which is less than the max number the system can support. that way your list of processes can never overflow. 

[https://secure.wikimedia.org/wikipedia/en/wiki/Fork_bomb](https://secure.wikimedia.org/wikipedia/en/wiki/Fork_bomb)

---

### Post by Soul-Sing on 2011-07-15
:[http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)
> Forkbomb: Executes a huge number of processes until system freezes, forcing you to do a hard reset which may cause corruption, data damage, or other awful fates.
In Bourne-ish shells, like Bash: (This thing looks really intriguing and curiousity provokes)

warning malicious commands: > We've recently had an increase in the number of dangerous commands being posted on the forums. Don't pretend you don't know what I mean -- commands that cause massive damage or disruption to the user's computer.

---

### Post by kirthi on 2011-07-15
> **leoquant said:**
> :[http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)


warning malicious commands:

If I am running too many process and if it results in a fork bomb problem I must restart or reboot my system to stop it. Why not I use kill or killall to stop that process. Will it completely kill the fork bomb? What does rebooting my system do?

---

### Post by uRock on 2011-07-15
> **kirthi said:**
> If I am running too many process and if it results in a fork bomb problem I must restart or reboot my system to stop it. Why not I use kill or killall to stop that process. Will it completely kill the fork bomb? What does rebooting my system do?

You can't run kill or killall if your system is already running its maximum number of processes.

---

### Post by doas777 on 2011-07-15
> **kirthi said:**
> If I am running too many process and if it results in a fork bomb problem I must restart or reboot my system to stop it. Why not I use kill or killall to stop that process. Will it completely kill the fork bomb? What does rebooting my system do?

well the problem is that the DOS is accomplished by filling up your process table to the extent that you cannot spawn new processes, including the instance of killall. 
so if you can get it to run, killall should work, but if the fork processes are not consuming resources beyond a entry in the process tab, then you would probably not notice all the forked processes until you have reach the max and are effectively locked out.

your process table is in ram, and gets recreated upon each boot. thats why rebooting fixes the problem.

---

### Post by kirthi on 2011-07-15
> **uRock said:**
> You can't run kill or killall if your system is already running its maximum number of processes.

It have been said in a website that using kill or killall we can terminate the bomb's process. And exec() can be used which replaces shell process with specified program.

---

### Post by uRock on 2011-07-15
> **kirthi said:**
> It have been said in a website that using kill or killall we can terminate the bomb's process. And exec() can be used which replaces shell process with specified program.

I think doas777 explains this very well. If your process table is full, then you will not be able to run the instance of kill(all).

---

### Post by Elfy on 2011-07-15
This smells of homework.

Closed.

---

