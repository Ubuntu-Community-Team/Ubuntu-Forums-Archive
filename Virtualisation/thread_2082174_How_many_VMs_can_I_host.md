---
title: "How many VMs can I host?"
date: 2012-11-08
forum: Virtualisation
---

### Post by rosefox911 on 2012-11-08
Hey guys,

I'm trying to setup a small server for my home. I intended to run 6~12 VMs on it (debian, just command line no GUI). The purpose of these VMs is going to be to run a small script that will change VPN Profiles, and access a site. I was thinking of buying a cheapish server like the INTEL SR1560SF (found one on ebay for 130 bucks)

But I am unsure if this sort of server would be able to handle what I need. What do you guys recommend? Is there one that would better suite my needs? If need be, I am willing to build a server myself. I currently run 5 VMs off my 4 year old macbook pro, it can barely handle it. Thank you!

Jorge

PS: The host OS is going to be either Debian or Ubuntu.

---

### Post by Slim Odds on 2012-11-08
I depends on how much memory you have and how much you intend to give to the VM's. etc. etc.

---

### Post by rosefox911 on 2012-11-08
I was thinking something like this:

[http://www.ebay.com/itm/INTEL-SR1560SF-1U-SERVER-w-S5400SF-2-x-QUAD-CORE-L5410-2-33GHz-8GB-RAM-RAILS-/110971807050?pt=COMP_EN_Servers&hash=item19d66f654a](http://www.ebay.com/itm/INTEL-SR1560SF-1U-SERVER-w-S5400SF-2-x-QUAD-CORE-L5410-2-33GHz-8GB-RAM-RAILS-/110971807050?pt=COMP_EN_Servers&hash=item19d66f654a)

The VMs are going to be running a very basic python script. But I need them to be isolated from each other. I plan to use virtual box to host the VMs. How many could I host on the server I listed?

---

### Post by Slim Odds on 2012-11-08
> **rosefox911 said:**
> I was thinking something like this:

[http://www.ebay.com/itm/INTEL-SR1560SF-1U-SERVER-w-S5400SF-2-x-QUAD-CORE-L5410-2-33GHz-8GB-RAM-RAILS-/110971807050?pt=COMP_EN_Servers&hash=item19d66f654a](http://www.ebay.com/itm/INTEL-SR1560SF-1U-SERVER-w-S5400SF-2-x-QUAD-CORE-L5410-2-33GHz-8GB-RAM-RAILS-/110971807050?pt=COMP_EN_Servers&hash=item19d66f654a)

The VMs are going to be running a very basic python script. But I need them to be isolated from each other. I plan to use virtual box to host the VMs. How many could I host on the server I listed?
I think that you're grossly oversimplifying the concept here.

A VM typically runs an entire OS. That's seems like a bit of overkill simply to run a few python scripts. Ubuntu is a multi-tasking OS. You should be able to run multiple processes to accomplish what you want.

---

### Post by rosefox911 on 2012-11-08
Hi there,

Thanks for your reply! Each script accessing a different VPN Profile, accesses a site, then goes to a different VPN Profile. I currently have 5 of those running on 5 different VMs. If I had them all on the same OS it wouldn't work. This is why I need the VMs. Is the server I provided not powerful enough to do this task? What would you recommend? Thank you,

Jorge

---

### Post by Slim Odds on 2012-11-08
> **rosefox911 said:**
> Hi there,

Thanks for your reply! Each script accessing a different VPN Profile, accesses a site, then goes to a different VPN Profile. I currently have 5 of those running on 5 different VMs. If I had them all on the same OS it wouldn't work. This is why I need the VMs. Is the server I provided not powerful enough to do this task? What would you recommend? Thank you,

Jorge
Just because they need different profiles doesn't mean they need to be in different VM's. Each process has its own environment.

Once again, it sounds like overkill to me.

Without more details, it's impossible to determine what your real needs would be.

---

### Post by rosefox911 on 2012-11-08
Here is the process of the python script.

Each script has a set number of profiles it will cycle through. It connects to the VPN profile, downloads an image, uploads it, then submits a query to the site. It then switches to another VPN Profile.

I have 5 of those scripts running simultaneously. What other information would you require? Thanks you!

---

### Post by dannyboy79 on 2012-11-08
how much ram does your current macbook pro have and how much memory did you give each VM? I would say just base it off that.

curious what you're doing with the VM's though, is it possible to have a python script access a youtube video to act as a "view". Would make sense what you're doing then. :)  Not sure about the legality of it all though.

---

### Post by Slim Odds on 2012-11-08
> **rosefox911 said:**
> Here is the process of the python script.

Each script has a set number of profiles it will cycle through. It connects to the VPN profile, downloads an image, uploads it, then submits a query to the site. It then switches to another VPN Profile.

I have 5 of those scripts running simultaneously. What other information would you require? Thanks you!
This could be quite a large topic. Look into background processing with bash.

[http://web.mit.edu/gnu/doc/html/features_5.html](http://web.mit.edu/gnu/doc/html/features_5.html)

---

### Post by rosefox911 on 2012-11-08
> **dannyboy79 said:**
> how much ram does your current macbook pro have and how much memory did you give each VM? I would say just base it off that.

curious what you're doing with the VM's though, is it possible to have a python script access a youtube video to act as a "view". Would make sense what you're doing then. :)  Not sure about the legality of it all though.

Hi Dannyboy,

Macbook has 4 GBs of ram (ddr2). I have about 256 for each VM. The purpose I am using it for isn't youtube or anything, its legal. I know a bit about computer hardware but not much about servers (specially used ones). Wanted some suggestions. Thanks! =]

---

