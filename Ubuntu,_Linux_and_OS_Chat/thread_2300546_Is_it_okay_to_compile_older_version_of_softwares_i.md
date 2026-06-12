---
title: "Is it okay to compile older version of softwares in Linux?"
date: 2015-10-26
forum: Ubuntu, Linux and OS Chat
---

### Post by remmas-sido on 2015-10-26
Hello guys 
For example, the latest VLC version available at the moment is 2.2.1 but I would like to compile 2.0.8 because I like it features. The point is:
In Windows we are always advised to upgrade to the latest version available for security reasons? Is it the same in Linux? I am not talking here about PPA, I am not talking here only about VLC. Let's say you compile an older version of a software even older than the one available in the official repositories or software center and everything works fine with you, my question is are you advised to use the version available in the official repositories which is considered newer to the version you compile it? 
Example: 
Ubuntu 12.04 comes with VLC 2.08 I decide to compile VLC 2.01 because I want to and it suits my needs very well, so is it a good idea to use 2.08 over 2.01? am I obliged to?

---

### Post by TheFu on 2015-10-26
There are two ways to look at software updates.
a) newer usually fixes bugs - those can be security or just inconvenience bugs.  If you are impacted, or run the software in the way that a security bug could be exploited, then newer is better. That is not always the situation.
b) sometimes versions break/remove some feature that we really like/need. If there aren't any security impacts in your environment running the older software, then the devil you  know is  best.

Make sense?

For VLC, I would suspect that security issues would mainly be limited to networking code. If you don't use VLC except on a secured LAN, then I wouldn't worry. However, if you stream any content off the internet, then that is risky behavior for the older release.

You'll need to review the release notes and change log for information about what has been fixed from the release you prefer until the current release to make that judgment.

If you decide to build vlc yourself, know that this is a non-trivial effort and if you don't setup a build environment carefully, some dependencies may not work at all. Installing source for the missing libraries is safer than  installing a .deb file directly. Doing that will likely break system dependencies and will likely lead  to  a  system that refuses to be upgrades because  the manually installed .DEB packages would hold-back any dependent packages. Make sense? It really depends on the packages and how many other dependencies there are on a system.

You can have both versions installed on the same machine through careful environment variable management. It isn't really hard at all. This is how we managed that stuff for source packages for many decades. Find a local grey-beard if you get stuck.  30 seconds face-to-face replaces  10 minutes  of my typing.

Hope this helps.

---

### Post by monkeybrain20122 on 2015-10-26
Well depends on how old. For most software that comes with stock Ubuntu they are old already especially if you use a few years old LTS, getting something 'too new' would be the last thing you should worry about :) I would be more interested in compiling new things.

Now if you're talking about something really old (like things that are no longer supported upstream) then it would depends on whether the dependencies are met, sometimes they may still work, other time the libraries that the software depends on may not be compatible with the newer versions that come with the OS. So you may need to compile old versions of those dependencies locally and then use those (instead of system libs) to compile your old software (by changing environmental variables during compiling) Same idea for compiling something 'too new' in that it depends on libs more recent that those supplied by repo.

Also old software may need an old compiler to compile. I have a small math visualization program which I had to compile with an old gcc (which is rather easy for debian based distros because they allow switching between multiple versions of gcc, but for that to work in Fedora I had to build the old compiler first, which was very frustrating)

p.s. I take it that you are only using vlc as an example, not that you really want an ancient version of vlc.  The vlc in stock  14.04 is quite outdated already and the version in 12.04 should really go to the museum.

---

