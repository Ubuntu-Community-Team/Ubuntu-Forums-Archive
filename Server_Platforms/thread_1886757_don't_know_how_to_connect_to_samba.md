---
title: "don't know how to connect to samba"
date: 2011-11-25
forum: Server Platforms
---

### Post by ejames82 on 2011-11-25
hi,
I have a fresh install of ubuntu 11.04, and my sole purpose for installing it is to set up a samba server (this will be my first) that can be accessed via the internet.  
I have been following a tutorial on youtube:

[http://www.youtube.com/watch?v=_I1v5mBbby4](http://www.youtube.com/watch?v=_I1v5mBbby4)


for all intents and purposes, this is the smb.conf file:

[global]
        workgroup = TEST
        netbios = TEST
        security = share

[data]
        comment = data
        path - /home/data
        read only = no
        guest ok = yes
        writable = yes


I know this is far from being secure and elaborate.  this is just to make a connection and I will make adjustments accordingly after the connection is made.

I am also unsure about how to connect to the server right here in my own home.  I ran ifconfig and it stated the servers address to be 192.168.0.13 and when I tried to connect with another computer, it failed.  
I tried [http://localhost:901](http://localhost:901) with no success.  I also tried [http://localhost:901:8080](http://localhost:901:8080) with no success.  If everything about the samba server is fine, I may not be putting the proper address in the address bar.  I don't know how to find out what the address would be.

any help would be most appreciated.

---

### Post by ian dobson on 2011-11-25
Hi,

Samba is for file sharing and not http. So try accessing your share with \\192.168.0.13 (Fom windows start,run \\192. etc)

Note this will only work from within your network, not over the internet unless you reconfigure your router and even then your ISP might block samba network trafic.

Regards
Ian Dobson

---

### Post by ejames82 on 2011-11-25
ian dobson,

I tried it with:

\\192.168.0.13

like you suggested and 'firefox cant find the server'.  I used linux, but that shouldn't make a difference, should it?
also, with all due respect, are those slashes facing in the right direction, if so, my fault.  I know everything has to be perfect for it to work.

is there an active firewall in ubuntu 11.04 after fresh install?  I thought there wasn't, and that it needed to be turned on.

I built a 'minecraft server' a few days ago, and it connected to all computers in my home, but wouldn't connect to the web, which leads me to believe I have something wrong with this samba configuration (I don't think the router is interfering with the connection).  minecraft is a game, so using it as a server wouldn't benefit me.  that's why I am trying samba.

do you think that if I called the ISP (road runner) that they would tell me whether or not they are blocking me?

thanks for the reply.

---

### Post by ian dobson on 2011-11-25
Hi,

What do you see when you ping your server from another computer from within your network:-

ping 192.168.0.13

And yes the \\ slashes under windows mean this is a remote file server that has a directory/share.

I've just tried to access my backend server by typing \\192.168.0.2 (which is the IP address of my samba server) into internet explorer running on windows7 and it started explorer and opened the share, so I'd say it works.
 
Regards
Ian Dobson

---

### Post by volkswagner on 2011-11-25
Since your share has not been setup as browsable you may need the entire path.
To make sure it is browseable you can add the following to the share definition.

```
browseable = yes
```


Try:
\\192.168.0.2\data

or perhaps the smb protocol added like:

smb://192.168.0.2/data


From the server run:

```
testparm
```


So you have samba client installed on your client machine?  See if you client can see the server.  From the client run:

```
smbclient -L test
```


One thing I don't like is your netbios name is set to the same as the workgroup name.  Also from your Linux


Of all the SAMBA how-to's I've seen, never did I have the document have me clear out the entire smb.conf.  Usually create a backup and edit the existing smb.conf is the way to go.  There are some password schemes and such you'll be missing.  Also the log file pointer is not there so I don't know if samba will be logging for you.

---

### Post by Morbius1 on 2011-11-25
That how to is a piece of work - at least in a forum you have some level of peer review. Anything I would say has been covered by someone else but just look at what he had you do:
> [global]
        workgroup = TEST
        netbios = TEST
        security = share

[data]
        comment = data
        path - /home/data
        read only = no
        guest ok = yes
        writable = yes* There is no "netbios" parameter in samba - it's "netbios name"
* The path has the wrong syntax. the "-" sould be an "="

All of this would have come out when you ran the "testparm" command as suggested above but apparently the author of the HowTo never considered it.

---

### Post by ejames82 on 2011-11-26
sorry for the late reply, guys.  I just got home from work.  :)

after briefly reading your replies, I would like to quickly respond to Morbius1.  That was my fault.  That was a typo by me.

the syntax by the tutorial was indeed:

path = /home/data

I have to be more careful next time.  thanks for catching that.:oops:
by the way, it is correct in my smb.conf as well (with a "=")

now I will proceed toward trying what you guys suggest  :)

I will keep you informed.

---

### Post by ejames82 on 2011-11-26
ian dobson,

[B]What do you see when you ping your server from another computer from within your network:-

ping 192.168.0.13[/B]


here is just a sample of what I get:

64 bytes from 192.168.0.13: icmp_seq=1 ttl=64 time=0.199 ms
64 bytes from 192.168.0.13: icmp_seq=2 ttl=64 time=0.172 ms
64 bytes from 192.168.0.13: icmp_seq=3 ttl=64 time=0.177 ms
64 bytes from 192.168.0.13: icmp_seq=4 ttl=64 time=0.186 ms
64 bytes from 192.168.0.13: icmp_seq=5 ttl=64 time=0.178 ms
64 bytes from 192.168.0.13: icmp_seq=6 ttl=64 time=0.172 ms
64 bytes from 192.168.0.13: icmp_seq=7 ttl=64 time=0.177 ms
64 bytes from 192.168.0.13: icmp_seq=8 ttl=64 time=0.148 ms
64 bytes from 192.168.0.13: icmp_seq=9 ttl=64 time=0.175 ms
64 bytes from 192.168.0.13: icmp_seq=10 ttl=64 time=0.170 ms
64 bytes from 192.168.0.13: icmp_seq=11 ttl=64 time=0.178 ms

it keeps giving info endlessly.  this is a good sign, isn't it?


[B]And yes the \\ slashes under windows mean this is a remote file server that has a directory/share.

