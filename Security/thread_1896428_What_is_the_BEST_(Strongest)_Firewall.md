---
title: "What is the BEST (Strongest) Firewall?"
date: 2011-12-16
forum: Security
---

### Post by adamantasaurus on 2011-12-16
Hello,

I am going to be using ubuntu server edition either 10.04 or 11.10 (not sure which one yet) and I was wondering if you guys could point me to the strongest firewall out there. I am going to be setting up an online business and the firewall is going to be one of the most important things to have. Any advice is welcome.

P.S. I am completely new at this so please when you respond please do so in La mans terms (or at least explain yourself). 

Thanks Much Appreciated

Adamantasaurus

---

### Post by sammiev on 2011-12-16
They are all the same but what you do to it. I use Gufw which is already there but set the out bound to deny and add the rules yourself. :)

---

### Post by sammiev on 2011-12-16
Read [this]("http://ubuntuforums.org/showthread.php?t=1876124") it will help you a lot. :)

---

### Post by HermanAB on 2011-12-16
Firewalls are mostly a Windows thing.  It is needed when you don't have proper control over the server and cannot limit the stuff that is running on it.

On my Linux servers, I use only one IP tables rule, to limit DOS and brute force attacks.

---

### Post by adamantasaurus on 2011-12-17
What is the IP tables rule?

If I have an ecommerce site up and running with a ssl is it feasible for me to build a firewall myself to keep attackers out?

---

### Post by Dangertux on 2011-12-17
If you're talking about running an ecommerce site - I assume you're talking about accepting payment card information. That is going to put you into the realm of PCI compliance, which is a scary thing for someone new to server administration. You can't just accept credit card information.

So in terms of ecommerce a firewall is only one thing you need to think about. For PCI compliance guidelines you have to meet the following (and this is a simplified list) Here is the full list : [http://www.bbb.org/data-security/becoming-pci-compliant/checklists/](http://www.bbb.org/data-security/becoming-pci-compliant/checklists/)

But basically in terms of what you're setting up on your system you're going to need the following.

- Firewall (optional but recommended)
- AV required (not really , but for compliance it needs to be there, this can be an external appliance)
- IPS /IDS (required for compliance, again can be an external appliance)
- Web Application Firewall (same applies, can be external appliance)
- Encryption (AES or stronger, can't store track 2 etc ... Read the standard for this)
- Transmittal of data MUST BE SSL
- Credentials (they need to be very strong consult the checklist)
- Patch levels, current, always, or you are out of compliance
- Stored data can not be on the same server (either physical or virtual separation is acceptable) as the web application accepting the PCI.

Also you're not hosting this from your home or small business are you? Because you won't meet the rigorous phsyical security standards.

Now that should keep you busy for awhile ;-) My advice accept paypal or use a hosting company.

To answer your question about Firewalls, they're not just a Windows thing that being said, most if not all SPI firewalls are going to be nothing but a front end for iptables/netfilter. Again for PCI compliance a DPI firewall OR IDS is required  though it can be external. So really, unless you're talking about serious configuration of an IPS/DPI system you're best just using iptables.

Hope this helps.

---

### Post by uRock on 2011-12-17
Moved to Security Discussions.

I use GUFW, which can be found in the Ubuntu Software Center.

---

### Post by dFlyer on 2011-12-17
I use GUFW which is located in the archives and is as good as the rest.

---

### Post by adamantasaurus on 2011-12-17
> **Dangertux said:**
> If you're talking about running an ecommerce site - I assume you're talking about accepting payment card information. That is going to put you into the realm of PCI compliance, which is a scary thing for someone new to server administration. You can't just accept credit card information.

So in terms of ecommerce a firewall is only one thing you need to think about. For PCI compliance guidelines you have to meet the following (and this is a simplified list) Here is the full list : [http://www.bbb.org/data-security/becoming-pci-compliant/checklists/](http://www.bbb.org/data-security/becoming-pci-compliant/checklists/)

But basically in terms of what you're setting up on your system you're going to need the following.

- Firewall (optional but recommended)
- AV required (not really , but for compliance it needs to be there, this can be an external appliance)
- IPS /IDS (required for compliance, again can be an external appliance)
- Web Application Firewall (same applies, can be external appliance)
- Encryption (AES or stronger, can't store track 2 etc ... Read the standard for this)
- Transmittal of data MUST BE SSL
- Credentials (they need to be very strong consult the checklist)
- Patch levels, current, always, or you are out of compliance
- Stored data can not be on the same server (either physical or virtual separation is acceptable) as the web application accepting the PCI.

Also you're not hosting this from your home or small business are you? Because you won't meet the rigorous phsyical security standards.

Now that should keep you busy for awhile ;-) My advice accept paypal or use a hosting company.

To answer your question about Firewalls, they're not just a Windows thing that being said, most if not all SPI firewalls are going to be nothing but a front end for iptables/netfilter. Again for PCI compliance a DPI firewall OR IDS is required  though it can be external. So really, unless you're talking about serious configuration of an IPS/DPI system you're best just using iptables.

Hope this helps.

Wow That's a lot of work, this will probably take me a couple of years. But I do have that time to learn it so I think maybe I will just host my site during those couple of years. This is a startup business with almost no disposable cash (I can't pay someone to do it for me). Is it reasonable for me to learn how to do all of this and get it up and running in a few years?

And I'm thinking of eventually (like 5 years from now) setting up a server for other people to host their websites on and pay me money!!! :) is that reasonable to do and are there other guidelines for that?

---

### Post by Thewhistlingwind on 2011-12-17
> **adamantasaurus said:**
> Wow That's a lot of work, this will probably take me a couple of years. But I do have that time to learn it so I think maybe I will just host my site during those couple of years. This is a startup business with almost no disposable cash (I can't pay someone to do it for me). Is it reasonable for me to learn how to do all of this and get it up and running in a few years?


