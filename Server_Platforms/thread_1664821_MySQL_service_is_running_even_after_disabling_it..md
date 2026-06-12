---
title: "MySQL service is running even after disabling it."
date: 2011-01-11
forum: Server Platforms
---

### Post by s.a.patil on 2011-01-11
Hello community brothers/sisters:), I'm facing unique problem. I have installed AMP on my laptop to learn PHP, but after going through introduction chapter of PHP it came to my knowledge that I have to learn HTML first, OK not a problem at all, I now find myself immersed in HTML5 book, but my problem started from this point:(. Since I didn't needed AMP, I disabled them via 'sysv-rc-conf' application and rebooted my laptop then I 'sudo' netstat -tap |grep LISTEN but to my dismay MySQL was still running:(, I opened 'sysv-rc-conf' and made sure that MySQL is disabled and again I rebooted my laptop and 'sudo' netstat -tap |grep LISTEN, but MySQL is still running:confused:. Now every time I boot I go to terminal and 'sudo' service mysql stop, this has became hassle to me:(. Please help. Thanks in advance:).

---

### Post by ajgreeny on 2011-01-11
I don't think **sysv-rc-conf** works any more for some things, since ubuntu started using a different way of starting several services at boot, ie upstart.  Unfortunately I can't help with any more detail than that, but it may point you in the right direction to find an answer.

You may also be able to disable the service by stopping it in **/etc/rc.local** in the same way that I stop ssh server running.

I need ssh very occasionally, so for security, I stop it at boot-up with an added line in /etc/rc.local ```
service ssh stop
``` just above the "exit 0" line, then when I do need ssh, I start it from terminal with ```
sudo service ssh start
```(actually I use an alias of **ssh+** to start it, and then after using it **ssh-** to stop it again).

Paranoid?  Perhaps. But it makes me feel better about security.

---

### Post by truant on 2011-01-11
if you're not using mysql, you could always just uninstall it.  if you mark it for removal rather than complete removal, your config files will remain so when you install it again, it'll all be set up as it was.

or - and this is what I'd do - just not care about it running.  if it's not being actively used, it won't use up a significant amount of your computer's resources.

---

### Post by sisco311 on 2011-01-11
To disable it you have to comment out the **start on** stanza from /etc/init/mysql.conf:
```
# MySQL Service

description     "MySQL Server"
author          "Mario Limonciello <superm1@ubuntu.com>"

#start on (net-device-up
#          and local-filesystems
#	   and runlevel [2345])
stop on runlevel [016]

respawn
...

```

See: [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

### Post by s.a.patil on 2011-01-11
Thank you very much ajgreeny, your suggestion really worked. I edited /etc/rc.local and added following line "service mysql stop" just before "exit 0" and rebooted my laptop and "sudo netstat -tap |grep LISTEN" and I discovered that MySQL service was not running. You really have saved lot of hassle as I do not have to be 'root' to do this.
> **ajgreeny said:**
> (actually I use an alias of **ssh+** to start it, and then after using it **ssh-** to stop it again).
Can you please guide how to do this. Thanks a lot in advance.

---

### Post by s.a.patil on 2011-01-11
> **sisco311 said:**
> To disable it you have to comment out the **start on** stanza from /etc/init/mysql.conf:
```
# MySQL Service

description     "MySQL Server"
author          "Mario Limonciello <superm1@ubuntu.com>"

#start on (net-device-up
#          and local-filesystems
#	   and runlevel [2345])
stop on runlevel [016]

respawn
...

```

See: [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

Thanks a lot sisco311, I go through above guide line on "upstart", indeed this thread will help many like me.

---

### Post by ajgreeny on 2011-01-12
> **s.a.patil said:**
> > (actually I use an alias of **ssh+** to start it, and then after using it **ssh-** to stop it again).

Can you please guide how to do this. Thanks a lot in advance.

In your home there is a file called .bashrc which is hidden, so you may need to use Ctrl+H to see hidden files and folders.  In that file there is a section:-
```

# some more ls aliases
[COLOR=Red]#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'[/COLOR]

# Alias definitions.
[COLOR=Blue]# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.[/COLOR]
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi


```

If you remove the # from the 3 lines shown in red above they will become active aliases.  That is a standard pattern for the lines for aliases, so my ssh lines are
[COLOR=Red]alias ssh+='sudo service ssh start'[/COLOR]
and
[COLOR=Red]alias ssh-='sudo service ssh stop'[/COLOR]

[COLOR=Black]For ease, you will see that in the blue text above[/COLOR], you can make a new file called .bash_aliases in home and put just alias lines in it.  Whilst not absolutely necessary, I find it a neater solution, and I do use aliases a great deal.
Here's some of my list which you may find useful.
```
alias am='alsamixer'
alias cleanhistory='grep -v ^q .bash_history > .bash_history2 && mv .bash_history .bash_historybak && mv .bash_history2 .bash_history'
alias cp='cp -i' #makes copy command interactive
alias cron='gedit Quicknotes/Cron_Commands.txt & crontab -e' #Opens a crontab edit terminal and also a reminder txt file of cron syntax
alias df='df -hT' # Shows disk free space and filesystem type
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias free='free -m' # Shows ram usage in MB
alias fsck='sudo touch /forcefsck' # Forces filesystem check (fsck) at next boot
alias fstab='cat /etc/fstab'
alias gip='get_iplayer'
alias gipg='get_iplayer -g'
alias gipr='get_iplayer --type radio'
alias grep='grep --color=auto'
alias hw='sudo lshw -html > hw.html' #Makes an html file listing of computer hardware
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -l'
alias ls='ls --color=auto'
alias menu='grep menuentry /boot/grub/grub.cfg'  #Shows grub menu entries
alias mv='mv -i' # Makes move/rename command interactive
alias q='exit'
alias rm='rm -i' # Makes remove command interactive
alias ssh+='sudo service ssh start'
alias ssh-='sudo service ssh stop'
alias temp='sudo mbmon'

```

---

### Post by Loggy on 2011-02-16
I have been puzzling about this issue.  Some services use upstart and others don't.  Starting and configuration seems to be work in progress at the moment.  I understand the motivation behind upstart but for my purposes it is just a nuisance.

I have a server based on 10.04 LTS currently being tested on an old Dell PE1850 in my office (I have earplugs as well!).  The aim is to have a stripped down very fast server as a KVM guest on a cloud (can't KVM on my Dell as the chips are too old).  

I have prepared a concise kernel (starting with nothing and adding as per the hardware rather than taking out all the unwanted stuff) that is only about 2MB in size, compiles in 15 minutes and is fast to boot.

But configuring the services is rather messy.  I want to strip out all the services that I don't need.  For example I want to use lighty rather than apache2 but whatever I did apache2 was started on booting and I had to stop it and start lighty manually.  Putting them both in just meant that apache2 started and lighty never got a look in because of the port 80 clash.  But I don't want to uninstall apache2 as I may decide to use it if lighty doesn't fit the bill.

So far the the easiest way I have found to disable service {servicename} from level {m} is to remove the S{n}{servicename} from rc{m}.d (it is a symlink to init.d).

This seems to be a very 1990's approach so is there a better way?  
Or is this way likely to run into difficulties when I upgrade?

TIA

---

### Post by Loggy on 2011-02-16
A bit more detective work.  

Services started by upstart have their initiation scripts in /etc/init.d symlinked to /lib/init/upstart-job which is what delivers the odd message if you do use hte /etc/init.d/service start command.  

So my little trick of removing the corresponding rc?.d file won't work.  This is about half of them on my server and these are controlled from /etc/init/*.conf.  To remove a service permanently you can comment out the appropriate line or the start levels or whatever in the .conf file although it seems as if you then can't start it manually...

---

