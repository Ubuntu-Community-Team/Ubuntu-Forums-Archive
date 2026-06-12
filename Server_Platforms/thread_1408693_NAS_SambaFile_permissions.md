---
title: "NAS Samba/File permissions"
date: 2010-02-16
forum: Server Platforms
---

### Post by frente69 on 2010-02-16
Hi,

I am building a headless ubuntu nas.
I have been making a script to do the following:
 - create soft raid array
 - create default folders
 - install and configured supporting services like minidlna, torrent, mysql, apache etc etc etc etc
 - install/create web guis for supporting services
 - create users and groups
 - create shares and set permissions

The last point is where i am having issues. As this is a nas device the only real permissions I want to fiddle with (after initial setup) are the samba shares.

I am having problems getting the correct combination. 
I have a folder at /data(a link to the raid array) where all the shares are going to be kept.
So i thought i could just create the subfolders and then "> chmod -R 666 /data"(current owner is root) and then add the shares to /etc/samba/smb.conf like so:
> 
[documents]
comment =
path = /data/documents
browsable = yes
public = yes
invalid users = guest
read list =
write list = @"administrators",@"documentusers"
valid users = @"administrators",@"documentusers"
inherit permissions = yes

[public]
comment = Full Read Write for Everyone
path = /data/public
browsable = yes
writable = yes
public = yes

[downloads]
comment = Downloaded files
path = /data/downloads
browsable = yes
public = yes
writable = yes

but it doesn't seem to work. It won't let me access the shares from Win7.
Can anyone help me please?

PS 
- I know setting 666 is considered a security risk but this is what companies like QNAP seem to do to simpilyfy permissions management
 - I have a Qnap 209 which is where i am taking my design insperation from.

---

### Post by Morbius1 on 2010-02-16
I'm fairly certain you have to have the executable bit set on directories or else you won't be able to open them. So instead of 666 you need 777:

```
chmod -R 777 /data 			 		
```

---

### Post by frente69 on 2010-02-18
Fair enough. I will give it a go.
I have also moved mysql databases to the /data folder. Will this break anything?
Also do i need to change the owner and group  from root?

---

### Post by doas777 on 2010-02-18
what does the global section of your smb.conf look like? most of the windows authentication confiruration is there.

one thing you probably need to add, is ```
client NTMLv2 auth = yes
```

---

### Post by frente69 on 2010-02-18
Out of interest, What does that change?

---

### Post by doas777 on 2010-02-19
ok.
smb uses an authentication mechanism called NT Lan Manager (an upgrade from the older lanman mechanism in windows 3.11 and w95/98). Lanman passes network credentials in plaintext so anyone with a network analyzer can capture the password. obiviously that is not good.

to alleviate these issues, NTML v1 was released for NT4 and it performs weak encryption on the authentication packets, but it is not strong enough. the hashes also use reversible encryption, so you can derive the password from the hash. it's just plain easy to hack.

NT Lan Manager version 2 uses a much stronger encryption, and has numerous security related upgrades, to make credentials exchange safer. 

so, in windows, you have a few options (all these settings are in secpol.msc under "Security Options"\"Network Access") including allowing all three protocols, using NTLM of whatever version the server requests, or strictly using ntlmv2.

Windows7 uses NTMLv2 by default, so that line of config is telling samba to allow authentication using that protocol.

---

### Post by frente69 on 2010-03-11
Finally got around to trying out the suggestions managed to kill my mysql db's in the process(I stored them in /data and apparently they like to have specific permissions and ownership).

Anywho.. 

So when a user copies data to a share(which works now that i have set 777) other users are unable to access/modify the data because the new data doesn't have the 777 permissions anymore. How can i make all default data inherit 777 permission?

---

### Post by Morbius1 on 2010-03-12
I assume you're talking about your [public] and [downloads] shares.

You could do the same thing you did on the [documents] share. Add:
```
inherit permissions = yes
```to each share.

They will still be owned by the remote user's name or "nobody" in the case of a pure guest but their permissions will become 777 ( for directory transfers ) or 766 ( for file transfers )

EDIT: You could also add a **force user = nobody** to each share. That will force everyone to appear to be the user "nobody" regardless of who they are. The nobody account is set up by default in the desktop version - don't know about the server version.

---

