---
title: "Linux Easter Eggs"
date: 2015-04-04
forum: The Cafe
---

### Post by cariboo on 2015-04-04
I ran into an article about Linux Easter Eggs last night, that had one I hadn't seen before.

Insult Users with sudo. 

You can configure sudo, used to elevate the privileges of a command, to insult users when they type in an incorrect password.
To do so, edit the sudoers file with a tool called visudo, which edits and validates modifications to the sudo configuration file.

```
sudo visudo
```

Near the top add a line:

```
Defaults insults
```

Save and close the file.

Next, empty the cache that stores your password for a certain amount of time and then mistype your password for a sudo command:

```
sudo -k
sudo ls
```

```
cariboo@skynet:~$ sudo ls
[sudo] password for cariboo: 
Pauses for audience applause, not a sausage
[sudo] password for cariboo: 
You type like I drive.
```

Has any one else run into any Easter eggs aside form the usual?

---

### Post by d-cosner on 2015-04-04
Watch Star Wars in the terminal!

```
telnet towel.blinkenlights.nl
```

Just copy and paste into the terminal and enjoy! :)

---

### Post by oldos2er on 2015-04-06
> **cariboo907 said:**
> I ran into an article about Linux Easter Eggs last night, that had one I hadn't seen before.

Insult Users with sudo. 

This is actually one of the first things I do on a fresh install. Not an easter egg, but you can also add pwfeedback if you want to see asterisks in terminal when you type in your password.

---

### Post by ethan26 on 2015-04-07
> Watch Star Wars in the terminal!
```

     telnet towel.blinkenlights.nl 
```
Just copy and paste into the terminal and enjoy! :smile:
this is not just a linux easter egg. besides the fact that on some systems you have to installl the telnet command it works on all pcs.

---

### Post by d-cosner on 2015-04-07
Yeah but it's still kind of cool and not a lot of people know about it.

---

### Post by Habitual on 2015-04-07
> **d-cosner said:**
> Watch Star Wars in the terminal!

```
telnet towel.blinkenlights.nl
```

Just copy and paste into the terminal and enjoy! :)
BoFH excuse generator on the same host:
```
telnet towel.blinkenlights.nl 666
``` Some of them are actually passable to uninformed users, not that I'd *ever* do that! :wink:

"Defaults insults" didn't work as described on Ubuntu 14.04.1 LTS server for some reason, yes, I restarted ssh and did a sudo -k

```
openssh-server:
  Installed: 1:6.6p1-2ubuntu2
```

Visudo dork, not /etc/ssh/sshd_config

---

### Post by portalhavoc on 2015-04-07
Android  (Which is a Linux-based OS) has had some pretty interesting easter eggs since Android 2.3 Gingerbread. 

My favorite has to be the Jelly Bean one where you get to throw jelly beans across the screen. :)

---

### Post by ethan26 on 2015-04-07
how do you the jelly bean thing. I need to know!

---

### Post by portalhavoc on 2015-04-07
To do it you need to go into the settings, open "About Phone or Tablet" press the Android version number about 20 times and press on the jelly bean and there you go!

---

### Post by john387 on 2015-04-17
heheh...some fun ones here!

---