I've just tried to access my backend server by typing \\192.168.0.2 (which is the IP address of my samba server) into internet explorer running on windows7 and it started explorer and opened the share, so I'd say it works.[/B]
I stand enlightened.  :)

---

### Post by ejames82 on 2011-11-26
volkswagner,

=D>\\:D/

progress!

[B]perhaps the smb protocol added like:

smb://192.168.0.2/data[/B]
I added an attachment.  I hope the attachment works.  it shows that I got into the 'data' folder.  while I was there (connected via another computer) I made a folder 'mary' and sure enough there was a 'mary' folder there as well.  a connection has been established.

oh, and by the way, I did add:

browseable = yes

to the very end of the file.  I didn't know where else to put it.

I still haven't finished with the rest of your suggestions.

---

### Post by ejames82 on 2011-11-26
here is the 'testparm' command output:

root@ed-PC182A-ABA-SR1103WM-NA430:/etc/samba# testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Unknown parameter encountered: "netbios"
Ignoring unknown parameter "netbios"
Processing section "[data]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = TEST
	security = SHARE

[data]
	comment = data
	path = /home/data
	read only = No
	guest ok = Yes
root@ed-PC182A-ABA-SR1103WM-NA430:/etc/samba#

---

### Post by ejames82 on 2011-11-26
**So you have samba client installed on your client machine? See if you client can see the server.**
I don't have samba client installed.

the reason I am setting up the server is to allow my sister access to her family pictures that I have stored on several external hard drives.  I suppose she could install samba client (I have no problem with EVERYBODY installing it).  but if it's not necessary, I'd prefer not to.
I should wait and see what you guys recommend when you find out that I did connect.

and, even though I am a newbie, I think I understand your dissatisfaction over these entries:
1. the netbios name (or lack thereof)
2. the workgroup label

allow me to clarify.  this was just a 'quick and dirty' effort to see if I could get it to work with as little in the way as possible.  those things will be changed before the family pictures are able to be accessed.  I will have password verification and the whole nine yards when I am done.

Thanks you very much, ian dobson, volkswagner and Morbius1 for your expertise.  I hope I hear more from all of you.  :)

---

### Post by Morbius1 on 2011-11-26
By default Samba will use the host name to broadcast it's presence to the rest of the local network but it has rules. It must be 15 characters or less in length:
> root@[COLOR=Blue]ed-PC182A-ABA-SR1103WM-NA430[/COLOR]Yours is 28.

You need to add a parameter in smb.conf to correct for this length problem:
```
netbios name = test
```Then restart samba:
```
sudo service smbd restart
```The mistake in the HowTo was the author had you do a "netbios = test". There is no "netbios = " parameter in samba as the output of testparm stated above.

---

### Post by volkswagner on 2011-11-26
OK,

Before you go and spend time getting SAMBA setup, perhaps we should discuss your plans.

In your original post, you mention using SAMBA over the internet.  SAMBA is not a secure protocol and is not intended for use other than over LAN.

What operating system are the clients running?  If you don't want to setup SAMBA on your clients how do you plan to access the shares?  Try to access the share from Nautilus.  If you select <places><network> you should see your workgroup "test" (perhaps under "WindowsNetwork".

For sharing files over the internet I suggest you use SSH with SFTP, if you client machines are running Linux.  The nice thing about this, is it can look like your standard file browser for easy drag and drop.  Try from your Linux client, go to <places><connect to server> then choose ssh protocol and enter your server information username, etc.  This assumes you already have ssh running on both machines.

If they are not running Linux they can easily use the secure ftp protocol with an ftp client on port 22.


Another option would be to setup a WebDAV server.  This is not the most secure, but you can setup users with passwords + it's designed to work over WAN.

---

### Post by ejames82 on 2011-11-26
Morbius1,

I knew when I saw that long host name:

ed-PC182A-ABA-SR1103WM-NA430

that a problem would occur.
do I put exactly this:

**netbios name = test**

?
I actually would prefer to change the host name.  this name was chosen by the installer, not me.  do you know if this can be changed, and if so, how is it done?

**The mistake in the HowTo was the author had you do a "netbios = test". There is no "netbios = " parameter in samba as the output of testparm stated above. **
I will readily admit when I screw up, but this time HE did.  I do appreciate his tutorial though.

thanks

---

### Post by ejames82 on 2011-11-26
volkswagner,

**you mention using SAMBA over the internet. SAMBA is not a secure protocol and is not intended for use other than over LAN.**
and here I thought it was the preferred server software.

**What operating system are the clients running? If you don't want to setup SAMBA on your clients how do you plan to access the shares?**
I said I prefer not to, if possible.  the reason for this is, she lives 40 miles away and she's not very computer savvy.  if it's not a one or two click ordeal, I prefer that she doesn't even attempt it.  she's likely to get it wrong.

