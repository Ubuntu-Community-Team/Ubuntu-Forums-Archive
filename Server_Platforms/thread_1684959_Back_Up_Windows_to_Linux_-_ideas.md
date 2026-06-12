---
title: "Back Up Windows to Linux - ideas?"
date: 2011-02-09
forum: Server Platforms
---

### Post by garfonzo on 2011-02-09
I need to back up a Windows computer to a Ubuntu server across the internet. It needs to be secure as I'm transferring business data. I have been searching high and low and am only coming up with sporadic, half solutions. Anyone have any good ideas or solutions that they have seen implemented? 

Thanks

---

### Post by kevinthecomputerguy on 2011-02-09
I have done this a few ways, when having to do it for free i use scp from a batch file, page 5 on my website.
 
But it totally sucks compared to this solution.
 
-Setup a linux box on the LAN with samba and webmin
-Install Cobian Backup on the windows machines, with the samba server as the backup destination for Cobain software.
-Setup the linux box to webmin-file-system-backup over ssh that data to another ssh box over the internet. (if .tar is too big, rsync it over ssh or rsh)

---

### Post by garfonzo on 2011-02-09
> **kevinthecomputerguy said:**
> I have done this a few ways, when having to do it for free i use scp from a batch file, page 5 on my website.
 
But it totally sucks compared to this solution.
 
-Setup a linux box on the LAN with samba and webmin
-Install Cobian Backup on the windows machines, with the samba server as the backup destination for Cobain software.
-Setup the linux box to webmin-file-system-backup over ssh that data to another ssh box over the internet. (if .tar is too big, rsync it over ssh or rsh)

Thanks for the response. Interesting idea, but isn't this overkill to have a second computer simply to forward files using rsync? Why not use the Window's version of rsync (cig-win or whatever) to do the same thing? 

I'm wondering if I need to make a custom solution...

---

### Post by garfonzo on 2011-02-09
> **kevinthecomputerguy said:**
> ... i use scp from a batch file, page 5 on my website...

Where's your website?

---

### Post by BenWuan on 2011-02-10
That additional computer would be a backup of your backup, at very least

---

### Post by garfonzo on 2011-02-10
> **BenWuan said:**
> That additional computer would be a backup of your backup, at very least
That's true. However, the Windows computer has two hard drives in it that are mirrored via a script that runs every night. I want to get a backup off site to my Linux server.

---

### Post by kevinthecomputerguy on 2011-02-10
Garfonzo-
Sorry, thought you were a faithful reader
 
