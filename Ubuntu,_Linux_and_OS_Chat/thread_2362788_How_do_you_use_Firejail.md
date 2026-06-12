---
title: "How do you use Firejail?"
date: 2017-06-02
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2017-06-02
Please mention the version of Firejail and your OS version. The version in the 16.04 repos is a bit old but I'm assuming it's maintained to some extent because of what is near the top of this page: [https://firejail.wordpress.com/download-2/](https://firejail.wordpress.com/download-2/)> Download the latest version:
Firejail development: 0.9.47 (GitHub)
Firejail current: 0.9.46 (SourceForge).
**Firejail Long Term Support: 0.9.38.10** (SourceForge).
Firetools current: 0.9.46 (SourceForge).


It may be  useful to mention the application as well.

Do you just use```
firejail <program_name>
```or do you use any of the many options?

```
       --caps.drop=all
              Drop  all  capabilities  for  the processes running in the sandbox.
              This option is recommended for running GUI programs  or  any  other
              program  that  doesn't  require  root privileges. It is a must-have
              option for sandboxing untrusted programs installed from  unofficial
              sources - such as games, Java programs, etc.

              Example:
              $ firejail --caps.drop=all warzone2100

```seems useful.

Then, there is```
       --overlay-tmpfs
              Mount  a  filesystem  overlay on top of the current filesystem. All
              filesystem modifications go into the  overlay,  and  are  discarded
              when the sandbox is closed.

              OverlayFS  support  is  required in Linux kernel for this option to
              work.  OverlayFS was officially introduced in Linux kernel  version
              3.18

              Example:
              $ firejail --overlay-tmpfs firefox

```which seems useful if you don't want any changes written to your profile or anywhere else (including *~/Downloads*).

*--private* seems to do something similar:```
       --private
              Mount  new  /root  and /home/user directories in temporary filesys&#8208;
              tems. All modifications are discarded when the sandbox is closed.

              Example:
              $ firejail --private firefox

```

I've just started exploring without an understanding of the technicalities involved!

---

### Post by poorguy on 2017-06-02
[URL="https://sites.google.com/site/easylinuxtipsproject/sandbox"][COLOR=#000000]A proven methood.[/COLOR]

https://sites.google.com/site/easylinuxtipsproject/sandbox[/URL]

---

### Post by #&amp;thj^% on 2017-06-02
vasa1 I love firejail....wish I could give you a 18 month self case  test...but usage varies from user to user and application to  application.
Great thread topic though ;) I'll be watching for some insight of my own.
```
firejail --version
firejail version 0.9.44.8

Compile time support:
    - AppArmor support is enabled
    - AppImage support is enabled
    - bind support is enabled
    - chroot support is enabled
    - file and directory whitelisting support is enabled
    - file transfer support is enabled
    - networking support is enabled
    - overlayfs support is enabled
    - private-home support is enabled
    - seccomp-bpf support is enabled
    - user namespace support is enabled
    - X11 sandboxing support is enabled

```
And "man firejail"
netblue is the guy to get the answer's you seek.  [URL="https://github.com/netblue30"]https://github.com/netblue30

[/URL]

---

### Post by TheFu on 2017-06-02
$ firejail --private chromium-browser
firejail version 0.9.38.10

I have used it for shells to play around with newly downloaded applications.

---

### Post by vasa1 on 2017-06-02
> **1fallen said:**
> ...
And "man firejail"
netblue is the guy to get the answer's you seek.  [URL="https://github.com/netblue30"]https://github.com/netblue30

[/URL]Yes, that's a very helpful resource. As a matter of fact, his tip on getting --overlay to work on WiFi was very helpful as I've posted here: [https://ubuntuforums.org/showthread.php?t=2362591&p=13651238#post13651238](https://ubuntuforums.org/showthread.php?t=2362591&p=13651238#post13651238)

I'm now using```
firejail --overlay --dns=8.8.8.8 --dns=8.8.4.4 google-chrome-unstable && firejail --overlay-clean
```because I prefer --overlay over --private. With the former, I have all my browser customization available. --private seems to open a pristine browser, clean profile, clean everything, I've to log into sites afresh, generally more painful.

Apparently, --overlay-tmpfs doesn't work with Chrome/Chromium with the version of firejail for 16.04 unless one disables the sandbox which is not what I'd like to do. So to keep the --overlay folders from piling up, I've added the "&& firejail --overlay-clean" bit.

---

### Post by #&amp;thj^% on 2017-06-02
> **vasa1 said:**
> Yes, that's a very helpful resource. As a matter of fact, his tip on getting --overlay to work on WiFi was very helpful as I've posted here: [https://ubuntuforums.org/showthread.php?t=2362591&p=13651238#post13651238](https://ubuntuforums.org/showthread.php?t=2362591&p=13651238#post13651238)

I'm now using```
firejail --overlay --dns=8.8.8.8 --dns=8.8.4.4 google-chrome-unstable && firejail --overlay-clean
```because I prefer --overlay over --private. With the former, I have all my browser customization available. --private seems to open a pristine browser, clean profile, clean everything, I've to log into sites afresh, generally more painful.

Apparently, --overlay-tmpfs doesn't work with Chrome/Chromium with the version of firejail for 16.04 unless one disables the sandbox which is not what I'd like to do. So to keep the --overlay folders from piling up, I've added the "&& firejail --overlay-clean" bit.

Yes it is Great Tool>>>and still learning it myself. :)
_I Like the the fact you opened such a thread,_ as this could be helpful to all over time. (If there are contributors here that is)

There is also some very advanced tweaks also but I have not tested thoroughly enough yet to post here, but will when I feel it is relevant (with facts and not guesses)

Kudos

---

### Post by &amp;KyT$0P# on 2017-06-02
Currently I'm using [this version of firejail]("https://github.com/netblue30/firejail/tree/0.9.46-bugfixes") (self-compiled .deb), on Xubuntu 16.04.

Mostly I use firejail for [FONT=Courier New]--overlay-tmpfs[/FONT].  Lots of ways that's useful.  It has even more uses inside VMs.

I also use firejail for [FONT=Courier New]--read-only[/FONT], which I generally set in the profiles.  This option too has several uses.  But it's especially useful for applications stored inside the home directory.  Let's put it this way: Imagine you're driving in the fast lane on a busy highway, smoothly hurtling along at the speed limit.  Would you want your car's engine taken apart and adjusted at that very moment?

Other options I find useful are:
 - firejail's blacklist/whitelist feature, so that the contents of my home folder inside the sandbox is only what's needed for that program, nothing more
 - using firejail to disable Internet access for a single program, either with [FONT=Courier New]--net=none[/FONT] or [FONT=Courier New]--protocol=unix[/FONT]


Like 1fallen said, lots of different options.  And which ones you will find useful depends on what you want to sandbox, and in what ways you want to sandbox it.

Have fun :)

---

### Post by LastDino on 2017-06-03
Not as knowledgeable as some other posts here but as for how I use it, I use gui "firejail configuration wizard" and put certain programs like web-browser in it, next time I directly run them from there.

I feel that is about the easiest way it can be done by the "click-click" user.

---

### Post by linuxyogi on 2017-06-09
> **1fallen said:**
> 
netblue is the guy to get the answer's you seek.  [URL="https://github.com/netblue30"]https://github.com/netblue30
[/URL]

Is this PPA safe to install [https://launchpad.net/~deki/+archive/ubuntu/firejail](https://launchpad.net/~deki/+archive/ubuntu/firejail) ?

I find  mention of the maintainer [COLOR=#333333][FONT=Ubuntu]Reiner Herrmann here too [https://packages.ubuntu.com/yakkety/utils/firejail](https://packages.ubuntu.com/yakkety/utils/firejail)

> [/FONT][/COLOR][h=3]Original Maintainer (usually from Debian):[/h]
[LIST]
[*]Reiner Herrmann
[*]
[/LIST]
[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2017-06-09
> **linuxyogi said:**
> Is this PPA safe to install [https://launchpad.net/~deki/+archive/ubuntu/firejail](https://launchpad.net/~deki/+archive/ubuntu/firejail) ?

I find  mention of the maintainer [COLOR=#333333][FONT=Ubuntu]Reiner Herrmann here too [https://packages.ubuntu.com/yakkety/utils/firejail](https://packages.ubuntu.com/yakkety/utils/firejail)

[/FONT][/COLOR]

Yes I use it.:)
Your mileage may vary though.
Is there a reason you don't just use the Version already provided in Our Repos?

---

### Post by linuxyogi on 2017-06-09
> **1fallen said:**
> Yes I use it.:)
Your mileage may vary though.
Is there a reason you don't just use the Version already provided in Our Repos?

I am using 16.04. Under 17.04 any app opened with firejail opened as regular user (not root) but after moving to 16.04 I find that app are labelled "(as superuser)".
Its no big deal I guess they answer it on their FAQ page.

---

### Post by &amp;KyT$0P# on 2017-06-09
> **linuxyogi said:**
> Is this PPA safe to install [https://launchpad.net/~deki/+archive/ubuntu/firejail](https://launchpad.net/~deki/+archive/ubuntu/firejail) ?

I find  mention of the maintainer [COLOR=#333333][FONT=Ubuntu]Reiner Herrmann here too [https://packages.ubuntu.com/yakkety/utils/firejail](https://packages.ubuntu.com/yakkety/utils/firejail)

[/FONT][/COLOR]
Reiner Herrmann is one of the firejail developers.
[https://github.com/netblue30/firejail/blob/master/README#L37]("https://github.com/netblue30/firejail/blob/master/README#L37")

---

### Post by vasa1 on 2017-06-09
> **1fallen said:**
> Yes I use it.:)
Your mileage may vary though.
Is there a reason you don't just use the Version already provided in Our Repos?
The version in the **xenial** repos is ```
firejail/xenial-updates,now 0.9.38.10-0ubuntu0.16.04.1 amd64 [installed]

```The ppa mentioned is newer and shinier and I'll try it as well. Thanks!

---

### Post by Quarkrad on 2017-06-14
I have been using firejail for a few weeks now - without any additional options, i.e.** firejail firefox**.  A few days ago I suddenly lost the ability to type in firefox. I have tried disabling all my add-ons - I'm running 16.04, ff 53.0.3 (64bit) and firejail 0.9.38.10 install via Synaptic.  Anybody else experienced this?

---

### Post by vasa1 on 2017-06-14
> **Quarkrad said:**
> I have been using firejail for a few weeks now - without any additional options, i.e.** firejail firefox**.  A few days ago I suddenly lost the ability to type in firefox. I have tried disabling all my add-ons - I'm running 16.04, ff 53.0.3 (64bit) and firejail 0.9.38.10 install via Synaptic.  Anybody else experienced this?
And can you type when you launch Firefox without firejail?

---

### Post by LastDino on 2017-06-14
> **Quarkrad said:**
> I have been using firejail for a few weeks now - without any additional options, i.e.** firejail firefox**.  A few days ago I suddenly lost the ability to type in firefox. I have tried disabling all my add-ons - I'm running 16.04, ff 53.0.3 (64bit) and firejail 0.9.38.10 install via Synaptic.  Anybody else experienced this?
[https://ubuntuforums.org/showthread.php?t=2362947](https://ubuntuforums.org/showthread.php?t=2362947)

Read something similar here. Though, I'm not having that problem

---

### Post by vasa1 on 2017-06-14
Quarkrad is using 16.04 and the repo version of firejail (v 0.38). 1fallen is on 17.10 and I think his firejail version is 0.46.

Edit: and this edit is typed using the repo version
```
vasa1@aes-3567:~$ apt policy firejail
firejail:
  Installed: 0.9.38.10-0ubuntu0.16.04.1
  Candidate: 0.9.38.10-0ubuntu0.16.04.1
  Version table:
 *** 0.9.38.10-0ubuntu0.16.04.1 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     0.9.38-1ubuntu0.1 500
        500 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
     0.9.38-1 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages

```and Firefox 53. So I don't know how to explain Quarkrad's problem :(

---

### Post by Quarkrad on 2017-06-14
Yes - I can type if I launch firefox without firejail.  The same thing (for me!) happens with Thuinderbird - if I launch **firejail thunderbird** I cannot type into a new message, if I just launch **thunderbird** I can type.

---

### Post by vasa1 on 2017-06-14
Have you tried launching a text editor with Firejail? What happens there? Can you then type?

This is my terminal output:```
vasa1@aes-3567:~$ firejail firefox
Reading profile /etc/firejail/firefox.profile
Reading profile /etc/firejail/disable-mgmt.inc
Reading profile /etc/firejail/disable-secret.inc
Reading profile /etc/firejail/disable-common.inc
Reading profile /etc/firejail/disable-devel.inc
Reading profile /etc/firejail/whitelist-common.inc
Parent pid 7063, child pid 7064
Blacklist violations are logged to syslog

Child process initialized
1497445868502	addons.update-checker	WARN	Update manifest for aushelper@mozilla.org did not contain an updates property
1497445868628	addons.update-checker	WARN	Update manifest for webcompat@mozilla.org did not contain an updates property
1497445868714	addons.update-checker	WARN	Update manifest for firefox@getpocket.com did not contain an updates property
1497445869518	addons.update-checker	WARN	Update manifest for e10srollout@mozilla.org did not contain an updates property
1497445869533	addons.update-checker	WARN	Update manifest for {972ce4c6-7e08-4474-a285-3208198ce6fd} did not contain an updates property
1497445870819	addons.xpi	WARN	Add-on firefox-hotfix@mozilla.org is not compatible with application version.
1497445871202	addons.xpi	WARN	Add-on firefox-hotfix@mozilla.org is not compatible with application version.

(firefox:5): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion 'gtk_accelerator_valid(key, modifier)' failed

parent is shutting down, bye...
vasa1@aes-3567:~$ 

```

---

### Post by &amp;KyT$0P# on 2017-06-14
@Quarkrad Completely quit Firefox, then try -
```
firejail --noprofile firefox
```
Can you type in that Firefox?

---

### Post by Quarkrad on 2017-06-14
Via the terminal.  If I type **gedit** it launches and I can type as normal.  Via the terminal if I type **firejail gedit** it launches and I cannot type.  Here is my terminal output:

```
dad@dadubuntu:~$ firejail firefox
Reading profile /etc/firejail/firefox.profile
Reading profile /etc/firejail/disable-mgmt.inc
Reading profile /etc/firejail/disable-secret.inc
Reading profile /etc/firejail/disable-common.inc
Reading profile /etc/firejail/disable-devel.inc
Reading profile /etc/firejail/whitelist-common.inc
Parent pid 2721, child pid 2722
Blacklist violations are logged to syslog

Child process initialized

parent is shutting down, bye...
dad@dadubuntu:~$ 


```

Shut down firefox.  If I type** firejail --noprofile firefox**  firefox launches but I cannot type.

---

### Post by Quarkrad on 2017-06-14
Since having this trouble I have purged firejail and reinstalled - it is still happening.  Is there a config file somewhere that is not deleted when I purge?

---

### Post by vasa1 on 2017-06-14
IIRC, if you haven't done anything special, there shouldn't be any firejail files in your home folder.

For those who've gone a bit further, one could have ~/.config/firejail with one or more profiles in there.

---

### Post by Quarkrad on 2017-06-15
When  I launched gedit this morning with this command **firejail --noprofile gedit**, gedit launched with this terminal output:

```
dad@dadubuntu:~$ firejail --noprofile gedit
Parent pid 2817, child pid 2818

Child process initialized
```

When I tried to type something nothing appeared on the terminal but an extra line appeared in the terminal:

```
dad@dadubuntu:~$ firejail --noprofile gedit
Parent pid 2817, child pid 2818

Child process initialized

(gedit:2): IBUS-WARNING **: Unable to connect to ibus: Could not connect: Connection refused
```


Each time I tried to type something I got another *(gedit:2): IBUS-WARNING **: Unable to connect to ibus: Could not connect: Connection refused[/CODE]* line appear in the terminal

I closed down gedit and the terminal to repeat the above - but gedit refused to launch with this output:

```
dad@dadubuntu:~$: command not found
dad@dadubuntu:~$ Reading profile /etc/firejail/generic.profile
Reading: command not found
dad@dadubuntu:~$ Reading profile /etc/firejail/disable-mgmt.inc
Reading: command not found
dad@dadubuntu:~$ Reading profile /etc/firejail/disable-secret.inc
Reading: command not found
dad@dadubuntu:~$ Reading profile /etc/firejail/disable-common.inc
Reading: command not found
dad@dadubuntu:~$ 
dad@dadubuntu:~$ ** Note: you can use --noprofile to disable generic.profile **
1.mp3: command not found
dad@dadubuntu:~$ 
dad@dadubuntu:~$ Parent pid 2362, child pid 2363
Parent: command not found
dad@dadubuntu:~$ 
dad@dadubuntu:~$ Child process initialized
Child: command not found
dad@dadubuntu:~$ /bin/bash: –noprofile: command not found
bash: /bin/bash:: No such file or directory
dad@dadubuntu:~$ 
dad@dadubuntu:~$ parent is shutting down, bye...
parent: command not found
dad@dadubuntu:~$ 

```

What is odd to me is that there is a line in the above output that says *1.mp3: command not found*.  This is 1.mp3 file is a file on my Desktop that I'm using to test my audio output as I have another thread open (General Help - No Audio) because I'm experiencing sudden loss of audio.  I'm not sure why 1.mp3 is appearing in this output.

---

### Post by vasa1 on 2017-06-15
This really bizarre!

```
dad@dadubuntu:~$: command not found
dad@dadubuntu:~$ Reading profile /etc/firejail/generic.profile
Reading: command not found
dad@dadubuntu:~$ Reading profile /etc/firejail/disable-mgmt.inc
Reading: command not found
dad@dadubuntu:~$ Reading profile /etc/firejail/disable-secret.inc
Reading: command not found
dad@dadubuntu:~$ Reading profile /etc/firejail/disable-common.inc
Reading: command not found

```Did you really enter "Reading profile /etc/firejail/generic.profile" from the command-line? At least that's what it looks like.

Then there's also the "–" instead of "--" in```
dad@dadubuntu:~$ /bin/bash: –noprofile: command not found
```

Let's see if anyone can figure out what's going on.

I'm wondering if your terminal is messed up in some way.

---

### Post by Quarkrad on 2017-06-15
I'm having, for me, a really inconvenient problem with my audio that I cannot get sorted.  I'm thinking of re-installing 16.04 and hope it will sort out my audio problem and this firejail issue.  If I have, which it looks like, something weird/one-off it seems a waste of peoples time trying to get me sorted if I am the only one that will benefit.  I will re-install and get back later re firejail.

---

### Post by #&amp;thj^% on 2017-06-15
> **Quarkrad said:**
> When  I launched gedit this morning with this command **firejail --noprofile gedit**, gedit launched with this terminal output:

```
dad@dadubuntu:~$ firejail --noprofile gedit
Parent pid 2817, child pid 2818

Child process initialized
```

When I tried to type something nothing appeared on the terminal but an extra line appeared in the terminal:

```
dad@dadubuntu:~$ firejail --noprofile gedit
Parent pid 2817, child pid 2818

Child process initialized

(gedit:2): IBUS-WARNING **: Unable to connect to ibus: Could not connect: Connection refused
```


Each time I tried to type something I got another *(gedit:2): IBUS-WARNING **: Unable to connect to ibus: Could not connect: Connection refused[/CODE]* line appear in the terminal

I closed down gedit and the terminal to repeat the above - but gedit refused to launch with this output:

```
dad@dadubuntu:~$: command not found
dad@dadubuntu:~$ Reading profile /etc/firejail/generic.profile
Reading: command not found
dad@dadubuntu:~$ Reading profile /etc/firejail/disable-mgmt.inc
Reading: command not found
dad@dadubuntu:~$ Reading profile /etc/firejail/disable-secret.inc
Reading: command not found
dad@dadubuntu:~$ Reading profile /etc/firejail/disable-common.inc
Reading: command not found
dad@dadubuntu:~$ 
dad@dadubuntu:~$ ** Note: you can use --noprofile to disable generic.profile **
1.mp3: command not found
dad@dadubuntu:~$ 
dad@dadubuntu:~$ Parent pid 2362, child pid 2363
Parent: command not found
dad@dadubuntu:~$ 
dad@dadubuntu:~$ Child process initialized
Child: command not found
dad@dadubuntu:~$ /bin/bash: –noprofile: command not found
bash: /bin/bash:: No such file or directory
dad@dadubuntu:~$ 
dad@dadubuntu:~$ parent is shutting down, bye...
parent: command not found
dad@dadubuntu:~$ 

```

What is odd to me is that there is a line in the above output that says *1.mp3: command not found*.  This is 1.mp3 file is a file on my Desktop that I'm using to test my audio output as I have another thread open (General Help - No Audio) because I'm experiencing sudden loss of audio.  I'm not sure why 1.mp3 is appearing in this output.

I also had some issue's with the version in the repos, netblue30 asked if I would try an updated version on the master git hub site, and it solved a bunch of my issue's.
I'm not sure a reinstall of your OS will help but maybe try the newer version first to see.
I'm now using:
```
firejail --version
firejail version 0.9.49

Compile time support:
    - AppArmor support is disabled
    - AppImage support is enabled
    - bind support is enabled
    - chroot support is enabled
    - file and directory whitelisting support is enabled
    - file transfer support is enabled
    - git install support is disabled
    - networking support is enabled
    - overlayfs support is enabled
    - private-home support is enabled
    - seccomp-bpf support is enabled
    - user namespace support is enabled
    - X11 sandboxing support is enabled


```
Found here: [https://github.com/netblue30/firejail](https://github.com/netblue30/firejail)

---

### Post by Quarkrad on 2017-06-15
I purged firejail via **sudo apt-get purge --auto-remove firejail**.  I then installed the latest version:

```
dad@dadubuntu:~$ firejail --version
firejail version 0.9.49

Compile time support:
	- AppArmor support is disabled
	- AppImage support is enabled
	- bind support is enabled
	- chroot support is enabled
	- file and directory whitelisting support is enabled
	- file transfer support is enabled
	- git install support is disabled
	- networking support is enabled
	- overlayfs support is enabled
	- private-home support is enabled
	- seccomp-bpf support is enabled
	- user namespace support is enabled
	- X11 sandboxing support is enabled


```

I have also install Chromium Web Browser.

firefox  [COLOR="#0000CD"]can type  [/COLOR]                                               
firejail firefox  [COLOR="#FF0000"]cannot type[/COLOR]
firejail --noprofile [COLOR="#FF0000"]cannot type[/COLOR]

chromium-browser  [COLOR="#0000CD"]can type[/COLOR]
firejail chromium-browser [COLOR="#FF0000"]cannot type[/COLOR]
firejail --noprofile chromium-browser [COLOR="#FF0000"]cannot type[/COLOR]

THIS IS INTERESTING(?)

gedit  [COLOR="#0000CD"]can type[/COLOR]
firejail gedit   [COLOR="#0000CD"]can type[/COLOR]
firejail --noprofile  [COLOR="#0000CD"]can type[/COLOR]

With this latest version it seems to work with the text editor but no the browsers.

---

### Post by #&amp;thj^% on 2017-06-15
> **Quarkrad said:**
> I purged firejail via **sudo apt-get purge --auto-remove firejail**.  I then installed the latest version:

```
dad@dadubuntu:~$ firejail --version
firejail version 0.9.49

Compile time support:
    - AppArmor support is disabled
    - AppImage support is enabled
    - bind support is enabled
    - chroot support is enabled
    - file and directory whitelisting support is enabled
    - file transfer support is enabled
    - git install support is disabled
    - networking support is enabled
    - overlayfs support is enabled
    - private-home support is enabled
    - seccomp-bpf support is enabled
    - user namespace support is enabled
    - X11 sandboxing support is enabled


```

I have also install Chromium Web Browser.

firefox  [COLOR=#0000CD]can type  [/COLOR]                                               
firejail firefox  [COLOR=#FF0000]cannot type[/COLOR]
firejail --noprofile [COLOR=#FF0000]cannot type[/COLOR]

chromium-browser  [COLOR=#0000CD]can type[/COLOR]
firejail chromium-browser [COLOR=#FF0000]cannot type[/COLOR]
firejail --noprofile chromium-browser [COLOR=#FF0000]cannot type[/COLOR]

THIS IS INTERESTING(?)

gedit  [COLOR=#0000CD]can type[/COLOR]
firejail gedit   [COLOR=#0000CD]can type[/COLOR]
firejail --noprofile  [COLOR=#0000CD]can type[/COLOR]

With this latest version it seems to work with the text editor but no the browsers.
Very Odd? I,m using Firefox now with firejail typing this, gnome-wayland....But I find the same as you in a X11 session.
I'm not sure what I can add here. :confused:
EDIT: This seems to be specific to Ubuntu or Debian, due to the fact all works as expected on Arch. :(
netblue30 i "think" is looking at this as we speak: also see this: [URL="https://ubuntuforums.org/showthread.php?t=2362947"]https://ubuntuforums.org/showthread.php?t=2362947

[/URL]

---

### Post by &amp;KyT$0P# on 2017-06-15
> **Quarkrad said:**
> ```
IBUS-WARNING **: Unable to connect to ibus: Could not connect: Connection refused
```
Does [this]("https://github.com/netblue30/firejail/issues/116#issuecomment-271516261") help?

---

### Post by #&amp;thj^% on 2017-06-15
> **halogen2 said:**
> Does [this]("https://github.com/netblue30/firejail/issues/116#issuecomment-271516261") help?

Dude You Rock!!! :)
Works like a charm. Remind me to put you on my Christmas card list;) :KS
BTW it works for all Browsers in a X11 session.

---

### Post by Quarkrad on 2017-06-16
Wow - well done Houston, mission back on track.   All applications working well with Typing by inserting **GTK_IM_MODULE=xim firejail** - thank you.

---

### Post by Quarkrad on 2017-06-16
This is a little off topic - please advise if I should open a new thread under General Support.   I use 16.04 Mate and use customer launchers in the top panel - if I create a custom launcher using **GTK_IM_MODULE=xim firejail firefox** or **GTK_IM_MODULE=xim firejail thunderbird** neither application will launch. If I right click on the top left icon in the top panel and chose Edit Menus and change the application launchers then going Application / Internet / firefox or thunderbird - neither application launches.  However, when I open the terminal and launch either **GTK_IM_MODULE=xim firejail firefox** or **GTK_IM_MODULE=xim firejail thunderbird** the applications open and I can type.  Is there a way I can launch apps with firejail other than using the terminal? Appreciate this is not a firejail issue.

---

### Post by vasa1 on 2017-06-16
> **Quarkrad said:**
> This is a little off topic - please advise if I should open a new thread under General Support.   I use 16.04 Mate and use customer launchers in the top panel - if I create a custom launcher using **GTK_IM_MODULE=xim firejail firefox** or **GTK_IM_MODULE=xim firejail thunderbird** neither application will launch. If I right click on the top left icon in the top panel and chose Edit Menus and change the application launchers then going Application / Internet / firefox or thunderbird - neither application launches.  However, when I open the terminal and launch either **GTK_IM_MODULE=xim firejail firefox** or **GTK_IM_MODULE=xim firejail thunderbird** the applications open and I can type.  Is there a way I can launch apps with firejail other than using the terminal? Appreciate this is not a firejail issue.

Could you try something like```
Exec=bash -c 'GTK_IM_MODULE=xim firejail firefox'
``` after copying over the Firefox launcher (desktop file) from */usr/share/applications* to *~/.local/share/applications*? You'll want to modify the *Exec=* line.

---

### Post by Quarkrad on 2017-06-16
Sorry - I'm struggling.  The command in the firefox launcher is **firefox %U**.  I don't understand what command I have to replace it with.

---

### Post by vasa1 on 2017-06-16
> **Quarkrad said:**
> Sorry - I'm struggling.  The command in the firefox launcher is **firefox %U**.  I don't understand what command I have to replace it with.

Please post the path to the launcher. In other words, where is it?

Then also post the entire contents of the launcher.

---

### Post by Quarkrad on 2017-06-16
The path is:```
dad@dadubuntu:~$ which firefox
/usr/bin/firefox

```

To be honest I'm not sure what you mean by the contents of the launcher.  There is a symbolic link called firefox in /usr/bin that has these contents:

```
#!/bin/sh

set -e

# Firefox launcher containing a Profile migration helper for
# temporary profiles used during alpha and beta phases.

# Authors:
#  Alexander Sack <asac@jwsdot.com>
#  Fabien Tassin <fta@sofaraway.org>
#  Steve Langasek <steve.langasek@canonical.com>
#  Chris Coulson <chris.coulson@canonical.com>
# License: GPLv2 or later

MOZ_LIBDIR=/usr/lib/firefox
MOZ_APP_LAUNCHER=`which $0`
MOZ_APP_NAME=firefox

export MOZ_APP_LAUNCHER

while [ ! -x $MOZ_LIBDIR/$MOZ_APP_NAME ] ; do
    if [ -L "$MOZ_APP_LAUNCHER" ] ; then
        MOZ_APP_LAUNCHER=`readlink -f $MOZ_APP_LAUNCHER`
        MOZ_LIBDIR=`dirname $MOZ_APP_LAUNCHER`
    else
        echo "Can't find $MOZ_LIBDIR/$MOZ_APP_NAME"
        exit 1
    fi
done

usage () {
    $MOZ_LIBDIR/$MOZ_APP_NAME -h | sed -e 's,/.*/,,'
    echo
    echo "      -g or --debug          Start within debugger"
    echo "      -d or --debugger       Specify debugger to start with (eg, gdb or valgrind)"
    echo "      -a or --debugger-args  Specify arguments for debugger"
}

moz_debug=0
moz_debugger_args=""
moz_debugger="gdb"

while [ $# -gt 0 ]; do
    case "$1" in
        -h | --help )
            usage
            exit 0
            ;;
        -g | --debug )
            moz_debug=1
            shift
            ;;
        -d | --debugger)
            moz_debugger=$2;
            if [ "${moz_debugger}" != "" ]; then
	      shift 2
            else
              echo "-d requires an argument"
              exit 1
            fi
            ;;
        -a | --debugger-args )
            moz_debugger_args=$2;
            if [ "${moz_debugger_args}" != "" ] ; then
                shift 2
            else
                echo "-a requires an argument"
                exit 1
            fi
            ;;
        -- ) # Stop option processing
            shift
            break
            ;;
        * )
            break
            ;;
    esac
