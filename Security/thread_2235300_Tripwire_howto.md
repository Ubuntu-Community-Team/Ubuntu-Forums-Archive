---
title: "Tripwire howto"
date: 2014-07-20
forum: Security
---

### Post by patrikmellq on 2014-07-20
.

First i want to say thank you to the member Gyokuro on this forum board, who help me to understand and support me to install Tripwire.

[B]TRIPWIRE

[/B]Tripwire is a "intrusion detection system" ... this means that Tripwire don't prevent an intrusion, but it will notice it has happen.
It works like this; Tripwire sign each file with a specific algorithm or key on your operating system and save all the information on a database.
So if some one change of modifie any file, then Tripwire will notice this, so no one can break into your computer without you being aware of that.

**THE FIRST PART OF THE INSTALLATION**

First you need to have a new installation from scratch, so you know that your operating system has not been temporized with.
You install your Ubuntu without internet connection.


When you have your system up running you can activate your firewall - ufw.

```

sudo ufw enable

``` 

Now you can connect to internet and install Tripwire.

```

sudo apt-get update

```

```

sudo apt-get install tripwire

```

Now when you run Tripwire installation it will ask you at the beginning to configuration email option.
Then you should pick "internetsystem" ...

[IMG]http://i59.tinypic.com/23sgqw7.jpg[/IMG] 

After that it will ask you to add what kind of email you use.
Like hotmail.com or gmail.com

[IMG]http://i59.tinypic.com/2ilh8bk.jpg[/IMG]

After this Tripwire will ask you if you want to install two secure keys.
The site key and the local key.

You should answer yes and continue doing so true the hole installation process.
It is a good idea if you have prepared your self with two good key phrases.

---

### Post by patrikmellq on 2014-07-20
[B]THE SECOND PART OF THE INSTALLATION

[/B]Now you have install the Tripwire process.
So now you need to install the Tripwire database.

Write the following code to install the database.

```

sudo tripwire --init

```

In the end of the installation process of the database you should have seen error messages.
That was files that did not match your operating system.

Now you want to change and modifies Tripwire so it match your Ubuntu system 100%
It does not do that by default.

So now we will create a file that show us what kind of error messages we got when we install the Tripwire database.
We create a file with the name "test_results"

Type the following code:

```

sudo sh -c 'tripwire --check | grep Filename > test_results'

```

You will find the file in your home directory or at /etc/tripwire
Just click on the "test_results" file and it will open up with gedit by default.

This is how the file looks like:

```

  Filename: /etc/rc.boot
     Filename: /root/mail
     Filename: /root/Mail
     Filename: /root/.xsession-errors
     Filename: /root/.xauth
     Filename: /root/.tcshrc
     Filename: /root/.sawfish
     Filename: /root/.pinerc
     Filename: /root/.mc
     Filename: /root/.gnome_private
     Filename: /root/.gnome-desktop
     Filename: /root/.gnome
     Filename: /root/.esd_auth
     Filename: /root/.elm
     Filename: /root/.cshrc
     Filename: /root/.bash_profile
     Filename: /root/.bash_logout
     Filename: /root/.bash_history
     Filename: /root/.amandahosts
     Filename: /root/.addressbook.lu
     Filename: /root/.addressbook
     Filename: /root/.Xresources
     Filename: /root/.Xauthority
     Filename: /root/.ICEauthority
     Filename: /proc/4116/fd/3
     Filename: /proc/4116/fdinfo/3
     Filename: /proc/4116/task/4116/fd/3
     Filename: /proc/4116/task/4116/fdinfo/3

```

All this files gave you error messages when you install the Tripwire database.
Now we will remove this error messages from our Tripwire configuration.

To do that we have to open a file with the name twpol.txt
And we have to open the file using Nano

With Nano you only need to know two commands.
"ctrl o" and Enter save changes and "ctrl x" close the editor.

Now we will open the twpol.txt file that is the blue print for Tripwire - it is the file that control what files Tripwire should check.
You open the policy file writing following code:

```

sudo nano /etc/tripwire/twpol.txt

```

This is how the file look like:

