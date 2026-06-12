---
title: "File sharing through the internet"
date: 2007-08-09
forum: Server Platforms
---

### Post by newtronica on 2007-08-09
I have a client who has 4 different locations with all Windows based networks in place.  We are putting in an Ubuntu server to act as an Axigen mail server for them, and now they have decided that they would like to be able to share files from the Ubuntu server to the 4 locations.  

I have done this before with Windows 2003 servers by setting up an incoming VPN connection and then setting up each users workstation to connect to it with a simple shortcut.  And I managed all the permissions through Active Directory groups.

What I would like to be able to do is to connect each user to the server via VPN or some sort of other secure internet connection and be able to map the drive to the local Windows machine.  

Could someone please give me some direction on how to set this up using the Ubuntu server?  Ive read a bit about OpenVPN, but even if I establish the connection from the users to the server, Im not sure how to control the permissions of the folders.

Thank you to anyone who offers help.

---

### Post by steve.horsley on 2007-08-10
OpenVPN would be my suggestion. It's easy to set up, and has good security. 

For sharing files from Ubuntu, you need to install **samba**. There are lots of guides for installing samba, just remember that lots of these guided forget to mention that you have to specifically add users to samba. Most samba guides don't bother to mention this rather critical fact.

---

### Post by newtronica on 2007-08-10
Thank you for the reply, Steve.

Ive setup Samba before and am somewhat familiar with the process.  Is there any sort of GUI for managing user permissions to each folder?  Such as, can I add users to appropriate groups and then allow those groups permissions to the folders that they need access to?

Thanks again,
Newtronica

---

### Post by jimcooncat on 2007-08-10
Until you're able to incorporate something better (Samba and Openvpn?), here's a way that you can set up fairly quickly.

Run an SSH server on your Ubuntu server. Have it listen to a nonstandard port, that is, don't have port 22 available to the internet, use something much higher and obscure (like 22022). Make a user for each participant. Create symlinks in their /home directories to your shared directories. 

Have your Windows users install WinSCP and give them instructions on how to set it up with usernames, passwords, and your servers hostname and nonstandard port.

Bonus points for implementing public key authentication. WinSPC comes with Puttygen and Pageant to help your Windows users with this. That will keep the kiddies from brute-forcing your system if they do find your SSH server running on your nonstandard port.

If you use a linux client, you can use one of several FTP-type clients that can do SSH file transfers, I use gFTP. More seamless would be using setting up the file manager to connect -- I understand this is available on both Gnome and KDE. But I think the best, if you're going to use it a lot, is sshfs. That makes the shared directories available even if you're using the terminal, and saves configuration pain if you use more than one desktop environment. I use seahorse and libpam-keyring for public key helpers (link to tutorial: [Password Hell Resolved]("http://staff.xiaoka.com/smoku/2007/05/17/password-hell-resolved/")). [Edit: Link no longer working. Have pasted text of it below.]

Since your clients will appear as if they're using your system, managing permissions is very easy.

Disadvantages:

Not seamless for Windows users. There might be a trick I don't know about, but they would have to use the WinSCP interface (which is very nice to use, though) to open documents and manage their files. No opening the files directly from an application, or access from other file managers like Windows Explorer.

No file locking or advisories. This works by making a copy of the file to the client, then copying back the edited file. If two people are editing the same file at the same time, the last one to finish wins -- the first person's edits are lost!!! 

Communication is needed to avoid this. One way is to train users to rename popular files before editing, for example: 

[LIST=1]
[*]rename policy.doc to policy-edit-JC.doc 
[*]edit policy-edit-JC.doc
[*]look to see there isn't any new policy.doc file
[*]rename  policy-edit-JC.doc to policy.doc
[/LIST]

Not good for huge files. Because it makes a copy of the file over a somewhat slow (because of encryption) connection, I wouldn't suggest trying to use this for video editing, RAW format photos, etc.

----- Following is text of article from Password Hell Resolved -----

Password HELL - Resolved
Published 3 months ago in KnowHow. Tags: Bez Tagów.

There it is. Your Linux system just booted and you’re presented with a GDM screen asking you to provide an username and password. That’s fine. You really want only authorized users on your machine.

You enter your username and password and your GNOME desktop loads. NetworkManager starts, seeing there are some wireless networks on the air, tries to access them, but to do that it needs to access wireless keys. These are stored in your keyring, which in turn is protected with a keyring password. You are presented with a keyring unlocking dialog asking for your keyring password.

Next you need to access files on a remote site. This is accessible via SSH protocol and you use SSH keys authentication. The keys are protected from unauthorized access with a key passwords. You’re presented with an SSH key unlocking dialog asking for your key password.

Some minutes later you want to send an email. Evolution is configured to automatically GPG sign your emails. To do this it needs to access your GPG, which is password protected. You’re presented with an GPG key unlocking dialog asking for your key password.

Sounds familiar?

Protecting your keyring and your keys with passwords is a GoodThing(TM). Under no circumstances you shouldn’t use empty passwords to make your life easier. You will loose all passwords (and all accesses) if someone gets access to your files. This really could happen by accident. You really do not want this.

But you were authenticated during GDM login, so is there a way to just use the keys you own without all the password hassle? Well… There luckily is.

The solution consists of two things. First is pam_keyring module, that uses your login password to unlock your keyring during login. Second is the Seahorse application, that handles all your SSH and GPG keys, unlocks them as needed and stores the key passwords in… the GNOME keyring.

So, let’s install it. Under Ubuntu this is:

sudo apt-get install libpam-keyring seahorse

You will get the file /etc/pam.d/common-pamkeyring which says that you need to add a line @include common-pamkeyring to a PAM file of a service you want to use pam_keyring module. So let’s edit /etc/pam.d/gdm.

sudo gedit /etc/pam.d/gdm

It should contain something like this:

#%PAM-1.0
auth    requisite    pam_nologin.so
auth    required    pam_env.so
@include common-auth
@include common-account
session    required    pam_limits.so
@include common-session
@include common-password
# added for libpam-keyring
@include common-pamkeyring

And you’re done. Please notice, that the line should be last, and you shouldn’t have any sufficient lines.

One more thing is that you need to have your keyring password the same as your login password. There is no way to change it, so if it is different you need to delete ~/.gnome2/keyrings/default.keyring and recreate it after login (giving your login password).

Seahorse configured itself to autostart automatically, so you do not need to edit anything. You may launch Encryption Preferences though and check if you have an GPG key configured and SSH key loading enabled.

Now reboot your system, relogin and enjoy.

---

### Post by jimcooncat on 2007-08-10
lol -- that's what happens when I take an hour to write a post!

---

### Post by steve.horsley on 2007-08-11
I have used **gsambad** before - actually, it's the only time I ever got samba to work. It's in the repos.

---

