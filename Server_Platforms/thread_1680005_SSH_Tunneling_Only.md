---
title: "SSH Tunneling Only"
date: 2011-02-01
forum: Server Platforms
---

### Post by PierreRobiquet on 2011-02-01
Hello,

I currently have SSH set up on my network and facing outwards so that I can use my private key to authenticate and remotely administrate my server along with the ability to use SSH tunnels when needed to encrypt my traffic. However, I want to be able to give a friend access and use my server as a SSH tunnel, I do not want him to be able to execute any commands or write any files, just to create an SSH tunnel. Although it would not be too much of a large issue if he could write to his own home directory, I just want to ensure that he isn't able to browse around the whole file system and keep it as simple as possible.

---

### Post by papibe on 2011-02-01
If you create a new user, by default she will be a regular user, no able to exec sudo. Unfortunately, as the default permission are pretty open in Ubuntu, she will be able to see most user's files. Of course you can easily change that by doing a chmod 700 of all users root.

I think what you want to do can be accomplished by creating ssh keys, and then settings options on the key file to restrict login. Check [this ]("http://www.linuxquestions.org/questions/linux-server-73/ssh-tunneling-with-no-shell-prompt-720003/")out.

I hope it helps.

---

### Post by rudelgurke on 2011-02-02
Setup a new user, give it nologin as shell and set in your SSH configuration something like:

User example
 ForceCommand /bin/false

Then this user won't be able to execute commands. Additionally you can (and should) restrict sftp / scp access by

User example
 ForceCommand /bin/false
 ChrootDirectory /home/user/nonexistent

And set the right permissions to nonexistent to prevent the user from changing anything there.

A note - you should maybe setup server side forwardings to prevent the user from setting up his own forwards.

---

### Post by PierreRobiquet on 2011-02-03
Just for informations sake, what could a malicious user do with the ability to set up SSH tunnels and nothing else? Obviously they would have access to my network, but would they for example be able to route connections from the server back to them for some strange phishing attempt or possibly to send malicious updates (Of course if they had the PGP key)?

---

### Post by WinstonChurchill on 2011-02-03
When you say tunnel, I'm assuming you're talking about SOCKS proxying (the '-D' option). If you actually mean IP-Layer tunnels using the tunX interfaces, only root can do that.

The problem with SOCKS proxying is that your clients magically have access to everything your server has access to (the internals of your LAN, presumably), which is probably not what you want. I've done what you're talking about by installing Squid with the following SSH configuration:```

## sshusers: Users allowed to forward to Squid and SFTP /public; no shell
Match Group sshusers
X11forwarding no
AllowTcpForwarding yes
PermitOpen 127.0.0.1:3128
GatewayPorts no
ChrootDirectory /public/
ForceCommand internal-sftp

```The client just port-forwards 3128 with normal TCP and points their applications there, and then you can configure Squid to allow exactly what you do/don't want the client to be able to access.

Also, I may be wrong about this, but I believe that if you have "ForceCommand /bin/false" you can't do anything at all (including SFTP), and you don't need the "ChrootDirectory" line. Try it and see.

Something else to consider: SSH allows you to specify a ton of options per-public-key (if you're using public keys, which you should be) like so:
```

command="ip route add 172.16.1.0/24 via 192.168.1.2",no-port-forwarding,no-pty,no-user-rc,no-agent-forwarding,no-X11-forwarding,tunnel="1",from="18.0.0.0/8" ssh-rsa [[[Pubkey here]]] An_Informative_Comment

```This would be a key for root - it only allows the user authenticating with this key to create a tunnel interface, automatically executes a command to add a route, dissallows a bunch of stuff, and only allows connections from MIT. THe great thing about this is that you can have multiple keys for the same user, but different rules for each. For example, on your laptop, you might want to log in as yourself and get a shell; but if you have another machine that just makes backups, you can make it it's own key and only allow it to do that.

I'd suggest thoroughly reading 'man ssh' and 'man sshd_config' - OpenSSH is an extremely powerful daemon, and it's worth understanding in depth everything it can do.

---

### Post by papibe on 2011-02-03
> **ConcreteDonkey said:**
> Just for informations sake, what could a malicious user do with the ability to set up SSH tunnels and nothing else? ...

One thing to keep in mind is that anything the user does while tunneling, would be as you were doing it (and then responsible for it).

Most people do tunneling to read their mail on a public cafe, or maybe get into facebook at work. Nothing wrong with that right? But image that the user either download something questionable, or go to sites that can get you in trouble.

I think you REALLY have to trust the person you are giving her access.

Just a thought.
Regards.

---

### Post by Thirtysixway on 2011-02-03
> **papibe said:**
> One thing to keep in mind is that anything the user does while tunneling, would be as you were doing it (and then responsible for it).

Most people do tunneling to read their mail on a public cafe, or maybe get into facebook at work. Nothing wrong with that right? But image that the user either download something questionable, or go to sites that can get you in trouble.

I think you REALLY have to trust the person you are giving her access.

Just a thought.
Regards.

Agreed. and if you don't trust that person to not look through files or run commands, why would you trust them to tunnel all of their web traffic through your system?

---

### Post by brettg on 2011-02-03
If you follow these instructions your friend will be able to do exactly what you need.

[http://tuxnetworks.blogspot.com/search?q=ppp](http://tuxnetworks.blogspot.com/search?q=ppp)

---

### Post by PierreRobiquet on 2011-02-04
> **Thirtysixway said:**
> Agreed. and if you don't trust that person to not look through files or run commands, why would you trust them to tunnel all of their web traffic through your system?

I'm just trying to follow the theory of least privilege, it will not be the worst thing in the world if they are able to write to there home directory or execute commands but if they do not need access to that then why not ensure that they are not allowed to access it? Plus hopefully it will minimise the damage if an attacker is able to gain access to my friends private key.

---

### Post by kroon78 on 2011-02-04
You could always tell your friend not to do anything questionable and then store their traffic logs and review them to see if he/she is following what you asked.  Just my 2 cents.

---

