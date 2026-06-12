---
title: "Ubuntu Server 19.04 systems service for PixArk"
date: 2019-10-02
forum: Server Platforms
---

### Post by silent001 on 2019-10-02
Ihave created a systemd service for a PixArk server on my Ubuntu server. The code is as follows:

```
```
[Unit]
Description=PixArk SilentMecha
After=network.target

[Service]
WorkingDirectory=/PixArk
Type=forking
User=mecha

Restart=always

ExecStart=/usr/bin/screen -S PixArk -d -m ./start_server.sh

ExecStop=/PixArk/rconcli/rcon-cli --config /PixArk/PixArk.yaml "ServerChat SERVER SHUTTING DOWN IN 15 SECONDS..."
ExecStop=/bin/sleep 5
ExecStop=/PixArk/rconcli/rcon-cli --config /PixArk/PixArk.yaml "ServerChat SERVER SHUTTING DOWN IN 10 SECONDS..."
ExecStop=/bin/sleep 5
ExecStop=/PixArk/rconcli/rcon-cli --config /PixArk/PixArk.yaml "ServerChat SERVER SHUTTING DOWN IN 5 SECONDS..."
ExecStop=/bin/sleep 5
ExecStop=/PixArk/rconcli/rcon-cli --config /PixArk/PixArk.yaml "saveworld"
ExecStop=/bin/sleep 1
ExecStop=/PixArk/rconcli/rcon-cli --config /PixArk/PixArk.yaml "DoExit"

[Install]
WantedBy=multi-user.target
```
```

The start_server.sh file looks like this:

```
```
#!/bin/bash
wine64 /PixArk/ShooterGame/Binaries/Win64/PixARKServer.exe CubeWorld_Light?DelayRegisterServer=True?bRawSockets=True?SessionName="SilentMecha"?MaxPlayers=20?RCONEnabled=True?RCONPort=27017? -server -gameplaylogging -log -CULTUREFORCOOKING=en -NoBattlEye -QueryPort=27016 -Port=27015 -CubePort=27018 -cubeworld=SilentMecha -NoHangDetection
```
```

I have it working. It starts and everything however when I run the command `sudo systemctl stop PixArk` it hangs for a very long time then the command finishes. I have created an exact same service for my Minecraft server and it completes as soon as it finishes the last ExecStop command. Is there something I am missing? Please can someone assist me in this as I am not an expert at working with systemd yet. It does stop but it takes longer than with the minecraft server for it to return back to the shell before you can do another command.

So if I run the commands by hand I get everything to complete in 20 seconds. When run in with systemd `sudo systemctl stop PixArk` it takes about a minute to two minutes before it returns to the terminal. The reason why I am trying to find the fault is because how it is supposed to work is safely stop the PixArk server before turning off the system. If it takes to long to complete then I fear it will increase the shutdown sequence by 2 minutes longer than in should. It isn't currently a major issue but I would like to just find where my error is. Maybe I am missing something simple.

---

### Post by howefield on 2019-10-02
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by LHammonds on 2019-10-02
Well, you are using full path names everywhere except these parts:
```
./start_server.sh
```

```
wine64
```

Should not be causing your shutdown command to go slow though but I'd change it to full path anyways.

In order to better troubleshoot what's going on, why not put the stop commands into a single "stop.sh" script and just reference that in the config file?

Then you can add logging lines to the script so you can see exactly where the slowdown is at.

Example:

```

#!/bin/bash
LogFile="/var/log/pixark-stop.log"
rconcmd="/PixArk/rconcli/rcon-cli --config /PixArk/PixArk.yaml"

echo "`date +%Y-%m-%d_%H:%M:%S` - Shutdown initiated." | tee -a ${LogFile}
echo "`date +%Y-%m-%d_%H:%M:%S` -- Shutdown in 15 seconds..." | tee -a ${LogFile}
${rconcmd} "ServerChat SERVER SHUTTING DOWN IN 15 SECONDS..."
/bin/sleep 5
echo "`date +%Y-%m-%d_%H:%M:%S` -- Shutdown in 10 seconds..." | tee -a ${LogFile}
${rconcmd} "ServerChat SERVER SHUTTING DOWN IN 10 SECONDS..."
/bin/sleep 5
echo "`date +%Y-%m-%d_%H:%M:%S` -- Shutdown in 5 seconds..." | tee -a ${LogFile}
${rconcmd} "ServerChat SERVER SHUTTING DOWN IN 5 SECONDS..."
/bin/sleep 5
echo "`date +%Y-%m-%d_%H:%M:%S` -- Saving world..." | tee -a ${LogFile}
${rconcmd} "saveworld"
/bin/sleep 1
echo "`date +%Y-%m-%d_%H:%M:%S` -- DoExit..." | tee -a ${LogFile}
${rconcmd} "DoExit"
echo "`date +%Y-%m-%d_%H:%M:%S` - Shutdown complete." | tee -a ${LogFile}

```

Once you run the "systemctl stop pixark" command, a log will be generated in /var/log/pixark-stop.log and a timestamp will be posted before every command is issued and you will see exactly where your delay is happening (or not happening).

I don't have PixArk to test this but I do play Ark Survival Evolved. ;)

LHammonds

---

