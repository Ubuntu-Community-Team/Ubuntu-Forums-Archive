---
title: "HowTO: Sudoers Configuration"
date: 2009-04-22
forum: Tutorials
---

### Post by ibuclaw on 2009-04-22
[CENTER][IMG]http://justinsomnia.org/images/sudo-bang-bang.png[/IMG]
[COLOR="Sienna"][SIZE=6]**HowTO: Sudoers Configuration**[/SIZE][/CENTER]
[/COLOR]

For reference on how to setup your sudoers, I suggest you have a skim through this guide: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)
It may need a little work here or there (I should know, I wrote some bits of it), but should give you enough information to get some small things started.

This guide is aimed at giving a beginners transition into configuring sudo, and builds up the knowledge enough to tailor permissions for a basic multi-user system (ie: Family Computer).

Once you have a working understanding, it is always a good thing to get acquainted with the [sudoers manual]("http://www.gratisoft.us/sudo/man/sudoers.html") on the home site, which goes more indepth and more into the advanced and sometimes unneeded features of how to tweak the sudoers configuration.

[CENTER][COLOR="Sienna"][SIZE="5"]**The Scenario**[/SIZE][/COLOR][/CENTER]
Rather than just writing a listed guide or a sudoers cheatsheet, I thought it may be best if I'd use a practical element that most people will benefit from, and others will adapt to their own needs.

So here is the scenario. I use the following applications frequently that require my password in order to carry out administrative tasks:
[LIST]
[*]apt-get update
[*]apt-get upgrade
[*]gmount-iso
[*]gnome-format
[*]truecrypt
[*]unetbootin
[*]update-manager
[/LIST]
and with the somewhat persistent use of them, it can get very dia at times having to type out my password constantly in order to get my usual work done in them. So it would be nice if I could configure sudo to allow me to use these with less of a hassle. Well, fortunately you can!

[COLOR="Sienna"][SIZE="4"]**Enter /etc/sudoers**[/SIZE][/COLOR]
Everyone knows sudo, everyone knows how it works and when and where to use it. But there seems to be an unspoken art of configuring and setting it up for a multiuser domain, or for a single-user workstation.

But to give you the dropdown basics. Sudo's configuration file is located in /etc/sudoers. But due to the powerness of the program, we don't want to edit it directly in the event of a type error in file; so we use the program **visudo** instead. visudo is a program which makes a temporary copy of the sudoers file, and sanity checks it after you've finished editing it. If any errors are found, it then prompts you about it, and allows you to go back to fix that misconfigured line.

[COLOR="Sienna"][SIZE="4"]**Opening Sudoers**[/SIZE][/COLOR]
visudo, as of Intrepid, uses the sensible-editor to edit the sudoers file. So to ensure that sensible-editor is setup on your computer run:
```
sudo select-editor
```
And you'll be given a list of programs to choose from. In most cases, you'll want to choose **nano**. But other people prefer other editors such as vi, or emacs.

With that set, we are all ready to go, launch visudo.
```
sudo visudo
```
and you are in.

[COLOR="Sienna"][SIZE="4"]**Before we begin**[/SIZE][/COLOR]
There are some things that need explaining first before we start playing about with configuration:

**1)** The sudo binary is setuid root. This means that when any user runs sudo, they are instantly granted root permissions. The only thing stopping a user from using those root permissions for any use is the sudo application itself, which locks down very hard on access. From a security point of view, a sloppy configuration file that grants everything from everywhere root access can be seen as - and is - a **major risk to your system**.

**2)** Sudo reads the sudoers file and applies permissions in order from top to bottom. So the last line in the file will overwrite any previous conflict with the config settings. So it is best to put new configuration lines at the bottom.

**3)** Sudo has a sizeable list of Defaults that you can tweak/set. These are shown by running the following command
> sudo -L
By all means, you can look into them, but the only three I recommend you use are:
[LIST]
[*]env_reset - Reset the environment to a default set of variables
[*]tty_tickets - Use a separate timestamp for each user/tty combo
[*]timestamp_timeout - Authentication timestamp timeout
[/LIST]
The only one requiring arguments being timestamp_timeout:
```
Defaults:ALL timestamp_timeout=0
```
Which means that ALL users sudo permissions timeout immediately, meaning that they must enter their password every time they use sudo.

A softer usage would be:
```
Defaults:ALL timestamp_timeout=15
```
Where instead the timestamp is 15 minutes.
**Note:** Active timestamps can be removed at any time by running:
> sudo -K
This is can especially useful if you leave your computer **without locking it**!
Although I can't stress enough the enforcement of common practice, it is safer to deny intruders root access than it is to leave your workstation unlocked for anyone to walk up to/use.

**4)** For a huge multi-user system, it can sometimes be difficult to know just exactly what commands you have sudo access to, or whether or not your recent sudo tweak took effect in the way that you hoped.

To find out just exactly what sudo permissions you have on your computer, you would run the following
> sudo -l
That is "sudo" and a lowercase **L** as the argument.

OK! Now, with that out the way, lets look at our first line in the sudo configuration file.

