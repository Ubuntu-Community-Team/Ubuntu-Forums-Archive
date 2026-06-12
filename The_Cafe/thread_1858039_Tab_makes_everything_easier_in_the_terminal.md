---
title: "Tab makes everything easier in the terminal"
date: 2011-10-11
forum: The Cafe
---

### Post by pr3zident on 2011-10-11
I have been using Ubuntu for sometime in and out the terminal, but i just learned that i can use tab to complete my command in the terminal. Now i can't stop using tab i try it on my phone when sending a message, writing a document smh i try it everywhere.

tab - finishes command
find + ctrl r = finds commands 

is there any other shortcuts like these ?

---

### Post by ajgreeny on 2011-10-11
Have you caught up with the use of aliases in the terminal?  If not look into it.  I use many as it makes life very easy.

Here are the ones I use, some very often, others less often, but they all make life a lot quicker.
```
alias addppa='sudo add-apt-repository'
alias am='alsamixer'
alias blk='sudo blkid'
alias db='sudo updatedb'
alias df='df -hT'
alias dl='vnstat -d'
alias dldays='vnstat -d > /tmp/$(date +%F-%T)-DLs && gedit /tmp/*DLs & exit'
alias dll='vnstat -l'
alias egrep='egrep --color=auto'
alias fd+='mount /media/floppy'
alias fd-='umount /media/floppy'
alias fgrep='fgrep --color=auto'
alias free='free -m'
alias fsck='sudo touch /forcefsck'
alias fstab='cat /etc/fstab'
alias gip='get_iplayer'
alias gipg='get_iplayer -g'
alias gipr='get_iplayer --type radio'
alias grep='grep --color=auto'
alias hw='sudo lshw -html > $(date +%F-%I%M)hw.html'
alias installed='grep -w install /var/log/dpkg.log'
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -lh'
alias ls='ls --color=auto'
alias menu='grep menuentry /boot/grub/grub.cfg'
alias mv='mv -i'
alias q='exit'
alias removed='grep -w remove /var/log/dpkg.log'
alias rm='rm -i'
alias scan='sudo tune2fs /dev/sda1 -l'
alias scanhome='sudo tune2fs /dev/sda2 -l'
alias ssh+='sudo service ssh start'
alias ssh-='sudo service ssh stop'
alias temp='sudo mbmon -c 4 && hddtemp /dev/sda /dev/sdb'
alias upgraded='grep -w upgrade /var/log/dpkg.log'
alias version='uname -a && lsb_release -a'
alias xorg='cat /etc/X11/xorg.conf'

```Just put the ones you want plus any others you may think of into a hidden txt file in your home called **.bash_aliases** and you can run the command with the shortcut instead.

Very useful for any long but repeated commands you may need.  I think there may be a forum thread of other useful aliases, so have a search.

---

### Post by TheLions on 2011-10-11
> **pr3zident said:**
> I have been using Ubuntu for sometime in and out the terminal, but i just learned that i can use tab to complete my command in the terminal. Now i can't stop using tab i try it on my phone when sending a message, writing a document smh i try it everywhere.

tab - finishes command
find + ctrl r = finds commands 

is there any other shortcuts like these ?

[IMG]http://troll.me/images/depardieu/o-rly.jpg[/IMG]

---

### Post by pr3zident on 2011-10-11
> **ajgreeny said:**
> Have you caught up with the use of aliases in the terminal?  If not look into it.  I use many as it makes life very easy.