```

  
 # 
 # Standard Debian Tripwire configuration 
 # 
 # 
 # This configuration covers the contents of all 'Essential: yes' 
 # packages along with any packages necessary for access to an internet 
 # or system availability, e.g. name services, mail services, PCMCIA 
 # support, RAID support, and backup/restore support. 
 # 
  
 # 
 # Global Variable Definitions 
 # 
 # These definitions override those in to configuration file.  Do not          
 # change them unless you understand what you're doing. 
 # 
  
 @@section GLOBAL 
 TWBIN = /usr/sbin; 
 TWETC = /etc/tripwire; 
 TWVAR = /var/lib/tripwire; 
  
 # 
 # File System Definitions 
 # 
 @@section FS 
  
 # 
 # First, some variables to make configuration easier 
 # 
 SEC_CRIT      = $(IgnoreNone)-SHa ; # Critical files that cannot change 
  
 SEC_BIN       = $(ReadOnly) ;        # Binaries that should not change 
  
 SEC_CONFIG    = $(Dynamic) ;         # Config files that are changed 
           # infrequently but accessed 
           # often 
  
 SEC_LOG       = $(Growing) ;         # Files that grow, but that 
                 # should never change ownership 
  
 SEC_INVARIANT = +tpug ;              # Directories that should never 
           # change permission or ownership 
  
 SIG_LOW       = 33 ;                 # Non-critical files that are of 
          # minimal security impact 
  
 SIG_MED       = 66 ;                 # Non-critical files that are of 
          # significant security impact 
  
 SIG_HI        = 100 ;                # Critical files that are 
          # significant points of 
          # vulnerability 
  
 # 
 # Tripwire Binaries 
 # 
 ( 
   rulename = "Tripwire Binaries", 
   severity = $(SIG_HI) 
 ) 
 { 
  $(TWBIN)/siggen   -> $(SEC_BIN) ; 
  $(TWBIN)/tripwire  -> $(SEC_BIN) ; 
  $(TWBIN)/twadmin  -> $(SEC_BIN) ; 
  $(TWBIN)/twprint  -> $(SEC_BIN) ; 
 } 
  
 # 
 # Tripwire Data Files - Configuration Files, Policy Files, Keys, 
 # Reports, Databases 
 # 
  
 # NOTE: We remove the inode attribute because when Tripwire creates a 
 # backup, it does so by renaming the old file and creating a new one 
 # (which will have a new inode number).  Inode is left turned on for 
 # keys, which shouldn't ever change. 
  
 # NOTE: The first integrity check triggers this rule and each 
 # integrity check afterward triggers this rule until a database update 
 # is run, since the database file does not exist before that point. 
 ( 
   rulename = "Tripwire Data Files", 
   severity = $(SIG_HI) 
 ) 
 { 
  $(TWVAR)/$(HOSTNAME).twd -> $(SEC_CONFIG) -i ; 
  $(TWETC)/tw.pol   -> $(SEC_BIN) -i ; 
  $(TWETC)/tw.cfg   -> $(SEC_BIN) -i ; 
  $(TWETC)/$(HOSTNAME)-local.key -> $(SEC_BIN) ; 
  $(TWETC)/site.key  -> $(SEC_BIN) ; 
  
  #don't scan the individual reports 
  $(TWVAR)/report   -> $(SEC_CONFIG) (recurse=0) ; 
 } 
  
 # 
 # Critical System Boot Files 
 # These files are critical to a correct system boot. 
 # 
 ( 
   rulename = "Critical system boot files", 
   severity = $(SIG_HI) 
 ) 
 { 
  /boot   -> $(SEC_CRIT) ; 
  /lib/modules  -> $(SEC_CRIT) ; 
 } 
  
 ( 
   rulename = "Boot Scripts", 
   severity = $(SIG_HI) 
 ) 
 { 
  /etc/init.d  -> $(SEC_BIN) ; 
  /etc/rc.boot  -> $(SEC_BIN) ; 
  /etc/rcS.d  -> $(SEC_BIN) ; 
  /etc/rc0.d  -> $(SEC_BIN) ; 
  /etc/rc1.d  -> $(SEC_BIN) ; 
  /etc/rc2.d  -> $(SEC_BIN) ; 
  /etc/rc3.d  -> $(SEC_BIN) ; 
  /etc/rc4.d  -> $(SEC_BIN) ; 
  /etc/rc5.d  -> $(SEC_BIN) ; 
  /etc/rc6.d  -> $(SEC_BIN) ; 
 } 
  
  
 # 
 # Critical executables 
 # 
 ( 
   rulename = "Root file-system executables", 
   severity = $(SIG_HI) 
 ) 
 { 
  /bin   -> $(SEC_BIN) ; 
  /sbin   -> $(SEC_BIN) ; 
 } 
  
 # 
 # Critical Libraries 
 # 
 ( 
   rulename = "Root file-system libraries", 
   severity = $(SIG_HI) 
 ) 
 { 
  /lib   -> $(SEC_BIN) ; 
 } 
  
  
 # 
 # Login and Privilege Raising Programs 
 # 
 ( 
   rulename = "Security Control", 
   severity = $(SIG_MED) 
 ) 
 { 
  /etc/passwd  -> $(SEC_CONFIG) ; 
  /etc/shadow  -> $(SEC_CONFIG) ; 
 } 
  
  
  
  
 # 
 # These files change every time the system boots 
 # 
 ( 
   rulename = "System boot changes", 
   severity = $(SIG_HI) 
 ) 
 { 
  /var/lock  -> $(SEC_CONFIG) ; 
  /var/run  -> $(SEC_CONFIG) ; # daemon PIDs 
  /var/log  -> $(SEC_CONFIG) ; 
 } 
  
 # These files change the behavior of the root account 
 ( 
   rulename = "Root config files", 
   severity = 100 
 ) 
 { 
  /root    -> $(SEC_CRIT) ; # Catch all additions to /root 
  /root/mail   -> $(SEC_CONFIG) ; 
  /root/Mail   -> $(SEC_CONFIG) ; 
  /root/.xsession-errors  -> $(SEC_CONFIG) ; 
  /root/.xauth   -> $(SEC_CONFIG) ; 
  /root/.tcshrc   -> $(SEC_CONFIG) ; 
  /root/.sawfish   -> $(SEC_CONFIG) ; 
  /root/.pinerc   -> $(SEC_CONFIG) ; 
  /root/.mc   -> $(SEC_CONFIG) ; 
  /root/.gnome_private  -> $(SEC_CONFIG) ; 
  /root/.gnome-desktop  -> $(SEC_CONFIG) ; 
  /root/.gnome   -> $(SEC_CONFIG) ; 
  /root/.esd_auth   -> $(SEC_CONFIG) ; 
  /root/.elm   -> $(SEC_CONFIG) ; 
  /root/.cshrc          -> $(SEC_CONFIG) ; 
  /root/.bashrc   -> $(SEC_CONFIG) ; 
  /root/.bash_profile  -> $(SEC_CONFIG) ; 
  /root/.bash_logout  -> $(SEC_CONFIG) ; 
  /root/.bash_history  -> $(SEC_CONFIG) ; 
  /root/.amandahosts  -> $(SEC_CONFIG) ; 
  /root/.addressbook.lu  -> $(SEC_CONFIG) ; 
  /root/.addressbook  -> $(SEC_CONFIG) ; 
  /root/.Xresources  -> $(SEC_CONFIG) ; 
  /root/.Xauthority  -> $(SEC_CONFIG) -i ; # Changes Inode number on login 
  /root/.ICEauthority      -> $(SEC_CONFIG) ; 
 } 
  
 # 
 # Critical devices 
 # 
 ( 
   rulename = "Devices & Kernel information", 
   severity = $(SIG_HI), 
 ) 
 { 
  /dev  -> $(Device) ; 
  /proc  -> $(Device) ; 
 } 
  
 # 
 # Other configuration files 
 # 
 ( 
   rulename = "Other configuration files", 
   severity = $(SIG_MED) 
 ) 
 { 
  /etc  -> $(SEC_BIN) ; 
 } 
  
 # 
 # Binaries 
 # 
 ( 
   rulename = "Other binaries", 
   severity = $(SIG_MED) 
 ) 
 { 
  /usr/local/sbin -> $(SEC_BIN) ; 
  /usr/local/bin -> $(SEC_BIN) ; 
  /usr/sbin -> $(SEC_BIN) ; 
  /usr/bin -> $(SEC_BIN) ; 
 } 
  
 # 
 # Libraries 
 # 
 ( 
   rulename = "Other libraries", 
   severity = $(SIG_MED) 
 ) 
 { 
  /usr/local/lib -> $(SEC_BIN) ; 
  /usr/lib -> $(SEC_BIN) ; 
 } 
  
 # 
 # Commonly accessed directories that should remain static with regards 
 # to owner and group 
 # 
 ( 
   rulename = "Invariant Directories", 
   severity = $(SIG_MED) 
 ) 
 { 
  /  -> $(SEC_INVARIANT) (recurse = 0) ; 
  /home  -> $(SEC_INVARIANT) (recurse = 0) ; 
  /tmp  -> $(SEC_INVARIANT) (recurse = 0) ; 
  /usr  -> $(SEC_INVARIANT) (recurse = 0) ; 
  /var  -> $(SEC_INVARIANT) (recurse = 0) ; 
  /var/tmp -> $(SEC_INVARIANT) (recurse = 0) ; 
 }

```

