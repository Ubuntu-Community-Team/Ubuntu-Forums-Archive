---
title: "[Cafe] Show your .screenrc thread"
date: 2010-01-19
forum: The Cafe
---

### Post by frenchn00b on 2010-01-19
Hi, 

As similar to the famous [conkyrc]("conky.sourceforge.net/") thread, simple, share your screenrc [+ eventually a screenshot]

mine remains light. Here is the $HOME/.screenrc : 
```

hardstatus alwayslastline "%c %w"
bindkey ^[[1;5A prev
bindkey ^[[1;5B next
bindkey ^[[1;5D prev
bindkey ^[[1;5C next
bindkey ^N screen
bindkey ^[[1;2D prev
bindkey ^[[1;2C next

```

**Enjoy coding guys as a [linuxgeek]("www.linuxgeek.net/"). [Happy Tux]("http://img9.imageshack.us/img9/8023/20721069901ba03789ba.jpg") **

Ref:
[[Screen]("http://labs.dagensskiva.com/wp-content/uploads/2008/05/screenrc1.jpg")]

---

### Post by dragos240 on 2010-01-19
I only wish I knew what screen was.

---

### Post by Daisuke_Aramaki on 2010-01-19
Old one. I don't use screen anymore. It's tmux all the way.

Nothing special here as well!

Screenshot

