---
title: "Diagnosing an Overwhelmed Server"
date: 2014-08-10
forum: Server Platforms
---

### Post by regnumimbriumx on 2014-08-10
Hey friends, I've got a 14.04 x86 server running on older but still decent hardware. I've got a number of software and processes running on it, as I'm experimenting with a few different things at once. I realized, this week, that the server HDD or processor is churning away like wild, inside. Its resources are so consumed that I can hardly login. The mouse moves slowly, the cursor only blinks like every 10 seconds, and it takes a full 5-15 minutes just for my typed password to appear. Login usually fails, too. Rebooting the server restores functionality, until I get to doing other things, the monitor turns off, and it eventually gets back to its absurd workload.

What's the quickest / best way to diagnose a rogue server that's eating up all its resources? I don't have any idea where to look, since I have no idea what the problem is.

Thanks so much!

---

### Post by Bashing-om on 2014-08-10
regnumimbriumx; Hi !

As in all things 'server' look to your logs ! ..Are they being swamped ? Are your logs running away to the point they are consuming all the user space ?
What does the terminal commands 
```

top
htop
ps aux
free

```
say about the memory management ?

[INDENT][INDENT]gotta start somewhere;
[INDENT][INDENT][INDENT][INDENT]these look good to me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tgalati4 on 2014-08-10
Then check your log files in /var/log.

---

### Post by SeijiSensei on 2014-08-10
Since you talk about a mouse, my first recommendation is to dump the GUI interface.  If you need to interact with the machine use the command prompt or SSH.  

Next, how much memory and how much swap do you have?  Without information like that, no one can really give you much help.  

If you reboot the server, how long does it take to bog down?  What is it doing when that happens?

---

