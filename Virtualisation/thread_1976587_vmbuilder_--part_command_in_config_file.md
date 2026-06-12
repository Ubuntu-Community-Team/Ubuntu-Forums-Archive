---
title: "vmbuilder --part command in config file"
date: 2012-05-08
forum: Virtualisation
---

### Post by borromeotlhs on 2012-05-08
I am currently running oneiric and kvm to make vms with the vmbuilder command.  

I have an issue that I can't designate the vmbuilder.partition in my config file.  I want to run a command similar to ```
vmbuilder kvm ubuntu -c testvm.cfg
```
and have a vmbuilder.partition file referenced from within the testvm.cfg file.

I input the part option as part of the testvm.cfg file, with a url path to the vmbuilder.partition file, but whenever the vm is built, the partition file was not referenced at all, and the partitions switch to default values.

I have tried placing it in various portions within the config file and nothing works except using the --part option from the command line.  

Any clarification would be appreciated.

---

### Post by geeksmith on 2012-09-12
Don't know if this is still an issue for you, but post the content of your vmbuilder config and partition files and I'll see if I can help.

--
@@ron

---

