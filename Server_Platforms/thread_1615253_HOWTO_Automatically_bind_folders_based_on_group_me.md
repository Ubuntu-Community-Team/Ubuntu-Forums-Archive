---
title: "HOWTO: Automatically bind folders based on group membership"
date: 2010-11-06
forum: Server Platforms
---

### Post by krippa on 2010-11-06
The most probable use case for this is if you have a server where you have your users chrooted to a directory and want them to be able to access other directories outside that folder. You could do this by binding the folders through fstab entries, however, that quickly becomes hard to manage and is not very dynamic. This howto focuses on this particular case but can also be applied to other situations.

What I wanted to do was give enable users a safe way to transfer files without giving them access to the whole file system. After some looking around sftp with chrooting seemed like the way to go. I set up the ssh daemon to support ldap, only allow ssh access to groups "sftp" and "admin" and to chroot users of group admin to /chroot/<user_name>.

Here is an extract of my /etc/ssh/sshd_config file:
```

Subsystem sftp internal-sftp

usePAM yes

AllowGroups sftp admin

Match Group sftp
	ChrootDirectory /chroot/%u
        ForceCommand internal-sftp
        X11Forwarding no
        AllowTcpForwarding no 

Match Group admin
	X11Forwarding yes
	AllowTcpForwarding yes

```

I had some trouble with this initially and had to use /chroot/ instead of /home/ which will probably work well for most people.

The next problem I had was how to share folders between the different users, enabling different kinds of admin, collaboration and access to data. Basically I wanted my users to have access to different folders with different permissions based on which groups they were part of so that I wouldn't have to bind all of them in fstab which was the solution I found while searching the web. Since I found nothing better I decided to write a script that would:

[LIST=1]
[*]Find all groups and their respective users on the system
[*]For each group, go through a file of binding-data and identify what folders to bind where
[*]Bind folders relative to users' chroot home
[/LIST]

Here is the resulting script that uses bindfs (you might need to install this) to achieve this.
```
#!/bin/sh
getent group | awk '
BEGIN 	{
	FS=":";
	chroot_dir="/chroot/";
	binding_dir="/root/chroot_bindings/";
} 
{ 
	#If  there are users in the group
	if ($4 != "") {

		#split the users into an array 
                split($4,users,",");
		
		#Read mappings from file with the same name as the group
                filename = binding_dir $1;
		print filename;
		while ((getline line < filename) > 0) {
			
			#Get the binding data from each line
        	    	split(line, mapping, ":");

			#Go through all users
			for (i in users ) {
				args = mapping[1];
				to_bind = mapping[2];
				target = chroot_dir users[i] "/" mapping[3];
					
				#Make sure target dir exists
				system("mkdir -p " target);
			    	command = "bindfs " args " " to_bind " " target;
				print strftime("%c") "\t" command;
				system(command);
			}
	        }
		close($1); 
	}
}

END   	{ 
	print " - DONE -" 
} 
' | tee /var/log/chroot_binder.log

```

Save the script to where you want it and make sure it's executable. If you look at what's in the script you probably noticed two parameters in the beginning that you might customize to fit your needs. 

First, chroot_dir is the root directory of where your users are chrooted to. The script assumes each user is chrooted to a folder with the name of the user in this dir. E.g. /chroot/user1/.

The second parameter specifies where the binding files are located. You should specifiy a directory where you will create binding files with the name of the group. The binding file syntax is as follows: each line has one binding. One binding consists of three parts; arguments to bindfs, dir to bind and the location to bind it to relative to the users chroot jail. The parts are separated by colon. Here is an example file that would give all members of the sftp group access read only acess to a folder called pub_files.

```
-p ug=rD:/media/pub_files:pub_files
```

If not altering the root folder of bindings, this should be saved in a file called "/root/chroot_bindings/sftp" because the script will search for this file when it finds the group "sftp" in the output from ```
getent group
```.

This binding will bind the /media/pub_files to all users who are a member of the sftp group. E.g. /chroot/user1/pub_files.

That's it for now. I might add some more binding examples later on as I refine them.

---

