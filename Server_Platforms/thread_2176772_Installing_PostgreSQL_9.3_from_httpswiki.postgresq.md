---
title: "Installing PostgreSQL 9.3 from https://wiki.postgresql.org/wiki/Apt - unable to initi"
date: 2013-09-25
forum: Server Platforms
---

### Post by victorhooi on 2013-09-25
Hi,

I'm attempting to install PostgreSQL 9.3 from the official PostgreSQL APT repository into a Docker container running Ubuntu 13.04:

[https://wiki.postgresql.org/wiki/Apt](https://wiki.postgresql.org/wiki/Apt)

There isn't a specific 13.04 package, but then mention that the previous one (12.10) should work.

This blog post seems to imply it's a fairly smooth process:

[http://amattn.com/2013/09/19/tutorial_postgresql_usage_examples_with_docker.html](http://amattn.com/2013/09/19/tutorial_postgresql_usage_examples_with_docker.html)

However, when I actually try to install the package on my system, I get:

```
Setting up libpq5 (9.3.0-2.pgdg12.4+1) ...
Setting up pgdg-keyring (2012.1) ...
Setting up postgresql-client-common (149.pgdg12.4+1) ...
Setting up postgresql-client-9.3 (9.3.0-2.pgdg12.4+1) ...
update-alternatives: using /usr/share/postgresql/9.3/man/man1/psql.1.gz to provide /usr/share/man/man1/psql.1.gz (psql.1.gz) in auto mode.
Setting up ssl-cert (1.0.28) ...
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (Can't locate Term/ReadLine.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/FrontEnd/Readl
ine.pm line 7.)
debconf: falling back to frontend: Teletype
Setting up postgresql-common (149.pgdg12.4+1) ...
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (Can't locate Term/ReadLine.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/FrontEnd/Readl
ine.pm line 7.)
debconf: falling back to frontend: Teletype
Adding user postgres to group ssl-cert
Building PostgreSQL dictionaries from installed myspell/hunspell packages...
Removing obsolete dictionary files:
 * No PostgreSQL clusters exist; see "man pg_createcluster"
Setting up postgresql-9.3 (9.3.0-2.pgdg12.4+1) ...
Creating new cluster 9.3/main ...
  config /etc/postgresql/9.3/main
  data   /var/lib/postgresql/9.3/main
  locale C
  port   5432
update-alternatives: using /usr/share/postgresql/9.3/man/man1/postmaster.1.gz to provide /usr/share/man/man1/postmaster.1.gz (postmaster.1.gz) in auto mode.
 * Starting PostgreSQL 9.3 database server
   ...done.
Setting up postgresql-contrib-9.3 (9.3.0-2.pgdg12.4+1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

I did find this which seems to mention the same error:

[https://github.com/teddziuba/docker-postgres/issues/1](https://github.com/teddziuba/docker-postgres/issues/1)
[https://gist.github.com/bshi/6311159/](https://gist.github.com/bshi/6311159/)

However, that specific part isn't mentioned there.

Any thoughts on how to fix the above?

Cheers,
Victor

---

### Post by SeijiSensei on 2013-09-27
It looks like its running regardless of those errors.  Did you try connecting to the server with the psql command-line client?  If you run "ps ax" do you see a postmaster process with its various children?  Try "telnet localhost 5432".  If the server is running, you'll get a reply.

---

### Post by victorhooi on 2013-09-28
Hi,

Yes, it does seem to be running, however, I'm curious what that error is about, or if there's anything I can do to address it?

If I was to guess, I'd say it's asking me something, and because it's running through Docker, somehow that doesn't work with dialog. However, I'm not sure, of course.

Is this something I should be worried about?

Cheers,
Victor

---

### Post by SeijiSensei on 2013-09-28
I don't know what "Docker" is, but the installer is complaining that you don't have a default terminal set via the TERM environment variable.  It tried the usual suspects and fell back to the "Teletype" interface.  The Ubuntu default is xterm, as you can see from running the command "echo $TERM" at the command prompt.

Since it found a compatible terminal type, the installation should be fine.

---

### Post by Cybolic on 2013-10-16
The error roughly translates to: The package itself didn't have any errors during installation, but it wanted to ask you a question and couldn't find a way to do so.

I'm no expert on Docker, but I'm guessing you want the installation to happen without user interference, in which case you should probably put Debconf in non-interactive mode - which will also fix the error:
```
DEBIAN_FRONTEND=noninteractive apt-get install -y postgresql-9.3 postgresql-client-9.3 postgresql-contrib-9.3
```

---

