---
title: "[SOLVED] Using sudo in terminal"
date: 2008-09-15
forum: Security
---

### Post by sternkanz on 2008-09-15
Hi, when I use "sudo <some command>" in the terminal, it requires I type in my root password. However, when I then enter another "sudo <some command>" in the terminal, it remembers that I've already put in the password so it doesn't ask me for it again.

I would like to be asked for my password every time I type "sudo <command>".

How can I do this?

Thanks,

Stern

---

### Post by tollboy on 2008-09-15
i don't know wether  it is possible to do that or not
there is super-user authorisatio. 
if u type ur password after typing sudo u get super user authoristation.
and u will be authorised as superuser as long as u didn't close ur terminal.

---

### Post by Steve1961 on 2008-09-15
You need to edit the sudoers file.  See this link for instructions:

[http://ubuntuforums.org/showthread.php?t=229309](http://ubuntuforums.org/showthread.php?t=229309)

---

### Post by sternkanz on 2008-09-15
I just typed "sudo ls", put in my password, then closed the terminal. I then opened a new terminal, typed "sudo ls" again, and wasn't asked for my password.

---

### Post by sternkanz on 2008-09-15
> **Steve1961 said:**
> You need to edit the sudoers file.  See this link for instructions:

[http://ubuntuforums.org/showthread.php?t=229309](http://ubuntuforums.org/showthread.php?t=229309)

I had a look at that link, seems like a fairly simple operation. Just one question (in case I mess it all up).

If I set the passwd timout to 0, will it break sudo? Or will it work exactly as I want it to and make sudo commands require a password all the time?

---

### Post by Steve1961 on 2008-09-15
> **sternkanz said:**
> I had a look at that link, seems like a fairly simple operation. Just one question (in case I mess it all up).

If I set the passwd timout to 0, will it break sudo? Or will it work exactly as I want it to and make sudo commands require a password all the time?


It shouldn't break sudo, but you can always create a backup just in case:

cd /etc
sudo cp sudoers sudoers.backup

---

### Post by sisco311 on 2008-09-15
> **sternkanz said:**
> I had a look at that link, seems like a fairly simple operation. Just one question (in case I mess it all up).

If I set the passwd timout to 0, will it break sudo? Or will it work exactly as I want it to and make sudo commands require a password all the time?
just add this line:
> Defaults:ALL timestamp_timeout=0
to edit the file with gedit:
```
export EDITOR="gedit"&&sudo -E visudo
```

---

### Post by cdenley on 2008-09-15
> **sternkanz said:**
> I had a look at that link, seems like a fairly simple operation. Just one question (in case I mess it all up).

If I set the passwd timout to 0, will it break sudo? Or will it work exactly as I want it to and make sudo commands require a password all the time?

```

man sudoers

```
> 
timestamp_timeout
                       Number of minutes that can elapse before sudo will ask
                       for a passwd again.  The default is 15.  Set this to 0
                       to always prompt for a password.  If set to a value
                       less than 0 the user’s timestamp will never expire.
                       This can be used to allow users to create or delete
                       their own timestamps via sudo -v and sudo -k respec&#8208;
                       tively.


---

### Post by sternkanz on 2008-09-15
Ahh, "man sudoers" helped me.

I had to use "timestamp_timeout=0", not "passwd_timeout=0". The passwd_timeout only changed how long it would wait for me to enter the password.

Thanks, and sorry for not thinking of man pages. I have some strange aversion to them.

---

