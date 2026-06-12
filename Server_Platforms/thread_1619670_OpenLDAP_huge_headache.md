---
title: "OpenLDAP huge headache"
date: 2010-11-12
forum: Server Platforms
---

### Post by slooksterpsv on 2010-11-12
EDIT:
So I still don't have it working in Ubuntu, if you read #7 I got it working in OpenSuSE, but I did get Ubuntu as a client on it. You have to excuse the harshness of my language and take towards LDAP and Ubuntu.

I had been working on it for 16 hours, tried on Fedora, etc. none of it worked, following guides closely, but running into errors. I was speaking out of anger, but I'll try to get Ubuntu LDAP working again and that. Now that I've got it working in OpenSuSE and manually configured Ubuntu as a client more of it makes sense for what I need to do to fix what issues I ran into.

Again all I apologize where I come off harsh in the original text below. Just understand playing with it for 16 hours and getting no where is stressful haha.

Original Post:

Ok, officially, Ubuntu and OpenLDAP is the worst! I'm very frustrated right now so I apologize in advance. I've been through 6 different guides to try and get ldap to work on ubuntu, NONE work. It's all garbage, same with OpenLDAP. Some how it's so screwed up that when you do dpkg-reconfigure, it doesn't completely reconfigure slapd.

I cannot create a user or even inject a user for ldap. it gives me an error about no secret in database, I've looked up the errors, had it not use SASL and use base users, and it still fails. Here's a few guides (that I still have open) that I've went through

