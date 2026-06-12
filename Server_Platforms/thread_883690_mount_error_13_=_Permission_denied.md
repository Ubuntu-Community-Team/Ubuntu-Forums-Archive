---
title: "mount error 13 = Permission denied"
date: 2008-08-08
forum: Server Platforms
---

### Post by klcom on 2008-08-08
I have Ubuntu Server 8.04.1 and i can't mount shared folders with a samba sistem.


root@ServUbuntu:~# mount -t smbfs //192.9.201.5/basket /area/basket -o username=xxx,password=xxx
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

Thx!

---

### Post by Tha-Fox on 2008-08-08
Did you take a look at the man pages suggested? Maybe you find the answer there?

---

### Post by pparks1 on 2008-08-08
change your mount command from mount -t smbfs to mount -t cifs instead.

---

### Post by klcom on 2008-08-08
I change it and nothing......:confused:

root@ServUbuntu:~# mount -t cifs //192.9.201.5/basket /area/basket -o username=xxx,password=xxx
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

---

### Post by a.thomas on 2008-08-08
Try this...

```
mount //192.9.201.5/basket /area/basket -t cifs -o <DomainName>/username=xxx,password=xxx
```

---

### Post by klcom on 2008-08-11
Nothing..... help please.... ](*,)

root@ServUbuntu:~# mount //192.9.201.5/basket /area/basket -t cifs -o 192.9.201.5/username=xxx,password=xxx
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

Thx!

---

### Post by Tha-Fox on 2008-08-13
Just a guess, a hopeless one, but try using normal (not root) shell and sudo.

---

### Post by klcom on 2008-08-20
Somebody can't help me!?:(

---

### Post by PerJensen on 2008-08-21
Is the smbfs package installed on your system ?, that usually escapes me

/Per

---

### Post by klcom on 2008-08-22
Yes, i have it....

i am searching in the www and find that is a reconized problem from ubuntu. Becouse change smbfs for cifs, and not suport old protocols...

But in mandriva 2008 all works perfectly....

i don't know i am very lost.

thks!

---

### Post by PerJensen on 2008-08-22
This is my entry in /etc/fstab

//192.168.2.10/pj       /home/pj/balrog         cifs uid=pj,credentials=/root/.smb-password-pj.txt,workgroup=CPH,iocharset=utf8,unicode 0 2

all on one line (!), as you can see we have a workgroup "CPH", i specify UFT-8 as charset

This works nicely and after I did this (see [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/212019](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/212019)) :
cd /etc/rc0.d
# mv S31umountnfs.sh K15umountnfs.sh
cd /etc/rc6.d
# mv S31umountnfs.sh K15umountnfs.sh

shutdowns now goes through

/Per

---

### Post by rocketero2008 on 2008-08-25
I also can not mount or browse the network, I installed samba package, smbfs, nts, cifs, ... it's ubuntu 8.04.1 v.5.3.1 DVD 

I used the following commands:

sudo mount -t cifs //hostname/sharename /home/ubuntu/folder -o user=xxx,password=xxx

this will give me the mount error 13 permission denied

the other command I used is this:

sudo mount.nfs hostname:/sharename -v

this will give me an 'internal error' or somthing like that.

when I use nautilius to browse the network it shows the list of hostnames in a domain but when I double-click on a hostname to browse the shares the browser shows a blank content, nothing in it.

---

### Post by cariboo on 2008-08-25
Try:

```
sudo smbmount //hostname/sharename /home/ubuntu/folder
```

You would probably be better off mounting your share in /media

Jim

---

### Post by rocketero2008 on 2008-08-25
> **cariboo907 said:**
> Try:

```
sudo smbmount //hostname/sharename /home/ubuntu/folder
```

You would probably be better off mounting your share in /media

Jim


issueing that command also gives me this message:

"mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)"

---

### Post by Carbonfusion on 2008-08-25
Have you tried checking for extra spaces or tabs at the end of the username and password? That solved the problem on my system.

---

### Post by rocketero2008 on 2008-08-25
> **Carbonfusion said:**
> Have you tried checking for extra spaces or tabs at the end of the username and password? That solved the problem on my system.

I have tried  all combinations using the commands "smbmount" and "mount" with several file types as cifs, smbfs and nothing works.

Someone may ask, have you check the network configuration to see if it is setup properly?, well I just used the command line to ping the remote host by IP Address and by dns-hostname and they work fine, the replay was just what one expected. I used the terminal window and the network tools for it.

I am running Ubuntu in vmware, but that should not be the problem
I tried mounted the remote share using NFS with the "mount.nfs" command:

root@ubuntu8041:/home/user# mount.nfs hostname:/sharename /home/user/test -v

I get this result:
mount.nfs: timeout set for Mon Aug 25 19:16:19 2008
mount.nfs: text-based options: 'addr=192.168.1.152'
mount.nfs: internal error

