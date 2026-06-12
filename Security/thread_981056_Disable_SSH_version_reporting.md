---
title: "Disable SSH version reporting"
date: 2008-11-13
forum: Security
---

### Post by benanzo on 2008-11-13
Hi all,

I'd like to prevent sshd from reporting it's version:

$ nc example.com <ssh port>
SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2

Ideally it would report nothing, or at least just say something like "SSH"

I understand some (all?) clients use this information for on-the-fly config depending on the daemon version.  Is this possible?

Thanks

Ben

---

### Post by lemming465 on 2008-11-15
RFC 4253 "SSH Transport Layer Protocol" requires that the server and client start by sending each other "SSH-protoversion-softwareversion[SP comment]CR LF". So you can't turn it off.  I'm guessing you'd have to recompile from source to suppress the "Debiann-8ubuntu1.2" comment.  The lowest you could strip it down to would be something like "SSH-2.0-generic".  

I don't think you are going to gain much security by obscuring the server version, certainly not enough to justify the loss in interoperability.  I'd focus effort on things like iptables rules, tcpwrappers, switching to a non-default listening port, and general server security with apparmor or SeLinux.  SSH has a very good security track record overall.

---

### Post by bodhi.zazen on 2008-11-16
See this link for great tips to harden ssh:

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

If you do those things I would not worry as much about advertising the version of the ssh server :twisted:

---