**Try to access the share from Nautilus. If you select <places><network> you should see your workgroup "test" (perhaps under "WindowsNetwork".**
I would assume that you mean the server machine for this task.  I clicked places>network>windows network>workgroup>ED-PC128A-ABA-SR which I tried to open and received:
"unable to mount location".  there is a screenshot attached.
I also tried (from another computer on the network) places>network>windows network, then tried to open, but received "unable to mount location".

**For sharing files over the internet I suggest you use SSH with SFTP,**
sounds ok to me.  you know about these things and I'm listening.  what are SSH and SFTP, some type of encryption?

**if you client machines are running Linux.**
in fact, they are.  but I would also like to be flexible and be accessible to windows if it's practical.  we can cross that bridge when we get to it.

**Try from your Linux client, go to <places><connect to server> then choose ssh protocol and enter your server information username, etc. **
it asks for server, port, folder, and username

would this be 'server'?

ed-PC182A-ABA-SR1103WM-NA430


port?....this wouldn't be 22 as well, would it?


folder?

/home/data


username?

ed


**This assumes you already have ssh running on both machines.**
I don't, but I will get it if I can.

**If they are not running Linux they can easily use the secure ftp protocol with an ftp client on port 22.**
I was going to try using ftp once, but didn't because part of the process was establishing a static IP address, if my memory serves me correctly.

**Another option would be to setup a WebDAV server. This is not the most secure, but you can setup users with passwords + it's designed to work over WAN.**
how secure is it once the username and password requirements are set up?
which, with your knowledge, is the way to go?

thanks.

---

### Post by volkswagner on 2011-11-26
> **ejames82 said:**
>   what are SSH and SFTP, some type of encryption?


[SSH]("https://help.ubuntu.com/community/SSH") is your friend, a friend you should be intimate with.  SSH is the single most used tool for administering a Server.

If you were using ssh, you could have performed the original how-to (youtube) while sitting at your client machine...(more on this later)


> **ejames82 said:**
> I was going to try using ftp once, but didn't because part of the process was establishing a static IP address, if my memory serves me correctly 

Likely any method of sharing will require your clients to know your external ip address.  If they would like to access it using a domain name and you want to compensate for a changing ip you will want a DynamicDNS service running such as [NoIP]("http://www.no-ip.com/") or [DynDNS]("http://dyn.com/dns/") or similar.

I think you should concentrate getting ssh server and client going on all your LAN machines.

When using nautilus to <connect to Server><ssh> you can use the ip of the server you are connecting to, any path(folder) and no need to specify the port unless the server is listening on a non standard port (not port 22).  The user you are connecting to needs to be a real user on that server.  There are more complex ways to set it up, but let's keep it simple for now.


To install ssh, I'd select the server and client for all machines.  It makes it convenient to work remotely to/from any box.

```
sudo apt-get install ssh
```

Test the ssh-client and ssh-server is working on the server machine:

```
ssh user@localhost
```

To disconnect:
```
exit
```

Then install ssh on the client and try to connect to the server:

```
ssh user@serverLANipAddress
```

Now this will open a shell session at the server just as if you were sitting at the physical machine.

---

### Post by ejames82 on 2011-11-27
volkswagner,

though there is much in your last post that I intend to respond to tomorrow morning (a long night at work), I felt this needed to be shown to you tonight.  it appears to be the most important info at this time.
bottom line is, it is asking for a password, and I was thinking it wanted my root password.  that's the only password I have made with this machine.

ed@ed-PC182A-ABA-SR1103WM-NA430:~$ sudo apt-get install ssh
[sudo] password for ed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openssh-server ssh-import-id
Suggested packages:
  rssh molly-guard openssh-blacklist openssh-blacklist-extra
The following NEW packages will be installed:
  openssh-server ssh ssh-import-id
0 upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 318 kB of archives.
After this operation, 954 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main openssh-server i386 1:5.8p1-1ubuntu3 [311 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main ssh all 1:5.8p1-1ubuntu3 [1,280 B]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main ssh-import-id all 2.4-0ubuntu1 [5,934 B]
Fetched 318 kB in 1s (202 kB/s)     
Preconfiguring packages ...
Selecting previously deselected package openssh-server.
(Reading database ... 165164 files and directories currently installed.)
Unpacking openssh-server (from .../openssh-server_1%3a5.8p1-1ubuntu3_i386.deb) ...
Selecting previously deselected package ssh.
Unpacking ssh (from .../ssh_1%3a5.8p1-1ubuntu3_all.deb) ...
Selecting previously deselected package ssh-import-id.
Unpacking ssh-import-id (from .../ssh-import-id_2.4-0ubuntu1_all.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Processing triggers for man-db ...
Setting up openssh-server (1:5.8p1-1ubuntu3) ...
Creating SSH2 RSA key; this may take some time ...
Creating SSH2 DSA key; this may take some time ...
Creating SSH2 ECDSA key; this may take some time ...
ssh start/running, process 22549
Setting up ssh (1:5.8p1-1ubuntu3) ...
Setting up ssh-import-id (2.4-0ubuntu1) ...
ed@ed-PC182A-ABA-SR1103WM-NA430:~$ ssh user@localhost
The authenticity of host 'localhost (::1)' can't be established.
ECDSA key fingerprint is 23:e6:39:9d:75:67:2b:a2:fc:5b:21:fa:43:f8:9b:0a.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added 'localhost' (ECDSA) to the list of known hosts.
user@localhost's password: 
Permission denied, please try again.
user@localhost's password: 
Permission denied, please try again.
user@localhost's password:

---

### Post by volkswagner on 2011-11-27
As mentioned earlier, the user you are trying to ssh into must be a real user located on the server (server being the ssh host machine).

So try:

```
ssh ed@localhost
```

---

### Post by ejames82 on 2011-11-27
volkswagner,

I need to take care of some automotive stuff this morning (I dont want to have to walk, and that's what will happen if I dont).  I promise I will get back to you later today.  I hope I dont lose your valuable help.  :)

here's a quick show of the successful command.

ed@ed-PC182A-ABA-SR1103WM-NA430:~$ ssh ed@localhost
ed@localhost's password: 
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-12-generic i686)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

New release 'oneiric' available.
Run 'do-release-upgrade' to upgrade to it.


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

ed@ed-PC182A-ABA-SR1103WM-NA430:~$

---

### Post by Paddy Landau on 2011-11-27
@ejames82, I will give you the solution that works for me (with Morbius1's help -- he's good at this).

But first:


[LIST]
[*]Samba is the Linux method of making the computer look like a Windows computer. Why would you want to do that? Because Windows (as usual with Microsoft) uses its own format and expects everyone else to conform. So, Linux conforms. Samba is the answer.

That's also why you don't install Samba on Windows.
[/LIST]

[LIST]
[*]Samba should be, but is not, easy and intuitive. :( But we can make it work anyway.
[/LIST]

[LIST]
[*]My instructions here assume you are connecting computers over the LAN and *not* over the Internet.
[/LIST]

[LIST]
[*]These instructions assume you are sharing just one folder on Ubuntu, and everyone within the network has full access to it. Get this working first, then you can work on adding new folders (if you want) and tightening the security (if you need).
[/LIST]
 
Try following these instructions and let us know what happens.


[LIST=1]
[*]Ensure you have installed [samba]("apt:samba"), [smbclient]("apt:smbclient"), and [nautilus-share]("apt:nautilus-share").
[*]Identify (or create) the folder on Ubuntu that you want to share. I use [FONT=Fixedsys]/public[/FONT]. Grant read-write access to everyone on that folder.
[*]Back up your current [FONT=Fixedsys]/etc/samba/smb.conf[/FONT] (in case my instructions don't work and you need to revert).
[*]Find out the name of your workgroup on Windows (in Networking and Sharing Centre). It's probably WORKGROUP if you didn't change it; I recommend that you do change it to something else.
[*]Find out the name of your Ubuntu computer. Change it if you want. You will find your computer's name in two places. (Strictly speaking, as Morbius1 will tell you, this is not necessary, but it makes it consistent and easier.)
[LIST=a]
[*]Look at the file [FONT=Fixedsys]/etc/hostname[/FONT]. It contains exactly one line, being your computer name. This is case-sensitive. Change it if you would prefer a different name. Remember what Morbius1 said: no more than 15 characters. Also note that you must never have two computers on the network with the same name, so check that it is not the same as your Windows computer name (Control Panel > System).
[*]Look at the file [FONT=Fixedsys]/etc/hosts[/FONT]. It has several lines, but the ones you are interested in start with [FONT=Fixedsys]127.0.0.1[/FONT]. There are two such lines; one has [FONT=Fixedsys]localhost[/FONT]. Leave that line alone. The other is your computer name. Change it to match whatever you put in [FONT=Fixedsys]/etc/hostname[/FONT].
[/LIST]
 
[*]Take my [FONT=Fixedsys]smb.conf.txt[/FONT] (attached). Make the following changes.
[LIST=a]
[*]Change [FONT=Fixedsys]WORKGROUP[/FONT] to the name of the Windows workgroup. This should be in capital letters.
[*]Change [FONT=Fixedsys]COMPUTERNAME[/FONT] to your computer name (as you have in /etc/hostname).
[*]Change [FONT=Fixedsys]COMMENT[/FONT] to some comment that will help you identify this share.
[*]Change [FONT=Fixedsys]/public[/FONT] to the path of the folder you want to share (from step 2).
[/LIST]
 
[*]Save this amended [FONT=Fixedsys]smb.conf.txt[/FONT] as [FONT=Fixedsys]/etc/samba/smb.conf[/FONT].
[/LIST]


Finally, reboot both your Windows and Ubuntu machines.



[LIST]
[*]You should be able to access Ubuntu from your Windows computer (without having to enter 192...). Just open your file browser, go to Network, and find it as if it were another Windows computer.
[*]You should also be able to access Windows from your Ubuntu computer (as long as you have a shared folder on Windows) from Nautilus. Just open Nautilus and go to Network.
[/LIST]

---

### Post by Morbius1 on 2011-11-27
@Paddy, thanks for the kind words but as you may or may not know there is a somewhat heated debate going on about step 6b. Some claim that you need to explicitly state it in smb.conf whereas I contend that it's already in the defaults. If you change the hostname in /etc/hostname and /etc/hosts and reboot it will automatically update the samba defaults. You can always verify this by running the following command:
```
testparm -sv /dev/null
```That will show you all the defualt settings of samba before you make any additions or modifications in smb.conf. The "netbios name" automatically becomes the hostname - unless of course you have some lan side dns thing going on.

Having gotten that rant out of the way I think that [COLOR=Blue]**volkswagner**[/COLOR] has the best approach in this particular case since this user is attempting to share things over the internet not his local lan. Using samba over the internet gives me the willies :)

---

### Post by Paddy Landau on 2011-11-27
> **Morbius1 said:**
> ... you may or may not know there is a somewhat heated debate going on about step 6b.
Thanks for that information. I was unaware of the debate. I guess that if Samba's specifications *explicitly* say that [FONT=Fixedsys]/etc/hostname[/FONT] is the default, then you should omit that line in order to reduce redundancy. It would be good if [FONT=Fixedsys]/etc/hosts[/FONT] could have an (optional) setting to use the computer name; then, there would be no redundancy at all.

> **Morbius1 said:**
> ... I think that [COLOR=Blue]**volkswagner**[/COLOR] has the best approach in this particular case since this user is attempting to share things over the internet not his local lan. Using samba over the internet gives me the willies :)
Thank you. I had misunderstood the previous posts. @ejames82, please ignore my previous post!

---

### Post by Paddy Landau on 2011-11-27
> **Morbius1 said:**
> If you change the hostname in /etc/hostname and /etc/hosts and reboot it will automatically update the samba defaults.
Out of interest, I changed [FONT=Fixedsys]/etc/hostname[/FONT] to have a name different from [FONT=Fixedsys]/etc/hosts[/FONT], removed [FONT=Fixedsys]netbios name[/FONT] from [FONT=Fixedsys]smb.conf[/FONT], rebooted and ran [FONT=Fixedsys]testparm -v[/FONT]. It seems that Samba explicitly uses [FONT=Fixedsys]/etc/hostname[/FONT] and not [FONT=Fixedsys]/etc/hosts[/FONT].

(I don't know what problems having two different names would cause, so I have set the names back to being equal again.)

---

### Post by Morbius1 on 2011-11-27
If you check /etc/hosts after changing just /etc/hostname and then reboot does 127.0.1.1 show the new hostname or the old one?
[COLOR=Blue]**EDIT:**[/COLOR] You know we really should be having this conversation here: [http://ubuntuforums.org/showthread.php?t=1884035](http://ubuntuforums.org/showthread.php?t=1884035)

---

### Post by ejames82 on 2011-11-27
Hello Paddy Landau, and welcome back Morbius1,

**I think that volkswagner has the best approach in this particular case since this user is attempting to share things over the internet not his local lan.**
**Thank you. I had misunderstood the previous posts. @ejames82, please ignore my previous post! **
**You know we really should be having this conversation here: [http://ubuntuforums.org/showthread.php?t=1884035](http://ubuntuforums.org/showthread.php?t=1884035)**
I am glad that both of you chose to exchange info within my thread.  

now I am looking forward to replying to volkswagner.

thanks.

---

### Post by ejames82 on 2011-11-28
volkswagner,

sorry it took so long to get back to you.

here I installed samba on the client:

ed@ed-desktop:~$ ssh user@serverLANipAddress
ssh: connect to host serverLANipAddress port 22: Connection timed out
ed@ed-desktop:~$ sudo apt-get install ssh
[sudo] password for ed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  openssh-server
Suggested packages:
  rssh molly-guard openssh-blacklist openssh-blacklist-extra
The following NEW packages will be installed:
  openssh-server ssh
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 286kB of archives.
After this operation, 827kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main openssh-server 1:5.3p1-3ubuntu7 [285kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main ssh 1:5.3p1-3ubuntu7 [1,256B]
Fetched 286kB in 1s (195kB/s)         
Preconfiguring packages ...
Selecting previously deselected package openssh-server.
(Reading database ... 266043 files and directories currently installed.)
Unpacking openssh-server (from .../openssh-server_1%3a5.3p1-3ubuntu7_i386.deb) ...
Selecting previously deselected package ssh.
Unpacking ssh (from .../ssh_1%3a5.3p1-3ubuntu7_all.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Processing triggers for man-db ...
Setting up openssh-server (1:5.3p1-3ubuntu7) ...
Creating SSH2 RSA key; this may take some time ...
Creating SSH2 DSA key; this may take some time ...
ssh start/running, process 2146

Setting up ssh (1:5.3p1-3ubuntu7) ...

ed@ed-desktop:~$ ssh user@serverLANipAddress
ssh: Could not resolve hostname serverLANipAddress: Name or service not known
ed@ed-desktop:~$ 




ed@ed-desktop:~$ ssh ed@serverLANipAddress
ssh: connect to host serverLANipAddress port 22: Connection timed out
ed@ed-desktop:~$ ssh user@serverLANipAddress
ssh: connect to host serverLANipAddress port 22: Connection timed out
ed@ed-desktop:~$

than I tried this again:

smb://192.168.0.2/data

and it would not connect.  maybe I screwed it up somehow.

---

### Post by ejames82 on 2011-11-28
volkswagner,

I had to change machines.  I am back on the server.

here is the testparm command:

ed@ed-PC182A-ABA-SR1103WM-NA430:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Unknown parameter encountered: "netbios"
Ignoring unknown parameter "netbios"
Processing section "[data]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = TEST
	security = SHARE

[data]
	comment = data
	path = /home/data
	read only = No
	guest ok = Yes
ed@ed-PC182A-ABA-SR1103WM-NA430:~$ 


another look at /etc/samba/smb.conf

[global]
        workgroup = TEST
        netbios = TEST
        security = share

[data]
        comment = data
        path = /home/data
        read only = no
        guest ok = yes
        writable = yes
        browseable = yes

---

### Post by ejames82 on 2011-11-28
here is from the client again:

ed@ed-desktop:~$ smbclient -L test
Enter ed's password: 
Connection to test failed (Error NT_STATUS_BAD_NETWORK_NAME)
ed@ed-desktop:~$ 

this is actually good news, isn't it?

look forward to hearing from you tomorrow.
thanks.

---

### Post by volkswagner on 2011-11-28
Please pay close attention to instructions.

Do you have an actual user, username = user?  When trying to ssh into your server you need to replace the username and the ip address to reflect that of your machine.

If you are still trying to get SAMBA going, I'd fix the NetBios Name entry as mentioned earlier.  I see you are still getting the error in testparm.  Also to use hostnames over LAN you need to have DNS working.

Lets try to keep it simple for now, as it appears you have a learning curve ahead.  Please concentrate on the SSH approach, as it should meet your long term goal better than SAMBA.

---

### Post by ejames82 on 2011-11-28
volkswagner,

**Do you have an actual user, username = user?**
when you installed ubuntu, the installer asks for your name.  since my name is ed james (and of course, I enter it as my full name), it assigns my username as ed.  it is probably a bad idea, but all my computers (at least the linux OSs) have my username as ed.  when I install windows, my username is either ed or ed james.

**When trying to ssh into your server you need to replace the username and the ip address to reflect that of your machine.**
with all due respect, this statement needs clarification.  I assume the computer you are referring to is the client.

to be sure of my username I ran this command on the (one and only) client machine:

grep x:1000 /etc/passwd | cut -d: -f1  

ed@ed-desktop:~$ grep x:1000 /etc/passwd | cut -d: -f1
ed
ed@ed-desktop:~$

now as for ip address, I hope I am not getting too far ahead of myself here, maybe this is what is needed (this is from the client machine):

ed@ed-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:20:7f:e4:41  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe7f:e441/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:200653 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:262315532 (262.3 MB)  TX bytes:12360214 (12.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ed@ed-desktop:~$

is 192.168.0.10 what we need?
this is assuming that we are querying the client machine specifically.
next, I need to know exactly where and how this info goes.  again, I don't want to get to far ahead, but would that be places>connect to server>service type:SSH
1. server
2. user

I am not, and I have not, changed anything about either of these computers without your say-so (I quit bothering with samba when you said).  the commands I have ran on my own were merely info-gathering commands that I knew would not change a thing.
also, I did run this command (from the client to the server) again:
ping 192.168.0.13

the output was the same as before.  ping still makes a connection.

for the sake of clarification:

server:  192.168.0.13
client:  192.168.0.10

thanks you so much, volkswagner.  I can see that you are highly respected here and deservedly so.  you clearly know your stuff.  I will be right here until thursday when I have to work again.

---

### Post by volkswagner on 2011-11-28
You can ssh into any machine from the terminal.


server: 192.168.0.13
client: 192.168.0.10

From a terminal session on client run the following:

```
ssh ed@localhost
```


If that works 

```
exit
```

then

```
ssh ed@192.168.0.13
```

If that works good!


```
exit
```

Let me know how you get on before we move ahead.

---

### Post by ejames82 on 2011-11-28
volkswagner,

I will leave it up to you as to whether or not it was successful.
here are the commands:

ed@ed-desktop:~$ ssh ed@localhost
The authenticity of host 'localhost (::1)' can't be established.
RSA key fingerprint is 0a:25:04:28:8d:5e:1d:22:28:ab:c2:f3:58:8c:2e:12.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
ed@localhost's password: 
Linux ed-desktop 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 15:27:15 UTC 2011 i686 GNU/Linux
Ubuntu 10.04.3 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

6 packages can be updated.
0 updates are security updates.


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

ed@ed-desktop:~$ exit
logout
Connection to localhost closed.
ed@ed-desktop:~$ ssh ed@192.168.0.13
The authenticity of host '192.168.0.13 (192.168.0.13)' can't be established.
RSA key fingerprint is 4e:c2:06:c7:33:37:44:78:89:20:4c:fc:df:13:bd:26.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.0.13' (RSA) to the list of known hosts.
ed@192.168.0.13's password: 
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-12-generic i686)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

New release 'oneiric' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Sun Nov 27 09:22:55 2011 from ed-pc182a-aba-sr1103wm-na430
ed@ed-PC182A-ABA-SR1103WM-NA430:~$ exit
logout
Connection to 192.168.0.13 closed.
ed@ed-desktop:~$

---

### Post by volkswagner on 2011-11-28
Excellent.  So tell me with all this don't you feel as though you'll never need a keyboard and monitor at your Server?

Now you should be able to browse your server via SFTP.

From your client:

Go to "Connect to Server" > 192.168.0.13 as server:> select SSH as the Protocol > port should default to 22 after selecting "SSH" > /home/ed as folder > ed as username > your password for ed on the server.

Dont check the box "Remember password" on the first try.  It is best to make sure it connects first.

---

### Post by ejames82 on 2011-11-28
volkswagner,

here I am with the info in the dialog boxes.

---

### Post by ejames82 on 2011-11-28
volkswagner,

here I am after clicking 'connect'.

---

### Post by ejames82 on 2011-11-28
volkswagner,

the last screenshot is a screenshot of success.

:guitar:

**Excellent. So tell me with all this don't you feel as though you'll never need a keyboard and monitor at your Server?**
well, once my sister starts downloading her pictures, the keyboard and monitor are not needed.

**Now you should be able to browse your server via SFTP.**
I was browsing.  I was definitely in the server.

**Go to "Connect to Server" > 192.168.0.13 as server:> select SSH as the Protocol > port should default to 22 after selecting "SSH" > /home/ed as folder > ed as username > your password for ed on the server.**
just like in the screenshot.

**Dont check the box "Remember password" on the first try. It is best to make sure it connects first.**
will I eventually have to check that box?

I suppose I was a bit difficult with a job that was relatively easy.:oops:

I am going to keep looking for your posts late into the night.  I am not going away.

thanks volkswagner.

---

### Post by ejames82 on 2011-11-28
volkswagner,

there is a new development.  it is an icon on the desktop.  all I have to do is click on it and voila, I am in the server.  hehe  :)

---

### Post by volkswagner on 2011-11-28
> **ejames82 said:**
> volkswagner,

there is a new development.  it is an icon on the desktop.  all I have to do is click on it and voila, I am in the server.  hehe  :)

Yes that will disappear after reboot.  You can drag that to the quick launch (sidebar) to create a more permanent shortcut (do this after enabling "remember password").

Next would be to open port 22 on your router so your sister can connect.  You may need to research your particular router to find how to forward port 22 to your server ip   (192.168.0.13).  Once you feel port forward is setup correctly, go to [www.canyouseeme.org](www.canyouseeme.org) and check to see if port 22 is visible.  If it is, then you can talk your sister through connection as you did on your lan.  Just substitute ip for your external ip. 

Are you going to setup a user on the server for your sister?  Where are her files located (what directory)?

With this opening of port 22 you will need to learn about security.

1. Disable root login on your server
2. It is more secure to require key authentication vs. password.
3. use strong passwords if you don't use keys.


I'll point you to the [sticky from this forum]("https://help.ubuntu.com/community/SSH").  That should get you through securing your server, ssh keys, etc.


This should help you implement a more secure connection when you are ready.

---

### Post by ejames82 on 2011-11-28
volkswagner,

**You can drag that to the quick launch (sidebar) to create a more permanent shortcut**
where is the 'quick launch (sidebar)'?  I tried dragging that icon to the top and bottom bars (but I haven't checked the box yet to remember the password either) would the top or bottom bars work too?

the router is supplied by my isp, road runner.  it is an ubee DDW2600.  I am going to see if google provides any info about opening port 22.

once it is determined that the port is open.  I assume that she will need to:
places>connect to server>SSH

1. server-will I find this info with this command (I am looking for the routers external ip address, is this correct)?
wget -O - -q icanhazip.com
2. port: 22
3. folder: /home/ed
4. username: ed

**Are you going to setup a user on the server for your sister?**
I will just be giving/providing files for her.  files are just going to travel in one direction, from my computer to hers.  would the steps above suffice for allowing this to happen?

**Where are her files located (what directory)?**
since she would be strictly receiving files, that wouldn't matter, would it?  I would imagine they would be located in the default ubuntu locations.  home, desktop, downloads, documents, etc.  her family pretty much uses it the same way it's laid out to use.  I can get that info if it's a must.

[B]With this opening of port 22 you will need to learn about security.

1. Disable root login on your server[/B]
I will need to know how to do this.

**2. It is more secure to require key authentication vs. password.**
I will need to know how to do this too.

while I am thinking of it, what is this type of connection called (specifically)?  I have done a little research and read a little about openSSH, but I don't think that is what this is.

thanks volkswagner  :)

---

### Post by ejames82 on 2011-11-28
volkswagner,

the default username and password do not work on this router, so I will need to contact the isp.  hopefully they will give me that info.

will keep you posted.  :)

---

### Post by volkswagner on 2011-11-28
```
wget -O - -q icanhazip.com
```

Works great for getting external ip.  I never used that before, it may come in handy, thanks.

What version of Ubuntu are you running on your client?  
```
cat /etc/issue
```
To expose the side bar you may need to select "View" > "Sidebar".

The reason I ask where your sisters files are located, was to be sure she will have permission to get them.  If you are lending her your username and password, and you can access the files, then there should be no problem.

The type of connection you are making is an SSH connection.  More specifically SFTP using SSH protocol.

The link I provided should have the info you need to set up keys and such.

To disable root login:

Create a backup of config file before editing it:
```
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak
```

Now open file for edit:
```
sudo nano /etc/ssh/sshd_config
```

Nano is an easy to use editor.  You can navigate the file with your arrow keys, and use backspace and delete!  At the bottom of the screen shows you shorcut keys for commands... <ctrl> + O enters save mode then using enter writes your changes to the file.  <crtl> + X, exits.

<ctrl> + W = where is or find, then type "PermitRootLogin" without quotes to find that in file.

Then change:

```
PermitRootLogin Yes
```

to

```
PermitRootLogin No
```

If it is not that way already.

Save and exit>

Restart ssh:

```
sudo /etc/init.d/ssh restart
```


You can also allow only connections from your sisters external ip address.

Using hosts.allow and hosts.deny you can limit the allowed sshd connections.

Create backups before editing... This is always true when editing config files.

```
sudo cp /etc/hosts.allow /etc/hosts.allow.bak
```
```
sudo cp /etc/hosts.deny /etc/hosts.deny.bak
```

Now edit the allow for your entire LAN and your sister's external ip, substitute the xxx for your sister's actual ip address.

```
sudo nano /etc/hosts.allow
```

Add the following to the end of the file, notice the last part of your ip is left off.  This allows any address in your LAN to connect.

```
# added my lan and Sister Ip
sshd: 192.168.0. xxx.xxx.xxx.xxx
```

Now lets add the deny.
```
sudo nano /etc/hosts.deny
```

Add the following to the end.

```
# Lets deny everyone unless they are in the hosts.allow for ssh
sshd: all
```

Restart ssh for good measure:
```
sudo /etc/init.d/ssh restart
```

With this setup, if your sister's external ip changes, you will need to update hosts.allow.

---

### Post by ejames82 on 2011-11-29
volkswagner,

SUPER POST!8-)

but there's bad news.  the account is in my wifes name and I had her call (right after she got home from work-touchy territory) and ask for the router username and password and they told us that the ubee DDW2600 is not capable of port forwarding.  if they were lying, I don't know why they would lie.  perhaps they think we intent to 'game' and they frown on gamers (lots of bandwidth use).  bottom line is, no access to port forwarding port 22.
they did say that we could buy our own router.

I am not sure what this ubee DDW2600 is/does.  I have electronic devices in a storage garage, that I believe are ethernet modems.  in fact, I specifically recall the first time I purchased road runner and the subscription ran out, their tech came to the house and I had the modem ready for him to take and he asked me if I wanted to keep it.  he said (and I quote) 'you would be doing me a favor by not making me take that'.  the reason I mention this is; maybe I can rustle together a modem (is it true that you NEED a modem?) and I have a completely functional (I am 99% certain that there is no password loaded into it) linksys 8-output router right here not even ten feet from me.  
if I have a working modem and this linksys router, can I remove the ubee (from blocking me)?  the thought of removing it permanently (if it doesn't slow down the connection) appeals to me.
I don't know if your expertise covers those areas of networking, I just thought I would ask.  If you don't know, maybe someone checking out the thread does.  :)


**What version of Ubuntu are you running on your client? **
10.04  I tried upgrading, but there were problems with unity, so a partial upgrade is all that happened.

I have looked at all the great info in your post and it is just torture that I can't take advantage (there would be no benefit) because of being unable to port forward.:(

I am going over to the garage tomorrow to get the devices that I believe are modems (and routers, why not) and bring them here.  my computer desk is wide open, so this kind of work is physically very easy.  I plan on extinguishing all possible options before I quit trying to make this server project work.  you obviously have gone all-out to help me and I intend to do the same to be helped.

thanks again, volkswagner for the very informative post.  :)

---

### Post by volkswagner on 2011-11-29
OK, this has gone off topic from SAMBA.  I sent you a PM.

---

### Post by ejames82 on 2011-12-01
to all observers:

the thread moved away from samba because volkswagner was able to show me a better alternative, SSH.

---

### Post by ejames82 on 2011-12-01
volkswagner,

I was able to find two modems, and as I told you before I have a fully functional router (linksys BEFSR81) to my access.  the modems are as follows:


surfboard SB4100

toshiba PCX2200


I am supposed to be able to connect the road runner to them via an F cable, and go to the computer with an ethernet cable, but I received 'limited or no connectivity' with either modem.  I can't get ANY webpage to come up.  I get 'this webpage cannot be displayed'.  
would you be offended if I posted at portforwarding.com with my problem?  if you have any suggestions I would be glad to hear them.

I really appreciate your help.  I would be glad to post whatever helpful info I receive, providing I make headway.

---

### Post by volkswagner on 2011-12-01
I am certainly not offended.

What do the activity lights tell you on the modem?

What is the output of ifconfig?

```
ifconfig
```

```
route
```

Makes me curious why you have so many modems??? Perhaps they are defective?


If you get WAN and Or cable activity, perhaps your ISP is looking for a certain mac address on the modem to enable the DHCP?

---

### Post by ejames82 on 2011-12-02
volkswagner,

I connected each modem specifically to run the commands on the server with ubuntu 10.04.  the lights are all constantly on except for the activity light on the surfboard, and the data light on the toshiba, which flash on and off rapidly.  I connect the modem directly to the computer, there is no router.
I am not a knowledgeable network tech.  I have alot to learn.  I am not even sure if I need a modem.  from what I have read, I do.

first I connected the surfboard and restarted.  when the computer first boots in to the desktop, I get an empty triangle-looking icon in the top bar where the up and down arrows normally would be, and along with them is the message 'eth0 disconnected-offline mode'.  I would later experience the exact same thing from the toshiba modem.


I was surprised when I ran the ipconfig command to receive a 'command not found' (I got that message with both modems).  I thought perhaps you meant ifconfig.


ifconfig from surfboard:

ed@ed-PC182A-ABA-SR1103WM-NA430:~$ ipconfig
No command 'ipconfig' found, did you mean:
 Command 'tpconfig' from package 'tpconfig' (universe)
 Command 'iwconfig' from package 'wireless-tools' (main)
 Command 'ifconfig' from package 'net-tools' (main)
ipconfig: command not found
ed@ed-PC182A-ABA-SR1103WM-NA430:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:09:14:1e:c6  
          inet6 addr: fe80::211:9ff:fe14:1ec6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10547 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:632820 (632.8 B)  TX bytes:6137 (6.1 KB)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

ifconfig from toshiba:

ed@ed-PC182A-ABA-SR1103WM-NA430:~$ ipconfig
No command 'ipconfig' found, did you mean:
 Command 'tpconfig' from package 'tpconfig' (universe)
 Command 'iwconfig' from package 'wireless-tools' (main)
 Command 'ifconfig' from package 'net-tools' (main)
ipconfig: command not found
ed@ed-PC182A-ABA-SR1103WM-NA430:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:09:14:1e:c6  
          inet6 addr: fe80::211:9ff:fe14:1ec6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5795 (5.7 KB)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)


the route command output was the same with both modems:

ed@ed-PC182A-ABA-SR1103WM-NA430:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
ed@ed-PC182A-ABA-SR1103WM-NA430:~$


**Makes me curious why you have so many modems??? Perhaps they are defective?**
I supposed they could be, but I don't think either are.  I just don't know the proper way to use them.  I have also got a users manual for each, however those users manuals are not as informative as they should be.

**If you get WAN and Or cable activity, perhaps your ISP is looking for a certain mac address on the modem to enable the DHCP?**
got any more suggestions?  :) 

I appreciate your efforts, volkswagner.

---

### Post by volkswagner on 2011-12-02
I'm not sure where you got the "ipconfig" from.  Clearly my post is pointing to the Linux command "ifconfig".

It is difficult to decide if your hardware is defective.  Normally the modem will have an indicator light  "cable" which would blink to indicate a good communication link with the WAN.

Possibly you have set up a static ip on your machine using /etc/network/interfaces or the network manager.

In my opinion I can't think of a good reason not to have full control over the network.

You either need to get the password for your current modem/router or a functioning unit.

A quick google search on my end lead to know evidence that your router/modem was not capable of port forward. [ Page 29 of the manual]("http://www.ubeeinteractive.com/user-guides/DDW2600_DDC2700_End%20User%20Guide_1.3-2009-07-28.pdf") indicates how to setup port forwarding.

Perhaps you should do a hard reset on your unit, and try the default user/password.

---

### Post by ejames82 on 2011-12-03
volkswagner,

**I'm not sure where you got the "ipconfig" from. Clearly my post is pointing to the Linux command "ifconfig".**
I don't know what I was thinking that day.  I'm sure it won't be the last time that happens.:confused::oops:  my fault.

**It is difficult to decide if your hardware is defective. Normally the modem will have an indicator light "cable" which would blink to indicate a good communication link with the WAN.**

the surfboard SB4100 has this:
1. power
2. receive
3. send
4. online
5. activity-this flashes

the toshiba PCX2200 has this:

1. cable
2. PC
3. data-this flashes
4. test
5. power


**Possibly you have set up a static ip on your machine using /etc/network/interfaces or the network manager.**
not purposefully.  I don't think I have.  I intend to, because everywhere I look says I need to do that.  I spent a bunch of time investigating and then had to work, which I have to do again tonight.  I do have all of the info written down.
IP address
subnet mask
default gateway and DHCP server
DNS servers

**In my opinion I can't think of a good reason not to have full control over the network.**
If I knew all that you know about networking I would already have the server working.

**You either need to get the password for your current modem/router or a functioning unit.**
I prefer to use the surfboard or the toshiba.  if I find that they absolutely won't work, I can still resort to the ubee and I still have internet.  the ubee is the only thing I am sure of at this point.

**You either need to get the password for your current modem/router or a functioning unit.**
does a modem ALWAYS have a password? 

**A quick google search on my end lead to know evidence that your router/modem was not capable of port forward. Page 29 of the manual indicates how to setup port forwarding.** 
with all due respect, I can't tell what you are saying here.  are you saying that the ubee can do it, or can't do it?

**Perhaps you should do a hard reset on your unit, and try the default user/password.**
I tried doing this on the surfboard.  there is a little hole that you stick a paper clip through and push.  it didn't work like I hoped.  there was still 'limited or no connectivity'.  on the toshiba I don't know if that function exists.  If I hard reset the ubee, I may lose internet, which of course, is a problem.

I have tomorrow to divulge into this situation again.  I haven't posted anywhere else yet.
thanks, volkswagner.

---

### Post by trogdor1138 on 2011-12-04
Hopefully you don't mind if I try to offer help too. I found the user manuals for both of those modems; have you tried looking at those and comparing to your modems' status lights to determine possible problems?

Surfboard: [http://www.motorola.com/staticfiles/Support/US-EN/Home-and-Office/Discontinued-Products/SURFboard-Cable-Modem-SB4100/Documents/Static-Files/SB4100_User_Guide.pdf](http://www.motorola.com/staticfiles/Support/US-EN/Home-and-Office/Discontinued-Products/SURFboard-Cable-Modem-SB4100/Documents/Static-Files/SB4100_User_Guide.pdf)

Toshiba: [http://www.toshiba.com/taisnpd/products/pcx2200_manual.pdf](http://www.toshiba.com/taisnpd/products/pcx2200_manual.pdf)

Also, when volkswagner asks if you have a static IP set up it's because you can't generally set up this way. If you want/need a static IP you'll need to contact your ISP and order one. Your server will still be set up to use DHCP, but the ISP will "automagically" give you the same IP address every time. This generally adds a monthly fee, so you'll want to ask about this. While you have them on the phone also ask if you need to have your MAC address registered. If this is the case it would explain why switching back and forth between modems is not successful.

Could you provide us with the contents of your network interface configuration? Probably the easiest way to get this is to enter 'cat /etc/network/interfaces'. This should print out the interface configuration file and you can then copy and paste.

Finally, it might be helpful to go over how your equipment actually needs to be set up. There are a few different ways depending on what your end-goal is.

A) Coax cable --> cable modem --> ethernet cable --> Ubuntu box

This setup is appropriate if your Ubuntu server is the only machine that will be connecting over this internet connection. No other machines will receive internet access in this configuration (unless you add another NIC to the Ubuntu box and set up bridging, but that's a whole different can of worms).

B) Coax cable --> cable modem --> ethernet cable --> switch --> computers

This setup will only work if you have specifically ordered multiple IP addresses from your ISP. Each machine is connected to the switch and is set up to use DHCP. I know your Motorola modem supports this, not sure if the Toshiba does. This is probably not what you want unless you have a specific reason.

C) Coax cable --> cable modem --> ethernet cable --> router --> computers

This setup is what I would recommend. Any decent router includes at least a basic firewall, separating your machines from the internet. Routers use NAT to allow all computers access to the internet by means of one public IP address. The router hosts and connects to the internet with a public IP (ie 101.1.2.3 as an example only) and your computers have private range IP addresses (ie 192.168.x.x addresses are common). The router has the job of routing (go figure) traffic between the two networks. Again, this is probably the best setup, unless you know specifically why not.

---

