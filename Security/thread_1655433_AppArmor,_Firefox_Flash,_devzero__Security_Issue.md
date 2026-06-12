---
title: "AppArmor, Firefox Flash, \dev\zero:  Security Issue?"
date: 2010-12-29
forum: Security
---

### Post by kycul on 2010-12-29
I've just put the default AppArmor profile for firefox into enforcing mode (  sudo aa-enforce /etc/apparmor.d/usr.bin.firefox ), and when I tried to view a you tube video ( using the flash plug-in ), and it played normally, until I hit the full-screen button.  This caused the plug-in to crash.  

The following message was printed to my kern.log:

Dec 29 10:09:43 bill-desktop kernel: [ 1223.788611] type=1503 audit(1293635383.181:1635):  operation="file_mmap" pid=1600 parent=1536 profile="/usr/lib/firefox-3.6.13/firefox-*bin" requested_mask="::m" denied_mask="::m" fsuid=1000 ouid=0 name="/dev/zero"

Apparently, dev/zero is a way to copy nulls;  "file_mmap" refers to a memory mapping function;  so I guess maybe it's trying to create an area in memory and initialize it to nulls.

There's no specific reference to '/dev/zero' in the profile, so I don't know...

Has anyone seen this before?  I wonder whether this is a security issue or not.  

And, if it's not a security issue, what could be put into the profile to allow the operation?

Thanks in advance.  Happy New Year!

---

### Post by lovinglinux on 2010-12-29
I don't use AppArmor, but I suspect could be an issue with plugin-container privileges. Perhaps you could create a profile for the plugin-container, but I'm not sure if AppArmor threats it as a child process of Firefox or as a standalone program. Just a thought.

---

### Post by jbrown96 on 2010-12-30
No this is poor programming on the part of Mozilla or Adobe. I'll break down this error message because I think that it will help people understand Apparmor.

Apparmor is designed to enforce properties on programs, or more correctly on filenames. When you load an Apparmor profile for app X, what you are saying is that the Apparmor service (daemon) should monitor, and potentially restrict, the actions of X. Let's step back for a minute. It's important to recognize that Apparmor doesn't treat X like "Firefox"; instead, X is far more specific and is a location on the file system (i.e. /usr/bin/firefox). 
An Apparmor profile deals with a source file(s) and the access that it/they are allowed with other files. 
Firefox, ahh /usr/bin/firefox, is trying to read from the (special) file /dev/zero, which is an everlasting supply of the character "0". (Try running "cat /dev/zero". Use Ctrl+c to cancel after you get the picture). However, in the profile for /usr/bin/firefox, there is no rule allowing Firefox to read from /dev/zero.

Now that you have some understanding of the problem. Let's run through the error message for some Apparmor and general Linux information.

> Dec 29 10:09:43 bill-desktop kernel: [ 1223.788611] This is just the header for a syslog message. We get the date, the hostname of you computer: "bill-desktop," the source of the message: the kernel, and some sequence number from the kernel.
This is just basic information, so you or anyone/anything reading the logs can tell the time, source, and location of the message.

> type=1503 audit(1293635383.181:1635)
We get the kernel's type of error: 1503. This code is specific for Apparmor. It could've said "type=Apparmor," same thing. We have also been given the Apparmor audit number for this message. Apparmor probably keeps these errors stored elsewhere in more detail. This is like a Dewey decimal code on a library book; you get a summary of the book and the number, then find the full book.

> operation="file_mmap"
Now we're in the meat of the message. When an application needs memory (RAM), it has to request it from the kernel. There are quite a few ways to do this, but the two primary methods are: malloc and mmap. (These aren't really equal comparisons, but they will work). Malloc is more a method that programs use to get additional memory. Let's say I have a program that will simply print your name. When you enter your name, you can think of that memory as being request from the kernel in a "malloc" operation. On the other hand, let's say my program will play an MP3 file stored on the hard drive. I need to read that file in and play it through the speakers. Getting the memory to store that file as it's being read is an "mmap" operation. 

The offending operation was an attempt by a process to "mmap," or read, a file to which it doesn't have access. 



