---
title: "Good Tripwire twpol.txt for 6.06?"
date: 2006-09-24
forum: Server Platforms
---

### Post by andb on 2006-09-24
Anyone have a good Tripwire twpol.txt file that cuts out a lot of the noise? 

Tripwire is great,it just seems that the default policy in the Ubuntu package should be set up to be more appropriate for the typical ubuntu desktop user instead of the current tight policy which is better suited for a server.

---

### Post by andb on 2006-09-27
Asked another way, which files are critical and should be unchanged? The following seem the most important to me:

/boot
/bin
/etc
/lib
/opt
/sbin
/usr (potentialy excluding /usr/src/)

What does not seem important to me:
/media
/var
/tmp

what Im unsure about are:
/dev
/proc
It seems to me that these are constantly changing and on a desktop system wouldnt be main targets of hacking.

Obviously ownership changes on files in /home would be important but additions, deletions, changes not. 

Thanks for any help, when Ive finished making a good twpol.txt file, Ill be sure to post it...

---

### Post by andb on 2007-01-14
In case it helps anyone, my solution in the end was to prune back the directories being checked. Hopefully I didt exclude something important. My biggest problem is the frequencyof updates. It would be amazing if apt-get and aptitude could incorporate a funciton to call tripwire and update it's database. As updates come every 2-3 days, it can mean cheking and updating tripwire that often. Or shceduling updates less frequently and then cheking tripwire simultaniously. Or if developers would include a "tripwire update file/script" that could handle this safely. Problem is that there are just too many warnings on a desktop machine. Ona production server which would have a minimal set of packages, I can imagine it would be more appropriate.

You will see below that i stared with the standard debian file and trimmed it back using excludes and remarks. Ideally, I would have included more directories, but limited the checking to ownership or such limited factors. If someone chas a better tripwire config file, please post! 

