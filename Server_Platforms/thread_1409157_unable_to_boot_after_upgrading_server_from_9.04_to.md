---
title: "unable to boot after upgrading server from 9.04 to 9.10 under Xen"
date: 2010-02-17
forum: Server Platforms
---

### Post by alexm@nus.edu.sg on 2010-02-17
Note that I posted this in the installation/upgrade forum but had no replies, so I'm reposting here. Hope that's ok...

I've just upgraded my server installation from 9.04 to 9.10. I'm running this as a Xen virtual machine. All seemed to go well until I restarted, at which point I got stuck at this point:
 
Begin: Running /scripts/init-bottom ...
Done.
mountall:/proc: unable to mount: Device or resource busy
mountall:/proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't mounted
init: mountall main process (819) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
Give root password for maintenance
(or type Control-D to continue):
 

My service provider is running xen-shell 1.0.79 running on Xen version 3.0.3-1, and after the seemingly-successful do-release-upgrade, uname -r reports ubuntu kernal 2.6.18-5-xen-amd64.

Unfortunately, this isn't mentioned as a possible problem here [http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)  - if it was, I might have held off upgrading until I was sure there's a fix. :sad:

 Is there a fix? I see several seemingly-related bugs: [https://bugs.launchpad.net/ubuntu/+s...ll/+bug/430374]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/430374"), [https://bugs.launchpad.net/ubuntu/+s...ll/+bug/469985]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/469985"), [https://bugs.launchpad.net/ubuntu/+bug/398214](https://bugs.launchpad.net/ubuntu/+bug/398214) and [https://bugs.launchpad.net/ubuntu/+s...ll/+bug/447747]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/447747"), but no clear answers, unless I missed them. I managed to get the server up manually following these step [http://meeb.org/post/319933907/dont-...rmic-9-10-on-a]("http://meeb.org/post/319933907/dont-upgrade-xen-domus-to-ubuntu-karmic-9-10-on-a") but I need to be able to boot properly... Any suggestions as to what I should do to get my just-upgraded-to-karmic server to boot properly under Xen?
  

Any help would be greatly appreciated.
 thanks,
Alex

---

### Post by mazarini on 2010-02-26
Hi,

I believe your kernel don't support ext4. 

I have read some problems with this kernel and 9.10 on DomU. May be some problem with with Dom0 too.

I'm not expert on xen.

---

