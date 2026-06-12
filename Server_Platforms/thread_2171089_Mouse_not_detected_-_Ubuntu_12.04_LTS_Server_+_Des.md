---
title: "Mouse not detected - Ubuntu 12.04 LTS Server + Desktop interface"
date: 2013-08-29
forum: Server Platforms
---

### Post by GMHilltop on 2013-08-29
I am still learning all the command line stuff which is why I don't just run the Server alone.

I am ultimately looking at installing Squid3 as a proxy, and was thinking that running the server edition would be the best way to go.

As I am still learning I found this link that show you how to install the Desktop interface without all the extras:

[http://www.ubuntugeek.com/how-to-install-gui-on-ubuntu-12-04-precise-server.html](http://www.ubuntugeek.com/how-to-install-gui-on-ubuntu-12-04-precise-server.html)

I used:  sudo apt-get install --no-install-recommends ubuntu-desktop

When I rebooted, the mouse was not detected, and I haven't been able to figure out how to get to terminal using just the Keyboard in order to install whatever it is I need to to get the mouse detected and working.

I can reinstall again I guess, I was just wondering if there was a way to get the mouse working from where I am at so I can still use the:
sudo apt-get install --no-install-recommends ubuntu-desktop
option.  Any Ideas?

It is being installed on a little Asus EEE box - EB1033.

---

### Post by nerdtron on 2013-08-29
If you get a keyboard working press Alt+F2 and type terminal. The default terminal can be launched there. If you don't Press CTRL+ALT+F2 and get to a tty terminal, login using username and password and you'll be able to run commands.
Also, why bother installing a GUI? You can just remotely access your server from your own desktop computer.

---

### Post by 1/0 on 2013-08-29
> **nerdtron said:**
> If you get a keyboard working press Alt+F2 and type terminal. The default terminal can be launched there.
Or by pressing [Ctrl] + [Alt] + [t].

Double check that everything got installed ok by:

```
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get update --fix-missing
```

I'm wondering what went wrong. If for instance 

```
sudo dpkg-reconfigure ubuntu-desktop
```

would help. Is it a usb connected mouse? Is it not recognized or "does it not work"?

---

### Post by GMHilltop on 2013-08-29
> **nerdtron said:**
> If you get a keyboard working press Alt+F2 and type terminal. The default terminal can be launched there. If you don't Press CTRL+ALT+F2 and get to a tty terminal, login using username and password and you'll be able to run commands. Also, why bother installing a GUI? You can just remotely access your server from your own desktop computer.  Thanks for the response nerdtron.  I'll give that a try. As I am still learning my way around using commands, sometimes I'd find it easier using the GUI to do simple things.  That is why I tried installing the non-full-blown version - which I wondered if that had something to do with why the mouse wasn't detected.  As far as accessing the server  from my desktop, are you referring to using PuTTY, Webmin, a GUI interface FROM my desktop, or something else? What did you have in mind?  Playing with the server side of things is new to me at the moment so the learning curve is a little steeper at the moment. Any suggestions are more than appreciated. Thanks.

---

### Post by GMHilltop on 2013-08-29
> **1/0 said:**
> Or by pressing [Ctrl] + [Alt] + [t].

Double check that everything got installed ok by:

```
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get update --fix-missing
```

I'm wondering what went wrong. If for instance 

```
sudo dpkg-reconfigure ubuntu-desktop
```

would help. Is it a usb connected mouse? Is it not recognized or "does it not work"?

Thanks 1/0 for jumping in.  Yes it is a USB mouse and it WAS connected when I installed the Desktop GUI.
I'll give those commands a try.

By the way, does anyone have a Good 'Cheat Sheet' that covers a large majority of commands one can use in terminal and what the . . . switches (?) or options are (sorry, I'm not sure what the official term is for the -f -v -l etc, etc, is ).

Thanks

---

### Post by nerdtron on 2013-08-29
> **GMHilltop said:**
> Thanks for the response nerdtron.  I'll give that a try. As I am still learning my way around using commands, sometimes I'd find it easier using the GUI to do simple things.  That is why I tried installing the non-full-blown version - which I wondered if that had something to do with why the mouse wasn't detected.  As far as accessing the server  from my desktop, are you referring to using PuTTY, Webmin, a GUI interface FROM my desktop, or something else? What did you have in mind?  Playing with the server side of things is new to me at the moment so the learning curve is a little steeper at the moment. Any suggestions are more than appreciated. Thanks.

PuTTY? If you are using windows then you might as well ignore my suggestion in remote access :)
If you are in Linux, you can always access the server from your desktop via:
command line - ssh user@serverIP
file browser - type sftp://user@serverIP in the location field of your file browser to access the filesystem of the server

And here's a free ebook. [http://www.rigacci.org/docs/biblio/offline/TLCL-09.12.pdf](http://www.rigacci.org/docs/biblio/offline/TLCL-09.12.pdf) 
I don't like reading but this one is very easy to read and follow even from a complete beginner. It won't help you how to setup samba share or access databases but it will teach you the command line basic so that you'll be much more comfortable living on the command line.

---

### Post by 1/0 on 2013-08-30
> **GMHilltop said:**
> By the way, does anyone have a Good 'Cheat Sheet' that covers a large majority of commands one can use in terminal and what the . . . switches (?) or options are (sorry, I'm not sure what the official term is for the -f -v -l etc, etc, is ).

Here are two, one for ubuntu and the other one for bash. 

[http://forum.pinguyos.com/attachment.php?aid=407]("http://forum.pinguyos.com/attachment.php?aid=407")

[http://cli.learncodethehardway.org/bash_cheat_sheet.pdf]("http://cli.learncodethehardway.org/bash_cheat_sheet.pdf")

---

### Post by GMHilltop on 2013-08-31
> **nerdtron said:**
> PuTTY? If you are using windows then you might as well ignore my suggestion in remote access :)
If you are in Linux, you can always access the server from your desktop via:
command line - ssh user@serverIP
file browser - type sftp://user@serverIP in the location field of your file browser to access the filesystem of the server

NO WAY!  That is soooo cool - I didn't know you could do that! THANKS =D>
Yeah, we are using windows, but I am slowly trying to migrate over.

> **nerdtron said:**
> And here's a free ebook. [http://www.rigacci.org/docs/biblio/offline/TLCL-09.12.pdf](http://www.rigacci.org/docs/biblio/offline/TLCL-09.12.pdf) 
I don't like reading but this one is very easy to read and follow even from a complete beginner. It won't help you how to setup samba share or access databases but it will teach you the command line basic so that you'll be much more comfortable living on the command line.

This too is REALLY REALLY Good!
All along I'd just google for a command to make something happen, but I never really knew much about 'why' it was working.
I didn't really like operating that way, but I just lived with it hoping to fill in the missing pieces as I went along. This pdf is excellent!
Thank You again.

Oh, and by the way, I restarted the system, and the mouse started working! I don't know why, but it did and I never got the chance to try anything else.

---

### Post by GMHilltop on 2013-08-31
> **1/0 said:**
> Here are two, one for ubuntu and the other one for bash. 

[http://forum.pinguyos.com/attachment.php?aid=407](http://forum.pinguyos.com/attachment.php?aid=407)

[http://cli.learncodethehardway.org/bash_cheat_sheet.pdf](http://cli.learncodethehardway.org/bash_cheat_sheet.pdf)

Thanks 1/0 - these I am going to keep close by as well.  Cheers!

---

