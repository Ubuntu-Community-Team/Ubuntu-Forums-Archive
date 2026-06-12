---
title: "100% Linux PDC and Clients Setup!"
date: 2006-08-18
forum: Server Platforms
---

### Post by Jabran Asghar on 2006-08-18
Hi,

I have been looking for information on 100% linux based setup which includes 

1. Domain Controller (LDAP + Samba), this also should be a File Server
2. Linux Clients (authenticate from Domain Controller through LDAP)
3. Linux Client user home directories hosted on Domain Controller (Roaming profiles in Microsoft Terms)
4. Accessing Domain shares from Linux (Authentication of shares through LDAP), if an LDAP user is already logged in the client, then accessing the shares should not require additional password prompt)

I managed to achieve no. 1 and no. 2. 

No. 3 I tried using NFS, but NFS has its flaws requiring to synchrnize UIDs and GIDS accross all machine, which is a big overhead. Using Samba shares, mounting them in /etc/fstab file requires provision of client password in the fstab file or in a separate file. This approach is also not very useful, as if user changes his/her LDAP password, it must also be changed in the correspoding files locally. This is also not much practicale in case 2/3 users use the same machine on different days, or a single user used to login on differnt machines.

All the scenarios I found on Samba site and forums mostly consider the scenario invloving Linux based PDC and "Windows Clients". I achieved no. 3 and no. 4 when using Windows as client machines, but could not make them work for Linux Client machines.

I am not assuming that the whole LDAP and Samba stories are to service "Windows Client Machines", so there must be 100% Linux based setups providing the same functionality or at least providing similar alernatives.

Can anyone please suggest options for point 3 and 4?

(I am using Ubuntu Dapper for server and client installations).

Thanks for putting in any thoughts.

Regards,
Jabran

---

### Post by alanandhispc on 2006-08-20
have a look at the karoshi code for the client and also for zen the main file server.

[www.karoshi.org.uk](www.karoshi.org.uk)

this is a education server setup, but there is a lot additional business functionality in there, like windows xp client connection.

heafty read, but should have all the anwsers

fancy documenting you completed steps, i would apprecate a ldap, samba setup on ubuntu.

Alan

---

### Post by dazedandconfused on 2006-08-20
Hiya,

I have an answer for 3 but it's set up on my work PC and I can't find find the info on the net.

Will post it tomorrow.

Cheers,

Jools

---

### Post by Jabran Asghar on 2006-08-21
> **dazedandconfused said:**
> Hiya,

I have an answer for 3 but it's set up on my work PC and I can't find find the info on the net.

Will post it tomorrow.

Cheers,

Jools

Hi

Alan: I checked the link and it seems interesting, but I more prefer to get hold of all components involded. I intend to post a full setup doc and am trying to put bits and pieces together.

Jools: It will be great if you can post some info.

Thanks.

Jabran

---

### Post by lavanga on 2006-08-25
hi 

i have suse 9 LDAP and Samba , can i get the kubuntu clients authenticated with it , any resource links please

---

### Post by dazedandconfused on 2006-08-29
Hiya,

Firstly, a thousand apologies for the delay. I've been away for a few days and haven't had access to a PC but I'll try to set things straight now.

Firstly, Karoshi is an excellent package but it does have the limitation that it doesn't run LDAP which you quoted as a requirement.

For LDAP + Samba the best source of info has to be IdealX at [www.idealx.org](www.idealx.org). They also produce the smbldap toolkit which has all the tools for creating, modifying and deleting Samba/LDAP accounts. I have smbldap running on Redhat EL4 at work where we have a PDC, two BDCs and 350 Linux/Windows dual boot clients but I will say this much; Follow the Idealx instructions to the letter. Read them though first, preferably several times and stick to them. Even the slightest error can lead to an evening or five of debugging ;) As soon as I have it running reliably on Ubuntu I will be posting instructions on my website at [www.foss4all.co.uk](www.foss4all.co.uk) (may be a while yet though).

Once you've set up LDAP and samba as per Idealx you need to install libpam-mount on the Linux clients and modify pam to use smb authentication. I'd recommend smb authentication as you'll be using it with your Windows clients anyway although you could authenticate against  LDAP directly. You'll need to modify various files in the PAM (portable authentication module) configs to allow Linux clients to authenticate against Samba or LDAP. Samba auth uses lib_winbind.so and there are instructions here:

