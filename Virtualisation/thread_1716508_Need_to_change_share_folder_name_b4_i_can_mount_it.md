---
title: "Need to change share folder name b4 i can mount it"
date: 2011-03-28
forum: Virtualisation
---

### Post by jao_madn on 2011-03-28
HI

I would like to ask about my virtualbox 4.0.4 in my lucyd lynx box

My shared forlder isn't auto mount in my linux guest OS. And everytime i manually mount using command sudo mount -t vboxsf <shared_folder_name> <Guest_location> i need to first change the filename of the shared folder before i can mount it manually..

Hope someone can shed a light of my problem..

Thanks in advance

---

### Post by jao_madn on 2011-03-28
What i mean from my post. Is that the shared folder i create doesn't  automount to my desired location which is in my home share folder or  don't know where it automount location in the guest OS. if i execute a  manual mount command which is sudo mount -t vboxsf  <local_share_folder> <Guest_share_location> it throws  various error about the mount.vboxsf-------. and i need to chage the  SHARED_FOLDER name before i can mount it using the command i mention  earlier.

I think i had a new problem

I just recently knows  the the automount is located in the /media/sf-<share_folder_name>  my problem now is the /media/sf-<share_folder_name> is root  permission and i cant view the content not unless i su to root in  terminal..

How do i accomplish to mount it to my desired location ~home/vboxshared-guest

i already add in the fstab the following 
sharename Guest_mountpoint vboxsf uid=<my userid 1000>,gid=<vboxGID=1001 0 0

after  some checking in the mount command i found that its mounted to my  specific location but after sharing files only in the  /media/sf-<shared_named> the files located not in my specific  location

here are mount command output in restart

vboxsharedname on /home/user/vbox type vboxsf (uid=1000,gid=1001,rw)
vboxsharedname on /media/sf-vboxsharedname type vboxsf (gid=1001,rw)

By the way this two location will dis appear it i execute the sudo mountall command

---

### Post by jao_madn on 2011-03-28
Its ok now. i just accomplished my goals. the shared folder is mounted to my desired location

what i did in the second post is the right one..the only problem is it didn't loaded to the main config files so decided to give it a try to close the virtual box and also the main virtualbox menu in which u manage all your VM.. and after i try to open it. and bwela its OK right now.

and also i uncheck the automount in the shared menu. I read in the Vbox wiki that if the automount is enable it will mount to the /media/sf-share_name location default.

Thanks and Best Regards.

---

