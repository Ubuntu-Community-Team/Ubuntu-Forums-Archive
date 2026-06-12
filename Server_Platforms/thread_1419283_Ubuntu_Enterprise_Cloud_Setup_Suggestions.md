---
title: "Ubuntu Enterprise Cloud Setup Suggestions"
date: 2010-03-01
forum: Server Platforms
---

### Post by mboudro on 2010-03-01
I am an IT manager currently running Citrix XenServer on 4 HP Proliant blade servers handling instances of Windows Server 2008, Debian Lenny and Ubuntu 8.04 LTS.

Unfortunately, the free license of XenServer does not supply high availability or automatic fall-over, two features I would really like to have. The cloud structure eliminates the need for either of these as the instances are hardware independent; even more so than the standard virtualized deployment.

I have been considering several solutions, including the Ubuntu Enterprise Cloud. Before I explore this option further, I was hoping someone with more substantial experience with this particular offering could offer some suggestions and advice.

Would it be possible to deploy Windows Server 2008 on top of the UEC? I know Server '08 can be deployed on both KVM and Xen so I'm under the assumption that with a little massaging it would be deployable under UEC as well. Can anyone confirm this for me? Furthermore, does anyone have such experience and could provide any additional details?

I would need to also run two more instances of Linux based operating systems, but they can both be Ubuntu; therefore they obviously shouldn't have any trouble running properly on the cloud.

Would the UEC be the best, most cost effective solution? Does anyone have any other suggestions? I am leaning towards a private cloud implementation because it provides automatic load balancing and fall-over. Up-time is CRITICAL in my particular situation. Am I correct in thinking that the UEC could handle an entire server loss without downtime (as long as the cloud as adequate resources)?

Please note I have significant Ubuntu, virtualization and Windows server experience so the technical ability to achieve these goals will not be a problem.

If you need any additional details, please feel free to ask and I will provide as necessary.

Thanks in advance for your help.

---

### Post by suseendran.rengabashyam on 2010-03-02
Hi,

I haven't worked much on Ubuntu Enterprise Cloud, but you can take a look at the blog of one of my colleagues regarding Windows on UEC, more specifically, Eucalyptus:

[http://megam.info/2009/12/24/windows-on-eucalyptus/](http://megam.info/2009/12/24/windows-on-eucalyptus/)

---

### Post by munky99999 on 2010-03-02
> Would it be possible to deploy Windows Server 2008 on top of the UEC?
it takes some effort but yes.

> Would the UEC be the best, most cost effective solution?
uec is great for what it is.

> Up-time is CRITICAL in my particular situation. Am I correct in thinking that the UEC could handle an entire server loss without downtime (as long as the cloud as adequate resources)?
yes and no. Yes it can do the job you want it to do. No UEC isnt production quality which can be relied on to be highly available. It is good enough to implement to a lab environment and mess with it until you can reasonably know it's stable to put into production.

---

