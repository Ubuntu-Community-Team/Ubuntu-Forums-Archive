---
title: "Trouble with FreeRadius and Samba Active Directory"
date: 2017-04-22
forum: Server Platforms
---

### Post by ads3 on 2017-04-22
Hello, 
So, I've got a home project I need to ask for help with. Y'all are gonna be my rubber ducks for a bit here. :) Here's what I've got going on. 

I have a Samba server that I'm using to make one of those Windows-compatible Active Directories. I do still have a few Windows boxes laying around, so I wanted to tinker with getting Linux and Windows devices on the same domain. But that's actually outside the scope of this particular problem. 
I have a router/firewall running pfSense. Eventually, I want to set up a VPN server on this router. I figured, hey, since I already have an Active Directory domain, why don't I set up something that'll let me log in to the VPN I'll create someday with my existing AD credentials? I decided to use a FreeRADIUS server for future compatibility with any fancy wireless access points I may get. 
Getting FreeRADIUS installed was the easy part. Integrating it into my Active Directory is where I'm stuck. I'm hoping that some of you are a bit more experienced with this software than I am, and can point out any mistakes I'm making or misunderstandings I've accumulated along the way here. 

Here's the current situation:
[LIST]
[*]DC FQDN: dc1.example.local 
[*]DC IP Addr: 10.10.0.15 
[*]Router IP: 10.10.0.1 
[*]Test PC IP: 10.10.0.120 
[*]Domain: example.local 
[*]Username: example\testUser 
[/LIST]
Some notes about this user: I'm still pretty new to AD, so please correct any incorrect terminology I use. This user is represented by a "file" in a folder called "Users." This folder is in the root of my domain. I can view this "file" using a Windows machine, using the program called, "Active Directory Users and Computers." I can test logging in as this user by running the following command:
```
 $ ldapsearch -x -LLL -h 10.10.0.15 -D "example\testUser" -w "fakePassword" -b "dc=example,dc=local" -s sub "(objectClass=user)" givenName
```
This command succeeds. However, when I use a different command to test logging in via Radius:
```
 $ radtest "example\testUser" "fakePassword" 10.10.0.15 "coolSecret"
```
the command fails. **This tells me that there is a problem with my ldap configuration in my FreeRADIUS server.** Only thing is... where? I get the feeling there's some syntactical convention I'm not familiar with thats tripping me up, but... I'm not familiar with it, so I don't even know where to look for it. 

Let me show y'all some config files.
```

$ cat **/etc/freeradius/clients.conf**
# Allow the router to make radius requests on behalf of future vpn clients
client 10.10.0.1 {
    secret = "fakeSecret"
    shortname = fw
    nastype = other
}
# Allow desktop PC to make radius requests for testing.
client 10.10.0.120 {
    secret = "test"
    shortname = "coolSecret"
    nastype = other
}

```

```

$ cat **/etc/freeradius/modules/ldap**
ldap {
    server = "10.10.0.15"
    identity = "cn=testUser,cn=Users,dc=example,c=local"    #**Is this syntax correct?**
    #identity = "ads103\radius"                    # Or is this one?
    password = "fakePassword"
    basedn = "dc=example,dc=local"
    #filter = "(uid=%{%{Stripped-User-Name}:-%{User-Name}})"
    #filter = "(sAMAccountName=%{Stripped-User-Name:-%{User-Name}})"
    filter = "(sAMAccountName=%{%{Stripped-User-Name}:-%{User-Name}})"
    #base_filter = "(objectclass=radiusprofile)"
    ldap_connections_number = 5
    max_uses = 0
    #port = 389
    timeout = 4
    timelimit = 3
    net_timeout = 1
    tls {
        start_tls = no
    }
    dictionary_mapping = ${confdir}/ldap.attrmap
    edir_account_policy_check = no
    keepalive {
        idle = 60
        probes = 3
        interval = 3
    }
}

```

The idea is pretty simple. The active directory contains the credentials users will log in with. When a user gives their credentials to the Radius server, the Radius server will contact the LLDP server and say, "Hey, its your best buddy, the radius server!" (authentication) "Listen, whoever testUser is, they're trying to log in. They good?" Ideally, the LLDP server will then say, "Yep, they good, let 'em on in!" The Radius server will then inform the client that they're authenticated and authorized for login. So what's stopping my Radius server from communicating with my LLDP server?

If any additional information is required or desired, please don't hesitate to let me know!

---

### Post by wildmanne39 on 2017-04-22
*Thread moved to **Server Platforms**.*

---

### Post by ads3 on 2017-04-23
I just wanted to follow up with my first post and report that I was overlooking a typo in /etc/freeradius/modules/ldap. In the line that reads, "identity = "cn=testUser,cn=Users,dc=example,c=local"" the final "c" should read "dc=local"
A systemctl restart freeradius and a radtest later, I see that things still aren't working as expected. My error has changed. When I tail -f /var/log/freeradius/radius.log and try radtest, I see:
```
$ tail -f /var/log/freeradius/radius.log
Error:   [ldap] ldap_search() failed: Operations error

```
Time to head back to Google, I guess.

---

