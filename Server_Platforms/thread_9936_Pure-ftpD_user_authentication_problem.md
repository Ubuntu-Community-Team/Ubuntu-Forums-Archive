---
title: "Pure-ftpD user authentication problem"
date: 2005-01-03
forum: Server Platforms
---

### Post by smooth.operator on 2005-01-03
this is what i'm typing to create a new user: 

sudo pure-pw useradd brother -u ftpuser -d /home/ftpusers/brother

then i type in the new password twice. now when i use ws_ftp to try and connect it says the user is OK then i get the following error message (ip address and user name changed):

Connecting to 127.0.0.1:21
Connected to 127.0.0.1:21, Waiting for Server Response
220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 1 of 50 allowed.
220-Local time is now 03:46. Server port: 21.
220-This is a private system - No anonymous login
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.
Host type (1): Automatic detect
USER brother
331 User brother OK. Password required
PASS (hidden)
530 Authentication failed, sorry

ideas anyone?

this is my first experience with linux so i'm not really that familiar with the command line.

---

### Post by britishtrident on 2005-01-03
No its fine for me   but I compiled from tar ball. Could be that some the complie flags  wern't set when the binary was compiled 

I did find however I couldn't use sftp and scp until ssh was installed  -- ftp shouldn't require it but try installing ssh if it isn't already installed.

---

### Post by smooth.operator on 2005-01-03
[QUOTE=britishtrident]No its fine for me   but I compiled from tar ball. Could be that some the complie flags  wern't set when the binary was compiled 

I did find however I couldn't use sftp and scp until ssh was installed  -- ftp shouldn't require it but try installing ssh if it isn't already installed.[/QUOTE]
 ok i think i have it figured out but how do i stop the service from running?

---

### Post by Sylphize on 2005-01-03
Try running "pure-pw mkdb" after adding, deleting and changing users. It's in the manual somewhere..

---

### Post by smooth.operator on 2005-01-03
Ok I've made the databases and I'm now at "enabling virtual users". I try to enter this line

/usr/local/sbin/pure-ftpd -j -lpuredb:/etc/pureftpd.pdb &

in order to "run the server with automatic creation of home directories and puredb
authentication" and I get the following error:

Unable to start a standalone server: Address already in use

so I run this command "invoke-rc.d pure-ftpd stop" and it tells me "Stopping ftp server: pureftpd.". Then when I run the command to enable virtual users I get the same error again. I'm about ready to say screw it and throw this machine out the window.

---

### Post by britishtrident on 2005-01-03
[QUOTE=smooth.operator]Ok I've made the databases and I'm now at "enabling virtual users". I try to enter this line

/usr/local/sbin/pure-ftpd -j -lpuredb:/etc/pureftpd.pdb &

in order to "run the server with automatic creation of home directories and puredb
authentication" and I get the following error:

Unable to start a standalone server: Address already in use

so I run this command "invoke-rc.d pure-ftpd stop" and it tells me "Stopping ftp server: pureftpd.". Then when I run the command to enable virtual users I get the same error again. I'm about ready to say screw it and throw this machine out the window.[/QUOTE]
 Are sure you don't have another ftp daemon installed ?

---

### Post by smooth.operator on 2005-01-03
[QUOTE=britishtrident]Are sure you don't have another ftp daemon installed ?[/QUOTE]
 how do i check if i do?

---

### Post by acidmax on 2005-01-07
[QUOTE=smooth.operator]how do i check if i do?[/QUOTE]

**netstat -ap | grep "*:ftp"**

Look at the end of the line.

For example:
# **netstat -ap | grep "*:ftp"**
# tcp        0      0 *:ftp                   *:*                     LISTEN     2938/**inetd**

The program in question is inetd.

---

### Post by Krank on 2005-05-30
I'm having the exact same problem, though I used the pure-pw command to create my virtual users. I am pretty dang sure i haven't another ftp daemon installed.

I am able to login using my linux user name and password - only the VIRTUAL users refuse to be authenticated - which satrikes me as being very, very weird.


Seeing as the Ubuntu/Debian version of ProFTPd seems to start automatically, using the /etc/init.d/ script, how do I go about adding and/or deleting command-line parameters? How do I enable/disable options?

---

### Post by Golgot on 2005-06-26
you need to comment the ftp line in the /etc/inetd.conf...

---

