---
title: "Help connecting to samba"
date: 2011-02-19
forum: Server Platforms
---

### Post by rodney757 on 2011-02-19
I am in the process of setting up a home server. I am using the woodel how-to to help me set up the server. I am not following that guide exactly as I have no need for ftp and some other things right now.

I am having trouble accessing my samba server. When I try to access the samba server I get a message saying that there was an error accessing the server. I can ssh and use webmin to access it so it has to be something with the way samba is configured.

I just tried connecting from a windows computer and when I diagnosed the problem it says that the remote device won't accept the connection.

Any help would be great. Thanks

---

### Post by Morbius1 on 2011-02-19
I usually try to stay away from the Server section of the forum but what would be helpful is the output of the following command:
```
testparm -s
```
It will show folks how your samba server is set up.

---

### Post by cariboo on 2011-02-19
I'd suggest using smbtree to see if the shares actually available:

```
smbtree
```

The above command can be run on any system running a Linux variant on your internal network. this is what the output looks like on my system:

```
smbtree
Enter cariboo's password: 
APLUS
	\\WILLY          		willy server (Samba, Ubuntu)
		\\WILLY\IPC$           	IPC Service (willy server (Samba, Ubuntu))
		\\WILLY\siet           	Mom's directory
		\\WILLY\john           	Dad's directory
		\\WILLY\TV2            	TV shows part 2
		\\WILLY\TV1            	TV shows part 1
		\\WILLY\Images         	iso images
		\\WILLY\Iso            	Mounted iso's
		\\WILLY\Stuff          	Everything Else
		\\WILLY\Documents      	Documents
		\\WILLY\Music          	Music
		\\WILLY\Movies         	Ripped DVDs
		\\WILLY\print$         	Printer Drivers	
```

---

### Post by TechSupportx86 on 2011-02-20
Try this guide:

[http://www.jonathanmoeller.com/screed/?p=2143](http://www.jonathanmoeller.com/screed/?p=2143)

Helped alot switching from 9.10 to 10.10, and is overall a very good guide (well for me it was, got me running)

---

### Post by rodney757 on 2011-02-20
The out put from ```
testparm -s
``` is 

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[rj]"
Unknown parameter encountered: "revalidate"
Ignoring unknown parameter "revalidate"
Processing section "[family]"
Processing section "[media]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = HOME.NETWORK
	server string = %h server (Samba, Ubuntu)
	interfaces = eth0
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	read only = No
	hosts allow = 127.0.0.1, 192.168.1.0/254
	sync always = Yes
	delete readonly = Yes

[rj]
	path = /home/rj
	invalid users = family, @family
	valid users = rj, @rj
	create mask = 0700
	directory mask = 0700

[family]
	path = /home/family
	create mask = 0775
	directory mask = 0775

[media]
	path = /home/media
	create mask = 0775
	directory mask = 0775


```

When I run smbtree I don't get anything. When I run it as root it comes back saying: 

```
Unable to create directory /var/run/samba for file gencache.tdb. Error was no such file or directory.
```

I'll take a look at that guide. thanks for the help

---

### Post by Morbius1 on 2011-02-21
Start the following services in this order:
```
sudo service smbd start
``````
sudo service nmbd start
```You may get a "start: Job is already running: xxxx". If that happens to both smbd and nmbd then my guess is incorrect. If either service now starts wait 5 minutes ( seriously - 5 minutes ) then run smbtree again.

---

### Post by rodney757 on 2011-02-21
It said that both those services were already running.

I tried smbtree from my linux laptop and I get the unable to creat directory thaat I posted earlier.

I ran the smbtree command on the server and it said that I needed to install  smbclient. I installed smbclient and ran the command again. This is what it came back with:
```
smbtree
Enter rj's password: 
failed negprot: NT_STATUS_INVALID_NETWORK_RESPONSE
failed negprot: NT_STATUS_INVALID_NETWORK_RESPONSE

``` 

Thanks

---

### Post by Morbius1 on 2011-02-21
> hosts allow = 127.0.0.1, [COLOR=Blue]192.168.1.0/254[/COLOR]I do believe that that is an invalid netmask. Try this instead:
> hosts allow = 127.0.0.1, [COLOR=Blue]192.168.1.0/24[/COLOR]Then restart samba:
```
sudo service smbd restart
sudo service nmbd restart
```

---

### Post by rodney757 on 2011-02-21
That was the problem. I thought that I needed to put 192.168.1.0/254 because my router assigns ip's that high? 

Thanks for the help.

---

### Post by Morbius1 on 2011-02-21
No problem - it was an interesting brain teaser.

Actually the "24" is shorthand so 192.168.1.0/24 will give you a range of ip addresses from 192.168.1.1 - 192.168.1.254 which is what you wanted in the first place.

---

