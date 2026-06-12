---
title: "Secure FTP and Telnet???"
date: 2008-08-29
forum: Server Platforms
---

### Post by Vegan on 2008-08-29
As it stands I am depending on my firewall to secure my server from the wild wild web. Some propaganda suggested installing this and that would allow secure connections.

My Windows clients, FTP with several SSL flavors, WinSCP. So what demons are really needed. Obviously telnet and FTP are important, but there must be a better way.

---

### Post by windependence on 2008-08-29
SSH is all you need. Don't even think about telnet unless you really don't care about being hacked. Use SSH, SCP, AND SFTP. WinSCP is a client for all of them.

-Tim

---

### Post by Vegan on 2008-08-30
There are ways to secure Telnet. Unix is not exactly a new OS. The have some experience.

Still, I installed ssh, and no joy on the intranet.

---

### Post by windependence on 2008-08-30
OK, I'm not saying it's impossible, but I would love to see you secure telnet without tunneling it.

I don't understand your installation problems, Openssh is one of those things that "just works" Explain what you mean by no joy. What error are you getting? Run ssh with the -vvv option and post it here. What is in your authlog? Info, and we can fix this.

-Tim

---

### Post by Vegan on 2008-08-30
usage: ssh [-1246AaCfgKkMNnqsTtVvXxY] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-e escape_char] [-F configfile]
           [-i identity_file] [-L [bind_address:]port:host:hostport]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-R [bind_address:]port:host:hostport] [-S ctl_path]
           [-w local_tun[:remote_tun]] [user@]hostname [command]

No sure if its functioning, or needs config.

---

### Post by jerome1232 on 2008-08-30
what did you type?

basic usage would be (with verbosity to help with troubleshooting)

```
ssh -vv user@host
```

---

### Post by Vegan on 2008-08-31
With WinSCP is says connection refused.

---

### Post by windependence on 2008-08-31
Do you have ssh installed and running?

What is the output of 

```
sudo ps auxww | grep sshd
```

Are you trying to ssh from a computer on your LAN and what is the exact command you are using?

Something is not right here.

-Tim

---

### Post by Vegan on 2008-08-31
I am on the LAN. I am using the firewall to secure the LAN so I don't care, I have implemented a lockout for excessive failed login to thwart hackers.

---

