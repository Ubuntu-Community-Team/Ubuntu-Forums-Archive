---
title: "KVM networking help"
date: 2017-09-01
forum: Virtualisation
---

### Post by ozkhan1 on 2017-09-01
Newbie here, trying to setup pfsense in virtual manager /kvm on ubuntu desktop 16.04 LTS.

I have two nics that I'm passing to the pfsense vm. When I do that the ubuntu machine itself of course doesn't have any network connection. Is there a way I can configure a bridge that connects to the LAN nic? I want the ubuntu machine behind the firewall as well.

Or perhaps what I'm trying to do is not an efficient way of doing it so please recommend the best setup. The ubuntu machine will run a virtualized firewall and be part of the same network which will have physical machines as well as other vms, all part of the same. 

With my setup I have been able to accomplish most except the actual host machine doesn't have any connectivity. Ideally I know a three nic host would be best but I only have two nics at the moment.

Thx in advance!

---

### Post by deadflowr on 2017-09-01
*Thread moved to **Virtualisation**.*

---

### Post by TheFu on 2017-09-01
Welcome to the forums.

IMHO, a WAN router should be on dedicated hardware. There are many reasons for this, but failure modes is my main reason.  If you loose the VM host beachhead, you've lost the war.

For a lab, this is a great solution, provided it isn't protecting against inbound internet traffic.

So assuming you still want to do this, perhaps to have a LAN router, then your KVM host needs to support IOMMU passthru and you should pass the outbound NIC through to the VM guest.  This is the most secure way.  Do NOT use a bridge for this connection.

On the LAN NIC, you can setup a bridge.

Clearly, you'll need to connect each of the different NICs to different physical network infrastructure.  The KVM host NIC would be on the LAN interface too.  Normal Linux bridging does that by default through the interfaces file. Physical separation is important.

Does this make sense?

BTW, running a router on a desktop install is a very poor choice, even worse doing it on the KVM host.

IMHO.  BTW, my advice is the same if you were running VMware ESX/ESXi.  Just because many people do this, doesn't make it a good idea in all situations.

---

### Post by ozkhan1 on 2017-09-01
> **TheFu said:**
> Welcome to the forums.

IMHO, a WAN router should be on dedicated hardware. There are many reasons for this, but failure modes is my main reason.  If you loose the VM host beachhead, you've lost the war.

For a lab, this is a great solution, provided it isn't protecting against inbound internet traffic.

So assuming you still want to do this, perhaps to have a LAN router, then your KVM host needs to support IOMMU passthru and you should pass the outbound NIC through to the VM guest.  This is the most secure way.  Do NOT use a bridge for this connection.

On the LAN NIC, you can setup a bridge.

Clearly, you'll need to connect each of the different NICs to different physical network infrastructure.  The KVM host NIC would be on the LAN interface too.  Normal Linux bridging does that by default through the interfaces file. Physical separation is important.

Does this make sense?

BTW, running a router on a desktop install is a very poor choice, even worse doing it on the KVM host.

IMHO.  BTW, my advice is the same if you were running VMware ESX/ESXi.  Just because many people do this, doesn't make it a good idea in all situations.

Thanks for the valuable input. It makes sense. I am doing this to try out pfsense because it has sOne good features and honestly I don't have dedicated hardware for it. I had a spare nic I put in new desktop. I use ubuntu desktop on it because I am still learning the cli. But the idea is once I have it set up, I will remove the GUI to let it run headless. It is also running a storage vm so I can't dedicate it 100 percent to pfsense.

So going through your post, sounds to me you prefer a three nic solution. One dedicated for inbound, one for outbound and one for host? There is no secure way of setting it up so the host uses the same nic as outbound LAN?

---

### Post by TheFu on 2017-09-02
Linux is very flexible. You can almost always do whatever you want. Just because you **can** do something, doesn't mean it is a good idea.

Just because pfsense has a feature, that doesn't mean it is always a good idea to use it.

I do like the 3 NIC solution, but the 3rd NIC is for a guest/unsecured LAN, not outbound. I use physically separate LANs, not vLANs.  

I think you'll find that removing the GUI isn't easy.  Best to start fresh on a server install and add the pkgs you want.

---

