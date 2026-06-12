---
title: "How is windows 7/8 on a virtual machine?"
date: 2014-04-26
forum: Ubuntu, Linux and OS Chat
---

### Post by Nick_Halden on 2014-04-26
Hello guys,
I would like to switch to ubuntu only (maybe with arch) from dual boot windows 8/ubuntu. I don't want to use wine, so I wanted to ask you, how is windows 7/8 on a virtual machine? Is it smooth and works good? I'm looking for using it sometimes for office (Because I want to work with the same software as my partner if we work toghether) and visual studio (visual studio for simple programs, university homework and so on), will it do the job well?

Thenks in advance :)

---

### Post by Old_Grey_Wolf on 2014-04-26
I haven't tried Windows 8 but I have used Windows 7 in a VM. How well it works depends on your processor and the amount of RAM your computer has. Can you post the specs for your computer so people can give you advice?

---

### Post by Eggnog on 2014-04-26
I'm running Ubuntu 14.04 on one of my desktops, an AMD 965 quad core with 4GB RAM.  I have a Win 7 VM in Virtualbox, using 1.5GB RAM.  It runs fast, smooth and problem free.  I use it mostly for Netflix, MS Office and, more importantly, Quicken.  Yes, Quicken.  Try as I might, I can't find anything else I like better.  Not KMyMoney, not GNU Cash, not Moneydance ... nothing.  I think Ubuntu with Win in a VM is the best of both worlds.  You can still run Win, but it isn't running your machine.

---

### Post by monkeybrain20122 on 2014-04-27
> **Eggnog said:**
> I'm running Ubuntu 14.04 on one of my desktops, an AMD 965 quad core with 4GB RAM.  I have a Win 7 VM in Virtualbox, using 1.5GB RAM.  It runs fast, smooth and problem free.  I use it mostly for Netflix, MS Office and, more importantly, Quicken.  Yes, Quicken.  Try as I might, I can't find anything else I like better.  Not KMyMoney, not GNU Cash, not Moneydance ... nothing.  I think Ubuntu with Win in a VM is the best of both worlds.  You can still run Win, but it isn't running your machine.

You don't need VM Windows for netflix. Pipelight works very well though netflix is garbage. :)
[http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)

---

### Post by Eggnog on 2014-04-27
Oh, I know.  I've had it installed under Linux before.  But I've already got the VM for other things so why not use it for Netflix, too?  I generally leave the VM up in another workspace, so it's just a click or two to get there.  I don't use Netflix all that often anyway.

---

### Post by Nick_Halden on 2014-04-27
> **Old_Grey_Wolf said:**
> I haven't tried Windows 8 but I have used Windows 7 in a VM. How well it works depends on your processor and the amount of RAM your computer has. Can you post the specs for your computer so people can give you advice?

I have 2.5 GHZ proccesor (dual-core) with 6gb ram (4gb+2gb, I don't know why they sold it that way).

And thenk you all for your help guys :) I really appreciat it.

---

### Post by lykwydchykyn on 2014-04-27
My machine at work is an Athlon II X2 (Dual-core AMD 2.8GHz) with 8 GB of RAM.  I run Windows 7 in virtualbox with like 1.5 - 2 GB of RAM and I hardly know it's on.  The only thing that really grinds it down is disk access, especially if I try to run a second VM at the same time.  Mostly I just have it for little windows-only client applications, I don't do a lot of heavy work in it.

---

### Post by Old_Grey_Wolf on 2014-04-27
> **Nick_Halden said:**
> I have 2.5 GHZ proccesor (dual-core) with 6gb ram (4gb+2gb, I don't know why they sold it that way)

I have run Windows 7 on a similar computer using virtualbox. Like lykwydchykyn, I gave it 1.5 - 2 GB of RAM. Windows 7 ran as well as a VM in virtualbox as it did as a dual boot on my notebook.

Try it if you can. That is the way to know for sure it will work for you. If your dual-core is multi-threaded, I think it will work very well.

---

### Post by LVDave on 2014-04-27
I run a virtualbox vm of windows 7 with 3.5GB of ram on a quad-core xeon system with 8GB of ram on KUbuntu 14.04.. Can hardly tell the vm is running.. Definately no problems.. Dunno about 8, I looked at it during its beta, and gave it a pass...

---

