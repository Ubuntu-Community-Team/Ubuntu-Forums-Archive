---
title: "File server"
date: 2007-05-11
forum: Server Platforms
---

### Post by borahshadow on 2007-05-11
I know there are lots of threads on samba and file servers but I still have some questions
here are my needs 
1 public directory I think I can handle this. I was thinking about locating it in /shared or something.  This should be fully public for pictures etc.

I have already created an account for every member and I figured that I would share their /home folder.  But have it so that they they can access their share from any computer by typing in their username and password or by mapping it as a drive when they log on.

so my questions are
 
do they have to have a separate samba user or something or will their linux username and password be synced(the same) as the password they use to access their files?

If they have to have a separate SAMBA user/pswd combination how could I sync that with their linux user?

what does it involve to have a share map when they logon to their computer?

what is the deal with winis or what ever? I think I want it but I don't fully understand what it is

Do I want this server to be a domain controler like[ _this_]("http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10_p3")?
the above domain controller thing sounds like ever computer needs to be added to the config file.  If say my brother-in-law wants to come over and I want to show him a file on my share on his laptop I want to be able to just put in a password, not add his temporary dhcp address to a config file. correct me if that is not what a domain controller is, but if it is then I don't want a domain controller
What is quota (in the above tutorial)?
What is active directory ? do I want it?
I want to be able to share printers etc. I think I can manage that but if someone wants to give me hints on that I would not mind one bit
I figured I would set this up static ip address which I also think I can manage but once again I won't complain if someone wants to post something to help me more fully understand how (I know how I can make it static but a tutorial could help me fully grasp what each line in the config file does)
and any other suggestions are welcome to
thanks
here are some tutorials I was looking at

[how to forge (linked above)]("http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10_p3")

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch10_:_Windows,_Linux,_and_Samba]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch10_:_Windows,_Linux,_and_Samba")

I also looked at many others but those two cover mainly the same things that all the other guides that I looked at
ps I'm not against Command line editing but I like GUI editing too
I want /was considering (but don't have to) use SWAT that way I get a GUI and I can change settings on the share super easy from any computer on the network I have use SWAT a little before so I know my way around if some

Thanks again these forums are great

---

### Post by dmizer on 2007-05-11
if you add your users to your file server like so:
```
sudo useradd -s /bin/true winusername
sudo smbpasswd -L -a winusername
sudo smbpasswd -L -e winusername
```
they will not have a home folder, and they samba users will not have the ability to gain root access.  it's safer and easier to manage users this way.

if you add your samba users with the exact same username and password as they use in windows, they will not be prompted for a password when accessing your server.

here's my common (but not public) directory listing in smb.conf:
```
[common]
    path = /home/shared/common
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = ubuntu
    force group = ubuntu
```

here's the section in my samba.conf i created to limit access to one user:
```
[kappa$]
    path = /home/shared/winuser
    browseable = no
    read only = no
    guest ok = no
    valid users = windowsuser
    create mask = 0644
    directory mask = 0755
    force user = ubuntu
    force group = ubuntu
```
the "$" after the share name prevents it from being seen from other user's "my network places".

more information on the actual configuration of your server can be found in the first link in my sig.

i would strongly suggest against having different samba/windows usernames and passwords.  it compilcates matters, and often causes difficulty when trying to mount your shares.  it also makes it easier to keep track of which account belongs to which user.

a domain controller keeps track of each computer and their respective human readable name.  so instead of having to browse to your server by typing: smb://192.168.1.2/share for example, they can browse to smb://borahshadows-server/share.  if you have a one time user who you want to allow access to your server, you shouldn't have to worry about adding him/her to your domain unless you want to access your guest's machine from your network.  there's a good howto on configuring your hosts file, but i don't have time to hunt it down.  i'll post it later if i get caught up.

wins is a windows netbios domain name controller.  it has advantages and disadvantages.  one of it's biggest advantages is that it comes configured by default on windows machines.  it does take some doing to get it working on a linux box though.  check the second link in my sig for more information on that.

don't know much about swat ... i use webmin and it works fine.  it does come in handy to have a web point and click interface on occasion.

i think i touched on everything.  let me know if you have more questions or if i've missed something.

---

### Post by borahshadow on 2007-05-11
ok thanks for the reply
I have already created every body accounts because they will also be using it for more than a file server (VNC)
so will samba just read those accounts what do I have to do to make them work with samba do I just make a samab group and add them all to it?
the deal is not everybody has their own windows machine
 we have a family computer that is used my everybody but because of windows XP's stupid user management system we all end up using one account
so some people might want to have their share prompt for a password (ps when they enter their password iwindows stores it until you log out right?) but might also want to have it mapped always on their computer 

and my sister on her laptop runs win98 and i don't think she even has a password on her laptop so if she had it mapped then would it just prompt her for a password when she turned her comp on?

keeping track of which account is which should not be a problem considering <5 users and everybody having their name be their account name and they probably want different passwords I don't think I can change that

ok now in that how to forge tutorial what is quota do I want to install it?
and it sais this> Adding Users To Our SAMBA Domain

Now we will add a user, e.g. tom, to our Samba domain. You will have to add a user like this for each user account you want to connect to this SAMBA domain server.

1) Add a Linux user tom:

useradd tom -m -G users

2) Add the Linux user tom to the SAMBA password database:

smbpasswd -a tom
I already have the first step done I think (adding users)
but I don't know what the second step does I think it makes their account work with samba (I mentioned above possibly having a samba group) if user #1 wants to change their password will samba see that change too?

I know in windows that you can access things with names and not IP addresses but where my network is DHCP the computers usually have the same IP address but it is possible for that to change
windows some how seems to handle that change transparently ie. it seems to scan or something to find out what the computer names are
if I have to say this IP = this name then if that computer's IP changes then what happens
Thanks I think you touched most everything but I am still open to more help and anwsers to my above questions thanks everybody

---