Here above can you see the rules that Tripwire follows to check your system.
Now we want to change and modify this file.

You have to comment out the files/rules that you don't need with a # sign.
You put the # sign in front of each line you don't need.

So now we can look at our "test_reults" file and comment out all does filenames with the twpol.txt file.
This is how it looks like when you comment out the files with # sign.

```

{
    /root                -> $(SEC_CRIT) ; # Catch all additions to /root
    #/root/mail            -> $(SEC_CONFIG) ;
    #/root/Mail            -> $(SEC_CONFIG) ;
    #/root/.xsession-errors        -> $(SEC_CONFIG) ;
    #/root/.xauth            -> $(SEC_CONFIG) ;
    #/root/.tcshrc            -> $(SEC_CONFIG) ;
    #/root/.sawfish            -> $(SEC_CONFIG) ;
    #/root/.pinerc            -> $(SEC_CONFIG) ;
    #/root/.mc            -> $(SEC_CONFIG) ;
    #/root/.gnome_private        -> $(SEC_CONFIG) ;
    #/root/.gnome-desktop        -> $(SEC_CONFIG) ;
    #/root/.gnome            -> $(SEC_CONFIG) ;
    #/root/.esd_auth            -> $(SEC_CONFIG) ;
    #/root/.elm            -> $(SEC_CONFIG) ;
    #/root/.cshrc                -> $(SEC_CONFIG) ;
    /root/.bashrc            -> $(SEC_CONFIG) ;
    #/root/.bash_profile        -> $(SEC_CONFIG) ;
    #/root/.bash_logout        -> $(SEC_CONFIG) ;
    #/root/.bash_history        -> $(SEC_CONFIG) ;
    #/root/.amandahosts        -> $(SEC_CONFIG) ;
    #/root/.addressbook.lu        -> $(SEC_CONFIG) ;
    #/root/.addressbook        -> $(SEC_CONFIG) ;
    #/root/.Xresources        -> $(SEC_CONFIG) ;
    #/root/.Xauthority        -> $(SEC_CONFIG) -i ; # Changes Inode number on login
    #/root/.ICEauthority            -> $(SEC_CONFIG) ;

```

