---
title: "Windows on System 76"
date: 2007-03-12
forum: System76 Support
---

### Post by tux_rox on 2007-03-12
Most "experts" say that you shouldn't put Windows on *after* you've already booted with Ubuntu - something about Windows taking over the system (like it didn't do that enough already).  So, if Sys 76 computers come with Ubuntu, how would you load on Windows if you really have to (excluding wine and the linux-ed versions of apps)?

P.S.  I know there's a link about this floating around somewhere from the company that I've already read - I'm also interested in what you guys have to say in addition to that wiki.

---

### Post by tux_rox on 2007-03-12
WOW - I'm an idiot.  My thread is pretty much repeated a couple lines below mine.  :oops:

Sorry about that - but if anyone has any thoughts, feel free to share!

---

### Post by x64Jimbo on 2007-03-12
The only thing that Windows does to your system is it overwrites your MBR with its own bootloader. If you resize your Ubuntu partition, you can then install Windows, then restore the MBR with GRUB.

---

### Post by Paul41 on 2007-03-12
Unless you are installing Windows to play games you could just run it in VMware.

---

### Post by maniacmusician on 2007-03-12
> **Paul41 said:**
> Unless you are installing Windows to play games you could just run it in VMware.
I recommend VirtualBox instead of VMWare. 

But Paul41 is right. Most computers from Sys76 are fast enough to run Virutal Machines, and so could run Windows using VirtualBox pretty easily. Unless you need it for games, it's a much easier solution than making a Windows partition.

---

### Post by crichell on 2007-03-13
adding Windows in a dual boot situation is pretty easy - and won't hose your Ubuntu install.  Here's directions:

[http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)

---

### Post by tux_rox on 2007-03-13
I'm assuming this will work on Edgy and Feisty too, right?  (It says you need the Dapper cd in the directions.)

Thanks for your suggestions - my only hesitation about switching to Ubuntu for a primary OS has been the fear of never being able to use Windows software again.  If more people knew that there are options out there, I'm sure that there would be many more Ubuntu-ers.  :)

---

### Post by crichell on 2007-03-14
> I'm assuming this will work on Edgy and Feisty too, right? 

Yes - I should update that too.  Thanks.

---

