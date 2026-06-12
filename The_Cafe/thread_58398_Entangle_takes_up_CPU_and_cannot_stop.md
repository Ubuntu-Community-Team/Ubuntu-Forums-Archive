---
title: "Entangle takes up CPU and cannot stop"
date: 2005-08-20
forum: The Cafe
---

### Post by erikpiper on 2005-08-20
Hi! I have recently installed e17 on my Ubuntu t23 install. I like it, and would like to keep it, but while in gnome, and console, the daemon "entangle" takes up 90%-100% I cannot close it. Kill 7484 (Job IT according to Top) does not do a thing. 

I searched a few times and came up with nothing.

Thanks!

---

### Post by Stormy Eyes on 2005-08-20
Did you try **kill -9** instead of plain old **kill**? kill by itself sends a polite "please terminate ASAP" to the specified process. kill -9, on the other hand, doesn't bother being polite; it just whips out a sledgehammer and beats the process into the ground.

---

### Post by erikpiper on 2005-08-20
And this is why I am a newbie! It worked! Now let me see what happens when I reboot. Hope it doesn't start again... (Cant avoid it. Battery powered. :) )

Thanks!

---

### Post by Stormy Eyes on 2005-08-20
[QUOTE=erikpiper]And this is why I am a newbie! It worked! Now let me see what happens when I reboot. Hope it doesn't start again... (Cant avoid it. Battery powered. :) )

Thanks![/QUOTE]

No problem. Remember that you can use killall instead of kill if you don't want to get the PID (process ID) of a process that's hogging the CPU(e.g. **killall -9 entangle**). Also, top also lets you kill processes if you hit the 'k' key. You'll be prompted first for the PID, and then for the signal to use. Signal 15 is the polite "please shut down" signal, while signal 9 is the "sledgehammer to the head" signal.

---

