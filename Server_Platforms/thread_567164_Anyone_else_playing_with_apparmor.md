---
title: "Anyone else playing with apparmor?"
date: 2007-10-04
forum: Server Platforms
---

### Post by jdong on 2007-10-04
I've started messing around a bit with Apparmor, doing a bit of preventative security :). I am remarkably impressed at how easy it is to write Apparmor rules, and the little impact it seems to have on the rest of the system (Often times, SELinux feels like turning the whole system upside down, while Apparmor is simpler to focus just on a few vulnerable processes)


Here's my current set of profiles:
```

[jdong@severance:tmp/openSUSE-10.3-GM-DVD-i386-iso]$ sudo aa-status                                                 (10-04 10:29)
apparmor module is loaded.
24 profiles are loaded.
24 profiles are in enforce mode.
   /usr/bin/irssi
   /usr/bin/skype
   /usr/lib/firefox/firefox
   /usr/sbin/traceroute
   /bin/ping
   /usr/sbin/cupsd
   /usr/sbin/mdnsd
   /usr/sbin/avahi-daemon
   /usr/sbin/ntpd
   /usr/sbin/lighttpd
   /usr/sbin/identd
   /usr/bin/ktorrent
   /sbin/ipw3945d-2.6.22-12-generic
   /sbin/klogd
   /usr/sbin/nmbd
   /usr/sbin/dnsmasq
   /usr/sbin/mysqld
   /usr/sbin/smbd
   /usr/bin/pidgin
   /sbin/syslogd
   /sbin/syslog-ng
   /usr/sbin/nscd
   /usr/local/bin/jailbash
   /usr/sbin/named
0 profiles are in complain mode.
14 processes have profiles defined.
14 processes are in enforce mode :
   /sbin/syslog-ng (22364) 
   /usr/bin/skype (9697) 
   /usr/sbin/smbd (304) 
   /usr/sbin/avahi-daemon (5328) 
   /usr/bin/pidgin (10873) 
   /usr/sbin/avahi-daemon (5323) 
   /usr/sbin/smbd (308) 
   /usr/sbin/lighttpd (11527) 
   /usr/sbin/nmbd (302) 
   /usr/sbin/dnsmasq (16876) 
   /usr/bin/irssi (9009) 
   /usr/sbin/ntpd (5987) 
   /usr/sbin/cupsd (6343) 
   /sbin/ipw3945d-2.6.22-12-generic (5252) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.

```

I found a code injection vulnerability in an irssi script that I use, which prompted me to lock down irssi. In addition, lighttpd and dnsmasq were simple to lock down and since they listen on the network and have a history of a few exploits, I thought it'd be worth it.

I don't trust all the extensions I pile on top of Firefox either, as well as things like Flash/Java that I don't understand how good their sandboxes are, so I just sandbox it more.

Finally, closed-source applications like Skype and Intel's ipw3945d daemon get special attention too :)


KTorrent was extremely upset about the limitations I put on it, and it was flooding syslog, so I had to replace syslogd with syslog-ng and do filtering on audit events, discarding KTorrent and a few other offenders.


Anyone else using Apparmor? I'd love to hear your story.

---

### Post by jibazee on 2007-10-20
hi,

i like your postings everywhere in these forums.
seems that popularity boosts masses into ubuntu,
but intelligence doesn't seem to be linked... :-)
i'm trying apparmor in a few days,
then post my results.

have a nice day

jibazee

---

### Post by daimaru on 2007-10-20
@jdong
you seem to know alot about apparmor, me nothing at all :lolflag:
so maybe you can help me. I installed antivir and the dazuko module, but i can only load dazuko module when i disable apparmor. 
```
$ modprobe dazuko
FATAL: Error inserting dazuko (/lib/modules/2.6.22-14-generic/extra/dazuko.ko): Operation not permitted
```

how do you set up a rule for a module to load ? 

thx

---

### Post by jdong on 2007-10-20
Can you look in dmesg for audit: entries?

---