[http://woodel.com](http://woodel.com)

---

### Post by garfonzo on 2011-02-10
> **kevinthecomputerguy said:**
> Garfonzo-
Sorry, thought you were a faithful reader
 
[http://woodel.com](http://woodel.com)

Thanks! And, now that I look at your signature picture, the website is right there. Go me. :confused:

---

### Post by Vegan on 2011-02-10
I use SAMBA on my Linux box so it can be a target for backups.

I find it very helpful as this way I can leverage the machine nicely for many tasks.

SAMBA is definitely been a must have in my shop. I am very grateful to the people who developed and maintained it.

---

### Post by garfonzo on 2011-02-10
> **Vegan said:**
> I use SAMBA on my Linux box so it can be a target for backups.

I find it very helpful as this way I can leverage the machine nicely for many tasks.

SAMBA is definitely been a must have in my shop. I am very grateful to the people who developed and maintained it.

But, do you access your Linux box outside your LAN?

---

### Post by elico on 2011-02-10
over the internet or on the lan?
if it's over the internet and you want it to be secure use a VPN connection like IPSEC with high encryption and you are done.
on the vpn connection you can use what ever mean you want.
another option is an SFTP conncection.
but in your case it' off site  so samba is not an option.
you can use cobian backup as a backup agent to make it simple the backup proccess.

---

### Post by garfonzo on 2011-02-10
Thanks for the responses. I am thinking that a VPN connection would do the trick (using OpenVPN, perhaps). However, I'm a little confused about what a VPN connection would look like on the client side and what they can "see". All the tutorials and examples I have been researching over the last 12 hours show everything up to the connection point with "... and now you should be connected." as the last line. Well that's nice, but what does a Window's client *see*!?

Can someone explain what the Window's user would actually see once the VPN connection is established? Does a network hard drive pop up? Does a new window showing a virtual desktop show up? I'm just not grasping what the client side sees. Further, I'm trying to see how this would fit into a backup solution that can be automated via scripts on the client side. 

Thanks!

---

### Post by HermanAB on 2011-02-10
Howdy,

Rsync is your friend.  Install Cygwin with OpenSSL and Rsync.  Then you do your backups exactly the same way as in Linux.

---

### Post by perspectoff on 2011-02-10
You can also use WebDAV.

I created a WebDAV server for all my files on a (K)Ubuntu server. 

I mount the WebDAV shares in Windows as virtual drives, and then use the native Windows utility Robocopy to backup to the virtual drive(s). 

Works pretty well for me, anyway.

It also allows me to use my (K)Ubuntu server as a virtual folder in Windows applications.

---

### Post by elico on 2011-02-10
when you are using a VPN it means you have a new network "card" on each end of the connection and all the machine services as samba nfs ftp or what ever you want will be like the other computer is "side by side" next to the local computer but!!
everything that will go from one server to the other will go inside the vpn that is encrypted.
but in your case im not sure that this is good for you.
one of the questions is "how does you local backup goes?"
if you are creating one file as a backup or maybe a directory you will might want to consider installing 
filezilla FTP server for windows that supports SFTP and just use the proper script on the linux machine to take the file\dir in specific time in the day.

---

### Post by garfonzo on 2011-02-10
> **elico said:**
> when you are using a VPN it means you have a new network "card" on each end of the connection and all the machine services as samba nfs ftp or what ever you want will be like the other computer is "side by side" next to the local computer but!!
everything that will go from one server to the other will go inside the vpn that is encrypted.
but in your case im not sure that this is good for you.
one of the questions is "how does you local backup goes?"
if you are creating one file as a backup or maybe a directory you will might want to consider installing 
filezilla FTP server for windows that supports SFTP and just use the proper script on the linux machine to take the file\dir in specific time in the day.

Ya, the more I look into the VPN thing, the more I think it is over the top for my needs. I'm intrigued by rsync, however your suggestion is interesting so I'll have to look into it. I never really thought of using a secure FTP setup to backup files. 

The backup I do on the Windows machine is a simple XCOPY script I wrote to copy the "data" directory from one physical hard drive to another within the same computer. I then want to scoop that data off the Windows box and send it to my Linux server. So, this FTP idea is good...

---

### Post by garfonzo on 2011-02-10
I think I have a solution that is:

[LIST=1]
[*]Secure
[*]Completely scriptable
[*]Free
[*]Works in Windows *and* Linux
[/LIST]

After reading through your suggestions, I did some hunting and found **[WinSCP]("http://winscp.net/eng/index.php")**. This is a free Windows based sftp client that is fully scriptable, yet has a GUI front end if it is needed (say by an employee). With this, I think I can host an ftp server on my Linux box and then have the Windows box automatically sync it's data to the server nightly. The beauty in with this setup is that my plan for the office was that, if their Windows box crashes (as a side note, this Windows box acts as a LAN server simply to host files), they would connect to the Linux server to continue their access to their data. Two birds, one stone, no? 

Anyone see any problems with this solution?

---

### Post by HermanAB on 2011-02-11
Howdy,

Rsync over SSH is pretty much the UNIX standard way to do it.  SSH is a kind of ad-hoc VPN and is very easy to use.  It can work as a secure terminal, a network VPN, a secure proxy and many other things.

Using rsync over over SSH is done as follows:

rsync -e ssh /from wherever hostipaddress:/towherever

On a Windows host with Cygwin, the paths are a little funny:
rsync -e ssh /cygdrive/c/fromwherever hostipaddress:/towherever

Read the rsync man page for details and examples.

---

### Post by maikel.b on 2011-02-11
Yes i think that this is a good solution, 

Use clonezilla, put the CD in the windows machine, reboot the computer, and start clonezilla from the CD.

Then you have a  few choices, just use beginner, and  use ssh to backup your windows machine..

I hope this is a good solution for you, we work in the Netherlands ( at my JOB ) only with these images..

Works as a m*th*r f*ck*r ;-)  Oke and one thing, you can also restore the system with clonezilla, its backing up the whole system.... even partitions!!!!! make sure that your new drive is the same, or greater!!! ( BIGer!!)

Have a nice day

---

### Post by elico on 2011-02-11
ssh\RSYNC is the same...(the idea)
it's a good idea to use winscp.
if you do ask me i still think about SFTP either on the windows machine or the linux one.
crygwin is nice but i think that if you do have a native option for the server and client such as filezilla or any other way it's much more better (for you).
if you can do winscp scripting for auto bakcup using ssh than go for it.
by the way instead of using xcopy you can use some storage file such as zip\tar\7zip.
but it depends on the size of the files and the size of the directory tree you are using.
if it's a small list of files use the xcopy but if you do have a big amount of files you sure better use one file to store it and them transfer it to the remote machine.

---

### Post by garfonzo on 2011-02-11
> **HermanAB said:**
> Howdy,

Rsync over SSH is pretty much the UNIX standard way to do it.  SSH is a kind of ad-hoc VPN and is very easy to use.  It can work as a secure terminal, a network VPN, a secure proxy and many other things.

Using rsync over over SSH is done as follows:

rsync -e ssh /from wherever hostipaddress:/towherever

On a Windows host with Cygwin, the paths are a little funny:
rsync -e ssh /cygdrive/c/fromwherever hostipaddress:/towherever

Read the rsync man page for details and examples.

Thanks for the response. I do agree that rsync is a good method. I use rsync on my personal Linux box for weekly backups of multiple drives. My concern with using rsync in a Windows environment is that it is not native and so a workaround (cygwin) is needed. I know this isn't a big deal, but an extra "step" nonetheless.

---

### Post by garfonzo on 2011-02-11
> **maikel.b said:**
> Yes i think that this is a good solution, 

Use clonezilla, put the CD in the windows machine, reboot the computer, and start clonezilla from the CD.

Then you have a  few choices, just use beginner, and  use ssh to backup your windows machine..

I hope this is a good solution for you, we work in the Netherlands ( at my JOB ) only with these images..

Works as a m*th*r f*ck*r ;-)  Oke and one thing, you can also restore the system with clonezilla, its backing up the whole system.... even partitions!!!!! make sure that your new drive is the same, or greater!!! ( BIGer!!)

Have a nice day

Thanks for the response. The only problem is that I won't have physical access to the Windows box. The system will be 1,100 miles away from me. I've got it with me now during the setup stage, but it will be heading out in a couple of weeks for deployment.

---

### Post by garfonzo on 2011-02-11
> **elico said:**
> ssh\RSYNC is the same...(the idea)
it's a good idea to use winscp.
if you do ask me i still think about SFTP either on the windows machine or the linux one.
crygwin is nice but i think that if you do have a native option for the server and client such as filezilla or any other way it's much more better (for you).
if you can do winscp scripting for auto bakcup using ssh than go for it.
by the way instead of using xcopy you can use some storage file such as zip\tar\7zip.
but it depends on the size of the files and the size of the directory tree you are using.
if it's a small list of files use the xcopy but if you do have a big amount of files you sure better use one file to store it and them transfer it to the remote machine.

Thanks for the response. I agree that a native solution is (possibly) better. This WinSCP does have SFTP as an option so I like the security potential. About zipping it up, the concern I have with this is that the office's internet connection is slow and intermittent. I would imagine that if the backup starts on one *big* file and is interrupted, nothing would transfer. Whereas if there are many small files (which is the case with us) at least a partial transfer would occur. I could "pickup" the missed files on the next backup.

---

