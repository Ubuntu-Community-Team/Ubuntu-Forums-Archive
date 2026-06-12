---
title: "MAAS Landscape issue."
date: 2017-08-01
forum: Ubuntu Cloud and Juju
---

### Post by sirtcp on 2017-08-01
Hi,

Sorry i dont know if this is the right place to right it down i am new to ubuntu and trying to play with Openstack Conjure-up Juju and MAAS. i tried really hard to reach the point where i successfully install landscape with conjure-up  now at the bottom of the page i see check list for the required deployment.  which is as under.

**Checklist**

     
[LIST]
[*]                    Registered a MAAS region controller 
[*]                    Connection to the MAAS region controller available 
[*]                    At least three machines with more than one           disk have been commissioned 
[*]                    At least one of the commissioned machines must have multiple network           connections. 
[/LIST]

There must be at least one machine, available in the MAAS cluster,           that has two or more network interfaces connected to the networks           that are defined in MAAS.         

now the problem point is i always see the last option red no matter what i do. i double check my machine. i have 8 machines in total of which 2 are physical nodes and 6 are logical nodes proxmox(KVM) i checked and confirm that there is a single machine with Local and Public IP. however i still see this red line. which is really annoying. 
Please help me out. i am working on this test lab for more then 5 days and my head is really melting out working on this testlab. 

Any help will be highly appreciated.

Thanks,
Yousuf

---

### Post by slickymaster on 2017-08-01
*Thread moved to **Ubuntu Cloud and Juju**.*

---

### Post by tschuh on 2017-09-06
I have a similar issue.  I've got 9 blades, each with 6 interfaces.  I'm only using two interfaces on each blade.  One for PXE/Management one for Public.  I can get to the internet from either interface on any of the nodes and MAAS sees all of the interfaces without issue so I'm a bit perplexed.  Lack of a configuration guide is causing me great grief.

---

### Post by pal-arlos on 2017-10-06
I followed this; [http://www.openstackbasement.com/conjure-up-2-0](http://www.openstackbasement.com/conjure-up-2-0) that took me from baremetal, MAAS, conjure-up, Landscape, deployed Openstack... 
The 'issue' I had was assuming that I could run all networking on one interface but with VLAN separation (did not work). Furthermore, it seemed more likely to succeed if the PXE network is on the lowest interface, MAAS can commission the nodes, but juju deployment of Landscape, and subsequently OpenStack did not work. Guess that it assumed that the lowest interface was used for pxe (should be able to read that from maas). 

/Patrik

---

### Post by xiordanidis on 2017-10-06
Probably there is a solution or we are only 3 guys who do this in the entire world. Openstack is already a complicated thing and many prophets around the world evangelize the "easy" deployment. I believe it's not easy and unfortunately, the false promises lead to misconceptions. This specific problem can lead you to depression. I believe it is fairer to tell us "Pay us" as all these demos, youtubes etc. where evangelists appear with nice gestures etc.

---

### Post by pal-arlos on 2017-10-11
Think the original poster may have solved it, as no feedback/additional input has come.. 
OpenStack is not that complicated (sure, it depends what you compare to), but its 'just' a bunch of services that needs to be configured and their configurations are interdependent to some extent. Then this has to be mapped to a physical/logical world.. What I think is omitted/simplified/hidden? is that stage. 

/P

---

