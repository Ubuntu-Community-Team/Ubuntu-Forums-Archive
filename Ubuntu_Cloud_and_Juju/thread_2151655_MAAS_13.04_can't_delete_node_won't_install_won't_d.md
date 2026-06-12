---
title: "MAAS 13.04 can't delete node won't install won't deploy"
date: 2013-06-05
forum: Ubuntu Cloud and Juju
---

### Post by attrezzop on 2013-06-05
I was having trouble with MAAS in 13.04 and wasn't finding any good documentation on others' first experiences and impressions of it so I've edited this post to give back a little and relay what I have learned.

First adding a MAAS in a node is divided into a few steps. Enlist, Commission, Deploy, and Ready. The remote install goes something like this:

First you boot up and PXE or use the install media to Enlist the machine. This is the step where the new node tells the MAAS controller that it wants to be included in the cluster. It will appear on the web UI as in the node and the pie chart will be white at this step. The machine is now "declared". It will automatically power down.

The next step involves viewing the details about the node and accepting their configuration. Here we'd add wake-on-lan details and mac addresses and the version of linux you want to install. Then click "Accept and Commission" in the web ui. Commissioning will pull additional information about the machine (processor number and amount of ram) and queue the node up to be activated and deployed by a MAAS user or administrator. It will automatically power down at this step as well.

The final step assumes you have juju installed. It will work if you don't have juju installed it's just that from the ui you can't remove a node that doesn't have juju installed. It also **requires** you have a public ssh-key in your profile so you can "Start" the node. Clicking Start in the ui from the details section of the node assigns the node to that user and on the next pxe boot will install the desired version of linux. It's worth noting here that preseed is the ubuntu way of auto-responding for auto-install. I had trouble with the installer the first time because my primary hard disk didn't have a partition system on it. When I booted to a rescue environment and parted then mklabel gpt and quit on the next boot ubuntu installed correctly. Read up on preseed and take a look at the compiled preseed document in the web ui if you're having trouble installing. It may require some tweaks.

I've found out in 13.04 you CAN delete a node once it has been deployed but it's tricky. You can't do this from the UI because the UI assumes you have the node registered in juju and need to delete the juju services first. You need to use the maas-cli to do this.

First login to the maas server using:

maas-cli login username url-to-server-ie-http//localhost/MAAS MAAS-key-here

Then figure out what groups you have set up. The cli refers to auto-generated uuids and they're long and complicated. It's easiest to do this via ssh so that you can copy/paste.

maas-cli username node-groups list

The group name should be the DNS suffix you gave when you installed the controller.

maas-cli username node-group list-nodes groupuuid

This will return node uuids... if you have multiples you'll have to read through each one to find the one you're looking for.

maas-cli username node read nodeuuid

Finally you can stop and remove the node.

maas-cli username node stop nodeuuid
maas-cli username node release nodeuuid
maas-cli username node delete nodeuuid

---

### Post by attrezzop on 2013-06-07
Here are a few resources that help. Although a good deal of the information is centered around 12.04 and I don't have any experience with that version. Still most of it is helpful.

[http://www.sebastien-han.fr/blog/2012/05/04/maasive-round-2/](http://www.sebastien-han.fr/blog/2012/05/04/maasive-round-2/)

[https://help.ubuntu.com/lts/installation-guide/powerpc/appendix-preseed.html](https://help.ubuntu.com/lts/installation-guide/powerpc/appendix-preseed.html)

Also logs are in /var/logs/maas these can be helpful. In my case to figure out what was going on I had to watch the pxe boot and take pictures with a smartphone periodically. So far I haven't been able to get Wake-on-lan working properly. I don't know if this was meant to be a post-install thing or not though. In my case I had to manually start the machine three times. (One to enlist, One to commission, and One to deploy)

---

