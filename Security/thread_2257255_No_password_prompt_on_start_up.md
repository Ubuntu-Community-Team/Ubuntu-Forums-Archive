---
title: "No password prompt on start up"
date: 2014-12-18
forum: Security
---

### Post by Entheo on 2014-12-18
Hi All

I want to have to enter my password on start up due to privacy but i cannot. I have checked related settings and i should be asked for password on start up but nothing is happening. 

Any help would be appreciated.

---

### Post by Penguin360 on 2014-12-18
Are you using Live CD?

---

### Post by deadflowr on 2014-12-18
Which start up point?
When you boot or when you login?

---

### Post by Entheo on 2014-12-18
No it is not a live cd. It is a full install on hdd.

It is when i boot up. I dont get any login options. After post it loads straight to desktop. I have checked that i have selected the option to login on start up (boot) but nothing happens. It is weird!

---

### Post by Entheo on 2014-12-19
Can anyone tell me if Xubuntu 14.04 should have a password prompt on start up (boot) by default? On installation i did deselect the option for a login password but surely there is a way to change that after install.

When i leave my pc for a while and the screensaver appears then i have to enter password to log back in so the password prompt is working just not on starting up my pc.

---

### Post by oldos2er on 2014-12-19
I know you said in your first post you checked related settings, which would be Users and Groups in the Settings Manager. Autologin can be enabled or disabled from there. 

I think there is an option when installing *buntu to enable autologin, if you did this you would never see a password prompt.

---

### Post by Entheo on 2014-12-19
Thanks for your reply oldos2er! The weird thing with this is that, on the **[COLOR=#000080]Users and Groups[/COLOR]** screen, there is the usual first line regarding account type and the line below it says......
Password: Asked on login..............but it is not being asked on login! I even changed the password to see if that reset it but nope. Bizarre!

---

### Post by Elfy on 2014-12-19
What files do you have in /etc/lightdm/ and /etc/lightdm/lightdm.conf.d ?

---

### Post by slickymaster on 2014-12-19
Make sure that your user is not in the **nopasswdlogin** group:```
sudo gpasswd -d username nopasswdlogin
```where username is your login name. After that reboot your system to confirm that everything is working as expected.

---

### Post by Entheo on 2014-12-19
In my lightdm directory i got a file called users.conf which may be of help.......

# User accounts configuration
#
# NOTE: If you have AccountsService installed on your system, then LightDM will
# use this instead and these settings will be ignored
#
# minimum-uid = Minimum UID required to be shown in greeter
# hidden-users = Users that are not shown to the user
# hidden-shells = Shells that indicate a user cannot login
#
[UserAccounts]
minimum-uid=500
hidden-users=nobody nobody4 noaccess
hidden-shells=/bin/false /usr/sbin/nologin

and this is what is in my /etc/lightdm/lightdm.conf......
 
[SeatDefaults]
user-session=xubuntu

---

### Post by Entheo on 2014-12-19
Ok Slickymaster i will give that a go now..........cool avatar btw!

Update: I just entered that command into terminal Slicky and a message came up to say that i was no longer in the nopasswdlogin group but after rebooting still no login prompt.

---

### Post by slickymaster on 2014-12-19
> **Entheo said:**
> Ok Slickymaster i will give that a go now..........cool avatar btw!

Update: I just entered that command into terminal Slicky and a message came up to say that i was no longer in the nopasswdlogin group but after rebooting still no login prompt.
Hmmm...

I'm starting to suspect that you're being affect by [https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/1169054](https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/1169054)

---

### Post by Entheo on 2014-12-19
Yep it sure sounds similar! I wonder if i can add third party software to act as a password manager? I will look in USC and through some PPA's and see if there is one that integrates well with ubuntu.

---

### Post by Entheo on 2014-12-20
No luck with getting software to fix the problem so am struggling to find a solution. The read outs on page one look like they might hold the key but i am not yet good enough at reading the language to do anything with it.

---

### Post by Elfy on 2014-12-20
Check out files in /usr/share/lightdm/lightdm.conf.d/ 

See if any of those still show autologin.

---

### Post by Entheo on 2014-12-20
There are four files inside that folder and none mention anything regarding autologin. 

SeatDefaults]
greeter-session=lightdm-gtk-greeter

[SeatDefaults]
guest-wrapper=/usr/lib/lightdm/lightdm-guest-session

