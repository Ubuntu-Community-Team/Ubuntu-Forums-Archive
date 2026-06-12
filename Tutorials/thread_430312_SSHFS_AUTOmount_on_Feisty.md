---
title: "SSHFS AUTOmount on Feisty"
date: 2007-05-02
forum: Tutorials
---

### Post by Darwin Award Winner on 2007-05-02
HOWTO: Automount sshfs filesystems as soon as the network becomes available.
Ubuntu Version: Feisty or later


[COLOR="Red"]If you are looking for a way to easily do remote backups or any other sort of mass network transfer, you have come to the *wrong* place. Sshfs is nice, but it tends to be unreliable under heavy load. You would be much better off looking into rsync or Unison, for example.[/COLOR]

Update: New Features!
[LIST]
[*]Asynchronous mounting
All sshfs mounts will be mounted at the same time, rather than waiting for each one to finish mounting before starting the next.
[*]Works better when run as user
Only attempts to mount your own shares.
[*]Specify username rather than uid number
e.g. uid=yourname. The script now handles both correctly.
[/LIST]

This isn't just a howto on writing fstab lines for sshfs shares. That's part of it, yes, but the idea here is that you want you be able to walk into a cafe somewhere, start up your laptop, connect to the nearest wireless network, and immediately have your sshfs shares available without having to do anything extra beyond connecting to the network.

This howto looks long, but it really isn't; I'm just providing lots of background information for those that are interested, and for those that are not very familiar with fstab entries. A lot of this howto is a crash course in the salient points of fstab entries. If you already know these, you can skip down to the good stuff in step 3.

REQUIREMENTS: 
Feisty Fawn! (or later) The versions of fuse in Edgy and earlier releases are incapable of handling sshfs lines in [FONT="System"]/etc/fstab[/FONT] If you don't want to upgrade to Feisty, another possible solution might be to install the fuse packages provided [here]("http://www.debuntu.org/2006/04/27/39-mounting-a-fuse-filesystem-form-etcfstab"). Your mileage may vary.

Next requirement: Sshfs. Sshfs is the tool used to mount any remote folder that you can access via ssh as a filesystem. To install it, ```
sudo apt-get install sshfs
``` That should also install any other dependencies, including Fuse, if they aren't already installed.

Finally, and very importantly, you must have set up PASSWORDLESS login to the ssh host that you wish to mount. For details on how to set this up, go [here]("http://www.debian-administration.org/articles/152"). A non-automatic variation of this howto is possible without passowrdless logins.

Also, you should already know how to mount your sshfs shares manually. There are plenty of howto's for this on these forums and elsewhere.

PROCEDURE:
Before you can *auto*mount your shares, you first have to *mount* them, and you have top set them up in your [FONT="System"]/etc/fstab[/FONT] so that they can be mounted with a simple command. So, 

STEP 1: Setting up fstab and fuse.conf.
My source for this section is [this page]("http://www.debuntu.org/2006/04/27/39-mounting-a-fuse-filesystem-form-etcfstab") (the same one mentioned above). [FONT="System"]/etc/fstab[/FONT] is a critical system file, so naturally you will need administrator privileges to edit it: ```
gksu gedit /etc/fstab
``` A typical sshfs fstab entry ready for automounting looks something like this:
```
# <file system>       <mount point>         <type>  <options>
sshfs#myname@www.myhome.com:/home/myname    /mnt/sshfs/homebox    fuse    comment=sshfs,noauto,users,exec,uid=1000,gid=1000,allow_other,reconnect,transform_symlinks,BatchMode=yes 0 0
```

If you're familiar with fstab entries, the only thing that should look new is the filesystem specification at the beginning of the line. If you're new at this, I'll provide a quick explanation. The first part determines the sshfs share. The syntax is the same as when you are using sshfs on the command line, except that it is prefixed by "sshfs#" to tell the mount program what kind of filesystem this is.  (By the way,This kind of syntax probably works for other fuse filesystems as well, but I haven't tried it.) Also, make sure to put your username in, or else the system will not know which user to log in to the remote host as.

The next part is the mount point. Again, you can simply use the same folder that you always use when you mount the share manually. The next part tells mount that this is a Fuse filesystem.

