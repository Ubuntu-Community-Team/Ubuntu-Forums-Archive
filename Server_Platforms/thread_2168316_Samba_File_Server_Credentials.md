---
title: "Samba File Server Credentials"
date: 2013-08-17
forum: Server Platforms
---

### Post by ZellTM84 on 2013-08-17
OK,

For the first time, I'm trying to set up a simple - yet secure - Linux file server using Samba (Ubuntu Server 12.04).  I'll be connecting to it via Linux (Xubuntu 12.04) & Windows 7 clients.  So far, I went through this method with no success (the share did not appear on either client's side):

   [https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html)

Next, I found this walkthrough, and it worked great for both Xubuntu & Windows:

   [http://rbgeek.wordpress.com/2012/04/25/how-to-install-samba-server-on-ubuntu-12-04/](http://rbgeek.wordpress.com/2012/04/25/how-to-install-samba-server-on-ubuntu-12-04/)

However, this setup allowed access by anyone on the network - which I don't want.  So, I followed this:

   [https://help.ubuntu.com/12.04/serverguide/samba-fileprint-security.html](https://help.ubuntu.com/12.04/serverguide/samba-fileprint-security.html)

I simply edited the smb.conf file from "guest ok = yes" to "guest ok = no".

At this point, I am happy with the Windows side of things (for once) - I navigated to the share from explorer: e.g. "\\192.168.1.100" and the credentials window pops up.  All good there.

On my Xubuntu machine i navigate to the correct IP address - all of them are static btw - and nothing happens: no credential pop up and I can't even see the share.  So, finally, how do I get the credentials pop up on my Linux machine?  Why does the share disappear when I prevent guest access?

-Thx

---

### Post by Morbius1 on 2013-08-17
Since you followed so many HowTo's you are almost obligated to show us what you've done. Please post the output of the following command:
```
testparm -s
```
And just in case ( don't be alarmed if there is no output ):
```
net usershare info --long
```

---

### Post by ZellTM84 on 2013-08-17
Admin@Server:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[Share]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    netbios name = UBUNTU
    server string = Samba Server %v
    map to guest = Bad User
    dns proxy = No
    idmap config * : backend = tdb

[Share]
    path = /srv/SambaShare
    read only = No



No output for "net usershare info --long"

---

### Post by Morbius1 on 2013-08-17
You win the prize for the smallest smb.conf I have ever seen.

What are the permissions on the target shared folder:
```
ls -dl /srv/SambaShare
```

---

### Post by ZellTM84 on 2013-08-17
Admin@Server:~$ ls -dl /srv/SambaShare
drwxr-xr-x 3 nobody nogroup 4096 Aug 17 07:26 /srv/SambaShare

---

### Post by Morbius1 on 2013-08-17
That's an odd setup for a share. You nave enabled write access but limited it to credentialed users only.  After the pass the correct credentials they are no longer "nobody" however and "nobody" is the only one who has write access. 

Anyway, that's not the original question which was why does the linux client not ask for credentials. Actually the Xubuntu machine can't even see the share.

If you run the following command on Xubuntu there are no error messages:
```
thunar smb://192.168.1.100
```
[COLOR=#0000cd]**EDIT**: Finally got around to reading all your links to the HowTo's you are using. The last one deals with AppArmor. Did you do anything with AppArmor? I know nothing about it as I have never used it. Don't know if this is interfering with anything or not.[/COLOR]

---

### Post by ZellTM84 on 2013-08-17
no error messages when running "thunar smb://192.168.1.100".  The share appears open; however, i see none of the files/directories nor do I have permission to create files/directories in the share.

No, I didn't mess with AppArmor; I just looked under the "Security = User" section.

---

### Post by Morbius1 on 2013-08-17
So you can see the list of shares.

You can access the share labeled "Share".
[COLOR=#0000cd] *If you are able to do that without passing credentials you must have selected "Remember Forever" at some point in the past when you accessed the share.*[/COLOR]

But you cannot write to the share.
[COLOR=#0000cd] *No one can write to the share. The share is writeable only to "nobody". None of your clients are nobody.*[/COLOR]

And the share appears to have no content.
[COLOR=#0000cd]* That's interesting. What are the permissions of the contents of that shared folder:*[/COLOR]
```
 ls -al /srv/SambaShare
```

---

### Post by ZellTM84 on 2013-08-19
Morbius1,

   I figured out some things since yesterday.  First, Thunar - the default file browser on Xubuntu - had issues opening up anything over the network; this was the reason the credentials window wasn't popping up.  After quickly installing Nautilus, that issue went away: I now get the credentials pop up!  Once you mentioned permissions, that set me on the right track.  Now I just got to figure out an effective ownership setup on the share.

-Thanks for the help!

P.S.: Restarting the daemons - i.e., "sudo restart smbd && sudo restart nmbd" - takes a solid minute or so to register from the client side; so, I'd suggest a hard restart of everything just to make sure everything works smoothly.

---

