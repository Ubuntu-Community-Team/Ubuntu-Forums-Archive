---
title: "Help with an intranet setup"
date: 2007-02-10
forum: Server Platforms
---

### Post by Uta on 2007-02-10
I have successfully installed Edgy's LAMP server running headless, and additionally,installed SSH server, phpmyAdmin,ProFTPD Server and Webmin 1.320.
Everything is working without error. 
Do I need to install, "BIND DNS Server" if this is just an intranet situation?

My plan is to use this server for in house development, not for web hosting via the Internet.
I have read so many versions of how "best" to do this that I am now completely confused.
One idea was to create separate users for each virtual website. 
ex. /home/user1/test-site1.dev/
      /home/user2/test-site2.dev/
      /home/user3/test-site3.dev/
If this is a good plan, then the question is access to these different intranet sites.
In Webmin I created 3 different virtual servers using this template and setting their Document Root accordingly and making them Name-Base servers.
The default for browser access is /var/www/
My static IP is 192.168.0.102 and [http://192.168.0.102/?](http://192.168.0.102/?) will give me my development  sites?
There is some configuration that I have not done because [http://192.168.0.102/test-site1.dev](http://192.168.0.102/test-site1.dev) gives me "Not Found"
Which config files do I need to edit to add these sites?
Was it correct to make these virtual development sites "Name-Base servers"
I thought since I had a static IP name-base would work best?
Help would be very appreciated.
Thanks!
--------------------------------------------------
I  found that if I added the name server that Apache calls my virtual server (192.168.0.102 test-site1.dev) in /etc/hosts on the computer that wants to access the development site it does go to 192.168.0.102 but not to the directory I specified in setting up the virtual server (Document root)? It goes to /var/www/   Help?

---

### Post by kidders on 2007-02-10
Hi there,

> **Uta said:**
> Do I need to install, "BIND DNS Server" if this is just an intranet situation?You don't *absolutely have to*, but if you have no internal DNS service at all, it can be difficult to run virtual hosts ... especially if your LAN has more than one PC on it. A local DNS server also gives you the opportunity to cache DNS lookups, which would speed them up.

> **Uta said:**
> I have read so many versions of how "best" to do this that I am now completely confused.A common problem when there are so many choices!

> **Uta said:**
> One idea was to create separate users for each virtual website.In my opinion (not that it's worth very much!) this would be a daft thing to do, unless of course you want an easy way to isolate your virtual hosts from eachother in such a way that user1 would not necessarily be allowed to modify user2's site. In that case, it would be quite convenient. I, on the other hand, tend to put all mine in /var, which makes them easy to manipulate as a group, and keeps them separate from my personal files.

If I were you, I would be sure to avoid writing out absolute local paths in web pages (scripts, etc.), so you could easily move your sites around, without having to worry about breaking them.

> **Uta said:**
> My static IP is 192.168.0.102 and [http://192.168.0.102/](http://192.168.0.102/)? will give me my development  sites?True. By default, apache creates virtual directories (that all start with a tilde) for each local user. The site at ~user3/test-site3.dev would probably be accessible at [http://192.168.0.102/~user3](http://192.168.0.102/~user3).

> **Uta said:**
> Was it correct to make these virtual development sites "Name-Base servers"You effectively have two options:

**The "complicated" option**
By administratively creating multiple virtual network interfaces, and binding apache to each one, you could use IP-based virtual hosting ... or even bind individual copies of apache to each interface. That way, you could run multiple radically different web server configurations on the same box. Alternatively of course, you could just install lots of network cards.

**The "easy" option**
Opting for name-based virtual hosting is far more straightforward, as it requires almost no configuration, beyond a few CNAME records on your DNS server. You couldn't use this option to host multiple SSL services though, as the SSL wrapper encrypts HTTP headers, making the *name* of the destination host unreadable.

> **Uta said:**
> I thought since I had a static IP name-base would work best?How your IP is assigned doesn't really make any difference. A properly configured DHCP server can update the DNS records for addresses it assigns, to ensure that the right CNAMEs always point to the right places.

---

### Post by Uta on 2007-02-11
Thank you for the information, ah but more possibilities--
I will install BIND DNS Server and try out your suggestions.
Cheers.

---

### Post by kidders on 2007-02-11
No problem. :-)

---

### Post by Uta on 2007-02-12
OK I have installed BIND but need to configure it.
The headless server I am running is:
firewire-server.intranet-sites.com, it has a static IP of 192.168.0.102

I have created several virtual servers, one example is "intranet-site1.com"

So now what goes where?
named.conf.local
Using this example:
# This is the zone definition. replace example.com with your domain name
zone "example.com" {
        type master;
        file "/etc/bind/zones/example.com.db";
        };

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0
zone "0.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.0.168.192.in-addr.arpa";
};

Do I replace "example.com" with my "firewire-server.intranet-sites.com" ?

And in terms of reverse lookup since I have a static IP of 192.168.0.102 what would I put?

Thanks, er another thought is,should I just use Dnsmasq since I am only doing an intranet setup?

---

### Post by kidders on 2007-02-12
There's a fairly good HOWTO here ... [http://www.ubuntuforums.org/showthread.php?t=236093](http://www.ubuntuforums.org/showthread.php?t=236093). Have you seen it? By default, Ubuntu's Bind configuration is slightly odd, so using a Ubuntu HOWTO is a good idea.

> **Uta said:**
> I have created several virtual servers, one example is "intranet-site1.com"You can give virtual web servers CNAME records in your DNS database. That way, any machine on your network that is configured to use your DNS server knows they're not "real", and will send packets where they're supposed to go.

> **Uta said:**
> should I just use Dnsmasq since I am only doing an intranet setup?That all depends on your personal requirements, really. Masquerading allows computers on your network to communicate with machines outside your LAN through your Ubuntu box. The masquerading PC forwards incoming requests destined for the outside world, and keeps track of what's what so, when a response comes back, it knows who to send it to.

If you're going to the trouble of installing a DNS service, there is one more thing you might be interested in. Assuming you've set up a DHCP server (and have configured it to tell clients to use your new DNS service!), you can have DHCP update the DNS records of machines whose addresses it allocates. That way, you'll always be able to refer to your computers by name.

---

### Post by Uta on 2007-02-12
Again thanks for the quick response but... the how to you referred me to is the one I am asking the question about. Do I replace "example.com" with the name of my host server's name, in my case "fire-server.intranet-sites.com" and in terms of the reverse lookup and my static IP for this server box being 192.168.0.102 would it be the same as the example 0.168.192 ?

Also the dnsmasq option if I understand correctly would be what all the computers in my lan would have to go through to access the outside world instead of how they now, just go through the main router. If that is what you mean then, no I don't want my development server to be routing outside Internet requests.

Also does this mean my ISP's server or my router's IP?

forwarders {
      # Replace the address below with the address of your provider's DNS server
      68.87.77.130;


Thanks again--

---

### Post by kidders on 2007-02-12
> **Uta said:**
> Again thanks for the quick response but... the how to you referred me to is the one I am asking the question about.Lol sorry... I should've been paying more attiontion. :lolflag: @ me!

> **Uta said:**
> Do I replace "example.com" with the name of my host server's name, in my case "fire-server.intranet-sites.com""example.com" is your _domain_ name.

> **Uta said:**
> in terms of the reverse lookup and my static IP for this server box being 192.168.0.102 would it be the same as the example 0.168.192 ?Yes. That seems right.

> **Uta said:**
> Also the dnsmasq option if I understand correctly would be what all the computers in my lan would have to go through to access the outside world instead of how they now, just go through the main router.Yep, that's it. Using your Ubuntu box as a router gives you fabulous control over advanced network behaviour, but many people don't have any need for it. It seems like your router hardware is handling this for you though.

> **Uta said:**
> forwarders {
      # Replace the address below with the address of your provider's DNS server
      68.87.77.130;
This is a list of DNS servers your DNS server will forward queries to. Your ISP's DNS server addresses are probably the best (fastest) ones to use. Note that the order you specify them in *is* significant. You can also choose which order the forwarding occurs in (ie before or after consulting your own DNS database), depending on your needs. You need this setting to be able to resolve addresses that aren't in your local DNS database.

---

### Post by Uta on 2007-02-12
Boy am I  glad you're out there somewhere, (and this great forum)answering my 'questions'
So this is where I am, I install BIND, followed the how-to and I was hoping the results would be>

all the computers on my lan would be able to find all the virtual servers I created on my host server
(the domain name being  firewire-server.intranet-sites.com)

After I followed the steps and restarted the server, did the command 
"dig firewire-server.intranet-sites.com" everything came back OK
But... moving to a different computer and typing in one of my virtual servers name
it couldn't find it. Ugh!

Ok where and in what file do I need to add all the names of my virtual servers ( in BIND land somewhere that is?)
The point of me setting up BIND was so I did not have to edit everyone's resolv.conf file.

This is possible isn't it?

Thanks again--

---

### Post by kidders on 2007-02-12
> **Uta said:**
> Boy am I  glad you're out there somewhere, (and this great forum)answering my 'questions'Hehe.

> **Uta said:**
> But... moving to a different computer and typing in one of my virtual servers name it couldn't find it.Hmm. If it works on some machines and not others, you've probably hotwired them somehow, perhaps by doctoring /etc/hosts. You should undo any tweaks like that.

> **Uta said:**
> Ok where and in what file do I need to add all the names of my virtual servers ( in BIND land somewhere that is?)They go with the rest of your hosts in your zone definition file. You'll need to restart bind after making changes.

> **Uta said:**
> The point of me setting up BIND was so I did not have to edit everyone's resolv.conf file.Not exactly. That file controls basic information about your network environment, such as the default domain name. This file needs to be correctly configured for your network to work properly, regardless of where your DNS service is.

If your network's IP addresses are DHCP-assigned, that file will be overwritten on a regular basis anyhow. If you find yourself having to alter it, you should really configure your DHCP server to send the correct details to your computers. Once your DNS service is operating, any computer configured to use it will be able to resolve any addresses in your zone definition files. Often, the DNS server addresses being used by a Linux box are listed in the /etc/resolv.conf file you mentioned.

---

### Post by Uta on 2007-02-12
"zone definition file"
is the real name for that "named.conf.local"

and again thanks--

---

### Post by kidders on 2007-02-12
No, not usually. It's the one that probably starts something like **mydomain.com. IN SOA ns.mydomain.com** that lists the contents of a zone (network).

---

### Post by Uta on 2007-02-12
OK, is this the file I am suppose to put the additional virtual hosts in:
-------------------------------------------------------------------------------

// replace example.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
firewire-server.intranet-sites.com.	IN	SOA	ns1.firewire-server.intranet-sites.com. admin.firewire-server.intranet-sites.com. (
							
												        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400 
)

// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// example.com = domain name
firewire-server.intranet-sites.com.      IN      NS              ns1.firewire-server.intranet-sites.com.
firewire-server.intranet-sites.com.      IN      MX     10       mta.firewire-server.intranet-sites.com.

// Replace the IP address with the right IP addresses.
www              IN      A       192.168.0.102
mta              IN      A       192.168.0.102
ns1              IN      A       192.168.0.102


-----------------------------------------------------------
192.168.0.102 is the static IP of the server, is the above the right place to put that?

I'm not giving up but I am getting back to my confused-state of mind--

---

### Post by kidders on 2007-02-12
Yep that seems perfect. I would add something like...
```
virtualhost1 CNAME www
virtualhost2 CNAME www
virtualhost3 CNAME www
```

**Edit:** DNS *is* a bit overcomplicated, isn't it!

---

### Post by Uta on 2007-02-13
OK, new day another day of hopeful configuration. 
When I restart my bind9, I get this:
*Stopping domain name service...
rndc: connect failed; connection refused
* Starting domain name service...

rndc? Something else I need to configure?

I'm not 100% sure BIND is running or working, when I "dig" [www.google.com](www.google.com), I get answered back with info but when I "dig" my server box I get this:
QUESTION SECTION:
:firewire-server.intranet-sites.com. IN A

;; AUTHORITY SECTION:
com.  900 IN SOA a.gtld-servers.net. nstld.verign.grs.com 1171382527 1800 900 604800 900
;; Query time: 53 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Tue Feb 13 10:02:39 2007
;; MSG SIZE rcvd: 125

Remember the router's address is 192.168.0.1 and my server's static address is 192.168.0.102

Did I fluff somewhere?Yikes.

Also according to my Webmin server status "BIND is down"
Me thinks this error has something to do with it's down-ness
"rndc: connect failed; connection refused"

OK I got BIND running but with some weird issues, here is the terminal output:

root@firewire-server:~# named -g -p 53
13-Feb-2007 14:37:49.524 starting BIND 9.3.2 -g -p 53
13-Feb-2007 14:37:49.524 found 1 CPU, using 1 worker thread
13-Feb-2007 14:37:49.530 loading configuration from '/etc/bind/named.conf'
13-Feb-2007 14:37:49.532 listening on IPv4 interface lo, 127.0.0.1#53
13-Feb-2007 14:37:49.533 binding TCP socket: address in use
13-Feb-2007 14:37:49.533 listening on IPv4 interface eth0, 192.168.0.102#53
13-Feb-2007 14:37:49.534 binding TCP socket: address in use
13-Feb-2007 14:37:49.539 /etc/bind/named.conf:70: couldn't add command channel 127.0.0.1#953: address in use
13-Feb-2007 14:37:49.539 ignoring config file logging statement due to -g option
13-Feb-2007 14:37:49.541 zone 0.in-addr.arpa/IN: loaded serial 1
13-Feb-2007 14:37:49.543 zone 127.in-addr.arpa/IN: loaded serial 1
13-Feb-2007 14:37:49.543 /etc/bind/zones/rev.0.168.192.in-addr.arpa:1: unknown RR type 'example.com'
13-Feb-2007 14:37:49.543 zone 0.168.192.in-addr.arpa/IN: loading master file /etc/bind/zones/rev.0.168.192.in-addr.arpa: unknown class/type
13-Feb-2007 14:37:49.544 zone 255.in-addr.arpa/IN: loaded serial 1
13-Feb-2007 14:37:49.545 /etc/bind/zones/firewire-server.intranet-sites.com.db:1: unknown RR type 'replace'
13-Feb-2007 14:37:49.545 zone firewire-server.intranet-sites.com/IN: loading master file /etc/bind/zones/firewire-server.intranet-sites.com.db: unknown class/type
13-Feb-2007 14:37:49.546 zone localhost/IN: loaded serial 1
13-Feb-2007 14:37:49.547 running

Now interms of this:" /etc/bind/zones/rev.0.168.192.in-addr.arpa:1: unknown RR type 'example.com'"
I looked in the file and any reference to example.com has a ## in front of it? Huh?
Where else to look?


 

As always-- Thanks!

---

### Post by kidders on 2007-02-14
Sorry I took so long replying to you...

Two issues:

> **Uta said:**
> 13-Feb-2007 14:37:49.532 listening on IPv4 interface lo, 127.0.0.1#53
13-Feb-2007 14:37:49.533 binding TCP socket: address in useYou need to be careful you haven't got multiple servers running simultaneously.

> **Uta said:**
> 13-Feb-2007 14:37:49.545 /etc/bind/zones/firewire-server.intranet-sites.com.db:1: unknown RR type 'replace'I'd say you have some explanatory stuff (comments, etc.) in your zone definitions that needs to be removed. Also, afaik you shouldn't leave any blank lines in zone files either.

Also ...

> **Uta said:**
> Also according to my Webmin server status "BIND is down"That may be correct, but having said that, I wouldn't necessarily believe anything Webmin tells me. Hehe.

> **Uta said:**
> root@firewire-server:~# named -g -p 53Be cautious, when you do this, that bind doesn't create files as root that it won't be able to access later, when it runs under its own account.

---

### Post by Uta on 2007-02-14
Thank you for your reply--
I need to backtrack a little, excuse my fuzziness:

here is my file named.conf.options
-----------------------------------------------------
options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you might need to uncomment the query-source
	// directive below.  Previous versions of BIND always asked
	// questions using port 53, but BIND 8.1 and later use an unprivileged
	// port by default.

	// query-source address * port 53;

	// If your ISP provided one or more IP addresses for stable 
	// nameservers, you probably want to use them as forwarders.  
	// Uncomment the following block, and insert the addresses replacing 
	// the all-0's placeholder.

	// forwarders {
	// 	0.0.0.0;
	// };

	auth-nxdomain no;    # conform to RFC1035

	// By default, name servers should only perform recursive domain
	// lookups for their direct clients.  If recursion is left open
	// to the entire Internet, your name server could be used to
	// perform distributed denial of service attacks against other
	// innocent computers.  For more information on DDoS recursion:
	// [http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-0987](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-0987)

	allow-recursion { localnets; };

	// If you have DNS clients on other subnets outside of your
	// server's "localnets", you can explicitly add their networks
	// without opening up your server to the Internet at large:
	// allow-recursion { localnets; 192.168.0.0/24; };

	// If your name server is only listening on 127.0.0.1, consider:
	// allow-recursion { 127.0.0.1; };

};

forwarders {
      // Replace the address below with the address of your provider's DNS server
      68.87.77.130;
};

----------------------------------------------------------------------------------------------------
BIND, o,mysterios bind won't start this morning and here's the reason why:

/etc/bind/named.conf.options;42 unknown option 'forwarders'

Ok, what's with forwarders not being recognized here?

Thanks!

---

### Post by kidders on 2007-02-14
If I rewrite this a little for you, you'll see...

```
options {
	directory "/var/cache/bind";
	auth-nxdomain no;
	allow-recursion { localnets; };
};

forwarders { 68.87.77.130; };
```

It *should* be...

```
options {
	directory "/var/cache/bind";
	auth-nxdomain no;
	allow-recursion { localnets; };
	forwarders { 68.87.77.130; };
};
```

As I'm sure you've noticed with things like Apache, Ubuntu loves subdividing config files into "manageable" little chunks. Trying to find problems when things go wrong would drive you to drink though!

---

### Post by Uta on 2007-02-14
Thanks that worked!
OK, so the mysterios BIND is up and running--

So the question remains, what does this give me in terms of my hopeful intranet?
If I want all 8 pc-s on my lan to query mister BIND (local dns info center) but also being able to query the outside Internet...
here's where I backtrack--
do I on each lan pc, edit their resolv.conf file with 2 dns servers (one being BIND and one being my local ISP's dns)? or is it redundant in terms of listing the ISP's dns server?
confused yet, I sure am.

Simply put, I want all lan pc to query the intranet and Internet.

Thanks--

---

### Post by kidders on 2007-02-14
> **Uta said:**
> Thanks that worked!Yay! :-)

> **Uta said:**
> So the question remains, what does this give me in terms of my hopeful intranet?Basically, that gives you control over your LAN's DNS service. You can now use things like DHCP without having to worry about how dynamically assigned addresses will affect your servers, and avoid having to tinker with 8 computers' config files ever again, any time you add new virtual servers in Apache, etc.

> **Uta said:**
> If I want all 8 pc-s on my lan to query mister BIND (local dns info center) but also being able to query the outside Internet...Since you've configured your own DNS server with a "forwarder", it will hand off (I think the term is "delegate") any requests it doesn't know how to handle. Your ISP's DNS server does exactly the same thing for requests *it* can't deal with, so in effect, you've plugged yourself into the worldwide DNS system ... the difference now is that your own service is the first port of call. If I were you, I would make the following alterations:

[LIST]
[*]Add a second forwarder to your DNS server configuration. Most ISPs provide their customers with two (a first & second preference), in case their primary service gets into difficulty. (The DNS system is quite delicate!)
[*]Configure your computers to use only one DNS service ... *your* one. If you're using DHCP, make sure the server is sending the right address to its clients, and making no reference to your ISP's DNS servers. Remeber to refer to DNS servers by IP, not by name.
[*]Remove any addresses you may have put in /etc/hosts files, that may, in time, conflict with DNS.
[/LIST]

> **Uta said:**
> do I on each lan pc, edit their resolv.conf fileOnly if you're not using DHCP. If you are, those changes will be lost the next time each computer's DHCP client refreshes its network information. My network, for instance, has centralised DNS/DHCP, so I can make configuration changes in one place, and let them propagate throughout the network by themselves.

> **Uta said:**
> confused yet, I sure am.Hopefully, all will become clear as you fine tune your network. DNS plays useful roles in DHCP-driven LANs, Windows filesharing, virus protection, etc. Over time, you will hopefully notice more and more ways having a proper DNS service makes life easy! Hopefully!

---

### Post by Uta on 2007-02-14
good response-- much gratitude here.
OK let's speak of DHCP
What was installed with my LAMP installation was dhcp3
are you suggesting installing something additional? 
plain old, "dhcp"

sorry for all these endless questions, I'm sure there will be a happy intranet ending here somewhere.

Alsooooooooooo--
if I were to add the 2nd ISP's address can I just add a "space" between the first entry?

options {
	directory "/var/cache/bind";
	auth-nxdomain no;
	allow-recursion { localnets; };
	forwarders { 68.87.77.130; 68.87.72.130; };
};

---

### Post by kidders on 2007-02-14
> **Uta said:**
> sorry for all these endless questionsLol don't worry, that's what the forum's for! I'll help as best I can.

> **Uta said:**
> What was installed with my LAMP installation was dhcp3You're probably referring to the DHCP *client* software here. Linux (naturally) also has a few DHCP *server* implementations ... assuming you even want one.

Without knowing what you've got exactly, it's hard to know where to pitch a description of DHCP, but let's suppose you have a fairly standard domestic DSL modem/router. Most users of devices like that tend to leave network management entirely in its hands, which is perfectly fine ... until you decide you want to do something it's not able to handle. One example might be DNS. My DSL router for instance has a _crappy_ DNS service, that won't resolve the names of machines on my network. The DHCP server is worse, and won't allow me to configure pseudo-static addressing, the way I want it. So I disabled them both, and gave my Linux box control over the whole LAN.

With DHCP, you can have your machines write their own resolv.conf files, eliminating the need to manually configure them for network access. In OSs like OSX and Windows, this is particularly nice, as network connections can be set up in 5 seconds flat. DHCP configured machines are, in theory, also immune to changes in DNS server address, their own IP addresses or those of other machines, default route, etc., and can also be sent information about Windows filesharing, date/time synchronisation, and so on.

One possible configuration (and *you* may, of course, not want this) would be to run DNS & DHCP off an actual computer, rather than a DSL gizmo. On my home network, for instance:

[LIST]
[*]Any computer I preauthorise can connect to the LAN automagically with no prior configuration.
[*]DNS records are kept up to date by the DHCP server, as computers come and go.
[*]I can alter hostnames, virtual websites, etc. from a single file (my zone definition).
[*]Additionally (and this has nothing to do with your question), everything connects to the internet via my Linux box, so I have very fine control over the firewall, odd things like UPnP, proxying, and so on.
[/LIST]

Most people have absolutely zero interest in doing anything weird or "special" with their networks, so the trouble they'd have to go to, to set something like that up, would outweight any practical benefit they'd gain from it. How about you?

If you're like me, and can't handle not being in control of *everything* that happens on your LAN, then I'd be happy to walk you through DHCP. On the other hand, if you would have no use for the kind of advanced control running your own server would give you, I would definitely recommend a less involved alternative.

---

### Post by Uta on 2007-02-14
Hardware vs Software

If I understand correctly, my router/cable modem (which is AirPlus XtremeG by D-Link) is my DHCP server; that explains why, if on any pc (all macs and linux boxes here) I change the routers IP (192.168.0.1) to the server's IP for nameserver, I'm without a connect. (I haven't set up dhcp on the server box)?
As I mentioned when I installed the server, it's own dhcp3 was installed but you are speaking of installing a "DHCP Server" a very different animal.

Am I tracking ok on this?
++++++++++++++++++++++++++++
OK installed DHCP server.
Here's the options?
help please?
++++++++++++++++++++++++++++

Subnets and Shared Networks
No subnets or shared networks have been defined.

Add a new subnet. | Add a new shared network.
Hosts and Host Groups
No hosts or groups have been defined.

Add a new host. | Add a new host group.
DNS-zones
No DNS zones have been defined yet.

Add a new DNS zone.  
	Edit DHCP client options that apply to all subnets, shared networks, hosts and groups
	Edit TSIG-keys (used for authenticating updates to DNS servers)
	Edit configfile in texteditor (caution!)
	Set the network interfaces that the DHCP server listens on when started.
	List leases currently issued by this DHCP server for dynamically assigned IP addresses.
	Click this button to start the DHCP server on your system, using the current configuration.

---

### Post by kidders on 2007-02-14
> **Uta said:**
> If I understand correctly, my router/cable modem (which is AirPlus XtremeG by D-Link) is my DHCP serverSounds reasonable. There's no reason to change that unless you particularly *want* to. In DNS configuration terms, your default route setting should remain unchanged ... it's the advertised DNS server setting you should alter. (I *think* that's what you were describing.)

> **Uta said:**
> As I mentioned when I installed the server, it's own dhcp3 was installed but you are speaking of installing a "DHCP Server" a very different animal.Yes, that's right. If you're happy with your router's DHCP server, I wouldn't really recommend replacing it with a software one.

If you *do* want to give it a try, adding a new "subnet" is probably step 1. I strongly suggest editing the config file directly ... it's much less awkward & time-consuming.

Here's an example:
```
server-identifier server.mydomain.com;
ddns-update-style interim;
authoritative;
log-facility local7;

ddns-domainname "mydomain.com";
ddns-rev-domainname "5.168.192.in-addr.arpa";
use-host-decl-names off;
ddns-updates on;
deny unknown-clients;
allow client-updates;
update-static-leases on;

include "/etc/ddns.key";

subnet 192.168.5.0 netmask 255.255.255.0 {
        option domain-name "mydomain.com";
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.5.255;
        option domain-name-servers 192.168.5.100;
        option routers 192.168.5.100;
        option netbios-name-servers 192.168.5.100;
        option netbios-dd-server 192.168.5.100;
        option netbios-node-type 8;

        one-lease-per-client on;
        default-lease-time 3600;
        max-lease-time 3600;

        zone mydomain.com. {
                key ddns-key;
                primary 127.0.0.1;
        }

        zone 5.168.192.in-addr.arpa. {
                key ddns-key;
                primary 127.0.0.1;
        }

        host example-host {
                ddns-hostname "example-host";
                hardware ethernet 01:1d:13:3b:39:1c;
                fixed-address 192.168.5.110;
        }
}
```

Given the proper changes to Bind's configuration, something like this would:

[LIST]
[*]Perform appropriate DNS updates automatically.
[*]Inform clients about basic network configuration.
[*]Hardwire the machine called "example-host", so it has a fixed IP ... essentially achieving the same effect as a static configuration, but in a "configurationless" way, with centralised control.
[/LIST]

That's just one (partial) example of the sort of thing you could do with a DHCP server. There are, of course, many other ways to arrange your LAN.

---

### Post by Uta on 2007-02-14
Again, thank you.

---

### Post by Uta on 2007-02-15
New day, new questions.
I found out this morning that my BIND is indeed working in terms of dns because my lan pc-s could not connect to the Internet. Why? Because I shutdown my server last night. OOPS.
So after turning on my server, they still could not connect. Why? Because BIND doesn't automatically start. Why I don't know because in "Webmin" in the Bootup and Shutdown section it says ""yes" to start at boot... but no it doesn't--  I have to line command it to start or within Webmin hit the start button in the BIND section.
#1 question how to get BIND to start with server boot?

thank you--

---

### Post by kidders on 2007-02-15
Odd! I would have expected **/etc/init.d/<servicename> start** to be enough. I almost never use Webmin, so I'm not sure how it behaves with bind & ubuntu.

It's good to see your service is working though. Hopefully, in addition to being able to do local lookups, your remote lookups should speed up a little bit, now that something's caching them.

---

### Post by Uta on 2007-02-15
Hello.
I think it has something to do with the fact I have a chrooted server,"-u bind -t /var/lib/named" and my "named" has been moved to /var/lib/named
Starting BIND manually it knows where "named" is but not the system boot, where do I need my symbolic link?
In the BIND script it states if it can't find "named" not to start. in the same script "I" know something needs to be changed or is it just a symbolic link. (changing the bind9 script seems like a bad idea)
The script in mention
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

#!/bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin

# for a chrooted server: "-u bind -t /var/lib/named"
# Don't modify this line, change or create /etc/default/bind9.
OPTIONS=""
RESOLVCONF=yes

test -f /etc/default/bind9 && . /etc/default/bind9

test -x /usr/sbin/rndc || exit 0

. /lib/lsb/init-functions
DISTRO=$(lsb_release -is 2>/dev/null || echo Debian)

case "$1" in
    start)
	log_daemon_msg "Starting domain name service..."

	modprobe capability >/dev/null 2>&1 || true

	# dirs under /var/run can go away on reboots.
	mkdir -p /var/run/bind/run
	chmod 775 /var/run/bind/run
	chown root:bind /var/run/bind/run >/dev/null 2>&1 || true

	if [ ! -x /usr/sbin/named ]; then
	    log_action_msg "named binary missing - not starting"
	    log_end_msg 1
	    exit 1
	fi
	if start-stop-daemon --start --quiet --exec /usr/sbin/named \
		--pidfile /var/run/bind/run/named.pid -- $OPTIONS; then
	    if [ "X$RESOLVCONF" != "Xno" ] && [ -x /sbin/resolvconf ] ; then
		echo "nameserver 127.0.0.1" | /sbin/resolvconf -a lo.named
	    fi
	fi
	log_end_msg 0
    ;;

    stop)
	log_daemon_msg "Stopping domain name service..."
	if [ "X$RESOLVCONF" != "Xno" ] && [ -x /sbin/resolvconf ] ; then
	    /sbin/resolvconf -d lo.named
	fi
	/usr/sbin/rndc stop
	log_end_msg 0	
    ;;

    reload|force-reload)
	log_daemon_msg "Reloading domain name service..."
	/usr/sbin/rndc reload
	log_end_msg 0
    ;;

    restart)
	$0 stop
	sleep 2
	$0 start
    ;;
    
    *)
	log_action_msg "Usage: /etc/init.d/bind9 {start|stop|reload|restart|force-reload}"
	exit 1
    ;;
