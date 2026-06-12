---
title: "Ukash New Zealand Police Variant"
date: 2013-11-15
forum: Security
---

### Post by bombze.326 on 2013-11-15
Hi Everyone!

I am a newbie on using ubuntu and I'm currently using an Ubuntu 12.04 on a Sony VAIO VPCEB33FM partitioned/dual-boot with Windows 7.

I've been searching around the forum regarding the ukash virus but none of the threads has helped me. Even this one, [http://ubuntuforums.org/showthread.php?t=2174536&highlight=ukash](http://ubuntuforums.org/showthread.php?t=2174536&highlight=ukash)

I've been infected about 2-3 weeks ago and right after I've acquired the malware, a project required me to use my Windows 7 and during those times, I haven't been able to use my ubuntu.

So, when I've contracted the virus(using Firefox), I was still able to surf the internet but when I logged out, I couldn't log back in to my GUI desktop however I could login to the terminal.

I've tried scanning with ClamAV and AVG to no avail.  

All the google results returned with mostly Windows problem and solutions.

I am writing this post on my Windows 7 partition on the same laptop. 

Thanks in advance!

bombze

---

### Post by houstonbofh on 2013-11-15
Log in to the CLI and create a new user...

```
**sudo adduser** *username*
**sudo usermod -a -G adm,admin,audio,cdrom,dialout,fax,sudo,dip,video,plugdev,fuse,netdev,lpadmin,sambashare** *username*
```

Your groups may differ from mine.  To check what you need look at groups with your old username like this.
```
lee@it-ubuntu-lee:~$ more /etc/group | grep lee
adm:x:4:lee
dialout:x:20:lee
fax:x:21:lee
cdrom:x:24:lee
floppy:x:25:lee
tape:x:26:lee
audio:x:29:pulse,lee
dip:x:30:lee
video:x:44:lee
plugdev:x:46:lee
fuse:x:104:lee
lpadmin:x:105:lee
netdev:x:112:lee
admin:x:119:lee
sambashare:x:122:lee
lee:x:1000:
```

If the new users works, selectively restore things from your old home directory until it fails again.

---

### Post by bombze.326 on 2013-11-17
hi houstonbofh,

thanks for the help but I still couldn't log in (GUI).

also, what do you mean "...until it fails again."?

cheers!

---

### Post by Irihapeti on 2013-11-17
When you say that you can't log in (GUI), exactly what happens? Does the login screen not appear at all? Does the login refuse to accept your username and password? Does it accept them and then try to load Firefox immediately? Or something else?

---

### Post by houstonbofh on 2013-11-17
If a clean new user also fails, then we need to know a lot more about how exactly it fails.

---

### Post by bombze.326 on 2013-11-18
hi guys,

When I boot into ubuntu, the only GUI that I see is the login screen.

When I try to login into my account or a newly created user or just the guest, what happens is that it only flashes a black screen for a few seconds and it brings me back to the login screen. I couldn't get through that and I think it is accepting every passwords only that it just couldn't load the GUI desktop for the user.

Hope it helps and if you need more info, I'd be glad to give. I just don't know what info to give though. 

Thank you!

---

### Post by bombze.326 on 2013-11-27
Okay, so I was trying to migrate my ubuntu to Virtualbox so that I could just troubleshoot from there and when I performed an e2fsck on it and did a restart, a GUI error page prompted me for the first time to try and fix the GUI problem.

I tried following the prompt page but I still wasn't able to fix it however, I have created an error log about it.

==========================================================================
[I][+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.2.3, UID=0 PID=1381
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for greeter
[+0.00s] DEBUG: Starting local X display
[+0.01s] DEBUG: X server :0 will replace Plymouth
[+0.03s] DEBUG: Using VT 7
[+0.03s] DEBUG: Activating VT 7
[+0.03s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.03s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.03s] DEBUG: Launching X Server
[+0.03s] DEBUG: Launching process 1400: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
[+0.03s] DEBUG: Waiting for ready signal from X server :0
[+0.04s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.04s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.55s] DEBUG: Got signal 10 from process 1400
[+0.55s] DEBUG: Got signal from X server :0
[+0.55s] DEBUG: Stopping Plymouth, X server is ready
[+0.57s] DEBUG: Connecting to XServer :0
[+0.57s] DEBUG: Starting greeter
[+0.57s] DEBUG: Started session 1427 with service 'lightdm', username 'lightdm'
[+1.38s] DEBUG: Session 1427 authentication complete with return value 0: Success
[+1.38s] DEBUG: Greeter authorized
[+1.38s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+1.38s] DEBUG: Session 1427 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+1.66s] DEBUG: Greeter closed communication channel
[+1.66s] DEBUG: Session 1427 exited with return value 1
[+1.66s] DEBUG: Greeter quit
[+1.66s] DEBUG: Failed to start greeter
[+1.66s] DEBUG: Stopping display
[+1.66s] DEBUG: Sending signal 15 to process 1400
[+1.92s] DEBUG: Process 1400 exited with return value 0
[+1.92s] DEBUG: X server stopped
[+1.92s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+1.92s] DEBUG: Releasing VT 7
[+1.92s] DEBUG: Display server stopped
[+1.92s] DEBUG: Display stopped
[+1.92s] DEBUG: Stopping X local seat, failed to start a display
[+1.92s] DEBUG: Stopping seat
[+1.92s] DEBUG: Seat stopped
[+1.92s] DEBUG: Required seat has stopped
[+1.92s] DEBUG: Stopping display manager
[+1.92s] DEBUG: Display manager stopped
[+1.92s] DEBUG: Stopping daemon
[+1.92s] DEBUG: Exiting with return value 1[/I]
=======================================================================

