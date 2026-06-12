---
title: "Access Denied in users home folders"
date: 2013-04-05
forum: Server Platforms
---

### Post by JnPson on 2013-04-05
I have installed Ubuntu 12.04.2 Server on a Dell poweredge R710 using LVM. I have installed DNS, DHCP and Samba4, I have created a domain with provisioning and I have created users with roaming profiles and *H:* as their home folder. I am using Adminpak for Windows server 2003 and administrating it from an XP machine. 

To create roaming user profiles I first created a folder named *profile* and created the profile with *\\dc01\profile\%USERNAME%.* That works just fine and users can log on to any computer with their profile. I then created a folder named *hem* for the users home folders and used *\\dc01\hem\%USERNAME%* and this is where things goes wrong. 

This is the error: 

```
The \\dc01\hemkatalog\clark home folder was not created because you do not have create access on the server. The user account has been updated with the new home folder value but you must create the directory manually after obtaining the required access rights. 
```

Here is my smb.conf

```
root@DC01:~# testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Unknown parameter encountered: "server role"
Ignoring unknown parameter "server role"
Processing section "[netlogon]"
Processing section "[sysvol]"
Processing section "[profile]"
Processing section "[profiles]"
Processing section "[hemkatalog]"
Processing section "[Hem]"
Loaded services file OK.
ERROR: cache directory /var/cache/samba does not exist
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    workgroup = MYDOMAIN
    realm = MYDOMAIN.LAN
    passdb backend = samba4
    idmap config * : backend = tdb

[netlogon]
    path = /var/lib/samba/sysvol/mydomain.lan/scripts
    read only = No

[sysvol]
    path = /var/lib/samba/sysvol
    read only = No

[profile]
    path = /home/profile
    read only = No
    browseable = No

[profiles]
    path = /home/profiles
    read only = No
    browseable = No

[hemkatalog]
    comment = Hemkataloger for alla deltagare.
    path = /home/hemkatalog
    read only = No
    browseable = No

[Hem]
    path = /home/hem


```

This is the permissions and rights from ls -l: 

```
drwxrwxrwx 3 root    root    4096 Apr  5 11:53 hem
drwxrwxrwx 3 root    root    4096 Apr  2 11:00 hemkatalog
drwxrwxrwx 8 root    root    4096 Apr  2 10:51 profile
drwxrwxrwx 5 root    root    4096 Apr  2 10:52 profiles

```

I have done several attempts to create home folders for the users. The first time I created *hemkatalog *but only Administrator could create files and folders. Now only root can create files and folders within *hem/hemkatalog *

Can any of you see what's wrong here or have you had the same problem created users with home folders?

---

### Post by darkod on 2013-04-05
I didn't understand, how are you actually creating the users on the ubuntu server?

---

### Post by JnPson on 2013-04-05
Througn adminpak from an xp machine.

---

### Post by darkod on 2013-04-05
Are you sure that can create them on a linux filesystem? Only root has those permissions, are you sure it's working?

It seems to me like that is the part that's failing, the creation of a new user. And not samba user, the linux user. Creating the user will make the corresponding home folder too, and set that user as owner of its home folder.

I have no idea what adminpak is about but you can try adding few users on the command line and see if they work as expected. Then you know where the problem lies.

I always mix up the command to add users, was it useradd or adduser. I think they both have something to do with it. :)

If you want users to belong to specific group, etc, you can add options to the command. I guess the man page can give you more details about that. This is what a quick google search says:
[http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/](http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/)

---

### Post by Toxic64 on 2013-04-05
hi,

 I have had the same problem. Here is what I did to create my /User folder:

```

sudo mkdir -m 770 /Users

sudo chmod g+s /Users

```

but that didn't work quite immediately though...

```

sudo chown root:users /Users

```

made it work.

you also have to add this to your smb.conf

```
[Users]
directory_mode: parameter = 0700
read only = no
path = /Users
csc policy = documents
```


Editing again but after further inspection on your testparm command result, your server is not a DC, it only has a standalone server role which could also explain your problem.
I m not sure ADS authentication is possible against a standalone server and I think what you need is a functionnal ADS domain controller.

> **darkod said:**
> Are you sure that can create them on a linux filesystem? Only root has those permissions, are you sure it's working?


Yes it can, thes "Users" folder is a container and has to have the rights for each newly logged user to the active directory to create his homefolder inside it.
each user can only see or edit what's in his own homefolder.

---

### Post by JnPson on 2013-04-07
Toxic64, I will try this tomorrow when I'm back to work and I will post here how things turn out.

---

### Post by Toxic64 on 2013-04-08
Ok, no problem.
As I said, it seems you have a problem with your server. from what I can read from the testparm result your server is not a Domain controller.
```
Server role: ROLE_STANDALONE
```

which means your users haven't got anything to authenticate against, unless you have another Domain controller somewhere else.

