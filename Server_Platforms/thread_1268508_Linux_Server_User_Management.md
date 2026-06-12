---
title: "Linux Server User Management"
date: 2009-09-17
forum: Server Platforms
---

### Post by stefanadelbert on 2009-09-17
I have a server hosting an email server (postfix, dovecot) and webmail (horde), SVN repository, sharing folders and a printer with Linux and Windows boxes using Samba, running WebSVN and potentially other services.

It's important that the server be fairly secure - so some basic security will do (doesn't need to be SSL). I've setup UNIX user accounts and home directories for all users (this seems to cater for the email server side of things nicely) - one set of passwords. I've created SVN users - another set of passwords. I've created Samba users - another set of passwords.

Is it possible to create UNIX user accounts and then have Samba, SVN and other services use the same users and groups and passwords? It seems like openLDAP might be a solution, which I'm reading about at the moment. Does anyone have any suggestions or advice?

---

### Post by openfly on 2009-09-18
OpenLDAP will be the easiest solution for you.

Down the road you may end up choosing to support more Microsoft systems and products in which case you'll probably end up deploying Active Directory.

I'll get back to the two approaches to that.

With LDAP your configuration is fairly well documented on the internet.  You configure ldap in /etc/.  Confirm your ldap queries are working.  Load in the users with POSIX accounts in their schema.  Then you setup PAM to use LDAP as an auth type, and to auto create home directories for new users.  Then you might want to set group access in PAM to allow access to servers based on LDAP GIDs.

It's been done a lot and this stuff is all over the internet.  You can get help.  And it's awesome once it's running.

With AD you can basically do the same with a few caveats... relying on the LDAP access to AD.

OR...

You can use Kerberos for the auth, and setup a cross realm trust between AD and the Kerberos system.  Then you can do Kerberos ticket based auth across the board.  This is really an enterprise solution and the sort of thing the DOE would deploy... not something most people would do.  But the results are seamless pass through auth resulting in one time authentication.

Depending on your application and budget you may want to look into securid tokens or something at some point.  Who knows.  Maybe do some region based auth checking in pam.  That's down the road though.

---

### Post by stefanadelbert on 2009-09-27
Thanks for the response, openfly.

ATM there are only four users on the network, so critical mass has not yet been reached and a LDAP/AD style approach is probably not necessary. But it could very quickly ramp up to 10 people and then things would start becoming interesting.

The likelihood is that the proportion of Windows machines will decline as the company grows (about half-half at the moment), so support for Microsoft services in the future is not too much of a consideration.

I think I'll take a look at setting up LDAP. If you happen to know of a particularly good tutorial, I would like to hear about it! I'll post back here if I find a good one.

---

