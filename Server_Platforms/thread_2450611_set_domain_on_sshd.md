---
title: "set domain on sshd"
date: 2020-09-17
forum: Server Platforms
---

### Post by bardiamgtgc on 2020-09-17
ive been using a ubuntu 18.04 as my server with a hosted dns server for my domains and i would redirect domains to my server
today i decided not to pay for dns server anymore and just run one myself 
now after i completed bind9 configuration everything works fine but when i was using a hosted dns server and redirection i could use domain to ssh to my server but now i cant 
is there anyway i can set a domain for sshd?(i dont want to set a local ip to domain config file i want to access it from anywhere with domain name)

---

### Post by ahbart on 2020-09-17
It sounds like you want to set an internet domainname on your server without a domain name registrar on the internet. Is it? 
As far as I know, this is not possible.

---

### Post by TheFu on 2020-09-17
Why do you really care about the domainname?  Are you confusing DNS and Kerberos or AD or NIS or NIS+ "domains?"  These are all different, not connected at all.

There are 3 things needed for internet lookups to work.
[LIST=1]
[*]Paid domain registrar
[*]DNS provider
[*]Service/Server system
[/LIST]

Each of these are inter-connected, but it starts at the top.

In the domain registrar records, there is a DNS of record (or 2 or 3) setup.  If you didn't change this, then the root DNS servers, run by the "Elders of the Internet" don't know where to send any TLD requests to learn the IP of the system.

While you and I can run a DNS and make it public for the "Elders of the Internet" to know about, this is best left to experts or you risk being hacked.  Never put the primary DNS server on the internet. Always use a secondary that only accepts updates from the primary and from nobody else.  In 2002, my internet-facing DNS was hacked. It was an ugly day.  Since then, I've found the $20/yr a deal, paid to some experts. I was running BIND.

Of course, you don't need to have a paid domain or internet DNS if the systems will only be accessed by you. Then you just need to know the public IP for the Internet and setup a /etc/hosts file line for any domains you'd like for your clients to use.  This is easy for real computers, but gets harder for tablets and smartphones because those devices see /etc/hosts files as attack vectors used by "bad people" on the internet.  For a time, Google Android only allowed host lookups to be served by DNS, not /etc/hosts files.  Firefox has enabled DNS-over-HTTPS by default in the last few months, which points their browser somewhere other than the DNS settings in /etc/resolv.conf - a huge personal violation, IMHO.

I don't know of Android still mandates the use of DNS or not.  I've root'd all my devices and modified the settings to my preferences. For portable devices, I have both /etc/hosts and an internal DNS.  The internal DNS is provided through a pi-hole system running inside an LXD container.  The DNS in the pi-hole isn't 2-way. It only does name-to-IP lookups, not the reverse. For most end-users, and me, this is sufficient.  However, a real DNS would support reverse lookups too.  If I have a full VPN running from my clients, then my pi-hole is used as the DNS for those clients too.

Ok ... that's a bunch of words to say ....

```
123.456.78.99  my.kewl-name.org  my  www  home
```

For ssh, you can also just use the ~/.ssh/config file on each client to provide an alias to an IP.
```
host pihole2
  user ubuntu
  hostname 172.22.22.81
  port 22
host pihole2-pub
  user ubuntu
  hostname 50.123.45.45
  port 61022
```
These 2 entries point to the same machine for ssh connections.  The same ssh-key is used, but the first one only works from inside the LAN. The 2nd entry, pihole2-pub, will connect to the public WAN-IP on a specific port, which is forwarded to the internal LAN-IP of the pihole2 system.  The router does the port-translation  61022/tcp --> 22/tcp for us.  I have lots of these aliases setup for systems. My trick is to append "-pub" for any internet accessible ssh connections.

If you want this to magically work for everyone else in the world, you'll need to connect the registrar record to your DNS. Often, those records have 60+ day freezes to prevent domain snatching and it takes a few hours to a few days to unlock those domains.  A few times each year, I am notified about someone in a different country trying to take over one or more of my registrar'd domains. Thanks to the freeze, they've always failed.

Hopefully, in my stumbling around, you'll find some useful information above.

---