```

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
	$(TWBIN)/siggen			-> $(SEC_BIN) ;
	$(TWBIN)/tripwire		-> $(SEC_BIN) ;
	$(TWBIN)/twadmin		-> $(SEC_BIN) ;
	$(TWBIN)/twprint		-> $(SEC_BIN) ;
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
	$(TWVAR)/$(HOSTNAME).twd	-> $(SEC_CONFIG) -i ;
	$(TWETC)/tw.pol			-> $(SEC_BIN) -i ;
	$(TWETC)/tw.cfg			-> $(SEC_BIN) -i ;
	$(TWETC)/$(HOSTNAME)-local.key	-> $(SEC_BIN) ;
	$(TWETC)/site.key		-> $(SEC_BIN) ;

	#don't scan the individual reports
	$(TWVAR)/report			-> $(SEC_CONFIG) (recurse=0) ;
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
	/boot			-> $(SEC_CRIT) ;
	/lib/modules		-> $(SEC_CRIT) ;
}

(
  rulename = "Boot Scripts",
  severity = $(SIG_HI)
)
{
	/etc/init.d		-> $(SEC_BIN) ;
#	/etc/rc.boot		-> $(SEC_BIN) ;
	/etc/rcS.d		-> $(SEC_BIN) ;
	/etc/rc0.d		-> $(SEC_BIN) ;
	/etc/rc1.d		-> $(SEC_BIN) ;
	/etc/rc2.d		-> $(SEC_BIN) ;
	/etc/rc3.d		-> $(SEC_BIN) ;
	/etc/rc4.d		-> $(SEC_BIN) ;
	/etc/rc5.d		-> $(SEC_BIN) ;
	/etc/rc6.d		-> $(SEC_BIN) ;
}


#
# Critical executables
#
(
  rulename = "Root file-system executables",
  severity = $(SIG_HI)
)
{
	/bin			-> $(SEC_BIN) ;
	/sbin			-> $(SEC_BIN) ;
}

#
# Critical Libraries
#
(
  rulename = "Root file-system libraries",
  severity = $(SIG_HI)
)
{
	/lib			-> $(SEC_BIN) ;
}


#
# Login and Privilege Raising Programs
#
(
  rulename = "Security Control",
  severity = $(SIG_MED)
)
{
	/etc/passwd		-> $(SEC_CONFIG) ;
	/etc/shadow		-> $(SEC_CONFIG) ;
}



# Disabled to prevent noise
#
# These files change every time the system boots
#
#(
#  rulename = "System boot changes",
#  severity = $(SIG_HI)
#)
#{
#	/var/lock		-> $(SEC_CONFIG) ;
#	/var/run		-> $(SEC_CONFIG) ; # daemon PIDs
#	/var/log		-> $(SEC_CONFIG) ;
#}


# 20060924  Disabled as root acct is never used and generates tons of noise
# These files change the behavior of the root account
#(
#  rulename = "Root config files",
#  severity = 100
#)
#{
#	/root				-> $(SEC_CRIT) ; # Catch all additions to /root
#	/root/mail			-> $(SEC_CONFIG) ;
#	/root/Mail			-> $(SEC_CONFIG) ;
#	/root/.xsession-errors		-> $(SEC_CONFIG) ;
#	/root/.xauth			-> $(SEC_CONFIG) ;
#	/root/.tcshrc			-> $(SEC_CONFIG) ;
#	/root/.sawfish			-> $(SEC_CONFIG) ;
#	/root/.pinerc			-> $(SEC_CONFIG) ;
#	/root/.mc			-> $(SEC_CONFIG) ;
#	/root/.gnome_private		-> $(SEC_CONFIG) ;
#	/root/.gnome-desktop		-> $(SEC_CONFIG) ;
#	/root/.gnome			-> $(SEC_CONFIG) ;
#	/root/.esd_auth			-> $(SEC_CONFIG) ;
#	/root/.elm			-> $(SEC_CONFIG) ;
#	/root/.cshrc		        -> $(SEC_CONFIG) ;
#	/root/.bashrc			-> $(SEC_CONFIG) ;
#	/root/.bash_profile		-> $(SEC_CONFIG) ;
#	/root/.bash_logout		-> $(SEC_CONFIG) ;
#	/root/.bash_history		-> $(SEC_CONFIG) ;
#	/root/.amandahosts		-> $(SEC_CONFIG) ;
#	/root/.addressbook.lu		-> $(SEC_CONFIG) ;
#	/root/.addressbook		-> $(SEC_CONFIG) ;
#	/root/.Xresources		-> $(SEC_CONFIG) ;
#	/root/.Xauthority		-> $(SEC_CONFIG) -i ; 
# Changes Inode number on login
#	/root/.ICEauthority		    -> $(SEC_CONFIG) ;
#}

# 20060927 As devices are allways changing, decided to leave out
# Critical devices
# 
#(
#  rulename = "Devices & Kernel information",
#  severity = $(SIG_HI),
#)
#
# Change made 2006.09.21 to avoid proc being reported.
#{
#	/dev		-> $(Device) ;
#	/proc		-> $(Device) ;
#}
#{
#	/dev		-> $(Device) ;
#}



#
# Other configuration files
#
(
  rulename = "Other configuration files",
  severity = $(SIG_MED)
)
{
	/etc		-> $(SEC_BIN) ;
}

#
# Binaries
#
(
  rulename = "Other binaries",
  severity = $(SIG_MED)
)
{
	/usr/local/sbin	-> $(SEC_BIN) ;
	/usr/local/bin	-> $(SEC_BIN) ;
	/usr/sbin	-> $(SEC_BIN) ;
	/usr/bin	-> $(SEC_BIN) ;
}

#
# Libraries
#
(
  rulename = "Other libraries",
  severity = $(SIG_MED)
)
{
	/usr/local/lib	-> $(SEC_BIN) ;
	/usr/lib	-> $(SEC_BIN) ;
}

#
# Commonly accessed directories that should remain static with regards
# to owner and group
#
#(
#  rulename = "Invariant Directories",
#  severity = $(SIG_MED)
#)
#{
#	/		-> $(SEC_INVARIANT) (recurse = 0) ;
#	/home		-> $(SEC_INVARIANT) (recurse = 0) ;
#	/tmp		-> $(SEC_INVARIANT) (recurse = 0) ;
#	/usr		-> $(SEC_INVARIANT) (recurse = 0) ;
#	/var		-> $(SEC_INVARIANT) (recurse = 0) ;
#	/var/tmp	-> $(SEC_INVARIANT) (recurse = 0) ;
#}

# directories to ignore 2006.09.21
! /proc;
! /mnt;
! /lost+found;
! /usr/src;
! /home;
! /dev/;
! /var;
! /tmp;
! /etc/mtab;
! /etc/adjtime;
! /etc/motd;
! /etc/printcap;

# this is a symlink used to deal with Firefox 1.5/flash and it thinks its always being added
!/usr/lib/libesd.so.1;

# log of bootup events, will always change
! /dev/.initramfs/usplash_log;


```

---