The options are also the same options you use when you mount the share manually, with a few additions: [LIST]
[*][FONT="System"]comment=sshfs[/FONT]
This option is just what it says: a comment. We'll see later how the automount script uses this.
[*][FONT="System"]users[/FONT]
This option allows anyone to mount this filesystem. Without this, you could only mount the filesystem using sudo. Allowing normal users to mount the share isn't strictly necessary for automatic operation, but it allows you to easily remount the share manually if something goes wrong during the automatic mount. (If you know how to edit the sudoers file, feel free to do that instead of using the "users" option; if you don't know what the sudoers file is, don't worry about it - The "users" option is good enough.)
[*][FONT="System"]uid[/FONT] and [FONT="System"]gid[/FONT]
These two options are required because when the sshfs share is automounted, it won't be *you* running the mount program; it will be the *system*, and the system needs to know who the share belongs to. To find out your uid and gid, simply open a terminal and run "[FONT="System"]id[/FONT]". Use the numbers that it tells you, not the numbers given in the example above.
[FONT="System"]noauto[/FONT]
This tells the system not to mount the filesystem when it first boots. (because the network isn't up yet!)
[*][FONT="System"]BatchMode=yes[/FONT]
This tells the sshfs process not to try asking for a password, because the automount script certainly isn't going to provide one. With this option, if you don't have passwordless logins working correctly, you'll know immediately; you won't have to waste time cancelling a password prompt.
Secondly, this option tells ssh not to allow idle timeouts. Without this, your sshfs mounts will unmount if you don't touch them for a while.
[/LIST]

Next, you should put the following in /etc/fuse.conf (create the file if it doesn't exist):
```
user_allow_other
```

STEP 2: Testing Your Fstab entries
(If you already know how to do this, then go ahead and do it, then skip to step 3.)
To see if your fstab entry works, open up a terminal and try to mount it like this (I will continue with the example above):
```
mount /mnt/sshfs/homebox
```
Then see if your sshfs share has been successfully mounted, for example, by:
```
ls /mnt/sshfs/homebox
```
If you see the contents of your remote share, then you're good to go.

At this point, if you have not set up passwordless ssh logins, then mounting will still work, but you will have to provide your password on each mounting, and step 3 will not work for you.

STEP 3: *Auto*mounting your shares when you connect to the internet
Ok, now that your computer knows *how* to mount your shares, it's time to tell it *when* to mount them. Also, just as importantly, you need to tell your compute when to *unmount* them as well, because if you lose your network connection and forget to unmount the shares, any program that tries to access them will freeze indefinitely and will need to be killed.

Accomplishing both of these is actually quite easy. You should have a pair of directories called [FONT="System"]/etc/network/if-up.d[/FONT] and [FONT="System"]/etc/network/if-down.d[/FONT]. Scripts in the first directory will be executed when the computer connects to the network, and scripts in the second one will be executes when it disconnects. Again, editing files in these directories requires administrator privileges. Create the following two files:
[FONT="System"]/etc/network/if-up.d/mountsshfs[/FONT]
```
#!/bin/sh

## http://ubuntuforums.org/showthread.php?t=430312
## The script will attempt to mount any fstab entry with an option
## "...,comment=$SELECTED_STRING,..."
## Use this to select specific sshfs mounts rather than all of them.
SELECTED_STRING="sshfs"

# Not for loopback
[ "$IFACE" != "lo" ] || exit 0

## define a number of useful functions

## returns true if input contains nothing but the digits 0-9, false otherwise
## so realy, more like isa_positive_integer 
isa_number () {
    ! echo $1 | egrep -q '[^0-9]'
    return $?
}

## returns true if the given uid or username is that of the current user
am_i () {
	[ "$1" = "`id -u`" ] || [ "$1" = "`id -un`" ]
}

## takes a username or uid and finds it in /etc/passwd
## echoes the name and returns true on success
## echoes nothing and returns false on failure 
user_from_uid () {
    if isa_number "$1"
    then
		# look for the corresponding name in /etc/passwd
    	local IFS=":"
    	while read name x uid the_rest
    	do
        	if [ "$1" = "$uid" ]
			then 
				echo "$name"
				return 0
			fi
    	done </etc/passwd
    else
    	# look for the username in /etc/passwd
    	if grep -q "^${1}:" /etc/passwd
    	then
    		echo "$1"
    		return 0
    	fi
    fi
    # if nothing was found, return false
   	return 1
}

## Parses a string of comma-separated fstab options and finds out the 
## username/uid assigned within them. 
## echoes the found username/uid and returns true if found
## echoes "root" and returns false if none found
uid_from_fs_opts () {
	local uid=`echo $1 | egrep -o 'uid=[^,]+'`
	if [ -z "$uid" ]; then
		# no uid was specified, so default is root
		echo "root"
		return 1
	else
		# delete the "uid=" at the beginning
		uid_length=`expr length $uid - 3`
		uid=`expr substr $uid 5 $uid_length`
		echo $uid
		return 0
	fi
}

# unmount all shares first
sh "/etc/network/if-down.d/umountsshfs"

while read fs mp type opts dump pass extra
do
    # check validity of line
    if [ -z "$pass" -o -n "$extra" -o "`expr substr ${fs}x 1 1`" = "#" ]; 
    then
        # line is invalid or a comment, so skip it
        continue
    
    # check if the line is a selected line
    elif echo $opts | grep -q "comment=$SELECTED_STRING"; then
    	
    	# get the uid of the mount
        mp_uid=`uid_from_fs_opts $opts`
        
        if am_i "$mp_uid"; then
			# current user owns the mount, so mount it normally
			{ sh -c "mount $mp" && 
				echo "$mp mounted as current user (`id -un`)" || 
				echo "$mp failed to mount as current user (`id -un`)"; 
			} &
		elif am_i root; then
			# running as root, so sudo mount as user
			if isa_number "$mp_uid"; then
				# sudo wants a "#" sign icon front of a numeric uid
				mp_uid="#$mp_uid"
			fi 
			{ sudo -u "$mp_uid" sh -c "mount $mp" && 
				echo "$mp mounted as $mp_uid" || 
				echo "$mp failed to mount as $mp_uid"; 
			} &
		else
			# otherwise, don't try to mount another user's mount point
			echo "Not attempting to mount $mp as other user $mp_uid"
		fi
    fi
    # if not an sshfs line, do nothing
done </etc/fstab

wait
```

[FONT="System"]/etc/network/if-down.d/umountsshfs[/FONT]
```
#!/bin/bash

# Not for loopback!
[ "$IFACE" != "lo" ] || exit 0

# comment this for testing
exec 1>/dev/null # squelch output for non-interactive

# umount all sshfs mounts
mounted=`grep 'fuse.sshfs\|sshfs#' /etc/mtab | awk '{ print $2 }'`
[ -n "$mounted" ] && { for mount in $mounted; do umount -l $mount; done; }
```

Now make both files executable and owned by root:
```
sudo chmod 755 /etc/network/if-up.d/mountsshfs /etc/network/if-down.d/umountsshfs
sudo chown root:root /etc/network/if-up.d/mountsshfs /etc/network/if-down.d/umountsshfs
```

That should be it! If your shares are configured as above, they should now automatically mount and unmount with your network. Try disconnecting and reconnecting. 

ADDITIONAL COMMENTS:
As an added bonus, since these shares are in fstab, GNOME will automatically create desktop icons for them when they are mounted, so you will have easy access to them.

Those more familiar with [FONT="System"]mount[/FONT] might point out that the -a option could be used in these scripts instead of loops and grep, awk, etc. Indeed, my first implementation used this. However, the current form of the scripts allows them to be executed successfully by any user.

By the way, remember that comment option? Well, that's how the mounting script knows which filesystems to mount.

The mounting script can also be run manually at any time to *remount* your shares. There is no need to use sudo. When run as a user, the script will only remount *your* shares.

When, your computer boots, it may complain that the fstab lines that you entered are invalid, but nothing should go wrong.

And lastly, like most of the open source/free software world, this guide comes with no warranty.

[COLOR="Red"]UPDATE[/COLOR]

In Hardy Heron and above, there is a bug in sshfs that prevents non-root unmounting of sshfs. There is a workaround described in [https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/243298](https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/243298) that makes things work for now. You can try the following perl one-liner to automatically apply the workaround to your fstab, but I only guarantee that it worked for me:

```
sudo perl -lape 's/(sshfs#\S+)(\s+\S+\s+\S+\s+)(.*)/\1\2fsname=\1,\3/' -i /etc/fstab
```

Thanks to conchyliferous for bringing this to my attention.

---

### Post by wildlifer on 2007-05-04
Thanks. I use Xubuntu and I now have an easy way to access ssh shares (thunar does not have native ssh browsing support).

---

### Post by Barleyman on 2007-05-11
How do you do this on an alternate port?

---

### Post by Darwin Award Winner on 2007-05-11
> **Barleyman said:**
> How do you do this on an alternate port?

```
$ sshfs -h 2>&1 | grep -i port
    -p PORT                equivalent to '-o port=PORT'
    -o directport=PORT     directly connect to PORT bypassing ssh
```

So you'll have to add "port=22" or whatever port you want to the filesystem options in /etc/fstab. There's also an way to pass options to ssh. You could specify the port or any number of other things that way.

---

### Post by ernstblaauw on 2007-05-14
My entry in fstab looks like this:
```
sshfs#xxxxxx@rattler.few.vu.nl:/home/xxxxxx/	/media/VU	fuse	comment=sshfs,users,noauto,uid=1000,gid=1000,allow_other,reconnect,transform_symlinks	0	0
```

As I have a password login, I'm not going to auto mount. However, when I type sudo mount /media/VU, I get the following error:
```
/sbin/mount.fuse: 23: function: not found
-e mount.fuse# sshfs#xxxxxx@rattler.few.vu.nl:/home/xxxxxx/
exit: 26: Illegal number: /media/VU
```

What's going wrong?

**Update**
I installed FUSE 2.6.5, and now I get this output:
```
[: 54: ==: unexpected operator
[: 54: ==: unexpected operator
[: 54: ==: unexpected operator
[: 54: ==: unexpected operator
[: 54: ==: unexpected operator
[: 54: ==: unexpected operator
[: 54: ==: unexpected operator
[: 54: ==: unexpected operator
[: 54: ==: unexpected operator
[: 54: ==: unexpected operator
[: 54: ==: unexpected operator
[: 54: ==: unexpected operator
Password:
fuse: unknown option `IGNORE'
```
(By 'Password:' I entered my password)

The share is not mounted

---

### Post by Darwin Award Winner on 2007-05-14
Fuse 2.6.5? The latest version of Fuse in Feisty (i.e. the one that I am using) is 2.6.3. I don't know if something might have changed between those two versions. Anyway, you can try the following:
[LIST]
[*]Try mounting without sudo. The 'users' option should make this unnecessary, and this could be a possible problem, though I doubt it.
[*]Make sure you can log in via ssh. Again, probably not the problem, but you should make sure.
[*]Make sure you can mount your remote directory using sshfs directly.
[*]Make sure the mount directory already exists. I think Ubuntu might have some way of cleaning out the /media directory. That's why I showed my example in /mnt.
[/LIST]
Please try those and let me know what happens. If you solve your problem, I'd like to be able to update my guide.

---

### Post by Barleyman on 2007-05-14
> **Darwin Award Winner said:**
> ```
$ sshfs -h 2>&1 | grep -i port
    -p PORT                equivalent to '-o port=PORT'
    -o directport=PORT     directly connect to PORT bypassing ssh
```

So you'll have to add "port=22" or whatever port you want to the filesystem options in /etc/fstab. There's also an way to pass options to ssh. You could specify the port or any number of other things that way.

Sorry, I should have explained my problem a little better.  I was aware of how to switch the port using the -p option.  This currently works fine for my little shell script I launch to mount the drive.  But I couldn't seem to find the correct sytax to make it work via fstab.  

your pointer to filesytem options gave me a clue, so I decided to read through the documentation of fstab and found the solution that works for me.  

```
sshfs#me@remoteserver:/remote/folder/ /media/myserver fuse port=123,noauto,user 0 0
```

Thanks again.```

```

---

### Post by ernstblaauw on 2007-05-15
> **Darwin Award Winner said:**
> Fuse 2.6.5? The latest version of Fuse in Feisty (i.e. the one that I am using) is 2.6.3. I don't know if something might have changed between those two versions. Anyway, you can try the following:
[LIST]
[*]Try mounting without sudo. The 'users' option should make this unnecessary, and this could be a possible problem, though I doubt it.
[*]Make sure you can log in via ssh. Again, probably not the problem, but you should make sure.
[*]Make sure you can mount your remote directory using sshfs directly.
[*]Make sure the mount directory already exists. I think Ubuntu might have some way of cleaning out the /media directory. That's why I showed my example in /mnt.
[/LIST]
Please try those and let me know what happens. If you solve your problem, I'd like to be able to update my guide.
[LIST]
[*]Mounting without sudo doesn't work.
[*]I can log in via ssh
[/list]
Then, I reinstalled FUSE and sshfs by going to synaptic and marking them for reinstallation. Then, I used another mounting point. I had to add 'user_allow_other' to fuse.conf (this was a message when I tried to mount). And guess what.. it works now :-). 

I got another question: I really need a password to log in. Is it possible to store it somewhere and then use it to automatically log in?

---

### Post by prankst3r on 2007-05-18
For those of you asking about being able to mount sshfs without a password, you can setup a trust relationship between your local and remote machines as follows:

Make sure you are logged in as the user you want to set up the trust relationship. Then go to your home directory on your client machine:

```
cd $HOME
```

Then generate a public/private rsa key pair:

```
 ssh-keygen -t rsa
```

Leave all the fields as default (just press enter). Do not enter a passphrase unless you want to enter that everytime you establish an ssh/sshfs connection (which I assume you don't since we wanted to eliminate a password/passphrase prompt to begin with).

Now go ahead and enter your .ssh directory:

```
cd $HOME/.ssh
```

Establish an sftp connection to the _server box_:

```
sftp <login>@<server_name>:/home/<login>/.ssh
```
```
put id_rsa.pub
```

*Note <login> refers to the server login you want to establish the trust relationship with.

Then quit sftp and ssh to the server box from your client box:
```
ssh <login>@<server_name>:/home/<login>/.ssh
```

Now you will need to append your client's public key to the authorized keys as follows:
```
cat id_rsa.pub >> authorized_keys
```

Next make sure permissions on authorized_keys are 600:
```
chmod 600 authorized_keys
```

And thats it - you now have a trust relationship setup between the client login you setup the rsa key and the server login whose authorized key list you added the client's public key to.

Go ahead and test out an ssh or sftp connection from your client box to make sure it is working:
```
ssh <login>@<server_name>
```

I certainly don't claim to be any sort of Linux guru, so feel free to point out anything that could be done better - as far as I know you can't automate this with a passphrase when generating the rsa key, but I could be wrong. Cheers.

---

### Post by lindsay_keir on 2007-06-18
[COLOR="Red"]**Passwordless Logons**[/COLOR]
Here's a simpler method
[FONT="Courier New"]
# Create a public key-pair for whichever user you are using on the local PC
ssh-keygen -t rsa           
 # Give the user's public key to admin1@myServer                   
ssh-copy-id -i .ssh/id_rsa.pub admin1@myServer  
# ... admin1@myserver's password:XXXXXX         # You must know admin1's password
# The user can now automatically connect as admin1
ssh admin1@myServer                             @myserver[/FONT]
This saves all that copying, etc. 

I did the same for the local PC's root account
[FONT="Courier New"]# Switch to the root account
su -[/FONT]

I got this from Item 6 at [http://www.venturecake.com/10-linux-shell-tricks-you-dont-already-know-for-once/]("http://www.venturecake.com/10-linux-shell-tricks-you-dont-already-know-for-once/")

Thanks to both of you - I spent hours screwing this up and never did get it to work until now.

---

### Post by LuckyProphet on 2007-06-19
Hi,

I am trying to do this for all my users that are able to connect from different workstations to the server.

First I assumed that I should use the root user as a user name, but than it only works for the root user and not for any other user.

How can I have this done for all users without adding one for each user to fstab?

Cheeers
... LuckyProphet

---

### Post by lindsay_keir on 2007-06-19
[LIST]
[*]Allow each PC's root to do the passwordless logon to the myServer PC
[/LIST]
[LIST]
[*]Create - adjust - install this batch file. I used Webmin Boot commands panel to create and install the base batch file - sorry, I am not versatile in boot  sequences, etc. Webmin picked the spot. Then I modified it to create the inside.
[/LIST]
```
#!/bin/sh
# Mount shares controlled by FUSE
case "$1" in
'start')
    `fusermount -u -z /myGlobal`
    `sshfs admin1@myServer:/myGlobal /myGlobal -o allow_other -o nonempty`
    if [ ! -e /myGlobal/automountFUSE_OK ]
    then
      `sshfs admin1@my.remote.net:/myGlobal /myGlobal -p 1022 -o allow_other -o nonempty`
    fi
    ;;
'stop')
    `fusermount -u -z /myGlobal`
    ;;
*)
    echo "Usage: $0 { start | stop }"
    ;;
esac
exit 0

```
[LIST]
[*]***[COLOR="Red"]Don't forget to create the file /myGlobal/automountFUSE_OK  on myServer[/COLOR]***[/LIST]

**In my case ...**
[LIST]
[*]Every PC has a (sudo root) admin1 account
[/LIST]
[LIST]
[*]Every PC has a /myGlobal mountpoint (directory) used to auto-mount the /myGlobal directory residing on myServer
[/LIST]
[LIST]
[*]The back-tick is required on the web connection's sshfs command - I back-ticked all of them just because.
[/LIST]
[LIST]
[*]My router deflects the incoming port (-p 1022) to myServer's ssh port 22 (I have ports 1122, 1222, etc. pointing to other PCs). Hopefully, if myServer isn't on the LAN, I'll find it on the web.
[/LIST]
[LIST]
[*]No timeout is used - why would I? sshfs will timeout by itself. Likewise, no error logs, etc. Again, why?
[/LIST]
[LIST]
[*]No - you do not need shares defined - no Samba, no NTFS
[/LIST]

---

### Post by monkeyking on 2007-07-13
I'm having some problems using the automount feature.
that is, problems with
```

/etc/network/if-up.d/mountsshfs

```

I've got a user on the system and this user has copyed the ssh-key stuff to the server,
so this user is able to run sshfs by commandline, without entering password.

And if this user manually runs
```

/etc/network/if-up.d/mountsshfs