### Post by borahshadow on 2007-05-12
ok so I decided that I like KDE's samba configuration GUI and decided to just start configuring it
I installed all samba samba-common samba-doc libcupsys2-gnutls10 libkrb53 winbind smbclient like the how to forge said to and I configured my server with a static ip
then I thought I would just use the GUI to configure things but nothing seemed to take effect so I ended up just making a backup of the smb.conf and pasting the one from howto forge
I changes the things like workgroup etc and I removed all the shares except for printers and print$
I then added this share
> [shared]
case sensitive = no
msdfs proxy = no
read only = no
comment = Public Files
path = /shared
create mask = 0777
directory mask = 0777
I now have a smb config that looks like this 
> 
[global]
workgroup = WORKGROUP
netbios name = SERVER-HOME
server string = Home File Server


passdb backend = tdbsam
username map = /etc/samba/smbusers
name resolve order = wins bcast hosts
domain logons = yes
preferred master = yes
wins support = yes

# Set CUPS for printing
load printers = yes
printcap name = CUPS
printing = CUPS
printer admin = @lpadmin

# Default logon
logon drive = H:
logon script = scripts/logon.bat
logon path = \\server1\profile\%U


# Useradd scripts
add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
delete user script = /usr/sbin/userdel -r %u
add group script = /usr/sbin/groupadd %g
delete group script = /usr/sbin/groupdel %g
add user to group script = /usr/sbin/usernod -G %g %u
add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
winbind uid = 15000-20000
winbind gid = 15000-20chmod 777 /var/spool/samba/ 000
template shell = /bin/bash


# sync smb passwords woth linux passwords
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
passwd chat debug = yes
unix password sync = yes

# set the loglevel
log level = 3
restrict anonymous = no
domain master = no
set primary group script = /usr/sbin/groupadd %g
max protocol = NT
ldap ssl = No
server signing = Auto
map to guest = Bad User
guest ok = yes

[printers]
comment = All Printers
path = /var/spool/samba
printable = yes
create mask = 0700

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
write list = root, @smbadmin

[shared]
case sensitive = no
msdfs proxy = no
read only = no
comment = Public Files
path = /shared
create mask = 0777
directory mask = 0777

I have no Idea what this is for
> # Default logon
logon drive = H:
logon script = scripts/logon.bat
logon path = \\server1\profile\%U

or this
> 
# Useradd scripts
add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
delete user script = /usr/sbin/userdel -r %u
add group script = /usr/sbin/groupadd %g
delete group script = /usr/sbin/groupdel %g
add user to group script = /usr/sbin/usernod -G %g %u
add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
winbind uid = 15000-20000
winbind gid = 15000-20chmod 777 /var/spool/samba/ 000
template shell = /bin/bash
why do I need user add scripts?

anyway that allows anyone to click on the server from my network places etc. and see and use the shared folder (no password nessissary because of the guest account)
but my problems arise in the fact that I cannot add any samba users if I add them then they just dissappear when I click ok I have tried with the smbpasswd command too
so I did 
> sudo touch /etc/samba/smbusers
sudo touch /etc/samba/smbpasswd

