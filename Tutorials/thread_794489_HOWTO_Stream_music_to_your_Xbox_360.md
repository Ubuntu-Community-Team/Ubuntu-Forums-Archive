---
title: "HOWTO: Stream music to your Xbox 360"
date: 2008-05-14
forum: Tutorials
---

### Post by Sonic Reducer on 2008-05-14
i just got X360MeditServe working in Gutsy, then i wrote a shell script to start the program on boot

Step 1: download x360MediaServe v.0.0.2
```
wget http://superb-east.dl.sourceforge.net/sourceforge/x360mediaserve/x360mediaserve-0.0.2.tar.gz
```

Step 2: Unpackage the .tar.gz
```
tar -xzvf x360mediaserve-0.0.2.tar.gz
```

Step 3: (Optional) Rename the folder to .x360MediaServe (i did it to make it hidden in my /home folder and to make everything look neater)
```
mv "x360mediaserve-0.0.2" ".x360MediaServe"
```
```
cd ./.x360MediaServe
```

Step 4: create a script named x360MediaServe.sh in ~/.x360MediaServe and paste this into it
```
#!/bin/bash
cd "~/.x360MediaServe";
./start
```

[QUOTE=Edited]if you don't know how to create a file from the right click menu in a nautilus window, here is the equivalent commands from the command line

first, make the file
```
gedit ~/.x360MediaServe/x360MediaServe.sh
```

paste the shell script from the box above, then save and exit[/QUOTE]

make it executable
```
sudo chmod +x x360MediaServe.sh
```

Step 5: make the script start every boot from **System>Preferences>Sessions**
**Name:** x360MediaServe
**Command:** ~/.x360MediaServe/x360MediaServe.sh
**Comment:** Stream music to your Xbox 360

Step 6A: edit config.xml
```
gedit config.xml
```

paste this into it, making sure to tailor it to your system
```
<Configuration>
	<FriendlyName>**Name**</FriendlyName>
	<MusicDir>**Your Music Folder**</MusicDir>
	<PCMOutput>0</PCMOutput>
</Configuration>
```
remember to edit the bold parts. the name is what you will see on your 360 when you connect to your computer

