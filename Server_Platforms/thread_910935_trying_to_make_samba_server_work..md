---
title: "trying to make samba server work."
date: 2008-09-05
forum: Server Platforms
---

### Post by bossyman15 on 2008-09-05
i need to be able to access the folder on xubuntu web server. my other PC are running XP

i went to system --> file share and i get the message saying the service are not installed. it asked me to install the SMB stuff for windows and unticked the other unix option. i click install then i get same popup window saying the service are not installed. so i just click close and added a folder to share.

i checked the package mangaer and i see that samba are installed but i have no clue what to do. i checked the network place in XP and i don't see my shared folder from xubuntu there.

any help would be good.

---

### Post by bullgr on 2008-09-05
hi...

make sure samba is installed:
```
sudo apt-get install samba smbfs
```

then config samba options:
```
sudo nano /etc/samba/smb.conf
```
use command-line text editors. gui text editors (like gedit) make strange things...

after you open smb.conf delete all the contents and copy-paste this:
```

[global]
netbios name = server
server string = server
workgroup = Workgroup
security = share
log file = /var/log/samba.log
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
encrypt pass = yes
wins support = yes

[share_name]
path = /your_mount_folder/your_mount_point
available = yes
browseable = yes
public = yes
writable = yes

```
of course you have to change /your_mount_folder/your_mount_point to your correspont options (ex. /media/c). also you can change the share_name with whatever you like to shown up in the network.

then restart samba:
```
sudo /etc/init.d/samba restart
```
and you are done!!! :guitar:

PS.
deleting all the content in smb.conf and copy-paste the code i give above is the easiest way especialy for newcomers. if you like to challenge yourself change the correspond options i give you in the original smb.conf. it's up to you what you choose.

---

### Post by jerome1232 on 2008-09-05
Also after installing samba for the first time you do have to logout and log back in for your group membership to samba to become effective.

---

### Post by bossyman15 on 2008-09-05
ok good now that "the service are not installed" part are now fixed.

i went ahead and added a folder to share but i still don't see it in my windows network place. I can see my server in Mshome workgroup.

---

### Post by erwall on 2008-09-05
> **bossyman15 said:**
> ok good now that "the service are not installed" part are now fixed.

i went ahead and added a folder to share but i still don't see it in my windows network place. I can see my server in Mshome workgroup.
Try setting the "workgroup" variable to MSHOME in your smb.conf, like this:
```
workgroup = MSHOME
```
then
```
sudo /etc/init.d/samba restart
```

---

### Post by Krupski on 2008-09-05
> **bossyman15 said:**
> ok good now that "the service are not installed" part are now fixed.

i went ahead and added a folder to share but i still don't see it in my windows network place. I can see my server in Mshome workgroup.

Here's a nice simple smb.conf file that may help you. Note that it is intended for a small, in home, private intranet safe behind a firewall and used only by people you trust - as there is NO security in it!

```

root@storage:/etc/samba# cat smb.conf
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash)
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic
# errors.
#
#======================= Global Settings =======================

[global]
        workgroup = WORKGROUP
        server string = Storage Drive
        security = SHARE
        deadtime = 5
        socket options = tcp_nodelay iptos_lowdelay so_keepalive so_rcvbuf=32768 so_sndbuf=32768
        os level = 65
        preferred master = Yes
        wins support = Yes
        create mask = 0644
        directory mask = 0755
        guest ok = Yes
        store dos attributes = Yes
        dos filemode = Yes

[shared]
        comment = storage
        path = /home/shared
        read only = No


```

Note: You will probably wish to edit the workgroup name and the share directory to match YOUR system.

Again, be aware that this creates a totally open, no passwords needed share!

Good luck

-- Roger

---

### Post by bossyman15 on 2008-09-05
> **erwall said:**
> Try setting the "workgroup" variable to MSHOME in your smb.conf, like this:
```
workgroup = MSHOME
```
then
```
sudo /etc/init.d/samba restart
```

it was already set to mshome.

---

### Post by bossyman15 on 2008-09-08
hello? it was like i said i can see my server in mshome group but shared folder will not show up in my network. that's all i need to fix.

---

### Post by jerome1232 on 2008-09-08
what's the output of 'smbtree'?

---

### Post by bossyman15 on 2008-09-08
> **jerome1232 said:**
> what's the output of 'smbtree'?

ummm subtree? you mean the path to which the folder is shared?

if so then 

/opt/lampp/htdocs

---

### Post by jerome1232 on 2008-09-08
no smbtree will output what samba see's on your network.

---

### Post by bossyman15 on 2008-09-08
where can i find subtree?

---

### Post by jerome1232 on 2008-09-08
**S** as in **S**am, **M** as in **M**ary, **B** as in **B**oy, **T** as in **T**om, **R** as in **R**oger, **E** as in **E**dward, **E** as in **E**dward

smbtree, run it in a terminal, should tell what is shared on the network
```
jeremy@lifebane:~$ smbtree
Password: 
MSHOME
HOMELAN
	\\DARKSHORE      		
		\\DARKSHORE\Users          	
		\\DARKSHORE\Public         	
		\\DARKSHORE\print$         	Printer Drivers
		\\DARKSHORE\IPC$           	Remote IPC
		\\DARKSHORE\D$             	Default share
		\\DARKSHORE\C$             	Default share
		\\DARKSHORE\ADMIN$         	Remote Admin
```

That shows there's some computer in the workgroup mshome, and some in homelan, I'm in the homelan workgroup so it list the computers in homelan, there's only one called darkshore, under darkshore it lists the samba shares available.

---

### Post by bossyman15 on 2008-09-09
mmm i tried it and i get this...

```
bossyman15@ubuntu:~$ smbtree
Unknown parameter encountered: "encrypt pass"
Ignoring unknown parameter "encrypt pass"
Password: 
bossyman15@ubuntu:~$ 
```

is this a problem?

---

### Post by bossyman15 on 2008-09-11
> **bossyman15 said:**
> mmm i tried it and i get this...

```
bossyman15@ubuntu:~$ smbtree
Unknown parameter encountered: "encrypt pass"
Ignoring unknown parameter "encrypt pass"
Password: 
bossyman15@ubuntu:~$ 
```

is this a problem?

hello?

---

### Post by jerome1232 on 2008-09-11
srry looks like a problem to me, but I'm not sure what you would do from here.

---

