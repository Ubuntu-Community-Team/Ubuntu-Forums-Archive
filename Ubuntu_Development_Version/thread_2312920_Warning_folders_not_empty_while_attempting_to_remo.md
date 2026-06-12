---
title: "Warning folders not empty while attempting to remove python3.4"
date: 2016-02-08
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2016-02-08
```
cavsfan@cavsfan-le-beast:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libpython3.4 libpython3.4-minimal libpython3.4-stdlib python3.4 python3.4-minimal
The following packages will be upgraded:
  findutils
1 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 280 kB of archives.
After this operation, 26.6 MB disk space will be freed.
Do you want to continue? [Y/n] Y
```

Then while it was doing so, it got some xargs errors. Those I did not capture. But, I did notice this:
```

Report bugs to <bug-findutils@gnu.org>.
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/asyncio' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/distutils/command' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/json' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/sqlite3' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/lib2to3/fixes' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/lib2to3/pgen2' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/email/mime' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/venv' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/curses' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/dbm' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/concurrent/futures' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/tkinter' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/xml/sax' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/xml/parsers' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/xml/etree' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/xml/dom' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/ctypes' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/html' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/test/support' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/idlelib' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/multiprocessing/dummy' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/urllib' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/wsgiref' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/xmlrpc' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/http' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/unittest' not empty so not removed
dpkg: warning: while removing libpython3.4-stdlib:amd64, directory '/usr/lib/python3.4/pydoc_data' not empty so not removed
Removing python3.4-minimal (3.4.4-1) ...
```


So, I guess it would be save to delete the /usr/lib/python3.4/ folder right?

---

### Post by dino99 on 2016-02-08
as said into the installlog, its a bug to report upstream against findutils
i've taken the risk of:" sudo rm -rf /usr/lib/python3.4* " to clean my system

---

### Post by mc4man on 2016-02-08
> **Cavsfan said:**
> 


