---
title: "Virtualbox guest doesn't see USB device while VM is loaded"
date: 2009-08-18
forum: Virtualisation
---

### Post by trunkmonkey on 2009-08-18
I just had a friend install Ubuntu (Jaunty), but my wife wanted Windows XP back (she just doesn't like her computing environment to change), so I loaded XP Pro in a Virtualbox VM. No problems there, installed fine, and I finally figured out how to get it to recognize my USB devices (printer and iPhone), but there is one problem.

If I plug the iPhone in before I start the VM, it sees it and connects to it just fine. But if I launch the VM and then plug in the iPhone, it won't see it and I have to go under the devices menu and connect manually. That's not a problem for me, but I'd like it to be invisible for my wife so she doesn't have to worry about that. 

So, my question is: is there any way to get a Virtualbox guest OS to see USB devices automatically if you plug them in after it's running?

Thanks.

---

### Post by jocampo on 2009-08-18
Your wife is really picky, hahaha...sorry, I'm kidding!.

Couple of things...did you install virtualbox additions? ... what VirtualBox version you're running now

---

### Post by shiva.n on 2009-08-20
If you have Virtualbox OSE, you will not have USB support.
 
[http://ubuntuforums.org/showthread.php?t=715636](http://ubuntuforums.org/showthread.php?t=715636)
 
Disclaimer: I have just installed Virtualbox yesterday, and am by no means knowledgable. But will be soon...:)

---

