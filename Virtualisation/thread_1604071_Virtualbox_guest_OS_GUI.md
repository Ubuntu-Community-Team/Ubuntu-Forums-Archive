---
title: "Virtualbox guest OS GUI"
date: 2010-10-23
forum: Virtualisation
---

### Post by holocene on 2010-10-23
I know that in VB, I can install linux guests and interact with the guest  using the guests GUI. 

Is there an Ubuntu user here who could say if Xenserver provide the same functionality? IOW, would I have access to the guest OS gui?

I wish Xen esxi supported Ubuntu guests natively. 

Regards
Steve.

---

### Post by holocene on 2010-10-23
Updating on my progress on this.

The problem with the GUI display concerned templates.

Xenserver allows VM's to be created based on templates, which seems to supply info to the hypervisor particlar to that client. 

Oddly, choosing a template that matches the guest OS (initially for me CentOS as it is "supported"), resulted in no guest desktop GUI available, just  the text console. 

Choosing the "Other" template and installing CentOS resulted in a guest OS with a working desktop GUI. 

While a novice can do a lot with Xen just taking the defaults, it does make you appreciate the very fine interface that VirtualBox has. 

<ramble mode=on>

This is probably all old hat to you all, but under Xen, you mostly administer the server remotely, which also serves to present the guest OS screen. Xenserver is also very nearly bare metal. 

I tried vmware first, but ran into problems on my first guest install, so I switched to Xen. I may retry vm later. 

I feel good I got this far, but of course I have just scratched the surface. 

I will attempt to install Ubuntu 10.10 next as a guest under Xen.

I want to try KVM but the documentation seems a little "short". 

Regards
Steve.

---

