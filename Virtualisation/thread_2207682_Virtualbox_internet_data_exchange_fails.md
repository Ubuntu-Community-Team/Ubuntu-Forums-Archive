---
title: "Virtualbox internet data exchange fails"
date: 2014-02-24
forum: Virtualisation
---

### Post by uwe-bungto on 2014-02-24
I have two apps running on windows 7 in virtual box. Tomtom MyDrive Connect and Polar Websync. The both connect to their servers and go through the motions of exchanging data; but they never finish. they both hang at about 99% finished.
I am in the vboxuser group, no problem with network access. W7 gets its' updates. Is there any other settings to check?

---

### Post by varunendra on 2014-02-25
If the VM is able to communicate over Internet, I wouldn't suspect the external settings. But what kind of networking the VM has? NAT or Bridged? I think Bridged mode should rule out _any_ possibility of problems on the host side.

---

### Post by uwe-bungto on 2014-02-26
> **varunendra said:**
> If the VM is able to communicate over Internet, I wouldn't suspect the external settings. But what kind of networking the VM has? NAT or Bridged? I think Bridged mode should rule out _any_ possibility of problems on the host side.
thanks
The problem occurs whether the network is set to NAT or Bridged adaptor. Both give internet access, but will not allow these apps to transfer data.

---

### Post by varunendra on 2014-02-26
To me it seems like a problem in the way these applications or their servers work. Since a simple download works normally as you mentioned yourself.

As far as I know, the OS directly communicates to the router like a normal setup when the networking is in Bridged mode. The Host and the VM platform have nothing to do with how the packets are routed or exchanged between the communicating nodes.

Have you confirmed that it is not a known problem with the applications themselves? I have seen data exchange hanging like this before, both on Windows and Ubuntu (not in VMs), but that always happened to be a temporary problem at the server's end.

---

### Post by uwe-bungto on 2014-02-27
> **varunendra said:**
> To me it seems like a problem in the way these applications or their servers work. Since a simple download works normally as you mentioned yourself.

As far as I know, the OS directly communicates to the router like a normal setup when the networking is in Bridged mode. The Host and the VM platform have nothing to do with how the packets are routed or exchanged between the communicating nodes.

Have you confirmed that it is not a known problem with the applications themselves? I have seen data exchange hanging like this before, both on Windows and Ubuntu (not in VMs), but that always happened to be a temporary problem at the server's end.

After my last post I updated VB to the latest and tried to transfer the data from the Polar monitor to their website, still a no-go.I fired up windoze and the transfer was successful, also updated TomTom with new maps. maybe I should ask over at the VirtualBox forum I can't be the only one using either of there toys.

Thanks If you come up with any ideas let me know.

---

### Post by varunendra on 2014-02-27
> **uwe-bungto said:**
> maybe I should ask over at the VirtualBox forum

You definitely should. If there is a known problem, they can provide much better insight.

---

