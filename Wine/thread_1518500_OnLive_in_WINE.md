---
title: "OnLive in WINE?"
date: 2010-06-26
forum: Wine
---

### Post by quadomatic on 2010-06-26
I got my invitation to the founding members program for OnLive. It's a free year of OnLive service (still have to pay for games though). If I could get this working in Ubuntu on my laptop...

Installation worked fine. When running signing in, I get an "Unable to contact the OnLive Gaming Service. Please check play.onlive.com for details" error. The error code says a512 in the bottom left corner.

In the command line output, it says:

> fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub

I added [Bug 14233]("http://bugs.winehq.org/show_bug.cgi?id=14233") to the [OnLive AppDB page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20517").

Any ideas?

---

### Post by cogadh on 2010-06-26
OnLive requires Internet Explorer or Firefox. Since IE doesn't actually work in Wine, have you tried installing Firefox?

---

### Post by quadomatic on 2010-06-26
> **cogadh said:**
> OnLive requires Internet Explorer or Firefox. Since IE doesn't actually work in Wine, have you tried installing Firefox?

How does it require IE or Firefox? Logging in works through the launcher. In Windows 7, I closed my browsers and monitored the task manager and I didn't see IE or Firefox open either.

---

### Post by cogadh on 2010-06-26
Odd, I couldn't even install the client on my Windows machine because I was using Chrome. It gave me some error message about only being compatible with IE and Firefox.

---

### Post by quadomatic on 2010-06-27
> **cogadh said:**
> Odd, I couldn't even install the client on my Windows machine because I was using Chrome. It gave me some error message about only being compatible with IE and Firefox.

Hmm...well if you want to launch OnLive from the browser, it has to be from Firefox or IE, but otherwise it doesn't matter. I'll give it a try though.

I had grabbed my install file from my installation in Windows, so it didn't matter for me. In linux, it will check the browser's useragent before allowing you to download the installer. After installation, in your browser, the download button becomes a launch button. In Firefox in Linux, the browser plugin isn't supported so this change doesn't occur. It works in WINE's Firefox though.

UPDATE: Tried it from Firefox in WINE. Launches the application fine, but same error when trying to connect.

UPDATE2: I found this thread: [http://onlivefans.com/showthread.php?4025-LINUX-Getting-Onlive-to-run-in-Linux-Operating-systems-%28status%29&highlight=linux](http://onlivefans.com/showthread.php?4025-LINUX-Getting-Onlive-to-run-in-Linux-Operating-systems-%28status%29&highlight=linux)

I think on WINE, the program may be trying to connect to ds.onlive.net on the wrong port. Is there a way to modify the ports WINE chooses to connect to?

UPDATE3: I used tcpspy to see where OnLive tries to connect. Here's the output I get from when OnLive starts till I close the program after I get the error

```
Jun 26 23:45:17: connect: proc /usr/bin/wine-preloader, user aneesh, local 192.168.1.66:51395, remote 74.85.146.222:https
Jun 26 23:45:18: disconnect: proc /usr/lib/erlang/erts-5.7.4/bin, user aneesh, local 127.0.0.1:48453, remote 127.0.0.1:45799
Jun 26 23:45:18: disconnect: proc /usr/bin/wine-preloader, user aneesh, local 192.168.1.66:51395, remote 74.85.146.222:https
Jun 26 23:45:18: connect: proc /usr/bin/wine-preloader, user aneesh, local 192.168.1.66:41982, remote 74.85.146.215:https
Jun 26 23:45:18: connect: proc /usr/bin/wine-preloader, user aneesh, local 192.168.1.66:38926, remote 74.85.148.213:https
Jun 26 23:45:18: connect: proc /usr/bin/wine-preloader, user aneesh, local 192.168.1.66:57473, remote 74.85.146.211:https
Jun 26 23:45:19: disconnect: proc /usr/bin/wine-preloader, user aneesh, local 192.168.1.66:41982, remote 74.85.146.215:https
Jun 26 23:45:19: disconnect: proc /usr/bin/wine-preloader, user aneesh, local 192.168.1.66:38926, remote 74.85.148.213:https
Jun 26 23:45:19: disconnect: proc /usr/bin/wine-preloader, user aneesh, local 192.168.1.66:57473, remote 74.85.146.211:https
Jun 26 23:45:19: connect: proc /usr/lib/erlang/erts-5.7.4/bin, user aneesh, local 127.0.0.1:48453, remote 127.0.0.1:45799
```

It looks like the 74.85.146.222:https (port 443, right?) is the authentication server.

The other 3 connections are probably to OnLive content servers (74.85.146.215, 74.85.148.213, 74.85.146.211), but I guess something goes wrong perhaps. I want to run OnLive in windows and get a log of the connections OnLive makes, but I can't find a program that continues to record connections - only ones that show current connections.

Any ideas?

---

### Post by asdfoo on 2010-06-27
> **quadomatic said:**
> Hmm...well if you want to launch OnLive from the browser, it has to be from Firefox or IE, but otherwise it doesn't matter. I'll give it a try though.

UPDATE: Tried it from Firefox in Wine. Launches the application fine, but same error when trying to connect.

UPDATE2: I found this thread: [http://onlivefans.com/showthread.php?4025-LINUX-Getting-Onlive-to-run-in-Linux-Operating-systems-%28status%29&highlight=linux](http://onlivefans.com/showthread.php?4025-LINUX-Getting-Onlive-to-run-in-Linux-Operating-systems-%28status%29&highlight=linux)

I think on Wine, the program may be trying to connect to ds.onlive.net on the wrong port. Is there a way to modify the ports Wine chooses to connect to?

UPDATE3: I used tcpspy to see where OnLive tries to connect. Here's the output I get from when OnLive starts till I close the program after I get the error

```
Jun 26 23:45:17: connect: proc /usr/bin/wine-preloader, user aneesh, local 192.168.1.66:51395, remote 74.85.146.222:https
Jun 26 23:45:18: disconnect: proc /usr/lib/erlang/erts-5.7.4/bin, user aneesh, local 127.0.0.1:48453, remote 127.0.0.1:45799
Jun 26 23:45:18: disconnect: proc /usr/bin/wine-preloader, user aneesh, local 192.168.1.66:51395, remote 74.85.146.222:https
Jun 26 23:45:18: connect: proc /usr/bin/wine-preloader, user aneesh, local 192.168.1.66:41982, remote 74.85.146.215:https
Jun 26 23:45:18: connect: proc /usr/bin/wine-preloader, user aneesh, local 192.168.1.66:38926, remote 74.85.148.213:https
Jun 26 23:45:18: connect: proc /usr/bin/wine-preloader, user aneesh, local 192.168.1.66:57473, remote 74.85.146.211:https
Jun 26 23:45:19: disconnect: proc /usr/bin/wine-preloader, user aneesh, local 192.168.1.66:41982, remote 74.85.146.215:https
Jun 26 23:45:19: disconnect: proc /usr/bin/wine-preloader, user aneesh, local 192.168.1.66:38926, remote 74.85.148.213:https
Jun 26 23:45:19: disconnect: proc /usr/bin/wine-preloader, user aneesh, local 192.168.1.66:57473, remote 74.85.146.211:https
Jun 26 23:45:19: connect: proc /usr/lib/erlang/erts-5.7.4/bin, user aneesh, local 127.0.0.1:48453, remote 127.0.0.1:45799
```

It looks like the 74.85.146.222:https (port 443, right?) is the authentication server.

The other 3 connections are probably to OnLive content servers (74.85.146.215, 74.85.148.213, 74.85.146.211), but I guess something goes wrong perhaps. I want to run OnLive in windows and get a log of the connections OnLive makes, but I can't find a program that continues to record connections - only ones that show current connections.

Any ideas?

on windows use wireshark.

---

### Post by quadomatic on 2010-06-27
I used WireShark in Windows and captured all the connections made during OnLive's launch process, and after keeping OnLive open for a few seconds.

But, is there a way to make wireshark save just the information about the connections and not the packets? I want to upload the capture to Bugzilla, but I don't want to put myself at risk in any way.

---

### Post by asdfoo on 2010-06-27
hmm, I would just post a note on bugzilla saying that you have made a wireshark capture on windows for comparison which can be provided privately if anyone is interested.

I'm guessing that it's not going to be all that useful.  What you could try is generating a +relay,+seh,+tid log and look through it  (it will probably be several hundred MB of text), try to find the text of the error dialog and look backwards to see if there is anything obvious

---

### Post by DeviantGuy on 2011-02-01
> **quadomatic said:**
> How does it require IE or Firefox? Logging in works through the launcher. In Windows 7, I closed my browsers and monitored the task manager and I didn't see IE or Firefox open either.

When you have the plugin installed. The login screen (Not the plugin) is separate from the plugin. What the login screen does is it redirects you to Play.onlive.com without opening a browser. Internet explorer is the Plugins primary browser. This means that OnLive has to run natively over Windows. Or in a virtualbox. One of my friends over at OnLiveFans.com managed to get as far as the login screen. I even heard that someone managed it to run over Ubuntu without any sound. I even contacted Onlive about this...
Greetings, Deviantguy. 

Thank you for contacting OnLive. The OnLive Game Service currently supports PC and Mac platforms. See [http://support.onlive.com/app/answers/detail/a_id/178](http://support.onlive.com/app/answers/detail/a_id/178) for more information.

While we do not currently have a client for Linux, we do appreciate your interest in OnLive. Feedback such as this will help us improve our service. Please check out our blog ([http://blog.onlive.com](http://blog.onlive.com)) and website ([http://www.onlive.com](http://www.onlive.com)) for updates. Once again, thank you for contacting us.

Eric Customer Service Representative
[http://support.onlive.com/](http://support.onlive.com/)

---

### Post by altima on 2011-09-18
I installed firefox into wine, downloaded the onlive installer with it, ran the installer. it took a considerably long time for it to start, but the installer appeared, installation was successful and the first start was fast and without bugs. the only drawback is that the sound runs echoed. I suppose, it is a bug of pulseaudio, and yet I don't know how to solve this issue. also I haven't tried playing, yet.
my system is ubuntu 10.04.3,
the version of wine is 1.3.26
wine has several dlls assigned to be able to run ms-office 2003. they are: msxml3 (native, genuine), riched20 and riched32 (both set as native).

---

