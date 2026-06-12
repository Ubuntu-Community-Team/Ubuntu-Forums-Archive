---
title: "I have a basic ssh server configuration question"
date: 2012-05-12
forum: Security
---

### Post by rtedbyers on 2012-05-12
I have read through three pages of information on the basic configuration of ssh server, and it seems straight forward enough, but I have a nagging question they don't seem to address (I will keep looking, of course, but perhaps you can accelerate the pace of my study by pointing me to a resource that addresses my specific questions).

I will certainly be disabling login as root via ssh (though there is a question related to that and that is, does that also prevent the user from using sudo to gain root priviledges, and if not how can that limited also - NB: I am just beginning to study creation of new users in Ubuntu and how I can restrict certain users to a tiny sandbox, as it were - so even when a user gets in, he can't go exploring to see what else is on the LAN), and changing the port it uses to some random port number greater than 3000.

But, for my main question, my impression is that I can choose between public key/private key login or password login, but there is nothing said about whether or not they can be combined.

The question is this.  Can I use the public key/private key capability to permit a connection between my machine and only certain remote machines, and then use a username/password combination to require the user of that remote machine to prove he is the one user of that remote machine authorized to connect to my machine?  If so, how do I do this?  And related to this, how can I enforce a certain strength of password, as well as, say, 4096 RSA keys, to be required of users connecting remotely?

Thanks

Ted

---

### Post by markbl on 2012-05-12
> **rtedbyers said:**
> 
I will certainly be disabling login as root via ssh (though there is a question related to that and that is, does that also prevent the user from using sudo to gain root priviledges, and if not how can that limited also

You can and should disallow root login in /etc/ssh/sshd_config. That just means that all valid users have to log in with a name that is logged etc. So you won't have an anomymous "root" user logging in. If users need root privilege on a box then, completely independently of ssh, you give them sudo privilege or not, or for only some commands etc. Don't confuse ssh and sudo. Ssh is just about logging in to the box remotely. Sudo is about assigned privilege to users (once they are logged in).

> 
Can I use the public key/private key capability to permit a connection between my machine and only certain remote machines, and then use a username/password combination to require the user of that remote machine to prove he is the one user of that remote machine authorized to connect to my machine?  If so, how do I do this?  And related to this, how can I enforce a certain strength of password, as well as, say, 4096 RSA keys, to be required of users connecting remotely?

If you allow password access, then any ssh user can log in remotely with his password, and he can then also install his public key and can use ssh key from then on. Using a key is easier because he only has to enter the pass-phrase once and his client key chain will remember it while he remains logged in (on his client pc). A password has to be entered every time and can not be cached. Or you can force all ssh users to use keys in which case they can not log in with a password and so will have to mail you their public key for you to install (in their ~/.ssh/authorized_keys) before they can log in.

I don't know about restricting access to specific client machines, and requiring minimum key sizes, etc. These options are probably possible. Read man sshd_config.

---

