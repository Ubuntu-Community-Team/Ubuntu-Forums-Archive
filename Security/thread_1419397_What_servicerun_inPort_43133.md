---
title: "What servicerun inPort 43133???"
date: 2010-03-01
forum: Security
---

### Post by Diogo Falcomer on 2010-03-01
I ran nessus on my notebook. He returned a web server on port 43133. I wonder if anyone knows any service that runs on this port. I typed: [http://localhost:43133](http://localhost:43133) he shows me a login and password, and my login ubuntu does not work.
I Wanted to know what is! I found it strange that high port, it could be someone virus?

---

### Post by Bachstelze on 2010-03-02
Run

```
sudo fuser -n tcp 43133
```

It will return the PID of the process listening on that port. Then you can get its name with something like

```
ps aux | grep PID
```

---

### Post by Diogo Falcomer on 2010-03-02
The port is ramdom, I take that port when i turn on my computer this morning.

```


diogo@diogo-laptop:~$ sudo fuser -n tcp 44628
[sudo] password for diogo: 
44628/tcp:            1951
diogo@diogo-laptop:~$ ps aux | grep 1951
diogo     1951  0.0  0.3  62556  8072 ?        Sl   16:32   0:05 /usr/lib/erlang/erts-5.7.2/bin/beam.smp -Bd -K true -- -root /usr/lib/erlang -progname erl -- -home /home/diogo -noshell -noinput -smp auto -sasl errlog_type error -pa /usr/lib/couchdb/erlang/lib/couch-0.10.0/ebin /usr/lib/couchdb/erlang/lib/mochiweb-r97/ebin /usr/lib/couchdb/erlang/lib/ibrowse-1.5.2/ebin /usr/lib/couchdb/erlang/lib/erlang-oauth/ebin -eval application:load(ibrowse) -eval application:load(oauth) -eval application:load(crypto) -eval application:load(couch) -eval crypto:start() -eval ssl:start() -eval ibrowse:start() -eval couch_server:start([ "/etc/couchdb/default.ini", "/etc/xdg/desktop-couch/compulsory-auth.ini", "/home/diogo/.config/desktop-couch/desktop-couchdb.ini"]), receive done -> done end. -pidfile /home/diogo/.cache/desktop-couch/desktop-couchdb.pid -heart
diogo     1960  0.0  0.0   1532   424 ?        Ss   16:32   0:00 heart -pid 1951 -ht 11
diogo     5170  0.0  0.0   3056   820 pts/0    R+   18:26   0:00 grep --color=auto 1951


```

any idea?

---

### Post by FuturePilot on 2010-03-02
> **Diogo Falcomer said:**
> The port is ramdom, I take that port when i turn on my computer this morning.

```


diogo@diogo-laptop:~$ sudo fuser -n tcp 44628
[sudo] password for diogo: 
44628/tcp:            1951
diogo@diogo-laptop:~$ ps aux | grep 1951
diogo     1951  0.0  0.3  62556  8072 ?        Sl   16:32   0:05 /usr/lib/erlang/erts-5.7.2/bin/beam.smp -Bd -K true -- -root /usr/lib/erlang -progname erl -- -home /home/diogo -noshell -noinput -smp auto -sasl errlog_type error -pa /usr/lib/couchdb/erlang/lib/couch-0.10.0/ebin /usr/lib/couchdb/erlang/lib/mochiweb-r97/ebin /usr/lib/couchdb/erlang/lib/ibrowse-1.5.2/ebin /usr/lib/couchdb/erlang/lib/erlang-oauth/ebin -eval application:load(ibrowse) -eval application:load(oauth) -eval application:load(crypto) -eval application:load(couch) -eval crypto:start() -eval ssl:start() -eval ibrowse:start() -eval couch_server:start([ "/etc/couchdb/default.ini", "/etc/xdg/desktop-couch/compulsory-auth.ini", "/home/diogo/.config/desktop-couch/desktop-couchdb.ini"]), receive done -> done end. -pidfile /home/diogo/.cache/desktop-couch/desktop-couchdb.pid -heart
diogo     1960  0.0  0.0   1532   424 ?        Ss   16:32   0:00 heart -pid 1951 -ht 11
diogo     5170  0.0  0.0   3056   820 pts/0    R+   18:26   0:00 grep --color=auto 1951


```

any idea?

Part of couchdb by the looks of it.

---

### Post by Diogo Falcomer on 2010-03-02
Good! is connected to CouchDB!

must be connected to this package ... (desktopcouch) I do not know
it was installed!

is connected with the evolution also very strange. I took
package.

And a python libs together. but because he runs a "web
service "? may be a kind of GUI pgadmin.

but it's still running! It will be a rool-kit? It looks like virus?

I took all the packages CouchDB, and I'm running again. And returned the same thing.

---

### Post by FuturePilot on 2010-03-02
No it is not a virus. It's a database. Certain applications (like Evolution, Firefox and Gwibber) can store information in the database which is also able to sync to Ubuntu One.

---

### Post by Diogo Falcomer on 2010-03-02
humm.. Thank you man!

i have uninstaled the package and did not feel a difference in the system!

:DThank you very much!:D

---

