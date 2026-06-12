---
title: "Ubuntu 17.10 server [Virtualbox], PROBLEM! please help!"
date: 2018-01-21
forum: Server Platforms
---

### Post by lionel4anlominus on 2018-01-21
Hello everyone
I installed Virtual Box, on Ubuntu 17.10,
And the virtual machine installed Ubuntu 17.10 Server.
Now I try to set up a static IP server, without success.
I have read some solutions in forums, everyone is talking about the same solution,
But I can not apply the changes in NetPlan with the command, [netplat apply]
Maybe someone can help me set the fixed IP that?

:wink:
[COLOR=#000000]Has anyone encountered this? And passed it ..?[/COLOR]
:razz:
[COLOR=#000000]Thanks in advance for helpers![/COLOR]

---

### Post by LHammonds on 2018-01-22
> **lionel4anlominus said:**
> 
Now I try to set up a static IP server, without success.

That doesn't give us a lot to go on.

Is this because you are not familiar with the process of setting up a static IP in /etc/network/interfaces or were you able to set a static IP but just not able to access / ping that IP from a different box?

I don't use Ubuntu Desktop but if VirtualBox behaves the same on Ubuntu as it does Windows, the Virtual Machine (VM) will default to an internal network configuration only...meaning no traffic from the outside (including the hosting machine) will be able to ping it.  You have to configure the VM's network adapter to use "Bridged" instead of "NAT"

LHammonds

---

### Post by darkod on 2018-01-22
> **LHammonds said:**
> process of setting up a static IP in /etc/network/interfaces

Since 17.10 (and in the new 18.04 I guess) ubuntu uses netplan instead of the widely known /etc/network/interfaces setup for NIC config.

I agree, most probably the issue is that you don't have the VBox virtual interface set to Bridged mode. You need that if you want the VM NIC to act as if it was in your LAN.

After that you need to set it up with a network config valid for your LAN and it will work.

---

### Post by LHammonds on 2018-01-22
> **darkod said:**
> Since 17.10 (and in the new 18.04 I guess) ubuntu uses netplan instead of the widely known /etc/network/interfaces setup for NIC config.Ah, didn't know about that.  Latest version I've installed so far is 16.04.  I'll have to learn that process and include that in my how-to dox for 18.04 when I start replacing my servers with that version.

Thanks,
LHammonds

---

### Post by darkod on 2018-01-22
Yeah, me too. Saw it here on the forum. Since the last LTS we have to learn few new tricks I guess. The netplan way is quite different. :)

---

