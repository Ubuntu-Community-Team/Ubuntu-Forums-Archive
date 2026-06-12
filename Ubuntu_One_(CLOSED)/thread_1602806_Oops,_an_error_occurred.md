---
title: "Oops, an error occurred"
date: 2010-10-21
forum: Ubuntu One (CLOSED)
---

### Post by mcnica on 2010-10-21
I am having trouble using ubuntu one.
1.  In nautilus when I right click on a file or folder I don't have an option to share on ubuntu one.
2. I've tried putting files in Ubuntu One folder with no luck in syncing.

I am not sure what to do.

This is the result from
```
u1sdtool -q; killall ubuntuone-login; u1sdtool -c
ubuntuone-syncdaemon stopped.
ubuntuone-login: no process found

Oops, an error ocurred:
Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
alex@alex-desktop:~$ 

```

---

### Post by RedSingularity on 2010-10-21
Is the ubuntu one core utilities installed?

---

### Post by mcnica on 2010-10-21
What is the ubuntu one core utilities?
I am running a fresh install of Ubuntu 10.10.  Whatever Ubuntu one utilities are installed by default is what I have.

---

### Post by RedSingularity on 2010-10-21
Silly question but are you connected to the Internet?

---

### Post by mcnica on 2010-10-23
Yes, I am connected to the Internet.

I ran the following command
u1sdtool --start

Now, in nautilus I seen the option to share files and folders.  However there is a ribbon on the top of nautilus that says "Operations on this folder are disabled because there is no network connection"

---

### Post by RedSingularity on 2010-10-23
Have you added that computer to the Ubuntu one servers?

---

### Post by mcnica on 2010-10-23
Yes.  The computer has been added.

---

### Post by RedSingularity on 2010-10-24
We can try removing configuration files and making new ones.......

Run the following commands 

rm -rf ~/.local/share/ubuntuone
rm -rf ~/.cache/ubuntuone
rm -rf ~/.config/ubuntuone

Then **REBOOT**

---

### Post by mcnica on 2010-10-25
I tried the commands.  I rebooted and it seems that Ubuntu One is/has not started on its own.  If I open nautilus, there is not option to share any folders/files.

---

### Post by torpidnotion on 2010-10-25
I'm experiencing the same issue.


slash@helios:~$ u1sdtool -c

Oops, an error ocurred:
Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntuone-client/ubuntuone-syncdaemon exited with status 1

Tried purging/reinstalling packages, deleted local cache as advised above, still nothing.

---

### Post by RedSingularity on 2010-10-25
> **mcnica said:**
> I tried the commands.  I rebooted and it seems that Ubuntu One is/has not started on its own.  If I open nautilus, there is not option to share any folders/files.

Yeah you need to have the deamon running.  Run the following command and see if the deamon starts up.

ubuntuone-client

---

### Post by RedSingularity on 2010-10-25
> **torpidnotion said:**
> I'm experiencing the same issue.


slash@helios:~$ u1sdtool -c

Oops, an error ocurred:
Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntuone-client/ubuntuone-syncdaemon exited with status 1

Tried purging/reinstalling packages, deleted local cache as advised above, still nothing.


Interesting, we may have a legit bug here.

---

### Post by mcnica on 2010-10-25
When I type ubuntuone-client in a terminal I get the following
~$ ubuntuone-client
ubuntuone-client: command not found

---

### Post by torpidnotion on 2010-10-25
> **RedSingularity said:**
> Interesting, we may have a legit bug here.
I have no ubuntuone-client binary anywhere, nor do any packages have it.  However, I did do this:

slash@helios:~$ ubuntuone-launch
I recieved a gnome dialog window that said this:  
Your Ubuntu One storage is full. Follow the link below to upgrade your subscription.

I only have used 47kb, so this is definitely not the case.

slash@helios:~$ u1sdtool -c
slash@helios:~$ u1sdtool -s
State: AUTH_FAILED
    connection: With User With Network
    description: auth failed
    is_connected: False
    is_error: True
    is_online: False
    queues: WORKING_ON_BOTH

slash@helios:~$ u1sdtool --current-transfers
Current uploads: 0
Current downloads: 0
slash@helios:~$ u1sdtool --refresh-shares
slash@helios:~$ u1sdtool --list-shares
No shares
slash@helios:~$ u1sdtool --list-folders
No folders

