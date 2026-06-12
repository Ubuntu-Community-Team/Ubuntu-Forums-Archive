---
title: "Securing NFS"
date: 2007-10-23
forum: Server Platforms
---

### Post by thornomad on 2007-10-23
Hi,

I have a home file server running Ubuntu.  On my home network (wired and with WPA2 wireless) I use netatalk (AFP) to connect my macs to the file server.  To connect remotely, I use SSH (requiring public/private key authentication, no password authentication).  I have a router which forwards incoming requests to port 22 to the file server.  No other ports are forwarded.

I would like to setup the file server to use NFS in addition to SSH and Netatalk (afp) on the local portion of the network.  However, I am a little concerned about making sure the shares are secure.  

For SSH, there are a lot of online resources I found showing suggestions for making it more secure (disabling password login, requiring key pairs, for example) and netatalk requires a password.  That coupled with only opening port 22 on the router has me feeling semi-safe.

But if I add NFS I get a little nervous.  I want to setup a second web server (ubuntu) to have access these shares and, being a web server, the machine seems more prone to being compromised -- so I want to make sure my NFS is safe.  I also want to build my own ubuntu dekstop in the future and would like to use NFS for that as well.

I have viewed the NFS documentation on the Ubuntu Wiki (as well as some google search results) but am not finding the kinds of suggestions and insight that makes me feel safe enough to go about setting it up myself.

Does anyone have some good tutorials or how to guides (or just suggestions) that can ease my mind and make NFS secure ?  

Thanks,
Damon

---

### Post by kidders on 2007-10-24
Hi there,

One common approach to securing network traffic is to tunnel it over SSH. Secure tunnels are an attractive solution, because they're application independent ... so it doesn't matter in the slightest whether you're talking about SMTP relaying, traffic between a MySQL server and an Apache/PHP server, or sharing files.

You're already familiar with SSH, so chances are you've dealt with tunneling before. As you may know, it has the potential to greatly enhance the security of NFS traffic by...[LIST]
[*]Handling issues like IP spoofing for you.
[*]Adding an extra layer of authentication.
[*]Encrypting all traffic.
[*]Providing a sensible way of accessing NFS shares through a firewall.
[*]Allowing you to avoid having to do certain things that can sometimes be a source of concern, like binding an NFS server to an NIC that handles external traffic.
[/LIST]

---

### Post by thornomad on 2007-10-27
Hi - thanks for your reply and input.  Appreciate it.

Would tunnelling NFS have any benefit over just straight SSH mounting via FUSE ?  I mean, I assume that if you tunnel I will already be taking a performance hit ... would it be better just to mount via FUSE ?  

And, is there a big performance hit using the tunnel?

Damon

---

### Post by kidders on 2007-10-27
Hey again,

Good point. I suppose tunneling would be more useful for AFP or Samba ... you know ... sharing protocols for platforms that don't like FUSE very much. Having said that, I would *guess* that NFS over SSH would outperform SFTP, and may be a little more stable. Filesystems mounted using FUSE can exhibit odd behaviour sometimes. In addition, there would be subtle differences in behaviour. For instance...
[LIST]
[*]The ability to log into an NFS share using an account that didn't have SSH access to the machine hosting it.
[*]The ability to see "under" mounted filesystems.
[/LIST]

Whether to choose SFTP or NFS over SSH is up to you really ... I'm not sure I can think of a particularly good reason to go for one over the other. :-)

In general, encrypted connections are more CPU-intensive. In addition to the increased bandwidth requirements, this will tend to make them slower, but they aren't *always* slower.

I hope that helps.

---

