---
title: "multiple instance of postgres on the same machine"
date: 2010-03-16
forum: Server Platforms
---

### Post by detorresrc on 2010-03-16
Hi,

  Please help me how to setup multiple instance of postgre server on the same machine.

Thanks

---

### Post by KB1JWQ on 2010-03-16
Big trick is to bind it to an alternate port and use alternate data directories, after that it's smooth sailing.

May I ask why you're doing this?  Most of the time this is ill advised.

---

### Post by detorresrc on 2010-03-16
Im doing this becauze i need two postgreSQL server, but i dont have any unit to install another one. Thats why i need to install it on the same machine. Do you have a manual or link how i can i do it?

---

### Post by KB1JWQ on 2010-03-16
Very, very, very few applications will require an entirely seperate server.  Most will require a new database, which can easily be done within one running instance-- but we'll assume you know what you're talking about.
Copy the intiscript to be called something like postgres2; edit it so that it pulls from a second configuration file.  Copy /etc/postgres.conf to that second location, and tweak the data directory and port assignments.  Boom, done.

---

### Post by detorresrc on 2010-03-17
Thanks for the info. God Bless :)

---

