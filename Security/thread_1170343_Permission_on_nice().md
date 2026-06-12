---
title: "Permission on nice()"
date: 2009-05-26
forum: Security
---

### Post by jarmok on 2009-05-26
Hi all,
i need a process to have a high priority, so at the beggining of the code I try to execute nice(-10), but program crashes with an "Unpermitted operation" message.

If i sudo the program, i can do this.

How can I assign nice permission to an user?

Cheers

---

### Post by Boondoklife on 2009-05-26
Only way that I cna think of is to put them in sudoers but limit them to only be able to sudo the nice command. this however would lead to an issue of nice running apps as root so not a really good option.

renice might do what you want though, just run the app and then renice it to -10 after

---

### Post by bodhi.zazen on 2009-05-26
> **maletek said:**
> Only way that I cna think of is to put them in sudoers but limit them to only be able to sudo the nice command. this however would lead to an issue of nice running apps as root so not a really good option.

renice might do what you want though, just run the app and then renice it to -10 after

no, not at all , this is the advantage of sudo ;)

Add the users into sudoers and give them permission to run the script as root.

[http://www.sudo.ws/sudo/man/sudoers.html](http://www.sudo.ws/sudo/man/sudoers.html)

---

### Post by Boondoklife on 2009-05-26
> **bodhi.zazen said:**
> no, not at all , this is the advantage of sudo ;)

Add the users into sudoers and give them permission to run the script as root.

[http://www.sudo.ws/sudo/man/sudoers.html](http://www.sudo.ws/sudo/man/sudoers.html)


wonder what would happen if the user did```
sudo nice -n 0 passwd
```

for me it resets the root pass. that is why i said it would worry me.

---

### Post by bodhi.zazen on 2009-05-27
Such is the problem with writing all programs, writing programs so that they are secure.

---

### Post by Boondoklife on 2009-05-27
yea i was just plyaing on my box and renice would be your best bet. it doesnt need admin rights and can only change what is already running.

---

### Post by jarmok on 2009-05-27
Best option to me is running as user and renice later :)
 
Thanks for your replys.

---

### Post by sisco311 on 2009-05-27
You can set the limit in /etc/security/limits.conf

i.e.
```
@users    -    nice    -10
```

---

### Post by jarmok on 2009-05-28
Modifying /etc/security/limits.conf doesn't work for me.
 
I'm trying to use nice in a Python script:
 
```

os.nice(-10)

```
 
And I get:
```

OSError: [Errno1] Operation not permitted

```
 
Maybe it works only in console...

---

