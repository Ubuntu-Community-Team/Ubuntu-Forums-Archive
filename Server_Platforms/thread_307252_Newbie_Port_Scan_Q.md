---
title: "Newbie Port Scan Q"
date: 2006-11-26
forum: Server Platforms
---

### Post by DocMSK on 2006-11-26
Hello,

New to Linux.

I did a Port Scan on my Ubuntu box and it said the following ports were open:

111 sunrpc
139 netbios-ssn
445 microsoft-ds
614 unknown
2049 nfs

I believe the first three are to do with Samba, I do explore drives on my XP box via Linux.

What are ports 614 and 2049? I saw on the web that NFS could stand for Network File System, is this also linked to Samba?

Do I need to be concerned about the above open ports, and do you recommend a firewall ( I am behind a wireless router which is connected to an ADSL modem )?

Any advice appreciated.

Many thanks
Doc

---

### Post by tturrisi on 2006-11-26
No need to worry, you scanned the comp from another lan comp, but those ports won't show up when scanned from a wan comp (outside your lan).

port 614 is sshell
port 2049 is NFS (Network File System)

---

### Post by DocMSK on 2006-11-26
Many thanks for your swift reply.
Rgds
Doc

---

### Post by tturrisi on 2006-11-26
> **DocMSK said:**
> Many thanks for your swift reply.
Rgds
Doc
you're welcome.
If you have any uncertainty, post your public IP and we'll hammer the heck out of your router to see how secure you are.

---

