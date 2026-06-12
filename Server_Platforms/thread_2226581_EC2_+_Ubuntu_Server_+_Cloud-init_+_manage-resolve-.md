---
title: "EC2 + Ubuntu Server + Cloud-init + manage-resolve-conf = fail"
date: 2014-05-28
forum: Server Platforms
---

### Post by MikaelSetterberg on 2014-05-28
Hi,
I am trying to migrate a Vagrant setup from my local machine to EC2. It is provisioned with Puppet that in many cases rely on the fqdn. Everything works locally in my VirtualBox but I have issues setting up /etc/resolv.conf in EC2. I discovered the cloud-init feature and have successfully passed user-data into the VM to set the hostname. However, what I cannot get to work is the manage-resolv-conf directive. There is a comment in the cloud-init changelog for version 0.7.2 that implies this only works on Redhat systems:

"- Adding a resolv.conf configuration module (LP: #1100434). Currently only
  working on redhat systems (no support for resolvconf)"

Is this correct? I also found another comment somewhere by smoser that it would be good if this could be made to work on Ubuntu too. The comment was quite old and I have troubles figuring out whether this was ever fixed. The changelogs for cloud-init > 0.7.2 do not provide any clues either.

I guess the problem really lies in resolvconf clashing with cloud-init. 

Has anyone successfully updated resolv.conf via cloud-init on Ubuntu? If so, how? Do I have any other options? I keep running into tons of SSL issues since I cannot get this to work reliably.

Thanks,
Mikael

---

### Post by MikaelSetterberg on 2014-05-28
I never managed to resolve this using Vagrant+Puppet+Cloud-init for EC2. However, it turns out the contents of the /etc/resolv.conf is pulled in via DHCP. The EC2 console provides "DHCP Option Sets" for VPC clusters. Using the EC2 console I could tweak the domain name and now this work as expected.

---

