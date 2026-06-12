---
title: "SVN Server"
date: 2009-08-12
forum: Server Platforms
---

### Post by joe2012 on 2009-08-12
Anyone know of any easy to setup svn servers?

Thanks

---

### Post by alastair on 2009-08-12
apt-get install subversion

?

What's the specific problem ?

---

### Post by joe2012 on 2009-08-13
Ok, so I ran
```
sudo apt-get install subversion
```

and then I ran this:
```
svnadmin create /var/svn/test
```

and now I don't know how to connect to the machine remotely. I installed TortiseSVN on a windows machine, and tried to connect and import the repo using:
svn+ssh://<username>@<myip>:443/var/svn/test

I'm running my ssh on 443 because 22 is blocked at work. Is there anything I'm missing?

Thanks

---

### Post by hessiess on 2009-08-13
You will want to set up Apache with SSL, and use that for serving your SVN repos, read [http://www.geocities.com/arhuaco/doc/subversion/apache-subversion-in-debian.html](http://www.geocities.com/arhuaco/doc/subversion/apache-subversion-in-debian.html)

---

### Post by joe2012 on 2009-08-13
> **hessiess said:**
> You will want to set up Apache with SSL, and use that for serving your SVN repos.

I want to use svnserve, but I can't seem to connect to after running the server with:
```
 svnserve -t -r /home/joe/repo/
```

---

### Post by hessiess on 2009-08-13
> **joe2012 said:**
> I want to use svnserve, but I can't seem to connect to after running the server with:
```
 svnserve -t -r /home/joe/repo/
```

You rilly should use Apache with HTTP DAV and SSL for serving SVN. As HTTPS is impossable to filter it is easy to sneek through firewalls ;), Read the page linked to in the edit above.

From where carn't you connect to the server, home or work? Check your port forwarding, Dynamic DNS (I assume you are using this?) and make sure that the server has a static IP on your home network.

---

### Post by dwhitese on 2009-08-13
> **hessiess said:**
> You rilly should use Apache with HTTP DAV and SSL for serving SVN. As HTTPS is impossable to filter it is easy to sneek through firewalls ;), Read the page linked to in the edit above.
Agreed. **apt-get install subversion apache2 libapache2-svn**, if I remember correctly, will pull in all the dependencies you need to do DAV/SVN over HTTP, and the howto above will cover HTTPS.

A note, there are more ways than just htpasswd files to authenticate, but for 99.99% of small setups, you don't need anything more complicated than htpasswd.

---

