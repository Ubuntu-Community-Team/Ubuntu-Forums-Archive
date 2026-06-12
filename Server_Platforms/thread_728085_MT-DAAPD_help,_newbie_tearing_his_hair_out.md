---
title: "MT-DAAPD help, newbie tearing his hair out"
date: 2008-03-18
forum: Server Platforms
---

### Post by daftfunk on 2008-03-18
i'm trying to setup my ubuntu server with firefly mt-daapd to work with itunes on my macbook and dell. 

this is my first ubuntu experience so for give me if i say anything stupid. i already tried setting it up but failed so i've just reinstalled 7.10 lamp with webmin followed these instructions

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install mt-daapd avahi-daemon firestarter libid3tag0 

then tried this to check

liam@ubuntuserver:~$ sudo mt-daapd -f

but got this instead

```
liam@ubuntuserver:~$ sudo mt-daapd -f
Firefly Version svn-1586: Starting with debuglevel 2
Error loading plugin /usr/lib/mt-daapd/plugins/ssc-script.so: plugin declined to load
Plugin loaded: daap/svn-1586
Plugin loaded: rsp/svn-1586
Plugin loaded: ssc-ffmpeg/svn-1586
Starting rendezvous daemon
*** WARNING *** The programme 'mt-daapd' uses the HOWL compatiblity layer of Avahi.
*** WARNING *** Please fix your application to use the native API of Avahi!
*** WARNING *** For more information see <http://0pointer.de/avahi-compat?s=howl&e=mt-daapd>
Starting signal handler
Initializing database
Full reload...
Starting web server from /usr/share/mt-daapd/admin-root on port 3689
Listen port: Address already in use
Error staring web server: Address already in use
Aborting
[1]+  Done                    sudo mt-daapd
liam@ubuntuserver:~$ Rendezvous socket closed (daap server crashed?)  Aborting.
Aborting

```

any ideas?

---

### Post by ubuntu_demon on 2008-03-20
If neededd you can revert any other changes you made :
```

sudo gedit /etc/mt-daapd.conf

```

Now kill mt-daapd and start it :
```

sudo killall mt-daapd
sudo /etc/init.d/mt-daapd start

```

Then go with firefox to :
[http://yourserverip:3689](http://yourserverip:3689) (change yourserverip to the ip of your server)

First change the admin password from mt-daapd to something secure and set your music directory. Now let mt-daapd scan your files (using the web admin interface). 

When all your files are scanned you probable need to restart mt-daapd :
```

sudo /etc/init.d/mt-daapd restart

```

You shouldn't need this :
[http://forums.fireflymediaserver.org/](http://forums.fireflymediaserver.org/)
[http://onlyubuntu.blogspot.com/2008/01/howto-setup-itunes-compatible-media.html](http://onlyubuntu.blogspot.com/2008/01/howto-setup-itunes-compatible-media.html)
[http://wiki.mt-daapd.org/wiki/Quickstart_Ubuntu](http://wiki.mt-daapd.org/wiki/Quickstart_Ubuntu)
[http://jamiedumbill.com/index.php?page=28](http://jamiedumbill.com/index.php?page=28)

---

