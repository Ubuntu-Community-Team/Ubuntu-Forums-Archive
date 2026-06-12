---
title: "LKL (Linux KeyLogger)"
date: 2009-11-25
forum: Security
---

### Post by schlep3 on 2009-11-25
I'm not sure if this is the proper section to put this, so I apologize beforehand if it isn't.


So it was brought to my attention that there could possibly be a keylogger installed on my system. I did some Google searches and for a while, I didn't find anything. Then, I stumbled upon this little program called LKL.

[COLOR=Red][SIZE=4][I][B]PAUSE. A little back story that ties in later;

[/B][/I][SIZE=1][COLOR=Black]For about the past week or so, my keyboard and mouse were acting funny. The keyboard would sometimes not type the key i struck on the initial press, and a lot of the time it would repeat keys, example: If i were to type in a web address, let's say Google, I'd get "ggggggggggooooggle or googleeee." And my mouse would sometimes move/scroll on it's own and if I'd attempt to take control, It'd keep doing it, resulting in me having to restart my computer to stop it.


RESUME.

Anyway, so I found LKL and it struck me as odd that it was so.. available. There for anyone to download and use. I clicked the link, read through it and found some comments on the program, things such as repeating keys and mouse issues(as I typed above). I got curious, opened a terminal and typed in "sudo apt-get remove lkl".. lo and behold, there it was, asking me [Y/n] to go on with the uninstall. Meaning it WAS installed, right?

So my question is; Is it possible AT ALL for this to have been accidentally "leaked" into my system, installed due to a system breach, or is this a program you must manually install onto your system?
[/COLOR][/SIZE][/SIZE][/COLOR]

---

### Post by liquider on 2009-11-25
I don't think lkl is installed by default. Are you sure you didn't install it some time ago?

Anyway, should anyone have malicious intentions after already obtaining your root password, he could install lkl locally or conceal it otherwise, or install another rootkit altogether. I think. :)

Also, lkl is meant for you to keylog your own machine, hence the ease of availability. Serves me good. :P

---

### Post by schlep3 on 2009-11-25
I would never install something like this on my own machine, I have no need for it. But other people in the house do, apparently. 

If i were to check for other rootkits by running chkrootkit, what should I be looking out for?

---

### Post by liquider on 2009-11-25
I'm guessing
> not infected/not found/etc.
? :)

chkrootkit only finds known stuff and as such doesn't report similar home-brewed "apps".

I would check your /etc/rc.local and /etc/rcX.d/SXXwhatever and desktop startup configuration for any references to lkl being started.

For example
```

$ grep 'lkl' /etc/rc*.d/*

```

---

### Post by cariboo on 2009-11-25
If you allow other people to log into your system with sudo privileges, they could have installed the key logger.

For safties sake, change your password, lock your screen or log out when leaving the computer. 

If others need to use your computer create an account without admin privileges for them to use.

---

### Post by hallu on 2009-11-25
> **schlep3 said:**
> [COLOR=Red][SIZE=4][SIZE=1][COLOR=Black]
So my question is; Is it possible AT ALL for this to have been accidentally "leaked" into my system, installed due to a system breach, or is this a program you must manually install onto your system?
[/COLOR][/SIZE][/SIZE][/COLOR]

lkl is available in the repository btw

---

### Post by BkkBonanza on 2009-11-25
It sounds like someone installed this on your computer. Probably not an "expert hacker" or they would have put a rootkit in that would have prevented you from finding out.

You could try viewing the apt log to see if there are traces of when it occurred.

sudo less /var/log/apt/term.log

(it may be way back and then you have to dig deeper in archived logs)

For someone to install this without you knowing they would have to have admin rights. When you use sudo it is open for some minutes and if you left your machine then someone could sneak in and install it with one command. Or if they were helping you and you gave them the password they could have come back and done it. You should definitely change your password.

---

