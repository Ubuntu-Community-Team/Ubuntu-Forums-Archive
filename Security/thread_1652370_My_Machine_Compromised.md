---
title: "My Machine Compromised?"
date: 2010-12-24
forum: Security
---

### Post by tech newbie on 2010-12-24
Out of curiosity I decided to run rkhunter and chkrootkit.
I ran
```
sudo chkrootkit
```
I got nothing but a few "Suspicious Hidden Directories", which i determined as false positives.

Then I ran:
```
sudo rkhunter -c --rwo
```
I got some common false positives, but also got some worrying results.
First of all, I had root login via ssh enabled, I opened synaptic and saw i had openssh-server installed, I doubt I installed that (I am not so sure, I might have installed something with openssh-server as a dependency.) I disabled root logins, and uninstalled openssh-server.

The other warning that caused me some concern was:
```

Warning: The file properties have changed:
         File: /usr/bin/ldd
         Current hash: e79af94393ac30aad681f0a25eab1ff84121b2aa
         Stored hash : 48348ffee4064114a55b48892e509a78cabccfb9
         Current inode: 133143    Stored inode: 135794
         Current size: 5277    Stored size: 5276
         Current file modification time: 1290005274 (17-Nov-2010 08:47:54)
         Stored file modification time : 1289337357 (09-Nov-2010 15:15:57)

```

I did some searching on google and found warning with /usr/bin/ldd being replaced by a script, but that is not the warning I am getting.

Here are the contents of the file /usr/bin/ldd
```

#! /bin/bash
# Copyright (C) 1996-2008, 2009, 2010 Free Software Foundation, Inc.
# This file is part of the GNU C Library.

# The GNU C Library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.

# The GNU C Library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.

# You should have received a copy of the GNU Lesser General Public
# License along with the GNU C Library; if not, write to the Free
# Software Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA
# 02111-1307 USA.


# This is the `ldd' command, which lists what shared libraries are
# used by given dynamically-linked executables.  It works by invoking the
# run-time dynamic linker as a command and setting the environment
# variable LD_TRACE_LOADED_OBJECTS to a non-empty value.

# We should be able to find the translation right at the beginning.
TEXTDOMAIN=libc
TEXTDOMAINDIR=/usr/share/locale

RTLDLIST="/lib/ld-linux.so.2 /lib64/ld-linux-x86-64.so.2"
warn=
bind_now=
verbose=

while test $# -gt 0; do
  case "$1" in
  --vers | --versi | --versio | --version)
    echo 'ldd (Ubuntu EGLIBC 2.12.1-0ubuntu10) 2.12.1'
    printf $"Copyright (C) %s Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
" "2010"
    printf $"Written by %s and %s.
" "Roland McGrath" "Ulrich Drepper"
    exit 0
    ;;
  --h | --he | --hel | --help)
    printf $"Usage: ldd [OPTION]... FILE...
      --help              print this help and exit
      --version           print version information and exit
  -d, --data-relocs       process data relocations
  -r, --function-relocs   process data and function relocations
  -u, --unused            print unused direct dependencies
  -v, --verbose           print all information
"
    printf $"For bug reporting instructions, please see:
%s.
" "<http://www.debian.org/Bugs/>"
    exit 0
    ;;
  -d | --d | --da | --dat | --data | --data- | --data-r | --data-re | \
  --data-rel | --data-relo | --data-reloc | --data-relocs)
    warn=yes
    shift
    ;;
  -r | --f | --fu | --fun | --func | --funct | --functi | --functio | \
  --function | --function- | --function-r | --function-re | --function-rel | \
  --function-relo | --function-reloc | --function-relocs)
    warn=yes
    bind_now=yes
    shift
    ;;
  -v | --verb | --verbo | --verbos | --verbose)
    verbose=yes
    shift
    ;;
  -u | --u | --un | --unu | --unus | --unuse | --unused)
    unused=yes
    shift
    ;;
  --v | --ve | --ver)
    echo >&2 $"ldd: option \`$1' is ambiguous"
    exit 1
    ;;
  --)		# Stop option processing.
    shift; break
    ;;
  -*)
    echo >&2 'ldd:' $"unrecognized option" "\`$1'"
    echo >&2 $"Try \`ldd --help' for more information."
    exit 1
    ;;
  *)
    break
    ;;
  esac
done

nonelf ()
{
  # Maybe extra code for non-ELF binaries.
  return 1;
}

add_env="LD_TRACE_LOADED_OBJECTS=1 LD_WARN=$warn LD_BIND_NOW=$bind_now"
add_env="$add_env LD_LIBRARY_VERSION=\$verify_out"
add_env="$add_env LD_VERBOSE=$verbose"
if test "$unused" = yes; then
  add_env="$add_env LD_DEBUG=\"$LD_DEBUG${LD_DEBUG:+,}unused\""
fi

# The following use of cat is needed to make ldd work in SELinux
# environments where the executed program might not have permissions
# to write to the console/tty.  But only bash 3.x supports the pipefail
# option, and we don't bother to handle the case for older bash versions.
if x=`set -o` && test "$x" != "${x#*pipefail}" && set -o pipefail ; then
  try_trace() {
    eval $add_env '"$@"' | cat
  }