```
It will work.

But if the user running the script is root(as it is when run by the system),
the sshfs will not work and the system ask for the password.

Any ideas?

thanks in advance

---

### Post by Darwin Award Winner on 2007-07-22
Actually, I have the same problem. The only reason it worked initially is because I foolishly had the same ssh keys in my home and in the root directory. However, I have modified my script to work whether called by a user or by root. Furthermore, when invoked by a user, it will only attempt to mount that user's own mount points. I'll edit my first post accordingly.

---

### Post by buntunub on 2007-07-23
I keep getting this error whenever I try to automount:

[mntent]: line 19 in /etc/fstab is bad
mount: can't find /home/username/Desktop/sshfs projects in /etc/fstab or /etc/mtab

I can and regularly do sshfs to this exact folder which I created for that purpose, so whats the deal? I followed your guide quite closely so im wondering what I could have done wrong. Heres my fstab entry:

# fuse mounts
sshfs# username@fileserver:/path/to/file/  /home/username/Desktop/sshfs\ projects/    fuse    comment=sshfs,users,noauto,uid=1000,gid=1000,allow_other,reconnect,transform_symlinks 0 0

Names and IP's are changed as needed here obviously. Anyway, what gives?

Edit: Ok so im a moron :(

I had a space after the sshfs# and some spaces in the paths. Anyway, fixed that in fstab and all is well :)

Great guid btw and thanks a ton!

---

### Post by Darwin Award Winner on 2007-07-23
I have to make several updates and fixes to my guide, but for those who are waiting, here is the updated script that should work whether it is run as root or as a normal user, with the important caveat that in order to run as root, you must give each fstab entry an owner with the option uid=yourusername. For fstab entries without this option, this script will function identically to the previous one.

Also, this is exactly the script I am using. I have not yet attempted to make the comments intelligible to anyone but myself. That's one thing I intend to do before adding this script to my guide.

```
#!/bin/sh

isa_number () {
    ! echo $1 | egrep -q '[^0-9]'
    return $?
}

user_from_uid () {
    # we need a number
    if ! isa_number $1
    then
        return 1
    fi
    
    local IFS=":"
    while read name x uid the_rest
    do
        if [ "$1" -eq "$uid" ]
        then 
            echo "$name"
            return 0
        fi
    done </etc/passwd
    return 1
}


# Not for loopback
[ "$IFACE" != "lo" ] || exit 0

# comment this for testing
exec &>/dev/null # squelch output for non-interactive

# unmount them first
mounted=`grep 'sshfs#' /etc/mtab | awk '{ print $2 }'`
[ -n "$mounted" ] && umount -l $mounted

while read fs mp type opts dump pass extra
do
    # check validity of line
    if [ "`expr substr ${fs}x 1 1`" = "#" -o -z "$pass" -o -n "$extra" ]; then
        # line is a invalid or a comment
        continue
    # check if the line is an sshfs line
    elif echo $opts | grep -q 'comment=sshfs'; then
        #find out the user 
        mp_uid=`echo $opts | egrep -o 'uid=\w+'` # "mp" stands for mount point
        if [ -z "$mp_uid" ]; then
            # no uid was specified, so just try to mount as the current user
            mount $mp
        else
            mp_uid_length=`expr length $mp_uid - 3`
            mp_uid=`expr substr $mp_uid 5 $mp_uid_length` # delete the "uid="
            # mp_uid now contains either a username or a uid
            # convert to username if possible; otherwise assume that it already is one
            if ! mp_user=`user_from_uid $mp_uid`; then
                mp_user=$mp_uid
            fi             
            # mp_user is either a username or an invalid uid; either way is ok
            if [ "$mp_user" = "`whoami`" ]; then
                # current user owns the mount, so mount normally
                mount $mp
            elif [ "`whoami`" = "root" ]; then
                # running as root, so su to user and mount
                su $mp_user -c "mount $mp"
            fi
            # otherwise, don't try to mount another user's mount point
        fi
    fi
    # if not an sshfs line, do nothing
done </etc/fstab

```

---

### Post by monkeyking on 2007-07-24
Thanks your updated script fixed my problem

---

### Post by yzf600 on 2007-08-08
> I'd like to point out that RSA keys mean SSH protocol 1, which is less secure than DSA keys//SSH protocol 2.  Just use these steps to get SSH to use protocol 2:

Actually my original post is wrong. SSH protocol can use RSA or DSA keys. There is apparently not much difference between the keys. 

Thanks for howto on sshfs. It helped me out immensely.

---

### Post by mkramer on 2007-09-12
Thanks.  This is great.  You read my mind with this tute.  However, there is one niggle.  Everything works great except that it doesn't mount on a reboot.  It mounts if I run /etc/init.d/networking restart.  It mounts if I run /etc/network/if-up.d/mountsshfs as a user.  But it does not mount on reboot.  What could be the problem here?

PS thanks to #6 for the neat command ssh-copy-id

I added this script to /etc/rc.local and it now mounts on boot.

---

### Post by Darwin Award Winner on 2007-10-04
Good news. I have updated the first post with a significantly updated scripts. Check the update for the new features. 

LuckyProphet, sshfs is not really designed for that sort of thing. This setup is more amenable to a single user who wants to connect to many ssh servers. You want the opposite: many clients connecting to one server. Your problem is better solved with traditional network filesystems, like NFS or samba.

---

### Post by christian.paratschek on 2007-10-29
This does not work for me (Gutsy on the client, Etch on the server). I have successfully exported the ssh key. So passwordless ssh into my remote box works.

As long as I keep "BatchMode=Yes" OUT of my fstab entry, I can mount the remote folder as expected: manually, as user with a simple "mount /mountpoint" command.

When I put "BatchMode=Yes" into the fstab-entry, I can no longer mount the server manually, I get a  "read: Connection reset by peer"-error. Of course automounting also doesn't work.

Regards,
Christian

---

### Post by Darwin Award Winner on 2007-10-29
Oops, ssh options are case sensitive. The "yes" should be all lower case. I've fixed that in my howto.

---

### Post by christian.paratschek on 2007-10-29
OK, this problem is solved. Mounting the server manually works now even with "BatchMode=yes" in the fstab-line. I can happily mount/unmount with "mount /mnt/point" and "umount /mnt/point" - as non-root user.

But... Automounting still does not work! 

If I execute /etc/network/if-up.d/mountsshfs from a terminal (sudo or as normal user), nothing happens. Permissions are set, file is executable: 

-rwxr-xr-x 1 root root 3018 2007-10-29 22:14 mountsshfs

Note: only my non-root user has ssh-keys stored on the server. Root would need a password to ssh into the server. But I didn't set that intentionally, because I thought it is enough to have a normal user have passwordless login. Am I correct? 

Regards,
Christian

---

### Post by christian.paratschek on 2007-10-30
I've found a nice addition to your fstab-entry.

If you plan zu use rsync to sync files from your local machine to your ssh-server, you need "workaround=rename"

Otherwise, you will not be able to update an older version of a file with a newer one. Without this option, you will be able to create files and folders and delete them, but you will get an error like this, if you try to update a file:

rsync: rename "/home/christian/Server/xxx/yyy/.index.html.Q3Btvn" -> "xxx/yyy/index.html": Operation not permitted (1)

---

### Post by christian.paratschek on 2007-10-31
It works now, thank you!

---

### Post by christian.paratschek on 2007-10-31
Another edit: the scripts work flawlessly from outside: if I use my external IP and connect from somewhere to my homeserver, everything works as intended.

It does, however, NOT work for me if I substitute the external IP address with the internal one and try to connect from within my LAN.

That's why I didn't get it to work in the beginning: I always tried from within my LAN. Today I tried from outside and suddenly everything worked.

This is strange because it doesn't make sense to me: I can ssh into the machine with user@external-ip from outside, I can connect with user@local-ip from inside to my ssh. I can mount my share with sshfs from outside and from inside. 

Only the mountsshfs script does not work when I am on the LAN.

Please don't ask me why I need ssh within my LAN, hehe - it obviously makes no sense and I should just use smb/nfs instead. But I would like to know why the script does not work from within local network.

---

### Post by ieatkittens on 2007-11-02
I have the same issue...I can mount the sshfs at my office but from home I have no such luck...

I'd love to get sshfs working for both so that I only need the single automount regardless of where I'm connecting!

Also, in your tutorial the second automation script has the same filename as the first...I believe you want us to create if-down.d/umountsshfs in place of another if-up.d/mountsshfs

It just occured to me that I can't even manually mount the points from my fstab....but the first time I connected it worked perfectly!

---

### Post by Endolith on 2007-11-28
Is there an "easy way" to do this?

GNOME's "Connect to Server", for instance, lets you connect to a folder over SSH through a menu, and it's persistent through reboots, etc.  But you can't access the files in non-GNOME programs, it requires the keyring/dbus to remember the password (which doesn't work with ssh -X), and you can't mount the files inside other directories that I know of (so that Rhythmbox, etc can watch it).

SSHFS seems obviously superior.  But the line I used to mount my music folder from one computer inside the music folder of another computer is three lines long, and there's no auto-complete for remote names, it's very error prone, newbs really don't want to muck around with stuff like this in their fstab, etc.

---

### Post by Darwin Award Winner on 2007-11-28
Well, my method simpy involves a few scripts and entries in fstab. The scripts could easily be installed by a deb package, but as for the fstab entries, your questions reduces to one of whether there exist any reasonable GUIs for /etc/fstab. I don't know of any.

If only GNOME mounted its virtual filesystems somewhere in the real filesystem.

---

### Post by Endolith on 2007-11-28
> **Darwin Award Winner said:**
> Well, my method simpy involves a few scripts and entries in fstab.

Of course.  But its all added by hand and is still very error-prone.  And the automounting depends on whether your network is up, right?  Not necessarily on whether the other computer is online.  And.... it just seems like a one-off thing that would work well for one person, but that there should be a more... "fundamental" way to do all this.  I don't know.

> 
 The scripts could easily be installed by a deb package, but as for the fstab entries, your questions reduces to one of whether there exist any reasonable GUIs for /etc/fstab. I don't know of any.

It seems like it might be better in something completely different from fstab, like the way removable drives are automounted.  I don't *know* how removable drives are mounted (or I could fix mine :-)), but I know it's not controlled by fstab and sort of works smoothly in the background.  I just want to right-click something in Nautilus and say "mount an SSH folder here" and be done with it.  :-D

> If only GNOME mounted its virtual filesystems somewhere in the real filesystem.

Agreed 100%.  I heard somewhere that they were trying to improve GNOME VFS for situations like this, but I don't know the details.

---

### Post by cherry316316 on 2007-11-29
where can I find my ip address, I use the wireless network provided to me by my college.
when I do
“ifconfig”
I get
eth1 inet addr:10.XXX.XXX.XXX
and
lo inet addr:XXX.XXX.XXX.XXX

now from remote, when I try
ssh @10.XXX.XXX.XXX
its refuse to except my password.

also, from the other blog, i edited /etc/ssh/sshd_config file and I added line
AllowUsers

but its still not working. which IP address I am suppose to use.
also, when I open a website, which gives IP address, it shows my IP address as
127.XXX.XXX.XXX
which is different from 10.XXX.XXX.XXX which i get using “ifconfig”
Thanks

---

### Post by VstarAl on 2007-11-30
Thank you very much for the tutorial.  I'm running 7.10 (Gutsy Gibbon).  There is only one portion that does not work for me; the mountsshfs script.  Even if I run it manually, it does not mount my SSHFS share.  (The umountsshfs file runs fine.)  I can manually mount the SSHFS share using "mount /server/share", so my fstab entry seems to be working correctly.  

If I manually mount the SSHFS share, then run mountsshfs, the script appears to hit the line where it calls umountsshfs (because I see the icon to my share disappear from the desktop).

I tried both mountsshfs scripts that were posted, made the chmod/chown modifications, and neither one worked for me.

Thanks again!

---

### Post by Endolith on 2007-11-30
> **cherry316316 said:**
> where can I find my ip address, I use the wireless network provided to me by my college.
when I do
“ifconfig”
I get
eth1 inet addr:10.XXX.XXX.XXX
and
lo inet addr:XXX.XXX.XXX.XXX

now from remote, when I try
ssh @10.XXX.XXX.XXX
its refuse to except my password.

Are you trying to access it from inside a LAN or outside?  To see your IP from the outside world, go to whatismyip.com or something like that.  Then you will need to have the SSH port forwarded to your internal IP.

> also, from the other blog, i edited /etc/ssh/sshd_config file and I added line
AllowUsers

You added your username after that right?  You provide a list of usernames after that, and everyone not on the list is blocked.  I imagine if you don't list anyone, everyone is blocked.  :-)

---

### Post by christianco on 2008-01-15
hi, this is where I'm stuck too, in gutsy - you seem to have worked out the problem but there is no post inbetween to say how you did it! 

When I run mountsshfs as root or user, nothing happens, no error, no output. umountsshfs works great as does mount ... as user. seems to be something wrong with if-up.d/mountsshfs script maybe but I can't figure out what.


> **christian.paratschek said:**
> 
But... Automounting still does not work! 

If I execute /etc/network/if-up.d/mountsshfs from a terminal (sudo or as normal user), nothing happens. Permissions are set, file is executable: 

-rwxr-xr-x 1 root root 3018 2007-10-29 22:14 mountsshfs

Note: only my non-root user has ssh-keys stored on the server. Root would need a password to ssh into the server. But I didn't set that intentionally, because I thought it is enough to have a normal user have passwordless login. Am I correct? 

Regards,
Christian

---

### Post by TCopple on 2008-01-17
For Gutsy Users try this as your mountsshfs script.
```
#!/bin/bash 

