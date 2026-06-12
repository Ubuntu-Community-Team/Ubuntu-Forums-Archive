---
title: "ubuntuzilla can't find .tar.gz extension"
date: 2008-06-17
forum: Ubuntuzilla
---

### Post by xmidway on 2008-06-17
running ubuntuzilla.py 4.4.7.
It looks for firefox-3.0.tar.gz and can't find the file because the file on the mozilla site is .tar.bz2 (the tar.gz extension is hard coded in ubuntuzilla.py).
So, I downloaded firefox-3.0.tar.bz2; bunzip2'ed it; gziped the .tar, and moved it to /tmp, but ubuntuzilla.py doesn't look for it in /tmp. It exits with "Download failed. This may be due to transient network problems, so try again later. Exiting." because it can't find a gzip file!
Any help?

---

### Post by naeonlite on 2008-06-18
I saw this problem too, I guess Mozilla have changed the file compression method they're using. I fixed it by doing:

```
sudo gedit /usr/local/bin/ubuntuzilla.py
```

and then find and replace on .tar.gz with .tar.bz2

---

### Post by xmidway on 2008-06-18
Yeah, I did the same, but it, of course, failed on the tar call.  Tar is called with -xzf so I had to change the z to j for the bz2 (I assume you did as well) and the script worked fine after that as I'm writing this reply on 3.0.
Thanks for the response.

---

### Post by DrMilo on 2008-06-20
> **xmidway said:**
> Yeah, I did the same, but it, of course, failed on the tar call.  Tar is called with -xzf so I had to change the z to j for the bz2 (I assume you did as well) and the script worked fine after that as I'm writing this reply on 3.0.
Thanks for the response.

I thought that I did that but I get:

sudo dpkg -L firefox-3.0 |egrep 'firefox(-[0-9]\.[0-9]+[a-z][0-9]+)?/plugins$'
Failed to determine plugin path. Exiting.
Process returned code 1
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1060, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 209, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 236, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 528, in install
    self.linkPlugins()
  File "/usr/local/bin/ubuntuzilla.py", line 681, in linkPlugins
    self.pluginPath = self.util.getSystemOutput(executionstring="sudo dpkg -L " + self.aptPackage + " |egrep 'firefox(-[0-9]\.[0-9]+[a-z][0-9]+)?/plugins$'", errormessage="Failed to determine plugin path. Exiting.")
  File "/usr/local/bin/ubuntuzilla.py", line 118, in getSystemOutput
    raise SystemCommandExecutionError, "Command has not completed successfully.

---

### Post by nanotube on 2008-06-20
Hi,
it looks like they changed the archive type for ff3, so ubuntuzilla was failing at installing it.
i have updated the code to take care of this, the latest release candidate is attached to this bug report thread on sourceforge:
[http://sourceforge.net/tracker/index.php?func=detail&aid=1996632&group_id=202789&atid=982990](http://sourceforge.net/tracker/index.php?func=detail&aid=1996632&group_id=202789&atid=982990)
i also took care of the different plugin path in hardy.
please feel free to give this one a try and let me know if it works as it should.
thanks for your feedback!

---

### Post by DrMilo on 2008-06-20
> **nanotube said:**
> Hi,
it looks like they changed the archive type for ff3, so ubuntuzilla was failing at installing it.
i have updated the code to take care of this, the latest release candidate is attached to this bug report thread on sourceforge:
[http://sourceforge.net/tracker/index.php?func=detail&aid=1996632&group_id=202789&atid=982990](http://sourceforge.net/tracker/index.php?func=detail&aid=1996632&group_id=202789&atid=982990)
i also took care of the different plugin path in hardy.
please feel free to give this one a try and let me know if it works as it should.
thanks for your feedback!

I c+p'd your file into ubuntuzilla.py. It installed FF but I get a crash when it starts or it starts as the old version.

---

### Post by OregonPete on 2008-06-21
> **DrMilo said:**
> I c+p'd your file into ubuntuzilla.py. It installed FF but I get a crash when it starts or it starts as the old version.

Did you remember to change the link in your launcher/menu to point to the new firefox installation?

BTW, I had the same problem -- ubuntuzilla couldn't find the .tar.gz extension. I installed the new ubuntuzilla release (4.4.9) and was then able to install firefox 3.0 without any problems. Um, well, there was another problem, but I'll open a new thread for that... ;-)

---

### Post by DrMilo on 2008-06-21
> **OregonPete said:**
> Did you remember to change the link in your launcher/menu to point to the new firefox installation?
BTW, I had the same problem -- ubuntuzilla couldn't find the .tar.gz extension. I installed the new ubuntuzilla release (4.4.9) and was then able to install firefox 3.0 without any problems. Um, well, there was another problem, but I'll open a new thread for that... ;-)

I just installed 4.4.9, Sourceforge has been down for the better part of 2 days it seems so I didn't know it was final, and I got another crash, see attached if you want. I'm wondering if I need another non-FF package? The problem with that theory is that FF3 is standard with HH 8.04. In any case I can't read core dumps so my FF crash report doesn't help me. Oh and there's a separate link for FF3, the link to FF2 doesn't crash.

