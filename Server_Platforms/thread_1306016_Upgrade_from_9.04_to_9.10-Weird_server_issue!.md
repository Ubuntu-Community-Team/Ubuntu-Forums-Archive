---
title: "Upgrade from 9.04 to 9.10-Weird server issue!"
date: 2009-10-30
forum: Server Platforms
---

### Post by danooch13 on 2009-10-30
Hello,

Yesterday I upgraded my Ubuntu webserver/mysql server from 9.04 to 9.10 by using the usual command sudo do-release-upgrade.  

All upgraded well, with no errors, and I rebooted the server, and all worked fine for about 30 mins or so.  I was able to ssh and see my website.  

After about 30 mins, the server became unresponsive, meaning that you could not ssh, view the website, or even ping, but the machine is still on.  Rebooted again, it worked again for a little while, then the same issue happened, just dead.

A note about this server is that it is hooked up without any accessories, meaning it only has a network cable and a power cable.  It was on for months straight like this, but since the upgrade it just dies after a little while of being on.

So I said to myself, let me hook it up to a monitor and keyboard and see if I can catch this error on the terminal.  I left it on and in about 30 mins the server was fine...hmmmmm...so I went to sleep and left it that way all night for about 7-8 hours.  I woke up in the morning to check and it was still on, so I said, hmmm must have been just a glitch, so I hooked it back up in the server room with just a network cable and a power cable.

Withing 30 min, it happened again the server just became unresponsive.  It was fine as soon as I turned it on, but about 30 min later, it just died again.  Seems to have something to do with a monitor or keyboard being hooked up to it.

Any ideas what I can do?  I cant have a monitor and keyboard hooked up to it where it is.

Any help would be appreciated.

Thank you.

---

### Post by elvinatom on 2009-10-30
I had that phenomenon once.  I did however hook up a monitor and keyboard then and as soon as I turned on the machine, an endless list of the same error was repeated - I don't remember what it was.  Bottom line: the OS could not handle more then so-and-so many thousands of that error.  It was some software problem that could be fixed easily.  Just a thought ...

---

### Post by danooch13 on 2009-10-30
Funny thing is, when I had it hooked up to the monitor all night, nothing showed up on the screen.  It was just a nice clean login screen.

Syslog showed nothing either from the times it did lock up.

---

### Post by elvinatom on 2009-10-30
is the system responsive to direct kb input when the net died - maybe issue with nic under 9.10?  btw, sometimes the rj45 locking comes off and then the cable can come out of the nic a bit.

---

### Post by danooch13 on 2009-10-30
I checked the cable a few times, lol always start at layer 1 of the osi model!

When it is in the server room, it does not have a keyboard or mouse hooked up to it.  Only thing it has is an ethernet cable and power.

When it was hooked up to a monitor keyboard and mouse, all was fine, it stayed on with no errors and no problems.  It stayed on all night (about 8 hours)

---

### Post by elvinatom on 2009-10-30
just so i understand you correctly - you pulled that thing out of server room and put it on a test bench and it ran 8hrs without any issues (network or otherwise), but as soon as it runs inside the server room it fails within 30min?

That would suggest that the issue is with the server room, isn't that right?  Perhaps something electrical or environmental.  Or do you think it was a lucky glitch that the server ran smoothly on your bench?  In either event, it is for sure a good idea to have a look at what fails.  got a spare nic laying around?  it would then be eth1 and you could put a cable into it after the "crash" - to see if you can ssh into it.  Obviously if you can it's a nic problem.

---

### Post by danooch13 on 2009-10-30
When I pulled it out of the server room, and hooked it up to a keyboard and monitor, yes pretty much a workbench with another network cable plugged into it, it stayed on for 8 hrs no problems, errors, loss of connectivity etc...

As soon as I put it back in the server room without a monitor and keyboard, it works for about 30 min, then goes dead.  The power on the server is on, it is just unresponsive to any network activity, which is all I have at that point because while in the server room all it has is a power and nic cable attached.

Its weird, but I believe it is looking for a keyboard or something which locks it up.  Maybe this new linux kernel???  It was working fine for months until I upgraded to 9.10 yesterday.

I upgraded 3 servers (all no monitor/keyboard) to 9.10 yesterday.  Out of the 3, two of them both have this same problem, that being dead, and the similarities are they they both only have a nic cable attached and power.

---

### Post by elvinatom on 2009-10-30
That is indeed quite strange.  Does your server boot into X (gdm or whatever)?  How about you put that box back onto the bench with only power and nic cable in and wait for it to fail and then plug in kb/monitor to see what went wrong?  Or let the box fail in server room, then type in blindly your username and pw into cli, then 'reboot 0' to see if system is completely crashed.

(And btw, don't you have a ANY monitor/kb in that room that you could share via kvm-box for all your servers, or is your server room like a crack in the wall? lol)

---

### Post by danooch13 on 2009-10-30
It is ubuntu server, so it does not have gnome desktop manager.  Just a regular login.

I was just thinking about doing that.  I will put it on the bench with just a nic and power and when it dies, hook a monitor up to it and see what I find.

I have a kvm switch in the server room, (which is literally a hole in the wall), but I use it for other computers and all the wires are tied neatly and I dont want to take them apart.

I will try what I said above first to see what happens, then I will report back.  I have a strange feeling it is looking for a keyboard....I cant see the monitor causing the issue.

---

### Post by elvinatom on 2009-10-30
It could also be a 9.10 bug, since this version is quite new - with some heavy duty changes.  I somehow find it awfully strange that the system runs for half an hour - no problem - and then dies over a problem that was present since initial boot, but then again ... you never know.

---

### Post by danooch13 on 2009-10-30
yeah it does not make sense with that 30 min stuff.

I will hook it up on the bench without a monitor and keyboard then when it fails (hopefully it does), I will plug in a monitor and see if there is an error...

Only thing is sometimes you need to hit a key to have the screen turn on and show a prompt so hopefully I can plugin a keyboard too and see an error message.

Thanks for your help.  Will report back.

---

### Post by danooch13 on 2009-10-31
OK well at least I narrowed it down to what is causing it, now I just need to know how to fix it.

It seems that I was wrong and it is not the keyboard.  I hooked up just a monitor to the server on my workbench and the server stayed on no problems.  As soon as you turn the server on without a monitor, it will stay on for like 10 min (not 30, guess I really wasnt paying attention to time.)  

So def the monitor.  So then I said maybe it has to be the new kernel and how it shuts of the monitor after a certain amount of time.  So I ran some setterm commands like blank 0 powersave off and powerdown 0, thinking that would prevent the hardware abstraction layer from attempting to turn off a monitor that does not exist.

After running the commands, I moved the server back to the server room, but to no avail.  Same issue happened.  I am sure it has something to do with a monitor not attached, but how do I fix it?

---

### Post by danooch13 on 2009-11-01
Any idea what I can do, I really dont want to have to format because of an upgrade...

---

### Post by elvinatom on 2009-11-04
sry for replying so late, I hope you got it resolved by now, but if not (just as a patch) i would redo the cables in you server room to have kvm to it, even if it's a pain in the neck.

---

### Post by danooch13 on 2009-11-04
Thanks for writing back.

Actually started a more specific thread, and noticed alot of people are having this issue.  We are working on resolving the issue and possibly reporting a bug.

If your interested: [http://ubuntuforums.org/showthread.php?t=1311112&page=4]("http://ubuntuforums.org/showthread.php?t=1311112&page=4")

---

