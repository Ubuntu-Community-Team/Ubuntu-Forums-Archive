---
title: "Welcome page for Apache 2"
date: 2011-11-21
forum: Server Platforms
---

### Post by Sock! on 2011-11-21
Hey Guys,
Like the [CentOS Welcome page]("http://img14.imageshack.us/img14/4314/cshot.jpg") I'm after the same thing because we want to put up a provider welcome page. 

[HTML]<LocationMatch "^/+$">
Options -Indexes
ErrorDocument 403 /error/noindex.html
</LocationMatch>[/HTML] works for 1 host but not for the Virtual hosts.


Any Apache wizzes out there, help would greatly be appreciated.

[COLOR="Green"]- Sock[/COLOR]

---

### Post by newbie-user on 2011-11-22
Do you have /error/noindex.html in all of your DocumentRoots?

---

