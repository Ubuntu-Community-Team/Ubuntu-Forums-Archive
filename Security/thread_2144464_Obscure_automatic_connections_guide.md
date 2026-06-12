---
title: "Obscure automatic connections guide"
date: 2013-05-12
forum: Security
---

### Post by F27 on 2013-05-12
I put together a list of obscure automatic remote connections that Ubuntu makes and a guide how to stop them. 

The purpose of this thread:
1.  Educational - provide information to people who would like to  know/control what connections their computer makes. Of course, beside  bugs, these connections are made for a reason, so the point of this  thread is to explain why they are made, and let user decide/justify for  himself the need/use for them.
2. To make Ubuntu better (by exposing bugs - maybe they will get fixed sooner) and more transparent (no surprises in the logs).

Some reasons to stop these connections may be:
1.  Privacy/security concerns about computer connecting to the internet  without any obvious user action/consent (automatic updates being  well-known exclusion) - either because user don't want remote  server/internet provider to be aware of their online "presence" or for  some other reason.
2. Bandwidth/traffic limited connection - when every byte counts.

Some of these connections are known bugs, so everyone is welcome to  log-in/register in Launchpad and set "Yes, it affects me" status, spread  the word and fix them. I think that in order to increase transparency  and user trust, Canonical should publish these info in  Privacy policy or Documentation (with Mozilla being great example, see  (8)). 

If there is any demand, I can try to make a wiki article  based on this information - so feedback, suggestions, corrections are  welcome.

List of obscure automatic remote connections that  Ubuntu makes (with "Include Online Search Results" switch set to "Off"  in Privacy panel of System Settings):

1). Ubuntu GeoIP services. It is currently used to determine if your  timezone has changed. It connects to geoip.ubuntu.com on every boot (or  when internet connection is established). There is currently no way to  remove the geoclue-ubuntu-geoip package without also removing  indicator-datetime.

To disable this connection:
1. Launch dconf-editor (type dconf in the dash)
2. Navigate to com/ubuntu/geoip
3. Set the value of geoip-url to nothing ""
(Note: Ubuntu will lose ability to determine if your timezone has changed)

Relevant bugs:
Add an option to disable geoip check
[https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1120350](https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1120350)
Reduce the dependency on the geoclue-ubuntu-geoip packages to a recommends
[https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1120358](https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1120358)

