---
title: "Adding a proftpd user to /var/www"
date: 2011-09-07
forum: Server Platforms
---

### Post by Heeter on 2011-09-07
Hi all,

What is the command line for adding a user with password to access the /var/www folder through Filezilla?

I presently have proftpd + TLS installed on Ubuntu 11.04 Server (32bit)

I can disable TLS if need be. When I log in I do see the certificate I created, but cannot get past that.

I also opened ports 20 & 21 on the firewall.

This is the error I am getting:
```

Status:	Resolving address of hcctech.ca
Status:	Connecting to 108.21.187.192:21...
Status:	Connection established, waiting for welcome message...
Response:	220 FTP Server ready.
Command:	AUTH TLS
Response:	234 AUTH TLS successful
Status:	Initializing TLS...
Status:	Verifying certificate...
Command:	USER userftp
Status:	TLS/SSL connection established.
Response:	331 Password required for userftp
Command:	PASS ***********
Response:	530 Login incorrect.
Error:	Critical error
Error:	Could not connect to server

```

I did try to create a user (userftp) by following one of the how-to's, but it isn't helping.

I really would like full direct access directly to my web folders.

Thanks

Heeter

---

### Post by DavidBeijer on 2011-09-07
First of all take a good look at your ftp session: its error is in the authentication of the user. I see you try to log in using the "userftp" username. I'm not a pro in Linux (installed my first server a couple of days ago, my main PC is still Windows), but as far as I understand proftpd this is a user for the software to use to get access rights to the physical folders to read and write in, this is not a useraccount for remote users trying to log in to your FTP. 

The explanation given [here]("http://ubuntuforums.org/showthread.php?t=79588") helped me enough to get it working. Did you restart proftpd after having changed the config file? 

Good luck!

PS: Please let me know if any of this helped or what the problem turned out to be. I'm a n00b in this myself, and would like to learn!

---

### Post by Heeter on 2011-09-07
Hi David,

That is exactly the howto I used.

I will take a look at it again.

I would like to have direct access to my /var/www folder, not somewhere in a home folder. The I have to go move it around in the server after that.

Heeter

---

### Post by Heeter on 2011-09-07
Can anyone help, please

Thanks

I followed that howto again,

I am still getting the same error as above.

Thanks 


Heeter

---

### Post by DavidBeijer on 2011-09-08
Heeter,

Changing the home directory is not too difficult. In the guide we both used they tell to set the home directory to /home/FTP-shared/, if you replace that with /var/www/ that should help:

```
sudo useradd userftp -p your_password -d /var/www -s /bin/false
sudo passwd userftp
```

You should then also proceed to change the directory specifications in the /etc/proftpd/proftpd.conf file. I modified one entry from the example in the guide:
```

<Directory /var/www>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

```
The next two entries should be modified similarly, I think you get the idea. 

The error you got in your first post looked like some authentication error. I would try setting the password for userftp to a really simple one and making sure that you've added userftp to the #VALID LOGINS sections of the proftpd.conf file. 

I'm not sure whether you are immediately trying to get the users to login to the /var/www folder, but if so I would recommend to first get it to work exactly as in the example. Then start to change stuff around. This will make finding the problem easier.

Good luck!

---

### Post by Heeter on 2011-09-09
Thanks a million for your help so far.

Following your direction, I have managed to get past the login,

Now I am getting this error:

```

Status:	Resolving address of hcctech.ca
Status:	Connecting to 107.20.185.192:21...
Status:	Connection established, waiting for welcome message...
Response:	220 FTP Server ready.
Command:	USER userftp2
Response:	331 Password required for userftp2
Command:	PASS *******
Response:	230 User userftp2 logged in
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Features:
Response:	 LANG en-US.UTF-8*;en-US
Response:	 MDTM
Response:	 MFMT
Response:	 TVFS
Response:	 AUTH TLS
Response:	 UTF8
Response:	 MFF modify;UNIX.group;UNIX.mode;
Response:	 MLST modify*;perm*;size*;type*;unique*;UNIX.group*;UNIX.mode*;UNIX.owner*;
Response:	 PBSZ
Response:	 PROT
Response:	 SITE MKDIR
Response:	 SITE RMDIR
Response:	 SITE UTIME
Response:	 SITE SYMLINK
Response:	 REST STREAM
Response:	 SIZE
Response:	211 End
Command:	OPTS UTF8 ON
Response:	200 UTF8 set to on
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is the current directory
Command:	TYPE I
Response:	200 Type set to I
Command:	PASV
Response:	227 Entering Passive Mode (10,220,27,45,130,113).
Status:	Server sent passive reply with unroutable address. Using server address instead.
Command:	MLSD
Error:	Connection timed out
Error:	Failed to retrieve directory listing

```