Next you should continue comment out files.
In the "Boot Scripts" section so do you have /etc/rc.boot
This file does not exist on Ubuntu system
So you comment out that file.

```

(
  rulename = "Boot Scripts",
  severity = $(SIG_HI)
)
{
    /etc/init.d        -> $(SEC_BIN) ;
    #/etc/rc.boot        -> $(SEC_BIN) ;
    /etc/rcS.d        -> $(SEC_BIN) ;
    /etc/rc0.d        -> $(SEC_BIN) ;
    /etc/rc1.d        -> $(SEC_BIN) ;
    /etc/rc2.d        -> $(SEC_BIN) ;
    /etc/rc3.d        -> $(SEC_BIN) ;
    /etc/rc4.d        -> $(SEC_BIN) ;
    /etc/rc5.d        -> $(SEC_BIN) ;
    /etc/rc6.d        -> $(SEC_BIN) ;
}

```

There is more ...
The /proc file should you comment out because it does give allot or error messages for no reason at all.
But you should also add some specific /proc files that the system need to check.

This is how it should look like:

```

{
        /dev                    -> $(Device) ;
        #/proc                  -> $(Device) ;
        /proc/devices           -> $(Device) ;
        /proc/net               -> $(Device) ;
        /proc/tty               -> $(Device) ;
        /proc/sys               -> $(Device) ;
        /proc/cpuinfo           -> $(Device) ;
        /proc/modules           -> $(Device) ;
        /proc/mounts            -> $(Device) ;
        /proc/dma               -> $(Device) ;
        /proc/filesystems       -> $(Device) ;
        /proc/interrupts        -> $(Device) ;
        /proc/ioports           -> $(Device) ;
        /proc/scsi              -> $(Device) ;
        /proc/kcore             -> $(Device) ;
        /proc/self              -> $(Device) ;
        /proc/kmsg              -> $(Device) ;
        /proc/stat              -> $(Device) ;
        /proc/loadavg           -> $(Device) ;
        /proc/uptime            -> $(Device) ;
        /proc/locks             -> $(Device) ;
        /proc/meminfo           -> $(Device) ;
        /proc/misc              -> $(Device) ;
}

```

Now you have a file-system that not get notice with the system and you have to add it.
/dev/pts

