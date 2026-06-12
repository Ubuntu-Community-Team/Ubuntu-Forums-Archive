---
title: "Having trouble installing CouchDB 1.6.1 in Ubuntu 14.04"
date: 2015-06-19
forum: Repositories &amp; Backports
---

### Post by RobRobinson on 2015-06-19
I am using tor and python to scrape tor, and to use torscraper, CouchDB needs to be installed.  I have gotten this far with no problems.

```
sudo apt-get install --yes build-essential curl git
sudo apt-get install --yes python-software-properties python g++ make

sudo apt-get install -y erlang-dev erlang-manpages erlang-base-hipe erlang-eunit erlang-nox erlang-xmerl erlang-inets
sudo apt-get install -y libmozjs185-dev libicu-dev libcurl4-gnutls-dev libtool

# via http://ftp.fau.de/apache/couchdb/source/1.6.1/
cd /tmp
wget http://ftp.fau.de/apache/couchdb/source/1.6.1/apache-couchdb-1.6.1.tar.gz
tar xvzf apache-couchdb-*

cd apache-couchdb-*
./configure && make

sudo make install
```

The problem comes in the next step, which is:

```
useradd -d /var/lib/couchdb couchdb
```

I get the following error:

```
useradd: Permission denied.
useradd: cannot lock /etc/passwd; try again later.

```

Can someone help me out on this please?

Thank you.

---

### Post by sandyd on 2015-06-20
Useradd requires root privileges to run, you will have to add 'sudo' in front of the useradd command.

---

### Post by RobRobinson on 2015-06-20
Thank you so much.  That did the trick.

---

### Post by sandyd on 2015-06-21
Glad you got it working :)

Please mark this thread as solved via Thread Tools -> Mark Thread as Solved

---

