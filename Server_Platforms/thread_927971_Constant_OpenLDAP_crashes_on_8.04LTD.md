---
title: "Constant OpenLDAP crashes on 8.04LTD"
date: 2008-09-23
forum: Server Platforms
---

### Post by Caesonia on 2008-09-23
Hi all. I am somewhat new to Ubuntu, trying my first installs back in December, and before that it was CentOS and Redhat. I would say I am a middle level linux/server user, and have done most of my development in a LAMP environment. Since then, I have built 3 different Ubuntu Servers -1 with 7.10, the other 2 with 8.04 LTD.

My choice was to install the Default Desktop, and build the servers from there, and basically everything has gone fairly smoothly. There are some bugs, but on the whole, it was possible to get things configured in fairly standard manners, and they have happily accepted updates and such.


Unfortunately, I have had a bear of a time with the LDAP server. Doing the initial default install has gone very well, as a whole. The problem comes when I actually start doing development for central login interfaces, and have to modify the configuration files say to allow for self write abilities for authenticated users.

ANY modification to the configuration files causes a failure. The server  might or might not restart. Even if it does restart, I will lose often lose the ability to authenticate, even as an admin user. Sometimes I can go back the default configuration and restart it, but not always.

The most common error is error 13 cannot bind to server sort of error. The rest are a combination of things that flick up.

I have had to completely rebuild the LDAP server several times now, and its getting tiresome, because I am never really sure what is going on, so I am not able to learn from the experience.Most importantly it raises the point that if LDAP is this much trouble, it really is not the solution it is sold as. I am afraid to start using it for our SAMBA or anything else, until it proves it can be managed in a stable manner.

Having said all that, I would REALLY appreciate some help on guidance from bug workarounds, to why making any change from adding a new schema to just changing a singel line on a schema causes the entire server to just crash, and fail to restart when the default is reinstalled. 

LONG searches haven't really made anything any clearer, and I fear that I am running into things that have yet to be really addressed.

I am running the .9 version of ubuntu OpenLDAP on an Inspiron 530.

TIA for any guidance I can get.

---

### Post by pdwerryhouse on 2008-09-23
It's hard to tell what's going on without detailed logs. My suggestion is that if the server dies when you start it, try running it with some debug options (-d and a number) and see what errors it is throwing.

Have you tuned it correctly? The defaults are not necessarily going to be good for your dataset; see [the FAQ]("http://www.openldap.org/faq/data/cache/190.html"). Look carefully at the settings that you need to put in the DB_CONFIG file *before* you create the database.

---

### Post by Caesonia on 2008-09-24
> **pdwerryhouse said:**
> It's hard to tell what's going on without detailed logs. My suggestion is that if the server dies when you start it, try running it with some debug options (-d and a number) and see what errors it is throwing.

Have you tuned it correctly? The defaults are not necessarily going to be good for your dataset; see [the FAQ]("http://www.openldap.org/faq/data/cache/190.html"). Look carefully at the settings that you need to put in the DB_CONFIG file *before* you create the database.

Thanks for replying. I'll bring some more logs on, and see if that helps.

However, what is DB_CONFIG. In all my reading about this, I have never seen any mention of that before.

TIA

---

### Post by gpredrag on 2008-09-24
slapd is very picky about its configuration file, you really should read man page of slapd.conf VERY carefully.
I had similar experience log ago when first tried LDAP my self, and the problem was me not understanding the format of slapd.conf.
For instance, every directive (line) in the file MUST start from the first column, otherwise it is considered continuation of the previous line. So what I saw in slapd.conf and what slapd saw were two different things.
After making any changes you should run slaptest it will catch errors before restarting.
Also try running slapd in debug mode i.e 
```
slapd -u openldap -g openldap -h ldap://127.0.0.1/ -d255
```
to see errors.
Why did you rebuild the slapd? I don't see anything wrong with regular Ubuntu package. Even if you need something different try rebuilding ubuntu (or debian)  package. Slapd is very sensitive to version of berkley DB that you have on the system. I had problem with DIY slapd after OS upgrades because of that.
DB_CONFIG is very important file that lives in /var/lib/ldap and configures berkley DB that is used by slapd. One of advantages of regular Ubuntu package is that it has some sensible default.
I have several LDAP servers, some on Ubuntu others on Debian (almost the same package) and the are rock solid.
My advice would be to aptitude purge slapd, remove self-built slapd and then reinstall.
Read man slapd.conf, run slaptest after changes.

---

### Post by Caesonia on 2008-09-25
> **gpredrag said:**
> slapd is very picky about its configuration file, you really should read man page of slapd.conf VERY carefully.
I had similar experience log ago when first tried LDAP my self, and the problem was me not understanding the format of slapd.conf.
For instance, every directive (line) in the file MUST start from the first column, otherwise it is considered continuation of the previous line. So what I saw in slapd.conf and what slapd saw were two different things.
After making any changes you should run slaptest it will catch errors before restarting.
Also try running slapd in debug mode i.e 
```
slapd -u openldap -g openldap -h ldap://127.0.0.1/ -d255
```
to see errors.
Why did you rebuild the slapd? I don't see anything wrong with regular Ubuntu package. Even if you need something different try rebuilding ubuntu (or debian)  package. Slapd is very sensitive to version of berkley DB that you have on the system. I had problem with DIY slapd after OS upgrades because of that.
DB_CONFIG is very important file that lives in /var/lib/ldap and configures berkley DB that is used by slapd. One of advantages of regular Ubuntu package is that it has some sensible default.
I have several LDAP servers, some on Ubuntu others on Debian (almost the same package) and the are rock solid.
My advice would be to aptitude purge slapd, remove self-built slapd and then reinstall.
Read man slapd.conf, run slaptest after changes.

