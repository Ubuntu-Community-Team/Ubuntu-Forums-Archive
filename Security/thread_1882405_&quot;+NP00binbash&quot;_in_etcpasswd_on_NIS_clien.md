---
title: "&quot;+:*NP*:0:0:::/bin/bash&quot; in /etc/passwd on NIS client"
date: 2011-11-17
forum: Security
---

### Post by KIAaze on 2011-11-17
Hi,

What does the "+:*NP*:0:0:::/bin/bash" in the /etc/passwd file of an NIS client mean?

I found this info: [http://www.linux-nis.org/nis-howto/HOWTO/settingup_client.html](http://www.linux-nis.org/nis-howto/HOWTO/settingup_client.html) which mentions the following lines:
```
+::::::
```
and
```
+:*::::::/etc/NoShell
```

The second one apparently makes the account data of all users available, but what does "*NP*" do then?
And isn't that field supposed to be the password field? Even though the password hashes are in /etc/shadow (where I'm also wondering what the "*" and "!" mean).

Another worrying thing I read is the following from the passwd manual:
```
     A line beginning with a '+'  means  to  incorporate  entries
     from  the  naming  service source. There are three styles of
     the '+' entries in this file. A single + means to insert all
     the entries from the alternate naming service source at that
     point, while a +name means to insert the specific entry,  if
     one  exists,  from  the  naming service source. A +@netgroup
     means to insert the entries for all members of  the  network
     group netgroup from the alternate naming service. If a +name
     entry has a non-null password,  gcos,  home-dir,  or  login-
     shell  field, the value of that field overrides what is con-
     tained in the alternate naming  service.  The  uid  and  gid
     fields cannot be overridden.
```
cf [http://www.cims.nyu.edu/cgi-systems/man.cgi?section=4&topic=passwd](http://www.cims.nyu.edu/cgi-systems/man.cgi?section=4&topic=passwd)

So does that mean that an NIS client user can simply edit /etc/passwd on his machine (physical access=>root access possibility) to gain access to all other accounts on the NIS server?

So lots of questions on the password systems in the end. :)

---

### Post by Jonathan L on 2011-11-18
Hi KIAaze

> What does the "+:*NP*:0:0:::/bin/bash" in the /etc/passwd file of an NIS client mean?The values specified in the client's file override those from the server, so this means: "don't give root access by virtue of anything in NIS".

```
+          Bring in entrie(s) from the NIS server.
*NP*       But any password in the server's entry is overridden by '*NP*'
0:0        Bring in the entry for user 0:0, ie Root
blank      Bring in any real name
blank      Bring in any home directory
/bin/bash  Override any funny shell

```But because we are overriding the password to be '*NP*', they'll never log in, as this is not the hash of anything.  It's just a different habit than writing '*'.  Same for '!': it's not the hash of anything, so will never match the hash of any password the user types.  (See [man crypt(3)]("http://manpages.ubuntu.com/manpages/lucid/man3/crypt.3.html") for detail.)

> So does that mean that an NIS client user can simply edit /etc/passwd on his machine (physical access=>root access possibility) to gain access to all other accounts on the NIS server?
Up to a point.  It depends where the credentials are checked.  The one that's the real problem is NFS, as the credentials are checked on the client; mail and so on are typically checked on the server.  Of course, the NFS problem is really a problem and you might consider something else for file service of things people want to keep private.  Depends entirely on your circumstances about how physically secure your network is, whether anybody has any of their own laptops (for example) and what penalties are in place for miscreants.  And of course, perhaps they all have 775 workgroup-style permissions anyways or write their passwords on Post Its on their screen in case they need them.

Some good explanations at [Symantec]("http://www.symantec.com/connect/articles/nfs-and-nis-security")

Hope that's helpful.

Kind regards,
Jonathan.

---

### Post by KIAaze on 2011-11-18
Ah, thanks a lot. :)
I still have to read through all of this, but that already clears up the weird password "hashes".
So I suppose people put in NP for "no password". It's still a bit strange that there is no consistency in the /etc/passwd file for the "*" or "!".

---

