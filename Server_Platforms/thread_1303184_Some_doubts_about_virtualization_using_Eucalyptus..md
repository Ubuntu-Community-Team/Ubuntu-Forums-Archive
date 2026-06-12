---
title: "Some doubts about virtualization using Eucalyptus."
date: 2009-10-27
forum: Server Platforms
---

### Post by jroliv on 2009-10-27
Hello guys, I just started to deploy a Private Cloud using Eucalyptus on the koala server edition, and I am studying a lot about the concept of the virtualization, hipervisor, kind os hypervisor (kvm, xen,.. ).
On our lab, we have the node controler, one server (node) that has virtualization support on the processor, and another that doens't.
What I would like to ask is:

Can We make this cloud work? With one node controler, one server using Xen hypervisor (on koala) and another using KVM?

Is there any difference for the node controller the hypervisor that I am using on the servers?

Another "dummy" question: when I run a instance, all its resources will be used on ONE node, or... the resource is shared on more than ONE nodes?

I really want to make this running and send the feedback to help improving this version of Ubuntu Server.

thanks!!

---

