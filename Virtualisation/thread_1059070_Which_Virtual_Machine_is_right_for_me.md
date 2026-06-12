---
title: "Which Virtual Machine is right for me?"
date: 2009-02-03
forum: Virtualisation
---

### Post by shally87 on 2009-02-03
HI,
I have a PC with 1gb ddr2 ram, intel dual core 1.6 processor, asus x series mother board and 160gb hdd.
I want to make this pc as my experiment live server to host a website. 
So as  I know I need to install LAMP server, DNS server, Mail Server, Samba File server and LAMP server with dev environment. 

But one thing that i have to make sure, with this one pc and lo specification, **what Virtual Machine should i install?** and **Do i need to install 5 OS to host the 5 server that i want to install?**

I prefer a easy to use Virtual Machine.

---

### Post by HotShotDJ on 2009-02-03
> **shally87 said:**
> HI,
I have a PC with 1gb ddr2 ram, intel dual core 1.6 processor, asus x series mother board and 160gb hdd.
I want to make this pc as my experiment live server to host a website. 
So as  I know I need to install LAMP server, DNS server, Mail Server, Samba File server and LAMP server with dev environment.I don't have any experience with servers... so I'll let somebody else handle that part.  However, I have a concern regarding your hardware.  I really don't think you've got enough RAM to do what you want.  My past experience is that 2 Gig RAM is really the minimum for virtualization (and that is for desktop work.  Servers are a completely different animal.) -- remember, you have to 1) Assign enough RAM to the VM so that it can run the guest OS along with all the software you'll be running, and 2) Leave enough RAM for the host OS to run.  Thats a pretty tall order with only 1 Gig of physical RAM to divide up.

I know that VirtualBox is usually a very good choice for desktop work.  I wonder, though, if something like VMWare Server might be a better choice for your needs.  Again, you should probably wait for somebody with some server experience to chime in.

---

### Post by shally87 on 2009-02-03
Ok, I guess it's time to change to 2x2gb ram for my pc.. Hope it can run well..

---

### Post by crazyone on 2009-02-04
well if u want a server for what u need u can assign only 512mb ram to the server and it will run fine as long as u dont install a gui for it. as for vm programs if u want access to it i have found vmware server to be the best but if u jsut want internet threw nat use virtualbox becuase it is in the repos. hope this helps

---

### Post by shally87 on 2009-02-07
Thanks Crazyone, 
BTW, i need to divide my pc server to different virtual machine. 
1. LAMP
2. DNS Server
3. Email Server
4. Samba File server (not really needed)
5. LAMP (Dev environment)
So to avoid a crash from one server cause the whole system to crash, I might need VM.
VMware might be a choice but how good is it? After installing it do i need a Virtual Box to get different ip?

---

### Post by crazyone on 2009-02-07
it to me is fast. and it uses a web gui to manage it. to get ips it is jsut setting up a bridge network during the install which is what i do sense i have my server wiht multiple vms on it for the same reason

---

### Post by Ng Oon-Ee on 2009-02-08
Just a question, why do the servers have to be virtualized? I know all the above functionalities can be implemented within Linux (Ubuntu), in most cases its more secure and reliable that way, even.

EDIT: Ah, I saw the part about crash-proofing. Well, in that case OpenVZ may be good, the wikipedia states that 768 MB of RAM could support 120 VMs. Basically its a modified kernel that can run many Linux-based OSes at the same time.

I don't think you'd want VMWare/VirtualBox, except that they're easy. Considering you're setting up five different servers (a non-easy task in itself) I believe your technical proficiency would be sufficient to setup an OpenVZ kernel and script the routines for it. The overhead is very much less than for VirtualBox/VMWare (which are actually running a separate OS for each instance, and even the relatively memory-efficient WinXP is constantly leeching an average 10% of my CPU when on in RDP mode.). Consider also that each virtual Windows machine needs to be running its own SOFTWARE-BASED firewall and anti-virus which would tax the system. Unless, of course, all 5 VMs connect through connection sharing on your main machine and the firewall is done there, but you'd still need antivirus....

---

