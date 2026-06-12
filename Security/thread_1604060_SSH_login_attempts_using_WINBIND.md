---
title: "SSH login attempts using WINBIND ?"
date: 2010-10-23
forum: Security
---

### Post by fa2k on 2010-10-23
Hi,

I have an SSH server on my laptop, and I'm using the default configuration file, but I added "AllowUsers <myUserName>". I get lots of login attempts like the ones below in my /var/log/auth.log.

From Google, I find that **pam_winbind** allows some kind of Windows authentication. This leaves me with 2 questions. What does winbind do when I have not configured any Windows/Samba accounts? 
How can I turn it off?

```
Oct 23 20:01:49 muon sshd[24329]: User root from 201.116.17.163 not allowed because not listed in AllowUsers
Oct 23 20:01:49 muon sshd[24329]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.116.17.163  user=root
Oct 23 20:01:49 muon sshd[24329]: pam_winbind(sshd:auth): getting password (0x00000388)
Oct 23 20:01:49 muon sshd[24329]: pam_winbind(sshd:auth): pam_get_item returned a password
Oct 23 20:01:49 muon sshd[24329]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Oct 23 20:01:51 muon sshd[24329]: Failed password for invalid user root from 201.116.17.163 port 55957 ssh2
Oct 23 20:01:53 muon sshd[24397]: reverse mapping checking getaddrinfo for static.customer-201-116-17-163.uninet-ide.com.mx [201.116.17.163] failed - POSSIBLE BREAK-IN ATTEMPT!
Oct 23 20:01:53 muon sshd[24397]: User root from 201.116.17.163 not allowed because not listed in AllowUsers
Oct 23 20:01:53 muon sshd[24397]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.116.17.163  user=root
Oct 23 20:01:53 muon sshd[24397]: pam_winbind(sshd:auth): getting password (0x00000388)
Oct 23 20:01:53 muon sshd[24397]: pam_winbind(sshd:auth): pam_get_item returned a password
Oct 23 20:01:53 muon sshd[24397]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Oct 23 20:01:55 muon sshd[24397]: Failed password for invalid user root from 201.116.17.163 port 56938 ssh2
Oct 23 20:01:58 muon sshd[24447]: reverse mapping checking getaddrinfo for static.customer-201-116-17-163.uninet-ide.com.mx [201.116.17.163] failed - POSSIBLE BREAK-IN ATTEMPT!
Oct 23 20:01:58 muon sshd[24447]: User root from 201.116.17.163 not allowed because not listed in AllowUsers
Oct 23 20:01:58 muon sshd[24447]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.116.17.163  user=root
Oct 23 20:01:58 muon sshd[24447]: pam_winbind(sshd:auth): getting password (0x00000388)
Oct 23 20:01:58 muon sshd[24447]: pam_winbind(sshd:auth): pam_get_item returned a password
Oct 23 20:01:58 muon sshd[24447]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Oct 23 20:02:00 muon sshd[24447]: Failed password for invalid user root from 201.116.17.163 port 57905 ssh2
Oct 23 20:02:02 muon sshd[24497]: reverse mapping checking getaddrinfo for static.customer-201-116-17-163.uninet-ide.com.mx [201.116.17.163] failed - POSSIBLE BREAK-IN ATTEMPT!
Oct 23 20:02:02 muon sshd[24497]: User root from 201.116.17.163 not allowed because not listed in AllowUsers
Oct 23 20:02:02 muon sshd[24497]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.116.17.163  user=root
Oct 23 20:02:02 muon sshd[24497]: pam_winbind(sshd:auth): getting password (0x00000388)
Oct 23 20:02:02 muon sshd[24497]: pam_winbind(sshd:auth): pam_get_item returned a password
Oct 23 20:02:02 muon sshd[24497]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Oct 23 20:02:05 muon sshd[24497]: Failed password for invalid user root from 201.116.17.163 port 58900 ssh2

```

---

### Post by Trougedoor122 on 2010-10-23
Do you use password authentication for SSH, if you do, you should consider using authentication keys instead. I'm not sure about pam_winbind.

---

### Post by HermanAB on 2010-10-24
I am not sure what you are trying to do, but you should only use winbind if you have Active Directory running somewhere and that server has to be firewalled off from the wild wild web, since Windows is insecure.

Your log shows you clearly why you must ALWAYS use secure passwords for everybody.

---

### Post by luvshines on 2010-10-24
Looks like you have pam_winbind.so in your PAM common-<modules>.

You can check this:
```

cd /etc/pam.d
grep pam_winbind.so *

```

pam_winbind.so is provided by winbind package. If pam_winbind.so is present, it is very likely that winbind is installed and running as well.
If you are not using it, you can remove it
```
sudo apt-get remove winbind
```

Before you press yes, just make sure that it is not removing any other relevant package and then take your decision.

---

### Post by cariboo on 2010-10-24
Using apt-get remove, only does half the job, to remove winbind completely, use:

```
sudo apt-get purge <package_name>
```

---

### Post by fa2k on 2010-10-29
Thanks, that's right, I did have winbind installed, don't know how that got there (I know for a fact that I didn't install any samba/windows/etc.. packages) It's now removed :)

I can't use public key auth, because I never know where i want to log in from...

---

### Post by luvshines on 2010-11-02
Hi
Though it has been marked SOLVED, but I need to ask one question.
After you removed winbind package(which removed pam_winbind.so), I guess pam_winbind.so still appears in your pam files, right ?```

cd /etc/pam.d
grep pam_winbind.so *

```

Do you still get winbind in ssh logs ?

---

### Post by SlugSlug on 2010-11-02
```
sudo apt-get install denyhosts  
```will ban these attempts

---

### Post by fa2k on 2010-11-02
> **luvshines said:**
> pam_winbind.so still appears in your pam files, right ?
No it's gone. I am somewhat surprised about the number of files in that directory, looks like a likely place for a bug to hide.

> **luvshines said:**
> Do you still get winbind in ssh logs ?
No they are also gone.

Marius

---

### Post by klikevil on 2011-01-05
> **SlugSlug said:**
> ```
sudo apt-get install denyhosts  
```will ban these attempts


That's easy peasy secure n breezy thanks for the fast solution =p

---

