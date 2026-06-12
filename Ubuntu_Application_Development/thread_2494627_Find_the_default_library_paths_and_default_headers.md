---
title: "Find the default library paths and default headers include paths"
date: 2024-01-22
forum: Ubuntu Application Development
---

### Post by luca-ub-1993 on 2024-01-22
[COLOR=#000000]I'm on an Ubuntu 22.04 system and I'm working with C language and libraries.[/COLOR]

[COLOR=#000000]I know ( from different books, included "The Linux Programming Interface" by Kerrisk ) that this algorithm is used when looking for runtime shared libraries locations ( I just omitted the preloaded libraries for the sake of simplicity ) :[/COLOR]

[COLOR=#000000]When RUNPATH field is specified (i.e. DT_RUNPATH is non-empty)[/COLOR]

[COLOR=#000000]1 ) LD_LIBRARY_PATH[/COLOR]
[COLOR=#000000]2 ) runpath (DT_RUNPATH field)[/COLOR]
[COLOR=#000000]3 ) ld.so.cache[/COLOR]
[COLOR=#000000]4 ) default library paths (/lib and /usr/lib)[/COLOR]

[COLOR=#000000]In the absence of RUNPATH (i.e. DT_RUNPATH is empty string)[/COLOR]

[COLOR=#000000]1 ) RPATH[/COLOR]
[COLOR=#000000]2 ) LD_LIBRARY_PATH[/COLOR]
[COLOR=#000000]3 ) ld.so.cache[/COLOR]
[COLOR=#000000]4 ) default library paths (/lib and /usr/lib)[/COLOR]

[COLOR=#000000]The problem is that most books say that generally speaking the default library paths are /lib and /usr/lib but they don't mention [/COLOR][B]HOW I CAN GET THE EXACT DEFAULT LIBRARY PATHS FOR MY SYSTEM. What command can I use on my Ubuntu 22.04 system ?

[B]What about the default headers include paths ? What command can I use the get them ?

And finally what is the specific algorithm used in my ubuntu system when dealing with "headers.h" vs <headers.h> ?[/B][/B]

---

### Post by TheFu on 2024-01-22
$ more /etc/ld.so.conf.d/*

has the defaults.

I've never heard or used DT_RUNPATH.  Generally, people set the value of LD_LIBRARY_PATH in their start script for any programs, if the defaults aren't ok.  It is common to setup a complex program with a standard directory structure
```
FOO
&#9500;&#9472;&#9472; bin
&#9500;&#9472;&#9472; doc
&#9500;&#9472;&#9472; etc
&#9500;&#9472;&#9472; include
&#9500;&#9472;&#9472; lib
&#9492;&#9472;&#9472; src

```
The set FOO_HOME to the top directory value and use that environment variable to locate programs, configs, documentation and libraries.  You might have include/ and src/ on the developer's machines too, but not for deployment. Subdirectories under src and include are expected for each program or library specific to the project.

As for default header paths, that is 100% dependent on the compiler being used.  Look in that documentation.

```
And finally what is the specific algorithm used in my ubuntu system when dealing with "headers.h" vs <headers.h> ?
```
Ubuntu doesn't do anything different for this than any other platform, including MS-Windows.  Typically, <headers> are in the system locations and "headers" are in the specific project.  It is common to have subdirectories for the "headers", since they would be included in the Makefile to point at the top directory - 

```
-I $FOO_HOME/include
```

The same for libraries - 

```
-L $FOO_HOME/lib
```

You are using Makefiles or cMakefiles right?  Don't reinvent the wheel.

---

### Post by breakdaze on 2024-01-27
What  TheFu said. Which toolchain, how did you install it, where did you get it? Which Linux version? You are not giving us much to go on.

<header.h> is going to be part of your C standard library as set up in your toolchain path for whatever you are using.

You might need to use sudo and edit your /etc/profile

On Slackware (don't know about Ubuntu, but should be the same) the top of said file:

```
# /etc/profile: This file contains system-wide defaults used by
# all Bourne (and related) shells.

# Set the values for some environment variables:
# add your custom variables for global use:
PATH=/opt/gcc-13.2/bin:$PATH
export LD_LIBRARY_PATH=/opt/gcc-13.2/lib

```

Add whatever global environmental variables to the above as needed, but it all depends on where you put stuff.
Just add what is required by your toolchain to make it work. RTFM - Read the fine manual.
The above example assumes you put the version 13.2 gcc libraries in /opt/gcc-13.2/lib

You can alternately edit your bash environment for just the end user using the toolchain.

This is Linux, you can put anything where you want, just tell the system where it is with the correct variables.

Also, maybe this is not out of date: [https://wiki.ubuntu.com/ToolChain](https://wiki.ubuntu.com/ToolChain)

---

### Post by TheFu on 2024-01-27
^^^^^ bad advice to modify /etc/profile.  This applies to all Linuxen, including slackware, BTW.  It may seem easier, but it is a bad habit.  Eventually, you'll end up on a system that you don't control and won't be allowed to modify system-level stuff like this.  

Never edit the /etc/profile.  Edit startup settings on a per-userid basis, in their HOME directories.  If you need to change all new normal user's settings, there are skeleton versions under /etc/ somewhere.  I've never done that in 30 yrs as an admin because it is a great way to break an OS.  Just don't do it.

Also, don't assume people are using sh, ksk, bash as their shells.  Lots of programs use zsh or psh or tcsh.  I did when I was programming. These days, I'm lazy and find that bash provides all I want (and more).

---

### Post by breakdaze on 2024-01-27
Ah, no? Well, I mean, why is /etc/profile there with comments if we are not meant to edit it? I'm not saying you don't have great advice here, but can you please provide an example of how things can go wrong? Yeah, of course, editing .bashrc or .bash_profile is better. One is for login shells, and the other is for interactive shells, if I recall correctly. So, I use:

```
breakdaze@ace:~/src/gdb/gdb-14.1$ cat ~/.bashrc
# ~/.bashrc
. /etc/profile
. ~/.bash_profile
breakdaze@ace:~/src/gdb/gdb-14.1$ cat ~/.bash_profile
set PS1="\$\u\h\:\$ "
export PATH=$PATH:~/scripts

```

Because I read if you edit .bashrc as above, it will always use .bash_profile since most end users don't care if they differ.
Also, there have been valid discussions about not using export too much and just use set depending.

Also, about bash vs. another shell, you are quite correct, I should not have assumed! It is true it could differ.

As far as the OP's question, again, we have no idea if they installed their compiler from source, if it is from a package, and which compiler it actually is!

But, if it was the GNU C Library built from source, they should read the docs: [https://www.gnu.org/software/libc/manual/html_node/Configuring-and-compiling.html](https://www.gnu.org/software/libc/manual/html_node/Configuring-and-compiling.html)
[https://www.gnu.org/software/autoconf/manual/autoconf-2.67/html_node/Default-Prefix.html](https://www.gnu.org/software/autoconf/manual/autoconf-2.67/html_node/Default-Prefix.html)

default prefix is /usr/local

However, if it is a package, just look at the filelist for the package on the www page: [https://packages.ubuntu.com/jammy/amd64/gcc-11/filelist](https://packages.ubuntu.com/jammy/amd64/gcc-11/filelist)

> 
File list of package gcc-11 in jammy of architecture amd64

/usr/bin/gcc-11
/usr/bin/gcc-ar-11
/usr/bin/gcc-nm-11
/usr/bin/gcc-ranlib-11
/usr/bin/gcov-11
/usr/bin/gcov-dump-11
/usr/bin/gcov-tool-11
/usr/bin/lto-dump-11
/usr/bin/x86_64-linux-gnu-gcc-11
/usr/bin/x86_64-linux-gnu-gcc-ar-11
/usr/bin/x86_64-linux-gnu-gcc-nm-11
/usr/bin/x86_64-linux-gnu-gcc-ranlib-11
/usr/bin/x86_64-linux-gnu-gcov-11
/usr/bin/x86_64-linux-gnu-gcov-dump-11
/usr/bin/x86_64-linux-gnu-gcov-tool-11
/usr/bin/x86_64-linux-gnu-lto-dump-11
/usr/lib/gcc/x86_64-linux-gnu/11/collect2
/usr/lib/gcc/x86_64-linux-gnu/11/libcc1.so
/usr/lib/gcc/x86_64-linux-gnu/11/libgomp.spec
/usr/lib/gcc/x86_64-linux-gnu/11/libitm.spec
/usr/lib/gcc/x86_64-linux-gnu/11/liblto_plugin.so
/usr/lib/gcc/x86_64-linux-gnu/11/libsanitizer.spec
/usr/lib/gcc/x86_64-linux-gnu/11/lto-wrapper
/usr/lib/gcc/x86_64-linux-gnu/11/lto1
/usr/lib/gcc/x86_64-linux-gnu/11/plugin/libcc1plugin.so
/usr/lib/gcc/x86_64-linux-gnu/11/plugin/libcc1plugin.so.0
/usr/lib/gcc/x86_64-linux-gnu/11/plugin/libcc1plugin.so.0.0.0
/usr/lib/gcc/x86_64-linux-gnu/11/plugin/libcp1plugin.so
/usr/lib/gcc/x86_64-linux-gnu/11/plugin/libcp1plugin.so.0
/usr/lib/gcc/x86_64-linux-gnu/11/plugin/libcp1plugin.so.0.0.0
/usr/share/doc/gcc-11
/usr/share/doc/gcc-11-base/NEWS.gz
/usr/share/doc/gcc-11-base/NEWS.html
/usr/share/doc/gcc-11-base/README.Bugs
/usr/share/doc/gcc-11-base/README.ssp
/usr/share/doc/gcc-11-base/changelog.gz
/usr/share/doc/gcc-11-base/gcc/changelog.gz
/usr/share/doc/gcc-11-base/gomp/changelog.gz
/usr/share/doc/gcc-11-base/itm/changelog.gz
/usr/share/doc/gcc-11-base/quadmath/changelog.gz
/usr/share/doc/gcc-11-base/sanitizer/changelog.gz
/usr/share/lintian/overrides/gcc-11
/usr/share/man/man1/gcc-11.1.gz
/usr/share/man/man1/gcc-ar-11.1.gz
/usr/share/man/man1/gcc-nm-11.1.gz
/usr/share/man/man1/gcc-ranlib-11.1.gz
/usr/share/man/man1/gcov-11.1.gz
/usr/share/man/man1/gcov-dump-11.1.gz
/usr/share/man/man1/gcov-tool-11.1.gz
/usr/share/man/man1/lto-dump-11.1.gz
/usr/share/man/man1/x86_64-linux-gnu-gcc-11.1.gz
/usr/share/man/man1/x86_64-linux-gnu-gcc-ar-11.1.gz
/usr/share/man/man1/x86_64-linux-gnu-gcc-nm-11.1.gz
/usr/share/man/man1/x86_64-linux-gnu-gcc-ranlib-11.1.gz
/usr/share/man/man1/x86_64-linux-gnu-gcov-11.1.gz
/usr/share/man/man1/x86_64-linux-gnu-gcov-dump-11.1.gz
/usr/share/man/man1/x86_64-linux-gnu-gcov-tool-11.1.gz
/usr/share/man/man1/x86_64-linux-gnu-lto-dump-11.1.gz



---

### Post by breakdaze on 2024-01-27
Quick note, I suppose we would want to append the LD_LIBRARY_PATH variable to the end of the existing in case you have more than one path to the libraries:```
export LD_LIBRARY_PATH=/path/to/my/libraries:$LD_LIBRARY_PATH

```

Again, building from source using Autoconf and make, adjust configure.in or configure.ac with the macro , the prefix used would be then in your configure: ac_default_prefix=/usr/local

for example in configure.ac you can specify it with the macro
```
# Set default installation prefix
AC_PREFIX_DEFAULT([/usr/local])
```

---

### Post by TheFu on 2024-01-27
I think there's a huge misunderstanding.  I didn't mean to imply that anyone modify their login scripts.  I intended to say modify the LD_LIBRARY_PATH for the program startup script.  This would usually be in the FOO/bin/start script or whatever you choose to name it.

Modifying the LD_LIBRARY_PATH is like replacing the system python with some newer release.  It can break things.  

In short, avoid making system-wide changes unless it is absolutely required for every program on the system to function correctly.  Minimize changes to only impact the specific programs that need those changes.  Avoiding issues is a core idea for any good developer and admin.

---

### Post by breakdaze on 2024-01-27
Ah, good point! I suppose we don't want every compiler looking for libraries in the same place!

---

### Post by TheFu on 2024-01-27
> **breakdaze said:**
> Ah, good point! I suppose we don't want every compiler looking for libraries in the same place!

Less about the compiler, more about the other things on the system that could be broken.

With C, it doesn't matter since all calls are standard across all platforms. With C++, the name mangling is different between each compiler.

Our backgrounds are so different, we both come at this with our built-in assumptions.

---

### Post by breakdaze on 2024-01-28
Yeah... different assumptions.  :)

With C, it doesn't matter? What if you have gcc and clang installed simultaneously? Tanget: [https://llvm.org/](https://llvm.org/)

But, that's besides your point. I do think your point about not mucking up system wide script files is a good one.

Also, let's not get started on systemd vs sysV init or anything ;) I actually don't have strong opinions about that.

For reference, this is what Slackware 15.0 offers for the /etc/profile out of the box... what does Ubuntu do, by the way? I don't currently have an Ubuntu running.
```
# /etc/profile: This file contains system-wide defaults used by
# all Bourne (and related) shells.

# Set the values for some environment variables:
export MINICOM="-c on"
export HOSTNAME="`cat /etc/HOSTNAME`"
export LESSOPEN="|lesspipe.sh %s"

# Setting a default $LESS was something inherited from SLS many years ago,
# but apparently the previous setting of "-M" causes display issues with
# some programs (i.e. git log). Adding "-R" as well fixes this, but some
# folks have concerns about the security of this option (I think it's
# actually "-r" that's the dangerous one). Anyway, it might be best to just
# leave this unset by default. Uncomment it if you like, or set up your
# own definition or aliases on a per-account basis.
#export LESS="-M -R"

# If the user doesn't have a .inputrc, use the one in /etc.
if [ ! -r "$HOME/.inputrc" ]; then
  export INPUTRC=/etc/inputrc
fi

# Set the default system $PATH:
PATH="/usr/local/bin:/usr/bin:/bin:/usr/games"

# For root users, ensure that /usr/local/sbin, /usr/sbin, and /sbin are in
# the $PATH.  Some means of connection don't add these by default (sshd comes
# to mind).
if [ "`id -u`" = "0" ]; then
  echo $PATH | grep /usr/local/sbin 1> /dev/null 2> /dev/null
  if [ ! $? = 0 ]; then
    PATH=/usr/local/sbin:/usr/sbin:/sbin:$PATH
  fi
fi

# I had problems with the backspace key using 'eval tset' instead of 'TERM=',
# but you might want to try it anyway instead of the section below it.  I
# think with the right /etc/termcap it would work.
# eval `tset -sQ "$TERM"`

# Set TERM to linux for unknown type or unset variable:
if [ "$TERM" = "" -o "$TERM" = "unknown" ]; then
 TERM=linux
fi

# Set ksh93 visual editing mode:
if [ "$SHELL" = "/bin/ksh" ]; then
  VISUAL=emacs
#  VISUAL=gmacs
#  VISUAL=vi
fi

# Set a default shell prompt:
#PS1='`hostname`:`pwd`# '
if [ "$SHELL" = "/bin/pdksh" ]; then
 PS1='! $ '
elif [ "$SHELL" = "/bin/ksh" ]; then
 PS1='! ${PWD/#$HOME/~}$ '
elif [ "$SHELL" = "/bin/zsh" ]; then
 PS1='%n@%m:%~%# '
elif [ "$SHELL" = "/bin/ash" ]; then
 PS1='$ '
else
 PS1='\u@\h:\w\$ '
fi
PS2='> '
export PATH DISPLAY LESS TERM PS1 PS2

# Default umask.  A umask of 022 prevents new files from being created group
# and world writable.
umask 022

# Notify user of incoming mail.  This can be overridden in the user's
# local startup file (~/.bash.login or whatever, depending on the shell)
if [ -x /usr/bin/biff ]; then
 biff y 2> /dev/null
fi

# Append any additional sh scripts found in /etc/profile.d/:
for profile_script in /etc/profile.d/*.sh ; do
  if [ -x $profile_script ]; then
    . $profile_script
  fi
done
unset profile_script

```
# Append any additional sh scripts found in /etc/profile.d/: <----- Ah, that's a nice touch.

---

