---
title: "Ways to secure my server"
date: 2010-06-19
forum: Security
---

### Post by nautica17 on 2010-06-19
I've set up a server for the first time today, and I'm reading up on how to secure it. But I was wondering if anyone here would give me some tips from personal experience on what to do before going online with my website for the whole world to see. I'm running Ubuntu Server edition and Apache. Am I good to go with default settings or is there anything recommended that I should first do?

---

### Post by CharlesA on 2010-06-19
Are you only running Apache or are you running other services as well (SSH, Samba, etc)?

---

### Post by HermanAB on 2010-06-19
Hmm, make sure that you passwords are all really long > 9 characters.  Most security issues in Ubuntu are caused by people thinking that a 4 character password would be kewl.

---

### Post by yeleek on 2010-06-19
> **nautica17 said:**
> I've set up a server for the first time today, and I'm reading up on how to secure it. But I was wondering if anyone here would give me some tips from personal experience on what to do before going online with my website for the whole world to see. I'm running Ubuntu Server edition and Apache. Am I good to go with default settings or is there anything recommended that I should first do?

Loads of good stuff online - below off the top of my head.
1) Put the server in a DMZ
2) Specify specific firewall rules allowing only the ports you need into the DMZ.
3) Keep it patched and up to date
4) Keep the permissions needed on the web server to the minimum needed
5) If the website is a dynamic site (PHP, Mysql, etc) - Use best practice when it comes to coding
6) Complex passwords as has been said
7) Disable all unrequired services so as to minimize possible vulnerabilities
8) Don't keep any development files/passwords on the box - obvious i know
9) Back it up to a device not in the dmz regularly - preferably with imagine technology (clone zilla?) so in the event its compromised, you can blow a good image straight back onto the box (once you've fixed the original vulnerability).

---

### Post by nautica17 on 2010-06-19
> **CharlesA said:**
> Are you only running Apache or are you running other services as well (SSH, Samba, etc)?
I plan to run both Apache and SSH. 

> **HermanAB said:**
> Hmm, make sure that you passwords are all really  long > 9 characters.  Most security issues in Ubuntu are caused by  people thinking that a 4 character password would be kewl.
Alright cool, got that at least. 

> **yeleek said:**
> Loads of good stuff online - below off the top of  my head.
1) Put the server in a DMZ
2) Specify specific firewall rules allowing only the ports you need into  the DMZ.
3) Keep it patched and up to date
4) Keep the permissions needed on the web server to the minimum needed
5) If the website is a dynamic site (PHP, Mysql, etc) - Use best  practice when it comes to coding
6) Complex passwords as has been said
7) Disable all unrequired services so as to minimize possible  vulnerabilities
8) Don't keep any  development files/passwords on the box - obvious i know
9) Back it up to a device not in the dmz regularly - preferably with  imagine technology (clone zilla?) so in the event its compromised, you  can blow a good image straight back onto the box (once you've fixed the  original vulnerability).

Sweeeet. I'll look into those! :)

---

### Post by mituw16 on 2010-06-22
another thing to look into if you're running ssh on the default port of 22 is to look at either 

fail2ban or
denyhosts

they both protect ssh against brute force attacks

---

### Post by metalf8801 on 2010-06-22
If you are going to be using MySQL after you have installed run this script 

sudo /usr/bin/mysql_secure_installation

after you do that it will ask you for you root password then your MySQL root password then it will ask you a few more important questions 

for more info [http://cloudservers.rackspacecloud.com/index.php/Ubuntu_-_MySQL_Installation](http://cloudservers.rackspacecloud.com/index.php/Ubuntu_-_MySQL_Installation)

---

### Post by cryptotheslow on 2010-06-22
Move ssh to a port other than port 22 to cut down on the number of lame bots hitting it.

Look into only allowing ssh access using keys rather than passwords.

Not just long passwords, but also strong passwords - combinations of lower & upper case letters, numbers and symbols with no dictionary word element to them. 
e.g. n[7w3&PnTy5_~w 

I generally go with 14+ characters.

[http://strongpasswordgenerator.com/](http://strongpasswordgenerator.com/) Always useful if you get tired of thinking them up yourself.

---

### Post by dfreer on 2010-06-24
> **yeleek said:**
> Loads of good stuff online - below off the top of my head.
1) Put the server in a DMZ
2) Specify specific firewall rules allowing only the ports you need into the DMZ.


I don't see how exposing the server from behind the router's firewall is a security feature. Sure you can rely on the server's firewall to protect it but why not have a second line of defence?

And #2 doesn't make any sense, because it's already completely exposed to the internet. That's what the DMZ does. Now, if you didn't have the server in the DMZ then only opening the ports you need in the firewall makes sense.

---

### Post by yeleek on 2010-06-24
Don't understand your point...  and i think you've misunderstood mine

1) means put the server in a DMZ - i.e. in an isolated area of the network protected by a firewall which is separate from the rest of your production network.  And you have to 'expose' it on at least one port for people to be able to connect to it.....

and you've said

'I don't see how exposing the server from behind the router's firewall is a security feature. Sure you can rely on the server's firewall to protect it but why not have a second line of defence?'

So that would seem to agree?

2) By only allowing access to the services you have to give access to on that server you stop individuals from attempting to connect on other ports.  If I only allow access to my server on an obscure port with a very specific service bound to it.  All other ports being blocked by a FW I'm limiting the options of a malicious individual.

---

