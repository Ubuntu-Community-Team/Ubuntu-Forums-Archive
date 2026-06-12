---
title: "Why isnt apparmor firefox profile enabled by default?"
date: 2010-04-25
forum: Security
---

### Post by jasonmchristos on 2010-04-25
This page [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor) shows how to enable apparmor firefox profile. Why isnt apparmor firefox profile enabled by default? I would postulate that this would be because  there must be some limitation by having the profile enabled. If so, what would the limitation be?:confused:

---

### Post by rookcifer on 2010-04-25
> **jasonmchristos said:**
> This page [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor) shows how to enable apparmor firefox profile. Why isnt apparmor firefox profile enabled by default? I would postulate that this would be because  there must be some limitation by having the profile enabled. If so, what would the limitation be?:confused:

Short answer: not everyone has the same needs from Firefox, so enabling the profile by default might "break" Firefox for some people and might be too permissive for others.

---

### Post by lovinglinux on 2010-04-25
> **rookcifer said:**
> Short answer: not everyone has the same needs from Firefox, so enabling the profile by default might "break" Firefox for some people and might be too permissive for others.

+1

For instance, it might break extensions functions.

---

### Post by Rubi1200 on 2010-04-25
So, here's the thing; if I enable the AppArmor profile for Firefox and things get messed up can I just disable it and everything will be back to "normal"? Secondly, I don't understand what the default profile is doing; a brief explanation about what it protects/prevents would be nice.
Thanks in advance

---

### Post by rookcifer on 2010-04-25
> **Rubi1200 said:**
> So, here's the thing; if I enable the AppArmor profile for Firefox and things get messed up can I just disable it and everything will be back to "normal"? 

Yes.  

> Secondly, I don't understand what the default profile is doing; a brief explanation about what it protects/prevents would be nice.
Thanks in advance

There is an apparmor sticky at the top of this forum which explains a lot of this.

---

### Post by Rubi1200 on 2010-04-25
Thanks!
I will check out the sticky as well.
:)

---

### Post by Rubi1200 on 2010-04-25
Ok, so I read the sticky and understood perhaps 70-80%. If I enable the default profile am I protected in the way that AppArmor intends the system to be protected? Lastly, is there a real need to use the profile and is it considered as THE recommended approach to security in Ubuntu?

---

### Post by Rubi1200 on 2010-04-26
Another question: if the default profile for Firefox that ships with 9.10 is too restrictive which of the profiles posted by bodhi.zazen would be most appropriate?
FYI: I have no extensions installed or other addons. I use the default Firefox/Ubuntu pack that ships with the distro.
Thanks in advance.

---

### Post by bodhi.zazen on 2010-04-26
> **Rubi1200 said:**
> Another question: if the default profile for Firefox that ships with 9.10 is too restrictive which of the profiles posted by bodhi.zazen would be most appropriate?
FYI: I have no extensions installed or other addons. I use the default Firefox/Ubuntu pack that ships with the distro.
Thanks in advance.

That is why it is not enabled by default =)

If you use the default FF profile, you will be using apparmor in a generic way, ie should work for most people most of the time.

If you do not like the default profile, either too restrictive or too loose, you will need to modify the profile yourself.

Only you can decide what is most appropriate for you.

---

### Post by Rubi1200 on 2010-04-26
Thanks for replying. Do you recommend using the default profile? In your AppArmor sticky you say that you want to encourage people to use AppArmor. But I am a bit confused as to whether or not I really need it.
Thanks in advance.

---

### Post by bodhi.zazen on 2010-04-26
If it is working I would use the default profile for firefox.

I would encourage people to at least install and enable apparmor

```
sudo apt-get install apparmor-profiles
sudo aa-enforce /etc/apparmor.d/*
```

If you wish to investigate and learn apparmor beyond that, more power to you.

---

### Post by Rubi1200 on 2010-04-26
Thanks! I think I may give it a try and see what happens. When I installed 9.10 I saw that AppArmor is installed and 10 profiles are enabled with default settings (I assume this is normal?).
Anyway, I will continue reading and trying to learn.

---

### Post by rookcifer on 2010-04-27
> **Rubi1200 said:**
> Thanks for replying. Do you recommend using the default profile? In your AppArmor sticky you say that you want to encourage people to use AppArmor. But I am a bit confused as to whether or not I really need it.
Thanks in advance.

