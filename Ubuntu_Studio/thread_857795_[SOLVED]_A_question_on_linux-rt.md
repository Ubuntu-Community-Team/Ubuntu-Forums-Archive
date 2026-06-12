---
title: "[SOLVED] A question on linux-rt"
date: 2008-07-12
forum: Ubuntu Studio
---

### Post by Waqsione on 2008-07-12
Just a simple question: What does the linux-rt do?

---

### Post by Stochastic on 2008-07-13
laymans answer: makes low-latency audio recording/playback possible (i.e. fixes bugs in audio chain)

I can't give many specific kernel stack specification details as I don't really know, but a quick google search or a five minute session on #ubuntustudio IRC channel will provide more detail.

---

### Post by Capoeira on 2008-07-13
anybody knows what the disadvantage of the rt-Kernel is? more CPU-usage? has to exist a disadvantage because if it woudnt exist the "normal" would be rt too, wouldn't he?

---

### Post by thorgal on 2008-07-13
the completely preempted kernel can do real-time operation for audio work. It allows one to set the SCHED_FIFO scheduler bit to some processes, insuring those real-time execution. There are userspace tools to allow a non root user to benefit from this privilege (the PAM security stuff) and tune the priority of the IRQ threads according to needs (chrt tool). 

In human language, it means that a normal user can process audio in realtime without the drawback that the kernel would decide to suddenly give priority to something else (network interrupt, etc), which would result in an audible latency point in the audio flow.

There are drawbacks : security (non root user with certain super user privileges) and other awkward consequences (hibernation or sleep not working properly for exemple).

---

### Post by Waqsione on 2008-07-13
Thanks for the answers, everyone!

---

