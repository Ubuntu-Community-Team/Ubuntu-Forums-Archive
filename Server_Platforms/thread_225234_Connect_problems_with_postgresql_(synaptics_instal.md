---
title: "Connect problems with postgresql (synaptics install)"
date: 2006-07-29
forum: Server Platforms
---

### Post by pelgrim on 2006-07-29
2 problems occured ...

1) I can't find a way to put my database files where I want.
  I can run initdb /mydisc/mydir
  but there's no way I can make postmaster work with this new database,
  it runs with the initial defautl database location.
  This is extremely anoying, I want a seperate disc for my database files,
  there is just not enough room on my OS disc.

  probably related to this, pg_ctl reload simply doesn't work

2) (probably of 1) ), I can't connect with pgadmin to the database.
  pg_hba.conf would have errors, or does not exist, or connection refused ...
  
  pg_hba.conf isn't all that difficult, right ?
  host    all         all         127.0.0.1/32          trust
  host    all         all         192.168.0.1/32          trust

  or
  host 	all	all	127.0.0.1	255.255.255.255		trust
  host	all	all	192.168.0.1	255.255.255.0		trust

  or both, it shoud work
  (it dit on my mandrake server)

  and yes, I putted "localhost', '*' active in postgresql.conf

Who can help me out with this,
it's blocking me to do just about any work I should be doing ...

---

