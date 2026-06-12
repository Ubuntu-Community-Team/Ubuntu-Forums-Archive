---
title: "Ubuntu 16.04 how to remove vmware?"
date: 2017-02-26
forum: Server Platforms
---

### Post by deepakdeshp on 2017-02-26
I have installed vmware by downloading Vmware player 12.5. 
How can I remove the software? I am running the Vm player under Ubuntu server 16.04.
Also I am testing applications by running them on the Ubuntu server 16.04 but testing them by running browser on Mint 17.1 since ubuntu server does not have a browser. 
Can I Install browser on the server?

Or can I upload files directly on the Ubuntu server? At present I am forced to download files on Mint 17.1 browser . The download locations are in http format. Rather than use wget format , I would prefer to use mouse to download the files directly to the server, Now the files are being downloaded to Mint 17.1.
BTW I am running Vmware workstation under Vmware played 17.1 and under vmware player I am running the Ubuntu server.

---

### Post by darkod on 2017-02-26
Doesn't the VMware Player have removal instructions? I'm sure there must be some on the VMware website. That should help you remove it.

Installing browser and GUI on ubuntu server is not the recommended way. Since you already have another workstation with GUI (Mint) you can do any testing you want from there. The server is to serve clients, not to work directly on it.

For moving files to the server you can use scp which works over ssh port 22. Whether you use GUI (mouse) for that or not, depends on the workstations where you will be doing it from. There are GUI frontends for scp or you can run it from command line.

And in case you want to download files from internet directly to the server, then I see no reason why you wouldn't use ssh session and wget. That will download the file exactly where you need it instead of moving it around later.

---

