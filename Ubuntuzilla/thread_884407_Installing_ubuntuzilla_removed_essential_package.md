---
title: "Installing ubuntuzilla removed essential package"
date: 2008-08-09
forum: Ubuntuzilla
---

### Post by williumbillium on 2008-08-09
I'm running ubuntu gutsy 64bit.

I installed ubuntuzilla and then firefox 3 a few days ago using the instructions here:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

Everything went fine.

Today I issued the command:

```
dmesg
```

and got

```
The program 'dmesg' is currently not installed.  You can install it by typing:
sudo apt-get install util-linux
bash: dmesg: command not found
```

Umm, that's not good.  I wondered if somehow my PATH had got messed up or something, but no, util-linux really isn't installed and /bin/dmesg does not exist.  The other programs it provides such as fdisk, mkfs etc are all missing from /bin too.

I checked my apt logs at /var/log/apt/term.log and here's the offending part:

```
Log started: 2008-08-05  23:07:43
(Reading database ... 132451 files and directories currently installed.)
Removing getlibs ...
Removing ubuntu-minimal ...
Removing util-linux-locales ...
dpkg - warning, overriding problem because --force enabled:
 This is an essential package - it should not be removed.
Removing util-linux ...
Selecting previously deselected package libnotify-bin.
(Reading database ... 132312 files and directories currently installed.)
Unpacking libnotify-bin (from .../libnotify-bin_0.4.4-3build1_amd64.deb) ...
Selecting previously deselected package linux32.
Unpacking linux32 (from .../linux32_1-3build1_amd64.deb) ...
Setting up libnotify-bin (0.4.4-3build1) ...
Setting up linux32 (1-3build1) ...
Log ended: 2008-08-05  23:07:46
```

I'm guessing this happened because I used GDebi to install ubuntuzilla-4.5.2-0ubuntu1-amd64.deb instead of the terminal.  (On a side note, I'm not sure what would be more worrysome, that GDebi informed me of what it was removing and I happily went along with it or that it didn't inform me at all...)

So back to the point.  What's the best way to go about dealing with this mess?  My system is surprisingly stable right now but I obviously need to sort this out.

The obvious thing to do is to follow the instructions for removing firefox and ubuntuzilla at [http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

So:

```
ubuntuzilla.py -a remove -p firefox
sudo apt-get remove --purge ubuntuzilla

```

Modify crontab:

```
crontab -e
```

Then reinstall util-linux (and the other removed packages) if apt doesn't automatically do it when I remove ubuntuzilla.

Does that seem like the best thing to do?

Also, when I've got back to where I started, I would like to reconsider installing ubuntuzilla.  So if anyone has any ideas of how to do so without being in this same situation, that would be appreciated.  Of course, this time I'll use the terminal so I can see what's going on...

Thanks.

---

### Post by williumbillium on 2008-08-09
This appears to have been solved with:

```
sudo apt-get install util-linux util-linux-locales ubuntu-minimal
```

All of the above were reinstalled and linux32 (which is provided by util-linux anyway) was removed.

I am unable to reinstall getlibs at this point, but that is less of an issue, hopefully.

---

### Post by nanotube on 2008-08-11
hi,
what exactly makes you think that it is the installation of ubuntuzilla that caused the uninstallation of all those packages? 

since nobody else has ever reported having this happen to them as a result of ubuntuzilla, i suspect that it was something else that did this. ...

---

### Post by williumbillium on 2008-08-16
> **nanotube said:**
> hi,
what exactly makes you think that it is the installation of ubuntuzilla that caused the uninstallation of all those packages? 

since nobody else has ever reported having this happen to them as a result of ubuntuzilla, i suspect that it was something else that did this. ...

Hi Nanotube,

Thanks for replying.

I came to that conclusion because, based on the timestamp in the apt logs I referenced in my original post and the timestamp of ubuntuzilla-4.5.2-0ubuntu1-amd64.deb that I downloaded, the package was removed 1 minute after the .deb was downloaded.  Of course, that doesn't guarantee it happened when I installed ubuntuzilla, but it seems quite likely.

Interestingly, when I issued:

```
sudo apt-get install util-linux util-linux-locales ubuntu-minimal

```

to resolve the problem, here's what is in my apt logs:

```
Log started: 2008-08-08  22:08:03
dpkg: linux32: dependency problems, but removing anyway as you request:
 ubuntuzilla depends on linux32; however:
  Package linux32 is to be removed.
  Package util-linux which provides linux32 is not installed.
(Reading database ... 132334 files and directories currently installed.)
Removing linux32 ...
Selecting previously deselected package util-linux.
(Reading database ... 132327 files and directories currently installed.)
Unpacking util-linux (from .../util-linux_2.13-8ubuntu1_amd64.deb) ...
Setting up util-linux (2.13-8ubuntu1) ...

Selecting previously deselected package util-linux-locales.
(Reading database ... 132459 files and directories currently installed.)
Unpacking util-linux-locales (from .../util-linux-locales_2.13-8ubuntu1_all.deb) ...
Selecting previously deselected package ubuntu-minimal.
Unpacking ubuntu-minimal (from .../ubuntu-minimal_1.79_amd64.deb) ...
Setting up util-linux-locales (2.13-8ubuntu1) ...

Setting up ubuntu-minimal (1.79) ...
Log ended: 2008-08-08  22:08:17
```

Note the 3rd line.  This makes me think that it was ubuntuzilla depending on linux32 that caused the installation of linux32 and the removal of util-linux.

It seems that this problem is partly a result of this bug which was fixed in hardy:

[https://bugs.launchpad.net/ubuntu/+source/linux32/+bug/141607](https://bugs.launchpad.net/ubuntu/+source/linux32/+bug/141607)

---

### Post by nanotube on 2008-08-17
aha, i see, in that case indeed it was due to ubuntuzilla's dependency on linux32. 

thanks for investigating further and pinpointing the bug. indeed, gutsy seems to be the only version of ubuntu that has both util-linux providing linux32, and also a separate and conflicting linux32 package. 

if you still wish to use ubuntuzilla, you can edit the .deb package to remove the linux32 dependency - then it will install and not give you any trouble. (in the .deb, inside control.tar.gz, edit the 'control' file)

---

### Post by williumbillium on 2008-08-17
I think that at this point the dependency has been satisfied with the util-linux package which is now installed again.  Issuing:

```
sudo apt-get check
```

Does not report any dependency problems.

Or do you think I may still run into problems in the future?

Thanks.

---

### Post by nanotube on 2008-08-17
> **williumbillium said:**
> I think that at this point the dependency has been satisfied with the util-linux package which is now installed again.  Issuing:

```
sudo apt-get check
```

Does not report any dependency problems.

Or do you think I may still run into problems in the future?

Thanks.

well, if everything is installed and working, should be ok
but turn off the ubuntuzilla automatic self-updates (otherwise, when/if a new ubuntuzilla version is released, it will install an upgrade of itself, and may (probably will) screw things up again because of the linux32 dependency... )
to turn off self-updates, remove file /etc/cron.d/ubuntuzillaupdatecron

---

### Post by williumbillium on 2008-08-17
> **nanotube said:**
> well, if everything is installed and working, should be ok
but turn off the ubuntuzilla automatic self-updates (otherwise, when/if a new ubuntuzilla version is released, it will install an upgrade of itself, and may (probably will) screw things up again because of the linux32 dependency... )
to turn off self-updates, remove file /etc/cron.d/ubuntuzillaupdatecron

I've done as you suggested.  Thanks for your help on this matter.

---

