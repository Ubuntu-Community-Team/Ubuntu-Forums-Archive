---
title: "Samba problems"
date: 2013-02-03
forum: Server Platforms
---

### Post by hostingdude on 2013-02-03
For background, see the SAMBA PROBLEMS thread:   [http://ubuntuforums.org/showthread.php?t=1533629](http://ubuntuforums.org/showthread.php?t=1533629)

I don't have much experience here, but I'm finding the same problem, and I'm positive it's on the Windows 7 side.

I have a CentOS 5.x 64-bit server with a share on it (Ubuntu vs. CentOS is irrelevant here, same problem on either OS, as you will see), and my Windows 7 Ultimate 64 machine CAN access it when I have the SAMBA share completely open, using:

username:  guest
admin:  guest

This is when I set it up going to COMPUTER, MAP NETWORK DRIVE, pick a drive (Z) and choose folder as:

\\(ip address)\(shared samba folder)

e.g.:

\\000.000.000.000\samba_drive

when I connect, I get a window labelled WINDOWS SECURITY, which at the top says:  

Enter Network Password 
Enter your password to connect to:  000.000.000.000

Then it lets me login one of two ways:

(My Computer Name)\(my Windows username)
e.g.:
STATION15\jones123

plus a password
with a REMEMBER MY CREDENTIALS checkbox below it

...OR...

USE ANOTHER ACCOUNT

And that allows me to select a USERNAME and PASSWORD...

THE PROBLEM IS THIS:

When I choose that second option to put in the SAMBA username, my Win7 computer still PREPENDS \STATION15\ to the front of the username (that's my Windows 7 computer name).

And my login is REJECTED by the Samba server...

So let's say that my SAMBA setup on Linux is waiting for this combo:

username:  sambaguy
password:  SambaPass1

Apparently, WINDOWS is SENDING THIS:

username:  \STATION15\sambaguy
password:  SambaPass1

and I'm rejected...


AGAIN, this is ONLY after I set up the credential requirements on the SAMBA Server.


NOW IT GETS WEIRD -- It only does it on THIS PC, which is:

Windows 7 Ultimate 64-bit, UPGRADED from a Windows Vista Ultimate 64-bit.

On ANY OTHER PC I own, I do NOT have this problem -- all the others do NOT try to prepend my computer name to my login name:

Windows 7 Home Premium 32-bit works fine
Windows 7 Home Premium 64-bit works fine
Windows 7 Professional 64-bit works fine
Windows 8 64-bit (on cheap craptop... no clue what version or how to even find it... I H8 Win8) works fine
(Even an Android phone and tablet work fine to connect - one ICS, one Jelly Bean)

But the problem is on THIS COMPUTER which is:

Windows 7 Ultimate 64-bit -- upgraded using the Microsoft Upgrade, from Windows Vista Ultimate 64-bit...

So, unless other folks have problems using Windows 7 Ultimate to connect to Samba with this specific issue, then I am thinking that...

This may be a problem that's legacy to Windows Vista.

Since my upgrade to Win7 was via the MS upgrade method, and not by a fresh installation...  I am thinking that SOME of my control and .conf files are still VISTA-ish...  that some of them were simply left alone, or only lightly-modified by Windows 7 when I did the upgrade.  Whereas, if I had done a fresh Win7 install, I would have gotten all new and properly set configuration files.

I say this also because Vista is known to have this type of problem... Vista had known samba connection problems.

Somebody with more experience with Windows could take a guess at this and perhaps could HELP(!) me configure Windows 7 so it's not sending the COMPUTER NAME as a prepend to the username when I go to log in to Samba remotely.

I know the Samba end is set up right since every other computer on the planet can connect...

Can someone help?

Also, is this related to YOUR issue?  Was your computer OS an upgrade from Vista to Win7?   You may have tweaked something in your Win7 that fixed the issue, and after a reboot (or directly after the tweak) you connected...  You say you still don't know why.  This theory may apply to you too...

Please help!

---

### Post by varunendra on 2013-02-03
Not a network problem.
*Thread moved to **Server Platforms**.*

---