[SeatDefaults]
greeter-wrapper=/usr/lib/lightdm/lightdm-greeter-session

[SeatDefaults]
# Dump core
xserver-command=X -core

---

### Post by Entheo on 2014-12-21
I can't understand why i am asked to enter password after screensaver kicks in but can't find a way to do the same for when i boot up.

---

### Post by Elfy on 2014-12-22
Tried this in a 15.04 vm and a 14.04 vm

When installing - set it to autologin.

Checked Users post-install - that showed user password was asked on login.

lightdm.conf was
```

[SeatDefaults]
autologin-guest=false
autologin-user=hob
autologin-user-timeout=0
autologin-session=lightdm-autologin
```

Commented out the last 4 lines - booted to password request on both vm's.

Was this a clean install or an upgrade from a previous version? IIRC lightdm files changed about the time of 14.04, if that's the case I wonder if you've got a file elsewhere still showing autologin.

If you are still having issues please run from a terminal

```
sudo updatedb
locate lightdm | pastebinit
```

give the url you receive from that.

---

### Post by Entheo on 2014-12-22
It was a clean install Elfy. OK i will try that code and post url............[http://paste.ubuntu.com/9599486/](http://paste.ubuntu.com/9599486/)...........i didnt know you could do that (pastebinit) from terminal. That is a cool trick! Ubuntu never fails to impress.

---

### Post by Elfy on 2014-12-23
```
cat /etc/lightdm/lightdm.conf.d/10-xubuntu.conf
```

paste that here please

(pastebinit - this is available in the repos, but Xubuntu seeds it by default)

---

### Post by slickymaster on 2014-12-23
Besides the output Elfy asked you, can you please also provide us the output of```
cat /etc/init/lightdm.conf
```

---

### Post by Entheo on 2014-12-23
Ok Elfy here is the output you asked for:

```
[SeatDefaults]
user-session=xubuntu
```

And here is yours Slicky:
[SIZE=1]
```
[SIZE=2]LightDM - light Display Manager
#
# The display manager service manages the X servers running on the
# system, providing login and auto-login services
#
# based on gdm upstart script

description    "LightDM Display Manager"
author        "Robert Ancell <robert.ancell@canonical.com>"

start on ((filesystem
           and runlevel [!06]
           and started dbus
           and plymouth-ready)
          or runlevel PREVLEVEL=S)

stop on runlevel [016]

emits login-session-start
emits desktop-session-start
emits desktop-shutdown

script
    if [ -n "$UPSTART_EVENTS" ]
    then
        # Check kernel command-line for inhibitors, unless we are being called
        # manually
        for ARG in $(cat /proc/cmdline); do
            if [ "$ARG" = "text" ]; then
        plymouth quit || : 
                stop
        exit 0
            fi
        done

    [ ! -f /etc/X11/default-display-manager -o "$(cat /etc/X11/default-display-manager 2>/dev/null)" = "/usr/bin/lightdm" -o "$(cat /etc/X11/default-display-manager 2>/dev/null)" = "/usr/sbin/lightdm" ] || { stop; exit 0; }

    if [ "$RUNLEVEL" = S -o "$RUNLEVEL" = 1 ]
    then
        # Single-user mode
        plymouth quit || :
        exit 0
    fi
    fi

    exec lightdm
end script

post-start script
    sleep 5
    clear > /dev/tty7
end script

post-stop script
    clear > /dev/tty7
    sleep 1
    if [ "$UPSTART_STOP_EVENTS" = runlevel ]; then
        initctl emit desktop-shutdown
    fi
end script[/SIZE]
```

[SIZE=3]Sorry, i should of used pastebinit for that last lot [/SIZE]
[/SIZE]

---

### Post by Elfy on 2014-12-23
mmm

output of this?

```
groups
``` just to see if it is appearing in nopasswdlogin group (but I suspect not)

OK - so rebooted the vm which was left previously requiring a password from above.

Going to Users Settings - changing to autologin and NOW it tells me that Password: Not Asked at login - rebooted and it asked for password

It seems that Users Settings makes no effective changes.

Looks like a bug to me - doesn't appear to be the same as the one above to me. 

Maybe report the bug. Not that it helps you much here. I'm not able to help more here I'm afraid.

---

### Post by Entheo on 2014-12-23
Output of groups = adam adm dialout fax cdrom floppy tape sudo audio dip video plugdev netdev fuse lpadmin sambashare

I might report the bug as it may help someone else out down the line. It is ok i can live with the problem.

 Thank you very much for your time on this elfy and slickymaster! It is appreciated.

---

### Post by Elfy on 2014-12-23
please run 

```
lsb_release -a
```

---

### Post by Entheo on 2014-12-23
This is what i got......

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

---

### Post by slickymaster on 2014-12-23
You could try something as an experiment, which is to add **autologin-user=yourUserName** to your _[COLOR=#000000]/etc/lightdm/lightdm.conf.d/[/COLOR]10-xubuntu.conf_ file.

In any case, please be aware that if it goes wrong you might need to resort to recovery and nano to fix it.

In a terminal window```
sudo nano [COLOR=#000000]/etc/lightdm/lightdm.conf.d/[/COLOR]10-xubuntu.conf
```Now add ```
autologin-user=yourUserName
``` to the end of the file. Save and close the file and reboot your system. You should login without being prompted for your password. Now repeat again```
sudo nano [COLOR=#000000]/etc/lightdm/lightdm.conf.d/[/COLOR]10-xubuntu.conf
```and comment out that last line so it reads like this```
#autologin-user=yourUserName
```save and close the file and reboot once again to see if now you're prompted for your password.

---

### Post by philrobww on 2015-09-12
Hi Stickymaster I run xubuntu 14.04 LTS, and needed to set the password prompt at startup You  suggested editing  /etc/lightdm/lightdm.conf.d/10-xubuntu.conf  by using the 'sudo nano' command and add a “#” to the line "autologin-user=yourUserName".  I found that this line isn't in the document "10-xubuntu.conf"  but I found it in   /etc/lightdm/lightdm.conf. after the “#” symbol was added my machine requested the password on startup, this solved the problem for me. Hope you find this useful.





> **slickymaster said:**
> You could try something as an experiment, which is to add **autologin-user=yourUserName** to your _[COLOR=#000000]/etc/lightdm/lightdm.conf.d/[/COLOR]10-xubuntu.conf_ file.

In any case, please be aware that if it goes wrong you might need to resort to recovery and nano to fix it.

In a terminal window```
sudo nano [COLOR=#000000]/etc/lightdm/lightdm.conf.d/[/COLOR]10-xubuntu.conf
```Now add ```
autologin-user=yourUserName
``` to the end of the file. Save and close the file and reboot your system. You should login without being prompted for your password. Now repeat again```
sudo nano [COLOR=#000000]/etc/lightdm/lightdm.conf.d/[/COLOR]10-xubuntu.conf
```and comment out that last line so it reads like this```
#autologin-user=yourUserName
```save and close the file and reboot once again to see if now you're prompted for your password.

---

### Post by slickymaster on 2015-09-14
> **philrobww said:**
> Hi Stickymaster I run xubuntu 14.04 LTS, and needed to set the password prompt at startup You  suggested editing  /etc/lightdm/lightdm.conf.d/10-xubuntu.conf  by using the 'sudo nano' command and add a “#” to the line "autologin-user=yourUserName".  I found that this line isn't in the document "10-xubuntu.conf"  but I found it in   /etc/lightdm/lightdm.conf. after the “#” symbol was added my machine requested the password on startup, this solved the problem for me. Hope you find this useful.

Thanks for the heads up.

---

### Post by deadflowr on 2015-09-14
There is a hierarchy to lightdm's loading sequence.
It looks first to the default location in /usr/share/lightdm.
Then it looks in /etc/lightdm for any configuration files.
Then finally it looks in the lightdm.conf.d subfolder for any configuration files found there.(if the subfolder exists, that is)

Each one can overwrite the next.

Note that you ignore the /usr/share folder for various reasons, top of which is that it's the default setup and as such will get overwritten upon any lightdm software update/upgrade. Making editing it a comical variation of who's on first?(you'd just keeping repeating the action of editng you setup, over and over)
System updates generally do not change any settings in /etc. And any updates that do will inform you of those changes, and most give you the option of keeping the old setup in place. Which is why you make/create or edit existing configs in here.

Generally it's easiest on a user to make their own configuration file sometime (such as a time like this) which the user can fully control and not worry about what might happen if the user decides to remove that config.
Perhaps this is a good reason why it's mostly suggested to do the editing in a new file, typically the 10-myconfig.conf file.
As opposed to adding/editing the existing config /etc/lightdm/lightdm.conf.

Hope this makes sense.

---

