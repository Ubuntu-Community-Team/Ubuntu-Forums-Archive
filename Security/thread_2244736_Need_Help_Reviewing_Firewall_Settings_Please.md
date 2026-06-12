---
title: "Need Help Reviewing Firewall Settings Please"
date: 2014-09-18
forum: Security
---

### Post by dexz2 on 2014-09-18
Hello

I am in the process of trying to properly configure my firewall. As you can see from the image, I have denied both ingoing and outgoing access with the exceptions of http, https and dns ports and from a practicality perspective, this seems to work just fine.

However, after doing some testing using commands such as ```
sudo watch -d netstat -atnp
``` and ```
sudo nmap 127.0.0.1 
``` I initially found an open cups port! of which I closed by disabling the service and blocking it from loading on reboot. My first question is why was this open by default? Was it because nmap detected it on localhost only? Would that have been perceived as being open if someone else tried nmaping my ip address? Bare in mind this was done whilst also technically blocking the port with my iptables config. 

Furthermore, looking at the gufw listening report, there seems to be a fair amount of things listening. Now obviously, I had chrome open when I conducted this test as well as having dropbox installed on my pc. But what about the others? Why are they listening on a default Ubuntu install? Are they needed? If so, why? and if not, how can I go about disabling them? For reference, this computer is being used for simple work related tasks such as browsing the web, and typing up documents. I have no use for printers or scanning services however.

Also, if you happen to know of any easy to implement system hardening measures, then I would greatly appreciate you sharing this information.

Thanks for your time.

[[IMG]http://s16.postimg.org/ekowodx29/Screenshot_from_2014_09_18_14_44_44.jpg[/IMG]]("http://postimg.org/image/ekowodx29/")

---

### Post by cariboo on 2014-09-18
You are going about this the wrong way, any services open on 127.0.0.1 are not accessible from outside. You need to test for open ports using a second system on your internal network.

---

### Post by dexz2 on 2014-09-18
> **cariboo907 said:**
> You are going about this the wrong way, any services open on 127.0.0.1 are not accessible from outside. You need to test for open ports using a second system on your internal network.

Oh, I see. Thanks. How do I go about this? Do I just nmap my computers ip address from another device?

---

### Post by cariboo on 2014-09-18
> **dexz2 said:**
> Oh, I see. Thanks. How do I go about this? Do I just nmap my computers ip address from another device?

Yes you can run nmap from any other computer on your home network, whether it's running WIndows Mac or a Linux distribution.

---

