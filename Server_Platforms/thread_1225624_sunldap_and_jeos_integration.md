---
title: "sunldap and jeos integration"
date: 2009-07-28
forum: Server Platforms
---

### Post by upengan78 on 2009-07-28
Hello,
 
I am sure this is discussed many a times but googling did not help me much. 
 
Basically we have a sun ldap server and jeos 8 as ldap client.
 
To set up the client on jeos , followed this document here : [https://help.ubuntu.com/community/SunLDAPClientAuthentication](https://help.ubuntu.com/community/SunLDAPClientAuthentication) 
 
Even though the ldap user can login to Jeos, the connection does not use ssl which is one issue for me. Secondly, the user's home directory does not get mounted on the ldap client. 
 
At the moment having user's home directory mounted would be priority for me. Any help is appreciated and I will be happy to provide any more details if needed.
 
>  
# su - ldapuser
No directory, logging in with HOME=/
ldapuser@client:/$
 

 
Thanks in advance.

---

### Post by samosamo on 2009-07-28
ldap client settings are stored in /etc/ldap.conf.  Read more about it on how to use an SSL connection.

As for the home directory problem, can you give more info?  What is your network configured for?  NFS directories?  Local directories?  Don't just guess, post proof.

---

### Post by upengan78 on 2009-07-29
> **samosamo said:**
> ldap client settings are stored in /etc/ldap.conf. Read more about it on how to use an SSL connection.
 
As for the home directory problem, can you give more info? What is your network configured for? NFS directories? Local directories? Don't just guess, post proof.
 
ok regarding home directory only,
 
Well I have already shown in the quote that home directory for user is not there on the client when user logs in. Also the link I used to configure does not have any info about configuring home directories, does it? So I have not configured anything on the client side other than LDAP authentication. I don't see anything in the logs on client as well as server. 
 
As far as ldap server configuration, the user is set to have home directory on a nfs server:/home/dir/path. 
 
I am ready to post and already shown willingness for that but there is nothing in the logs so let me know exactly what information or output (proof) should I post.
 
Isn't there a standard procedure for nfs mounting ldap users directories on clients using autofs? :)
 
Thanks for your help.

---

### Post by upengan78 on 2009-07-29
> ldaplist -l auto_home
dn: automountkey=ldapuser,automountmapname=auto_home,dc=sub,dc=domain,dc=com
        automountKey: ldapuser
        objectClass: automount
        objectClass: top
        automountInformation: -fstype=nfs,rw,intr nfs.sub.domain.com:/nfs/ldapuserNFS share is running fine. shared as below,
> share
-               /nfs/   root=clientIP,rw=clientIP   ""> hosts.allow on server
ALL: clientIP

hosts.allow client has ALL : NFS and LDAP serverIPsOn the client's auto.master file I tried putting below 

> /home ldap:automountkey=ldapuser,automountmapname=auto_home,dc=sub,dc=domain,dc=com
and restarted autofs but that did NOT mount user's home directory from nfs when ldapuser did login.

Just trying to provide more info. Thanks

---

### Post by jlattus on 2011-06-03
Did you load a portmapper?  I had the exact same problem trying to mount home directories and it turned out that I had neglected to load the portmapper.  I believe the package was portmap-6.0.0-2ubuntu5.  My two cents.  Hope it helps

---

### Post by upengan78 on 2011-06-03
It's been long time :)

Issue was resolved by using correct automount schema on SUN ldap side. I don't understand why linux and solaris have different standards for LDAP schemas, i.e auto_mount/auto.mount :D

Thanks!

---

