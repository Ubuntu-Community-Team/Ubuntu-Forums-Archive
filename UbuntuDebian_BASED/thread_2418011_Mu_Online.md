---
title: "Mu Online"
date: 2019-04-30
forum: Ubuntu/Debian BASED
---

### Post by krenkz on 2019-04-30
Hello there,

I need your help.
I am back on linux after few years (was using ubuntu 16.04). Now I installed PoP!_OS 18.04 LTS and this system looks like rly great. I would like to play Mu Online game, not on official server but on private server. This server is not using any guard. I have tried PlayOnLinux, WineHQ, CrossOver but nothing works for me. I have to doing something wrong, are there somebody who has experience in this and can help me? 

Thank you for any kind of help

---

### Post by oldrocker99 on 2019-04-30
The news isn't good. [https://appdb.winehq.org/objectManager.php?sClass=application&iId=1873](https://appdb.winehq.org/objectManager.php?sClass=application&iId=1873)

The [https://winehq.org](https://winehq.org) is a vast database of how well Windows games and utilities work under wine, and is worth checking before trying to run one. There are usually tips on how to get the game running properly. IF it runs.

---

### Post by krenkz on 2019-04-30
So last chance should be VM Virtual Machine. But I am not sure about graphic through path of performance or how to say that... I know that Mu is not so performance demanding game... we will see....

---

### Post by oldrocker99 on 2019-05-01
A VM is probably the way to go. VirtualBox has worked fine for me.

---

### Post by DuckHook on 2019-05-01
> **krenkz said:**
> So last chance should be VM Virtual Machine. But I am not sure about graphic through path of performance or how to say that... I know that Mu is not so performance demanding game... we will see....
I know nothing about MU but if you wish to go the VM route and graphic performance is a concern, then one possible option is using GPU passthrough in KVM.
Pros:
[LIST]
[*]KVM is native to Linux and already built into the kernel.
[*]It has proven GPU passthrough ability.
[/LIST]
Cons:
[LIST]
[*]Requires a second GPU, which usually means a second monitor and a desktop machine.
[*]Setting up passthrough is not trivial. [Example here]("https://ubuntuforums.org/showthread.php?t=2320369").
[/LIST]

---

### Post by krenkz on 2019-05-01
> **DuckHook said:**
> I know nothing about MU but if you wish to go the VM route and graphic performance is a concern, then one possible option is using GPU passthrough in KVM.
Pros:
[LIST]
[*]KVM is native to Linux and already built into the kernel.
[*]It has proven GPU passthrough ability.
[/LIST]
Cons:
[LIST]
[*]Requires a second GPU, which usually means a second monitor and a desktop machine.
[*]Setting up passthrough is not trivial. [Example here]("https://ubuntuforums.org/showthread.php?t=2320369").
[/LIST]


Thanks for guide. I've done that with WMware Workstation. This utility has passthrough ability up to 3GB of graphic memory so it is enough for Mu online, all works fine :). License is only 15-30 days but WMware Player should be free for non commercial use. 
Oracle VM was not work for me. I don't know why, probably graphic performance was so low...

Thanks all

---

### Post by Frogs Hair on 2019-05-02
Moved to *Ubuntu/Debian Based*.

---

