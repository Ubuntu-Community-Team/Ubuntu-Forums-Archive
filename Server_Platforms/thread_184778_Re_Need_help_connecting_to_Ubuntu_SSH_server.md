---
title: "Re: Need help connecting to Ubuntu SSH server"
date: 2006-05-30
forum: Server Platforms
---

### Post by osinghrathore on 2006-05-30
I am experiencing a strange problem when connecting to SSH server on my Home PC. 

Here's the description of the problem I m having:
> My Home PC is running SSHD (no firewall is there) and I am not able to connect to it from my office  system, I've checked  hosts.allow to find any denying entries, when I try to SSH to it I get "connection timed out error", but when I SSH to it thru the live server I own, it works. Though I haven't made any specific settings for my live server, the SSHD is running on port 2233.
 
 I m really clueless on this
 can somebody pls help.

---

### Post by Iowan on 2006-05-30
May need s'more info - sounds like you've got a couple of layers of complications in there... What steps do you use to successfully connect through the live server.   What steps do you use for the unsuccessful direct attempt.  Is the server forwarding from one port to another?

---

### Post by osinghrathore on 2006-05-30
I simply issue command
ssh user@mydyndnsname -p 2233
 for direct connection from my office PC to home PC
then it just stays like that and after a few minutes timesout connection.
but when I ssh to my live server (with static IP ) and from there to home pc using the same command, it works.

 Even I tried testing connection from my friends PC and I was able to connect to it from his PC also. 

 And server isn't using port forwarding at all.

---

### Post by Iowan on 2006-05-30
I've used SSH only from inside my network, and I've never used dyndns.  Having made clear how useless my advice is likely to be...  might dyndns pass SSH only on  the standard port?  > Even I tried testing connection from my friends PC and I was able to connect to it from his PC also.  Direct, via live server, or both?

---

### Post by osinghrathore on 2006-06-01
Actually first I tried SSHD on standard port (22) but that didn't worked so I thought may be changing port to 2233 might help but that also didn't worked.
Also I tried using IP instead of dynamic DNS name but that also didn't worked.

One more thing I tried connecting to web server on the home machine from office pc and it also worked, only the ssh is not working. I m sure there's something I m missing in ssh config.

>  Direct, via live server, or both?

I tried connecting to it directly.

---

### Post by Iowan on 2006-06-01
[QUOTE=osinghrathore] Even I tried testing connection from my friends PC and I was able to connect to it from his PC also. [/QUOTE]You were able to directly connect via SSH on port 2233 from your friend's PC? >  I m sure there's something I m missing in ssh config. Hmmm, Is the live server on the same subnet (wonder if SSH is only allowing connections from "local" net)?

---

### Post by osinghrathore on 2006-06-02
Live server is on diff. net

Yes, I was able to connect on port 2233 from my friends PC and his PC was also on diff subnet ( on diff ISP network)

---

### Post by osinghrathore on 2006-06-17
Come on.... somebody pls help.

---

