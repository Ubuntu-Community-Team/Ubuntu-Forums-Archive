---
title: "Virtual windows vista under virtual box on ubunto 9.10 host"
date: 2010-03-19
forum: Security
---

### Post by dogdo on 2010-03-19
Hi

Im trying to set up the above to play windows games while using ubuntu-for a virtual windows system do i need to have windows security measures in place? 

If the windows virtual machine gets infected will ubuntu host be attacked as well?

---

### Post by yota on 2010-03-19
Hi Dogdo,

the problem is that virtual machines are lacking graphical performance.
So I don't think that virtualbox is suitable for last-gen gaming.

Speaking about security, windows viruses don't work on linux, but for instance if the windows host is infected by a trojan you still have an hole in your perimeter...

Hope this helps!

---

### Post by dogdo on 2010-03-19
Well i still have a windows xp partition under dual boot configuration. *sigh*

So what can operating systems under virtual box do-only basic stuff like word documents? 

Where can i find info on virtualisation security-i would have thought that in order for malware to attack the host system it would first have to bypass the virtual barrier-but is the virtual system not sandboxed from the host os?

---

### Post by yota on 2010-03-19
I would not say that virtual machines are just for "basic stuff", on them you can even install an application server that hosts a web application which connects to a database (on the same vm). You can install a full blown integrated development environment and program in .N-PropriETarycrap (or whatever your pick is ;-) ).  You can do pretty much everything you like.

VMs just lack (a bit of) graphical preformance, so everything that is not graphic intensive works perfectly fine.

About the isolation/sandboxing remember that (even if it'not strictly necessary) VMs usually are connected to the host through the network (local, NAT or host only).
Sure, disabling network would enhance security, but would reduce usability as well.

---

### Post by dogdo on 2010-03-19
Fair enough im only using my current set up at home for basic stuff-surfing and writing essays-so ubuntu is ideal for me. 

My understanding is that the reason linux cant play games is due to the proprietary direct x protocol- is there a likelyhood in the near future that new pc games will support open gl any time soon? 

Till then i have to use windows xp to play games.

---

### Post by yota on 2010-03-19
Exactly, DirectX is the way MS uses to enforce a lock-in on windows as a gaming platform. You can read some details on the matter [here]("http://blog.wolfire.com/2010/01/Why-you-should-use-OpenGL-and-not-DirectX").

As the article says, the problem is that this is a positive feedback loop (developer chooses to develop for the most widely used platform and user chooses the platform with most titles). So probably this will require time to change.

There's an effort to make a realtime-translator which maps directX calls to OpenGL, thus enabling to play windows games on Linux: [transgaming]("http://transgaming.com/")
Unfortunately, even if it's a remarkable work, it has some drawbacks as well. First cedega is not free, second there are compatibility and performance issues, and finally (most important IMHO) that you lose the "I just wanna play®" appeal.

My personal answer to gaming is using a console (which is OpenGL powered by the way ;-) )

---

### Post by dogdo on 2010-03-19
I would have thought that the lock in imposed by direct x would be an illegal anti competitive practice-similar to how microsoft were nearly forced to create a windows e edition(windows os without internet explorer installed). 

Unfortunately i cant support the open gl protocol. As the article said its a vicious circle-if consumers want to play the latest games then these will be more than likely built by the developers with direct x. And the fact that some of the compatibility programs such as Crossover Games have a limited list of what is supported under linux. A lot of the games i play on windows wont even run under crossover. Its really quite sad that people are forced to use windows to play games. The main reason i left windows was for security issues-viruses!! 

And one of the games im looking forward to playing-command and conquer 4 will have that DRM that forces you to connect the EA servers in order to play. So if my internet connection goes down or if there servers are offline i cant even play as a single player,let alone multiplayer.

---

