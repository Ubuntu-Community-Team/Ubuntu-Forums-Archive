---
title: "Check if system restart is required on server"
date: 2008-12-16
forum: Server Platforms
---

### Post by netJackDaw on 2008-12-16
I've seen this question asked a few times but never really answered...

When you run a desktop installation of Ubuntu you will get an icon that tells you a system restart is required if there are updates that require that. When you run a server with only cli you don't get this feedback from the system. So I would like to ask the system if it needs a restart. Is there a file a can look in or a command I can launch to get this information?

I am not interested in a discussion whether or not you should restart your server based on what was upgraded. I know that basically only kernel updates require restart.

---

### Post by cariboo on 2008-12-16
The short answer is no. As a server admin you should know what you are upgrading, in most cases when services are upgraded they are restarted during the upgrade, services can be stopped and started without rebooting, so really then only time you need to restart is for a kernel upgrade. 

Jim

---

### Post by netJackDaw on 2008-12-16
Thanks for the short answer. But I am not really satisfied because the information behind the icon in the notification area has to come from somewhere. Some apt or deb-tool must be aware of the status as it can be shown in the notification area or is the status produced by the front end tool (update-manager).

If the notification is produced by update-manager I can understand why I can't see it on a server. On the other hand I can't see why update-manager would produce the notification (or state for it).

Is it produced by update-manager? Its a mystery...

---

### Post by gdebat on 2009-02-14
good question... anyone?

---

### Post by tubezninja on 2009-02-15
The extra information pretty much comes from the synaptic package manager, which obtains additional descriptive metadata about the package updates it's downloading.

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

There are two additional processes that it works with, called Update-Notifier and Update-Manager.

These packages as they're written now are GUI-based, and intended for desktop users.  If you want them, you install a GUI.  I realize this too, might be an unacceptable answer to you.  But that's just the way it is right now.

Of course, you are welcome to look at the source code, see where Synaptic and these helper programs are getting their package descriptive metadata from, and create your own command-line based notifier. :)  

But, as you said in your own first post on this thread, typically the only updates that require a reboot are kernel updates.  And if I were a betting sysadmin, I'd bet that since most sysadmins already know this, a full fledged cli-based notifier that belabors the point has just never really been a priority.

