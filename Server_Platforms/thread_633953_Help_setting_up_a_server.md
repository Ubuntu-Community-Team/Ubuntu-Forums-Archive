---
title: "Help setting up a server"
date: 2007-12-07
forum: Server Platforms
---

### Post by v2k on 2007-12-07
Hello, I'm kinda new to linux and I would like to setup a small home server and I hope I could get some help here. ^^

I'm running 6.06-server base install and I need help to set it up to work as..
[LIST]
[*]SMB shares (Local)
[*]FTP (Local / Internet)
[*]Web interface (Local / Internet)[LIST]
[*]SMB administrations ex. add/remove share and users
[*]FTP administrations ex. add/remove share and users
[*]Torrent download
[/LIST]
[/LIST]

---

### Post by gaten on 2007-12-07
Well, you might want to be a bit more specific. At least try to do some of the stuff and see where you get stuck. But i'll do the best I can to give you some direction. 

For samba, look at SWAT (it;s in the repos, and there are a bunch of tutorials out there), 

As far as FTP goes, you might want to think about SSH or sFTP at least, especially if you're going to be accessing the FTP server from outside your local network.

---

### Post by HermanAB on 2007-12-07
Hmm, start by doing a straight up Ubuntu or Xubuntu install.  Then add Firestarter to configure iptables, before doing anything else.

After that, install openssh, proftpd and Samba - in that order of difficulty.  Get them going one by one, before tackling the next one.

Cheers,

Herman

---

### Post by mmichalik on 2007-12-07
I would also suggest using Webmin as an administrative tool.  It eases newer people into server administration very nicely.  It has a lot of features, more then you will probably ever need and it's just makes things organized.

We run Webmin on all of our servers for a variety of different administrative tasks and we like it.  We manage our DNS, VPN, IPtables, Postfix and all it's side programs like ClamAV, Amavis and SpamAssassin, Apache2 and NFS mounts. 

[www.webmin.com](www.webmin.com) will get you there.  They have a debian release for it with instructions on how to set it up.

It will simplify everything you are trying to do.

---

### Post by v2k on 2007-12-10
Thanks, I decide to go with samba, ProFTPd, Apache2, shorewall and administrate all with webmin and it works great, thanks. ^^

Now I need help with one more thing how should I configure the firewall? (I have 1 ethern card)
I want to only allow as I told in first post.

And another question.
Is it a big security risk to rune a own e-mail server if I don't have to much expertness with linux and security?

---

