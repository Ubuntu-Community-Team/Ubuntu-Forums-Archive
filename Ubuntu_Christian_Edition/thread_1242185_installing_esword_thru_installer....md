---
title: "installing esword thru installer..."
date: 2009-08-16
forum: Ubuntu Christian Edition
---

### Post by stlsaint on 2009-08-16
hey i just tried installing esword on a new install but i keep erroring out!! what am i missing!! i feel stupid since i installed it on my own system just fine!

---

### Post by david_kt on 2009-08-17
> **stlsaint said:**
> hey i just tried installing esword on a new install but i keep erroring out!! what am i missing!! i feel stupid since i installed it on my own system just fine!

What is the error?

DK

---

### Post by stlsaint on 2009-08-17
could not load wine-gecko. HTML rendering will be disabled: etc etc
wine: configuration in '/home/user/.wine_Esword' has been updated etc etc
wine: could not load L"Z://\\home\\user\\.wineeswordchache, etc etc
"ESword_installer error: NOTE: command 'env WINEPREFIX=/home/user/.wine_Esword wine /home/user/.wineeswordcache/seti[903.exe' returned status 193 Aborting"

it looks like something simple like making a dir somewhere i just dont wanna go touching stuff and making things worse!! i have the setup903.exe from the site should i be using that instead?

---

### Post by david_kt on 2009-08-17
> **stlsaint said:**
> 
"ESword_installer error: NOTE: command 'env WINEPREFIX=/home/user/.wine_Esword wine /home/user/.wineeswordcache/seti[903.exe' returned status 193 Aborting"

You could try to copy your setup903.exe to /home/user/.wineeswordcache/
and then relaunch the e-sword-installer.

DK

---

### Post by stlsaint on 2009-08-17
ok..i replaced the setup.exe that was in there with the one i downloaded off the website and the tried to re-install thru installer but now it says that something about sha1 sum mismatch...im assuming thats because what you originally had in the .winescached folder doesnt match with what i put in there...so i was able to install but cant use...it said something about renaming a folder inside winescache folder but there is no folder there?

---

### Post by stlsaint on 2009-08-17
am i supposed to have wine tricks installed when i install esword?

---

### Post by stlsaint on 2009-08-17
> **stlsaint said:**
> ok..i replaced the setup.exe that was in there with the one i downloaded off the website and the tried to re-install thru installer but now it says that something about sha1 sum mismatch...im assuming thats because what you originally had in the .winescached folder doesnt match with what i put in there...so i was able to install but cant use...it said something about renaming a folder inside winescache folder but there is no folder there?


correction...its not a folder!! its telling me to rename the InstMsiA.exe...how am i suppose to do that?

---

### Post by david_kt on 2009-08-17
> **stlsaint said:**
> correction...its not a folder!! its telling me to rename the InstMsiA.exe...how am i suppose to do that?

May be just try "clear_cache" option, and then try installing it again.

DK

---

### Post by stlsaint on 2009-08-17
clear as in delete files in folder or delete cache folder(winecache)

---

### Post by david_kt on 2009-08-17
> **stlsaint said:**
> clear as in delete files in folder or delete cache folder(winecache)
Yes, use the installer, it has that option.
DK

---

### Post by stlsaint on 2009-08-17
> **david_kt said:**
> Yes, use the installer, it has that option.
DK

tried it and still nothing...still says "sha1sum mismatch"...rename InstMsiA.exe then try again"

---

### Post by david_kt on 2009-08-17
> **stlsaint said:**
> tried it and still nothing...still says "sha1sum mismatch"...rename InstMsiA.exe then try again"

Can you post the output of:

```
 cat /etc/dansguardian/lists/bannedextensionlist | grep exe
```

DK

---

### Post by stlsaint on 2009-08-17
> **david_kt said:**
> Can you post the output of:

```
 cat /etc/dansguardian/lists/bannedextensionlist | grep exe
```

DK


janel@janel-laptop:~$ cat /etc/dansguardian/lists/bannedextensionlist | grep exe# File extensions with executable code 
# The following file extensions can contain executable code.
.exe  # Program
# Files which one normally things as non-executable but
# Other files which may contain files with executable code
janel@janel-laptop:~$

---

### Post by stlsaint on 2009-08-17
> **david_kt said:**
> Can you post the output of:

```
 cat /etc/dansguardian/lists/bannedextensionlist | grep exe
```

DK


think i messed the last post up...

janel@janel-laptop:~$ cat /etc/dansguardian/lists/bannedextensionlist | grep exe
# File extensions with executable code 
# The following file extensions can contain executable code.
.exe  # Program
# Files which one normally things as non-executable but
# Other files which may contain files with executable code
janel@janel-laptop:~$

---

### Post by david_kt on 2009-08-17
> **stlsaint said:**
> think i messed the last post up...

janel@janel-laptop:~$ cat /etc/dansguardian/lists/bannedextensionlist | grep exe
# File extensions with executable code 
# The following file extensions can contain executable code.
.exe  # Program
# Files which one normally things as non-executable but
# Other files which may contain files with executable code
janel@janel-laptop:~$

Could you launch the dansguardian-gui, and select autoconfigure. After that, try again 
```
cat /etc/dansguardian/lists/bannedextensionlist | grep exe
``` 

