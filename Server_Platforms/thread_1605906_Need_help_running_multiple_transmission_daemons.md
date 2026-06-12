---
title: "Need help running multiple transmission daemons"
date: 2010-10-25
forum: Server Platforms
---

### Post by Sickhaus on 2010-10-25
I have transmission-daemon running perfectly on ubuntu server 10.04, but I would like to run multiple transmission daemons. I imagine this is possible with separate ports, config files, and separate directories. I just don't know how to go about this. I tried following a guide on how to do this for a different program unsuccessfully. Could somebody please help a ubuntu/linux novice?

---

### Post by vikjon0 on 2010-10-26
I can only imaging the reason for this.

If you dont know what you are doing just install a second sw...eg. deluge and you are set.

---

### Post by Sickhaus on 2010-10-26
There will be several people using the server for bt purposes. I thought it would be convenient to keep everybody's media separate.

I never thought about just using another bt client. I could see this being an easy way to run 2, but I was intending to scale up even further. Maybe 3 or 4 instances.

I have found posts of others doing this, just no info on how.

---

### Post by Sickhaus on 2010-10-26
Gave deluge a try, it appears I can't set the scheduler in the web ui. Unfortunately this is a deal breaker for me.

---

### Post by Sickhaus on 2010-10-29
Could I?
```
cp -a /etc/transmission-daemon /etc/transmission-daemon2
cp /etc/init.d/transmission-daemon /etc/init.d/transmission-daemon2
update-rc.d transmission-daemon2 defaults
```Even if this would work I imagine i would have to tell transmission-daemon2 where to look for the other settings.json file (with the separate ports identified), how could i do this?

Should I make log file directories for #2?

Any other considerations?

I'm trying guys....

---

### Post by Sickhaus on 2010-10-29
I forgot
```
cp -a /usr/sbin/transmission-daemon /usr/sbin/transmission-daemon2
```

Im basically trying to follow the instructions here: [http://ubuntuforums.org/showthread.php?t=1192639](http://ubuntuforums.org/showthread.php?t=1192639) but tailoring it to transmission of course.

---

### Post by Axel Mak on 2011-05-08
it works!
I did this!!! Thanks all of you!!!!! that link did help me to run second  copy of this daemon and now i've got two notebooks with two separate  transmissions on diff. ports

---

### Post by c_wolff on 2012-01-15
I'm using Ubuntu 11.04 and Transmission 2.42 (13013)
It works for me, here the instructions for multiple instances of transmission daemon:
In this case i will make a copy named transmission-daemon2. You can name it whatever you want, and make many copies as you wish, for example:

transmission-daemon3
transmission-daemon4
transmission-daemonBLAH
...
transmission-daemonN

Follow the steps for any transmission-daemon you have

1.Stop Transmission daemon

you can list all your transmission-daemon instances using:
```
ps -efa|grep transmission-daemon
```

for each of your instances, run the following:
```
sudo /etc/init.d/transmission-daemon stop
```

if you have a have a transmission-daemon-blah in the ps list:
```
sudo /etc/init.d/transmission-daemon-blah stop
```

2.Update Transmission through ppa:

```
sudo add-apt-repository ppa:transmissionbt/ppa
sudo apt-get update
sudo apt-get install transmission transmission-daemon
```

3.Copy the resources from transmission-daemon to transmission-daemon2:
```
cp /usr/bin/transmission-daemon /usr/bin/transmission-daemon2
cp /etc/init.d/transmission-daemon /etc/init.d/transmission-daemon2
cp -a /var/lib/transmission-daemon /var/lib/transmission-daemon2
cp -a /etc/transmission-daemon /etc/transmission-daemon2
cp /etc/default/transmission-daemon /etc/default/transmission-daemon2

```

4.modify symbolic link:

```
ln -sf /etc/transmission-daemon2/settings.json /var/lib/transmission-daemon2/info/settings.json
```

5.edit config and script files:
edit /etc/init.d/transmission-daemon2, changing lines:

```
NAME=transmission-daemon
to
NAME=transmission-daemon2
```

6.edit settings.conf of your new transmission-daemon2, located at /etc/transmission-daemon2/settings.json:
changing the lines:
```
"download-dir": "/var/lib/transmission-daemon/downloads"
to
 "download-dir": "new download path for transmission-daemon2"
```

for each transmission-daemon instance, increase the peer port by 1:
```
"peer-port": 51413,
para
"peer-port": 51414,
```

If you wish change password and user:

```
"rpc-password": "{745678907320987632076238d58a4510eda06ff7sCZfdZ",
to
"rpc-password": "newpassword",
```

transmission-daemon2 is smart enough to hash yout flat password, so nobody can see it later, even editing settings.json. The new password will be hashed when you restart the transmission-daemon2

You can change user too:
```
"rpc-username": "transmission",
to
"rpc-username": "newuser",
```

for each transmission-daemon instance, again increase by 1 the webadmin port:
```
"rpc-port": 9091,
to
"rpc-port": 9092,
```

if you wish, grant access to any ip:
```
"rpc-whitelist-enabled": true,
to
"rpc-whitelist-enabled": false,
```

edit /etc/default/transmission-daemon2, changing the line:
```
CONFIG_DIR="/var/lib/transmission-daemon/info"
to
CONFIG_DIR="/var/lib/transmission-daemon2/info"
```


8.Almost done. Now update init, so transmission-daemon2 can start upon boot:

```
sudo update-rc.d transmission-daemon2 defaults
```

9.Now restart the daemons

```
sudo /etc/init.d/transmission-daemon start
sudo /etc/init.d/transmission-daemon2 start
```

If everything is ok, you can access the transmissions instances through web admin:
[http://host:9091](http://host:9091)
and
[http://host:9092](http://host:9092)

Following these steps above, you can create as many daemons as you want

Cheers

---

