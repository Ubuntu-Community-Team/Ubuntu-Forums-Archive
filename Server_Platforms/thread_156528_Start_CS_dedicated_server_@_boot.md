---
title: "Start CS dedicated server @ boot"
date: 2006-04-07
forum: Server Platforms
---

### Post by indispus on 2006-04-07
Hi there!
I've installed a dedicated CS1.6 server on my personal Ubuntu server( 86.55.237.18 ).
I start my server with the fallowing commands:

```
~: cd /srv/games/hl/
~: sudo ./hlds_run -game cstrike +ip 86.55.237.18 +sv_lan 1 -nomaster +maxplayers 18 +map de_aztec
```

Question: How can i make my CS1.6 server start automatically @ boot, like a deamon?




P.S.: Yes, I am a n00b ](*,)!

---

### Post by robert_pectol on 2006-04-08
You are welcome to use my Ubuntu Startup Script Generator to make a startup script for your CS server.  Just fill in the blanks and click the, "generate" button.  Here's the URL:
[http://rob.pectol.com/content/view/17/33/](http://rob.pectol.com/content/view/17/33/)

I quickly generated one for you based on your post above.  It should run ok but if not, you may need to, "tweak" it a little.  Anyway, you can download the one I generated for you, here:
[http://rob.pectol.com/startup_scriptbuilder/cs1.6.sh](http://rob.pectol.com/startup_scriptbuilder/cs1.6.sh)

Copy or move it to your /etc/init.d/ directory and test it out with, "sudo /etc/init.d/cs1.6.sh start" to see if it works as expected.  Once you have one that works, then simply do, "sudo update-rc.d cs1.6.sh defaults" to add it to your boot-up sequence.  Enjoy!

---

### Post by indispus on 2006-04-08
Thank you robert for your help... Your script generator is very useful.

Problem with the cs1.6.sh script...

```

 * Starting Counter Strike startup script: hlds_run
start-stop-daemon: group `ame' not found
 (Success)

```

Start function:

d_start() {
	start-stop-daemon --start --quiet --pidfile /var/run/hlds_run.pid --exec /srv/games/hl/hlds_run -g**[COLOR="Red"]ame[/COLOR]** cstrike +ip 86.55.237.18 +sv_lan 1 -nomaster +maxplayers 18 +map de_aztec
}

I've tried with quotes, but it doesn't work either.....

d_start() {
	start-stop-daemon --start --quiet --pidfile /var/run/hlds_run.pid --exec [COLOR="Red"]'[/COLOR]/srv/games/hl/hlds_run -game cstrike +ip 86.55.237.18 +sv_lan 1 -nomaster +maxplayers 18 +map de_aztec[COLOR="Red"]'[/COLOR]
}

HELP plz...

---

### Post by robert_pectol on 2006-04-09
Ya found a bug in my startup script generator...  Thanks! :)  At least I think it's fixed now.  Anyway, you can either re-generate it or download the one I generated for you (same URL as I replaced the defective one).  Let me know if it works.  Not having that particular server daemon to test out on my system makes it tough to debug any particularities with it.  But I did indeed find and fix a valid bug so give it a try.  Also, the one I generated for you was done as though it were a daemon process.  If it doesn't respond properly, perhaps it might work better as a non-daemon or, "Other" as specified on the script generator page.  But do give it a try before regenerating it with the, "Other" option.  I'm interested to know if I've fixed the problem.  Good luck!

---

### Post by indispus on 2006-04-09
d_start() {
	start-stop-daemon --start --quiet --pidfile /var/run/cs1.6.pid --exec /srv/games/hl/hlds_run -- [COLOR="Red"]-game cstrike[/COLOR] +ip 86.55.237.18 +sv_lan 1 -nomaster +maxplayers 16 +map de_aztec
}

```
 * Starting Counter Strike Server: hlds_run
Invalid game type 'cstrike' sepecified.
```

It's not takeing the "-game cstrike" parameter....

---

### Post by robert_pectol on 2006-04-09
That's odd!  It looks like maybe the hlds_run command is taking issue with the options passed to it.  At the command prompt, try just running the command:
```

sudo /srv/games/hl/hlds_run -game cstrike +ip 86.55.237.18 +sv_lan 1 -nomaster +maxplayers 18 +map de_aztec
```
...and see if you get that same error (Invalid game type 'cstrike' sepecified.).  If you do, then double-check the options you're passing to it, make any corrections, and re-generate your script if needed.

---

### Post by indispus on 2006-04-09
Robert... I get the same error. But....

```
cd /var/games/hl/
sudo ./hlds_run -game cstrike +ip 86.55.237.18 +sv_lan 1 -nomaster +maxplayers 16 +map de_aztec
```That works fine...

```
sudo /srv/games/hl/hlds_run -game cstrike +ip 86.55.237.18 +sv_lan 1 -nomaster +maxplayers 16 +map de_aztec
```That doesn't work.



wtf?

---

### Post by robert_pectol on 2006-04-09
Ahh... I see what the problem is.  Apparently hlds_run relies on other files within the same directory in which it's located and it's probably referring to those files using relative paths.  Try adding the path (/srv/games/hl) to the, "PATH" var at the top of the script and see it that works.  If it doesn't, let me know as I've got a couple of other options for you to try.  You're getting closer though!  :)

---

### Post by indispus on 2006-04-09
```
PATH=:/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/srv/games/hl
```

Still not working :(
Show me the other 2 options plz... :-k

---

### Post by robert_pectol on 2006-04-09
Yeah, that was an oversight.  Here's something I know will work but it's not the most elegant solution...  Put, "cd /srv/games/hl" somewhere at the top of the script (like right below the, "PATH" line) and that *should* work.  I'll try to think of a better alternative in the meantime.  You might also look at the options and switches you can give the hlds_run command.  Perhaps there's a switch that will let you, "point" to the base directory of /srv/games/hl for it's support files.  If so, then that would be the ideal way.  If not, then just do as I suggested with adding the, "cd /srv/games/hl" line.  Let me know.

---

### Post by indispus on 2006-04-09
Deam'...Still not working ](*,).

Here is the hlds_run file:

[http://www.indispus.evonet.ro/hlds_run](http://www.indispus.evonet.ro/hlds_run)

---

### Post by robert_pectol on 2006-04-09
That almost *has* to work!  If it doesn't, then I'm afraid I can't help further.  All I can suggest is to double-check that you didn't mistype anything and verify the path to the hlds_run executable again.  Try placing the, "cd /path/to/hlds_run/dir" line just above the line near the top that says, "# Start function" and try it again.  If that doesn't work, then I'm out of suggestions for now.  Good luck and if I think of anything else to try, I'll pass it along.  :confused:   <--- me!

---

### Post by indispus on 2006-04-10
Here he is... :-D

```
#!/bin/sh

cd /srv/games/hl/
PORT="27015"

case "$1" in
start)
sudo screen -A -m -d -S cs ./hlds_run -game cstrike +ip 86.55.237.18 -nomaster +maxplayers 16 +map de_dust2
;;

stop)
screen -r hlds01 -X quit
echo Server has been stopped!
;;

*)
echo "Usage: hlds {start|stop}"
exit 1
;;

esac
exit 0
```

P.S.: 10Q robert for your help!

---

### Post by dynamicres on 2007-01-07
hey guys!
ive followed your conversation and was kinda curious as to your "screen" setup.
i installed the app thru aptitude but no "screens" ever pop up or anything. therefore it cant kill the servers or something =/

btw thats a great idea with the startup compiler, seems really close to a finished version!

---

