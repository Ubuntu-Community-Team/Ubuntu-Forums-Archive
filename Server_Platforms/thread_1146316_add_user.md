---
title: "add user"
date: 2009-05-02
forum: Server Platforms
---

### Post by dldeskins on 2009-05-02
I set up a ubuntu server (8.04) on an old dell machine.  Everything is working well, but I think I am doing something wrong here.

I would like to add a new user:
sudo adduser -c "My User" myuser

It gives me this before I enter a password:
passwd: password updated successfully

When I try to change the password with this:
sudo passwd myuser

I get this before i have entered anything:
passwd: password updated successfully

What am i doing wrong?

---

### Post by John Cheng on 2009-05-04
> **dldeskins said:**
> I set up a ubuntu server (8.04) on an old dell machine.  Everything is working well, but I think I am doing something wrong here.

I would like to add a new user:
sudo adduser -c "My User" myuser

It gives me this before I enter a password:
passwd: password updated successfully

When I try to change the password with this:
sudo passwd myuser

I get this before i have entered anything:
passwd: password updated successfully

What am i doing wrong?

Nothing as far as I can see. Try to log into the "root" shell, then run passwd, it might give you more information with this approach.

```

sudo su - 
# now you would be in the root shell
passwd myuser

```

---

### Post by dldeskins on 2009-05-05
```

sudo su - 
# now you would be in the root shell
passwd myuser

```
OK... I figured it out.  I was using the likewise-open for Windows Active Directory.  I didn't really need it, so i removed it.

Thanks

---

