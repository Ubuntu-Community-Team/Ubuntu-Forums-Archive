---
title: "How to get my SUDO back?"
date: 2007-03-05
forum: Server Platforms
---

### Post by lwetzel on 2007-03-05
I guess I was playing where I should not have.  Now I cannot perform SUDO nor can I set user accounts.  How might I get this control back.  It is just a standalone machine.:confused:

---

### Post by jtc on 2007-03-05
How about if you tell us where you've been playing?

---

### Post by lwetzel on 2007-03-05
Well I went in to the user accounts.  I had two users one I had been able to do SUDO with  the other just normal user.  I started to add some accounts to the right panel then thought better of that and removed them.  The next time I restarted no SUDO!:mad:

---

### Post by jtc on 2007-03-05
That doesn't sound like anything which would cause trouble. Obviously it has thought :-)

What happens when you try to run sudo? What errormessage do you get?

That username which should have sudo right, what groups does it belong to?

```
groups username
```

---

### Post by lwetzel on 2007-03-05
Well that's a good question and I can't give you the answer.  I'm really green at this linux stuff and I can't see the user admin so I am not sure.

well If I would read you post....

dialout fax cdrom floppy tape audio dip video plugdev lpadmin scanner

---

### Post by jpkotta on 2007-03-05
The user must be a member of the admin group in order to use sudo, so that's the problem.

If none of the users are in admin, you need to reboot in "recovery mode" (or something like that), and add whatever users back to the admin group.

```
adduser jpkotta admin
```

This site is pretty good at getting you started with the terminal: [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/).  See other links in my sig too.

---

### Post by lwetzel on 2007-03-05
Yes I finally figured out what he asked.  However I see that the user is not a member of admin.  How can I right that?

---

### Post by lwetzel on 2007-03-05
> **jpkotta said:**
> The user must be a member of the admin group in order to use sudo, so that's the problem.

If none of the users are in admin, you need to reboot in "recovery mode" (or something like that), and add whatever users back to the admin group.

```
adduser jpkotta admin
```


That was what I needed.  Thanks for the help!

---

