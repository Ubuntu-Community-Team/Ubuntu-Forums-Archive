---
title: "Problems using OpenVPN"
date: 2010-08-04
forum: Security
---

### Post by espressobeanie on 2010-08-04
I installed OpenVPN and gadmin-openvpn-server from the repos and I can't seem to activate the openvpn server in the gui. I have the server certificate generated, and all the information on encryption protocols setup, and accounts named and ready, despite accounts that were already there, such as www-data, bind, ossec, etc... being listed. The server log states:

> PLUGIN_INIT: could not load plugin shared object /usr/lib/openvpn-pam-auth.so: /usr/lib/openvpn/openvpn-pam-auth.so: cannot open shared object file: No such file or directory.
Exiting


---

### Post by Bachstelze on 2010-08-05
This file does not seem to exist in Ubuntu.  Did you use some sort of guide or tutorial to set up OpenVPN?

---

### Post by espressobeanie on 2010-08-05
I haven't used a guide. I tried the manpage, but it only gives commands. There's an OpenVPN.net website, but I think that software is proprietary. They charge for connections or something. I'm using the openvpn package on the repo, and I haven't found any directions for it yet.

*Correction: I found a guide here: [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)* 
Going to give it a try.

---

### Post by hannuko on 2011-01-02
Yes.. same problem here.  This is the reason I definitely do not want to update my operating system very often. I already once made the openvpn to work, now installed all from scratch and again, I should do all the manual work to make the openvpn to work again.  Why is there gadmin-openvpn-server available at all, if it does not work?  Edit: see this: [http://ubuntuforums.org/showthread.php?p=10306785#post10306785](http://ubuntuforums.org/showthread.php?p=10306785#post10306785)  Well, another 'easy-to-config-tool" that does not work.. should have done all manually from the start, would save hours. this tool does not save any changes I make to the config. Tired of doing all again and again.. :-(   I give up.

---

### Post by The Cog on 2011-01-02
[http://openvpn.net/index.php/open-source/documentation/howto.html](http://openvpn.net/index.php/open-source/documentation/howto.html)

This is all I ever used. It's enough to let you create server and client config files. I found that when openvpn starts, it runs any config files it finds in /etc/openvpn.

---

### Post by spynappels on 2011-01-02
The link provided by The Cog is the only one I've ever used, and I've set up quite a few OpenVPN deployments. Just keep backups of your certs and keys and configfiles and there should be no problem, it is very easy to set up and maintain.

---

