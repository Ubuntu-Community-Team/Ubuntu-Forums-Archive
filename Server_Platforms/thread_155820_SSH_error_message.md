---
title: "SSH error message"
date: 2006-04-05
forum: Server Platforms
---

### Post by lingsongyou on 2006-04-05
Hey guys

I am trying to SSH into a computer where I work, and I always get the message "ssh_exchange_identification: Connection closed by remote host"
 when I do either
"ssh -l mberger patdsk2.fnal.gov" 
or
 "ssh [email]mberger@patdks2.fnal.gov[/email]"

I am told by the tech people that this should work, but I always get this message.  I would appreciate any help anyone could give me

---

### Post by jpkotta on 2006-04-06
Make sure you have an ssh server running on the remote machine.  That's where I've seen this error before.  On the remote machine, you can find out if the ssh server is running with ```
ps -ef | grep sshd
```

---

