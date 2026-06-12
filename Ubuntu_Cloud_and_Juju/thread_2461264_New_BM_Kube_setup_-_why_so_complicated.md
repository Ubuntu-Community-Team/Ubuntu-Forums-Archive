---
title: "New BM Kube setup - why so complicated?"
date: 2021-04-27
forum: Ubuntu Cloud and Juju
---

### Post by tman24 on 2021-04-27
I know this has probably been asked many times, as Kube is HARD, initially at least. We're looking to setup a new bare metal cluster on-prem. We have the hardware (servers/10GbE switches etc), but I'm struggling with the actual setup. We believe MaaS+JuJu would be the best solution for us, maybe with Portainer as the management layer and some Ceph storage, but finding a step-by-step guide that covers all this is almost impossible. Plenty of snippets here and there, but they always seem to assume you have some Kube experience, and we're coming in from almost nothing (we do have lots of Ubuntu experience though, and have 20.04 deployed and ready). For example;

sudo juju add-cloud --client

Fair enough, select 'maas', but then you're prompted for the API endpoint URL - is this something you just make up, or does it have to be something specific? Which port for example? Assumptions on parts of the setup like this are not good.

Does juju also initialize maas, or do you need to do sudo maas init before juju? What are examples of the input answers required? Is 'full' Charmed Kube the best choice, or Kube core? In all my worst nightmares, I never thought this setup phase from scratch would be so awkward - surely someone must have taken pity on admins and done a step-by-step guide - with explanations (not assumptions) - for this?

Ultimately, I want a production setup that can integrate with Gitlab Enterprise, but first steps, trying to get some form of Kube cluster up and running. One of the main issues with Kube seems to be just too much choice and variation on doing things - it's almost overwhelming.

Thanks

---

### Post by TheFu on 2021-04-27
No clue what "Kube" is.

[https://ubuntu.com/kubernetes/install](https://ubuntu.com/kubernetes/install) might help?  Or not.

I've never used juju nor MAAS since we only have 3 physical server nodes. Always seemed overly complex for our needs. We use simple virt-manager + libvirt + kvm to manage new systems and Ansible to do the configurations.

---

