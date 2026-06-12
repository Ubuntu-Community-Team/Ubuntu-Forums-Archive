---
title: "How Do I Remotely Shut Down My SSH Server?"
date: 2013-06-08
forum: Server Platforms
---

### Post by Plumtreed on 2013-06-08
I am using an older PC running 12.04LTS, not the Ubuntu Server edition, and use it as a SSH server for backups and file exchange.....nothing very serious and it all works well. It is networking with three other 12.04LTS units.

I don't have it connected to a screen and this makes it appealing to be able to shut down remotely........when I try "ssh user@IP ***.***.*.*** sudo poweroff" I get the message 'no TTY present and no askpass program specified'. I have searched and googled but the replies are beyond my experience and seem to relate to more serious applications!

I have tried with similar results......sudo shutdown -h now; halt -p; sudo service ssh stop etc

The keyboard is still attached so I can shut it down but this means getting off my butt and walking into 'it's' room:confused: I usually have to 'blindly' log in again then press the shortcut key combination I have set up. 

Please, Is there an answer to my dilemma?

---

### Post by sandyd on 2013-06-08
> **Plumtreed said:**
> I am using an older PC running 12.04LTS, not the Ubuntu Server edition, and use it as a SSH server for backups and file exchange.....nothing very serious and it all works well. It is networking with three other 12.04LTS units.

I don't have it connected to a screen and this makes it appealing to be able to shut down remotely........when I try "ssh user@IP ***.***.*.*** sudo poweroff" I get the message 'no TTY present and no askpass program specified'. I have searched and googled but the replies are beyond my experience and seem to relate to more serious applications!

I have tried with similar results......sudo shutdown -h now; halt -p; sudo service ssh stop etc

The keyboard is still attached so I can shut it down but this means getting off my butt and walking into 'it's' room:confused: I usually have to 'blindly' log in again then press the shortcut key combination I have set up. 

Please, Is there an answer to my dilemma?

You cant do that unless you allow the user to run sudo without a password for a specific command

You see - sudo requires a password when you run it - by running it in that form, sudo has no way of asking for a password.

To allow shutdown to be run without a password,
Run
```

sudo visudo
```
Add at the bottom
```

%sudo ALL=(ALL) NOPASSWD: /sbin/poweroff, /sbin/reboot, /sbin/shutdown
```
restart (it sometimes needs it), and sudo wont ask for a password for the shutdown command :D

The line makes it so that sudo will not ask for a password when running /sbin/poweroff, /sbin/reboot, or /sbin/shutdown with sudo

---

### Post by CharlesA on 2013-06-08
Why not just login to the box and shut it down from there?

It sounds like more work to get it to work with shutdown than it would be just to login and run those commands.

---

### Post by Plumtreed on 2013-06-09
> **CharlesA said:**
> Why not just login to the box and shut it down from there?

It sounds like more work to get it to work with shutdown than it would be just to login and run those commands.

That sounds good to me.......how do I do that?

.....I continue to get an error message about my lack of TTY and Askpass!

Even after trying Sandyd's suggestion.

---

### Post by CharlesA on 2013-06-09
Just login via putty or a terminal and run the poweroff command.

```
ssh user@host
```

Enter password, then do:

```
sudo poweroff
```

---

### Post by markbl on 2013-06-09
OP, this will do what you want:
```

ssh -t user@host sudo poweroff

```

-t forces the allocation of a tty for the command.

---

### Post by Plumtreed on 2013-06-09
Many thanks for all the considered assistance......I really am a beginner with this server business and very much appreciate your help. 

I immediately have taken to CharlesA's suggestion because it is cleary straight forward and simple....but I have tried the other ideas, they do work.

Thanks!

---

