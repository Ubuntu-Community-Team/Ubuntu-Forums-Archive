---
title: "Fails searching for libunixprintplugin.so"
date: 2009-03-03
forum: Ubuntuzilla
---

### Post by CodeNosher on 2009-03-03
Hello,

I'm trying to use this and have hit this error after running in a couple of times.  It fails when trying to find libunixprintplugin.so.  It appears I do not have one of these.  

From what I can tell my plugins are at /opt/firefox/plugins  

The script has this:

        result = self.util.getSystemOutput(executionstring="find /usr/lib -name 'libunixprintplugin.so'", numlines=0)
        for line in result:

Since I don't seem to have a "libunixprintplugin.so" the find fails.  I'm not sure what a libunixprintplugin.so is.  Can you please let me know what to do?


Here's the error:

gpg: Signature made Mon 02 Feb 2009 11:41:18 PM EAT using DSA key ID 17785FE8
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 8D6F 1BA4 A340 4DDB 3F2F  D080 7447 4499 8123 47DD
     Subkey fingerprint: 3338 E6BA FF10 3B3D A6A9  E424 B57B 5484 1778 5FE8
**Trying to determine firefox plugin path...**
find /usr/lib -name 'libunixprintplugin.so'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1146, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 209, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 236, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 610, in install
    self.linkPlugins()
  File "/usr/local/bin/ubuntuzilla.py", line 506, in linkPlugins
    result = self.util.getSystemOutput(executionstring="find /usr/lib -name 'libunixprintplugin.so'", numlines=0)
  File "/usr/local/bin/ubuntuzilla.py", line 118, in getSystemOutput
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by nanotube on 2009-03-03
Hi
What version of ubuntu are you running?

---

### Post by CodeNosher on 2009-03-04
7.10

---

### Post by nanotube on 2009-03-04
hi

well, libunixprintplugis.so /should/ be there in /usr/lib, if you have a firefox from the repos installed...

do you have /any/ plugins installed from the repos?

---

### Post by hongleong on 2009-07-04
I'm having the same issue.

Ubuntuzilla used to work perfectly for me but recently it started failing. The command I have been using all along is:

$ ubuntuzilla.py -a install --skipbackup -p seamonkey

I'm using:
[LIST]
[*]Ubuntu 8.04.3 LTS
[*]ubuntuzilla: 4.6.1-0ubuntu1
[*]firefox-3.0: 3.0.11+build2+nobinonly-0ubuntu0.8.04.1
[/LIST]

Here's part of the log leading to the error:

> Verifying Seamonkey MD5 sum

./seamonkey-1.1.17.en-US.linux-i686.tar.gz: OK
[sudo] password for hongleong:
If you have the repositories version of Firefox installed, you can choose to link all the Firefox plugins to your Seamonkey install. Would you like to do that? [y/n]?
Please enter 'y' or 'n': y
Trying to determine firefox plugin path...
find /usr/lib -name 'libunixprintplugin.so'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1146, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 215, in start
    si.start()
  File "/usr/local/bin/ubuntuzilla.py", line 236, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 610, in install
    self.linkPlugins()
  File "/usr/local/bin/ubuntuzilla.py", line 971, in linkPlugins
    MozillaInstaller.linkPlugins(self)
  File "/usr/local/bin/ubuntuzilla.py", line 506, in linkPlugins
    result = self.util.getSystemOutput(executionstring="find /usr/lib -name 'libunixprintplugin.so'", numlines=0)
  File "/usr/local/bin/ubuntuzilla.py", line 118, in getSystemOutput
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

Any clue?

---

### Post by nanotube on 2009-07-04
Hi
hmm, strange...
can you try running the find command manually and see what it finds?
```

find /usr/lib -name 'libunixprintplugin.so'

```

---

### Post by hongleong on 2009-07-04
Hi nanotube,

Thanks for helping. Here you go...

> $ find /usr/lib -name 'libunixprintplugin.so'
/usr/lib/xulrunner-addons/plugins/libunixprintplugin.so
/usr/lib/seamonkey/plugins/libunixprintplugin.so

$ locate libunixprintplugin.so
/opt/seamonkey/plugins_2009-01-13T13:56:32+0800/libunixprintplugin.so
/usr/lib/seamonkey/plugins/libunixprintplugin.so
/usr/lib/xulrunner-addons/plugins/libunixprintplugin.so
/usr/share/Songbird/xulrunner/plugins/libunixprintplugin.so

---

### Post by nanotube on 2009-07-05
Hi
hmm, that's weird, it seems that it should be working....

here, could you run this modified version of ubuntuzilla, attached, (should print out the actual command output on error), and post output here.

just download the file to wherever you want (e.g., your desktop), extract it, open a terminal, cd to the directory where you downloaded it to, and run
```

python ubuntuzilla_test.py -a install -p seamonkey --skipbackup

```

---

### Post by hongleong on 2009-07-05
Hi nanotube,

Thanks for the script. I need to go out now, but will try to test it tonight after I'm back. :)

You have a great day!

---

### Post by hongleong on 2009-07-06
Hi nanotube,

I think I know what's causing the problem.

In the log that I quoted, I removed a "Permission denied" line from it, thinking that it's not important or related.

This is what it should be:

> $ find /usr/lib -name 'libunixprintplugin.so'
/usr/lib/xulrunner-addons/plugins/libunixprintplugin.so
/usr/lib/seamonkey/plugins/libunixprintplugin.so
find: /usr/lib/AntiVir/gui: Permission denied

$ echo $?
1

After temporarily applying "chmod o+rx" to the denied directories, ubuntuzilla is able to run successfully. Looks like I'll have to remember to chmod everytime before running ubuntuzilla, although a more comprehensive solution is to change the script to take care of such permission issue.

Thank you. :p

---

### Post by nanotube on 2009-07-06
Hi

indeed, that would explain it! :)

Why not just permanently chmod o+x that stuff in /usr/bin/antivir? only programs (rather than program data) should live in /usr/bin, so there's no reason to restrict read access to it... ?

---

### Post by hongleong on 2009-07-07
Hi nanotube,

I thought of doing that too, but when I look at what AntiVir is trying to protect, I found that the directory /usr/lib/AntiVir/gui/cert contains these files: cacert.jks, cacert.pem, client.jks, server.pem

The other files/directories are actually unprotected. I suppose AntiVir protected these directories because of these certificates.

---

