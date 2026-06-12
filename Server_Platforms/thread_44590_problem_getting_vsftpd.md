---
title: "problem getting vsftpd"
date: 2005-06-26
forum: Server Platforms
---

### Post by mythalethe on 2005-06-26
When I try:

apt-get install vsftpd

I am getting an error message that says:

Package vsftpd is not available, but is referred to by another package.  This may mean that the package is missing, has been obseleted, or is only available from another source.
E: package vsftpd has no installation candidate


Any idea on how to find this program?

thanks,

Mythalethe

---

### Post by mythalethe on 2005-06-27
[QUOTE=mythalethe]When I try:

apt-get install vsftpd

I am getting an error message that says:

Package vsftpd is not available, but is referred to by another package.  This may mean that the package is missing, has been obseleted, or is only available from another source.
E: package vsftpd has no installation candidate


Any idea on how to find this program?

thanks,

Mythalethe[/QUOTE]
 (Just in case another total newbie like me looks at this...)

From: [http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories)

Q: How to add extra repositories?

   1. Read General Notes
   2.

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

   3. Find this section

...
## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

   4. Replace with the following lines

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

   5. Save the edited file (sample)
   6.

sudo apt-get update

---

### Post by abood on 2005-06-29
hey mythalethe,
where is the proplem dude ?
u had already answered your solution :) ?
plz tell me if u faced any proplem in configing the Vsftpd server. :)
Abood

---

### Post by mythalethe on 2005-06-30
I am having a permissions problem where I can access files with an FTP client and download them, but I cannot make a new folder or upload yet.  My FTPsite folder permissions are set to allow owner and group RWE and others to R and Execute.  Do I need to allow others to write as well.

I am not sure what else might cause this problem, but the server seems to be working fine if I could just figure out what I missed when setting it up!

cheers,

M

---

### Post by abood on 2005-06-30
hey mythalethe,
i think ur proplem is in the vsftpd.conf file, there u might find the soultion for ur proplem, u can chroot ur folders and allow the private users to upload or download files, and the annou users also, try to check it and read on the offical vsftpd site the user help commands, and also there is ready scripts for use, and im telling u that its much easier than u think :).
tell me what happend with u :).

---

