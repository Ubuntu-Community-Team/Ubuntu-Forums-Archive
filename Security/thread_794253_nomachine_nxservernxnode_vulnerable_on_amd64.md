---
title: "nomachine nxserver/nxnode vulnerable on amd64"
date: 2008-05-14
forum: Security
---

### Post by freelsjd on 2008-05-14
After I installed the new openssh security updates to 1:4.7p1-8ubuntu1.1, it became necessary to regenerate the public keys from nomachine's nxnode. Unfortunately, the keys remain shown as vulnerable (compromised) no matter what I do for the amd64 version of Ubuntu. For the 32-bit Ubuntu, 32-bit Debian, and 64-bit Debian amd64, the keys are OK. I will cross post this to the security forum.

---

### Post by freelsjd on 2008-05-15
Is there anyone else out there in Ubuntu land that uses nomachine.com products (nxserver, nxclient, nxnode).  If so , did you have this problem on your amd64 Ubuntu system ?

---

### Post by mannheim on 2008-05-16
I am running nomachine's nxnode/nxserver on an amd64 machine. I generated new keys for nx using
```
 sudo /usr/NX/scripts/setup/nxserver --keygen
```
following instructions [here]("http://www.nomachine.com/ar/view.php?ar_id=AR01C00126"). After configuring the nx clients to use the new key, it all worked.

I think that, whenever a user uses nxclient to connect to a server machine, the nx key is stored in ~/.ssh/authorized_keys2 on the server machine (at least that's what happens here). The ssh-vulnkey tool may pick up these entries and report them as "compromised" (but without telling them which file they are in). You can remove these entries by hand.

---

