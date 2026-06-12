---
title: "AppArmor Support Thread"
date: 2009-01-24
forum: Security
---

### Post by jgoguen on 2009-01-24
To avoid cluttering up the [Share your AppArmor Profiles](http://ubuntuforums.org/showthread.php?t=1008911) thread, please post questions about AppArmor (why something is asking for certain permissions or capabilities, what is the difference between Px and ix and why do I never ever ever use Ux, how do I figure out where the real executable is...) in this thread.

---

### Post by q.dinar on 2009-01-25
[http://ubuntuforums.org/showpost.php?p=6607036&postcount=40](http://ubuntuforums.org/showpost.php?p=6607036&postcount=40) :
> hello.
xchat asks for /home/*/.recently-used.xbel . what is that, why xchat wants it, i looked into it, i have thought it is written with what file opened with what program.
also i see wine asks something though [i thought] it is off, i looked in system monitor and see "winbind"s by root.
wine asks for:
... operation="capable" name="dac_override" ... profile="/usr/bin/wine"
... operation="capable" name="dac_read_search" ... profile="/usr/bin/wine"
... operation="inode_mkdir" requested_mask="w::" denied_mask="w::" fsuid=0 name="/root/.wine/" ... profile="/usr/bin/wine"

---

### Post by jgoguen on 2009-01-25
To start off, here's a few questions that have already been asked:

> Can I have one application use different AppArmor profiles?Yes, but not easily.  You need to make a hard link from the program to a second name for the program.  This is because AppArmor enforces profiles by paths.  So let's say for example that you have /usr/bin/myprogram that you want to apply two different AppArmor profiles to.  Create an AppArmor profile for /usr/bin/myprogram.  Then, make a hard link for the path to use in the second application:
```
sudo ln /usr/bin/myprogram /usr/bin/myprogram2
```Now, create your second AppArmor profile, but instead of /usr/bin/myprogram usr /usr/bin/myprogram2.  Once that's done, you can run **myprogram** to have it use the first profile, or you can run **myprogram2** to have it use the second profile.

> What is the difference between r::, ::x, etc. in the log?These are the permissions the program is asking for.  The colons split the permissions up into user permissions, group permissions, and "other" (neither user nor group) permissions.  So **r::** means the program is asking for user read permissions.  If you see **:w:**, that means the program wants group write permissions. **::x** means "other" execute permissions.  Note that when you're giving execute permissions, you can't just give **x** - you have to give Px, Ux, or ix.  More on those later.

> What is the difference between "requested mask" and "denied mask"?**Requested mask** is what the program is asking for.  This may be something like **rmx::**.  The "m" permission means it wants permission to use mmap(2) on the executable.  **Denied mask** is what the program isn't getting.  Given the previous requested mask, if the denied mask were to be **mx::** that would mean that the AppArmor profile allows read permissions, but it does not allow map or execute permissions.  Before blindly giving those permissions, however, you should decide whether they're reqlly needed.  If you're not certain, you can always ask here.

> What's the difference between ix, ux, Px, etc.?AppArmor provides 5 permission flags for execute permissions:

[LIST]
[*]ux - Unconfined execute
[*]Ux - Unconfined execute, scrub the environment
[*]px - execute with a profile written for the application
[*]Px - execute with a profile written for the application, scrub the environment
[*]ix - execute using the existing profile
[/LIST]

In general, you should never use ux or Ux - that removes AppArmor protection for the executed program!  Instead, use Px (or px) if the application being executed has its own profile, or ix if not.

More again later!

---

### Post by jgoguen on 2009-01-25
> **q.dinar said:**
> hello.
 xchat asks for /home/*/.recently-used.xbel . what is that, why xchat wants it, i looked into it, i have thought it is written with what file opened with what program.
 also i see wine asks something though [i thought] it is off, i looked in system monitor and see "winbind"s by root.
 wine asks for:
 ... operation="capable" name="dac_override" ... profile="/usr/bin/wine"
 ... operation="capable" name="dac_read_search" ... profile="/usr/bin/wine"
... operation="inode_mkdir" requested_mask="w::" denied_mask="w::" fsuid=0 name="/root/.wine/" ... profile="/usr/bin/wine"

.recently-used.xbel is a XML file containing information about the last files opened and what applications have opened those files.  This is used in the Recent Documents (Places -> Recent Documents) list, as well as the recent documents list of applications.  Some applications don't use this file, but I believe any that are written to take advantage of the GNOME environment do use it.

I'm not sure about the Wine capabilities.  It sounds like something that Windows programs would try to override though.  dac_override means to bypass read, write and execute permission checks.  dac_read_search means to bypass file read permission checks and directory read and execute permission checks.  Windows programs may not function properly without those.

---

### Post by jgoguen on 2009-01-25
A few more questions that have been asked:

> Can I use AppArmor to restrict access based on IP address?No.  You can use AppArmor to prevent an application from accessing the network, and you can allow it access to only IPv4 or IPv6, and only TCP or UDP.  If the program is run by a specific user, you could instead use iptables to handle this, using the parameters **-m owner --uid-owner <userid>**.  The --uid-owner parameter accepts a user ID, and the iptables rule will match packets coming from a program run by that user.  To find a user ID given a username, use this command (replace "username" with the username you want to find the ID for):
```
grep username /etc/passwd | cut -d":" -f3
```
There is no way to use iptables with Ubuntu to restrict access based on the program name, because the Ubuntu Linux kernel is not compiled with the options required to enable the **--cmd-owner** flag.

> How do I decide what path to use for the profile?You need the full path that actually gets run.  I'll use Firefox here as an example, since it requires following some links:

[LIST]
[*]Start with the path to Firefox.  Checking the menu shows that the command run is **firefox**.
[*]Find where the firefox command is: **which firefox** (output: **/usr/bin/firefox**)
[*]Check to see if this is a link: **readlink /usr/bin/firefox** (output: **firefox-3.0**)
[*]This means that the link points to *firefox-3.0* relative to */usr/bin/firefox*, and the full path now becomes **/usr/bin/firefox-3.0**
[*]Check if this is a link: **readlink /usr/bin/firefox-3.0** (output: ../lib/firefox-3.0.5/firefox.sh[/b])
[*]This means that the link points to *../lib/firefox-3.0.5/firefox.sh* relative to */usr/bin/firefox-3.0* and the full path now becomes **/usr/lib/firefox-3.0.5/firefox.sh**
[*]Check if this is a link: **readlink /usr/lib/firefox-3.0.5/firefox.sh** (output: <none>)
[*]No output means this is not a link.  You've now found the full path to use for your profile
[/LIST]


> Just to take that last question one step further, how do I know what name to give the AppArmor profile?Profile files take a name based off the full path used for the profile.  Let's use Firefox as an example again, since we've already found its full path:

[LIST]
[*]First, take the full path name and remove the first slash.  This means that **/usr/lib/firefox-3.0.5/firefox.sh** becomes **usr/lib/firefox-3.0.5/firefox.sh**
[*]Now, convert all remaining slashes to periods.  The name now becomes **usr.lib.firefox-3.0.5.firefox.sh**
[*]This is the name for the AppArmor profile file.  AppArmor profiles are placed in /etc/apparmor.d/
[/LIST]

---

### Post by q.dinar on 2009-01-28
hello. i asked this: [does apparmor work against codecs, flash player, videodriver?](http://ubuntuforums.org/showthread.php?t=1033264)
now i know that i cannot make separate profile for flash when it is used with firefox. by the way does not flash package include a separate flash player for swf files?

now i ask these: how to name/create profile file for nvidia and ati videodriver.
can we make separate package for video codecs for they are used with different players. but i think there is another way: to make rules for them in separate file and include that in different profiles. that also applies to rules for flash player that can be used with different browsers.
there are "bad" codec package that is in "multiverse", is it at least partially closed-source? 8:11 gmt: i have posted [notice if multiverse package is completely/fully open-source](http://brainstorm.ubuntu.com/idea/17713/) in ubuntu brainstorm.

---

### Post by q.dinar on 2009-01-28
/usr/share/libthai/* r,

is in firefox's [apparmor] profile file, but it still asks for it:

Jan 28 09:52:17 linux2008 kernel: [808819.249751] type=1503 audit(1233125537.243:5497): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=1000 name="/usr/share/libthai/thbrk.sbm" pid=29530 profile="/usr/lib/firefox-3.0.5/firefox.sh"

---

### Post by q.dinar on 2009-01-28
and [btw] what are these?:

808819.249751
type=1503
audit(1233125537.243:5497)
fsuid=1000

---

### Post by jgoguen on 2009-01-28
> **q.dinar said:**
> how to name/create profile file for nvidia and ati videodriver.
can we make separate package for video codecs for they are used with different players.
No, and no, for the same reason you can't have a profile for the Flash player in Firefox.  I believe that Gnash and swfdec both include standalone Flash players, and you could write profiles for those, but unless Firefox executes those as separate processes Flash in Firefox would remain affected only by the Firefox profile.  Adobe's Flash plugin is only a plugin, not a standalone player, so you can't write a profile for it.  Similarly, because the video drivers are loaded as part of X and not executed, the profile would have to be written for X, not for the video drivers.  And video codecs are the same, they're loaded as part of the video player application and so the profile would have to be written for the video player (totem, mplayer, etc.) and not the video codecs themselves.  I would love to be wrong on this entire paragraph though, so if anyone can show that I'm wrong please do :)

---

### Post by jgoguen on 2009-01-28
> **q.dinar said:**
> /usr/share/libthai/* r,

is in firefox's [apparmor] profile file, but it still asks for it:

Jan 28 09:52:17 linux2008 kernel: [808819.249751] type=1503 audit(1233125537.243:5497): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=1000 name="/usr/share/libthai/thbrk.sbm" pid=29530 profile="/usr/lib/firefox-3.0.5/firefox.sh"
Did you replace the profile after you edited it?
```
sudo apparmor_parser -r < usr.lib.firefox-3.0.5.firefox.sh
```

---

### Post by q.dinar on 2009-02-04
yes, replacing has helped. thank you.
now i see this:

Feb  4 15:26:23 linux2009 kernel: [  617.777856] type=1503 audit(1233750383.067:156): operation="inode_permission" requested_mask="::x" denied_mask="::x" fsuid=1000 name="/sbin/killall5" pid=7602 profile="/usr/lib/firefox-3.0.5/firefox.sh"

should i allow it? how does it use it?

and i want to say about a feature of apparmor: its permissions are other way than linux's. when new user is added and firefox first started by it, it requested w permission for .mozilla in home directory. i added it and it works. w permission for home directory is not needed.

---

### Post by q.dinar on 2009-02-05
man iptables:
>  --cmd-owner name
   Matches  if  the  packet was created by a process with the given command name.  (this option is present only if iptables was compiled under a kernel supporting this feature)
this has not worked. in ubuntu 8.10 . i think because iptables is not compiled so.
i tried this command:
sudo iptables -I OUTPUT 2 -p tcp -m owner --uid-owner 1234 --cmd-owner virtualbox --dport 80 -j ACCEPT

---

### Post by jgoguen on 2009-02-05
> **q.dinar said:**
> this has not worked. in ubuntu 8.10 . i think because iptables is not compiled so.
i tried this command:
sudo iptables -I OUTPUT 2 -p tcp -m owner --uid-owner 1234 --cmd-owner virtualbox --dport 80 -j ACCEPT
That's unfortunate.  Indeed it doesn't work.  I've updated my post above to reflect this :(

---

### Post by jgoguen on 2009-02-06
> **q.dinar said:**
> yes, replacing has helped. thank you.
now i see this:

Feb  4 15:26:23 linux2009 kernel: [  617.777856] type=1503 audit(1233750383.067:156): operation="inode_permission" requested_mask="::x" denied_mask="::x" fsuid=1000 name="/sbin/killall5" pid=7602 profile="/usr/lib/firefox-3.0.5/firefox.sh"

should i allow it? how does it use it?
I'm not sure how that's used.  I don't allow it and I haven't run into problems, but I also haven't seen Firefox asking for that program.  What were you doing when you saw that?  Do you have any steps that allow you to consistently make Firefox ask for /sbin/killall5?

> **q.dinar said:**
>  and i want to say about a feature of apparmor: its permissions are other way than linux's. when new user is added and firefox first started by it, it requested w permission for .mozilla in home directory. i added it and it works. w permission for home directory is not needed.
Quite right, Linux and AppArmor use two different sets of permissions.  The permissions applied are the least common permissions between the two.  So if a file has Linux permissions for read, write, and execute, but the AppArmor profile permissions allow read and execute, you won't be able to write to the file under that profile no matter how hard you try.

---

### Post by q.dinar on 2009-02-15
i am quite sad. :( .

[SIZE="4"]you should rename and modify and reload /etc/apparmor.d/usr.lib.firefox-3.0.5.firefox.sh when firefox has upgraded to 3.0.6 ![/SIZE]

2009-12-22: this can be solved , at least in apparmor of ubuntu 9.10 : there is preinstalled but turned off firefox profile, profile's file name is not important, it is "usr.bin.firefox-3.5" , but in it:
...
#include <tunables/global>

/usr/lib/firefox-3.5.*/firefox {
  #include <abstractions/audio>
...
and that works with all versions, i think.

---

### Post by jgoguen on 2009-02-15
Yes, you will need to change the file name and the paths in the file to match the new paths.  The same would also apply to anything else installed with version information in the path name, like XUL Runner (/usr/lib/xulrunner-1.9/).

AppArmor is definitely not a "set and forget" security system.  In fact, any system which claims to be such a thing should be viewed suspiciously.  When upgrades are done, or new packages installed, current rules may need to be revised or removed, or new rules may need to be added.

---

### Post by q.dinar on 2009-02-16
even when i have just started firefox, and only one blank tab(page) was on the start, it asked for killall5. when i opened new blank tab(page) it asked for it 4 times - but programs usually ask for things several times if not succeeded on first time. i allowed it but now again have denied it, so i see it now in syslog.

"Quite right, Linux and AppArmor use two different sets of permissions. The permissions applied are the least common permissions between the two. ..."
but i wanted to say about other feature: to create new "a" directory in "b" directory in linux "write" permission to "b" directory should be. in apparmor rules "write" permission to non-existing yet "a" itself is enough.

i see that when i switch to firefox from other program with clicking to tab on task bar or with alt+tab it asks for killall5 2 times.

---

### Post by q.dinar on 2009-02-16
```

Feb 16 10:53:31 linux2009 kernel: [  382.914441] type=1505 audit(1234770811.273:665): operation="profile_replace" name="/usr/bin/xchat" name2="default" pid=7453
Feb 16 10:53:43 linux2009 kernel: [  395.513632] type=1502 audit(1234770823.873:666): operation="inode_permission" requested_mask="::x" denied_mask="::x" fsuid=1000 name="/sbin/killall5" pid=7460 profile="/usr/bin/xchat"
Feb 16 10:53:43 linux2009 kernel: [  395.514803] type=1504 audit(1234770823.873:667): operation="exec" info="set profile" pid=7460 profile="null-complain-profile"
Feb 16 10:53:43 linux2009 kernel: [  395.514830] type=1502 audit(1234770823.873:668): operation="file_permission" requested_mask="::r" denied_mask="::r" fsuid=1000 name="/sbin/killall5" pid=7460 profile="null-complain-profile"
Feb 16 10:53:43 linux2009 kernel: [  395.520025] type=1502 audit(1234770823.877:669): operation="file_permission" requested_mask="::r" denied_mask="::r" fsuid=1000 name="/sbin/killall5" pid=7460 profile="null-complain-profile"
Feb 16 10:53:43 linux2009 kernel: [  395.521749] type=1502 audit(1234770823.881:670): operation="file_permission" requested_mask="::r" denied_mask="::r" fsuid=1000 name="/sbin/killall5" pid=7460 profile="null-complain-profile"
Feb 16 10:53:43 linux2009 kernel: [  395.525482] type=1502 audit(1234770823.885:671): operation="inode_permission" requested_mask="::x" denied_mask="::x" fsuid=1000 name="/lib/ld-2.8.90.so" pid=7460 profile="null-complain-profile"

```
also xchat has asked for killall5.
what is null-complain-profile ?

---

### Post by q.dinar on 2009-02-16
[does firefox use killall5? • mozillaZine Forums](http://forums.mozillazine.org/viewtopic.php?f=23&t=1096505)

---

### Post by q.dinar on 2009-02-16
now i have tested with renaming .mozilla . it asks for killall5 with newly created profile. but just now other user has used firefox, but in that time it has not asked for killall5!

---

### Post by jgoguen on 2009-02-16
> **q.dinar said:**
> ```

Feb 16 10:53:31 linux2009 kernel: [  382.914441] type=1505 audit(1234770811.273:665): operation="profile_replace" name="/usr/bin/xchat" name2="default" pid=7453
Feb 16 10:53:43 linux2009 kernel: [  395.513632] type=1502 audit(1234770823.873:666): operation="inode_permission" requested_mask="::x" denied_mask="::x" fsuid=1000 name="/sbin/killall5" pid=7460 profile="/usr/bin/xchat"
Feb 16 10:53:43 linux2009 kernel: [  395.514803] type=1504 audit(1234770823.873:667): operation="exec" info="set profile" pid=7460 profile="null-complain-profile"
Feb 16 10:53:43 linux2009 kernel: [  395.514830] type=1502 audit(1234770823.873:668): operation="file_permission" requested_mask="::r" denied_mask="::r" fsuid=1000 name="/sbin/killall5" pid=7460 profile="null-complain-profile"
Feb 16 10:53:43 linux2009 kernel: [  395.520025] type=1502 audit(1234770823.877:669): operation="file_permission" requested_mask="::r" denied_mask="::r" fsuid=1000 name="/sbin/killall5" pid=7460 profile="null-complain-profile"
Feb 16 10:53:43 linux2009 kernel: [  395.521749] type=1502 audit(1234770823.881:670): operation="file_permission" requested_mask="::r" denied_mask="::r" fsuid=1000 name="/sbin/killall5" pid=7460 profile="null-complain-profile"
Feb 16 10:53:43 linux2009 kernel: [  395.525482] type=1502 audit(1234770823.885:671): operation="inode_permission" requested_mask="::x" denied_mask="::x" fsuid=1000 name="/lib/ld-2.8.90.so" pid=7460 profile="null-complain-profile"

```also xchat has asked for killall5.
I think I found this one.  /bin/pidof is a symbolic link to /sbin/killall5.  So programs that find /bin/pidof and follow the link rather than just calling 'pidof' will find themselves calling /sbin/killall5.  My first instinct now is that this is harmless and it's the program trying to find a PID.  Hopefully not its own, C has getpid() for that...

> **q.dinar said:**
>  what is null-complain-profile ?
Check out [this post](http://forums.novell.com/novell-product-support-forums/apparmor/302143-about-apparmors-audit-log-format-post1418231.html#post1418231) over at Novell's forums and see if that applies to you. null-complain-profile is used in learning mode, it complains about absolutely everything.

---

### Post by q.dinar on 2009-02-16
there is other message in log.

how to create profile for x server? as was said in this thread or "share your apparmor profiles" to limit/set rules for/confine/restrict video driver profile for x server should be created.

---

### Post by jgoguen on 2009-02-16
> **q.dinar said:**
> but i wanted to say about other feature: to create new "a" directory in "b" directory in linux "write" permission to "b" directory should be. in apparmor rules "write" permission to non-existing yet "a" itself is enough.
OK, I see where you're going with this.  Yes, that does seem to be the case, and I'm not sure why, or even if that's the correct behaviour...sounds like a good candidate for a bug to me.  You can report bugs [here](https://bugs.edge.launchpad.net/ubuntu/+filebug).

---

### Post by bodhi.zazen on 2009-02-16
> **q.dinar said:**
> i am quite sad. :( .

[SIZE=4]you should rename and modify and reload /etc/apparmor.d/usr.lib.firefox-3.0.5.firefox.sh when firefox has upgraded to 3.0.6 ![/SIZE]

While I agree apparmor requires active monitoring, I would also suggest you file this as a bug report in Launchpad.

---

### Post by jgoguen on 2009-02-16
> **q.dinar said:**
> how to create profile for x server? as was said in this thread or "share your apparmor profiles" to limit/set rules for/confine/restrict video driver profile for x server should be created.
Very carefully :)  I'm only half-joking, and I'm not completely sure where to start.  Probably /usr/sbin/gdm and /usr/X11R6/bin/X, and be prepared to do a lot of work tracing why it's not working and what it's asking for.  You may want to put the profiles into complain mode so you don't completely lose graphics:
```
sudo aa-complain /path/to/profile
```Then when you're satisfied and/or ready to test your profile in enforcing mode:
```
sudo aa-enforce /path/to/profile
```Remember of course that this doesn't give you the ability to have separate profiles for nvidia, nv, radeon, etc., the profile is for X in general.

To get an idea of the programs you'd need to have profiles for (or give execute permissions with 'ix') open a terminal and use this command:
```
ps fax
```That prints out a process tree.  Look for the set starting with '/usr/sbin/gdm'.

---

### Post by bodhi.zazen on 2009-02-16
Locking down X or GDM with apparmor will probably be impractical, to say the least.

The things, IMO, you should look at are network facing applications or deamons (firefox, ssh, etc) and not something big like X.

If you need to lock down X or a shell (like bash) take a look at jdong's jailbash.

[http://www.friedcpu.net/?p=70](http://www.friedcpu.net/?p=70)

Just make jailbash the default, log in shell 

Or something like selinux.

---

### Post by duanedesign on 2009-03-20
I just recently installed apparmor and I am fine tuning my profiles. I have got just one more message, related to Firefox, popping up in my log that I want to address. 

Mar 20 20:01:08 my-computer kernel: [ 0000.000000] type=0000 audit(000000.000:0000): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=1000 name="/home/duanedesign/.icons/" pid=5664 profile="/usr/lib/firefox-3.0.7/firefox.sh"

I have  in my Firefox profile:

@{HOME}/.icons/** r,

adding the line above did fix five or six log messages like these:

~/.icons/hydroxygen/16x16/categories
~/.icons/hydroxygen/16x16/devices
~/.icons/hydroxygen/16x16/emblems
ECT...

So I get the feeling it is working on some level. 

I understand the colon's significance in showing (owner permissions:extended ownership tests: other permissions). Does this provide a clue to help me solve this.

I thank you in advance for any help you can give me.

**[COLOR="Red"]UPDATE:[/COLOR]** funny I worked on this for over an hour and five minutes after i break down and ask for help I come up with a solution:)

I added the following to my firefox profile:

@{HOME}/.icons/ r,

I started Firefox, and no message in my log. I guess I still have a question do I need both
@{HOME}/.icons/ r,
@{HOME}/.icons/** r,
or is there a better way to get apparmor to allow firefox to access all my icons.

---

### Post by jgoguen on 2009-03-20
Short answer - yes, you do need both, but only if the application actually needs to read the directory :)  That tends to be true if it doesn't know for sure what the path to the file is, which may be the case here.

The issue is that using ** will match everything in the directory and its subdirectories - but not the directory itself.  So using
```
@{HOME}/.icons/** r,
```will provide read access for all files and directories under /home/<username>/.icons/, but does not provide any access for /home/<username>/.icons/ at all.  That's taken care of by the other rule you discovered you need:
```
@{HOME}/.icons/ r,
```This is the rule that gives access to read the directory itself.

Similarly, but going further than needed to answer your question, if you only used
```
@{HOME}/.icons/* r,
```you still would have no read access for /home/<username>/.icons/, but you would have read access for all files directly inside it, plus all subdirectories directly underneath it - but not the contents of those subdirectories.  As an example, you could see that /home/<username>/.icons/16x16/ exists, and you could also see that /home/<username>/.icons/16x16/unknown.png exists, but you would not be able to read that file.

Hope that helps and doesn't raise more questions than it answers - but feel free to ask away if you have any more questions or if I wasn't clear enough :)

---

### Post by bodhi.zazen on 2009-03-20
That was going to be my advice :twisted:

Nice to see people learning apparmor.

FYI: I have posted some apparmor profiles for your reference here :

[http://bodhizazen.net/aa-profiles/](http://bodhizazen.net/aa-profiles/)

I am looking for people willing to post their profiles, so if anyone is willing please send me a PM.

---

### Post by jgoguen on 2009-03-20
> **bodhi.zazen said:**
> That was going to be my advice :twisted:
I just learn from my betters ;)

---

### Post by q.dinar on 2009-04-03
hello.

i have looked at what is run by what with ps fax and with system monitor.
though many programs are run by gdm, among them there is nautilus, they all are run in "x-session-manager" branch and nothing is run by Xorg. only two things: Xorg and x-session-manager are run by gdm directly. what will be if i restrict only Xorg? if videodriver is in Xorg it would work.
how can i restart Xorg? quitting and logging in, i think.
and firefox is not run by x-session-manager. i have just started gedit to check and see that it also does not run in gdm branch.

what do you think about restricting installer of ".deb" files? to install deb files for ubuntu that are got from different sites relatively harmlessly, because deb file can (or always?) contain script and it runs as root. as i know there are many deb files of newer versions of programs that are in ubuntu's own repository and also of programs that are not in the repository and among them closed-source programs.
for example process of installing of deb file should not browse files in /mnt/ subdirectories, i think.

---

### Post by jgoguen on 2009-04-03
> **q.dinar said:**
> i have looked at what is run by what with ps fax and with system monitor.
though many programs are run by gdm, among them there is nautilus, they all are run in "x-session-manager" branch and nothing is run by Xorg. only two things: Xorg and x-session-manager are run by gdm directly. what will be if i restrict only Xorg? if videodriver is in Xorg it would work.
I'm not entirely certain what you're asking about here.  Are you asking what you will restrict if you use AppArmor on Xorg?  You would restrict Xorg, anything loaded by Xorg, and anything run as a child of Xorg.  Unless the child has its own profile and you specify Px (or px), or if you specify Ux (or ux).  Although, as has been mentioned earlier, there are better places to start for securing your system.  If you allow Xorg to listen for incoming connections, then Xorg would be a good (although large and complex) candidate for AppArmor, but if you leave it at the default setting and don't allow remote X connections (note: NOT the same as allowing X forwarding over SSH) then it's not as important IMO.

> **q.dinar said:**
>  how can i restart Xorg? quitting and logging in, i think.
No, that won't restart Xorg, just your login session.  You can press Ctrl+Alt+Backspace.  That will immediately terminate Xorg (and any GUI programs you have running, and any of their children) and bring you back to the login screen.  This was disabled in Jaunty, you can add this to **/etc/X11/xorg.conf** and restart to enable it again:
```
Section "ServerFlags"
    Option  "DontZap"   "False"
EndSection
```Note that you should not have two ServerFlags sections, so just merge this with the existing one if you already have a ServerFlags section.

> **q.dinar said:**
> and firefox is not run by x-session-manager. i have just started gedit to check and see that it also does not run in gdm branch.
No, you're right, they (and IIRC everything else you start) is run as its own process.  Restrictions on gdm (or kdm, or Xorg, or x-session-manager, or /usr/bin/bodhi-zazens-super-spyware-script-pretending-to-be-Xorg :)) will not affect these.

> **q.dinar said:**
>  what do you think about restricting installer of ".deb" files? to install deb files for ubuntu that are got from different sites relatively harmlessly, because deb file can (or always?) contain script and it runs as root. as i know there are many deb files of newer versions of programs that are in ubuntu's own repository and also of programs that are not in the repository and among them closed-source programs.
for example process of installing of deb file should not browse files in /mnt/ subdirectories, i think.
Depends on what precisely you're trying to achieve.  As you note, these are run as root, and they always have scripts.  In fact they can have up to (IIRC) 4 scripts, possibly 6 - pre-install, post-install, pre-remove, and post-remove.  There may also be install and remove, I don't recall.  However, regardless, I would be much less concerned about what these scripts are doing in /mnt/ or /media/ (which you could deny access to and legitimately expect nothing to break) and much more concerned about what they're doing in /bin/, /sbin/, /usr/bin/, /usr/sbin/..., all of which you would need to allow read, write, and symlink access to.  Think for a second.  If I trick you into installing "my-malicious-package_1.0.0-0ubuntu1.deb" and I drop stuff in /mnt/ only, then big deal.  Provided I don't change other things of course :)  Now, let's say that I later also trick you into installing "my-malicious-package_1.0.1-0ubuntu1.deb" which does any (all?) of these clearly malicious things:

[LIST]
[*]Replace /bin/ls with a modified version.  Use your imagination to think of what I could do with that.
[*]Replace /boot/vmlinuz-2.6.28-11-generic with a modified version.  That's your kernel.  I'm sure you can think of plenty of things I could do with *that* ;)
[*]Replace /usr/bin/firefox with a symlink to my malicious script that "does stuff" before starting the real Firefox
[/LIST]

The list of possibilities goes on of course.  So is there value in restricting the dpkg installer?  Yes, but not as much as you might think.

---

### Post by q.dinar on 2009-04-11
[QUOTE="jgoguen"]You would restrict Xorg, anything loaded by Xorg, and anything run as a child of Xorg.[/QUOTE]
is video driver code >2009-04-18:[s]completely loaded only by Xorg?[/s]loaded completely by Xorg and only by Xorg?<

[QUOTE="jgoguen"]If you allow Xorg to listen for incoming connections, then Xorg would be a good (although large and complex) candidate for AppArmor, but if you leave it at the default setting and don't allow remote X connections (note: NOT the same as allowing X forwarding over SSH) then it's not as important IMO.[/QUOTE]
can driver code make connections [by itself] over the internet if Xorg is configured to be not allowed to make remote X connections?

i have not seen anything under Xorg branch in process list. what process can be shown there?

---

### Post by jgoguen on 2009-04-11
> **q.dinar said:**
> is video driver code completely loaded only by Xorg?
Yes, as far as I'm aware.

> **q.dinar said:**
> can driver code make connections [by itself] over the internet if Xorg is configured to be not allowed to make remote X connections?
Probably not, but I wouldn't rule out the possibility.

> **q.dinar said:**
>  i have not seen anything under Xorg branch in process list. what process can be shown there?
You're probably looking for gdm or kdm if you want to see child processes.  Keep in mind that everything started by gdm/kdm/xdm may not necessarily be shown as a child process!  That's important to remember, since it's possible that you write a profile for gdm and suddenly see that other processes are bound by that same profile.

As has already been said though, locking down X/GDM/KDM/XDM is going to be difficult, including quite likely a lot of time spent editing with no working GUI, and the benefits are unlikely to outweigh the troubles.  I will happily help you out, but I want to make sure you have fair warning before you start :)  Network applications, like Firefox, Evolution, Pidgin, Thunderbird, XChat, SSH, etc. are better targets for profiles.  I hesitate to say SSH though, in that case you're probably better using jdong's [jailbash]("http://www.friedcpu.net/?p=70") instead.  Yes, X can listen on a network, but if you haven't configured it to do so it won't accept incoming connections, so the benefit is limited.

If you really want to, start with a base profile (things that make sense to you for X/GDM/KDM/XDM to need access to), put the profile in complain mode, and then load it and restart.  That will let you keep your GUI and see everything it's asking for access to.  Check what it legitimately needs, add that to the profile, restart again.  Rinse and repeat until it's only complaining about things it doesn't actually need.

You may also find that it's easier (for profile creation, readability, maintenance, and generally making sense of everything 6 months down the road) to create multiple smaller profiles (one for GDM, one for each program called by GDM, and so on) and using the 'Px' execute permissions rather than trying to fit everything into a single profile with lots of 'ix' execute permissions.  That advice also applies to other smaller applications too.  Rather than writing a profile for Firefox that includes everything needed for file-roller or ark to run, write profiles for file-roller and ark and give Firefox Px access to those programs.

---

### Post by rileinc on 2009-04-17
Is _[this](http://ubuntuforums.org/showthread.php?p=7091491#post7091491)_ too permissive?

While I was going through logprof, firefox wanted read access to the following:
```
  deny owner "/home/*/.BOINC Manager" r,
  deny owner /home/*/.DCOPserver_Roadrunner64__0 r,
  deny owner /home/*/.aspell.en.prepl r,
  deny owner /home/*/.bash_logout r,
  deny owner /home/*/.esd_auth r,
  deny owner /home/*/.gksu.lock r,
  deny owner /home/*/.pulse-cookie r,
  deny owner /home/*/.sudo_as_admin_successful r,
  deny owner /home/*/.xsession-errors r,
  deny /proc/1/cmdline r,
  deny /proc/1/stat r,
  deny /proc/2/cmdline r,
  deny /proc/2/stat r,
  deny /proc/3/cmdline r,
  deny /proc/3/stat r,
  deny /proc/4/cmdline r,
  deny /proc/4/stat r,
  deny /sbin/killall5 x,
  deny /var/run/dbus/system_bus_socket w,
```Should I allow them? What do they do and why does firefox wants read access to them? I've denied them for the time being.

---

### Post by bodhi.zazen on 2009-04-17
Is firefox working ?

If so, then you are done.

If not, then you will have to allow more things ;)

---

### Post by jgoguen on 2009-04-18
There's a lot of files Firefox tries to access that I just can't explain.  Files like ~/.viminfo and ~/.rsyncignore (which is a custom file, so it's really weird that Firefox wants it!) make no sense to me for Firefox to have access to, but it seems to try anyway.

As for your profile, basically what bodhi said - if Firefox is working, and you've achieved your goals in creating the profile, then the profile is fine :)

---

### Post by rileinc on 2009-04-20
> **jgoguen said:**
> As for your profile, basically what bodhi said - if Firefox is working, and you've achieved your goals in creating the profile, then the profile is fine :)Ah I see. I asked because I don't want to permit things that I'm not suppose to allow.

Quick question: when I remove a profile, do I have to specifically tell AppArmor that the profile is gone (e.g. apparmor_parser -R /etc/apparmor.d/profile), or can I just delete it from /etc/apparmor.d (then reload AA)?

---

### Post by bodhi.zazen on 2009-04-20
Delete the profile and re-load apparmor.

You do not need to worry too much about allowing something, remember without apparmor firefox has full access to your system limited only by permissions.

With apparmor firefox has less access limited by the aparmor kernel module and permissions.

In general it should be obvious what to confine, but to be honest this is an area where I prefer selinux ;)

---

### Post by loudog23 on 2009-05-02
Hello everyone,

as a first timer, i tried creating a profile for pidgin to get some pratice with apparmor. When in enforce mode, Pidgin wont even load :\

Im not sure i got everything right, but when i do:
```

lou@trooper:~$ sudo genprof pidgin
Please start the application to be profiled in 
another window and exercise its functionality now.

Once completed, select the "Scan" button below in 
order to scan the system logs for AppArmor events.  

For each AppArmor event, you will be given the  
opportunity to choose whether the access should be  
allowed or denied.

Profiling: /usr/bin/pidgin

[(S)can system log for SubDomain events] / (F)inish
Reading log entries from /var/log/messages.
Updating AppArmor profiles in /etc/apparmor.d.

Create New User?

(Y)es / [(N)o]
Username:

```
I followed the instruction, i saw the messages log entry for pidgin as i took him for a spin, then when i press the S key, the create user appear.... What user are we talking about here? i did not find any help for this :/

Apparmor had created and file for pidgin but it only shows:
```

# Last Modified: Sat May  2 13:33:45 2009
#include <tunables/global>

/usr/bin/pidgin flags=(complain) {
  #include <abstractions/base>

}

```

i installed the apparmor_profiles
if i run apparmor_status, pidgin is loaded
```

 sudo apparmor_status
apparmor module is loaded.
17 profiles are loaded.
5 profiles are in enforce mode.
   /usr/share/gdm/guest-session/Xsession
   /usr/lib/cups/backend/cups-pdf
   /usr/bin/pidgin
   /usr/sbin/cupsd
   /usr/sbin/avahi-daemon
12 profiles are in complain mode.
   /usr/sbin/identd
   /usr/sbin/ntpd
   /sbin/klogd
   /usr/sbin/dnsmasq
   /usr/sbin/nmbd
   /sbin/syslogd
   /usr/sbin/smbd
   /sbin/syslog-ng
   /usr/sbin/traceroute
   /usr/sbin/nscd
   /bin/ping
   /usr/sbin/mdnsd
5 processes have profiles defined.
1 processes are in enforce mode :
   /usr/sbin/cupsd (4792) 
0 processes are in complain mode.
4 processes are unconfined but have a profile defined.
   /sbin/klogd (4681) 
   /usr/sbin/avahi-daemon (4727) 
   /sbin/syslogd (4630) 
   /usr/sbin/avahi-daemon (4726) 
lou@trooper:~$ 

```

Thx for any input

--------

does apparmor replace chrooting in a better ways? Can both live together?

Im planning on running apache2 and proftpd. Any tips to apparmor them? or any profile to share?

EDIT: i just saw that a a bit more complex to apparmor apache because of the subprocess. I will need to get further into that. and see if apparmor is really worth it for me.



thx again
lou

---

### Post by loudog23 on 2009-05-02
deleted

---

### Post by jgoguen on 2009-05-04
> **loudog23 said:**
> as a first timer, i tried creating a profile for pidgin to get some pratice with apparmor. When in enforce mode, Pidgin wont even load :\
If you've got the profile you had quoted loaded, that's because AppArmor thinks it should deny everything.  Try using this profile as a base, and tweak it to your needs: [http://bodhizazen.net/aa-profiles/jgoguen/ubuntu-9.04/usr.bin.pidgin](http://bodhizazen.net/aa-profiles/jgoguen/ubuntu-9.04/usr.bin.pidgin)

> **loudog23 said:**
>  I followed the instruction, i saw the messages log entry for pidgin as i took him for a spin, then when i press the S key, the create user appear.... What user are we talking about here? i did not find any help for this :/
I'm not very familiar with genprof, and I can't figure out why it's asking for a username.  Hopefully someone else has some insights.  I would completely remove whatever profile is currently there, reload AppArmor (sudo /etc/init.d/apparmor reload) and try **sudo aa-genprof /usr/bin/pidgin** again.  Failing that, or if you just want something to look at for comparison, I would make use of the profile I linked to.

> **loudog23 said:**
>  does apparmor replace chrooting in a better ways? Can both live together?
Yes and I think so.  A chroot jail can be broken out of.  AppArmor restrictions aren't so easy to break.  As for the two playing nicely together, I don't see why not.  It would require some extra thought as to the absolute paths of programs required before and after calling chroot(), and I don't know for sure if AppArmor would apply to absolute paths relative to the real root directory or relative to the chroot() but that wouldn't be too hard to figure out.

> **loudog23 said:**
> Im planning on running apache2 and proftpd. Any tips to apparmor them? or any profile to share?

EDIT: i just saw that a a bit more complex to apparmor apache because of the subprocess. I will need to get further into that. and see if apparmor is really worth it for me.
Whether AppArmor is worth it for you depends on what you're trying to achieve.  The answer, especially if you're accepting arbitrary data from an arbitrary source (which you are with both programs you've mentioned) is typically "quite likely" for network applications.  Apache would certainly be an interesting beast to configure, but even with subprocesses it wouldn't be that much worse than any other single-process application.  Just remember to put your profiles (because you'll quite likely be writing multiple profiles for Apache and its children) into complain mode and check /var/log/messages for AppArmor deny entries.  Keep in mind that multiple profiles doesn't mean multiple files - a single file can contain all the profiles you want.  [This profile]("http://bodhizazen.net/aa-profiles/jgoguen/ubuntu-9.04/usr.lib.thunderbird.thunderbird") is an example of how to handle multiple profiles in one file.  If you were trying to restrict mod_perl, mod_php, mod_python, and other Apache modules it would probably get a little weird.  To make things a little easier (or harder?) for that, you could find mod_change_hat (which isn't in the Ubuntu repos) and use that.  It will allow you to have a sub-profile for each script and a default sub-profile for scripts that don't match an existing sub-profile.

---

### Post by loudog23 on 2009-05-09
ty for your reply,
Quick technical question.
I have a private ftp (proftpd), If i can make a profile to succefully connect locally (ip 127.0.1.1), can i assume web request to be allowed too?
I don't have access to another web connection, therefore i can't try it from external source.

---

### Post by jgoguen on 2009-05-09
If your profile allows you to connect from localhost, you can safely assume that your AppArmor profile won't prevent other incoming connections.  AppArmor can't restrict IP addresses, it can only allow or deny TCP and/or UDP connections for IPv4 and/or IPv6.  Doesn't mean your firewall won't be restricting anything though, so be sure to check that, and also check port forwarding on your router (if applicable).

---

### Post by q.dinar on 2009-05-31
i am not going to allow some files. but apparmor writes messages to syslog not stopping, continuously, near 3 messages per second in syslog and messgages. how to stop it? apparmor must have such ability, because this is its main target, goal - to block up programs, it is normal, so it should not write so many to log files.

---

### Post by jgoguen on 2009-05-31
AppArmor writes one message per access attempt.  So if you write a profile for /usr/bin/myprogram that does not allow access to /etc/shadow and /usr/bin/myprogram makes 10 attempts per second to access /etc/shadow, you will get approximately 10 messages per second in your log saying that access was denied.

---

### Post by rookcifer on 2009-06-14
Anyone tried to profile the latest Firefox-3.0.11?  I am not having any luck as there appears to be something wrong with how AppArmor is parsing logs.  If I do 
```

sudo aa-genprof firefox
```

and then attempt to "Scan" for changes (after I run firefox for a while), it will find some of the denial log messages but not all of them.  Once I click on "Finished" and firefox goes into enforce mode, it won't open if I try to restart it.  Thereafter, I ran:

```
sudo aa-logprof
```

but it finds no log messages.  However, there is a "null-complain-profile" that is still listed in complain mode.  ps -A shows this as being firefox.  So, what's the deal with these null-profiles and how does one integrate them with an existing firefox profile?

Also, firefox is asking for dac_overide capabilities.  It should not need this!

I saw that there were some bugs filed about AppArmor (in Jaunty) not parsing error logs properly.  Some people on launchpad said that installing autid.d helped them.  It doesn't work for me -- I'm still getting this strange behavior.

Or maybe I am just not doing it right?

---

### Post by jgoguen on 2009-06-14
I'll be profiling the latest Firefox later today.  I can't imagine why it's asking for dac_override, but then again I still haven't figured out why it wants to read ~/.rsynclist (a file I created myself for one of my scripts) or why it's looking for a lot of things in /proc/ that aren't related to it...

I'll be starting from my current profile, which is posted [here](http://bodhizazen.net/aa-profiles/jgoguen/ubuntu-9.04/usr.lib.firefox-3.0.10.firefox.sh).  I'll be removing a lot of stuff and trying to re-integrate the [file-roller profile](http://bodhizazen.net/aa-profiles/jgoguen/ubuntu-9.04/usr.bin.file-roller) back into Firefox, so I'll be sure to post the result here once I'm done.

---

### Post by bodhi.zazen on 2009-06-14
If it helps , my profile is here

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.04/usr.lib.firefox-3.0.10.firefox.sh](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.04/usr.lib.firefox-3.0.10.firefox.sh)

All I changed was the version from "10" to "!!"

Have not looked at logs ..

---

### Post by rookcifer on 2009-06-14
> **bodhi.zazen said:**
> If it helps , my profile is here

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.04/usr.lib.firefox-3.0.10.firefox.sh](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.04/usr.lib.firefox-3.0.10.firefox.sh)

All I changed was the version from "10" to "!!"

Have not looked at logs ..

That's what I ended up doing.  After trying to unsuccessfully aa-genprof firefox, I just went and changed 10 to 11 inside the profile and all seems to be working.  I posted the profile in the profiles thread.

---

### Post by samiux on 2009-06-16
[Did I set it up correctly?]("http://samiux.wordpress.com/2009/06/16/howto-security-enhanced-your-ubuntu-9-04-lamp-server-with-apparmor/")

Please comment and advice, thanks.

---

### Post by bodhi.zazen on 2009-06-16
> **samiux said:**
> [Did I set it up correctly?]("http://samiux.wordpress.com/2009/06/16/howto-security-enhanced-your-ubuntu-9-04-lamp-server-with-apparmor/")

Please comment and advice, thanks.

It is a fine start, keep going :)

As you become more familiar with the syntax I think you will find it is easy to use.

As this happens you will likely find you rely less on aa-logprof .

I highly suggest you back up a working profile before you edit it (outside of /etc/apparmor.d/).

In terms of paths / directories it depends on what you are serving with apache. Apache may need access to things such as ssl, php, perl, python, cgi, home directories (~/www), svn, etc, etc, etc.

This is one "problem" with apparmor, every users will need to derive his or her own profile and you need to first understand what is normal behavior for apache before you can confine it.

---

### Post by Jens_Li on 2009-07-11
There is no way to make a profile for all programs in a certain directory, is there?

E.g. I would like to block internet traffic for all programs, except for  those which have a profile that allows it?

Or limit the read/write rights for all programs which I run from directory ~/downloaded-files?


/jeli

---

### Post by jgoguen on 2009-07-11
Not easily.  You could make a set of common profile elements in one file, but you would still require one profile per program.  You could do it all in two files, like so:

/etc/apparmor.d/home.bin.common:
```
network inet stream,
network inet dgram,
network inet6 stream,
network inet6 dgram,
<other common allow lines>
```
The first 4 lines will allow network access. You apply this file in various profiles like below:

/etc/apparmor.d/home.bin.all
```
#include <tunables/global>
/home/jgoguen/bin/prog1 {
     #include <home.bin.common>
}

/home/jgoguen/bin/prog2 {
     #include <home.bin.common>
}

/usr/local/bin/prog3 {
     #include <home.bin.common>
}

```

Change the file names and paths appropriately.

---

### Post by q.dinar on 2009-08-08
hello
rookcifer:
> Anyone tried to profile the latest Firefox-3.0.11? I am not having any luck as there appears to be something wrong with how AppArmor is parsing logs. If I do
```
sudo aa-genprof firefox
```
and then attempt to "Scan" for changes (after I run firefox for a while), it will find some of the denial log messages but not all of them. Once I click on "Finished" and firefox goes into enforce mode, it won't open if I try to restart it. Thereafter, I ran:
```
sudo aa-logprof
```
but it finds no log messages. 
i could not make profile automatically and i have not asked about that, i make them "manually" checking log files after every change of profile, reloading it, restarting program, trying different things with program.

once i made profile for konqueror it asked for "w" permission in my home directory when i opened kde.org - default home bookmark of konqueror. i did not allow it. then after some time i tried to test it in test user, but it has not asked for that "w" permssion in home dir. any more.

how konqueror sees home directory content while "@{HOME}/ r, " is not in the profile nor it allowed other way?

---

### Post by Sporkman on 2009-09-09
Question: I'm working on an apparmor profile for apache2. It's currently in complain mode, and I get the following complaint (among others):

Sep  9 00:23:19 elcamino kernel: [118235.056951] type=1504 audit(1252470199.886:18401): operation="clone" task=22233 pid=22233 profile="null-complain-profile"

How do I set the profile to allow this "clone" operation (I assume this is when it forks..?)?

---

### Post by q.dinar on 2009-09-27
transmission requests for /etc/ r, and /mnt/sda1/user1/ r, /mnt/sda1/user1/ is home directory. i do not allow it. apparmor writes very many in syslog and messages. feature request, though i said that, say again: that should be able to turn off, something like /etc/ r nolog or other way, maybe in special nolog file.
why it asks for /etc/ ? why transmission needs it? i think it do not need it and it should "shut up" after several attempts. also home directory. both these looks like that transmission wants to spy what programs i have installed.

---

### Post by rookcifer on 2009-09-27
> **q.dinar said:**
> transmission requests for /etc/ r, and /mnt/sda1/user1/ r, /mnt/sda1/user1/ is home directory. i do not allow it. apparmor writes very many in syslog and messages. feature request, though i said that, say again: that should be able to turn off, something like /etc/ r nolog or other way, maybe in special nolog file.
why it asks for /etc/ ? why transmission needs it? i think it do not need it and it should "shut up" after several attempts. also home directory. both these looks like that transmission wants to spy what programs i have installed.

I have noticed some quirks like this too.  Sometimes when you deny something, it will still ask even though there is a clearly a "deny" line already in the profile.

Then there is the infamous error:

"Use of uninitialized value $profile in concatenation (.) or string at /usr/share/perl5/Immunix/SubDomain.pm line 4401."

I get this quite often.  Sometimes it happens so often I have to reboot.  There was a bug filed a long time ago, but nothing has been done about it yet.  This is not surprising as AppArmor does not seem to be under development anymore.  I suppose TOMOYO might be the way to go in the future.

---

### Post by bodhi.zazen on 2009-09-27
The other problem is that apparmor has actually been in development and as such it is very different between each version of Ubuntu.

Documentation of these changes is lagging and your best option is probably reading the man pages.

There are basically two approaches to apparmor. One is to generate a profile, run it in complain mode for some time ( a week ?) , generate logs, then assume such activity is "normal" and allow it all. Then change the profile to enforce and now you should only be logging abnormal activity.

The other approach is to limit access as much as possible. With this second approach you will get a ton of activity in your logs.

Personally I do a blend of the two. Allow full access to $HOME and restrict to the few files or directories such as ~/.ssh or ~/.Private.

Same with etc. Allow applications to at least read the "normal" config files they need, many of these things are in the abstractions. Restrict access to things such as passwd, shadow, and such.

You may also wish to restrict access to /sys and /proc and /etc/init.d/apparmor (restrict the ability of a profile to turn apparmor off).

I also restrict access to things in /sbin such as iptables.

It is much easier to allow all and generate a black list then deny all and allow a white list. Further you can copy-paste your black list between profiles.

Last, in 9.10 there are more and more default profiles. I use the defaults as much as possible.

---

### Post by q.dinar on 2009-09-28
[QUOTE=bodhi.zazen]Personally I do a blend of the two. Allow full access to $HOME and restrict ...[/QUOTE]
what is full access? @{HOME}/ and @{HOME}/**?
i said about that i denied even directory listing of home and etc. (programs can directly request subdirectory listing or file in subdirectory not looking directory listings of outer directories, of course...)
i do not know in apparmor how to allow all in area and then deny several things in it. i only know allow marks like r, w, k, l, ix, mrix, rix, rw - they all allow some paths over the all paths denied by default .

---

### Post by q.dinar on 2009-10-31
after upgrade to 9.04 once i see at start time some mysql complains of apparmor. now (on firefox upgrade) i have looked for mysql apparmor file and see that it has been disappeared. then i downloaded and looked at files of apparmor-profiles package and see that it also do not include mysql profile, even not in /usr/share/doc/apparmor-profiles/extras/ . why it disappeared and if it has disappeared how it complained? or i do not know where it is?

2009-12-07: found: usr.sbin.mysqld

---

### Post by rookcifer on 2009-10-31
> **q.dinar said:**
> after upgrade to 9.04 once i see at start time some mysql complains of apparmor. now (on firefox upgrade) i have looked for mysql apparmor file and see that it has been disappeared. then i downloaded and looked at files of apparmor-profiles package and see that it also do not include mysql profile, even not in /usr/share/doc/apparmor-profiles/extras/ . why it disappeared and if it has disappeared how it complained? or i do not know where it is?

AppArmor on Karmic has not been without its problems for me.  The "aa-logprof" command did not work on the BETA and profile generation was impossible because of it.  I filed a bug and one of the devs fixed it.  I assume that fix got pushed to the Final release.

At any rate, I don't know about your problem but I would file a bug about it (search for similar bugs first, of course).

---

### Post by keb on 2009-11-01
i recently upgraded to 9.10 and now i these messages in my log:
```
Nov  1 20:26:51 peace kernel: [   42.053509] type=1505 audit(1257125211.942:35): operation="profile_replace" pid=1134 name=/bin/ping
Nov  1 20:26:51 peace kernel: [   42.059470] type=1505 audit(1257125211.946:36): operation="profile_replace" pid=1135 name=/sbin/dhclient3
Nov  1 20:26:51 peace kernel: [   42.063092] type=1505 audit(1257125211.950:37): operation="profile_replace" pid=1135 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Nov  1 20:26:51 peace kernel: [   42.063675] type=1505 audit(1257125211.950:38): operation="profile_replace" pid=1135 name=/usr/lib/connman/scripts/dhclient-script
Nov  1 20:26:51 peace kernel: [   42.070677] type=1505 audit(1257125211.958:39): operation="profile_replace" pid=1136 name=/sbin/klogd
Nov  1 20:26:51 peace kernel: [   42.078618] type=1505 audit(1257125211.966:40): operation="profile_replace" pid=1137 name=/sbin/syslog-ng
Nov  1 20:26:51 peace kernel: [   42.085532] type=1505 audit(1257125211.974:41): operation="profile_replace" pid=1138 name=/sbin/syslogd
Nov  1 20:26:51 peace kernel: [   42.101399] type=1505 audit(1257125211.990:42): operation="profile_replace" pid=1139 name=/usr/bin/evince
Nov  1 20:26:52 peace kernel: [   42.119482] type=1505 audit(1257125212.006:43): operation="profile_replace" pid=1139 name=/usr/bin/evince-previewer
Nov  1 20:26:52 peace kernel: [   42.130401] type=1505 audit(1257125212.018:44): operation="profile_replace" pid=1139 name=/usr/bin/evince-thumbnailer
```

how do i get rid of them safely?

---

### Post by bodhi.zazen on 2009-11-02
> **keb said:**
> i recently upgraded to 9.10 and now i these messages in my log:
```
Nov  1 20:26:51 peace kernel: [   42.053509] type=1505 audit(1257125211.942:35): operation="profile_replace" pid=1134 name=/bin/ping
Nov  1 20:26:51 peace kernel: [   42.059470] type=1505 audit(1257125211.946:36): operation="profile_replace" pid=1135 name=/sbin/dhclient3
Nov  1 20:26:51 peace kernel: [   42.063092] type=1505 audit(1257125211.950:37): operation="profile_replace" pid=1135 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Nov  1 20:26:51 peace kernel: [   42.063675] type=1505 audit(1257125211.950:38): operation="profile_replace" pid=1135 name=/usr/lib/connman/scripts/dhclient-script
Nov  1 20:26:51 peace kernel: [   42.070677] type=1505 audit(1257125211.958:39): operation="profile_replace" pid=1136 name=/sbin/klogd
Nov  1 20:26:51 peace kernel: [   42.078618] type=1505 audit(1257125211.966:40): operation="profile_replace" pid=1137 name=/sbin/syslog-ng
Nov  1 20:26:51 peace kernel: [   42.085532] type=1505 audit(1257125211.974:41): operation="profile_replace" pid=1138 name=/sbin/syslogd
Nov  1 20:26:51 peace kernel: [   42.101399] type=1505 audit(1257125211.990:42): operation="profile_replace" pid=1139 name=/usr/bin/evince
Nov  1 20:26:52 peace kernel: [   42.119482] type=1505 audit(1257125212.006:43): operation="profile_replace" pid=1139 name=/usr/bin/evince-previewer
Nov  1 20:26:52 peace kernel: [   42.130401] type=1505 audit(1257125212.018:44): operation="profile_replace" pid=1139 name=/usr/bin/evince-thumbnailer
```how do i get rid of them safely?

Those messages are normal, they are telling you these profiles are loaded.

---

### Post by q.dinar on 2009-12-07
now i see mysql profile, may be that time i just have not noticed it thinking that it should start with "usr.bin." . but it is "usr.sbin.mysqld".

i have successfully loaded a file in table with "LOAD DATA LOCAL INFILE ..." command, as in [http://dev.mysql.com/doc/refman/5.1/en/loading-tables.html](http://dev.mysql.com/doc/refman/5.1/en/loading-tables.html) , from ~/doc/tmp/msql.txt , which is not allowed in apparmor profile for mysqld, i loaded that from mysql command, so "mysql" does not use "mysqld" when loads data in table? i add after a minute: probably they share some binary libraries.

---

### Post by q.dinar on 2009-12-21
hello . i have installed extra profiles, they are installed in /usr-share/doc/apparmor..... , i have copied some of them to /etc/apparmor.d/ .
when i runned netstat program these messages appeared:
Dec 21 08:54:06 dinar-desktop kernel: [ 2393.374180] type=1503 audit(1261374846.637:173): operation="open" pid=3033 parent=2363 profile="/bin/netstat" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/proc/1/fd/"
Dec 21 08:54:06 dinar-desktop kernel: [ 2393.374225] type=1503 audit(1261374846.637:174): operation="open" pid=3033 parent=2363 profile="/bin/netstat" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/proc/2/fd/"
...
though there is
@{PROC}/[0-9]*/fd r,
in /etc/apparmor.d/bin.netstat
.

and:
Dec 21 08:36:49 dinar-desktop kernel: [ 1356.514076] type=1503 audit(1261373809.777:172): operation="open" pid=2710 parent=2709 profile="/etc/cron.daily/logrotate" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/etc/logrotate.d/"
though there was
/etc/logrotate.d r,
in /etc/apparmor.d/etc.cron.daily.logrotate .
i have now added
/etc/logrotate.d/ r,
to it and will look what will happen during logrotate runned by cron.

also there is some packet for apache change hat, now there is usr.lib.apache2.mpm-prefork.apache2 profile, is it possible to make change hat to "worker" apache?
2009-12-22: and also there is another profile called like /usr/sbin/httpd... , it works with some edition.

---

### Post by q.dinar on 2009-12-21
i used netstat this way:
sudo netstat -tunp
and now i have added to its profile:
  @{PROC}/[0-9]*/fd/ r,
and it says other messages now, so "trailing slash" is important here. and i hope that adding last slash also fixed that error of logrotate.

2009-12-25 18:39 utc+3 : may be these profiles are written not by mistake but they are not edited since older version of apparmor, there is about changes in path writings: [http://en.opensuse.org/AppArmor/Changes_AppArmor_2_1](http://en.opensuse.org/AppArmor/Changes_AppArmor_2_1) .

---

### Post by q.dinar on 2009-12-21
hello. why tcpdump needs "usb"? and is "usb" "universal serial bus"?
it asked at my computer:
Dec 21 14:53:16 dinar-desktop kernel: [ 4185.081498] type=1503 audit(1261396396.345:195): operation="open" pid=2963 parent=2185 profile="/usr/sbin/tcpdump" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/dev/bus/usb/"
also there is in its apparmor profile:
  @{PROC}/bus/usb/ r,
  @{PROC}/bus/usb/** r,
now i have added
/dev/bus/usb/ r,
but i think i will comment it out.

now it has asked also for /dev/usbmon1 , /dev/usbmon2, /dev/usbmon3 .

may be that is for usb adsl modem ? but mine is not that.


and i have question about installing programs like skype and google earth. if i open their deb file with archive manager (file-roller...?) and check files in control.tar.gz and data.tar.gz ? as i remember and know there is none installer script in skype package and only one binary file. if there is installer script in control.tar.gz, i should check what they do looking at their code content, i think.

i runned some programs as root by mistake(?) sometimes even not blocked up with apparmor. now i have deleted /root/ from tunables/home and suggest to you. now i have runned firefox 3.5 with apparmor profile ant /root/ deleted as root, it could not run, i have checked profile, i see it cannot do much, but do you know what it can do so if runs as root.
unfortunately once i have runned open office as root by mistake in previous installation. now only firefox blocked. now i am going to open files clicking right button first and suggest that to you when working with gksudo nautilus.

---

### Post by q.dinar on 2009-12-21
another thing about tcpdump:
sudo tcpdump -qn > /var/log/tcpdump.log
says:
bash: /var/log/tcpdump.log: Permission denied
and nothing is written by apparmor in log files.

by the way, why syslog and messages and kern.log contents are partially dublicated? how to make every of log lines written only in one log file?

---

### Post by cariboo on 2009-12-21
You can use the edit button in the lower right of a post to add to it, instead of creating so many posts.

---

### Post by q.dinar on 2009-12-21
hello.
i am now trying to setup worker mpm apache with apparmor. i have renamed apparmor profile for apache to
usr.lib.apache2.mpm-worker.apache2
.
now on
sudo /etc/init.d/apache2 reload
there are:
in apache error log:
[Mon Dec 21 23:21:36 2009] [notice] SIGUSR1 received.  Doing graceful restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Mon Dec 21 23:21:36 2009] [notice] Apache/2.2.12 (Ubuntu) configured -- resuming normal operations
[Mon Dec 21 23:21:36 2009] [error] Failed to change_hat to 'HANDLING_UNTRUSTED_INPUT'
[Mon Dec 21 23:21:36 2009] [error] Failed to change_hat to 'HANDLING_UNTRUSTED_INPUT'
>2009-12-24 8:57 utc+3 : there were dublicated profiles ...<

in syslog:
Dec 21 23:21:36 dinar-desktop kernel: [ 4228.280778] type=1503 audit(1261426896.545:356): operation="change_hat" info="unconfined" error=-1 pid=5670
Dec 21 23:21:36 dinar-desktop kernel: [ 4228.280828] type=1503 audit(1261426896.545:357): operation="change_hat" info="unconfined" error=-1 pid=5670
Dec 21 23:21:36 dinar-desktop kernel: [ 4228.287792] type=1503 audit(1261426896.549:358): operation="change_hat" info="unconfined" error=-1 pid=5698
Dec 21 23:21:36 dinar-desktop kernel: [ 4228.287844] type=1503 audit(1261426896.549:359): operation="change_hat" info="unconfined" error=-1 pid=5698

23:55 utc+3: may be there is bug: [http://forge.novell.com/pipermail/apparmor-general/2007-January/000233.html](http://forge.novell.com/pipermail/apparmor-general/2007-January/000233.html) .

2009-12-22 9:40 utc+3 : somehow it works now after some changes of apache profile and "/etc/init.d/apache2 stop" and "/etc/init.d/apache2 start"s and "a2dismod apparmor" and "a2enmod apparmor". 19:15 utc+3 : and after restart of OS.

---

### Post by q.dinar on 2009-12-22
empathy says "Failed to execute child process "firefox" (No such file or directory)" when i try to open a url in chat room. there is in empathy profile:
/usr/lib/firefox-3.5.*/firefox.sh Pxr,
and no log, so i do not know what is denied.


why there is in firefox profile (that is in ubuntu 9.10):
/usr/bin/evince PUxr,
? what is PUxr? is it correct?

---

### Post by q.dinar on 2009-12-22
hello. i have installed php so that apache uses it through(?) fcgid. now i test apparmor. i test in default vhost, it is in /var/www/ , i applied a "hat" to it - with AAHatName directive in directory tag in virtualhost tag in apache's "default" site configuration file, but i see that hat works only for html files. php is not blocked up, it can read any files. i have made "usr.bin.php5-cgi" profile but it does not work, may be name of it is not correct - i am trying to block up wrong binary program?
how to create profile for php ?
may be i will try apparmor's tool for creating profile...

---

### Post by jgoguen on 2009-12-22
> **q.dinar said:**
> hello . i have installed extra profiles, they are installed in /usr-share/doc/apparmor..... , i have copied some of them to /etc/apparmor.d/ .
when i runned netstat program these messages appeared:
Dec 21 08:54:06 dinar-desktop kernel: [ 2393.374180] type=1503 audit(1261374846.637:173): operation="open" pid=3033 parent=2363 profile="/bin/netstat" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/proc/1/fd/"
Dec 21 08:54:06 dinar-desktop kernel: [ 2393.374225] type=1503 audit(1261374846.637:174): operation="open" pid=3033 parent=2363 profile="/bin/netstat" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/proc/2/fd/"
...
though there is
@{PROC}/[0-9]*/fd r,
in /etc/apparmor.d/bin.netstat
> **q.dinar said:**
>  Dec 21 08:36:49 dinar-desktop kernel: [ 1356.514076] type=1503 audit(1261373809.777:172): operation="open" pid=2710 parent=2709 profile="/etc/cron.daily/logrotate" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/etc/logrotate.d/"
though there was
/etc/logrotate.d r,
in /etc/apparmor.d/etc.cron.daily.logrotate .
i have now added
/etc/logrotate.d/ r,
to it and will look what will happen during logrotate runned by cron.
> **q.dinar said:**
> i used netstat this way:
sudo netstat -tunp
and now i have added to its profile:
  @{PROC}/[0-9]*/fd/ r,
and it says other messages now, so "trailing slash" is important here. and i hope that adding last slash also fixed that error of logrotate.
This is the difference with that final slash :)  As you've noticed, adding it is necessary to allow reading not only the directory itself but also what is in that directory.  I suspect that with the final slash added (assuming you've reloaded the profile) you won't see this particular error from these profiles.  Also assuming of course that UNIX permissions also allow what you're trying to do ;)

> **q.dinar said:**
> hello. why tcpdump needs "usb"? and is "usb" "universal serial bus"?
it asked at my computer:
Dec 21 14:53:16 dinar-desktop kernel: [ 4185.081498] type=1503 audit(1261396396.345:195): operation="open" pid=2963 parent=2185 profile="/usr/sbin/tcpdump" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/dev/bus/usb/"
also there is in its apparmor profile:
  @{PROC}/bus/usb/ r,
  @{PROC}/bus/usb/** r,
now i have added
/dev/bus/usb/ r,
but i think i will comment it out.

now it has asked also for /dev/usbmon1 , /dev/usbmon2, /dev/usbmon3 .

may be that is for usb adsl modem ? but mine is not that.
As you've noticed in previous posts, sometimes access is requested that isn't actually required.  As before, my general advice is to grant access you know is needed if the program isn't working properly.  If the program works properly with the access you've given it, apply the principle of "if it's not broken, don't fix it" :)  I believe you're right though, I think the USB-related access requests are for USB modems.  Since you don't have one, you can safely ignore these messages

 > **q.dinar said:**
> and i have question about installing programs like skype and google earth. if i open their deb file with archive manager (file-roller...?) and check files in control.tar.gz and data.tar.gz ? as i remember and know there is none installer script in skype package and only one binary file. if there is installer script in control.tar.gz, i should check what they do looking at their code content, i think.
That is completely up to you.  If you want to open the package up and check the installer script, go right ahead.  But, if you're going to do that because you don't trust it, I would question the use of Skype, which is a closed program that you can't inspect in any way, more than I would question the installer script :)

 > **q.dinar said:**
>  i runned some programs as root by mistake(?) sometimes even not blocked up with apparmor. now i have deleted /root/ from tunables/home and suggest to you. now i have runned firefox 3.5 with apparmor profile ant /root/ deleted as root, it could not run, i have checked profile, i see it cannot do much, but do you know what it can do so if runs as root.
unfortunately once i have runned open office as root by mistake in previous installation. now only firefox blocked. now i am going to open files clicking right button first and suggest that to you when working with gksudo nautilus.
I'm not quite sure what you're asking (or saying?) here.  Could you explain it more and I'll see if I can help?

> **q.dinar said:**
> another thing about tcpdump:
sudo tcpdump -qn > /var/log/tcpdump.log
says:
bash: /var/log/tcpdump.log: Permission denied
and nothing is written by apparmor in log files.
That's because you're being denied by UNIX permissions.  Here's what happens with that command:

[LIST]
[*]The shell attempts to create the file /var/log/tcpdump.log
[*]The shell attempts to open the file /var/log/tcpdump.log for writing, deleting the existing contents (if any)
[*]The shell executes tcpdump, setting its stdout file stream to the stream opened in the last step
[/LIST]

In your case, step 1 fails so nothing else happens.  You should either redirect output to a file somewhere you can write, or use "sudo tcpdump -qn | sudo tee /var/log/tcpdump.log" to get the same result as what I believe you intend based on the command you tried.

> **q.dinar said:**
>  by the way, why syslog and messages and kern.log contents are partially dublicated? how to make every of log lines written only in one log file?
That would require a lot of playing around with the syslog configuration files.

> **q.dinar said:**
> empathy says "Failed to execute child process "firefox" (No such file or directory)" when i try to open a url in chat room. there is in empathy profile:
/usr/lib/firefox-3.5.*/firefox.sh Pxr,
and no log, so i do not know what is denied.
What is denied is executing firefox.  The profile allows executing firefox.sh, but Empathy is trying to execute firefox.  If you change the profile accordingly, reload the profile, and restart Empathy it should work fine.

> **q.dinar said:**
>  why there is in firefox profile (that is in ubuntu 9.10):
/usr/bin/evince PUxr,
? what is PUxr? is it correct?
Evince is allowed since that's what is used to read PDF files.  PUxr is indeed correct, it's a new sequence for Karmic.  "PUx" means "execute this program with an AppArmor profile if one exists, or execute it unconfined if no profile exists".

> **q.dinar said:**
> hello. i have installed php so that apache uses it through(?) fcgid. now i test apparmor. i test in default vhost, it is in /var/www/ , i applied a "hat" to it - with AAHatName directive in directory tag in virtualhost tag in apache's "default" site configuration file, but i see that hat works only for html files. php is not blocked up, it can read any files. i have made "usr.bin.php5-cgi" profile but it does not work, may be name of it is not correct - i am trying to block up wrong binary program?
how to create profile for php ?
may be i will try apparmor's tool for creating profile...
I think we will need to see the full profiles for all relevant programs to be able to best help here.  If you would rather not post profiles, please describe what applications in this scenario are confined, which are executed with and without profiles, and what executable path you specify in the profiles.

---

### Post by q.dinar on 2009-12-23
hello. i have written both firefox and firefox sh in empathy profile, it does not work, it even did not ask for firefox through apparmor, there were only ...sh.
>14:47 utc+3 : now i have written ..sh Ux, and it works<

i think if closed source binary is blocked up by apparmor it is quite safe, only thing to check is install scripts, because they are not blocked up by apparmor, but good that they are open-source. can they be closed source (in normal deb file)?

i asked about running gksudo nautilus and double-clicking in it files like ...html, ...doc and running so big programs as root.

thank you.

i am going to publish my old and new profiles.

after restart again apache complained as was before yesterday:
Dec 23 10:06:53 dinar-desktop kernel: [ 2359.691871] type=1503 audit(1261552013.953:459): operation="open" pid=5816 parent=5668 profile="/usr/lib/apache2/mpm-worker/apache2//HANDLING_UNTRUSTED_INPUT" requested_mask="::r" denied_mask="::r" fsuid=33 ouid=0 name="/etc/ld.so.cache"
Dec 23 10:06:53 dinar-desktop kernel: [ 2359.692017] type=1503 audit(1261552013.953:460): operation="open" pid=5816 parent=5668 profile="/usr/lib/apache2/mpm-worker/apache2//HANDLING_UNTRUSTED_INPUT" requested_mask="::r" denied_mask="::r" fsuid=33 ouid=0 name="/lib/libgcc_s.so.1"
Dec 23 10:06:53 dinar-desktop kernel: [ 2359.713426] type=1503 audit(1261552013.977:461): operation="open" pid=5816 parent=5668 profile="/usr/lib/apache2/mpm-worker/apache2//HANDLING_UNTRUSTED_INPUT" requested_mask="::rw" denied_mask="::rw" fsuid=33 ouid=0 name="/dev/tty"
this is many times. apache profile reload has helped, will look what will happen after restart.
>14:47 utc+3 : i think this is solved now, there were 2 apache profiles, one with incorrect file name thinking it will not affect anything on because there is no such file but i should edit file name in content of profile file.<

11:44 utc+3 : when HANDLING_UNTRUSTED_INPUT is used and when DEFAULT_URI is used and when main profile is used? 2009-12-24 8:54 utc+3 : [http://www.mpipks-dresden.mpg.de/~mueller/docs/suse10.3/opensuse-manual_de/manual/bx5dh07.html](http://www.mpipks-dresden.mpg.de/~mueller/docs/suse10.3/opensuse-manual_de/manual/bx5dh07.html) , [http://manpages.ubuntu.com/manpages/hardy/man8/mod_apparmor.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/mod_apparmor.8.html) , [http://www.novell.com/documentation/apparmor/book_apparmor21_admin/?page=/documentation/apparmor/book_apparmor21_admin/data/bx5dh07.html](http://www.novell.com/documentation/apparmor/book_apparmor21_admin/?page=/documentation/apparmor/book_apparmor21_admin/data/bx5dh07.html) .

11:46 utc+3: i think i know why php is not blocked: because
  / rw,
  /** mrwlkix,
is in main profile and in HANDLING_UNTRUSTED_INPUT and in DEFAULT_URI. 13:34 utc+3: now i think it is not because this.

---

### Post by q.dinar on 2009-12-23
many
```
Dec 23 10:06:53 dinar-desktop kernel: [ 2359.691871] type=1503 audit(1261552013.953:459): operation="open" pid=5816 parent=5668 profile="/usr/lib/apache2/mpm-worker/apache2//HANDLING_UNTRUSTED_INPUT" requested_mask="::r" denied_mask="::r" fsuid=33 ouid=0 name="/etc/ld.so.cache"
Dec 23 10:06:53 dinar-desktop kernel: [ 2359.692017] type=1503 audit(1261552013.953:460): operation="open" pid=5816 parent=5668 profile="/usr/lib/apache2/mpm-worker/apache2//HANDLING_UNTRUSTED_INPUT" requested_mask="::r" denied_mask="::r" fsuid=33 ouid=0 name="/lib/libgcc_s.so.1"
Dec 23 10:06:53 dinar-desktop kernel: [ 2359.713426] type=1503 audit(1261552013.977:461): operation="open" pid=5816 parent=5668 profile="/usr/lib/apache2/mpm-worker/apache2//HANDLING_UNTRUSTED_INPUT" requested_mask="::rw" denied_mask="::rw" fsuid=33 ouid=0 name="/dev/tty"
```
again after restart.>14:47 utc+3 : i think this is solved now, there were 2 apache profiles, one with incorrect file name thinking it will not affect anything on because there is no such file but i should edit file name in content of profile file.<


another strange thing:
```
sudo  apparmor_parser -R /etc/apparmor.d/usr.lib.apache2.mpm-worker.apache2
Ignoring: '/etc/apparmor.d/apache2.d/123php~'
apparmor_parser: Unable to remove "123php".  Profile doesn't exist
```
though that file exist, and there is also phpsysinfo hat profile file, no error message about it, only about 123php. i made 123php to apply to default virtualost.

some thing may be related to that with apache at start: on system boot up(?) time there are many lines about profile load in syslog but none among them about apache.

---

### Post by jgoguen on 2009-12-23
> **q.dinar said:**
> hello. i have written both firefox and firefox sh in empathy profile, it does not work, it even did not ask for firefox through apparmor, there were only ...sh.
14:47 utc+3 : now i have written ..sh Ux, and it works
If it works with Ux, what that means is that either the Empathy or the Firefox profile was defined incorrectly (possibly both) and now Firefox runs unconfined when started from Empathy.  I don't know what I was thinking suggesting to have firefox in the profile when it's just a symlink pointing to a firefox.sh :)  Try making your Empathy rule "/usr/lib/firefox-*/firefox.sh Px" (or use the shiny new PUx to avoid issues) and make sure your Firefox profile is defined for the current Firefox install.  Currently, in Karmic at least, that's /usr/lib/firefox-3.5.6/firefox.sh.

> **q.dinar said:**
> i think if closed source binary is blocked up by apparmor it is quite safe, only thing to check is install scripts, because they are not blocked up by apparmor, but good that they are open-source. can they be closed source (in normal deb file)?
I believe the install scripts must be scripts, but they aren't required.  I've never tried having anything other than a shell script for a package install.

---

### Post by jgoguen on 2009-12-23
> **q.dinar said:**
> ```
sudo  apparmor_parser -R /etc/apparmor.d/usr.lib.apache2.mpm-worker.apache2
Ignoring: '/etc/apparmor.d/apache2.d/123php~'
apparmor_parser: Unable to remove "123php".  Profile doesn't exist
```though that file exist, and there is also phpsysinfo hat profile file, no error message about it, only about 123php. i made 123php to apply to default virtualost.
The message about the profile not existing doesn't mean there's no file with that name, it means there's no profile loaded with that name.  The tilde (~) at the end of the name typically indicates a backup file, so check to see that there is only one file that defines the profile.  If you have both 123php and 123php~ and they both define the same profile, delete 123php~ and try again.

---

### Post by q.dinar on 2009-12-23
[QUOTE=jgoguen]...
If it works with Ux, what that means is that either the Empathy or the Firefox profile was defined incorrectly (possibly both) and now Firefox runs unconfined when started from Empathy. I don't know what I was thinking suggesting to have firefox in the profile when it's just a symlink pointing to a firefox.sh Try making your Empathy rule "/usr/lib/firefox-*/firefox.sh Px" (or use the shiny new PUx to avoid issues) and make sure your Firefox profile is defined for the current Firefox install. Currently, in Karmic at least, that's /usr/lib/firefox-3.5.6/firefox.sh.[/QUOTE]
no, here at ubuntu 9.10 i have profile for firefox:
```
/usr/lib/firefox-3.5.*/firefox {
```
now firefox runs confined when opened from empathy, because firefox.sh runs it with Px. it did not work just because i set ...sh Px but there were not any profile for ...sh .

---

### Post by rookcifer on 2009-12-23
q.dinar, 

On a related note, it would be better if you installed auditd for logging.  This is recommended for AppArmor (as some of the devs themselves told me).

---

### Post by q.dinar on 2009-12-23
hello.
i have searched in web some about auditd, i do not want to install it, i think it is extra problem for me, i do not need it, syslog is enough for me. if you think that i need it please(?) say what it gives(?).

now i have started from empty apache profile and all things are understandable.
by the way: /etc/init.d/apparmor reload and restart, as i know, reload all profiles that are already turned on, just deleting profile and restart do not help as i know, if i am not mistaken, need to delete with apparmor_parser -R or disable by making link at disable directory. so may be would be good if there is command to load profiles as they are in /apparmor.d/ .
now i have moved 2 apache profiles, which are needed only to compare with them, to "disable" directory though it is for setting there links to profiles that should be disabled , i moved because moving with mouse is easier in nautilus. is there some key holding that i can directly make link in place other than folder of file? that would be also good to make links to files like /mnt/sdb1 because need root account to create link in /mnt/ .

---

### Post by q.dinar on 2009-12-24
i attach /etc/apparmor.d content as it was when i have installed new ubuntu 9.10 , there are profiles that worked with ubuntu 9.04 and ubuntu 8.10 .
i have attached them in "share your apparmor profiles" thread: [http://ubuntuforums.org/showthread.php?p=8551897#post8551897](http://ubuntuforums.org/showthread.php?p=8551897#post8551897) .

---

### Post by q.dinar on 2009-12-24
i have just installed ejabberd to ubuntu 9.10 i386 from its repository, have not configured any files of it, just started to make apparmor profile. last installation i made profile for /usr/sbin/ejabberd , this time i make for /etc/init.d/ejabberd . because if you look at system monitor there is beam and epmd proccesses running for ejabberd and no "ejabberd" process and ejabberd starts from /etc/init.d/ejabberd , so i make profile for it to control everything that it can start. and there is /usr/sbin/ejabberdctl is also started sometimes.
   to restart ejabberd use this commands: sudo /etc/init.d/ejabberd stop and sometimes sudo killall epmd - look whether it is running in system monitor then reload profile with sudo  apparmor_parser -r /etc/apparmor.d/etc.init.d.ejabberd then start ejabberd with sudo /etc/init.d/ejabberd start.
   now i have apparmor profile so that no messages of apparmor about ejabberd.
   after i have this profile and stopped ejabberd, epmd and beam processes are left running so stop them with sudo killall epmd and sudo killall beam. i say to kill them because in previous installation without killing them ejabberd could not start again and if do not kill them i think new, modified apparmor profile will not apply properly or not apply at all.
   this current ejabberd apparmor profile wich works with fresh installed ejabberd of ubuntu 9.10 :
```
#include <tunables/global>
/etc/init.d/ejabberd {
#/etc/ld.so.cache r,
#/lib/tls/i686/cmov/libc-2.10.1.so r,
#/lib/libc-2.10.1.so r,
#include <abstractions/base>
/etc/init.d/ejabberd r,
/etc/default/ejabberd r,
/bin/su ix,
capability dac_override,
capability dac_read_search,
/usr/bin/expr ix,
/bin/sleep ix,
/var/run/utmp rk,
#include <abstractions/nameservice>
/etc/login.defs r,
/etc/pam.d/* r,
/lib/security/** mr,
/etc/shells r,
/proc/filesystems r,
capability setgid,
/etc/shadow r,
/etc/security/** r,
capability setuid,
/etc/environment r,
/etc/default/locale r,
/bin/dash ix,
/usr/sbin/ejabberdctl ixr,
/usr/sbin/ejabberd ixr,
/bin/date ix,
/usr/lib/erlang/bin/erl ix,
/bin/sed ix,
/usr/lib/erlang/** ix,
/sys/devices/system/cpu/ r,
/var/lib/ejabberd/** r,
@{HOME}/erl_crash.dump wr,
/sys/devices/system/cpu/** r,
/etc/ejabberd/** r,
/var/lib/ejabberd/ r,
/var/log/ejabberd/** wr,
/var/lib/ejabberd/** wr,
/usr/lib/ejabberd/** mr,
}
```
why does it need "su" ?  how can it use it? it is not only to became root? why it needs "shadow"? not only root can read it? ah i myself run it - /etc/init.d/ejabberd as root!
11:01 utc+3: i think making profile for /etc/init.d/ejabberd is not correct , because it allows things like shadow which normal process that does not run as root cannot and should not use , because if it could it could use it to know out password. for what do you suggest create profiles? may be better for /usr/sbin/ejabberd and /usr/sbin/ejabberdctl ... may be also possible for epmd and beam ...

---

### Post by q.dinar on 2009-12-24
now i have:
```
#include <tunables/global>
/etc/init.d/ejabberd {
#/etc/ld.so.cache r,
#/lib/tls/i686/cmov/libc-2.10.1.so r,
#/lib/libc-2.10.1.so r,
#include <abstractions/base>
/etc/init.d/ejabberd r,
/etc/default/ejabberd r,
/bin/su ix,
capability dac_override,
capability dac_read_search,
/usr/bin/expr ix,
/bin/sleep ix,
/var/run/utmp rk,
#include <abstractions/nameservice>
/etc/login.defs r,
/etc/pam.d/* r,
/lib/security/** mr,
/etc/shells r,
/proc/filesystems r,
capability setgid,
/etc/shadow r,
/etc/security/** r,
capability setuid,
/etc/environment r,
/etc/default/locale r,
/bin/dash ix,
#/usr/sbin/ejabberdctl ixr,
#/usr/sbin/ejabberd ixr,
/usr/sbin/ejabberdctl Px,
/usr/sbin/ejabberd Px,
#/bin/date ix,
#/usr/lib/erlang/bin/erl ix,
#/bin/sed ix,
#/usr/lib/erlang/** ix,
#/sys/devices/system/cpu/ r,
#@{HOME}/erl_crash.dump wr,
#/sys/devices/system/cpu/** r,
#/etc/ejabberd/** r,
#/var/lib/ejabberd/ r,
#/var/log/ejabberd/** wr,
#/var/lib/ejabberd/** wr,
#/usr/lib/ejabberd/** mr,
}
```
and
```
#include <tunables/global>
/usr/sbin/ejabberd {
#include <abstractions/base>
/usr/sbin/ejabberd r,
/etc/default/ejabberd r,
/usr/lib/erlang/bin/erl ix,
/bin/sed ix,
/usr/lib/erlang/** ix,
/proc/filesystems r,
/sys/devices/system/cpu/ r,
/bin/dash ix,
/var/log/ejabberd/** wr,
/var/lib/ejabberd/** wr,
/sys/devices/system/cpu/** r,
#include <abstractions/nameservice>
/etc/ejabberd/** r,
/var/lib/ejabberd/ r,
/usr/lib/ejabberd/** mr,
}
```
and
```
#include <tunables/global>
/usr/sbin/ejabberdctl {
#include <abstractions/base>
/usr/sbin/ejabberdctl r,
/etc/default/ejabberd r,
/bin/date ix,
/usr/lib/erlang/bin/erl ix,
/bin/sed ix,
/usr/lib/erlang/** ix,
/proc/filesystems r,
/sys/devices/system/cpu/ r,
/bin/dash ix,
#include <abstractions/nameservice>
/sys/devices/system/cpu/** r,
@{HOME}/erl_crash.dump wr,
/var/lib/ejabberd/** wr,
}
```

---

### Post by jgoguen on 2009-12-24
First, if no one has answered you please edit your post so that it has the most up-to-date information.  Unfortunately, I don't know how much more help I can be since I'm not familiar with ejabberd :(

The "su" command isn't just used to switch to root.  Think of "su" as short for "switch user", which is exactly what it lets you do.  It just happens that if you don't give it a user to change to, it defaults to root.  If I say "su joe", I will be asked for the password for user "joe" and I will get a shell open as "joe", not as root.  It's possible that ejabberd uses su to change to a lower-privilege user, or to run part of itself with lower privileges, but I would think the developers would use the system setuid() and setgid() calls to do that.  I can't think of any reason for it to need access to /etc/shadow though.

Do you have any problems with the set of three profiles you posted?  If they work fine, you should post them in the thread for sharing profiles rather than here.  Keep up the good work learning AppArmor :)

---

### Post by BigCityCat on 2009-12-24
I really hate to be a lazy *** but is there a way I can just import a firefox profile that is already set up for me. lol

---

### Post by rookcifer on 2009-12-25
> **BigCityCat said:**
> I really hate to be a lazy *** but is there a way I can just import a firefox profile that is already set up for me. lol

There is already a firefox profile (9.10 only), it just needs to be enabled.  If you're using 9.10 all you need to do is:

```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox-3.5
```

And then restart apparmor:

```
sudo /etc/init.d/apparmor restart
```

This firefox profile should work well most of the time, but since it isn't possible for one profile to serve all purposes, there might be instances where you might find it blocks normal behavior.  For that you will need to check the logs in syslog to see what it's blocking and adjust it accordingly.

---

### Post by q.dinar on 2009-12-25
to #87 : and restart firefox, i think, if it is not changed in new apparmor.
10:10 utc+3 : to [#70](http://ubuntuforums.org/showpost.php?p=8537449&postcount=70): i had known about that...
to #85 "... If they work fine, you should post them in the thread for sharing profiles rather than here. ..." - i have not used this much enough yet now, even has not registered a user.

14:52 utc+3 : again adding to #87 : and may be you want to deny full access to your home folder and /mnt/ and /srv/ content , for that you should edit the profile.

---

### Post by q.dinar on 2009-12-25
hello.
(some tips/suggestions)
when test apache do not just "sudo /etc/init.d/apache2 reload" but "sudo /etc/init.d/apache2 restart" or "... stop" and then "...start", because if you just reload, i think >2010-02-01: even maybe ... (unbelievable..) < some processes of it are left running and no apparmor profile apply to them, and you do not see in syslog what they used.
i have forgotten second thing that i wanted to write.
2009-12-25 23:43 utc+3 : i have remembered:
what do you think about blocking up pppd?

---

### Post by BigCityCat on 2009-12-25
> **rookcifer said:**
> There is already a firefox profile (9.10 only), it just needs to be enabled.  If you're using 9.10 all you need to do is:

```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox-3.5
```

And then restart apparmor:

```
sudo /etc/init.d/apparmor restart
```

This firefox profile should work well most of the time, but since it isn't possible for one profile to serve all purposes, there might be instances where you might find it blocks normal behavior.  For that you will need to check the logs in syslog to see what it's blocking and adjust it accordingly.

I appreciate that, thank you.

---

### Post by Cypher1101 on 2009-12-27
I don't really understand how the options logprof is giving me relate to the permissions outlined in the sticky and other documentation. Actually, most of the documentation I've been through makes almost no reference to logprof at all. Here's an example:
```
Reading log entries from /var/log/messages.
Updating AppArmor profiles in /etc/apparmor.d.

Profile:  /usr/lib/firefox-3.0.16/firefox.sh
Execute:  /usr/bin/basename
Severity: unknown


(I)nherit / (P)rofile / (C)hild / (N)ame / (U)nconfined / (X)ix / (D)eny / Abo(r)t / (F)inish
Use of uninitialized value $profile in concatenation (.) or string at /usr/share/perl5/Immunix/SubDomain.pm line 4401.
Complain-mode changes:

Profile:  /usr/bin/basename
Path:     /usr/bin/basename
Mode:     r
Severity: unknown


 [1 - /usr/bin/basename]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /usr/bin/basename r to profile.

Profile:  /usr/lib/firefox-3.0.16/firefox.sh
Path:     /bin/dash
Old Mode: ix
New Mode: rix
Severity: unknown


 [1 - /bin/dash]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /bin/dash rix to profile.

Profile:  /usr/lib/firefox-3.0.16/firefox.sh
Path:     /dev/ati/card0
Mode:     rw
Severity: unknown


 [1 - /dev/ati/card0]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /dev/ati/card0 rw to profile.

Profile:  /usr/lib/firefox-3.0.16/firefox.sh
Path:     /etc/mailcap
Mode:     r
Severity: unknown


 [1 - /etc/mailcap]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /etc/mailcap r to profile.

Profile:  /usr/lib/firefox-3.0.16/firefox.sh
Path:     /etc/mime.types
Mode:     r
Severity: unknown


 [1 - /etc/mime.types]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /etc/mime.types r to profile.

Profile:  /usr/lib/firefox-3.0.16/firefox.sh
Path:     /home/cypher/.Xauthority
Mode:     owner r
Severity: 4

  1 - /home/cypher/.Xauthority 
 [2 - /home/*/.Xauthority]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts



```My Firefox profile is basically a stub, so i should be getting complaints on everything. I've noticed that most people give firefox rix access to basename. That's read and inherit, correct? So I hit I and it looks like that was the right option, but what do the others do? I'm really having trouble finding any documentation on the usage of logprof.

Oh, and I'm still on 9.04

---

### Post by bodhi.zazen on 2009-12-27
logprof is a command that will read the logs for you and give you suggestions on how to fix the problem or denials you are having.

You will crawl into some of the darkes corners of your system learning to use apparmor and logprof.

The problem with logprof is that, especially in the beginning, you do not have enough experience to know what it is telling you.

Stay with it, it does get easier.

Actually, firefox needs a profile in a big way, but it is NOT the best to start with. As you can see, firefox touches a ton of system and $HOME files 

For example, one starts with firefox, but it is not long before one wants to open documents with say OOO, or music, or flash, or open a pdf in evence, and on an on ...

There is a profile available for firefox in 9.10 , you can start there.

You may also wish to look at what others are doing. I already suggested Zenix earlier today, you can also look at some aa repositories or google search aa profiles =)

[http://bodhizazen.net/aa-profiles/](http://bodhizazen.net/aa-profiles/)

---

### Post by q.dinar on 2009-12-28
may be i have found a bug of apparmor. i have in apparmor.d profiles for postfix's files, probably they are from apparmor-profiles package, may be from /usr/share/doc/apparmor-profiles/extra/ . and i have gone to install postfix. but it did not install without error messages. some apparmor logs appeared during install, i have fixed for them profiles and uninstall and reinstall postfix, then again fixed profiles and such one or several more times but after that even though there were not any log , it could not be installed without errors. only when i have set one and then also other profile to complain mode it has been installed without error messages. bug is that apparmor blocked up programs runned by post-install script and post install script returned error code but apparmor has not logged anything about that.

2009-12-29 21:36 utc+3 : [https://bugs.launchpad.net/apparmor/+bug/501401](https://bugs.launchpad.net/apparmor/+bug/501401)

---

### Post by rookcifer on 2009-12-28
> **bodhi.zazen said:**
> You may also wish to look at what others are doing. I already suggested Zenix earlier today, you can also look at some aa repositories or google search aa profiles =)


<thread hijack>

I downloaded Zenix the other day and I didn't realize until I got it that you were behind it, bodhi.  But I am running into one problem.  I don't know the root password, and it prompts me for it when I try to install it!  What is the root password?  I searched the Zenix website and did not see it.  I've tried everything: root, admin, zenix, buddha, zen, etc.

</thread hijack>

---

### Post by bodhi.zazen on 2009-12-29
> **rookcifer said:**
> <thread hijack>

I downloaded Zenix the other day and I didn't realize until I got it that you were behind it, bodhi.  But I am running into one problem.  I don't know the root password, and it prompts me for it when I try to install it!  What is the root password?  I searched the Zenix website and did not see it.  I've tried everything: root, admin, zenix, buddha, zen, etc.

</thread hijack>
  The root account is locked. When asked to enter an admin password, it is blank, simply hit enter (sudo or graphical apps) =)

---

### Post by q.dinar on 2009-12-29
may be i have found another bug of apparmor.
currently /var/www/ is not allowed to apache.
i have made new vhost with directory root like /var/www/newsite/ .
but have not created that directory and have not fixed apache profile for that directory.
if i open that vhost apache says "Not Found" but it should not know about that that directory does not exist. if i create that directory apache says "Forbidden"! ie indeed this is not apache bug/behavior when it cannot know whether there is directory. so apparmor says to apache: "forbidden" if directory is not allowed and says {something else} if this directory does not exist even if parent directory listing of it is not allowed.

i will write about this 2 bugs in bug tracker ", if the god wants".

21:42 utc+3 : [https://bugs.launchpad.net/apparmor/+bug/501404](https://bugs.launchpad.net/apparmor/+bug/501404) .

---

### Post by q.dinar on 2009-12-30
another thing about apache: php scripts working through cgi do not work under hats of apache but under main apache profile or under php-cgi profile if it is allowed with Px in main apache profile. in my case: i have used mpm-worker apache with php-cgi and fcgid. if you want to block up php script in subdirectory from accessing files that are in parent directory of same domain, that is hard to make with suexec, but may be possible with apache and apparmor and mod_apparmor and mod_php, i have not tried it yet.

---

### Post by windowless on 2010-01-02
can someone please tell me why firefox profile is disabled by default in 9.10 .I have enabeld it and it works fine.Also should i continue with apparnor or switch to selinux?

thanks

---

### Post by bodhi.zazen on 2010-01-03
> **windowless said:**
> can someone please tell me why firefox profile is disabled by default in 9.10 .I have enabeld it and it works fine.

Because not everyone understands apparmor and not all profiles work for everyone, they are disabled by default.

This is similar to iptables, by default it is permissive.

> Also should i continue with apparnor or switch to selinux?

thanksIt depends on what and how you are trying to restrict with SELinux or Apparmor. SElinux are tools, and each has advantages and disadvantages. For example, I don not believe there is any policy on Firefox in SElinux, have you ever tried to write a  policy for firefox in SELinux ? Much easier to do in Apparmor.

SELinux is used by the vast majority of people in the "targeted" mode and firefox is not currently "targeted".

SELinux is not easy to install or configure on Ubuntu, and if you prefer SELinux I would steer you to Fedora. Although we are a large community, I think you will get better support for SELinux on the Fedora Forums =)

---

### Post by rileinc on 2010-02-01
What's the difference these?
```
deny /abc r,
deny owner /abc r,
```

I looked around and found [_this_](http://en.opensuse.org/AppArmor/Changes_AppArmor_2_3#File_rules_conditional_on_file_ownership) but I don't understand what it means. 

Does it mean the owner is exempt from the rule?

---

### Post by jgoguen on 2010-02-01
> **rileinc said:**
> What's the difference these?
```
deny /abc r,
deny owner /abc r,
```I looked around and found [_this_]("http://en.opensuse.org/AppArmor/Changes_AppArmor_2_3#File_rules_conditional_on_file_ownership") but I don't understand what it means. 

Does it mean the owner is exempt from the rule?
Basically the opposite actually.  The "owner" keyword means the rule only applies to the file (or directory/socket/device) owner.  If you have /abc owned by user1, then the rule denies read access to only user1.  Other users may be denied access via other means (like UNIX permissions or ACLs) but the AppArmor rule is what blocks user1.

Why one would want to use "deny owner" I'm not too sure, but I'm sure if I put some thought into it I'd end up rewriting half my profiles to use it :)

---

### Post by bodhi.zazen on 2010-02-01
The only reason I can think to deny the owner would be if you wished to deny access to a specific file or directory or resource , but allow other users access (within the profile).

This would be rare and I can not think of a specific example at this time.

I would think the vast majority of the time it would be the case when you would simply wish to deny access to everyone.

---

### Post by q.dinar on 2010-02-09
hello.
it seems there is one disadvantage of syslog, it seems that it do not log all messages but write "n messages suppressed".  does it? does auditd log all?

add after a minute: is it possible to configure syslog [temporarily] to not write "suppressed" but log all?

---

### Post by q.dinar on 2010-02-09
installation of driver for samsung ml-1640 printer:
```
# min qdb yazam
#include <tunables/global>

/home/dinar/cdroot/autorun {
  #include <abstractions/base>
/home/dinar/cdroot/autorun r,
/usr/bin/dirname ix,
/bin/dash ix,
/home/dinar/cdroot/** r,
/usr/bin/basename ix,
/bin/sed ix,
/bin/grep ix,
/usr/bin/tr ix,
/bin/cat ix,
/proc/filesystems r,
/etc/issue r,
/bin/uname ix,
/bin/ls ix,
/usr/bin/mawk ix,
/etc/nsswitch.conf r,
/etc/passwd r,
/etc/group r,
/proc/bus/usb/ r,
/proc/bus/usb/** r,
/bin/mount ix,
/home/dinar/cdroot/Linux/i386/qt4apps/install/guiinstall ix,
/home/dinar/cdroot/Linux/i386/install/guiinstall ix,
/usr/lib/ r,
/bin/zcat ixr,
/bin/tar ix,
/sbin/ldconfig ixr,
/etc/fstab r,
/etc/mtab r,
/proc/*/mounts r,
/dev/tty rw,
/dev/pts/* rw,
/bin/gzip ix,
/sbin/ldconfig.real ix,
/home/dinar/cdroot/Linux/i386/lib/*.so* mr,
/usr/bin/id ix,
/bin/sleep ix,
/etc/ld.so.cache~ wr,
/usr/lib/libtiff.so.3 w,
/usr/lib/libtiff.so.3.6.1 w,
/etc/ld.so.conf r,
/var/cache/ldconfig/aux-cache r,
/lib/ r,
/usr/lib/libstdc++.so.5 w,
/usr/lib/libstdc++.so.5.0.5 w,
/etc/ld.so.conf.d/ r,
/etc/ld.so.cache w,
/etc/ld.so.conf.d/** r,
/var/cache/ldconfig/aux-cache~ wr,
capability dac_override,
capability dac_read_search,
/root/.qt/ wr,
/root/.qt/* wr,
/usr/share/X11/XKeysymDB r,
/usr/bin/gs ix,
/etc/fonts/ r,
/etc/fonts/** r,
/var/cache/fontconfig/** r,
/usr/share/fonts/ r,
/usr/share/fonts/** r,
/tmp/libgksu-*/.Xauthority r,
/root/.config/Trolltech.conf wrk,
/var/lib/dbus/machine-id r,
/usr/bin/dbus-launch ix,
/var/lib/defoma/fontconfig.d/** r,
/tmp/orbit-root/linc-*-*-* wrk,
/usr/share/themes/** r,
/usr/lib/pango/1.6.0/modules/*.so mr,
/usr/share/icons/ r,
/usr/share/icons/** r,
/usr/lib/gtk-2.0/2.10.0/immodules/*.so m,
/usr/share/gvfs/remote-volume-monitors/ r,
/usr/share/gvfs/remote-volume-monitors/** r,
/usr/lib/ghostscript/8.70/X11.so m,
/home/dinar/cdroot/Linux/i386/qt4apps/install/*.so* m,
/usr/local/share/icons/ r,
/usr/local/share/icons/** r,
/usr/share/pixmaps/ r,
/usr/share/pixmaps/** r,
/root/.local/share/mime/* r,
/tmp/smfp_users_to_add wr,
/home/dinar/cdroot/Linux/install.sh ix,
/home/dinar/cdroot/Linux/i386/qt4apps/at_opt/bin/shhv ix,
/home/dinar/cdroot/Linux/i386/** ix,
/bin/mkdir ix,
/usr/share/mime/* r,
/usr/lib/gtk-2.0/2.10.0/loaders/*.so m,
/tmp/mfp_Samsung_install/ wr,
/tmp/mfp_Samsung_install/** wr,
/bin/touch ix,
/opt/Samsung/ wr,
/opt/Samsung/** wr,
/usr/bin/find ix,
/bin/ln ix,
/bin/chown ix,
/bin/chmod ix,
/etc/sane.d/dll.conf rw,
/usr/bin/head ix,
/usr/sbin/lpadmin ix,
/usr/bin/lpoptions ix,
/usr/bin/expr ix,
#/root/Desktop/SamsungConfigurator.desktop wr,
/bin/cp ix,
/sbin/udevadm ix,
/lib/init/upstart-job ix,
/bin/rm ix,
/usr/share/ppd/samsung wr,
/usr/share/ppd/samsung/** wr,
/etc/init.d/cups ixr,
/etc/services r,
/etc/udev/udev.conf r,
/sys/bus/ r,
/sys/bus/** r,
/sys/class/ r,
/sys/class/** r,
/etc/timezone r,
/sbin/usplash_write ix,
/bin/readlink ix,
/sbin/start-stop-daemon ix,
/var/run/cups/cupsd.pid r,
/proc/*/stat r,
/usr/sbin/cupsd ix,
/etc/cups/* r,
/etc/lsb-base-logging.sh r,
/usr/lib/cups/backend/mfp ix,
/etc/papersize r,
/usr/share/cups/** r,
/etc/cups/** r,
/etc/cups/ r,
/var/spool/cups/ r,
/sys/devices/ r,
/etc/resolv.conf r,
/etc/host.conf r,
/etc/hosts r,

/tmp/* wr,
/var/run/cups/** rw,
/var/spool/cups/** rw,
/var/cache/cups/** rw,
/var/log/cups/** rw,
capability fsetid,
#network inet stream,
#network inet6 stream,
/etc/cups/lpoptions wr,
/etc/cups/smfp.convs wr,
/etc/cups/smfp.types rw,
/dev/.initramfs/usplash_fifo wr,
capability chown,
capability sys_ptrace,
/sys/devices/LNXSYSTM:00/** w,
/sys/devices/pci0000:00/** w,
/sys/devices/platform/** w,
/sys/devices/** wr,
/etc/cups/ppd/*.ppd wr,


#/root/.gnome-desktop/ wr,
#/root/.gnome-desktop/** wr,
#/usr/sbin/Desktop/ wr,
#/usr/sbin/.gnome-desktop/ rw,
#/usr/sbin/Desktop/SamsungConfigurator.desktop wr,
#/usr/sbin/.gnome-desktop/SamsungConfigurator.desktop rw,
#/bin/Desktop/ wr,
#/bin/.gnome-desktop/ wr,
#/bin/Desktop/SamsungConfigurator.desktop wr,
#/bin/.gnome-desktop/SamsungConfigurator.desktop wr,
#/dev/Desktop/ wr,
#/dev/.gnome-desktop/ wr,
#/usr/games/Desktop/ wr,
#/usr/games/.gnome-desktop/ wr,
#/dev/Desktop/SamsungConfigurator.desktop wr,
#/dev/.gnome-desktop/SamsungConfigurator.desktop wr,
#/usr/games/Desktop/SamsungConfigurator.desktop wr,
#/usr/games/.gnome-desktop/SamsungConfigurator.desktop wr,
#/var/{mail,www,backups}/{Desktop,.gnome-desktop}/ wr,
#/var/{mail,www,backups}/{Desktop,.gnome-desktop}/SamsungConfigurator.desktop wr,
#/Desktop/ wr,
#/.gnome-desktop/ wr,
#/Desktop/SamsungConfigurator.desktop wr,
#/.gnome-desktop/SamsungConfigurator.desktop wr,
/home/{MYSISTER,dinar}/Desktop/ wr,
/home/{MYSISTER,dinar}/.gnome-desktop/ wr,
/home/{MYSISTER,dinar}/Desktop/SamsungConfigurator.desktop wr,
/home/{MYSISTER,dinar}/.gnome-desktop/SamsungConfigurator.desktop wr,
#/var/cache/bind/Desktop/ w,
#/var/cache/bind/.gnome-desktop/ w,
#/var/cache/bind/Desktop/SamsungConfigurator.desktop w,
#/var/cache/bind/.gnome-desktop/SamsungConfigurator.desktop w,

/opt/smfp-common/ wr,
/opt/smfp-common/** wr,
/usr/lib/libmfp.so.1.0.1 w,
/usr/lib/cups/filter/rastertosamsungspl w,
/usr/lib/cups/filter/rastertosamsungsplc w,
/usr/lib/cups/filter/pscm w,
/usr/lib/cups/filter/libscmssf.so w,
/usr/lib/cups/filter/rastertosamsungpcl w,
/usr/lib/cups/filter/pscms w,
/usr/lib/cups/filter/libscmssc.so w,
/usr/lib/cups/filter/smfpautoconf w,
/usr/lib/cups/filter/rastertosamsunginkjet w,
/usr/lib/cups/backend/mfp w,
/usr/sbin/smfpd w,
/usr/lib/libmfp.so* w,
/usr/lib/sane/libsane-smfp.so* w,
/etc/modprobe.conf w,
/etc/mfpcommon.modules.conf w,
/usr/bin/lpr wr,
/var/tmp/ipp_*.log wr,
/etc/cups/printers.conf* wr,
/etc/cups/classes.conf* wr,
/usr/bin/lpr.orig wr,
/var/tmp/PrinterOptions.log wr,
"/root/.config/Unknown Organization.conf" wrk,



/usr/ r,
/bin/rmdir ix,
/etc/udev/rules.d/*_smfpautoconf_samsung.rules wr,
/usr/lib/libcups.so w,
/usr/bin/file ix,
/usr/share/cups/model/ wr,
/usr/share/cups/model/** wr,
/opt/Samsung/mfp/bin/printeradd ix,
/etc/magic r,
/usr/share/file/* r,
/etc/default/cups r,
/bin/mv ix,
/bin/which ixr,
/etc/modprobe.conf r,
/opt/Samsung/** m,
/usr/lib/cups/** ix,
/usr/bin/dpkg ix,
capability setgid,
capability setuid,
/etc/dpkg/** r,
/usr/bin/dpkg-query ix,
/var/lib/dpkg/** r,
/usr/local/share/ppd/ r,
/usr/share/ppd/ r,
/usr/local/share/ppd/** r,
/usr/share/ppd/** r,
/usr/lib/gutenprint/** m,
/usr/share/gutenprint/** r,
/proc/sys/dev/parport/parport0/autoprobe r,
/opt/Samsung/mfp/bin/printertest ix,
/dev/usb/lp* rw,
/opt/Samsung/mfp/bin/* ix,
/usr/bin/lpr.orig ix,
/bin/mktemp ix,
/proc/sys/kernel/osrelease r,
/usr/bin/pdftops ix,
/var/tmp/jobN*.tmp wr,
/usr/share/ghostscript/** r,
/bin/egrep ix,
/usr/bin/ps2pdf13 ixr,
/usr/bin/perl ix,
/var/lib/defoma/gs.d/dirs/fonts/ r,
/var/lib/defoma/gs.d/dirs/fonts/** r,
/var/tmp/backend.out wrk,
/usr/bin/ps2pdfwr rix,
/usr/bin/bc ix,


}
``` - not fully in time order as i usually write/make apparmor profile.

---

### Post by jgoguen on 2010-02-09
> **q.dinar said:**
> hello.
it seems there is one disadvantage of syslog, it seems that it do not log all messages but write "n messages suppressed".  does it? does auditd log all?

add after a minute: is it possible to configure syslog [temporarily] to not write "suppressed" but log all?
That's no bug, that's a feature :)

When you see that "messages suppressed" message, what it means is that the message immediately before it was repeated, with no changes at all, *n* times.  So if you see a message that says "denied incoming connection from 192.168.2.1" and then immediately after you see "28 messages suppressed", that means the first "denied connection" message actually happened 29 times in a row.  Trust me, it's a feature, it helps keep the size of your log file down without actually taking away much important info.  I think all you lose is how quickly those events happened and the actual times of each event.  I don't know off the top of my head if you can disable that, or if auditd does it or not.

---

### Post by q.dinar on 2010-02-09
thank you, i thought that it suppresses even if messages are not exactly same. i have not said "bug".

---

### Post by andrewthomas on 2010-02-22
I added the following lines to the default apparmor profile for firefox to enable support for java :

  /etc/passwd mr,
  /etc/timezone r,
  /etc/lsb-release r,
  # java
  /opt/java/64/** mr,
  /opt/java/64/jre1.6.0_*/bin/java ixr,
  /tmp/** mwr,
  /etc/.java/** rwk,
  /etc/.java/ rw,

It would probably work without the access to passwd, timezone and lsb-release but it was asking so I let it.

Is there any reason why I should deny any of the above access?

---

### Post by bodhi.zazen on 2010-02-22
I would not allow access to /etc/passwd unless denying access breaks something.

Neural on /etc/lsb-release On these more minor files, it s a balance between a quiet log file and access.

---

### Post by jgoguen on 2010-02-22
> **andrewthomas said:**
> I added the following lines to the default apparmor profile for firefox to enable support for java :

  /etc/passwd mr,
  /etc/timezone r,
  /etc/lsb-release r,
  # java
  /opt/java/64/** mr,
  /opt/java/64/jre1.6.0_*/bin/java ixr,
  /tmp/** mwr,
  /etc/.java/** rwk,
  /etc/.java/ rw,

It would probably work without the access to passwd, timezone and lsb-release but it was asking so I let it.

Is there any reason why I should deny any of the above access?
Those are all fine.  /etc/passwd is commonly read to convert numeric UIDs into actual user names (or the other way around) and for other info like what shell the user wants, or their full name or things like that.  /etc/timezone is timezone information, what your offset from GMT is, are you in daylight savings time, etc.  /etc/lsb-release is a distro-agnostic way of determining the operating system, release version and codename.  Here's what my /etc/lsb-release contains for Ubuntu 9.10 (Karmic):
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
```
So in short, I would allow those accesses myself. (EDIT: Obviously opinions differ, but that's OK. Just don't go allowing Java to read /etc/shadow  :))

The only thing I would add is that the paths under /opt won't work for people who installed Java from the Ubuntu repositories.  The Java installs from the repos go under a subdirectory of /usr/lib/jvm/ (like my Java install at /usr/lib/jvm/java-6-openjdk/).  All this means is that people using your profile additions with Java from the repositories will need to use different paths than what you have, but it's good for you to keep those lines since that's where your Java is installed :)

---

### Post by andrewthomas on 2010-02-22
> **bodhi.zazen said:**
> I would not allow access to /etc/passwd unless denying access breaks something.

Neural on /etc/lsb-release On these more minor files, it s a balance between a quiet log file and access.
Thanks.  I removed the access to /etc/passwd and it works fine.  I can deal with two extra log lines  :D

---

### Post by q.dinar on 2010-04-01
i have disallowed network stream and dgram for virtualbox. now i have tried to access to host ubuntu's apache server. for that i searched in internet and from that know out that should access 10.0.2.2 but it does not work, at that time there is reaction in syslog, reports that needs stream and dgram permission. i used that 10.0.... ip but do not remember what exactly.
as i know accessing to localhost should not require network access. so why it looks like virtualbox requires it?
i think i will not explore this thing >15:13utc+4:without allowing network in vbox<, i am going to try to enable access to network.
virtualbox required network and dgram network permission also when it just works, without accessing 10.0.... form browser. i also have now tried to disable network, with that setting it only have written one line in log or none. i think even without NAT or any other network setting it may be possible to access to 10.0.... to host computer. there are other options except NAT, if i select them vbox says incorrect setting, only internal networking does not cause it to say so , but it is for connecting several guest OSes.

---

### Post by Jigen on 2010-04-10
Hi there, I hope this is the right thread for my question.

I have tried to create a new apparmor profile for firefox 3.5 running on jaunty, however I did not succeed so I tried to grab the profile included in karmic, copy it into jaunty's apparmor.d directory and load it
```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox-3.5
```it complained about the unavailability of some abstractions (private-files, ubuntu-mail...), I looked for them in my abstractions directory and did not find them (probably they do not exist in jaunty, even though I have installed the additional apparmor profiles from ubuntu's repos), so I deleted just the 4  lines the terminal complained of (they were all like #include abstraction ...).

it tried to load the profile again but replied with the following error

```
AppArmor parser error in /etc/apparmor.d/usr.bin.firefox-3.5 at line 915: syntax error, unexpected TOK_ID, expecting TOK_MODE
 Profile /etc/apparmor.d/usr.bin.firefox-3.5 failed to load
```but I am absolutely sure I only deleted those four lines with #include abstraction...

in particular they are line 85, 181, 182 and 186 in karmic default firefox-3.5 profile.

How can I solve the problem? :confused:

---

### Post by rookcifer on 2010-04-10
Those abstraction files *should* be there.  They were when I was using Jaunty.

Why don't you tell us exactly which 4 abstraction files are missing and then I (or someone) here can post them so you can add them manually.  That will be better than deleting lines from the firefox-profile itself.

---

### Post by uRock on 2010-04-10
have you ran ```
sudo apt-get install apparmor-profiles
```

---

### Post by bodhi.zazen on 2010-04-10
IMO firefox is not the best aa profile to start with and there are syntax variations between version of ff.

You can try this repository and go from there ...

[http://bodhizazen.net/aa-profiles/bodhizazen/](http://bodhizazen.net/aa-profiles/bodhizazen/)

---

### Post by uRock on 2010-04-10
> **bodhi.zazen said:**
> IMO firefox is not the best aa profile to start with and there are syntax variations between version of ff.

You can try this repository and go from there ...

[http://bodhizazen.net/aa-profiles/bodhizazen/](http://bodhizazen.net/aa-profiles/bodhizazen/)

You've been on a roll with getting Lucid in there, thanx.

Cheers,
Ronnie

---

### Post by Jigen on 2010-04-11
> **bodhi.zazen said:**
> IMO firefox is not the best aa profile to start with and there are syntax variations between version of ff.

You can try this repository and go from there ...

[http://bodhizazen.net/aa-profiles/bodhizazen/](http://bodhizazen.net/aa-profiles/bodhizazen/)

I have tried with the ff-3.5 profile for karmic (even though I run jaunty, but I cannot find a ff 3.5 profile for jaunty in the repository), but it does not work, giving the same problems as above mentioned:(

@uRock 
of course I have installed apparmor-profiles, but there is no trace of a ff 3.* profile or the abstractions I was asked for

@rookcifer
unfortunately they are not there :(  the abstractions apparmor looked for should be:

```
Setting /etc/apparmor.d/usr.bin.firefox-3.5 to enforce mode.
Error:  #include <abstractions/private-files> not found at line 85 in  stdin.
Error: #include <abstractions/ubuntu-email> not found at  line 181 in stdin.
Error: #include  <abstractions/ubuntu-console-email> not found at line 182 in  stdin.
Error: #include <abstractions/ubuntu-gnome-terminal> not  found at line 186 in stdin.
```when I deleted them (furthermore, bodhi.zazen's profile did not include the last three so I thought I could do it without specific drawbacks) I got

```
AppArmor parser error in /etc/apparmor.d/usr.bin.firefox-3.5~ at  line 916: syntax error, unexpected TOK_ID, expecting TOK_MODE
 *  Failure: /etc/apparmor.d/usr.bin.firefox-3.5~ failed to load
```:(

---

### Post by bodhi.zazen on 2010-04-11
Due to syntax changes in apparmor you can not use the karmic profile.

You can start with 

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.04/usr.lib.firefox-3.0.14.firefox.sh](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.04/usr.lib.firefox-3.0.14.firefox.sh)

and the karmic profile and manually update the 3.0.14 profile based on the karmic firefox 3.5.x

Hint: Change the references for firefox 3.0.x to firefox 3.5.x

But the exact path will depend on how you installed firefox 3.5.

---

### Post by rookcifer on 2010-04-11
Jigen:

Here are the abstraction files as they appear on my machine.  

First up is **"private-files"**:

```
# vim:syntax=apparmor
# privacy-violations contains rules for common files that you want to explicity
# deny access

  # privacy violations (don't audit files under $HOME otherwise get a
  # lot of false positives when reading contents of directories)
  deny @{HOME}/.*history mrwkl,
  deny @{HOME}/.fetchmail* mrwkl,
  deny @{HOME}/.viminfo* mrwkl,
  deny @{HOME}/.*~ mrwkl,
  deny @{HOME}/.*.swp mrwkl,
  deny @{HOME}/.*~1~ mrwkl,
  deny @{HOME}/.*.bak mrwkl,

  # special attention to (potentially) executable files
  audit deny @{HOME}/bin/** wl,

  deny @{HOME}/.bash* mrk,
  audit deny @{HOME}/.bash* wl,

  deny @{HOME}/.profile* mrk,
  audit deny @{HOME}/.profile* wl,

  deny @{HOME}/.*rc mrk,
  audit deny @{HOME}/.*rc wl,
```

**ubuntu-email**:

```
#
# abstraction for allowing graphical email clients in Ubuntu
#

  /usr/bin/anjal Ux,
  /usr/bin/balsa Ux,
  /usr/bin/claws-mail Ux,
  /usr/bin/evolution Ux,
  /usr/lib/GNUstep/Applications/GNUMail.app/GNUMail Ux,
  /usr/bin/kmail Ux,
  /usr/bin/mailody Ux,
  /usr/bin/modest Ux,
  /usr/bin/seamonkey Ux,
  /usr/bin/sylpheed Ux,
  /usr/bin/tkrat Ux,

  /usr/lib/thunderbird/thunderbird Ux,
```

**ubuntu-console-email**

```
#
# abstraction for allowing console email clients in Ubuntu. These will
# typically also need a terminal, so when using this abstraction, should also
# do something like:
#
# #include <abstractions/ubuntu-gnome-terminal>
#

  /usr/bin/alpine Ux,
  /usr/bin/citadel Ux,
  /usr/bin/cone Ux,
  /usr/bin/elmo Ux,
  /usr/bin/mutt Ux,
```


**ubuntu-gnome-terminal**

```
#
# for allowing access to gnome-terminal
#

  #include <abstractions/gnome>

  # do not use ux or Ux here. Use at a minimum ix
  /usr/bin/gnome-terminal ix,
```

Add these to abstractions then put the FF profile back to how it was at default, and you should be set.

---

### Post by Jigen on 2010-04-11
Thank you for the help! :)

Unfortunately there are still a couple of issues which are not clear to me:

So even if I add the above reported abstractions file in my abstractions directory, the karmic's profile won't work? 

Does "manually update the 3.0.14 profile based on the karmic firefox 3.5.x" mean that I have to edit the file with gedit? In this case, I suppose I should just change the references for "ff-3.0.14" to "ff-3.5.*", am I right??
:confused:

---

### Post by bodhi.zazen on 2010-04-11
> **Jigen said:**
> Thank you for the help! :)

Unfortunately there are still a couple of issues which are not clear to me:

So even if I add the above reported abstractions file in my abstractions directory, the karmic's profile won't work? 

Does "manually update the 3.0.14 profile based on the karmic firefox 3.5.x" mean that I have to edit the file with gedit? In this case, I suppose I should just change the references for "ff-3.0.14" to "ff-3.5.*", am I right??
:confused:

Yes you will need to manually edit the firefox profile. You will need to know the proper location of the various libs which is as I tried to point out is dependent on how you installed firefox.

I am not positive, but I do not think you can use * with jaunty, you will have to specify the version.

Thus you will need to use firefox 3.5.x and NOT firefox 3.5.*

---

### Post by bapoumba on 2010-05-26
Ping jgoguen :)
[http://ubuntuforums.org/showpost.php?p=9365820&postcount=2](http://ubuntuforums.org/showpost.php?p=9365820&postcount=2)

---

### Post by jgoguen on 2010-05-26
ohai :)

---

### Post by q.dinar on 2010-06-01
hello
i have "cache" directory in apparmor.d directory. is this normal? this is in ubuntu 9.10 . was it in previous versions? in my ubuntu 9.04 it was not, i think. this cache directory's content: [http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/cache/](http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/cache/) .

---

### Post by q.dinar on 2010-07-11
hello
after reloading profile restarting apache is needed. after restart apache cache disappear and it work little slower. for that once installing new script and changing for that apparmor profile of apache, i thought let i do not restart apache today, will see whether it work tomorrow after restart. that tomorrow it worked. after several days i see that some files are created by apache though not allowed by apparmor. i have looked sudo aa-status and see no apache here! i have loaded it with sudo apparmor_parser /etc/apparmor.d/usr.lib.apache2.mpm-worker.apache2 and have seen that there is syntax error and it just did not load on system start these days. so reload edited(updated) profile immediately, even if you do not restart blocked program, to check syntax of profile. also may be there is syntax check command? ... seems not.
and by the way, bug report: line number of syntax error is not shown correctly... i should write this to bug tracker...

---

### Post by CandidMan on 2010-07-12
Hi there,
1st post on these forums so hope I don't sound too much of a noob. :-k

I've been running Ubuntu since February, so since Karmic and am now onto Lucid, and only just recently discovered AppArmor. I figured better safe than sorry.

My question is, when running "aa-logprof" there's a "(C)hild" option. "Inherit" I think I get but what's the difference?

Bigger question: Anyone worked out how to get Firefox 3.6.6 and AppArmor to play nice? Am pulling my hair out here ](*,)

I have what I think is a pretty permissive Firefox profile:

```
#include <tunables/global>

/usr/lib/firefox-3.6.6/firefox.sh {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/bash>
  #include <abstractions/consoles>
  #include <abstractions/evince>
  #include <abstractions/nameservice>

  deny capability sys_ptrace,



  /bin/basename rix,
  /bin/bash rix,
  /bin/dash rix,
  /bin/grep rix,
  /bin/ps rix,
  /bin/sed rix,
  /bin/uname cx,
  /bin/which rcx,
  /etc/firefox/** r,
  /etc/magic r,
  /etc/mailcap r,
  /etc/mime.types r,
  /etc/xul-ext/* r,
  owner /home/*/.adobe/**/ r,
  owner /home/*/.cache/* k,
  owner /home/*/.config/** rw,
  owner /home/*/.esd_auth r,
  owner /home/*/.gtk-bookmarks r,
  owner /home/*/.local/** r,
  owner /home/*/.macromedia/** rw,
  /home/*/.mozilla/firefox/** rwk,
  owner /home/*/.recently-used.xbel r,
  owner /home/*/Documents/** r,
  owner /home/*/Downloads/ r,
  owner /home/*/Downloads/* rw,
  /proc/ r,
  /proc/* r,
  /proc/*/cmdline r,
  /proc/*/stat r,
  /proc/*/status r,
  /proc/sys/kernel/pid_max r,
  /usr/bin/basename cx,
  /usr/bin/dirname cx,
  /usr/bin/expr rix,
  /usr/bin/file rix,
  /usr/bin/gedit rix,
  /usr/lib/firefox-3.6.6/firefox rix,
  /usr/lib/firefox-3.6.6/firefox-bin rix,
  /usr/lib/firefox-3.6.6/plugin-container rix,
  /usr/lib/firefox-3.6.6/run-mozilla.sh rix,
  /usr/lib/firefox/firefox px,


profile /bin/uname {

    /etc/*.alias r,
    /etc/*.cache r,
    /lib/tls/i686/cmov/*.so mr,
    /usr/lib/gconv/*.cache r,
    /usr/lib/locale/** r,

  }

profile /bin/which {
    #include <abstractions/kde>


    /bin/which r,

  }

profile /usr/bin/basename {
    #include <abstractions/base>


    /etc/*.cache r,

  }

profile /usr/bin/dirname {
    #include <abstractions/base>



  }
}
```

---

### Post by q.dinar on 2010-07-22
hello.
i have installed mod wsgi for apache and now i have 6 dac_override messages after apache start, no other messages. how can i discover, why apache needs it? it needs it for concrete files?

---

### Post by CandidMan on 2010-07-22
> **CandidMan said:**
> Hi there,
1st post on these forums so hope I don't sound too much of a noob. :-k

I've been running Ubuntu since February, so since Karmic and am now onto Lucid, and only just recently discovered AppArmor. I figured better safe than sorry.

My question is, when running "aa-logprof" there's a "(C)hild" option. "Inherit" I think I get but what's the difference?

Bigger question: Anyone worked out how to get Firefox 3.6.6 and AppArmor to play nice? Am pulling my hair out here ](*,)

I have what I think is a pretty permissive Firefox profile:

```
#include <tunables/global>

/usr/lib/firefox-3.6.6/firefox.sh {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/bash>
  #include <abstractions/consoles>
  #include <abstractions/evince>
  #include <abstractions/nameservice>

  deny capability sys_ptrace,



  /bin/basename rix,
  /bin/bash rix,
  /bin/dash rix,
  /bin/grep rix,
  /bin/ps rix,
  /bin/sed rix,
  /bin/uname cx,
  /bin/which rcx,
  /etc/firefox/** r,
  /etc/magic r,
  /etc/mailcap r,
  /etc/mime.types r,
  /etc/xul-ext/* r,
  owner /home/*/.adobe/**/ r,
  owner /home/*/.cache/* k,
  owner /home/*/.config/** rw,
  owner /home/*/.esd_auth r,
  owner /home/*/.gtk-bookmarks r,
  owner /home/*/.local/** r,
  owner /home/*/.macromedia/** rw,
  /home/*/.mozilla/firefox/** rwk,
  owner /home/*/.recently-used.xbel r,
  owner /home/*/Documents/** r,
  owner /home/*/Downloads/ r,
  owner /home/*/Downloads/* rw,
  /proc/ r,
  /proc/* r,
  /proc/*/cmdline r,
  /proc/*/stat r,
  /proc/*/status r,
  /proc/sys/kernel/pid_max r,
  /usr/bin/basename cx,
  /usr/bin/dirname cx,
  /usr/bin/expr rix,
  /usr/bin/file rix,
  /usr/bin/gedit rix,
  /usr/lib/firefox-3.6.6/firefox rix,
  /usr/lib/firefox-3.6.6/firefox-bin rix,
  /usr/lib/firefox-3.6.6/plugin-container rix,
  /usr/lib/firefox-3.6.6/run-mozilla.sh rix,
  /usr/lib/firefox/firefox px,


profile /bin/uname {

    /etc/*.alias r,
    /etc/*.cache r,
    /lib/tls/i686/cmov/*.so mr,
    /usr/lib/gconv/*.cache r,
    /usr/lib/locale/** r,

  }

profile /bin/which {
    #include <abstractions/kde>


    /bin/which r,

  }

profile /usr/bin/basename {
    #include <abstractions/base>


    /etc/*.cache r,

  }

profile /usr/bin/dirname {
    #include <abstractions/base>



  }
}
```
Never mind. Recent Firefox update included a pretty comprehensive Apparmor profile

---

### Post by q.dinar on 2010-07-25
hello
i many have errors in ...messages like:
```
Jul 25 20:45:35 dinar-desktop kernel: [56178.185437] type=1502 audit(1280076335.905:11290): operation="file_lock" pid=5505 parent=1 profile="/etc/cron.daily/logrotate//null-1e3" requested_mask="::k" denied_mask="::k" fsuid=123 ouid=0 name="/var/run/proftpd/proftpd.scoreboard"

```
i have made rule for them in ...etc.cron.daily.logrotate and reloaded it but i do not know how to restart logrotate. good that it is in complain mode and i will restart OS at night, but i would restart logrotate if know how. i googled it and found almost only this: [http://www.linuxquestions.org/questions/linux-newbie-8/restart-logrotate-505343/](http://www.linuxquestions.org/questions/linux-newbie-8/restart-logrotate-505343/) where is said that it is impossible to restart it.

add after several minutes:
it has stopped to log after restart of proftpd.

---

### Post by bodhi.zazen on 2010-07-25
Null profiles , like the one you posted,
[FONT=monospace]
[/FONT]> profile="/etc/cron.daily/logrotate//[COLOR=darkred]**null-1e3**[/COLOR]"Are generated from and earlier denial. You need to identify and fix the earlier denial (null profiles are in general meaningless).

---

### Post by q.dinar on 2010-08-04
thank you. logrotate asks for /usr/sbin/proftpd (x), /var/run/proftpd.pid (i think rwk), /etc/proftpd/** (r), /usr/lib/apache2/mpm-worker/apache2 (x). i have now added apache and proftpd with Px. i hope it did not execute them in complain mode.

why there are these logs at system start?, this is today, other day may be differ :
```
Aug  4 06:55:58 dinar-desktop kernel: [    4.908385] type=1505 audit(1280904932.165:2): operation="profile_load" pid=383 name=/bin/netstat
Aug  4 06:55:58 dinar-desktop kernel: [    4.951065] type=1505 audit(1280904932.205:3): operation="profile_load" pid=384 name=/bin/ping
Aug  4 06:55:58 dinar-desktop kernel: [    4.974530] type=1505 audit(1280904932.229:4): operation="profile_load" pid=385 name=/etc/cron.daily/awffull
Aug  4 06:55:58 dinar-desktop kernel: [    5.007439] type=1505 audit(1280904932.261:5): operation="profile_load" pid=386 name=/etc/cron.daily/logrotate
Aug  4 06:55:58 dinar-desktop kernel: [    5.039473] type=1505 audit(1280904932.293:6): operation="profile_load" pid=387 name=/etc/cron.daily/slocate.cron
Aug  4 06:55:58 dinar-desktop kernel: [    5.053068] type=1505 audit(1280904932.309:7): operation="profile_load" pid=388 name=/etc/cron.daily/tmpwatch
Aug  4 06:55:58 dinar-desktop kernel: [    5.082692] type=1505 audit(1280904932.337:8): operation="profile_load" pid=389 name=/etc/init.d/amavis
Aug  4 06:55:58 dinar-desktop kernel: [    5.106370] type=1505 audit(1280904932.361:9): operation="profile_load" pid=390 name=/etc/init.d/clamav-daemon
Aug  4 06:55:58 dinar-desktop kernel: [    5.110278] type=1505 audit(1280904932.365:10): operation="profile_load" pid=391 name=/etc/init.d/clamav-freshclam
Aug  4 06:55:58 dinar-desktop kernel: [    5.748447] __ratelimit: 111 callbacks suppressed
Aug  4 06:55:58 dinar-desktop kernel: [    5.748455] type=1505 audit(1280904933.005:48): operation="profile_load" pid=425 name=/usr/bin/gajim
Aug  4 06:55:58 dinar-desktop kernel: [    5.776960] type=1505 audit(1280904933.033:49): operation="profile_load" pid=426 name=/usr/bin/ghex2
Aug  4 06:55:58 dinar-desktop kernel: [    5.784703] type=1505 audit(1280904933.041:50): operation="profile_load" pid=427 name=/usr/bin/gimp-2.*
Aug  4 06:55:58 dinar-desktop kernel: [    5.789306] type=1505 audit(1280904933.045:51): operation="profile_load" pid=428 name=/usr/bin/gossip
Aug  4 06:55:58 dinar-desktop kernel: [    5.799475] type=1505 audit(1280904933.053:52): operation="profile_load" pid=429 name=/usr/bin/icecast
Aug  4 06:55:58 dinar-desktop kernel: [    5.811557] type=1505 audit(1280904933.065:53): operation="profile_load" pid=430 name=/usr/bin/icecast2
Aug  4 06:55:58 dinar-desktop kernel: [    5.829942] type=1505 audit(1280904933.085:54): operation="profile_load" pid=431 name=/usr/bin/ices2
Aug  4 06:55:58 dinar-desktop kernel: [    5.834723] type=1505 audit(1280904933.089:55): operation="profile_load" pid=432 name=/usr/bin/konqueror
Aug  4 06:55:58 dinar-desktop kernel: [    5.850446] type=1505 audit(1280904933.105:56): operation="profile_load" pid=433 name=/usr/bin/kopete
Aug  4 06:55:58 dinar-desktop kernel: [    5.862958] type=1505 audit(1280904933.117:57): operation="profile_load" pid=434 name=/usr/bin/liveice
...
...
Aug  4 06:55:58 dinar-desktop kernel: [   30.864252] type=1505 audit(1280890558.121:162): operation="profile_replace" pid=1230 name=/bin/netstat
Aug  4 06:55:58 dinar-desktop kernel: [   30.868229] type=1505 audit(1280890558.125:163): operation="profile_replace" pid=1231 name=/bin/ping
Aug  4 06:55:58 dinar-desktop kernel: [   30.872185] type=1505 audit(1280890558.129:164): operation="profile_replace" pid=1232 name=/etc/cron.daily/awffull
Aug  4 06:55:58 dinar-desktop kernel: [   30.945018] type=1505 audit(1280890558.201:165): operation="profile_replace" pid=1233 name=/etc/cron.daily/logrotate
Aug  4 06:55:58 dinar-desktop kernel: [   30.949303] type=1505 audit(1280890558.205:166): operation="profile_replace" pid=1245 name=/etc/cron.daily/slocate.cron
Aug  4 06:55:58 dinar-desktop kernel: [   30.953068] type=1505 audit(1280890558.209:167): operation="profile_replace" pid=1246 name=/etc/cron.daily/tmpwatch
Aug  4 06:55:58 dinar-desktop kernel: [   30.956893] type=1505 audit(1280890558.213:168): operation="profile_replace" pid=1247 name=/etc/init.d/amavis
Aug  4 06:55:58 dinar-desktop kernel: [   30.960764] type=1505 audit(1280890558.217:169): operation="profile_replace" pid=1248 name=/etc/init.d/clamav-daemon
Aug  4 06:55:58 dinar-desktop kernel: [   30.991635] type=1505 audit(1280890558.245:170): operation="profile_replace" pid=1249 name=/etc/init.d/clamav-freshclam
Aug  4 06:55:58 dinar-desktop kernel: [   30.995578] type=1505 audit(1280890558.249:171): operation="profile_replace" pid=1250 name=/etc/init.d/ejabberd
```
i have checked with aa-status, not only these profiles are loaded.

and again ask what is in post #124, what is cache directory ( and why there are such file names and file times).

---

### Post by andrewthomas on 2010-09-10
I am having trouble with the profile for firefox-4.0.  The profile is not in /etc/apparmor.d/disable, yet when I restart, the profile is not loaded and I have to load it explicitly.  Then if I restart apparmor, it is no longer loaded.  What am I doing wrong?

**EDIT: after a couple of reboots it does now load on its own.**
```
ats@M3A32-MVP:~$ sudo apparmor_parser -r /etc/apparmor.d/usr.bin.firefox-4.0
ats@M3A32-MVP:~$ sudo /etc/init.d/apparmor status
/usr/lib/firefox-4.0b6pre/firefox{,*[^s][^h]} (enforce)
/usr/lib/firefox-4.0b6pre/firefox{,*[^s][^h]}//browser_openjdk (enforce)
/usr/lib/firefox-4.0b6pre/firefox{,*[^s][^h]}//browser_java (enforce)
/usr/bin/evince-thumbnailer (enforce)
/usr/bin/evince-previewer (enforce)
/usr/bin/evince (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//browser_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//browser_java (enforce)
/usr/sbin/tcpdump (enforce)
/usr/sbin/mysqld-akonadi (enforce)
/usr/sbin/cupsd (enforce)
/usr/lib/cups/backend/cups-pdf (enforce)
/usr/lib/connman/scripts/dhclient-script (enforce)
/usr/lib/NetworkManager/nm-dhcp-client.action (enforce)
/sbin/dhclient3 (enforce)
/usr/share/gdm/guest-session/Xsession (enforce)
ats@M3A32-MVP:~$ sudo /etc/init.d/apparmor restart
 * Reloading AppArmor profiles                                           [ OK ] 
ats@M3A32-MVP:~$ sudo /etc/init.d/apparmor status
/usr/bin/evince-thumbnailer (enforce)
/usr/bin/evince-previewer (enforce)
/usr/bin/evince (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//browser_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//browser_java (enforce)
/usr/sbin/tcpdump (enforce)
/usr/sbin/mysqld-akonadi (enforce)
/usr/sbin/cupsd (enforce)
/usr/lib/cups/backend/cups-pdf (enforce)
/usr/lib/connman/scripts/dhclient-script (enforce)
/usr/lib/NetworkManager/nm-dhcp-client.action (enforce)
/sbin/dhclient3 (enforce)
/usr/share/gdm/guest-session/Xsession (enforce)
ats@M3A32-MVP:~$
```

---

### Post by andrewthomas on 2010-09-14
Transmission does not seem to work right with the profile loaded.  I get many messages such as:
```
apparmor="DENIED" operation="open" parent=1 profile="/usr/bin/transmission" name="/var/lib/dbus/machine-id" pid=2643 comm="transmission" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
apparmor="DENIED" operation="exec" parent=2643 profile="/usr/bin/transmission" name="/usr/bin/pulseaudio" pid=7729 comm="transmission" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
apparmor="DENIED" operation="open" parent=1 profile="/usr/bin/transmission" name="/var/lib/dbus/machine-id" pid=2643 comm="transmission" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
apparmor="DENIED" operation="exec" parent=2643 profile="/usr/bin/transmission" name="/usr/bin/pulseaudio" pid=7731 comm="transmission" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
```What is the harm in allowing access to the above?

---

### Post by bodhi.zazen on 2010-09-14
> **andrewthomas said:**
> Transmission does not seem to work right with the profile loaded.  I get many messages such as:
```
apparmor="DENIED" operation="open" parent=1 profile="/usr/bin/transmission" name="/var/lib/dbus/machine-id" pid=2643 comm="transmission" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
apparmor="DENIED" operation="exec" parent=2643 profile="/usr/bin/transmission" name="/usr/bin/pulseaudio" pid=7729 comm="transmission" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
apparmor="DENIED" operation="open" parent=1 profile="/usr/bin/transmission" name="/var/lib/dbus/machine-id" pid=2643 comm="transmission" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
apparmor="DENIED" operation="exec" parent=2643 profile="/usr/bin/transmission" name="/usr/bin/pulseaudio" pid=7731 comm="transmission" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
```What is the harm in allowing access to the above?

Harm ? Apparmor should not harm anything.

If the application is working to your satisfaction you do not need to do anything further.

If the application is not working, you will need to allow access.

Other then that there are two strategies -> 

1. Allow minimal access. This may fill your logs (with "false positives").

2. Allow all normal access, this will quiet your logs, you then will find any alerts you receive meaningful (reduce false positives).

The second strategy is helpful if you wish to monitor your logs or use apparmor-notify

[http://packages.ubuntu.com/lucid/apparmor-notify](http://packages.ubuntu.com/lucid/apparmor-notify)

---

### Post by andrewthomas on 2010-09-14
> **bodhi.zazen said:**
> Harm ? Apparmor should not harm anything.

What I should have said is: 

[LIST=1]
[*]Should I grant read access on /var/lib/dbus/machine-id?
[*]Why would pulseaudio access be necessary?
[/LIST]

---

### Post by bodhi.zazen on 2010-09-14
> **andrewthomas said:**
> What I should have said is: 

[LIST=1]
[*]Should I grant read access on /var/lib/dbus/machine-id?
[/LIST]
Only you can decide that, honestly, as long as the application is working ... Depends on how full you want your logs to be vs how quiet you want aa to run.

If you are going to monitor your logs, IMO, make them as quiet as possible.> 


[LIST=1]
[*]Why would pulseaudio access be necessary?
[/LIST]


Well pulse audio is necessary for sound. Perhaps playing a theme sound ? If you really want to know, use strace.

---

### Post by rookcifer on 2010-09-14
> **andrewthomas said:**
> I am having trouble with the profile for firefox-4.0.  The profile is not in /etc/apparmor.d/disable, yet when I restart, the profile is not loaded and I have to load it explicitly.  Then if I restart apparmor, it is no longer loaded.  What am I doing wrong?


I don't know if this is the cause of your problem, but you need to go through that profile and change all "3.6.9" entries to "4.*".

---

### Post by andrewthomas on 2010-09-15
> **rookcifer said:**
> I don't know if this is the cause of your problem, but you need to go through that profile and change all "3.6.9" entries to "4.*".
They are two separate profiles.  A reboot fixed the problem
> **andrewthomas said:**
> 
**EDIT: after a couple of reboots it does now load on its own.**
```
ats@M3A32-MVP:~$ sudo apparmor_parser -r /etc/apparmor.d/usr.bin.firefox-4.0
ats@M3A32-MVP:~$ sudo /etc/init.d/apparmor status
/usr/lib/firefox-4.0b6pre/firefox{,*[^s][^h]} (enforce)
/usr/lib/firefox-4.0b6pre/firefox{,*[^s][^h]}//browser_openjdk (enforce)
/usr/lib/firefox-4.0b6pre/firefox{,*[^s][^h]}//browser_java (enforce)
/usr/bin/evince-thumbnailer (enforce)
/usr/bin/evince-previewer (enforce)
/usr/bin/evince (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//browser_openjdk (enforce)
/usr/lib/firefox-3.6.9/firefox-*bin//browser_java (enforce)

```

---

### Post by MountainX on 2010-10-14
I posted this question earlier, but I'm reposting here because I think this thread is a better place to ask my question.
          
                                                                I want to solve the apparmor="DENIED" messages from  Firefox. 

I'm looking for the quick/easy solution right now. Time doesn't permit me to study apparmor in detail at the moment. In cookbook style, what changes should I make to eliminate these messages?

[15006.769069] type=1400 audit(999999.533:28): **apparmor="DENIED"**  operation="open" parent=1  profile="/usr/lib/firefox-4.0b8pre/firefox{,*[^s][^h]}"  name=XXX_REALLY_LONG_XXX pid=3503 comm="firefox-4.0-bin"  requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000

[15112.077815] type=1400 audit(999999.834:41): **apparmor="DENIED" **operation="open"  parent=1 profile="/usr/lib/firefox-4.0b8pre/firefox{,*[^s][^h]}"  name=XXX_REALLY_LONG_XXX pid=3515 comm="firefox-4.0-bin"  requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000

[15129.784227] type=1400 audit(9999999.543:45): **apparmor="DENIED" **operation="mknod"  parent=1 profile="/usr/lib/firefox-4.0b8pre/firefox{,*[^s][^h]}"  name="/my/downloads/Software/ubuntu-10.10-dvd-amd64.iso" pid=2035  comm="firefox-4.0-bin" requested_mask="c" denied_mask="c" fsuid=1000  ouid=1000

---

### Post by bodhi.zazen on 2010-10-14
> **MountainX said:**
> I posted this question earlier, but I'm reposting here because I think this thread is a better place to ask my question.
          
                                                                I want to solve the apparmor="DENIED" messages from  Firefox. 

I'm looking for the quick/easy solution right now. Time doesn't permit me to study apparmor in detail at the moment. In cookbook style, what changes should I make to eliminate these messages?

[15006.769069] type=1400 audit(999999.533:28): **apparmor="DENIED"**  operation="open" parent=1  profile="/usr/lib/firefox-4.0b8pre/firefox{,*[^s][^h]}"  name=XXX_REALLY_LONG_XXX pid=3503 comm="firefox-4.0-bin"  requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000

[15112.077815] type=1400 audit(999999.834:41): **apparmor="DENIED" **operation="open"  parent=1 profile="/usr/lib/firefox-4.0b8pre/firefox{,*[^s][^h]}"  name=XXX_REALLY_LONG_XXX pid=3515 comm="firefox-4.0-bin"  requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000

[15129.784227] type=1400 audit(9999999.543:45): **apparmor="DENIED" **operation="mknod"  parent=1 profile="/usr/lib/firefox-4.0b8pre/firefox{,*[^s][^h]}"  name="/my/downloads/Software/ubuntu-10.10-dvd-amd64.iso" pid=2035  comm="firefox-4.0-bin" requested_mask="c" denied_mask="c" fsuid=1000  ouid=1000

Well, if your time is limited, I would first ask, why fix the problem then ? Are these denials preventing you from using firefox ?

Second, each denial is likely an edit to the firefox profile. You will need to post the exact denials, uneditied, or learn how to configure apparmor yourself. In other words, I can not tell you how to fix the problem as you edited the denials and did not post the raw data.

---

### Post by MountainX on 2010-10-14
> **bodhi.zazen said:**
> Well, if your time is limited, I would first ask, why fix the problem then ? Are these denials preventing you from using firefox ?

Second, each denial is likely an edit to the firefox profile. You will need to post the exact denials, uneditied, or learn how to configure apparmor yourself. In other words, I can not tell you how to fix the problem as you edited the denials and did not post the raw data.

Yes, the main problem that I'm encountering is that I cannot save my downloads to the locations I wish to use.

Under the commented section "# Default profile allows downloads to ~/Downloads and uploads from ~/Public" can I just list the directories I wish to be able to use?

For example, I see this entry:
```
owner @{HOME}/{Desktop,Downloads}/** rw,
```Can I simply add below that one the following new line?
```
/shared_location/downloads/** rw,
```Is "owner" necessary? Why does it use two asterisks as wildcards?

I will be happy to post all the DENIED messages that I'd like to address, but if we can solve my download locations issue, that would be a great start and I would really appreciate it!

EDIT: thanks for this great thread! And for you aa-profiles repo!!!

---

### Post by bodhi.zazen on 2010-10-14
That line

```
/shared_location/downloads/** rw,
```

should allow you to download to the location in question, yes.

---

### Post by MountainX on 2010-10-14
> **bodhi.zazen said:**
> That line

```
/shared_location/downloads/** rw,
```should allow you to download to the location in question, yes.

Thank you. And what about my two questions: 
What does "owner" do? Is that just a parameter for @{HOME} to get the path?
Why does it use two asterisks as wildcards? What would one asterisk do?

---

### Post by MountainX on 2010-10-14
> **bodhi.zazen said:**
> That line

```
/shared_location/downloads/** rw,
```should allow you to download to the location in question, yes.

I changed that and restarted firefox and I still can't save to that location. Do I have to restart the OS?

Log entry:
[30144.764313] type=1400 audit(1287094667.522:60): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/lib/firefox-4.0b8pre/firefox{,*[^s][^h]}" name="/shared_location/downloads/Software/Linux/UbuntuReleases/ubuntu-10.10-dvd-amd64.iso" pid=4326 comm="firefox-4.0-bin" requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000

---

### Post by bodhi.zazen on 2010-10-14
> **MountainX said:**
> I changed that and restarted firefox and I still can't save to that location. Do I have to restart the OS?

Log entry:
[30144.764313] type=1400 audit(1287094667.522:60): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/lib/firefox-4.0b8pre/firefox{,*[^s][^h]}" name="/shared_location/downloads/Software/Linux/UbuntuReleases/ubuntu-10.10-dvd-amd64.iso" pid=4326 comm="firefox-4.0-bin" requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000

After editing the firefox profile you need to restart apparmor.

```
sudo service apparmor restart
```

---

### Post by MountainX on 2010-10-14
> **bodhi.zazen said:**
> After editing the firefox profile you need to restart apparmor.

```
sudo service apparmor restart
```

Thank you! Everything I need is working now and I learned a few things too, thanks to your kind assistance!

---

### Post by bodhi.zazen on 2010-10-14
> **MountainX said:**
> Thank you! Everything I need is working now and I learned a few things too, thanks to your kind assistance!

You are most welcome =)

---

### Post by WeAreLinux on 2010-10-16
Hi

I have 2 quick questions about this program. Didn't think this warranted it's own thread.

I want to restrict media files I have on my external HD from being able to do anything dangerous on my system except what is necessary to run properly with it's parent program (.pdf files open with Evince, video/audio open with VLC, etc.). The reason being to protect my system if I open something dangerous without knowing. Can I achieve this with AppArmor & is using AppArmor the ideal way or is there an easier method to achieve the above?

I've read the "Introduction to AppArmor sticky, but I'm still quite confused. It doesn't help that I only been using Ubuntu about 2 months now (basic computing).

Thank You

---

### Post by bodhi.zazen on 2010-10-17
> **WeAreLinux said:**
> Hi

I have 2 quick questions about this program. Didn't think this warranted it's own thread.

I want to restrict media files I have on my external HD from being able to do anything dangerous on my system except what is necessary to run properly with it's parent program (.pdf files open with Evince, video/audio open with VLC, etc.). The reason being to protect my system if I open something dangerous without knowing. Can I achieve this with AppArmor & is using AppArmor the ideal way or is there an easier method to achieve the above?

I've read the "Introduction to AppArmor sticky, but I'm still quite confused. It doesn't help that I only been using Ubuntu about 2 months now (basic computing).

Thank You

Apparmor takes a few hours to learn.

The basic syntax is that a profile is written for an application.

Within the configuration file you use

/full/path/to/file_or/directory permissions,

It would be difficult or impossible to use apparmor for what you are thinking as you would need to write a profile for each and every (or most) binaries on your system.

For what you want I would think selinux.

Better, read the security sticky.

I think if you mount your removable device as noexec and nodev that would be sufficient.

---

### Post by WeAreLinux on 2010-10-18
> **bodhi.zazen said:**
> I think if you mount your removable device as noexec and nodev that would be sufficient.

I would do that by modifying the fstab file, correct? 

Would creating a non-admin user account & editing user permissions give me that same protection (deny execute permission)?

---

### Post by donato roque on 2010-10-29
Hi. I have encountered this bit of a problem when I 
user@user-desktop:~$sudo genprof 
or use any of the apparmor utilities like logprof.

Can't find include file abstractions/apache2-common: No such file or directory

Before the problem arose, I downloaded apparmor-profiles from the repositories.  I have them in enforce mode now except a couple. If one of the profiles are looking for abstractions/apache2-common and it's not in the /etc/apparmor.d directory should I just modify the profile?  I don't run apache and don't think I will.  

Can you give me a clue on which one of the profiles would include abstraction/apache2-common? Thank you.

---

### Post by CandidMan on 2010-10-29
I'd just use:
grep -r apache /etc/apparmor.d/

to find the offending profile

I had the same problem and fixed it that way. Think it was an apache abstraction actually

---

### Post by donato roque on 2010-10-29
thank you for the tip.
I did what you said and found the reference to abstractions/apache2-common and modified the profile and saved it.  
fine now.

---

### Post by arapaho on 2010-11-05
> **CandidMan said:**
> I'd just use:
grep -r apache /etc/apparmor.d/

to find the offending profile

I had the same problem and fixed it that way. Think it was an apache abstraction actually
Can you tell me what to do exactly?
I have the same problem and after executing the above command I get this:
```
arapaho@kompik ~ $ grep -r apache /etc/apparmor.d/
/etc/apparmor.d/apache2.d/phpsysinfo:    #include <abstractions/apache2-common>
/etc/apparmor.d/apache2.d/phpsysinfo:    /var/log/apache2/access.log w,
/etc/apparmor.d/apache2.d/phpsysinfo:    /var/log/apache2/error.log w,
/etc/apparmor.d/abstractions/svn-repositories:  # it is intended to be included in profiles for svnserve/apache2 and maybe
/etc/apparmor.d/abstractions/php5:  /etc/php5/{conf.d,apache2,cli,fastcgi,cgi}/ r,
/etc/apparmor.d/abstractions/php5:  /etc/php5/{conf.d,apache2,cli,fastcgi,cgi}/*.ini r,

```

---

### Post by CandidMan on 2010-11-05
I just deleted the line containing:

#include <abstractions/apache2-common>

I suppose that's a 'hack' but it seems to work

---

### Post by MiniT on 2011-08-14
[COLOR=Green]Edits  - [/COLOR][COLOR=SeaGreen][COLOR=Blue]the whole thing LOL[/COLOR][/COLOR] - [COLOR=Red]multiple times[/COLOR]  :)


Hi and thanks for all the incredible information - there are giants in the room:twisted:

I have been slowly working though securing a laptop install of LinuxMint which is based on Ubuntu 10.10. Very similar in many ways.  Draws on Ubuntu repos.
Have installed AA(though some parts built in), AA-profiles,-docs,-notify, and their deps.

I have AA profile for firefox, based on the default one which came bundled with the distro.  I am pretty sure they didn't change anything from the Ubuntu 10.10 default FF profile,  though I did.  [COLOR=DarkOrange]Slowly reading and gaining understanding.[/COLOR]

A couple questions . . . .

[COLOR=Magenta][Redacted a big chunk of my post cause I need to read up and not be stupid.][/COLOR]

[COLOR=SeaGreen]I had some difficulty getting the profile to stick.
On system restart, it was fine, but on reload or restart of AA, Firefox's profile got dropped from view (neither enforce, nor complain . . .inconsistently).

[COLOR=Magenta][redacted - need to gather more info to expect response][/COLOR][/COLOR]

Will report back on [COLOR=Magenta][redacted][/COLOR] my progress
Will make separate post as I am feeling ridiculous with multiple edits.  :)

[COLOR=Blue](Part of message redacted.  I had issue with Flash not working  - was me not reading posts and instructions, then not hitting save.  . .<chuckle>)[/COLOR]


All of your help (any) will be much appreciated.
You rock:guitar:[COLOR=Blue]
[/COLOR]

---

### Post by MiniT on 2011-08-15
Ok
lets try from a fresh piece of paper, eh?  :)

Still having issue with what profiles get loaded when:
#on system restart - everything cool
#on restart or reboot of AA - Firefox not in status list, must start individually
#also on AA re-up - sometimes, inconsistently, samba daemons are unconfined!?  

Is this all expected/dangerous/ . . .I'm unsure!  Mostly about Samba since I dont have a printer, but may one day get one.
I expect to keep it around, but . . . don't know if I should care that it's loose irregularly  :confused:



Muchos gracias, dudes.
and sorry about the mess, I'm under construction.  :-({|=
(cool, a smily playin fiddle)

mini

---

### Post by jgoguen on 2011-08-16
OK, let's see what I can do for you :)

> **MiniT said:**
> I have AA profile for firefox, based on the default one which came bundled with the distro.  I am pretty sure they didn't change anything from the Ubuntu 10.10 default FF profile,  though I did.  [COLOR=DarkOrange]Slowly reading and gaining understanding.[/COLOR]
Make sure here that you remove the usr.bin.firefox link from /etc/apparmor.d/disable/ (anything in this directory isn't loaded by AppArmor).

> **MiniT said:**
> [COLOR=SeaGreen]I had some difficulty getting the profile to stick.
On system restart, it was fine, but on reload or restart of AA, Firefox's profile got dropped from view (neither enforce, nor complain . . .inconsistently).
This is odd. It should (as you expect) either load or not load and be consistent about it. Check for the link in /etc/apparmor.d/disable/ and see if there's anything interesting in your logs.

> **MiniT said:**
> [COLOR=Blue](Part of message redacted.  I had issue with Flash not working  - was me not reading posts and instructions, then not hitting save.  . .<chuckle>)[/COLOR]
Flash is silly anyway, I look forward to the day when we can all do without it :)

> **MiniT said:**
> 
Still having issue with what profiles get loaded when:
#on system restart - everything cool
#on restart or reboot of AA - Firefox not in status list, must start individually
#also on AA re-up - sometimes, inconsistently, samba daemons are unconfined!?

Is this all expected/dangerous/ . . .I'm unsure!  Mostly about Samba since I dont have a printer, but may one day get one.
I expect to keep it around, but . . . don't know if I should care that it's loose irregularly  :confused:
Yea, it's bad for something to not be loaded when it should. Especially if the profile isn't in /etc/apparmor.d/disable/, it should always be loaded then. I can't recall what it does with a syntax error in the profile, but that should still be a consistent load or not load.

---

### Post by MiniT on 2011-08-16
Chank you for your timely reply,much needed assistance (and forebearance)
All is well - some thoughts:

oooohhhhh.
Right, this makes perfect sense . . .

I'll put the inconsistency up to my errors of some kind.  User error is usually a safe bet when things aren't consistent in some way.  :)

Actually followed the Flash issue just as per directions:
tail -F /var/log/messages
in seperate term, sudo gedit /etc/apparmor.d/usr.bin.firefox
(fiddle with the goofy bits - my work - one line at a time)
freshly started FF profile, FF open to HULU.com
messages say first thing - (whine) FF gets into a special MINT flash directory! what the. . . OK, works much better now

Here's to directions  :)

@jgoguen - yeah man, yeah

---

### Post by MiniT on 2011-08-16
New post for [COLOR=Red]orgzanitional[/COLOR] purposes.  :)

Grey area regarding permissions - requires ME reading.
What i would like a hint on is EXPLICIT versus IMPLICIT rules in profiles.
 It starts with whatever permission it had before.
Tht means the firefox or transmission or samba critter may have a user account of sorts in a group of some kind - and defined limits therof.
What I don't get is why I can Save Page As . . . and see - pretty much anything.  Maybe even save to most sensitive areas - by default?
Shouldn't FF be, well, [COLOR=Gray]less honored[/COLOR]?
Is this the place for AA - to trim the over-reaching program?

Or is there another, more appropriate way to fence in programs' screwing with my [COLOR=Blue]sacred[/COLOR] files?
Seems like it would be a long list of DENYs to trim permissions only in a AA profile - if I wanted to limit it LITERALLY to only what it asked for and needed.  

What if I start iwth a profile that basically says :
audit deny /  mrwkl   # or anything else goshdarnit

Maybe I don't have the syntax right, but you get the idea.
In complain, it should tell me everything it needs access to, and I get to figure out if it really does or not (the hard part).

But how do I keep the blanket denial, with holes punched?
[COLOR=Green]Can I basically say NO then, WELL MAYBE?[/COLOR]  [COLOR=Green]What would that syntax look like?[/COLOR]
My profile seems very relative and very reactive to outside permissions.
Is this just part of the gammit with AA? (uh-oh, the music is starting to fade - this Armor is starting to feel heavy  :)  )

Thank you for your help before, and in future.
again @jgoguen - yeah man:cool:

(Links and "read this, dummy" would be most helpful)  [COLOR=Green]peace yall[/COLOR]

---

### Post by jgoguen on 2011-08-17
> **MiniT said:**
> 
Tht means the firefox or transmission or samba critter may have a user account of sorts in a group of some kind - and defined limits therof.
It's actually not important what the user account is until you look at rules that have the "owner" directive or use the "@{HOME}" expansion.

> **MiniT said:**
> What I don't get is why I can Save Page As . . . and see - pretty much anything.  Maybe even save to most sensitive areas - by default?
AppArmor may (for various reasons) allow you to **view** areas even if you can't save there. In the default Firefox profile, at least as I have it, Firefox only has write access to ~/Downloads/, ~/.config/ibus/bus/ and ~/.gnome2/firefox*-bin-*. But, it has read access to the home directory and to ~/Public/. So under that profile, if you use Save As in Firefox, you could go into ~/Public/ and view what's there, but you would get an error if you actually tried to save there. Are you experiencing something different? Post your whole profile if you are, we can look at it and try to figure it out.

> **MiniT said:**
> What if I start iwth a profile that basically says :
audit deny /  mrwkl   # or anything else goshdarnit
That probably won't work quite as well as you think and would lead to a much larger profile than is necessary :) What's in the default Firefox profile, which is "/ r", is a good starting point.

---

### Post by MiniT on 2011-08-17
Ah, as I thought originally.
AppArmor is supposed to be a semi-standalone permissions enforcer, yes?
A hand smackin', keep the kids in line, hard nosed old so and so.

Good.

So I'll figure out how to pin my profile for Firefox up here and you'll see DENYs for things that prob'ly shouldn't be allowed by default, but I had access to write to.  Thus the DENY rules I wrote.

Suspected issue with my messing in the code . .. we'll see.

miniT:D

[COLOR=Purple]maybe in new post I can add attachment?[/COLOR]

---

### Post by bodhi.zazen on 2011-08-17
Well , two problems you have ...

1. Yes, there is a learning curve with apparmor, there is one with selinux as well ;)

2. You are starting with a profile for firefox, try starting with a smaller, easier application and then working your way up to firefox.

[http://blog.bodhizazen.net/linux/apparmor-privoxy-profile/](http://blog.bodhizazen.net/linux/apparmor-privoxy-profile/)

---

### Post by jgoguen on 2011-08-17
AppArmor is a method for implementing Mandatory Access Control (see [http://en.wikipedia.org/wiki/Mandatory_access_control](http://en.wikipedia.org/wiki/Mandatory_access_control) for an overview; SELinux is another implementation). Enjoy your first round of light reading :)

---

### Post by MiniT on 2011-08-17
[COLOR=Purple]Ah there we go.[/COLOR] (That's a friendly color, I think I'll stay with it.)
[COLOR=Purple]Attachment attached in the attachable position.
So, do your worst.
It seems to be working for what I want.  And watch TV on internet.
I can get to everything I need, the /var/log/messages is silent for FF!
That is unless I try to open something forbidden or save to somewhere forbidden.  [COLOR=Red][bong][/COLOR]USER SMACKDOWN!  <-- also with the dialog box.

You'll note the limits on folders within my user's home.
I should only be able to write to Downloads and Desktop.
That's how it works at present, with the DENYs in place.
Oh, and despite the comment, OWNER found its way back in.
Without it . . . something wasn't working?
I forget, but this is a single user computer, so who cares right?[/COLOR]

[COLOR=Green]Perhaps there's something I should have seen, but the DENYs were necessary to limit writing to directories in home, when she was set to Enforce.[/COLOR]

Profile cobbled together for Firefox 5/Linux Mint 10 (Gnome) "Julia"
This OS is based on Ubuntu 10.10(just prettier + some tweaks).
[COLOR=Blue]
Thanks for helping dudes, you're both awesome.
Oh you slipped in while i was typing and eating oatmeal. . .
. . . 
did some reading and will do some more . . .
So folder/file permissions are DAC - user adjustable, relatively insecure. And AppArmor is  . . . not simple to describe, but works in relation to kernel to keep programs/processes in line.

OK, it seems like I should have to Explicitly grant access to somewhere, or that by saying Read access is granted, that implies nothing else is OK. 
But should NOT have to Deny access to any of the other folders in Home unless I granted it in the first place . . . maybe in the Includes . .?

Is it possible this is a Minty re-imagining of . . . sumthin'? Don't even want to think about that.
I will sieve through the Mint resources I can find and see if they have any advice to offer on this - unless you tell me I am being thick and ITS RIGT THERE in front of my face.  First time for everything.[/COLOR]
:)
--------------
I feel like I've visited this post before . . .

---

### Post by MiniT on 2011-08-18
Ok.
Me: too many [COLOR=SlateGray]words[/COLOR] B4, not enough[COLOR=Blue] content.[/COLOR]

M.A.C. reading led to more.  See helpful (many overlaps) below:

[http://en.wikipedia.org/wiki/Mandatory_access_control](http://en.wikipedia.org/wiki/Mandatory_access_control)
[Main Page - AppArmor]("http://wiki.apparmor.net/index.php/Main_Page") 
[AppArmor - Community Ubuntu Documentation]("https://help.ubuntu.com/community/AppArmor") 
[AppArmor Detail - openSUSE]("http://old-en.opensuse.org/AppArmor_Detail") 
[SDB:AppArmor geeks - openSUSE]("http://en.opensuse.org/SDB:AppArmor_geeks") 
[[all variants] Introduction to AppArmor - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1008906") 
[AppArmor - Ubuntu Wiki]("https://wiki.ubuntu.com/AppArmor") 

Also read Ubuntu Security wiki et al, [COLOR=Cyan]props[/COLOR] to [COLOR=DarkOrange]Bodhi.zazen[/COLOR].

Then scanned my usr.bin.firefox, its includes, their includes, variables, et cetera.

Came full circle to a post/thread I already had in bookmarks . . .
[[SOLVED] How to test that Apparmor is working? - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1591314") 
The name is not what I was looking for.  I knew AA was working, just not right.  Got the link to BZ's FF profile there - but missed the rest!

This is a problem in App Armor version 2.5.1, for Ubuntu 10.10.4.
If you read that SOLVED:
> Yeah, but his profile apparently does not allow writing to a directory  he is writing to.  So something is wrong somewhere, and I doubt it's the  profile.
They did as I did and traced back to [COLOR=Red]user-files[/COLOR].  Therein is the problem.

Also discovered potential for JAVA SCRIPTS to have [COLOR=Red]rwk[/COLOR] privileges in my HOME!  From /etc/apparmor.d/abstractions/ubuntu-browsers.d/java :
>     owner @{HOME}/ r,
    owner @{HOME}/** rwk,
WHat-the . . . !
Does that say what I think it does?!
Please tell me javascripts are not allowed to read/write as they please in my only user's home directory.  (no pets allowed!)

I think these are two mistakes that need reporting.
Is it Launchpad? Log in just like this forum?

I suppose my profile for FF is good for now, except the JAVA issue.
I will figure how to report if you can help me fix (if it needs fixing/reporting).

_Please set me straight if I need it!_ :(

[COLOR=Purple]Respectfully,[/COLOR]
miniT

---

### Post by jgoguen on 2011-08-18
> **MiniT said:**
> Does that say what I think it does?!
Please tell me javascripts are not allowed to read/write as they please in my only user's home directory.  (no pets allowed!)
No, JavaScript never has access to the file system. That profile snippet is for Java, which is a whole other nasty thing. But yes, that does mean "read $HOME and read/write **anything** under $HOME". Which I think we both agree is a Bad Thing (although needed for Java to work...) and is a reason why I tend to avoid Java where I can :) If you don't use Java applets, you could try removing that and see how far you get.

Always remember, despite any naming similarities Java and JavaScript are **not** related. It tends to help to think less about "JavaScript" and more about "ECMAScript". JavaScript is a dialect of ECMAScript, and so is JScript, QtScript and ActionScript. Thinking of it as ECMAScript also helps to avoid any confusion with Java, which is completely unrelated and wholly separate from JavaScript.

---

### Post by MiniT on 2011-08-18
I'll read up on Java (and ECMA scripts).  Thank you.

A load off of the mind! :D
So, perhaps just striking the line that calls up the java file?
Or edit it's permissions to a strict level with audit DENYs and watch what happens?

Why does it need ALL of Home?  That's greedy.

---

### Post by jgoguen on 2011-08-19
I'm not familiar with Java so I'm not sure what the plugin needs under $HOME to make it so greedy. This is part of why bodhi.zazan suggested you start with a smaller program and work up to Firefox :)

I rarely allow Java applets at home, so I can safely remove the Java abstraction from the Firefox abstraction. However, that does imply a bit of extra work when I actually do need to run Java applets as I need to put that line back, reload AppArmor, restart Firefox and then undo it all again later. AppArmor is anything but "fire and forget", much to the annoyance of people looking for a simple no-maintenance solution :)

---

### Post by MiniT on 2011-08-21
> **jgoguen said:**
> AppArmor is anything but "fire and forget", much to the annoyance of people looking for a simple no-maintenance solution :)
Yeah, moving target makes it more fun! :)

[COLOR=Blue]EDIT: fixed this profile, see next post if you like[/COLOR] :)
Speaking of which:
Simple Transmission profile, in complain mode.
One line popped up in /var/log/messages, I couldn't figure out how to fix.

When Trans. profile is complaining, magnet links work from Firefox, open in Trans.  But I get a line similar to below, but allowed.
When Trans. profile is enforced, magnet links don't ask to open with Transmission. 
No problem with torrent files, though. And I get this in messages:

```
Aug 21 10:46:52 mini1012 kernel: [ 2682.813007] type=1400 audit(1313938012.696:49): apparmor="DENIED" operation="file_mprotect" parent=1 profile="/usr/bin/transmission" name="/usr/bin/transmission" pid=2905 comm="transmission" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```I have to figure out what the IDs are referring to and allow right?
Oops, there's my inexperience showing! :(

A link to a similar problem solved would be a fine answer.
Any help appreciated, dudes.

[COLOR=Lime][COLOR=Green]EDIT: something to do with ps or pstree or ptrace commands? am searching . . .
Found the following in my bookmarks LOL, but can become more independent of others' work when I know more about the above.
[/COLOR][/COLOR][Transmission profile in Share your AppArmor Profiles - thank you DanneStrat! ]("http://ubuntuforums.org/showthread.php?t=1008911&highlight=debugging+apparmor&page=11") 
 
MiniT

----------------------------------
you guys:guitar:

---

### Post by MiniT on 2011-08-21
Ah . . HAAHH!:shock:  made it work. (tranny profile from above).

I am not absolutely sure of the meaning of the newer execute permissions.  (Known - mrkwl + a.  Got - ix, px, Px, ux, Ux.)  But what does PUx and other combos do?

[COLOR=Blue]EDIT: RE: "PUx, etc."  see my post further down, found some explanation in dev mailing list[/COLOR]

RE: the transmission profile - I made something work.
The long way round - used logprof to fiddle with stuff and don't dig it, but that's another story.
One of it's suggestions to fix my Transmission profile was to include a ubuntu-bittorrent-client abstraction - nope.  But hat has the execute line I needed for Firefox to call up (execute) Transmission, to open a magnet link or torrent file.  Thought there was a problem with the trans. profile, looking in the wrong place:  LOL. :D

So "r" is obvious, and documented, but "PUx" is another matter . . . ?  [COLOR=Blue] see later post[/COLOR]
Seems like - use an existing profile, scrub environment, but also don't confine.. . ?   Could use a shove in the right direction here, boss.  Doesn't seem to be documented yet (where I'm looking :) ), though I see many signs of new growth.

As always, thanks and peaceful days to you.
You'ns rock.

--------------------------------------------------------------------

Looking forward to posting a few profiles for new versions of progs.  
I can be proud of myself even if nobody uses them - hehe.

---

### Post by bodhi.zazen on 2011-08-21
> **MiniT said:**
> Ah . . HAAHH!:shock:  made it work. (tranny profile from above).

I am not absolutely sure of the meaning of the newer execute permissions.  (Known - mrkwl + a.  Got - ix, px, Px, ux, Ux.)  But what does PUx and other combos do?

RE: the transmission profile - I made something work.
The long way round - used logprof to fiddle with stuff and don't dig it, but that's another story.
One of it's suggestions to fix my Transmission profile was to include a ubuntu-bittorrent-client abstraction - nope.  But hat has the execute line I needed for Firefox to call up (execute) Transmission, to open a magnet link or torrent file.  Thought there was a problem with the trans. profile, looking in the wrong place:  LOL. :D

So "r" is obvious, and documented, but "PUx" is another matter . . . ?
Seems like - use an existing profile, scrub environment, but also don't confine.. . ?   Could use a shove in the right direction here, boss.  Doesn't seem to be documented yet (where I'm looking :) ), though I see many signs of new growth.

As always, thanks and peaceful days to you.
You'ns rock.

--------------------------------------------------------------------

Looking forward to posting a few profiles for new versions of progs.  
I can be proud of myself even if nobody uses them - hehe.

The documentation on apparmor is hard to find sometimes.

See the bottom section on this page :

[http://www.linuxtopia.org/online_books/opensuse_guides/apparmor_guide/apparmor_bx5bmkc.html](http://www.linuxtopia.org/online_books/opensuse_guides/apparmor_guide/apparmor_bx5bmkc.html)

---

### Post by MiniT on 2011-08-22
Yes!  An excellent explanation.:KS
Here is why I ask.

[COLOR=Blue]Edit: Found an answer in archive of dev mailing list - hopefully helpful.[/COLOR]
[https://lists.ubuntu.com/archives/apparmor/2011-April/](https://lists.ubuntu.com/archives/apparmor/2011-April/)

I have seen Pxr, pxr, rix, et al.
But in ubuntu-bittorrent-clients file (abstraction), I found this!
```
#
# abstraction for allowing graphical bittorrent clients in Ubuntu
#
  /usr/bin/azureus PUxr,
    . . .
  /usr/bin/transmission PUxr,
```
[COLOR=Red]In fact, almost all progs listed in the default abstractions I have are called this way.[/COLOR]
From the linuxtopia page you linked, in reference to "px":
> Incompatible with Ux, ux,        Px, and ix.Each of these five is incompatible with the others,
and _assuming_ that the abstraction's rules are written "legally",  [COLOR=Blue]apparently so[/COLOR]
I must deduce this:
# PUxr = (Pxr  OR  Uxr is allowed) 
# If there is a profile it MUST be used. 
# If there is not a profile, let [BT client] run unconfined. 
# Either way, scrub the environment variables. 

[COLOR=Blue]RE: environment variables - apparently the first bit, P of Pux, sets whether env. vars are kept or not.  Not 100% if this is still the case.[/COLOR]

[COLOR=Black]PLEASE do set me straight if I've strayed there.[/COLOR]

Doesn't it make sense to get rid of the "U"s there?
[COLOR=Blue]Surely in the case of torrent clients or other net facing executables?[/COLOR]
Is that probably another case of permissiveness built in?
_I can appreciate the desire not to restrict an end user's (someone else's) program functionality while they work on local authoring._  But I prefer to break my toys, only to put them back together stronger.
(In fact, I am gaining great respect for Jamie and others who's names are all over the profiles in my apparmor profiles pkg.)

Again, please set me straight if you would.

As always thank you kindly,
and . . .
you rock! :D
--------------------------------------------------------------
LinuxMint10 Julia (pretty clone of Ubuntu 10.10)
AppArmor version 2.5.1

---

### Post by MiniT on 2011-08-22
Another post because I din't ask very well a while ago.
When I see this:
```
Aug 21 10:46:52 mini1012 kernel: [ 2682.813007] type=1400 audit(1313938012.696:49): apparmor="DENIED" operation="file_mprotect" parent=1 profile="/usr/bin/transmission" name="/usr/bin/transmission" pid=2905 comm="transmission" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```How would you go from that to a rule?
Does it require more information?
I guessed well, basically, and the fix worked.  (To open magnet link with transmission, FF needs permission to run Transmission.)
[COLOR=Red]But no idea what the connection between message line(above) and my fix!?[/COLOR]

Sometimes the log lines say, [COLOR=Blue]forgive the shorthand,[/COLOR] "DENYed" - "/directory/file"
and it's [COLOR=Blue]obvious what to correct[/COLOR] for simple file access.
[COLOR=Red]This is much less obvious.[/COLOR]

Is this a case for logprof?  I don't like her so much, but . . .
It would be better if I can crawl into the machine a bit and understand why she is telling me these off-the-wall suggestions.

If only I could go from the code in log messages to human, preferably English. :icon_frown:

As always, I am grateful for the guidance
MiniT:D
--------------------------------------------------------------
LinuxMint10 Julia (pretty clone of Ubuntu 10.10)
AppArmor version 2.5.1

---

### Post by peterj1974 on 2011-09-03
Hello - I've just started using apparmor and it's driving me mad - I hope someone can help.
I'm running ubuntu 11.04 and have created a profile for apache2. The profile is called /etc/apparmor.d/usr.lib.apache2.mpm-prefork.apache2. I ran the profile in complain mode for a bit - did a bit of surfing on the web etc and then ran sudo aa-logprof. I could see that my profile was updated. I then set the profile to enforce. All looked good until I tried to restart apache - the stop and start failed. In /var/log/syslog I could see a couple of denied messages so I put profile back into complain mode, stopped and started apache (which ran fine) and then ran aa-logprof again. Put profile back in enforce mode and same issue - could n't stop and start apache.
 
So I manually added the files in was complaining about to the profile and then ran the command sudo apparmor_parser -r /etc/apparmor.d/usr.lib.apache2.mpm-prefork.apache2.
I tried the apache restart again and it failed - this time syslogs showed different files. I've been manually adding to the profile for nearly an hour now.
 
Anyone had this problem where complain mode doesn;t fully update the profile - or am I doing something wrong?
 
Thanks
 
Pete

---

### Post by jgoguen on 2011-09-05
Apache is a web server, so just browsing the Internet won't give you a proper profile for Apache. You need to exercise your own server, not other people's servers. Things like loading pages from your own server, making it execute scripts and anything else you expect it to be doing during its normal operation.

That said, I also look at aa-logprof as a way to generate a starting profile. It doesn't (in my opinion) tend to give you a profile that can be used as-is; you still need to go through the generated profile and clean it up. Usually, that means taking an educated guess about which profile entries can be removed, loosened up or tightened and reading the logs when things don't work right to see what you should add to your profile. It's very rare that you could take software as complex as Apache and right away get a perfectly working profile with aa-logprof.

In general, you should start with less complicated programs and generate good profiles for them before attempting something as complex as Apache. Try starting with Empathy or Evince (which has a profile in /etc/apparmor.d/ already, so you could refer to that to start) first and then move to more complex software. Firefox is an example of one that can take a bit to get right and is rarely customized the same way by many people. Apache adds an additional layer of complexity by allowing you to load mod_apparmor and take advantage of AppArmor's concept of "hats"; see [http://wiki.apparmor.net/index.php/Mod_apparmor](http://wiki.apparmor.net/index.php/Mod_apparmor) for a good starting point.

Once you've had some time to investigate other profiles and tweak your generated Apache profile, if you're still having problems please feel free to post your profile here (enclosed in code tags) and I'm sure the great group of people around here would be happy to help you move along.

---

### Post by Azrael84 on 2011-10-29
I have written a profile for firefox that seems to work (although it is probably a little lax at this stage)

One thing I am slightly confused about is "rix" against executables, I know ix means inherit parents profile and r means read only, but why would not just ix?

Another thing I keep seeing in the logs is "/run/shm/pulse-shm-3405496852" where the number at the end changes, and read access is requested. I haven't allowed this and all seems to work, but I am curious as to what it wants as it is cluttering the logs.

Finally in order to read a pdf in firefox with adobe I had to add: 
   /usr/bin/dirname rix,
   /usr/bin/test rix,
   /bin/sed rix,
   /usr/bin/expr rix,
   /bin/pwd rix,
   /usr/bin/cut rix,
   /bin/cat rix,
   /bin/uname rix,
   /bin/rm rix,
   /bin/mkdir rix,   
   /bin/cp rix,
Is this normal that it would need all these functions? 

Thanks

---

### Post by MiniT on 2011-11-09
hey there Azrael

I just got a new system set up and haven't had time to look through AppArmor files for a few.
If  any of the below is elementary or more basic than you're asking for,  please pardon since I don't know what level you are at - and I'm hardly  Master at this - just friendly.

Seems you have another issue besides what you are asking for.
As  the heavyweights in the Ubuntu security area will tell you, Firefox is  not an easy one to start with.  They will encourage you to start with  something much less connected and simpler.

I also started with the Firefox - to my chagrin.
Here is the way I approached, so you can save some misery trying to do it from scratch:
There  are profiles posted in another thread here from folks with more  experience.  Read through them and read through al the info you can find  on how this AppArmor thing works - and you'll be able to decide what  needs to be tweaked.  See endof post for helpful links. 
It is safe to start with the default profiles that are part of a package (called AppArmor profiles? maybe? No remember).
The default profiles are pretty open, but safer than NO App Armor was!
Set  to complain, watch logs, try to connect what you do at one second and  what the log says.  For instance, see what the log says when you open  the PDF from in Firefox.
Nothing? Then no rule violation.  Is that OK  with you?  Do you maybe want a rule that says Firefox can't open PDFs  from your Documents folder?  You can write a rule that Denies that.  

Executes are a little more tricky.  Definitely requires much study, on your part.
Please see some friendly links at end of post.

I remember Adobe causing an extra wrinkle in this profile business.
As  long as it is acting as an addon, it is within your Firefox AppArmor  profile and rules for its actions fall within that.  When Firefox calls  up a seperate binary or program on your filesystem, then tell it to  inherit profile, or write a new one for it.

SO, long story short . . .

The  best info to give if you want a good guidance about your issue, is to  attach or somehow post your profile here, then describe or also post the  part of the log that is troubling you.  For instance, what led you to  believe you have to give those permissions? Did /var/log/messages  contain an apparmor line that you interpreted as saying you had to give  that permission?

Hopefully some of this was helpful at least?
Goodluck and try these!  
Be careful of accuracy, check details at two sources if possible.

mini

in no particular order
[Mandatory access control - Wikipedia, the free encyclopedia]("http://en.wikipedia.org/wiki/Mandatory_access_control") 
[Securing Debian Manual]("http://www.debian.org/doc/manuals/securing-debian-howto/") 
[[ubuntu] AppArmor enforce program without logging - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1733231") 
[Main Page - AppArmor]("http://wiki.apparmor.net/index.php/Main_Page") 
[AppArmor Detail - openSUSE]("http://old-en.opensuse.org/AppArmor_Detail")
[SDB:AppArmor geeks - openSUSE]("http://en.opensuse.org/SDB:AppArmor_geeks") 
[[all variants] Introduction to AppArmor - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1008906") [U]
[/U][[SOLVED] Help debugging apparmor profile - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1698800")
[[all variants] Share your AppArmor Profiles - Page 10 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1008911&page=10") 
[AppArmor - Community Ubuntu Documentation]("https://help.ubuntu.com/community/AppArmor") 
[AppArmor - Ubuntu Wiki]("https://wiki.ubuntu.com/AppArmor") 
[[SOLVED] How to test that Apparmor is working? - Page 2 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1591314&page=2") 
[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.10/usr.bin.firefox](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.10/usr.bin.firefox) 
[linuxtopia.org]("http://www.linuxtopia.org/online_books/opensuse_guides/apparmor_guide/apparmor_bx5bmkc.html")

---

### Post by MiniT on 2011-11-09
@Azrael-

BTW - pulse is almost certainly PulseAudio (pulsecookies?) so it is just your audio abstraction.  Is this being denied?  Or is your complaining profile saying something, so it would deny if enforced?  You will want to find out why that is not allowed - maybe allow so when enforced profile - you don't lose sounds!  I don't think its serious at all.

And another thought on your list of permissions:
Did you have acopy of the default profile from the developers - the one that comes as part fo the package - to compare to?  There might be a mistake in yur tweked version, a deleted line?  Also check to make sure you are INCLUDing all you should be.  Those default files save a TON of work. Yea developers, you guys rock!!!!

good luck - only trying to help  :)
mini

---

### Post by vasa1 on 2011-11-10
I'm quite new to Linux (despite the date I joined the forum).
I'm on Ubuntu 11.10 and am trying to learn to get AppArmor going with Firefox 7.
To that end, I've installed **apparmor-notify** and **auditd** from USC.
Since the Firefox profile supplied with the 11.10 installation doesn't run by default, I ran ```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
```
On examining /var/log/audit/audit.log, the only "denied" message I saw was like this: ```
type=AVC msg=audit(1320823528.107:31): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/firefox-7.0.1/firefox{,*[^s][^h]}" name="/proc/4540/statm" pid=4540 comm="firefox" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
```
I then modified /etc/apparmor.d/local/usr.bin.firefox to look like this:
```
# Site-specific additions and overrides for usr.bin.firefox.
# For more details, please see /etc/apparmor.d/local/README.
/proc/*/statm r,
```
I then ran ```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
```
Now, I do not see anymore "denied" messages in the audit.log.

My question is this: have other people seen the same type of "denied" message when confining Firefox and using the default profile? If they have, how did they deal with it? If the rule I used is the way to go, will the devs consider incorporating it in the main profile (/etc/apparmor.d/usr.bin.firefox) so that the profile is more usable out of the box?

Needless to say, with the current profile I checked that I can use Firefox, my extensions (Stylish, DOM Inspector, DownThemAll, SimpleBlock) and plug-ins (Flash and IcedTea) without any problems.

---

### Post by bodhi.zazen on 2011-11-10
> **vasa1 said:**
> My question is this: have other people seen the same type of "denied" message when confining Firefox and using the default profile? If they have, how did they deal with it? If the rule I used is the way to go, will the devs consider incorporating it in the main profile (/etc/apparmor.d/usr.bin.firefox) so that the profile is more usable out of the box?

Needless to say, with the current profile I checked that I can use Firefox, my extensions (Stylish, DOM Inspector, DownThemAll, SimpleBlock) and plug-ins (Flash and IcedTea) without any problems.

Apparmor makes  fair amount of noise in your logs.

It is then up to you to monitor you logs and decide what to do.

The questions to ask yourself is:

1. Is the application working ? Does the application need to access the resource ?

2. Would you prefer your application to have minimal access and make a lot of noise in your logs ?

Or do you prefer to give your application full access to all "normal" activities and log only when there is unexpected behavior ?

So, after answering those questions you can decide.

If your application is broken, you need to fix it.

If the application is working, and you do not mind noise in the logs or you do not wish to monitor your logs, you do not need to do anything.

If your application is working, and you wish to monitory your logs, then yes you will need to evaluate and address this noise. Is it a "false positive" ? If so correct the profile.

Note: It is not a false positive until you have investigated the log and determined that the access that was denied is both normal and acceptable to you.

As you might imagine, only you can decide how you wish to manage apparmor.

Firefox is a poor example as it is a large and complex program, and many people use it for many things, so it requires fairly extensive system access.

Start with a smaller application and work up to firefox.

---

### Post by gwrt78 on 2011-11-21
The following lines appears in syslog when I load the Java applet for my home banking. I have tried to add the line "**owner @{HOME}/.mozilla/firefox/profiles.ini r,**" to both "**/etc/apparmor.d/usr.bin.firefox**" and "**/etc/apparmor.d/abstractions/ubuntu-browsers.d/java**",  just to get started solving the problem, but this doesn't do anything as profiles.ini still cannot be read.

```
apparmor="DENIED" operation="open" parent=3018 profile="/usr/lib/firefox-7.0.1/firefox{,*[^s][^h]}//browser_openjdk" name="/home/gwrt78/.mozilla/firefox/profiles.ini" pid=3063 comm="java" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
apparmor="DENIED" operation="open" parent=3018 profile="/usr/lib/firefox-7.0.1/firefox{,*[^s][^h]}//browser_openjdk" name="/dev/random" pid=3115 comm="java" requested_mask="ac" denied_mask="ac" fsuid=1000 ouid=0
apparmor="DENIED" operation="open" parent=3018 profile="/usr/lib/firefox-7.0.1/firefox{,*[^s][^h]}//browser_openjdk" name="/" pid=3121 comm="java" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```Any suggestions on to what file I should add the line?

---

### Post by Laiquendi on 2013-04-11
Forgive me necromancy, but this is the core of the question actually - why most topics dealing with apparmor went dead? No new profiles, less and less answers - is apparmor being abandoned - any other better solution came up?

---

### Post by Soul-Sing on 2013-04-11
There used to be a sharing of profiles. But ubuntu comes with default profiles, which are in dev.

---

### Post by wildmanne39 on 2013-04-19
Thread closed. Please do not post in old threads.

---

