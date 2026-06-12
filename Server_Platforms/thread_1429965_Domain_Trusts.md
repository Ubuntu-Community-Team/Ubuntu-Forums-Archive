---
title: "Domain Trusts"
date: 2010-03-14
forum: Server Platforms
---

### Post by dudemanbubba on 2010-03-14
We setup a new remote office and I ended up setting up a basic linux file server as a pdc for that office.  Our main office is a windows 2000 ads domain.  The two offices are connected with a vpn.  I only have two users at the new location so I simply have the linux and samba usernames/passwords setup manually.

I would like to know if it is possible to setup a domain trust between the two sites so I don't have to create a username/password in the remote site for every user at the main office to access.

I did some searching but came up empty.  Thanks in advance if anyone can point me in the right direction.

Thanks.

---

### Post by koenn on 2010-03-15
looks like it's doable, 
[http://samba.anu.edu.au/samba/docs/man/Samba-HOWTO-Collection/InterdomainTrusts.html](http://samba.anu.edu.au/samba/docs/man/Samba-HOWTO-Collection/InterdomainTrusts.html)
(especially the paragraph "http://samba.anu.edu.au/samba/docs/man/Samba-HOWTO-Collection/InterdomainTrusts.html" near the bottom of the page, but you'll probably want to read the lot of it)

OTOH, wouldn't this also just work if your file server was an AD Domain Member ?  (except maybe for network latency when logging on)

---

### Post by dudemanbubba on 2010-03-17
The ubuntu server machine is a AD member of our main windows 2000 AD domain:  oci.local

We have a child domain of fm.oci.local with its own windows 2000 AD PDC.  There is a trust relationship between the two PDC's and everything works on the windows side.  For some reason, the ubuntu server is requiring a login and they aren't being authenticated.

---

### Post by dudemanbubba on 2010-03-17
When I run ***wbinfo --sequence*** I get the following:

```
administrator@ls1:~$ wbinfo --sequence
TMP : DISCONNECTED
WPB : DISCONNECTED
FP : DISCONNECTED
FM : DISCONNECTED
BUILTIN : 1268847680
LS1 : 1268847680
OCI : 4606942
```When I run ***wbinfo -u*** I get the following for the child domains in lieu of the trusted domain users:

```
OCI+fm$
OCI+fp$
OCI+tmp$
OCI+wpb$
```

---

### Post by dudemanbubba on 2010-03-18
I have read a lot of threads and pages about winbind / kerberos and can't seem to find a way to work through this.  Anyone have any help... my remote offices can not connect to any of the shares on the ubuntu server.  I may be forced to move them back to the windows box until I get this resolved. :(

---

### Post by jrssystemsnet on 2010-03-18
This isn't the answer you want, but honestly, I would advise you to NOT use Samba 3.x as a PDC.  Samba's DC functionality is limited to NT4-style domains, and frankly trying to get that connected to a modern Active Directory sounds as blecherous as... well, as blecherous as trying to keep an old NT 4.0 domain alive and related to a modern AD domain.  If not more so.

Samba 3.x will work fine as a member server in an AD domain, though.  So my recommendation would be to put an SBS server in your remote office, set it up as a DC in your AD domain and make sure it keeps a copy of the GC and of the AD DNS, then join your Samba fileserver to the single domain.

I know that's a giant pain in the rear since you then have to deal with migrating user profiles, but honestly, in the long run that's probably your best bet... unless you want to bank on Samba 4.x both achieving release status soon AND working just fine right out-of-the-box as an AD DC.

---

