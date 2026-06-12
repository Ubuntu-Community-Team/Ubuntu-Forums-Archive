---
title: "Help with screen"
date: 2021-02-18
forum: Server Platforms
---

### Post by xeneration on 2021-02-18
Hello, I am running a mc sever on a Ubuntu Server 20.04 LTS. I’ve recently started using screen to run my sever but whenever I close my terminal from my pc I’m unable to bring up that screen page. Any help would be very helpful

---

### Post by howefield on 2021-02-18
Thread moved to the "*Server Platforms*" forum.

---

### Post by LHammonds on 2021-02-18
I can help you with that.  Forgive me if I present typos or forget steps/commands....its been a long time since I setup a Minecraft server.

I assume you are wanting to run multiple Minecraft servers so I will show you how this is done with 2 servers running 2 different accounts so you can see what changes in each of the commands used and what stays the same.

The 1st step is to create low-rights groups/users that cannot login via SSH or the console and grant that user ownership/permissions to your Minecraft folder/sub-folders.

Example:
```

sudo mkdir -p /opt/minecraft
sudo addgroup minecraft
sudo chown root:minecraft /opt/minecraft
sudo chmod 0750 /opt/minecraft
sudo useradd --comment "Minecraft Server" --shell /bin/false --home /opt/minecraft/spigot --gid minecraft spigot
sudo useradd --comment "Minecraft Server" --shell /bin/false --home /opt/minecraft/hungergames --gid minecraft hungergames

```

Substitute your own server path(s) and user accounts you want to use.

Place the server files in the destination locations.  The absolute minimum is the server.jar file and eula.txt file.

Make sure the ownership and permissions are set correctly for initial setup and after the server has started and created its files/folders.  Run these commands after getting the files in place and before you run the server the 1st time.  Then again after stopping the server.  You could schedule these to run inside a script that runs daily or in the startup/shutdown scripts you use to start/stop the servers to ensure permissions are always correct...and make adjustments as necessary.

```

chown --recursive spigot:minecraft /opt/minecraft/spigot
find /opt/minecraft/spigot -type d -exec chmod 0750 {} \;
find /opt/minecraft/spigot -type f -exec chmod 0640 {} \;
chmod --recursive 440 /opt/minecraft/spigot/*.jar

```

```

chown --recursive hungergames:minecraft /opt/minecraft/hungergames
find /opt/minecraft/hungergames -type d -exec chmod 0750 {} \;
find /opt/minecraft/hungergames -type f -exec chmod 0640 {} \;
chmod --recursive 440 /opt/minecraft/hungergames/*.jar

```

You then start Minecraft using that account inside a screen session.  You never actually login using that account.  You just run screen/Minecraft with that account.

Here is the crux to the main command to start Minecraft:

```
su spigot --command "screen -d -m -S spigot -t spigot java -d64 -XX:MaxPermSize=256M -Xincgc -Xmx4096 -jar /opt/minecraft/spigot/server.jar --log-strip-color"
```

The user in the above example is called "spigot" as signified in the switch user part: "su spigot"
I also used the same name for the screen session name "-S spigot" and the screen title "-t spigot" but that is not important other than signifying which user is attached to that screen when you have many screens running.
The folder path used is /opt/minecraft/spigot/ in this example.  Others could be placed in similar location reflecting a different username/folder such as hungergames "/opt/minecraft/hungergames/"

Once the screen session is running, you need a way to send console commands such as the command to "stop" the server.

Here is an example for stopping the server that was started from the example above using the "spigot" user:

```

su spigot --command "screen -S spigot -p spigot -X stuff \"stop\""
su spigot --command "screen -S spigot -p spigot -X eval \"stuff \015\""

```

Here is an example for stopping the server that was started from the example above using the "hungergames" user:

```

su spigot --command "screen -S hungergames -p hungergames -X stuff \"stop\""
su spigot --command "screen -S hungergames -p hungergames -X eval \"stuff \015\""

```

The user is switched to the specified user (spigot or hungergames in these examples) and runs the screen command specifying the session and pre-selects the screen window and pushes the characters ***stop*** but because the command is already encased in quotes because of ***--command***, we must escape the quote used to encase the ***stuff*** parameter which just means you add a backslash for each of the inside quotes used.

The 2nd line does the same thing but presses the carriage return key which is needed or the console will never execute what was typed in.  The ASCII value for carriage return is 015 and the eval lets it translate that code into the actual return key.

All of this and more can be placed in scripts to help automate everything.  Daily reboots, shutdown notifications, repeating messages to online players, etc.

I think I have covered your question as thorough as I can.  Feel free to ask for more clarification if needed.

LHammonds

---

### Post by ameinild on 2021-02-18
> **LHammonds said:**
> its been a long time since I setup a Minecraft server.

I was at a loss at first, but then noticed the very subtle "mc server" - I didn't spot it had anything to do with minecraft at first.

---

### Post by xeneration on 2021-02-18
Thank you very much for the help. It seems to be working great so far :)

---