done

if [ $moz_debug -eq 1 ] ; then
    case $moz_debugger in
        memcheck)
            debugger="valgrind"
            ;;
        *)
            debugger=$moz_debugger
            ;;
    esac

    debugger=`which $debugger`
    if [ ! -x $debugger ] ; then
        echo "Invalid debugger"
        exit 1
    fi

    case `basename $moz_debugger` in
        gdb)
            exec $debugger $moz_debugger_args --args $MOZ_LIBDIR/$MOZ_APP_NAME "$@"
            ;;
        memcheck)
            echo "$MOZ_APP_NAME has not been compiled with valgrind support"
            exit 1
            ;;
        *)
            exec $debugger $moz_debugger_args $MOZ_LIBDIR/$MOZ_APP_NAME "$@"
            ;;
    esac
else
    exec $MOZ_LIBDIR/$MOZ_APP_NAME "$@"
fi
```

---

### Post by vasa1 on 2017-06-16
No! That's something I don't know about. Please post the output of```
ls /usr/share/applications/firefox.desktop
```and if such a file exists, post the contents of that file.

---

### Post by vasa1 on 2017-06-16
Let's try this:
Open your file manager and move to **~/.local/share/applications**. Create a new file in there called **FirejailFox.desktop**. Open that file with a plain text editor, pluma or gedit or mousepad or gedit but _not_ LibreOffice, and paste in the following:
```

