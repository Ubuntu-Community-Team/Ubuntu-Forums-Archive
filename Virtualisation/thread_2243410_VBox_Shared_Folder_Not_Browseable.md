---
title: "VBox Shared Folder Not Browseable"
date: 2014-09-08
forum: Virtualisation
---

### Post by JKyleOKC on 2014-09-08
I'm running Xubuntu 12.04.4 as the host and have installed a copy of Xubuntu 14.04.1 as a guest, with my home folder on the host (/home/jk) set up as a permanent shared folder, not read-only, and auto-opened.

However any attempt to browse that folder through its mount point at /media/sf_jk returns "Access Denied." The same thing happens if I open a copy of Thunar as root via "gksudo thunar" and attempt to browse it. However if I go into the terminal emulator, do "sudo -i" to get to a root prompt, and then "ls -l /media/sf_jk/" I do get the listing.

All attempts, so far, to modify the permissions have failed without any error messages. These include remounting with uid=1000, chown -R, and chmod 777 among others. Typing "mount" shows the shared folder open with GID=999,rw as its options, and I'm a member of group 999. The permissions for the mount point are rwxr-x--- which should make the folder readable to me but not writable (although I do not have read-only checked for it in VBox).

It's rather pointless to have a shared folder to which all normal access is denied. Has this happened to anyone else? VBox version is latest with all updates, installed and updated via Oracle's PPA. Guest additions are installed and everything else seems to be working. Suggestions?

---

### Post by TheFu on 2014-09-08
Please post the ls -al from the host AND from inside the guestOS of the mount areas.
Sounds like a simple permission/ownership issue so far.

Also - please ensure the shared folder is using a Linux file system.

---

### Post by JKyleOKC on 2014-09-09
[ATTACH=CONFIG]256295[/ATTACH]> **TheFu said:**
> Please post the ls -al from the host AND from inside the guestOS of the mount areas.
Sounds like a simple permission/ownership issue so far.

Also - please ensure the shared folder is using a Linux file system.This is from inside the guest; I don't understand which host folder you want to see.

If I get to a root prompt in the guest, then everything in "sf_host" shows up. The "sf_jk" is left over from earlier attempts; I changed the name on the share from "jk" to "host" thinking there might be confusion between too many "jk" folders!

The puzzling part is that "sudo chown" and "sudo chmod" have no effect, nor does remounting of "sf_host" with "uid=1000" but in none of these cases do any errors show up either interactively or in the syslog.

EDIT: Both filesystems are ext4.

---

### Post by TheFu on 2014-09-09
Morbius's answer below is better.

---

### Post by Morbius1 on 2014-09-09
If instead of "ls -al /media/*" you did this:
```
ls -al /media
```
You should see that the /media/sf_XYZ is accessible only to root  and members of the vboxsf group.

So the question is are you a member of the vboxsf group in the guest:
```
groups
```
If not then add yourself:
```
sudo gpasswd -a your-user-name vboxsf
```
Then logoff ( of the guest ) and login again to make the group change.

---

### Post by JKyleOKC on 2014-09-09
> **TheFu said:**
> You don't know which directory (not called "folder" in UNIX) you are sharing on the hostOS? That would make it impossible to set the permissions correctly on the hostOS - at least that is how it seems from here.  I'm confused by using any "uid" setting at all.

You are trying to share a directory ON the HOSTOS to the guestOS using vbox settings, correct?

Perhaps using NFS would be easier? - oh - and root doesn't work with nfs by default. It is a security consideration.

Based on your bean count, I assume someone with many, many, many years of experience at the CLI - with a complete understanding of users, groups, permissions. Is that not the situation?[ATTACH=CONFIG]256298[/ATTACH][ATTACH=CONFIG]256299[/ATTACH]Noo, I just didn't understand that you wanted to see the listing of the directory I'm trying to share -- which is my home directory of "/home/jk" on the host.

These two screenshots show what happens when I try to change permissions at the guest, and the first screen's worth of listing at the host. Note that on the host, the directory permissions are 775 while on the guest it's mounted with 770.

I've been doing this as my standard for host-guest communication for several years now, through three previous LTS versions of hosts. Current host is 12.04.4 and guest is 14.04.1; I'm evaluating 14.04 to get a feel for its changes before updating all my hosts to it. This is the first time I've run into anything like this.

I like to think I understand the permission structure pretty well, having worked on MULTICS almost 40 years ago and used Linux on and off since Slackware 2 but full-time for the past 6 years. However it's always possible for glitches to sneak in. I did initially create the guest VM to use bidirectional drag-and-drop together with bidirectional clipboard, which might have had something to do with it. However disabling both features from the Devices menu, then rebooting the guest, made no difference at all. 'Tis a puzzlement!

Thanks for any ideas. I've examined the guest log and find only one mention of the shared folder...

---

### Post by JKyleOKC on 2014-09-09
> **Morbius1 said:**
> If not then add yourself:
```
sudo gpasswd -a your-user-name vboxsf
```
Then logoff ( of the guest ) and login again to make the group change.I posted my previous message before seeing this -- and you solved the problem! This is apparently something new in 14.04.1, since I don't recall ever having to add the "vboxsf" group to my list before; simply being a member of the "vboxusers" group was adequate!

Many thanks! I learn something new most every day, here...

---

### Post by ajgreeny on 2014-09-09
I am.using xubuntu trusty as a VM on a xubuntu precise host, and have been doing so since before trusty was finally released and I have had no problem sharing my complete precise home folder, just as you are trying to do. 
I am away from my normal machine at present and for another week but will keep an eye on this thread and add any further help I can manage as sson as I am able to do so.
I have no idea about permissions of my folders in the guest as it has not been necessary to look at them; everything simply worked as it should.
Watch this space; I will be back next week.

EDIT.
I have just noticed you have solved the problem.
I was already a vboxsf group member, hence my sharing success!

Glad you are now fixed.

---