[http://ubuntuforums.org/showthread.php?t=5409](http://ubuntuforums.org/showthread.php?t=5409)

Assuming you're using winbind auth you should add the following entry to your /etc/security/pam_mount.conf file on the Linux clients for each Samba share you wish to mount substituting server_name and YOURWORKGROUP for the settings you require:

volume * smb server_name &       /home/YOURWORKGROUP/&     uid=&,gid=&,dmask=0700,workgroup=YOURWORKGROUP - -

The uid=& and gid=& will force the client to mount the user's share on the named server with the ownership and permissions of each user. If while creating the user's accounts using smbldap-tools you specify this directory as the user's home, any user related files should follow the user around like Window's roaming profiles although I cannot guarantee this as I've only just started implementing Linux on my work's network clients but I'm pretty sure it'll work.

If at the end of this you don't need Windows support I believe you can achieve LDAP/Linux support using autofs/LDAP although  of this I know little :)

Try a Google search and see if it fits your needs any better.

All the best,

Jools

---

### Post by Jabran Asghar on 2006-08-30
Hi,

Thank you Jools for the information. pam_mount worked to mount remote samba shares through SMB authentication (Single Sign On).

For roaming linux profiles, I have little luck yet. As I am using Samba, the remote profile will be basically placed on a samba share on Linux PDC. I am working on following idea:

a. Share user's home directory on the Linux PDC through Samba --> OK

b. Use pam_mount to mount the remote hoem to a local mount point (e.g. "/mnt/<user>/remote") --> OK

c. On user login (GDM/Text/Whatever), use Unison to synchronize user's local home dir ("/home/<user>") to the remote mounted home dir ("/mnt/<user>/remote") --> PROBLEM!

d. On user logout, synchronize the above two directories again --> Could find a place to do this!

In point (c), Unison is not able to synchrnoize contents to samba share and gives permission errors. I have tried using "-perms 0" and its variants with Unison, but no change. User can read/write to the mounted share normally, so share rights seems not to be a problem. For text login, I am using .bash_profile to start unison, and for gdm I am using .gnomerc to start unison. Any thoughts?

In point (d), I could not find a place to put unison command. What I need is: Execute unison command when GDM/Test sesson is logged out, so that local home and remote home can be synched.

Of-course Unison problem is at its place as well :-(

Thanks for any further thoughts.

Jabran

---

### Post by dazedandconfused on 2006-08-30
Hiya,

Have you tried naming the mount point as the user's Linux home directory?

I'm planning on trying that myself but haven't got around to it yet.

Cheers,

Jools

---

### Post by kartheekpn on 2006-09-13
Hello Jabran,

I have used the Idealx document and smbldap-tools....
I am able to do the following:
Authenticate Windows User and Give Him "Home Directories"
Autnenticate "Linux Client"...
But I am not able to give him home directory...

When I log in to a linux client, i get authenticated but no home directory...
Now, from this thread I am understanding that I need to get pam_mount, for mounting home directory via samba....
I have installed pam_mount, but i am not able to get it work...
Can you please share the exact steps I need to follow on the linux client?

Thanks & Regards
KartheeK

---

### Post by hyrcan on 2006-09-13
There seems to be some confusion on this one:

*3. Linux Client user home directories hosted on Domain Controller (Roaming profiles in Microsoft Terms)*

It's important to understand just what Roaming Profiles in Microsoft do, in order to decide how to implement the functionality in a linux environment.  

First and most importantly, Roaming Profiles are *not* remote home folders.  They do not live, breath, and die on the server.  

Here's how roaming profiles work...

When the user logs into the computer (online) and there's no local copy of the Roaming profiles the system will download a complete copy of your profile from the server to the local machine.  When you logoff the system will check for any changes, if it finds any it will upload them back to the server.  The next time you logon to that machine the local copy of the roaming profile is compared to what is found on the server.  Anything that is newer on the server is downloaded, if there isn't any nothing is downloaded. Again when you logoff the system checkes to see if any new things are in the local copy of the profile, if there is it uploads them to the server.

If you are offline and you logon then these changes would be uploaded to the server the next time you are online and have logoff.

Of course if you make changes on a computer to FileA then on your laptop you modify FileA again when you logoff it will overwrite the changes you made to FileA the first time.  Not to mention that if you never logoff, e.g hibernate/etc  you'll never upload the profile.

To get this sort of experiance from a Linux Desktop all one would need to do is create logon and logoff scripts that rsync's the user home folder to a remote share folder.


Microsoft also has the ability to "Make folder avalible offline" which is a cacheing sort of thing... this works differently in that when online it actively posts things to the server instead of waiting for you to logout.  

This activity would require something more than rsync, though I've not looked into what that maybe...

---

### Post by kartheekpn on 2006-09-14
Hi Hyrcan,

Thankyou for the inputs....
In my case all i need to do is to give the "Linux Client", the Home directory for my File Server/Samaba PDC/LDAP server.
As of now, I am able to do everything for Windows users, but I am unable to give the linux clients the home directory.. I am not loking for roaming profile....

My Doubts: :confused: 
Can Samba PDC + smbldap-tools(From Idealx) alone give the home directories to linux clients?
Should I mandatoryly use pam_mount on all linux clients?

Thanks & Regards
KartheeK

---

### Post by lramos85 on 2006-10-16
I'm working on this:

[https://help.ubuntu.com/community/LDAP-Samba_PDC_%28for_Linux_and_Windows%29](https://help.ubuntu.com/community/LDAP-Samba_PDC_%28for_Linux_and_Windows%29)

Still under construction as of 10-16-06

---

