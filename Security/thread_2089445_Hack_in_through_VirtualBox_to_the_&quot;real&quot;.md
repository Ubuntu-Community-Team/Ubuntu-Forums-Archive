---
title: "Hack in through VirtualBox to the &quot;real&quot; system."
date: 2012-11-29
forum: Security
---

### Post by kleenex on 2012-11-29
Hi, is there any chance, that somebody can hack in to the Linux machine through VirtualBox? Let say, that I am running Linux 1, I've installed VBox and on VBox another Linux 2 distro. Is there any chance, that during using Linux 2 via VBox, Linux 1 host system can be hacked? If so, how?

I'm asking, because I'm planning to install VBox and test some others systems etc.

Thanks.

---

### Post by haqking on 2012-11-29
> **kleenex said:**
> Hi, is there any chance, that somebody can hack in to the Linux machine through VirtualBox? Let say, that I am running Linux 1, I've installed VBox and on VBox another Linux 2 distro. Is there any chance, that during using Linux 2 via VBox, Linux 1 host system can be hacked? If so, how?

I'm asking, because I'm planning to install VBox and test some others systems etc.

Thanks.

it depends, the answer is both yes and no, like everything security is a process not a product.

If you have a VM which is acting a live client on the network with shares and using shares, using shared folders to host machine then in theory yes as there is access to the host.

if you however minimise the access to host and network then you reduce the risks.

it is a possibility but still not a common one so not too much to worry about, but as i say as with everything contol ingress and egress

