---
title: "What are the chances of tweaking the Gmail Filesystem Google hack for music files?"
date: 2006-05-14
forum: The Cafe
---

### Post by RAV TUX on 2006-05-14
This would be nice to utilize to store and retreive music files, if possible.


"Gmail Filesystem provides a mountable Linux filesystem which uses your Gmail account as its storage medium. Gmail Filesystem is a Python application and uses the FUSE userland filesystem infrastructure to help provide the filesystem, and libgmail to communicate with Gmail.

GmailFS supports most file operations such as read, write, open, close, stat, symlink, link, unlink, truncate and rename. This means that you can use all your favourite unix command line tools to operate on files stored on Gmail (e.g. cp, ls, mv, rm, ln, grep etc. etc.).

Please be gentle on the code. This is my first foray into Python and I'm sure the code is far from elegant. I'm particularly concerned with my attempts to manipulate mutable byte arrays. I'm sure that there must be a less clumsy way of doing it than the nasty list -> array -> string path I'm currently using. This language has a reputation as an excellent choice for rapid prototyping. The first working version of GmailFS took about 2 days of coding. There was an additional 1.5 days spent on performance tuning and bugfixing. Given that this includes language learning curve, the reputation seems well deserved. A special mention should go to libgmail and FUSE , both greatly contributed to the short development time."

[http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html)

Installing Gmail Filesystem
[http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-installing.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-installing.html)

Using Gmail Filesystem
[http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-using.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-using.html)

Gmail Filesystem implementation overview.
[http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-implementation.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-implementation.html)

---