Step 6B: alternatively, you can go to [http://127.0.0.1:7000/configure](http://127.0.0.1:7000/configure) and set it up, i preferred to edit *config.xml*, but to each their own.

you're finsished. now you can reboot or hit Alt+F2 and type ```
/home/**<Username>**/.x360MediaServe/start
```, wait a few minutes*, then try finding your computer with your 360

* i have roughly 23Gb of music in my ~/Music folder, and it took about two minutes for x360MediaServe to load it all

---

### Post by jtreach on 2008-05-21
This is definitely going to work for Hardy right?

---

### Post by TMcKSmith on 2008-05-21
Why not just use TwonkyMedia?  [http://www.twonkymedia.com/](http://www.twonkymedia.com/)

Very easy, very effective

You can stream videos, pictures, AND music.

Also, if you download the "linux manual install" the "free trial" never expires...

---

### Post by jtreach on 2008-05-21
It doesn't appear to scan my music either right now.... 

Anybody else get this?

---

### Post by davebridges on 2008-05-21
does this find meta tags for music sorting?  does twonkymedia?  i currently use ushare, which just dumps everything into an unsorted mess

---

### Post by S0VERE1GN on 2008-05-21
how do you create the script?
 (step 4?)

---

### Post by wikwanderlust on 2008-05-21
I'd also like to know how to make the script.

---

### Post by Steve Fisher on 2008-05-21
> **wikwanderlust said:**
> I'd also like to know how to make the script.

In the terminal, type
```
gedit x360MediaServe.sh
```
Copy and paste the script as listed, then save and quit.

---

### Post by wikwanderlust on 2008-05-21
Thank you very much. (I'm brand spanking new at this if you didn't figure that out yet.)

---

### Post by phoenix23 on 2008-05-21
I find this to be the easiest way to stream media (audio, video, pics) to a 360

[http://badoh.com/2008/01/howto-stream-music-pictures-and-movies-to-an-xbox-360-with-linux/](http://badoh.com/2008/01/howto-stream-music-pictures-and-movies-to-an-xbox-360-with-linux/)

---

### Post by pmicka on 2008-05-21
@Sonic Reducer, works great. Thanks for the write up!

---

### Post by Sonic Reducer on 2008-05-21
twonky is not a free program, and x360mediashare is free. you might not have to pay for it if you install it a certain way, but i don't like the idea of being supposed to pay for something that is free with windows.

---

### Post by sideshowmel91 on 2008-05-21
Neither this or twonky show up on my 360.

---

### Post by Sonic Reducer on 2008-05-21
look under the current session tab in Sessions (system>preferences>sessions) and see if you see the process going

if you do and still don't see anything click this link [http://127.0.0.1:7000/configure](http://127.0.0.1:7000/configure) and configure x360ms again.

i'm not an expert on this by any means, maybe i just got lucky setting it up

---

### Post by jmcantrell on 2008-05-22
I second Twonky media server. it works great.

---

### Post by offlineryan on 2008-05-27
I have been using Ushare ( [http://ushare.geexbox.org/](http://ushare.geexbox.org/) ) on Gutsy and Hardy without major problems.  Very Small almost no overhead.

---

### Post by Kreuger on 2008-05-27
I tried both programs and both times when I tried to open the config in the browser; nothing loaded.

@ offlineryan: How do I go about setting it up? I grabbed it from the repos. I tried it out and got this:

> kreuger@kreuger-desktop:~$ ushare -c /home/kreuger/Music
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Cannot initialize UPnP subsystem
Stopping UPnP Service ...

---

### Post by Sonic Reducer on 2008-05-28
> **thomasz said:**
> Your instruction is clear to understand, however how can i create at step 4? Thanks.

Step 4: create a script named x360MediaServe.sh in ~/.x360MediaServe and paste this into it

```
#!/bin/bash
cd "~/.x360MediaServe";
./start
```

right-click in the folder ~/.x360MediaServe (~ means your home folder, so ~ means */home/ryan/* to me but might be */home/thomasz/* for you)

select "Create Document" then "Empty File". this will make the actual file. rename it **x360MediaServe.sh** (if you renamed it right the icon will change) and paste what is in the code box into the file, then save and exit.

i'll rewrite that step so the next person doesn't get stuck. thanks for pointing out i wasn't clear there =]

---

### Post by Nowlan1971 on 2008-05-29
> **phoenix23 said:**
> I find this to be the easiest way to stream media (audio, video, pics) to a 360

[http://scrambled.wordpress.com/2008/01/06/howto-stream-music-pictures-and-movies-to-an-xbox-360-with-linux/](http://scrambled.wordpress.com/2008/01/06/howto-stream-music-pictures-and-movies-to-an-xbox-360-with-linux/)

Worked perfect, Thanks phoenix23. I watched a 2 hour movie tonight, streamed perfect, no issues.

Cheers

---

### Post by Kreuger on 2008-05-29
Can anyone help me?

---

### Post by Sonic Reducer on 2008-05-29
> **Kreuger said:**
> Can anyone help me?

it would help if you explained whats going on a bit better.

are you still having problems with the configuration part?

---

### Post by jackal242 on 2008-06-08
I tried this and got a nice overflow error:


Exception in thread "main" java.lang.StackOverflowError
	at sun.nio.cs.UTF_8$Decoder.decodeArrayLoop(UTF_8.java:212)
	at sun.nio.cs.UTF_8$Decoder.decodeLoop(UTF_8.java:358)
	at java.nio.charset.CharsetDecoder.decode(CharsetDecoder.java:544)
	at java.lang.StringCoding$StringDecoder.decode(StringCoding.java:140)
	at java.lang.StringCoding.decode(StringCoding.java:173)
	at java.lang.String.<init>(String.java:444)
	at java.lang.String.<init>(String.java:516)
	at java.io.UnixFileSystem.list(Native Method)
	at java.io.File.list(File.java:973)
	at java.io.File.listFiles(File.java:1051)

---

### Post by Sonic Reducer on 2008-06-08
> **jackal242 said:**
> I tried this and got a nice overflow error:


Exception in thread "main" java.lang.StackOverflowError
	at sun.nio.cs.UTF_8$Decoder.decodeArrayLoop(UTF_8.java:212)
	at sun.nio.cs.UTF_8$Decoder.decodeLoop(UTF_8.java:358)
	at java.nio.charset.CharsetDecoder.decode(CharsetDecoder.java:544)
	at java.lang.StringCoding$StringDecoder.decode(StringCoding.java:140)
	at java.lang.StringCoding.decode(StringCoding.java:173)
	at java.lang.String.<init>(String.java:444)
	at java.lang.String.<init>(String.java:516)
	at java.io.UnixFileSystem.list(Native Method)
	at java.io.File.list(File.java:973)
	at java.io.File.listFiles(File.java:1051)

what command did you issue?

---

### Post by Nephus on 2008-06-11
well, I've got a strange issue.  When I paste the command into the alt+f2 box, it says file not found.  Yet if I paste the exact same line into a terminal window it works.  Does this mean I'm going to have to keep a terminal window open just to use this?

---

### Post by Sonic Reducer on 2008-06-11
> **Nephus said:**
> well, I've got a strange issue.  When I paste the command into the alt+f2 box, it says file not found.  Yet if I paste the exact same line into a terminal window it works.  Does this mean I'm going to have to keep a terminal window open just to use this?

try putting it inside quotes, i know when copying files from the command-line it doesn't like spaces, maybe thats the issue here.

there also might be a typo, a net little trick i figured out (but i'm sure is well known and acting like it's neat will get me branded a n00b) is that if you copy the file in nautilus (right-click, copy) and you paste into a text box, it will pastes the complete path in plain text. i do this to eliminate any typos when i'm making a startup program or launcher.

for example, i just right-clicked and copied a song from my music collection, if i paste into another folder, a duplicate file will be created there, but if i just ctrl+v here i get: **/home/ryan/Music/Bandits Of The Acoustic Revolution/02 - Here's To Life.mp3**

unfortunately, i also pasted the above bolded path directly into the Alt+F2 box, and it accepted the spaces without complaint.

how about you copy the directory address for us?

---

### Post by Nephus on 2008-06-11
Oddly enough, changing ~/.x360MediaServe/x360MediaServe.sh to .x360MediaServe/x360MediaServe.sh fixed it.  I'm not near my linux box right now to give you the exact error, (and my wife is probably using mythtv if I know her, so I couldn't use it anyway) but essentially it was trying to run it in home/nephus/home/nephus/.x360MediaServ.  Not sure what that's all about, but it appears that alt+f2 is automatically running everything from my home dir and specifying it caused a bit of a problem. *shrug* Is that something to do with Hardy or do I have something configured wrong?

---

### Post by Sonic Reducer on 2008-06-12
> **Nephus said:**
> Oddly enough, changing ~/.x360MediaServe/x360MediaServe.sh to .x360MediaServe/x360MediaServe.sh fixed it.  I'm not near my linux box right now to give you the exact error, (and my wife is probably using mythtv if I know her, so I couldn't use it anyway) but essentially it was trying to run it in home/nephus/home/nephus/.x360MediaServ.  Not sure what that's all about, but it appears that alt+f2 is automatically running everything from my home dir and specifying it caused a bit of a problem. *shrug* Is that something to do with Hardy or do I have something configured wrong?

were you trying to run it with
```
home/nephus/home/nephus/.x360MediaServ
```

or

```
/home/nephus/home/nephus/.x360MediaServ
```

it is very important to have that first slash, otherwise you're specifying a folder that isn't in the root filesystem

---

### Post by Nephus on 2008-06-12
Nope just ~/.x360MediaServe/x360MediaServe.sh

here's the error: Could not open location file:///home/nephus/~/.x360MediaServe/x360MediaServe.sh

---

### Post by Sonic Reducer on 2008-06-12
> **Nephus said:**
> Nope just ~/.x360MediaServe/x360MediaServe.sh

here's the error: Could not open location file:///home/nephus/~/.x360MediaServe/x360MediaServe.sh

hmm, the tilde means the home folder for the user you are logged in as, so the complete path you tried to open is:
```
/home/nephus/home/nephus/.x360MediaServe/x360MediaServe.sh
```

that looks like a bug or at least a quirk, though i don't know if it's a quirk of hardy (which there have been enough damn quirks and bugs), a quirk of GNOME, a quirk in the run dialog, or a quirk in something else.

at least you got it working

---

### Post by Nullack on 2008-06-12
I think this howto needs to be reconsidered. What is needed for xbox360 and ps3 serving from linux is a upnp server. The one used in this howto is in alpha, and really isnt robust or feature complete.

IMHO the ideal server is fruppes. It allows for transcoding as well. Anyway I have been trying to get it to work from an SVN build because the last official build has since had bugs corrected. Here is my notes:

FUPPES - FUPPES is a free, multiplatform UPnP A/V Media Server

[http://fuppes.ulrich-voelkel.de/](http://fuppes.ulrich-voelkel.de/)

sudo apt-get install subversion autoconf automake1.9

svn co [https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk](https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk) fuppes

cd fuppes/

autoreconf -vfi

m4_pattern_allow([^AC_DISABLE_STATIC$])
m4_pattern_allow([^AC_PROG_LIBTOOL$])
m4_pattern_allow([^AM_ICONV$])

Its here that I ran into further problems. As you can see the auto conf didnt goto too well and I tried to manually deal with the m4s allowed but then I had further problems.

If someone can figure it out, I think this would be the ultimate solution. We could even look at getting a package into multiverse or something to make it easy???

---

### Post by Sonic Reducer on 2008-06-12
> **Nullack said:**
> I think this howto needs to be reconsidered. What is needed for xbox360 and ps3 serving from linux is a upnp server. The one used in this howto is in alpha, and really isnt robust or feature complete.

IMHO the ideal server is fruppes. It allows for transcoding as well. Anyway I have been trying to get it to work from an SVN build because the last official build has since had bugs corrected. Here is my notes:

FUPPES - FUPPES is a free, multiplatform UPnP A/V Media Server

[http://fuppes.ulrich-voelkel.de/](http://fuppes.ulrich-voelkel.de/)

sudo apt-get install subversion autoconf automake1.9

svn co [https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk](https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk) fuppes

cd fuppes/

autoreconf -vfi

m4_pattern_allow([^AC_DISABLE_STATIC$])
m4_pattern_allow([^AC_PROG_LIBTOOL$])
m4_pattern_allow([^AM_ICONV$])

Its here that I ran into further problems. As you can see the auto conf didnt goto too well and I tried to manually deal with the m4s allowed but then I had further problems.

If someone can figure it out, I think this would be the ultimate solution. We could even look at getting a package into multiverse or something to make it easy???

it's kind of off-topic for this thread, and it doesn't even look like it's a better choice that x360MediaServe (it can have every little feature under the sun, but this one works and yours doesn't right now) :p

if you get it working and have a decent write-up i will edit my first post explaining how FUPPES is a better choice and i'll link to your how-to.

i would appreciate if you started your own thread for getting help with FUPPES though, as it is off topic here. when you bury your question on the 4th page of a how-to for a different program youre not likely going to get it answered.

---

### Post by mr2guysingh on 2008-06-14
I am having some trouble. Where should I save the file? It says it cant find it, but when I run it in the terminal, it says permission denied.

---

### Post by Sonic Reducer on 2008-06-15
> **mr2guysingh said:**
> I am having some trouble. Where should I save the file? It says it cant find it, but when I run it in the terminal, it says permission denied.

if you follow my instructions it will save in ~/.x360MediaServe

did you set the file as executable?

---

### Post by jcr1 on 2008-06-16
Sorry if this is the wrong place to ask, but this streaming media to an xbox360, via whichever of the above mentioned methods, what is actually playing the movies? The pc or the xbox? My server is a low spec and would struggle to play decent videos, but the xbox360 should be capable of playing 1080p videos rights?

This is just the first I have heard of this... very interesting.

---

### Post by Sonic Reducer on 2008-07-03
nobody thought i'd like to know lifehacker linked my thread? thanks a lot doods.

[http://lifehacker.com/392336/stream-music-from-ubuntu-to-an-xbox-360](http://lifehacker.com/392336/stream-music-from-ubuntu-to-an-xbox-360)

---

### Post by jcr1 on 2008-07-03
> **phoenix23 said:**
> I find this to be the easiest way to stream media (audio, video, pics) to a 360

[http://scrambled.wordpress.com/2008/01/06/howto-stream-music-pictures-and-movies-to-an-xbox-360-with-linux/](http://scrambled.wordpress.com/2008/01/06/howto-stream-music-pictures-and-movies-to-an-xbox-360-with-linux/)

This was so simple to set up. Thanks!

---

### Post by Twisp on 2008-07-04
I need a little help I got though the steps with relative ease, but when I start the x360MediaShare.sh script, it gives me some feedback of failed SocketConnector at 192.168.1.64 and 127.0.0.1:7000. Then it gives some java errors of addresses already in use. Any help would be great.

Here is an example of when I start the script:
```
/home/dotechis/.x360MediaServe/x360MediaServe.sh: line 2: cd: ~/.x360MediaServe: No such file or directory
xbox360mediaserve, Copyright (C) 2006 Thomas Walker
xbox360mediaserve comes with ABSOLUTELY NO WARRANTY; for details see license
This is free software, and you are welcome to redistribute it
under certain conditions; see license for details.

OS Detected:Linux
Adding artist:
Adding playlist:Streams
Starting media server servlet
Got directory:/home/dotechis/Music
Got File:/home/dotechis/Music/01 - The Ides Of March.mp3
Adding artist:Iron Maiden
New Album:Killers
Setting UDN to uuid:492a4242-22c2-25b1-a112-000001448681
Setting Friendly Name to "x360MediaServe"
Testing interface:192.168.1.64
Interface size:4
Got Interface:192.168.1.64
External Address set to:192.168.1.64
192.168.1.64
2008-07-04 12:27:37.448::INFO:  Logging to STDERR via org.mortbay.log.StdErrLog
Starting Server
2008-07-04 12:27:37.462::INFO:  jetty-6.0.1
2008-07-04 12:27:37.574::WARN:  failed SocketConnector @ 192.168.1.64:7000
2008-07-04 12:27:37.575::WARN:  failed SocketConnector @ 127.0.0.1:7000
2008-07-04 12:27:37.575::WARN:  failed Server@1507fb2
org.mortbay.util.MultiException[java.net.BindException: Address already in use, java.net.BindException: Address already in use]
	at org.mortbay.jetty.Server.doStart(Server.java:192)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:38)
	at net.sourceforge.x360mediaserve.newServlet.WebServer.start(WebServer.java:36)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setUpWebServer(MediaServer.java:114)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setup(MediaServer.java:100)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.<init>(MediaServer.java:70)
	at Run.main(Run.java:57)
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:336)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.mortbay.jetty.bio.SocketConnector.newServerSocket(SocketConnector.java:78)
	at org.mortbay.jetty.bio.SocketConnector.open(SocketConnector.java:72)
	at org.mortbay.jetty.AbstractConnector.doStart(AbstractConnector.java:313)
	at org.mortbay.jetty.bio.SocketConnector.doStart(SocketConnector.java:136)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:38)
	at org.mortbay.jetty.Server.doStart(Server.java:217)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:38)
	at net.sourceforge.x360mediaserve.newServlet.WebServer.start(WebServer.java:36)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setUpWebServer(MediaServer.java:114)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setup(MediaServer.java:100)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.<init>(MediaServer.java:70)
	at Run.main(Run.java:57)
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:336)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.mortbay.jetty.bio.SocketConnector.newServerSocket(SocketConnector.java:78)
	at org.mortbay.jetty.bio.SocketConnector.open(SocketConnector.java:72)
	at org.mortbay.jetty.AbstractConnector.doStart(AbstractConnector.java:313)
	at org.mortbay.jetty.bio.SocketConnector.doStart(SocketConnector.java:136)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:38)
	at org.mortbay.jetty.Server.doStart(Server.java:217)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:38)
	at net.sourceforge.x360mediaserve.newServlet.WebServer.start(WebServer.java:36)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setUpWebServer(MediaServer.java:114)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setup(MediaServer.java:100)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.<init>(MediaServer.java:70)
	at Run.main(Run.java:57)
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:336)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.mortbay.jetty.bio.SocketConnector.newServerSocket(SocketConnector.java:78)
	at org.mortbay.jetty.bio.SocketConnector.open(SocketConnector.java:72)
	at org.mortbay.jetty.AbstractConnector.doStart(AbstractConnector.java:313)
	at org.mortbay.jetty.bio.SocketConnector.doStart(SocketConnector.java:136)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:38)
	at org.mortbay.jetty.Server.doStart(Server.java:217)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:38)
	at net.sourceforge.x360mediaserve.newServlet.WebServer.start(WebServer.java:36)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setUpWebServer(MediaServer.java:114)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setup(MediaServer.java:100)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.<init>(MediaServer.java:70)
	at Run.main(Run.java:57)
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:336)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.mortbay.jetty.bio.SocketConnector.newServerSocket(SocketConnector.java:78)
	at org.mortbay.jetty.bio.SocketConnector.open(SocketConnector.java:72)
	at org.mortbay.jetty.AbstractConnector.doStart(AbstractConnector.java:313)
	at org.mortbay.jetty.bio.SocketConnector.doStart(SocketConnector.java:136)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:38)
	at org.mortbay.jetty.Server.doStart(Server.java:217)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:38)
	at net.sourceforge.x360mediaserve.newServlet.WebServer.start(WebServer.java:36)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setUpWebServer(MediaServer.java:114)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setup(MediaServer.java:100)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.<init>(MediaServer.java:70)
	at Run.main(Run.java:57)


