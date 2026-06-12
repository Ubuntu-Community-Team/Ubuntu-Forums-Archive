---
title: "System writable files"
date: 2016-02-15
forum: Server Platforms
---

### Post by extremis11 on 2016-02-15
I am trying to remount all directories with files that system writes to, so that i can boot multiple nodes from the same image. Till now, i have considered remounting /run, /var/log to a local disk, or RAM.

What are the files/directories that get written whenever Ubuntu server boots/shuts down?


Thanks in advance,
Kostas

---

### Post by SeijiSensei on 2016-02-15
Filesystems like /run, /proc, and /sys are not "real" in the sense that they are created anew at each boot.  You don't want to preserve any of those.

I'm not sure what you mean by "nodes," so it's difficult to respond more specifically.  If you want to have multiple systems write entries to a common set of log files, use the remote features of [rsyslogd]("http://linux.die.net/man/5/rsyslog.conf").

---

### Post by MAFoElffen on 2016-02-15
... and parts of /var are spools.

---

### Post by MAFoElffen on 2016-02-15
> **extremis11 said:**
> I am trying to remount all directories with files that system writes to, so that i can boot multiple nodes from the same image. Till now, i have considered remounting /run, /var/log to a local disk, or RAM.

What are the files/directories that get written whenever Ubuntu server boots/shuts down?

I'm also confused by what you say you are trying to do.

From what you are describing here: "so that i can boot multiple nodes from the same image." that reminds me of LXC, except that would prevent an instance from being a different instance. Sharing those directories between nodes ... well, not sure how that would work without crashing the other nodes (because they did not make the change done to them). Unless you talking about server replication clusters, where you are is mirroring the server nodes(?)

If you are just looking for this: "What are the files/directories that get written whenever Ubuntu server boots/shuts down?" then I would add to the last post, parts of /var and parts of /etc. /var is a combination of logs and spools. Some of /etc is built dynamically during upstart.

---

### Post by extremis11 on 2016-02-16
Thank you all for the suggestions.

What i am really trying to do here is to boot some machines (nodes) from network using the same Ubuntu Server installation (image) located on /nfsroot directory of another machine. I have already installed Ubuntu Server on the first machine and also created (and exported) the image; i have booted the second machine from the network using the image on the first machine, everything goes just fine. The result of 'df -h' on the second machine is:

Filesystem            Size  Used Avail Use% Mounted on
192.168.1.1:/nfsroot  459G   11G  425G   3% /
udev                   32G  4.0K   32G   1% /dev
tmpfs                 6.3G  976K  6.3G   1% /run
none                  4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs                  32G  4.0K   32G   1% /tmp
none                  5.0M     0  5.0M   0% /run/lock
none                   32G     0   32G   0% /run/shm
none                  100M     0  100M   0% /run/user

