---
title: "Lifting the restriction of directory size to Install Windows through VMware"
date: 2013-11-09
forum: Virtualisation
---

### Post by psyclone on 2013-11-09
I've been trying to work through the following post, i.e. to adjust the  directory size to run VMware to install Windows, there's a restriction  on the folder size.

[http://www.yolinux.com/TUTORIALS/LinuxTutorialQuotas.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialQuotas.html) {taken from the following ubuntu-fourm post }
[http://ubuntuforums.org/showthread.php?t=1698297](http://ubuntuforums.org/showthread.php?t=1698297)

I've edited the /etc/fstab file by adding:


/dev/hda2            /home          ext3           defaults,usrgroup,grpquota     1       1 
chmod 600 /home/aquota.user


But my I can't mount/remount the  /home partition to go onto the next stage. 

sudo mount -o remount /home 

I get the following response:
mount:  /home not mounted or bad option
 
Also, rebooting doesn't fix this problem either.

Please help.

---

### Post by mcduck on 2013-11-10
Have you actually set the quotas at some point then, and do you really need them? By default there are no size limits (apart from the size of your disk partitions, of course).

What comes to fstab modification, it seems like you have just copied and pasted the code from the website? That's not going to work, you have to use the partitions that actually exist on *your* system. "hda2" is and old way of pointing to second partition of first hard drive, these days the correct device name would be "sda2", although you should be using UUID instead (like all the default entries in fstab do). Also Ubuntu has used Ext4 as the default file system for quite a while now, and of course unless you actually have a separate /home partition you can't edit the settings for one...

Coould you describe the error you are getting (while trying to create the virtual machine) in a bit more detail, and where are you trying to create it? If you tr to create one on a partiton or external drive formatted as FAT you'll have max fiel size limit of 4GB as FAT filesystem doesn't support larger files than that. If youare insetad tryign to create it on your Linux partiton please post the output of "*sudo fdisk -l*" and contents of your fstab file so we can take a better look at what's gong

---

### Post by oldos2er on 2013-11-10
Moved to Virtualisation.

---

### Post by psyclone on 2013-11-11
To reply to:
 		                                                                                                                                                    1 Day Ago                                                                                                                                                                                                     [#2]("http://ubuntuforums.org/showthread.php?t=2186922&p=12843650#post12843650")                                                                                                                                                                                      		
  		 			 				 					[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar17309_6.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=17309") 				 				 					 						 	[**[COLOR=#000000]mcduck[/COLOR]**]("http://ubuntuforums.org/member.php?u=17309") 	 
 						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG]  					 					 						mmmm... Ubuntu. 					 					 						[IMG]http://ubuntuforums.org/images/rank_26.png[/IMG] 					                                           					 					 						 							     						
 					 				
 			
 			 				 					 					 					 				

 			 		
 	
  	 		 		 		 		[h=2]Re: Lifting the restriction of directory size to Install Windows through VMware[/h] 		 				 				 		 			 				[INDENT] 					Have you actually set the quotas at some point then, and do you  really need them? By default there are no size limits (apart from the  size of your disk partitions, of course).

What comes to fstab modification, it seems like you have just copied and  pasted the code from the website? That's not going to work, you have to  use the partitions that actually exist on *your* system. "hda2" is  and old way of pointing to second partition of first hard drive, these  days the correct device name would be "sda2", although you should be  using UUID instead (like all the default entries in fstab do). Also  Ubuntu has used Ext4 as the default file system for quite a while now,  and of course unless you actually have a separate /home partition you  can't edit the settings for one...

Coould you describe the error you are getting (while trying to create  the virtual machine) in a bit more detail, and where are you trying to  create it? If you tr to create one on a partiton or external drive  formatted as FAT you'll have max fiel size limit of 4GB as FAT  filesystem doesn't support larger files than that. If youare insetad  tryign to create it on your Linux partiton please post the output of "*sudo fdisk -l*" and contents of your fstab file so we can take a better look at what's gong 				[/INDENT] 			
  			   		
 			 				 			 			 			 		
 	

--------------------------------------------
My post in response:

desktop@ubuntu:~$ sudo fdisk -l
[sudo] password for desktop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 byte

   Device Boot      Start         End          Blocks           Id  System
/dev/sda1   *        2048      206847      102400            7  HPFS/NTFS/exFAT
/dev/sda2          206848   976771071   488282112        7  HPFS/NTFS/exFAT


The error I get when I'm installing VMware is:
[COLOR=#000000]"The current amount of free space on the hard disk  (1.1 GB) is not enough to create the specified disk file. Please choose  a different location or specify a smaller disk size." (in a pop-up  window)[/COLOR].

Sorry for not getting back to you sooner.

---

### Post by psyclone on 2013-11-13
Thanks, I've solved the problem.

---

### Post by Bucky Ball on 2013-11-13
***Threads merged.***

psyclone, I find it totally bizarre that you decided to start a new thread to respond to mcduck. Please stick to the one thread and address the issue here. What you did creates complete confusion and mcduck may never have seen the other thread or the fact that your problem is solved. Common courtesy, please.

Also, share with the community how you solved your issue rather than just telling us you've fixed it. That helps no-one.

Please mark this thread as solved from thread tools.

---

