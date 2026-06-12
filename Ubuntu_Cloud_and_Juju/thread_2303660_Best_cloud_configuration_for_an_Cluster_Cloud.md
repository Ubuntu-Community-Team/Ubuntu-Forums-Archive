---
title: "Best cloud configuration for an Cluster /Cloud"
date: 2015-11-20
forum: Ubuntu Cloud and Juju
---

### Post by Johnny_P on 2015-11-20
Good afternoon,

I am interested to create an cloud using Ubuntu. For this I want to use Openstack. But also I see that that I can install also Juju and Maas. All of them work together very well and also have their role in cloud.

My question is: what is the order in which must be installed (1. Ubuntu Server, 2. Juju 3. Maas, 4. OpenStack)?
For my necessity is necessary all of them?
In this configuration for OpenStack can be split the instalation as default?  (Network, ...)

I must specify that the cluster will be dedicate only to: CAD, CAM, and CAE. On the cluster/cloud will never been installed site.

Thanks to all comunity for advice and support. 
I waiting your sugestion/recomandation with interest.

Keep in touch.

---

### Post by MAFoElffen on 2015-12-23
Since no one has answered this in 4 weeks, I'll give it some attention.

First an explanation of terms:

Ubuntu Server Edition- The server operating system on which server services will be installed. Openstack, Juju, MAAS are services.

OpenStack- The Cloud operating system which will run your shared applications and resources. It is is a cloud operating system that controls large pools of compute, storage, and networking resources throughout a datacenter, all managed through a dashboard that gives administrators control while empowering their users to provision resources through a web interface. (I will go into this below, where it goes like and also differs from something you mentioned) This comprises of an OpenStack controller and your OpenStack computing nodes.

Juju is like an APT repository for a cloud environment. It allows you to deploy your applications (Charms) to your Cloud nodes.

MAAS is a configurations managers that allows you to deploy standardized computing nodes.

The conflicting and/or parallel verbiage: 
Cluster usually refers is a physical or virtual replicated server, so that uptime is more likely, becuase if there is any error, services balance off /switch to another server. This is not usually needed in the cloud, as the cloud thought of as one big cooperative computing cluster.

You can install OpenStack on many server OS'es. but my preferred choice is Ubuntu. You have to have a server OS installed and configured before installing OpenStack. Configured may include your prepatory network and any subnetworks for your OpenStack Nodes, your choice of your Database, which Openstack which and Juju will use. The OpenStack controller is usually installed on one machine and nodes installed on others ... but it could be done on the same machine, if you install them in virtual, using a virtual hypervisor. That would mean that the virtual hypervisor you choose needs to be install previous to that.

MAAS and Juju could be optional and I don't think there is a matter in which order you install one or the other between them, but their configuration implies that you have a cloud (OpenStack) in place already, to point them to in their configuration.

What you need to ask yourself is: What kind of services do you need provided? What is the initial scope of those provided services? How big will that scope grow over time?

A private cloud could provide for unlimited growth and weigh in to implied up-time ... But is one of many solutions to your needs. It is your decision if that investment fits your business needs.

The next question is if the vendor for your Computer Aided Drafting, Computer Aided Manufacturing and Computer Aided Engineering software that you are presently using offers a cloud based product and it's licensing structure. I'm sure that this might be a consideration to your decisions. Anything other than what you r are presently using might require employee retraining and some conversions to implement. (I know that all "CNC" do not talk the same specifics.)

---

### Post by Johnny_P on 2015-12-25
Good afternoon,

Thank you very much for answer.
It is very easy and clear explained. If I will need for the future other advice from your side, I will post with trust.
This thread also can assigned as solved.

Thank you for support and advice.
Keep in touch.

---

### Post by matt_symes on 2015-12-25
> **Johnny_P said:**
> This thread also can assigned as solved.

Thread marked as [SOLVED]

---

