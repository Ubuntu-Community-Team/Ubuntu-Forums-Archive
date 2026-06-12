---
title: "Using Virtualbox for web browsing"
date: 2020-03-01
forum: Security
---

### Post by linuxyogi on 2020-03-01
If I do all my web browsing in a Virtualbox VM (Lubuntu) and do not use  the host (also Linux) at all for browsing will this increase security ?

---

### Post by TheFu on 2020-03-01
Maybe.   It depends on 50 other choices too and what you mean by "increase security."

Asking general result questions without a bunch of specific inputs makes any answer impossible.  in the end, it comes down to whether you can guaranty zero dumb-user-clicks can happen.  in general, yes, but it wouldn't be hard to imagine a setup that actually reduces the security too.

---

### Post by EuclideanCoffee on 2020-03-01
What will happen is all your browsing will be virtualized. Virtualization isn't too crazy, most computers run a virtualized operating system more or less, and everything you are concerned about with browsing may already exist as what we call containers. [https://www.redhat.com/en/topics/virtualization/what-is-virtualization](https://www.redhat.com/en/topics/virtualization/what-is-virtualization)

Chrome and Firefox can do something similar where your browsing is typically separated from the entire computer system, which effectively does the same thing unless you're actively downloading material or visiting websites that ask (and you permit) access to your computer. Javascript is also a risk that can be mitigated with refusing Javascript upon first visiting a website and then switching it on. uMatrix is a popular application that can do this.

For reasons like this, it's less likely to receive a virus simply by browsing, but that doesn't mean you're 100% safe as zero days occur, which means vulnerabilities not yet known to professionals. And there are potentially a lot of zero days.

Will browsing everything in a virtualbox or virtual host save your computer if a zero day were to infect your machine? Likely you will be saved.

But they are not fool proof. One thing your virtual computer cannot protect you from is hosts scanning your network for vulnerabilities. Even if you're running the latest virtualbox software, a determined attacker could automatically scan the network where your traffic is coming from. If they were to find a way into your network, they could still directly infect your machine, especially if you give them reason to do so (perhaps based on your raised confidence due to having one layer of security).

You will need to mask your traffic. This is likely already done for you via your ISP, so at your edge network (this is where your true identity is where your public identity is given to you via a public IP address), you can route traffic however you want. In the case of an attacker going into your network, you can create a barrier commonly known as a firewall. Here you intercept any unwanted traffic and end it before it gets to its destination. However, people are clever enough to capture your traffic, inspect it, and know your internal network well enough to track where your true computer's identity is. This is harder to do over HTTPS but if you're sending traffic to a website, that administrator can create a trap to identify you.

From this we now know that a virtualized computer via VM will be one layer of security needed while browsing. To protect you from people knowing your IP address, you'd need to mask your IP and then provide a way to prevent bad people from tracking your traffic and using that to try accessing your network. Fortunately these things are pretty common, and you can find yourself a nice router at any store, or you can simply choose to trust your ISP to provide you with a good router. Make sure the firmware is updated, and you can expect to be fine. The final concern then may be privacy, which is resolved with a "VPN." But remember, using a VPN masks your traffic while in transit, but the host you send traffic to can see everything.

Another note, whoever is your VPN provider will see all traffic in transit.

This is true for other protocols that are commonly used for their anonymizing reputation. 

Improved security is easier to accomplish with simpler browsing habits, visiting low-risk websites, using HTTPS, and blocking Javascript on untrusted websites.

Good luck. :)

---

### Post by linuxyogi on 2020-03-01
> **TheFu said:**
>  Asking general result questions without a bunch of specific inputs makes any answer impossible. 

Please tell me what I need to mention. I will do that.

