---
title: "Notify-send HOWTO"
date: 2010-02-20
forum: Tutorials
---

### Post by DeusEx on 2010-02-20
Notify-send is a little, simple On-Screen Display application. It uses the notify bubble (or balloon?) pop-up system as seen in 9.10 Karmic.

Despite its usage is very simple you can have a lot of fun with it. Let's install it first:

```

sudo apt-get install notify-osd

```

Now this command should pop up a 'bubble':
```

notify-send Test "Hello World"

```

The --help option shows basic usage:

```

$notify-send --help
Usage:                             
  notify-send [OPTION...] <SUMMARY> [BODY] - create a notification                                                    

Help Options:
  -?, --help                        Show help options

Application Options:
  -u, --urgency=LEVEL               Specifies the urgency level (low, normal, critical).                              
  -t, --expire-time=TIME            Specifies the timeout in milliseconds at which to expire the notification.
  -i, --icon=ICON[,ICON...]         Specifies an icon filename or stock icon to display.
  -c, --category=TYPE[,TYPE...]     Specifies the notification category.
  -h, --hint=TYPE:NAME:VALUE        Specifies basic extra data to pass. Valid types are int, double, string and byte.
  -v, --version                     Version of the package.

```

Some examples:

1. Basic message with an icon in front of the Title showing 5000 milliseconds
```

notify-send "Message Title" "The message body is shown here" -i /usr/share/pixmaps/idle.xpm -t 5000

```

2. Show contents of a file:
```

notify-send test "`tail /var/log/syslog`"

```

3. Follow log file:
```

tail -n0 -f /var/log/messages | while read line; do notify-send "System Message" "$line"; done

```

4. Format message with HTML:
```

notify-send Test "<font size=16 color=blue><b><i>Hello World</b></i></font>"

```

---

### Post by mohave on 2010-02-22
To help anyone in my case: if notify-send can't be found to be installed in your system install first libnotify-bin.

And just a comment: the HTML sample is not working in my system...maybe anyother library is required ¿?

Thank you DeusEx !

---

### Post by DeusEx on 2010-02-22
Odd, I don't have a notify-bin package in my repositories. My version of notify-osd is 0.9.24, and for notify-send it's 0.4.5. Perhaps your DBUS version doesn't like the HTML?

BTW I made a typo, the package to install should be notify-osd (updated first post). the command to send messages is notify-send...

---

