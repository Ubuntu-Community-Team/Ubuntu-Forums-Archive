---
title: "Virtual box affect security?"
date: 2009-10-09
forum: Security
---

### Post by Camilia on 2009-10-09
Recently read that there is a BANKING TROJAN HORSE that doesn't just steal your bank log-in credentials but actually steals money from your account while you are logged in and displays a fake balance. The Trojan runs an executable only on Windows systems.

Now I have a CD written for windows. I am unable to view in ubuntu. Been advised to use virtual box. Read info on virtual box but still uncertain if I have windows software in virtual box if it will affect security. 

Will having windows xp in virtual box affect security?

---

### Post by undecim on 2009-10-10
If VirtualBox gets infected by a virus, it won't be able to spread to the rest of your system, but it will be able to access other hosts on the network and potentially infect more windows PCs. Also, anything you do it that VB system can be compromised by the virus, but other than that, there is little a virus in a virtual machine can do (this is what is called "security by isolation" -- The VirtualBox system is isolated from the rest of the system. It's one of the reasons that virtualization has become popular)

---

### Post by rookcifer on 2009-10-10
It should be noted that virtualization is not a magic bullet for security.  There are already Xen hypervisor exploits that allow an attacker to "break out" of a virtual machine and attack the physical machine.  Of course, I know of no "viruses" or malicious scripts that do this automatically, but I see no reason why it couldn't be done.

SeLinux and AppArmor can be used to stop these virtual machine "break outs."  Google for libsvirt for some info.

---

### Post by Chayak on 2009-10-10
It's a common practice in the security research field to run malware in VMs.  I do it every day I'm at work.  There are quite a few that's gone so far as to compartmentalize their systems by keeping the base OS install as slim and locked down as possible and doing every day activities inside of VMs.

As for breaking out of VMs I haven't heard of it being used in the wild yet, just in controlled lab enviornments.

---

### Post by Camilia on 2009-10-24
> **Chayak said:**
> It's a common practice in the security research field to run malware in VMs.  I do it every day I'm at work.

What malware did you dowload? How do you do it?  Is it safe to just start the virtual box with windows restore os disk?

---

### Post by cariboo on 2009-10-25
When running a vm, the first thing I do after the install is finished to my liking is to take a snapshot, that way I can revert back to a clean install when needed.

---

### Post by Chayak on 2009-10-25
> **Camilia said:**
> What malware did you dowload? How do you do it?  Is it safe to just start the virtual box with windows restore os disk?

I do malware research so I purposely infect VMs.  You set up the machine the way you want, take a snapshot, and then go about whatever work you do.  When your're done you revert to that known clean state.

---

### Post by unspawn on 2009-10-25
> **Chayak said:**
> I do malware research so I purposely infect VMs.
The mcrsft side of things or GNU/Linux? 
//Apologies to the OP for my OT post.

---

### Post by update_manager on 2009-10-25
> **Camilia said:**
> Recently read that there is a BANKING TROJAN HORSE that doesn't just steal your bank log-in credentials but actually steals money from your account while you are logged in and displays a fake balance. The Trojan runs an executable only on Windows systems.

Now I have a CD written for windows. I am unable to view in ubuntu. Been advised to use virtual box. Read info on virtual box but still uncertain if I have windows software in virtual box if it will affect security. 

Will having windows xp in virtual box affect security?

If the virtual box client has access to your bank stuff, and it gets infected the virus/worm/malware could have access to the banking information.

---

### Post by slowth5 on 2009-10-25
> **Chayak said:**
> There are quite a few that's gone so far as to compartmentalize their systems by keeping the base OS install as slim and locked down as possible and doing every day activities inside of VMs.

[http://www.tomshardware.com/reviews/joanna-rutkowska-rootkit,2356.html](http://www.tomshardware.com/reviews/joanna-rutkowska-rootkit,2356.html)

This is a great article. She uses multiple VMs, each with a specific security privilege.

---