[CENTER][COLOR="Sienna"][SIZE="5"]**Hello Configuration!**[/SIZE][/COLOR][/CENTER]
For example purposes, lets tweak the sudo permissions for **apt-get**.
Now, scroll to the bottom, and we can insert our line:
```
%admin ALL=(ALL)NOPASSWD:/usr/bin/apt-get
```
To break it down:
[LIST]
[*] **%admin** - All users of the admin group
[*] **ALL=**   - from any Host/IP
[*] **(ALL)** - can run as any user
[*] **NOPASSWD** - with no password required
[*] **:/usr/bin/apt-get** - the list of comma, separated, applications.
[/LIST]

[COLOR="Sienna"][SIZE="4"]**Fine Graining Permissions**[/SIZE][/COLOR]
Now, as quick and efficient this may be in most cases, it's not the best thing to do from a security point of view for a number of reasons:

**1. **Any connected computer can run the command, so long as they are logged in as one of the administrators. From a paranoid perspective, ideally we would rather only computers within our local host/network/subnet.

**2. **They can run the given command as any user. Which apt-get isn't intended for. (Although the argument is weak in this case, in some scenarios and with certain applications, you could be quite literally giving a key for a user to invade another user's private account if not careful).

**3. **Sometimes, we want the user only to be able to perform "**certain**" tasks of the application, and not all features.

**4. **In some circumstances, we only want **one user** to run a command, rather than all the users in the admin group.

Considering this list, you can make the following changes to it.

[COLOR="Sienna"][SIZE="4"]**Restrict Computers/Hosts**[/SIZE][/COLOR]
**Note:** This applies to computers running application services. If you connect to a machine via ssh, this does not apply.

There are two ways you can tackle this:

The first way is by using hostnames.
**Note:** This is my recommended way.

If you don't know what a hostname is, it is the name of a computer that identifies it on the network. You can find out what the hostname of your machine is by reading the name after the **@** symbol in the bash prompt.
ie: my prompt looks like this, 'jaunty' is my hostname.
> iain@**jaunty**:~$ 
Alternately, if your prompt doesn't show it, you can run in a terminal:
> cat /etc/hostname
To obtain the same information.

We can now change our resultant line so it now looks like this:
```
%admin **jaunty**=(ALL)NOPASSWD:/usr/bin/apt-get
```
So, as long as your hostname remains as 'jaunty', then you can run the sudo command from **only your computer**.

The second way is by using IP addresses.
**Note:** This requires for you to be connected to a network! Else you will be **denied access**
```
%admin **192.168.1.0/255.255.255.0**=(ALL)NOPASSWD:/usr/bin/apt-get
```
192.168.1.0 is the IP of your local network.
255.255.255.0 is the subnet of your local network.

So, in this instance, you are restricting the use of sudo only to users with an IP address of 192.168.1.1 through to 192.168.1.254

[COLOR="Sienna"][SIZE="4"]**Restricting User Switching**[/SIZE][/COLOR]
To run commands as another user (other than root), you would run the following:
> sudo -u **username** command
To prevent this from happening, you can restrict it by using:
```
%admin jaunty=**(root)**NOPASSWD:/usr/bin/apt-get
```
So now members of the admin group can only run the given commands without a password as root. Doesn't matter how hard they try otherwise. ;)

**Note:** if a previous permission is set so the user can run the command as any user.
More specifically this line that is the default in Ubuntu:
```
%admin ALL=(ALL) ALL
```
Then they will have to provide their own password to continue.

A more secure method:
```
%admin ALL=(root) ALL
```
Where they will be instead denied if they try to run an application as another user.

[COLOR="Sienna"][SIZE="4"]**Restricting Application Usage**[/SIZE][/COLOR]
As well, as limiting the applications a user can run using sudo, you can limit the arguments of those applications that the user can use also, for apps that do more than one job.

To limit apt-get usage to just 'update' and 'upgrade', we can have something like this:
```
%admin jaunty=(root)NOPASSWD:**/usr/bin/apt-get update,/usr/bin/apt-get upgrade**
```
And now everything other apt-get argument (install, remove, dist-upgrade) is denied!

Alternately, we can also use the glob match '*****'.
```
%admin jaunty=(root)NOPASSWD:**/usr/bin/apt-get up***
```
The '*****' match is very powerful, and can apply to anything in the command listing part of the configuration line, ie:
```
%admin jaunty=(root)NOPASSWD:/*/sbin/*
```
This could match anything from all the files in '/usr/sbin/' to '/usr/local/sbin/' and even places such as '/home/user/sbin/' fall into the match. As such, it is advised that you use it wisely.

[COLOR="Sienna"][SIZE="4"]**Restricting use of sudo to Single Users**[/SIZE][/COLOR]
As well as specifying groups, we can hand out sudo permissions on a 'per-user' basis too. For example, to only allow the user 'iain' (me) to run 'apt-get update' and 'apt-get upgrade', we use the following:
```
**iain** jaunty=(root)NOPASSWD:/usr/bin/apt-get update,/usr/bin/apt-get upgrade
```
**Note:** The difference between a user and a group. Groups have the '**%**' symbol prefixed against their name. So, to change this so only users in the group 'iain' can run 'apt-get', we simply add the '%' symbol:
```
**%iain** jaunty=(root)NOPASSWD:/usr/bin/apt-get update,/usr/bin/apt-get upgrade
```

