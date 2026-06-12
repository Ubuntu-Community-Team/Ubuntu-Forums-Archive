---
title: "graphically manage server from main box (remote desktop?)"
date: 2008-12-12
forum: Server Platforms
---

### Post by jimmy the saint on 2008-12-12
I have a server in my living room currently running Gutsy.  It is going to get an upgrade soon and I am wondering if there is a way to get it set up to do what I have in mind.

Currently, I manage it via the CLI.  That is fine for most things, but I also use it to do tasks that are time intensive that I don't want holding up my main box. (some video conversions etc.)

The server is headless, and I really want to keep it that way, but I would also like to have the option of using graphical tools on it.  Is there an easy way run a desktop over the lan?  I am thinking something like a remote desktop client.  Is that practical?  If so, what is the best implementation?  Are there any pitfalls?  I am not overly concerned about a small performance hit, as the dual core processor is far more juice than is necessary to serve files and music!

Thanks for any input!

JTS

---

### Post by CrucifiedEgo on 2008-12-12
You can enable remote desktop through the settings menu somewhere, or install tightvncserver.  This should listen on port 5901, and you can connect with vncviewer(installed by default if i recall).  Others may suggest X forwarding over SSH, but to me that's too much work for what i need to do.

---

### Post by jimmy the saint on 2008-12-12
What are the security implications of vnc vs ssh?  The server is actually behind two routers (bridged).

---

### Post by hictio on 2008-12-12
> **jimmy the saint said:**
> What are the security implications of vnc vs ssh?  The server is actually behind two routers (bridged).

The security implication is that all VNC traffic, unless tunneled, goes in plain text, unencrypted.
While all SSH traffic goes encrypted.

Another option, if you haven't thought of it yet, might be [Webmin](http://www.webmin.com/), not a GUI in the traditional sense of the word, but a web front to your server.
Oh, yeah, if you have OpenSSL and a few Perl modules installed, Webmin does its thing over SSL, so its secure :D

---

### Post by jimmy the saint on 2008-12-13
I have stumbled upon the nx protocol.  I am considering this setup:
Hardy Server:
      FreeNX server
Main Box:
      NoMachine nx client.

Has anyone had any experience with NX and Ubuntu?  It seems to be similar to vnc, except it is faster, lower bandwidth and more secure.  There do not seem to be any packages in the repos though.

---

### Post by cariboo on 2008-12-13
The easiest way to do what you want in my opinion is to install the apps you need on the server then use xforwarding to run the apps. In a termianl type:

```
ssh -X user@server
```

Then on the server for instance if you wanted to use brasero at the prompt type:

```
brasero
```

I use the above command to burn backup dvds, as I'm to lazy to burn dvds from the command line.

Jim

---

### Post by jimmy the saint on 2008-12-17
wow.  If that's all there is to it, I may just stick with x over ssh.  I read a few tutorials and got the impression that it was WAY more work than that.  I will give it a shot.

---