```

---

### Post by Sonic Reducer on 2008-07-04
> **Twisp said:**
> I need a little help I got though the steps with relative ease, but when I start the x360MediaShare.sh script, it gives me some feedback of failed SocketConnector at 192.168.1.64 and 127.0.0.1:7000. Then it gives some java errors of addresses already in use. Any help would be great.

Here is an example of when I start the script:
```
/home/dotechis/.x360MediaServe/x360MediaServe.sh: line 2: cd: ~/.x360MediaServe: No such file or directory
xbox360mediaserve, Copyright (C) 2006 Thomas Walker
xbox360mediaserve comes with ABSOLUTELY NO WARRANTY; for details see license
This is free software, and you are welcome to redistribute it
under certain conditions; see license for details.

OS Detected:Linux
Adding artist:
Adding playlist:Streams
Starting media server servlet
Got directory:/home/dotechis/Music
Got File:/home/dotechis/Music/01 - The Ides Of March.mp3
Adding artist:Iron Maiden
New Album:Killers
Setting UDN to uuid:492a4242-22c2-25b1-a112-000001448681
Setting Friendly Name to "x360MediaServe"
Testing interface:192.168.1.64
Interface size:4
Got Interface:192.168.1.64
External Address set to:192.168.1.64
192.168.1.64
2008-07-04 12:27:37.448::INFO:  Logging to STDERR via org.mortbay.log.StdErrLog
Starting Server
2008-07-04 12:27:37.462::INFO:  jetty-6.0.1
2008-07-04 12:27:37.574::WARN:  failed SocketConnector @ 192.168.1.64:7000
2008-07-04 12:27:37.575::WARN:  failed SocketConnector @ 127.0.0.1:7000
2008-07-04 12:27:37.575::WARN:  failed Server@1507fb2
org.mortbay.util.MultiException[java.net.BindException: Address already in use, java.net.BindException: Address already in use]
	at org.mortbay.jetty.Server.doStart(Server.java:192)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:38)
	at net.sourceforge.x360mediaserve.newServlet.WebServer.start(WebServer.java:36)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setUpWebServer(MediaServer.java:114)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setup(MediaServer.java:100)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.<init>(MediaServer.java:70)
	at Run.main(Run.java:57)
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:336)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.mortbay.jetty.bio.SocketConnector.newServerSocket(SocketConnector.java:78)
	at org.mortbay.jetty.bio.SocketConnector.open(SocketConnector.java:72)
	at org.mortbay.jetty.AbstractConnector.doStart(AbstractConnector.java:313)
	at org.mortbay.jetty.bio.SocketConnector.doStart(SocketConnector.java:136)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:38)
	at org.mortbay.jetty.Server.doStart(Server.java:217)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:38)
	at net.sourceforge.x360mediaserve.newServlet.WebServer.start(WebServer.java:36)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setUpWebServer(MediaServer.java:114)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setup(MediaServer.java:100)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.<init>(MediaServer.java:70)
	at Run.main(Run.java:57)
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:336)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.mortbay.jetty.bio.SocketConnector.newServerSocket(SocketConnector.java:78)
	at org.mortbay.jetty.bio.SocketConnector.open(SocketConnector.java:72)
	at org.mortbay.jetty.AbstractConnector.doStart(AbstractConnector.java:313)
	at org.mortbay.jetty.bio.SocketConnector.doStart(SocketConnector.java:136)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:38)
	at org.mortbay.jetty.Server.doStart(Server.java:217)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:38)
	at net.sourceforge.x360mediaserve.newServlet.WebServer.start(WebServer.java:36)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setUpWebServer(MediaServer.java:114)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setup(MediaServer.java:100)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.<init>(MediaServer.java:70)
	at Run.main(Run.java:57)
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:336)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.mortbay.jetty.bio.SocketConnector.newServerSocket(SocketConnector.java:78)
	at org.mortbay.jetty.bio.SocketConnector.open(SocketConnector.java:72)
	at org.mortbay.jetty.AbstractConnector.doStart(AbstractConnector.java:313)
	at org.mortbay.jetty.bio.SocketConnector.doStart(SocketConnector.java:136)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:38)
	at org.mortbay.jetty.Server.doStart(Server.java:217)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:38)
	at net.sourceforge.x360mediaserve.newServlet.WebServer.start(WebServer.java:36)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setUpWebServer(MediaServer.java:114)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setup(MediaServer.java:100)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.<init>(MediaServer.java:70)
	at Run.main(Run.java:57)
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:336)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.mortbay.jetty.bio.SocketConnector.newServerSocket(SocketConnector.java:78)
	at org.mortbay.jetty.bio.SocketConnector.open(SocketConnector.java:72)
	at org.mortbay.jetty.AbstractConnector.doStart(AbstractConnector.java:313)
	at org.mortbay.jetty.bio.SocketConnector.doStart(SocketConnector.java:136)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:38)
	at org.mortbay.jetty.Server.doStart(Server.java:217)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:38)
	at net.sourceforge.x360mediaserve.newServlet.WebServer.start(WebServer.java:36)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setUpWebServer(MediaServer.java:114)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.setup(MediaServer.java:100)
	at net.sourceforge.x360mediaserve.newServlet.MediaServer.<init>(MediaServer.java:70)
	at Run.main(Run.java:57)
