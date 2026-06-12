---
title: "MoinMoin superuser setup and ACLs"
date: 2008-08-31
forum: Server Platforms
---

### Post by 3strandchords on 2008-08-31
Hi.

I'm running ubuntu 8.04 and have installed apache2 and the moinmoin wiki (running via CGI).

I visited the wiki ([http://localhost/mywiki](http://localhost/mywiki)) and created a user account ('BigCheese').  I'd like to set the wiki so that 'BigCheese' has admin rights to set ACLs on all pages.

In the wikiconfig.py script, there is a section that reads:
```
    # This is checked by some rather critical and potentially harmful actions,
    # like despam or PackageInstaller action:
    #superuser = [u"YourName", ]
```

I've uncommented the line, changed the 'YourName' default to 'BigCheese', saved the file, and restarted the apache server.

I revisit the wiki, login as 'BigCheese', and try to edit a page and insert an ACL:
```
#acl Guy1:read,write,revert,delete Guy2:read
```

But when I save the page, I get the following error:
```
You can't change ACLs on this page since you have no admin rights on it!
```

So:  How do I create a working superuser (for the wiki) who can assign ACLs?  Do I need to specify the superuser in wikiconfig.py *before* their user account is created in the wiki?

Thanks in advance.

---

### Post by 3strandchords on 2008-08-31
Half-answered my own question...

It appears that the fix is to just use the next line of the wikiconfig.py to pre-grant a user 'superuser-esque' rights:
```
    # IMPORTANT: grant yourself admin rights! replace YourName with
    # your user name. See HelpOnAccessControlLists for more help.
    # All acl_rights_xxx options must use unicode [Unicode]
    acl_rights_before = u"BigCheese:read,write,delete,revert,admin"

```

It doesn't seem to matter whether the 'superuser' line is on/off or not.  

So, I've solved the problem, but in a way that lacks elegance.  If there's a superuser assignment line in the config file, I would expect that to actually create a superuser or allocate those privileges wiki-wide.  Am I missing something here?

Anyway, up and running.  But I'd still like an answer, if anyone knows.

---

### Post by sebald on 2008-10-06
FWIW, nobody replied to my post on similar topic, and meanwhile I just gave up and went to MediaWiki :-)

I'll try your solution just for fun.

---