and still no good I even tried chmoding those files to 777 (I changed it back because it didn't make a difference) so I am stuck
I want to have it so that every body can see the shares list without a username password which is accomplished with the guest account and then if they try to access their share or any share that the guest account does not have access to then it prompts them I can do this except for the fact that I can have no users so any share I set up that needs a user cannot be accessed (that is why I have none in my smb.conf right now)
If anybody has any ideas about this please let me know
BTW what does this do 
> Edit /etc/nsswitch.conf. Change the line:

vi /etc/nsswitch.conf

hosts: files dns

to:

hosts: files wins dns
I have done this but it does not help any ether

and BTW I have not added anything to my /etc/hosts file yet but as long as I have everycomputer set up to look at this for a wins server it does not matter right? (I plan to add them to my hosts file but I have not yet and that shoulden't be causing my user problems)

thanks

---

### Post by dmizer on 2007-05-12
your problem may not be ubuntu.  your problem may be windows firewall software.

also ... i strongly urge you not to allow the windows 98 computer to have access to your shares.  it will quickly infect your connected machines.  windows 98 is NOT a safe operating system.

use this smb.conf file instead ... i KNOW it will work, and there's no reason for it to be as complicated as the one you posted:
```
[global]
    ; General server settings
    netbios name = SERVER-HOME
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[shared]
    path = /shared
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = [COLOR="Red"]ubuntu_username[/COLOR]
    force group = [COLOR="Red"]ubuntu_username[/COLOR]
```
replace "ubuntu_username" with your actual ubuntu username

then add your ubuntu user to the samba group:
```
sudo smbpasswd -L -a ubuntu_username
sudo smbpasswd -L -e ubuntu_username
```
again, replacing ubuntu_username with your actual ubuntu username.

restart samba:
```
sudo /etc/init.d/samba restart
```
now, if you can't view, read, and write to the files on your ubuntu computer, you'll need to take a very close look at your windows machines ... firewalls in particular.

this will give you password free access to /shared

as for your password prompting ... that cannot happen unless your windows users have their own account in windows, each with their own password, AND you have to make sure that those windows user accounts are added to the samba group in ubuntu along with their password.  there's simply no other way i can think of to make this happen when all windows users are using the same guest account in xp.

as far as wins is concerned ... let's not worry about that just yet.  for the time being, your windows computer will take care of name resolution for you.

---

### Post by borahshadow on 2007-05-12
ok thanks good idea to start simple (possibly add wins later)
I used that smb.conf and added me to the users with that command
I then went to my windows box and removed the wins server and I had full access the only problem is that everything was created with my user name in the public share (I was thinking about making a samba user group and just adding all of my needed accounts to it and using that instead)
anyway I then went and shared my home folder the same way, just with the public=off
 great it prompted my for a password but it would only let me use the user guest, I had to use my password though?
oh what ever I tried backing out of the directory and going back in ok no prompt just like I expected then I logged out and logged back in , ok it prompted me again great everything so far is working about like I expected

I then added the rest of the users to samba with those commands and I made another share same as mine except for that I used force user to a different one
I then restarted samba
and went back to my windows box when I tried to access the new share it prompted me for a password, I put in that users ok great I went back and tried to access my share
What? their password worked on my share I don't want this
I logged out (so windows quit storing that password) and logged back in and I could access their share with my password too not good

I thought that I would just say reject all unspecified users and then only specify the people I want to be able to access that share, but there is a problem even though samba seems to accept those usernames /passwords. (actually just passwords since it forces guest in the user name ) none of those users show up in my GUI config utility as being registered with samba

also since I have sync with unix password off if they change their unix password it won't change their samba password right? I want to renable that if you think I can

and also when I go to my network places >view workgroup computers I can see the server but when I click on it is gives an error massage about can't fine server-home but if I type in the ip it works (this is because of wins being disabled right?)

also I noticed that the security level was changed to share which is what I originally thought i wanted but then I saw that if you want to use if as a PDC or anything then it has to be user so I might need/want to change that I realize that under user they can't even see the shares without a password and then when they logon they can but I think I can live with that (and I think I found a workaround with allowing guest logons but the guest only has access the the public share)

any way I really need to figure why it is being stupid with users

ps about this
> as for your password prompting ... that cannot happen unless your windows users have their own account in windows, each with their own password, AND you have to make sure that those windows user accounts are added to the samba group in ubuntu along with their password. there's simply no other way i can think of to make this happen when all windows users are using the same guest account in xp.
I figured that I would just tell them if they loginto their share from the public computer then they will stay loged on until they logoff and back on to the public computer (once again to clear windows memory of that password) and if they tried to access share1 with user1's password and then left and user 2  tried to access share2 with out logging off and back on wouldn't it just not allow access to share 2 without a different password? (and possibly a relogon)

anyway I can deal with that but I do need to get the user problem fixed

EDIT looks like I might be installing SWAT or another GUI I was just going to use KDE's GUI but it looks like I'm not the only one having trouble with it 
[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/16575]("https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/16575")

---

### Post by borahshadow on 2007-05-12
OK I think I have this almost figured out
I Have it configured at user level security so everybody needs an account

I have a homes section like this
> 
[homes]
read only = no
create mask = 764
valid users = %S
browseable = no

Which makes it so that when they log on they see a folder with their name on it which is their home directory (If I have browseable = yes then they have a folder with their name on it AND a folder named homes which point to the same thing)
also they can only access their home folder due to the valid users = %S
 the only thing that I still would like to have/do would be to have no logon nessissary to see the shared directory I have tried different things with guest accounts and such and I think I will just make an account named guest that has access to the shared directory
but I don't want that guest account to 
               Have a password
               or a home folder (that would mean putting something like invalid users = guest under homes right?)
               or be able to use their account like a not\rmal UNIX account like the rest of everybody
also would I want to force group and user to the guest account?

PS for anybody who cares for the shared computer rather then having to logout you can run the command > net use \\NAMEOFCONNECTION /delete in the windows command prompt (start>run cmd)
which will disconnect you from the server so someone else can login 
you can add a batch script with that on the desktop or something (where NAMEOFCONNECTION is ether an ip adderss or a wins name
(in the script it might be beneficial to include the command twice once with an ip and once with a wins name because windows treats those like different connections so then one command will fail but that should not cause any problems))

also I have files that start with a DOT "." hidden but when their windows box is configured to show idden files that makes their home directory very cluttered is there any way around this? besides telling them to disable hidden files?

Now should I try setting up the wins server because I can see the server in My Network Places but when I click on it it won't connect it says it can't find it so right now I have to access with its IP
Edit: 
> when I click on it it won't connect it says it can't find it so right now I have to access with its IPit only does this on some of my computers?

---

### Post by dmizer on 2007-05-12
i think you're getting confused with "accounts".

unless you've added all your users with different logins on your windows machine, you really only have ONE account.  so even though you have multiple users added in your ubuntu computer, your ubuntu computer only ever sees your windows computer as the same exact account every time it tries to connect.  until you have different users on your windows machine, you're going to continue to have problems.

authentication (password protection) needs to take place in two locations.
1) on your windows computer when you log in.
2) on your ubuntu server, which reads your user account information from your windows computer as it connects.

once you have set up multiple users in windows, it's simple to allow everyone to access the common share without password challenge (and without having to relegate them to a common guest account).  it's also simple to prevent other users from gaining access to another user's share.

