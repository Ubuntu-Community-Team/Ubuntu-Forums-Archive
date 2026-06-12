---
title: "SSH tunnel for the public"
date: 2008-09-02
forum: Security
---

### Post by blackicepro on 2008-09-02
Hello, I have a server set up that's running ubuntu. I'm wondering if it's possible to create a SSH account for the "public" so they can ssh tunnel their traffic through my box. The main problem with that is security, as they can login and run commands. 
Is there a way for them to be able to connect and proxy their traffic though ssh while restricting their access to /usr/bin so they can't execute any commands and they can't execute/read/ write any files?

Thank you

---

### Post by blackicepro on 2008-09-02
Ah crap, sorry guys. I didn't post in the correct thread. Can a moderator move this? thank you

---

### Post by moonpup on 2008-09-02
Although this is completely possible to do, I question your motivation to do so? Is there a reason why you want to become a public proxy?

Although there is good in providing this, you open yourself up to a lot of nasty people looking to use your box as a launching pad into other systems while hiding behind your ip address for which you will be held accountable.

You may want to rethink this...

---

### Post by blackicepro on 2008-09-02
I would only give it to selective people. I'm in a university and some people want to use the ssh tunnel to increase their protection on wifi.

---

### Post by kpatz on 2008-09-02
**man sshd**

Read up on AuthorizedKeysFile (default ~/.ssh/authorized_keys).

You can give them a key that is set up with the no-pty option, which prevents a tty from being allocated to the session, thus preventing the user from getting a shell.  You can also set restrictions on port forwarding in this file.

For the best security, I'd give each user their own key, preferably with a passphrase.  Then you can control access by user, and revoke any keys that get compromised or abused.  You could send the port forwarding through a squid proxy to log and restrict access as well.

---

### Post by blackicepro on 2008-09-02
Thanks for the reply. I'll get on it asap :)

---

### Post by Biochem on 2008-09-02
Since all you want is secure traffic for the clients I would suggest openvpn. You can use it with port forwarding ( I use shorewall to do it and setup iptables at the same time). That way, there is no shell and you don't have to create accounts. You can create as many keys as you want or sign the one created by the clients. And you can revoke them also.

If your plan involes many clients I strongly recommand a solution where there is some form of individual authentification. That way you will be able to revoke access to an abuser without cutting the services to the others.

---

### Post by sfenton on 2009-06-22
I know this is an old thread, but the comments about openvpn and SSH is like what I'm trying to setup. 

I have the openvpn, and that is working fine, but I need to allow a person to deposit an image on a PC protected by openvpn. I've been trying all sorts of configurations with iptables, but I still get the PC to respond to the SSH request. I know it's got to do with the forwarding, but it doesn't get out of the openvpn box. tcpdump shows the request coming in from the ethernet adapter, but nothing going out the tunnel adapter. 

The client continues to show connection refused. 

I'l update this thread with the iptables when I can get to the openvpn box. 

If I could see some same iptables lines, I can configure it for me. 

Regards, 

Symon

---

### Post by sfenton on 2009-06-22
A little more help from the Internet and I got this working. For future reference here are the two commands in IPTABLES. 

-A FORWARD -p tcp -m state --state NEW --dport 22 -i tun0 -j ACCEPT

This forwards port 22 to the tunnel, I believe. 

-A PREROUTING -i eth0 -p tcp -m tcp --dport 22 -j DNAT --to-destination 10.9.0.6:22

This Nat's port 22 to port 22 at the remote server. 

Please correct me, if I've got that wrong. 

Cheers, 

Symon

---

