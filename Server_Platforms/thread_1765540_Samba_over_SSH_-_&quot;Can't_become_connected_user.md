---
title: "Samba over SSH - &quot;Can't become connected user!&quot;"
date: 2011-05-23
forum: Server Platforms
---

### Post by bacterozoid on 2011-05-23
I've got a Samba share set up on my Ubuntu server. I'm trying to access it remotely through an SSH tunnel on Windows using Putty.

I can get to the server and see the shares by entering \\IP into the Run box on Windows. As soon as I try to open my share, I get this error:

**[COLOR="Red"]\\IP\share is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions. Access is denied.[/COLOR]**

[COLOR="RoyalBlue"][NOTE: This was working last week. After testing successfully, I reinstalled Ubuntu on my server to clear out all the crap I was testing.][/COLOR]

In /var/log/samba/log.hostname, this translates to: [COLOR="red"]**"Can't become connected user"**[/COLOR]

My Samba config:

```
writable = yes
create mask = 0775
directory mask = 0775
# I tried commenting out the following two lines. When I do, samba connects as "nobody". I can read the share but it acts a bit funny. I also want only allow one user.
valid users = my_user
public = yes
```

Thoughts?

Edit: I should note that I can connect to the samba share fine locally.

---

### Post by papibe on 2011-05-23
I believe your are trying to connect remotely to your server using Putty. If that the case, you need to:
[LIST]
[*]Use the server name or its ip address (no \\ prefix).
[*]An SSH service up and running on your server.
[*]Once you're connected, you'll be on CLI using bash. To get to your shares, 'cd' to them.
[/LIST]

I hope it helps.

---

### Post by bacterozoid on 2011-05-26
I can connect to my server fine using Putty. I have a tunnel (and loopback adapter) set up to direct all samba traffic over SSH. I'm pretty sure the tunnel works because I can see a list of all the shares...I just can't access them.

I just upgraded samba and let it overwrite my smb.conf file, but I'm still having the same problem.

---

