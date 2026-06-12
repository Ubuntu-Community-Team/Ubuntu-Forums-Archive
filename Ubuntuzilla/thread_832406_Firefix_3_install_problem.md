---
title: "Firefix 3 install problem"
date: 2008-06-17
forum: Ubuntuzilla
---

### Post by gordonh on 2008-06-17
I typed ubuntuzilla.py -a install -p firefox and got the following results:

It fails at the "backing up preferences" step and doesn't continue.

Help please


gordon@gordon-laptop:~$ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.4.7

This script installs the latest release of the official Mozilla build of Firefox on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.0. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) for steps you can take to resolve this problem.]
  0. af           1. ar           2. be           3. ca        
  4. cs           5. da           6. de           7. el        
  8. en-GB        9. en-US       10. es-AR       11. es-ES     
 12. eu          13. fi          14. fr          15. fy-NL     
 16. ga-IE       17. gu-IN       18. he          19. hu        
 20. id          21. it          22. ja          23. ka        
 24. ko          25. ku          26. lt          27. mk        
 28. mn          29. nb-NO       30. nl          31. nn-NO     
 32. pa-IN       33. pl          34. pt-BR       35. pt-PT     
 36. ro          37. ru          38. si          39. sk        
 40. sl          41. sq          42. sr          43. sv-SE     
 44. tr          45. uk          46. zh-CN       47. zh-TW     

Enter your choice of localization (integer, from 0 to 47): 8
You have chosen localization en-GB. Is that correct [y/n]? 
Please enter 'y' or 'n': y
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-3.0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Backing up old Firefox preferences

cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/5C41C76Cd01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/EB58FD8Ad01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/C8E69405d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/DF21D914d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/1A209C9Bd01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/C8E69407d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/DF213814d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/4EA081E1d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/A1C26F2Ed01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/EE6651DDd01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/A938BBA1d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/DE97FA14d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/398D0618d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/748B2F5Dd01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/20387F23d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/96E6EF50d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/4D22BA00d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/46BC254Cd01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/2508F569d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/14AE7BF6d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/CF4012C5d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/C30646CEd01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/DBF40ECFd01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/54F0A0D5d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/34956179d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/C8E69406d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/C8E69404d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/FD6D180Dd01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/FF416A32d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/2D65017Fd01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/9AF52865d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/FFECF217d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/Cache/E2131153d01' for reading: Permission denied
cp: cannot open `/home/gordon/.mozilla/firefox/jw8613g5.default/cookies.txt' for reading: Permission denied
cp -R ~/.mozilla ~/.mozilla_backup_$(date -Iseconds)
Failed to back up profile.
Process returned code 1
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1060, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 209, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 236, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 519, in install
    self.backupProfile()
  File "/usr/local/bin/ubuntuzilla.py", line 663, in backupProfile
    self.util.execSystemCommand(executionstring="cp -R ~/.mozilla ~/.mozilla_backup_$(date -Iseconds)", errormessage="Failed to back up profile.")
  File "/usr/local/bin/ubuntuzilla.py", line 140, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by sp2edman on 2008-06-17
Hey, I'm not sure if it is the right one to fix the problem, yet have you tried to change the owner of the directories which cause the problem?

I guess the owner of the directory, /home/gordon/.mozilla/firefox/jw8613g5.default/Cache, and the sub-directories of it might be 'root'.

As I told you, I'm not sure about this so following my way is your own risk.

e.g.)

$ sudo chown -R your_username:your_user_group /home/gordon/.mozilla/firefox/jw8613g5.default/Cache

e.g.) If your username and user group are 'gordon'.
$ sudo chown -R gordon:gordon /home/gordon/.mozilla/firefox/jw8613g5.default/Cache


Regards,
Kevin

---

### Post by tiggsy on 2008-06-19
I got the "new version" notify yesterday quite late and I followed your instructions. I closed firefox, checked in system monitor and it was all closed. 

Went to terminal typed:
[FONT="Courier New"]
gksudo firefox &[/FONT]

The firefox that loaded didn't have "check for updates" greyed out like the one I normally use, so i clicked it. It came back and said there were no updates. I checked in about, it's 2.0.0.14

So then I went back to terminal and entered: 

[FONT="Courier New"]ubuntuzilla.py -a checkforupdatetext -p firefox[/FONT]

it came back and said 3.0 was available, and i could install by adding install to the command.

I typed:

[FONT="Courier New"]ubuntuzilla.py -a checkforupdatetext -p firefox -install [/FONT]

but it didn't work. So I read your page some more, and then ran the manual, tried

[FONT="Courier New"]ubuntuzilla.py -a checkforupdatetext -p firefox -a install[/FONT]

This seemed to work fine, but after it tried numerous mirrors multiple times, it didn't find firefox.tar.gz so it failed.

Today i got the notify again. I did the terminal "gksudo firefox &" again and again, the firefox update button came back with no new version.

What do i do now?

---

### Post by Slothie on 2008-06-19
I've got Ubuntu Dapper and kept getting these upgrade messages. If you're on Dapper then you've got to ignore it. If your on a more recent version then you could try removing it and re-installing it.
If you try installing it on Dapper, then it fails to find the install files when it tries to FTP it, because its looking for firefox-3.0.tar.gz and the file is actually firefox-3.0.tar.bz2.
I edited the ubuntuzilla script to change the tar.gz to tar.bz2 in the 2 places necessary, and the install worked. However, firefox wouldn't run because v3.0 needs gtk-2.10 and dapper comes with gtk 2.8 - and their appears to be no 2.10 available for dapper.
So now I'm back to 1.5 until I can work out how to get 2.0.0.14 back!
:confused:

---

### Post by thesios on 2008-06-19
> **Slothie said:**
> 
So now I'm back to 1.5 until I can work out how to get 2.0.0.14 back!
:confused:

When you type **ubuntuzilla.py -a install -p firefox**, one of the first prompts you get is asking if you want to install the latest version, or not.  Answer **n**.  It will then ask you what version you want, tell it **2.0.0.14**.  It will install the latest stable version that'll work with Dapper (2.0.0.14).

If you made the changes to ubuntuzill.py that were mention in another post, revert to the original or reinstall ubuntuzilla.

---

### Post by nanotube on 2008-06-20
Hi,
it looks like they changed the archive type for ff3, so ubuntuzilla was failing at installing it.
i have updated the code to take care of this, the latest release candidate is attached to this bug report thread on sourceforge:
[http://sourceforge.net/tracker/index.php?func=detail&aid=1996632&group_id=202789&atid=982990](http://sourceforge.net/tracker/index.php?func=detail&aid=1996632&group_id=202789&atid=982990)
please feel free to give it a try and let me know if it works as it should.
thanks for your feedback!

---

### Post by nanotube on 2008-07-08
just a quick update: ubuntuzilla is now updated to work just fine with ff3.

we are still working on getting ff3 to run on dapper, though, because ff3 requires a newer version of gtk than dapper's. keep an eye on this thread, if you are interested in running ff3 on dapper:
[http://ubuntuforums.org/showthread.php?t=847484](http://ubuntuforums.org/showthread.php?t=847484)

---

