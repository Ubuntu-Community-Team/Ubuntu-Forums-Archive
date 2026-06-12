---
title: "Openssh pubkey AND password authentication?"
date: 2013-02-21
forum: Server Platforms
---

### Post by oleink on 2013-02-21
Hey guys,
I was wondering if anyone knew an appropriate, clean way to incorporate both a form of key authentication AND password authentication with openssh.  I have googled this before and haven't had much luck.  I know a lot of people will simply reply "Why?" when reading this but understand the ssh server I have created is made for sftp and the files on this server are bank account information.  It may seem redundant, but the extra authentication does add a small, extra layer of security.

Thanks guys

---

### Post by ali abry on 2013-02-22
i don't now the answer but you can put passphrase on your keys.

---

### Post by CharlesA on 2013-02-22
> **oleink said:**
> Hey guys,
I was wondering if anyone knew an appropriate, clean way to incorporate both a form of key authentication AND password authentication with openssh.  I have googled this before and haven't had much luck.  I know a lot of people will simply reply "Why?" when reading this but understand the ssh server I have created is made for sftp and the files on this server are bank account information.  It may seem redundant, but the extra authentication does add a small, extra layer of security.

Thanks guys

Do you already have a passphrase on your private key?

I found this, but it doesn't really answer your question.
[http://serverfault.com/questions/93807/how-do-i-setup-ssh-with-both-private-key-and-password](http://serverfault.com/questions/93807/how-do-i-setup-ssh-with-both-private-key-and-password)

As far as having two-factor authentication, have you looked into a Google authenticator?
[http://www.howtogeek.com/121650/how-to-secure-ssh-with-google-authenticators-two-factor-authentication/](http://www.howtogeek.com/121650/how-to-secure-ssh-with-google-authenticators-two-factor-authentication/)

---

### Post by hawkmage on 2013-02-22
I do not think the standard OpenSSH does two-factor authentication.  The version of OpenSSH that comes with RedHat 6 and its derivatives are patched for two factor auth using a directive "RequiredAuthentications2".

---

### Post by CharlesA on 2013-02-22
> **hawkmage said:**
> I do not think the standard OpenSSH does two-factor authentication.  The version of OpenSSH that comes with RedHat 6 and its derivatives are patched for two factor auth using a directive "RequiredAuthentications2".

Good find. Too bad it seems to be a RH only change.

[http://serverfault.com/questions/409465/ssh-two-factor-authentication](http://serverfault.com/questions/409465/ssh-two-factor-authentication)

---

### Post by Habitual on 2013-02-23
sad, no one has mentioned the ssh key [passphrase]("https://help.github.com/articles/working-with-ssh-key-passphrases").

---

### Post by CharlesA on 2013-02-23
> **Habitual said:**
> sad, no one has mentioned the ssh key [passphrase]("https://help.github.com/articles/working-with-ssh-key-passphrases").

Second and third post mentioned it, didn't they? :confused:

Good link, though. :)

---

### Post by Habitual on 2013-02-23
> **CharlesA said:**
> Second and third post mentioned it, didn't they? :confused:

Good link, though. :)Yeah, I need to slow down. :)

---

### Post by CharlesA on 2013-02-23
> **Habitual said:**
> Yeah, I need to slow down. :)

Haha! Happens to everyone. :)

I'll just leave this here in case the OP comes back:
[https://help.ubuntu.com/community/SSH/OpenSSH/Advanced](https://help.ubuntu.com/community/SSH/OpenSSH/Advanced)

---

### Post by wlraider70 on 2013-02-23
Since no one mentioned this I assume I'm wrong, but doesn't just turning the options on in sshd_conf fix that?

```

#RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication YES
# Change to yes if you don't trust ~/.ssh/known_hosts for
# RhostsRSAAuthentication and HostbasedAuthentication
#IgnoreUserKnownHosts no

# To disable tunneled clear text passwords, change to no here!
PasswordAuthentication yes
PermitEmptyPasswords no

# Change to no to disable s/key passwords
ChallengeResponseAuthentication yes


```


ChallengeResponseAuthentication yes-- This part is for the PAM authentication which is how Google does two factor. IT works great I followed the guide posted above.

I currently use a password and a google auth pam code at the same time.

---

### Post by CharlesA on 2013-02-23
Yeah, if you set PasswordAuthentication to yes, it will take either the key *or* the password, but not both.

---

### Post by oleink on 2013-03-06
> **CharlesA said:**
> Yeah, if you set PasswordAuthentication to yes, it will take either the key *or* the password, but not both.


This seems to be the main problem (Sorry Everyone that I have not been back in a while.  Tons of crap going on at work and school).  I know the limitations of open-ssh but my question is there a way to fake 2 forms of authentication.  Maybe with using 2 machines instead of one and ssh tunnels?  I could maybe use a raspberry pi?

---

### Post by oleink on 2013-04-11
bump

---

### Post by oleink on 2013-05-14
Decided its possible to do vpn and ssh security paired with multiple forms of authentication thanks guys

---

