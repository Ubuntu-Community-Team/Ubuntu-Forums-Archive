---
title: "vncserver daemonized to display gdm on lucid?"
date: 2010-05-05
forum: Server Platforms
---

### Post by liquidonline on 2010-05-05
I just did a fresh install on a headless server at home I often use for virtualizing and remote file storage, and simple access to a gnome/xfce desktop from windows PC's.  I went from jaunty (desktop) to lucid (server).  Running Jaunty, I was able to run vnc4server in such a way that it was launched with xinetd and ran as root, logging in on the vnc gave me a gdm chooser window.  

My research has been extensive over the past 2-3 days.  I know what changed (gdm regressions) and have heard about all the alternatives. I never wanted to use alternatives and stick to what I knew and worked well for me.  However, even in this case, alternatives appear to be lacking.  I have no familiarity with FreeNX, but it seems it's missing in lucid, replaced with neatx from google, but there is ZERO documentation on this (another thing I love about linux) and the guides for FreeNX certainly did not work to get neatx working for me.  Lastly, it seems that gdm 2.20 does not exist in lucid repos anymore.  I feel like I'm out of options.

So.  If anyone has some ideas on how I can gain remote desktop access to my ubuntu server without having direct ssh access (actually at this point even local LAN remote desktop would be nice) I'm all ears.  This is very frustrating, I don't understand how something like this requires such difficulty setting up.  The included remote desktop junk with ubuntu, when I do plug in a monitor is PAINFULLY slow, and still requires a local login first.


=================================================
BTW, because I've noticed that many forum topics across sites always include pseudo geniuses who say you shouldn't use vnc, that a real sysadmin uses ssh yada yada yada... For starters, I ran VNC server on a machine which had no access to the internet, and I was ssh portforwarding on an openbsd router to tunnel my vnc sessions through it, so it was secure.  I know you can admin a machine using ssh blah blah blah, and I do. Most administrative work is done via ssh, but sometimes, it's just super convenient to be able to do gui stuff on that machine, rather than whomever's laptop or what not, so that any work I may do is saved there.  Using X-Forwarding is not only horribly slow/unresponsive on external connections, but is also difficult to do unless I open a pinhole on my router to access the server, which I don't care to do.  Ubuntu is hardly hardened out of the box compared to openbsd, and it's a simple quick tool, I'd rather not have to figure out how to harden linux.

---

