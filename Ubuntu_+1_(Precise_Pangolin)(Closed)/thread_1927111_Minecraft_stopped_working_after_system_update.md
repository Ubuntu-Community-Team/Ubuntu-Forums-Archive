---
title: "Minecraft stopped working after system update"
date: 2012-02-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by the_blue_box on 2012-02-17
Hi all

I've had Minecraft 1.1 installed on my 12.04 64bit laptop for some weeks now and
I've only had one problem with it up till now...

The first problem I had was I'd just updated my system and after the reboot Minecraft wouldn't start :( . update manager was saying that it wanted to do a partial upgrade so I went over to synaptic and clicked the "Mark all upgrades" button and then "apply" stuff up graded and after a reboot  Minecraft was working :) (this was about a week ago)

But now last night the same thing happened after a upgrade so I did every thing I did before but to no avail :( and when I run Minecraft from the terminal I get this


```
** WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-4Hu3hyqhAy: Connection refused
java.net.UnknownHostException: mcupdate.tumblr.com
	at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:175)
	at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:384)
	at java.net.Socket.connect(Socket.java:546)
	at java.net.Socket.connect(Socket.java:495)
	at sun.net.NetworkClient.doConnect(NetworkClient.java:178)
	at sun.net.www.http.HttpClient.openServer(HttpClient.java:409)
	at sun.net.www.http.HttpClient.openServer(HttpClient.java:530)
	at sun.net.www.http.HttpClient.<init>(HttpClient.java:240)
	at sun.net.www.http.HttpClient.New(HttpClient.java:321)
	at sun.net.www.http.HttpClient.New(HttpClient.java:338)
	at sun.net.www.protocol.http.HttpURLConnection.getNewHttpClient(HttpURLConnection.java:935)
	at sun.net.www.protocol.http.HttpURLConnection.plainConnect(HttpURLConnection.java:876)
	at sun.net.www.protocol.http.HttpURLConnection.connect(HttpURLConnection.java:801)
	at sun.net.www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1139)
	at java.net.HttpURLConnection.getResponseCode(HttpURLConnection.java:397)
	at javax.swing.JEditorPane.getStream(JEditorPane.java:792)
	at javax.swing.JEditorPane.setPage(JEditorPane.java:433)
	at net.minecraft.LoginForm$8.run(LoginForm.java:198)
java.io.FileNotFoundException: /home/*myusername*/.minecraft/lastlogin (No such file or directory)
	at java.io.FileInputStream.open(Native Method)
	at java.io.FileInputStream.<init>(FileInputStream.java:137)
	at net.minecraft.LoginForm.readUsername(LoginForm.java:131)
	at net.minecraft.LoginForm.<init>(LoginForm.java:76)
	at net.minecraft.LauncherFrame.<init>(LauncherFrame.java:30)
	at net.minecraft.LauncherFrame.main(LauncherFrame.java:158)
	at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:13)
[xcb] Unknown sequence number while processing queue
[xcb] Most likely this is a multi-threaded client and XInitThreads has not been called
[xcb] Aborting, sorry about that.
java: ../../src/xcb_io.c:273: poll_for_event: Assertion `!xcb_xlib_threads_sequence_lost' failed.
/usr/local/bin/minecraft: line 1: 15244 Aborted                 (core dumped) java -jar /home/*myusername*/.minecraft/minecraft.jar
```

Has anyone got any idea how to fix this???
I want my Minecraft back :(

---

### Post by the_blue_box on 2012-02-17
I'm a little bit further on now. I can run it using ```
sudo minecraft
``` (so what ever the problem is it's got something to do with permissions) but I really don't want to have to.

I can't find anything on Google about this ether :(

Any ideas would be great :)

---

### Post by Stinger on 2012-02-21
This:
```
[xcb] Most likely this is a multi-threaded client and XInitThreads has not been called
[xcb] Aborting, sorry about that.
```
Pinpoints the problem I think,"XInitThreads has not been called", you can google it, I did, it's a known problem.

I have a thread about it here
[http://ubuntuforums.org/showthread.php?t=1927531]("http://ubuntuforums.org/showthread.php?t=1927531")

As a temporary workaround this guide can be used, until the developers has a fix for the bug.
There is a howto for both 32 and 64 bit:

[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by Stinger on 2012-02-24
God news  [#935296]("https://bugs.launchpad.net/ubuntu/+source/java-atk-wrapper/+bug/935296") has got the developers attention, it is now marked as a high priority bug and targeted for beta-2

There is another workaround too, posted by Xerxes in [comment #20]("https://bugs.launchpad.net/ubuntu/+source/java-atk-wrapper/+bug/935296/comments/20")

---

### Post by Stinger on 2012-02-24
[Bug #935296]("https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/935296") just got a new headline an hour ago, [Matthias Klose]("https://launchpad.net/~doko") changed it from > minecraft fails to start after latest precise updates... to > java-atk-wrapper prevents java applications from starting.

---