esac

exit 0

++++++++++++++++++++++++++++++++++++++++++++++++
also note that /etc/default/bind9
DOES have this in it:

OPTIONS="-u bind -t /var/lib/named"
# Set RESOLVCONF=no to not run resolvconf
RESOLVCONF=yes

++++++++++++++++++++++++++++++++++++++++++++++++
Here's what the system had to say this morning:

Feb 15 07:38:39 firewire-server named[3501]: loading configuration from '/etc/bind/named.conf'
Feb 15 07:38:39 firewire-server named[3501]: /etc/bind/named.conf.options:2: change directory to '/var/cache/bind' failed: file not found
Feb 15 07:38:39 firewire-server named[3501]: /etc/bind/named.conf.options:2: parsing failed
++++++++++++++++++++++++++++++++++++++++++++++++
OK I put a symbolic link in /var/cache/bind for /etc/bind/named.conf.options and the system started without error, bind said it started but it didn't till I again manually started it. Pls. note that bind9 is in /etc/init.d and /etc/default
Why won't it start on it's own?

---

### Post by kidders on 2007-02-15
[COLOR="Silver"]> **Uta said:**
> Feb 15 07:38:39 firewire-server named[3501]: /etc/bind/named.conf.options:2: change directory to '/var/cache/bind' failed: file not foundI wonder if /var/cache/bind is the absolute path from within the chroot-ed environment. I don't have bind installed on Ubuntu at the moment, so I can't be *completely* sure what's going on here, but that strikes me as a possibility.

