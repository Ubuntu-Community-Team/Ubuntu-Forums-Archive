---
title: "HOWTO: Run USDownloader on Ubuntu server 8.10"
date: 2008-11-24
forum: Server Platforms
---

### Post by ais77 on 2008-11-24
To run the best in automati&#1089; file share downloading - russian Universal Share Downloader (USD)  ([http://www.dimonius.ru/](http://www.dimonius.ru/))
on GUI-less (or, they say, headless) Linux server (in my case it's Ubuntu server 8.10) we will need 4 steps. 
The most complicated thing will be setting up the "fake" framebuffer version of X - Xvfb. The rest is easy.
Well, let's go:


**1) - SETUP XVFB, WINE and CABEXTRACT -**
== Install Xvfb, wine &#1080; cabextract:
```
$ sudo apt-get install xvfb wine cabextract
```

Due to the minor packaging bug in xvfb: 
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/294454](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/294454)
we need to compensate it by installation of some additional packages: 
```
$ sudo apt-get install xfs xfonts-scalable xfonts-100dpi
```

== Start Xvfb: 
```
$ /usr/bin/X11/Xvfb :10.10 -screen 10 800x600x16 -ac -br -kb -c -fbdir /var/tmp/ &
```

** At this step you may get several errors with default Xorg configarution (due to mentioned bug in xvfb package) - so here are my conf files for reference (in attach).



== Set up the current display:
```
$ export DISPLAY=:10.10
```
Doublecheck it:
```
$ echo $DISPLAY
```

== Dance around to get Xvfb work correct (at least - wine-applications shouldn't crash with critical error).
Minor errors (fonts-related and like) won't shut down USDownloader - leave them unresolved.
To check try start, for example:
```
$ wine notepad.exe &
```
And check if it's running:
```
$ ps -C notepad.exe  
```



**2) - SETUP IES4LINUX -**
Follow instructions from the respectable author (I guess step &#8470;6 is the only we really need for Ubuntu 8.10):
[http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)



**3) - SETUP WINDOWS SCRIPTING HOST (needed for .VBS) -**
== Download the great script for automatic installation of windoze components on wine (big thanks for input of Dan Kegel, [email]dank@kegel.com[/email]):

[http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)

We need to hack this script a bit - removing with  /Q option all unnecessary (in our headless :) case) pop-ups with user action request ("Accept license terms" etc):
*change corresponding line from>*
```
try $WINE "$WINETRICKS_CACHE"/vc6redistsetup_enu.exe "/T:`$WINE winepath -w "$WINETRICKS_TMP"`" /c $WINETRICKS_QUIET
```
*to>*
```
try $WINE "$WINETRICKS_CACHE"/vc6redistsetup_enu.exe "/T:`$WINE winepath -w "$WINETRICKS_TMP"`" /c /Q

```
*change corresponding line from>*
```
$WINE "$WINETRICKS_CACHE"/vcredist.exe || true
```
*to>*
```
$WINE "$WINETRICKS_CACHE"/vcredist.exe /Q || true 
```

*change corresponding line from>*
```
try $WINE "$WINETRICKS_CACHE"/WindowsXP-Windows2000-Script56-KB917344-x86-enu.exe $WINETRICKS_QUIET
```
*to>*
```
try $WINE "$WINETRICKS_CACHE"/WindowsXP-Windows2000-Script56-KB917344-x86-enu.exe /Q
```

== Install Windows Scripting Host (it's necessary to run .vbs scripts in USD):
```
$ ./winetricks -v wsh56
```


**4) - SETUP USDownloader itself -**
== Download the recent portable blackmanos' USD assembly  (we need JavaScript enabled browser here - assembly is placed on several file-sharing hostings)
[http://forum.ru-board.com/topic.cgi?forum=5&topic=27428&start=20#19](http://forum.ru-board.com/topic.cgi?forum=5&topic=27428&start=20#19)
Unpack assembly in windoze, copy it's content to some Linux directory under wine (for me it's ~/.wine/drive_c/usd)