> pid=1600 parent=1536
Now we get to figure out exactly who did. A PID (Process ID) is a unique number given to every application currently running on your system. The first process is called "init" and is #1; it is the "parent" of all others, which is the second part. Every program was started by another one. We could take this all the way down to the power switch-->BIOS-->GRUB, but that's not germane. Init is the first process and is #1. There's all kinds of things that init starts. All the various services and such on your computer; there's hundreds of programs that execute when the computer boots. Each one of the has a "parent": the program that initiated it. When I log into my system, I have a Bash shell running, which has it's own PID (let's say #1268). If I run a program (let's say emacs), it gets an unused PID (let's say #1344). This instance of emacs also knows its parent. It's a really great way to track how processes run. If I know the PID and PPID (Parent Process ID) of a program that's causing a problem, then I can go to the grandparent, greatgrandparent, etc. until I find the source. 

These two pieces of information help us determine exactly which program performed the illegal action.

> profile="/usr/lib/firefox-3.6.13/firefox-*bin"
This tells us which profile prohibited the operation. The firefox profile.

> requested_mask="::m" denied_mask="::m"
This is technical information about mmap from earlier. The mask "m" means the application tried to invoke the mmap(2) system call (type "man 2 mmap" to read about it). Process 1600 requested "m" access and was denied "m" access. The colons are there to separate other permissions that were not needed. 


> fsuid=1000 ouid=0
This tells information about the user running firefox (fsuid). The first regular user id (UID) on an Ubuntu system is 1000. Knowing the hostname and that user 1000 ran this, I'd say your name is Bill. the OUID is the owner of the firefox file. All normally installed programs on Linux are owned by root (UID 0) and users are given read-only access to provide security. 
User 1000 was running a program owned by root.


> name="/dev/zero
Finally we see the file that Firefox was trying to read. It's wants a bunch of zeros.


