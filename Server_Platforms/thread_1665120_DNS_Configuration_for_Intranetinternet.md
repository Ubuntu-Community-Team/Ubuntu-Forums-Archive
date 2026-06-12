---
title: "DNS Configuration for Intranet/internet"
date: 2011-01-11
forum: Server Platforms
---

### Post by Ed_Ziffel on 2011-01-11
Objective:  Set up a local web server for development and testing mysql/php sites over a local intranet while still having internet access from the machines on the local network.

Network set up:  Cable modem to ISP.  Newish dual band router -lacks ability to configure multiple domains :(  otherwise full featured.  Multiple machines laptop and desktop dual/tripple booted with varying installs of xp/vista/win7/ubuntu all 64bit cpus.  1 dedicated machine running 10.10 server 64 bit.  Have extra routers and desktops if needed.

Been reading the server manual -first 180 pages or so - and other tutorials on BIND and DNS, however still not clear on whether one can configure the server to resolve local only requests for test domains  and still have internet access.  Test domains would be domains that are just there so that they can be used for testing browsers and checking code results in real time and NOT to be be seen at any time by the public, as public version will be uploaded when they are ready.  Repeat these are non production versions for development and testing locally on the company intranet only.  

Given that:
1.Can one server install do that?
2.If so does the router dns need to be disabled. And what combination of Cache DNS/Primary/Seconday  would one be looking at?
3.If not what about adding a second router or server to get the job done?
 
Will worry about virtual host, ftp server and other later, just trying to focus on one issue here.  I'm good with Winblows but am only a beginning intermediate with linux.  What is needed here is to be pointed in the right direction not a blow by blow.  i.e. just want to be working on the right items.  

Thanks:D

---

### Post by Ed_Ziffel on 2011-01-12
Uh yeah okay
No sweat.  I can do this myself starting with out a clue. Been schlepping through endless Ubuntu blogs, tuts, forums, guides for over 100 hours so far and no good answers for what on the face of it seems like a practicale application for a working server.](*,)

Work arounds include just using the static ip for the server xxx.xxx.xxx.xxx/a, xxx.xxx.xxx.xxx/b... etc for all domains and create a link or shortcut depending on OS.  FYI you don't need a FQDN and it will work just fine.  And a and b while just variables here could actully be the root folders for their respective sites. Did that within the first 20 minutes of setting up the server after installing the gnome desktop.  Having never seen the file system structure for Ubuntu server before this proved to be an excellent tool.  Will take 45 minutes plus update time to wipe out the practice install and redo to go headless  which is waaaaaay less time than it would take someone to use the "Brail" method to learn the system via the command line: conceptually rediculous. Can set up the required 6 sites with frameworks in about 2 hours.  

Could just use windows with wamp.  Set up time wamp 15 minutes. 2 hours for 6 sites.

Could just test remotely on remote site, FTP slightly slower initially on set up but similar actual worktime.  

But am going to WAG or SWAG (semi wild a-- guess)it a bit and use virtual hosts as this could avoid a possible issue with uploading into production.  Who cares if the install gets porked? Only a moron :confused: jerks around with the OS when critial data is on it with no viable tested backup on hand. Fully intend to wipe and redo for real time working set anyway.  Besides redoing is good training and if you can't do it again you don't really know it.  

Out and gone. ):P

---

### Post by Ed_Ziffel on 2011-01-12
a

---

### Post by bsntech on 2011-01-12
From the sound of it, you want to host in-house web pages - and have a DNS server that will both do recursion (reach out to the Internet for DNS lookups) and also pull from your own "authoritative" dns records.

Easily done.

Install bind9 (sudo apt-get install bind9).

Recursion is enabled by default with bind9 so that is done - although it would be wise to setup "forwarders" - which are DNS servers that bind9 will go to in order to seek out Internet DNS information.  This is done in the /etc/bind/named.conf.options file.  Find the area for "forwarders" and I'd enter at least two IP addresses; one on each line with a semicolon at the end.  So you should have something like:

> forwarders {
x.x.x.x;
x.x.x.x;
};

OK - now you will need to create a DNS zone to point to a server (I guess the same one you have DNS on?) for the test sites.  You will have to come up with a domain name for this.  In this example, I will just use "developer.com" and figure that your test machines may be "dev1".  Note the "NS" record needs to be the name of your machine - then an "A" record needs to give it an IP address.

First, set a new zone in the /etc/named.conf.local file:

> zone "developer.com" {
type master;
file "/etc/bind/zones/developer.com";
};

Ensure the file is pointing to the proper location.  In the case above, I just used /etc/bind/zones/ as the folder path.  Now, make a new file in the /etc/bind/zones/ folder called "developer.com" - which will have all of your DNS records:

> @       IN      SOA     ns0.developer.com.        admin.developer.com. (
                        2011011201; Serial
                        28800; Refresh
                        36000; Retry
                        60480; Expire
                        120 ); Cache TTL

@       IN      NS      ns0.developer.com.
@       IN      A       IP.ADDRESS.OF.SERVER
dev1     IN      CNAME   ns0.developer.com.
ns0        IN      A       IP.ADDRESS.OF.SERVER


That is a simplistic configuration and then just reboot bind9.  Ensure you update IP.ADDRESS.OF.SERVER with the IP address of the server you have installed bind9 on.  The CNAME record above basically says that "dev1" is the same computer as "ns0.developer.com".  That will allow you to type in [http://dev1.developer.com](http://dev1.developer.com) and it will point to the A record of "ns0.developer.com" and then find the IP address.  No need to continuously enter the same IP over and over again.

I hope that provided some help.

Brian S.
[BsnTech Networks]("http://www.bsntech.com")

---

