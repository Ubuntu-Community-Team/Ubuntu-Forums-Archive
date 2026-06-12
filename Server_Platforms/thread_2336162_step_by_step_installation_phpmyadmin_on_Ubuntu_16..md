---
title: "step by step installation phpmyadmin on Ubuntu 16.04 (Access denied while installing"
date: 2016-09-05
forum: Server Platforms
---

### Post by sruj on 2016-09-05
[COLOR=#111111][FONT=Ubuntu]I got "Access denied for user" in the process of installing phpmyadmin on Ubuntu 16.04.[/FONT][/COLOR]

Ubuntu 16.04, phpmyadmin (4:4.5.4.1-2ubuntu2), mysql-client-5.7 mysql-client-core-5.7,mysql-server-5.7 mysql-server-core-5.7


[IMG]http://i.stack.imgur.com/udxkw.png[/IMG]
[IMG]http://i.stack.imgur.com/upybo.png[/IMG]
[IMG]http://i.stack.imgur.com/3my56.png[/IMG]
[IMG]http://i.stack.imgur.com/0mcrr.png[/IMG]
[IMG]http://i.stack.imgur.com/GkP0I.png[/IMG]
[IMG]http://i.stack.imgur.com/1DYn6.png[/IMG]

[IMG]http://i.stack.imgur.com/F0BEi.png[/IMG]

[IMG]http://i.stack.imgur.com/hgzlp.png[/IMG]

---

### Post by darkod on 2016-09-05
You are trying to set port 0, so it reports an error. If mysql is on the same machine simply leave that option commented (with # in front). Try it like that.
phpmyadmin knows where to find mysql on the same machine.

---

