---
title: "vmware server strange mouse screen resolution problem"
date: 2009-10-23
forum: Virtualisation
---

### Post by sdowney717 on 2009-10-23
the mouse does not go to the edge of the virtual window. clicking anywhere outside of a smaller rectangle insode the virtual maching does not work, the mouse cursor does not follow where it should go, the numlock light flashes on the keyboard as does the message 'to release input press cntrl g'

if i increase the virtual machine screen resolution the problem gets worse

i also discovered my keyboard in ubuntu host does not respond to shift or caplock or numlock anymore/

I rebooted and the keyboard is working, but the vmware machine xp still is doing the weird mouse
The mouse can go to the extreme left and extreme top, but cant go down to the bottom or to the extreme right.

---

### Post by sdowney717 on 2009-10-23
the only screen resolution which work is 640 by 480. anything bigger and the mouse stops working and the numlock key flashes when you move the mouse

found this, but trying the 'solution' did not solve the problem
[http://lnxwalt.wordpress.com/2006/12/26/vmware-player-maximum-screen-resolution/](http://lnxwalt.wordpress.com/2006/12/26/vmware-player-maximum-screen-resolution/)

i tried with and without the quotes

> UPDATE, 2007-10-21: There is a problem some people have with version 2 of VMWare Player, where the mouse is unable to reach the edges of the screen.  JRI Panama solved it (in part with information from this article) this way:

    And it did not solve it. However, I decided to run the guest machine at 1024 x 768, so I change these lines accordinly and resize the screen resolution on the guest machine and the problem went away. The mouse can be moved freely when switching from the host to the guest.

    svga.maxWidth = “1024&#8243;
    svga.maxHeight = “768&#8243;

Also, if you copy and paste, remember that the quote marks you see are probably "curly", while the software expects regular straight quote marks or sometimes none at all.  If you hand-replace the quotes or even remove them, it may work acceptably.

---

### Post by sdowney717 on 2009-10-24
why does it only happen to me.
I get these problems that no one seems to have.
this problem is bad enough to make it unusable except at 640 by 480.
640 by 480 is the max screen size you can go and get normal behavior.

---

### Post by sdowney717 on 2009-10-26
nasty problem but easy to work around
this fixes the problem for me, mouse is now working

create this file using the bin/bash text.
give it a name like VMlaunch.sh
make it executable
run it and it loads the VMware machine

> #!/bin/bash
################################################## ##############################
# Call VMWare Server's Remote Console in a clean GTK setup.
################################################## ##############################

# Clean GTK setup for VMWare
export VMWARE_USE_SHIPPED_GTK=yes

# Find console executable in Firefox plugins.
vmrc="$(find "$HOME/.mozilla/firefox" -name vmware-vmrc -type f -perm -111 | tail -1)"
[ -x "$vmrc" ] || exit 1

set -x
cd "$(dirname "$vmrc")" && "$vmrc" -h 127.0.0.1:8333



[http://shellack.de/info/content/vmware-server-20-console-failure](http://shellack.de/info/content/vmware-server-20-console-failure)

It should also be possible to run Firefox by VMWARE_USE_SHIPPED_GTK=yes firefox in your Linux command line to fix the GTK issue.
sdowney717 wrote 2 seconds ago: #6

---

### Post by whoop on 2009-10-26
I have the same annoying problem...

---

### Post by whoop on 2009-10-26
Although the solution works. Isn't this a dirty fix? Hope this will be fixed in a later release...

---

### Post by sdowney717 on 2009-10-26
i posted a bug report
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/460531](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/460531)

however, the gtk folks say it is a vmware problem?
it is a major bug, anyone coming along and trying this out would experience the same unusable condition. IT would be a big turnoff.

if you wish, go ahead and put in your comments on the bug report

follow this thread for more info
[http://www.rootloot.de/blog/vmware_in_ubuntu_karmic](http://www.rootloot.de/blog/vmware_in_ubuntu_karmic)
[http://ubuntuforums.org/showthread.php?t=1289847](http://ubuntuforums.org/showthread.php?t=1289847)

---

### Post by danteuk on 2009-11-03
These work-arounds are not working.

I had to modify the script to work for some shared library issues.

```

#!/bin/bash
################################################## ##############################
# Call VMWare Server's Remote Console in a clean GTK setup.
################################################## ##############################

# Clean GTK setup for VMWare

export VMWARE_USE_SHIPPED_GTK=yes

# Find console executable in Firefox plugins.
vmrc="$(find "$HOME/.mozilla/firefox" -name vmware-vmrc -type f -perm -111 | tail -1)"
[ -x "$vmrc" ] || exit 1

VMLIB=$(dirname "$vmrc")
VMLIB=$(dirname "$VMLIB")/lib

export LD_LIBRARY_PATH=$VMLIB/libexpat.so.0:$VMLIB/libsexymm.so.2:$VMLIB/libview.so.2:$VMLIB/libvmwarebase.so.0:$VMLIB/libvmwareui.so.0:$VMLIB/libgvmomi.so.0

set -x
cd "$(dirname "$vmrc")" && "$vmrc" -h 127.0.0.1:8333

```

But I still get the 640x480 problem in that the mouse changes to local mouse if I move it across screen making most the screen unusable. 
I'm running Kubuntu 9.10 @ 1440x900.
I didn't previously have the problem on 9.04 but I was also using VMware 2.0.1 before but I'm using 2.0.2 now.

---

### Post by danteuk on 2009-11-03
I found a post in another forum, this works for me now:
Added these lines to my /usr/bin/firefox
export VMWARE_USE_SHIPPED_GTK=force
export GDK_NATIVE_WINDOWS=true

---

### Post by sdowney717 on 2009-11-03
this works also

[http://ubuntuforums.org/showthread.php?t=1306032&page=2](http://ubuntuforums.org/showthread.php?t=1306032&page=2)

> Alright I think I have a partial solution, as I mentioned earlier all the scripts I have seen for launching the web console do not help me.

I had to go into:
/home/username/.mozilla/firefox/df34789dfgj/extensions/VMwareVMRC@vmware.com/plugins/lib

Then edit the file:
wrapper-gtk24.sh

I added the following lines near the top:
VMWARE_USE_SHIPPED_GTK='force'
export VMWARE_USE_SHIPPED_GTK="force"

So now the mouse appears to work correctly.

However ctrl-alt-del does not work correctly.
I was expecting ctrl-alt-ins to work instead:
ctrl-alt-ins - no response from guest
ctrl-alt-del - no response from guest
ctrl-alt-. - (the . and del key on the numeric keypad) does work!
(BUT of course this is a a laptop and only when I am docked to I have a numeric keypad, so I'll be unable to login to a guest most of the time).

---

### Post by ben_l on 2009-11-04
Adding those lines to wrapper-gtk24.sh seems to have worked for me.  This also seems to have resolved an intermittent issue I had with the VMWare Remote Console window closing on its own occasionally.  My keyboard works fine though.  When I initially installed VMWare, I had to adjust the keyboard mapping to work with the keyboard on my ThinkPad T61.  This keyboard mapping seems to have been retained.  It was kind of annoying to have to do this, but I guess this is really the only problem I've had with the upgrade to 9.10.

---

### Post by fjm03 on 2009-11-04
Solved? Really?

The best I can see is a dirty workaround for a particular box with a suggestion that the problem is VMware's problem to solve.

When we get a script/how to/process to correctly configure VMware Server 2.0.2 on Ubuntu 9.10, THEN we can say SOLVED.

---

### Post by sdowney717 on 2009-11-05
Fix for the key mapping problem:

Edit the file: /etc/vmware/config

Add the line:
xkeymap.nokeycodeMap = "TRUE"

See these links for more details:


Some keys does not work on in the guest
[http://communities.vmware.com/thread/177010](http://communities.vmware.com/thread/177010)

---

### Post by RazorV on 2009-12-03
> **sdowney717 said:**
> the mouse does not go to the edge of the virtual window. clicking anywhere outside of a smaller rectangle insode the virtual maching does not work, the mouse cursor does not follow where it should go, the numlock light flashes on the keyboard as does the message 'to release input press cntrl g'

if i increase the virtual machine screen resolution the problem gets worse

i also discovered my keyboard in ubuntu host does not respond to shift or caplock or numlock anymore/

I rebooted and the keyboard is working, but the vmware machine xp still is doing the weird mouse
The mouse can go to the extreme left and extreme top, but cant go down to the bottom or to the extreme right.


i have this exact same problem.  hence no caps now unless i reboot.  i cannot for the life of me figure it out.  i will be reading this post for a possible solution but wanted to say you are not alone.  im running ubuntu 9.10 32bit with vmware server 2.02 and xp.  xp runs great, outlook runs great, but the darn mouse and keyboard are a peripheral devices to be delt with under vmware 2.02.

glad to know i'm not the only one thinking i was gong crazy.

greg
sarasota, fl

with no caps and no num-lock

---

### Post by jsmit89 on 2009-12-05
> **danteuk said:**
> These work-arounds are not working.
 
I had to modify the script to work for some shared library issues.
 
```

#!/bin/bash
################################################## ##############################
# Call VMWare Server's Remote Console in a clean GTK setup.
################################################## ##############################
 
# Clean GTK setup for VMWare
 
export VMWARE_USE_SHIPPED_GTK=yes
 
# Find console executable in Firefox plugins.
vmrc="$(find "$HOME/.mozilla/firefox" -name vmware-vmrc -type f -perm -111 | tail -1)"
[ -x "$vmrc" ] || exit 1
 
VMLIB=$(dirname "$vmrc")
VMLIB=$(dirname "$VMLIB")/lib
 
export LD_LIBRARY_PATH=$VMLIB/libexpat.so.0:$VMLIB/libsexymm.so.2:$VMLIB/libview.so.2:$VMLIB/libvmwarebase.so.0:$VMLIB/libvmwareui.so.0:$VMLIB/libgvmomi.so.0
 
set -x
cd "$(dirname "$vmrc")" && "$vmrc" -h 127.0.0.1:8333

```
 
But I still get the 640x480 problem in that the mouse changes to local mouse if I move it across screen making most the screen unusable. 
I'm running Kubuntu 9.10 @ 1440x900.
I didn't previously have the problem on 9.04 but I was also using VMware 2.0.1 before but I'm using 2.0.2 now.
 
Thanks for solving the problem, however I dont quite understand it. what do I have to type by dirname ? which directory names do I choose?
 
I did a normal installation..
 
Thanks in advance.
Johan

---

### Post by javajesse on 2009-12-12
QUICK FIX THAT WORKED FOR ME:

When the mouse only operates on a small area of the screen and you cant click on things outside that area:

[LIST]
[*]I took a snapshot of my current, broken state (named it S1).  
[*]I switched to to a previous snapshot and the problem did NOT exist there.
[*]I then switched forward to the broken snapshot I made (S1)
[/LIST]

The problem went away.  Why?  Dunno!

Worth a try. It saved me twice when I developed this issue. Hope this helps.

---

### Post by yakupm on 2010-01-29
sdowney717's solution:

> [I][COLOR=Green]I had to go into:
/home/username/.mozilla/firefox/df34789dfgj/extensions/VMwareVMRC@vmware.com/plugins/lib

Then edit the file:
wrapper-gtk24.sh

I added the following lines near the top:
VMWARE_USE_SHIPPED_GTK='force'
export VMWARE_USE_SHIPPED_GTK="force"[/COLOR][/I]  worked for me too.  Thanks!

---

### Post by rwheindl on 2010-05-03
Delete me.

---

