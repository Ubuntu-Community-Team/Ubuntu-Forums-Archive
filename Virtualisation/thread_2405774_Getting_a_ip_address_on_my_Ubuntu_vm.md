---
title: "Getting a ip address on my Ubuntu vm"
date: 2018-11-11
forum: Virtualisation
---

### Post by th3radman on 2018-11-11
I just installed an Ubuntu vm on my server and I'm trying to get it set up with a couple ip addresses according to my main network interface and p2p interface.  I can see my mac address from my esxi interface, but only one ip address.  As a complete noob to linux and command line, how to I get an ip address to my interfaces?  I'm running Ubuntu version 18.04.1.

---

### Post by slickymaster on 2018-11-11
Thread moved to **Virtualisation** for a better fit

---

### Post by TheFu on 2018-11-11
[https://netplan.io/examples](https://netplan.io/examples)

The Ubuntu Server Guide for 18.04 has a section on networking: [https://help.ubuntu.com/lts/serverguide/networking.html.en](https://help.ubuntu.com/lts/serverguide/networking.html.en) It has an example with multiple IPs.

Netplan is relatively new. This is what 18.04 uses for network configuration, so whenever you search for solutions, if they don't start with "netplan", then they are for older releases and do not apply.  We've used the same basic network configuration for 20+ yrs, until 18.04.

---

### Post by SeijiSensei on 2018-11-11
You don't tell us what VM solution you're using. In Virtualbox, you can configure the network adapter to run in "bridged" mode. It will then be on the same network as the host computer and can use addresses in the same space.

---

### Post by TheFu on 2018-11-11
Think he's using VMware ESXi. Normally, I'd ask lots of questions, as  you know, but anyone running ESXi is probably a paid admin of some sort and aware of the different options.  But this is all just a guess, except the esxi part.

---

### Post by th3radman on 2018-11-11
I am far from any IT admin.  I'm just a nerd who swan dove into a subject that you really shouldn't dive straight into without knowing anything.

---

### Post by TheFu on 2018-11-12
> **th3radman said:**
> I am far from any IT admin.  I'm just a nerd who swan dove into a subject that you really shouldn't dive straight into without knowing anything.

If you are trying to have multiple IP addresses on the same subnet, that is easy for inbound connections to be used on the server. It is less easy to be useful for outbound connections and requires a strong understanding of networking to make it work.
Having multiple addresses on different subnets is easier, mainly because the routing is easier. This is why professional IT setups will have different networks for services, storage, backups and administration needs.  Usually there are 4+ NICs inside a server to keep the networks physically separate for security purposes. Random DHCP isn't used for servers, ever. All IPs are static.

I think the answer for your question has been provided. If you didn't get what you need to work, then please clearly specify what you are attempting and show the config files involved with the settings on the system. More details means better answers.

---

