---
title: "Password prompts"
date: 2014-10-15
forum: Security
---

### Post by Vassilis on 2014-10-15
[COLOR=#000000]Hello there,

[/COLOR]i am reposting here as this seems a more appropriate forum than the general help.

[COLOR=#000000]I recently installed Ybunutu 14.04 on an old laptop and I am getting sick and tired of the constant password prompts when trying to install/uninstall software etc. Can someone please tell me how to disable those prompts? What I have tried so far is going through a terminal, entering the command sudo visudo and editing the file at the line [/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]%admin ALL=(ALL) ALL
[/FONT][/COLOR][COLOR=#000000]to[/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]%admin ALL=(ALL) NOPASSWD: ALL.
[/FONT][/COLOR][COLOR=#000000]That had no effect whatsoever. Is there another way? I am still getting those annoying prompts. I understand it can be somewhat a security risk to turn them off but this is a single user old laptop with practically nothing in it. I am only using it to play with linux and learn some python.[/COLOR]

---

### Post by The Cog on 2014-10-15
You pretty-much can't turn them off. They serve the same function as they do in windows - protect your computer from system changes by unauthorised users or trojans.
When you have finished your initial system tweaking, you should be able to settle into just being a normal user and you won't bump up against the password prompt so often.

There should be a timer that only re-requests your password after 15 minutes anyway, so the password prompts are not "constant". 
If you know you are going to be issuing a lot of commands as root, you can always use "sudo -i" in a command prompt, which gains you root privilege until you exit again. That way, you don't even need to use "sudo" in front of the commands you issue.

---

### Post by HermanAB on 2014-10-15
Two things:
1. You'll get used to it.
2. Use KeepassX

---

### Post by Vassilis on 2014-10-15
I didn't mean when issuing commands. In that case I know about the sudo -i "workaround". I meant when using the desktop. This is where it gets annoying, not in the terminal.
I was thinking maybe I can be logged in as the superuser root constantly. That should get rid of them right?

---

### Post by ajgreeny on 2014-10-15
> **Vassilis said:**
> I didn't mean when issuing commands. In that case I know about the sudo -i "workaround". I meant when using the desktop. This is where it gets annoying, not in the terminal.
I was thinking maybe I can be logged in as the superuser root constantly. That should get rid of them right?
In theory, yes, you could do that.

However it is a very dangerous way to use a computer as there will be no security "fence" around the whole OS.  You will not get any help here on the forum on how to enable the root account, which is disabled by default, and if I, or any other person attempted to tell you how, that post would be removed by the forum mods, I think.

Just accept that one of the reasons why Linux is secure is the password requirement to do anything that affects the OS itself; you can do whatever you like to your own files and folders in your home, but the OS is more protected from that kind of activity.

You'll soon get used to it, and once you have set up the OS as you want it, it will normally be only for installing/uninstalling and updating packages that you need a password.

---

### Post by The Cog on 2014-10-15
It would, but you really should not do that. It is disabled in the default install, and I don't know how to enable it (and don't want to know). 

As HermanAB says, you'll get used to it. And as I said, once you have the system bedded down you won't be making constant changes to the system configuration anyway.

---

### Post by Vassilis on 2014-10-15
> **ajgreeny said:**
> Just accept that one of the reasons why Linux is secure is the password requirement to do anything that affects the OS itself; you can do whatever you like to your own files and folders in your home, but the OS is more protected from that kind of activity.

You'll soon get used to it, and once you have set up the OS as you want it, it will normally be only for installing/uninstalling and updating packages that you need a password.

As I said in the first post I realise the possible security risks arising from what I am asking and that this is one of the features that makes Linux much safer than Windows. The way I see it though, what Linux offers compared to other OS is exactly the fact that it gives you the power to do anything. That is why I installed it and I do not want it blocking me from doing things "for my own good". Besides what's the worst case scenario? I do something I shouldn't have, destroy the OS, format the HDD and reinstall a fresh Ubuntu copy. Big deal. I have been googling this thing for two days now and all I see is the same response "I could tell you how but I won't because you shouldn't do it". Honestly I appreciate the concern but please let me destroy my computer if I want to. :)
Maybe I have the wrong idea here but I thought the point of the Linux community is in part to teach noobs like me stuff, not to refuse to share information in order to "protect" them.

---

### Post by Impavidus on 2014-10-15
I'm also on a single user laptop and I like those password prompts. They remind me when I have to think twice before doing something.

By default there is a 15 minute timeout. If you use another sudo command in the same terminal within 15 minutes you won't get a new password prompt. If you wish, you can increase the timeout period. You can also use **sudo -i** to get a root shell. Then you don't have to use sudo or type any passwords to do anything as root until you terminate the root shell by typing **exit**.

A graphical package manager like synaptic asks the password once when you start the program, then you can keep it open for as long as you want. I'm not sure about the software centre, as I never use it.

Once you have installed all applications you want and have the system set up to your likings, you don't need sudo and those command prompts very often.

---

### Post by Iowan on 2014-10-15
> **Vassilis said:**
> 
Maybe I have the wrong idea here but I thought the point of the Linux community is in part to teach noobs like me stuff,...Perhaps you've missed the point of what they're trying to teach you...

> **Vassilis said:**
> i am reposting here as this seems a more appropriate forum than the general help.You can use the **Report Post** button to request to have a thread moved. :)

---

### Post by ajgreeny on 2014-10-15
> **Vassilis said:**
> 
Maybe I have the wrong idea here but I thought the point of the Linux community is in part to teach noobs like me stuff, not to refuse to share information in order to "protect" them.
It is, but as I said in my post above, this forum has rules and one of those is that any information we give has to abide by the Ubuntu and forum philosophy, ie a root account is not the way to do things.

Google is your friend if you feel you must pursue this; this forum, however, is not allowed help you.

---

### Post by cortman on 2014-10-15
We don't want you to bork your system. But you have the perfect right to if you desire. :) In respect of that, here's a blog post that should explain how to accomplish your goal. <snip>
Enjoy learning Linux.

---

### Post by jamesisin on 2014-10-15
You should always prefer to use sudo and gksudo.  There is little to no reason to ever enable the root user account in an Ubuntu system (or really any system similarly designed to take advantage of sudo).  Here is everything you might need to know about sudo and root.  Don't blame us if someone takes control of your machine and uses as their cyber-puppet.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by oldos2er on 2014-10-15
> **Vassilis said:**
>   I have been googling this thing for two days now and all I see is the same response "I could tell you how but I won't because you shouldn't do it". 

Keep googling; info on how to enable the root account (and therefore essentially always run as root) is not a secret (hint: check Ubuntu's online documentation). We can't support it here though because it's poor practice.

---

### Post by cariboo on 2014-10-15
My feeling is that if you have to ask here, on how to enable the root account, you aren't ready to use it.

---

### Post by coffeecat on 2014-10-15
> **cortman said:**
> We don't want you to bork your system. But you have the perfect right to if you desire. :) In respect of that, here's a blog post that should explain how to accomplish your goal. <snip>

I've removed the link in accord with our login as root policy:

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

@OP, you might want to read that. You are being given good advice. You are welcome to compromise the Ubuntu security model in your own system, but when you do and if you turn your system into a bot distributing malware, please do us all a favour and stay off the internet with it.

---