(Yes, I now, you didn't want to talk about that, either.  But that's a lot like saying you want someone to tell you when to put sunglasses on while they're not allowed to discuss the position of the Sun.  You HAVE to know about the position of the Sun if you want to know when to put those sunglasses on.)

FWIW, if I haven't found out about these updates through my own periodic checking of the repos, I usually get notifications about this sort of thing [here]("http://ubuntu.com/usn").  Nearly all of the kernel updates I've seen come down the pike are security updates, and the announcement of a new kernel update on this list generally lets you know if a reboot is required.

---

### Post by netJackDaw on 2009-03-06
Thank you for the informative answer.

Me wanting to focus on the specific question rather than the reasons for it was 
that I have seen the point get lost a few times regarding this question. I know some things but I also have the right to ask for an answer to a simple question without being bashed for it...

Also look at a situation like this. A few administrators are updating a set of servers. One does an update and does not restart. How will another or even the same admin know if the servers are restarted a few months from know. I know that this admin group should look at the ways they are doing their work. But the little help from getting this question answered would still help them...

---

### Post by threetimes on 2009-03-06
> **netJackDaw said:**
> ...How will another or even the same admin know if the servers are restarted a few months from know...```
uptime
```

---

### Post by netJackDaw on 2009-03-06
modded up: funny

> **threetimes said:**
> ```
uptime
```

Gee... it is hard to try to express what you mean sometimes...

---

### Post by bluefrog on 2009-03-06
for a desktop, have a look in /var/lib/update-notifier and /etc/apt/apt.conf/

for a server there's no update-notifier, still you could issue the following command (it certainly could be smaller but I am no genious in command line)

```
grep reboot /var/lib/dpkg/info/*.postinst | awk '{ print $1 }' | sed 's/:.*//' | uniq | xargs ls -clt | awk '{ print $6 "\t" $7 "\t" $8 }'
```

So you will see right away what package is advising you to reboot

---

### Post by Yashiro on 2009-03-07
That's not exactly seeing right away, is it?

I totally agree with the OP. Packages that require a reboot to enable their changes should not only tell you straight after the upgrade is performed but should be written to a log.

Other admins can then consult the 'deferred reboot' log to see what will bite them in the *** when they reboot.

---

### Post by HermanAB on 2009-03-07
A common way to manage things when you have a relatively small number of servers, is to keep a black hardcover book for each server as an engineering log.

BTW, here is the uptime of my mail server:
10:30:03 up 425 days,  8:07,  1 user

So, reboots really don't happen all that often!

Cheers,

Herman

---

### Post by Yashiro on 2009-04-03
There are a few Debian packages that remedy this flaw.

---

### Post by Kareeser on 2009-04-03
Might also be easier if the package manager sent local mail to inform the admin to reboot...

---

### Post by netJackDaw on 2009-04-07
> **Yashiro said:**
> There are a few Debian packages that remedy this flaw.
Hi Yashiro!
Which are these Debian packages that you refer to? Seems interesting to me!

---

### Post by neel.d on 2009-06-11
Hi, this is my 1st post on the forum. Please bare with me if my post is off the mark.

i found a script on the machine: 
"/usr/share/update-notifier/notify-reboot-required"

my understanding is, if the reboot is required, then this script is invoked. it will touch a file:
"/var/run/reboot-required"

if this file is present on the system, then restart the system.

Please let me know if this is the right answer.

cheers.. :D

---

### Post by Vegan on 2009-06-11
Given the updates are notified when I log on in 9.04 I can run...

```

sudo apt-get update
sudo apt-get upgrade

```

and I will be advised if a kernal update is needed.

I find that upgrades will restart services that have dependencies so rebooting the server is hardly needed save for a new kernel.

Until my old disk failed, uptime was over 4 months.

Now I have a new disk finally and uptime is growing as I slowly build new sites.

---

### Post by nitrogoldfish on 2009-07-14
I have this problem sometimes on servers that I don't log into very frequently that run updates automatically in cron. I hate having to restart them without really needing to, and I'm too lazy to look through all the updates that have happened recently for any kernel updates.

Since the only thing that really requires a restart is a kernel update, would it work to use something like this:
```

#discover installed version of kernel
dpkg --get-selections | grep -e "^linux-image-2\.[0-9]\."
#discover running version of kernel
uname -a

```
and check if the two match? 

or, if you prefer having the whole thing in a script, (which can run automatically after an apt-get upgrade) add some formatting and an if statement:
```

#!/bin/bash
#get installed version of kernel (strip "installed" from the end)
installed=`dpkg --get-selections | grep -e "^linux-image-2\.[0-9]\." | awk '{print $1}'`
#get running version of kernel and format to look like the package name
running="linux-image-`uname -a | awk '{print $3}'"
#check if the two match
if [ "$installed" != "$running" ]; then
echo "restart required"
#or send an email, or inform you however you want
#uncomment this line to actually perform the restart
#shutdown -r 0
#probably a bad idea without first checking who's logged in, etc.
fi

```

I think it might work, not quite sure though as I haven't had the opportunity to test this out yet...those lazy linux developers haven't released any kernel updates this afternoon : )

a secondary idea, which is a bit simpler (and i think more likely to tell you a restart is required when it really isn't), is to check the timestamps of the grub menu, and compare it with uptime, to see if it's been changed since the system last booted.

Feedback, anyone?

---

### Post by nitrogoldfish on 2009-07-14
Turns out one of my servers hadn't been updated since the last kernel patch, so i could test this after all...also turns out that my first idea didn't work. The running version of the kernel and the installed version seem to both be the same, despite just installing an update that requires a restart to become active. oh well.

the 2nd idea, checking the timestamps of /boot/grub/menu.lst looks like it should work: the updated timestamp matched the time i ran the update.

If you want to get the timestamp, you can use
```

ls -l /boot/grub/menu.lst | awk '{print $6" "$7":00"}'

```
compare to output of uptime, and see if you need a restart. There are a number of things that could throw this off, but it's better than nothing, so I'm going to call that my not-perfect-but-good-enough solution for now. Hope it helps

---

### Post by abadr on 2010-02-24
Not exactly an answer but an observation: On my backup server that doesn't have a GUI install, I'm running Byobu (an improved version of 'screen'). After a kernel upgrade Byobu gave me an alert in its status bar that I need to reboot. So there must be something flagged in the system for that purpose.

---

### Post by MonkeyZiggurat on 2010-04-19
I seem to remember my server used to say *restart required* or something similar when I logged into it via ssh. That was before I changed my motd welcome message, though. Had to come from somewhere.

---

### Post by richardjh on 2010-04-19
Hi netJackDaw

The simple answer to your simple question is to check for the existence of the file

```
/var/run/reboot-required
```as neel.d correctly pointed out in reply #15.

Another useful file is 

```
/var/lib/update-notifier/updates-available
```If that exists, then updates are available.

See [_this link_]("http://serverfault.com/questions/92932/how-does-ubuntu-keep-track-of-the-system-restart-required-flag-in-motd/92940#92940") too. 

You could run a daily script in cron to get email alerts of required reboots like this

```
00 08 * * * /usr/local/sbin/email_update_required
```And put this into /usr/local/sbin/email_update_required

```
if [ -f /var/run/reboot-required ]; then
    echo "A reboot is required following updates to server `hostname`" | mail -s "Reboot Required" admin@your-domain.com
fi
```

Make sure the file is executable and you are good to go.

Or you could put something in your ~/.bashrc file that notifies you when you log in. Edit ~/.bashrc and add this:

```
if [ -f /var/run/reboot-required ]; then
    echo "A reboot is required following updates.\n"
fi
```

---

### Post by Vegan on 2010-04-19
> **netJackDaw said:**
> I've seen this question asked a few times but never really answered...

When you run a desktop installation of Ubuntu you will get an icon that tells you a system restart is required if there are updates that require that. When you run a server with only cli you don't get this feedback from the system. So I would like to ask the system if it needs a restart. Is there a file a can look in or a command I can launch to get this information?

I am not interested in a discussion whether or not you should restart your server based on what was upgraded. I know that basically only kernel updates require restart.

I reboot my server with a cron job whether it needs it not not.

My server is lean and mean enough to reboot faster than a browser times out.

---

### Post by zfreak7c5 on 2010-04-20
> **MonkeyZiggurat said:**
> I seem to remember my server used to say *restart required* or something similar when I logged into it via ssh. That was before I changed my motd welcome message, though. Had to come from somewhere.

That is landscape-sysinfo by default, at least in Ubuntu Server it will notify you of a required reboot when you login, it can be ran separately though as well.  It seems to update on a schedule though so won't tell you right after installing updates, does shortly after though.

---

### Post by subssn594 on 2011-09-09
> **neel.d said:**
> Hi, this is my 1st post on the forum. Please bare with me if my post is off the mark.

i found a script on the machine: 
"/usr/share/update-notifier/notify-reboot-required"

my understanding is, if the reboot is required, then this script is invoked. it will touch a file:
"/var/run/reboot-required"

if this file is present on the system, then restart the system.

Please let me know if this is the right answer.

cheers.. :D

This is the right answer.  To get /usr/share/update-notifier/notify-reboot-required without installing a GUI, install update-notifier-common.

---

### Post by nothingspecial on 2011-09-09
Use byobu and set restart required to be displayed in the notification area.

**EDIT** Not again, this thread's three years old!!!

---

### Post by masuch on 2011-09-28
> **neel.d said:**
> Hi, this is my 1st post on the forum. Please bare with me if my post is off the mark.

i found a script on the machine: 
"/usr/share/update-notifier/notify-reboot-required"

my understanding is, if the reboot is required, then this script is invoked. it will touch a file:
"/var/run/reboot-required"

if this file is present on the system, then restart the system.

Please let me know if this is the right answer.

cheers.. :D


Excellent. thanks a lot - I have been looking for it.

---

### Post by beradero on 2011-10-13
But this files seems not to exist anymore.. There is no "/usr/share/update-notifier/notify-reboot-required" in my Ubuntu Server 10.10.

---

### Post by neel.d on 2011-10-16
> **beradero said:**
> But this files seems not to exist anymore.. There is no "/usr/share/update-notifier/notify-reboot-required" in my Ubuntu Server 10.10.

As subssn594 mentioned in reply #24, could you please check if you have package 'update-notifier-common' installed? This package will provide '/usr/share/update-notifier/notify-reboot-required'

---

