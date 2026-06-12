---
title: "Smbclient connencts to Windows 7, but can't list any files"
date: 2010-09-23
forum: Server Platforms
---

### Post by conoral11 on 2010-09-23
Hi there.

I've recenelty setup a backup server using Ubuntu server 10.4 x64.

I'm currently attempting to get the server to connect to windows vista and windows 7 shares on the network.

When running the command

```

smbclient \\\\hazard-pc\\test
```

a prompt for a password appears, I enter nothing and am then presented with. I am not using passwords on the windows shares.

```

smb: \>
```

If I attempt to list the directory using ls then I get the following error:

```

smb: \> ls
NT_STATUS_ACCESS_DENIED listing \*

                57138 blocks of size 1048576. 32044 blocks available
smb: \>
```

I've looked on google and on here and have not been able to find anything that works. I also don't have any xp machines to test with either.

I discovered this issue whilst trying to configure the backuppc service using smb.

Hope you can help

Conoral11

---

### Post by conoral11 on 2010-09-23
I found the answer.

After testing if both windows machines could access each other, they displayed the same issues as smbclient was having.

They could both see each other and their shares, but not access them "Access Denied".

To solve this in windows 7


[LIST=1]
[*]I unshared the folder that was being shared.
[*]I reshared it, making sure to add in permissions the Guest account
[*]All fixed.
[/LIST]
I then did the same thing with vista and the problem was sorted.

I hope this helps anyone else who is having the same problem

---