and post the output.

DK

---

### Post by stlsaint on 2009-08-17
> **david_kt said:**
> Could you launch the dansguardian-gui, and select autoconfigure. After that, try again 
```
cat /etc/dansguardian/lists/bannedextensionlist | grep exe
``` 

and post the output.

DK


I think something was wrong with dansG...i tried the autoconfig and i got this!! and i tried that cat cmd and it gave me the same thing as before!!

mkdir: cannot create directory `/home/janel/.cache': File exists
grep: /usr/lib/firefox-3.0.13/firefox.cfg: No such file or directory
 * Stopping DansGuardian dansguardian                                    [ OK ] 
 * Stopping Firewall firehol                                                    

WARNING
File '/etc/firehol/RESERVED_IPS' is more than 90 days old.
You should update it to ensure proper operation of your firewall.

Run the supplied get-iana script to generate this file.

                                                                         [ OK ]
Stopping tinyproxy: tinyproxy.
Starting tinyproxy: tinyproxy.
 * Starting Firewall firehol                                                    

WARNING
File '/etc/firehol/RESERVED_IPS' is more than 90 days old.
You should update it to ensure proper operation of your firewall.

Run the supplied get-iana script to generate this file.

                                                                         [ OK ]
 * Starting DansGuardian dansguardian                                    [ OK ] 
grep: /usr/lib/firefox-3.0.13/firefox.cfg: No such file or directory

---

### Post by david_kt on 2009-08-17
> **stlsaint said:**
> 
 * Stopping Firewall firehol                                                    

WARNING
File '/etc/firehol/RESERVED_IPS' is more than 90 days old.
You should update it to ensure proper operation of your firewall.

Run the supplied get-iana script to generate this file.

                                                                         [ OK ]
Stopping tinyproxy: tinyproxy.
Starting tinyproxy: tinyproxy.
 * Starting Firewall firehol                                                    



Your dansguardian gui is old version (1.X). Please do as follow:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Make sure dansguardian-gui is updated to version 2.2.
After that you could remove firehol:
```
sudo apt-get remove --purge firehol
```

Then run dansguardian-gui and choose autoconfiguration and again  cat /etc/dansguardian/lists/bannedextensionlist | grep exe 


DK

---

### Post by stlsaint on 2009-08-18
> **david_kt said:**
> Your dansguardian gui is old version (1.X). Please do as follow:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Make sure dansguardian-gui is updated to version 2.2.
After that you could remove firehol:
```
sudo apt-get remove --purge firehol
```

Then run dansguardian-gui and choose autoconfiguration and again  cat /etc/dansguardian/lists/bannedextensionlist | grep exe 


DK

upon doing sudo apt-get remove --purge firehol....dansG gui is now gone!

---

### Post by david_kt on 2009-08-18
> **stlsaint said:**
> upon doing sudo apt-get remove --purge firehol....dansG gui is now gone!

That means you do not have the (correct/new) ubuntu ce repository. Please add it according to your architecture (32 bit or 64 bit):

[http://ubuntuce.com/convert.htm](http://ubuntuce.com/convert.htm)

DK

---

### Post by stlsaint on 2009-08-18
should i do a fresh install and then update/upgrade then try all this again cuz even after the repo update i still get the same errors on everything!!

---

### Post by david_kt on 2009-08-18
> **stlsaint said:**
> should i do a fresh install and then update/upgrade then try all this again cuz even after the repo update i still get the same errors on everything!!

No, it would be the same. Now whatis the output of:

```
cat /etc/dansguardian/lists/bannedextensionlist | grep exe
```

?

DK

---

### Post by david_kt on 2009-08-18
The easy way is to stop dansguardian using dansguardian gui and then install e-sword. But Actually I have make some changes so that the dansguardian is not blocking e-Sword installer anymore.

DK

---

### Post by stlsaint on 2009-08-18
> **david_kt said:**
> No, it would be the same. Now whatis the output of:

```
cat /etc/dansguardian/lists/bannedextensionlist | grep exe
```

?

DK


janel@janel-laptop:~$ cat /etc/dansguardian/lists/bannedextensionlist | grep exe# File extensions with executable code 
# The following file extensions can contain executable code.
#.exe  # Program
# Files which one normally things as non-executable but
# Other files which may contain files with executable code
janel@janel-laptop:~$

---

### Post by david_kt on 2009-08-18
> **stlsaint said:**
> janel@janel-laptop:~$ cat /etc/dansguardian/lists/bannedextensionlist | grep exe# File extensions with executable code 
# The following file extensions can contain executable code.
#.exe  # Program
# Files which one normally things as non-executable but
# Other files which may contain files with executable code
janel@janel-laptop:~$

With this setting, e-Sword should be installed easily. But you have to clear_cache first before installing e-Sword.

DK

---

### Post by stlsaint on 2009-08-19
how do i clear cache?

---

### Post by david_kt on 2009-08-19
> **stlsaint said:**
> how do i clear cache?

Launch the e-Sword installer, and choose "clear_cache" option.

DK

---

### Post by stlsaint on 2009-08-19
DK THAT WAS IT!!! cleared like you said and esword did some updating an installed flawlessly thanks for you patience and dedication!!!

---

