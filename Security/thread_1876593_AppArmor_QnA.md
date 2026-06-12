---
title: "AppArmor QnA"
date: 2011-11-06
forum: Security
---

### Post by vasa1 on 2011-11-06
DangerTux has a write-up on AppArmor and has kindly agreed to answer questions on it:
[Apparmor Profiles Quickly, if not easily.]("http://dangertux.wordpress.com/2011/10/09/apparmor-profiles-quickly-if-not-easily/")

For my convenience, I copied the article and pasted it into gedit so that I could make reference to line numbers. Just to clarify:
Line 1 has just "Introduction"
Line 2 is blank
Line 3 is this: "With the release of Ubuntu 11.10 Oneiric Ocelot upon us, I decided I would discuss one of the lesser used security features bundled with Ubuntu, Apparmor. Apparmor is actually a great utility particularly in terms of desktop security where browser exploits can become ridiculous quickly. It is suited for production applications as well, however often times is forgone due to the resources confining an application can require."
And so on.

My questions so far are:
Line 3: *however often times is forgone due to the **resources** confining an application can require.*
*What resources? CPU, RAM?*

Line 15: *sudo apt-get install apparmor-utils*
Is it needed? My list of installed software shows:
apparmor		install
apparmor-utils		install

Line 17: *For this guide we will be constructing a profile for Chromium Browser you can install it by doing the following*
Why did you choose Chromium and not Firefox? Is it just a precaution not to mess with the "default" browser? Can those of us who have Firefox and Chrome follow along using Chrome?

[CENTER]:::::::::::::::::::::::::::::::[/CENTER]

---

### Post by Dangertux on 2011-11-06
> **vasa1 said:**
> DangerTux has a write-up on AppArmor and has kindly agreed to answer questions on it:
[Apparmor Profiles Quickly, if not easily.]("http://dangertux.wordpress.com/2011/10/09/apparmor-profiles-quickly-if-not-easily/")

For my convenience, I copied the article and pasted it into gedit so that I could make reference to line numbers. Just to clarify:
Line 1 has just "Introduction"
Line 2 is blank
Line 3 is this: "With the release of Ubuntu 11.10 Oneiric Ocelot upon us, I decided I would discuss one of the lesser used security features bundled with Ubuntu, Apparmor. Apparmor is actually a great utility particularly in terms of desktop security where browser exploits can become ridiculous quickly. It is suited for production applications as well, however often times is forgone due to the resources confining an application can require."
And so on.

My questions so far are:
Line 3: *however often times is forgone due to the **resources** confining an application can require.*
*What resources? CPU, RAM?*

Line 15: *sudo apt-get install apparmor-utils*
Is it needed? My list of installed software shows:
apparmor        install
apparmor-utils        install

Line 17: *For this guide we will be constructing a profile for Chromium Browser you can install it by doing the following*
Why did you choose Chromium and not Firefox? Is it just a precaution not to mess with the "default" browser? Can those of us who have Firefox and Chrome follow along using Chrome?

[CENTER]:::::::::::::::::::::::::::::::[/CENTER]


I chose chromium because Ubuntu comes with an Apparmor profile for firefox. Also chromium utilizes a lot of features that allowed me to expound on some other functionality of apparmor.

apparmor utils is necessary for completing the guide as written. Otherwise you'll be writing the profile by hand and examining logs by hand.

As far as resources go yes, cpu and ram, but on a normal machine they are negligible.

---

### Post by Elfy on 2011-11-06
Thread moved to Security Discussions.

---

### Post by vasa1 on 2011-11-06
> **Dangertux said:**
> I chose chromium because Ubuntu comes with an Apparmor profile for firefox. Also chromium utilizes a lot of features that allowed me to expound on some other functionality of apparmor.

apparmor utils is necessary for completing the guide as written. Otherwise you'll be writing the profile by hand and examining logs by hand...

Can we follow along with Chrome instead of Chromium?

And apparmor utils is also installed by default, if the list is correct.

So is Firefox "protected" by AppArmor by default? How can we tell?