Now, i would like to boot a third machine from the same image (192.168.1.1:/nfsroot), but i am afraid that the same files will get overwritten, possibly resulting in a crash and a corrupted image. SeijiSensei, if i understand it well i don't have to worry about tmpfs, udev, and none filesystems as these are created on every boot (and are located on local RAM?), so they are unique to each machine. It is the 192.168.1.1:/nfsroot mounted on / that bothers me. Can rsyslogd handle all logging (even that from programs like SLURM) so that logfiles will not get messed up? Even if that is possible, i think remounting will solve other problems, like configuration files that should be different for each machine booted (e.g. /etc/hostname).
[COLOR=#000000]
[/COLOR]MAFoElffen, are you sure /etc and /var are the only directories the system writes to? /etc is only 5MB, but /var is 415MB (/var/log is 17MB). Should i remount these directories on a local disk (NFS or RAM)? Is it necessary to remount /var or would it suffice to remount only /var/log?[COLOR=#000000]

Thanks again for any suggestions,
Kostas

[/COLOR]

---

### Post by MAFoElffen on 2016-02-16
I said besides what SeijiSensei had mentioned. And that depends if you are running in a virtualized container or on hardware... Besides hostname, hosts, domainname that you mentioned ... in /etc, there is also /etc/resolve.d and a few others in /etc, that  have scripts that dynamically build parts of the networking details. So if the image is done when it is powered down, is different when it is running. Example of these dynamic files are /etc/resolve.conf. 

As far as I know, most logs in /var can be reconfigured to log remotely.

I'm still curious in the "what" that you are doing. Why not use LXC, Docker, MAAS or a hypervisor? Or are you creating images for one of those to provision machine instances? I know some of the basics of that, but not the specifics.

But from your description, it sounded more like your were doing something along the lines of recreating the wheel on diskless thinclients, but with server instances???

---

### Post by extremis11 on 2016-02-16
[COLOR=#000000]MAFoElffen, thanks again for your help.

I am trying to build a small Cluster (5-6 machines). I read about diskless (network) booting and i thought it would be nice to have one image on the first node that could be used for booting all other nodes. This way, if i need to add/update some program i will only have to do it once and the change will apply to every node (other than the first). I am running on hardware; i do not have any experience with LXC, Docker, MAAS or hypervisors. Maybe diskless thinclients is the most appropriate way to describe what i am trying to do (of course, all my machines have SSDs, it is just that i would like to boot them from a single image). I chose Ubuntu Server instead of Desktop edition as i don't need any GUI.

Perhaps this has been answered elsewhere, but i was unable to find a tutorial that covers all this.[/COLOR]

---

### Post by SeijiSensei on 2016-02-16
Take a look at this: [http://www.ltsp.org/](http://www.ltsp.org/)

---

### Post by MAFoElffen on 2016-02-16
> **SeijiSensei said:**
> Take a look at this: [http://www.ltsp.org/](http://www.ltsp.org/)
Exactly! When I was writing that last post and asking about thin-clients, I was thinking of our own:
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

---

### Post by extremis11 on 2016-02-17
Thanks guys, LTSP looks exactly what i need; however, since i would like to be able to run applications using application server's CPU and RAM, i think i should follow the guide for fat clients supported in LTSP 5.2 and later. Sometimes it is better to let the experts take care of all these details. Only problem is i have already installed a zillion applications both on root server and application server image, and now i will have to do it all over again.

Maybe i should do a clean installation on a spare drive (assuming i find one) to learn how LTSP works. I am still curious how LTSP handles all these configuration and log files of different fat clients from a single image.

---

### Post by MAFoElffen on 2016-02-17
Basically PXE goes to dhcp to setup initial network settings.A tftp server part of it then dl's and boot an intrafs image that points and mounts to where the files are on a nfs share as read-only, to where the target guest system is stored (this is not a running system, but a static storage of that guest config. So the clients share one root file system (readonly) and run programs off the server as an application server. That is thin-client... The drawback is all are the same, so none have "special roles."

The drawback to that, is usually the logs in thin client (to conserve resources) are thought of as temporary... much like it is when running a liveCD image.

The differences in the transition from thin to thick to smart client: config and profile files are stored, where the applications are stored and where they actually run/process. (and the storage of client logs)

---

### Post by extremis11 on 2016-02-18
I have run the following command on the client machine

```
sudo find / -mtime -7 -print
```

that prints all the files modified the last week. Files written by system are located in /proc, /run, /sys, /dev, /var/log, /var/lib, /var/cache, /tmp. For my purpose /proc, /run, /sys, and /dev require no special attention, /var/cache does not seem important and therefore could be mounted on tmpfs along with /tmp. /var/log, /var/lib and /etc could be mounted on a local disk, or copied at boot time to tmpfs from nfs and back to nfs at shutdown.

---

### Post by MAFoElffen on 2016-02-18
Congrat's on finding a solution. On the model you did, you ended up with something along the lines of tempfs with persistence, and a bit more.

Note that the next step up would be boot local from grub on intrafs (various) that points to a specific nfs shared system directory... That way you can have TS pools that point to different configurations... Then you are not locked into all clients having to be the same.

So let me be the devils advocate. Years ago, I did a text-console Linux suite based on Ubuntu core. I could carry it around as a pocket OS, to use for diagnostics. So I know something like that runs in 64 -128 MB, I know it installed with its suites and ran comfortably in much less that 700 MB.

I have to ask for my own curiosity on this... Since you said you were doing just console clients and you started out with just terminal services  <> and then mentioned that fat-clients might work for you... Why not a minimal core install with ssh-client, signed keys to a central server? And that server either running as an app server or if needed, access to virtual server guests?

Cause TSP is based on the model I was introduced to when I first worked in IT in the late 80's - early 90's. TSP is terminal Services (Terminals do not have disks). All the processing is done on the host. We dreamed of distributed processing back then, which evolved to workstations, then to server networks with smart clients... And now we have virtualization, where we can present vm guests and vm server guests to clients... If it were still just thin or fat clients, then they could still be enriched by current technology to present an enriched environment.

If you can do fat-client, then I have to ask if you can actually boot from your clients and connect to an enriched environment(?) Or is that more than they will ever need?

---

### Post by extremis11 on 2016-02-20
If you worked in IT in the late 80's - early 90's, all i have to say is i envy you; at that time i was just another kiddo shooting bad guys on my Amstrad CPC 6128. Now, i am a Ph.D. student struggling to set up a mini cluster, so i (and other group members) could run some quantum simulations. You see i am by no means an IT professional (though i would like to be). I think i understand now what to do and (maybe) how to do it, but i have not set up a working cluster yet; i only rushed to mark the thread as solved because the main question asked here was about the writable system directories which is pretty clear to me right now... Thanks again for your suggestions, but we don't need anything that sophisticated, just some computing machines that could (hopefully) be used together for running some parallel software.

---

