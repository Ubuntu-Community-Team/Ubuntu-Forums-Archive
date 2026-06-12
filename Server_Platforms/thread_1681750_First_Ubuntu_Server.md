---
title: "First Ubuntu Server"
date: 2011-02-04
forum: Server Platforms
---

### Post by auzzie2112 on 2011-02-04
hello everyone.
 
to start off i have set up a microsoft server 2003 setup and my house for experimental purposes but i have been reading on ubuntu server and how that is the way to go. I have the install disc but its not as simple as simply enabling roles such as domain controller, DHCP, and DNS on 2003.
 
What are the steps to successfully set up a domain contoller, DHCP, and DNS server on ubuntu server 10.10?
 
Just so i can connect all my machines to the server and connect to the internet. Basically at fist my server will act as a firewall/antivirus/spyware and give each machine an IP address. Eventually when i learn more ill setup Mail, FTP, Media Server, etc.
 
Anything helps! Thanks.

---

### Post by grimm08 on 2011-02-04
Working with linux is much different then working with Windows.

Ubuntu does not have a firewall on by default but ubuntu doesn't open ports up untill a package/service is activated.

For DHCP use dhcp3-server: use [http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html) for configuration.

For DNS use bind9: use [http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093) for configuration.  
Note, from my experience bind give me a lot of formatting error before running properly, so check your daemon log in /var/log when stopping and restarting bind with the command "tail -f /var/log/daemon.log". This will give you any errors.

Domain Controller you want to use open-ldap, can't help you there to much since I am still experimenting.

If your looking for a firewall system use IPcop, its free and all you need as an old desktop and a few network cards.  IPcop has firewall, av, and proxy capability just to name a few options.

Hope this helps.

Also before I forget Ubuntu does not use the root account, just use sudo for all your administrative commands, ex sudo useradd username.

---

### Post by auzzie2112 on 2011-02-04
wow! thanks a lot. that will definately suit my needs for right now thanks for the help. Ill get back to you if i run into any issues on the set up but i doubt there will with with instruction.

---

### Post by WannabeFantasma on 2011-02-05
Just stumbled upon this thread, since I'm playing with making a server might check those 2 links and stuff! Thanks!

---

