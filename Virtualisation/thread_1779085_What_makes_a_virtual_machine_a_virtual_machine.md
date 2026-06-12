---
title: "What makes a virtual machine a virtual machine?"
date: 2011-06-09
forum: Virtualisation
---

### Post by ClientAlive on 2011-06-09
I was wondering what tangible things (files, etc) make a virtual machine different from a regular os. For instance: If one were to begin with just a regular old Linux os and attempt to manually make it into a virtual machine, what would he actually be doing - specifically, by name.

I'm not asking anyone to write a phD dissertation on the topic (unless you want to, I'll study it). I'm just hoping to get a kind of basic idea to start with.

For instance, I know there is some xml file in a virtual machine, or connected with it in some way. Apparently this xml file contains the parameters of the machine that you set up when you create it with the software. Things like the amount of ram for it to have and the size of the virtual disk.

Are there any other files that are unique to a virtual machine? What are they for? What do they do?

I'd sure appreciate a little start on this concept. By the way. I'm not actually intending to manually create a virtual machine. I do have intentions for the knowledge but that's another story and will involve more information than this question.

Anyhoo . . .  I'd sure appreciate if someone can give me a leg up on this. Really, right now, I'm just trying to work toward determining whether this thing I want to do is going to even be possible.

Thanks in advance to anyone and everyone who responds. Thanks for taking the time to read my post.

Jake

---