[Desktop Entry]
Version=1.0
Name=FirejailFox
Comment=Firejailed Firefox
Exec=bash -c 'GTK_IM_MODULE=xim firejail firefox' %U

Icon=firefox
Terminal=false
Type=Application
Categories=Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml_xml;image/webp;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;
```
Save that file and close your editor.

Now when you double-click on that file in your file manager what happens?

---

### Post by Quarkrad on 2017-06-16
The output of that command is:

dad@dadubuntu:~$ ls /usr/share/applications/firefox.desktop
/usr/share/applications/firefox.desktop

Attached file shows contents of that location.  I am using Mate/gnome 16.04

---

### Post by vasa1 on 2017-06-16
Please see the post just above your latest post.

---

### Post by Quarkrad on 2017-06-16
Tried attachment again

---

### Post by Quarkrad on 2017-06-16
Sorry, sorry sorry - didn't read your text properly - inexcusable on my part.  I have created your file and it works - it is now sitting in my top panel and launches ff.

---

### Post by vasa1 on 2017-06-16
> **Quarkrad said:**
> Sorry, sorry sorry - didn't read your text properly - inexcusable on my part.  I have created your file and it works - it is now sitting in my top panel and launches ff.
Good to know! Now you can make something similar for Tbird.

---

### Post by Quarkrad on 2017-06-16
Both desktop files done and working.

---

### Post by Quarkrad on 2017-06-16
I'm guessing if I want to add a firejail option like --noprofile it is just a case of adding:
```