```

{
    /dev        -> $(Device) ;
    /dev/pts    -> $(Device) ;
    #/proc        -> $(Device) ;
    /proc/devices    -> $(Device) ;
    /proc/net    -> $(Device) ;
    /proc/tty    -> $(Device) ;
    /proc/sys    -> $(Device) ;

```

At last we will comment out some common /var location to avoid unnecessary error messages.

```

)
{
    #/var/lock        -> $(SEC_CONFIG) ;
    #/var/run        -> $(SEC_CONFIG) ; # daemon PIDs
    /var/log        -> $(SEC_CONFIG) ;
}

```

Now you can save all changes with Nano - type "ctrl o" and Enter.
Close Nano with "ctrl x"

This is how the tailored blue print for the Tripwire database should look like:
You can open the file twpol.txt writing following command:

```

sudo nano /etc/tripwire/twpol.txt

```

```

#
# Standard Debian Tripwire configuration
#
#
# This configuration covers the contents of all 'Essential: yes'
# packages along with any packages necessary for access to an internet
# or system availability, e.g. name services, mail services, PCMCIA
# support, RAID support, and backup/restore support.
#
#
# Global Variable Definitions
#
# These definitions override those in to configuration file.  Do not         
# change them unless you understand what you're doing.
#
@@section GLOBAL
TWBIN = /usr/sbin;
TWETC = /etc/tripwire;
TWVAR = /var/lib/tripwire;
#
# File System Definitions
#
@@section FS
#
# First, some variables to make configuration easier
#
SEC_CRIT      = $(IgnoreNone)-SHa ; # Critical files that cannot change
SEC_BIN       = $(ReadOnly) ;        # Binaries that should not change
SEC_CONFIG    = $(Dynamic) ;         # Config files that are changed
                # infrequently but accessed
                # often
SEC_LOG       = $(Growing) ;         # Files that grow, but that
                         # should never change ownership
SEC_INVARIANT = +tpug ;              # Directories that should never
                # change permission or ownership
SIG_LOW       = 33 ;                 # Non-critical files that are of
                     # minimal security impact
SIG_MED       = 66 ;                 # Non-critical files that are of
                     # significant security impact
SIG_HI        = 100 ;                # Critical files that are
                     # significant points of
                     # vulnerability
#
# Tripwire Binaries
#
(
  rulename = "Tripwire Binaries",
  severity = $(SIG_HI)
)
{
    $(TWBIN)/siggen            -> $(SEC_BIN) ;
    $(TWBIN)/tripwire        -> $(SEC_BIN) ;
    $(TWBIN)/twadmin        -> $(SEC_BIN) ;
    $(TWBIN)/twprint        -> $(SEC_BIN) ;
}
#
# Tripwire Data Files - Configuration Files, Policy Files, Keys,
# Reports, Databases
#
# NOTE: We remove the inode attribute because when Tripwire creates a
# backup, it does so by renaming the old file and creating a new one
# (which will have a new inode number).  Inode is left turned on for
# keys, which shouldn't ever change.
# NOTE: The first integrity check triggers this rule and each
# integrity check afterward triggers this rule until a database update
# is run, since the database file does not exist before that point.
(
  rulename = "Tripwire Data Files",
  severity = $(SIG_HI)
)
{
    $(TWVAR)/$(HOSTNAME).twd    -> $(SEC_CONFIG) -i ;
    $(TWETC)/tw.pol            -> $(SEC_BIN) -i ;
    $(TWETC)/tw.cfg            -> $(SEC_BIN) -i ;
    $(TWETC)/$(HOSTNAME)-local.key    -> $(SEC_BIN) ;
    $(TWETC)/site.key        -> $(SEC_BIN) ;
    #don't scan the individual reports
    $(TWVAR)/report            -> $(SEC_CONFIG) (recurse=0) ;
}
#
# Critical System Boot Files
# These files are critical to a correct system boot.
#
(
  rulename = "Critical system boot files",
  severity = $(SIG_HI)
)
{
    /boot            -> $(SEC_CRIT) ;
    /lib/modules        -> $(SEC_CRIT) ;
}
(
  rulename = "Boot Scripts",
  severity = $(SIG_HI)
)
{
    /etc/init.d        -> $(SEC_BIN) ;
    #/etc/rc.boot        -> $(SEC_BIN) ;
    /etc/rcS.d        -> $(SEC_BIN) ;
    /etc/rc0.d        -> $(SEC_BIN) ;
    /etc/rc1.d        -> $(SEC_BIN) ;
    /etc/rc2.d        -> $(SEC_BIN) ;
    /etc/rc3.d        -> $(SEC_BIN) ;
    /etc/rc4.d        -> $(SEC_BIN) ;
    /etc/rc5.d        -> $(SEC_BIN) ;
    /etc/rc6.d        -> $(SEC_BIN) ;
}

#
# Critical executables
#
(
  rulename = "Root file-system executables",
  severity = $(SIG_HI)
)
{
    /bin            -> $(SEC_BIN) ;
    /sbin            -> $(SEC_BIN) ;
}
#
# Critical Libraries
#
(
  rulename = "Root file-system libraries",
  severity = $(SIG_HI)
)
{
    /lib            -> $(SEC_BIN) ;
}

#
# Login and Privilege Raising Programs
#
(
  rulename = "Security Control",
  severity = $(SIG_MED)
)
{
    /etc/passwd        -> $(SEC_CONFIG) ;
    /etc/shadow        -> $(SEC_CONFIG) ;
}
 

#
# These files change every time the system boots
#
(
  rulename = "System boot changes",
  severity = $(SIG_HI)
)
{
    #/var/lock        -> $(SEC_CONFIG) ;
    #/var/run        -> $(SEC_CONFIG) ; # daemon PIDs
    /var/log        -> $(SEC_CONFIG) ;
}
# These files change the behavior of the root account
(
  rulename = "Root config files",
  severity = 100
)
{
    /root                -> $(SEC_CRIT) ; # Catch all additions to /root
    #/root/mail            -> $(SEC_CONFIG) ;
    #/root/Mail            -> $(SEC_CONFIG) ;
    #/root/.xsession-errors        -> $(SEC_CONFIG) ;
    #/root/.xauth            -> $(SEC_CONFIG) ;
    #/root/.tcshrc            -> $(SEC_CONFIG) ;
    #/root/.sawfish            -> $(SEC_CONFIG) ;
    #/root/.pinerc            -> $(SEC_CONFIG) ;
    #/root/.mc            -> $(SEC_CONFIG) ;
    #/root/.gnome_private        -> $(SEC_CONFIG) ;
    #/root/.gnome-desktop        -> $(SEC_CONFIG) ;
    #/root/.gnome            -> $(SEC_CONFIG) ;
    #/root/.esd_auth            -> $(SEC_CONFIG) ;
    #/root/.elm            -> $(SEC_CONFIG) ;
    #/root/.cshrc                -> $(SEC_CONFIG) ;
    /root/.bashrc            -> $(SEC_CONFIG) ;
    #/root/.bash_profile        -> $(SEC_CONFIG) ;
    #/root/.bash_logout        -> $(SEC_CONFIG) ;
    #/root/.bash_history        -> $(SEC_CONFIG) ;
    #/root/.amandahosts        -> $(SEC_CONFIG) ;
    #/root/.addressbook.lu        -> $(SEC_CONFIG) ;
    #/root/.addressbook        -> $(SEC_CONFIG) ;
    #/root/.Xresources        -> $(SEC_CONFIG) ;
    #/root/.Xauthority        -> $(SEC_CONFIG) -i ; # Changes Inode number on login
    #/root/.ICEauthority            -> $(SEC_CONFIG) ;
}
#
# Critical devices
#
(
  rulename = "Devices & Kernel information",
  severity = $(SIG_HI),
)
{
    /dev        -> $(Device) ;
    /dev/pts    -> $(Device) ;
    #/proc        -> $(Device) ;
    /proc/devices    -> $(Device) ;
    /proc/net    -> $(Device) ;
    /proc/tty    -> $(Device) ;
    /proc/sys    -> $(Device) ;
    /proc/cpuinfo    -> $(Device) ;
    /proc/modules    -> $(Device) ;
    /proc/mounts    -> $(Device) ;
    /proc/dma    -> $(Device) ;
    /proc/filesystems -> $(Device) ;
    /proc/interrupts -> $(Device) ;
    /proc/ioports    -> $(Device) ;
    /proc/scsi    -> $(Device) ;
    /proc/kcore    -> $(Device) ;
    /proc/self    -> $(Device) ;
    /proc/kmsg    -> $(Device) ;
    /proc/stat    -> $(Device) ;
    /proc/loadavg    -> $(Device) ;
    /proc/uptime    -> $(Device) ;
    /proc/locks    -> $(Device) ;
    /proc/meminfo    -> $(Device) ;
    /proc/misc    -> $(Device) ;
}
#
# Other configuration files
#
(
  rulename = "Other configuration files",
  severity = $(SIG_MED)
)
{
    /etc        -> $(SEC_BIN) ;
}
#
# Binaries
#
(
  rulename = "Other binaries",
  severity = $(SIG_MED)
)
{
    /usr/local/sbin    -> $(SEC_BIN) ;
    /usr/local/bin    -> $(SEC_BIN) ;
    /usr/sbin    -> $(SEC_BIN) ;
    /usr/bin    -> $(SEC_BIN) ;
}
#
# Libraries
#
(
  rulename = "Other libraries",
  severity = $(SIG_MED)
)
{
    /usr/local/lib    -> $(SEC_BIN) ;
    /usr/lib    -> $(SEC_BIN) ;
}
#
# Commonly accessed directories that should remain static with regards
# to owner and group
#
(
  rulename = "Invariant Directories",
  severity = $(SIG_MED)
)
{
    /        -> $(SEC_INVARIANT) (recurse = 0) ;
    /home        -> $(SEC_INVARIANT) (recurse = 0) ;
    /tmp        -> $(SEC_INVARIANT) (recurse = 0) ;
    /usr        -> $(SEC_INVARIANT) (recurse = 0) ;
    /var        -> $(SEC_INVARIANT) (recurse = 0) ;
    /var/tmp    -> $(SEC_INVARIANT) (recurse = 0) ;
}

```

