---
title: "Problem with winscp/sftp"
date: 2005-08-06
forum: Server Platforms
---

### Post by Paul Bramscher on 2005-08-06
I keep getting sporadic exepected "exit status 11" errors when I try to sftp data from a Windows XP box to an ubuntu box via winscp.  Running Ubuntu 5.04 and winscp 3.7.4.

Anyone else see this behavior?  It's so unreliable that I may have to switch back to Fedora -- can't seem to get more than a few megabytes pushed over to the ubuntu box without it erroring out.

Any suggestions?  Thanks.

---

### Post by Paul Bramscher on 2005-08-06
Nobody else notice issues sftp stability with ubuntu?  With WinSCP I get the following on a regular basis: "Connection has been unexpectedly closed. Server sent command exit status 11".

Filezilla also hung on me.  I didn't have issues on the same hardware when it ran SuSE.  I also notice buggy sftp performance on a second ubuntu box I have (different hardware), which ran RH FC3 without problem.

Is there some setting I ought to make in /etc/ssh/sshd to make it more stable?  I'd like to keep ubuntu, but a rock-solid sftp is important for me.

---

### Post by Paul Bramscher on 2005-08-06
I'll reply to my own question here.   I installed Fedora Core 4 on another machine and noticed the same problem with WinSCP/sftp.  Must be something buggy in the newer version of sftp server?

Anyway, I changed WinSCP's settings to SCP and did not see a reliability problem.  Is  sftp just not as well supported?  I'm trying to figure out whether this is a client or a server issue.

---

### Post by Paul Bramscher on 2005-08-20
[QUOTE=Paul Bramscher]I'll reply to my own question here.   I installed Fedora Core 4 on another machine and noticed the same problem with WinSCP/sftp.  Must be something buggy in the newer version of sftp server?

Anyway, I changed WinSCP's settings to SCP and did not see a reliability problem.  Is  sftp just not as well supported?  I'm trying to figure out whether this is a client or a server issue.[/QUOTE]

I feel somewhat uncomfortable replying to myself here.  But for the record, the lead programmer of WinSCP was aware of this problem, and released 3.7.6 which apparently fixes it.  Just came out a few days ago. \\:D/

---

