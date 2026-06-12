---
title: "Connect to remote mysql server fails."
date: 2005-04-09
forum: Server Platforms
---

### Post by martijntje on 2005-04-09
As the topic title says, i'm having trouble making a connection to a remote database server. Whatever i try it won't make a connection.

Both servers are on the same internal network, and between the computers there is no firewall set up.

I have edited the mysql user account to allow remote connections. To be sure, i even set the host to *, so that it has to work.

The hosts can make connections to eachother no problem. I can ssh from host a to b, and from b to a. It all works, except for the connection to the mysql daemon.

> ERROR 2003: Can't connect to MySQL server on '*ip-address*' (111)

Is this maybe an ubuntu security feature? Something that's blocking the connection?

Any help appreciated,
martijntje

---

### Post by p!=f on 2005-04-09
> 
Check if the server is up by doing telnet your-host-name tcp-ip-port-number and press Enter a couple of times. If there is a MySQL server running on this port you should get a responses that includes the version number of the running MySQL server. If you get an error like telnet: Unable to connect to remote host: Connection refused, then there is no server running on the given port.

Does it work for you?

---

### Post by martijntje on 2005-04-09
Didn't work, but it brought me to an idea, namely to search for the default port.

Led me to the skip-networking option, which solved my problem!

Thanks mate.

---

### Post by p!=f on 2005-04-09
Glad to hear that! Enjoy your database experience. :)

---