### Post by TheJoker on 2005-10-16
I'm having the same problem... *sigh* 

And, btw, the login message posted in the first post clearly shows that it's Pure-FTPD that's answering:

> Connected to 127.0.0.1:21, Waiting for Server Response
220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 1 of 50 allowed.

---

### Post by TheJoker on 2005-10-16
Fixed it! :)

My suspicions were correct; Pure-FTPd wasn't configured to use PureDB as authentication method.
To enabled PureDB you create a link in auth directory to the pure DB file
as such:
Go to Auth dir:
```
cd /etc/pure-ftpd/auth
```
To have PureDB checked first, give the link a lower number than anything else in that dir.
```
ln -s ../conf/PureDB 50pure
```
This will link 50pure to the PureDB configuration.

Should work now!

Now I need to figure out what to do with my firewall... :rolleyes:

---

### Post by ac3bf1 on 2005-11-28
hey guys new on this forum...

i see people have the same prob as i do...

in the previous post JOcker was saying to cd to the auth directory...

is there a reason why i dont have an Auth directory?

im running on fedore (thats the problem maybe?)

and i am getting the same

"Unable to start a standalone server: Address already in use" error

any idea why?
when i enter the command
```
pure-pw mkdb
```
it doesnt give any message (no error no nothing - thats fine?)

then i try and do 
```

/usr/local/sbin/pure-ftpd -j -lpuredb:/etc/pureftpd.pdb &

```
and it says that error
"Unable to start a standalone server: Address already in use"

i'm sort of nOOb on linux... :S
sorry :(

---

### Post by TheJoker on 2006-01-09
ac3bf1, it seems like your port is already take, probably by another FTP server program. Try looking in your etc start dir and shutting down any other FTP server you can find there. :) Sorry that I don't know an exact cure for your problem, but hopefully this will set you on your way. :)

---

### Post by bvk2 on 2006-02-05
Hello,

I've been trying unsuccessfully for nearly 3 weeks to get PureFTP Manager to work on my Mac OS 10.2.3. I too get the message:

Unable to start a standalone server: [Address already in use]

When I use Fetch, the following error is displayed:
Error: the server dropped the connection (it may be too busy).

A similar message is displayed if I telnet from the PC and the Mac (telnet command to open port: 10.1.1.2 21):
Unable to start a stand alone server: Address already in use.

I have the Mac and a PC connected to the router.
I have a static IP address. LAN IP on the Mac: 10.1.1.2 which I'm entering to test.

I have FTP access disabled in the Mac OS firewall settings.
FTP access is not blocked by service filtering in the modem/router's firewall settings.

I've set up port-forwading on ports 21, to 10.1.1.2. (Just following modem instructions)

I really have no idea when it comes to using the Terminal window and typing commands. I've tried to follow a suggestion from one of the posts but must be doing something wrong:
Welcome to Darwin!
[Bart-Kelseys-Computer:~] bartkelsey% netstat -ap | grep "*:ftp" 
netstat: option requires an argument -- p
usage: netstat [-Aan] [-f address_family] [-M core] [-N system]
       netstat [-bdghimnrs] [-f address_family] [-M core] [-N system]
       netstat [-bdn] [-I interface] [-M core] [-N system] [-w wait]
       netstat -m [-M core] [-N system]
[Bart-Kelseys-Computer:~] bartkelsey% 

Any suggestions?

Thank you for any contributions.

Bart

---

### Post by qferret on 2006-02-12
[QUOTE=smooth.operator]
Unable to start a standalone server: Address already in use
[/QUOTE]


inetd has a lock on port 21

You can confirm this by doing a:

sudo fuser -n tcp 21

The command above will spit out a pid if something is using the port named (21)

Look up the pid in System Monitor.....  probably inetd

For a single session you can:

sudo kill [pid]

Then try running pure-ftpd again....should work

If so, set inetd to not start @ boot:

sudo mv /etc/inetd.conf /etc/inetd.orig.conf

---

### Post by knockout on 2006-04-13
Hi,

I managed to stop inetd

```
sudo /etc/init.d/inetutils-inetd stop
```

I verified that port 21 was not in use.

Also, added the link to the pureDB auth.

Restarted pure-ftp in standalone mode.

Virtual user authentication still fails :-? 

Any answers?

---

