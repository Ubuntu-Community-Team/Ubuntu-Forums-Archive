---
title: "VirtualBox fails on ubuntu 12.04"
date: 2012-03-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by odror on 2012-03-14
I have installed Virtualbox on my machine.

I get the following cryptic error message when I try to run Virtualbox

Error opening file for reading: Permission denied

I have added my name to vboxusers. it did not help.

"sudo Virtualbox" run just fine. with no error. Can someone tell me which file needs permission. or where can I find the answer

Thanks

---

### Post by bcarlowise on 2012-03-15
Can't say that I have ever seen issues starting virtualbox. I have it installed and working on both 11.10 and 12.04 with no problems. You're getting the error when trying to launch the virtualbox application or one of your VM's? If you're getting the error when trying to launch virtualbox I would recommend just uninstalling, rebooting and reinstalling.

---

### Post by odror on 2012-03-15
> **bcarlowise said:**
> Can't say that I have ever seen issues starting virtualbox. I have it installed and working on both 11.10 and 12.04 with no problems. You're getting the error when trying to launch the virtualbox application or one of your VM's? If you're getting the error when trying to launch virtualbox I would recommend just uninstalling, rebooting and reinstalling.

Yes I get the error when I was trying to launch. I did not get the menu that will enable me to import my machine from the 11.10 machine. I used The ubuntu package. May be I need to use the one from oracle?

Thanks

---

### Post by bcarlowise on 2012-03-15
> **odror said:**
> Yes I get the error when I was trying to launch. I did not get the menu that will enable me to import my machine from the 11.10 machine. I used The ubuntu package. May be I need to use the one from oracle?

Thanks

I use VirtualBox that comes in the Ubuntu Software Center so I don't think you need to use the Oracle version. Have you tried uninstalling it, rebooting and reinstalling?

---

### Post by odror on 2012-03-16
I have re-installed. I got the same error, basically only the root user can use the Virtualbox.

---

### Post by melenanyma on 2012-04-23
Out of the blue same error here. Can't do a thing with virtualbox anymore. 
Just this error

---

### Post by thatguruguy on 2012-04-23
I can't replicate your error. It still strikes me as a user permissions problem.

---

### Post by neu5eeCh on 2012-04-23
Make sure you make yourself a member of the following groups:

vboxusers, lp and users.

Not knowing about "lp" really cramped my style when I was first using virtualbox. Also, the only reason to use the Oracle version (which I use) is for USB connectivity.

---

### Post by tehowe on 2012-04-23
> **VTPoet said:**
> Make sure you make yourself a member of the following groups:

vboxusers, lp and users.

Not knowing about "lp" really cramped my style when I was first using virtualbox. Also, the only reason to use the Oracle version (which I use) is for USB connectivity.

Aha... thanks for mentioning that. I'd everything else working okay, even the somewhat glitchy support for the Aero application rolodex display. The 'extensions' and guest drivers iso's were duly imported, but I could never see any USB devices attached. Is it something that got fixed just after Precise's application freeze?

---

