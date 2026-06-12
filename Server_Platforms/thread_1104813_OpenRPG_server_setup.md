---
title: "OpenRPG server setup"
date: 2009-03-24
forum: Server Platforms
---

### Post by faldore on 2009-03-24
I wanted to set up OpenRPG server to automatically start in Ubuntu, and there were no good guides.  So here is the procedure I came up with.

```
sudo apt-get install openrpg
sudo gedit --new-document /etc/init.d/openrpg
```

Paste the following code:
```
#!/bin/sh

do_start() {
	echo -n "Starting OpenRPG server..."	
	/usr/bin/expect /etc/init.d/openrpg_srv.exp
}

do_stop() {
	echo -n "Stopping OpenRPG server..."
	pkill start_server.py		
}

case "$1" in
start)
	do_start
	;;

stop)
	do_stop
	;;

restart|reload|force-reload)
	do_stop
	sleep 10
	do_start
	;;
	
*)
	echo "Usage: $0 start|stop|restart|reload|force-reload"
	exit 1
	;;
	
esac
```

Save the file, and close gedit.

```
sudo gedit --new-document /etc/init.d/openrpg_srv.exp
```

Paste the following code into gedit:

```
#!/usr/bin/expect --

spawn /usr/games/openrpg-server-cli
expect "Enter boot password for the Lobby:  "
send "\r"
expect "Do you want to post your server to the OpenRPG Meta Server list? (y,n)"
send "n\r"

if {[fork] != 0} exit
disconnect

while {1} {
  sleep 60
}
```

Note:  If you want to set the Lobby boot password, or post the server to the OpenRPG Meta Server List, just adjust the "send" strings.

Save the file, and close gedit.

Now add to defaults

```
sudo chmod 755 /etc/init.d/openrpg
sudo update-rc.d openrpg defaults
sudo /etc/init.d/openrpg start
```

Of course, you need to set your Ubuntu machine to have a static IP address, and use your router to forward port 6774 to your Ubuntu machine, and of course give your friends the IP address that the router says it has with the WAN, or better yet use DynDNS.org.

Also if you want Ventrilo I have a guide for that too.  [http://ubuntuforums.org/showthread.php?t=1104656]("http://ubuntuforums.org/showthread.php?t=1104656")

---

