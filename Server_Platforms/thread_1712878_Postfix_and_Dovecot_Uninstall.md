---
title: "Postfix and Dovecot Uninstall"
date: 2011-03-23
forum: Server Platforms
---

### Post by San1ty on 2011-03-23
Hi All,

Yesterday I tried following a bad guide on how to set up Postfix and Dovecot, in the end it seemed best to me to just uninstall and start over. So I just apt-get purged everything I installed.

Now I have found some great documentation on Postfix + Courier and I would like to start from a clean sheet.

So I started to look around for stuff that might have survived the purge.

/etc/passwd returns a user mail with group mail with an id of 8.
Is this user there on a clean Install or is that something that can be removed.

I already removed /var/mail as I thought it was something from Dovecot but I see now the user mail has /var/mail as a home dir. Should I recreate the homedir? If so, to what should it be chowned an chmodded?

Another option is a complete reinstall but ofcourse I would prefer not to.

---

### Post by SeijiSensei on 2011-03-23
You've already removed everything that needs removal.  Don't touch the /etc/passwd (or /etc/group) file, and restore /var/mail.  It has unusual permissions, too:

```

cd /var
sudo mkdir mail
sudo chown root.mail mail
sudo chmod u+rwx,g+rws,o+rx mail

```

---

### Post by stmiller on 2011-03-24
Eek! Yeah never go and delete random directories. 

Just use 
```

sudo apt-get remove postfix

```

etc,

---

