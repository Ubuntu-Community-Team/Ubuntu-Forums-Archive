---
title: "hardy apt-cacher problem"
date: 2008-05-14
forum: Server Platforms
---

### Post by rogier.de.groot on 2008-05-14
Hi all. I have a small network with several Ubuntu machines (three clients, two servers) and so usually use apt-cacher to save bandwidth. I normally (on previous releases) do this via apache2, which is already on the server anyway. I normally accomplish this by doing:
1) sudo apt-get install apt-cacher
2) change AUTOSTART to 1 in /etc/default/apt-cacher
3) change allowed_hosts to '192.168.1.0/24, 127.0.0.0/8' in /etc/apt-cacher/apt-cacher.conf
4) sudo /etc/init.d/apache2 restart
5) check [http://server-hostname/apt-cacher](http://server-hostname/apt-cacher) to see if apt-cacher is there.
6) change /etc/apt/sources.list entries from 'deb [http://stuff](http://stuff)' to 'deb [http://server-hostname/apt-cacher/stuff](http://server-hostname/apt-cacher/stuff)'.

But with Hardy this results in apt-get giving me lots of errors instead of updates! I can't figure out what's wrong. Anyone else using apt-cacher on hardy?

---

### Post by bluefrog on 2008-05-15
apt-cacher works finr on 8.04.

out of curiosity, why changing apt-cacher files then restarting apache2, why not restarting apt-cacher?

---

### Post by rogier.de.groot on 2008-05-15
apt-cacher doesn't run as a seperate process in this setup, it's run by apache.

---

### Post by KittyChunk on 2008-05-23
Hi Rogier, I was having the same problem with apt-cacher on our Ubuntu cluster after upgrading to 8.04. I got it to work by putting the port number into the sources.list arguments for the client machines:

6) change /etc/apt/sources.list entries from 'deb [http://stuff](http://stuff)' to 'deb [http://server-hostname](http://server-hostname)**:3142**/apt-cacher/stuff'.

Perhaps that will help?

---

### Post by Aearenda on 2008-05-23
Apt-cacher is working fine for me on 8.04. As an alternative to changing all the sources.list entries, you can create /etc/apt/apt.conf containing this:
```

Acquire::http::Proxy "http://yourserver:3142/apt-cacher/";

```

---

