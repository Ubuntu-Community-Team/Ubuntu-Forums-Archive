---
title: "TLS errors delaying authentication"
date: 2012-06-21
forum: Server Platforms
---

### Post by allaboutmike on 2012-06-21
I have setup the LDAP server as per official Ubuntu documentation. It appears to work fine when I manually user ldapsearch and returns all the information I expect.
When I login to the server, either locally or through SSH, there is a long (1-2 minute) pause before the authentication succeeds and I can log in.
During this time, the server syslog gets many repeats of this:

[SIZE="1"]Jun 21 15:31:47 skyserver slapd[10310]: conn=1098 op=0 STARTTLS
Jun 21 15:31:47 skyserver slapd[10310]: conn=1098 op=0 RESULT oid= err=0 text=
Jun 21 15:31:48 skyserver slapd[10310]: conn=1098 fd=25 closed (TLS negotiation failure)
Jun 21 15:31:49 skyserver slapd[10310]: conn=1099 fd=25 ACCEPT from IP=127.0.0.1:53084 (IP=0.0.0.0:389)
Jun 21 15:31:49 skyserver slapd[10310]: conn=1099 op=0 EXT oid=1.3.6.1.4.1.1466.20037
Jun 21 15:31:49 skyserver slapd[10310]: conn=1099 op=0 STARTTLS
Jun 21 15:31:49 skyserver slapd[10310]: conn=1099 op=0 RESULT oid= err=0 text=
Jun 21 15:31:50 skyserver slapd[10310]: conn=1099 fd=25 closed (TLS negotiation failure)
Jun 21 15:31:51 skyserver slapd[10310]: conn=1100 fd=25 ACCEPT from IP=127.0.0.1:53085 (IP=0.0.0.0:389)
Jun 21 15:31:51 skyserver slapd[10310]: conn=1100 op=0 EXT oid=1.3.6.1.4.1.1466.20037
Jun 21 15:31:51 skyserver slapd[10310]: conn=1100 op=0 STARTTLS
[/SIZE]

After that, I see some searches performed on my uid and they return entries that obviously allow nssldap (or pamldap?) to authenticate me.

Does anyone have any idea on what is going wrong and where I should look for clues?
Thanks 
Mike

---

### Post by luvshines on 2012-06-23
> When I login to the server, either locally or through SSH, there is a long (1-2 minute) pause before the authentication succeeds and I can log in

What is the authentication source for your ldap server ?
I mean are you logging in to your ldap server through ssh/login using the ldap user or some local user on the machine on which ldap server has been hosted ?

```
egrep "^passwd|^group" /etc/nsswitch.conf
```

---

### Post by allaboutmike on 2012-07-10
Sorry about the slow response, I've been out of town...

> **luvshines said:**
> What is the authentication source for your ldap server ?
I mean are you logging in to your ldap server through ssh/login using the ldap user or some local user on the machine on which ldap server has been hosted ?

Either. I can log in as either a local user (eg root) or an ldap directory user successfully. They just take ages.
> 
```
egrep "^passwd|^group" /etc/nsswitch.conf
```

```
root@skyserver:~# egrep "^passwd|^group" /etc/nsswitch.conf
passwd: files ldap
group: files ldap

```

Seems right?
Mike

---

### Post by luvshines on 2012-07-12
So are you trying to login using an ldap user or a local user defined on the box ?

---

### Post by allaboutmike on 2012-07-27
luvshines, I can log in with either a local (defined in /etc/passwd only) user or with a user account which is only defined in the ldap directory. It makes no difference, they both work. The problem is, they are both delayed by that minute or so. (or they were until I gave up and disabled TLS)
What I assume was happening: the pam stack or nsswitch (not totally sure of the order of precessing in there) was trying to connect to the ldap service (it's on the same machine) and was trying to do it securely first. When that failed enough times, it seemed to connect anyway (not securely?) and then work.
I was trying to do the right thing and make TLS work, but there was too much time pressure, so I gave up. 
Sorry for the lack of feedback here.
If you have any thoughts on what was wrong with the TLS setup, I could revisit this.

---

