---
title: "Cannot start Ubuntu One"
date: 2010-05-10
forum: Ubuntu One (CLOSED)
---

### Post by peeteepee on 2010-05-10
Having problems starting Ubuntu One. 

When I try clicking on *Ubuntu One ...* from the Indicator Applet at the top of the screen, nothing happens. The cursor doesn't even change to an hourglass.

If I try running Ubuntu One from *System/Preferences* the cursor changes, but nothing happens.

I've tried running the command *[u1sysnc --authorise]* as suggested elsewhere on this forum and I get the following:
[FONT="Courier New"][I]peter@Ubuntop:~$ u1sync --authorize
** Message: secret service operation failed: The name org.freedesktop.secrets was not provided by any .service files
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/main.py", line 462, in main
    do_main(argv=argv)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/main.py", line 454, in do_main
    reactor.run(installSignalHandlers=False)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 249, in run
    self.__run()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 293, in simulate
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/base.py", line 751, in runUntilCurrent
    f(*a, **kw)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/client.py", line 73, in wrapper
    ent = func(*arg, **kwargs)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/client.py", line 295, in _obtain_token
    oauth_client.clear_token()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 181, in clear_token
    items = self._get_keyring_items()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 153, in _get_keyring_items
    self.consumer.key})
gnomekeyring.IOError: 

[/I][/FONT]
I'm running UNR 10.4 on a Samsung NC10. It's dual boot with Windows XP and a shared data partition. If I run UNR from a USB thumbdrive, the Ubuntu One works fine, but running from the hard drive it doesn't work.

Any ideas anyone?

---

### Post by joshuahoover on 2010-05-11
> **peeteepee said:**
> Having problems starting Ubuntu One. 

When I try clicking on *Ubuntu One ...* from the Indicator Applet at the top of the screen, nothing happens. The cursor doesn't even change to an hourglass.

If I try running Ubuntu One from *System/Preferences* the cursor changes, but nothing happens.

I've tried running the command *[u1sysnc --authorise]* as suggested elsewhere on this forum and I get the following:
[FONT=Courier New][I]peter@Ubuntop:~$ u1sync --authorize
** Message: secret service operation failed: The name org.freedesktop.secrets was not provided by any .service files
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/main.py", line 462, in main
    do_main(argv=argv)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/main.py", line 454, in do_main
    reactor.run(installSignalHandlers=False)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 249, in run
    self.__run()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 293, in simulate
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/base.py", line 751, in runUntilCurrent
    f(*a, **kw)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/client.py", line 73, in wrapper
    ent = func(*arg, **kwargs)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/client.py", line 295, in _obtain_token
    oauth_client.clear_token()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 181, in clear_token
    items = self._get_keyring_items()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 153, in _get_keyring_items
    self.consumer.key})
gnomekeyring.IOError: 

[/I][/FONT]
I'm running UNR 10.4 on a Samsung NC10. It's dual boot with Windows XP and a shared data partition. If I run UNR from a USB thumbdrive, the Ubuntu One works fine, but running from the hard drive it doesn't work.

Any ideas anyone?

A couple of things:


[LIST=1]
[*]You mentioned you're running 10.04 but also mention the Ubuntu One applet in the task bar. We removed the Ubuntu One applet from 10.04 and our beta PPA. So I'm not sure how you're seeing the applet.
[*]The error seems to indicate the GNOME keyring service isn't functioning properly. Can you make sure that you have all the latest updates. If you still have problems, can you please file a bug report using the following steps so that we get some debug logs? Also, please let us know in the bug report if you are set to auto-login to your computer.
[/LIST]

