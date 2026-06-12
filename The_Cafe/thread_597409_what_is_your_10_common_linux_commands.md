---
title: "what is your 10 common linux commands?"
date: 2007-10-30
forum: The Cafe
---

### Post by mysurface on 2007-10-30
Recently I wrote a combo of commands that digs your history of command lines, and generate your top ten common command I use recently.

I was thinking since yesterday, hey why don't I post it up at forums and see what is the common commands that Ubuntu users use daily? And here I come.

```
history | awk '{CMD[$2]++;count++;}END { for (a in CMD)print CMD[a] " " CMD[a]/count*100 "% " a;}' | grep -v "./" | column -c3 -s " " -t | sort -nr | nl |  head -n10
```

Just copy and paste to your terminal will do. And here is my recent TOP TEN command list

```
     1  99  19.8%  cd
     2  89  17.8%  ls
     3  57  11.4%  vi
     4  24  4.8%   apt-get
     5  21  4.2%   sudo
     6  15  3%     apt-cache
     7  10  2%     ssh
     8  10  2%     man
     9  10  2%     katapult
    10  7   1.4%   exit

```

Yeah, recently I did a lots of software searching through apt-cache and vi is always my fav editor allows me to edit my conf, and katapult, a kde apps that allows me to type my app command and run.

In case you are interested to understand that combo's of commands, you may check out [**this blog post**]("http://linux.byexamples.com/archives/332/what-is-your-10-common-linux-commands/").

Have fun :KS

---

### Post by x0as on 2007-10-30
[http://ubuntuforums.org/showthread.php?t=472090](http://ubuntuforums.org/showthread.php?t=472090)

---

### Post by PatrickMay16 on 2007-10-30
Here's mine:

     1  219  43.8%  sudo
     2  71   14.2%  cd
     3  33   6.6%   ls
     4  24   4.8%   dmesg
     5  22   4.4%   sensors
     6  18   3.6%   killall
     7  12   2.4%   for
     8  11   2.2%   play
     9  10   2%     timidity
    10  10   2%     rm

---

### Post by Havoc on 2007-10-30
Hehe

     1  134  26.8%  make
     2  49   9.8%   sudo
     3  23   4.6%   kill
     4  23   4.6%   export
     5  21   4.2%   cd
     6  21   4.2%   bitbake
     7  18   3.6%   wine
     8  16   3.2%   patch
     9  8    1.6%   latex
    10  8    1.6%   killall

Developer stuff :)

---

### Post by FuturePilot on 2007-10-30
```
     1  40  35.3982%   sudo
     2  17  15.0442%   apt-cache
     3  5   4.42478%   gdb
     4  5   4.42478%   cd
     5  4   3.53982%   pidof
     6  4   3.53982%   killall
     7  3   2.65487%   wget
     8  3   2.65487%   sh
     9  3   2.65487%   java
    10  2   1.76991%   lspci

```
Low numbers- fresh install

---

### Post by funrider on 2007-10-30
1  181  30.7301%   ls
     2  138  23.4295%   cd
     3  20   3.39559%   cat
     4  19   3.22581%   vi
     5  15   2.54669%   ps
     6  15   2.54669%   exit
     7  13   2.20713%   tail
     8  11   1.86757%   .
     9  10   1.69779%   l
    10  9    1.52801%   kopete

---

### Post by Anonii on 2007-10-30
1  67  13.4%  mplayer
     2  55  11%    sudo
     3  55  11%    ls
     4  53  10.6%  cd
     5  43  8.6%   irssi
     6  31  6.2%   su
     7  23  4.6%   nano
     8  19  3.8%   gcc
     9  15  3%     gmplayer
    10  14  2.8%   eix

---

### Post by Kingsley on 2007-10-30
1  123  51.4644%  sudo
     2  26   10.8787%  apt-cache
     3  17   7.11297%  cd
     4  9    3.76569%  killall
     5  7    2.92887%  ls
     6  4    1.67364%  dpkg
     7  3    1.25523%  tangerine
     8  3    1.25523%  make
     9  3    1.25523%  exit
    10  3    1.25523%  clear

---

### Post by justsomedude on 2007-10-30
```
copy and paste
```

That's basically all I use. :lolflag:

err...

1  158  51.1327%   sudo
2  50   16.1812%   cd
3  14   4.53074%   make
4  14   4.53074%   compiz
5  10   3.23625%   tar
6  6    1.94175%   wget
7  6    1.94175%   glxgears
8  3    0.970874%  gedit
9  2    0.647249%  uname
10  2    0.647249%  trackerd

---

### Post by KuriKai on 2007-10-30
Looks like I do more browsing in the command line than most people
     1  103  20.6%  cd
     2  97   19.4%  sudo
     3  25   5%     svn
     4  23   4.6%   wine
     5  21   4.2%   make
     6  14   2.8%   winecfg
     7  11   2.2%   ls
     8  9    1.8%   javac
     9  8    1.6%   git
    10  8    1.6%   cp

---

### Post by anaconda on 2007-10-30
Good idea :)

Not quite what I expected, but here it is:

     1  148  29.6%  ls
     2  111  22.2%  cd
     3  62   12.4%  cp
     4  28   5.6%   sudo
     5  14   2.8%   45
     6  12   2.4%   exit
     7  11   2.2%   more
     8  11   2.2%   chmod
     9  8    1.6%   convert
    10  7    1.4%   rm