### Post by daimaru on 2007-10-21
here the demsg output:
```

 dmesg | grep audit
[   29.536546] audit: initializing netlink socket (disabled)
[   29.536557] audit(1192979033.372:1): initialized
[   31.325753] AppArmor: AppArmor initialized<5>audit(1192979034.872:2):  type=1505 info="AppArmor initialized" pid=1257
[   43.639254] audit(1192971849.658:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5064 profile="/usr/sbin/cupsd"
[ 1355.875225] audit(1192973164.733:4):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=12845 profile="/usr/sbin/cupsd"
[ 1355.933349] audit(1192973164.733:5):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=12848 profile="/usr/sbin/cupsd"
[ 1467.613385] audit(1192973276.739:6):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=26314 profile="/usr/sbin/cupsd"
[ 1467.629973] audit(1192973276.739:7):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=26319 profile="/usr/sbin/cupsd"
[ 1534.405341] audit(1192973343.743:8):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=2446 profile="/usr/sbin/cupsd"
[ 1534.427242] audit(1192973343.743:9):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=2455 profile="/usr/sbin/cupsd"

```

and my apparmor status output (default from install of gutsy)

```

sudo apparmor_status
[sudo] password for gg:
apparmor module is loaded.
2 profiles are loaded.
2 profiles are in enforce mode.
   /usr/sbin/cupsd
   /usr/lib/cups/backend/cups-pdf
0 profiles are in complain mode.
1 processes have profiles defined.
1 processes are in enforce mode :
   /usr/sbin/cupsd (5064) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.

```

---

### Post by jdong on 2007-10-21
Hmm it does not appear like apparmor is the culprit blocking that module from going in.

---

### Post by /etc/init.d/ on 2007-10-22
I've been stuck on Ubuntu 6.10 for a while now, I figured if it ain't broke don't fix it, but AppArmor is really giving me a reason to upgrade to Gutsy.

I've tried SELinux and grsecurity in the past, and I agree they're too difficult to set up and break too many things, so it's nice to see there's an integrated and supported way.

When I finally take the plunge and upgrade I'll post how I get on :)

---

### Post by matthew on 2007-10-24
I've just started digging through the documentation for apparmor. This looks great! From what I can see, it seems to be a lot easier, and pretty much just as effective as using SELinux. Hopefully I'll have some real free time this week to grok it well.

---

### Post by damatta on 2007-10-24
Is there anywhere I can download profiles to apply on my Gutsy Gibbon?
Particularly firefox, pidgin and a few other default apps.
And how do I apply em?

thanks

---

### Post by jaakan on 2007-10-24
> **daimaru said:**
> @jdong
you seem to know alot about apparmor, me nothing at all :lolflag:
so maybe you can help me. I installed antivir and the dazuko module, but i can only load dazuko module when i disable apparmor. 
```
$ modprobe dazuko
FATAL: Error inserting dazuko (/lib/modules/2.6.22-14-generic/extra/dazuko.ko): Operation not permitted
```

how do you set up a rule for a module to load ? 

thx

You should try sudo aa-logprof if you think it is related apparmor. apparmer could be blocking that or something else it might need to load.

---

### Post by jdong on 2007-10-24
[http://jdong.mit.edu/~jdong/apparmor/](http://jdong.mit.edu/~jdong/apparmor/)

Here's a snapshot of my apparmor.d -- these rules are probably experimental at best but somewhat work for me :D

---

### Post by damatta on 2007-10-24
Thanks for the share mate :)

---

### Post by inphektion on 2007-10-25
So I started playing with apparmor today.  Here is what I did:

First I grabbed the profiles avail in the universe repos:
aptitude install apparmor-profiles

that gives you a few but unfortuneatley none that I really needed.  

So I figured I'd learn by apparmoring ping...

The profiles live in /etc/apparmor.d/ and config files in /etc/apparmor/
type apparmor_status (should be in path) to see status.
I typed autodep /bin/ping
and that puts ping in complain or learning mode.
after pinging a few things by name and IP to fill the apparmor log I then type logprof to go through the wizard to create the ping profile.  It asks questions and generally you just hit A for accept though if its a dir you know it needs full access to you can hit G for glob.
Once that was saved I typed enforce bin.ping and voila.
I did the same for /usr/sbin/apache2 and is working well.
the apache2 I had to throw into complain mode a few times to get everywhere nagios had stuff but eventually seems good now.

I think that's the basics of apparmor.  Great security tool.

