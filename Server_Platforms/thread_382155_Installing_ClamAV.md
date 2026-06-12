---
title: "Installing ClamAV"
date: 2007-03-11
forum: Server Platforms
---

### Post by ComputerGuy56 on 2007-03-11
I really want ClamAV. I researched as much as I could but I still have no idea how to install clamav.
I also need to know which file(s) to download.

---

### Post by Mr. C. on 2007-03-11
Look at the debian section:

[http://www.clamav.net/download/packages/packages-linux](http://www.clamav.net/download/packages/packages-linux)

---

### Post by ComputerGuy56 on 2007-03-11
So I just type:
```
sudo apt-get install clamav
```
This is what happens:
```
sly@sly-desktop:~$ sudo apt-get install clamav
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
clamav is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
I've already did that once and it came with an error(I dont have it) I tried to uninstall it(forgot the code) but it said it wasn't installed.:confused:

---

### Post by rennen01 on 2007-03-12
Would you guys consider ClamAV the Server anti-virus of choice?

---

### Post by Mr. C. on 2007-03-12
Sorry I have not replied earlier.  I'd forgotten about the reminder email in my mailbox.

The instructions on that page indicate how you need to add a line to your debian repository file.  Once that is there, you can use Synaptec or apt-get to download and install the clamav .90.1 build for your system.

These packages are not official, and a warning comes along with them indicating that you are installing untested, unverified software.

I don't use them, as I've been building my own software for years.

As far as a "server antivirus", what are you trying to protect ?  ClamAV was designed as a mail server AV scanner.

MrC

---

### Post by rennen01 on 2007-03-12
Thanks for the response.  I am just wondering if anti-virus is recommended on File/Print Servers? Users will be placing their data on network shares.

---

### Post by DougieFresh4U on 2007-03-12
Not to hijack, wondering how do you launch clam once installed? Thanks (don't see it in any menu)

---

### Post by ComputerGuy56 on 2007-03-12
I looked around and put this in my sources.list
```
stable/sarge:

deb http://ftp2.de.debian.org/debian-volatile/ sarge/volatile main
```

Then I was going to download ClamAV and I think I found the correct link, although I want the very official and the one that'll update it self. Can I get a link?

---

### Post by Mr. C. on 2007-03-12
Because the creation of viruses and other malware happens so rapild, there is no "official" package that can keep up.

The "freshclam" utility that comes with clamAV will update the signatures.

MrC

---

### Post by ComputerGuy56 on 2007-03-12
Well, I've been trying every tutorial, googled it for about 1 Hour, looked in the forums, tried apt-get again, almost broke my computer, can someone just help me get it.:confused:

---

### Post by ComputerGuy56 on 2007-03-12
I found instructions at:
[http://www.linux.com/howtos/Qmail-ClamAV-HOWTO/x114.shtml](http://www.linux.com/howtos/Qmail-ClamAV-HOWTO/x114.shtml)

I get to the part when I have to type
```
make
```
and
```
make install
```

It always says this:
```
sly@sly-desktop:~/clamav-0.90.1$ make
make: *** No targets specified and no makefile found.  Stop.

```

---

### Post by ComputerGuy56 on 2007-03-12
So I'm the only one in the WHOLE world having trouble with this thing. What about the people that actually GOT it installed. This is really getting me mad.:confused: :-k

---

### Post by Mr. C. on 2007-03-12
ComputerGuy56,

It is a requirement with computers and software that one follows instructions very carefully.  They are simply too complex to do otherwise.  And a corollary of that is not to follow advice blindly without knowing how to resolve bad advice:

```
#tar -xvzf clamav-0.65.tar.gz 
#cd clamav-0.65 #groupadd clamav
#useradd clamav -g clamav -c "Clam AntiVirus" -s /nonexistent .
#/configure
#make 
#make install 
```

Above were the instructions.  You decided to skip the step that was in error, and not report its error message.

Change the line to:
```
#./configure
```


MrC

---

### Post by ComputerGuy56 on 2007-03-12
Do I have to do it EXACTLY like that. I always did it without the # marks. I thought those were comments.

---

### Post by ComputerGuy56 on 2007-03-12
Do I have to do it EXACTLY like that. I always did it without the # marks. I thought those were comments. Time to start over....

---

### Post by ComputerGuy56 on 2007-03-12
> **ComputerGuy56 said:**
> Do I have to do it EXACTLY like that. I always did it without the # marks. I thought those were comments. Time to start over....

Oops, double post.

---

### Post by Mr. C. on 2007-03-12
No, # is a comment in the shell, and will do nothing if you start your lines with those.  It is also the default root shell prompt.  Remove the # 's from each line and enter the lines, with the correction I supplied.

MrC

---

### Post by ComputerGuy56 on 2007-03-12
Still the same error.....

```
sly@sly-desktop:~$ cd clamav-0.90.1
sly@sly-desktop:~/clamav-0.90.1$ groupadd clamav
groupadd: group clamav exists
sly@sly-desktop:~/clamav-0.90.1$ useradd clamav -g clamav -c "Clam AntiVirus" -s /nonexistent .
Usage: useradd [options] LOGIN

Options:
  -b, --base-dir BASE_DIR       base directory for the new user account
                                home directory
  -c, --comment COMMENT         set the GECOS field for the new user account
  -d, --home-dir HOME_DIR       home directory for the new user account
  -D, --defaults                print or save modified default useradd
                                configuration
  -e, --expiredate EXPIRE_DATE  set account expiration date to EXPIRE_DATE
  -f, --inactive INACTIVE       set password inactive after expiration
                                to INACTIVE
  -g, --gid GROUP               force use GROUP for the new user account
  -G, --groups GROUPS           list of supplementary groups for the new
                                user account
  -h, --help                    display this help message and exit
  -k, --skel SKEL_DIR           specify an alternative skel directory
  -K, --key KEY=VALUE           overrides /etc/login.defs defaults
  -m, --create-home             create home directory for the new user
                                account
  -o, --non-unique              allow create user with duplicate
                                (non-unique) UID
  -p, --password PASSWORD       use encrypted password for the new user
                                account
  -r, --system                  create a system account
  -s, --shell SHELL             the login shell for the new user account
  -u, --uid UID                 force use the UID for the new user account
sly@sly-desktop:~/clamav-0.90.1$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
creating target.h - canonical system defines
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gawk... (cached) mawk
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
sly@sly-desktop:~/clamav-0.90.1$ make
make: *** No targets specified and no makefile found.  Stop.
sly@sly-desktop:~/clamav-0.90.1$ make install
make: *** No rule to make target `install'.  Stop.
sly@sly-desktop:~/clamav-0.90.1$ 

```

I unzipped it in the beginning but it's too long.

---

### Post by Mr. C. on 2007-03-12
```
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
```

You need a C compiler to build software.  You need gcc.


MrC

---

### Post by ComputerGuy56 on 2007-03-12
Googled GCC. Found [http://gcc.gnu.org/](http://gcc.gnu.org/)

I have to idea where to download it. I know I sound like a complete noob, but it's sorta confusing...

---

### Post by Mr. C. on 2007-03-12
If you are going to build software, it would be worth using Synaptec to download the build-essential package, under Development.  That should pull in all you need to configure, compile and install.

MrC

---

### Post by ComputerGuy56 on 2007-03-12
Can you explain a little more of what Synaptec is? And where/how to get it? Wow, at this point I'm hoping I'll ever get ClamAV but I'm not going to give up yet.

---

### Post by Mr. C. on 2007-03-12
Is the GUI package management system located at System->Administration->Synaptec Package Manager.

If you don't have that, use apt-get.

MrC

---

### Post by ComputerGuy56 on 2007-03-13
I have it, should it work?

---

### Post by Mr. C. on 2007-03-13
That's the theory.  It should.

---

### Post by ComputerGuy56 on 2007-03-13
Well, the only ClamAV things that are selected are...:
ClamAV
ClamAV-Base
ClamAV-freshclam

That ones that I can select are:
ClamAV
ClamAV-Base
clamav-daemon
clamav-data
clamav-dbg
clamav-docs
clamav-freshclam
clamav-getfiles
clamav-milters
clamav-testfiles

Though ClamAV isn't Installed.
What do I do?
By the way, If you just want to PM me, you can.

---

### Post by DougieFresh4U on 2007-03-16
How can I open clam? Also I do not see it in any menu. Terminal gives the following ::[B]dougie@DougiesToyBox:~$ freshclam
ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).
dougie@DougiesToyBox:~$[/B] Also from the log file you can see I can not access the permission  to fix

---

### Post by Mr. C. on 2007-03-16
DougieFresh4U - Freshclam must be run as a privileged user, or a user that has write access to the log files and definitions directory.  Typically you'd run freshclam out of a cron job.

ClamAV is designed to be run from a command line - there is no GUI.  It was designed as an email antivirus checker.

If the clam service is running, you can run from a terminal:

```
   clamdscan *somefile*
```
Otherwise, run:
```
   clamscan *somefile*
```

ComputerGuy-  have you made any progress?

MrC

---

### Post by jtc on 2007-03-16
EDIT: ohh, bad post, missed a lot of previous ones.

---

### Post by heffo_j on 2007-03-23
Easiest way to install Clam is with Automatix (and possibly Easy Ubuntu - but not sure). There used to be an Automatix link on this forum. Install it then run it. You will see a lot of goodies that are easily installed without the fuss.

Regards
John H

---

### Post by jackrobinson on 2007-03-23
> **heffo_j said:**
> Easiest way to install Clam is with Automatix (and possibly Easy Ubuntu - but not sure). There used to be an Automatix link on this forum. Install it then run it. You will see a lot of goodies that are easily installed without the fuss.

Regards
John H

[http://www.getautomatix.com](http://www.getautomatix.com)

---

