---
title: "Script not running at startup"
date: 2015-11-15
forum: Server Platforms
---

### Post by WeKnowMC on 2015-11-15
I am running ubuntu server with the desktop installed on it and I am having some problems making a script run at boot.

I want to run this script which starts a minecraft server in screen at boot:
```
screen -A -m -d -S "Hub" java -Xms512M -Xmx512M -jar  spigot-1.8.8.jar nogui
```
This script is located in:
```
~/Desktop/Minecraft/Hub/start.sh
```
Also, the script is executable as it runs as it should if you do ./start.sh

I have looked at multiple ways to make the script run at boot, including adding a line to rc.local:
```
sh /home/Samuel/Desktop/Minecraft/Hub/start.sh
```

 and adding a file to /etc/init.d:
```
#!/bin/sh
/home/Samuel/Desktop/Minecraft/Proxy/start.sh

```

None of these have worked because the screen session and minecraft server are both not running.

Does anyone know what I have done wrong and how I can fix this issue?

---

### Post by Lars Noodén on 2015-11-15
Have you tried using -- to terminate screen's options?

```

screen -A -m -d -S "Hub" [color=blue]**--**[/color] java -Xms512M -Xmx512M -jar  spigot-1.8.8.jar nogui

```

Or else wrap "java -Xms512M -Xmx512M -jar  spigot-1.8.8.jar nogui" in a script and then call the script from screen.

Someone asked a similar question recently and it was solved by the latter.

---

### Post by WeKnowMC on 2015-11-15
> **Lars Noodén said:**
> Have you tried using -- to terminate screen's options?

```

screen -A -m -d -S "Hub" [COLOR=blue]**--**[/COLOR] java -Xms512M -Xmx512M -jar  spigot-1.8.8.jar nogui

```


I tried this however, it made no difference.

