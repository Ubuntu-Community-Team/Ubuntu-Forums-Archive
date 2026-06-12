---
title: "Ubuntu 11.10 through VirtualBox Install Help"
date: 2012-02-09
forum: Virtualisation
---

### Post by LinuXofArabiA on 2012-02-09
Hello Everyone,

I am trying to install Ubuntu 11.10 on my VirtualBox. I downloaded the source file onto my computer, and simply located that file as the installation (bootable) file when asked to in the installation step. The installation didnt complete, giving me an error message about not being able to boot. The installation was aborted. Any tips?

---

### Post by japzone on 2012-02-09
> **LinuXofArabiA said:**
> Hello Everyone,

I am trying to install Ubuntu 11.10 on my VirtualBox. I downloaded the source file onto my computer, and simply located that file as the installation (bootable) file when asked to in the installation step. The installation didnt complete, giving me an error message about not being able to boot. The installation was aborted. Any tips?
Do this:
VM Settings-->Storage-->IDE Controller-->Add CD/DVD Device-->Choose disk
Now Simply Browse to the Ubuntu ISO file.

After that make sure all the other VM settings are to your liking and then "Start" the VM. It should boot and the Ubuntu Installer should appear..

---

### Post by LinuXofArabiA on 2012-02-09
Hello japzone. I think you got me all wrong. What I am trying to do is the other way round. I already have VirtualBox, and I am trying to install Ubuntu Oneiric virually on my computer. 

Thanks

---

### Post by japzone on 2012-02-09
> **LinuXofArabiA said:**
> Hello japzone. I think you got me all wrong. What I am trying to do is the other way round. I already have VirtualBox, and I am trying to install Ubuntu Oneiric virually on my computer. 

Thanks

Yeah sorry about that, I edited my post to the Correct Answer. I mistook what you were trying to do during my first Read Through of your Post.

---

### Post by larrypg on 2012-02-09
Hello,

What I had to do was play with the install updates and install third party.  If one did not work then I would uncheck it and go with another.  I think (not sure though) that I chose install updates but not third party software.

---

### Post by japzone on 2012-02-09
> **larrypg said:**
> Hello,

What I had to do was play with the install updates and install third party.  If one did not work then I would uncheck it and go with another.  I think (not sure though) that I chose install updates but not third party software.
All that does is tell Ubuntu whether it should install things like Flash and other non-OpenSource software. Doesn't effect anything except how much Hard Drive space is used.

---

### Post by larrypg on 2012-02-09
Well I am  glad it does not effect anything...pretty sure that deciding if you should install updates now or later might have something to do with other than just drive space.  Come to think of it I am pretty sure that install third party software might have something to do with other than hard drive space used. Might even be because I experienced the exact same problems.

---

### Post by japzone on 2012-02-09
> **larrypg said:**
> Well I am  glad it does not effect anything...pretty sure that deciding if you should install updates now or later might have something to do with other than just drive space.  Come to think of it I am pretty sure that install third party software might have something to do with other than hard drive space used. Might even be because I experienced the exact same problems.

Installing Updates might cause problems because something incompatible is installed by mistake(abridged version). I usually just install without connecting to the Net then install updates later so I can be sure if I need something or not.

---

### Post by LinuXofArabiA on 2012-02-09
Thank you everyone for your input. I completed the installation and it is up and running. The problem was actually that I had allocated too much RAM for the virtualOS (more than 75%) of my physical RAM!:-?

I marked the thread as solved.

Thanks

---

### Post by japzone on 2012-02-10
> **LinuXofArabiA said:**
> Thank you everyone for your input. I completed the installation and it is up and running. The problem was actually that I had allocated too much RAM for the virtualOS (more than 75%) of my physical RAM!:-?

I marked the thread as solved.

Thanks

You might want to consider upgrading your RAM. It's pretty cheap these days and if you install the Ubuntu PAE Kernal you will then be able to use up to 4gb of RAM(Although you may see less then that in Ubuntu as some of it will be used for behind the scenes stuff)

---