Now you have to tell Tripwire that you made all this changes.
You have to tell Tripwire that you have tailored twpol.txt to match your Ubuntu system.
Write the following code:

```

sudo twadmin -m P /etc/tripwire/twpol.txt

```

Now you need to re-create the database to notice the changes.
Write following code:

```

sudo tripwire --init

```

Now all the error messages should be gone when you run the Tripwire database process.
If not then you have to open the twpol.txt file again and make necessary changes.

---

### Post by patrikmellq on 2014-07-20
**THE THIRD PART OF THE INSTALLATION**

Now lets say you get one intrusion on your Ubuntu system, then that some one could modifie and crack you Tripwire.
But this is not the case, because we are going to save our Tripwire database on a USB stick.

As long we have our Tripwire database on removable media we will be very safe.
This is a very high security measurement.

At /var/lib/tripwire can you find a folder with the name "report" and the database.
We will move the database to our USB stick and create a folder with the name report.

1. First you put in the USB stick on your computer, it should mount automatically if you rund Ubuntu 12.04.
You create a folder with the name tripwire on your USB stick.
Now you open up your tripwire folder on your USB stick and create one more folder within it with the name report.

2. Now you move the database from /var/lib/tripwire to your tripwire folder on your USB stick.
On my computer my database has the same name as my computer "patrik-ubuntu.twd"