[LIST]
[*]Open [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)  - Be sure to include the steps you're taking and the results you're seeing
[*]At a terminal session (Applications->Accessories->Terminal) run the following command (replacing ###### with the bug number from the previous step): apport-collect -p ubuntuone-client ######
[/LIST]
Thank you,

Joshua

---

### Post by peeteepee on 2010-05-12
Sorry, I've been clumsy in using the wrong phrase. Let me describe my actions: Go to top right hand corner of the screen, left click on my login name, click on *Ubuntu One...* . Nothing happens.

Regarding the latest updates, yes, I'm up to date (as of 12 May 17:20 GMT). I have my netbook set to check for updates daily and notify me if any are waiting.

I'll report the bug as you ask but I can confirm now that I have auto-login set.

Many thanks.

---

### Post by joshuahoover on 2010-05-12
> **peeteepee said:**
> Sorry, I've been clumsy in using the wrong phrase. Let me describe my actions: Go to top right hand corner of the screen, left click on my login name, click on *Ubuntu One...* . Nothing happens.

Regarding the latest updates, yes, I'm up to date (as of 12 May 17:20 GMT). I have my netbook set to check for updates daily and notify me if any are waiting.

I'll report the bug as you ask but I can confirm now that I have auto-login set.

Many thanks.

Thank you for the reply! Can you try some things for me and let me know how it goes?

[LIST=1]
[*]Open Applications->Accessories->Terminal and run: ubuntuone-preferences
[*]Report the output of that command here
[*]In the terminal session try: u1sdtool -q; killall ubuntuone-login; u1sdtool -c
[/LIST]
Thanks,

Joshua

---

### Post by mozza314 on 2010-05-13
I'm having exactly the same problem. I don't have my machine logging in automatically. I'm running inside virtualbox and I upgraded from 9.10 rather than a fresh install.

Actually my output from u1sync --authorize is a bit different, but it says basically the same thing:
andrew@andrew-desktop:~$ u1sync --authorize
** Message: secret service operation failed: The name org.freedesktop.secrets was not provided by any .service files
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 249, in run
    self.__run()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 120, in wrapper
    return real_cb(real_s, condition)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 283, in callback
    self.simulate() # fire Twisted timers
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 293, in simulate
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/base.py", line 751, in runUntilCurrent
    f(*a, **kw)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/client.py", line 73, in wrapper
    ent = func(*arg, **kwargs)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/client.py", line 295, in _obtain_token
    oauth_client.clear_token()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 181, in clear_token
    items = self._get_keyring_items()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 153, in _get_keyring_items
    self.consumer.key})
gnomekeyring.IOError: 



Here's my output from the commands you asked the thread starter to execute:

andrew@andrew-desktop:~$ ubuntuone-preferences
** Message: secret service operation failed: The name org.freedesktop.secrets was not provided by any .service files
Traceback (most recent call last):
  File "/usr/bin/ubuntuone-preferences", line 62, in <module>
    from desktopcouch.replication_services import ubuntuone as dcouch
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 20, in <module>
    from desktopcouch.start_local_couchdb import process_is_couchdb, read_pidfile
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 38, in <module>
    from desktopcouch import local_files
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 297, in <module>
    xdg_base_dirs.save_config_path("desktop-couch"))
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 237, in __init__
    self.configuration = _Configuration(self)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 91, in __init__
    {'desktopcouch': 'basic'})
gnomekeyring.IOError
andrew@andrew-desktop:~$ 
andrew@andrew-desktop:~$ 
andrew@andrew-desktop:~$ u1sdtool -q; killall ubuntuone-login; u1sdtool -c
ubuntuone-syncdaemon stopped.
ubuntuone-login: no process found



I also have the latest updates. Please help.

---

### Post by peeteepee on 2010-05-13
Hi Joshua,

