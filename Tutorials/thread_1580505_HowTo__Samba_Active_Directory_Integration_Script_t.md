---
title: "HowTo : Samba Active Directory Integration: Script tested on win 2003r2 and 2008r2"
date: 2010-09-23
forum: Tutorials
---

### Post by SerbisS on 2010-09-23
The information in this thread has been moved to [https://help.ubuntu.com/community/SambaActiveDirectoryDomainIntegrationScript](https://help.ubuntu.com/community/SambaActiveDirectoryDomainIntegrationScript)

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?t=2012421](http://ubuntuforums.org/showthread.php?t=2012421)

Thread closed.

[CENTER][SIZE=6]**Samba Complete Active Directory Domain Integration**[/SIZE]
**[SIZE=6]tested on windows 2003r2/2008r2[/SIZE]**[/CENTER]
 
[SIZE=3]**What this procedure will do**[/SIZE]
If all runs well you will have a Linux machine completely integrated with your Active Directory server. The shared folders permissions will be managed from your samba server and it will use groups and users taken directly from your AD Domain Controller. Just follow this guide and use the attached script!
 
**[SIZE=3]Preface[/SIZE]**
This procedure was tested with a Linux machine running Ubuntu10.04 and both Windows Server2003 and WindowsServer2008r2 as AD Server.
 
This procedure is taken from a lot of guides but you can find the best guide that I've could find here: [http://wiki.samba.org/index.php/Samba_&_Active_Directory#Authenticating_share_users_and_groups_against_active_directory](http://wiki.samba.org/index.php/Samba_&_Active_Directory#Authenticating_share_users_and_groups_against_active_directory)
 
It's perfectly explicated in all its section and it treats every part more deeply than this one. I really recommend to consult it for every doubt. 
 
[SIZE=3]**Requirements**[/SIZE]
 
 

To join your Linux machine to your Active Directory Domain you need:
[LIST]
[*]access to a Windows Domain Controller with a Domain Administrator account
[*]access to a Linux machine with administrator account (sudoer or root account)
[*]the archive provided with this guide extracted in a folder (do not move or edit the &#8220;templates&#8221; folder or its content)
[/LIST]
For testing I really recommend to use a Linux virtual machine for the first time if it is possible.
 
It's important that the name of the machine you will add to domain has a name shorter than 15 characters. If not you must modify it in /etc/hostname and in /etc/hosts file with your preferred text editor (vi,nano,gedit) and restart the machine:
```
sudo nano /etc/hostname
```> user-laptop```
sudo nano /etc/hosts
```> 127.0.0.1 localhost
127.0.1.1 user-laptopKerberos is time-dependent, so you may have to make sure that the machine time is correct using a protocol like NTP. So synchronize your Linux machine time and date with the same NTP server of your domain with:
```
sudo ntpdate your.domain.ntp.server
```You can also make this command running regularly with crontab:
```
sudo crontab -e
```> # m h dom mon dow command
00 12 * * * ntpdate your.domain.ntp.serverIn this way the command will run at 12:00 o'clock every day with root privilege (visit [http://www.crontabrocks.org/](http://www.crontabrocks.org/) for more information about crontab).
It is also important that your DNS is properly configured as your domain DNS; you can do that using a network manager (like network-manager or wicd) or modifying the /etc/resolv.conf file with the proper configuration. An example:
```
sudo nano /etc/resolv.conf
```> domain yourdomain.local
search yourdomain.local
nameserver 10.0.0.5
nameserver 10.0.0.1Note that if you using a network manager program it's probably that your /etc/resolv.conf configuration will be ignored and replaced by an auto-generated one.
Now test your configuration with the &#8220;nslookup&#8221; command using both server name and his IP; the result might be something like this:
```
nslookup 10.0.0.5
```> Name: WServer2k3
Address: 10.0.0.5```
nslookup WServer2k3
```> Name: WServer2k3
Address: 10.0.0.5If you changed the name maybe it's better to reboot the machine.
 
[SIZE=3]**Running**[/SIZE]
The first thing to do is to edit AD_join.sh variables: open it with your favorite editor
```
nano AD_join.sh
```and modify only the variables in the first part of the script editing only between &#8220;quotation_marks&#8221;: 
> SUPER_USER="myusername" 
DOMAIN="MYDOMAIN" 
FQDN_CAPITAL="MYDOMAIN.LOCAL" 
FQDN="mydomain.local" 
DOMAIN_CONTROLLER="mydomaincontroller.domain.local"do not modify under the WARNING line unless you know what you're doing :) (in Italy we say &#8220;Cazzi tua!&#8221;)
Be sure that AD_join.sh has the execution bit set. Open a terminal, change location in the containing directory, and run the script with root privilege:
```
cd /path/of/script/directory/AD_join
sudo chmod +x AD_join.sh
```Now you can run the script
```
sudo ./AD_join.sh
```The script will install samba, winbind and kerberos in your machine and will change the original configurations files name in *.bkp in order to preserve them (also the entire /etc/pam.d/ directory will be copied to /etc/pam.d.bkp). Then it puts the new files (smb.conf, krb5.conf, nsswitch.conf, system-auth) in proper directories and restart the necessary services. 
Remember that when kerberos visual configuration appear you have to say just <OK> leaving blank the text field.
 
[SIZE=3]**Testing and Joining**[/SIZE]
It's time to test your configuration and try to join in your Active Directory domain.
First of all test your samba configuration file, open a terminal and digit:
```
testparm
```If all runs well you will see your samba's configuration. If not, the program will say you in which line of smb.conf file there is problem. In this case you can try to correct it or you can comment it out with "#" or ";". 
Note that probably Samba will warn you about "winbind separator = +" line, but that should be okay.
Now try to join domain with the command:
```
sudo net ads join -U your_domain_admin
```Change "administrator" with proper domain's administrator name.
If all runs well the domain's administrator password is requested. If not, it's possible that your network connection parameter for DNS server is not properly configured, modify your network configuration or run:
```
sudo net ads join -S your_server_IP_or_name -U your_domain_admin
```If all it's right you will see a "SUCCES" message in your terminal.
Reboot your machine.
Now you can test the joining with:
```
wbinfo -u 
```this gives the domain's users list
```
wbinfo -g
```this gives the domain's groups list
```
sudo  wbinfo -a your_domain_user
```this checks if your_domain_user using password connect to the domain
You can also check the Winbind nsswitch module with getent:
```
getent passwd
getent group
```Note that even if the procedure it's a success, is not sure that "getent" command gives the expected results.
For testing your Kerberos configuration use this:
```
kinit your_domain_user@YOUR_DOMAIN.LOCAL
```Replace "your_domain_user" with an existing user name and replace "YOUR_DOMAIN.LOCAL" with your domain name. If all is set correctly your_domain_user's password is requested. If not a kinit error will be prompted in terminal; in this case you might check your Kerberos configuration. Remember it's important CASE SENSITIVENESS.
 
[SIZE=3]**That's it!**[/SIZE]
Your Linux machine is now joined to your Active Directory.
 
 

Now you can:
[LIST]
[*]manage permissions and access to your shared resource from your samba server
[*]log on the Linux machine using your domain's credentials
[*]browse shares on your Linux machine from your domain computers
[/LIST]
Try to log in trough ssh
```
ssh your_domain_user@linux_machine
```at &#8220;password:&#8221; enter your domain user password
Every time you log on the Linux machine with domain credentials a new home it's created for that user in /home/YOUR_DOMAIN/your_domain_user.
In order to secure those home folders, once them are created, you may run
```
sudo chgrp &#8220;domain admins&#8221; /home/MY_DOMAIN/*
sudo chmod 700 /home/MY_DOMAIN/*
```So your user's homes will be private but accessible from &#8220;Domain Admins&#8221; members. You may wish to automate this by scheduling this commands using cron or crontab, because when a new user logs in the home directory just created has 755 permissions and &#8220;Domain Users&#8221; as group, so all users can browse each other homes. (and that's not such a deal. In italian &#8220;Bella merda!&#8221;)
 
If you want you can read the /etc/samba/smb.conf.bkp (recommended) file to understand what each field signifies. You can also uncomment the end of /etc/samba/smb.conf file in order to share a &#8220;test&#8221; folder (be sure to modify the field with the correct path and info). Remember that every time you change the /etc/samba/smb.conf file you might to restart the service with:
```
sudo service smbd restart
```Manage folder's accesses editing the "valid users" field with the proper users and or groups. 
The syntax is as follow:
> valid users =@YOUR_DOMAIN+your_group YOUR_DOMAIN+your_userNote: no spaces between = and @
This allow all the users of the Active Directory group "your_group" to access the shared folder and to the Active Directory user "your_user" also.
If your groups name have spaces like "Group Name with Spaces" is necessary to put quotation marks:
> valid users =@"YOUR_DOMAIN+Group Name with Spaces"Pay attention to the case sensitiveness of the domain names.
There are a lot of fields you can add or modify in your samba configuration: you can find some example in the preconfigured file (smb.conf) like the &#8220;admin user&#8221; field or the &#8220;[homes]&#8221; sharing option (with which you can share user's home folders to them as they login).
 
Feel free to do all the experiments you want and please, if you find something interesting, post it here! 
 
 
[SIZE=3]**Trubleshooting**[/SIZE]
 
idQp posted some trubleshooting (here the post [http://ubuntuforums.org/showthread.php?t=1580505&highlight=serbiss&page=10](http://ubuntuforums.org/showthread.php?t=1580505&highlight=serbiss&page=10)) tested on Debian 6.0
 
> If you get this error msg: 

"Failed to join domain: failed to connect to AD: Strong(er) authentication required"

you must add the following line to your smb.conf (GLOBAL Settings):

client ldap sasl wrapping = sign

this is because of an microsoft update that enables the ldap signing requirement to your AD.


edit: this howto worked for me on debian 6.0 (squeeze) and windows server 2008 r2
ccsaway posted this ([http://ubuntuforums.org/showthread.php?t=1580505&page=11):]("http://ubuntuforums.org/showthread.php?t=1580505&page=11%29:")

> just installed it on 11.10. works great! THANK YOU SOOOOOOOOOO MUCH

Had to do just one extra thing though, 

apt-get install krb5-user  to test if kinit was working


Couple of things I did after

net groupmap add ntgroup="Domain Users" unixgroup=users
net groupmap add ntgroup="Domain Guests" unixgroup=nogroup
net groupmap add ntgroup="Domain Admins" unixgroup=root                                                                                                                   
\\:D/[SIZE=5]Enjoy[/SIZE]\\:D/

---

### Post by dmizer on 2010-09-26
Subscribed. Thank you for posting this. I have been dreading figuring this out on my own.

---

### Post by luvshines on 2010-09-26
Nice to have scripts and comprehensive guides to solve Samba - AD configuration issues

Great work SerbisS, to start this

I just have some general queries regarding it.

1. smb.conf is missing 'password server' parameter. Isn't that an important one for the configuration

2. When samba and winbind is installed, are they added to startup at general runlevels by default or do we need to add them separately so that setup works fine after restarts

3. Maybe we can also add that since kerberos comes into picture with AD and Samba, make sure that time skew is not too great and within permissible limits. Else join step may complain of 'time skew too great'. Right ?

---

### Post by luvshines on 2010-09-26
Also wanted to add that on samba.org and almost all the other places, the 'winbind' is not added to against 'shadow' entry in /etc/nsswitch.conf file

Don't know why ?? :)

---

### Post by SerbisS on 2010-09-29
First of all thanks to have read (and tested?) this guide.
I'm not an expert but I would try to give you an answer anyway despite my very bad english:
> 1. smb.conf is missing 'password server' parameter. Isn't that an important one for the configuration
The password server parameter it's necessary to delegate authentication to another SMB server, in this case is not necessary because the authentication is already made locally.
> 2. When samba and winbind is installed, are they added to startup at general runlevels by default or do we need to add them separately so that setup works fine after restarts
I never had problems about this; but I think you refer to older Linux machine version where it was necessary to stop winbind, stop and start samba and then start winbind.
> 3. Maybe we can also add that since kerberos comes into picture with AD and Samba, make sure that time skew is not too great and within permissible limits. Else join step may complain of 'time skew too great'. Right ?
I've completely forgot to specify this in the guide: thank you!
Of course it's right, kerberos is time-dependent, it needs to be synchronized with domain ntp. I've just added this to the post.
> the 'winbind' is not added to against 'shadow' entry in /etc/nsswitch.conf file

Don't know why ?? 
I'm not sure to have understood..if I have understood it I can't answer to; but if you take a look to the original nsswitch.conf file you can see that "shadow" entry exists against "winbind" entry.
I hope it is what you are looking for... greetings

---

### Post by SerbisS on 2010-10-06
I updated the script adding variables and commands in order to running regulary the update of ntp server and the change of the new home folders' permissions and group. Here is the modified "AD_join.sh" file.
It creates the "/etc/SECUREHOME" folder and the "/etc/SECUREHOME/file" file, it builds crontab with "file" information with which:
[LIST]
[*]sync linux ntp server with domain ntp sever once a day at 12:30 o'clock
[*]changes the group of "homes" folders with domain admins group every 60 minutes
[*]changes the "homes" permissions in "700" every 60 minutes
[/LIST]

---

### Post by SerbisS on 2010-10-06
I tested the procedure on several computers of the company where I work and everything gone well:guitar:
Once you know the procedure and the requirements and once you have edited the script one time, it's only necessary to change the first value (sudoer user) and the entire procedure is done in 10 minutes max (in the same domain of course).
I hope for you is the same. Please let me now if it is.
Regards):P

---

### Post by luvshines on 2010-10-07
1. For my 1st query regarding 'password server' parameter, I found in smb.conf that 'password server' defaults to * which shall solve our purpose here. **Although when I use it, I always set it to the list of servers I have**

2. For the last query regarding winbind against shadow entry, I actually meant this [taken from [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html ](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html )]
```

passwd:     files winbind
**[COLOR="Blue"]shadow:     files[/COLOR]**
group:      files winbind
```

winbind is not mentioned against shadow in nsswitch.conf, though I don't know what effect it may have.
Maybe because the only thing we may expect from AD server is username and groups information and ofcourse authentication which will any how not involve 'shadow'

---

### Post by SerbisS on 2010-10-08
There are a lot of programs and method to perform a Linux machine NT authentication. Every program depend to another one and so on. I tried a lot of configuration first to find a well running one. In &#8220;samba-common&#8221; packet you will find winbind packet which is made by an utility and a daemon: wbinfo and winbindd. Wbinfo is necessary in order to hook PAM authentication and using them for authenticate NT users locally, winbindd daemon take info about NT users and groups for nsswitch program. Nss program (editable in nsswitch.conf file) take information (like users, group and passwords) from a lot of different sources. Shadow is an encryption password database; with the &#8220;shadow winbind&#8221; line we indicate to shadow program to take information from winbind (as for passwd and group line). Knowing this for me it was logic to edit nsswitch line in that way. Of course it is possible that is not necessary or wrong (as I said I'm not an expert). I read a lot of guide and I made a lot of test before publish this script/method and also what you say about &#8220;password server&#8221; parameter is logic, but I have see that the authentication is already made using winbind that use nsswich program and PAM authentication method. Knowing this, for me it was also logic to not put the &#8220;password server&#8221; parameter in smb.conf and as I could see it run perfectly. Do you think that my argument and what I said is wrong 8-[? Have you try to modify in a different way the configuration files? For you it works with this different way? Please, can you paste or attach here you working configuration?
Thank you for your interest:biggrin:

---

### Post by guimenez on 2010-10-12
Please, can you change this script to work in Ubuntu 10.10

Please, i need this a lot

many thanks

---

### Post by luvshines on 2010-10-12
> **SerbisS said:**
> There are a lot of programs and method to perform a Linux machine NT authentication. Every program depend to another one and so on. I tried a lot of configuration first to find a well running one.
I read a lot of guide and I made a lot of test before publish this script/method and also what you say about “password server” parameter is logic, but I have see that the authentication is already made using winbind that use nsswich program and PAM authentication method. 
Have you try to modify in a different way the configuration files? For you it works with this different way? Please, can you paste or attach here you working configuration?
Thank you for your interest:biggrin:

Hi, though I haven't tried running the script on my Ubuntu machine but I noticed that the template folder contains 'system-auth' file for PAM configurations.

AFAIK, Ubuntu has that file divided in 4 components. Will a single 'system-auth' file work as it worked on RHEL/Fedora ?

---

### Post by SerbisS on 2010-10-13
> Please, can you change this script to work in Ubuntu 10.10
Have you try to test the procedure on Ubuntu 10.10 yet? It doesn't work?
I'll try to do it, but I don't have too much time, so I couldn't promise anything. If you can try to test the procedure with a virtual machine first, then post the problems.

---

### Post by guimenez on 2010-10-13
i've try in Ubuntu 10.10 and script gives a lots of errors.

Ubuntu 10.10 doesn't have samba package, krb5-config and some other things :(

because of that, i can't make it work in Ubuntu 10.10

thanks

---

### Post by SerbisS on 2010-10-13
> I noticed that the template folder contains 'system-auth' file for PAM configurations. Ubuntu has that file divided in 4 components.
Yes I know...it's not really an &#8220;orthodox&#8221; system but in this way it is more simple to manage...PAM authentications are very tricky parameters and if you make something wrong it is possible that you could not still login in your machine.. For this reason I tested the configuration on myself first and then I publish the post. I also advised that for testing it's better to use a virtual machine. Anyway as you can see the entire &#8220;pam.d&#8221; directory is copied so if something bad happened you can always use a Live CD to remove the new one and replace it with the original. Fortunately I never had problems with it.

---

### Post by SerbisS on 2010-10-13
> i've try in Ubuntu 10.10 and script gives a lots of errors.

Ubuntu 10.10 doesn't have samba package, krb5-config and some other things
I tried the configuration using Ubuntu 10.10 and Windows Server 2003 r2 Std, and **_everything_** works well!!! Everything and without any problem; the join to the domain works, shared folders works, users and groups works, DNS works,  also users local authentications works! All the packets (samba samba-common smbclient winbind krb5-config krb5-user) are present and working...of course you haven't try the procedure or you haven't read instructions...maybe your network doesn't work. Ensure your network connection work properly and try again!

---

### Post by guimenez on 2010-10-13
> **SerbisS said:**
> I tried the configuration using Ubuntu 10.10 and Windows Server 2003 r2 Std, and **_everything_** works well!!! Everything and without any problem; the join to the domain works, shared folders works, users and groups works, DNS works,  also users local authentications works! All the packets (samba samba-common smbclient winbind krb5-config krb5-user) are present and working...of course you haven't try the procedure or you haven't read instructions...maybe your network doesn't work. Ensure your network connection work properly and try again!

Thanks for loosing your time testing and help me. I've try 2 times and gives me lots of errors installing. I've change all the things i can change in the script. 

I will do it again one more time and show you a log with all errors that appears. 

Many thanks once again

---

### Post by SerbisS on 2010-10-14
Mmmmm...once you have run the script the first time and something gone wrong, it is not a good thing to re-run it without remove the modification that it made. So remove all the packets manually:

```
sudo apt-get remove samba samba-common smbclient winbind krb5-config krb5-user

```
Remove all the folders and the files that it created:

```
sudo rm /etc/krb5.conf  /etc/nsswitch.conf  /etc/samba/smb.conf
sudo rm -R /etc/pam.d
sudo rm -R /home/DOMAINDIR(change this with the correct name)
```

Restore all the folders and the files backups

```
sudo mv /etc/krb5.conf.bkp /etc/krb5.conf
sudo mv /etc/nsswitch.conf.bkp /etc/nsswitch.conf
sudo mv /etc/samba/smb.conf.bkp /etc/samba/smb.conf
cp -R /etc/pam.d.bkp /etc/pam.d
```

Remove crontab rules if you used it (this is not indispensable)

```
sudo crontab -e (then remove the lines with canc, or dd if you use vi instead nano; save and exit)
```

Please be careful using #rm and #rm -R command, once you have remove files with rm you can't restore it.

Then move in your domain and ensure your machine name is not added to “computer” section in Active Directory Users and Computers. If there is remove it.

I think it's all. Reboot your machine and try again. I hope it will work well.

As I said it's better to practice with a virtual machine first. I'd like to see your errors anyway. Let me know....

---

### Post by luvshines on 2010-10-14
> **SerbisS said:**
> 
Remove all the folders and the files that it created:

```
sudo rm /etc/krb5.conf  [COLOR="red"]/etc/nsswitch.conf[/COLOR]  /etc/samba/smb.conf
[COLOR="Red"]sudo rm -R /etc/pam.d[/COLOR]
sudo rm -R /home/DOMAINDIR(change this with the correct name)
```

Restore all the folders and the files backups

Please be careful using #rm and #rm -R command, once you have remove files with rm you can't restore it.


I don't think removing(rm and rm -R) /etc/nsswitch.conf and /etc/pam.d is a good idea. It may leave you with an unusable system

Will sudo command work once /etc/pam.d/sudo is gone along with other PAM configurations in /etc/pam.d directory ??

I did it once, removed system-auth from pam.d thinking that I will replace it with backep up file, but couldn't login to the system

---

### Post by SerbisS on 2010-10-14
Mabe you can replace it directly with #mv and #cp -R command

```
sudo mv /etc/krb5.conf.bkp /etc/krb5.conf
sudo mv /etc/nsswitch.conf.bkp /etc/nsswitch.conf
sudo mv /etc/samba/smb.conf.bkp /etc/samba/smb.conf
sudo cp -R /etc/pam.d.bkp /etc/pam.d
```

I'll try it

---

### Post by SerbisS on 2010-10-14
Open a terminal and log in with a superuser and leave it there it's a way to ensure you can always re-modify your changes I think...

---

### Post by guimenez on 2010-10-14
First of all i just want to say that you are a genius   **SerbisS**  :D:

i've tested in Ubuntu 10.04 and everything works perfect :D:D:
even the problem i have it, that when mount shares with pam-mount the ubuntu doesn't logoff and hang. That problem is not happening any more :D:D:

i'm now installing again the new Ubuntu 10.10 and try everything again.

I will tell you any problem

thanks once again genius :D

---

### Post by guimenez on 2010-10-14
Thank you  **SerbisS** :D:D:D:D

you are my hero!!!!

i've installed Ubuntu 10.10 again and run the script and everything works like a charm :D

the main problem was that i needed to make sudo apt-get update for the first time and then run the script

please, now how can i deploy Ubuntu to another machine?, Microsoft have Sysprep

many thanks once again and keep your excellent work 

Guimenez

---

### Post by SerbisS on 2010-10-14
Of course I'm not a genius, anyway thank you;)
> how can i deploy Ubuntu to another machine?
I can't completely understand your question. You want to make an iso of your configured system to install it on other machines?

If so, I can't help you but I think you can find some documentation about this on web (let me know if you find something interesting)

...anyway I don't think it's a good idea to replicate a machine already joined in a domain to install it in another one.
I think it's better to replicate a clean one and then run the script.

As I wrote in other post, if you still work in the same domain, once you have edited the script, it is just necessary to change first value (sudoer user) and that's it: in 5 minutes you have a joined and working machine.

---

### Post by guimenez on 2010-10-14
> **SerbisS said:**
> 
I can't completely understand your question. You want to make an iso of your configured system to install it on other machines?


No. i will install Ubuntu 10.10 in a new computer and install everything i need to all computers without joining them to a domain. Then i will make a backup with savepart(great backup tool) and restore it to all my computers. After that i will run your perfect script to join them to my domain.

I just don't know if i can just backup and restore the image, or i need to run any tool to prepare Ubuntu to deploy to other computers like microsoft windows (need to run sysprep)

thanks

---

### Post by ductsoup on 2010-10-14
First off, thanks for putting this together. Though I've done a couple dozen Samba/AD configurations in the past, I've been wrestling with VM/10.04/Win2k3R2 the last couple days. Seems like you're a couple days ahead of me so the insight is really helpful.

Three quick question/observations

-

```
net ads join -U Administrator
```Does succeed but gives that pesky DNS update failure notice. Is anyone else seeing this, know why this happens or better yet, know how to resolve it? It's easy enough to force it with a manual DNS entry but I'm thinking that shouldn't be necessary. Likewise-open doesn't seem to have a problem with this bit so I feel like I'm missing something.

-

Dumping everything into system-auth doesn't seem to work for me and I don't know a lot about PAM. Are you replacing common-* with these entries or appending?

-

If a domain user logs in via SSH the home directory and permissions are created on-the-fly just fine. If that same AD user hits the Samba share from a Windows client first, the home directory isn't created and things get ugly.

Any thoughts on that? And, what's the proper way to handle a previous user with home directory that's since been deleted from Active Directory?

Stay well, Craig

---

### Post by SerbisS on 2010-10-15
> i need to run any tool to prepare Ubuntu to deploy to other computers like microsoft windows (need to run sysprep)

I never used something like this on Ubuntu in order to deploy it to other computers. I think there shouldn't be a need for a tool like sysprep on linux - since there's no SID and no registering.

---

### Post by SerbisS on 2010-10-15
> DNS update failure notice

I know about this error. I saw it a lot of time but I couldn't remove it. I think it appear because Linux can't add a DNS entry in DNS Domain Controller Service. Anyway if you run from a domain's windows machine \\name-of-linux-machine the name is resolved. Let me know if you can remove that error. (I already spent a lot of time to make this procedure and as it works I can't spent time anymore, at least not for the moment)

> Dumping everything into system-auth doesn't seem to work for me and I don't know a lot about PAM. Are you replacing common-* with these entries or appending?


PAM are used for authentication in general. In this case are used in order to authenticate NT users locally(I have just append it).

> If that same AD user hits the Samba share from a Windows client first, the home directory isn't created
And, what's the proper way to handle a previous user with home directory that's since been deleted from Active Directory?

An home directory is created just when you log in your linux machine with a domain user. If the user still not exist in domain it couldn't be authenticate. So I think it's better to remove his directory with a sudoer user.

---

### Post by guimenez on 2010-10-25
i'm having a new issue :(

when i try to login with a user that has few days to expire is password, it hang displaying the message "your password will expire in ... days". and stop there :(

if a press Esc key, I'm back to users choose menu.

Please, can i change any configuration file to authorize this kind of login users?

many thanks

---

### Post by guimenez on 2010-10-26
Please can anyone help to fix this issue. Any place to start?

Thanks

---

### Post by SerbisS on 2010-10-27
So you need to manage your AD user with your Linux machine...I don't know if there is other way to do it but you can make the AD user a local user...
use command:
```
#getent passwd
```
copy the line of the users you want to make local users and paste it in /etc/passwd file.

Now you can see that user in Administration --> User and Group and also pressing the button in the up right corner...

Use sudoer user or log in with that user and change the password with:
```
#sudo user_name passwd
```

or from the logged user with
```
#passwd
```

I hope it is what you are looking for.

---

### Post by guimenez on 2010-10-27
Thanks again for help me. 

My main problem its when a user have just few days before the password expires, that user can't login. I can't copy all users(500 hundreds) to all my machines(150 hundreds). 

I think its something with the conf files

Hope you understand my problem now

Thanks

---

### Post by SerbisS on 2010-10-29
The problem is in pam authentication and NT authentication token I think. For the moment I've not other ideas...

Change configuration files it's not something simple.
If you read some previous post you can see that in order to authenticate in AD, a lot of programs and configuration work together; often change one of this means changing all of them.

I haven't much time to spend in this now, I'm sorry.

I hope you can find a solution or that other members will help us to improve the system.

Greetings

---

### Post by guimenez on 2010-10-29
thank you one more time

i will try to find the solution and then post here

cumps

guimenez

---

### Post by luvshines on 2010-10-30
> **guimenez said:**
> thank you one more time

i will try to find the solution and then post here

cumps

guimenez

Are you sure that login hangs indefinitely after the password expiration notification.
That should not happen :(
Maybe, if you don't need password expiry, you can remove it altogether

---

### Post by guimenez on 2010-10-30
When i press login, the dgm display the message "your password will expire in ... days" and then stop there. But if i press ESC key, it back to normal login.
But it never login to that user.

I don't need to change the user password in Ubuntu, but i need that user to login

i don't know what i can change in the auth or session files to autorize this kind of users :(

thanks for the reply

guimenez

---

### Post by luvshines on 2010-10-31
> **guimenez said:**
> When i press login, the dgm display the message "your password will expire in ... days" and then stop there. But if i press ESC key, it back to normal login.
But it never login to that user.

I don't need to change the user password in Ubuntu, but i need that user to login

i don't know what i can change in the auth or session files to autorize this kind of users :(

thanks for the reply

guimenez

The message and password expiry are controlled by DC in this case. And AFAIK, the message is dispayed 14 days prior to password expiry date. Till the password expires user will be allowed login. After expiry, Admin has to reset the password for the user to login, if user has not changed it within permissible time.
You can change the DC settings so that password never expires.

PS: But I still can't understand why the user can't login

Can you try this from terminal:```


## Authenticate with password.Assuming + is the winbind separator
wbinfo -a <domain>+<username>%<password>

## Try to access any Samba share with this user which is configured to use DC for authentication
smbclient //<samba-server>/<share-name> -U<domain>+<username>%<password>

```

---

### Post by guimenez on 2010-11-02
> **luvshines said:**
> The message and password expiry are controlled by DC in this case. And AFAIK, the message is dispayed 14 days prior to password expiry date. Till the password expires user will be allowed login. After expiry, Admin has to reset the password for the user to login, if user has not changed it within permissible time.
You can change the DC settings so that password never expires.

PS: But I still can't understand why the user can't login

Can you try this from terminal:```


## Authenticate with password.Assuming + is the winbind separator
wbinfo -a <domain>+<username>%<password>

## Try to access any Samba share with this user which is configured to use DC for authentication
smbclient //<samba-server>/<share-name> -U<domain>+<username>%<password>

```

now i can't login with any other user because the time sync :(
yesterday the time change here and now i can't sync with my server

i put sudo ntpdate domain.local
and it display: no server suitable for synchronozation found"

i've try sudo ntpdate my_server_ip and nothing :(

now i'm stuck

---

### Post by luvshines on 2010-11-02
> **guimenez said:**
> now i can't login with any other user because the time sync :(
yesterday the time change here and now i can't sync with my server

i put sudo ntpdate domain.local
and it display: no server suitable for synchronozation found"

i've try sudo ntpdate my_server_ip and nothing :(

now i'm stuck

Should not command be something like```

sudo ntpdate <time-server-ip>

```

Check what you have in ```
crontab -l
```since AD_join.sh puts time synching as a cron job

---

### Post by guimenez on 2010-11-03
> **luvshines said:**
> Should not command be something like```

sudo ntpdate <time-server-ip>

```

Check what you have in ```
crontab -l
```since AD_join.sh puts time synching as a cron job

when i execute the command crontab -l it says: no crontab for administrator(my admin user) 

thanks

---

### Post by SerbisS on 2010-11-03
Try both
```
crontab -l
```
and
```
sudo crontab -l
```

---

### Post by Piconit on 2010-11-03
Hi SerbisS,
I've integrated an ubuntu 10.04 LTS in an active directory and all was right.
wbinfo -u, wbinfo -g and getent passwd and getent group answer well. I've shared four folders on ubuntu to all windows active directory users. When I login on a windows xp or 7 machine like domain user or administrator, ubuntu machine is visible on microsoft network and I can see the shared folders too. But, when I click on one of this folder comes a message saying that I haven't permissions to access to this folder.
The folders have read and write permissions for all windows domain users (they belong to winusers group, and I've given read and write permissions to winusers group).
What's wrong? Is it necessary to modifiy pam.d configuration files (how)?
(I'm almost finish to complete the sharing)
Thanks.

---

### Post by SerbisS on 2010-11-03
Sharing permissions are set in /etc/samba/smb.conf file. There you have to specify “valid users” and “admin users”. The syntax is as follow:

```
valid users =YourShortDomainName+domain_user  YourShortDomainName+other_domain_user

admin users =YourShortDomainName+domain_user YourShortDomainName+other_domain_user
```

If you need to add a group:

```
… =@”YourShortDomainName+Domain Group”
```

Note there is no space between “=” and “YourShortDomainName”

Note also that after a modification of smb.conf file it's necessary to restart the service:

```
sudo services smbd restart
```

All right?!

---

### Post by Piconit on 2010-11-03
Yes, I do it! This is the piece of my smb.conf
[SharedFolder-A]
writable = yes
path = /media/sharedfolders/SharedFolder-A
write list=@winusers 
force directory mode = 0775
force security mode = 0000
force group=winusers
guest ok = yes
force create mode = 0764
create mask = 0764
comment = Folder A to share with winusers group
directory mask = 0764
force directory security mode = 0000
valid users=@winusers
browsable = yes
 
With this code I haven't access to SharedFolder-A from windows machine (or lan machine integrated to windows domain). Is it necessary to write 
admin users=MyShortDomainName+domain_user ?
I think perhaps it could be some linux system permissions or kernel-level access don't allow to apply samba permissions, but I don't know which they are or how to modify it. Or surely I've done something wrong.

---

### Post by s1nch4n on 2010-11-04
> **Piconit said:**
> Yes, I do it! This is the piece of my smb.conf
[SharedFolder-A]
writable = yes
path = /media/sharedfolders/SharedFolder-A
write list=@winusers 
force directory mode = 0775
force security mode = 0000
force group=winusers
guest ok = yes
force create mode = 0764
create mask = 0764
comment = Folder A to share with winusers group
directory mask = 0764
force directory security mode = 0000
valid users=@winusers
browsable = yes
 
With this code I haven't access to SharedFolder-A from windows machine (or lan machine integrated to windows domain). Is it necessary to write 
admin users=MyShortDomainName+domain_user ?
I think perhaps it could be some linux system permissions or kernel-level access don't allow to apply samba permissions, but I don't know which they are or how to modify it. Or surely I've done something wrong.what u need is to set up directory permission with the right Group/User...

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by guimenez on 2010-11-04
> **SerbisS said:**
> Try both
```
crontab -l
```
and
```
sudo crontab -l
```

i have the same error:

no crontab for root

if AD_join.sh adds a function in crontab, why is not in my crontab list?

have i done anything wrong?

thanks

---

### Post by SerbisS on 2010-11-04
If my shred folder is my home (toast) and if my domain is test.something.com an example of a correct syntax is as follow:

```
path = /home/toast/
available = yes
read only = no
browsable = yes
public = yes
writable = yes
valid users =TEST+user @TEST+Group 
admin users =@”TEST+Admin Group”
```

---

### Post by SerbisS on 2010-11-04
> if AD_join.sh adds a function in crontab, why is not in my crontab list?

The original script don't add any crontab roule.
If  ```
#ntpdate
``` command don't make the expected results try with

```
#ntpdate -d  (debugging mode).
```

If it show the expected result signify that it's something that block incoming traffic to privilege ports (like a firewall).

In this case you can run the command anyway using an unprivileged port with

```
#ntpdate -u
```

---

### Post by Piconit on 2010-11-04
Thank you very much, SerbisS and s1nch4n. I've read FilePermissions documentation and I've changed manually all shared files and folders permissions. Now It works fine.

---

### Post by guimenez on 2010-11-05
> **SerbisS said:**
> The original script don't add any crontab roule.
If  ```
#ntpdate
``` command don't make the expected results try with

```
#ntpdate -d  (debugging mode).
```

If it show the expected result signify that it's something that block incoming traffic to privilege ports (like a firewall).

In this case you can run the command anyway using an unprivileged port with

```
#ntpdate -u
```

ntupdate -u domain.local still the same error (can't find server)l

> **luvshines said:**
> The message and password expiry are controlled by DC in this case. And AFAIK, the message is dispayed 14 days prior to password expiry date. Till the password expires user will be allowed login. After expiry, Admin has to reset the password for the user to login, if user has not changed it within permissible time.
You can change the DC settings so that password never expires.

PS: But I still can't understand why the user can't login

Can you try this from terminal:```


## Authenticate with password.Assuming + is the winbind separator
wbinfo -a <domain>+<username>%<password>

## Try to access any Samba share with this user which is configured to use DC for authentication
smbclient //<samba-server>/<share-name> -U<domain>+<username>%<password>

```

i've attached the 2 logs(ntpdate -d and the wbinfo -a commands)

if i use the smbclient command it works well and i can see the share

and now? :(

many thanks

---

### Post by SerbisS on 2010-11-05
> ntupdate -u domain.local still the same error

Post here the output of ```
ntpdate -d
``` command

---

### Post by guimenez on 2010-11-05
> **SerbisS said:**
> Post here the output of ```
ntpdate -d
``` command

5 Nov 10:10:36 ntpdate[3313]: ntpdate 4.2.4p8@1.1612-o Fri Aug 22:49:55 UTC 2010 (1)
5 Nov 10:10:36 ntpdate[3313]: no servers can be used, exiting

---

### Post by SerbisS on 2010-11-05
> 5 Nov 10:10:36 ntpdate[3313]: ntpdate 4.2.4p8@1.1612-o Fri Aug 22:49:55 UTC 2010 (1)
5 Nov 10:10:36 ntpdate[3313]: no servers can be used, exiting

Of course you must put a server name or IP!!!

```
ntpdate -d (server)
```

---

### Post by guimenez on 2010-11-05
> **SerbisS said:**
> Of course you must put a server name or IP!!!

```
ntpdate -d (server)
```

sorry :)

i've attached the log

---

### Post by SerbisS on 2010-11-05
> i've attached the log

Now try with ```
ntpdate-debian -d
```and post the output
(don't worry because with "-d" option the command doesn't adjust the local clock but just print usefull iformation for general debugging)

---

### Post by ihs on 2010-11-05
'Failed to join domain: failed to set machine spn: Constraint Violation'
 
'Validate Write for DNS and SPN were not set.'
 
Appears to be a Domain Controller setting that should be set on the Windows server.
 
Unfortunately I had to give up on this, so good luck to others and I hope the above helps you solve the problem.

---

### Post by guimenez on 2010-11-05
> **SerbisS said:**
> Now try with ```
ntpdate-debian -d
```and post the output
(don't worry because with "-d" option the command doesn't adjust the local clock but just print usefull iformation for general debugging)

here it is

---

### Post by SerbisS on 2010-11-05
It's possible that an internal firewall block incoming ntp-server packets? Try disable it
Error happened with other machine?

---

### Post by guimenez on 2010-11-05
All my machines (25) display the same message :(

i don't know what can i do more

---

### Post by SerbisS on 2010-11-05
> Failed to join domain: failed to set machine spn: Constraint Violation

Unable to solve your problem in this way...need more information, or maybe somebody already encountered it and know how to resolve it...

---

### Post by SerbisS on 2010-11-05
> i don't know what can i do more
If it's not an internal firewall (like firestarter) I really don't know what it could be.. a solution or something to understand why the error happened is setting up an internal ntp-server in ubuntu..no other ideas sorry

---

### Post by guimenez on 2010-11-05
many thanks once again. i will try to find a solution

please, and what about other problem. All users that have they password almost expired can't login. it display the message "your password will expire in ... days" and stop login

---

### Post by luvshines on 2010-11-05
> **guimenez said:**
> All my machines (25) display the same message :(

i don't know what can i do more

For the ntp error, you might want to check if the Windows Time server is running or not.
```

## On Win 2003 server command console
net start w32time
```

And for the login error, since smbclient is able to login so should login through GUI. Just try disabling the expiry(temporarily) or maybe reduce the number of days from 14 to some smaller value and try again

---

### Post by luvshines on 2010-11-05
> **ihs said:**
> Hello, I have been following the guide however I always get stuck on using net ads join.
 
The error message I'm getting is:
 
'Failed to join domain: failed to set machine spn: Constraint Violation'
 
I've tried to find info on this from google and all that came up was someone saying that they fixed the problem because:
 
'Validate Write for DNS and SPN were not set.'
 
Is this a setting for the krb5.conf file to enable validation?
 
This is the first time I've really attempted using samba, let alone trying to join an AD domain, so I may be missing something very obvious :)
 
Thankyou.

Are you using Active directory Admin credentials to join ?

---

### Post by ihs on 2010-11-08
Please disregard this post

---

### Post by Keamas on 2010-11-09
Hi I get always this Message on Ubuntu 10.10 and AD 2008 R2.

```
# sudo net ads join -U Administrator
Enter Administrator's password:
Using short domain name -- PLANET-EXPRESS
Joined 'SCRUFFY' to realm 'planet-express.local'
No DNS domain configured for scruffy. Unable to perform DNS Update.
DNS update failed!

```

```
# sudo net ads join -S zoidberg -U Administrator
Enter Administrator's password:
Using short domain name -- PLANET-EXPRESS
Joined 'SCRUFFY' to realm 'planet-express.local'
No DNS domain configured for scruffy. Unable to perform DNS Update.
DNS update failed!
root@scruffy:/home/ladmin/Deskto
```

I tried it with no record in the DNS after this message I added manually a DNS record, but always the same.

---

### Post by luvshines on 2010-11-09
> **Keamas said:**
> Hi I get always this Message on Ubuntu 10.10 and AD 2008 R2.

```
# sudo net ads join -U Administrator
Enter Administrator's password:
Using short domain name -- PLANET-EXPRESS
Joined 'SCRUFFY' to realm 'planet-express.local'
No DNS domain configured for scruffy. Unable to perform DNS Update.
DNS update failed!

``````
# sudo net ads join -S zoidberg -U Administrator
Enter Administrator's password:
Using short domain name -- PLANET-EXPRESS
Joined 'SCRUFFY' to realm 'planet-express.local'
No DNS domain configured for scruffy. Unable to perform DNS Update.
DNS update failed!
root@scruffy:/home/ladmin/Deskto
```I tried it with no record in the DNS after this message I added manually a DNS record, but always the same.

Is that breaking something ?

After that error, did you try ```
net ads testjoin
```

---

### Post by Keamas on 2010-11-09
> **luvshines said:**
> Is that breaking something ?

After that error, did you try ```
net ads testjoin
```



```
root@scruffy:~# net ads testjoin
Join is OK
```

All other steps of "Testing and Joining" worked.

But I can not login with a domain user:

```
# ssh Administrator@scruffy.planet-express.local
Warning: Permanently added the RSA host key for IP address '192.168.0.20' to the list of known hosts.
Administrator@scruffy.planet-express.local's password: 
Permission denied, please try again.
Administrator@scruffy.planet-express.local's password: 
Connection closed by UNKNOWN

```

Is this because of the DNS error or is it something else ?
Can anyone help here ?


```
# sudo net ads join -U Administrator
Enter Administrator's password:
Using short domain name -- PLANET-EXPRESS
Joined 'SCRUFFY' to realm 'planet-express.local'
No DNS domain configured for scruffy. Unable to perform DNS Update.
DNS update failed!

```

---

### Post by luvshines on 2010-11-09
> **Keamas said:**
> ```
root@scruffy:~# net ads testjoin
Join is OK
```

All other steps of "Testing and Joining" worked.

But I can not login with a domain user:

```
# ssh Administrator@scruffy.planet-express.local
Warning: Permanently added the RSA host key for IP address '192.168.0.20' to the list of known hosts.
Administrator@scruffy.planet-express.local's password: 
Permission denied, please try again.
Administrator@scruffy.planet-express.local's password: 
Connection closed by UNKNOWN

```

Is this because of the DNS error or is it something else ?
Can anyone help here ?


Try this command for password verification```

# Assuming + as winbind separator
wbinfo -a <domain>+<username>%<password>

```

And for login```

ssh <domain>+<username>@<server-ip>
```

I think in your case, username is Administrator, domain is planet-express, passsword and server-ip are known to you

---

### Post by Keamas on 2010-11-09
> **luvshines said:**
> Try this command for password verification```

# Assuming + as winbind separator
wbinfo -a <domain>+<username>%<password>

```

And for login```

ssh <domain>+<username>@<server-ip>
```

I think in your case, username is Administrator, domain is planet-express, passsword and server-ip are known to you

```
# wbinfo -a planet-express+Administrator%Password
plaintext password authentication succeeded
challenge/response password authentication succeeded
root@scruffy:~# 
```

The wbinfo seems to work but the login not.
I tried planet-express, planet-express.local and so on...
But always Permission denied. Do I need to configure something else to allow the Domain users to login ?


```

$ ssh planet-express.local+Administrator@192.168.0.20
planet-express.local+Administr@192.168.0.20's password: 
Permission denied, please try again.
planet-express.local+Administr@192.168.0.20's password: 
Permission denied, please try again.
planet-express.local+Administr@192.168.0.20's password: 
Permission denied (publickey,password).
.
```

---

### Post by luvshines on 2010-11-09
> **Keamas said:**
> ```
# wbinfo -a planet-express+Administrator%Password
plaintext password authentication succeeded
challenge/response password authentication succeeded
root@scruffy:~# 
```

The wbinfo seems to work but the login not.
I tried planet-express, planet-express.local and so on...
But always Permission denied. Do I need to configure something else to allow the Domain users to login ?


```

$ ssh planet-express.local+Administrator@192.168.0.20
planet-express.local+Administr@192.168.0.20's password: 
Permission denied, please try again.
planet-express.local+Administr@192.168.0.20's password: 
Permission denied, please try again.
planet-express.local+Administr@192.168.0.20's password: 
Permission denied (publickey,password).
.
```

Is that the exact error you are getting while login or is it a typo that 'ator' from Administrator has been chopped off

You may get something useful in auth.logs of the server you are trying to ssh

---

### Post by Keamas on 2010-11-09
> **luvshines said:**
> Is that the exact error you are getting while login or is it a typo that 'ator' from Administrator has been chopped off

You may get something useful in auth.logs of the server you are trying to ssh

**Administr**
It seems ssh is cutting the last letters because it is too long.
With other Usernames it is the same. But I think thats not the problem because if I do it without local SSH writes the full username:

```
root@scruffy:~# ssh planet-express+Administrator@localhost
planet-express+Administrator@localhost's password: 
Permission denied, please try again.
planet-express+Administrator@localhost's password: 
Permission denied, please try again.
planet-express+Administrator@localhost's password: 
Permission denied (publickey,password).
root@scruffy:~# 

```

See without local the full username appears

```
root@scruffy:~# ssh planet-express+Administrator@localhost
planet-express+Administrator@localhost's password: 
Permission denied, please try again.
planet-express+Administrator@localhost's password: 
Permission denied, please try again.
planet-express+Administrator@localhost's password: 
Permission denied (publickey,password).

```


```
root@scruffy:~# cat /var/log/auth.log
...
Nov  9 14:13:49 scruffy sshd[2050]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=localhost.localdomain  user=planet-express+Administrator
Nov  9 14:13:51 scruffy sshd[2050]: Failed password for planet-express+Administrator from 127.0.0.1 port 37457 ssh2
Nov  9 14:14:02 scruffy sshd[2050]: last message repeated 2 times
Nov  9 14:14:02 scruffy sshd[2050]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=localhost.localdomain  user=planet-express+Administrator

Nov  9 14:16:09 scruffy sshd[2054]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=scruffy  user=planet-express+Administrator
Nov  9 14:16:10 scruffy sshd[2054]: Failed password for planet-express+Administrator from 192.168.0.20 port 51083 ssh2
Nov  9 14:16:23 scruffy sshd[2054]: last message repeated 2 times
Nov  9 14:16:23 scruffy sshd[2054]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=scruffy  user=planet-express+Administrator
Nov  9 14:16:46 scruffy sshd[2058]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=scruffy  user=planet-express+Administrator
Nov  9 14:16:49 scruffy sshd[2058]: Failed password for planet-express+Administrator from 192.168.0.20 port 51084 ssh2
Nov  9 14:16:55 scruffy sshd[2058]: Failed password for planet-express+Administrator from 192.168.0.20 port 51084 ssh2
Nov  9 14:17:01 scruffy CRON[2060]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  9 14:17:01 scruffy CRON[2060]: pam_unix(cron:session): session closed for user root
Nov  9 14:17:03 scruffy sshd[2058]: Failed password for planet-express+Administrator from 192.168.0.20 port 51084 ssh2
Nov  9 14:17:03 scruffy sshd[2058]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=scruffy  user=planet-express+Administrator

...

```

---

### Post by luvshines on 2010-11-09
> **Keamas said:**
> **Administr**
It seems ssh is cutting the last letters because it is too long.
With other Usernames it is the same. But I think thats not the problem because if I do it without local SSH writes the full username:

See without local the full username appears

```
root@scruffy:~# ssh planet-express+Administrator@localhost
planet-express+Administrator@localhost's password: 
Permission denied, please try again.
planet-express+Administrator@localhost's password: 
Permission denied, please try again.
planet-express+Administrator@localhost's password: 
Permission denied (publickey,password).

```


```
root@scruffy:~# cat /var/log/auth.log
...
Nov  9 14:13:49 scruffy sshd[2050]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=localhost.localdomain  user=planet-express+Administrator
Nov  9 14:13:51 scruffy sshd[2050]: Failed password for planet-express+Administrator from 127.0.0.1 port 37457 ssh2
Nov  9 14:14:02 scruffy sshd[2050]: last message repeated 2 times
Nov  9 14:14:02 scruffy sshd[2050]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=localhost.localdomain  user=planet-express+Administrator

Nov  9 14:16:09 scruffy sshd[2054]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=scruffy  user=planet-express+Administrator
Nov  9 14:16:10 scruffy sshd[2054]: Failed password for planet-express+Administrator from 192.168.0.20 port 51083 ssh2
Nov  9 14:16:23 scruffy sshd[2054]: last message repeated 2 times
Nov  9 14:16:23 scruffy sshd[2054]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=scruffy  user=planet-express+Administrator
Nov  9 14:16:46 scruffy sshd[2058]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=scruffy  user=planet-express+Administrator
Nov  9 14:16:49 scruffy sshd[2058]: Failed password for planet-express+Administrator from 192.168.0.20 port 51084 ssh2
Nov  9 14:16:55 scruffy sshd[2058]: Failed password for planet-express+Administrator from 192.168.0.20 port 51084 ssh2
Nov  9 14:17:01 scruffy CRON[2060]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  9 14:17:01 scruffy CRON[2060]: pam_unix(cron:session): session closed for user root
Nov  9 14:17:03 scruffy sshd[2058]: Failed password for planet-express+Administrator from 192.168.0.20 port 51084 ssh2
Nov  9 14:17:03 scruffy sshd[2058]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=scruffy  user=planet-express+Administrator

...

```

Can you post the output of this```

cat /etc/pam.d/common-auth
cat /etc/pam.d/sshd

```

---

### Post by Keamas on 2010-11-09
> **luvshines said:**
> Can you post the output of this```

cat /etc/pam.d/common-auth
cat /etc/pam.d/sshd

```

```
root@scruffy:~# cat /etc/pam.d/common-auth
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth	[success=2 default=ignore]	pam_unix.so nullok_secure
auth	[success=1 default=ignore]	pam_lsass.so try_first_pass
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
```

```

root@scruffy:~# cat /etc/pam.d/sshd
# PAM configuration for the Secure Shell service

# Read environment variables from /etc/environment and
# /etc/security/pam_env.conf.
auth       required     pam_env.so # [1]
# In Debian 4.0 (etch), locale-related environment variables were moved to
# /etc/default/locale, so read that as well.
auth       required     pam_env.so envfile=/etc/default/locale

# Standard Un*x authentication.
@include common-auth

# Disallow non-root logins when /etc/nologin exists.
account    required     pam_nologin.so

# Uncomment and edit /etc/security/access.conf if you need to set complex
# access limits that are hard to express in sshd_config.
# account  required     pam_access.so

# Standard Un*x authorization.
@include common-account

# Standard Un*x session setup and teardown.
@include common-session

# Print the message of the day upon successful login.
session    optional     pam_motd.so # [1]

# Print the status of the user's mailbox upon successful login.
session    optional     pam_mail.so standard noenv # [1]

# Set up user limits from /etc/security/limits.conf.
session    required     pam_limits.so

# Set up SELinux capabilities (need modified pam)
# session  required     pam_selinux.so multiple

# Standard Un*x password updating.
@include common-password
```

---

### Post by luvshines on 2010-11-09
Looks like you are using likewise-open for domain join, right ?

Though I am totally stumped with likewise-open since I haven't worked with it :(, what does this say```

cat /etc/nsswitch.conf | egrep "^passwd|^group|^shadow"
```

---

### Post by Keamas on 2010-11-09
> **luvshines said:**
> Looks like you are using likewise-open for domain join, right ?

Though I am totally stumped with likewise-open since I haven't worked with it :(, what does this say```

cat /etc/nsswitch.conf | egrep "^passwd|^group|^shadow"
```

Oh yeahh I tried likewise some days ago but I removed it via apt-get remove... but it wasn't removed completely. I couldn't remove it manually completely so I reinstaled the mashine new and it worked perfect now after reinstall.

Thx so much for your help !!!

---

### Post by luvshines on 2010-11-09
> **Keamas said:**
> Oh yeahh I tried likewise some days ago but I removed it via apt-get remove... but it wasn't removed completely. I couldn't remove it manually completely so I reinstaled the mashine new and it worked perfect now after reinstall.

Thx so much for your help !!!

You re-OS'ed the machine completely ? :D

Maybe apt-get purge could have removed it completely.
The pam_lsass.so in common-auth was from likewise-open, and as you said that you had removed it, maybe that was causing the failure since it was still lurking around :)
Just for sanity check, can you check if pam_lsass.so is still in common-auth ?

---

### Post by Keamas on 2010-11-10
> **luvshines said:**
> You re-OS'ed the machine completely ? :D

Maybe apt-get purge could have removed it completely.
The pam_lsass.so in common-auth was from likewise-open, and as you said that you had removed it, maybe that was causing the failure since it was still lurking around :)
Just for sanity check, can you check if pam_lsass.so is still in common-auth ?

Here thats the working one

```

~#  cat /etc/pam.d/sshd
# PAM configuration for the Secure Shell service

# Read environment variables from /etc/environment and
# /etc/security/pam_env.conf.
auth       required     pam_env.so # [1]
# In Debian 4.0 (etch), locale-related environment variables were moved to
# /etc/default/locale, so read that as well.
auth       required     pam_env.so envfile=/etc/default/locale

# Standard Un*x authentication.
@include common-auth

# Disallow non-root logins when /etc/nologin exists.
account    required     pam_nologin.so

# Uncomment and edit /etc/security/access.conf if you need to set complex
# access limits that are hard to express in sshd_config.
# account  required     pam_access.so

# Standard Un*x authorization.
@include common-account

# Standard Un*x session setup and teardown.
@include common-session

# Print the message of the day upon successful login.
session    optional     pam_motd.so # [1]

# Print the status of the user's mailbox upon successful login.
session    optional     pam_mail.so standard noenv # [1]

# Set up user limits from /etc/security/limits.conf.
session    required     pam_limits.so

# Set up SELinux capabilities (need modified pam)
# session  required     pam_selinux.so multiple

# Standard Un*x password updating.
@include common-password

```

```
~# cat /etc/pam.d/common-auth
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth    [success=2 default=ignore]      pam_unix.so nullok_secure
auth    [success=1 default=ignore]      pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
# here's the fallback if no module succeeds
auth    requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

```

---

### Post by SerbisS on 2010-11-21
> please, and what about other problem. All users that have they password almost expired can't login. it display the message "your password will expire in ... days" and stop login
Have you find a solution? Otherwise I found this command which should change Windows domain password from Linux..
```
smbpasswd -t <domain-server> -U <user name>
```
I hope it works for you...let me know

---

### Post by guimenez on 2010-11-22
> **SerbisS said:**
> Have you find a solution? Otherwise I found this command which should change Windows domain password from Linux..
```
smbpasswd -t <domain-server> -U <user name>
```
I hope it works for you...let me know

the -t option doesn't exist in smbpasswd :(
it fail when i run the command and display the help option

thanks

---

### Post by SerbisS on 2010-11-22
> the -t option doesn't exist in smbpasswd
Ups! I'm really sorry! This is the right one:
```
smbpasswd -r <domain-server> -U <user name>
```
For me it works..

---

### Post by ramuja on 2011-04-21
Well done script! I really appreciate it. In my case the script installs and configure all required modules on the client. But when I want to join the client, I have got the following error 
DNS Update fails!
when I check on server's syslog file,
[INDENT]Apr 21 11:04:28 Server2 named[10823]: client 192.168.0.21#39956: updating zone 'groupe6.com/IN': update unsuccessful: lucid.groupe6.com/A: 'RRset exists (value dependent)' prerequisite not satisfied (NXRRSET)
Apr 21 11:04:28 Server2 named[10823]: client 192.168.0.21#39956: updating zone 'groupe6.com/IN': update failed: rejected by secure update (REFUSED)[/INDENT]

I don't know why! I searched on google but with no luck.
 - client: Ubuntu 10.04, 
 - AD: Samba 4 PDC with ADS 

please help me,
regards,

---

### Post by SerbisS on 2011-04-21
Try reading tutorial's posts. View for example the post nuber 25 and following; maybe it's your same situation.

---

### Post by UncleBoarder on 2011-05-09
Thank you for all your work!! :-)

Your script seems to work for most people but I'm having a problem.  I've been trying to get Active Directory integration working for the past three weeks.  Doing my own editing, I've been almost successful except for this error...

Failed to join domain: failed to set machine spn: Operations error

When I found your script I tried it and it still gave me the same error.  Perhaps all the installations and edits I've done along the way have caused a problem.  So I did a fresh installation of Ubuntu 10.04.2, updated my video and mouse drivers and installed VirtualBox...

Then I ran your script.  Same error.

sudo net ads join -U my_domain_admin 

**Failed to join domain: failed to set machine spn: Operations error**

I've exhausted Goggle with no solution.  Any ideas?

---

### Post by SerbisS on 2011-05-10
[SIZE=2]**> [SIZE=2][B]Failed to join domain: failed to set machine spn: Operations error**[/SIZE][/B]> 

[/SIZE]
[SIZE=2]I never seen this error before, I'm sorry...Here I wrote what I belive could be useful for you[/SIZE]

[SIZE=2]Maybe you have Samba4 instead of Samba3? [/SIZE][SIZE=2]I read that it could be the cause of the error.[/SIZE]
 
[SIZE=2]Remeber to update your fresh-installed machine before run the script.[/SIZE]
 
[SIZE=2]I know it's a stupid question, but are you sure that yours accounts are root or sudoer for Ubuntu and administrator for Window?[/SIZE]
[SIZE=2]Since I read that SPN is ***s**ervice **p**rincipal **n**ame *I thought that it could be a permissions problem[/SIZE]

[SIZE=2]DNS resolves names? Have you tested it?[/SIZE]
 
[SIZE=2]If you can try the procedure with another machine (virtual machine it's ok) and/or with another domain, in order to understand where the problem is located[/SIZE]
 
[SIZE=2]I know it's not so much but for now I haven't other ideas.[/SIZE]
 
[SIZE=2]Please let me know if something changes and please if you find the solution post it here![/SIZE]
 
[SIZE=2]Regards[/SIZE]

---

### Post by UncleBoarder on 2011-05-10
I forgot to mention the Samba version... Yes I'm running 3.4.7, I never installed Samba4.

I had not done the upgrade to my machine so to be certain, I completely reinstalled again... this time I ran apt-get update, installed the updates and then, installed the video drivers and set up IP, hostname, and hosts, then I ran your script.

Same result. :(

DNS does resolve properly... but I'm a little confused if I've done the root access correctly.  I set the root password so once I log on with my_domain_admin account (same name as my domain name), I then do 'su' and change to my root account.  Then I run your script.

After script is run, wbinfo works, then I tried net ads join -U my_domain_admin  (all from root prompt #)

**Failed to join domain: failed to set machine spn: Operations error**

I hope someone has some input.  Thanks again for your script, I think I'm close... but I'm still stuck.

---

### Post by SerbisS on 2011-05-11
[SIZE=3][FONT=Calibri]I read that it is possible that the user used to join your AD server has enough privileges to create the computer account, but not to update it.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[SIZE=3][FONT=Calibri]Try create another domain administrator account, ensure that your Ubuntu machine is not already present in yours AD hosts or use directly another one (with another name and SID) and try again the procedure.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Please let me know if it works.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3]Regards[/SIZE][/FONT]

---

### Post by UncleBoarder on 2011-05-11
I will remove the machine from the domain and have another admin try the 'net ads join' command.  In the mean time, I got this when I tried to leave...

```
root@x8387-u:/home/konowak# net ads leave -U konowak
Enter konowak's password:
[2011/05/11 09:21:29,  0] libads/ldap.c:3487(ads_leave_realm)
  Host account for x8387-u does not exist.
Disabled account for 'X8387-U' in realm 'LCSD.LOCAL'
``` Since my machine name is presented above in both lower, and upper case.  Could it be case related?  My machine name is all lower case.

---

### Post by UncleBoarder on 2011-05-13
A different domain admin (enterprise administrator) did not make any difference, same error.

I found that the 'net ads join' command DOES accomplish something, because without it, I can't access my Ubuntu based share from my Windows virtual machine.  Once I attempt to join the domain and get that error, I CAN then see my samba share.

However, while the share allows me to read and write files, when I try to set the permissions to a domain user name (which I can also browse to from Windows)... when I try to apply that user permission to a folder I get a permission error...

So error number one is still happening... "failed to set machine spn"

But if I try to move past that, it MOSTLY works, until I try to add permissions for a domain user.  Actually I used the domain admin account but I still get "Access is denied" when I try to apply permissions on the Windows machine.

I then tried adding your "valid users =@LCSD+konowak" parameter to my smb.conf.  With that parameter added, I can no longer access my share from Windows.

I hope that all made sense.  I don't know if the "failed to set machine spn" error is the cause or not, but, no matter what I do, I can not set Domain permissions on the share.

Confusing results...

```
root@x8387-u:/etc/samba# net ads testjoin
Join is OK
root@x8387-u:/etc/samba#
root@x8387-u:/etc/samba# net ads status -U konowak
Enter konowak's password:
ads_find_machine_acct: Operations error
```

---

### Post by UncleBoarder on 2011-05-17
I notice that your template krb5.conf file has the following...

```
[kdc]
profile = /var/kerberos/krb5kdc/kdc.conf
```I have no such directory nor a kdc.conf file... problem?

---

### Post by pardocorp on 2011-07-06
Thanks SerbisS tested en WS2008 :popcorn:

---

### Post by SerbisS on 2011-07-13
Thankyou for have tested it and for your feedback :D

---

### Post by idQp on 2011-08-29
hey folks,

only want to add some nice stuff. if you get this error msg: 

"Failed to join domain: failed to connect to AD: Strong(er) authentication required"

you must add the following line to your smb.conf (GLOBAL Settings):

client ldap sasl wrapping = sign

this is because of an microsoft update that enables the ldap signing requirement to your AD.


edit: this howto worked for me on debian 6.0 (squeeze) and windows server 2008 r2

---

### Post by SerbisS on 2011-08-30
Thankyou very much idQp. I added your trubleshooting to the guide!

---

### Post by arbabnazar on 2011-09-04
with these settings, I haven't access my Shared Folder (in this case home)from windows machine (or lan machine integrated to windows domain). 

Note: all the procedure went well.

here are the screen shorts, kindly help me.

[IMG]http://i54.tinypic.com/5whx7t.jpg[/IMG] [IMG]http://i52.tinypic.com/153lo3m.jpg[/IMG]

I can see the share in my windows machine but when i try to access it using my domain user account (in this case Administrator), then I got this error:

[IMG]http://i51.tinypic.com/2igmzy1.jpg[/IMG]

---

### Post by SerbisS on 2011-09-05
I can't see in your wbinfo command a user named "user" neither a group called "Domain Admins Group". You have to replace "user" with an existing domain user and "group" with an existing domain group.
Remeber to restart the services when finished to modify

---

### Post by arbabnazar on 2011-09-05
SerbisS, can you explain it with example as i didn't get because i am fairly new in linux...thanks

---

### Post by SerbisS on 2011-09-05
An example using your users and group info (from wbinfo command):
 
[FONT=Courier New][SIZE=3][test][/SIZE][/FONT]
[SIZE=3][FONT=Courier New]path = /media/test --> This directory must exist[/FONT][/SIZE] 
[SIZE=3][FONT=Courier New]available = yes[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]read only = no[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]browsable = yes[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]public = yes[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]writable = yes[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]valid users =@"[COLOR=#000000]HOME[/COLOR]+domain users" DOMAIN+arbab[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]admin users [EMAIL="=@"HOME+Domain"]=@"HOME+Domain[/EMAIL] Admins"[/FONT][/SIZE]
 
 
This allow all the users of "domain users" group and the user "arbab" to access the directory /media/test and set all the users of "domain admins" group as administrators of that folder
 
When you have finished to modify smb.conf restart the service with:
 
```
 
sudo service smbd restart

```

---

### Post by arbabnazar on 2011-09-05
SerbisS, that's excellent, after making the changing(that you mentioned) in the smb.conf file, it work and even didn't ask for the password to access this test folder.

But still i want to ask you the meaning of these two lines,truth to be told, i didn't get the meaning of these two lines........please explain these two lines, please...........

valid users =@"HOME+domain users" DOMAIN+arbab
admin users =@"HOME+Domain Admins"

Thanks...

---

### Post by SerbisS on 2011-09-05
I already wrote about this at the end of the tutorial. I really don't know how explain it better..

> [SIZE=3][FONT=Courier New]valid users =@[COLOR=#000000]DOMAIN_NAME[/COLOR]+domain_group DOMAIN_NAME+domain_user[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]admin users =@"DOMAIN_NAME+domain group with space"[/FONT][/SIZE]After "**=**" you specify domain users and groups can access the folder

When you want to specify a group you have to begin with "**@**". **NOTE**: no space between "=" and "@"

If a group has a name with spaces you have to use benchmarks -->** " "**

Then you put your DOMAIN_NAME+domain_group or DOMAIN_NAME+domain_user


At the place of "DOMAIN_NAME" put your domain name

At the place of "domain_group" put your domain group name

At the place of "domain_user" put your domain user


So in your case in order to grant access to the user "arbab" you have to write HOME+arbab (yes, I make a mistake before)

In order to grant access to the group "domain users" you have to write @"HOME+ domain users"

and so on...

---

### Post by arbabnazar on 2011-09-06
Thanks for explanation, 

valid users =@DOMAIN_NAME+domain_group DOMAIN_NAME+domain_user


I know, I am wasting your time but it might be helpful for other's as well. 

Lets see I want to give access to all the domain users to access this folder than manually i have to add these users with the mentioned command or there is a better way, this thing confuse me that's why i asked for explanation.

---

### Post by SerbisS on 2011-09-06
Oh come on! Maybe you don't know what's a domain group: [http://technet.microsoft.com/en-us/library/bb727067.aspx](http://technet.microsoft.com/en-us/library/bb727067.aspx)
 
If you add "domain users" group to smb.conf you grant access to all the members of that group, in this case all the users of your domain
 
So if you need that just some users have access to that folder you can add domain user names one by one in your configuration or you can create a group, named for example "FolderAccessUsers", add in that group the users you want and then add that group in smb.conf as explicated before
 
Regards

---

### Post by arbabnazar on 2011-09-06
SerbisS, that's simply owsome, the way you explain is the things are simply excellent..........and i really appreciate your efforts....you devoted a lot of time to your thread. 

I just want to say bundle of thanks, million of thanks to you... Hope you will bring a lot of thread like this for us.

Thanks for your really really good,helping and positive attitude.

---

### Post by SerbisS on 2011-09-06
You're welcome

---

### Post by guimenez on 2011-10-10
> **SerbisS said:**
> You're welcome
Hi

first of all many thanks for all the great work you are making for this community.

I have 2 problems.

I run the script and everything work fine.
But sometime i can success login, and other times i can't login (i think it lost domain)

if i go to a terminal and run kinit username
it works well and make the login with kinit.

hope you can help me on that

many thanks

---

### Post by SerbisS on 2011-10-13
> But sometime i can success login, and other times i can't login (i think it lost domain)
 
I'm sorry, too little information to help you. I need to know the systems you use, any errors and\or the circumstances in which they occur. 
 
Right now for me it may be also an ethernet cable damaged.
 
>  
I have 2 problems.
 

 
What's the second?
 
Regards

---

### Post by guimenez on 2011-10-14
> **SerbisS said:**
> I'm sorry, too little information to help you. I need to know the systems you use, any errors and\or the circumstances in which they occur. 
 
Right now for me it may be also an ethernet cable damaged.
 

 
What's the second?
 
Regards
Thanks for the reply.

I have 2008 r2 server and Ubuntu 11.04 on the client side.
I'm using 37 machines.
Sometimes some machines doesn't login, but if i go to terminal on that machine and run kinit "username" of the domain it logins well.

Can you tell me what is the log file that i need to open to tell you what are the errors?

My second problem is now solved. I'm using pam_mount.xml to mount the shared folder of the user that starts the login, but sometimes i can't write to the mount folders. I found that the problem was smbfs. now i'm using cifs and that problem its solve :)

Do you know if this perfect script work on 11.10?

many thanks

---

### Post by SerbisS on 2011-11-30
I have too many things to do at this time. Really sorry I can not help you now... ](*,)

I found this:
> [http://www.ubuntugeek.com/how-to-active-directory-integration-with-centrify-directcontrol-express-on-ubuntu-11-10-oneiric-ocelot.html](http://www.ubuntugeek.com/how-to-active-directory-integration-with-centrify-directcontrol-express-on-ubuntu-11-10-oneiric-ocelot.html).
Not tested yet but it looks good, If you try it let us know how it is

 Regards

---

### Post by guimenez on 2011-12-01
> **SerbisS said:**
> I have too many things to do at this time. Really sorry I can not help you now... ](*,)

I found this:
.
Not tested yet but it looks good, If you try it let us know how it is

 Regards

Many thanks :D

I will try it and let you know

---

### Post by UncleBoarder on 2011-12-05
Perhaps I've found an answer to my error...

***"Failed to join domain: failed to set machine spn: Operations error"***

I've found a number of people posting the same error, but no answers.  This thread I found is a little over my head so if you could read through it when you get a chance, I think it may be a non critical error.  It would be very helpful if you could add to your instructions, if this error is important or not.  Check this reference...

[http://samba.2283325.n4.nabble.com/Failed-to-join-domain-failed-to-set-machine-spn-Constraint-violation-td2448157.html](http://samba.2283325.n4.nabble.com/Failed-to-join-domain-failed-to-set-machine-spn-Constraint-violation-td2448157.html)

---

### Post by ccsalway on 2012-01-23
> **guimenez said:**
> Do you know if this perfect script work on 11.10?


just installed it on 11.10. works great! THANK YOU SOOOOOOOOOO MUCH

Had to do just one extra thing though, 

apt-get install krb5-user  to test if kinit was working


Couple of things I did after

net groupmap add ntgroup="Domain Users" unixgroup=users
net groupmap add ntgroup="Domain Guests" unixgroup=nogroup
net groupmap add ntgroup="Domain Admins" unixgroup=root

---

### Post by wadl on 2012-05-01
Thank you very much for this Howto! Worked perfectly with Ubuntu 10.04 and Windows Server 2008 R2.

However when I log in to the Linux box via SSH, I get the following messages

Could not chdir to home directory /home/DOMAIN/ad_user: No such file or directory
groups: cannot find name for group ID 10006
groups: cannot find name for group ID 10008
...

Do you by chance know what causes the groups messages to appear? Is there a mapping between local groups and AD groups which has to be made or how is this handled?

How do you handle creation of home directories for Active Directory users? For me it seems that either they have to be manually created properly before users will be able to log in or that one has to use the pam_mkhomedir.so PAM module to automatically create local home directories “on the fly” as users log in.

Perhaps you can help me on that.

Regards

---

### Post by SerbisS on 2012-05-26
> Had to do just one extra thing though, 


[FONT=&quot]Thankyou. I’ve added your comment in troubleshooting section[/FONT]

---

### Post by SerbisS on 2012-05-26
> Could not chdir to home directory /home/DOMAIN/ad_user: No such file or directory Here you try to login through ssh with “ad_user”, right? If you make the same login not through ssh, home directory is created? 

Maybe it’s a permission problem. If when you login directly from the Linux machine (not through ssh) home directory is not created try with:
```

  #chmod u+rw /home/$SUPER_USER/.ICEauthority
```[FONT=&quot]
[/FONT]Where “/$SUPER_USER” is the sudoer user used to join Linux machine to the domain
  
  > Is there a mapping between local groups and AD groups which has to be made or how is this handled?  Try with “#wbinfo –u” and “#wbinfo –g”. These command have to list all domain users and groups (from a joined Linux machine of course)
  
  Use “#getent” for fetch user account entries from administrative database (/etc/passwd and /etc/group)

This command (where “user” it’s a domain user)

  ```
#getent passwd user
```  Makes an output like this more or less
  ```
#user:x:1000:1000:User,,,:/home/user:/bin/bash
```  You can see:
  •             login name (user)
  •             x (encrypted password and stored in /etc/shadow)
  •             User ID or UID : 1000
  •             Group ID or GID: 1000
  •             Then additional informations are listed (as phone, full name, etc..)
  •             Home directory
  •             Command shell absolute path
   
  You can do the same for groups with:

  ```
#getent group user
```  Hope that this could help you. If you solved let us know.
   
  Regards

---

### Post by SerbisS on 2012-05-26
> Perhaps I've found an answer to my error...

I read this thread, but I can't found solutions.

I think you have already try with:

```
# net ads join --disable-dns-update 
```

And you already create a completely new super user and\or admin user and try operation with it, right?

Cannot figure out other possible solution


Please let us know if you found a solution, 
Regards

---

### Post by Elfy on 2012-06-29
This thread is closed. 
 
The information is now held on the community wiki at  [https://help.ubuntu.com/community/SambaActiveDirectoryDomainIntegrationScript](https://help.ubuntu.com/community/SambaActiveDirectoryDomainIntegrationScript)
 
Thank you for your thread and the work you have done in keeping it current and of use to the community. 
 
A thread for discussion of the wiki can be found at  [http://ubuntuforums.org/showthread.php?t=2012421](http://ubuntuforums.org/showthread.php?t=2012421)
 
 
Support threads regarding the wiki and it's content should be created in a suitable forum.

---