---

### Post by jdong on 2007-10-25
Yep, that's the basic workflow for apparmor rule creation. It's really a breeze.

---

### Post by Jose Catre-Vandis on 2007-10-27
Don't necessarily want to play with it, but it is getting in the way of running one of my programs

I use Geexbox ([www.geexbox.org](www.geexbox.org)) which provide a small program that generates a custom iso of the geexbox open media center.

Apparmor is stopping this from running. Can you tell me how to allow a program to run whilst apparmor is up? Am having to kill apparmor to run the generator. Alternatively, what problems will I face if I uninstall apparmor?

Thx

---

### Post by jdong on 2007-10-27
Can you please paste logs that indicate Apparmor blocking an action? Apparmor assumes an off-by-default mode of operation and unless you explicitly define a rule for a particular executable, it is not restricted in any way.

---

### Post by ice60 on 2007-10-27
apparmor is completely safe to uninstall, it's a kind of application firewall.

i just tried running it like this -
sudo aa-genprof opera
then running opera and doing everything it does like run flash, open a PDF etc, then closing it and telling it to scan the events. i picked inherit and allow with a few globs too lol. this is how my opera profile looks now -

```

# Last Modified: Sat Oct 27 17:14:01 2007
#include <tunables/global>
/usr/bin/opera flags=(complain) {
  #include <abstractions/base>
  #include <abstractions/nameservice>

  capability sys_ptrace,

  /bin/dash ixr,
  /bin/grep ixr,
  /bin/ps ixr,
  /bin/sed ixr,
  /dev/snd/controlC0 rw,
  /dev/snd/pcmC0D0p rw,
  /dev/snd/timer r,
  /dev/tty r,
  /etc/fonts/** r,
  /etc/gnome/defaults.list r,
  /etc/mailcap r,
  /etc/opera6rc r,
  /etc/opera6rc.fixed r,
  /etc/qt3/qt_plugins_3.3rc r,
  /etc/qt3/qtrc r,
  /home/*/.ICEauthority r,
  /home/*/.Xauthority r,
  /home/*/.fonts.conf r,
  /home/*/.icons/** r,
  /home/*/.local/share/applications/* r,
  /home/*/.local/share/icons/ r,
  /home/*/.local/share/mime/* r,
  /home/*/.macromedia/Flash_Player/#SharedObjects/** rw,
  /home/*/.macromedia/Flash_Player/*/ r,
  /home/*/.macromedia/Flash_Player/macromedia.com/support/flashplayer/** r,
  /home/*/.mozilla/firefox/** r,
  /home/*/.opera/** krw,
  /home/*/.qt/* krw,
  /proc/ r,
  /proc/*/cmdline r,
  /proc/*/maps r,
  /proc/*/mounts r,
  /proc/*/stat r,
  /proc/*/status r,
  /proc/cpuinfo r,
  /proc/meminfo r,
  /proc/stat r,
  /proc/sys/kernel/pid_max r,
  /proc/tty/drivers r,
  /proc/uptime r,
  /proc/version r,
  /tmp/* rw,
  /tmp/.ICE-unix/* w,
  /tmp/.X11-unix/* w,
  /usr/bin/evince Px,
  /usr/bin/mplayer ixr,
  /usr/bin/opera mr,
  /usr/lib/** mr,
  /usr/lib/opera/9.24-20071015.6/opera ixr,
  /usr/lib/opera/9.24-20071015.6/works ixr,
  /usr/lib/opera/plugins/operaplugincleaner ixr,
  /usr/lib/opera/plugins/operapluginwrapper ixr,
  /usr/local/share/applications/*.cache r,
  /usr/local/share/icons/ r,
  /usr/share/X11/XErrorDB r,
  /usr/share/X11/XKeysymDB r,
  /usr/share/alsa/alsa.conf r,
  /usr/share/alsa/cards/HDA-Intel.conf r,
  /usr/share/alsa/cards/aliases.conf r,
  /usr/share/alsa/pcm/*.conf r,
  /usr/share/applications/* r,
  /usr/share/fonts/** r,
  /usr/share/gdm/applications/*.cache r,
  /usr/share/icons/ r,
  /usr/share/icons/** r,
  /usr/share/locale-langpack/en_GB/LC_MESSAGES/*.mo r,
  /usr/share/mime/aliases r,
  /usr/share/mime/application/ogg.xml r,
  /usr/share/mime/application/x-flash-video.xml r,
  /usr/share/mime/audio/* r,
  /usr/share/mime/globs r,
  /usr/share/mime/image/x-macpaint.xml r,
  /usr/share/mime/image/x-pict.xml r,
  /usr/share/mime/magic r,
  /usr/share/mime/subclasses r,
  /usr/share/mime/video/* r,
  /usr/share/mimelnk/application/* r,
  /usr/share/opera/** r,
  /var/cache/fontconfig/* r,
  /var/lib/defoma/fontconfig.d/*.conf r,
}
```i know that's the world's worst profile :| can someone help me clean it up a bit?

