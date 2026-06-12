---
title: "Free Software alternatives to Exact Audio Copy (EAC)"
date: 2008-09-27
forum: The Cafe
---

### Post by DPic on 2008-09-27
What are the free software alternatives to EAC that already offer all of its functionality or aim to do so?

---

### Post by tbroderick on 2008-09-27
There are lots of CD rippers.

Asunder
Grip
Sound Juicer
K3B
Brasero
Abcde

Or use EAC in wine.

---

### Post by Artemis3 on 2008-09-27
The only one aiming the same goal is [rubyripper](http://code.google.com/p/rubyripper/). The problem is [cdparanoia](http://www.xiph.org/paranoia/) needs updating (to bypass cache, C2 support, etc), and most rippers use cdparanoia.

---

### Post by DPic on 2008-09-27
> **Artemis3 said:**
> The only one aiming the same goal is [rubyripper](http://code.google.com/p/rubyripper/). The problem is [cdparanoia](http://www.xiph.org/paranoia/) needs updating (to bypass cache, C2 support, etc), and most rippers use cdparanoia.

Is cdparanoia being worked on for that update? 

Is rubyripper already stable and supporting all those things? 

What does bypassing the cache, C2 support, and whatever else, do?

---

### Post by DPic on 2008-09-28
Hello? Does anybody know?

---

### Post by erudite on 2008-10-15
I dunno if you've made a decision yet but rubyripper is the best (most secure and best rip).

I recommend it.

I have no clue about your questions but just use it and if they update it then good.

---

### Post by Bungo Pony on 2008-10-15
I used EAC in Wine until I added a second drive, which seems to have made it flakey. :confused:

When I'm not using EAC, I use Sound**K**onverter. But there seems to be a bug where I have to restart the program if I change my destination directory. But it works pretty good :)

---

### Post by Polygon on 2008-10-15
if you have to ask, are you really sure you want the microscopic differences that exact audio copy gives you over traditional cd rippers?

anyway, i would presume that they are methods of making it so that the audio extracted from teh cd is as accurate as possible. Why people bother with this, i have no clue, since the majority of the human population would not notice the difference between an EAC and some other rip, but thats just me.

---

### Post by plantatree on 2011-01-09
I hate shareware but this time I have to say that EAC just kills any competition. It rips on full speed and only on quality concerns lowers drive speed.
I'm ATM ripping a very badly damaged Audio CD. I couldn't rip it with cdparanoia for 12 hours so decided to stop before my drive is still functioning. So here is the time to say EAC has an option to let CD drive rest each hour or whatever user configures.

After the rip completes, I'll compare result of cdparanoia and EAC. Will compare how much data roughly is different by different encoding. I do it like:

1. convert track to raw format
2. base64 encode the track with line wrapping
3. compare the base64 encoded audio data of the two tracks

That tells me comperaively how different the two tracks are. So far I have found that paranoia mode 3 and mode 0 result in some differences. EAC vs cdparanoia is next to check. Also I'm curious to see how will EAC and paranoia mode 0 compare on the most damaged tracks. As I said couldn't make paranoia mode 3 to complete in a reasonable timeframe with them.

---

### Post by dh04000 on 2011-01-09
> **Artemis3 said:**
> The only one aiming the same goal is [rubyripper](http://code.google.com/p/rubyripper/). The problem is [cdparanoia](http://www.xiph.org/paranoia/) needs updating (to bypass cache, C2 support, etc), and most rippers use cdparanoia.

When you say rubyripper has the same goal... do you mean the same goal to provide the same quality as EAC does, because at the moment, noone is better than EAC when it comes down to pure control and sound excellence.

Also, how do I make a .deb out of that .tar file...? I don't know how to use source files for installation.

---

### Post by s.fox on 2011-01-09
[IMG]http://serial-coder.co.uk/blog/wp-content/uploads/2010/11/threadNecromancy.jpg[/IMG]

Thread Closed.

---

