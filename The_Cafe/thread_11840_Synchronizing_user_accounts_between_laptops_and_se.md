---
title: "Synchronizing user accounts between laptops and server"
date: 2005-01-19
forum: The Cafe
---

### Post by karih on 2005-01-19
Hello

I didn't know where to post this so please move it if you know a better place ;).

I will start by saying this hasn't got anything to do with "Ubuntu Linux" but this community is good and has a lot of knowledge and I figured I'd give it a try.

<History starts>
Me and my friend are setting up a kind of school network.  Originally we planned to use the SkoleLinux "distro" but after installing we found that inconvenient because SkoleLinux doesn't like being modified, I hope that will improve over time but we decided to drop that and do it from skratch.

We had three old machines we planned on using as thin-clients, so we installed Debian on the main server and set up [LTSP](ltsp.org) (amazingly easy to install) on the server and boom, the thin clients were up and running in not so long time, very neat if you ask me :).

Then we decided to add "the laptops" to the network.  The networks has some 15 user accounts and all users should be able to login to the thin-clients and the laptops.  We figured installing Debian on the laptops too, and using [Unison](http://www.cis.upenn.edu/~bcpierce/unison/) (as SkoleLinux does) to synchronize users home directories (without syncing hidden dirs/files) between the main server and the laptops and that will propably do its job easily.  
<History ends - Problem begins>

The problem we are facing are the user accounts.  A user that is added on the main server should automaticly be added on all the laptops (and vica-versa if that is possible).  Also if user modifies his password (or user-account) it should be changed across the entire network.  The best part is that the laptops won't always be connected to the network, so users should be able to login to a laptop without being connected to the main server.  The only good idea we had was using Unison (again) to synchronize /etc/passwd and /etc/shadow between the computers but that doesn't look to pretty to me (since the system might come with different users to start with so user id's might be different and I see endless problems with this).  Probably there is something else needed to be synchronized between the computers that I am forgetting, but the same solution should go for that.

So I ask, has anyone a good suggestion on how to do this, or a hint in the right direction?

Thanks in advance!

---

### Post by nocturn on 2005-01-20
Bingo, you hit a sore issue with Linux...

Here is what I do, although this setup is still troubled too.

My server is set up as a NIS server, it holds all user data except the pw.
My server also runs Kerberos, this holds the authentication data (pw, policy, ...).
Each workstation, specially laptops are NIS slave servers, so NIS maps are automaticly pushed arround.  unfortunately, I cannot cache the Kerberos data, so that is not available on disconnects.

Each machine has a 'primary user', that one is locally known (overwriting NIS).  I had to do this because gksudo does not like my pam_krb5 module.  The local user has a second 'local' password to use the machine off the net, and run gksudo.

The homedirectories can be shared over NFS for connected operation, or synced using rsync for disconnected operations.  Unfortunately, multi-tier syncing presents problems...  

Another thing that might help is LDAP, although I have not tried it myself.
There is a PAM module with credential caching available from PADL software, this might do it for you.

---

### Post by karih on 2005-01-20
[QUOTE=nocturn]Bingo, you hit a sore issue with Linux...

Here is what I do, although this setup is still troubled too.

My server is set up as a NIS server, it holds all user data except the pw.
My server also runs Kerberos, this holds the authentication data (pw, policy, ...).
Each workstation, specially laptops are NIS slave servers, so NIS maps are automaticly pushed arround.  unfortunately, I cannot cache the Kerberos data, so that is not available on disconnects.

Each machine has a 'primary user', that one is locally known (overwriting NIS).  I had to do this because gksudo does not like my pam_krb5 module.  The local user has a second 'local' password to use the machine off the net, and run gksudo.

The homedirectories can be shared over NFS for connected operation, or synced using rsync for disconnected operations.  Unfortunately, multi-tier syncing presents problems...  

Another thing that might help is LDAP, although I have not tried it myself.
There is a PAM module with credential caching available from PADL software, this might do it for you.[/QUOTE]
 Hmm, ok.
Read about Kerboeros and had an idea to install "slave" server on all the laptops (to allow them to disconnect from the network) although that presents some security issues, but security isn't top consern, although more security is always better.

PAM sounds nice, although I haven't quite figured out exactly what it does ;)

Bah, better get reading...:)

---

### Post by nocturn on 2005-01-21
[QUOTE=karih]Hmm, ok.
Read about Kerboeros and had an idea to install "slave" server on all the laptops (to allow them to disconnect from the network) although that presents some security issues, but security isn't top consern, although more security is always better.

PAM sounds nice, although I haven't quite figured out exactly what it does ;)

Bah, better get reading...:)[/QUOTE]

PAM stands for Pluggable Authentication Modules.
It is a framework for authenticating that allows one layer to be replaced without affecting the others.  It's quite cool in fact.

Kerberos is quite secure in any case, unfortunately, to use it fully in Ubuntu some recompiling is needed...
Note also that Kerberos only does authentication, it is not a directory service, so it always has to be used toghether with something like NIS or LDAP.  

I think the LDAP credential caching module might help you.

---

