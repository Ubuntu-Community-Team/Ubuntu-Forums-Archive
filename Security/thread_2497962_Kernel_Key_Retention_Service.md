---
title: "Kernel Key Retention Service"
date: 2024-05-24
forum: Security
---

### Post by mpytasz01 on 2024-05-24
Hi Everyone !

I'm new to this forum, yet I have quite specific problem with using service in the topic. Possibly either I have misconfigured system or I am misinterpreting domumentation.

What am I trying to do:
Store ant retain keys in a safe way.

Using 22.04 and having had followed the following:
[https://docs.kernel.org/6.5/security/keys/ecryptfs.html](https://docs.kernel.org/6.5/security/keys/ecryptfs.html)

I have tried the following:
[FONT=monospace][COLOR=#000000]~> keyctl add encrypted 1000100010001000 "new ecryptfs user:test 64" @u [/COLOR]
346307461 

~> keyctl print 346307461 
keyctl_read_alloc: Required key not available

Seems I have failed, although:
[/FONT][FONT=monospace][COLOR=#000000]
~> keyctl list @u [/COLOR]
4 keys in keyring: 
825075532: ---lswrv  1000 65534 keyring: _persistent.1000 
346307461: --alswrv  1000   100 encrypted: 1000100010001000

Rights seem fine to me
[/FONT][FONT=monospace] 

If I get it right, and if I consider option of not using TPM as it may simply be unavailable, I ought to mount an encrypted FS, therefore mounting filesystem requires retaining the key... If I create it the way above, it will not be the same, therefore:
1. What am I missing to be available to fetch the key ?
2. Are my assumptions on the usage scenario correct that I ought to do it the way described in kernel doc ?
3. I tried generating not only "ecryptfs" encrypted keys, including 
[/FONT][FONT=monospace][COLOR=#000000]
keyctl add encrypted 3000100010001002 "new default user:something 128" @u
[/COLOR]
which cannot be read, but i[/FONT][FONT=monospace]n contrast, adding:
[/FONT][FONT=monospace][COLOR=#000000]
echo -n "some proper hex string" | keyctl padd user "user:manual" @u[/COLOR]
[/FONT]
can be printed, but cannot survive system reboot.
4. Can the key be made really persistent without tpm ? I think key stored in tpm cannot be returned to a userspace application, or am I wrong ?

[FONT=monospace]I have tried it in one more distribution than Ubuntu to see if it's a specific problem, on the systems with and without TPM enabled, therefore the error I make must be systematic and possibly not a  bug...

Thanks in advance for some guidance
Cheers,
Michal

[/FONT]

---

### Post by currentshaft on 2024-05-24
What problem are you trying to solve?

Create keys -- keys for what? What are you trying to protect and from whom, i.e. what is your threat model?

---

### Post by deadflowr on 2024-05-24
I'd probably not use ecryptfs as it's buggy and probably vulnerable
[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1756840](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1756840)

---

### Post by aranc23 on 2024-10-07
This is my exact experience on Ubuntu 22.04.  I tested on Fedora 40 and Ubuntu 24.04 and it works exactly as I expect, that is I can print the key.  

I believe the difference might actually be in the versions of systemd on those systems, (24.04 and Fedora 40 have the same major version of systemd.)

Which version of Ubuntu were you testing on?

---