Here's the output as requested:
[B]peter@Ubuntop:~$ ubuntuone-preferences
** Message: secret service operation failed: The name org.freedesktop.secrets was not provided by any .service files
Traceback (most recent call last):
  File "/usr/bin/ubuntuone-preferences", line 1146, in <module>
    prefs_dialog = UbuntuOneDialog()
  File "/usr/bin/ubuntuone-preferences", line 538, in __init__
    self.__construct()
  File "/usr/bin/ubuntuone-preferences", line 978, in __construct
    self.devices.list_devices()
  File "/usr/bin/ubuntuone-preferences", line 380, in list_devices
    token = get_access_token(self.keyring)
  File "/usr/bin/ubuntuone-preferences", line 124, in get_access_token
    'oauth-consumer-key': 'ubuntuone'})
gnomekeyring.IOError
peter@Ubuntop:[/B]

The second command you suggested produced the following:
[B]peter@Ubuntop:~$ u1sdtool -q; killall ubuntuone-login; u1sdtool -c
ubuntuone-syncdaemon stopped.
ubuntuone-login: no process found
peter@Ubuntop:~$ 
[/B]

But still no Ubuntu One

Peter

---

### Post by peeteepee on 2010-05-13
Breaking news:
I noticed that I now have an *Ubuntu One* folder in my Home folder (never had one before). Rebooted my netbook, but Ubuntu One functions still not working. Copied a file to the *Ubuntu One* folder, nothing happens and the folder and file have a shriek mark (!) attached to them.

---

### Post by joshuahoover on 2010-05-13
> **peeteepee said:**
> Breaking news:
I noticed that I now have an *Ubuntu One* folder in my Home folder (never had one before). Rebooted my netbook, but Ubuntu One functions still not working. Copied a file to the *Ubuntu One* folder, nothing happens and the folder and file have a shriek mark (!) attached to them.

Hi Peter,

Can you file a bug for this problem so we can track it better and I can get some devs to look into it further? It's definitely something going on with the keyring. I'm just not sure if it's something that changed in the keyring code, a config issue on some computers, or something else.

You can file a bug by doing the following:

[LIST=1]
[*][https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)  - Be sure to include the steps you're taking and the results you're seeing
[*]At a terminal session (Applications->Accessories->Terminal) run the following command (replacing ###### with the bug number from step 1): apport-collect -p ubuntuone-client ######
[/LIST]
Thank you,

Joshua

---

### Post by joshuahoover on 2010-05-13
> **peeteepee said:**
> Hi Joshua,

Here's the output as requested:
[B]peter@Ubuntop:~$ ubuntuone-preferences
** Message: secret service operation failed: The name org.freedesktop.secrets was not provided by any .service files
Traceback (most recent call last):
  File "/usr/bin/ubuntuone-preferences", line 1146, in <module>
    prefs_dialog = UbuntuOneDialog()
  File "/usr/bin/ubuntuone-preferences", line 538, in __init__
    self.__construct()
  File "/usr/bin/ubuntuone-preferences", line 978, in __construct
    self.devices.list_devices()
  File "/usr/bin/ubuntuone-preferences", line 380, in list_devices
    token = get_access_token(self.keyring)
  File "/usr/bin/ubuntuone-preferences", line 124, in get_access_token
    'oauth-consumer-key': 'ubuntuone'})
gnomekeyring.IOError
peter@Ubuntop:[/B]

The second command you suggested produced the following:
[B]peter@Ubuntop:~$ u1sdtool -q; killall ubuntuone-login; u1sdtool -c
ubuntuone-syncdaemon stopped.
ubuntuone-login: no process found
peter@Ubuntop:~$ 
[/B]

But still no Ubuntu One

Peter

Something else to try from a terminal session:

gnome-keyring-daemon
u1sdtool -q; killall ubuntuone-login; u1sdtool -c

I think it may be that gnome-keyring-daemon is not running. If that fixes the problem for you, can you do the following?

1. Open System->Preferences->Startup Application Preferences
2. Make sure "Secret Storage Service - GNOME Keyring: Secret Service" is selected to startup and then click the "Close" button
 2a. If it's not showing up (or anything with GNOME Keyring in that list), then you may need to add it by doing the following:
  * Click the "Add" button
  * Set the fields to:
     Name: "GNOME Keyring Service"
     Command: gnome-keyring-daemon
  * Click the "Add" button and then the "Close" button to close the startup applications preferences window