@[**[COLOR=#000000]EuclideanCoffee[/COLOR]**]("https://ubuntuforums.org/member.php?u=1943968")

Thanks for the reply.

---

### Post by EuclideanCoffee on 2020-03-02
Helpful information could include what you may be browsing. If you simply want privacy, see my above statement on how difficult privacy is to achieve. If you want security, see my above post about layered security.

Generally, virtualized computing is a layer of security that helps.

If you are going to use it practically depends on your use case. If you want to use it for Facebook browsing, I will recommend that you use a sandboxed Firefox tab, called "container." It's an addon from Mozilla.

If you want to create many virtual machines for customers, then we could talk about jailed shells or something a bit more interesting and efficient. :D

---

### Post by TheFu on 2020-03-02
For sandboxing, I'd prefer an external-to-browser tool like firejail.  There are others.  Browsers are already overly complex and trusting come add-on for an already complex system seems like adding another level on a house of cards.  After all, the incognito modes have always had faults and failures.  I'll put my trust outside the browser.  Look up the firejail capabilities and play with some of the options.  Play with these:
```

$ firejail  bash
$ firejail  --private bash
```
See how each confinement is different? See how a browser/email client would benefit from those constraints and when being over-constrained could be bad?

A VM, an external sandbox, and a browser that cannot run complex addons.  Lynx first, then dillo, then firefox only if the other two don't work and the site is "trusted".  What is a trusted site?  That's a judgement call.  Most media companies aren't.

How the VM network connection is configured for a VM matters.  Too many important details.  Read up about host-only, NAT, bridged.
How the network where the host and VM run are also important. Are there any guests allowed?  Is there any wifi?  Those are all security risks.

Every setting for the VM matters to security.  Is a clipboard shared between the guest and host?  Are host directories shared?  What sort of risky 3rd party software is installed on both?

Lots of choices. Lots of options. Each matters for security.

Have you considered any other hypervisors?  Why use vbox?

---

### Post by linuxyogi on 2020-03-03
> **EuclideanCoffee said:**
> Helpful information could include what you may be browsing. If you simply want privacy, see my above statement on how difficult privacy is to achieve. If you want security, see my above post about layered security.

Generally, virtualized computing is a layer of security that helps.

If you are going to use it practically depends on your use case. If you want to use it for Facebook browsing, I will recommend that you use a sandboxed Firefox tab, called "container." It's an addon from Mozilla.

If you want to create many virtual machines for customers, then we could talk about jailed shells or something a bit more interesting and efficient. :D

I browse mainly Facebook, various Linux forums and occasionally some porn. 

I am already using "Facebook Container".

---

### Post by linuxyogi on 2020-03-03
> **TheFu said:**
> For sandboxing, I'd prefer an external-to-browser tool like firejail.  There are others.  Browsers are already overly complex and trusting come add-on for an already complex system seems like adding another level on a house of cards.  After all, the incognito modes have always had faults and failures.  I'll put my trust outside the browser.  Look up the firejail capabilities and play with some of the options.  Play with these:
```

$ firejail  bash
$ firejail  --private bash
```
See how each confinement is different? See how a browser/email client would benefit from those constraints and when being over-constrained could be bad?

A VM, an external sandbox, and a browser that cannot run complex addons.  Lynx first, then dillo, then firefox only if the other two don't work and the site is "trusted".  What is a trusted site?  That's a judgement call.  Most media companies aren't.

How the VM network connection is configured for a VM matters.  Too many important details.  Read up about host-only, NAT, bridged.
How the network where the host and VM run are also important. Are there any guests allowed?  Is there any wifi?  Those are all security risks.

Every setting for the VM matters to security.  Is a clipboard shared between the guest and host?  Are host directories shared?  What sort of risky 3rd party software is installed on both?

Lots of choices. Lots of options. Each matters for security.

Have you considered any other hypervisors?  Why use vbox?

I am already using Firejail on the host. I haven't yet installed Firejail on the guest.
I am using Virtualbox just coz I am familiar with it.

---

### Post by TheFu on 2020-03-03
> **linuxyogi said:**
> I am already using Firejail on the host. I haven't yet installed Firejail on the guest.
I am using Virtualbox just coz I am familiar with it.

How does firejail help anything on the guest when installed on the host?

i wouldn't trust browser add-ons to provide much security.  Seems like asking the Fox to guard the hen-house, doesn't it?

And what about everything else - network, VM settings, etc.

---

### Post by pending... on 2020-03-03
Zero day vulnerabilities which give the ability to an attacker to run arbitrary code from a VM to infect its host system exist. However, such attacker would need at least one more 0 day to chain in order to get the host OS compromised, which means someone able to secretly discover and develop an exploit for two 0 days in a row. It's very unlikely that you'll have to face this kind of attackers if you stay away from any criminal or terrorist networks.

---

### Post by kevdog on 2020-03-03
Define "increased security" since that is rather a vague term given all the potential security threats in your current model.  I believe others have elucidated to this fact all ready.

---

### Post by linuxyogi on 2020-03-04
> **TheFu said:**
>  And what about everything else - network, VM settings, etc.

The host is connected to a 4G wireless router using WiFi. 
The guest is configured to use Bridged Adapter.

---

### Post by TheFu on 2020-03-04
> **linuxyogi said:**
> The host is connected to a 4G wireless router using WiFi. 
The guest is configured to use Bridged Adapter.

Which are about the least secure options available to use.

---

### Post by linuxyogi on 2020-03-04
> **TheFu said:**
> Which are about the least secure options available to use.

Then please tell me the secure way to connect.

---

### Post by TheFu on 2020-03-04
> **linuxyogi said:**
> Then please tell me the secure way to connect.

Use a router with a real firewall.
Use host-only networking for the VM. If that doesn't meet your needs, use NAT for the VM.

But these are just the tip.  There are 50 other things, at least.  
Read the threads in the Security sub-forum.
Read the threads in the Virtualization sub-forum about security.

---

### Post by linuxyogi on 2020-03-04
> **TheFu said:**
> Use a router with a real firewall. 

At the moment I am using a 4G connection. The router my ISP provides is similar to [this]("https://www.jio.com/shop/en-in/router-m2-black/p/491193575")

> **TheFu said:**
> 
Use host-only networking for the VM. If that doesn't meet your needs, use NAT for the VM.
But these are just the tip.  There are 50 other things, at least.  
Read the threads in the Security sub-forum.
Read the threads in the Virtualization sub-forum about security.

As per your suggestions I have changed the VM networking to NAT.

---

### Post by linuxyogi on 2020-03-04
@[B]TheFu

[/B]What I mean is I am stuck with the router provided by my ISP.

I checked my router at grc.com and it passed the test.

---

