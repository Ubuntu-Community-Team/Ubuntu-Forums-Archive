---
title: "Working on remote configuration HELP"
date: 2008-12-27
forum: Server Platforms
---

### Post by lomitko on 2008-12-27
[SIZE="2"][COLOR="DimGray"]*preface: I'm somewhat new to linux so please accept my apology for potential stupidities anywhere in my query. I tried to do the research before asking. thx*[/COLOR][/SIZE]


Greetings, 

**what:** I need to manage some of the server configurations from home. For that purpose I'd like to use packages intended to work with local configuration files, like **rapache** or **gadmin-samba** 

**why:**(I'm not familiar with the system enough to edit cfgs manually yet and for a reason webmin is not an option)

It came to my mind to run a shell chroot it into sshfs mounted directory or something like that. (wchich I tried, realized that root is nonsense, tried to create symbolic link of remote /etc/apache2 plus some /var/www inside local filesystem etc etc etc). Not sure whether these are the best ideas. 

_** concrete question ** How to (provided it's possible) use things like RAPACHE or GADMIN-SAMBA to work with configuration on a remote machine ? _

---

### Post by cariboo on 2008-12-27
You can use ssh and xforwarding to run your gui apps eg:

```
ssh -X user@server
```

Then to run your gui apps at the prompt:

```
sudo rapache
```

and the same for gadmin-samba. Truthfully I have looked at both apps and found them to be not worth the trouble of learning to use them, and you don't learn anything about configuring apache and proftpd. Directly editing the config files is way easier for me. :)

Jim

---

