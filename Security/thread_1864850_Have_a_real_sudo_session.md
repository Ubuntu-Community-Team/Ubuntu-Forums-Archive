---
title: "Have a real sudo session?"
date: 2011-10-19
forum: Security
---

### Post by biffta on 2011-10-19
Is there a way that after having entered my sudo password once, I am authorised for all tasks requiring elevated privileges? I've searched quite a bit on this subject and haven't found anything that solves my particular problem.

example:

I open a terminal and run (and successfully authenticate) 
```
sudo visudo
```
I then open another terminal and run
```
sudo visudo
```
where I am again prompted for the password. This is the same for graphical prompts as well, e.g. you install some software from the software centre close it, then realise you need something else. I'd like to at this point **not** have to re-enter the password provided it's within a certain timeframe.

I understand this would make my system less secure but given the environment my computer sits in, I believe the benefits would be worthwhile.

From what I've read there doesn't seem to be a way to achieve this with a sudo setting. The closest I came was to set NOPASSWD in the sudoers file which is a) not desirable and b) does not apply to graphical sudo actions.

Perhaps there is some kind of keyring tool that might help me achieve this?

Much love!

---

### Post by Dangertux on 2011-10-19
Though it is not recommended the following command will get you to a root shell. 

```

sudo -i 

```

Or 

```

sudo su -

```

---

### Post by biffta on 2011-10-19
> **Dangertux said:**
> 
```

sudo -i 

```

Or 

```

sudo su -

```

Running either of these will not make any difference if you open another shell or try to run a graphical program requiring elevated privileges.

---

### Post by snowpine on 2011-10-19
Correct; this is a built-in security feature at the heart of Linux.

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by biffta on 2011-10-19
> **snowpine said:**
> Correct; this is a built-in security feature at the heart of Linux.

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Yeah had a feeling I was pissing in the wind but wanted to double check. Danke!

---

### Post by The Cog on 2011-10-19
I often open a terminal with **sudo -i** to do admin work, and occasionally then run gui applications from it, e.g. **synaptic &** or **thunar &**

---

### Post by biffta on 2011-10-19
> **The Cog said:**
> I often open a terminal with **sudo -i** to do admin work, and occasionally then run gui applications from it, e.g. **synaptic &** or **thunar &**

Yeah not a bad idea, I'll try remember it next time! Cheers.

---

### Post by bodhi.zazen on 2011-10-19
> **The Cog said:**
> I often open a terminal with **sudo -i** to do admin work, and occasionally then run gui applications from it, e.g. **synaptic &** or **thunar &**

for graphical applications you *should* use gksu (or kdesudo).

For some additional information on sudo see:

[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

---

### Post by dodo3773 on 2011-10-20
Just install terminator terminal. Then you can launch that as sudo/root and just keep splitting it. Each new split will still have root permissions.

---

### Post by The Cog on 2011-10-22
> **bodhi.zazen said:**
> for graphical applications you *should* use gksu (or kdesudo).

For some additional information on sudo see:

[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

If I'm launching a root graphical app directly from my account, I use gksu. 

But I almost never do that - I generally use sudo -i from a terminal, and then if I happen to want a root graphical app, I launch it from there. I know it's probably not the way most people work, but I find that when I'm doing admin work, it's almost always a terminal I want rather than a GUI. The exception is if I want to do more than a one-or-two line file edit - I'm not that hot on vi.

Do you think there's a problem with launching apps from a "sudo -i"'d  terminal? 

I can't think why there should be, but I did get caught out by a failure to log in (X crashing) earlier this week because of a root owned .Xauthority in my home directory. I haven't worked out what I did to deserve that yet. I know it would have completely stumped a newbie - it had me perplexed for a few minutes.

---

### Post by biffta on 2011-10-22
Seems to me like you just answered your own  question ;-)

---

### Post by matt_symes on 2011-10-22
Hi

> **biffta said:**
> Is there a way that after having entered my sudo password once, I am authorised for all tasks requiring elevated privileges? I've searched quite a bit on this subject and haven't found anything that solves my particular problem.

example:

I open a terminal and run (and successfully authenticate) 
```
sudo visudo
```I then open another terminal and run
```
sudo visudo
```where I am again prompted for the password.

Hi 

You need to edit the sudoers file and use the tty_tickets option.

I do not recommend it but for your information. Open a terminal and type

```
sudo visudo 
```Looks for the line that says (or something similar if you have changed it)

```
Defaults        env_reset
```and add !tty_tickets so it becomes

```
Defaults        env_reset, !tty_tickets
```Kind regards

---

### Post by The Cog on 2011-10-22
> **biffta said:**
> Seems to me like you just answered your own  question ;-)

