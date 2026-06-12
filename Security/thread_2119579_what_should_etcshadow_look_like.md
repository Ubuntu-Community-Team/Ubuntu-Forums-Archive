---
title: "what should /etc/shadow look like?"
date: 2013-02-24
forum: Security
---

### Post by lou21 on 2013-02-24
Quick question.. If the root user account is disabled what should the line in the /etc/passwd and /etc/shadow files look like?  I just noticed that my /etc/shadow line reads: ```
   root:!:number
```  ...  I thought that a logon disabled account should read    ```
name:*:number
``` ...  Thanks!

---

### Post by samiux on 2013-02-24
> **lou21 said:**
> Quick question.. If the root user account is disabled what should the line in the /etc/passwd and /etc/shadow files look like?  I just noticed that my /etc/shadow line reads: ```
   root:!:number
```  ...  I thought that a logon disabled account should read    ```
name:*:number
``` ...  Thanks!

In my opinion, you will be regretted for disabling the root account.

Samiux

---

### Post by thermion on 2013-02-24
Why would you want to disable the login for root?
Ubuntu comes pre-configured this way unless you run something like:

```
sudo bash
passwd
```

---

### Post by Ms. Daisy on 2013-02-24
> **lou21 said:**
> Quick question.. If the root user account is disabled what should the line in the /etc/passwd and /etc/shadow files look like?  I just noticed that my /etc/shadow line reads: ```
   root:!:number
```  ...  I thought that a logon disabled account should read    ```
name:*:number
``` ...  Thanks! It's not disabled, it's locked. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) 

From this: [http://manpages.ubuntu.com/manpages/intrepid/man5/passwd.5.html](http://manpages.ubuntu.com/manpages/intrepid/man5/passwd.5.html)
> The encrypted password field may be blank, in which case no password is
       required to authenticate as the specified login name. However, some
       applications which read the /etc/passwd file may decide not to permit
       any access at all if the password field is blank. If the password field
       is a lower-case “x”, then the encrypted password is actually stored in
       the shadow(5) file instead; there must be a corresponding line in the
       /etc/shadow file, or else the user account is invalid. If the password
       field is any other string, then it will be treated as an encrypted
       password, as specified by crypt(3). so the ! indicates to me that the root password is encrypted.

---

### Post by prodigy_ on 2013-02-24
> **lou21 said:**
> root user account is disabled
It seems you're a little confused and I guess this is because you think root is like in-built Administrator account is Windows. In fact root is more like System in Windows. You can't really disable it.

---

### Post by thnewguy on 2013-02-24
The manual page for /etc/shadow reads

```

If the password field contains some string that is not a valid result of crypt(3), for instance ! or *, the user will not be able to use a unix password to log in (but the user may log in the system by other means).

```

In other words, to answer the original question, he * and ! characters are equivalent in this case. People will not be able to login as the root user. You and other users may be able to perform admin tasks using sudo, but the root account itself is locked.

---

### Post by lou21 on 2013-02-24
> **Ms. Daisy said:**
> It's not disabled, it's locked. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) 

