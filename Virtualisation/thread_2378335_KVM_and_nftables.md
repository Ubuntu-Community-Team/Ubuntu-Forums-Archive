---
title: "KVM and nftables"
date: 2017-11-22
forum: Virtualisation
---

### Post by The Cog on 2017-11-22
I am using nftables for my firewall rules. On the odd occasion where I use KVM, it insists on creating some iptables rules which appear to have no effect, but there are warnings on the interwebs about not trying to mix iptables and nftables NAT settings. Additionally, the guest cannot get an IP address untl I issue the command ```
sudo nft insert rule inet FILTER INPUT iif "virbr0" accept
``` (FILTER AND INPUT are my table and chain names).

I can't add the fix-up to the nftables startup config because nftables starts before the virbr0 interface, so the nftables config fails to restore on boot if I add the virbr0 rule there.

Is there any way of getting KVM to use nft rules instead of making pointless iptables entries and needing a manual fix-up?

---