There are some known vulnerabilites been patched but shows potential such as cloudburst [http://www.darkreading.com/security/news/217701908/hacking-tool-lets-a-vm-break-out-and-attack-its-host.html](http://www.darkreading.com/security/news/217701908/hacking-tool-lets-a-vm-break-out-and-attack-its-host.html)

There are new techniques emerging daily, unless you unplug you are never "secure" you can only take steps to make it harder to breach.

Peace

---

### Post by Hungry Man on 2012-11-29
Sure. Virtual Machines are very complex systems. Whereas your typical operating system has its own set of bugs a VM should (if it's emulating perfect) have all of those bugs as well. Because no emulation, no program, is perfect the VM should share bugs while still maintaining its own set of bugs.

This added complexity makes VMs actually a somewhat poor choice for security outside of malware analysis and very specific use cases.

Very little malware 'in the wild' is going to attempt to break out of a VM, most will just shut down to avoid analysis. But if your question is about whether or not it is possible, it is very possible.

---

### Post by kleenex on 2012-11-29
Hi **haqking** and **Hungry Man**. If I will install VBox, certainly a system in it will not be exposed to the world with any services etc. So, if there will be no open ports, services such as Apache etc. the risk is similar?  Of course all the updates also will be installed. 

Hmm, now I'm very seriously considering whether install or not to install ;-)

---

### Post by Hungry Man on 2012-11-29
If any operating system has no open ports it's going to be pretty secure, barring special vulnerabilities.

---

### Post by pkadeel on 2012-11-29
> **kleenex said:**
> Hi **haqking** and **Hungry Man**. If I will install VBox, certainly a system in it will not be exposed to the world with any services etc. So, if there will be no open ports, services such as Apache etc. the risk is similar?  Of course all the updates also will be installed. 

Hmm, now I'm very seriously considering whether install or not to install ;-)
The actual situation is not that serious specially when the guest is not exposed to the Wild Wild Web.

On the contrary to what others say, I consider virtual machine more secure because the concept of virtual machine is similar to a sandbox and whatever I do inside it does not affect my host system unless you share system folders of the host with read/write permissions. But it is just my thinking and can be wrong.

---

### Post by kleenex on 2012-11-29
Hi **pkadeel**. True, VBox seems to be like a sandbox. So, maybe I will decide to install VBox. Thanks for all answers!

---

### Post by SeijiSensei on 2012-11-29
> **kleenex said:**
> Hi **haqking** and **Hungry Man**. If I will install VBox, certainly a system in it will not be exposed to the world with any services etc. So, if there will be no open ports, services such as Apache etc. the risk is similar?  Of course all the updates also will be installed.

In this model just who would be attacking the server in the manner you describe?  Is the host OS exposed to the Internet?

If you plan to the VM in the standard "NAT" mode, then the VM guest is hidden behind the host in much the same way LAN clients behind a masquerading firewall are hidden.  

I don't think there is much to worry about here.

---

### Post by kleenex on 2012-11-29
Hi **SeijiSensei**. For now I'm planning to do only some tests. Nothing big. Host OS is not exposed to the Internet.

---

### Post by Ms. Daisy on 2012-11-29
> **haqking said:**
> it depends, the answer is both yes and no, like everything security is a process not a product.

If you have a VM which is acting a live client on the network with shares and using shares, using shared folders to host machine then in theory yes as there is access to the host.

if you however minimise the access to host and network then you reduce the risks.

it is a possibility but still not a common one so not too much to worry about, but as i say as with everything contol ingress and egress

There are some known vulnerabilites been patched but shows potential such as cloudburst [http://www.darkreading.com/security/news/217701908/hacking-tool-lets-a-vm-break-out-and-attack-its-host.html](http://www.darkreading.com/security/news/217701908/hacking-tool-lets-a-vm-break-out-and-attack-its-host.html)

There are new techniques emerging daily, unless you unplug you are never "secure" you can only take steps to make it harder to breach.

Peace OMG haqking stepped out of the shadows! \o/

@ kleenex: Maybe if you describe what you plan to test with some more detail you'll get a better answer.  But even if the guest is bridged, the likelihood of guest-to-host break-out is pretty slim. Can you even create a canned exploit for such a thing? Seems like there are way too many variables- you'd have to create a unique attack on each system. --> the cost of exploitation is pretty high.

---

### Post by kleenex on 2012-11-30
Hello **Ms. Daisy**. I decided yesterday, that at the beginning I would like to test (improve) firewall for a small network with ~30 computers, of course Squid etc.

---

### Post by coldraven on 2012-11-30
[I]For some good info about networking in Virtualbox  go here and click on the image of issue 61 to download it  
[http://fullcirclemagazine.org/issue-61/](http://fullcirclemagazine.org/issue-61/)  
Then read from page 15 onwards.

I found this to be easy to understand, I hope it helps you.
[/I]

---

### Post by haqking on 2012-11-30
as said already, it is possible, not as common though.

As with everything, nothing is completely secure unless no sharing is done and no connection to outside world happens.

read here for some more information:

[http://www.infosecisland.com/blogview/10047-Hacking-Virtual-Machines-pt-4-Targeting-a-Virtual-Machine.html](http://www.infosecisland.com/blogview/10047-Hacking-Virtual-Machines-pt-4-Targeting-a-Virtual-Machine.html)

There have been exploits that have been patched over the years, and as always there will be more to come and until they are patched then they allow attack.

Turn off connectivity, and if as you say nothing is connected to outside world then you have no problem, hackers wont come in through the AC~  ;-)

Peace

---

### Post by haqking on 2012-11-30
> **Ms. Daisy said:**
> OMG haqking stepped out of the shadows! \o/

@ kleenex: Maybe if you describe what you plan to test with some more detail you'll get a better answer.  But even if the guest is bridged, the likelihood of guest-to-host break-out is pretty slim. Can you even create a canned exploit for such a thing? Seems like there are way too many variables- you'd have to create a unique attack on each system. --> the cost of exploitation is pretty high.

Hi Ms Daisy,

I am back from my online community/forum sabbatical ;-)

Are you excited ? LOL

---

### Post by CharlesA on 2012-11-30
> **haqking said:**
> Hi Ms Daisy,

I am back from my online community/forum sabbatical ;-)

Are you excited ? LOL
Woot!

@OP: Haqking and others have covered pretty much everything. It is possible to break of the VM but it is unlikely unless you have that VM directly exposed to the internet.

---

### Post by Ms. Daisy on 2012-11-30
> **haqking said:**
> Hi Ms Daisy,

I am back from my online community/forum sabbatical ;-)

Are you excited ? LOL
Well yeah, hence the \o/
:P

---

