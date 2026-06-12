---
title: "Guacamole For Screen Sharing"
date: 2015-04-01
forum: Server Platforms
---

### Post by lingpanda on 2015-04-01
Hello,

I'm unable to verify if Gucamole can be used to share another workstation screen. Anyone have experience with this software? Looking for an alternative to Citrix Go To Assist. Thanks.

[http://guac-dev.org/](http://guac-dev.org/)

---

### Post by volkswagner on 2015-04-02
Perhaps you can offer more specific scenario you are considering.

Guacamole is a gateway allowing you to have a server behind a firewall and access all machines
on the same LAN via browser using VNC or RDP on the LAN machines.

You would need a Guacamole server behind each firewall you want access.

The "Workstations" or servers still need to have RDP or VNC installed and enabled.

In short, Guacamole is not a replacement for TeamViewer, GoToAssist, ShowMyPC type
Desktop support software (where you'd need to connect to various client workstations on a moments notice).

It may work well if you have a fixed number of networks that you support remotely.

To note: If you want to share screens, then you can't use the RDP protocol on Windows machines. You'd have 
to install VNC on Windows workstations so both local and remote users can view the same logged in user's screen.

---

### Post by TheFu on 2015-04-02
> **volkswagner said:**
> It may work well if you have a fixed number of networks that you support remotely.

To note: If you want to share screens, then you can't use the RDP protocol on Windows machines. You'd have 
to install VNC on Windows workstations so both local and remote users can view the same logged in user's screen.

Sharing screens is tough. There are linux presentation tools like mikogo that work well for that, but don't have remote control (I don't think they do).  If you just want remote access use ssh and/or x2go. VNC and RDP need a full VPN to be secure. x2go uses ssh on the same port that is already used by ssh.  Of course, all of these methods will require the router be modified to allow inbound connections --- unless you have a 3rd party server that can spoof packets to trick the client and the server to open their firewalls to each other (like at how napster did it).  x2go is based on NX which feels about 2-3x more network efficient over VNC or RDP. It is night and day better than other free alternatives. No scree sharing, however.

For working with other people, tmux and screen have a way to share terminal sessions. [https://www.howtoforge.com/sharing-terminal-sessions-with-tmux-and-screen](https://www.howtoforge.com/sharing-terminal-sessions-with-tmux-and-screen)

---

### Post by lingpanda on 2015-04-02
> **volkswagner said:**
> Perhaps you can offer more specific scenario you are considering.

Guacamole is a gateway allowing you to have a server behind a firewall and access all machines
on the same LAN via browser using VNC or RDP on the LAN machines.

You would need a Guacamole server behind each firewall you want access.

The "Workstations" or servers still need to have RDP or VNC installed and enabled.

In short, Guacamole is not a replacement for TeamViewer, GoToAssist, ShowMyPC type
Desktop support software (where you'd need to connect to various client workstations on a moments notice).

It may work well if you have a fixed number of networks that you support remotely.

To note: If you want to share screens, then you can't use the RDP protocol on Windows machines. You'd have 
to install VNC on Windows workstations so both local and remote users can view the same logged in user's screen.

I would like to deploy a server that will allow me to screen share workstations on the same local lan. All workstations will be Windows and Ubuntu. The purpose is to offer remote support. I would like to find a approach similar to GoTo Assist where end users simply enter a code to request help. I could then see the issue and take over their workstation to rectify.

---

### Post by lingpanda on 2015-04-02
> **TheFu said:**
> Sharing screens is tough. There are linux presentation tools like mikogo that work well for that, but don't have remote control (I don't think they do).  If you just want remote access use ssh and/or x2go. VNC and RDP need a full VPN to be secure. x2go uses ssh on the same port that is already used by ssh.  Of course, all of these methods will require the router be modified to allow inbound connections --- unless you have a 3rd party server that can spoof packets to trick the client and the server to open their firewalls to each other (like at how napster did it).  x2go is based on NX which feels about 2-3x more network efficient over VNC or RDP. It is night and day better than other free alternatives. No scree sharing, however.

For working with other people, tmux and screen have a way to share terminal sessions. [https://www.howtoforge.com/sharing-terminal-sessions-with-tmux-and-screen](https://www.howtoforge.com/sharing-terminal-sessions-with-tmux-and-screen)

Mikogo would work but requires a fee for commercial use. Would like to avoid a model that requires a fee if possible. Quickly scanning tmux, it looks to be a linux to linux solution.

---

### Post by PhilGil on 2015-04-02
TeamViewer has always worked well for me (on both Windows and Linux). There is a fee for commercial use, however. [Chrome Remote Desktop](https://support.google.com/chrome/answer/1649523?hl=en) might also be an option.

---

### Post by bmullan2 on 2015-04-02
I use Guacamole and x2go.   I'm not sure about Guacamole but I know x2go supports screen/session sharing ([http://wiki.x2go.org/doku.php/doc:usage:desktop-sharing?s](http://wiki.x2go.org/doku.php/doc:usage:desktop-sharing?s)[]=sharing)

---

### Post by lingpanda on 2015-04-09
> **PhilGil said:**
> TeamViewer has always worked well for me (on both Windows and Linux). There is a fee for commercial use, however. [Chrome Remote Desktop]("https://support.google.com/chrome/answer/1649523?hl=en") might also be an option.

After trying all the suggestions I decided to go with Chrome for remote sharing. While not ideal it does the job. I've been able to tweak things a bit by deploying via AD Group Policy. Thanks all.

---

### Post by TheFu on 2015-04-09
Thanks for posting back your final decision. 
This thread has lots of different options which fill different requirements. It will be good for lurkers.

---