[[img]http://omploader.org/vM2FyeQ[/img]](http://omploader.org/vM2FyeQ)

screenrc

```
startup_message	off
vbell		off
defscrollback	512
shell		-$SHELL
shelltitle	sh
autodetach on

# enable SHIFT-PGUP / SHIFT-PGDOWN scroll
termcapinfo rxvt ti@:te@

# change window with ALT-Q ALT-W
bindkey "^[q" prev
bindkey "^[w" next

# F1-F4 switch
# bindkey -k k1 select 1
# bindkey -k k2 select 2
# bindkey -k k3 select 3
# bindkey -k k4 select 4

# unbind defaults
bind ^m
bind ^i
bind ^f
bind ^s
bind ^w

# keyboard shortcuts
bind ^m screen -t mpd  ncmpc	                 # C-a-m
bind ^i screen -t icq  centericq                 # C-a-i
bind ^f screen -t fish fish                      # C-a-f
bind ^s screen -t bge0 slurm -i bge0             # C-a-s
bind ^w screen -t wpi0 slurm -i wpi0             # C-a-w

# startup sessions
screen -t sh	0 
screen -t sh	1
select 0

# status
hardstatus alwayslastline '%{= M} %H%{= G} %l %= %{= w}%-w%{+b r}%n*%t%{-b r}%{w}%+w %= %{c}%d %D %{B}%c '

# add CPU idle/sustem/user/interrupt stats
backtick 100 5 5 tail -1 /var/tmp/mprem.stats.top
caption always '%{= wk} %200` %= %100` %='
```

---

### Post by AskApache on 2010-04-24
```
term putty-256color
debug off
chdir $HOME
maxwin 11
verbose on
autodetach on
nethack on                      # print wackier status messages
password HJa4lhjDp4UIDlLA          # always of course
defobuflimit 4096
setenv LC_CTYPE en_US.UTF-8
defutf8 on
defencoding UTF-8

idle 360 eval "screen nice -n 19 /opt/s/cmatrix" "idle 360000 pow_detach"

shell -$SHELL                   # use the default shell
shelltitle '$ | bash'           # search | name for dynamic window titles

defmode 600
defmonitor off         # turn monitoring on
defnonblock 2             # flaky/slow ssh lines
defscrollback 15000     # 5000 line scrollback
deflog off
defbce on     # erase background with current bg color
defflow off  # will force screen to process ^S/^Q
deflogin on             # Log new screen windows in utmp.



hardcopy_append on
hardcopydir ~/.backups/.screen
bufferfile ~/.backups/.screen/buffer
logfile ~/.backups/.screen/screen_%y-%m-%d_%n

zombie cr # don't kill window after the process died
silencewait 4

startup_message off     # no way
autodetach on           # Never, ever turn this off.
zombie cr               # Keep dead windows around until I tell them to exit.
verbose on              # And show the command for the windows when they're resurrected.

altscreen on            # restore window contents after using (e.g.) vi
attrcolor b ".I"        # allow bold colors - necessary for some reason

msgwait 6               # 6 second messages
msgminwait 2
multiuser off

pow_detach_msg "Screen session of $LOGNAME $:cr:$:nl:ended." # emulate .logout message



# debug         -       debugging info is written to /tmp/debug/
# dumptermcap   -       Termcap entry written to "/home/srot/tmp/.screen/.termcap".
# info          -       (1,3)/(270,37)+5000 -(-)flow bce UTF-8 6(hellopwd)
# dinfo         -       (270,77) UTF-8 color iso2022

# ===============================================================
# Messages
# ===============================================================
# They are also the names of the commands that set the respective messages.  In every message there can be "meta
# strings" which are replaced by values.  A meta string starts with a percent sign and is then followed by one
# of the following letters: aAcCdDfFhHlmMnstuwWyY The meta strings usually refer to the current
# date and time or to a window title or number. There are also some specials like embedded branches (with %?),
# color codes (with %{xy}) and padding (with %=, %<, %>). you can find their description in the manual in section  "STRING ESCAPES":
#
#  %%      percent sign (the escape character itself)
#  %f      flags of the window
#  %F      sets %? to true if the window has the focus
#  %h      hardstatus of the window
#  %H      hostname of the system
#  %l      current load of the system
#  %n      window number
#  %t      window title
#  %u      all other users on this window
#  %w      all window numbers and names.
#  %-w     all window numbers up to the current window
#  %+w     all window numbers after the current window
#  %W      all window numbers and names except the current one
#
#  DATE VARS -- USELESS!
#  %a      either 'am' or 'pm' - according to the current time
#  %A      either 'AM' or 'PM' - according to the current time
#  %c      current time HH:MM in 24h format
#  %C      current time HH:MM in 12h format
#  %d      day number - number of current day
#  %D      Day's name - the weekday name of the current day
#  %m      month number
#  %M      month name
#  %s      seconds
#  %y      last two digits of the year number
#  %Y      full year number
# ===============================================================
vbell off                               # I like to hear the beep.
activity "%c activity -> %n%f %t^G"     # ^G makes it beep
bell "%c bell -> %n%f %t^G"             # likewise

###########################################################################################################################
 #
 # TERMINAL CONTROL
 # ae: Standout          # ct: Initialization    # es: Status Line
 # AL: Insdel Line       # cv: Cursor Motion     # ff: Cursor Motion
 # al: Insdel Line       # da: Scrolling         # fs: Status Line
# am: Wrapping          # dB: Pad Specs         # gn: Basic
# as: Standout          # db: Scrolling         # hc: Basic
# bc: Cursor Motion     # dC: Pad Specs         # hd: Half-Line
# bl: Bell              # DC: Insdel Char       # ho: Cursor Motion
# bs: Cursor Motion     # dc: Insdel Char       # hs: Status Line
# bt: Cursor Motion     # dF: Pad Specs         # hu: Half-Line
# bw: Cursor Motion     # DL: Insdel Line       # hz: Basic
# CC: Basic             # dl: Insdel Line       # i1: Initialization
# cd: Clearing          # dm: Insdel Char       # i3: Initialization
# ce: Clearing          # dN: Pad Specs         # IC: Insdel Char
# ch: Cursor Motion     # DO: Cursor Motion     # ic: Insdel Char
# cl: Clearing          # do: Cursor Motion     # if: Initialization
# CM: Cursor Motion     # ds: Status Line       # im: Insdel Char
# cm: Cursor Motion     # dT: Pad Specs         # in: Insdel Char
# co: Screen Size       # ec: Clearing          # ip: Insdel Char
# cr: Cursor Motion     # ed: Insdel Char       # is: Initialization
# cS: Scrolling         # ei: Insdel Char       # it: Initialization
# cs: Scrolling         # eo: Basic
#
termcapinfo * hs@

###########################################################################################################################
# COLOR:  colors codes are combinations of [attribute modifier] [color description]
# the manual talks of "attribute/color modifiers".
#
# 0 Black             .    leave color unchanged
# 1 Red               b    blue
# 2 Green             c    cyan
# 3 Brown / yellow    d    default color
# 4 Blue              g    green           b    bold
# 5 Purple            k    blacK           B    blinking
# 6 Cyan              m    magenta         d    dim
# 7 White             r    red             r    reverse
# 8 unused/illegal    w    white           s    standout
# 9 transparent       y    yellow          u    underline
#
# note: "dim" is not mentioned in the manual.
#hardstatus string "%-Lw%{= G0}%50>%n%f* %t%{-}%+Lw%<"

#hardstatus string "%?%F%{-b bc}%:%{-b bb}%?%C|%D|%M %d|%H|%0`%?%F%{+u wb}%? %L=%-Lw%45>%{+b by}%n%f* %t%{-}%+Lw%-0<"

#yaption always "%?%F%{.R.}%?%3n %t%? [%h]%?"
#caption always "%?%F%{-b bc}%:%{-b bb}%?%C|%D|%M %d|%H|%1`%?%F%{+u wb}%? %L=%-Lw%45>%{+b by}%n%f* %t%{-}%+Lw%-0<"
#hardstatus alwayslastline
#hardstatus string "%?%F%{-b bc}%:%{-b bb}%?%C|%D|%M %d|%H|%1`%?%F%{+u wb}%? %L=%-Lw%45>%{+b kG}%n%f* %t%{-}%+Lw%-0<"
hardstatus alwayslastline "[%02c] %`%-w%{=b bw}%n %t%{-}%+w"
# Make screen messages stand out a little more - black on bright green.
#sorendition "= kG"
#caption always "%{.wB}%-w%{.bW}%n %t%{-}%+w %=%{..Lw} %H %{..b} %m/%d %C%a "
caption always "%{cK}$LOGNAME %{bK}(%d %M %Y, %c) %{-}%{bW} %-w%{bW}%50>%{= wb}%n%f %t%{-}%+w%< %{-}"



###########################################################################################################################
#
# default windows
# L - LOGGING
# l - log to utmp
# ln - nolog to utmp
# O - better vt100 emul
# a - all terminal caps
# A - resize
# h - scrol lines
#
screen -t 'LOG' -h 0   1 nice -n 19 sh -c 'read -n1 -t1000000 -p "[ LOG ]" && exec sudo nice tail -n 60 -s 10 -f /var/log/everything.log | ccze -A'
screen -t 'MEM' -h 0   2 nice -n 19 sh -c 'read -n1 -t1000000 -p "[ MEM ]" && sleep 4 && tput civis; CLS=$`tput clear`; trap "tput cnorm; exit 0" 1 2 3; while :; do free -olt && sleep 2 && echo $CLS; done;'
screen -t 'NET' -h 0   3 nice -n 19 sh -c 'read -n1 -t1000000 -p "[ NET ]" && while :; do /bin/netstat --numeric-ports -a -e --tcp |sort --key=4 && sleep 5; done;'
screen -t 'WWW' lynx http://www.askapache.com/
screen -t '# |ROOT'    4 sh -c 'read -n1 -t1000000 -p "[ ROOT ]" && exec sudo su -'
screen -t 'askapache'      5 sh -c 'read -n1 -t1000000 -p "[ ASKAPACHE ]" && exec sudo su - askapache'
screen -t 'compiler'     6       sh -c 'read -n1 -t1000000 -p "[ srot ]" && exec sudo su - compiler'

#select 5
windowlist


# screen -t 'BASH4'     5 sh -c 'read -n1 -p "[ BASH4 ] && export SHELL=/bin/bash4 && /bin/bash4 -l'
# screen -h 5000 -t 'bash' 1
# screen -h 5000 -t 'root' 2
# sudo -i screen -h 5000 -t 'gator' 3
# $HOME/.ssh/start_control.sh select
# screen -h 100 -t 'log' 4 sudo sh -c 'nice tail -n 60 -s 10 -f /var/log/everything.log | ccze -A'
# screen -h 100 -t 'top' 5 nice top -c
# screen -h 100 -t 'netstat' 6 nice sh -c 'watch -n 30 -t netstat -ane'
# links http://www.askapache.com/






###########################################################################################################################
#
# CUSTOM keybindings
#
# bind ^t screen -t 'TOP' sh -c 'exec sudo nice /usr/bin/top'
# bind ^g screen -t 'LOG' sh -c 'exec sudo nice tail -s 3 -n 25 -f /usr/local/apache/logs/error_log /home/askapache/sites/askapache.com/logs/php_error.log|ccze -A'
# bind ^g screen -t 'gator' -$SHELL $HOME/.ssh/start_control.sh
# bind ^s screen -t 'root' sudo -i
###########################################################################################################################
# bindkey [@var{opts}] [@var{string} [@var{cmd} @var{args}]]
#
# keybindings
#
# remove some stupid / dangerous key bindings
bind k
bind ^k
bind ^.
bind .
bind ^\
bind \\
bind ^h
bind h
bind ^x
bind x
bind }
bind ^}

