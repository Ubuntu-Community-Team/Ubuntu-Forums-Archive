---
title: "Ubuntu Server Eucalyptus Testers Needed"
date: 2009-10-09
forum: The Fridge Discussions
---

### Post by TheFridge on 2009-10-09
Koalas love eucalyptus, they spend three hours a day munching away on the sturdy plant. Likewise, Ubuntu 9.10 Karmic Koala loves Eucalyptus, the Open Source system for implementing on-premise private and hybrid clouds using the hardware and software infrastructure that is in place, without modification. This allows you to run your own private cloud on your own hardware and infrastructure. Sound interesting? It really is, and this a rocking new feature in the new Ubuntu Server edition.

 As we build to release, we could really use your help to make sure that Karmic Koala&#8217;s Eucalyptus support is rock solid. This post outlines how you can test this functionality, and provide some valuable feedback.

 **What You Will Need**

 You need two machines, one of which has to be capable of handling [KVM]([https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)). The following command will check to see if your CPU has the correct VT extensions for running KVM (though you might have to additionally enable VT in your BIOS):

 egrep '(vmx|svm)' /proc/cpuinfo

 Each machine will also need 1GB of RAM and 80GB of free space. Documentation for all this is provided [here]("http://testcases.qa.ubuntu.com/System/Eucalyptus").

 You will also need to [download the latest daily Ubuntu Server ISO image]("http://cdimage.ubuntu.com/ubuntu-server/daily/current/") and burn it to CD.

 **Performing The Tests**

 Testing the *Ubuntu Enterprise Cloud* support with Eucalyptus involves three steps: setting up the cluster, the nodes and activating the cloud. Let&#8217;s look at it in three easy steps:

 The Cluster Machine

 This machine will control the nodes, it does NOT need KVM support. You can install it via the Ubuntu Enterprise Cloud task in the installer and select Cluster as the type.

 Step-by-step instructions are [here]("http://testcases.qa.ubuntu.com/Install/ServerECluster").

 The Nodes

 After you have installed a controller you are ready to add *nodes*. This is the machine that needs the KVM support. Install it via the *Ubuntu Enterprise Cloud* task in the installer and select *Node* as the type.

 Step-by-step instructions are [here]("http://testcases.qa.ubuntu.com/Install/ServerENode").

 Activating Your Cloud

 After you have got the cluster and the node all installed and ready to go you&#8217;re ready for the final steps which are available [here]("http://testcases.qa.ubuntu.com/Install/ServerEConfig").

 **Testing and Filing Bugs**

 Each of these steps should be relatively pain free, after that you&#8217;re ready to start testing Eucalyptus. 

 The [Eucalyptus Getting Started Guide]("http://open.eucalyptus.com/wiki/EucalyptusGettingStarted_v1.5.2") contains commands you may want to try. Please Note: the Getting Started Guide is for version 1.5.2. Karmic Koala includes version 1.6, so there are some differences involved. You can however take a look to the on going work of the [version 1.6 documentation]("http://open.eucalyptus.com/wiki/Documentation_v1.6").

 Bugs should be filed in Launchpad in the Ubuntu eucalyptus package. You can see this list of bugs at [https://bugs.launchpad.net/ubuntu/+source/eucalyptus](https://bugs.launchpad.net/ubuntu/+source/eucalyptus). Bugs should be reported using the ubuntu-bug tool. This tool is shipped with Ubuntu Server. To file a bug, simply type in:

 ubuntu-bug eucalyptus

 This tool will send relevant debugging content to Launchpad to help identify and resolve the bug. More details on ubuntu-bug can be found [here]("https://help.ubuntu.com/community/ReportingBugs").

 **Discussion and Getting Help**

 Discussion about Eucalyptus can be posted directly to the [ubuntu-devel]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel") mailing list and you are welcome to join the server development team in the #ubuntu-server IRC channel on irc.freenode.net.

 

[More...](http://fridge.ubuntu.com/node/1925)

---