[COLOR="Sienna"][SIZE="4"]**Restrict Applications**[/SIZE][/COLOR]
There is a hidden 5th that I forgot to mention. In some cases, you want to restrict the application once it has been given root powers.

ie: **vim**, **less** and some other similar applications can allow you to 'shell out' of the application and run commands using the **!** operator, as an example:
```
:!aptitude
```
The risk? If given the permissions to running vim as root, you can carry out any administrative task on the system. Which isn't very good if you just want certain users to run vim as root, but not any other command.

For this, we have the **NOEXEC** option, with will prevent the command from shelling out.
```
%admin ALL=(root)**NOEXEC**:/usr/bin/vim
```
Although, bare in mind that for the majority of applications, this isn't the best option for usability, since programs such as '**apt-get**' do indeed fork a shell to run applications such as **dpkg** and **wget**.

[CENTER][COLOR="Sienna"][SIZE="5"]**Hello Aliases!**[/SIZE][/COLOR][/CENTER]
Thus far, I have only been concentrating on one application, as from the above line, you can see that bare word configuration can get rather lengthy.
Luckily, the sudoers configuration file can handle variables, or **aliases** as they are called. There are four types, all to which will be covered in brief.

[COLOR="Sienna"][SIZE="4"]**Host Alias Specification**[/SIZE][/COLOR]
The host alias, are aliases for the addresses of the host computers to which the commands are ran from.
Host aliases are declared as so, to use my hostname as an example:
```
Host_Alias HOST = jaunty
```
If I were to alias the local network:
```
Host_Alias LAN = 192.168.1.0/255.255.255.0
```

[COLOR="Sienna"][SIZE="4"]**User Alias Specification**[/SIZE][/COLOR]
The user alias, are aliases for the usernames, or group names, this allows you to create a new group within the sudoers file, but not on the system.

Now, as an owner of a single user system, there is no need for me to go into this. But if you are interested, it works likes so:
```
User_Alias FUSE_USERS = andy,ellz,matt,jamie
```
The users andy, ellz, matt and jamie are - in this example - unprivileged users who are not in the fuse group, and as such, cannot mount/unmount loopback devices. But using the sudo configuration, you can allow them to grant root privileges to use an application that handles the loopback devices. So they have at least some control, but not full control.
A rudimentary line that would show this:
```
FUSE_USERS ALL=(root):/usr/bin/the-application
```

[COLOR="Sienna"][SIZE="4"]**RunAs Alias Specification**[/SIZE][/COLOR]
The runas alias, are aliases for the users you can sudo as, via the 'sudo -u' command. Again, I won't go into this, but it works like so:
```
Runas_Alias USERS = root,andy,ellz,matt,jamie
```
And put in the following context:
```
%admin  ALL=(USERS) ALL
```
Members of the admin group can run any command as any of the users enlisted in USERS.

[COLOR="Sienna"][SIZE="4"]**Command Alias Specification**[/SIZE][/COLOR]
And lastly, the command alias, as you may have guessed, are aliases for the command names. To skip any brief talk about them, lets first fufil what my original scenario intended.
```

Cmnd_Alias CRYPT   = /usr/bin/truecrypt
Cmnd_Alias USBDEV  = /usr/bin/unetbootin,/usr/bin/gnome-format
Cmnd_Alias APT     = /usr/bin/apt-get update,/usr/bin/apt-get upgrade
Cmnd_Alias UPDATES = /usr/bin/update-manager
Cmnd_Alias FUSE    = /usr/bin/Gmount-iso
Cmnd_Alias MYPROGS = CRYPT,USBDEV,APT,UPDATES,FUSE

```
Woah, that is alot. Infact, what I've done is split the applications into sub-groups, and shuffled those groups into one, MYPROGS.

[COLOR="Sienna"][SIZE="4"]**Gelling it together**[/SIZE][/COLOR]
With the above in place, we can now write out lines such as this:
```
iain HOME=(root)NOPASSWD:MYPROGS
```
Which result in a much cleaner, easier to maintain configuration.

[COLOR="Sienna"][SIZE="4"]**The Result**[/SIZE][/COLOR]
Put that all together, and we have something that looks like this:
```

Defaults    env_reset,tty_tickets

# Host alias specification
Host_Alias HOST = jaunty
Host_Alias LAN  = 192.168.1.0/255.255.255.0
Host_Alias HOME = HOST,LAN

# User alias specification

# Cmnd alias specification
Cmnd_Alias CRYPT   = /usr/bin/truecrypt
Cmnd_Alias USBDEV  = /usr/bin/unetbootin,/usr/bin/gnome-format
Cmnd_Alias APT     = /usr/bin/apt-get update,/usr/bin/apt-get upgrade
Cmnd_Alias UPDATES = /usr/bin/update-manager
Cmnd_Alias FUSE    = /usr/bin/Gmount-iso
Cmnd_Alias MYPROGS = CRYPT,USBDEV,APT,UPDATES,FUSE

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin HOME=(root) ALL
%admin HOME=(root) NOEXEC:/usr/bin/vim
iain   HOME=(root) NOPASSWD:MYPROGS

```

[CENTER][COLOR="Sienna"][SIZE="5"]**Conclusion**[/SIZE][/COLOR][/CENTER]
My resultant visudo file is fine as is to build/work on. But it may not be for everyone.