```

is something else using port 7000 on your computer? bittorrent or something?

---

### Post by Twisp on 2008-07-04
> **Sonic Reducer said:**
> is something else using port 7000 on your computer? bittorrent or something?

Nothing I know of. I'm running a stock Ubuntu, does anything on that use port 7000?
Is there a program to check what ports are being used?

---

### Post by Sonic Reducer on 2008-07-04
hey, try this out
```
sudo ufw disable
```
and then try it out. the command disable the uncomplicated firewall, which could be blocking your ports

right after you try it out, regardless if it works or not, run:
```
sudo ufw enable
```

let us know if it works then

---

### Post by Twisp on 2008-07-04
Well it didn't change anything, but thanks anyway. Still gave me the failed socketconnection error

---

### Post by Kreuger on 2008-07-06
> it would help if you explained whats going on a bit better. Sorry the 360 I had died so I obviously gave up trying. However, I now have a PS3 and I use MediaTomb but Im unsure if it will work with a 360.

---

### Post by TMcKSmith on 2008-07-06
hmmm...looks like I may have been wrong about Twonky...my "30-day-trial" expired today...looks like I'm going to have to try X360MediaServe

---

### Post by TMcKSmith on 2008-07-06
question - if I already have X360MediaServe running/configured...if I add a new album to my music folder will it automatically pick it up?  or will I have to restart the server and rescan the music folder?

---

### Post by Sonic Reducer on 2008-07-07
> **TMcKSmith said:**
> question - if I already have X360MediaServe running/configured...if I add a new album to my music folder will it automatically pick it up?  or will I have to restart the server and rescan the music folder?

i haven't seen anything about setting a rescan interval (like in the configuration for twonky), and if you look at the output when you start x360 it loads all the library information right at boot.

it looks like you'd need to restart the server.

the process is named "start" when x360 is running, so it's a matter of finding the PID and killing it if it is running, or simply starting it if it isn't running.

you can open up the system monitor, find if "start" is running, then kill and start it, or write a little script to do it for you:

```
gedit ~/.x360MediaServe/x360MediaServe_Switch.sh
```

Paste this into it:
```
#!/bin/bash
if pgrep start
  then
    pkill start && exit