== Create  "windoze disk" u:\ as the soft link to the directory where we want USD to put downloaded files then (for my case - it's /mm/usd):
```
$ cd ~/.wine/dosdevices
$  ln -s -T /mm/usd u:
```

== Correct corresponding paths in USDownloader.ini (and at this step let's change USD default language to English - to read logs more easily on Linux):
```
[Main]
SelectLang=1
Language=USDownloader.eng.lng
SaveTo=u:\
SaveToItems=u:\
...
DefaultSaveToFolder=u:\
```

== Also in USDownloader.ini set up the USD web-server start: 
```
[WebServer]
Enabled=1
Address=0.0.0.0
Port=8088
Login=YOURLOGIN
Password=YOURPASSWORD
Form.AddLink.Width=400
Form.AddLink.URL.Height=200
Form.AddLink.Descr.Height=100
```

YOURLOGIN and YOURPASSWORD, off course, should be yours. Don't forget to open the mentioned port (8088 here) in your firewall for outbound connections - it will be the only way to manage USD.

== Start USDownloader:
```
$ wine C:\\usd\\USDownloader.exe &
```

Check if this process is running:
```
$ ps -C USDownloader.exe
```

== Use your favorite browser to log in to USD:
```
http://your.server.ip.address:8088
```

Check how the staff works - add some download, simultaneously watching USD log:
```
$ tail -f ~/.wine/drive_c/usd/USDownloader.log
```

Downloads from depositfiles work fine - therefore it seems that vbs-automation scripts work as they should.
That's it.

---

### Post by globalenigma on 2008-12-02
I just wanted to say thank you and this works great for me running on Intrepid as well.  The directions are right on and if you know how to follow directions you can start downloading using USD.

-enigma

---

### Post by ais77 on 2008-12-03
> **globalenigma said:**
> The directions are right on and if you know how to follow directions you can start downloading using USD.


I wrote it in the hope of helping. Glad to hear that it works :)

---

### Post by deGz0rx on 2008-12-10
yeah it would be nice to have USDownloader in ubuntu but i got a problem which you've already predicted
after doing the command which you said generates errors i got this:
```
digrejzo@deGzyrx:~$ /usr/bin/X11/Xvfb :10.10 -screen 10 800x600x16 -ac -br -kb -c -fbdir /var/tmp/ &
[1] 6468
digrejzo@deGzyrx:~$ Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
(EE) config/hal: NewInputDeviceRequest failed
(EE) config/hal: NewInputDeviceRequest failed
(EE) config/hal: NewInputDeviceRequest failed
(EE) config/hal: NewInputDeviceRequest failed

```
i know thats supposed to happen (because you said so lol :D)
but what do i do with that .txt file you added as an attachment?

---

### Post by ais77 on 2008-12-10
> **deGz0rx said:**
> 
but what do i do with that .txt file you added as an attachment?
Xvfb's behavior corresponds to the bug I mentioned - it seems that Xvfb wasn't tested in pure (X-less) server environment.
In this environment there aren't necessary X configuration files wich are needed to run Xvfb as a (lets say) "X-server".
Two of them I placed in attach - just create them in corresponding paths (look inside txt) - and try to run Xvfb again.
And post results here ;)

---

### Post by deGz0rx on 2008-12-10
you mentioned that i should create new files in corresponding paths, im not sure which files are those because i couldnt really find anything related to making new files in the attached .txt :D
or i havent looked hard enough? :O

the only thing i found worth typing into terminal is that "sudo dkpg-reconfigure -phigh xserver-xorg" thing but it says thats used for updating xorg so i dont think this is what im looking for

---

### Post by ais77 on 2008-12-11
> **deGz0rx said:**
> because i couldnt really find anything related to making new files in the attached .txt :D
or i havent looked hard enough? :O
Yes you haven't - those strings in txt
```
$ cat /etc/X11/xorg.conf
$ cat /etc/X11/xserver/SecurityPolicy
```
are commands for listing two corresponding X configuration files (including paths):
/etc/X11/xorg.conf
/etc/X11/xserver/SecurityPolicy
Try to create these files in their paths manually - and see what happens with Xvfb.

---

### Post by deGz0rx on 2008-12-11
ok yesterday, i didnt type anything but the "sudo dkpg-reconfigure -phigh xserver-xorg" command and today i start my ubuntu to find out that xorg got fcked up :confused:
everything returned back to the beginning as if i dont have any drivers, my compiz is off, effects are off and i cant start nvidia-settings
i tried installing 188.06 driver again, it installed fine, but when i do sudo nvidia-settings i get this:
```
The program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadName (named color or font does not exist)'.
  (Details: serial 311 error_code 15 request_code 45 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```
i know i broke something with that command i typed in yesterday, now i need some tips on bringing my ubuntu back to life :D
any way of "repairing" xorg?

edit: just found out exaile aint working as well, and im getting that same message
i seriously hope i can repair this :/

---

### Post by ais77 on 2008-12-11
> **deGz0rx said:**
> my compiz is off, effects are off and i cant start nvidia-settings

Ooops, fellow.. 
It seems, that you are running Ubuntu desktop, eh? :confused:
Why did you tried this SERVER (this means x-less) HOWTO?
USD works fine on usual Ubuntu GNOME systems under WINE.

Repairing Xorg is out of this topic - definitely. 

PS: try something like apt-get purge xorg, then install it back...

---

### Post by deGz0rx on 2008-12-11
omg, i just realized what im doing lol
didnt really pay attention to the topic name until you mentioned it. words USDownloader, Ubuntu and 8.10 were enough to make me try the commands without actually reading what im doing .. :S
anyways, i managed to repair xorg, and sorry for few offtopic messages (the topic was dead anyways :D)

thanks again, cheers

---

### Post by inferno0270 on 2008-12-21
help!

when i run this

> ./winetricks -v wsh56

i get 

> bash: ./winetricks: Permission denied


EDIT:

Got it working!

I just set it to allow executing as program.

---

