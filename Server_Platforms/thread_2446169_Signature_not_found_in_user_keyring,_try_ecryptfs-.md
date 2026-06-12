---
title: "Signature not found in user keyring, try ecryptfs-mount-private (Server 18.0.4.4)"
date: 2020-06-25
forum: Server Platforms
---

### Post by vellofrell on 2020-06-25
After a shutdown to apply updates and clone the boot drive, I keep getting this in the login shell:

Signature not found in user keyring
Perhaps try the interactive 'ecryptfs-mount-private'

So I run that 'ecryptfs-mount-private' and get through with my user password. It then says
"Inserted auth tok with sig (.......... and such) into the user session keyring
[B]fopen: No such file or directory

[/B]What is this fopen business, and how do I fix it? And how can I make this problem go away and remain fixed through system restarts?

As things are now there is limited connectivity to the server and the openvpn connections from my client devices will not work.

---

### Post by LHammonds on 2020-06-25
When you installed the server, did you opt to encrypt the home system?

---

### Post by vellofrell on 2020-06-25
> **LHammonds said:**
> When you installed the server, did you opt to encrypt the home system?

I believe I made it do no encryption in order for me to restart the machine remotely if necessary.

---

### Post by LHammonds on 2020-06-25
What encrypted file system is it trying to mount?  I know the /home is a typical question the installer asks to encrypt but that is usually the only thing you would accidentally encrypt during install.

LHammonds

---

### Post by vellofrell on 2020-06-25
> **LHammonds said:**
> What encrypted file system is it trying to mount?  I know the /home is a typical question the installer asks to encrypt but that is usually the only thing you would accidentally encrypt during install.

LHammonds

I'm not sure. Is there a command I can use to check? I doubt it would be anything other than the home directory, but even then I don't know how since I could have sworn I intentionally left unencrypted at the time of my last fresh install.

If this part even matters, the contents of /home/User/.ecryptfs include auto-mount, auto-umount, Private.mnt, Private.sig, and wrapped-passphrase.

---

### Post by vellofrell on 2020-06-26
So, somehow this thing worked itself out. I don't know what I did other than force an additional security update that was held back ```
sudo apt-get upgrade && sudo apt-get upgrade
```

and then running 
```
**update-initramfs [B]-u**[/B]
```

Apparently this whole god-awful experience maybe stems from fully shutting down without rebooting and shutting down a second time before cloning the boot drive. I don't know for sure really. Now my openvpn connectivity has a DNS problem and I don't really know why. The VPN clients connect to the server but there is no Internet access or external pinging going on. So some kind of DNS problem now.

---

### Post by vellofrell on 2020-06-26
I spoke to soon - "Signature not found in user keyring" is still there upon reboot from the connected monitor.

---

### Post by LHammonds on 2020-06-26
I do not encrypt any of my file systems so I am not that great at troubleshooting such a scenario but here is what my Google-Fu found:

[Check if partition is encrypted]("https://askubuntu.com/questions/53242/check-if-partition-is-encrypted")
[Ubuntu 14.04 x64 encrypted home - signature not found in user keyring]("https://askubuntu.com/questions/602360/ubuntu-14-04-x64-encrypted-home-signature-not-found-in-user-keyring")

LHammonds

---

### Post by vellofrell on 2020-06-26
> **LHammonds said:**
> I do not encrypt any of my file systems so I am not that great at troubleshooting such a scenario but here is what my Google-Fu found:

[Check if partition is encrypted]("https://askubuntu.com/questions/53242/check-if-partition-is-encrypted")
[Ubuntu 14.04 x64 encrypted home - signature not found in user keyring]("https://askubuntu.com/questions/602360/ubuntu-14-04-x64-encrypted-home-signature-not-found-in-user-keyring")

LHammonds


Thanks for the tip, I have applied this fix from that second URL link: [https://askubuntu.com/a/602559](https://askubuntu.com/a/602559)

I expect I won't know if this has fully corrected the problem until I get back to physical access to the server this evening. I'm only shelling in right now. I'll update further then. I'm still having connectivity trouble through the VPN, but perhaps that's another matter entirely.

---

### Post by vellofrell on 2020-06-26
To update from my last post: still no dice. When logging into the server with physical on-site access at the terminal, I still see "Signature not found in user keyring. Perhaps try the interactive 'ecryptfs-mount-private'

...of which I have tried numerous times, with no luck whatsoever - other than chasing my own tail in an endless recursive loop of futility. 

For some reason though, this message is not shown in the shell from a client device shelled into the server. Any more suggestions?

---

### Post by vellofrell on 2020-06-27
I have been trying something else but am still at an impasse. 

entering 
```
[COLOR=#000000][FONT=Menlo]sudo mount -t ecryptfs ~/secret ~/secret[/FONT][/COLOR]

```

runs me through a few steps where I come to this...

```
[COLOR=#000000][FONT=Menlo]WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]it looks like you have never mounted with this key [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]before. This could mean that you have typed your [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]passphrase wrong.[/FONT][/COLOR]

```

```
[COLOR=#000000][FONT=Menlo]Successfully appended new sig to user sig cache file[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]**Error mounting eCryptfs: [-2] No such file or directory**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Check your system logs; visit <http://ecryptfs.org/support.html>[/FONT][/COLOR]

```


Again, nothing.

---