Did you install Samba 4 from apt-get or did you compile from source via git?
what version of samba 4 are you running? (samba -V to find out)

---

### Post by darkod on 2013-04-08
So, does that mean we are going back to what I said, it doesn't actually create users on linux filesystem? You seem to say "you need functional Active Directory contoller" and this adminpak program seems only to help with the GUI to manage users which at the end are authenticating against an AD.

But if you have only your samba server, adminpak doesn't do anything for you since it doesn't actually create users on linux for you. There is a big difference again simply authenticating a user against existing AD and creating the user in your linux server. The OP seems to think it can do that, and from what has been said so far it doesn't look like that to me. Again I say, I might be wrong.

I don't know how many users we are talking about, but especially if there is not a huge number of users, I would say consider creating them in linux and that's it. Don't rely too much on GUI tools that are based on windows and AD, especially if you have no AD running.

From what I have seen so far, I doubt this adminpak helps with OpenLDAP too. I mean what's the point if it needs a running AD server?

PS. You can very easily check whether the home folders get created at all, I think they don't. Just open /home and check if you have the home folders off all users that you expect. I think this adminpak can't create anything on linux, but if you create the user on the server yourself, it will work. Try it with one user. Creating a user on linux creates the home folder automatically.

---

### Post by Toxic64 on 2013-04-08
> So, does that mean we are going back to what I said, it doesn't actually  create users on linux filesystem? You seem to say "you need functional  Active Directory contoller" and this adminpak program seems only to help  with the GUI to manage users which at the end are authenticating  against an AD.

Well actually not.
 Samba 4 has AD integration. you can create or join an Active directory domain with Samba4 without an actual Windows server. Adminpak helps you with your samba4/AD administration and it works just great.
The AD creates the Users home folder on the linux file system but for it to work you have to have a working DC wether its Samba4 acting as AD or Microsoft AD doesn't matter.

As a matter of fact, it doesn't create the users on your linux, it creates the users in the AD database/ users Organizational Unit. but the AD administrator account with which you create the users and do other tasks has rights on the linux filesystem through Samba4.  

For instance I have a full Samba4 Active Directory with 5 Samba4 servers replicating, DNS working etc...none of those 5 servers is a windows server...(which is cool)
I have adminpak installed on windows 7 machine and doing all my administration from there wether it's AD administration or DNS or GPo (Group policy Objects).
Samba4/Ad domains are just great.

---

### Post by JnPson on 2013-04-08
I did a clean install of Ubuntu server 12.04.2 and chose SSH only, during install to be able to admin it. I then installed samba4 with apt-get, then I ran provisioning:
```

/usr/share/samba/setup/provision --realm=mydomain.lan --domain=MYDOMAIN --adminpass='Test123' --server-role=dc
```

I'm pretty sure it is a domain controller, even though the testparm result shows otherwise. I have added several XP machines to the domain, and I've created users with roaming profiles. Both computers and users can authenticate against the server and everything but making home folders works. 

I believe there is a new version of testparm I could run but I have forgotten the command, testparm for samba 4. Correct me if I'm wrong. 

The version of samba4: 

```
root@DC01:/# samba -V
Version 4.0.0alpha18
```



I did what you suggested.

```
root@DC01:/# mkdir -m 770 /users
root@DC01:/# chmod g+s /users
root@DC01:/# chown root:users /users

```

I edited smb.conf and added:

```
[Users]
        directory_mode: parameter = 0700
        read only = no
        path = /users
        csc policy = documents
```

Administrator can now create home folders for the users, but users can't access it.

