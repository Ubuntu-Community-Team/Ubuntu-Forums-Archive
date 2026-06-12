---
title: "Invoke script on boot by pressing key"
date: 2011-05-01
forum: Server Platforms
---

### Post by Cha0sgr on 2011-05-01
Hello everyone,

I have created a script which asks the user a few questions and then it configures the wireless network.

I'd like to run it somehow while Ubuntu still boots by pressing a key for example.


Let's say, while booting, when it comes to the script I made, it will sleep for a few seconds giving the user the oportunity to press the pre-defined key (eg: spacebar).
Once pressed, then the script will load.

Can you give me the right directions on how to implement such a feature?

Also a 'beep' sound just when the user is supposed to press the pre-defined key would be ideal :)


Thank you all for your time in advance!

Regards,
Vaggelis.

---

### Post by elico on 2011-05-01
it depends on the place and the role you want it to do.
you can use the "read" command using a timeout as :

> 
#!/bin/bash
echo "beep1"
beep C
echo "beep1"
beep C
#echo "starting menu"
DEFSEL=0
echo "1. net down + wrieless down"
echo "2. net up +wireless down"
echo "3. net up + wireless up"
echo "enter number and press enter:"
echo -n "you have 10 sec to choose:  "
read -t10 DEFSEL




---

### Post by Cha0sgr on 2011-05-02
Hello elico,

Thanks for your reply :)

I will check it out and let you know.

---

### Post by Cha0sgr on 2011-05-02
Hello again,

read command did the trick! Thanks mate :)


beep on the other hand does not work. I tested it on a VM and on an old laptop but I can't get it to work.

It's not that important anyway so I will check it out later...


The problem now is that all this seems to have been done the wrong way...
When ubuntu boots, I get the 'Press any key' message I wanted but if I press any key, the keystroke goes to tty1 but the output of the script is printed on tty7.


If I switch to tty1 and press something and switch back to tty7 then I the script get's what was sent over tty1.

In other words, the script output is on tty7 but the input is on tty1.

Any ideas on which is the proper way of having an interactive init script at startup?

I also tried /etc/rc.local file instead of a typical init script but the I get the same exact behavior.

---

### Post by Cha0sgr on 2011-05-02
I tried to explain what I want to do to some friends and they seem to be confused with how I wrote this post so maybe it will be of help that what I want to do is a 'firstboot' equivalent of CentOS but just for wireless configuration by invoking my wireless-config script I wrote.

The first time it boots just before the login screen, a utility pops up and lets the user configure some basic stuff on the CentOS installation.

This is what I need actually but on Ubuntu Server.

---

### Post by koenn on 2011-05-02
re the tty1 and tty7 thing - I assume that's just all output being redirected to tty7, because that's where X will run. I assume nobody expected to have to deal with input on tty7 because X server will handle it.

Which brings us to the core of the matter : init scripts are expected to run without user input. 

If you want user input, your desktop environment or your desktop manager should offer you facilities for that. 

Also, be aware that init scripts run as root. Making them interactive might, in some circumstances, provide a way to drop to a root shell. You don't want that.



If this script only needs to run once (succesfully), I'd make it a normal init script, and let it check for a marker : the existence of an arbitrary file, o given value in a certain file, .... If that marker is found, exit. If it isn't there, set it after successful completion of the other commands in the script.

---

### Post by elico on 2011-05-02
fot the beep there is another nice trick using print or echo.. better use print:
> printf \\awill beep on any terminal tty or pts your are using now and the script is running on
if you want to let say send beep to specific terminal such as in the boot it sould be 
> printf \\a >>/dev/tty1and on ssh
or you can use some to all tty or all pts using a xargs something

> printf \\a >>/dev/pts/0 0 = number of terminal or:
> printf \\a >> $SSH_TTY

---

### Post by Cha0sgr on 2011-05-03
Hello again guys,

Thank you for your replies.

We dismissed the method I was asking about since it seems to be more complicated that we thought.


Thanks for your infos though! I learned a couple of new stuff (read, beep) :)


Keep up the good work guys!

Vaggelis.

---

