---
title: "rkhunter reports timidity is listening on the network, I'm curious why"
date: 2015-04-16
forum: Security
---

### Post by a-you on 2015-04-16
A couple of days ago rkhunter said: "Warning: Process '/usr/bin/timidity' (PID  2778) is listening on the network." I understand that various applications listen and that that's normal. What struck me as odd was that rkhunter would warn about it, under "Checking for packet capturing applications." Am I maybe misunderstanding this? It seems to me that "listening" is a perfectly normal thing (and rkhunter doesn't treat it as problematic) but that packet sniffing is something else, and that this is what it's warning about(??)

All I  was doing at the time was reading/writing email plus using firefox. I  thought that maybe firefox invoked timidity for some reason even though  I'm quite sure that there was no MIDI anywhere on any web site I  happened to be browsing, but when I looked in the firefox preferences  under the "Applications" tab timidity was not mentioned at all. Also btw  I had just started the computer, and another strange thing, possibly  unrelated, was that the system literally crashed as I was looking into  this; that is, I was logged out and presented with the login again. That  sort of freaked me out because that pretty much never happens. And btw  upon restarting rkhunter no longer reported timidity as listening.

So I'm wondering if anybody has any ideas?? Thanks in advance for any insight!

Ubuntu Studio 14.4 Trusty 64 bit

[edit here: Task Manager reports that one running process at the  moment is "timidity -Os -iAD" but I don't get a lot from that(?); I'm  not doing anything related to MIDI at all at the moment.]

Dear forum admin: I posted this question in the wrong forum (under ubuntu studio). And now I don't know of any way to move it. Sorry!! Please feel free to either delete the thread I started in the ubuntu studio forum with exactly the same title. or do any other thing you see fit to do. I think it really should have been here though since what I'm trying to understand is whether there's any reason to be concerned.

---

