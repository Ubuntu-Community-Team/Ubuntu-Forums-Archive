---
title: "Active Directory and LDAP"
date: 2009-09-23
forum: Server Platforms
---

### Post by luksol on 2009-09-23
Ok, I am quite new system admin, so I don't know if my question sounds silly or not :)

I want to copy Active Directory from Microsoft Windows server to LDAP in order to be able to access this data from multiple Linux clients.

Can anyone advise me on that?

---

### Post by rickyjones on 2009-09-23
> **luksol said:**
> Ok, I am quite new system admin, so I don't know if my question sounds silly or not :)

I want to copy Active Directory from Microsoft Windows server to LDAP in order to be able to access this data from multiple Linux clients.

Can anyone advise me on that?

What is your end goal? Are you just looking to copy the data to an OpenLDAP server so that you can query it? Because you can query against the Active Directory LDAP using any standards-based LDAP tool already.

More information, I think, is necessary :)

Thanks,
Richard

---

### Post by luksol on 2009-09-23
thanks rickyjones for quick reply.

To clarify things:
- yes I want to query AD to get information stored in it.
- server AD sits on is windows 2003
- I am using Ubuntu and would like to have access to it (possibly via some GUI tool)

---

### Post by rickyjones on 2009-09-23
> **luksol said:**
> thanks rickyjones for quick reply.

To clarify things:
- yes I want to query AD to get information stored in it.
- server AD sits on is windows 2003
- I am using Ubuntu and would like to have access to it (possibly via some GUI tool)

Any standard LDAP browser software should be able to query your AD server then - I do it at work all the time. Modifying it will require authentication and most LDAP software offers this option.

Pulling data from AD is a pretty standard operation. Microsoft even provides an LDAP Only implementation (ADAM) so you can spread the LDAP load around.

I hope this helps. :)

-Richard

---

### Post by openfly on 2009-09-23
Hey luksol so AD is kind of an interesting beast.

It's sort of like a combination of LDAP, Kerberos, and Samba.  The thing is... authentication in AD is tied to kerberos.

Now the trick for synchronizing authentication between the two beasts would be to allow a cross realm transitive trust between an MIT Kerberos V ( or heimdal if you are a crazy european ) and Active Directory.  That way you can store user auth credentials in a database that unix can work with.  From there you'll probably want to add posix user schema to AD.

You SHOULD be able to with relatively little effort then pull user info from AD directly... and authenticate against your non AD kerberos server with not too much effort.

There's some caveats with this approach but for the most part it works.

---

### Post by HermanAB on 2009-09-23
See the man page for 'wbinfo', then go to the Samba web site and read the Official Howto.

---

