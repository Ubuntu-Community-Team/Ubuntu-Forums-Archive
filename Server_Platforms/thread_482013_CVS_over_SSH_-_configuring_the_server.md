---
title: "CVS over SSH - configuring the server"
date: 2007-06-23
forum: Server Platforms
---

### Post by cygnus81 on 2007-06-23
Hi

I'm trying to set a CVS server over SSH. But I cannot seem to make a tunnel to the cvs-pserver.

I'm using Eclipse, and I assume the pserverssh2 connection-type option there is what I need.

Basically what I want guess should happen is: ($client, %server)
$Eclipse establishes an SSH connection to the server.
$Eclipse tries to establish a connection to the pserver over the established SSH connection.
%sshd tunnels the connection to port 2401 (pserver) locally.
%xinetd, which is listening on port 2401 runs cvs pserver.

"client --2402--> sshd --2401--> inetd --2401--> cvs pserver", right?

What I've done so far:
1. Blocked cvs-pserver port (2401) on the firewall - to prevent direct (insecure) access to the pserver.
2. Added "cvsssh 2402/tcp" to /etc/services.
3. Opened cvsssh port (2402) on the firewall.
4. Added cvspserver to xinetd (with "only_from=localhost" but I guess this doesn't really matter since I blocked port 2401 from outside anyway).

The missing link: I don't know how to make sshd on the server, listen to port 2402 and redirect it to port 2401.
I looked around and I think I need to use either the -L or the -R options with ssh. But both seem to be executed on the client, and not on the server.. But I cannot execute this command on the client because I have neither access to Putty (or others. Its a Windows env' on the client) nor the will to execute such command before starting Eclipse. Can the tunnel be configured on the server ?

Thanks for any help :-)

---

### Post by dzoner on 2007-06-23
for cvs over ssh you don't need separate pserver daemon loaded

but as I can see it, you wan't to create tunnerl for pserver via ssh

---

### Post by cygnus81 on 2007-06-23
> **dzoner said:**
> for cvs over ssh you don't need separate pserver daemon loaded


As far as I understood this means the developer needs to manually login to the ssh server, and then use cvs "locally" on the server.

> **dzoner said:**
> 
but as I can see it, you wan't to create tunnerl for pserver via ssh

Yep. Even if its just for the sport. How can I do that - configure the tunnel on the server ?

---

### Post by dzoner on 2007-06-23
> **cygnus81 said:**
> As far as I understood this means the developer needs to manually login to the ssh server, and then use cvs "locally" on the server.



Yep. Even if its just for the sport. How can I do that - configure the tunnel on the server ?

I didn't played too much with tunneling through ssh, but I use my cvs through ssh with local user login.

My wincvs on developer machine is configured with default options, only hostname, login and passwords are changed, and cvs root as well.

---

### Post by cygnus81 on 2007-06-23
Well I got it. Just a big mistake on my side.
Simply had to tell Eclipse use extssh instead of pserverssh2, and all is well.

To sum it up, all I needed was:
1. Prevent access via pserver (blocking port 2401 and disabling cvspserver on xinetd/inetd).
2. Have an sshd running on the server (and of course have  cvs installed).
3. Set Eclipse to use extssh when connecting to the remote repository, or when connecting manually:
```

export CVS_RSH=ssh
cvs -d :ext:user@server/path/to/repository checkout module_name

```

As simple as that...

---

