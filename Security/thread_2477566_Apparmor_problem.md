---
title: "Apparmor problem"
date: 2022-07-29
forum: Security
---

### Post by vbgf3 on 2022-07-29
Hi Everyone,

I am trying to write an apparmor profile for Chrome. And I am stuck. I got this error message: 

> Failed to move to new namespace: PID namespaces supported, Network namespace supported, but failed: errno = Operation not permitted


Can somebody help ? Thanks.

---

### Post by #&amp;thj^% on 2022-07-29
> **vbgf3 said:**
> Hi Everyone,

I am trying to write an apparmor profile for Chrome. And I am stuck. I got this error message: 



Can somebody help ? Thanks.

We would need to see that profile here to help you.

---

### Post by vbgf3 on 2022-07-29
Here it is: 

> #include <tunables/global>


profile /opt/google/chrome/chrome flags=(enforce) {


        #  #include <abstractions/ubuntu-helpers> 


        ptrace                                                 ,


        /opt/google/chrome/chrome			mklrix     ,
        /opt/google/chrome{,-beta,-unstable}/chrome_crashpad_handler Pixr  ,
        /opt/google/chrome/**				mklrix       ,
        @{HOME}/.config/google-chrome/**		rkw       ,
        @{HOME}/Downloads/**				rw       ,
        /tmp/**                                         mkrw    ,
        /dev/**						r       ,
        /dev/usb/hiddev0                                r       ,
        /run/**						r     ,
        /proc/**					rw       ,
        
        /etc/**                                         r        ,
        /lib/**                                         mr     ,
        /lib64/**                                       mr    ,
        /usr/**                                         mr     ,
        /sys/**                                         mr     ,
        
        network                                                  ,
        
        
        #unix (send, receive) type=(seqpacket) peer=(label=@{profile_name}//sanitized_helper, addr=none),
        #unix (send, receive) type=(stream) peer=(label=@{profile_name}//sanitized_helper, addr=none),
        #unix (send, receive) type=(stream),
        #unix (send, receive) type=(seqpacket),
        #unix (send, receive) type=(raw),
        	
	deny /usr/bin/apt-get x,
	deny /usr/bin/apt     x,
	deny /usr/bin/dpkg    x,
	


	deny /etc/apparmor.d/  r,
 	deny /usr/sbin/apparmor_parser x,
 	
 	audit deny @{HOME}/Documents/** rwl,
 	audit deny @{HOME}/Videos/** rwl,
	audit deny @{HOME}/Music/** rwl,
	audit deny @{HOME}/Pictures/** rwl,
	audit deny @{HOME}/Templates/** rwl,
	audit deny @{HOME}/Public/** rwl,


	#audit deny capability mknod,
	#audit deny /{,var/}run/utmp r,
 	
	}


---

### Post by #&amp;thj^% on 2022-07-29
So in essence your trying to sandbox Chrome, is that right?

---

### Post by vbgf3 on 2022-07-29
Yes I am trying to use Apparmor to sandbox chrome.

---

### Post by #&amp;thj^% on 2022-07-29
That's going to be a hard one to do or make work (apparmor), but I have a thought to run past ya.
Would [firejail ]("https://github.com/netblue30/firejail")work for you on this one?
I'll show you a quick example, I feel that info is needed in making this kind of choice.
See screenshots without and with firejail.
The browser was pointed to my users Home Directory..
And you can see the difference in boxing it up does.

---

### Post by #&amp;thj^% on 2022-07-30
I seemed to have lost you, let me add the little I do know with the differences.
AppArmor could be closer compared to SELinux than FireJail, but here's the differences.

[B]The most important (IMO) is the level at which they run. FireJail runs as a program in userspace while AppArmor runs at the kernel level.
[/B]
FireJail takes advantage of Linux namespaces to provide isolation on a user, mount, network, and process level. This isolation provides the application it's own sandbox to do whatever it wants in while preventing those changes from effecting the rest of the system. You can think of this being similar to a container like you said. Containers also use namespaces for isolation.

**By contrast, AppArmor doesn't provide sandboxing, **rather it limits what parts of the system the application can access. You're specifying specific resources an app cannot use. These resources are not isolated though, so two apps running with AppArmor with access to the same resource could interact.

---

### Post by vbgf3 on 2022-07-31
Hi,

I have spent a day or so looking at firejail. 

Compared to my bwrap script, my bwrap script seems to do more. Since bwrap uses namespaces and you can choose which folders to bring into the namespace, I have managed to avoid bin sbin usr/bin usr/sbin . Chrome has no need for any external programs and it still works. And as for my home directory, I have only mapped Downloads. So it works just like firejail.

But firejail has this blacklist functionality which bwrap doesn't have. And it can block stuff within the mapped directories. 

Now if only I can get apparmor to work with Chrome - I am still stuck.

---

### Post by #&amp;thj^% on 2022-07-31
I think you possibly missed the important workings of firejail
However if you use Linux I would only suggest: Firejail and GUFW or Firewalld. 
I think the vast majority feel the same here.
I can limit Chrome as deep as i need, IE:
```


firejail --ignore=seccomp --ignore=protocol google-chrome-stable -no-remote

 ### And This:

firejail --private --nogroups google-chrome-stable
### This basicaly renders Chrome for Browsing only, and dystroys all data on close.
Screenshot

```
There are a few more flags that can be added as well.
I think folks just get hung-up on trying write apparmor profiles, when firejail handels it with ease.
I think I had some success with apparmor back in 2012, but quickly tossed it for firejail.
If you want I'll try to find the "old profile", I keep very deep records of things I've done over the decades.
While they do have a AppArmor profile on their wiki, doesn't seem like anyone uses it. 
But at the end of the day, it is your choice after all.
Firefox with apparmor and firejailed:
```
5 processes have profiles defined.
15 processes are in enforce mode.
   /usr/lib/firefox/firefox (22090) firejail-default
   /usr/lib/firefox/firefox (23186) firejail-default
   /usr/lib/firefox/firefox (23366) firejail-default
   /usr/lib/firefox/firefox (23677) firejail-default
   /usr/lib/firefox/firefox (23717) firejail-default
   /usr/bin/plasma-browser-integration-host (24348) firejail-default
   /usr/lib/firefox/firefox (162311) firejail-default
   /usr/lib/firefox/firefox (173260) firejail-default
   /usr/lib/firefox/firefox (177527) firejail-default
   /usr/lib/firefox/firefox (177859) firejail-default
   /usr/lib/firefox/firefox (230888) firejail-default
   /usr/lib/firefox/firefox (238404) firejail-default
   /usr/lib/firefox/firefox (296478) firejail-default
   /usr/lib/firefox/firefox (296540) firejail-default
   /usr/lib/firefox/firefox (296582) firejail-default
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
0 processes are in mixed mode.
0 processes are in kill mode.

```

---

### Post by ubcandles49 on 2022-08-12
Sandboxing browsers makes your fingerprint very unique. Whonix, thetorproject, they all warn people about running a sandboxed browser. I got no time to find all the links for you but you can google it. TheTorProject even closed their bubblewrap torbrowser project because of it: [URL="https://gitlab.torproject.org/tpo/applications/tor-browser/-/wikis/Sandbox/Linux"]https://gitlab.torproject.org/tpo/applications/tor-browser/-/wikis/Sandbox/Linux


[/URL]If you want to use firefox I recommend you to run a stricter firefox apparmor profile than the default profile and run a hardened firefox profile using [https://github.com/arkenfox/user.js/](https://github.com/arkenfox/user.js/). Read the arkenfox wiki on github first!

---

### Post by #&amp;thj^% on 2022-08-12
Would that not add more of Unique fingerprint, since this was brought up?

You know if I was a bad actor I'd be concerned, but I'm not.;)
First of all I have 2 Unique fingerprint's, proprietary.
the rest are in the averages IE:
> 
Similarity ratio All time   Name of plugin
Plugin 0    31.07%  PDF Viewer
Plugin 1    33.53%  Chrome PDF Viewer
Plugin 2    32.17%  Chromium PDF Viewer
Plugin 3    31.19%  Microsoft Edge PDF Viewer
Plugin 4    31.92%  WebKit built-in PDF

Most privacy-minded people are of the mindset that the less information you provide, the better your privacy will be. This is true** only in a world where you can opt to not do things. **For example, if I don&#8217;t want to have any personal information on Facebook, then I choose not to use Facebook.

However, it&#8217;s virtually impossible to not use the internet at all these days, so you&#8217;re going to leave fingerprints behind. Therefore, the goal here is to make it difficult for your private activities to be correlated to your public activities. Maintaining this separation prevents anyone from identifying you, personally, using data from activities you&#8217;d like to keep private.

However, using good privacy techniques such as locking down your browser to disallow JavaScript, cookies, and WebRTC requests could make your browser more unique since few people do the same. For example, using the Electronic Frontier Foundation&#8217;s Panopticlick : [https://coveryourtracks.eff.org/](https://coveryourtracks.eff.org/), we can see the difference in the two configurations.
Example:
```
 Our tests indicate that you have strong protection against Web tracking.
Is your browser:
Blocking tracking ads?  Yes
Blocking invisible trackers?    Yes
Protecting you from fingerprinting?     Your browser has a unique fingerprint
```
I use firejail for a bit more security than privacy which is a >>>Myth, Fairy Tale
I'm just comfortable with safe enough. ;)
Thanks for your input though.

---

### Post by ubcandles49 on 2022-08-13
Ok so the Mozilla developers that recommend Arkenfox to reduce the uniqueness of your fingerprint are all wrong. Good to know.

It's not disallowing cookies or javascript at all. Even DoNotTrack is disabled. Because disabling this things increase fingerprint as you say. Things as WebGL are disabled because they create a very unique fingerprint. A lot of people are using the same hardened template. Using that template makes your fingerprint way less unique using the default firefox settings which millions of people use. Besides reducing fingerprint it also increases the firefox security.

Firejail doens't bring more security at all. None of the security focused OS'es like Whonix support Firejail today. For a reason.

---

### Post by #&amp;thj^% on 2022-08-13
> **ubcandles49 said:**
> 
Firejail doens't bring more security at all. None of the security focused OS'es like Whonix support Firejail today. For a reason.
yes I can appreciate you statements, but you'll have to show me outside of Whosnix proof as of now this day forward, all your concerned statements have been fixed. >>[https://firejail.wordpress.com/](https://firejail.wordpress.com/) June 2022 – released Firejail 0.9.70. 
Show me one Linux system that has not had a flaw or two, some of which were critical.

Firejail significantly reduces attack surface for 1 (it may vary across different profiles) and increases attack surface for 2 (more or less). Everyone has to decide for themselves what net attack surface impact is for them.

Granting access to firejail for untrusted local unprivileged user may be not good idea (this is the scenario for which most of past cve's were applicable). 
FTR: Firejail, Apparmor Security-Enhanced Linux (SELinux) , bubblewrap, a minimal alternative to Firejail **None are bullet proof or a magic pill. Merely tools to help a knowledgeable user. If used wrong of course there is no fix for that. ;)**

Warning: Bubblewrap is a tool which provides sandboxing technologies like namespaces and seccomp filter. It does not by default provide a full sandbox that isolates weakpoints like the X11 window system (see #Sandboxing X11). **Running untrusted code** is never safe, sandboxing cannot change this. :[https://wiki.archlinux.org/title/Bubblewrap#Installation](https://wiki.archlinux.org/title/Bubblewrap#Installation)

I'm not condemning your information, but adding facts to you information.

I use all the above, for certain apps, programs, or system related functions or lack of.
```
firejail --list && sudo aa-status
 02995:me::firejail firefox --no-remote
[sudo] password for me: 
apparmor module is loaded.
58 profiles are loaded.
58 profiles are in enforce mode.
   /usr/lib/apache2/mpm-prefork/apache2
   /usr/lib/apache2/mpm-prefork/apache2//DEFAULT_URI
   /usr/lib/apache2/mpm-prefork/apache2//HANDLING_UNTRUSTED_INPUT
   /usr/lib/apache2/mpm-prefork/apache2//phpsysinfo
   /usr/lib/lightdm/lightdm-guest-session
   /usr/lib/lightdm/lightdm-guest-session//chromium
   apache2
   apache2//DEFAULT_URI
   apache2//HANDLING_UNTRUSTED_INPUT
   apache2//phpsysinfo
   avahi-daemon
   dnsmasq
   dnsmasq//libvirt_leaseshelper
   dovecot
   dovecot-anvil
   dovecot-auth
   dovecot-config
   dovecot-deliver
   dovecot-dict
   dovecot-dovecot-auth
   dovecot-dovecot-lda
   dovecot-dovecot-lda//sendmail
   dovecot-imap
   dovecot-imap-login
   dovecot-lmtp
   dovecot-log
   dovecot-managesieve
   dovecot-managesieve-login
   dovecot-pop3
   dovecot-pop3-login
   dovecot-script-login
   dovecot-ssl-params
   dovecot-stats
   identd
   klogd
   lsb_release
   mdnsd
   nmbd
   nscd
   ntpd
   nvidia_modprobe
   nvidia_modprobe//kmod
   php-fpm
   ping
   samba-bgqd
   samba-dcerpcd
   samba-rpcd
   samba-rpcd-classic
   samba-rpcd-spoolss
   smbd
   smbldap-useradd
   smbldap-useradd///etc/init.d/nscd
   syslog-ng
   syslogd
   torbrowser_firefox
   torbrowser_tor
   traceroute
   winbindd
0 profiles are in complain mode.
0 profiles are in kill mode.
0 profiles are in unconfined mode.
0 processes have profiles defined.
0 processes are in enforce mode.
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
0 processes are in mixed mode.
0 processes are in kill mode.


```
However I'm a big fan/advocate for what ever works for >>you!
I can Harden Firejail

The security risk of Firejail being a SUID executable can be mitigated by adding the line
```

force-nonewprivs yes
```

to **/etc/firejail/firejail.config**. However, this can break specific applications. Just a Heads up
Ending Statement,
>>> If it's facing the Net, All Bets are Off. ;)

---

