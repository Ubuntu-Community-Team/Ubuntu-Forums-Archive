---
title: "Trouble configuring IRCD-hybrid"
date: 2013-01-19
forum: Server Platforms
---

### Post by omgTravis on 2013-01-19
I am attempting to setup an irc server that requires password authentication to access. I installed ircd-hybrid through apt-get, however I was having a little trouble setting a server password in my ircd.conf. I added a password field encrypted with /usr/bin/mkpasswd to the users auth block, but whenever I add this password and reset the ircd-hybrid service I can't seem to connect with any users. Here is an excerpt from my ircd.conf [https://gist.github.com/7104d086d41c0bd4677f](https://gist.github.com/7104d086d41c0bd4677f) I would greatly appreciate anyone telling me what I'm doing wrong.

I am using Ubuntu 12.04 if it makes a difference.

---

