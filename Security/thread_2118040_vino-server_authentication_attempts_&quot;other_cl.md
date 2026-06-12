---
title: "vino-server authentication attempts &quot;other clients&quot; listed"
date: 2013-02-20
forum: Security
---

### Post by thatcooldude on 2013-02-20
TL;DR - Can I see who's connected to vino-server without connecting myself to check the tray icon?  And are all attempts listed as "other clients"?

I have a VNC server (the built in vino-server) in Ubuntu 12.04.2 LTS with 3.2.0-37-generic that I start and stop while connected over SSH.

I don't **usually** leave it running, but I'll occasionally '& disown' it so it runs and is easily reconnectable without SSH'ing back in to restart vino-server over and over again throughout the day.

I'm exporting the display and launching vino server to output to a log like so:

```
~$ export DISPLAY=:0.0 ; /usr/lib/vino/vino-server > /var/log/vino.log 2>&1 & disown
```

While watching the resulting log, I'm seeing the following after just a few minutes:

```
** (vino-server:4452): WARNING **: Deferring authentication of '178.76.223.64' for 5 seconds


** (vino-server:4452): WARNING **: VNC authentication failure from '178.76.223.64'

20/02/2013 12:21:52 AM rfbAuthPasswordChecked: password check failed
20/02/2013 12:22:03 AM [IPv4] Got connection from client 178.76.223.64
20/02/2013 12:22:03 AM   other clients:
20/02/2013 12:22:03 AM      178.76.223.64
20/02/2013 12:22:03 AM      178.76.223.64
20/02/2013 12:22:03 AM      178.76.223.64
20/02/2013 12:22:03 AM      178.76.223.64
20/02/2013 12:22:03 AM      178.76.223.64
20/02/2013 12:22:03 AM      178.76.223.64
20/02/2013 12:22:03 AM      178.76.223.64
20/02/2013 12:22:03 AM      178.76.223.64
20/02/2013 12:22:03 AM      178.76.223.64
20/02/2013 12:22:03 AM      178.76.223.64
20/02/2013 12:22:03 AM      178.76.223.64
20/02/2013 12:22:03 AM      178.76.223.64
20/02/2013 12:22:03 AM      178.76.223.64
20/02/2013 12:22:03 AM      178.76.223.64
20/02/2013 12:22:03 AM      pjc-23-232.tm.net.my
20/02/2013 12:22:03 AM      pjc-23-232.tm.net.my
20/02/2013 12:22:03 AM      pjc-23-232.tm.net.my
20/02/2013 12:22:03 AM      my.router
20/02/2013 12:22:03 AM Client Protocol Version 3.5
20/02/2013 12:22:03 AM Ignoring minor version mismatch

```

I know that my.router is "me", and I'm aware that since I've set up this machine to be accessible outside of my local network, that means I'm open to brute force attacks.  While I'm fairly confident that none of these attempts have been successful (the password is randomly generated, 20+ character length made of numbers / symbols), is there anything in the log that shows "currently connected users"?

I initially freaked out after seeing so many "other clients", thinking that all of those users were currently connected and controlling my desktop.  After checking my auth.log in a panic and unplugging the machine from the network while killing vino-server, I realized that the "other client" list most likely serves as a history of attempted client connections, not currently active users.

[B]Besides logging in through vino-server myself and clicking on the remote desktop icon to verify "One person is connected"...is there any way to tell how many users are connected and active from the vino log or with some other terminal command?
[/B]
Thanks in advance!

---

### Post by CharlesA on 2013-02-20
If you really need to access VNC from the internet, it is a good idea to tunnel it over SSH or use a VPN because it transmits data unencrypted.

Personally, I would limit it to localhost and SSH in to connect via VNC.

---

### Post by cariboo on 2013-02-21
Doing a simple whois on the ip address:

```
whois 178.76.223.64
```

shows that it is originating from Russia, and pjc-23-232.tm.net.my originates from Malaysia.

I think it may be best to do as CharlesA suggeests.

---

### Post by thatcooldude on 2013-02-21
Thanks for the responses!

I'd already run a whois lookup on the various IPs trying to connect, but it's fairly probably they're also "owned" boxes themselves.

I think I've figured it out though.  It lists any attempts to log in under "other clients" in the log, but if someone is successfully logeed in, it'll output what image quality and compression level is being used for that client:

```
20/02/2013 08:50:38 AM Using image quality level 9 for client xxIP_ADDR_HERExx
20/02/2013 08:50:38 AM Using compression level 9 for client xxIP_ADDR_HERExx

```

For now, I'm disabling my VNC server when I don't need it, tunneling through SSH when I do.

Thanks for the advice!

---

