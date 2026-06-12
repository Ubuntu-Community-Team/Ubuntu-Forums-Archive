---
title: "Newbie proxy advice, authentication against OS X LDAP"
date: 2010-06-18
forum: Server Platforms
---

### Post by dave_maltby on 2010-06-18
Hi,

Firstly thanks for reading my post. 

I've just installed Ubuntu Server for the first time with the goal as setting it up as a proxy server for our Apple computers here since I can get neither ISA of OS X Server's firewall to play properly.

So far I have the machine authenticating against our OS X OpenLDAP server and multiple NIC's setup ready to be connected to the outside world.

My question is does anyone have a preference on what proxy I should be using? 
So far my search efforts seem to of turned up Squid Proxy as a favorite among Ubuntu users but I can't seem to work out how to get it authenticating against my OpenLDAP server.

Any help would be greatly appreciated and again thanks for reading.

Dave Maltby

---

### Post by craigp84 on 2010-06-18
Hi,

Squid would be a sensible choice based on: it *will* do what you want it to and it has the biggest support community of any of the proxy server products.

For authentication via LDAP, you're probably easiest using the bundled squid_ldap_auth helper program. If you google that helper program name you'll find 1001 examples, it's a really easy copy & paste job.

Then all you need is an acl for proxy_auth REQUIRED, and then just do an http_access allow on your ACL and an http_access deny all on the next line.

Hope this helps!

---

### Post by dave_maltby on 2010-06-21
Hi Craig,

Thanks for your reply.

I've got a free day today so I'll spend the day setting up squid as you suggested.

Thank you very much for your simple & concise answer

Dave

---

### Post by dave_maltby on 2010-06-21
Ok,

So I guess I did something bad.

I installed squid with:

sudo apt-get install squid

Started setting it up and I got completely lost with myself, so decided to start again.

I did a:
sudo apt-get uninstall squid 

but that left all the botched conf files so I did a:

sudo apt-get purge squid

Now when I reinstall squid I don't get any auth helpers or any conf fine in /etc/squid

I'm guessing I've screwed the pooch on this one

any help greatly appriciated.

Dave Maltby

---

### Post by dave_maltby on 2010-06-22
Ok,

So I have this 99% working now but Squid directs clients to sites via Ip address.

For instance if a client requests [www.google.com](www.google.com) I get this in the access log:

1277231592.742    153 10.0.1.132 TCP_MISS/200 11201 GET [http://www.google.co.uk/](http://www.google.co.uk/) - DIRECT/66.102.9.99 text/html

This would be fine if I was using Squid for my firewall but from the squid server these requests are forwarded to our ISA Server and ISA is ignoring the black lists for these requests since the IP's of the sites aren't listed only their URL's.

I've specified dns_nameservers in /etc/squid/squid.conf but to no avail.

Again any help greatly appreciated.
]
Dave Maltby

---

### Post by dave_maltby on 2010-06-25
For anyone who finds this thread in the future wondering the same thing I solved this with the following in my squid.conf:

cache_peer {ISA SERVERS IP} parent {ISA SERVERS PORT} 0 no-query

I am now however struggling to get kerberos authentication working with squid.

My OS X Clients get a ticket from my OS X server absolutely fine and they use it for most services.

Currently on my ubuntu server I couldn't find the squid_kerb_auth helper so I downloaded it from [HERE]("http://sourceforge.net/projects/squidkerbauth/files/"), extracted it, did a ./configure then make then sudo make install.

It the resulting squid_kerb_auth in /usr/local/bin

After this I added the following to my squid.conf:

auth_param negotiate program /usr/local/bin/squid_kerb_auth
auth_param negotiate children 10
auth_param negotiate keep_alive on

but upon restarting the squid service I am given:
2010/06/25 13:09:22| Parsing Config File: Unknown authentication scheme 'negotiate'.

I believe I also need to make a keytab file and move that to /etc/squid and if I'm honest I'm a little lost now.

Any help would be greatly recieved

Thanks

Dave Maltby

EDIT: I should also note that currently my ubuntu server can authenticate agaiunst my OS X LDap server using kinit and can receive tickets. doing a kinit dmalt and logging in followed by a klist gives the following output:

Ticket cache: FILE:/tmp/krb5cc_1000
Default principal: [email]dmalt@CARL.APPLENET.ORG[/email]

Valid starting     Expires            Service principal
06/25/10 13:27:23  06/25/10 23:27:23  krbtgt/CARL.APPLENET.ORG@CARL.APPLENET.ORG
	renew until 06/26/10 13:27:33


Kerberos 4 ticket cache: /tmp/tkt1000
klist: You have no tickets cached

---

