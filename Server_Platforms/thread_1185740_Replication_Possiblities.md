---
title: "Replication Possiblities"
date: 2009-06-12
forum: Server Platforms
---

### Post by XanTrax on 2009-06-12
Hi everyone,

I need to get some ideas for user account replication across multiple servers in the same network.

What I am trying to do is:

1.) Have a central server where users can have a shell and ftp access to
2.) This server will serve as their central hub for other services they have access to which include access to a web share, access to their roaming profile (via samba), access to an FTP share (hand in hand with web share), and other services such as those
3.) My idea is to, upon writing my own adduser script, have NFS (Network File Shares) to each of these shares on these separate servers, for instance:

A user executes "ls -al" from the central hub server in their home folder, in this case /home/test on the central hub:
```

ls -al
lrwxrwxrwx 1 test 26 2009-06-08 13:52 Maildir -> NFS://email-server.example.local:/home/test/Maildir
lrwxrwxrwx 1 test 26 2009-06-08 13:52 Webroot -> NFS://web-server.example.local:/var/www/test
lrwxrwxrwx 1 test 26 2009-06-08 13:52 Profile -> NFS://samba-server.example.local:/home/test/ftp

```

Now, I recognise that each of these NFS shares must have user name and passwords supplied accordingly.  So, to remedy this, I would like to replicate all the user accounts created on the central hub and passed to the other servers so that when the user logs into the central hub their password is sent for the NFS and they can access it accordingly.

I hope I have made this as clear as possible.

By the way, the automatic mounting of these Network file shares will be handled in fstab as well as /etc/skel

So, back to the primary question, how would I replicate users and passwords from /etc/shadow and /etc/passwd and /etc/groups without direct rsync since I want to avoid possible GUID and UID's already existing and there being a problem.  I want the user to have the same username and password for ALL servers in the network providing a specific service but I also need them to have noshell set in all of the other servers.  Now that I think of it, would having noshell set for the user on the separate server allow them to still have an accessible NFS?

EDIT: I dont really want to use LDAP for this sort of thing...I was looking at: [https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo) but it seems to be kinda insecure as compared to LDAP?

---

### Post by scorp123 on 2009-06-12
> **XanTrax said:**
>  EDIT: I dont really want to use LDAP for this sort of thing... And why?? :confused:

> **XanTrax said:**
>  I was looking at: [https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo) but it seems to be kinda insecure as compared to LDAP? NIS is insecure and hopelessly outdated. If I had to do what you wrote up there I'd use LDAP and NFS, so the users can login everywhere and always get their same home directories.

