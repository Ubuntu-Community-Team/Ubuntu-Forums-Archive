---
title: "DirectX acceleration in VMware."
date: 2008-02-23
forum: Virtualisation
---

### Post by indianballer24 on 2008-02-23
Is there any way to get Direct in any VMware product? Preferably VMware Server.

---

### Post by pytheas22 on 2008-02-23
The last I heard, VMware support for 3d-acceleration is still in beta mode.  DirectX worked pretty well for me on an older laptop with Intel video and only 512 megabytes of memory total (half that for the vm), but on my desktop with 2 gigabytes of memory and a newer Intel video card, it doesn't work at all.  So you might have to just try it and see what happens.  You can install VMware player for free and set up a machine in it to see how well it works on your machine; there are directions if you search the Internet.

---

### Post by indianballer24 on 2008-02-23
> **pytheas22 said:**
> The last I heard, VMware support for 3d-acceleration is still in beta mode.  DirectX worked pretty well for me on an older laptop with Intel video and only 512 megabytes of memory total (half that for the vm), but on my desktop with 2 gigabytes of memory and a newer Intel video card, it doesn't work at all.  So you might have to just try it and see what happens.  You can install VMware player for free and set up a machine in it to see how well it works on your machine; there are directions if you search the Internet.
What are the steps to enable it in though? I looked on the internet, but I couldn't find anything.

---

### Post by pytheas22 on 2008-02-23
You have to add a line to your configuration file, and then if you're lucky DirectX will install and work.  This explains it: [http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html](http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html)

---

### Post by indianballer24 on 2008-02-25
> **pytheas22 said:**
> You have to add a line to your configuration file, and then if you're lucky DirectX will install and work.  This explains it: [http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html](http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html)
Those steps are for VMware Workstation. What are the steps for VMware Server?

---

### Post by pytheas22 on 2008-02-25
I haven't really used vmware server so sorry if I'm wrong, but I think there should still be a .vmx file somewhere that you can edit.  Isn't vmware server just a way of sharing virtual machines across a network?

Otherwise, you could always install vmware player (it's free) and make a local machine that way that you can edit.

---

### Post by OmegaBLK on 2008-02-25
> **indianballer24 said:**
> Those steps are for VMware Workstation. What are the steps for VMware Server?

As far as VMware Server (<=1.4) is concerned, it **does not** include Direct3D support.  Only VMware Workstation and VMware Player (>=2.0) support it.  I am not sure of the status of Direct3D or graphical hardware acceleration in VMware Server 2.0 Beta; you should check the VMware forums, knowledge base, or docs on their site for info on that.  The link posted above was for WS 5.0, so I will post the link to enable Direct3D in WS 6.0:

[http://pubs.vmware.com/ws6_ace2/ws/ws_vidsound_d3d_enabling_guestos.html](http://pubs.vmware.com/ws6_ace2/ws/ws_vidsound_d3d_enabling_guestos.html) 

You can pretty much use those same instructions enable it in VMware Player.  If in doubt make sure to check/ask in the [official VMware forums](http://communities.vmware.com/index.jspa;jsessionid=4E1A45C6C6E0DF09887AD0410798A70C).

---

### Post by indianballer24 on 2008-02-27
> **OmegaBLK said:**
> As far as VMware Server (<=1.4) is concerned, it **does not** include Direct3D support.  Only VMware Workstation and VMware Player (>=2.0) support it.  I am not sure of the status of Direct3D or graphical hardware acceleration in VMware Server 2.0 Beta; you should check the VMware forums, knowledge base, or docs on their site for info on that.  The link posted above was for WS 5.0, so I will post the link to enable Direct3D in WS 6.0:

[http://pubs.vmware.com/ws6_ace2/ws/ws_vidsound_d3d_enabling_guestos.html](http://pubs.vmware.com/ws6_ace2/ws/ws_vidsound_d3d_enabling_guestos.html) 

You can pretty much use those same instructions enable it in VMware Player.  If in doubt make sure to check/ask in the [official VMware forums](http://communities.vmware.com/index.jspa;jsessionid=4E1A45C6C6E0DF09887AD0410798A70C).
How do I make a virtual machine in VMware Player?

---

### Post by pytheas22 on 2008-02-27
You can't make a machine with only the player, however you can easily and legally set one up here [http://www.easyvmx.com/](http://www.easyvmx.com/)

---

### Post by indianballer24 on 2008-02-28
> **pytheas22 said:**
> You can't make a machine with only the player, however you can easily and legally set one up here [http://www.easyvmx.com/](http://www.easyvmx.com/)
Is there any way to copy an existing machine image from Server to Player?

---

### Post by pytheas22 on 2008-02-28
I don't know as I've never used Server, but presumably if you could find where the .vmx file is stored, you would be able to open it in Player as well as Server.

---