This is what I have in my proftpd.conf file:
```


#VALID LOGINS
<Limit LOGIN>
AllowUser userftp2
AllowUser userftp
DenyALL
</Limit>

<Directory /var/www/>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

<Directory /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
        <Limit READ RMD DELE>
        DenyAll
        </Limit>

        <Limit STOR CWD MKD>
        AllowAll
        </Limit>
</Directory>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>


```

Heeter

---

### Post by Heeter on 2011-09-09
Well,

By changing filezilla client to "Active" from "Default", I now see my /var/www folder. 

Now I cannot upload (or delete) anything into it. I can download, but cannot upload or delete either.

Must be a permissions setting, but where?

I am almost there..............


Heeter

---

### Post by DavidBeijer on 2011-09-10
As far as I can see, your proftpd.conf file (as you posted it two posts ago) is set to deny access rights to the /var/www folder: 

```
<Directory /var/www/>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>
```

The capital arguments in the <limit> tags specify ftp commandos, and these, more specifically the MKD and STOR commandos are set to DenyAll. MKD and STOR are ftp commandos used for MaKing Directories and STORing files respectively, and these are denied to all users. I believe you should be able to write to the file if you remove these commands from the <limit>'s arguments, and add a second set of limit tags to this directory specification in order to allow these commands, something like this:
```

<Limit MKD STOR >
   AllowAll
</Limit>
```

BE CAREFULL: you now give each user write rights, which may be undesirable for you from a security perspective. I would recommend to read the "advanced" section of the guide again or google around to limit these rights to certain users if you wish to set up your server in a secure way.

Hope this helps!

---

### Post by Heeter on 2011-09-10
Thanks a million, for your great assistance,

Not too worried about security, As I am the only one with access to this server.

Here is new updated file:
```

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp2
AllowUser userftp
DenyALL
</Limit>

<Directory /var/www>
Umask 022 022
AllowOverwrite off
        <Limit DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
        <Limit MKD STOR>
        AllowAll
        </Limit>
</Directory>

```

Still not working, same as before.

So I tried this:
```

<Directory /var/www>
Umask 022 022
AllowOverwrite on
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        AllowAll
        </Limit>
</Directory>

```

And Still I cannot upload to the folder

Could it be that the server is simply not allowing At all uploads to the /var/www folder?


Heeter

---

### Post by DavidBeijer on 2011-09-12
Hi,

Have you checked that the ftpuser account has linux write rights on the /var/www folder? Otherwise proftpd will not be able to write to these folders as userftp.

The part about setting user rights is explained in the guide you used before, just before step 3. The code they give there is 
```

cd /home
sudo chmod 755 FTP-shared
cd FTP-shared
sudo chmod 755 download
sudo chmod 777 upload

```
Writing rights are given here to the upload directory, so you should do something similar to your /var/www folder, I suggest you look up some documentation or tutorials on chmod in order to fully understand what's going on.

Good luck!

---

### Post by Heeter on 2011-09-12
Hi David,

Thanks for helping.

I have tried that already.

I have started another thread in the server section because, as far as I can see, It is Ubuntu itself blocking me, because I have no issues with FTP'ing within anywhere in my user's /home folder. Once I am out of the /home folder I am locked down to downloading only.

I have tried chmodding the folders to no avail.

