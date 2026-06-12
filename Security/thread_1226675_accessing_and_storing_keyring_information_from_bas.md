---
title: "accessing and storing keyring information from bash"
date: 2009-07-29
forum: Security
---

### Post by yelirekim on 2009-07-29
Right now I have RSA identification set up, along with aliases for each remote machine that I have to access defined in my bash profile, so a bunch of entries that look like this:
```

alias client_name='ssh user@host.com -p <port number>'

```

So if i want to login to a client machine, I just have to type in that client's name and BAM, I'm there.

The only problem is that invariably I need that user's password in order to sudo once I'm logged in, so I then have to go look that password up, which kind of defeats most of the convenience afforded by RSA shell logins.  At first I had just been entering an additional command into the alias, which would echo the user's password when I logged in, but as our client list grows steadily larger I'm less and less comfortable with the idea of all of those passwords being stored in one file.

Ideally I would like to set it up so that when I type in one of those client aliases, it first asks for my keyring password, then grabs the appropriate client password from within the keyring and echoes it.

So, Ubuntu community, how do I do this?  Is there a better way?

---

### Post by yelirekim on 2009-08-06
For anyone that is interested, I found a nice little explanation about how to do this here:

[http://www.gentoo-wiki.info/HOWTO_Use_gnome-keyring_to_store_SSH_passphrases](http://www.gentoo-wiki.info/HOWTO_Use_gnome-keyring_to_store_SSH_passphrases)

---