Also, if I launch ubuntuone-preferences, it shows Name, E-Mail and Current Plan as "Unknown"

I am connected to the network and internet, so I'm sure it's nothing network-related.

---

### Post by RedSingularity on 2010-10-25
Go to system>prefs>Ubuntu one

Go to devices tab.  Click connect.  Then see if you are connected and able to sync files.

---

### Post by torpidnotion on 2010-10-25
> **RedSingularity said:**
> Go to system>prefs>Ubuntu one

Go to devices tab.  Click connect.  Then see if you are connected and able to sync files.

The Connect button is grayed out.

I hit restart, and hit connect again.
I then recieve the error about being out of space.

---

### Post by RedSingularity on 2010-10-25
Well i just tried reinstalling the whole piece of software.  It seems there is a bug after all.  I am going to file a report.  I would be great if you guys could pop in and "confirm" you are having the same problem.  I will hand the bug off to one of the ubuntuone guys in the bug squad.

---

### Post by torpidnotion on 2010-10-25
> **RedSingularity said:**
> Well i just tried reinstalling the whole piece of software.  It seems there is a bug after all.  I am going to file a report.  I would be great if you guys could pop in and "confirm" you are having the same problem.  I will hand the bug off to one of the ubuntuone guys in the bug squad.

Absolutely - Post the bug link here and I'll help as needed.

---

### Post by RedSingularity on 2010-10-25
Bug [666608](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/666608)

---

### Post by RedSingularity on 2010-10-25
Please note that I am using 10.04

If you want you can follow the steps i posted to reproduce the problem and see if it has the same outcome on your computer.

---

### Post by torpidnotion on 2010-10-26
I managed to get things working again by deleting the Ubuntu One key from my passwords keyring, removing the local cache and config and rebooting.  Things are now working as they should.
Thanks for your help.

---

### Post by RedSingularity on 2010-10-26
Thats good news!  Did you reinstall ubuntuone before deleting the key to get it working by any chance?

---

### Post by torpidnotion on 2010-10-26
> **RedSingularity said:**
> Thats good news!  Did you reinstall ubuntuone before deleting the key to get it working by any chance?

I did not.

---

### Post by mcnica on 2010-10-26
I tried what torpidnotion did and it is working again.  However, now, everything in Documents and Music is automatically syncing and I cannot stop it from syncing.

---

### Post by torpidnotion on 2010-10-26
> **mcnica said:**
> I tried what torpidnotion did and it is working again.  However, now, everything in Documents and Music is automatically syncing and I cannot stop it from syncing.

Try this, replacing your folder id with the one that is listed for the directories:
```

slash@helios:~$ u1sdtool --list-folders
Folder list:
  id=a9b35284-c63d-4cfd-8e2e-1e4792ba57a3 subscribed=True path=/home/slash/Documents

slash@helios:~$ u1sdtool --unsubscribe-folder a9b35284-c63d-4cfd-8e2e-1e4792ba57a3 

slash@helios:~$ u1sdtool -q;u1sdtool -c

```

See if that stops it.

---

### Post by RedSingularity on 2010-10-27
mcnica:  Do you have 10.10 installed as well?

---

### Post by mcnica on 2010-10-27
Yes, I have the 64bit version of 10.10 installed.

---

### Post by mcnica on 2010-10-27
torpidnotion: I tried unsubscribing a folder via the terminal like you recommended I got this error

```
~$ u1sdtool --unsubscribe-folder 79901d85-9f55-4854-9903-2a989df15681

Oops, an error ocurred:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 270, in run
    self.__run()
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/tools.py", line 92, in parse_reply
    *message.get_args_list()))
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 345, in errback
    self._startRunCallbacks(fail)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 424, in _startRunCallbacks
    self._runCallbacks()
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 441, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/bin/u1sdtool", line 127, in <lambda>
    d.addErrback(lambda r: show_error(r, out))
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/tools.py", line 794, in show_error
    raise error.value
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

---

### Post by mcnica on 2010-10-29
I got things working again.  It seems that Documents and Music would not be removed from the server.  I opened a terminal and deleted the folders from the server.

u1sdtool --delete-folders=

After deleting the folders, I removed my ubuntuone key and removed the local, cache, and config ubuntuone folders.  Reboot the machine and now everything is working.  It is not trying to sync Documents and music anymore and I have been able to sync only a few folders that I wanted to be synced.  Thanks for all the help.

---

