---
title: "Dovecot: Help with IMAP Shared Folders?"
date: 2009-05-13
forum: Server Platforms
---

### Post by lightnb on 2009-05-13
Hi everyone,

I'm having a bit of trouble figuring out how IMAP shared folders work in Dovecot.

We'd like to have a shared mailbox for our customer service department, so that any of our reps can see the new message, but more importantly, they can see which one's have already been replied to, and the replies  themselves (via the Sent folder).

I've tried creating a namespace, but it doesn't show up in the client, and I'm honestly not sure what else to do since there's very little documentation on this.

From /etc/dovecot/dovecot.conf:
```
namespace public {
prefix = AG_Shared/
separator = /
location = maildir:/home/dovecot/AG_Shared:INDEX=~/Mail/AG_Shared
subscriptions = no
}
```

Does anyone know how this is actually supposed to work?

---

### Post by lightnb on 2009-05-18
Still no luck on this... Anyone?

---

### Post by gpredrag on 2009-05-21
Maybe stupid question, but what mail clients are being using, did they try to subscribe to folder?

---