If you connect to your computer from outside your network, I recommend:
```
%admin ALL=(root)NOPASSWD:MYPROGS
```
But, if your company's/workstation's IP address is static, then you can set it as a Host_Alias to be more restrictive.

If you are - like me - on a machine where you are the only admin, and never login from remote. It's probably better to prevent all external computers from running sudo commands, and to specify your username instead.
For the paranoid:
```
iain HOST=(root)NOPASSWD:MYPROGS
```
NOTE: Use your username in place of 'iain', you don't want to give **me** access to your system. :twisted:

[COLOR="Red"]
[CENTER]**[SIZE="3"]Remember, as the user of your own system, you are advised to use your powers responsibly.[/SIZE]**[/CENTER][/COLOR]

Regards
Iain

---

### Post by lalada on 2009-04-23
Thank you. This is very useful...

---

### Post by ibuclaw on 2009-04-24
Right, I think this is near enough finished.

If you have any comments or questions, please ask.

If you notice something wrong, please tell!

[EDIT]
I think this HowTO needs some colour ... what do you guys/girls think to that?

Regards
Iain

---

### Post by sbsheetz on 2009-04-25
> **tinivole said:**
> Right, I think this is near enough finished.

If you have any comments or questions, please ask.

If you notice something wrong, please tell!

[EDIT]
I think this HowTO needs some colour ... what do you guys/girls think to that?

Regards
Iain

Iain,

This is a fantastic post.  I've wanted a deeper understanding of /etc/sudoers for a while now.  That this post is written in very understandable language was a tremendous benefit!

As for color, go for it.  Just don't change the content!

Best regards,
Steve

---

### Post by ibuclaw on 2009-04-25
> **sbsheetz said:**
> Iain,

This is a fantastic post.  I've wanted a deeper understanding of /etc/sudoers for a while now.  That this post is written in very understandable language was a tremendous benefit!

As for color, go for it.  Just don't change the content!

Best regards,
Steve

Thanks Steve, glad you liked it!

You will likely see the content change marginally, as I find grammar errors; as my needs change; as sudo get's upgraded to version 1.7.1, and I learn more about configuring it myself, this guide will slowly update and addon some small bits, pieces, and really nifty feature here and there.

Remember, anything you are unsure about, or you need clarifying on, just ask. ;)

Regards
Iain

---

### Post by acrane1 on 2009-04-30
hey, love the post. I am having some trouble though and was wondering if you could help. I am trying to make it so that when I do sudo mount I am not prompted for a password. This is what my visudo looks like


# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification
Host_Alias HOST = Crane3
# User alias specification

# Cmnd alias specification
Cmnd_Alias MYCMD = /usr/bin/mount
# User privilege specification
root    ALL=(ALL) ALL
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
acrane1 HOST=(root) NOPASSWD:MYCMD

any help would be greay thanks.

---

### Post by ibuclaw on 2009-05-01
> **acrane1 said:**
> hey, love the post. I am having some trouble though and was wondering if you could help. I am trying to make it so that when I do sudo mount I am not prompted for a password. This is what my visudo looks like


# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification
Host_Alias HOST = Crane3
# User alias specification

# Cmnd alias specification
Cmnd_Alias MYCMD = /usr/bin/mount
# User privilege specification
root    ALL=(ALL) ALL
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
acrane1 HOST=(root) NOPASSWD:MYCMD

any help would be greay thanks.
You can find out where the location of a file is by running
```
which **application**
```

For example:
```
which mount
```
Reveals that it is actually located in **/bin/mount** - not /usr/bin/mount as you have stated in your configuration. Also, it may be a good idea to include **umount** also, depending on what you intend to use mount for in the first place.
So, you would have instead:
```
Cmnd_Alias MYCMD = /bin/mount,/bin/umount
```
Paths locations are very important. ;)

Regards
Iain

---

### Post by acrane1 on 2009-05-01
tinivole, i tired /bin/mount and it didn't work, so thats why I tried usr/bin/mount just in case and that didn't work either, sorry should have mentioned that in the post.

---

### Post by ibuclaw on 2009-05-01
What is being displayed when you run the follow?
```
which mount
```
```
echo $USER
```
```
cat /etc/hostname
```

Regards
Iain

---

### Post by acrane1 on 2009-05-01
i get /bin/mount ; acrane1 ; and Crane3

---

### Post by ibuclaw on 2009-05-01
> **acrane1 said:**
> i get /bin/mount ; acrane1 ; and Crane3

Well, I get no problems using that combination, I would say that that may be because I use an upstream version of sudo, but I have my doubts.

Does it work when you tried out what was [originally suggested to you?]("http://ubuntuforums.org/showthread.php?p=7187928#post7187928")
```
Cmnd_Alias MYCMD=/bin/mount
acrane1 ALL=NOPASSWD: MYCMD
```

Also, what type of script are you using, and how are you running it?

Regards
Iain

---

### Post by acrane1 on 2009-05-01
No it doesn't work with the originally suggested code. The script section is 
#!/bin/sh
sudo mount /dev/sdf1 /media/Xtreme\ Drive
sudo mount /dev/sdc1 /media/Barracuda