Sources/more info:
[http://askubuntu.com/questions/135602/i-have-permanent-connections-to-canonical-servers-what-are-they-for-and-how-can](http://askubuntu.com/questions/135602/i-have-permanent-connections-to-canonical-servers-what-are-they-for-and-how-can)
[http://askubuntu.com/questions/106916/how-do-i-stop-geoip-from-connecting-to-the-internet-every-time-i-boot](http://askubuntu.com/questions/106916/how-do-i-stop-geoip-from-connecting-to-the-internet-every-time-i-boot)
[http://askubuntu.com/questions/142581/is-ubuntu-geoip-geoclue-used-for-tracking](http://askubuntu.com/questions/142581/is-ubuntu-geoip-geoclue-used-for-tracking)

2).  Time update/synchronization - connects to ntp.ubuntu.com on every boot.
To disable, open System Settings -> Time & Date -> select "Manually" in "Set the time:"
(Note:  disabling ntp can break things that rely on an accurate time stamp and  an accurate clock, also if your bios battery has problems you may have  to set time manually every now and then to keep clock precise)

3). Remote videos scope. This scope adds a remote video search engine to the Video lens.
Due to bug, it makes empty queries to videosearch.ubuntu.com every few  minutes, even when "Include Online Search Results" set to "Off" in  Privacy panel of System Settings.

To disable these connections, you can remove unity-scope-video-remote package:
Open Ubuntu Software Center, search for unity-scope-video-remote, select/open it, click Remove.
(Note: videos lens will lose ability to search for online videos)

Relevant bug:
Empty queries being sent to videosearch
[https://bugs.launchpad.net/unity-lens-video/+bug/1079699](https://bugs.launchpad.net/unity-lens-video/+bug/1079699)

4). Apps Available for Download. Connection being made when you type  something in Dash search bar with applications lens selected, despite  "Include Online Search Results" switch set to "Off" in Privacy panel of  System Settings.

To disable this connection:
1. Launch dconf-editor (type dconf in the dash)
2. Navigate to desktop/unity/lenses/applications
3. Uncheck the display-available-apps box
(Note: applications lens will lose ability to search for "Apps Available For Download")

Relevant bug:
"Apps Available For Download" are displayed despite "Include Online Search Results" switch set to "Off"
[https://bugs.launchpad.net/ubuntu/+source/unity-lens-applications/+bug/1179179](https://bugs.launchpad.net/ubuntu/+source/unity-lens-applications/+bug/1179179)

Source:
[http://askubuntu.com/questions/37747/how-to-remove-apps-available-for-download-from-the-applications-lens](http://askubuntu.com/questions/37747/how-to-remove-apps-available-for-download-from-the-applications-lens)

5). Remote Login Service. Service to track the remote servers to use. (Ubuntu 12.10 and later)
On every boot, when LightDM starts, it pings  uccs.landscape.canonical.com to make sure the service exists and is  usable before prompting the user to interact with it.

To disable this connection, you can remove remote-login-service package:
Open Ubuntu Software Center, search for remote-login-service, select/open it, click Remove.
(Note: you will lose ability to use remote login from the login screen via RDP (Remote Desktop Protocol))

Source/more info:
[URL="http://askubuntu.com/questions/135602/i-have-permanent-connections-to-canonical-servers-what-are-they-for-and-how-can"]https://help.ubuntu.com/13.04/ubuntu-help/sharing-remote-login.html
http://askubuntu.com/questions/135602/i-have-permanent-connections-to-canonical-servers-what-are-they-for-and-how-can[/URL]

6). Ubuntu error tracker submission. This program submits crash reports back to an Ubuntu server.
Due to bug, it makes DNS queries for daisy.ubuntu.com every few minutes.

To disable them, you can remove whoopsie package:
Open Ubuntu Software Center, search for whoopsie, select/open it, click Remove.
(Note: Ubuntu will lose ability to automatically report bugs)

Revelant bug:
Constant dns traffic for daisy.ubuntu.com
[https://bugs.launchpad.net/whoopsie/+bug/991481](https://bugs.launchpad.net/whoopsie/+bug/991481)

7). Rhythmbox fetching album cover from remote sources if no local one is found.
To disable, launch rhythmbox, click on "Edit" menu -> "Plugins" -> uncheck "Cover art search".
(Note: Rhythmbox will lose ability to search/discover local album covers. Those already cached will stay in place.)

Revelant bug:
Add option to disable fetching content from remote sources
[https://bugzilla.gnome.org/show_bug.cgi?id=700083](https://bugzilla.gnome.org/show_bug.cgi?id=700083)

8). Firefox

How to stop Firefox from automatically making connections without my permission
[https://support.mozilla.org/en-US/kb/how-stop-firefox-automatically-making-connections](https://support.mozilla.org/en-US/kb/how-stop-firefox-automatically-making-connections)

Mozilla Firefox Privacy Policy
[https://www.mozilla.org/en-US/legal/privacy/firefox.html](https://www.mozilla.org/en-US/legal/privacy/firefox.html)


P.S.
 Revelant thread:
Disabling privacy-invasive Zeitgeist, Geoclue, Whoopsie (and NTPD)
 [http://ubuntuforums.org/showthread.php?t=2000108](http://ubuntuforums.org/showthread.php?t=2000108)

---

### Post by Elfy on 2013-05-12
>  I think that in order to increase transparency, user trust, privacy and security, Canonical or community should publish these info in Documentation/Wiki/Privacy policy (with Mozilla being great example, see (8)).

Go ahead and write it then, that's what the community wiki is for. 

I'd assume you'll make sure the wiki is complete with pro's and con's for each thing you've detailed and not just a list - that'll help no-one.

---

### Post by matt_symes on 2013-05-12
Disabling ntp can break things that rely on an accurate time stamp and an accurate clock.

Removing whoopsie will break automatic bug reporting, helping to make this community driven distribution that bit more unstable.

I would address your other points but I'm only really interested in the ones that may break peoples systems, now or in the long run.

---

### Post by cariboo on 2013-05-12
It sounds to me like you would be better off using a different distribution, if you object to the way Ubuntu works.

Instead of uninstalling packages, and maybe breaking something, you can disable remote connections using lightdm.conf, have a look at this [blog]("http://www.mattfischer.com/blog/?p=343")

---

### Post by matt_symes on 2013-05-12
> **cariboo907 said:**
> Instead of uninstalling packages....

Agreed !!

If you really feel the need to ensure your computer does not connect to these services then at least do it by blocking DNS resolution to the IP address.

Edit your /etc/hosts file and get the domain names to point to 127.0.0.1.

```
127.0.0.1 domain.to.block.com
```

Make sure that host is queried before dns in /etc/nsswitch.conf

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

Actually, i need to check the above changes will work still now that dnsmasq points to localhost so i may very well edit this post.

**EDIT:**

Just tested this on 13.04 and the technique of disabling DNS resolution using the hosts file still works. You may have to clear any DNS caches you have.

However, i still think that disabling key functionality is not the most sensible things to do.

---

### Post by F27 on 2013-05-12
I edited the guide: added the purpose of the thread, reasons to stop these connections, notes about consequences of disabling them.

---

### Post by Soul-Sing on 2013-05-13
> It sounds to me like you would be better off using a different distribution, if you object to the way Ubuntu works.
Hmm, thats an easy one, I don't like those statements keeping members away from ubuntu just being critical, and privacy concerned.
On the other hand, the op goes far in his/her concerns. As said by Mark S. 'we are already root'. :)
Serious, I would not remove geo-ip. It breaks the syn server. If you care about Ubuntu, I should not remove whoopsy, because the service improves the distro via bug reports.

---

### Post by F27 on 2013-05-13
> **cariboo907 said:**
> It sounds to me like you would be better off using a different distribution, if you object to the way Ubuntu works.

Instead of uninstalling packages, and maybe breaking something, you can disable remote connections using lightdm.conf, have a look at this [blog]("http://www.mattfischer.com/blog/?p=343")

I like Ubuntu, and don't object to the way it works (I object the bugs) - I just prefer to be in control of my computer.

Why should something break after removing packages? Linux is not Windows. That's what packages dependencies system and package descriptions for - you just have to do a research and be careful (Obviously, you will lose uninstalled package functionality). I remove large ammount of packages I don't need  from my system, and only see faster boot time, more responsive experience and more free disk space.

> **Soul-Sing said:**
> Hmm, thats an easy one, I don't like those statements keeping members away from ubuntu just being critical, and privacy concerned.
On the other hand, the op goes far in his/her concerns. As said by Mark S. 'we are already root'. :)
Serious, I would not remove geo-ip. It breaks the syn server. If you care about Ubuntu, I should not remove whoopsy, because the service improves the distro via bug reports.

As I wrote, my main intention is to make this information open, easy accessible - i.e. in privacy policy (like Mozilla does).
I don't encourage users to remove anything, just point out how to control your experience.
 
I did not suggested to remove geo-ip: "There is currently no way to  remove the geoclue-ubuntu-geoip package without also removing  indicator-datetime."
What is syn server? I would not even mentioned whoopsie, if it's not for the bug.

---

### Post by Soul-Sing on 2013-05-13
> As I wrote, my main intention is to make this information open, easy accessible - i.e. in privacy policy (like Mozilla does).
I don't encourage users to remove anything, just point out how to control your experience.

I did not suggested to remove geo-ip: "There is currently no way to remove the geoclue-ubuntu-geoip package without also removing indicator-datetime."
What is syn server? I would not even mentioned whoopsie, if it's not for the bug. 

yeah, your information is correct, and good to hear you do not encourage removing things perse.

---

### Post by F27 on 2013-05-19
Here's wiki article I made:  (and link to it in [https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking))
[https://help.ubuntu.com/community/AutomaticConnections](https://help.ubuntu.com/community/AutomaticConnections)
Feedback is welcome.

---

### Post by HRJet on 2013-07-08
Thanks @F27 for compiling this list and the wiki page!

I like to keep my PC lean and the number of osbscure connections from my PC was bothering me.

There is one type of connection which is bothering me: 
> [FONT=courier new] tcp     2068      0 hrj-laptop.local:47320  papeda.canonical.c:http CLOSE_WAIT  5536/gvfsd-http[/FONT]

There are about a dozen such connections in my PC. Wondering what those are.

There is also this one:
>  [FONT=courier new]tcp        0      0 hrj-laptop.local:48658  feijoa.canonical.c:http TIME_WAIT   -[/FONT]   

The PID is not avaialble for that one!

Any clues about these?

---

### Post by F27 on 2013-07-14
> **HRJet said:**
> Thanks @F27 for compiling this list and the wiki page!  I like to keep my PC lean and the number of osbscure connections from my PC was bothering me.  There is one type of connection which is bothering me:    There are about a dozen such connections in my PC. Wondering what those are.  There is also this one:   The PID is not avaialble for that one!  Any clues about these?  I think gvfsd-http connections are established when you use Software Center and Dash right click previews on applications.

---

