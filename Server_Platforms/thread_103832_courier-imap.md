---
title: "courier-imap"
date: 2005-12-14
forum: Server Platforms
---

### Post by diebels on 2005-12-14
Can courier-imap listen on more than one address?

It's set to
'ADDRESS=127.0.0.1'
now, for squirrelmail.

I'd like to add more ip's, but can't figure out the syntax.

---

### Post by diebels on 2005-12-15
Can I connect to courier-imap with both squirrelmail running on the same machine, and thunderbird from another machine?

---

### Post by flurdy on 2005-12-15
[QUOTE=diebels]Can courier-imap listen on more than one address?

It's set to
'ADDRESS=127.0.0.1'
now, for squirrelmail.

I'd like to add more ip's, but can't figure out the syntax.[/QUOTE]

try
ADDRESS=0

---

### Post by flurdy on 2005-12-15
[QUOTE=diebels]Can I connect to courier-imap with both squirrelmail running on the same machine, and thunderbird from another machine?[/QUOTE]

Squirrelmail in the end is just another imap client, so if thunderbird works so will squirrelmail.

---

### Post by diebels on 2005-12-15
[QUOTE=flurdy]try
ADDRESS=0[/QUOTE]
Thanks! I was sure I had tried and failed that one before. Must have mistyped something..
Both squirrelmail and thunderbird is happy now :)

---

