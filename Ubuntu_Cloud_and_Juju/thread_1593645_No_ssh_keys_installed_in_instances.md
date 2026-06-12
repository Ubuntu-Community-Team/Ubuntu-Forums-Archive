---
title: "No ssh keys installed in instances"
date: 2010-10-11
forum: Ubuntu Cloud and Juju
---

### Post by obast on 2010-10-11
While I can start instances in my UEC install, I can't do anything with them. 

After some poking around and with the help of ssh -v, I've figured out that the problem is that the ssh-keys aren't getting installed.

What I don't know is how to fix that!

I've tried deleting my old key-pair and making a new one, but that didn't help. 

Any suggestions?

I suspect that part of the problem might be running both the cloud controller and the node controller on the same machine. I already found that I had to remove the node, then re-register it to get it to show up.

---

### Post by Rusty au Lait on 2010-10-11
I found out the hard way that every time you restart an instance it recreates the ssh key pair (not your mykey.priv). The one I created the first time I sshed in using ssh -i ~/.euca/mykey.priv ubuntu@ip_of_insidence is still in my .ssh/known_hosts file (the one for all ssh public keys based on the ip address). When I restart an instance (or when I used the same IP address for some other ssh keyed access) the login fails because it is now the wrong ssh public key. The error returned from a failed login shows the line number in the known_hosts file. I edit known_hosts and delete the offending line. All is well.
Is this your problem?
ElasticFox and HybridFox do not tell you this when you click on the button to log into the instance, they just fail without explanation.

---

### Post by obast on 2010-10-11
No, it never gets to the key negotiation at all, it fails early. So there are no ssh keys period.

---

### Post by kim0 on 2010-10-12
If you don't get a reply here, you can try the ubuntu-cloud mailing list too
[https://lists.ubuntu.com/mailman/listinfo/Ubuntu-cloud](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-cloud)

---