[Desktop Entry]
Version=1.0
Name=FirejailFox
Comment=Firejailed Firefox
Exec=bash -c 'GTK_IM_MODULE=xim firejail [COLOR="#FF0000"]--noprofile[/COLOR] firefox' %U

Icon=firefox
Terminal=false
Type=Application
Categories=Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml_xml;image/webp;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;
```

---

### Post by vasa1 on 2017-06-16
You can always open a terminal and run```
firejail --list
```to get information.

For example:```
08:33 PM ~ $ firejail --list
14888:vasa1:firejail --caps.drop=all google-chrome --profile-directory=Default %U 
15051:vasa1:firejail --list 
08:33 PM ~ $ 

```

---

### Post by Erik1984 on 2017-06-20
I use it now for Firefox, Thunderbrid and Chrome. Only annoying thing is that Firefox and Thunderbird show "(as superuser)" in the title bar. Which seems like the opposite of what you want to achieve with Firejail. I guess/hope these applications are not really run as superuser as Firejail seems to restrict access (I can only see a few files and directories in $HOME when browsing to file:///).

---

### Post by vasa1 on 2017-06-20
> **Erik1984 said:**
> I use it now for Firefox, Thunderbrid and Chrome. Only annoying thing is that Firefox and Thunderbird show "(as superuser)" in the title bar. Which seems like the opposite of what you want to achieve with Firejail. I guess/hope these applications are not really run as superuser as Firejail seems to restrict access (I can only see a few files and directories in $HOME when browsing to file:///).
I don't see that.

Could you share your versions of Firefox, firejail, and your distro?

I have *wmctrl* installed and so I run```
wmctrl -l | grep -i firefox
``` and see```
05:59 AM ~ $ wmctrl -l | grep -i firefox
0x04a00004  0 aes-3567 firejail firefox 
0x04c00010  0 aes-3567 LIbreOffice Base crashes Ubuntu 16.04 - Mozilla Firefox
05:59 AM ~ $ 

