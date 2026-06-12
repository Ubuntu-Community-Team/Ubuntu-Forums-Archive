---
title: "IDS auditory alarm"
date: 2007-11-26
forum: Server Platforms
---

### Post by MaindotC on 2007-11-26
I like the tutorial on setting up snort to interact with ACIDBASE and MySQL.  How do I get the IDS to sound an alarm when inappropriate activity is coming through the NIC ?

---

### Post by craigp84 on 2007-11-29
Step 1. Choose your alarm hardware...

If you're just going for the built in PC speaker on your server, then "sudo apt-get install beep". This package allows you to easily make a 2-tone ringing alarm sound from the server.

If you're going for wiring up some speakers to an isntalled soundcard, then  i guess you could just launch something simple like oggplay with the filename of an alarm sound file.

There are "alarm" boards out there that plug into USB or parallel ports (although my quick google there didnt turn them up!). I don't know how the driver situation is with this type of solution, and it's another expense where the above 2 x are essentially free.

Step 2. Launch the script / program that causes the alarm to ring when the alert condition arises. I don't know the software you;re talking about so can't help there.

If it doesn't have the ability to launch a command on alert, then a simple shell or perl script to hoover the log file looking for alerts would do the trick.

HTH,

-c

---

### Post by MaindotC on 2007-12-02
Hey, craig.  Thanks so much for your reply.  What you typed makes a lot of sense, I'm just not familiar with scripting or how to make sure that script is executed in the event an alarm is triggered from snort.  I'm assuming there must be some type of process that constantly checks the output of snort and the minute it sees something is generated in the text file then it will execute the alarm.

It's just kind of difficult when you're tasked to set up an IDS using all these great tools - I'm in the Network Administration program, not the comp sci program - but have no idea of the science of how they work :(  Thank you again for your reply.

---

