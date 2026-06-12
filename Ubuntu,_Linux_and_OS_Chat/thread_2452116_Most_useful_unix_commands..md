---
title: "Most useful unix commands."
date: 2020-10-17
forum: Ubuntu, Linux and OS Chat
---

### Post by carb987 on 2020-10-17
What are the most useful unix commands ?  or, your favorite commands??

---

### Post by T6&amp;sfpER35% on 2020-10-17
this is a very broad question
can find some basic commands [here]("https://www.tjhsst.edu/~dhyatt/superap/unixcmd.html")

to clean up system periodically (once a week) i use these
 
  Remove packages that didn&#8217;t install completely.
```
sudo apt-get autoclean
``` 
Remove your apt-cache.
```
sudo apt-get clean
```
Remove software dependencies that you don&#8217;t need.
```
sudo apt-get autoremove
```
clear thumbnails
```
rm -rfv ~/.cache/thumbnails
```
clear cache
```
sudo du -sh /var/cache/apt
```
update 
```
sudo apt-get update -y
```
upgrade
```
sudo apt upgrade
```
Kernel and other Cleanups after Deletions
```
sudo apt autoremove --purge
```
Clear DNS Cache
```
sudo systemd-resolve --flush-caches
```

my personal favourite?

```
windscribe connect
```

:p

---

### Post by mastablasta on 2020-10-17
mostly i use application commands. i think system is actually made from separate applications that bind into one. for example apt commands are form apt package manager, systemd commands are from systemd. so they won't work if you have old init based linux.
there are probably not that many directly from Linux kernel or base of the system. but you can see some that go back to Unix time. just read about seq command yesterday. at first few examples it seemed pointless, but when more uses were demonstrated, it made it quite interesting. ls, rm, cd and such are probably brought over from unix as well.

---

### Post by metacell on 2020-10-17
[FONT=courier new]sudo apt --fix-broken install[/FONT]

---

### Post by metacell on 2020-10-17
screen[FONT=courier new][/FONT]

It can be used to create multiple text-based "windows" inside a terminal. Eg, if you want to run a long package update process with lots of text flowing by, you can use [FONT=courier new]screen[/FONT] to put it in the background, and then switch back and forth to watch the progress.

You can also reattach to a screen session if you're forced to restart X, or if your SSH connection is broken, and your programs keep running in the background.

---

### Post by carb987 on 2020-10-17
Thank you everyone.
I love du.exe in Windows system.  It's convenient for me.

---

### Post by TheFu on 2020-10-17
I have a few aliases for the commands I use most often: 
```

# listings, history
alias ls='ls -F'
alias ll='ls -al'
alias ltm='ls -alt| more'
alias h='history'
alias mkdir='mkdir -p'

alias psg='ps -eaf | grep $*'
alias iproute='ip route | column -t'

# storage
alias du='du -h'
alias df='df -h'
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
alias lsblk='lsblk -e 7 -o name,size,type,fstype,mountpoint'

# private browsing
alias firepchrome='firejail --private chromium-browser --js-flags=--noexpose_wasm --mute-replay-warnings '
alias firepff='firejail --private firefox '
```

The order of the aliases matter.

Besides those, ssh, rsync, egrep, dd, awk, sed, sort, cut, perl, nmap are extremely useful.  For example,
```
$ lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/'
```

---

