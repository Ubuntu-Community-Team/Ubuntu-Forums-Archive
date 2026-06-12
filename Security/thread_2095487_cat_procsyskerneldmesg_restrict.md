---
title: "cat /proc/sys/kernel/dmesg_restrict"
date: 2012-12-17
forum: Security
---

### Post by Hungry Man on 2012-12-17
Any reason the default for ubuntu is 0?

Anyone tried setting it to 1 to restrict dmesg?

There's a grsecurity feature that restricts user access to dmesg, an unprivileged user can not read all but the last 4kb of the messages. It doesn't break anything as far as I can tell.

Does Ubuntu have this by default or what?

Edit: Enabled with 0 consequence. From everything I've read this should have been default a while ago, as in it was talked about but hasn't been from what I can tell.

Edit2: Further research pretty much confirms the above.

---

### Post by chadk5utc on 2012-12-17
This is an interesting point and worth reading. Ill have to think about this in my own systems for sure. All I have read indicate that its defaulted to off giving regular users access. Enabling it would be beneficial.

---

### Post by kleenex on 2012-12-18
Hi, is there any way to set this value to **1**? When I am trying to do it with sudo, I have got [COLOR=Green]bash: /proc/sys/kernel/dmesg_restrict: permission denied[/COLOR] message.

---

### Post by chadk5utc on 2012-12-18
the following will/should turn this on
> echo 1 > /proc/sys/kernel/dmesg_restrict

To verify
> cat /proc/sys/kernel/dmesg_restrict
should return
> 1

---

### Post by kleenex on 2012-12-18
Hi **chadk5utc**. I wrote that I've got an error. When I'm trying to change this value from **0** to **1** with sudo. It's all in my previous post! Maybe I will show You how it looks like:

```
[COLOR=Red]$[/COLOR] [COLOR=Green]sudo echo 1 > [/COLOR][COLOR=Green]/proc/sys/kernel/dmesg_restrict[/COLOR]
bash: /proc/sys/kernel/dmesg_restrict: Permission denied
```

Regards!

---

### Post by Bachstelze on 2012-12-18
```
echo 1 | sudo tee /proc/sys/kernel/dmesg_restrict
```

---

### Post by churchy d on 2012-12-18
you can do it as root

```

churchy-d@gator:~$ sudo su -
[sudo] password for churchy-d: 
root@gator:~# echo 1 > /proc/sys/kernel/dmesg_restrict 
root@gator:~# cat /proc/sys/kernel/dmesg_restrict 
1
root@gator:~# exit

```

i need to refresh myself on the finer details of sudo

---

### Post by chadk5utc on 2012-12-18
Sorry about leaving out the sudo I tend to take some things for granted and shouldnt.

---

### Post by churchy d on 2012-12-18
ok, now im confused, why would
```
echo 1 | sudo tee /proc/sys/kernel/dmesg_restrict
```
but not 
```
[COLOR=Green]sudo echo 1 > [/COLOR][COLOR=Green]/proc/sys/kernel/dmesg_restrict[/COLOR]
```

---

### Post by chadk5utc on 2012-12-18
Im not sure I can explain it I used echo 1 > ... but Im using another linux OS how ever I did google the differences and found a better explanation.
[http://techspalace.blogspot.com/2009/01/sudo-echo.html](http://techspalace.blogspot.com/2009/01/sudo-echo.html)

---

### Post by kleenex on 2012-12-18
Hi, it is working with [COLOR=Green]sysctl[/COLOR] command. Echoing does not work, because  the sudo only applied to the 'echo', not to the file were I was trying to write. 

```
[COLOR=Red]$[/COLOR] [COLOR=SeaGreen]sudo sysctl kernel.dmesg_restrict=1
[COLOR=Red]$[/COLOR] dmesg[/COLOR]
dmesg: klogctl failed: Operation not permitted
```

---

### Post by churchy d on 2012-12-18
ok, that makes sense, i assumed sudo applied to all the commands on that line, i guess it makes sense that it applies only to the command immediately following it though, thanks for the explanation.

---

### Post by JKyleOKC on 2012-12-18
> **churchy d said:**
> ok, now im confused, why would
```
echo 1 | sudo tee /proc/sys/kernel/dmesg_restrict
```
but not 
```
[COLOR=Green]sudo echo 1 > [/COLOR][COLOR=Green]/proc/sys/kernel/dmesg_restrict[/COLOR]
```The answer to your question is more arcane than most of what happens behind the scenes, but I'll try to explain it.

The ">" redirection actually opens a sub-shell of the command processor, and that sub-shell does **not** inherit the super-user capabilities of its parent. Thus you get "permission denied" from it.

Using echo to put the value into stdout, then piping it to a "sudo tee" command, gives the super-user capability to the "tee" command. This command echos its stdin input to the screen and at the same time writes it to the file named as an argument, achieving the desired result.

As I said above, more arcane than most -- but as Spock might observe, completely logical...

---

### Post by daKoolaid on 2013-02-21
Does the sudo tee command above make sure this is enabled on reboots?

---

### Post by CharlesA on 2013-02-21
> **daKoolaid said:**
> Does the sudo tee command above make sure this is enabled on reboots?

No idea, but if you want to make sure it gets enabled, you could always run the command as a cronjob with @reboot for the time to run.

---

### Post by daKoolaid on 2013-02-21
> **CharlesA said:**
> No idea, but if you want to make sure it gets enabled, you could always run the command as a cronjob with @reboot for the time to run.
I noticed that someone above said it works in sysctl, so I can add kernel.dmesg_restrict = 1 to sysctl.conf. 

Would that be better than putting the tee command in rc.local?

---

### Post by CharlesA on 2013-02-21
> **daKoolaid said:**
> I noticed that someone above said it works in sysctl, so I can add kernel.dmesg_restrict = 1 to sysctl.conf. 

Would that be better than putting the tee command in rc.local?

Probably.

---

### Post by kleenex on 2013-02-22
Hi **daKoolaid**. _In my opinion_, it is better to put this value to the [COLOR=Green]/etc/sysctl.conf [/COLOR]file, because I think, that all of the [COLOR=Green]sysctl's[/COLOR] should be placed right there. Of course, [COLOR=Green]/etc/rc.local [/COLOR]file is also a good place, but... I set this option on all of my computers by using [COLOR=Blue]sysctl kernel.dmesg_restrict=1[/COLOR] command and of course, I added this option to the [COLOR=Green]/etc/sysctl.conf [/COLOR]file. It's working after every reboot. Please remember, that [COLOR=Green]sysctl[/COLOR] offers many interesting options.

---

### Post by daKoolaid on 2013-02-24
> **kleenex said:**
> Hi **daKoolaid**. _In my opinion_, it is better to put this value to the [COLOR=Green]/etc/sysctl.conf [/COLOR]file, because I think, that all of the [COLOR=Green]sysctl's[/COLOR] should be placed right there. Of course, [COLOR=Green]/etc/rc.local [/COLOR]file is also a good place, but... I set this option on all of my computers by using [COLOR=Blue]sysctl kernel.dmesg_restrict=1[/COLOR] command and of course, I added this option to the [COLOR=Green]/etc/sysctl.conf [/COLOR]file. It's working after every reboot. Please remember, that [COLOR=Green]sysctl[/COLOR] offers many interesting options.
Thanks kleenex. That sums things up nicely.

---

### Post by kleenex on 2013-02-26
[LEFT]Welcome.
[/LEFT]

---