---

### Post by Dangertux on 2011-11-06
I didnt test it with chrome. Try it and see. 

The apparmor profile for firefox is disabled by default I think. 

You can check to see if it is being enforced by typing

```

sudo aa-status

```

The install I had didn't have apparmor utils but if yours did then you're good.

---

### Post by Brian0312 on 2011-11-06
I've been using AppArmor for about a week now and I was going to start a thread with my own question, but since this exists now, I thought I'd ask here instead.

I've enabled the Firefox profile (among others).  I'm wondering though with the whole "sub profile" thing, should I consider making one for both flash and java, or is that more or less confined by being used as a plug in for Firefox to begin with?

---

### Post by vasa1 on 2011-11-07
> **Dangertux said:**
> ...
The apparmor profile for firefox is disabled by default I think. 
...
You can check to see if it is being enforced by typing
```

sudo aa-status

```
...
This is what I get on typing the code suggested:
```
apparmor module is loaded.
13 profiles are loaded.
13 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/lightdm/lightdm-guest-session-wrapper
   /usr/lib/telepathy/mission-control-5
   /usr/lib/telepathy/telepathy-*
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
   /usr/share/gdm/guest-session/Xsession
0 profiles are in complain mode.
2 processes have profiles defined.
2 processes are in enforce mode.
   /usr/lib/telepathy/mission-control-5 (1669) 
   /usr/sbin/cupsd (999) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.

```
As you hinted, the Firefox profile isn't being enforced! Isn't that odd? I can't remember where I read it or even if I remember correctly, but the rapid changes in Fx version number may have something to do with it not being on by default?

Looking at the profile, there are several *uncommented* lines containing a reference to the version number:
```
/usr/lib/firefox-7.0.1/
```

I would have thought this would be better publicized even if as a *user beware*?

So how many security-conscious users of Ubuntu have dived in and enable the Firefox profile? (I'm going to do so as soon as I can figure out how to do it properly. If you never hear from me again, then ...)

---

### Post by vasa1 on 2011-11-07
> **vasa1 said:**
> ...
As you hinted, the Firefox profile isn't being enforced! Isn't that odd? I can't remember where I read it or even if I remember correctly, but the rapid changes in Fx version number may have something to do with it not being on by default?
...

I came across [this page]("https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/AppArmorProfiles") which makes it clear that not enabling the Firefox profile by default will continue even in 12.04:
> Will be disabled by default and be opt-in for advanced users
And it doesn't appear to be linked to changes in version number because the appropriate profile will be incorporated in the new version.

---

### Post by OpSecShellshock on 2011-11-07
> **vasa1 said:**
> I came across [this page]("https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/AppArmorProfiles") which makes it clear that not enabling the Firefox profile by default will continue even in 12.04:

Most likely this is for the same reason it hasn't been up to now, which from what I understand is because of the potential number of unique use cases making it difficult to predict exactly how Firefox should be properly confined.

---

### Post by vasa1 on 2011-11-07
Here's a nice read (last edited 2010-03-21) on why it isn't **on** by default:
[https://wiki.ubuntu.com/SecurityTeam/Specifications/Karmic/AppArmorFirefoxProfile](https://wiki.ubuntu.com/SecurityTeam/Specifications/Karmic/AppArmorFirefoxProfile)

---

### Post by vasa1 on 2011-11-10
> **Brian0312 said:**
> I've been using AppArmor for about a week now and I was going to start a thread with my own question, but since this exists now, I thought I'd ask here instead.

I've enabled the Firefox profile (among others).  I'm wondering though with the whole "sub profile" thing, should I consider making one for both flash and java, or is that more or less confined by being used as a plug in for Firefox to begin with?

Hi Brian, you could try asking over in this thread (which I didn't know existed): [http://ubuntuforums.org/showthread.php?t=1049698](http://ubuntuforums.org/showthread.php?t=1049698)

My *suspicion* is that plug-ins and extensions will also be confined. Otherwise the whole thing will get close to impossible!

---