[http://ubuntuforums.org/showthread.php?t=1842715]("http://ubuntuforums.org/showthread.php?t=1842715")

Heeter

---

### Post by tester100 on 2011-10-17
Hi guys

i found this thread and found it usefull, but nevertheless i still have alot of doubts.

So i ask here for help , or direction to a correct link with all the information necessary.

a brief description of my setup here.

I have 1 pc machine, in installed vsftpd , apache2 and others in order to run several webhosts on the same machine

at total 6 websites.


so i have configured all the sites on the 

var/www/

website1 folder
website2 folder
website3 folder
website4 folder
website5 folder
website6 folder

now i need to setup 6 accounts, with specific user+pass , or using just ROOT user + individual passwd for each website folder.

and also i want to giver only especific access rights to the correct website folder for each site.

example on FTP login from user1+passwd1  user would only be able to login to website1 folder in order to upload or chance information in their website.

the same thing also to be done with the other users for the other websites.

so can this be done?

if yes is there a open thread already that someone could point me out? 

Any help at this stage guys is welcomed, as i am completelylost, and i dont feel like giving full access to all the folders in my ubuntu machine  for all users.

kind regards
tester100

---

### Post by DavidBeijer on 2011-10-17
This should be well possible. I do not have experience with that specific setup, but it should work by modifiing these blocks to the right folders:
```

<Directory /var/www>
Umask 022 022
AllowOverwrite on
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        AllowAll
        </Limit>
</Directory>

```

And using the AllowUser directive instead of AllowAll. A source on the AllowUser directive can be found [here]("http://www.proftpd.org/docs/directives/linked/config_ref_AllowUser.html").

If that is not clear enough now you at least have a direction to search for in google. Good luck!

---

### Post by tester100 on 2011-10-17
> **DavidBeijer said:**
> This should be well possible. I do not have experience with that specific setup, but it should work by modifiing these blocks to the right folders:
```

<Directory /var/www>
Umask 022 022
AllowOverwrite on
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        AllowAll
        </Limit>
</Directory>

```And using the AllowUser directive instead of AllowAll. A source on the AllowUser directive can be found [here]("http://www.proftpd.org/docs/directives/linked/config_ref_AllowUser.html").

If that is not clear enough now you at least have a direction to search for in google. Good luck!


Hi 
thanks for input info still lost with it, but will figure it out eventually...

i found another kind of option where i have to add a new user to ubuntu, then in the home folder create a www folder, then on apache setup chroot_enabled=yes, so he can only have access to that folder when he logs in via FTP. aldo... need to find more info on how to setup the hosts file correctly

as now i need to setup 


website1  on  127.0.0.1  website1.com
website2  on  127.0.0.2  website2.com   

just need to know if i can use the same port 80 on all them or if that will cause problems on apache2 after i restart everything.

---

### Post by vendar13 on 2011-10-18
First of all take a good look at your ftp session: its error is in the authentication of the user. I see you try to log in using the "userftp" username. I'm not a pro in Linux (installed my first server a couple of days ago, my main PC is still Windows), but as far as I understand proftpd this is a user for the software to use to get access rights to the physical folders to read and write in, this is not a useraccount for remote users trying to log in to your FTP.

      [Computer   Store](http://www.computervalley.ca/)       [Online   Computer Store](http://www.computervalley.ca/)

---

### Post by vivideo on 2012-10-25
Hi all,

After struggling with the settings to adding a guest user, I would like to share the following code for the proftpd.conf file in my XAMPP-system. My goal was to setup a guest ftp-account and pointing this user to its own directory to exchanging project files. The main account (me, webhoster) exists seperately, so no interference should be possible. 

After adding user 'klant' with [this help]("http://ubuntuforums.org/showthread.php?t=79588"), I got the follwing configuration setting to work. I would like to hear if its secure enough :)

```

# This is a basic ProFTPD configuration file (rename it to 
# 'proftpd.conf' for actual use.  It establishes a single server
# and a single anonymous login.  It assumes that you have a user/group
# "nobody" and "ftp" for normal operation and anon.

ServerName			"ProFTPD"
ServerType			standalone
DefaultServer			on

# Port 21 is the standard FTP port.
Port				21
# Umask 022 is a good standard umask to prevent new dirs and files
# from being group and world writable.
Umask				022

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				nobody
#Group				nogroup

<Limit LOGIN>
AllowUser nobody
AllowUser klant
DenyALL
</Limit>

# Normally, we want files to be overwriteable.
<Directory /opt/lampp/htdocs/*>
  AllowOverwrite		on
</Directory>

# only for the web servers content
DefaultRoot /opt/lampp/htdocs

# nobody gets the password "lampp"
# commented out by lampp security
#UserPassword nobody (removed)
UserPassword nobody (rmoved)

# nobody is no normal user so we have to allow users with no real shell
RequireValidShell off

# nobody may be in /etc/ftpusers so we also have to ignore this file
UseFtpUsers off

<Anonymous ~klant>
Umask 022 022
AnonRequirePassword on
User klant
RequireValidShell off
<Directory /home/FTP-shared/upload/*>
<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
</Anonymous>

```

---

