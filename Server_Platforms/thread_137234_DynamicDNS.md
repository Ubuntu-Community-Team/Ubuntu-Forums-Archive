---
title: "DynamicDNS"
date: 2006-02-27
forum: Server Platforms
---

### Post by Useless on 2006-02-27
I have a webserver set up in a company network.  Now this network is a Activer DIrectory Windows Domain based network.  This being the only linux box on the network it is a little tough sometimes as i am administering it.  The main question i had was how do i configure dynamic dns on this box through a terminal.  I had configured all the settting such as the domain, static IP, and dns servers, but not dynamic dns.  I could have one of the windows admins configure it manually....but that would be too easy.  Any help would be appreciated.

---

### Post by colo on 2006-02-27
To be honest: I don't know exactly what you want to do, but if it happens to be configuring a dyndns-service (like [www.dyndns.org)](www.dyndns.org)), there's an excellent Perl-powered daemon for this kind of thing, **ddclient**. It's in Ubunut's repos, too:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ddclient&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ddclient&searchon=names&subword=1&version=all&release=all)

Hth :)

---

### Post by az on 2006-02-27
There are several dyndns clients available through the repos, but I have found ddclient the easiest.

You can install it and it will prompt you for your user information.  You can edit the /etc/ddclient.conf file (I may be wrond about the name of the file) or just run
sudo dpkg-reconfigure ddclient
to re-run the configuration scripts.

You set and forget it.

---

### Post by TeeSeeJay on 2006-02-28
He's not asking for a dyndns client such that you'd find as a service on the Internet. He's asking about Dynamic DNS, a feature extant in Windows and BIND DNS servers.

To the OP: I haven't gotten this figured out myself, but if I can point you in the right direction, I'd say check the docs for the dhclient software (the dhcp client).

---

### Post by az on 2006-02-28
This is over my head.  Maybe look here:
[http://www.debian-administration.org/](http://www.debian-administration.org/)

---

### Post by Useless on 2006-02-28
DDclient is a great tool, but i dont think it is exactly what i am looking for.  It seems as though this is more for something connecting out to the internet.  I need a dynamicDNS to connect to something within a Active Directory Network.  Perhaps i am just setting up ddclient up wrong, or there is some custom script i would need.

---

### Post by Useless on 2006-02-28
the thing is, i dont have the server setup with a dhcp configuration nor do we use it.  Mostly it all runs on static addresses.  I could just configure the manual entry in the Active directory network, but i was wondering how to configure it on the local workstation/server end rather than on the directory end.

---