## The script will attempt to mount any fstab entry with an option
## "...,comment=$SELECTED_STRING,..."
## Use this to select specific sshfs mounts rather than all of them.
SELECTED_STRING="sshfs"

# Not for loopback
[ "$IFACE" != "lo" ] || exit 0

## define a number of useful functions

## returns true if input contains nothing but the digits 0-9, false otherwise
## so realy, more like isa_positive_integer 
isa_number () {
    ! echo $1 | egrep -q '[^0-9]'
    return $?
}

## returns true if the given uid or username is that of the current user
am_i () {
	[ "$1" = "`id -u`" ] || [ "$1" = "`id -un`" ]
}

## takes a username or uid and finds it in /etc/passwd
## echoes the name and returns true on success
## echoes nothing and returns false on failure 
user_from_uid () {
    if isa_number "$1"
    then
		# look for the corresponding name in /etc/passwd
    	local IFS=":"
    	while read name x uid the_rest
    	do
        	if [ "$1" = "$uid" ]
			then 
				echo "$name"
				return 0
			fi
    	done </etc/passwd
    else
    	# look for the username in /etc/passwd
    	if grep -q "^${1}:" /etc/passwd
    	then
    		echo "$1"
    		return 0
    	fi
    fi
    # if nothing was found, return false
   	return 1
}

## Parses a string of comma-separated fstab options and finds out the 
## username/uid assigned within them. 
## echoes the found username/uid and returns true if found
## echoes "root" and returns false if none found
uid_from_fs_opts () {
	local uid=`echo $1 | egrep -o 'uid=[^,]+'`
	if [ -z "$uid" ]; then
		# no uid was specified, so default is root
		echo "root"
		return 1
	else
		# delete the "uid=" at the beginning
		uid_length=`expr length $uid - 3`
		uid=`expr substr $uid 5 $uid_length`
		echo $uid
		return 0
	fi
}

# unmount all shares first
bash "/etc/network/if-down.d/umountsshfs"

while read fs mp type opts dump pass extra
do
    
    # check if the line is a selected line
    if echo $opts | grep -q "comment=$SELECTED_STRING"; then
    	
    	# get the uid of the mount
        mp_uid=`uid_from_fs_opts $opts`
        
        if am_i "$mp_uid"; then
			# current user owns the mount, so mount it normally
			{ bash -c "mount $mp" && 
				echo "$mp mounted as current user (`id -un`)" || 
				echo "$mp failed to mount as current user (`id -un`)"; 
			} &
		elif am_i root; then
			# running as root, so sudo mount as user
			if isa_number "$mp_uid"; then
				# sudo wants a "#" sign icon front of a numeric uid
				mp_uid="#$mp_uid"
			fi 
			{ sudo -u "$mp_uid" bash -c "mount $mp" && 
				echo "$mp mounted as $mp_uid" || 
				echo "$mp failed to mount as $mp_uid"; 
			} &
		else
			# otherwise, don't try to mount another user's mount point
			echo "Not attempting to mount $mp as other user $mp_uid"
		fi
    fi
    # if not an sshfs line, do nothing
done </etc/fstab

wait
```

Major difference, changed all (sh)ell calls to (bash) calls and 
removed the first conditional statment in the while loop because the # in the sshfs#... fstab line was causing that line to not get evaluated.

Works now after a few hours of tinkering.  Thanks.

---

### Post by Darwin Award Winner on 2008-02-15
To the people for whom automounting works only from *outside* their lan:

The difference suggests to me that the issue may be with name resolution. I personally had to jump through some creative hoops to ensure that I could access my server using the same hostname regardless of whether I am on my lan or elsewhere. I am currently using the exact version of the script that appears on the front page of this thread, and it has served me well for months.

Also, one more option to try in your fstab: Compression=yes
This option enables gzip-like compression of transferred data. I haven't done any serious performance testing with this enabled, so I don't know if it actually speeds things up. man ssh_config for more info.

---

### Post by corban on 2008-02-27
Thanks for this Howto. I think with a tiny addaptation it work also for an curlftpfs entry.
I try this...
changed two lines in ifup.d/mountsshfs:

SELECTED_STRING="sshfs|curlftpfs"

    elif echo $opts | grep -q -E "comment=($SELECTED_STRING)"; then

also changed one line in ifdown.d/umountsshfs

mounted=`grep -E "(sshfs#|curlftpfs#)" /etc/mtab | awk '{ print $2 }'`

I hope it works. You can see here [http://ubuntuforums.org/showthread.php?t=517939]("http://http://ubuntuforums.org/showthread.php?t=517939") how curlftpfs it set up in your /etc/fstab. I added a "comment=curlftpfs" option similar to your "comment=sshfs" option.

---

### Post by Darwin Award Winner on 2008-02-27
Yes, indeed, this script is generalizable to any network file system. This is left as an excercise for the reader.

---

### Post by Endolith on 2008-02-27
> **Darwin Award Winner said:**
> Yes, indeed, this script is generalizable to any network file system. This is left as an excercise for the reader.

No reason not to spell out examples, though.  Is there a way to do stuff like this through the GUI?

---

### Post by Darwin Award Winner on 2008-02-27
If you're looking for a GUI way, you should probably wait until Hardy Heron comes out, featuring the new GVFS system from Gnome, which *does* let you mount virtual filesystems in the real filesystem.

---

### Post by leetcharmer on 2008-03-13
```
admin@testBackupVM:/mnt$ mount vmware/
mount: wrong fs type, bad option, bad superblock on sshfs#admin@192.168.100.20:/vmfs/,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```I get this error -- What do I do?

This is my fstab:

```
sshfs#admin:/vmfs/ /mnt/vmware fuse port=123,noauto,user 0 0
```This is the normal command I use to connect:
```
sshfs admin@192.168.100.20:/vmfs vmware/
```

---

### Post by Darwin Award Winner on 2008-03-13
You haven't included the IP of the server in your fstab. Based on the command you type, your fstab should probably look like this:
```
sshfs#admin@192.168.100.20:/vmfs /mnt/vmware fuse port=123,noauto,user 0 0
```
Also, from your post, it looks like you are planning to use this to do backups of some sort. If so, you might not want to do things using sshfs. In my experience, transferring large amounts of data over sshfs is somewhat unreliable. I would look into using rsync instead. Rsync can operate over ssh, giving you all the security advantages that sshfs does.

---

### Post by goodtimetribe on 2008-03-16
> **christian.paratschek said:**
> I've found a nice addition to your fstab-entry.

If you plan zu use rsync to sync files from your local machine to your ssh-server, you need "workaround=rename"

Otherwise, you will not be able to update an older version of a file with a newer one. Without this option, you will be able to create files and folders and delete them, but you will get an error like this, if you try to update a file:

rsync: rename "/home/christian/Server/xxx/yyy/.index.html.Q3Btvn" -> "xxx/yyy/index.html": Operation not permitted (1)

Thanks for the heads up on this. So let me make sure I understand, if I'm using the command line I need to add a -o workaround=rename ?

thanks,

---

### Post by goodtimetribe on 2008-03-16
Thanks, it definitely mounts fine, but II can't get it to automount. I don't know what I'm doing wrong. I'm using gutsy. Where do I begin to trouble shoot? I'm on a laptop so of course it's not on the network until after the wireless network manager for kubuntu launches.

thanks for any help

---

### Post by Darwin Award Winner on 2008-03-16
First you should verify that your fstab entries are ok. If you can mount the sshfs folder simply by typing
```
mount /path/to/folder
```
then your fstab is set up correctly. 

Next, you should check that the mounting script works correctly when run manually in a terminal, first as yourself, then using sudo.

Let me know if both of those work.

---

### Post by leetcharmer on 2008-03-18
> **Darwin Award Winner said:**
> Also, from your post, it looks like you are planning to use this to do backups of some sort. If so, you might not want to do things using sshfs. In my experience, transferring large amounts of data over sshfs is somewhat unreliable. I would look into using rsync instead. Rsync can operate over ssh, giving you all the security advantages that sshfs does.

You're right; I've been planning on using a program called BackerUpper to backup the virtual machines once per week.  So, it accesses the VM Server via ssh and then stores it to another Server with SSH (I could do SAMBA though).  Do you still think rsync would be the best solution when I want to backup just a single folder?  I don't know anything about rsync yet.

---

### Post by goodtimetribe on 2008-03-18
> **Darwin Award Winner said:**
> First you should verify that your fstab entries are ok. If you can mount the sshfs folder simply by typing
```
mount /path/to/folder
```
then your fstab is set up correctly. 

Next, you should check that the mounting script works correctly when run manually in a terminal, first as yourself, then using sudo.

Let me know if both of those work.

both work... my script calls simply upon mount for it's function. I didn't try my script as sudo, but since it works as the active user i cant think of any reason why it would not as sudo. if you think it makes a difference i can try another time.

and if i'm correct on this, i should be able to simply test this by re-selecting my active network from the default kubuntu wifi manager to force it to restart. it doesnt seem like it launches my script, after i modified it to append to a logfile in ~/

still looking for a solution.

---

### Post by Darwin Award Winner on 2008-03-18
Ok, it sounds like the script itself is ok. First of all, are you using KNetworkManager, or some other wifi manager? This script is only tested with Network Manager. Specifically, the script that runs the scripts in the appropriate directories is located at /etc/NetworkManager/dispatcher.d/01ifupdown. 

Another problem I can think of is that you may have made the scripts executable by you, but not by anyone else, or there may be some other odd permission problem.

---

### Post by Darwin Award Winner on 2008-03-18
> **leetcharmer said:**
> Do you still think rsync would be the best solution when I want to backup just a single folder?  I don't know anything about rsync yet.

