---
title: "[Solved] KVM - dropped network connection"
date: 2009-02-24
forum: Virtualisation
---

### Post by bodhi.zazen on 2009-02-24
I am having some problems with KVM and networking.

Host : Ubuntu 8.04 , all packages up to date.

Guest : Centos 5.2 , all packages up to date.

Network : Bridged w/ tap interface.

I have been running the guest for some time, but in the last week started having problems.

When I boot the guest, Internet connections work just fine. Internet connections to the guest are lost, seemingly at random. When this happens I can **not** connect to the guest from the host via ssh or ping. Internet connections are dropped, seemingly at random, over a 6-24 hour time frame.

From the KVM console, the guest is running and there are no errors in the logs. From the guest I can ping localhost, but not the host OS or router. restarting the network does not help.

I have tried several kernels, including the oldest one I have on the guest, as well as several virtual ethernet configurations to no avail.

It seems that either the tap loses connection with the bridge ?

I have searched but could not find and advice on Google. Any suggestions ?

Thank you in advance.

---

### Post by bonovoxpsu on 2009-02-25
the issues i've seen are with 8.10;  however, they may help you...

when i create a hardy VM on an intrepid host, i have to set the network card model to 'virtio'.  i usually have a line like so:

```

<interface type='bridge'>
  <mac address ='xx:xx:xx:xx:xx:xx'/>
  <source bridge='br0'/>
  <model type='virtio'/>
</interface>

```

i'd watch your ARP traffic, just to be sure, because i think the above might not affect you.

---

### Post by bodhi.zazen on 2009-02-25
Thank you for your reply [bonovoxpsu]("http://ubuntuforums.org/member.php?u=9145"), greatly appreciated and I appreciate this is a somewhat technical issue.

I have tried several interfaces (models) including the virtio (was using virtio by default) and I tried the[FONT=monospace] [/FONT]rtl8139.

I went to #kvm for advice, and they suggested the e1000 .

No joy with any of these 3 models :(

I have also tried different kernels including one for VMWare (from Centos peopel repositories).

---

### Post by bodhi.zazen on 2009-03-02
Just an update / FYI :

It appears as if the problem was with snort.

After trying several things, I removed and re-installed snort and my server has bee up for almost 5 days now.

I re-installed snort with :

```
sudo make uninstall && sudo make install
```

---

### Post by bodhi.zazen on 2009-03-02
> **bodhi.zazen said:**
> Just an update / FYI :

It appears as if the problem was with snort.

After trying several things, I removed and re-installed snort and my server has bee up for almost 5 days now.

I re-installed snort with :

```
sudo make uninstall && sudo make install
```

Thanks to everyone who looked at my thread, sorry it was so esoteric :twisted:

---

### Post by TheRoot on 2009-04-07
BTW, I am facing the same problem even before snort was running on my machine.

I have to reboot the system so that everything works fine again.

---

### Post by bodhi.zazen on 2009-04-08
> **TheRoot said:**
> BTW, I am facing the same problem even before snort was running on my machine.

I have to reboot the system so that everything works fine again.

I feel your pain :)

Are you running snort on the client ? If so which version and how did you install it ?

---

