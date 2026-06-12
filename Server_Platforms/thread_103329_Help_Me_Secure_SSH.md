---
title: "Help Me Secure SSH"
date: 2005-12-13
forum: Server Platforms
---

### Post by Geekboy on 2005-12-13
I am currently using ssh and Freenx to connect to my box from work.  SSH and Freenx work great, no problem there.  I happened to go through my /var/log/auth.log (read about this in another post) and found out that I have been the target of a hack.

I realize now that I need to take some more precautions.  I already have a good password, but I would like to tighten up the box.  So I would like to do the following:

1. Change the port number of SSH.  I know that a port scan will discover the new port number, but I am hoping to avoid some of the attacks with this.  I figure this is just a simple change.

2.  Set up Key-based authentication.  I've read about this in the forums, but I am not sure how to do this.  I use PUTTY on my Windows XP laptop at work to connect from work.  Would this change anything?

3.  Any other suggestions?  I heard about excluding IP subnets in IPtables.  How do I go about that?

Thanks for any help.  I'm off to Google to do some research now.

---

### Post by Zelut on 2005-12-13
sounds like the easiest way to tighten down your box would be to install firestarter & ONLY allow connections from known, trusted IPs (ie; your work).  that is what I've done on my system.  It only allows connections from my office and a few other trusted IPs.  This way, no matter if you have a wide-open password, nobody can connect to you unless they're on your list.

---

### Post by drogoh on 2005-12-13
[QUOTE=Geekboy]
2.  Set up Key-based authentication.  I've read about this in the forums, but I am not sure how to do this.  I use PUTTY on my Windows XP laptop at work to connect from work.  Would this change anything?
[/QUOTE]

Nothing would change.  SSH keys are portable.

Most "attacks" are just from zombied machines.  I use [bruteforceblocker]("http://danger.rulez.sk/projects/bruteforceblocker/") on my FreeBSD machine but you can edit it for iptables.  He even tells you what to change.

---