else
  ./start
fi
exit
```
save and exit.

then make it executable:
```
sudo chmod +x ~/.x360MediaServe/x360MediaServe_Switch.sh
```

make a link somewhere it will be easy to find, you could even make an icon on the applications menu or on the panel if you'd like.

of course, i'll give credit where it's due, i did kind of edit the script **mdebusk** proposed [here]("http://ubuntuforums.org/showpost.php?p=3705845&postcount=8")

now i got a couple questions for all the bigger nerds out there, can i safely rename "start" to something a little more unique? i don't want this script to kill something that just uses the same generic process name. also, can i edit my first post to simply use this script here instead of my little three-line masterpiece?

---

### Post by mtgmutton on 2008-07-12
I'm getting a java error... And seeing as I don't know java, I need a little help :)

```
/home/evan/.x360mediaserve/start
Exception in thread "main" java.lang.NoClassDefFoundError: Run
Caused by: java.lang.ClassNotFoundException: Run
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
```

Does anyone know how to fix this?

---

### Post by Fstop on 2008-07-13
I just installed Ubuntu the other day and have been fiddling with it. Streaming to my 360 is important to me, and I thought I'd register to say thank you for your thread. I followed your instructions and everything works great!!

---

### Post by mtgmutton on 2008-07-13
I tried double-clicking the "start" file and running it in the terminal, and i got no errors. I don't know why it was giving me the error before, but it's fixed now :)

---

### Post by Cherry Cotton on 2008-08-01
Ooogh! I had a lot of trouble with transcoding until I realized that I didn't have "lame" (the MP3 encoder) installed. (I did for all the other ones!) For some reason, I just assumed that it would be there, given all the various media-related programs I've installed. Of course, what x360mediaserve needs isn't the "lame" libraries, which was needed for various programs I've already installed, but the "lame" executable itself in the plain "lame" package. Same goes for the other ones, but for some reason "lame" is the one I missed (sheer hubris, I guess).

Oh, and the README file says that if you hear static when trying to play music, try adding "-x" to lame or something like that. What it means is to go into the "ScriptDir" directory ("cd ScriptDir" from the main "x360mediaserve" or "x360mediaserve-0.0.2" directory) and edit a file accordingly. For instance, if you have trouble playing an Ogg Vorbis file--that is, it gives you static--than edit the "ScriptDir/oggmp3" file:

```
$ cd ScriptDir
$ gedit oggmp3
```

(replace "gedit" with another editor if you wish, like "nano")

Then edit this line:

```
sox -t ogg "$var" -t raw -r 44100 -c 2 -w -s - 2>/tmp/oggerr | lame --preset insane -
```

This is the line that actually changes the Vorbis music to MP3 music. Before the | bar is the Vorbis-specific stuff, and after it is the MP3-specific stuff. Since this concerns the MP3-specific "lame," you should be able to extrapolate just fine from this what to do if another of your audio formats starts giving you static problems. (That is, if m4a music is giving you static, look at the "m4amp3" script in the same directory, and this line should look just the same after the bar, and you can make the same changes.)

Anyway, change it to this, and make sure it's all still one line:

```
sox -t ogg "$var" -t raw -r 44100 -c 2 -w -s - 2>/tmp/oggerr | lame -x --preset insane -
```

That is, add the "-x" after the "lame" command. If the "-x" is already there (as it is with "m4amp3"), try removing it. You can always go back and change it as long as you're careful only to add or remove the "-x" parameter.

("-x" has to do with "endian-ness"... I'm sure a programmer here could explain it...)

Okay! One last thing. You should be able to change it to transcode from any format to raw PCM, rather than MP3, by changing the "Output Format" setting in the config XML file or in the Web-based frontend. But! ...I haven't been able to do that! Even if I change it to "PCM" in the Web-based options and confirm it's there in the XML file, the terminal output still shows that this thing is transcoding to MP3 each and every time, and I would imagine transcoding from one lossy format (Vorbis) to another (MP3) results in a lot of loss. Does anyone know why I can't tell this thing to transcode to PCM? Thanks!

---

### Post by Fedora314 on 2008-09-13
There is one more thing I had to do before .flac files would play through the Xbox:

Edit the flacpcm file in the ScriptDir directory and add quotation marks around $var in the bottom line, so that it reads:

```
flac -d "$var"  -c --endian=big --force-raw-format --sign=signed
```

Cheers,
Jeremy

---

### Post by sean01 on 2008-10-04
Thanks for the info sonic.  But I'm having two issues:

1) I can't get the prog to load on startup.  I can get it to start by manually running x360MediaServe.sh , but the sessions manager will not.

2) I have mp3s in my Music folder, but it doesnt seem to see them, or the music folder at all for that matter.  Streams work just fine though.

Any sugestions?  Thanks!

---

### Post by MrBucket101 on 2008-12-11
> **mtgmutton said:**
> I'm getting a java error... And seeing as I don't know java, I need a little help :)

```
/home/evan/.x360mediaserve/start
Exception in thread "main" java.lang.NoClassDefFoundError: Run
Caused by: java.lang.ClassNotFoundException: Run
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
```

Does anyone know how to fix this?

Has anyone else encountered this error?

I am getting the same thing, verbatim...except my username is different

---

### Post by duiu on 2009-01-02
I found a much nicer way to start x360MediaServe automatically. Change the script code to this
```
#!/bin/bash
cd "/home/**Username**/.x360MediaServe";
./start >>/dev/null &
```

Put in your username at **username** (in my case, David).

I like to have the script run without being in the directory, so copy it to your /usr/local/bin folder. This also allows you to not have to have the .sh, and just type x360MediaServe.
```
sudo cp .x360MediaServe.sh /usr/local/bin/x360MediaServe
```

Copy the script to /etc/init.d (assuming you are in the directory of the script) using this code.
```
sudo cp .x360MediaServe.sh /etc/init.d/x360MediaServe
```

Then update init.d
```
sudo update-rc.d x360MediaServe defaults
```

It will now start at startup, not a login. The ampersand makes it run in the background. The /dev/null outputs data to null, so it doesn't get in the way.

---

### Post by duiu on 2009-01-03
See original post. (I edited)

---

### Post by vik.vaughn on 2009-01-04
This is working great for me so far, thanks for the write up!

Does anyone know if it's possible to not sort the songs by title? When I go to play an album, the songs are in alphabetical order, not the order that they would usually play in.

---

### Post by Sonic Reducer on 2009-01-04
> **vik.vaughn said:**
> This is working great for me so far, thanks for the write up!

Does anyone know if it's possible to not sort the songs by title? When I go to play an album, the songs are in alphabetical order, not the order that they would usually play in.

you could use EasyTAG to rename the song titles to **%n - %t** (i.e. 01 - London Calling, 02 - Brand New Cadillac, etc.)

---

### Post by be_placid on 2009-01-09
uShare is an option too:
[http://blog.beplacid.net/2008/11/24/xbox-360-debianubuntu-linux-media-video-music-streaming/]("http://blog.beplacid.net/2008/11/24/xbox-360-debianubuntu-linux-media-video-music-streaming/")

---

### Post by aeilos on 2009-02-08
Don't forget to forward port 7000 on your router if you use this setup. It worked for me, after trying with no success with ushare and fuppes

---

### Post by PhoenixDragon777 on 2009-03-11
> **MrBucket101 said:**
> Has anyone else encountered this error?

I am getting the same thing, verbatim...except my username is different

I've seen this error many many times while developing Java code.  It is spit out by the Java system when it can't find the program you were trying to run.

If you're x360MediaServe.sh script, make sure you have that second line correct (the one that starts with "cd").  If you're trying to run start directly, you have to make sure that it's running from the correct directory.

---

### Post by PhoenixDragon777 on 2009-03-11
> **Sonic Reducer said:**
> i haven't seen anything about setting a rescan interval (like in the configuration for twonky), and if you look at the output when you start x360 it loads all the library information right at boot.

it looks like you'd need to restart the server.

the process is named "start" when x360 is running, so it's a matter of finding the PID and killing it if it is running, or simply starting it if it isn't running.

you can open up the system monitor, find if "start" is running, then kill and start it, or write a little script to do it for you:

```
gedit ~/.x360MediaServe/x360MediaServe_Switch.sh
```

Paste this into it:
```
#!/bin/bash
if pgrep start
  then
    pkill start && exit