The script works, it is being used as a start up script. When I run the script I am prompted for a password, once I type it in then they mount.

So from what I've shown you, my visudo file looks correct? and it should be working?

---

### Post by ibuclaw on 2009-05-02
> **acrane1 said:**
> No it doesn't work with the originally suggested code. The script section is 
#!/bin/sh
sudo mount /dev/sdf1 /media/Xtreme\ Drive
sudo mount /dev/sdc1 /media/Barracuda

The script works, it is being used as a start up script. When I run the script I am prompted for a password, once I type it in then they mount.

So from what I've shown you, my visudo file looks correct? and it should be working?
There should be no issue whatsoever.

Just ensure that the path is **/bin/mount** and the line that grants you permissions to execute it without a password is **at the very bottom** of the configuration file, and that should be it.

If you are certain that everything is right, post the output of:
```
sudo -l
```
if you are still having problems.

Regards
Iain

---

### Post by acrane1 on 2009-05-02
I get 
User acrane1 may run the following commands on this host:
    (ALL) ALL

---

### Post by ibuclaw on 2009-05-02
hmmm... that is definitely not set then. :)
only one way to find out for sure what is going on.
```
sudo cat /etc/sudoers
```

Regards
Iain

---

### Post by acrane1 on 2009-05-02
I edited my visudo to 
# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
acrane1 ALL=NOPASSWD:/bin/umount
acrane1 ALL=NOPASSWD:/bin/mount

now sudo -l outputs

User acrane1 may run the following commands on this host:
    (ALL) ALL
    (root) NOPASSWD: /bin/umount
    (root) NOPASSWD: /bin/mount

It is now working. Thanks for all your help

---

### Post by ibuclaw on 2009-05-02
Heh, thanks.

I suppose you ultimately figured it out yourself though, and that is what counts. ;)

---

### Post by rduke15 on 2009-06-25
Is it possible to restrict commands to specific paths?

I am looking for a way to allow users to chown and chmod certain files and directories, IF they are under a specific directory.

For example:

  ```
sudo chown -R -c :webmasters /docs/www
```

should be allowed. But NOT other directories like

  ```
sudo chown -R -c :users /etc
```

Is this possible with sudo?

Thanks.

---

### Post by ibuclaw on 2009-06-25
> **rduke15 said:**
> Is it possible to restrict commands to specific paths?

I am looking for a way to allow users to chown and chmod certain files and directories, IF they are under a specific directory.

For example:

  ```
sudo chown -R -c :webmasters /docs/www
```

should be allowed. But NOT other directories like

  ```
sudo chown -R -c :users /etc
```

Is this possible with sudo?

Thanks.
If I understand you correctly, I think this outside of the scope of what sudo can do. So I would have to say that no this is not possible using sudo.

To answer your problem, though, I would use Linux ACL (Access Control Lists) to do that sort of thing.

With access control lists, you can set permissions of files and directories on a "per user" or "per group" basis.

To implement it into your system, add "acl" to fstab, so it may look like the following:
```
UUID=b3d3d8f2  /  ext4  relatime,errors=remount-ro,**acl**  0  1
```
Then remount the partition:
```
sudo mount -o remount /
```
A simple application to set such permissions is **eiciel**
```
sudo apt-get install eiciel
```

If setup correctly, you do not need to use sudo to carry out what you want to do.

Regards
Iain

---

### Post by jarrah-95 on 2009-06-27
i have just actadently blocked all access to sudo exept for apt-get this whould have been alright for what i wanted to use update manager too and i also forgot to make a sudo user that can edit these things 
is there any way out of this
thanks

---

### Post by sisco311 on 2009-06-27
> **jarrah-95 said:**
> i have just actadently blocked all access to sudo exept for apt-get this whould have been alright for what i wanted to use update manager too and i also forgot to make a sudo user that can edit these things 
is there any way out of this
thanks
d'oh.


