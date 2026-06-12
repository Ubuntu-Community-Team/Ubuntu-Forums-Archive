---
title: "Introduction to AppArmor"
date: 2008-12-12
forum: Security
---

### Post by bodhi.zazen on 2008-12-12
[FONT=Times New Roman][SIZE=6][CENTER]Introduction to AppArmor[/CENTER]
[/SIZE][CENTER]

[IMG]http://geek.linuxman.pro.br/images/apparmor.jpg[/IMG][/CENTER]


[SIZE=4]Contents[/SIZE]


[LIST]
[*]Post 1 Introduction (This is it).
[*][Post 2]("http://ubuntuforums.org/showpost.php?p=6353894&postcount=2") AppArmor on Ubuntu.
[*][Post 3]("http://ubuntuforums.org/showpost.php?p=6353899&postcount=3") Anatomy of a Profile.
[*][Post 4]("http://ubuntuforums.org/showpost.php?p=6353900&postcount=4") Generating Profiles.
[/LIST]



[SIZE=4]Introduction[/SIZE]


The intent of this post is to increase awareness of AppArmor and encourage it's use by Ubuntu users. Although there are portions of this post that may seem quite technical, it is not my intent to give a full technical review of the workings of AppArmor or compare AppArmor to alternate options, such as [SELinux]("http://www.nsa.gov/selinux/").

From the Novell site :

> &#65279;AppArmor is designed to provide easy-to-use application security for both servers and workstations. Novell AppArmor is an access control system that lets you specify per program which files the program may read, write, and execute. AppArmor secures applications by enforcing good application behavior without relying on attack signatures, so it can prevent attacks even if they are exploiting previously unknown vulnerabilities. AppArmor is a security tool and uses name-based mandatory access controls to restrict or confine system access by "at risk" applications. "At risk" applications generally include both server and client applications with network access. In this post I will use Firefox as an example.

The goal is to apply application specific rules or "profiles" to "confine" Firefox, or any other application, to only the directories, files, and posix 1003.1e draft capabilities needed for normal functioning. In the event Firefox is compromised, Apparmor's confinement  helps to prevent the compromising of the system as a whole.

AppArmor is a powerful program and, when an application is confined, AppArmor can restrict the activity of even the root user. AppArmor was designed as an alternative to SELinux and is designed to be easier to use.

AppArmor is configured by writing a profile for an application. Profiles are written one application at at time and and typically targeted at applications which have network access. These profiles are a text files which restrict or confine an application. These restrictions are in addition to the standard Linux permissions. For example, you can not give access to a directory or file with AppArmor if such access violates the permissions. 

Let us imagine, for example, your browser, Firefox, is hijacked (due to some flaw in the code). Let us also imagine the cracker may then use Firefox to access your home directory or system files, allowing him or her to read and modify system files and/or execute arbitrary code. This hypothetical flaw in Firefox then leads to an escalation of privileges and root access is obtained.

The "traditional" security model would remedy the problem by first correcting the flaw in the code (ie a "security update" for Firefox) and possibly result in a new rule for HIDS, such as viruses scanners or root kits.

The problem with this model it it does nothing to protect against the next attack, aka a [Zero Day Attack]("http://en.wikipedia.org/wiki/Zero-Day_Attack"). AppArmor adds another check to the system, asking the question, should Firefox be accessing or making changes to system files ? AppArmor confines Firefox and if there is a new exploit, AppArmor will help prevent any escalation of privileges.



[SIZE=2][SIZE=2][COLOR=navy][/size][size=4]I set up a collection of AppArmor profiles [/COLOR][here]("http://bodhizazen.net/Tutorials/aa/") . [COLOR=navy]Additional contributions are welcome (PM me if interested).[/COLOR][/SIZE]

References[/SIZE]

