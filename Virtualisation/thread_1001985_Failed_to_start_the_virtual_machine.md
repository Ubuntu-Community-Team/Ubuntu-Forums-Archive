---
title: "Failed to start the virtual machine ***"
date: 2008-12-04
forum: Virtualisation
---

### Post by JeyPeyy on 2008-12-04
I can't start virtual machines under VirtualBox anymore. Everytime I try to do so, I get this message:

---

### Post by bodhi.zazen on 2008-12-04
Looks like you installed kvm. kvm and virtualbox are incompatible.

If you did not install kvm, did you activate hardware acceleration in advanced settings ?

---

### Post by Santala on 2008-12-04
> **JeyPeyy said:**
> I can't start virtual machines under VirtualBox anymore. Everytime I try to do so, I get this message:
Hi!

Same thing here.  I used -- purge KVM and the result is a VirtualBox that starts, but will not get very far booting machines.  At times I get a black window, sometimes I get as far as XP without start button -- just blue wall paper.  

Is there a difference (especially with KVM) between 8.04 and 8.10?

Could somebody help us, please?  Thanks!

Santala

---

### Post by Santala on 2008-12-04
> **bodhi.zazen said:**
> Looks like you installed kvm. kvm and virtualbox are incompatible.

If you did not install kvm, did you activate hardware acceleration in advanced settings ?
Hi Bodhi-Zazen!  Glad to see you.  Do you mean the VT-x enabling in the VirtualBox settings?  Yes, I did.  

I understand Ubuntu pushes KVM?  What is the reason?  This gives me an idea: how about Synaptics noticing such incompatibilities when I try to install VirtualBox...

---

### Post by JeyPeyy on 2008-12-04
> **bodhi.zazen said:**
> Looks like you installed kvm. kvm and virtualbox are incompatible.

If you did not install kvm, did you activate hardware acceleration in advanced settings ?

Oh yeah I remember doing that now! Thank you =)

Should I mark this thread as solved? It seems like other people still have issues with this even after purging kvm.

---

### Post by bodhi.zazen on 2008-12-04
> **Santala said:**
> Hi Bodhi-Zazen!  Glad to see you.

:Redface:

> Do you mean the VT-x enabling in the VirtualBox settings?  Yes, I did.  

I understand Ubuntu pushes KVM?  What is the reason?  This gives me an idea: how about Synaptics noticing such incompatibilities when I try to install VirtualBox...

I do not know why Ubuntu chose KVM, but my guess is that KVM is open source (and not a stripped down version of a commercial product) and that is is "cutting edge".

It will be interesting to watch, but as KVM matures it will be interesting.

If your thread is solved it is considered conscientious to both mark it as solved (see the link below) and specify *what* solution you used (this helps others who search these forms with similar questions).

Solved:

Woot ... :guitar:

Please mark this thread as solved, it saves the time of many volunteers looking to help 
[indent]... and users looking for solutions.[/indent]

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

