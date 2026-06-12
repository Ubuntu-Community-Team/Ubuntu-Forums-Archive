---
title: "Questionable entry to auth.log--Does it mean that another &quot;user&quot; has signed on?"
date: 2017-03-28
forum: Security
---

### Post by SciGuy1872 on 2017-03-28
I am unsure if someone has hacked their way into my machine, thus, I was reviewing the auth.log and came across this entry:

```
anthony-Aspire-X1200 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "anthony"
```

Is the "user ingroup" someone trying to get into my machine, and was it unsuccessful, because the text reports that it was not met by me?

Thanks--here's the line with more of the text--the lines also mention the user "lightdm".  Is it time to do a fresh install, or is there another way?

```
Mar 28 11:40:37 anthony-Aspire-X1200 lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Mar 28 11:40:37 anthony-Aspire-X1200 lightdm: PAM adding faulty module: pam_kwallet5.so
Mar 28 11:40:37 anthony-Aspire-X1200 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "anthony"
Mar 28 11:40:50 anthony-Aspire-X1200 lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Mar 28 11:40:50 anthony-Aspire-X1200 lightdm: pam_unix(lightdm:session): session opened for user anthony by (uid=0)
Mar 28 11:40:50 anthony-Aspire-X1200 systemd: pam_unix(systemd-user:session): session opened for user anthony by (uid=0)

```

---

### Post by deadflowr on 2017-03-28
It's *user in group*, the group being the nopasswdlogin group.
That group is used for users who do not want to use their password to login.

This is opposed to the autologin option you get.
The difference between the nopasswdlogin setting and the autologin setting is that the nopasswdlogin setting will still start at the login screen, where you then just click the Login button to login.
Whereas the autologin setting logs you in without any need to interact at the login screen.

hope that makes sense.

So the comment in the log is perfectly normal, unless you did actually add you user to the nopasswdlogin group.

---

### Post by SciGuy1872 on 2017-03-28
I understand the difference between the nopasswdlogin and autologin settings--I would know if I added to the nopasswdlogin because I would no longer have to enter my password, correct? Very sorry, but just want to make certain that there is nothing wrong with the log entry.

---

### Post by deadflowr on 2017-03-28
> I would know if I added to the nopasswdlogin because I would no longer have to enter my password, correct? 
Only when you login.
You still need to enter a password to open the login keyring and to access anything with elevated privileges (like when you use sudo)

---