From this: [http://manpages.ubuntu.com/manpages/intrepid/man5/passwd.5.html](http://manpages.ubuntu.com/manpages/intrepid/man5/passwd.5.html)
 so the ! indicates to me that the root password is encrypted.

  That line I quote in the original question is from /etc/shadow NOT /etc/passwd. The line in /etc/passwd looks like: ```
root:x:0:0:root:/root:/bin/bash
``` Which I know points to the /etc/shadow file for a potential pass word.

---

### Post by lou21 on 2013-02-24
OK clearly I didn't express myself very well in the first post.  First to be clear. I am referring to the /etc/shadow file. NOT to /etc/passwd.  So a better simpler question would be. What is the difference between a * and a ! in the password field of the /etc/shadow file on an Ubuntu 12.10 system?  I know that both of these imply that pass word baased logon is not possible. However, apparently on some systems the ! implies that key based logons are possible. In this case why is this possible on my ubuntu box?  I am asking why this file is not how I expected or remembered it being and I am wondering if someone has cracked my system.

---

### Post by lou21 on 2013-02-24
> **thermion said:**
> Why would you want to disable the login for root?
Ubuntu comes pre-configured this way unless you run something like:

```
sudo bash
passwd
```

 I personally never changed anything to do with root access. I never enabled nor disabled any sort of root logon.

---

### Post by matt_symes on 2013-02-24
Hi

You have not been hacked, as i have not.  the x's i added.

```
matthew-S206:/home/matthew/fxp % sudo grep root /etc/shadow
root:!:xxxx:x:xxxx:7:::
matthew-S206:/home/matthew/fxp % 
```

Kind regards

---

### Post by deadflowr on 2013-02-25
The ! symbol means the account is locked. In this instance locked and disable are synonymous.
When you lock a password, you ultimately disable it, as if you want to unlock it, you'll need to create a new one.
Or use the -u(unlock flag), in which case the old password will be re-enabled. But if, as it is in this case, you never set a password, then unlocking it would be moot, as you never knew what is/was.

---

### Post by lou21 on 2013-02-25
So the information I saw somewhere else (from google I have to admit) that the ! in the password field indicates a key based logon is possible is wrong then?

Good news. Thank you all and sorry that the original wording of the question was poor.

---

### Post by lou21 on 2013-02-25
> **matt_symes said:**
> Hi

You have not been hacked, as i have not.  the x's i added.

```
matthew-S206:/home/matthew/fxp % sudo grep root /etc/shadow
root:!:xxxx:x:xxxx:7:::
matthew-S206:/home/matthew/fxp % 
```Kind regards

Cool. It's good to see that my file is still in the default settings (as it should be). Thank you very much!

---

### Post by bodhi.zazen on 2013-02-26
The discussion here is for the most part spot on.

The ! and * symbols prevent root from logging in via a password.

You can obtain root access via several other means, however. This might include booting a live CD, booting to recovery mode, using sudo, logging in via ssh (keys) or kerberos. This list is incomplete , but hopefully you get the idea.

See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by lou21 on 2013-02-27
> **bodhi.zazen said:**
> The discussion here is for the most part spot on.

The ! and * symbols prevent root from logging in via a password.

You can obtain root access via several other means, however. This might include booting a live CD, booting to recovery mode, using sudo, logging in via ssh (keys) or kerberos. This list is incomplete , but hopefully you get the idea.

See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

 So that means that IF a remote desktop service of some type is installed and IF a shh key exists then a remote root logon would be possible?

---

### Post by schragge on 2013-02-27
From the manual page for [shadow(5)](http://manpages.ubuntu.com/manpages/precise/en/man5/shadow.5.html)
> 
Refer to [crypt(3)](http://manpages.ubuntu.com/manpages/precise/en/man3/crypt.3.html) for details on how this string is interpreted.

If the password field contains some string that is not a valid
result of [crypt(3)](http://manpages.ubuntu.com/manpages/precise/en/man3/crypt.3.html), for instance ! or *, the user will not be able
to use a unix password to log in (but the user may log in the
system by other means).

This field may be empty, in which case no passwords are required to
authenticate as the specified login name. However, some
applications which read the /etc/shadow file may decide not to
permit any access at all if the password field is empty.

A password field which starts with a exclamation mark means that
the password is locked. The remaining characters on the line
represent the password field before the password was locked.


In short, you can use any character outside the [a-zA-Z0-9./] set to lock password in */etc/shadow*. By convention, *passwd -l* uses **!** for it, and *passwd -u* strips the **!** prefix from locked password.

---

### Post by schragge on 2013-02-27
> **lou21 said:**
> So that means that IF a remote desktop service of some type is installed and IF a shh key exists then a remote root logon would be possible?The access for root over ssh can be disabled in the configuration file */etc/ssh/sshd_config*. From the manual page for [sshd_config(5)](http://manpages.ubuntu.com/manpages/precise/man5/sshd_config.5.html)
> 
**PermitRootLogin**
Specifies whether root can log in using ssh(1).  The argument
must be “yes”, “without-password”, “forced-commands-only” or
“no”.  The default is “yes”.

If this option is set to “without-password” password authentica-
tion is disabled for root.

If this option is set to “forced-commands-only” root login with
public key authentication will be allowed, but only if the
command option has been specified (which may be useful for taking
remote backups even if root login is normally not allowed).  All
other authentication methods are disabled for root.

If this option is set to “no” root is not allowed to log in.


---

### Post by bodhi.zazen on 2013-02-27
> **lou21 said:**
> So that means that IF a remote desktop service of some type is installed and IF a shh key exists then a remote root logon would be possible?

Depending on how ssh and your VNC is configured, yes. I listed other protocols in my post.

As indicated by schragge, you configure each service (ssh, kerberos, VNC, etc) to allow/restrict users, including root.

---