Yes, rsync is ideal for that sort of thing. Rsync transfers over ssh by default, so you get the same security benefits as sshfs. However, rsync does not have the overhead associated with emulating a real filesystem over ssh, so it should be much faster and more relaiable. There is a nice GUI for rsync called GRsync, if you don't like the command line. Also, you may want to look into a tool called Unison, which synchronizes folders much like rsync, only bidirectionally. In any case, sshfs is not a good way to do folder synchronization.

---

### Post by dittaeva on 2008-06-26
Two zeroes "0  0" are needed in the end of the fstab entry in the tutorial, they are missing and needed.

Those familiar with fstab will remember to add them, but for those who follow the guide blindly it will pose a problem, at least it did for me in Ubuntu 8.10.

---

### Post by chriv on 2008-06-26
I found your guide very useful, and appreciated the fact that your solution conformed to debian/ubuntu standards (many don't).

I have found that in Hardy Heron, /etc/mtab sees fuse mounted sshfs mounts as being type "fush.sshfs".  Since we have to define them of type "fuse" in /etc/fstab, the two don't match, and "umount" does not work.  I can only unmount these drives with "fusermount -u" or "fusermount -u -z".  Also, these mounts do not show "sshfs#" at the beginning of each sshfs mounted drive.

Based on these two items, I modified my version of /etc/network/if-down.d/umountsshfs to end with these two lines:
```
mounted=`grep '[COLOR="Red"]fuse.sshfs[/COLOR]' /etc/mtab | awk '{ print $2 }'`
[ -n "$mounted" ] && { for mount in $mounted; do [COLOR="Red"]fusermount -u -z[/COLOR] $mount; done; }
```

I am not fond of the differences between /etc/fstab and /etc/mtab.  They are probably actually a bug in the sshfs or fuse code.  I'm tempted to create add some lines to /etc/network/if-up.d/mountsshfs (after a successful mount) AND /etc/network/if-down.d/umountsshfs (before an attempt to unmount) to use sed to change the "fuse.sshfs" lines to match the /etc/fstab lines using "sshfs#" and "fuse".  I really think that a fuse.sshfs wrapper might be needed, but I have no idea what should be in it.

This line will modify /etc/mtab, but requires su rights, so it defeats part of the purpose of this (suggestions are appreciated):
```
sudo sed 's/\(^[^@]\{1,\}@\)\(.\{1,\}\) fuse\.sshfs /sshfs#\1\2 fuse /' -i /etc/mtab
```

The line above is effective in making umount work correctly, but it does not change the fact that it requires su rights to run.  I'm filed the differences between fstab and mtab as a bug#243298 on launchpad ([https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/243298](https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/243298)).

---

### Post by Darwin Award Winner on 2008-06-26
> **dittaeva said:**
> Two zeroes "0  0" are needed in the end of the fstab entry in the tutorial, they are missing and needed.

Those familiar with fstab will remember to add them, but for those who follow the guide blindly it will pose a problem, at least it did for me in Ubuntu 8.10.

Thank you, I fixed it.


I'd also like to note that the script still works unmodified in Hardy, except for the problem, already mentioned, that you must use fusermount -u instead of umount. Despite this, I find that the auto-unmount script (which uses umount) still works fine, since it unmounts everything with administrator (root) privileges. I will file a bug in the Ubuntu bug-tracking system for this.

If possible, I would like to work out how to use the GNOME gvfs system to replace sshfs, since that should integrate better with the file manager. If I succeed, I will post a link in this thread.

---

### Post by Darwin Award Winner on 2008-06-26
> **Darwin Award Winner said:**
> If possible, I would like to work out how to use the GNOME gvfs system to replace sshfs.

After some preliminary tests, I'm convinced that this is possible. However, I cannot work on it right now, because the sftp transport of gvfs is unable to connect to one of my servers.

---

### Post by Endolith on 2008-07-07
> **Darwin Award Winner said:**
> 
You should have a pair of directories called [FONT="System"]/etc/network/if-up.d[/FONT] and [FONT="System"]/etc/network/if-down.d[/FONT].

Scripts in the first directory will be executed when the computer connects to the network, and scripts in the second one will be executes when it disconnects.


Does this work if the ssh server is the thing going up and down, though?  If I'm trying to have a remote machine mount directories on my laptop, and I shut down the laptop, what will happen?  This script is running on the remote server, so its own network connection will still be up.

> **Darwin Award Winner said:**
> If you're looking for a GUI way, you should probably wait until Hardy Heron comes out, featuring the new GVFS system from Gnome, which *does* let you mount virtual filesystems in the real filesystem.

I waited, and GVFS still doesn't do what I want.  In this case, when you first log into a server through the *Places* GUI, a link is created in ~/.gvfs, which is what I was hoping for, but this link does not exist in the future, even if you connect to the same location through Nautilus or the *Places* list.  ~/.gvfs is just empty.  I was expecting the link to be persistent, and to open up an SSH connection whenever accessed.

Also, since GVFS is user-based, it doesn't work for a remote server connecting to the thing you are logged into  (In my case, a media player that accesses the music directory on my laptop.)

---

### Post by Darwin Award Winner on 2008-07-08
Endolith, you're right, this is a client-side solution. It basically assumes that all the servers will always be up. 

However, as for GVFS, there's a command called gvfs-mount which could be used in a script to automount locations in the same way as my script, so my script could easily be rewritten to use GVFS. (The only problem for me is that it has trouble connectign to one of the servers I use, since that server doesn't use openssh.) That still doesn't serve your problem, though.

To solve your problem, I can think of another solution using ssh and sshfs. First, you'd need to set up passwordless logins going both ways (i.e. set it up so you can ssh from laptop to server and server to laptop). Then, on the laptop, in /etc/network/if-up.d/, you would put a script that runs a command something like this:

```
#!/bin/sh
sudo -u username ssh myserver '{ fusermount -uz ~/musicfolder; sshfs username@mylaptop:~/musicfolder ~/musicfolder; }'
```

---

### Post by Endolith on 2008-07-09
> **Darwin Award Winner said:**
> However, as for GVFS, there's a command called gvfs-mount which could be used in a script to automount locations in the same way as my script, so my script could easily be rewritten to use GVFS. (The only problem for me is that it has trouble connectign to one of the servers I use, since that server doesn't use openssh.) That still doesn't serve your problem, though.

Oh, I see.  That's in gvfs-bin, which I didn't have installed.  Still don't see documentation for it, though.

> To solve your problem, I can think of another solution using ssh and sshfs. First, you'd need to set up passwordless logins going both ways (i.e. set it up so you can ssh from laptop to server and server to laptop).

Already did that.  :)  [http://ubuntuforums.org/showthread.php?p=5339039](http://ubuntuforums.org/showthread.php?p=5339039)

> 
 Then, on the laptop, in /etc/network/if-up.d/, you would put a script that runs a command something like this:

```
#!/bin/sh
sudo -u username ssh myserver '{ fusermount -uz ~/musicfolder; sshfs username@mylaptop:~/musicfolder ~/musicfolder; }'
```

Aha!  That's basically what I've been typing by hand, except you put it in a script that gets run whenever the network comes up.  Suddenly everything makes a lot more sense to me.  :)

I notice there are (possibly redundant [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/228150](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/228150)) scripts in if-up.d that mount all the network file systems defined in fstab. Apparently this does not include sshfs, which is why you created your mountsshfs script?

Maybe it would be easier to set this up, and more robust, if we got sshfs added to the default scripts, and then defined the sshfs shares in fstab, and then had my laptop script simply call the mountnfs script on the other machine through ssh?  Then the shares would connect whenever both machines were online, regardless of which machine turned off and back on?


Also, you should put a comment in your scripts with this thread's URL, so it's easy to remember where they came from when some configuration change breaks them 3 years from now. :)

---

### Post by Darwin Award Winner on 2008-07-09
> **Endolith said:**
> Maybe it would be easier to set this up, and more robust, if we got sshfs added to the default scripts, and then defined the sshfs shares in fstab, and then had my laptop script simply call the mountnfs script on the other machine through ssh?  Then the shares would connect whenever both machines were online, regardless of which machine turned off and back on?
The mountnfs scripts make the same assumption that my script does, i.e. that the servers that it connects to are always on (you could call this the client assumption), so there's nothing about those scripts that would guarantee that the shares were mounted whenever both ends were on. I seem to recall someone else's solution which included a script that pinged all the servers every 5 minutes or so and mounted or unmounted the shares based on whether the ping succeeded. You could try searching for that.

As for integration of sshfs into those scripts, I suppose it would be possible. It gets complicated, though, since you have to put "fuse" as the filesystem type in /etc/fstab, which obviously does not indicate an sshfs mount.

> 
Also, you should put a comment in your scripts with this thread's URL, so it's easy to remember where they came from when some configuration change breaks them 3 years from now. :)
Done.

---

### Post by Endolith on 2008-07-09
> **Darwin Award Winner said:**
> The mountnfs scripts make the same assumption that my script does, i.e. that the servers that it connects to are always on (you could call this the client assumption), so there's nothing about those scripts that would guarantee that the shares were mounted whenever both ends were on.

I meant that building sshfs into the network shares script would simplify things for both use cases.  I would still be calling the other computer's scripts through SSH, but I'd just tell it to run its own if-up script instead of mounting the shares explicitly.  Having it defined in the server's fstab would ensure that it was mounted when the server reboots, too, right?

I set up your explicit script and it seems to work.  Thanks!

> As for integration of sshfs into those scripts, I suppose it would be possible. It gets complicated, though, since you have to put "fuse" as the filesystem type in /etc/fstab, which obviously does not indicate an sshfs mount.

Ah..

---

### Post by Endolith on 2008-09-13
> **Darwin Award Winner said:**
> The mountnfs scripts make the same assumption that my script does, i.e. that the servers that it connects to are always on (you could call this the client assumption), so there's nothing about those scripts that would guarantee that the shares were mounted whenever both ends were on.

Here's what I have for now:

Server **/etc/network/if-up.d/sshfsmount**:
```
#!/bin/bash

fusermount -uz "/home/serverusername/Music/Remote CD-ROM/"
sshfs username@laptophostname:"/media/cdrom" "/home/serverusername/Music/Remote CD-ROM"

fusermount -uz "/home/serverusername/Music/Remote My Music"
sshfs username@laptophostname:"/media/windows/Documents and Settings/Username/My Documents/My Music" "/home/serverusername/Music/Remote My Music"

fusermount -uz "/home/serverusername/Music/FTP music/"
sshfs username@laptophostname:"/home/ftp" "/home/serverusername/Music/FTP music"

```Laptop **/etc/network/if-up.d/sshfsmount**:
```
#!/bin/bash

sudo -u username ssh serverhostname '
bash /etc/network/if-up.d/sshfsmount
'

```That way if the server comes up and the laptop is already on, it mounts the laptop's shares.  If the laptop comes up and the server is already up, it asks the server to mount the shares, and I only have to edit the shares list in one place.

> I seem to recall someone else's solution which included a script that pinged all the servers every 5 minutes or so and mounted or unmounted the shares based on whether the ping succeeded. You could try searching for that.That's a good idea.  I can't find it, though.

---

### Post by dittaeva on 2008-10-08
"As an added bonus, since these shares are in fstab, GNOME will automatically create desktop icons for them when they are mounted, so you will have easy access to them."

I have yet to see these desktop icons appear, any settings I have to change to make it happen?

---

### Post by cov on 2008-10-16
Hi,

I'm trying to mount an image file of a partition captured by dd thru gzip.

Someone mentioned gvfs-mount might do the trick, but I'm unable to find any documentation on how to do this.

Can someone point me in the right direction or let me have the syntax for this?

Many thanks,

Dave

---

