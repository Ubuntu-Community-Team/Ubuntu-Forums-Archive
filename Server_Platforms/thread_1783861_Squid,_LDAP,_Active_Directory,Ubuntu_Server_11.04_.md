---
title: "Squid, LDAP, Active Directory,Ubuntu Server 11.04 x64"
date: 2011-06-16
forum: Server Platforms
---

### Post by dguffy on 2011-06-16
First off, I'm probably somewhere between a newbie and a "sort of know some stuff" user of Ubuntu and Linux in general.  I have been using Ubuntu and FOG for several years, but once that was configured I haven't had to do much to it in the meantime.  

I am testing a squid proxy server setup as a potential replacement for Microsoft's ISA (rather than moving to TMG). My requirements for this to work in my environment are that 1. it needs to log all the user traffic and save those logs for at least 60 days, and 2. it needs cache websites.  Beyond that, I want to eventually get SquidGuard working on this box as well, but that's not essential at the moment. 

In case it is relevant my test system is a Dell Optiplex 745
4 GB of RAM
120 GB HDD
Ubuntu 11.04 Server edition x64
I have installed the Ubuntu Desktop as well
I have installed Squid...it's in a very basic configuration at the moment, but it's working and I can watch traffic if I do a tail command.
I used Centrify to join the box to my Active Directory domain.  Domain accounts can now log in and use the server.

What I need to happen is for Squid to ask for Domain Username and Password when users get on the internet.  I think I am missing some configuration somewhere in Squid to force it to ask for credentials and then query the domain. I may not have the ldap files configured or included.  I thought they were but I can't seem to find squid_ldap_auth (or squid_auth_ldap) or whatever the file should be named.  

From command line if I run:
[FONT="Courier New"] # /usr/lib/squid/squid_ldap_auth -b "dc=myomain,dc=com" -f "uid=%s" [/FONT]

The command appears to run.  No errors, but no "ok" either.  So I'm not sure what that's telling me.

From what I understand transparent proxy and username authentication are not possible.

I can supply config files if needed.  

Any and all help would be greatly appreciated.

---

### Post by craig@locationlabs.com on 2011-11-07
I'm currently evaluating the Centrify Express + Ubuntu + Squid combo.  I haven't gotten very far yet.  Did you ever get this working?

Did you try using Kerberos authentication instead of LDAP?

---