else
  ./start
fi
exit
```
save and exit.

then make it executable:
```
sudo chmod +x ~/.x360MediaServe/x360MediaServe_Switch.sh
```

make a link somewhere it will be easy to find, you could even make an icon on the applications menu or on the panel if you'd like.

of course, i'll give credit where it's due, i did kind of edit the script **mdebusk** proposed [here]("http://ubuntuforums.org/showpost.php?p=3705845&postcount=8")

now i got a couple questions for all the bigger nerds out there, can i safely rename "start" to something a little more unique? i don't want this script to kill something that just uses the same generic process name. also, can i edit my first post to simply use this script here instead of my little three-line masterpiece?

I'd guess that you can rename start to something more descriptive without changing anything, it doesn't *look* like it's actually used anywhere.

My solution to the killing x360mediaserve problem was a little different, I modified the start script in x360mediaserve to save off the pid for the java instance (save to /tmp/x360MediaServe.pid), and then wrote the standard init.d start/stop script to kill that pid directly (and erase the .pid file).

Just in case you're curious...
```

user@host:~$ cat /etc/init.d/x360MediaServe.sh
#######################################################
#! /bin/bash
case "$1" in
   start)
      echo -n "Starting x360MediaServe..."
      cd /usr/local/bin/x360MediaServe
      ./start >/tmp/x360MediaServe.log 2>&1 && echo "Ok" || echo "Failed"
   ;;

   stop)
      echo -n "Shutting down x360MediaServe..."
      if [ -e /tmp/x360MediaServe.pid ]
      then
         kill `cat /tmp/x360MediaServe.pid` && rm /tmp/x360MediaServe.pid && echo Ok || echo Failed
      fi
   ;;

   *)
      echo "Usage: $0 {start|stop}"
      exit 1
