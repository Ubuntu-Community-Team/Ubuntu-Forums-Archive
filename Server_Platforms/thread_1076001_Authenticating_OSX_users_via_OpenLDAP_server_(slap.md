---
title: "Authenticating OSX users via OpenLDAP server (slapd)"
date: 2009-02-20
forum: Server Platforms
---

### Post by samosamo on 2009-02-20
I am at my wits end trying to configure OSX users to authenticate against an OpenLDAP server which already works for other linux boxes.

I used "Directory Utility" to add the server.  It automatically populated the DN and it appears to have configured successfully.  I am able to search for users using "dscl" and "id" and "finger" but when it comes to authenticating, there is trouble in LDAPland.

SSH errors look like so:
```
$ sudo tail -f -n 0 /var/log/secure.log
Feb 19 22:53:49 iMac com.apple.SecurityServer21: checkpw() returned -2; failed to authenticate user elvis (uid 1002).
Feb 19 22:53:49: --- last message repeated 1 time ---
Feb 19 22:53:49 iMac com.apple.SecurityServer21: Failed to authorize right system.login.tty by client /usr/sbin/sshd for authorization created by /usr/sbin/sshd.
Feb 19 22:53:49 iMac sshd2470: error: PAM: Authentication failure for elvis from XXXXXXXXXXXXXXX
```

I know Apple is finicky in mixed-environments.  I know I'm missing something, I just don't know what. If you were successful at this, would you be so kind as to post your slapd.conf and any extra steps you took when configuring the OSX client?  I am working with OSX 10.5 Leopard.

---

### Post by samosamo on 2009-02-22
ttt

---

### Post by samosamo on 2009-02-23
ttt

---

### Post by samosamo on 2009-02-25
ttt

---

### Post by samosamo on 2009-02-27
ttt

---

### Post by samosamo on 2009-03-08
ttt

---

### Post by GabrielSyme on 2009-04-06
I would *really* like some insight on this too, if there is the knowledge out there. I can see the users with finger, but mac won't log them in!

---

### Post by samosamo on 2009-04-10
I fixed it myself.  It's the usual LDAP setup for auth.  You know what the problem was?  I wasn't clearing the "Directory Services" cache before testing, so even if I fixed it, the cache had the old wrong settings.

[http://www.emmes-world.de/mac-afp-homes.html](http://www.emmes-world.de/mac-afp-homes.html)

Basically I used these directions, but without the need for apple.schema because I was using local home directories.  The trick is to always do "dscacheutil -flushcache" before testing.  This is how I would test each time:

> $ dscacheutil -flushcache && su user

Here is another great tip: If you wish to use local home directories, use Directory Utility to remap "NFSHomeDirectory" under "User" to this: #/User/$uid$

---

### Post by GabrielSyme on 2009-04-13
samosamo, I am glad to hear that you were able to get this working (that means it *can* be done!). I am still having trouble getting this set up. I have my ldap server added in the directoryutility.app, with default mappings with "RFC 2307 Unix". I am *not* using ssl. I can finger and list (with dscacheutil) users who are not local users on the computer. They just won't log in! I keep flushing the cache and trying an su. I've also tried rebooting and logging in from the login screen, to no avail. This is my error from /var/log/secure.log :
```
Apr 13 09:08:53 Adama-3 com.apple.SecurityServer[23]: checkpw() returned -2; failed to authenticate user strongbad (uid 30007).
Apr 13 09:08:53: --- last message repeated 1 time ---
Apr 13 09:08:53 Adama-3 com.apple.SecurityServer[23]: Failed to authorize right system.login.tty by client /usr/bin/su for authorization created by /usr/bin/su.
Apr 13 09:08:54 Adama-3 su[13293]: pam_authenticate: Authentication failure
```

This is my output for an ldap user *dscacheutil -q user -a name strongbad*:
```
name: strongbad
password: 
uid: 30007
gid: 513
dir: /home/strongbad
shell: /bin/bash
gecos: strongbad
```

And this is the output for a local user:
```
name: tkrell
password: ********
uid: 503
gid: 503
dir: /Users/tkrell
shell: /bin/bash
gecos: Timothy Krell
```

I've noticed that there aren't any asterixs displaying for the ldap users' passwords. The ldap users' passwords are hashed with SSHA, however I also have a user with a cleartext password. Both will not login in. Any ideas? It seems like I am so close, but I can't get past this! Thanks for your help so far.

---

### Post by samosamo on 2009-04-17
Once I figured out I had to flush cache when testing, it was as simple as setting up any other client machine.  What steps did you take to configure the client?  Can you tell me more about the LDAP server?  Sorry for the slow responses. I only visit this forum once in a while.

---

### Post by GabrielSyme on 2009-04-20
I set up the client by launching the directory utility app. I edited the ldap3 service and clicked "new". I typed in the server's IP address, chose "RFC Unix" for the mappings and and clicked OK with out checking the SSL box. 

On the LDAP side, I set up the LDAP server using the smbldap-tools to populate the directory. I don't have the apple.schema set up. It seems like it should "just work", and I can't seem to pin point what is going wrong. I set up LDAP following this tutorial [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

> **samosamo said:**
> Sorry for the slow responses. I only visit this forum once in a while.
No problem! I appreciate you taking the time at all! :D

---

### Post by samosamo on 2009-04-28
DOH!  I just set up a second client and had the same problem all over again!  After wasting ANOTHER day on this issue, because I did not correctly document the first time I fixed it, I figured it out... again

In Directory Utility, when entering a new LDAP server, you must hit "Manual."  Fill out all the info manually.  MANUALLY.  I don't know why it makes a difference but it does.  Do not automatically configure it.  The search base is dc=mydomain,dc=com.  The mapping should be RFC UNIX preset and make your changes from there if needed.

And you're right, there is no need for the apple schema as long as you use my method of local directories.  If you want AFP mounted directories you need it though.

---

### Post by samosamo on 2009-04-28
I should also mention that I am using an ubuntu-server configured like so: [https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html)

And I use Webmin's "LDAP Users and Groups" for user management which I really recommend.

---

