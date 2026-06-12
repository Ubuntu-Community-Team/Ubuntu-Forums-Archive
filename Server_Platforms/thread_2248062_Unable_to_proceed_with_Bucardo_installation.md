---
title: "Unable to proceed with Bucardo installation"
date: 2014-10-12
forum: Server Platforms
---

### Post by hdry on 2014-10-12
I'm recently installing Bucardo to work with PostgreSQL. I had trouble installing Bucardo and the relevant libraries from packages, so I installed them through apt-get instead.

My problem is that after I created a directory to act as its piddir (either /tmp/bucardo/ or /var/run/bucardo/) and proceed with the installation, I received this error message:

```

psql: FATAL: password authentication failed for user "postgres" Sorry, unable to determine the database version.

```

I then rest the password for user postgres, as well as giving it a new password, but the problem still remains. I've also deleted the password and left it blank, but when I tried to proceed with the installation, I received an error message saying ```
psql: fe_sendauth: no password supplied
```.

I'm using PSQL 9.1.14 and Bucardo 4.4.8 on Ubuntu Server 12.04, if that helps.

---

### Post by hdry on 2014-10-13
I've also edited the `pg_hba.conf` file in both master and slave servers, so that it includes these values: `local all postgres ident and local all all md5`, but when I restarted psql and tried to proceed with the installation I still received the same error messages.

---

### Post by hdry on 2014-10-14
So basically when I tried to proceed with my Bucardo installation (using bucardo_ctl install) with these settings:

 Current connection settings:
 1. Host:          localhost
 2. Port:          5432
 3. User:          postgres
 4. Database:      postgres
 5. PID directory: /var/run/bucardo
 Enter a number to change it, P to proceed, or Q to quit:

It accepted my password for user postgres, but when I keyed in a password for user bucardo, I received the error message:

```
INSTALLATION FAILED! (psql:/usr/local/share/bucardo/bucardo.schema:18: \connect:FATAL: password authentication failed for user "bucardo"
FATAL: password authentication failed for user "bucardo"
)

Installation cannot proceed unless the Pl/PerlU language is available
This is usually available as a separate package.
```

Please note I have Pl/PerlU installed earlier, using

```
sudo apt-get install postgresql-plperl-9.1
```

I'm using Bucardo 4.4.8 and PSQL 9.1.14 on Ubuntu Server 12.04.

---

