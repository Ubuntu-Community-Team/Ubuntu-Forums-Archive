---
title: "VMWare install woes"
date: 2007-12-27
forum: Virtualisation
---

### Post by valkarin on 2007-12-27
I am running Ubuntu 6.10 and am trying to install VMWare fom the repos.  However I keep getting this error message:

```
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

At this point I would be happy if I could just get it to quit trying to install it.  Does anyone know what is going on with this?  How to I get it to finish installing correctly or uninstall it?

---

### Post by p_quarles on 2007-12-27
This is kind of a hit or miss solution to this particular problem. I've had good luck and bad luck with. Anyway, try this first:
```
sudo apt-get -f install
```
The -f option attempts to fix broken or partially installed packages.

If that fails:
```
sudo apt-get build-dep vmware-player
```
This attempts to fetch any missing dependencies that, for whatever reason, weren't properly installed in the first place. While this is unlikely to fix anything, it could produce error output that could be useful later. Then, run the first command again.

Finally, try removing it completely:
```
sudo apt-get remove --auto-remove vmware-player
```

---

### Post by dcstar on 2007-12-27
> **valkarin said:**
> I am running Ubuntu 6.10 and am trying to install VMWare fom the repos.  However I keep getting this error message:
........
At this point I would be happy if I could just get it to quit trying to install it.  Does anyone know what is going on with this?  How to I get it to finish installing correctly or uninstall it?

You may want to try booting up in Recovery mode and running the apt-get command to either install or remove it.

I just installed this package the other day 100% ok - but I'm using 7.10 64 bit.

I must admit I like vmware, I have the 32bit version of Ubuntu installed in it on my 64 bit Ubuntu system - best of both worlds!

---

### Post by valkarin on 2007-12-27
Tried all of your apt-get suggestions and am still in the same boat.  The auto remove one returned this:

```
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Have not tried the recovery mode suggestion yet.  It will have to wait until morning.  Any other ideas keep them coming and thanks for the help so far.

---

### Post by dcstar on 2007-12-28
> **valkarin said:**
> Tried all of your apt-get suggestions and am still in the same boat.
.........
Have not tried the recovery mode suggestion yet.  It will have to wait until morning.  Any other ideas keep them coming and thanks for the help so far.

You might have to manually stop the vmware startup by editing your /etc/rc directories, then it may allow you to remove it after a clean boot.

---

### Post by valkarin on 2007-12-28
Do I just delete the scripts in the rc*.d directories?

---