```"LibreOffice Base ...." is also what is shown in my Firefox titlebar.

If you don't want to use *wmctrl*, you can use *xwininfo* which probably is already present on your system.

---

### Post by Erik1984 on 2017-06-21
> **vasa1 said:**
> I don't see that.

Could you share your versions of Firefox, firejail, and your distro?

I have *wmctrl* installed and so I run```
wmctrl -l | grep -i firefox
``` and see```
05:59 AM ~ $ wmctrl -l | grep -i firefox
0x04a00004  0 aes-3567 firejail firefox 
0x04c00010  0 aes-3567 LIbreOffice Base crashes Ubuntu 16.04 - Mozilla Firefox
05:59 AM ~ $ 

```"LibreOffice Base ...." is also what is shown in my Firefox titlebar.

If you don't want to use *wmctrl*, you can use *xwininfo* which probably is already present on your system.

Thanks for your response. Ok, here you go:

Firejail
```

erik@erik-desktop:~$ firejail --version
firejail version 0.9.44.8

Compile time support:
    - AppArmor support is enabled
    - AppImage support is enabled
    - bind support is enabled
    - chroot support is enabled
    - file and directory whitelisting support is enabled
    - file transfer support is enabled
    - networking support is enabled
    - overlayfs support is enabled
    - private-home support is enabled
    - seccomp-bpf support is enabled
    - user namespace support is enabled
    - X11 sandboxing support is enabled