your common account share will look like this (just as i've posted above):
```
[shared]
    path = /shared
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = ubuntu_username
    force group = ubuntu_username
```
this will allow anyone logged in under any account to access files located on the /shared directory.

then you will need to create an entry like the following for each respective user on your windows computer:
```
[user1-share]
    path = /home/user1
    browseable = no
    read only = no
    guest ok = no
    valid users = windows-user
    create mask = 0644
    directory mask = 0755
    force user = ubuntu_username
    force group = ubuntu_username
```

---

### Post by borahshadow on 2007-05-14
ok thanks I'm ready to be done with this
I have baged the idea of being able to have everybody share an account on the public computer everybody will have a different account
so I changed the account on the server to match the username of the windows user
but when they try to access their share it still pops up a prompt for a password and in the username field it says Guest and it is grayed out so you can't change it ???
I think everything else is setup how it should be

Ps what happens if the windows user decides to change their password? on their windows machine?

---

### Post by dmizer on 2007-05-15
okay ... let's step back for a second.

you've changed your main ubuntu user account.  so you'll have to add that to the sama group as i indicated above:
```
sudo smbpasswd -L -a new_ubuntu_username
sudo smbpasswd -L -e new_ubuntu_username
```

keeping in mind at this point ... it doesn't matter a hill of beans what the user id on the ubuntu machine is, just that it's added to the samba group as above.  in fact ... it's better to have the main ubuntu account different from any of the windows accounts.  again ... this is simply to make it easier to keep track of them all.  remember, you indicated you're only working with five accounts ... and it's still an issue to keep track of it all.

so let's lay this out ...

i assume you now have 5 accounts on your windows box.  i don't know what they are so i'll call them as follows:
[LIST]
[*]user1
[*]user2
[*]user3
[*]user4
[*]user5
[/LIST]

you should also have an ubuntu account separate from your windows user names:
[LIST]
[*]ubuntu1
[/LIST]

now ... you indicate that you've added users to the ubuntu machine with the idea that they would access them later in a vnc environment.  this is fine, but they still need to be added to the samba group just as your ubuntu1 account needed to be:
```
sudo smbpasswd -L -a user1
sudo smbpasswd -L -e user1
```
with each user on the windows machine.  make sure passwords and user names match exactly.  the user changing their own password on the windows computer is a valid concern, but we can worry about that down the road.

now, you should have a smb.conf file that looks something like this:
```
[global]
    ; General server settings
    netbios name = SERVER-HOME
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[shared]
    path = /shared
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = ubuntu1
    force group = ubuntu1

[user1-share]
    path = /home/user1
    browseable = no
    read only = no
    guest ok = no
    valid users = user1
    create mask = 0644
    directory mask = 0755
    force user = ubunt1
    force group = ubunt1

[user2-share]
    path = /home/user2
    browseable = no
    read only = no
    guest ok = no
    valid users = user2
    create mask = 0644
    directory mask = 0755
    force user = ubuntu1
    force group = ubuntu1

[user3-share]
    path = /home/user3
    browseable = no
    read only = no
    guest ok = no
    valid users = user3
    create mask = 0644
    directory mask = 0755
    force user = ubuntu1
    force group = ubuntu1

[user4-share]
    path = /home/user4
    browseable = no
    read only = no
    guest ok = no
    valid users = user4
    create mask = 0644
    directory mask = 0755
    force user = ubuntu1
    force group = ubuntu1

[user5-share]
    path = /home/user5
    browseable = no
    read only = no
    guest ok = no
    valid users = user5
    create mask = 0644
    directory mask = 0755
    force user = ubuntu1
    force group = ubuntu1
```

restart samba, or simply reboot your server.

after restarting, all users should be able to view the common share, but perhaps not yet be able to view their own share.  map each user's individual share on the windows machine like so (i've highlited your needed network path in blue):
>    1. Open Windows Explorer or My Computer from the Windows Start Menu.

   2. From the Tools menu, click Map Network Drive&#8230;. A new Map Network Drive window opens.

   3. In the Map Network Drive window, choose an available drive letter from the dropdown list located next to the "Drive:" option. Any drives already mapped will have a shared folder name displayed inside the dropdown list, next to the drive letter.

   4. Type the name of the folder to map: [COLOR="Blue"]\\SERVER-HOME\user1-share[/COLOR].

   5. Click the "Reconnect at login" checkbox if this network drive should be mapped permanently. Otherwise, this drive will un-map when the user logs out of this computer.

   6. If the remote computer that contains the shared folder requires a different username and password to log in, click the "different user name" hyperlink to enter this information.

   7. Click Finish.

   8. If the drive letter was previously mapped to a different location, a message box will appear asking to replace the current connection with the new one. Click Yes to disconnect and un-map the old mapped drive.

   9. If the Finish operation succeeds, the network drive will be mapped. If the network drive cannot be mapped, ensure the folder name is spelled correctly, that this folder was correctly set up for sharing on the remote computer, that (if necessary) the correct username and password have been entered, and that the computer network connections are functioning properly.
[above taken from about.com](http://compnetworking.about.com/od/windowsxpnetworking/ht/mapnetworkdrive.htm)

test this and see if it works.  if you're still having problems, post back :)

---

### Post by twinax on 2007-05-15
Hi Dmizer
I have a sort of similar situation,  please let me know if your setup will work .  I have 24 computers in the office.  There is one windows 2000 server, there is a program there for payroll, no domain controller.  No active directory or login in any where. Each desktop is really standalone. I have a DHCP fortigate firewall. No windows box where all the users are registered that is. 

 I want to create a shared folder for anybody and everybody to use with no password prompt.  I also want to create department folders  -password promt required - so I would create groups on Ubuntu.. And then I want to create , individual folders password protected for each user 
Appreciate your help'
Regards
RS

---

### Post by borahshadow on 2007-05-15
ok i'll try that when I get a chance to day I can't right now but one question first shoulden't I force the user to use THEIR account not ubuntu1? shoulden't it look like this
> [user1-share]
    path = /home/user1
    browseable = no
    read only = no
    guest ok = no
    valid users = user1
    create mask = 0644
    directory mask = 0755
    force user = **user1**
    force group = **user1**
not this
> [user1-share]
    path = /home/user1
    browseable = no
    read only = no
    guest ok = no
    valid users = user1
    create mask = 0644
    directory mask = 0755
    force user = **ubunt1**
    force group = **ubunt1**
did you say you would recommend having an account for samba so I have an account for all 5 users (including me) and then an account for samba? or just use my account for the "ubuntu1" account
and one last question they don't have to map the drive they can just go to My network places right?

thanks for all your help I've probably been frusterating but I appreaciate all that you have done to explain to me how things SHOULD work (not the way that I've been doing thisgs)

---

### Post by dmizer on 2007-05-15
> **borahshadow said:**
> ok i'll try that when I get a chance to day I can't right now but one question first shoulden't I force the user to use THEIR account not ubuntu1?
no, it should be just as i've done it.  your suggestion was the mistake i made when i tried to put together my first server.  the force user/group options arrange for the correct os level permissions on the server side.  the "valid users" option provides for the authentication.

> **borahshadow said:**
> did you say you would recommend having an account for samba so I have an account for all 5 users (including me) and then an account for samba? or just use my account for the "ubuntu1" account
you need one account on your ubuntu server with sudo capability (this is probably your personal ubuntu user ... or whatever user you created when you installed ubuntu).  this will be the user that will appear in the "force user/group" lines.  this user should NOT also be a user id on any of the windows accounts.

none of the other users should have sudo capability unless absolutely necessary.

> **borahshadow said:**
> and one last question they don't have to map the drive they can just go to My network places right?

