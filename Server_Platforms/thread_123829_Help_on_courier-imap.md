---
title: "Help on courier-imap"
date: 2006-01-31
forum: Server Platforms
---

### Post by hkl on 2006-01-31
hello,i need help on courier-imap ..i've try to setup install courier-imap-ssl package with: apt-get install courier-imap-ssl ..and the output is: 
```

root@gnu /etc/init.d # apt-get install courier-imap-ssl
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  at: Depends: mail-transport-agent
  courier-imap-ssl: Depends: courier-imap (>= 1.3.7-3) but it is not going to be installed
                    Depends: courier-ssl (>= 0.47) but it is not going to be installed
  mailx: Depends: exim4 but it is not going to be installed or
                  mail-transport-agent
  mutt: Depends: exim4 but it is not going to be installed or
                 mail-transport-agent
  postfix-mysql: Depends: postfix but it is not going to be installed
                 Depends: postfix (= 2.1.5-9ubuntu3) but it is not going to be installed
  postfix-tls: Depends: postfix but it is not going to be installed
               Depends: postfix (= 2.1.5-9ubuntu3) but it is not going to be installed
  ubuntu-base: Depends: postfix but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

any help ?

---

### Post by olddog55 on 2006-01-31
And did you try the dpkg -f install?  :-o

What is your current MTA?  postfix or exim4?   (That's a very strange error message you posted.)

When I had a similar problem [ on some other packages ] I had to update/correct my /etc/apt/sources.list.  If memory serves, the out-of-the-box distribution only includes the  'main' and 'restricted' chains.  I added 'universe' and 'multiverse' to get my problem to go away.

It now reads:
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse

I don't know if this is your problem, but you might try it...   And as always, YMMV.

/d

---

