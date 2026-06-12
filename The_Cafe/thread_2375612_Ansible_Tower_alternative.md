---
title: "Ansible Tower alternative"
date: 2017-10-26
forum: The Cafe
---

### Post by satimis on 2017-10-26
Hi all,


I'm searching FREE alternatives on Open Source for Red Hat Ansible Tower.

Red Hat Ansible Tower 3.2.1
[https://access.redhat.com/products/ansible-tower-red-hat](https://access.redhat.com/products/ansible-tower-red-hat)

Ansible Tower
[https://www.ansible.com/tower](https://www.ansible.com/tower)


In my search I found follows;

1)
Semaphore - Ansible Tower alternative
[https://blog.utar.co/blog/semaphore-ansible-tower-alternative](https://blog.utar.co/blog/semaphore-ansible-tower-alternative)
[https://ansible-semaphore.github.io/semaphore/](https://ansible-semaphore.github.io/semaphore/)

2)
ansible-cmdb
[https://alternativeto.net/software/ansible-cmdb/](https://alternativeto.net/software/ansible-cmdb/)

3)
Tensor - Ansible Tower free alternative
[https://www.youtube.com/watch?v=FqwprZrIxKE](https://www.youtube.com/watch?v=FqwprZrIxKE)

4)
Foreman vs Ansible Tower
[https://www.upguard.com/articles/foreman-vs.-ansible-tower](https://www.upguard.com/articles/foreman-vs.-ansible-tower)

To my understanding Semaphore seems to be a good choice.  Please shed me some light.

Thanks

Regards
satimis

---

### Post by TheFu on 2017-10-26
[https://github.com/ansible/awx](https://github.com/ansible/awx)

---

### Post by satimis on 2017-11-10
> **TheFu said:**
> [https://github.com/ansible/awx](https://github.com/ansible/awx)
Thanks

I'm now busily engaged in testing oVirt (oVirt engine, oVirt node etc.) and nested virtualizaion.  After finished I'll test awx

satimis

---

### Post by TheFu on 2017-11-11
Does oVirt run on Ubuntu? Didn't think it had been ported.  These are the Ubuntu Forums, after all.

---

### Post by silver-lynx on 2017-12-04
Polemarch
[https://github.com/vstconsulting/polemarch](https://github.com/vstconsulting/polemarch)

---

### Post by satimis on 2017-12-05
> **silver-lynx said:**
> Polemarch
[https://github.com/vstconsulting/polemarch](https://github.com/vstconsulting/polemarch)
Hi,

Thanks for your advice and link

Following "Ubuntu/Debian installation" I have Polemarch installed on VM of Oracle VirtualBox.  Also I have both polemarchweb and polemarchworker started.  Please see attached file.

Host - Ubuntu 16.04 desktop
VM - Ubuntu 16.04 desktop
Oracle VirtualBox

Then what will be next?  How to use it?

On 
Welcome to Polemarch’s documentation!
[http://polemarch.readthedocs.io/en/latest/](http://polemarch.readthedocs.io/en/latest/)

Where shall I start?

Please advise.  Thanks

Regards
satimis

---

### Post by silver-lynx on 2017-12-11
[http://[your-vm-ip]:8080/](http://[your-vm-ip]:8080/)
Default creditials admin:admin
Create project and inventory with hosts and groups and start any playbooks or modules.

---

### Post by satimis on 2017-12-12
> **silver-lynx said:**
> [http://[your-vm-ip]:8080/](http://[your-vm-ip]:8080/)
Default creditials admin:admin
Create project and inventory with hosts and groups and start any playbooks or modules.

Thanks

Regards
satimis

---