thanks for all your help I've probably been frusterating but I appreaciate all that you have done to explain to me how things SHOULD work (not the way that I've been doing thisgs)
you've not been frustrating at all.

as for mapping the drive, i think it's necessary.  but you only have to do it once.  then they can browse to the share from my network places or from my computer if they like.

---

### Post by dmizer on 2007-05-15
> **twinax said:**
> Hi Dmizer
I have a sort of similar situation,  please let me know if your setup will work .  I have 24 computers in the office.  There is one windows 2000 server, there is a program there for payroll, no domain controller.  No active directory or login in any where. Each desktop is really standalone. I have a DHCP fortigate firewall. No windows box where all the users are registered that is. 

 I want to create a shared folder for anybody and everybody to use with no password prompt.  I also want to create department folders  -password promt required - so I would create groups on Ubuntu.. And then I want to create , individual folders password protected for each user 
Appreciate your help'
Regards
RS

several things here ... but first and foremost, in an office environment you should never have a non-password protected share.  even a common share should be password protected.  this will help to inhibit possible office wide infections.

your desired setup is somewhat more complicated than what is discussed here.  i highly suggest you take a very close look at the first link in my sig, and browse through the succeeding several pages of posts.  i don't remember exactly where, but your configuration is discussed.

---

### Post by borahshadow on 2007-05-15
ok well I think I'm almost there I backed up my smb.conf and posted the one you gave me but modified the usernames here it is now (I have blanked the names of the users)
> [global]
    ; General server settings
    netbios name = SERVER-HOME
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[shared]
    path = /shared
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0664
    directory mask = 0755
    force user = samba
    force group = samba

[*****]
    path = /home/*****
    browseable = yes
    read only = no
    guest ok = no
    valid users = *****
    create mask = 0664
    directory mask = 0755
    force user = samba
    force group = samba

[*****]
    path = /home/*****
    browseable = yes
    read only = no
    guest ok = no
    valid users = *****
    create mask = 0664
    directory mask = 0755
    force user = samba
    force group = samba

[*****]
    path = /home/melissa
    browseable = yes
    read only = no
    guest ok = no
    valid users = *****
    create mask = 0664
    directory mask = 0755
    force user = samba
    force group = samba

[*****]
    path = /home/*****
    browseable = yes
    read only = no
    guest ok = no
    valid users = *****
    create mask = 0664
    directory mask = 0755
    force user = samba
    force group = samba

ok I added a user samba 
I made that user a member of every group that I am plus a member or every user's group I didn't know weather to make samba a member of the sudo group or not but I didn't because I am not and so I don't know whether samba can sudo or not but I just made it the same as my account which can
I then added every user (real person users) to the samba group as well 
I did that because you said that the "ubuntu1" account should not have a windows account otherwise I would have just used my account which I might prefer
anyway
I added samba to the samba users and enabled it
I restarted samba
ok now here is the deal I went and logged on to my windows account (same user name as my linux account but no password(it is a vm))
I then went to the share and clicked on my folder it brought up a prompt again it had guest in the user name box (grayed out) but I put in my samba password and boom I was in 
ok great but I did/do not have full access rights I noticed this is because my home folder has privileges such as owner can read&write and everyone else can read but it was forced to the samba user and group.
why can't I force me to use my user and group???
also I noticed that in the smb.conf you gave my everything had create with 644 I changed that to at least 664
and shouldn't the shared folder even have 666 or something?
the shared folder has 664 permissions but the folders in it do not so i can write to the shared folder but none of the sub folders

I also went ahead and mapped my drive I did enter the username and password but I still do not have write privileges 

and one of my users has a space in their username I know this is less then Ideal but you said that they need to match and I don't think I can convince(it is my dad) him to change his username on his laptop so I have to make the username on the server match (you said) 
in the path to his share do I need a "\" before the space or not same question on the valid users line
thanks

---

### Post by dmizer on 2007-05-16
on the linux side, you're better off not fiddling with permission levels.  some things will simply refuse to function correctly if their permissions are not set correctly.

now, the folder /shared is a folder you created (it's not a part of standard linux file system structure).  you can change permissions on this folder to 777.  you will still need to leave the permission masks in place just as they are.  these are masking the permission levels to allow proper communication between windows and linux clients (who use different permission structures).

you can't change the permissions on the /home/user* directories because as i indicated before ... it will break their home.  you should have read/write ability on the /home/user* directory only but most likely not the sub directories therein.  you can remedy this by making an explicit share inside the user's home and giving it 777 permissions.

don't know why you are getting prompted for password even on the shared drive ... i can't imagine why that would be the case (assuming your /shared directory permissions are in order).  try right clicking on "my computer" and select "disconnect network drive" and remove anything that might be listed in there.

as for your username with the space in it.  you shouldn't have any problem adding it to ubuntu via gui.  when you list it in smbconf you should encase it with quotes like so:
```
[user1-share] [COLOR="Red"]< this should not have a space[/COLOR]
path = /home/windows\040username
browseable = yes
read only = no
guest ok = no
valid users = "windows username"
create mask = 0644
directory mask = 0755
force user = samba
force group = samba
```
in the path option, the \040 represents your space, but that only works for directory structure, not for user name.

---

### Post by borahshadow on 2007-05-16
ok that anwseres my questions about the space in the username
I'm not getting prompted for a username on the shared folder I just get an access denied on the subfolders on the unix side because they are created with 644 permissions and they were created with a user different from samba (I just realized that I can just chown them to samba right) to fix that but in the users home directory it belings to the user and their group and they are forced to use the user group samba so it seems that since smaba is a member of all of their groups that it would work fine if I just chmoded the home folder to allow group write access (I don't know why it does not by deafault) and mad the create mask 664 
I do not see how this would break anything I could see changeing the permissions on a /home folder the other way breaking something but allowing more people ti use it I do not see why if you could shed some light on that I would appreaciat that
I also still do not understand why to force them to use the samba user when they access THEIR share I can see on the shared share but theirs?
thanks
ps I must not have been clear this is not happening sorry
> don't know why you are getting prompted for password even on the shared drive ... i can't imagine why that would be the case (assuming your /shared directory permissions are in order). try right clicking on "my computer" and select "disconnect network drive" and remove anything that might be listed in there.
I just don't have the correct access rights on that share as I explained above
pps do you think I set up the samba user correctly?

---

### Post by borahshadow on 2007-05-16
Update ok I didn't have time to do tons of testing this morning but just now I did some more tests
I logged on to my windows vm(that has my account) and mapped the drive that is fine just like it was
I then went to my linux desktop and tried to access it I could access the shared folder but when I tried to access my share it prompted me for a user name and password I put it in but it didn't accept it I tried a few more times still no good I tried with my user name capitalized nope I tried it with the user name guest both capitalized and not nope i even tried it with the user samba nope
I tried logging on to my dad's share (I know his password :))(He does not care though) and I think the same thing I did not try as many combinations but it seemed to act the same way
I tried it with my sisters share and my moms wait they worked???:confused: 
I also noticed because my sister and my mom have the same temporary password I didn't have to relogon to access both shares
I don't have access to windows accounts with their user names so I can't test whether they can map or not but they are set up in about the same fashion as mine so there shouldn't be a problem

question what is the routine for changing a password this is not pressing at the moment getting the base of the server is more important but I will need to know will they have to change their smaba password and then change their unix password or what is the deal with the unix password sync thing again we can cross this bridge when we come to it but I thought I'd throw it out their anyway

are the usernames case sensitive? does it matter if the windows user account is User and the linux is user?

I don't want to start messing with permissions until my questions in my last post get answered

But I still can't figure out why I have to force myself to use the samba group I would kinda like to own the things that I put in my home folder from a remote location
thanks

---

### Post by borahshadow on 2007-05-17
I just noticed there is an update for samba and related things samba smbclient swat winbind etc it is something like from 3.0.22ubuntu4.1 to 3.0.22ubuntu4.2 should I upgrade or not I just thought I would ask before I did

---

### Post by borahshadow on 2007-05-17
I apoligise for posting so many times in a row
dmizer must be busy with some other things right now and my dad is kinda getting anxious for my to get this done and I am ready to be finished setting this up 

does any body else know much about permissions and stuff I have a hard time believing that nobody else could answer some of my questions about permissions someone out there must be good with that kind of stuff

again sorry for posting so many times in a row but I thought I'd post rather to edit for the purpose of bumping

also I've been looking around at some different tutorials and most of them don't use a force user thing at all just thought I'd mention that

---

### Post by dmizer on 2007-05-17
i've been both busy (windows update dos doom at the office :( ), and engaged in attempting to figure out how to address your problem.

i think i may have it here but i haven't tested it:
```
[homes]
   comment = Home Directory for %S
   path = /home/%u
   force user = %u
   create mode = 0600
   directory mode = 0755
   browseable = no
   writable = yes
   valid users = %u
   veto files = /*.{*}/.*/mail/bin/
