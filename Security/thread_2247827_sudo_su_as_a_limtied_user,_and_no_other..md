---
title: "sudo su as a limtied user, and no other."
date: 2014-10-10
forum: Security
---

### Post by ant2ne on 2014-10-10
I need to allow a limited user to sudo su to another limited user, but just the other user and no other users. Especially not root. How can I accomplish this?

Thanks!!

---

### Post by Lars Noodén on 2014-10-10
It's hard to find good material about sudo, but if you are interested in knowing a lot about it and how to configure sudoers, you might look at Michael W Lucas' book *Sudo Mastery*

But to answer the question, the following settings in sudoers would let anyone in the group "ant2ne" run the program "whoami" as the user / group "foobar", but only without any options:

```

%ant2ne   ALL=(foobar:foobar) /usr/bin/whoami ""

```

Then that those users could run.

```

sudo -u foobar whoami

```

It's worth taking a look at the manual page for [sudoers](http://manpages.ubuntu.com/manpages/trusty/en/man5/sudoers.5.html).  It will be overwhelming at first, but you'll pick up something each time.

---

### Post by deadflowr on 2014-10-10
You do not need sudo to switch users.
simply
```
su <otheruser>
```
All you need is the other users password.
This can also be applied to su for root.
The reason people use sudo is because root typically, at least on Ubuntu, does not have a password and sudo will cover that.
If that makes sense.
Or if that's helpful?

---

### Post by ant2ne on 2014-10-10
deadflower: I do not want the first user to know the second users password. Not only that, with security lockdowns su is only executable by sudo.

lars: I will try what you suggest on Monday.

---

### Post by Lars Noodén on 2014-10-10
The settings above in #2 will allow you to run a specific program as that other user.  If you really need to login as that other user but without giving away the password to that account, then you will have to run su as root via sudo.  But it can be locked down to not give any leeway for other options.

```
%ant2ne   ALL=(root:root) /bin/su foobar
```

---

### Post by ant2ne on 2014-10-24
> **Lars Noodén said:**
> The settings above in #2 will allow you to run a specific program as that other user.  If you really need to login as that other user but without giving away the password to that account, then you will have to run su as root via sudo.  But it can be locked down to not give any leeway for other options.

```
%ant2ne   ALL=(root:root) /bin/su foobar
```I used this solution. I'm worried about the root:root thing as I don't want this user to execute anything else, but I assume that the only thing that is executed as root is /bin/su foobar so It should be safe.

---

