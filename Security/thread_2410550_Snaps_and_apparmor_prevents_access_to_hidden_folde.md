---
title: "Snaps and apparmor prevents access to hidden folders in home dir"
date: 2019-01-17
forum: Security
---

### Post by crusty1337 on 2019-01-17
I'm running Ubuntu 18.10

I'm a little confused about how to best accomplish what I want, so if someone could point me in the right direction that would be appreciated.

I've installed a number of applications as snaps from the software center and none of them can access hidden directories (directories staying with a ".") in my home folder. My home folder is in the default location of /home/user

Using journalctl I determined that apparmor was preventing access (permission denied).

There are no apparmor profiles for any of the apps in /etc/apparmor.d, but I did find some profiles in /var/lib/snap/apparmor/profiles which seem to grant access to /home/ but NOT any hidden folders. I'm not sure how apparmor knows how to load these profiles but these profiles seem to be causing me my grief.

Why is this an issue?
Well I've installed libreoffice (to view docx files) as a snap and evolution (to handle my email). If I click on docx attachments in evolution the file is downloaded to /home/user/.cache/evolution/tmp before launching libreoffice.writer to open it. Libreoffice is not allowed to open it because apparmor blocks it. Moving the file from .cache directly into my home folder allows me to open it with libreoffice.

Similarly remmina is unable to access my ssh keys as they reside in /home/user/.ssh

I'm not sure why snaps are not allowed to access hidden directories by default - this seems unnecessarily limiting.

Is there some way I can create an apparmor profile to overwrite the default behavior of the snaps profiles?

If I modify the profiles in /var/lib/snap/apparmor/profiles I'm worried that my changes will be overridden when the system updates, or even worse, it's not updated if an update is pushed out.

---

### Post by suzukawa on 2019-01-17
You can modify your recently blocking profiles by

```
 sudo aa-logprof -d /etc/apparmor.d -f /var/log/syslog
sudo aa-logprof -d /etc/apparmor.d -f /var/log/syslog.1 
```

If this doesn't work just set the profile back to complain-mode and it will not block anymore.

```
 sudo aa-complain profile 
```

---

### Post by crusty1337 on 2019-01-24
I don't think that is correct. 
None of those commands work for me. Also I do not think that aa-logprof is even snap-aware ... aa-logprof doesn't seem to register that snap apparmor profiles are a thing (remember that my apparmor profiles are not in /etc/apparmor.d)

