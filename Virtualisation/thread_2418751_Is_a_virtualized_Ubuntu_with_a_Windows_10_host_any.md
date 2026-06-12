---
title: "Is a virtualized Ubuntu with a Windows 10 host any more secure than Windows 10?"
date: 2019-05-10
forum: Virtualisation
---

### Post by AbleTassie on 2019-05-10
Is a virtualized Ubuntu with a Windows 10 host any more secure than Windows 10? 

In other words, if you browsing the internet e.g., with Ubuntu (or Mint or Lubuntu) that is virtualized using Virtualbox with Windows 10 as the host OS, is this anymore secure in terms of viruses,etc. than just browsing the internet with the host OS, Windows 10?

Thanks,

A.

---

### Post by Frogs Hair on 2019-05-10
Windows viruses won't run on Ubuntu , but browser exploits are often cross platform. The security of vbox hosted on Windows is really a Windows security question.

---

### Post by TheFu on 2019-05-11
Perhaps. Perhaps not.  IMHO, it depends on the network architecture used.
If both systems are available over the internet, then no, it is not more secure.

I don't believe there is any way to secure a Windows server or desktop against network attacks.  

With the popular Linux desktops, as long as you don't enable services to other systems, then the security is much better.  That isn't to say that Linux desktops are always secure if there aren't any services running. There have been attacks possible, over the network, without running any services, against Linux systems.  Almost always, those sorts of attacks are fixed before their existence is widely known.  Stay patched and avoid visiting the dangerous parts of the internet.

If you are a little more paranoid, then don't allow javascript and don't use any plugs, especially video ones, inside the browser.  For most desktops, the browser and email programs are the primary attack vectors.

Hopefully, some other opinions will come.

---

### Post by AbleTassie on 2019-05-13
Thanks Fu and Froghair for your opinions. So if I understand correctly what you are saying Fu, if you make your browser as secure as possible and don't click on suspicious emails, don't use any browser plugins, then you think a Virtualized Linux like Mint or Lubuntu (with Windows 10 as a host). Is more secure than the same situation & practices with Windows 10 alone, correct?

**Aside:** Fu when you say: *"If both systems are available over the internet"* I think you mean:* if Windows is somehow accessible to the internet (either through the virtualized Linux or otherwise)*, correct?

Thanks,

A.

---

### Post by TheFu on 2019-05-13
I don't believe it is possible to have any secure system with Windows as the hostOS.

I would never allow Win10 on my network. It is particularly bad for privacy and network security, IMHO. When they started pushing ads and demanded access to computer data without any way to disable their data collection by end-users, I knew MSFT was off the network.  I've read their EULA for Win10 and couldn't agree to the terms. I cannot imagine ever agreeing to those terms. When I agree to a contract, I intend to honor it.

---

### Post by AbleTassie on 2019-05-16
Thanks Fu and Frogs Hair.

A.

---

### Post by Skaperen on 2019-05-16
if it were me, i'd stack it the other way ... Ubuntu on the bottom.  no idea how Windows licensing reacts to that.  OTOH, i have no case to find out.

---

### Post by SeijiSensei on 2019-05-16
I run Win7 in a VirtualBox VM on top of Kubuntu 19.04.  Having Windows as the guest OS rather than the host has a number of advantages. First, Ubuntu is much less vulnerable when exposed to the Internet than Windows.  If you run the virtualized Windows in "NAT" mode, so all of its network transactions are proxied through the host, then the Windows host is invisible to external threats.  (Doing stupid things like opening random links to malware in email is obviously not prohibited by using virtualization.)  

The other advantage of virtualized Windows is that you can take a "snapshot" of the installation at any time and revert to it should disaster strike. So I'd build a clean implementation of Windows in the virtual machine, run Windows Update, install the software you need, then take a snapshot and store it in a safe location.

I hardly ever use my Windows VM for anything having to do with the Internet. I use Ubuntu for all my browsing, email, and other tasks, and use Windows only for proprietary things like my tax software and Microsoft Access.

If you intend to use Windows for gaming, this approach won't work for you.  Games typically require direct access to the video hardware rather than the emulated video adapter provided by the virtualization system.

---

### Post by TheFu on 2019-05-16
> **SeijiSensei said:**
>  
If you intend to use Windows for gaming, this approach won't work for you.  Games typically require direct access to the video hardware rather than the emulated video adapter provided by the virtualization system.

It is possible to passthru a GPU to the Windows VM using VT-d and IOMMU.  I understand the configuration is much easier these days than it was 5+ yrs ago, but it only works with specific motherboards and specific GPUs and requires having 2 GPUs physically inside the machine.  If you have an Intel CPU with on-board graphics, that would typically be used by the Host Linux OS and the hot AMD or nVidia GPU would be passed through to the Windows VM.  KVM is the normal hypervisor used for this.  Gamers claim over 95% of native performance doing this.

Google "kvm gpu passthru" for more details.
[https://forums.linuxmint.com/viewtopic.php?t=212692](https://forums.linuxmint.com/viewtopic.php?t=212692) is a how-to guide. Expect to spend a few hours setting this up, assuming all your current hardware is perfect.

---

### Post by SeijiSensei on 2019-05-16
Thanks, but I have a native Windows machine if I want to play games. That's more or less its only purpose in life.

---

### Post by AbleTassie on 2020-03-16
Thanks to everybody. I think you answered my questions and I will mark this thread a SOLVED.

A.

---

