---
title: "stupid question about my VM &quot;file&quot;"
date: 2009-01-16
forum: Virtualisation
---

### Post by muteXe on 2009-01-16
Hiya,
This is my first delve into the world of VMs, so I apologise for my (possibly) stupid questions.

I have used virtualbox OSE to create myself a VM(allocating 10Gb of my HD and 1.5Gb of RAM to it).  I mounted my dvd drive and pointed at the Damn Small Linux iso that was on there, and sure enough DSL booted up fine.
I tried the same with a Fedora disk,  and sure enough the install/boot/mem test menu came up.  I panicked there and switched off.  Do i select the normal install option?  Will this install Fedora to my 10Gb VM "file"?  Do i need to allocate swap space within my 10Gb VM?

Is there an option to delete this VM in the future?  Or do i just "rm -rf <VM file>" from the command line?

If i had the fedora iso and not the disk could I have just pointed my VM to this file? Would this have worked?

Once again, sorry for the silly questions.  Been using Linux for a few years but never experimented with VMs.

Thanks very much,

mute

p.s. using hardy as my host if it makes a difference to the answers.  Thanks.

---

### Post by Dedoimedo on 2009-01-16
Hello,

Think of virtual machines as complete machines living inside your host.

You can boot from CD, install to the virtual hard disk, you can even dual boot inside virtual machines. When you setup the partition layout, should you choose to install, you can setup swap for your distros, too.

What you experienced with Fedora was the normal boot menu before you hit the live CD session. Not to worry. Hitchhiker's Guide to the Galaxy rule 1: Don't panic!

Virtual machines are just files, delete or copy or move them as you like.

Mounting isos as CD works great. It will also make things faster.

I've written quite a bit on virtualization, you may want to read a few things before you dig in:

[http://www.dedoimedo.com/computer_software.html#virtualization](http://www.dedoimedo.com/computer_software.html#virtualization)

Enjoy.

More questions | ping me ...

Cheers,
Dedoimedo

---

### Post by muteXe on 2009-01-16
cheers mate, that was really useful. Gonna have a read of your link now.

thanks again,

mute

ps  Cant see the "thank you" icon anywhere sorry.

---

