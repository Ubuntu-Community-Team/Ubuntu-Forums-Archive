---
title: "pgadmin3 through ssh tunnel"
date: 2010-03-01
forum: Security
---

### Post by Saghaulor on 2010-03-01
Hello all.

I'm learning sql. I'm using Postgresql 8.4.2-2. I'm trying to remote into my server securely. I figure I could do so with ssh. Apparently I figured correctly, as per, [http://www.pgadmin.org/docs/1.4/pg/ssh-tunnels.html]("http://www.pgadmin.org/docs/1.4/pg/ssh-tunnels.html")
and
[http://www.postgresonline.com/journal/index.php?/archives/38-PuTTY-for-SSH-Tunneling-to-PostgreSQL-Server.html]("http://www.postgresonline.com/journal/index.php?/archives/38-PuTTY-for-SSH-Tunneling-to-PostgreSQL-Server.html")

I setup the ssh tunnel.

ssh -L 5432:serverip:5432

Then I setup pgadmin3 to connect as follows:

host: localhost
port: 5432
user: postgres
maintenance db: postgres

And I receive the following error:

An error has occurred:

> An error has occurred:

Error connecting to the server: server closed the connection unexpectedly
	This probably means the server terminated abnormally
	before or while processing the request.


I'm not sure what the problem is. I can connect with ```
psql
``` from the cli after connecting to the terminal via ssh. So I know that I'm using the correct password.

Please advise. Thank you in advance.

---

### Post by Bachstelze on 2010-03-02
> **Saghaulor said:**
> 
I setup the ssh tunnel.

ssh -L 5432:serverip:5432


Try

```
ssh -L 5432:localhost:5432
```

---

### Post by Saghaulor on 2010-03-02
> **Bachstelze said:**
> Try

```
ssh -L 5432:localhost:5432
```

That solved it. Thank you so much. Now I can feel much more comfortable connecting to my database.

---

### Post by victorhooi on 2010-11-07
heya,

I had the same issue, and it worked for me (setting server to localhost, instead of the actual internet-accessible hostname).

I guess I know why it works, since from the perspective of the SSH server, localhost is, well, itself.

I'm curious though, why doesn't the version where you put in the internet-addressable hostname in it working?

Cheers,
Victor

---

