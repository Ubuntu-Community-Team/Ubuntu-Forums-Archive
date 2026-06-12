---
title: "an app called &quot;yes&quot; crash my system"
date: 2011-05-01
forum: The Cafe
---

### Post by eGelor on 2011-05-01
Hello friends,
when i boot my pc there are 3-4 process running from a small program called yes. To stop them, i had to kill them after boot.
Please post me back.

---

### Post by NovaAesa on 2011-05-01
Why would you stop them? Were they doing something you didn't want them to do?

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-05-01
Or, you could just, you know, open another virtual terminal and kill them without rebooting.

---

### Post by Lucradia on 2011-05-01
> **NovaAesa said:**
> Why would you stop them? Were they doing something you didn't want them to do?

"yes" is a terminal program that feeds (infinitely) the word "yes" or any word given after its call. (Using yes appropriately, IE: Piping it through another command, however... will make it useful.)

So of course, leaving it on can cause CPU to increase dramatically over time. High End CPUs however won't crash for hours, if ever. (You may see considerable slowdown though.)

---

### Post by NovaAesa on 2011-05-01
I'm aware of what the yes program does, I was just trying to establish the reason the OP was stopping the running instances of it. As you pointed out, if yes is used for its intended purpose by being piped into another program, it shouldn't be taking up many CPU cycles at all.

---

### Post by nerdopolis on 2011-05-01
actually... it can use lots of CPU if you do ```
yes > /dev/null
```that command should bring the CPU usage to that of 1 CPU core.

(if you have a single core system it will use 100%, an on a dual core system 50%...)

EDIT: I just realized that **NovaAesa** had said "if its being used for its intended purpose" it should not be taking up too many CPU cycles... sorry

---

### Post by matthewbpt on 2011-05-01
Strange that the program is running on every boot :S It isn't running on any of my machines.

---

### Post by eGelor on 2011-05-01
Thank you all for replying at once.
Before i post this thread i read the man page of yes.
before a week there was no problem. i try to remove it but i cant.
Also i didnt said that i had to reboot my machine. i just kill yes at every boot of my machine. 
Please post and answer.

Thank you all again.

---