[http://en.wikipedia.org/wiki/Network_Information_Service](http://en.wikipedia.org/wiki/Network_Information_Service)

" .... Administrators have the ability to configure NIS to serve password data to outside processes to authenticate users; however, not only is this cumbersome to do without resorting to DES encrypted passwords (which are known to be weak), **_it also allows any NIS client to retrieve the entire password database for offline inspection._** ... "

Ouuuuch. So anyone having access to your NIS setup can get all the passwords from all users and then use a password cracker program to get all passwords from all users. Double oouuuuch.

That's precisely why nobody is using NIS anymore. Please use LDAP.

---

### Post by XanTrax on 2009-06-12
> **scorp123 said:**
> And why?? :confused:

 NIS is insecure and hopelessly outdated. If I had to do what you wrote up there I'd use LDAP and NFS, so the users can login everywhere and always get their same home directories.

[http://en.wikipedia.org/wiki/Network_Information_Service](http://en.wikipedia.org/wiki/Network_Information_Service)

" .... Administrators have the ability to configure NIS to serve password data to outside processes to authenticate users; however, not only is this cumbersome to do without resorting to DES encrypted passwords (which are known to be weak), **_it also allows any NIS client to retrieve the entire password database for offline inspection._** ... "

Ouuuuch. So anyone having access to your NIS setup can get all the passwords from all users and then use a password cracker program to get all passwords from all users. Double oouuuuch.

That's precisely why nobody is using NIS anymore. Please use LDAP.

I guess it was pretty silly of me to consider NIS over LDAP.  I guess I just felt that LDAP was a little too much for the simplicity of what I wanted (like rsync, without the worries).  I guess LDAP will be the way to go.  Also, my primary thing too was to make sure that they have noshell on all other servers except for the central hub.  With LDAP, am I able to specify such options or would I need to write a standalone cronjob or something that parses the /etc/passwd file and makes appropriate changes from /bin/bash to /bin/noshell in the passwd file?

So, to reiterate, I want the users to be replicated, specifically only in the sense of the username, password, and group across the servers and ensure that all the users are locked out of the other servers and must access their stuff via their shares in the central hub.

Possible:

Have LDAP to replicate the users with their passwords and other assorted information.  Then, have a cronjob parse the /etc/passwd file for /bin/bash and, based on the user, change it accordingly to /bin/noshell

Sound like a plausible idea?

---

### Post by scorp123 on 2009-06-12
> **XanTrax said:**
>  I guess I just felt that LDAP was a little too much for the simplicity of what I wanted You could use a distro such as "eBox" ([http://ebox-platform.com/](http://ebox-platform.com/)) as server ... with it you get a easy-to-use web interface and you'd configure everything there.

Or you could use Novell SLES 11 (easy to use too) or OpenSUSE 11 (still easy to use and configure).

If you really really want to use Ubuntu then this will involve some manual work. Please see this super-super long thread:
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

That thread was originally written with Ubuntu 7.10 in mind, but it should still work. It's a bit of a hassle to configure all those files (this stuff is done more or less automagically in SLES 11 or OpenSUSE 11).


> **XanTrax said:**
>  (like rsync, without the worries).  What do you need rsync for? Use NFS for the home directories! :)

> **XanTrax said:**
>  With LDAP ...  ... you don't touch /etc/passwd at all. That file is irrelevant as far as LDAP is concerned. ;)

> **XanTrax said:**
>  am I able to specify such options  If a user object is lacking the POSIX schema, then it would be unable to login into a Unix-like system such as a Linux LDAP-client system. So the answer is yes ... except it works different from what you suggest here. I suggest you refresh your knowledge on LDAP and how it works. :)

The cool thing with the LDAP schemas is that a user could have the "NT-user" attributes, and/or the "POSIX-account" attributes, or none of the two. Depending what's configured a user could therefore login to Windows system (where the "Primary Domain Controller" role is in fact handled by the LDAP-Server .... Novell SLES 11 does all that pretty much automagically) or into a Unix-system ... or into no system at all (useful if they just need to authenticate e.g. for a web portal but actually don't need to be able to login ...)

> **XanTrax said:**
>  or would I need to write a standalone cronjob or something that parses the /etc/passwd file and makes appropriate changes from /bin/bash to /bin/noshell in the passwd file?  See above. LDAP doesn't really care about those files, it uses its own mechanisms to keep track of user accounts. And even if: What you suggest sounds like a bad idea. 

Example LDAP search (as root):
```
ldapsearch -b "dc=mycompany,dc=net" -L -s sub -D "cn=administrator,dc=mycompany,dc=net" -h localhost -W -x

``` ... returns a lot of output; amongst it are entries like this one:

```
# johndoe, people, mycompany.net
dn: uid=johndoe,ou=people,dc=mycompany,dc=net
cn: John Doe
gidNumber: 5000
givenName: John
homeDirectory: /home/johndoe
**[COLOR="Red"]loginShell: /bin/bash[/COLOR]**
objectClass: top
[COLOR="Red"]**objectClass: posixAccount**[/COLOR]
objectClass: inetOrgPerson
objectClass: sambaSamAccount
objectClass: shadowAccount
sambaAcctFlags: [U          ]
sambaPrimaryGroupSID: S-1-5-21-0011108314-2407543925-1328701488-11001
sambaPwdCanChange: 1238348340
sambaPwdMustChange: 2147483647
shadowInactive: -1
shadowLastChange: 14332
shadowMax: 99999
shadowMin: 0
shadowWarning: 7
sn: Doe
uid: johndoe
uidNumber: 5026
sambaSID: S-1-5-21-1000000-0004-2407543925-1328701488-21026
sambaPasswordHistory: 00000000000000000000000000000000000000000000000000000000
 00000000
sambaLMPassword: ABCDEFABCDEFABCDEFABCDEFABCDEFAB
sambaNTPassword: FABCDEFABFABCDEFABFABCDEFABFABCD
sambaPwdLastSet: 1238594186
userPassword:: =soMeEnCryptEdBSr1gHtHere=
```

The presence of the "posixAccount" attribute defines if a user account is able to login or not into a Unix-like LDAP client (such as Linux), and the "loginShell" attribute defines the shell a user would get.

This is all done and handled by LDAP ... and not by some file which you shoulnd't be messing around with manually anyway ;)

> **XanTrax said:**
>  So, to reiterate, I want the users to be replicated LDAP replication? Or do you just want to have the same users everywhere (= no need for "replication")?


> **XanTrax said:**
>  specifically only in the sense of the username, password, and group across the servers "across the servers"?? What you mean is: 1 x LDAP Server; the rest authenticates against this server ... right?

> **XanTrax said:**
>  and ensure that all the users are locked out of the other servers  If they don't have a (local) account there, then they would not be able to login there anyway.

> **XanTrax said:**
>  and must access their stuff via their shares in the central hub.  See above. You can't login to a system if you don't have an account there. So if they only get an LDAP-account on the few systems that are actually configured to accept LDAP-users then this will be precisely all they will be able to access.

> **XanTrax said:**
>  Have LDAP to replicate the users with their passwords and other assorted information.   To another LDAP server, e.g. to achieve high-availability and redundancy? If you just want to have a central place where the usernames and passwords are stored then there is no "replication", LDAP does that already. All other machines have to be configured as "LDAP clients". When someone logs into those "clients" then the process goes and asks the central server if it knows this user or not. That's it. If the LDAP has that account you get access ... if not: Access denied, bye bye.

> **XanTrax said:**
>   Then, have a cronjob parse the /etc/passwd file for /bin/bash and, based on the user, change it accordingly to /bin/noshell .... Sound like a plausible idea? Nope, not at all :D

---

