---
title: "[SOLVED] rkhunter issues warnings"
date: 2008-05-26
forum: Security
---

### Post by bryncoles on 2008-05-26
hallo! i just ran rkhunter, read through (though not in detail) [http://wiki.linuxquestions.org/wiki/Rootkit_Hunter](http://wiki.linuxquestions.org/wiki/Rootkit_Hunter). now, rkhunter gives me the following warnings:

file prerequisite checks:

/bin/bash					warning
/bin/dmesg					warning
/bin/more					warning
/bin/mount					warning
/usr/bin/logger					warning
/usr/bin/slocate				warning
/usr/bin/sudo					warning
/usr/bin/whereis				warning

performing file system checks:

checking /dev for suspicious file types		warning
checking for hidden files or directories	warning

but no rootkits found, so thats nice. so what id like to know is, are these false positives, or genuine cause for concern? and either way, what would the appropriate action be to either prevent false positives showing up the the future, or address security concerns. 

im running hardy heron, dual booting with xp (though not often ha ha), and using a packard bell easy not r4360 (I think). 

any advise appreciated! thank you one and all.

---

### Post by Nepherte on 2008-05-26
Take a look at /var/log/rkhunter.log first.

---

### Post by bryncoles on 2008-05-26
hi nepherte! thanks for replying. shall i post all of var/log/rkhunter.log? its a little long...

for now, heres the edited highlights... just the warnings.

[11:03:35] Checking system commands...
[11:03:35] Info: Starting test name 'system_commands'
[11:03:35]

...

[11:03:39] /bin/bash                                         [ Warning ]
[11:03:39] Warning: The file properties have changed:
[11:03:39]          File: /bin/bash
[11:03:39]          Current hash: 8c74bdbb0d94f4bb162e69a87fd157e5d4c16868
[11:03:39]          Stored hash : fc22cc7f937df7042049f30744ae29c13431e4f8
[11:03:39]          Current inode: 83594    Stored inode: 81789
[11:03:39]          Current size: 702160    Stored size: 701808
[11:03:39]          Current file modification time: 1210617204
[11:03:39]          Stored file modification time : 1208230594

...

[11:03:40] /bin/dmesg                                        [ Warning ]
[11:03:41] Warning: The file properties have changed:
[11:03:41]          File: /bin/dmesg
[11:03:41]          Current inode: 83411    Stored inode: 89116
[11:03:41]          Current file modification time: 1209470261
[11:03:41]          Stored file modification time : 1208230606

...

[11:03:43] /bin/more                                         [ Warning ]
[11:03:43] Warning: The file properties have changed:
[11:03:43]          File: /bin/more
[11:03:43]          Current inode: 83421    Stored inode: 89119
[11:03:43]          Current file modification time: 1209470261
[11:03:43]          Stored file modification time : 1208230606
[11:03:43] /bin/mount                                        [ Warning ]
[11:03:43] Warning: The file properties have changed:
[11:03:43]          File: /bin/mount
[11:03:43]          Current inode: 83417    Stored inode: 81779
[11:03:43]          Current file modification time: 1209470261
[11:03:43]          Stored file modification time : 1208230606

...

[11:03:49] /usr/bin/logger                                   [ Warning ]
[11:03:49] Warning: The file properties have changed:
[11:03:49]          File: /usr/bin/logger
[11:03:49]          Current inode: 2355054    Stored inode: 2354804
[11:03:49]          Current file modification time: 1209470261
[11:03:49]          Stored file modification time : 1208230606

...

[11:03:51] /usr/bin/slocate                                  [ Warning ]
[11:03:51] Warning: The file '/usr/bin/slocate' does not exist on the system, but it is present in the rkhunter.dat file.

...

[11:03:52] /usr/bin/sudo                                     [ Warning ]
[11:03:52] Warning: The file properties have changed:
[11:03:52]          File: /usr/bin/sudo
[11:03:52]          Current hash: 0ed9a0d689ad891475eb13d02be7e34b4c104f6c
[11:03:52]          Stored hash : 094fe12401c97bdfeef1c11938f331fb143fe056
[11:03:52]          Current inode: 2354859    Stored inode: 2356213
[11:03:52]          Current size: 107872    Stored size: 107776
[11:03:52]          Current file modification time: 1210812110
[11:03:52]          Stored file modification time : 1203938573

...

[11:03:55] /usr/bin/whereis                                  [ Warning ]
[11:03:55] Warning: The file properties have changed:
[11:03:55]          File: /usr/bin/whereis
[11:03:55]          Current inode: 2355025    Stored inode: 2356019
[11:03:55]          Current file modification time: 1209470261
[11:03:55]          Stored file modification time : 1208230606

...

[11:06:00] Performing filesystem checks
[11:06:00] Info: Starting test name 'filesystem'
[11:06:00] Info: SCAN_MODE_DEV set to 'THOROUGH'
[11:06:17]   Checking /dev for suspicious file types         [ Warning ]
[11:06:17] Warning: Suspicious file types found in /dev:
[11:06:17]          /dev/shm/pulse-shm-1293727385: data
[11:06:18]   Checking for hidden files and directories       [ Warning ]
[11:06:18] Warning: Hidden directory found: /etc/.java
[11:06:18] Warning: Hidden directory found: /dev/.static
[11:06:18] Warning: Hidden directory found: /dev/.udev
[11:06:18] Warning: Hidden directory found: /dev/.initramfs
[11:10:29]

...

and the last thing it says is quite encouraging:

[11:10:32] File properties checks...
[11:10:32] Files checked: 122
[11:10:32] Suspect files: 8
[11:10:32]
[11:10:32] Rootkit checks...
[11:10:32] Rootkits checked : 109
[11:10:32] Possible rootkits: 0
[11:10:32]
[11:10:32] Applications checks...
[11:10:32] Applications checked: 3
[11:10:32] Suspect applications: 0
[11:10:32]
[11:10:32] The system checks took: 6 minutes and 57 seconds
[11:10:32]
[11:10:32] Info: End date is Mon May 26 11:10:32 BST 2008

no rootkits found, just suspicious files. 

also: i noticed in other peoples posts that they are able to put output like the above into 'code box's'. any idea how i would do that, or shall i just not worry about that bit?

---

### Post by Nepherte on 2008-05-26
The hidden files in your /dev directory are certainly not to be worried about. I have the same log for it on a clean hardy install. I think you can safely ignore those.

The system command warnings say that the system command files were altered (hash mismatch). Probably an installation of some sort of program altered it. Not sure if it's that much of a security problem. To be sure you should look at the file itself.

P.S You can put output or terminal commands in a code box by placing [code'] in front of the text and ending the text with ['/code'] but without the 's. There's also a button that looks like # in the graphical editor that does the same thing.

---

### Post by bryncoles on 2008-05-27
thats good to know! ill not worry too much then. one last thing though, how exactly would i tell if there was anything wrong with a system file? for example, i can navigate to /bin/bash, for example, but then ive no idea what to do! any pointers appreciated.

---

### Post by Nepherte on 2008-05-27
I'm afraid that it is not so trivial. You could look at the content of the file and see if there is anything wrong with it, but you should have a decent amount of programming knowledge and knowing the original not changed repo version of the file would come in handy too. I couldn't do it myself to be honest.

---

### Post by bryncoles on 2008-05-27
bum! that rules out my being able to do it too! never mind though, i might just hope that nothings wrong! after all, no problems were identified, only suspicions. 

thankyou for your help though!

---

