---
title: "Forwarding root emails to my real email?"
date: 2009-02-15
forum: Server Platforms
---

### Post by ibob on 2009-02-15
Hi guys,

I have a server with sits in a remote office. Currently, I have to log in to check the root emails for warning etc. 

Is there a way to get the server to sent root email to another account? 

Thanks,

James

---

### Post by brian_p on 2009-02-17
> **ibob said:**
> 

Is there a way to get the server to sent root email to another account? 

If you were using exim4 /etc/aliases would be a starting point.

---

### Post by songshu on 2009-02-17
/etc/aliases would work with any mailer, jus change it to look like this

[HTML]root:   you@yourmail.com[/HTML]

and then run
```
newaliases
```
after making changes to /etc/aliases

and refresh maybe your mail server

---

### Post by brian_p on 2009-02-17
> **songshu said:**
> 

and then run
```
newaliases
```
after making changes to /etc/aliases

and refresh maybe your mail server

With exim4 (ibob does not say what her MTA and I am unfamiliar with postfix and sendmail):

```
brian@desktop:~$ ls -l /usr/bin/newaliases
lrwxrwxrwx 1 root root 13 2008-03-13 11:51 /usr/bin/newaliases -> ../sbin/exim4
```

and after a change to /etc/aliases it is not necessary to run any command or restart the daemon.

---

### Post by songshu on 2009-02-17
> **brian_p said:**
> With exim4 (ibob does not say what her MTA and I am unfamiliar with postfix and sendmail):


the system will check aliasses first and then send it to the MTA, so it does not matter which one you use, personaly i use postfix with mailx but you could also have it send to any other local user without an MTA.

---

### Post by brian_p on 2009-02-17
> **songshu said:**
> the system will check aliasses first and then send it to the MTA, so it does not matter which one you use, personaly i use postfix with mailx but you could also have it send to any other local user without an MTA.

I'm a bit bothered by that last bit. On my system mailx depends on bsd-mailx which in turn depends on mail-transport-agent. How does mail get sent locally without an MTA?

---

### Post by songshu on 2009-02-18
> **brian_p said:**
> I'm a bit bothered by that last bit. On my system mailx depends on bsd-mailx which in turn depends on mail-transport-agent. How does mail get sent locally without an MTA?

you've sent me on a goose hunt there, trying to find some nice link to prove my assumption ;)

must admit that i have a hard time finding it, but i was positively sure it could be done and still think it should be possible with mailx in combination with a mda like deliver or procmail, but it seems i'm wrong on this one, my bad.

---