```
i wanted to test this before i sent it to you, but i'm not sure i'll have time today.

try replacing your smb.conf like so:
```
[global]
    ; General server settings
    netbios name = SERVER-HOME
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[homes]
   comment = Home Directory for %S
   path = /home/%u
   force user = %u
   create mode = 0600
   directory mode = 0755
   browseable = no
   writable = yes
   valid users = %u
   veto files = /*.{*}/.*/mail/bin/

[shared]
    path = /shared
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = samba
    force group = samba
```

permissions are tricky because of the difference in how linux and windows handle file permissions.  you may indeed have problems with your samba user account ... can you log in as samba and perform sudo?

as for the update, i've performed it on all my clients but none of my servers yet because i'm not sure how it will effect the server side yet (cf above windows update dos doom).

---

### Post by borahshadow on 2007-05-17
> and engaged in attempting to figure out how to address your problem.
oh thank you very much sorry if I sounded impatient
before I try that I wanted to ask a few questions and make a few comments 
I don't mind if other people see a folder that they can't access (ie an other user's share ) so if they can see a folder named user-2 but can't open it that is not a problem
with that said it is also not a problem for them to not see unaccessible folders (duh)
I had experimented with the [homes] thing but I'm not positive if that is what I want/need
I noticed that you have it as not browseable that means to access it one must type in the actual part \\server\user right?
I still noticed that the create mode was set lower than 664 or aprox.
I noticed the veto files I think this is the answer to my question about the files with a . being hidden
and I noticed that it is share mode I thing this is good but how does that play with the [homes] how does it know what home folder to show (I think this goes back to the having to type in the path right?)

I backed up my smb.conf and I'm about to try this anyway but I thought I say what my first thought were

I did su samba and performed a command that needs root access and got a permission denied then i added sudo it worked so I think samba is setup correctly

I also wonderd what if I just removed the force user and group completely from the user shared on my current/ working smb.conf (by working I mean - the permission problems I've been having

UPDATE:
I just tried that smb.conf and I had the same permission problems with my shared folder (I have not chmoded it to 777 yet but that should fix it I was waiting until I got some more info on permissions)
and I can see a folder named with my username when I browse to the server but I can't logon it won't accept my password (again it has guest grayed out in the username box)
and when I try to map it so I can force it to use the correct username it won't accept it either

I think my old smb.conf will actually work if I just change the permissions and possibly remove/change the force user/group
this is what I was thinking chmod everything currently in my shared folder to 777
change the create mask to at least 644 mabey 666 or 777 (I'm not an expert on what these numbers mean so I might be off a little)

then change the create mask on the usershares([homes]) to at least 644 and chmod the home folder /home/*** to allow the group to write as well as read

one question I have though is how can I ensure that all files that are put in the /shared folder or in the users home folder have the correct permissions? (when they are using the maching localy(or vnc)
when accessed through samba that is done with the create mask but what about when things are done locally
thanks

---

### Post by dmizer on 2007-05-18
okay here goes:
1) the create mode and directory mode as well as the create mask and directory mask don't have much to do with what permissions the files end up with.  they (as i've indicated before) merely negotiate for the correct permissions levels to allow windows and linux to talk to one another.

2) you can probably safely remove the force user/force group.  this option is in place to allow for servers with users who do not have any command access, but since your samba users all have home directories, you should be okay.  doesn't make any difference either way.  think of it this way.  if you logged in as samba and created a file and put it in your home shared directory,  you could log off samba and log in as yourself and still have access to the file as long as it wasn't created with sudo.

3) do NOT under any circumstances ... chmod the permissions of your home directory.  you will render it useless.  leave them just as they are.

4) yes, you must chmod everything in your /shared folder to 777, as i indicated a couple of days ago.

5) the "." is not a hidden file in windows.  so, the only way for you to prvent your windows box from seeing them, is to veto them from being sent in the first place.

let's add one more option to your homes like so:
```
[homes]
   comment = Home Directory for %S
   path = /home/%u
   force user = %u
   create mode = 0600
   directory mode = 0755
   browseable = no
   [COLOR="Red"]read only = no[/COLOR]
   writable = yes
   valid users = %u
   veto files = /*.{*}/.*/mail/bin/
