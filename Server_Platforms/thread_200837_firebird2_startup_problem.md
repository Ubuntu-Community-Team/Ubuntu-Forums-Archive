---
title: "firebird2 startup problem"
date: 2006-06-20
forum: Server Platforms
---

### Post by euzkoarima on 2006-06-20
Hi, I'm dist-upgrade a from breezy to Dapper with nearly no problem. But the firebird database (super server) which change from 1.5.1 to 1.5.3 now doesn't startup giving the following error message:

```
Starting Firebird Server: Could not open /usr/lib/firebird2/run/isc_guard1.ubuntuServer
```

I'm check and /usr/lib/firebird2/run is a link to /var/run/firebird2 but there isn't a firebird2 directory in /var/run.
There isn't any file isc_guard* in the server.

Any idea?

Regards.

---

### Post by mariuz on 2006-06-28
[QUOTE=euzkoarima]Hi, I'm dist-upgrade a from breezy to Dapper with nearly no problem. But the firebird database (super server) which change from 1.5.1 to 1.5.3 now doesn't startup giving the following error message:

```
Starting Firebird Server: Could not open /usr/lib/firebird2/run/isc_guard1.ubuntuServer
```

I'm check and /usr/lib/firebird2/run is a link to /var/run/firebird2 but there isn't a firebird2 directory in /var/run.
There isn't any file isc_guard* in the server.

Any idea?

Regards.[/QUOTE]
seems to be an bug in the firebird package  (/var/run/firebird2 was left out )
mkdir /var/run/firebird2

---

### Post by euzkoarima on 2006-06-28
Yes, with mkdir it works. But since each time I restart the server, the directory /var/run seems to be emptied, I modified the /etc/init.d/firebird2 script, and before the case (for start, stop, etc) I added:

```
if [ ! -d /var/run/firebird2 ]
then
        cd /var/run
        mkdir firebird2
        chmod -f 770 firebird2
        chown -f firebird:firebird firebird2
fi
```

Now all is working.

regards.

---

### Post by Patagon on 2006-07-13
> **euzkoarima said:**
> Yes, with mkdir it works. But since each time I restart the server, the directory /var/run seems to be emptied, I modified the /etc/init.d/firebird2 script, and before the case (for start, stop, etc) I added:

```
if [ ! -d /var/run/firebird2 ]
then
        cd /var/run
        mkdir firebird2
        chmod -f 770 firebird2
        chown -f firebird:firebird firebird2
fi
```

Now all is working.

regards.

This works fine :KS 

Thanks

---

### Post by puya on 2006-07-31
hi.

I try to install the firebird super-server in Ubuntu with apt-get.


sudo apt-get install firebird2-super-server 

sudo apt-get install firebird2-utils-super 

sudo apt-get install firebird2-server-common

the problem is that the server it dos'nt run.
how can I run it? 

with the top command I saw the running processes , but the fbguard it was not present.

can you help me?

thank you.

---

### Post by fipsfuchs on 2006-08-10
wow - that was an annoying bug - thanks for the help - and I hope they fix the package soon...

---

### Post by smeto on 2006-12-05
after i install firebird2 from ubuntu repositories, firebird classic server don't running.

after install /etc/init.d/firebird2 don't exist

how to run server?

please someone post me init firebird script

thanks

---

### Post by jckdnk111 on 2007-04-15
firebird2 uses xinetd instead of init.d ... however it doesn't install it as a dependency.

You need to do a: "sudo apt-get install xinetd"
followed by: "sudo update-inetd --disable gds_db"
then, in /etc/xinet.d/firebird2, comment out the line that says: "disable =     yes"
(just put a '#' in front)

restart xinetd by issuing: "/etc/init.d/xinetd stop"
followed by: "/etc/init.d/xinetd start"

if all goes well firebird2 will nowbe running and will start at boot time.
Good luck.

---

### Post by spyblue on 2007-11-28
Hello people.. my name is Felipe. I have same problem on Ubuntu 7.10.. every time that restart system i need mkdir /usr/run/firebird to run Firebird. I tryed both solutions but nothing work. :(

Somebody can help me please ?

Thank's
From Brasil

---

### Post by Colonus on 2007-12-02
Hi Felipe,

it's a bug in Gutsy.
To solve the problem, just take a look [here]("https://bugs.launchpad.net/ubuntu/+source/firebird/+bug/135582/comments/5")

Franz

---

### Post by juandc on 2007-12-29
Hello,

This thread helped me get Firebird 2.03 to startup on Xubuntu 7.10 and I thought to contribute something back.  I simply modified euzkoarima's fix a bit to:

```

if [ ! -d /var/run/firebird/2.0 ]
then
    cd /var/run
    mkdir -p firebird/2.0
    chmod -fR 770 firebird
    chown -fR firebird:firebird firebird
fi

``` 

Hope my first post helps someone.  As always, make a backup first.

---

### Post by dschulz on 2008-01-27
Instead of using chmod and chown, you can just use **fixPermsConfigure**, is a function provided by the script 
**/usr/share/firebird${FB_VER}-common/functions.sh**, loaded at the beggining of **/etc/init.d/firebird2.0-***


```

if ! [ -d $RUN ]; then
   mkdir -v -p $RUN
   fixPermsConfigure
fi

```


The function just does the same  :)

```
fixPermsConfigure()
{
    find $RUN -type d \
            -exec chown firebird:firebird {} \; \
            -exec chmod 0770 {} \;
    find $RUN -type f \
            -exec chown firebird:firebird {} \; \
            -exec chmod 0660 {} \;

}
```

---

### Post by mariuz on 2008-03-14
i agree i tested and i have submitted the debdiff to be included and package to be updated by the MOTU 

[https://bugs.launchpad.net/ubuntu/+source/firebird2.0/+bug/135582](https://bugs.launchpad.net/ubuntu/+source/firebird2.0/+bug/135582)

[http://launchpadlibrarian.net/12666826/firebird2.0_2.0.3.12981.ds1-1ubuntu3.debdiff](http://launchpadlibrarian.net/12666826/firebird2.0_2.0.3.12981.ds1-1ubuntu3.debdiff)


also package is now uploaded to my ppp repository (for gutsy)

[https://launchpad.net/~mapopa/+archive](https://launchpad.net/~mapopa/+archive)

---

