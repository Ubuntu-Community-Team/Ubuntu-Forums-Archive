---
title: "postfix relay + spam filters"
date: 2007-11-29
forum: Server Platforms
---

### Post by ultralame on 2007-11-29
I am running gutsy + postfix.  The system is configured to relay only with authentication and use my ISP as a smarthost.  Everything works fine.

The problem is that if I am remote and I send an email (via my mobile phone network, from work or from a cafe) OTHER systems will look at the typically dynamic IP address I was using when I sent the email, and not at my ISP address or server address.  Depending on where I am, that address might be in a spam database.  (In the case of my iPhone, it  is ALWAYS in a db!).

I was delivering directly from the server, but a couple large systems refused to accept mail from me because I do not have a reverse DNS lookup.  That problem was solved with the smarthost.

So... can I set up postfix to send the mail as if it was ORIGINATING on my server?

---

### Post by MJN on 2007-11-29
An increasing problem but not one which I've hit yet so it's still on my 'to do' list.

A solution off the top of my head is for you to configure Postfix to rewrite/delete the first Received-from: header line (perhaps using header_checks) using a suitable matching string (so as not to alter any other headers, particularly those on incoming mail).

Sorry I can't be more specific but this might steer you in the right direction.

Needless to say, if you suss it out do post back then I can tick it off my to do list!

Mathew

---

### Post by ultralame on 2007-11-29
Will do!

---

