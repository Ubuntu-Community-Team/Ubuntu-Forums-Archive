---
title: "passwordless eucalyptus"
date: 2010-12-20
forum: Ubuntu Cloud and Juju
---

### Post by oldhoot on 2010-12-20
No matter what I try, I can't get passwordless login to work for the "eucalyptus" user account.  ssh-copy-id seems to be doing what it's supposed to but ssh still prompts for a password.  Where can I look?

---

### Post by raymdt on 2010-12-20
Hey oldhoot,
please don't start a new thread for the same Problem ;)

---

### Post by oldhoot on 2010-12-21
My apologies but I don't understand this response

---

### Post by raymdt on 2010-12-21
Hey oldhoot,
you only need to reset the eucalyptus-user's Password on the NC.

Try this as root(on NC)
```

#passwd eucalyptus 

```

Regards

---

