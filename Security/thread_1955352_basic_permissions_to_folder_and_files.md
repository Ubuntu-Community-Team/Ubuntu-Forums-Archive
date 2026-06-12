---
title: "basic permissions to folder and files"
date: 2012-04-09
forum: Security
---

### Post by ButchMel on 2012-04-09
Hi,

I'm new to Linux, period. And building a file server at home. 

After over a week of trilas and errors and conflicting share permissions between Linux, Samba and nautilus, I can now access all 4 different hard drives of this server from any computer at home (Mac and Windows). 

Two of these (NTFS) drives were simply pulled from a Windows machine and connected to the (Unbutu server 10.04.4 only) machine. 

Now, I would like to secure some critical folders on different drives, but I am told that I do not own these files, so I cannot change permissions. Bought a 704 pages 'Unleashed' Ubuntu book with lots of descriptions but useless for a newbie (and I don't need chapters to know I can go on the web with Ubuntu...). I surfed here but found commands which I am unsure 'where' and 'how' to use and apply at the right place.

Let's go with a simple exemple:

1) a folder is on an external drive, showned as /dev/sdd1 in Disk Utility. Say the folder is called 'FolderOne'.

2) I want this FolderOne accessible just by me (User1). No read, write or execute by anyone else. Of course I want the same apply to all content of this folder (files and sub-folders). Ideally (if this exists as it does in Windows): can I also (not to say 'simply') make the folder 'hidden'? (If so, then how would I access this from another machine ? - or maybe I'm self answering that question here?....) 

Now, if I double-click the drive, right-click the folder, go to permissions, I see at the bottom that I am not the owner and cannot change permissions). 

Is there a way this can be done under Gnome or does it have to be changed in terminal ? (And yes, I'd like to learn the second one, please).

Doing through terminal, hat would be the exact steps to get exactely 'there' and do appropriate changes ?  (For meaning of the command, I guess I can find these i my book.... But there's no place in there I find a clear 1-2-3-4-5....

Thanks

---

### Post by Cheesemill on 2012-04-09
If the folder is on one of your NTFS drives then you are out of luck, NTFS drives don't understand the Linux permissions system.
You can only have one set of permissions for the entire drive which are set when it is mounted.

For understanding permissions on a Linux formatted drive (ext2, ext4, etc) there is a good article here:
[https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions](https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions)

---

### Post by Morbius1 on 2012-04-09
First, Ownership and Permissions are different on NTFS partitions then they are on Linux partitions. 

[COLOR=Blue]**[]**[/COLOR] Linux mounts an NTFS partition with a "view" that gives it the appearance of having linux permissions but ones that permeate throughout the partition. For example if I automount a partition with a line in fstab that looks like this:
> /dev/sda1 /Mount-ntfs1 ntfs defaults,uid=1000,umask=077 0 0Then the sda1 partition will mount to /Mount-ntfs1 with the owner as me ( assuming my user id is 1000 ) and with permissions for me to read/write/execute not only the mount point itself but everything within it. But it will give no access to anyone else. I can change the way Linux views this partition and change who owns, who has access to, and what they can do by manipulating different parameters in the fstab line.

Just keep in mind that you cannot apply different linux ownership and permissions to the subdirectories and files of the ntfs partition because that would violate the parameters set up in the "view" ( i.e., fstab ).

[COLOR=Blue]**[]**[/COLOR] Linux partitions are just the opposite. They have ownership and permissions built into the folders and files themselves so you don't specify ownership and permissions in the mount only after it's mounted.

[COLOR=Blue]**[]**[/COLOR] You've complicated somewhat this discussion by bringing up Samba. I could set the ntfs partition to be rwx by everyone and your Aunt Tilly by having this line in fsab:
> /dev/sda1 /Mount-ntfs1 ntfs defaults,umask=000 0 0And then use the share definition to determine who has access and what they can do:
> [ntfs1-share]
path = /Mount-ntfs1
valid users = morbius
read only = yesThe local box internally may have made that partition universally accessible but samba will let only morbius connect to it from the network and he will only be able to read.

---