```

wmctrl
```

erik@erik-desktop:~$ wmctrl -l | grep -i firefox
0x03c00010  0 erik-desktop How do you use Firejail? - Page 5 - Mozilla Firefox

```
That is the tab I have currently open so the title of the Firefox window (minus the "(as superuser)")

Distro
```

cat /var/log/installer/media-info
Ubuntu-MATE 17.04 "Zesty Zapus" - Release amd64 (20170412)

```

It could be that this is an issue with the MATE desktop. I did find this issue: [https://github.com/netblue30/firejail/issues/258](https://github.com/netblue30/firejail/issues/258) Some people in that thread also report this as a specific issue for MATE.

---

### Post by #&amp;thj^% on 2017-06-21
> **Erik1984 said:**
> Thanks for your response. Ok, here you go:

Firejail
```

erik@erik-desktop:~$ firejail --version
firejail version 0.9.44.8

Compile time support:
    - AppArmor support is enabled
    - AppImage support is enabled
    - bind support is enabled
    - chroot support is enabled
    - file and directory whitelisting support is enabled
    - file transfer support is enabled
    - networking support is enabled
    - overlayfs support is enabled
    - private-home support is enabled
    - seccomp-bpf support is enabled
    - user namespace support is enabled
    - X11 sandboxing support is enabled