[http://en.wikipedia.org/wiki/Selinux](http://en.wikipedia.org/wiki/Selinux)
[http://en.wikipedia.org/wiki/AppArmor](http://en.wikipedia.org/wiki/AppArmor)
[https://help.ubuntu.com/8.04/serverguide/C/apparmor.html](https://help.ubuntu.com/8.04/serverguide/C/apparmor.html)
[http://www.linux.com/feature/58789](http://www.linux.com/feature/58789)
[http://www.linuxtopia.org/online_books/opensuse_guides/apparmor_guide/index.html](http://www.linuxtopia.org/online_books/opensuse_guides/apparmor_guide/index.html)[/FONT]

---

### Post by bodhi.zazen on 2008-12-12
[FONT=Times New Roman][SIZE=4]**AppArmor on Ubuntu**[/SIZE]

First, by default AppArmor does very little (and thus with this post I am hoping to change that ...). With a default installation of Ubuntu 8.04 , AppArmor protects only CUPS (Ubutu 9.04 includes 7 profiles by default: dhclient-script (listed twice), dhclient3, cupsd, tcpdump, cups-pdf, nm-dhcp-clinet.action {basically cpus, dhclient, and tcpdump} ).

You can install additional AppArmor-profiles , which will get you started with a few additional applications, but we must also write and customize our own profiles. I will cover Firefox as an example.

To install some additional profiles :

```
sudo apt-get install apparmor-profiles
```Although this installs some additional profiles, they are permissive in that they default to the complain mode (you will need to manually activate them).

Profiles are stored in **/etc/apparmor.d**

On Ubuntu, AppArmor logs profile violations to **/var/log/messages**

Apparmor uses the kernel standard securityfs mechanism load and monitor profiles. 

securityfs is moutned on **/sys/kernel/security** .
**/sys/kernel/security/apparmor/profiles** is a virtualized file representing the currently loaded set of profiles. 

On Ubuntu there are no gui tools to manage or write profiles, so we are talking good old command line tools and editing configuration files. The configuration files are text files and ,with a little reading, are fairly easy to understand.

[SIZE=2]_Profiles_[/SIZE]

Profiles are stored in **/etc/apparmor.d** 

Profiles are names for the application they confine, using the full path, dropping the first / and converting the others to a . Firefox is a bit confusing because /usr/bin/firefox is a link to /usr/bin/firefox-3.0, which in turn is a link to /usr/lib/firefox-3.0.4/firefox.sh (On Ubuntu 9.04 Alpha).

Thus  **/usr/lib/firefox-3.0.4/firefox.sh**
becomes **usr.lib.firefox-3.0.4.firefox.sh**
and is stored in **/etc/AppArmor.d/usr.lib.firefox-3.0.4.firefox.sh**

More on profiles later. 


[SIZE=2]_Enforcement_[/SIZE]

Once a profile is defined it is automatically activated when the application is started. There are 2 modes of operation, complain and enforce.

_complain_ - In complain mode AA monitors applications and logs violations to your profile without restricting or confining the application. I think of this as "Testing" mode.

_enforce_ - In enforce mode AA monitors applications and logs violations to your profile. In the event of a violation, access to the resource is denied and the application is confined.


[SIZE=2]_Start / Stop AppArmor_[/SIZE]

Usage: /etc/init.d/apparmor {start|stop|restart|try-restart|reload|force-reload|status|kill}

Start : sudo /etc/init.d/apparmor start
Stop : sudo /etc/init.d/apparmor stop
reload: sudo /etc/init.d/apparmor reload
Show status: sudo /etc/init.d/apparmor status

and on ...


[SIZE=2]_Additional useful AppArmor commands_[/SIZE]

[COLOR=blue]_Note_: In these examples, | = or. So you may use geprof or aa-gprof (and on).[/COLOR]

Source : [Novell AppArmor Guide]("http://www.novell.com/documentation/AppArmor/book_opensuse_aaquick21_start/index.html?page=/documentation/AppArmor/book_opensuse_aaquick21_start/data/article_book_book_opensuse_aaquick_start.html")


**genprof | aa-genprof**
> &#65279;Generate or update a profile. When running, you must specify a program to profile. If the specified program is not an absolute path, genprof searches the $PATH variable. If a profile does not exist, genprof creates one using autodep. Syntax : sudo genprof application
Example sudo genprof firefox
This generates a profile for firefox at /etc/apparmor.d/usr.lib.firefox-3.0.4.firefox.sh


**autodep | aa-autodep**
> &#65279;Guess basic AppArmor profile requirements. autodep creates a stub profile for the program or application examined. The resulting profile is called *approximate because it does not necessarily contain all of the profile entries that the program needs to be confined properly. *
**complain | aa-complain**
> &#65279;Set an AppArmor profile to enforce mode from complain mode.syntax : complain rule 
Example : sudo complain firefox


**enforce | aa-enforce**
> &#65279;Set an AppArmor profile to enforce mode from complain mode.syntax : enforce rule 
Example : sudo enforce firefox


**unconfined | aa-unconfined**
> &#65279;Output a list of processes with open tcp or udp ports that do not have AppArmor profiles loaded.
**logprof | aa-logprof**
> &#65279;Manage AppArmor profiles. logprof is an interactive tool used to review the learning or complain mode output found in the AppArmor syslog entries and to generate new entries in AppArmor profiles. 
Translation: search your logs for problems and use this information to modify the firefox profile.


**apparmor_parser**

This is used to load, or more commonly reload a profile into the kernel. After modifying (editing) a profile use :

```
sudo apparmor_parser -r /etc/apparmor.d/<profile>
```Where "<profile>" is the profile to re-load.

If you prefer you can restart AppArmor (same as reload) ```
/etc/init.d/apparmor restart
```[/FONT]

---

### Post by bodhi.zazen on 2008-12-12
[FONT=Times New Roman][size=4]**Anatomy of a Profile**[/size]

Now we are getting into the nitty gritty :twisted:

Each application you wish to confine under AppArmor is given a profile which is stored in the
/etc/AppArmor.d directory.

Each profile is named after the application to which it applies, changing the / in the path to a . (the first / is simply dropped).

So, /usr/lib/firefox-3.0.4/firefox.sh becomes **usr.lib.firefox-3.0.4.firefox.sh**.

Profiles are nothing more then text files and are generated by you the user sometimes with the assistance of AppArmor tools from the command line (sorry no GUI in Ubuntu, although there is a GUI in YAST on OpenSUSE). They can be viewed and manually managed (tweaked) with any editor (gedit, nano, vim, etc). I will walk you through generating a profile for firefox in the next post.

Profiles are comprised of &#65279;4 sections #include, capability entries, rules, and hats.

_[size=2]# include_[/size]

#include is akin to sourcing or libraries and allows you to generate a list of common restrictions. Rather then writing this list over and over in profiles, you can keep it in a common location and incorporate it into a profile with an #include. When you update the common list, all your profiles are updated.

 
_[size=2]Capability entries_[/size]

In English, this is permission checking.

In Geek speak :

> &#65279;Capabilities statements are simply the word capability followed by the name of the POSIX.1e capability as defined in the capabilities(7) man page.

And, if you are interested, [capabilities(7) man page](http://linux.die.net/man/7/capabilities).


_[size=2]Rules_[/size]

These are basically a set of permissions applied to files or directories. The syntas is a path followed by a set of rules.

[path] [rules]

path

You may use Globing or special characters in the path.

&#65279;
```
*  Substitutes for any number of characters, except /. 

** Substitutes for any number of characters, including /. 

?  Substitutes for any single character, except /. 

[ abc ] Substitutes for the single character a, b, or c. 

[ a-c ] Substitutes for the single character a, b, or c. 

{ ab,cd } Expand to one rule to match ab and another to match cd. 

[ ^a ] Substitutes for any character except a.
```


Rules for files include

```
r = read
w = write
l = link
k = lock
a = append
```

Rules for executable (applications) include

```
ix = inherit = Inherit the parent's profile.
px = requires a separate profile exists for the application, with environment scrubbing.
Px = requires a separate profile exists for the application, without environment scrubbing.

ux and Ux = Allow execution of an application unconfined, with and without environmental scrubbing. (use with caution if at all).

m = allow executable mapping.
```

For a more detailed explaination see the man page : [AppArmor(5)](http://man-wiki.net/index.php/5:AppArmor.d)

Example (from the above man page)

> &#65279;
# a variable definition
              @{HOME} = /home/*/ /root/
 
              # a comment about foo.
              /usr/bin/foo {
                /bin/mount          ux,
                /dev/{,u}random     r,
                /etc/ld.so.cache    r,
                /etc/foo.conf       r,
                /etc/foo/*          r,
                /lib/ld-*.so*       x,
                /lib/lib*.so*       r,
                /proc/[0-9]**       r,
                /usr/lib/**         r,
                /tmp/foo.pid        wr,
                /tmp/foo.*          lrw,
                /@{HOME}/.foo_file  rw,
 
                # a comment about foo's subprofile, bar.
                ^bar {
                  /lib/ld-*.so*       x,
                  /usr/bin/bar        ix,
                  /var/spool/*        rwl,
                }
              }

Comments :

[list=number][*]Note the use of variable. This is only necessary if you mount your /home partition in a non-standard location.
[indent]" /@{HOME}/.foo_file"[/indent]
[*]Comments start with an octothorpe (#).
[*] /etc/foo/*          r,
[indent]Allows read access to the files in /etc/foo[/indent]
[indent]/etc/**  would allow read access to all sub-directories in /etc[/indent][/list]


_[size=2]Hats_[/size]

While an AppArmor profile is applied to an application, there are times with a sub process of the program may need access differing from the main program. In this event, the sup process may "change hats" or use an alternate sub-profile.

A profile may have more then 1 sub-profile, however the sub-profiles may not have sud-sub profiles (if that makes sense). 

Right now very few applications use hats, and one example is Apache. 

For a more detailed explanation see 

man AppArmor
man AppArmor.d[/FONT]

---

### Post by bodhi.zazen on 2008-12-12
[FONT=Times New Roman][SIZE=4]**Generating Profiles**[/SIZE]

By default, Ubuntu includes a profile only for CUPS. You can install a few additional profiles with

```
sudo apt-get install apparmor-profiles
```The additional profiles are :

usr.sbin.avahi-daemon , usr.sbin.nmbd , bin.ping, sbin.klogd , usr.sbin.nscd , sbin.syslogd , usr.sbin.dnsmasq, usr.sbin.ntpd , sbin.syslog-ng, usr.sbin.identd , usr.sbin.smbd , gdm-guest-session , usr.sbin.mdnsd , and usr.sbin.traceroute

Also included are some information for #includes in /etc/AppArmor.d/abstractions directory.

_Note_: After you generate a new profile, or edit an existing  profile, the profile must be (re)loaded into the kernel and the application to which it applies must be restarted. The can be performed by restarting the application or rebooting.

```
sudo apparmor_parser -r /etc/apparmor.d/<profile>
```Where "<profile>" is the name of the profile to reload.

As promised, let us generate a profile for firefox.

First, close firefox.

Next run ```
sudo genprof firefox
```This will generate a "basic" profile for Firefox and place it into complain mode. You will be able to run Firefox and any violations of the profile will be logged.

I suggest you start by reviewing the profile for Firefox and add what you can.

Now lets follow the logs while we take Firefox for a spin. Open a terminal and enter

```
tail -F /var/log/messages
```The next step, with the AppArmor profile for Firefox still in complain mode, start Firefox and perform "normal activities". Open and close Firefox, browse some web sites, download some simple files, browse local files, etc. This will vary from one setup to another and we do not all use Firefox in the same way.

During this trial period you will see a variety of error messages flash in the terminal where your are following /var/log/messages. Initially you will get an overwhelming number, that is OK, work through the error messages one at at time, modify your profile, quit Firefox, reload your profile and work on the next set of messages.

If you get stuck and do not understand what to add, use aa-logprof. I suggest you make a backup of your current profile first (keep backups outside of /etc/apparmor.d):

```
sudo cp /etc/apparmor.d/user.lib.firefox-3.0.4.firefox.sh /root/user.lib.firefox-3.0.4.firefox.sh
```Next,```
sudo aa-logprof firefox
```This will search your logs and modify your profile on the basis of how you answer the resulting questions. 

_Note_: aa-logprof is a bit unrefined and you should review and edit the resulting changes in the profile manually.

My final profile was (Ubuntu 9.04 Alpha, FF 3.0.4):

> # Last Modified: Thu Dec 11 21:08:14 2008
#include <tunables/global>

/usr/lib/firefox-3.0.4/firefox.sh {
  #include <abstractions/base>
  #include <abstractions/bash>
  #include <abstractions/consoles>
  #include <abstractions/gnome>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>

  network dgram,
  network stream,

  /bin/dash rix,
  /bin/grep rix,
  /bin/ps rix,
  /usr/bin/basename rix,
  /usr/lib/firefox-3.0.4/firefox mrix,
  /usr/lib/gamin/gam_server mrix,

  /dev/shm/ r,
  owner /dev/shm/pulse-* rw,
  /etc/ r,
  /etc/firefox-3.0/pref/ r,
  /etc/firefox-3.0/pref/* r,
  /etc/gre.d/ r,
  /etc/gre.d/1.9.0.4.system.conf r,
  /etc/mime.types r,
  /etc/pulse/client.conf r,
  /etc/sound/events/gtk-events-2.soundlist r,
  /etc/xulrunner-1.9/system-greprefs.js r,
  owner /home/** rw,
  owner /home/*/.adobe/ rw,
  owner /home/*/.adobe/** rw,
  owner /home/*/.config/gtk-2.0/** rwk,
  owner /home/*/.macromedia/ w,
  owner /home/*/.macromedia/** rw,
  owner /home/*/.mozilla/** rwk,
  owner /home/*/.pulse-cookie rwk,
  owner /home/*/.pulse/ w,
  owner /home/*/{Desktop,Documents,Downloads}/ rw,
  owner /home/*/{Desktop,Documents,Downloads}/** rw,

  owner /proc/*/maps r,
  /proc/*/mounts/* r,
  owner /proc/*/stat r,
  /proc/version r,
  /usr/local/share/** r,
  /usr/share/** r,
  /var/lib/dbus/machine-id r,

}_Note_: If you use this profile you will probably NOT be able to browse local files and / or pictures etc.

Generating a profile is thus an active process an one where you can learn what "normal functioning" of Firefox entails. There are only really two mistakes you can make:

1. Too restrictive. In extreme cases Firefox will not run (when Apparmor is in the enforcing mode).

2. Too permissive. Keep in mind, however, that before you make a profile Firefox had relatively unfettered access to your system. Also standard Linux permissions still apply.

Some helpful globs:

/home/*/

/usr/share/** r
/usr/local/share/** r

When you are ready, put the Firefox profile into enforcing mode. Watch your log and re-start Firefox. You may need to further modify your profile.

As with any application, as you use AppArmor you will get a feel for how it works and how to write efficient Profiles.

[COLOR=darkred]**DON'T FORGET to reload a profile after editing it.**[/COLOR]

```
sudo apparmor_parser -r /etc/apparmor.d/<profile>
```Or if you prefer, ```
/etc/init.d/apparmor restart
```
I would also like to start a thread :

[Share your AppArmor Profiles]("http://ubuntuforums.org/showthread.php?p=6353911")[/FONT]

---

