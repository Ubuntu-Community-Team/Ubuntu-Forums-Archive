---
title: "export normal unix users to ldap user"
date: 2010-07-01
forum: Server Platforms
---

### Post by Thyagaraj on 2010-07-01
Can any one tell me how to export normal unix user to ldap 
I've unbuntu ldap server with some local users. I want to export all my local users to ldap database as a ldap users. Or if there is any configuration so that when ever a normal user is created then automatically an ldap user with the same name as the normal user will be created, please give me step by step guide.

---

### Post by dlepiane on 2010-07-01
> **Thyagaraj said:**
> Can any one tell me how to export normal unix user to ldap 
I've unbuntu ldap server with some local users. I want to export all my local users to ldap database as a ldap users. Or if there is any configuration so that when ever a normal user is created then automatically an ldap user with the same name as the normal user will be created, please give me step by step guide.

There are standard tools for migrating password file users to LDAP:

[http://www.jukie.net/~bart/ldap/ldap-authentication-on-debian/#Populate%20the%20database](http://www.jukie.net/~bart/ldap/ldap-authentication-on-debian/#Populate%20the%20database)

There are other examples Online.

---

### Post by Thyagaraj on 2010-07-07
Is there any other way in ubuntu when ever i create a normal unix user, same user is automatically created in ldap database.

Could any one give me step by step guide to export/import ldap user to or from /etc/passwd.

Plz need help...

---

### Post by capscrew on 2010-07-07
> **Thyagaraj said:**
> Is there any other way in ubuntu when ever i create a normal unix user, same user is automatically created in ldap database.

This would defeat the purpose of having a separate domain wide database of users.  When logging in which database would the system use?   The LDAP vs local should never be resolved by have both locations for this data.> 
Could any one give me step by step guide to export/import ldap user to or from /etc/passwd.

Not all of the user information is kept in the /etc/passwd file.  The password is kept in the encrypted file /etc/shadow.

See [**_here _**]("http://www.google.com/search?hl=en&q=export+/etc/passwd+/etc/shadow+to+ldap&aq=f&aqi=m1&aql=&oq=&gs_rfai=")for more thoughts.

---

### Post by Thyagaraj on 2010-07-09
ok fine.

Now, I want to export /import an object of an ldap server to another ldap server.

Using  #slapcaat -l outputfile.ldif will export all into ldif format. But I want to export only a particular ou in ldif format from an ubuntu server to another ubuntu server. Or if there is other way of exporting ldap database?

If any tips & tricks of any thing of ldap please help me replying to this

Thank you all!

---

### Post by dlepiane on 2010-07-11
> **Thyagaraj said:**
> ok fine.

Now, I want to export /import an object of an ldap server to another ldap server.

Using  #slapcaat -l outputfile.ldif will export all into ldif format. But I want to export only a particular ou in ldif format from an ubuntu server to another ubuntu server. Or if there is other way of exporting ldap database?

If any tips & tricks of any thing of ldap please help me replying to this

Thank you all!

This is straight from the documentation:

[http://linux.die.net/man/8/slapcat](http://linux.die.net/man/8/slapcat)

-s subtree-dn
    Only dump entries in the subtree specified by this DN. Implies '-b subtree-dn' if no -b or -n option is given. 


If you need more help like this, LDAP is also very well explained in this book:

[http://oreilly.com/catalog/9781565924918](http://oreilly.com/catalog/9781565924918)

And there are a lot of other excellent books on the topic, LDAP has been around for a long time and is widely used on basically every platform.

---

