---
title: "HOWTO: Setup Local Repository Mirror"
date: 2007-11-01
forum: Tutorials
---

### Post by bmk789 on 2007-11-01
If your like me, you and your friends have several machines running Ubuntu, Kubuntu, or other *buntu variants.  After going through upgrades of all these machines, it can eat a lot of your and Canonical's bandwidth to download all the packages for each machine.  There are other solutions such as apt-proxy, apt-cacher, etc.  But what works best for me is apt-mirror, which creates a mirror of any Ubuntu, Debian, or any other deb repository.  So if you have 20+ GB of hard drive space,  you can setup a local repository mirror to speed up the upgrading process and save Canonical some bandwidth.

**Step 1: Install apt-mirror**

```
sudo apt-get install apt-mirror
``` (Universe repository needed)

**Step 2: Configure apt-mirror**

Configuring apt-mirror is fairly simple.  We just need to modify the /etc/apt/mirror.list file.

Ubuntu users: ```
gksudo gedit /etc/apt/mirror.list
```
Kubuntu users: ```
kdesu kate /etc/apt/mirror.list
```
Ubuntu server users: ```
sudo nano /etc/apt/mirror.list
```

Here's my sample mirror.list configuration:
```
# apt-mirror configuration file

##
## The default configuration options (uncomment and change to override)
##
#
set base_path    /var/spool/apt-mirror
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
#set var_path     $base_path/var
set defaultarch  i386
set nthreads     5
#


##
## Sources
##
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb-amd64 http://archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-amd64 http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-amd64 http://archive.ubuntu.com/ubuntu/ gutsy universe
deb-amd64 http://archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-amd64 http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-amd64 http://archive.canonical.com/ubuntu gutsy partner
deb-amd64 http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-amd64 http://security.ubuntu.com/ubuntu gutsy-security universe
deb-amd64 http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-amd64 http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
clean http://archive.ubuntu.com/ubuntu
clean http://archive.canonical.com/ubuntu
clean http://security.ubuntu.com/ubuntu
```
This configuration mirrors all of Ubuntu's repositories for i386 and AMD64 architectures and stores them all in /var/spool/apt-mirror.  If you don't need to mirror AMD64, just take all the deb-amd64 lines out of the above configuration and it will only download all the i386 repositories. 

NOTE: Make SURE whatever partition stores your /var/spool directory has plenty of space.  Trust me, you do NOT want to download 17GB and find out your partition doesn't have enough space.  If you use a separate /home partition with storage capacity you want to use for apt-mirror, you can do what I did by creating a /home/apt-mirror and making /var/spool/apt-mirror link to it.  That can be done with these two commands: ```
ONLY DO THIS IF YOU HAVE THE SAME SITUATION AS ABOVE!
TYPICAL USERS WONT NEED THIS
sudo mkdir /home/apt-mirror
sudo rm -Rf /var/spool/apt-mirror
sudo ln -s /home/apt-mirror /var/spool/apt-mirror
```

**Step 3: Run apt-mirror**
To have apt-mirror start downloading the repositories, run:
```
sudo apt-mirror /etc/apt/mirror.list
```
I recommend running this command overnight, as it will take several hours depending on your connection speed and what you setup to mirror.  For example, my server is mirroring with the above configuration and downloaded around 35-40GB for i386 and AMD64.  This took between 4-10 hours over my 10mbps cable connection.

**Step 4: Install apache**
For you to be able to use this local mirror normally, you will need a web server to share the directories.  In this guide, I will use apache, but you may prefer to use lighthttpd or some other server. ```
sudo apt-get install apache2
```

**Step 5: Setup links**
We need to now link our local repository folder to our shared apache directory.
```
sudo ln -s /var/spool/apt-mirror/mirror/archive.ubuntu.com /var/www/archive-ubuntu
sudo ln -s /var/spool/apt-mirror/mirror/archive.canonical.com /var/www/archive-canonical
sudo ln -s /var/spool/apt-mirror/mirror/security.ubuntu.com /var/www/security-ubuntu
```

**Step 6: Set apt to use local mirror**
In this step, we'll edit the /etc/apt/sources.list file and replace Ubuntu's repositories with our local mirror.
First, make a backup of the default sources.list.
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup
sudo nano /etc/apt/sources.list
```
This should open a blank file wherein we will paste the following:
```
deb http://127.0.0.1/archive-ubuntu/ubuntu gutsy main restricted universe multiverse
deb http://127.0.0.1/archive-ubuntu/ubuntu gutsy-updates main restricted universe multiverse
deb http://127.0.0.1/archive-ubuntu/ubuntu gutsy-backports main restricted universe multiverse
deb http://127.0.0.1/security-ubuntu/ubuntu gutsy-security main restricted universe multiverse
deb http://127.0.0.1/archive-canonical/ubuntu gutsy partner
```
Then press Ctrl+X then y to save and close the file.
Next, we need to update the repositories to make sure everything is working as expected.
```
sudo apt-get update
```
This should run the same as before we changed the file.  Any errors will need to be addressed.  Post a reply if you have any errors here.

You should also use this step on other machines you want to setup to use this mirror.  You will just need to replace the 127.0.0.1 with the LAN address for machines over LAN or public IP for other machines over the net.

If you have questions, comments, suggestions, feel free to reply, send me a message on IRC (bmk789 on freenode), or send me an email (bmk789@gmail.com)

