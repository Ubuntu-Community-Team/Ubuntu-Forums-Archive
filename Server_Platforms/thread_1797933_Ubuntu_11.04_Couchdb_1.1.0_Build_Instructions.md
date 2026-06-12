---
title: "Ubuntu 11.04 Couchdb 1.1.0 Build Instructions"
date: 2011-07-05
forum: Server Platforms
---

### Post by ewhitmor27 on 2011-07-05
I couldnt find anyone who posted an installation guide for building couchdb 1.1.0 on ubuntu 11.04 that worked.  So here is my build instructions which i setup on a clean install of ubuntu 11.04.
I hope this helps someone.

Eric

```
apt-get build-dep couchdb
apt-get install xulrunner-1.9.2-dev
apt-get install erlang-eunit
mkdir data
cd /data/
wget http://www.eng.lsu.edu/mirrors/apache//couchdb/1.1.0/apache-couchdb-1.1.0.tar.gz
tar -xvf apache-couchdb-1.1.0.tar.gz
cd apache-couchdb-1.1.0
./configure --prefix=/data/couchdb --with-js-lib=/usr/lib/xulrunner-devel-1.9.2.17/lib --with-js-include=/usr/lib/xulrunner-devel-1.9.2.17/include
make && sudo make install
```

To open up the firewall after updating default.ini bind address to 0.0.0.0:
```

iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 5984 -j ACCEPT
iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 6984 -j ACCEPT
```

Make it so couchdb will start after reboot
```

adduser --system --home /usr/local/var/lib/couchdb --no-create-home --shell /bin/bash --group --gecos "CouchDB Administrator" couchdb
chown -R couchdb:couchdb /data/couchdb
chmod -R 0770 /data/couchdb

cp /data/couchdb/etc/init.d/couchdb /etc/init.d/
update-rc.d couchdb defaults

```

If you get this error:
```

OS Process Error <0.4649.0> :: {os_process_error,{exit_status,127}}
/opt/couchdb/lib/couchdb/bin/couchjs: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

```

Do this:
Check what XULRunner version you have installed use 
```

xulrunner -v

```

create /etc/ld.so.conf.d/xulrunner.conf (nano /etc/ld.so.conf.d/xulrunner.conf)and add the following lines where x.x.x.x is your xulrunner version:
```

/usr/lib/xulrunner-x.x.x.x
/usr/lib/xulrunner-devel-x.x.x.x

```

next run: 
```

sudo /sbin/ldconfig

```

---

### Post by RNZ on 2011-07-07
&#1054;r use ppa [https://launchpad.net/~ericdrex/+archive/couchdb](https://launchpad.net/~ericdrex/+archive/couchdb) created by Eric Drechsel

---

### Post by Seym0ur on 2011-08-15
I really appreciated these instructions: thanks! also the ppa didn't work for me.

---