> **Uta said:**
> OK I put a symbolic link in /var/cache/bind for /etc/bind/named.conf.optionsI'm not sure why that would change anything. Am I confused? :confused: The problem appears to have to do with finding something referenced in line 2 of that file.
[/COLOR]

Hmm... this is quite confusing. What did you do to have bind run chrooted?

---

### Post by Uta on 2007-02-15
I did use these "instructions"
+++++++++++++++++++
 For security reasons we want to run BIND chrooted so we have to do the following steps:

/etc/init.d/bind9 stop

Edit the file /etc/default/bind9 so that the daemon will run as the unprivileged user bind, chrooted to /var/lib/named. Modify the line: OPTIONS=" -u bind" so that it reads OPTIONS="-u bind -t /var/lib/named":

vi /etc/default/bind9

OPTIONS="-u bind -t /var/lib/named"
# Set RESOLVCONF=no to not run resolvconf
RESOLVCONF=yes

Create the necessary directories under /var/lib:

mkdir -p /var/lib/named/etc
mkdir /var/lib/named/dev
mkdir -p /var/lib/named/var/cache/bind
mkdir -p /var/lib/named/var/run/bind/run

Then move the config directory from /etc to /var/lib/named/etc:

mv /etc/bind /var/lib/named/etc

Create a symlink to the new config directory from the old location (to avoid problems when bind is upgraded in the future):

