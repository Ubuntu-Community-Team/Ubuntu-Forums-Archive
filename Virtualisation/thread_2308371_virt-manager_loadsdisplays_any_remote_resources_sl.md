---
title: "virt-manager loads\displays any remote resources slowly"
date: 2016-01-02
forum: Virtualisation
---

### Post by elico on 2016-01-02
I have two kvm hypervisors ubuntu 14.04 host for a while and I am having very slow virt-manager display and response times.
When I am connecting using ssh from an ubuntu desktop I am getting the list of vm's and or listed files in some storage it takes more then 10 seconds most of the time to get just the list of things to show on the windows.
If I am running the same operations via ssh using the cli tools it works great.
If I am using the Fedora virt-manager to connect the ubuntu server the virt-manager will show everything fine.
So my conclusion is that the ubuntu virt-manager is doing something wrong compared to the Fedora one.

Do I file a bug on such a thing? if so where? Also have anyone experienced such an issue?

* I have about 30 VMs on each hypervisor and about the same amount of vm disks image files at the local storage

---

### Post by elico on 2016-01-02
I wanted to make sure how things are and it seems that using a new version of virt-manager from: [http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)
Solves the slowdowns, however there is a drawback and I cannot see in the details overview graph the memory usage.

---

