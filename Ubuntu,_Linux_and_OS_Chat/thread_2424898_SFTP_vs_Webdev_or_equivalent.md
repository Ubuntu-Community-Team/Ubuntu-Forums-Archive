---
title: "SFTP vs Webdev or equivalent"
date: 2019-08-16
forum: Ubuntu, Linux and OS Chat
---

### Post by orion20k on 2019-08-16
Hi all hope you are well, long story short i run a file server on my local network and when im out and about i use ssh/sftp to access my files securely.

some have questioned the logic of this suggesting it could be achieved by webdev or some other means, it is worth pointing out i access my media as well as my files remotely and i use a chroot jail.

im interested to see what you all think as for me been able to access my data knowing it is encrypted is a waight off my mind as i have to use public wi-fi on occasion

---

### Post by TheFu on 2019-08-16
webDAV has all sorts of security issues.  Best to avoid it, but if you can't, only use it on the LAN or with a full, secure, key-based VPN.  Setting up openVPN isn't THAT hard, but there are hundreds of options, each for specific needs. If your network skills are weak, it is easy to get confused.  It is also not-so-hard for remote locations to block VPN access. I've run into this in hotels around the world.

If you want to access media, you can setup a plex server, then use an SSH socks proxy to access the plex web GUI and have access to all of it fairly secure.  Just be certain your ssh access never uses passwords, only ssh-keys.  The ssh-socks proxy also behaves as a poor-man's VPN so all your http traffic goes to your home server first, then to the public websites you are browsing.  It does leak normal DNS, however.
If you setup ssh to listen on port 443/tcp, then most hotel proxies will let it pass.  Many corporations will too, but those with excellent security will recognize it as ssh, not https, and block it.  You can setup openvpn to listen on 443/tcp too and might have better luck.

"jail" is a BSD term that means something specific and isn't provided in Linux.  chroot is helpful for some security needs, but there are almost always ways to break out of a linux chroot setup.

If you need help setting up ssh-keys, let someone know. It is really easy on Unix systems.  

Please use the default fonts here. No need to funkify them.

---

### Post by DuckHook on 2019-08-16
@ orion20k

Please post with the default fonts, styles and sizes. Oddball formatting might fail to render properly on small screens and can be challenging to those with vision limitations.

---

### Post by orion20k on 2019-08-17
ill post using the defaults even if it looks huge on my screen &#55357;&#56834;, sounds like im better sticking with my current sftp setup

---

### Post by TheFu on 2019-08-17
> **orion20k said:**
> ill post using the defaults even if it looks huge on my screen &#65533;&#65533;, sounds like im better sticking with my current sftp setup

<ctrl>+- will reduce the text size in most windows, including every popular browser that I know.  That's the **cntl** key with the minus key, **-** as a chord.  To make it larger, use the <cntl>++ key  ---- which might be <shift><cntl>+= on your keyboard.  <shift>-= is the + on mind.
The rest of us have our screens and fonts setup perfectly for use on all websites including this one. I use the default settings, and it is sized perfect.

Assuming you aren't using passwords, and your ssh-keys are strong, like an ed25519 key, and you have **fail2ban** installed and configured to block brute force attacks for your setup, yes.  Never use passwords over internet connections.  Also, to make connecting with different userids and different keys and different ports easier, setting up a few lines in the ~/.ssh/config file will make life easier.  Don't type full hostnames, userids, ports, keyfiles any more, and I'm not suggesting creating aliases or tiny scripts to get around that.  Just use the ~/.ssh/config.

Ask if you'd like help on any of that.

Also, there are lots of ssh-based tools you can use.  **sshfs** is pretty great. So is **rsync**.   Some editors will let you edit remote files using rsync over ssh, which can be very efficient.  If you need a remote desktop, there's **x2go**, which goes over ssh and uses the nx protocol which is 2-3x faster than vnc or rdp while still using a secure ssh tunnel - the same ssh that sftp uses.

ssh is freakin' amazing.  [http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html](http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html)

---

