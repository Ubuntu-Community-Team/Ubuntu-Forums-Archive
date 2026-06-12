---
title: "postgres database replication with pgpool-II"
date: 2009-06-25
forum: Server Platforms
---

### Post by mjrmua on 2009-06-25
Is anyone succesfully using pgpool-II witih ubuntu?

I'm trying to set up database replication across two servers but am getting the following errors from pgpool when I try to connect to the pgpool server:

```

Protocol Major: 3 Minor: 0 database: postgres user: postgres
new_connection: connecting 0 backend
new_connection: connecting 1 backend
pool_read_message_length: slot: 0 length: 12
pool_read_message_length: slot: 1 length: 8
pool_read_message_length: message length (8) in slot 1 does not match with slot 0

```

What could be going wrong here?
I've copied the same "/var/lib/postgres" dir to both servers, so database contents should be the same.  
I can log into both databases from the pgpool server.

Is there anyway to get pgpool to display the messages received from the two database servers to assist debugging?

---