### Post by pravuil on 2006-06-24
I got it to work. Most of this stuff is documented here: [http://download.pureftpd.org/pub/pure-ftpd/doc/README.Virtual-Users](http://download.pureftpd.org/pub/pure-ftpd/doc/README.Virtual-Users)  
and from previous posts in this thread. I just needed to condense it so you guys could know which step I'm talking about. This is instruction for installing pure-ftpd on a newly installed dapper installation.

You might not need pureadmin but if you're using a desktop environment I would definitely think about installing this as the graphical front-end.

```
# sudo -s
# apt-get install pure-ftpd pureadmin
```

Create the user and group accounts:

```

# groupadd ftpgroup
# useradd -g ftpgroup -d /dev/null -s /etc ftpuser
# pure-pw useradd NAME -u ftpuser -d /DIRECTORY
   Type in the password when prompted for the new user twice.
```

NAME *and* DIRECTORY *can be whatever you want them to be.*

Create the database and make sure that the pure-ftpd configuration strictly uses the pdb file for managing accounts:

```
# pure-pw mkdb
# ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/PureDB
# gedit /etc/pure-ftpd/conf/PAMAuthentication
   Change yes into no
```

[I]Make sure that a backup file (.PAMAuthentication~) isn't created because it will create a conflict when trying to restart service. Using PAM can allow public access to administrative accounts using pure-ftpd, that's why I disable it within pure-ftpd. I prefer it off so I can strictly use virtual accounts maintained within the pdb file.
[/I]
Finally it's time to enable the pdb file and yes you do have to stop the server in order to avoid errors stating that the port is already in use.

```
# /etc/init.d/pure-ftpd stop
# /usr/sbin/pure-ftpd -j -lpuredb:/etc/pure-ftpd/pureftpd.pdb &
# /etc/init.d/pure-ftpd start
```

It works great and is very simple to administer with PureAdmin. Most of the virtual user creation can be done there. Saves a lot of time. The visual log helps out a bit too.

---

### Post by floyd24 on 2006-12-20
> **pravuil said:**
> 
Finally it's time to enable the pdb file and yes you do have to stop the server in order to avoid errors stating that the port is already in use.

```

# /etc/init.d/pure-ftpd stop
# /usr/sbin/pure-ftpd -j -lpuredb:/etc/pure-ftpd/pureftpd.pdb &
# /etc/init.d/pure-ftpd start
```

The last bit is not needed on Dapper, I think. But maybe the package was already upgraded in my case (fresh install 2day). 

A simple

```

# /etc/init.d/pure-ftpd restart
```

did it all for me once the pdb file was created.

Keep in mind that on Dapper all the configuration for Pure-ftpd is done via the pure-ftpd-wrapper. See the correspoding manpage for more info on how to configure the demon using the configuration value files like the default install does.

For example, if you want to limit the maximum disk usage of your server to prevent flooding with large files, create a file called "MaxDiskUsage" in the "conf" subdir and add your value to it using your favourite editor. E.g. add a value of 80 to disable uploads as soon as the harddisk is 80% full.

```

# cd /etc/pure-ftpd/conf
# touch MaxDiskUsage
# chmod 644 MaxDiskUsage
# echo '80' >> MaxDiskUsage
# /etc/init.d/pure-ftpd restart
Restarting ftp server: Running: /usr/sbin/pure-ftpd -l puredb:/etc/pure-ftpd/pureftpd.pdb -O clf:/var/log/pure-ftpd/transfer.log -u 1000 -E -k 80 -B

```

As you can see from the output, another parameter (-k 80) has been added to the procramm call.

I think this is a very convenient way of configuring a server as it is very modular and simple (once you know how to do it). Actually, I didn't find a hint on the wrapper myself when I browsed through the documentation and howtos. I don't know if my reading was too bad or if the docs were not up to date. Anyway, it took away all my bad feelings about how to configure pure-ftpd and really I like how this is done on Ubuntu.

HTH, cheerz, Floyd

---

### Post by jaymoney on 2007-07-31
i was able to get pure-ftpd running following pravuil's instructions.  there were two things that had to be modified to get it working.

in the file /etc/pure-ftpd/conf/PureDB

i had to change the path to:

/etc/pureftpd.pbd

also. after stopping pure-ftpd, you need to change the path to point to the correct database as follows:

/usr/sbin/pure-ftpd -j -lpuredb:/etc/pureftpd.pdb &

thats all it took to install it on 7.04.

---

