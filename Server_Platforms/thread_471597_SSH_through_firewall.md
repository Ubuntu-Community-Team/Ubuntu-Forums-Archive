---
title: "SSH through firewall"
date: 2007-06-12
forum: Server Platforms
---

### Post by apoth on 2007-06-12
I've asked the network admin at work to forward a port on the firewall for SSH access. He's forwarded external port 8080 to 8080 on a local machine.

If I run apache on port 8080 on the local machine I can see it from the internet fine.

If I run sshd on port 8080, although I can see it from the local network I can't connect from the internet, the ssh client just hangs.

Any suggestions? Thanks.

---

### Post by MJN on 2007-06-12
Are you using the correct client command to specify the port?
 
Mathew

---

### Post by apoth on 2007-06-12
I'd assume so because it works locally.

ssh -p 8080 ip.add.re.ss

---

### Post by MJN on 2007-06-12
I only asked because we had a similar thread recently which went round the houses for a bit until it became apparent that the wrong command syntax had been used (but not mentioned)!
 
I'm not sure what else to suggest... the port forwarding obviously works. Can you run a packet trace (with ethereal or whatever) on the local machine to check if any packets are coming through at all?
 
Mathew

---

### Post by gaten on 2007-06-12
Try telneting to the open port from outside the network to make sure it's not the server:
```
telnet ip.ad.dr.es 8080
```It should return something like this:
```
Trying ip.ad.dr.es...
Connected to ip.ad.dr.es.
Escape character is '^]'.
SSH-2.0-OpenSSH_4.3p2 Debian-5ubuntu1
```If  you get that, the server/port forwarding is working fine. If you don't get something like that, make sure the port is accessible from the outside world with something like Open port checker: [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by apoth on 2007-06-12
Thanks. I did try the telnet idea a few days ago. At the moment it connects but doesn't print the SSH version string - however it did print it when I tried it a few days ago, but that was on a Windows machine and I don't have one to test it with at the moment. I may as well say that the IP is 217.37.54.13.

In fact I do get the ssh string when I view it in a web browser (SSH-2.0-OpenSSH_4.3p2 Debian-5ubuntu1), so it's definitely there, at least in spirit!

Thanks again.

---

### Post by gaten on 2007-06-12
If that doesn't work (or works erratically) then I would start checking the server logs located in   **/var/log/auth.log**. Also, try connecting  to the server using the "debug" mode of the client:
```
ssh -v ip.ad.dr.es
``` 

Also, the server can be debugged (it will run in the foreground and print out messages you can review) with:
```
sshd -de
```

If you see something odd, post it here any maybe we can figure it out.

Oh, and are you trying to connect remotely with a hostname or IP address?

---

### Post by apoth on 2007-06-13
sshd gives me this...

```
$ sudo /usr/sbin/sshd -de
debug1: sshd version OpenSSH_4.3p2 Debian-5ubuntu1
debug1: read PEM private key done: type RSA
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: private host key: #1 type 2 DSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-de'
debug1: Bind to port 8080 on ::.
Server listening on :: port 8080.
debug1: Bind to port 8080 on 0.0.0.0.
debug1: Bind to port 22 on ::.
Server listening on :: port 22.
debug1: Bind to port 22 on 0.0.0.0.
```

Then nothing when I attempt to connect from outside the LAN.

/var/log/auth.log gives me nothing when I attempt to connect from outside the LAN.

And just the following output from the client before it hangs:

```
ssh -v -p 8080 -l username 217.37.54.13
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 217.37.54.13 [217.37.54.13] port 8080.
debug1: Connection established.
debug1: identity file /home/username/.ssh/identity type -1
debug1: identity file /home/username/.ssh/id_rsa type -1
debug1: identity file /home/username/.ssh/id_dsa type -1
```

Could someone try and see if they can get a username prompt perhaps?

---

### Post by MJN on 2007-06-13
A connection, but no prompt:

```

**ssh -v -p 8080 217.37.54.13**
OpenSSH_4.2p1 Debian-7ubuntu3.1, OpenSSL 0.9.8a 11 Oct 2005
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 217.37.54.13 [217.37.54.13] port 8080.
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug1: identity file /home/user/.ssh/id_rsa type -1
debug1: identity file /home/user/.ssh/id_dsa type -1

```

