---
title: "No gui in virtual Ubuntu install"
date: 2012-01-12
forum: Virtualisation
---

### Post by thbeau@gmail.com on 2012-01-12
Hi, brand new with ubuntu. I am trying to install ubuntu 32Bits under Virtual PC 2007. The installation goes well, except when all seems to be completed, I do not have the GUI desktop, rather a console prompt [EMAIL="USER@machinename:~$"]USER@machinename:~$[/EMAIL]     What should i DO to get the GUI interface ? Thank you in advance for a prompt answer - cdt - Thierry

---

### Post by nothingspecial on 2012-01-12
Question moved to it's own thread.

Hi Thierry, welcome to the forums :)

Please do not post your questions in someone else's thread, particularly if the thread you post in has nothing to do with your question.

---

### Post by drmrgd on 2012-01-12
I'm not entirely sure what your specific problem is, and there may be some quick fixes that someone will suggest.  However, I do want to weigh in on running Ubuntu under Virtual PC.  I've tried that here and found that Ubuntu runs horribly under that environment.  I was limited, though, as I don't have admin privledges on my work computer and they had already installed Virtual PC on this computer.  I think it's designed more to run Windows XP as a guest under Windows Vista, 7, etc. I do recall getting Ubuntu to install, but kept getting all kinds of errors and compatibility problems (can't quite remember specifics, though). 

If possible, I would recommend switching to VMware Player or Virtual Box.  Once I got IT support out to install VMware Player and Kubuntu, all of my problems disappeared and I'm able to virtualize Kubuntu without any problems at all.

---

### Post by japzone on 2012-01-13
try running in the prompt:
```
startx
```
That should launch the GUI. Also make sure your giving enough RAM and other resources to the VirtualMachine. If your limited on what you can give it try the Alternative Install ISOs many distributions provide or even use a Less-Resource hungry Distribution like **Lubuntu**.

But I agree with **drmrgd**, Virtualbox or VMware will probably work much better with Linux installs. I personally use Virtualbox and never have problems.

Also if it's your own Computer you could give WUBI(Windows Installer) a try. It Installs Ubuntu to a Virtualdisk so you don't Partition your Drive, and allows you to Boot your Computer into Ubuntu. Once your done with it, Uninstall it from within Windows just like a program. It suffers some performance because it's running off a Virtual Disk instead of a real one, but it'll definitly Perform better than running Ubuntu inside a VM inside Windows.

---

