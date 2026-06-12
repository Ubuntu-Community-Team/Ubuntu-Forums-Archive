---
title: "Safe way to share and access /var/www with samba?"
date: 2008-05-29
forum: Server Platforms
---

### Post by peap on 2008-05-29
I've been running Ubuntu Desktop LAMP for a few years now but I never really cared about security as it's been working so nicely out of the box.

Today (after continuous problems with my 8.04 desktop) I finally installed 8.04 Server instead. Things are working but I would like to be able to get samba access to my webroot (/var/www) in a "safe" way. Samba is up and running and my test shares work just fine.

I've read that chown /var/www isn't a good way to remotely access it so I would like to get tips on how to approach it this time.

I'm accessing my webserver from my iMac and would like to have a folder mounted on my iMac with direct and full access to my ubuntu webroot, as safely as possible with samba.

I'd appreciate some help as I haven't been able to find any that fits my needs (this can't be an unusual setup, can it?) and find that a bit strange...

Perhaps some kind of alias/link will do the trick? I want access to the very bottom (i.e. to [http://myserver/](http://myserver/) and not [http://myserver/~user](http://myserver/~user) or anything like that) of the web root.

/ Johan

---

### Post by erwall on 2008-05-29
I'm doing just this but w/NFS, that is, accessing shared files on an ubuntu box from a mac that mounts the NFS volumes at login.  The owner/group stays constant no matter who drags what in.  Is NFS an option for you?  This is the relevant line in my /etc/exports
```
/var/www 192.168.1.100/24(rw,async,all_squash,insecure,no_subtree_check,anonuid=1000,anongid=1000)
```

---

### Post by peap on 2008-05-30
If NFS does the job in a safe and easy way I'm happy. I just haven't used anything else than samba to share files from my ubuntu box before.

Does this link describe a good way to do it?
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by erwall on 2008-05-30
> **peap said:**
> If NFS does the job in a safe and easy way I'm happy. I just haven't used anything else than samba to share files from my ubuntu box before.

Does this link describe a good way to do it?
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Yep, check this out too...

[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

Note you must use different options if connecting from a mac, refer to my example above.  After you mount the drive you can drag it to the dock for a shortcut that will mount when clicked.  NFS is worth a shot, it's much faster, easier, and simpler than samba imo.  This utility made it easy to mount shares on a mac:

[http://jm.marino.free.fr/index.php?switch=sw_&title=AutomountMaker](http://jm.marino.free.fr/index.php?switch=sw_&title=AutomountMaker)

---

### Post by peap on 2008-05-30
How about security? I run a DHCP network with reserved IP's by mac address, will this be sufficient when using access by IP as in your example?

Thanks for your informative and quick replies. Yet another proof that Ubuntus best feature is the community. :)

---

### Post by erwall on 2008-05-30
> **peap said:**
> How about security? I run a DHCP network with reserved IP's by mac address, will this be sufficient when using access by IP as in your example?

Thanks for your informative and quick replies. Yet another proof that Ubuntus best feature is the community. :)
I'm no nfs expert but I don't see why not, unless you need to have different access levels on a single computer.

---

### Post by peap on 2008-05-31
I can't seem to get this right. I'm running OSX Tiger, can that be a problem perhaps?

My line in /etc/exports:
```
/var/www 10.0.1.2/24(rw,async,all_squash,insecure,no_subtree_check,anonuid=1000,anongid=1000)
```

I followed the steps in SettingUpNFSHowTo and tried to connect with finder and the software you suggested but it won't work.

I'm not sure on what to do. I'd like to confirm from another ubuntu comp that I can access the nfs share but I only have one PC. Will PPC Ubuntu boot on a iBook G4 or iMac G5 now? I tried last year but my G5 froze at bootup.

---

### Post by erwall on 2008-05-31
You should be able to boot with a livecd on any intel machine to try it out

---

### Post by peap on 2008-05-31
I actually get the same error from OSX as I get when running Ubuntu:

```
sudo mount 10.0.1.3:/var/www /home/ubuntu/Desktop/www
mount.nfs: mount to NFS server '10.0.1.3' failed: RPC Error: Program not registered
```

I then checked everything again and I found a slight error in my hosts.allow, now it's working from ubuntu. I'll reboot OSX to try it now, cross your fingers.

Yeay! It worked... NFS actually is easier now that I got it working. Thank very much for all your help!

---

### Post by erwall on 2008-06-01
> **peap said:**
> I actually get the same error from OSX as I get when running Ubuntu:

```
sudo mount 10.0.1.3:/var/www /home/ubuntu/Desktop/www
mount.nfs: mount to NFS server '10.0.1.3' failed: RPC Error: Program not registered
```

I then checked everything again and I found a slight error in my hosts.allow, now it's working from ubuntu. I'll reboot OSX to try it now, cross your fingers.

Yeay! It worked... NFS actually is easier now that I got it working. Thank very much for all your help!
No problem, glad you got it sorted out and working!

---

### Post by peap on 2008-06-01
Right now I'm experimenting with NetInfo and Automount... hopefully I'll be able to prevent my clients from stalling if the server is unreachable.

Got any tips on that? I don't find the available software very useful and I prefer having 100% control of what I'm doing when modifying OSX.

---