### Post by yeleek on 2010-06-24
NIST Guidelines on FW's and FW policy
[http://csrc.nist.gov/publications/nistpubs/800-41-Rev1/sp800-41-rev1.pdf](http://csrc.nist.gov/publications/nistpubs/800-41-Rev1/sp800-41-rev1.pdf)

1) 'Many hardware firewall devices have a feature called DMZ, an acronym related to the demilitarized zones that are sometimes set up between warring countries. While no single technical definition exists for
firewall DMZs, they are usually interfaces on a routing firewall that are similar to the interfaces found on the firewall&#8217;s protected side. The major difference is that traffic moving between the DMZ and other
interfaces on the protected side of the firewall still goes through the firewall and can have firewall protection policies applied. DMZs are sometimes useful for organizations that have hosts that need to
have all traffic destined for the host bypass some of the firewall&#8217;s policies (for example, because the DMZ hosts are sufficiently hardened), but traffic coming from the hosts to other systems on the organization&#8217;s
network need to go through the firewall. It is common to put public-facing servers, such as web and email servers, on the DMZ.'


2)
'Generally, firewalls should block all inbound and outbound traffic that has not been expressly permittedby the firewall policy&#8212;traffic that is not needed by the organization. This practice, known as deny by default, decreases the risk of attack and can also reduce the volume of traffic carried on the organization&#8217;s networks. Because of the dynamic nature of hosts, networks, protocols, and applications, deny by default is a more secure approach than permitting all traffic that is not explicitly forbidden'

---

### Post by OpSecShellshock on 2010-06-24
> **yeleek said:**
> NIST Guidelines on FW's and FW policy
[http://csrc.nist.gov/publications/nistpubs/800-41-Rev1/sp800-41-rev1.pdf](http://csrc.nist.gov/publications/nistpubs/800-41-Rev1/sp800-41-rev1.pdf)

1) 'Many hardware firewall devices have a feature called DMZ, an acronym related to the demilitarized zones that are sometimes set up between warring countries. While no single technical definition exists for
firewall DMZs, they are usually interfaces on a routing firewall that are similar to the interfaces found on the firewall’s protected side. The major difference is that traffic moving between the DMZ and other
interfaces on the protected side of the firewall still goes through the firewall and can have firewall protection policies applied. DMZs are sometimes useful for organizations that have hosts that need to
have all traffic destined for the host bypass some of the firewall’s policies (for example, because the DMZ hosts are sufficiently hardened), but traffic coming from the hosts to other systems on the organization’s
network need to go through the firewall. It is common to put public-facing servers, such as web and email servers, on the DMZ.'


2)
'Generally, firewalls should block all inbound and outbound traffic that has not been expressly permittedby the firewall policy—traffic that is not needed by the organization. This practice, known as deny by default, decreases the risk of attack and can also reduce the volume of traffic carried on the organization’s networks. Because of the dynamic nature of hosts, networks, protocols, and applications, deny by default is a more secure approach than permitting all traffic that is not explicitly forbidden'

Precisely. If you have a device on your network that allows connections to be initiated from the open web, then it should be separated by the firewall from the other devices on the same network that are not meant to have connections initiated from the web.

---

### Post by dfreer on 2010-06-24
I'm refering to a home router's DMZ function, which operates in a different manner from a DMZ in say a large corporation.

A home router's DMZ will completely expose the server's ports to the internet, without the protection of the router's firewall. In addition, the server will still be able to communicate with other clients behind the router's firewall as normal. Therefore if an attacker gains access to the server, he can attack clients on the network behind the router's firewall.

The DMZ set up for large companies actually places the server in a separate logical subnet, with a firewall between the clients and the server, and sometimes a different firewall between the servers and the internet. This seems to be what you are referring to I think. 

So if the OP is behind a home router, it's advisable NOT to use the DMZ.

---

### Post by yeleek on 2010-06-25
> **OpSecShellshock said:**
> Precisely. If you have a device on your network that allows connections to be initiated from the open web, then it should be separated by the firewall from the other devices on the same network that are not meant to have connections initiated from the web.
Hear Hear!

> **dfreer said:**
> I'm refering to a home router's DMZ function, which operates in a different manner from a DMZ in say a large corporation.

A home router's DMZ will completely expose the server's ports to the internet, without the protection of the router's firewall. In addition, the server will still be able to communicate with other clients behind the router's firewall as normal. Therefore if an attacker gains access to the server, he can attack clients on the network behind the router's firewall.

The DMZ set up for large companies actually places the server in a separate logical subnet, with a firewall between the clients and the server, and sometimes a different firewall between the servers and the internet. This seems to be what you are referring to I think. 

So if the OP is behind a home router, it's advisable NOT to use the DMZ.

'In addition, the server will still be able to communicate with other clients behind the router's firewall as normal.' isn't a true DMZ.  A server in a DMZ is completely isolated... hence 'The major difference is that traffic moving between the DMZ and other interfaces on the protected side of the firewall still goes through the firewall and can have firewall protection policies applied'.

---

### Post by lisati on 2010-06-25
A couple of ideas:[LIST]
[*]In certain circumstances, by default, Apache will display things like its version and give an idea of some of the stuff you have installed in its banner. You can do some customization of what gets displayed here: [http://www.ducea.com/2006/06/15/apache-tips-tricks-hide-apache-software-version/](http://www.ducea.com/2006/06/15/apache-tips-tricks-hide-apache-software-version/)
[*]There are some plugins and other goodies that can help keep out unwanted visitors, such as mod-defensible, e.g. [http://www.howtoforge.com/block-spammers-hackers-with-mod_defensible-on-apache2-debian-etch](http://www.howtoforge.com/block-spammers-hackers-with-mod_defensible-on-apache2-debian-etch)
[/LIST]

---

