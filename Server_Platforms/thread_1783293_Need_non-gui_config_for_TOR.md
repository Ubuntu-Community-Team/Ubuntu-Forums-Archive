---
title: "Need non-gui config for TOR"
date: 2011-06-15
forum: Server Platforms
---

### Post by M4rotku on 2011-06-15
Hey guys,

I have a server set up in my basement and I want to contribute some bandwidth to the TOR network.  The problem is that every guide that I seem to find for setting up TOR to contribute, includes the step of "Install Vidalia, use that for most things."  I can't really do this on a headless server.  I've tried editing the config files on my own, but I don't understand everything well enough to be able to do it.  I keep running into errors with the ports and I don't really know what I'm doing in that area.

Does anyone know of a TOR configuration tool that doesn't use a GUI?  Or, does anyone know of a nice tool for viewing/configuring which ports are being used?

---

### Post by M4rotku on 2011-06-15
I don't know if this will help, but here is the output that I receive when I try to run TOR:

```
$ tor
Jun 15 15:53:52.030 [notice] Tor v0.2.1.30. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Jun 15 15:53:52.073 [notice] Your ContactInfo config option is not set. Please consider setting it, so we can contact you if your server is misconfigured or something else goes wrong.
Jun 15 15:53:52.076 [notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Jun 15 15:53:52.076 [notice] Opening OR listener on 0.0.0.0:9002
Jun 15 15:53:52.076 [warn] Could not bind to 0.0.0.0:9002: Address already in use. Is Tor already running?
Jun 15 15:53:52.076 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Jun 15 15:53:52.076 [err] Reading config failed--see warnings above.

```

---

### Post by M4rotku on 2011-06-16
bump

---

### Post by Lars Noodén on 2011-06-17
The EFF is currently running a [campaign for privacy using Tor](https://www.eff.org/torchallenge/).  They might have some tips or be able to point to better guides.

---

### Post by M4rotku on 2011-06-18
I checked out the link you gave me and while it doesn't seem to have any information that will help my specific problem, it was very interesting to read, so thank you for posting it.  I may get in contact with those people once I successfully set this up.

---

### Post by M4rotku on 2011-06-20
bump

---

### Post by M4rotku on 2011-06-26
bump

---

### Post by M4rotku on 2011-06-30
bump...about to give up on the non gui and install a small desktop.

---

### Post by Bachstelze on 2011-06-30
[https://www.torproject.org/docs/tor-doc-relay.html.en](https://www.torproject.org/docs/tor-doc-relay.html.en)

> # Manual Configuration:

    * Edit the bottom part of your torrc file. If you want to be a public relay (recommended), make sure to define ORPort and look at ExitPolicy; otherwise if you want to be a bridge for users in countries that censor their Internet, just use these lines.

---

### Post by Thegmandrive on 2011-06-30
> **M4rotku said:**
> I don't know if this will help, but here is the output that I receive when I try to run TOR:

```
$ tor
Jun 15 15:53:52.030 [notice] Tor v0.2.1.30. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Jun 15 15:53:52.073 [notice] Your ContactInfo config option is not set. Please consider setting it, so we can contact you if your server is misconfigured or something else goes wrong.
Jun 15 15:53:52.076 [notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Jun 15 15:53:52.076 [notice] Opening OR listener on 0.0.0.0:9002
Jun 15 15:53:52.076 [warn] Could not bind to 0.0.0.0:9002: Address already in use. Is Tor already running?
Jun 15 15:53:52.076 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Jun 15 15:53:52.076 [err] Reading config failed--see warnings above.

```


Login Via SSH using "ssh -X [email]user@sever.com[/email]"

then try starting up tor. I had a similar problem setting up PS3MediaServer, I had to use the gui to configure it initially.

---

### Post by M4rotku on 2011-06-30
Ok, I managed to resolve the problem with the help of the guide Bachstelze posted.  Thanks guys.

---

### Post by it'smeagainmartha on 2011-07-03
> **Thegmandrive said:**
> Login Via SSH using "ssh -X [EMAIL="user@sever.com"]user@sever.com[/EMAIL]"

then try starting up tor. I had a similar problem setting up PS3MediaServer, I had to use the gui to configure it initially.
The very short, easy is to download tor.
I'm not a Ubunta user so you'll have to figure it out.
I used a Redhat command: yum tor install.
It ain't fancy version of Tor.
I then downloaded Polipo: a very secure proxy server.
I then downloaded the Polipo conf file poated on the Tor site which is configured for max security.
Edit Tor conf file to port 8118 the default port for polipo,.
Start polipo, then start Tor.

Done!:D

---

