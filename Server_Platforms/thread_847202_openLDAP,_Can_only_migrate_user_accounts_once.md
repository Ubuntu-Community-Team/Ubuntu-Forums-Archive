---
title: "openLDAP, Can only migrate user accounts once?"
date: 2008-07-02
forum: Server Platforms
---

### Post by Titan8990 on 2008-07-02
I am trying to set up LDAP to authenticate on a redmine site hosted on the local machine. I used migration tools to migrate the local machines user accounts with LDAP. I added a user to the local machine and it will not migrate again.

Do these need to be updated manually once LDAP has been migrated with the local user accounts one?

---

### Post by promodus on 2008-07-02
I'm not certain what you're trying to do.

Ideally you would have your base local accounts, then you add LDAP as an option for other (or domain) accounts to the local system.

If you have used windows in an domain setting, it's very similar where you can log onto the domain and also log on locally.

Having said that, you typically would migrate the accounts once. Once the accounts are migrated you set the host to also bind to LDAP so when you add a new account it's added to LDAP and it works in both places that you mentioned.

---

### Post by Titan8990 on 2008-07-03
Thank you, I will look into binding LDAP with the host machine. Until then I found a way to do it manually. 

I find the documentation on LDAP is flakey at best. I had a hell of time getting it set up because the dpkg for slapd wasn't actaully editing my config file. Go figure.

Is it possible to bind openLDAP to active directory?

Thanks for the reply.

---

### Post by promodus on 2008-07-03
> **Titan8990 said:**
> Thank you, I will look into binding LDAP with the host machine. Until then I found a way to do it manually. 

I find the documentation on LDAP is flakey at best. I had a hell of time getting it set up because the dpkg for slapd wasn't actaully editing my config file. Go figure.

Is it possible to bind openLDAP to active directory?

Thanks for the reply.

You've getting the right idea.

The idea of having a directory is centralizing your configuration. You could almost compare it to the windows registry, but for the network. In a way.

What you may be after is binding your linux machines to your active directory. You wouldn't bind OpenLDAP to it. Think  of DNS. You could have a DNS Server look up records in another server. With OpenLDAP you would replicate or you would segment a portion. 

So you could have one domain being domain.local on one server
and then have another with sub.domain.local on another.

There is a learning curve. 

Depending on the size of your network, ideally you'd only have one domain. When you deal with larger networks, some spanning the country be it a company with several branches, then what may work well is having sub domains for each branch, and having one master controller where they all replicate to. (So if someone goes to another Branch, they can still log in)

Huge can of worms.
What size is your network?
What are you planning to use Directory services for?

---

### Post by Titan8990 on 2008-07-07
Our internal network is not very large. We have about 40 employees/clients that access our domains over 3 states. The main objective here is actually to bind our Active Directory users to our Redmine website. Those Active Directory users already use thier usernames/passwords for a varienty of things such as access to our software, internal wikis, and etc. 

I was trying to set up LDAP auth on redmine as I figured it would be easier to do testing when the machine that authenticates is the localhost of the redmine website. I later had planned to change auth to our AD domain or find a way to migrate AD over to the localhost.

---

