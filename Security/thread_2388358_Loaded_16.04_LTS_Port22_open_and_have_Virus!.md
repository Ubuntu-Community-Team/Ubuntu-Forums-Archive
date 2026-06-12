---
title: "Loaded 16.04 LTS Port22 open and have Virus!"
date: 2018-04-01
forum: Security
---

### Post by ence on 2018-04-01
Hello 
After reloading Ubuntu 16.04 last month I looked at router logs user root killed 61.177.172.130 - ISP:China Telecom
Went to ShieldsUP showed that port 22 was open. 

Was port made to be open from the Ubuntu ISO or is this down to my router.

I then loaded ClamTK and ran showed I have possible threats: 58 most if all PUA.Doc Tool LibreofficeMacro-2 

Is this a real threats photos below?
Thanks

[IMG]https://ibb.co/nv1ph7[/IMG]
[IMG]https://ibb.co/ekG3aS[/IMG][IMG]https://ibb.co/nv1ph7[/IMG]

---

### Post by TheFu on 2018-04-01
Ubuntu doesn't enable a firewall since the normal install doesn't include any listeners.  If you install openssh-server, then that does enable the ssh service. The default port for ssh is 22/tcp. Securing any service is your responsibility.

Unless your router is hacked or you opened the router ports to forward ssh traffic to your computer, I can't think of any way someone would get in.  Routers need to be patched at least quarterly.  If patches aren't available that often, there are likely issues with the router that can be exploited.  Last spring, there were a few remote access bugs in all versions of Linux, including Android and routers based on Linux.  I think there were some last fall too ... so if you haven't patched since then, it is very possible that your router has been hacked.

As for ssh ... securing ssh against brute force attacks isn't too hard. fail2ban will do that, but it should be the last defense. A correctly configured router and correctly configured sshd that prevents all remote root access should happen first.
[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) is my take on this. Summary is:
* don't allow remote root
* don't allow password logins from the internet
* don't allow brute-force attacks. 
* use a non-standard port on the WAN/internet side. This is a router setting.
* monitor attacks

Can't read the images - poor eyesight.  If you post text, not images, someone might be able to help.

---

### Post by deadflowr on 2018-04-01
*Thread moved to **Security***

---

### Post by ence on 2018-04-01
Thanks 
Additional info 


I did & do have firewall and it's enabled, didn't open or load ssh service. 
Did make a rule in firewall to deny in & out of port 22 but once I re-scan with ShieldsUP still shows as open!

So this is down to my router then Ubuntu.
Lager image loaded as no text. 


Thanks for link got some reading to do.

---

### Post by TheFu on 2018-04-01
If you don't run ssh on the ubuntu system, then the router is probably hacked.  Consumer routers are next to impossible to maintain.

Firewall rules that completely block a service probably aren't useful. Just remove the package if you don't want it.  There is a firewall on most routers AND there is a firewall built-into Linux.  Use both.

---

### Post by ence on 2018-04-01
Thanks

---

### Post by ence on 2018-04-01
Thanks 
Just looking how to do from website, don't think I have synaptic package manager,

Loaded now :)

From synaptic package manager SSH is not loaded.
OpenSSH now removed.


Time to look for new router?

---

### Post by TheFu on 2018-04-01
> **ence said:**
> Thanks 
Just looking how to do from website, don't think I have synaptic package manager,

Any package manager works. APT is APT, so apt, apt-get, aptitude, synaptic, all should work. The tool used to access it generally doesn't matter, though "software center" may be too stupid to show some packages you might want.  I use "apt" usually, and aptitude when I need more detailed controls.  I haven't used any GUI package manager in years - maybe 8.

Same applies (mostly) to Linux firewall interfaces. ufw, iptables, gufw, and a few others are just interfaces into the kernel firewall. Best to pick one and stay with it.

---

### Post by HermanAB on 2018-04-02
If you don't want port 22 open, then stop the SSH daemon.  Blocking it in the packet filter is redundant/inefficient.

---

### Post by ence on 2018-04-02
All this is like another language.
Hello Google 

Thanks all

---

### Post by SeijiSensei on 2018-04-02
> PUA.Doc Tool LibreofficeMacro-2 

Is this a real threats?

No. It's what Clamav calls a "potentially unwanted application" and can be ignored. See [http://www.clamav.net/documents/potentially-unwanted-applications-pua](http://www.clamav.net/documents/potentially-unwanted-applications-pua)

Linux suffers from few "viruses" of note.

I use "consumer" routers. They're usually not a problem.

---

### Post by TheFu on 2018-04-02
> **SeijiSensei said:**
>  I use "consumer" routers. They're usually not a problem.

[https://www.tomsguide.com/us/home-router-security,news-19245.html](https://www.tomsguide.com/us/home-router-security,news-19245.html)

[https://www.theregister.co.uk/2017/04/14/new_critical_linux_kernel_flaw/](https://www.theregister.co.uk/2017/04/14/new_critical_linux_kernel_flaw/)

These sorts of critical flaws have been happening about every 6 months.

---