### Post by Icegirl on 2010-06-04
Alguien sabe si el icono tiene que tener caracteristicas específicas para ser mostrado?. No logro que me aparezcan:(

---

### Post by sossanator on 2010-07-29
Does anyone know the code if i want it to notify me if someone logs in like via ssh?

---

### Post by baddnady23 on 2010-09-12
> **sossanator said:**
> Does anyone know the code if i want it to notify me if someone logs in like via ssh?

I'm going to bump this, great idea

---

### Post by dualbus on 2010-09-12
> **Icegirl said:**
> Alguien sabe si el icono tiene que tener caracteristicas específicas para ser mostrado?. No logro que me aparezcan:(

Las reglas de ubuntuforums especifican que debes comunicarte en inglés. 
Ubuntuforums rules specify that you must communicate in English.


Not all GNU/Linux distros have the same icons, so before you use them, you should check that they exist:

```
file /path/to/file
```

If they do exist, then you can use them with notify-send as specified above.

---

### Post by MeduZa on 2010-09-21
> **sossanator said:**
> Does anyone know the code if i want it to notify me if someone logs in like via ssh?

you can try with notifyme and notify-send

notifyme -C `cat /etc/passwd | cut -d: -f1`

---

### Post by sossanator on 2010-10-07
> **MeduZa said:**
> you can try with notifyme and notify-send

notifyme -C `cat /etc/passwd | cut -d: -f1`

It worked, sort of. It will only notify me if i have a terminal open. In my case i use Yakuake and it will only show the message in the terminal when i have it visible. Maybe im doing something wrong. Thanks for the help.

---

### Post by Covi on 2010-10-11
> **dualbus said:**
> Las reglas de ubuntuforums especifican que debes comunicarte en inglés. 
Ubuntuforums rules specify that you must communicate in English.


Not all GNU/Linux distros have the same icons, so before you use them, you should check that they exist:

```
file /path/to/file
```

If they do exist, then you can use them with notify-send as specified above.Tampoco hace falta ser desagradable.
To be unpleasant is not necessary either.
:(


Lucid, notify-send 0.4.5 (*libnotify-bin 0.4.5-1ubuntu4*): html format doesn't work :S

---

### Post by cgroza on 2010-10-11
Thanks, you helped me improve my script's notification system.

---

### Post by DrAcid on 2010-10-13
Btw, if anyone is interested, after Karmic(or jaunty, I'm not sure) -t timeout parameter is broken.

Lately a guy named Sukochev Roman [leolik] has been working on notify-osd a lot!
ThanX to him, now we have a pretty customizable notifications! :)
He has fixed the timeout issue as well!

Here's an article from webupd8 on how to customize the messages:
[http://www.webupd8.org/2010/05/finally-easy-way-to-customize-notify.html](http://www.webupd8.org/2010/05/finally-easy-way-to-customize-notify.html)

* *Edit*:

If Your notify bubbles flicker on fade in/out --> disable "Fading Windows" in Compiz 'Effects' group... ;)

---

### Post by averlon on 2011-06-10
Hi,
I have successfully used notify-send in an interactive shell and in scripts.

But if an script is started via cron, notify-send does not work.

Any hints?

---

### Post by cream wobbly on 2011-06-14
> **averlon said:**
> Hi,
I have successfully used notify-send in an interactive shell and in scripts.

But if an script is started via cron, notify-send does not work.

Any hints?
I'm a RHEL user, so paths might be different in Ubuntu.

You need to allow local root user to display to the current X session. Create a new file */etc/X11/xinit/xinitrc.d/localroot.sh*, containing the command:
```
xhost +si:localuser:root
```
When X starts next time, this new script will be sourced from the script */etc/X11/xinit/xinitrc-common*. You can do it to a running session by having the session owner (whoever logged in) type the full *xhost* command exactly as above.

Now your cron command can say:
```
DISPLAY=:0  notify-send ... 
```

---

### Post by averlon on 2011-06-21
Hi cream wobbly,
thanks for the reply.
although ubuntu seems to have a different file structure, since */etc/X11/xinit/xinitrc.d* does not exist.

I am not sure how to setup it here but I will find the way through now.

Thanks again for your good help.

---

### Post by averlon on 2011-06-22
Hi,
so far it was not possible for me to identify the path where to make the appropriate changes in ubuntu.

When I enter the xhost-command in a terminal window the cron-job using the  ```
DISPLAY=:0  notify-send ...
``` works.

If i enter the xhost command and the notify-send inside the cron-job, although the job is run as root, it does not work.

Could you give me a hint where to search and find out what file structure in ubuntu is according to the file structure you reported from RHEL.
Thanks

---

### Post by ryran on 2011-12-06
> **sossanator said:**
> Does anyone know the code if i want it to notify me if someone logs in like via ssh?I'm a little late, but... The question inspired me to write a bash script to do just that. You can get it **[here, at my github]("https://github.com/ryran/tail2notify/blob/master/tail2notify")**. (Or **[here, for direct-download]("https://raw.github.com/ryran/tail2notify/master/tail2notify")**.)

But here's the simple answer: What you need is something like this.
```
sudo tail -fn0 /var/log/secure  |
  grep --line-buffered "sshd.*Accepted" |
    while read line; do
      notify-send -u critical "SSH LOGIN" "$line"
    done
```

Or, more spiffy-like:
```
#WARNING: The following uses some special BASH features, meaning, it won't work in dash.

sudo tail -fn0 /var/log/secure |
  grep --line-buffered 'sshd.*Accepted' |
    while read line; do
      timestamp=${line/ $(hostname)*/}
      ip=${line#*from }; ip=${ip% port*}
      msg=${line#*]: }
      notify-send -u critical "sshd: Session initiated by $ip" "[$timestamp]\n$msg"
    done
```

The script I linked above also prints notifications for failed login attempts. Hope someone finds it useful!

Edit: In my sleep-deprived stupor I forgot to link the screenshots I took. Here's two. The rest are at [http://b19.org/linux/notify_sshd/](http://b19.org/linux/notify_sshd/).

[IMG]http://b19.org/linux/notify_sshd/sshd_accepted_pubkey.png[/IMG]

[IMG]http://b19.org/linux/notify_sshd/sshd_failed_login.png[/IMG]

---

### Post by mohave on 2011-12-06
Appreciate, ryran, works great!!
(in my k-ubuntu release Oneiric, just changing /var/log/secure by /var/log/auth.log)

Thanks!

---

### Post by ryran on 2011-12-07
Updated the script I linked in my previous comment. Same link. It worked fine before, but error-handling and cleanup is quite better now (e.g., if you execute it multiple times, it doesn't leave any orphaned tail processes hanging about), and I took into account the whole /var/log/secure VS /var/log/auth.log thing. (THANKS mohave!)

---

### Post by ryran on 2011-12-18
WOW! My previous post was only a week ago?! Man, since then I've learned a whole new programming language...

In any case, I almost completely rewrote the script from before (edited the link). Still BASH, but now it's called [tail2notify]("https://github.com/ryran/tail2notify/blob/master/tail2notify"). It is much more generic (takes parameters to pass to tail & grep); however, it can still meet the original goal of notifications on ssh logins. Peace!

---

### Post by thirdy on 2012-01-03
Thanks! I am relatively new to linux but I managed to create a simple bash script to show a notification to rest my eyes & also activate the screen saver :p


> **DeusEx said:**
> Notify-send is a little, simple On-Screen Display application. It uses the notify bubble (or balloon?) pop-up system as seen in 9.10 Karmic.

Despite its usage is very simple you can have a lot of fun with it. Let's install it first:

```

sudo apt-get install notify-osd

```

Now this command should pop up a 'bubble':
```

notify-send Test "Hello World"

```

The --help option shows basic usage:

```

$notify-send --help
Usage:                             
  notify-send [OPTION...] <SUMMARY> [BODY] - create a notification                                                    

Help Options:
  -?, --help                        Show help options

Application Options:
  -u, --urgency=LEVEL               Specifies the urgency level (low, normal, critical).                              
  -t, --expire-time=TIME            Specifies the timeout in milliseconds at which to expire the notification.
  -i, --icon=ICON[,ICON...]         Specifies an icon filename or stock icon to display.
  -c, --category=TYPE[,TYPE...]     Specifies the notification category.
  -h, --hint=TYPE:NAME:VALUE        Specifies basic extra data to pass. Valid types are int, double, string and byte.
  -v, --version                     Version of the package.

```

Some examples:

1. Basic message with an icon in front of the Title showing 5000 milliseconds
```

notify-send "Message Title" "The message body is shown here" -i /usr/share/pixmaps/idle.xpm -t 5000

```

2. Show contents of a file:
```

notify-send test "`tail /var/log/syslog`"

```

3. Follow log file:
```

tail -n0 -f /var/log/messages | while read line; do notify-send "System Message" "$line"; done

```

4. Format message with HTML:
```

notify-send Test "<font size=16 color=blue><b><i>Hello World</b></i></font>"

```

---

### Post by znikolov on 2012-02-20
Hi, I have a related issue. I am using ubuntu 11.10 and tried the scrypt for ultrabay_eject from thinkwiki. It calls notify-send but no notificatio is displayed. The ONLY way for the notification to work is to do 

xhost +local: 

in a terminal window and then generate the acpi event by pulling the lever on the laptop. Note that the script is working with notifications if manually run via the terminal. 

So the question here is - how can i make xhost +local: work in the script or being executed as my laptop starts? Tried placing it in /etc/rc.local but still no go.

Thanks

---

### Post by Lupius on 2013-02-14
For some reason my notify-send does not load stock icons. For example, instead of ```
notify-send -i notification-message-im
```, I have to specify the full path with ```
notify-send -i /usr/share/notify-osd/icons/hicolor/scalable/status/notification-message-im.svg
```

Is there any way to fix this?

---

### Post by ebik on 2013-02-15
> **Lupius said:**
> For some reason my notify-send does not load stock icons. For example, instead of ```
notify-send -i notification-message-im
```, I have to specify the full path with ```
notify-send -i /usr/share/notify-osd/icons/hicolor/scalable/status/notification-message-im.svg
```Is there any way to fix this?

Just send ```
notify-send -i message-im
```
I.e., without the "notification-" in the beginning.

---

### Post by Lupius on 2013-02-19
Thanks but that didn't work either.

---

### Post by Vu_Trung_An on 2013-09-20
> **Lupius said:**
> For some reason my notify-send does not load stock icons. For example, instead of ```
notify-send -i notification-message-im
```, I have to specify the full path with ```
notify-send -i /usr/share/notify-osd/icons/hicolor/scalable/status/notification-message-im.svg
```

Is there any way to fix this?

You should put the image path into "...". Try this and feed back me your result :D

---

### Post by beetee2 on 2013-12-30
I'm trying to add a custom icon to my notification that is getting created in a Java class. When I explicitly provide a path to the image, ie-'/home/name/Pictures/image.png' it works beautifully. But I'm having a problem now where I want to package this app up and put it on github so anyone can use it, but when I include the image in my java project, and either put it in a 'res' folder, or even in the same folder as the Main.java file, it isn't working. Any idea why?

---

### Post by gautamsomani on 2014-05-02
I am trying to set the maximum time to 5000 ms, using -t 5000, but its staying longer than that. What could be the reason?

---

### Post by fabrizio-marana on 2014-11-02
Just follow this article to change the time-out:
[http://www.webupd8.org/2014/04/configurable-notification-bubbles-for.html](http://www.webupd8.org/2014/04/configurable-notification-bubbles-for.html)

---

