---
title: "Ubuntu Account With SSH"
date: 2013-07-05
forum: Security
---

### Post by joo4gperpetual on 2013-07-05
Hi guys,
I just set up a SSH (openssh) account with public key authentication on my Ubuntu computer.
I have 10 Users account on the computer.

How may i login with different account?, i can only login with the root account as of now (root@myip : port)
How may i set different public key for different users account.

Thanks :)

---

### Post by Lars Noodén on 2013-07-05
If you are logging in as root over SSH then something went wrong.

Anyway, to enable key-based login for an account, make a key pair (using a strong passphrase) and put the public key in the destination account inside the file *~/.ssh/authorized_keys*  The key goes in the whole and ubroken on a single line.  You can use nano if that's comfortable for you.

```

nano -w ~/.ssh/authorized_keys

```

You can do that for as many accounts as you need to.

---

### Post by The Cog on 2013-07-05
I presume you added your key to /root/.ssh/authorized_keys - well you need to add that key to the /home/username/.ssh/authorized_keys file of every user you want to log in as. So for instance, to be able to login as thecog@myip you need to add your key to /home/thecog/.ssh/authorised_keys.

---

### Post by joo4gperpetual on 2013-07-06
Thanks 
[COLOR=#DD4814]**_Lars Noodén_**[/COLOR] 
and
[COLOR=#C61919]**_The Cog_**[/COLOR]
 :)

@ [COLOR=#C61919]**_The Cog _**[/COLOR]you really answered my question.
Do i have to add the each users keys directory to the AuthorizedKeysFile directive of the sshd_config file?
Thanks

---

### Post by Lars Noodén on 2013-07-06
The AuthorizedKeysFile directive is set only once per SSH server.  It will contain a pattern that is supposed to work for all users.  On Ubuntu it is like this:

```

AuthorizedKeysFile     %h/.ssh/authorized_keys

```

There is no need to change it from the default.  Your public keys go in the file the sshd_config points to, not in sshd_config itself.

As mentioned above, the keys go in the user's *authorized_keys* file.  The tilde (~) is a shortcut that means the user's home directory.  So if you are logged in as 'joo4gperpetual' then both */home/joo4gperpetual/.ssh/authorized_keys* and *~/.ssh/authorized_keys* refer to the same file.  If you want to read about all the options you have with keys (they can be constrained in many ways for automation) you can look at the 'authorized_keys file format' section of the manual page for [sshd](http://manpages.ubuntu.com/manpages/raring/en/man8/sshd.8.html).

---

### Post by joo4gperpetual on 2013-07-06
Thanks. you have really answered my question. You are wonderful, regards. :)

---

