---
title: "Juju Bootstrap Error"
date: 2016-04-27
forum: Ubuntu Cloud and Juju
---

### Post by Maile_Halatuituia on 2016-04-27
I install MAAS with no issue, enlist 2 nodes and commissioned and both are in READY state now. I install juju with not problem and to the point of running juju bootstrap command i cannot go pass with juju complaining regarding my storage. Below is the error on my nodes on MAAS 
[COLOR=#333333][FONT=Ubuntu][SIZE=2][B]Storage
No storage information. Commissioning this node will gather the storage information.
Specify a storage device to be able to deploy this node.
Mount the root '/' filesystem to be able to deploy this node.[/B]
[/SIZE]
[/FONT][/COLOR]
Like i said i have commissioned the nodes but from this error it seems MAAS does not recognize my disks or something like that.
Then i go to this [http://www.ubuntu.com/download/cloud/install-openstack-with-autopilot](http://www.ubuntu.com/download/cloud/install-openstack-with-autopilot) for a try and yet stuck on the same error as shown on the command.log file ....
i am not sure what else to do .... please if anyone can help as i have been with this issue for over two weeks now ....thanks

---

### Post by Maile_Halatuituia on 2016-04-27
Here is the additional error from manually running juju quickstart

Bootstrap failed, destroying environment
ERROR failed to bootstrap environment: cannot start bootstrap instance: gomaasapi: got error back from server: 400 BAD REQUEST ({"storage": ["Specify a storage device to be able to deploy this node.", "Mount the root '/' filesystem to be able to deploy this node."]})

---

### Post by Maile_Halatuituia on 2016-04-30
no one has any idea of my issue ???

---

### Post by blakehenderson on 2016-05-02
click on your node and go to the storage section ---

Under file system you should see a disk mounted as /   <-- is it there?

If nothing there, is there something available under   Available disks and partitions  ?

Sounds to me like you just don't have a drive setup as /

---

### Post by Maile_Halatuituia on 2016-05-02
> **blakehenderson said:**
> click on your node and go to the storage section ---

Under file system you should see a disk mounted as /   <-- is it there?

If nothing there, is there something available under   Available disks and partitions  ?

Sounds to me like you just don't have a drive setup as /
I believe there is non that's why juju complain even when run auto pilot open stack installer, it reports the exact same error.

FYI
On BIOS of both my machines it reports 4 disk for my HP server and one 1TB for my Acer Desktop PC. And these two machines were perfect when previous OS install on them before enlist on MAAS.
The strange thing to me is MAAS did not report any error regarding the two nodes while commission...
Here is the Storage Detail of one of the nodes. I hope it will shed some light way forward.

[COLOR=#333333][FONT=Ubuntu][h=2]Storage[/h][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]
[LIST]
[*]No storage information. Commissioning this node will gather the storage information.
[/LIST]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]
[LIST]
[*]Specify a storage device to be able to deploy this node.
[/LIST]


[LIST]
[*]Mount the root '/' filesystem to be able to deploy this node.
[/LIST]

[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][h=3]File systems[/h][COLOR=#888888][/COLOR]
[COLOR=#888888]Name[/COLOR]
[COLOR=#888888]Size[/COLOR]
[COLOR=#888888]Mountpoint[/COLOR]
[COLOR=#888888]File system[/COLOR]

No filesystems defined.

[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][h=3]Available disks and partitions[/h][COLOR=#888888][/COLOR]
[COLOR=#888888]Name  Model  Serial[/COLOR]
[COLOR=#888888]Boot[/COLOR]
[COLOR=#888888]Size[/COLOR]
[COLOR=#888888]Device Type[/COLOR]
[COLOR=#888888]File system[/COLOR]
[COLOR=#888888]Tags[/COLOR]
[COLOR=#888888][/COLOR]

No available disks or partitions.

Create RAID Create volume group Create cache Set Create bcache[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][h=3]Used disks and partitions[/h][COLOR=#888888]

[/COLOR]
[COLOR=#888888]Name  Model  Serial[/COLOR]
[COLOR=#888888]Boot[/COLOR]
[COLOR=#888888]Device type[/COLOR]
[COLOR=#888888]Used for[/COLOR]

No disk or partition has been fully utilized.




[/FONT][/COLOR]

---

