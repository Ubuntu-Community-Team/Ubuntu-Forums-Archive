---
title: "SSH to Virtual Machine"
date: 2012-08-31
forum: Virtualisation
---

### Post by daniel488 on 2012-08-31
Hi,

what are the advantages to connect to VM via ssh from host operating system. I saw many tutorials about it, often it is first step after installing Linux on VM when someone wants to create development environment on VM. Why just don't use that VM like normal system?

Kind regards,
Daniel

---

### Post by 2F4U on 2012-08-31
Given that the VM runs on your local machine, direct access may be the easiest option. However, if the VM runs on another machine or on a server located in a data center, SSH may be the only option.

---

### Post by daniel488 on 2012-08-31
Yeah sure, but if it is the same machine...
Even [Youtube tutorial]("http://www.youtube.com/watch?v=5BsShkcweIs")... I don't get it.

---

### Post by TJet1.8 on 2012-09-15
You can't cut/paste text or entire file contents in a linux console.
You can't resize your linux console.

You can, however, do the above in an ssh session.....

This is just one advantage of using ssh.

---

### Post by Habitual on 2012-09-16
ssh'ing into a VM I have installed locally allows me to use copy/cut/paste (clipboard) in terminal to manage the users or environment.
Virtualbox does not have that feature at the moment. I cannot copy from the Host's clipboard into the Guest's clipboard, AFAIK.

---

### Post by markbl on 2012-09-17
> **Habitual said:**
> 
Virtualbox does not have that feature at the moment. I cannot copy from the Host's clipboard into the Guest's clipboard, AFAIK.
Virtualbox has had guest/host bidirectional clipboard transfer for as many years as I can remember back.

---

### Post by HermanAB on 2012-09-20
If I run Vbox on a machine with a GUI, then I install the host extensions and use the Vbox GUI.  

However, if the Vbox machine is on a server with no GUI on the other side of the planet, in a cupboard of basement toilet with a sign 'beware of the leopard', then SSH is pretty much the only option.

---

### Post by CharlesA on 2012-09-21
> **HermanAB said:**
> If I run Vbox on a machine with a GUI, then I install the host extensions and use the Vbox GUI.  

However, if the Vbox machine is on a server with no GUI on the other side of the planet, in a cupboard of basement toilet with a sign 'beware of the leopard', then SSH is pretty much the only option.
Pretty much dead on.

I have ssh installed on all my *nix VMs, even if they are running a GUI. It is easier to manage a machine via SSH instead of having to login to the GUI and do some task such as checking and applying updates.

---

