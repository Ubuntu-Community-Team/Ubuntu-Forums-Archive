---
title: "Help! I have some security issue on my system"
date: 2010-10-08
forum: Security
---

### Post by federer2nadal on 2010-10-08
hello.
I have some problem. I kinda new to ubuntu and don't know it to very deep level. I never touched the software sources or important places of the system and only isntalled sowftwares from the ubuntu software center. I did add few applets but only from the ubuntu software center. I added few themes from art.gnome. I did today an update and after the update I scanned the computer with rkhunter and chkrootkit( no warnings). the rkhunter found the following:

File properties checks...
    Files checked: 132
    Suspect files: 43

 Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]
and for the results for the first section:
    /bin/cat                                                 [ Warning ]
    /bin/chmod                                               [ Warning ]
    /bin/chown                                               [ Warning ]
    /bin/cp                                                  [ Warning ]
    /bin/date                                                [ Warning ]
    /bin/df                                                  [ Warning ]
    /bin/echo                                                [ Warning ]
  /bin/ls                                                  [ Warning ]
    /bin/mktemp                                              [ Warning ]
    /bin/mv                                                  [ Warning ]
    /bin/pwd                                                 [ Warning ]
    /bin/readlink                                            [ Warning ]
   /bin/touch                                               [ Warning ]
    /bin/uname                                               [ Warning ]
    /usr/bin/basename                                        [ Warning ]
    /usr/bin/cut                                             [ Warning ]
   /usr/bin/dirname                                         [ Warning ]
    /usr/bin/dpkg                                            [ Warning ]
    /usr/bin/dpkg-query                                      [ Warning ]
    /usr/bin/du                                              [ Warning ]
    /usr/bin/env                                             [ Warning ]
    /usr/bin/groups                                          [ Warning ]
    /usr/bin/head                                            [ Warning ]
    /usr/bin/id                                              [ Warning ]
    /usr/bin/md5sum                                          [ Warning ]
   /usr/bin/runcon                                          [ Warning ]
    /usr/bin/sha1sum                                         [ Warning ]
    /usr/bin/sha224sum                                       [ Warning ]
    /usr/bin/sha256sum                                       [ Warning ]
    /usr/bin/sha384sum                                       [ Warning ]
    /usr/bin/sha512sum                                       [ Warning ]
  /usr/bin/sort                                            [ Warning ]
    /usr/bin/stat                                            [ Warning ]
    /usr/bin/tail                                            [ Warning ]
    /usr/bin/test                                            [ Warning ]
    /usr/bin/touch                                           [ Warning ]
    /usr/bin/tr                                              [ Warning ]
    /usr/bin/uniq                                            [ Warning ]
    /usr/bin/users                                           [ Warning ]
    /usr/bin/wc                                              [ Warning ]
    /usr/bin/who                                             [ Warning ]
    /usr/bin/whoami                                          [ Warning ]
    /usr/sbin/chroot                                         [ Warning ]
most of the changes took place at 21 sept 2010(from the log) and few from today. 
I installed avast and scanned few days ago and it found nothing but lot files have been skipped. (I don't know why) .

my question is: does my system has any security risk ? I remind you that I never touched the software sources and the update settings. I didn't touched inside the system either. ( the warnings came after the today update, before it I had only 2 warnings).

thank you for your help.

---

### Post by federer2nadal on 2010-10-08
by the way I have ubuntu 10.04.

---

### Post by cariboo on 2010-10-08
As usual rkhunter came up with a lot of false positives. After installing new packages you have to update the rkhunter database. or you wil get the results you did. To update the database type:

```
rkhunter --propupd
```

When running tools like rkhunter for no reason, you should check the manpages, so at least you have an idea what the package is supposed to do, and how it does it.

---

### Post by federer2nadal on 2010-10-08
thank you very much! 0 warnings after. 
but what about this :

    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]
It's mainly contains java and other staff.

---

### Post by scrooge_74 on 2010-10-09
I was reading your list and hopping you hadnt delete anything.

I basically dont use that app, I dont feel I need to, some reading will provide more security and confidence that those kind of apps.

/dev  <---stores the devices of your equipment (lan cards, usb, etc etc) dont touch it

there are lots of hidden files in your /home/user that are suppose to be hidden.
Do yourself a favor dont use that app, and do more research, that way you wont have to panic when you see something weird.

