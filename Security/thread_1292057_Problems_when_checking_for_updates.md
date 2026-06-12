---
title: "Problems when checking for updates"
date: 2009-10-15
forum: Security
---

### Post by dr13 on 2009-10-15
When I check for updates I get the following reply:

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


Please help:(

---

### Post by cariboo on 2009-10-15
Open up a terminal and try this:

```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

---

### Post by dr13 on 2009-10-16
Hi cariboo907

Tried and this appears

apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory
dane@dane-desktop:~$ cd /var/lib/apt
dane@dane-desktop:/var/lib/apt$ mv lists lists.old
mv: cannot move `lists' to `lists.old': Permission denied
dane@dane-desktop:/var/lib/apt$ mkdir -p lists/partial
dane@dane-desktop:/var/lib/apt$ apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory
dane@dane-desktop:/var/lib/apt$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
dane@dane-desktop:/var/lib/apt$ 


Any more help pls

---

### Post by phillw on 2009-10-16
I think you need to sudo .....

```
sudo apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```
                                                           
Hope that sorts it,

Phill.

---

### Post by dr13 on 2009-10-16
Hi phillw

This is what i get;

name@name-desktop:~$ sudo apt-get clean
name@name-desktop:~$ cd /var/lib/apt
name@name-desktop:/var/lib/apt$ mv lists lists.old
mv: cannot move `lists' to `lists.old': Permission denied


name@name-desktop:/var/lib/apt$ mkdir -p lists/partial
name@name-desktop:/var/lib/apt$ sudo apt-get clean
name@name-desktop:/var/lib/apt$ sudo apt-get update
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy Release.gpg
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/main Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/universe Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/multiverse Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/main Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/universe Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/multiverse Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy Release 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]  
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates Release              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/main Packages                
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/restricted Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/main Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/restricted Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/universe Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/universe Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_ZA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_ZA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_ZA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_ZA
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Fetched 190B in 4s (44B/s)
Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
name@name-desktop:/var/lib/apt$ 

Now what do i?
Run what cariboo907 has given me?

---

### Post by styxcoverbnd on 2009-10-16
Have you tried changing to a different server to get updates from? (I'm at work so I'm not on my ubuntu boxes) But I believe you can change which server you get updates from by 'System' -> 'Administration' -> 'Software Sources' and there should be a button to change the server in the bottom right hand corner

---

### Post by phillw on 2009-10-16
Hi,

as always, the answer is in the error message ...

```
name@name-desktop:/var/lib/apt$ mv lists lists.old
mv: cannot move `lists' to `lists.old': Permission denied

```you need to

```
sudo mv lists lists.old
```a couple of things to note about sudo.
When you 1st issue sudo, it will prompt you for your password - It then allows about 10 minutes of you issuing sudo commands without re-entering the password
And, a dead handy one for what happened to you...
```
sudo !!
```Issues the command you had just typed with sudo at the start of it - handy for if you type a long command in, but forget to put sudo at the start.

As I wasn't actually carrying out the commands on my machine, I didn't check to see if you needed the sudo for the mv command, sorry for any confusion that caused you :-(



Hopefully, that'll all know work.:P

Regards,

Phill.

---

### Post by cariboo on 2009-10-16
Sorry about that, you have to add sudo before all the commands. Any time you are doing any file manipulation outside your home directory, everything must be done as root. If you don't want to type sudo before each command, type:

```
sudo -i
```

this will drop you to command shell and allow you to run the commands as root.

---

### Post by dr13 on 2009-10-18
Guys i have received two update packages since I last posted. I don't seem to be having the problem anymore but will keep your'll posted if it happens again.

thanks a million guys, your help is really appreciated :cool:

---