Considering that if you mess this up, the lawsuits can and will follow. (And make no mistake, it is easy to mess any one of these things up.) I would personally echo the recommendation of paypal or paypal-like services. 

Also for web hosting, you'd better have some crazy bandwidth to do something like that. (And for that matter make sure your contract with your ISP allows web hosting.)

---

### Post by Lars Noodén on 2011-12-17
> **adamantasaurus said:**
> What is the IP tables rule?

If I have an ecommerce site up and running with a ssl is it feasible for me to build a firewall myself to keep attackers out?

Not really.  You have to leave port 80 and port 443 open for your customers and the attacks will come via those ports.  You can limit other kinds of attacks, such as brute force attacks against SSH:

```

   # allow the courtesy of at least a ping
   iptables -A INPUT -p icmp --icmp-type echo-request \
        -m limit --limit 1/s -i eth0 -j ACCEPT
. . .
   # limit bruteforce attacks on SSH
   iptables  -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 4/minute --limit-burst 5 -j ACCEPT

```

I guess you could also rate-limite ports 80 and 443 but I can't see the advantage there.

---

### Post by dodo3773 on 2011-12-17
Pretty sure that most (if not all) firewalls you will find use iptables as their back end. So, straight iptables (cli / config files) is probably the best firewall as it is built into the Linux kernel.

---

### Post by Lars Noodén on 2011-12-17
> **dodo3773 said:**
> Pretty sure that most (if not all) firewalls you will find use iptables as their back end. So, straight iptables (cli / config files) is probably the best firewall as it is built into the kernel.

There are a lot of firewalls based on [PF](http://home.nuug.no/~peter/pf/), not just IP Tables.  But those are built around one of the BSDs even if it is just PFSense.  I find PF a lot easier to work with than IP Tables, but it would mean a shift from Linux.

---

### Post by UltimateCat on 2011-12-17
> **dFlyer said:**
> I use GUFW which is located in the archives and is as good as the rest.

Hi! As a newbie I have to admit I'm don't know a lot of things about Ubuntu ( but learning)

Iv'e thought about uninstalling Firestarter.  It worked for me last year but for whatever the reason it's been buggy for me.  Anyway, I have to do something....as I'm sure you'll agree.

Could reinstall Ubuntu 10.04: Ultimate Edition 2.7 if I have to-

How would I know where and if GUFW is already a part of My current OS?
Advice at this point is greatly needed !

---

### Post by dodo3773 on 2011-12-17
> **Lars Noodén said:**
> There are a lot of firewalls based on [PF]("http://home.nuug.no/%7Epeter/pf/"), not just IP Tables.  But those are built around one of the BSDs even if it is just PFSense.  I find PF a lot easier to work with than IP Tables, but it would mean a shift from Linux.
Should have specified. Linux kernel. Previous post has been edited.

---

### Post by uRock on 2011-12-17
> **UltimateCat said:**
> Hi! As a newbie I have to admit I'm don't know a lot of things about Ubuntu ( but learning)

Iv'e thought about uninstalling Firestarter.  It worked for me last year but for whatever the reason it's been buggy for me.  Anyway, I have to do something....as I'm sure you'll agree.

Could reinstall Ubuntu 10.04: Ultimate Edition 2.7 if I have to-

How would I know where and if GUFW is already a part of My current OS?
Advice at this point is greatly needed !

UFW is already installed. GUFW is a GUI front end for UFW. GUFW is found in the Ubuntu Software Center or installed via CLI with **sudo apt-get install gufw**. Once installed, GUFW can be found under System> Administration menu or by typing Firewall or GUFW in the Unity search. If you are installing a CLI only server, then learning IP tables is recommended.

I do not recommend Firestarter. It has not been maintained, nor updated in many years.

---

### Post by adamantasaurus on 2011-12-17
.....

---

