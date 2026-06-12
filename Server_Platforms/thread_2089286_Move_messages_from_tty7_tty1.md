---
title: "Move messages from tty7 tty1"
date: 2012-11-28
forum: Server Platforms
---

### Post by JheregJAB on 2012-11-28
I am trying to make the move from a very old, custom, from-scratch linux install to a more modern and supported Ubuntu distribution. On my custom linux install and the old init daemon, I had things setup on this server so that when a keyboard and monitor were connected, any messages (both from boot and afterwards) were displayed right away on tty1. The user could then press alt+f{2..6} to get a console and sign in.

Since I have moved to Ubuntu, the startup messages are displayed on tty1, but then at some point they switch over to tty7, and a login prompt appears on tty1.

I know from my experiences with Ubuntu that the login prompt is started by the upstart job "tty1" defined in /etc/init/tty1.conf. However, try as I might, I can't seem to figure out how to tell upstart (or anything else, for that matter) to keep messages on this tty1, rather than switching them over to tty7.

Since this server is accessible via ssh, most of the time when I am looking for a problem I can't find over ssh I go to this "message console" and look for the issue there. It is inconvenient to have to switch to tty7 after start up to see the messages. In addition, in situations such as a kernel panic, I am no longer able to switch which tty I am on. If I had not connected to tty7, then I may not see the kernel panic, and will instead be presented by a much-less useful frozen login screen.

How do I move the display on tty7 back to tty1, or else make tty7 the console which is displayed by default? (note, there is no X server installed on this server, and there never will be. I do not need to worry about conflicts with X) I really just want the on-screen bootup and system messages to continue to be displayed even after the system is "finished" booting.

---

