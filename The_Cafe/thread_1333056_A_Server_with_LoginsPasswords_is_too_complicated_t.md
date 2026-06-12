---
title: "A Server with Logins/Passwords is too complicated thing in Linux :("
date: 2009-11-21
forum: The Cafe
---

### Post by frenchn00b on 2009-11-21
check this, I mean, this is not a way: 
[https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows)?highlight=(ldap](https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows)?highlight=(ldap))

**the target was [this]("http://yellowprotoss.ye.funpic.org/website/ubuntu_installing_ldap/ubuntu_server_logins.JPG"), but it seemed and seems impossible with LDAP. maybe buggy or not reliable :(  This mission is impossible under Ubuntu**. My Samba and NFS /home export are working well, but password/login server is impossible.

Luckily one can do : 
```
dpkg-reconfigure slapd

```
and it is installed, but for the rest: forget.  

It can be said for serveral daemons: openvpn, samba, ... 
Servers are for geek. So what does Ubuntu ?   [LDAP]("http://yellowprotoss.ye.funpic.org/website/ubuntu_installing_ldap/linux_ldap_frenchn00b.gif")

we need xmenu, xdialog like to install, not vim or nano. We are in 2009 !!!!! and linux is not capable to code a damn simple installer.

---

### Post by Islington on 2009-11-21
Has anyone really been far even as decided to use even go want to do look more like?

---

### Post by Xbehave on 2009-11-21
A server for what? there are plenty of simple GUI tools that offer simple servers, but if you want a real server you need to know what you want

Filesharing through samba,ftp-deamons(various),simple-http deamons,nfs all have gui tools to setup. LDAP is a more complicated tool and so i wouldn't be suprised that it requires you to know what you are doing to set up. In general setting up authentication systems requires you to have a clue about security, if you have that clue then editing text file sis not going to be a problem, if you do not then the authentication is going to be pointless.

---

### Post by frenchn00b on 2009-11-21
> **Xbehave said:**
> A server for what? there are plenty of simple GUI tools that offer simple servers, but if you want a real server you need to know what you want

Filesharing through samba,ftp-deamons(various),simple-http deamons,nfs all have gui tools to setup. LDAP is a more complicated tool and so i wouldn't be suprised that it requires you to know what you are doing to set up. In general setting up authentication systems requires you to have a clue about security, if you have that clue then editing text file sis not going to be a problem, if you do not then the authentication is going to be pointless.
  
I mean one can use dialog to make a samba installer.

it is not difficult: 
here are teh commands:


we need howto ok, but installer are hugerly important with dialog (no X or Xdialog please after asking), are such: 


```
dialog --title "My input box" --clear   --inputbox "Hi, this is a sample input box\n Try entering your name below:" 16 51 2
 echo $?

dialog --title " My first dialog"        --yesno "Hello , this is my first dialog program" 10 30
 echo $?

dialog --clear --title "My  favorite HINDI singer" --menu "Hi, Choose  your favorite HINDI singer:" 20 51 4   "Rafi"  "Mohammed Rafi"                          "Mukesh" "Mukesh P."   "Saigal" "K L Saigal"   "Lata"  "Lata Mangeshkar"
echo $?

  seq 1 1 100  | while read i ; do        echo "coucou"   ; sfdialog  --clear --title "hello $i" --gauge "coucou " 8 75 $i ; sleep 2s ; done
 echo $?

```

---

### Post by frenchn00b on 2009-11-21
> **Xbehave said:**
> A server for what? there are plenty of simple GUI tools that offer simple servers, but if you want a real server you need to know what you want

Filesharing through samba,ftp-deamons(various),simple-http deamons,nfs all have gui tools to setup. LDAP is a more complicated tool and so i wouldn't be suprised that it requires you to know what you are doing to set up. In general setting up authentication systems requires you to have a clue about security, if you have that clue then editing text file sis not going to be a problem, if you do not then the authentication is going to be pointless.
  
it is not right what you say. 
[COLOR="Red"]It would be better that a geek write a good installer, rather than a n00b installs a server that does have SECURITY ISSUES !!!
think about it . If it is too complicated, the n00b wont make it, to install it well. And dont tell me that Linux is simple[/COLOR]

---

### Post by cariboo on 2009-11-21
The server version has no gui tools by design. It is felt by the design team that you get better performance and more security by running without a gui.

If you need or want a server with gui setup tools, you don't have to stick with Ubuntu, there are plenty of other server distributions with the features you want.

---

### Post by frenchn00b on 2009-11-21
> **cariboo907 said:**
> The server version has no gui tools by design. It is felt by the design team that you get better performance and more security by running without a gui.

If you need or want a server with gui setup tools, you don't have to stick with Ubuntu, there are plenty of other server distributions with the features you want.
  
did I mean  a gui?? 

A server has no monitor. Check this page, this is dialog
[http://linuxgazette.net/101/sunil.html](http://linuxgazette.net/101/sunil.html)

So Ubuntu DIALOG installers, instead of long and complicated wiki with nano, cp... edit,... , can be coded.


> Ubuntu, there are plenty of other server distributions with the features you wan
which server distro you meant? Live-CDroms? It will be too more complicated. Ubuntu is the easiest distro ever I would say, and has good forums.


--
[For fun, I made this LDAP, nothing meant. It's a funny gif ;) I like his face... I was laughing a lot when I saw this on tv]("http://yellowprotoss.ye.funpic.org/website/ubuntu_installing_ldap/linux_ldap_frenchn00b.gif")

---

### Post by Xbehave on 2009-11-21
> **frenchn00b said:**
> we need howto ok, but installer are hugerly important with dialog (no X or Xdialog please after asking),
who is this aimed at, desktop users can use GUI tools
synaptic + systrem-config-ftp, etc
Server admins should be good enough with the CLI and it's assumed they know what they are doing.

I fail to see the need for a CLI,installer wrapper for stuff when you can just use apt-get for a default install then tweak it to your needs.

---

### Post by frenchn00b on 2009-11-21
> **Xbehave said:**
> who is this aimed at, desktop users can use GUI tools
synaptic + systrem-config-ftp, etc
Server admins should be good enough with the CLI and it's assumed they know what they are doing.

I fail to see the need for a CLI,installer wrapper for stuff when you can just use apt-get for a default install then tweak it to your needs.

> **cariboo907 said:**
> The server version has no gui tools by design. It is felt by the design team that you get better performance and more security by running without a gui.

If you need or want a server with gui setup tools, you don't have to stick with Ubuntu, there are plenty of other server distributions with the features you want.
  
did I mean  a gui?? 

A server has no monitor, we can just access it from the network. **[COLOR="Red"]A server has NO X ,no XORG[/COLOR]**. Check this page, this is dialog
[http://linuxgazette.net/101/sunil.html](http://linuxgazette.net/101/sunil.html)

So Ubuntu DIALOG installers, instead of long and complicated wiki with nano, cp... edit,... , can be coded.


> Ubuntu, there are plenty of other server distributions with the features you wan
which server distro you meant? Live-CDroms? It will be too more complicated. Ubuntu is the easiest distro ever I would say, and has good forums.


--
[For fun, I made this LDAP, nothing meant. It's a funny gif ;) I like his face... I was laughing a lot when I saw this on tv]("http://yellowprotoss.ye.funpic.org/website/ubuntu_installing_ldap/linux_ldap_frenchn00b.gif")

---

### Post by Xbehave on 2009-11-21
> So Ubuntu DIALOG installers, instead of long and complicated wiki with nano, cp... edit,... , can be coded.It could be done but it can't be as flexible as calling the current tools manually, so i don't see where it would be useful. when your dealing with servers flexibility trumps ease of use.

---

### Post by frenchn00b on 2009-11-21
> **Xbehave said:**
>   so i don't see where it would be useful.  .

come on, do not tell me that newbies do not need help. Such efforts from Linux community wouldnt be worth. An Installer is intended to help. 

look here... : [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

it maybe looks simple for you... yeah you are bright
Us the N00b's, we are stupid.

---

### Post by cariboo on 2009-11-21
frenchn00b, I'm sorry, I misunderstood your post. There is a Documentation team working on cleaning up and simplifying the how to's. 

The problem is that anyone can create an account and write a wiki howto. What seems easy to some people, is incomprehensible for other people. 

That particular howto has a couple of large banners across the top saying basically not to use it. The team is working hard to simplify or remove howto's like that.

The wiki is owned by Canonical, and there are procedures that have to be followed before a document can be reomved.

---

### Post by frenchn00b on 2009-11-21
> **cariboo907 said:**
> frenchn00b, I'm sorry, I misunderstood your post. There is a Documentation team working on cleaning up and simplifying the how to's. 

The problem is that anyone can create an account and write a wiki howto. What seems easy to some people, is incomprehensible for other people. 

That particular howto has a couple of large banners across the top saying basically not to use it. The team is working hard to simplify or remove howto's like that.

The wiki is owned by Canonical, and there are procedures that have to be followed before a document can be reomved.


Ohh dont worry. I just wish that linux replaces windows. 

Here I made this poll concerning installations under LINUX, let's check what will the mass reply, after this survey:
[http://ubuntuforums.org/showthread.php?t=1333105](http://ubuntuforums.org/showthread.php?t=1333105)

---

### Post by frenchn00b on 2009-11-21
> **cariboo907 said:**
> frenchn00b, I'm sorry, I misunderstood your post. There is a Documentation team working on cleaning up and simplifying the how to's. 

The problem is that anyone can create an account and write a wiki howto. What seems easy to some people, is incomprehensible for other people. 

That particular howto has a couple of large banners across the top saying basically not to use it. The team is working hard to simplify or remove howto's like that.

The wiki is owned by Canonical, and there are procedures that have to be followed before a document can be reomved.

the problem is that how'to are not up-to-date.
Packages are changing too fast, man. Several how to about LDAP openvpn, ... samba are out-dated, and can cause real damages in the machine and servers.
No one can modify them. Look wikipedia. it works better

---

### Post by Xbehave on 2009-11-21
> **frenchn00b said:**
> it maybe looks simple for you... yeah you are bright
Us the N00b's, we are stupid.
If your a noob why not use a gui? just install xorg then use x forwarding to set stuff up, xorg will only run when your configuring stuff so it won't slow anything down.

BTW i think there yast (the opensuse config tool) has an ncurses (a slightly more advance dialog) frontend, i don't know why it hasn't been ported to ubuntu though

---

### Post by frenchn00b on 2009-11-21
> **Xbehave said:**
> If your a noob why not use a gui? just install xorg then use x forwarding to set stuff up, xorg will only run when your configuring stuff so it won't slow anything down.

BTW i think there yast (the opensuse config tool) has an ncurses (a slightly more advance dialog) frontend, i don't know why it hasn't been ported to ubuntu though

a server has no X, otherwise we dont call it server man

---

### Post by koenn on 2009-11-21
> **frenchn00b said:**
> a server has no X, otherwise we dont call it server man
a server is defined by its role in a network infrastructure, not by having X or not.

---

### Post by frenchn00b on 2009-11-21
> **koenn said:**
> a server is defined by its role in a network infrastructure, not by having X or not.

In my univ. all server machines have no monitors. The admins are SSH-ing, certainly.

---

### Post by koenn on 2009-11-21
> **frenchn00b said:**
> In my univ. all server machines have no monitors. The admins are SSH-ing, certainly.

there's a whole world outside your uni's campus :)

---

### Post by Mornedhel on 2009-11-21
> **frenchn00b said:**
> In my univ. all server machines have no monitors. The admins are SSH-ing, certainly.

A server (software) is a daemon on *any* machine that listens for incoming connections (including local) and replies accordingly. You already have a number of servers running on a default desktop Ubuntu installation. X and CUPS come to mind. You can install many more.

A server (hardware) is what you're talking about, but it may or may not have an X server running, although most don't (waste of resources), as you point out.

If you're a n00b, you most certainly won't be installing an LDAP/Samba solution, by the way.

---

### Post by 3rdalbum on 2009-11-21
Ubuntu doesn't package Webmin, but it is available for use on your server. It handles LDAP, apparently.

---

### Post by frenchn00b on 2009-11-21
> **Mornedhel said:**
> A server (software) is a daemon on *any* machine that listens for incoming connections (including local) and replies accordingly. You already have a number of servers running on a default desktop Ubuntu installation. X and CUPS come to mind. You can install many more.

A server (hardware) is what you're talking about, but it may or may not have an X server running, although most don't (waste of resources), as you point out.

If you're a n00b, you most certainly won't be installing an LDAP/Samba solution, by the way.

```
A server (software) is a daemon on *any* machine that listens for incoming connections (including local) and replies accordingly.
``` 
 
I do not see well the need to have an X since they are all daemons running. I have nohting against sure about that you like X. 
 
For daemon and setting up things, I think that a chooser for configurator/setting up i.e. [dialog under console ]("http://www.dataswamp.net/apple2eserialterm/appleiie-terminal-nano.jpg")( or xdialog / or evtl. gtk), depending on how the users like it, would be a solution. user can choose other he works under SSH or SSH -X.

---

### Post by Mornedhel on 2009-11-21
> **frenchn00b said:**
> I do not see well the need to have an X since they are all daemons running. I have nohting against sure about that you like X.

They don't need X. I was pointing out that desktop machines run servers (software servers) as well. The default install of Ubuntu has servers (X, CUPS, etc. are servers). They communicate only to the local machine by default, but they are servers. If you configurate them, you can communicate with them through the network as well.

Server *machines* don't need X to be operated, since typically you'll only do admin tasks on them, you can perform that through SSH well enough, and it would be a waste of resources to run X sessions on those.

Anyway, moving on to the main topic of the thread.

> **frenchn00b said:**
> For daemon and setting up things, I think that a chooser for configurator/setting up i.e. [dialog under console ]("http://www.dataswamp.net/apple2eserialterm/appleiie-terminal-nano.jpg")( or xdialog / or evtl. gtk), depending on how the users like it, would be a solution. user can choose other he works under SSH or SSH -X.

The problem with graphical (yes, console-based dialogs are graphical interfaces) configurators is that you can never get as much power as editing configuration files would give you, unless you give the user the possibility to edit every possible option, which is just as complicated a task as editing the file directly. For things like LDAP, Samba, etc., this is a problem, because more use cases are not covered by the possibilities of the graphical configurator.

However, graphical configurators are still interesting in that they would allow you to quickly write config files corresponding to a basic use case, which you could then tweak until it corresponds exactly to what you need.

I suggest you check the feature requests/bug reports of your distribution and upstream, and file a request/bug report if there are none.

---

### Post by Exodist on 2009-11-21
> **cariboo907 said:**
> The server version has no gui tools by design. It is felt by the design team that you get better performance and more security by running without a gui.

If you need or want a server with gui setup tools, you don't have to stick with Ubuntu, there are plenty of other server distributions with the features you want.
+1 for server without GUI.

---

### Post by frenchn00b on 2009-11-21
Since fighting to get LDAP installed since 3 weeks... :) it's amazing. 

**Please could somebody post the content of its /etc/ldap ?**

I want to populate using: 
```
ldapadd -x -D "cn=french00b,dc=ubuntu,dc=local"  -W -f  french00b.ldif
```

and not way, creditential error

---

### Post by frenchn00b on 2009-11-21
To Frenc h Mornedhel, thanks, nicely writen, and meant.

> **Exodist said:**
> +1 for server without GUI.

wow !! 
thanks guys for support!! 

No X for daemons !

---

### Post by tnywtson on 2009-11-21
Well i don't know about Linux,i face some difficulty to use it.

---

### Post by juancarlospaco on 2009-11-21
Buy landscape and pro support...

---

### Post by koenn on 2009-11-21
> **frenchn00b said:**
> Since fighting to get LDAP installed since 3 weeks... :) it's amazing. 

**Please could somebody post the content of its /etc/ldap ?**

I want to populate using: 
```
ldapadd -x -D "cn=french00b,dc=ubuntu,dc=local"  -W -f  french00b.ldif
```

and not way, creditential error
start a thread in a support section (and include the exact output and error msgs you're getting)

---

### Post by frenchn00b on 2009-11-21
> **koenn said:**
> start a thread in a support section (and include the exact output and error msgs you're getting)

nobody replies because not so much people in the world are capable to understand how ldap works, even less kerberos.
LDAP team isnt capable to make something clear or shelf installable as a setup.exe under windows. 
 
So forget about daemons under linux. 

Even books, they never talk about those things. 
Because it is too complicated. 

It is like marketing. They know nothing, and pretend to be bright, and sell you crap. That's corporate world, nowadays. Nobody do really care about others.

> Enter LDAP Password:
ldap_bind: Invalid credentials (49)

then:
```
# This is the main slapd configuration file. See slapd.conf(5) for more
# info on the configuration options.

#######################################################################
# Global Directives:

# Features to permit
#allow bind_v2

# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile        /var/run/slapd/slapd.args

# Read slapd.conf(5) for possible values
loglevel        none

# Where the dynamically loaded modules are stored
modulepath	/usr/lib/ldap
moduleload	back_hdb

# The maximum number of entries that is returned for a search operation
sizelimit 500

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.
tool-threads 1

#######################################################################
# Specific Backend Directives for hdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend		hdb

#######################################################################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
#backend		<other>

#######################################################################
# Specific Directives for database #1, of type hdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        hdb

# The base of your directory in database #1
#suffix          "dc=ubuntu,dc=local"
 
#suffix          "dc=example,dc=com"
#directory       "/var/lib/ldap"
#rootdn          "cn=admin,dc=example,dc=com"
# 
# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
#rootdn          "cn=admin,dc=ubuntu,dc=local"
# Where the database file are physically stored for database #1
#directory       "/var/lib/ldap"

suffix          "dc=ubuntu,dc=local"
directory       "/var/lib/ldap"
rootdn          "cn=admin,dc=ubuntu,dc=local"
rootpw          secretsecret




# The dbconfig settings are used to generate a DB_CONFIG file the first
# time slapd starts.  They do NOT override existing an existing DB_CONFIG
# file.  You should therefore change these settings in DB_CONFIG directly
# or remove DB_CONFIG and restart slapd for changes to take effect.

# For the Debian package we use 2MB as default but be sure to update this
# value if you have plenty of RAM
dbconfig set_cachesize 0 2097152 0

# Sven Hartge reported that he had to set this value incredibly high
# to get slapd running at all. See http://bugs.debian.org/303057 for more
# information.

# Number of objects that can be locked at the same time.
dbconfig set_lk_max_objects 1500
# Number of locks (both requested and granted)
dbconfig set_lk_max_locks 1500
# Number of lockers
dbconfig set_lk_max_lockers 1500

# Indexing options for database #1
index           objectClass eq

# Save the time that the entry gets modified, for database #1
lastmod         on

# Checkpoint the BerkeleyDB database periodically in case of system
# failure and to speed slapd shutdown.
checkpoint      512 30

# Where to store the replica logs for database #1
# replogfile	/var/lib/ldap/replog

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword,shadowLastChange
        by dn="cn=admin,dc=ubuntu,dc=local" write
        by anonymous auth
        by self write
        by * none

# Ensure read access to the base for things like
# supportedSASLMechanisms.  Without this you may
# have problems with SASL not knowing what
# mechanisms are available and the like.
# Note that this is covered by the 'access to *'
# ACL below too but if you change that as people
# are wont to do you'll still need this if you
# want SASL (and possible other things) to work 
# happily.
access to dn.base="" by * read

# The admin dn has full write access, everyone else
# can read everything.
access to *
        by dn="cn=admin,dc=ubuntu,dc=local" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#        by dn="cn=admin,dc=ubuntu,dc=local" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be hdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix		"dc=debian,dc=org"

 
```

---

### Post by koenn on 2009-11-21
> **frenchn00b said:**
> nobody replies because not so much people in the world are capable to understand how ldap works, 
yet you expect some random people in a forum for "non-tech-support topics"  and " lighthearted and enjoyable discussions, like you might find around a water cooler at work" to fix your ldap problem. Makes sense.

---

### Post by koenn on 2009-11-21
I'm not an expert on ldap (way too complicated !), but "invalid credentials" usually means something like
- you gave an invalid password (maybe you mistyped)
- the user account you specified doesn't exist
- the user account you specified has no right to do what you want to do. 

maybe try with "cn=admin,dc=ubuntu,dc=local" instead of frenchn00b ?

---

### Post by frenchn00b on 2009-11-21
> **koenn said:**
> yet you expect some random people in a forum for "non-tech-support topics"  and " lighthearted and enjoyable discussions, like you might find around a water cooler at work" to fix your ldap problem. Makes sense.

no no 
the idea is that I expected that the community realizes that linux is NOT easy, and do something.

Instead of wiki, we need SETUP.EXE or installers, as under MAC or XP. 

[here LINK]("http://ubuntuforums.org/showthread.php?t=1333105")

I do think LINUX would gain lot of attention it is was made easier for everyone: 

GTK INSTALLER
+ 
CONSOLE INSTALLERS (DIALOG)
+ 
XDIALOG

the fundamental thinking how to make it for all is in our hands, ideas => brings a better world (well, can...)

---

### Post by Mornedhel on 2009-11-21
Can I ask why you're trying to install an LDAP server in the first place ?

---

### Post by frenchn00b on 2009-11-21
> **Mornedhel said:**
> Can I ask why you're trying to install an LDAP server in the first place ?

j'ai pas compris

---

### Post by frenchn00b on 2009-11-21
> **koenn said:**
> I'm not an expert on ldap (way too complicated !), but "invalid credentials" usually means something like
- you gave an invalid password (maybe you mistyped)
- the user account you specified account doesn't exist
- the user account you specified has no right to do what you want to do. 

maybe try with "cn=admin,dc=ubuntu,dc=local" instead of frenchnoob ?

I did the checking- :>  # ldapsearch -x -b 'dc=ubuntu,dc=local' '(objectclass=*)' 
looks working

```

# extended LDIF
#
# LDAPv3
# base <dc=ubuntu,dc=local> with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# ubuntu.local
dn: dc=ubuntu,dc=local
objectClass: top
objectClass: dcObject
objectClass: organization
o: RP614v4
dc: ubuntu

# admin, ubuntu.local
dn: cn=admin,dc=ubuntu,dc=local
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator

# search result
search: 2
result: 0 Success

# numResponses: 3
# numEntries: 2

```

I dont understand why because I used the default configuration file from a fresh install

 Is tehre someone with a tar.gz and the config files that work.

---

### Post by koenn on 2009-11-21
> **frenchn00b said:**
> I did the checking- :
looks working

it's not because you're allowed to query LDAP that you'd also be allowed to modify it.

besides, I don't see any object with "cn=frenchn00b" in that output. Maybe the account "cn=french00b,dc=ubuntu,dc=local" doesnt exist ?

try with cn=admin, why don't you.

---

### Post by koenn on 2009-11-21
> **frenchn00b said:**
> no no 
the idea is that I expected that the community realizes that linux is NOT easy, and do something.

Instead of wiki, we need SETUP.EXE or installers, as under MAC or XP. 

There's no setup.exe for Active Directory (LDAP+Kerberos on Windows Server) either. Those things are complex because they need to handle lots of different situations, all of which are complex by themselves. You can not replace understanding and design by wizards and dialog boxes. At least, not always.

---

### Post by Mornedhel on 2009-11-21
> **frenchn00b said:**
> j'ai pas compris

Bon, ok, on va le faire en français alors :)

Pourquoi tu veux un serveur LDAP ?  C'est pas vraiment quelque chose dont l'utilisateur standard a besoin, si tu vois ce que je veux dire.  La première chose à faire serait de s'assurer que tu essaies d'installer quelque chose qui correspond bien à tes besoins.

(Si tu as des soucis d'anglais, il y a aussi un forum de support francophone [ici](http://forum.ubuntu-fr.org/).)

---

### Post by frenchn00b on 2009-11-22
> **Mornedhel said:**
> Bon, ok, on va le faire en français alors :)

Pourquoi tu veux un serveur LDAP ?  C'est pas vraiment quelque chose dont l'utilisateur standard a besoin, si tu vois ce que je veux dire.  La première chose à faire serait de s'assurer que tu essaies d'installer quelque chose qui correspond bien à tes besoins.

(Si tu as des soucis d'anglais, il y a aussi un forum de support francophone [ici](http://forum.ubuntu-fr.org/).)

Jai pas de soucis en anglais. I have like 5 to 8 machines, connected to a server box nfs of the /home, I admin, and I have enough to adduser all the time on those 8 boxes and passwords too manually for each. une centrale de login/password connecte au server : c est la solution. Ils ont ca dans toutes les univ. par exmaple. mais faut du facile. le server export /home nfs et a un samba export too of hte /home for the windows xp. LDAP only is the solution? but its impossible for an human to be configured.

---

### Post by frenchn00b on 2009-11-22
> **Mornedhel said:**
> Bon, ok, on va le faire en français alors :)

Pourquoi tu veux un serveur LDAP ?  C'est pas vraiment quelque chose dont l'utilisateur standard a besoin, si tu vois ce que je veux dire.  La première chose à faire serait de s'assurer que tu essaies d'installer quelque chose qui correspond bien à tes besoins.

(Si tu as des soucis d'anglais, il y a aussi un forum de support francophone [ici](http://forum.ubuntu-fr.org/).)


Comme t'as du mal a comprendre, voici une image qui resume l'objectif: [here]("http://yellowprotoss.ye.funpic.org/website/ubuntu_installing_ldap/ubuntu_server_logins.JPG")

 

[B]I made a picture of what I would be pleased to achieve: 
[http://yellowprotoss.ye.funpic.org/website/ubuntu_installing_ldap/ubuntu_server_logins.JPG](http://yellowprotoss.ye.funpic.org/website/ubuntu_installing_ldap/ubuntu_server_logins.JPG)[/B]

 My Samba and NFS /home export are working well, but password/login server is impossible.

---

### Post by cariboo on 2009-11-22
Please keep your comments in English, as Mornedhel pointed out there is a French forum, if you feel more comfortable in your native language.

---

### Post by frenchn00b on 2009-11-22
> **cariboo907 said:**
> Please keep your comments in English, as Mornedhel pointed out there is a French forum, if you feel more comfortable in your native language.

well I wrote a bit in French because he was lacking of clarity with his english, i.e.: 
> Can I ask why you're trying to install an LDAP server in the first place ? First place? 

I am back with english speaking. it was few lines, above. I won't do in French, boss! it's ok. Greetings.

---

### Post by Mornedhel on 2009-11-22
About the weird English...

> Adverb
in the first place
   1. (idiomatic) To begin with; earlier; first; at the start.
   "The question is not whether I still enjoy the job, when I never enjoyed it in the first place."
   "In the first place, let's get the basics settled."

(from [http://en.wiktionary.org/wiki/in_the_first_place](http://en.wiktionary.org/wiki/in_the_first_place))

I just wanted to make sure you were trying to install a tool that matched your problems.  So far you hadn't mentioned what your configuration was like; with that many machines, LDAP is probably a reasonable solution.

However, I can't help you for the LDAP configuration itself. I have only one machine at home, so it's definitely not the kind of network that would require LDAP...

There are plenty of howtos other than the Ubuntu wiki, though. Most are floating around the Internet (for instance ([http://www.openldap.org/doc/admin24/quickstart.html](http://www.openldap.org/doc/admin24/quickstart.html)), or you could ask your uni's admins for pointers at a time when they're not too busy.

---

### Post by frenchn00b on 2009-11-22
Here guys I made what I would be glad to find for installign LDAP for logins / password or whatever daemon or things to install under linux, as example (not instlling ldap), for samba and nfs:
Mac and XP have installers / setup.exe.

[http://yellowprotoss.ye.funpic.org/website/ubuntuinstallers/ubuntu-samba-nfs-installer.sh](http://yellowprotoss.ye.funpic.org/website/ubuntuinstallers/ubuntu-samba-nfs-installer.sh)

-.-
edit:
I found a master for installing servers: [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

---

### Post by frenchn00b on 2010-01-10
I found a master for installing servers: [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

[LDAP]("http://yellowprotoss.ye.funpic.org/website/ubuntu_installing_ldap/linux_ldap_frenchn00b.gif")

---

### Post by steveneddy on 2010-01-10
:-s

---

### Post by frenchn00b on 2010-01-16
> **steveneddy said:**
> :-s

so here is the installer program.

[CENTER][I][U][B]EASY LDAP INSTALLER 
        (Dialog based):[/B][/U][/I][/CENTER]

Screenshots [1]("http://easyldap.exofire.net/files/installer/shot01.jpg") [2]("http://easyldap.exofire.net/files/installer/shot02.jpg") [3]("http://easyldap.exofire.net/files/installer/shot03.jpg") [4]("http://easyldap.exofire.net/files/installer/shot04.jpg")


Here a screenshot: [here]("http://easyldap.exofire.net/files/installer/easyldap-installer-screenshot.jpg")
[mirror]("http://img8.imageshack.us/img8/4145/easyldapinstallerscreen.jpg")


**Download link: **
[http://easyldap.exofire.net/files/installer/easyldap-installer.sh](http://easyldap.exofire.net/files/installer/easyldap-installer.sh)
(version alpha)

**Howto / how to start the program:**
> cd /tmp
wget "http://easyldap.exofire.net/files/installer/easyldap-installer.sh"
sudo easyldap-installer.sh
 
  
(Version alpha, in progress, please any help and continuing the code would be very welcome for the Linux community ! )

---

### Post by HermanAB on 2010-01-16
Yup, the Ubuntu server wizards still leave much to be desired.  The best server distributions with wizards for everything are still Mandriva, Suse and Red Hat - in that order.

Probably the best way to administer an Ubuntu server is with Usermin.

---

### Post by frenchn00b on 2010-01-17
> **HermanAB said:**
> Yup, the Ubuntu server wizards still leave much to be desired.  The best server distributions with wizards for everything are still Mandriva, Suse and Red Hat - in that order.

Probably the best way to administer an Ubuntu server is with Usermin.

Hi Hermann
Please could you check it. I worked on it, and added several services. I still have to make LDAP+Kerberos+samba together, jailkit ssh, and many more. 

Is the program better now? 


[http://easyldap.exofire.net/files/installer/easyldap-installer.sh](http://easyldap.exofire.net/files/installer/easyldap-installer.sh)
 
[screenshot]("http://easyldap.exofire.net/files/installer/shot01.jpg")

---