esac
exit 0
#######################################################

user@host:~$ cat /usr/local/bin/x360MediaServe/start
#!/bin/bash
if [ ! -e /tmp/x360MediaServe.pid ]
then
   java -cp x360mediaserve.jar:lib/cyberlink/clink170.jar:lib/cyberlink/cmgatejava120.jar:lib/jetty/commons-logging.jar:lib/entagged/entagged-audioformats-0.15.jar:lib/jetty/servlet-api-2.5-6.0.1.jar:lib/jetty/jetty-6.0.1.jar:lib/jetty/jetty-util-6.0.1.jar:lib/xerces/xercesImpl.jar:lib/xerces/xml-apis.jar:lib/cyberlink/clinkwrap.jar Run $1 &
   echo $! > /tmp/x360MediaServe.pid
fi

user@host:~$

```

This does not recover automatically from a x360mediaserve crash, I'll have to manually delete /tmp/x360MediaServe.pid (or reboot, letting ubuntu delete it for me).

Also, as a suggestion, you should specify that config.xml goes in the x360mediaserve directory and not in one of the sub-directories.  I could not get the web interface to work because it insists on linking to [http://127.0.0.1:7000/](http://127.0.0.1:7000/) and I'm not accessing the ubuntu box directly (it's actually a headless server sitting in my closet), so I had to take a guess about where to put config.xml.

---

### Post by mamamia88 on 2009-07-15
steps work great but i had to manually start script even after i rebooted any reason that could be?

---

### Post by stonebergftw on 2009-11-16
Hey all.

I followed these instructions exactly, but get the following message on two different Linux systems.

tim@tim-desktop:~/x360MediaServe$ start
start: missing job name
Try `start --help' for more information.

Any ideas?

---

### Post by Nerdfest on 2010-01-17
If your startup script is called start, you should start it with ./start

---

