---
title: "SSH + Radius + LDAP"
date: 2013-08-24
forum: Security
---

### Post by Kevin_Lopez on 2013-08-24
I have been doing a lot of research on ssh (openssh) and radius.

What I want to do:

SSH in to equipment with credentials (username and password) stored in either on a radius server or ldap store. I have been reading online and some people point to having an ldap server running in the background of your radius server. This will work, but will only work if the user is found in the local machine.

The problem:
Is there a way for me to ssh (or telnet) in to my equipment by logging in via a radius server that contains the credentials? if not is there a way for the client (the machine I am trying to connect to) get an updated list of credentials and store it locally from a central location (whether it be a radius server or an sql database etc).

I have been able to connect via Radius but only on accounts that are local, but for example if I try to connect with an account that does not exist locally (client-wise) I get "incorrect"

Here is the radius output:
```
rad_recv: Access-Request packet from host 192.168.4.1 port 5058, id=219, length=85	User-Name = "klopez"
	User-Password = "\010\n\r\177INCORRECT"
	NAS-Identifier = "sshd"
	NAS-Port = 4033
	NAS-Port-Type = Virtual
	Service-Type = Authenticate-Only
	Calling-Station-Id = "192.168.4.200"



```
```
[ldap] performing user authorization for klopez[ldap] WARNING: Deprecated conditional expansion ":-".  See "man unlang" for details
[ldap]     ... expanding second conditional
[ldap]     expand: %{User-Name} -> klopez
[ldap]     expand: (uid=%{Stripped-User-Name:-%{User-Name}}) -> (uid=klopez)
[ldap]     expand: dc=lab,dc=local -> dc=lab,dc=local
  [ldap] ldap_get_conn: Checking Id: 0
  [ldap] ldap_get_conn: Got Id: 0
  [ldap] performing search in dc=lab,dc=local, with filter (uid=klopez)
[ldap] No default NMAS login sequence
[ldap] looking for check items in directory...
  [ldap] userPassword -> Cleartext-Password == "somepass"
  [ldap] userPassword -> Password-With-Header == "somepass"
[ldap] looking for reply items in directory...
[ldap] user klopez authorized to use remote access
  [ldap] ldap_release_conn: Release Id: 0
++[ldap] returns ok
++[expiration] returns noop
++[logintime] returns noop
[pap] Config already contains "known good" password.  Ignoring Password-With-Header
++[pap] returns updated
Found Auth-Type = PAP
# Executing group from file /etc/freeradius/sites-enabled/default
+- entering group PAP {...}
[pap] login attempt with password "?  INCORRECT"
[pap] Using clear text password "somepass"
[pap] Passwords don't match
++[pap] returns reject
Failed to authenticate the user.
  WARNING: Unprintable characters in the password.  Double-check the shared secret on the server and the NAS!
Using Post-Auth-Type Reject
# Executing group from file /etc/freeradius/sites-enabled/default
+- entering group REJECT {...}
[attr_filter.access_reject]     expand: %{User-Name} -> klopez
attr_filter: Matched entry DEFAULT at line 11
++[attr_filter.access_reject] returns updated
Delaying reject of request 3 for 1 seconds



```

I also have pam_radius installed, and its working (can log in on a account that exists locally). Although I read this and do not know if this is 100% accurate:
[http://freeradius.1045715.n5.nabble.com/SSH-authendication-with-radius-server-fails-if-the-user-does-not-exist-in-radius-client-td2784316.html](http://freeradius.1045715.n5.nabble.com/SSH-authendication-with-radius-server-fails-if-the-user-does-not-exist-in-radius-client-td2784316.html)
and
[http://fhf.org/archives/713](http://fhf.org/archives/713)

tl:dr:
I need to ssh into a machine that does not have a user/pass locally and that combination will be stored remotely, such as a radius server or ldap.

please advise

P.S.

The solution is preferable using radius server or ldap but not necessary. If there is an alternate please advise.

Thanks,

Kevin

---

### Post by bab1 on 2013-08-26
> **Kevin_Lopez said:**
> I have been doing a lot of research on ssh (openssh) and radius.

There seems to be plenty of information about storing ssh keys using LDAP.  I used the search terms "ssh keys stored LDAP" and [**_[COLOR="#0000FF"]here[/COLOR]_**]("https://www.google.com/search?q=ssh+keys+stored+ldap&btnG=Go!") is what I got.
> 
What I want to do:
SSH in to equipment with credentials (username and password) stored in either on a radius server or ldap store. I have been reading online and some people point to having an ldap server running in the background of your radius server. This will work, but will only work if the user is found in the local machine.

You shouldn't need two repositories of authentication (LDAP or RADIUS).  They both do the same thing  but in different ways (e.g authenticate remote users).
> 
The problem:
Is there a way for me to ssh (or telnet) in to my equipment by logging in via a radius server that contains the credentials? if not is there a way for the client (the machine I am trying to connect to) get an updated list of credentials and store it locally from a central location (whether it be a radius server or an sql database etc)....

I don't believe RADIUS is the way to go in this instance.  Your experience kind of proves that.  The RADIUS server uses the local users database (passwd/shadow) to authenticate the user's remote login.
> 
tl:dr:
I need to ssh into a machine that does not have a user/pass locally and that combination will be stored remotely, such as a radius server or ldap.

P.S.
The solution is preferable using radius server or ldap but not necessary. If there is an alternate please advise.

Thanks,

Kevin
I think if you break down you will see that what you are trying to accomplish is this:
[LIST]
[*]Remote user login (LDAP)
[*]Remote user ssh key repository (LDAP (or a centralized SSH certificate))
[*]Remote users centralized home directory (NFS)
[/LIST]

The user needs to have a home directory to log in to a Linux host.  This can be achieved by mounting the users home directory via NFS from the same server that holds the LDAP user data.

All authentication is centralized along with also centralizing the users home directories on one dedicated server.  The local machine holds only the home directory mount point for the NFS exports of /home.

My previous experience with a setup like this was to have a key provided to me in my home dir at ~/exports/home/bab/.ssh.  I managed 100+ Solaris  workstations.  I could ssh to any of them.  I always had the same home directory.  The authentication was through  Sun iPlanet,  which is LDAP.  I know Linux, OpenLDAP and NFSv4 will be functionally the same. 

[COLOR="#0000FF"]**Edit:  **In looking at the SSH man pages I see that you ***can use a centralized SSH certificate.  See[/COLOR]***.
```
man ssh
... A variation on public key authentication is available in the form of certificate authentica&#8208;
     tion: instead of a set of public/private keys, signed certificates are used.  This has the
     advantage that a single trusted certification authority can be used in place of many pub&#8208;
     lic/private keys.  See the CERTIFICATES section of ssh-keygen(1) for more information.

```

[COLOR="#0000FF"]Plenty of variations with ssh, but you still need a home directory and LDAP user information for authentication.[/COLOR]

---

### Post by Kevin_Lopez on 2013-08-31
awesome, appreciate the help, I will be looking into this and getting it up and running!

---