Thanks,

Joshua

---

### Post by mozza314 on 2010-05-13
That worked! :-D

However Secret Storage Service - GNOME Keyring: Secret Service

was already there and checked when I looked in my startup application preferences. When I reboot ubuntu one misbehaves again. Adding gnome-keyring-daemon to my .profile doesn't fix this either.

---

### Post by joshuahoover on 2010-05-14
> **mozza314 said:**
> That worked! :-D

However Secret Storage Service - GNOME Keyring: Secret Service

was already there and checked when I looked in my startup application preferences. When I reboot ubuntu one misbehaves again. Adding gnome-keyring-daemon to my .profile doesn't fix this either.

Progress! (Though, far from ideal.) I did a little more reasearch on this bug and think I found one that matches: [https://launchpad.net/bugs/573387](https://launchpad.net/bugs/573387) 

Unfortunately, this sounds like it may be a bug in GNOME Keyring. I'll see if there is anything the Ubuntu One team can do to help with fixing this.

Thank you,

Joshua

---

### Post by peeteepee on 2010-05-14
Hello Joshua,

That's seems to have done the trick!

"Secret Storage Service - GNOME Keyring: Secret Service" wasn't selected, so, as suggested, I ticked it and rebooted. Ubuntu One could now be started and allowed me to re-register my machine. It started to synchronise, albeit a bit slowly, but eventually it got everything together and seems to be working fine.

Thanks very much for all your help, much appreciated.

Peter

---

### Post by joshuahoover on 2010-05-14
> **peeteepee said:**
> Hello Joshua,

That's seems to have done the trick!

"Secret Storage Service - GNOME Keyring: Secret Service" wasn't selected, so, as suggested, I ticked it and rebooted. Ubuntu One could now be started and allowed me to re-register my machine. It started to synchronise, albeit a bit slowly, but eventually it got everything together and seems to be working fine.

Thanks very much for all your help, much appreciated.

Peter

Hi Peter,

Great to hear things are working for you now! Thanks for following up with the message here so I know that it's fixed and if anyone else runs into this hopefully they'll see this thread and see the solution. :)

Joshua

---

### Post by peternickson on 2010-06-06
I'm getting exactly the same error messages.  Ubuntu one still not working.

---

### Post by Byrnz on 2010-06-08
First, this is my first post on the forums, as I am a new convert to GNU/Linux/Ubuntu, fleeing Winderz world. I've managed to convert my mom and brother so far, and they are both extremely surprised at how well it's working out for them. So, a big thanks to the Ubuntu folks.

I am having a similar issue to the original poster, however mine is a little more narrow, so hopefully the answer will come easy to the experts here.

Ubuntu One works correctly if I am logged in and using the "Main account" on my PC. This is the account from which I created my Ubuntu One account. I am able to browse the music store via Rhythm Box and get to the stage of entering my credit card info if purchasing a song, so no problems there.

The issue only arose when I added a new user account for my wife to use. I'm currently trying to get her used to using Linux, and, as she is a big fan of buying music on iTunes, get her set up with the Ubuntu One Music Store. While logged into _her_ account, I am not able to access the Ubuntu One setup/preferences, similar to the original poster. The symptoms of a mouse cursor changing but nothing happening are the same.

I am able to browse the music store via Rhythm Box. I can select a song. I can listen to a song. I can add the song to my cart. When I click "checkout", everything hangs on "connecting to Ubuntu One Music Store." screen.

Does Ubuntu One only allow one account per PC (not per user)? If so, is that what's preventing my wife's user account from accessing the service properly?

Thanks for any help offered. This community has already been a great help getting me started with Linux/Ubuntu.

EDIT: Sorry, I just noticed, this is for netbook remix. I'm using regular 32-bit on my desktop.

---

