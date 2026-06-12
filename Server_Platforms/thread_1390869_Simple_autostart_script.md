---
title: "Simple autostart script"
date: 2010-01-26
forum: Server Platforms
---

### Post by dukla on 2010-01-26
Hi i am succesfully installed TeamSpeak 3 server and now i want to startup it automatically without screen daemon and on every startup on linux ubuntu 9.10 i am using this command for start the TS3 server:

./ts3server_linux_amd64 dbplugin=ts3db_mysql

in home/user/Desktop/ts3server_linux_amd64

Thx for help.

---

### Post by Kemon on 2010-01-26
Make a file like this:
```
#! /bin/bash
cd /home/user/Desktop/ts3server_linux_amd64
./ts3server_linux_amd64 dbplugin=ts3db_mysql -d
```

Save it somewhere like /home/USER/ts.sh

Edit: /etc/rc.local
Add: 'sh /home/USER/ts.sh' before 'exit 0'

That's how I did it with my vent server. I hope it helps =)

---

### Post by IXL on 2010-01-26
Hi fellas.
 
Im on this very case myself... so this is very useful to me....
 
However... Im used to doing these sorts of things in "screen".
 
Would that be a better way to do this?
 
Also how would you stop the server in the method Kemon suggests?

---

### Post by Kemon on 2010-01-26
I don't think you can do it in "screen".

To stop the server I would use:
```
ps aux | grep ts3
sudo kill <id beside the owner>
```

---

### Post by IXL on 2010-01-26
Hmm.
 
I use scripts, simply because I use webmin to manage the server, so I assign the script to a custom command button. That way I can do most things without putty for example.
 
Perhaps your right and it cant be done using a script, but this is the way I thought about doing it. (im half way through my install, so will confirm if I can later ).
 
To Start :
 
```
 
#!/bin/sh
cd /home/ts3
screen -r -X quit
echo Server has been rebooted
screen -[COLOR=black]dmS ts3 ./ts3server_linux_x86[/COLOR]

```
 

To Stop :
 
```

#!/bin/sh
cd /home/ts3
echo Server has been stopped
screen -r -X quit
```

---