else
  try_trace() {
    eval $add_env '"$@"'
  }
fi

case $# in
0)
  echo >&2 'ldd:' $"missing file arguments"
  echo >&2 $"Try \`ldd --help' for more information."
  exit 1
  ;;
1)
  single_file=t
  ;;
*)
  single_file=f
  ;;
esac

result=0
for file do
  # We don't list the file name when there is only one.
  test $single_file = t || echo "${file}:"
  case $file in
  */*) :
       ;;
  *) file=./$file
     ;;
  esac
  if test ! -e "$file"; then
    echo "ldd: ${file}:" $"No such file or directory" >&2
    result=1
  elif test ! -f "$file"; then
    echo "ldd: ${file}:" $"not regular file" >&2
    result=1
  elif test -r "$file"; then
    RTLD=
    ret=1
    for rtld in ${RTLDLIST}; do
      if test -x $rtld; then
	verify_out=`${rtld} --verify "$file"`
	ret=$?
	case $ret in
	[02]) RTLD=${rtld}; break;;
	esac
      fi
    done
    case $ret in
    0|2)
      try_trace "$RTLD" "$file" || result=1
      ;;
    1|126)
      # This can be a non-ELF binary or no binary at all.
      nonelf "$file" || {
	echo $"	not a dynamic executable"
	result=1
      }
      ;;
    *)
      echo 'ldd:' ${RTLD} $"exited with unknown exit code" "($ret)" >&2
      exit 1
      ;;
    esac
  else
    echo 'ldd:' $"error: you do not have read permission for" "\`$file'" >&2
    result=1
  fi
done

exit $result
# Local Variables:
#  mode:ksh
# End:

```
ldd is part of the gnu c library, I have compiled some c++ programs (very very basic, im just learning) in the Anjuta IDE, But I doubt that had anything to do with this warning.

Is there any cause for concern, or am I being worried for nothing?

EDIT: I am running GUFW with it set to enabled and deny incoming connections, allow outgoing and I have no rules.
Running Ubuntu 10.10 32bit

---

### Post by chroniccommand on 2010-12-24
> **tech newbie said:**
> Out of curiosity I decided to run rkhunter and chkrootkit.
I ran
```
sudo chkrootkit
```I got nothing but a few "Suspicious Hidden Directories", which i determined as false positives.

Then I ran:
```
sudo rkhunter -c --rwo
```I got some common false positives, but also got some worrying results.
First of all, I had root login via ssh enabled, I opened synaptic and saw i had openssh-server installed, I doubt I installed that (I am not so sure, I might have installed something with openssh-server as a dependency.) I disabled root logins, and uninstalled openssh-server.

The other warning that caused me some concern was:
```

Warning: The file properties have changed:
         File: /usr/bin/ldd
         Current hash: e79af94393ac30aad681f0a25eab1ff84121b2aa
         Stored hash : 48348ffee4064114a55b48892e509a78cabccfb9
         Current inode: 133143    Stored inode: 135794
         Current size: 5277    Stored size: 5276
         Current file modification time: 1290005274 (17-Nov-2010 08:47:54)
         Stored file modification time : 1289337357 (09-Nov-2010 15:15:57)

```I did some searching on google and found warning with /usr/bin/ldd being replaced by a script, but that is not the warning I am getting.

Here are the contents of the file /usr/bin/ldd
```

#! /bin/bash
# Copyright (C) 1996-2008, 2009, 2010 Free Software Foundation, Inc.
# This file is part of the GNU C Library.

# The GNU C Library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.

# The GNU C Library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.

# You should have received a copy of the GNU Lesser General Public
# License along with the GNU C Library; if not, write to the Free
# Software Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA
# 02111-1307 USA.


# This is the `ldd' command, which lists what shared libraries are
# used by given dynamically-linked executables.  It works by invoking the
# run-time dynamic linker as a command and setting the environment
# variable LD_TRACE_LOADED_OBJECTS to a non-empty value.

# We should be able to find the translation right at the beginning.
TEXTDOMAIN=libc
TEXTDOMAINDIR=/usr/share/locale

RTLDLIST="/lib/ld-linux.so.2 /lib64/ld-linux-x86-64.so.2"
warn=
bind_now=
verbose=

while test $# -gt 0; do
  case "$1" in
  --vers | --versi | --versio | --version)
    echo 'ldd (Ubuntu EGLIBC 2.12.1-0ubuntu10) 2.12.1'
    printf $"Copyright (C) %s Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
" "2010"
    printf $"Written by %s and %s.
" "Roland McGrath" "Ulrich Drepper"
    exit 0
    ;;
  --h | --he | --hel | --help)
    printf $"Usage: ldd [OPTION]... FILE...
      --help              print this help and exit
      --version           print version information and exit
  -d, --data-relocs       process data relocations
  -r, --function-relocs   process data and function relocations
  -u, --unused            print unused direct dependencies
  -v, --verbose           print all information
"
    printf $"For bug reporting instructions, please see:
%s.
" "<http://www.debian.org/Bugs/>"
    exit 0
    ;;
  -d | --d | --da | --dat | --data | --data- | --data-r | --data-re | \
  --data-rel | --data-relo | --data-reloc | --data-relocs)
    warn=yes
    shift
    ;;
  -r | --f | --fu | --fun | --func | --funct | --functi | --functio | \
  --function | --function- | --function-r | --function-re | --function-rel | \
  --function-relo | --function-reloc | --function-relocs)
    warn=yes
    bind_now=yes
    shift
    ;;
  -v | --verb | --verbo | --verbos | --verbose)
    verbose=yes
    shift
    ;;
  -u | --u | --un | --unu | --unus | --unuse | --unused)
    unused=yes
    shift
    ;;
  --v | --ve | --ver)
    echo >&2 $"ldd: option \`$1' is ambiguous"
    exit 1
    ;;
  --)        # Stop option processing.
    shift; break
    ;;
  -*)
    echo >&2 'ldd:' $"unrecognized option" "\`$1'"
    echo >&2 $"Try \`ldd --help' for more information."
    exit 1
    ;;
  *)
    break
    ;;
  esac
done

nonelf ()
{
  # Maybe extra code for non-ELF binaries.
  return 1;
}

add_env="LD_TRACE_LOADED_OBJECTS=1 LD_WARN=$warn LD_BIND_NOW=$bind_now"
add_env="$add_env LD_LIBRARY_VERSION=\$verify_out"
add_env="$add_env LD_VERBOSE=$verbose"
if test "$unused" = yes; then
  add_env="$add_env LD_DEBUG=\"$LD_DEBUG${LD_DEBUG:+,}unused\""
fi

# The following use of cat is needed to make ldd work in SELinux
# environments where the executed program might not have permissions
# to write to the console/tty.  But only bash 3.x supports the pipefail
# option, and we don't bother to handle the case for older bash versions.
if x=`set -o` && test "$x" != "${x#*pipefail}" && set -o pipefail ; then
  try_trace() {
    eval $add_env '"$@"' | cat
  }
else
  try_trace() {
    eval $add_env '"$@"'
  }
fi

case $# in
0)
  echo >&2 'ldd:' $"missing file arguments"
  echo >&2 $"Try \`ldd --help' for more information."
  exit 1
  ;;
1)
  single_file=t
  ;;
*)
  single_file=f
  ;;
esac

result=0
for file do
  # We don't list the file name when there is only one.
  test $single_file = t || echo "${file}:"
  case $file in
  */*) :
       ;;
  *) file=./$file
     ;;
  esac
  if test ! -e "$file"; then
    echo "ldd: ${file}:" $"No such file or directory" >&2
    result=1
  elif test ! -f "$file"; then
    echo "ldd: ${file}:" $"not regular file" >&2
    result=1
  elif test -r "$file"; then
    RTLD=
    ret=1
    for rtld in ${RTLDLIST}; do
      if test -x $rtld; then
    verify_out=`${rtld} --verify "$file"`
    ret=$?
    case $ret in
    [02]) RTLD=${rtld}; break;;
    esac
      fi
    done
    case $ret in
    0|2)
      try_trace "$RTLD" "$file" || result=1
      ;;
    1|126)
      # This can be a non-ELF binary or no binary at all.
      nonelf "$file" || {
    echo $"    not a dynamic executable"
    result=1
      }
      ;;
    *)
      echo 'ldd:' ${RTLD} $"exited with unknown exit code" "($ret)" >&2
      exit 1
      ;;
    esac
  else
    echo 'ldd:' $"error: you do not have read permission for" "\`$file'" >&2
    result=1
  fi