### Post by akand074 on 2011-06-09
[http://en.wikipedia.org/wiki/Virtual_machine](http://en.wikipedia.org/wiki/Virtual_machine)

---

### Post by ClientAlive on 2011-06-10
> **akand074 said:**
> [http://en.wikipedia.org/wiki/Virtual_machine](http://en.wikipedia.org/wiki/Virtual_machine)


Thanks akand047 but I've already read that article and a couple others that contain basic information. The article you reference talks about the uses of virtual machines and some basics about the difference between different types of virtual machines out there (such as type 1 vs. type 2 and paravirtualization vs. hardware assisted virtualization).

This: [http://en.wikipedia.org/wiki/Xen#Hardware-assisted_virtualization.2C_allowing_for_unmodified_guests](http://en.wikipedia.org/wiki/Xen#Hardware-assisted_virtualization.2C_allowing_for_unmodified_guests)  article talks a little bit about hardware assisted virtualization.

What I haven't seen though is what exactly is the _difference_ that makes a vm a vm as compared to a regualar system. Specifically, what I mean is, exactly what files are part of a virutual machine that are not part of a regular operating system? (The nuts and bolts of it). And, what do those files do and how to they work with the virtualization software to produce the virtual machine?

I certainly do appreciate the time you took to read my post and reply. I do feel, however, that I should clarify my objective with this thread.

I can google and I can read and research things. However, the subject at hand is a very vast subject, on the one hand, and a very convoluted subject on the other. Because it is so vast you have as many unreliable "facts" being told out there as you do reliable ones. In addition, without some specific direction that narrows down what I should be looking for information on, it would be like looking for a needle in a haystack.

So for example (and this is completely made up, just to give an example) - an answer that would fit my question might look something like this

[Example]
A virtual machine has 3 uniqe items in it that a regular operating system does not have. One of them is an xml file that contains the parameters of the hardware configuration for the machine. The other is a configuration file that is used by the virtualization software. That file is usually named [blank] or [blank] within the system. And finally there are drivers that . . . [??]. What makes those drivers different from regular drivers is [blank]. You should look into [blank] and [blank] and [blank]. Also, looking into [blank] would show you a good example of creating a virtual machine manually without using the software to do it. Maybe it would show you some things that apply to what you are trying to discover.
[/Example]


Thanks everyone for putting up with my long and very direct post. This is an important question to me and I really need help to point me in the right direction for my research. I talk like that only because this is the case. My intention is not to be rude but stems from a very pragmatic, matter of fact approach. Thanks for understanding.


Jake

---

### Post by psusi on 2011-06-10
The difference is that a virtual machine is not a real machine.

An OS normally manages a real computer.  A VM runs an OS so that it THINKS it is managing a real computer, but is not.

---

### Post by akand074 on 2011-06-10
> **psusi said:**
> The difference is that a virtual machine is not a real machine.

An OS normally manages a real computer.  A VM runs an OS so that it THINKS it is managing a real computer, but is not.

Exactly. From the wiki link:

> A virtual machine (VM) is a software implementation of a machine (i.e. a  computer) that executes programs like a physical machine.

---

### Post by ClientAlive on 2011-06-10
> **akand074 said:**
> Exactly. From the wiki link:


We aren't on the same page here guys. Maybe it's because of the title I used on this thread - I'm not sure. I'm not talking about the conceptual here; I'm talking about the tangible.

---

### Post by pricetech on 2011-06-10
Maybe I'm not on the same page either, but here goes anyway;

A virtual machine has "synthetic" hardware that is known to work with most contemporary operating systems and therefore requires no additional drivers be installed.

The virtual machine is "sandboxed" so to speak by the VM software and therefore can be better controlled and is less trouble if it goes astray because it can be terminated at any time without damage to real hardware, such as a head crash damaging a hard drive.

Virtual machines allow for multiple uses of given piece of hardware and are quite handy if you have an application that tends to be problematic or requires a specific environment, as in a legacy application that needs for example an old DOS based version of Windows to run properly.

Is that more in line with the input you were wanting ??

---

### Post by ClientAlive on 2011-06-10
> **pricetech said:**
> Maybe I'm not on the same page either, but here goes anyway;

A virtual machine has "synthetic" hardware that is known to work with most contemporary operating systems and therefore requires no additional drivers be installed.

The virtual machine is "sandboxed" so to speak by the VM software and therefore can be better controlled and is less trouble if it goes astray because it can be terminated at any time without damage to real hardware, such as a head crash damaging a hard drive.

Virtual machines allow for multiple uses of given piece of hardware and are quite handy if you have an application that tends to be problematic or requires a specific environment, as in a legacy application that needs for example an old DOS based version of Windows to run properly.

Is that more in line with the input you were wanting ??


Yes, getting much, much warmer. Thank you. Seriously, thank you.

What I'm after is the 'guts' of the virtual machine. The tangible files and folders, what function or purpose each of them serves, and their connections with one another that make it different from a regular, non virtual, system. And that's exactly what you've touched on here.

I don't expect anyone to write me a book on it and post it in this thread, that would be ridiculous. I do, however, ultimately need to learn these things pretty in depth. I thought some people might know some _relevant_ sources of information (ebooks, articles, etc) and maybe even go the extra mile for me by listing some brief details and connecting concepts to help me form a concept before digging into something that might be over my head.

By the way, I spent most of today googling for information on this and haven't gotten very far. (And I'm pretty darn good at doing internet research). For instance, one of the search terms I used was: "virtual machine from scratch." A bunch of deceptively good looking results came up. They all claimed to address building a virtual machine "from scratch" but when you read it, it's guiding you in using some piece of software to create the machine. I cry foul! That's not "from scratch!"

From scratch would be you open up a blank text document and begin to type into it. Perhaps you create several or even many of these text documents, and maybe some symbolic links, and other things; of course, an iso of the os you are turning into the vm is involved - and what you end up with is a virtual machine that you really really created from scratch that will run perfectly in Virtual Box or VMware or whatever else.


Thanks again guys. I really appreciate it.

---

### Post by psusi on 2011-06-10
You aren't making sense.  A machine is not a set of files, text or otherwise.  A machine is a set of hardware, starting with the cpu, ram, and other devices, like the keyboard and a disk drive.  A virtual machine is a program that presents a set of fake hardware that executes an OS just like real hardware would.  Inside the VM, nothing is different than it would be on real hardware.

---

### Post by akand074 on 2011-06-10
> **psusi said:**
> You aren't making sense.  A machine is not a set of files, text or otherwise.  A machine is a set of hardware, starting with the cpu, ram, and other devices, like the keyboard and a disk drive.  A virtual machine is a program that presents a set of fake hardware that executes an OS just like real hardware would.  Inside the VM, nothing is different than it would be on real hardware.

This.

In other words, a VM basically reserves a fraction of your actual machines hardware and as far as the OS being used within the VM that reserved fraction of hardware is your actual machine and runs on that assumption. To try to hit what you are actually asking, from scratch you would just have to write software that reserves a chunk of your RAM, hard disk space (perhaps dedicate processing threads), etc and then you'd allow other software (an OS) to run within it by pointing it towards your reserved resources to use. So then as far as that OS is concerned, that is a computer and the resources you reserved are the specs.

It's actually kind of difficult to explain to be honest, it can be a little abstract if you aren't some sort of specialist on virtual machines. So as far as most people could get is a general overview as I just explained. But the main thing to get out of it is that a Virtual Machine still needs actual hardware. You can't write fake RAM and fake hard disk that don't actually exist. The hardware does exist but is just separated from the rest of the hardware via software to reserve for a particular use.

---

### Post by ClientAlive on 2011-06-11
> **akand074 said:**
> This.
In other words, a VM basically reserves a fraction of your actual machines hardware and as far as the OS being used within the VM that reserved fraction of hardware is your actual machine and runs on that assumption. To try to hit what you are actually asking, from scratch you would just have to write software that reserves a chunk of your RAM, hard disk space (perhaps dedicate processing threads), etc and then you'd allow other software (an OS) to run within it by pointing it towards your reserved resources to use. So then as far as that OS is concerned, that is a computer and the resources you reserved are the specs.



I understand. Thanks akand074.

> **akand074 said:**
> 
It's actually kind of difficult to explain to be honest, it can be a little abstract if you aren't some sort of specialist on virtual machines. So as far as most people could get is a general overview as I just explained. But the main thing to get out of it is that a Virtual Machine still needs actual hardware. You can't write fake RAM and fake hard disk that don't actually exist. The hardware does exist but is just separated from the rest of the hardware via software to reserve for a particular use.


I understand. The hardware is what gives life to the software. The software directs the hardware and performs useful tasks. I get it. All software is just text in text files though and some links. Even if the text is special characters it is still a text file/ text files. You run it through a compiler and you get your machine code which is what actually runs on the hardware/ what the hardware components can actually use. The virtual machine uses the hardware. It has to or it would be nothing. That's common sense. It defines the resources (hard disk, ram, etc) that constitute the vm and presents it to the os as though it were the entirety of it. For all virtual machines other than hardware vm's it is necessarily the case that this hardware is defined via software and now we're back full circle to software being files and links. So the iso of the os in the "virtualization software" ("virtual machine" and "virtualization software" speak of two different things) is neccessarily identical to a regular, non virtual, os. It's this "virtual" part that I hope to discover what it is. I think what I'll do is create a virtual machine of something small and simple, puppy maybe, and try to reverse engineer it. I'll see if I can start taking the thing apart piece by piece and reading what I can find on the net and try to see what makes it tick.

Thanks a bunch for the effort. I do appreciate it. Sorry about the mistake in terminology.

Jake

---

### Post by slooksterpsv on 2011-06-11
> **ClientAlive said:**
> I was wondering what tangible things (files, etc) make a virtual machine different from a regular os. For instance: If one were to begin with just a regular old Linux os and attempt to manually make it into a virtual machine, what would he actually be doing - specifically, by name.


Virtual Machine means it runs inside of the OS you're running. It's not actually using all of the hardware, bios, memory, etc. that your computer has, and may have to subsequently "virtualize" (make up and use it's own implementation) drivers, disks, etc.

The "Disk" like your hard drive, is usually a file on your current OS. But it's accessed in the virtual like it was it's own hard disk. Now you can have a VM use the actual physical disk for its data as well.

VMs (Virtual Machine for short) are separate from the Host OS as you tell it what it can interact with, so in a sense they are more secure. But only as secure as you make them.

> 
...

Are there any other files that are unique to a virtual machine? What are they for? What do they do?
...


Yes, the hard disk images themselves, such as VMDK, VDI, QCOW2, COW, IMG, etc. Qemu/KVM mainly uses qcow2, cow, which are file types that are the files on the OS for what the Guest (Virtualized OS) writes data to. Some may have performance enhancing characteristics, or that.

I would seriously look into Virtual Box and run a VM, see what it's made of, see how it works in the sense of what you see. VMs are amazing. I run Windows XP in a VM for Netflix where it's not on Linux yet. It uses my VT-x enabled CPU so that it's faster. Audio is routed through the VM to my sound card so I can hear what is playing or that. And the connection I believe is a standard local SDL connection, but I can use a VNC. KVM allows the use of SPICE. (Different display servers). With a VNC I can access my VM over the web or over a local network. VERY useful for servers that you aren't always near, on, etc.

---

### Post by ClientAlive on 2011-06-11
> **slooksterpsv said:**
> Virtual Machine means it runs inside of the OS you're running. It's not actually using all of the hardware, bios, memory, etc. that your computer has, and may have to subsequently "virtualize" (make up and use it's own implementation) drivers, disks, etc.

The "Disk" like your hard drive, is usually a file on your current OS. But it's accessed in the virtual like it was it's own hard disk. Now you can have a VM use the actual physical disk for its data as well.

VMs (Virtual Machine for short) are separate from the Host OS as you tell it what it can interact with, so in a sense they are more secure. But only as secure as you make them.



Yes, the hard disk images themselves, such as VMDK, VDI, QCOW2, COW, IMG, etc. Qemu/KVM mainly uses qcow2, cow, which are file types that are the files on the OS for what the Guest (Virtualized OS) writes data to. Some may have performance enhancing characteristics, or that.

I would seriously look into Virtual Box and run a VM, see what it's made of, see how it works in the sense of what you see. VMs are amazing. I run Windows XP in a VM for Netflix where it's not on Linux yet. It uses my VT-x enabled CPU so that it's faster. Audio is routed through the VM to my sound card so I can hear what is playing or that. And the connection I believe is a standard local SDL connection, but I can use a VNC. KVM allows the use of SPICE. (Different display servers). With a VNC I can access my VM over the web or over a local network. VERY useful for servers that you aren't always near, on, etc.



Thanks a whole lot slooksterpsv. That gives me some good specifics to go on. I have Virtual Box by the way. I've created and run vm's in it before and today or tomorrow I'll be cloning my os and installing it as a vm in Virtual Box. That's awesome though with the file types you gave for the file for the virtual hard drive. If you have any specific technical information about a file for virtual memory or drivers I would love that. I'm trying to discover if I can do a certain special thing with a virtual machine - not just use the thing in the standard sense. That's why I'm looking for this info.

Thanks again.

Jake

---

### Post by slooksterpsv on 2011-06-12
> **ClientAlive said:**
> Thanks a whole lot slooksterpsv. That gives me some good specifics to go on. I have Virtual Box by the way. I've created and run vm's in it before and today or tomorrow I'll be cloning my os and installing it as a vm in Virtual Box. That's awesome though with the file types you gave for the file for the virtual hard drive. If you have any specific technical information about a file for virtual memory or drivers I would love that. I'm trying to discover if I can do a certain special thing with a virtual machine - not just use the thing in the standard sense. That's why I'm looking for this info.

Thanks again.

Jake

If you're thinking of gaming? If your system supports IOMMU then some Virtualization software can use the graphics card on your system to almost it's full extent. (e.g. you could run Portal 2 in a Windows 7 VM type deal) But your system has to support IOMMU and you need a Virtualization software that can handle that (like VMWare or Xen 4, etc.).

Specifics? I would just look at the documentation (or source) of like Virtual Box, Bochs, Qemu, KVM, Xen, etc.

KVM uses virtualization (vt-x)
Qemu is emulation (so you can use a MIPS-based OS on an x86 CPU)

---

### Post by ClientAlive on 2011-06-12
> **slooksterpsv said:**
> If you're thinking of gaming? If your system supports IOMMU then some Virtualization software can use the graphics card on your system to almost it's full extent. (e.g. you could run Portal 2 in a Windows 7 VM type deal) But your system has to support IOMMU and you need a Virtualization software that can handle that (like VMWare or Xen 4, etc.).

Specifics? I would just look at the documentation (or source) of like Virtual Box, Bochs, Qemu, KVM, Xen, etc.

KVM uses virtualization (vt-x)
Qemu is emulation (so you can use a MIPS-based OS on an x86 CPU)


Cool. I think now I have enough to go on for a while to do more in depth research. Names of file types for the hard drive file, etc.

Thanks man.

---

### Post by JKyleOKC on 2011-06-12
I just found this one, Jake, and it's right down my alley!

If you grok the mathematical concept of "duality" it becomes very simple, but I'll try to make it clear without getting too horribly math-oriented.

So long as at least a little bit of each are present in a system, hardware and software are equivalent to each other. It's theoretically possible to construct a fully programmable computer using a single flip-flop, a "nor" gate, a read-write head, and an infinitely long magnetic tape. That's the bare minimum for a Turing machine, and many years ago I actually wrote a program for such a device that would emulate an addition circuit. This was before the microcomputer appeared and it seemed like the only practical (?) way I could own my own computer. Had I actually built it instead of emulating its actions on paper, it would have taken a week or more to add 2+2 and come up with 4, and longer than that to do anything useful, but it eventually would do so.

Note what I said: the only hardware I used was a pencil and a pad of paper. The "hardware" in my test circuit consisted of *emulation* of the flip-flop, nor gate, head, and tape.

Now extrapolate that by a huge amount. It's also possible to write software to emulate just about any kind of hardware.

And that's what a virtualization program is: a program that emulates another computer, complete with RAM, disk storage, keyboard, display, the works. The program itself does the nitty-gritty of the emulation, creating the equivalent of a motherboard and power supply but very little more to start with.

When you create a virtual machine within that program, you create a configuration file that tells it how much RAM, what disks, what kind of display and keyboard, and so on, that your VM will have. The program uses this information to call in other routines that do the necessary emulation, and you wind up with a VM -- but it's still not usable because it does not have an operating system.

Once you install your o/s of choice, you have a working VM, and even though it gets all its input through the physical hardware of the host, and provides all its output the same way, it has no necessary logical connection at all to its host. They are two almost-independent systems. I say almost because the host has to be running the virtualization program itself before the VM can exist.

Operating systems themselves are not really all that difficult right down at their core; I've written a couple, long long ago. They get complex in a hurry when features start to be added, and I don't even try to understand all the levels of abstraction involved with the Linux kernel. The systems I wrote were very simple: they loaded programs, handled input and output, and dealt with boot-up and shutdown. The whole thing would fit easily on a small part of a single 5-inch floppy disk; one of them, in fact, was only about 100 bytes or so (on a "communications controller" that just happened to have all the attributes of a full-fledged computer, back about 1968 or thereabouts). Those three major areas are still the skeleton of any system, but "input and output" now involve literally thousands of kinds of devices, and scheduling program execution has become extremely complicated.

I hope this helps answer your original question somewhat. The flip answer that "one is real and the other isn't" was actually probably the closest to accurate that anyone can be!

---

### Post by ClientAlive on 2011-06-12
> **JKyleOKC said:**
> I just found this one, Jake, and it's right down my alley!

If you grok the mathematical concept of "duality" it becomes very simple, but I'll try to make it clear without getting too horribly math-oriented.

So long as at least a little bit of each are present in a system, hardware and software are equivalent to each other. It's theoretically possible to construct a fully programmable computer using a single flip-flop, a "nor" gate, a read-write head, and an infinitely long magnetic tape. That's the bare minimum for a Turing machine, and many years ago I actually wrote a program for such a device that would emulate an addition circuit. This was before the microcomputer appeared and it seemed like the only practical (?) way I could own my own computer. Had I actually built it instead of emulating its actions on paper, it would have taken a week or more to add 2+2 and come up with 4, and longer than that to do anything useful, but it eventually would do so.

Note what I said: the only hardware I used was a pencil and a pad of paper. The "hardware" in my test circuit consisted of *emulation* of the flip-flop, nor gate, head, and tape.

Now extrapolate that by a huge amount. It's also possible to write software to emulate just about any kind of hardware.

And that's what a virtualization program is: a program that emulates another computer, complete with RAM, disk storage, keyboard, display, the works. The program itself does the nitty-gritty of the emulation, creating the equivalent of a motherboard and power supply but very little more to start with.

When you create a virtual machine within that program, you create a configuration file that tells it how much RAM, what disks, what kind of display and keyboard, and so on, that your VM will have. The program uses this information to call in other routines that do the necessary emulation, and you wind up with a VM -- but it's still not usable because it does not have an operating system.

Once you install your o/s of choice, you have a working VM, and even though it gets all its input through the physical hardware of the host, and provides all its output the same way, it has no necessary logical connection at all to its host. They are two almost-independent systems. I say almost because the host has to be running the virtualization program itself before the VM can exist.

Operating systems themselves are not really all that difficult right down at their core; I've written a couple, long long ago. They get complex in a hurry when features start to be added, and I don't even try to understand all the levels of abstraction involved with the Linux kernel. The systems I wrote were very simple: they loaded programs, handled input and output, and dealt with boot-up and shutdown. The whole thing would fit easily on a small part of a single 5-inch floppy disk; one of them, in fact, was only about 100 bytes or so (on a "communications controller" that just happened to have all the attributes of a full-fledged computer, back about 1968 or thereabouts). Those three major areas are still the skeleton of any system, but "input and output" now involve literally thousands of kinds of devices, and scheduling program execution has become extremely complicated.

I hope this helps answer your original question somewhat. The flip answer that "one is real and the other isn't" was actually probably the closest to accurate that anyone can be!


Jim, you really need to see this business plan. It will, at the very least, make a lot of things I talk about on here make sense.

Also, as it turns out, I am somewhat of a math guy. I did very well with algebra, pretty good with trig, and went on through gen calc. It was about in the middle of my year of gen calc that things started to get real tough real fast.

Just thought I'd share that info.

This is fantastic! by the way. Thank you.

---

### Post by ClientAlive on 2011-06-12
> **JKyleOKC said:**
> I just found this one, Jake, and it's right down my alley!

If you grok the mathematical concept of "duality" it becomes very simple, but I'll try to make it clear without getting too horribly math-oriented.

So long as at least a little bit of each are present in a system, hardware and software are equivalent to each other. It's theoretically possible to construct a fully programmable computer using a single flip-flop, a "nor" gate, a read-write head, and an infinitely long magnetic tape. That's the bare minimum for a Turing machine, and many years ago I actually wrote a program for such a device that would emulate an addition circuit. This was before the microcomputer appeared and it seemed like the only practical (?) way I could own my own computer. Had I actually built it instead of emulating its actions on paper, it would have taken a week or more to add 2+2 and come up with 4, and longer than that to do anything useful, but it eventually would do so.

Note what I said: the only hardware I used was a pencil and a pad of paper. The "hardware" in my test circuit consisted of *emulation* of the flip-flop, nor gate, head, and tape.

Now extrapolate that by a huge amount. It's also possible to write software to emulate just about any kind of hardware.

And that's what a virtualization program is: a program that emulates another computer, complete with RAM, disk storage, keyboard, display, the works. The program itself does the nitty-gritty of the emulation, creating the equivalent of a motherboard and power supply but very little more to start with.

When you create a virtual machine within that program, you create a configuration file that tells it how much RAM, what disks, what kind of display and keyboard, and so on, that your VM will have. The program uses this information to call in other routines that do the necessary emulation, and you wind up with a VM -- but it's still not usable because it does not have an operating system.

Once you install your o/s of choice, you have a working VM, and even though it gets all its input through the physical hardware of the host, and provides all its output the same way, it has no necessary logical connection at all to its host. They are two almost-independent systems. I say almost because the host has to be running the virtualization program itself before the VM can exist.

Operating systems themselves are not really all that difficult right down at their core; I've written a couple, long long ago. They get complex in a hurry when features start to be added, and I don't even try to understand all the levels of abstraction involved with the Linux kernel. The systems I wrote were very simple: they loaded programs, handled input and output, and dealt with boot-up and shutdown. The whole thing would fit easily on a small part of a single 5-inch floppy disk; one of them, in fact, was only about 100 bytes or so (on a "communications controller" that just happened to have all the attributes of a full-fledged computer, back about 1968 or thereabouts). Those three major areas are still the skeleton of any system, but "input and output" now involve literally thousands of kinds of devices, and scheduling program execution has become extremely complicated.

I hope this helps answer your original question somewhat. The flip answer that "one is real and the other isn't" was actually probably the closest to accurate that anyone can be!


I had to read this a couple times to get it, but I think I get what you're saying. Yes, the vm requires physical hardware to run on (obviously) but the os in the vm is running on software that emulates hardware. It doesn't know the difference. In a way, one could use the analogy of piping. It's almost as if the vm is piping hardware to the os running in it except it goes both ways (not like with piping in Linux where it goes one way). So if we used that analogy it would be like saying the emulated hardware is the pipe. If I'm on the right track I can already see one big difference between emulated hardware and real hardware. That's probably the question I needed to ask from the beginning - what the difference is between emulated and real hardware is. I just didn't know enough to even ask.


> **JKyleOKC said:**
> 
I hope this helps answer your original question somewhat. The flip answer that "one is real and the other isn't" was actually probably the closest to accurate that anyone can be!


Yes it does. Actually it answers a couple of questions I've had; and, at least one of them is in an other thread. Wow. Really cool stuff Jim. Thanks.

---

### Post by JKyleOKC on 2011-06-13
The major differences between emulated and real hardware (assuming that the emulated is configured to be as identical as possible to the real, of course, which usually is NOT a valid assumption) almost all involve timing. The emulated version is necessarily slower since it's limited by the clock speed of the real on which it runs, and it takes several machine instructions in the virtualization program to emulate a single instruction in the emulated version. That's one of the reasons that virtualization works best with a multi-core CPU; it frees more power. Also, in real hardware many things can happen at essentially the same time (give or take a few nanoseconds) while in the emulated version the number of simultaneous actions is much smaller, and usually is only one unless you have many cores handling the job.

You'll see a distinction made between virtualization and emulation, but it's really one of degree rather than any major difference. Current processors that are optimized for "virtualization" have circuitry that reduces the severity of the timing problem, but they are still emulating hardware to create the guest machine. They're just doing it more efficiently. And it doesn't always help. Vbox, for instance often seems to perform better with the VT features turned off! Much depends on how your VM's o/s is configured. Some systems configure themselves differently at install time depending on whether the VT features are active, and changing the VT settings afterward can make them fail to work at all.

---

### Post by ClientAlive on 2011-06-14
> **JKyleOKC said:**
> 
The emulated version is necessarily slower since it's limited by the clock speed of the real on which it runs, and it takes several machine instructions in the virtualization program to emulate a single instruction in the emulated version.



Hmm . . .

I wonder if one can "overclock" a virtual machine? Now, of course, this would not ultimately be anything like real over clocking but but would be more along the lines of giving the vm higher priority at the processor and maybe ram too. In addition it would be to create a difference in the processing speed between the vm and the real. So the real would be reduced and the vm run full bore and the optimum setting for each determined by where they (the processing speeds) cross in the middle. I think this would result in an overall reduction in system performance though - perhaps even create some kind of downward spiral. In the best case scenario, would it even be any better?

Just some crazy ideas.
------------------

Edit: How do I convey this thought I'm having now?

So the above situation would indeed create a reduction in performance. Not just for the real but for the virtual as well. Because there are only two things in play here. Hardware and emulated hardware, and because the emulated runs on the hardware, reducing processing speed in the hardware will effect the vm performance as well. It is linear and only goes one way. The only work around this is to add a third element and use it as the basis of both the hardware and the emulated hardware. And now - I suppose that is exactly what that virtualization circuitry they talk about does (or at least how it tries to go about it). I wonder if I'm on the right track here.

All this being said though I can't get it out of my head how something like this could actually work. It makes logical sense if you look at it the right way. It could work because the potential of the processor to process at a given speed (quantity/time) does not change. That is the real foundation. Then because you aren't trying to make it process faster than it processes - your just telling it not to process the real as fast. Between the real and the emulated only one thing is being changed and that is to reduce the processing speed of the real. (I mean the real or host os. In all this that is what I'm referring to). So the way one does this is to have some (deamon?) or something that effects the way the kernel dishes out resources whenever the vm is launched. If you can set a constant in the vm itself you can then set a ratio for turns at the cpu in the kernel. If the vm takes and average of 3 instructions for every one of the host os, you set the kernel to give the vm 3 turns at the cpu for every one of the host os. Again if you can even out the load across the vm by making all its processing need come at a constant rate - you've got it.

This would not even be an overall reduction in system performance either since the potential of the cpu to run x number of cycles per (time unit) has not changed. The only thing that changes is the way you are using it's processing power. Not the processing power itself. In a way the big picture is like evening everything out across the board (everything meaning the host os and the vm all together - everything).

Hmmm . . .
------------

Edit 2: Arggghh! There's problems with that latter line of thought too. The hadware's ability is a fixed quantity. You're just shifting things around. What you add in one place to bring performance up rears its ugly head as a reduction in another place. You just can't get more out of something than is actually there. I guess that's why "optimize" is a really great word when thinking about this sort of thing.

---

### Post by slooksterpsv on 2011-06-14
I doubt I'm hitting this right, but the only way I could see is increasing it's "nice" priority to give the VM more power rather than having apps cut in and access the cpu.

(Like how on Windoze you have Low, Below Normal, Normal, Above Normal, Realtime)

I mean technically you could allocate a core of your CPU for the VM and dedicate it to that and revoke the privileges from the other programs. The only issue is you won't get the full CPU speed cause for the things it does have to emulate it has to use the CPU to calculate what to do with it, so you've hit a performance bump. Tech. the only way to get a full CPU speed in a VM would be to have an "extra" core to handle the other tasks that are being "emulated" which is where VMs are heading - more interaction with the hardware and bypassing the emulation stage all together.

---

### Post by JKyleOKC on 2011-06-14
Yep, "optimize" is the perfect word for this situation. You're dealing with two contradictory goals, in which attempting to increase performance for one causes a decline of performance for the other, so you simply have to make the best of it and find the compromise that gives the best result in total.

Today's multi-core processors, given adequate memory, make that "best result" pretty good. I actually see better performance from WinXP running in my VMs than I get with it running native (but on older, less capable, real hardware). My one experiment with running Linux in a VM under Xubuntu, to evaluate Debian Squeeze and see if it might be a viable replacement for Xubuntu in coming years, ran amazingly well also, although slower than the same package did when installed on an aging single-core machine later.

I don't see any advantage in trying to tweak things for better VM performance. When better performance is really needed, the best approach (IMO) is to go for improved real hardware, such as more cores and dizzying amounts of RAM. And if that's not enough, then abandon virtualization and run multiple real machines.

I doubt, however, that multiple real machines are likely to be necessary for many situations. In my own case, I've gone from the multiple-machine approach to using multiple VMs on a single, adequate, system and find that this gives me great advantages in the ability to snapshot and/or back up entire machines. Being able to move them from one real system to another simply by copying a few dozen gigabytes of files is much easier than moving by any other means...

---

