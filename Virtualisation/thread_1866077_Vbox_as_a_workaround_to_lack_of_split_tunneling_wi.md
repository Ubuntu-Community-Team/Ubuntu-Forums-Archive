---
title: "Vbox as a workaround to lack of split tunneling with Cisco VPN"
date: 2011-10-20
forum: Virtualisation
---

### Post by superyounan1 on 2011-10-20
Hello,
My corporate Cisco VPN is intentionally configured in such a way were all traffic is routed through the corporate network while on the VPN, and they don't want to allow 'split tunneling', which would let users access both local and corporate network resources.

A while back I created a ubuntu VM and configured VBox for bridged networking, and to my delight I saw that the VM was able to access my local network and web browsing was also not being tunneled through the VPN. This was great, I could browse the internet privately and without bogging down the corporate network.

Recently I installed Ubuntu 11.10 on that VM, and now while connected to my VPN the VM is completely cut off from any network access, local or corporate.

Any advice on this?

Here's a link of what my network settings look like:
[IMG]http://i.imgur.com/tHJQG.jpg[/IMG]

I also noticed that, on my router page, my guest machine and host machines are both listed with the host name and MAC address of the host machine. I'm not positive, but I thought that back when I had the 'split tunnel' behavior, the guest ubuntu machine was registering its own MAC and host name with the router.

---

