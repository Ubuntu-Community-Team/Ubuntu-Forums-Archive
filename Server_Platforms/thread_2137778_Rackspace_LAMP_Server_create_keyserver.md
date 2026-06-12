---
title: "Rackspace LAMP Server create keyserver"
date: 2013-04-21
forum: Server Platforms
---

### Post by wolfgentleman on 2013-04-21
I created an apt repository on my rackspace server by rsyncing a local repository. I want to create a PGP keyserver like keyserver.ubuntu.com but I can't find any documents on how to do it... I can't install anything, I don't have root access so I want something that I can rsync to it or something like that. Is this possible?

Any help is appreciated.

---

### Post by Lars Noodén on 2013-04-22
The Universe repository has the package [sks](http://packages.ubuntu.com/quantal/sks), though there might be others.  I found a fair number of documents about setting up a key server doing a regular web search.  Here is one that applies to SKS:

[http://www.bauer-power.net/2010/05/how-to-setup-free-pgp-key-server-in.html](http://www.bauer-power.net/2010/05/how-to-setup-free-pgp-key-server-in.html)

---

### Post by wolfgentleman on 2013-04-22
Like I said in the OP I don't have root, because I am not the server owner. I just use it. All I have is SFTP/Rsync access. The user account I have is a standard user, not even sudo access. So I guess its not possible... I was hoping I could do like I did with the apt repository.

---

### Post by CharlesA on 2013-04-22
Doubt it. You would need either root access or sudo rights to install anything. Ask the person responsible for the server what you can do.

---

### Post by Lars Noodén on 2013-04-23
It is not as nice as installing with APT, it's more work to maintain, but you could grab the source and try to install it to your home directory.  I've done that with other packages before.  

You might be able to get the source via **apt-get source sks** or else directly from the [sks project](https://bitbucket.org/skskeyserver/sks-keyserver/wiki/Home) web site.  However, looking at the code I don't see any obvious way to tell it to install in a particular part of the file system.  The README file doesn't have that info and there is no INSTALL file.

---

### Post by Lars Noodén on 2013-04-23
There is also a development mailing list for SKS over at GNU Savannah:

[https://savannah.nongnu.org/projects/sks/](https://savannah.nongnu.org/projects/sks/)

It might be able to help you install SKS to a non-standard, unprivileged location in your account.

---

### Post by wolfgentleman on 2013-04-27
> **Lars Noodén said:**
> It is not as nice as installing with APT, it's more work to maintain, but you could grab the source and try to install it to your home directory.  I've done that with other packages before.  

You might be able to get the source via **apt-get source sks** or else directly from the [sks project]("https://bitbucket.org/skskeyserver/sks-keyserver/wiki/Home") web site.  However, looking at the code I don't see any obvious way to tell it to install in a particular part of the file system.  The README file doesn't have that info and there is no INSTALL file.




There is also a development mailing list for SKS over at GNU Savannah:

[https://savannah.nongnu.org/projects/sks/](https://savannah.nongnu.org/projects/sks/)

It might be able to help you install SKS to a non-standard, unprivileged location in your account.

There is only one problem there. To my knowledge the server only has port 80 forwarded.

---