# Window numbering starts at 1, not 0
bind c screen 1
bind 0 select 10
bind = resize =
bind + resize +1
bind - resize -1
bind _ resize max

bind 'K' kill
bind 'X' lockscreen
bind 'I' login on
bind 'O' login off
bind '}' history


# Prepend/append register [/] to the paste if ^a^] is pressed.  autoindent mode in vi.
register [ "\033:se noai\015a"
register ] "\033:se ai\015a"
bind ^] paste [.]

# A better detach
bind ^D eval 'echo -p "\^\^D%080="' 'command -c detach'
bind -c detach d detach
bind -c detach ^D detach
bind -c detach D pow_detach

# This one is great, restarts/reloads screen
bind . eval 'source /etc/screenrc' 'echo "/etc/screenrc has been reloaded."'

###
# Use the function keys to switch among windows.
##
bindkey -k k1 select 1
bindkey -k k2 select 2
bindkey -k k3 select 3
bindkey -k k4 select 4
bindkey -k k5 select 5
bindkey -k k6 select 6
bindkey -k k7 select 7
bindkey -k k8 select 8
bindkey -k k9 select 9
bindkey -k k; select 10
bindkey -k F1 select 11
bindkey -k F2 select 12
# windows 13-24 are Shift-Fn
#bindkey -k F3 select 13
#bindkey -k F4 select 14
#bindkey -k F5 select 15
#bindkey -k F6 select 16
#bindkey -k F7 select 17
#bindkey -k F8 select 18
#bindkey -k F9 select 19
#bindkey -k FA select 20



