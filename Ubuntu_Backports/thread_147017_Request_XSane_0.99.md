---
title: "Request XSane 0.99"
date: 2006-03-19
forum: Ubuntu Backports
---

### Post by shomati_sen on 2006-03-19
Hi,

I'd like to request backporting xsane's latest version into Breezy mostly because it has the ability to scan directly as PDF. 

Thanks,

Shomati

---

### Post by JamesNorris on 2006-03-19
Small problem there is that we're still only using 0.97 in dapper...

---

### Post by phetre on 2006-03-28
Yeah, is there any chance they would consider upgrading?  I'm having trouble scanning in Dapper, but I don't know whether to file a bug report on an outdated version...

---

### Post by davegod75 on 2006-04-02
[QUOTE=phetre]Yeah, is there any chance they would consider upgrading?  I'm having trouble scanning in Dapper, but I don't know whether to file a bug report on an outdated version...[/QUOTE]


how about a better scanning program as well.  xsane is overly complicated for the casual scanner

---

### Post by easy_target on 2006-05-21
I concur. Xsane is functional but scares the hell out of the casual user.

---

### Post by SpEcIeS on 2006-06-17
Use the debian unstable source and compile xsane 0.99 on you own. Works great. :)

Add these to you sources.list and rem once done:
```

# Debian Unstable
deb ftp://sunsite.cnlab-switch.ch/mirror/debian/ unstable main contrib non-free
deb-src ftp://sunsite.cnlab-switch.ch/mirror/debian/ unstable main contrib non-free
```
Apply changes using **"sudo apt-get update"**

Build using this (You may need to add dev packages):
```

sudo apt-get -b source xsane
sudo apt-get -b source xsane-common
```
Install using:
```

sudo dpkg -i xsane_0.99+0.991-1_i386.deb
sudo dpkg -i xsane-common_0.99+0.991-1_all.deb
```

---

### Post by robertmcox on 2006-08-20
You 'da man, Species! (thank you for sharing knowledge)

Your directions worked like a champ for me and allowed me to scan via ADF straight into PDF file.

---

### Post by volkerbradley on 2006-09-05
I couldn't use the apt-get to get the sources.  When I added the two sites to the sources list and then did sudo apt-get update, I received the following error messages:
Fetched 5829kB in 1m36s (60.1kB/s)
Reading package lists... Error!
W: GPG error: [ftp://sunsite.cnlab-switch.ch](ftp://sunsite.cnlab-switch.ch) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F
E: Dynamic MMap ran out of room
E: Error occurred while processing tclthread (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/sunsite.cnlab-switch.ch_mirror_debian_dists_unstable_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened

Any suggestions?  Can the source files be downloaded directly from somewhere?

---

### Post by MintabiePete on 2006-09-19
I am having  the same  problem and getting the same  errors , have  you  found a  way around it  yet ?

---

### Post by SpEcIeS on 2006-09-19
Not too sure about the:
> E: Dynamic MMap ran out of room
E: Error occurred while processing tclthread (NewVersion1)
Seems to me I have seen that one before. Have to look (try Google) into that one, but the first is just a key issue. Here is a script that I made to ease the key addition.
```
#!/bin/bash

if [ "$#" = 1 ]; then
	gpg --recv $1
	gpg -a --export $1 | sudo apt-key add -
else
	echo;
	echo "You must supply a key ID to download and apply to the apt keyring."
	echo;
fi
```
In the case above use this line: **apt-addkey 010908312D230C5F**.

When creating shell scripts remember to enable execution. (*chmod 700 apt-addkey*)

---

### Post by SpEcIeS on 2006-09-19
Since I am using ***Ubuntu*** Dapper again, I decided to build the xsane packages. These packages were build from the **[COLOR="DarkOrange"]Edgy[/COLOR]** source repos and they work fine on my system.

I anyone would like them please _send me your email address_ and I would be happy to supply them. :D

---

### Post by MintabiePete on 2006-09-19
The only  way I  could  get rid of those  errors  was  to remove  those  lines out of my sources.list . I am only  new  to unix  commands and   while I tried  to follow  your instructions  to add key I must have  been  missing  something . And back in your instructions  when adding  those  lines to  sources.list  you  said " and rem once done" , I wasnt  sure  what  you meant  about that . I really  would  like to get xsane  working as that is  the  only  reason I still have  windows , to be  able   to use my old  Canoscan N340P scanner .

---

### Post by SpEcIeS on 2006-09-19
Oh.. yeah..  computer jargon. :) "rem" means to remove with a symbol. In the case of the **sources.list** you use a "**#**" symbol to disinclude the line.

To add the key that you were missing, copy the script, provided previously, to a file called "**apt-addkey**" and then use this: "**apt-addkey 010908312D230C5F**".
That should get you your key into the apt.

---

### Post by SpEcIeS on 2006-09-21
> **volkerbradley said:**
> 
E: Dynamic MMap ran out of room
E: Error occurred while processing tclthread (NewVersion1)
E: Problem with MergeList

I knew I saw this problem before. Add this [COLOR="Red"]**APT::Cache-Limit "33554432";**[/COLOR] to your apt.conf.

**sudo gedit /etc/apt/apt.conf**

That will fix that. :cool:

---

### Post by MintabiePete on 2006-10-01
@ SpEcIeS

I still have  an ongoing  problem with my CanoScan N340P scanner . I have  done a re install , which was  about  time as  I havnt  touched this  computer for a long time :)

I found that for me to get xsane  working properly I had to go into CMOS and  change the  Parallel port mode  from SPP to NORMAL  then I could get it  scanning  but only  in greyscale .

For the start I found that I could only scan in safe mode , but found a fix that I had to edit my /etc/udev/rules.d file and change the 40-permissions.rules. to be able to start in normal mode instead of root , and it works  It was a pain saving things in root and then not being able to access them like I should be able to .

This  being  able to scan only in greyscale  and not in colour has  me mystified at the moment , if anyone  has any ideas I would appreciate them passing them on :)

Thanks 

Peter

---

### Post by SpEcIeS on 2006-10-01
Wow.. gray scale only..  you got me???  That is a strange result.

---

