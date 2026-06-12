---
title: "running xp as guest cant access usb drives or shared folder"
date: 2009-02-14
forum: Virtualisation
---

### Post by shateredsoul on 2009-02-14
Hi,

any idea on how to make xp recognize usb devices through virtual machine?   I installed the guest additions iso.

Also, how can you access the shared folder from xp ? 

thank you

---

### Post by HotShotDJ on 2009-02-14
> **shateredsoul said:**
> Hi,

any idea on how to make xp recognize usb devices through virtual machine?   I installed the guest additions iso.

Also, how can you access the shared folder from xp ?For USB: [http://ubuntuforums.org/showpost.php?p=6398716&postcount=1](http://ubuntuforums.org/showpost.php?p=6398716&postcount=1)

As far as shared folders, this should work just find once the guest additions are installed.  Did you actually install the guest additions or did you simply mount the ISO?

---

### Post by empty_spaces on 2009-02-14
Are you running virtualbox-ose from the repositories, or do you have version 2.1.2 from [http://www.virtualbox.org/](http://www.virtualbox.org/) ?
The one from the repositories does not support usb.

If you are using 2.1.2, this is the link to instructions for usb and shared folders below that.
[https://help.ubuntu.com/community/VirtualBox#USB](https://help.ubuntu.com/community/VirtualBox#USB)

---

### Post by HotShotDJ on 2009-02-14
> **empty_spaces said:**
> If you are using 2.1.2, this is the link to instructions for usb and shared folders below that.
[https://help.ubuntu.com/community/VirtualBox#USB](https://help.ubuntu.com/community/VirtualBox#USB)These instructions for enabling USB in VirtualBox are obsolete.  Please do not use them with recent version of Ubuntu (Hardy and newer).

---

### Post by empty_spaces on 2009-02-14
> **HotShotDJ said:**
> These instructions for enabling USB in VirtualBox are obsolete.  Please do not use them with recent version of Ubuntu (Hardy and newer).

Well, I have successfully used those instructions on 3 different installs - 32 bit Hardy, 64 bit Hardy and 64 bit Intrepid.

So I really would like to know where you got your information from.

And links to updated instructions would also be appreciated.

---

### Post by HotShotDJ on 2009-02-14
> **empty_spaces said:**
> Well, I have successfully used those instructions on 3 different installs - 32 bit Hardy, 64 bit Hardy and 64 bit Intrepid.

So I really would like to know where you got your information from.

And links to updated instructions would also be appreciated.Link is in my original reply to the OP.  And yes, using the instructions to which you linked are often successful.  Others have reported problems with them.  The point is that it is no longer necessary to follow those instructions.  The problems that they were designed to overcome are no longer present in newer version of Ubuntu.  They are unnecessarily complicated and therefore prone to user error (although even a simple "type cd in a terminal" instruction is not fool-proof :)).  For some people, even the simple /etc/fstab fix isn't necessary since Virtualbox 2.1.2 ... although others still need it.  Hopefully the next version of VirtualBox will have USB support working out of the box universally, thereby obsoleting all USB HowTo's.

---

### Post by empty_spaces on 2009-02-14
Oh ok. I just assumed that since I have a 100% success rate with those instructions, they would be fine.
Well, whatever works. :)

---

### Post by chandra on 2009-02-17
This works for me on Intrepid for making USB devices recognizable:

1. Install VirtualBox-2.1 following the instructions at:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

2. Ensure that the group ```
vboxusers
``` exists and you are in it. This should be automatic if you install VirtualBox-2.1 at step 1.

3. Save this this Perl script to a file and execute it make USB devices accessible:
```
#!/usr/bin/perl
use warnings;
use diagnostics;
use strict;
use File::stat;
use File::Basename;

# Perl script to enable use of USB devices in VirtualBox
# on K/Ubuntu Intrepid Ibex 8.10 running VirtualBox 2.1

print "Script for enabling USB in VirtualBox 2.1 on K/Ubuntu Intrepid 8.10\n";

# Get GID of vboxusers group from /etc/group if it exists or exit otherwise

my $filename = "/etc/group";
open my $file, $filename or die "Unable to open $filename";
my $vboxusersGID = "";
while (<$file>)
    {
    # In line beginning with vboxusers
    # match first contiguous set of digits delimited by colons
    if (/^vboxusers\D+:(\d+):/) {$vboxusersGID = $1};
    }
close $file;
if ($vboxusersGID eq "")
    {
    print "Group \"vboxusers\" not found.\nCreate it, add yourself to it, and re-run this script.\nExiting.\n";
    }
else {
    print "GID of vboxusers is $vboxusersGID\n";
    }
exit unless ($vboxusersGID);

# Examine /etc/fstab to see if a line like that below exists
# none /proc/bus/usb usbfs devgid=$vboxusersGID,devmode=664 0 0

$filename = "/etc/fstab";
my $usbfsline = "";
open $file, $filename or die "Unable to open $filename";
while (<$file>)
    {
    if (/^[^#].+(usbfs\s+devgid=$vboxusersGID).*/)
        {
        $usbfsline = $1;
        print "Line containing \"$usbfsline\" already exists in $filename.\nExiting leaving $filename untouched.\n";
        }
    }
close $file;

# Conditionally
# (a) make a backup of /etc/fstab in /tmp/fstab.backup
# (b) append the line
# none /proc/bus/usb usbfs devgid=$vboxusersGID,devmode=664 0 0
# to /etc/fstab

unless ($usbfsline)
    {
    $filename = "/etc/fstab";
    my $path = dirname($filename);
    my $fstab = basename($filename);
    my $tempfile = "/tmp/$fstab";
    my $inode = stat($filename);
    my $uid = $inode->uid; # should be zero for a root-owned file
    system "cp", "$filename", "$tempfile"; # working copy of /etc/fstab in /tmp
    print "Making backup copy of $filename as $tempfile.backup\n";
    system "cp", "$filename", "$tempfile.backup";
    open $file, ">> $tempfile" or die "Unable to open $tempfile";
    print $file "\# For VirtualBox USB access; vboxusers has gid $vboxusersGID\n";
    $usbfsline = "none /proc/bus/usb usbfs devgid=$vboxusersGID,devmode=664 0 0";
    print $file "$usbfsline\n";
    close $file;
    system "sudo", "-u", "\#uid", "mv", "$tempfile", "$filename";
    print "Appended \"$usbfsline\" to $filename\n";
    # Remount devices
    system "sudo", "mount", "-a";
    }
# Send comments and corrections to chandra@ee.uwa.edu.au
```

For shared folders do the following:

4. Before starting up the VM, enable shared folders by clicking on Settings -> Shared Folders on VirtualBox and making your selections.

5. With the VM running, open up Windows Explorer, go to My Network Places and look for the VirtualBox Shared Folders. 

6. Right click on each and map it to a Windows drive of your choice. You will then be able to access your shared folders fast.

---

### Post by shateredsoul on 2009-02-18
For those like me that don't know...

here's how to execute a perl script.  Make sure you first copy and paste it into a text file.

[http://ubuntuforums.org/showthread.php?t=473820]("http://ubuntuforums.org/showthread.php?t=473820")

---

### Post by shateredsoul on 2009-02-18
does the new virtual box solve these issues?

---

### Post by HotShotDJ on 2009-02-18
> **shateredsoul said:**
> does the new virtual box solve these issues?Yes.  I just tested it today.  VirtualBox 2.1.4 PUEL version fully supports USB out of the box.  I'm changing my HowTo today.

(BTW... perl scripts were NEVER required.  Although the one posted here is an interesting way to automate the /etc/fstab edits that used to be necessary.  To me, it seems like using a sledge hammer to kill a mosquito, but to each his/her own.)

---

### Post by HotShotDJ on 2009-02-18
DUH... nearly a duplicate of my previous post.  :oops:

---

