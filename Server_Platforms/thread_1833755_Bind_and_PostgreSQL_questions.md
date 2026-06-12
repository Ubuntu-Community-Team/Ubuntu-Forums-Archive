---
title: "Bind and PostgreSQL questions"
date: 2011-08-26
forum: Server Platforms
---

### Post by makescents on 2011-08-26
Hello,

I'm running Ubuntu 64bit version 11.04

Firstly can I kill bind if I am using an external DNS service? I'm running various websites with Nginx and I noticed that bind is running when I did ```
ps aux | less
```

Secondly I installed PostgreSQL using ```
apt-get install postgresql
``` but it installed version 8.4.

Is it possible to install version 9? Lastly, why can't I see how much memory PostgreSQL and Nginx are using.

I used ```
free -m
``` and I'm using 600MB of my 2GB, however I can't seem to clearly see how much is being used by these 2 specific programs when running ```
ps aux | less
```

Thanks,

MC

---

### Post by SeijiSensei on 2011-08-26
> **makescents said:**
> Is it possible to install version 9? Lastly, why can't I see how much memory PostgreSQL and Nginx are using.

You can download pre-compiled binaries of 9.0.4 from [here](http://www.enterprisedb.com/downloads/postgres-postgresql-downloads).  If you prefer, you can build it from source.  I built 9.1rc1 today before posting just to make sure it works.  Here's a quick overview of the process:

```

sudo apt-get install build-essential
sudo apt-get build-dep postgresql
cd ~
mkdir build
cd build
wget http://wwwmaster.postgresql.org/download/mirrors-ftp/source/v9.1rc1/postgresql-9.1rc1.tar.bz2
tar xjvf postgresq1-9.1rc1.tar.bz2
cd postgresql-9.1rc1
./configure
make
sudo make install
sudo mkdir /usr/local/pgsql/data
sudo adduser postgres
sudo chown -R postgres.postgres /usr/local/pgsql
cd /usr/local/pgsql
sudo su -c 'bin/initdb' postgres
sudo su -c 'bin/pg_ctl -D /usr/local/pgsql/data -l /usr/local/pgsql/pgstart.log start' postgres

```

If you already have a running instance of Postgres listening on port 5432, you need to add '-o "-p 55432"' before 'start' in the final command to make it listen on a different port, 55432 in this case. Also, if you have a running instance, you already have a postgres user and need not create one with adduser above.

With "ps aux", you should see a line like this:

```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
postgres  9758  0.0  0.1  50620  6708 pts/1    S    16:21   0:00 /usr/local/pgsql/bin/postgres
```

The "virtual size (VSZ)" of postgres is about 50 MB.

---