I run the error check, and I always consistently get 
daemon: bind(7) failed errno13 (Permission Denied)

I see others asking this question, but I never see any answers. But its the consistent failure. It simply will not restart the server, except sometimes on a reboot.

---

### Post by gpredrag on 2008-09-25
What are the permissions for /var/lib/ldap directory? Regular slapd runs as 'openldap' user. Directory and it's content should be owned and readable by openldap user and openldap group.
If you have run slapindex as root user you have to correct those permissions afterwards manualy.
slapd.conf should be readable by the same user.
Are you using TLS? If so, private key file as well as the certificate file should be readable by the same user that slapd runs under (openldap)?

---

### Post by Caesonia on 2008-09-25
> **gpredrag said:**
> What are the permissions for /var/lib/ldap directory? Regular slapd runs as 'openldap' user. Directory and it's content should be owned and readable by openldap user and openldap group.
If you have run slapindex as root user you have to correct those permissions afterwards manualy.
slapd.conf should be readable by the same user.
Are you using TLS? If so, private key file as well as the certificate file should be readable by the same user that slapd runs under (openldap)?
 Yeah, that is the direction I was going in. So if you are suggesting it, at least I know I am going in the right direction.

 I happen to have this running on CentOS but it runs a little differently, with a different username. So far I see things as readable and executable for group and owner...but I see root owning a lot, and I have had a question mark regarding that. I will get back with you when I look at all the configurations.

Do you have a list of all the directories and files that slapd is running in? I am always a afraid I am missing a few, and that's where the 'bug' is.

Where is slapindex?

TIA.

---

### Post by gpredrag on 2008-09-25
I have to correct my self,
directory where database is (and all the files) should be  owned to whatever user and group slapd is runnig, and **writable** by owner (i.e openldap user).
User and group are set in /etc/default/slapd under ubuntu/debian something like..
```

SLAPD_USER="openldap
SLAPD_GROUP="openldap"

```
under CentOS, you figure it yourself reading startup scripts

Location of the database is in slapd.conf. Something like...
```
directory "/var/lib/ldap"
```
under database section of the file. This is default location under ubuntu/debian, do not know about CentOS, but just read the file.

If you have instructed slapd to use certificates and keys check the permissions of the directory where they are. openldap user should be able to read them (and nobody else). Same goes for slapd.conf. Or you can skip TLS until you actually get slapd running in the first place.

Rest of the files are libraries. Under debian/ubuntu
```
dpkg -L slapd
```
will give you all the files of particular package. Under CentOS that would be rpm -something -something, I forgot, long time since I haven't used RedHat.
Anyway you probably haven't hosed those permissions since those are non-edited libraries and are readable by anone and that is sufficent.
slapindex is in /usr/sbin and in your PATH probably. DO NOT run that command while slapd is running. It is used to reindex slapd database if you have changed your mind about what should be indexed on existing object. You should run it under openldap user, or if you run it as a root, change back ownership of /var/lib/ldap/* back to openldap user.
Under debian you got warnings about that after the command is run.

---

### Post by Caesonia on 2008-09-26
```

SLAPD_USER="openldap
SLAPD_GROUP="openldap"

```

Yeah, this was very helpful. All this time I have been dealing with Linux based servers, and I was always installing everything from the ground up and not really using apt-get yum type 'packages' so I never realized that slapd had a default file or even thought about the whole default. I am not sorry its there, I am just saying that the Ubtunu documentation should probably make users aware of it. Becuase most of the time, you are going to have install as root, and I don't recall being given and option to choose ownership.

I actually was looking in the start-up scripts file, as with CentOS, and I wasn't seeing anything there. 

Anyhoo, by the time I saw that, I had already changed the ownership on all the slapd stuff I could find, and it seems to be working now. I can start it and stop it routinely, to make changes in the configuration. One of the additional glitches I ran into, is when I was trying somethings through the webmin interface, and found it was adding some addition ' ' and that was causing problems reading the access files.  




```
directory "/var/lib/ldap"
```

 Again this was very helpful as a place to peek.

I haven't put TSL in yet, but I will as I move forward, especially if I decide to put the server outside. For now, its running completely internally. 

```
dpkg -L slapd
```

I wasn't even thinking of doing this this way. Thanks. 


Anyway you probably haven't hosed those permissions since those are non-edited libraries and are readable by anone and that is sufficent.

[I]slapindex is in /usr/sbin and in your PATH probably. DO NOT run that command while slapd is running. It is used to reindex slapd database if you have changed your mind about what should be indexed on existing object. You should run it under openldap user, or if you run it as a root, change back ownership of /var/lib/ldap/* back to openldap user.
Under debian you got warnings about that after the command is run.[/I]

As someone fairly new to LDAP, I am not even sure about how things are going to be structured at the moment. I am just trying to get a healthy test bed set up so I can play with the configurations some to see if I can adapt it to some of our purposes as a central authentication point. Right now I am developing my own user interface for a central login point into all the different applications being run, and seeing how the configuration itself can be modified around that. 

I am sure I will back here for more help shortly, but your pointers have really gotten some frustrations overcome. Thanks.

---

