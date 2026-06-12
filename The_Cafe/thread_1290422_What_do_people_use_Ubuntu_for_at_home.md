---
title: "What do people use Ubuntu for at home?"
date: 2009-10-13
forum: The Cafe
---

### Post by dchurch24 on 2009-10-13
In my house I have a touchscreen attached to a machine running Xubuntu. My main TV is ubuntu 8.04 running MythTV. This machine has an ADU200 unit plugged into it and also an 8-way USB relay.

Also on that machine it runs a Python TCPIP listener that listens for commands to execute.

On the touchscreen machine, I can touch a "button" - it's SDL so not really a 'button' more of a 'sprite' - and turn the lights on, turn the amp on, return the Mythbox to the menu, open the front door etc...

I also have a MyBookWorld that is hacked and running linux that I use as a file server (it's not running Ubuntu, that would probably kill the poor 32mhz processor!).

I have another box running 8.04 running MythFrontend - that also has a 8 way relay plugged into it. On that one however, there is a wireless remote-control that I have opened up and shorted the connections into the relay switches. The remote control is one from those kits you can buy for around 10 quid where you can remotely turn on and off power sockets. This way, I can remotely turn off lamps, amplifiers etc... without wires. The lamps in that room ARE wired as there was little point wasting the wireless plugs when the lamp was right next to the PC/Relay.

I also have another 8.04 box (server edition) that hosts a MySQL DB with tables that hold the wherabouts of each device that can be controlled.

So, each 'client' can talk to each 'server' and vice-versa.

To find which machine controlled the front door, I would simply have the client do this:

"select * from automation where room='front' and device='door' and action='on';"

The IP address of the machine with the relay that controls the door would be returned along with the command to switch the correct relay (./adu sk2 for example).

On my *big* machine, I have a VM setup using VirtualBox running Trixbox with a free SIP *in* number. I have real exentions set up so that the mythboxes can be called. Each mythbox has a Centronix wireless headset and mic, so you can answer the phone from anywhere in the house, but callers can be directed through to whichever room they want (provided it's one that has a Mythbox - there are 4 in this house).

The added advantage of this is that I can have 'secret' exentions that I can call that execute Python scripts to lookup which machine to execute the commands on. This way, if, for instance I forget my keys and leave them indoors, I can simply phone up from my mobile phone and tap in the 'secret' exention that opens the front door, and voila! I'm back in the house.

I can control each and every device through cron or through a command line, so even when abroad I can turn lights on and off, open the door if there's someone who wants to drop of a parcel etc...  I even have a 'holiday' mode which randomizes the times that lights come on and turn off within a given time frame so that the house looks occupied and without any pattern that might be recognised.

Just recently, I have started work on my 'whole house audio' which is basically a media centre that I have written in Mono/SDL that checks a central playlist table (on the MySQL server) for songs to play. Each song will have a 'room id' attached to it, so each machine running the media centre knows if it is to play that song, or wait for another. On the touchscreen box a user can select which room they want the music to play in - if they don't choose one it defaults to the living room.

The next step which I have to implement is to have cheap webcams detect movement and tell one of the machines with another 8 way relay - which I have yet to buy - which room I'm in and have it switch the speaker output to that room, and perhaps switch off the room I've just walked from.

I'd love to do face recognision with it too, so that it could randomly choose a song it knows I like when I walk in, or if my GF is with me, it could choose a song of her liking instead - this is half way there, as when you choose music through either the touchscreen box or the media centre, you can choose to tell it who is choosing songs - this way, I've built up a table of most commonly played songs and by whom. One of the options on the touch screen is "random song" - you can make it choose from the top 100 most common, or from the whole lot.

I can't imagine just how difficult this whole setup would have been if I had not discovered Ubuntu and still used Windows.

Anyway, has anyone else done anything interesting with Ubuntu?

PS. I can post screenshots if anyone is interested.

---

### Post by dchurch24 on 2009-10-13
The only annoying thing is that the adutux kernel support seems to have dissapeared after 8.04 :-(

---

### Post by wyliecoyoteuk on 2009-10-13
Wow, Adventurous or what?

I use Mythbuntu on my media server/PVR with Zoneminder for security cams, I use Opensuse on a nettop in my kitchen, which functions as a jukebox/digital picture frame/recipe database/web browser and Skype point. It also runs a MythTV frontend, and plays files from the Mythbuntu box.
I use UNR on my Acer aspire one, and Opensuse on my main PC.

To be honest, I am not a fan of Gnome, which is probably why I don't use Ubuntu more.

---

### Post by Excedio on 2009-10-13
> **dchurch24 said:**
> ....I'd love to do face recognision with it too, so that it could randomly choose a song it knows I like when I walk in, or if my GF is with me, it could choose a song of her liking instead - this is half way there, as when you choose music through either the touchscreen box or the media centre, you can choose to tell it who is choosing songs - this way, I've built up a table of most commonly played songs and by whom. One of the options on the touch screen is "random song" - you can make it choose from the top 100 most common, or from the whole lot....
 
 
First...... =D> (I couldn't find a drueling smiley)
Second...... I would LOVE some screenshots
Third...... Not sure if this would be of help to you, but here you go.
 
[Image Recognition Neural Networks, Open Sourced]("http://tech.slashdot.org/story/09/10/12/0345210/Image-Recognition-Neural-Networks-Open-Sourced")

---

### Post by wyliecoyoteuk on 2009-10-13
Actually, I have one of those remote setups too ( a slightly more expensive one, which can control up to to 16 devices), but I just use a central timer remote unit to switch lights on and off, at night or when on holiday.
I might get a couple more units and use it to control the wireless speakers that I have in the kitchen and dining room (the living room media server and the Kitchen PC both have wireless transmitters for the speakers)

---

### Post by nothingspecial on 2009-10-13
Sorry to be boring but I just use it to stream media, and generaly **** about.

---