done

exit $result
# Local Variables:
#  mode:ksh
# End:

```ldd is part of the gnu c library, I have compiled some c++ programs (very very basic, im just learning) in the Anjuta IDE, But I doubt that had anything to do with this warning.

Is there any cause for concern, or am I being worried for nothing?
Hm. The file looks normal to me and its the same as mine and mines not infected.

---

### Post by tech newbie on 2010-12-24
Do you mind uploading a copy of your ldd file?

---

### Post by uRock on 2010-12-24
rkhunter brings back too many false positives. It will be tripped with almost every hash change, which happens often when updates are run.

---

### Post by tech newbie on 2010-12-24
Yes but that still does not explain ssh root logins being enabled,(is that default with openssh-server ?) and the fact I had openssh-server installed (I'm pretty sure it is not default.)

---

### Post by cariboo on 2010-12-24
Allowing root logins is the default setting on /etc/sshd_config. Running rkhunter and chkrootkit, are pretty useless you run a baseline scan on a fresh install, and then update each time before running them.

---

### Post by HermanAB on 2010-12-25
Howdy,

Rootkit hunting tools are all unmaintained and quite useless.

There are various reasons why Linux is not susceptible to viruses and crudware: Netfilter, tcpwrappers, no execute, program memory randomization and using ANSI C and not C++, to name a few. 

So, relax and enjoy your Linux system.

---

