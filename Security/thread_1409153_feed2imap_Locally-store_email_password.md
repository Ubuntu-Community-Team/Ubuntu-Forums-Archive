---
title: "feed2imap: Locally-store email password?"
date: 2010-02-17
forum: Security
---

### Post by 655 on 2010-02-17
Hello all,

The excellent feed2imap utility scrapes RSS feeds and puts them to your IMAP folder.  To do this, it needs your username and password, stored in a local config file called .feed2imaprc.

I feel vaguely leery about doing this, but it has been suggested that I chmod the file to 600 permissions.  I spoke with the developer and he said that it's not uncommon for people to store passwords in the .fetchmailrc file and elsewhere.

I don't know enough about the ramifications of security on Linux to know whether my concern is justified.  From a 'common sense' standpoint, the idea of saving such an important password locally (versus in my head) is new to me.  But I would be happy to be proven otherwise, or pointed in the direction of how to ensure this isn't a security problem, because I'd much rather use feed2imap than not!

FWIW, the tool can be run on the remote server, eliminating the need for the local file, but I'm using a gmail account so I have no say about what happens on their server.

---