### Post by Endolith on 2008-10-16
> **cov said:**
> I'm trying to mount an image file of a partition captured by dd thru gzip.


I don't think that's really relevant to this thread, but which command did you use?

---

### Post by cov on 2008-10-18
> **Endolith said:**
> I don't think that's really relevant to this thread, but which command did you use?

My apologies.

I have started another thread here...[http://ubuntuforums.org/showthread.php?p=5988126#post5988126]("http://ubuntuforums.org/showthread.php?p=5988126#post5988126")

---

### Post by _sAm_ on 2008-11-07
Thank you for your tutorial, it works well. Could you please explain the exec options in /etc/fstab

---

### Post by Hedian on 2008-11-29
Kudos to Darwin Award Winner for this great HOWTO!
Alas, despite everything else working I cannot run the mounting script via sudo, what I suppose thwarts automounting. Permission problems anyone (I'm running Intrepid, in case it matters)? Advice on this would be really appreciated, I'm just to close to perfect happiness to give up now. :-k

---

### Post by Darwin Award Winner on 2008-11-29
> **Hedian said:**
> Kudos to Darwin Award Winner for this great HOWTO!
Alas, despite everything else working I cannot run the mounting script via sudo, what I suppose thwarts automounting. Permission problems anyone (I'm running Intrepid, in case it matters)? Advice on this would be really appreciated, I'm just to close to perfect happiness to give up now. :-k

Odd. I'm not sure why it wouldn't work. I've upgraded to Intrepid, and I'm still using this script unmodified. When run as root, the script is supposed to mount each mount point as its owner, as specified in the uid option in fstab. I suppose it's possible that my user-detection code is wrong for some rare cases. Obviously, I can't test it on other people's computers. I'm afraid that if the script doesn't work as is, you'll have either give up or learn bash scripting and debug it yourself. Sorry.

---

### Post by Hedian on 2008-11-29
Thanks for the fast reply, at least I have a starting point now.
And some bash kung fu could come in handy anyway. :)

---

### Post by NetGenSuperstar on 2008-12-07
I'm having a problem as well.  Running *mountsshfs* as user works fine, and running *umountsshfs* as root works fine.  I've successfully set up passwordless ssh login, and the unmount script runs fine when I disable the network.  But if I re-enable the network, the script doesn't seem to run.  If I run *mountsshfs* as root, I get this error:

```
read: Connection reset by peer
/home/<user>/mount-ssh failed to mount as <user>
```

I can only assume it's throwing this same error when the network is enabled, but I don't know how to check that.

Does anyone know what the problem may be?  The client computer is running Ubuntu Hardy, connecting to a server running Mac OS X.  If you need more info, just ask.

EDIT: I got it working.  I forgot that I had set a password for my id_rsa file.  I created a new one without a password, and now it works fine.  However, if this is not safe, I'd like to know if there is an alternative.  For now, though, it seems fine.

---

### Post by alex wingnut on 2008-12-22
Hi All!

After more than 15 hours of error searching I stumbled across an easier way.
My problem was that mount, if-up and if-down runs as root. So when sshfs where looking for the rsa-key located in my home-dir it could not find any as it was looking in the root's home dir. The ssh rsa-authentication failed and ssh where asking for password. The sshfs rejected that response and exited with status "read: Connection reset by peer".

[http://www.debian-administration.org/articles/587](http://www.debian-administration.org/articles/587)

In this post I read that sshfs added the option "password_stdin" by march 2008. So now it is possible to mount automaticly when network goes up by adding the following line in /etc/network/if-up/mountsshfs:
```

!#/bin/sh
echo "yourPassword" | sshfs username@server:remoteDir /mountDir -o allow_other,uid=yourUserId,gid=yourGroupId,password_stdin

```

And simply add the following to /etc/network/if-down/umountsshfs:
```

!#/bin/sh
umount /mountDir

```

This is the minimalistic way and I use it here just to share what I found. I'm sure you can tweak this solution to make it more error safe and secure.

EDIT: Of course you need to chmod mountsshfs and umountsshfs to 755 and set the root as owner so that they will become executable.

---

### Post by Darwin Award Winner on 2008-12-22
> **alex wingnut said:**
> My problem was that mount, if-up and if-down runs as root. So when sshfs where looking for the rsa-key located in my home-dir it could not find any as it was looking in the root's home dir. 
Yes, the script does run as root. However, it is designed to use sudo to run the sshfs command as the appropriate user. Notice that in my examples, I explicitly assign an owner to the sshfs mount in the fstab options. My script uses this to find out which user to mount the share as.

> Of course you need to chmod mountsshfs and umountsshfs to 755 and set the root as owner so that they will become executable.
Whoa, there. If you're putting your login password in those scripts, it's probably more appropriate to chmod the scripts 700, since they now contain sensitive information. The least you can do is require the root password to read them, in the name of security.

---

### Post by conchyliferous on 2009-01-02
I had problems with non-root unmounting.

Fixed it by adding "fsname=sshfs#<user>@<host>:<path>" to the fstab options (kept all other options).

```
sshfs#<user>@<host>:<path> <local path> fuse comment=sshfs,noauto,users,exec,uid=1000,gid=1000,allow_other,reconnect,transform_symlinks,BatchMode=yes,fsname=sshfs#<user>@<host>:<path> 0 0
```

Read this for more information:
[https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/243298](https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/243298)

Regards,
Ola

---

### Post by shuthichi on 2009-01-28
Hi there,

i have Problems with the automount.

My System is Ubuntu 8.10 and I want to connect to a Terastation with running OpenSSH.
On my old system (Ubuntu 8.04) this script already has worked!! But not with my 8.10...

I have setup public key authentification, so i can connect to my terastation via
```
ssh root@192.168.178.25
```without password.


My fstab looks like this
```
sshfs#root@192.168.178.25:/mnt/array1/data /home/niko/mnt/terastation fuse fsname=sshfs#root@192.168.178.25:/mnt/array1/data,comment=sshfs,noauto,users,exec,uid=1000,gid=1000,allow_other,reconnect,transform_symlinks,BatchMode=yes 0 0
```


If i run the /etc/network/if-up.d/mountsshfs with my user, the mount is working well!
```
niko@nik-thinkpad:/etc/network/if-up.d$ ./mountsshfs
/home/niko/mnt/terastation mounted as current user (niko)
niko@nik-thinkpad:/etc/network/if-up.d$
```

But when i run this script as sudo i get a: connection reset by pear
```
niko@nik-thinkpad:/etc/network/if-up.d$ sudo ./mountsshfs
read: Connection reset by peer
/home/niko/mnt/terastation failed to mount as #1000
niko@nik-thinkpad:/etc/network/if-up.d$ 

```
So the automount on system start doesnt's work for me.

The files mountsshfs and unmountsshfs are chown to root:root with chmod 755.

Whats going wrong?

//Edit: Ok, found the Problem: I have setup a phasphrase for my rsa_key. Without the a phasphrase it works.

---

### Post by shavedmonkey on 2009-03-18
These scripts work flawlessly out of the box for me between two Intrepid machines.  More importantly, you documented every single step, command, and edit clearly instead of providing the usual "just copy and paste this, it'll work" type of post that plagues Linux forums.  Thank you so much.

---

### Post by SeanOB on 2009-03-30
Thanks!
Much better than nfs for video streaming on my boxes!

---

### Post by jpseixas on 2009-04-13
Including de sshfs mount in my fstab does not work for me. The system tries to mount before the network is available, causing the automount to fail.

I made a very simple script to work around that:

```
#!/bin/bash

SERVER="xxx.xxx.xxx.xxx"

until ping $SERVER -W 5 -c 1 -q; do continue; done

sshfs $SERVER:[server path] [local path]

exit 0

```

I made this script run at startup. This way, I get the ssfs share automount as soon the server is up. This is particular useful when the client machine starts up before server.

It simply pings the server every 5 seconds, and when it's available, it mounts the sshfs share.

---

### Post by Darwin Award Winner on 2009-04-14
That should not be necessary. You simply need to use the noauto mount option. As the title implies, my guide already shows a way to automatically mount your sshfs mounts when the network comes up. You simply need to use the /etc/network/if-up.d/ directory. Any scripts in that directory will only be executed after the network is up.

---

### Post by hedgefighter on 2009-04-24
In Kubuntu Jaunty, I was actually getting Permission denied errors from fuse even after uncommenting user_allow_other in fuse.conf. The problem seems to be this bug: [https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/123501](https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/123501)

The solution is to add yourself to the fuse group:```
sudo adduser <youruser> fuse
```Then logout and log back in for the group change to take effect.

---

### Post by jbernardo on 2009-05-10
Thanks a lot! This solved quite a few problems for me.

---

### Post by Temposs on 2009-05-22
This is an excellent tutorial, and I've implemented it successfully on two machines. My wife loves seemless access to her stuff on our home server.

Two points of update:
1) The link for passwordless SSH login is broken as of this post.

2) Running Jaunty, I seem to be able to unmount sshfs from a non-root user using the original fstab entry. So the perl fix at the end should be specified for 8.04 and 8.10.

---

### Post by TuxCrafter on 2009-06-13
I made a support package that integrates sshfs better with the ifup and ifdown network systems, it works with all network managers like gnome-network-manager or the /ect/network/interfaces systems.

I hope you like it, there is also a private repository and a mailinglist see the readme in the root of the svn repoisory, join and help out if you like.

package is also in debian mentors waiting for a sponser:
[http://mentors.debian.net/debian/pool/main/p/pct-sshfs-storage/](http://mentors.debian.net/debian/pool/main/p/pct-sshfs-storage/)

[https://secure.powercraft.nl/svn/packages/trunk/source/pct-sshfs-storage/debian/pct-sshfs-storage_0.1.0-1_all.deb](https://secure.powercraft.nl/svn/packages/trunk/source/pct-sshfs-storage/debian/pct-sshfs-storage_0.1.0-1_all.deb)

```
Source: pct-sshfs-storage
Section: misc
Priority: extra
Maintainer: Jelle de Jong <jelledejong at powercraft dot nl>
Build-Depends: debhelper (>= 7)
Standards-Version: 3.8.1
Homepage: https://secure.powercraft.nl/svn/packages/trunk/source/pct-sshfs-storage/

Package: pct-sshfs-storage
Architecture: all
Depends: sudo, sshfs, ifupdown
Description: intergrate sshfs fstab (u)mount with ifup and ifdown systems
 This package contains scripts and a configuration system to easily
 intergrate your sshfs remote storage system with the standard ifup and
 ifdown systems. This will make it possible to disconnect and reconnect
 to diffrent networks without freezing your sshfs mounts.
 .
 Features:
  - uses the sshfs entry in /etc/fstab
  - supports multiple users, servers, and mount locations
  - connect and disconnect sshfs mounts when network goes up/down
  - possiblility to automatic make smart symbolic links
  - prechecks on mount points and debuging options
  - uses bash, mount and umount mainstream processing tools
```

---

### Post by olembe on 2009-07-31
This tutorial has been extremely useful for me. However, my system doesn't seem to be calling the /etc/network/ip-up.d and /etc/network/if-down.d scripts. I can now mount my folder without a password, and can call the if-up.d or if-down.d scripts from the command line just fine. But there is no automatic mount when I log in, and no automatic unmount when I kill the network collection (e.g., by manually disconnecting my wifi, which I've just done as a test).

Can anyone please clarify when the scripts in if-up.d and if-down.d are called by the system?

---

### Post by Darwin Award Winner on 2009-07-31
> **olembe said:**
> This tutorial has been extremely useful for me. However, my system doesn't seem to be calling the /etc/network/ip-up.d and /etc/network/if-down.d scripts. I can now mount my folder without a password, and can call the if-up.d or if-down.d scripts from the command line just fine. But there is no automatic mount when I log in, and no automatic unmount when I kill the network collection (e.g., by manually disconnecting my wifi, which I've just done as a test).

Can anyone please clarify when the scripts in if-up.d and if-down.d are called by the system?
The scripts in the directory /etc/network/if-up.d should be run right after a network connection is established. Likewise, the scripts in /etc/network/if-down.d should be right right before a connection is terminated.

---

### Post by olembe on 2009-07-31
Thanks for the quick reply, D.A.W.

It doesn't seem to be working. I've used the scripts from this tutorial, but the directory doesn't automount when I boot up, and doesn't disconnect automatically when I lose the network connection. The permissions all seem right (the .d directories and the scripts inside are owned by root), so I'm mystified.

---

### Post by Darwin Award Winner on 2009-07-31
Did you make sure to mark the scripts executable?

You can test things by makeing some scripts in those directories called 50-test-script.sh with the following contents:

date >> /tmp/if-test.log
echo "Interface came up/down." >> /tmp/if-test.log

Then check the file /tmp/if-test.log while you connect and disconnect your network. It should have new lines of text appended each time. If not, then the scripts are definitely not being executed. You can monitor this file in real time by running the following command in a terminal:

tail -f /tmp/if-test.log

---

### Post by olembe on 2009-07-31
> **Darwin Award Winner said:**
> Did you make sure to mark the scripts executable?

Yes, they're 755.

> **Darwin Award Winner said:**
> You can test things by makeing some scripts in those directories called 50-test-script.sh with the following contents:

date >> /tmp/if-test.log
echo "Interface came up/down." >> /tmp/if-test.log

Then check the file /tmp/if-test.log while you connect and disconnect your network. It should have new lines of text appended each time. If not, then the scripts are definitely not being executed. You can monitor this file in real time by running the following command in a terminal:

tail -f /tmp/if-test.log

Good suggestion. I tried that and disconnected, then reconnected, my wifi connection. Nothing went into the file. Do I need to do something more dramatic than kill my wifi connection? Or is that now evidence the scripts aren't being called?

---

### Post by Darwin Award Winner on 2009-07-31
The default Ubuntu configuration executes these scripts at the appropriate times. I haven't messed around with it lately, but if I recall correctly, the component responsible for executing the scripts is Newtork Manager. Have you switched to wicd or some other network configuration system?

---

### Post by olembe on 2009-07-31
Ah! Yes, I'm using wicd. Sorry: I should have mentioned that. Right: that explains it.

I've just had a hunt and found [http://ubuntuforums.org/archive/index.php/t-905131.html](http://ubuntuforums.org/archive/index.php/t-905131.html) which mentions scripts. This solved it. 

For the benefit of anyone else: From the wicd window (the one which lists available networks), click the little triangle next to your wireless network name to see extra options. One of these is a button called 'scripts'. Here, you can choose scripts to run before and after connection, and after disconnection.

I entered the paths to my if-up.d and if-down.d scripts here and it solved everything!

Thanks so much for the help.

(Incidentally, I decided to leave the scripts in the if-up.d and if-down.d directories, so it's all set if I switch back to network manager in the future)

---

### Post by mano the shark on 2009-09-05
Thanks for the outstanding script.  One suggestion for unmounting the shares from:
```
for mount in $mounted; do umount -l $mount; done;
```
to
```
for mount in $mounted; do fusermount -uq $mount; done;
```
mountsshfs works if called by root or user, but umountsshfs doesn't as umount returns an error if not called by root.

---

### Post by Darwin Award Winner on 2009-09-06
Yes, I need to update this setup. I had been meaning to set up a solution that used gvfs (GNOME Virtual File System) instead of sshfs, but the gvfs implementation of sftp has not worked consistently for me. However, I've recently found out about autossh, which can be combined with sshfs for more persistent mounts. I plan to update this script in the next few weeks.

---

### Post by jbernardo on 2009-09-06
Please, don't tie it to a desktop environment. I am using your scripts on kubuntu netbooks, where all hard disk space is at a premium and every added lib might be one too many... :)

autossh migh be a good idea...

---

### Post by Groover20 on 2009-10-16
I got a bit of a weird problem.  I followed the How-To and had everything working perfectly.  I was away this week, and was able to access files on my server from the hotel easily.

I was working in my office this morning, listening to some music located on my server.  I left for lunch, and when I got back, I noticed the the icon for the MusicOnServer was gone.  All the others (Movies, Fun, E-Books) were still there.  I stop the network and restarted it, I rebooted the computer, nothing worked.

When I try to run the mount script manually, I get a message stating that /media/MusicOnServer failed to mount as #1000.

I then logged onto the server with sftp (through Gnome), and checked the properties of the folder...It shows #1000.

I'm not sure of what to do next.

-----

Ok, after posting here, I went and looked in /media/MusicOnServer.  There was a folder.  I deleted it, ran the mount script, and it's back!

---

### Post by Groover20 on 2009-12-04
Me again... I updgraded to Karmic earlier this week, and I had to comment out the SSH mount in my FSTAB.  It was as if it was slowing the computer right down, and making it very unstable.

I'm able to get it to work for 1 drive at the time, but I can't seem to mount all my drives at once, as it was the case in Jaunty.

Anybody else had the same issue?

---

### Post by houdodu on 2009-12-19
works for me on 9.10, and seems to mount consistently, but doesn't show the mount point in nautilus with the others? is that normal?

---

### Post by mano the shark on 2009-12-21
I'm not home to check, but I mount everything in /mnt and then link back to the folders.  I know that multiple links show up within nautilus and I'm fairly confident that all of the mount points are displayed.

---

### Post by ilSignorCarlo on 2010-01-04
Hi,
I am using Ubuntu Hardy Heron. I followed the guide and now I can mount to remote filesystems just using mount /mountpoint. Anyway they are not automatically mounted at startup, even if my wireless connection is up and working.

Then if I try to run the script manually I get this:

(workspace/ferro and workspace/prediction are my local mount points)

```

[carlo@pynchon:~]$ ls workspace/ferro                             (01-04 00:57)
[carlo@pynchon:~]$ /etc/network/if-up.d/mountsshfs                (01-04 01:01)
read: Connection reset by peer
/home/carlo/workspace/prediction failed to mount as current user (carlo)
/home/carlo/workspace/ferro mounted as current user (carlo)
[carlo@pynchon:~]$ ls workspace/prediction                        (01-04 01:01)
[carlo@pynchon:~]$ mount workspace/prediction                     (01-04 01:02)
[carlo@pynchon:~]$ ls workspace/prediction                        (01-04 01:02)
BCK_style.css          css  index.php    no_style.css  style.css
calendar-icons.tar.gz  img  license.txt  scripts       system
```

Any idea why it doesn't work properly?

---

### Post by chaeron on 2010-01-17
Hey Darwin Award Winner:

Brilliant!  Your process/scripts worked flawlessly on my new Karmic Koala system, accessing a remote WD MyBook NAS drive.

Thanks so much for posting and updating this stuff. Very much appreciated.

BTW...how did you earn your moniker?  Or are you posting from beyond the grave? LOL

---

### Post by bohemier on 2010-04-16
Wow, thanks this is wonderful. Works flawlessly in 10.4 (using beta 2 right now). :KS

---

### Post by saeraphas on 2010-04-22
This guide worked for me today in Ubuntu 9.10 with a few small modifications. 

In step 2, I had to set /etc/fuse.conf global readable before I could mount without errors: 
```
sudo chmod o+r /etc/fuse.conf
```

GNOME did not automagically create a new icon for me on the desktop or in Nautilus at first because I had chosen /mnt/sshfs/homeserver as my mount point. I changed my mount point to /media/sshfs/homeserver and remounted and the new icons appeared immediately.

---

### Post by Darwin Award Winner on 2010-07-07
> **chaeron said:**
> BTW...how did you earn your moniker?  Or are you posting from beyond the grave? LOL

That's the joke. I originally came up with it when playing online shooting games -- the kind where your average lifespan is measured in seconds.

---

### Post by cong06 on 2010-07-14
Sorry, I'm not reading the next 10 pages of posts. But I have a suggestion:

> **Darwin Award Winner said:**
> 
Finally, and very importantly, you must have set up PASSWORDLESS login to the ssh host that you wish to mount. For details on how to set this up, go [here]("http://doc.gwos.org/index.php/SecureSSH#Avoid_Using_Passwords"). A non-automatic variation of this howto is possible without passowrdless logins.

The link is bad. So  let me recommend:
[http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)
which was very easy for me to follow.

---

### Post by amppa on 2010-08-03
> **mkramer said:**
>  Everything works great except that it doesn't mount on a reboot.  It mounts if I run /etc/init.d/networking restart.  It mounts if I run /etc/network/if-up.d/mountsshfs as a user.  But it does not mount on reboot.  What could be the problem here?

I added this script to /etc/rc.local and it now mounts on boot.

I had the same problem with one machine. It is using Wicd instead of network manager. 

Wicd doesn't run /etc/network/if-up.d and /etc/network/if-down.d scripts automatically. Scripts had to be added in Wicd's own directories (/etc/wicd/scripts/...)

---

### Post by trygve.u on 2010-09-01
Hi and thanks for a fantastic script.

Is there any way to mount with the ability to follow symlinks?

---

### Post by goodtimetribe on 2010-09-10
> **amppa said:**
> I had the same problem with one machine. It is using Wicd instead of network manager. 

Wicd doesn't run /etc/network/if-up.d and /etc/network/if-down.d scripts automatically. Scripts had to be added in Wicd's own directories (/etc/wicd/scripts/...)

is that why using sshfs#fuse lines in my fstab produces an error?

---

### Post by sonicb00m on 2010-09-24
> **trygve.u said:**
> Hi and thanks for a fantastic script.

Is there any way to mount with the ability to follow symlinks?

Append ,follow_symlinks to your fstab or if mounting manually use -ofollow_symlinks

---

### Post by narcisgarcia on 2010-10-07
A new guide to configure better the client and the server:
[http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses](http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses)

---

### Post by narcisgarcia on 2010-10-07
A new guide to configure better the client and the server:
[http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses](http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses)

(with special care with owners and permissions questions)

---

### Post by cong06 on 2010-10-10
> **narcisgarcia said:**
> A new guide to configure better the client and the server:
[http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses](http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses)

(with special care with owners and permissions questions)

I just skimmed over it, but I found it a bit more confusing...

---

### Post by narcisgarcia on 2010-10-10
Your questions can help me to arrange the guide.

---

### Post by cong06 on 2010-10-16
narcisgarcia. I wrote something up, but I don't feel like it's necessarily appropriate to discuss the editing of a guide, in the topic of another guide (doing the same thing).

So if you enable PMs, I'll send my edits/questions in a PM.

---

### Post by narcisgarcia on 2010-10-17
You can also write in the wiki's discussion tab.

---

### Post by Jungleboss on 2010-11-06
Please delete this. I found the solution to my problem in this thread. sorry

---

### Post by joe4379 on 2010-11-30
:KS:KS:KS:KS:KS - 5 STAR scripting !!!!

I registered just to say SPANKS A LOT !!!!

Confirmed working on Maverick.  Solid.

btw, fyi, and fwiw, this was the missing piece of my network-search-indexing puzzle.  now gdsearch is crawling my doc server with no babysitting or cmdline sshfs cmds.

---

### Post by Darwin Award Winner on 2010-11-30
joe4379, I should warn you that sshfs can be unreliable under heavy load. If it works for you, then go for it. But don't be surprised when it randomly hangs or disconnects.

---

### Post by narcisgarcia on 2010-12-01
Darwin, with the [proper parameters]("http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses"), a SSH link can be very stable.

I've tested playing remote videos, and working through internet.
A well configured network can be used with fuse.sshfs for production with a file server (no Samba/CIFS, no FTP, no NFS).

---

### Post by nolanpro on 2010-12-10
Thanks for this awesome script!

However, for some reason, it prevents my machine from suspending or hibernating. (Maverick, Mactel)

I wonder if autofs (and its esoteric auto.master, auto.* config files) would hold up better to suspending.

---

### Post by narcisgarcia on 2010-12-11
I think is necessary to unmount when suspending or hibernating.
I don't know which events can be intercepted to run unmounting and mounting commands.

---

### Post by ncolson on 2011-03-07
I followed the instructions in this thread to persistently mount an sftp share between reboots, and met with authentication issues and errors at every twist and turn (most of which is probably due to me being a n00b).  So that was all a good learning experience, BUT...

How's this for an alternative:

1. In gnome, got to System > Preferences > Startup Applications
2. Click Add
3. Enter this in the Command field:   gvfs-mount s[ftp://location.to/my_bookmark](ftp://location.to/my_bookmark)

More here: [http://www.mail-archive.com/nautilus-list@gnome.org/msg05343.html](http://www.mail-archive.com/nautilus-list@gnome.org/msg05343.html)

I'm using Maverick, and this worked perfectly for me, and took about 30 seconds with 0 command line (yes, I'm lazy).

This should work for anyone who can connect to the share using Places > Connect to Server, as a starting point.  The resulting mount point is under[FONT=monospace] [/FONT]~/.gvfs

---

### Post by Darwin Award Winner on 2011-03-07
> **ncolson said:**
> I followed the instructions in this thread to persistently mount an sftp share between reboots, and met with authentication issues and errors at every twist and turn (most of which is probably due to me being a n00b).  So that was all a good learning experience, BUT...

How's this for an alternative:

1. In gnome, got to System > Preferences > Startup Applications
2. Click Add
3. Enter this in the Command field:   gvfs-mount s[ftp://location.to/my_bookmark](ftp://location.to/my_bookmark)

More here: [http://www.mail-archive.com/nautilus-list@gnome.org/msg05343.html](http://www.mail-archive.com/nautilus-list@gnome.org/msg05343.html)

I'm using Maverick, and this worked perfectly for me, and took about 30 seconds with 0 command line (yes, I'm lazy).

This should work for anyone who can connect to the share using Places > Connect to Server, as a starting point.  The resulting mount point is under[FONT=monospace] [/FONT]~/.gvfs
Adding 'gvfs-mount' to your startup programs is an acceptable solution, but be aware that if your computer frequently disconnects and reconnects to the network, you will have to manually remount your shares. The main reason I wrote this howto was to automate this process of re-connecting.

---

### Post by Darwin Award Winner on 2011-03-07
> **narcisgarcia said:**
> I think is necessary to unmount when suspending or hibernating.
I don't know which events can be intercepted to run unmounting and mounting commands.
If you follow the howto as written, then sshfs shares *should* be unmounted when suspending or hibernating. If not, then your computer may not be explicitly disconnecting from the network before going to sleep.

---

### Post by rkrizan on 2011-04-05
I'm getting this for erros:

root@capone:/home/ryan# /etc/network/if-up.d/mountsshfs 
read: Connection reset by peer
/home/ryan/fuse failed to mount as #1000
root@capone:/home/ryan# 

root@capone:/home/ryan# id ryan
uid=1000(ryan) gid=1000(ryan) groups=1000(ryan),4(adm),20(dialout),24(cdrom),44(video),46(plugdev),104(fuse),111(lpadmin),119(admin),122(sambashare)
root@capone:/home/ryan#

fstab properties:
sshfs#ryankrizan@youecho.com:/home/ryankrizan	/home/ryan/fuse		fuse	comment=sshfs,noauto,users,exec,uid=1000,gid=1000,allow_other,reconnect,transform_symlinks,BatchMode=yes 0 0

Removing uid/gid settings in fstab, able to run the mount script as root without issue. However, will not run at startup after network starts. If I run the mount script after network startup, it asks for a private keyring password.

Suggestions?

---

### Post by Darwin Award Winner on 2011-04-05
If you're getting private key password prompts, then you have a problem with your provate keys. There are already enough howtos on the internet for setting up keys, and my howto here doesn't cover that.

---

### Post by rkrizan on 2011-04-05
I can login via ssh without a password without an issue (CLI). I am getting a GUI window asking for passcode.

---

### Post by narcisgarcia on 2011-04-05
rkrizan, your copied lines have space characters between some words and commas.

---

### Post by rkrizan on 2011-04-05
I just checked fstab. I'm not clear why it post that way here, but there isn't spaces in the fstab entry.

---

### Post by rkrizan on 2011-04-05
Just to show that I am able to login without a password with the 1000 id:


root@capone:~# umount /home/ryan/fuse
root@capone:~# /etc/network/if-up.d/mountsshfs 
read: Connection reset by peer
/home/ryan/fuse failed to mount as #1000
root@capone:~# su ryan
ryan@capone:/root$ ssh [email]ryankrizan@youecho.com[/email] cat /proc/cpuinfo|grep bogomips
bogomips	: 5985.37
bogomips	: 5984.25
ryan@capone:/root$

---

### Post by ernstblaauw on 2011-04-22
I stumbled upon a question: I use your script not only for sshfs, but also for CIFS mounts to just mount and unmount when the network (dis)connects. (I added the comment also to the CIFS share).

Since I upgraded to Natty, my computer takes ages to shutdown (actually, 5 minutes). If I look at the messages which are shown on the console during shutdown, I see, just before the computer finally shits down, the follwoing message:

```
CIFS VFS: Server xxx.xxx.xxx.xxx has not responded in 300 seconds.
```

Could this be related to this script? As it works correectly in previous version, I doubt it is related, but you never know...

---

### Post by narcisgarcia on 2011-04-22
ernstblaauw, you need to try the script manually, and also test manually deactivating NetworkManager without shutting down the system.

---

### Post by ernstblaauw on 2011-04-23
> **narcisgarcia said:**
> ernstblaauw, you need to try the script manually, and also test manually deactivating NetworkManager without shutting down the system.

Do I need to run the script as root or as normal user?
If I do "sudo umount /mnt/share", the computer is turned off normally.

---

### Post by narcisgarcia on 2011-04-23
I suggested you a test to diagnose the problem.
Try the procedure first in the same permissions situation you have, next with root permissions if you feel.

---

### Post by ernstblaauw on 2011-04-24
> **narcisgarcia said:**
> I suggested you a test to diagnose the problem.
Try the procedure first in the same permissions situation you have, next with root permissions if you feel.

I executed manually umountsshfs, as user and with sudo:
```
$ /etc/network/if-down.d/umountsshfs 
umount: /home/ernstblaauw/neostrada mount disagrees with the fstab
$

$ sudo /etc/network/if-down.d/umountsshfs 
$

```
However, the share is still available and if I shutdown, the delay is still there.

The line in my fstab looks like:
```
//172.19.3.10/share    /mnt/nmt    cifs    comment=sshfs,username=xxx,password=xxx,noauto,nounix,users,exec,uid=1000,gid=1000,domain=THUISNETWERK,iocharset=utf8    0    0

```

I also stopped the network-manager applet:
```
sudo killall nm-applet
```
If I shutdown, the dealy is stil there.

Do you have any clues what could be the problem, or is probably the CIFS server buggy?

---

### Post by natacho on 2011-05-15
I'm not able to get it to mount when automatically 
It umount automatically without a problem

When I run it manually i get this


ignacio@ignacio-Laptop:/etc/network/if-up.d$ ./homedir 
[: 109: missing ]
[: 109: missing ]
[: 109: missing ]
[: 109: missing ]
[: 109: missing ]
[: 109: missing ]
[: 109: missing ]
[: 109: missing ]
[: 109: missing ]
[: 109: missing ]
[: 109: missing ]
[: 109: missing ]
[: 109: missing ]
[: 109: missing ]
./homedir: 109: id-un: not found
/home/ignacio/homedir mounted as current user ()

and it mounts fine.

Any idea of how to fix it?

Thanks!

---

### Post by noblepylon on 2011-11-18
First of all, Thank you for your script, it made things a lot easier.

I've just noticed that when my internet connection is unexpectedly cut (i.e. weak wireless signal), the file manager would freeze up. It turned out that /etc/network/if-down.d/umountsshfs did not execute. 
After some hours of investigation, I've solved the problem by moving umountsshfs script to /etc/network/if-post-down.d, which would make it execute *some time after *the time of disconnection.

It would be nice if this problem was specific to my system.

Thanks.

---

### Post by narcisgarcia on 2011-11-19
As I know;

When you use "if-down.d", you are allowing the normal unmount before the connection is really down, but when you use "if-post-down.d" the unmounts occur after disconnection, and any final transaction will fail (such as cache flush or close files in use).

The umount action needs (if possible) alive connection to communicate the end of the SFTP session and release any locked resource.
I see the same situation as unmounting an USB pendrive _before_ or _after_ unplugging it with the hand.

---

### Post by noblepylon on 2011-11-19
But in some situations the connection is suddenly down (i.e. weak wireless signal) so that any "final transactions" could not take place. Maybe that's why the file manager froze up after the wireless is down.

In any case, I had better work in a secure connection so as to keep safe my files.

---

### Post by narcisgarcia on 2011-11-20
Unmounting before network disconnection minimizes probability of data loss, because many umounts will go as expected (other can have unexpected connection break).

Another kind of example: if you are talking on the phone with a friend, it's better to first say "good bye" and after hung up the phone, than first hung up and after say "good bye".
When unmount, you are saying "good bye" to the other computer.

---

### Post by bakinsoda on 2011-11-27
I know this might seem counter-intuitive for this post, but is it possible for sshfs automount to work with a passphrase-enabled key with ssh-agent?  That is, when the computer is turned on, and the network is connected, ubuntu's ssh-agent would ask for the passphrase.  Then enter the passphrase once and automount will work for the remainder of the session without asking for the passphrase again.

I've been using the sshfs autmount method described in this post for the past year, but I just think having a passphrase-enabled key + ssh-agent is essential for better security.

---

### Post by pete_otaqui on 2013-10-04
I wrote a guide on using this with a web development virtual machine for mapping subdirectories to subdomains:

[http://otaqui.com/blog/1652/setting-up-a-virtualbox-virtual-machine-for-web-development-with-multiple-sites-using-mod_vhost_alias-and-virtualdocumentroot/](http://otaqui.com/blog/1652/setting-up-a-virtualbox-virtual-machine-for-web-development-with-multiple-sites-using-mod_vhost_alias-and-virtualdocumentroot/)

---

### Post by spookybathtub on 2014-02-18
If I unplug the ethernet cable, then replug it a few seconds later, should all the scripts in /etc/network/if-up.d/ run?  Is there some longer amount of time the cable needs to be unplugged for?

---

### Post by narcisgarcia on 2014-02-19
Please, take note of the subject, that talks about Feisty version (7.04)
spookybathtub, the best thing you can do to check this in your OS version, is to put some custom script in the directory (/etc/network/if-up.d/) and test.
Example script to watch executions at /tmp/test.log :

#!/bin/sh
date +'%F %T' >> /tmp/test.log

---