Why would Firefox want to mmap, or read, an endless source of zeros? A web browser is constantly downloading data from the internet while you are using it. All of that requires memory. Firefox needs more memory for some operation. It's typical to request large chunks of memory at once because it's a relatively slow operation. Firefox is requesting that part of /dev/zero (that's all zeros) be read into Firefox's memory. Obviously, Firefox has no need for a whole bunch of zeros, but it works out perfectly for network situations. While this chunk of memory could be used for all kinds of things (text, icons, downloaded files, graphics, etc.), let's saw it's an MP3 that you are downloading. Firefox needs some amount of memory to store that file while it's being downloading from the internet and before it's written to disk. This is typically far, far less than the size of the file (It's not like you need to dedicate 700MB of RAM to download a Linux iso); however, there is some memory needed. 



Long story short: you need to add something (I don't know Apparmor profiles) to your Firefox Apparmor profile to allow it access to /dev/zero. There isn't a security risk associated with it. What could an attacker do reading an infinite supply of zeros? And there's no way to write to it (you can but it doesn't do anything).

---

### Post by donato roque on 2010-12-31
Hi kycul

Short answer to your question is Yes. Apparmor has something to do with the plugin crashing.  But I would strongly recommend you read jbrown96's post/answer because he certainly explains it in depth.

The situation is your apparmor profile for firefox restricts an operation from being performed.  You may allow the operation by modifying the apparmor profile for firefox.  Location of apparmor profile is /etc/apparmor.d

or you can open a terminal and 
~$ sudo logprof  it.

---

### Post by kycul on 2010-12-31
Thanks jbrown96, donato roque, lovinglinux

jbrown96's post answered a number of my questions. Thanks for your time.

I was able to update the apparmor firefox profile, by editing the profle directly and putting this line in:

```
/dev/zero m,
```I had tried using aa-logprof, but it ran, and did not update the profile despite there being a 'denied_mask' message in the syslog.

Thanks again.  :p

---

### Post by oldmankit on 2011-04-18
> **jbrown96 said:**
> No this is poor programming on the part of Mozilla or Adobe. I'll break down this error message because I think that it will help people understand Apparmor.

Apparmor is designed to enforce properties on programs, or more correctly on filenames. When you load an Apparmor profile for app X, what you are saying is that the Apparmor service (daemon) should monitor, and potentially restrict, the actions of X. Let's step back for a minute. It's important to recognize that Apparmor doesn't treat X like "Firefox"; instead, X is far more specific and is a location on the file system (i.e. /usr/bin/firefox). 
An Apparmor profile deals with a source file(s) and the access that it/they are allowed with other files. 
Firefox, ahh /usr/bin/firefox, is trying to read from the (special) file /dev/zero, which is an everlasting supply of the character "0". (Try running "cat /dev/zero". Use Ctrl+c to cancel after you get the picture). However, in the profile for /usr/bin/firefox, there is no rule allowing Firefox to read from /dev/zero.

Now that you have some understanding of the problem. Let's run through the error message for some Apparmor and general Linux information.

 This is just the header for a syslog message. We get the date, the hostname of you computer: "bill-desktop," the source of the message: the kernel, and some sequence number from the kernel.
This is just basic information, so you or anyone/anything reading the logs can tell the time, source, and location of the message.


We get the kernel's type of error: 1503. This code is specific for Apparmor. It could've said "type=Apparmor," same thing. We have also been given the Apparmor audit number for this message. Apparmor probably keeps these errors stored elsewhere in more detail. This is like a Dewey decimal code on a library book; you get a summary of the book and the number, then find the full book.


Now we're in the meat of the message. When an application needs memory (RAM), it has to request it from the kernel. There are quite a few ways to do this, but the two primary methods are: malloc and mmap. (These aren't really equal comparisons, but they will work). Malloc is more a method that programs use to get additional memory. Let's say I have a program that will simply print your name. When you enter your name, you can think of that memory as being request from the kernel in a "malloc" operation. On the other hand, let's say my program will play an MP3 file stored on the hard drive. I need to read that file in and play it through the speakers. Getting the memory to store that file as it's being read is an "mmap" operation. 

The offending operation was an attempt by a process to "mmap," or read, a file to which it doesn't have access. 




Now we get to figure out exactly who did. A PID (Process ID) is a unique number given to every application currently running on your system. The first process is called "init" and is #1; it is the "parent" of all others, which is the second part. Every program was started by another one. We could take this all the way down to the power switch-->BIOS-->GRUB, but that's not germane. Init is the first process and is #1. There's all kinds of things that init starts. All the various services and such on your computer; there's hundreds of programs that execute when the computer boots. Each one of the has a "parent": the program that initiated it. When I log into my system, I have a Bash shell running, which has it's own PID (let's say #1268). If I run a program (let's say emacs), it gets an unused PID (let's say #1344). This instance of emacs also knows its parent. It's a really great way to track how processes run. If I know the PID and PPID (Parent Process ID) of a program that's causing a problem, then I can go to the grandparent, greatgrandparent, etc. until I find the source. 

These two pieces of information help us determine exactly which program performed the illegal action.


This tells us which profile prohibited the operation. The firefox profile.


This is technical information about mmap from earlier. The mask "m" means the application tried to invoke the mmap(2) system call (type "man 2 mmap" to read about it). Process 1600 requested "m" access and was denied "m" access. The colons are there to separate other permissions that were not needed. 



This tells information about the user running firefox (fsuid). The first regular user id (UID) on an Ubuntu system is 1000. Knowing the hostname and that user 1000 ran this, I'd say your name is Bill. the OUID is the owner of the firefox file. All normally installed programs on Linux are owned by root (UID 0) and users are given read-only access to provide security. 
User 1000 was running a program owned by root.



Finally we see the file that Firefox was trying to read. It's wants a bunch of zeros.


Why would Firefox want to mmap, or read, an endless source of zeros? A web browser is constantly downloading data from the internet while you are using it. All of that requires memory. Firefox needs more memory for some operation. It's typical to request large chunks of memory at once because it's a relatively slow operation. Firefox is requesting that part of /dev/zero (that's all zeros) be read into Firefox's memory. Obviously, Firefox has no need for a whole bunch of zeros, but it works out perfectly for network situations. While this chunk of memory could be used for all kinds of things (text, icons, downloaded files, graphics, etc.), let's saw it's an MP3 that you are downloading. Firefox needs some amount of memory to store that file while it's being downloading from the internet and before it's written to disk. This is typically far, far less than the size of the file (It's not like you need to dedicate 700MB of RAM to download a Linux iso); however, there is some memory needed. 



Long story short: you need to add something (I don't know Apparmor profiles) to your Firefox Apparmor profile to allow it access to /dev/zero. There isn't a security risk associated with it. What could an attacker do reading an infinite supply of zeros? And there's no way to write to it (you can but it doesn't do anything).
That was an awesome post by jbrown.  Thanks for helping us understand apparmor.

---

