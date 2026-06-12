---
title: "HOWTO: Share sound from one computer to another"
date: 2011-10-23
forum: Tutorials
---

### Post by krippa on 2011-10-23
**Introduction**
This howto describes how I (finally!) managed to stream local audio from all our households laptops to a linux box connected to the stereo and now we can play music in everything from spotify to rhythmbox and listen to it through the stereo. Throughout this howto I will refer to the server (connected to stereo) and clients (will play the sound and send to server) Feel free to suggest improvements/alternate solutions because there might very well be an easier way to do this.

Note: This solution produces a ~10second delay so it may not be suited for watching video but for music this doesn't really matter.

**Howto Overview:**
1 - Install icecast2 on server to receive audio from clients
2 - Install darkice on client(s) and start sending to icecast2
3 - Use mpg123 on the server to play the stream created by icecast2
4 - Optional - Make the sound on the server run forever
5 - Optional - Create launchers to easily start/stop audio sharing

**Step 1. Installing icecast2**

Install the package "icecast2" on the server, either using ubuntu software center or by pasting the following to the terminal:

```
sudo apt-get install icecast2
```

Configure icecast2 by editing the following file as super user: /etc/icecast2/icecast.xml. For example by hitting alt+F2 and pasting: ```
gksu gedit /etc/icecast2/icecast.xml 
```and entering your password.

In this file locate and make sure you change at least the following:

source-password (choose a password to be used by clients)
admin-password (choose an admin password to avoid anyone getting into your icecast)
port (if you need to use a port different than 8000 which is the default)

Save and start the icecast2 daemon (from a terminal):

```
sudo /etc/init.d/icecast2 start
```

**Step 2 - Install and start darkice on a client computer**

Install the package darkice from ubuntu software center.

For some reason this does not create a config file in the default folder so you need to copy the config example from /usr/share/doc/darkice/examples/darkice.cfg to /etc/darkice.cfg:

```
sudo cp /usr/share/doc/darkice/examples/darkice.cfg /etc/darkice.cfg
```

After that please configure darkice: (to edit as super user type: sudo gedit /etc/darkice.cfg)

duration - set to 0 or darkice will terminate after playing the amount of seconds specified here.
device - I set it to "default" which seems to work

in the [icecast2-0] section:
format - I set this to "mp3"
bitrate - I increased this to 192 to improve quality
server - the IP address or host name of the server configured in step 1
port - the port of the server - 8000 - unless you changed this in step 1
password - the source-password you configured on step 1
mountPoint - name of the stream (this will be available at the server as: [http://server-name/mountPoint](http://server-name/mountPoint)), I simply set it to "stream"

Remove any config section below this since darkice wont start if you leave the sections below without configuring them properly - you don't need them for this HOWTO.

Start streaming to server by running:

```
/usr/bin/darkice
```

**Step 3 - Play the stream on the server using mpg123**

On the server install the package mpg123:

```
sudo apt-get install mpg123
```

Start playing the sound from the stream by starting mpg123 with a link to the stream, for example:

```
mpg123 http://localhost:8000/stream
```

If you're lucky you will now hear all your local audio played on the server!

Step 4 - Optional - Make the sound on the server run forever

As you will soon notice, as soon as the stream stops, mpg123 will quit. To avoid this you can use the following shell script that will try to play the stream every 10 seconds:

#!/bin/bash
while :
do
    mpg123 "http://server1:8000/stream"
    sleep 10
done


**Step 5 - Optional - Create launchers to easily start/stop audio sharing**

In order to easily start/stop audio I created a couple of launchers to start and stop sharing. To do this you need to create a couple of .desktop files in /usr/share/applications/

To edit the start launcher run:

```
gksudo gedit /usr/share/applications/start-audio.desktop
```

Paste the following (you need to specify an icon, I just got one I liked from [http://findicons.com/search/music](http://findicons.com/search/music)) and save:

```
[Desktop Entry]
Name=Start Sharing Audio to Server
Comment=
Exec=/usr/bin/darkice
Icon=PATH TO YOUR ICON OF CHOICE
Terminal=false
Type=Application
StartupNotify=true
```

```
gksudo gedit /usr/share/applications/stop-audio.desktop
```

```
[Desktop Entry]
Name=Stop Sharing Audio to Server
Comment=
Exec=killall darkice
Icon=/usr/share/icons/128/close_music.png
Terminal=false
Type=Application
StartupNotify=true
```

After saving these two files you should now be able to easily start and stop audio sharing :)

---

### Post by majedaly on 2011-11-09
Worked perfectly for me.
Thanks

---

### Post by Jose Catre-Vandis on 2011-11-11
In a similar vein:

[http://bimma.me.uk/2010/12/26/linux-listen-to-microphone-on-remote-pc/](http://bimma.me.uk/2010/12/26/linux-listen-to-microphone-on-remote-pc/)

---

