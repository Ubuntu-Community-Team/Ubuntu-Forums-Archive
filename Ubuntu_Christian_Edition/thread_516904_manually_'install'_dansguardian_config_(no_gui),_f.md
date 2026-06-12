---
title: "manually 'install' dansguardian config (no gui), firefox proxy - update script"
date: 2007-08-03
forum: Ubuntu Christian Edition
---

### Post by TravMan63 on 2007-08-03
Due to (my) past installation difficulties and upgrades of Ubuntu CE 7.04 (Dansguardian in particular)  - I have these questions:

The Dansguardian gui is tied closely to the dansguardian config file - If you uninstall one - I 'believe' both must be uninstalled (dependency issues)... although dansguardian CAN stand on it's own (can be reinstalled) - but - no gui. (again - for some that's ok - I've been doing most of my config via ssh wireless remote connection via putty.exe on a XP box)

I like the gui - it's a nice piece of work.

So - one could - manually config (or replace) the files - (although for some, I'm sure it isn't something they would feel comfortable doing (and that's perfectly fine)).... and it's not as easy and quick as the install script.

Now that my mumbling is over...

1st - one would need the correct files installed
dansguardian, tinyproxy, firehol, clamav2 (am I missing any?)

Is it possible - to extract the config files from the update tar

(install_dansguardian_gui_feisty.tar.gz)

and just manually insert the files where needed? (backing up original config files is a very good idea!)

IE - specific files such as:
firefox.js
firefox.cfg
firehol.conf (although I wonder if this should be 'firehol' ?)
sources.list (I doubt that is needed - it's just for the gui? not sure)

tinyproxy.conf
and 
dansguardian.conf and
template.html

---
I'm guessing it's not that easy, and it's why there is a script.

I have everything (but the gui) installed.  Unfortunately, I left the proxy settings locked before I uninstalled the gui- and now when I go to edit them (they were set to directly connect - and not use tinyproxy) - they are greyed out (I assume that is what the 'lock' function of the gui does.) - I"ve read of a user.JS file(?) that can lock these - but it doesn't exist... in the firefox directory...


I'm considering giving this a shot and see if it corrects my problem (proxy and filtering - although I think I have errors with firehol ?)- but if anyone out there has already climbed this mountain... I"d appreciate the input!

TM
----------
>edit - filtering ON! (processes not starting)

I ran a script which allowed me to edit my settings in firefox
I reset it to:
- Firefox - edit-preferences - advanced-network-settings

manual

		HTTP PROXY	127.0.0.1 PORT 8080
		NO PROXY FOR  	localhost 127.0.0.1

----
now - need to lock the file again,
make dansguardian and tinyproxy run at startup

(receiving these errors: on tty8 )

/etc/init/rc: 2: /etc/rc2.d/s20tinyproxy: Permission denied
/etc/init/rc: 2: /etc/rc2.d/s50Dansguardian: Permission denied

I can run them later with no problems... perhaps the files in that dir are not executeable?
hmm - they are ..

but in folder - /etc/init.d (I had to copy to there) - they are not (should be 755 are 644
firehol was as well, changed it also...

reboot and hope it all works!

(also hoping these files will be 'portable' - that is - I can set this up on elive and SAM linux... and other distros!)
---------

---

