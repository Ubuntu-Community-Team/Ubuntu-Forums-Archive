---
title: "vsftpd with pam mysql libgcc_s.so.1 missing"
date: 2012-03-07
forum: Server Platforms
---

### Post by hatsch on 2012-03-07
i was upgrading my server from ubuntu 10.04 to 12.04 yesterday.

i have vsftp set up to authenticate with a mysql database wich worked fine with ubuntu 10.04

but now when i connect with a ftp client i get an error response from the server:

[B]Invalid reply: "libgcc_s.so.1 must be installed for pthread_cancel to work"
[/B]
anonymous logins work so my guess is that the problem must be with libpam-mysql

there is a file called libgcc_s.so.1 in /lib/x86_64-linux-gnu/ but vsftpd doesn't seem to find it.

any ideas for hot to fix this are very welcome.

there is also an error showing in dmesg output:
> [70706.832118] vsftpd[18878] general protection ip:7f5e43045b07 sp:7f5e40cf0590 error:0 in libc-2.15.so[7f5e4300c000+1b1000]


---

### Post by MiniMeCZ on 2012-04-17
Hi, same problem here. Have you solved it?

---

### Post by compusys on 2012-04-28
I made the same mistake.

So i tried to fix it by adding to 

/etc/ld.so.conf the path to libgcc_s.so.1 "
include /lib/x86_64-linux-gnu/
include /lib/
include /lib/i386-linux-gnu/
include /usr/lib32/
include /lib32/
"
and running ldconfig

but with no chance.

the only ftp acoount working is my root account.

Anybody else? have you find other options to try?

> **hatsch said:**
> i was upgrading my server from ubuntu 10.04 to 12.04 yesterday.

i have vsftp set up to authenticate with a mysql database wich worked fine with ubuntu 10.04

but now when i connect with a ftp client i get an error response from the server:

[B]Invalid reply: "libgcc_s.so.1 must be installed for pthread_cancel to work"
[/B]
anonymous logins work so my guess is that the problem must be with libpam-mysql

there is a file called libgcc_s.so.1 in /lib/x86_64-linux-gnu/ but vsftpd doesn't seem to find it.

any ideas for hot to fix this are very welcome.

there is also an error showing in dmesg output:

---

### Post by compusys on 2012-04-28
I have a solution what worked for me.

I instaled libpam-chroot and libpam-ldap i don't know which one made it but after instalin these two packages my fileziila sayed another error  something like 500 OOPS: vsftpd: refusing to run with writable root inside chroot() but this is easy to fix if you have the users in sibdirectories you will have to chmod a-w the user root directory.
Before these two thing i made a new compile of vsftpd from their site source code. but with no chance.
please tell me if this works on your maschine too.

bye

---

### Post by rcane on 2012-04-28
> **compusys said:**
> I have a solution what worked for me.

I instaled libpam-chroot and libpam-ldap i don't know which one made it  but after instalin these two packages my fileziila sayed another error   something like 500 OOPS: vsftpd: refusing to run with writable root  inside chroot() but this is easy to fix if you have the users in  sibdirectories you will have to chmod a-w the user root directory.
Before these two thing i made a new compile of vsftpd from their site source code. but with no chance.
please tell me if this works on your maschine too.

bye

By installing libpam-ldap I get the same new error as you.
But removing write permission doesn't help so much...

Have you tried the new vsftpd version 3.0.0?

---

### Post by compusys on 2012-04-29
Yes i have tried.
It helped me for a few hour now i am getting the folowing message
553 Could not create file. when i try to upload a file.
yesterday after installing ldap and putting vsftpd 3. it worked fine now i have upload error.

---

### Post by rcane on 2012-04-29
> **compusys said:**
> Yes i have tried.
It helped me for a few hour now i am getting the folowing message
553 Could not create file. when i try to upload a file.
yesterday after installing ldap and putting vsftpd 3. it worked fine now i have upload error.

I'm pretty sure it's because you removed write access for all users: chmod a-w.

---

### Post by compusys on 2012-04-29
I found why because the sub folder and folder where uploaded by my root user so it had write acess just for that user. i deleted them and recopied with secondary user and voila it is working fine.

---

### Post by bvidinli on 2012-09-16
I still have same problem.
using vsftpd 2.3.5, Ubuntu 12.10

I also tried installing libpam-ldap, that did not help.
And, why should I install it, I dont want any extra component such as ldap... 

anyboyd knows why ?



kernel: vsftpd general protection ip:7f881af02ac7 sp:7f8817cf8590 error:0 in libc-2.15.so[7f881aec9000+1b2000]


220 Welcome to vsFTPd Server, 
Name (localhost:ehcp): ftp
331 Please specify the password.
Password:
libgcc_s.so.1 must be installed for pthread_cancel to work
Login failed.

---

### Post by kovacssupki on 2012-09-17
ok. verify the user that you have in your vsftpd conf.... you must change it to www-data because this is the user that have rights to /var/www/vhosts or any other subfolders in www. Reply if it works for you..

---

### Post by bvidinli on 2012-09-17
vsftpd.conf is this:


listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
nopriv_user=vsftpd
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
guest_enable=YES
guest_username=vsftpd
local_root=/var/www/vhosts/$USER
user_sub_token=$USER
virtual_use_local_privs=YES
user_config_dir=/etc/vsftpd_user_conf
local_max_rate=2000000 # bytes per sec, 2Mbytes per sec
max_clients=50 # to avoid DOS attack, if you have a huge server, increase this..
ftpd_banner=Welcome to vsFTPd Server, managed by EHCP (Easy Hosting Control Panel, [www.ehcp.net](www.ehcp.net) )



I used this before too, this was working up to Ubuntu 11.10
what do I need to fix ?


Other info:


apt-get install ia32-libs :  not worked
apt-get install libc6-i386 lib32gcc1 : not worked

may be the cause?: "FC5 is using GLibC v2.4, which is not compatible with most of the EDA tools. So, I'll recommend FC4 instead."

---

### Post by bvidinli on 2013-03-03
after months, still same problem. many people are using vsftpd, many people living this situation, 
I am still looking for a solution if I find time to deal..

"This error is fixed by adding /lib to /etc/ld.so.conf and running ldconfig" :  not worked

---

### Post by sean.m.durkin on 2014-01-12
[TABLE]
[TR]
[TD="class: votecell"]     0     down vote        
              [/TD]
                [TD="class: answercell"]                  I had the same problem, running vsftpd on Ubunto 13.10, and none of the suggestions worked.
  After a lot of googleing, I stumbled upon the same issue in the [Redhat Bugzilla]("https://bugzilla.redhat.com/show_bug.cgi?id=913519")
  Their solution, which worked for me: recompile the vsftpd package  after modifying the source file defs.h (the DEFINE VSFTP_AS_LIMIT has to  be changed to the value "400UL * 1024 * 1024"). I don't claim to  understand what that does, but now everything works perfectly for me.
  To recompile the package, follow these steps (this is for Ubuntu 13.10, but should work similar for other releases):
  
[LIST=1]
[*]add source repositories to /etc/apt/sources.list by adding the line deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy main universe restricted
[*]Update the package lists: sudo apt-get update
[*]Install some utilities needed for compiling stuff: sudo apt-get install fakeroot build-essential
[*]Get everything that is needed for compiling vsftpd: sudo apt-get build-dep vsftpd
[*]Get the vsftpd sources: apt-get source vsftpd (this works as a non-root user)
[*]Change VSFTP_AS_LIMIT in the defs.h file to the value 400UL * 1024 * 1024
[*]Commit the changes, or compile will fail: dpkg-source --commit. This will create a new patch file. You are then prompted to enter a name and info for that post.
[*]Re-build vsftpd: fakeroot buildpackage. It should compile, and there should be a new .deb-file created.
[*]Install this newly created package: dpkg --install vsftpd_3.0.2-1ubuntu2_amd64.deb (change the file name accordingly)
[/LIST]
  That's it, worked for me. It might be a good idea to put that package  on hold so it will not be overwritten when a new official package is  released by the Ubuntu team.
  **Update:** I just tried this on Ubuntu 12.04 LTS, worked as well.
      
[/TD]
[/TR]
[/TABLE]

---

### Post by Z3r0- on 2014-01-24
Unfortunately I have this bug too. I've no idea how to solve it.

On my Saucy 13.10 in VMWare - Installing vsftpd then libpam-mysql - results in this error message on connect. I installed libpam-ldap and the error message disappeared. Have reconfirmed this is a workaround by removing and reinstalling etc.

However, on my Production machine, the EC2 instance  of 13.10, installing libpam-ldap doesn't fix the problem.

I'm a bit stumped, both machines are x86_64 kernels (confirmed with uname -m).

ld.so.conf.d already has all the correct paths.

Tried stuff I found off the net that worked for others, but all fails for me: 
(FAILS) Installing ia32-libs  - which is now  lib32z1 lib32ncurses5 lib32bz2-1.0
(FAILS) Installing lib32gcc1
(FAILS) Installing libgcc1:i386 (requires gcc-4.8-base:i386 libc6:i386 libc6-amd64:i386)
(FAILS) LD_PRELOAD=/lib/x86_64-linux-gnu/libgcc_s.so.1 sudo vsftpd
(FAILS) LD_PRELOAD=/lib/i386-linux-gnu/libgcc_s.so.1 sudo vsftpd
(FAILS) LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/lib/x64_64-linux-gnu/ ; export LD_LIBRARY_PATH ; sudo vsftpd

(FAILS) I have also tried compiling the source code with the fix in the above post - DEFINE VSFTP_AS_LIMIT has to be changed to the value "400UL * 1024 * 1024"  - it doesn't work for me.

ldconfig -p | grep libgcc_s.so.1
        libgcc_s.so.1 (libc6,x32) => /usr/libx32/libgcc_s.so.1
        libgcc_s.so.1 (libc6,x86-64) => /lib/x86_64-linux-gnu/libgcc_s.so.1
        libgcc_s.so.1 (libc6,x86-64) => /lib64/libgcc_s.so.1
        libgcc_s.so.1 (libc6) => /lib/i386-linux-gnu/libgcc_s.so.1
       libgcc_s.so.1 (libc6) => /usr/lib32/libgcc_s.so.1


gcc --print-file-name=libgcc_s.so.1
/lib/x86_64-linux-gnu/libgcc_s.so.1

---

### Post by Z3r0- on 2014-01-24
> **Z3r0- said:**
> 
(FAILS) LD_PRELOAD=/lib/x86_64-linux-gnu/libgcc_s.so.1 sudo vsftpd
(FAILS) LD_PRELOAD=/lib/i386-linux-gnu/libgcc_s.so.1 sudo vsftpd


Seems that command is wrong anyhow - it's meant to be:
sudo LD_PRELOAD=/lib/x86_64-linux-gnu/libgcc_s.so.1 vsftpd

In fact, this does get rid of that error message about libgcc_s.so.1 . But now i'm unable to log in. There's nothing in /var/log/auth.log. Which suggests the plugin libpam-mysql isn't working at all for some reason on the EC2 instance.

---

### Post by noliemiliano on 2014-07-02
has anyone could solve this? i have the same issue on ubuntu 12.04 64bit, but in my development server Ubunutu 12.04 32bit its working well, and thats the only diference (64 vs 32 bit, no small difference, but the only one)... i've tried every solution but still got the issue

---