Boot in recovery mode and edit the file:
[http://www.psychocats.net/ubuntu/fixsudo]("http://www.psychocats.net/ubuntu/fixsudo")

---

### Post by jarrah-95 on 2009-06-27
thanks sisco311 your a life svaer

---

### Post by rduke15 on 2009-06-28
Thanks for the ACLs suggestion. In the meantime, I had found a simple workaround. In case it helps someone else:

I put the wanted chmod and chown lines into a shell script which is root:root and suid (4755/-rwsr-xr-x).

So users can run it to fix the permissions and ownership where I want, but cannot change the script to mess elsewhere in the system. Of course, the correct fix would be to find out why we get files in there with wrong permissions in the first place...

---

### Post by sisco311 on 2009-06-29
> **rduke15 said:**
> Thanks for the ACLs suggestion. In the meantime, I had found a simple workaround. In case it helps someone else:

I put the wanted chmod and chown lines into a shell script which is root:root and suid (4755/-rwsr-xr-x).

So users can run it to fix the permissions and ownership where I want, but cannot change the script to mess elsewhere in the system. Of course, the correct fix would be to find out why we get files in there with wrong permissions in the first place...

When a user creates a file the file inherits the users primary group ID. Setting the setgid permission on a directory causes new files and subdirectories created within it to inherit its group ID, rather than the primary group ID of the user who created the file.

i.e.
```
[sisco@acme xtmp]$ id sisco
uid=1000(sisco) **gid=100(users**) groups=100(users),6(disk),7(lp),10(wheel),91(video),92(audio),93(optical)
[sisco@acme xtmp]$ > file1
[sisco@acme xtmp]$ ls -al file1 
-rw-r--r-- 1 sisco **users** 0 2009-06-29 09:52 file1
[sisco@acme xtmp]$ mkdir dir1
[sisco@acme xtmp]$ > dir1/file2
[sisco@acme xtmp]$ ls -al dir1
total 8
drwxr-xr-x 2 sisco users 4096 2009-06-29 09:53 .
drwxr-xr-x 4 sisco users 4096 2009-06-29 09:52 ..
-rw-r--r-- 1 sisco users    0 2009-06-29 09:53 file2
[sisco@acme xtmp]$ **chmod g+s dir1**
[sisco@acme xtmp]$ **chgrp audio dir1/**
[sisco@acme xtmp]$ ls -al dir1
total 8
drwxr-sr-x 2 sisco **audio** 4096 2009-06-29 09:53 .
drwxr-xr-x 4 sisco users 4096 2009-06-29 09:52 ..
-rw-r--r-- 1 sisco users    0 2009-06-29 09:53 file2
[sisco@acme xtmp]$ > dir1/file3
[sisco@acme xtmp]$ ls -al dir1/
total 8
drwxr-sr-x 2 sisco audio 4096 2009-06-29 09:54 .
drwxr-xr-x 4 sisco users 4096 2009-06-29 09:52 ..
-rw-r--r-- 1 sisco users    0 2009-06-29 09:53 file2
-rw-r--r-- 1 sisco **audio**    0 2009-06-29 09:54 file3

```

---

### Post by erniej on 2010-01-11
Excellent, and very well stated. My immediate problem has been solved, thanks to another respondent, but I've bookmarked this for future reference after I'm more familiar with the lingo.

---

### Post by BobCFC on 2010-02-05
Thank you this is an excellent tutorial :D

Just to be clear, you still have to type sudo but it won't ask you for the password anymore

---

### Post by bapoumba on 2010-04-29
Ping ibuclaw: [http://ubuntuforums.org/showthread.php?t=1464729](http://ubuntuforums.org/showthread.php?t=1464729)
:KS

---

### Post by ibuclaw on 2010-05-01
Thanks bapoumba. :)

I suppose this will give me a reason to update / refactor a few bits and pieces of the guide then for Lucid. ;)

---

### Post by Penguin Guy on 2010-05-01
Nice How-To! I've used sudoers before but never fully understood it. The host-restriction tip is helpful, but instead of making an alias [FONT="Courier New"]Host_Alias HOST = jaunty[/FONT] and using [FONT="Courier New"]HOST=[/FONT], can't you just use [FONT="Courier New"]localhost=[/FONT]?

---

### Post by ibuclaw on 2010-05-01
> **Penguin Guy said:**
> Nice How-To! I've used sudoers before but never fully understood it. The host-restriction tip is helpful, but instead of making an alias [FONT="Courier New"]Host_Alias HOST = jaunty[/FONT] and using [FONT="Courier New"]HOST=[/FONT], can't you just use [FONT="Courier New"]localhost=[/FONT]?

Unless you've specified explicitly in /etc/hostname, localhost is not the hostname, localhost is just the alias to 127.0.0.1.

So no, that won't work.

Regards :)

---

### Post by Penguin Guy on 2010-05-02
> **ibuclaw said:**
> Unless you've specified explicitly in /etc/hostname, localhost is not the hostname, localhost is just the alias to 127.0.0.1.

So no, that won't work.

Regards :)
I know [FONT="Courier New"]localhost[/FONT] is an alias for [FONT="Courier New"]127.0.0.1[/FONT], but I don't see why [FONT="Courier New"]127.0.0.1[/FONT] wouldn't work in sudoers?

---

### Post by pradeeprajkumar on 2010-06-17
```
username HOST=(root)NOPASSWD:MYPROGS
```

