---
title: "Hacker?"
date: 2006-10-28
forum: Server Platforms
---

### Post by gerowen on 2006-10-28
I use the firestarter gui frontend for managing my firewall, and earlier today I noticed something rather odd.  For about 2 minutes I received "many" connection attempts from the IP 68.100.253.190 on a wide range of ports.  I even spotted them browsing [my fileserver.](http://www.marcusadams.4t.com)  When I did a whois I got:
```
Cox Communications Inc. NVRDC-68-100-0-0 (NET-68-100-0-0-1) 
                                  68.100.0.0 - 68.100.255.255
Cox Communications Inc. COX-ATLANTA-2 (NET-68-96-0-0-1) 
                                  68.96.0.0 - 68.111.255.255

```

I did a quick google search and Cox appears to be an ISP based in Atlanta.  [Here is a snippet of the event log.](http://147.133.214.88:8001/Hacker%20Thwarted.txt)  Is this something I should worry about?  I mean my firewall is pretty closed off, the only open ports I have are for my webserver, VNC which is password protected, and Samba which is restricting access to only the IP of my laptop, so I think I'm pretty safe, but I wasn't even doing anything when these started popping up, so it makes me wonder how they managed to get my IP, unless it was someone on this forum who saw the topic asking for verification that my server was viewable from the outside world...

---

### Post by kvonb on 2006-10-28
Just another ratbag doing a port sniff, it happens all the time.

I looked at your web-server, it seems to be working fine, it asked me for a password when trying to access the 'CD Images' folder.

Make sure that Firestarter has the option to not report errors, but drop them silently, (sorry can't remember the exact menu location, I stopped using it because the stress of seeing all the hack attempts was too much :D ).

I would even do a 'nessus' scan of people scanning me, just to get some revenge and maybe scare them, until my server mysteriously shut down on me just after such a retaliation.

That left me scared so I have just ignored them ever since!

As long as your SMB server and SSH server (if you are using it) are set to listen only on the internal network you should be OK.

You could always get someone you trust to do a nessus scan of your server to see what ports are open, it would put your mind at ease.

Regards,  Kev :)

---

### Post by kvonb on 2006-10-28
Just another quick observation:

You offer a document titled "Setting up Remote Desktop.doc", this is an advertisement that you are running remote desktop, it's like a red flag to ratbags to have a go at getting in!

Just my thoughts :)

---

### Post by gerowen on 2006-10-28
Yeah I put a password on the CD Images folder because I've got things like Windows XP Pro SP2 and stuff in there that I might need when I'm away, but I don't want every Tom Dick and Harry who sees a link to my folder downloading illegal copies of Windows, :p

---

### Post by gerowen on 2006-10-28
Yeah I'm not running Remote Desktop, but one of my friends didn't know how so I typed that up and told him to go get it whenever he wanted.  I guess it would be a good idea to take it down now huh?

---

### Post by kvonb on 2006-10-28
You're always going to get ratbags knocking at your door, maybe rename it to something unrelated or put it in the password protected zone.

You can get so wound up with paranoia that it makes you a little strange in the end, (I know the Martians are coming for me ha ha :D ).

Just make sure that you don't have any REALLY important personal info anywhere near your server and you should be OK.

And if you are running remote desktop, Firestarter can block it from the outside, just un-block it if you need remote access for the duration.

Regards,  Kev :)

---

