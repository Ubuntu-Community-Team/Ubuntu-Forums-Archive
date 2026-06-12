---
title: "LDAP + NFS/Autofs = roaming profiles?"
date: 2010-06-20
forum: Server Platforms
---

### Post by DaveVentresca on 2010-06-20
Hey there Ubuntu land!
  I am setting up a server for a business in Portland and I have the ldap server setup on a 9.10 server  with 10.04 clients. The ldap authentication works beautifully and users can log into their desktops authenticating off the server. I have set permissions the way I want them and everything works except the ONE critical thing. The home folders on the local machines are not syncing to the respective home folders on the server. I have tried to follow the guides online to set up the NFS and Autofs, but to no avail...I'm not using kerberos cause they don't need the extra security and it's a little over my head in terms of complexity. So please if anyone has had luck setting this up on their servers - help a geek out!!!

---

### Post by DaveVentresca on 2010-06-24
Bump...please anyone?

---

### Post by bab1 on 2010-06-24
> **DaveVentresca said:**
> Hey there Ubuntu land!
  I am setting up a server for a business in Portland and I have the ldap server setup on a 9.10 server  with 10.04 clients. The ldap authentication works beautifully and users can log into their desktops authenticating off the server. I have set permissions the way I want them and everything works except the ONE critical thing. The home folders on the local machines are not syncing to the respective home folders on the server. I have tried to follow the guides online to set up the NFS and Autofs, but to no avail...I'm not using kerberos cause they don't need the extra security and it's a little over my head in terms of complexity. So please if anyone has had luck setting this up on their servers - help a geek out!!!

There is no need for "roaming profiles" in Linux/UNIX.  All you need to do is figure out how to export from the server the domain users home directory via NFS to the local host that they are  logging into.  All the users personal settings are in the respective exported home directory as hidden files (i.e. .hidden).

This means that you need to configure the domain user to receive the exported home directory (such as /export/home/username) instead of the local user (/home/username).

FYI -- Sun Microsystems developed NFS.  Most Solaris systems have a /export filesystem for NFS mounts.

---

### Post by Lucky. on 2010-06-24
I've been looking for a way to do this as well, and I keep calling it a "roaming profile" for a lack of better words.  I guess it doesn't technically roam (since everybody is directed to the same server holding their single home folder), but from an end user perspective it's the same if not better. (Roaming profiles in Windows drive me bonkers with the crazy bloat, corrupted local copies, etc.)

I'm looking into the Kerberos+NFS version though, not LDAP.

---

### Post by bab1 on 2010-06-24
> **Lucky. said:**
> I've been looking for a way to do this as well, and I keep calling it a "roaming profile" for a lack of better words.  I guess it doesn't technically roam (since everybody is directed to the same server holding their single home folder), but from an end user perspective it's the same if not better. (Roaming profiles in Windows drive me bonkers with the crazy bloat, corrupted local copies, etc.)

I'm looking into the Kerberos+NFS version though, not LDAP.

I believe you will need both in a domain situation.  LDAP to hold the users information to log in.  Then a Kerberos ticket to provide the SSO for services 

You will need to look at NFS4 with Kerberos.

---

### Post by Lucky. on 2010-06-24
That's some good stuff to know.  I'm pretty clueless about LDAP...the howtos seem more intimidating to me than the Kerberos stuff.  Just recently I got DNS & Kerberos working well!  I got the NFSv4 + Kerberos working, but I only tried it for general shares (not home folders on login).  When I get some more time, I'm pretty excited about the home folders thing.

---