When i tried this code it says,
> bash: syntax error near unexpected token `('
I'm using fedora 13 64 bit OS.
I run this command on kernel on an intension to grant all priveleges to the root user without password prompts.
Since I'm the only person to use my system i want no more password prompts while installing softwares or mounting hard disks.
What will be the optimal solution for this ?

---

### Post by ibuclaw on 2010-06-18
> **pradeeprajkumar said:**
> ```
username HOST=(root)NOPASSWD:MYPROGS
```

When i tried this code it says,

I'm using fedora 13 64 bit OS.
I run this command on kernel on an intension to grant all priveleges to the root user without password prompts.
Since I'm the only person to use my system i want no more password prompts while installing softwares or mounting hard disks.
What will be the optimal solution for this ?

Hmm... much to learn, you have. Hasty, you are. Perhaps reading the post from top down, and taking the time to understand it all, you must. Rather than skipping to the bits you are most interested in. :)

---

### Post by Penguin Guy on 2010-07-30
> **Penguin Guy said:**
> I know [FONT="Courier New"]localhost[/FONT] is an alias for [FONT="Courier New"]127.0.0.1[/FONT], but I don't see why [FONT="Courier New"]127.0.0.1[/FONT] wouldn't work in sudoers?
I finally understand the whole host thing after reading [this superuser answer]("http://superuser.com/questions/169278/localhost-in-sudoers#answer-169563").

---

### Post by AjAMz BoY on 2010-09-12
Very useful tutorial, thank you, ibuclaw!

---

### Post by Omnomnom on 2010-10-29
This is an interesting tut, cheers! I'll use this later :)

---

### Post by kerorolww on 2011-03-09
Dear Sir&#65306;
In the sudoers file, I have defined a User_Alias list and a Cmnd_Alias list as follows:
[I][B]User_Alias ADMINS = lee, vbird
Cmnd_Alias ADMINSCOM = !/usr/bin/passwd, /usr/bin/passwd [a-zA-Z]*, \
                                         !/usr/bin/passwd root
ADMINS ALL=(root) ADMINSCOM[/B][/I]

My problem is that the Cmnd_Alias ***ADMINSCOM*** didn't work. But if I replace ADMINSCOM with ***!/usr/bin/passwd***, it did work! 
Can you tell me why? Many Thanks!

---

### Post by tetchy_techie on 2011-03-09
Hi,

Thanks for the article - it made a lot more sense than the man pages! I have a question about the following paragraph:

[I]A more secure method:
%admin ALL=(root) ALL
Where they will be instead denied if they try to run an application as another user.[/I]

As I understand it, this will allow a member of the admin group to use sudo to invoke a command as root but not as any other user. This sounds like something we would definitely want to do, but my question is:
Could members of this group bypass this restriction by using sudo to invoke another shell (e.g. sudo xterm)? Because (on my system at least) that new shell launches as root. As root in the second shell you can then run su to become another user.

Thanks again.

---

### Post by realthor on 2011-05-26
Just wanted to say that this is one of the best written articles/how-tos on sudoers and sudo. I've been reading a ton of info just to remmember the stuff but for a bookmark I returned to this one, one of the first I've read today.

Good stuff, thank you.:popcorn:

---

### Post by count.zero on 2011-10-20
Hi Iain. This is indeed a very nice tutorial which got me started with the sudoers file a while ago. Now it's time for me to give some information back.

> The '*****' match is very powerful, and can apply to anything in the command listing part of the configuration line, ie:
     ```
