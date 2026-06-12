---
title: "Build a backup server with syncing capability"
date: 2017-02-24
forum: Server Platforms
---

### Post by goginos on 2017-02-24
Hello community members!

I want to build a file server to use it as backup server for a small network with ten windows clients. The current network topology is as shown in the picture attached.
The basic requirements are:
[LIST=1]
[*]Being able to copy every file created in any of the clients. More specifically, I would like the server to be able to monitor specific folders on the network or even entire hard drives of the clients and make real time copy as soon as a file is created or updated, thus being able to sync. This operation is similar to cloud services like Dropbox, Onedrive or Google Drive which they are able to monitor specific folders and upload them on server somewhere in the cloud. The difference is that I don't demand to upload it on the cloud, rather than to a local server. 
[*]The shared folders in the local backup server will be accessible from each one of the windows clients. 
[/LIST]
Future requirements of the backup server are:
[LIST=1]
[*]To be accessed via internet with a VPN 
[*]To have a security level such as SSH when is accessed via internet 
[/LIST]

Of course I am only asking for general guidelines and advises, for example which programs are required to do this (samba?), what to read, or similar how to's. 

Therefore for I ask you to be tolerant with my novice question and thank you in advance.

---

### Post by volkswagner on 2017-02-24
Typically in an environment with fixed workstations (not portable devices) a central fileserver with share(s) will be used for
all files related to the company/organization. This file server will then be backed up regularly.

You may want to look into Owncloud or Nextcloud which can be run on a local server.

What version of Windows are the workstations running? Have you tried Microsoft's File History? I'm not
sure about realtime sync but it can do at least hourly.

---

