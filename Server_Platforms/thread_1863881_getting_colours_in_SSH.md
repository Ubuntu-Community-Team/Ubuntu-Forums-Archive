---
title: "getting colours in SSH"
date: 2011-10-18
forum: Server Platforms
---

### Post by bigmonmulgrew on 2011-10-18
Hi
I'm using putty for ssh access to ubuntu server 11.04
I noticed that when accessing the server directly (well in a VM anyway) the terminal has colours.
When accessing through SSH I only get white/grey. Is there a way to enable the colours while accessing via ssh. Its much easiter on the eye.

---

### Post by aeiah on 2011-10-18
perhaps gnome-terminal (or whatever ubuntu uses on the desktop) has its own way of laying out colours. the standard way is to put the information in your ~/.bashrc (on your VM)

might be best to take someone elses .bashrc rather than spend ages messing with different things. arch forums probably have loads of .bashrc colour configs.

---

### Post by Jonathan L on 2011-10-18
> **bigmonmulgrew said:**
> Hi
I'm using putty for ssh access to ubuntu server 11.04
I noticed that when accessing the server directly (well in a VM anyway) the terminal has colours.
When accessing through SSH I only get white/grey. Is there a way to enable the colours while accessing via ssh. Its much easiter on the eye.

Hi Big

Colour in ls is controlled by a number of things, but ultimately it's an alias
```
alias ls='ls --color=auto'

```This is normally set inside an individual user's .bashrc:
```
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    ...
fi
```Hope that helps.

I've just tried it from Gnome terminal and an xterm, logged in via ssh to an Ubuntu server, and I'd be surprised if putty didn't behave the same.  You can just alias ls and you'll get the colours.

Kind regards
Jonathan

---

### Post by bigmonmulgrew on 2011-10-19
Ok that works for adding colour to ls but there are lost of places there is colour.
like in nano for example.
I'll loook and see if I can find a colour profile but ideally is there a way to make the ssh session use the same colour set as logging in directly

---

### Post by bigmonmulgrew on 2011-10-19
I was checking my bashrc file and noticed colours are enables via ssh
For some reason putty seems to interpret white as grey which is irritating since I find the white much clearer.
The following is the .bashrc file section which refers to colour

```
# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
	# We have color support; assume it's compliant with Ecma-48
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# a case would tend to support setf rather than setaf.)
	color_prompt=yes
    else
	color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi
```

This leaves me wondering why things like nano are coloured when accessing directly

---

### Post by bigmonmulgrew on 2011-10-19
ok getting there I googled nano colour profiles and found an article on how to reconfigure nano by createng a .nanorc file.
This does much more than colour. The article can be found [here]("http://www.linuxhowtos.org/System/config_nano.htm")

MY first problem was that copying the code added a space and CRLF at the end of lines that wrap. This was on line 103. Delinting the space and CRLF.
I'm now getting 3 errors (2 of which are repeated several  times)

```
Error in /home/admindm/.nanorc on line 121: Background colour "brightgreen" cannot be bright

Error in /home/admindm/.nanorc on line 141: Bad regex "\": Trailing backslash

Error in /home/admindm/.nanorc on line 141: Bad regex "\": Trailing backslash

Error in /home/admindm/.nanorc on line 141: Bad regex "\": Trailing backslash

Error in /home/admindm/.nanorc on line 141: Bad regex "\": Trailing backslash

Error in /home/admindm/.nanorc on line 141: Bad regex "\": Trailing backslash

Error in /home/admindm/.nanorc on line 141: Bad regex "\": Trailing backslash

Error in /home/admindm/.nanorc on line 141: Bad regex "\": Trailing backslash

Error in /home/admindm/.nanorc on line 141: Bad regex "\": Trailing backslash

Error in /home/admindm/.nanorc on line 141: Bad regex "\": Trailing backslash

Error in /home/admindm/.nanorc on line 142: Bad regex "\": Trailing backslash

Error in /home/admindm/.nanorc on line 142: Bad regex "\": Trailing backslash

Error in /home/admindm/.nanorc on line 142: Bad regex "\": Trailing backslash

Error in /home/admindm/.nanorc on line 142: Bad regex "\": Trailing backslash

Error in /home/admindm/.nanorc on line 142: Bad regex "\": Trailing backslash

Press Enter to continue starting nano.

```

I dont know enough about linux to solve this but from what I can tell the first error referes to trying to turn square brackets in javascript files bright green and the other two refer to trying to turn backslashes blue in bash files. I've decided I can live without those so deleted the offending lines.
My .nanorc file including the errors is below