when i run -
sudo apparmor_status
the programs i profiled are in complain mode, none are in enforcement. has anyone put any of their profiles in enforcement mode yet? ping and traceroute should be safe to enforce. 

i enabled that repository it asks about too, that downloads profiles for you if there's one for the program you are about to profile. i hope it doesn't automatically upload them too lol mine are rubbish :D

there should be a fair few profiles that will be the same on all our computers, we should upload the universially safe ones to this thread for people to use.

---

### Post by Jose Catre-Vandis on 2007-10-27
> **jdong said:**
> Can you please paste logs that indicate Apparmor blocking an action? Apparmor assumes an off-by-default mode of operation and unless you explicitly define a rule for a particular executable, it is not restricted in any way.

It gives this message in dmesg (live)

```
AppArmor: aa_register: Failed to get filename<3>
```

doesn't appear to come through in any logs

---

### Post by arijarot on 2007-11-12
I know how (i.e., the method) to setup an apparmor profile --I have read the manuals (e.g., [http://www.novell.com/documentation/apparmor/apparmor201_sp10_admin/index.html?page=/documentation/apparmor/apparmor201_sp10_admin/data/book_apparmor_admin.html](http://www.novell.com/documentation/apparmor/apparmor201_sp10_admin/index.html?page=/documentation/apparmor/apparmor201_sp10_admin/data/book_apparmor_admin.html), [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor), [http://beginlinux.com/index.php/desktop_training/ubuntu/ubsecure_m/Secure_ub](http://beginlinux.com/index.php/desktop_training/ubuntu/ubsecure_m/Secure_ub)), but I don't know how to choose which things should be allowed, denied, profiled, etc. Is there a guide about making informed decisions/rules for individual programs (e.g., firefox)?

---

### Post by snide on 2007-12-15
Hello

I uninstalled apparmor because it didn't let me run my programs like mugen or hamachi, i tried to make profiles of this programs but the profiles that apparmor autogenerated had a sintax error. :(

---

### Post by simoncifer on 2007-12-18
> **Jose Catre-Vandis said:**
> It gives this message in dmesg (live)

```
AppArmor: aa_register: Failed to get filename<3>
```

doesn't appear to come through in any logs

Sorry to dig up an old thread, but I find out why AppArmor was killing geexbox-generator: it was because geexbox-generator uses a kind of executable compression called UPX, which decompress the executable during run-time, and then run the new file (decompressed version of the executable).  The problem due to the new executable file is in /tmp, so it looks like geexbox-generator is randomly executing a file in /tmp.

I find this out when I try to generate an AppArmor profile for geexbox-generator.

Since the decompressed file in /tmp has a random filename, I couldn't generate a profile.  So, I downloaded UPX and decompressed the geexbox-generator.
```
 upx -d linux-i386-generator 
```

Now geexobox-generator runs, even without specifying an AppArmor profile.  And the file size is now 1120341 byte instead of 639151 byte (so about 1 MB instead of 600 kB).

Hope this help.

Oh, you can search google for UPX, it's actually pretty popular.  I downloaded the TAR file from the website, I just realize that UPX is in the repo.

Can someone post in the GeeXBox forum to let them know about this?  I don't have an account there....

---

### Post by SjRaptor on 2007-12-18
It would be nice to have PaX/grsecurity compiled into the Ubuntu kernel. Why on earth should a kernel *module* (SELinux, AppArmor, LSM) running in *userland* be more *trusted* than security compiled right into the kernel, running in ring 0?

---

### Post by jdong on 2007-12-19
GRSecurity/PaX address different aspects of security though (well, primarily -- grsec does have a MDAC system too). For the purposes of what AppArmor is meant to do, I don't think the fact that it's a security module or configured from userland to be a weakness...

---

### Post by stmurray on 2007-12-19
I am fairly new to Ubuntu, but I just read this thread and it piqued my interest in apparmor.  I noticed that no one seems to have a profile for dhclient (On my machine it is actually dhclient3 that is used).  As dhclient3 seems to always be listening on udp port 68, I figure this is really one of the processes you want to protect. 

I used gen-prof and logprof to create that profile.   The issue I am having that dhclient is shown as "processes are unconfined but have a profile defined", even after a reboot.   (I killed and restarted dhclient3 to create the audit entries to create the profile.)

Assuming I get  a profile and want to use it, will this be an issue ongoing?  Is there a way to get apparmor loaded before dhclient is run?


Thanks!

---

### Post by crazee_canuck on 2007-12-31
> **daimaru said:**
> @jdong
you seem to know alot about apparmor, me nothing at all :lolflag:
so maybe you can help me. I installed antivir and the dazuko module, but i can only load dazuko module when i disable apparmor. 
```
$ modprobe dazuko
FATAL: Error inserting dazuko (/lib/modules/2.6.22-14-generic/extra/dazuko.ko): Operation not permitted
```

how do you set up a rule for a module to load ? 

thx

I know this was a few months ago but your problem was that you were trying to load the module as a regular user (i.e., without sudo or su).

---

### Post by chrisccoulson on 2008-01-10
I've been setting up apparmor profiles on my machine in the last couple of weeks. It seems to be fairly straightforward, but I'm having issues with inherited permissions.

For example, I only allow Firefox to write to the Desktop, which seems to work ok. However, if I open up a file in an external viewer (say for instance, a PDF in Evince), that program doesn't inherit the permissions to write to the Desktop, despite the fact that Evince is listed in my profile for Firefox and has 'ixr' permissions.

The rule that allows Firefox to write the Desktop is specified in an abstraction (user-download), which is listed as a #include in my Firefox profile. I'm having this problem with a lot of my profiles, and I've noticed that the only permissions that aren't inherited are the ones specified in the abstractions.

I'm just wondering if anyone thinks there's something I might have missed, or whether it could be a bug.

---

### Post by jdong on 2008-01-10
Odd, I have things that are ixr and they seem to inherit parent permissions just fine. In fact I have entire restricted shells who operation solely depends on ixr working properly!

---

### Post by chrisccoulson on 2008-01-10
Mine inherit permissions that are explicitly defined in the profile, but inheriting permissions from the abstractions seems a bit flakey. I'll have a look over my profiles over the weekend and see if I can figure anything out.

---

### Post by jdong on 2008-01-10
Oh, I haven't tried abstraction inherit-execute before... maybe it's one of those "it's not a bug it's a security feature" things :D

---

### Post by NickD-NLUG on 2008-01-15
Just to say I'm someone else interested in AppArmor.  I've started running things in complain mode, and I'll start running it in "enforce" soon.

Apart from trawling through the man pages, is there any step by step documentation on this?  I didn't see a lot on the wiki....

---

### Post by pokkets on 2008-03-04
I haven't yet but I might .I have have an unstable hardy A5 that where the upgrade failed, so I put it on a USB to boot so I could 'play' with it, and restored gutsy on my main drive.so I could use wireless.  It seemed like cupsys failed because it couldn't find an apparmor_parser which failed to install, which also led to the failure of desktop upgrades and a few other things which seemed to have related dependencies. I'm on Ubuntu ultimate,1.7 with gnome and kde and have a few other ubuntu desktops. My Gutsy has apparmor.d hardy doesn't Apparmor.d has a reference to cupsd. Launchpad didn't want to know because it :guitar:was Ubuntu ultimate,  (and because I played with that) but I noticed others there had similar problems. While I'm fairly new to Linux, Hardy is set up so I have nothing to lose. Of course I also learned to get a tar file of root quickly.

---

