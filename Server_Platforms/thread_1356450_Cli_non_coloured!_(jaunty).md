---
title: "Cli non coloured!? (jaunty)"
date: 2009-12-16
forum: Server Platforms
---

### Post by mudcow007 on 2009-12-16
hello all

im using GNOME terminal 2.26.0

when i use the command
Code:

```
ls /etc
```

i see different colours but when i run Asterisk all i see is black and white.

in "colors" within the terminal its currently set to "Use colors from system theme"

i have also just tried the "Konsole" that also doesnt show colours when running Asterisk

any ideas? or any other tests i could run?

thanks

---

### Post by ajgreeny on 2009-12-16
Have a look at your hidden ~/.bashrc file.  There are references to colour in that which may be having an effect on your terminal's colours.  Here is the possibly relevant bit of mine.
> # set a fancy prompt (non-color, unless we know we "want" color)
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


There are also aliases set for the various "ls" commands, either in that file or perhaps the ~/.bash_aliases file.  Again, here's mine.
> # enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
fi

---

### Post by mudcow007 on 2009-12-16
thanks for the reply!

you will have to bear with me im a ubuntu noob!!

the ~/.bashrc file is in /etc/ and is bash.bashrc ?

if so this is the contents of mine

```
# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#    ;;
#*)
#    ;;
#esac

# enable bash completion in interactive shells
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

# sudo hint
if [ ! -e $HOME/.sudo_as_admin_successful ]; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
	cat <<-EOF
	To run a command as administrator (user "root"), use "sudo <command>".
	See "man sudo_root" for details.
	
	EOF
    fi
    esac
fi

# if the command-not-found package is installed, use it
if [ -x /usr/lib/command-not-found ]; then
	function command_not_found_handle {
	        # check because c-n-f could've been removed in the meantime
                if [ -x /usr/lib/command-not-found ]; then
		   /usr/bin/python /usr/lib/command-not-found -- $1
                   return $?
		else
		   return 127
		fi
	}
fi
```

---

### Post by ajgreeny on 2009-12-16
A good question, and if I remember correctly, there was no .bashrc file in my home folder when I installed karmic 9.10, so I made one from the bare bones of a previous ubuntu version.  Similarly with the .bash_aliases file which is not present in ubuntu at all, I think, unless you make one, and not used if you don't uncomment the lines that refer to it in the .bashrc file.

As you are asking such questions about the terminal, I assumed you were more used to linux than you seem to be, and therefore did not realise that you would not know the accepted way that **~/** is used to refer to the user's home folder; it can even be used in some, if not all commands that need a pathway.  However, if you did a ```
locate bashrc
``` in terminal and it only found the etc version, then my assumption about the home one not being present by default is obviously correct.

I did not know what asterix is either, but now see it is a PBX package, and I suspect that like most terminal apps there is no colour output, just plain text in your terminal profile's standard text colour.

---

### Post by mudcow007 on 2009-12-18
Hi sorry didnt have a chance to look at this yesterday!

i did the command ```
locate bashrc
```

this is what was returned

```
/etc/bash.bashrc
/etc/bash.bashrc.orig
/etc/bash.bashrc~
/etc/skel/.bashrc
/home/danny/.bashrc
/root/.bashrc
/usr/share/base-files/dot.bashrc
/usr/share/doc/adduser/examples/adduser.local.conf.examples/bash.bashrc
/usr/share/doc/adduser/examples/adduser.local.conf.examples/skel/dot.bashrc
```

if i do ```
vi cd /root/.bashrc 
``` it says "new file"

but if i go to etc/bash.bashrc it contains all the code that i posted earlier. is this the correct file i need to amend?

just checking through the contents of /etc/bash.bashrc all i have that mentions color is

```
# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

``` which seems way different to yours :(

---

### Post by mudcow007 on 2009-12-18
sorry im an Idiot ](*,) 

i was editing the wrong bash file!!

right i found ```
# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
# PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

```

in the real bash file. commenting the PS1 lines only resulted in the cli prompt turning lime green!

all i want is that errors are shown as Red notices Yellow etc.

if anyone can help out there :)

---

### Post by mudcow007 on 2009-12-21
hi guys i was looking more into this weekend i think i may have called it the wrogn thing what i want is "syntax highlighting" here is a screen dump of feisty fawn server 

[IMG]http://i25.photobucket.com/albums/c81/mudcow007/Screenshot.gif[/IMG]

our Jaunty server just has black and white?

anyone any ideas??

---

### Post by dc46and2 on 2010-01-02
In your original post, you said you are getting color when running ls, so this is not a problem with your terminal emulator or with bash.  This is probably an issue with asterisk--either you are using two different versions, one of which doesn't include the color feature, or you just need to enable the color feature somewhere in the configuration or with a command-line argument.

Sorry I don't use jaunty, feisty or asterisk so I can't do more, but hopefully this will get you headed in the right direction.  Googling "asterisk color" gets some promising-looking hits.

---

