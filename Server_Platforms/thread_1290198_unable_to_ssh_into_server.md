---
title: "unable to ssh into server"
date: 2009-10-13
forum: Server Platforms
---

### Post by mjfroggy on 2009-10-13
Hello all,

In error I changed a chmod value on the server and now I can not ssh into the server. The issue is I can not recall what directory I changed the chmod on.

So I am wondering if anyone might know off the top of there head what folder and what chmod level would prevent someone from ssh into the server (if it helps my server is in the next room so I am just trying to ssh via my local network)

I am able to reach the server via http:// I also have Smaba setup on the server and am able to get to editsave view files on the drive I have smaba setup on.  So its just ssh I can getin via.

thanks
Jason

---

### Post by benj1 on 2009-10-13
why don't you look through your history for the command ?

---

### Post by wojox on 2009-10-13
Yeah like benji said look in your bash history file. You would normally access your home folder on the server when you log in.

---

### Post by mjfroggy on 2009-10-13
well the last few commands that have been run on the machine are

sudo chmod -R 777 *
sudo chmod -R 755 *
sudo chmod o-rwx tmp

all where run from the root dir

---

### Post by benj1 on 2009-10-13
did you have root permissions ?

if you did you could try reversing execute permissions for every thing then adding them back for /bin /usr/sbin and /usr/bin but i dont know definitely if that would solve it, and even if it did you may get certain errors to do with messed up permissions.

if you didnt have root permissions it should only be your home folder that was affected 

in that case ```
chmod -R -x ~
``` would remove execute permissions for everything, then ```
chmod +x
``` everything you actually need execute permissions for.

---

### Post by mjfroggy on 2009-10-13
I had root access when I stupidly changed the chmod levels. 
I also still have root access if I use the monitor that is connected directly to the server to access the command line

So since I had root access what should I do to reverse this issue??

---

### Post by benj1 on 2009-10-13
```
chmod -R -x *
``` then manually add execute permission for /bin etc
but as i said you may still have alot of incorrect permissions that could affect other things, then theres security if youre accessing your server from the internet you probably have quite a few security holes now, i would personally reinstall then follow the steps i outlined above when you readd things from your home folder (unless you have a back up that wasnt on that pc of course)

edit: you may want to do this from a live cd or just chmod -R -x individual directories you dont want to take away execute permissions from chmod

---

### Post by mjfroggy on 2009-10-13
I think I am going to go the route of individually re-chmoding each directory until I am able to ssh in. Question though is there no one specific directory that would be the one I should try first since as I said I am able to access the var/www dir and read/write to it. The server is also not accessable to the outside world

thanks

edit
when I go to chmod my bin dir I get the following message

sudo /var/run/sudo/writeable by non owner (040777) should be 0777

---

### Post by benj1 on 2009-10-13
it could be anything, someone with more expertise may be able to help you more, but at the moment all of your configuration files have execute permissions, and everybody has read,write and execute permissions for everything. 
at the moment you dont even need to be root to do anything because you as the normal user have all permissions anyway.

---

### Post by Wim Sturkenboom on 2009-10-13
SSH might be prevented because there is a file in .ssh in the user's home directory that should have 600 as the permissions (not sure anymore which one). That might be a hint.

Getting permissions right is close to impossible in my opinion unless you have a reference machine. You better backup and re-install. If the latter is not an possibility, consider a temporary server.

---

### Post by mjfroggy on 2009-10-15
Hello Wim Sturkenboom,

I wanted to ask you where is the .ssh file you are refering too?
I ssh into a development box I have (just wanting to see if I can find the .ssh file you mention in that server)

so I ssh in I then go cd .. which gets me into /home directory
I then go ls and see my username so I cd into that directory and do a ls and no files are listed?

So just wondering if you can give me the full path to the .ssh file you mention

thanks

---

### Post by benj1 on 2009-10-15
i *think* ~/.ssh only contains private keys if youre using them, if your just using the ssh password you might not have one, also you can redefine where to look in /etc/ssh/sshd_config, so have a look in there, but the default is ~/.ssh

ps you are using ls -a arent you ?

---

