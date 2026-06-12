---
title: "U1 + Tomboy + PC + Netbook = hours and hours of fail"
date: 2012-04-04
forum: Ubuntu One (CLOSED)
---

### Post by TR4G- on 2012-04-04
Hey guys, I have been trying to get organized with tomboy notes and ubuntu one and I am having difficulties.

First off, I have legit been messing with this since 2 am last night, so I have seen practically every tutorial on the web. All I want to do is to be able to take notes VIA tomboy on my netbook in class and also on my PC at home and be able to consolidate these files easily.

I thought U1 could do this. I have gotten each computer synced to U1. First question: do I name each computer something different? I have tried both to no avail. Here is my current setup: my pc is called tomboy.desktop and my netbook is synced under tomboy.netbook.....

now how the hell does this function even work? 
when I click synchronize what is supposed to happen? I thought that my files would be updated on U1. But then how do i get these updated files back onto my PC? Is there a separate button for uploaded notes and then getting those updated notes back onto your computer? I can get it to work with just one computre, but whats the point in that? To back it up lol? Since they took out the notes section from U1, how the hell can I sync notes from both comps and have access to them? 

All that happens for me is that they each sync to their own individual place and dont talk to each other. So my netbook files get stored on the internet on u1 but i can only get them back onto my netbook, not onto my computer....... 

please cansomeone help me out? with speicific info? not just linking me to some tutorial> because i have seen them all

is this a pointless quest? I heard tomboy isnt the default note app in 12.04....should i just go ahead and not do any of this and try some other way that will continue to exist in the future?


EDIT

all it needed was 3 more hours of my time lol facepalm. ANy who, i used this work around:

[https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/848250](https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/848250)

---

### Post by duanedesign on 2012-04-06
Glad to hear you got it sorted. Sorry to hear it took so long. I thought I would post a couple of processes for helping fix and debug Tomboy.

[B]Option 1
[/B]Please try the following script that should provide you with the information regarding what note is causing the synchronization to fail.

Press Alt-F2, type "gnome-terminal", press "Enter" and run:

```
cd /tmp
wget http://people.canonical.com/~roman.yepishev/us/tomboy-sync-validator.py
python tomboy-sync-validator.py
```

It should print something like this:

[I]API ref is at [https://one.ubuntu.com/notes/api/1.0/user/](https://one.ubuntu.com/notes/api/1.0/user/), querying...
Notes are at [https://one.ubuntu.com/notes/api/1.0/op/](https://one.ubuntu.com/notes/api/1.0/op/), querying...
Current sync GUID: 0
Latest sync revision: 2
Found 5 notes
[1/5] "Start Here": OK
[2/5] "Ubuntu One": OK
[3/5] "Hello again!": OK
[4/5] "Using Links in Tomboy": OK
[5/5] "New Note 1": OK[/I]

However if there is an error it will print something like:

[I][1/5] "Start Here": ERROR
23d57ffb-a492-4ba1-adf4-72f0eb23b254: last-change-date-is-broken
(000)

[https://one.ubuntu.com/notes/view/23d57ffb-a492-4ba1-adf4-72f0eb23b254](https://one.ubuntu.com/notes/view/23d57ffb-a492-4ba1-adf4-72f0eb23b254)[/I]

If the script is showing you that there are errors in the notes, please run the script again with --fix option:

```
python tomboy-sync-validator.py --fix

```
After the script finishes running, please try syncing the notes again.

[B]Option 2
[/B]Their is one other way to get debug info. If the previous process fails you can try and get additional info by:

1. Quit Tomboy
2. Open a Terminal, and run:

```
tomboy --debug > ~/tomboy_debug.log

```
Try to reproduce the bug(Sync your notes) then look in ~/tomboy_debug.log for the output.

---