```
# Use auto-indentation 
set autoindent 
 
# Backup files to filename~ 
set backup 
 
# Use cut to end of line with ^K by default 
set cut 
 
# Enable ~/.nano_history for saving and reading search/replace strings. 
# set historylog 
 
# Don't convert files from DOS/Mac format 
set noconvert 
 
# Don't follow symlinks when writing files 
# set nofollow 
 
# Don't display the help lists at the bottom of the screen 
# set nohelp 
 
# Don't wrap text at all 
set nowrap 
 
# Use smooth scrolling as the default 
set smooth 
 
# Use this spelling checker instead of the internal one.  This option 
# does not properly have a default value. 
set speller "aspell -c" 
 
# Allow nano to be suspended with ^Z 
# set suspend 
 
# Use this tab size instead of the default; it must be greater than 0 
# set tabsize 8 
 
# Save automatically on exit, don't prompt 
# set tempfile 
 
# Enable ~/.nano_history for saving and reading search/replace strings. 
# set historylog 
 
# Disallow file modification, why would you want this in an rc file? ;) 
# set view 
 
#Color Syntax Highlighting 
syntax "c-file" "\.(c|h)$" 
color red "\<[A-Z_]{2,}\>" 
color green "\<(float|char|int|void|static|const|struct)\>" 
color brightyellow "\<(if|while|do|else|case|switch)\>" 
color brightcyan "^#(  )*(define|include|ifn?def|endif|elif|else|if)" 
color brightyellow "<[^=       ]*>" ""(.|[^"])*"" 
color brightyellow start=""(\\.|[^\"])*\\( |   )*$" end="^(\\.|[^\"])*"" 
color brightblue "//.*" 
color brightblue start="/\*" end="\*/" 
 
syntax "HTML" "\.html$" 
color blue start="<" end=">" 
color red "&[^;        ]*;" 
 
syntax "TeX" "\.tex$" 
color green "\\.|\\[A-Za-z]*" 
color magenta "[{}]" 
color blue "%.*" 
 
syntax "mutt" 
color green "^>.*" 
 
syntax "php" ".*/*.php$" 
color brightwhite "\{|\}|\." 
color red "('[^']*')" 
color red "\"[^\"]*\"" 
color brightblue "(\$([[:alpha:]_]|->)*)" 
color brightgreen "((\$(([[:alpha:]_0-9])+\->)+)[[:alpha:]_0-9]+\()" 
color yellow " (if|else if|else|return|case|break)" 
color yellow "\|\||\?|!|\||&&|=|;|\(|\)" 
color red "false|true" 
color brightwhite "[[:space:]]+debug|[[:space:]]+echo|\$this\->debug" 
color cyan "//.*" 
color cyan start="/\*" end="\*/" 
 
syntax "groff" "\.ms$" "\.mm$" "\.me$" "\.tmac$" "^tmac." ".rof" 
color cyan "^\.ds [^ ]*" 
color cyan "^\.nr [^ ]*" 
color brightmagenta "\\." 
color brightmagenta "\\f." 
color brightmagenta "\\f\(.." 
color brightmagenta "\\s(\+|\-)?[0-9]" 
color cyan "(\\|\\\\)n." 
color cyan "(\\|\\\\)n\(.." 
color cyan start="(\\|\\\\)n\[" end="]" 
color brightgreen "^\. *[^ ]*" 
color yellow "^\.\\\".*$" 
color green "(\\|\\\\)\*." 
color green "(\\|\\\\)\*\(.." 
color green start="(\\|\\\\)\*\[" end="]" 
color brightred "\\\(.." 
color brightred start="\\\[" end="]" 
color brightcyan "\\\\\$[1-9]" 
 
syntax "perl" "\.p[lm]$" 
color red "\<(accept|alarm|atan2|bin(d|mode)|c(aller|h(dir|mod|op|own|root)|lose(dir)?|onnect|os|rypt)|d(bm(close|open)|efined|elete|ie|o|ump)|e(ach|of|val|x(ec|ists|it|p))|f(cntl|ileno|lock|ork)|get(c|login|peername|pgrp|ppid|priority|pwnam|(host|net|proto|serv)byname|pwuid|grgid|(host|net)byaddr|protobynumber|servbyport)|([gs]et|end)(pw|gr|host|net|proto|serv)ent|getsock(name|opt)|gmtime|goto|grep|hex|index|int|ioctl|join|keys|kill|last|length|link|listen|local(time)?|log|lstat|m|mkdir|msg(ctl|get|snd|rcv)|next|oct|open(dir)?|ord|pack|pipe|pop|printf?|push|q|qq|qx|rand|re(ad(dir|link)?|cv|do|name|quire|set|turn|verse|winddir)|rindex|rmdir|s|scalar|seek|seekdir|se(lect|mctl|mget|mop|nd|tpgrp|tpriority|tsockopt)|shift|shm(ctl|get|read|write)|shutdown|sin|sleep|socket(pair)?|sort|spli(ce|t)|sprintf|sqrt|srand|stat|study|substr|symlink|sys(call|read|tem|write)|tell(dir)?|time|tr|y|truncate|umask|un(def|link|pack|shift)|utime|values|vec|wait(pid)?|wantarray|warn|write)\>"
color magenta "\<(continue|else|elsif|do|for|foreach|if|unless|until|while|eq|ne|lt|gt|le|ge|cmp|x|my|sub|use|package|can|isa)\>" 
color cyan start="[$@%]" end="( |\\W|-)" 
color yellow "".*"|qq\|.*\|" 
color white "[sm]/.*/" 
color white start="(^use| = new)" end=";" 
color green "#.*" 
color yellow start="<< 'STOP'" end="STOP" 
 
syntax "Java source" "\.java$" 
color green "\<(boolean|byte|char|double|float|int|long|new|short|this|transient|void)\>" 
color red "\<(break|case|catch|continue|default|do|else|finally|for|if|return|switch|throw|try|while)\>" 
color cyan "\<(abstract|class|extends|final|implements|import|instanceof|interface|native|package|private|protected|public|static|strictfp|super|synchronized|throws|volatile)\>" 
color red ""[^"]*"" 
color yellow "<(true|false|null)>" 
color blue "//.*" 
color blue start="/\*" end="\*/" 
color brightblue start="/\*\*" end="\*/" 
color brightgreen,brightgreen "[       ]+$" 
 
syntax "nanorc" "[\.]*nanorc$" 
color white "^ *(set|unset).*$" 
color cyan "^ *(set|unset) (autoindent|backup|const|cut|fill|keypad|multibuffer|noconvert|nofollow|nohelp|nowrap|operatingdir|preserve|quotestr|regexp|smooth|speller|suspend|tabsize|tempfile|historylog|view)" 
color brightwhite "^ *syntax [^ ]*" 
color brightblue "^ *set\>" "^ *unset\>" "^ *syntax\>" 
color white "^ *color\>.*" 
color yellow "^ *color (bright)?(white|black|red|blue|green|yellow|magenta|cyan)\>" 
color magenta "^ *color\>" 
color green "^#.*$" 
 
syntax "bash" "\.sh$" 
color brightblack "#.*" 
color brightyellow "\(" "\)" "\{" "\}" 
color red "\<[A-Z_]{2,}\>" 
color red "[\$\*\'\`\|\=]" 
color brightblue "\[.*\]" 
color green "\<-e\>" "\<-d\>" "\<-f\>" "\<-r\>" "\<-g\>" "\<-u\>" "\<-u\>" "\<-w\>" "\<-x\>" "\<-L\>" 
color green "\<-eq\>" "\<-ne\>" "\<-gt\>" "\<-lt\>" "\<-ge\>" "\<-le\>" "\<-s\>" "\<-n\>" "\<-z\>" 
color blue "\" "\" "\" "\" "\" "\" "\" "\" "\" 
color blue "\" "\" "\" "\" "\" 
color brightwhite "\.*"

```

As I've basically managed to do what I set out for I'm marking this thread as solved but if anyone can suggest fixes to the above errors I'd appreciate it.

---

### Post by bigmonmulgrew on 2011-10-19
ok so much for that it only seems to colour the .bashrc file

---

### Post by CharlesA on 2011-10-19
Hrm, I get colors fine in Putty on my 10.04 boxes. I haven't messed with .bash_rc on either of them.

That being said, I don't use nano for colors - if I want colors, I use vim. ;)

---

### Post by bigmonmulgrew on 2011-10-20
quick update
The main thing annoying me about putty was the grey text. Annoyingly I blamed this on the system and not on putty. Its a little of both. In the putty settings there are settings for colours. Not many but the main ones are there.

I used puttys colour settings to set text to white instead of grey. It also has a setting to antialias text which appears to be clearer, and you can also select font. Personally I think the current font size is ok but I can see how increasing it would be of benefit. So now my shh sessions now almost match accessing the server directly.

I'm still left with colours not working properly in nano though. I dont use it a lot. Normally I udit the files locally and then upload them.

I may take another look at vim but when I tried it I decided I prefered nano.

---

