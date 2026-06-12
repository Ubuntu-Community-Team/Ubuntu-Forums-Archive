---
title: "More improvements on dansguardian gui"
date: 2009-12-05
forum: Ubuntu Christian Edition
---

### Post by david_kt on 2009-12-05
I have just made some improvements on the dansguardian gui for Ubuntu CE version 6.0:

  * Prevent non sudoer to launch menu
  * Use gksu instead of sudo
  * Remove terminal
  * Improve user interface

Please help to test and feedback your opinion. To test it, do as follow:

```
sudo apt-get update
sudo apt-get upgrade
```

DK

---

### Post by squareff255 on 2009-12-18
Is there anywhere I can get this particular version of Dansguardian WITHOUT having to conver to CE?

---

### Post by david_kt on 2009-12-18
> **squareff255 said:**
> Is there anywhere I can get this particular version of Dansguardian WITHOUT having to conver to CE?

Follow the instruction on below link:

[http://ubuntuce.com/convert.htm](http://ubuntuce.com/convert.htm)

But change 

```
sudo apt-get install ubuntu-ce 
```

to 

```
sudo apt-get install dansguardian-gui
```

DK

---

### Post by squareff255 on 2009-12-18
Wow. Thanks for the quick reply. I'm checkin' to see if it all worked. :)

---

### Post by marius_brkt on 2010-05-02
Does it works for ubuntu 10.04?
I've install it, but when I want  to open a page, dansguardian block the internet connexion...I have to stop dansguardian and all goes fine after that...

any ideea?

PS on another machine with 9.10 all works fine..

---

### Post by david_kt on 2010-05-02
> **marius_brkt said:**
> Does it works for ubuntu 10.04?
I've install it, but when I want  to open a page, dansguardian block the internet connexion...I have to stop dansguardian and all goes fine after that...

any ideea?

PS on another machine with 9.10 all works fine..

It might be problem with tinyproxy compatibility. I have not check it myself.

DK

---

### Post by marius_brkt on 2010-05-03
I forgott to say that 10.04 is on 64 architecture..and 9.10 is 32
Dansguardian GUI was installed by "sudo apt-get insatll dansguardian-gui"...not the comand for karmic 64...
can u help me?
thks

---

### Post by david_kt on 2010-05-03
> **marius_brkt said:**
> I forgott to say that 10.04 is on 64 architecture..and 9.10 is 32
Dansguardian GUI was installed by "sudo apt-get insatll dansguardian-gui"...not the comand for karmic 64...
can u help me?
thks

That would be the same. I think the problem is with the new tinyproxy. You could try to use other proxy.

DK

---

### Post by nysnsweet on 2011-07-13
I did the switch in the command sudo apt-get install dansguardian-gui as instructed above, but I get a return in the terminal that says: 

[HTML]stephen@ubuntu:~$ wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa asc -O | sudo apt-key add - && sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/karmic_i386 list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install dansguardian-gui
wget: option requires an argument -- 'O'
gpg: no valid OpenPGP data found.
Ign http://us.archive.ubuntu.com natty InRelease
Ign http://security.ubuntu.com natty-security InRelease
Ign http://us.archive.ubuntu.com natty-updates InRelease
Hit http://security.ubuntu.com natty-security Release.gpg
Hit http://us.archive.ubuntu.com natty Release.gpg
Hit http://security.ubuntu.com natty-security Release
Hit http://us.archive.ubuntu.com natty-updates Release.gpg
Hit http://us.archive.ubuntu.com natty Release  
Hit http://security.ubuntu.com natty-security/main Sources            
Hit http://us.archive.ubuntu.com natty-updates Release                
Hit http://security.ubuntu.com natty-security/restricted Sources
Hit http://security.ubuntu.com natty-security/universe Sources
Hit http://security.ubuntu.com natty-security/multiverse Sources
Hit http://security.ubuntu.com natty-security/main i386 Packages
Hit http://security.ubuntu.com natty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty/main Sources
Hit http://us.archive.ubuntu.com natty/restricted Sources
Hit http://us.archive.ubuntu.com natty/universe Sources
Hit http://us.archive.ubuntu.com natty/multiverse Sources
Hit http://us.archive.ubuntu.com natty/main i386 Packages
Hit http://security.ubuntu.com natty-security/universe i386 Packages
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages
Ign http://security.ubuntu.com natty-security/main TranslationIndex
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Ign http://security.ubuntu.com natty-security/universe TranslationIndex
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty/universe i386 Packages
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty/main TranslationIndex
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex
Hit http://us.archive.ubuntu.com natty-updates/main Sources
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources
Hit http://us.archive.ubuntu.com natty-updates/universe Sources
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex
Ign http://security.ubuntu.com natty-security/main Translation-en_US
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://security.ubuntu.com natty-security/universe Translation-en
Ign http://us.archive.ubuntu.com natty/main Translation-en_US
Ign http://us.archive.ubuntu.com natty/main Translation-en
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty/universe Translation-en
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dansguardian-gui[/HTML]

