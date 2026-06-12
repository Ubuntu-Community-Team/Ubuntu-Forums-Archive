---
title: "Minecraft server auto run"
date: 2010-11-10
forum: Server Platforms
---

### Post by Whiteice on 2010-11-10
So I have recently been playing the called Minecraft. I run my own server and recently I have been SSH into my server and running the java command to run it. When when im done I stop the server and terminate my SSH connection. I want to get around this. I want to have the server run from start and I'm a bit confused. Ive read that I could make a bash to do this and something about running it as deamon. Could anyone help me out or possible sort out which way to does this?

---

### Post by roberto.tomas on 2010-11-10
sure. first, open a terminal and type:

```
sudo cp /etc/init.d/rc.local minecraft
gksu gedit minecraft &
```now change the script to refer to your specific application.. in the do_start change the log message to say it is starting minecraft, change the outer if statement and the line after the log line to the name of your application... something like this:

```

do_start() {
    if [ -x /path/to/minecraft ]; then
            [ "$VERBOSE" != no ] && log_begin_msg "Running local minecraft script (/path/to/minecraft)"
        /path/to/minecraft
        ES=$?
        [ "$VERBOSE" != no ] && log_end_msg $ES
        return $ES
    fi
}

```save the file as /etc/init.d/minecraft, and return to the terminal. finally prepare the script and add it to the system runlevel so it will call it on startup:

```
sudo chmod u+x  /etc/init.d/minecraft
sudo ln -s /etc/init.d/minecraft /etc/rc2.d/S99minecraft
```

---

### Post by Whiteice on 2010-11-10
Ok i see. The only problem is that minecraft is a jar file so I have to start up a java virtual for it using this command.

```
 sudo java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui

```

unless could I just use the minecraft_server.jar alone?

---

### Post by Whiteice on 2010-11-11
Bump

---

### Post by roberto.tomas on 2010-11-12
> **Whiteice said:**
> Ok i see. The only problem is that minecraft is a jar file so I have to start up a java virtual for it using this command.

```
 sudo java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui

```unless could I just use the minecraft_server.jar alone?

that should work just fine .. without the sudo because it will already run as root:
```
java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui
```

---

### Post by helluvamatt on 2011-01-09
Here is an init script that uses GNU screen:

[http://www.minecraftwiki.net/wiki/Server_startup_script](http://www.minecraftwiki.net/wiki/Server_startup_script)

EDIT: It is an HUGE security to risk to run the Minecraft server as root. It is good practice to create a user just for Minecraft (like 'minecraft'). Apache does this (www-data or www-user), MySQL (mysql), and many others!

---

### Post by 0PS on 2011-09-26
Edit: wrong thread.

---

