---
title: "Ubuntu 12.04 Alpha Virtualbox Folder Access"
date: 2012-02-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by afz12 on 2012-02-03
I installed Ubuntu 12.04 Alpha on a virtual machine (Virtualbox) from a Win7 computer and it actually runs extremely well! I have even embraced the Unity interface now. However I always have problems with "folder access" for any Ubuntu virtual machine running from a windows box. The USB access works fine, but how do I access a shared folder? (These are listed in the VB setup screen of course)

Interestingly, running XP, for example, on an Ubuntu box always provides simple and direct remote folder access. However the other way around is always problematic to me :)

I am not well versed in Linux and am probably best decribed as a dabbler. I have uses for XP, Win7 as well as Ubuntu and really don't believe in "one size fits all". Further, some external factors require Windows (I have no beef with Windows). Still, I'd appreciate any pointers on how to access folders on a Windows base from an Ubuntu virtual machine as this interchange can be quite convenient. I suspect the approach would be the same as in Ubuntu 11.10 (this also disto works extremely well and solves the niggly hassles that Ubuntu 10.10 / Thunderbird seemed to struggle with!) Thanks in advance.

---

### Post by oldos2er on 2012-02-03
Moved to Ubuntu +1 (Precise Pangolin).

---

### Post by r!ots on 2012-02-20
I was able to share folders between a windows 7 host and an ubuntu 12.04 alpha 2 guest. Here is what I did:

1. install the virtual box guest extensions using synaptic (or ubuntu software center). or open a terminal & paste this:

```
sudo apt-get install virtualbox-guest-x11 virtualbox-guest-utils virtualbox-guest-dkms
```

2. create a shared folder in the virtual box manager (devices -> shared folders).

3. create a mountpoint in your ubuntu guest install. this creates a folder called windows in your home directory:

```
mkdir ~/windows
```

4. mount the shared folder:

```
sudo mount -t vboxsf SHARE MOUNTPOINT
```

SHARE is the name you gave the shared folder at step 2
MOUNTPOINT is the mointpoint created at step 3 (e.g. ~/windows)

5. to mount the shared folder automatically, edit /etc/fstab and append the following line:

```
SHARE ~/windows vboxsf defaults 0 0
```

to edit /etc/fstab:

```
gksudo gedit /etc/fstab
```

DONE. you should now be able to access the shared folder from both the host and the guest system. for me, step 5 didn't work out. I have to mount the shared folder manually each time (step 4).

Have a look at the virtual box manual ([link]("http://download.virtualbox.org/virtualbox/UserManual.pdf")). Starting at page 65 you find all the information you need.

I just read on and realised, that automatically mounted shared folders are put in the /media/sf_SHARENAME directory of the guest system (page 66). If you tick the automatically mount option at step 2, you don't have to go on to step 3-5. Just rebooting your guest system should be fine. Nevertheless you have to change its permissons to be able to access it:

```
sudo chown -Rv yourUsername /media/sf_SHARENAME
```

---

### Post by Whoopie on 2012-02-21
Regarding the folder permissions: The /media mountpoint is mounted as root:vboxsf

Just add your username to the vboxsf group.
```

sudo adduser YOUR_USERNAME vboxsf

```

---

### Post by FulciLives on 2012-03-12
> **Whoopie said:**
> Regarding the folder permissions: The /media mountpoint is mounted as root:vboxsf

Just add your username to the vboxsf group.
```

sudo adduser YOUR_USERNAME vboxsf

```
I'm having some problems :(

I'm running Ubuntu 12.04 Beta 1 (32-Bit) as a guest and my host is Windows 7 Home Premium 64-Bit and of course I'm using VirtualBox (4.1.8 and it is updated).

I did what I quoted above and it seems to work. I found the shared folder under the FILE SYSTEM in MEDIA and made a bookmark for it so it would be easily accessible from the Nautilus file browser.

I can go to the shared folder and see my files.

So far so good BUT when I try to copy files from the shared folder to Ubuntu I get an error that says:
Error splicing file: Protocol error

I also tried the reverse (to copy a file from Ubuntu into the shared folder) and I get a similar error.

Not sure what is going on because this 'trick' of adding me to the vboxsf user group has worked in the past with Linux Mint and OpenSUSE when using them in VirtualBox with the same version of Windows as the host.

Any ideas?

By the way here are screen grabs of the two errors:

[IMG]http://ubuntuone.com/27QXRiDUPSk02QJzk5UZ47[/IMG]

[IMG]http://ubuntuone.com/6sL9sgwMzPVh59JcQeuZcU[/IMG]

---