POS
[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)
[http://www.debuntu.org/ldap-server-and-linux-ldap-clients](http://www.debuntu.org/ldap-server-and-linux-ldap-clients)


I get here: sudo ldapadd -x -D cn=admin,dc=example,dc=com -W -f frontend.example.com.ldif

and it gives me:
ldap_bind invalid credentials (49)

I'm so through, hopefully someone can give me some advice or suggestions of things to try, otherwise I'll find a different distro that work! Fedora I almost had it working, but the ldap items weren't in it; so I thought I know Ubuntu it works great let's try it. No it doesn't. I don't know if there's something they didn't document (probably) cause I just installed a fresh install of 10.04 on a vbox, and started that guide.

JUNK!

---

### Post by luvshines on 2010-11-12
> **slooksterpsv said:**
> Ok, officially, Ubuntu and OpenLDAP is the worst! I'm very frustrated right now so I apologize in advance. I've been through 6 different guides to try and get ldap to work on ubuntu, NONE work. It's all garbage, same with OpenLDAP. Some how it's so screwed up that when you do dpkg-reconfigure, it doesn't completely reconfigure slapd.

I cannot create a user or even inject a user for ldap. it gives me an error about no secret in database, I've looked up the errors, had it not use SASL and use base users, and it still fails. Here's a few guides (that I still have open) that I've went through

POS
[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)
[http://www.debuntu.org/ldap-server-and-linux-ldap-clients](http://www.debuntu.org/ldap-server-and-linux-ldap-clients)


I get here: sudo ldapadd -x -D cn=admin,dc=example,dc=com -W -f frontend.example.com.ldif

and it gives me:
ldap_bind invalid credentials (49)

I'm so through, hopefully someone can give me some advice or suggestions of things to try, otherwise I'll find a different distro that work! Fedora I almost had it working, but the ldap items weren't in it; so I thought I know Ubuntu it works great let's try it. No it doesn't. I don't know if there's something they didn't document (probably) cause I just installed a fresh install of 10.04 on a vbox, and started that guide.

JUNK!

Did you set a rootPw for LDAP rootDn since invalid credentials show that rootDn and rootPw don't match

---

### Post by david.garceau on 2010-11-12
[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)

This is pretty thorough

---

### Post by luvshines on 2010-11-12
Simplest method would be to go for the orthodox method of /etc/ldap/slapd.conf file, include everything in that and stay out of trouble and headaches ;)

---

### Post by slooksterpsv on 2010-11-12
Yeah I got it, had to comment out the line about back_hdb it won't load the module. So far I'm slowly getting closer I think, I'll post back here with Other issues I run into.

---

### Post by slooksterpsv on 2010-11-12
I give up, no documentation is consistent you have to work out your own errors, the configuration process is way way way too long. I can go out and get an older version of Windows Server or Mac OS X server and have that work better than Linux.

I'm very disappointed in Linux and the LDAP server market, it's very very very poor and has lost quite a few points in my book. I've read countless threads where people ask the same questions I'm asking, but no responses, it's like my signature, go into an IRC Chatroom 300 people there, you ask a question no one responds or helps you out. What's the point of 300 people being in there if no one helps?

Desktop wise, Ubuntu is still amazing same with the support for the Desktop. Web Server, file server, still amazing. 
Samba and LDAP sucks for user authentication on Windows machines and LDAP on Linux machines too! Too too much configuration, if I wanted to configure my whole OS I'd use slackware and compile my own dependencies. Fedora didn't even work either.

Again I'm still frustrated with all this.

---

### Post by slooksterpsv on 2010-11-13
OpenSuSE is my LDAP Server, it was so easy to setup and it works flawlessly. I've even been able to setup Ubuntu as an LDAP Client - still working on the NFS4 shares for the home folder, but it's working really well. =D

---

### Post by Versusnja on 2010-11-19
Hi!

Same problem here.
I follow the tutorial [https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)

And when I reach the line about adding frontend LDIF to the directory with
```
sudo ldapadd -x -D cn=admin,dc=example,dc=com -W -f frontend.example.com.ldif
```

the server replies

```
Enter LDAP Password: 
ldap_bind: Invalid credentials (49)

```

And yes, I changed the password in olcRootPW: secret
to my own. (btw, should it be plaintext password ot generated with ldappasswd?)

So, I can't move forward and I can neither roll-back since I don't know how to empty the directory to start over. 

please help.

---

### Post by Versusnja on 2010-11-19
This might give an idea as well:
[http://serverfault.com/questions/171965/ubuntu-10-04-lucid-openldap-invalid-credentials-issue](http://serverfault.com/questions/171965/ubuntu-10-04-lucid-openldap-invalid-credentials-issue)

i'm trying this now.

---

### Post by slooksterpsv on 2010-11-19
Let me know cause I tried a lot of those that had me put the password in like that, and it failed. That's why I really liked OpenSuSE, besides being graphical, it was easy to setup. I even had a NFS fileshare for user home directories.

---

### Post by flash007 on 2010-11-19
Wow!  Such frustrations and headaches, judging by the posts!  Sorry you had such a rough time of it!  Well, I got the ubuntu 10.04 ldap server and the client to work!  I had to do this for a company along with a full email server on ubuntu 10.04.  And THEY both work!  I'm finishing up the documentation such that anyone (in this company) can successfully get it installed, configured and tested in under 2 hours.  Both Server and Client are VM machines.  There are over 500 user accounts created.  Started with a txt file of 500 Harry Potter character names.  Created the script that read this and converted it to an ldif file which I used to create the ldap accounts with.     I used a couple of discussion forums but mostly I used these 3 basic URL's:
 
[http://www.cs.wcupa.edu/~rkline/Ubuntu/ldap.html](http://www.cs.wcupa.edu/~rkline/Ubuntu/ldap.html)
[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)
[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)
 
Of course, there were a few things I had to figure out on my own, but no worries.  How can I help?

---

### Post by slooksterpsv on 2010-11-19
Ok for 10.04 server that worked flawlessly. I followed one guide and got it to work - now to manually configure NFS and that. Wow, so 10.10 has ldap issues.
[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)

---

### Post by slooksterpsv on 2010-11-19
All,

I was having trouble authenticating with a Ubuntu client to my Ubuntu server, here's how my ldap.conf file had to be setup in /etc - not sure what made it work but the larger config made it not work.

[php]
BASE    dc=domain, dc=com
scope sub
suffix          "dc=domain,dc=com"

rootbinddn cn=Manager,dc=domain,dc=com

timelimit 5
bind_timelimit 5
uri ldap://ldap.domain.com/
pam_password md5
ldap_version 3
pam_filter objectclass=posixAccount
pam_login_attribute uid
pam_member_attribute memberuid
[/php]

In case that helps anyone.

---

### Post by Versusnja on 2010-11-22
My problem was with the credentials. I didn't change the credentials in the below mentioned command to mine.
```
sudo ldapadd -x -D cn=admin,dc=[COLOR="DarkRed"]mydomain[/COLOR],dc=[COLOR="DarkRed"]com[/COLOR] -W -f frontend.example.com.ldif
```

---

### Post by me_sasirekha on 2010-12-06
Hi,


   I am newbie to ldap environment.I have installed openldap and started slapd.conf file to start ldap server.Next how to proceed to write code in java to interact with ldap server and perform different operations like search ,store and all.

Thanks in advance for quick response.
sasi

---

### Post by slooksterpsv on 2010-12-06
> **me_sasirekha said:**
> Hi,


   I am newbie to ldap environment.I have installed openldap and started slapd.conf file to start ldap server.Next how to proceed to write code in java to interact with ldap server and perform different operations like search ,store and all.

Thanks in advance for quick response.
sasi

No clue, instead of using this thread, I would highly recommend creating a new one under programming. Someone should be able to help with using like pam authentication to search ldap trees.

---

### Post by slooksterpsv on 2010-12-23
> **Versusnja said:**
> My problem was with the credentials. I didn't change the credentials in the below mentioned command to mine.
```
sudo ldapadd -x -D cn=admin,dc=[COLOR="DarkRed"]mydomain[/COLOR],dc=[COLOR="DarkRed"]com[/COLOR] -W -f frontend.example.com.ldif
```

Backend probably didn't import properly, mine didn't when I did it again. I had to add .la to back_hdb on the backend.example.com.ldif

---

