---
title: "Postfix sockets seem broken on Dapper"
date: 2006-09-15
forum: Server Platforms
---

### Post by sclough on 2006-09-15
Can Dapper's build of postfix communicate on any sockets?  I configured it to use mysql for all it's domain and user lookups.  That would not work with the server set to localhost (which defaults to sockets) or the socket file.  I got that the file did not exist either way (which it did).  It would only work when I set to the server to 127.0.0.1 which, according to the documentation, forces postfix to connect via tcp.

Now, I'm trying to get postfix to pass emails to dspam as a content_filter and I get "cannot connect to socket."  The socket file is good, netstat reports it as listening.  Then I noticed that postfix "chroots" things in a way.  The strange thing is that I have exactly this setup working on FreeBSD with no problems.  Is this a chroot problem so that the process cannot see the socket file, or was postfix just built in a way that socket's don't work?  The strange thing is that it reports the file does not exist so it's like it's chrooted, tries to stat the file and can't find it.  Anybody have any ideas (solutions)? Help!:(

---

