---
title: "[SOLVED] Do you use Eclipse under Xubuntu ? I have shotcuts problem"
date: 2008-12-16
forum: Ubuntu Dev Link Forum
---

### Post by RomanIvanov on 2008-12-16
Hi, all.

I make my transition from Windows XP to Xubuntu 8.10. As a newbie i cope with number of problems to port all my work to Xubuntu. But there is one that drive me crazy and block me from forget about Windows.

I have to work in Eclipse, it is my job. But There is a frustrating issue with Xubuntu. I can't use half of Eclipse shortcuts - Ctrl+F6(shift Editors), Alt+Shift+R(Refactoring/Rename), Inspect window in debug is not sizable !! , ... .

**Does anybody cope with unblock all shortcuts in Eclipse? workaround ?**

This issue is not reproduced in Ubuntu, it seems to be problem of Xubuntu only. But I really like this Xubuntu for its lightweight UI.

Thanks in advance.

---

### Post by RomanIvanov on 2008-12-18
Ctrl+F6 - is workspace shifting 
Solved: Applications -> Settings -> Settings Manager -> Windows Manager -> tab "Keyboard"

Problem with other shortcuts could be solved by changing layout switch <Alt>+<Shift> to CapsLock. Does any body know how to do it ?

---

### Post by RomanIvanov on 2008-12-18
I found the solution:

```
sudo mousepad /etc/default/console-setup
```

and put this instead of existent:

```
XKBMODEL="pc105"
XKBLAYOUT="us,ru"
XKBVARIANT=",winkeys"
XKBOPTIONS="grp:switch,grp:caps_toggle,grp_led:scroll"

```
Do not forget to restart PC after change. (restarting of X(Ctl+Alt+BackSpace) DOES NOT WORK for this).

XKBLAYOUT="us,ru" - my second language is Russian (ru).

XKBVARIANT=",winkeys" - just set layout - for (ru) I put "winkeys"

this configuration make me switch layout by CapsLock (grp:caps_toggle,grp_led:scroll), and temporarily switch while pressing Alt (grp:switch).

---

### Post by RomanIvanov on 2008-12-18
In 9.04 it will be possible to do by UI - [https://bugs.launchpad.net/ubuntu/+source/xfce4-xkb-plugin/+bug/290255](https://bugs.launchpad.net/ubuntu/+source/xfce4-xkb-plugin/+bug/290255)

---

### Post by Markor on 2008-12-28
>> Firstly install debian-reference package. I found that solution there.
>> (file:///usr/share/doc/Debian/reference/ch-package.en.html#s-port)
>>  sudo apt-get build-dep xfce4-xkb-plugin
>> Go to [http://packages.ubunutu.com](http://packages.ubunutu.com)
>> search for package we want (xfce4-xkb-plugin)
>> and select Distribution: Any to see all releases versions for package.
>> Make some dir and We download *.dsc , *.orig.tar.gz and *.diff.gz
>> dpkg-source -x *.dsc
>> ls
>> cd new_directory
>> dpkg-buildpackage -rfakeroot -us -uc
>> cd ..
>> ls *.deb
>> sudo dpkg -i *.deb
>> and we got nice *.deb package we wanted for our Ubuntu we are using.

Just to post a way of porting newer package to stable Ubuntu release.
:)

---

### Post by alSee on 2009-01-02
Thanks, guys. It works!

---

### Post by FrenchyFungus on 2009-03-29
> **RomanIvanov said:**
> I found the solution:

```
sudo mousepad /etc/default/console-setup
```

and put this instead of existent:

```
XKBMODEL="pc105"
XKBLAYOUT="us,ru"
XKBVARIANT=",winkeys"
XKBOPTIONS="grp:switch,grp:caps_toggle,grp_led:scroll"

```
Do not forget to restart PC after change. (restarting of X(Ctl+Alt+BackSpace) DOES NOT WORK for this).

XKBLAYOUT="us,ru" - my second language is Russian (ru).

XKBVARIANT=",winkeys" - just set layout - for (ru) I put "winkeys"

this configuration make me switch layout by CapsLock (grp:caps_toggle,grp_led:scroll), and temporarily switch while pressing Alt (grp:switch).
Thanks for this.

You missed the "Alt" part of the temporary switch command though. It should read:
```
XKBOPTIONS="grp:alt_switch,grp:caps_toggle,grp_led:scroll"

```
:)

---