TBH, you probably don't *need* it, especially if you keep Firefox up to date.  However,it can be a good learning experience and a nice introduction into the world of Mandatory Access Controls.  It will prepare you for really complicated systems like SELinux (which make AppArmor look like a freshman CS project).  However, being simple is probably the greatest strength of AA.

---

### Post by Rubi1200 on 2010-04-27
I do keep Firefox updated as well as watching where I go on the web, but I am interested in Linux security. I have not enabled the profile yet because I am still reading about AppArmor and what it is all about. Do you think the average Ubuntu user should be using profiles like this or just stick with the default installation?
There seems to be a ton of information on the web, mostly dealing with security in Linux. On the one hand, I am fascinated by the subject, but I also realize how easy it would be to mess up my install. On the other hand, curiosity...
Thanks.
:)

---

### Post by lovinglinux on 2010-04-27
> **Rubi1200 said:**
> I do keep Firefox updated as well as watching where I go on the web, but I am interested in Linux security. I have not enabled the profile yet because I am still reading about AppArmor and what it is all about. Do you think the average Ubuntu user should be using profiles like this or just stick with the default installation?
There seems to be a ton of information on the web, mostly dealing with security in Linux. On the one hand, I am fascinated by the subject, but I also realize how easy it would be to mess up my install. On the other hand, curiosity...
Thanks.
:)

Only you can decide what is good for you. I don't use AppArmor for Firefox because it gave me too many warnings I couldn't understand. Besides, I upgrade every six months with a clean install, keep everything up-to-date and use these [security extensions](https://addons.mozilla.org/en-US/firefox/collection/securityandprivacy). Never had a problem. But that's me. I'm willing to sacrifice "a bit" of security to gain convenience. If you use AppArmor you will be certainly better protected.

---

### Post by rookcifer on 2010-04-27
> **Rubi1200 said:**
> I do keep Firefox updated as well as watching where I go on the web, but I am interested in Linux security. I have not enabled the profile yet because I am still reading about AppArmor and what it is all about. Do you think the average Ubuntu user should be using profiles like this or just stick with the default installation?
There seems to be a ton of information on the web, mostly dealing with security in Linux. On the one hand, I am fascinated by the subject, but I also realize how easy it would be to mess up my install. On the other hand, curiosity...
Thanks.
:)

Go ahead and enable it and play around with it.  If it gives you problems, just disable it again (or put it in complain mode).  It wont break your system.

---

### Post by Rubi1200 on 2010-04-27
Thanks rookcifer and lovinglinux, I appreciate the feedback. I think I will try it out after reading a bit more first. Security is something I take seriously and AppArmor seems to be a tool at the forefront of Linux security. Additionally, the default install of Karmic already came with 10 profiles enabled and since it is easy to turn off again, I see no reason not to add this extra layer of security to the install.
Thanks again to you both.

---

### Post by bodhi.zazen on 2010-04-27
IMO, apparmor, and similar tools, are not in common use because people have been secure enough without these tools enabled. Linux is very secure by default and although you can find examples of compromised systems, such events are very rare, so people do not feel the need to learn / use apparmor.

Not to single anyone out, but if lovinglinux found s/he was compromised by his or her firefox practices, I would imagine the interest in learning apparmor would increase rapidly.

lovinglinux: If you need help with apparmor, ask in a support thread. I would imagine you could lock down firefox in short order (because you already understand much more the the average user about how firefox works).

If there comes a time when linux exploits become more common place, tools such as apparmor will be more and more popular.

As they become more popular they will become more usable (default profiles available for all network aware applications, gui tools, etc).

IMO apparmor makes sense, it does take a few hours to learn, but, really, once you learn to use it you can write and customize profiles in a few minutes.

Firefox is not a good one to start with as firefox is a large application and interacts with many system files. In addition there are hundreds if not thousands of user customizations so a default profile that works for everyone is difficult.

Start small, say something like privoxy or the gnome weather applet.

Tools such as apparmor and selinux are more of a consideration on servers.

SELinux is a bit more mature and more complex, but there are better tools to manage selinux and the documentation is better. I have been using both selinux and apparmor for some time and can write a policy or profile for many applications within what I consider a reasonable time frame.

---

### Post by lovinglinux on 2010-04-27
> **bodhi.zazen said:**
> lovinglinux: If you need help with apparmor, ask in a support thread. I would imagine you could lock down firefox in short order (because you already understand much more the the average user about how firefox works).