I have found the following from the remmina website:
[https://remmina.org/how-to-install-remmina/#for-users-with-a-distro-that-supports-snap-packages-including-ubuntu](https://remmina.org/how-to-install-remmina/#for-users-with-a-distro-that-supports-snap-packages-including-ubuntu)

> Some features just don&#8217;t work, for example accessing your personal ~/.ssh directory is not possible for a snap. You have to manually copy your ~/.ssh/* files under ~/snap/remmina/common/.ssh/

So I guess that is the solution for remmina at least.

---

### Post by suzukawa on 2019-01-25
If it is an apparmor related issue you may want to follow the tips in this link from 3. onwards.

[https://forum.snapcraft.io/t/security-policy-and-sandboxing/554](https://forum.snapcraft.io/t/security-policy-and-sandboxing/554)

Just replace the directory of the aa-profiles in the command I gave above with [I]-d /var/lib/snapd/apparmor/profiles .
[/I]
With

```
sudo aa-status
```

you can see which profiles are in enforced-mode. Btw DENY-Rules in profiles in complain-mode are also enforced.

---

### Post by crusty1337 on 2019-01-31
> [COLOR=#000000]Just replace the directory of the aa-profiles in the command I gave above with [/COLOR]*-d /var/lib/snapd/apparmor/profiles .*
this does not work:

```
$ sudo aa-logprof -d /var/lib/snapd/apparmor/profiles -f /var/log/syslog
Reading log entries from /var/log/syslog.
Updating AppArmor profiles in /var/lib/snapd/apparmor/profiles.


ERROR: Include file /var/lib/snapd/apparmor/profiles/tunables/global not found
$
$ sudo aa-complain snap.libreoffice.writer Can't find snap.libreoffice.writer in the system path list. If the name of the application
is correct, please run 'which snap.libreoffice.writer' as a user with correct PATH
environment set up in order to find the fully-qualified path and
use the full path as parameter.
$
$ sudo aa-complain /var/lib/snapd/apparmor/profiles/snap.libreoffice.writer 
Profile for /var/lib/snapd/apparmor/profiles/snap.libreoffice.writer not found, skipping
$

```


According to [https://help.gnome.org/users/evolution/3.10/data-storage.html.en](https://help.gnome.org/users/evolution/3.10/data-storage.html.en) Evolution's disposable data caches (i.e. where evolution is going to temporarily place attachments when you double-click on them to open) = $HOME/.cache/evolution
As far as I can tell there is no setting in Evolution to change this directory, so we are stuck with putting it into a hidden (starts with ".") directory.

The snap for LibreOffice has the "Access files in your home folder" (:home) interface, which is described here [https://docs.snapcraft.io/the-home-interface/7838](https://docs.snapcraft.io/the-home-interface/7838) as "home allows access to **non-hidden files** in the user’s home ($HOME) directory."

Looking at the /var/lib/snapd/apparmor/profiles/snap.libreoffice.writer file there is nothing to allow access to $HOME/.cache/
I can solve my problem by adding the following to the bottom of **/var/lib/snapd/apparmor/profiles/snap.libreoffice.writer:**

```
# Allow read access to Evolution's disposable data cache directory (i.e. opening attachments)
owner @{HOME}/.cache/evolution/tmp/**             r,


```

and then reloading the apparmor profile:
```

$ sudo apparmor_parser -r /var/lib/snapd/apparmor/profiles/snap.libreoffice.writer
$

```

I just didnt want to do this as I was worried about system upgrade over-writing these changes, or not being applied because I have manually edited the file

The only other way I can think of to allow LibreOffice to open attachments is to symlink to a non hidden directory
```

$ mv ~/.cache/evolution/tmp/ ~/dot_cache_evolution_tmp
$ ln -s ~/dot_cache_evolution_tmp/ ~/.cache/evolution/tmp
$

```

The entire problem is that we are trying to pass a temporary file from one snap application to another snap application and there does not seem to be an effective way to do this yet :(

---

### Post by crusty1337 on 2019-02-13
Ah yes, it appears as if the **/var/lib/snapd/apparmor/profiles/snap.libreoffice.writer** file is overwritten when snapd updates the libreoffice snap, just as i feared (or at least my changes are no longer there after an update this morning).

So maybe the symlink option is the way forward?

---

### Post by psuter2 on 2019-08-23
Hi crusty 
i ran into a similar problem where apparmor was blocking my pre scripts that i wanted to run in a remmina snap. 

i was finally able to switch the snap.remmina.remmina profile to complain mode after i first symlinked the profile definition from /var/lib/snapd/apparmor/profiels to the /etc/apparmor.d folder like so: 
```
ln -s /var/lib/snapd/apparmor/profiles/snap.remmina.remmina /etc/apparmor.d/
```
after doing this, i could switch to complain mode: 
```
# aa-complain snap.remmina.remmina 
Setting /var/lib/snapd/apparmor/profiles/snap.remmina.remmina to complain mode.
```
and now my scripts are working :) maybe this helps with your issue as well.

---

### Post by TheFu on 2019-08-23
Support for 18.10 ended in mid-July.  Best to run only LTS releases like 18.04 if you can't move to a new release every 6 months, before support ends.  Basically, moving to 19.04 now is the first thing that should happen and a plan to move to 19.10 in Nov/Dec needs to be planned.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I don't use snaps. Sorry.

---

### Post by psuter2 on 2019-08-24
TheFu: sorry, i was replying to an old thread.. the OP was using 18.10 back in January this year and the related problem I had and solved was actually occurring on two separate machines, one running a rather fresh 19.04 install and the other on 18.04 ..

---