### Post by cactus on 2005-12-14
You might try this too: [http://denyhosts.sourceforge.net/](http://denyhosts.sourceforge.net/)

and the faq there has good tips for securing ssh in general..
[http://denyhosts.sourceforge.net/faq.html#1_3](http://denyhosts.sourceforge.net/faq.html#1_3)

---

### Post by Geekboy on 2005-12-14
[quote=cactus]You might try this too: [http://denyhosts.sourceforge.net/]("http://denyhosts.sourceforge.net/")

and the faq there has good tips for securing ssh in general..
[http://denyhosts.sourceforge.net/faq.html#1_3]("http://denyhosts.sourceforge.net/faq.html#1_3")[/quote]

That looks great! :p  Definitly will be installing that tonight.  Wish their was a package for it.  Thanks for the great tip.

Any advice on the key-based authentication?  I searched the forums and couldn't come up with any sort of setup guide (other than people saying that I should use it).

---

### Post by cactus on 2005-12-14
Some useful ssh key info.
[https://wiki.ubuntu.com/SSHHowto?highlight=%28ssh-key%29](https://wiki.ubuntu.com/SSHHowto?highlight=%28ssh-key%29)
*Public key authentication*

and maybe some of these for more info..
[http://www.arches.uga.edu/~pkeck/ssh/](http://www.arches.uga.edu/~pkeck/ssh/)
[http://www-128.ibm.com/developerworks/linux/library/l-keyc.html](http://www-128.ibm.com/developerworks/linux/library/l-keyc.html)
[http://www-128.ibm.com/developerworks/linux/library/l-keyc2/](http://www-128.ibm.com/developerworks/linux/library/l-keyc2/)
[http://www-128.ibm.com/developerworks/library/l-keyc3/](http://www-128.ibm.com/developerworks/library/l-keyc3/)

---

### Post by LordHunter317 on 2005-12-14
Denying hosts is silly unless you can't enforce a strong password policy.  In which case, you ought to whitelist, not blacklist.

Setup strong passwords or use keypairs and disable passwords; then forget about the attacks.

---

### Post by Felipe_U on 2005-12-14
I had my ssh server to only allow connection with public keys. Once I installed freenx I had to allow conns with passwords because I don't know how to configure the freenx to use the ssh key.
Any idea on how to make the freenx use the ssh keys??

Regards,
Felipe

---

### Post by noigeaR on 2005-12-18
I have exactly the same problem. I would like to run freenx without allowing passwords on sshd. Simple ssh connections work. I just need the public key and enter the passphrase to login. Freenx on the other hand only works when logins with passwords are allowed, so how do you setup freenx to use keys with a passphrase?

---

### Post by Vorik on 2006-01-11
I've got the same problem, authentication with a passphrase is still impossible. Or not?

Please let us know!

Many thanks,
Vorik

---

### Post by Mr_Grieves on 2006-01-11
Only allow connections from trusted IP-adresses or IP-networks.
You can controll this in /etc/hosts.allow and /etc/hosts.deny

Hosts.allow is a whitelist, once you have entered a IP-adress/network for a service there, everyone else is automaticly blacklisted.

Hosts.deny is a blacklist. Using that you will allow everyone that is not listed, wich is generally not a good idea, like people above already told you.

You're hosts.allow file should look like this:

```

# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5), hosts_options(5)
#                   and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8), rpc.mountd(8) and
# /usr/share/doc/portmap/portmapper.txt.gz for further information.
#
SSH: 192.168.124.66,192.168.135.

```

Note that you use a comma to separate adresses. Above config allows one separate IP-adress and a IP-network (C-net), including the 255 diffrent adresses in the network. (192.168.135.0-255)

---

### Post by Vorik on 2006-01-12
Hi!

Thanks for your reply.

For my work, I really need to be able to authenticate with a public key/passphrase. 

SSH works, but I cannot get FreeNX to work like that...
I've heard that my co-worker did get it to work, if I find out, I'll let it be known here.

Many thanks,
Ger.

---

### Post by Vorik on 2006-01-13
Hi!

Here the promised solution to my problem....

I saw in /var/log/auth.log that the nx user was locked. So a 
```
passwd -u nx
```
did the trick eventually.. 

How to connect using a key with a passphrase:
```
ssh-add [path-to-keyfile]
```
and enter your passphrase.

Then you can connect as usual. Note that the public key needs to be added to the homedir of the nx user (cat /usr/passwd | grep nx) ~/.ssh/authorized_keys2 file. (more detailed explanation at [http://www.ubuntuforums.org/showthread.php?t=29013](http://www.ubuntuforums.org/showthread.php?t=29013) second post)

Vorik.

---

### Post by thingy on 2006-07-22
> **Vorik said:**
> Hi!

Thanks for your reply.

For my work, I really need to be able to authenticate with a public key/passphrase. 

SSH works, but I cannot get FreeNX to work like that...
I've heard that my co-worker did get it to work, if I find out, I'll let it be known here.

Many thanks,
Ger.


I too wanted to be able to use my SSH passphrase with NX just like I do with SSH.

Problem is you can't!

The only thing you can do is:

1) In the /etc/ssh/sshd_config, ensure these two are setup as follows:

PasswordAuthentication no
UsePAM no

2) In the /usr/NX/etc/server.cfg, ensure that this is setup as follows:

ENABLE_PASSWORD_DB = "1"


3) Do:

cd /usr/NX/bin
./nxserver --usercheck username

it should say your user doesn't have a password, then type in:

./nxserver --useradd username

which will prompt you for a password!

From what I can tell, this password is only used by NX and ssh will continue to not accept any password based logins.


jin

---

### Post by Vorik on 2006-07-23
Ehr....... That's my setup. 

In what way am I not using a certificate logon through SSH then?

With a username/password combo I cannot logon to my server, just with a certificate. That I have to supply an additional password is of little relevance to me.

It's the security bit that is most important to me.

Vorik.

---

### Post by RavenOfOdin on 2006-07-26
I'm also looking into setting up a SSH server.

I'll echo the rest of this about "change the port number" and "restrictive firewall" . . . Also. . .Make sure to run DenyHosts in daemon mode and install the version of Python that your .rpm/.deb requires.

That step is VERY important, it tripped me up the first time so I was left without a running service.

At least I didn't have any ports open. :p

---

### Post by Vorik on 2006-07-26
If you're looking to secure your ssh access have a look at sshdfilter.

I run it on my server to prevent brute-force attacks (occurs at least twice a day)

Vorik

---

