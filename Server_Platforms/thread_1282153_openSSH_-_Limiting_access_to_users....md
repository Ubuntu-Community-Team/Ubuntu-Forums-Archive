---
title: "openSSH - Limiting access to users..."
date: 2009-10-04
forum: Server Platforms
---

### Post by Badcam on 2009-10-04
I have a sheevaplug with Ubuntu Server 9.04.

I've managed to set up access via ssh for:

User1
User2
..
User5

I'd like to set up the access rights so that User1 has access to all files and directories via sudo, and User2 through User5 only has access to their own directories and nothing else. The public keys are held in each users .ssh home directory.

Could you also point me in the direction of a good Samba share thread? I'd like each user to have access via their Linux or Windows PC's to their own server folders.

Thanks for your assistance.

---

### Post by Lars Noodén on 2009-10-04
Can you clarify a little more what you mean by all access for user1?

For user2 - user5, they already have their own groups.  So create a group (e.g. rusers) and add them to it, then put that group in [FONT="Courier New"]/etc/ssh/sshd_config[/FONT]
```

Subsystem sftp internal-sftp

Match Group rusers
   ChrootDirectory /home
   AllowTCPForwarding no
   X11Forwarding no

```

That will allow only sftp access to only the user's directory.

Then you'll need to set the permissions for those home directories so that they are owned by root and not writeable by anyone else.  They need to be readable by the user, of course, and as you wish they must not be readable by any others, except user1

[INDENT][FONT="Courier New"]
drwxr-x---   4 root user2  4096 2009-10-04 13:10 user2
drwxr-x---   4 root user3  4096 2009-10-04 13:10 user3
drwxr-x---   4 root user4  4096 2009-10-04 13:10 user4
drwxr-x---   4 root user5  4096 2009-10-04 13:10 user5
[/FONT][/INDENT]

Then for any subdirectories make those writeable by the respective users.  Add user1 to the groups user2 - user5.

[INDENT][FONT="Courier New"]
sudo usermod -G user2,user3,user4,user5 user1
[/FONT][/INDENT]

Was that heading in the direction you wanted?

---

### Post by Badcam on 2009-10-04
Wow.