---

### Post by Gourgi on 2008-06-11
i use apt-mirror as described above and it is working

but when i update the replace sources.list to my clients with those from my local repository a warning is displayed saying that the packages are from an unsigned source

is there any way, .deb package or script to sign the packages of my mirror?
or is there an other solution to this ?

---

### Post by Gewalop on 2008-06-17
thanx

---

### Post by mianda_psi on 2008-06-25
When I try to use apt-mirror I get the following error:

Proceed indexes: [SSSSSSSSSPsh: cannot open mirrors.uwa.edu.au/ubuntu///dists/hardy/main/binary-: No such file
apt-mirror: can't open index in proceed_index_gz at /usr/bin/apt-mirror line 382

Here is my mirror.list file:
```
############# config ##################
#
set base_path    /var/spool/apt-mirror
#
# if you change the base path you must create the directories below with write privlages
#
set mirror_path  $base_path/mirror
set skel_path    $base_path/skel
set var_path     $base_path/var
set cleanscript $var_path/clean.sh
set defaultarch  <running host architecture>
set nthreads     40
set _tilde 0
#
############# end config ##############

deb http://mirrors.uwa.edu.au/ubuntu/ hardy main restricted
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy main restricted

deb http://mirrors.uwa.edu.au/ubuntu/ hardy-updates main restricted
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy-updates main restricted

deb http://mirrors.uwa.edu.au/ubuntu/ hardy universe
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy universe
deb http://mirrors.uwa.edu.au/ubuntu/ hardy-updates universe
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy-updates universe

deb http://mirrors.uwa.edu.au/ubuntu/ hardy multiverse
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy multiverse
deb http://mirrors.uwa.edu.au/ubuntu/ hardy-updates multiverse
deb-src http://mirrors.uwa.edu.au/ubuntu/ hardy-updates multiverse

deb http://mirrors.uwa.edu.au/ubuntu hardy-security main restricted
deb-src http://mirrors.uwa.edu.au/ubuntu hardy-security main restricted
deb http://mirrors.uwa.edu.au/ubuntu hardy-security universe
deb-src http://mirrors.uwa.edu.au/ubuntu hardy-security universe
deb http://mirrors.uwa.edu.au/ubuntu hardy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse universe
deb-src http://mirrors.uwa.edu.au/ubuntu hardy-security multiverse
```I am sure that the source lines are correct - they come straight from my sources.list file and that works without any problems.

Thanks for any help.

---

### Post by ivanoz on 2008-07-01
G'day

hey, looks like your mirror.list is not ok, you have to have like this: ```
deb http://mirrors.easynews.com/linux/ubuntu hardy main restricted universe multiverse
```

you see, there is no / after Ubuntu i think thats all you need to change

cya

---

### Post by twining on 2009-05-05
I am having the same problem with apt-mirror showing the same error as per mianda_psi. 

You will note that there are three /// between ubuntu and dists in the error message.  
If you remove the one in the mirror.list you get two //.

When using Synaptic or Update manager, both work correctly.

This has happened on two installs of Jaunty but does work on another install of Jaunty on a Acer Aspire One.  

Would appreciate help.

Thanks

---

### Post by twining on 2009-06-12
I have found a solution for my problem of two //.

I had " in my 
export ftp_proxy="http://username:password@proxy:8080"/
in the /etc/bash.bashrc file.
Should be
export ftp_proxy=http://username:password@proxy:8080/

The above should read username : password with no spaces between e : p.

can't seem to get rid of the smilies.

Hope this helps.

---

### Post by Menthu_Rae on 2009-06-15
Can anyone please help with apt-mirror running via cron?

I have edited **/etc/cron.d/apt-mirror** to look like this (run at 4am for apt-mirror and 9am for cleanup):

```
#
# Regular cron jobs for the apt-mirror package
#
0 4	* * *	apt-mirror	/usr/bin/apt-mirror > /var/spool/apt-mirror/var/cron.log
0 9	* * *	apt-mirror	/var/spool/apt-mirror/var/clean.sh
```

However, looking at **/var/spool/apt-mirror/var/cron.log** we can see that it *tried* to run but then aborted:

```
Downloading 138 index files using 20 threads...
```

I have tried altering the permissions of the apt-mirror directories using:

```
sudo chown -R apt-mirror:apt-mirror /var/spool/apt-mirror/
```

However, this does not help!

Note that everything works **fine** if I run the following using **sudo**:

```
sudo /usr/bin/apt-mirror
sudo /var/spool/apt-mirror/var/clean.sh
```

Please help! :o

---

### Post by Pradeep Varma on 2012-02-29
hey guys need a help

once a local mirror is setup for ubuntu repository,
will it support different versions of ubuntu ????
pls respond asap .

regards
pradeep

---

### Post by xuampy on 2012-05-06
> **Pradeep Varma said:**
> hey guys need a help

once a local mirror is setup for ubuntu repository,
will it support different versions of ubuntu ????
pls respond asap .

regards
pradeep
Pradeep, I'm just doing some research on this so I cannot answer for sure, the quick way to find out is to set up a virtual machine (such as VirtualBox) running a different version of Ubuntu and then try for it to download from your mirrored repo.

I will be trying something like this in no time so, hopefully I will be coming back with an answer on this.

---

