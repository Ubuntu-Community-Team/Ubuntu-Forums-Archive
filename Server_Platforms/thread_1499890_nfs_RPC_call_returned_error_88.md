---
title: "nfs: RPC call returned error 88"
date: 2010-06-02
forum: Server Platforms
---

### Post by rawdmon on 2010-06-02
I recently upgraded a couple of my systems from 8.04 LTS to 10.04 LTS.  I had no issues with nfs prior to the upgrade.  After the upgrade I am occasionally seeing the following messages:

[269280.410969] nfs: RPC call returned error 88
/mspfiles: Socket operation on non-socket

mspfiles being the share name.

This never used to happen on 8.04.  Generally the error "Socket operation on non-socket" points to a coding error.  Could this be a bug in the kernel?  Has anyone else come across this?

The only other recent reference that I found to the same errors was in this comment on the OpenSUSE bugtracker: [https://bugzilla.novell.com/show_bug.cgi?id=557760#c10](https://bugzilla.novell.com/show_bug.cgi?id=557760#c10)

It seems as though it is handling loss of connectivity less gracefully than it did before.

Does anyone have any suggestions on how to fix this?  I can't really upgrade any more of my servers until this is fixed as we are heavily dependant on nfs.

---

### Post by arrrghhh on 2010-06-02
Are you using the same version of NFS on the server as on the client?  I don't know how well different versions of NFS communicate with eachother...

---

### Post by rawdmon on 2010-06-02
> **arrrghhh said:**
> Are you using the same version of NFS on the server as on the client?  I don't know how well different versions of NFS communicate with eachother...

Yeh, I was thinking about that yesterday but wasn't sure that that might be the cause.  I'll check that out.  Thanks.

If anyone else has suggestions I'm all ears.

---

### Post by rawdmon on 2010-06-02
Well, the client and the server aren't the same package versions, but they are both using NFSv3.

---

### Post by arrrghhh on 2010-06-02
> **rawdmon said:**
> Well, the client and the server aren't the same package versions, but they are both using NFSv3.

That should be OK then... I thought there was an issue with this with v3, have you tried v4?  I'm guessing you were using v3 previously tho...

---

### Post by rawdmon on 2010-06-02
No we haven't tried v4, but yes we were using v3 previously without issue.

---

### Post by Jeroensum on 2010-06-03
What options are you using to mount the shares, have you for instance played around with hard vs soft mounting or cache sizes?
Also, what settings do you have in you /etc/exports file on the server for this share?

---

### Post by rawdmon on 2010-07-14
We're not using anything special for the options, and besides, the options haven't changed from before when it was working perfectly fine.  Something has changed in 10.04 to cause these nfs issues.  There must be a bug in the code somewhere.

When I unmount/remount the nfs share I also see this in dmesg:

[277015.111151] svc: failed to register lockdv1 RPC service (errno 97).

I also see errors as follows...

Jul 14 05:28:34 lab01 snmpd[818]: /mspfiles: Socket operation on non-socket

That error is always a result of bad coding.  There has to be a bug somewhere.

---

### Post by arrrghhh on 2010-07-14
We'd need to see your exports file and how you're mounting to help.

Also, if this is a production server why didn't you leave it on 8.04?  10.04 isn't exactly designed for production machines.  If you need stability, stick with 8.04.

---

### Post by rawdmon on 2010-07-14
With 10.04 being the latest LTS I assumed it would be stable enough for production.  Also, the 2 machines that were upgraded are in production but they are for our own internal stuff instead of our customers, so it's not as big of a deal, which is why I'm using them as upgrade pilots.

---

### Post by rawdmon on 2010-07-14
Here are the 2 ways that I've tried mounting (fstab)...

The original:

hostname.of.server:/export/mspfiles /mspfiles nfs rsize=8192,wsize=8192,timeo=14,intr

I've also tried:

hostname.of.server:/export/mspfiles /mspfiles nfs rw,hard,intr

The exports file is as follows:

/export/mspfiles    192.168.0.0/255.255.255.0(no_root_squash,rw)
/export 192.168.0.0/255.255.255.0(no_root_squash,rw,fsid=0)

(I changed the IP and netmask from the originals).

Any help is appreciated.

---

### Post by rawdmon on 2010-07-14
Here's the same bug reported for redhat:

[https://bugzilla.redhat.com/show_bug.cgi?id=605355](https://bugzilla.redhat.com/show_bug.cgi?id=605355)

---

### Post by arrrghhh on 2010-07-14
> **rawdmon said:**
> With 10.04 being the latest LTS I assumed it would be stable enough for production.  Also, the 2 machines that were upgraded are in production but they are for our own internal stuff instead of our customers, so it's not as big of a deal, which is why I'm using them as upgrade pilots.

I typically wouldn't run a production server in anything "new".  I want to *know* that it'll all be good - I usually wait until at least the .1 update before going to it in production.

Hopefully someone can help out with the rest of that info you provided, nothing's jumping out at me...

---

### Post by rawdmon on 2010-07-14
> **arrrghhh said:**
> I typically wouldn't run a production server in anything "new".  I want to *know* that it'll all be good - I usually wait until at least the .1 update before going to it in production.

Hopefully someone can help out with the rest of that info you provided, nothing's jumping out at me...

We wanted to upgrade due to security vulnerabilities in the older versions of the kernel.  The newer version of the kernel seems to have a bug relating to nfs, and it's not distro specific either.  So far I've seen reports of it in OpenSUSE and RedHat (I linked to both bug reports in this thread).

Is this the same arrrghhh from #zenoss?

---

### Post by arrrghhh on 2010-07-14
I do poke around #zenoss now-and-then... Still trying to get it to work right in our environment.  Who are you in there?

I do understand the upgrade for security vulnerabilites.  Have you tried looking at a newer kernel?  Or even the dreaded downgrade?

---

### Post by rawdmon on 2010-07-14
> **arrrghhh said:**
> I do poke around #zenoss now-and-then... Still trying to get it to work right in our environment.  Who are you in there?

I do understand the upgrade for security vulnerabilites.  Have you tried looking at a newer kernel?  Or even the dreaded downgrade?

It's rmatte ;)

Not really looking to downgrade and I'm not in any rush to upgrade too, just trying to get this sorted out first.  If I have to file bug reports with kernel/nfs developers to get it fixed and wait months then so be it, but I want to work steadily towards an upgrade.

Just seeing if there's some config options that I'm not aware of which could remedy the situation.

---

### Post by arrrghhh on 2010-07-14
Nice!  Funny 'seeing' you here.  Based on those bug reports, it's definitely at the kernel level.  I know Ubuntu has its own kernel dev team, did you check to see if the bug has been reported there?

I guess I should ask, but what package are you using to install nfs?  I believe all you need is nfs-kernel-server and portmap for the server, and nfs-client and portmap for the client machines.  Probably not relevant, since most of the NFS stuff is in the kernel now.

---

### Post by rawdmon on 2010-07-14
> **arrrghhh said:**
> Nice!  Funny 'seeing' you here.  Based on those bug reports, it's definitely at the kernel level.  I know Ubuntu has its own kernel dev team, did you check to see if the bug has been reported there?

I guess I should ask, but what package are you using to install nfs?  I believe all you need is nfs-kernel-server and portmap for the server, and nfs-client and portmap for the client machines.  Probably not relevant, since most of the NFS stuff is in the kernel now.

Yeh, those are the packages that we're using, nothing special.

---

### Post by artur.linhart on 2010-08-15
Hello, I run the current version of debian squeeze and I also had this problems if reading the data from the remote nfs volume with the same message "RPC call returned error 88". I did not get the error message "/mspfiles: Socket operation on non-socket", but still the mater is the same I guess.

I have experimented with the rsize by the volume mounting and this seemed to be a workaround for me. I had originally the rsize set to 65536 what brought such errors (a lot of them). If I specified the rsize=16384 there came no such error at all...

So, it could confirm really this is maybe really a kernel-specific problem.

I also had massive problems if increasing the wsize to the max possible values (in manual there is written the maximum value about 1M is possible), then the nfs hungs after some time with very terrible consequences for the client...

I hope the experiments with rsize might help You too.

    cheers, Archie

---