---

### Post by nanotube on 2008-06-21
> **DrMilo said:**
> I just installed 4.4.9, Sourceforge has been down for the better part of 2 days it seems so I didn't know it was final, and I got another crash, see attached if you want. I'm wondering if I need another non-FF package? The problem with that theory is that FF3 is standard with HH 8.04. In any case I can't read core dumps so my FF crash report doesn't help me. Oh and there's a separate link for FF3, the link to FF2 doesn't crash.

so, are you saying that you have both ff3 and ff2 installed, from the hardy repositories?
if that's the case, it could be that ff3 from mozilla is trying to read the profile for ff2, rather than ff3. could you take a look at what profiles you have in ~/.mozilla? and see what happens if you run 
```
firefox -P 
```
and choose the ff3 profile?

---

### Post by DrMilo on 2008-06-21
> **nanotube said:**
> so, are you saying that you have both ff3 and ff2 installed, from the hardy repositories?
if that's the case, it could be that ff3 from mozilla is trying to read the profile for ff2, rather than ff3. could you take a look at what profiles you have in ~/.mozilla? and see what happens if you run 
```
firefox -P 
```
and choose the ff3 profile?

firefox -P gives me a cursor and nothing else. Attached is my profiles.ini

---

### Post by nanotube on 2008-06-22
try this instead:
```
firefox -profilemanager
```

---

### Post by DrMilo on 2008-06-22
> **nanotube said:**
> try this instead:
```
firefox -profilemanager
```

That launched a new session of Firefox.

---

### Post by nanotube on 2008-06-22
> **DrMilo said:**
> That launched a new session of Firefox.

cool... so does that mean you're good to go now? :)

---

### Post by DrMilo on 2008-06-23
> **nanotube said:**
> cool... so does that mean you're good to go now? :)

Firefox 2! If I install FF3 with your script it crashes. If I install it through the Hardy repos I get, "Failed to launch child process". And I really don't know anything about compiling.

---

### Post by nanotube on 2008-06-23
> **DrMilo said:**
> Firefox 2! If I install FF3 with your script it crashes. If I install it through the Hardy repos I get, "Failed to launch child process". And I really don't know anything about compiling.

hrm, so what exactly is currently installed on your system? ff3 from the repos is default. you also have ff2 from repos? you also have ff3 from mozilla? 

assuming your goal is to get ff3 from mozilla up and working, try the following:

remove anything installed by ubuntuzilla:
```
ubuntuzilla.py -a remove -p firefox
```

remove ff2 from repos version:
```
sudo apt-get remove firefox-2
```

move your profile out of the way:
```
mv ~/.mozilla /~.mozilla.backup
```

check that you have the latest ubuntuzilla (4.4.9):
```
ubuntuzilla.py --version
```
(if not, install the latest)

install ff3 with ubuntuzilla:
```
ubuntuzilla.py -a install -p firefox
```
and follow the prompts.

check which version of firefox is default:
```
firefox --version
```

check that the default link is proper:
```
ls -al /usr/bin/firefox
```
should show that it's a link to /opt/firefox/firefox

if the above is the case, and the version shows 3.0, then, try running  ff3:
```
firefox &
```

and see what comes up. :)

---

### Post by DrMilo on 2008-06-23
I did all that you said and I get a crash when I try to run 3!

Trying to remove ubuntuzilla stuff gets:

rm: cannot remove `/usr/bin/firefox': No such file or directory
sudo rm /usr/bin/firefox
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1082, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 209, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 238, in start
    self.remove()
  File "/usr/local/bin/ubuntuzilla.py", line 555, in remove
    self.removeLaunchLink()
  File "/usr/local/bin/ubuntuzilla.py", line 725, in removeLaunchLink
    self.util.execSystemCommand(executionstring="sudo rm /usr/bin/firefox")
  File "/usr/local/bin/ubuntuzilla.py", line 140, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfull

Removing FF2:

The following packages were automatically installed and are no longer required:
  libarts1c2a kdelibs4c2a kdelibs-data liblualib50 cryptsetup libkonq4 libavahi-gobject0
  libavahi-qt3-1 kfind libdbus-qt-1-1c2 liblua50 libruby1.8
Use 'apt-get autoremove' to remove them.

I didn't try to remove these.

Link gets:

lrwxrwxrwx 1 root root 20 2008-06-23 18:02 /usr/bin/firefox -> /opt/firefox/firefox

firefox & gets:

[1] 7991

Clicking the link got nothing the first time and the FF crash screen the 2nd.

---

### Post by nanotube on 2008-06-23
so the removal stalled at deleting the link... 

manually delete /opt/firefox directory:
```
sudo rm -rf /opt/firefox
```

run ubuntuzilla install again, make sure the .mozilla directory is out of the way, and try running firefox again.

to be sure, try running directly:
```
/opt/firefox/firefox
```

---

### Post by DrMilo on 2008-06-25
That did it! FF 3 up and running! Thank you very much!

---

### Post by nanotube on 2008-06-25
> **DrMilo said:**
> That did it! FF 3 up and running! Thank you very much!

awesome! :) enjoy :guitar:

---

