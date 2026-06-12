---
title: "RKhunter Scan Help"
date: 2009-04-02
forum: Security
---

### Post by jordanp123 on 2009-04-02
I just ran RKhunter (A little paranoid I guess) and it gave me a  warning for 
/usr/sbin/unhide
/usr/sbin/unhide-linux26

"Check /Dev for suspicious file typs: Warning"

"Check for hidden files and directories: Warning"

2 Suspect files found. 


Is this something I should be worried about ?

---

### Post by bodhi.zazen on 2009-04-02
rkhunter give a fair amount of false positives. These are "Warnings"

you will need to google search the exact warning as they are all well documented.

IMO it is best to run rkhunter on a fresh install ASAP to get a feel for what is "normal".

---

### Post by jordanp123 on 2009-04-02
erforming filesystem checks
[12:27:07] Info: Starting test name 'filesystem'
[12:27:07] Info: SCAN_MODE_DEV set to 'THOROUGH'
[12:27:08]   Checking /dev for suspicious file types         [ Warning ]
[12:27:08] Warning: Suspicious file types found in /dev:
[12:27:08]          /dev/shm/pulse-shm-510297099: data
[12:27:08]   Checking for hidden files and directories       [ Warning ]
[12:27:08] Warning: Hidden file found: /etc/.resolv.conf.swp: Vim swap file, version 7.1

[12:23:45] /usr/sbin/unhide                                  [ Warning ]
[12:23:45] Warning: The file '/usr/sbin/unhide' exists on the system, but it is not present in the rkhunter.dat file.

[12:23:45] /usr/sbin/unhide-linux26                          [ Warning ]
[12:23:45] Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunter.dat file.


Thanks, For the quick Response ! I went through the log file and copied the warnings, I figured I would post them encase anyone else already knew what they were. 
Just now starting to get the hang of ubuntu and I guess After I've got everything customized just how I want it I really dont want to lose what I have.

---

### Post by kryptikos on 2009-04-02
There's nothing there to be concerned by. 'unhide' and 'unhide-linux26' are tools to show tcp ports that are listening but not listed when you run netstat or lsof -i TCP. It is a Debian package. 

The resolve.conf.swp is a left over file that VIM will create if it is closed improperly. Edited your resolve.conf manually recently? 

If you like to compare results install chkrootkit as well and run after rkhunter to see if there are any differences. Should be in the repositories (although I haven't checked in a while), if not you can grab it from here if you end up deciding you want it:

[http://www.chkrootkit.org/]("http://www.chkrootkit.org/")

---

### Post by HermanAB on 2009-04-02
There are always people asking about root kits on these forums.  I have been using Unix systems since about 1985 on thousands of machines and have *never* encountered a root kit.  So relax and enjoy your nice and secure system.

---

### Post by jordanp123 on 2009-04-02
Yeah, just got done editing yesterday actually. Thanks for the help ! Was worried at first that I had somehow had an infection. Thanks Again for the help, all three of you !

---