3. With my ubuntu my USB stick is at " media folder " and the name of my USB stick is " 887D-1ED9 "
So the path to my USB stick is:

```

/media/887D-1ED9/tripwire

```

Now we have to tell Tripwire that the database is on our USB stick and also tell Tripwire that is should send the reports to our USB stick.
To do that we have to open up the twcfg.txt file

```

sudo nano /etc/tripwire/twcfg.txt

```

5. Change the patch for database and report
We will change DBFILE and REPORTFILE

This is how my path looks like to my USB stick:

Database

```

/media/887D-1ED9/tripwire/$(HOSTNAME).twd

```

Report

```

/media/887D-1ED9/tripwire/report/$(HOSTNAME) - $(DATE).twr

```

[IMG]http://i62.tinypic.com/2u9sger.jpg[/IMG]

---

### Post by patrikmellq on 2014-07-20
[B]THE FINAL PART OF THE INSTALLATION

[/B]Now we have to tell Tripwire about all our changes.
So we have to update and re-create some files.

1. First we have to update the site.key and twcfgl.txt

```

sudo twadmin -m F -S /etc/tripwire/site.key /etc/tripwire/twcfg.txt

```

2. Next we update the twpol.txt file

```

sudo twadmin -m P /etc/tripwire/twpol.txt

```

3. Now we have to re-create the database

```

sudo tripwire -m i

```

4. At last you can run this code again:

```

sudo twadmin -m F -S /etc/tripwire/site.key /etc/tripwire/twcfg.txt

```

[B]NOW YOU CAN RUN AND CHECK TRIPWIRE DATABASE FROM YOU USB-STICK

[/B]Run a tripwire check:

```

sudo tripwire --check

```

Now you can see on the report file below that the database has been read from the USB stick and that Tripwire wrote the report file to the USB stick.
All works great.

