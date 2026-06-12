---
title: "Raring getting an error Updating software catalog Bug # 1159023"
date: 2013-04-04
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2013-04-04
If you are getting this error as I have been for the past couple of days during updates you might want to sign your name to this bug.

```
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/workrave:workrave.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser-layer.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
Software catalog update was successful.
```

Bug: [https://bugs.launchpad.net/ubuntu/+source/workrave/+bug/1159023](https://bugs.launchpad.net/ubuntu/+source/workrave/+bug/1159023)

---

### Post by kevpan815 on 2013-04-05
I was having the same problem as you Pre-Final-Beta. I will try it out again tomorrow and see if the issue is fixed or not.

---

### Post by kevpan815 on 2013-04-05
Forgot to mention that I used sudo apt-get update and sudo apt-get upgrade instead of what you used in your Bug Report.

---

### Post by kevpan815 on 2013-04-05
Sorry Cavsfan, but the issue did NOT reproduce itself after Updating Beta 2. Will try again tomorrow.

---

### Post by kevpan815 on 2013-04-05
P.S. By the way, 1 Package was Held Back, even with Ubuntu hitting Beta, so you might NOT want to be trying a sudo apt-get dist-upgrade just yet.

---

### Post by Cavsfan on 2013-04-05
kevpan815,
I _always_ use sudo apt-get update and sudo apt-get upgrade and sudo apt-get dist-upgrade.

Someone in this forum I forget who told me to put the commands into .bashrc which makes it a lot simpler than typing those commands.
Also, these commands are much better than using update manager because you avoid "partial updates".

In /home/cavsfan/.bashrc I have added the blue lines below after the other lines in the file:

```
# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

[COLOR=#0000ff]# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade'[/COLOR]
```

You have to logout and back in for them to work.
Now all I do is enter **ud** and my password and it checks for updates.

If anything is held back I enter **ud2** and if whatever is held back will be installed if it is ready, if not it will just say it is still held back.

This is how I get my kernels with the **ud2** alias as several of the kernel packages are always held back.
It works with some other updates when a new package needs to be installed along with updating some existing packages.

I only get the error when I see this in the terminal:

Updating software catalog...this may take a moment.

I just got a bunch of updates and didn't get that error because the software catalog did not require updating.
Here is when I installed Raring:

```
cavsfan@cavsfan-MS-7529:~$ ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
Mar 3 09:58
```

---

### Post by kevpan815 on 2013-04-05
Sorry Cavsfan, but I thought that doing a sudo apt-get dist-upgrade would actually force a Partial Upgrade based on what I have read here before. If I am wrong about that then I apologize.

---

### Post by Cavsfan on 2013-04-05
> **kevpan815 said:**
> Sorry Cavsfan, but I thought that doing a sudo apt-get dist-upgrade would actually force a Partial Upgrade based on what I have read here before. If I am wrong about that then I apologize.

No apology necessary! :D A friend on here Ranch Hand always called Update Manager Update Mangler and told me to always use the CLI commands.

You can't go wrong and you will not get a partial upgrade with them either. 

One thing about Ubuntu or Linux is that if you aren't learning something you aren't doing anything.

My error (the bug) could very well be caused by using an older install but, I am not going to re-install because the Raring final release is April 25th.
But, I still recommend anyone getting that error report it on that bug.

I will do a clean install after April 25th myself.

---

### Post by Cavsfan on 2013-04-11
Any one still getting this error when the software catalog is updated? 

It happens any time I see this: "Updating software catalog...this may take a moment."

I just updated and got the error:

```
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/workrave:workrave.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser-layer.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
Software catalog update was successful.

```

---

### Post by mc4man on 2013-04-11
Not an error, just proper warnings 
(workrave needs some help as the .desktop created has 2 improper Comments, the sonic warnings are also justified as the 2 mentioned .desktops are improper & likely not even needed.

---

### Post by Cavsfan on 2013-04-12
> **mc4man said:**
> Not an error, just proper warnings 
(workrave needs some help as the .desktop created has 2 improper Comments, the sonic warnings are also justified as the 2 mentioned .desktops are improper & likely not even needed.

You are absolutely right they are just warnings. I am not as observant as I should be!
The bug just lists warnings too. I just posted this as it says at the end of the warning "Please consider raising a bug report for this issue with the maintainer of that application."

There are now 23 people listed on that bug as being affected.

---

### Post by mc4man on 2013-04-12
The 'warnings' are useful as they can point to other issues (outside of app producing, in this case S-C

The one about workrave sheds light on that when built 2 Comments in the actual installed workrave.desktop are translated into multi-line Comments which is improper & causes workrave not to show in the Dash, ect.
(the .desktop in /usr/share/app-install/desktop also contains a multi-line Comment which is the cause of the warning (- that's the Comment that would show in S-C 

The 2 about sonic-visualiser* are a bit more curious,  those 2 .desktops being installed into /usr/share/applications where they don't belong.
(if anything they should go into /usr/share/mimelnk/application or be gotten ride of entirely as their purpose seems uneffectual
So I'd gather those 2 .desktops shouldn't be in  /usr/share/app-install/desktop, they can be removed

---

### Post by Cavsfan on 2013-04-13
> **mc4man said:**
> The 'warnings' are useful as they can point to other issues (outside of app producing, in this case S-C

The one about workrave sheds light on that when built 2 Comments in the actual installed workrave.desktop are translated into multi-line Comments which is improper & causes workrave not to show in the Dash, ect.
(the .desktop in /usr/share/app-install/desktop also contains a multi-line Comment which is the cause of the warning (- that's the Comment that would show in S-C 

The 2 about sonic-visualiser* are a bit more curious,  those 2 .desktops being installed into /usr/share/applications where they don't belong.
(if anything they should go into /usr/share/mimelnk/application or be gotten ride of entirely as their purpose seems uneffectual
So I'd gather those 2 .desktops shouldn't be in  /usr/share/app-install/desktop, they can be removed

I moved ```
/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser.desktop
``` and ```
/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser-layer.desktop
``` to a temp directory.

I noticed this file exists although I never installed workrave - /usr/share/app-install/desktop/workrave:workrave.desktop.
Didn't even know what workrave was until now.

In SPM, workrave shows as installable but, not installed which makes it weird that I am even getting that error.

I should be able to remove /usr/share/app-install/desktop/workrave:workrave.desktop as well then right?

---

### Post by mc4man on 2013-04-13
> **Cavsfan said:**
> I moved ```
/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser.desktop
``` and ```
/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser-layer.desktop
``` to a temp directory.

I noticed this file exists although I never installed workrave - /usr/share/app-install/desktop/workrave:workrave.desktop.
Didn't even know what workrave was until now.

In SPM, workrave shows as installable but, not installed which makes it weird that I am even getting that error.

I should be able to remove /usr/share/app-install/desktop/workrave:workrave.desktop as well then right?
Don't see much point in removing, it's just a console warning. I guess if it really bothers you until fixed just edit the /usr/share/app-install/desktop/workrave:workrave.desktop, give it a single line comment such as in screen
(whether the contents of /usr/share/app-install/desktop/ get refreshed at some point/action I don't know...

If one was using workrave & pending a fix wanted it to show in the Dash for some reason then they'd need to edit /usr/share/applications/workrave.desktop & edit the 2 multi-line Comments to be on a single line

---

### Post by Cavsfan on 2013-04-13
Without editing that file it looks just like your except for the comment:

```
cavsfan@cavsfan-MS-7529:~$ cat /usr/share/app-install/desktop/workrave:workrave.desktop
[Desktop Entry]
Categories=Application;Other
X-AppInstall-Package=workrave
X-AppInstall-Popcon=500
X-AppInstall-Section=universe

Type=Application
Categories=[COLOR=#ff0000]Utility[/COLOR];GTK;Accessibility
Exec=workrave
Icon=workrave
Comment=Assists in the prevention and recovery of Repetitive Strain Injury (RSI)
- RSI (Repetitive Strain Injury) oraz wspomaga rekonwalescencj&#281;
 &#1079;&#1072;&#1087;&#1103;&#1089;&#1090;&#1100;&#1103; &#1080; &#1089;&#1085;&#1103;&#1090;&#1080;&#1080; &#1086;&#1073;&#1097;&#1077;&#1075;&#1086; &#1084;&#1099;&#1096;&#1077;&#1095;&#1085;&#1086;&#1075;&#1086; &#1085;&#1072;&#1087;&#1088;&#1103;&#1078;&#1077;&#1085;&#1080;&#1103;.
Name=Workrave

X-Ubuntu-Gettext-Domain=app-install-data
```

It doesn't bother me but, thanks for your help! 
I will install the final release after May 9th and this will most probably be history.

Thanks again. :)

---

### Post by serdotlinecho on 2013-04-17
> I noticed this file exists although I never installed workrave - /usr/share/app-install/desktop/workrave:workrave.desktop.
Didn't even know what workrave was until now.

[https://apps.ubuntu.com/cat/applications/workrave/](https://apps.ubuntu.com/cat/applications/workrave/)
[http://www.sonicvisualiser.org/download.html](http://www.sonicvisualiser.org/download.html)

Hmmm, this is just silly bug when updating software center database  ](*,)

```
$ cd /usr/share/app-install/desktop
$ ls | less
```

When you search in software center, it will search from this directory.

I don't use Software Center and have purged it. I can't stand waiting when updating software center database...slow. [-(

---

### Post by Cavsfan on 2013-04-18
> **serdotlinecho said:**
> I don't use Software Center and have purged it. I can't stand waiting when updating software center database...slow. [-(

Maybe you need a quad core like I have or even an i7 8 core like my son has. Nothing is slow on this core 2 quad Q9550 and it's about 3 1/2 years old. ;)

---

