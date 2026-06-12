---
title: "dangerous Commands"
date: 2010-11-04
forum: Security
---

### Post by NoSuchDevice on 2010-11-04
So I was looking into this thread> [http://ubuntuforums.org/announcement.php?f=329](http://ubuntuforums.org/announcement.php?f=329)

I was just wondering is there any kind of Anti-Virus software which stops these commands from running, I don't wanna' kill my system. 

Thanks
NoSuchDevice

---

### Post by cascade9 on 2010-11-04
No, antivirus wont stop you from running commands like that. 

Linux distros assume that your smart enough to know what your doing.

---

### Post by teh_pwnzr on 2010-11-04
You would need to have root priveleges to execute many of those commands.
 
This is also a great reminder that, although much better than windows, Ubuntu is not 100% safe.

---

### Post by Rubi1200 on 2010-11-04
The point of that thread is to warn users about the dangers of blindly running commands without knowing what they do.

ALWAYS think before running a command. Ask here on the forums if there is something you are not sure about; even if it *seems* trivial.

Better to take a few minutes to ask and check than have to reinstall your whole system because of one mistake.

I always take a second look at the command I have entered before hitting Enter to make sure:

a. there are no typos
b. I know what the command is about to do

At the end of the day, it is your responsibility to ensure that your system is not compromised because of using commands without being aware of the consequences.

---

### Post by artie_effim on 2010-11-04
While there is not much to actually prevent these commands from doing something a simple alias can help you remember to 'measure twice - cut once' for rm.

Just put ```
alias rm='rm -i'
``` into ~/.bashrc and logout.  After that rm will be interactive, prompting you to do the delete.

As for the rest - SELinux can severely lockdown a system, but remember - with more security comes less freedom - the more you lock it down, the harder it will be to use.

Also - if you want to play and have the memory, install VirtualBox and install a test system - that way you can always roll it back.  Or, if you want to really have fun, install a basic Ubuntu server as a VBox server and go completely virtual for your day-to-day.  Take regular snapshots, that way you can roll back to a working system in seconds.

---

### Post by Carl Hamlin on 2010-11-04
> **cascade9 said:**
> Linux distros assume that your smart enough to know what your doing.

And the hammer comes *DOWN*!

---

### Post by CharlesA on 2010-11-04
> **artie_effim said:**
> While there is not much to actually prevent these commands from doing something a simple alias can help you remember to 'measure twice - cut once' for rm.

Just put ```
alias rm='rm -i'
``` into ~/.bashrc and logout.  After that rm will be interactive, prompting you to do the delete.

+1 to that.

---

### Post by FuturePilot on 2010-11-04
> **artie_effim said:**
> 
Just put ```
alias rm='rm -i'
``` into ~/.bashrc and logout.  After that rm will be interactive, prompting you to do the delete.


That is a bad idea. You will become way too comfortable with using the rm command. One day you'll sit at a machine that doesn't have this alias and accidentally rm something and there will be no safety net to fall into. Not only that but your personal aliases do not work as root, so if you sudo rm something, there will also be no safety net.

Also [http://use.perl.org/~schwern/journal/38188]("http://use.perl.org/~schwern/journal/38188")

---

### Post by CharlesA on 2010-11-04
> **FuturePilot said:**
>  Not only that but your personal aliases do not work as root, so if you sudo rm something, there will also be no safety net.

Didn't know that, but I guess it would make sense.

Thanks.

---

