---
title: "How to completely reinstall lightdm"
date: 2018-02-07
forum: Ubuntu/Debian BASED
---

### Post by mattdiamond17 on 2018-02-07
Hello. Yesterday i tried to install a theme for lightdm. I "installed" :( and then when rebooting, for some reasons, it was stuck on the splash screen of elementary os. So i've opened elementary in recovery mode and then i managed to install gdm and i've booted into my system. I searched all the day for a way to install lightdm, but every solution that i founded haven't worked. Currently i'm with gdm but i don't like how it looks(don't ask) and i want to replace with lightdm. How can i do that. Every time when i try to install lightdm again from the terminal, the installation freezes at 0% and stays like that for hours. Can someone please help me? I am using elementary os Loki 0.4.1 64 bit

---

### Post by deadflowr on 2018-02-07
*Thread moved to **Ubuntu/Debian BASED***

---

### Post by tinylagarto on 2018-02-07
Is lightdm installed right now?

```
apt policy lightdm

```
from the terminal will tell us.

How did you install lightdm?

To install:

```
sudo apt install lightdm

```
If you want to change the login manager, proceed like this:

```
sudo dpkg-reconfigure lightdm

```
to change the defaults.

Normally when you install another login manager you will be asked which one to use.  

I guess that should work in the same manner on ElementaryOS. 

I posted some terminal commands because they work on any system in the same way. You could of course install lightdm from your app or software center.

---

### Post by mattdiamond17 on 2018-02-08
So, this is what i get after running the first command: 

lightdm:
  Installed: 1.18.3-0ubuntu1.1
  Candidate: 1.18.3-0ubuntu1.1
  Version table:
 *** 1.18.3-0ubuntu1.1 100
        100 /var/lib/dpkg/status
     1.18.1-0ubuntu1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 Packages


And if I remember good, i've installed with sudo apt-get install lightdm, after running sudo apt-get purge lightdm. Is this good?
Oh and if it helps, with lightdm selected it says while booting: Failed to start Light Desktop Manager. I think that means that lightdm can't start.

---

### Post by again? on 2018-02-08
What is your output for...
```
lightdm --show-config
```

---

### Post by mattdiamond17 on 2018-02-08
It says:

Failed to load configuration from /etc/lightdm/lightdm.conf: Key file does not start with a group

sorry, but i don't know how to put my commands like you have done

---

### Post by again? on 2018-02-08
Output for...
```
cat  /etc/lightdm/lightdm.conf
```
To put in code blocks when replying see [HERE]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168").
Basically reply in advanced mode, paste in your output, highlight the text with left mouse and then hit the "#" icon.

---

### Post by mattdiamond17 on 2018-02-08
Output:

```

greeter-session=lightdm-webkit-greeter

```

Thanks for the link!

---

### Post by again? on 2018-02-08
> **mattdiamond17 said:**
> It says:

Failed to load configuration from /etc/lightdm/lightdm.conf: Key file does not start with a group

sorry, but i don't know how to put my commands like you have done

> **mattdiamond17 said:**
> Output:

```

greeter-session=lightdm-webkit-greeter

```

Thanks for the link!
As shown in error output, "/etc/lightdm/lightdm.conf" does not have a group heading and should look like this...
```
[Seat:*]
greeter-session=lightdm-webkit-greeter
```

This command will correct the file...
```
echo -e "[Seat:*]\ngreeter-session=lightdm-webkit-greeter" | sudo tee /etc/lightdm/lightdm.conf
```

Then try again...
```
lightdm --show-config 
```

---

### Post by mattdiamond17 on 2018-02-08
OK. Thanks a lot for the reply.

So here is my output:
```

   [Seat:*]
B  greeter-session=lightdm-webkit-greeter


Sources:
A  /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
B  /etc/lightdm/lightdm.conf



```

It is good?

---

### Post by again? on 2018-02-08
Is lightdm still installed?
```
apt policy lightdm
```

Not familiar with loki.
Doesn't it have a pantheon-greeter for lightdm?
Did you install **lightdm-webkit-greeter** in an effort to change the greeter?

---

### Post by again? on 2018-02-08
I'm off to bed so I'll leave you with some info.
[https://www.freedesktop.org/wiki/Software/LightDM/](https://www.freedesktop.org/wiki/Software/LightDM/)
[https://wiki.archlinux.org/index.php/LightDM](https://wiki.archlinux.org/index.php/LightDM)

I would delete /etc/lightdm/lightdm.conf which is a sort of master admin config that overrides settings in /usr/share/lightdm/lightdm.conf.d

You greeter-session used will then be what's shown by configs in /usr/share/lightdm/lightdm.conf.d, higher numbered files taking precedence.
Your "lightdm --show-config" output shows that /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf will now be the source for your lightdm config.

Try to use lightdm again...
```
sudo rm /etc/lightdm/lightdm.conf
```
```
sudo apt install lightdm lightdm-gtk-greeter
sudo dpkg-reconfigure lightdm
```

---

### Post by mattdiamond on 2018-02-19
Still not working :( I eventually switched to windows back becuase of software compatibility... Thanks!!

---

