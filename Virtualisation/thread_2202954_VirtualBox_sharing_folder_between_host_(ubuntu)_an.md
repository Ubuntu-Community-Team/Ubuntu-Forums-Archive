---
title: "VirtualBox sharing folder between host (ubuntu) and guest (redhat) machine"
date: 2014-02-01
forum: Virtualisation
---

### Post by virus7 on 2014-02-01
I am using Ubuntu 12.04 as my host machine  and trying to share a folder with my guest machine which runs Redhat  Enterprise Linux 5.

I have already installed VirtualBox Additions. Now when I try to run my following command :
```

# mount -t vboxsf install /mnt/shareFolder
```

it keeps showing me the error of 
```

/sbin/mount.vboxsf: mounting failed with the error: No such device
```

I have been searching on net but most of the solutions are for guest  machines as ubuntu not redhat (I was thinking it wount cause a problem  but i tried the solution of ubuntu it didnt work)

Thanks in advance.

 		 	 		 		 		 		 		 		[HR][/HR] 		[TABLE="width: 100%"]
 		  [TR]
 			[TD] 								 			
[/TD]
 			[TD] 				[RIGHT] 					 					 						[[IMG]http://images.devshed.com/fds/buttons/edit.gif[/IMG]]("http://forums.devshed.com/editpost.php?do=editpost&p=2922953")[/RIGHT]
[/TD]
[/TR]
[/TABLE]

---

### Post by SeijiSensei on 2014-02-01
I highly doubt that "install" is the appropriate device name.

I've never had to mount a shared folder.  I just use the "Shared Folder" item in the VB GUI.  Select a VM, then choose "Settings." You'll see the Shared Folder item on the left.

---

