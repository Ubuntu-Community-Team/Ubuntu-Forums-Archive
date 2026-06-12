---
title: "virtual ubuntu on windows machine"
date: 2010-11-17
forum: Virtualisation
---

### Post by coloradocroat on 2010-11-17
I have a Dell Laptop running XP Pro, I would like to run a virtual copy of Ubuntu where I can have fast switching capability.  I would also like to not wipe out my XP Pro installation to do this.  

Is this possible?  I have a copy of VMWare VSphere, can I use this?

If I have to wipe out my XP Pro installation, can I image it first and then reload it from an image?

Anything special I have to do to install Ubuntu on a virtual machine?

Thank you,

---

### Post by sikander3786 on 2010-11-17
If you are going to install it as a Virtual machine, you probably don't need to image your Windows specifically for that. If you want to backup your XP just in case, you can use any tool like Norton Ghost, Acronis or a free alternative here.

[http://clonezilla.org](http://clonezilla.org)

Virtualbox is another free virtual machine server and works well with Ubuntu.

[http://virtualbox.org](http://virtualbox.org)

I haven't use VSphere and don't exactly know about its capabilities.

But as far as you are running Ubuntu as a Virtual Machine, you'll not see it work upto its potential, no compiz, wobbly windows etc. And the performance will be a bit reduced.

No need to completely wipe XP if you have some disk space available. You can install Ubuntu in dual boot to Windows. You'll get a menu at startup to switch between Ubuntu and Windows and it would be pretty stable, faster that way.

Go for Virtualbox if you just want to test it or install in dual boot if you want to use it for production purposes.

---

### Post by CharlesA on 2010-11-17
I use VirtualBox for running VMs on my Windows box.

You would only need to install VBox on the Windows machine and install Ubuntu into a virtual machine.

---

### Post by oldsoundguy on 2010-11-17
one thing to remember if you run a VM inside a Windows install .. if Windows crashes .. so does your VM.

Much more stable to run a VM inside of Linux .. then if Windows dumps (think percentages), you still have an OS and can do repairs, if possible.

---

### Post by endotherm on 2010-11-17
> **oldsoundguy said:**
> one thing to remember if you run a VM inside a Windows install .. if Windows crashes .. so does your VM.

Much more stable to run a VM inside of Linux .. then if Windows dumps (think percentages), you still have an OS and can do repairs, if possible.
see, i like that idea, but at the same time it is easier to live with ubuntu running with VB's generic hardware than it is with windows. can't play too many games with a "Virtual Box Video Card" running 128MB shared vram.

---

### Post by dcstar on 2010-11-20
> **coloradocroat said:**
> I have a Dell Laptop running XP Pro, I would like to run a virtual copy of Ubuntu where I can have fast switching capability.  I would also like to not wipe out my XP Pro installation to do this.  

Is this possible?  I have a copy of VMWare VSphere, can I use this?

If I have to wipe out my XP Pro installation, can I image it first and then reload it from an image?

Anything special I have to do to install Ubuntu on a virtual machine?

Thank you,

VMWare VSphere is an enterprise product, totally unsuitable for a laptop. Use VMWare's free VMware Player software as it will automate the install of Ubuntu as a VM.

If you wanted to run a Ubuntu host and turn your Windows into a VM then there is a free VMware tool to convert your current Windows install into a VM.

---