### Post by Puggytree on 2010-03-01
I've just been trying this and for some reason I can't get the tar file, says it's not found?
Any suggestions (I'm copying and pasting the first line and I've checked that I'm not missing a letter or anything

---

### Post by Puggytree on 2010-03-02
Okay, I've got round it... Just waiting for ma 360 to load, I'm guessing it's taking longer because it's finding the files? *hopes*

---

### Post by Kerwinj on 2010-03-14
Puggytree, I have the same problem.  How did you get "round" it?

---

### Post by elidoperezmd on 2010-06-04
HI guys...is all this info current? i see the post stared on 07

thanks

---

### Post by Sonic Reducer on 2010-06-04
i'm the original poster and haven't kept up on it, but i hope someone else has

---

### Post by elidoperezmd on 2010-06-04
> **Sonic Reducer said:**
> i'm the original poster and haven't kept up on it, but i hope someone else has

Hi... but do you still strem to the xbobx with this? or are you using some else?

thanks

---

### Post by Shalmainia on 2010-07-21
Hiya, I'm new to Ubuntu and Linux in general, so I'm looking for a little help. I realize this thread is ancient but when I run the terminal and type the code;
```
wget http://superb-east.dl.sourceforge.net/sourceforge/x360mediaserve/x360mediaserve-0.0.2.tar.gz

```
I get the error;
```
Connecting to superb-east.dl.sourceforge.net|216.34.181.96|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-07-21 10:04:04 ERROR 404: Not Found.

```
I'm going to presume this means the file no longer exists? Well if so, does anyone have a new solution for a noob?

Cheers

---

### Post by Shalmainia on 2010-07-21
Okay this is going to be a long post, I'm a new Ubuntu user so this is way over my head but I'd rather have it working.

I'm trying my best to stream to my Xbox 360, or at least should I say, for my computer to show up on the Xbox.
As I said in the prior post, the coding at the front end of this tutorial doesn't seem to work anymore, missing file.
So I went in search of other tutorials. I tried XBMC and the Xbox 360 (Wireless) didn't pick up on it, I installed the live and it black-screened me and I had to completely reinstall Ubuntu, luckily I only installed the OS yesterday anyway.
So I followed a few tutorials for uShare, by users. My conf now looks as thus;
```
USHARE_NAME=uShare
USHARE_IFACE=eth0
USHARE_PORT=49153
USHARE_TELNET_PORT=1337
USHARE_DIR=/home/barry/desktop/streaming
USHARE_OVERRIDE_ICONV_ERR=
ENABLE_WEB=Yes
ENABLE_TELNET=
ENABLE_XBOX=yes
ENABLE_DLNA=

```

Now when I run ushare -x, it says
```
bind: Address already in use
```

I'm extremely tired now and I 'just want it to work', I've been running in circles for 4 and a half hours and driving my room-mate insane because I'm borrowing his xbox as mine isn't hooked up to the net right now. I've tried changing everything in the conf to what other people have suggested, the one I've shown you is just my latest configuration.

Can anyone please shed some light on my problem, one thing I have noticed is that I can't see the Xbox 360 on my network either, even though it is on. I even added the ports through the firewall with no luck. Please help, thanks.

I'm running on
Ubuntu 10.04 x64 (Lucid)

---

### Post by jamesklyne on 2010-08-12
I installed the .deb Playstation 3 Media Server.

[http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=5589](http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=5589)

I used the manual installation instructions, so can't vouch for the automatic.

I can stream video, pics, and music.

It even transcodes video on the fly.

I started it using[FONT=monospace]

[/FONT]sudo /etc/init.d/pms-linux start

Added my shares...

/media/ExternalHdd/Video
/media/ExternalHdd/Music
/media/ExternalHdd/Pictures

And finally enable media library / cache option under the "Navigation / Share Settings" Tab.[FONT=monospace][/FONT]

---

### Post by Sonic Reducer on 2010-08-13
> **jamesklyne said:**
> I installed the .deb Playstation 3 Media Server.

[http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=5589](http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=5589)

I used the manual installation instructions, so can't vouch for the automatic.

I can stream video, pics, and music.

It even transcodes video on the fly.

I started it using[FONT=monospace]

[/FONT]sudo /etc/init.d/pms-linux start

Added my shares...

/media/ExternalHdd/Video
/media/ExternalHdd/Music
/media/ExternalHdd/Pictures

And finally enable media library / cache option under the "Navigation / Share Settings" Tab.[FONT=monospace][/FONT]

i just tested this on my desktop and the setup really was that easy. granted for the time being i'm usiung fedora 13. the biggest complaint i have so far is the tray icon background isn't transparent so i have a white square on my dark theme. i can live with that

---

### Post by H3LTerSK3LTer on 2010-08-15
[QUOTE=
Step 1: download x360MediaServe v.0.0.2
```
wget http://superb-east.dl.sourceforge.net/sourceforge/x360mediaserve/x360mediaserve-0.0.2.tar.gz
```Step 2: Unpackage the .tar.gz[/QUOTE]

Is there alternate mirrors for this download? If not I'm sorry you got cease and desist notice.  Can't see why tho its not like you actually copied any of their code.

---

### Post by mamamia88 on 2010-08-29
> **H3LTerSK3LTer said:**
> Is there alternate mirrors for this download? If not I'm sorry you got cease and desist notice.  Can't see why tho its not like you actually copied any of their code.

go to sourceforge and serch for it. download it from there and extract to home directory.  create the script that he tells you to.  then make sure that script and the start file in the media server folder are set up with execute privilidges.  run the start script then you will be able to acess web based interface to set what directory your music is in

---

### Post by aeronutt on 2010-08-29
I've had good luck with Playstation 3 media player for wired, but for my setup, it drops out when using wireless. But, so does every other attempt to use wireless streaming to xbox360....except for Windows Media Player.

---

### Post by mamamia88 on 2010-08-29
can i ask a simple question?  what is the point of creating the script?  i'm no programmer but it looks like all the script does is change directory to where script is located.  can't you just setup startup applications to point to the start script that comes with the program?

---

### Post by imgod22222 on 2010-09-05
mamamia,
./start expects to be run in its own directory.
So when you call it from a different directory (say you're in your home directory and start is in a directory called 360MedSer/ you can run start by calling 360MedSer/start and run it, but then start will not be able to call any of the helper files it calls, such as configuration.xml, as well as other files

Thanx OP for this tut. uShare has a maximum limit of listing 1000 entries for some reason, and this actually works. (lists all the artists, anyways, which is "good enough")

---

### Post by tux|Glux on 2010-11-17
Works great. Thanks

---

### Post by smb2004 on 2010-11-22
This is working great for music.  Does anyone know if this can be used for video as well?

---

### Post by aeronutt on 2010-11-22
x360mediaserve kinda works for me. I'm connected to my xbox, but when I play a song, it plays for 2min, then stops playing. If I hit 'next song' button on the xbox, it fires up the next song, and again, stops playing after ~2min

---

### Post by samm71790 on 2013-03-11
[http://gareth.halfacree.co.uk/2009/09/xbox-360-and-minidlna](http://gareth.halfacree.co.uk/2009/09/xbox-360-and-minidlna)

minidlna finally works for me.

avi and mp4 video as well as mp3's

still no FLAC and MKV but my little fileserver couldnt transcode stuff even if it wanted to

edit. my bad... didnt realise how old this thread was.

---

### Post by sandyd on 2013-03-11
**Necromancing - thread closed**
Please do not post in threads more than one year old as many things change between Ubuntu releases.

Thanks!

---

### Post by QIII on 2013-03-11
... and now closed.

---