ln -s /var/lib/named/etc/bind /etc/bind

Make null and random devices, and fix permissions of the directories:

mknod /var/lib/named/dev/null c 1 3
mknod /var/lib/named/dev/random c 1 8
chmod 666 /var/lib/named/dev/null /var/lib/named/dev/random
chown -R bind:bind /var/lib/named/var/*
chown -R bind:bind /var/lib/named/etc/bind

We need to modify the startup script /etc/init.d/sysklogd of sysklogd so that we can still get important messages logged to the system logs. Modify the line: SYSLOGD="-u syslog" so that it reads: SYSLOGD="-u syslog -a /var/lib/named/dev/log":

vi /etc/init.d/sysklogd

[...]
SYSLOGD="-u syslog -a /var/lib/named/dev/log"
[...]

Restart the logging daemon:

/etc/init.d/sysklogd restart

Start up BIND, and check /var/log/syslog for errors:

/etc/init.d/bind9 start

???

---

### Post by kidders on 2007-02-15
Ugh! Tbh, I wouldn't have bothered.

Would you be crazy enough to trust me to let me take a look at what you've done without garbaging your system or dumping you up to your neck in spyware? I'd love to be able to actually *see* what's going on.

---

### Post by Uta on 2007-02-15
how would that be done?
Do you mean open my development intranet server to be accessed from the Internet.
Maybe you should send a private message with this plan?
Thanks

---

### Post by kidders on 2007-02-15
> **Uta said:**
> how would that be done?
You'd have to do the unthinkable, and temporarily give me root access over SSH. In your position, I certainly wouldn't let a stranger into my Ubuntu box as root ... I only suggest it because I *may* be able to make your problem go away quite quickly, and I'm guessing your patience with it is probably wearing pretty thin!

---

### Post by Uta on 2007-02-15
Check your private message box.

Also I would be really interested in starting from "zero" to get this right once I understand what went wrong. Why did you think the chrooted idea wasn't so great?

---

### Post by kidders on 2007-02-15
> **Uta said:**
> Check your private message box.Done. :-) Replied.

> **Uta said:**
> Why did you think the chrooted idea wasn't so great?It's actually a very smart idea in general terms, but it's an extra complication that isn't really necessary on a private LAN. Afaik the idea is to protect your box from flaws in the DNS protocol or Bind's implementation of it.

---

### Post by kidders on 2007-02-15
Just in case anyone else reads this thread and wonders what just happened...

```
root@firewire-server:/tmp# cd /var/lib/named/
root@firewire-server:/var/lib/named/var# mkdir cache
root@firewire-server:/var/lib/named/var# mkdir !$/bind
root@firewire-server:/var/lib/named/var# cd ../..
root@firewire-server:/var/lib# chown -R bind named/
root@firewire-server:/var/lib# /etc/init.d/bind9 start
 * Starting domain name service...
   ...done.
root@firewire-server:/var/lib# ps aux|grep nam
bind      4220  0.2  0.1  31440  2784 ?        Ssl  13:54   0:00 /usr/sbin/named -u bind -t /var/lib/named
root      4226  0.0  0.0   3000   820 pts/2    R+   13:54   0:00 grep nam

[**Modified /etc/resolv.conf to use the correct DNS and default domain name**]

root@firewire-server:~# ping www
PING www.firewire-server.intranet-sites.com (192.168.0.102) 56(84) bytes of data.
64 bytes from firewire-server.intranet-sites.com (192.168.0.102): icmp_seq=1 ttl=64 time=0.033 ms
64 bytes from firewire-server.intranet-sites.com (192.168.0.102): icmp_seq=2 ttl=64 time=0.021 ms
64 bytes from firewire-server.intranet-sites.com (192.168.0.102): icmp_seq=3 ttl=64 time=0.029 ms

--- www.firewire-server.intranet-sites.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.021/0.027/0.033/0.007 ms
root@firewire-server:~# ping www.google.com
PING www.l.google.com (72.14.203.99) 56(84) bytes of data.
64 bytes from ro-in-f99.google.com (72.14.203.99): icmp_seq=1 ttl=241 time=37.5 ms
64 bytes from ro-in-f99.google.com (72.14.203.99): icmp_seq=2 ttl=241 time=32.8 ms

--- www.l.google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 32.805/35.165/37.525/2.360 ms
root@firewire-server:~# logout
```

Success. :-) The private DNS service is alive and kicking. Now, any linux box on your LAN with the same /etc/resolv.conf will behave identically, allowing you to make arbitrary modifications to the names of your PCs & virtual hosts from a central location.

---

### Post by Uta on 2007-02-15
Thank you for your IT help it was very generous and it WORKED!

---

### Post by kidders on 2007-02-15
No trouble. :-)

---