```

wmctrl
```

erik@erik-desktop:~$ wmctrl -l | grep -i firefox
0x03c00010  0 erik-desktop How do you use Firejail? - Page 5 - Mozilla Firefox

```
That is the tab I have currently open so the title of the Firefox window (minus the "(as superuser)")

Distro
```

cat /var/log/installer/media-info
Ubuntu-MATE 17.04 "Zesty Zapus" - Release amd64 (20170412)

```

It could be that this is an issue with the MATE desktop. I did find this issue: [https://github.com/netblue30/firejail/issues/258](https://github.com/netblue30/firejail/issues/258) Some people in that thread also report this as a specific issue for MATE.

Not necessarily IE: running XFCE here and mine shows:
```
 wmctrl -l | grep -i firefox
0x04a00010  0 me-pc How do you use Firejail? - Mozilla Firefox
firejail --list
3030:me:firejail firefox 
27442:me:firejail --list 


``` 
vasa1 is running a different firejail command. (I'm guessing though)
EDIT: Mea Culpa I see this now---(For me, MATE shows as if programs are running as root. XFCE and KDE, however, don't.)
Oddly I'm not seeing it on 17.04 Mate with compiz>>>Hmmm?
Nor have I ever seen it show on Arch with any DE. (Just saying) Netblue dose point to this being a Debian issue.

---

### Post by vasa1 on 2017-06-21
> **1fallen said:**
> ...
vasa1 is running a different firejail command. (I'm guessing though)
EDIT: Mea Culpa I see this now---(For me, MATE shows as if programs are running as root. XFCE and KDE, however, don't.)
Oddly I'm not seeing it on 17.04 Mate with compiz>>>Hmmm?
Nor have I ever seen it show on Arch with any DE. (Just saying) Netblue dose point to this being a Debian issue.
This is just a plain "firejail firefox". Still no superuser.
```
05:50 AM ~ $ firejail --version
firejail version 0.9.48

Compile time support:
	- AppArmor support is enabled
	- AppImage support is enabled
	- bind support is enabled
	- chroot support is enabled
	- file and directory whitelisting support is enabled
	- file transfer support is enabled
	- git install support is disabled
	- networking support is enabled
	- overlayfs support is enabled
	- private-home support is enabled
	- seccomp-bpf support is enabled
	- user namespace support is enabled
	- X11 sandboxing support is enabled

05:56 AM ~ $ firejail firefox
Reading profile /etc/firejail/firefox.profile
Reading profile /etc/firejail/disable-common.inc
Reading profile /etc/firejail/disable-programs.inc
Reading profile /etc/firejail/disable-devel.inc
Reading profile /etc/firejail/whitelist-common.inc
Parent pid 4744, child pid 4745
Blacklist violations are logged to syslog
Child process initialized in 168.30 ms

