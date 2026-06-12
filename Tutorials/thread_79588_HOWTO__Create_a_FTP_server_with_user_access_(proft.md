---
title: "HOWTO : Create a FTP server with user access (proftpd)"
date: 2005-10-20
forum: Tutorials
---

### Post by frodon on 2005-10-20
[COLOR="Red"][SIZE="2"]There's some support for this guide in the hoary section[/SIZE]
[SIZE="1"]Some questions are already answered in the [OLD THREAD]("http://www.ubuntuforums.org/showthread.php?t=51611") ,if you need support you should read it before posting here.[/SIZE][/COLOR]

I created this How to for people who want to share files with friends using FTP protocol, like FTPservU under windows. The way i give you is not the only one, I hope my How to is enough clear.
This FTP server will allow only users with the good password (persons to whom you gave the password and username). So you will be sure that only known persons will access your FTP server.

[SIZE=3]**A- The GUI way (_for beginners only_)**[/SIZE]

For those who are new to linux and don't want to use a FTP server without GUI, or just for those who don't use often their FTP server and wish to set it quickly without a high level of security, there is a GTK GUI for proftpd.
Be careful, it's less secure than configuring yourself your server.

**[SIZE=3]1- [/SIZE]** Install proftpd and gproftpd with synaptic or with this command : ```
sudo apt-get install proftpd gproftpd
```[SIZE=3]**2-**[/SIZE]Play with the GUI and set up quickly your server.
Beware no support is offered here for this tool but it shouldn't be too hard to use.


[SIZE="3"]**B- The secure way**[/SIZE]
[B]

[SIZE=3]1- [/SIZE][/B] Install proftpd with synaptic or with this command : ```
sudo apt-get install proftpd
```
**[SIZE=3]2-[/SIZE]** Add this line in /etc/shells file (sudo gedit /etc/shells to open the file) :```
/bin/false
``` Create a /home/FTP-shared directory : ```
cd /home
sudo mkdir FTP-shared
``` Create a user named **userftp** which will be used only for ftp access. This user don't need a valid shell (more secure) therefore select /bin/false shell for **userftp** and /home/FTP-shared as home directory (property button in user and group window).
To make this section clearer, i give you the equivalent command line to create the user,  but it would be better to use the GUI (System > Administration > User & Group) to create the user since users here often got problems with the user creation and the password (530 error) with the command line, so i really advice to use the GUI : ```
sudo useradd userftp -p your_password -d /home/FTP-shared -s /bin/false
sudo passwd userftp
``` In FTP-shared directory create a **download** and an **upload** directory : ```
cd /home/FTP-shared/
sudo mkdir download
sudo mkdir upload
```Now we have to set the good permissions for these directories : ```
cd /home
sudo chmod 755 FTP-shared
cd FTP-shared
sudo chmod 755 download
sudo chmod 777 upload
```
**[SIZE=3]3-[/SIZE]** OK, now go to the proftpd configuration file :  ```
sudo gedit /etc/proftpd.conf
```or for edgy eft (ubuntu 6.10) : ```
sudo gedit /etc/proftpd/proftpd.conf
```
and edit your proftpd.conf file like that if it fit to your need :
```
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias sauron userftp

ServerName			"ChezFrodon"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayChdir                    .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port				1980

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
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
```
Ok you have done proftpd configuration. Your server is on port 1980 (in this exemple) and the access parameters are 
user : sauron
password : the one you've set for **userftp**

**[SIZE=3]4-[/SIZE]** To start/stop/restart your server : ```
sudo /etc/init.d/proftpd start
sudo /etc/init.d/proftpd stop
sudo /etc/init.d/proftpd restart
```To perform a syntax check of your proftpd.conf file : ```
sudo proftpd -td5
```To know who is connected on your server in realtime use "ftptop" command (use "t" caracter to swich to rate display), you can also use the "ftpwho" command.
other informations [here](http://doc.gwos.org/index.php/DapperGuide#How_to_install_FTP_Server_for_File_Transfer_service) 


[SIZE="3"]**C- Advanced tricks**[/SIZE]

**[SIZE=2]1- Enable TLS/SSL encryption (FTPS)[/SIZE]** 
[COLOR="DarkOrange"]** Inportant note : proftpd versions before 1.3.2-rc2 may not work with latest filezilla versions using TLS encryption. [URL="http://ubuntuforums.org/showpost.php?p=8239887&postcount=1081"]See raymond.szebin's post for details.
[/URL][/COLOR]
The FTP file sharing protocol is an old protocol which was created when internet was still a secure place, therefore the default FTP protocol is not that secure.
For example the password and username for login are transmitted in plain text which obviously isn't secure.
That why, to fit the needs of our generation, encryption solutions were developed and one of them is TLS/SSH encryption.
This will encrypt the username and password and all the data you send, obviously to use it the FTP client must support SFTP protocol.

here are the steps to enable TLS/SSH encryption ([FTPS]("http://en.wikipedia.org/wiki/FTPS")):

Paste these commands in a terminal :```
sudo apt-get install build-essential
sudo apt-get install libssl-dev
cd /etc
sudo mkdir ftpcert
cd ftpcert/
sudo openssl genrsa -des3 -out server.key 1024
sudo openssl req -new -key server.key -out server.csr
sudo openssl genrsa -des3 -out ca.key 1024
sudo openssl req -new -x509 -days 365 -key ca.key -out ca.crt 
** download the sign.sh file (at the bottom of the post) and put it in ftpcert directory **
sudo chmod +x sign.sh
sudo ./sign.sh server.csr 
```

Then add this section to yout proftpd.conf file : ```
<IfModule mod_tls.c>
    TLSEngine on
    TLSLog /var/ftpd/tls.log
    TLSProtocol TLSv1

    # Are clients required to use FTP over TLS when talking to this server?
    TLSRequired off

    # Server's certificate
    TLSRSACertificateFile /etc/ftpcert/server.crt
    TLSRSACertificateKeyFile /etc/ftpcert/server.key

    # CA the server trusts
    TLSCACertificateFile /etc/ftpcert/ca.crt

    # Authenticate clients that want to use FTP over TLS?
    TLSVerifyClient off
</IfModule>

```

If you use edgy or proftpd 1.3 in general add this line at the beginning of your proftpd.conf file, it will load all the extra modules like mod_tls.c :
```
Include /etc/proftpd/modules.conf
```

Note - Use TLSRequired ON to force the use of TLS. OFF means that the use of TLS is optional.

Optional step:
You will notice that you will be asked for the password you set for the server.key file each time you start/stop/restart the server, it is because the RSA private key is encrypted in the server.key file.
The solution is to remove the encryption of the RSA private key but it makes the key readable in the server.key file which is obviously less secure, anyway if you do that **make sure that the server.key is readable only by root**.
Once you know that it's less secure here are the command lines to remove the encryption of the RSA private key : ```
cd /etc/ftpcert
cp server.key server.key.org
openssl rsa -in server.key.org -out server.key

```
Here are some links to read in case of problems or just to get more informations :
[http://www.modssl.org/docs/2.7/ssl_faq.html#cert-ownca](http://www.modssl.org/docs/2.7/ssl_faq.html#cert-ownca)
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html)

To use your TLS encrypted FTP server you will need a FTP client which support it like the latest versions of filezilla (the one present in the feisty repository has the TLS support).
In filezilla the option to use is called FTPES.

Thanks to **nix4me** for the help he provided and for the instructions.

**[SIZE=2]2- Restrict access for some users[/SIZE]** 
Some of you wish, for different reasons, to create more than one user and give a different access depending on the user.
For example if i create 2 users, one called user1 and the second called user2 and then want to deny access to the download directory for user2, You can do it as following :

First create the 2 users like userftp in the guide and give them alias names if you use aliases. Then allow your 2 users in the general LIMIT LOGIN section :```
#VALID LOGINS
<Limit LOGIN>
AllowUser user1
AllowUser user2
DenyALL
</Limit>
```Once done here is how to modify the directory sections to chose who is able to use which directory :```
<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off

        [B]<Limit ALL>
		Order Allow,Deny
		AllowUser user1
		Deny ALL
	</Limit>[/B]

	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on

       [B]<Limit ALL>
		Order Allow,Deny
		AllowUser user1
                AllowUser user2
		Deny ALL
	</Limit>[/B]

	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
```Note - user2 will see the download directory but will not be able to enter the directory.

That's all


[SIZE=6]**Misc**[/SIZE]
[SIZE=3]**_Best Common Practices - Everyone should read this_**[/SIZE]
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-BCP.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-BCP.html)

[SIZE=3]**_ProftpTools 1.0.1_**[/SIZE]
ProftpTools is a script I wrote thanks to swoop's feedback. This script allow you to start/stop proftpd, mount/unmount auto/manually directories, show your IP, ... and all of that with a **GUI** in order to use proftpd in a really easy way !
To install ProftpTools, download ProftpTools-v1.0.2.tar.gz (at the bottom of the page) and untar it where you want and then move the ProftpTools file in /usr/bin : ```
tar -xzvf ProftpTools-v1.0.2.tar.gz
cd ProftpTools-v1.0.2/
sudo mv ProftpTools /usr/bin/
```Then add these lines in your **.bashrc** (it's in your home directory : gedit /home/username/.bashrc) file in order to specify what is the ProftpTools directory path, YOU MUST REMOVE THE "/" CHARACTER at the end of the path. I give you an exemple if your ProftpTools directory is in your home directory : ```
ProftpTools_dir=/home/username/ProftpTools-v1.0.2
export ProftpTools_dir
```Now all you have to do is to type **ProftpTools** in a terminal and  .... enjoy  :smile: 
You need **zenity** installed to use this script.

Don't hesitate to post in this thread or send me PM to report bugs, ask new features, correct my english, suggest improvement  ;-)  and thank you to give me feedback about this tool.

[SIZE=3]_**useful trick**_[/SIZE] :
This trick is integrated in ProftpTools.
If you don't want (like me  ;-) ) to use space in your /home directory, and use space on another hard drive, or if you just want to share a directory from another partition ...   you can mount the directory you want in your **download** or **upload** directory without changing anything in proftpd.conf file, use these commands : ```
sudo mount -o bind the_directory_you_want_to_share /home/FTP-shared/download
or
sudo mount -o bind the_directory_you_want_to_use_for_upload /home/FTP-shared/upload
```This command **will not** overwrite the directory, the idea is just to mount a directory in another one without overwritng anything, so when someone will log in your server he will see and use the mounted directory if you have mounted one. To unmout a directory (download directory for exemple): ```
sudo umount /home/FTP-shared/download
```**Permanent mount :** 
If you don't want to re-mount your directories after a reboot you can add a line in fstab file like that (sudo gedit /etc/fstab to open the file) : ```
the_directory_to_mount /home/FTP-shared/download vfat bind 0 0
```thanks **reet**  ;-) 

If you want to create other directories in **FTP-shared**, think to add it in proftpd.conf file.
Don't hesitate to test yourself your server using gFTP for exemple, it's really helpful to debug your server.

[SIZE=3]_**Other stuff/Troubleshooting/FAQ**_[/SIZE]
**If you have a router** you should read [that](http://www.proftpd.org/localsite/Userguide/linked/x862.html), it describe the 2 commands to add in proftpd.conf and why. 
If you have a dynamic DNS have a look [here](http://doc.gwos.org/index.php/DapperGuide#How_to_assign_Hostname_to_local_machine_with_dynamic_IP_using_free_DynDNS_service), you can also use [ddclient](http://linux.cudeso.be/linuxdoc/ddclient.php)(maybe easier for newbies).  
If you have ***Unbindable port 21*** issue please refer [to this post]("http://ubuntuforums.org/showthread.php?t=79588&page=114") from **mustacheride**.
Most of informations you're looking for are [here](http://www.proftpd.org/) 
To get more debug informations : [http://www.proftpd.org/localsite/Userguide/linked/x1058.html](http://www.proftpd.org/localsite/Userguide/linked/x1058.html)
You can specify a specific passive port range using [PassivePorts](http://www.proftpd.org/localsite/Userguide/linked/config_ref_PassivePorts.html)  command, it's very useful when you use a [firewall](http://www.proftpd.org/localsite/Userguide/linked/x294.html)  in order to know which ports to allow.

[COLOR="Sienna"]For those who have a firewall/router i advice to read [this excelent post]("http://www.ubuntuforums.org/showpost.php?p=680702&postcount=81") from[/COLOR] **mssm**

Thanks for feedback, and sorry if my english is sometimes really bad :roll: 

Don't hesitate to post questions about proftpd in this thread.

---

### Post by anatole on 2005-10-22
hi,
thanks for the howto, however, i have a problem.
i have a router and the proftpd site is not really informative... well at least not for a noob like me:) so... on the link, it says "First configure your ProFTPD install so that it works right from inside the NAT. There are example configuration files included with the source." now i downloaded the source and had a look on the config files, but i couldn't find anything relevant. any help on this?
also, i'm not sure if i entered the value of 'MasqueradeAddress' correctly. I entered my dyndns domain, so what i get is
```
attila@nanaki:/home/FTP-shared$ sudo /etc/init.d/proftpd restart
Password:
Restarting ProFTPD ftp daemon.proftpd.
..localhost.localdomain - 127.0.0.1:1980 masquerading as 84.0.161.247
proftpd.
 done.
```
is thít what should happen? i'm just asking because i'm not sure :)

i did everything else as the guide said, and my problem is that i get a connection timeout. any help would be appreciated, thanks :)

---

### Post by frodon on 2005-10-22
I'm not a NAT expert because i have only a software firewall but i think this [link]("http://www.ubuntuforums.org/showthread.php?t=39566&highlight=proftp+nat") could help you, also in the original thread some users have used these commands with success, try to follow their example or send us a PM, your problem will be quickly solved. :p

---

### Post by anatole on 2005-10-22
strange, i get the 530 error when i try to log in... i've read the otheer forum but all my setting should match...

```
attila@nanaki:/home$ la
total 8.0K
drwxr-xr-x  55 attila  attila 4.0K 2005-10-22 17:46 attila
drwxr-xr-x   4 userftp root   4.0K 2005-10-22 10:45 FTP-shared
attila@nanaki:/home$ la FTP-shared 
total 8.0K
drwxr-xr-x  2 root root 4.0K 2005-10-22 10:45 download
drwxrwxrwx  2 root root 4.0K 2005-10-22 10:45 upload
```

sorry i'm almost sure i'm being lame but i cannot help it :) so here is my proftpd.conf as well, anyone could help?

---

### Post by frodon on 2005-10-22
You should comment the 2 last lines of your file because you have 3 active MasqueradeAddress lines in your file, and also try to change the password of the user, i already met persons who've got problems with the user password.
Your settings looks good, did you test the server with your own computer or with a friend ?

---

### Post by anatole on 2005-10-22
[QUOTE=frodon]You should comment the 2 last lines of your file because you have 3 active MasqueradeAddress lines in your file, and also try to change the password of the user, i already met persons who've got problems with the user password.
Your settings looks good, did you test the server with your own computer or with a friend ?[/QUOTE]

changed the password, commented out the last two lines, still error 530. tested on my comp, and on a friend's one. :/

---

### Post by frodon on 2005-10-24
Hmm, have you tested to comment the MasqueradeAddress and PassivePorts lines to see if the problem come from these lines ? Because for me your configuration is ok, are you sure to put the good parameters in gFTP when you attempt to connect yourself to the server ?
Just in case give me the gFTP log and what you enter in the fields but i guess it's ok.
Also if you still have a 530 error it could be interesting to collect more [debug infos]("http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Debugging.html").

---

### Post by kapetanski on 2005-10-26
Thanx for the howto, it works great! But I think it's strange that the xferlog has been empty two times now since I started to use my ftp server, is it cleared by default? Are there other logfiles aswell that proftpd use? I'am also thinking of using ssh(or some sort of crypto) on the proftpd server, anyone tried this?

---

### Post by frodon on 2005-10-26
What you're looking for is in the mod_tls module of proftpd, you should already have it (use the proftpd -l command to verify it).
There is a reference exemple [here]("http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html") and i think it's a good start to read this exemple.
If you get SSL/TLS working, send me a PM or post here and i will add this in the GUIDE.

Why do you want to use secure ftp protocol ? i'm just curious

---

### Post by frodon on 2005-10-27
[QUOTE=anatole]changed the password, commented out the last two lines, still error 530. tested on my comp, and on a friend's one. :/[/QUOTE]You could try this command line : ```
sudo passwd userftp
```and then retype your password, it solve the problem for tspec who give me his feedback.

---

### Post by herot on 2005-10-27
question:
i just did
```
apt-get install proftpd
```
then as root i unchecked the proftpd service at startup, so i can just ```
proftpd -n
``` 
whenever i want to (because i only run it sometimes...when i need it).  however i did not make many changes to my proftpd.conf file (just made it type=standalone)... i didn't change any permissions or anything... i figure this is secure enough for me since i only start it when i want to move some files and then end it when im finished... is this ok?

---

### Post by atomicski on 2005-10-29
I just installed Breezy Badger and am having some problems running certain services/servers...

when I do ```
apt-get install proftpd
```

it says ```
Couldn't Find Package proftpd
```

---

### Post by frodon on 2005-10-30
**herot**, if you want to disable proftpd on startup you could just go in System > Administration > Services, it works well. If your configuration is ok for your need and if you will not use proftpd often and for a long time, it might be enough secure like that.

**atomicski**, it seems that you haven't enable all the repositories. Open your source.list file : ```
sudo gedit /etc/apt/sources.list
```then check that you have these lines, if not add them : ```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

---

### Post by TokenBad on 2005-12-16
ok I have did like you said...I but I also am behind a router...I set the ports in the router and forward them to proftpd.  I set the ports in proftpd.conf...I can ftp in fine and all that..but when try to list a dir I get port error ip already in use....anyone help?

TokenBad

---

### Post by Leaf on 2005-12-17
I am having the same problem as anatole, error 530
Our .conf files are almost exactly the same (no las 2 lines and minor name differences)

I've reset the password too, still 530

The alias part of the conf, I've tied logging in as both the first name and the second, same each time

any suggestions?

---

### Post by frodon on 2005-12-19
Leaf, could you post your proftpd.conf file please, and check the path and the name of the directories because the 530 error is often due to name or path mismatches.

TokenBad this link may help you : [http://www.ubuntuforums.org/showthread.php?t=39566](http://www.ubuntuforums.org/showthread.php?t=39566)

---

### Post by keving79 on 2005-12-30
[QUOTE=frodon]Leaf, could you post your proftpd.conf file please, and check the path and the name of the directories because the 530 error is often due to name or path mismatches.[/QUOTE]

I'm having the same problem. I followed your tutorial. Attached is my proftpd.conf file.  I've tried changing things round, trying different port numbers, changing passwords, etc.  No matter what I keep getting the 530 error.  PLEASE help! I've been up all night trying to get this blasted thing to work. 

Thanks..

---

### Post by jbinc1 on 2005-12-30
I took a look at your proftpd.conf file. I noticed a few differences with my own. First, I'm not sure that the way you have your multiple user aliases will work. Take a look at the way I have mine set up. I know it works correctly. I have multiple user logins and a different password for each. I have this same configuration (with the exception of different user aliases and ip's.) running on 2 machines.

I took your proftpd.conf file and tried it in my test machine. Other than changing the UserAlias to make it work and commenting out the Mascarade line, It worked just fine. I am attaching a copy of the proftpd.conf file from my test machine so you can compare it with your own. 

Are you behind a router or firewall? And do you have another computer sharing the same connection to test with? If you can get it working within the NAT, it's just a matter of getting your router and or firewall configured correctly.

Let me know how it goes.

Good luck. :)

---

### Post by frodon on 2006-01-01
**keving79**, like in my guide you use this line at the beginning of the proftpd.conf file : ```
AuthAliasOnly on
```so only alias login are allowed and you didn't set an alias for your users and it's the problem here.
**jbinc1 **gave you a good exemple on how use differents users with an alias for each, you should follow his exemple and your problem should be solved. I use useralias in my guide because it prevent telnet accesses, but if you don't want to use useralias just replace the line "AuthAliasOnly on" by "AuthAliasOnly off" and login your ftp server with the username and the password and it should work too, up to you ;).

You can also define different access levels for each user, for exemple if you don't want a user to see or use a shared directory or if you just want to give him a read access. If some of you here are interrested, tell me and i will provide you some exemples.

---

### Post by steve_250 on 2006-01-02
I used my own and the test .conf file above and got the same results.  Error 530 Login incorrect.  I have used the password change command and still get 530.  After every change in pw and the .conf, I did a restart.
Oh, I did a /home/ftp AND /home/FTP-shared as the example, tried both.
Checked groups in etc and user/group exist.
Where else can I look for the "incorrect" login info? :confused: 

Conf file attached....

Thanks,
Steve...

---

### Post by frodon on 2006-01-03
Hi **steve_250**,
First you should replace those lines : ```
# Set the user and group that the server normally runs at.
User                  root
Group                 root
```by those lines : ```
# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup
```Go in your /home/ftp directory and give us the result of the "ls -lg", and tell me what are the exact parmeters you used to login your ftp server (user, pass, port, address). Try to give us the maximum details, because the 530 error always come from a small mismatch.

---

### Post by steve_250 on 2006-01-03
Hello Frodon, thanks for the reply.
I have replaced the lines and ran the command, here are the results:

steve@ubuntu:/home/ftp$ ls -lg
total 20
drwxrwxrwx  84 root 12288 2006-01-01 17:01 download
drwxrwxrwx   2 root  4096 2005-12-31 15:48 upload
-rw-r--r--   1 root   166 2005-09-05 13:17 welcome.msg
steve@ubuntu:/home/ftp$

Running Gftp with user steve pass xm3y9sjp port 21:

Looking up 192.168.2.33
Trying 192.168.2.33:21
Connected to 192.168.2.33:21
220 Ubuntu
USER steve

331 Password required for steve.
PASS xxxx
530 Login incorrect.
Disconnecting from site 192.168.2.33

Thanks for helping....
Steve...

---

### Post by frodon on 2006-01-03
There is another thing i didn't see before, in the "<Directory> /home/ftp/upload/>" field, modify it like that : ```
<Directory> /home/ftp/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	**AllowAll**
    	</Limit>
</Directory>

```This will allow you to write in the upload directory.
Now for your login issue, try to login your gnome session with **userftp** in order to be sure that it's not a user creation problem. Check also that your home/ftp directory have 755 rights.

---

### Post by steve_250 on 2006-01-03
Ok, did all the above and entered pw for ftpuser again.

I gftp in with "steve" and go this far and now it sits there.

230 welcome !!!
SYST

215 UNIX Type: L8
TYPE I

200 Type set to I
PWD

257 "/" is current directory.
Loading directory listing / from server (LC_TIME=en_US.UTF-8)
PASV

227 Entering Passive Mode (138,88,144,129,250,43).

The remote window just says "Receiving file names".
Kind'a stuck there.
Says the application is not responding when I try to close it after a 5 minute wait.

conf attached again.

---

### Post by steve_250 on 2006-01-03
I took a look at the permissions, all is set to 755 starting with "Home".

This is also what I see:

[U]Location                      Owner                          Group
[/U]
HOME                            Root                            Root
ftp                                  ftp                               nogroup

Under ftp:
download                        Root                           Root
upload                             Root                           Root

I gave 777 to u/l as the first page you wrote said to do.

---

### Post by frodon on 2006-01-03
Do you attempt to login the ftp server with the same computer which run the server or with another one ?
The first thing to test is to login the ftp server with the same computer which run the ftp server then if it works the problem come from your router.

---

### Post by steve_250 on 2006-01-03
I tried it with the same machine, that's the log I sent ya.
Through another machine I had the same problem.

I also have tried to set the owner/group of all the directories to "steve".
(home/ftp, u/l & d/l)
In doing so, I now get the 530 error again.

What should the dir's be set to for owner/group?
Also chmod them to 774.

My login is steve and the machine will normaly be running under my name login.

---

### Post by frodon on 2006-01-03
The owner should be root (it is in my case) and 775 rights are needed for your /home/ftp directory.

---

### Post by steve_250 on 2006-01-03
Just to make sure I have it right, owner/group for ALL the mentioned directories are supposed to be root?
I'll do that and make sure it's all 775.
Ok, fixed that.

I commented out the passive mode and masquereding and it works locally now.
Any concern with commenting these out?

I try it through the internet, still hangs at receiving file names.
This is what Gftp reports:

USER steve

331 Password required for steve.
PASS xxxx
230 welcome !!!
SYST

215 UNIX Type: L8
TYPE I

200 Type set to I
PWD

257 "/" is current directory.
Loading directory listing / from server (LC_TIME=en_US.UTF-8)
PASV

227 Entering Passive Mode (192,168,2,33,4,52).
LIST -aL

Disconnecting from site sjp.serveftp.net
Invalid response '

---

### Post by keving79 on 2006-01-03
[QUOTE=frodon]You can also define different access levels for each user, for exemple if you don't want a user to see or use a shared directory or if you just want to give him a read access. If some of you here are interrested, tell me and i will provide you some exemples.[/QUOTE]

YEs, I'd be very interested in this. Now that I finally got the FTP working (thanks to your advice), I'd like to setup different access levels for different users. If you could post a tutorial for that, that would be sweet. 

Thanks!

---

### Post by t0bb3 on 2006-01-03
I have followed the howto, but when I run "sudo /etc/init.d/proftpd start" I get this message: > ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration.

This is what my proftpd.conf file looks like:
```
#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

AllowOverwrite                  on
AuthAliasOnly                   on

# Choose here the user alias you want !!!!
UserAlias                       upload userftp

ServerName                      "htpc"
ServerType                      inetd
DeferWelcome                    on

MasqueradeAddress               my.ip.is.here
PassivePorts                    60000 60100 #this is a range, not just two ports

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    off

TimeoutNoTransfer               600
TimeoutStalled                  100
TimeoutIdle                     2200

DisplayFirstChdir               .message
ListOptions                     "-l"

RequireValidShell               off

TimeoutLogin 20

RootLogin                       on

# It's better for debugging purposes to create log files
ExtendedLog                     /var/log/ftp.log
TransferLog                     /var/log/xferlog
SystemLog                       /var/log/syslog.log

#DenyFilter                     \*.*/

# I don't choose to use /etc/ftpusers file (use it to ban users by
just writing their username in it)
UseFtpUsers                     off

# Allow to restart a download
AllowStoreRestart               on

# Port 21 is the standard FTP port, so don't use it for security
reasons (choose here the port you want)
Port                            2121

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                            nobody
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022     022

PersistentPasswd                off

MaxClients                      8
MaxClientsPerHost               8
MaxClientsPerUser               8
MaxHostsPerUser                 8

# Display a message after a successful login
AccessGrantMsg                  "welcome to t0bb3's ftp server"
# This message is displayed for each access good or not
ServerIdent                     on       "HTPC ftp server"

# Set /home/FTP-shared directory as home directory
DefaultRoot                     /home/FTP-shared

# Lock all the users in home directory,
#    ***** really important *****
DefaultRoot                     ~

MaxLoginAttempts                3

#VALID LOGINS
<Limit LOGIN>
       AllowUser userftp
       DenyALL
</Limit>

<Directory /home/FTP-shared>
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

<Directory> /home/FTP-shared/upload/>
       Umask 022 022
       AllowOverwrite on

       <Limit READ RMD DELE>
               DenyAll
       </Limit>

       <Limit STOR CWD MKD>
               AllowAll
       </Limit>
</Directory>
```
Do you see anything wrong?

---

### Post by frodon on 2006-01-03
Replace : ```
ServerType                      inetd
```by : ```
ServerType 			standalone
```and it should work.

By the way the "RootLogin                       on" option is not really secure, if you don't know why you use it i advice you to put it off.

---

### Post by t0bb3 on 2006-01-04
But I choose inetd duing the install of the server. It said inetd would be more resource friendly if I only had a few connections every day, and it's basicly only I that connect to the ftp server. Why should I change to standalone?

I'll change the RootLogin option

---

### Post by frodon on 2006-01-04
Yes it's a little bit more resource friendly but standalone server is easier to use and if you don't have 20 users who use your server at the same time you won't see the difference.

Link : [http://www.proftpd.org/localsite/Userguide/linked/config_ref_ServerType.html](http://www.proftpd.org/localsite/Userguide/linked/config_ref_ServerType.html)

---

### Post by t0bb3 on 2006-01-04
Thank you, it starts now :)

But why didn't it work with inetd as the servertype?

---

### Post by t0bb3 on 2006-01-04
Reading the proftpd manual ([http://www.proftpd.org/localsite/Userguide/linked/x430.html](http://www.proftpd.org/localsite/Userguide/linked/x430.html)) I decided to give inetd another go. They all say inetd is better suited when there aren't that many connections.

When I choose inetd as the server type duing the initial install proftpd made the necessary changes to /etc/inetd.conf. So the server should have been ready for use as soon as I had installed it. I had missunderstood the whole ```
 sudo /etc/init.d/proftpd start
 sudo /etc/init.d/proftpd stop
 sudo /etc/init.d/proftpd restart
```thing. It's only for when you run the server in standalone mode! I thought I should do that even when in inetd mode, but that was wrong.

Another nice thing about inetd mode is that you don't have to do anything special when you make changes to proftpd.conf. The server rereads that file for every new connection.

---

### Post by t0bb3 on 2006-01-04
[quote=keving79][quote=frodon]
You can also define different access levels for each user, for exemple if you don't want a user to see or use a shared directory or if you just want to give him a read access. If some of you here are interrested, tell me and i will provide you some exemples.[/quote]

YEs, I'd be very interested in this. Now that I finally got the FTP working (thanks to your advice), I'd like to setup different access levels for different users. If you could post a tutorial for that, that would be sweet.

Thanks![/quote]
I second this.
And I would also like to know how to set up virtual users

Thanks

---

### Post by frodon on 2006-01-04
This is a small exemple on how avoid **user2** to enter in the download directory.
In this case 2 users have been created (userftp and user2) and each one have its own alias.
This exemple will allow userftp to see all the shared directory and avoid user2 to use the dowload directory, (i give you only the directory section) : ```
#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
AllowUser user2
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
		Order Allow,Deny
		AllowUser userftp
		AllowUser user2 
		Deny ALL
	</Limit>
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
		Order Allow,Deny
		AllowUser userftp
		Deny ALL
	</Limit>
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
        <Limit ALL>
		Order Allow,Deny
		AllowUser userftp
		AllowUser user2 
		Deny ALL
	</Limit>
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
```

---

### Post by jbinc1 on 2006-01-04
Hello frodon,

My ftp server has been running for a few weeks now thanks to your excellent HOWTO. Now I need some help speeding it up. Inside the nat I get great upload/download speeds. Over the internet I am limited to about 50 kbs. Any ideas? :confused:

---

### Post by frodon on 2006-01-05
It's because when you are inside the NAT the limit is the limit of the local network and when you are outside the NAT the limit is your internet connection speed wich is really lower than the local network speed.
Did you already reach a better upload rate with IRC, msn, or another share protocol ?

---

### Post by frodon on 2006-01-05
I'm thinking about a new howto or an improvement of this one for newbies (and this will be only for newbies !). Because proftpd has a GUI called Gproftpd but i generally don't advice it because you need to run it as root and you can easily break your server configuration or create a unsecure ftp server, however i think newbies will prefer this way (less secure but more userfriendly).

So, please could someone test this GUI and give me his personnal opinion about it in order to help me to know if i should advice it for newbies and create a small guide for it ?

Thanks for helping me to estimate this way to use proftpd.

here are the website link and a screenshot at the bottom of the post : 
[http://mange.dynalias.org/linux.html](http://mange.dynalias.org/linux.html)

---

### Post by jbinc1 on 2006-01-06
Hello frodon,

I'm setting up a fresh install of Ubuntu and I'm going to test the Gproftpd gui. I will see how it goes using the instructions on the Gproftpd web site and give you feedback.

Also, I think my slow connections on my ftp server are possibly due to my router. I still have to do more research on that one. ](*,)
When I connect to other ftp servers, I'm getting excellent speeds. I did some searching and it seems I'm not the only one to have this problem. 

Take it easy.

---

### Post by steve_250 on 2006-01-06
Sure seems like an easier way for newbies like me.
I installed it and got a text that said it's running.  Didn't get the GUI interface or see an icon.
I'll try again today.

Jbinc1, no, you're not the only one with slow speed, going through my Netgear FVS318 is slow to connect too.

I tried the inet install instead of standalone and it won't run at all.  How to I reinstall proftpd?  I'll switch back to standalone.

---

### Post by jbinc1 on 2006-01-06
Hello Steve,

I've done some pretty extensive searching on the slow connection subject and I can't seem to find any solution. If you happen to find anything feel free to pm me and let me know. I really like the easiness of the setup and the way my ftp server is running, but I have the need for speed, if you know what I mean. :)

If you go into the proftpd.conf file where it says "ServerType" you should be able to just change it back to "standalone".

---

### Post by steve_250 on 2006-01-06
I also noticed some differences in the inet and standalone.  In the inet install, it creates it's own ftp directory under home.  It also starts in /init.d instead of inirtd as it wants to (says it can't find it in inirtd).

Jbinc1, I'm going to see if I can buy a splitter to run off my DSL modem to put the server outside the router.
Yep, changed it to standalone in the conf and now it won't run at all.  Want to do a re-install.  Stuff is in different directories than with the standalone install, at least in MY machine.

---

### Post by frodon on 2006-01-06
[QUOTE=jbinc1]Hello frodon,

I'm setting up a fresh install of Ubuntu and I'm going to test the Gproftpd gui. I will see how it goes using the instructions on the Gproftpd web site and give you feedback.

Also, I think my slow connections on my ftp server are possibly due to my router. I still have to do more research on that one. ](*,)
When I connect to other ftp servers, I'm getting excellent speeds. I did some searching and it seems I'm not the only one to have this problem. 

Take it easy.[/QUOTE]Hi jbinc1,

I'm wondering something, when you say that you have a slow connections, do you mean transfert speed ?
Because most of DSL connections have a really poor upload speed compared to the download speed, maybe it's just your internet connection which have a low upload speed and a good download speed. It could explain why you download fast on other FTP server and not with yours.

---

### Post by steve_250 on 2006-01-06
Going through my router when I enter the actual internet address and NOT the local net address (192.168.) it is slow to connect and go through the password dialogue.
Going locally, 192.168. it connects right away.
This is all done on the same machine ftp is installed on, using gftp.

Getting this error now when using gftp and the internet address:
As seen in gftp:

230 welcome !!!
SYST

215 UNIX Type: L8
TYPE I

200 Type set to I
CWD /

250 CWD command successful
Loading directory listing / from server (LC_TIME=en_US.UTF-8)
PASV

227 Entering Passive Mode (192,168,2,33,4,12).
LIST -aL

Disconnecting from site sjp.serveftp.net
Invalid response '

What do you thing the "invaild response" could be?

On edit:
I disabled passive xfers in gedit and it works fine now.
Using a standard browser it connects when I put in the local net address (192.168) but times out when putting in the internet address.

---

### Post by jbinc1 on 2006-01-06
Steve,

Try this in your proftpd.conf file

```
 
UseReverseDNS off
IdentLookups off
```

---

### Post by jbinc1 on 2006-01-06
[quote=frodon]Hi jbinc1,

I'm wondering something, when you say that you have a slow connections, do you mean transfert speed ?
Because most of DSL connections have a really poor upload speed compared to the download speed, maybe it's just your internet connection which have a low upload speed and a good download speed. It could explain why you download fast on other FTP server and not with yours.[/quote] 

Hi frodon,

I did some more tests and you're right. My conversion from Bps to kbps was wrong (oops). It looks like I'm getting all of the speed I'm going to get. My upload is limited to 312 kbps and I'm I'm averaging about 36000 Bps. I better double check my math next time. Live and learn.

Thanks for all of your help.

---

### Post by steve_250 on 2006-01-06
[QUOTE=jbinc1]Steve,

Try this in your proftpd.conf file

```
 
UseReverseDNS off
IdentLookups off
```[/QUOTE]

Thanks, it "seemed" to speed up the pw dialog box but still times out after entering name and pw.

---

### Post by jbinc1 on 2006-01-06
Do you have a firewall?

---

### Post by steve_250 on 2006-01-06
[QUOTE=jbinc1]Do you have a firewall?[/QUOTE]

Yes, I do but it is ported open.  Calls to the Apache server from outside go through.
It's on the same machine.
I'll mess with it more tomorrow.

---

### Post by steve_250 on 2006-01-09
I'm still not connecting from a windoze machine using the server's internet address.  Using IE I put in the pw and it hangs on "Getting contents of folder".  
Times out with "An error occured on the server, make sure you have permission to access that folder". (I know thats a standard Win error format)
I can connect fine using the 192.168 internal though.

More ideas?

---

### Post by frodon on 2006-01-09
Could you post your proftpd.conf, i'd like to see if there isn't something which block the LIST or CWD command, it could come from you configuration file or from wrong system rights in your ftp folder.

Also if you use IE to connect to the ftp server don't forget to specify the port if you don't use port 21, i give you an example corresponding to the guide (which use the port 1980) : ftp:\\sauron@100.12.xx.xxx:1980

---

### Post by steve_250 on 2006-01-09
I am currently using port 21 because I haven't yet figured out to make a port change in my Netgear FVS318.  It has a dropdown for service but no selection of ports.
Still looking for it....
Thank you Frodon!
Here is my conf file:

# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias steve userftp

ServerName			"Ubuntu"
ServerType 			standalone
DeferWelcome			on

UseReverseDNS off
IdentLookups off

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 99

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
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

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

---

### Post by BlueIce on 2006-01-09
Having a bit of trouble with step 3 "sudo gedit /etc/proftpd.conf" on the first page.

This file does not exist.

What have I done wrong, thanks

I did a search on this file (I think I did the search right) and it does not exist anyware on the system.

---

### Post by steve_250 on 2006-01-09
Try it in a new terminal window.
When doing a search, I don't remember if it is a hidden file (don't think so).

---

### Post by BlueIce on 2006-01-09
[QUOTE=steve_250]Try it in a new terminal window.
When doing a search, I don't remember if it is a hidden file (don't think so).[/QUOTE]

Didn't help when I don't read it carefully

sudo apt-get install proftpd
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package proftpd

What did I do wrong?
Do I have to add extra repositories?

Thanks

---

### Post by frodon on 2006-01-10
**Bluelce**, indeed you shouldn't have all the repositories enabled. You could post you /etc/apt/source.list here if you wish otherwise you will find all needed informations about source.list here : [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672).

**steve_250**, your configuration sounds good for me, so i think the problem should be your Netgear FVS318 configuration, because all your FTP server configuration seems good.

---

### Post by jbinc1 on 2006-01-10
steve_250

Take a look at these links from frodon's HOWTO.

[SIZE=3]_**Other stuff**_[/SIZE]
**If you have a router** you should read [that]("http://www.proftpd.org/localsite/Userguide/linked/x862.html"), it describe the 2 commands to add in proftpd.conf and why. 
If you have a dynamic DNS have a look [here]("http://www.frankandjacq.com/ubuntuguide/5.04/index.html#assignhostnametodynamicip"), you can also use [ddclient]("http://linux.cudeso.be/linuxdoc/ddclient.php")(maybe easier for newbies).  
Most of informations you're looking for are [here]("http://www.proftpd.org/") 
To get more debug informations : [http://www.proftpd.org/localsite/Use...ked/x1058.html]("http://www.proftpd.org/localsite/Userguide/linked/x1058.html")
You can specify a specific passive port range using [PassivePorts]("http://www.proftpd.org/localsite/Userguide/linked/config_ref_PassivePorts.html")  command, it's very useful when you use a [firewall]("http://www.proftpd.org/localsite/Userguide/linked/x294.html")  in order to know which ports to allow.

---

### Post by BlueIce on 2006-01-10
[QUOTE=frodon]**Bluelce**, indeed you shouldn't have all the repositories enabled. You could post you /etc/apt/source.list here if you wish otherwise you will find all needed informations about source.list here : [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672).[/QUOTE]

Alright I got it working, prob not how I wanted it to run but here is what I did.

Commented in 
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy universe
(Not sure if I am supposed to comment out other ones)

Then Installed proftpd, instructions on on first page of this thread.
I then wanted a GUI (I'm very new to linux)

gproftpd is at: [http://mange.dynalias.org/linux.html](http://mange.dynalias.org/linux.html)

Not sure if I did the right thing but I downloaded the source.

Needed to compile it and somehow got to this page: [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)
All beginners should read this, it made it really easy:) REALLY

End up running
sudo apt-get install build-essential

I think I then needed Development files for the GTK
So Installed libgtk2.0-dev (Development files for the GTK+ library) from Synaptic Package Manager. I hope that was the right thing to do.

I think it then compiled OK as I was able to run the GUI.

Problems:
1. Installed gproftpd in Home directory (How do I stop that from happing in the future and how can I fix that now(Copy n paste)?
2. How do I run something as root. Can I add it to the menu.
3. Should I wright commands in the forums with a $ in front of them?
Thanks

---

### Post by frodon on 2006-01-10
1. Generally only the config files are installed in the home directory because it defines specific setting for your user and only your user.
2. To run gproftpd as root, use this command in a terminal : ```
sudo gproftpd
```
3. Up to you ;)

But even if you're new to linux you don't inevitably need a GUI, especially if you use often your server. Also if you just want a GUI to see the traffic on your ftp server the "ftptop" command is enough.

However i planed to write a short guide in the next 3 weeks for Gproftpd if it's needed.
So if you finally use Gproftpd and enjoy using it don't forget to tell me.

---

### Post by steve_250 on 2006-01-10
Ok, finally found where to change the ftp port number in the router.
I changed it to 1980, it IS supposed to be TCP, oui?
Added the masquereding and passive lines in your page one example.
However, now I get "Connection refused" even when doing it through the same machine using Firefox.  Using gftp I see:

230 welcome !!!
SYST

215 UNIX Type: L8
TYPE I

200 Type set to I
PWD

257 "/" is current directory.
Loading directory listing / from server (LC_TIME=en_US.UTF-8)
PORT 192,168,2,33,18,53

500 Illegal PORT command
Invalid response '5' received from server.
Disconnecting from site such.and.such
](*,)

Oh yeah, Frodon, in the nmap usage example, the I (eye) feature is no longer supported.

---

### Post by jbinc1 on 2006-01-10
frodon,

I've been doing some testing on gftpd. I had problems installing from source. First, you have to make sure you have a c compiler installed. Next, it seems the the source is broken. I've tried everything I could think of to get it to work. So, I did some searching and was able to find a debian package and installed it. I was able to install but there are some errors in the config out of the box (ie. it looks for a directories that don't exist). I made some changes to the config file, but I continue to get a SecurityLog errror. I did a check on the syntax and everything was good. I had to add the directories it was looking for to stop the error

The interface seems nice, but there is a definite lack of documentation on the sight or in the help file to support the program. I don't know if it would be a help or a hinderence to someone trying to set up their first ftp server.

---

### Post by steve_250 on 2006-01-10
Update:
On same machine, switched gftp to passive and it logs on but gets stuck at "Receiving file names".
Tried ascii and also removing the -L option, still stuck.

---

### Post by frodon on 2006-01-10
I don't think the problem come from the the [ ListOptions]("http://www.proftpd.org/localsite/Userguide/linked/config_ref_ListOptions.html") so you should keep the -l option.
I think you should look in your router configuration first, you have to configure your router to link the port 1980 to your PC and also to enable it with the good protocol.

Don't forget to have a look in the proftpd forum, there's a lot of useful informations in, maybe you could find here a user who use the same router as you : [http://forums.proftpd.org/phpBB2/](http://forums.proftpd.org/phpBB2/)

---

### Post by steve_250 on 2006-01-10
The link above doesn't work, I'll start at their main page.

I do have the router set to port 1980, changed it back to 21 and got the same error.

I looked at the ftp.log and found the router is passing the request through but the file list isn't coming through.

138.88.144.129 UNKNOWN nobody [10/Jan/2006:10:48:12 -0500] "USER steve" 331 -
138.88.144.129 UNKNOWN userftp [10/Jan/2006:15:48:12 +0000] "PASS (hidden)" 230 -
138.88.144.129 UNKNOWN userftp [10/Jan/2006:15:48:12 +0000] "SYST" 215 -
138.88.144.129 UNKNOWN userftp [10/Jan/2006:15:48:12 +0000] "TYPE I" 200 -
138.88.144.129 UNKNOWN userftp [10/Jan/2006:15:48:12 +0000] "PWD" 257 -
138.88.144.129 UNKNOWN userftp [10/Jan/2006:15:48:12 +0000] "PASV" 227 -
138.88.144.129 UNKNOWN userftp [10/Jan/2006:15:50:13 +0000] "PASV" 227 -

I have the permissions set as you said to set them.

---

### Post by steve_250 on 2006-01-10
No progress...
Everything set to port 1980 (router, conf & gftp)
From the router log when attempting to gftp in from same machine:

Tues, 01/10/2006 09:48:17 - UDP packet dropped - Source:221.1.204.254, 45006, WAN - Destination:138.88.144.129, 1027, LAN - 'Suspicious UDP Data'
Tues, 01/10/2006 09:50:23 - TCP connection dropped - Source:138.88.28.18, 2770, WAN - Destination:138.88.144.129, 445, LAN - 'SMB'

From the debug log:
Jan 10 07:36:22 localhost kernel: [4718395.530000] ppdev0: registered pardevice
Jan 10 07:36:22 localhost kernel: [4718395.571000] ppdev0: unregistered pardevice
Jan 10 07:36:22 localhost kernel: [4718395.571000] ppdev1: claim the port first
Jan 10 07:36:22 localhost kernel: [4718395.571000] ppdev2: claim the port first

---

### Post by BlueIce on 2006-01-12
[QUOTE=jbinc1]I've been doing some testing on gftpd. I had problems installing from source. First, you have to make sure you have a c compiler installed. Next, it seems the the source is broken. I've tried everything I could think of to get it to work.[/QUOTE]

I think you might need the Development files for GTK
I Installed libgtk2.0-dev (Development files for the GTK+ library) from Synaptic Package Manager and I was able to install from source.

---

### Post by BlueIce on 2006-01-12
[QUOTE=frodon]1. Generally only the config files are installed in the home directory because it defines specific setting for your user and only your user.
2. To run gproftpd as root, use this command in a terminal : ```
sudo gproftpd
```
3. Up to you ;)

But even if you're new to linux you don't inevitably need a GUI, especially if you use often your server. Also if you just want a GUI to see the traffic on your ftp server the "ftptop" command is enough.

However i planed to write a short guide in the next 3 weeks for Gproftpd if it's needed.
So if you finally use Gproftpd and enjoy using it don't forget to tell me.[/QUOTE]

1. I am pritty sure it is all installed it in the home directory as the etc and src directors are in there. I used the command $./Autoinstall it [listed]("http://mange.dynalias.org/linux.html") on the site. What is the correct way to install it, and do I have to uninstall the old one? Dose linux have a registry or am I correct in saying it just uses config files.

2. so that what sudo does:D 

3. Umm thanks:)

---

### Post by frodon on 2006-01-12
[QUOTE=BlueIce]1What is the correct way to install it[/QUOTE]For me the correct way to install it is to follow the instructions of the web site and just replace the final command (sudo make install) by : ```
sudo checkinstall -D
```
checkinstall is a tool (you can find it in synaptic) which allow you to create a .deb of the sources and install the software with all the needed informations to see it in synaptic and therefore uninstall it easily.
If you didn't use checkinstall and want to use it i think this command (in the gproftpd source directory) will uninstall gproftpd : ```
sudo make uninstall
```

---

### Post by BlueIce on 2006-01-12
It all looks good now.

thank you heaps for your help:D

---

### Post by frodon on 2006-01-15
For those who want to use the proftpd GUI, i updated the HOWTO with some short instructions and a .deb of the latest version.

After some tests, i found that gproftpd is not so bad but a little bit annoying for advanced users because the GUI is able to create directories and system users (you need to run it as root) and it's less secure (it's just my opinion ;) )

---

### Post by hen3rz on 2006-01-15
Is there a way i can manage this server via php on my apache2 server?

---

### Post by kasemodz on 2006-01-16
alright mine is really wierd. I can get proftpd to start. However, when i try to access it from another computer, it asks for my username and password. I put it in and press enter. It searches for something then comes back with the login window, how do i fix this? Here is my proftpd config.
> #
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

ServerName			"OnDemand"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

DenyFilter			\*.*/
DefaultRoot                     ~

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd		off

# Uncomment this if you would use TLS module:
#TLSEngine 			on

# Uncomment this if you would use quota module:
#Quotas				on

# Uncomment this if you would use ratio module:
#Ratios				on

# Port 21 is the standard FTP port.
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				admin


# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default. 
#DelayEngine 			off

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayFirstChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>


---

### Post by frodon on 2006-01-17
I don't know what you want to do and you didn't use the guide as i see in your conf file so how could someone help you with so few informations ?
So how did you create your proftpd.conf file ? it seems really near from the default one, so what is your aim ?

**hen3rz**, i searched a little bit yesterday but i didn't find any informations on the topic. Maybe you could post your question in the server talk forum there's some server gurus in ;).

---

### Post by kasemodz on 2006-01-17
hey frodon since i couldn't get ftp working with the guide's conf I used this guide to install it. I just wanted to see if the ftp works by using nearly the default one. Here is the link btw. [http://www.ubuntuguide.org/#ftpserver]("http://www.ubuntuguide.org/#ftpserver")

Btw now that I'm thinking of it, I did install the gui version of ftp this guide talked about but I couldn't uninstall it. Then i installed proftpd. Do you think that could be the problem?

---

### Post by frodon on 2006-01-18
[QUOTE=kasemodz]Btw now that I'm thinking of it, I did install the gui version of ftp this guide talked about but I couldn't uninstall it. Then i installed proftpd. Do you think that could be the problem?[/QUOTE]Gproftpd is only a frontend for proftpd, so you need to have proftpd installed to use gproftpd.
To uninstall gproftpd, use this command if you used the .deb : ```
sudo dpkg -r gproftpd-8.2.2_8.2.2-1_i386.deb

```You should also be able to uninstall it with synaptic.
When i asked you what is your aim, i meant what is your need about ftp server. Do you just want to share some files with friend or with everybody ? do you wish a secure server ?

I ask you that because in your conf file you don't share any directories so i have no idea about what you're trying to do.

---

### Post by kasemodz on 2006-01-19
[QUOTE=frodon]Gproftpd is only a frontend for proftpd, so you need to have proftpd installed to use gproftpd.
To uninstall gproftpd, use this command if you used the .deb : ```
sudo dpkg -r gproftpd-8.2.2_8.2.2-1_i386.deb

```You should also be able to uninstall it with synaptic.
When i asked you what is your aim, i meant what is your need about ftp server. Do you just want to share some files with friend or with everybody ? do you wish a secure server ?

I ask you that because in your conf file you don't share any directories so i have no idea about what you're trying to do.[/QUOTE]

um frodon, my aim is just to setup a ftp server so i can access it on my land. I'll be uploading stuff to it and downloading.

---

### Post by linuxfan on 2006-01-19
t0bb3:

Thanks for your additional tip! I too had the same problem and was wondering what was wrong with inetd install type. Will try tonite once I get back from work.

Cheers

---

### Post by mssm on 2006-01-25
I have success at last :)  

I can ftp from the machine itself and from another computer inside home on the same network. The actual test whether I can access it from outside, will be done tomorrow. But I am hopeful that I shall succeed. ([COLOR="Lime"]Update : Now I can access it from outside; see my next post below[/COLOR]).

Thanks Frodon and everybody else in this forum. I am a longtime reader of this great howto thread and this my first post. For my research collaboration I made a plan to run a ftp server on my home laptop. Since I using a cable modem(Motorola SBG 900E), I am behind the firewall of the router. I faced all kind of problems similar to Steve_250 of this thread. Initially I had 530 error related to password, I had error 500 for invalid port etc etc. I would like to share how I did overcome all of these problems.

1. I followed Frodon's how-to in toto. I didn't use gproftpd. I just copied and pasted his proftpd.conf with few exceptions, e.g. I put AuthAliasOnly to ``off''. Since I am behind a firewall of the router and my ISP provided me with dynamic IP address, I had to install ddclient first and registered my computer at dyndns.com. Then I had to add two lines related to MasqueradeAddress and PassivePorts, as Frodon mentioned, at the end of the file. Finally, I attached two lines as jinc1 suggested. I attached the copy of my proftpd.conf.

2. Next I added the users from the command line but their passwords were added NOT from the command line but from the tool Ubuntu provided : Kmenu --> System --> User Groups(I'm running Kubuntu. Under Gnome I think it's under System). This is fairly easy to do. I checked that everything is consistent with other commands that Frodon's guide provided, e.g. no users get a shell(/bin/false). If I issue the passwd of the users from command line, somehow all the time I got 530 error.

3. Next thing was to configure my router. First, I made sure that my ISP do not block the ports 1980 and the ports 60000-65535. The former is used by proftpd and the latter are the passive ports. Now the firewall and port forwarding config. of my router looks like this :

Firewall
--------

Port ID            : proftpd       
Enable             : yes(tick)
Allowed Protocol : TCP
Allowed Range   : 1980:1980
Allow Inbound    : Yes
Allow Outbound   : Yes
Protocol #           : 0

Similarly I defined another Port ID : proftpd-passive. For this, the allowed range is 60000:65535 and all other parameters remaining exactly the same.  

The names of the Port ID can be anything. 

Port Forwarding
-----------------

Name                : proftpd
Port Start           : 1980               
Port End             : 1980
LAN IP Address    : 192.168.0.10
Enable                : yes

Similarly, I define another port called profptd-passive for which Port Start =60000 and Port End = 65535, and all other parameters remaining the same.
Here 192.168.0.10 is the internal LAN IP address assigned to my laptop by the router dynamically(using DHCP). Since my laptop remains on all the time I didn't go for a static address, though I recommend others to do so.

That's it. If I don't forward all the ports including the passive one I shall get error 500 or the infinite time loop which Steve_250 experienced. I can access it from a Windows machine within the same network, using WS_FTP.

---

### Post by frodon on 2006-01-25
Hey mssm

A BIG BIG thank you for this post, really useful, i will put a link to this post in the guide.
Thanks for sharing your experience ;)

---

### Post by mssm on 2006-01-26
[QUOTE=frodon]Hey mssm

A BIG BIG thank you for this post, really useful, i will put a link to this post in the guide.
Thanks for sharing your experience ;)[/QUOTE]


Thanks Frodon. It's working from browser(e.g. firefox) also. I can also access it from outside.

---

### Post by t0bb3 on 2006-01-30
I'm having problems accessing my ftp server from outside the lan. I always get this error: "500 Illegal PORT command".
I have forwarded the neccessary ports in my router. I confirmed this by setting Apache to listen to one of the ports in the interval, and I could access it.

I have also added the MasqueradeAddress, PassivePorts, UseReverseDNS and IdentLookups options to proftpd.conf

What else should I do?

The ftp server works great inside the lan, both in active and in passive mode

---

### Post by mssm on 2006-01-31
[QUOTE=t0bb3]I'm having problems accessing my ftp server from outside the lan. I always get this error: "500 Illegal PORT command".
I have forwarded the neccessary ports in my router. I confirmed this by setting Apache to listen to one of the ports in the interval, and I could access it.

I have also added the MasqueradeAddress, PassivePorts, UseReverseDNS and IdentLookups options to proftpd.conf

What else should I do?

The ftp server works great inside the lan, both in active and in passive mode[/QUOTE]

Hi t0bb3, did you opened all the relevant ports like 1980 and passive ones in your firewall? Allow both incomin and outgoing and the protocol should be TCP. Make sure your ISP do not block any of these ports. Many ISPs block  some of them in order that nobody can run server from home.

Did you create password for the user using the GUI ubuntu provide?

Another point : did you put AuthAliasOnly to off, like mine? Can you do one thing? Just back up your copy of proftpd.conf and use mine instead and tell me whether you are getting the same result? I am telling you all these since I got this 500 error:illegal ports infinite number of times before getting it working. Good luck

---

### Post by t0bb3 on 2006-02-01
[QUOTE=mssm]Hi t0bb3, did you opened all the relevant ports like 1980 and passive ones in your firewall?[/quote]
What is port 1980? Yes, I have all the passive ports open.
[QUOTE=mssm]Allow both incomin and outgoing and the protocol should be TCP. Make sure your ISP do not block any of these ports. Many ISPs block  some of them in order that nobody can run server from home.[/quote]They are open both ways, and if I run my webserver on one of the ports I can connect to it, so they aren't blocked by my ISP
[QUOTE=mssm]Did you create password for the user using the GUI ubuntu provide?

Another point : did you put AuthAliasOnly to off, like mine?[/quote]I don't think there is anything wrong with the passwords. All accounts work when I try them in my lan, and they work if I connect to them in active mode from the outside.[QUOTE=mssm]Can you do one thing? Just back up your copy of proftpd.conf and use mine instead and tell me whether you are getting the same result? I am telling you all these since I got this 500 error:illegal ports infinite number of times before getting it working.[/quote]Yes, I will try that. [QUOTE=mssm]Good luck[/QUOTE]Thanks, I will need it :)

---

### Post by t0bb3 on 2006-02-01
I saw in your config file that you use port 1980 as your ftp port... I use another port, but yeah, that port is open and forwarded in my router.

I have also tried your config file (with the needed changes). Got the same 500 error :(

---

### Post by mssm on 2006-02-02
t0bb3, just to make sure :
1) Did you check that your internal IP address didn't change meanwhile?
2) If your ISP provide you with a dynamic IP address, your fwding to some dynamic dns host like dyndns.org by some client and that client is running?
3) Did you try to ftp on the same machine and still you are getting 500 error?
4) If you turn on logging, what do they say?

I am sure this has to do with your router's firewall and port forwarding config.

---

### Post by t0bb3 on 2006-02-03
1) I have static IPs in my lan, so it didn't change
2) Yes, I get a dynamic IP from my ISP, and yes I use dyndns.com. My router has built in support for updating dyndns, so it is always up to date. Everyone can connect to the webserver I've got running on the same machine as the ftp server, so the address isn't a problem
3) What do you mean? I can connect to the ftp server from all computers in my lan, and active connections from internet works.
4) I've got logging on. What should I look for?

First I could only connect to the ftp server from the other computers in my lan using the internal IP, but when I added "AllowForeignAddress on" I could also connect to the server using my dyndns.com address from within my lan. (I used to get the 500 error when I tried that). But other ppl can't connect over the internet. But they don't get error 500 any more, now they get "Unknown error"...

Thanks for helping

---

### Post by t0bb3 on 2006-02-03
A little more info on what is going on now when I try to connect... (I actually got a real error message this time)
```
ftp> open address port
Connected to address
220 ProFTPD 1.2.10 Server (t0bb3's ftp) [Ip.address]
Name (address:local user): ftp login name
331 Password required for ftp login name.
Password:
230 User ftp login name logged in.
ftp> dir
200 PORT command successful
425 Unable to build data connection: Connection timed out
```

---

### Post by Orunitia on 2006-02-04
Real nice, thanks. gproftpd really helped me. I've been looking for something as good as bulletproof, and this is good enough for me.

---

### Post by Stormx on 2006-02-04
Password incorrect, all the time.

I've followed the steps exactly.

Looking up localhost
Trying localhost.localdomain:1980
Connected to localhost:1980
220 you're at home
USER sauron

331 Password required for sauron.
PASS xxxx
530 Login incorrect.
Disconnecting from site localhost

---

### Post by Orunitia on 2006-02-05
Is there any way to make it so that I can let the people logging in put their name for the username, and just have a set password?

---

### Post by frodon on 2006-02-05
[QUOTE=Stormx]Password incorrect, all the time.

I've followed the steps exactly.

Looking up localhost
Trying localhost.localdomain:1980
Connected to localhost:1980
220 you're at home
USER sauron

331 Password required for sauron.
PASS xxxx
530 Login incorrect.
Disconnecting from site localhost[/QUOTE]Re-create your user with the GUI if you used the command line to create it and check that the name of the directories you use for the FTP server are good in your system and in your config file, the 530 error is just a small configuration problem (wrong path names, password issues, ...). Don't forget to have a look in the hoary thread which contain a lot of support (link at the top of the first post).

---

### Post by makisupa123 on 2006-02-08
Great Howto....I've using it for months.  I installed gproftpd about a month ago and everything was fine...good for easy admin of the server.  Then, all the sudden (noticed it after installing 3ddesk, which i've since removed), gproftpd started segmentation faulting when running it as root.  I can run it as a user but that does me little good -- understandandably, you cant do much as a user.  I uninstalled everything, wrote a new config file, tried changing theme info for root (its caused problems before), but i cant get it to run as root again.  Wierdness...anyone got any ideas?  I'm stumped....

Thanks,

Mak

---

### Post by Murmeldjuret on 2006-02-08
I get this error when I try to connect the server. 

```
 - getaddrinfo 'ftp://guldkant.mine.nu' error: Name or service not known
 - Fatal: Bind: : unable to resolve "ftp://guldkant.mine.nu" on line 6 of '/etc/proftpd.conf'

```
what have I done wrong?

---

### Post by frodon on 2006-02-08
Could you post your proftpd.conf file ?

It sounds like a domain name problem.

---

### Post by mssm on 2006-02-08
Frodon, I would like to add myself as an ftp user who can browse all directories. What should I do? Thanks in advance

---

### Post by frodon on 2006-02-08
Well, all the security of this guide is based on the FTP-shared directory because all is lock in this directory and therefore you're sure that nobody will go outside this directory.
There are different ways to do that. What i would do if i was you is to add your user or create a new one (maybe better because you will not use you user password which may be the same one than you use for sudo ... up to you).
So just add a line for your user : ```
#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
**AllowUser Your_user**
DenyALL
</Limit>
```Create a directory under FTP-shared called my_root for exemple and give it the good rights (755 for a download only directory and 777 for a download/upload directory).
Then add a section at the end of the file like that for a download only directory : ```
<Directory /home/FTP-shared/my_root/*>
Umask 022 022
AllowOverwrite off
       <Limit ALL>
		Order Allow,Deny
		AllowUser **your_user**
		Deny ALL
	</Limit>
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>
```All the ftp users will see this directory but they won't be able to list or access it.
Then all you have to do is to mount in this directory the directory or the partition you want, there's some explainations on how to do it at the end of the guide (you could add a line in fstab if you want to do it on startup).

---

### Post by Murmeldjuret on 2006-02-08
ServerType standalone
DefaultServer on
Umask 022
ServerName "ftp://guldkant.mine.nu"
ServerIdent on "guldkant"
Bind "ftp://guldkant.mine.nu"
ServerAdmin [email]xxxxxxx@hotmail.com[/email]
IdentLookups off
UseReverseDNS off
Port 22
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
User oscar
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on

---

### Post by frodon on 2006-02-08
Be careful that your server name should be as simple as possible, some characters may create some problems, is it the whole configuration file ?

---

### Post by jackmacokc on 2006-02-08
Hello frodon,

First off - as everyone has pointed out - excellent howto. I at first tried the gproftpd gui option, but wasnt all that impressed and decided to go the other option. After some tinkering, reading, and time - I am successfully connecting to my home box from work right now. My only problem is that I'm having trouble with PASV. I can't seem to get it to work. Is there anything special you've seen to getting PASV to work? I specified PassivePorts 60000 60049 in my proftpd.conf and forwarded those ports to my internal IP on my router. I'm also masquerading my external IP. 

Like I said, all works fine in active mode, but I'd like to get passive mode working properly. Any ideas would be much appreciated. Thanks!

---

### Post by trinaryouroboros on 2006-02-17
[QUOTE=frodon]Be careful that your server name should be as simple as possible, some characters may create some problems, is it the whole configuration file ?[/QUOTE]

I'm jammed here.

I'll be upfront, I have two dyndns configurations. One which is sub'd off my main web host, and another with gotdns.com just in case.

I'm only using the masqueradeaddress as the one i'm technically using with filezilla, which is only specified as the main web host address.

On the lan, by IP address I don't even need to worry about passive mode, goes right on through. Logs in just the way I want it to for each user.

When trying from the LAN through the web address, I get:

Response:	500 Illegal PORT command
Error:	Could not retrieve directory listing

When trying from LAN to web address using PASV:

Response:	200 Type set to A
Command:	LIST
Error:	Disconnected from server
Error:	Could not retrieve directory listing
Error:	Timeout detected!

FTP from win32 command prompt results in a 425 error, when going through web address and typing "ls" as usual. So it leads me to believe something is silly with the PASV mode set up. The specified port ranges are opened on the router by the way.

I must have made a mess somewhere, but I'm running out of ideas. I included my proftpd.conf file which I'm sure will seem a bit sloppy.

I'm hoping someone will show me the light here. I really should be able to use the web address to do this, whether inside my LAN or not.

:-k

edit: I've tested inbound works perfectly fine, I guess I'll just deal with the provided setup as is.

---

### Post by Turtle.net on 2006-02-18
Hi,
My FTP server is up and running.
I can access it from outside and I can browse the folders.
I tried to mount a folder in my /home/FTP-shared/download but i've got the error 
```
$ sudo mount -o Photos /home/FTP-shared/download/
mount: can't find /home/FTP-shared/download in /etc/fstab or /etc/mtab
``` Then I created a folder
```
$ sudo mkdir /home/FTP-shared/download/Photos
``` and I created a permanent entry in my fstab as proposed in this howto.
I can browse this folder, but I'm unable to download a file from my ftp server....

Any help ??

---

### Post by frodon on 2006-02-19
Is it a typo ? the command is : ```
sudo mount -o **bind** Photo_directory_path /home/FTP-shared/download
```I think it's not needed to create a Photos directory under download if what you want is only to mount your photo directory in /home/FTP-shared/download.

If you're still not able to download in this directory post your proftpd.conf file and check that you put the good rights on this directory because proftpd won't overwrite the system rights you set on this directory.

---

### Post by darkraver on 2006-02-24
need some help ... :-k 

i have 2 diferent users to get in 2 diferent directories

"/home/shared"

and other to 

"/online/forum/"

the problem is that both of then enter in the same directory :| ...

user1 i created it like 
useradd user1 -p passuser1 -d /home/shared -s /bin/false

and user 2
useradd user2 -p passuser2 -d /online/forum -s /bin/false

config lines:
```

...
...
...
# Set /home/FTP-shared directory as home directory
# DefaultRoot /home/FTP-shared
DefaultRoot ~

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~
...
...
...
<Directory /home/shared/*>
Umask 022 022
AllowOverwrite on
        AllowUser user1
</Directory>

<Directory /online/forum/>
Umask 022 022
AllowOverwrite on
        AllowAll
</Directory>

```

so 1 want 1 user to access both directorys and the other only to 1 ... if possible or each user for each directory ...

can anyone help me ? ;)

---

### Post by frodon on 2006-02-24
The command *DefaultRoot ~* define the user home directory as home directory for the FTP, so each user will be locked in his home directory thanks to this command, so the way you use sounds good but i never used it so i don't know if it works but it should.

Add a section like that before setting the directories : ```
#VALID LOGINS
<Limit LOGIN>
AllowUser user1
AllowUser user2
DenyALL
</Limit>
```Thus you will be sure to allow only your 2 users to login.
Try to modify your directory section like that : ```
<Directory /home/shared/*>
Umask 022 022
AllowOverwrite on
       <Limit ALL>
		Order Allow,Deny
		AllowUser user1
		Deny ALL
	</Limit>

       <Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

<Directory /online/forum/>
Umask 022 022
AllowOverwrite on
       <Limit ALL>
		Order Allow,Deny
		AllowUser user2
		Deny ALL
	</Limit>

       <Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
</Directory>

```I assume that your directories are upload/download directories and therefore you gave 777 rights to them.

However, you can use also the way i gave in [this post]("http://www.ubuntuforums.org/showpost.php?p=715548&postcount=99") and then keep the guide spirit with the home/FTP-shared home directory for all the users and allow the user you want to enter in the directory you want. After that you can mount the directory you want in home/FTP-shared/upload, create more directories if you need.

Let me know if it works, i'm curious.

---

### Post by darkraver on 2006-02-24
ok so far so good ... i've changed something ... and now directory's work fine each user can enter in diferent directory.

user1 -> directory1
user2 -> directory2

the changes:

the Valid logins section was already there so no changes there

```

<Directory /home/shared/*>
Umask 022 022
AllowOverwrite on
       	**AllowAll**
</Directory>

<Directory /online/forum/>
Umask 022 022
AllowOverwrite on
      	**AllowAll**
</Directory>

```

and now they both enter in diferent directory's :)
1º move ok \\:D/ 

now the 2º fase :P ... i was thinking arround and it seems to be impossible to 1 of those users to access diferent directory's since i've defined when creating them their "home" directory, since in config i'm forcing them to be in their home directory it's gome be a bit hard :| ...

---

### Post by Tichondrius on 2006-02-24
Why not just install SSH server ?

---

### Post by souteneur3190 on 2006-02-24
What am i doing wrong

- no such group 'nobody'
 - Fatal: Group: Unknown group 'nobody'. on line 20 of '/etc/proftpd.conf'

what group should it be?

---

### Post by Turtle.net on 2006-02-26
First of all thanks for your answers
[quote=frodon]Is it a typo ? [/quote]
Yes it is :-?
[quote=frodon]If you're still not able to download in this directory post your proftpd.conf file and check that you put the good rights on this directory because proftpd won't overwrite the system rights you set on this directory.[/quote]
You were right :) I changed the permission of each file in the subdirectories I attached and now I am able to download the files without a single problem.

Thanks again for your great howto and support \\:D/

---

### Post by SSamiK on 2006-03-08
How do i add more users? :confused:

---

### Post by frodon on 2006-03-08
Create a new user thanks to the "user & group" windows like for userftp in the guide then add an alias line at the beginning of your proftpd.conf file : ```
UserAlias aliasname newuser
```Then add a line in the limit login section : ```
<Limit LOGIN>
AllowUser userftp
**AllowUser newuser**
DenyALL
</Limit>
```By the way, no problem if several friends try to login at the same time with the same user, it's allowed and controlled by this line : ```
MaxClientsPerUser 8
```

---

### Post by SSamiK on 2006-03-08
Thanks. :-D 
Worked like a charm! 
Been really helpfull this thread so once again, thanks! \\:D/

---

### Post by SSamiK on 2006-03-10
While i'm at it... :rolleyes: 

Been trying to get Passive to work, since most (?) clients seem to use is by default, and the more unexperienced users who don't know their client can't connect. I've tryed adding the line "PassivePorts 49152 65534" and opened the ports in my router, but still it seems that users who try connect using passive gets disconnected while trying to list the directories.

Any clues?  :confused:



EDIT: Got it working after rebooting the router.

---

### Post by zino1 on 2006-03-21
I am new to Ubuntu and I tried to install proftpd and got this;

sudo apt-get install proftpd

"Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package proftpd"

I downloaded it from [http://www.proftpd.org/goals.html](http://www.proftpd.org/goals.html) as a .tar.gz and uncompressed it into my home directory. I ran the install command from my home directory.

What am I doing wron?

---

### Post by Turtle.net on 2006-03-21
You have to add extra repositories in synaptic to have this kind of software ready to be installed.
Have a look to [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php) and [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) for more explanations :)

---

### Post by zino1 on 2006-03-23
I have proftp installed now... I have followed the how to on the first page. all seemed to have gone well.

Yet I am unable to ftp into this box using any ftp program.

I am behind a router. Is there anything I need to do for that?

---

### Post by zino1 on 2006-03-23
[QUOTE=zino1]I have proftp installed now... I have followed the how to on the first page. all seemed to have gone well.

Yet I am unable to ftp into this box using any ftp program.

I am behind a router. Is there anything I need to do for that?[/QUOTE]


Here is my proftpd.conf file:



etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

ServerName			"Zino"
ServerType			inetd
DeferWelcome			on

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer		600
TimeoutStalled			100
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

DenyFilter			\*.*/

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd		off

# Uncomment this if you would use TLS module:
#TLSEngine 			on

# Uncomment this if you would use quota module:
#Quotas				on

# Uncomment this if you would use ratio module:
#Ratios				on

# Port 21 is the standard FTP port.
Port				1980

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			8

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

#   # Limit the maximum number of anonymous logins
MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default. 
#DelayEngine 			off

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#
#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
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

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

---

### Post by frodon on 2006-03-24
I strongly advice to run proftpd as standalone so replace the line : ```
ServerType inetd
```by : ```
ServerType 	standalone
```Then if you are behind a router you will need to set MasqueradeAddress and PassivePorts following the link i gave in the misc section : [http://www.proftpd.org/localsite/Userguide/linked/x862.html](http://www.proftpd.org/localsite/Userguide/linked/x862.html)
You will need also to forward the ports you use for the ftp serveur in you router configuration.
You should also read this post : [http://www.ubuntuforums.org/showpost.php?p=680702&postcount=81](http://www.ubuntuforums.org/showpost.php?p=680702&postcount=81)

By the way, I'm wondering if i should add that in the guide itself and not in the misc section because many users have a router and sometimes they don't read the misc section which contain those informations. 
So should i add the router things in the guide itself instead of the misc section ?

---

### Post by zino1 on 2006-03-24
[QUOTE=frodon]I By the way, I'm wondering if i should add that in the guide itself and not in the misc section because many users have a router and sometimes they don't read the misc section which contain those informations. 
So should i add the router things in the guide itself instead of the misc section ?[/QUOTE]

As you can tell I am no export in this OS, but I am sure it would help many of us newbie's if it was.

Thank you for you assistance, I will research those links today.

---

### Post by Snugglej on 2006-04-04
Hello,

I'm a real newbie at this stuff. I just started and I decided to use the GUI to set up the FTP for me. 

I'm behind a router, I have all the forwarding ports (60000 - 65534) passive and  (77) ftp set up. I have set all the folders to what was stated in the begining of this how to.

I go to [ftp://myhost:77](ftp://myhost:77) and I can log in fine and the gui shows that I have logged in but I don't get a response from the ftp for the files... i have folder in there to test.

The response I get is that it puts me in the current directory "/" 
TYPE A
PASV
227 Entering Passive Mode (69,17,133,157,253,50).
Opening Data connection to 69.176.133.157 Port:64818
LIST -aL
A connection attempt failed because the connected party did not respond.
Timeout (40s).
Client Close Connection

Please help me... 
I tried what had been said earlier but i got confused
I let the gui set up the proftpd.conf.

---

### Post by frodon on 2006-04-04
If you are really accessing the "/" directory (your ubuntu partition) the LIST command will surely fail because of rights. Indeed you can access and list directories only if you have rights for it.
So my first advice would be to be sure that the directory you access when you login (set a good home directory not "/") the FTP server has the good rights (755 for a download directory).

---

### Post by Snugglej on 2006-04-04
[QUOTE=frodon]If you are really accessing the "/" directory (your ubuntu partition) the LIST command will surely fail because of rights. Indeed you can access and list directories only if you have rights for it.
So my first advice would be to be sure that the directory you access when you login (set a good home directory not "/") the FTP server has the good rights (755 for a download directory).[/QUOTE]

I looked at my settings and none of them are set to go to directory "/".

I am going to provide what config my gproftpd-8.2.2 has and maybe you can tell me if it is in there that something is set wrong.
I am using a netgear router, and I have all the ports forwarded as it does connect and verify the password and username.
If there is anything I need to do I will appreciate the help.

ServerType standalone
DefaultServer on
Umask 022
ServerName "192.168.1.4"
ServerIdent on "Richards Server"
Bind "192.168.1.4"
ServerAdmin [email]RichardGiesige@hotmail.com[/email]

IdentLookups off
UseReverseDNS off
Port 77
PassivePorts 60000 65534

MasqueradeAddress 69.176.133.157

TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
User snugglej
Group adm
DirFakeUser off nobuddy
DirFakeGroup off nogroup
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 30
TransferRate STOR 40
TransferRate STOU 40
TransferRate APPE 40

SystemLog /var/log/secure
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_root_path /home/FTP-shared
#gp_useradd_upload_path /upload
#gp_html_path /var/www/ftp.html
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
</IfModule>

<Limit LOGIN>
  AllowUser snugglej
  AllowUser ftp
  DenyALL
</Limit>


<Anonymous /home/snugglej>
User snugglej
Group snugglej
AnonRequirePassword on
MaxClients 3 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
AllowOverwrite off
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
<Limit ROOT_DIR_ALLOW RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit ROOT_DIR_DENY DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
 DenyAll
</Limit>
<Directory /upload>
AllowOverwrite on
<Limit UPLOAD_DIR_ALLOW LIST NLST  STOR STOU  APPE  RETR  MKD XMKD  SITE_CHMOD  SITE_CHGRP  STAT  MDTM  PWD XPWD  SIZE  CWD XCWD  CDUP XCUP  SITE >
 AllowAll
</Limit>
<Limit UPLOAD_DIR_DENY RNFR RNTO  DELE  RMD XRMD >
 DenyAll
</Limit>
</Directory>
</Anonymous>

<Anonymous /home/FTP-shared>
User ftp
Group userftp
AnonRequirePassword on
MaxClients 3 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
AllowOverwrite off
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
<Limit ROOT_DIR_ALLOW RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit ROOT_DIR_DENY DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
 DenyAll
</Limit>
<Directory /upload>
AllowOverwrite on
<Limit UPLOAD_DIR_ALLOW LIST NLST  STOR STOU  APPE  RETR  MKD XMKD  STAT  MDTM  PWD XPWD  SIZE  CWD XCWD  CDUP XCUP  SITE >
 AllowAll
</Limit>
<Limit UPLOAD_DIR_DENY RNFR RNTO  DELE  RMD XRMD  SITE_CHMOD  SITE_CHGRP >
 DenyAll
</Limit>
</Directory>
</Anonymous>

---

### Post by Snugglej on 2006-04-04
Okay I finally got it to work, all along it was my fault because I had firestarter running on Ubuntu and it was blocking the ports to the passive mode.

Once I enabled the ports by setting inbound allow traffic for ports 60000 and 65000 it worked like a charm!

so if anybody has this problem where they can't connect because it freezes at the locating files check if you have firestart or some sort of firewall installed on ubuntu.

*NEW PROBLEM*
But now i run into the problem where I try transfer something and I get Transfer Failed.
I'm trying to upload into the upload file but it's not working any ideas?? 
Rich.

---

### Post by frodon on 2006-04-05
hi Snugglej, glad to know that you solved your first problem.

In which directory do you get this error ?
If it's /home/FTP-shared, run this command : ```
sudo chmod 777 /home/FTP-shared
```You have to know that proftpd don't overwrite the system rights and therefore if the system rights are too restrictive you won't be able to upload even if you've well set your FTP server.

---

### Post by animesh on 2006-04-11
i was trying to add more user accounts with different usernames and passwords using conf files given in this thread. Also i don't know where to give passwords.....i have been trying to configure proftpd for a long time but could get only one account working that too anonymous...now when i tried again to introduce new users i am stuck........ 

How do i add more than 1 user with diff username and passwords

Searched the net ......the proftp guide itself is very confusing....put in a lot of fight with no results.....](*,) ](*,) ](*,) ](*,) ](*,) :( :( 

Please help me to configure proftpd

```

#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 
AuthAliasOnly                   on
UserAlias Junta userftp
UserAlias UPLOAD userftp1


ServerName			"BATMAN'S DEN"
ServerType			standalone
DeferWelcome			on

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer		40
TimeoutStalled			100
TimeoutIdle			40

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/
DefaultRoot                       ~

AllowStoreRestart		on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd		off

# Uncomment this if you would use TLS module:
#TLSEngine 			on

# Uncomment this if you would use quota module:
#Quotas				on

# Uncomment this if you would use ratio module:
#Ratios				on

# Port 21 is the standard FTP port.
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			10

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
#DelayEngine 			off

MaxClientsPerUser 5
AccessGrantMsg "Welcome to BATMAN'S DEN"

DefaultRoot /home/ftp

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp userftp1 
DenyALL
</Limit>



<Directory /home/ftp/Junta/*>
Umask 022 022
AllowOverwrite off
<Limit ALL>
		Order Allow,Deny
		AllowUser userftp 
		Deny ALL
	</Limit>
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/ftp/Upload/>
Umask 022 022
AllowOverwrite on
 <Limit ALL>
		Order Allow,Deny
		AllowUser userftp1 
		Deny ALL
	</Limit>
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

```

---

### Post by frodon on 2006-04-12
Your proftpd.conf file looks good, create your new user using the GUI, the password for the user is always the password you set when you created the user, and the username you use to login the FTP server is the alias you set in the proftpd.conf file.
What meassage error do you get with the user who don't work ?

---

### Post by RdM on 2006-04-13
Thanks. This was really useful. I finally got everyting to work.

---

### Post by slapper on 2006-04-15
H all!! this is my firts post here!!

I am trying to set up my proftpd server according to this howto.
Because i am newbie in linux world and espesially in proftpd i have some problems.

I followed the howto everything seems nice but i can not log in to my ftp server,neither from the same machine nor from my win pc.Always the same error 
(530 Login incorrect).

i have add two user one is userftp  the other is student.I follow the same command(sudo useradd userftp -p your_password -d /home/FTP-shared -s /bin/false).I dont want to install gui in my server so is it possible to create these  users in a other way??
One more i dont understand what is the useralias

Thanks a lot guys!!!!:D :D 

AA here is my proftpd.conf file


> 
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias student userftp

ServerName			"Miltos ftp server"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
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

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>


---

### Post by frodon on 2006-04-15
Hi slapper,

Some users reported me that the useradd command creates sometimes 530 error because of the password, so i advice you to re-create the users using the GUI tools (system > administration > user & group), you could try also this command it worked for some users : ```
sudo passwd userftp
```and then type the password you want to set for userftp again and do the same for your other user, it will just re-create the password.

However when i have a look in your proftpd.conf file there is a problem, do you really want 2 different users for your ftp server ? if yes you should modify those lines like that : ```
# Choose here the user alias you want !!!!
[B]UserAlias user1 userftp
UserAlias user2 student[/B]
...
..
.
#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
**AllowUser student**
DenyALL
</Limit>
```Why useralias ?
I use useralias in my guide because this tip prevents telnet access to your FTP server and therefore increase the security of your server.
So you always use the alias name to login your server even if the users is called userftp.

Feel free to require more details/help ;)

---

### Post by slapper on 2006-04-15
Frodon thanks for the quick answer!!!!!!!

I tried what you said but nothing happen.The same problem..:-k :-k 

Anyway im going to install gnome and create these users from there.
I will keep you inform..:D 

Thanks again for the response!!

---

### Post by frodon on 2006-04-15
The 530 error could also come from right problems for directories FTP-shared, FTP-shared/download and FTP-shared/upload. So check that the rights for those directories are good.

---

### Post by splendid on 2006-04-16
I tried installing.  Get this message after editing the proftpd.conf file

ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Ch eck your configuration.

Any suggestions on what I may have done wrong?  I am logged in as root, and did follow directions.

Thanks,

---

### Post by frodon on 2006-04-17
Try to re-install proftpd and/or post your proftpd.conf file in your next post, however this could come from the *ServerType* line in the proftpd.conf file : ```
ServerType 			standalone
```You should have this line in your proftpd.conf file.

---

### Post by splendid on 2006-04-17
Attached is my proftpd.conf file

#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

ServerName                      "basement"
ServerType                      inetd
DeferWelcome                    off

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    on

TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                     "-l"

DenyFilter                      \*.*/

"proftpd.conf" 103L, 2829C                                    1,1           Top

---

### Post by frodon on 2006-04-18
ok, change : ```
ServerType inetd
``` by ```
ServerType standalone
```And it should be good.

---

### Post by splendid on 2006-04-19
Frodon, Great that worked.  I am trying to install the GUI now.  Where do I need to edit the .bashrc file.  Where should I enter that path with ProfFtpd?


Then add these lines in your .bashrc (it's in your home directory : gedit /home/username/.bashrc) file in order to specify what is the ProftpTools directory path, YOU MUST REMOVE THE "/" CHARACTER at the end of the path. I give you an exemple if your ProftpTools directory is in your home directory :

Thanks so much for your help.

---

### Post by frodon on 2006-04-20
To open the .bashrc file : ```
cd
gedit .bashrc
```When the file is opened add the lines in like the guide says, for exemple if your PtftpdTools directory is in your home directory the lines to add would be : ```
ProftpTools_dir=/home/splendid/ProftpTools-v1.0.1
export ProftpTools_dir
```
I know it's not a really elegant way to install a script, but that's the best solution i found to set my script quickly. If i get time i will try to find an easier way than editing the .bashrc.

---

### Post by Nordoelum on 2006-04-21
How to make it work like a ftp client connect to an web server?

---

### Post by splendid on 2006-04-22
Frodon,

Attached is my .bashrc file.  I think I may have screwed something up because when I enter ProftpTools from a terminal window, nothing happens.  I put my entry in Bold (see below).
Thanks So much for your help.  I was just able to get my printer working this morning.  Took a couple days, but everyone on this forum like yourself has been real helpful.


 ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

[B]ProftpTools dir=/etc/ProftpTools-v1.0.1
export ProftpTools_dir
[/B]
# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
#export HISTCONTROL=ignoredups

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" -a -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
".bashrc" 75L, 2291C                                          1,1           Top

---

### Post by frodon on 2006-04-22
It looks like a typo, the line : ```
ProftpTools dir=/etc/ProftpTools-v1.0.1
```should be ```
ProftpTools**[COLOR="Red"][SIZE="4"]_[/SIZE][/COLOR]**dir=/etc/ProftpTools-v1.0.1
```

---

### Post by splendid on 2006-04-22
Sorry, not sure how I missed that  _

Anyway, I fixed the .bashrc and then typed ProftpTools and I get message that say's bash: ProftpTools: command not found

Any ideas?

Thanks!

---

### Post by frodon on 2006-04-23
Did you put the ProftpTools file in /usr/bin ?
By the way you may have to restart your terminal to get it working.

The only thing that the Proftptools file do is to run the proftpd_tools.bash script  with gksudo, so the purpose of the ProftpTools file is just to lauch the proftpd_tools.bash script in a elegant way with sudo rights.

---

### Post by dnlninja on 2006-05-07
i am also getting the same errors as splendid

also ( i have been reading through most of the thread so hopefully this isnt a repeat but sorry if it is)
i know it's a pretty newbie question ( considering this would be my 3rd or 4th ftp i've setup) but i am having trouble getting my ftp visible outside of my private network.  my local ip address and networked computers can connect to it (i fixed the 530 errors myself that everyone seems to have gotten), but now my direct ip isnt seeing it.  

i've opened the ports and turned off my firewall.  i also have the passive/masqeruade on... is there something i am not thinking of?

i have a few things going odd, i edit the conf with gedit and when i  gproftpd into the program, it is offline and all the settings are off (such as the port is 0, passive ports are all wrong, download speed is 1, etc) but it recognizes that im using the conf...

---

### Post by apresvoop on 2006-05-13
Okay, I am at my wits end with this thing.  I spent the better part of six hours reading forum posts and going through config files to get this thing to work.  Finally I'm able to connect and all seems right.  I go off to eat, and when I come back, I can no longer log in.  Really.  I have installed a couple other things, like Conky,  AVG Anti-Virus, and dependencies, but that's about it.  And even then I'm 99% sure it was working after I did that.

I tried deleting and recreating the userftp account just to make sure that wasnt the issues (it was done in GUI not commandline).  Frankly I just don't know what else to do.  Nothing has changed in my config since the last time it worked.

It gives me the 530 Login Incorrect error.  I know the password is correct, and I know the alias names are correct, and I know the config is correct.  Here's my config file.  Hopefully someone can tell me what I'm doing wrong.

Does the home directory need to be chmod'ed to a particular access level?

---

### Post by frodon on 2006-05-14
apresvoop, check also the rights on the ftp user home directory because wrong rights there can generate the 530 error, the rights for a download directory shoud be 755 and 777 for an upload directory.
Your config file seems good so i think about a privilege problem on the home directory.

---

### Post by apresvoop on 2006-05-14
Yes, you were right.  The permissions were slightly off.  Thanks.

---

### Post by NeoGreen on 2006-05-25
Need help, Ive tried to install proftpd by sudo apt-get install proftpd and I get this error message:
root@neoserver1:/# apt-get install proftpd
[B]Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package proftpd[/B]

I then tried the wget command (wget [http://frodubuntu.free.fr/ubuntu/gproftpd-8.2.2_8.2.2-1_i386.deb](http://frodubuntu.free.fr/ubuntu/gproftpd-8.2.2_8.2.2-1_i386.deb)
sudo dpkg -i gproftpd-8.2.2_8.2.2-1_i386.deb) and I get this message:

root@neoserver1:/home/admin#
wgethttp://frodubuntu.free.fr/ubuntu/gproftpd-8.2.2_8.2.2-1_i386.deb
--16:39:55--  [http://frodubuntu.free.fr/ubuntu/gproftpd-8.2.2_8.2.2-1_i386.deb](http://frodubuntu.free.fr/ubuntu/gproftpd-8.2.2_8.2.2-1_i386.deb)
           [B]=> `gproftpd-8.2.2_8.2.2-1_i386.deb'
Resolving frodubuntu.free.fr... failed: Temporary failure in name resolution.[/B]

Is there something I am doing wrong????](*,)

---

### Post by frodon on 2006-05-26
You need proftpd to install gproftpd so without proftpd installed you won't be able to install gproftpd.
I think you don't have all the repositories enabled, see this post to check that you have all the repositories enabled then open synaptic and perform a refresh : [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by NeoGreen on 2006-05-26
I went into synaptic manager and installed proftpd because it wasn't installed.  Will that help?  I don't know to much about repositories and last time a messed around with them I had to do a clean install.  Is a site of link where I can go to learn about repositories and their functions?:)

---

### Post by mumushi on 2006-05-27
i read your howto on setting up ftp server. thanks alot i did set it up correctly. my problem is how can i test it? its my first time to set up a ftp server. how can my friends access my server? what would e the command? thank you so much in advance.

---

### Post by Griff on 2006-05-28
I installed gproftpd/proftpd a long time ago (few months ago) using your excellent howto.  If I open up the gui using sudo the gui just freezes.  (I did have a shortcut button using gksudo).  As such I was forced to just open the gui without sudo and this doesn't allow me to view the security log file.  Guess the big question is:
Why can I no longer open the gui using gksudo?

---

### Post by frodon on 2006-05-29
[QUOTE=Griff]I installed gproftpd/proftpd a long time ago (few months ago) using your excellent howto.  If I open up the gui using sudo the gui just freezes.  (I did have a shortcut button using gksudo).  As such I was forced to just open the gui without sudo and this doesn't allow me to view the security log file.  Guess the big question is:
Why can I no longer open the gui using gksudo?[/QUOTE]Really strange, did you try with sudo instead of gksudo ? Sorry i have no idea for the moment, anyway you need sudo rights for gproftpd if you want to handle the FTP server.

[QUOTE=NeoGreen]I went into synaptic manager and installed proftpd because it wasn't installed.  Will that help?  I don't know to much about repositories and last time a messed around with them I had to do a clean install.  Is a site of link where I can go to learn about repositories and their functions?:)[/QUOTE]Well, if you installed proftpd with synaptic it's ok because synaptic is just a front end for apt-get command lines.
This may help you to understand how to install things on ubuntu : 
[http://ubuntuforums.org/showthread.php?t=153118](http://ubuntuforums.org/showthread.php?t=153118)

[QUOTE=mumushi]i read your howto on setting up ftp server. thanks alot i did set it up correctly. my problem is how can i test it? its my first time to set up a ftp server. how can my friends access my server? what would e the command? thank you so much in advance.[/QUOTE]I advice you to test yourself your server to begin, use a FTP client to do that like gFTP, thus you will see if your server works.
Then once it's works with your computer ask a friend to login the FTP server with a FTP client for example (but you can do that with a web browser too).

---

### Post by Griff on 2006-05-29
[QUOTE=frodon]Really strange, did you try with sudo instead of gksudo ? Sorry i have no idea for the moment, anyway you need sudo rights for gproftpd if you want to handle the FTP server.
[/QUOTE]
Yes.  After finding out that my shortcut no longer worked I tried opening it up in the terminal using sudo.  It yields the same result.  The window comes up, blank, and never loads.  Then I have to force quit it.

---

### Post by mumushi on 2006-05-29
i started my ft p server by ht command "sudo /etc/init.d/proftpd start" but got this message:

Starting ProFTPD ftp daemon: Anthony-desktop - mod_delay/0.4: error opening DelayTable '/var/run/proftpd/proftpd.delay': No such file or directory
proftpd.

what seems to be wrong? Thank you so much for the help.

---

### Post by frodon on 2006-05-29
mumushi, i would re-install proftpd in that case, i've never got this kind of error and it looks quite weird, backup your config file somewhere before doing that.

---

### Post by mumushi on 2006-05-29
ok thanks for the tip. i will be doing that now and let you know what happens. ciao!

---

### Post by Griff on 2006-05-29
[QUOTE=Griff]I installed gproftpd/proftpd a long time ago (few months ago) using your excellent howto.  If I open up the gui using sudo the gui just freezes.  (I did have a shortcut button using gksudo).  As such I was forced to just open the gui without sudo and this doesn't allow me to view the security log file.  Guess the big question is:
Why can I no longer open the gui using gksudo?[/QUOTE]
Ok.  I fixed my problem.  I'm not sure why this works so maybe someone that knows more about this can explain it.  Opening with sudo/gksudo allows gproftpd to read/write to the secure file under /var/log.  I went to this file as root in nautilus to take a look at it.  I scrolled to the bottom lines (line 47,000+) and the last few entries looked ok.  I emptied the contents of the file to a backup file and erased everything in /var/log/secure.  Opening gproftpd as sudo now works.  I'll print the last few entries of the file if you would like to see it to see if maybe there was an entry that scewed things up.

---

### Post by mumushi on 2006-05-30
i tried reinstalling it but on the process i got this message:

ProFTPd warning: not start neither in standalone nor in inetd/xinetd mode, apparently. Check your configuration.

i followed the howto yet i always get this message. Any idea what's wrong? thanks for the help (^.^)

---

### Post by frodon on 2006-05-31
This sould be an error or typo in the proftpd.conf file, could you post it there ?

---

### Post by mumushi on 2006-05-31
[QUOTE=frodon]This sould be an error or typo in the proftpd.conf file, could you post it there ?[/QUOTE]

here is my proftp config file. i hope this helps in determining what went wrong. thanks!

---

### Post by frodon on 2006-05-31
All you need there is to replace this line : ```
ServerType 			inetd
```by : ```
ServerType 			standalone
```

---

### Post by mumushi on 2006-05-31
ok the error is gone now. thanks alot!

Now i would like to ask how to connect to my ftp server using a browser? using my settings you have seen in my config. thanks again for the help. :-D

---

### Post by frodon on 2006-05-31
Open a web browser and put that in the adress bar : ```
ftp://cych@your_IP:1980
```I'm not sure about the character ":" maybe it's a space instead.
But it's always better to use a ftp client like Gftp.

---

### Post by mumushi on 2006-06-01
i tried [ftp://cych@your_IP:1980](ftp://cych@your_IP:1980) but it doesnt work. i also tried [ftp://my_IP:1980](ftp://my_IP:1980) and still doesn't work so i installed gftp instead. my problem is i get confused. What will i put in the host area? my ip address? Please be patient with me its really my first time to set up a ftp server and use gftp :)

---

### Post by frodon on 2006-06-01
No problem mumushi,

In Gftp, for host put your IP address, for user put cych for port 1980 and for the password the one you chose.
Don't forget to paste the Gftp log if you get problems (maybe the 530 error).

---

### Post by red-i on 2006-06-01
Greetings.

I am very new to this and require some help with the fundamentals.

I have set it up so that the server works from within my network.
I can send and receive from another machine on my local network no problems.

I am now trying to get it to work from outside the NAT.
My Service provider has given me the IP of 196.211.152.206 to use to connect with, he is apparently forwarding calls made to this IP to my Ubuntu box who's IP on my local Network is 196.20.20.67 the IP of the router on my network is 196.20.20.1

When I try to connect to 196.211.152.206 using Gftp I get the following response

> Looking up 196.211.152.206
Trying 196.211.152.206:21
Cannot connect to 196.211.152.206: Connection refused
Waiting 30 seconds until trying to connect again

When I check my Config file this is the response I get:

> 
If there are no complaints the configuration is ok...
localhost.localdomain - 127.0.0.1:21 masquerading as 196.211.152.206
Check completed.

I dont know where it is getting the above IP 127.0.0.1 from, as it does not apear in the config file ??

here is my config file [ATTACH]10351[/ATTACH]

IF someone could check my config file and make sure i'm not missing the basics that would be great.
This is starting to take years off my life](*,) 

Thanks
Sean.

---

### Post by mumushi on 2006-06-01
[QUOTE=frodon]No problem mumushi,

In Gftp, for host put your IP address, for user put cych for port 1980 and for the password the one you chose.
Don't forget to paste the Gftp log if you get problems (maybe the 530 error).[/QUOTE]


I did what you have said and i know i input the correct pass but i got this message: 
```
Looking up 192.168.232.69
Trying 192.168.232.69:1980
Connected to 192.168.232.69:1980
220 you're at home
USER cych

331 Password required for cych.
PASS xxxx
530 Login incorrect.
Disconnecting from site 192.168.232.69
```

What possibly went wrong? i know i am that close into making this thing work. Thanks again!

---

### Post by frodon on 2006-06-01
Well the 530 error is a common error, it can com from rights problems on the FTP-shared, download or upload directory. I advice you to use the user&group GUI and try to change the password of the user, re-create it if needed but with the GUI.
If it still not working i will read again your config file but it seems ok.

---

### Post by red-i on 2006-06-02
Any assistance will be golden, I just cant seem to get this to work !

---

### Post by frodon on 2006-06-02
Did you read this post ? 
[http://www.ubuntuforums.org/showpost.php?p=680702&postcount=81](http://www.ubuntuforums.org/showpost.php?p=680702&postcount=81)

Sorry, i can't help you more because i'm not an expert about router things.

Maybe a thread in the server talk sub-forum will provide you the help you need.

---

### Post by LordMerlin on 2006-06-02
What do I need to change to allow each user to access his home folder?

---

### Post by CameronCalver on 2006-06-03
I have set up a ftp but when i go to login i dont no the name or password can some1 help me this is my conf

ServerType standalone
DefaultServer on
Umask 022
ServerName cameronsftp
ServerIdent on "My FTPD"
Bind "0.0.0.0"
ServerAdmin [email]suped_up_supra_01@hotmail.com[/email]
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
User cameron
Group cameron
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 30
TransferRate STOR 40
TransferRate STOU 40
TransferRate APPE 40
SystemLog /var/log/secure
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_root_path /home/ftp
#gp_useradd_upload_path /upload
#gp_html_path /var/www/ftp.html
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
</IfModule>
<Limit LOGIN>
  AllowUser cameroncalver
  AllowUser cameron
  DenyALL
</Limit>

<Anonymous /home/FTP-shared>
User cameroncalver
Group cameroncalver
AnonRequirePassword on
MaxClients 3 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
AllowOverwrite off
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
<Limit ROOT_DIR_ALLOW RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit ROOT_DIR_DENY DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
 DenyAll
</Limit>
<Directory /home/FTP-shared/linux.png/*>
AllowOverwrite on
<Limit UPLOAD_DIR_ALLOW LIST NLST MDTM SIZE SITE STAT APPE RETR STOR STOU MKD XMKD CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit UPLOAD_DIR_DENY DELE SITE_CHMOD SITE_CHGRP RMD XRMD RNFR RNTO>
 DenyAll
</Limit>
</Directory>
</Anonymous>

<Anonymous /home/FTP-sharedp>
User cameron
Group cameron
AnonRequirePassword on
MaxClients 3 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
AllowOverwrite off
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
<Limit ROOT_DIR_ALLOW RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit ROOT_DIR_DENY DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
 DenyAll
</Limit>
<Directory /home/ftp/upload/*>
AllowOverwrite on
<Limit UPLOAD_DIR_ALLOW LIST NLST MDTM SIZE SITE STAT APPE RETR STOR STOU MKD XMKD CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit UPLOAD_DIR_DENY DELE SITE_CHMOD SITE_CHGRP RMD XRMD RNFR RNTO>
 DenyAll
</Limit>
</Directory>
</Anonymous>

cameron@ubuntu:~$

---

### Post by CameronCalver on 2006-06-03
I fixed the problem

---

### Post by LordMerlin on 2006-06-04
Anyone?

---

### Post by frodon on 2006-06-05
LordMerlin, you want to use several users in your FTP server and you want that each of this user use its own home directory as FTP directory ?
It's not really secure, could you explain me why you want to do that and what you want to do and i will try to find a secure way to do that, if you agree obviously ;)

---

### Post by LordMerlin on 2006-06-05
No, I want each user (normal Linux user) to have access to his folder via FTP, can that be done?

---

### Post by frodon on 2006-06-05
Sure it can be done.
Creates one directory for each home user directory under FTP-shared. Then in your proftpd.conf add a section like that for each directory : ```
<Directory /home/FTP-shared/user1-homedir/*>
Umask 022 022
AllowOverwrite off
       <Limit ALL>
		Order Allow,Deny
		AllowUser user1
		Deny ALL
	</Limit>
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

```Also add each user in the *<Limit LOGIN>* section and create an alias for each one in the proftpd.conf file.
Then link the home directories in those created in FTP-shared like that : ```
sudo mount -o bind /home/user1 /home/FTP-shared/user1-homedir
```In the example i gave you you will only be able to download in these directories.

---

### Post by frodon on 2006-06-06
By the way, did some tried this guide with dapper ?

Thanks for the feedback.

---

### Post by z-vet on 2006-06-06
[QUOTE=frodon]By the way, did some tried this guide with dapper ?

Thanks for the feedback.[/QUOTE]
I did and have no problems with it. Thanks, frodon :)

---

### Post by LordMerlin on 2006-06-07
That's a lot of work just to allow each user FTP access to his home folder!!!
 
Isn't there any other FTP server I can use which is just plain straight forward?

---

### Post by frodon on 2006-06-07
I gave you a secure way to do it but there are plenty of less secure solutions which are easier to set and this will be true with other FTP servers.

I know it will take you 15min to set it up but you only do it once, as for needed mount commands just put them in a script and it's done.

Anyway other popular servers are pureftp and vsftpd.

---

### Post by duffydack on 2006-06-07
Ive setup proftpd on breezy and it works fine.  I installed proftpd in dapper and setup exactly the same and its a lot slower when logging in and navigating folders, generally lot slower..

---

### Post by GlurG on 2006-06-10
Hi,

First post here, yay!:) Glad that I've found a thread which discusses proftpd configs. Anyhow, I have a couple of questions:

1) In the HOWTO-guide (the secure way), why is the DefaultRoot-directive defined twice?
```

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

```

2) I've followed the HOWTO-guide, but when I connect to the FTP-server from my WinXP comp on the same network, the file list is empty. I was expecting to see the /upload and /download directory when I log in, but I don't.

3) Some of the <Directory path/to/somewhere/*> directives have a star at the end of the path. Why?

4) I will mainly use my FTP-server to upload files to my DocumentRoot for apache. Does anyhow any tips/suggestions regarding how to do this as secure as possible?

5) How do I add encryption to my FTP-connections?

6) Also, it would be nice to know how to create different users with different passwords and different "starting"/jail directories when they log in.

Thanks

---

### Post by frodon on 2006-06-10
1)Indeed one is enough but it tought it would help users who want to customise the config file to understand the principle of this command.

3)Good point, the star is not really needed since there's no sub-directories to include following the guide. You can remove them if you wish, it's up to you.

4) Mount your DocumentRoot directory in the upload directory thanks to a *mount -o bind* command, there's some examples at the end of the file.

5) I never did that  but it's documented on the proftpd site : [http://www.proftpd.org/](http://www.proftpd.org/).
You will find examples and support for that in the proftpd forum : [http://forums.proftpd.org/phpBB2/](http://forums.proftpd.org/phpBB2/)

6) The users used by proftpd are the system users and you can add the users you want to allow in this section : ```
#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>
```Don't forget to set an aliasname for them, i use this trick to prevent telnet accesses to the server.
If you use only the *DefaultRoot ~* each user will access only his home directory when login.

I hope i have given you some of the informations you're looking for.

---

### Post by GlurG on 2006-06-10
Thanks for your response.

I'm still getting an empty directory listing when I login from my other (WinXP) comp. The DefaultRoot on the FTP-server is set to /home/FTP-shared/. I've created the upload and download directories and chmod:ed them. Still, I don't see them when I log in. I also tried to mount my webroot to /home/FTP-shared ... nothing. Why is this?

Offtopic: What does the 'sudo' command do?

---

### Post by frodon on 2006-06-12
Could you post your proftpd.conf file ? 

About sudo, you should read that : [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by GlurG on 2006-06-12
Finally got it working. I had accidentaly defined ListOptions twice, so I deleted one of them and replaced the other with ListOptions "-A". Anyhow, here is my config file:

# Daemon settings
ServerName "Proftpd Server"
ServerType standalone
DeferWelcome on
AuthAliasOnly on
UserAlias sauron userftp
ListOptions "-A"
RequireValidShell off
AllowOverride off
AllowOverwrite on
MultilineRFC2228 on
DefaultServer on
ShowSymlinks off
ServerIdent off
RootLogin off
TimeoutNoTransfer 600
TimeoutStalled 600
TimeoutIdle 1200
DisplayLogin welcome.msg
DisplayFirstChdir .message
DenyFilter \*.*/
IdentLookups off
UserReverseDNS off
MaxLoginAttempts 3
AllowStoreRestart on
PersistentPasswd off

# Log
ExtendedLog /var/log/ftp.log
TransferLog /var/log/xfer.log
SystemLog /var/log/syslog.log

MaxClients 10
MaxClientsPerHost 10
MaxClientsPerUser 10
MaxHostsPerUser 10

DefaultRoot /home/FTP-shared/

<Limit LOGIN>
  AllowUser userftp
  DenyAll
</Limit>

<Directory /home/FTP-shared/>
  Umask 022 022
  AllowOverwrite off
  <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
    DenyAll
  </Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
  Umask 022 022
  AllowOverwrite off
  <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
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

---

### Post by elemental666 on 2006-06-13
I just setup proftp per this howto, everything work great, except when I connect from my laptop and upload stuff, the file permissions are dropped completly.  This mean I can't upload entire directories. When I try to upload a directory with maybe 4 files in it, the directory gets created on the server, without any permisions at all.  Then it can't open that directory to start copying files.  The files likewise will get no permissions at all.

So how do I get it to copy the same file permissions that exist on the client to stay on the files/dirs when sent to the server?

---

### Post by frodon on 2006-06-14
What's happen if you perform the same attempt after entering in terminal : ```
umask 022
```Is the new folder still without any permissions ?

---

### Post by Chuckpaxton on 2006-07-01
This maybe to late to post on here and if it is then forgive me but i'm getting a fatal error
Fatal: AllowUser: directive not allowed in server config text on line 47 of /etc/proftpd.conf 

can anyone help?

---

### Post by frodon on 2006-07-01
Could you attach you proftpd.conf file in the next post, i'd like to see it because it sounds like a syntax error.

---

### Post by Chuckpaxton on 2006-07-01
Hopefully this helps..

---

### Post by frodon on 2006-07-01
Try to jump a line and make the limit login part look like that : ```
<Limit LOGIN>
 AllowUser John
 AllowUser chuck
 DenyALL
</Limit>
```

Except that, it looks good (i mean no syntax error)

---

### Post by Chuckpaxton on 2006-07-01
That didn't work... actually i got a different message...fatal: unknown configuration directive '<limit' on line 94

---

### Post by Chuckpaxton on 2006-07-01
Ok I'm dumb the thing you told me to do did work. But once i tried to bring it online I got the new error message.

---

### Post by horatiub on 2006-07-01
Ok, I was able to setup proftpd. I'm able to connect to my download, upload directory. But, how can I get access to my /var/www directories?

I host a site on my server, and the path is in the /var/www. What do I have to add in the proftpd.conf in order to be able to upload my files?

Thanks

---

### Post by frodon on 2006-07-01
Just mount your /var/www directory in the upload directory : ```
sudo mount -o bind /var/www /home/FTP-shared/upload
```

---

### Post by horatiub on 2006-07-01
ok, thank you.

But if I mount that folder, then all my users are going to have access to it, right? I setup a second user, and I logged in and I saw that he has access to the same /var/www as my own user.

---

### Post by frodon on 2006-07-02
Ok, if you wish to limit the access to the upload directory to your own user only, modify the directory section like that : ```
<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
        <Limit ALL>
		Order Allow,Deny
		AllowUser **Your_user** 
		Deny ALL
	</Limit>
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
```Thus other users will see the upload directory but won't be able to enter in and use it.

---

### Post by horatiub on 2006-07-02
that will work. But here is what I'm trying to accomplish:

I want user1 to have access to the /var/www directory, so I mount this.
Then I want user2 to only have access to /var/www/website1,  I don't want him to have access to the other websites as user1 does. 

Thank you everybody for your help

---

### Post by frodon on 2006-07-02
I would create 2 upload directories, mount /var/www in the first and /var/www/website1 in the second then use the "LIMIT" comand as shown in my previous post to control the access.

---

### Post by joncisco on 2006-07-04
Hi, I've gone through all the posts here and I am still lost. 
I'm using Ubuntu Server 6.06
I have tried downloading proftpd and get the usual error. 
I run this command :

root@server:~# apt-get install proftpd
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package proftpd
root@server:~#

so my first question is how do I install a program that doesn't appear to be there?

And second is how do I set it up so that the users root and fred have access to the /var/www folder. 

I will be installing ispconfig as well after this and want to have ftp access for these two users. I have tried to install through different methods but no luck so far....

---

### Post by frodon on 2006-07-04
You shouldn't have all thhe repositories enabled, have a look here for example to compare your source.list file : 
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)
Once you've modifyed your source.list file run a : ```
sudo apt-get update
sudo apt-get upgrade
```
Then retry the command.

To give rights to /var/www for the user root and fred i see 2 ways, allow rights for all (sudo chmod -R 777 /var/www) or add fred to the group "root" and give full rights to the group (sudo chmod -R 774 /var/www).
More details on how manage groups and users there : 
[http://www.cs.unm.edu/~storm/UNIX.html](http://www.cs.unm.edu/~storm/UNIX.html)

---

### Post by joncisco on 2006-07-04
Thanks for your help....how do I set /var/www as the default directory for when I login via ftp?

---

### Post by frodon on 2006-07-05
If you followed my guide, just mount the /var/www directoryin the upload directory otherwise you can create a user with /var/www as home directory, he will login in its home directory.
Post your proftpd.conf file if you need more help.

---

### Post by zasf on 2006-07-26
> **mssm said:**
> I can ftp from the machine itself and from another computer inside home on the same network. The actual test whether I can access it from outside, will be done tomorrow. But I am hopeful that I shall succeed. ([COLOR="Lime"]Update : Now I can access it from outside; see my next post below[/COLOR]).

Thanks for your message, it was very helpful.

I'd like to know if when you say 
> I can ftp from the machine itself and from another computer inside home on the same network

you mean using the command
```
ftp 192.168.1.X 1980
```

or using 

```
ftp yourname.homelinux.net 1980
```

I have a similar configuration to yours, I also have a home server registered with dyndns. What I want to do it to access my ftp server **always** using the dns name (ie yourname.homelinux.net). How do you achieve that? 

Thanks

---

### Post by n00buntu NJ on 2006-07-29
I'm stuck.  I have setup proftpd/gproftpd and everything is configured properly from within my LAN.  I can access the FTP server, and transfer files up and down.  

I have forwarded the port in my router, and configured proftpd/gproftpd so that I can access my ftp server remotely (e.g. [my.ip.addy.here] [port] ).  I know I set this part up right, because I can access the server from outside the LAN (from my work).  From a windows machine, and from a Mac at my office the results are the same, that I can successfully login, however I don't get a directory listing.  ?  

I have a feeling that this has to do with my Passive Port settings, and that I need to forward these ports on my router as well, but nothing I have tried has worked...  HELP!

---

### Post by nix4me on 2006-07-30
I have a question about multiple users.  I would like to have a shared tree of folders with multiple users.  The catch is I want different limits placed on each users.

/home/ftp/shared
with the following folders
scripts
code
upload

I want 3 users
download
upload
private

I want the download user to be able to download from any dir but not be able to upload.
I want the upload user to be able to see all dirs but only be able to upload into the upload dir.
I want the private user to be able to download from any dir and upload into upload only.

Is this possible?  IF so do you have an example?

nix4me

---

### Post by frodon on 2006-07-30
nix4me, there's some examples in some previous posts of this thread.

---

### Post by nix4me on 2006-07-30
I'm actually becoming more interested in trying mysql to control users with proftpd.  Doing some reading now on it.

nix4me

---

### Post by s6dalane on 2006-08-04
New version of gproftpd is out (8.2.8 ). Is it possible to update the .deb in the first post too?

---

### Post by shoot on 2006-08-11
Hello there, I have a problem with my proftpd setup. After installing everything(which went like a charm) I edited the .conf-file to my needs, and now I can upload and download stuff from the ftp. Theres one thing I can't do though - overwrite. It's probably something minor in the .conf I have to change, but I can't find out what, even after reading all the suggestions and confs posted.

I've attached the .conf.

Thank you in advance. Shoot

---

### Post by frodon on 2006-08-11
Maybe there's an option to add in the limit command used in the directory, there : ```
<Directory /var/www/>
Umask 022 022
AllowOverwrite on
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	AllowAll
	</Limit>
</Directory>
```I never tried to overwrite a file anyway you can delete the file then write it but for sure it's less easy than a simple overwrite.

Here is the official documentation about the limit options if it helps : [http://www.proftpd.org/localsite/Userguide/linked/config_ref_Limit.html](http://www.proftpd.org/localsite/Userguide/linked/config_ref_Limit.html)

Sorry to not help you more.

Good luck ;)

---

### Post by shoot on 2006-08-11
Atleast you tried to help, I appreciate that. Gonna go check that limit documentation through. Thanks

shoot


edit: Hmm, I read it and added some stuff, saved and restarted proftpd, now I get an error (550) when I try to upload anything to the server. I removed the stuff I added and restarted, still get error 550. What's the problem now?:|

---

### Post by BabyBoy on 2006-08-13
I have httpd installed, when i log into ftp with the made username and password it takes me to the website root DIR (WWW) hmmm how secure eh :P lol NOT!
whats up with this then? heres my conf file!

```
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias sauron userftp

ServerName			"c0ntempt"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers on

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome to c0ntempts ftp, **** around and your banned! !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
	<Limit ALL>
		Order Allow,Deny
		AllowUser userftp
	</Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
	<Limit ALL>
		Order Allow,Deny
		AllowUser userftp
	</Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit ALL>
		Order Allow,Deny
		AllowUser userftp
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

```

---

### Post by jakobc on 2006-08-15
Hi - what do I need to do to send users (when they login with their own username and passwd) to their home dir?

Thanks

---

### Post by Scorpuk on 2006-08-21
Just to say thanks for an excelent HOWTO.

Took me 2 days to get it all working, but that was down to my router and its inbuilt firewall. Just adding the PassivePorts section and including a ranged port allowance on my router and hey-presto it worked. :D 

All this done while in another country thanks to putty and ssh :cool: 

Cheers,

John.


```
#
# To really apply changes reload proftpd after modifications.
# 

MasqueradeAddress		(oops not showing this)
PassivePorts 			60000 65535


AllowOverwrite on
AuthAliasOnly on

#Choose here the user alias you want !!!
UserAlias 			scorpuk userftp


ServerName			"HTPC"
ServerType			standalone
DeferWelcome			on

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer		600
TimeoutStalled			100
TimeoutIdle			2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell		off

TimeoutLogin			20

Rootlogin			off

#It's better for debug to create log files ;-)
ExtendedLog			/var/log/ftp.log
TransferLog			/var/log/xferlog
SystemLog			/var/log/syslog.log

DenyFilter			\*.*/

#I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers			off

#Allow to restart a download
AllowStoreRestart		on

#Port 21 is the standard FTP port, so don't use it for security reasons
Port				1980

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			2

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022

PersistentPasswd		off

MaxClients			8
MaxClientsPerHost		8
MaxClientsPerUser		8
MaxHostsPerUser			8

#Display a message after a successful login
AccessGrantMsg "Welcome !!!"
#This message is displayed for each access good or not
ServerIdent			on	"Scorpuk FTP Server"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

#Lock all the users in home directory, ****** really important *****
DefaultRoot 			~

MaxLoginAttempts		5

#VALID LOGINS
<Limit LOGIN>
	AllowUser userftp
	DenyALL
</Limit>

<Directory /home/FTP-shared>
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
```

---

### Post by Scorpuk on 2006-08-21
> **BabyBoy said:**
> I have httpd installed, when i log into ftp with the made username and password it takes me to the website root DIR (WWW) hmmm how secure eh :P lol NOT!
whats up with this then? heres my conf file!


Just making sure but did you do this in the install sequence?

```
sudo useradd userftp -p your_password -d /home/FTP-shared -s /bin/false
```

The above coding forces the home directory for the user to the FTP-shared.

Other than that your config file is similar to mine except the end part for <directory> settings as far as i can tell.

Anywho hope ya get it sorted.

John.

---

### Post by Hawkowl on 2006-08-22
My setup is a little different from most.
I have a webserver that i want to allow users to update their own webpages on by FTP.

I have installed Proftp as per the early directions but changed some of it in an attempt to get access to a folder called testftp which resides in this folder /var/www/xxxxxxxxx/ftptest

I have set up a test user called *fred* with a password *flintstone* in system User and Groups.

this is a copy of my proftp.conf file, does it look ok?
and is this setup of mine the best way to go about this thing?

```

# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias hawkowl userftp

ServerName			"xxxxxxx"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /var/www/downtowncentral/ftptest

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /var/www/downtowncentral/ftptest>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /var/www/downtowncentral/ftptest/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /var/www/downtowncentral/ftptest/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

```

---

### Post by frodon on 2006-08-23
It looks all good for me, don't forget to set /var/www/downtowncentral/ftptest as home directory for your user *fred* and to give the good rights the directory you use for the ftp (755 for a dowload directory and 777 for an upload directory).

---

### Post by Coogan on 2006-08-26
I need some help.  I don't know what I did, but as early as this morning I was able to upload to my ftp server with no problem, and now all of a sudden I cannot upload or download to/from it.  I've removed and reinstalled proftp using the steps in the 1st post, and removed and recreated the userftp account, but it's still not working.

My conf file was a cut 'n paste straight from the 1st post, with some minor changes (I changed the home dir from FTP-shared to just ftp) and I changed the server name, user alias, and port.  I'm 99% sure it's a permissions problem but can't figure out why.

Coog

---

### Post by frodon on 2006-08-27
Be sure to give 755 rights to your ftp directory and dowload directory and 777 rights for your upload directory.
Post your conf file if you changed something, sometimes a typo may be hard to see and it easier if several people have a look to it.

---

### Post by Tavathlon on 2006-08-27
Hello everyone!

I'd like to begin with saying that I'm impressed over your dedication to this thread, rodon! I've just read the whole thread, and people seldom have to wait for long before you give them a good answer - creds to you!  :D 

However, in spite of reading the whole thread, I still have one question - the same one that made me search this thread.

In the original howto, you refer to a simple way of mounting folders into the folder that my ftp-users may access (which is their own respective home folders). In fstab, this line should be added:

'the_directory_to_mount /home/FTP-shared/download vfat bind 0 0'

I have used this kind of hard linking for about a year, and it works really well! (however I mount the folder into every users home folder instead, since that is the only part of my computer that they may access) However, as it is now, all users have complete access to the folder I mount into their home directory. I want them to have full access to their own Home, but I don't want them to be able to write or delete in the folder I mount into their Home - I only want them to have read access there. I've tried to use the umask function to limit their access in the mounting atself, but without any success. The line in fstab looks like this right now:


'the_directory_to_mount /home/user/name_of_folder vfat bind,umask=777 0 0'

I've also tried umask=000, umask=222 and so on...  But the users always have full access anyway.

Am I making the umask thing wrong? Is there any way to achieve the same goal by configuring proftpd.conf?

Unfortunately, I cannot just simply chmod the directory - I don't know why, but I cannot, even if I am root. It just simply doesn't work. On the other hand, it doesn't really matter, because I want _some_ users so have full access to the same folder.

Finally, I do not use gproftpd, and I do not intend to either, mostly because I think it works fine the old way. There is only one function in gproftpd that I would like to have, and that is the logging of what users are online, and what did they download/upload. But nah, that doesn't really matter that much...  =P

Hope to get some help with this problem, it would be really nice to have my stored files secured! :)

---

### Post by frodon on 2006-08-28
Hi and thanks for being so kind with me.

> **Tavathlon said:**
> There is only one function in gproftpd that I would like to have, and that is the logging of what users are online, and what did they download/upload. But nah, that doesn't really matter that much...  =POpen a terminal and type *ftptop* while your ftp server is running, you will see who is connected on the server in real time and what he's downloading, if you press the character *t* you will even see the transfert rate.
There also the *ftpwho* command which gave you the same kind of information but not in real time.

If you want to prevent write and deletion in a folder just modify the section corresponding to this folder in your proftpd.conf file.
For example the download directory on my guide : ```
<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>
```The parameters *DELE* and *RMD* are denied therefore the users will not be able to delete a file or a directory in the coreesponding folder.

See the limit page on the proftpd site for more details :
[http://www.proftpd.org/localsite/Userguide/linked/config_ref_Limit.html](http://www.proftpd.org/localsite/Userguide/linked/config_ref_Limit.html)

---

### Post by Tavathlon on 2006-08-28
*pointing at the two most recent posts*  10 hours. That _is_ impressive! :D 

The commands *ftptop* and *ftpwho* were really useful, thanks a lot! Someone told me once that such information was not available in proftpd, but apparently they were wrong.  :) 

However, the limit configuration did not work  =/  (and yes, I did restart the server before I tried it out :p )
I've been looking at the limit configuration before, but didn't really understand how it worked back then. This time, I copied the text in your post straight off, but it didn't work. (I changed the directory, of course.)

I'm not quite sure why the limit does not work, but on the other hand, the umask should have worked too...

---

### Post by frodon on 2006-08-28
Could you post your proftpd.conf file and tell me the name and path of the directories you want to protect from DEL and RMD commands ?
I'll have a look to it and see if something sounds wrong in your config file.

---

### Post by Tavathlon on 2006-08-28
Absolutely. The path to the directory (or rather an example - there are as many as I have ftp-users, but I use this particular one for testing)

Thanks a lot!

---

### Post by Tavathlon on 2006-08-29
By the way, the directory that is linked into user morot's home folder is actually a HD mounted at another spot. I'm not sure whether that might make any difference?

---

### Post by frodon on 2006-08-29
After reading your conf file i don't see anything wrong, i don't understand why users are still able to delete, i use quite the same method in my guide and it works without any problems, it's weird.

---

### Post by Tavathlon on 2006-08-30
Strange indeed. Well, I suppose I'll just put it in the pile of unsolved mysteries, then.  :p 

I found out today that I am actually able to change the permissions of the folder nowadays - I suppose I haven't tried that since I upgraded to Dapper or something. So it's possible for me to prevent people from deleting files, but the downside of it is that I myself won't be able to do it either without meddling as root. That's a minor problem, though.

Anyway, thanks a lot for the help! :D 

(After all, now I know that it's something strange, and not just I that is doing things wrong... :) )

---

### Post by recklessray on 2006-08-31
followed the howto - but when start the server , i get this error.. any ideas anyone? cheers :)

frank:/home/ftp# /etc/init.d/proftpd restart
Stopping ftp server: proftpd.
Starting ftp server: proftpd - IPv6 getaddrinfo 'localhost.localdomain' error: Name or service not known

---

### Post by frodon on 2006-08-31
Did you change anything in the proftpd.conf file given in the guide ? If yes could you post it ?

---

### Post by nix4me on 2006-09-03
I like the way you have the server setup however I have one question.  If I set more aliases to allow more login account names, they all have the same password...the password set for userftp.

Is there a way to still use aliases and have seperate passwords without having to setup system accounts for each user?

nix4me

---

### Post by frodon on 2006-09-04
Without creating new accounts, i would say no but obviously i may be wrong.

BTW, do you (all users) think it would be useful for you if i write a small guide on how set a FTP server with TLS/SSL encryption, that means the authentification and the data are encrypted (SFTP) ?

---

### Post by nix4me on 2006-09-04
Well i figurd out how to do what I wanted from my previous post.  I had to abandon the use of alias.

I am using virtual users with the AuthUserFile feature and things are working great.

I also have TLS enabled and working nicely.

Any value added in me documenting the use of virtual users on this forum?

nix4me

---

### Post by frodon on 2006-09-04
> **nix4me said:**
> Any value added in me documenting the use of virtual users on this forum?

nix4meOf course yes and i would gladly add this documentation to the first post with the due credits.
I would be really interested too if you could also explain the steps you followed to enable TLS.

Thanks a bunch, you rock :KS

---

### Post by nix4me on 2006-09-04
Use the following steps to get TLS working in proftpd:

```
# sudo apt-get install build-essential
# sudo apt-get install libssl-dev
# cd /etc
# sudo mkdir ftpcert
# cd ftpcert/
# sudo openssl genrsa 1024 > host.key
# sudo chmod 400 host.key
# sudo openssl req -new -x509 -nodes -sha1 -days 365 -key host.key > host.cert
```

Answer the questions - Valid answers are not important

Add these lines to the /etc/proftpd.conf

```
TLSEngine on
TLSLog /var/log/ftpd/tls.log
TLSProtocol TLSv1
TLSRequired off
TLSVerifyClient off
TLSRSACertificateFile /etc/ftpcert/host.cert
TLSRSACertificateKeyFile /etc/ftpcert/host.key
```

*Note - Use TLSRequired ON to force the use of TLS. OFF means that the use of TLS is optional.

Let me know if you have problems,

nix4me

---

### Post by emptycs on 2006-09-05
when i type
```
sudo apt-get install proftpd
```

I get couldn't find packages proftpd

---

### Post by frodon on 2006-09-05
emptycs, this shoulf be a repository problem, have you enabled the universe and multiverse repositories ?

nix4me, your instructions are really nice, i don't have the time to test them now but will do ASAP. Anyway it should work like a charm because i found the same instructions on the proftpd forum :
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html)
[http://www.castaglia.org/proftpd/modules/mod_tls.html](http://www.castaglia.org/proftpd/modules/mod_tls.html)
However i saw you don't use the *TLSCACertificateFile*, it is explained here :
[http://www.modssl.org/docs/2.7/ssl_faq.html#cert-ownca](http://www.modssl.org/docs/2.7/ssl_faq.html#cert-ownca)

On the other hand could you confirm that to get the authentification file to work you just created an authentification file and added the [AuthUserFile]("http://www.proftpd.org/localsite/Userguide/linked/config_ref_AuthUserFile.html") command ?
Could you give us as example your authentification file. Did you try aliases with the authentification file method ?
Thanks a lot

---

### Post by timka1 on 2006-09-05
When I get to the following line:

```
sudo openssl genrsa 1024 > host.key
```

I get "bash: host.key: Permission denied

How does this happen when using "sudo"?

---

### Post by frodon on 2006-09-05
Check the rights of the file host.key, if it don't have write rights even sudo can't open the file and write it.
To add "write" rights use this command : ```
sudo chmod +w host.key
```

---

### Post by timka1 on 2006-09-05
[COLOR="Blue"][trying the new TCL config from previous page][/COLOR]
I tried sudo chmod +w host.key 

As I suspected it said that the file did not exist.

I applied the chmod to the directory (ftpcert) and this worked

I then reran sudo openssl genrsa 1024 > host.key

But still got the Permission denied error.

[COLOR="Blue"][general error][/COLOR]

Not sure if this is relevant to the specific TCL config error but when I try to upload to the FTP server connecting via Fetch (Mac GUI) I drag the file into the upload directory and the transfer starts, the file name is created but then it hangs and eventually times out. The file is there but 0 bytes.

---

### Post by frodon on 2006-09-05
Ok, instruction on how enable TLS/SSL are tested and working like a charm.

See the main post for detailed instruction on TLS/SSL enabling.

Again thanks to nix4me ;)

---

### Post by whatalotta on 2006-09-05
Hi folks,

I've followed the howto inclusive of the tls part.  Everything works fine.  Thanks for taking the time to create a great howto like this one for the community to use.

I want to be able to remotely reboot my box.  However, I am concerned that the way the certs are setup, the system will just hang because I will need to input the password, and I don't know how to do so remotely (I use putty/ssh).

Can you advise how to modify or create certs that will allow me to perform an unattended reboot?

Thanks!

---

### Post by whatalotta on 2006-09-05
Okay, this turned out worse than feared.  Upon attended reboot, the system just hung.  I'm going to play with the configuration of grub to get rid of the fb stuff and try again later.

Note that after hitting Power Off (I hate to admit that),  I selected recovery mode from grub, and the system just hung after alsa was restored. Tried putting in the password a couple of times (blind).  Didn't work.

I ended up rebooting into Gentoo and chrooting into Kubuntu LTS.  I then removed the ftpcert directory and commented out the cert lines from the proftpd.conf.

Upon reboot, all is normal.  I'm feeling a bit confused.  For right now, I will use proftpd without encryption.  However, I really like the idea of having encryption.  Please let me know what I need to do to get rid of the requirements for passwords.

Thanks!

---

### Post by nix4me on 2006-09-05
I don't know what your talking about when you say you are having to enter a certificate password.  The instructions that i posted work flawlessly.

Another way to create a ssl certificate is to load gproftpd and use it generate a .pem file.  Then just load that certificate in the proftpd config with TLSRSACertificateFile.  I did that 3 years ago and have had my server up and running for the last 3 years.

Anyway, again, not sure what has happened to you.  I don't have a spare machine to try the config that Frodon posted.  I will try to test soon.

nix4me

---

### Post by whatalotta on 2006-09-05
I tested it with gproftpd and if works without requiring passwords everytime the proftpd daemon is started and stopped (restarted).  I believe the password was for a .key file.

We'll see if someone else comes along with the same problem.

-Whata

---

### Post by frodon on 2006-09-06
Yep, i noticed the password thing too and i confirm that the password is needed to start/restart/stop the server, i will search and see if it's possible to get rid of that.
Anyway having his own certificate file is not mandatory.

EDIT: well, i found the answer there : 
[http://www.modssl.org/docs/2.7/ssl_faq.html#remove-passphrase](http://www.modssl.org/docs/2.7/ssl_faq.html#remove-passphrase)

It is because the RSA private key is encrypted in the server.key file, thus the solution is to remove the encryption of the RSA private key but it makes the key readable in the server.key file. So for the moment i don't know what to advice.
For sure the most secure solution is to keep the RSA private key encrypted.

Do you think i should document the way to remove RSA private key encryption in the server.key file in the guide as  an alternative way to use the certificate file ? Obviously with a warning notifying that it's less secure.

---

### Post by Tavathlon on 2006-09-06
I don't really think most users will have any need of remotelly starting/stopping/restarting their servers. But on the other hand, if the information is available, it is more of a free choice for every user - most probably don't even know you could do that, but when they hear it's possible, they might want to have it that way.



> **nix4me said:**
> *Note - Use TLSRequired ON to force the use of TLS. OFF means that the use of TLS is optional.

Is there any downside of forcing the use of TLS?

---

### Post by frodon on 2006-09-06
> **Tavathlon said:**
> Is there any downside of forcing the use of TLS?You will only be able to login the server if you use a FTP client which support TLS/SSL, for example gFTP don't support it.
If you wish to get quickly a FTP client which support SSL/TLS install the "fireftp" extention of firefox, you just need firefox for that (the OS you use is not important).

---

### Post by whatalotta on 2006-09-06
Hi Frodon,
 
Thanks for the response. I will have a look at the link you posted and I will be able to figure out for myself how to set up the key without encryption.
 
BTW, I have everything setup and working using the configuration parameters that you provide in the howto except for encryption. Works great! Thanks for the Howto!
 
I tried using gproftpd and found it to be a little restrictive, so I went back to your howto. 
 
I found that the 503 error can be fixed simply by typing:
 
[html]passwd userftp[/html]
 
and typing in the password desired when prompted after the user is created. Not sure why the command string provided does not work. I think that with the command string provided, the password is not being taken when the user is created, so that when people try to authorize, they get the 503 error because the passwords do not match.
 
With respect to posting instructions for how to set up the certs and reboot without being asked for passwords, I think that this is completely up to you. My vote would obiously be yes, but clearly, my use of my system is different than a lot of other users. Is it worth it posting the instructions for one person? Probably not.
 
Thanks for the awesome howto!
 
-whata

---

### Post by whatalotta on 2006-09-06
Hi all,
 
Thanks to Frodon and the link provided, I have been able to remove the password requirement when using SSL certs. I know it can be done a little simpler by not requiring the password in the first place, but as Frodon pointed out, it is more secure than not requiring it. In other words, you are better off sticking to the howto as it is.
 
If you are looking for the easiest way to not end up with the password requirement, just go to the cert directory and follow most any howto on setting up SSL for an Apache web server. I haven't come across one that had made me type in a password when shutting down and starting up the server.
 
If you want to remove the password requirement after implementing it per the howto, here's how:
 
[html]cd /etc/ftpcert
cp server.key server.key.org
openssl rsa -in server.key.org -out server.key[/html]
 
Enter the password, restart your server and enjoy.
 
-whata

---

### Post by nix4me on 2006-09-06
I would recommend that the instructions to remove the required password be added or change the way certificates are created.  Having to enter a password is too intrusive for the average user.

nix4me

---

### Post by frodon on 2006-09-07
It's documented in the guide now, each user will have to make his own choice now ;)

Thanks again whatalotta and nix4me for the feedback.

---

### Post by Tavathlon on 2006-09-07
> **frodon said:**
> You will only be able to login the server if you use a FTP client which support TLS/SSL, for example gFTP don't support it.
If you wish to get quickly a FTP client which support SSL/TLS install the "fireftp" extention of firefox, you just need firefox for that (the OS you use is not important).


Ah, I see...  Thanks!  =)

---

### Post by whatalotta on 2006-09-07
Frodon,
 
Actually, thank you. This is one of the better guides I've used. You are also very involved with the users of the howto and very responsive to their queries. Please keep up the great work!
 
-whata

---

### Post by dmizer on 2006-09-10
> **whatalotta said:**
> 
I found that the 503 error can be fixed simply by typing:
 
[html]passwd userftp[/html]
 
and typing in the password desired when prompted after the user is created.

i was in agony over this 503 error because i administer 4 linux servers that have no gui interface.  the above quoted fix worked to get past the 503 error via cli interface.

thank you so much.  this was the only hangup i encountered in the howto.

---

### Post by whatalotta on 2006-09-10
Great!  I'm glad it helped someone.

-whata

---

### Post by frodon on 2006-09-11
Nice fix whatalotta, i add that in the guide, thanks you all for your help, if this guide is that good it's obviously thanks to the feedback you provide.

---

### Post by nix4me on 2006-09-12
After some research, I finally have a Proftpd server working with virtual users authenticating through a Mysql database.  It also is TLS/SSL enabled.

I wish I had the time to document it step by step but that would take some time.

If alot of users are interested enough, I might consider posting a Howto in the future when I get time.

nix4me

---

### Post by Phoobarnvaz on 2006-09-14
I want to thank everyone for all of the help you've provided.  Have gotten ProFTPd up & running with being able to connect with any computer on no-ip.  

The only glitch I'm running into which keeps me from putting this into production is not being able to put files into the FTP folders either locally or remotely.  Can download fine.  The permissions on the folders under ftp-shared are user: ftp group: nogroup.

The image was built & configured by myself with VMWare Workstation to be deployed in Player on a 2000 Server.  The reason for this is that I refuse to use IIS.

Not sure if it's in Kubuntu or in my config file.  Here's the file:

#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly off

# Choose here the user alias you want !!!!
# UserAlias sauron userftp  

ServerName			"Charlie Dunn Productions"
ServerType			standalone
DeferWelcome			on

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer		600
TimeoutStalled			100
TimeoutIdle			2200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

# It's better for debug to create log files  ;-) 
ExtendedLog                     /var/log/ftp.log
TransferLog                     /var/log/xferlog
SystemLog                       /var/log/syslog.log

# DenyFilter			\*.*/
DefaultRoot /home/ftp-shared/ftp 
# DefaultRoot ~   	 

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for
me)
UseFtpUsers off

UseReverseDNS off
IdentLookups off

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd		off

# Uncomment this if you would use TLS module:
#TLSEngine 			on

# Uncomment this if you would use quota module:
#Quotas				on

# Uncomment this if you would use ratio module:
#Ratios				on

# Port 21 is the standard FTP port.
Port				21

# I know it's not the best...but will save my sanity not taking calls why they can't connect & how to "do this properly."

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			8

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
# AllowOverwrite			on

# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default. 
#DelayEngine 			off

MaxLoginAttempts    5

#VALID LOGINS
 <Limit LOGIN>
# AllowUser userftp
# DenyALL
AllowALL
</Limit>

<Directory /home/ftp-shared/ftp>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

<Directory /home/ftp-shared/ftp/download/*>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
        Order Allow,Deny
	AllowUser phoobar
	AllowUser charlie
	DenyAll
        </Limit>
</Directory>

# Myself & the server admin are the only ones I want being able 
# to do anything with the server.

<Directory /home/ftp-shared/ftp/utilities/*>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	Order Allow,Deny
        AllowUser phoobar
        AllowUser charlie
        DenyAll
        </Limit>
</Directory>

<Directory /home/ftp-shared/ftp/waiting/*>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	Order Allow,Deny
        AllowUser phoobar
        AllowUser charlie    
	DenyAll
        </Limit>
</Directory>

<Directory> /home/ftp-shared/ftp/upload/>
Umask 022 022
AllowOverwrite on
        <Limit READ RMD DELE>
        DenyAll
        </Limit>

        <Limit STOR CWD MKD>
        AllowAll
        </Limit>
</Directory> 

Any help you can provide would be greatly appreciated.

---

### Post by frodon on 2006-09-14
> **Phoobarnvaz said:**
> I want to thank everyone for all of the help you've provided.  Have gotten ProFTPd up & running with being able to connect with any computer on no-ip.  

The only glitch I'm running into which keeps me from putting this into production is not being able to put files into the FTP folders either locally or remotely.  Can download fine.  The permissions on the folders under ftp-shared are user: ftp group: nogroup.You mean that you're not able to upload on your FTP server ?

---

### Post by Phoobarnvaz on 2006-09-15
> **frodon said:**
> You mean that you're not able to upload on your FTP server ?

That's the only thing...locally or remotely...that it will not do.  On the other hand...if I set it up for anonymous use only...can upload & download.

Thanks for the reply!!!

---

### Post by frodon on 2006-09-16
Your configuration seems good from what i see so i think to a system rights problem.
Check that your upload directory have 777 rights, if it's not the case give it 777 rights because it's needed to be able to upload.

---

### Post by Phoobarnvaz on 2006-09-19
> **frodon said:**
> Your configuration seems good from what i see so i think to a system rights problem.
Check that your upload directory have 777 rights, if it's not the case give it 777 rights because it's needed to be able to upload.

The upload directory is set for 777...with the other folders set for 755.

From gFTP...get:  Could not change local directory to (whatever folder I'm trying to upload from):  not a directory.

From Filezilla...Critical transfer error.

Here's the listing from Filezilla:

Response:	220 ProFTPD 1.2.10 Server ready.
Command:	USER charlie
Response:	331 Password required for charlie.
Command:	PASS *****
Response:	230 User charlie logged in.
Command:	FEAT
Response:	211-Features:
Response:	211-MDTM
Response:	211-REST STREAM
Response:	211-SIZE
Response:	211 End
Command:	SYST
Response:	215 UNIX Type: L8
Status:	Connected
Response:	257 "/Uploads" is current directory.
Command:	TYPE I
Response:	200 Type set to I
Command:	PASV
Response:	227 Entering Passive Mode (24,121,25,76,240,182).
Command:	STOR AutoGordianKnot.2.27.Setup.exe
Response:	550 AutoGordianKnot.2.27.Setup.exe: Permission denied
Error:	Upload failed
Status:	Retrieving directory listing...
Command:	TYPE A
Response:	200 Type set to A
Command:	PASV
Response:	227 Entering Passive Mode (24,121,25,76,240,184).
Command:	LIST
Response:	150 Opening ASCII mode data connection for file list
Response:	226 Transfer complete.
Status:	Directory listing successful
Command:	TYPE A
Response:	200 Type set to A
Command:	TYPE A
Response:	200 Type set to A
Status:	Disconnected from server
Command:	TYPE A
Response:	200 Type set to A
Command:	REST 0
Response:	350 Restarting at 0. Send STORE or RETRIEVE to initiate transfer
Command:	TYPE A
Response:	200 Type set to A
Command:	DELE /Uploads/AutoGordianKnot.2.27.Setup.exe
Response:	550 /Uploads/AutoGordianKnot.2.27.Setup.exe: Permission denied
Status:	Retrieving directory listing...
Command:	TYPE A
Response:	200 Type set to A
Command:	PASV
Response:	227 Entering Passive Mode (24,121,25,76,240,191).
Command:	LIST
Response:	150 Opening ASCII mode data connection for file list
Response:	226 Transfer complete.
Status:	Directory listing successful
Command:	PWD
Response:	257 "/Uploads" is current directory.

Any suggestions would be appreciated.

Thanks for all of the suggestions.

---

### Post by frodon on 2006-09-19
Is AutoGordianKnot.2.27.Setup.exe you're trying to upload ?
It seems to be the problem, from what i read from the log it seems to be the file you are trying to upload on the server but of course if the rights on this file are too restrictive and/or if it is owned by root you will not be able to handle it due to rights problems.

From what i know the 550 error tell you that there's a kind of right problems somewhere.

---

### Post by mssm on 2006-09-20
> **zasf said:**
> you mean using the command
```
ftp 192.168.1.X 1980
```

or using 

```
ftp yourname.homelinux.net 1980
```


Thanks zasf for your kind reply. Maybe, you have already solved the problem. I am sorry that I am replying back after almost 2 months.

I used the 2nd command. However, The first command will not work since it is an internal ip address which outside world can not see. I had a tough time using proftpd from another machine(OS = Windows) within my home network(some 530, 500 errors) which I think I clarified in my post how to get rid of.

> **zasf said:**
> I have a similar configuration to yours, I also have a home server registered with dyndns. What I want to do it to access my ftp server **always** using the dns name (ie yourname.homelinux.net). How do you achieve that? 

Thanks

I think you have registered with dyndns with your IP address which outside world can see(Not the internal one starting with 192). Check your IP address with checkip.com or similar website and if it is not a static IP address, but a dynamic one, you need some client like "noip" or "ddclient"(which I used) to keep dyndns posted about your dynamic IP address. If everything works fine, you can access it from inside or outside network using the address [ftp://yourname.homelinux.net](ftp://yourname.homelinux.net).

Finally, if you have a router at home and have more than one computers and turn off your computer(on which proftpd is installed), it is better to have an STATIC INTERNAL IP address for your server computer, since the router uses DHCP(hence dynamic) to assign iternal ip address. Th eprocedure for assigning static internal address to a computer will be given in your router's manual. Otherwise, if you just go with the dynamic internal ip address, make sure to check it, since you have opened the firewall and forwarded the port in your router for this internal ip address only. For example, in my case it was : 192.168.0.10 and since I never switch off my server, it remained the same. However, I checked for my other computer in my hme network that there internal ip addresses change from time to time. Moreover, I think the server is not a laptop. My point is that even it's a laptopwith wireless facility, I would recommend to put it on internet through ethernet for the purpose of proftpd.

Hope it helps.

---

### Post by TransformedBG on 2006-09-20
okay so ive been reading threw this. and ive got proftpd installed now im still trying to get it up and running. Every time i try to start the ftp i get a message that says "Starting ProFTPD ftp daemon: failed" i think it has something to do with the proftpd.conf file but im not sure. any ideas or suggestions would be great. Im basically just trying to set up an FTP server where i can share files to my friends in iraq.

---

### Post by erik_boi on 2006-09-20
Hi, thanks for writing this howto and thanks all the other contributors; it made the setup almost painless. I have everything working how I would like, basic server for me and my friends who each have their own folders. However, I was wondering if it possible to limit the upload rate so browsing and other things for me and my family do not get drastically slowed down when other people are downloading from me.

Thanks again
Erik

@TransformedBG: you should post your proftpd.conf so someone can help you find the problem.

---

### Post by frodon on 2006-09-21
Just use the [TransfertRate]("http://www.proftpd.org/localsite/Userguide/linked/config_ref_TransferRate.html") parameter to set the uload and download rates.
For example to limit the dowload rate to 4Kb/s add this line in your proftpd.conf file : ```
TransferRate RETR 4096
```To limit the upload rate to 4Kb/s : ```
TransferRate STOR 4096
```

@TransformedBG, without some details on what you did and your proftpd.conf file it would be almost impossible to help you.

---

### Post by TransformedBG on 2006-09-21
k so this is my proftpd.conf file in a nut shell: Im not a 100% sure what i need to change cause this is how it came minus the glens server part. 


#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

ServerName			"Glens"
ServerType			standalone
DeferWelcome			on

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer		600
TimeoutStalled			100
TimeoutIdle			2200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

DenyFilter			\*.*/

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd		off

# Uncomment this if you would use TLS module:
#TLSEngine 			on

# Uncomment this if you would use quota module:
#Quotas				on

# Uncomment this if you would use ratio module:
#Ratios				on

# Port 21 is the standard FTP port.
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default. 
#DelayEngine 			off

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayFirstChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

---

### Post by dannyboy79 on 2006-09-21
transformedbg, you have to use sudo to start and stop the server! that's how I got mine to work. if you did the ssl or certificate thingy to encrypt your traffic than it'll ask you for the passwords you used when you created the ceriticates in order to stop and start the server.

---

### Post by dannyboy79 on 2006-09-21
Frodon, is it normal to not be able to copy stuff from the upload server onto my work pc when I log in using the username and password I set up????? See what hapened to me was that i set this up in a hurry before work yesterday and didn't put anything in the folders. Then when I loggged in using gftp I got it to work when I was on a local computer, well when I was in gftp I tried transferring all my music from a music folder on the local machine into the download directory and it wouldn't let me??? So then I tried to copy music into the upload directory and it let me. So now I am at work and I want to get access to that music, well I loogged in and it worked but it won't let me copy anything off the server? how do I put stuff in the download folder if I can't write to it? i just thought about this, do i have to transfer stuff to the download folder when I at my server? so the upload folder is only for putting stuff in and nothing out and the download folder is for taking stuff out and nothing in? Ok I get it. I just tested something else out, it'll let me create a directory but I can't rename it, it just says new folder. this is a result of using your proftp.conf file except for the username, folder name, and alias, and I am using the default port 21 because my company doesn't let traffic out on any non-normal port. only 21, 80 etc etc. Can you help me? oh yeah, this is using internet explorer as a client cause I can't install any ftp client.

---

### Post by TransformedBG on 2006-09-21
> **dannyboy79 said:**
> transformedbg, you have to use sudo to start and stop the server! that's how I got mine to work. if you did the ssl or certificate thingy to encrypt your traffic than it'll ask you for the passwords you used when you created the ceriticates in order to stop and start the server.

ive used sudo, still no luck

---

### Post by dmizer on 2006-09-22
> **TransformedBG said:**
> k so this is my proftpd.conf file in a nut shell: Im not a 100% sure what i need to change cause this is how it came minus the glens server part. 
you'll need to replace all of that with what's in the guide on the first page under step 3.

everything you need to know to configure your ftp server is in the first post of this guide.  follow the directions carefully, and you'll end up with a working ftp server.

---

### Post by frodon on 2006-09-22
@dannyboy79, if i understand well you want to upload things in your upload directory and also download them from this same directory later ? Correct me if i'm wrong.
So modify your upload directory section like that : ```
<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD READ RETR>
      	AllowAll
    	</Limit>
</Directory>
```Read [this page]("http://www.proftpd.org/localsite/Userguide/linked/config_ref_Limit.html") if you want some details on how to use the LIMIT commands. The LIMIT command defines what is allowed or not in a directory thus you set the rights as you want in the directory if you know how to use them, for example in my guide i prevent file and directory deletion in the upload directory but you may want to change that if it don't fit your needs.

---

### Post by dannyboy79 on 2006-09-22
Frodon,
Thank you for responding but you didn't answer the question on how to adjust the upload folder settings so that users can rename a folder they create. I noticed that when I was in IE and I hit new folder, it named it New Folder with a space and wouldn't even let me change the name of the it??? Then later when I was at home I had a hell of a time figureing out how to delete a directory with spaces in it and then it was even worse cause I created 3 of them and IE put (2) and (3) on the end of the New Folder name so I spent probably an hour trying to delete the damn folders. I finally got it by putting rmdir New\ Folder\ \'(2)' but sinjce I am a newbie I had no idea itr was gonna be that hard to simply remove a directory! HA HA ANyway, thanks for the help so far,

---

### Post by frodon on 2006-09-22
All should be explained in the link i gave you, as you can see in my guide and in the example i gave you, file and directory deletion are forbidden in the upoload directory due to this section : 	```
<Limit RMD DELE>
      	DenyAll
    	</Limit>
```It says that RMD and DELE ftp commands are denied in the upload directory, so if you remove them from this section and add them to the "allow" section they will be allowed.
The ftp commands for the rename actions are RNFR and RNTO, add them to the "allow" list in the upload directory section if you want to allow them.
So your upload directory section would look like that : ```
<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
    	<Limit STOR CWD MKD READ RETR DELE RMD RNFR RNTO>
      	AllowAll
    	</Limit>
</Directory>
```

---

### Post by zasf on 2006-09-22
> **mssm said:**
> Thanks zasf for your kind reply. Maybe, you have already solved the problem. I am sorry that I am replying back after almost 2 months.

Thanks for your reply but I think you didn't get my point.

Anyway I discovered that what I meant is commonly known as "local loopback" wich is a feature that most home/office routers don't have. 

There are hacks to modify your router's iptables but they are lost on power off.. so what I'm planning to do (when I have a little time) is to make a script on my server (behind router) to perform such hacks periodically.

Thank you anyway,

---

### Post by horatiub on 2006-09-22
I setup the proftpd server with GProFTPD and here is what I'm trying to do:

I wanna have the home folder set to default: /home/ftp, but I would like to be able to access the /var/www directory as well.

How do I accomplish that? I made a simlink of the /var/www into the home folder, but when I connect thru FTP, I can't access it.

---

### Post by nix4me on 2006-09-22
Use:
mount --bind /var/www /home/ftp/www

Make sure you create the www dir in /home/ftp and run the command as sudo.

Will work like a champ.

nix4me

---

### Post by horatiub on 2006-09-22
> **nix4me said:**
> Use:
mount --bind /var/www /home/ftp/www

Make sure you create the www dir in /home/ftp and run the command as sudo.

Will work like a champ.

nix4me

yes it does, thank you.

Also, I'm assuming that all the other users will be able to see this directory though. I have to figure out a way to restrict them

---

### Post by horatiub on 2006-09-23
Ok, I have one more issue now. Every time I try to connect, I don't ge the directory listings, and after a while it times out.

I'm behind a router, so I forwarded the FTP port, and I also added the MasqueradeAddress and the Passive Ports 60000 65555.

Am I missing something? For the MasquaradeAddress, I used the name.dyndns.org account that I have.

---

### Post by nix4me on 2006-09-23
You have to forward the passive ports also.  Thats why the dir listing is timing out.

You can also limit the users who can list the www dir by using the limit command in the proftpd config.


nix4me

---

### Post by dannyboy79 on 2006-09-23
frodon, thank you very much for your response. I have posted many questions in these forums and have only been helped 2 times, this time and 1 other time someone attempted to help but to no success. Sometimes I just wonder what these forums are for if users who arent having problems don't come in here once in a while and read thru them and say to themselves, oh, I have that working on my machine, maybe I should respond to this one so I am can help out fellow Ubuntu users!!! Hell I am a newbie and I have helped other newbies who started linux after me with over a dozen things! My unsolved things are a Microsolution Cd-Burner hooked via USB doesn; work, they even have a linux download and it says it uploads the firmware to my CD writer thru  the hot plug thingy but I don;t know what do with all the stuff that the .tar contained? ALso, I am having a hell of a time getting Ubuntu Nautilus to browse my WINXP box thru the Servers pull down. After a long pause it states that it can't display all the contents of the folder??? Also, The sound out of my right speaker stopped working after I played songs thru XMMS thru a remote desktop setup. Weird but no one has hardly even bothered to help me figuer out what to do and since I am a newbie all I can do is gogle for hours on hours and read until my eyes pop out of my head which i have done for so long I pretty much give up and then try another day. Anyway, sorry for the long rant about users and thank you again for your help!

---

### Post by erik_boi on 2006-09-24
> **frodon said:**
> Just use the [TransfertRate]("http://www.proftpd.org/localsite/Userguide/linked/config_ref_TransferRate.html") parameter to set the uload and download rates.
For example to limit the dowload rate to 4Kb/s add this line in your proftpd.conf file : ```
TransferRate RETR 4096
```To limit the upload rate to 4Kb/s : ```
TransferRate STOR 4096
```

@TransformedBG, without some details on what you did and your proftpd.conf file it would be almost impossible to help you.

Excellent, thanks for the help here and with the rest of this topic. I would just like to point out for other people who may look at this that the numbers here are actually in kilobites-per-second. So, to limit the download to 4 kilobites/s simply use TransferRate RETR 4. It is in the link you provided but I thought that this might help someone.

Thanks again
Erik

---

### Post by dmizer on 2006-09-28
okay ... i have a small problem.  i don't have the fastest connection in the world, and i'm having problems with some of my ftp users getting authenticated.  they're getting 580 errors, but i know the account is set up correctly because i can log in myself with their user id and password.

i think it's just timing out before they can send the complete user name and password to my server.

i've changed TimeoutLogin to 100, but that still doesn't seem to give them enough time to send the entire user name and password.  is there something i'm missing?

---

### Post by dootch on 2006-09-29
> **nix4me said:**
> Use:
mount --bind /var/www /home/ftp/www

Make sure you create the www dir in /home/ftp and run the command as sudo.

Will work like a champ.

nix4me
Thanks for this nix4me but I am getting a permissions error when trying to upload. I created the directory www in my home/FTP-shared directory and used bind to "link" it with my /var/www/ directory all is well there, I think. I can see it's contents when I ftp to it but I cannot upload anything. I get a 550 error permissions denied. I used the same permissions as the Upload directory.

---

### Post by dootch on 2006-09-29
> **dootch said:**
> Thanks for this nix4me but I am getting a permissions error when trying to upload. I created the directory www in my home/FTP-shared directory and used bind to "link" it with my /var/www/ directory all is well there, I think. I can see it's contents when I ftp to it but I cannot upload anything. I get a 550 error permissions denied. I used the same permissions as the Upload directory.

Got it.. I had to edit the proftpd.conf file and add this to the bottom and restart the proftpd server 
```
<Directory> /home/FTP-shared/www/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
```

---

### Post by dannyboy79 on 2006-10-06
Frodon, you helped me setup my ftp server and i thank you for that. but for some reason i all of a sudden can't view any of my ftp directories. when i ftp in all i see is a blank list, meaning it is hsowing me nothing? here is my proftpd.conf
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on
# Choose here the user alias you want !!!!
UserAlias daniel ftp
ServerName "UBUNTU FTP Server"
ServerType 			standalone
DeferWelcome			on
MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off
TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 600
DisplayFirstChdir               .message
ListOptions                	"-l"
RequireValidShell 		off
TimeoutLogin 20
RootLogin 			off
# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog 		/var/log/syslog.log
#DenyFilter			\*.*/
# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off
# Allow to restart a download
AllowStoreRestart on
Port				21
# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8
# Set the user and group that the server normally runs at.
User nobody
Group nogroup
# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022
PersistentPasswd		off
MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8
# Display a message after a successful login
AccessGrantMsg "YOU MADE IT!"
# This message is displayed for each access good or not
ServerIdent on "you're at home"
# Set /home/ftp directory as home directory
DefaultRoot /home/ftp
# Lock all the users in home directory, ***** really important *****
DefaultRoot ~
MaxLoginAttempts 5
UseReverseDNS                   off
IdentLookups                    off
#VALID LOGINS
<Limit LOGIN>
AllowUser ftp
DenyALL
</Limit>
<Directory /home/ftp>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>
<Directory /home/ftp/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>
<Directory> /home/ftp/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ DELE>
      	DenyAll
    	</Limit>
    	<Limit STOR RMD RNFR RNTO CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
#added for encrypting all transfers thru ssh and ssl
<IfModule mod_tls.c>
TLSEngine on
TLSLog Log /var/ftpd/tls.log
TLSProtocol TLSv1
    # Are clients required to use FTP over TLS when talking to this server?
TLSRequired off
    # Server's certificate
TLSRSACertificateFile /etc/ftpcert/server.crt
    TLSRSACertificateKeyFile /etc/ftpcert/server.key
    # CA the server trusts
    TLSCACertificateFile /etc/ftpcert/ca.crt
    # Authenticate clients that want to use FTP over TLS?
TLSVerifyClient off
</IfModule>

this happened to me out of no where so then i tried instaling gproftpd and using that and I couldn't really understand hot to use it so i just went back to view my conf file and gproftpd messed it up, it added things in the middle of lines, the word col and ile were put between some options so I kept getting errors when i would try to restart the server, so i found the bad line, fixed it but I still only can log in and SEE NOTHING? can you help me? i would like t point out that it did work great, i have all the folders created and they are there inside the /home/ftp/ location. what could be wrong?  thank you if you can help

---

### Post by frodon on 2006-10-06
Your proftpd.conf file looks good, except a system rights problem on the directories you use i don't see what could be the problem.

---

### Post by dannyboy79 on 2006-10-06
Could you explain the problem you see with the system rights problem I use? Also, I am now outside my lan and everything is ok? So basically when I use FlashFXP from my WINXP machine within my LAN it doesn't show any dir's. it only shows a \ and that's it? Weird? I am trying to learn about Passive vs Active and I am curious as to how am I able to get a Passive FTP session from my work to my server when my server is behind a netgear firewall and I know that the only ports forwarded are 20 and 21. i read that Active FTP is beneficial to the FTP server admin, but detrimental to the client side admin. The FTP server attempts to make connections to random high ports on the client, which would almost certainly be blocked by a firewall on the client side. Passive FTP is beneficial to the client, but detrimental to the FTP server admin. The client will make both connections to the server, but one of them will be to a random high port, which would almost certainly be blocked by a firewall on the server side. 

so if my firewall should be blocking all those higher ports how is passive mode working? thanks for your help!

---

### Post by compir99 on 2006-10-08
frodon,

I want to share '/media/ftp' by FTP with 3 users: admin, download, & look. The admin user has the ability to do anything; the download user has the ablity to download and upload; and the look user can only browse the FTP. The download user can download from anywhere whil he can only upload to '/media/ftp/uploads'

All users have the default root of '/media/ftp' but each user has different file and folder permissions.

Is this possible to do? I've been killing myself for hours trying to find an answer. If it's not possible, please tell me so I can think of another way to do this. Thanks! :)

---

### Post by frodon on 2006-10-08
I think it's possible using the some "ifuser" sections inside each "directory" section. Here is a reference page on the topic :
[http://www.castaglia.org/proftpd/modules/mod_ifsession.html](http://www.castaglia.org/proftpd/modules/mod_ifsession.html)

@dannyboy79, for the moment i have no idea but i will have a look at it this week, anyway don't forget to post your problem on the proftpd forum, this forum is damn helpful :
[http://forums.proftpd.org/phpBB2/](http://forums.proftpd.org/phpBB2/)

---

### Post by compir99 on 2006-10-08
Thanks frodon but the good folks at #proftpd helped me out. I finally got it working a few hours ago. Thanks!

> **dannyboy79 said:**
> Could you explain the problem you see with the system rights problem I use? Also, I am now outside my lan and everything is ok? So basically when I use FlashFXP from my WINXP machine within my LAN it doesn't show any dir's. it only shows a \ and that's it? Weird? I am trying to learn about Passive vs Active and I am curious as to how am I able to get a Passive FTP session from my work to my server when my server is behind a netgear firewall and I know that the only ports forwarded are 20 and 21. i read that Active FTP is beneficial to the FTP server admin, but detrimental to the client side admin. The FTP server attempts to make connections to random high ports on the client, which would almost certainly be blocked by a firewall on the client side. Passive FTP is beneficial to the client, but detrimental to the FTP server admin. The client will make both connections to the server, but one of them will be to a random high port, which would almost certainly be blocked by a firewall on the server side. 

so if my firewall should be blocking all those higher ports how is passive mode working? thanks for your help!

Dannyboy,

I had the same problem. But the folks @ #proftpd told me to make sure that "DIRS" and "PORT" was ALLOWED in the Limit brackets. See if that helps.

---

### Post by dannyboy79 on 2006-10-09
> **compir99 said:**
> Thanks frodon but the good folks at #proftpd helped me out. I finally got it working a few hours ago. Thanks!



Dannyboy,

I had the same problem. But the folks @ #proftpd told me to make sure that "DIRS" and "PORT" was ALLOWED in the Limit brackets. See if that helps.

Thanks for the suggestion however there are tons of locations where it says, LIMIT, so I have no idea where you want me to put DIRS and PORT? Can you please post your proftpd.conf? or maybe just one little area showing the example and then explain where else I need to do it. thanks so much for your help!

---

### Post by sega on 2006-10-12
Is it possible to get gproftpd to work in implicit ssl mode and not just in Auth SSL/TLS ?

---

### Post by leteci on 2006-10-13
If I use port 21 for server, i can see directory listing. If i use different port like 1980, than i get error: Could not retrieve directory listing. Ftp client is FileZilla. use passive mode.

thnx.

---

### Post by dannyboy79 on 2006-10-13
i am trying to bind /home/daniel to /home/ftp/daniel. it appears to work but when i click on a folder within /home/daniel for example 300gb-ext3 there are no sub-folders which there should be??? What's weird is when I bind location /home/daniel/300gb-ext3 to /home/ftp/daniel that works, they'll be sub-folders upon sub-folders and files shown. This is using filezilla. i checked all the permissions of the folders and they appear to be the same and appear to be owned by me. I am logging into my ftp server as a user which gets jailed into /home/ftp. why does it show sub-dir's upon sub-dirs when i bind /home/daniel/300gb-ext3 but not when i bind /home/daniel?

---

### Post by jaywatkins on 2006-10-24
The tutorial worked for me, thanks Frodon!

I do have to say it is much easier on Windows Server 2003/Windows 2000 Server, but that many be because I understand them much more...

Thanx, great stuff...

/N

---

### Post by johnny9794 on 2006-10-31
Great tutorial on B- The secure way :) very very Great job!!!

Thanx Frodon and the ppl that helped Frodon out on the tutorial about the router and everything else :D

---

### Post by frodon on 2006-10-31
Glad to know that you like the tutorial, i hope no one will be scared anymore to set a FTP server on ubuntu.

---

### Post by jms1989 on 2006-11-03
> **frodon said:**
> Glad to know that you like the tutorial, i hope no one will be scared anymore to set a FTP server on ubuntu.

I need a little help here!! I'm having trouble logging into my FTP server, I type in the username and password, and it tells me invalid password. I know it's correct.

---

### Post by Darrious on 2006-11-04
This is the very first time that I have ever set up a server, and I have no idea how to do it. All I did was I turned on gproftpd, then I created a user. I created a server.... I think. I really do not know how to actually make one using gproftpd. I type in the ip address on my computer, and the domain I want, go through all the stuff that you need to fill out, and click generate certificate. It does... something. I do not know what clicking that actually does. I just want a server that people can connect to, host their files from, and have their own domain.

---

### Post by saxin on 2006-11-04
I have been using this guide to set up my own FTP-server, with gProftpd. Everyhing working great, untill yesterday. I can log in, but it just stops when it tries to list the file names.. 
"Loading directory listing / from server (LC_TIME=en_AU.UTF-8)
PASV
227 Entering Passive Mode (192.168.1.254,205,92)."


Any suggestions for this? Is it the setup, or something with the net?

---

### Post by snappy.tom on 2006-11-05
i'm not sure if this has been covered or not, but i've got current system users with their own home dir /home/username, but what gproftpd does, when i add those current users as an ftp user aswell, is that it allows me to choose an ftp home dir without changing the original home dir of /home/username. the new ftp home dir is /var/www/username.

i was wondering, is it possible to do what gproftpd does, except via command line?

this would save me from using gnome/xserver window manager

cheers

---

### Post by frodon on 2006-11-05
> **jms1989 said:**
> I need a little help here!! I'm having trouble logging into my FTP server, I type in the username and password, and it tells me invalid password. I know it's correct.Do you get the 530 errors ?
Checks the permission of the folder you share with your server and try to create again your user using the GUI.

> **Darrious said:**
> This is the very first time that I have ever set up a server, and I have no idea how to do it. All I did was I turned on gproftpd, then I created a user. I created a server.... I think. I really do not know how to actually make one using gproftpd. I type in the ip address on my computer, and the domain I want, go through all the stuff that you need to fill out, and click generate certificate. It does... something. I do not know what clicking that actually does. I just want a server that people can connect to, host their files from, and have their own domain.Sorry, but i can't really help you with gproftpd because i almost never used it but maybe some users who use it may be able to help you

> **saxin said:**
> I have been using this guide to set up my own FTP-server, with gProftpd. Everyhing working great, untill yesterday. I can log in, but it just stops when it tries to list the file names.. 
"Loading directory listing / from server (LC_TIME=en_AU.UTF-8)
PASV
227 Entering Passive Mode (192.168.1.254,205,92)."


Any suggestions for this? Is it the setup, or something with the net?Do you have more error log ?
Check the permissions of the folders you share, wrong permission can generate this issue.

> **snappy.tom said:**
> i'm not sure if this has been covered or not, but i've got current system users with their own home dir /home/username, but what gproftpd does, when i add those current users as an ftp user aswell, is that it allows me to choose an ftp home dir without changing the original home dir of /home/username. the new ftp home dir is /var/www/username.

i was wondering, is it possible to do what gproftpd does, except via command line?

this would save me from using gnome/xserver window manager

cheersThe way gproftpd share the directories is not really secure so i don't advice you to try to do the same thing. But yes you can do the same thing, it is just not enough secure IMO. Modifying the original home directory is more secure IMO.

---

### Post by blacha on 2006-11-07
Hi, 
I'm having some problems here..

I had some older version of proftpd which i chose to remove (by synaptic)
But as i discovered not all files were removed :confused: 

After going through your how-to (great job btw !) i've noticed that at the end, old conf file was being loaded.

Then I manualy removed proftpd.conf from /etc and from /etc/proftpd/
and also startup script from init.d

After another reinstall I'm missing startup script ](*,) Shouldn't it be recreated at apt-get install ?

any thoughts on working this out ?

help.

---

### Post by dannyboy79 on 2006-11-08
> **blacha said:**
> Hi, 
I'm having some problems here..

I had some older version of proftpd which i chose to remove (by synaptic)
But as i discovered not all files were removed :confused: 

After going through your how-to (great job btw !) i've noticed that at the end, old conf file was being loaded.

Then I manualy removed proftpd.conf from /etc and from /etc/proftpd/
and also startup script from init.d

After another reinstall I'm missing startup script ](*,) Shouldn't it be recreated at apt-get install ?

any thoughts on working this out ?

help.


why don't you try to go sudo aptitude remove proftpd && aptitude purge proftpd 

this should get rid of anything related to proftpd. just so you know though, the  newest proftpd from the repos doesn't have mod_tls compiled into  it so you can't connect to your server using any kind of encryption. if you want encrytpion, you'll ahve to compile the newest source by hand. i did start a thread for this and frodon informed the developers. (i hope)

---

### Post by salvo1 on 2006-11-14
What a thread!!!!

This is my problem:
I log-in using my unix user "surname.name" and then i see my root (/home/surname.name/) but, there, i can see also "/home/surname.name/Maildir" that is to say mail folder.

How can i modify proftpd.conf to hide /home/*/Maildir folder (that every user see as "/Maildir") to all users?

Thanks in advance,
Salvo

---

### Post by frodon on 2006-11-14
Try adding this at the end of your config file :```
<Directory /home/surname.name/Maildir/>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
		Order Allow,Deny
		Deny ALL
	</Limit>
</Directory>
```Then restart your server, if it works you should be able to see the directory but you won't be able to enter in.

Let me know if it works.

---

### Post by salvo1 on 2006-11-15
> **frodon said:**
> Try adding this at the end of your config file :```
<Directory /home/surname.name/Maildir/>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
		Order Allow,Deny
		Deny ALL
	</Limit>
</Directory>
```Then restart your server, if it works you should be able to see the directory but you won't be able to enter in.

Let me know if it works.

I already tried this: 

> < Directory /home/*/Maildir >
   < Limit READ WRITE >
             DenyAll
   < /Limit >
< /Directory >


But it doesn't work

Then I tried this:

> < Directory ~/Maildir >
   < Limit READ WRITE >
             DenyAll
   < /Limit >
< /Directory >

I can see the folder, enter, write...

Using your code (modified with /home/*/Maildir), it works... 

Thanks you!

---

### Post by n8bounds on 2006-11-16
I just wanted to say thanks.  This works great.  Your conf file was full of good hints--I didn't copy/paste, but reading through your post help me understand what was going on.

---

### Post by dannyboy79 on 2006-11-16
i gave out the alias I was using to login to my server to someone and now I don't want them to have access anymore so i changed the useralias and the password for the linux user ftp, but when I try to log into the server, the server won't accept the new alias, it does work with the old alias and the new password so he wont be able to login anymore which is what I want, but he stil knows the alias, YES I DID restart the server after changing the useralias in my proftpd.conf file? does anyone know why the new useralias isn't working?? do I need to restart my whole computer? i have restarted the server by doing sudo /etc/init.d/proftpd restart many times but I shouldn't have to do this as I run my server thru inited not as a standalone, so i am undert the impression that each time a user trys to log in, it starts up the server with the latest config each time so a server restart isn't required that's the advantage of inited instead of standalone but why isn't it working? anyone wanna help. Frodon maybe wanna help me? or are you still mad at me for asking for you know what?

---

### Post by frodon on 2006-11-16
Knowing your story about proftpd, i mean that you updated to the 1.3 version which don't use the same path for the config file i guess you modifyed the old config file under /etc/proftpd.conf rather than the one under /etc/proftpd/proftpd.conf which is i believe now the new one used in proftpd 1.3, it really sounds like this kind of stuff.

Try to search for mistakes in this spirit and i'm sure you will solve quickly your issue.

---

### Post by dannyboy79 on 2006-11-16
thank you very much however this has brought up another problem! i just realized tha tI have been running my server as standalone and this whole time I thought I was running it thru inetd. now that I want to switch it I am getting all screwed up with inetd, inetd.conf, xinetd, xinetd.conf, xinetd.d and all this stuff. i am wondering I can uninstall inetd and just use xinetd? I have xinetd installed as I had to to get swat to work I think? currently there is a line within my inetd.conf file that I am not sure what'll happen if I remove inetd, it states this:
netbios-ssn stream tcp nowait root  /usr/sbin/tcpd      /usr/sbin/smbd

does anyone know if I need this line for samba to work since I see it has something to do with netbios but I don't know what ssn is??

i have just decided to compile version 1.3 with all the goodie modules that came with proftpd's source. i am  not going to compile it with any of the 3rd party modules although some may be useful I haven't needed them yet so I don't think i will ever need them. if I do I can always compile again. this should be interesting, if it all works out, i'll look into making a .deb for everyone.

---

### Post by slk230mb on 2006-11-22
I'm having some issues trying to install proftpd on a new install. I try the command sudo apt-get install proftpd gproftpd and I get the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gproftpd

Any ideas on how to resolve this problem? I've tried updating my sources.list but that hasn't worked. I've googled and searched this forum and I haven't found anything useful. Thanks in advance.

Steve
a linux noob

---

### Post by frodon on 2006-11-22
I see the packet without any problems so i think it may come from your sources.list file, could you post it there ?

Thanks

---

### Post by slk230mb on 2006-11-22
> **frodon said:**
> I see the packet without any problems so i think it may come from your sources.list file, could you post it there ?

Thanks

It's attached. Thanks again.

---

### Post by frodon on 2006-11-22
Ok, i got it.

You're using breezy and gproftpd is in the repository only since dapper, however i made a .deb file at the time but i'm not sure it's the latest version, check if it is.

To install it type in a terminal (in the directory of your choice) :

---

### Post by slk230mb on 2006-11-22
Thanks, that did the trick. I got the ftp server up and running, now I can play around with the options and get it the way I want. :KS

---

### Post by Forgott3n on 2006-11-23
I royally messed up with the configuration of ProFTPD.. How do I uninstall the whole thing?

And I am a bit confused... How do I make a user with a username and password with full access to /var/www/?

```
ftp://user:pword@ftp.somehost.com
```

---

### Post by frodon on 2006-11-24
to unsintall : ```
sudo apt-get remove proftp
```Replace : ```
DefaultRoot /home/FTP-shared
``` by ```
DefaultRoot /var/www/
``` and set set /var/www/ as home directory for this user.
You create the user like all other system users.

---

### Post by frodon on 2006-11-24
Just for those who don't know this link, you will find all you need for a mor e advanced use of proftpd there :
[http://www.castaglia.org/proftpd/](http://www.castaglia.org/proftpd/)

---

### Post by Forgott3n on 2006-11-24
> **frodon said:**
> to unsintall : ```
sudo apt-get remove proftp
```Replace : ```
DefaultRoot /home/FTP-shared
``` by ```
DefaultRoot /var/www/
``` and set set /var/www/ as home directory for this user.
You create the user like all other system users.

Thanks for your help. But I am having issues with the user.

Since I am using Edgy Eft, I am experiencing the "[You are not allowed to access the system configuration.](http://ubuntuforums.org/showthread.php?t=286260)" bug and therefore must do everything by terminal.

I have, and successfully, tried to login as "justin" (my standard ubuntu login name). Despite the LIST -aL command taking forever to execute, I get a 550 (Permission Denied) for all commands and transfer attempts.

I put
```
<Directory /var/www/>
  <Limit All>
    AllowAll
  </Limit>
</Directory>
``` in the proftpd.conf with no avail.


Thanks for the help!

---

### Post by frodon on 2006-11-24
Try adding this in your directory section instead of what you have, just to be sure : ```
    	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
```

---

### Post by Forgott3n on 2006-11-24
```
[07:40:50] Resolving host name "forgotten.no-ip.info"
[07:40:50] Connecting to 66.183.94.100 Port: 21
[07:40:50] Connected to forgotten.no-ip.info.
[07:41:10] 220 ProFTPD 1.3.0 Server (Forgott3n's FTP Daemon) [::ffff:192.168.1.102]
[07:41:10] USER justin
[07:41:10] 331 Password required for justin.
[07:41:10] PASS (hidden)
[07:41:14] 230 User justin logged in.
[07:41:14] SYST
[07:41:14] 215 UNIX Type: L8
[07:41:14] Detected Server Type: UNIX
[07:41:14] FEAT
[07:41:14] 211-Features:
[07:41:14]  MDTM
[07:41:14]  REST STREAM
[07:41:14]  SIZE
[07:41:14] 211 End
[07:41:14] PWD
[07:41:14] 257 "/" is current directory.
[07:41:14] MKD test
[07:41:14] 550 test: Permission denied
```

Still isn't working. Could this be linked with the bug?

---

### Post by frodon on 2006-11-24
Ok, then now check that your "/var/www/" directory have 777 rights which is needed to download/upload in the directory.

If not give the directory 777 rights and test again.

---

### Post by IanVaughan on 2006-11-24
I get the following error, Im not sure 
```
 - IPv4 getaddrinfo 'homer' error: Name or service not known
 - warning: unable to determine IP address of 'homer'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd.conf'
```

---

### Post by Forgott3n on 2006-11-25
> **frodon said:**
> Ok, then now check that your "/var/www/" directory have 777 rights which is needed to download/upload in the directory.

If not give the directory 777 rights and test again.

Haha silly me, forgot to CHMOD the folder.


Quick question: how do I speed up LIST -aL? Its very slow to do anything with a good 10 second wait per file.

---

### Post by disc on 2006-11-25
I followed the walk through, and did everything as instructed, then when I try to ```
sudo /etc/init.d/proftpd start
``` it gives me ```
 - IPv6 getaddrinfo 'ryan-desktop' error: Name or service not known
ryan-desktop - 127.0.1.1:1980 masquerading as xx.xx.xx.xxx
                                                                         [ ok ]

```

Is this normal? If not, any ideas what could be wrong?

(I removed my IP address, it isn't actually masquerading as xx.xx.xx.xxx)

---

### Post by frodon on 2006-11-25
Yes it's normal, it's just an informative message and it won't hurt the behaviour of your FTP server. See the proftpd forum if you want more detailled informations on this message.

@Forgott3n, i would have loved to help you more but you reached the limit of my knowledge lol, anyway if you post your question on the proftpd forum i'm sure you will get an answer because this forum is watched by the proftpd maintainer who always give nice advices :
[http://forums.proftpd.org/phpBB2/](http://forums.proftpd.org/phpBB2/)

---

### Post by disc on 2006-11-25
I'm a bit confused, am I suppose to be able to access my server through [ftp://xx.xx.xx.xxx/](ftp://xx.xx.xx.xxx/), because it times out everytime I try it.

Edit: When I try to connect using gFTP, it causes gFTP to freeze, and thus I can't connect to my server.

---

### Post by chris23 on 2006-11-25
I've setup Gproftpd.
And in the default folder /var/ftp i've mounted 2 other folders from another partition, as the "how to " says
The partitions have been mounted correctly.
The problem is that when accessing the ftp,users don't have to access to the mounted folders (550).
I set chmod 777 for the /var/ftp/upload and 755 for /var/ftp/download.

any help?

---

### Post by slk230mb on 2006-11-25
Ok, since I got the ftp setup on my machine a friend asked me for help doing his. While I was running sudo apt-get install proftpd there was a power surge in his room and it caused the machine to reboot. Now when I run the command I get the following error from terminal:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Any ideas on the solution? I'm sure what needs to be in front of the dpkg line.

Thanks for any help, as always.

Edit - I figured it out.

---

### Post by glenncruz on 2006-11-29
hello just want to ask if it is possible to have multiple account in just one proftpd configuration? if yes how. thanks :)

---

### Post by frodon on 2006-11-29
I always answer why to this question.

What is your need to have several FTP users ?

Of course it's possible and there's mutiple ways to do it depending on what is your goal, tell me what is your need and i will explain you the most suitable way to do it.

---

### Post by frodon on 2006-11-29
> **chris23 said:**
> I've setup Gproftpd.
And in the default folder /var/ftp i've mounted 2 other folders from another partition, as the "how to " says
The partitions have been mounted correctly.
The problem is that when accessing the ftp,users don't have to access to the mounted folders (550).
I set chmod 777 for the /var/ftp/upload and 755 for /var/ftp/download.

any help?The 2 folders you mounted from the other partition must have the good rights too, because when you mount a folder in another one it overwrites the permissions of the destination folder.

---

### Post by chris23 on 2006-11-29
> **frodon said:**
> The 2 folders you mounted from the other partition must have the good rights too, because when you mount a folder in another one it overwrites the permissions of the destination folder.


yes the two folders that i mount have the good rights.
...

---

### Post by glenncruz on 2006-11-29
> **frodon said:**
> I always answer why to this question.

What is your need to have several FTP users ?

Of course it's possible and there's mutiple ways to do it depending on what is your goal, tell me what is your need and i will explain you the most suitable way to do it.

Hello Sir Frodon

I need multiple user to my ftp server so i could assign one username and password to each person and on each account has their own download and upload folders so not to mix up all of their files. :)

---

### Post by frodon on 2006-11-30
Ok, i understand what you mean.

The question is do you want completely separate directories for each user, i mean one directory for user A which contain one upload and one download directory ?
Or if we put all the directories under "FTP-shared" is it ok for you ?, i mean for example :
userA-download
userA-upload
userB-download
userB-upload
...
The second way is easier and more secure IMO, the second part of the "Advanced tricks" section will show you how to do it. The only inconvenient is that when you login each user will see all the directories but will be able to enter only in the one he has the rights for.
However if it's really annoying for you i can read some documentation because i read at the time somewhere that it's possible to hide the directories.

---

### Post by glenncruz on 2006-11-30
> **frodon said:**
> Ok, i understand what you mean.

The question is do you want completely separate directories for each user, i mean one directory for user A which contain one upload and one download directory ?



Yes sir Frodon 1 directory for 1 user! Thanks a lot for the help :)

---

### Post by frodon on 2006-11-30
mmm, not sure to know how to do it that way :-k

---

### Post by glenncruz on 2006-12-02
> Or if we put all the directories under "FTP-shared" is it ok for you ?, i mean for example :
userA-download
userA-upload
userB-download
userB-upload

ok sir can we this? :)

---

### Post by glenncruz on 2006-12-02
> Or if we put all the directories under "FTP-shared" is it ok for you ?, i mean for example :
userA-download
userA-upload
userB-download
userB-upload

ok sir can we do this? :)

---

### Post by frodon on 2006-12-02
Yes of course, it is explained in the "advanced tricks" part of the guide in the first post.
All you need is to create the users, create all the directoties then restrict the access depending of the user.

---

### Post by glenncruz on 2006-12-03
> **frodon said:**
> Yes of course, it is explained in the "advanced tricks" part of the guide in the first post.
All you need is to create the users, create all the directoties then restrict the access depending of the user.

ok sir will do! Give u feedback. Thanks again :KS

---

### Post by guetrochide on 2006-12-03
i think i've found a great source[,]("http://i-gunler.com/section/eventview.php?sec=60&Date=1&Day=3&Month=12&Year=2002&Page_Num=1") thank you so much[.]("http://i-gunler.com/section/eventview.php?sec=60&Date=1&Day=3&Month=12&Year=2002&Page_Num=1")[.]("http://i-gunler.com/section/eventview.php?sec=60&Date=1&Day=3&Month=12&Year=2002&Page_Num=1")

---

### Post by NumberOne on 2006-12-03
Maybe someon can help.  I've followed all the instructions on how to setup the FTP server.  When I try to restart the server I get this error:

..localhost - mod_delay/0.4: error opening DelayTable '/var/run/proftpd/proftpd.delay': No such file or directory

Everything is setup as outlined in the first post.  I don't think this has to do with config, my guess is there is something wrong with the install.  I've tried uninstalling completly and then reinstalling, but I get the same error.

How do I fix this?
Thanks.

---

### Post by ikkinu on 2006-12-05
**[SIZE=2]1- Enable TLS/SSL encryption (FTPS)[/SIZE]** 
The FTP file sharing protocol is an old protocol which was created when internet was still a secure place, therefore the default FTP protocol is not that secure.
For example the password and username for login are transmitted in plain text which obviously isn't secure.
That why, to fit the needs of our generation, encryption solutions were developed and one of them is TLS/SSH encryption.
This will encrypt the username and password and all the data you send, obviously to use it the FTP client must support SFTP protocol.

here are the steps to enable TLS/SSH encryption ([FTPS]("http://en.wikipedia.org/wiki/FTPS")):

Paste these commands in a terminal :```
sudo apt-get install build-essential
sudo apt-get install libssl-dev
cd /etc
sudo mkdir ftpcert
cd ftpcert/
sudo openssl genrsa -des3 -out server.key 1024
sudo openssl req -new -key server.key -out server.csr
sudo openssl genrsa -des3 -out ca.key 1024
sudo openssl req -new -x509 -days 365 -key ca.key -out ca.crt 
sudo wget http://frodubuntu.free.fr/ubuntu/sign.sh
sudo chmod +x sign.sh
sudo ./sign.sh server.csr 
```

HI all,
when I type sudo ./sign.sh server.csr I get this error:

CA signing: server.csr -> server.crt:
Using configuration from ca.config
Enter pass phrase for ./ca.key:
Check that the request matches the signature
Signature ok
The Subject's Distinguished Name is as follows
countryName           :PRINTABLE:'IL'
stateOrProvinceName   :PRINTABLE:'Ikkland'
localityName          :PRINTABLE:'Ikktown'
organizationName      :PRINTABLE:'Project ikkinu'
organizationalUnitName:PRINTABLE:'Ftp Dpt.'
commonName            :PRINTABLE:'ikkinu'
emailAddress          :IA5STRING:'ikkinu@inventati.org'
Certificate is to be certified until Dec  5 19:24:50 2007 GMT (365 days)
Sign the certificate? [y/n]:y


1 out of 1 certificate requests certified, commit? [y/n]y
Write out database with 1 new entries
Data Base Updated
CA verifying: server.crt <-> CA cert
server.crt: /C=IL/ST=Ikkland/L=Ikktown/O=Project ikkinu/OU=Ftp Dpt./CN=ikkinu/emailAddress=xxx@xxx.xxx
error 18 at 0 depth lookup:self signed certificate
/C=IL/ST=Ikkland/L=Ikktown/O=Project ikkinu/OU=Ftp Dpt./CN=ikkinu/emailAddress=xxx@xxx.xxx
error 7 at 0 depth lookup:certificate signature failure
12603:error:04067084:rsa routines:RSA_EAY_PUBLIC_DECRYPT:data too large for modulus:rsa_eay.c:645:
12603:error:0D0C5006:asn1 encoding routines:ASN1_item_verify:EVP lib:a_verify.c:168:

Can anyone help me?
Thanks

---

### Post by dannyboy79 on 2006-12-05
this happened to me, I couldn't figure it out so I just performed the steps over and over again, chosing different names for each of the prompts and finally it worked. don't know what exactly made it work but it did. for country name, I put US, for state I spelled out WISCONSIN, for city I spellled out my city, for company name I put NA1 (not applicable 1) for org unit name, I put not applicable 1 (spelled out this time), for commmon name I spelled out my first name, for email, I put my real email address. that is all for server.key, then for the next one, I think it was ca.key, I did everything the same except added "2" instead of the "1" where I used NA and not applicable. good luck. I have to be honest, despite not getting errors when I self signed the certificate, I still can't even ftp into my site. I use xinetd which may be the problem. also, are you using the new mod_tls by way of mod_dso? good luck

---

### Post by dannyboy79 on 2006-12-05
> **NumberOne said:**
> Maybe someon can help.  I've followed all the instructions on how to setup the FTP server.  When I try to restart the server I get this error:

..localhost - mod_delay/0.4: error opening DelayTable '/var/run/proftpd/proftpd.delay': No such file or directory

Everything is setup as outlined in the first post.  I don't think this has to do with config, my guess is there is something wrong with the install.  I've tried uninstalling completly and then reinstalling, but I get the same error.

How do I fix this?
Thanks.


you simply need to create the /var/run/proftpd/ dir and you'll be set. I don't know why it wouldn't have been created wehen you installed Proftpd. unless you compiled it yourself, since I did, I had that same error as well. For the future, if it tells you that a  file or folder doesn't exist, then do a locate or find for it and if  the folder isn't there, then linux needs you to create the folder so that proftpd has a place to put the proftpd.delay file when you log into your server. good luck

---

### Post by glenncruz on 2006-12-05
> **frodon said:**
> Yes of course, it is explained in the "advanced tricks" part of the guide in the first post.
All you need is to create the users, create all the directoties then restrict the access depending of the user.

Hello Sir Frodon

my ftp work with multiple users but one question is there a way to hide the download folders on the other accounts? :)

---

### Post by frodon on 2006-12-06
I know there is one but i don't remember exactly where i read that so i would have to search a little bit, give me one week and i will try to give you an answer.
Feel free to PM me in one week to remind me your question if i forgot to search ;)

---

### Post by dannyboy79 on 2006-12-07
> **NumberOne said:**
> Maybe someon can help.  I've followed all the instructions on how to setup the FTP server.  When I try to restart the server I get this error:

..localhost - mod_delay/0.4: error opening DelayTable '/var/run/proftpd/proftpd.delay': No such file or directory

Everything is setup as outlined in the first post.  I don't think this has to do with config, my guess is there is something wrong with the install.  I've tried uninstalling completly and then reinstalling, but I get the same error.

How do I fix this?
Thanks.


simply create the folder /var/run/proftpd/ and you should be fine! proftpd is telling you that it can't create the file because the directory isn't there, so create the dir, and then the server will be able to create the file when some1 tried to connect and all will be good. this happened to me because I compiled version 1.3 myself and I needed to create this folder for the scoreboard file as well as the delay file.

---

### Post by frodon on 2006-12-13
> **glenncruz said:**
> Hello Sir Frodon

my ftp work with multiple users but one question is there a way to hide the download folders on the other accounts? :)Ok, the command to do this is [HideNoAccess]("http://www.proftpd.org/localsite/Userguide/linked/config_ref_HideNoAccess.html").

In each directory section try adind this command the beginning, example :
```
Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
**[COLOR="Red"]HideNoAccess on[/COLOR]**

        <Limit ALL>
		Order Allow,Deny
		AllowUser user1
		Deny ALL
	</Limit>

	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>
```I'm not sure it will work because i never used it.

I found an interesting thread for you where a user is trying to configure his server in the same way than you :
[http://forums.proftpd.org/phpBB2/viewtopic.php?t=172&highlight=hidenoaccess](http://forums.proftpd.org/phpBB2/viewtopic.php?t=172&highlight=hidenoaccess)

---

### Post by addicted_to_the_net on 2006-12-16
Hi, just a note on the TLS part of your excellent HowTo.  I found that the server would disconnect immediatly after the TLS handshake, this is what it said in the log:

ssl3_get_record:wrong version number

Found the fix on this site: [http://forums.proftpd.org/phpBB2/viewtopic.php?t=1075&]("http://forums.proftpd.org/phpBB2/viewtopic.php?t=1075&")

Basically I changed the entry "TLSProtocol TLSv1" found in the proftpd.conf file to read "TLSProtocol SSLv23" and it worked after the restart of proftpd.

Does this sound right?  Anyone else have this problem?  

Also just to clarify, when I removed the password for the rsa key (so that I didn't have to enter everytime the server starts) your guide says to make the file accessable only for root.  How would I do this? (still learning) 

Thank you very much

---

### Post by knoc on 2006-12-29
I'm new to this so here is a pretty basic question:

What would my ftp address be if I were to access my FTP server from a browser? Is gFTP the only way to access it?

:confused:

---

### Post by stijn_pol on 2007-01-05
> **knoc said:**
> I'm new to this so here is a pretty basic question:

What would my ftp address be if I were to access my FTP server from a browser? Is gFTP the only way to access it?

:confused:

You need to know 2 things to access your FTP server: IP-address en port number. When trying to access your FTP server in a LAN, use your local IP-address to test the connection with the server.  For example: 192.168.1.101 with port 1980, this goes for gFTP.
Using a browser you should go to the following URL: [ftp://192.168.1.101:1980](ftp://192.168.1.101:1980).
Voila, my first post!!

UBUNTU YEAH!

---

### Post by The_Apprentice on 2007-01-06
Sorry to drag this up again, but I am getting the 530 error.

I have configured it exactly as the first post

> # To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias sauron userftp

ServerName			"woodside"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
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

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>


I have confirmed the CHMODs
I have created the user (userftp) from both the command line and the GUI
I have tested from both the local machine and a remote, through both IE, CLI and GUI.

> *********@woodside:~$ ftp localhost
Connected to localhost.
220 you're at home
Name (localhost:sean): userftp
331 Password required for userftp.
Password:
530 Login incorrect.
Login failed.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> quit
221 Goodbye.


Pretty please can someone help get my sanity back   ](*,)




EDIT:

Mmmmmmmm, this may be a clue, but I know not what :$

> Jan 06 21:18:28 woodside proftpd[6889] localhost (localhost[127.0.0.1]): FTP session opened.
Jan 06 21:18:38 woodside proftpd[6889] localhost (localhost[127.0.0.1]): USER userftp: user is not a UserAlias from localhost [127.0.0.1] to 127.0.0.1:21
Jan 06 21:18:44 woodside proftpd[6889] localhost (localhost[127.0.0.1]): FTP session closed.


---

### Post by stijn_pol on 2007-01-09
When using UserAliases like in your code:
-> UserAlias sauron userftp
You must login using the configured alias.
So login with sauron. Or remove the the UserAlias line in your code.
Yo!

---

### Post by The_Apprentice on 2007-01-09
LOL  

It just goes to show that the more you look at something the less you see :$

It works on localhost, just need to sort my router out.

Many many thanks

---

### Post by espo100583 on 2007-01-10
Hi Guys,

I have the following problem and no idea what to do so any heko would be great.

When I try to start proftpd I get -mod_delay/0.4:error opening DelayTable /var/run/proftpd.deal':No Such file or directory

I have manually created the dir /var/run/proftpd using sudo mkdir /var/run/proftpd then when I run the deamon it works fine however when I reboot the dir is lost so I cannot run the deamon again without re creating the dir. ](*,) 

I would also like the ftp server to run on start up so an idea of how to get this working would be great.

Thanks

---

### Post by frodon on 2007-01-10
Do you use the mod_delay module ?

If not please post your proftpd.conf, tell me me which version of proftpd you use then if you use the 1.3 post your /etc/proftpd/modules.conf.

---

### Post by espo100583 on 2007-01-12
Thanks for the quick responce. I've managed to sort the dir problm out.

the only issue I have now is connecting to the server. I can connect from within the network fine, but when trying it from an external connection it connects but I cannot see anything in the directory. my FTP client gives the following message

```
Connecting to 80.41.35.132:22024
Connected to 80.41.35.132:22024 in 0.062440 seconds, Waiting for Server Response
220 My FTPD
Host type (1): Automatic Detect
USER espo100583
331 Password required for espo100583.
PASS (hidden)
230 Anonymous access granted, restrictions apply.
SYST
215 UNIX Type: L8
Host type (2): Unix (Standard)
PWD
257 "/" is current directory.
TYPE A200 Type set to A
PASV
227 Entering Passive Mode (192,168,0,4,197,240).
connecting data channel to 192.168.0.4:197,240(50672)
Substituting connection address 80.41.35.132 for private address 192.168.0.4 from PASV
PORT 10,1,37,100,5,5
200 PORT command successful
LIST
Error reading response from server.
It appears that the connection is dead.  Attempting reconnect...
```

any Ideas of what the problem may be would be great.

Thanks

---

### Post by Joviannm on 2007-01-19
First I would like to thank you for all the work you have put into this. I would also like to note I am a complete newbie not only to Ubuntu but also Linux so I may need things more details. Very sorry.

When trying to log in via FTP from a windows box to the Ubuntu.
Here is the information Filezilla my FTP software gives:

Status:	Connected with 192.168.1.103. Waiting for welcome message...
Response:	220 you're at home
Command:	USER userftp
Response:	331 Password required for userftp.
Command:	PASS ********
Response:	530 Login incorrect.
Error:	Unable to connect!

Here is my config

```
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias name userftp

ServerName "Ubuntu"
ServerType standalone
DeferWelcome on

UseReverseDNS off
IdentLookups off

MultilineRFC2228 on
DefaultServer on
ShowSymlinks off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir .message
ListOptions "-l"

RequireValidShell off

TimeoutLogin 99

RootLogin off

# It's better for debug to create log files
ExtendedLog /var/log/ftp.log
TransferLog /var/log/xferlog
SystemLog /var/log/syslog.log

#DenyFilter \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart on

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port 21

# To prevent DoS attacks, set the maximum number of child processes
# to 30. If you need to allow more than 30 concurrent connections
# at once, simply increase this value. Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User nobody
Group nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask 022 022

PersistentPasswd off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent on "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts 5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
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

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
<Limit READ RMD DELE>
DenyAll
</Limit>

<Limit STOR CWD MKD>
AllowAll
</Limit>
</Directory>
```


Here is the user I created:
[http://img407.imageshack.us/img407/8510/screenshot1hd3.png](http://img407.imageshack.us/img407/8510/screenshot1hd3.png)
[http://img187.imageshack.us/img187/4889/screenshot2xt4.png](http://img187.imageshack.us/img187/4889/screenshot2xt4.png)

For all I know I may just be screwing up on the user I am creating.

Thanks,
Jovian

---

### Post by addicted_to_the_net on 2007-01-19
> # Choose here the user alias you want !!!!
UserAlias name userftp



I think you have to log in as that alias "name"

---

### Post by Joviannm on 2007-01-19
Thanks addicted_to_the_net this kinda put me on the right track. I ended up testing it without the follow lines:

> AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias name userftp

This worked! now I just need to figure out what im doing wrong with my user account alias stuff.

---

### Post by addicted_to_the_net on 2007-01-19
What ever you use for the alias is the login name that you should use to login to the server. So like alias guest would mean, username "guest" password "the one you set for userftp".. Good luck!

---

### Post by Joviannm on 2007-01-19
Ok so your saying the Alias which by the guide is userftp, is the account name you would use to connect to the FTP server. I thought that was the user. So whats the user then? hehe thanks so much for your help.

---

### Post by addicted_to_the_net on 2007-01-20
Read the guide again and you will find all what you are looking for... Goodluck

---

### Post by Thyme on 2007-02-15
Hello everyone,

Frodon, thanks for this superb HOW-TO. I had a bit of a tough time setting up the SFTP part but nevertheless I persevered and in the process even setup an SSH server! Although it took me the WHOLE of today, you won't believe how much else I could get done since I didn't have to google for this-and-that, fix this-and-that etc...

I'm VERY impressed with the calibre of dedication and committment that this forum possessess.

Cheerio1

---

### Post by dadantada on 2007-02-17
I'm not sure if this should go in this thread, or in the ProFTPd through NAT thread. Either way, here goes:

Starting proftpd gives the following:

```
::dadantada01@dadantada3::/home/dadantada01::
 $ sudo /etc/init.d/proftpd restart
 * Stopping ftp server proftpd                                                                                                                         [ ok ]
 * Starting ftp server proftpd                                                                                                                                 - IPv6 getaddrinfo 'localhost.localdomain' error: Name or service not known
localhost.localdomain - 127.0.0.1:12345 masquerading as 123.456.789.101
```Where 123.456.789.101 is the external WAN IP, and 12345 is the port that I have fowarded on my router.

**/etc/proftpd/proftpd.conf** is as follows
```
#
# Includes required DSO modules. This is mandatory in proftpd 1.3
#
Include /etc/proftpd/modules.conf

# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias dadantada dadantadaftp

ServerName                      "ftpdadantada"
ServerType                      standalone
DeferWelcome                    on

MultilineRFC2228 on
DefaultServer                   on
ShowSymlinks                    off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                     "-l"

RequireValidShell               off

TimeoutLogin 20

RootLogin                       off

# It's better for debug to create log files ;-)
ExtendedLog                     /var/log/ftp.log
TransferLog                     /var/log/xferlog
SystemLog                       /var/log/syslog.log

#DenyFilter                     \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart               on

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
# Port                          21
Port                            12345

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022     022

PersistentPasswd                off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/ftp directory as home directory
DefaultRoot /home/ftp

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser dadantadaftp
DenyALL
</Limit>

<Directory /home/ftp>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

<Directory /home/ftp/download/*>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

<Directory /home/ftp/upload/*>
Umask 022 022
AllowOverwrite on
        <Limit READ RMD DELE>
        DenyAll
        </Limit>

        <Limit STOR CWD MKD>
        AllowAll
        </Limit>
</Directory>

MasqueradeAddress 123.456.789.101
PassivePorts 12345 12345
```

When I connect remotely (to 123.456.789.101:12345, with user dadantada), I get the following spiel:

```
	Status:	Connecting to 123.456.789.101:12345 ...
Status:	Connected with 123.456.789.101:12345. Waiting for welcome message...
Response:	220 you're at home
Command:	USER dadantada
Response:	331 Password required for dadantada.
Command:	PASS ***************
Response:	230 welcome !!!
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Features:
Response:	 MDTM
Response:	 REST STREAM
Response:	 SIZE
Response:	211 End
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is current directory.
Command:	TYPE A
Response:	200 Type set to A
Command:	PASV
Response:	227 Entering Passive Mode (123,456,789,101,231,26).
Command:	LIST
Error:	Transfer channel can't be opened. Reason: A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.
Error:	Could not retrieve directory listing
Command:	PWD
Error:	Timeout detected!
Status:	Waiting to retry... (5 retries left)
```

Setting the FTP client to active means that I cannot connect at all. Is this a firewall issue, a mode issue or a local host issue?

I should also point out that I only have ports 21 and 12345 available to use, as I am logging onto the machine via ssh, and cannot access the hardware firewall remotely.

---

### Post by Gsundbrunn on 2007-02-22
Hi,

I still have the problem, that files I upload with an ftp-client are not readable and I get an "You don't have permission to access /test.html on this server." by accessing them by web.

I followed this instruction here (just disabled AliasLogin and used another username). Everything works really fine but I have to set the rights manually to the uploaded files.

Would be a great thing to get a hint or to find a solution!

Best regards

Stefan

---

### Post by frodon on 2007-02-23
Don't really understand your problem, are you able to upload the files ? If yes then if you don't like the default rights of the files try to tweak the Umask line in your proftpd.conf and in your system it is the command which handle the efault rights of a created file.

---

### Post by Gsundbrunn on 2007-02-23
Hi,

yes, the upload is possible. But the file did not get the "read by others" property :-) And - yes - I used the chmod 022 in the config file. But an hour ago I found the solution - I use GFTP as a client and there is the option:

  "keep the filerights" (not sure how it is called in the actual english version - in german it is "Dateirechte beibehalten"). By disabling this function everything works perfectly.

So the information given by my FTP-Client overrides the FTP-Server settings. Interesting to know... 

Thanks!

Stefan

---

### Post by frodon on 2007-02-23
Glad that you found the solution and thanks for sharing it ;)

---

### Post by Gsundbrunn on 2007-02-25
Just a little particle in a very, very big mosaic :-)

---

### Post by joTi on 2007-02-25
> **ikkinu said:**
> **[SIZE=2]1- Enable TLS/SSL encryption (FTPS)[/SIZE]** 
The FTP file sharing protocol is an old protocol which was created when internet was still a secure place, therefore the default FTP protocol is not that secure.
For example the password and username for login are transmitted in plain text which obviously isn't secure.
That why, to fit the needs of our generation, encryption solutions were developed and one of them is TLS/SSH encryption.
This will encrypt the username and password and all the data you send, obviously to use it the FTP client must support SFTP protocol.

here are the steps to enable TLS/SSH encryption ([FTPS]("http://en.wikipedia.org/wiki/FTPS")):

Paste these commands in a terminal :```
sudo apt-get install build-essential
sudo apt-get install libssl-dev
cd /etc
sudo mkdir ftpcert
cd ftpcert/
sudo openssl genrsa -des3 -out server.key 1024
sudo openssl req -new -key server.key -out server.csr
sudo openssl genrsa -des3 -out ca.key 1024
sudo openssl req -new -x509 -days 365 -key ca.key -out ca.crt 
sudo wget ***
sudo chmod +x sign.sh
sudo ./sign.sh server.csr 
```

HI all,
when I type sudo ./sign.sh server.csr I get this error:

CA signing: server.csr -> server.crt:
Using configuration from ca.config
Enter pass phrase for ./ca.key:
Check that the request matches the signature
Signature ok
The Subject's Distinguished Name is as follows
countryName           :PRINTABLE:'IL'
stateOrProvinceName   :PRINTABLE:'Ikkland'
localityName          :PRINTABLE:'Ikktown'
organizationName      :PRINTABLE:'Project ikkinu'
organizationalUnitName:PRINTABLE:'Ftp Dpt.'
commonName            :PRINTABLE:'ikkinu'
emailAddress          :IA5STRING:'ikkinu@inventati.org'
Certificate is to be certified until Dec  5 19:24:50 2007 GMT (365 days)
Sign the certificate? [y/n]:y


1 out of 1 certificate requests certified, commit? [y/n]y
Write out database with 1 new entries
Data Base Updated
CA verifying: server.crt <-> CA cert
server.crt: /C=IL/ST=Ikkland/L=Ikktown/O=Project ikkinu/OU=Ftp Dpt./CN=ikkinu/emailAddress=xxx@xxx.xxx
error 18 at 0 depth lookup:self signed certificate
/C=IL/ST=Ikkland/L=Ikktown/O=Project ikkinu/OU=Ftp Dpt./CN=ikkinu/emailAddress=xxx@xxx.xxx
error 7 at 0 depth lookup:certificate signature failure
12603:error:04067084:rsa routines:RSA_EAY_PUBLIC_DECRYPT:data too large for modulus:rsa_eay.c:645:
12603:error:0D0C5006:asn1 encoding routines:ASN1_item_verify:EVP lib:a_verify.c:168:

Can anyone help me?
Thanks


I have the exact same problem, did anyone come up with a reliable fix for this problem? 
It's aggrevating as hell.

And i don't feel like sitting and guessing up values and hoping for a miracle.

I've tried googling but it just made me more confused.

Would appriciate help in this matter.

Thanks.

---

### Post by frodon on 2007-02-26
Just make several attempts changing some parameters like you pasword and so on, it should work.

---

### Post by espo100583 on 2007-02-27
Hi Guys,

Had a few problems getting proftpd working but getting there.

I have a problem when starting the server though I get the following message

Starting ProFTPD ftp daemon: WBSRV01 - mod_delay/0.4: error opening DelayTable
'/var/run/proftpd/proftpd.delay': No such file or directory

If i create the dir manually then try it again it works fine but then if I restart the PC I have to do it again.

Please see below my Conf file

```
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias espo100583 userftp

ServerName			"WBSRV01"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port				22024
PassivePorts 			22025 22125
# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /var/www

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>


<Directory> /var/www>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

```

Any advice would be much appreciated.

Thanks

---

### Post by frodon on 2007-02-27
Could you paste there the content of your /etc/proftpd/modules.conf file, thanks

---

### Post by dzul1983 on 2007-02-27
hi all
I've followed all the instructions given here.. but I still can't FTP into my PC via outside line.. I've setup ddclient and registered my PC at dyndns.org and got myself an URL.. the problem is.. whenever I type the URL into firefox it would try to log into my router instead of my PC.. if I add the port number at the end, it would just not connect..

I guessed that entering the URL itself may not log into the PC itself, but using a port number should have.. hope you guys can help..

---

### Post by frodon on 2007-02-27
This will help you :
[http://www.ubuntuforums.org/showpost.php?p=680702&postcount=81](http://www.ubuntuforums.org/showpost.php?p=680702&postcount=81)
[http://www.proftpd.org/localsite/Userguide/linked/x862.html](http://www.proftpd.org/localsite/Userguide/linked/x862.html)

---

### Post by dzul1983 on 2007-02-27
I found that my router has this kind of layout for port forwarding..

1. you can only have 16 ports for entry (eg. 60000-60015)
2. each entry must be assigned to one port on the LAN side (eg. 60000-60015 on the WAN side will be assigned to say 60000 on the LAN side)

does this mean I have to forward every single port from 60000 to 65535?

EDIT: I was able to connect when I set the FTP port to 21 (I opened up port 21 on the router. I also edited the proftpd.conf and set the port to 21) but I get an Error 530

---

### Post by espo100583 on 2007-02-27
Thanks for the quick response,

as strange as this might sound I don't have a proftpd dir in /etc.

I used the apt-get install command to install it so not quite sure whats going on.

Any Ideas?

Thanks

---

### Post by dzul1983 on 2007-02-27
OK, I got around to actually getting connecting to the server locally.. (still having problems accessing it via dyndns URL.. getting to this after I can get it working locally)

new problem.. and I suspect it has something to do with the ports for Passive Mode.. I've only opened from 60000-60040 and I've assigned them all to ports 60000-60005 on the LAN side..

It says that "/" is the current directory and then it tries to load a listing of / from the server.. and it goes into PASV mode and gets caught in a loop or something.. I cancelled the connection coz it was taking too long..

I dont have any commands in proftpd.conf pointing to / as the root folder.. and I've checked the home dir for userftp and it was OK..

any ideas?

@espo100583
I'm not sure about this, but I think proftpd on earlier versions of ubuntu didn't have a proftpd folder.. if you're trying to find the proftpd.conf, try looking for it in the /etc folder.. just a thought..

---

### Post by dzul1983 on 2007-02-27
apparently by removing the MasqueradeAddress, I was able to get over the PASV mode looping.. I could get into the server locally, and am able to read/write files now..

on to getting it to work with dyndns.. still getting the "wrong password" error when I connect via dyndns URL..

---

### Post by frodon on 2007-02-27
> **espo100583 said:**
> Thanks for the quick response,

as strange as this might sound I don't have a proftpd dir in /etc.

I used the apt-get install command to install it so not quite sure whats going on.

Any Ideas?

ThanksWhat version of ubuntu are you using ?

---

### Post by dzul1983 on 2007-02-27
it seems masqueradeaddress is required if outside people are to access the server.. however.. using masqueradeaddress I cant seem to be able to access the server from the inside.. or at least not from the PC that the server is running on.. I've had a few friends try accessing it from the outside with success..

another thing I was wondering.. why is it when I enter the URL I setup on dyndns into say firefox, it tries to access my router? will setting up a web server and redirecting port 80 to the web server make it so that the URL will open up a webpage on the web server instead of the router? just for the record.. I got this router from NTT.. think it's called a Web Caster V110.. oh yes.. I live in Japan..

---

### Post by espo100583 on 2007-02-28
I'm using version 6.10

I'm also having another issue, I can log onto the server with no prolbems from within the network but when I try it externally I get 

"No connection could be made because the target machine actively refused it "

Thanks for all the help.

---

### Post by frodon on 2007-02-28
So try to re-install proftpd because you should have this directory if you use ubuntu edgy eft. For your second problem this is surely related to your firewall.

---

### Post by patty522 on 2007-02-28
i was wondering if some one might be able to help me.

i have proftpd get up and its running. but i need to add some users. 
the usernames:
patrick     ftphome: /home/patrick/
dstamp    ftphome: /home/dstamp/
var-user  ftphome: /var/www/
and they need full controll. how would i do this as im normlly do it in gproftpd but i have gone full command prompt so no gui.

many thanks
patrick king

---

### Post by frodon on 2007-02-28
Just take example of the proftpd.conf in the first post and make some tests, the upload directory is a good example for you because it gives full rights.

---

### Post by espo100583 on 2007-03-01
Hi,

I've tried to reinstall proftpd but it still has not created the dir/ file you mentioned.

I'm guessing this could be down to my cource file so here is a copy of it, I got this from a link on this thread to another post which recomended this source list. I have a backup of the source list I had on install but it couldn't find proftpd when I trie apt-get.

```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# If you get errors about missing keys follow these command's :
# gpg --keyserver subkeys.pgp.net --recv 33BAC1B3
# gpg --export --armor 33BAC1B3 | sudo apt-key add -
#
# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ breezy main

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## plf mirror. use if primary repo is offline
## FTP mirror from http://free.fr (french ISP)
## deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
## deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

##
## Use the following repos ONLY if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## official wine apt repository
##deb http://wine.budgetdedicated.com/apt breezy main
##deb-src http://wine.budgetdedicated.com/apt breezy main


## opera web browser
## deb http://deb.opera.com/opera/ etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb http://people.ubuntu.com/~doko/OOo2 ./

## skype
## deb http://download.skype.com/linux/repos/debian/ stable non-free
```

Thanks for the help.

---

### Post by frodon on 2007-03-01
From what i see you are using ubuntu breezy 5.10 and not ubuntu edgy 6.10 or you are using a wrong source.list file.
If you are really using ubuntu edgy you should have the 2.6.17.11 kernel, the command "uname -a" will give you your kernel version.

---

### Post by espo100583 on 2007-03-01
I have ran the command and got this

Linux WBSRV01 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

I have the original source list if I need to revert back to this, but I'm guessing I will need to add some sources to enable me to get proftpd using apt as when I first tried it with th original source the package could not be found.

Thanks
Phil

---

### Post by frodon on 2007-03-02
Yep your source.list is really wrong, replace all the words "breezy" by "edgy" and it should be good.

---

### Post by progrockusa on 2007-03-10
ok i'm pretty much a complete noob to linux
but i instaled GproftpD and when i try to run it it tells me i have to run it as a root (the window will close in 10 secs)  wth does that mean and how do i run it as root?

---

### Post by frodon on 2007-03-10
All about what is root rights and how to use them here  :
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Jackaniny on 2007-03-10
Hey,

I've been having a hell of a time trying to get my server working with multiple logins (and diferent permission for each login).

What I'm trying to setup is:

A home dir (/home/ftp) that I can control with the main ftp user account and a dir (/home/ftp/clientclips) that, when logged in as a second account, is read only.
I would like to have full control the main dir (and all sub-dir) using the main ftp account and still have the clientclips dir read only for the second ftp account.

So far the best I've been able to do is have the main dir be read/write for the main account (anarchyftp) and the clientsclips be read only, or have all dir and sub-dir be read/write for the anarchyftp account and get PWD or PORT errors (often both) when logging in as the second account (creativeftp)

I've attached my current conf.
with it I'm able to read/write while logged in as anarchyftp, but I get this error when logged in as creativeftp:
```
"Could not determine current path. Server said: PWD: Permission denied. Error -124: PWD failed"
```

Does anyone have any tips? I'm getting kind of desperate.

---

### Post by espo100583 on 2007-03-11
Hi Guys,

Just a quick question,

I am able to connect locally to the FTP server but not externally. I have set the passive prots in the proftpd.conf file and matche the ports the router allows through to the server but when I connect externally I get

Response:	500 Illegal PORT command
Error:	Could not retrieve directory listing

Any ideas would be greatly appreciated as I'm all out.

Thanks

---

### Post by Jackaniny on 2007-03-12
I figured out the PWD error!

the problem was I had set the permissions like this:

```
<Directory /home/ftp/*>
Umask 022 022
AllowOverwrite on

        <Limit ALL>
		Order Allow,Deny
		AllowUser anarchyftp
		AllowUser macwrech
		AllowUser caadmin
		Deny ALL
	</Limit>

	<Limit READ MKD STOR CWD DELE XMKD RNEF RNTO RMD XRMD>
	AllowAll
	</Limit>
</Directory>

<Directory> /home/ftp/clientclips/*>
Umask 022 022
AllowOverwrite on

       <Limit ALL>
		Order Allow,Deny
		AllowUser anarchyftp
		AllowUser macwrech
		AllowUser caadmin
		AllowUser creativeftp
		Deny ALL
	</Limit>

```

When I should have set them like this:

```
<Directory /home/ftp/*>
Umask 022 022
AllowOverwrite on

        <Limit ALL>
		Order Allow,Deny
		AllowUser anarchyftp
		AllowUser macwrech
		AllowUser caadmin
		AllowUser creativeftp
		Deny ALL
	</Limit>

	<Limit READ MKD STOR CWD DELE XMKD RNEF RNTO RMD XRMD>
	AllowAll
	</Limit>
</Directory>

<Directory> /home/ftp/clientclips/*>
Umask 022 022
AllowOverwrite on

       <Limit ALL>
		Order Allow,Deny
		AllowUser anarchyftp
		AllowUser macwrech
		AllowUser caadmin
		AllowUser creativeftp
		Deny ALL
	</Limit>

```


The problem was I didn't give the read-only user permission to use the root dir, so it couldn't get access to the sub-dir.

E.g.

This gave me the PWD and PORT errors:
```
<Directory /home/ftp/*>
Umask 022 022
AllowOverwrite on

        <Limit ALL>
		Order Allow,Deny
		AllowUser anarchyftp
		AllowUser macwrech
		AllowUser caadmin
		Deny ALL
	</Limit>

<Directory> /home/ftp/clientclips/*>
Umask 022 022
AllowOverwrite on

       <Limit ALL>
		Order Allow,Deny
		AllowUser anarchyftp
		AllowUser macwrech
		AllowUser caadmin
		AllowUser creativeftp
		Deny ALL
	</Limit>


```

This worked:
```
<Directory /home/ftp/*>
Umask 022 022
AllowOverwrite on

        <Limit ALL>
		Order Allow,Deny
		AllowUser anarchyftp
		AllowUser macwrech
		AllowUser caadmin
		**AllowUser creativeftp**
		Deny ALL
	</Limit>

<Directory> /home/ftp/clientclips/*>
Umask 022 022
AllowOverwrite on

       <Limit ALL>
		Order Allow,Deny
		AllowUser anarchyftp
		AllowUser macwrech
		AllowUser caadmin
		AllowUser creativeftp
		Deny ALL
	</Limit>


```

Hope that helps someone.

---

### Post by Glitch0r on 2007-03-18
Hello people, I installed proftpd on Ubuntu 6.10 with this tutorial and that all worked fine.

I now however want to install a third party module (mod_ban) but I really dont know how to do this. The instructions tell me to add a file (mod_ban.c) to the proftp-dir/contrib directory but I can not find this.

It also tells me to recompile using the commands below but executing these commands in terminal just give me a unknown command errors.

There must be someone out here that has done this before and who can help me out.

---

### Post by frodon on 2007-03-18
You should see in the proftpd forum for this, did you check that the module isn't installed by default ?

---

### Post by Glitch0r on 2007-03-18
> **frodon said:**
> You should see in the proftpd forum for this, did you check that the module isn't installed by default ?
The proftpd forum has very bad support so I thought I'd try it here especially since the problem seem to lay in the fact that I installed a packaged version as explained in this tutorial while the installation instructions from the module I want assume you have compiled it yourself as it seems.

Now I need to find a way to recompile the packaged version with the extra modules.

The module is not installed by default:```

jelger@jelger-desktop:/etc/proftpd$ proftpd --list
Compiled-in modules:
  mod_core.c
  mod_xfer.c
  mod_auth_unix.c
  mod_auth_file.c
  mod_auth.c
  mod_ls.c
  mod_log.c
  mod_site.c
  mod_delay.c
  mod_dso.c
  mod_auth_pam.c
  mod_readme.c
  mod_cap.c
  mod_ctrls.c

```

---

### Post by technics on 2007-03-18
great howto thx!

---

### Post by kptracey on 2007-03-20
Hi,

I plan to search the 41 pages for an answer to this post but in case someone is feeling charitable... 

My setup isn't working correctly and I get the following error:

kieran@samurai:/home/FTP-shared$  sudo /etc/init.d/proftpd restart
 * Stopping ftp server proftpd                                           [ ok ] 
 * Starting ftp server proftpd                                                  
 - IPv4 getaddrinfo 'samurai' error: Name or service not known
 - warning: unable to determine IP address of 'samurai'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'


I'm very new to Ubuntu. I setup a Samba server last night with a static ip and I'm running Firestarter. I also have a wireless router.

Thanks in advance.
______________________________________

I GOT IT WORKING!!!! (even though no one has previously replied to this problem- so I will now =)

If you run into the same problem... do me a favour and in terminal type: 'hostname -f'
I bet it responds 'hostname: Unknown host'

If it does, do this:
sudo gedit /etc/hosts/

Add this line: '127.0.0.1 <hostname> <FQDN>'

FQDN stands for Fully Qualified Domain Name
hostname is the name of your machine

Mine reads something like this:
127.0.0.1 samurai samurai.phubs.net.cab.irelandrules.com

In this instance, hostname is samurai and samurai.phubs.net.cab.irelandrules.com is the FQDN.

In hindsight, this is a result of me being lazy during my Samba install and simply appending a preexisting entry with mshome and slightly altering the 127 mask.

And yes, to my fellow lazy people, you're all very very welcome =)

Happy FTPing!!!

---

### Post by sputnik2012 on 2007-03-21
Hi.

I've googled this but can find no answers.
I can access my server when I type ftp localhost. 
> 
rob@ubuntu-rydal:~$ ftp localhost
Connected to ubuntu-rydal.
220 My FTPD
Name (localhost:rob): *****
331 Password required for *****.
Password:
230 User rob logged in.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> 

Logins work fine.

However, when I try ftp (my.domain.name) I get:
> 
530 Login Incorrect
Login Failed.
Remote type system is ignored.


I've checked /etc/hosts.deny (empty)
/etc/hosts.allow ALL

Any help greatly appreciated.

Rob.

> 
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

ServerName                      "Sputnik_rydal"
ServerType                      standalone
DeferWelcome                    off

MultilineRFC2228                off
DefaultServer                   on
ShowSymlinks                    on

TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                     "-l"

#DenyFilter                     \*.*/
AllowOverwrite on

DefaultRoot ~
# Port 21 is the standard FTP port.
Port                            21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                    49152 65534

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

# Set the user and group that the server normally runs at.
User                            proftpd
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd              off
# Be warned: use of this directive impacts CPU average load!
#
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
# UseSendFile                   off

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_tls.c>
TLSEngine off
</IfModule>

<IfModule mod_quota.c>
QuotaEngine on
</IfModule>

<IfModule mod_ratio.c>
Ratios on
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        on
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine on
</IfModule>

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User                                ftp
#   Group                               nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias                   anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell           off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients                  10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin                        welcome.msg
#   DisplayFirstChdir           .message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask                           022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

<Directory /home/ftp/music>
Umask 022 022
AllowOverwrite off
        <Limit LOGIN MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
        AllowAll
        </Limit>
</Directory>

<Directory> /home/ftp/upload/>
Umask 022 022
AllowOverwrite on
        <Limit LOGIN READ RMD DELE>
        AllowAll
        AllowUser All
        </Limit>

        <Limit LOGIN STOR CWD MKD>
        AllowAll
        AllowUser All
        </Limit>
</Directory>


---

### Post by frodon on 2007-03-21
Are you behind a router or a firewall ? if yes it is things to check as well.

---

### Post by kptracey on 2007-03-22
Sputnik,

 I get the impression that Frodon isn't behind a router. Which is fine, except for the fact that his awesome instructions don't drill down into routers.

I suggest you port forward 21 on your router.

There are some other things you should do too if you haven't already done so.

1. Login into your router.
2. Under Internet Connection Type (or similar- I'm using linksys router), select Static IP. If you need your Internet IP address, subnet mask and gateway click on Status (or similar).


To port forward 21, click into your Port Range Forward table (this is located under Application & Gaming on Linksys)
Application: FTP
Start: 21 to 
End: 21
Protocol: TCP
IP Address (linksys and based on DHCP Server starting IP address): 192.168.1.100
Enable: Y

Hope this helps. Keep posting your questions if it doesn't =)

---

### Post by sputnik2012 on 2007-03-22
Thank you both.  Tried it over a PPP connection and things worked fine.  As a note ftp uses port 20 as well as port 21,  21 is for commands and 20 for data, unless passive ftp is used.

Thanks again,
        Rob.

---

### Post by Harry_Callahan on 2007-04-01
many compliments for this guide frodon. I got it work in a few minutes, I tried in local network(ftp 127.0.0.1), no problem. But know I'm always getting this error from Linux or Windows SO:

xxx@Linux-desktop:~$ ftp 192.168.0.253
Connected to 192.168.0.253.
500 FTP server shut down (Sun Apr  1 21:17:59 2007 , Current connections will be dropped: Sun Apr  1 21:07:59 2007) -- please try again later

I tried restarting proftpd and Ubuntu, but nothing. Why is this happening?

---

### Post by frodon on 2007-04-01
I thnk you need to pass the username at least in your command to go to the next login step, for example "ftp username@192.168.0.253" then you will be asked to enter the password (it's how it works with a web browser).

---

### Post by Harry_Callahan on 2007-04-01
> **frodon said:**
> I thnk you need to pass the username at least in your command to go to the next login step, for example "ftp username@192.168.0.253" then you will be asked to enter the password (it's how it works with a web browser).

that's strange. I got it to work in a couple of minutes simply typing ftp 127.0.0.1(from Ubuntu). I logged off from ftp, then I tried from Windows and started getting the 500 error. The strange thing seems to be the hour-minute in the error:

500 FTP server shut down (Sun Apr 1 21:17:59 2007

that's about the time I logged off from fto in Ubuntu

Thanks

edit: tried ftp username@192.168.0.253 and got Unknown host errror.

Like I said before, the 500 error came out when I started the Windows macchine, Could it be a conflict with Samba?

---

### Post by ojve on 2007-04-03
Hi!

I'm a complete Linux/Ubuntu newbie:) 

I've followed the tutorial, but when i try to start the server I Just get:
root@Server:~# sudo /etc/init.d/proftpd start
 * Starting ftp server proftpd                                           [fail] 

How do I go about to get a little more information on exactly what it is that has failed?

//T

---

### Post by frodon on 2007-04-03
[http://www.proftpd.org/localsite/Userguide/linked/x1058.html](http://www.proftpd.org/localsite/Userguide/linked/x1058.html)

Don't forget to perform a syntax check first just to see that there isn't any typo somewhere :
```
proftpd -td5
```More here : [http://www.proftpd.org/localsite/Userguide/linked/x1044.html](http://www.proftpd.org/localsite/Userguide/linked/x1044.html)

---

### Post by ojve on 2007-04-03
did that. It says it's ok...

---

### Post by frodon on 2007-04-03
And with the -nd5 option you don't get more details on what failed ?

---

### Post by ojve on 2007-04-03
oops, guess i missed a couple lines at the top. This is what it says:

root@Server:~# proftpd -td5
Checking syntax of configuration file
 - mod_ctrls/0.9.4: binding ctrls socket to '/var/run/proftpd/proftpd.sock'
 - parsing '/etc/proftpd/proftpd.conf' configuration
 - <Directory /home/tjar/media>: deferring resolution of path
 - IPv6 getaddrinfo 'Server' error: Name or service not known
Server - 
Server - Config for ServerTorkel:
Server - /home/tjar/media
Server -  Limit
Server -   AllowAll
Server -  Limit
Server -   AllowAll
Server -  Umask
Server -  DirUmask
Server -  AllowOverwrite
Server -  AuthAliasOnly
Server -  ShowSymlinks
Server -  DisplayFirstChdir
Server -  ListOptions
Server -  RequireValidShell
Server -  RootLogin
Server -  TransferLog
Server -  UseFtpUsers
Server -  AllowStoreRestart
Server -  MaxClients
Server -  MaxClientsPerHost
Server -  MaxClientsPerUser
Server -  MaxHostsPerUser
Server -  AccessGrantMsg
Server - Limit
Server -  AllowUser
Server -  DenyAll
Server - AllowOverwrite
Server - AuthAliasOnly
Server - DeferWelcome
Server - DefaultServer
Server - ShowSymlinks
Server - TimeoutNoTransfer
Server - TimeoutStalled
Server - TimeoutIdle
Server - DisplayFirstChdir
Server - ListOptions
Server - RequireValidShell
Server - TimeoutLogin
Server - RootLogin
Server - ExtendedLog
Server - TransferLog
Server - UseFtpUsers
Server - AllowStoreRestart
Server - UserID
Server - UserName
Server - GroupID
Server - GroupName
Server - Umask
Server - DirUmask
Server - MaxClients
Server - MaxClientsPerHost
Server - MaxClientsPerUser
Server - MaxHostsPerUser
Server - AccessGrantMsg
Server - ServerIdent
Server - DefaultRoot
Server - DefaultRoot
Server - MaxLoginAttempts
Server - mod_ctrls/0.9.4: binding ctrls socket to '/var/run/proftpd/proftpd.sock'
Syntax check complete.

---

### Post by frodon on 2007-04-03
It looks good, the IPv6 error shouldn't prevent the FTP server from running properly, your problem should be elsewhere.

---

### Post by Ek0nomik on 2007-04-03
**ojve**:  I had to add sudo in front of the command to start the server.  Otherwise I was getting permission denied on some things.  Also, make sure the user you created in still in your Users & Groups under System / Administration.

**frodon**:  Thanks for the guide!  I have my FTP working.  I wanted to set it up with SSL/TLS (I don't know the difference or if they are the same thing).  I followed your steps, and I get prompted to enter the key on starting the server.  The server starts fine, but how do I know if the SSL/TLS is working?  Is there a way to check?  I can still connect just the same with Firefox and KFTP Grabber on my other box.  I feel like I should have had to accept a certificate or configure something in order for it to connect.

Any help would be appreciated!  Thanks again!

Cheers!

---

### Post by frodon on 2007-04-04
In the log you will see the TLS step and if you try yourself to log in your server you will see that you need to accept the certificate you created before giving the username and password.
It also depend of the parameter "TLSRequired off" if you left it at the off state then normal connections (not encrypted) will be allowed but if you want for security reasons to accept only encrypted connections then put this parameter at the "on" state and your server will accept only TLS encrtpted traffic.
Be careful not all the FTP client support TLS encryption, GFTP do not for example.

---

### Post by Ek0nomik on 2007-04-04
I deleted my log file and started it from scratch.  This log file has loggings of me running the start command to start the server, and attempting to login once.  (Which was successful, but I was never prompted to accept a certificate):

```
Apr 04 11:30:40 love proftpd[5828] love: error setting IPV6_V6ONLY: Protocol not available
Apr 04 11:30:40 love proftpd[5828] love: ProFTPD 1.3.0 (stable) (built Wed Nov 29 02:01:20 UTC 2006) standalone mode STARTUP
Apr 04 11:30:45 love proftpd[5850] love (xx.xx.xx[::ffff:xx.xx.xx]): error setting IPV6_V6ONLY: Protocol not available
Apr 04 11:30:45 love proftpd[5850] love (xx.xx.xx[::ffff:xx.xx.xx]): FTP session opened.
Apr 04 11:30:45 love proftpd[5850] love (xx.xx.xx[::ffff:xx.xx.xx]): no such user 'anonymous'
Apr 04 11:30:45 love proftpd[5850] love (xx.xx.xx[::ffff:xx.xx.xx]): USER anonymous: no such user found from xx.xx.xx [::ffff:xx.xx.xx] to ::ffff:xx.xx.xx:21
Apr 04 11:30:57 love proftpd[5850] love (xx.xx.xx[::ffff:xx.xx.xx]): USER districtthree: Login successful.
Apr 04 11:30:57 love proftpd[5850] love (xx.xx.xx[::ffff:xx.xx.xx]): error setting IPV6_V6ONLY: Protocol not available
Apr 04 11:30:57 love proftpd[5850] love (xx.xx.xx[::ffff:xx.xx.xx]): error setting IPV6_V6ONLY: Protocol not available
Apr 04 11:35:57 love proftpd[5850] love (xx.xx.xx[::ffff:xx.xx.xx]): FTP session closed.

```

/etc/proftpd/proftpd.conf is as follows...

```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

ServerName			"Fleur"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

DenyFilter			\*.*/

# Port 21 is the standard FTP port.
Port				21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                    49152 49153

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			10

# Set the user and group that the server normally runs at.
User				proftpd
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd		off

# Be warned: use of this directive impacts CPU average load!
#
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
# UseSendFile			off

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_tls.c>
TLSEngine off
</IfModule>

<IfModule mod_quota.c>
QuotaEngine on
</IfModule>

<IfModule mod_ratio.c>
Ratios on
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        on
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine on
</IfModule>

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayFirstChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

<IfModule mod_tls.c>
    TLSEngine on
    TLSLog /var/ftpd/tls.log
    TLSProtocol TLSv1

    # Are clients required to use FTP over TLS when talking to this server?
    TLSRequired on

    # Server's certificate
    TLSRSACertificateFile /etc/ftpcert/server.crt
    TLSRSACertificateKeyFile /etc/ftpcert/server.key

    # CA the server trusts
    TLSCACertificateFile /etc/ftpcert/ca.crt

    # Authenticate clients that want to use FTP over TLS?
    TLSVerifyClient off
</IfModule>
```

I turned it to ON, but I still didn't get prompted.  Thanks for the help frodon.  :)

Edit:  My computer name is love, I am user fleur.  fleur@love:~$

---

### Post by frodon on 2007-04-05
You have :
```
<IfModule mod_tls.c>
TLSEngine off
</IfModule>
```This is for sure the or a least one of the reasons why your TLS encryption isn't active.

---

### Post by dannyboy79 on 2007-04-06
hi frondon, i am back. i had stopped using my ftp server but now I want it again. i removed the backport and installed dapper version 1.2.10-27ubuntu3.1. i followed this guide to make sure it would work with my router. (this time I am going with "standalone" as I could never get xinetd to work with ssl/tls or without?
 ([http://ubuntuforums.org/showpost.php?p=680702&postcount=81](http://ubuntuforums.org/showpost.php?p=680702&postcount=81)) no matter what I try I  can't get tls/ssl to work i am in dapper. i have forwarded both ports 20 and 21 and 60000 and 65534 (65534 is the last port available in my netgear router). i have made sure that iptables isn't blocking any of them. this is what the fireftp log shows so this is really weird:

220 you're at home
       AUTH TLS
234 AUTH TLS successful
       PBSZ 0

but it does say that over and over and over but the error window pops up right away. oh, i am working/troublshooting my dapper server thru putty in windows and using firefox/fireftp on that same machine to test my ftp server.another thing that's weird is that I can connect locally by using the ftp command. this is the tls.log file on the server it self.

Apr 05 23:03:23 mod_tls/2.0.7[20517]: unable to accept TLS connection:
  (1) error:140890C7:SSL routines:SSL3_GET_CLIENT_CERTIFICATE:peer did not return a certificate
Apr 05 23:03:23 mod_tls/2.0.7[20517]: TLS/TLS-C negotiation failed on control channel

it appears that something is blocking the certificate from being passed thru the control channel? or the peer isn't sending the cert back? i do click ok in the  firefox cert request i am using fireftp version 0.95.2 in firefox version 2.0.0.3. can you sugegst anything? I would be very greateful if you could. a little dialog does appear asking if I want to accept the cert and i click on yes, then I get this weird error in firefox. i tried taking a snapshot of it and putting it in imageshack but out of know where just now my netowrk connection is lagging horribly.

i have even tried disabling tls/ssl and this is what i get in the log file:

331 Password required for xxxxxxxxx.
       PASS (password not shown)
230 YOU MADE IT!
       TYPE A
200 Type set to A
       CWD /
250 CWD command successful
       PASV
227 Entring Passive Mode (xxxxxxxxxxx,243,171
Error: [Exception... "Component returned failure code: 0x80070057 (NS_ERROR_ILLEGAL_VALUE) [nsISocketTransportService.createTransport]" nsresult: "0x80070057 (NS_ERROR_ILLEGAL_VALUE)" location: "JS frame :: chrome://fireftp/content/js/connection/dataSocket.js :: anonymous :: line 41" data: no]
Unable to make a data connection. Please try again.
       LIST -al

then a message pops up and says, unable to make data connection. it just doesn't make sense due to the fact that I have triple checked all the port forwarding etc etc. any suggestions.

---

### Post by frodon on 2007-04-06
You should read carefully [this post]("http://ubuntuforums.org/showpost.php?p=680702&postcount=81") and check that you have well added your *MasqueradeAddress* and *PassivePorts* commands which are needed when you use a router.

You can always try those parameters if it still don't work :
```
UseReverseDNS off
IdentLookups off
```

---

### Post by Harry_Callahan on 2007-04-06
Hello again,

I fixed the "500 FTP server shut down" error by reinstalling as standalone server.
Now I have a little problem with my permissions. If I try copying a file(with command sudo cp file_name /home/FTP-shared/download) to the download folder(that way someone can download it)

I don't get the same permissions as the folder:

drwxr-xr-x 2 root root 4096 2007-04-03 20:40 download

 I only get:

-rwx------

If I connect from remote I can't download the file. I must add permission "read" to group and user(-rwxr--r-- )

Is it possibile to copy and assign the same permissions as the folder?

Thanks

---

### Post by frodon on 2007-04-06
This is a right management question, when you copy a file it keeps its own permission. So except giving the file you want to copy in the download folder the read permission before copying it i have no clue.
BTW you can mount a whole directory in /home/FTP-shared/download if you wish using the "mount -o bind" command rather than copying files in the download directory.

---

### Post by sinaen on 2007-04-09
I want the GFTPD program to remote administrate an proftpd server :( and that's not possible with these features it uses right now :/

---

### Post by SLMHC on 2007-04-12
Hello.  New to Ubuntu and linux actually.  I need to setup a secure ftp server for my hospital to transfer sensitive information to external partners.  This setup looks like it is just the thing I need.

I was able to follow the 1st part of the how-to and had a working ftp server.  I then moved onto the encryption part.  i had no errors following that how to either, but I am not able to connect to the server any longer.

I am using Filezilla as my client (2.2.26a), here is my config:
Servertype: FTP over TLS (explicit encryption)
Logontype: Normal

Filezilla log: 
Status:	Connecting to 10.1.1.16 ...
Status:	Connected with 10.1.1.16, negotiating SSL connection...
Response:	220 ProFTPD 1.3.0 Server ready.
Command:	AUTH TLS
Response:	234 AUTH TLS successful
Error:	Can't establish SSL connection
Error:	Disconnected from server
Error:	Unable to connect!

Any ideas?

-Dave

---

### Post by frodon on 2007-04-12
Hi SLMHC,

I think your problem is related to the connection parameters you entered in Filezilla, there's 2 encryption methods for the FTP protocol one based on SLL (often called SFTP) which use a ssh tunnel as far as i know and the other described in the guide called TLS encryption (also called FTPS). Seing the word SSL in the filezilla log you posted makes me think that you chose SSL instead of TLS in your filezilla settings.
Reading the home page of filezilla i'm not sure it supports FTP with TLS encryption also called FTPS (whish is different than SFTP which use the SSL method), so i thinks it's just that filezilla don't support this encryption method.

If you use firefox you can just install fireftp which is a FTP extension of firefox and supports FTP with TLS encryption, click the link below to install it :
[https://addons.mozilla.org/en-US/firefox/addon/684](https://addons.mozilla.org/en-US/firefox/addon/684)

---

### Post by SLMHC on 2007-04-12
I tried using fireftp and I was able to connect, well, sortof...I was able to see the remote folder but the program kept trying to complete the connection and would finally time out.

---

### Post by frodon on 2007-04-12
Maybe some firewall issues, did you check that all the needed ports are opened on both server and client side ?

---

### Post by SLMHC on 2007-04-12
This test was via the internal network, once I get it working locally Ill move to opening up my firewall.

To my knowledge SFPT uses SSH and isnt FTP & FTPS is FTP over SSL/TLS.

---

### Post by esaym on 2007-04-12
Hmm  I installed using gproftpd and proftpd.  I just need something real simple for accessing my computer from school.  the gui seemed to work great but I don't really know if it works at all.  The ftp server seems to use /etc/proftpd/proftpd.conf and the gui makes a new file to use: /etc/proftpd.conf.  So I am not really sure if the server sees that or not.  The main thing is that I will have the server atleast working but when I reboot it clears the password settings on the accounts.  So then on a reboot I will have to re-run to the gui and set the passwords again before I can log in.  Not sure if I am doing something wrong or what...:(


edit:

Ok I found an alternative to ftp (not to knock the mod authors or anything).  If you just need very basic upload capability, then look into the "simple upload script":  [http://paksofts.uni.cc/scripts.htm](http://paksofts.uni.cc/scripts.htm) :)

---

### Post by hbomb on 2007-04-12
When I try to use proftptools, i get this error:


hbomb@ubuntu:~$ ProftpTools
The application 'gksudo' lost its connection to the display localhost:10.0;
most likely the X server was shut down or you killed/destroyed
the application.
hbomb@ubuntu:~$

Any idea as to why? I followed the how to as instructed. I am using dapper.

Any help would be most appreciative. :)

---

### Post by frodon on 2007-04-13
It seems to be a problem with gksudo, do you have problems with gksudo when you use it for an other apps ?

BTW, this script can be improve but it seems that you are not many to use it, that's why the few bug it has hasn't been fixed, if you find the script useful feel free to say it so i wll maybe put some energy in when  have time.

---

### Post by dannyboy79 on 2007-04-13
> **esaym said:**
> Hmm  I installed using gproftpd and proftpd.  I just need something real simple for accessing my computer from school.  the gui seemed to work great but I don't really know if it works at all.  The ftp server seems to use /etc/proftpd/proftpd.conf and the gui makes a new file to use: /etc/proftpd.conf.  So I am not really sure if the server sees that or not.  The main thing is that I will have the server atleast working but when I reboot it clears the password settings on the accounts.  So then on a reboot I will have to re-run to the gui and set the passwords again before I can log in.  Not sure if I am doing something wrong or what...:(


edit:

Ok I found an alternative to ftp (not to knock the mod authors or anything).  If you just need very basic upload capability, then look into the "simple upload script":  [http://paksofts.uni.cc/scripts.htm](http://paksofts.uni.cc/scripts.htm) :)

At least you found an alternative but to answer your questions so you don't think Proftpd isn't a good FTP server.

1.) This is most likely because gproftpd has been updated to reflect Proftpd config file location for Edgy (/etc/proftpd.conf). The good thing about open source stuff is that all you would have to do is open up the gproftpd script/program file and look for the line of code that calls for where the config file gets saved and change it to where the Proftpd version in Dapper asks for it.
OR
You could always change the Proftpd program and look for the code that calls out for the location of the config file it should use and  change it there. 
OR
If you're learly about editing code (you shouldn't be, it's just a line that says, "Hey, go get this file and use it for your configuration") You would have to do is simply take the latest file that you know has the changes you made from within the gui and put it in the location that Dapper's Proftpd server access's, which is /etc/proftpd/proftpd.conf.
OR
You could make a symlink that would basically make /etc/proftpd/proftpd.conf be linked to /etc/proftpd.conf

2.) I am not sure what you mean about passwords getting changed? I haven't used gproftpd but the way that Proftpd works I thought (at least a secure way) is by creating a user without shell access and chrooting him into his home directory. So it's PAM that saves the password for this user. Maybe you could explain better but I am sure there is an explaination.

---

### Post by esaym on 2007-04-13
> **dannyboy79 said:**
> 

2.) I am not sure what you mean about passwords getting changed? I haven't used gproftpd but the way that Proftpd works I thought (at least a secure way) is by creating a user without shell access and chrooting him into his home directory. So it's PAM that saves the password for this user. Maybe you could explain better but I am sure there is an explaination.

Thanks for the info.

What I mean is that everything works fine until I restart the box and then once proftpd is back up and running no one can log in.  The only fix I found is to open gproftpd up and go to the user and re enter the password.

---

### Post by hbomb on 2007-04-14
Frodon, 

It works now, I rebooted my box and that fixed it, odd huh? Anyways, I like the tools, they make tasks easier and I will most definitely be using it. And thanks for the excellent howto, it really made it a breeze getting proftp set up securely. :D 

h-bomb

---

### Post by frodon on 2007-04-14
If you have a problem with the script feel free to PM me, there"s a known bug with the mount function in my scrpt for directories which contain space in their name but i know how to fiw it so if you ask i will commit a version with this bug fixed.

---

### Post by Olsson on 2007-04-16
Hello. I have done almost everything from tutorial but i get this when i try to start the ftp: 

* Starting ftp server proftpd  
- IPv6 getaddrinfo 'localhost' error: Name or service not known

I have also tried with other peoples configs but that didn't work either. I have opened the port 1980 and I also tried with 60000 65535 ports and they didn't even work to forward on my Dell router.. whys that? Yeah, I ve put a static ip too..

Please somebody write a bit what i should do..! As I said I ve almost done everything (added userftp as a user, made the dirs etc).. Thanks.

---

### Post by frodon on 2007-04-16
The IPv6 error don't prevent the server from running as expected, it just tells that you don't use IPv6 which is normal, you can just forget this error.

---

### Post by Olsson on 2007-04-16
Thank you frodon! That helps alot. :D 

Okey i have opned the port 1980 in the router as i said and It doesn't work in the FTP with that port. But when i try with 21 in the ftp (and 1980 in the config file) I get the welcome massage and info about what ftp I'm using etc and then i get the 530 error. What should I do now?

This is what almost works (exept for the 530 problem)
adress: the servers ip
user: the one that I wrote in the conf
pass: the one that I gave ftpuser
port: 21 (as I said 1980 dosen't work)

Very thankfull for answers.

EDIT: Just tried with user: ftpuser and it worket! (on port 21 also) .. Any word on that?

EDIT2: Also.. I'm, trying to get it to work outside my home (and router) and it doesnt work. OFcours I'm using the WAN ip then.. Any tips on that?

---

### Post by frodon on 2007-04-16
This is a common issue and often due to a configuration problem, in this case you should check that you gave the good rights to the directories you are using then try to change the password of the user you use for the FTP, sometimes there's some problems with the password recognition on the first use.

---

### Post by Olsson on 2007-04-16
The weird thing is that i got it working with the ftpuser, the user i made because the tutorial said me too, I didn't know that I were suppose to use the ftpuser-user to access my ftp, is that so? 

And how can i change the port to a more secure one that 21? Didn't work to use 1980 in the config file and open the port on the router.. And what should I do to be able to use the ftp outside the router?

---

### Post by frodon on 2007-04-16
If it don't work with 1980 it's mainly due to your router/firewall but don't bother with if someone want to hack your FTP server he will scan all your ports so that's not a big issue to have your server on port 21.
For the user you are supposed to use the alias you set in the config file but it's not dramatic if you use directly ftpuser.

For the router config see this post :
[http://ubuntuforums.org/showpost.php?p=680702&postcount=81](http://ubuntuforums.org/showpost.php?p=680702&postcount=81)

---

### Post by Olsson on 2007-04-16
Thanks! Last questions now.. Sorry if I'm a pain in the ***..

Got it working with my wan-ip now, but I can't reach it with a browser, only in a ftp. Why's that? A domain shouldn't be necessery if I'm correct. What can i do about that?

Also, is this something to worry about?

ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default

---

### Post by Olsson on 2007-04-16
Thanks! Last questions now.. Sorry if I'm a pain in the ***..

Got it working with my wan-ip now, but I can't reach it with a browser, only in a ftp. So I need apache right? Which i already got installed. But now to the tricky question: How do I add apache to my ftp-server? I'm very thankfull and no more question after this ^^

Also, is this something to worry about?

ALSA lib confmisc.c:672 :(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c :3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c :3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c: 1072:(snd_func_refer) error evaluating name
ALSA lib conf.c :3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c :3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c :2102:(snd_pcm_open_noupdate) Unknown PCM default

---

### Post by dannytherocker on 2007-04-16
Hi,
tried to configure proftpd to let myself only, view all files, hidden ones included.
Did this way:

```
<IfUser userfp2>
ListOptions "-l -a"
<\IfUser>
```

but I get:
Fatal: unknown configuration directive '<IfUser>' in line ....

The weird thing is that i get this kind of error, even with lines suggested on Castaglia's website...
Any suggestion??
thanks in advance

---

### Post by frodon on 2007-04-17
> **Olsson said:**
> Thanks! Last questions now.. Sorry if I'm a pain in the ***..

Got it working with my wan-ip now, but I can't reach it with a browser, only in a ftp. Why's that? A domain shouldn't be necessery if I'm correct. What can i do about that?No problem 

To join your FTP server in a browser you need to pass the username ine the adress, for example if your IP is 123.456.789.123 and your ftp username "toto" you will need to enter this in your browser :
```
ftp://toto@123.456.789.123
```
> **Olsson said:**
> Also, is this something to worry about?

ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM defaultALSA is a sound driver so this has nothing to do with you FTP server

---

### Post by frodon on 2007-04-17
> **dannytherocker said:**
> Hi,
tried to configure proftpd to let myself only, view all files, hidden ones included.
Did this way:

```
<IfUser userfp2>
ListOptions "-l -a"
<\IfUser>
```

but I get:
Fatal: unknown configuration directive '<IfUser>' in line ....

The weird thing is that i get this kind of error, even with lines suggested on Castaglia's website...
Any suggestion??
thanks in advanceI think it's surely because you don't load the module which contain these directives. Which version of proftpd are you using ?

---

### Post by dannytherocker on 2007-04-17
> **frodon said:**
> I think it's surely because you don't load the module which contain these directives. Which version of proftpd are you using ?

Actually, I thought of it but was not sure. Anyway, my version on Edgy is 1.3.0
How can I load the module ?
thanks, frodon!

---

### Post by frodon on 2007-04-17
The list of available modules should be in /etc/proftpd/modules.conf, just uncomment those you want to load and make sure that you have this line at the beginning of your proftpd.conf file :
```
Include /etc/proftpd/modules.conf
```

For your ListOptions command you need "mod_ls"and for IfUser commands i believe it's mod_ifsession.

---

### Post by dannytherocker on 2007-04-17
> **frodon said:**
> The list of available modules should be in /etc/proftpd/modules.conf, just uncomment those you want to load and make sure that you have this line at the beginning of your proftpd.conf file :
```
Include /etc/proftpd/modules.conf
```

For your ListOptions command you need "mod_ls"and for IfUser commands i believe it's mod_ifsession.

Thanks Frodon! everything works now!
Anyway, the mod_ifsession was uncommented already, so I had to add the line you suggested in /etc/proftpd.conf, only!
No clues about mod_ls, instead! it's no listed! anyway, as I said, everything seems to be working!
Thanks again!

---

### Post by frodon on 2007-04-17
Glad to hear that :)

Could you post your proftpd.conf just to share your config with others, some may be interested by your config i think ;)

---

### Post by dannytherocker on 2007-04-17
> **frodon said:**
> Glad to hear that :)

Could you post your proftpd.conf just to share your config with others, some may be interested by your config i think ;)

Sure, I'll do it in the afternoon! even I think it's no a special one :-) many people could do it better :-)

---

### Post by Olsson on 2007-04-17
Thanks again frodon! 

Well I said the last questions.. But well I'm wondering one more thing! Are there any tutorial or do you got any tips on how to configure apache2 on proftpd?

---

### Post by frodon on 2007-04-17
> **Olsson said:**
> Thanks again frodon! 

Well I said the last questions.. But well I'm wondering one more thing! Are there any tutorial or do you got any tips on how to configure apache2 on proftpd?I'm scared that you reached the limit of my knowledge lol, seriously i never used apache2 server so i can't help you on this but if you have successfully set a FTP server it shouldn't be too hard ;)

---

### Post by dannyboy79 on 2007-04-17
> **frodon said:**
> No problem 

To join your FTP server in a browser you need to pass the username ine the adress, for example if your IP is 123.456.789.123 and your ftp username "toto" you will need to enter this in your browser :
```
ftp://toto@123.456.789.123
```
ALSA is a sound driver so this has nothing to do with you FTP server


just an FYI, for some ftp sites, I am able to simply type in [ftp://45.345.34.123](ftp://45.345.34.123)
and then internet explorer will pop open a dialog box. this is in IE 6.0.2800.1106.......

---

### Post by Spejs on 2007-04-20
I find your post for Proftp very useful, but I have a problem obviously with my firewall. I am on red hat and when I select my eth0 as trusted, remote machines can log on to my server, if its not trusted is not reachable
in my proftd.conf i added PassivePorts 49152 65534 and here is my iptables

Generated by iptables-save v1.2.11 on Thu Apr 19 17:52:31 2007
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [2259:2187792]
:RH-Firewall-1-INPUT - [0:0]
-A INPUT -j RH-Firewall-1-INPUT
-A INPUT -p tcp -m tcp --dport 49152:65534 -j ACCEPT
-A FORWARD -j RH-Firewall-1-INPUT
-A RH-Firewall-1-INPUT -i lo -j ACCEPT
-A RH-Firewall-1-INPUT -p icmp -m icmp --icmp-type any -j ACCEPT
-A RH-Firewall-1-INPUT -p ipv6-crypt -j ACCEPT
-A RH-Firewall-1-INPUT -p ipv6-auth -j ACCEPT
-A RH-Firewall-1-INPUT -d 224.0.0.251 -p udp -m udp --dport 5353 -j ACCEPT
-A RH-Firewall-1-INPUT -p udp -m udp --dport 631 -j ACCEPT
-A RH-Firewall-1-INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A RH-Firewall-1-INPUT -p tcp -m state --state NEW -m tcp --dport 80 -j ACCEPT
-A RH-Firewall-1-INPUT -p tcp -m state --state NEW -m tcp --dport 443 -j ACCEPT
-A RH-Firewall-1-INPUT -p tcp -m state --state NEW -m tcp --dport 21 -j ACCEPT
-A RH-Firewall-1-INPUT -p tcp -m state --state NEW -m tcp --dport 22 -j ACCEPT
-A RH-Firewall-1-INPUT -j REJECT --reject-with icmp-host-prohibited
COMMIT
# Completed on Thu Apr 19 17:52:31 2007


and here's the error from the remote ftp client

Error:               Transfer channel can't be opened. Reason: A socket operation was attempted to an unreachable host.

Error:               Could not retrieve directory listing

Command:       TYPE A

Error:       Timeout detected!

tell me what is the problem pls.

---

### Post by dannyboy79 on 2007-04-20
> **Spejs said:**
> I find your post for Proftp very useful, but I have a problem obviously with my firewall. I am on red hat and when I select my eth0 as trusted, remote machines can log on to my server, if its not trusted is not reachable
in my proftd.conf i added PassivePorts 49152 65534 and here is my iptables

Generated by iptables-save v1.2.11 on Thu Apr 19 17:52:31 2007
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [2259:2187792]
:RH-Firewall-1-INPUT - [0:0]
-A INPUT -j RH-Firewall-1-INPUT
-A INPUT -p tcp -m tcp --dport 49152:65534 -j ACCEPT
-A FORWARD -j RH-Firewall-1-INPUT
-A RH-Firewall-1-INPUT -i lo -j ACCEPT
-A RH-Firewall-1-INPUT -p icmp -m icmp --icmp-type any -j ACCEPT
-A RH-Firewall-1-INPUT -p ipv6-crypt -j ACCEPT
-A RH-Firewall-1-INPUT -p ipv6-auth -j ACCEPT
-A RH-Firewall-1-INPUT -d 224.0.0.251 -p udp -m udp --dport 5353 -j ACCEPT
-A RH-Firewall-1-INPUT -p udp -m udp --dport 631 -j ACCEPT
-A RH-Firewall-1-INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A RH-Firewall-1-INPUT -p tcp -m state --state NEW -m tcp --dport 80 -j ACCEPT
-A RH-Firewall-1-INPUT -p tcp -m state --state NEW -m tcp --dport 443 -j ACCEPT
-A RH-Firewall-1-INPUT -p tcp -m state --state NEW -m tcp --dport 21 -j ACCEPT
-A RH-Firewall-1-INPUT -p tcp -m state --state NEW -m tcp --dport 22 -j ACCEPT
-A RH-Firewall-1-INPUT -j REJECT --reject-with icmp-host-prohibited
COMMIT
# Completed on Thu Apr 19 17:52:31 2007


and here's the error from the remote ftp client

Error:               Transfer channel can't be opened. Reason: A socket operation was attempted to an unreachable host.

Error:               Could not retrieve directory listing

Command:       TYPE A

Error:       Timeout detected!

tell me what is the problem pls.

this is the same error that I get?? It does show me that I am logged in but then it gives me this error just like your saying and also doesn't show me any directories etc etc. what's weird is that at 1 time I did have this working and the only ports that I forwarded were 20 and 21 and I didn't use the Passive Ports option or masquarade option within proftpd but now I can't get it working again? I don't understand why it worked at one time and now it doesn't?

---

### Post by Spejs on 2007-04-20
The problem is within the firewall i previously i used this passive port range
-A INPUT -p tcp -m tcp --dport 49152:65534 -j ACCEPT

and then i change it to

-A INPUT -p tcp -m tcp --dport 1023:65534 -j ACCEPT

and it works now :P

dont know if I'm doing a mistake or not u this is the only solution that I found.

---

### Post by dannyboy79 on 2007-04-23
what about the passive ports config setting within proftpd.conf??? did you comment that out or change that value to match iptables? i can't believe we have to open all those ports!!!! very insecure I would think

---

### Post by pepotiger on 2007-04-23
Nice Tutorial Thnx :)

---

### Post by Spejs on 2007-04-24
U are opening the ports of the firewall, but u can still leave the range of the ftp not so widely open. U can make a small range of ur ftp conf if u have little users

---

### Post by dannyboy79 on 2007-04-24
i have a questions also, lets say that I will be the only one using this ftp server, do I have to use passive mode? are there advantages to using passive mode, i mean besides when many people use it at the same time?

---

### Post by Torahteen on 2007-04-24
Hey guys... I'm not sure if this has been asked and solved before (I got tired of reading through after the first 5 pages... sorry), but I have a problem. I did as in the tutorial. This is an FTP server to compliment my Apache web server, so I've got a user called webadmin that has the home directory of /var/www/, I can get into the server fine using KFTPGrabber, But when I try to delete any files, I get permission denied. I thought I had the right permissions allowed, but maybe not... here's the permissions part:

<Directory /var/www/>
Umask 022 022
AllowOverwrite on
    	<LIMIT RMD DELE READ WRITE STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

Did I type something wrong? Or what? Thanks in advance for the help.

---

### Post by tbuss on 2007-04-24
Okay, I have been using linux for a little over 2 months; and so far nothing as worked (exaggeration; just very frustrated). The funny thing is how grateful I am when something just partially works, like I'm making some type of progress or something. I've used this how-to before and it worked flawlessly for me, much appreciation. However, I did a clean install of edgy and decided to try and install proftpd again; felt a little more confident this time. I followed the how-to step by step up to the point of creating user accounts and passwords. I created a user account and set the password in the Users and Groups section. I get a 530 incorrect login when trying to connect. What is puzzling to me is when I go back to Users and Groups, the password entered is not what I declared earlier? I know you can't read what is entered but the password is shorter than what I entered. I tried to log out/in again but his had no effect. Is there something I'm missing? Why doesn't the password entered in User and Groups remain the same.

---

### Post by frodon on 2007-04-25
> **tbuss said:**
> Why doesn't the password entered in User and Groups remain the same.Maybe it's just a bug or a typo when you typed the password. Anyway you can change it with this command :
```
sudo passwd username
```

---

### Post by tbuss on 2007-04-25
I've got it up and running, thanks for help

---

### Post by Jordanwb on 2007-04-26
I got to Part B Step 3 in the understanding department however the larger text about editing the proftpd.conf I have no idea what I'm supposed to edit. Any suggestions?

---

### Post by frodon on 2007-04-27
I don't know it depends on you, edit what don't fit your needs like the ftp server port number for example (1980 in the guide) or the directory paths or maybe if it's fine for you like that just cut and paste.

---

### Post by carnussien on 2007-04-27
Hello,
I am an absolute beginner .
I get this in my terminal session:

[COLOR="Lime"][CENTER]robert@pentiumIII:~$ sudo apt-get install proftpd gproftpd
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package proftpd
robert@pentiumIII:~$[/CENTER][/COLOR]

What can i do ?
Thanks for your help

---

### Post by dannyboy79 on 2007-04-27
enable the repositories that proftpf exists in. i believe it's in the universe repo. here's mine for dapper:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

just do 

sudo cp /etc/apt/sources.list /etc/apt/sources.list-backup

(This step backs it up in case you need to revert to the original. this is a good habit with all system files. always backup first)

gksudo gedit /etc/apt/sources.list

(then just read the contents of the file and where it states to uncomment the 2 lines that are similar to mine, that means to delete the pound symbol. In linux, a pound symbol (#) usually means that the line that starts with that symbol is "generally" not used, meaning it's not part of the program etc etc.

then make sure you save the file before you close. then

sudo aptitude update && aptitude upgrade

then simply try to install it again and it should work this time as you have now enabled tons of other software possibilities.

---

### Post by Kulgan on 2007-04-30
A lot of people, not only here, seem to get a 530 error. A simple way to test what that's all about is to modify the [XAMPP]("http://www.apachefriends.org/en/xampp-linux.html#374") config file to suit the server. It reads:

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

# Normally, we want files to be overwriteable.
<Directory /home/ftp/*>
  AllowOverwrite		on
</Directory>

# only for the web servers content
DefaultRoot /home/ftp

# nobody gets the password "lampp"
UserPassword nobody wRPBu8u4YP0CY

# nobody is no normal user so we have to allow users with no real shell
RequireValidShell off

# nobody may be in /etc/ftpusers so we also have to ignore this file
UseFtpUsers off

```

It's not as secure, but it's a step towards debugging the problem, at least. Of course, if you were to use this config, you would have to change the username and password. I also changed the "/home/FTP-shared/[up|down]load" system to just having one folder for it all. Seems a little more... logical.

---

### Post by Jordanwb on 2007-04-30
How do I get to the GUI in 7.04 Server?

---

### Post by carnussien on 2007-05-02
Hello Dannyboy79,
Thanks for your help about /etc/apt/sources.list
I could install my proftpd  program. Fine
Next job for me : work with it !

---

### Post by Jordanwb on 2007-05-02
^ Same for me. Now I have to figure out what to change and how to get to the GUI.

---

### Post by dannyboy79 on 2007-05-04
> **Jordanwb said:**
> ^ Same for me. Now I have to figure out what to change and how to get to the GUI.

what gui are you guys talking about? maybe gproftpd? If you follow his guide there is really no need for a gui. it's just editing 1 file and he has great instructions. plus you'll learn more this way whereas when you use a gui you're so dependent on it and then what if you upgrade somethign and then the gui doesn't work, you're stuck and then have to learn how to manually edit files anyway. just my 2 cents.

---

### Post by `opH on 2007-05-12
i start server and it get back something like this

* Starting ftp server proftpd                                                   - IPv6 getaddrinfo 'hal9000' error: No address associated with hostname



what should i do?

thx a lot

---

### Post by Kulgan on 2007-05-12
start by posting the content of your /etc/hosts file

---

### Post by dannyboy79 on 2007-05-12
> **`opH said:**
> i start server and it get back something like this

* Starting ftp server proftpd                                                   - IPv6 getaddrinfo 'hal9000' error: No address associated with hostname



what should i do?

thx a lot
this error is ok, it's merely stating that you don't have a regisetered hostname on IPv6 inernet and according to Frodon this is ok. I see he error on my fp server and i still works. no sure what page frodon commens abou this on but it's alright or are you saying that your server isn't working?

---

### Post by `opH on 2007-05-12
> **Kulgan said:**
> start by posting the content of your /etc/hosts file


127.0.0.1 localhost
86.49.126.49 hal9000
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by Kulgan on 2007-05-12
can you connect to the ftp server?

---

### Post by tbuss on 2007-05-13
`opH

add your box's name to the IPv6 info in /etc/hosts:
```
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback <add it here>
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Do this if you wish for the error message to go away, it is no big deal like dannyboy79 said, but if the message annoys you then just add you box's name like above.

---

### Post by `opH on 2007-05-13
> **tbuss said:**
> `opH

add your box's name to the IPv6 info in /etc/hosts:
```
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback <add it here>
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Do this if you wish for the error message to go away, it is no big deal like dannyboy79 said, but if the message annoys you then just add you box's name like above.


thank you very much now it's work

---

### Post by crapaud on 2007-05-14
Hallo!
I have Ubuntu 6.06 with ProFTPd 1.3.0. Now I  want to configure mod_tls. I've read the first post of this topic and done all. 
Now, if mod_tls ON, connection to ftp is very slow, and TLS isn't work :-(  
In TLS.log:
> mod_tls/2.1.1[15712]: ssl/tls required but absent on control channel, denying USER command 
What I've done wrong?

---

### Post by `opH on 2007-05-15
i've got another problem... nobody cam connect to my FTP. it's like he haven't a created acc but i created it. what should i post to get me an advice? thx opH

---

### Post by Darth_tater on 2007-06-07
wow!  great guide!

i managed to use your guide as a base for setting up my own multi user server  (see here: [http://ubuntuforums.org/showthread.php?t=466582](http://ubuntuforums.org/showthread.php?t=466582))

but, i wanted to try encrypted FTP, and i managed to follow your instructions and now my server operates only on SSL (as i would like...) but when i try to connect this is the output i get

```
 WinSock 2.0 -- OpenSSL 0.9.8b 04 May 2006
[R] Connecting to 192.168.2.88 -> IP=192.168.2.88 PORT=1396
[R] Connected to 192.168.2.88
[R] 220 you're at home
[R] AUTH TLS
[R] 234 AUTH TLS successful
[R] Connected. Negotiating TLSv1 session..
[R] error:14094410:SSL routines:SSL3_READ_BYTES:sslv3 alert handshake failure
[R] Failed TLSv1 negotiation, disconnected
[R] Connection failed (Connection closed by client)
[R] Delaying for 120 seconds before reconnect attempt #1
[R] Retry attempt Aborted
```

this output comes from flashfxp 3.4.0 running on windows x64

any ideas?

---

### Post by dannyboy79 on 2007-06-07
> **Darth_tater said:**
> wow!  great guide!

i managed to use your guide as a base for setting up my own multi user server  (see here: [http://ubuntuforums.org/showthread.php?t=466582](http://ubuntuforums.org/showthread.php?t=466582))

but, i wanted to try encrypted FTP, and i managed to follow your instructions and now my server operates only on SSL (as i would like...) but when i try to connect this is the output i get

```
 WinSock 2.0 -- OpenSSL 0.9.8b 04 May 2006
[R] Connecting to 192.168.2.88 -> IP=192.168.2.88 PORT=1396
[R] Connected to 192.168.2.88
[R] 220 you're at home
[R] AUTH TLS
[R] 234 AUTH TLS successful
[R] Connected. Negotiating TLSv1 session..
[R] error:14094410:SSL routines:SSL3_READ_BYTES:sslv3 alert handshake failure
[R] Failed TLSv1 negotiation, disconnected
[R] Connection failed (Connection closed by client)
[R] Delaying for 120 seconds before reconnect attempt #1
[R] Retry attempt Aborted
```

this output comes from flashfxp 3.4.0 running on windows x64

any ideas?

I never could get encryption to work either but from what I see, you're trying to use 2 different protocols, TLSv1 and SSLv3, those can't communicate properly I don't think. Is there an preference within FlashFXP for the encypt protocol that is used? sorry I couldn't be of more help.

---

### Post by frodon on 2007-06-08
Darth_tater, Are you sure to have selected the right protocol ? The instruction in my guide are for TLS encryption (also called FTPS) not SSL (which is called SFTP).

---

### Post by Darth_tater on 2007-06-08
uhh, as ia said above flashfxp 3.4.0 running on windows x64

here is a screenshot...

[[IMG]http://img338.imageshack.us/img338/2774/ftpdl4.th.jpg[/IMG]](http://img338.imageshack.us/my.php?image=ftpdl4.jpg)

---

### Post by frodon on 2007-06-11
Could you try with another FTP client just to be sure that it's not a FTP client issue, ? If you have firefox you can try the fireFTP extension it has TLS support.

---

### Post by godlygb on 2007-06-12
nvm fixed it**
post edited**

---

### Post by dannyboy79 on 2007-06-12
I haven't tried this in a very long time but I just found this and it may or may not help you. BUt according to this link: [http://www.verio.com/support/documents/view_article.cfm?doc_id=2261](http://www.verio.com/support/documents/view_article.cfm?doc_id=2261)
you need to ensure that your server will accept various ciphers of the TLS/SSL encryption so they suggest adding this to your TLS section within your proftpd.conf file.

TlsCipherList                  ALL:!EXP

As I said, don't know if it will help, just found it and thought what the hell, might as well let him know. Good luck

---

### Post by Heinrisch on 2007-06-14
I have followed the guide step by step but I can't get it to work. I try to log on to my servers ftp from IE, I type the correct port and the login box pops up. I enter the correct information and the box dissapears and it start to load, then nothing happens, it never gets passed the loading part. Anyone who has a solution for this?

---

### Post by frodon on 2007-06-15
Heinrisch, we need more details to help you like your config, you proftpd.conf, the log of your FTP client and in general all informations that can help to make an analysis. Without that it will be hard to help you.

---

### Post by Heinrisch on 2007-06-15
This is my config:
```
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias samba userftp

ServerName			"wihoo"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port				1112

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
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

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
```

Its basically the same as the example, I thinkn I only changed the username and the port.  Im running the latest version of the ubuntu server.

This is what my ftp log says:
```

...
::ffff:192.168.1.1 UNKNOWN nobody [14/Jun/2007:22:22:16 -0400] "USER samba" 331 -
::ffff:192.168.1.1 UNKNOWN userftp [14/Jun/2007:21:22:16 -0500] "PASS (hidden)" 230 -
::ffff:192.168.1.1 UNKNOWN userftp [14/Jun/2007:21:22:16 -0500] "CWD /" 250 -
::ffff:192.168.1.1 UNKNOWN userftp [14/Jun/2007:21:22:16 -0500] "TYPE A" 200 -
::ffff:192.168.1.1 UNKNOWN userftp [14/Jun/2007:21:22:16 -0500] "PASV" 227 -
...

```

When I try to log this happens:
I connect, get respons from server asking me for password, sending back password and then it timeouts..

---

### Post by seodavid on 2007-06-20
Hello,

Thankyou for your guide,

Im having this problem, and i dont know what it means:
(the IPv4 gettaddrinfo 'MAINSERVER' bit)
[img]http://xs216.xs.to/xs216/07254/proftpd-instal-problem.png[/img]

And had i mention same thing while trying ot install, so not sure about what the current users/passes are set to as default etc.

:(

---

### Post by frodon on 2007-06-21
First post your proftpd.conf and run a synthax check just to be sure that there's no errors in your proftpd.conf file :
```
proftpd -nd5
```

---

### Post by seodavid on 2007-06-21
Here is the Config:
```
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias sauron userftp

ServerName			"KALM-FTP-Server"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port				1980

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
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

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
```

---

### Post by frodon on 2007-06-21
And about the syntax check, does it return errors ?

Anyway, proftpd don't like complex name with special characters like "-" so i would advice you to choose a simple name instead then test again your server.

---

### Post by seodavid on 2007-06-21
> **frodon said:**
> And about the syntax check, does it return errors ?

Anyway, proftpd don't like complex name with special characters like "-" so i would advice you to choose a simple name instead then test again your server.

Changed the name so config is now:

```

# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias sauron userftp

ServerName			"kalmftp"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port				1980

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
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

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

```

and screenshot of the test u said to do:

[img]http://xs216.xs.to/xs216/07254/proftp-nd5.png[/img]

And if i use:

```

sudo /etc/init.d/proftpd start

```

IT comes up with:

```

david@MAINSERVER:~$ sudo /etc/init.d/proftpd start
Password:
 * Starting ftp server proftpd                                                   - IPv4 getaddrinfo 'MAINSERVER' error: No address associated with hostname
 - warning: unable to determine IP address of 'MAINSERVER'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
                                                                         [fail]
david@MAINSERVER:~$ 

```

---

### Post by frodon on 2007-06-21
Ok if "proftpd -nd5" give you erros then that's not worth to try to start the server because it's sure it will fail. I advice you to take the time to read this thread, if you would have read it before posting you would have surely found this post (post #41) where a user already had a similar problem and explained how to solve it, thanks for using the search function ;) :
[http://ubuntuforums.org/showpost.php?p=2329159&postcount=409](http://ubuntuforums.org/showpost.php?p=2329159&postcount=409)

---

### Post by seodavid on 2007-06-21
> **frodon said:**
> Ok if "proftpd -nd5" give you erros then that's not worth to try to start the server because it's sure it will fail. I advice you to take the time to read this thread, if you would have read it before posting you would have surely found this post (post #41) where a user already had a similar problem and explained how to solve it, thanks for using the search function ;) :
[http://ubuntuforums.org/showpost.php?p=2329159&postcount=409](http://ubuntuforums.org/showpost.php?p=2329159&postcount=409)

Thanx for the link, I used the search, just not well enough:p

Anyway, proftpd -nd5 now gives:

```

root@MAINSERVER:~# proftpd -nd5
 - mod_ctrls/0.9.4: binding ctrls socket to '/var/run/proftpd/proftpd.sock'
 - parsing '/etc/proftpd/proftpd.conf' configuration
 - <Directory /home/FTP-shared>: deferring resolution of path
 - <Directory /home/FTP-shared/download/*>: deferring resolution of path
 - <Directory /home/FTP-shared/upload/>: deferring resolution of path
 - IPv6 getaddrinfo 'MAINSERVER' error: No address associated with hostname
localhost - 
localhost - Config for kalmftp:
localhost - /home/FTP-shared/upload/
localhost -  Limit
localhost -   AllowAll
localhost -  Limit
localhost -   DenyAll
localhost -  Umask
localhost -  DirUmask
localhost -  AllowOverwrite
localhost -  AuthAliasOnly
localhost -  UserAlias
localhost -  ShowSymlinks
localhost -  DisplayFirstChdir
localhost -  ListOptions
localhost -  RequireValidShell
localhost -  RootLogin
localhost -  TransferLog
localhost -  UseFtpUsers
localhost -  AllowStoreRestart
localhost -  MaxClients
localhost -  MaxClientsPerHost
localhost -  MaxClientsPerUser
localhost -  MaxHostsPerUser
localhost -  AccessGrantMsg
localhost - /home/FTP-shared/download/*
localhost -  Limit
localhost -   DenyAll
localhost -  Umask
localhost -  DirUmask
localhost -  AllowOverwrite
localhost -  AuthAliasOnly
localhost -  UserAlias
localhost -  ShowSymlinks
localhost -  DisplayFirstChdir
localhost -  ListOptions
localhost -  RequireValidShell
localhost -  RootLogin
localhost -  TransferLog
localhost -  UseFtpUsers
localhost -  AllowStoreRestart
localhost -  MaxClients
localhost -  MaxClientsPerHost
localhost -  MaxClientsPerUser
localhost -  MaxHostsPerUser
localhost -  AccessGrantMsg
localhost - /home/FTP-shared
localhost -  Limit
localhost -   DenyAll
localhost -  Umask
localhost -  DirUmask
localhost -  AllowOverwrite
localhost -  AuthAliasOnly
localhost -  UserAlias
localhost -  ShowSymlinks
localhost -  DisplayFirstChdir
localhost -  ListOptions
localhost -  RequireValidShell
localhost -  RootLogin
localhost -  TransferLog
localhost -  UseFtpUsers
localhost -  AllowStoreRestart
localhost -  MaxClients
localhost -  MaxClientsPerHost
localhost -  MaxClientsPerUser
localhost -  MaxHostsPerUser
localhost -  AccessGrantMsg
localhost - Limit
localhost -  AllowUser
localhost -  DenyAll
localhost - AllowOverwrite
localhost - AuthAliasOnly
localhost - UserAlias
localhost - DeferWelcome
localhost - DefaultServer
localhost - ShowSymlinks
localhost - TimeoutNoTransfer
localhost - TimeoutStalled
localhost - TimeoutIdle
localhost - DisplayFirstChdir
localhost - ListOptions
localhost - RequireValidShell
localhost - TimeoutLogin
localhost - RootLogin
localhost - ExtendedLog
localhost - TransferLog
localhost - UseFtpUsers
localhost - AllowStoreRestart
localhost - UserID
localhost - UserName
localhost - GroupID
localhost - GroupName
localhost - Umask
localhost - DirUmask
localhost - MaxClients
localhost - MaxClientsPerHost
localhost - MaxClientsPerUser
localhost - MaxHostsPerUser
localhost - AccessGrantMsg
localhost - ServerIdent
localhost - DefaultRoot
localhost - DefaultRoot
localhost - MaxLoginAttempts
localhost - mod_ctrls/0.9.4: binding ctrls socket to '/var/run/proftpd/proftpd.sock'
localhost - deleting existing scoreboard '/var/run/proftpd/proftpd.scoreboard'
localhost - error setting IPV6_V6ONLY: Protocol not available
localhost - Failed binding to ::, port 1980: Address already in use
localhost - Check the ServerType directive to ensure you are configured correctly.
root@MAINSERVER:~# 

```

And when u run "sudo /etc/init.d/proftpd start":
(I did not expect to work)
```

root@MAINSERVER:~# sudo /etc/init.d/proftpd start
 * Starting ftp server proftpd                                                                                                                    - IPv6 getaddrinfo 'MAINSERVER' error: No address associated with hostname
                                                                                                                                          [ OK ]
root@MAINSERVER:~# 

```

the "IPv6 getaddrinfo 'MAINSERVER' error: No address associated with hostname" bit does not seem right :s

Thanx for your help so far btw.

---

### Post by frodon on 2007-06-22
From what i read on the proftpd forum the IPv6 error don't prevent the FTP server to work properly (i have it as well because i use IPv4 address) so you can just forget this one, you get this error because you don't use IPv6 address, anyway if you want to solve this error message read this post :
[http://ubuntuforums.org/showpost.php?p=2295568&postcount=2](http://ubuntuforums.org/showpost.php?p=2295568&postcount=2)

---

### Post by hobs0n on 2007-07-01
Newb question :D

Is there a FTP server for linux that you can share other HDDs/directories? When I had a Windows server running I used the old trustworthy FTP server G6 and in that you could just share whatever directory you wanted too and make links so you could see all the shared dirs in the root dir. Is this possible with some linux FTP server?

---

### Post by frodon on 2007-07-01
It is exactly what you do here, just mount the directoty/hdd you want in the dowload or upload directory and you are all done ;)
Look in the first post the mount command details are given

---

### Post by hobs0n on 2007-07-01
Hm ok ;) Sorry.. I guess I never looked hard enough, Ive checked various ftp servers and missed the fact that you mount what dirrs and HDDs you want =)

---

### Post by frodon on 2007-07-01
The tip is that the mount command allows you to mount a directory (even already mounted) in another one, this command don't overwritte the content of the destination directory it just kind of wrap it in your wanted download/upload directory.
That's why ultimatly the name and the place where you share the directory don't really matter because you can mount in what you want.

Hope my explanation make sense.

Good luck ;)

---

### Post by wizekid on 2007-07-01
how can i change the ftp directory to /var/www? i want to upload files straight into the www directory

---

### Post by frodon on 2007-07-01
Please take the time to read the thread (or at least a part of)  before posting, why should one take the time to answer your question when you don't take the time to find this answer in the thread (because the answer to your question is already in the thread).

To be quick either put "/var/www" as home directory for your ftpuser and adapt the directory section or like i said in my previous post (yes the one above your post) mount your /var/www directory in the upload directory.

---

### Post by bucketoclams on 2007-07-01
First, I'd like to apologize if I'm posting a problem already met. I dug through this thread as much as I could (I even used the search functions just in case I missed anything). I thought I'd wait for an answer to [[COLOR="Blue"]this thread[/COLOR]](http://ubuntuforums.org/showthread.php?t=467872&highlight=proftpd+socket), but it was empty for 3 weeks when I looked at it.

I'm having the same problem as that guy. Here's what mine says, specifically:

> nate@nate-desktop:/$ proftpd
 - notice: unable to bind to Unix domain socket at '/var/run/proftpd/test.sock': Permission denied
 - notice: unable to listen to local socket: Address already in use
 - Fatal: SystemLog: unable to redirect logging to '/var/log/proftpd/proftpd.log': Permission denied on line 87 of '/etc/proftpd/proftpd.conf'

Here's my proftpd.conf file:

> # To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias bucketoclams userftp

ServerName			"desknate"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  userftp
Group                 userftp

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /media/hdb1/FTP-Shared directory as home directory
DefaultRoot /media/hdb1/FTP-Shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /media/hdb1/FTP-Shared>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /media/hdb1/FTP-Shared/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /media/hdb1/FTP-Shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

Sorry if that's a bit of an unruly way to display it. I have everything on a secondary, much larger hard drive in the box, which is why it's at /media/hdb1/FTP-Shared instead of just /home.

Just let me know if you need any more info. Thanks!

---

### Post by frodon on 2007-07-02
proftpd needs to be run as root and i think it may be the problem here, the command to start proftpd is :
```
sudo /etc/init.d/proftpd start
```

Hope it solves you problem.

---

### Post by bucketoclams on 2007-07-02
Well, it kind of solved it. It showed me other things, and now I'm going through and finding info about them (all common errors, no need to repeat). Thanks!

---

### Post by frodon on 2007-07-02
Great, feel free to post questions, sometimes even when reading post containing the answer we are not sure of what to do so if you need some infos go on ;)

---

### Post by poncho1 on 2007-07-03
found this post very helpful but would like to know what these command do or at least be able to find a link to a listing of what they do....

<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>

some info on the rnrf and rnto and rnef would be great....

thanks again for the how to

---

### Post by frodon on 2007-07-03
> **poncho1 said:**
> found this post very helpful but would like to know what these command do or at least be able to find a link to a listing of what they do....

<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>

some info on the rnrf and rnto and rnef would be great....

thanks again for the how toDon't forget the documentation in such case ;) :
[http://www.proftpd.org/localsite/Userguide/linked/userguide.html](http://www.proftpd.org/localsite/Userguide/linked/userguide.html)

You will find what interest you in the LIMIT directive documentation :
[http://www.proftpd.org/localsite/Userguide/linked/config_ref_Limit.html](http://www.proftpd.org/localsite/Userguide/linked/config_ref_Limit.html)

---

### Post by BradMajors on 2007-07-04
I can not install proftpd.  I get the following error messages:

----------------------------------------------------------------------------------------------

root@server:/home/brad# apt-get install proftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  proftpd-doc
The following NEW packages will be installed:
  proftpd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/784kB of archives.
After unpacking 2331kB of additional disk space will be used.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Preconfiguring packages ...
Selecting previously deselected package proftpd.
(Reading database ... 116567 files and directories currently installed.)
Unpacking proftpd (from .../proftpd_1.3.0-21ubuntu1_i386.deb) ...
Setting up proftpd (1.3.0-21ubuntu1) ...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
 * Starting ftp server proftpd                                                                     - IPv4 getaddrinfo 'server' error: No address associated with hostname
 - warning: unable to determine IP address of 'server'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
                                                                                           [fail]
invoke-rc.d: initscript proftpd, action "start" failed.
dpkg: error processing proftpd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Skootle on 2007-07-04
I've managed to install proFTPd and it works just fine, except for one problem. When a computer from my LAN connects to my FTP server and downloads something, it is limited to 30KB/s... :( I don't know why it is so slow. Any ideas?

---

### Post by frodon on 2007-07-04
You can try to specify explicitlty the maximum transfer rate, for example :
```
TransferRate RETR 4096
```

Documentation :
[http://www.proftpd.org/localsite/Userguide/linked/config_ref_TransferRate.html](http://www.proftpd.org/localsite/Userguide/linked/config_ref_TransferRate.html)

Anyway this is strange, you shouldn't have such problems, i believe that by default it takes the maximum bandwidth it can.

---

### Post by ltcmdata on 2007-07-04
Hi!
I used the default GPROFTPD configuration to set up my server, I added a user and am able to connect to the server from my own computer, but noone can connect from the outside.I don't have any routers or such things, and my friend who is trying to connect can ping me.he is using filezilla and gets the message "Waiting for welcome message..."and there it sits.
I could post my gproftpd.conf, but I really haven't touched a thing in it, everything is default.
Any help will be appreciated...

Data

---

### Post by dannyboy79 on 2007-07-05
what does this return?
sudo iptables -L

if there are any rules shown then you need to allow connections on the port you're using for your ftp server. Iptables is the main firewall for Ubuntu and many other Distribution. If you're not using a firewall, I'd ask you why in the heck not especially if you don't have a Hardware Firewall (router or the likes). If that still doesn't work, have your friend try a different client. Firefox has a free client (meaning he'd have to install Firefox first) as a plugin, it's called FireFTP. Check it out, it's actually a very usable client. If that doesn't work, there is most likely other free clients but I am not sure of them for Winbloz.

---

### Post by dannytherocker on 2007-07-05
> **frodon said:**
> There is another thing i didn't see before, in the "<Directory> /home/ftp/upload/>" field, modify it like that : ```
<Directory> /home/ftp/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	**AllowAll**
    	</Limit>
</Directory>

```This will allow you to write in the upload directory.
Now for your login issue, try to login your gnome session with **userftp** in order to be sure that it's not a user creation problem. Check also that your home/ftp directory have 755 rights.

Hi frodon,

I've got a problem I thought I had passed, but I did not :-)

3 users accessing the download dir, but only one, that's me, aliased userftp2 can write, delete, rename and make all this an admin does, into this dir.
Here's my lines, but it doesn't work!
Can you help me ? Thanks a lot :-)

```
<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
           <Limit ALL>
		Order Allow,Deny
		AllowUser userftp
		AllowUser userftp2
               AllowUser userftp3
               Deny ALL
	       </Limit>
	
            <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	     Order Allow,Deny
             AllowUser userftp2
             DenyAll
	     </Limit>
</Directory>
```

---

### Post by frodon on 2007-07-05
I'm not sure i'm not misunderstanding you but you should allow the real user in the directory not the alias name (the alias name don't matter).
You are also supposed to have a general "Limit LOGIN" section outside the "directory" section where you allow login from all the wanted user.

---

### Post by ltcmdata on 2007-07-05
Thanks for the advice, but I figured it out.I had to use a port that is in the passive port range.I don't quite understand why this is so, but it works now :D

---

### Post by dannytherocker on 2007-07-06
> **frodon said:**
> I'm not sure i'm not misunderstanding you but you should allow the real user in the directory not the alias name (the alias name don't matter).
You are also supposed to have a general "Limit LOGIN" section outside the "directory" section where you allow login from all the wanted user.

I'm sorry...my fault....my explanation was not so clear.! 
userftp2 is not an alias, it's the real name....and so are userftp3 and userftp!
Limit LOGIN is set up correctly (I followed your guide, many months ago :-) ) 
My target is to allow userftp2 only to write, delete, rename etc in the "download" directory!
of contrary, userftp3 and userftp could not !

But now a new suspect is in my mind:

when I set up my ftp server, "/home/FTP-Shared" directory and "/home/FTP-Shared/download" directory were chmoded by 755 ! so the real owner is only the system user who did this (by using sudo, obviously), that's me! 
I'll never be able to write in download dir. just because "userftp2" doesn't match the real system user (myself).

and the confirmation is that everyone can do eveything in "upload" dir., chmoded 777 :-)
 

Is this correct ?

Maybe this could be a good solution:

I could give userftp2 a valid shell for a little while....then I could switch to userftp2 by typing ```
su userftp2
``` and chmod by 755 the download dir.
From now on, userftp2 will be the owner and will be able to do everything into that dir :-)
Last but not least, I could give him back a fake shell !

I'll give a try :-)

---

### Post by rev0 on 2007-07-07
I have read through all the posts here, read some 3rd party sites, and formatted my ubuntu box twice to try to get SSL/TLS secure ftp working.

My ftp works fine without encryption, however with encryption I get these errors.

```
WinSock 2.0 -- OpenSSL 0.9.8b 04 May 2006
[R] Connecting to 192.168.1.102 -> IP=192.168.1.102 PORT=21
[R] Connected to 192.168.1.102
[R] 220 ProFTPD 1.3.0 Server (Restricted-Access) [::ffff:192.168.1.102]
[R] AUTH TLS
[R] 234 AUTH TLS successful
[R] Connected. Negotiating TLSv1 session..
[R] error:14094410:SSL routines:SSL3_READ_BYTES:sslv3 alert handshake failure
[R] Failed TLSv1 negotiation, disconnected
[R] Connection failed (Connection closed by client)
[R] Delaying for 120 seconds before reconnect attempt #1
```

Not quite sure...I have noticed other uses have had this similar problem, and any help would be much appreciated. Thank you in advance.

---

### Post by dannyboy79 on 2007-07-10
> **rev0 said:**
> I have read through all the posts here, read some 3rd party sites, and formatted my ubuntu box twice to try to get SSL/TLS secure ftp working.

My ftp works fine without encryption, however with encryption I get these errors.

```
WinSock 2.0 -- OpenSSL 0.9.8b 04 May 2006
[R] Connecting to 192.168.1.102 -> IP=192.168.1.102 PORT=21
[R] Connected to 192.168.1.102
[R] 220 ProFTPD 1.3.0 Server (Restricted-Access) [::ffff:192.168.1.102]
[R] AUTH TLS
[R] 234 AUTH TLS successful
[R] Connected. Negotiating TLSv1 session..
[R] error:14094410:SSL routines:SSL3_READ_BYTES:sslv3 alert handshake failure
[R] Failed TLSv1 negotiation, disconnected
[R] Connection failed (Connection closed by client)
[R] Delaying for 120 seconds before reconnect attempt #1
```

Not quite sure...I have noticed other uses have had this similar problem, and any help would be much appreciated. Thank you in advance.

if you notice the handshake is attempting sslv3 and your server is using TLSv1, I am guessing the client you're using isn't using the correct encryption handshake protocol BUT with that said, I couldn't get TLS to work either. Kind of sucks if you ask me. Why don't you just tunnel in with SSH, that way all your ftp stuff will be encrypted within the SSH tunnel. I only have 1 port open, and that's for ssh and even that has Public/Private Key pair for authentification, so it's very secure. I then tunnel my x11vnc, my ftp, my mythweb all thru that tunnel.

---

### Post by smed on 2007-07-11
I'm having trouble adding users. 

I understand that multiple people can use the original user name, but I want some users to have a different home directory.

Can someone please explain how to successfully add users and be able to connect through smartftp

Thanks

---

### Post by frodon on 2007-07-12
You should find some examples in this thread, some users have posted configurations with several users and different home directory.

---

### Post by Spejs on 2007-07-14
Hi
I have created proftp server on RHES, and it works fine, thanks to this post but I have some complaints when users try to log in. They say it is very slow when u try to log in and also when u browse the folders, some say it took them 2 min to log in. Download speed is good. Here is my profto conf file 


# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias user userftp
UserAlias admins administrator
UserAlias admin spejs

ServerName			"Net Cable"
ServerType 			standalone
DeferWelcome			on

MasqueradeAddress 89.185.223.5
#PassivePorts                    50000 65534

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port				21


# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 100

# Set the user and group that the server normally runs at.
User                  nobody
#Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 1000
MaxClientsPerHost 1000
MaxClientsPerUser 1000
MaxHostsPerUser 1000

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "NetCable's Freeserver"

# Set /home/FTP-shared directory as home directory
# DefaultRoot /ftproot

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
AllowUser spejs
AllowUser administrator
DenyALL
</Limit>

<Directory /ftproot/>
Umask 022 022
AllowOverwrite off
	
	<Limit ALL>
		Order Allow,Deny
		AllowUser userftp
		AllowUser spejs
		Deny ALL
	</Limit>


	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        Order Allow,Deny
	AllowUser spejs	
        DenyAll
	</Limit>
</Directory>

<Directory /ftproot/*>
Umask 022 022
AllowOverwrite off
	<Limit ALL>
		Order Allow,Deny
		AllowUser userftp
		AllowUser spejs
		Deny ALL
	</Limit>

	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	Order Allow,Deny
	AllowUser spejs
	DenyAll
	</Limit>
</Directory>

<Directory> /ftproot/upload/>
Umask 022 022
AllowOverwrite on
	

	<Limit ALL>
		Order Allow,Deny
		AllowUser spejs
		# AllowUser userftp
		Deny ALL
	</Limit>

  	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

<Directory /admin/>
Umask 022 022
AllowOverwrite off
	
	<Limit ALL>
		Order Allow,Deny
		AllowUser administrator
		Deny ALL
	</Limit>


	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        Order Allow,Deny
	AllowUser administrator
        DenyAll

---

### Post by anpk on 2007-07-15
I have successfully installed proftpd and run it as root. It works fine when I connect to it from inside or outside my local network.
I want to change the permissions so that the server runs as non root. However when I run it, I get the following error.

anoopk@app1:~$ sudo -u ftpuser service proftpd start
open: Permission denied
 * Starting ftp server proftpd                                                                                                - notice: unable to bind to Unix domain socket at '/var/run/proftpd/test.sock': Permission denied
 - notice: unable to listen to local socket: Address already in use
app1.home.net - 127.0.1.1:75 masquerading as 75.58.60.212
app1.home.net - PRIVS_ROOT: unable to seteuid(): Operation not permitted
app1.home.net - PRIVS_ROOT: unable to setegid(): Operation not permitted
app1.home.net - PRIVS_RELINQUISH: unable to seteuid(PR_ROOT_UID): Operation not permitted
app1.home.net - PRIVS_RELINQUISH: unable to setegid(session.gid): Operation not permitted
app1.home.net - PRIVS_RELINQUISH: unable to seteuid(session.uid): Operation not permitted
app1.home.net - mod_delay/0.5: error opening DelayTable '/var/run/proftpd/proftpd.delay': No such file or directory
app1.home.net - PRIVS_ROOT: unable to seteuid(): Operation not permitted
app1.home.net - PRIVS_ROOT: unable to setegid(): Operation not permitted
app1.home.net - PRIVS_RELINQUISH: unable to seteuid(PR_ROOT_UID): Operation not permitted
app1.home.net - PRIVS_RELINQUISH: unable to setegid(session.gid): Operation not permitted
app1.home.net - PRIVS_RELINQUISH: unable to seteuid(session.uid): Operation not permitted
app1.home.net - unable to set daemon groups: Operation not permitted
app1.home.net - PRIVS_ROOT: unable to seteuid(): Operation not permitted
app1.home.net - PRIVS_ROOT: unable to setegid(): Operation not permitted
app1.home.net - PRIVS_RELINQUISH: unable to seteuid(PR_ROOT_UID): Operation not permitted
open: Permission denied

I have attached my conf file for the configuration details. 

I have also tried adding the ip to the iptables
sudo iptables -A INPUT -p tcp -m tcp --dport 75 -j ACCEPT


I have searched on google and havent found anything to point me in the right direction, not sure if I missed anything in the forums either.
Any help will be greatly appreciated.
Thanks in advance,

---

### Post by frodon on 2007-07-15
> **anpk said:**
> I want to change the permissions so that the server runs as non root. Why such a need ? It makes your computer more secure to require root rights to run or modify services

---

### Post by r0ot5 on 2007-07-18
hi, i'm new to ubuntu 6.10 and i'm trying to setup an ftp on it and after I finish the setup I receive this error:

> 
ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration.

Setting up gproftpd (8.2.6-1) 3



here my config file

> 
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

ServerName			"Debian"
ServerType			inetd
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

DenyFilter			\*.*/

# Port 21 is the standard FTP port.
Port				21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                    49152 65534

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				proftpd
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd		off

# Be warned: use of this directive impacts CPU average load!
#
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
# UseSendFile			off

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_tls.c>
TLSEngine off
</IfModule>

<IfModule mod_quota.c>
QuotaEngine on
</IfModule>

<IfModule mod_ratio.c>
Ratios on
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        on
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine on
</IfModule>

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayFirstChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>



thx all for your help

---

### Post by frodon on 2007-07-19
The guide is for a standalone server no support is provided for the inetd mode. The line "ServerType inetd" shows that you are using the inetd mode.

---

### Post by r0ot5 on 2007-07-19
I try using the standalone also & still giving me an error!

---

### Post by frodon on 2007-07-19
Then please give the error message, i can't guess what the problem is without error log.

---

### Post by r0ot5 on 2007-07-19
I updated my conf file to use standalone and when I start the service here what I receive:

 * Starting ftp server proftpd                                                   - IPv6 getaddrinfo 'ks351281.kimsufi.com' error: Name or service not known
                                                                         [ ok ]

thx for your help!

---

### Post by frodon on 2007-07-19
As i explained several post ago this error don't prevent the good work of the FTP server, it is just that you don't use ipv6.
I think you will find some useful posts in this thread and for sure in the forum if you want to remove this error message.

---

### Post by r0ot5 on 2007-07-19
ok and if I want to use the GUI, how can I start it, because now I want to create users?

sorry for all this questions, i'm very new to ubuntu.


thx again,

---

### Post by guilly on 2007-07-19
> **r0ot5 said:**
> ok and if I want to use the GUI, how can I start it, because now I want to create users?

sorry for all this questions, i'm very new to ubuntu.


thx again,

sudo apt-get install gproftp 

this will install the GUI version of proftp. However if you just want to simply add another user i don't think you need the GUI to do so....

if you want to learn Ubuntu, command line is the only way to go in my opinion anwyays, i'm still very unfamiliar with linux but i can say one thing i've learned alot more by punching out commands as i would of done by doing everythign thru GUI

---

### Post by trenog on 2007-07-21
Alright, so using the default port 21 I was able to get to work the FTP server once I opened up the port in my DI-604 Virtual Server list (public 21, private 21, ip - internal IP). But unfortunately(?) I have to use my external IP to connect.

Is using my external IP and port 21 to login a bad thing?

Does anyone else who has a DI-604 know how to use a different port and set up proftpd to work with the DI-604 settings?

Thanks

---

### Post by anpk on 2007-07-22
> **frodon said:**
> Why such a need ? It makes your computer more secure to require root rights to run or modify services

Basic security. Any service running as root is really dangerous. Its best to run it as a user with specific access rights so that critical access permissions are always followed.

---

### Post by frodon on 2007-07-22
> **anpk said:**
> Basic security. Any service running as root is really dangerous. Its best to run it as a user with specific access rights so that critical access permissions are always followed.Yes but anyone would be able to gain access easily and configure the FTP server to share other directories.
Anyway i think it would be good to ask this question in the proftpd forum, im' curious to know what the proftpd experts think of the question :
[http://forums.proftpd.org/smf/](http://forums.proftpd.org/smf/)

If you have any interesting feedback about this in the proftpd forum please share it with us :)

---

### Post by Poka64 on 2007-07-22
this password 530 error, how do I fix it?
No, I can't use the GUI way because this is on a server without GUI, I'm just using SSH + terminal to update things.

I'm adding the users with aliases and everything. The thing is that when I installed the server I added users without any problems, but if I try to change password or add users now it doesn't work :(

---

### Post by frodon on 2007-07-22
> **Poka64 said:**
> this password 530 error, how do I fix it?
No, I can't use the GUI way because this is on a server without GUI, I'm just using SSH + terminal to update things.

I'm adding the users with aliases and everything. The thing is that when I installed the server I added users without any problems, but if I try to change password or add users now it doesn't work :(THe 530 error is in general a problem with the user creation and especially the password so in general resetting the password solve the problem.

It is stange that you can't change the password however, it is not supposed to behave like that.

---

### Post by Poka64 on 2007-07-22
yes, It's very strange, can't add user or change password for current users.

The thing is, the user can login through bash but they get dissconnected because I set /bin/false

---

### Post by Elv13 on 2007-07-22
noob questions: how can i access to my FTP

when i write [ftp://69.70.242.31/](ftp://69.70.242.31/) or [ftp://69.70.242.31/FTP-shared/](ftp://69.70.242.31/FTP-shared/) i get unable to connect to host

i did open a port on my router like that:
[http://img381.imageshack.us/img381/1421/captureqw9.png](http://img381.imageshack.us/img381/1421/captureqw9.png)

but i dont know if it is the right way, my local ip is 192.168.1.100 and my ip is 69.70.242.31 according to my router

ProFTP is running

EDIT: I can connect locally (127.0.0.1)

---

### Post by dannyboy79 on 2007-07-23
either you have a firewall rules on your Ubuntu machine, check with 
sudo iptables -L
or you didn't forward the correct port? Plus if you have a router/firewall between you and the cable modem or dls connection, you need to be using passive mode I believe. There's always issues for newbies trying to get it to work thru a hardware firewall. You need to read the links at the bottom of the guide about opening up all ports from 1025 to 65535 or whatever it says, then adding a passive line within proftpd.conf. Just read the bottom of the guide where it talks about being behind a router. The problem is that the connection is done thru port 21 but I think the data connection is done on ports above 1024 so it doesn't work because you don't have those higher ports open (something along those lines). Also, I just ran nmap on your external ip address and it does NOT show port 21 open just so you know so you can't have forwarded port 21 on your router to your internal ip's address port 21. Also, what does this command return:
netstat -pant
you should be able to see something like 0.0.0.0:21, that means that your ftp server is listening on the external interface and not just to localhost. Good luck.

---

### Post by anpk on 2007-07-23
> **frodon said:**
> Yes but anyone would be able to gain access easily and configure the FTP server to share other directories.
Anyway i think it would be good to ask this question in the proftpd forum, im' curious to know what the proftpd experts think of the question :
[http://forums.proftpd.org/smf/](http://forums.proftpd.org/smf/)

If you have any interesting feedback about this in the proftpd forum please share it with us :)

Thanks frodon for your prompt replies :). I've posted to the proftpd forums, hopefully someone else has tried it before :guitar:

---

### Post by salehid on 2007-07-23
Thanks everybody for this valuable information ....

---

### Post by JOWIROMA on 2007-07-24
Hey guys...
I have been trying to get this to work but the only thing that I get when I give the start comand is a "FAIL"

This is my conf file:

[HTML]
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias jose userftp

ServerName			"Monark"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port				1980

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
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

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
[/HTML]

And this is when I run -td5:

[HTML]monark@monark-desktop:/home/FTP-shared$ sudo proftpd -td5
Checking syntax of configuration file
 - mod_ctrls/0.9.4: binding ctrls socket to '/var/run/proftpd/proftpd.sock'
 - parsing '/etc/proftpd/proftpd.conf' configuration
 - <Directory /home/FTP-shared>: deferring resolution of path
 - <Directory /home/FTP-shared/download/*>: deferring resolution of path
 - <Directory /home/FTP-shared/upload/>: deferring resolution of path
 - IPv6 getaddrinfo 'monark-desktop' error: No address associated with hostname
monark-desktop - 
monark-desktop - Config for Monark:
monark-desktop - /home/FTP-shared/upload/
monark-desktop -  Limit
monark-desktop -   AllowAll
monark-desktop -  Limit
monark-desktop -   DenyAll
monark-desktop -  Umask
monark-desktop -  DirUmask
monark-desktop -  AllowOverwrite
monark-desktop -  AuthAliasOnly
monark-desktop -  UserAlias
monark-desktop -  ShowSymlinks
monark-desktop -  DisplayFirstChdir
monark-desktop -  ListOptions
monark-desktop -  RequireValidShell
monark-desktop -  RootLogin
monark-desktop -  TransferLog
monark-desktop -  UseFtpUsers
monark-desktop -  AllowStoreRestart
monark-desktop -  MaxClients
monark-desktop -  MaxClientsPerHost
monark-desktop -  MaxClientsPerUser
monark-desktop -  MaxHostsPerUser
monark-desktop -  AccessGrantMsg
monark-desktop - /home/FTP-shared/download/*
monark-desktop -  Limit
monark-desktop -   DenyAll
monark-desktop -  Umask
monark-desktop -  DirUmask
monark-desktop -  AllowOverwrite
monark-desktop -  AuthAliasOnly
monark-desktop -  UserAlias
monark-desktop -  ShowSymlinks
monark-desktop -  DisplayFirstChdir
monark-desktop -  ListOptions
monark-desktop -  RequireValidShell
monark-desktop -  RootLogin
monark-desktop -  TransferLog
monark-desktop -  UseFtpUsers
monark-desktop -  AllowStoreRestart
monark-desktop -  MaxClients
monark-desktop -  MaxClientsPerHost
monark-desktop -  MaxClientsPerUser
monark-desktop -  MaxHostsPerUser
monark-desktop -  AccessGrantMsg
monark-desktop - /home/FTP-shared
monark-desktop -  Limit
monark-desktop -   DenyAll
monark-desktop -  Umask
monark-desktop -  DirUmask
monark-desktop -  AllowOverwrite
monark-desktop -  AuthAliasOnly
monark-desktop -  UserAlias
monark-desktop -  ShowSymlinks
monark-desktop -  DisplayFirstChdir
monark-desktop -  ListOptions
monark-desktop -  RequireValidShell
monark-desktop -  RootLogin
monark-desktop -  TransferLog
monark-desktop -  UseFtpUsers
monark-desktop -  AllowStoreRestart
monark-desktop -  MaxClients
monark-desktop -  MaxClientsPerHost
monark-desktop -  MaxClientsPerUser
monark-desktop -  MaxHostsPerUser
monark-desktop -  AccessGrantMsg
monark-desktop - Limit
monark-desktop -  AllowUser
monark-desktop -  DenyAll
monark-desktop - AllowOverwrite
monark-desktop - AuthAliasOnly
monark-desktop - UserAlias
monark-desktop - DeferWelcome
monark-desktop - DefaultServer
monark-desktop - ShowSymlinks
monark-desktop - TimeoutNoTransfer
monark-desktop - TimeoutStalled
monark-desktop - TimeoutIdle
monark-desktop - DisplayFirstChdir
monark-desktop - ListOptions
monark-desktop - RequireValidShell
monark-desktop - TimeoutLogin
monark-desktop - RootLogin
monark-desktop - ExtendedLog
monark-desktop - TransferLog
monark-desktop - UseFtpUsers
monark-desktop - AllowStoreRestart
monark-desktop - UserID
monark-desktop - UserName
monark-desktop - GroupID
monark-desktop - GroupName
monark-desktop - Umask
monark-desktop - DirUmask
monark-desktop - MaxClients
monark-desktop - MaxClientsPerHost
monark-desktop - MaxClientsPerUser
monark-desktop - MaxHostsPerUser
monark-desktop - AccessGrantMsg
monark-desktop - ServerIdent
monark-desktop - DefaultRoot
monark-desktop - DefaultRoot
monark-desktop - MaxLoginAttempts
monark-desktop - mod_ctrls/0.9.4: binding ctrls socket to '/var/run/proftpd/proftpd.sock'
Syntax check complete.
monark@monark-desktop:/home/FTP-shared$ 

[/HTML]

Please any help I would like to get this to work so I will not get frustated...  	](*,) 	](*,)  	](*,)

---

### Post by frodon on 2007-07-25
As i repeat every 3 or 4 posts (read the thread you will see more than 10 posts about this)  the Ipv6 error don't prevent the FTP server to work so you can just ignore it, if you can't ignore this error message do as following :
[http://ubuntuforums.org/showthread.php?p=2295568#post2295568](http://ubuntuforums.org/showthread.php?p=2295568#post2295568)

---

### Post by JOWIROMA on 2007-07-25
[HTML]As i repeat every 3 or 4 posts (read the thread you will see more than 10 posts about this) the Ipv6 error don't prevent the FTP server to work so you can just ignore it, if you can't ignore this error message do as following :
http://ubuntuforums.org/showthread.p...68#post2295568
[/HTML]

Yeah frodon I already ignored the error but what would be the cause of my problem???
when I put the start comand it just goes:
[HTML]
starting proftpd server                                                             [FAIL]
[/HTML]

Could you be so kind to show me a way to find a debug log for this or is there anything else I would have to look into??

please help me.....

thanks anyways for replying.

What a better place to look for help that your "UBUNTU FORUMS"

---

### Post by frodon on 2007-07-25
If your server fail to start then you may have another problem, anyway first fix your Ipv6 hostname so we will be sure that it don't create problems on your computer.
As i said you can ignore the Ipv6 error **except** if you are using Ipv6 adresses.

So do as explained here (replace bohdan-ubuntu by monark-desktop in your case):
[http://ubuntuforums.org/showpost.php?p=2295568&postcount=2](http://ubuntuforums.org/showpost.php?p=2295568&postcount=2)

Then restart your server and post back here the errors log if your server still fail to start.

---

### Post by JOWIROMA on 2007-07-25
[HTML]
If your server fail to start then you may have another problem, anyway first fix your Ipv6 hostname so we will be sure that it don't create problems on your computer.
As i said you can ignore the Ipv6 error except if you are using Ipv6 adresses.

So do as explained here (replace bohdan-ubuntu by monark-desktop in your case):
http://ubuntuforums.org/showpost.php...68&postcount=2

Then restart your server and post back here the errors log if your server still fail to start.
[/HTML]

Pardon my ignorance but where would i find the "error  log"
or I just have to run -5td again and just see what it says???

Thank you so much fur your help... and time... and patience...

---

### Post by frodon on 2007-07-25
Just restart the server using a terminal, error messages should appear in the terminal if the server fail to start.
You can also run the proftpd -td5 command, it will give some more infos.

---

### Post by JOWIROMA on 2007-07-25
[HTML]
Just restart the server using a terminal, error messages should appear in the terminal if the server fail to start.
You can also run the proftpd -td5 command, it will give some more infos.
[/HTML]

Thanks man,  I will try that tonight and I will post back to let you know how it goes....

---

### Post by JOWIROMA on 2007-07-26
Hey Frodon!!!!

I got it working, I got rid of the ipv6 error and and my problem was that I did not read carefully your How To,
I just went through the tutorial again just to check that all the settings where fine and I found that I created the  ftp user wrong and then when I got it running I got the 530 error but it is fixed now, and I even got it working with my  dyndns.org account. Now my cousin in San Francisco can get into my FTP server and browse through the folders and I will have look into the encrypting (is this really necesary?) . Man this is great... The only thing now is to see if I can get it to upload faster, my cousin was getting a download rate of 40 kb/s, it would be great if there would be a way to speed this up a bit...
If anybody  knows llet me know...

Thanks anyway...

(I will post back if I got any problem)

---

### Post by frodon on 2007-07-26
The upload speed depend of your connection, by default the FTP server will use all the upload bandwidth availables o maybe it is just that your connection can't do more.
About encryption, it's easy to set up and it increases the security because the basic FTP protocol transfer the username and password in plain text so if someone is listening your traffic he will get easily your FTP password and username.
When you set encryption all is encrypted including your username and password so can live in peace :)

---

### Post by dannyboy79 on 2007-07-26
> **JOWIROMA said:**
> Hey Frodon!!!!

I got it working, I got rid of the ipv6 error and and my problem was that I did not read carefully your How To,
I just went through the tutorial again just to check that all the settings where fine and I found that I created the  ftp user wrong and then when I got it running I got the 530 error but it is fixed now, and I even got it working with my  dyndns.org account. Now my cousin in San Francisco can get into my FTP server and browse through the folders and I will have look into the encrypting (is this really necesary?) . Man this is great... The only thing now is to see if I can get it to upload faster, my cousin was getting a download rate of 40 kb/s, it would be great if there would be a way to speed this up a bit...
If anybody  knows llet me know...

Thanks anyway...

(I will post back if I got any problem)

I never could get the SSL encryption working. What I do is just use ssh tunnels for all my over the internet stuff like vnc and mythweb access. and for transferring files, I use WinSCP, it's free for Windows. You can also use any ftp client that has SFTP option. It'll use the ssh encrypted connection to transfer files back and forth. BUT, keep in mind that your ssh server makes your friend have access to your ENTIRE computer so hopefully he knows not to just move or delete stuff. There may even be a way to "block" off certain folder but most likely not. You'll need ssh server running on your Ubuntu machine, I set mine up with RSA Keys, then I just open port 22 on my router, then I use any ssh client to connect.

As far as how fast your friend downloads, I have that same problem! I have great download but horrible upload, so he is restricted to how ever fast your upload connection is. I am guessing it's around 320 Kilobits per second which equates to the 40 kilobytes that your friend is downloading at. Remember, kilobit is NOT the same as what files are stored in, Kilobytes or megabytes. The conversion is APPROX .125 to 1.

---

### Post by JOWIROMA on 2007-07-27
Well, I will try to put the encrypting and I will post back to tell how it goes...

---

### Post by frodon on 2007-07-27
BTW dannyboy79, what was your problem with TLS encryption, the certificate creation ?

---

### Post by anpk on 2007-07-28
> **frodon said:**
> Yes but anyone would be able to gain access easily and configure the FTP server to share other directories.
Anyway i think it would be good to ask this question in the proftpd forum, im' curious to know what the proftpd experts think of the question :
[http://forums.proftpd.org/smf/](http://forums.proftpd.org/smf/)

If you have any interesting feedback about this in the proftpd forum please share it with us :)

For others who want to run proftpd as non root, please follow this article

[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Nonroot.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Nonroot.html)

Mods: This might be a good link to be put on its own as a sticky post for others who might find it useful. I'll leave it to your best judgement. :)

---

### Post by dannyboy79 on 2007-07-31
> **frodon said:**
> BTW dannyboy79, what was your problem with TLS encryption, the certificate creation ?

it was with actually connecting. The cert creation worked fine. I could never connect with Filezilla, FireFTP, or Gftp. I even tried every different version of encryption I could like TLSv1 SSL or whatever all the options are within each of the clients. I also could never tell if my server was actually using the TLS enryption.

---

### Post by frodon on 2007-07-31
I'm wondering how many users had this problem as well, i suppose you tried the FTPES option in filezilla (this is the option i use on my box) ...
Did you find any other users on the proftpd forum with this issue ?

---

### Post by dannyboy79 on 2007-07-31
> **frodon said:**
> I'm wondering how many users had this problem as well, i suppose you tried the FTPES option in filezilla (this is the option i use on my box) ...
Did you find any other users on the proftpd forum with this issue ?

this was long ago, I spent days reviewing the proftpd forums trying to get my proftpd server working thru inited (or whatever the opposite of standalone was) along with encryption but never got it to work. No, I don't believe I did try that within Filezilla. I don't even use an ftp server anymore on my Ubuntu box. Since I am the only person wtih access I don't need to struggle with the setting up users, folders, access etc etc.

 I just setup ssh with public/private key pairs with passphrase and use winscp from windows and or gftp (sftp) thru Ubuntu and instead of only having access to certain folders, I have access to everything. I would like to learn how to do it properly but right now I just don't have the time, I have plenty going on.

---

### Post by SeanCM on 2007-07-31
I have read through the very helpful guide and the posts and have managed to get my FTP server up and running.  I have run into a bit of a problem though that I am hoping someone may be able to help me with.

Here is the situation, I also have a Ubuntu server running with proftpd running.  I have a NAS that has a few directories that get backed up from my various other systems.    I have mounted a few of these to directories within my ftp-shared directory.  The problem is that there are a couple directories that I don't want to be available via ftp.  To complicate things more these directories have spaces.

So I tried this:
```

<Directory /home/ftp-shared/backup/My Photos/>
        <Limit ALL>
                Deny ALL
        </Limit>
</Directory>

```

and this:
```

<Directory /home/ftp-shared/backup/My\ Photos/>
        <Limit ALL>
                Deny ALL
        </Limit>
</Directory>

```
But neither work.  Any ideas?  Thank you in advance.

---

### Post by dannyboy79 on 2007-07-31
> **SeanCM said:**
> I have read through the very helpful guide and the posts and have managed to get my FTP server up and running.  I have run into a bit of a problem though that I am hoping someone may be able to help me with.

Here is the situation, I also have a Ubuntu server running with proftpd running.  I have a NAS that has a few directories that get backed up from my various other systems.    I have mounted a few of these to directories within my ftp-shared directory.  The problem is that there are a couple directories that I don't want to be available via ftp.  To complicate things more these directories have spaces.

So I tried this:
```

<Directory /home/ftp-shared/backup/My Photos/>
        <Limit ALL>
                Deny ALL
        </Limit>
</Directory>

```

and this:
```

<Directory /home/ftp-shared/backup/My\ Photos/>
        <Limit ALL>
                Deny ALL
        </Limit>
</Directory>

```
But neither work.  Any ideas?  Thank you in advance.

the folders are still showing up you're saying? also, you didn't specify the commands that are deny all for since you're using the limit option? try the hidenoaccess, you can read all about configuring proftpd here: [http://chronos.cs.msu.su/proftpd/Configuration.html#HideNoAccess](http://chronos.cs.msu.su/proftpd/Configuration.html#HideNoAccess)

---

### Post by SeanCM on 2007-08-01
Thanks for the suggestion I tried this:

```

<Directory /home/ftp-shared/backup/My\ Photos/>
   Umask 022 022
   AllowOverwrite off
   HideNoAccess on
   <Limit ALL>
      Order Deny,Allow
      Deny ALL
   </Limit>
   <Limit CWD>
      Order Deny,Allow
      Deny ALL
   </Limit>
</Directory>

```

Yet I can still see the directory when I ftp in.  I have tried lots of other combinations too.  Then I got the idea of trying with a directory that did not have a space in it and sure enough it worked.  So the problem is the space.  Is there anyway to get proftpd to take that into account?  I can not easily remove the space as it would mess other things up.

Thank you in advance.

Sean

---

### Post by dannyboy79 on 2007-08-01
I found this within 1 minute via google. 

If the name of the directory contains spaces, you should enclose the entire directory name in quotations, e.g.: 

  <Directory "/path/to/My Directory">

---

### Post by SeanCM on 2007-08-01
Thanks for the info.  On my search through google I only got 5 hits back and none of them were about what I wanted.  I guess I was too specific in my search.  Thanks again.

Sean

---

### Post by Leonin on 2007-08-05
I have done what it says in the How to, but I cant login. The client tells me that I'm using either a wrong password or login. What should I do?

---

### Post by frodon on 2007-08-05
You should try to reset your password and see if you stil have the problem.

---

### Post by Leonin on 2007-08-05
I still have the problem after a  password restart.

---

### Post by frodon on 2007-08-05
ok, could you post your config file and the error log you get with your FTP client, don't forget to give some details about your configuration (firewall, router , ..).

---

### Post by shortbus on 2007-08-16
I'm getting the 530 error and I can't figure out what the issue is... below is my .conf file:

# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
UserAlias  Nick userftp
AuthAliasOnly                   on

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6                         off

ServerName                      "Debian"
ServerType                      standalone
DeferWelcome                    off

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    on

TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                     "-l"

DenyFilter                      \*.*/

# Use this to jail all users in their homes
# DefaultRoot                   ~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShells            off

# Port 21 is the standard FTP port.
Port                            21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress             1.2.3.4

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

# Set the user and group that the server normally runs at.
User                            proftpd
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022  022

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
AllowUser Nick
AllowUser guest
DenyALL
</Limit>

<Directory /home/FTP-shared>
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

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on

       <Limit ALL>
                Order Allow,Deny
                AllowUser guest
                AllowUser Nick
                Deny ALL
        </Limit>

        <Limit READ RMD DELE>
        DenyAll
        </Limit>

        <Limit STOR CWD MKD>
        AllowAll
        </Limit>
</Directory>

# Normally, we want files to be overwriteable.
AllowOverwrite                  on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd              off

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile                   off

# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
#<IfModule mod_sql.c>
# SQLBackend                    mysql
#</IfModule>

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_tls.c>
TLSEngine off
</IfModule>

<IfModule mod_quota.c>
QuotaEngine on
</IfModule>

<IfModule mod_ratio.c>
Ratios on
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default.
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        on
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine on
</IfModule>

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User                                ftp
#   Group                               nogroup

#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias                   anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser on ftp
#   DirFakeGroup on ftp
#
#   RequireValidShell           off
#
#   # Limit the maximum number of anonymous logins
#   MaxClients                  10
#
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin                        welcome.msg
#   DisplayFirstChdir           .message
#
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
#
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask                           022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
#
# </Anonymous>

I can log in with the user 'Nick' but not guest. Any help would be greatly appreciated.

---

### Post by frodon on 2007-08-16
Your user guest has no alias name and the option "AuthAliasOnly on" allows only alias name to login, so either create an alias name for the user guest or disable the "AuthAliasOnly" option.

Otherwise try to reset the password, it often solve this problem :
```
sudo passwd guest
```

---

### Post by shortbus on 2007-08-16
call me a n00b, because i call myself that and I am, but is all i have to is like below?:

# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
UserAlias  Nick userftp
UserAlias guest userftp1
AuthAliasOnly                   on

or is there another way i have to set the alias?

i have done
sudo passwd guest

and reset the password but am still getting the 530 error.

---

### Post by frodon on 2007-08-16
Ok wait a minute, what are the names of the users you created and what login name do you use in your ftp client ?

---

### Post by shortbus on 2007-08-16
I've tried using both userftp1 and guest, still no go.

---

### Post by Jordanwb on 2007-08-23
I get an error saying that it can't find the proftpd package.

---

### Post by frodon on 2007-08-23
> **shortbus said:**
> I've tried using both userftp1 and guest, still no go.Please answer my question first, i think your problem is just that in your LOGIN section you are allowing the alias name instead of the real user name.

> **Jordanwb said:**
> I get an error saying that it can't find the proftpd package.This is more likely to be a repository problem, could you tell us which version of ubuntu you are using ?

---

### Post by Jordanwb on 2007-08-23
I'm using 6.06

---

### Post by Weavz on 2007-08-27
I'm getting the same problem with 6.06 when I try and get the gproftpd.  I'm also a noobie :(

---

### Post by spartan777 on 2007-08-28
nvm

---

### Post by spartan777 on 2007-08-31
how do I know whether I'm connected to my ftp server via ssl or not? it seems to me that I'm not, even though I've set

```
    TLSRequired on
```

also, when i'm setting up my ssl certificates, on the last step, i get this:

```
1 out of 1 certificate requests certified, commit? [y/n]y
Write out database with 1 new entries
Data Base Updated
CA verifying: server.crt <-> CA cert
server.crt: /C=US/ST=Illinois/O=Internet Widgits Pty Ltd/CN=Calvin/emailAddress=MY_EMAIL_ADDR@gmail.com
error 18 at 0 depth lookup:self signed certificate
/C=US/ST=Illinois/O=Internet Widgits Pty Ltd/CN=Calvin/emailAddress=MY_EMAIL_ADDR@gmail.com
error 7 at 0 depth lookup:certificate signature failure
22235:error:0407006A:rsa routines:RSA_padding_check_PKCS1_type_1:block type is not 01:rsa_pk1.c:100:
22235:error:04067072:rsa routines:RSA_EAY_PUBLIC_DECRYPT:padding check failed:rsa_eay.c:708:
22235:error:0D0C5006:asn1 encoding routines:ASN1_item_verify:EVP lib:a_verify.c:168:
calvin@calvin-desktop:/etc/ftpcert$ 

```

---

### Post by xaco1234 on 2007-08-31
it tells me that i got a iv6 problem when i try to start it, how do i turn of ipv6? ipw4 shoud do in a lan right

---

### Post by new486dx on 2007-09-02
hi frodon, i have just copied and pasted your howto but i still have an error. i've used mssm's proftd.conf because i am also using a router and a dynamic ip address from the dsl provider.(im using d-link 524 router) can u pls tell what im am going to do to fix
 these errors?  

* Stopping ftp server proftpd                                           [ ok ]
 * Starting ftp server proftpd  - IPv4 getaddrinfo 'abelardoom.dyndns.org' error: Name or service nome t known
 - Fatal: MasqueradeAddress: unable to resolve "abelardoom.dyndns.org" on line 1 81 of '/etc/proftpd/proftpd.conf'

---

### Post by Jordanwb on 2007-09-02
sudo nano /etc/proftpd/proftpd.conf

There's a line near the beginning where we can enable or disable IPv6, set it to off. That should fix it.

---

### Post by new486dx on 2007-09-03
>sudo nano /etc/proftpd/proftpd.conf

>There's a line near the beginning where we can enable or disable >Pv6, set it to off. That should fix it.


is that ok to delete that line? i mean is it not needed by the program?
im sorry im just realy noob to linux.. thanks for the reply.

---

### Post by Tensk8 on 2007-09-03
Hi, 

I try to set up the TFT server but I received this message.

ZZZ@ZZZ-laptop:~$ sudo /etc/init.d/proftpd restart
 * Stopping ftp server proftpd                                           [ OK ] 
 * Starting ftp server proftpd                                                   - IPv6 getaddrinfo 'andre-laptop' error: No address associated with hostname
                                                                         [ OK ]
ZZZ@ZZZ-laptop:~$ sudo /etc/init.d/proftpd start
 * Starting ftp server proftpd                                           [fail] 
ZZZ@ZZZ-laptop:~$ 



Help me please

---

### Post by frodon on 2007-09-04
> **new486dx said:**
> >sudo nano /etc/proftpd/proftpd.conf

>There's a line near the beginning where we can enable or disable >Pv6, set it to off. That should fix it.


is that ok to delete that line? i mean is it not needed by the program?
im sorry im just realy noob to linux.. thanks for the reply.If your ISP don't use IPV6 adresses then for sure you can disable IPV6 support,

---

### Post by new486dx on 2007-09-04
hi frodon, i have just copied and pasted your howto but i still have an error. i've used mssm's proftd.conf because i am also using a router and a dynamic ip address from the dsl provider.(im using d-link 524 router) can u pls tell what im am going to do to fix
these errors?

im done with the ipv6 thing:)

* Stopping ftp server proftpd [ ok ]
* Starting ftp server proftd - IPv4 getaddrinfo 'abelardoom.dyndns.org' error: Name or service nome t known
- Fatal: MasqueradeAddress: unable to resolve "abelardoom.dyndns.org" on line 1 81 of '/etc/proftpd/proftpd.con

---

### Post by frodon on 2007-09-04
Hi new486dx,

I saw your post but unfortunately i am not really able to help you as i don't use a router and never used it so users who followed the guide and use a router are more likely to provide you the solution to your problem than me.
Don't forget also to search and maybe post your question on the proftpd forum, it is a really good place to learn more about proftpd and its configuration :
[http://forums.proftpd.org/smf/](http://forums.proftpd.org/smf/)

However my guess is that your problem is more related to your domain name and the way you set it rather than your proftpd.conf file. Are you able to ping successfully your domain name (abelardoom.dyndns.org) ?

---

### Post by new486dx on 2007-09-05
it works fine now, but i can't ftp from the outside.

---

### Post by Jeinhor on 2007-09-09
Thanks for a great howto!
Worked like a charm here.

---

### Post by kenmiles on 2007-09-15
I have got proftp setup but I can't seem to login to my site. This is the output that I am getting, can anyone see where I am going wrong please. Is it looking for mu ubuntu login and password or the one set up in proftp as neither work.

/home/FTP-shared-->ftp kmiles.co.uk
Connected to kmiles.co.uk.
220 Inactivity timer = 120 seconds. Use 'site idle <secs>' to change.
Name (kmiles.co.uk:kenneth): ken
331  Password required.
Password:
530 Permission denied
Login failed.

Thanks in advance.
Regards, Kenneth.

---

### Post by elmagique on 2007-09-18
hi, i've got a problem, i tried to mount my usb drive to the folder "mount"

I have changed my config file 

(added
<Directory> /media/disk>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	AllowAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
)

but i still get a 550 error when trying to get into my mounted directory (if nothing's mounted in there I can get in the folder)

Help please!

---

### Post by elmagique on 2007-09-19
ok, i found out how to fix it, it didn't have to do anything with the ftp, just user restrictions

---

### Post by klwh on 2007-09-20
Hello. I use ubuntu feisty fawn of server edition.
I installed and set up the proftpd just you guys introduced above. But I don't think that mine is working correctly. 
I can access to my server by typing [ftp://localhost](ftp://localhost) on the server machine which runs proftpd. But when I try to access from other computer which runs opensuse, I can't login. The other computer returns the message "Could not find server". I don't see why it happens. Could you help me?

---

### Post by frodon on 2007-09-20
> **klwh said:**
> Hello. I use ubuntu feisty fawn of server edition.
I installed and set up the proftpd just you guys introduced above. But I don't think that mine is working correctly. 
I can access to my server by typing [ftp://localhost](ftp://localhost) on the server machine which runs proftpd. But when I try to access from other computer which runs opensuse, I can't login. The other computer returns the message "Could not find server". I don't see why it happens. Could you help me?For sure a firewall/router issue, check the configuration of both computers and verify that you have all the needed ports opened.

---

### Post by klwh on 2007-09-20
Thank you. I just discovered that if I type IP address in, I can access to the server. For instance, like 192.168.xx.x, then I can access to the server but if I type the name of computer which you need to type in at the instllation, it does not work.Could you give me some advices?

---

### Post by frodon on 2007-09-20
> **klwh said:**
> Thank you. I just discovered that if I type IP address in, I can access to the server. For instance, like 192.168.xx.x, then I can access to the server but if I type the name of computer which you need to type in at the instllation, it does not work.Could you give me some advices?I always use the IP to connect to my server so if you don't have a domain name for your computer i'm not sure if it is possible to reach your computer with something else than the IP.

---

### Post by kalipopo on 2007-09-21
BTW thanks for the how to.  iam still having a little bit of an issue.  i have my ftp server currently setup behind a router and have already configured the masquerade address and passive port.  the issue iam running into is that from withing my network i can access the ftp site fine, but when i try to connect from outside my network i keep getting a permission denied error stating that i dont have enough permissions.  the wierd part is that it does connect and authenticates but gives me the permission denied error (550 i think).  i have attached my config file for review to see if iam missin anything. thanks

---

### Post by jrjvai on 2007-09-22
Hi!

I tried to follow the guide to the letter but still managed to get in trouble. Running proftpd gives me
```

vainio@Kepuinen:/$ sudo /etc/init.d/proftpd start
 * Starting ftp server proftpd                                                   - IPv4 getaddrinfo 'Kepuinen' error: No address associated with hostname
 - warning: unable to determine IP address of 'Kepuinen'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
                                                                         [fail]

```
I copied the file directly from the guide. What did I do wrong?

---

### Post by frodon on 2007-09-22
There's a problem in your proftpd.conf file surely with the server name, could post your config file here so we can review it ?

---

### Post by kalipopo on 2007-09-24
> **kalipopo said:**
> BTW thanks for the how to.  iam still having a little bit of an issue.  i have my ftp server currently setup behind a router and have already configured the masquerade address and passive port.  the issue iam running into is that from withing my network i can access the ftp site fine, but when i try to connect from outside my network i keep getting a permission denied error stating that i dont have enough permissions.  the wierd part is that it does connect and authenticates but gives me the permission denied error (550 i think).  i have attached my config file for review to see if iam missin anything. thanks

Any ideas as to what may be the issue here.  All help will be greatly appreciated

---

### Post by pofigster on 2007-09-30
Frodon!  This is a very clear how-to!  However, I have run into a  few problems...  First, I'm not behind a firewall or anything like that - I host a number of websites off this computer and I have no problem accessing them.  I do get the IPv6 notice when I start proFTPd - can't seem to fix it, so, here's my conf file, maybe you could provide some idea on how to get my address [ftp://statmajor.info](ftp://statmajor.info) (which I own) to point to this.  I did all the SSL/TSL stuff too, to make it more secure.  Thanks!  

> # To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias sauron userftp

ServerName			"ftp://statmajor.info"
ServerType standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		on

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "Welcome Mr. Ewing"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
     #DefaultRoot /home/mark/Documents/School

# Lock all the users in home directory, ***** really important *****
     #DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp,
AllowUser mark
</Limit>

<Directory /home/mark/Documents/School/*>
Umask 022 022
AllowOverwrite on
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD CWD MKD READ>
	AllowAll
	</Limit>
</Directory>

<IfModule mod_tls.c>
    TLSEngine on
    TLSLog /var/ftpd/tls.log
    TLSProtocol TLSv1

    # Are clients required to use FTP over TLS when talking to this server?
    TLSRequired on

    # Server's certificate
    TLSRSACertificateFile /etc/ftpcert/server.crt
    TLSRSACertificateKeyFile /etc/ftpcert/server.key

    # CA the server trusts
    TLSCACertificateFile /etc/ftpcert/ca.crt

    # Authenticate clients that want to use FTP over TLS?
    TLSVerifyClient on
</IfModule>
<Global>
DeferWelcome on
MaxClients 5
ServerIdent on "Welcome Mr. Ewing"
AllowOverwrite on
RequireValidShell on
</Global>


---

### Post by frodon on 2007-10-01
Hi pofigster,

What is your problem exactly, the IPv6 error message or the access to your FTP server ?

For all you need is to make your domain name [ftp://statmajor.info](ftp://statmajor.info) to point to the IP of your computer but if you already have some websites on this computer i guess it is already the case so you should already be able to access your FTP server using this domain name.

About your config file not much to say, it is not mandatory to put your domain name as server name because from my understanding the ServerName command is just to set a simple name for the server, i have another remark about your user called "mark" because you chose to allow this user to access to the server (AllowUser mark command) however like recommended in my guide the server allows only connection with alias names (AuthAliasOnly on command) so you would need to create an alias name for your user mark and login your server with this alias name.

---

### Post by pofigster on 2007-10-01
Ok, I think the real problem is the IPv6 thing then, associating an address with my computer's name.  I noticed in this thread that there's supposed to be something in the config file to edit?  I couldn't find it.  

Anyway, I've got [ftp://statmajor.info](ftp://statmajor.info) pointing at this computer, but the login for userftp doesn't work (keeps asking for the password), I assumed the two were interconnected.

---

### Post by frodon on 2007-10-01
About the IPv6 error try this :
[http://ubuntuforums.org/showthread.php?p=2295568#post2295568](http://ubuntuforums.org/showthread.php?p=2295568#post2295568)

---

### Post by pofigster on 2007-10-01
frodon, that last post fixed the IPv6 warnings that were showing up.  Still, though, everytime I try and login I get a 530 error.  I double checked, I don't require a valid shell in the conf file, and the user I created on this computer, userftp, has the right folder as home and the right /bin/false shell.  Any idea on why I simply cannot login?

---

### Post by frodon on 2007-10-01
Check the system rights of your /home/mark/Documents/School/ directory, it is an upload directory so the rights of this folder must be 777. Then if you still get this error try to set another password for the user several time and verify that you are using the alias name to login the server.

BTW i saw one huge security mistake in your config file, please uncomment the line "DefaultRoot /home/mark/Documents/School" it is what prevent a user from going outside your /home/mark/Documents/School directory so this is really important.

---

### Post by pofigster on 2007-10-01
It works!  Thanks for your help, I wasn't using the alias name to login...stoopid me.

---

### Post by frodon on 2007-10-01
Great, enjoy your encrypted FTP server ;)

---

### Post by pofigster on 2007-10-01
Frodon - it's me again :( Ok, so the unencrypted FTP server is working great - but when I use Webmin to update the configuration file to include the TLS code (After getting it all set up like in the how-to) this is what I get:
> Failed to apply FTP configuration :

Checking syntax of configuration file

Please provide passphrases for these encrypted certificate keys:
RSA key for the 127.0.1.1#21 ([ftp://statmajor.info](ftp://statmajor.info)) server: 

Passphrases do not match.  Please try again.
RSA key for the 127.0.1.1#21 ([ftp://statmajor.info](ftp://statmajor.info)) server: 

Passphrases do not match.  Please try again.
RSA key for the 127.0.1.1#21 ([ftp://statmajor.info](ftp://statmajor.info)) server: 

Passphrases do not match.  Please try again.

Wrong passphrase for this key.  Please try again.
RSA key for the 127.0.1.1#21 ([ftp://statmajor.info](ftp://statmajor.info)) server: 

Passphrases do not match.  Please try again.
RSA key for the 127.0.1.1#21 ([ftp://statmajor.info](ftp://statmajor.info)) server: 

Passphrases do not match.  Please try again.
RSA key for the 127.0.1.1#21 ([ftp://statmajor.info](ftp://statmajor.info)) server: 

Passphrases do not match.  Please try again.

Wrong passphrase for this key.  Please try again.
RSA key for the 127.0.1.1#21 ([ftp://statmajor.info](ftp://statmajor.info)) server: 

Passphrases do not match.  Please try again.
RSA key for the 127.0.1.1#21 ([ftp://statmajor.info](ftp://statmajor.info)) server: 

Passphrases do not match.  Please try again.
RSA key for the 127.0.1.1#21 ([ftp://statmajor.info](ftp://statmajor.info)) server: 

Passphrases do not match.  Please try again.

Wrong passphrase for this key.  Please try again.
mark-desktop - mod_tls/2.1.1: unable to use RSA certificate key in '/etc/ftpcert/server.key', exiting


How do I get the passphrases to match?  I used the same passwords for both of the certificates, not the same as my login password though.  Any help would be great!  Thanks!

---

### Post by frodon on 2007-10-01
If you are not sure of your certificate password maybe it will be faster to recreate your certificate. 
I never used webmin so i can't really help you about webmin related stuff.

---

### Post by floz23 on 2007-10-01
Greetings everyone,

Decent how-to.  I should note however, I needed to use the LATEST version of firezilla, in order to use the TLS compression.  You may want to note that in the how-to.

But I have a question about a module that is not in the packaged version in the repos.  I would really like to use the mod_shaper module, in order to limit the overall bandwidth usage of my crummy adsl connection.  I looked at the "TransferRate RETR" control, but I realized that thats for a per connection basis, not to powerful at all.

Since I'm almost a total Linux n00b, could you give me an idea of how to recompile proftpd with the included mod_shaper module?

Much thanks to everyone, including the how-to's author!

-Adam

---

### Post by frodon on 2007-10-02
First are you sure it is not included ? Not loaded not necessarily mean not present. The list a modules you are loading when running proftpd is set in the /etc/proftpd/modules.conf file.
The command "proftpd -l" should return you the module list.

In addition TransferRate is not on a "connection basis" but on a command basis, for the moment i don't see the need to restrict the bandwidth other than for the RETR and STOR commands and maybe also the LIST command, other commands not being bandwidth eaters.

Will add a note about filezilla, i use the feisty repository version which Support for TLS encryption but i guess previous version don't, thanks for your feedback :)

---

### Post by floz23 on 2007-10-02
Thanks frodon,

Yes, I'm pretty sure its not included.  I check in the /usr/lib/proftpd directory, and its not listed.  

Well, the reason why I want the mod_shaper is because i want to be able to set an upstream transfer rate in total.  So if I have 60kb/s to spare, i want that entire 60kb/s to be allocated, no matter how many transfers are running.

As for the firezilla, I was referring to the windows version.  I can't speak for the linux version because I don't use it, but version2 of firezilla just wouldn't connect to my TLS encrypted server!  I was going nuts trying to figure it out, thinking it was a problem with the server configuration.  Then I just decided to try the latest version (version3) of firezilla; it worked perfectly.

-Adam


> **frodon said:**
> First are you sure it is not included ? Not loaded not necessarily mean not present. The list a modules you are loading when running proftpd is set in the /etc/proftpd/modules.conf file.
The command "proftpd -l" should return you the module list.

In addition TransferRate is not on a "connection basis" but on a command basis, for the moment i don't see the need to restrict the bandwidth other than for the RETR and STOR commands and maybe also the LIST command, other commands not being bandwidth eaters.

Will add a note about filezilla, i use the feisty repository version which Support for TLS encryption but i guess previous version don't, thanks for your feedback :)

---

### Post by wilberfan on 2007-10-19
I've only been using Ubuntu for a year or so, and I've never tried setting up an FTP server, so this thread is invaluable...

I've stumbled through the HowTo, understanding probably half of it :) 

I'm behind a router, and have tried to make those allowances in the proftpd.conf file.

When I try and connect using fireftp in Firefox, I can't connect, and don't get any useful information about why:   "Unable to make a connection.  Please try again."

Is there a log file, or...?

Where on Earth do I start looking to see what the problem is?   :confused:

---

### Post by appzattak on 2007-10-24
thanks for the great tut. I have one prob though. I cannot get the proftptools to work, I think I did the .bashrc correct, can you let me know. when I run ProftpTools from the terminal it does nothing.

Here is my .bashrc file.

> ProftpTools_dir=/home/steve/downloads/ProftpTools-v1.0.2
export ProftpTools_dir
fi

---

### Post by appzattak on 2007-10-24
nevermind, I fixed it, I had to remove that fi

---

### Post by j3n0vacHiLd on 2007-10-24
Hey, great tutorial there I got through it just find I'm just running into a problem now I can't seem to solve.

I have this ftp server setup just for local file transfer between windows/linux mostly. I can connect to the server, browse the files, etc.. but If I want to create a new folder or upload a file I get a "550: Permission Denied" error.. I have chmod my ftp folder to 777 and still unsure what the problem is. Anyone know what might be wrong?

```

ftp> put /home/daniel/hmm.txt
local: /home/daniel/hmm.txt remote: /home/daniel/hmm.txt
200 PORT command successful
550 /home/daniel/hmm.txt: Permission denied
ftp>

```

I have copy/paste the .conf file from the tutorial so unless there is a mistake I think that is fine.

Any help is appreciated, thanks!


EDIT: I just chmod all directories to 777 including the ftp directory and its working fine now :/ .. I just had to specify a remote path because it was trying to upload to the wrong place.

---

### Post by b3dm4n on 2007-10-25
Hi.
I'm a newbee to Linux world and Ubuntu is the first distro I tried. I want to make an ftp server, so I followed your steps literally for a start.
I manage to get almost everything going, but 1 thing I couldn't get it done is to make a symlink in the ftp-share directory to be accessable by the ftp user. 

I want an ftpuser to access directory /home/ftp-share, /site/www, and /store/client
I already make *ln -s* command to make shortcut to www and client directory in ftp-share folder, but ftpuser cannot see them, what should I do?

---

### Post by frodon on 2007-10-25
> **b3dm4n said:**
> Hi.
I'm a newbee to Linux world and Ubuntu is the first distro I tried. I want to make an ftp server, so I followed your steps literally for a start.
I manage to get almost everything going, but 1 thing I couldn't get it done is to make a symlink in the ftp-share directory to be accessable by the ftp user. 

I want an ftpuser to access directory /home/ftp-share, /site/www, and /store/client
I already make *ln -s* command to make shortcut to www and client directory in ftp-share folder, but ftpuser cannot see them, what should I do?All is explained in the tutorial, symlink are not allowed with the config i provided as they decrease seriously the security of your FTP server.
This is the exact purpose of the section Misc > Useful tricks to let you mount where you need the directory you wish to share.

---

### Post by djrakun on 2007-11-14
i can set permissions for users to upload to a particular directory but any subfolders in that directory do not inherit the permissions of the parent folder. Do i have to add something to my conf file for this to happen?

Thanks

---

### Post by ronaldor9 on 2007-11-18
hey what do i put here

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup


what should i put in user and group thanks

---

### Post by ronaldor9 on 2007-11-18
oh and as well whenever i start or restart i get these messeages
when i try to start it simply fails ?? and when i restart it gives me this messege

 - IPv6 getaddrinfo 'server.gateway.2wire.net' error: No address associated with hostname

---

### Post by frodon on 2007-11-18
> **ronaldor9 said:**
> hey what do i put here

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup


what should i put in user and group thanksYou can leave it like that, that doesn't really matter for a standard use.

> **ronaldor9 said:**
> oh and as well whenever i start or restart i get these messeages
when i try to start it simply fails ?? and when i restart it gives me this messege

 - IPv6 getaddrinfo 'server.gateway.2wire.net' error: No address associated with hostnameThis is explained everywhere in this thread.

---

### Post by ronaldor9 on 2007-11-18
ok thanks great guide i was a little spectical but i just ignored it and it worked

exept that when i login to the ftp i have acces to a different users home folder not the FTP-shared 

??? how can i change this

thanks

---

### Post by frodon on 2007-11-19
The ftp server will login in the user home directory so if you didn't set the FTP-shared directory as home directory for your ftp user then it is normal.

---

### Post by Kulgan on 2007-11-19
I'm having some problems with this after upgrading to Gutsy - when starting the server without a wired network connection:
```
/etc/init.d/proftpd start
 * Starting ftp server proftpd                                                   
 - IPv4 getaddrinfo 'manetheren' error: No address associated with hostname
 - warning: unable to determine IP address of 'manetheren'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
```

With no or wireless connection, the server refuses to start. There is nothing in the conf that suggests anything about "manetheren" - which is indeed my hostname. 

Completely removing and re-installing proftpd doesn't seem to do the trick...
any ideas?

-K

---

### Post by frodon on 2007-11-19
Your problem is not related to proftpd but to your network configuration, post here your /etc/hosts file, your problem is here.

---

### Post by Kulgan on 2007-11-19
```
cat /etc/hosts
127.0.0.1 manetheren.lan
127.0.1.1 manetheren.lan manetheren.lan

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

remove ".lan" from the first entry?

---

### Post by frodon on 2007-11-19
I guess your host name may be different when you use your wireless connection, check this and if it is really the case just add your wireless specific host name to the file.

---

### Post by Kulgan on 2007-11-19
Hehe, that did it :D

When I had wireless, it asked for "manetheren", when I was using a wired connection, it was going on about "manetheren.lan". Added "manetheren" to hosts - it now works. 

Thanks!
-K

---

### Post by frodon on 2007-11-19
Glad you got it working :)

---

### Post by ronaldor9 on 2007-11-19
wondering userftp is a group

so what does it mean if i add a user such as my default ubuntu user to that group 
what effects will this have on my ftp?

btw great guide still working on setting it up heheeh
edit 
do i type the computers private ip      like this  [ftp://192](ftp://192)................ ect
to view my ftp beacuse its not working for somereason ? i did exactly as u did even copied teh config but im not getting login page i also forwareded the ports

---

### Post by frodon on 2007-11-20
If you put your normal user to the userftp group (which have no sense IMO) this won't do anything as you normal user isn't allowed to login your ftp server except obviously if you add a line to allow it.

To access your ftp server i strongly advice you to use a FTP client (like fireftp, or filezilla) otherwise you have to use a browser which handle correctly ftp identification and you have to know how to enter your ftp address.

In a web browser the address to type is something like :
[ftp://*your_alias_name](ftp://*your_alias_name)*@192.***.***.***:*your_ftp_port_number*

---

### Post by ronaldor9 on 2007-11-20
ic well now i  get the login page exept im using my alias and im using the password set for the group userftp and it still dont work gives me 530 error

---

### Post by frodon on 2007-11-20
You will see a bunch of posts in this thread about the 530 error, it means that there's a configuration problem.
That might come from the password, wrong username, wrong rights on your FTP shared directories, so check thoroughly your config and perform a search in this thread using "530 error" as key word, you will find a lot of useful informations.

---

### Post by ronaldor9 on 2007-11-20
ok ill do that  but quick qestion before i do that ubuntu doesent let me login with userftp and the password
? is this a possible problem

---

### Post by frodon on 2007-11-20
That may be indeed, try to regenerate the password using "sudo passwd userftp".

---

### Post by quickshot89 on 2007-11-20
sorry to bump , but im stuck

ive installed the server, configured it as best i can, all i did was change the server name to discovery

and when i come to access the server, it says unable to find it :S im using [ftp://my](ftp://my) ip address:21

is that correct?

my servers ip is 192.168.1.11 if it helps

edit: cant even view the server on the internal network too

edit 2: getting a 503 error saying incorrect details

so im really :S now

btw, the attached file had to have .doc added on the end, i coppied everything from the gedit cmd and saved it in a new file in the same program, hope it helps

edit 3: can view it internally, however the whole HDD is viewable, i only want certain folders to be viewable, not my whole HDD, also, still cant get external address to view it, even thou ive added the ports in my router :(

---

### Post by frodon on 2007-11-21
Sorry but you didn't followed the tutorial, there's no LIMIT LOGIN section, no directory section and even worst no DefaultRoot in your proftpd.conf command which is the reason nothing limits users from browsing your whole computer so your FTP server is really not safe for the moment.
So please read thoroughly the config file provided in the tutorial and take example on it.

As for you problem where you can't connect from the outside it is related to your network configuration first thing to check is your firewall and configure your rooter if you have one.

---

### Post by quickshot89 on 2007-11-21
got it working now, i used the script on the 1st page and changed the details to suit my folders etc

---

### Post by ronaldor9 on 2007-11-21
nice     is it safe to delet the folder named ftp with a file named welcome in it in /home


so whats the point of the download folder is i cant put stoff on it from my linux box or any other pc

also where can i find more information for like making the ftp-shared directory give more privilages such as move files from the folder to the desktop delet files from there and everythign related to that

thanks alot for helping a noob just got litnux little over 2 weeks ago and i already got ftp with public domain thank you very much and ur detication

also quick qestion when creating a new user do i have to add him from the users and groups and then add them to group user ftp?

can u explain  i have authoraliaseonly set to off

but then i have         john1 userftp set for my alias
john1 is also another acount i have  that i use for all my ubuntu stuff
and i am able to login with john1 with authalias only to off     but im not able to sign in with userftp
i played around with this forl ike 2 hours i could not figure it out please help

as well i set my upload lilmit like this

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit ALL>
	AllowAll
	</Limit>
</Directory>
but it doesent let me delet stuff of of it ??????

---

### Post by frodon on 2007-11-22
Not sure to understand your first question, the point of the download directory is to be able to download only otherwise you have the upload directory. If you wish you can make only upload directories.

The following section is what restrict the access of your upload directory :
[CODE]        <Limit READ RMD DELE>
      	DenyAll
    	</Limit>[/CODE
All the commands yo can use with the LIMIT command are detailed there :
http://www.proftpd.org/localsite/Userguide/linked/config_ref_Limit.html

About the new user creation my first question is why do need more than one ?
Otherwise to answer your question no it is not enough, you also have to set the home directory of this user to /home/FTP-shared, create an alias name for it in the proftpd.conf and allow this user in the LIMIT LOGIN section of your proftpd.conf file. But again i don't see the point creating more users except if you want to give them access to different directories.

Disabling authoraliaseonly makes you unprotected against telnet accesses, congrats you decreased the security of your server ;) (just joking :P)

For the rest you should really read the proftpd user guide and watch others configurations on the proftpd forum, links below :
http://www.proftpd.org/localsite/Userguide/linked/userguide.html
http://forums.proftpd.org/smf/

---

### Post by ronaldor9 on 2007-11-22
i see
but the wierd thing is that i can only set my alias to john if i set it to john1 and restart my server it wont let me login with it only with john i dono why this happens

i also tired with the limits to set it to all like this
<Limit ALL>
AllowAll
</Limit>
and it woulditn let me delete or upload no clue why can u just tell me how set the limits for a folder that can delet acces make folders upload transfer and everything ?? ive treid for soo long so frustrating

---

### Post by frodon on 2007-11-23
It don't work like that, an alias name is just an alias so you choose any name (choosing the name of an existing user as alias name is a bad idea IMO) you want as long as the user you set an alias name on is allowed in the proftpd.conf. About the LIMIT section you have to tell explicitly what command to allow like that for instance :
```
<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD RMD DELE>
      	AllowAll
    	</Limit>
</Directory>
```

---

### Post by chronographer on 2007-11-28
Hello, I have set up ftp, as outlined, gained access from local network, but have reached a stumbling block from remote site. Following is output from filezilla on a windows box.
> Status:    Connecting to ***********:1980 ...
Status:    Connected with ************:1980. Waiting for welcome message...
Response:    220 you're at home
Command:    USER ******************
Response:    331 Password required for **********.
Command:    PASS ******
Response:    230 welcome !!!
Command:    SYST
Response:    215 UNIX Type: L8
Command:    FEAT
Response:    211-Features:
Response:     MDTM
Response:     REST STREAM
Response:     SIZE
Response:    211 End
Status:    Connected
Status:    Retrieving directory listing...
Command:    PWD
Response:    257 "/" is current directory.
Command:    TYPE A
Response:    200 Type set to A
Command:    PASV
Response:    227 Entering Passive Mode (192,168,2,9,191,119).
Command:    LIST
Error:    Transfer channel can't be opened. Reason: A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.
Error:    Could not retrieve directory listing
Command:    REST 0
Error:    Timeout detected!


Can anyone help explain the reason here? it obviously connects and then timesout or something!

Alex

---

### Post by frodon on 2007-11-28
I think your firewall or your router is blocking something it shouldn't block. Do you get the same result if you put your FTP server on port 21 ?

---

### Post by Tavathlon on 2007-11-28
Hello!

I have a problem with proftpd that I have not experienced before - I used proftpd a couple of years ago, and it worked fine. Trying it in Gutsy now, however, seems to be problematic.

I have tried some different configurations, based on the default config-file modified by myself, and based on the config file that is suggested in the first post of this thread. They provide me with different problems, though:

After implementing the suggestion in the first post, I just simply can't login, neither with the actual username or the alias username. The only error message I get is that the password is incorrect. (And I have tried to remove the aliasing, same thing happens.)

With the default file, modified by myself, I get logged on to the system, but I cannot retrieve the list from the server - nothing happens here at all, until the timeout sets in and I get thrown out. (I'm not sure, but I think I also tried aliases here, but it gave the same result as without aliases.)
I have tried the things about PassivePorts and MasqueradeAddress, but without any luck. However, I am able to connect internally from the LAN with this configuration!

I have a D-link DI-604, if that rings any bell for anyone (which I did not have in the old days, btw).

Last comment: I also tried pure-ftp, but I was never able to connect on that one either. However, I _was_ able to connect internally within the LAN, just like default in proftpd...

It could be the same problem as chronographer above, but I am using port 21. Moreover, I guess it's the router, but what can I do about it? I'm not really used to routers...  (and the router does not explain why I can't login at all when I use the config file as suggested in post #1)

---

### Post by chronographer on 2007-11-30
HEllo

I tried using port 21, with a mac from a remote location and was able to see my directories but not transfer to and from them. I will try using filezilla when I next go to my brother-in-law's house and post the results.

So if I want to use port 1980 I guess I need to ensure forwarding is right in my router and firewall for 1980. I will report back, Thanks.

---

### Post by AmidamaruFlame on 2007-11-30
Hello. First off I would like to say thanks for all the information you provide in this thread. Very helpful. Secondly, I have 2 issues that I am trying to resolve:

First, I was wondering if it was possible to limit the space a user has. I have created a FTP server that myself and my friends can use, but I would like to allocate a specific amount (say 1GB or so) to each user, so I won't lose all my space.

Secondly, I tried to install ProftpTools, but every time I type ProftpTools into terminal, it asks me for my password, then stops. I don't think it's actually doing anything. :/

Thanks in advance!

---

### Post by frodon on 2007-11-30
1) you have the mod_quotas module for this purpose, here is the documentation i found about it :
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Quotas.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Quotas.html)

2) ProftpTools is a script i wrote to ease common Proftpd admin operations, it is not made to work with TLS encription so if you are using it it may not work.
If you want to see some error log in your terminal and know what the problem is run directly the proftpd_tools.bash script.

---

### Post by AmidamaruFlame on 2007-11-30
Thank you for the help.

My 2nd problem was fixed, but I am still having trouble with the module....
[QUOTE="Terminal"]
server@Room212:/usr/lib/proftpd$ ./configure --with-modules=mod_quotatab:mod_quotatab_file
bash: ./configure: No such file or directory[/QUOTE]

is the terminal error I receive. I have little linux knowledge, and the documentation you sent me to was just too confusing for me to understand...

---

### Post by frodon on 2007-11-30
Why are you compiling proftpd ?

I think the version in the repositories already have the mod_quotas module compiled, if it is not loaded by default add the module name in /etc/proftpd/modules.conf and make sure to have the following line at the beginning of your proftpd.conf file :
```
Include /etc/proftpd/modules.conf
```

---

### Post by AmidamaruFlame on 2007-11-30
thank you for the help. I only have one more question....

using the quotatab module, I receive an error caused by the "QuotaOptions ScanOnLogin" directive. This occurs when i go to apply my changes. I receive this error:
>  - Fatal: unknown configuration directive 'QuotaOptions' on line 49 of '/etc/proftpd/proftpd.conf'

any help?

---

### Post by frodon on 2007-11-30
Unfortunately i have no knowledge about this module, i'm on the same level than you about this, however don't forget to post your question on the proftpd forum if you don't get the help you need here :
[http://forums.proftpd.org/smf/](http://forums.proftpd.org/smf/)

---

### Post by Tavathlon on 2007-11-30
No ideas on how I should do with my router problem? To be precise, these are the last messages that get sent after it first connects to the server, using gftp (filezilla gives more or less exactly the same result):

Loading directory listing / from server (LC_TIME=en_US.UTF-8)
PASV

227 Entering Passive Mode (192,168,0,42,141,110).
Cannot create a data connection: No route to host
Disconnecting from site 83.233.18.110

So I thought that perhaps if I tell the server which ports it may allow for PASV, and then open those ports, it would work - but the server doesn't seem to bother about what I type in after PassivePorts in .conf

Or is the numbers 141 and 110 above not ports? I don't have a clue..
Is there perhaps some way in which I can prevent the server from going into passive mode? How, in that case - have not been able to find anything, so far..  (must admit I haven't been looking too much either, have a deadline coming up..  >.< )

(btw, when I was using proftpd a couple of years ago, I think it was frodon who helped me get everything working back then..  =P  )

---

### Post by frodon on 2007-11-30
Here is what says the proftpd userguide about it :
[http://www.proftpd.org/localsite/Userguide/linked/config_ref_PassivePorts.html](http://www.proftpd.org/localsite/Userguide/linked/config_ref_PassivePorts.html)

If you perform a search in this thread you will find many useful informations like in this post which i linke in first page :
[http://ubuntuforums.org/showpost.php?p=680702&postcount=81](http://ubuntuforums.org/showpost.php?p=680702&postcount=81)

Sorry but i think i can't help you more, i don't use a rooter so my knowledge about this kind of stuff is really limited.

---

### Post by chatuu on 2007-12-01
look... i just started with gproftpd.....   

i created the users and stuff.... i am able to connect in this account....


but when i creat another user... this user come back with 530 erro in 2 lines 

530-Unable to set anonymus privigeles
530 Login error


what can be it ?

i want to have different accounts with diferentes floders for each one  
my onw floder i am able to make, and with that username i can set anyfloder to see, but if i try creat another user, this user is unable to see anythigs and came back with erros 530...

any ideias ??

my proftpd.conf 

```
 ServerType standalone
DefaultServer on
Umask 022
ServerName "0.0.0.0"
ServerIdent on "My FTPD"
ServerAdmin Admin@this.domain.topdomain
IdentLookups off
UseReverseDNS off
Port 2121
PassivePorts 2000 2100
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 10
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 100
TransferRate STOR 40
TransferRate STOU 40
TransferRate APPE 40
SystemLog /var/log/secure
RequireValidShell off
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_homedir_path /var/ftp
#gp_html_path /var/www/html/ftp.htm
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
</IfModule>
<IfModule mod_ratio.c>
Ratios off
SaveRatios off
RatioFile "/restricted/proftpd_ratios"
RatioTempFile "/restricted/proftpd_ratios_temp"
CwdRatioMsg "Please upload first!"
FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
LeechRatioMsg "Your ratio is unlimited."
</IfModule>
<Limit LOGIN>
  AllowUser arquivos
  AllowUser chatuu
  DenyALL
</Limit>

<Anonymous /home/chatuu/Desktop/ArquivosFTP>
User arquivos
Group ftp
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>

<Anonymous /home/chatuu/Desktop/Henrique>
User chatuu
Group ftp
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
<Directory /home/chatuu/Desktop/ArquivosFTP>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  MKD XMKD SITE_MKDIR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit RNFR RNTO  DELE  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Directory>
</Anonymous> 
```

---

### Post by Bionic Apple on 2007-12-05
I may be an idiot, but here it goes:  I try to setup an FTP server with gproftpd, but I can't get the hostname/ip right.  What should I put there?  I have tried my local address, remote address, and my computer's linux "nickname".  Also, if I am behind a firewall (in a linksys router) on a local network with several computers, what else should I configure?  Should I leave the NAT setting alone?  And if I should change the NAT setting, what do I put there?  Sorry if it is very simple, but I can't figure it out no matter how much searches I do.

---

### Post by pj12345 on 2007-12-06
Hey, I've looked throughout this tutorial on how to set up my ftp. I copied the proftpd.conf file in the first post and editted a few lines around for myself however, I'm still getting that 530 error message when i try to log-in. On my network if my ip is xxx.xxx.xxx.2 I can log in to it from my own computer, but can't from someone elses. Any ideas?

---

### Post by frodon on 2007-12-06
@pj12345, this is a firewall/router problem, check your firewall and router settings and be sure that you are not blocking somethings which shouldn't be blocked.

If you have a router this may help :
[http://ubuntuforums.org/showpost.php?p=680702&postcount=81](http://ubuntuforums.org/showpost.php?p=680702&postcount=81)

---

### Post by dirtNap on 2007-12-09
Hi Frodon, great guide and keep up the great work! :)  My problem is that proftpd times out at exactly ten minutes every time I connect and transfer files on a remote computer.  I use filezilla and fireftp (both work great with TLS by the way) to transfer the files. I have set up anonymous accounts as well as using my shell via TLS.  If you need my proftpd.conf file I will shoot it in another reply. Thanks for all of your help!

---

### Post by flasher702 on 2007-12-16
after doing: 
sudo apt-get install proftpd gproftpd
it asks me to insert some cd and press enter. I don't even have a cd-rom drive installed in this system. So I do:
sudo mount -o loop -t iso9660 ubuntu-7.10-desktop-i386.iso /cdrom
which works perfectly until I hit enter and then it unmounts the image and asks me to insert the CD again.

How do I make it install without a cd-rom drive? Why is it even asking me for a CD in the first place? That's lame. I would totally complain at the right people if I knew who that was. Not sure if it's entirely ubuntu's fault or if it's the proftpd.

I guess I will install a CD-ROM drive but any help is greatly appreciated in case I run into this kind of problem again in the future or if anyone knows which group is responsible.

Update: I mounted the .iso of the alternate install cd (the one I used to install with) and it worked. This reminds me a bit too much of MS windows... :(

---

### Post by frodon on 2007-12-17
This is not really a proftpd question. Just remove your cd link in your /etc/apt/source.list file or clicking repositories in synaptic, if you have an internet connection you don't need the cd.

---

### Post by dlhilario on 2007-12-17
sudo apt-get install proftpd

I tried the line shown above to install the proftpd and is not working. what does this like do and what is actually istalling and in what directory. Can I do manually isntead. 

I was able to do everything else without a problem except for this line **sudo apt-get install proftpd** does anyone have any idea. I notice that I don't have any file in the **init.d **directory.

I will really appreciate your kind help.

---

### Post by frodon on 2007-12-17
Enable all the ubuntu repositories first (universe and multiverse), you will find many threads about it.

---

### Post by general.chaos on 2007-12-19
Hi, Im getting the following error:

 - notice: unable to bind to Unix domain socket at '/var/run/proftpd/test.sock': No such file or directory
 - notice: unable to listen to local socket: No such file or directory
 - error: /media/Storage is a world writeable directory
 - Fatal: SystemLog: you are attempting to log to a world writeable directory on line 32 of '/etc/proftpd/proftpd.conf'


I'm using the GUI method... I've also noticed that I cant set the default home directory to anything other than the default.   Whenever I do and hit apply it just changes itself back.

Please help..

---

### Post by Lemmings74 on 2007-12-20
Hi  I am a newbie to Ubuntu but ave managed to setup proftpd to allow 1 user ftp access to one of my home directories.

This user can download files, ammend them and then upload files with no problem, however if they upload a new file, then the user rights are set to -------w-. I have set the Umask to 022 as default, and to 775 in the <directory> section of the script... any ideas??

(hope this makes sense!

---

### Post by frodon on 2007-12-20
You should also set the same umask for your system, you can add this in your .basrc file  present in your home directory.

---

### Post by Lemmings74 on 2007-12-20
not sure what you mean! I dont have .basrc in that directory :S

---

### Post by frodon on 2007-12-20
You have one in your own home directory. I mean that you should set the same umask for your whole ubuntu system as proftpd never overwrite your ubuntu system settings. That's why i told you that you should set a "umask 022" for your ubuntu system too.
You can type the command in the terminal directly or put it in your .bashrc file if you wish this command to be executed automatically each time you open your terminal.

Not sure it will solve your problem but it is something you should try first.

---

### Post by mcleod9 on 2007-12-23
Wow, there is a ton of useful information and generous people here. Thanks very much! 

I couldn't find the answer to this issue:

I seem to connect to my server from outside my LAN, but this error comes up:

Command:	CWD /home/FTP-shared/
Response:	550 /home/FTP-shared/: No such file or directory
Error:	Failed to retrieve directory listing

the /home/FTP-shared directory does exist though...any thoughts?

---

### Post by frodon on 2007-12-23
My guess is rights problems on this folder (if you didn't modify the original configuration i gave in first post, if you did please post it).
At the is step you are connected to your server which mean that you global config is ok however the user loged in don't have enough rights to see the directories there.

Check the rights of you FTP directories, it should be 777 for upload directories and 755 for download directories, 755 is enough for the FTP-shared directory.

---

### Post by mcleod9 on 2007-12-24
@Frodon -- Thanks for your thoughts. I have slightly modified the original proftpd config file, maingly to change the port and UserAlias. 

The permissions are ok on my installation, so I'm not sure what's wrong. 

Here's the config file. Thanks again!

#
# Includes required DSO modules. This is mandatory in proftpd 1.3
#
Include	/etc/proftpd/modules.conf
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

ServerName			"mouse"
ServerType			standalone
DeferWelcome			on

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer		600
TimeoutStalled			100
TimeoutIdle			2200
TimeoutLogin			20

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

DefaultRoot 			/home/FTP-shared
#IdentLookups off
#ServerIdent off

# Lock all the users in home directory, ***** really important *****
# DefaultRoot ~

RootLogin			off

MaxLoginAttempts		3

UseFtpUsers 			off

DenyFilter			\*.*/

# Allow to restart a download
AllowStoreRestart		on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd		off

# Uncomment this if you would use TLS module:
TLSEngine 			on

# Uncomment this if you would use quota module:
#Quotas				on

# Uncomment this if you would use ratio module:
#Ratios				on

# Port 21 is the standard FTP port.
Port				2121

MaxInstances 			8

MasqueradeAddress xxxxxxx.org
MasqueradeAddress xx.xxx.xxx175
PassivePorts 60000 60100

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome to the SFTP Server"

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
# MaxInstances			10

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on
AuthAliasOnly			on

UserAlias share userftp

# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default. 
#DelayEngine 			off

<Directory /home/FTP-shared>
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

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

<IfModule mod_tls.c>
    TLSEngine on
    TLSLog /var/ftpd/tls.log
    TLSProtocol TLSv1

    # Are clients required to use FTP over TLS when talking to this server?
    TLSRequired on

    # Server's certificate
    TLSRSACertificateFile /etc/ftpcert/server.crt
    TLSRSACertificateKeyFile /etc/ftpcert/server.key

    # CA the server trusts
    TLSCACertificateFile /etc/ftpcert/ca.crt

    # Authenticate clients that want to use FTP over TLS?
    TLSVerifyClient off
</IfModule>

---

### Post by frodon on 2007-12-24
Hum, you broke all the security of the server commenting the defaultroot line, users will be able to browse your whole computer if you comment this line, i prefer to warn you that it is in general a really unsafe configuration.

Except this your config file looks ok so i would check the directory permissions on your system.

---

### Post by mcleod9 on 2007-12-24
> **frodon said:**
> Hum, you broke all the security of the server commenting the defaultroot line, users will be able to browse your whole computer if you comment this line, i prefer to warn you that it is in general a really unsafe configuration.

Except this your config file looks ok so i would check the directory permissions on your system.
Thanks Frodon. The permissions are all as you have written, but it still doesn't work :\ Same message about the directory not existing.

---

### Post by bionnaki on 2007-12-25
so, how do people connect to the ftp server if you do not have a static ip?

---

### Post by frodon on 2007-12-25
In this case use a domain name, dyndns can provide you one for free. To keep your domain name up to date you can use ddclient or the script made for dyndns, o think i have left some links about this in first post.

@mcleod9, it is strange, i don't see for the moment what could be wrong. I still think there's somewhere a too restrictive permission which block the directory listing. I will try to review this again as soon as i get some free time this week.

---

### Post by krelkor on 2008-01-04
thanks for the tutorial, but i have a little problem

im trying to setup an FTP server so that i can backup a log from my router

i can login fine, but i cannot upload anything to the directory /data/FTP/ nor can i see anything within that directory from within my ftp client on another machine

here is the output form ls -la 

drwxrwxrwx  2 wrt54g wrt54g       4096 2008-01-04 17:22 FTP



and here is my .conf

AllowOverwrite on
AuthAliasOnly off

UseReverseDNS                   off
IdentLookups                    off

# Choose here the user alias you want !!!!
UserAlias steve wrt54g

ServerName                      "server"
ServerType                      standalone
DeferWelcome                    off

MultilineRFC2228 on
DefaultServer                   on
ShowSymlinks                    off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

#DisplayFirstChdir               .message
ListOptions                     "-l"

RequireValidShell               off

TimeoutLogin 20

RootLogin                       off

# It's better for debug to create log files ;-)
ExtendedLog                     /var/log/ftp.log
TransferLog                     /var/log/xferlog
SystemLog                       /var/log/syslog.log

#DenyFilter                     \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart               on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port                            21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022     022

PersistentPasswd                off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
#AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
#ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /data/FTP

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser wrt54g
DenyALL
</Limit>

<Directory /data/FTP>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

---

### Post by krelkor on 2008-01-05
bump! :)

---

### Post by krelkor on 2008-01-05
im so close to being done! does anyone see a problem with my above posted proftpd.conf, or is the problem somewhere else?

---

### Post by frodon on 2008-01-06
As usual check your directory rights (they must be 777), your directory in your proftpd.conf is defined as a download directory so you won't be able to upload in it according to your proftpd.conf. You should take example on the upload directory in the guide on first post to create your directory configuration in your proftpd.conf file.

And please don't bump the thread like that (3 times a day).

---

### Post by dbsoundman on 2008-01-09
I'm considering setting up all this, but I have a question. I went ahead and created a userftp profile, and made the default directory for that user FTP-Shared, as the tutorial says. However, I'm not quite sure if this will do what I want it to do. What I would like to set up is two profiles: one for myself only, to remotely access all my documents on this computer remotely, and another for whatever guest user to read and write to whatever folder I choose. As it is now, I can't write to the FTP-Shared folder without sudo permissions, meaning that if I wanted to put a file in there for someone else to download through the guest account I would have to do it via command line. I would like to be able to do it so that I don't have to do that...so I could just drag-and-drop. I guess I'm looking to set up a slightly different menu structure in terms of the FTP access. I guess I primarily don't understand why creating a user profile with a separate home directory is advantageous...why couldn't I just create a subdirectory of my home folder (/home/dan) that the guest could read and write to, and make it so that that is the only one that they can access? If this makes any sense...what should I do?

Thanks,
Dan

---

### Post by frodon on 2008-01-10
> **dbsoundman said:**
>  As it is now, I can't write to the FTP-Shared folder without sudo permissions, meaning that if I wanted to put a file in there for someone else to download through the guest account I would have to do it via command line. I would like to be able to do it so that I don't have to do that...so I could just drag-and-drop. This is a write management question, my guide is more designed to mount the directory you want in the download and upload directory rathan using them directly. Anyway you can just set you as owner of these directories :
```
sudo chown -R *your_username* /home/FTP-shared
```
> **dbsoundman said:**
> I guess I'm looking to set up a slightly different menu structure in terms of the FTP access. I guess I primarily don't understand why creating a user profile with a separate home directory is advantageous...Security of course. Doing this you're using a user with no rights on your system, no valid shell and locked in his home directory. You're somwhat creating a secure area for your FTP server.
> **dbsoundman said:**
> why couldn't I just create a subdirectory of my home folder (/home/dan) that the guest could read and write to, and make it so that that is the only one that they can access? If this makes any sense...what should I do?It is possible but way less secure as you will have to use your personal account as login and thus give your personal password to your guest. Encryption is inescapable IMO if you do such thing.

---

### Post by dbsoundman on 2008-01-10
I figured it was about security. I was thinking I would use the FTPS setup instead of regular FTP, but I will look into how I could keep it all to that one directory like you say. I figure you probably know better than I do in this area...:). I will have to do some research on FTPS just to see how it can be accessed from, say, other computers without Filezilla or something like that, but I'm pretty sure I can google up that info. I will also need to see if I can even get this to work in the first place, because last time I never quite got it working outside of my home network due to weirdness with the software on my home network router and the DSL modem. Hopefully I'll get that all figured out though...I'm sure if I have problems I will post back!

-Dan

---

### Post by frodon on 2008-01-10
The basic FTPS setting i propose in my guide will establish encrypted connection with users using a FTP client configured to use TLS encription but will also allow normal (unencrypted) connection for those who don't have a FTP client.

This is handled by the "TLSRequired off" parameter, i think this setting will give you the flexibility you are looking for.

---

### Post by Bionic Apple on 2008-01-11
Can someone tell me the basics to create a working FTP server using Gproftpd?  The first post didn't help me at all.  I have been messing around with the settings, yet nothing will work.

---

### Post by dbsoundman on 2008-01-12
All right, I got everything set up, and the server runs. I have a problem though. When I start it up, here is what it says:
```
:~$ sudo /etc/init.d/proftpd start
 * Starting ftp server proftpd                                                  blackdiamond - 127.0.1.1:1980 masquerading as 76.1.0.243
                                                                         [ OK ]
```
However, the 127.0.1.1 address is not the correct IP address. According to my router, it should be 192.168.1.xxx. I'm pretty sure this computer is 192.168.1.102. How can I fix this? I did assign a static IP to this computer already, the 192 address. As far as I know that's the only issue, because I can't even access the server from within my home network, so at least for now I'm not having router/modem issues, though I'm almost positive I will when I get to that point...

Thanks,
Dan

---

### Post by Palcrypt on 2008-01-12
Ok, so I got the ftp set up to work. I decided I wanted the ftps to work. The problem is that I am behind a firewall on my router. proftpd's website says this is because with the encrypted credentials the router gets confused with somethings. It says the solution is to set: 

TLSRequired auth+data
instead of
TLSRequired off

The problem is when I do that (or just set it to auth) when I restart the server I get this error: 
- Fatal: TLSRequired: bad parameter on line 95 of '/etc/proftpd/proftpd.conf'

auth and auth+data are supposed to be valid parameters for TLSRequired. Any suggestions?

---

### Post by dbsoundman on 2008-01-12
I figured out how to fix my wrong-IP address problem by modifying the "hosts" settings in the network connection manager thing. I can now at least detect the FTP server with my laptop, but I get a 530 login error when I try to login. I was going to research this to see if I could figure it out but if anyone has suggestions that would be great as well...

-Dan

---

### Post by Palcrypt on 2008-01-12
> **Palcrypt said:**
> Ok, so I got the ftp set up to work. I decided I wanted the ftps to work. The problem is that I am behind a firewall on my router. proftpd's website says this is because with the encrypted credentials the router gets confused with somethings. It says the solution is to set: 

TLSRequired auth+data
instead of
TLSRequired off

The problem is when I do that (or just set it to auth) when I restart the server I get this error: 
- Fatal: TLSRequired: bad parameter on line 95 of '/etc/proftpd/proftpd.conf'

auth and auth+data are supposed to be valid parameters for TLSRequired. Any suggestions?

just noticed that the problem is that apt-get of proftpd only installs version 1.3.0 and the auth+data parameters are only handled in 1.3.1. I tried doing a manual build and install of the newest version, but still had issues. Looks like no SSL for me. :(

---

### Post by dbsoundman on 2008-01-12
Ok, I'm still having 530 issues. I also cannot connect from my wifi-connected laptop within the network, so it's not a modem problem, and I don't think it's the router. I'm thinking it's either a configuration problem (I have checked the folder permissions) or a firewall problem somewhere. I understand that ubuntu has a built-in firewall somewhere? How can I check up on this and see if it's the issue? I'm going to try switching from port 1980 to port 21 but I'm not sure if that will help. When I do localhost it says that the Connection is refused, so I don't think I'm even getting in. Any clues?

-Dan

---

### Post by offramp13 on 2008-01-13
Hi, i followed the guide using the gproftpd set up. I have been having issues setting it up so that i can get to more than one directory with a single user.

---

### Post by Deviltongue on 2008-01-19
how do I open up the FTP server?

---

### Post by linux noooob on 2008-01-28
very nice howto thanks :D

---

### Post by linux noooob on 2008-01-28
i have set up my domain name and it goes strait to my router how do i make it all forward to my server?

---

### Post by Georgie.Mathews on 2008-02-12
Hello

I used your Guide, Im currrently on Ubuntu Gutsy Gibbon. Created the directory /home/FTP-shared with the two download and upload subdirectories. The ftp works fine, tested it out on the LAN with filezilla. 

Now I wanted to share my NTFS partition in the download folder so i used the code u posted which said something like 

```

sudo mount -o /media/sda5 /home/FTP-shared/download

```

i restarted the FTP server and tried logging in with my ftp client. I can connect fine into the server but when i try to open the download directory it says

 ```

Error : 550. Permission Denied.

```

Please advise. 

Much appreciated.
G.Mathews

---

### Post by frodon on 2008-02-12
The problem with NTFS is that it doesn't support unix rights system therefore the rights on it depends only on how you mounted the drive.
Keep in mind that when you mount a directory into another one it will have the rights of the source directory (here your NTFS directory).
So check the rights of the directory you are trying to mount, if they are not at minimum 755 then you have the cause of your issue.

---

### Post by splendid on 2008-02-12
I had proftpd working on 5.10, and I just removed that installation and installed 7.10.  Copied over my .conf file from the old configuration, and I get the following message when attempting to restart the service.  

* Stopping ftp server proftpd                                           [ OK ] 
 * Starting ftp server proftpd                                                   - IPv6 getaddrinfo 'basement' error: No address associated with hostname
                                                                         [ OK ]

I am thinking it has something to do with /etc/hosts or an ip route table.  Any thoughts????

This guide is awesome, and was very helpful when I set the ftp server up on 5.10,  I am going to take notes this time, so I don't forget all the places I have to touch.

Thanks,

Rob

---

### Post by frodon on 2008-02-12
You will find the answer in previous posts in the thread, start a search on this thread using the "Search this thread" button under the poll with ipv6 as key word and you will find the posts which contain the fix.
Anyway this error message is not important if you don't use IPV6, so if you use srtandard IPV4 you can ignore it.

---

### Post by Georgie.Mathews on 2008-02-13
Hello

Thanks Frodon. But Im not exactly sure on how to go about it (still a newbie :)). How do i make the rights for my source directory (media/sda5/Stuff) the same as the /home/FTP-shared/download since it doesnt support Unix commands as you said.

Can you please give me a few instructions on how to proceed. Im using Gutsy so it auto mounts my NTFS drive (which is /dev/sda5) into /media/sda5. 

Thanks again
G. Mathews

---

### Post by frodon on 2008-02-13
Auto-mount you said, um could you paste a sample of the output of the "ls -l /media/sda5/" command just to see how the automount mount your partition.
More likely the solution will be to either mount manualy your drive with the suitable command when you want to use it for your ftp or leave an autoexec script at the root of this drive containing the mount command to apply then select in your system mount options to execute autoexec files on removable devices when they exist.

---

### Post by Georgie.Mathews on 2008-02-15
Hello again

Sorry about the late reply was Valentines :lolflag:

Ok i was having a look at my /etc/fstab and i saw a line saying that my /dev/sda5 was mounted on /media/sda5 with Umask=007. I changed that to 022 saved it and rebooted. 
I ran

```
 sudo mount -o bind /media/sda5/Stuff /home/FTP-shared/download


```

and then restarted the ftp server.

I tried connecting with an ftp client again, and guess what, IT WORKED!!
I could access my mounted NTFS drive in the download folder.

But there is a slight problem. Since i have mounted it with the 022 rights I cant even copy anything onto my /media/sda5 partition on my machine.

Is it possible to mount something twice, as in create another line in fstab, using the same UUID as the /dev/sda5, then mount it in lets say for example /media/sda7, but this time using umask=022. Then i can leave the original line (the one with umask=007). using this way i can bind /media/sda7/Stuff onto /home/FTP-shared/download, but at the same time i have write access on the same drive using /media/sda5. In this way i can serve the partition with read access(/media/sda7) but I will have read and write access on my machine (/media/sda5) 

Please let me know if it is safe to do so? It was just an idea, makes sense to me but lol, i just wanted to confirm before i tried it.

Thanks again mate
G. Mathews

---

### Post by frodon on 2008-02-15
I think you can just find a mask option which allows you to use your partition in all cases, maybe 777 i don't know. I have never used NTFS under linux so i can't really help you on this anyway i'm sure the solution exist.

---

### Post by reehan10 on 2008-02-15
i m unable to start my ftp server.....it shows fail....pls help me:confused:

---

### Post by frodon on 2008-02-15
Provide full error message and some proftp config details if you wish help please.

---

### Post by reehan10 on 2008-02-15
i performed all the steps you had said...
but when i gave start command...
it showed startin n then gave fail

---

### Post by reehan10 on 2008-02-15
- IPv6 getaddrinfo 'reehan-laptop' error: No address associated with hostname
reehan-laptop -

---

### Post by frodon on 2008-02-15
Are you kidding ?

Sorry reehan10, it is not you in particular but i'm a bit tired to answer this question every 10 posts, search in this thread the answer is everywhere.
To be exact you will find last iteration of this question just 9 post before !

---

### Post by reehan10 on 2008-02-15
Hey sorry friend....actually i m new to this site..so didnt read it...sorry and thanks...i ll read it
:-)

---

### Post by reehan10 on 2008-02-15
hey thanks a lot...donw with the ftp server n its working fine...
just one more thing...cant i  access ftp server by name..i mean i m accessing it by [ftp://ipaddr...cnt](ftp://ipaddr...cnt) i do by instead a name???
pls do reply

---

### Post by frodon on 2008-02-17
If you wish a domain name there're some free domain name services available on internet the most known i think is dyndns. So you create a dmain name on dyndns then it will point on your IP, if you have a dynamic IP then use one of the scripts available to refresh your domain name automatically.

There's some infos a the end of the first post.

---

### Post by splendid on 2008-02-17
Installed filezilla.  Tried logging in and I am getting a 500 Auth error.  
I have FTPES selected.  Tried the account and interactive options.  No dice.  

Any thoughts, or more info on configuration for filezilla.  I followed the directions and am assuming that TLS is setup properly.

Thanks,

Splendid

---

### Post by frodon on 2008-02-19
Did you try with the computer running the server ?

If you tweaked you proftp config please post your proftpd.conf file so i can check it.

---

### Post by qrwe on 2008-02-19
It should me mentioned that [Webmin]("http://www.webmin.com/") has pretty good support for [proftpd]("http://www.proftpd.org/") configuration.

---

### Post by frodon on 2008-02-19
Webmin is like other automatic configuration tools, like gproftpd though gproftpd tends to be more powerful, it can't do all and won't give you the result you expect if you don't put interest in getting some minimum FTP knowledge.
Webmin won't for example handle your FTP user creation, directory rights.

Even if these are interesting tools nothing is better than real knowledge :)

---

### Post by splendid on 2008-02-19
Frodon,  Attached is proftpd.conf as requested.

Thanks,

Splendid



c/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				on

Include /etc/proftpd/modules.conf

ServerName			"basement"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

DenyFilter			\*.*/

# Use this to jail all users in their homes 
# DefaultRoot			~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell		off

# Port 21 is the standard FTP port.
Port				21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress		1.2.3.4

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				proftpd
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd		off

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile			off

# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend 
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
#<IfModule mod_sql.c>
# SQLBackend			mysql
#</IfModule>

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_tls.c>
TLSEngine on
TLSLog /var/ftpd/tls.log
TLSProtocol TLSv1

# Are clients required to use FTP over TLS when talking to this server?
TLSRequired on
# Server's certificate
TLSRSACertificateFile /etc/ftpcert/server.crt
TLSrsaCertificateKeyFile /etc/ftpcert/server.key

# CA the server trusts
TLSCACertificateFile /etc/ftpcert/ca.crt

# Authenticate clients that want to use FTP over TLS?
TLSVerifyClient off
</IfModule>


<IfModule mod_quota.c>
QuotaEngine on
</IfModule>

<IfModule mod_ratio.c>
Ratios on
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        on
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine on
</IfModule>

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayFirstChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

---

### Post by frodon on 2008-02-20
Hum, you should give me some more details as your structure is not the one used in the tutorial. You have no <LIMIT LOGIN> section and you seem to be using the "user proftp" command to do the user restriction, in addition you have no <DIRECTORY> section and worst of the worst you are not locking the user in a directory which mean your whole system will be accessible which is really unsafe for a FTP server.
BTW you are using IPV6 for your internet connection ?

---

### Post by splendid on 2008-02-21
It was late when I was working on this.  I guess maybe I did not look close enough at the proftpd.conf file in the tutorial.  

I definitely was not planning to open this up and allow it too be so vulnerable.  What do you suggest to do for user restriction?

Thanks for looking at this, and pointing out my deficiencies with the file.  I appreciate it.

---

### Post by frodon on 2008-02-21
To limit the login no need to use "user" and "group" commands, i'm not even sure they can be used for this purpose.
Just use a <LIMIT LOGIN> section to choose what user will be able to access you FTP server (the first post config should give you a good example).
Then i think it is mandatory to lock the user in a specific directory otherwise your whole system will be accessible for this purpose use the "DefaultRoot /home/FTP-shared" command (change the directory path according to your need).
Finally to be more accurate add a directory section for each directory you wish to share so you can handle the rights on a per directory basis.

---

### Post by MoriyaMinakata on 2008-02-23
I have a few questions which I am not sure if they were covered.
73 pages is a lot to read. ^^;

So, here we go:

1) Is there a way to mount drives shared from a Windows machine through Samba and then set the ftp to allow users to get onto those?

2) Is it possible for more than one user to have the same home drive?
A little further explaination: I want to set users with access to the same folders, but I want different bandwidth caps on them. When I try to add two different users with the same home folder, proftpd doesn't start, telling me that the home folder is already in use or something to that effect.

3) How do I allow users to change to different drives without creating a new username? Is it the same as windows based ftp servers where they are simply shortcuts?

Thanks in advance for the help, guys.

---

### Post by splendid on 2008-03-04
Frodon, I am having problems again.  Getting following message:

* Starting ftp server proftpd                                                   - mod_dso/0.4: module 'mod_tls.c' already loaded
 - Fatal: LoadModule: error loading module 'mod_tls.c': File exists on line 16 of '/etc/proftpd/modules.conf'

---

### Post by splendid on 2008-03-04
This file is used to manage DSO modules and features.
#

# This is the directory where DSO modules reside

ModulePath /usr/lib/proftpd

# Allow only user root to load and unload modules, but allow everyone
# to see which modules have been loaded

ModuleControlsACLs insmod,rmmod allow user root
ModuleControlsACLs lsmod allow user *

#  LoadModule mod_ctrls_admin.c
LoadModule mod_tls.c
LoadModule mod_sql.c
LoadModule mod_ldap.c
LoadModule mod_sql_mysql.c
LoadModule mod_sql_postgres.c
LoadModule mod_quotatab.c
LoadModule mod_quotatab_file.c
LoadModule mod_quotatab_ldap.c
"modules.conf" 31 lines, 741 characters

---

### Post by frodon on 2008-03-05
@splendid, it's because (according to post #727) you have the "Include /etc/proftpd/modules.conf" twice in your proftpd.conf.

@MoriyaMinakata:
1) Yes, you just need to set the good rights on this folder.

2)Yes, just create your user like you created the "userFTP" user then at him to the LIMIT login section and eventually give him an alias if you use alias names.

3)I don't understand the question sorry.

---

### Post by splendid on 2008-03-05
Frodon Thanks.  That took care of problem.  I am unable to FTP into the server.  It seems like it is connecting through Filezilla, and then complains.  I get a 550 error code.  Any ideas where I might check.  Have been reading through the forum and hav enot found anything yet.

Thanks,

Splendid

---

### Post by frodon on 2008-03-06
I would need the exact filezilla log and also test with some other FTP clients as it might be from the client. Of course check one more times your shared folder rights they must be 755 for download directories and 777 for upload directories, the files in the directories you share must have the good rights too.

---

### Post by Daleth on 2008-03-06
Hey, Ive read the replies but I still got a 530 error, 

after a second try to install proftpd, I just did what you wrote on the turorial, using your config and the same chmod /home/FTP-shared/ etc, but I still get 530, whats the problem? 
Response:	220 you're at home
Command:	USER breakz
Response:	331 Password required for breakz.
Command:	PASS ******
Response:	530 Login incorrect.
Error:	Unable to connect!

CHmods: 
download 755
upload 777
FTP-shared 755

---

### Post by frodon on 2008-03-06
530 error as you should have read is the indicator of a mistake in the config, most often wrong directory rights or problem with password.
Check thoroughly your whole config and set a new password for your userFTP user it solve the problem in some cases (try either using GUI either using command line).

---

### Post by Daleth on 2008-03-06
> **frodon said:**
> 530 error as you should have read is the indicator of a mistake in the config, most often wrong directory rights or problem with password.
Check thoroughly your whole config and set a new password for your userFTP user it solve the problem in some cases (try either using GUI either using command line).

well Im using your config, havent changed anything in it :P I only changed sauron to breakz, thats all

---

### Post by frodon on 2008-03-06
Have you tested several password change using GUI and CLI ? Have you tested this on the same computer that run the server ?

---

### Post by Daleth on 2008-03-06
> **frodon said:**
> Have you tested several password change ?

yes, tried it a few times..

---

### Post by frodon on 2008-03-06
Then search check more thoroughly to get what is wrong in your config, it's almost impossible for me to guess what is wrong on your config in this case, the person the most able to help you on this is yourself unfortunately.
Try to explain how you tested your server and maybe give details about your home network structure.

---

### Post by Daleth on 2008-03-06
Okay, Ive got it working, Installed it to another dir,

anywayz, now Ive installed SSL/TSL for proftpd:
<IfModule mod_tls.c>
TLSEngine                  on
TLSLog                     /var/log/proftpd/tls.log
TLSProtocol                SSLv23
TLSOptions                 NoCertRequest
TLSRSACertificateFile      /etc/proftpd/ssl/proftpd.cert.pem
TLSRSACertificateKeyFile   /etc/proftpd/ssl/proftpd.key.pem
TLSVerifyClient            on
TLSRequired                on
</IfModule>

is there a way to check if its working? I know on IRC when you install SSL, you need to do something with the ports to logon with SSL, is it the same way on proFTPD? I just wanna allow SSL clients

---

### Post by frodon on 2008-03-06
"TLSRequired on" directive indicates that only TLS encrypted connection will be allowed so you are sure with this setting to use encrypted connection, in addition you should also see in your FTP client log the "AUTH TLS" directive.

---

### Post by Daleth on 2008-03-06
Hm, cant seem to find "Auth TLS" Pasting Client list:

Response:	220 you're at home
Command:	USER ftpd
Response:	331 Password required for ftpd.
Command:	PASS ******
Response:	230 welcome !!!
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Features:
Response:	 MDTM
Response:	 REST STREAM
Response:	 SIZE
Response:	211 End
Status:	Connected
Status:	Retrieving directory listing...

---

### Post by frodon on 2008-03-06
I would say it is not running reading this log, are you sure you have added the "Include /etc/proftpd/modules.conf" line in your proftpd.conf file and that mod_tlc module is well listed in /etc/proftpd/modules.conf file ?
If not then your mod_tls module is not loaded and then not used.

---

### Post by Daleth on 2008-03-06
modules.conf: 
LoadModule mod_tls.c

proftpd.conf:
Include /etc/proftpd/modules.conf

quite strange huh? Ive tried to restart it but its still now working somehow hm..

---

### Post by frodon on 2008-03-06
Sorry i didn't see you did not used the instruction from the first post, I don't know for the instructions you use, i know mine are working and i support them however other instructions are not supported by me in this tutorial.

Don't know where you got these instructions but you should ask for support where you got them, not here.

---

### Post by splendid on 2008-03-07
I checked the Upload and Download directories.  Needed to change permissions on the Upload directory, but still having problems.  Tried accessing from Windows Explorer and get following msg:

Windows Cannot access this folder.  Make sure you typed the file name correctly and that you have permission to access the folder.

Details
220 ProFTPD 1.3.0 Server (basement) [192.168.0.101]
550 SSL/TLS required on the control channel


Been searching through posts.  Not sure what to do next.

---

### Post by splendid on 2008-03-07
proftpd.conf

#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				off

# Choose here the user alias you want!!!!
UserAlias rob userftp

ServerName			"basement"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer		600
TimeoutStalled			100
TimeoutIdle			2200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

DenyFilter			\*.*/

# Use this to jail all users in their homes 
# DefaultRoot			~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
RequireValidShell		off

TimeoutLogin 20

RootLogin			off

# Port 21 is the standard FTP port.
Port				1980

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  6000 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress		192.168.0.101

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd		off

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile			off

# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend 
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
#<IfModule mod_sql.c>
# SQLBackend			mysql
#</IfModule>

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_tls.c>
TLSEngine on
TLSLog /var/ftpd/tls.log
TLSProtocol TLSv1

# Are clients required to use FTP over TLS when talking to this server?
TLSRequired on
# Server's certificate
TLSRSACertificateFile /etc/ftpcert/server.crt
TLSrsaCertificateKeyFile /etc/ftpcert/server.key

# CA the server trusts
TLSCACertificateFile /etc/ftpcert/ca.crt

# Authenticate clients that want to use FTP over TLS?
TLSVerifyClient off
</IfModule>


<IfModule mod_quota.c>
QuotaEngine on
</IfModule>

<IfModule mod_ratio.c>
Ratios on
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        on
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine on
</IfModule>

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayFirstChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

---

### Post by frodon on 2008-03-08
> **splendid said:**
> I checked the Upload and Download directories.  Needed to change permissions on the Upload directory, but still having problems.  Tried accessing from Windows Explorer and get following msg:

Windows Cannot access this folder.  Make sure you typed the file name correctly and that you have permission to access the folder.

Details
220 ProFTPD 1.3.0 Server (basement) [192.168.0.101]
550 SSL/TLS required on the control channel


Been searching through posts.  Not sure what to do next.I'm not sure windows explorer support this protocol and without the exact url you typed in windows explorer i can't tell you if you did something wrong. Anyway FTP client are there to avoid having nightmares with web browsers and FTP so you should just use them.

---

### Post by TomFumb on 2008-03-08
First off, great howto, I had a secure ftp server up and running in no time! Thanks very much for that.

I have a quick question about proftpd, and although it might have been answered already in this thread, I don't particularly want to trawl through 50+ pages...

So if no one minds, could you please tell me how to disable the server by default? I don't envisage needing to provide ftp server most of the time, just every once in a while. I have proftpd configured as a standalone process, so what can I do to tell it to not startup with the computer, and only when I want?

Any help with this would be greatly appreciated,

Tom.

---

### Post by frodon on 2008-03-08
System > Administration > Services, uncheck proftp so it won't be start on boot :).

---

### Post by TomFumb on 2008-03-08
hehe, thanks

---

### Post by splendid on 2008-03-08
Okay tried Filezilla

host:  basement.homelinux.net            port:1980

server type:  FTPES  -FTP over explicit TLS/SSL

logontype:  Ask for Password

user:   rob

Get following message:

Resolving IP-Address for basement.homelinux.net
Connecting to 71.230.201.151:1980
Connection established, waiting for welcome message
[COLOR="SeaGreen"]220 ProFTPD 1.3.0 Server (basement) [192.168.0.101][/COLOR]
AUTH TLS
[COLOR="SeaGreen"]234 AUTH TLS Successful[/COLOR]
Initializing TLS
[COLOR="Blue"]USER rob[/COLOR]
[COLOR="Red"]Error:  Could not connect to server[/COLOR]

[COLOR="Black"]When I set this up with 5.10, I did not have this much trouble.   [/COLOR]

---

### Post by splendid on 2008-03-09
I was able to get ssh working and can transfer files.  Still working at FTP.

---

### Post by bhuwan on 2008-03-16
How does one use the GUI to add users for ProFTPD? I have Ubuntu Server installed.

---

### Post by frodon on 2008-03-16
You said it all, you have Ubuntu Server edition which means with no GUI (except if you installed a desktop environment). Just use command line to create your user.

---

### Post by Agman on 2008-03-17
This is my first post in the Ubuntu forum and I must say Ubuntu Server is indeed very powerful and I am very pleased with it :)

Okay. I don't know if this issue has been brought up before or not. But I have my SFTP server up and running and its doing great. I can connect to it with FileZilla using the FTPES connection and it works.

The problem is that for my web development I use Dreamweaver CS3 on Windows. It supposedly supports SFTP yet when I try to log in using SFTP it doesn't connect to the server. It gives me an authentication error. It can log in if I use regular unencrypted FTP. But I want to use SFTP.

Do any of you know if there is a way that I can connect to this SFTP server without having the connection be an FTPES type and just a regular SFTP connection. Basically I want to know if its possible to connect to this without having to have a client that supports exlicit TLS/SLL connections (i.e. Dreamweaver)

Thanks in advance for the help,
Agman

---

### Post by frodon on 2008-03-18
It is not SFTP here, SFTP is ftp in ssh tunnel. The tutorial explains you how to set a FTP server with TLS encryption most often called FTPS.
Without a client which support FTP with TLS/SLL i'm scared there's no way to login your server except if you remove the encryption obviously.

The other option you have is to install a SSH server, configure it to restrict the access only to the directories you want to share then you will be able to access these directories using the SFTP support of Dreamweaver because if i understood well SFTP just mean you connect through FTP client to a SSH server.

---

### Post by Agman on 2008-03-18
Ohh I see. After looking at it now it makes sense. I feel kinda dumb now.

Anyway, do you know howt o set this up. I already have an SSH server running and I can log in using my account. But I don't know how to restrict it to one folder.

I still want to be able to login via SSH and have complete control of the machine so I don't have to stand in front of it to make changes but I would also like to do SFTP with restricted access so this makes me believe I have to use the account I created for ftps. What do you think?

---

### Post by frodon on 2008-03-18
Unfortunately i'm far to be an SSH expert as i never had to set myself a ssh server so i can't help you on this, sorry.
Maybe you should try to post your ssh server question in the server forum, i'm sure there's some experts around who will be able to bring some insight one this and help you.

---

### Post by blithen on 2008-03-19
How do you access it..like what do I type into the address bar or what? (I'm a complete noob sorry)

---

### Post by frodon on 2008-03-19
In address bar ?

Bad idea in general to use web browser to access your FTP, it not as convenient as using a FTP client. About FTP client you have the choice, i guess most of use Gftp or filezilla.

---

### Post by NeonSamurai on 2008-03-19
Hi Frodon,

Great thread and thanks for sticking with it for noobs like myself. 

Following your instructions I'm having problems when I try restarting the FTP server:

> * Stopping ftp server proftpd                                           [ OK ] 
 * Starting ftp server proftpd                                                   - IPv4 getaddrinfo 'Auriga' error: No address associated with hostname
 - warning: unable to determine IP address of 'Auriga'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
                                                                         [fail]

I'm pretty sure the problem isn't the proftpd.conf, but something else. Any ideas?

Thanks


Mark

---

### Post by frodon on 2008-03-19
Post your proftpd.conf just in case, if it's not in your proftpd.conf i would say the issue is in /etc/hosts file with a missing hostname (here Auriga) at the end of the "localhost" line.

---

### Post by Yes on 2008-03-20
Great guide, but... how do I get to the FTP? I think I have it mostly figured out, but In the FTP client, what do I put for host?

Thanks!

---

### Post by Sir Jake on 2008-03-20
Ever since I installed this, my connection starts to peak every second using my max speed. Any idea what could be doing this? I tried sudo /init.d/blahblah. stop command and it said stopped but my connection is still peaking. :(
I have to keep my server off tell I can find out what is doing it.

---

### Post by Kulgan on 2008-03-20
> **Yes said:**
> Great guide, but... how do I get to the FTP? I think I have it mostly figured out, but In the FTP client, what do I put for host?

Thanks!

You can either use "localhost", without the quotes of course, or the IP 127.0.0.1

In addition, if you want to use something random, you can go into the file /etc/hosts (execute "sudo gedit /etc/hosts") and add any names, seprated by space, at the end of the line strting with 127.0.0.1

---

### Post by frodon on 2008-03-20
> **Yes said:**
> Great guide, but... how do I get to the FTP? I think I have it mostly figured out, but In the FTP client, what do I put for host?

Thanks!The host to use is the IP address of the computer running the server.

> **Sir Jake said:**
> Ever since I installed this, my connection starts to peak every second using my max speed. Any idea what could be doing this? I tried sudo /init.d/blahblah. stop command and it said stopped but my connection is still peaking. :(
I have to keep my server off tell I can find out what is doing it.If you stopped the server and still have these peaks then it is not related to proftp.

---

### Post by alejaaandro on 2008-03-20
Thanks a lot frodon..  And of course everybody that has given a piece of advice in this thread..
After 3-4 days i finally managed to set up an FTP, which turned out really handy for file sharing between my ubuntu machine and a windows laptop that we have at home...I also decided to make it accessible from the internet (which is what actually troubled me the most)

For all the newbies trying to do the same thing (this might have already been mentioned, but I couldn't read through the entire thread, it's pretty large.. I only got to page 20something) here's some advice:

* if you decided not to follow frodons' HOWTO and go with port 21, think it over.. It's not only for safety reasons, it's because some modems or routers have an "internal FTP" which in most of the cases is on by default.. In that case you will see you are connected but your login will always fail. Try putting the username and psswd you use to configure your modem/router and you'll probably be able to login. But it's not what you've been trying to do, it has nothing to do with proftpd.. How to solve the problem? You either change the port you are using for your FTP or disable the modem/routers' FTP..

*when trying to connect to your FTP** from the internet** and you get 
Cannot connect to your_external_ip: Connection refused
 it's probably because your modem/router prevents you from  sending information out and then in again.. (I think it's called loop protection or something).. I don't think you can turn that off, so you will have to find another connection to test you FTP.. **When I say another connection I don't mean another computer from your network!!!!** I mean a friends pc or something else.
I spent 2 days trying to "fix" the problem, only to find out in the end that my FTP server was working flawlessly, it was my router preventing me to connect!!! Using a proxy to connect is supposed to solve the problem, but it didn't for me. (frodon, you might want to put a notice of that in the tutorial so people won't have to spend time trying to figure out the problem)

*for file sharing between windows and ubuntu, when trying to connect from windows to proftpd, dont' use Internet Explorer (IE). It's pretty crappy, and if you can't connect it will probably not help you as its' error messages are useless.. Google "free ftp client" and choose one (i use coreftp). Install it and you're ready. (FireFTP for Firefox didn't work for me and it's error messages aren't very helpful either)

---

### Post by blithen on 2008-03-25
OKAY! I finally got it working. I just don't have write access to the upload/download folder. What group do I set userftp at to make it have write functions.
EDIT: I got it so anything I put in the upload folder you can download. But that's it. I can't make any directories anywhere. Only if I'm root on my computer...any help?

---

### Post by blithen on 2008-03-26
If I'm correct I should put stuff I want people to access in the Upload folder and I want things people put in my server in the Download folder right?

---

### Post by frodon on 2008-03-26
No it's the invert :P, in the download directory you put what you want your users be able to download without being able to modify anything and in the upload directory users can upload things on your computer.

---

### Post by NeonSamurai on 2008-03-27
> **frodon said:**
> Post your proftpd.conf just in case, if it's not in your proftpd.conf i would say the issue is in /etc/hosts file with a missing hostname (here Auriga) at the end of the "localhost" line.

Hi frodon, sorry for the delay ion getting back to you. Here's my proftpd.conf:

> # To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

UserAlias splendid userftp

ServerName                      "Auriga FTP"
ServerType                      standalone
DeferWelcome                    on

MultilineRFC2228 on
DefaultServer                   on
ShowSymlinks                    off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                     "-l"

RequireValidShell               off

TimeoutLogin 20

RootLogin                       off

# It's better for debug to create log files ;-)
ExtendedLog                     /var/log/ftp.log
TransferLog                     /var/log/xferlog
SystemLog                       /var/log/syslog.log

#DenyFilter                     \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ba$
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart               on

# Port 21 is the standard FTP port, so you may prefer to use another port for s$
Port                            1980

MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022     022

PersistentPasswd                off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "Greetings Higlander !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "Welcome to Auriga"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/vault

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS

<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

<Directory /home/vault/download/*>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

<Directory> /home/vault/upload/>
Umask 022 022
AllowOverwrite on
        <Limit READ RMD DELE>
        DenyAll
        </Limit>

        <Limit STOR CWD MKD>
        AllowAll
        </Limit>
</Directory>


And just to recap, here's the error I'm getting:

> * Stopping ftp server proftpd [ OK ]
* Starting ftp server proftpd - IPv4 getaddrinfo 'Auriga' error: No address associated with hostname
- warning: unable to determine IP address of 'Auriga'
- error: no valid servers configured
- Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
[fail]

Many thanks


Mark

---

### Post by frodon on 2008-03-27
Ok i think *ServerName "Auriga FTP"* is the problem as i'm not sure space are supported there, server name must remain as simple as possible if you want to avoid such problems.

---

### Post by NeonSamurai on 2008-03-27
Cheers Frodon, I'll give that a go. 

Many thanks

---

### Post by psychobeauty on 2008-03-27
when i install proftp i get this error:
and i cannot start it 



```
Not creating home directory `/var/run/proftpd'.
 * Starting ftp server proftpd                                                   - IPv4 getaddrinfo 'psycho' error: No address associated with hostname
 - warning: unable to determine IP address of 'psycho'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
                                                                         [fail]
invoke-rc.d: initscript proftpd, action "start" failed.
dpkg: error processing proftpd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by blithen on 2008-03-28
Well either way I can't modify anything in the upload directory 
```
Status:	Creating directory '/upload/New folder/'...
Command:	MKD New folder
Response:	550 New folder: Permission denied
Command:	MKD /upload/New folder/
Response:	550 /upload/New folder/: Permission denied
```

---

### Post by frodon on 2008-03-28
> **psychobeauty said:**
> when i install proftp i get this error:
and i cannot start it 



```
Not creating home directory `/var/run/proftpd'.
 * Starting ftp server proftpd                                                   - IPv4 getaddrinfo 'psycho' error: No address associated with hostname
 - warning: unable to determine IP address of 'psycho'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
                                                                         [fail]
invoke-rc.d: initscript proftpd, action "start" failed.
dpkg: error processing proftpd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Ouch, the install definitively went bad, check that you have well all the repositoriues enable (main,universe, multiverse, restricted) and try to reinstall. There should be a reason why the install fail on your system.

> **blithen said:**
> Well either way I can't modify anything in the upload directory 
```
Status:	Creating directory '/upload/New folder/'...
Command:	MKD New folder
Response:	550 New folder: Permission denied
Command:	MKD /upload/New folder/
Response:	550 /upload/New folder/: Permission denied
```Normally it should work without any problem. The problem either come to too restrictive rights on your upload directory (rights must 777 to avoid pb on this directory) or the problem come from your proftpd.conf file.
Please post your proftpd.conf file if you modified it.

---

### Post by NeonSamurai on 2008-03-28
> **frodon said:**
> Ok i think *ServerName "Auriga FTP"* is the problem as i'm not sure space are supported there, server name must remain as simple as possible if you want to avoid such problems.

Okay, I took out the space (making it AurigaFTP) but the problem persists. 

>  * Stopping ftp server proftpd                                                     [ OK ] 
 * Starting ftp server proftpd                                                             - IPv4 getaddrinfo 'Auriga' error: No address associated with hostname
 - warning: unable to determine IP address of 'Auriga'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
                                                                                   [fail]


Any ideas?

---

### Post by frodon on 2008-03-28
Then it should come from your /etc/hosts file i think, could you post it there please ?

---

### Post by psychobeauty on 2008-03-28
> **frodon said:**
> Ouch, the install definitively went bad, check that you have well all the repositoriues enable (main,universe, multiverse, restricted) and try to reinstall. There should be a reason why the install fail on your system.

Normally it should work without any problem. The problem either come to too restrictive rights on your upload directory (rights must 777 to avoid pb on this directory) or the problem come from your proftpd.conf file.
Please post your proftpd.conf file if you modified it.


thanx for replying..my problem is that while before vsftpd was installed ok..i removed it and now it cannot reinstalled again..its shows the same errors as in proftpd.....

---

### Post by frodon on 2008-03-28
Ok, you should solve your issue following the instructions given in this thread :
[http://ubuntuforums.org/showthread.php?t=543172](http://ubuntuforums.org/showthread.php?t=543172)

---

### Post by psychobeauty on 2008-03-28
check that you have well all the repositoriues enable (main,universe, multiverse, restricted) and try to reinstall. There should be a reason why the install fail on your system.








how can i check that????

---

### Post by frodon on 2008-03-28
You can check that using [synaptic package manager]("https://help.ubuntu.com/community/SynapticHowto"), in *Settings* tab click on *Repositories*, but here i think it might not be the cause.
I think the solution is in the thread i linked in my previous post.

---

### Post by tmcmulli on 2008-03-28
I've got my ftp server up and running, and all looks good.  I mount a USB hard drive to one of my download directories, but get "access denied" from my ftp client.  I tried to chmod the usb drive, and the mounted directory and nothing is happening...

Am I being a total bonehead here??  Does chmod work differently on ext hard drives?  Ideally, I have a system account that I would like to have mostly full access to my mounted drives, but lesser access depending on logins...any help MUCH appreciated...

---

### Post by frodon on 2008-03-28
What filesystem use your external drive ?

Chmod should work as expected normally, at least it did for me last time i tried, in general when one want to attribute same rights for several users on the same file one use group rights attributes.

---

### Post by tmcmulli on 2008-03-28
> **frodon said:**
> What filesystem use your external drive ?



'Doh!  Fat32... problem solved...  Thanks!

---

### Post by psychobeauty on 2008-03-29
> **psychobeauty said:**
> check that you have well all the repositoriues enable (main,universe, multiverse, restricted) and try to reinstall. There should be a reason why the install fail on your system.








how can i check that????



hi again, i check everythink i changed the hostname but stills nothing...

the problem is that with every ftp the install fail..i tried ftpd,vsftp,proftp....


the vsftp the first time i install it worked...but then i remove it...and i reinstall it again but it does not installed correctly anymore...

i think the problem might be due to some etc files of vsftp that did not removed completely...

but when i try ```
sudo killall -9 vsftp or froftp
```

its says no process to be removed....how can i have it completelly remove.. as the system was before i install them for the first time...

---

### Post by blithen on 2008-03-29
Alright. Here is my proftpd.conf
```
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias blithen userftp

ServerName			"ChaosTheory"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port				1980

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/YourUploads/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>
```
Change Downloads to 'YourUploads' and Uploads to 'MyUploads'. It was easier to understand to me. I changed everything accordingly though.

---

### Post by frodon on 2008-03-29
Ok your upload directory just don't allow basic write commands so the FTP server is behaving right not allowing anyone to upload on your server.

Your upload directory section should look like that to allow users to upload files :
```
<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
```
With this configuration users are allowed to write in your upload directory but they won't be allowed to delete files (this is configurable of course).

---

### Post by blithen on 2008-03-29
YES FINALLY. Everything work perfectly. Thank you SO much for all of your help. You rock.:guitar:

---

### Post by BlizzofOZ on 2008-03-29
Read thru the tutorial decided to give it a try.

When I go to start Proftpd, I get the following error:
root@MyServer:/home/john# /etc/init.d/proftpd start
 * Starting ftp server proftpd                                                   - IPv6 getaddrinfo 'MyServer.ri.cox.net' error: No address associated with hostname


I had modified my hosts config file to get Putty and TightVNC working, so I have a feeling I'm missing something here... 

Any ideas?

Thought this might give some more into:  /etc/hosts

127.0.0.1	localhost
127.0.1.1	MyServer.ri.cox.net	MyServer

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

EDIT:
Well, I found msm's post and made some mods regarding masquerading... still getting above error.

In Firefox, I tried to get to the FTP server and got the following.  I seem to be connecting... how do you connect?  Is Firefox acceptable?

220 you're at home
500 GET not understood
500 HOST: not understood
500 USER-AGENT: not understood
500 ACCEPT: not understood
500 ACCEPT-LANGUAGE: not understood
500 ACCEPT-ENCODING: not understood
500 ACCEPT-CHARSET: not understood
500 KEEP-ALIVE: not understood
500 CONNECTION: not understood
421 Login Timeout (20 seconds): closing control connection.

---

### Post by BlizzofOZ on 2008-03-29
> **BlizzofOZ said:**
> Read thru the tutorial decided to give it a try.

When I go to start Proftpd, I get the following error:
root@MyServer:/home/john# /etc/init.d/proftpd start
 * Starting ftp server proftpd                                                   - IPv6 getaddrinfo 'MyServer.ri.cox.net' error: No address associated with hostname


I had modified my hosts config file to get Putty and TightVNC working, so I have a feeling I'm missing something here... 

Any ideas?

Thought this might give some more into:  /etc/hosts

127.0.0.1	localhost
127.0.1.1	MyServer.ri.cox.net	MyServer

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

EDIT:
Well, I found msm's post and made some mods regarding masquerading... still getting above error.

In Firefox, I tried to get to the FTP server and got the following.  I seem to be connecting... how do you connect?  Is Firefox acceptable?

220 you're at home
500 GET not understood
500 HOST: not understood
500 USER-AGENT: not understood
500 ACCEPT: not understood
500 ACCEPT-LANGUAGE: not understood
500 ACCEPT-ENCODING: not understood
500 ACCEPT-CHARSET: not understood
500 KEEP-ALIVE: not understood
500 CONNECTION: not understood
421 Login Timeout (20 seconds): closing control connection.

Ok... I d/l Filezilla and was able to connect and login to the FTP server.

Noob question:  Can you use a web brower like Firefox to access the FTPserver?

---

### Post by frodon on 2008-03-29
Of course you can but it is less convenient, to do so type the adress like that :
[ftp://username@hostname:port](ftp://username@hostname:port)

You can skip the port attribute if you use port 21 as it is the default port used.

For the ipv6 error it doesn't prevent the server to work correctly, anyway if you don't want to see it anymore add your hostname after* ::1 ip6-localhost ip6-loopback*, for you it would make :
```
::1 ip6-localhost ip6-loopback MyServer.ri.cox.net
```

---

### Post by BlizzofOZ on 2008-03-29
> **frodon said:**
> Of course you can but it is less convenient, to do so type the adress like that :
[ftp://username@hostname:port](ftp://username@hostname:port)

You can skip the port attribute if you use port 21 as it is the default port used.

For the ipv6 error it doesn't prevent the server to work correctly, anyway if you don't want to see it anymore add your hostname after* ::1 ip6-localhost ip6-loopback*, for you it would make :
```
::1 ip6-localhost ip6-loopback MyServer.ri.cox.net
```

frodon, when I try to access thru Firefox, it how askes for the use password.  After entering pswd, screen goes blank and just sits there loading.

I guess I was wrong on Filezilla as I'm getting an error after connecting:
Status:	Connected
Status:	Retrieving directory listing...
Command:	CWD /home/FTP-shared/
Response:	550 /home/FTP-shared/: No such file or directory
Error:	Failed to retrieve directory listing

I have followed the instructions on setting the directory and permissions... not sure why it can't find /home/FTP-shared.

Where do I add this:
::1 ip6-localhost ip6-loopback MyServer.ri.cox.net

---

### Post by frodon on 2008-03-29
If you did not modified the proftpd.conf ilfe provided and well set the rights on the directories then it should work without any problem.
If you mofified the given proftpd.conf files please post it.

About the suggestion for the IPV6 erors i meant to fix the concerned line in your /etc/hosts file.

---

### Post by BlizzofOZ on 2008-03-29
> **frodon said:**
> If you did not modified the proftpd.conf ilfe provided and well set the rights on the directories then it should work without any problem.
If you mofified the given proftpd.conf files please post it.

About the suggestion for the IPV6 erors i meant to fix the concerned line in your /etc/hosts file.

frodon,
First would like to thank you for taking the time to help!

Second
I used msm's config file and tweaked it slightly for user and port stuff:
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly off

# Choose here the user alias you want !!!!
#UserAlias scott schmeerftp

ServerName			"MyFTP"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 1200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port				21000

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

#MaxClients 8
#MaxClientsPerHost 8
#MaxClientsPerUser 8
#MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser scottftp
#AllowUser schmeerftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
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

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default. 
#DelayEngine 			off

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayFirstChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

MasqueradeAddress	myserver.homelinux.net

# These ports should be safe...
PassivePorts 60000 65535

UseReverseDNS off
IdentLookups off

---

### Post by NeonSamurai on 2008-03-31
> **frodon said:**
> Then it should come from your /etc/hosts file i think, could you post it there please ?

Hi Frodon, here's my hosts file:

> 127.0.0.1 localhost
127.0.1.1 Auriga.agency.org

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Many thanks


Mark

---

### Post by frodon on 2008-03-31
I think it should be :
127.0.0.1 localhost Auriga.agency.org

But i'm not sure, try some different implementations and search on the forum, some other users had this problem and solved it.

---

### Post by NeonSamurai on 2008-03-31
> **frodon said:**
> I think it should be :
127.0.0.1 localhost Auriga.agency.org

But i'm not sure, try some different implementations and search on the forum, some other users had this problem and solved it.

Thanks frodon I found post #409 by kptracey which covered this:

> 
If you run into the same problem... do me a favour and in terminal type: 'hostname -f'
I bet it responds 'hostname: Unknown host'

If it does, do this:
sudo gedit /etc/hosts/

Add this line: '127.0.0.1 <hostname> <FQDN>'

FQDN stands for Fully Qualified Domain Name
hostname is the name of your machine

Mine reads something like this:
127.0.0.1 samurai samurai.phubs.net.cab.irelandrules.com

In this instance, hostname is samurai and samurai.phubs.net.cab.irelandrules.com is the FQDN.

In hindsight, this is a result of me being lazy during my Samba install and simply appending a preexisting entry with mshome and slightly altering the 127 mask.

I amended my hosts file accordingly (in this case using your syntax and renaming 'localhost' to 'Auriga').

Thanks


Mark

---

### Post by frodon on 2008-03-31
Glad to hear this, enjoy your FTP server now :)

---

### Post by BlizzofOZ on 2008-03-31
> **BlizzofOZ said:**
> frodon,
First would like to thank you for taking the time to help!

Second
I used msm's config file and tweaked it slightly for user and port stuff:
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly off

# Choose here the user alias you want !!!!
#UserAlias scott schmeerftp

ServerName			"MyFTP"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 1200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port				21000

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

#MaxClients 8
#MaxClientsPerHost 8
#MaxClientsPerUser 8
#MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser scottftp
#AllowUser schmeerftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
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

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default. 
#DelayEngine 			off

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayFirstChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

MasqueradeAddress	myserver.homelinux.net

# These ports should be safe...
PassivePorts 60000 65535

UseReverseDNS off
IdentLookups off

Hi fordon, see above... not sure if you missed my posting my conf file like you asked.

---

### Post by frodon on 2008-03-31
I did not miss you post, i just can't help you as nothing seem wrong. I think the issue is in your system rights and the FTP shared folders.

---

### Post by blithen on 2008-04-02
Okay. It seems that even though i followed the instructions on the front page about the router it still will not work.
Any ideas? People can't connect to me server.

---

### Post by Animortis on 2008-04-17
I did everything in your first post verbatim with TLS support and when I log in the FTP client gets to LIST and times out. 

My proftpd.conf file is copied and pasted from yours in the first post and I added the "on" trigger for TLSRequired and included the TLS lines, copied and pasted at the bottom, as well as the "Include /etc/proftpd/modules.conf" line.

I gave the FTP-shared chown access to userftp:userftp as well as all its subdirectories and 755 access to the directory. Upload has 777 access and download has 755.

Why is it still timing out?

**EDIT:**

Scratch that. I found the posts about setting up passive listening ports. Ehehe. It works fine now. Well done with the post, though maybe you should set that part a little more prominently in the post since most people use routers anymore.

---

### Post by mattchess on 2008-04-17
Thank you for this guide.  I was able to get my ftp up and running in minutes!  It works perfectly. :)

---

### Post by Lostincyberspace on 2008-04-17
I have just started setting up my ftp server and have been trying to login to test and I get 
```

Status:    Connecting to 192.168.0.109:21...
Status:    Connection established, waiting for welcome message...
Error:    Could not connect to server
Status:    Waiting to retry...

```

Here is my proftpd.conf for you pleasure

```

ServerType standalone
DefaultServer on
Umask 022
ServerName "192.168.0.109"
ServerIdent on "minttop"
ServerAdmin Lee@logonomics.net
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 10000
TimeoutIdle 10000
DisplayLogin welcome.msg
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 999999
TransferRate STOR 999999
TransferRate STOU 999999
TransferRate APPE 999999
SystemLog /var/log/secure
RequireValidShell off
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_homedir_path /var/ftp
#gp_html_path /var/www/html/ftp.htm
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
</IfModule>
<IfModule mod_ratio.c>
Ratios off
SaveRatios off
RatioFile "/restricted/proftpd_ratios"
RatioTempFile "/restricted/proftpd_ratios_temp"
CwdRatioMsg "Please upload first!"
FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
LeechRatioMsg "Your ratio is unlimited."
</IfModule>
<Limit LOGIN>
  AllowUser lmyers
  AllowUser userftp
  AllowUser ftp
  AllowUser proftpd
  AllowUser lee
  DenyALL
</Limit>

<Anonymous /home/FTP-shared>
User lmyers
Group lee
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>


```

Please see if there is any thing wrong and if you know how I could make it work.

---

### Post by frodon on 2008-04-18
This thread is to support users using the tutorial not to debug your proftpd configurations, proftpd forum is way more appropriate for this.
[http://forums.proftpd.org/smf/](http://forums.proftpd.org/smf/)

Anyway with so few details there's no answer to your question, think to check firewall and router settings. On the other hand i warn you that your config is not safe so you should better use it only on home network.

---

### Post by Animortis on 2008-04-19
How do you get proftpd to start automatically on booting your system?

**EDIT:**
And if it's supposed to start automatically, what can I do to get it to happen? Note: update-rc.d does not work, it says system startup links already exist.

---

### Post by frodon on 2008-04-21
System > Administration > Services is the place in ubuntu where you can choose which service to start on boot or not.

---

### Post by Lostincyberspace on 2008-04-21
I did use the tutorial but I have been having major problems with it after the tutorial ended so I saw others that had posted their information and got help so I figured I would try to see if it was some very small problem that I had missed some where. But thank you for the link to the forum I wil go there and see if I get more help. Oh and I know it is safe because no one can connect up to it at all.

---

### Post by frodon on 2008-04-22
You are not locking the user in one directory in your configuration which is what sound unsafe for me as the user will be able to browse your whole system what in general users want to avoid, but maybe here it is the purpose of your FTP server.

---

### Post by bneese on 2008-04-25
I am trying to get proftpd to work with RSA/Radius authentication. Do any of you have any experience with that? I can't seem to find much documentation on it. It might also be that I am a Linux newbie. Please help if you can. Thanks

---

### Post by clparker on 2008-04-27
All These Steps Should Work Just Fine In Hardy W/O Any Trouble?

---

### Post by tk0 on 2008-04-28
First off great tutorial...
Well Im new to Ubuntu but I think Im making the transition nicely.

Where to begin... Ive used GPROFTPD and worked like a charm and with being behind a router (*worked within and out of my LAN*).. and upload/download/fxp all good, but only thing I didnt like is that it injected allot of useless stuff when compared to the conf used here.

So axed it, and wanted to use a clean conf.. but having issues... cant upload (*used the PassivePort and MasqueradeAddress*) and I have no idea why that is...any help would help.

TIA.


**UPDATE**: I was able to get it to work, just turned out I needed to open port 20-21 instead of just 21... upload/download works great... again thanks for this tut.

---

### Post by plablo09 on 2008-04-29
This is a great tutorial, very helpful.
I've got an issue though:

I can connect to my server from my LAN (and apparently also from outside although I have´nt tested it thoroughly), but only using the ftp client that runs from the dos shell. I cannot connect from other ftp clients (I've tried filezilla and fireftp). Any help would be much appreciated.

I'll attach my proftpd.conf and the Filezilla log



Thanks

---

### Post by Giak on 2008-05-06
I've set my home directory to /home/myuser, so that's what I see when I log in. I've also added /home/myuser to the folders in GroFTPD, as well as /media/My Book. However, I can't see the folders there when I log in. Any idea why?

---

### Post by rybaxs on 2008-05-06
user@user-desktop:/home/FTP-shared$ sudo /etc/init.d/proftpd start
 * Starting ftp server proftpd                                           [fail] 


i configure the proftpd and followed all instructions. but 
my Ubuntu gutsy gibbon 7.10 ftp always [fail] when i start the ftp server.

---

### Post by rybaxs on 2008-05-06
it works! thanks.. ive just gedit a wrong file.

---

### Post by tk0 on 2008-05-07
> **frodon said:**
> This is a small exemple on how avoid **user2** to enter in the download directory.
In this case 2 users have been created (userftp and user2) and each one have its own alias.
This exemple will allow userftp to see all the shared directory and avoid user2 to use the dowload directory, (i give you only the directory section) : ```
#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
AllowUser user2
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
		Order Allow,Deny
		AllowUser userftp
		AllowUser user2 
		Deny ALL
	</Limit>
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
		Order Allow,Deny
		AllowUser userftp
		Deny ALL
	</Limit>
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
        <Limit ALL>
		Order Allow,Deny
		AllowUser userftp
		AllowUser user2 
		Deny ALL
	</Limit>
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
```

was wonder how can this be done with "virtual users" using a passwd file? is it possible? I would like to have the upload user only have axx to the upload directory, while the rest of the users can have axx to both download/upload directories..

---

### Post by frodon on 2008-05-07
Yes it is possible, virtual users are supposed to work the same way than normal users. Also the way i propose to restrict the access is not the only one.

Good luck.

---

### Post by tk0 on 2008-05-07
> **frodon said:**
> Yes it is possible, virtual users are supposed to work the same way than normal users. Also the way i propose to restrict the access is not the only one.

Good luck.

not to be a lazyass or anything but you think you might be able to point in that direction.. cuz I tried they way you outlined but was unsuccessful unless there are specific directives that need to be in my config.. 

if you dont mind to just look over my config and see if all is up to snuff, cuz users can connect and all just trying to lock the upload user to just the upload dir while everyone else can have axx to both dirs.

```

Include /etc/proftpd/modules.conf
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 
AllowOverwrite on
AuthAliasOnly off

# Choose here the user alias you want !!!!
#UserAlias upload userftp

ServerAdmin	root@localhost
AllowForeignAddress	on

ServerName			"kMHFTP"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer		300
TimeoutStalled			600
TimeoutIdle			120
TimeoutLogin			300

#DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

AuthOrder mod_auth_file.c
AuthUserFile /etc/proftpd/passwd
#AuthGroupFile /etc/proftpd/ftpd.group

# I don't choose to use /etc/ftpusers file (set inside the users you want 
#to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on



# Uncomment this if you are using NIS or LDAP to retrieve passwords:
PersistentPasswd		off

# Uncomment this if you would use TLS module:
#TLSEngine 			on

# Uncomment this if you would use quota module:
#Quotas				on

# Uncomment this if you would use ratio module:
#Ratios				on

# Port 21 is the standard FTP port, so don't use it for security reasons 
#(choose here the port you want)
Port				31337
#Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

DirFakeUser	on	~

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
#AllowOverwrite			on

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
Allow from all
#AllowUser upload
#AllowUser von
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD MACB>
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

    	<Limit STOR CWD MKD RETR>
      	AllowAll
    	</Limit>
</Directory>

# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
#DelayEngine 			off

MasqueradeAddress	mysite.dyndns.org

# These ports should be safe...
PassivePorts 31337 31437

UseReverseDNS off
IdentLookups off
UseIPv6	off

DisplayConnect	/etc/welcome.msg


```

---

### Post by frodon on 2008-05-07
You are not filtering any user in your proftpd.conf so i don't really understand what you tried.
Basically you allow any valid user to login and that's what you FTP server do allowing all users in all the available FTP directories.

To perform a per directory user access you must add *<Limit LOGIN>* commands in each *<Directory ******>* section as in the example in the first post.

---

### Post by tk0 on 2008-05-07
> **frodon said:**
> You are not filtering any user in your proftpd.conf so i don't really understand what you tried.
Basically you allow any valid user to login and that's what you FTP server do allowing all users in all the available FTP directories.

To perform a per directory user access you must add *<Limit LOGIN>* commands in each *<Directory ******>* section as in the example in the first post.

Thanks a bunch frodon!!! I did the *<Limit ALL>* for each directory and i commented all lines of the *<Limit LOGIN>* and was able to keep *upload* from cdup out of upload/ dir.. not sure if thats right but it worked *shrugs*... and this could also work with groups, in case the user base is bigger than just a few users?

```

#VALID LOGINS
#<Limit LOGIN>
#Allow from all
#AllowUser upload
#AllowUser von
#DenyALL
#</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
	<Limit ALL>
		Order Allow,Deny
		AllowUser von
		Deny ALL
	</Limit>
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD MACB>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
	<Limit ALL>
		Order Allow,Deny
		AllowUser von
		Deny ALL
	</Limit>
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit ALL>
		Order Allow,Deny
		AllowUser von
		AllowUser upload
		Deny ALL
	</Limit>
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD RETR>
      	AllowAll
    	</Limit>
</Directory>

```

---

### Post by yawnzzzz on 2008-05-07
Great tutorial, but for some reason when I log in using an FTP client it appears to take me to the wrong directory.  It shows the directory as just "/" and won't let me do anything.  Any help would be appreciated.  I've added all of the directories.  Here's my config file:

```
AllowOverwrite on
AuthAliasOnly on

UserAlias music userftp

ServerName      "brianserver"
ServerType      standalone
DeferWelcome    on

MultilineRFC2228        on
DefaultServer           on
ShowSymlinks            off

TimeoutNoTransfer       600
TimeoutStalled          100
TimeoutIdle             2200

DisplayChdir    .message
ListOptions             "-1"

RequireValidShell       off

TimeoutLogin            20
RootLogin               off

ExtendedLog             /var/log/ftp.log
TransferLog             /var/log/xfer.log
SystemLog               /var/log/syslog.log

UseFtpUsers             off

AllowStoreRestart       on

Port                    1980

MaxInstances            8

User                    nobody
Group                   nogroup

Umask                   022     022

PersistentPasswd        off

MaxClients              8
MaxClientsPerHost       8
MaxClientsPerUser       8
MaxHostsPerUser         8

AccessGrantMsg          "welcome!!!"
ServerIdent             on      "you're at home"

DefaultRoot             /home/FTP-shared

DefaultRoot             ~

MaxLoginAttempts        5

<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022       022
AllowOverwrite  off
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

<Directory /home/FTP-shared/download/>
Umask 022       022
AllowOverwrite  off
        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

<Directory /home/FTP-shared/upload/>
Umask 022       022
AllowOverwrite on
        <Limit READ RMD DELE>
        DenyAll
        </Limit>

        <Limit STOR CWD MKD>
        AllowAll
        </Limit>
</Directory>

```

---

### Post by qingrenjyf on 2008-05-08
Hi,frodon
    I tried the way you say(Create user through the GUI) but got a 530 login error...I just use the default conf file you provided,and I don't know what is wrong.Could you please give me a hand?Thx a lot.

---

### Post by frodon on 2008-05-08
@tk0, i think it's even more safe to keep also a general *<Limit LOGIN>* section (the one you had previously before all your *<Directory ****>* section.

@yawnzzzz, i would say that you user may not have the right home directory, anyway i think keeping only the *DefaultRoot     /home/FTP-shared* line would be enough. Now that i look at it it seems redundant to me as "DefaultRoot  ~" says to lock the user connected in his home directory.

@qingrenjyf, In this case i would try to change the password several time and also using CLI (sudo passwd userftp).

---

### Post by yawnzzzz on 2008-05-08
> **frodon said:**
> 
@yawnzzzz, i would say that you user may not have the right home directory, anyway i think keeping only the *DefaultRoot     /home/FTP-shared* line would be enough. Now that i look at it it seems redundant to me as "DefaultRoot  ~" says to lock the user connected in his home directory.


The user has the correct home directory.  When I connected from a Mac, it didn't show anything, but when I connected from a PC, it showed 'download' and 'upload' as type 'File' instead of being directories.  I previously had this config file working correctly, and it showed the 'download' and 'upload' as directories.  The only thing I've changed since then is the config file.

I did some more tests by not containing the user in a directory, and it shows every directory as a file type of 'file', which means I can't do anything with it.  Any ideas on this?

---

### Post by vikramsharma on 2008-05-12
I have an ftp server as well as a telnet server running, all of a sudden my ftp server has stopped accepting my password.  I am using the same password to login to Ubuntu and also for the telnet server, only for the ftp access my password is being denied.  Help is appreciated.

---

### Post by frodon on 2008-05-12
> **yawnzzzz said:**
> The only thing I've changed since then is the config file.Then the most important i think, is to remember what you changed in your config file.

---

### Post by yawnzzzz on 2008-05-12
> **frodon said:**
> Then the most important i think, is to remember what you changed in your config file.

It would help if I remembered, but I don't because I changed it multiple times.  Any suggestions on where to start looking?

I believe it would have something to do with user permissions, and I'm having trouble finding the commands to view what user permissions I've set up for my userftp along with the user permissions for the directories.  I followed your tutorial to set them up, but maybe they somehow got changed by another program.

---

### Post by vikramsharma on 2008-05-12
> **vikramsharma said:**
> I have an ftp server as well as a telnet server running, all of a sudden my ftp server has stopped accepting my password.  I am using the same password to login to Ubuntu and also for the telnet server, only for the ftp access my password is being denied.  Help is appreciated.

Sorry I forgot to add that I get "530 Login incorrect", eventhough the same password works for logging into my computer and telnet server that I run on my computer.

---

### Post by frodon on 2008-05-13
You should post your proftpd.conf too just in case and detail what you enter to login and what apps you use for FTP.

---

### Post by Vince-0 on 2008-05-13
Hi,

Im running Ubuntu 8.04 Alt_Server, 
I get this error when running the sign.sh server.csr and haven't proceeded any further (my apologies if I'm repeating someone here but I cant find out whats going on):

metonymy@Aurelius:/etc/ftpcert$ ./sign.sh server.csr 
./sign.sh: 33: cannot create ca.config: Permission denied
CA signing: server.csr -> server.crt:
Using configuration from ca.config
error loading the config file 'ca.config'
6382:error:02001002:system library:fopen:No such file or directory:bss_file.c:122:fopen('ca.config','rb')
6382:error:2006D080:BIO routines:BIO_new_file:no such file:bss_file.c:125:
6382:error:0E078072:configuration file routines:DEF_LOAD:no such file:conf_def.c:197:
CA verifying: server.crt <-> CA cert
Error loading file ca.crt
6383:error:02001002:system library:fopen:No such file or directory:bss_file.c:122:fopen('ca.crt','r')
6383:error:2006D080:BIO routines:BIO_new_file:no such file:bss_file.c:125:
6383:error:0B084002:x509 certificate routines:X509_load_cert_crl_file:system lib:by_file.c:274:
usage: verify [-verbose] [-CApath path] [-CAfile file] [-purpose purpose] [-crl_check] [-engine e] cert1 cert2 ...
recognized usages:
	sslclient 	SSL client
	sslserver 	SSL server
	nssslserver	Netscape SSL server
	smimesign 	S/MIME signing
	smimeencrypt	S/MIME encryption
	crlsign   	CRL signing
	any       	Any Purpose
	ocsphelper	OCSP helper

Any suggestions ?
Whoot for this Howto, awesome work!

---

### Post by frodon on 2008-05-13
You need to run this command as root because the /etc directoryis in the root space. So type *sudo ./sign.sh server.csr* instead.

---

### Post by Vince-0 on 2008-05-13
> **frodon said:**
> You need to run this command as root because the /etc directoryis in the root space. So type *sudo ./sign.sh server.csr* instead.

Ok, here's the real problem : 

Enter pass phrase for ./ca.key:
unable to load CA private key
24053:error:06065064:digital envelope routines:EVP_DecryptFinal_ex:bad decrypt:evp_enc.c:461:
24053:error:0906A065:PEM routines:PEM_do_header:bad decrypt:pem_lib.c:425:
CA verifying: server.crt <-> CA cert
Error opening certificate file server.crt
24099:error:02001002:system library:fopen:No such file or directory:bss_file.c:352:fopen('server.crt','r')
24099:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:354:
unable to load certificate

wtf eh ? (thanks for quick reply, much appreciated)

(Nevermind, its working now!)

---

### Post by Georgecooldude on 2008-05-21
This is a good guide.

I've one question. Have had a brief look but couldn't see the answer.

How can I have a single directory with read/write access?

> 
<Directory /home/FTP-shared>
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

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>


Currently I have this but I'd like to setup /home/FTP-shared/read-write/ and do away with seperate upload/download directories as I'll be updating my webserver this way.

Can anyone advise what <directory> commands would be needed?

---

### Post by cschill on 2008-06-01
Hi, 

New to Ubuntu but have some Linux knowledge.  

I have almost the exact same setup as Frodon (btw, thanks for taking the time to write and monitor this useful tutorial).  However, my machine is connected to my cable modem through a NETGEAR wireless router.  I do not think that the router has a hardware firewall.

A few things:
a) I have a dyndns domain name (ricochet.dyndns.info) and ddclient running.
b) In my .config, I have 
            PassivePorts 60000 60100
            MasqueradeAddress ricochet.dyndns.info

When I restart proftpd, I get this message:
cschill-desktop - 127.0.1.1:1980 masquerading as 67.188.114.239

So, I forward port 1980 and 60000-60100 for address 127.0.1.1 in my router setup.

On my ubuntu machine, I can 
ftp 127.0.1.1 1980
and I login fine.

However if I try to do this from my ubuntu desktop:
ftp ricochet.dyndns.info 1980
it just hangs.  Also, I have a mac running os x on the same wireless network.  If I use fugu
to connect, it just hangs for either address (127.0.1.1 or ricochet.dyndns.info).

I attached my config file.  Thanks for taking the time...

BTW, I noticed some posts discussing the /etc/hosts file.  Here is mine:
127.0.0.1	localhost
127.0.1.1	cschill-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Chris

---

### Post by Kulgan on 2008-06-01
Two main problems as I see it...

First, you seem to be using "127.x.x.x" for logging in to the FTP server from other computers. Not good. Use the IP address specified for the active interface in
```
ifconfig
```
when connecting from other computers, at least. This also means changing the port forwards to direct to the right ip (usually 192.168.x.x or 10.0.x.x).

I'm not completely sure about the second one. It depends on my understanding of the ddns client. Which is probably wrong. My understanding is that ddns clients take the ip of the computer they are running on, and send it to dyndns or whatever. So it will be, say... 192.168.0.2... which isn't much space outside the network. It needs to be set up to point to your external IP - at least, if you plan on using it from outside home, which is sort of the purpose of dyndns. The client should therefore be running on the device that gives you your IP address - ie, your modem. 
An alternative to this would be to set up the server so that it runs a script hosted somewhere else - a php script, say, that updates a file with the $_SERVER['REMOTE_ADDR'] var or something - and stick and entry for it in chrontabs...

---

### Post by sotoskawasaki on 2008-06-04
Hey, this is an excellent tutorial you got there. Thanks! 
I wanted to ask about the part with the ssl (ftps). Will those commands work with xampp? It uses proftpd as an ftp server. I would really want to enable ssl with my ftp server. Again thanks!

---

### Post by haryoh on 2008-06-06
I followed your tutorials and had no problems all through but when I tried to access the ftp with filezilla, mozilla, and IE6, it gives me time out on all connection types.

I have attached a copy of my proftpd.conf in the message

---

### Post by frodon on 2008-06-06
@haryoh, you are more likely to have firewall/router issues.

---

### Post by haryoh on 2008-06-06
I do have a PROXY server (squid + dansguardian)  up and running. I added the ports both SSL 21 and safe ports 21 and also on my router, I already have port 21 opened. so what do you think I'm doing wrong?

Thanks. your response would be appreciated.

---

### Post by haryoh on 2008-06-06
Is my configuration setup ok.

---

### Post by frodon on 2008-06-06
Your config seems ok, as i told you timeout issues are in general the indicator of network issue (firewall, router, port forwarding and so on).
I think there's something in your home network preventing the FTP server to accept incoming connections.

---

### Post by haryoh on 2008-06-06
I will look into it for am still at work. I I have a  windows server 2003 running in the back ground but the internal IP is been blocked and I haven't even set up the NFS or SAMBA on my server that will be conflicting the WIN 2003.

like I said I will look into it and if I come up with anything, I will let you know.

Good tutorial. it's perfect. I had to tweak somethings in though..

---

### Post by DaveTheAve on 2008-06-06
I'm getting the following error on Kubuntu Hardy (KDE 3) using the gproftpd "guide":
>  - warning: unable to determine IP address of 'devlon'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'


My Config is:
> ServerType standalone
DefaultServer on
Umask 022
ServerName "0.0.0.0"
ServerIdent on "Devlon"
ServerAdmin [email]David@Neoelite-Consulting.com[/email]
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49149 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 0
TransferRate STOR 0
TransferRate STOU 0
TransferRate APPE 0
SystemLog /var/log/secure
RequireValidShell off
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_homedir_path /var/ftp
#gp_html_path /var/www/html/ftp.htm
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
</IfModule>
<IfModule mod_ratio.c>
Ratios off
SaveRatios off
RatioFile "/restricted/proftpd_ratios"
RatioTempFile "/restricted/proftpd_ratios_temp"
CwdRatioMsg "Please upload first!"
FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
LeechRatioMsg "Your ratio is unlimited."
</IfModule>
<Limit LOGIN>
  AllowUser david
  DenyALL
</Limit>

<Anonymous /var/ftp>
User david
Group david
AnonRequirePassword on
MaxClients 3 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Anonymous>



---

### Post by haryoh on 2008-06-06
check your proftpd.config and make sure you are not missing anything. The error you could get is TIME OUT ERROR when you setup proftpd. Can you attach your configuration here?

---

### Post by frodon on 2008-06-06
> **DaveTheAve said:**
> I'm getting the following error on Kubuntu Hardy (KDE 3) using the gproftpd "guide":


My Config is:Your computer name *devlon* is not defined in your /etc/hosts file therefore the FTP server can't resolve it.

If you don't have the following or something similar in your /etc/hosts file then add it and it should solve your issue :
```
127.0.1.1	devlon
```

---

### Post by DaveTheAve on 2008-06-06
Haryoh, Are you responding to me? If so I already posted my error and my config.

frodon you guru you! Thanks for that, everything works now. Finally I can access my PHP development files from the University.

---

### Post by haryoh on 2008-06-06
> Haryoh, Are you responding to me? If so I already posted my error and my config.

Ok.. Fordon is right.
[COLOR="Red"]
ServerName "0.0.0.0"
ServerIdent on "Devlon"[/COLOR]

Devlon needs to resolve ServerName or you will continue to get the error.
Also make sure in /etc/hosts that everything is configured to work with your box. I just have a rough example below

```
$cat /etc/hosts

127.0.0.1       localhost
127.0.1.1       Devlon

192.168.0.3 Devlonbox

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by haryoh on 2008-06-07
Hello Frodon,

It's working now. there was nothing my firewall. I turned off my proxy and my windows 2003 server and nothing.

But when I open the passive ports as directed in [quick guide]("http://www.proftpd.org/localsite/Userguide/linked/x862.html"), everything worked fine.

Thanks for this, now I can bind it with my /var/www and work on the security part of it. 

Thanks to all people that participated in this great thread. my own HOW TO is coming soon.

---

### Post by frodon on 2008-06-08
Yep, i should have thought to passive ports, some other users have reported this to be a mandatory step when using NAT and domain names.

Glad you got all working, good FTP server is a must to have to access his website and manage it remotely.

If you have suggestions about this tutorial or want me to link one of yours related to the topic feel free to contact me by PM.

---

### Post by haryoh on 2008-06-11
No problem Frodon. Thanks again.

---

### Post by runesvend on 2008-06-14
Thankyou for this useful guide.

I'm experiencing one problem. If a user logs into my FTP server and uploads a file in the upload directory I have no problem deleting the file locally on my Ubuntu machine when I'm logged in as my usual user (non-root). But when a user logged in to the FTP creates a directory in the upload directory and uploads a file in *that* I can't delete the file created.

How come this differs from a file in the "root" upload-directory? And is there a way to change it?

Here's my proftpd.conf:

```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				on

MasqueradeAddress		<my-ip>

PassivePorts			60000 65534

ServerName			"RunesFTP"
ServerType			standalone
DeferWelcome			on

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200
TimeoutLogin			20

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

RootLogin 			off

#DenyFilter			\*.*/

UseFtpUsers			off

AccessGrantMsg			"Hej hej !!!"

AllowForeignAddress		on

DefaultRoot			/media/sdb4/ftp

# Use this to jail all users in their homes 
#DefaultRoot			~

MaxLoginAttempts		5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
RequireValidShell		off

# Port 21 is the standard FTP port.
Port				1986

# Allow to restart a download
AllowStoreRestart		on

# Allow to restart an upload
AllowRetrieveRestart		on

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress		1.2.3.4

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
PersistentPasswd		off

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile			off

# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend 
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
#<IfModule mod_sql.c>
# SQLBackend			mysql
#</IfModule>

ExtendedLog /var/log/proftpd/extdftp.log
TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_tls.c>
TLSEngine off
</IfModule>

<IfModule mod_quota.c>
QuotaEngine on
</IfModule>

<IfModule mod_ratio.c>
Ratios on
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        on
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine on
</IfModule>

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
UserAlias			mrftp userftp


<Directory /media/sdb4/ftp>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /media/sdb4/ftp/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /media/sdb4/ftp/upload/*>
Umask 022 022
AllowOverwrite on
	<Limit RMD DELE>	
	DenyAll
	</Limit>

	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
```

All input is appreciated!

EDIT: I *think* I've solved this by changing the Umask of the upload directory from "022 022" to "022 000". I'm not sure this is the correct solution though so I'd still very much appreciate any feedback on this.

---

### Post by frodon on 2008-06-14
Umask is as you guessed something you can set differently depending on what is more convenient for you. I don't see any particular security risk with the modification you did.

---

### Post by kira_yamato on 2008-06-14
I do have install Ubuntu Server Hardy, FTP server with proftpd, i want to use SSL to secure data transmission, but if in the TLS.log i choose TLSRequired ON, i don't see my directory...it's failed somehow..

---

### Post by runesvend on 2008-06-14
Cool, thanks for the heads up frodon. I guess I fixed it myself then :)

kira_yamato, if you are using the proftpd from the repositories, TLS isn't an option sadly. Try running this command:

```
proftpd -l
```

if mod_tls.c isn't amongst the output you have to compile proftpd yourself. But don't worry it's not hard at all. Take a look at this guide:

[http://www.troublenow.org/?p=6](http://www.troublenow.org/?p=6)

For it to work you have to add the following arguments to the configure script in order to match the directories proftpd has already been installed in by apt-get:

./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var --with-modules=mod_tls


EDIT: Wait a minute. I'm just now finding out where the correct directories are. THe above is not correct.

---

### Post by frodon on 2008-06-14
Since proftp version 1.3 modules are implemented in a different way, the version of proftp in the repositories include mod_tls but you must uncomment it in Include /etc/proftpd/modules.conf and add the following line in your proftpd.conf file to use it :
```
Include /etc/proftpd/modules.conf
```

@kira_yamato, details the steps you followed to set the TLS encrytion and how your tried to login your FTPO server (which client, how it is configured and so on).

---

### Post by jorge.maravi on 2008-06-24
This How to es great but a little bit outdated...
I tried to install the proftpd server and the config file looks different. Is there another tutorial for the latest proftpd latest version?

---

### Post by frodon on 2008-06-24
Outaded based on what ?

This tutorial is and has always been up to date, it does what the title says in a safe way. This is not the default config, default config set anonimous login which is not the purpose of this tutorial.

---

### Post by jorge.maravi on 2008-06-24
Frodon
The config file in your post on October 20th, 2005 is different to the config file i saw yesterday. There are many fields are not there.
The config file I saw yesterday looks like runesvend posted 1 week ago

---

### Post by frodon on 2008-06-24
I thought one second you were going to base your opinion on serious arguments.

The config file in first post is a customized config file **_[COLOR="Red"]last edited in october 2007[/COLOR]_** as written explicitely at the bottom of the first post therefore it is different from the default config file which do not perform user access restriction and per directory access.

Please lets not steer the thread off topic now, if you have valid arguments/suggesstion/enhancement to propose they are of course more than welcome.

---

### Post by jorge.maravi on 2008-06-24
Hi Frodon
I am trying to use TLS with the proftpd server and when i ran proftpd -l it doesn't show that the module mod_tls was loaded. I checked the modules.conf and It seems that it should load. The line: 
"LoadModule mod_tls.c" is not commented out, when i ran the proftpd -td5 it says:"My-Server - mod_tls/2.1.1: passphrase locked into memory".

I am having trouble trying to connect using the sftp protocol from a client to this server, but when I use the FTP protocol it works

---

### Post by frodon on 2008-06-25
Modules in latest proftp versions are handled in modules.conf so you did the right thing uncommenting mod_tls in the file but don't forget to add "Include /etc/proftpd/modules.conf" somewhere at the beginning of your file to make your server parsing the module configuration.

Be careful FTP + TLS encryption is not SFTP, SFTP is connecting to a ssh server through FTP. FTP + TLS encryption is commonly called FTPS and in filezilla (a FTP client i advice you) it is called FTPES.

---

### Post by jorge.maravi on 2008-06-25
Ok Frodon, my /etc/proftpd/proftpd.conf file has the line "Include /etc/proftpd/modules.conf" uncommented.
So, it is correct to say if i try to connect to my ftp server (that is using the default port 21)with the sftp protocol. It will work?
I understand the sftp protocol points to port 22 instead port 21

---

### Post by frodon on 2008-06-25
No it won't as my guide is for FTP over TLS encryption not SFTP which is FTP in SSH tunnel and it is why it use port 22 as port 22 is the default port for SSH.
You must have a FTPS compliant FTP client to login your server if you use TLS encription.

---

### Post by jorge.maravi on 2008-06-25
Ok thanks Frodon i will try with filezilla

---

### Post by jorge.maravi on 2008-06-25
Hey Frodon
I just downloaded the filezilla client and it works great with the FTPES protocol....

Thanks for your help, and sorry for the initial post about the how-to was no up-to-date, actually it is and is great, sorry Frodo my bad :( 

Only a question: with the FTPES protocol the authentication process will be encripted, but what about the data transmitted. is that encrypted too?

Thanks

---

### Post by frodon on 2008-06-25
np, you're welcome :)

With TLS encription all is encripted (authentification + datas) so you are safe transfering sensible datas with your FTP server. You can even force users to use FTPES using "TLSRequired on" but your friends will have to find a FTPES compliant client like filezilla.

---

### Post by jorge.maravi on 2008-06-25
Hi frodon if I am going to use a masquerade address (nat) in the proftpd.conf file i should add the fields: MasqueradeAddress and PassivePorts right?
The MasqueradeAddress should be the public IP address (IP in the internet) right?

---

### Post by frodon on 2008-06-25
Yes it should be your IP or domain name, however i'm not expert on this as i don't have NAT configuration myself.

---

### Post by sotoskawasaki on 2008-06-25
Ok, I followed your tutorial and everything is working just fine! Great tut!!
I am using xampp 1.6.6 on Kubuntu 8.04. Thanks..

---

### Post by arvvvs on 2008-06-29
I can't connect using FileZilla and i've used everything I can.  I have tried other clients and can't connect 
this is my thing:
ServerType standalone
DefaultServer on
Umask 022
ServerName "192.168.1.3"
ServerIdent off "My FTPD"
ServerAdmin [email]arvvvs@gmail.com[/email]
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 30
TransferRate STOR 40
TransferRate STOU 40
TransferRate APPE 40
SystemLog /var/log/secure
RequireValidShell off
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_homedir_path /var/ftp
#gp_html_path /var/www/html/ftp.htm
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
</IfModule>
<IfModule mod_ratio.c>
Ratios off
SaveRatios off
RatioFile "/restricted/proftpd_ratios"
RatioTempFile "/restricted/proftpd_ratios_temp"
CwdRatioMsg "Please upload first!"
FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
LeechRatioMsg "Your ratio is unlimited."
</IfModule>
<Limit LOGIN>
  AllowUser userftp
  AllowUser userftp
  AllowUser arvvvs
  DenyALL
</Limit>

<Anonymous /var/ftp>
User userftp
Group FTP
AnonRequirePassword on
MaxClients 3 "The server is full, hosting %m users"
DisplayLogin welcome.msg
AllowOverwrite off
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
<Limit RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
 DenyAll
</Limit>
</Anonymous>

<Anonymous /home/FTP>
User userftp
Group FTP
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
AllowOverwrite off
<Limit LIST NLST  RETR  SITE_CHMOD  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>

<Anonymous /home/FTP>
User arvvvs
Group FTP
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  RETR  SITE_CHMOD  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>

---

### Post by jorge.maravi on 2008-07-02
Hi
I have my ftp server connected to the internet when i try to connect using the ftp protocol it works fine, but when i try to use the FTPES protocol it fails. This is my log's output in my client:
13:42:19	Trace:	ControlSocket.cpp(1057): CRealControlSocket::ContinueConnect(0p22dcc8) m_pEngine=0p128f6d8   caller=0p1332b60
13:42:19	Status:	Connecting to <my-ip-address>:21...
13:42:19	Status:	Connection established, waiting for welcome message...
13:42:33	Trace:	CFtpControlSocket::OnReceive()
13:42:33	Response:	220 ProFTPD 1.3.0 Server ready.
13:42:33	Trace:	CFtpControlSocket::SendNextCommand()
13:42:33	Command:	AUTH TLS
13:42:33	Trace:	CFtpControlSocket::OnReceive()
13:42:33	Response:	234 AUTH TLS successful
13:42:33	Status:	Initializing TLS...
13:42:33	Trace:	CTlsSocket::Handshake()
13:42:33	Trace:	CFtpControlSocket::SendNextCommand()
13:42:33	Command:	USER <user-name>
13:42:34	Trace:	CTlsSocket::OnSocketEvent(): wxSOCKET_LOST received
13:42:34	Trace:	CRealControlSocket::OnClose()
13:42:34	Trace:	CFtpControlSocket::ResetOperation(66)
13:42:34	Trace:	CControlSocket::ResetOperation(66)
13:42:34	Error:	Could not connect to server
13:42:34	Status:	Waiting to retry...

I checked the proftpd mini how-to and they said there is a problem with TSL and NAT and that is fixable if you add this in the config file: TLSRequired auth+data(to use the Clear Command Channel) I tried to add this in my config file but it threw an error when i restart the daemon.

Is there any way to force this in a proftod server ver 1.3.0?

Thanks

---

### Post by jorge.maravi on 2008-07-09
frodon u there?

---

### Post by frodon on 2008-07-10
Yep, but there's nothing i can do for you, i don't use NAT on my home config. In your case i would try at least once to regenerate the rsa key.

Maybe some users who used this howto and who use a NAT can help you.

---

### Post by jorge.maravi on 2008-07-10
I already figured out the problem. It was a port problem in my dsl modem.
If I want that my internal clients access to my FTP server behind my dsl modem i have to create a virtual server right?

Why when i try to connect from my internal IP addresses to my internet IP address my clients fail to connect to the FTP server?

---

### Post by frodon on 2008-07-10
You may find some useful infos in this post :
[http://ubuntuforums.org/showpost.php?p=680702&postcount=81](http://ubuntuforums.org/showpost.php?p=680702&postcount=81)

---

### Post by jorge.maravi on 2008-07-10
I don't have problems with my router/DSL modem anymore, After using the directive Ipmasquerade I cannot connect to my internal IP address anymore, I am not sure if I have to set up a virtual server section in my proftpd.conf file

In don't understand either why when I tried to connect to the ftp server from an internal IP address using the public internet address it fails....

---

### Post by frodon on 2008-07-11
You external IP (i guess IPv4) is not related to s apecific computer of your local network therefor if you didn't set any rules to redirect the needed ports to your computer then the FTP frame is more likely to be lost.
Check your router configuration and that FTP ports are well redirected to the computer hosting the FTP server then to test from the internet maybe just call a friend.

---

### Post by jorge.maravi on 2008-07-11
I am lost now, when i tried to connect from another complete different IP address (ie my house) It works, I already forwarded the ports and passive ports to the FTP's internal IP address it work fine, I am using the masquerading directive. The problem is when an internal client from the same FTP server's network try to connect to the FTP using the external IP address (internet address)it fails

---

### Post by frodon on 2008-07-11
You should not use your external IP when communicating within your localnetwork but the IP of the computer directly.

---

### Post by jorge.maravi on 2008-07-11
i tried that, using the internal IP address in my network, but it fails when is listing the directories.
that's the reason i ask if I need to create a field for a virtual server in my conf file (using the FTP's internal address and without the maquerading directive)

---

### Post by fridaythe14th on 2008-07-31
Been making various attempts of setting up an ftp server myself but failed. This was a great guide so thank you!

---

### Post by Jordanwb on 2008-08-09
Okay with section C, I set it up okay, but do I need to store a file on my computer if I want to login using SFTP?

---

### Post by Anthony M on 2008-08-12
Im also having the problem where I can login to the FTP server from all computers on same home network as the server but not from any remote computers.  I have opened, on my router, port 21 and the range of passive ports.  

When attempting to connect from a remote computer, filezilla simply says "unable to connect"....

What else to I need to enable in gproftpd?

Thanks!

---

### Post by Jordanwb on 2008-08-12
> **Anthony M said:**
> I have opened, on my router, port 21 and the range of passive ports.

Did you set the router to forward to the right IP?

---

### Post by anlayne on 2008-08-28
I know there are a lot of 530 Login failed. questions here, and I have looked through them and tried many things. I have changed the password for my ftpuser (changed from the original userftp) many times through both the GUI and CLI. I do not know how to confirm the file permissions, but I have gone back and reassigned them. When I login, I make sure to use the user name (tst) assigned by UserAlias in proftpd.conf (below) and not the UNIX user name. Still, my 530 problem persists. Any help would be appreciated.

Also, a prompt reply would be appreciated, because I am going overseas in a few days and want to use the server to dump files onto my computer.

Thanks in advance.

```

# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias tst ftpuser

ServerName			"adamserver"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port				1981

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/ftpuser

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/ftpuser>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/ftpuser/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/ftpuser/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

```

---

### Post by frodon on 2008-08-28
Did you tried to login on the same computer that runs the server or from another one.

---

### Post by anlayne on 2008-08-28
I tried to login from the same machine. I am on a LAN behind a router and I understand the complications about access from outside my LAN, but as far as I know, that should not affect this. Also, I am able to communicate with the ftp server, just not login. The full input/output looks like this:

```
adam@adam-desktop:~$ ftp 192.168.1.220 1981
Connected to 192.168.1.220.
220 you're at home
Name (192.168.1.220:adam): tst
331 Password required for tst
Password:
530 Login incorrect.
Login failed.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> quit
221 Goodbye.
```

---

### Post by frodon on 2008-08-29
So you tried from the same computer that runs the server because it can be firewall issue too on either computer. Try with other ftp clients than ftp command line too. You can test that the password is working trying to login your session with your ftpuser directly, that would exclude any password issue on the user creation level.

---

### Post by herot on 2008-08-29
I am using proftp and no matter what i set the allowed transfer rates at my friends and i can only download files from my server at about 50-60kbs i have 384kbs upload speed in my plan with bellsouth. There are no other problems with the server other than the speed. The bellsouth speed test returns the correct values. Bellsouth told me they do not cap or throttle any ports my server might be using.

I am not using passive ftp.

What can I do to speed up the rate at which my server uploads to clients? I am referring to the file transfer speed, logins and listings are all fine.

---

### Post by frodon on 2008-08-29
380kbits/s ~= 50kbytes/s, ISPs almost always give you bandwidth information in kbits whereas everything in the computer world is displayed in kbytes.

---

### Post by anlayne on 2008-08-29
I tried logging in to the session with ftpuser and it completed (although I got a "The computer administrator has disabled your account" or something equivalent, probably because the user has no privileges). Could this be the problem?

I am trying from the same machine, so firewall shouldn't be a problem, but if it is, how do I add an exception to iptables? (ie. can I add an exception just for proftpd on a certain port?)

I tried connecting from Firefox and gFTP and both communicate with the server (I get 220 and 331), but still get 530; exactly the same as with the command line.

Thanks for all your help.

---

### Post by herot on 2008-08-29
ugh! i see... i guess my only option is to try and upgrade my plan... 

Any other suggestions for faster file sharing?? anybody aware of off site server services?

---

### Post by frodon on 2008-08-29
If you have iptables configured and try to login from the computer that runs the server the only thing you need is to allow loopback interface (connection from yourself). If you never played with iptables or firewall it should be allowed already.

For the moment you seem to have done all the things well so i have no real idea of what is wrong in your config.

---

### Post by TheRazer on 2008-09-06
I hawe a problem... 
my proftpd server WORKS...
but...
wen i login on nucftp ewrything is good... but with razer i cane make a dir... but i cant se annything. not the dir i made or nothing... but wen i check the server the new dir i made is there... and my ftp client say directory identifier unavailable...

```

# To really apply changes reload proftpd after modifications.
AllowOverwrite on

ServerName                      "razer"
ServerType                      standalone
DeferWelcome                    on

MasqueradeAddress razer
MasqueradeAddress xxx.xxx.xxx.xxx

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    off

PassivePorts 60000 60100

UseReverseDNS off
IdentLookups off

RequireValidShell               off

RootLogin                       off

# It's better for debug to create log files ;-)
ExtendedLog                     /var/log/ftp.log
TransferLog                     /var/log/xferlog
SystemLog                       /var/log/syslog.log

#DenyFilter                     \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart               on
# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port                            23

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 30

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           077

PersistentPasswd                off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

MaxLoginAttempts    5
DefaultRoot ~

<Limit LOGIN>
AllowUser razer
AllowUser nucftp
Deny ALL
</Limit>

<Limit ALL>
 Order Allow,Deny
 AllowUser razer
 Deny ALL
</Limit>

<Limit READ STOR RETR REST PWD NLST LIST DELE CWD>
 AllowUser nucftp
 Deny ALL
</Limit>


```


and this made me get 530 ALL THE TIME but wen i removed it all is fine...
```

AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias sauron userftp


```

---

### Post by Dayvo on 2008-10-02
I'm really struggling to get TLS with gproftpd, I installed proftpd and gproftpd just like at the begininng of the tutorial and followed all the instructions to create the tls certificates and stuff but it seems as though the module is not being loaded at all. I can connect to the FTP fine without TLS, but when I select Auth TLS In flashFXP i get:

[R] AUTH TLS
[R] 500 AUTH not understood
[R] Failed SSL/TLS negotiation, disconnected
[R] Connection failed (Connection lost)

I checked the tls log but it is blank ( The file/ path doesn't even exist!)

Can anyone point me in the right direction?

This is my proftpd.conf file:

Include /etc/proftpd/modules.conf

ServerType standalone
DefaultServer on
Umask 022
ServerName "xxx.xxx.xxx.xxx"
ServerIdent on "SupaBox"
ServerAdmin [email]Admin@this.domain.topd[/email]omain
IdentLookups off
UseReverseDNS off
Port 443
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 600
TimeoutIdle 600
DisplayLogin welcome.msg
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 1100
TransferRate STOR 1100
TransferRate STOU 1100
TransferRate APPE 1100
SystemLog /var/log/secure
RequireValidShell off
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_homedir_path /var/ftp
#gp_html_path /var/www/html/ftp.htm
#gp_welcome_name welcome.msg

<IfModule mod_ratio.c>
Ratios off
SaveRatios off
RatioFile "/restricted/proftpd_ratios"
RatioTempFile "/restricted/proftpd_ratios_temp"
CwdRatioMsg "Please upload first!"
FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
LeechRatioMsg "Your ratio is unlimited."
</IfModule>
<Limit LOGIN>
  AllowUser admin
  DenyALL
</Limit>

<IfModule mod_tls.c>
    TLSEngine on
    TLSLog /var/ftpd/tls.log
    TLSProtocol TLSv1

    # Are clients required to use FTP over TLS when talking to this server?
    TLSRequired on

    # Server's certificate
    TLSRSACertificateFile /etc/ftpcert/server.crt
    TLSRSACertificateKeyFile /etc/ftpcert/server.key

    # CA the server trusts
    TLSCACertificateFile /etc/ftpcert/ca.crt

    # Authenticate clients that want to use FTP over TLS?
    TLSVerifyClient off
</IfModule>

<Anonymous /home/admin>
User admin
Group ftp
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
AllowOverwrite off
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit SITE  SITE_CHMOD  SITE_CHGRP >
 DenyAll
</Limit>
</Anonymous>

---

### Post by blithen on 2008-10-04
Never mind 'AuthAliasOnly on'
was 'off'

---

### Post by Sir Jake on 2008-10-04
Where do I change my users password?
Someone else setup proftp with webmin in the config file I can see my username. No clue what my password was setup as. 
Thanks for any help. Jake

---

### Post by blithen on 2008-10-04
> **Sir Jake said:**
> Where do I change my users password?
Someone else setup proftp with webmin in the config file I can see my username. No clue what my password was setup as. 
Thanks for any help. Jake
If you followed frodon's tutorial you change the password by doing...
```
sudo passwd userftp <password here>
```

---

### Post by blithen on 2008-10-05
Now it's just giving me a connection refused. I'm trying to access it from a VMWare virtual server, you know to simulate someone trying to access it from the outside.

---

### Post by AppleSeed666 on 2008-10-06
Hello everyone

I followed these instructions line by line and have setup the proftpd server on my ubuntu desktop. I have a static ip assigned to this pc so i don't have any issues w/ routers. 

Everything seemed to work, however, when i try and go "ftp ipAddress" of the ubuntu box it can't connect. Am i missing something here?

---

### Post by blithen on 2008-10-15
> **AppleSeed666 said:**
> Hello everyone

I followed these instructions line by line and have setup the proftpd server on my ubuntu desktop. I have a static ip assigned to this pc so i don't have any issues w/ routers. 

Everything seemed to work, however, when i try and go "ftp ipAddress" of the ubuntu box it can't connect. Am i missing something here?
Actually yes, if you followed everything correctly you need to connect to the server through a client such as Filezilla. 
```
sudo apt-get install filezilla
```
Then once install run it and then for your host Put your IP address
And well everything else is self explanatory.

---

### Post by scullkrusher on 2008-10-17
When i was setting up my user account I made a typo in the name and didn't realize it. My question is - Is there a way to remove a user account? Is there also a way to change the root directory as well?

---

### Post by frodon on 2008-10-17
Of course there is :)

In the System > Administration menu you should have an item pointing to the user & group window which allows to handle all the user and group stuff.
You can do it using command line too using the "userdel" tool.

---

### Post by scullkrusher on 2008-10-17
Ahh thanks. I was trying to type userdelete rather than userdel. I also find the User and Groups menu easier to use than the terminal commands and it never occurred to me use that for some reason. That would've saved me abunch of time. I've been using Ubuntu for a week now and I've learned alot so far and things are going better than I thought they would. Just a few minor hang-ups like these.

Thanks for the help.

---

### Post by angelkiller on 2008-10-20
Ok, I followed you guide from the first page and got proftpd set up. Everything *is* working. But there are some things I'd like to change about *how* it works. First, before I used your guide, I was logging into the server (via ftp) with the same user/password that I used to log into the system. I was using whatever proftpd.conf that came installed. (I didn't change anything.) My first question is how safe is that? Now, when logged in as that user, I could go anywhere on the filesystem that I wanted. I liked being able to access everything. How can I do this again?

I'm no linux expert, so keep that in mind. ;-) Thanks!

---

### Post by frodon on 2008-10-21
If you mean access your whole system nothing is more dangerous and i would strongly advice you ssh over FTP for this use.

Having said this you only need to set the defaultroot directory to /

---

### Post by angelkiller on 2008-10-21
Thanks for the response. So giving access to / over FTP is really unsafe. Why? I enabled TLS/SSL encryption from the guide. Is this secure enough? If not, exactly to I use SSH and FTP together?

Now you also said that to give me access to / all I had to do was change defaultroot to /. I did this but nothing seems to have changed. / is my default folder, but the only folders I have access to are still the upload and download folders. Is there something else I have to change?

Thanks again.

---

### Post by frodon on 2008-10-22
Have you modified both ? :
```
# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~
```Giving access to / is unsafe by nature and in general users giving access to / want to remotely administrate their computer that's why ssh is more used when you want full access.

Now about the easiest to crack between FTP with TLS and SHH i don't know but in both cases i strongly recommend you a well definied firewall maybe also protecting you against from brute force attacks and before all strong password :).

---

### Post by Mantecore on 2008-10-24
proftpd is working great, but I have a quick question about the Useful Trick permament mount trick. Here is my /etc/fstab file (I've added the last 3 lines).

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=20d564bc-2e44-42b8-8918-968c182aacb6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=db43db79-44cc-4a20-8e31-6e8be90dd54a none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1 	/media/hd2 ext3 defaults			  0 	 0
/media/hd2/backup/externalHD/My\ Music /media/music vfat bind 0 0
/media/music /home/steve/music vfat bind 0 0

```

but when I boot, the folders don't automatically mount and when I run sudo mount -a I get the output

```

steve@sklesser-server:/media/music$ sudo mount -a
[mntent]: line 13 in /etc/fstab is bad


```

where line 13 is the second to last line. However, when I run sudo mount -o bind it works. Any ideas on what could be causing this? Thank you!

---

### Post by frodon on 2008-10-24
From my first looking i see no biog mistake however i find it strange that you mount a directory in another one to mount again this directory elsewhere, i have never tested the mount -o bind command with 2 layers of bind.

---

### Post by Penteado on 2008-10-26
Hello, i followed the guide. But i cant connect to the ftp server even on LAN. The ftp server is on my desktop and im trying to connect from my laptop. I've enabled the port forwarding to port 21 but still no connection ...
 
   I can see that the service is up and running .

   ```
bruno@bruno-desktop:~$ ps aux | grep proftp 
nobody    7445  0.0  0.1   9908  1604 ?        Ss   11:13   0:00 proftpd: (accepting connections)
```

   I'll paste my proftpd.conf
 
   ```


#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				off

ServerName			"Debian"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayChdir               	.message true
ListOptions                	"-l"

#DenyFilter			\*.*/

# Use this to jail all users in their homes 
DefaultRoot			~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell		off

# Port 21 is the standard FTP port.
Port				21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress		1.2.3.4

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd		off

# This is required to use both PAM-based authentication and local passwords
# AuthOrder			*mod_auth_pam.c mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile			off

# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend 
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
#<IfModule mod_sql.c>
# SQLBackend			mysql
#</IfModule>

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        off
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine off
</IfModule>

#
# Alternative authentication frameworks
#
#Include /etc/proftpd/ldap.conf
#Include /etc/proftpd/sql.conf

#
# This is used for FTPS connections
#
#Include /etc/proftpd/tls.conf

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayFirstChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/bruno/FTP-shared/>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/bruno/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/bruno/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

```
   

 I'm on Hardy , 8.04 2.6.24-21 kernel.

 I'll apreciatte any help.

 Thank You

---

### Post by frodon on 2008-10-26
Could you paste you FTP client log so that we can see the nature of the problem ?

Thanks.

---

### Post by Penteado on 2008-10-26
Log shows a blank, it just hangs when i try to log in. :s
  
    just says : 

    ```

    Looking up : 192.168.1.67
    Trying 192.168.1.67:21
    
```

     I think the problem isnt on the proftpd configuration but something else, because i also tried trough ssh and hangs the same way. I openned both ports on router. Dont know what to do next :/

---

### Post by Penteado on 2008-10-26
I just tried on locahost and it works fine. Besides port forwarding port 21, is there any other issues that block external connections(including LAN) ?

 Note : just notice i cant even ping both machines ( helpful ? )

 Send Note : Have been done some reading altough i couldnt understand much, found some threads talking about iptables and ftp/ssh servers. Doest iptables by default block this kind of services? I never worked with those before, and never changed anything since i installed ubuntu. 

 Thank you in advance

---

### Post by Penteado on 2008-10-26
Ei, I have figured out!

  I'm a complete newbie, but i figured that ubuntu comes with a built in firewall (iptables), have start to read some tutorials and understanding chains and policies. but in the mean time i fount out that firestarter is a frontend to configure iptables, so i've manage to allow ftp / ssh.

  I'm gonna need to understand better iptables for the future, so do you know a good tutorial or documentation?

  I just cant access from an external IP to the server. Any Info ?

  Thank You

---

### Post by frodon on 2008-10-27
I've writen one for beginners if interested :
[http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables](http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables)

---

### Post by Penteado on 2008-10-27
Ye great howto, i've manage to open the ports already. But i cant get people from outside my local network to connect to the ftp server.

   I've read something about passive and active ftp server . But couldnt get any configuration to solve the problem.

   Can you help me in this issue?

   Thank you so much

---

### Post by frodon on 2008-10-27
Read in the iptables tutorial thread from post 169, you will see a user who managed to get all working with passive connections although passive FTP is not mandatory.

Are you using a router ?

---

### Post by Penteado on 2008-10-27
> **frodon said:**
> Read in the iptables tutorial thread from post 169, you will see a user who managed to get all working with passive connections although passive FTP is not mandatory.

Are you using a router ?

yes i am :s

---

### Post by frodon on 2008-10-27
Ok so i trongly advice you to read this post in details :
[http://ubuntuforums.org/showpost.php?p=680702&postcount=81](http://ubuntuforums.org/showpost.php?p=680702&postcount=81)

It explains the steps to follow to get FTP server working through a router on the FTP server config side and on the router side too.

Hope it will answer your questions.

---

### Post by Penteado on 2008-10-27
:)

---

### Post by Penteado on 2008-10-27
> **frodon said:**
> Read in the iptables tutorial thread from post 169, you will see a user who managed to get all working with passive connections although passive FTP is not mandatory.

Are you using a router ?

gonna test and will be back with the result ;)

---

### Post by Penteado on 2008-10-27
Still the same, i used the config provided by that post. got me this error while restarting the service :

  ```
- warning: the DisplayFirstChdir directive is deprecated and will be removed in a future release.  Please use the DisplayChdir directive.

```

   And whats the functionality of MasqueradeAddress ?

   And what this comments means ?

   ```
# These ports should be safe...
    PassivePorts 60000 65535
```

  What im missing ? :(

---

### Post by frodon on 2008-10-28
MasqueradeAddress is mandatory when using a router, here you must put either your domain name or the IP of the router.

PassivePorts command allows to define accurately what port to use if in passive mode.

---

### Post by Penteado on 2008-10-28
Should i port forward the passive ports aswell ?

    Thank you

---

### Post by frodon on 2008-10-28
I don't think so.

---

### Post by Penteado on 2008-10-28
Still no go :s

---

### Post by Penteado on 2008-10-28
heres my proftpd.conf

```

#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 
AllowOverwrite on
AuthAliasOnly off

# Choose here the user alias you want !!!!
UserAlias frbr userftp


ServerName			"Debian"
ServerType			standalone
DeferWelcome			on

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

#DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want 
#to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on



# Uncomment this if you are using NIS or LDAP to retrieve passwords:
PersistentPasswd		off

# Uncomment this if you would use TLS module:
#TLSEngine 			on

# Uncomment this if you would use quota module:
#Quotas				on

# Uncomment this if you would use ratio module:
#Ratios				on

# Port 21 is the standard FTP port, so don't use it for security reasons 
#(choose here the port you want)
Port				1980
#Port				21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			8

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
#AllowOverwrite			on

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
#AllowUser frbr
DenyALL
</Limit>

<Directory /home/FTP-shared>
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

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
#DelayEngine 			off

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayFirstChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

MasqueradeAddress	192.168.1.254

# These ports should be safe...
PassivePorts 60000 65535

UseReverseDNS off
IdentLookups off

```

I'm port forwarding 20,21,1980. 

And using firestarter (iptables fron-end) allowing connections on 21.21.1980

Any clues?

---

### Post by frodon on 2008-10-29
Try to set and configure your FTP server install on port 21, it is way easier in general when having with router, firewall and passive ports.

BTW MasqueradeAddress must be the IP of your router not the IP of your computer on local network.

---

### Post by Sowa on 2008-11-01
hi, i tried to set up a proftpd server with tls (ftps)

my config:

```


# This is a basic ProFTPD configuration file (rename it to
# 'proftpd.conf' for actual use.  It establishes a single server
# and a single anonymous login.  It assumes that you have a user/group
# "nobody" and "ftp" for normal operation and anon.

ServerName                      "FTPS Server"
ServerType                      standalone
DefaultServer                   on

# Port 21 is the standard FTP port.
Port                            21

# Umask 022 is a good standard umask to prevent new dirs and files
# from being group and world writable.
Umask                           022

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd).
MaxInstances                    30

# Set the user and group under which the server will run.
User                            nobody
Group                           nogroup

# To cause every FTP user to be "jailed" (chrooted) into their home
# directory, uncomment this line.
DefaultRoot ~

# Normally, we want files to be overwriteable.
AllowOverwrite          on
AllowRetrieveRestart on
AllowStoreRestart on

# Bar use of SITE CHMOD by default
<Limit SITE_CHMOD>
  DenyAll
</Limit>

# A basic anonymous configuration, no upload directories.  If you do not
# want anonymous users, simply delete this entire <Anonymous> section.
<Anonymous /data/ftp/Pub/Download>
  User                          ftp
  Group                         ftp

  # We want clients to be able to login with "anonymous" as well as "ftp"
  UserAlias                     anonymous ftp
RootLogin off
RequireValidShell off

  # Limit the maximum number of anonymous logins
  MaxClients                    10

  # We want 'welcome.msg' displayed at login, and '.message' displayed
  # in each newly chdired directory.
  DisplayLogin                  welcome.msg
  DisplayChdir                  .message


  # Limit WRITE everywhere in the anonymous chroot
  <Limit WRITE>
    DenyAll
  </Limit>

</Anonymous>

<IfModule mod_tls.c>

#Security (TSL/SSL Layer)
TLSEngine on
TLSLog /var/log/proftpd/tsl.log
TLSProtocol TLSv1
TLSRequired off
TLSRSACertificateFile /etc/proftpd/ftpcert/server.crt
TLSRSACertificateKeyFile /etc/proftpd/ftpcert/server.key

TLSCACertificateFile /etc/proftpd/ftpcert/ca.crt

TLSVerifyClient off
</IfModule>

```

with 
 sudo proftpd -nd5 -c /etc/proftpd/proftpd.conf
i see

> server (xxxxx) - FTP session requested from unknown class
server (xxxxx) - connected - local  : Server IP:21
server (xxxxx) - connected - remote : Remote IP:50594
server (xxxxx) - FTP session opened.
server (xxxxx) - dispatching PRE_CMD command '' to mod_tls
server (xxxxx) - dispatching PRE_CMD command '' to mod_core
server (xxxxx) - dispatching PRE_CMD command '' to mod_core
server (xxxxx) - dispatching LOG_CMD_ERR command '' to mod_log
server (xxxxx) - mod_tls/2.1.2: scrubbing 1 passphrase from memory
server (xxxxx) - FTP session closed.


in the tls_log i get this

> Nov 01 15:08:57 mod_tls/2.1.2[25298]: using default OpenSSL verification locations (see $SSL_CERT_DIR environment variable)
Nov 01 15:09:07 mod_tls/2.1.2[25298]: SSL/TLS required but absent on control channel, denying ^V^C^B command


i am using filezilla 3.1.5 connection with FTPS and normal auth

> - ProFTPD Version 1.3.1

Compiled-in modules:
  mod_core.c
  mod_xfer.c
  mod_auth_unix.c
  mod_auth_file.c
  mod_auth.c
  mod_ls.c
  mod_log.c
  mod_site.c
  mod_delay.c
  mod_tls.c
  mod_cap.c



what did i wrong what can i do?


thanks :)

---

### Post by sykostig on 2008-11-02
Great How-To. Got it all set up now :)

I wonder if its possible for me as "main user" on the computer to save files to Download folder with subfolders. But I only want 1 user to be able to add files there.

---

### Post by frodon on 2008-11-03
Bad idea in general to connect with your main user which have root access especially because he has root access.

Anyway to allow your user it is as simple as adding your user in LIMIT LOGIN section and create an alias for him if you use aliases.

If you want to go further proftp offers you a second way to handle users able to login via virtual users :
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-VirtualUsers.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-VirtualUsers.html)

---

### Post by sykostig on 2008-11-03
> **frodon said:**
> Bad idea in general to connect with your main user which have root access especially because he has root access.

Anyway to allow your user it is as simple as adding your user in LIMIT LOGIN section and create an alias for him if you use aliases.

If you want to go further proftp offers you a second way to handle users able to login via virtual users :
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-VirtualUsers.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-VirtualUsers.html)
Maybe I stated my question a little confusing.
Let's call my main account on my ubuntu box for "bob". I want "bob" to have write and read permission to the /home/FTP-share/download/(including subfolders) without sudo command. Since I will RSS download to that directory.


Edit:
I fixed it with this
```

cd /home
sudo chown -R <username>.<usergrp> FTP-shared

```
without the <> ofc.

---

### Post by frodon on 2008-11-03
Maybe tweak the group and user directive so that files uploaded on the FTP server are owned by the user of your choice.

I think it is where to look.

---

### Post by streetart on 2008-11-05
I had some real problems with this. But I am totally new so I thought maybe I had made a silly mistake. I typed up my problems in the [Beginners Section here]("http://ubuntuforums.org/showthread.php?t=971268#post6107743").

---

### Post by uneo on 2008-11-10
hi i,m totaly newbie to linux & with this tutorial i was able to install gproftp but i want change home directory to /home from /var but can't find they way to do it.:confused:

---

### Post by GoFishy on 2008-11-10
very nice tutorial..

i thank you

---

### Post by metalguy639 on 2008-11-11
I get an error when I try to click on the GUI. I go to "Applications>System Tools>GADADMIN-PROFTPD and I get a box that says:

```
Could Not Launch The Menu Item:

Failed to execute child process "su-to-root" (No such file or directory)
```

How do I get the program to open??

---

### Post by anunnak on 2008-11-12
limit transfer speed /and/  failed transfers
- is there a way to limit speed transfer per group or directory ?
- I have limit MaxClientsPerUser and MaxClientsPerHost to 2 (max simultaneous transfers)
but there is a problem when I use ftp client and put a bunch of files to queue. only two they start to transfer, which is okay, but all others shoud be waiting in queue are cancelled to "failed transfer"
thank you in advance

---

### Post by anunnak on 2008-11-12
_

---

### Post by anunnak on 2008-11-12
> **metalguy639 said:**
> I get an error when I try to click on the GUI. I go to "Applications>System Tools>GADADMIN-PROFTPD and I get a box that says:

```
Could Not Launch The Menu Item:

Failed to execute child process "su-to-root" (No such file or directory)
```

How do I get the program to open??


It's an Intrepid bug. you have to install newest version from

[http://debian.cs.binghamton.edu/debi...3.5-2_i386.deb]("http://debian.cs.binghamton.edu/debi...3.5-2_i386.deb")

```
 sudo dpkg -i gadmin-proftpd_0.3.5-2_i386.deb 
```

---

### Post by frodon on 2008-11-12
you should find all the needed tutorials there :
[http://www.castaglia.org/proftpd/](http://www.castaglia.org/proftpd/)

---

### Post by anunnak on 2008-11-12
> **uneo said:**
> hi i,m totaly newbie to linux & with this tutorial i was able to install gproftp but i want change home directory to /home from /var but can't find they way to do it.:confused:

don't change the home dir! make a link to home

```

mkdir mounted_var
mount --bind /var /home/your_username/mounted_var

```

if you want to access every time you boot, put 
the line into # sudo vim /etc/fstab
```

/var /home/your_username/mounted_var none bind 0 0

```


or another solution: make a symlink

```

ln -s /var /home/your_username

```
this folder you can't list via ftp if you are grounded to "home"

---

### Post by DragonFlyEye on 2008-11-28
Just wanted to say "Thanks" for all the great information.  So, thanks!:guitar:

---

### Post by captclearleft on 2008-12-07
First:  Great Post, Very Informative.  Thanks.

I am noobie 1, and I am learning.  Much apologies...

I have been running a Samba file/print server (ubuntu desktop) for some time successfully.

I would like to now set up an FTPs.  

Do I need to disable samba? 
Does samba settings create a security hole, or risk?  
Will both run at the same time?  
Can I keep the shared samba directories separate from the FTP directories?

Second Note:

I tried firestarer when I first got things up and running (samba), however it disabled my ability to print over the network.  All attempts to correct (port allowing...) were unsuccessful, so I got rid of firestarter.  Now I block non-local traffic to the file server(samba) through my router.

If I use PROFTPD would you recommend "firestarter"?

Thank You

ccl

---

### Post by tmcmulli on 2008-12-08
If you're inside a firewall/router, you probably don't need something like firestarter.  I used to use it, but have removed as it really didn't ever catch anything.  Samba directories and FTP directories are set through the respective config files, so yes, you can keep them separate if you like.  

It all depends on what you are doing with your FTP server... are you using this internal to your network, or are you using it to share files on the Internet??  If the latter, you'll want to make sure you chroot the FTP users so they can't browse your server.

Samba/Proftpd run on separate ports, so no security hole if your behind the router.  If your FTP is a private one, I recommend changing the default port it runs on (which is 21) because most crack attempts will be blindly set on that port.  Also look into hosts.allow/hosts.deny settings as well as a package called fail2ban.

This basically locks people out from your system after x attempts...

---

### Post by captclearleft on 2008-12-10
Thanks,

I a behind a router/firewall.  my samba file server is set up for local network only.

It works great!!!  It was super cheap to set up, and the best investment ever.  I would recomend it to anyone.

I think I will set up the FTP on another machine at first, just to play with it and get the security settings, and sharing figured out.  I do not want to mess up my current configuration.

Thanks Again.

CCL

---

### Post by philosophia on 2008-12-26
I'm having trouble getting TLS to work.  The mod_tls section of my proftpd.conf looks like

```
<IfModule mod_tls.c>
    TLSEngine on
    TLSLog /var/log/proftpd/tls.log
    #TLSProtocol TLSv1
    TLSProtocol SSLv23

    # Are clients required to use FTP over TLS when talking to this server?
    TLSRequired off
    #TLSRequired on

    # Server's certificate
    TLSRSACertificateFile /etc/apache2/ftpcert/server.crt
    TLSRSACertificateKeyFile /etc/apache2/ftpcert/server.key

    # CA the server trusts
    TLSCACertificateFile /etc/apache2/ftpcert/ca.crt

    # Authenticate clients that want to use FTP over TLS?
    TLSVerifyClient off
</IfModule>
```


Although I'm able to connect using TLS/SSL encryption (FTPS),  I'm unable to download any files - I get a 'Download Failed' error message.  I get the following errors

```
I/O error 
Download failed
No available certificate or key corresponds to the SSL cipher suites which are enabled.



220 you're at home
AUTH TLS
234 AUTH TLS successful
PBSZ 0
200 PBSZ 0 successful
PROT P
200 Protection set to Private
USER jay
331 Password required for jay
PASS ********
230 welcome !!!
NOOP
200 NOOP command successful
TYPE I
200 Type set to I
SIZE /download/test.txt
213 5
NOOP
200 NOOP command successful
MDTM /download/test.txt
213 20081224173213
NOOP
200 NOOP command successful
NOOP
200 NOOP command successful
SYST
215 UNIX Type: L8
STAT /download
211-Status of /download:
211-drwxr-xr-x   2 (?)      (?)          4096 Dec 24 17:32 .
211-drwxr-xr-x   4 (?)      (?)          4096 Dec 24 16:16 ..
211--rwxrwxr-x   1 (?)      (?)             5 Dec 24 17:32 test.txt
211 End of status
CWD /download
250 CWD command successful
FEAT
211-Features:
 MDTM
 AUTH TLS
 PBSZ
 PROT
 REST STREAM
 SIZE
211 End
PORT 96,14,230,244,195,117
200 PORT command successful
RETR test.txt
150 Opening BINARY mode data connection for test.txt (5 bytes)
QUIT
```

Here's snippets from my tls.log
```

Dec 26 21:08:19 mod_tls/2.1.2[16323]: TLS/TLS-C requested, starting TLS handshake
Dec 26 21:08:22 mod_tls/2.1.2[16323]: TLSv1/SSLv3 connection accepted, using cipher RC4-MD5 (128 bits)
Dec 26 21:08:23 mod_tls/2.1.2[16323]: Protection set to Private
Dec 26 21:08:45 mod_tls/2.1.2[16324]: TLS/TLS-C requested, starting TLS handshake
Dec 26 21:08:48 mod_tls/2.1.2[16324]: TLSv1/SSLv3 connection accepted, using cipher RC4-MD5 (128 bits)
Dec 26 21:08:48 mod_tls/2.1.2[16324]: Protection set to Private
Dec 27 03:08:54 mod_tls/2.1.2[16324]: starting TLS negotiation on data connection

```

Any idea what's going on?

---

### Post by philosophia on 2008-12-29
please for the love of god

---

### Post by frodon on 2008-12-30
You should look at the proftpd forum, when no answer are given there on ubuntuforums the proftpd forum is the place where to go.

Your issue is above my current proftpd knowledge.

---

### Post by dmydmy on 2009-02-01
You haven't specified that you need to change group and owner to userftp. Otherwise, they'll both be root and someone logging in as userftp won't be able to write to download, for instance.

chown userftp download

chgrp userftp download

HTH

---

### Post by shogan85 on 2009-02-03
Hi all,

I have been trying to get ftp working on my ubuntu 8.04 virtual machine for some time now. I have followed this guide, and replaced the proftpd.conf file with the one in the first post. (See attached file)

I must point out that I have lampp installed, hosting a couple of sites on this machine, and that it seems to come with proftpd already. I have tried the tutorial, then stopped and started the proftpd service, but still no luck getting a login using my PC on the same lan, and filezilla client.

Under System - Administration - GPROFTPD, 
I check the settings there, and at the top right it says, STATUS : DEACTIVATED

Even after starting the proftpd service from the terminal.

I have used /home/ftp as my ftp home directory, and added the upload / download dirs and permissions too.

Any ideas as to why this is not working? attached is my config file...

Thanks in advance!

[ATTACH]102055[/ATTACH]

---

### Post by etamax on 2009-02-04
Did you try to start it manually via /etc/init.d?
Did you check the /var/log/ftp.log for problems?

---

### Post by shogan85 on 2009-02-04
> **etamax said:**
> Did you try to start it manually via /etc/init.d?
Did you check the /var/log/ftp.log for problems?

Hi etamax,

The ftp server doesn't seem to be even initializing, as the log file under /var/log/ftp.log doesn't exist yet.

I have been trying to start the service by using :

sudo /etc/init.d/proftpd start

It returns a status of : * Starting ftp server proftpd
-warning: the DisplayFirstChdir directive is deprecated and will be removed in a future release. Please use the DisplayChdir directive. [ OK ]

As I said in the GPROFTPD gui, status says : Deactivated. Even after starting from init.d manually.

---

### Post by etamax on 2009-02-04
Can you start it at a debug level 6? Then see if there is a problem...

```
sudo proftpd -nd6
```

---

### Post by shogan85 on 2009-02-04
> **etamax said:**
> Can you start it at a debug level 6? Then see if there is a problem...

```
sudo proftpd -nd6
```

etamax, you are the man! Thank you.

Ran that in "debug" mode, and the last line I saw indicated my problem.

It said something along the lines of failed to initialize, port 21 already in use. Went into my proftpd.conf file, and changed the port it uses to something else, connected from my client on that port number, and it works! Once again thank you.

Now that I have identified the issue, how do I figure out what is using 21 at the moment, and how do I kill off this process? I need to do some wordpress updates, and the built in web updater uses a standard FTP updater, which obviously connects on port 21 and nothing else, so I need proftpd to use 21 in the end.

Thanks for the help so far! :D

---

### Post by etamax on 2009-02-05
^_^
To find out which port is in LISTEN status, you can try with:

```
netstat -anp --tcp --udp | grep LISTEN
```

---

### Post by shogan85 on 2009-02-05
> **etamax said:**
> ^_^
To find out which port is in LISTEN status, you can try with:

```
netstat -anp --tcp --udp | grep LISTEN
```

Haha, ok well I ran that as root, and it shows inetd as using port 21.

No idea how I'm gonna get rid of inetd now though - if I do, are there any other processes that are going to be relying on it?

I have proftpd running now for my ftp needs so this shouldn't be an issue.

---

### Post by slouchez on 2009-02-05
bonjour frodon
I'm in the newbie category and have a very simple and specific machine to machine application (on my desk) and I need my ftp server on the ubuntu machine. So gproftpd is ideal for me - but after configuring it (I have the setup working from a windows server - ip address - single user -  which I duplicated) the server remains "deactivated" without giving me any diagnostics - also looked at /var/log/.. 
Also even though I save the configuration (last tab) before exiting - changes are lost when i restart
When I do try to connect I predictably get told "421 Service not available, remote server has closed connection"
What could I still be missing?

---

### Post by shogan85 on 2009-02-05
> **slouchez said:**
> bonjour frodon
I'm in the newbie category and have a very simple and specific machine to machine application (on my desk) and I need my ftp server on the ubuntu machine. So gproftpd is ideal for me - but after configuring it (I have the setup working from a windows server - ip address - single user -  which I duplicated) the server remains "deactivated" without giving me any diagnostics - also looked at /var/log/.. 
Also even though I save the configuration (last tab) before exiting - changes are lost when i restart
When I do try to connect I predictably get told "421 Service not available, remote server has closed connection"
What could I still be missing?

slouchez, try running that command that etamax gave me :

```
sudo proftpd -nd6
```

That will tell you if there is a problem with port 21... For me the last line told me that port 21 was in use by another process, which I have now been able to identify and work around.

---

### Post by shogan85 on 2009-02-05
Update! etamax, thank you very much for your help. After finding out what process it was (inetd) I went to the inetd.conf file and removed the FTP reference. killed inetd process and restarted it, then configured my proftpd.conf to use port 21 again instead of my custom port I had used yesterday to test, restarted that and I now have a fully functional FTP server again!

Once again thank you! :D

---

### Post by shogan85 on 2009-02-05
Ok so now my ftp is running well on local lan, I am getting issues with remote access :(

I have configured port forwarding on my router for 20 and 21 to forward to internal IP of the FTP server. So that seems fine. I have also done 60000-60100 for passive connections, and done the masquerading and passive ports config in my proftpd.conf file. When it starts it says Masqueading as .... and my static IP.

I can connect to FTP server perfectly on LAN, but not remotely. Can't figure out why though. I am using FileZilla client.

Status:	Resolving IP-Address for [www.mydomain.co.uk](www.mydomain.co.uk)
Status:	Connecting to mystaticIP:21...
Status:	Connection established, waiting for welcome message...
Response:	220 Inactivity timer = 120 seconds. Use 'site idle <secs>' to change.
Command:	USER shogan
Response:	331  Password required.
Command:	PASS ********
Response:	530 Permission denied
Error:	Could not connect to server

That is using the exact same user and password as the internal FTP test which works... Tried resetting the password too. Any more ideas? :)

---

### Post by frodon on 2009-02-06
If it works on your LAN on not outside then it's surely a firewall/router problem. Are you sure that you have forwarded the needed ports on your router ?

---

### Post by shogan85 on 2009-02-06
> **frodon said:**
> If it works on your LAN on not outside then it's surely a firewall/router problem. Are you sure that you have forwarded the needed ports on your router ?

Almost 100% sure as I have done all the other port forwarding for web, https, rdp on windows box, pptp vpn, etc. in the same way. I will however go and double check it just to be sure. I have setup proftpd to use port 21 so I should in theory, only require port 21 to be open to the ubuntu machine right?

---

### Post by frodon on 2009-02-06
If i look at the /etc/services files port 20 is required too for ftp-data. I think there we just need to find what port forwarding is missing.

---

### Post by shogan85 on 2009-02-08
> **frodon said:**
> If i look at the /etc/services files port 20 is required too for ftp-data. I think there we just need to find what port forwarding is missing.

frodon, thanks for the reply :)

I have just swapped out my crap thomson router for a good old netgear dg834 and re-did all my port forwarding. FTP is now working 100% from external too, so as you said it had to be port forward issues on the router itself. Thanks for the guide, I have also now changed my default FTP home location to my site so I can now upload content via FTP...

:D

---

### Post by Tony25 on 2009-02-27
I use proftpd from an year now but the only thing still dont understand how to fix is the info of folders and files of the home directories. I have more than 5 accounts on my server, I mean every account have its own home directory, I create them like this (example username: tony20   homefoldername: tony

useradd tony20 -d /home/tony -s /bin/false
passwd tony20

and then I see that all the files and folders on /home/tony get this info User: tony20 Group: tony20

Is that possible to make that this folders and files take the info like this user: ftp-user and group: ftp-group
to make this thing in automatic when you create the accounts.

Thanks

---

### Post by Packrat73 on 2009-03-16
Okay, I have looked through this entire thread (even doing the step by step on the first page) I still get a 530 Login incorrect error. What am I missing. The shell login is right. the home dir is fine and chmod 755. I can log into the ftp using my own username and password that is the admin of the box from anywhere, but any user I create for the ftp never gets passed the incorrect error.

Thanks for any help.

---

### Post by sanemanmad on 2009-03-16
Why not just use sftp ? and chroot your user to their $HOME dir, or make default shell /bin/sh ?

---

### Post by jaywatkins on 2009-03-16
Nice tutorial for ProFTPD w/MySQL backend here:

[http://howtoforge.com/howtos/ftp](http://howtoforge.com/howtos/ftp)

---

### Post by TimsterC on 2009-03-16
I've done the install but I get a "segmentation fault" when I try and run gadmin-proftpd
I've also tried it from a sudo command and the menu item.

Nothing work, any ideas?

---

### Post by frodon on 2009-03-16
> **Packrat73 said:**
> Okay, I have looked through this entire thread (even doing the step by step on the first page) I still get a 530 Login incorrect error. What am I missing. The shell login is right. the home dir is fine and chmod 755. I can log into the ftp using my own username and password that is the admin of the box from anywhere, but any user I create for the ftp never gets passed the incorrect error.

Thanks for any help.Could you post your proftpd.conf file so we can have a look at it ?

Thanks.

---

### Post by MyR on 2009-03-18
> **TimsterC said:**
> I've done the install but I get a "segmentation fault" when I try and run gadmin-proftpd
I've also tried it from a sudo command and the menu item.

Nothing work, any ideas?

It's a known bug.  You will have to compile the lastest package for it to work.

peace

---

### Post by m3bik on 2009-03-27
All I get is the error message saying it couldn't find the package.

---

### Post by MyR on 2009-03-28
Enable the "universe" repositories in system > admin > software sources.
peace

---

### Post by tomstealthports on 2009-03-31
Okay, I have gproftpd, a file on my hard drive at /home/file.txt and a chum.

There are no special folders, or anything like that, that either I or my friend have made.  Literally, I've done nothing yet except the things listed above.

Let's say I have ip address 87.100.92.2 and my friend has ip address 86.90.17.50

How the fsck do I send him the bloody file?

Sorry, don't have much time to check google at the moment.

Other non-gproftpd solutions are welcome, the simpler the better!

Thanks!

---

### Post by MyR on 2009-03-31
> **tomstealthports said:**
> Okay, I have gproftpd, a file on my hard drive at /home/file.txt and a chum.

There are no special folders, or anything like that, that either I or my friend have made.  Literally, I've done nothing yet except the things listed above.

Let's say I have ip address 87.100.92.2 and my friend has ip address 86.90.17.50

How the fsck do I send him the bloody file?

Sorry, don't have much time to check google at the moment.

Other non-gproftpd solutions are welcome, the simpler the better!

Thanks!

email it to him?

---

### Post by tomstealthports on 2009-03-31
Good idea.  And it made me laugh.

---

### Post by loudog23 on 2009-03-31
Hey,
i folloewd every step and now i have a server running. :)
-I'm able to connect to myself
-I see myself in the ftptop

**_Need Help with this: _**i can connect, send password but then it stucks on "loading files names", ive tried with 2 different client and with firefox. with firefox i stall half way loading.

i don't know if it's related to my conf file but i attached it anyway.
I took the defaults and modified it with some of your advise.
Take note i use a 2nd hardrive for sharing so my ftp path is '/media/louserv/loushared' also use 'louserv' instead of ftpuser


**_Tweaking help please: _**The second thing i need help with, is i want to create an separate full access folder for each user and one shared (read only) folder. I will only have few friend connecting to my ftp.
exemple:
one Read only folder (/media/louserv/loushared/shared)
one folder for me (/media/louserv/loushared/lou
on for my friend julie (/media/louserv/loushared/julie)
and so on....

is there a way i can access my shared folder with full access localy and keep it read only in the ftp?

Thank so much for your help and time
lou

---

### Post by frodon on 2009-04-01
Is "/media/louserv/loushared" the home directory of the user you use for FTP connection ?

For your tweaking you have some explanation on how filter based on user in first post then the "DefaultRoot			~" command alone will lock all users in their home directory. Finally you would need to create one shared directory inside the home directory of each user and mount your /media/louserv/loushared/shared directory there. There're surely many other options to do this, this one is just the most secure i have in mind.

---

### Post by loudog23 on 2009-04-01
> **frodon said:**
> Is "/media/louserv/loushared" the home directory of the user you use for FTP connection ?

For your tweaking you have some explanation on how filter based on user in first post then the "DefaultRoot			~" command alone will lock all users in their home directory. Finally you would need to create one shared directory inside the home directory of each user and mount your /media/louserv/loushared/shared directory there. There're surely many other options to do this, this one is just the most secure i have in mind.

Yes, loushared is the home directory of user 'louserv' (i know it's confusing since the label of my hdd is called louserv too)
if i understood correctly i can make my shared folder wherever i want on my system and just mount it into the user's home if i want him to have access.

To allow a friend into my FTP, where do i set his userename and password?
the GUI dosen't work on my system. Is it linked with the user on my system? I saw your exemple of user1 and user2 with different access, but still i wonder how to create those user.

And this morning as i woke up, i had a flash and now i wonder if an VPN would be more what i'm looking for.

Merci beaucoup de votre aide!
And thank for the prompt reply, all my student-friend-with-limited-space-laptop are thanking you as well ):P
lou

---

### Post by frodon on 2009-04-01
> **loudog23 said:**
> Yes, loushared is the home directory of user 'louserv' (i know it's confusing since the label of my hdd is called louserv too)
if i understood correctly i can make my shared folder wherever i want on my system and just mount it into the user's home if i want him to have access.Yes it's the most convenient way i found to do it, i don't know all the way to do though.



> **loudog23 said:**
> To allow a friend into my FTP, where do i set his userename and password?He just need to have the username and password of a user listed in your ftp config.


> **loudog23 said:**
> the GUI dosen't work on my system. Is it linked with the user on my system? I saw your exemple of user1 and user2 with different access, but still i wonder how to create those user.Forget the GUI, your use is not common and i'm not sure you will be able to do what you want to do with the GUI.

> **loudog23 said:**
> And this morning as i woke up, i had a flash and now i wonder if an VPN would be more what i'm looking for.I can't really answer you by lack of VPN knowledge but ssh can also be an option for you, many ftp client are able to connect ssh server for file transfer stuff it is called SFTP.

---

### Post by loudog23 on 2009-04-01
I feel dumb asking you this but,

To create a user on the ftp, i need to:
1-Create the user and password in my system (system -> admin -> usergroup) (example: User=julie pwd=1234)
2-I set his home folder to 'media/louserv/loushared/julie'
3-Add 'UserAlias julienick julie' to the .conf file
And from there, julie can access my FTP by login in as 'julienick' and need to use the password 1234 i've set on my system. Is that right?

Sorry to ask you all these question, i really apreciate your help. I saw in the symapect packge manager the proftp-doc pacakge, i will download it an will read it when i get home tonight.

---

### Post by frodon on 2009-04-01
You should have all you need in first post about user creation but you are right with 1, 2 and 3. However you must also add in the LIMIT LOGIN section each user you want to be able to login the FTP server.

---

### Post by loudog23 on 2009-04-01
> **frodon said:**
> You should have all you need in first post about user creation but you are right with 1, 2 and 3. However you must also add in the LIMIT LOGIN section each user you want to be able to login the FTP server.

Thank you so much for all your help, i will re-read you post. Im far from france but i definitively own you an (ubuntu grided-style) coffee ;)

thank again ):P

EDIT (Added): So if there is a way to mount the share folder into an user folder, this give us the possibility to mount an external device (such as a cd-rom) into the ftp. (remind me of those BBS-cd-rom we use to have in the old day :P)

I also made a huge clean up in the system and on the shared disk. Removing confusing names and rebuilding the directory tree. Hope this will work fine in a fews.

---

### Post by loudog23 on 2009-04-06
Here it is, all done, running smooth and like i wanted.
Here some pointers for ppl who wants to make multiple user with private folders.

[SIZE="4"]**_To create a private folder for every user:_**[/SIZE]

_1.Create the user: (almost same as creating 'userftp' (in frodon's How-To))_
-Using the GUI (system > Admin > user&group) create a userid.
--Set the path of the home folder to '/home/FTP-shared/**user2**/'
--Set '/bin/false'
--Set group to 'userftp'

_2.Remove 'Examples.lnk' from the newly created home folder._
-Open terminal window and go to 'cd /home/FTP-shared'
--Take ownership of the folder (sudo chown youruserhere /home/FTP-shared/**user2**)
--Delete the file '/home/FTP-shared/user2/Examples.lnk'
--Give back the ownership to user2 (sudo chown user2 /home/FTP-shared/user2)
I don't know if it is necessary to remove this file, but i do it since it link the user into your filesystem.

_3.Set Permision Localy for user2_
-Open terminal window and go to 'cd /home/FTP-shared'
--Set permisision to 700 (or 755) for user2 (sudo chmod 700 /home/FTP-shared/user2)

_4.Set Permission inside proftpd.conf:_
-Open terminal window and edit the proftpd.conf files (sudo gedit /etc/proftpd/proftpd.conf)

4.1.Add the user to #Valid Login
```
#Valid Login
<Limit LOGIN>
AllowUser userftp
**AllowUser user2**
DenyALL
</Limit>
```

4.2.Set Private access to user2 folder
```
# user2
<Directory /home/FTP-shared/user2>
Umask 022 022
AllowOverwrite on
        <Limit ALL>
		Order Allow,Deny
		AllowUser user2
		Deny ALL
	</Limit>
</Directory>
```

To add a 3rd user, simply repeate step 1,2,3

at 4.1, simply add the line for user3
```
#Valid Login
<Limit LOGIN>
AllowUser userftp
AllowUser user2
**AllowUser user3**
DenyALL
</Limit>
```

at 4.2, copy/paste the section for user2 and change the user to user3

```
# user2
<Directory /home/FTP-shared/user2>
Umask 022 022
AllowOverwrite on
        <Limit ALL>
		Order Allow,Deny
		AllowUser user2
		Deny ALL
	</Limit>
</Directory>

[B]# user3
<Directory /home/FTP-shared/user3>
Umask 022 022
AllowOverwrite on
        <Limit ALL>
		Order Allow,Deny
		AllowUser user3
		Deny ALL
	</Limit>
</Directory>[/B]
```

Frodon: Thank you so much again for this How-To!

---

### Post by frodon on 2009-04-07
> **loudog23 said:**
> Frodon: Thank you so much again for this How-To!You're welcome, glad to see you server is up and running. I can't tell you how much time i spent the first time i tried to set up a FTP server, at this time i was new to linux too so i let you guess ;)

---

### Post by foy1der on 2009-04-20
First off, thank you to frodon for making this guide. It is well written and easy to follow. 
I was able to get through all the setup and configuration, also I followed the steps to configure sftp.
When I completed all of these steps, I tried to start the server and I get this error.

```

tim@tim-desktop:~$ sudo /etc/init.d/proftpd start
[sudo] password for tim: 
 * Starting ftp server proftpd                                                   - mod_dso/0.4: module 'mod_ctrls_admin.c' already loaded
 - Fatal: LoadModule: error loading module 'mod_ctrls_admin.c': Operation not permitted on line 15 of '/etc/proftpd/modules.conf'
                                                                         [fail]

```
I tried to search for mod_ctrls_admin.c but a lot the results just point back to examples of /etc/proftpd/proftpd.conf.
Here is my proftpd.conf
```

Include /etc/proftpd/modules.conf
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				on
# If set on you can experience a longer connection delay in many cases.
IdentLookups			off

# Choose here the user alias you want
UserAlias	ftp76User	ftp76user

ServerName			"ubuntu-ftp"
ServerType			standalone
DeferWelcome			on

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer		600
TimeoutStalled			100
TimeoutIdle			2200

DisplayLogin                    welcome.msg
DisplayChdir               	.message true
ListOptions                	"-l"

RequireValidShell		off

TimeoutLogin			20

RootLogin			off

#It's better for debug to create log files ;-)
ExtendedLog			/var/log/ftp.log
TransferLog			/var/log/xfer.log
SystemLog			/var/log/syslog.log


DenyFilter			\*.*/

UseFtpUsers			off

#Allow to restart a download
AllowStoreRestart		on

# Use this to jail all users in their homes 
# DefaultRoot			~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell		off

# Port 21 is the standard FTP port.
Port				1980

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress		1.2.3.4

# This is useful for masquerading address with dynamic IPs:
# refresh any configured MasqueradeAddress directives every 8 hours
<IfModule mod_dynmasq.c>
# DynMasqRefresh 28800
</IfModule>

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			8

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
PersistentPasswd		off

MaxClients 			8
MaxClientsPerHost		8
MaxClientsPerUser		8
MaxHostsPerUser			8

# Display a message after a successful login
AccessGrantMsg "welcome!!"
#This message is depsayed for each access good or not
ServerIdent			on	"you're at home"

# Set /home/FTP-shared as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ********* really important **********
DefaultRoot			~

MaxLoginAttempts		5

#Valid Logins
<Limit LOGIN>
AllowUser ftp76user
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/music/*>
Umask 022 022
AllowOverwrite on
		<Limit READ RMD DELE>
		DenyAll
		</Limit>
</Directory>

<Directory /home/FTP-shared/upload>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
	DenyAll
	</Limit>

	<Limit STOR CWD MKD>
	AllowAll
	</Limit>
</Directory>

# This is required to use both PAM-based authentication and local passwords
# AuthOrder			*mod_auth_pam.c mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile			off

# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend 
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
#<IfModule mod_sql.c>
# SQLBackend			mysql
#</IfModule>


<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        off
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine off
</IfModule>

#
# Alternative authentication frameworks
#
#Include /etc/proftpd/ldap.conf
#Include /etc/proftpd/sql.conf


<IfModule mod_tls.c>
    TLSEngine on
    TLSLog /var/ftpd/tls.log
    TLSProtocol TLSv1

    # Are clients required to use FTP over TLS when talking to this server?
    TLSRequired off

    # Server's certificate
    TLSRSACertificateFile /etc/ftpcert/server.crt
    TLSRSACertificateKeyFile /etc/ftpcert/server.key

    # CA the server trusts
    TLSCACertificateFile /etc/ftpcert/ca.crt

    # Authenticate clients that want to use FTP over TLS?
    TLSVerifyClient off
</IfModule>


#
# This is used for FTPS connections
#
#Include /etc/proftpd/tls.conf

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayFirstChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

```

Here is my modules.conf

```

#
# This file is used to manage DSO modules and features.
#

# This is the directory where DSO modules reside

ModulePath /usr/lib/proftpd

# Allow only user root to load and unload modules, but allow everyone
# to see which modules have been loaded

ModuleControlsACLs insmod,rmmod allow user root
ModuleControlsACLs lsmod allow user *

LoadModule mod_ctrls_admin.c
LoadModule mod_tls.c

# Install proftpd-mod-mysql or proftpd-mod-pgsql to use this
#LoadModule mod_sql.c

# Install proftpd-mod-ldap to use this
#LoadModule mod_ldap.c

#
# 'SQLBackend mysql' or 'SQLBackend postgres' directives are required 
# to have SQL authorization working. You can also comment out the
# unused module here, in alternative.
#

# Install proftpd-mod-mysql to use this
#LoadModule mod_sql_mysql.c

# Install proftpd-mod-pgsql to use this
#LoadModule mod_sql_postgres.c

LoadModule mod_radius.c
LoadModule mod_quotatab.c
LoadModule mod_quotatab_file.c

# Install proftpd-mod-ldap to use this
#LoadModule mod_quotatab_ldap.c

# Install proftpd-mod-pgsql or proftpd-mod-mysql to use this
#LoadModule mod_quotatab_sql.c
LoadModule mod_quotatab_radius.c
LoadModule mod_wrap.c
LoadModule mod_rewrite.c
LoadModule mod_load.c
LoadModule mod_ban.c
LoadModule mod_wrap2.c
LoadModule mod_wrap2_file.c
# Install proftpd-mod-pgsql or proftpd-mod-mysql to use this
#LoadModule mod_wrap2_sql.c
LoadModule mod_dynmasq.c


# keep this module the last one
LoadModule mod_ifsession.c

```

I'm pretty sure that everything is setup correctly, but I'm sure anything is possible.

---

### Post by frodon on 2009-04-20
You have the line *Include /etc/proftpd/modules.conf* twice in your proftpd.conf ;)

---

### Post by foy1der on 2009-04-20
ok, I got rid of the stray "include" line and now it says that my certificate file doesn't exist. Specifically:
```

tim@tim-desktop:~$ sudo /etc/init.d/proftpd start
[sudo] password for tim: 
* Starting ftp server proftpd                                                   
- Fatal: TLSRSACertificateFile: '/etc/ftpcert/server.crt' does not exist on line 214 of '/etc/proftpd/proftpd.conf'
                                                                         [fail]

```

I think that this is my question. Where does the certificate file come from? I tried to run the .crt file, which I assume is the certificate file, and it was blank.

---

### Post by frodon on 2009-04-21
The certificate comes from you, it belongs to you to create a certificate for your encryption.
Just follow the steps in first post and you should succeed creating one. Once you will have one in the right directory this error will disappear.

---

### Post by loudog23 on 2009-04-30
> **frodon said:**
> Bad idea in general to connect with your main user which have root access especially because he has root access.

Anyway to allow your user it is as simple as adding your user in LIMIT LOGIN section and create an alias for him if you use aliases.

If you want to go further proftp offers you a second way to handle users able to login via virtual users :
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-VirtualUsers.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-VirtualUsers.html)

Ok, so we then use a user to run the process 'userftp'

What if:
-I download and extract the package in home/userftp/
-I ./configure --prefix=/home/userftp/proftpd
-make, make install
-Configure the ftp
-Set owning and persmission of /home/userftp to userftp 750
-Run the ftp as userftp

Using this method, 
1) can i simply chroot userftp to /home/ftpuser/?
2) does it create security "flaw" if i mount one of my /home/me/folder into the /home/ftpuser/download/?
3) what about the /etc/ and /var/, will they be inside the chrotted folder also?
4)is there any file i need to leave outside the chroot?

Thx for any input, if im succesfful ill send a post to help chroot the server and install ot in a 'more' secure way

thx again frodon for your time.
lou

---

### Post by stinger30au on 2009-05-04
g'day,
thansk so much for starting this thread.tihs looks like it might just be what i need

im getting extremely frustrated trying to get this s/w to run consistently and any assistance would be great.


i have a thread already with what i have done so far, and now my ftp server has decided to stop talking to my lan, let alone talk to the internet at all.


my config follows

ServerType standalone
DefaultServer on
Umask 022
ServerName "0.0.0.0"
ServerIdent on "My FTP Server"
ServerAdmin [email]email@example.org[/email]
IdentLookups off
UseReverseDNS off
Port 21
MasqueradeAddress "xxx.xxx.xxx.xxx"
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
DisplayChdir .message
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores on
TransferRate RETR 220
TransferRate STOR 250
TransferRate STOU 250
TransferRate APPE 250
SystemLog /var/log/secure
RequireValidShell off
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol SSLv23
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gadmin-proftpd/certs/cert.pem
TLSRSACertificateKeyFile /etc/gadmin-proftpd/certs/key.pem
TLSCACertificateFile /etc/gadmin-proftpd/certs/cacert.pem
TLSRenegotiate required off
</IfModule>
<IfModule mod_ratio.c>
Ratios off
SaveRatios off
RatioFile "/restricted/proftpd_ratios"
RatioTempFile "/restricted/proftpd_ratios_temp"
CwdRatioMsg "Please upload first!"
FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
LeechRatioMsg "Your ratio is unlimited."
</IfModule>
<Limit LOGIN>
  AllowUser cocos
  DenyALL
</Limit>

<Anonymous /media/disk/coco-photos>
User cocos
Group dez
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>



i have given my pc a static ip of 192.168.1.1
router is a billion 7402LM
i have enabled port forward of port 20 & 21 

if i try and connect on my lan now i get his  (output from my client - filezilla)
(im trying to connect from the same pc just to test  if it works or not)

Status:    Connecting to 127.0.0.1:21...
Status:    Connection established, waiting for welcome message...
Response:    220 My FTP Server
Command:    USER testing
Response:    331 Password required for testing
Command:    PASS *******
Response:    230 Anonymous access granted, restrictions apply
Command:    SYST
Response:    215 UNIX Type: L8
Command:    FEAT
Response:    211-Features:
Response:     LANG en
Response:     MDTM
Response:     UTF8
Response:     REST STREAM
Response:     SIZE
Response:    211 End
Command:    OPTS UTF8 ON
Response:    200 UTF8 set to on
Status:    Connected
Status:    Retrieving directory listing...
Command:    PWD
Response:    257 "/" is the current directory
Command:    TYPE I
Response:    200 Type set to I
Command:    PASV
Response:    227 Entering Passive Mode (xxx,xxx,xxx,xxx,xxx,xxx).
Command:    LIST
Error:    Connection timed out
Error:    Failed to retrieve directory listing



any ideas/suggestions would be great to get it talking on the lan consistantly and get it talking to the net as well would be greatly appreciated.

thanks

---

### Post by frodon on 2009-05-04
Sorry stinger30au, we offer support for this tutorial only here.
General proftpd config debug belongs elsewhere.

Maybe drop your question in the proftpd forum if you don't get answers on ubuntuforums.

---

### Post by stinger30au on 2009-05-05
> **frodon said:**
> Sorry stinger30au, we offer support for this tutorial only here.
General proftpd config debug belongs elsewhere.

Maybe drop your question in the proftpd forum if you don't get answers on ubuntuforums.


i got it sorted out

it was the router causing the issue. i had by suspicions it was

i had to adjust the firewall in the router to enable port 20 & 21 to be allowed

now the ftp server talks to the net and does what i wanted it to do

---

### Post by kinggo on 2009-05-24
THX for this tutorial. I've been using samba on 8.04 but it doesn't work on jaunty any more. At least, not. So I decided to start using FTP again as I did on win long time ago. Samba was good because of streaming.

I think I set up my servers correctly. I can log on on both of them (jaunty x2) but the problem is that I can't see the folders that are supposed to be shared. I used Gadmin-proftpd to do that. First I got some error when I tried to add shared folder (something about "var/ftp missing") but I added folder anyway. But I can't see them.

The folders I want to share are on non system disks, but those disks are mounted under media folder automatically during boot. What am I missing?

---

### Post by etamax on 2009-05-25
Which error do you get exactly?
I have never used Gadmin-proftpd so I can't help you on that program. Could you post your /etc/proftd/proftd.conf?

---

### Post by kinggo on 2009-05-25
I think there is no error, apart from that "missing var/ftp folder" wich occurs on selecting folder that I want to share through Gadmin-proftpd. But I believe my connection is OK. I can connect, but I don't see anything on the other side.

Here is the config file.........
```

ServerType standalone
DefaultServer on
Umask 022
ServerName "192.168.0.39"
ServerIdent on "tx1000"
ServerAdmin email@example.org
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
DisplayChdir .message
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 220
TransferRate STOR 250
TransferRate STOU 250
TransferRate APPE 250
SystemLog /var/log/secure
RequireValidShell off
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol SSLv23
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gadmin-proftpd/certs/cert.pem
TLSRSACertificateKeyFile /etc/gadmin-proftpd/certs/key.pem
TLSCACertificateFile /etc/gadmin-proftpd/certs/cacert.pem
TLSRenegotiate required off
</IfModule>
<IfModule mod_ratio.c>
Ratios off
SaveRatios off
RatioFile "/restricted/proftpd_ratios"
RatioTempFile "/restricted/proftpd_ratios_temp"
CwdRatioMsg "Please upload first!"
FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
LeechRatioMsg "Your ratio is unlimited."
</IfModule>
<Limit LOGIN>
  AllowUser mario
  DenyALL
</Limit>

<Anonymous /media/sda2/FTP tx1000>
User mario
Group mario
AnonRequirePassword on
MaxClients 400 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
<Directory /media/sda2/dig it>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Directory>
</Anonymous>

```

---

### Post by etamax on 2009-05-25
Could you try to not use spaces in folder's name?

---

### Post by kinggo on 2009-05-25
THX THX THX =D> I would never think about that. Never had any issues with that on windows.

---

### Post by etamax on 2009-05-25
If the problem was that, you can put the directory name between " if you want to use spaces in directory names.

Example:
<Anonymous "/media/sda2/FTP tx1000">

---

### Post by kinggo on 2009-05-25
Good to know. I'll try some other time when I'll be setting up some ftp. Now I already renamed my folders and everything seems to be fine. Thanks again.

---

### Post by chippanfat on 2009-05-27
I'm not sure if this has already been asked and replied too. I don't want to read through 100+ pages :(

My question is, how do I specify a default directory for each user using the gui? If I create and add the directory when I'm creating  a new user but how to I make a directory default for a user? There's no where that really says make default directory for user. I've tried a few different ways but nothing has worked

I want each user/computer in the house to have their own area where they don't see anyone else's files and for example the person is connecting whilst using Ubuntu (Places>Connect to server>FTP(With log in)) I want them to type in their own directory to connect to. And because its specified what directory they connect to on the server, it will reject anyother file path.

Hopefully I've explained it right :)

Cheers.:KS

---

### Post by frodon on 2009-05-28
Yep, don't forget the "search this thread feature" it allows you to find what you look for if it exists without reading the whole thread :)
About your issue unfortunately we don't really officialy provide support for using the GUI but some users using it may pop in with a solution.

If you are not text file allergic using the manual configuration is a better option as it allows painless debug and accurate configuration.

Good luck

---

### Post by ataol on 2009-06-04
I'm friends with a problem in time to restart the ftp, I copied exactly what was in the configuration of "frodon. 
 What can be?


/home/FTP-shared
root@server(0/8,2k)$sudo /etc/init.d/proftpd restart
 * Stopping ftp server proftpd                                           [ OK ]
 * Starting ftp server proftpd
- warning: the DisplayFirstChdir directive is deprecated and will be removed in
a future release.  Please use the DisplayChdir directive.
 - warning: handling possibly truncated configuration data at line 112 of '/etc/
proftpd/proftpd.conf'
                                                                         [ OK ]

---

### Post by frodon on 2009-06-04
Hum check this line :
```
<Directory**[COLOR="Red"]>[/COLOR]** /home/FTP-shared/upload/*>
```I think the character in red bold is maybe a typo of mine from last time i edited the post.

---

### Post by ataol on 2009-06-04
I made the change you said it was to get the ">" same as the error occurred on line 112.

---

### Post by ataol on 2009-06-04
[LEFT]I see by the error is happening in this part

<Directory /home/FTP-shared/upload/*>
Umask 022 022
AllowOverwrite on
    <Limit READ RMD DELE>
          DenyAll
        </Limit>

        <Limit STOR CWD MKD>
          AllowAll
        **[COLOR=Red]</Limit>[/COLOR]**

</Directory>
[/LEFT]

---

### Post by frodon on 2009-06-04
Your log just report warning so i guess your server should be running anyway. As you use the default config which work for many users i think the issue might be elsewhere.

---

### Post by ataol on 2009-06-04
you have the original file? 
 with him because I got to ask for the password, but can not login in by not knowing the username and password.

---

### Post by frodon on 2009-06-05
If you get the now classic 530 login error perform a search in this thread and you will find the ;utiple ways of solving this issue. It mainly depends how you created your user.

---

### Post by sideshowmel on 2009-06-12
I keep getting "550 SSL/TLS required on the control channel" when trying to connect.  I don't want ftp enabled, just sftp.  I'm using FileZilla as my client, and I've tried all sorts of theories I've found on various posts.  What am I missing here?

---

### Post by frodon on 2009-06-12
In filezilla you must choose FTPES, SFTP is ftp in ssh tunnel. The tutorial explains how to set FTPS not SFTP.

---

### Post by Eddy Gordo from Tekken on 2009-06-14
I am having all sorts of problems with proftpd.  I've searched this thread and the web in general, but I'm not sure how to word the question to find a solution.

First, I can not stop/restart the server using

```
sudo /etc/init.d/proftpd restart
```

I not only get no feedback in terminal after issuing init.d script, when I use the stop command, I am still able to make sFTP connections to the server.  I even tried renaming the proftpd.conf file, to see if it would stop the server.  but I was still able to make connections.

The conf file appears to work
```

#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6                         on
# If set on you can experience a longer connection delay in many cases.
IdentLookups                    off

ServerName                      "Debian"
ServerType                      inetd
DeferWelcome                    off

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    on

TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200

DisplayLogin                    welcome.msg
DisplayChdir                    .message true
ListOptions                     "-l"

DenyFilter                      \*.*/

# Use this to jail all users in their homes
# DefaultRoot                   ~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell             off

# Port 21 is the standard FTP port.
Port                            21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress             1.2.3.4

# This is useful for masquerading address with dynamic IPs:
# refresh any configured MasqueradeAddress directives every 8 hours
<IfModule mod_dynmasq.c>
# DynMasqRefresh 28800
</IfModule>

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

# Set the user and group that the server normally runs at.
User                            proftpd
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd              off

# This is required to use both PAM-based authentication and local passwords
# AuthOrder                     *mod_auth_pam.c mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile                   off

# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
#<IfModule mod_sql.c>
# SQLBackend                    mysql
#</IfModule>

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default.
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        off
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine off
</IfModule>

#
# Alternative authentication frameworks
#
#Include /etc/proftpd/ldap.conf
#Include /etc/proftpd/sql.conf

#
# This is used for FTPS connections
#
#Include /etc/proftpd/tls.conf

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User                                ftp
#   Group                               nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias                   anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser on ftp
#   DirFakeGroup on ftp
#
#   RequireValidShell           off
#
#   # Limit the maximum number of anonymous logins
#   MaxClients                  10
#
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin                        welcome.msg
#   DisplayFirstChdir           .message
#
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
#
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask                           022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
#
# </Anonymous>


DefaultRoot /etal/ftp
IdentLookups  off
ServerIdent on "FTP Server ready."
```

which brings me to my other question.  I want to chroot users into /etal/ftp, but i also want to prevent them from searching up the filesystem from there. my efforts haven't prevented users from cd'ing up.  even after changing permissions in the file system and limit command usage.  I was hoping that solving the first problem would help out the second.  any help would be awesome.

---

### Post by frodon on 2009-06-14
sFTP is FTP in ssh tunnel so this has nothing to do with proftpd but with your ssh server configuration.

---

### Post by khelben1979 on 2009-06-14
I prefer [pureftpd]("http://en.wikipedia.org/wiki/Pureftpd") over this one any day.

---

### Post by PirateChef on 2009-06-18
Oh, man, this is driving me crazy!
I've been working on this for days, poring over this thread, and any related ones I could find.

I have a router, with a dynamic IP. I've assigned it a name from dyndns.com (gaygoyle.homelinux.org), and set up the router to automatically update.

I've set up the FTP user (ftp1) in "Users & Groups". I have the shell set to /bin/false.

I have port 1980 forwarded, as well as ports 60000-65535. I made sure that I had the proper IP for the machine that the ports were being forwarded to.

Also, I have the ftp directory (/home/ftp1) permissions set to 755.

Still, when I try to log in, both with the DynDNS address and the IP number, I get "connection refused". I'm using gFTP for the client. I tried [this website]("http://www.g6ftpserver.com/en/ftptest"), too, and got a more verbose error:

```
* About to connect() to gargoyle.homelinux.org port 1980
* Trying 98.237.xxx.xxx... connected
* Connected to gargoyle.homelinux.org (98.237.xxx.xxx) port 1980
< 500 FTP server shut down (Tue Jun 16 09:29:22 2009 , Current connections will be dropped: Tue Jun 16 09:19:22 2009) -- please try again later
* This doesn't seem like a nice ftp-server response
* Closing connection #0
```

Here's my proftpd.conf:

```
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias sauron ftp1

ServerName          "ChezFrodon"
ServerType          standalone
DeferWelcome            on

MultilineRFC2228 on
DefaultServer           on
ShowSymlinks            off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                 "-l"

RequireValidShell       off

TimeoutLogin 20

RootLogin           off

# It's better for debug to create log files ;-)
ExtendedLog             /var/log/ftp.log
TransferLog             /var/log/xferlog
SystemLog           /var/log/syslog.log

#DenyFilter         \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart       on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port                1980

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask               022 022

PersistentPasswd        off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/ftp1

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser ftp1
DenyALL
</Limit>

<Directory /home/ftp1>
Umask 022 022
AllowOverwrite off
    <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
    DenyAll
    </Limit>
</Directory>

<Directory /home/ftp1/download/*>
Umask 022 022
AllowOverwrite off
    <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
    DenyAll
    </Limit>
</Directory>

<Directory /home/ftp1/upload/>
Umask 022 022
AllowOverwrite on
    <Limit READ RMD DELE>
        DenyAll
        </Limit>

        <Limit STOR CWD MKD>
        AllowAll
        </Limit>
</Directory>

MasqueradeAddress gargoyle.homelinux.org
MasqueradeAddress 98.237.xxx.xxx

UseReverseDNS off
IdentLookups off
```

---

### Post by frodon on 2009-06-19
First thing try to set first your server on port 21 as it is often easier on he firewal side. BTW, do you run any firewall on your computer ?
Then to make it easier your can put AuthAliasOnly to off and then try to login directly with the username (i guess this won't really help but ...)

---

### Post by PirateChef on 2009-06-19
> **frodon said:**
> First thing try to set first your server on port 21 as it is often easier on he firewal side. BTW, do you run any firewall on your computer ?
Then to make it easier your can put AuthAliasOnly to off and then try to login directly with the username (i guess this won't really help but ...)

I tried it both ways, same error.
I also tried logging in with just the IP address.

How do I know if I have a firewall running?

---

### Post by frodon on 2009-06-19
If you haven't set on thne you should not have any. Are you trying to log in from the computer that runs the server ?

If not it is the thing to try to exclude any network config issue.

---

### Post by PirateChef on 2009-06-19
> **frodon said:**
> Are you trying to log in from the computer that runs the server ?

Yes.

---

### Post by frodon on 2009-06-19
Remove your /etc/shutmsg file and try again (i mean restart the server with */etc/init.d/proftp restart*). If it still doesn't work re-install proftpd.

---

### Post by PirateChef on 2009-06-19
OK, this seems to be getting somewhere.
Now, I get this error:
```
* About to connect() to gargoyle.homelinux.org port 21
* Trying 98.237.xxx.xxx... connected
* Connected to gargoyle.homelinux.org (98.237.xxx.xxx) port 21
< 220 you're at home

> USER ftp1
< 331 Password required for ftp1

> PASS *****
< 530 Login incorrect.
* Access denied: 530
* Closing connection #0
```

I uninstalled and re-installed proftpd, which changed nothing. I changed the password for ftp1 in the Users & Groups control panel, and the command line. Still getting this error.

---

### Post by frodon on 2009-06-20
Perform a search in the thread with "530 error" as keyword and you should find the information you need.
It is the most common error setting proftpd, nothing serious, either your password has not been set correctly either your are using wrong username (e.g. using user name when alias is expected).

---

### Post by PirateChef on 2009-06-20
It seems to be logging in fine, if I use the alias "sauron" instead.
However, it kicks me right back out again:
```

* About to connect() to gargoyle.homelinux.org port 21
* Trying 98.237.xxx.xxx... connected
* Connected to gargoyle.homelinux.org (98.237.xxx.xxx) port 21
< 220 you're at home

> USER sauron
< 331 Password required for sauron

> PASS *****
< 230 welcome !!!

> PWD
< 257 "/" is the current directory
* Entry path is '/'

> CLNT Testing from http://www.g6ftpserver.com/ftptest from IP 98.237.xxx.xxx
< 500 CLNT not understood
* QUOT command failed with 500
* Connection #0 to host gargoyle.homelinux.org left intact

* Closing connection #0
```

Does this mean there's something wrong with the CLNT (client), proftpd?
I can't find too much information on error 500.
gFTP still gets "connection refused".

---

### Post by frodon on 2009-06-20
At this step, it's a problem with the client IMO. Try with a client like filezilla or gFTP.

---

### Post by PirateChef on 2009-06-21
> **frodon said:**
> At this step, it's a problem with the client IMO. Try with a client like filezilla or gFTP.

gFTP gives me
```
Cannot connect to gargoyle.homelinux.org: Connection refused
```
and Filezilla:
```
Status:	Resolving address of gargoyle.homelinux.org
Status:	Connecting to 98.237.xxx.xxx:21...
Status:	Connection attempt failed with "ECONNREFUSED - Connection refused by server".
```

---

### Post by frodon on 2009-06-21
Yep i think the issue is on your network config either firewall, router or server port. Check everything you should have done a mistake somewhere.

---

### Post by Muscovy on 2009-06-21
I'm going to set up a simple ftp server in the next while, but I'm not sure how to set a password to it. How do I set one?

PS - Although it's on Ubuntu, the clients are all Windows users, in case this changes anything.

---

### Post by Ishino on 2009-06-26
> **PirateChef said:**
> OK, this seems to be getting somewhere.
Now, I get this error:
```
* About to connect() to gargoyle.homelinux.org port 21
* Trying 98.237.xxx.xxx... connected
* Connected to gargoyle.homelinux.org (98.237.xxx.xxx) port 21
< 220 you're at home

> USER ftp1
< 331 Password required for ftp1

> PASS *****
< 530 Login incorrect.
* Access denied: 530
* Closing connection #0
```

I uninstalled and re-installed proftpd, which changed nothing. I changed the password for ftp1 in the Users & Groups control panel, and the command line. Still getting this error.

I had this exact same problem today, I found a tip that said using a smaller password. This worked for me. I went from 15 chars to 8 chars. I hope it wasn't just a coincidence :p

grts

---

### Post by Muscovy on 2009-06-28
I just had a '530 Login incorrect' error as well. However, it's already using a short password, and it's a new setup, so I'm pretty sure in my case I've done something wrong.

  What does the your_password represent? The account's password, or a validitory one of your own? I tried using the same password for everything asa an experiment, and still got the 530 error.

---

### Post by schizomasochizt on 2009-07-07
Hi guys, Im a noob when it comes to this field so I installed the GUI. I was able to install it, configured the server, and added users. But then here comes the part where I will log onto the server. My server name is "Testftp.com" shall I type this one on my web browser? or is there a way for me to log into the server as a user?

---

### Post by Dale Lewis on 2009-08-04
I have a question...I have a permissions issue on uploading....downloading works like a charm...here is my error:
 
STOR /_Boston_ Foreplay-Long Time.mp3

550 /_Boston_ Foreplay-Long Time.mp3: Permission denied
Loading directory listing / from server (LC_TIME=en_US.UTF-8)
PASV

227 Entering Passive Mode (xx,xxx,xxx,xxx,xxx,125).
LIST -aL

150 Opening ASCII mode data connection for file list
226 Transfer complete

I have changes permissions and all for this directory to no avail..,.any ideas?

---

### Post by loudog23 on 2009-08-04
-Make sure you have this inside proftpd.conf (preferably inside your upload directory section)
<limit STOR>
AllowAll
</limit>

-And make sure your upload folder is owned by root with 777 permision

---

### Post by chetan55 on 2009-08-06
Hello,
       we have proftpd install on our sever previously.But i don't know how ot create new user or change passwd to new user also. Please let me know.
 
I have below lines in my  proftpd.conf
 
DefaultRoot     ~ftp/xyz abcftpadmin
DefaultRoot     ~ftp/xyz/rumblefish rumblefish
DefaultRoot     ~ftp/xyz/ryan ryan
DefaultRoot     ~ftp/xyz/pliqftpguest pliqftpguest

Thanks
Chetan

---

### Post by loudog23 on 2009-08-06
chetan55:
Simply create the user on your system.

Option 1:
USing the GUI: System -> user and group -> Create new user.
Make sure the 'bin' is set to false.
Make also sure they have an alias set.

Option 2:
From the command line use: (if you use this method, make sure you have 'authaliasonly off' inside your proftpd.conf
create user -> 'sudo useradd *UserNameHere* -d *UserHomeFolder* -s /bin/false'
set password -> 'sudo passwd *UserNameHere*'

Option 3: (my way)
Edit the file /etc/adduser.conf
Set the variable you want
use the command 'sudo adduser *UserNameHere*
fill the requested field and voila

Keep in mind:
If you want each user to be 'locked' inside their home folde, simply replace all you 'defaultroot' lines posted above by 'defaultroot ~'

I suggest you revise Post #1 and check out post #992

Good luck

---

### Post by loudog23 on 2009-08-06
delete post please... misplaced post.

---

### Post by ductiletoaster on 2009-09-04
when my friend uploads files they appear in the directory with his permissions.... is there away they will always have mine?

---

### Post by frodon on 2009-09-04
You should try to modify the following lines:
```
# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup
```I know this but i never really found a way to make them to have your normal user rights, i've not searched hard though. Anyway i would start trying to modify the above lines to match your user.

---

### Post by dspinfo on 2009-09-04
After read the posts :-s i have "503 not loggin in" yet
Please any idea?

Thanks for advance!

---

### Post by vladinecko on 2009-09-04
hi all, i went the easy way and installed proftpd using gproftpd. everything was a piece of cake and all is set up correctly. 

however, when i connect to the ftp server, listing directory contents takes up to 2 minutes (even when the directory is empty) and many times it times out altogether. once i'm in the dir, copying files to/from it is very fast. it's literally only retrieving the list of files that is timing out on me.

any help would be greatly appreciated!

---

### Post by lhffan on 2009-09-22
I have sucsessfully added my two users and when they logon they comes to /game dir

But both users can now go higher up, dont want then to have acess outside the /game


How do i acomplish that?

---

### Post by frodon on 2009-09-22
Reomove both DefaulRoot command and replace them by :
```
DefaultRoot /game
```This should lock your FTP users users in /game.

---

### Post by dannyz on 2009-09-22
thanks for the great tutorial i was wondering how to get ProFTPD working :guitar:

---

### Post by lhffan on 2009-09-23
> **frodon said:**
> Reomove both DefaulRoot command and replace them by :
```
DefaultRoot /game
```This should lock your FTP users users in /game.

Worked fine thanx

But i want to have /game for user x and /game/server for user y?

---

### Post by frodon on 2009-09-23
Then use the following command instead:
```
DefaultRoot ~
```It will lock each user in his home directory, then you set user x home directory to /game and user y home directory to /game/server.

---

### Post by qubew on 2009-10-06
Hi, I have 530 login failed too, :(

i try proftpd -n 

it said

```
    root@DNS:/# proftpd -n
   - warning: the DisplayFirstChdir directive is deprecated and will be removed in a future release.  Please use the DisplayChdir directive.
  DNS.finalwave.com - Failed binding to ::, port 2110: Address already in use
  DNS.finalwave.com - Check the ServerType directive to ensure you are configured correctly.
  
```


This is my proftpd.conf


```

# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias user1 userftps

ServerName            "FTP"
ServerType             standalone
DeferWelcome            on

MultilineRFC2228 on
DefaultServer            on
ShowSymlinks            off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                    "-l"

RequireValidShell         off

TimeoutLogin 20

RootLogin             off

# It's better for debug to create log files ;-)
ExtendedLog             /var/log/ftp.log
TransferLog             /var/log/xferlog
SystemLog            /var/log/syslog.log

#DenyFilter            \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart        on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port                2110

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                022    022

PersistentPasswd        off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/share/ftp-test

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftps
DenyALL
</Limit>

<Directory /home/share/ftp-test>
Umask 022 022
AllowOverwrite off
    <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
    DenyAll
    </Limit>
</Directory>

<Directory /home/share/ftp-test/download/*>
Umask 022 022
AllowOverwrite off
    <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
    DenyAll
    </Limit>
</Directory>

<Directory /home/share/ftp-test/upload/>
Umask 022 022
AllowOverwrite on
    <Limit READ RMD DELE>
          DenyAll
        </Limit>

        <Limit STOR CWD MKD>
          AllowAll
        </Limit>
</Directory>

```


thanks
qubew

---

### Post by frodon on 2009-10-06
Try on port 21 first, it's easier for debug.

---

### Post by qubew on 2009-10-06
> **frodon said:**
> Try on port 21 first, it's easier for debug.

okie, I try port 21 and get the same error.

```
Failed binding to ::, port 21: Address already in use
```

---

### Post by frodon on 2009-10-07
Tell us more on how you test your server (with which computer, which FTP client, how do you fill your FTP client, ...)

---

### Post by qubew on 2009-10-07
> **frodon said:**
> Tell us more on how you test your server (with which computer, which FTP client, how do you fill your FTP client, ...)

:)

i test on my pc (win XP) in same network with Filezilla

host : 192.168.1.145 (ubuntu server)
user : userftps
pass : xxxxxxx
port : 21


And I try telnet 192.168.1.145 21 from my pc
it's work,

---

### Post by frodon on 2009-10-07
Ok first thing to test is with filezilla on the pc that runs the server, if it work there then the issue is more likely on your network config and not from your FTP server config.

---

### Post by qubew on 2009-10-07
> **frodon said:**
> Ok first thing to test is with filezilla on the pc that runs the server, if it work there then the issue is more likely on your network config and not from your FTP server config.

I can connect Filezilla to other Ftp server (Buffalo Terra server ),

---

### Post by frodon on 2009-10-07
No no, i mean run filezilla on the _same_ computer that runs the FTP server and try to login _your_ FTP server, thus this will exclude any network issue.

---

### Post by qubew on 2009-10-07
> **frodon said:**
> No no, i mean run filezilla on the _same_ computer that runs the FTP server and try to login _your_ FTP server, thus this will exclude any network issue.

Oop! sorry

```

ftp 192.168.1.145
Connected to 192.168.1.145.
220 you're at home
Name (192.168.1.145:admins): userftps
331 Password required for userftps
Password:
530 Login incorrect.
Login failed.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp>
ftp> quit
421 Login Timeout (20 seconds): closing control connection.

```and this is the userftps's profile on /etc/passwd

```

userftps:x:1017:1021::/home/share/ftp-test:/bin/false

```and this is file permission of the directory
```

root@DNS:/home/share# ls -lh
drwxrwxrwx  4 userftps  root       4.0K 2009-10-05 15:28 ftp-test

root@DNS:/home/share/ftp-test# ls -lh
total 8.0K
drwxrwxrwx 2 userftps root 4.0K 2009-10-05 15:28 download
drwxrwxrwx 2 userftps root 4.0K 2009-10-05 15:28 upload


```

---

### Post by frodon on 2009-10-08
Ok, thanks for the details.

You must use the alias you set in the profrpd config instead of the username directly. In the config file "AuthAliasOnly on" command tells the FTP server to only accept alias names as login, the the command "UserAlias user1 userftps" set the alias name "user1" for the user "userftps" therefore you must use "user1" to login your FTP server. Any other login name will return 530 error.

---

### Post by qubew on 2009-10-08
> **frodon said:**
> Ok, thanks for the details.

You must use the alias you set in the profrpd config instead of the username directly. In the config file "AuthAliasOnly on" command tells the FTP server to only accept alias names as login, the the command "UserAlias user1 userftps" set the alias name "user1" for the user "userftps" therefore you must use "user1" to login your FTP server. Any other login name will return 530 error.

Ohh, that's it!!
Work now,

It's my mistake absolutely. 

Many thanks **Frodon**

---

### Post by n0an on 2009-10-11
**Subject: ****Error: 530 The server is full, hosting 5 users?**

Hello,

I am on an Ubuntu Desktop (Kimsufi). Everything is good, but whenever I am downloading something from the ftp, the other user is not able to access the ftp with an error "530 The server is full, hosting 5 users".The apache2.conf file has maxclients set as 150. 

Even GPROFTPD (gui for proftpd) doesn't have any options to configure it. How do I change the max # of connections for the server?

Thanks!

---

### Post by frodon on 2009-10-12
Modify this part to suit your needs :
```
MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8
```

---

### Post by n0an on 2009-10-14
> **frodon said:**
> Modify this part to suit your needs :
```
MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8
```

Do I add that in the .conf file? Nothing like that in the conf file.

---

### Post by frodon on 2009-10-15
If you don't have that in your config file then maybe you didn't follow the tutorial as the config file given in first post contains these commands.

I remind you just in case that no real support is offered for GProftpd in this thread, some users might be able to help you with it though.

---

### Post by penguinv on 2009-10-24
> 
For Beginners:
1-  Install proftpd and gproftpd with synaptic or with this command :
Code:

sudo apt-get install proftpd gproftpd

2-Play with the GUI and set up quickly your server.
Beware no support is offered here for this tool but it shouldn't be too hard to use.

I did (1-) ... I found it unders system tools. >>

Now I need to fill in server address, server port.
I need to learn some basics about what I need to do to administer it and the consequences of my actions. Will the administrater email address be visible? What is an identity lookup. What access will a user have to my computer? Where do I put files I want to be available. If someone sends me a file, where will it go?

Pretty dumb I am but I am really glad that frodon has posted this.
I'll get smarter if I know where to read something, on my level.

I sincerely appreciate all assistance.

---

### Post by raymond.szebin on 2009-11-03
guys, i'm lost, please anyone take mercy and help me out: 

i have set up proftpd as the tutorial said, a logged in etc. 

but my goal is securing it with TLS and i've been reading this thread and all my eyes could find on the internet yet i don't know what i am doing wrong. 

after i enable TLS, and do proftpd -td5 i get 

Please provide passphrases for these encrypted certificate keys:
RSA key for the ***.***.***.***#2525 (Jerry) server:
Verifying - RSA key for the ***.***.***.***#2525 (Jerry) server:
hostname - mod_tls/2.1.2: passphrase locked into memory
Syntax check complete.

so i guess i'm ok with syntax - i will post conf file is required. 

i try to log in using filezilla client from another machine but after TLS is on, bummer! 

Connecting to ***.***.***.***:2525...
Status:    Connection established, initializing TLS...
Error:    Connection timed out
Error:    Could not connect to server

and my ftp.log file says 
::ffff:***.***.***.*** UNKNOWN root [03/Nov/2009:12:14:30 +0300] "" 550 -
::ffff:***.***.***.*** UNKNOWN root [03/Nov/2009:12:14:30 +0300] "OAOâ<YnI1?" 550 -
::ffff:***.***.***.*** UNKNOWN root [03/Nov/2009:12:14:41 +0300] "" 550 -
::ffff:***.***.***.*** UNKNOWN nobody [03/Nov/2009:12:18:06 +0300] "" 550 -
::ffff:***.***.***.*** UNKNOWN nobody [03/Nov/2009:12:18:17 +0300] "" 550 -
::ffff:***.***.***.*** UNKNOWN nobody [03/Nov/2009:12:18:17 +0300] "V mOa6ó"A)>Y3" 550 -

the root stuff is when i tried to run as root trying to troubleshoot the problem ( no fix though) 

if you guys need more stuff from me i will provide. it's killing me and no ideea what i am doing wrong. running Ubuntu 8.10,  ProFTPD Version 1.3.1 OpenSSL 0.9.8g libgnutls.so.26.4.5

](*,)

---

### Post by frodon on 2009-11-03
As usual describe you test process, the first test you must do is to login your FTP server from the same PC that runs the server and with a FTP client well configured (filezilla in FTPES mode for instance) with your firewall disabled.

If it works like that then your issue is related to network config or firewall.

---

### Post by raymond.szebin on 2009-11-03
the problem is Filezilla is GUI and i'm working on a server without X (connecting via ssh) and i could not find CLI clients that support TLS ( tried gftp but the fag keeps saying it was not compiled with SSL) it is quite off topic, but maybe advice in this direction? 

my test is best described like :

test server running proftpd like the tutorial, just added 

ServerType standalone
DeferWelcome on

UseReverseDNS off
IdentLookups off

TimeoutLogin 20

RootLogin off


MultilineRFC2228 on
DefaultServer on
ShowSymlinks off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200
TimeoutLogin 20

to the config file, 
 where the TLS part is: 

<IfModule mod_tls.c>
TLSEngine on
TLSLog /var/ftpd/tls.log
TLSProtocol TLSv1

# Are clients required to use FTP over TLS when talking to this server?
TLSRequired on

# Server's certificate
TLSRSACertificateFile /etc/ftpcert/server.crt
TLSRSACertificateKeyFile /etc/ftpcert/server.key

# CA the server trusts
TLSCACertificateFile /etc/ftpcert/ca.crt

# Authenticate clients that want to use FTP over TLS?
TLSVerifyClient off
</IfModule>

without TLS i cann conect and it works from remote machine ( my notebook runin winxp - filezilla)
after i put all the TLS part in, it becomes all blurry and nothing works 

i mean, proftpd runs, it's just that i am not able to log in .

---

### Post by frodon on 2009-11-03
It can be network issue, anyway you can stilll try to re-create your TLS certificate just in case something went wrong with it.
I assume you've well configured your filezilla client on your notebook.

---

### Post by raymond.szebin on 2009-11-03
i think i should have mentioned this, the server is running in VMWare, not sure if this is an performance issue. anyway installed the Filezilla client on the Server running the VMWare, and now filezilla reports 
"Server did not properly shut down TLS connection" 
and log says 
::ffff:***.***.***.*** UNKNOWN nobody [03/Nov/2009:13:22:52 +0300] "" 550 -

I did regenerate the certificates about 3 times, i cannot be a certificate thing. 
Before, i installed FIlezilla Server (win32) and enabled TLS - all on my notebook to test filezilla client as reliable TLS client. as soon as i hit log in, i was prompted with certificate, i accepted it, and it was all sweet. After i found out Filezilla server is available only on win32 (wtf ?!) i stumbled upon proftpd and seemed like a winner solution. 
i have zero experience with secure ftp servers so i suppose i am prone to mistakes in this regard. 
appreciate all the help, but please indulge me a question:
what should happen upon successful connection ? will the ftp client be promoted with certificate? 

from the win32 log, 

2009-11-02 16:19:58 6716 0 Status: Connecting to ***.***.***.***:990...
2009-11-02 16:19:58 6716 0 Status: Connection established, initializing TLS...
2009-11-02 16:19:58 6716 0 Status: Verifying certificate...
2009-11-02 16:19:58 6716 0 Status: TLS/SSL connection established, waiting for welcome message...
2009-11-02 16:19:58 6716 0 Response: 220-FileZilla Server version 0.9.31 beta
2009-11-02 16:19:58 6716 0 Response: 220-written by Tim Kosse (Tim.Kosse@gmx.de)

so i guess that my problem is getting proftpd to talk to filezilla from what i gather.

---

### Post by raymond.szebin on 2009-11-03
frodon, when you say it can be a networking problem, what would you recommend i should check? maybe i am overlooking something :)

---

### Post by frodon on 2009-11-03
My TLS overall knowledge is not very high so i'm not sure to be able to help more. What i can say is that your configuration sounds good to me and that the proposed solution in the tutorial has been tested and works for many users.
On thing you can try is to post your issue on the proftpd forum too :
[http://forums.proftpd.org/smf/](http://forums.proftpd.org/smf/)

---

### Post by frodon on 2009-11-03
> **raymond.szebin said:**
> frodon, when you say it can be a networking problem, what would you recommend i should check? maybe i am overlooking something :)I'm thinking about the server firewall and the router forwarding the ports to the server. Except that i don't see what could prevent you from login on the network config side.

---

### Post by raymond.szebin on 2009-11-03
thank you very much for the support, i will post when i fix the problem and what i did to fix it.

---

### Post by raymond.szebin on 2009-11-03
after some log digging, i found this: 
Nov 03 17:01:51 mod_tls/2.1.2[6556]: SSL/TLS required but absent on control channel, denying  command

and "normal" filezilla trace looks like 

Status:   Connecting to x.y.z.k:21... 
Status:   Connection established, waiting for welcome message... 
Trace:   CFtpControlSocket::OnReceive() 
Response:   220 
Trace:   CFtpControlSocket::SendNextCommand() 
Command:   AUTH TLS 
Trace:   CFtpControlSocket::OnReceive() 
Response:   234 AUTH Command OK. Initializing SSL 
Status:   Initializing TLS... 
Trace:   CTlsSocket::Handshake() 

and mine looks like 

Trace:    ControlSocket.cpp(1056): CRealControlSocket::ContinueConnect(0p22f830) m_pEngine=0p19d1d28   caller=0p1a7fc68
Status:    Connecting to ***.***.***.***:990...
Status:    Connection established, initializing TLS...
Trace:    CTlsSocket::Handshake()
Trace:    CTlsSocket::OnRead()
Trace:    CTlsSocket::Handshake()
Trace:    CTlsSocket::OnRead()
Trace:    CTlsSocket::Handshake()
Trace:    CTlsSocket::OnRead()
Trace:    CTlsSocket::Handshake()
Error:    Connection timed out
Trace:    CFtpControlSocket::ResetOperation(2114)
Trace:    CControlSocket::ResetOperation(2114)
Error:    Could not connect to server




my pfortpd.conf looks like 




# Includes required DSO modules. This is mandatory in proftpd 1.3
#
Include /etc/proftpd/modules.conf
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

ServerName "Jerry"
ServerType standalone
DeferWelcome on
ServerIdent on "FTP Server ready."
DeferWelcome on
UseReverseDNS off
IdentLookups off

TimeoutLogin 20

RootLogin off


#MultilineRFC2228 on
#DefaultServer on
#ShowSymlinks off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200
TimeoutLogin 20

# It's better for debug to create log files
ExtendedLog /var/log/proftpd/ftp.log
TransferLog /var/log/proftpd/xferlog
SystemLog /var/log/proftpd/syslog.log

DisplayLogin welcome.msg
DisplayChdir .message
ListOptions "-l"

DefaultRoot /home/FTP-shared
#IdentLookups off
#ServerIdent off

# Lock all the users in home directory, ***** really important *****
# DefaultRoot ~

RootLogin off

MaxLoginAttempts 3

UseFtpUsers off

DenyFilter \*.*/

# Allow to restart a download
AllowStoreRestart on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd off

# Uncomment this if you would use TLS module:
TLSEngine on

# Uncomment this if you would use quota module:
#Quotas on

# Uncomment this if you would use ratio module:
#Ratios on

# Port 21 is the standard FTP port.
Port 990

MaxInstances 8


PersistentPasswd off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome to the SFTP Server"

# To prevent DoS attacks, set the maximum number of child processes
# to 30. If you need to allow more than 30 concurrent connections
# at once, simply increase this value. Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
# MaxInstances 10

# Set the user and group that the server normally runs at.
User nobody
Group nogroup

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask 022 022
# Normally, we want files to be overwriteable.
AllowOverwrite on
AuthAliasOnly on

UserAlias tom userftp

# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?pag...LSS-2004-10-02](http://security.lss.hr/index.php?pag...LSS-2004-10-02)
# It is on by default.
#DelayEngine off

<Directory /home/FTP-shared>
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

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
<Limit READ RMD DELE>
DenyAll
</Limit>

<Limit STOR CWD MKD>
AllowAll
</Limit>
</Directory>

<IfModule mod_tls.c>
TLSEngine on
TLSLog /var/log/proftpd/tls.log
TLSProtocol TLSv1
TLSOptions                              NoCertRequest
TLSVerifyClient                         off
TLSRequired                             ctrl
TLSRenegotiate                          required off

# Are clients required to use FTP over TLS when talking to this server?
TLSRequired on

# Server's certificate
TLSRSACertificateFile /etc/ftpcert/server.crt
TLSRSACertificateKeyFile /etc/ftpcert/server.key

# CA the server trusts
TLSCACertificateFile /etc/ftpcert/ca.crt

# Authenticate clients that want to use FTP over TLS?
TLSVerifyClient off
</IfModule>




anything wrong ? :(

---

### Post by frodon on 2009-11-03
Now that i see your config again there's one thing i forgot to ask you to test. Put your server on port 21 just to test, i have seen users having issues with connection from servers not on standard FTP port.
Second thing is to check that you have "mod_tls.c" in your /etc/proftpd/modules.conf file.

---

### Post by raymond.szebin on 2009-11-03
now filezilla reports 

17:41:12    Status:    Connecting to ***.***.***.***:21...
17:41:12    Status:    Connection established, waiting for welcome message...
17:41:12    Trace:    CFtpControlSocket::OnReceive()
17:41:12    Response:    220 FTP Server ready.
17:41:12    Trace:    CFtpControlSocket::SendNextCommand()
17:41:12    Command:    USER tom
17:41:12    Trace:    CFtpControlSocket::OnReceive()
17:41:12    Response:    550 SSL/TLS required on the control channel
17:41:12    Trace:    CControlSocket::DoClose(64)
17:41:12    Trace:    CFtpControlSocket::ResetOperation(66)
17:41:12    Trace:    CControlSocket::ResetOperation(66)
17:41:12    Error:    Could not connect to server
17:41:12    Trace:    CFileZillaEnginePrivate::ResetOperation(66)


and less /etc/proftpd/modules.conf

#
# This file is used to manage DSO modules and features.
#

# This is the directory where DSO modules reside

ModulePath /usr/lib/proftpd

# Allow only user root to load and unload modules, but allow everyone
# to see which modules have been loaded

ModuleControlsACLs insmod,rmmod allow user root
ModuleControlsACLs lsmod allow user *

LoadModule mod_ctrls_admin.c
LoadModule mod_tls.c

# Install proftpd-mod-mysql or proftpd-mod-pgsql to use this
#LoadModule mod_sql.c

# Install proftpd-mod-ldap to use this
#LoadModule mod_ldap.c

#
# 'SQLBackend mysql' or 'SQLBackend postgres' directives are required
# to have SQL authorization working. You can also comment out the
# unused module here, in alternative.
#

# Install proftpd-mod-mysql to use this
#LoadModule mod_sql_mysql.c

# Install proftpd-mod-pgsql to use this
#LoadModule mod_sql_postgres.c

LoadModule mod_radius.c
LoadModule mod_quotatab.c
LoadModule mod_quotatab_file.c

# Install proftpd-mod-ldap to use this
#LoadModule mod_quotatab_ldap.c

# Install proftpd-mod-pgsql or proftpd-mod-mysql to use this
#LoadModule mod_quotatab_sql.c
LoadModule mod_quotatab_radius.c
LoadModule mod_wrap.c
LoadModule mod_rewrite.c
LoadModule mod_load.c
LoadModule mod_ban.c
LoadModule mod_wrap2.c
LoadModule mod_wrap2_file.c
# Install proftpd-mod-pgsql or proftpd-mod-mysql to use this
#LoadModule mod_wrap2_sql.c
LoadModule mod_dynmasq.c


# keep this module the last one
LoadModule mod_ifsession.c



:///

my guess is that i messed something up since i get no 

Trace:   CFtpControlSocket::OnReceive() 
Response:   220 
Trace:   CFtpControlSocket::SendNextCommand() 
Command:   AUTH TLS 
Trace:   CFtpControlSocket::OnReceive() 
Response:   234 AUTH Command OK. Initializing SSL 

it just goes to the handshake ... but enough for today, i'm going home, live to fight another day

---

### Post by raymond.szebin on 2009-11-04
i have a breakthrough
[http://forum.filezilla-project.org/viewtopic.php?f=2&t=13717&sid=d11ef82c0b1af7f53b3f743f6f6c25df](http://forum.filezilla-project.org/viewtopic.php?f=2&t=13717&sid=d11ef82c0b1af7f53b3f743f6f6c25df)

and for future concern, proftpd 1.3.1 and latest filezilla will not work ... 

[http://forum.filezilla-project.org/viewtopic.php?f=2&t=7688](http://forum.filezilla-project.org/viewtopic.php?f=2&t=7688)

hope it helps someone out there!

---

### Post by frodon on 2009-11-04
Wow, well done, i wasn't aware of this.

So if i summarise, those using Karmic Koala which include proftpd 1.3.2-3 should not have this issue, good to know.

Thank you very much for your contribution, i will try to find a place for this in first post.

---

### Post by raymond.szebin on 2009-11-07
Hello everybody. 

For those of you that are faced for the first time with the concept of secure ftp server, and got through the thread so far, i thought i will post a copy of my 'proftpd.conf' as it can be quite a handful :) 
i have 
ubuntu 9.10
proftpd 1.3.2-3
filezilla 3.2.8.1

i followed all the steps presented in this very good guide, and it's working! w00t :D


here it goes!



# Includes required DSO modules. This is mandatory in proftpd 1.3
#
Include /etc/proftpd/modules.conf
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

ServerName "your server name goes here"
ServerType standalone
DeferWelcome on
ServerIdent on "FTP Server ready."
DeferWelcome on
UseReverseDNS on
IdentLookups off

TimeoutLogin 20

RootLogin off


MultilineRFC2228 on
DefaultServer on
ShowSymlinks on

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200
TimeoutLogin 30

# It's better for debug to create log files
ExtendedLog /var/log/proftpd/ftp.log
TransferLog /var/log/proftpd/xferlog
SystemLog /var/log/proftpd/syslog.log

DisplayLogin welcome.msg
DisplayChdir .message
ListOptions "-l"

DefaultRoot /home/FTP-shared
#IdentLookups off
#ServerIdent off

# Lock all the users in home directory, ***** really important *****
# DefaultRoot ~

RootLogin off

MaxLoginAttempts 3

UseFtpUsers off

DenyFilter \*.*/

# Allow to restart a download
AllowStoreRestart on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd off

# Uncomment this if you would use TLS module:
TLSEngine on

# Uncomment this if you would use quota module:
#Quotas on

# Uncomment this if you would use ratio module:
#Ratios on

# Port 21 is the standard FTP port.
Port 5555

MaxInstances 8

#MasqueradeAddress xxxxxxx.org
#MasqueradeAddress xx.xxx.xxx175
#PassivePorts 60000 60100

PersistentPasswd off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome to the SFTP Server"

# To prevent DoS attacks, set the maximum number of child processes
# to 30. If you need to allow more than 30 concurrent connections
# at once, simply increase this value. Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
# MaxInstances 10

# Set the user and group that the server normally runs at.
User nobody
Group nogroup

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask 022 022
# Normally, we want files to be overwriteable.
AllowOverwrite on
AuthAliasOnly on

UserAlias ##yourfavoriteusername## userftp

# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?pag...LSS-2004-10-02](http://security.lss.hr/index.php?pag...LSS-2004-10-02)
# It is on by default.
#DelayEngine off

<Directory /home/FTP-shared>
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

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
<Limit READ RMD DELE>
DenyAll
</Limit>

<Limit STOR CWD MKD>
AllowAll
</Limit>
</Directory>

<IfModule mod_tls.c>
TLSEngine on
TLSLog /var/log/proftpd/tls.log
TLSProtocol TLSv1
#TLSCipherSuite ALL:!ADH:!DES
#TLSVerifyClient on
TLSRequired on
TLSRenegotiate required off
#TLSOptions NoCertRequest


# Server's certificate
TLSRSACertificateFile /etc/ftpcert/server.crt
TLSRSACertificateKeyFile /etc/ftpcert/server.key

# CA the server trusts
TLSCACertificateFile /etc/ftpcert/ca.crt

# Authenticate clients that want to use FTP over TLS?
TLSVerifyClient off
</IfModule>



enjoy

---

### Post by pickarooney on 2009-11-16
I can't get the service to run on any port. I've tried using 5555, 1980 and 21 but [www.canyouseeme.org](www.canyouseeme.org) tells me the service is not running (I've opened the relevant ports in my router). 

Any ideas?

---

### Post by raymond.szebin on 2009-11-17
make sure that your server runs in the first place, before anything else, 

 ps axf | grep proftpd
 5087 pts/0    S+     0:00                      \_ grep proftpd
 5071 ?        Ss     0:00 proftpd: (accepting connections)

check config by using 

#proftpd -td5 
last line should be 

#Syntax check complete.

---

### Post by slvfx on 2009-12-03
Trying to set up the Proftpd server

> I am at the point of installing the tools. I have the script installed. When I put Proftptools in the command line it comes back with nothing. I ran a locate for the file and found /home/bob2/.bashrc to find a file to put it in as suggested by your instructions..bob2@bob-desktop:~$ locate .bashrc
/etc/bash.bashrc
/etc/skel/.bashrc
/home/bob2/.bashrc
/usr/share/base-files/dot.bashrc
/usr/share/doc/adduser/examples/adduser.local.conf.examples/bash.bashrc
/usr/share/doc/adduser/examples/adduser.local.conf.examples/skel/dot.bashrc

> I posted ProftpTools_dir=/home/username/ProftpTools-v1.0.2
export ProftpTools_dir at the bottom of the filebob2@bob-desktop:~$ sudo cat /home/bob2/.bashrc
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# don't overwrite GNU Midnight Commander's setting of `ignorespace'.
HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
    # We have color support; assume it's compliant with Ecma-48
    # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
    # a case would tend to support setf rather than setaf.)
    color_prompt=yes
    else
    color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
ProftpTools_dir=/home/username/ProftpTools-v1.0.2
export ProftpTools_dir
bob2@bob-desktop:~$

---

### Post by frodon on 2009-12-03
Maybe you just forgot to clocse your terminal and re-launch it so that the .bashrc is read again (with the update).

Anyway glad to see that some users use my old home made zenity script :)

---

### Post by tad1073 on 2010-01-05
EDIT: problem fixed

---

### Post by tad1073 on 2010-01-13
I am having problems adding users.

```
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias thomas userftp
UserAlias dale userftp
UserAlias tommy userftp
UserAlias linzi userftp


ServerName            "ThompsonFTP"
ServerType             standalone
DeferWelcome            on

MultilineRFC2228 on
DefaultServer            on
ShowSymlinks            on

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayLogin                    welcome.msg
DisplayChdir                   .message true
ListOptions                    "-l"

RequireValidShell         off

TimeoutLogin 20

RootLogin             off

# It's better for debug to create log files ;-)
ExtendedLog             /var/log/ftp.log
TransferLog             /var/log/xferlog
SystemLog            /var/log/syslog.log

#DenyFilter            \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart        on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port                1980

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 userftp

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                022    022

PersistentPasswd        off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /media/FamilyFiles/FTPShares

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
AllowUser dale
AllowUser tommy
AllowUser linzi
DenyALL
</Limit>

<Directory /media/FamilyFiles/FTPShares>
Umask 022 022
AllowOverwrite off
    <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
    AllowUser userftp
    AllowUser dale
    AllowUser tommy
    AllowUser linzi
    DenyAll
    </Limit>
</Directory>

<Directory /media/FamilyFiles/FTPShares/download/*>
Umask 022 022
AllowOverwrite off
    <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
    AllowUser userftp
    AllowUser dale
    AllowUser tommy
    AllowUser linzi    
    DenyAll
    </Limit>
</Directory>

<Directory /media/FamilyFiles/FTPShares/upload/>
Umask 022 022
AllowOverwrite on
    <Limit READ RMD DELE>
    AllowUser userftp
    AllowUser dale
    AllowUser tommy
    AllowUser linzi          
    DenyAll
        </Limit>

        <Limit STOR CWD MKD>
          AllowAll
        </Limit>
</Directory>
```

---

### Post by frodon on 2010-01-13
You are making confusion between system user and alias names. What you allow in <Directory > section are system users not alias names.

---

### Post by tad1073 on 2010-01-13
> **frodon said:**
> You are making confusion between system user and alias names. What you allow in <Directory > section are system users not alias names.

I changed it back to this:

```
# Choose here the user alias you want !!!!
UserAlias thomas userftp
```

but I still can't log in as a different user. All the users have user accounts on the server and have been added to the userftp group.

---

### Post by frodon on 2010-01-13
Yep because you need to set an alias name for these new users withe the *UserAlias* command.

Ex:
UserAlias *aliasname2* *systemuser2*

---

### Post by tad1073 on 2010-01-13
> **frodon said:**
> Yep because you need to set an alias name for these new users withe the *UserAlias* command.

Ex:
UserAlias *aliasname2* *systemuser2*

Thank you, got it working.

---

### Post by tad1073 on 2010-01-13
I am unable to access the ftp shares from windows 7 on the same box as ubuntu 10.04 desktop and from windows xp on another box.

---

### Post by frodon on 2010-01-14
This is more likely a network/firewall config issue on either your FTP server or your windows computer (maybe both).

To ease the debug i strongly advice you to put your FTP server on port 21 as it is sometimes harder to use another port for FTP on the network/firewall config side.

---

### Post by frodon on 2010-01-14
This is more likely a network/firewall config issue on either your FTP server or your windows computer (maybe both).

To ease the debug i strongly advice you to put your FTP server on port 21 as it is sometimes harder to use another port for FTP on the network/firewall config side.

---

### Post by cyberfloater on 2010-02-18
Hello,

I finally managed to get my local ftp server up and running, but there's is something I like to know.. I really did my best to locate the documentation somewhere but failed..

Is there any documentation on the parameters used within the <limit> section in the proftpd.conf?
[*edit: sorry, this was really a noob question afterall, by monitoring the output screen in gftp, it came to mind that these are the commands given for certain actions...* :biggrin:]

Lot's of thanx in advance :D

And another minor, maybe even irrelevant question.. Does the pass phrase for the ssl certificate need to be a rather long one, or can it be short like a 'normal' pass?

Cyberfloater

---

### Post by frodon on 2010-02-19
For documentation you should find all you need on the proftpd website there :
[http://www.proftpd.org/localsite/Userguide/linked/userguide.html](http://www.proftpd.org/localsite/Userguide/linked/userguide.html)

For the password, i guess it's always better to have at least 8 characters but it's just a feeling not something i can demonstrate.

---

### Post by frodon on 2010-02-19
For documentation you should find all you need on the proftpd website there :
[http://www.proftpd.org/localsite/Userguide/linked/userguide.html](http://www.proftpd.org/localsite/Userguide/linked/userguide.html)

For the password, i guess it's always better to have at least 8 characters but it's just a feeling not something i can demonstrate.

---

### Post by illy123 on 2010-02-24
Thanks very much for your guide.

I have a few questions.

When I log into the userftp account from filezilla I am still able to open my main account's home folder. Is it possible to allow access to only two folders - download and upload? I don't want my friend's being able to see what is in my home folder.

How would I upload files to the download directory remotely? Would I be able to do this via ssh?

So I guess in short:

1. Limit userftp only to download and upload
2. Find a way to upload files to the 'download' folder remotely (e.g. ssh).

Also, if I create any more folders (e.g. in the download or upload folder) will I need to change my log or chmod then in any way?

Thanks :)

---

### Post by frodon on 2010-02-25
1- if you follow the tutorial your user will be locked into it's own home directory.
2- This is the purpose of the upload directory, if you want to be able to upload in the download directory as well take the upload directory as example to configure it.

---

### Post by frodon on 2010-02-25
1- if you follow the tutorial your user will be locked into it's own home directory.
2- This is the purpose of the upload directory, if you want to be able to upload in the download directory as well take the upload directory as example to configure it.

---

### Post by illy123 on 2010-02-25
> **frodon said:**
> 1- if you follow the tutorial your user will be locked into it's own home directory.
2- This is the purpose of the upload directory, if you want to be able to upload in the download directory as well take the upload directory as example to configure it.

Thanks very much for your response.

I tried my best to follow this word for word; here is what my config file looks like:

> #
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf


# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6                on
# If set on you can experience a longer connection delay in many cases.
IdentLookups            off

ServerName            "Debian"
ServerType            inetd
DeferWelcome            off

MultilineRFC2228        on
DefaultServer            on
ShowSymlinks            on

TimeoutNoTransfer        600
TimeoutStalled            600
TimeoutIdle            1200

DisplayLogin                    welcome.msg
DisplayChdir                   .message true
ListOptions                    "-l"

DenyFilter            \*.*/

# VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

# Use this to jail all users in their homes 
# DefaultRoot            ~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell        off

# Port 21 is the standard FTP port.
Port                21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress        1.2.3.4

# This is useful for masquerading address with dynamic IPs:
# refresh any configured MasqueradeAddress directives every 8 hours
<IfModule mod_dynmasq.c>
# DynMasqRefresh 28800
</IfModule>

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances            30

# Set the user and group that the server normally runs at.
User                proftpd
Group                nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                022  022
# Normally, we want files to be overwriteable.
AllowOverwrite            on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd        off

# This is required to use both PAM-based authentication and local passwords
# AuthOrder            mod_auth_pam.c* mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile            off

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        off
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine off
</IfModule>

#
# Alternative authentication frameworks
#
#Include /etc/proftpd/ldap.conf
#Include /etc/proftpd/sql.conf

#
# This is used for FTPS connections
#
#Include /etc/proftpd/tls.conf

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User                ftp
#   Group                nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias            anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser    on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell        off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients            10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin            welcome.msg
#   DisplayChdir        .message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask                022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

Regarding uploading - I want to be able to put files into the download directory somehow so that others can download them. Could this be achieved up uploading to the upload directory and then using vnc through an ssh tunnel to 'sudo nautilus' and copy and paste them to the download directory and then change group and ownership to userftp?

Or would it be possible to share the folder over my LAN so I can just log in from my mac using the userftp login and copy files over to it - or will that screw up my permissions?

Thanks for your help.

---

### Post by frodon on 2010-02-25
Ok, first jsut in case this is not clear, this thread is dedicated to the support of the tutorial in post #1 and not about Proftpd custom configurations in general.

Your proftpd.conf file is a custom/unknown one, i can't guaranty its security and won't provide support about it in this thread since it is unrelated to the proftpd.conf file posted in first post.

---

### Post by illy123 on 2010-02-25
> **frodon said:**
> Ok, first jsut in case this is not clear, this thread is dedicated to the support of the tutorial in post #1 and not about Proftpd custom configurations in general.

Your proftpd.conf file is a custom/unknown one, i can't guaranty its security and won't provide support about it in this thread since it is unrelated to the proftpd.conf file posted in first post.

Oh I see,

Sorry I got a bit confused; should I replace the config file I have with the one you pasted in the first post?

In that case it gives me an error:

"unkown configuration directive 'DisplayFirstChdir' on line 20" of my proftpd.conf

---

### Post by frodon on 2010-02-25
It depends what you want to do, if the tutorial suit your needs then yes you should better follow the whole tutorial as we (all the users using it) have experience about this configuration and we are confident about the security of this configuration.

About DisplayFirstChdir error it seems latest proftpd version made this command obsolete so use DisplayChdir command instead, i will update first post accordingly.

---

### Post by illy123 on 2010-02-25
> **frodon said:**
> It depends what you want to do, if the tutorial suit your needs then yes you should better follow the whole tutorial as we (all the users using it) have experience about this configuration and we are confident about the security of this configuration.

About DisplayFirstChdir error it seems latest proftpd version made this command obsolete so use DisplayChdir command instead, i will update first post accordingly.

I see, I've changed it and it runs :)

However, now I am not able to log into as I get a 530 access denied message. I think this is similar to what you mention on your first message - as I created the account via the command line.

---

### Post by frodon on 2010-02-25
Yes it happens often, it is either a configuration issue, a rights management issue on folders or password issue.

So check your folder rights and set another password for *userftp* using command line (see fist post), if you use the proftpd.conf file from first post with no modification then your FTP config shouldn't be the issue.

---

### Post by illy123 on 2010-02-25
> **frodon said:**
> Yes it happens often, it is either a configuration issue, a rights management issue on folders or password issue.

So check your folder rights and set another password for *userftp* using command line (see fist post), if you use the proftpd.conf file from first post with no modification then your FTP config shouldn't be the issue.

Thanks for your patience and help.

I'm moving forward :p I'm able to log into and access the downloads and the uploads directory however I cannot open anything I have in the uploads directory. I have a look at permissions with nautilus and they are set as owner userftp, and group userftp. However I get the error: "550 no such file or directory"

---

### Post by frodon on 2010-02-25
If you want to access these directories with your own user the best way i think is to give your download and upload directory group access (read or/and write) and to make your user member of the *userftp* group.

By default, following the tutorial the rights on the download/upload directories are restrictive for highest security but for sure you can modify them for convenience, however i strongly advice you not to give more than group access.

---

### Post by illy123 on 2010-02-25
> **frodon said:**
> If you want to access these directories with your own user the best way i think is to give your download and upload directory group access (read or/and write) and to make your user member of the *userftp* group.

By default, following the tutorial the rights on the download/upload directories are restrictive for highest security but for sure you can modify them for convenience, however i strongly advice you not to give more than group access.

Sorry forgive my english (French but learning :p) - I meant that when I login into my ftp account I am not able to access the files I have in my upload directory. E.g. I uploaded a picture just to test it out but when I try and download it I get '550 /upload/xxxx.jpg: No such file or directory".

---

### Post by frodon on 2010-02-25
Ok i see, by default read is denied in the upload directory according to the proftpd.conf given in first post.

Relevant section is :
```
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
```

Just modify it as follow :

```
<Directory /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD **READ**>
      	AllowAll
    	</Limit>
</Directory>
```

My english is not perfect too ;)

---

### Post by frodon on 2010-02-25
Ok i see, by default read is denied in the upload directory according to the proftpd.conf given in first post.

Relevant section is :
```
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
```

Just modify it as follow :

```
<Directory /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD **READ**>
      	AllowAll
    	</Limit>
</Directory>
```

---

### Post by woofire on 2010-02-25
Hello,

This is my first FTP build and everything seems to be good except a few last things.

Let me explain a little about my build:
- running the latest long term support ubuntu 8.4 I believe server so no gui 
- proftpd does not allow you to manage virtual users so I was forced to create system users
- users are "jailed" via proftpd.conf to the "/home/baseuser/vendor" dir's, none have /bin access and use that path as their home dir as well
- each vendor is the owner of their dir and is a member of a vendors group so that the baseuser can allocate files to each users dir
- standard FTP xfer works fine each vendors

Problem:

SSL quit working

[LIST]
[*]at first I could connect with either SSL or passive FTP
[*]SSL quit working when I tried to force it at connection in proftpd.conf
[*]I commented it back out and now SSL connections look like this:
220 ProFTPD 1.3.1 Server (The FTP Server) [::ffff:#.#.#.#]       AUTH SSL
234 AUTH SSL successful
       PBSZ 0
- I seem to connect but I can not access the dir's and it kicks me out immediately
[/LIST]

Even when I uncomment the #Include /etc/proftpd/tls.conf section I have no luck.  I shouldn't need it as I entered my own RSA info already.

Here is a close copy of my proftpd.conf file any help is appreciated:

```

#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6                on

ServerName            "The FTP Server"
ServerType            standalone
DeferWelcome            off

MultilineRFC2228        on
DefaultServer            on
ShowSymlinks            on

TimeoutNoTransfer        600
TimeoutStalled            600
TimeoutIdle            1200

DisplayLogin                   /home/ftp/welcome.msg
DisplayChdir                   .message true
ListOptions                    "-l"

DenyFilter            \*.*/

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell        off

# Port 21 is the standard FTP port.
Port                21

<IfModule mod_tls.c>
    TLSEngine on
    TLSLog /var/ftpd/tls.log
    TLSProtocol TLSv1

    # Are clients required to use FTP over TLS when talking to this server?
    TLSRequired on

    # Server's certificate
    TLSRSACertificateFile /etc/ftpcert/server.crt
    TLSRSACertificateKeyFile /etc/ftpcert/server.key

    # CA the server trusts
    TLSCACertificateFile /etc/ftpcert/ca.crt

    # Authenticate clients that want to use FTP over TLS?
    TLSVerifyClient off
</IfModule>


# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress        1.2.3.4

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances            30

# Set the user and group that the server normally runs at.
User                proftpd
Group                nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                022  022
# Normally, we want files to be overwriteable.
AllowOverwrite            on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd        off

# This is required to use both PAM-based authentication and local passwords
# AuthOrder            *mod_auth_pam.c mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile            off

# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend 
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
#<IfModule mod_sql.c>
# SQLBackend            mysql
#</IfModule>

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        off
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine off
</IfModule>

#
# Alternative authentication frameworks
#
#Include /etc/proftpd/ldap.conf
#Include /etc/proftpd/sql.conf

#
# This is used for FTPS connections
#
#Include /etc/proftpd/tls.conf

# Use this to jail all users in their homes
DefaultRoot      ~

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User                ftp
#   Group                nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias            anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser    on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell        off
# 
#   # Limit the maximum number of anonymous logins
   MaxClients            10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
   DisplayLogin            ./home/ftp/welcome.msg
#   DisplayFirstChdir        .message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory ./home/FTP/anonymous>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask                022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

#VALID LOGINS
<Limit LOGIN>
AllowUser baseuser
AllowUser vendor1
AllowUser vendor2
DenyALL
</Limit>

<Directory /home/FTP/baseuser>
Umask 022 022
AllowOverwrite on
        <Limit ALL>
            Order Allow,Deny
            AllowUser baseuser
            Deny All
        </Limit>

    <Limit CDUP CWD LIST MDTM NLST PWD RNFR STAT XCUP XCWD XPWD>
        AllowAll
    </Limit>

    <Limit APPE DELE MKD RMD RNTO STOR STOU XMKD XRMD>
        AllowAll
    </Limit>
</Directory>

<Directory /home/FTP/baseuser/vendor1>
Umask 022 022
AllowOverwrite on
        <Limit ALL>
            Order Allow,Deny         
            AllowUser vendor1
            AllowUser baseuser
            Deny ALL
        </Limit>

        <Limit CDUP CWD LIST MDTM NLST PWD RNFR STAT XCUP XCWD XPWD>
                AllowAll
        </Limit>

        <Limit APPE DELE MKD RMD RNTO STOR STOU XMKD XRMD>
                AllowAll
        </Limit>
</Directory>

<Directory /home/FTP-shared/baseuser/vendor2>
Umask 022 022
AllowOverwrite on
        <Limit ALL>
                Order Allow,Deny
                AllowUser vendor2
                AllowUser baseuser
        Deny ALL
        </Limit>

        <Limit CDUP CWD LIST MDTM NLST PWD RNFR STAT XCUP XCWD XPWD>
                AllowAll
        </Limit>

        <Limit APPE DELE MKD RMD RNTO STOR STOU XMKD XRMD>
                AllowAll
        </Limit>
</Directory>


```

---

### Post by illy123 on 2010-02-25
> **frodon said:**
> Ok i see, by default read is denied in the upload directory according to the proftpd.conf given in first post.

Relevant section is :
```
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
```Just modify it as follow :

```
<Directory /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
    <Limit RMD DELE>
          DenyAll
        </Limit>

        <Limit STOR CWD MKD **READ**>
          AllowAll
        </Limit>
</Directory>
```My english is not perfect too ;)

Thanks so much for your help :)

I have one final issue; now when I open the download and try and download a file the browser gets stuck on 'waiting' or a few seconds and then starts downloading with a speed of 0.1kB/s and claims it will take 400 days. Is this is a problem with my setup or my home internet connection?

Edit:

I just tried uploading and the speed was great, but downloading appears to be non existant.

Edit2:

This is really weird; after 20/30 seconds of 0kB/s it picks up to a very fast speed and then sticks at around 200kB/s

I have it configured as starting from inetd rather than standalone not sure if that might be the problem.

Edit3:

I've changed it to standalone (and commented out the ftp line in inetd.conf) however I still get a speed of 0 until it downloads the first 8 bytes, then it soars above my home's upload bandwidth limit (1.2MB/s) and returns to 200kB/s gradually. It is as if it is somehow 'buffering' it, as my home upload speed is around 250kB/s.

---

### Post by illy123 on 2010-02-27
Also one more question :p

I want to samba share this folder so that other computers on my network can read and write to it. When I do this ubuntu asks me: "do you want nautilus to add these permissions to the folder automatically?". Will this screw up previously set permissions?

Thanks.

---

### Post by frodon on 2010-02-27
I don't know, i never tried this so maybe just try ans see how the rights are modified.

---

### Post by Gala Tux-Fan on 2010-02-27
Hi and thanks for this really good howto
Ok this may sound really stupid but I managed to start the daemon in the terminal but what addree do I have to type in my web browser to access my shared files from anywhere? (I am a newb..)
I'm kinda stuck...if anobody could help it would be really cool
thanks;)

---

### Post by Stayblind on 2010-03-04
[B]nice guide!

I'm having some problems I hoped you could troubleshoot for me.

(I have no Linux or other OS CLI experience, just thought you should know.)

After setting up proftpd.conf and trying to restart the FTP server, I am getting this error:[/B]

```
nicholas@Kids Computer:~$ sudo /etc/init.d/proftpd restart
sudo: unable to resolve host Kids Computer
 * Stopping ftp server proftpd                                           [ OK ] 
 * Starting ftp server proftpd                                                   
- warning: unable to determine IP address of 'Kids_Computer'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
                                                                         [fail]
```[B]

Here is my proftpd.conf:

[/B][ATTACH]148937[/ATTACH]

[B]Like I said, I have NO experience with Linux or setting up FTP servers.  I am currently a student and would like to host my work from home so I can access it from school.  

If anyone would like to help me you can contact me at [/B][EMAIL="stayblind@gmail.com"]stayblind@gmail.com[/EMAIL] [B]or my AIM is USDLatimer2003.  I will also be checking back here.

Any help is appreciated. :)


[/B]

---

### Post by frodon on 2010-03-04
Change the following lines :
```
UserAlias C.F userftp
ServerName			"C.FTP"
```

One must choose simple names for these parameters (Don't use "." "-" "_" ...) to avoid problems.

---

### Post by CurtBruno on 2010-03-24
Hi,
I've encountered an error whenever I tried to initiate a SFTP session on another PC and what I get is:

> Status:    Connecting to xx.xx.xx.xx...
Response:    fzSftp started
Command:    open "xxx@xx.xx.xx.xx" 22
Error:    Could not connect to server
Status:    Waiting to retry...


and,
i kept getting the "first attempt" of entering passphrase wrong, but the second attempt is always correct.

> sudo /etc/init.d/proftpd restart
 * Stopping ftp server proftpd                                           [ OK ] 
 * Starting ftp server proftpd                                                  
Please provide passphrases for these encrypted certificate keys:
RSA key for the 127.0.1.1#21 (xxx) server: 
Verifying - RSA key for the 127.0.1.1#21 (xxx) server: 

Passphrases do not match.  Please try again.
RSA key for the 127.0.1.1#21 (xxx) server: 
Verifying - RSA key for the 127.0.1.1#21 (xxx) server: 
                                                                         [ OK ]


anyone know what happened?
is there a bug with the passphrase entering command?
first time always wrong passphrase but second will be correct. i'm very sure it's typo the first time... i've tried copy and paste the password when prompted... so there couldn't be any typo.

and the SFTP error too.

Curtis

---

### Post by seng1978 on 2010-03-29
> **woofire said:**
> Hello,

This is my first FTP build and everything seems to be good except a few last things.

Let me explain a little about my build:
- running the latest long term support ubuntu 8.4 I believe server so no gui 
- proftpd does not allow you to manage virtual users so I was forced to create system users
- users are "jailed" via proftpd.conf to the "/home/baseuser/vendor" dir's, none have /bin access and use that path as their home dir as well
- each vendor is the owner of their dir and is a member of a vendors group so that the baseuser can allocate files to each users dir
- standard FTP xfer works fine each vendors

Problem:

SSL quit working

[LIST]
[*]at first I could connect with either SSL or passive FTP
[*]SSL quit working when I tried to force it at connection in proftpd.conf
[*]I commented it back out and now SSL connections look like this:
220 ProFTPD 1.3.1 Server (The FTP Server) [::ffff:#.#.#.#]       AUTH SSL
234 AUTH SSL successful
       PBSZ 0
- I seem to connect but I can not access the dir's and it kicks me out immediately
[/LIST]

Even when I uncomment the #Include /etc/proftpd/tls.conf section I have no luck.  I shouldn't need it as I entered my own RSA info already.

Here is a close copy of my proftpd.conf file any help is appreciated:




I got the same problem with fireftp, everything shows succesfull but no directory listing and im not connected.

So I tried Filezilla with explicit SSL and BANG it works!
How do I get Fireftp to work as well tho?

---

### Post by frodon on 2010-03-29
Does Fireftp supports FTP with full TLS encryption ? I know filezilla does but i'm not sure about Fireftp.

---

### Post by khodamn on 2010-04-04
I follwed the instruction precisely, but no luck with TLS/SSL connection. When i sniff the packets, i can see the username and passwd in plain text.

---

### Post by frodon on 2010-04-04
You shouldn't, check that you force the use of TLS encryption in your config.

---

### Post by rixter07 on 2010-04-04
I'm getting that 530 error with proftpd, and am at my wit's end trying to debug it. 
This is a really excellent thread, however, so I hope someone could please help me to see the error of my ways. :/

I've attached my proftpd.conf file, which I attempted to resemble the example shown at the beginning of this thread.

To start with, there's my error message:
ftp -P 1024 avatar@184.73.199.128
Connected to 184.73.199.128.
220 ProFTPD 1.3.1 Server ready.
331 Password required for avatar
Password: 
530 Login incorrect.
ftp: Login failed

Here's what my ftp directories look like:
drwxr-xr-x  2 root nogroup 4096 2010-03-23 18:14 ftp
drwxr-xr-x  4 root nogroup 4096 2010-04-02 15:02 FTP-shared

and in FTP-shared:
drwxr-xr-x 4 root nogroup 4096 2010-04-02 15:02 .
drwxr-xr-x 5 root root    4096 2010-04-02 14:56 ..
drwxr-xr-x 2 root root    4096 2010-04-02 15:02 download
drwxrwxrwx 2 root root    4096 2010-04-02 15:02 upload

I can start/stop proftpd fine, and I can see it is listening on port 1024 (this is at Amazon Web Services):
> netstat -nap 
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1217/apache2    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1120/sshd       
tcp        0      0 0.0.0.0:5432            0.0.0.0:*               LISTEN      21309/postgres  
tcp        0      0 10.252.46.20:22         67.173.232.99:49383     ESTABLISHED 1572/1          
tcp        0    288 10.252.46.20:22         67.173.232.99:49373     ESTABLISHED 1531/0          
tcp        0      0 10.252.46.20:21         67.173.232.99:50187     TIME_WAIT   -               
tcp6       0      0 :::1024                 :::*                    LISTEN      2108/proftpd: (acce
tcp6       0      0 :::21                   :::*                    LISTEN      26636/xinetd    
tcp6       0      0 :::22                   :::*                    LISTEN      1120/sshd       
tcp6       0      0 :::5432                 :::*                    LISTEN      21309/postgres  
udp        0      0 127.0.0.1:32769         127.0.0.1:32769         ESTABLISHED 21309/postgres  
udp        0      0 0.0.0.0:68              0.0.0.0:*                           799/dhclient3   



Any help will be much appreciated! (Trying to get this finished for a client!)

Thanks in advance,
Rick

---

### Post by frodon on 2010-04-05
Try to set it on port 21 for debug purpose, try to reset the password using command line, check directory rights, disable IPV6 if you don't need it.

These are the things i would try if i was in your case.

---

### Post by khodamn on 2010-04-05
Can someone help me to tighten my security up. I dont wanna users to be able to browse through root dir. I don't know what shell to use. I have a Download and Upload map. I just want users to be able to browse through these dir's and nothing else.

---

### Post by rhunt on 2010-04-05
the easiest i've seen

---

### Post by frodon on 2010-04-06
> **khodamn said:**
> Can someone help me to tighten my security up. I dont wanna users to be able to browse through root dir. I don't know what shell to use. I have a Download and Upload map. I just want users to be able to browse through these dir's and nothing else.It's the purpose of the DefaultRoot command to define in which directory to lock users. Play with it to get what you're looking for.

---

### Post by peman on 2010-04-07
Hello,
First of all, thank you for this great HOWTO!!

I had it working for a year, then i change the location of the folders to /var/www after that everything screwed up. I got the 530 Login incorrect, everytime i try to login. I tried to change the user accounts but that didnt work so i changed it back to the exact same thing as in your howto.

i have now recover it back to /home/userftp and the logins. But i still get the 530 Login incorrect.

Any ideas?

My system is Debian etch with no X and ProFTPD Version 1.3.0.

I really need help this.

Thanks

/Martin

---

### Post by volkovski on 2010-04-12
Hello, thank you for your HOW TO.
Im newbie in proftpd configuration , I need your help.  I'm trying to configure proftpd and I'd like to add new user, whom isn't created under ubuntu  users and groups. I need special user, which can log in to my FTP but doesn't to UBUNTU. Please help I'm noob, sry for my eng. Please show my any example configuration.

---

### Post by frodon on 2010-04-12
> **volkovski said:**
> I need special user, which can log in to my FTP but doesn't to UBUNTU. Please help I'm noob, sry for my eng. Please show my any example configuration.First thing why ?

Anyway standard proftpd config don't allow this however there is an alternative way to create FTP users which is not covered in this tutorial. See here for details:
[http://www.proftpd.org/localsite/Userguide/linked/c572.html#AEN576](http://www.proftpd.org/localsite/Userguide/linked/c572.html#AEN576)

---

### Post by angry_norwegian on 2010-04-15
I'm using ProFTPd, and have followed [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588).

I get 530 Login incorrect error, although I've quintuple-checked that alias, username, folder permissions, port and password are correct. Anyone know what to do?

My proftp.conf: [http://paste.ubuntu.com/414711/](http://paste.ubuntu.com/414711/)

EDIT: I found the error, I put the conf in /etc/ instead of /etc/proftpd/. Maybe update first post to say Edgy eft *and later*?

Thanks for the guide, though.

---

### Post by MadMikeyB on 2010-04-25
Hey all, I seem to be having some troubles, not sure exactly what is going wrong. Can anyone take a look at my errors and see whats up? Thanks

```
mikey@ubuntu:~$ sudo apt-get install proftpd gproftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting proftpd-basic instead of proftpd
E: Couldn't find package gproftpd
mikey@ubuntu:~$ sudo apt-get install proftpd-basic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++6-4.3-dev libconvert-binhex-perl libqca2 libsoap-lite-perl libmime-types-perl libcrypt-ssleay-perl
  libnet-ssleay-perl g++-4.3 libass1 libossp-uuid-perl libdvbpsi4 libmime-tools-perl libossp-uuid15 libx264-65
  libio-stringy-perl libnet-google-perl libemail-date-format-perl nullmailer libphonon4 libmime-lite-perl
  libfcgi-perl libid3tag0 libjcode-pm-perl libio-socket-ssl-perl libvlccore0 qt4-qtconfig libnet-libidn-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openbsd-inetd
Suggested packages:
  proftpd-doc proftpd-mod-mysql proftpd-mod-pgsql proftpd-mod-ldap proftpd-mod-odbc proftpd-mod-sqlite
The following NEW packages will be installed
  openbsd-inetd proftpd-basic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 836kB of archives.
After this operation, 2,195kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://gb.archive.ubuntu.com karmic/main openbsd-inetd 0.20080125-2ubuntu1
  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic/universe proftpd-basic 1.3.2-3
  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openbsd-inetd/openbsd-inetd_0.20080125-2ubuntu1_i386.deb  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/p/proftpd-dfsg/proftpd-basic_1.3.2-3_i386.deb  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
mikey@ubuntu:~$ 

```

EDIT: this was fixed by gedit /etc/apt/sources.list and removing gb. from gb.archive.ubuntu.com

---

### Post by mustacheride on 2010-04-30
You should maybe include this in the FAQ as I am relatively sure it is a common problem among newbies like myself, took me the better part of 2 or 3 hours to figure this out, port conflicts, frustration is thy name.


ProFtpd...Unbindable port 21

[http://ubuntuforums.org/archive/index.php/t-822706.html](http://ubuntuforums.org/archive/index.php/t-822706.html)

The problem is the default FTP service installed in Ubuntu Server (yeah, I should've known) that you just comment out in the /etc/inetd.conf

---

### Post by frodon on 2010-04-30
Added to first post in last section, thanks for helping it is more than welcome :)

---

### Post by mcfil on 2010-05-25
hello frodon

i wanna thank you for ya verryyy goood tutorial right here! :) but as you can imagine, i got also a lil problem with my proftpd.conf....so let me explain...

my conf-file is as like as yours!! only a few changes (port, servername, etc) :)

when i log in with my user "userftp" i can directly see /home/FTP-shared! soo thats fine, ok...BUT now...when i click to go "BACK" in the directories, i can navigate through the whole pc!!!!! please tell me how i can LOCK INTO HOMEDIRECTORY!!!?? because...in the proftpd.conf i see the line with the right commands!

sorry my ubuntu is in an virtual machine and i can't copy and paste ^^
i will post the conf-file....

thx for your help
p.s. i saw a line wich contains MAYBE the problem?! ...this here:

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
           <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>    <---- maybe one of these have to be changed or somethin like that?!??

big big thx....
bye 
Fil

---

### Post by frodon on 2010-05-25
Check the home directory you set for your ftp user, in the proftpd.conf file the Default *DefaultRoot* command is the one which define where to lock the user (either ~ for the users's home dir or a complete path).

---

### Post by etamax on 2010-05-25
> **mcfil said:**
> hello frodon

i wanna thank you for ya verryyy goood tutorial right here! :) but as you can imagine, i got also a lil problem with my proftpd.conf....so let me explain...

my conf-file is as like as yours!! only a few changes (port, servername, etc) :)

when i log in with my user "userftp" i can directly see /home/FTP-shared! soo thats fine, ok...BUT now...when i click to go "BACK" in the directories, i can navigate through the whole pc!!!!! please tell me how i can LOCK INTO HOMEDIRECTORY!!!?? because...in the proftpd.conf i see the line with the right commands!

sorry my ubuntu is in an virtual machine and i can't copy and paste ^^
i will post the conf-file....

thx for your help
p.s. i saw a line wich contains MAYBE the problem?! ...this here:

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
           <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>    <---- maybe one of these have to be changed or somethin like that?!??

big big thx....
bye 
Fil

Have you put
DefaultRoot ~
in the config file?

---

### Post by mcfil on 2010-05-25
hey guys!

yess, guys... i got the lines in my config-files!! thats why i'm about to get crazy!! :P
i have this

DefaultRoot ~

and i also tried the whole path, like u said, frodon!

DefaultRoot /home/FTP-shared

but no chance!! i can navigate trough my whole computer! :(

---

### Post by mcfil on 2010-05-25
sorry....i forgot my conf.file...

-------------------------------------------------
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias sauron userftp

ServerName            "mein ftp server"
ServerType             standalone
DeferWelcome            on

MultilineRFC2228 on
DefaultServer            on
ShowSymlinks            off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayChdir                    .message
ListOptions                    "-l"

RequireValidShell         off

TimeoutLogin 20

RootLogin             off

# It's better for debug to create log files ;-)
ExtendedLog             /var/log/ftp.log
TransferLog             /var/log/xferlog
SystemLog            /var/log/syslog.log

#DenyFilter            \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart        on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port                21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                022    022

PersistentPasswd        off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "willkommen daheim"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
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
---------------------------------------------------------------------------------------------------------------

---

### Post by etamax on 2010-05-26
Can you attach the three log files?

---

### Post by frodon on 2010-05-26
I bet your ftp user *(userftp)* don't have "/home/FTP-shared" well set as home directory as the *DefaultRoot ~* command will look this field to know where to lock the user.

---

### Post by mcfil on 2010-05-26
hmmmm when i go to SYSTEM - USER AND GROUPS......i see my accounts...once my personally account (mcfil) and once the user "USERFTP". so, now when i click preferences, there is a field with "personally folder - /home/FTP-shared" <<<--- well, guys...so thats right!!! or not?!??

---

### Post by frodon on 2010-05-26
If there's no typo it should be right but i have seen some strangeness already with user creation. So either re-create your user or save it again then reboot, maybe things have not been updated.

---

### Post by mcfil on 2010-05-26
okay i will try it...i've set the usercreation by your howto...via console..next time i will try to do it via GUI...let me test.....:)

thx a lot bye bye

//EDIT//

no chance, frodon! i tried...i've created "userftp" via GUI, edited new the proftpd.conf...nothin..still the same problem! its veryyy veeeerry strange! :(

no ideas?! :( i think i have to go back to windows server 2008! :((((

---

### Post by thrawn717 on 2010-05-27
Hey All, 

I am trying to figure out how to get the permissions for the ftp folders to work correctly. 
I have 2 different users setup just for the FTP access userftp and user2 what I want to do is all userftp to download from the download folder only. And then user2 I want to allow them to upload files to the upload folder only. How do I do this? Below is a copy of my proftpd.conf file. Most of this file I have taken from other peoples posts on this forum and then made some changes to it. 

Thanks

#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

AllowOverwrite                  on
AuthAliasOnly                   on

# Choose here the user alias you want !!!!
UserAlias                       upload userftp

ServerName                      "McDade-Woodcock FTP Test Server"
ServerType                      standalone
DeferWelcome                    on

MasqueradeAddress               my.ip.is.here
PassivePorts                    60000 60100 #this is a range, not just two ports

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    off

TimeoutNoTransfer               600
TimeoutStalled                  100
TimeoutIdle                     2200

DisplayFirstChdir               .message
ListOptions                     "-l"

RequireValidShell               off

TimeoutLogin 20

RootLogin                       on

# It's better for debugging purposes to create log files
ExtendedLog                     /var/log/ftp.log
TransferLog                     /var/log/xferlog
SystemLog                       /var/log/syslog.log

#DenyFilter                     \*.*/

# I don't choose to use /etc/ftpusers file (use it to ban users by
just writing their username in it)
UseFtpUsers                     off

# Allow to restart a download
AllowStoreRestart               on

# Port 21 is the standard FTP port, so don't use it for security
reasons (choose here the port you want)
Port                            21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                            nobody
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022     022

PersistentPasswd                off

MaxClients                      8
MaxClientsPerHost               8
MaxClientsPerUser               8
MaxHostsPerUser                 8

# Display a message after a successful login
AccessGrantMsg                  "Welcome to McDade-Woodcock's FTP Test Server"
# This message is displayed for each access good or not
ServerIdent                     on       "McDade-Woodcock FTP Test Server"

# Set /home/FTP-shared directory as home directory
DefaultRoot                     /home/FTP-shared

# Lock all the users in home directory,
#    ***** really important *****
DefaultRoot                     ~

MaxLoginAttempts                3

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
AllowUser user2
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
        Order Allow,Deny
        AllowUser userftp
        AllowUser user2 
        Deny ALL
    </Limit>
    <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
    DenyAll
    </Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
        Order Allow,Deny
        AllowUser userftp
        Deny ALL
    </Limit>
    <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
    DenyAll
    </Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
        <Limit ALL>
        Order Allow,Deny
        AllowUser user2 
        Deny ALL
    </Limit>
    <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
          AllowAll
        </Limit>

        <Limit STOR CWD MKD>
          AllowAll
        </Limit>
</Directory>

---

### Post by frodon on 2010-05-28
Your config looks good, you just need to define an alias name for user2.

---

### Post by thrawn717 on 2010-05-28
i added user2 as an UserAlias but when I restarted the FTP server I can't logon to the ftp site using any of the user logins. I get error 530. I have been messing with this thing all morning and I can't get it working. What am I doing wrong? ](*,)


#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

AllowOverwrite                  on
AuthAliasOnly                   on

# Choose here the user alias you want !!!!
UserAlias                       upload userftp
UserAlias            upload user2

ServerName                      "McDade-Woodcock Test FTP Server"
ServerType                      standalone
DeferWelcome                    on

MasqueradeAddress               192.168.1.65
PassivePorts                    60000 60100 #this is a range, not just two ports

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    off

TimeoutNoTransfer               600
TimeoutStalled                  100
TimeoutIdle                     2200

DisplayLogin            welcome.msg
DisplayChdir                 .message true
ListOptions                     "-l"

RequireValidShell               on

TimeoutLogin 20

#RootLogin                       on

# It's better for debugging purposes to create log files
ExtendedLog                     /var/log/ftp.log
TransferLog                     /var/log/xferlog
SystemLog                       /var/log/syslog.log

#DenyFilter                     \*.*/

# I don't choose to use /etc/ftpusers file (use it to ban users by
#just writing their username in it)
UseFtpUsers                     off

# Allow to restart a download
AllowStoreRestart               on

# Port 21 is the standard FTP port, so don't use it for security
#reasons (choose here the port you want)
Port                            21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                            nobody
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022     022

PersistentPasswd                off

MaxClients                      8
MaxClientsPerHost               8
MaxClientsPerUser               8
MaxHostsPerUser                 8

# Display a message after a successful login
AccessGrantMsg                  "Welcome to McDade-Woodcock's test FTP Server"
# This message is displayed for each access good or not
ServerIdent                     on       "MWI ftp server"

# Set /home/FTP-shared directory as home directory
DefaultRoot                     /home/FTP-shared

# Lock all the users in home directory,
#    ***** really important *****
DefaultRoot                     ~ 

MaxLoginAttempts                3

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
AllowUser user2
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
        Order Allow,Deny
        AllowUser userftp
        AllowUser user2 
        Deny ALL
    </Limit>
    <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
    DenyAll
    </Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
        Order Allow,Deny
        AllowUser userftp
        Deny ALL
    </Limit>
    <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
    DenyAll
    </Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
        <Limit ALL>
        Order Allow,Deny
        Allowuser userftp
        AllowUser user2 
        Deny ALL
    </Limit>
    <Limit READ RMD DELE>
         DenyAll
        </Limit>
        <Limit STOR CWD MKD>
          AllowAll
        </Limit>
</Directory>

---

### Post by frodon on 2010-05-28
Ok, i think you missed a point about user alias and LIMIT LOGIN section.

In LIMIT LOGIN sections what you allow or deny is real system user(s) and each of these allowed system users should have an alias to login (when you login you use the alias name).
In your case your system users have both the same alias name "upload" so this can't work.

---

### Post by frodon on 2010-05-28
Ok, i think you missed a point about user alias and LIMIT LOGIN section.

In LIMIT LOGIN sections what you allow or deny is real system user(s) and each of these allowed system users should have an alias to login (when you login you use the alias name).
In your case your system users have both the same alias name "upload" so this can't work.

---

### Post by thrawn717 on 2010-06-01
Hey Frodon, 

Your last post makes total sense! Thanks for helping me understand that part of the conf file. I am pretty new to Ubuntu so this is all very interesting, new and frustrating! Thanks for your help!!! I am very grateful for it!

But.... It's still is not working. I changed the Alias to the following:

UserAlias download userftp 
UserAlias upload user2 

still no go.... :( 
I even added my user user profile to the conf file as a test, with a Alias as well and still no go...

Could there be something wrong with the user profiles?

Thanks


#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

AllowOverwrite                  on
AuthAliasOnly                   on

# Choose here the user alias you want !!!!
UserAlias download userftp
UserAlias upload user2

ServerName                      "McDade-Woodcock Test FTP Server"
ServerType                      standalone
DeferWelcome                    on

#MasqueradeAddress               192.168.1.65
PassivePorts                    60000 60100 #this is a range, not just two ports

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    off

TimeoutNoTransfer               600
TimeoutStalled                  100
TimeoutIdle                     2200

DisplayLogin            welcome.msg
DisplayChdir                 .message true
ListOptions                     "-l"

RequireValidShell                off

TimeoutLogin 20

RootLogin                       off

# It's better for debugging purposes to create log files
ExtendedLog                     /var/log/ftp.log
TransferLog                     /var/log/xferlog
SystemLog                       /var/log/syslog.log

#DenyFilter                     \*.*/

# I don't choose to use /etc/ftpusers file (use it to ban users by
#just writing their username in it)
UseFtpUsers                     off

# Allow to restart a download
AllowStoreRestart               on

# Port 21 is the standard FTP port, so don't use it for security
#reasons (choose here the port you want)
Port                            21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                            nobody
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022     022

PersistentPasswd                off

MaxClients                      8
MaxClientsPerHost               8
MaxClientsPerUser               8
MaxHostsPerUser                 8

# Display a message after a successful login
AccessGrantMsg                  "Welcome to McDade-Woodcock's test FTP Server"
# This message is displayed for each access good or not
ServerIdent                     on       "MWI ftp server"

# Set /home/FTP-shared directory as home directory
DefaultRoot                     /home/FTP-shared

# Lock all the users in home directory,
#    ***** really important *****
DefaultRoot                     ~ 

MaxLoginAttempts                3

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
AllowUser user2
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
        Order Allow,Deny
        AllowUser userftp
        AllowUser user2
        Deny ALL
    </Limit>
    <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
    DenyAll
    </Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
        Order Allow,Deny
        AllowUser userftp
        Deny ALL
    </Limit>
    <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
    DenyAll
    </Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
        <Limit ALL>
        Order Allow,Deny
        Allowuser userftp
        AllowUser user2
        Deny ALL
    </Limit>
    <Limit READ RMD DELE>
         DenyAll
        </Limit>
        <Limit STOR CWD MKD>
          AllowAll
        </Limit>
</Directory>

---

### Post by frodon on 2010-06-01
I bet that your FTP server name is too complex, keep your server name as simple as possible and try again.

BTW, use QUOTE next time to post your config file, it's easier to read ;)

---

### Post by frodon on 2010-06-01
I bet that your FTP server name is too complex, keep your server name as simple as possible and try again.

BTW, use QUOTE next time to post your config file, it's easier to read ;)

---

### Post by thrawn717 on 2010-06-01
Still nothing. I changed ServerName to "MWI" and the ServerIdent to "MWI" as well and still nothing...

---

### Post by frodon on 2010-06-01
Ok, so if you have still the 530 error then it is either a directory rights, user password or home network issue.

Be sure to perform your test from the same computer that runs the server for debug.

---

### Post by znupii on 2010-06-04
good tutorial. works perfectly!

but, how can i add an anonymous user tu access [ftp://mydomain.com](ftp://mydomain.com) without password ? like public one.

---

### Post by ldsilva on 2010-06-06
I have tried this scrips.The server works, but when authenticating The ftpuser (guest in my case) cant get access to FTP-shared .The ftp client (fireftp) never gets access.No error is displyed, so I think something must be wrong with the ownership of the folders.In my case the folder are owned by root .

---

### Post by SpiderLover on 2010-07-21
Hi, when I attempt to activate gftpd with gadmin I get " - Fatal: TLSRSACertificateFile: '/etc/gadmin-proftpd/certs/cert.pem' does not exist on line 58 of '/etc/proftpd/proftpd.conf"
Any ideas on how to fix this? Thanks.

---

### Post by lhffan on 2010-07-21
How does i fix so one user is locked into

/srcds

another locked into those two

/srcds
/var/www

The third is locked into this

/var/www


?

---

### Post by frodon on 2010-07-22
You have to use the DefautRoot command to suit your needs, by default in my tutorial the users are locked in their home directory but you can choose what you want there.

---

### Post by aRagnis on 2010-08-05
Over FTP i can edit only those files/folders which have chmod 0700 or more. If the chmod is lower than 0700, then i get error "Operation failed".

```
My proftpd.conf file:
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6                 off
IdentLookups                off

ServerName              "***.**"
ServerType              standalone
DeferWelcome                off

MultilineRFC2228            on
DefaultServer               on
ShowSymlinks                on

TimeoutNoTransfer           600
TimeoutStalled              600
TimeoutIdle             1200

DisplayLogin                        welcome.msg
DisplayChdir                    .message true
ListOptions                     "-l"

DenyFilter              \*.*/

# Use this to jail all users in their homes 
DefaultRoot             ~

RequireValidShell  off
# AuthUserFile  /etc/proftpd/ftpd.passwd
# AuthGroupFile /etc/proftpd/ftpd.group

# Port 21 is the standard FTP port.
Port                    21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                10

# Set the user and group that the server normally runs at.
User                    proftpd
Group                   nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                   022 022

# Normally, we want files to be overwriteable.
AllowOverwrite              on

TransferLog /var/log/proftpd/xferlog
SystemLog /var/log/proftpd/proftpd.log

<IfModule mod_quotatab.c>
    QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
    Ratios off
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default. 
<IfModule mod_delay.c>
    DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
    ControlsEngine      off
    ControlsMaxClients  2
    ControlsLog     /var/log/proftpd/controls.log
    ControlsInterval    5
    ControlsSocket      /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
    AdminControlsEngine off
</IfModule>

# Include /etc/proftpd/sql.conf

# Limit login permission only to users listed here
<Limit LOGIN>
    DenyALL
    AllowUser ragnis
</Limit>

<Directory ~>
    <Limit READ WRITE STOR RMD DELE MKD>
        DenyALL
        AllowUser ragnis
    </Limit>
</Directory>
```

---

### Post by Tidwop on 2010-08-09
So I recently logged into my FTP server and it seems I can get out of the two main directories. Now I've copied and pasted the conf file directly and I can still get out of the upload and download directory. So it looks like I may have to re-write this whole thing again. I'm a bit of a noob with Ubuntu so what would I have to do to start from scratch?

---

### Post by jcnewman83 on 2010-08-17
Hi guys I am having real trouble getting folder access rights to work via the proftpd.conf file.

I have set everything up as per the user guide and only want to make one change in that i want to only allow 1 user access to the upload and download folder and everyone else access to the download folder.

My Conf is below, is anyone able to help??

```

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
                Order Allow,Deny
                AllowUser ftpuser
                AllowUser broker
                Deny ALL
        </Limit>

        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
                Order Allow,Deny
                AllowUser ftpuser
                AllowUser broker
                Deny ALL
        </Limit>

        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

<Directory /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
HideNoAccess on

        <Limit ALL>
                Order Allow,Deny
                AllowUser ftpuser
                Deny ALL
        </Limit>

        <Limit READ RMD DELE>
        DenyAll
        </Limit>

        <Limit STOR CWD MKD>
        AllowAll
        </Limit>
</Directory>

```

---

### Post by frodon on 2010-08-17
Could you post the whole config file and explain in detail what doesn't work please ?

---

### Post by jcnewman83 on 2010-08-17
yes sorry,

full config below, basically I only want user to be able to access the upload directory broker must only have access to the download directory, I have tried using the config examples to get this to work but when I log in as broker i am still able to access the upload dir and copy files etc.

```

# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias user ftpuser
UserAlias fcbroker broker

ServerName                      "FC FTP Server"
ServerType                      standalone
DeferWelcome                    on

MultilineRFC2228 on
DefaultServer                   on
ShowSymlinks                    off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayChdir                    .message
ListOptions                     "-l"

RequireValidShell               off

TimeoutLogin 20

RootLogin                       off

# It's better for debug to create log files ;-)
ExtendedLog                     /var/log/ftp.log
TransferLog                     /var/log/xferlog
SystemLog                       /var/log/syslog.log

#DenyFilter                     \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart               on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port                            21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022     022

PersistentPasswd                off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-Shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser ftpuser
AllowUser broker
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
                Order Allow,Deny
                AllowUser ftpuser
                AllowUser broker
                Deny ALL
        </Limit>

        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
                Order Allow,Deny
                AllowUser ftpuser
                AllowUser broker
                Deny ALL
        </Limit>

        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
                Order Allow,Deny
                AllowUser ftpuser
                AllowUser broker
                Deny ALL
        </Limit>

        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>

<Directory /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
HideNoAccess on

        <Limit ALL>
                Order Allow,Deny
                AllowUser ftpuser
                Deny ALL
        </Limit>

        <Limit READ RMD DELE>
        DenyAll
        </Limit>

        <Limit STOR CWD MKD>
        AllowAll
        </Limit>
</Directory>
                                                                     

```

---

### Post by frodon on 2010-08-17
Except the duplicate *<Directory /home/FTP-shared/download/*>* section and the *HideNoAccess* command i don't realy know your config looks good.

If you perform a search in this thread you will see that some users got it working with a really similar config file. And if you really can't find any help here on ubuntuforums the proftpd forum can be of great help.

Will try to think about it but from my first look your config looks good.

---

### Post by firedragoneater on 2010-08-30
How would I go about removing users, changing there usernames and there directorys?
many thanks
Jordan

---

### Post by Cyph0n on 2010-09-04
Flawless tutorial. Used this several times.

ProFTPd FTW :D

---

### Post by Joey Calamaro on 2010-09-21
I'm trying to establish an FTP server on my Ubuntu nettop to be used for some light file serving in my office. I don't need a lot of features, I just need something that's simple and easy to manage (I am a Mac user after all), so I went with Proftpd +GADMIN. 

The trouble is, I simply can't get this to work. My goal is to have a single login that accesses a directory on an external drive. The user for this account is going to be called "transfer." I went ahead and created this user via the Users and Groups preference panel. It's set to be a member of the nobody group and the home directory is my target ftp share:

/media/ftp/transfers

Using GADMIN, I set up the following configuration file:

```

ModulePath /usr/lib/proftpd
LoadModule mod_ctrls_admin.c
LoadModule mod_tls.c
LoadModule mod_radius.c
LoadModule mod_quotatab.c
LoadModule mod_quotatab_file.c
LoadModule mod_quotatab_radius.c
LoadModule mod_wrap.c
LoadModule mod_rewrite.c
LoadModule mod_load.c
LoadModule mod_ban.c
LoadModule mod_wrap2.c
LoadModule mod_wrap2_file.c
LoadModule mod_dynmasq.c
LoadModule mod_ifsession.c
ServerType standalone
DefaultServer on
Umask 022
ServerName "mylocalipaddress"
ServerIdent on "ftp.myserver.com"
ServerAdmin support@myserver.com
IdentLookups off
UseReverseDNS on
Port 21
PassivePorts 49152 65534
MasqueradeAddress mylocalipaddress
TimesGMT off
MaxInstances 30
MaxLoginAttempts 10
TimeoutLogin 300
TimeoutNoTransfer 122
TimeoutIdle 122
DisplayLogin welcome.msg
DisplayChdir .message
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 5000
TransferRate STOR 5000
TransferRate STOU 5000
TransferRate APPE 5000
SystemLog /var/log/secure
RequireValidShell off
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol SSLv23
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gadmin-proftpd/certs/cert.pem
TLSRSACertificateKeyFile /etc/gadmin-proftpd/certs/key.pem
TLSCACertificateFile /etc/gadmin-proftpd/certs/cacert.pem
TLSRenegotiate required off
</IfModule>
<IfModule mod_ratio.c>
Ratios off
SaveRatios off
RatioFile "/restricted/proftpd_ratios"
RatioTempFile "/restricted/proftpd_ratios_temp"
CwdRatioMsg "Please upload first!"
FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
LeechRatioMsg "Your ratio is unlimited."
</IfModule>
<Limit LOGIN>
  AllowUser transfer
  DenyALL
</Limit>

<Anonymous /media/ftp/transfers>
User transfer
Group nobody
AnonRequirePassword on
MaxClients 11 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit APPE  SITE  SITE_CHMOD  SITE_CHGRP >
 DenyAll
</Limit>
</Anonymous>

```

When I attempt to connect to the server using the correct credentials, it replies:

530-Unable to set anonymous privileges.
530 Login incorrect.
ftp: Login failed

This differs from a bad login which returns: 

530 Login incorrect.
ftp: Login failed

I don't intend to have any anonymous logins, though I'm not entirely sure if this is part of the problem. Either way, I've tried creating the transfer user within GADMIN first (allowing it to create the system user) and I've even tried setting it up as a virtual user with no system account. Neither approach works. I simply can't login.

Any ideas? I've been at this for some time now and I'm simply stumped.

---

### Post by ZnoteOT on 2010-10-04
Hello, I have a question.

What if I want user 1 to access both
/home/user1 (777)
AND
/var/www/user1 (777)

So I can give them both online and offline storage. So they can make their own website and stuff and still keep some files private.

Do I have to put separate users for this case? One for the /var/www/name and one for the /home/name?

---

### Post by frodon on 2010-10-04
Yep, you have to use separate users or bind one directory somewhere in the other (mount -o bind commands).

---

### Post by ZnoteOT on 2010-10-04
Tiny big problem!

I try to keep is as simple as possible. However I found out a security leak by doing so.

I wrote this:
sudo useradd USERNAME -p PASSWORD -d /var/www -s /bin/false
To create a username. And I assumed that -d /var/www would be not only default dir, but also the only allowed dir to be in. (+ sub dirs).

People who access this account, can also go outside the /var/www dir and view my other files.

Any easy way to restrict these users to their specific default dir (+ sub dirs) only? Lets say I have 4 users. All have individual dirs connected to them. Their own "space" on my server. They can do whatever they want inside the space, but are not allowed to go outside their default dir.

I hope you understand me. My knowledge in Linux is low. I use Ubuntu Server (terminal only).

---

### Post by frodon on 2010-10-04
The following command locks users in their home directory:
```
DefaultRoot ~
```
Keep only this *DefaultRoot* command in your config file.

---

### Post by ReplicateThis on 2010-10-17
After giving up the fight to make Samba and Windows 7 play nice, I am trying the old fashioned FTP approach to share files from a Linux server to a Win7 client.  After noticing very few GUI options for FTP servers, I thought this guide would be a godsend.  My hopes came crashing down, however, when I noticed this from my terminal...:

```
padraic@devon-2:~$ sudo aptitiude install proftpd gproftpd
sudo: aptitiude: command not found
padraic@devon-2:~$ sudo aptitude install proftpd gproftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Note: selecting "proftpd-basic" instead of the
      virtual package "proftpd"
Couldn't find any package whose name or description matched "gproftpd"
Couldn't find any package whose name or description matched "gproftpd"

```I know I used aptitude instead of apt-get, but aside from that detail I entered the command as listed in step 1.  I haven't read quite all 16 pages of this thread quite yet, but is there a workaround to still get the GUI aspect of this? :confused:

---

### Post by kon_nos on 2010-10-19
Hello all.

I've followed the guide, and I have a problem trying to find out if it works.

Every time I use a standard sudo /etc/init.d/proftp command it sais: *ProFTPd is started from inetd/xinetd*. (even if i use the stop command).

When I use the force-stop i get
Warning: ProFTPd is started from inetd/xinetd (trying to kill anyway).
 * Stopping ftp server proftpd  [ OK ]

but when i use the force-start I get
 * Starting ftp server proftpd                                                  athena - fatal: Socket operation on non-socket
                                                                         [fail]

As you can assume I can't even login. My servertype is inetd, and not standalone. Should i try the standalone?

My proftpd.conf is most of it the example i found:
```
# This sample configuration file illustrates configuring two
# anonymous directories, and a guest (same thing as anonymous but
# requires a valid password to login)

ServerName			"Athena"
ServerType			inetd

# Port 21 is the standard FTP port.
Port				21

# If you don't want normal users logging in at all, uncomment this
# next section
#<Limit LOGIN>
#  DenyAll
#</Limit>

# Set the user and group that the server normally runs at.
User				proftpd
Group				nogroup

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

# Set the maximum number of seconds a data connection is allowed
# to "stall" before being aborted.
TimeoutStalled			300

# We want 'welcome.msg' displayed at login, and '.message' displayed
# in each newly chdired directory.
DisplayLogin			welcome.msg
DisplayChdir			.message

# Our "basic" anonymous configuration, including a single
# upload directory ("uploads")
<Anonymous ~ftp>

  # Allow logins if they are disabled above.
  <Limit LOGIN>
    AllowAll
  </Limit>

  # Maximum clients with message
  MaxClients			5 "Sorry, max %m users -- try again later"

  User				ftp
  Group				ftp
  # We want clients to be able to login with "anonymous" as well as "ftp"
  UserAlias			anonymous ftp

  # Limit WRITE everywhere in the anonymous chroot
  <Limit WRITE>
    DenyAll
  </Limit>

  # An upload directory that allows storing files but not retrieving
  # or creating directories.
  <Directory uploads/*>
    <Limit READ>
      DenyAll
    </Limit>

    <Limit STOR>
      AllowAll
    </Limit>
  </Directory>
</Anonymous>

# A second anonymous ftp section.  Users can login as "private".  Here
# we hide files owned by root from being manipulated in any way.

<Anonymous /usr/local/private>
  User				bobf
  Group				users
  UserAlias			private bobf
  UserAlias			engineering bobf

  # Deny access from *.evil.net and *.otherevil.net, but allow
  # all others.
  <Limit LOGIN>
    Order			deny,allow
    Deny 			from .evil.net, .otherevil.net
    Allow			from all
  </Limit>

  # We want all uploaded files to be owned by 'engdept' group and
  # group writable.
  GroupOwner			engdept
  Umask				006

  # Hide all files owned by user 'root'
  HideUser			root

  <Limit WRITE>
    DenyAll
  </Limit>

  # Disallow clients from any access to hidden files.
  <Limit READ DIRS>
    IgnoreHidden			on
  </Limit>

  # Permit uploading and creation of new directories in
  # submissions/public

  <Directory submissions/public>
    <Limit READ>
      DenyAll
      IgnoreHidden			on
    </Limit>

    <Limit STOR MKD RMD XMKD XRMD>
      AllowAll
      IgnoreHidden			on
    </Limit>
  </Directory>
</Anonymous>

# The last anonymous example creates a "guest" account, which clients
# can authenticate to only if they know the user's password.

<Anonymous ~userftp>
  User				userftp
  Group				nobody
  AnonRequirePassword		on

  <Limit LOGIN>
    AllowAll
  </Limit>

  # Hide all files owned by user 'root'
  HideUser			root
  

  # Deny write access from all except trusted hosts.
  <Limit WRITE>
    Order			allow, deny
    Allow			from 10.0.0.
    Deny			from all
  </Limit>
</Anonymous>
```

---

### Post by Return Privacy on 2010-10-19
Hi,
I tried to follow this and install Proftpd, it doesn't work at all. Won't install or work.

---

### Post by ZnoteOT on 2010-10-23
> **frodon said:**
> The following command locks users in their home directory:
```
DefaultRoot ~
```
Keep only this *DefaultRoot* command in your config file.

Thanks, your a life saver! :D

---

### Post by ZnoteOT on 2010-10-29
I think I messed a bit up. Any command I can do to view all the users I have added to the server? like proftpd -ls or something?

Some command that gives me a list of the usernames I have added? Or view a document?

---

### Post by frodon on 2010-10-30
If you followed the tutorial the users you created are system users therefore you just need to manage your system users.

The file /etc/passwd should contain all the users you created (and a bit more).

---

### Post by frodon on 2010-10-30
If you followed the tutorial the users you created are system users therefore you just need to manage your system users.

The file /etc/passwd should contain all the users you created (and a bit more).

---

### Post by jsra on 2010-11-14
Hello,

how can one set maximum size of a directory?
Is it even possible to set such option?

I really tried to find a solution for this but i could not find it anywhere.

Thanks for any reply.

---

### Post by frodon on 2010-11-14
It seems you didn't choose the good keywords, what you are looking for is how to handle "quotas" with proftpd. Here are 2 links which should be a good start point for you :
[http://www.proftpd.org/docs/howto/Quotas.html](http://www.proftpd.org/docs/howto/Quotas.html)
[http://www.castaglia.org/proftpd/modules/mod_quotatab.html](http://www.castaglia.org/proftpd/modules/mod_quotatab.html)

I'm sure you will find many other good websites and examples over the web or in the proftpd forum.

---

### Post by frodon on 2010-11-14
It seems you didn't choose the good keywords, what you are looking for is how to handle "quotas" with proftpd. Here are 2 links which should be a good start point for you :
[http://www.proftpd.org/docs/howto/Quotas.html](http://www.proftpd.org/docs/howto/Quotas.html)
[http://www.castaglia.org/proftpd/modules/mod_quotatab.html](http://www.castaglia.org/proftpd/modules/mod_quotatab.html)

I'm sure you will find many other good websites and examples over the web or in the proftpd forum.

---

### Post by killboymota on 2010-11-24
dude, as soon as i got connected i get disconnected! :(

Looking up xxxxx
Trying xxxxx
Connected to xxxx
Disconnecting from site xxxx
Waiting 30 seconds until trying to connect again

---

### Post by CurtBruno on 2010-12-29
Hi all,
I've encountered 1 flaw.
I can connect using FTP but not FTPES.

All I get from FileZilla Client was
> Resolving address of ftp.xxxx.com
17:38:02    Status:    Connecting to xxxx:21...
17:38:02    Status:    Connection established, waiting for welcome message...
17:38:12    Response:    220 Test FTP
17:48:09    Command:   AUTH TLS
17:48:10    Response:    234 AUTH TLS successful
17:48:10    Status:    Initializing TLS...
17:48:30    Error:    GnuTLS error -9: A TLS packet with unexpected length was received.
17:48:30    Status:    Server did not properly shut down TLS connection
17:48:30    Error:    Could not connect to server
Then I've checked on my tls.log.
It's as follows
> Dec 29 17:47:58 mod_tls/2.2.2[14786]: error loading TLSRSACertificateFile '/etc/ftpcert/server.csr': 
  (1) error:0906D06C:PEM routines:PEM_read_bio:no start line
  (2) error:140AD009:SSL routines:SSL_CTX_use_certificate_file:PEM lib
Dec 29 17:48:08 mod_tls/2.2.2[14786]: TLS/TLS-C requested, starting TLS handshake
Dec 29 17:48:34 mod_tls/2.2.2[14795]: error loading TLSRSACertificateFile '/etc/ftpcert/server.csr': 
  (1) error:0906D06C:PEM routines:PEM_read_bio:no start line
  (2) error:140AD009:SSL routines:SSL_CTX_use_certificate_file:PEM liband as for my proftpd config, it's as follows:
> # To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

Include /etc/proftpd/modules.conf

# Choose here the user alias you want
UserAlias test xxx1

ServerName            "Test FTP"
ServerType             standalone
DisplayLogin            welcome.msg
DeferWelcome            on
UseIPv6                off

MultilineRFC2228        on
DefaultServer            on
ShowSymlinks            off

TimeoutNoTransfer        600
TimeoutStalled            100
TimeoutIdle            2200

DisplayChdir                    .message
ListOptions                    "-l"

RequireValidShell         off

TimeoutLogin 20

RootLogin             off

# It's better for debug to create log files
ExtendedLog             /var/log/ftp.log
TransferLog             /var/log/xferlog
SystemLog            /var/log/syslog.log

#DenyFilter            \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart        on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port                21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                022    022

PersistentPasswd        off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 5
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "xxx"

# This message is displayed for each access good or not
ServerIdent                  on        "xxx"

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

# Bar use of SITE CHMOD by default
<Limit SITE_CHMOD>
DenyAll
</Limit>

# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=deta...=LSS-2004-10-02](http://security.lss.hr/index.php?page=deta...=LSS-2004-10-02)
# It is on by default.
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
UseSendFile on

<IfModule mod_tls.c>
    TLSEngine on
    TLSLog /var/log/tls.log
    TLSProtocol SSLv23 TLSv1

    # Are clients required to use FTP over TLS when talking to this server?
    TLSRequired on

    # Server's certificate
    TLSRSACertificateFile /etc/ftpcert/server.csr
    TLSRSACertificateKeyFile /etc/ftpcert/server.key

    # CA the server trusts
    TLSCACertificateFile /etc/ftpcert/ca.crt

    # Authenticate clients that want to use FTP over TLS?
    TLSVerifyClient off

    # Allow SSL/TLS renegotiations when the client requests them, but
    # do not force the renegotations.  Some clients do not support
    # SSL/TLS renegotiations; when mod_tls forces a renegotiation, these
    # clients will close the data connection, or there will be a timeout
    # on an idle data connection.
    TLSRenegotiate none

</IfModule>

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
AllowUser xxx1
DenyALL
</Limit>

#
<Directory /home/FTP-xxx/xxx1/>
Umask 022 022
AllowOverwrite on
        <Limit ALL>
        Order Allow,Deny
        AllowUser xxx1
        Deny ALL
    </Limit>
</Directory>

#<Directory /home/FTP-xxx>
#Umask 022 022
#AllowOverwrite off
#    <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
#    DenyAll
#    </Limit>
#</Directory>any idea what's going on?

---

### Post by frodon on 2010-12-29
I woud try to re-generate the certificate in that case.

---

### Post by CurtBruno on 2010-12-29
hmm, I'm using a non self-signed cert (cert signed by CA) also, I've solved it by changing from > TLSRSACertificateFile /etc/ftpcert/server.csr to > TLSRSACertificateFile /etc/ftpcert/server.crtbut, connecting via LAN does work for me but not when I connect from WAN.
I get the following error on FileZilla while testing on WAN.
> Resolving address of ftp.xxxx.com
Status:    Connecting to xxxx:21...
Status:    Connection established, waiting for welcome message...
Response:    220 Test Server
Command:    AUTH TLS
Response:    234 AUTH TLS successful
Status:    Initializing TLS...
Error:    GnuTLS error -73: ASN1 parser: Error in TAG.
Error:    Could not connect to serverand in tls.log it's as follows:
> Dec 30 06:04:59 mod_tls/2.2.2[3860]: TLS/TLS-C requested, starting TLS handshake
Dec 30 06:05:01 mod_tls/2.2.2[3860]: unable to accept TLS connection: received EOF that violates protocol
Dec 30 06:05:01 mod_tls/2.2.2[3860]: TLS/TLS-C negotiation failed on control channelalso, another issue... sorry for the trouble! ](*,)

I can't seems to get implicit ftp over ssl/tls to work.
I get the following error on FileZilla as follows
> 06:07:53    Status: Connecting to xxx:990...
06:07:54    Status:    Connection attempt failed with "ECONNREFUSED - Connection refused by server".
tried in LAN and WAN with LAN (private address) and WAN (ftp.xxx.com) and also tried using FileZilla in server itself (127.0.0.1), i get connection refused by server.
I've disabled the firewall and restarted the server but i still get the same error. :confused:

any idea, sir?

---

### Post by frodon on 2010-12-31
> **CurtBruno said:**
> connecting via LAN does work for me but not when I connect from WAN.When i read this i think about network issue as if it works on LAN then it means the FTP server is ok.

So if it works on LAN i would exclude any FTP server issue, it is more likely home network issue be home network issue (router, firewall, switch, ...).

---

### Post by CurtBruno on 2010-12-31
hmm, but what about the implicit ssl issue? tried turning off all firewalls on server and tested using filezilla on the machine itself (127.0.0.1) also doesn't work.
i get > 06:07:53    Status: Connecting to xxx:990...
06:07:54    Status:    Connection attempt failed with "ECONNREFUSED - Connection refused by server". 			 		

---

### Post by MakingTheServer on 2011-01-07
hya i m doing FTP server but my problem is the same i removed inetd to standalone and Rootlogin off
my problem is this i do that bla bla bla and then it says

[B]root@ubuntu:/home/xubuntuforservers# sudo /etc/init.d/proftpd restart
ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration.
root@ubuntu:/home/xubuntuforservers# [/B]

whata ???

My CFG

# # /etc/proftpd.conf -- This is a basic ProFTPD configuration file. # To really apply changes reload proftpd after modifications. #   ServerName			"FTP Server" Serverident                     on "FTP" ServerType			standalone DeferWelcome			off TimesGMT                        off   MultilineRFC2228		on #DefaultServer			on ShowSymlinks			on  TimeoutNoTransfer		600 TimeoutStalled			600 TimeoutIdle			1200  DisplayLogin                    welcome.msg DisplayFirstChdir               .message ListOptions                	"-l"  DenyFilter			\*.*/  AllowForeignAddress             on AllowRetrieveRestart            on  # Uncomment this if you are using NIS or LDAP to retrieve passwords: #PersistentPasswd		off  # Uncomment this if you would use TLS module: #TLSEngine 			on  # Uncomment this if you would use quota module: #Quotas				on  # Uncomment this if you would use ratio module: #Ratios				on  # Port 21 is the standard FTP port. Port				21 SocketBindTight                 on  PassivePorts                    11000 20000   # To prevent DoS attacks, set the maximum number of child processes # to 30.  If you need to allow more than 30 concurrent connections # at once, simply increase this value.  Note that this ONLY works # in standalone mode, in inetd mode you should use an inetd server # that allows you to limit maximum number of processes per service # (such as xinetd) MaxInstances			30  # Set the user and group that the server normally runs at. User				nobody Group				nogroup  # Umask 022 is a good standard umask to prevent new files and dirs # (second parm) from being group and world writable. Umask				022  022 # Normally, we want files to be overwriteable. AllowOverwrite			on  AllowForeignAddress             on AllowRetrieveRestart            on AllowStoreRestart on  # Speed up the server, no DNS lookups, just plain ip's. Turn off when being hax0r3d. UseReverseDNS off IdentLookups off  DefaultRoot                     ~ ExtendedLog                     /var/log/proftpd.all ALL   # Delay engine reduces impact of the so-called Timing Attack described in # [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02) # It is on by default.  DelayEngine 			off  <Anonymous ~ftp>   User                          ftp   Group                         nogroup   UserAlias                     anonymous ftp   DirFakeUser                   on ftp   DirFakeGroup                  on ftp   RequireValidShell             off   MaxClients                    10   DisplayLogin                  welcome.msg   DisplayFirstChdir             .message   AccessGrantMsg                "Anonymous access granted for user %u connecting."    MaxClientsPerHost             1    <Directory>     #DenyAll     TransferRate        RETR 50     <Limit WRITE>       DenyAll     </Limit>   </Directory>



HELPP!!! xD i m n00b xD

---

### Post by Docfxit on 2011-01-13
I just setup the FTP server.  I can't connect to it.  
Could someone please help me figure out what I did wrong?

I tried to turn debugging on:
 proftpd -nd5
 - notice: unable to bind to Unix domain socket at '/var/run/proftpd/test.sock': Permission denied
 - mod_ctrls/0.9.4: binding ctrls socket to '/var/run/proftpd/proftpd.sock'
 - notice: unable to listen to local socket: Address already in use
 - parsing '/etc/proftpd/proftpd.conf' configuration
 - parsing '/etc/proftpd/modules.conf' configuration
 - mod_tls/2.1.1: using OpenSSL 0.9.8e 23 Feb 2007
 - Fatal: SystemLog: unable to redirect logging to '/var/log/syslog.log': Permission denied on line 37 of '/etc/proftpd/proftpd.conf'

```

#
# Includes required DSO modules. This is mandatory in proftpd 1.3
#
Include	/etc/proftpd/modules.conf

# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias docfxit userftp

ServerName			"UbuntuAsterisk"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port				a different # I chose

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  userftp
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /var/spool/asterisk/monitor

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /var/spool/asterisk/monitor>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/docfxit/Dnload/*>
#Download
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/docfxit/Dnload/>
#Upload
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

```

I'm trying to connect with:
port # a different # I chose
user userftp
Transfer Mode: Binary, 
No Passive Mode

I have followed the instructions at the beginning of this thread.

Thank you,

Docfxit

---

### Post by imakbari on 2011-03-05
Hey people,
I'm kinda noob in network stuff, so please bear with me.
I did as it was said in the first post (nice tutorial by the way, tnx a lot)
now i can connect to the ftp network with the administrator user-pass and access the whole file system.
but as userftp, i can't.
( i use Places > connect to server > FTP with login)

thanx in advance

---

### Post by capitalfear on 2011-03-12
good stuff thanks...workin on my ftp :]

---

### Post by dannyboy79 on 2011-03-12
i created SMF forums on my home server and needed FTP to be able to run install script. I made a symlink in /var/www/ called forums which points to /home/FTP-shared/upload/forum and I want it to be open to do whatever useftp user needs to do to it. It wouldn't let me download files from that folder but it would let me upload them. So I made some changes to the config but not sure if it's optimal settings. Here's what the folders settings are

> <Directory /home/FTP-shared/upload>
Umask 022 022
AllowOverwrite on
        <Limit ALL>
                Order Allow,Deny
                AllowUser userftp
                Deny ALL
        </Limit>

        <Limit MKD STOR DELE XMKD RNRF RNEF RNTO RMD XRMD READ>
        AllowAll
        </Limit>
</Directory>


are those ok?

---

### Post by frodon on 2011-03-13
I'm not sure symlink are fully supported, they are a high security risk for a FTP server anyway so i really don't recommend them even if you can get them to work. You can reach the same goal mounting a directory in another one (see first) post, it is fully supported and less risky.

---

### Post by dannyboy79 on 2011-03-14
> **frodon said:**
> I'm not sure symlink are fully supported, they are a high security risk for a FTP server anyway so i really don't recommend them even if you can get them to work. You can reach the same goal mounting a directory in another one (see first) post, it is fully supported and less risky.ok, will check out mounting /var/www/forums to /home/FTP-shared/upload/forum  but are my limits or what have you ok? I mean, is there an easier way to do it instead of limit, then list everything, then AllowAll?  thanks

---

### Post by frodon on 2011-03-14
The other way to do it would be not to use /home/FTP-shared/.... directories in your config file but /var/www/forums directory (think to put it as home dir for your ftp user), i think most users using the FTP server for their website do it this way.

For the LIMIT section i don't really know what to answer, there might be an easier way i guess, in my example i listed all i wanted to deny and all i wanted to allow to be sure of what is restricted and what is not.

---

### Post by danba185 on 2011-03-17
Hi, thank you all the valuable information you have shared in this thread. Is there someone who can explain how the passive ports works and why isn't it enough with one port? Another question, why do we have to use MasqueredeAddress when the ftp server is behind a router? I have followed some advises from this thread so this isn't any problem for me (at the moment :)), I'm just curious how all this stuff works and  the information at proftpd.org was quite small?

---

### Post by profiseller-pohland on 2011-07-14
Helloo can everybody German???

Ich habe ein problem  ich bekomme keinen 2ten user angelegt!!
kann mir einer erklären wie ich das genau mache???

translate with google translate:

I have a problem I can not get a 2nd user created!
 can not explain exactly how I'm a?

MFG

---

### Post by tetsu7 on 2011-08-17
i cant seem to get a second user created. i set it up exactly like the first one but it just doesnt work. i logged into my ubuntu with the user and it worked just fine, however i get a 530 login error trying to login to the ftp server with this user. userftp works fine. website does not. i mounted /var/www to the upload directory. everything for website looks the same as userftp..anyone have any ideas as to what im doing wrong? below is my .conf


Include /etc/proftpd/modules.conf
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias webmaster website
UserAlias lordofthenexus userftp


#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
AllowUser website
DenyALL
</Limit>

ServerName            "TheNexus"
ServerType             standalone
DeferWelcome            on

MultilineRFC2228 on
DefaultServer            on
ShowSymlinks            off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayChdir                    .message
ListOptions                    "-l"

RequireValidShell         off

TimeoutLogin 20

RootLogin             off

# It's better for debug to create log files ;-)
ExtendedLog             /var/log/ftp.log
TransferLog             /var/log/xferlog
SystemLog            /var/log/syslog.log

#DenyFilter            \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart        on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port                21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                022    022

PersistentPasswd        off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "Welcome to The Nexus Wretch!!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
    <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
    Order Allow,Deny
        AllowUser website
                AllowUser userftp
        DenyAll
    </Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
        <Limit ALL>
        Order Allow,Deny
        AllowUser website
                AllowUser userftp
        Deny ALL
    </Limit>

    <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
    DenyAll
    </Limit>
</Directory>

<Directory /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
    
        <Limit ALL>
        Order Allow,Deny
        AllowUser website
        Deny ALL
    </Limit>

        <Limit STOR CWD MKD>
          AllowAll
        </Limit>
</Directory>

---

### Post by frodon on 2011-08-18
You miss "website" user in general *<Limit LOGIN>* section which is mandatory if i remember well.

---

### Post by tetsu7 on 2011-08-22
yer the man! i dont know how i missed it but it works now thanks! and after many long days trying to get an ftp server up it wasnt until i found this thread that ive had any success. thank you so much for your instructions and support!

---

### Post by renovatiohq on 2011-08-24
I HAVE A QUICK QUESTION.. I'M KINDA NEW... SO HOW DO I ACCESS THE FTP SERVER FROM ANOTHER COMPUTER... OR LINK IT TO A FTPPROGRAM LIKE 
FILE ZILLA...


PLEASE email me if you can thank you :)


i really want to figure this out thank


[email]renovatio988@gmail.com[/email]

---

### Post by loudog23 on 2011-08-24
> **renovatiohq said:**
> I HAVE A QUICK QUESTION.. I'M KINDA NEW... SO HOW DO I ACCESS THE FTP SERVER FROM ANOTHER COMPUTER... OR LINK IT TO A FTPPROGRAM LIKE 
FILE ZILLA...


PLEASE email me if you can thank you :)


i really want to figure this out thank


[email]renovatio988@gmail.com[/email]


edit: did you read the post? and plz go ez on the caps... thx ;)

punch the address as
[ftp://www.mywebsite.com/](ftp://www.mywebsite.com/)

You can specify the port number
[ftp://www.mywebsite.com:21/](ftp://www.mywebsite.com:21/)

or a folder
[ftp://www.mywebsite.com:21/myfolder](ftp://www.mywebsite.com:21/myfolder)

or user name
[ftp://username@www.mywebsite.com:21/](ftp://username@www.mywebsite.com:21/)

i don't remember the password
you don't want to punch your password in the address bar anyway

edit: did you even read the thread? and plz go ez with the CAPS, thx ;)

---

### Post by #dude on 2011-09-22
I used this guide I think it is nice, but the only problem is the user is not locked into the directory!

This is not too bad of a problem because I do not broadcast that IP, but I still do not want an open system. I followed the guide to the "T" except for the directory is /home/XXX/Videos

Can you think of any reasons why it is letting the user go out of Videos?

---

### Post by frodon on 2011-09-22
Config file and user config detail please (i mean the user you created to use the FTP server) ?

Without this we can't help you.

---

### Post by Steve(spt) on 2011-09-28
Hello frodon,

Thankyou for your help in this thread.

I have Proftp running fine with Ubuntu 11.04.
Using dyndns.org also working fine.

What I would like to create is a user who can delete files.

I guess I need to use the <Limit > .. </Limit> rules. Could you give an example based on the code below please? ( I could not find what I needed to know in the thread search) 

many thanks in advance.


#userftp1 to be allowed to delete files

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp1
AllowUser userftp2
DenyALL
</Limit>

<Directory /home/FTP-shared>
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

---

### Post by frodon on 2011-09-29
I'm scared you will have to go with some reading of the Proftp documentation. The tutorial shows a way to limit access to directories to some users but all the allowed users in a directory have the same rights.

I'm pretty sure what you want to do is possible but the hard thing is to find the right way to do it and i'm not sure the way described in my tutorial is the way to go.

Maybe you should post your question in the proftp forum too, there are some good experts in this place.

---

### Post by vikikamath on 2011-10-19
> **frodon said:**
> Replace : ```
ServerType                      inetd
```by : ```
ServerType             standalone
```and it should work.

By the way the "RootLogin                       on" option is not really secure, if you don't know why you use it i advice you to put it off.

thanks this worked for me!
~Vikram

---

### Post by sil3nthunt3r on 2011-11-16
Hi all,

I got a problem when configure my ftp setting.
I has bind the user to their private folder, for example testuser bind to /usr/local/folder/testuser

I tried the setting on active mode, ok no problem. testuser can only see their folder only. But when I try in passive mode, the user can navigate to other folder. How to force the user to can only see their folder, no matter in passive or active mode.

Below is my config setting.

```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				on
# If set on you can experience a longer connection delay in many cases.
IdentLookups			off

ServerName			"Debian"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayChdir               	.message true
ListOptions                	"-l"

DenyFilter			\*.*/

# Use this to jail all users in their homes 
# DefaultRoot			~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell		off

# Port 21 is the standard FTP port.
Port			        40	

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress		1.2.3.4

# This is useful for masquerading address with dynamic IPs:
# refresh any configured MasqueradeAddress directives every 8 hours
<IfModule mod_dynmasq.c>
# DynMasqRefresh 28800
</IfModule>

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				proftpd
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022

MaxClients 9
MaxClientsPerHost 9
MaxClientsPerUser 9
MaxHostsPerUser 9

AllowForeignAddress off

# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd		off

# This is required to use both PAM-based authentication and local passwords
# AuthOrder			mod_auth_pam.c* mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile			off

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        off
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine off
</IfModule>

#
# Alternative authentication frameworks
#
#Include /etc/proftpd/ldap.conf
#Include /etc/proftpd/sql.conf

#
# This is used for FTPS connections
#
#Include /etc/proftpd/tls.conf

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

#VALID LOGINS
<Limit LOGIN>
AllowUser tfluxadmin
AllowUser testuser
DenyALL
</Limit>



<Directory /usr/local/folder/>
Umask 022 022
AllowOverwrite off
	
        <Limit ALL>
		Order Allow,Deny
		AllowUser tfluxadmin
		Deny ALL
        </Limit>

</Directory>

<Directory /usr/local/folder/testuser>
Umask 022 022
AllowOverwrite off
	
       <Limit ALL>
		Order Allow,Deny
		AllowUser tfluxadmin
        AllowUser testuser
		Deny ALL
      </Limit>

      <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
      </Limit>

</Directory>

<Directory /usr/>
Umask 077 077
AllowOverwrite off
	
        <Limit ALL>
		Order Allow,Deny
		Deny ALL
        </Limit>

</Directory>

```

---

### Post by frodon on 2011-11-17
Add somewhere before the <Limit LOGIN> section the following command :
```
DefaultRoot	/usr/local/folder/testuser	
```The *DefaultRoot* command is the command allowing to define where to lock the user ("~" indicates the user's home directory but it is even better to give a hard path if it suit your needs).

---

### Post by sil3nthunt3r on 2011-11-17
> **frodon said:**
> Add somewhere before the <Limit LOGIN> section the following command :
```
DefaultRoot	/usr/local/folder/testuser	
```The *DefaultRoot* command is the command allowing to define where to lock the user ("~" indicates the user's home directory but it is even better to give a hard path if it suit your needs).

Thanks. It working now :D

---

### Post by Siwon on 2011-11-17
How would I go about creating multiple FTP accounts to go along with apache?

I'd like something like this:

**FTP Login Directory:** /home/bob/
**HTTP Root Directory:**/home/bob/www

**FTP Login Directory:** /home/joe/
 **HTTP Root Directory:**/home/joe/www

**FTP Login Directory:** /home/jack/
 **HTTP Root Directory:**/home/jack/www

and I'd like them to be able to access something like:
http://<ip>/bob/
http://<ip>/joe/
http://<ip>/jack/

and maybe subdomains for them

---

### Post by sil3nthunt3r on 2011-11-22
I have another problem.
When using Flashget, my FTP connection will give error 530: Maximum user already login (9) after some time. I have add the maximum connection to 9, but still give me 530 error. Increase the maximum connection also give the same error after some time.

But when I try using IDM, no such problem.
Anything wrong in my config?

```

#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				on
# If set on you can experience a longer connection delay in many cases.
IdentLookups			off

ServerName			"Debian"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayChdir               	.message true
ListOptions                	"-l"

DenyFilter			\*.*/

# Use this to jail all users in their homes 
DefaultRoot			/usr/local/

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell		off

# Port 21 is the standard FTP port.
Port			        40	

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress		1.2.3.4

# This is useful for masquerading address with dynamic IPs:
# refresh any configured MasqueradeAddress directives every 8 hours
<IfModule mod_dynmasq.c>
# DynMasqRefresh 28800
</IfModule>

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				proftpd
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022

MaxClients 9
MaxClientsPerHost 9
MaxClientsPerUser 9
MaxHostsPerUser 9

AllowForeignAddress off

# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd		off

# This is required to use both PAM-based authentication and local passwords
# AuthOrder			mod_auth_pam.c* mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile			off

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?pag...LSS-2004-10-02
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        off
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine off
</IfModule>

#
# Alternative authentication frameworks
#
#Include /etc/proftpd/ldap.conf
#Include /etc/proftpd/sql.conf

#
# This is used for FTPS connections
#
#Include /etc/proftpd/tls.conf

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

#VALID LOGINS
<Limit LOGIN>
AllowUser tfluxadmin
AllowUser testuser
DenyALL
</Limit>



<Directory /usr/local/folder/>
Umask 022 022
AllowOverwrite off
	
        <Limit ALL>
		Order Allow,Deny
		AllowUser tfluxadmin
		Deny ALL
        </Limit>

</Directory>

<Directory /usr/local/folder/testuser>
Umask 022 022
AllowOverwrite off
	
       <Limit ALL>
		Order Allow,Deny
		AllowUser tfluxadmin
        AllowUser testuser
		Deny ALL
      </Limit>

      <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
      </Limit>

</Directory>

<Directory /usr/>
Umask 077 077
AllowOverwrite off
	
        <Limit ALL>
		Order Allow,Deny
		Deny ALL
        </Limit>

</Directory>
```

---

### Post by tetsu7 on 2011-12-16
had a 530 message.
i would delete this post if i knew how. i figured it out i had an issue with my alias and user accounts

---

### Post by myusernameisnotvalid on 2012-01-05
Hello!

I'm running ubuntu 11.10. I did what was in the quide and ftp works without any problems, but since I want to use this outside my LAN I want it to be secure. When I add TLS/SSL protection and modify conf file, I'm still able to login to ftp server with normal unsecure connection. But when I try to use sftp or ftps then it just stucks to verifying TLS.

And Also I get following warning when I restart proftpd server:

 - mod_tls/2.4.2: compiled using OpenSSL version 'OpenSSL 1.0.0d 8 Feb 2011' headers, but linked to OpenSSL version 'OpenSSL 1.0.0e 6 Sep 2011' library
 - mod_sftp/0.9.7: compiled using OpenSSL version 'OpenSSL 1.0.0d 8 Feb 2011' headers, but linked to OpenSSL version 'OpenSSL 1.0.0e 6 Sep 2011' library
 - mod_tls_memcache/0.1: notice: unable to register 'memcache' SSL session cache: Memcache support not enabled




Here's what's in my proftpd.conf file:
------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------

<IfModule mod_tls.c>
    TLSEngine on
    TLSLog /var/log/proftpd/tls.log
    TLSProtocol TLSv1

    # Are clients required to use FTP over TLS when talking to this server?
    TLSRequired ON

    # Server's certificate
    TLSRSACertificateFile /etc/ftpcert/server.crt
    TLSRSACertificateKeyFile /etc/ftpcert/server.key

    # CA the server trusts
    TLSCACertificateFile /etc/ftpcert/ca.crt

    # Authenticate clients that want to use FTP over TLS?
    TLSVerifyClient off
</IfModule>

Include /etc/proftpd/modules.conf


# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias micro userftp

ServerName            "Ubuntuserver"
ServerType             standalone
DeferWelcome            on

MultilineRFC2228 on
DefaultServer            on
ShowSymlinks            off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayChdir                    .message
ListOptions                    "-l"

RequireValidShell         off

TimeoutLogin 20

RootLogin             off

# It's better for debug to create log files ;-)
ExtendedLog             /var/log/ftp.log
TransferLog             /var/log/xferlog
SystemLog            /var/log/syslog.log

#DenyFilter            \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart        on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port                1980

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 5

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                022    022

PersistentPasswd        off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "ftp server open"

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
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
------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------

please help me

---

### Post by kembar4 on 2012-01-10
Thank you very much for this nice writeup!

I finally found a way to mount an external folder via ftp.

Was having a tough time doing it with vsftpd.

This one seems alot more better :)

I have a question though.

When i run ftptop and then press 't' 

the rate of download in KB/s is shown as -NeN and the Progress stays at 0% although the download rate is about 165KB/s and progress is at 4%. 

Why is this happening and what can i do to get the correct readings?

---

### Post by pauliolio on 2012-03-05
Hi,

I'm hoping you'll be willing to cast an expert eye over this little conf file.

I've inherited the admin of a webserver and am trying like mad to learn a bit more linux & work out what it's doing.

At the moment I'm just trying to back up one of the domains using Wordpress. For this I need FTP access.

I can log into the server using ssh, I know for certain the password of the adm account as I've just set it.

The problem is that I can't log in at all using FTP. I always get a 530 error.

I have cut down the proftpd.conf file an awful lot getting rid of the extras, and am left with this:



# Server Config — config used for anything outside a <VirtualHost> or <Global>  
# See: [http://www.proftpd.org/docs/howto/Vhost.html](http://www.proftpd.org/docs/howto/Vhost.html) 


ServerName                        “ProFTPD server” 
Serverldent                on     “FTP Server ready.” 
ServerAdmin                       root@localhost 
DefaultServer              on 
RootLogin                  on 

# Don’t do reverse DM5 lockups (hangs on DNS problems) 
UseReverseDNS              off 

# Set the user and group that the server runs as 
User nobody 
Group nobody 

Maxlnstances               20 

# Disable sendfile by default since it breaks displaying the download speeds in 
# ftptop and ftpwho 
UseSendfile               off 

# Define the log formats 
LogFormat       default    “%h 11 %u %t \“%r\” s b” 
LogFormat       auth       “%v (%P3 %h %t \“%r\” %s” 

UseFtpUsers                off 
AllcwStoreRestart          on 
DefaultRoot                — 


#VALID LOGINS 
<Limit LOGIN> 
AllowUser                  adm 
AllowUser                  root 
DenyALL 
</Limit> 

AccessGrantMsg             “Login ok, Welcome to the server.” 
MaxClients 10              “Sorry, max %m users —— try again later” 
DisplayLogin               /welcome.rnsg 
DisplayChdir               .message 



It looks to me to be nicely simple, I know root's listed there, I'm just trying to get it to work .


Given that I'm in the server by another route with the same accounts & credentials, could anyone give me an idea as to why the 530 please?


Many thanks,
Pauliolio

---

### Post by tanoloco on 2012-04-15
Hello,

I cannot make userowner working.
I want that any user create files and dirs owned by nobody:nogroup rather than the logged user.
Here is my proftpd.conf file
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
#Umask				022
Umask				002

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

# Normally, we want files to be overwriteable.
<Directory /opt/lampp/htdocs/*>
  AllowOverwrite		on
</Directory>

# only for the web servers content
#DefaultRoot /opt/lampp/htdocs
DefaultRoot ~/ftp-root

# nobody gets the password "lampp"
UserPassword nobody wRPBu8u4YP0CY

# nobody is no normal user so we have to allow users with no real shell
RequireValidShell off

# nobody may be in /etc/ftpusers so we also have to ignore this file
UseFtpUsers off
```

I tried with no luck
```
<Directory /opt/lampp/htdocs/*>
  AllowOverwrite		on
  UserOwner	nobody
  GroupOwner	nogroup
</Directory>
```

Please help me :(

---

### Post by Wilson18 on 2012-09-22
Hi, Im not sure if this would help you or not but I have written a guide about how you can do this with pureftp. You can set up different accounts which you can manage through  mysql. As i said, im not sure if this is you wanted but I hope it helps

[http://wilson18.com/how-to/linux-networking/how-to-add-ftp-accounts-for-your-hosted-sites/](http://wilson18.com/how-to/linux-networking/how-to-add-ftp-accounts-for-your-hosted-sites/)

---

### Post by Alice2009 on 2012-11-05
hi everybody,

my problem is that i can't connect with the local linux users
only the anonymous ftp work!

please help

this is my proftpd.conf :
```

ServerName                      "serverftp01"
ServerType                      standalone
DefaultServer                   on

RequireValidShell               off

# Port 21 is the standard FTP port.
Port                            21

# Don't use IPv6 support by default.
UseIPv6                         off

# Umask 022 is a good standard umask to prevent new dirs and files
# from being group and world writable.
Umask                           022

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd).
MaxInstances                    30

# Set the user and group under which the server will run.
User                            proftpd
Group                           proftpd

# To cause every FTP user to be "jailed" (chrooted) into their home
# directory, uncomment this line.
DefaultRoot ~

# Normally, we want files to be overwriteable.
<Directory />
        AllowOverwrite          on
</Directory>

# Bar use of SITE CHMOD by default
#<Limit SITE_CHMOD>
#  DenyAll
#</Limit>

# A basic anonymous configuration, no upload directories.  If you do not
# want anonymous users, simply delete this entire <Anonymous> section.
<Anonymous ~ftp>
  User                          ftp
  Group                         ftp

  # We want clients to be able to login with "anonymous" as well as "ftp"
  UserAlias                     anonymous ftp

  # Limit the maximum number of anonymous logins
  MaxClients                    10

  # We want 'welcome.msg' displayed at login, and '.message' displayed
  # in each newly chdired directory.
  DisplayLogin                  welcome.msg


```

---

### Post by fifofil on 2012-11-14
thanks for awesome tutorial!

---

### Post by azvampyre on 2013-01-04
Don't follow the last two lines to permanently mount if you're on a VPS or it'll lock your root/prv into the hosts root and they will have to manually unmount it.


> **frodon said:**
> [COLOR="Red"][SIZE="2"]There's some support for this guide in the hoary section[/SIZE]
[SIZE="1"]Some questions are already answered in the [OLD THREAD]("http://www.ubuntuforums.org/showthread.php?t=51611") ,if you need support you should read it before posting here.[/SIZE][/COLOR]

I created this How to for people who want to share files with friends using FTP protocol, like FTPservU under windows. The way i give you is not the only one, I hope my How to is enough clear.
This FTP server will allow only users with the good password (persons to whom you gave the password and username). So you will be sure that only known persons will access your FTP server.

[SIZE=3]**A- The GUI way (_for beginners only_)**[/SIZE]

For those who are new to linux and don't want to use a FTP server without GUI, or just for those who don't use often their FTP server and wish to set it quickly without a high level of security, there is a GTK GUI for proftpd.
Be careful, it's less secure than configuring yourself your server.

**[SIZE=3]1- [/SIZE]** Install proftpd and gproftpd with synaptic or with this command : ```
sudo apt-get install proftpd gproftpd
```[SIZE=3]**2-**[/SIZE]Play with the GUI and set up quickly your server.
Beware no support is offered here for this tool but it shouldn't be too hard to use.


[SIZE="3"]**B- The secure way**[/SIZE]
[B]

[SIZE=3]1- [/SIZE][/B] Install proftpd with synaptic or with this command : ```
sudo apt-get install proftpd
```
**[SIZE=3]2-[/SIZE]** Add this line in /etc/shells file (sudo gedit /etc/shells to open the file) :```
/bin/false
``` Create a /home/FTP-shared directory : ```
cd /home
sudo mkdir FTP-shared
``` Create a user named **userftp** which will be used only for ftp access. This user don't need a valid shell (more secure) therefore select /bin/false shell for **userftp** and /home/FTP-shared as home directory (property button in user and group window).
To make this section clearer, i give you the equivalent command line to create the user,  but it would be better to use the GUI (System > Administration > User & Group) to create the user since users here often got problems with the user creation and the password (530 error) with the command line, so i really advice to use the GUI : ```
sudo useradd userftp -p your_password -d /home/FTP-shared -s /bin/false
sudo passwd userftp
``` In FTP-shared directory create a **download** and an **upload** directory : ```
cd /home/FTP-shared/
sudo mkdir download
sudo mkdir upload
```Now we have to set the good permissions for these directories : ```
cd /home
sudo chmod 755 FTP-shared
cd FTP-shared
sudo chmod 755 download
sudo chmod 777 upload
```
**[SIZE=3]3-[/SIZE]** OK, now go to the proftpd configuration file :  ```
sudo gedit /etc/proftpd.conf
```or for edgy eft (ubuntu 6.10) : ```
sudo gedit /etc/proftpd/proftpd.conf
```
and edit your proftpd.conf file like that if it fit to your need :
```
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias sauron userftp

ServerName			"ChezFrodon"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayChdir                    .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port				1980

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
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
```
Ok you have done proftpd configuration. Your server is on port 1980 (in this exemple) and the access parameters are 
user : sauron
password : the one you've set for **userftp**

**[SIZE=3]4-[/SIZE]** To start/stop/restart your server : ```
sudo /etc/init.d/proftpd start
sudo /etc/init.d/proftpd stop
sudo /etc/init.d/proftpd restart
```To perform a syntax check of your proftpd.conf file : ```
sudo proftpd -td5
```To know who is connected on your server in realtime use "ftptop" command (use "t" caracter to swich to rate display), you can also use the "ftpwho" command.
other informations [here](http://doc.gwos.org/index.php/DapperGuide#How_to_install_FTP_Server_for_File_Transfer_service) 


[SIZE="3"]**C- Advanced tricks**[/SIZE]

**[SIZE=2]1- Enable TLS/SSL encryption (FTPS)[/SIZE]** 
[COLOR="DarkOrange"]** Inportant note : proftpd versions before 1.3.2-rc2 may not work with latest filezilla versions using TLS encryption. [URL="http://ubuntuforums.org/showpost.php?p=8239887&postcount=1081"]See raymond.szebin's post for details.
[/URL][/COLOR]
The FTP file sharing protocol is an old protocol which was created when internet was still a secure place, therefore the default FTP protocol is not that secure.
For example the password and username for login are transmitted in plain text which obviously isn't secure.
That why, to fit the needs of our generation, encryption solutions were developed and one of them is TLS/SSH encryption.
This will encrypt the username and password and all the data you send, obviously to use it the FTP client must support SFTP protocol.

here are the steps to enable TLS/SSH encryption ([FTPS]("http://en.wikipedia.org/wiki/FTPS")):

Paste these commands in a terminal :```
sudo apt-get install build-essential
sudo apt-get install libssl-dev
cd /etc
sudo mkdir ftpcert
cd ftpcert/
sudo openssl genrsa -des3 -out server.key 1024
sudo openssl req -new -key server.key -out server.csr
sudo openssl genrsa -des3 -out ca.key 1024
sudo openssl req -new -x509 -days 365 -key ca.key -out ca.crt 
** download the sign.sh file (at the bottom of the post) and put it in ftpcert directory **
sudo chmod +x sign.sh
sudo ./sign.sh server.csr 
```

Then add this section to yout proftpd.conf file : ```
<IfModule mod_tls.c>
    TLSEngine on
    TLSLog /var/ftpd/tls.log
    TLSProtocol TLSv1

    # Are clients required to use FTP over TLS when talking to this server?
    TLSRequired off

    # Server's certificate
    TLSRSACertificateFile /etc/ftpcert/server.crt
    TLSRSACertificateKeyFile /etc/ftpcert/server.key

    # CA the server trusts
    TLSCACertificateFile /etc/ftpcert/ca.crt

    # Authenticate clients that want to use FTP over TLS?
    TLSVerifyClient off
</IfModule>

```

If you use edgy or proftpd 1.3 in general add this line at the beginning of your proftpd.conf file, it will load all the extra modules like mod_tls.c :
```
Include /etc/proftpd/modules.conf
```

Note - Use TLSRequired ON to force the use of TLS. OFF means that the use of TLS is optional.

Optional step:
You will notice that you will be asked for the password you set for the server.key file each time you start/stop/restart the server, it is because the RSA private key is encrypted in the server.key file.
The solution is to remove the encryption of the RSA private key but it makes the key readable in the server.key file which is obviously less secure, anyway if you do that **make sure that the server.key is readable only by root**.
Once you know that it's less secure here are the command lines to remove the encryption of the RSA private key : ```
cd /etc/ftpcert
cp server.key server.key.org
openssl rsa -in server.key.org -out server.key

```
Here are some links to read in case of problems or just to get more informations :
[http://www.modssl.org/docs/2.7/ssl_faq.html#cert-ownca](http://www.modssl.org/docs/2.7/ssl_faq.html#cert-ownca)
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html)

To use your TLS encrypted FTP server you will need a FTP client which support it like the latest versions of filezilla (the one present in the feisty repository has the TLS support).
In filezilla the option to use is called FTPES.

Thanks to **nix4me** for the help he provided and for the instructions.

**[SIZE=2]2- Restrict access for some users[/SIZE]** 
Some of you wish, for different reasons, to create more than one user and give a different access depending on the user.
For example if i create 2 users, one called user1 and the second called user2 and then want to deny access to the download directory for user2, You can do it as following :

First create the 2 users like userftp in the guide and give them alias names if you use aliases. Then allow your 2 users in the general LIMIT LOGIN section :```
#VALID LOGINS
<Limit LOGIN>
AllowUser user1
AllowUser user2
DenyALL
</Limit>
```Once done here is how to modify the directory sections to chose who is able to use which directory :```
<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off

        [B]<Limit ALL>
		Order Allow,Deny
		AllowUser user1
		Deny ALL
	</Limit>[/B]

	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on

       [B]<Limit ALL>
		Order Allow,Deny
		AllowUser user1
                AllowUser user2
		Deny ALL
	</Limit>[/B]

	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
```Note - user2 will see the download directory but will not be able to enter the directory.

That's all


[SIZE=6]**Misc**[/SIZE]
[SIZE=3]**_Best Common Practices - Everyone should read this_**[/SIZE]
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-BCP.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-BCP.html)

[SIZE=3]**_ProftpTools 1.0.1_**[/SIZE]
ProftpTools is a script I wrote thanks to swoop's feedback. This script allow you to start/stop proftpd, mount/unmount auto/manually directories, show your IP, ... and all of that with a **GUI** in order to use proftpd in a really easy way !
To install ProftpTools, download ProftpTools-v1.0.2.tar.gz (at the bottom of the page) and untar it where you want and then move the ProftpTools file in /usr/bin : ```
tar -xzvf ProftpTools-v1.0.2.tar.gz
cd ProftpTools-v1.0.2/
sudo mv ProftpTools /usr/bin/
```Then add these lines in your **.bashrc** (it's in your home directory : gedit /home/username/.bashrc) file in order to specify what is the ProftpTools directory path, YOU MUST REMOVE THE "/" CHARACTER at the end of the path. I give you an exemple if your ProftpTools directory is in your home directory : ```
ProftpTools_dir=/home/username/ProftpTools-v1.0.2
export ProftpTools_dir
```Now all you have to do is to type **ProftpTools** in a terminal and  .... enjoy  :smile: 
You need **zenity** installed to use this script.

Don't hesitate to post in this thread or send me PM to report bugs, ask new features, correct my english, suggest improvement  ;-)  and thank you to give me feedback about this tool.

[SIZE=3]_**useful trick**_[/SIZE] :
This trick is integrated in ProftpTools.
If you don't want (like me  ;-) ) to use space in your /home directory, and use space on another hard drive, or if you just want to share a directory from another partition ...   you can mount the directory you want in your **download** or **upload** directory without changing anything in proftpd.conf file, use these commands : ```
sudo mount -o bind the_directory_you_want_to_share /home/FTP-shared/download
or
sudo mount -o bind the_directory_you_want_to_use_for_upload /home/FTP-shared/upload
```This command **will not** overwrite the directory, the idea is just to mount a directory in another one without overwritng anything, so when someone will log in your server he will see and use the mounted directory if you have mounted one. To unmout a directory (download directory for exemple): ```
sudo umount /home/FTP-shared/download
```**Permanent mount :** 
If you don't want to re-mount your directories after a reboot you can add a line in fstab file like that (sudo gedit /etc/fstab to open the file) : ```
the_directory_to_mount /home/FTP-shared/download vfat bind 0 0
```thanks **reet**  ;-) 

If you want to create other directories in **FTP-shared**, think to add it in proftpd.conf file.
Don't hesitate to test yourself your server using gFTP for exemple, it's really helpful to debug your server.

[SIZE=3]_**Other stuff/Troubleshooting/FAQ**_[/SIZE]
**If you have a router** you should read [that](http://www.proftpd.org/localsite/Userguide/linked/x862.html), it describe the 2 commands to add in proftpd.conf and why. 
If you have a dynamic DNS have a look [here](http://doc.gwos.org/index.php/DapperGuide#How_to_assign_Hostname_to_local_machine_with_dynamic_IP_using_free_DynDNS_service), you can also use [ddclient](http://linux.cudeso.be/linuxdoc/ddclient.php)(maybe easier for newbies).  
If you have ***Unbindable port 21*** issue please refer [to this post]("http://ubuntuforums.org/showthread.php?t=79588&page=114") from **mustacheride**.
Most of informations you're looking for are [here](http://www.proftpd.org/) 
To get more debug informations : [http://www.proftpd.org/localsite/Userguide/linked/x1058.html](http://www.proftpd.org/localsite/Userguide/linked/x1058.html)
You can specify a specific passive port range using [PassivePorts](http://www.proftpd.org/localsite/Userguide/linked/config_ref_PassivePorts.html)  command, it's very useful when you use a [firewall](http://www.proftpd.org/localsite/Userguide/linked/x294.html)  in order to know which ports to allow.

[COLOR="Sienna"]For those who have a firewall/router i advice to read [this excelent post]("http://www.ubuntuforums.org/showpost.php?p=680702&postcount=81") from[/COLOR] **mssm**

Thanks for feedback, and sorry if my english is sometimes really bad :roll: 

Don't hesitate to post questions about proftpd in this thread.

---

### Post by Madcamper on 2013-01-05
thank you for this great setup tutorial, worked like a charm! I have only run into one problem. I have a total of 4 USB Hard drives hooked into my ubuntu 12.10 system, all of which are recognized. I have proftpd setup and running, and when I run the sudo mount -o bind /media/username/harddrive /home/username/harddrive , it replicates perfectly. The issue I am having is when I edit the /etc/fstab with, /media/username/harddrive /home/username/harddrive vfat bind 0 0 it tries to mount it but gives me an "Unable to mount Harddrive: [mntent]: line 19 in /etc/fstab is bad
Mount: according to mtab, /media/username/harddrive is mounted on /media/username/harddrive
Mount failed
I need the /media/username/harddrive to replicate in /home/username/harddrive everytime on boot.

I know /etc/fstab is used for mounting partitions and such but is there any other way for this to work? I have tried getting the mount -o bind command to run at startup by putting it into a /etc/init.d file but that didn't seem to work, I probably didn't do it right.
Am I missing something? 
Any help would be greatly appreciated.

---

### Post by lasse210659 on 2013-04-28
hello im new at linux and dont know to to connect to my ftp server
please help

---

### Post by adm2p on 2013-05-23
8 years later...tnx again :cool:

---

### Post by guillaumesoucy on 2013-09-13
Hi, 

When I try to connect localy I get this error in FileZilla ; Réponse :    500 Sorry, no server available to handle request on ::ffff:192.168.2.22

Any ideas?

Thanks!

Guillaume

---

### Post by toni-appelqvist on 2013-09-17
I have ptoblem.
When restart ftp:
Stopping ftp server proftpd****************************************** [ OK ] 
** Starting ftp server proftpd************************************************* Master proftpd[29709]: Fatal: UserAlias: missing arguments on line 6 of '/etc/proftpd/proftpd.conf'


Conffile
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on


# Choose here the user alias you want !!!!
UserAlias userftp

ServerName*** *** *** "ChezFrodon"
ServerType *** *** *** standalone
DeferWelcome*** *** *** on

---

### Post by dave46 on 2013-09-20
I too am embarrassed to say I have the 530 error - I read the first 20~ pages of this thread, and also the last 10, but no solution was found that worked. 

> [L] USER root
[L] 331 Password required for root
[L] PASS (hidden)
[L] 530 Login incorrect.

and

> [L] USER ShareFTP
[L] 331 Password required for ShareFTP
[L] PASS (hidden)
[L] 530 Login incorrect.


Config file: 

> # To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias root ShareFTP

ServerName "FTP Server"
ServerType standalone
DeferWelcome on

MultilineRFC2228 on
DefaultServer on
ShowSymlinks off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayChdir .message
ListOptions "-l"

RequireValidShell off

TimeoutLogin 20

RootLogin on


ExtendedLog /var/log/ftp.log
TransferLog /var/log/xferlog
SystemLog /var/log/syslog.log

UseFtpUsers off

AllowStoreRestart on

Port 21


MaxInstances 8

User nobody
Group nogroup

Umask 022 022

PersistentPasswd off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8


AccessGrantMsg "Successfully gained access."

ServerIdent on "Welcome to a secure server.."


DefaultRoot ~

MaxLoginAttempts 5

#VALID LOGINS
<Limit LOGIN>
AllowUser ShareFTP
DenyALL
</Limit>

<Directory /home/FTP-Shared/>
Umask 022 022
AllowOverwrite off
<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
DenyAll
</Limit>
</Directory>

<Directory /home/FTP-Shared/download/*>
Umask 022 022
AllowOverwrite off
<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
DenyAll
</Limit>
</Directory>

<Directory /home/FTP-Shared/upload/>
Umask 022 022
AllowOverwrite on
<Limit READ RMD DELE>
DenyAll
</Limit>

<Limit STOR CWD MKD>
AllowAll
</Limit>
</Directory>



I can access the folders OK, so it isn't an error in them

> root@xx:/home/FTP-Shared/upload# cd /home/FTP-Shared/upload/
root@xx:/home/FTP-Shared/upload# cd /home/FTP-Shared/download/
root@xx:/home/FTP-Shared/download# cd /home/FTP-Shared/

I'm stumped now, and given up after an hour of changing password for ShareFTP, testing, changing FTP port, testing, checking folders etc.. 

Hopefully i'm something simple, i'm ready to look stupid but can't see it for the life of me! I removed the comment lines to make reading easier (hopefully).

---