# vim: tw=78 ts=3 sw=3 et nowrap ft=screen paste nonumber nofoldenable

```




Here is my custom-built (for 256-colors + screen), I'd rather edit this and keep it backed up than fiddle with screen's termcapinfo stuff.
```
#       Reconstructed via infocmp from file: /usr/share/terminfo/p/putty-256color
putty-256color|PuTTY 0.58 with xterm 256-colors,
        am, bce, bw, ccc, hs, mir, msgr, xenl, xon,
        colors#256, it#8, ncv#22, pairs#32767,
        acsc=``aaffggjjkkllmmnnooppqqrrssttuuvvwwxxyyzz{{||}}~~,
        bel=^G, blink=\E[5m, bold=\E[1m, cbt=\E[Z, civis=\E[?25l,
        clear=\E[H\E[J, cnorm=\E[?25h, cr=^M,
        csr=\E[%i%p1%d;%p2%dr, cub=\E[%p1%dD, cub1=^H,
        cud=\E[%p1%dB, cud1=\ED, cuf=\E[%p1%dC, cuf1=\E[C,
        cup=\E[%i%p1%d;%p2%dH, cuu=\E[%p1%dA, cuu1=\EM,
        dch=\E[%p1%dP, dch1=\E[P, dl=\E[%p1%dM, dl1=\E[M,
        dsl=\E]0;\007, ech=\E[%p1%dX, ed=\E[J, el=\E[K, el1=\E[1K,
        enacs=\E(B\E)0, flash=\E[?5h\E[?5l, fsl=^G, home=\E[H,
        hpa=\E[%i%p1%dG, ht=^I, hts=\EH, il=\E[%p1%dL, il1=\E[L,
        ind=^J, indn=\E[%p1%dS, initc@,
        is2=\E7\E[r\E[m\E[?7h\E[?1;4;6l\E[4l\E8\E>\E]R,
        kb2=\E[G, kbs=\177, kcan=^C, kcbt=\E[Z, kcub1=\E[D,
        kcud1=\E[B, kcuf1=\E[C, kcuu1=\E[A, kdch1=\E[3~,
        kend=\E[4~, kf1=\E[11~, kf10=\E[21~, kf11=\E[23~,
        kf12=\E[24~, kf13=\E[25~, kf14=\E[26~, kf15=\E[28~,
        kf16=\E[29~, kf17=\E[31~, kf18=\E[32~, kf19=\E[33~,
        kf2=\E[12~, kf20=\E[34~, kf3=\E[13~, kf4=\E[14~,
        kf5=\E[15~, kf6=\E[17~, kf7=\E[18~, kf8=\E[19~, kf9=\E[20~,
        khome=\E[1~, kich1=\E[2~, kmous=\E[M, knp=\E[6~, kpp=\E[5~,
        kspd=^Z, nel=^M^J, oc=\E]R, op=\E[39;49m, rc=\E8, rev=\E[7m,
        ri=\EM, rin=\E[%p1%dT, rmacs=^O, rmam=\E[?7l,
        rmcup=\E[2J\E[?47l, rmir=\E[4l, rmpch=\E[10m,
        rmso=\E[27m, rmul=\E[24m, rs2=\Ec\E[?1000l\E[?25h,
        s0ds=\E[10m, s1ds=\E[11m, s2ds=\E[12m, sc=\E7,
        setab=\E[48;5;%p1%dm, setaf=\E[38;5;%p1%dm, sgr0=\E[0m,
        smacs=^N, smam=\E[?7h, smcup=\E[?47h, smir=\E[4h,
        smpch=\E[11m, smso=\E[7m, smul=\E[4m, tbc=\E[3g, tsl=\E]0;,
        u6=\E[%i%p1%d;%p2%dR, u7=\E[6n, u8=\E[?6c, u9=\E[c,
        vpa=\E[%i%p1%dd,

```

---

### Post by alzaf on 2010-10-27
Just discovered screen and wanted to mention how great it is. Only started using it but here is my .screen file which has two 'consoles' split in a terminal which is handy programming when using one for editing code via vim and the other for running the code.

```
hardstatus on
hardstatus alwayslastline
hardstatus string "%{.bW}%-w%{.rW}%n %t%{-}%+w %=%{..G} %{..Y} %m/%d %C%a "
defscrollback 5000
startup_message off
screen 0
title "main"
split on
focus down
screen 1 
title "console"
focus up

```

---

