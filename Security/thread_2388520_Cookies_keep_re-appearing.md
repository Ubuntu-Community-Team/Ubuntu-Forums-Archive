---
title: "Cookies keep re-appearing ?"
date: 2018-04-04
forum: Security
---

### Post by oygle on 2018-04-04
I use Firefox and regularly clear the web cache, and also have cookies set to be only kept until I close firefox. Don't allow 3rd party cookies.

The other day I ran a ```
locate cookies
``` and noticed 2 files called cookies.

/home/username/.local/share/kcookiejar/cookies
/home/username/.kde/share/apps/kcookiejar/cookies

Despite deleting these files, they keep on re-appearing. My concern is that there is Paypal and other site information within the (cookie) files. Where are these files sourced from, and how do I permantly delete them.

---

### Post by SeijiSensei on 2018-04-04
KDE stores passwords and such in its "[kwallet]("https://docs.kde.org/trunk5/en/kdeutils/kwallet5/index.html")" function. If you have not disabled the wallet, then some things will be stored there, but they should be encrypted if you chose a master password when activating the function.  

I browsed a bit for documentation on [kcookiejar]("https://www.google.com/search?q=kcookiejar"), and its not clear what function it performs.  The "cookies" file in .local/share on my machine just has a couple of Google cookies.  The file is in plain-text so you can see for yourself what it contains.  

I'm on 18.04 beta; there is no cookies file under .kde/share on my machine.

I imagine the cookies file is created anew by KDE if you delete it.  You could try making the file "[immutable]("http://www.aboutlinux.info/2005/11/make-your-files-immutable-which-even.html")," but I don't know the implications of such a change.

In general, most browser cookies rarely contain any sort of personal information.  I use them all the time when designing web sites to handle authorization and to keep track of logged-in users.  The cookies I use simply identify someone as authorized and contain no security information.  That's pretty much the standard for "session cookies."

---

### Post by oygle on 2018-04-05
> **SeijiSensei said:**
> KDE stores passwords and such in its "[kwallet]("https://docs.kde.org/trunk5/en/kdeutils/kwallet5/index.html")" function. If you have not disabled the wallet, then some things will be stored there, but they should be encrypted if you chose a master password when activating the function. 

I searched for 'wallet' on the plasma desktop and there were 2 tools there:

KWalletManager - runs Kwalletmanager5
KDE Wallet  - runs  kcmshell5

I do use KeePassx which I thought was linked to KWallet, but it doesn't appear to be. Checked package dependecies for kwalletmanager

```
$ apt-cache rdepends kwalletmanager
```

> 
kwalletmanager
Reverse Depends:
  geary
  smb4k
  libqt5keychain0
  kwalletcli
  kubuntu-full
  kubuntu-desktop
  ksshaskpass

```
$ apt-cache depends kwalletmanager
```

> kwalletmanager
  Depends: libc6
  Depends: libkf5archive5
  Depends: libkf5auth5
  Depends: libkf5codecs5
  Depends: libkf5configcore5
  Depends: libkf5configwidgets5
  Depends: libkf5coreaddons5
  Depends: libkf5dbusaddons5
  Depends: libkf5i18n5
  Depends: libkf5iconthemes5
  Depends: libkf5itemviews5
  Depends: libkf5kdelibs4support5
  Depends: libkf5notifications5
  Depends: libkf5service-bin
  Depends: libkf5service5
  Depends: libkf5textwidgets5
  Depends: libkf5wallet-bin
  Depends: libkf5wallet5
  Depends: libkf5widgetsaddons5
  Depends: libkf5xmlgui5
  Depends: libqt5core5a
  Depends: libqt5dbus5
 |Depends: libqt5gui5
  Depends: libqt5gui5-gles
  Depends: libqt5widgets5
  Depends: libqt5xml5
  Depends: libstdc++6

> **SeijiSensei said:**
> I browsed a bit for documentation on [kcookiejar]("https://www.google.com/search?q=kcookiejar"), and its not clear what function it performs.  The "cookies" file in .local/share on my machine just has a couple of Google cookies.  The file is in plain-text so you can see for yourself what it contains.

I couldn't find out what creates/updates that file. Yes, just plain text, and whenever I deleted it, some app kept re-creating it. So I modified it to remove all the actual info and now it looks like this

> # KDE Cookie File v2
#
# Host               Domain               Path         Exp.date   Prot Name                 Sec  Value


and since I have done that, it hasn't been modified. I guess I could go a step further and find out what was actually modifying the file. Probably a monitor like - [https://askubuntu.com/questions/819265/bash-script-to-monitor-file-change-and-execute-command](https://askubuntu.com/questions/819265/bash-script-to-monitor-file-change-and-execute-command)

> **SeijiSensei said:**
> I'm on 18.04 beta; there is no cookies file under .kde/share on my machine.

Okay thanks. I'm on 16.04.4

Thanks for that link on making the file immutable and the info in regards to what is usually contained within a cookie file. I probably tend to want to take extra safeguards as some websites don't respect browser settings and read other sites cookies.

---

### Post by SeijiSensei on 2018-04-05
Another option might be to replace the file with a symbolic link to /dev/null:

```

cd .local/share/kcookiejar/
rm -f cookies
ln -s /dev/null cookies

```

I don't know if KDE will handle that correctly, but it might be a better option than marking the file immutable.

---

### Post by TheFu on 2018-04-07
Another option is to run the browser in a jail that cannot write to the disk.

```
$ firejail --private firefox
```
this will provide a temporary, empty, file system overlay that it remove when firefox is closed.  It is an external sandbox based on cgroup limitations, like Linux containers use.  Firejail has some options and each program can have a different  profile to control what is allowed or not.

---

### Post by SeijiSensei on 2018-04-07
I don't think the cookies stored by kcookiejar have anything to do with Firefox.  I still only have two stale Google cookies in my cookies file despite using Firefox many, many times over the course of the day.

This is pretty clearly a KDE thing.  I just don't know which KDE apps store cookies in that file.

---

### Post by TheFu on 2018-04-07
Ah ...  what good are cookies that aren't used for web access?  

**chattr +i** on empty files?  That should stop it. ;)  If the app trying to write to the files dies, then we'd know.\
or use **setfacl** to remove write for the userids involved.

---