Was that supposed to be a useful contribution?

When I use sudo -i, the resulting terminal as /root as the working directory, and my id is uid=0(root) gid=0(root) groups=0(root). So I can't really see why there should be a  problem launching any GUI app from this terminal. If you know of one, please don't keep it a secret - we are all here to learn.

---

### Post by nothingspecial on 2011-10-22
> **The Cog said:**
> If I'm launching a root graphical app directly from my account, I use gksu. 



Do you think there's a problem with launching apps from a "sudo -i"'d  terminal? 

I can't think why there should be, but I did get caught out by a failure to log in (X crashing) earlier this week because of a root owned .Xauthority in my home directory. I haven't worked out what I did to deserve that yet. I know it would have completely stumped a newbie - it had me perplexed for a few minutes.

That is exactly why you should use gksudo etc

Graphical apps sometimes write to config files in your home including .Xauthority. Launced with sudo this changes the owner of them to root.

gksudo prevents this.

---

### Post by biffta on 2011-10-22
> **The Cog said:**
> Was that supposed to be a useful contribution?


Ok sorry allow me to elaborate, I'm on my phone here so probably should have waited to use a PC to reply properly.

It seemed as though you were asking if launching gui apps from a sudo -i terminal was really all that bad. You then went on to say how you ended up with a root owned file in you home directory. This is the main reason why you should use gksu, as it sets the $HOME for the running process to the actual root user's home directory.

---

### Post by The Cog on 2011-10-22
Yes, I know this is why you should use gksudo or gksu. I suspect that the .Xauthority got there because I forgot myself and simply launched a gui app with sudo. 

I would have gone on with that assumption except that Bhodi.Zazen explicitly picked up my comment about using sudo -i and then launching graphical apps from there. I really don't see how that could cause problems: see the -i option in man sudo. If it can cause problems, I would rather like to know how it know, such as how it knows which user's home directory to place the .Xauthority in - how does it know that it was me that launched it?

Also if this can cause problems, I need to know that I should't tell other users that I think it's OK to do it.

---

### Post by matt_symes on 2011-10-22
Hi
```

matthew@matthew-Aspire-7540:~$ sudo -i
[sudo] password for matthew: 
root@matthew-Aspire-7540:~# env
<snip>
[COLOR=Red]USER=root[/COLOR]
<snip>
[COLOR=Red]SUDO_USER=matthew[/COLOR]
SUDO_UID=1000
USERNAME=root
MAIL=/var/mail/root
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PWD=/root
<snip>
[COLOR=Red]HOME=/root[/COLOR]
LOGNAME=root
LESSOPEN=| /usr/bin/lesspipe %s
SUDO_GID=1000
<snip>
[COLOR=Red]XAUTHORITY=/home/matthew/.Xauthority[/COLOR]
_=/usr/bin/env
root@matthew-Aspire-7540:~# 
```Hence a root owned /home/<user>/.Xauthority can happen. Remember it's the user who logs onto X that requires the .Xauthority cookie. If you logged into a root X session then root would have its own .Xauthority cookie.

@OP. I did reply to your initial post BTW.

Kind regards

---

### Post by biffta on 2011-10-22
>  Defaults        env_reset, !tty_tickets 

Hey matt, yeah regarding this. I will give this a try soon as I can, do you know if it works across gksu as well?

---

### Post by matt_symes on 2011-10-22
Hi

> **biffta said:**
> Hey matt, yeah regarding this. I will give this a try soon as I can, do you know if it works across gksu as well?

Yes i think it does. I am not 100% sure though. Almost everything i do that requires elevated privileges i do from the terminal or a console.

Kind regards

---

### Post by The Cog on 2011-10-22
Yikes! 
And there it is. Thank you, Matt. 

I'll have to change my ways then. 
I see that sudo su -l does the same thing.

---

### Post by bodhi.zazen on 2011-10-22
As others have explained it is all about the environmental variables.

When you run graphical applications you also have to be concerned with X security.

gksu and kdesudo will set the environmental and X variables properly.

The result is some configuration files in $HOME will potentially overwritten as you discovered.

As you say, it is easy to fix if you are experienced with Linux and you still have root access, but it can be difficult for new users.

So best to advise sudo -i and gksu and reference the wiki rootsudo page for additional information.

You might also be interested in [this post](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4) .

---