Here are the ones I use, some very often, others less often, but they all make life a lot quicker.
```
alias addppa='sudo add-apt-repository'
alias am='alsamixer'
alias blk='sudo blkid'
alias db='sudo updatedb'
alias df='df -hT'
alias dl='vnstat -d'
alias dldays='vnstat -d > /tmp/$(date +%F-%T)-DLs && gedit /tmp/*DLs & exit'
alias dll='vnstat -l'
alias egrep='egrep --color=auto'
alias fd+='mount /media/floppy'
alias fd-='umount /media/floppy'
alias fgrep='fgrep --color=auto'
alias free='free -m'
alias fsck='sudo touch /forcefsck'
alias fstab='cat /etc/fstab'
alias gip='get_iplayer'
alias gipg='get_iplayer -g'
alias gipr='get_iplayer --type radio'
alias grep='grep --color=auto'
alias hw='sudo lshw -html > $(date +%F-%I%M)hw.html'
alias installed='grep -w install /var/log/dpkg.log'
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -lh'
alias ls='ls --color=auto'
alias menu='grep menuentry /boot/grub/grub.cfg'
alias mv='mv -i'
alias q='exit'
alias removed='grep -w remove /var/log/dpkg.log'
alias rm='rm -i'
alias scan='sudo tune2fs /dev/sda1 -l'
alias scanhome='sudo tune2fs /dev/sda2 -l'
alias ssh+='sudo service ssh start'
alias ssh-='sudo service ssh stop'
alias temp='sudo mbmon -c 4 && hddtemp /dev/sda /dev/sdb'
alias upgraded='grep -w upgrade /var/log/dpkg.log'
alias version='uname -a && lsb_release -a'
alias xorg='cat /etc/X11/xorg.conf'

```Just put the ones you want plus any others you may think of into a hidden txt file in your home called **.bash_aliases** and you can run the command with the shortcut instead.

Very useful for any long but repeated commands you may need.  I think there may be a forum thread of other useful aliases, so have a search.

Cool I know about alias but never really found a reason to use it, I'm going to try it out.. 
Lol @TheLion

---

### Post by TeoBigusGeekus on 2011-10-11
Check these aliases as well
```
 alias wtf='dmesg'
 alias onoz='cat /var/log/errors.log'
 alias rtfm='man'

 alias visible='echo'
 alias invisible='cat'
 alias moar='more'

 alias icanhas='mkdir'
 alias donotwant='rm'
 alias dowant='cp'
 alias gtfo='mv'

 alias hai='cd'
 alias plz='pwd'

 alias inur='locate'

 alias nomz='ps -aux'
 alias nomnom='killall'

 alias cya='reboot'
 alias kthxbai='halt'
```

---

### Post by pr3zident on 2011-10-11
> **TeoBigusGeekus said:**
> Check these aliases as well
```
 alias wtf='dmesg'
 alias onoz='cat /var/log/errors.log'
 alias rtfm='man'

 alias visible='echo'
 alias invisible='cat'
 alias moar='more'

 alias icanhas='mkdir'
 alias donotwant='rm'
 alias dowant='cp'
 alias gtfo='mv'

 alias hai='cd'
 alias plz='pwd'

 alias inur='locate'

 alias nomz='ps -aux'
 alias nomnom='killall'

 alias cya='reboot'
 alias kthxbai='halt'
```

Your aliases are funny lol

---

### Post by matthew.ball on 2011-10-11
> **pr3zident said:**
> I have been using Ubuntu for sometime in and out the terminal, but i just learned that i can use tab to complete my command in the terminal. Now i can't stop using tab i try it on my phone when sending a message, writing a document smh i try it everywhere.

tab - finishes command
find + ctrl r = finds commands 

is there any other shortcuts like these ?
Check out [GNU Readline]("http://cnswww.cns.cwru.edu/php/chet/readline/readline.html").

---

### Post by oldos2er on 2011-10-11
If you want tab completion to the extreme, check out zsh. [http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/](http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/)

---

### Post by wolfen69 on 2011-10-11
I repeat a lot of the same commands, so my favorite thing is hitting the up arrow to bring up recently used commands.

---

### Post by pr3zident on 2011-10-11
> **wolfen69 said:**
> I repeat a lot of the same commands, so my favorite thing is hitting the up arrow to bring up recently used commands.

Thank everybody .... but wolfen69, i do that to but sometimes the command i want is like 10 commands back so i use the find and ctrl + R and start typing the command i want...

---

### Post by ilovelinux33467 on 2011-10-11
> **oldos2er said:**
> If you want tab completion to the extreme, check out zsh. [http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/](http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/)

+1 zsh's tab completion is awesome.

---

