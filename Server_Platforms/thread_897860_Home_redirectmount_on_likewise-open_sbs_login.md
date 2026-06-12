---
title: "Home redirect/mount on likewise-open sbs login"
date: 2008-08-22
forum: Server Platforms
---

### Post by cjelec on 2008-08-22
Hi,

Yes first thread, but have been using linux/ubuntu for a few years, never needed to ask questions on here before, always managed to find the solutions needed, google was my friend.

Until now:

I'm using Hardy 8.04.1 as client
Windows SBS 2003 server
Successfully installed likewise-open and can login to sbs 2003 domain.

But what I'm trying to do now is get the domain users My Docs and Desktop (Profile) folders to be redirected or mounted over the users local Home folder, so that they can access their docs and settings on any machine on the network...

I thought I was going to be cleaver and set the homedir option in lwiauthd.conf to:

template homedir = smb://sbsdomain.local/share/%U

But it came up with an error when I logged in as 'test', something like: unable to find folder location 'smb://sbsdomain.local/share/test'... the path given does exist on the server.

Then thought about setting up a script that would mount the profile path over the default homedir (/home/%D/%U), but I would have the problem of the user not having root permissions to mount and I can't give them it either.

Read a few examples of having fstab mounts to the share folder, and guess I could set homedir to it like:

template homedir = /mnt/servershare/%U

But this would open a security hole, cos the servershare would be visible to all, and the username and password to access the share would be available in the fstab file for all to see...

So my question, is there a better or 'proper' way to do this. Or can my idea's be modified to work securely?

Any help, advice or links on this would be very much appreciated.

Thanks

Chris

---

### Post by cjelec on 2008-09-04
Hi,

I'm still working to get this right. I have continued with the smbfs share in the fstab, that points to the location where the users home folder exists on the sbs server. And I can login, see my documents and desktop icons, but I get a few errors regarding the folder (/media/users/* for example) being read-only.

Looking at the folder it is root r/w only, and I could change this by setting chown and chmod, but that would only grant one user and I have a few users that would need access, so I could do it by group but which one?

If any one can help, I would be v/much appreciated.

Thanks again

Chris

---

### Post by croperz on 2008-09-08
I am in the same position as Chris. Any help would be greatly appreciated.

---

### Post by cjelec on 2008-09-08
croperz,

I'm actually looking at mod'ing the source code to allow for home folder mounting when the user logs in.


If I get anywhere with it, I'll post something here. Currently having a problem with the sbs server so this project may be on hold for a week :(


I'm guessing that it would only be a few lines of code:
1) check the config file for mount point details
2) run the smbfs mount script using the logged in users name for the smbfs permission masking...

If anyone can help with this mini project, more the merrier. One problem I have at the mo, is where in the source code to put this mod. It needs to be right after the auth check comes back as ok from the server...

anyway, back to the sbs woes...

Thanks

Chris

---

### Post by Goosemoose on 2008-09-17
Any luck on this? I'm having the same issue. I was trying to follow the docs here: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently) but without much luck.

---

### Post by likeWiseGuy on 2008-09-24
> **cjelec said:**
> croperz,

I'm actually looking at mod'ing the source code to allow for home folder mounting when the user logs in.


If I get anywhere with it, I'll post something here. Currently having a problem with the sbs server so this project may be on hold for a week :(


I'm guessing that it would only be a few lines of code:
1) check the config file for mount point details
2) run the smbfs mount script using the logged in users name for the smbfs permission masking...

If anyone can help with this mini project, more the merrier. One problem I have at the mo, is where in the source code to put this mod. It needs to be right after the auth check comes back as ok from the server...

anyway, back to the sbs woes...

Thanks

Chris

Hi Chris,

It looks like you're moving along with this. I hope you're able to get this done.

The only other way I know of to manage the home directory for domain accounts is to use Likewise Enterprise, which allows you to manage user configurations on Linux and much more on the domain controller. 

I wish you best of luck and keep us posted with your solution. If you need any help, please let me know. I'll see if I can help you out.

---

### Post by Rudy507 on 2008-12-11
Hi Chris,
Any luck on this? I am trying to do the same thing right now, as we are contemplating moving most of our network computers over to Linux. I'm supposed to create the guinea pig computer, and that's what I'm doing now. 

I got the same error you got, and as a result, found this thread.

---

### Post by brian mcgee on 2009-02-12
This helped me:

[http://blog.cyphermox.net/2008/10/automatic-mounting-of-samba-shares.html](http://blog.cyphermox.net/2008/10/automatic-mounting-of-samba-shares.html)

For sbs user folders you might have to call a script from ~/.profile that auto-generates ~/.pam_mount.conf.xml based on username etc. That means it won't mount on first ever login. Also, on login, you might have to enter password twice (2nd time for pam_mount). I haven't had time to look at that, but I think there's a way to pass to pam_mount... :) 

Probably better ways of going about all this...

(btw, I know this thread is a little stale, but hopefully this helps someone)

---

