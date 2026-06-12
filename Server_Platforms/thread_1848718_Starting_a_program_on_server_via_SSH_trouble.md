---
title: "Starting a program on server via SSH trouble"
date: 2011-09-23
forum: Server Platforms
---

### Post by avatarmonkeykirby on 2011-09-23
Okay, so I have a server in the other room. I also have a program that runs on the machine that continuously runs that displays various things in the terminal and can also take input at my discretion (You know, your standard server).

I want to be able to start this program via SSH on my computer in my room. The problem is that when the terminal is closed the program ends. I attempted to run the program with the "&" option to run it in the background, and I still get the same problem.

What I would like to do is this. From my computer, I want to run the program on my server and have it display on that machine's terminal; as if I had run the program while physically sitting at the server. If this is possible I would like to know, or if I shouldn't use SSH but should be using a different program,  etc.  Thanks in advance for the help =)

---

### Post by Porcini M. on 2011-09-23
Precede the command with "nohup" - means "no hangup". Also use the "&".

---

### Post by papibe on 2011-09-23
There's an application called 'screen' that works perfectly to left commands running as they were running on a terminal.

To install it:
```
$ sudo apt-get install screen
```

Here are couple of tutorial: [here]("http://www.nixtutor.com/linux/introduction-to-gnu-screen/") and [there]("http://news.softpedia.com/news/GNU-Screen-Tutorial-44274.shtml").

The program is very powerful and have so many options that can be overwhelming sometimes, but you can keep it simple. In your case, all you need is grasp very well the first paragraph of the first tutorial (Leaving the Terminal).

I hope it helps, and tell us how it goes.
Regards,

---