Thanks, but I'm doing a lot of FF development recently and most of the time I need full access for testing and debugging. So probably it would be disable 99% of the time anyway. I'm already going crazy trying to figure out why the new version of one of my extensions is not working on a VM, while it works perfectly on my machine :)

BTW I'm a "he" :)

---

### Post by jasonmchristos on 2010-05-01
[QUOTE=Rubi1200;9172716]Secondly, I don't understand what the default profile is doing; a brief explanation about what it protects/prevents would be nice.
 Well if fiefox is exploited someone may want to read the password files on the system using a Firefox exploit in attempts to crack them and gain access to your system. Skype for instance does this by default, the skype software is programmed to probe all of the sensitive areas on your system, however I found that the apparmor extra profile that is supposed to keep skype in line renders the current version of skype unusable. Looks like i will have to actually make my own profile. In short the firefox profile puts restrictions on what firefox can do. I am not sure of the exact details yet since i havent got too deep into apparmor yet. I heard through the grapevine that canonical intends to abandon apparmor for selinux. Not sure if I should be spending a lot of time on learning apparmor.

---

### Post by djchandler on 2010-05-06
That is truly puzzling. I think I posted almost that very question on ZDNet ([Hardware 2.0 April 26th]("http://www.zdnet.com/blog/hardware/can-switching-to-linux-protect-your-online-identity/8120"))  in answer to one of our fellow Ubuntites touting the advantages of using Ubuntu to the great unwashed. It's better to hedge a bit about your fervor to maintain some credibility amongst the fanbois of other platforms.
[I]
"Why isn't the Firefox profile for Apparmor activated by default?"[/I] That was my opening line in my Talkback.

Nice job on the thread topic, [jasonmchristos]("http://ubuntuforums.org/member.php?u=842442")! Obviously I have been wondering the same thing myself.;)

---

### Post by Velnias on 2010-05-06
Maybe because of possible further questions like "Why Firefox needs to read my whole /etc (including passwords file)?"...

---

### Post by bodhi.zazen on 2010-05-06
> **djchandler said:**
> That is truly puzzling. I think I posted almost that very question on ZDNet ([Hardware 2.0 April 26th]("http://www.zdnet.com/blog/hardware/can-switching-to-linux-protect-your-online-identity/8120"))  in answer to one of our fellow Ubuntites touting the advantages of using Ubuntu to the great unwashed. It's better to hedge a bit about your fervor to maintain some credibility amongst the fanbois of other platforms.
[I]
"Why isn't the Firefox profile for Apparmor activated by default?"[/I] That was my opening line in my Talkback.

Nice job on the thread topic, [jasonmchristos]("http://ubuntuforums.org/member.php?u=842442")! Obviously I have been wondering the same thing myself.;)

There are two issues :

1. The broader issue - Apparmor is relatively new and it is extremely frustrating if a system is broken by security features. Look at SELinux - Fedora has been shipping with selinux enabled by default for some time, and it mostly works now, but if you go back to Fedora 5-10 or so almost every tutorial ever written for Fedora starts with disabling SELinux.

Until the apparmor profiles are polished enough that the will work for the majority of people the majority of the time IMO they should not be enabled.

IMO we should encourage people to use apparmor and report bugs so that the profiles can be refined to the point where they are ready.

2. Firefox specific - Firefox is a bad example. I agree it is one of the applications most in need of confinement, but, people use Firefox for almost everything from multimedia (flash / you tube) to Opening documents (Open office , evince) to browsing documentation, to sys administration (apt-url), to managing remote servers (you may tunnel VNC over firefox), to using proxy servers (privoxy / tor), to tunneling socks over ssh, and probably a few things I forgot to list.

So the resulting profile for firefox , that "just works" for everyone would almost be so permissive to be useless to most people.