```

patrik@patrik-ubuntu:~$ sudo tripwire --check
[sudo] password for patrik: 
Parsing policy file: /etc/tripwire/tw.pol
*** Processing Unix File System ***
Performing integrity check...
### Warning: File system error.
### Filename: /var/lib/tripwire/patrik-ubuntu.twd
### No such file or directory
### Continuing...
Wrote report file: /media/887D-1ED9/tripwire/report/patrik-ubuntu-20140719-212845.twr


Open Source Tripwire(R) 2.4.2.2 Integrity Check Report

Report generated by:          root
Report created on:            Sat Jul 19 21:28:45 2014
Database last updated on:     Never

===============================================================================
Report Summary:
===============================================================================

Host name:                    patrik-ubuntu
Host IP address:              127.0.1.1
Host ID:                      None
Policy file used:             /etc/tripwire/tw.pol
Configuration file used:      /etc/tripwire/tw.cfg
Database file used:           /media/887D-1ED9/tripwire/patrik-ubuntu.twd
Command line used:            tripwire --check 

===============================================================================
Rule Summary: 
===============================================================================

-------------------------------------------------------------------------------
  Section: Unix File System
-------------------------------------------------------------------------------

  Rule Name                       Severity Level    Added    Removed  Modified 
  ---------                       --------------    -----    -------  -------- 
  Other binaries                  66                0        0        0        
  Tripwire Binaries               100               0        0        0        
  Other libraries                 66                0        0        0        
  Root file-system executables    100               0        0        0        
  Tripwire Data Files             100               0        0        0        
* System boot changes             100               1        0        5        
  (/var/log)
  Root file-system libraries      100               0        0        0        
  (/lib)
* Critical system boot files      100               0        0        1        
* Other configuration files       66                0        0        6        
  (/etc)
  Boot Scripts                    100               0        0        0        
  Security Control                66                0        0        0        
* Root config files               100               0        0        2        
* Devices & Kernel information    100               1        1        0        
  Invariant Directories           66                0        0        0        

Total objects scanned:  32705
Total violations found:  17

===============================================================================
Object Summary: 
===============================================================================

-------------------------------------------------------------------------------
# Section: Unix File System
-------------------------------------------------------------------------------

-------------------------------------------------------------------------------
Rule Name: System boot changes (/var/log)
Severity Level: 100
-------------------------------------------------------------------------------

Added:
"/var/log/dmesg.4.gz"

Modified:
"/var/log/Xorg.0.log"
"/var/log/dmesg"
"/var/log/dmesg.1.gz"
"/var/log/dmesg.2.gz"
"/var/log/dmesg.3.gz"

-------------------------------------------------------------------------------
Rule Name: Other configuration files (/etc)
Severity Level: 66
-------------------------------------------------------------------------------

Modified:
"/etc"
"/etc/cups"
"/etc/cups/subscriptions.conf"
"/etc/cups/subscriptions.conf.O"
"/etc/mtab"
"/etc/tripwire/twpol.txt"

-------------------------------------------------------------------------------
Rule Name: Critical system boot files (/boot)
Severity Level: 100
-------------------------------------------------------------------------------

Modified:
"/boot/grub/grubenv"

-------------------------------------------------------------------------------
Rule Name: Root config files (/root)
Severity Level: 100
-------------------------------------------------------------------------------

Modified:
"/root/.pulse"
"/root/.pulse/9fc69314a76666ab4b21a64100000008-runtime"

-------------------------------------------------------------------------------
Rule Name: Devices & Kernel information (/dev/pts)
Severity Level: 100
-------------------------------------------------------------------------------

Added:
"/dev/pts/2"

Removed:
"/dev/pts/4"

===============================================================================
Error Report: 
===============================================================================

-------------------------------------------------------------------------------
  Section: Unix File System
-------------------------------------------------------------------------------

1.   File system error.
     Filename: /var/lib/tripwire/patrik-ubuntu.twd
     No such file or directory

-------------------------------------------------------------------------------
*** End of report ***

Open Source Tripwire 2.4 Portions copyright 2000 Tripwire, Inc. Tripwire is a registered
trademark of Tripwire, Inc. This software comes with ABSOLUTELY NO WARRANTY;
for details use --version. This is free software which may be redistributed
or modified only under certain conditions; see COPYING for details.
All rights reserved.
Integrity check complete.

```

[B]NOTE
[/B]After you move the database from /var/lib/tripwire to the USB stick - then Tripwire will complain about it and give you a error message - you can ignore that and Tripwire works great with the new configuration.

---

