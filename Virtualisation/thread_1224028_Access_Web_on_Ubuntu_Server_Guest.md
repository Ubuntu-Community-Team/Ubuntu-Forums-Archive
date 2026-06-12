---
title: "Access Web on Ubuntu Server Guest?"
date: 2009-07-26
forum: Virtualisation
---

### Post by ShinHadoken on 2009-07-26
I'm running Apache 2 on Ubuntu Server 9.04, guest OS on a Windows XP (SP3) host. Is there any way that I could view the webpages hosted by Apache on the VM via my host's browser?

---

### Post by bodhi.zazen on 2009-07-27
Yes, this is fairly standard. You can user host only, NAT, or a bridged network solution, although the exact configuration depends on what virtualization you are using (vmware is different from Virtualbox is diffferent from KVM, Xen, OpenVZ, etc).

---

### Post by ShinHadoken on 2009-07-27
Well, Ubuntu's virtual card is _bridged_ to my hosts ethernet card. What do I do?

---

### Post by bodhi.zazen on 2009-07-27
put your guest ip address in your browser ?

If that fails we will need more details . Windows host ? What virtualization ? VMware ? VBox ? what.

Are you running a firewall on host or guest ?

---

### Post by ShinHadoken on 2009-07-27
My apologies, I thought I mentioned in the original post that I'm using VirtualBox.

---

### Post by ShinHadoken on 2009-07-28
BumpP (Bring up my post, Please)  ;)

---

### Post by bodhi.zazen on 2009-07-28
On Virtualbox

Shut down your guest.

Open the options panel, under the networking tab select bridged networking (Not NAT).

Re boot the guest.

You should be able to access the guest using the ip address in the firefox bar.

If not, again, firewall on host or guest ?

---

### Post by ShinHadoken on 2009-07-28
Afraid it didn't work, yes I am running a firewall on both host and guest. Host is just the standard Windows XP firewall, Ubuntu is running UFW. Any rules/exceptions need to be made?

---

### Post by bodhi.zazen on 2009-07-28
Yes, you need to allow port 80.

Shut off ufw and if you can then connect re-enable ufw and then add a rule to allow connections to port 80.

---

### Post by ShinHadoken on 2009-07-30
Alright, I'll give that a shot.

---