---

### Post by snickers295 on 2007-10-30
```
 
     1  46  33.0935%   sudo
     2  14  10.0719%   qemu
     3  11  7.91367%   cd
     4  8   5.7554%    mount
     5  7   5.03597%   cfdisk
     6  4   2.8777%    chmod
     7  3   2.15827%   gparted
     8  2   1.43885%   vncviewer
     9  2   1.43885%   totem
    10  2   1.43885%   print

```

---

### Post by SirBob1701 on 2007-10-30
```
     1  186  37.2%  sudo
     2  75   15%    ls
     3  65   13%    cd
     4  24   4.8%   vi
     5  23   4.6%   exit
     6  17   3.4%   locate
     7  14   2.8%   pstree
     8  12   2.4%   chmod
     9  10   2%     clear
    10  7    1.4%   man

```

---

### Post by Rinzwind on 2007-10-30
1  97  25.6614%   sudo
2  55  14.5503%   ls
3  53  14.0212%   cd
4  18  4.7619%    more
5  14  3.7037%    cat
6  9   2.38095%   pwd
7  9   2.38095%   locate
8  8   2.1164%    epsxe
9  6   1.5873%    wget
10  6   1.5873%    rm

I am the only one using rm hmmm? :+

anaconda what's 45? :D

---

### Post by svtfmook on 2007-10-30
1  194  38.8%  sudo
     2  94   18.8%  cd
     3  25   5%     make
     4  16   3.2%   gedit
     5  13   2.6%   wget
     6  9    1.8%   bzr
     7  8    1.6%   gksudo
     8  6    1.2%   conky
     9  6    1.2%   chmod
    10  5    1%     sensors

---

### Post by Salpiche on 2007-10-30
1  53  30.1136%   sudo
     2  35  19.8864%   top
     3  30  17.0455%   kill
     4  24  13.6364%   conky
     5  4   2.27273%   exit
     6  3   1.70455%   smartctl
     7  3   1.70455%   q
     8  3   1.70455%   cd
     9  2   1.13636%   svn
    10  2   1.13636%   SUDO

---

### Post by snickers295 on 2007-10-30
seems sudo is very popular!

---

### Post by misfitpierce on 2007-10-30
1  160  40.404%    sudo
     2  64   16.1616%   tail
     3  33   8.33333%   gksu
     4  10   2.52525%   make
     5  8    2.0202%    startx
     6  7    1.76768%   cd
     7  6    1.51515%   transmission-remote
     8  6    1.51515%   fglrxinfo
     9  6    1.51515%   airport-config
    10  5    1.26263%   wine

---

### Post by budr on 2007-10-30
Wow.  Thanks for that one-liner.  I've been mucking around the *nix command line for a dozen years and I still learned half a dozen useful things from it.  The day is not a total loss.

    1  87  17.4%  ls
     2  53  10.6%  cd
     3  47  9.4%   sudo
     4  34  6.8%   less
     5  33  6.6%   vi
     6  24  4.8%   grep
     7  18  3.6%   man
     8  17  3.4%   tail
     9  17  3.4%   locate
    10  15  3%     cal
~$

---

### Post by koleoptero on 2007-10-30
Fresh install, few stuff
[FONT="Fixedsys"]
     1  8  18.6047%  sudo
     2  7  16.2791%  ls
     3  7  16.2791%  cd
     4  4  9.30233%  gksudo
     5  2  4.65116%  pon
     6  2  4.65116%  exit
     7  2  4.65116%  bash
     8  1  2.32558%  umount
     9  1  2.32558%  tar
    10  1  2.32558%  su[/FONT]

---

### Post by angkor on 2007-10-30
```
 1  104  20.8%  ls
     2  104  20.8%  cd
     3  69   13.8%  sudo
     4  30   6%     mplayer
     5  28   5.6%   apt-cache
     6  27   5.4%   rm
     7  12   2.4%   ps
     8  9    1.8%   dmesg
     9  9    1.8%   cat
    10  8    1.6%   htop
```

---

### Post by Happy_Man on 2007-10-30
```
     1  42  29.5775%   cd
     2  24  16.9014%   sudo
     3  22  15.493%    ls
     4  7   4.92958%   aptitude
     5  5   3.52113%   cp
     6  3   2.11268%   mv
     7  3   2.11268%   df
     8  3   2.11268%   cat
     9  3   2.11268%   apt-cache
    10  2   1.40845%   mkdir

```

Fresh install of Gutsy, so the numbers are still pretty low. ;)

---

### Post by UltraMathMan on 2007-10-30
```
     1  126  25.2%  exit
     2  118  23.6%  ssh
     3  68   13.6%  sudo
     4  42   8.4%   sftp
     5  34   6.8%   ls
     6  27   5.4%   cd
     7  17   3.4%   aptitude
     8  8    1.6%   man
     9  4    0.8%   vncviewer
    10  4    0.8%   locate
```

---

### Post by fuscia on 2007-10-30
1  122  29.2566%   sudo
     2  38   9.11271%   ncmpc
     3  29   6.95444%   cd
     4  24   5.7554%    nano
     5  20   4.79616%   ls
     6  19   4.55635%   streamripper
     7  19   4.55635%   apt-cache
     8  17   4.07674%   mplayer
     9  14   3.35731%   htop
    10  13   3.11751%   exit

---

