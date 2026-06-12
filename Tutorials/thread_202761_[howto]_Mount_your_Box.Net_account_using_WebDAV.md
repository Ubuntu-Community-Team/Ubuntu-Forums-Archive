---
title: "[howto] Mount your Box.Net account using WebDAV"
date: 2006-06-24
forum: Tutorials
---

### Post by pingflood on 2006-06-24
Hello!

You can mount your [Box.Net](http://www.box.net/signup/invitation/box@pingflood.cjb.net) account to easily upload/download files.

First, install davfs2:

```

# apt-get install davfs2

```

Now, create the mount directory:

```

# mkdir /media/box.net

```

and mount:

```

# mount -t davfs http://www.box.net/dav /media/box.net

```

Insert your username and password and it's done!

You can also put your username/password in /etc/davfs2/secrets

```

echo "http://www.box.net/dav   username   password" >> /etc/davfs2/secrets

```

So, mount will not ask for username/password.

Also, Konqueror can access Box.Net directly using the WebDAV protocol:

```

webdav://www.box.net/dav

```

(I think the protocol is just "dav://" in Nautilus)

If you want a Free Box.Net account, 
[Box.Net](http://www.box.net/signup/invitation/box@pingflood.cjb.net)

Tested in Kubuntu Dapper Drake 6.06

More info and options:
```

$ man mount.davfs

```

Regards,
Ping Fløød
#356111

---

### Post by patrick295767 on 2006-07-03
Thank you !
Very nice
  
Btw, Is there somethg else than box.net
is there any good concurrents to this program ??

Pat'
  
-
I tried; works great !!
  I added -o rw 
but still cannot drag & drop (copy) from rox filer ... Is it normal ??

Thx

---

### Post by tcort on 2006-07-03
Wow, Box.net is really cool. Thanks for posting the howto.

---

### Post by joakim2 on 2006-07-03
Hmm.... this seems to be doing some really strange things... Copying a picture into the /media/box.net/ folder seems to work, using mv to move the picture it has suddenly disappeared (though it's now showing in the web interface but without a name...) I would be careful with this service :)

---

### Post by naked on 2006-07-03
I was trying to do this via "Connect to server" in the places menu and kept having trouble, how should I put the settings in there?  I'd like the keyring to manager my password for this and also auto connect for me.

Is this possible?

L

---

### Post by patrick295767 on 2006-07-04
[QUOTE=naked]I was trying to do this via "Connect to server" in the places menu and kept having trouble, how should I put the settings in there?  I'd like the keyring to manager my password for this and also auto connect for me.

Is this possible?

L[/QUOTE]
  
For the autoconnect, I guess the regular /etc/fstab would work ... 
then, you can play with permissions.
:rolleyes:
  
And, to mount the google box, is it the same way ?

---

### Post by gThree on 2006-07-05
@naked | anyone else:

Nautilus File Browser >> File >> Connect To Server
or
Start Menu >> Places >> Connect To Server

then

```

Service type = Secure WebDAV (HTTPS)
Server = www.box.net
Port = [leave blank]
Folder = dav
User Name = [optional, log-in will prompt for it]
Name To Use For Connection = ["boxnet" or whatever label you prefer]

```
**note:**
Like joakim2 had very mixed experience with above in Ubuntu Dapper/Power PC (G4).  Had error with davfs2.  Worked great with Kubuntu Dapper/Konqueror on same machine ... faster than Box.Net web access, split-pane interface, notifications ... suddenly a very useful service.  Bookmarked.  Used following to access:

```

webdavs://box.net/dav [certificate throws error]
or
webdav://box.net/dav

```
Haven't used Box.Net long enough to comment on quality of service itself, but so far so good.

@patrick295767:
When I checked around a month or so ago, Box.Net looked like best free option in terms of space, access and single upload size.

Hope that helps ....

---

### Post by gThree on 2006-07-07
Add:

Had best results in Ubuntu with Cadaver, a command-line webDAV client.  Fast, simple.  Could only get it to work with HTTP access.

---

### Post by twelve17 on 2006-09-28
I was having trouble mounting dav shares as a local user:

```
/usr/lib/mount.davfs-2.6: Can't get root permissions, maybe program is not setuid
```

I verified that the folders I created for the local mount points are readable by the user.  I would prefer to not have to make the program SUID, but I had to in order for it to allow normal users to mount:

```
foo@myhost:/$ sudo chmod u+s /usr/lib/mount.davfs-2.6

```

I couldn't think of any other ways to do this, as the man page states that the files are owned by the user who mounted the resource, which would mean that root would always own them. :(

---

### Post by PartickThistle on 2006-10-01
> **pingflood said:**
> Hello!

You can mount your [Box.Net](http://www.box.net/signup/invitation/box@pingflood.cjb.net) account to easily upload/download files.


Are you donating the money from your referrals to Ubuntu/Open Source projects?

---

### Post by iamacarpetlicker on 2007-02-06
Hey,
Every time I mount a WebDAV share it is only accessible as root, but I cant mount it as my normal user.
Is there any way to sort this out, am I just doing something wrong?

I have been doing....
*sudo mount -t devfs http://<local_server_ip>/dav/sam/ /home/sam/dav*
But then nothing will work on that folder, and I cant chmod it or anything. But it works with root fine.

Some help, please? :)

Thankyou lots,
Sam.

---

### Post by joshkidd on 2007-02-06
I just spent most of today trying to figure this out on my own.  So, here's my solution. 

First, I assume you've installed the davfs2 package.  If you haven't use the following command:

```
sudo apt-get install davfs2
```

By default this package is installed so that only root can mount davfs volumes.  To mount as other users, you need to set the SUID bit for /sbin/mount.davfs and designate a group whose members can mount davfs volumes.  To set the SUID bit, use this command:

```
sudo chmod u+s /sbin/mount.davfs
```

You then need to configure davfs so that only members of the group "users" can mount davfs volumes.  The config file for davfs is: /etc/davfs/davfs.conf  Edit however you like, but to use gedit:

```
gksudo gedit /etc/davfs2/davfs2.conf
```

There should be a line something like:

```
dav_group $group
```

This should be changed to:

```
dav_group users
```

Now, you should add your user to the users group:

```
sudo addgroup your-user users
```

Now add something like the following line to your /etc/fstab

```
http://<local_server_ip>/dav/sam/    /home/sam/dav    davfs    rw,user,noauto    0    0 
```

Here, I used your examples for the webDAV server and the mountpoint.  davfs is the filesystem type.  rw,user,noauto are the options.  user is the key option here.  It allows users other than root to mount the volume.  rw for read/write and noauto means it won't mount on startup.

At this point, I needed to restart my computer before anything would work.

When you get back to the prompt, all you need to do is:

```
mount /home/sam/dav
```

And you should be good to go.  If you have any questions, please ask.  I'm new to these forums too, but I hope I've explained well.

---

### Post by iamacarpetlicker on 2007-02-08
Hey Joshkidd,

Thankyou loads!! That worked amazing! =]
You rock, and yes you explained it perfectly.

Thankyou again!
Sam.

---

### Post by Oulianov on 2007-02-12
Hi,

Mount works great for me, but each time I try to write or read something (by nautilus or by a term), I get "I/O error" (nothing else....just "I/O error").

Does anybody have the same error ? Or a solution...

Thanks

Ouli

---

### Post by iamacarpetlicker on 2007-02-13
Maybe the I/O Error is to do with either a server or connection error?
You can try *[http://test.webdav.org/](http://test.webdav.org/)* to see if its a server error.

Also you could try and recompile *davfs2* to see its its a client error, or try *cadaver* which may give you a more detailed error message?

Thanks,
Sam.

---

### Post by Oulianov on 2007-02-13
> **iamacarpetlicker said:**
> Maybe the I/O Error is to do with either a server or connection error?
You can try *[http://test.webdav.org/](http://test.webdav.org/)* to see if its a server error.

I can read and write on test server

> Also you could try and recompile *davfs2* to see its its a client error, or try *cadaver* which may give you a more detailed error message?

I tried the last version of davfs2, same problem.
But cadaver works fine, I'm able to put or get a file.

I discovered that with davfs I can create a folder. No file, only folders.

That's quite strange, I didn't find anything one the web about.

Thanks

Ouli

---

### Post by uglowp on 2007-09-11
I have a similar problem.

I can mount boxnet ok, but I can't save any file to the folder.  I followed all the instructions in the thread but can't get it to work.

Any ideas?

Thanks!

Phil.

---

### Post by euphrate_ylb on 2007-09-24
Exactly, the same issue. 

I can't add/manage files. Most of the time I am told that the "file already exists" (cp in command line). In nautilus, it looks like I don't have write privileges.However I can create folders???

The problem remains with davfs2 1.2.2...

Works fine with cadaver.

Any help?

euphrate_ylb  
-------
[http://www.fbollon.net](http://www.fbollon.net)

---

### Post by munkiepus on 2007-10-03
I'm having the same problem where i can create folders via a mounted webdav folder but if i try to create a file it says "file exists" (when it really doesn't) or i/o error.

Cadaver works fine.

Anyone else found this problem :confused:

---

### Post by aitorcalero on 2007-11-13
I have the same issue (can create folders but no files). Does anyone find a solution or a workarround for this?

---

### Post by ulriks on 2008-01-27
To remount without restarting:
```

sudo mount -a

```

I had to remove line 16 and line 18 in my .davfs2/davfs2.conf to get be able to mount box.net. As with most people, I can create folders using the command line, but cp and mv does not work.

Adding box.net as a Network Folder (Kubuntu) allows me to copy and stuff using Dolphin.

---

### Post by Botsinge on 2008-02-23
The problem with I/O Errors upon copying/moving files has to do with the webdav server not responding well to file locks.

Add 'nolocks' to the options in the fstab entry or add '-o nolocks' on the command line.

See this thread for more info [http://sourceforge.net/forum/forum.php?thread_id=1619210&forum_id=82589]("http://sourceforge.net/forum/forum.php?thread_id=1619210&forum_id=82589")

---

### Post by aitorcalero on 2008-03-03
Thank you very much! Finally I could use WebDAV!!! :)

---

### Post by beansbbq on 2008-03-30
Hi everyone,


I recently signed up for Ubuntu 7.10 based hosting with VPSLink.  I wanted to try mounting Box.net from the command line to get a little more disk.  My plan was to place my photos and videos on Box.net, yet be able to access them 'locally'.  


Unfortunately I am encountering some problems. I'm receiving the following three lines after I enter my username and password.

===
/sbin/mount.davfs: no free coda device to mount
/sbin/mount.davfs: trying fuse kernel file system
/sbin/mount.davfs: fuse device opened successfully.
===

Now, I'm not sure what to make of this. I see the mount point 'Box.net' on the file system. When I 'cd' onto the mount point and try to 'ls', I receive the following message.

"ls: .: Transport endpoint is not connected
===

Can anyone make any sense of this, and what should I do to fix or get around this?  I opted for OpenVZ instead of Xen based hosting.  Could this be the cause of my problems?

Thanks in advance...

---

### Post by allmycrud on 2008-05-19
Did you ever get any answers?
I have the problem where I can mount box.net with my user and create folders and copy over files, but only the folders show up in box.net. Anyone have a solution to this?

Thanks

---

### Post by HappySpaceInvader on 2008-05-23
> **gThree said:**
> @naked | anyone else:

Nautilus File Browser >> File >> Connect To Server
or
Start Menu >> Places >> Connect To Server

then

[CODE]
Service type = Secure WebDAV (HTTPS)


Ah... there's a problem there, you see in Hardy Heron, I don't get the Secure WebDAV option - just the plain HTTP version.

---

### Post by EmilyRose on 2008-08-28
Yeah, I'm thinking the reason I can't login with the server is because its not HTTPS but only HTTP. So the only way I can get in is through the CL and then I can't access it cause' its mounted as bloody root!!

---

### Post by ya-manickill on 2008-11-14
Does anyone have any idea how to use a proxy through davfs? I would like to access my account when I am at uni, but it uses a proxy at uni, and I can't work out how to do that.

---

### Post by TheMacFactor on 2009-01-12
> **ya-manickill said:**
> Does anyone have any idea how to use a proxy through davfs? I would like to access my account when I am at uni, but it uses a proxy at uni, and I can't work out how to do that.

Set it up in /etc/davfs2/davfs2.conf

Read ```
man davfs2.conf
``` for the full story.

---

### Post by alexei.colin on 2009-10-03
Thank you for the great HowTo!

For me, mount, cp, mv, rm all work, and I can create directories, but the directories are not recognized as directories: cd says: "Not a directory."

Any thoughts on how to make davfs see that the directories are in fact directories? Thank you in advance!

---

### Post by xxilus on 2010-05-23
add this to /etc/fstab
```
https://box.net/dav       /media/box.net        davfs     defaults   0    0
```

---

### Post by covert on 2010-07-19
I got a error

"Input/output error"

When I tried to create a file on the box.net mount. I found this fix.

Put use_locks 0 to your davfs2.conf file

---

### Post by DrPotoroo on 2011-09-16
> **covert said:**
> I got a error

"Input/output error"

When I tried to create a file on the box.net mount. I found this fix.

Put use_locks 0 to your davfs2.conf file

That was very handy when I finally found this post. However, I'm still getting *some* input/output errors, both reading and writing files. Any ideas why?

Also, has anyone had any success using rsync or unison with a box.net mount? I tried rsync and it would do okay for a while then fail with input/output errors.

---

### Post by rudametkin on 2011-09-16
I just setup my box.net and wanted to share the steps with anybody having trouble. I suppose you've installed davfs already.

Create a mount point:
```

mkdir ~/box.net

```
Add this to /etc/fstab (correct the details for your user):
```
http://www.box.net/dav /home/user/box.net davfs rw,user,noauto 0 0

```
(Just as a note, https didn't work for me. It mounts but copied files never showed up. I saw something on their site about 256bit SSL encryption being available when you upgrade to business.)

To allow your your user to mount without being root you want to say yes to this:
```
sudo dpkg-reconfigure davfs2
```

Then add user to davfs2 group
```
sudo adduser $USER davfs2
```

Let's configure davfs in your home directory
```
mkdir ~/.davfs2
cp /etc/davfs2/davfs2.conf ~/.davfs2
```

Add this to ~/.davfs2/davfs2.conf:
```
use_locks       0
```

To avoid typing your login and password every time:
```
sudo cp /etc/davfs2/secrets ~/.davfs2
sudo chown $USER ~/.davfs2/secrets

```
Add your login and pass to ~/.davfs2/secrets:
```
http://www.box.net/dav	username@mail.com	password
```

And finally mount:
```
mount ~/box.net
```

I hope I didn't miss anything. I used some stuff originally found in french here: [http://doc.ubuntu-fr.org/davfs2](http://doc.ubuntu-fr.org/davfs2)


> **DrPotoroo said:**
> Also, has anyone had any success using rsync or unison with a box.net mount? I tried rsync and it would do okay for a while then fail with input/output errors.

I've been running rsync for a little while and ever since I got the configuration correct (i.e., nolocks, http) I haven't had any trouble. 

On the other hand, I want better synchronization so instead of rsync (or even Unison) I'm thinking of using something like dvcs-autosync or SparkleShare because they use a git backend and provide version control (among other features), but I haven't figured out how to set it up so that I can put the "central" .git repo on my box.net. (Maybe it's really simple.) Also, lots of my files are photos & music and I'm not sure if using git on them is a good idea.

[http://www.syncany.org/](http://www.syncany.org/) might be an interesting option, they say they provide synchronization for local folders (including nfs and fuse mounts) out of the box, but the project doesn't seem very mature yet.

Any ideas?

---

### Post by HuntMike79 on 2011-11-15
> **gThree said:**
> Add:

Had best results in Ubuntu with Cadaver, a command-line webDAV client.  Fast, simple.  Could only get it to work with HTTP access.

HI, would you mind telling me how you managed to connect to box.net using Cadaver?

I've tried many many times and get this error:


[FONT="Courier New"]Could not access /dav/ (not WebDAV-enabled?):
207 Multi-Status
Connection to `[www.box.net](www.box.net)' closed.
[/FONT]

What am I doing wrong?

---

### Post by purplemonk on 2011-11-16
EDIT:

Just figured out you have to pass the -t option to cadaver:


```
cadaver -t https://www.box.net/dav
```

and everything works perfectly. =)

> **HuntMike79 said:**
> 
[FONT="Courier New"]Could not access /dav/ (not WebDAV-enabled?):
207 Multi-Status
Connection to `[www.box.net](www.box.net)' closed.
[/FONT]


Hello, 

I'm getting the same error too here. Accessing to my box.net account through webdav on macos worked well a few days ago.

---

### Post by jat255 on 2011-12-21
> **purplemonk said:**
> EDIT:

Just figured out you have to pass the -t option to cadaver:


```
cadaver -t https://www.box.net/dav
```

and everything works perfectly. =)



Hello, 

I'm getting the same error too here. Accessing to my box.net account through webdav on macos worked well a few days ago.


Try switching the address to ```
https://www.box.com/dav
```

Box.net is undergoing a transition to Box.com (as I understand it) and I believe they deactivated access to the box.net domain via webDAV.

---

### Post by paperclip on 2011-12-21
Thanks.. I was able to connect with Nautilus using [www.box.com/dav](www.box.com/dav)

---

### Post by treesurf on 2011-12-26
> **paperclip said:**
> Thanks.. I was able to connect with Nautilus using [www.box.com/dav](www.box.com/dav)


thanks, this worked great for me as well.

---

### Post by Cicer on 2012-02-21
I kept getting this error:

```
/sbin/mount.davfs: Mounting failed.
302 Found
```

and solved it by changing my fstab from [http://www.box.net](http://www.box.net) to [https://www.box.com](https://www.box.com) after reading [this thread]("http://ubuntuforums.org/showthread.php?t=1807481").

I think the problem is that box.net redirects to box.com.

---

### Post by grana on 2012-03-08
I have a strange problem with mounted box.com + rsync.
Apparently, I succesfully uploaded (rsync'ed) 25GB of photos, but when I go to the web frontend (box.com), I see all the folder trees, some images, but most folders (the most recently uploaded) are empty.
Even stranger, on my local machine I can open and view the images in the mounted (/media/box.com) device.

I'm not a rsync expert, so maybe there's something I'm missing... can you help me?

Thanks
Federico

---

### Post by grana on 2012-03-08
> **grana said:**
> I have a strange problem with mounted box.com + rsync.
Apparently, I succesfully uploaded (rsync'ed) 25GB of photos, but when I go to the web frontend (box.com), I see all the folder trees, some images, but most folders (the most recently uploaded) are empty.
Even stranger, on my local machine I can open and view the images in the mounted (/media/box.com) device.

I'm not a rsync expert, so maybe there's something I'm missing... can you help me?

Thanks
Federico
edit: solved... Too stupid to be true!

---

### Post by AllGamer on 2012-05-18
Thank you! :KS

works like a charm

unfortunately, the Box.Net service is forever slow as it has always been, but that's a discussion for another topic



> **rudametkin said:**
> I just setup my box.net and wanted to share the steps with anybody having trouble. I suppose you've installed davfs already.

Create a mount point:
```

mkdir ~/box.net

```
Add this to /etc/fstab (correct the details for your user):
```
http://www.box.net/dav /home/user/box.net davfs rw,user,noauto 0 0

```
(Just as a note, https didn't work for me. It mounts but copied files never showed up. I saw something on their site about 256bit SSL encryption being available when you upgrade to business.)

To allow your your user to mount without being root you want to say yes to this:
```
sudo dpkg-reconfigure davfs2
```

Then add user to davfs2 group
```
sudo adduser $USER davfs2
```

Let's configure davfs in your home directory
```
mkdir ~/.davfs2
cp /etc/davfs2/davfs2.conf ~/.davfs2
```

Add this to ~/.davfs2/davfs2.conf:
```
use_locks       0
```

To avoid typing your login and password every time:
```
sudo cp /etc/davfs2/secrets ~/.davfs2
sudo chown $USER ~/.davfs2/secrets

```
Add your login and pass to ~/.davfs2/secrets:
```
http://www.box.net/dav	username@mail.com	password
```

And finally mount:
```
mount ~/box.net
```

I hope I didn't miss anything. I used some stuff originally found in french here: [http://doc.ubuntu-fr.org/davfs2](http://doc.ubuntu-fr.org/davfs2)




I've been running rsync for a little while and ever since I got the configuration correct (i.e., nolocks, http) I haven't had any trouble. 

On the other hand, I want better synchronization so instead of rsync (or even Unison) I'm thinking of using something like dvcs-autosync or SparkleShare because they use a git backend and provide version control (among other features), but I haven't figured out how to set it up so that I can put the "central" .git repo on my box.net. (Maybe it's really simple.) Also, lots of my files are photos & music and I'm not sure if using git on them is a good idea.

[http://www.syncany.org/](http://www.syncany.org/) might be an interesting option, they say they provide synchronization for local folders (including nfs and fuse mounts) out of the box, but the project doesn't seem very mature yet.

Any ideas?

---

### Post by Gaurne on 2012-06-07
> Thank you!   works like a charm  unfortunately, the Box.Net service is forever slow as it has always been, but that's a discussion for another topic      Quote:                      Originally Posted by rudametkin                I just setup my box.net and wanted to share the steps with anybody having trouble. I suppose you've installed davfs already.  Create a mount point:   Code:  mkdir ~/box.net Add this to /etc/fstab (correct the details for your user):   Code:  [http://www.box.net/dav](http://www.box.net/dav) /home/user/box.net davfs rw,user,noauto 0 0 (Just as a note, https didn't work for me. It mounts but copied files never showed up. I saw something on their site about 256bit SSL encryption being available when you upgrade to business.)  To allow your your user to mount without being root you want to say yes to this:   Code:  sudo dpkg-reconfigure davfs2 Then add user to davfs2 group   Code:  sudo adduser $USER davfs2 Let's configure davfs in your home directory   Code:  mkdir ~/.davfs2 cp /etc/davfs2/davfs2.conf ~/.davfs2 Add this to ~/.davfs2/davfs2.conf:   Code:  use_locks       0 To avoid typing your login and password every time:   Code:  sudo cp /etc/davfs2/secrets ~/.davfs2 sudo chown $USER ~/.davfs2/secrets Add your login and pass to ~/.davfs2/secrets:   Code:  [http://www.box.net/dav](http://www.box.net/dav) [email]username@mail.com[/email] password And finally mount:   Code:  mount ~/box.net I hope I didn't miss anything. I used some stuff originally found in french here: [http://doc.ubuntu-fr.org/davfs2](http://doc.ubuntu-fr.org/davfs2)     I've been running rsync for a little while and ever since I got the configuration correct (i.e., nolocks, http) I haven't had any trouble.   On the other hand, I want better synchronization so instead of rsync (or even Unison) I'm thinking of using something like dvcs-autosync or SparkleShare because they use a git backend and provide version control (among other features), but I haven't figured out how to set it up so that I can put the &quot;central&quot; .git repo on my box.net. (Maybe it's really simple.) Also, lots of my files are photos &amp; music and I'm not sure if using git on them is a good idea.  [http://www.syncany.org/](http://www.syncany.org/) might be an interesting option, they say they provide synchronization for local folders (including nfs and fuse mounts) out of the box, but the project doesn't seem very mature yet.  Any ideas? 
Hey guys, 
 
I couldn't agree more. I really don['](http://bestelectricshaverhq.org)t get why more people just don't get it. 
 
Great post, keep it up. 
 
Cheers!

---

### Post by Gaurne on 2012-06-07
> Thank you ! Very nice    Btw, Is there somethg else than box.net is there any good concurrents to this program ??  Pat'    - I tried; works great !!   I added -o rw  but still cannot drag &amp; drop (copy) from rox filer ... Is it normal ??  Thx 
Hey guys, 
 
I couldn't agree more. I really don['](http://bestelectricshaverhq.org)t get why more people just don't get it. 
 
Great post, keep it up. 
 
Cheers!

---

### Post by Gaurne on 2012-06-07
> is this script safe? (sorry, I'm newbish). 
Hey guys, 
 
I couldn't agree more. I really don['](http://bestelectricshaverhq.org)t get why more people just don't get it. 
 
Great post, keep it up. 
 
Cheers!

---

### Post by Gaurne on 2012-06-07
> Quote:                Thank you ! Very nice    Btw, Is there somethg else than box.net is there any good concurrents to this program ??  Pat'    - I tried; works great !!   I added -o rw  but still cannot drag &amp;amp; drop (copy) from rox filer ... Is it normal ??  Thx            Hey guys,    I couldn't agree more. I really don't get why more people just don't get it.    Great post, keep it up.    Cheers! 
Hey guys, 
 
I couldn't agree more. I really don['](http://bestelectricshaverhq.org)t get why more people just don't get it. 
 
Great post, keep it up. 
 
Cheers!

---

### Post by drumz on 2013-02-11
Has anyone taken the extra step to use encfs with this?  I'm trying, but apparently the davfs doesn't like filenames beginning with a period (i.e. ".foo").  Encfs uses a hidden file to store information and it fails silently when setting it up.  I just happened to try creating a hidden file in my box.com directory and discovered this was the issue:

[PHP]cd box.com
touch .foo
touch: cannot touch `.foo': No such file or directory[/PHP]

---

### Post by prokennexusa on 2013-03-17
To All-

I wated to take a moment and post this solution since I was working on the problem for most of the day today.

When I would type:

```
mount box.com

```

I would get this response:

```
/sbin/mount.davfs: Mounting failed.
Could not authenticate to server: rejected Basic challenge

```

This was the solution:

gksudo gedit /etc/davfs2/davfs2.conf

Add the following to davfs2.conf:

dav_group users
use_locks       0

Then type:

```

sudo addgroup <yourusername> users
```

Then do:

```
sudo apt-get update
sudo apt-get install cadaver


```

Then do:

```
cadaver -t https://www.box.net/dav
```

Login with your Box.com Username and Password once you sucessfully authenticate type 'quit' to exit from the session.

Finally, you will be able to sucessfully do:

```
sudo mount box.com

```
That is it! The bottom line is that most of the toutorials miss adding your name to the user group and finally installing cadaver. I do not understand why davfs2 requires cadaver, I suspect it calls to the cadaver module in the backgroud and if it is missing davfs2 has no way to authenticate ssl.

My system is Kabuntu 12.10 32-bit just in case another user requires this informtion. Thank you for having this thread available to us!

---

### Post by narsaw on 2013-04-26
Anyone notice that when box.net is mounted via webdav that it shows you have 26GB of storage with 13GB already used?

On their website it shows that I have 50GB on only 8.5MB in use

Why the difference?

```

% df -h
.
.
.
https://www.box.com/dav     26G   13G   13G  50% /media/box.net
.
.
.

```

---

### Post by guillemsola on 2013-08-31
I saw this and don't understand why, it's a bit annoying

> **narsaw said:**
> Anyone notice that when box.net is mounted via webdav that it shows you have 26GB of storage with 13GB already used?

```

% df -h
https://www.box.com/dav     26G   13G   13G  50% /media/box.net

```

---

