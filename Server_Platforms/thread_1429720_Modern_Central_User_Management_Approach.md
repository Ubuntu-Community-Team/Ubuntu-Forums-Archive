---
title: "Modern Central User Management Approach"
date: 2010-03-14
forum: Server Platforms
---

### Post by schreiter on 2010-03-14
Hello all,
I am looking for recommendations for the current thinking in central user management using Ubuntu on the server and client side.  

I've setup Kerberos and OpenLDAP servers (9.10) similar to the official documentation (and other sites that fill in the "gaps").  However, when you start to get in to some of the details, there seem to be many options - and I guess I'm looking for what could be the defacto standard.

I'd like to allow Ubuntu clients to have a sso capability, with the ability for local caching of passwords if not connected to the network (such as a laptop user away from the office, prior to a VPN).  I'd like to automount a secure NFS share somewhere in the /home directory.  If the user logs in to a computer they've not logged in to before (if they're authorized), it would be nice if a skeleton /home directory could be setup there automatically  I'm guessing that it is not desirable to use a shared /home NFS - as if you're off the network this would be problematic - as well as multiple computers sharing the same /home.  There are some benefits to a shared /home (SSH certs, etc.), so maybe there is a hybrid approach out there.

I've read that it's not necessarily good practice to have OpenLDAP to do the authentication (leave this to Kerberos), but it's fine for authorization (such as ACLs for logins to certain computers).  It's also good practice to use TLS with OpenLDAP (which requires public certs on all the clients) and to not allow anonymous read to the directory.  

I would guess that a computer host keytab could be refreshed to bind to the OpenLDAP server via GSSAPI / SASL to allow a non-anonymous read, and then determine if, say, the user was a member of a group allowed to log in.  Kerberos would then pick up and authenticate the user and then proceed to the login.  Off the network here, I'm not sure.

I found this document, but it's self declared missing items: <https://help.ubuntu.com/community/SingleSignOn>

I'll stop the rambling, but I cannot be the only one who would like to setup a relatively standard and secure server based network authentication and authorization back-end.  Is there any _complete_ documentation on the best practices and how to implement?

Many thanks!
Jonathan

---

### Post by Samatva on 2010-03-15
Most of your question is way above my experience, although I am quite interested as I am currently undergoing "trial by fire" setting up an OpenLDAP server to replace an old in-house MySQL auth system. We are planning to do authentication with OpenLDAP using TLS, but only for logging into other systems (i.e. web scripts), not into Ubuntu itself. We are load/updating LDAP from our existing databases.

I would question the desire to mount a /home directory for users - this is a seemingly crude way to provide disk space. As soon as we have our LDAP going, my very next project is to tie in the Alfresco ECM - our preliminary test (using local login) have our users chomping at the bit for the production launch. Alfresco implements most of the SharPoint protocol, can "mount" a webfolder (WebDAV) (to a drive letter in Windoze), and has a slick "share" web system as well. (I *think* it supports incoming NFS mounts as well, but need to double check on that...)

Good luck on getting your system going...

---

### Post by beniwtv on 2010-03-15
There is no "best practices". It varies with what you want to do.

I previously considered OpenLDAP as well. It's a very good piece of software, however, I found it very difficult to work with. I've now settled on a MySQL auth scheme. (MySQL + PAM should get you started on that).

The reason I changed from OpenLDAP to MySQL was mainly that it has good integration with our CRM system that uses MySQL already. 

You might have an existing CRM system (I don't know), which has it's user accounts already there. My idea was to not having to maintain separate user databases for each service. For that, OpenLDAP had to be synchronized with MySQL automatically.

Obviously, you can make a script that synchronizes them on every CRM change ("Save" button). Or even synchronize every 4 hours or so the whole tree. Both ways I found unacceptable, because with the first way there was a slight chance everything gets out of sync someday.  The second way is OK, however I'd have to wait 4 hours or so for the data to propagate.

So I started looking into back_sql (which allows you to use MySQL with OpenLDAP). However, this was bad too as OpenLDAP needs a restart for every change you make to your users for it to pick up the changes.

With MySQL, I can change the user's details (password, name, etc) instantly, and there is no delay. All services start using it right away, and the set-up is very simple.

Just my 2 cents.

Cheers,

---

### Post by algoe on 2011-01-12
I am also looking for this kind of solution. Where you successful in finding a complete guide or setting this up?

---

### Post by beniwtv on 2011-01-12
> **algoe said:**
> I am also looking for this kind of solution. Where you successful in finding a complete guide or setting this up?

Yes, I have sucessfully set something like this up before, though I have had no time yet to make a script that does it automatically.

Though if you want some pointers for your project, let me know, I may be able to get you started.

---

