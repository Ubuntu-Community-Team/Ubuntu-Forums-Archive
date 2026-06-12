---
title: "HLDS Problem"
date: 2009-08-15
forum: Server Platforms
---

### Post by er4o on 2009-08-15
Hello, I got a problem with the HLDS which I want to run it on Ubuntu Server Edition. The problem is that after the putty stops, the hlds doesn't want to change the map (it crashed). I tried with nohup ./hlds_run <and so on> & but the CPU is going to 99.9%. Also I tried with screen, but when I close the putty it crashes again.

---

### Post by er4o on 2009-08-16
Anyone? :confused:

---

### Post by dfreer on 2009-08-16
Let me see if I get this straight: you are using SSH to access your server, and after you launch the server and close the putty window, your server executable is no longer running?

If I got that right, the first thing I'd recommend would be to try launching it with screen. I used screen to monitor 3 CS:S servers and it worked great for me. However it appears you have already tried that and it didn't work for you. Could you paste the command that you used to launch screen + HLDS? Perhaps there is an error that you missed.

---

### Post by er4o on 2009-08-16
Thanks for the reply dfreer!
Well yes, mainly that is my problem. So here is my line - 
*@*:~/hlds/Server1$ screen -A -m -d -S hlds_classic ./hlds_run -game cstrike +maxplayers 16 +map de_dust2 -binary ./hlds_i686 and when i close the putty with Control + A + D, when the timelimit is 0, before changing the map it just crashesh with error changelevel to 'cs_assault' failed, but cs_assault exists on the server.
Thanks!

---

### Post by dfreer on 2009-08-17
Hmmm well, that's the exact same arguments I gave to screen in my init scripts. Does this same error occur when you *don't* close putty or the screen session (best if you can start HLDS locally on the server itself, and observe it there), and change the map to cs_assault? 

My original thought was that HLDS was crashing due to you ending your session (killing all running programs), but perhaps the error is not related to screen/putty.

---

### Post by er4o on 2009-08-17
Well, when the putty is open, the server is not crashing. I test it, and when close the putty, shows me this strange error. Something its something with models - Bad model models/player/player.mdl or something.

---

### Post by er4o on 2009-08-17
It may be something with the SSH server?

---

### Post by dfreer on 2009-08-17
Try running HLDS on the server itself (e.g. locally, not using SSH/screen), leave the HLDS server console open and changelevel as you normally would. If the error still occurs you should be able to rule out SSH and screen (since they wouldn't be involved), which is what I suspect is happening (I can't think of a reason why SSH would cause a map not to load/error in player model).

There may be some unique difference between HLDS and SRCDS (Source Dedicated Server), that I'm unaware of since I've only dealt with SRCDS, but I'm really thinking there is something wrong with your HLDS setup that is causing these errors.

---

### Post by er4o on 2009-08-17
Okay thanks, I will try that tomorrow.

---

