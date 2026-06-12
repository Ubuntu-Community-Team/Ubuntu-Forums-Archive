---
title: "Issues with mandos / mandos -client"
date: 2015-10-07
forum: Server Platforms
---

### Post by ruessel on 2015-10-07
Hello Everyone!

as i am new to Ubuntu, a first-timer since about a month, i guess it is best to post this here,
if not so, please pardon me Mod's! 

Well, here is the Issue:
Every time i install a package (Whether with the Synaptic-packet management, or by Terminal), i get 
error messages from the mandos-client, 

Here is the duplicate of my bug: [https://bugs.launchpad.net/ubuntu/+source/mandos/+bug/1400145](https://bugs.launchpad.net/ubuntu/+source/mandos/+bug/1400145)

so i looked for solutions on the web, and found this one:
[http://askubuntu.com/questions/563157/package-operation-failed-warning-some-openpgp-programs-cant-handle-a-dsa-key-w](http://askubuntu.com/questions/563157/package-operation-failed-warning-some-openpgp-programs-cant-handle-a-dsa-key-w)

And did what it says:
> [TABLE]
[TR]
[TD="class: answercell"] Did you give a try with purging mandos-client?

  ```
$ sudo apt-get autoremove --purge  mandos-client 

```  This should remove this package in a clean way, so that you can install later.
--------------------[/TD]
[/TR]
[TR]
[TD][TABLE]
[TR="class: comment"]
[TD="class: comment-text"]                              That solved it.  Now sudo  apt-get upgrade is putting out:  The following packages have been kept  back:
   linux-generic linux-headers-generic linux-image-generic 0  upgraded, 0 newly installed, 0 to remove and 3 not upgraded.                 &#8211;                      [Shut Up]("http://askubuntu.com/users/324057/shut-up")                 [Dec 19 '14 at 4:52]("http://askubuntu.com/questions/563157/package-operation-failed-warning-some-openpgp-programs-cant-handle-a-dsa-key-w#comment774478_563159")[/TD]
[/TR]
[TR="class: comment"]
[TD="class: comment-text"]                              ------------------
The previous comment was solved just fine with ```
sudo apt-get dist-upgrade
```                 &#8211;                      [Shut Up]("http://askubuntu.com/users/324057/shut-up")                 [Dec 19 '14 at 5:11]("http://askubuntu.com/questions/563157/package-operation-failed-warning-some-openpgp-programs-cant-handle-a-dsa-key-w#comment774485_563159")[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]


So, been there, done that, and after the next reboot, after logging in everything freezes, no Dash, no mouse, nothing...
So i rebooted again a few times, also using the recovery mode to check the filesystem, reboot again, but nothing.
So i guess i bricked this kernel... Any suggestions to repair it?

Thankfully i have the option to use a earlyer kernel with the ending number -28 or -30 (vs ending number -31 in the broken one)
with whom i was able to boot in to ubuntu again.

[B]EDIT: 
Solved Brick/freeze after login-Issue:
Uninstalled the Linux kernel image for version 3.19.0-31 on 64 bit x86 SMP with all dependencies.[/B]

So first thing i did was to check in Synaptic if mandos-client is installed here, but nope...
So, i checked it for installation and got this darn log:

```

(synaptic:4625): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
Vormals nicht ausgewähltes Paket add-apt-key wird gewählt.
(Lese Datenbank ... 282724 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../add-apt-key_1.0-0.5_all.deb ...
Entpacken von add-apt-key (1.0-0.5) ...
Vormals nicht ausgewähltes Paket gui-apt-key wird gewählt.
Vorbereitung zum Entpacken von .../gui-apt-key_0.4-2ubuntu1_all.deb ...
Entpacken von gui-apt-key (0.4-2ubuntu1) ...
Trigger für man-db (2.6.7.1-1ubuntu1) werden verarbeitet ...
Trigger für gnome-menus (3.10.1-0ubuntu2) werden verarbeitet ...
Trigger für desktop-file-utils (0.22-1ubuntu1) werden verarbeitet ...
Trigger für bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) werden verarbeitet ...
Rebuilding /usr/share/applications/bamf-2.index...
Trigger für mime-support (3.54ubuntu1.1) werden verarbeitet ...
mandos-client (1.6.0-1) wird eingerichtet ...
Note: Due to entropy requirements, key generation could take
anything from a few minutes to SEVERAL HOURS.  Please be
patient and/or supply the system with more entropy if needed.
Started: Mi 7. Okt 12:58:42 UYT 2015
gpg: WARNING: some OpenPGP programs can't handle a DSA key with this digest size
++++++++++..++++++++++++++++++++.....++++++++++.+++++.++++++++++.+++++...+++++.....+++++.+++++++++++++++...+++++...+++++++++++++++.++++++++++++++++++++...++++++++++>+++++>....+++++............................................................................................>+++++...........+++++
+++++++++++++++...+++++++++++++++..+++++...+++++..+++++++++++++++..+++++++++++++++.+++++++++++++++++++++++++.++++++++++.++++++++++.+++++.++++++++++...+++++++++++++++>..+++++...+++++>+++++....................>.+++++.......................................................................................................................................................................................................+++++^^^
[B][I]gpg: fatal: '/tmp/mandos-keygen-keyrings.NlLBJJvO4f/trustdb.gpg' Unable to open: file or directory not found
secmem usage: 3424/6848 bytes in 8/19 blocks of pool 7488/65536
dpkg: Error processing the packet mandos-client (--configure):
Subprocess installed post-installation script returned error value 2[/I][/B]
add-apt-key (1.0-0.5) wird eingerichtet ...
gui-apt-key (0.4-2ubuntu1) wird eingerichtet ...
[B][I]Errors were encountered while processing:
 mandos-client[/I][/B]
[I][B]E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Recovery is attempted:
mandos-client (1.6.0-1) installing ...[/B][/I]
Note: Due to entropy requirements, key generation could take
anything from a few minutes to SEVERAL HOURS.  Please be
patient and/or supply the system with more entropy if needed.
Started: Mi 7. Okt 13:05:44 UYT 2015
gpg: WARNING: some OpenPGP programs can't handle a DSA key with this digest size
+++++.+++++..+++++.+++++++++++++++.+++++.++++++++++.++++++++++.++++++++++.+++++..++++++++++.+++++..++++++++++..+++++..++++++++++.++++++++++++++++++++....+++++>+++++..>.....+++++.....<+++++......................................................................................................+++++
.++++++++++.+++++.++++++++++++++++++++++++++++++.+++++.+++++.+++++.++++++++++..+++++..+++++++++++++++++++++++++++++++++++.++++++++++++++++++++.++++++++++++++++++++>+++++...>.+++++.........................................................................................................................................+++++^^^
gpg: fatal: '/tmp/mandos-keygen-keyrings.Zxbw1FA7nc/trustdb.gpg' ***Unable to open: file or directory not found***
secmem usage: 3424/6848 bytes in 8/19 blocks of pool 7520/65536
[B][I]dpkg:Error processing the packet mandos-client (--configure):
 Subprocess installed post-installation script returned error value 2
 Errors were encountered while processing:
 mandos-client[/I][/B]


```

I tried to translate the relevant areas (marked Bold) as accurate as possible(German Language pack).

I looked if the File ```
trustdb.gpg
``` exists, and it does. in several locations.
As it seems to me, the mandos-client (or the server???) is supposed to create a 
temporary folder to place the key, but fails to do so. I looked in to /tmp but did not
find any folders with relevant names(and, yes, cheched to show hidden files)...

Any suggestions?

PS: As i said, i am a noob, i can use the terminal if told to do in a manner, BUT i am
far from understanding the commands i put in there, so please dont bash me!!! :)

Best regards, Ruessel!

---

### Post by ruessel on 2015-10-07
Hi everyone,

i think i stumbled upon a possible solution, but hence my oblivion about what i am actually doing,
i wanted to ask if it sounds like a good idea to follow the guide. 

I found this:

[https://bugs.launchpad.net/ubuntu/+source/mandos/+bug/1400145](https://bugs.launchpad.net/ubuntu/+source/mandos/+bug/1400145)

and at the end, one of the [Mandos Maintainers (mandos-maintainers)]("https://launchpad.net/%7Emandos-maintainers") suggests following:

```
=== modified file 'mandos-keygen'
--- mandos-keygen    2014-02-16 13:12:20 +0000
+++ mandos-keygen    2014-03-01 09:51:07 +0000
@@ -228,6 +228,11 @@
     date
     fi
     
+    # Make sure trustdb.gpg exists;
+    # this is a workaround for Debian bug #737128
+    gpg --quiet --batch --no-tty --no-options --enable-dsa2 \
+    --homedir "$RINGDIR" \
+    --import-ownertrust < /dev/null
     # Generate a new key in the key rings
     gpg --quiet --batch --no-tty --no-options --enable-dsa2 \
     --homedir "$RINGDIR" --trust-model always \
```

So, as a noob, i can copy and paste the code, BUT i have some questions:
1. Is it relevant WHERE trustdb.gpg exists? Or should it be in a specific folder?
2.How and where do i Generate a new Key in to which ring??? :O

Help? :/

Best regards, Ruessel

PS: I use Ubuntu 14.04, if that helps...

---

