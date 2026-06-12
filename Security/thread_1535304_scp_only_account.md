---
title: "scp only account?"
date: 2010-07-20
forum: Security
---

### Post by shaggy999 on 2010-07-20
Here is my scenario: I have a server running rtorrent & ssh.

rtorrent monitors a specific directory which is chmod 777 for new incoming torrents. My normal method for transferring torrent files is using my user, which has sudo privileges, to scp files across the network to the folder. I use an ssh key with a password for this account because it has sudo privileges.

But I would like to be able to do simple scripting on my local computer to monitor the Downloads directory and scp files over manually without having to enter my password. So I was thinking that if I created a new, non-sudo user on the server w/ a password-less ssh key I could easily script the file copy process. But I want to limit this user to only being able to scp files. I don't want this user able to be locally logged in or ssh in. I just want a dummy account to scp files. Is this possible? I've heard of 'scponly', but from what I gather this is used by people that at least want to allow local logon, just not ssh logon. I don't even want local logon.

Does anybody have any recommendations?

---

### Post by Bachstelze on 2010-07-20
To disable local logins, do

```
sudo passwd -l username
```

Then use scponly or rssh.

---

