---
title: "How to install the latest version of Mumble server"
date: 2012-05-23
forum: Server Platforms
---

### Post by pcarlos853 on 2012-05-23
Good Morning,

I run a mumble server (1.2.2) on Ubuntu 10.10 server. So far I have not had any problems, but now I want to run mumble server 1.2.3. I have been trying all morning to install mumble server 1.2.3. The sourceforge.net says:


```
**  Ubuntu **

 Ubuntu carries whatever Mumble version was current at the time of the  release in the universe repository. We also maintain a PPA that has the  latest version for recent Ubuntu versions 
 sudo add-apt-repository ppa:slicer sudo apt-get update  sudo apt-get install mumble  or 
 sudo apt-get install mumble-server sudo dpkg-reconfigure mumble-server 
```([http://mumble.sourceforge.net/Installing_Mumble#Linux](http://mumble.sourceforge.net/Installing_Mumble#Linux))

When I install using the instructions above I get version 1.2.2. I downloaded  [http://mumble.info/snapshot/murmur-static_x86-1.2.3.tar.bz2](http://mumble.info/snapshot/murmur-static_x86-1.2.3.tar.bz2)

However I don't really know what to do with it. I uploaded it to the server and tried running it but I had no luck this is what I got:

```
carlos@UbuntuSvrDell2400:~/new-install$ murmur -ini murmur.ini
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not o                                   pen display
  warnings.warn(str(e), _gtk.Warning)
Note: Python Bindings for libsexy were not found. To enable SpellChecking, insta                                   ll them from http://www.chipx86.com/wiki/Libsexy
Python module geoip could not be loaded.
Murmur is a PyGTK2 client for Museek, the P2P Soulseek Daemon
Dir: Daelstorm
Credit: Hyriand
Version: 0.3.1
        Default options: none
        -c,     --config <file> Use a different config file
        -l,     --log <dir>     Use a different logging directory
        -v,     --version       Display version and quit
        -d                              Debug mode

        -h,     --help          Display this help and exit

carlos@UbuntuSvrDell2400:~/new-install$ murmur -supw helloworld -ini murmur.ini -fg v
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Note: Python Bindings for libsexy were not found. To enable SpellChecking, install them from http://www.chipx86.com/wiki/Libsexy
Python module geoip could not be loaded.
Murmur is a PyGTK2 client for Museek, the P2P Soulseek Daemon
Dir: Daelstorm
Credit: Hyriand
Version: 0.3.1
        Default options: none
        -c,     --config <file> Use a different config file
        -l,     --log <dir>     Use a different logging directory
        -v,     --version       Display version and quit
        -d                              Debug mode

        -h,     --help          Display this help and exit

carlos@UbuntuSvrDell2400:~/new-install$ sudo murmur -supw helloworld -ini murmur.ini -fg v
[sudo] password for carlos:
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Note: Python Bindings for libsexy were not found. To enable SpellChecking, install them from http://www.chipx86.com/wiki/Libsexy
Python module geoip could not be loaded.
Murmur is a PyGTK2 client for Museek, the P2P Soulseek Daemon
Dir: Daelstorm
Credit: Hyriand
Version: 0.3.1
        Default options: none
        -c,     --config <file> Use a different config file
        -l,     --log <dir>     Use a different logging directory
        -v,     --version       Display version and quit
        -d                              Debug mode

        -h,     --help          Display this help and exit

```

Thanks for the help!

---

### Post by roelforg on 2012-05-23
I take it the murmur bin you want to run is in ~/new-install
Because you didn't prefix ./ to the command
```

./murmur -ini murmur.ini

```
will run the murmur bin in the current dir and
```

murmur -ini murmur.ini

```
will run the murmur bin that's in the system paths for binaries (/bin /sbin /usr/bin /usr/sbin /usr/local/bin /usr/local/sbin)

---