In fact want to see weird stuff and then have to learn about it to understand your system go to /var/log and read the logs, is a more interesting reading and you will have questions and you will then google for them learn a lot and feel more confident of having left Window$ world.

---

### Post by Rubi1200 on 2010-10-09
> **scrooge_74 said:**
> I was reading your list and hopping you hadnt delete anything.

I basically dont use that app, I dont feel I need to, some reading will provide more security and confidence that those kind of apps.

/dev  <---stores the devices of your equipment (lan cards, usb, etc etc) dont touch it

there are lots of hidden files in your /home/user that are suppose to be hidden.
Do yourself a favor dont use that app, and do more research, that way you wont have to panic when you see something weird.

In fact want to see weird stuff and then have to learn about it to understand your system go to /var/log and read the logs, is a more interesting reading and you will have questions and you will then google for them learn a lot and feel more confident of having left Window$ world.
+1

Tools like this are basically useless unless you are willing to do the legwork and investigate the results.

Almost every week someone posts their logs from chkrootkit or rkhunter and freaks out because it says it found hidden this or warning that.

Read the security stickies, keep your system updated, only install software from the repositories, and don't run services like vnc etc. without properly securing them, and use strong passwords.

If you do all that, you can sleep easy at night!

---

### Post by federer2nadal on 2010-10-09
ok I have lot of information from sites about security and other stuff. thank you for your advice and help. I really glad that I've left windows forever. I don't touch any system files because I don't know what would happen. I install updates only from ubuntu servers which were installed by defult. about the services: I download programs for ubuntu only from the ubuntu software center and downloading themes from art.gnome.

---

### Post by cariboo on 2010-10-09
be careful when downloading files from gnome-look.org, as there was a malicious .deb available for a while.

---

### Post by wacky_sung on 2010-10-10
> **cariboo907 said:**
> be careful when downloading files from gnome-look.org, as there was a malicious .deb available for a while.

It seem like it has happened quite some time back and ponder how safe is it.I think it is better to be safe than sorry.

[http://www.ubuntu-user.com/Online/News/Malicious-Screensaver-Malware-on-Gnome-Look.org](http://www.ubuntu-user.com/Online/News/Malicious-Screensaver-Malware-on-Gnome-Look.org)

```
Malicious Screensaver: Malware on Gnome-Look.org
12/10/2009
A screensaver from Gnome-Look.org at closer look revealed itself to be malware.

When installing an innocuous "waterfall" screensaver from Gnome-Look.org, an Ubuntu user noticed something strange: apart from the screensaver not being on GNOME's approved list, it also contained a script that performed some peculiar substitutions.

Among other things, it took a file named auto.bash from the server and installed it on /user/bin/, along with a file named gnome.sh that it put in the /etc/profile.d/ directory. The script then issued ping requests to send very large packages to a particular server. The script presumably helped serve in a denial-of-service (DoS) attack against other servers that provide exploits for huge multiplayer games such as World of Warcraft.

The user posted his discovery in the Ubuntu Forums and the screensaver has since disappeared from the Gnome-Look.org site. The guesswork as to what the script exactly did and how to remove was batted about in the forum. Apparently the Debian package installed under the name app5552. It was determined that removing the malware together with the malicious script required the command

sudo rm -f /usr/bin/Auto.bash /usr/bin/run.bash /etc/profile.d/gnome.sh /usr/bin/index.php /usr/bin/run.bash && sudo dpkg -r app5552

In general the lesson to be learned is if you want a secure system, don't download any software outside the official package sources without at least looking at the source code first.
```

---

### Post by cariboo on 2010-10-10
There a couple threads in Recurring, about the .deb

[http://ubuntuforums.org/showthread.php?t=1349801&highlight=gnome-look](http://ubuntuforums.org/showthread.php?t=1349801&highlight=gnome-look)

[http://ubuntuforums.org/showthread.php?t=1349678](http://ubuntuforums.org/showthread.php?t=1349678)

---

### Post by OpSecShellshock on 2010-10-10
As far as I can tell, there's no reason to elevate privileges for the sake of a mere visual tweak on a single-user system, much less use a full-on package installer. Sometimes themes and icon sets include scripts for the sake of convenience, but you should read those before running them. The really good ones have commented-out lines that tell you what everything does.

---