What should I do?  I would like the dansguardian-gui from ubuntuCE to be installed into ubuntustudio 11.04.  please help. Thanks

---

### Post by newb85 on 2011-08-15
nysnsweet,

It looks like you didn't copy that line carefully enough.  You need to use "-O-", not just "-O" on the first wget statement.  Copying & pasting would be more reliable.

---

### Post by newb85 on 2011-08-15
I have to agree with nysnsweet that it would be nice to run the GUI on 11.04.  But I would like to have an idea of the potential for compatibility issues, since the UbuntuCE repository is a Karmic repository.  Should this be a concern, or am I worried about nothing?

---

### Post by papageorgiou on 2011-09-05
[SIZE=2]I did the following and got Dansguardian with a GUI running in Edubuntu 11.04.
[/SIZE][INDENT][SIZE=2]1. [/SIZE]```
wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc -O- | sudo apt-key add -  
```[/INDENT][INDENT][SIZE=2]2. [/SIZE]```
sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/lucid_amd.list -O- /etc/apt/sources.list.d/ubuntuce.list;
```[SIZE=2]

This failed for me.  I assume there is a typo. 
I completed the following steps to get the right repo added by doing the following:[/SIZE][INDENT][SIZE=2]a. **System** -> **Administration** -> **Update Manager**
b. Select **Settings** button
c. Go to **Other Software** tab
d. Click **Add...** button
e. Paste the following for the **APT line: **
[/SIZE]```
deb http://ubuntuce.com/repos/Ubuntu_CE/ lucid_amd/
```[SIZE=2]
[/SIZE][FONT=Arial][SIZE=2]f. Click **Add Source** button[/SIZE][/FONT]
[FONT=Arial][SIZE=2]g. If a source exists for **[http://ubuntuce.com/repos/Ubuntu_CE/lucid_amd/](http://ubuntuce.com/repos/Ubuntu_CE/lucid_amd/) (Source Code)**, un-check the box for the repo.[/SIZE][/FONT] You only want the binary repo.
[/INDENT][/INDENT][INDENT]3. ```
sudo apt-get update && sudo apt-get install dansguardian-gui

```4. Go to [SIZE=2]**System** -> **Administration** -> **Configure Parental Controls** to access the Dansguardian GUI.

Steps I performed to get Dansguardian functioning was the following:
1. Click **Autoconfigure/Reset Dansguardian and Tinyproxy.**
2. **Filter setting** - Select the setting to your liking.
3. **Start Dansguardian** - this did not start Dansguardian
4. **Lock Firefox Proxy**
5. Click **OK** button then reboot computer
6. Dansguardian is working.(Well, it's working for me.)

I hope this helps.
[/SIZE][/INDENT]

---

### Post by papageorgiou on 2011-09-05
If granular customization is needed, the Dansguardian lists can be found in the following location: **/etc/dansguardian/lists**

The filenames in **bold** are probably the ones you want to focus on.[INDENT]**bannedextensionlist**
bannediplist
**bannedmimetypelist**
bannedphraselist
bannedregexpheaderlist
bannedregexpurllist
**bannedsitelist**
bannedurllist
contentregexplist
**exceptionextensionlist**
exceptionfilesitelist
exceptionfileurllist
exceptioniplist
**exceptionmimetypelist**
exceptionphraselist
exceptionregexpurllist
**exceptionsitelist**
exceptionurllist
filtergroupslist
greysitelist
greyurllist
headerregexplist
logregexpurllist
logsitelist
logurllist
pics
urlregexplist
weightedphraselist
[/INDENT]

---

