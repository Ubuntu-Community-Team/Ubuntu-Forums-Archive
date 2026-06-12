---
title: "Bringing an old computer to life"
date: 2006-02-02
forum: The Cafe
---

### Post by blackbeastofaarrgh on 2006-02-02
Hello, people! My friend gave me her old computer, which is an old eMachine.
It has 332 mhz, 32 megs of RAM, and a 3.2 gig hard drive. I've put Damn Small Linux on it, but since it has a 2.4 kernel, the machine locks up whenever I try to install a wireless driver with ndiswrapper. I know that this probably has something to do with the 2.4 kernel, so what I need is a Linux distro that is very lightweight, has a kernel higher than 2.4, and has wifi support. I know about a "kernel patch" for DSL, but I haven't found out how to do it. If you could explain how to do it, that'd be great. But an alternative distro would be just fine.
Sorry if this post is poorly written, my friend is bugging me on the phone and it's hard to focus. ](*,) 

-Cat

---

### Post by aysiu on 2006-02-02
If you want to use Ubuntu, maybe a server install and *sudo apt-get install xubuntu-desktop* might help... or is 32 MB too light for even XFCE?

---

### Post by blackbeastofaarrgh on 2006-02-02
I was thinking of doing that... I'll read up on XFCE and see what the minimum requirements are.

---

### Post by xequence on 2006-02-02
[QUOTE=aysiu]If you want to use Ubuntu, maybe a server install and *sudo apt-get install xubuntu-desktop* might help... or is 32 MB too light for even XFCE?[/QUOTE]

XFCE would not run in 32MB. It wasnt even that fast in 192 when I loaded up programs.

---

### Post by Iandefor on 2006-02-02
[quote=aysiu]If you want to use Ubuntu, maybe a server install and *sudo apt-get install xubuntu-desktop* might help... or is 32 MB too light for even XFCE?[/quote] Too light. XFCE needs around 64 MB to run at an acceptable speed. My suggestion to the original poster would be to play around a little. If she doesn't mind Fluxbox (the DSL interface), she could do a server install and then install Fluxbox or Blackbox. Or, she could try Windowmaker or some such thing.

---

### Post by aysiu on 2006-02-02
64 sounds about right. I used it on 128 MB of RAM, and it worked just fine.

---

### Post by blackbeastofaarrgh on 2006-02-02
Alright. DSL works great other than the ndiswrapper problem, and I do like Fluxbox. I'll try that sometime today/tomorrow morning and see if it works.
Oh, by the way, Iandefor, the "original poster" (if you're talking about me) is a she. :p Just letting you know.

---

### Post by Iandefor on 2006-02-02
[quote=blackbeastofaarrgh]Alright. DSL works great other than the ndiswrapper problem, and I do like Fluxbox. I'll try that sometime today/tomorrow morning and see if it works.
Oh, by the way, Iandefor, the "original poster" (if you're talking about me) is a she. :p Just letting you know.[/quote] oops :).

---

### Post by xmastree on 2006-02-03
[QUOTE=blackbeastofaarrgh]Oh, by the way, Iandefor, the "original poster" (if you're talking about me) is a she. :p[/QUOTE]
Hmm... **The Black Beast of Aarrgh.**

If you're interested, [**this**]("http://198.144.2.125/Siege/Photos/Full/black-beast-of-aaarrrrggh.jpg") is what she looks like. :rolleyes: 

Sorry I can't help about the ndiswrapper thing, only to suggest if you're looking for a lightweight distro, don't try puppy linux, it won't run with only 32MB.

Try over on [openlaptops]("http://www.openlaptops.org/"), you might get some ideas there.
Edit: I'm assuming that it's a laptop... is it?

---

### Post by briancurtin on 2006-02-03
try windowmaker if you cant get anything else going. it will probably work with what you have, no harm in trying anyways

---

### Post by blackbeastofaarrgh on 2006-02-03
Alright. I've run into some more problems.
I pop in the CD, it detects hardware, blah blah blah, but once it gets to a certain installation item (I forget what it was...) the CD drive stops (and I can hear the CD stop spinning) and it gives me a CD read error. It says that it cannot read the disc and it allows me to retry or cancel. The disc starts spinning again but the installation won't continue. I know it's not my CD because I tried 3 different discs. I'm thinking it might be the CD drive taking a crap on me.
Any solutions for this one? I'll try installing again and write down what it screwed up on. I'll also try googling for that DSL kernel patch...

---

### Post by newuser111 on 2006-02-03
boot with linux acpi=off

---

### Post by noalternative on 2006-02-18
Try feather linux, or a more recent version of dsl.  dsl should work with the ndis wrapper though.  The wireless problem maybe be a bios issue.

---

