---
title: "SSH - detailed access control"
date: 2006-11-01
forum: Server Platforms
---

### Post by nickbooker on 2006-11-01
Hi.

I have a security problem with SSH that I cannot find a solution to anywhere - it is as follows:

I know that I can disable specific users from any host, and that I can disable specific hosts from accessing the server by any user, but I want to combine these and restrict individual users' access based on the originating IP address.
For example, under my proposed policy if the client machine is connected to my local network with network address, say, [FONT="Courier New"]123.456.789.0/24[/FONT], I want [FONT="Courier New"]root, erwin, mike[/FONT] and [FONT="Courier New"]pitr[/FONT] to be able to log in, but if a client outside my LAN (for example [FONT="Courier New"]80.123.456.789[/FONT]) attempts to connect using any login but [FONT="Courier New"]mike[/FONT] I would like their login to be refused in some way without impeding [FONT="Courier New"]mike[/FONT] from logging in at the same time.

Hope someone can help, and thanks in advance.

Nick Booker

---

### Post by nixfaced on 2006-11-01
Hi,

On my network I do this by running a second instance of sshd.  Using sshd's -f <filename> argument, it loads a seperate configuration file containing different ListenAddress and AllowUsers settings.  

If you're only working with one network interface, you should be able to bind an additional IP address to that interface, for example by using ifconfig eth0:1 <address>.  You can then start sshd to listen on that IP with your customized sshd config file.

Additional tweaks may be necessary depending on your exact network configuration, and don't ask me the best way to start this on boot because I'll give you a "wrong" answer, but hopefully this gets you started.

---

### Post by nickbooker on 2006-11-21
Cheers for the quick response (sorry I didn't pick it up earlier - I'd got the forums sending to my old-spamridden-email-account-that-I-never-check).

I've just gone for locking everyone but me out - it turns out the other users are unlikely to use SSH, and if they decide they do I'll just make them choose a better password.

---