//Edit
[http://wiki.samba.org/index.php/Samba_AD_DC_HOWTO](http://wiki.samba.org/index.php/Samba_AD_DC_HOWTO)
The command is [I]samba-tool testparm
[/I]```
root@DC01:/# samba-tool testparm
Press enter to see a dump of your service definitions

# Global parameters
[global]
    server role = domain controller
    workgroup = MYDOMAIN
    realm = mydomain.lan
    netbios name = DC01
    passdb backend = samba4

[netlogon]
    path = /var/lib/samba/sysvol/mydomain.lan/scripts
    read only = No

[sysvol]
    path = /var/lib/samba/sysvol
    read only = No

[profile]
    path = /home/profile
    read only = No
    browseable = No

[profiles]
    path = /home/profiles
    read only = No
    browseable = No

[Users]
    path = /users
    read only = No
    csc policy = documents
    directory_mode: parameter = 0700

[hemkatalog]
    comment = Hemkataloger for alla deltagare.
    path = /home/hemkatalog
    read only = No
    browseable = No

[Hem]
    path = /home/hem

```
//

---

### Post by darkod on 2013-04-08
Aha. So, if you don't need a windows server, what is running the AD? The samba server? I was under the impression the term AD goes for windows only, linux usually uses LDAP. Am I wrong?

I know samba has AD integration but I always thought (and the tutorials I have seen usually say that too) that in that situation you have windows AD server and samba can integrate with it, I understand that.

---

### Post by Toxic64 on 2013-04-08
the Samba4 server is indeed running the Ad with all the Ms AD schemas etc so you don't need a windows server anymore to do it.

AD is an LDAP too, just different one from OpenLDAP or eDirectory etc.

that's an alpha version. Git has Samba 4.0.4 which is lastest stable Final version of samba 4. 
so I'd advise you to set it up via GIT .
I can provide you with a simple script I have made that does it just fine if you would like it.


First time I tried the Alpha version I had tons of problems.

---

### Post by JnPson on 2013-04-08
Yes, that would be great. Do I need to remove the aplha version and run provisioning again? If so I would have to start all over again. 
I'm pretty new with linux so I could need some pointer on how to use and run the script. 
Thanks.

---

### Post by JnPson on 2013-04-08
> **darkod said:**
> 
PS. You can very easily check whether the home folders get created at all, I think they don't. Just open /home and check if you have the home folders off all users that you expect. I think this adminpak can't create anything on linux, but if you create the user on the server yourself, it will work. Try it with one user. Creating a user on linux creates the home folder automatically.

Yes, initial users got their home folders created under /home when I used Adminpak. I don't think there is any other way to create users in samba4, other than local users, like you describe.

---

### Post by Toxic64 on 2013-04-08
I' d advise to have a clean server setup as I absolutely don't know how to remove the alpha version.

There are two script files and one configuration file for samba4 to start at boot with upstart

Copy then on a share on your windows machine if you have one

you need to edit the variables at the begining of the Samba-1.sh and samba-2.sh files according to your setup (ask if you need help)

then mount a cifs share:(you might need to install cifs-utils)

```
mount -t cifs //<IPadress>/share /mnt/scripts -o username=<username>,password='whatever password you have for the username'
```

then make those scripts executable like that:
```
sudo chmod +x /mnt/scripts/samba-1.sh
sudo chmod +x /mnt/scripts/samba-2.sh
```

run samba-1.sh as root and reboot when it tells you.After reboot, remount your share and just run samba-2.sh as root.

the script provisions tha domain with SAMBA_INTERNAL DNS not BIND. SAMBA_INTERNAL DNS can be administered with adminpak or RSAT dnsmgmt.msc console.


if any help is needed, just ask.

---

### Post by JnPson on 2013-04-08
I should be able to run apt-get purge samba4 and then use this script. I have bind9 and isc-dhcp-server installed as well, but then again, the server is not in production yet. 
Anyway I think I will test this on a virtual machine first, just to make it right when I run it on the poweredge server. 

Thanks for the script.

---

### Post by Toxic64 on 2013-04-08
I have a little question: does your samba4 server runs at boot or do you have to start it manually everytime you reboot?

---

### Post by JnPson on 2013-04-08
It runs at boot. I don't have to start it manually.

---

### Post by Toxic64 on 2013-04-08
Ok cause I have this probleme with Samba4.0.4 does'nt have a working startup script so I have to start it manually at every reboot... but I'm working on it.

Samba4.0.5 stable is out today!!! the script I provided earlier will install latest stable release so that ll be 4.0.5.

---

### Post by JnPson on 2013-04-09
I have tested the script and failed several times. Or I think it failed. The scripts stops at: 

                        ```
[SIZE=2]*============================SAMBA4 DOWNLOAD AND SETUP ==============*[/SIZE]
 [SIZE=2]*Cloning into 'Samba4'...*[/SIZE]
 [SIZE=2]*remote: Counting objects: 1113478*[/SIZE]
 [SIZE=2]*remote: Compressing objects: 100% 251305/251305, done.*[/SIZE]
 [SIZE=2]*Remote: Total 1113478 (delta 861734), reused 1107421 (delta 856423)*[/SIZE]
```

 
I have no clue why.
I have tried it on several virtual machines and I thought it might work better on "bare metal", but the result is the same. :(

---

### Post by Toxic64 on 2013-04-09
trying again right now.maybe a problem with git tree due to S4.05 getting out today. Ill tell you what

---

### Post by JnPson on 2013-04-09
Ok. Is it possible to stop the script without destroying something, and can I restart it and get the expected result?

---

### Post by Toxic64 on 2013-04-09
no problem here with the same script. I think it was temporary . you should try it again.

ctrl + C will stop the script.
you should delete the samba 4 folder prior to starting again and comment those lines in the script before launching it again: 

```
sed -i 's/dhcp/static/g' /etc/network/interfaces
echo "    address $IP
    netmask $NM 
    network $NW 
    broadcast $BC
    gateway $GW 
    dns-nameservers $NSI $NSE
    dns-search $FQDN ">> /etc/network/interfaces
    
# Configuration du fichier hosts     
sed -i 's/127.0.0.1    localhost/127.0.0.1    localhost.localdomain    localhost/' /etc/hosts
sed -i  "s/127.0.1.1    $HN"/"$IP    $HN"."$FQDN    $HN"/"" /etc/hosts
```

Ok so I just finished setting up Samba 4.0.5 on a new VM without any problem
Samba4 server is booting at startup with the samba4.conf file I provided in the archive.
everything works like a charm.

Also a few more things.
you have to run the scripts as root.
 you MUST respect the complexity policy for the AD administrator account password (the one you provide as variable in the scripts) - 8 characters minimum - 1 capital letter - 1 number at least

---

### Post by JnPson on 2013-04-10
I ran the script with root-priviliges and used a complex password on a VM. I stops at the same place, without displaying any errors. I am now trying again on a clean, fresh virtual machine and I'll let you know how it goes.

//Edit
I got the give the kerberos realm, even though it was named in the script

---

### Post by Toxic64 on 2013-04-10
I ve had no problem stting it up would you mind sending me your edited script with variables etc so that I can try it?

Kerberos realm an kcc server configuration is normal and comes with the installation of the krb5-user package.

---

### Post by JnPson on 2013-04-10
I've sent you a private message.

---

### Post by Toxic64 on 2013-04-10
I just replied ;)

---

### Post by JnPson on 2013-04-12
The problem was: A permission problem solved with:
```
mkdir -m 770 /Users
chmod g+s /Users
chown root:users /Users
```

//Edit
Forgot this part in smb.conf
```

[Users] directory_mode: parameter = 0700
read only = no
path = /Users
csc policy = documents
```

This problem was solved and users could create files and folders in their own Home Folder. 
A bug in Samba 4.0.0alpha18 did prevent me from creating it as I should so I have installed and configured Samba 4.0.5 from GIT with the great help of [Toxic64]("http://ubuntuforums.org/member.php?u=1807148").

---

### Post by Toxic64 on 2013-04-12
glad I could help. ;)

