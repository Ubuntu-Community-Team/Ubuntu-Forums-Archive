---
title: "Linux firewall on DSL home network"
date: 2008-03-04
forum: Security Discussions
---

### Post by FastZ on 2008-03-04
Hey Guys, I have a DSL internet connection here at my house and I want to protect my networking using an old computer I had laying around that I will install Smoothwall on to create a hardware firewall.

Here is what my network looks like.  Currently, the DSL line comes in and connects to a DSL wireless AP/router, then I have the family desktop connected to the 4-port switch on the DSL AP.  Then I have a Linksys WRT54G with DD-WRT installed in my office that is configured as a client-bridge so I didn't have to run any extra cabling from the family room into here.  In my office, I have two computers connected to the Linksys client-bridge.  There are up to three laptops that are used in various spots of this house that need to use the wireless signal being broadcast from the DSL AP/router.  

What I want to do is take this firewall and place it between the actuall DSL connection coming into the house and the DSL AP/router.  

I understand that I will need a DSL modem installed on the red interface of the firewall, but what I don't know is whether I can still use my DSL AP/router on the green side.  Is this possible or will I need to have an Ethernet NIC on the green side and use one of my other Linksys Ethernet APs to provide the wireless and connection to the family computer?

Would it be possible to install two DSL modem PCI cards in my firewall, one red, one green, and route the DSL connection through the red and out the green and back into the DSL modem using a regular DSL phone cable?  Currently, the DSL AP/router is where I have my login credentials to gain access to the internet, but from what I've understood, these are placed on the firewall since it's the first machine that the DSL connection connects to.

Have any hints or tips?

---

### Post by Oldsoldier2003 on 2008-03-04
> **FastZ said:**
> Hey Guys, I have a DSL internet connection here at my house and I want to protect my networking using an old computer I had laying around that I will install Smoothwall on to create a hardware firewall.

Here is what my network looks like.  Currently, the DSL line comes in and connects to a DSL wireless AP/router, then I have the family desktop connected to the 4-port switch on the DSL AP.  Then I have a Linksys WRT54G with DD-WRT installed in my office that is configured as a client-bridge so I didn't have to run any extra cabling from the family room into here.  In my office, I have two computers connected to the Linksys client-bridge.  There are up to three laptops that are used in various spots of this house that need to use the wireless signal being broadcast from the DSL AP/router.  

What I want to do is take this firewall and place it between the actuall DSL connection coming into the house and the DSL AP/router.  

I understand that I will need a DSL modem installed on the red interface of the firewall, but what I don't know is whether I can still use my DSL AP/router on the green side.  Is this possible or will I need to have an Ethernet NIC on the green side and use one of my other Linksys Ethernet APs to provide the wireless and connection to the family computer?

Would it be possible to install two DSL modem PCI cards in my firewall, one red, one green, and route the DSL connection through the red and out the green and back into the DSL modem using a regular DSL phone cable?  Currently, the DSL AP/router is where I have my login credentials to gain access to the internet, but from what I've understood, these are placed on the firewall since it's the first machine that the DSL connection connects to.

Have any hints or tips?
Dsl modem to Ubuntu box configured as firewall/NAT/DHCP/Connection sharing box , then hub/wireless connected to a second nic in the Ubuntu box. That is what I would think the best setup would be. I don't think your idea would work but its easy enough to play with the old machine and unplug the current router/ap available to plug back in while you test and configure.

---

### Post by FastZ on 2008-03-04
Ok, I see what you're saying, but here is the problem with me doing it that way right now.  Currently, the DSL wireless access point is also the DSL modem, since it's built-in to the unit.  The phone line comes from the phone jack, into the back of the DSL AP and then you can connect computers to it's built-in 4-port switch or use the wireless signal it broadcasts.  Is there no way for me to place my hardware firewall between the phone jack and the DSL AP?

This would be so simple if our ISP provided cable internet connections out here, but unfortunately, they do not. :(

---

### Post by FastZ on 2008-03-05
Does anyone have any experience with placing a linux firewall machine on a home DSL connection?

---

### Post by Oldsoldier2003 on 2008-03-05
> **FastZ said:**
> Does anyone have any experience with placing a linux firewall machine on a home DSL connection?
I hoe someone posts with  some information for you soon. I don't have a linux box setup as the primary firewall here at home, my Server has its own firewall as does my workstation, I port forward the ports to my sever from the dsl gateway. Since you have windows users perhaps zone alarm for them until you figure out how to configure a "master" firewall.

I may be mistaken in my beliefs but im pretty satisfied that for a home network I've got fairly decent security using my gateway as the primary router and locking down the machines inside with bastllle hardening and iptables rules.

---

### Post by FastZ on 2008-03-05
I also have port forwarding configured on my DSL AP.  I have a few ports directed only to my server machine, which I can monitor and protect with the iptables firewall on that machine, but I have no way to protect the other computers, some of which do use Windows.  All of the Windows machines have up-to-date security software (AVG anti-virus on the family computer and CyberDefender Free on two of the laptops). 

I haven't mentioned it yet, but the firewall machine I built is using the Smoothwall firewall distro and the purpose of me wanting to find a way to put this on my home network is so I can protect every machine that connects to the internet here and also monitor what types of sites are being visited.  The latter reason is moreso just an experiment for me.

---

### Post by BooBooNTZU on 2008-03-05
I don't understand why you want to use a computer as a firewall when every single wireless router or modem has a built in firewall. Even your dsl-modem-router-wifi-ap has a built in firewall. You just have to connect to it , log-in and adjust the settings using a web browser.

---

