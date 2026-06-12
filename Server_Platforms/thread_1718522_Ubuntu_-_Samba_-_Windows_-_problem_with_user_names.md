---
title: "Ubuntu - Samba - Windows - problem with user names"
date: 2011-03-31
forum: Server Platforms
---

### Post by Grafcom on 2011-03-31
Hello,
 
my first time here... 
 
I do not know if this is the right place for this post because I do not use the server edition.
 
I have a peer to peer network set up with Ubuntu desktop (10.04), Samba (version 3.5.8 ) and 3 Windows XP computers.
 
Everything works fine but I have one problem.
 
The Windows computers are 1 XP Pro and 2 XP Home editions.
 
In one of the Home editions the (real) User Account Name has a space in the name. In Windows XP Home Edition, you cannot change the actual name of a user account, only the name that is displayed on the Welcome screen.
 
So, in Ubuntu I can not create a (Linux) user with a space in the name (why not, this is not a Linux limitation is it?)
 
The Windows user is therefore not recognized. On that computer the user must always manually enter other information than his actual credentials. This is not convenient.
 
Reinstalling the Windows computer is not a real option.
 
Is there a way to get it working with the credentials of the computer?
 
Thanks for your comments.
 
Grafcom (from the Netherlands)

---

### Post by Morbius1 on 2011-03-31
Give this a shot:

Let's say the Windows users name is "bart simpson"

Create a local username on the Linux server as "bart"

Edit /etc/samba/smbusers as root and add the following line:
```
bart = "bart simpson"
```That will map the Windows name to the Unix name.

Then restart samba:
```
sudo service smbd restart
```And make sure bart is added to the samba database:
```
sudo smbpasswd -a bart
```

---

### Post by Grafcom on 2011-03-31
@Morbius1,
 
Unfortunately, that does not work.
 
With the request for a username and password I can login with "Bart" and password.
 
But it does not pick up the data of the logged in user.

---

### Post by Morbius1 on 2011-03-31
> **Grafcom said:**
> But it does not pick up the data of the logged in user.
Please explain that comment.

---

### Post by Grafcom on 2011-03-31
I mean, when on the other computers users logging in with their username and password they have immediate access to the Linux computer and share. 
 
This is because their "usernames" and passwords appear in the Linux computer, and that is picked up well
 
sorry for my bad English.....
 
Example that works:
 
Linux user has the name computer1 - the real user account on computer1 is "user1" (no spaces) the password for user1 is password1
 
in /etc/samba/smbusers there is "computer1 = password1"
 
The example that does not work:
 
Linux user has the name computer2 the real user account on computer2 is "user 2" (with a space) the password for user2 is password2
 
in /etc/samba/smbusers there is "computer2 = password2"
 
As you can see the real user account names are not stored in Linux but they do play a role...

---

### Post by Morbius1 on 2011-03-31
I don't see how the "example that works" would ever work since /etc/samba/smbusers contains no passwords but let's focus on the example that does not work:

Windows username = user 2
Windows password = password2

What I'm suggesting is create a local user on the Linux machine with:
Linux username = user2
Linux password = password2

Then add a line to /etc/samba/smbusers:
```
user2 = "user 2"
```Make sure there is a line in /etc/samba/smb.conf that looks like this:
```
username map = /etc/samba/smbusers
```If not add it and restart samba:
```
sudo service smbd restart
```Then add a samba password to the database:
```
sudo smbpasswd -a user2 
```It will first ask for root's password then it will ask for user2's password. Give it: password2

The Windows machine will pass username = user 2 and password = password2 and Linux will convert user 2 to user2 and use password2 to authenticate.

Are we saying the same thing?

---

### Post by Grafcom on 2011-03-31
First, in the /etc/samba/smbusers there are no passwords, they are in /etc/passwd I think.
 
I tried your suggestion but no luck.
 
The Linux username can be anything, the password is the same as on the Windows computer.
 
In Samba you add the Linux username with a Samba password (also the same password as on the Windows computer) and in Samba you **link** to the Windows inlog user account.
 
(This is in the /etc/samba/smbusers)
 
Here is the tricky part.... In Samba you put the Windows inlog user account but that is only the user account displayed on the Welcome screen in Windows that is linked to the "real user account name" on the Windows machine.
 
On the Windows machine the real user account is (example) computer1 The displayed name when you login could be "Bart Simpson". The password could be BartUJK
 
So, in Linux you have user "ME" in Samba "ME" has the password BartUJK and the user account name "Bart Simpson"
 
This works.... and there are no "Windows real user account name" defined in Linux or Samba
 
But when the "real user account name" in Windows has a space..... no, it don't work
 
 
I hope I do make this clearer.

---

### Post by Morbius1 on 2011-03-31
> Linux user has the name computer2 the real user account on computer2 is  "user 2" (with a space) the password for user2 is password2
 
in /etc/samba/smbusers there is "computer2 = password2"
 The above will not work because you don't add passwords to /etc/samba/smbusers.

The line should read:
```
computer2 = "user 2"
```

---

### Post by Grafcom on 2011-04-01
@Morbius1,
 
This is how I did it:
 
