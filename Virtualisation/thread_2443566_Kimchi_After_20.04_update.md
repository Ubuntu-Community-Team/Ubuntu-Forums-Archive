---
title: "Kimchi After 20.04 update"
date: 2020-05-17
forum: Virtualisation
---

### Post by Forbees on 2020-05-17
So before i updated to 20.04 from 19.10(plain ubuntu), i had Wok running with Kimchi to manage KVM - but after upgrading to 20.04, Wok, Kimchi, and Webmin are no longer working - or rather they were completely removed from my computer

Got Webmin installed again with no issues, but Wok and Kimchi aren't playing well. Doing some online digging it seemed like installing the 3.0.0 versions of both from source was the way to go but i'm still stuck here(deb versions fail to install). 

So here's the first issue, Wokd service isn't found
```
sudo systemctl -l status wokd.service
Unit wokd.service could not be found.
```

But i can start it like this and you'll see my second problem
```

sudo python3 /usr/bin/wokd --environment=dev
Push server created on address /run/user/0/woknotifications
Failed to load plugin conf from /etc/wok/plugins.d/kimchi.conf: ("Config error in section: 'wok', option: 'enable', value: 'True'. Config values must be valid Python.", 'TypeError', ("unrepr does not recognize 'Constant'",))
Plugin configuration file /etc/wok/plugins.d/__pycache__.conf doesn't exist.
[17/May/2020:11:08:51] ENGINE Listening for SIGTERM.
[17/May/2020:11:08:51] ENGINE Listening for SIGHUP.
[17/May/2020:11:08:51] ENGINE Listening for SIGUSR1.
[17/May/2020:11:08:51] ENGINE Bus STARTING
[17/May/2020:11:08:51] ENGINE Started monitor thread 'Autoreloader'.
[17/May/2020:11:08:51] ENGINE Serving on http://127.0.0.1:8010
[17/May/2020:11:08:51] ENGINE Bus STARTED

```

So two big things i need help with, how do i get my computer to run Wokd as a service like it used to, and how can i get it to see the Kimchi plugin?

Side note, during the install of dependencies, M2Crypto was not found, after some digging i found to install it like so - ran again so you can see it's installed
```

sudo pip3 install M2Crypto
Requirement already satisfied: M2Crypto in /usr/local/lib/python3.8/dist-packages (0.35.2) 
```

Another side note just to paint how weird this update hit me. I can now only SSH into the computer i'm running this on, if i try to VNC into it, it instead VNC's me into one of the Debian VM's it's running.

So anything i have to do has to be done through SSH till i can figure out this other issue too.

There is [this]("https://github.com/kimchi-project/kimchi/issues/1318#issuecomment-610583198"), which might fix me, but i'm not sure how to do it

---

### Post by Forbees on 2020-05-18
Update:
So i changed dependencies.yaml to have - python3-m2crypto instead of - python-m2crypto.
Found that and changed it but still no change - when running Wok there is no Kimchi. 
I'm unable to find this reprconf.py mentioned in issue 1318 i linked above

```

sudo python3 /usr/bin/wokd --environment=dev
Push server created on address /run/user/0/woknotifications
Failed to load plugin conf from /etc/wok/plugins.d/kimchi.conf: ("Config error in section: 'wok', option: 'enable', value: 'True'. Config values must be valid Python.", 'TypeError', ("unrepr does not recognize 'Constant'",))
Plugin configuration file /etc/wok/plugins.d/__pycache__.conf doesn't exist.
[18/May/2020:19:14:49] ENGINE Listening for SIGTERM.
[18/May/2020:19:14:49] ENGINE Listening for SIGHUP.
[18/May/2020:19:14:49] ENGINE Listening for SIGUSR1.
[18/May/2020:19:14:49] ENGINE Bus STARTING
[18/May/2020:19:14:49] ENGINE Started monitor thread 'Autoreloader'.
[18/May/2020:19:14:49] ENGINE Serving on http://127.0.0.1:8010
[18/May/2020:19:14:49] ENGINE Bus STARTED
[18/May/2020:19:16:31] ENGINE Started monitor thread 'Session cleanup'.

```

Starting Wok via /usr/bin/wokd is still the only way to get it running, where on 19.04 this used to work as a service
```
sudo service wokd start
Failed to start wokd.service: Unit wokd.service not found.

```

Edit - I've tried removing 3.0 of both version and install the master versions with no change

---

