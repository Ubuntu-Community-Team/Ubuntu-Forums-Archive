---
title: "Pam-mount on 12.04 LTS"
date: 2013-03-02
forum: Server Platforms
---

### Post by vikfreeze on 2013-03-02
Hi,

im trying to configure libpam-mount to mount user homes when a user logs in via freenx, this worked on 10.04 LTS but pam is not playing along on 12.04.

The problems come from the way pam-mount is invoked in pam, at first it only invoked for the nx user and not the user who is logging in, moving the pam_mount.so entry higher in common-session made pam-mount invoke for both nx user and the user logging in. The nx user fails to authenticate in samba witch is normal but so does the users attempt, witch means pam is forwarding the wrong credentials. Mounting the share manually works fine.

I need some help from anyone who is familiar with how the /etc/pam.d files on 12.04 work, i simply don't understand how they work as a whole so i don't know what im doing. I do however know what i have to realize:
1.Make sure pam forwards the users login password
2.(optional) limit pam-mount to a distinct group(to excluse the nx and root user)

Alternatively, if anyone knows a better way to mount samba shares from a central server at login, id be more then happy to try it since libpam-mount is not maintained anymore witch is the reason for all these issues

---

### Post by ranger12 on 2013-03-02
You might try looking into using autofs on the client and mounting the samba shares that way. I use autofs to mount the user's home directory when they login to the server but I use nfs and not smb but the autofs package does come with a auto.smb automounter file. I have been using autofs for about 8 or 9 months now on my lone workstation and have had no issues with it so far. I have not actually tried automounting a samba share yet.

---

### Post by vikfreeze on 2013-03-03
i did look into autofs but from what i understand its not what i am looking for since you have to specify the username and password witch is no different than static mounts in fstab. The entire pint of pam-mount is that its completely general, like this:

<volume fstype="smbfs" server="mysambaserver" path="homes" mountpoint="/home/%(USER)" options="domain=ads,sec=ntlmv2" />

and it uses whatever password is supplied at log in witch is the entire point since i don't know the user password.

Can autofs be used like this? If yes can you show me how to set it up since all i came across needed the credentials to be specified.

---

### Post by ranger12 on 2013-03-03
I use nfs and for mounting nfs mounts you do not have to specify a username in the file - you can do it that way. I do not know about samba shaes since I have never tried it. For nfs mounts I do this:

auto.master file has this:
/home auto.home

auto.hone file has this:

* -fstype=nfs4    elrancho.local:/home/&

Whatever user logs in, it grabs their home directory off the file server and mounts into /home on the workstation. Samba shares maybe different. I don't use samba even though I have my file server setup as a Samba PDC.

---

### Post by vikfreeze on 2013-03-04
how is your export set up? i.e. do you need to provide credentials to mount or is the share public?
ill may give it a try but i doubt it works for samba and nfs does not export symbolic links so i cant use it to export the homes

i did manage to get a bit further tough, it seems that my hunch was right that pam was forwarding the wrong credentials and it was due to the ssh daemon settings in /etc/sshd_config witch need to look like this:
**ChallengeResponseAuthentication no** (was changes by lwopen)
**PasswordAuthentication yes** (this is default)

Now the share mounts at log in but it does not unmount at log out, im not sure if this is a permission or configuration problem(i think i have seen this issue in some forum)

so now the only thing left is if i can configure pam not to invoke for my local user, the nx user and root since this only results in errors because these users don't exist in the active directory, this is not a necessity but it  would be nice to have

Thanks for your support ranger12

PS. /etc/pam.d/common-session also need to be modifyed to invoke pam-mount see:[https://bugs.launchpad.net/ubuntu/+source/likewise-open5/+bug/552001](https://bugs.launchpad.net/ubuntu/+source/likewise-open5/+bug/552001)

---

### Post by ranger12 on 2013-03-04
For nfs in the exports file? No credentails needed. This is what is in my /etcexports file on my server:

/home xxx.xxx.xxx.0/24(rw,sync,no_subtree_check)

This exports the /home directory of my server to my lan. I have never had any trouble with it. Now keep in mind this is for nfs not samba. I do have the /home directory set up as a samba share in my smb.conf - I just do not have it automounted when I log in from the workstation. The authentication on the workstaion is done via ldap thanks to libnss-ldap. After I login than autofs takes over and mounts my home directory off of my server.

---

