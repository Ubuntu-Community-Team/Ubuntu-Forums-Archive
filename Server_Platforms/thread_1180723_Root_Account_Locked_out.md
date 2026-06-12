---
title: "Root Account Locked out"
date: 2009-06-07
forum: Server Platforms
---

### Post by Fliprising on 2009-06-07
New ubuntu server user here and I really do believe I messed up. I set up a server I got from a provider remotely ubuntu 8.10 and everything was going well. Unfortunately I edited the sshd_config file to change the port. I restarted and exited the server. 

I forgot to keep track of the port number and now I am unable to login to the server even with root access. Is there anything I can do I have tried google and this forum but I found noone dumb enough to do what I did :popcorn:. If there is any way you guys can help me out that would be great =)

---

### Post by .nedberg on 2009-06-07
I think you will need to contact the provider!

You _could_ try all possible ports... If you have an idea of the port number (was it in the 100's, 1000's or 10000's). You could narrow it down.

---

### Post by amingv on 2009-06-07
If your server is connected directly to the network (no router/firewall in between, which would be a bad idea to begin with) you could try a port scan *if, and only if* the server **belongs** to you. If it does have a router/firewall then it'd be impossible to find the port (assuming only port 22 was forwarded to the server) unless you have remote configuration enabled in the router (which would be a bad idea, too).

All these possibilities aside, the only way to get back the port would be contacting someone with physical access to the server/network and asking them to reconfigure it for you, I'm not aware of there being another way...

---

### Post by .nedberg on 2009-06-07
amingv is correct. I forgot about the firewall/router problem...

If you didn't configure the machine to much they can possibly just restore it to the default configuration easily!

---

