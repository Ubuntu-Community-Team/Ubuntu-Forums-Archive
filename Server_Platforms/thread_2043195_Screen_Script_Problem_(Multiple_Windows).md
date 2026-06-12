---
title: "Screen Script Problem (Multiple Windows)"
date: 2012-08-16
forum: Server Platforms
---

### Post by Jademalo on 2012-08-16
I have been searching for about an hour, and I cant figure out how to do this.

I want to create a screen session called "JadeCraft" with 6 different windows

JadeCraft
JadeCraft Tekkit
JadeCraft TF2
Top
Temps
Shell

These are all invoked from scripts:

bash /home/scotty/Scripts/runme.sh
bash /home/scotty/Scripts/runmetekkit.sh
cd hlds && cd ga* && cd or* && ./srcds_run -game tf -autoupdate -maxplayers 32 -ip 192.168.16.10 +map mvm_coaltown
top
bash /home/scotty/Scripts/tempwatch.sh
empty


Now, what I am wanting to do is make a script that I can run that will automatically create a screen session with that content in it. So far, I have managed to get one window going:

```
screen -d -m -S JadeCraft -t JadeCraft
screen -S JadeCraft -p JadeCraft -X exec bash /home/scotty/Scripts/runme.sh
screen -S JadeCraft -p 1 -X exec bash /home/scotty/Scripts/runmetekkit.sh
```

Now obviously, this doesn't work. The last line does nothing, but it does create a single window with runme.sh running.
The first problem I run into is I can't seem to create another screen window from a script. So I need to figure out how to do that. I also need to figure out how to give that the correct title.
I was thinking something along the lines of this for the third line:

```
screen -S JadeCraft -t "JadeCraft Tekkit" -p "JadeCraft Tekkit" -X exec bash /home/scotty/Scripts/runmetekkit.sh
```

However obviously it 1. Doesn't work, and 2. has nothing in there that says it's making a new window.

I know you can invoke commands on spesific windows using -p (Either 1-9 or the name of the window) but I need to create that window first before it does anything.


tl;dr
How can I get screen to create multiple windows with individual names from a single script that I run on startup?

---

### Post by LHammonds on 2012-08-17
If you have 6 scripts you want to run in screens/windows so you can attach/detach to any you want at will, you just need to start them up like this:

```

screen -d -m -S JC -t JC /home/scotty/Scripts/jadecraft.sh
screen -d -m -S JCTekkit -t JCTekkit /home/scotty/Scripts/jadecrafttekkit.sh
screen -d -m -S JCTF2 -t JCTF2 /home/scotty/Scripts/jadecrafttf2.sh
screen -d -m -S Top -t Top /home/scotty/Scripts/top.sh
screen -d -m -S Temps -t Temps /home/scotty/Scripts/temps.sh
screen -d -m -S shell -t shell /home/scotty/Scripts/shell.sh

```Of course, you could add those commands to the crontab schedule if you want it to create those screens each time the machine reboots so you will always have them available.

You can then list all the screens available by typing this:
```

screen -ls

```If you want to jump into the Top screen, type this:
```

screen -r Top

```When you are done looking at the screen, press CTRL+A to let screen know you are talking to it and then press "d" to detach from that screen.

LHammonds

---

### Post by Jademalo on 2012-08-17
Thanks, that's one solution, but I was looking for a slightly more elegant one.

Whereas that opens 6 different screen sessions, I was hoping to only open 1 screen session and have 6 windows nestled within that that I can switch between with CTRL+A Shift+"


Thanks though, this should work in the meantime =]

---

