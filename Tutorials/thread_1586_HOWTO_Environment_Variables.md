---
title: "HOWTO: Environment Variables"
date: 2004-10-22
forum: Tutorials
---

### Post by gecko on 2004-10-22
This thread is now closed. The information can be found on the wiki here

[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)




[size=6]Environment Variables[/size]

**Environment variables for a specific command**
To set a variable for just a one off you can specify the variable on the command line itself as follows...

NAME=VALUE COMMAND PARAMETERS

Example
http_proxy=http://localhost:8080/ apt-get update

NB: You can have multiple name=value pairs seperated by spaces.

**Environment Variables for the shell/command line**
To permanently add an environment variable you add the following lines to the relevant rc file. Th rc file is read whenever a terminal is opened from the ubuntu desktop. For a program that runs as a specific user you need to add them to the /home/username/.bashrc file. For programs that require sudo access you add these lines to the /root/.bashrc file.

NAME=VALUE
export NAME

Example

http_proxy=http://localhost:8080
export http_proxy

**Environment variables for the gnome desktop**
To permanently add variables for the Gnome desktop, you add lines to the ??? file. Please add this information.

**Contribute!**
If you find more information on environment variables then please add them as a reply to this post. Corrections should be sent to the author of his or her post.

Gecko

---

### Post by adamw523 on 2004-10-22
Environment variables for gnome desktop:

This worked for me:

edit file: /etc/gdm/gdm.conf 
add your path to the "DefaultPath" line

example of adding Java /bin to path:
```
# Default path to set.  The profile scripts will likely override this
DefaultPath=/usr/local/bin&#58;/usr/local/sbin&#58;/sbin&#58;/usr/sbin&#58;/bin&#58;/usr/bin&#58;/usr/bin/X11&#58;/usr/games&#58;/usr/local/java/bin

```

---

### Post by Neo40 on 2004-10-24
[QUOTE=adamw523]Environment variables for gnome desktop:

This worked for me:

edit file: /etc/gdm/gdm.conf 
add your path to the "DefaultPath" line

example of adding Java /bin to path:
```
# Default path to set.  The profile scripts will likely override this
DefaultPath=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games:/usr/local/java/bin

```[/QUOTE]


Well, it's not working for me. My java is in /usr/local/j2re1.4.2_05/bin. So, I just added this in /etc/gdm/gdm.conf as you said but when I log back and I type "which java" I see nothing! I also tried to add this line in my ~/.bash_profile:

export PATH=$PATH:/usr/local/j2re1.4.2_05/bin

But it's still loosing it when I reboot. What I'm doing wrong??

Thanks.

---

### Post by gecko on 2004-10-24
Try your ~/.bashrc file. 

Please turn on private messaging so I can privmsg replies to your questions.

Gecko

---

### Post by offby1 on 2004-12-26
More effective (Apparently) is adding them to /etc/environment.

exporting is not required there.

---

### Post by ekricyote on 2007-08-18
Is this a catch all situation for most Linux distributions? I tried editing a PATH variable in /etc/profile and wound up unable to ls or sudo (silly me, I forgot the /bin directory, let alone /sbin).

In these scripts, would just declaring the variable work or do I have to use export keyword?

e.g is it this

export PATH=" ... "

or this

PATH = " ... "

I've seen some scripts do this as well in /etc/profile. Any comments on it?

PATH=" ... "
export PATH

---

### Post by DarkBattM14 on 2012-09-13
> **gecko said:**
> [SIZE=6]Environment Variables[/SIZE]

**Environment variables for a specific command**
To set a variable for just a one off you can specify the variable on the command line itself as follows...

NAME=VALUE COMMAND PARAMETERS

Example
http_proxy=http://localhost:8080/ apt-get update

NB: You can have multiple name=value pairs seperated by spaces.

**Environment Variables for the shell/command line**
To permanently add an environment variable you add the following lines to the relevant rc file. Th rc file is read whenever a terminal is opened from the ubuntu desktop. For a program that runs as a specific user you need to add them to the /home/username/.bashrc file. For programs that require sudo access you add these lines to the /root/.bashrc file.

NAME=VALUE
export NAME

Example

http_proxy=http://localhost:8080
export http_proxy

**Environment variables for the gnome desktop**
To permanently add variables for the Gnome desktop, you add lines to the ??? file. Please add this information.

**Contribute!**
If you find more information on environment variables then please add them as a reply to this post. Corrections should be sent to the author of his or her post.

Gecko


Ohhh!!! Thanks!! this help me a lot!!! :popcorn::popcorn::popcorn:

---

### Post by sisco311 on 2012-09-13
[[img]http://ompldr.org/tYnpyNw[/img]](http://ompldr.org/vYnpyNw)

Thread closed.

---

