---
title: "Sudo problem"
date: 2005-09-26
forum: Server Platforms
---

### Post by paul_c on 2005-09-26
Hi there
I am a linux n00b. I've been playing around trying to get certain things to work with Ubuntu, but I think I messed something up with the sudo command. Whenever I try to use it, it comes back with this message:

sudo: /etc/sudoers is owned by uid 1000, should be 0

Is there any way to fix this and revert it back to normal?

---

### Post by Mustard on 2005-09-26
This is what I would do, which is to say, it might work.  It might not work either. :)

Can you start up a root terminal?

Try one of thes 'Rescue methods' from the Unofficial Ubuntu guide to enable yourself to log in as root.

[http://www.ubuntuguide.org/#rescuemode]("http://www.ubuntuguide.org/#rescuemode")

Once you are logged in as root, I would try
```

cd /etc
chown root sudoers

```

I'm assuming this will give the ownership of the sudoers file back to root, which is what it is on my system.  From there I imagine you just restart Ubuntu in normal mode and see if it is still giviing you the error.

---

### Post by paul_c on 2005-09-26
excellent! works perfectly now, thanks so much

---