I add the Linux User
 
```
computer1
```
 
password
 
```
password1
```
 
Then with the GUI "Samba-Server Configuration" I added
 
```
computer1
```
 
also
 
```
Windows account name = user 1 (with a space)
Samba password = password1
Group = Sambashare
```
 
Then I give the share folder access from computer1
 
When I look in /etc/samba/smbusers there is
 
```
computer1 = user 1
```
 
Samba passwords is stored in smbpasswd, right? 
 
This is a file I can't read, is coded in
 
```
/usr/bin/smbpassw
```
 
Windows computer1 has as owner name (**the real account name**) user1 (without a space) this can not be changed in Windows XP Home version.
 
The user sees the name that is displayed on the Welcome screen, that is also user 1 (but with a space, this can be changed).
 
When the user log in with the password "password1" the Linux computer is accessible.
 
When I change the name in the Welcome screen (user 1) in to "whatever" I must change that to with the "Samba-Server Configuration" for Samba
 
```
Windows account name = whatever 
Samba password = password1
Group = Sambashare
```
 
Everything still work.
 
Now the Computer with the **real account name** "user 2" (with a space) it does not work.
 
The only difference is the **real account name** with a space.
 
 
So yes, I add passwords to the Samba users

---

### Post by Morbius1 on 2011-04-01
Please post the output of the following command:
```
testparm -s
```

---

### Post by Grafcom on 2011-04-01
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Openbaar]"
Loaded services file OK.
Server role: ROLE_STANDALONE
 
[global]
workgroup = WERKGROEP
server string = %h server (Samba, Ubuntu)
map to guest = Bad User
obey pam restrictions = Yes
pam password change = Yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
username map = /etc/samba/smbusers
unix password sync = Yes
syslog = 0
log file = /var/log/samba/log.%m
max log size = 1000
dns proxy = No
usershare allow guests = Yes
panic action = /usr/share/samba/panic-action %d
 
[printers]
comment = All Printers
path = /var/spool/samba
create mask = 0700
printable = Yes
browseable = No
 
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
 
[Openbaar]
comment = Bestanden op Linux computer
path = /home/beheer/Openbaar
valid users = compu2, compu3, compu4
read only = No
create mask = 0777
force create mode = 0777
directory mask = 0777
force directory mode = 0777
&#12288;

```

---

### Post by Morbius1 on 2011-04-01
Since you and I seem to be in an infinite loop on the way you are trying to do this I would like to offer you an alternative:

This is what you have now:
> [Openbaar]
comment = Bestanden op Linux computer
path = /home/beheer/Openbaar
valid users = compu2, compu3, compu4
read only = No
create mask = 0777
force create mode = 0777
directory mask = 0777
force directory mode = 0777It would appear that the all of the "valid users" are in fact everyone else on your home network. By definition that's a guest share and there is no need to authenticate. So change the share definition to this:
> [Openbaar]
comment = Bestanden op Linux computer
path = /home/beheer/Openbaar
**[COLOR=Blue] guest ok = yes[/COLOR]**
read only = No
create mask = 0777
force create mode = 0777
directory mask = 0777
force directory mode = 0777"guest ok" will allow anyone access.

If for some reason you are concerned about security then you can limit where those guests come from by adding another line:
```
allow hosts = list
```[COLOR=Blue]***list***[/COLOR] can be ip addresses:
```
allow hosts = 192.168.0.100, 192.168.0.101, 192.168.0.102
```A range of ip address:
```
allow hosts = 192.168.
```Or host names:
```
allow hosts = hostname1, hostname2, hostname3
```

---

### Post by Grafcom on 2011-04-01
I tried something else.
 
The computer who worked and had access to the Linux computer (compu 1), I removed from Samba.
 
Now I no longer have access to the shared folder on the Linux computer and I'm asked for credentials.
 
Oké, I give as username compu 2 (with a space) and the right password.... No luck.
 
The "real account name" of the other computer now plays no role, right?
 
So, I changed the Windows username in Samba to compu**_**2 and... yes, I have access... on compu 1... Huh?
 
On this computer it works originally with the Windows username compu 1, yes with a space
 
Now I changed the (user) inlog name on the other computer to compu**_**2 and restart it.
 
The login name is now compu**_**2 and I used the password, oké I am now logged in this Windows computer 2.
 
Go to the Linux share and.... no.... no access....a few clicks and the credentials screen appeared.
 
No I typed compu_2 and the password and.... yes, I have access... Huh Huh?
 
Now I am completely lost....
 
But I will now try your alternative, thanks

---

### Post by Morbius1 on 2011-04-01
Just make sure that anytime you edit smb.conf directly you need to restart samba:
```
sudo service smbd restart
```
And make sure the target Linux permissions are in sync with allowing guests to access:
```
sudo chmod 0777 /home/beheer/Openbaar
```

---

### Post by Grafcom on 2011-04-01
@Morbius1,
 
the alternative you suggested works.
 
Also limiting the IP addresses works.
 
**[COLOR=red]Thank you very much !![/COLOR]**
**[COLOR=#ff0000][/COLOR]** 
Still strange that the other did not work, but I can live with this.

---