I research about this NFS mount command and found out that there is an error which other users reported, and supposedly there is a lengthy fix for it at [https://bugs.launchpad.net/ubuntu/+bug/213444/comments/23](https://bugs.launchpad.net/ubuntu/+bug/213444/comments/23) which I followed very carefully but at the end I got the same result.

running out options here.

PS, I also have this problem with a KNOPPIX LIVE_CD.

---

### Post by rocketero2008 on 2008-08-29
**[SIZE="2"]I jut want to report that after a long research I finally found what the problem was[/SIZE]**

First of all I found out that it had nothing to do with Ubuntu, that was something that it took me out of track for a long while.

After researching posts on differents linux forums, and based on that knoppix livecd have the same problem, I realized that the problem resided somewhere else. this post game me some ideas: [http://www.linuxquestions.org/questions/ubuntu-63/fstab-my-win-share-wont-mount-boot-but-will-when-i-sudo-mount-a...please-help-456024/](http://www.linuxquestions.org/questions/ubuntu-63/fstab-my-win-share-wont-mount-boot-but-will-when-i-sudo-mount-a...please-help-456024/) as I did some changes to the rc.local and created another bootfile in /etc/init.d folder, but nothing of that helped.

One of the things that kept me trying to find an answer was that from Windows Vista I could open Windows Explorer and see the Ubuntu Shares and even copy files from windows to Ubuntu.

So finally I realized that the windows vista computer that have the shares is part of a small network I have with windows server 2003, so I went to check the security policies on that server 2003 and find out that there is a GPO (group policiy Object) attached to the OU (organizational Unit) where the Windows Vista Computer is located.

So I edited that GPO. the security policies in particular that were affecting the mounting of the windows share in Ubuntu were one of the followings: (I disabled all of them to make sure so anyone reading this may play around with them):

on the GPO open: Computer Configuration > Windows Settings > Security Settings > Local Policies.

Disable the following setting: 
   - Domain Member: Digitally Encript or Sign secure channel data (always)
   = I also disabled the "when Possible", same line as above, just to make sure but may work without disabling it
   - Microsoft Network client: Digital sign communications (always)
   - I also disabled the "if serves agree", same line as above, to make sure but may work without disabling it
   - last line I disabled or not configured was one that says: Network Security LAN Authentication Level wich can be setup to accept only NTLMv2 only with is more secure, but I set it as Not configured.

These can be found also in a computer that is not networked, just at the RUN command type MMC and from there open GROUP POLICY EDITOR. 

Once I did those changes, I run the command: "gpupdate /force" at the windows vista computer, and rebooted the Ubuntu server and things work as a charm.
Thanks to anyone who reply to this post and helped me solve this issue. 
Regards.

---

### Post by bayforza on 2008-11-23
thanks rocketero that work as a charm...

---

### Post by abjt on 2009-04-04
> **rocketero2008 said:**
> **[SIZE="2"]I jut want to report that after a long research I finally found what the problem was[/SIZE]**

First of all I found out that it had nothing to do with Ubuntu, that was something that it took me out of track for a long while.

After researching posts on differents linux forums, and based on that knoppix livecd have the same problem, I realized that the problem resided somewhere else. this post game me some ideas: [http://www.linuxquestions.org/questions/ubuntu-63/fstab-my-win-share-wont-mount-boot-but-will-when-i-sudo-mount-a...please-help-456024/](http://www.linuxquestions.org/questions/ubuntu-63/fstab-my-win-share-wont-mount-boot-but-will-when-i-sudo-mount-a...please-help-456024/) as I did some changes to the rc.local and created another bootfile in /etc/init.d folder, but nothing of that helped.

One of the things that kept me trying to find an answer was that from Windows Vista I could open Windows Explorer and see the Ubuntu Shares and even copy files from windows to Ubuntu.

So finally I realized that the windows vista computer that have the shares is part of a small network I have with windows server 2003, so I went to check the security policies on that server 2003 and find out that there is a GPO (group policiy Object) attached to the OU (organizational Unit) where the Windows Vista Computer is located.

So I edited that GPO. the security policies in particular that were affecting the mounting of the windows share in Ubuntu were one of the followings: (I disabled all of them to make sure so anyone reading this may play around with them):

on the GPO open: Computer Configuration > Windows Settings > Security Settings > Local Policies.

Disable the following setting: 
   - Domain Member: Digitally Encript or Sign secure channel data (always)
   = I also disabled the "when Possible", same line as above, just to make sure but may work without disabling it
   - Microsoft Network client: Digital sign communications (always)
   - I also disabled the "if serves agree", same line as above, to make sure but may work without disabling it
   - last line I disabled or not configured was one that says: Network Security LAN Authentication Level wich can be setup to accept only NTLMv2 only with is more secure, but I set it as Not configured.

These can be found also in a computer that is not networked, just at the RUN command type MMC and from there open GROUP POLICY EDITOR. 

Once I did those changes, I run the command: "gpupdate /force" at the windows vista computer, and rebooted the Ubuntu server and things work as a charm.
Thanks to anyone who reply to this post and helped me solve this issue. 
Regards.

mate... thanks a lot. i had been struggling to access my DVD drive on Win vista from my Ubuntu. Your suggestions above worked like a charm. Great work !! :KS

I changed only two options i.e. the ones that said "always" and left the others fine. As you suspected, it is not necessary for the access.

---

### Post by Anacrusis on 2009-06-15
Just wanted to throw this out there in case somebody else finds this thread. I had similar issues and for me it was because my account was locked out on the server, must've entered my pw wrong too many times or something.

---

### Post by supi007 on 2009-10-18
This works properly:
I have just switched on the **-o** switch
```
sudo mount.smbfs //server/data/common /mnt/common/ -o user=username
```After I get the Password prompt and that's all.
:KS

---

### Post by cjlindem on 2009-11-07
I am unable to mount to a windows 2003 share using cifs at the command line, providing password:

sudo mount -t cifs //192.168.0.103/data/ /media/happy -o username=myusername,password=******,iocharset=utf8,uid=1000,gid=100,file_mode=0777,dir_mode=0777,rw
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

If I enter the EXACT same command, but delete the password portion:

sudo mount -t cifs //192.168.0.103/data/ /media/happy -o username=myusername,iocharset=utf8,uid=1000,gid=100,file_mode=0777,dir_mode=0777,rw
Password: 

I type in the password at the prompt, and it works perfectly.  I have tried this a dozen times now.. the password is definitely not mistyped in the first command.  Maybe I should file a bug report.

---

### Post by NacIK on 2010-01-24
I have 3 computers.  One using Win 7 and 2 using Ubuntu 9.10.  The computer hooked to the router is running 9.10.  I can print from all 3 computers just fine, but when I try to access files I have problems.  The windows computer access and writes to the shared folder on my 9.10 desktop and laptop just fine, but I can not share files on either 9.10 computers.  Neither Samba or NFS works like it should.  I am kind of new to networking so an Idiots Guide and a walk-through would be helpful.  I could even do remote desktop if needed.  Thanks.

---

### Post by dwroushey on 2010-03-02
This was happening to me as well, and this was the command I was trying to enter:
```
 
sudo mount -t cifs -o username=DOMAIN_NAME\user_name //server/share ~/LocalMountPoint

```
 
The thing that tipped me off, was that I could run this command and it would map just fine:
```
smbclient //server/share ~/LocalMountPoint
```
 
(Note: the machine was joined to the domian with Likewise-open, and I was logged into it as DOMAIN_NAME\user_name which was also in the sudoers file). Then if I added sudo in front of it, it would bomb. So that made me think that when it was running under the root context it was somehow not passing the username and domain correctly.
 
I think I ended up reading the manpages about it and finally came up with this command that works:
```
sudo mount -t cifs -o user=user_name,dom=DOMAIN_NAME //server/share ~/LocalMountPoint
```
 
If you needed to put in the password, the option would look like this:
```
-o user=user_name,dom=DOMAIN_NAME,pass=ClearTextPassword
```
Hope this helps someone.

---

### Post by dwroushey on 2010-03-03
In case people looking at this are interested in mounting windows shares (like the user home) automatically at login, here is what I did to get them working after joining the machine to the domain with Likewise-open:
[http://ubuntuforums.org/showpost.php?p=8906567&postcount=6](http://ubuntuforums.org/showpost.php?p=8906567&postcount=6)

---

### Post by RealG187 on 2010-03-08
I can't mount my Windows box at school for some reason. I get this error, host down, and broken pipe sometimes.

---

### Post by yasir.elsharif on 2010-04-12
1. make the directory
```
mkdir /mnt/myshare
```
2. create credentials file: /root/.creds (you will be root!)
```
 sudo gedit /root/.creds
```
add these lines:
username =myusername
password =mypassword
remember no spaces after "=" sign
Make sure the file is closed permissions...
```
chmod 0600 /root/.creds
```
3. edit /etc/fstab 

```
sudo gedit /etc/fstab 
```
add line:
//shareserver/myshare  /mnt/myshare    smbfs      credentials=/root/.creds,rw,uid=yourubuntuusername,umask=000  0  0
save and close
 
4. Now the share can be mounted just by doing:
```
sudo mount /mnt/myshare
```
 
more info can be found at:
 
[http://www.linux-noob.com/forums/index.php?/topic/1404-how-to-mount-a-windows-share-with-smbmount/](http://www.linux-noob.com/forums/index.php?/topic/1404-how-to-mount-a-windows-share-with-smbmount/)
 
have fun!

---

### Post by yasir.elsharif on 2010-04-13
and if you have spaces in your windows shares:
go to:
[http://ubuntuforums.org/showthread.php?t=27823](http://ubuntuforums.org/showthread.php?t=27823)

or just simply replace the spaces in your /etc/fstab with \040
for example if your share is
My Documents
then the line will be:

//shareserver/My\040Documents  /mnt/mydocs    smbfs      credentials=/root/.creds,rw,uid=yourubuntuusername,umask=000  0  0

---