---

### Post by silingtalusog on 2013-08-23
> mkdir -m 770 /Users
chmod g+s /Users
chown root:users /Users

> [Users]
directory_mode: parameter = 0700
read only = no
path = /Users
csc policy = documents

just tried that in my samba4 AD. but i am still getting that error "access denied" in home folders. i can go "inside" my home share but i cannot paste or save anything on it even if i have full control on it unless i change the owner to myself in the security tab of its folder properties. running  Samba Version 4.2.0pre1-GIT-52d66d8. am i missing something?:confused:

---

### Post by Toxic64 on 2013-08-24
remember 4.2.0pre is still beta (4.1 is on RC2) so not ready at all. use my script to get latest stable version which is 4.0.9 (production suitable)

---

### Post by JnPson on 2013-09-06
I wanted to stay updated with Samba so I did a clone from git with
```
git clone git://git.samba.org/samba.git samba-master
```
Checked for updates with
```
git pull
```
 It downloaded alright and I figured that I would get the latest stable version of Samba 4. I was on 4.0.6 then. 
I did
```
./configure --enable-debug --enable-selftest
make
make install
```
just to get Samba 4.2.0pre. But I wanted the stable version 4.0.9.
I have to ditch that server just because I don't know how to uninstall samba4 from git. 
I would very much like to know if the command 
```

apt-get remove samba4
```
is even possible?

I haven't found a guide on how to uninstall.

How do I remove Samba 4.2.0pre not from the repository?

---

### Post by Toxic64 on 2013-09-06
nope.
it has not been installed from the repos so it's impossible with apt-get.
You'll have to remove it manually.

---

### Post by JnPson on 2013-09-06
Ok.
So I will have to rm +rf on /usr/local/samba to delete subdirs?

Is there any other directories I must delete manually?

---

### Post by Toxic64 on 2013-09-06
Your Samba directory created by git
also edit each file you edited during the tutorial to it's initial state

---

### Post by JnPson on 2013-09-06
There should be an **make uninstall** or **make remove** script from what I've learned just a minute ago. I was too fast and just did an **rm -rf** on Samba without testing this.

I will install a new server with Samba 4.2.0pre or any other version from git and test if the **make uninstall **or **make remove** script exsist.

---

### Post by JnPson on 2013-09-07
The command for uninstalling samba4.2.0pre is 
```
make uninstall
```
It does the uninstall processs, but it leaves all folders on disk, so it feels like it's leaving a mess. 
I dint't get to try ```
make remove
```. 

/JnPson

---

### Post by lingpanda on 2013-09-09
I created and administered home shares following this from the Samba Wiki. [https://wiki.samba.org/index.php/Setup_and_configure_file_shares](https://wiki.samba.org/index.php/Setup_and_configure_file_shares) Worked like a charm.

---

