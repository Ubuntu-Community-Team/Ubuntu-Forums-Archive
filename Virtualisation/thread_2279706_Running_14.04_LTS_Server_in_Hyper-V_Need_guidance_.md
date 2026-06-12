---
title: "Running 14.04 LTS Server in Hyper-V: Need guidance for configuring the networking"
date: 2015-05-25
forum: Virtualisation
---

### Post by Chris of Arabia on 2015-05-25
I'm running an Ubuntu 14.04 LTS LAMP server on Hyper-V,  which itself is running under Windows 8.1. When I first set it up on my  usual home network, I set it up with an 'External' virtual switch (VS1)  which connected the VM to my laptop's NIC, and made the server available  around the rest of the network as 192.168.6.42. So far, so good and having got that far, I successfully installed a copy of the b2evolution CMS, which I could then access, not only from Win8.1 via a browser on 192.168.6.42/b2evolution.


  Fast forward a week or so, and I needed to take the laptop into the  office, where there was no WiFi available initially. I tried connecting  to the copy of b2evolution I'd installed when all was well, but the  browser was no longer able to find the server and gave me the message  "This web page is not available". Whilst eventually, I found myself a  WiFi feed, the IP range wasn't what the server was used to seeing, and I  still couldn't get connected. 

Taking it back home didn't improve matters - I could still not get a  connection despite the laptop being back on its usual IP address. The end result of the above was that I ended up re-installing b2evolution, with it picking up an IP address based on what the laptop's NIC was assigned. Where I am now, it's using 192.168.0.13 and b2evo is working just fine again. The problem will come when I take the laptop elsewhere, as I'll need to do shortly.

What I need to understand is the best approach to configuring Hyper-V and the Ubuntu VM on it, so that I can target a single IP address and/or computer name, regardless of where the laptop is, or IP address its NIC picks up. 

Anyone care to offer suggestions?

---

### Post by KillerKelvUK on 2015-05-26
Hey Chris of Arabia, it sounds like your problem is related to the networking component of Hyper-V and how addressing is managed by the virtual switch and the virtual machines it connects ergo the culprit isn't the Ubuntu OS within your virtual machine as this could easily be a Windows OS and it would have the same issues.  As such I'd suggest you also post in a Hyper-V / MS Community forum as this area on ubuntuforums.org is about virtualisation using linux based hypervisors e.g. KVM, Xen, Virtualbox +others.  I'm sure some of the more experienced users & mods here may know Hyper-V but I suspect you may have better support from a more dedicated community.

That said in the spirit of openness...
[LIST=1]
[*]How is your virtual switch (VS1) set up, i.e. when you say it "...connected the VM to my laptop's NIC..." do you know what method it used e.g. bridging, NAT any-other buzzwords you can see in the tooling used to create VS1?
[LIST]
[*] In your home environment before everything went wrong was the 192.168.6.42 address that of your Hyper-V host (laptop) or the Ubuntu guest or both?
[/LIST]

[*]Do you require access to the Ubuntu guest running [COLOR=#000000]b2evolution from only the host device or from elsewhere on a local network?[/COLOR]
[*][COLOR=#000000]&#8203;Is the Ubuntu guest configured to get IP addresses dynamically or have you applied a static address?[/COLOR]
[/LIST]
[COLOR=#000000]
From your answers we maybe able to steer you on either the Hyper-V config or at least the topics you need to research.
[/COLOR]

---