So, I guess it would be save to delete the /usr/lib/python3.4/ folder right?
Well you may wish to leave the /usr/lib/python3.4/lib-dynload  folder alone as it may still be  used by some things (from python3-gdbm package

---

### Post by Cavsfan on 2016-02-08
> **dino99 said:**
> as said into the installlog, its a bug to report upstream against findutils
i've taken the risk of:" sudo rm -rf /usr/lib/python3.4* " to clean my system

That's what I was thinking, but it did not list all the directories in that folder, nor did it delete them either. I figured it was a dumb/rhetorical question!
But, since it only listed some of the folders in that folder maybe not. But, since this is in development, one can always start over with a clean install from the daily ISOs.

> **mc4man said:**
> Well you may wish to leave the /usr/lib/python3.4/lib-dynload  folder alone as it may still be  used by some things (from python3-gdbm package

You seem to know much more than I do about this stuff. Like leaving that folder alone.
I think I'll just leave that whole folder alone, or maybe do the **rm -rf **to the folders listed in the output only.

---

### Post by Cavsfan on 2016-02-08
BTW, am I the only one that seen these errors in terminal? I simply do not use Update Mangler, never did. Thanks to Ranch Hand.

---

### Post by mc4man on 2016-02-08
The recent/current images don't include python3.4-minimal & it's direct deps/recommends  so not an issue 
ex. xubuntu - [http://cdimage.ubuntu.com/xubuntu/daily-live/current/xenial-desktop-amd64.manifest](http://cdimage.ubuntu.com/xubuntu/daily-live/current/xenial-desktop-amd64.manifest)

---

### Post by Doug S on 2016-02-08
> **Cavsfan said:**
> BTW, am I the only one that seen these errors in terminal? I simply do not use Update Mangler, never did. Thanks to Ranch Hand.I have been seeing some issues during updates also. I had some "not empty so not removed" messages also (on my 16.04 server). My test 16.04 LapTop has been complaining about stuff not found for a long time, I just haven't gotten around to starting from scratch again with a new daily ISO.

---

### Post by Doug S on 2016-02-09
I have been focused on my servers in recent days. Today I am attempting to update my test 16.04 LapTop, and it is complaining while doing so. Example:```
Setting up bsdutils (1:2.27.1-1ubuntu4) ...
(Reading database ... 300788 files and directories currently installed.)
Removing python3.4 (3.4.4-1) ...
xargs: invalid number for -s option
Usage: xargs [OPTION]... COMMAND [INITIAL-ARGS]...
Run COMMAND with arguments INITIAL-ARGS and more arguments read from input.

Mandatory and optional arguments to long options are also
mandatory or optional for the corresponding short option.
  -0, --null                   items are separated by a null, not whitespace;
...

```And I see this one a lot:```
Setting up ubuntu-settings (15.10.7) ...
Setting up unattended-upgrades (0.89.1) ...
[COLOR="#FF0000"]update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults[/COLOR]
Setting up unity-settings-daemon (15.04.1+16.04.20160209-0ubuntu1) ...
Setting up x11-common (1:7.7+13ubuntu1) ...
[COLOR="#FF0000"]update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults[/COLOR]
Setting up xserver-xorg-input-all (1:7.7+13ubuntu1) ...
Setting up xserver-xorg (1:7.7+13ubuntu1) ...
```

---

### Post by Cavsfan on 2016-02-09
> **mc4man said:**
> The recent/current images don't include python3.4-minimal & it's direct deps/recommends  so not an issue 
ex. xubuntu - [http://cdimage.ubuntu.com/xubuntu/daily-live/current/xenial-desktop-amd64.manifest](http://cdimage.ubuntu.com/xubuntu/daily-live/current/xenial-desktop-amd64.manifest)

Good to know. I searched the manifest and found no existence of **python3.4** anywhere.

> **Doug S said:**
> I have been focused on my servers in recent days. Today I am attempting to update my test 16.04 LapTop, and it is complaining while doing so. Example:```
Setting up bsdutils (1:2.27.1-1ubuntu4) ...
(Reading database ... 300788 files and directories currently installed.)
Removing python3.4 (3.4.4-1) ...
xargs: invalid number for -s option
Usage: xargs [OPTION]... COMMAND [INITIAL-ARGS]...
Run COMMAND with arguments INITIAL-ARGS and more arguments read from input.

Mandatory and optional arguments to long options are also
mandatory or optional for the corresponding short option.
  -0, --null                   items are separated by a null, not whitespace;
...

```And I see this one a lot:```
Setting up ubuntu-settings (15.10.7) ...
Setting up unattended-upgrades (0.89.1) ...
[COLOR=#FF0000]update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults[/COLOR]
Setting up unity-settings-daemon (15.04.1+16.04.20160209-0ubuntu1) ...
Setting up x11-common (1:7.7+13ubuntu1) ...
[COLOR=#FF0000]update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults[/COLOR]
Setting up xserver-xorg-input-all (1:7.7+13ubuntu1) ...
Setting up xserver-xorg (1:7.7+13ubuntu1) ...
```

I did see several errors in the output while getting this yesterday about xargs. Like this:
> xargs: invalid number for -s option
Usage: xargs [OPTION]... COMMAND [INITIAL-ARGS]...
Run COMMAND with arguments INITIAL-ARGS and more arguments read from input.

And I also see [COLOR=#FF0000]update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults[/COLOR] warnings all the time.
I've gotten to just ignore them and I don't know if that's right or wrong.

I guess I'll do what dino99 did and get rid of the whole shebang.

---

### Post by QDR06VV9 on 2016-02-09
> **Cavsfan said:**
> Good to know. I searched the manifest and found no existence of **python3.4** anywhere.



I did see several errors in the output while getting this yesterday about xargs. Like this:


And I also see [COLOR=#FF0000]update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults[/COLOR] warnings all the time.
I've gotten to just ignore them and I don't know if that's right or wrong.

I guess I'll do what dino99 did and get rid of the whole shebang.
Well I guess we will both be in this together..:D
That is what I did already and nothing bad to report yet..(I did say yet)

---

### Post by Cavsfan on 2016-02-09
> **runrickus said:**
> Well I guess we will both be in this together..:D
That is what I did already and nothing bad to report yet..(I did say yet)

:lol: If there's nothing on the manifest then we should be good to go.

---