%admin jaunty=(root)NOPASSWD:/*/sbin/* 
```This could match anything from all the files in '/usr/sbin/' to  '/usr/local/sbin/' and even places such as '/home/user/sbin/' fall into  the match. As such, it is advised that you use it wisely.I think you should add some information to this part of your tutorial, because */*/sbin/** could also become /etc/passwd. Let me show you the problem:

Here are the relevant part of my sudoers file:
```
Defaults        env_reset
# Host alias specification
Host_Alias HOST = eniac
Host_Alias LAN = 192.168.178.0/255.255.255.0
Host_Alias HOME = HOST,LAN

# Cmnd alias specification
Cmnd_Alias CHOWN_CMD    = /bin/chown zero /home/*

# User privilege specification
root    ALL=(ALL:ALL) ALL
zero HOME=(root) NOPASSWD:CHOWN_CMD
```Let me point out that i can only run the /bin/chown command as root:
```
0:zero@eniac:~$ sudo ls
Password:
Sorry, user zero is not allowed to execute '/bin/ls' as root on eniac.
1:zero@eniac:~$ 
```One would think that  since i got */home/** in my sudoers file, the use of the chown command is restricted to anything that is **below** /home/ 
Well, unfortunatelly that is **not** the case.

```
0:zero@eniac:~$ ls -l /etc/passwd
-rw-r--r-- 1 root root 531 Oct 12 20:51 /etc/passwd
0:zero@eniac:~$ sudo chown zero /home/../etc/passwd
0:zero@eniac:~$ ls -l /etc/passwd
-rw-r--r-- 1 [COLOR=Red]zero[/COLOR] root 531 Oct 12 20:51 /etc/passwd

```To prevent this, you will have to restrict the use of ".." in the argument.
```
Cmnd_Alias CHOWN_CMD    = /bin/chown zero /home/*,\
! /bin/chown zero *..*
```

---

### Post by rajesh.kalapura on 2011-10-20
Thanks for this tutorial..

---

### Post by Xantas on 2011-11-21
I'm trying to modify sudoers to allow a script to mount/umount windows shared folders without prompting for a password. 
But even if i carefully read all the how-to, untill the last post, i still can't mount any resource from the shell without sudo command. Here's my sudoers:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
www-data ALL= NOPASSWD: /sbin/reboot, /sbin/halt, /usr/sbin/faxdeluser -f *, /usr/sbin/faxadduser -f * -u * -p * *

#personalization
maxi ALL= NOPASSWD: /sbin/reboot, /sbin/halt, /bin/mount
#end personalization

```As you can see, to avoid any typo, i made a copy/paste of the line for the user www-data (added by avantfax, and it's working of course) and modified the new line for the user maxi, but nothing: it doesn't work. When i try a reboot or a mount it still says i need to be root user for that command. Everything seems to be right, here's the output for "sudo -l":
```
Matching Defaults entries for maxi on this host:
    env_reset

User maxi may run the following commands on this host:
    (ALL) ALL
    (root) NOPASSWD: /sbin/reboot, (root) /sbin/halt, (root) /bin/mount

```and of course i've even verified the path (which mount) and the user (echo $USER).
At this point i'm lost and don't know what to do more :(
Any suggestion?

---

### Post by canar on 2012-04-05
I've been through this thread ant can't really find the solution to my (simple) problem.
Here's what I'm trying to achieve:
As "canar" user I want to run a command, let's say "/opt/ocaml/bin/ocaml" as "duck" user

The only to achieve this is to give "canar" user root permission in sudoers, see below:
 [FONT=&quot]Host_Alias      LAB = [/FONT][FONT=&quot]linuxbox[/FONT]
  [FONT=&quot]User_Alias      LABTRUSTED = canar[/FONT]
  [FONT=&quot]Cmnd_Alias      LABADMIN = /bin/bash, /bin/su, /bin[/FONT]
  [FONT=&quot]LABTRUSTED       LAB=(ALL) NOPASSWD: LABADMIN[/FONT]
  
And run any command:
 [FONT=&quot]canar@linuxbox$ sudo -i -u duck  'id'[/FONT]


[FONT=&quot]But basically, this is a huge security hole since canar can run whatever he wants as anyone (including root)[/FONT]
[FONT=&quot]I want to restrict canar user to be able to login as duck user (or as anyone from a given group) without providing root access
[/FONT]
  
Any help would be welcome!
~canar

---

### Post by tripialos on 2012-04-08
Is it possible to add a command on sudoers with specific parameters?

for instance i would like to add iptables command with parameters 

-L -t nat -xvn to be executed for the user "testuser". I tried on visudo the following but it did not work:

```
testusr ALL=(ALL)NOPASSWD:/sbin/iptables -L -t nat -xvn
```

Got a syntax error. Any ideas if it is possible to add commands with arguments/parameters?

thanks

---

### Post by lulingar on 2012-04-15
Hello,

I have summarized the steps I had gone through in order to successfully add a set of rules to the sudoers configuration. You can see it [[COLOR="DimGray"]right here[/COLOR]]("http://luiseth.wordpress.com/2012/04/15/in-a-nutshell-add-permissions-with-configuration-files-in-etcsudoers-d/"). Enjoy!

---

### Post by feigoronin on 2012-05-17
Hi,

I am trying to give sudo login access(without having to enter password) to 'user1' so that it can login as 'user2' and run scripts, commands etc. I have made below entry in sudoers file

user1 ALL = (user2) NOPASSWD: ALL

This doesn't work and I still get prompted for password when I do(as user1)
sudo su - user2
But when I change sudoers file to:
user1 ALL = (ALL) NOPASSWD: ALL

it works. However, this also allows 'user1' to sudo login as super user without password, which I don't want. Can someone help me fix this.

Thanks.

---

### Post by CLWSI on 2013-01-03
I have joined my ubuntu desktop to my Server 2003 AD windows domain and I can successfully log in with domain credentials.

However domain users, and domain admins can not access sudo commands even with the following in the /etc/sudoer file

I followed sever guides and all of them show the following as acceptable code for giving domain admin/users  sudo ability.

Any ideas?

```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%clbei\\domain^admins ALL=(ALL) ALL
%clbei\\domain^users ALL=(ALL) ALL
```

---

### Post by ibuclaw on 2013-01-09
> **CLWSI said:**
> I have joined my ubuntu desktop to my Server 2003 AD windows domain and I can successfully log in with domain credentials.

However domain users, and domain admins can not access sudo commands even with the following in the /etc/sudoer file

I followed sever guides and all of them show the following as acceptable code for giving domain admin/users  sudo ability.

Any ideas?

```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%clbei\\domain^admins ALL=(ALL) ALL
%clbei\\domain^users ALL=(ALL) ALL
```

What's the output if you run 'id' on the domain user account?

eg:
```
id clbei\\ibuclaw
```

Regards

---

### Post by CLWSI on 2013-01-09
> **ibuclaw said:**
> What's the output if you run 'id' on the domain user account?

eg:
```
id clbei\\ibuclaw
```Regards

I ran the command several ways, all with the same type of result. It appears to pull my user groups correctly from the DC.

```
uid=1587545172(jasonladmin) gid=1587544577(domain^users) groups=1587544577(domain^users),1587545199(certsvc_dcom_access),1587545333(tatemusers),1587545394(vpn^users),1587546501(sqlserver2005mssqluser$moe$tcm),1587544576(domain^admins),1587545212(wo_po),1587545213(front),1587546508(sqlserver2005sqlbrowseruser$moe),1587546510(sqlserver2005mssqluser$moe$mssqlserver),1587544582(schema^admins),1587544583(enterprise^admins),1587545500(exchange^public^folder^administrators),1587545721(tcm),1587545190(exchange^organization^administrators),1587545191(exchange^recipient^administrators),1587545192(exchange^view-only^administrators)
jasonladmin@schemp:~$ 


```Please advise and thank you!

---

### Post by Reeload69 on 2013-06-29
I'm coming back to this tutorial for the third time already. Thanks, it's great. You made me make an account on the forums ;)

---

### Post by montu5742 on 2013-07-17
Really well writte...Many thanks to author...Cheers

---

