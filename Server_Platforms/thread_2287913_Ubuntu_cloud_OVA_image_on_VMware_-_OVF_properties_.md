---
title: "Ubuntu cloud OVA image on VMware - OVF properties not working??"
date: 2015-07-23
forum: Server Platforms
---

### Post by Aaron_Trout on 2015-07-23
I am trying to use the OVA template from the 'ubuntu cloud images' repository - [https://cloud-images.ubuntu.com/vivid/current/vivid-server-cloudimg-amd64.ova](https://cloud-images.ubuntu.com/vivid/current/vivid-server-cloudimg-amd64.ova)

I am deploying onto ESXi 5.5 with vCenter; the wizard asks me to fill in some OVF properties like hostname, put my SSH pubkey in there so I can log in, set default user password and so on. The machine boots up but the items configured in the OVF properties do not seem to have any effect. I can see that an ISO is attached which looks like it should have the data on it, but the hostname of the machine (only visible on the console login prompt) is just 'ubuntu' and not what I configured. I also cannot login either via SSH or the console with the default password.

Am I missing something here? This seems like it should just work. I cannot find any useful docs for this either.

Any help / pointers greatly appreciated!

Aaron

---

### Post by houstonbofh on 2015-07-28
You may have some different problems here.  The information for the running system is in the image.  The information for the hardware is in the vm config files...  If it boots up, the vm config files are (probably) correct.  If the password does not work, use the VMware console to boot into single user mode and reset the passwords.  The console will not need the ssh keys, which can be worked on later.

---

### Post by Aaron_Trout on 2015-07-29
Does anybody know what the default passwords should be? Are these images even supposed to be used in ESXi?? Are there any docs? I couldn't really find any info on them. :(

I want to be able to automatically deploy these from a script so manually going to single user and setting a PW is not really a viable option.

---