I'm not sure if this is the right file because there are 5 files in a tar ball. I just posted this one because it might give a clue without having to post the other files which are quite long.

---

### Post by bashiergui on 2013-11-27
> **bombze.326 said:**
> 
I've been searching around the forum regarding the ukash virus but none of the threads has helped me. Even this one, [http://ubuntuforums.org/showthread.php?t=2174536&highlight=ukash](http://ubuntuforums.org/showthread.php?t=2174536&highlight=ukash)
I don't understand why you decided this was the ukash virus. Did you see a ransom demand?

---

### Post by bombze.326 on 2013-12-01
> **bashiergui said:**
> I don't understand why you decided this was the ukash virus. Did you see a ransom demand?

Yes I did and it is just as the same as this one; [http://blog.yoocare.com/how-to-remove-new-zealand-police-virus/](http://blog.yoocare.com/how-to-remove-new-zealand-police-virus/) 
Unfortunately I wasn't able to take a photo of it before restarting as I thought it could be solved with just a simple restart.

---

### Post by Irihapeti on 2013-12-01
There's a look-alike of Ukash virus that runs on MacOS. Basically, it's a javascript that hijacks the browser so that it can't be used, and also makes the browser start up as soon as you log in. See [http://forums.whirlpool.net.au/archive/2143816](http://forums.whirlpool.net.au/archive/2143816)

If something like this is happening on your machine, it's possible that it's also overloading the X-server and causing it to crash. Hence the logouts.

You could try renaming your Firefox profile folder from .mozilla to .mozilla-old and seeing if that helps. If it doesn't, no harm will have been done.

---

### Post by bombze.326 on 2013-12-17
> **Irihapeti said:**
> There's a look-alike of Ukash virus that runs on MacOS. Basically, it's a javascript that hijacks the browser so that it can't be used, and also makes the browser start up as soon as you log in. See [http://forums.whirlpool.net.au/archive/2143816](http://forums.whirlpool.net.au/archive/2143816)

If something like this is happening on your machine, it's possible that it's also overloading the X-server and causing it to crash. Hence the logouts.

You could try renaming your Firefox profile folder from .mozilla to .mozilla-old and seeing if that helps. If it doesn't, no harm will have been done.

Thanks for the suggestion however I've read the same/similar article already before posting this thread... :frown:

---

### Post by bashiergui on 2013-12-17
If you still can't log into the GUI after 4 weeks then I recommend you drop to a root shell and purge firefox, which should remove all the config files associated with it.  ```
sudo apt-get purge firefox
``` Then see if you can reboot & log into the GUI.

If you can, then you can reinstall firefox.

---

### Post by Irihapeti on 2013-12-17
That won't remove the user profile. To do that, you need to remove the folder .mozilla

You will, of course, lose all your bookmarks etc.

```
rm -r ~/.mozilla
```

It will automatically be recreated the next time Firefox is run.

---

### Post by bashiergui on 2013-12-17
:/ 
I'll never understand why "purge" doesn't actually purge.

Is there anything else he'd need to remove or would that wipe out Firefox?

---

### Post by Irihapeti on 2013-12-17
"Purge" removes system config files (such as in /etc) but not users' ones. As a rule, installing a program doesn't install a personal config; it is created when the program is first run.

Removing the personal profile should remove all traces of Firefox. If there are still problems, it's due to something else.

---

### Post by bashiergui on 2013-12-17
Good info from Irihapeti. Here's additional info about firefox's user profiles for the record [http://askubuntu.com/questions/16758/removing-firefox-in-ubuntu-with-all-add-ons-like-it-never-existed/16773#16773](http://askubuntu.com/questions/16758/removing-firefox-in-ubuntu-with-all-add-ons-like-it-never-existed/16773#16773)

---

### Post by Irihapeti on 2013-12-19
I've discovered that Firefox now keeps its cache in ~/.cache/mozilla

That also needs to be deleted in order to remove all personal Firefox files.

---