```

---

### Post by borahshadow on 2007-05-18
> 1) the create mode and directory mode as well as the create mask and directory mask don't have much to do with what permissions the files end up with. they (as i've indicated before) merely negotiate for the correct permissions levels to allow windows and linux to talk to one another.
ok i'll leave them as you have them
> 
2) you can probably safely remove the force user/force group. this option is in place to allow for servers with users who do not have any command access, but since your samba users all have home directories, you should be okay. doesn't make any difference either way. think of it this way. if you logged in as samba and created a file and put it in your home shared directory, you could log off samba and log in as yourself and still have access to the file as long as it wasn't created with sudo
Well now i'm not sure what to do here i'll leave it on the shared share for now
> 3) do NOT under any circumstances ... chmod the permissions of your home directory. you will render it useless. leave them just as they are.]
ok that is why I waited but hypothetically thinking what would I have to do to fix a home dir if I did mess the permissions up? would I have to recreate the account?
> yes, you must chmod everything in your /shared folder to 777, as i indicated a couple of days ago.
ok I did this but how do I make sure that everything that is put inside that folder from here on out will be created with 777?
> 5) the "." is not a hidden file in windows. so, the only way for you to prvent your windows box from seeing them, is to veto them from being sent in the first place.

that is what I thought I just was not sure if that is what veto did

I added that line to the homes share but it still won't let me log on to the homes share

and the shared folder seems to be working correctly
the only weird thing is when I make a file from my windows box in the share it makes owner and group samba that is normal but the permissions are that ownly the owner can write to it but I can still edit the file even though I'm not owner:confused: but it works so I guess whatever I just don't want to run into a problem down the road

Oh I just changed the variables %u to %U (I looked in the man pages :)) and it didn't work but then I chnaged it to %S and it worked it let me in
and I seem to have the correct privileges too this might have fixed it :guitar:
 I'll do some more testing later I got to go for now though

---

### Post by borahshadow on 2007-05-18
ok I have done some more testing with both good and bad news
on my vm with my account everything seems to work perfectly (as for how it is configured) I can logon and see a folder named with my username I click on it and it brings up a prompt and I seem to have perfect access rights to it too I also can map the drive
The shared folder also seems to work perfectly

However when I go into konqueror and browse to smb://192.168.0.50/myshare it will prompt me for a username and password and when I enter my username and password it will not accept it (I tried this with my windows vm connected and without it connected) I tried the account user name guest, nope. and I noticed sometimes my windows tried to connect with 192.168.0.50/username so I tried that too nothing worked I cannot get it to accept my information this is from Linux to Linux
the shared share does seem to work fine under Linux however

But now things get more interesting if I try to access a different usrs's share like \\192.168.0.50\user3 it says it does not exist (this happens on user 3 and user 4 (no particular order) user3 has a space in the name I have tied with the/040 or whatever and that does not work and user4 I have no Idea why it can't find it
user2 however it finds but won't accept a password just like my share behaves from linux I do have access to a windows account with user2's user name and have tried it from that 
I have also tried their users from Linux with the same results

so to try to restate what I just said
myuser
>windows
>>mapping >good
>>permissions >good
>>shows up in my network places >yes
>Linux
>>won't accept authentication info
user2
>windows
>>won't accept authentication info
>> shows up in my network places> no but can manually type it in
>Linux
>> won't accept authentication info
user3 (has space)
>windows (no account available so mapping with a different user name option)
>>does not exist
>> shows up in my network places> no but can manually type it in but still does not exist
>Linux
>> does not exist
>> shows up in my network places> no but can manually type it in but still does not exist
user4
>windows (no account available so mapping with a different user name option)
>> doesn't exist
>Linux
>> does not exist
shared
>windows
>>seems to work fine
>Linux
>>seems to work fine
and actually from user2's windows account I was able to map my drive with the different user name option

and I am curious why the 600 permissions they used to be 644 which I think I am fine with but I don't understand why 644 even the default is 744

I think I need to have at least 664 permissions on the shared folder because from the windows side I can make a file and then it belongs to samba and samba group but I cannot write to it from the Linux side because even though I am a member of the samba group the group does not have write access I don't see anything wrong with the shared folder having 777 create mode please explain why not that is the only problem I can see with the shared folder

I really don't care about the fancy homes thing if it will cause problems with things not existing and it probably won't like the space in the user name I can go back to just defining every users share but I need to know why it won't accept my authentication info from the Linux side and why it won't accept user2's from anywhere 
I can't test user3 and user4 but I suspect that they would be the same

hope you understand what I said it is kinda confusing but I tried to make it comprehend able and thanks again for all your help

---

### Post by borahshadow on 2007-05-19
Well I just got word from my dad (the guy in control) that he has decided that he does not even want private shares on this server anymore (he said that anything that can't be trusted to the rest of the family should just be on their personal hard drive)so that solved 90% of my questions yay
but as for the permissions on the shared folder what is wrong with this
> [shared]
    path = /shared
    browseable = yes
    read only = no
    guest ok = yes
    create mask = **0777**
    directory mask = **0777**
    force user = samba
    force group = samba

also I was talking to my friend who is really good with linux that I get help from often and I asked him if there was a way to make it so that any files that were put into the share locally had the correct permissions and he didn;t know of any
what I want is to have it so that when a user vncs in or when they are sitting at the computer using it as a workstation if they put a file in the shared directory that it will have the correct permissions (777)

He however did suggest this,  It is not very pretty but I think I will have to make it work
just mount the share on the machine locally. 
I know I'll have to take a performance hit but how much would that be?
also If I was transfering something large (iso, vmware image, huge folder of files, etc) I could make sure to just change the permissions when I was done but for everyday use (and use by my mom for example) Just mount the shared folder somewhere so that samba takes care of the permissions

would there be a problem with putting it in fstab would it try to mount it before smaba started?

and about wins I think I'm ready to tackle it now 
I currently have to type in an ip address to get to the server wins would fix that right?
edit: actually I don't anymore don't know why it started working but it seems to

I would like to know about printers though I shared my printer but what is the deal with the printers database thing I think I would like to use that
I went ahead and just set up the shared folder with the permissions above and seems to be working great 777 might be a little more than I need but I don't see a problem with it
thanks

---

### Post by dmizer on 2007-05-20
not sure why you are insisting on changing the create/directory mask numbers.  were the file permissions incorrect when using your server with the numbers i gave you?  either way ... if it's working to satisfaction i suppose it's a moot point anyway.

as for printers, i suggest you share them through cups rather than samba, it's lightyears easier.

on your ubuntu machine, add your main account to the lpadmin group like so:
```
sudo adduser cupsys shadow
sudo adduser <yourusername> lpadmin
sudo sudo /etc/init.d/cupsys restart
```

now you can configure your printer by browsing to [http://localhost:631](http://localhost:631)

once you have listed your printer as shared, you can add it to your windows machine with the following url (adapted to your environment of course)
[http://servername:631/printers/printername](http://servername:631/printers/printername)

+++++++++++++++++++++++++++++

as you've already noticed, netbios names should work properly at this point as long as there is a windows computer connected to the network, AND if your network is dhcp.  if you want hostname resolution to work even if there is not a windows computer connected to the network, you will have to use static ip, and take a look at this guide:

[http://ubuntuforums.org/showthread.php?t=391601](http://ubuntuforums.org/showthread.php?t=391601)

---

### Post by borahshadow on 2007-05-20
I keep changing the permissions because that way the files can be accessed from the server locally (vnc) but I think I'm going to have to use the ugly workaround I mentioned in my post above so that the permissions are always correct and in that case I guess it does not matter as much
Thanks for the tip on sharing with CUPS I'll look at it it looks easier 

as for local access the the shared folder I would prefer not to mount the samba share as I'll take a performance hit (anybody care to shed some light on how much) and have to worry about mounting it which is a pain ,but since everything is the shared folder is suppose to belong to samba or have 777 permissions the only way I can think to change that would be to force all files to go through samba or manually change every file when you put it in the shared folder
any tips on this would be great

if everything had 777 permissions I would not need the force user would I?
likewise if everything ALWAYS accessed the folder through samba and was forced to use the same user I guess 600 would work for permissions correct?

I just don't want to run into problems not being able to access files because of permissions is why I keep wanting to have high permissions

There should always be a win box connected to the network so I'll leave wins alone
If I was to ever covert my family fully to linux I can change it later (not likely because my dad has lots of proprietary programs he needs for his work and several websites he accesses daily that need IE)

Thanks for all your help I've probably been a pain but I appreciate all your help
the only thing I really don't know about is in paragraph 2

---

### Post by borahshadow on 2007-06-06
Ok well I have been running this for a few weeks now and have a few problems
I havenot noticed this from windows (I RARELY use windows just the rest of my family does) but when I mount the shared share ether locally or from one of my ubuntu boxes I have some strange behavior detailed below

I mount with this command  sudo mount -t cifs //192.168.0.50/shared /media/shared -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 (from dmizers cifs tutorial)

scenario 1 try to copy a folder over through konqueror say ~/pictures to /media/shared/pictures
konqueror will bring up a box that says can't change permissions on file XYZ and if I click ok it will bring it up for the next file too but if I leave it up  it will suppress all the other files saying that. The files copy and if I go look on the server they seem to have the correct permissions so why the seemingly pointless error?

scenerio2 a program trying to create folders and files on the mounted share (ie. kaudiocreator)
ok I was ripping a bunch of cd's to the server and had this problem kaudiocreator was configured to make a folder for the artist and then a folder for the album and then put the ripped tracks in there.
ok well the first track would rip and then the encoder would throw up and error that it could not create the folder but the artist folder would be created.  Then the second track would throw up an error about the album folder then all tracks after that would work fine because even though it thought it couldn't create the folder it did.
I would either manually create the folders or just do the first 2 tracks over again to work around this one

scenerio3 rsync
ok I was actually using grsync which is just a gui for rsync so that should not effect this
when copying things over to the server I get output similar to this
> rsync: failed to set times on "/media/shared/pictures/.": Operation not permitted (1)
rsync: failed to set times on "/media/shared/pictures/Home and Family/Family/Cody": Operation not permitted (1)
rsync: failed to set times on "/media/shared/pictures/.": Operation not permitted (1)
rsync: failed to set times on "/media/shared/pictures/Home and Family/Family/Cody": Operation not permitted (1)
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]

I think the times is similar to the permissions thing from konqueror

scenerio4 Firefox
I have Firefox set to ask me where to save things if I select someplace on the server it will give me an error about permission denied and it creates a file.extension.part and then if I try again it works but the .part file is still there but now here is the really weird thing the file shows up with a padlock on it and I can't access the file I just downloaded but if I go over to the server it has all the correct permissions and I can do things like extract archives 
and then after a reboot of the remote machine I can see things correctly (probably just after an unmount and remount but I have not tried that) just a refresh does not work

Please help because these are getting really annoying and some (like the Firefox one) are really inconvenient.

---

