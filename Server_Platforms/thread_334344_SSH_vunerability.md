---
title: "SSH vunerability"
date: 2007-01-08
forum: Server Platforms
---

### Post by s04bf1c2 on 2007-01-08
Hi everyone,
I have just one simple question. Can viruses transfer through ssh? I mean do you control what travels through the ssh tunnel or can (unauthorised) files be transfered. I assume the answer is yes as a vunerble system accessing a remote one could in theory infect the remote system. I wish to setup access my server at home but don't really trust my college's computers security :(.

Thanks for your help,
s04bf1c2

---

### Post by chrisfay on 2007-01-08
Unless you hand out access to your SSH server to someone else there shouldn't be an issue. The communication to and from your server is heavily encrypted and no standard network sniffer can easily obtain this info. 

As far as viruses, I'm assuming your connecting from a Win machine. Those viruses will not effect your Lin server. They just can't, and won't. 

Don't give out ssh access to your server and you'll be fine.

---

### Post by s04bf1c2 on 2007-01-09
Thanks chrisfay.

With regards to windows servers. Is it possible then for a infected t windows computer to unknowingly transfer a virus through the tunnel. Or does ssh only transfer files that you authorise.

I know this is off ubuntu topic, but i have seriously considered the idea of using a windows server for some time now, and i'm sorry for the horror that many of you may be feeling at that thought.

---

### Post by MrHorus on 2007-01-09
> **s04bf1c2 said:**
> I mean do you control what travels through the ssh tunnel or can (unauthorised) files be transfered. 

The application initiating the connection itself would have to be subverted, for example if you were using PuTTY on a Windows machine and the PuTTY binary was compromised then it could certainally do nasty things over the connection or email your credentials to someone - hence why it's important to verify your source i.e. the MD5 hashes.

---

### Post by s04bf1c2 on 2007-01-10
Thanks thats all i needed to know

---

### Post by RichardBronosky on 2007-03-15
> **s04bf1c2 said:**
> i have seriously considered the idea of using a windows server for some time now, and i'm sorry for the horror that many of you may be feeling at that thought.

I wouldn't go so far as to say it gives us a feeling of horror.  As a matter of fact, why don't you post the IP address of this windows server here when you get it online.  We'll let you know if you did it right. ;) 

Seriously though, windows has no place on a server, unless you need to do something like MS SQL or ASP or some other locked down technology.  Must anything you could want to do with a server Linux can do.  Servers don't need the overhead and vulnerability that windows brings.  If you want to use windows as a desktop, I won't fault you.  But choosing it for a server, that's hard to justify.

---

### Post by Mr. C. on 2007-03-15
s04bf1c2,

I think you misunderstand what SSH is.  It is in a nut shell, and ecryption layer.  What passes through SSH is entirely up to you.

SSH allows you to make secure connections over an insecure network.  As the data that passes through SSH is encrypted, SSH has no idea what the contents are, nor can anyone/thing in between your machine and the server machine you are connected to.

Could someone write a virus that runs on Linux, and happens to watch for SSH connections to occur, and then send some malware through he connection?  It is certainly possible, but only if your machine itself becomes infected in some way.  And the server also must be vulnerable in some way.

Since you are likely to use SSH to make shell connections, and possibly tunnels, you are very likely to notice such activity ( such as commands seemingly typing themselves ).

Keep your system's safe and secure, and you have little to be worried about.

MrC

---

