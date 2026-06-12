---
title: "So.... i broke Root login shell"
date: 2018-08-01
forum: Server Platforms
---

### Post by warmango on 2018-08-01
So... yep, i was using chsh to set a user (named dos) to used DOSEMU as its shell... and i messed up, even though the command i ran was LITERALLY ```
sudo chsh -s $(which dos) dos
``` when i wanted to run ```
sudo chsh -s $(which dosemu) dos
```, it decided to change the root login shell to literally just "dos", like here is the line in /etc/passwd for root 

```
root:x:0:0:root:/root:dos
```

Any clue how to fix this? I wont be onsite to my server until a little over a week (Aug13)

And MODS, please dont put this in server,

---

### Post by howefield on 2018-08-01
Don't see why this thread shouldn't be in the "*Server Platforms*" forum ?

---

### Post by steeldriver on 2018-08-01
I was a little surprised that chsh actually allows `dos` to be set as  the login shell for root, since it's not in /etc/shells - I guess that  rule only applies to "ordinary" users.

It *should* be as simple as

```

sudoedit /etc/passwd

```

and then correcting the last field of root's passwd entry back to a valid shell such as /bin/bash - at least, I just tried it and it worked for me (I'm assuming because `sudoedit` doesn't require a login shell - I also had success with `sudo /bin/bash`)

FWIW this is one of those occasions where proper quoting would have saved you a headache

```

$ sudo chsh -s "$(which dos)" dos
[sudo] password for steeldriver:
chsh: user 'dos' does not exist

```

---

### Post by warmango on 2018-08-01
That helped and fixed my issue, thanks! Never knew of "sudoedit" before but it fixed it, thank you!

And I actually added it in a new line in the "shells" file.

---

### Post by steeldriver on 2018-08-01
OK glad that worked

I assume that you mean you added something like /usr/bin/dosemu to /etc/shells? You don't want to go adding random non-shell strings like "dos" to it - in fact, I'm not even sure you should add /usr/bin/dosemu

If you must have dosemu as a valid shell in /etc/shells, you may want to look at removing the setuid bit from the chsh binary - otherwise I think there's nothing to stop your "dos" user from changing their login shell to something else

At least it's something you should be thinking through the security implications of - see for example [chsh command security with Set-UID](https://security.stackexchange.com/questions/102172/chsh-command-security-with-set-uid)

---

### Post by warmango on 2018-08-01
That's exactly what I did, I had gotten. It working, but then I changed it back to normal bash so I could edit symlinks and drives while maintaining user permissions.
Also hard to change your shell when you can't access Linux CLI only Dosemu. I have it setup so users can just pop in and have a seamless expirince in dos. 

And I will check that out, thanks,

---

