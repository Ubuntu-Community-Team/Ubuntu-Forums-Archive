---
title: "User managment and home dir-s synchronization"
date: 2008-03-11
forum: Server Platforms
---

### Post by madey on 2008-03-11
Hello,
I have this problem:
I've got 8 PC's and the server in the lab. Some peoples work in this lab and they use these computers computers.
I would like the to synchronize the users and passwords on this computers, means that I could add a new user to all the PC's at one time (on the server) and this user could login at all of the computers in the lab. And the second think: I also would like to store the home directories of this users at the server. The result should be that: if the user with an account comes to the lab he can login on the any of the PC's with his login:password and then his home directory synchronizes with the server data (or mounts NFS dir or whatever) and he can use this computer transparently (he shouldn't mount anything or make other actions except login). Then he can logoff, and do the same on the other computers. I saw once somethink like that but with Windows and Novell Netware but I need Linux.
Does anybody could tell me what kind of software I should use?? Please just tell what kind of software can do that, maybe some of you use this kind of config?
best regards
madey

---

### Post by koenn on 2008-03-11
The "single sign-on" you describe can be implemented with either
- OpenLDAP (possibly needs Kerberos also)
- Samba, if configured as a domain controller (NT4 PDC )

The 'roaming home directory' is  something that can be done with eiter
- Samba
- NFS

There are quit some threads around these forums that go in to this, and I'm quit sure you'll find suitable recipes / howto's in the wiki
Google also knows a lot, and samba has extensive documentation about this

[http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html#id2554595](http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html#id2554595)
[http://moduli.net/sysadmin/sarge-ldap-auth-howto.html](http://moduli.net/sysadmin/sarge-ldap-auth-howto.html)
[http://www.debianhelp.co.uk/nfs.htm](http://www.debianhelp.co.uk/nfs.htm)

---

### Post by madey on 2008-03-11
Thanks for fast answer.
What do you think which one would be better for a roaming home directory: NFS or Samba? I'm using Samba on another server and I had this feeling that it is little slow. What about NFS? I have never used it before. Which solutions you think would be better ?

---

### Post by koenn on 2008-03-11
can't tell, really
NFS is quite straightforward compaired to samba, and NFS shares integrate nicely into the linux directory tree with a plain mount / fstab entry. Samba can do the same, but with some help (smbmount). 
On the other hand, I don't know how well NFS integrates in a single sign-on / centran user management sollution. I take it your client are Linux / OSX systems -for Windows clients, NFS is not an option. 

Samba would give you the benefit that you use the same package for bot single-sign-on and file sharing. 


NFS + LDAP apperas at least do-able. had a quick look on Google and found this ;
[http://www-theorie.physik.unizh.ch/~dpotter/howto/kerberos](http://www-theorie.physik.unizh.ch/~dpotter/howto/kerberos)
It's RedHat oriented but at least shows you what it's all about so you can go hunt for Debian/Ubuntu info yourself. 
NFS+LDAP is probably more complex to set up ; that's because these protocols were designed to be flexible  and scalable, to be able to still work in a large environment and to let you design a sollution that fits your requirements (whereas Samba's main objective is : compatibility with Windows). 

If it was my problem, I'd either
- choose the samba all-in-one approach if my main goal was to get a working sollution quickly and easily, and be done with it

- go for the NFS, Kerberos, LDAP sollution
* to learn how it's done
* if for some reason a native Linux sollution was preferable
* in a verry large environment or if scalability was really an important issue

---

### Post by rickyjones on 2008-03-11
I have an article that will do this for you. Ubuntu Server and Linux/Windows clients will work.

[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

-Richard

---

### Post by madey on 2008-03-12
thianks all of you for help, I have already installed today and it it works great (LDAP + NFS) it is what I exactly need.

---