Parent is shutting down, bye...
05:58 AM ~ $ 

```and from another terminal window:```
05:57 AM ~ $ firejail --list
4744:vasa1:firejail firefox 
4850:vasa1:firejail --list 
05:57 AM ~ $ wmctrl -l | grep -i firefox
0x03e00004  0 aes-3567 firejail firefox 
0x04200010  0 aes-3567 How do you use Firejail? - Mozilla Firefox
05:58 AM ~ $ 
```So no Superuser for me.

And there are comments in [https://github.com/netblue30/firejail/issues/258](https://github.com/netblue30/firejail/issues/258) indicating that it maybe related to one's choice of window manager. Metacity (marco in mate) seems to be to blame in some cases. I'm on kwin currently.

---

### Post by #&amp;thj^% on 2017-06-22
> **vasa1 said:**
> So no Superuser for me.

And there are comments in [https://github.com/netblue30/firejail/issues/258](https://github.com/netblue30/firejail/issues/258) indicating that it maybe related to one's choice of window manager. Metacity (marco in mate) seems to be to blame in some cases. I'm on kwin currently.
Thanks vasa1! :)
Yep same here I have never seen the Superuser shown, But I do use Compiz instead of  marco in mate... I do have some metacity installed as part of the install for mate..
I did  see however that he suggested that this was only a Debian related issue or non-issue.
And have never seen it with other Distros that I use.
Best Regards

---

### Post by Quarkrad on 2017-06-24
On my standard Mate 16.04 install I have three marco windows manager options (*no compositor*, *software compositor* and *compton gpu compositor*), all three launch firefox as Superuser.  When I switch to *compiz* windows manager firefox launchers as a normal user.

---

### Post by Erik1984 on 2017-06-24
Thanks for the feedback. I could try switching to Compiz. On the other hand the "(as superuser)" issue is cosmetic, so Firefox is not really running as superuser if I understand correctly.

---

### Post by Quarkrad on 2017-06-25
Sorry to ask a numpty question but apart from Firefox saying *as Superuser* in the top panel, how can you tell if it is actually is running as Superuser?

---

### Post by Erik1984 on 2017-06-25
I'm not a 100% sure on that but I checked the USER column in the output of ps aux:
```

erik@erik-desktop:~$ ps aux | sed -e '1p' -e '/firef/!d'
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
erik      2928  0.0  0.0  20500  2468 ?        S    11:26   0:00 firejail firefox
erik      2931  0.0  0.0  20500  1600 ?        S    11:26   0:00 firejail firefox
erik      2937 16.5  6.4 2521508 516236 ?      Sl   11:26   1:43 /usr/lib/firefox/firefox
erik      3126  0.0  0.0  18392  1044 pts/0    R+   11:36   0:00 sed -e 1p -e /firef/!d

```
I wonder why firejail firefox is listed twice btw. I have only one window open. But all these processes (the last being the search command itself) seem not be running as superuser.

For reference I ran pluma first normally and then with **gksu**.

Normal:
```
erik      3265  1.8  0.5 1049004 43604 ?       Sl   11:44   0:00 pluma
```

Gksu:
```
root      3334  1.3  0.5 673204 45036 ?        Sl   11:45   0:00 pluma
```

---

### Post by vasa1 on 2017-06-25
> **Quarkrad said:**
> On my standard Mate 16.04 install I have three marco windows manager options (*no compositor*, *software compositor* and *compton gpu compositor*), all three launch firefox as Superuser.  When I switch to *compiz* windows manager firefox launchers as a normal user.From the first post in [(as superuser) in title bar]("https://github.com/netblue30/firejail/issues/258"):
> Reply from netblue30: The sandbox process itself runs as root. The application inside the sandbox runs as a regular user. I don’t know why firefox shows as superuser, “ps aux | grep firefox” reports it as a regular user. I would say is a bug in firefox.
Plus Erik1984 has shown that Firefox isn't running as superuser.

---

### Post by Quarkrad on 2017-07-10
For information: on my 16.04 Ubuntu Mate system.  **bash -c 'GTK_IM_MODULE=xim firejail chromium-browser %U** does not launch the program either via the terminal or Application/Internet/Chromium Browser - nor does **bash -c 'GTK_IM_MODULE=xim firejail chromium-browser**. To launch Chromium Browser from either the terminal or Application/Internet/Chromium Browser I have to use **bash -c 'GTK_IM_MODULE=xim firejail chromium-browser'**

---

### Post by Quarkrad on 2017-07-31
**$ firejail --private --dns=8.8.8.8 --dns=8.8.4.4 firefox -no-remote**    I have just picked this up from [https://firejail.wordpress.com/documentation-2/firefox-guide/](https://firejail.wordpress.com/documentation-2/firefox-guide/).  Am I right in thinking if one uses a 'trusted' ISP like btinternet you can substitute their DNS ip address (62.6.40.178) for the google ones above?

---

### Post by Quarkrad on 2017-08-02
Something I don't quite understand is the default setup for firefox - it allows access, amongst other things to, Desktop, Downloads and ~/.mozilla.  Why ./mozilla(?) - this is where a users passwords are kept; surely of all folders to blacklist this is one of them.

---

### Post by Erik1984 on 2017-08-02
> **Quarkrad said:**
> Something I don't quite understand is the default setup for firefox - it allows access, amongst other things to, Desktop, Downloads and ~/.mozilla.  Why ./mozilla(?) - this is where a users passwords are kept; surely of all folders to blacklist this is one of them.

Firefox needs to store profiles, setting, cache and your browsing history somewhere. So it needs access to ~/.mozilla.

To come back to my earlier question regarding "(as superuser)" in the title bar. I switched to Compiz and it's not shown anymore.

---

### Post by Quarkrad on 2017-08-03
Something has happened to me as well - what I stated in #54 is no longer true.  I do not run as Superuser no matter what window manager I use. (firejail 0.9.38.10 kernel 4.10.0.28).

---

