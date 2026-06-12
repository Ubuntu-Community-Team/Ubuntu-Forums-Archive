---
title: "[SOLVED] unable to remove seamonkey"
date: 2007-09-30
forum: Ubuntuzilla
---

### Post by mandrill on 2007-09-30
Don't know why, (probably wrong directory) but here is the text from uninstall attempt(s): 

rm: cannot remove `/usr/bin/seamonkey': No such file or directory
sudo rm /usr/bin/seamonkey
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1045, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 210, in start
    si.start()
  File "/usr/local/bin/ubuntuzilla.py", line 233, in start
    self.remove()
  File "/usr/local/bin/ubuntuzilla.py", line 527, in remove
    self.removeLaunchLink()
  File "/usr/local/bin/ubuntuzilla.py", line 925, in removeLaunchLink
    self.util.execSystemCommand(executionstring="sudo rm /usr/bin/seamonkey")
  File "/usr/local/bin/ubuntuzilla.py", line 140, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

The executable still fires up, and is located at  /usr/local/seamonkey...cannot remove manually, as trash option greyed out.

removal because of 1) inability to launch mail separately, 2) themes revert to default on every start of application. Have visited website, sent here, hoping it is as simple as changing the command to point to the actual location...

Thank you in advance for your help!

Oh, and does this help?

 jim@monkey:~$ cd
jim@monkey:~$ /usr/local/
bash: /usr/local/: is a directory
jim@monkey:~$ cd /usr/local
jim@monkey:/usr/local$ rm seamonkey
rm: cannot remove directory `seamonkey': Is a directory
jim@monkey:/usr/local$

---

### Post by aysiu on 2007-09-30
Try pasting this command into the terminal: ```
sudo rm -r /usr/local/seamonkey
``` Make sure you copy and paste the command instead of retyping it. Retyping it can be dangerous!

---

### Post by nanotube on 2007-09-30
since your seamonkey is located in /usr/local, and since ubuntuzilla installs in /opt by default, am i correct in guessing that you did /not/ use ubuntuzilla to /install/ seamonkey?

if that is the case, then... it's not surprising that your uninstall isn't working - ubuntuzilla uninstall is built to undo what the install has done. if you installed by some other means, then you get to uninstall by some other means, as well.

that may also explain why you are having problems with your seamonkey install in the first place - if you have not properly set some permissions or symlinks somewhere in the process of install.

if i'm wrong in my guess, then let me know, and we'll go from there. the command that aysiu posted will work to remove your seamonkey directory - but before uninstalling, i think it's a good idea to figure out what procedure you followed during your install.

---

### Post by mandrill on 2007-10-01
First of all - thank you both for your replies.

I was going to mention that I obviously had screwed up the installation - Ubuntuzilla was my third attempt - I realized it, but did not know exactly how to safely fix it.  My first attempts were with the native installer. Another learning experience! This is my 4th install of Ubuntu, and, at this point, really do not feel like doing it all again - too much time invested!

Gotta throw out the old thinking - most of it, anyway! I will post results of un-install - I think I knew what to do, but not quite how....

---

### Post by mandrill on 2007-10-01
Perfect.

Ran this, its gone...you can see that I did it the second time, because there was no dialogue, or any elepsed time, and the second result (plus manually looking) convinced me....

jim@monkey:~$ sudo rm -r /usr/local/seamonkey
Password:
jim@monkey:~$ sudo rm -r /usr/local/seamonkey
rm: cannot remove `/usr/local/seamonkey': No such file or directory
jim@monkey:~$ 

Thanks again. 

ps  Funny, but after 4 installs I am able to answer a lot of the questions in "Absolute Beginners" !  :)

---

### Post by nanotube on 2007-10-01
congrats! :)

---

### Post by MSchenker on 2007-12-19
I was about to post about the same problem, and noticed there is a discussion on this already!

I installed SeaMonkey using Ubuntuzilla, but I can't seem to uninstall it with the command given above by aysiu.

Here's the session:
```
matthew@Main:~$ sudo rm -r /usr/local/seamonkey
rm: cannot remove `/usr/local/seamonkey': No such file or directory
matthew@Main:~$

```Can anyone help me figure out what's going on here?

Thanks!

---

### Post by MSchenker on 2007-12-19
I just found SeaMonkey listed in the following two places:
/opt/seamonkey
/usr/bin/seamonkey

Question: If I want to uninstall SeaMonkey, would I do this...

```
sudo rm -r /opt/seamonkey
```Would this work, or am I misunderstanding how to use the remove command?

Thanks!

---

### Post by mandrill on 2007-12-19
sudo rm -r /opt/seamonkey should work if installed with ubuntuzilla install

---

### Post by MSchenker on 2007-12-19
mandrill,
Thanks, it worked!
Is it safe to manually delete the "/usr/bin/seamonkey" file. now that SeaMonkey is uninstalled?

---

### Post by mandrill on 2007-12-20
Yes, it is. I prefer to use "wipe" when deleting files/directories, but that is just a personal preference and not at all necessary. You may also do 'sudo apt-get autoremove' to rid yourself of unnecessary or uninstalled packages. For wipe, use 'sudo apt-get install wipe'. Once installed, do 'sudo wipe -r' for directories, or 'sudo wipe' for regular files. It will let you know.
To avoid more typing, just drag the offending item into the terminal after typing either command, hit enter, and confirm by typing "yes"

---

### Post by nanotube on 2007-12-20
actually... while the "manual" method of seamonkey uninstall works just fine, ubuntuzilla comes with a built-in uninstaller that automatically does all that rm -rf stuff.
just do
```
ubuntuzilla.py -p seamonkey -a remove
```
and it will take care of all the bits and pieces automatically. 

for future reference. :)

---

