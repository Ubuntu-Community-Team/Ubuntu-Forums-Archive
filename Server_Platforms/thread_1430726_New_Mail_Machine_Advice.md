---
title: "New Mail Machine Advice"
date: 2010-03-15
forum: Server Platforms
---

### Post by unicorn13 on 2010-03-15
Hi All,

A bit of advice requested:-

Current mailer setup is XP Pro running 602software Lansuite 2004. Retrieving mail from ISP pop3 boxes and sending via ISP SMTP.

WHS is not an option :evil:

What I would like is if anyone can suggest recent Howto's so I can end up with the following:-

Ubuntu 9.11 machine to retrieve email from multiple POP boxes from isp and hosting company, to send emails with a from domain of isp by isp's smtp and emails with hosting company domain by host's smtp (Password access).

Mail received from both sources to be checked antivirus/spam etc then delivered to user mail box based on recipient email address. (taking over role from Lansuite 2004).

LAMP server for testing website etc.

SAMBA - to access shares both on the ubuntu box and also my xbmc media center and 2 windows 7 machines, share access must be both ways read and write access. (So far only been able to do read/write TO xbmc, cannot access windows boxes, netbios?).

Media library approx 4TB :) so sharing needs to be quick, all machines are  Gbit CAT5.

NFS? or just leave it upto SAMBA? - opinions welcome.

Ubuntu to take over dhcp/wins/cacheing nameserver from Netgear DGN2000. DGN2000 & Ubuntu Static IP everything else DHCP, access to all machines/devices by Hostname.

Thanks in advance for reading/replying.

Andy

-------------
Mods-Sorry if misposted move if required pls, thnx.

---

### Post by KB1JWQ on 2010-03-15
> **unicorn13 said:**
> Hi All,

A bit of advice requested:-

Current mailer setup is XP Pro running 602software Lansuite 2004. Retrieving mail from ISP pop3 boxes and sending via ISP SMTP.

WHS is not an option :evil:

What I would like is if anyone can suggest recent Howto's so I can end up with the following:-

Ubuntu 9.11 machine to retrieve email from multiple POP boxes from isp and hosting company, to send emails with a from domain of isp by isp's smtp and emails with hosting company domain by host's smtp (Password access).

Mail received from both sources to be checked antivirus/spam etc then delivered to user mail box based on recipient email address. (taking over role from Lansuite 2004).

LAMP server for testing website etc.

SAMBA - to access shares both on the ubuntu box and also my xbmc media center and 2 windows 7 machines, share access must be both ways read and write access. (So far only been able to do read/write TO xbmc, cannot access windows boxes, netbios?).

Media library approx 4TB :) so sharing needs to be quick, all machines are  Gbit CAT5.

NFS? or just leave it upto SAMBA? - opinions welcome.

Ubuntu to take over dhcp/wins/cacheing nameserver from Netgear DGN2000. DGN2000 & Ubuntu Static IP everything else DHCP, access to all machines/devices by Hostname.

Thanks in advance for reading/replying.

Andy

-------------
Mods-Sorry if misposted move if required pls, thnx.

Heh, you don't want a bit of advice, you want someone to do your job from you. :-p

Each one of these points you're asking for is an entire *nix administration topic; doing this from a series of (likely conflicting) howtos is a recipe for disaster.

Take each piece on its own, one step at a time.  Rather than using tutorials, actually seek to understand what it is you're trying to do.  If that fails and "I just need something running tomorrow" is the goal, pay someone.

---

### Post by dipeshmehta on 2010-03-16
Hello,

a. You may setup your ubuntu server as guided in 'The Perfect Server' guide by Falko.  It covers most of the things you might need.
b. Then retrive your mail from ISP's server to yours by using fetchmail or getmail
c. Setup your postfix to relay outgoing mails through ISP server
d. Setup samba, dhcp server etc, Almost done.  

Google for details and howto guides, lots of stuff is there.  or come back here for the links.

Dipesh

---

### Post by ragit on 2010-03-16
get webmin or something ( easy installing modules: dhcp, samba, etc.)

sudo su
apt-get install libnet-ssleay-perl python-mysqldf python-turbogears -y
mkdir /usr/local/webmin
cd /usr/local/webmin
wget [http://switch.dl.sourceforge.net/sourceforge/webadmin/webmin-1.500.tar.gz](http://switch.dl.sourceforge.net/sourceforge/webadmin/webmin-1.500.tar.gz)
tar xzvf webmin-1.500.tar.gz
cd webmin-1.500
sh setup.sh

*follow instructions*


setting up postfix etc. is easygoing
see howto on

[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-9.10](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-9.10)

---

