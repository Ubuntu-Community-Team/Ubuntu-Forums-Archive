---
title: "How to find files containing specific text in Ubuntu Linux or similar distro?"
date: 2014-08-19
forum: Tutorials
---

### Post by rousseau09 on 2014-08-19
Very often new users would dwell on Google trying to find the correct command to find files containing specific text. This is particularly important when you’re tying to follow a badly written guide of forum post that says something like replace 0 with 1 in this line which will fix PulseAudio configured for per-user sessions … (warning)

```
PULSEAUDIO_SYSTEM_START=0
```

Now for an experienced user, no problem, you know exactly where to find a configuration file for PulseAudio. For a new Linux user, yeah tell me about it. I’ve been there when I started with Slackware back late nineties.

This guide shows a bunch of commands that you can use  to find files containing specific text in Linux, namely Ubuntu, Debian, Mint, CentOS, Fedora and any Linux distro.

```
This guide will work for any Linux distributions, namely -

    Linux Mint
    Ubuntu
    Debian GNU/Linux
    Mageia / Mandriva
    Fedora
    openSUSE / SUSE Linux Enterprise
    Arch Linux
    CentOS / Red Hat Enterprise Linux
    PCLinuxOS
    Slackware Linux
    Puppy Linux
    Kali Linux (my distro ;) )
```

**Link to complete post: **

[How to find files containing specific text in Ubuntu Linux or similar distro?]("http://www.blackmoreops.com/2014/08/20/find-files-containing-specific-text/")

```
Table of Contents

    Find files containing specific text using grep command
        grep command syntax
    Find files containing specific text using grep command examples
        Find files containing specific text when you know the location
        Find files containing specific text when you don’t know the location
        Find files containing specific text with color output
        Find files containing specific text with filenames only
        Find files containing specific text and hide errors
        Find files containing specific text and ignore case
    Summary
```

Find files containing specific text using grep command

grep is a command-line utility for searching plain-text data sets for lines matching a regular expression. Grep was originally developed for the Unix operating system, but is available today for all Unix-like systems. Its name comes from the ed command g/re/p (globally search a regular expression and print), which has the same effect: doing a global search with the regular expression and printing all matching lines.

To find files containing specific text, you are possibly better off using the grep command. The grep command can find and search a specific text from all files quickly.
grep command syntax

Syntax for grep command is simple:

```
grep "text string to search” directory-path
```

OR

```
grep [option] "text string to search” directory-path
```

OR

```
grep -r "text string to search” directory-path
```

OR

```
grep -r -H "text string to search” directory-path
```

OR

```
egrep -R "word-1|word-2” directory-path
```

OR

```
egrep -w -R "word-1|word-2” directory-path
```

 
Find files containing specific text using grep command examples

In this example, we will search for 'PULSEAUDIO_SYSTEM_START‘ in all configuration files located in /etc directory.

Now there’s a small problem, depending on your Linux, BSD or Unix distro, Find command can be slightly different (in terms of Syntaxes). So I will outline all possible combinations, you can just try one at a time to determine which one best suites you.
Find files containing specific text when you know the location

If you know the exact location and directory you’re after, then use

```
root@kali:~# grep "PULSEAUDIO_SYSTEM_START" /etc/default/pulseaudio 
PULSEAUDIO_SYSTEM_START=1
root@kali:~#
```



If you know the exact directory with the files containing that specific text, then use
```

root@kali:~# grep "PULSEAUDIO_SYSTEM_START" /etc/default/*
grep: /etc/default/kdm.d: Is a directory
/etc/default/pulseaudio:PULSEAUDIO_SYSTEM_START=1
root@kali:~#
```

 
Find files containing specific text when you don’t know the location

If you don’t know the exact location of the file that contains the specific text you’re looking for, then you need to search all subdirectories recursively.

You can search for a text string all files under each directory, recursively with -r option:

```
root@kali:~# grep -r "PULSEAUDIO_SYSTEM_START" /etc/default/*
/etc/default/pulseaudio:PULSEAUDIO_SYSTEM_START=1
root@kali:~#
```

OR

```
root@kali:~# grep -R "PULSEAUDIO_SYSTEM_START" /etc/default/*
/etc/default/pulseaudio:PULSEAUDIO_SYSTEM_START=1
root@kali:~#

```


 
Find files containing specific text with color output

Now what if you are searching through a massive file and there might be many outputs similar to what you’re looking for.. you might want to use --col flag to colorcode your output which searching files containing specific strings.

 
```

root@kali:~# grep --col 'usb 1-1.4' /var/log/messages
Aug 18 09:14:25 kali kernel: [1191164.780496] usb 1-1.4: new low-speed USB device number 21 using ehci-pci
root@kali:~#
```



 
Find files containing specific text with filenames only

