---
title: "VMWARE error"
date: 2008-02-06
forum: Virtualisation
---

### Post by provenzano on 2008-02-06
hi vmware work pretty good with generic kernel but won't work with compiled 1 , i get this error
Unable to change virtual machine power state: The process exited with an error:
End of error message.

there is a way to fix it?

---

### Post by luisromangz on 2008-02-06
If you installed VMware before you started using your custom kernel, you should reconfigure VMware, as it uses a kernel module for the virtualization tasks.

---

### Post by provenzano on 2008-02-06
i tryed i used to 

vmware-config-network.pl

but not worked thensudo: vmware-config.pl: command not found


help!

---

### Post by fjgaude on 2008-02-06
The command, vmware-config.pl, should be in /usr/bin.

If not there is an installation issue.

---

### Post by provenzano on 2008-02-06
i think there is an installation issue ,. i've installe dit with repository..

---

### Post by fjgaude on 2008-02-06
Well, do a "whereis vmware-config.pl" before trying other things.

Then cd to that folder and then run:

```
sudo vmware-config.pl
```

There's a chance that your vmware config is called vmware-server-config.pl.

That could work.

---

### Post by provenzano on 2008-02-06
vmware-config.pl does not exist but vmware-config-network.pl

when i use to launch it  :

Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes] 

Generating SSL Server Certificate

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

---

### Post by fjgaude on 2008-02-06
Well, it seems if you cannot find the config script you might have to uninstall and then re-install. 

That's all I can think of. There must be a vmware-config file somewhere on your computer.

AFAIK, you will have to completely remove the old vmware before you can install a new one.

I got my vwware server from vmware.com. Installed on laptop and main box without troubles.

---

### Post by provenzano on 2008-02-06
ty i'll try to get it from that website and not from repos :)

---

### Post by fjgaude on 2008-02-06
Okay, but do an uninstall before you try the new install. Get your license number, if you don't already have one. I've used the same one for over a year on many different installs. All worked fine and still do.

---