> **Lars Noodén said:**
> [COLOR=#000000]Or else wrap "java -Xms512M -Xmx512M -jar spigot-1.8.8.jar nogui" in a script and then call the script from screen.[/COLOR]

How would you do this? Could you explain please.

---

### Post by matt_symes on 2015-11-15
Hi

What version of Ubuntu are you using on this server ?

If your using Upstart then i have created an Upstart script that starts when my server starts, starts a screen session using a custom screen configuration file that, in my case, starts Weechat and some other applications and some shells.

If you're using Upstart as your init system and not systemd, then i suspect it could be adapted to run Minecraft.

Kind regards

---

### Post by Lars Noodén on 2015-11-15
> **WeKnowMC said:**
> How would you do this? Could you explain please.

Put a file in /usr/local/bin  set it as executable.  Then fill it with the something like the following:

```

#!/bin/sh
/usr/bin/java -Xms512M -Xmx512M -jar  /some/path/to/spigot-1.8.8.jar nogui

```

Then you can call it with upstart, cron, or rc.local.

---

### Post by WeKnowMC on 2015-11-15
> **matt_symes said:**
> 
What version of Ubuntu are you using on this server ?
I am using ubuntu 15.04.

> **matt_symes said:**
> If your using Upstart then i have created an Upstart script that starts when my server starts, starts a screen session using a custom screen configuration file that, in my case, starts Weechat and some other applications and some shells.
I'm not sure which version I'm using so it will probably be whatever the default for ubuntu 15.04 is.

---

### Post by WeKnowMC on 2015-11-15
> **Lars Noodén said:**
> Put a file in /usr/local/bin  set it as executable.  Then fill it with the something like the following:

```

#!/bin/sh
/usr/bin/java -Xms512M -Xmx512M -jar  /some/path/to/spigot-1.8.8.jar nogui

```
Ok, I have done this.

> **Lars Noodén said:**
> Then you can call it with upstart, cron, or rc.local.
This is the part that is confusing me a bit, how would I make rc.local start the script with screen?

Thanks

---

### Post by matt_symes on 2015-11-15
Hi

> **WeKnowMC said:**
> I am using ubuntu 15.04.

I'm not sure which version I'm using so it will probably be whatever the default for ubuntu 15.04 is.

The default is systemd in 15.04.

Kind regards

---

### Post by Lars Noodén on 2015-11-15
If you can run the script manually, to make sure it is working, then you can just put the script (full path + name) in /etc/rc.local using sudoedit.  It should be inserted just before the line "exit 0"

---

### Post by WeKnowMC on 2015-11-17
> **Lars Noodén said:**
> [COLOR=#000000]Put a file in /usr/local/bin set it as executable. Then fill it with the something like the following:
[/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]#!/bin/sh[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]/usr/bin/java -Xms512M -Xmx512M -jar  /some/path/to/spigot-1.8.8.jar nogui[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR][COLOR=#000000]Then you can call it with upstart, cron, or rc.local.[/COLOR][COLOR=#000000]
[/COLOR]> **Lars Noodén said:**
> If you can run the script manually, to make sure it is working, then you can just put the script (full path + name) in /etc/rc.local using sudoedit.  It should be inserted just before the line "exit 0"

The server runs when I execute it manually and it also runs at startup but in my minecraft client, I can the server is online however, because this way isn't using screen, I cannot check the console of the server which also means that I am unable to safely shut the minecraft server down. Is there any way to use screen with this method?

---

### Post by Lars Noodén on 2015-11-17
Yes, anywhere you can call the script, you should also be able to call the script via screen

```

/usr/bin/screen -A -m -d -S "Hub" -- /usr/local/bin/somescript

```

or tmux.

---

### Post by WeKnowMC on 2015-11-18
I have done all that you have said and I have been experiencing some very weird behavior that I simply cant understand what is going on. Let me explain...

NOTE: I don't know if you know anything about minecraft servers but my plan was to get 2 minecraft servers (both spigot, 1 hub and 1 survival) to run at boot and 1 proxy minecraft server (bungeecord) to also run at boot. When you run a minecraft server jar file for the first time, it will add a lot of files and folders to the directory that you are running it from. I tested all of the following with my proxy server for my minecraft bungeecord network. But the hub server has the same issues.

So, first of all I made a file in /usr/local/bin called start.sh. In this file i entered:
```
!/bin/sh
/usr/bin/java -Xms256M -Xmx256M -jar  /home/Samuel/Desktop/Minecraft/Proxy/BungeeCord.jar nogui
```
I then did:
```
sudo chmod u+x start.sh
```

Finally, as root, I ran the script by doing
```
./start.sh
```
The server worked perfectly however, it had ran as it was new because it made new files and folders in /usr/local/bin (where the script was).

I thought I could easily find a solution for this later so I continued and added this line to /etc/rc.local
```
/usr/local/bin/start.sh &
```
Then when I rebooted my server, it ran at startup successfully.

This was the point when I made my last post, thinking everything was working however, when I tried to change some of the servers settings by editing the config.yml file in /usr/local/bin, I ran into some more problems. When I tried to restart the server again, the minecraft server was running as its default settings however, the config file had the settings that I had just changed but the minecraft server wasn't using them. I tried to put the start.sh script in the directory where the server .jar and other server files were however, after I edited my rc.local (I read somewhere that you should add sh to the start of line line in rc.local but that also didnt work) to match this new directory, it didn't work.

I figured out that when I manually run the server, it uses the config.yml file I edited however, when it starts up at boot, it doesn't use the config.yml file, it uses the default settings. I then checked to see if it was using some of the files where the BungeeCord.jar file is stored but it wasn't. This then made me think that it is running in a different directory when it starts at boot using rc.local. I have not yet worked out why this is happening.

I then thought that I would try to get screen to work with the script. I thought that it might display an error in the server console that could help me solve this issue. I created another file in /usr/local/bin called screenstart.sh. This file contained:
```
/usr/bin/screen -A -m -d -S "Hub" -- /usr/local/bin/start.sh
```

When I manually started this file, it opened the minecraft proxy/bungeecord server in screen however, when I changed rc.local to this new script and rebooted my server, the minecraft proxy/bungeecord server started up as I could see that it was online in my minecraft client but it didn't run in screen for some reason.

I am really confused to why this is happening.

---

### Post by Lars Noodén on 2015-11-19
If minecraft is populating the directory with its files, then the script should be where you want the files.  I hadn't anticipated a messy script.  But to get rc.local to run screen + script as your user, then you can use sudo or su

```

**sudo -u weknowmc -i ** /usr/bin/screen -A -m -d -S "Hub" -- /some/other/path/to/somescript

```

or

```

**su -l weknowmc -c ** '/usr/bin/screen -A -m -d -S "Hub" -- /some/other/path/to/somescript'

```

---