/bin/firefox {

/** rw,
/usr/bin/ rwUix,
}

well, you get the idea ...

Take a look at the current default firefox profile, I always need to edit the file and add restriction.

Also graphical tools are in development for apparmor, and so profiles need to be quiet or the graphical tools generate hundreds of warnings :

[http://img685.imageshack.us/i/201004262348371280x800s.png/](http://img685.imageshack.us/i/201004262348371280x800s.png/)

300 warnings ??? What do you think the average user would do if he or she saw 300 warnings from apparmor ?

So, while firefox will run if you deny access to files scus as /etc/passwd , if you do so you generate many more warnings, thus the profiles will need to be even more permissive.

On the flip side, how many boxes are cracked due to the lack of an apparmor profile ? I am aware of 0 .

Last, apparmor went through some "growing pains" and could benefit from users willing to test and debug the profiles.

Some people have suggested Ubuntu migrate to SELinux which is more mature then apparmor.

---

### Post by rookcifer on 2010-05-06
An easier way to running a confined browser is to use the nightly Chromium-builds from the PPA.  They are built with the chromium-sandbox (the "SUID sandbox" which is essentially a chroot).  There are actually [2 or 3 different sandboxes]("http://code.google.com/p/chromium/wiki/LinuxSandboxing") the Chromium team has developed for Linux.  

I have been using these nightly builds and am loving them on Lucid (not so much on Karmic where they crashed often for some reason). Chromium is *much* faster than FF and also has a wide selection of plugins.  I really think FF is going to have some heated competition from Chrome in the next few years.

At any rate, just a suggestion for anyone looking for an alternative to Firefox AA profiles.

---

### Post by bodhi.zazen on 2010-05-06
> **rookcifer said:**
> At any rate, just a suggestion for anyone looking for an alternative to Firefox AA profiles.

See :
[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/)

I have profiles there for ff, chromium, and opera (and a few others as well .... )

---

### Post by rookcifer on 2010-05-06
> **bodhi.zazen said:**
> See :
[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/)

I have profiles there for ff, chromium, and opera (and a few others as well .... )

I think having profiles for Chrome is redundant at this point, which is why I haven't generated my own (as I typically do with FF).

---

### Post by bodhi.zazen on 2010-05-06
> **rookcifer said:**
> I think having profiles for Chrome is redundant at this point, which is why I haven't generated my own (as I typically do with FF).

Not at all, it depends on what your wish to restrict.

IMO one of the major uses of apparmor is to restrict access to files in $HOME .

For example, make a ssh key, keep it in ~/.ssh

Without an apparmor profile you can open the keys files with chromium, including the private key.

Now try to open the same file with my apparmor profile enabled.

See the need ? System files are not the only consideration, lots of damage can, in theory, if not in practice, be done without escalating to root privileges and without changing system files, access to such files in an account with administrative access is one very tiny step short of root access.

That is but one example, there are other files in $HOME, primarily configuration or dot ( . ) files, one may wish to lock down. The profiles on my server are fairly permissive that way to reduce alerts on apparmor-notify. I use more restrictive profiles on some more sensitive boxen.

---

### Post by rookcifer on 2010-05-07
> **bodhi.zazen said:**
> Not at all, it depends on what your wish to restrict.

IMO one of the major uses of apparmor is to restrict access to files in $HOME .

For example, make a ssh key, keep it in ~/.ssh

Without an apparmor profile you can open the keys files with chromium, including the private key.

Now try to open the same file with my apparmor profile enabled.

See the need ? System files are not the only consideration, lots of damage can, in theory, if not in practice, be done without escalating to root privileges and without changing system files, access to such files in an account with administrative access is one very tiny step short of root access.

That is but one example, there are other files in $HOME, primarily configuration or dot ( . ) files, one may wish to lock down. The profiles on my server are fairly permissive that way to reduce alerts on apparmor-notify. I use more restrictive profiles on some more sensitive boxen.

You make a good point.  /home should always be a concern, because as we all know, a lot of Linux compromises are not root compromises (too difficult in many cases), so accessing files in the /home folder and the potential to send spam are big considerations of would be crackers.

I suppose it all boils down to what the Chrome sandbox confines.  It is my understanding it doesn't give the renderer much of any access at all to the filesystem, though the details are a bit thin.

---

### Post by zong1 on 2010-08-15
> **rookcifer said:**
> Yes.  

There is an apparmor sticky at the top of this forum which explains a lot of this.

Nope. I cannot see a sticky thread about AppArmour in :
Ubuntu Forums > The Ubuntu Forum Community > Main Support Categories > Security Discussions . However, I won't discount the possibility that I am partially blind.

---

### Post by zong1 on 2010-08-15
@bodhi.zazen
 I am very pleased to see a list of apparmour profiles, especially that you have included Snort Squid Opera and Privoxy.  I have to rebuild a squid server next month (move from Debian to SLES) and would be very interested to try it with apparmour running.

I quickly added the Opera profile and enforced it.  Opera would not start.
So I disabled.  If I am correct, in order to make it work I may have to change the the paths below to be allowed access by Opera: What confuses me is that the k is a lock: What has locked the file?  Was it Opera (locking itself :) or another process?

```

Aug 15 11:14:41 kakey kernel: [ 3915.351826] __ratelimit: 3 callbacks suppressed
Aug 15 11:14:41 kakey kernel: [ 3915.351830] type=1503 audit(1281863681.458:93):  operation="file_lock" pid=30226 parent=1 profile="/usr/bin/opera" requested_mask="k::" denied_mask="k::" fsuid=1000 ouid=1000 name="/home/smelly/.config/user-dirs.dirs"
Aug 15 11:14:41 kakey kernel: [ 3915.352833] type=1503 audit(1281863681.462:94):  operation="file_lock" pid=30226 parent=1 profile="/usr/bin/opera" requested_mask="::k" denied_mask="::k" fsuid=1000 ouid=0 name="/usr/share/opera/locale/en/en.lng"
Aug 15 11:14:41 kakey kernel: [ 3915.352962] type=1503 audit(1281863681.462:95):  operation="file_lock" pid=30226 parent=1 profile="/usr/bin/opera" requested_mask="::k" denied_mask="::k" fsuid=1000 ouid=0 name="/usr/share/opera/locale/en/en.lng"
Aug 15 11:14:41 kakey kernel: [ 3915.353070] type=1503 audit(1281863681.462:96):  operation="file_lock" pid=30226 parent=1 profile="/usr/bin/opera" requested_mask="::k" denied_mask="::k" fsuid=1000 ouid=0 name="/usr/share/opera/locale/en/en.lng"
Aug 15 11:14:41 kakey kernel: [ 3915.353167] type=1503 audit(1281863681.462:97):  operation="file_lock" pid=30226 parent=1 profile="/usr/bin/opera" requested_mask="k::" denied_mask="k::" fsuid=1000 ouid=1000 name="/home/smelly/.config/user-dirs.dirs"
Aug 15 11:14:41 kakey kernel: [ 3915.357962] type=1503 audit(1281863681.466:98):  operation="file_lock" pid=30226 parent=1 profile="/usr/bin/opera" requested_mask="k::" denied_mask="k::" fsuid=1000 ouid=1000 name="/home/smelly/.config/user-dirs.dirs"
Aug 15 11:14:41 kakey kernel: [ 3915.358199] type=1503 audit(1281863681.466:99):  operation="file_lock" pid=30226 parent=1 profile="/usr/bin/opera" requested_mask="k::" denied_mask="k::" fsuid=1000 ouid=1000 name="/home/smelly/.config/user-dirs.dirs"
Aug 15 11:14:42 kakey kernel: [ 3916.501324] type=1503 audit(1281863682.610:100):  operation="file_lock" pid=30226 parent=1 profile="/usr/bin/opera" requested_mask="::k" denied_mask="::k" fsuid=1000 ouid=0 name="/usr/share/opera/encoding.bin"
Aug 15 11:14:42 kakey kernel: [ 3916.527281] type=1503 audit(1281863682.634:101):  operation="file_lock" pid=30226 parent=1 profile="/usr/bin/opera" requested_mask="::k" denied_mask="::k" fsuid=1000 ouid=0 name="/usr/share/opera/defaults/pluginpath.ini"
Aug 15 11:14:42 kakey kernel: [ 3916.527548] type=1503 audit(1281863682.634:102):  operation="file_lock" pid=30226 parent=1 profile="/usr/bin/opera" requested_mask="::k" denied_mask="::k" fsuid=1000 ouid=0 name="/usr/share/opera/defaults/plugin-ignore.ini"

```

Is your file private-files required by the opera profile?

---

### Post by bodhi.zazen on 2010-08-15
Those are problems with the opera apparmor profile.

I will edit the profile and you can either review the changes or dl the new version.

Edit: Profile updated.

---

### Post by zong1 on 2010-08-17
Hi,

  I added the profile and Opera runs. Thank-you very much.  

AppArmour complains about the Picasa plug-in, which may well be a good thing given my love for Google these days ;)   
/opt/google/picasa/3.0/lib/npPicasa3.so

I noticed that it logged to messages and nothing was placed in /var/log/apparmour.

Below are the messages, in case these are of use to someone.

```

Aug 17 21:49:21 pan-pan kernel: [ 5001.628826] operapluginwrap[32238]: segfault at 0 ip (null) sp bfb0a61c error 4 in libm-2.11.1.so[110000+24000]
Aug 17 21:49:21 pan-pan kernel: [ 5001.813070] operapluginwrap[32244]: segfault at 0 ip (null) sp bfc682cc error 4 in libXau.so.6.0.0[110000+2000]
Aug 17 21:49:21 pan-pan kernel: [ 5001.846404] type=1503 audit(1282074561.886:72):  operation="open" pid=32246 parent=32230 profile="/usr/bin/opera" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/opt/google/picasa/3.0/lib/npPicasa3.so"
Aug 17 21:49:21 pan-pan kernel: [ 5001.846429] type=1503 audit(1282074561.886:73):  operation="open" pid=32246 parent=32230 profile="/usr/bin/opera" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/opt/google/picasa/3.0/lib/npPicasa3.so"
Aug 17 21:49:22 pan-pan kernel: [ 5002.073534] operapluginwrap[32250]: segfault at 0 ip (null) sp bff400fc error 4 in libgcc_s.so.1[110000+1d000]
Aug 17 21:49:22 pan-pan kernel: [ 5002.094830] operapluginwrap[32251]: segfault at 0 ip (null) sp bf9eab9c error 4 in libX11.so.6.3.0[110000+119000]
Aug 17 21:49:22 pan-pan kernel: [ 5002.147523] operapluginwrap[32253]: segfault at 0 ip (null) sp bf9a231c error 4 in libX11.so.6.3.0[110000+119000]
Aug 17 21:49:22 pan-pan kernel: [ 5002.173851] operapluginwrap[32255]: segfault at 0 ip (null) sp bf8de6ec error 4 in libstdc++.so.6.0.13[110000+e9000]
Aug 17 21:49:22 pan-pan kernel: [ 5002.187198] type=1503 audit(1282074562.226:74):  operation="open" pid=32256 parent=32230 profile="/usr/bin/opera" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/opt/google/picasa/3.0/lib/npPicasa3.so"

```

Many thanks, z

---

### Post by bodhi.zazen on 2010-08-17
Open the opera profile and add this line.

```
/opt/google/picasa/** r,
```

You may need to change the "r," to "rixmk," (not sure how many of those permissions you will need, you will need to watch the logs).

You may need to make additional edits, see the apparmor sticky for how to do that =)

---

### Post by zong1 on 2010-08-17
Thank-you.  

By the way, I tried to launch PDFs from within Opera but this failed as well.  The call is to evince ; Evince is set to complain mode only. 

I suppose I could add:

/usr/bin/evince r,

```

Aug 17 22:38:26 pan-pan kernel: [ 7946.346156] type=1503 audit(1282077506.386:1016):  operation="exec" pid=715 parent=1 profile="/usr/bin/opera" requested_mask="::x" denied_mask="::x" fsuid=1000 ouid=0 name="/usr/bin/evince"
Aug 17 22:38:42 pan-pan kernel: [ 7962.344237] type=1503 audit(1282077522.386:1017):  operation="exec" pid=719 parent=1 profile="/usr/bin/opera" requested_mask="::x" denied_mask="::x" fsuid=1000 ouid=0 name="/usr/bin/evince"

```

---

### Post by bodhi.zazen on 2010-08-17
ixr

you have gotten a start, but you are hijacking another thread and you need to read.

---

### Post by zong1 on 2010-08-18
> **bodhi.zazen said:**
> ixr
...but you are hijacking another thread and you need to read.

Your sentence is incomplete, but I think you meant to write:
     "... and you need to read more about AppArmour."  Which I shall do now.  

I thank you for giving me some examples that I could add to the Opera profile.  This means that I can develop this further.  I am off to read some more about it.  Consider this thread now jacked back into its original position.

---

### Post by bodhi.zazen on 2010-08-18
> **zong1 said:**
> Your sentence is incomplete, but I think you meant to write:
     "... and you need to read more about AppArmour."  Which I shall do now.  

I thank you for giving me some examples that I could add to the Opera profile.  This means that I can develop this further.  I am off to read some more about it.  Consider this thread now jacked back into its original position.

Thank you.

As you use apparmor, if you have questions, start a new thread ;)

---