Now I want to display all files with colorer output with containing specific text and instead of showing the whole content of the files, I just want to display the filenames. So I use something like this:
```

root@kali:~# grep --col -r 'Linux version 3.14-kali1' /var/log/* | cut -d: -f1
/var/log/dmesg
/var/log/dmesg.0
/var/log/installer/syslog
root@kali:~#
```



 
Find files containing specific text and hide errors

When you’re using grep, depending on the commands used and permission you have on the system, you might see any of the following errors.

```
    Input/output error
    recursive directory loop
    No such file or directory
    No such device or address
    Permission denied
```

If you want to hide all errors or warning message spamming your output window(specifically useful when you’re trying to use grep on a script) generated by the grep command, append 2>/dev/null to grep command. This will send and hide unwanted output to /dev/null device:

```
root@kali:~# grep -R "PULSEAUDIO_SYSTEM_START" /etc/* 2>/dev/null 
/etc/default/pulseaudio:PULSEAUDIO_SYSTEM_START=1
/etc/init.d/pulseaudio:PULSEAUDIO_SYSTEM_START=0
/etc/init.d/pulseaudio:if [ "$PULSEAUDIO_SYSTEM_START" != "1" ]; then
/etc/rc0.d/K01pulseaudio:PULSEAUDIO_SYSTEM_START=0
/etc/rc0.d/K01pulseaudio:if [ "$PULSEAUDIO_SYSTEM_START" != "1" ]; then
/etc/rc1.d/K01pulseaudio:PULSEAUDIO_SYSTEM_START=0
/etc/rc1.d/K01pulseaudio:if [ "$PULSEAUDIO_SYSTEM_START" != "1" ]; then
/etc/rc2.d/S20pulseaudio:PULSEAUDIO_SYSTEM_START=0
/etc/rc2.d/S20pulseaudio:if [ "$PULSEAUDIO_SYSTEM_START" != "1" ]; then
/etc/rc3.d/S20pulseaudio:PULSEAUDIO_SYSTEM_START=0
/etc/rc3.d/S20pulseaudio:if [ "$PULSEAUDIO_SYSTEM_START" != "1" ]; then
/etc/rc4.d/S20pulseaudio:PULSEAUDIO_SYSTEM_START=0
/etc/rc4.d/S20pulseaudio:if [ "$PULSEAUDIO_SYSTEM_START" != "1" ]; then
/etc/rc5.d/S20pulseaudio:PULSEAUDIO_SYSTEM_START=0
/etc/rc5.d/S20pulseaudio:if [ "$PULSEAUDIO_SYSTEM_START" != "1" ]; then
/etc/rc6.d/K01pulseaudio:PULSEAUDIO_SYSTEM_START=0
/etc/rc6.d/K01pulseaudio:if [ "$PULSEAUDIO_SYSTEM_START" != "1" ]; then
root@kali:~#
```

 
Find files containing specific text and ignore case

What if you’re not sure about the case of the text you’re after? You can use -i to ignore case (note that this takes significantly longer to find files containing specific text).

Below example shows the difference between -i flag. First command didn’t find the text, second command did as we used -i flag to ignore case.

```
root@kali:~# grep -r "pulseaudio_system_start" /etc/default/*
root@kali:~# 
root@kali:~# grep -i  -r "pulseaudio_system_start" /etc/default/*
/etc/default/pulseaudio:PULSEAUDIO_SYSTEM_START=1
root@kali:~#
```


 
Summary

In summary, I always prefer using grep command with -r  and --col flag in Debian Linux as -r complains less about permissions, files, directory etc. and of course some color helps on the eyes when you’re browsing through many lines.

```
root@kali:~# grep --col -r "PULSEAUDIO_SYSTEM_START" /etc/*
/etc/default/pulseaudio:PULSEAUDIO_SYSTEM_START=1
/etc/init.d/pulseaudio:PULSEAUDIO_SYSTEM_START=0
/etc/init.d/pulseaudio:if [ "$PULSEAUDIO_SYSTEM_START" != "1" ]; then
root@kali:~#
```


Other Linux distroes like Ubuntu, Mint, CentOS, Fedora, Redhat, Arch is no different to grep command. The commands shown above will help everyone and anyone trying to find files containing specific text in Linux.

Thanks for reading. If this helped you, please share.

**Link to complete post: **

[How to find files containing specific text in Ubuntu Linux or similar distro?]("http://www.blackmoreops.com/2014/08/20/find-files-containing-specific-text/")

---