Mathew

---

### Post by gaten on 2007-06-13
> debug1: Bind to port 8080 on ::.
Server listening on :: port 8080.
debug1: Bind to port 8080 on 0.0.0.0.
[B]debug1: Bind to port 22 on ::.
Server listening on :: port 22.
debug1: Bind to port 22 on 0.0.0.0.[/B]See those last three lines? That tells me that the ssh server binds to port 22 for some odd reason. Check your /etc/ssh/sshd_config and make sure you don't have two **Port** directives or something.

---

### Post by apoth on 2007-06-13
I do have two port directives, it's not a mistake. It's so people at work can easily find the SSH server, but I also want it available to people working from home, but those people will need to ask for instructions anyway to tunnel subversion over SSH so they get whatever non standard port the network guy gives out (8080). Both ports accept SSH connections locally without a problem.

---

### Post by netlogic on 2007-06-13
> **apoth said:**
> I've asked the network admin at work to forward a port on the firewall for SSH access. He's forwarded external port 8080 to 8080 on a local machine.

If I run apache on port 8080 on the local machine I can see it from the internet fine.

If I run sshd on port 8080, although I can see it from the local network I can't connect from the internet, the ssh client just hangs.

Any suggestions? Thanks.

i am not exactly understanding your question. why is your admin evolved if ssh is already allowed to go out? you can tunnel localport to any port from your ssh destination.
  -L local_port:destination_host:destination_port

---

### Post by netlogic on 2007-06-13
Wait.. Are you trying to tunnel to your desktop from outside, so you can view your apache server?
port 8080 is your apache server, so you shouldn't be ssh into your apache. are you trying to create a local loop? if you want your local machine that is outside to be your apache server.

your firewall has to be mapped to your ssh port number in the LAN machine.
the firewall port 8020 outside the firewall is your LANip address of 22 or 8020 if your firewall doesn't offer port redirection.

once, you test and can ssh into your LAN machine from the outside, logout and try tunneling the ssh port that you need to use.

ssh -p 8020 domainname -L 8080:localhost:8080 sleep 99999 

What this means, It will login you using port 8020 to pass through the firewall and forward 8080 back to localhost machine at 8080

if you open your browser, type
[http://localhost:8080](http://localhost:8080)
it should be the apache machine at work.

---

### Post by netlogic on 2007-06-13
I almost forgot... If the firewall is blocking ssh in, but ssh out.
You can create a "Reverse" ssh tunnel.
The reverse tunnel will allow you to create an ssh tunnel from your work computer to your home computer,  You must install ssh servers on the both side.

ssh -R remote_port:localhost:22 your_home_pc

you can even create a cron job from the work computer to constantly reconnect to your home pc, so the connection can be forwarded back.

At home, you would then run ssh -p remote_port_number_you_mapped localhost

That is why ssh policy has to be properly implemented in the network. It can be a serious security risk for network thieves (black hat hackers)

---

### Post by apoth on 2007-06-14
I'm trying to access SSH on a server at work from a desktop at home. SSH on the server at work **does** run on port 8080 as I've configured it to. I temporarily put apache on 8080 to test the port forwarding through the firewall.

The firewall is port forwarding from 8080 outside the work network to 8080 on the SSH server inside the work LAN.

The reverse SSH tunnel might do the trick without sorting out the port forwarding.

---

### Post by netlogic on 2007-06-14
Why are you sharing your apache and ssh on the same port?

---

### Post by MJN on 2007-06-14
He's not - the Apache-on-8080 was just a test to prove the port forwarding was working!

Apoth, you haven't got any restriction in the SSHD config file that may be stopping external connections? Aside form the port modifier have you made *any* other changes to the config?

Any firewall in place?

Mathew

---

### Post by apoth on 2007-06-18
Ugh. I got to the bottom of this. The guy that forwarded the port had put a restriction of only allowing HTTP traffic through. Hence apache worked and I could use a web browser to see the SSH string but nothing else worked.

Thanks guys.

---