This looks to be exactly what I'm looking for. Sorry about not being more clear. I'm learning more about Linux all the time, but mostly persevering by way of being the "King of Copy & Paste" 8-[

For User1, I just mean having full Admin rights. I want to keep root out of the ssh group.

You've given me just the advice that I needed. I'll now go and look up just what it is you've told me, but I'm happy to do that.

Cheers. Lovin' Linux.


(Oh. If anyone can point me to a thorough Samba thread, I'd greatly appreciate that. I don't really want to ask a million and one questions about that, until I'm well & truly stuck)

---

### Post by Badcam on 2009-10-04
OK.

I have set my permissions for each user1 to user5 as directed:

For instance:

drwxr-x--- 3 user1 user1 4096 Oct  4 22:30 /home/user1

I have set up User1 as Admin & set up all users except root as ruser. I have modified the ssd_config file as requested.

I was getting an error when restarting the ssh server as follows:

"/etc/ssh/sshd_config line 87: Directive 'UsePAM' is not allowed within a Match block"

I tried each option yes or no and in the end placed UserPAM=no above your supplied code, restarted and the message no longer appears.

I ran the command "usermod..." as requested.

I have restarted the server, however, I can no longer access the server via puTTy (windows xp) with the users2 through5. user1 logs in fine. It stops at authentication and the log shows this error:

"/bin/bash: No such file or directory"

I can login via Root and user1, so I'm guessing there's something I haven't done correctly when setting up the Groups admin & rusers. One point to note though and that is that all users and root have to login with a ssh-key, but only root and user1 require a password with the key. Users2 to user5 are using a passwordless key. Perhaps it's this?

:( :confused:

The command groups shows just Root even though I know I have created the admin and rusers groups.

I created admin with the following command:

"addgroup --system admin; echo "%admin ALL=(ALL) ALL" >> /etc/sudoers && adduser user1 admin"

& rusers was created with the "addgroup rusers" & all users were added to rusers group with "adduser userX rusers"

What do you think I've missed please?

---

### Post by cariboo on 2009-10-04
Have a look at this [this]("http://www.ssh.com/support/documentation/online/ssh/adminguide/32/Restricting_User_Logins.html") page, it may be of some help.

---

### Post by Lars Noodén on 2009-10-05
> **Badcam said:**
> OK.
"/etc/ssh/sshd_config line 87: Directive 'UsePAM' is not allowed within a Match block"


Match can only act upon a subset of sshd_config keywords:
[INDENT]AllowAgentForwarding, AllowTcpForwarding, Banner, ChrootDirectory, ForceCommand, GatewayPorts, GSSAPIAuthentication, HostbasedAuthentication, KbdInteractiveAuthentication, KerberosAuthentication, MaxAuthTries, MaxSessions, PasswordAuthentication, PermitEmptyPasswords, PermitOpen, PermitRootLogin, PubkeyAuthentication, RhostsRSAAuthentication, RSAAuthentication, X11DisplayOffset, X11Forwarding and X11UseLocalHost.[/INDENT]

UsePAM is not one of them.   Try putting the Match block at the very end of the config file.  

Which editor do you use?   To get to line 87, 
For vi, enter '87G'
For emacs, 'ESC-g-g87'
For nano or pico, 'ESC-g87' or 'CTRL-_87'

---

### Post by Badcam on 2009-10-05
OK. I think I have most of this resolved and hopefully just one issue left and that's the "/bin/bash: No such file or directory" problem when trying to login via puTTy.

I guess it's because I don't have /bin/bash directories set up in any of the user directories. They're all empty. Should I just create these directories, or is there something else I should be doing in order to get these directories established?

Thanks.

---

### Post by Lars Noodén on 2009-10-05
> **Badcam said:**
> OK.
The command groups shows just Root even though I know I have created the admin and rusers groups.


The program **groups** without any options will show the groups the current user is a member of.  So if you are logged in as root, then it will show the groups root is a member of.

```

# show group membership for some users
groups root;
groups user1;
groups user2;
groups user3;
groups user4;
groups user5;

# the same thing, with a fancier bash trick
groups root user{0,1,2,3,4}

```

---

### Post by Badcam on 2009-10-05
Wow, I'm so silly. Thanks.

I get these results, which I'm happy with:


root@sheevaplug:/# groups root
root sshusers
root@sheevaplug:/# groups user1
user1 user2 user3 user4 admin sshusers
root@sheevaplug:/# groups user2
user2 sshusers (and similar for user3 to user5).

---

### Post by Lars Noodén on 2009-10-05
> **Badcam said:**
> 
I guess it's because I don't have /bin/bash directories set up in any of the user directories. They're all empty. 


Ok.  I had assumed you wanted to use SFTP to work with the files to keep the server side as simple as possible.  AFAIK, PuTTY has SFTP support.  If not or if it is not nice enough, there is Filezilla.  

Otherwise, you get to populate the chroot directories with the various utilities (e.g.  bash, ls, cp, mv, rm, etc) and their dependent libraries.  

**ldd** will show which libraries are needed.  Once you have it working for one user, use tar to copy the set up to the other user accounts.  

```

$ ldd /bin/bash
        linux-vdso.so.1 =>  (0x00007fff24851000)
        libncurses.so.5 => /lib/libncurses.so.5 (0x00007ff7a3131000)
        libdl.so.2 => /lib/libdl.so.2 (0x00007ff7a2f2d000)
        libc.so.6 => /lib/libc.so.6 (0x00007ff7a2bbe000)
        /lib64/ld-linux-x86-64.so.2 (0x00007ff7a3374000)
$ mkdir /home/user2/lib/
$ cd /home/user2; ln -s lib lib64
$ cp /lib/libncurses.so.5 /home/user2/lib/libncurses.so.5
$ cp /lib/libdl.so.2 /home/user2/lib/libdl.so.2
$ cp /lib/libc.so.6 /home/user2/lib/libc.so.6
$ cp /lib64/ld-linux-x86-64.so.2 /home/user2/lib/lib64/ld-linux-x86-64.so.2

```

That was for bash.  The other programs would follow the same process.  I'm sure there must be a convenient script to do that in an automated manner, but didn't find it.

---

### Post by Badcam on 2009-10-05
Woahhhh Nelly!!! Brain Overload! Alert!

I'm sorry. All I've done so far is set up several users (2 to 5) whom I would like them to be able to use puTTy so that they can use my sheevaplug first as a transparent proxy server. I'd like user1 to be able to use the sheevaplug as a proxy server and to be able to do other things such as access and or backup files onto an attached external HD using SFTP & rsync. I'd like the other users to have very limited access ie proxy sever only.

I haven't created a "chroot prison" if that's what your chroot comment meant. I've just created users and the groups in a basic adduser/addgroup way.

So, from your post I gather I now have to set up user1 for instance with these "various utilities". What I'm not understanding is why? Is this some sort of standard setup that everyone has to do? I sorry, but I'm stumped.

---

### Post by Badcam on 2009-10-05
I found this thread:

[http://erdelynet.com/archive/ssh-l/2003-10/1958.html](http://erdelynet.com/archive/ssh-l/2003-10/1958.html)

which suggests that I may just need to modify the bash.exe permissions. Is this a possible solution? Or, is this not a good idea?

---

### Post by Lars Noodén on 2009-10-05
> **Badcam said:**
> Woahhhh Nelly!!! Brain Overload! Alert!

Sorry.   Leave chroot alone for at least a day or two.  Probably longer.  You probably don't need it.  

Now that you have the users and group memberships set, try instead using SFTP I mentioned to connect.  You have that option in [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) and in [Filezilla](http://filezilla-project.org/).  Will that give you the file access you need?

---

### Post by Lars Noodén on 2009-10-05
&#8659;

---

### Post by Lars Noodén on 2009-10-05
**[SIZE="7"]&#8658;[/SIZE]**  Again try using SFTP in [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) and in [Filezilla](http://filezilla-project.org/).  SFTP will be useful.  **[SIZE="7"]&#8656;[/SIZE]**

If you look at the root file system, say using **ls /** you see something like this:

[INDENT]
[FONT="Courier New"]afs   cdrom  home            lib         media  proc  selinux  tmp  vmlinuz
bin   dev    initrd.img      lib64       mnt    root  srv      usr  vmlinuz.old
boot  etc    initrd.img.old  lost+found  opt    sbin  sys      var[/FONT]
[/INDENT]

And you will see that the program **ls** is located somewhere in that root file system, so is the program **which**:
[INDENT][FONT="Courier New"]$ which ls
/bin/ls
$ which which
/usr/bin/which
[/FONT][/INDENT]

And I happen to have a directory on that filesystem called /var/chroot-test/ which looks like this:
[INDENT]
[FONT="Courier New"]
bin  dev  lib  lib64  usr  var
[/FONT]
[/INDENT]

And the directory /var/chroot-test/bin looks like this, containing a single program 'rbash':

[INDENT]
[FONT="Courier New"]
rbash
[/FONT]
[/INDENT]

chroot changes the apparent location of the root file system from / to something else.  

So if I chroot to /var/chroot-test/, then it and its contents are all that I see for a file system.  **ls** is not in /var/chroot-test, so it can't run if /var/chroot-test is the chroot jail

[INDENT]
[FONT="Courier New"]
sudo chroot /var/chroot-test/ /bin/rbash
$ ls
rbash: ls: command not found
[/FONT]
[/INDENT]

Now if I add **ls** using the [steps described above](steps described above) 

[INDENT]
[FONT="Courier New"]
# ldd /bin/ls
        linux-vdso.so.1 =>  (0x00007ffff0559000)
        librt.so.1 => /lib/librt.so.1 (0x00007fed85eaf000)
        libselinux.so.1 => /lib/libselinux.so.1 (0x00007fed85c91000)
        libacl.so.1 => /lib/libacl.so.1 (0x00007fed85a89000)
        libc.so.6 => /lib/libc.so.6 (0x00007fed8571a000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00007fed854fe000)
        /lib64/ld-linux-x86-64.so.2 (0x00007fed860b7000)
        libdl.so.2 => /lib/libdl.so.2 (0x00007fed852fa000)
        libattr.so.1 => /lib/libattr.so.1 (0x00007fed850f5000)
# cp -i /lib/librt.so.1 /var/chroot-test/lib/librt.so.1
# cp -i /lib/libselinux.so.1 /var/chroot-test/lib/libselinux.so.1
# cp -i /lib/libacl.so.1 /var/chroot-test/lib/libacl.so.1
# cp -i /lib/libc.so.6 /var/chroot-test/lib/libc.so.6
# cp -i /lib/libpthread.so.0 /var/chroot-test/lib/libpthread.so.0
# cp -i /lib/libattr.so.1 /var/chroot-test/lib/libattr.so.1
[/FONT]
[/INDENT]

then **ls** will run inside the jail.  Other programs, such as touch and find, are not there in the chroot jail until they too are added.

[INDENT]
[FONT="Courier New"]
# chroot /var/chroot-test/ /bin/rbashrbash-4.0
# ls
bin  dev  lib  lib64  usr  var
# touch
rbash: touch: command not found
# find
rbash: find: command not found
[/FONT]
[/INDENT]

to use chroot is to build a new system inside a subdirectory

---

### Post by Badcam on 2009-10-05
> **Lars Noodén said:**
> **[SIZE="7"]&#8658;[/SIZE]**  Again try using SFTP in [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) and in [Filezilla](http://filezilla-project.org/).  SFTP will be useful.  **[SIZE="7"]&#8656;[/SIZE]**

If you look at the root file system, say using **ls /** you see something like this:

[INDENT]
[FONT="Courier New"]afs   cdrom  home            lib         media  proc  selinux  tmp  vmlinuz
bin   dev    initrd.img      lib64       mnt    root  srv      usr  vmlinuz.old
boot  etc    initrd.img.old  lost+found  opt    sbin  sys      var[/FONT]
[/INDENT]

And you will see that the program **ls** is located somewhere in that root file system, so is the program **which**:
[INDENT][FONT="Courier New"]$ which ls
/bin/ls
$ which which
/usr/bin/which
[/FONT][/INDENT]

And I happen to have a directory on that filesystem called /var/chroot-test/ which looks like this:
[INDENT]
[FONT="Courier New"]
bin  dev  lib  lib64  usr  var
[/FONT]
[/INDENT]

And the directory /var/chroot-test/bin looks like this, containing a single program 'rbash':

[INDENT]
[FONT="Courier New"]
rbash
[/FONT]
[/INDENT]

chroot changes the apparent location of the root file system from / to something else.  

So if I chroot to /var/chroot-test/, then it and its contents are all that I see for a file system.  **ls** is not in /var/chroot-test, so it can't run if /var/chroot-test is the chroot jail

[INDENT]
[FONT="Courier New"]
sudo chroot /var/chroot-test/ /bin/rbash
$ ls
rbash: ls: command not found
[/FONT]
[/INDENT]




And now I realise what it is your showing me below here....and as per your bash example in the previous post:


> 
Now if I add **ls** using the [steps described above](steps described above) 

[INDENT]
[FONT="Courier New"]
# ldd /bin/ls
        linux-vdso.so.1 =>  (0x00007ffff0559000)
        librt.so.1 => /lib/librt.so.1 (0x00007fed85eaf000)
        libselinux.so.1 => /lib/libselinux.so.1 (0x00007fed85c91000)
        libacl.so.1 => /lib/libacl.so.1 (0x00007fed85a89000)
        libc.so.6 => /lib/libc.so.6 (0x00007fed8571a000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00007fed854fe000)
        /lib64/ld-linux-x86-64.so.2 (0x00007fed860b7000)
        libdl.so.2 => /lib/libdl.so.2 (0x00007fed852fa000)
        libattr.so.1 => /lib/libattr.so.1 (0x00007fed850f5000)
# cp -i /lib/librt.so.1 /var/chroot-test/lib/librt.so.1
# cp -i /lib/libselinux.so.1 /var/chroot-test/lib/libselinux.so.1
# cp -i /lib/libacl.so.1 /var/chroot-test/lib/libacl.so.1
# cp -i /lib/libc.so.6 /var/chroot-test/lib/libc.so.6
# cp -i /lib/libpthread.so.0 /var/chroot-test/lib/libpthread.so.0
# cp -i /lib/libattr.so.1 /var/chroot-test/lib/libattr.so.1
[/FONT]
[/INDENT]

then **ls** will run inside the jail.  Other programs, such as touch and find, are not there in the chroot jail until they too are added.

[INDENT]
[FONT="Courier New"]
# chroot /var/chroot-test/ /bin/rbashrbash-4.0
# ls
bin  dev  lib  lib64  usr  var
# touch
rbash: touch: command not found
# find
rbash: find: command not found
[/FONT]
[/INDENT]

to use chroot is to build a new system inside a subdirectory


It's amazing how taking a step back for a moment (well actually, a good nights sleep) can make you see things more clearly. I **actually** understand this  :shock:  :cool: 

Thanks for your patience Lars. So now:

1) If I create a /var/chroot-test/ directory (I'll use another name though), I assume that that one directory can be set up to be used by, say, users 1 through 5, but

2) How can I set that up for just users 2 through 5 only (not user1) and allow user1 to still have full access (ie sudo rights). Would I just create two versions of /var/chroot-test/ (chroot-test1 & chroot-test2)? Am I being clear?

3) Or, would the group permissions be sufficient? 

What I'm needing is for users2 to 5 to be able to login remotely and use this device purely as a transparent proxy server. But, I want user1 (which will be me) to be able to login in and manage the device, access it fully with sudo rights.

You've been a great help Lars and mighty patient with me.

(I won't have free time to trial this until tonight [11 hours time] but I'll wokr on it first chance I get. Brilliant!)

---

### Post by Lars Noodén on 2009-10-05
sudo (actually /etc/sudoers) is for access to running programs.

group permissions and membership would be for access to read or write files.

---

