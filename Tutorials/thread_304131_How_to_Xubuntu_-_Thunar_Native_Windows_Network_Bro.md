---
title: "How to: Xubuntu - Thunar Native Windows Network Browsing"
date: 2006-11-21
forum: Tutorials
---

### Post by Tazix on 2006-11-21
Since Thunar doesn't have native network Browsing, here is a good way to accomplish it:

1) In XFCE's Applications -> System -> Shared Folders. (This should trigger a Samba install if you don't already have a share, and it should allow you to define the proper workgroup)

2) Install fusesmb in Synaptic (from Universe repository)

3) Edit /etc/modules and add the word 'fuse' to the modules list to be loaded (without quotes), and save the file.

4) Reboot, so the fuse module loads, and the proper workgroup is read for samba.

5) In XFCE Applications -> System -> Users and Groups... Properties of your username... User Priveleges Tab... check "Allow use of fuse file systems..."

6) Create a directory that you are going to mount your network browse to... I used /media/network. Change permissions to read / write for group and others (777).

*** 6.5) In a terminal, type: sudo chown <username>:fuse /media/network
(Where <username> is your user account logon name)

*** 6.6) Double check that the permission to use fuse took. Applications -> System -> Users and Groups... Manage Groups... find fuse and choose properties.  Make sure your user name account is in that group and check-marked.

*** 6.7) Reboot the system and triple check with step 6.6

7) In XFCE Applications -> Settings -> Autostarted Applications... Add an application... name and describe as you wish... for command line, put: fusesmb /media/network (Or whatever mountoint you created).

8) Open Thunar, and navigate to the parent folder of your mountpoint... then drag the 'mounpoint folder' to the places (shortcut) pane of thunar.

9) Logout and log back in (So the user privilege and fusesmb autostart will take affect)

*** Added steps to help prevent some access denied issues some people have been experiencing with fusesmb.

My original thread on this topic is here: [http://www.ubuntuforums.org/showthread.php?t=300310](http://www.ubuntuforums.org/showthread.php?t=300310)

I hope this helps my fellow Xubuntu users... and I also hope that the Xubuntu team somehow enables something similar by default, or at least as an install option.

-Taz

---

### Post by foxy123 on 2006-11-24
It is definitely a Edgy how-to. However I managed to accomplish it on Dapper.

For those who is still on Dapper like myself and have no intention to move to Edgy in the nearest future:

1. You can backport fusesmb using an excellent prevu tool, see the topic here
[http://www.ubuntuforums.org/showthread.php?t=268687](http://www.ubuntuforums.org/showthread.php?t=268687)

Alternatively I am attaching a Daper version, I backported myself to this thread.

2. You need to add yourself in the fuse group using Users and Groups tool as there is no entry like "Allow use of fuse file systems..." in my case.

For some reason I had to reboot a number of times to make it work. But I have not done anything else.

---

### Post by sawjew on 2006-11-25
This is great.  I gave up on Xubuntu and went back to Ubuntu just because of the lack of a network browser.  This is so simple, I hope it gets included in the next release of Xubuntu if not in Thunar itself.  The only problem I have though is how to access a password protected user share.

Any ideas?

---

### Post by ruscook on 2006-11-26
I haven't got this working yet, but will I hope.

My workaround was just to put the nautilus home folder on the desktop/appbar and use that for my SMB browsing, other times I use thunar. Not ideal I know but it saved me going back to Gnome.

Russ

---

### Post by EatMorePie on 2006-12-02
Thanks for this.  I was able to get it going without installing samba, thus avoiding the overhead of being a server, since all I want to do is access shares on other servers.

Basically skip step 1, do all the other steps.

Skipping step 1 avoids all the server stuff but you'll have to do one or two other things before you're done:

Manually edit ~/.smb/fusesmb.conf to add your windows browsing credentials:
```
[global]
username=YourSMBUsername
password=YourSMBPassword

```

Do a "man fusesmb.conf" to learn what other options you can put here, but this is all you absolutely need.

Additionally I had to "chgrp fuse /dev/fusesmb", which should have happened automatically when fuse was installed but didn't.

To make life easier I added a launcher to the panel to run "thunar /media/network/" and gave it the file management icon.

That's it; all the browsing convenience and none of the being-a-server overhead.  Thanks again for the great howto.

---

### Post by kalikiana on 2006-12-02
I was just playing with a custom python app for that but maybe now I won't need that anymore since I can access everything directly from within Thunar.
Only drawback: Accessing my own shares works only partly and it says I don't have permissions for some folders. Weird...

---

### Post by detyabozhye on 2006-12-03
Awesome dude, maybe later I'll write an automated shell script for this. :D

---

### Post by Tazix on 2006-12-03
> **foxy123 said:**
> It is definitely a Edgy how-to. However I managed to accomplish it on Dapper.

Yes, it's an edgy How-to.  Glad you found a way to do it on Dapper! :)

> **sawjew said:**
> The only problem I have though is how to access a password protected user share.

Any ideas?

Not the most secure solution... but set your shares on the Windows box to "full control" for "everyone", and in the advanced options, set it to make the changes to the child folders and files.  If you are using "simple sharing"... check the box to "allow network users to change files".

> **EatMorePie said:**
> Thanks for this.  I was able to get it going without installing samba, thus avoiding the overhead of being a server, since all I want to do is access shares on other servers.

Basically skip step 1, do all the other steps.

Well, the first step is so you can send files back to your Xubuntu box from a Windows box.  If one doesn't have a need for that... then, yes... skip step 1.

> **kalikiana said:**
> Only drawback: Accessing my own shares works only partly and it says I don't have permissions for some folders. Weird...

See above... check your Windows security permissions on those shared folders that are giving problems.  Windows file sharing is a little wonky. ;)

---

### Post by grumpymole on 2006-12-03
Tazix,

Thanks, this [works well for me]("http://grumpymole.blogspot.com/2006/12/xubuntu-browsing-samba-shares-with.html") running Feisty, which shouldn't be that different from Edgy at the moment.  

Regards

Warren
[http://grumpymole.blogspot.com](http://grumpymole.blogspot.com)

---

### Post by detyabozhye on 2006-12-04
My idea won't work for this. What I want to do is make a graphical way to mount ISOs and FTP sites using Fuse. I wanted to do the SMB as well, but it mounts the whole network, not just one server or share, so my idea is unnecessary here.

---

### Post by sawjew on 2006-12-04
This works well until the network changes.  It only picks up what's on the network at boot not anything that is added later.  Is there any way to refresh the network?

EDIT:  I just found the answer to my own question from here [http://ubuntuforums.org/showthread.php?t=71797]("http://ubuntuforums.org/showthread.php?t=71797")
Just open a terminal and type in
```
fusesmb.cache
```

---

### Post by Miguellint on 2006-12-16
Hi all...Newbie alert :-)

I have followed the how-to but when I reach the final step (opening the /media/network folder) there is no MSHOME inside.

When I check /media/network folder permissions I find Owner (Root) is still read and write but Group and Others have been changed to read only. 

The "Allow use of fuse filesystems etc" box mentioned in step 5 is ticked.

sudo chmod 777 /media/network gives permission denied.

mount /media/network gives....

according to mtab, fusesmb is already mounted on /media/network   mount failed

FWIW, in "Process Manager" I have two instances of fusesmb running. 

Any advice appreciated.

Regards
Miguel

---

### Post by Tazix on 2006-12-17
> **Miguellint said:**
> sudo chmod 777 /media/network gives permission denied.

Sounds like either your sudo is messed up, or fusesmb is "locking" the changing of the directoy or something.

Since I don't see any way in the help / man pages to start / stop fusesmb... Try undoing step 7, so it doesn't auto start (remove the auto started application in xfce)

If you are also running it in your fstab, edit and take it out of there too.

Reboot... then try to sudo chmod 777 /media/network in a terminal window.

If you can successfully change the permissions to 777, Then redo step 7 and don't add anything to your fstab.

---

### Post by Miguellint on 2006-12-18
> **Tazix said:**
> Sounds like either your sudo is messed up, or fusesmb is "locking" the changing of the directoy or something.

Since I don't see any way in the help / man pages to start / stop fusesmb... Try undoing step 7, so it doesn't auto start (remove the auto started application in xfce)

If you are also running it in your fstab, edit and take it out of there too.

Reboot... then try to sudo chmod 777 /media/network in a terminal window.

If you can successfully change the permissions to 777, Then redo step 7 and don't add anything to your fstab.

Hello Taz....Thanks for the reply. Still no success.

There's no mention of fusesmb in my /etc/fstab.

Without the fusesmb autostart I can manually sudo chmod 777 /media/network.

But after I fusesmb /media/network in the terminal the permissions change back to Owner rw, Group and Others ro which was my original problem.

However once I do the fusesmb /media/network command my /etc/mtab has a fusesmb entry....

fusesmb /media/network fuse rw,nosuid,nodev,max_read=32768,user=samsung 0 0

(samsung is my username). Is this of any help?

Thanks
Miguel

---

### Post by reacocard on 2006-12-18
> **Miguellint said:**
> 
But after I fusesmb /media/network in the terminal the permissions change back to Owner rw, Group and Others ro which was my original problem.


Try running fusesmb with this command instead:
```
fusesmb /media/network -o allow_other
```
that should fix the permissions so anyone can access it.

---

### Post by Miguellint on 2006-12-18
> **reacocard said:**
> Try running fusesmb with this command instead:
```
fusesmb /media/network -o allow_other
```
that should fix the permissions so anyone can access it.

Hello reacocard....Thanks for taking the time to reply.

I entered the command as you suggested but there's no change except /etc/mtab now reads.....

fusesmb /media/network fuse rw,nosuid,nodev,allow_other,max_read=32768,user=samsung 0 0

Before I entered the fusesmb command, /media/network was owned by root and everyone had read and write permissions.

After I entered the fusesmb command, /media/network was owned by samsung (my user name) and Group and Others became read only. When I try to manually change the permissions I get "access denied"

Should "system/users_and_groups/root/properties/user privileges/allow use of fuse...." be ticked or not. My "user_name/allow use of fuse...." is ticked as per Taz's original instructions, but root isn't. (FTR, I've tried root ticked and not ticked and neither seem to make a difference.)

Any help appreciated.

Thanks
Miguel

---

### Post by reacocard on 2006-12-19
> **Miguellint said:**
> I entered the command as you suggested but there's no change except /etc/mtab now reads.....

fusesmb /media/network fuse rw,nosuid,nodev,allow_other,max_read=32768,user=samsung 0 0

Before I entered the fusesmb command, /media/network was owned by root and everyone had read and write permissions.

After I entered the fusesmb command, /media/network was owned by samsung (my user name) and Group and Others became read only. When I try to manually change the permissions I get "access denied"

Try doing fusesmb as root instead:
```
sudo fusesmb /media/network -o allow_other
```
that should work. If this fails, you could just mount fusesmb with read-write for your current user in /home/<username>/Network, thereby avoiding the permissions problem altogether.

> 
Should "system/users_and_groups/root/properties/user privileges/allow use of fuse...." be ticked or not. My "user_name/allow use of fuse...." is ticked as per Taz's original instructions, but root isn't. (FTR, I've tried root ticked and not ticked and neither seem to make a difference.)

Yes, allow fuse should be checked. Having root's checked shouldn't matter, as root has access to everything.

---

### Post by Miguellint on 2006-12-19
Hello again reacocard,

My apologies. I seem to have been wasting everyones time. 

I tried your latest suggestions but with no success.

So I resized my 60GB Xubuntu partition down to 50GB and used the freed up 10GB for a fresh install of Xubuntu to the new 10GB partition (called Xubuntu2)

Lo and behold, by following Taz's original instructions there were no problems setting up the samba network share in the fresh installation. So something is amiss in my original installation. 

I doubt I have the ability to track down what's causing the problem so it looks like I might just increase the size of my new 10 GB partition and gradually migrate to it from the old partition.

Crude, I know. But it gets the job done which is the main thing.

Again, apologies for wasting your (and Taz's) time.

Regards
Miguel

---

### Post by foxy123 on 2006-12-20
> **Miguellint said:**
> Hello again reacocard,

My apologies. I seem to have been wasting everyones time. 

I tried your latest suggestions but with no success.

So I resized my 60GB Xubuntu partition down to 50GB and used the freed up 10GB for a fresh install of Xubuntu to the new 10GB partition (called Xubuntu2)

Lo and behold, by following Taz's original instructions there were no problems setting up the samba network share in the fresh installation. So something is amiss in my original installation. 

I doubt I have the ability to track down what's causing the problem so it looks like I might just increase the size of my new 10 GB partition and gradually migrate to it from the old partition.

Crude, I know. But it gets the job done which is the main thing.

Again, apologies for wasting your (and Taz's) time.

Regards
Miguel
I had a similar problem but then it was gone. I am not sure that I did much for that. I remeber creating another dir in /media but have never used it as /media/network started to work fine.

Try to uninstall all the fuse stuff and do it again. Might help.

---

### Post by Tazix on 2006-12-26
> **Miguellint said:**
> Hello again reacocard,

So I resized my 60GB Xubuntu partition down to 50GB and used the freed up 10GB for a fresh install of Xubuntu to the new 10GB partition (called Xubuntu2)

Lo and behold, by following Taz's original instructions there were no problems setting up the samba network share in the fresh installation. So something is amiss in my original installation. 

Sorry for the long time to reply.  Busy Holliday Season for me this year. :)

It sounds like something was forcing security permissions on your original install...  Like an SELinux install option (Not sure if Xubuntu has this... haven't done an install in a while).  But the point is...  It looks like some security app (whether installed durring or after your original install) was overridding any permissions that you were trying to set.

Glad it worked for you on a fresh install, though. ;)

-Taz

---

### Post by faby on 2007-01-03
Hi All,
quickly...
- tried the "Tazix How to"...: every step ok....
- tried the "EatMorePie trick to avoid installing Samba"..: found problems...
1) trying to use the command "chgrp fuse /dev/fusesmb" I don't find any "fusesmb" file under /dev directory; there is only a "fuse" file....; 
- found the "fusesmb" file under /usr/bin/ directory together at "fusesmb.cache" and "fusermount" files...
...lost in Linux space....any idea??

best regards...
faby

---

### Post by bbuz on 2007-01-03
hello everyone

Im a newbie in ubuntu/xubuntu and im stuck in this:](*,) 

> **Tazix said:**
> 
7) In XFCE Applications -> Settings -> Autostarted Applications... Add an application... name and describe as you wish... for command line, put: fusesmb /media/network (Or whatever mountoint you created).




it returns me an error:  Error writting the file autostart/(mynamedescription).desktop  ( the original error message is in portuguese ->  "Falha ao escrever ficheiro autostart/ddd.desktop" where ddd is the name that i gave for the service name)

I believe its because i am not the root user, but no password is asked. How can i run xfce as root in order to alter or create the file ? Can i add this autostarted app by terminal in order to use the sudo thing?

This must be a simple thing but :-k  im a noob

cheers

---

### Post by bbuz on 2007-01-03
:)  SOLVED

Created a new user with admin privileges and added the app .. i really dont know whats wrong with my default  user.. but its done . 

cheers

---

### Post by DeprecatedBehaviour on 2007-01-06
This guide is exactly what I was looking for, but I am having an issue.

Everything seems to work fine, the mount point contains the workgroups, which in turn contains the servers, and the shares (ie. "/media/network/WORKGROUP/DANGERMOUSE/MUSIC (M)" exists) and I can browse this structure to that point, but as soon as I try to open the share (MUSIC in the above example) I get a dialog box saying
> Failed to open directory "MUSIC"
Connection timed out.
from Thunar, or from the command line
```
$ ls /media/network/WORKGROUP/DANGERMOUSE/MUSIC\ \(M\)/
ls: /media/network/WORKGROUP/DANGERMOUSE/MUSIC (M)/: Connection timed out
```

This is only a problem when accessing shares on the windows box in the network, accessing my local (samba) shares through this works perfectly. I'm 99.9% sure the windows shares aren't password protected (and it doesn't sound like a permissions problem anyway, but I could be wrong).

I've searched but can't seem to find anything useful. Has anyone else run into this, and found a cause and/or solution?

Note: I am actually using Ubuntu 6.10, not Xubuntu, but I use XFCE as my desktop. Not sure if this has any impact.

---

### Post by Tazix on 2007-01-11
> **DeprecatedBehaviour said:**
> Note: I am actually using Ubuntu 6.10, not Xubuntu, but I use XFCE as my desktop. Not sure if this has any impact.

Hmm... since I haven't run into this... the only thing I can say is, yes, possibly it's something quirky with Ubuntu running the XFCE desktop instead of using pure Xubuntu.  Miguellint reinstalled his Xubuntu and his problems went away.

Probably not the answer you want to hear, but I have no way of re-creating your situation since I don't run Gnome-Ubuntu at all.

You might try that fusesmb.cache command that Sawjew posted in this thread.

I really wish a Xubuntu dev would pipe in, here.  My Linux knowledge is mediocre... above newbie, but far from guru. ;)

-Taz

---

### Post by sawjew on 2007-01-12
I have had a similar problem and it seems to have resolved itself now.  I don't think that using it on ubuntu is a problem as I had it working on a standard install of ubuntu edgy with no problems, I just used nautilus instead of thunar and it is much faster and easier than nautilus's samba browser.

I think I found that if I went to the windows pc first and accessed my ubuntu pc then the network worked fine after that.  I had this problem but I am no longer having it and I am not exactly sure why.  Sorry I can't help any more.

---

### Post by cowlip on 2007-01-25
great howto :)  i agree it should be default, I wasn't going to use thunar until I found this, because smb support is essential to me..

---

### Post by Tazix on 2007-02-04
Well... on a fresh installation on another machine... I ran into the same issue as Miguellint did.

Not exactly sure what is causing it.... but after several attempts of recreating directories in /media, manually running fusesmb /media/network in the terminal... what seemed to fix it was removing from autostarted applications... then a  sudo fusesmb /media/network, then a reboot, then a discovery that the fuse permission needed to be redone (step 5) because it was no longer checked off, another reboot after fixing that, and then another manual fusesmb /media/network (no sudo this time).   Once working the command can be added back to autostarted applications (step 7).

I also found after that after I got it working.... /media/ was root owner and 777, but /network/ was myself as owner and 755. I'm pretty sure fusesmb sets that on the fly, because when I tried the sudo fusesmb command... I couldn't get in the directory as myself... had to look at it "as root".  Maybe adding a chown step 6.5 would be in order to help get the thing working. Example: Step  6.5 chown yourusername:yourusername /media/network

Anyway... the whole point is.... double check that step 5 took... you may have to fiddle around manually a few times, with a few reboots to get it to show step 5 didn't take.  It must be some sort of PAM glitch or something.  But it is repairable.

Hope that helps,

Taz

---

### Post by rjz35 on 2007-02-07
perfect thanks very much, this was the only reason to make still use of nautilus

---

### Post by TomFumb on 2007-02-17
Thanks for the great howto, I just have one question which I'm afraid might be more about xp than xubuntu - 

2 of the 3 computers on my network show up in mshome, but not the xp one that I'm really interested in seeing. The computer has a simple one-word name, similar description, is on the same workgroup, etc. I can see it fine from another xp computer.

Does anyone know why it doesn't show up in thunar? ( I can mount it just fine using mount //192..... )

Again, sorry for asking an xp-based question, but I figure you guys might have the most experience with this kind of problem

---

### Post by zek725 on 2007-02-17
> **TomFumb said:**
> Thanks for the great howto, I just have one question which I'm afraid might be more about xp than xubuntu - 

2 of the 3 computers on my network show up in mshome, but not the xp one that I'm really interested in seeing. The computer has a simple one-word name, similar description, is on the same workgroup, etc. I can see it fine from another xp computer.

Does anyone know why it doesn't show up in thunar? ( I can mount it just fine using mount //192..... )

Again, sorry for asking an xp-based question, but I figure you guys might have the most experience with this kind of problem

try ```
fusesmb.cache
``` then wait till it shows up.

---

### Post by TomFumb on 2007-02-17
thanks, I wrote that post just after trying fusesmb.cache, and came up with nothing, but then I left it for a while, and now everything's showing up fine

cheers

---

### Post by adam0509 on 2007-02-17
Hi,


Personnaly I use "LinNeighborhood" for XFCE, it roxx !!


```
$ sudo apt-get install linneighborhood smbfs samba
$ sudo chmod u+x /usr/bin/smbmnt
$ sudo chmod u+s /usr/bin/smbmnt
$ sudo chmod u+x /usr/bin/smbumount
$ sudo chmod u+s /usr/bin/smbumount

```

---

### Post by foxy123 on 2007-02-17
recently my Windows desktop stop appearing in the network folder. I can still access it through its ip address, but not through fusefs. I do not remember that I have changed anything eithe rin Windows nor in my Ubuntu network settings.

---

### Post by Not-very-wise-monkey on 2007-02-18
I currently have the same problem that Tazix and Miguellint have seen (I can browser machines but opening an actual share gives the connection timed out error).

It takes about 1minute for the error to come up after clicking on a share so I don't really believe it has timed out as this should be ample time.

I have fiddled around with things as Tazix explains but that has not helped me.  I too have notied that the owner and permissions on /media/network is being changed to me as the owner with only read permissions for all others.  This occurs when fusesmb is running, however started.

Any further ideas anyone?

Also another issue I have is that when I try to connect to the Xubuntu share (setup in the Shared Folders app) from my XP box I am prompted to login.  Whatever username and password I give it always fails so I cannot connect to the Xubuntu shares either.  The shared folder has been setup with 777 permissions.  I am sure this one is something stupid that I am missing - please enlighten me.

Appreciated
Monkey

---

### Post by sgla1 on 2007-02-18
I hate to be negative but I don't think any solution that requires a permanent mount of a windows share gives you the same network browsing ability native to both konqueror and nautilus.

Permanently mounting a share gives you fast access to that share only (you can use fuse or "mount -t smbfs").  As a sysadmin in a busy heterogeneous environment I need to do ad-hoc browsing of numerous windows shares.  So I need a client that will accept a unc path, a username and a password.  Yes, I am talking about a front end for smbclient, and yes, I can and often do use the terminal client.  But sometimes it's nice to have the graphic file mgr so that you can see what you are doing.

I hope that in the future the thunar developers will consider building in support for smb and ssh/sftp.  That would make xfce complete, imho.

Cheers, Steve

---

### Post by Tazix on 2007-02-19
> **Not-very-wise-monkey said:**
> Also another issue I have is that when I try to connect to the Xubuntu share (setup in the Shared Folders app) from my XP box I am prompted to login.  Whatever username and password I give it always fails so I cannot connect to the Xubuntu shares either.  The shared folder has been setup with 777 permissions.  I am sure this one is something stupid that I am missing - please enlighten me.

Well.. I can help you with that part.

If you don't want a user and password at all:
---------------------------------------------------

Open a terminal and:
sudo mousepad /etc/samba/smb.conf

change the line:
security = USER (Or whatever)
to:
security = SHARE

Then look for your share section and make sure it has these lines:
[share name]
path =/path/of/share
read only = no
guest ok = yes

That should let you in your Xubuntu's shares from Windows without needing a user and password.

------

If you want to keep a user / password thing going
---------------------------------------------------------

You need to add samba users.  Samba doesn't use native linux accounts... it has it's own accounts.

So, you need to open a terminal and do:
sudo smbpasswd -a USERNAME

It will prompt you for a password.

Then from windows... you use the samba user and password you just created.

Hope that helps,

-Taz

---

### Post by foxy123 on 2007-02-20
> **foxy123 said:**
> recently my Windows desktop stop appearing in the network folder. I can still access it through its ip address, but not through fusefs. I do not remember that I have changed anything eithe rin Windows nor in my Ubuntu network settings.

Actually none of my Windows shares appear in the network folder, while Linux samba shares appear all right. I wonder why it is happening...

---

### Post by blisteringblue on 2007-03-01
Just posting a big thanks to Tazix for your excellent "HOW TO" for xubuntu network browsing.

Worked a treat and was just what I was after.  I'm a complete noob to Linux but am an IT specialist so it's something to get my teeth into.  I wanted quick access to a Buffalo Linkstation shared network drive on my own network.  It was really bugging me as I have a simple workgroup with open permissions but I just couldn't get xubuntu to connect to the shares.  I now have the network folder in Thunar !!

So thats not bad in 2 days Ubuntu !!  I've got my wireless USB adapter working and now network shares working !!

Next week the world .......... :lolflag:

---

### Post by SBFC on 2007-03-03
Just curious as to what your solution is for shares that require a specific username password. The windows boxes show up fine, but I get an access denied to my linux share due to it having to authenticate.

Anyway to have a prompt?

Should also add that I'm perfectly fine mounting password required shares with linneighborhood (which I currently am). Was just wondering if there was a way to access password shares via thunar...cause the thunar method is damn nice.

---

### Post by reacocard on 2007-03-03
> **SBFC said:**
> Just curious as to what your solution is for shares that require a specific username password. The windows boxes show up fine, but I get an access denied to my linux share due to it having to authenticate.

Anyway to have a prompt?

Should also add that I'm perfectly fine mounting password required shares with linneighborhood (which I currently am). Was just wondering if there was a way to access password shares via thunar...cause the thunar method is damn nice.

No dialogs, but you can set up passwords manually in ~/.smb/fusesmb.conf

---

### Post by Tazix on 2007-03-04
More on the fuse and /network/media access denied issue...

Just did a fresh install edgy on my old laptop.

I purposely did a couple extra steps to ensure that it would work.

Step 6.5) In a terminal, type: sudo chown <username>:fuse /media/network
(Where <username> is your user account logon name)
Step 6.6) Double check that the permission to use fuse took. Applications -> System -> Users and Groups... Manage Groups... find fuse and choose properties.  Make sure your user name account is in that group and check-marked.
Step 6.7) Reboot the system and triple check with step 6.6

Oh... and this is all done on a non-updated Xubuntu Edgy.  I don't know if the problem has been a glitch all along, or if it's a glitch introduced with some package that is updated.

Hope that helps,

Taz

---

### Post by foxy123 on 2007-03-04
I've got a strange problem. I have set up fusesmb on Feisty and it seems ok. But quite often when I am copying something from the network it fails and /media/network folder disappear. I have to reboot to get it back. I tried:
```
fusesmb /media/network
fuse: bad mount point `/media/network': Transport endpoint is not connected

```
and
```
/media$ ls -l
total 4
lrwxrwxrwx 1 root root    6 2007-03-04 14:46 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-03-04 14:46 cdrom0
?--------- ? ?    ?       ?                ? network

```

I have no idea what is going on :(

---

### Post by Tazix on 2007-03-07
> **foxy123 said:**
> I've got a strange problem. I have set up fusesmb on Feisty and it seems ok. But quite often when I am copying something from the network it fails and /media/network folder disappear. I have to reboot to get it back. I tried:
```
fusesmb /media/network
fuse: bad mount point `/media/network': Transport endpoint is not connected

```
and
```
/media$ ls -l
total 4
lrwxrwxrwx 1 root root    6 2007-03-04 14:46 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-03-04 14:46 cdrom0
?--------- ? ?    ?       ?                ? network

```

I have no idea what is going on :(

Looks sort of like what happened to me when I tried installing it on my second Edgy Machine.

Try sudo ls -l

It's like the directory gets locked up by root somehow.

Then you need to unload fusesmb, delete the /network directory (with sudo), recreate it, change permissions and ownership, then reload fusesmb.  Make sure that your user account is in the fuse group.  Sometimes it takes a few tries before the settings stick.

Something wonky goes on and settings don't stick on certain machines sometimes.  I have no clue why.  The 1st and 3rd machines I tried it on, I had no issues.  But my second machine took several attempts before it worked right.

Hope that helps,

Taz

---

### Post by tabako on 2007-03-09
Hi,

I have some curious problem. I tried to do this succesfully some days ago, but yesterday I reinstalled Xubuntu on my laptop and now I can't install "fusesmb", simply because it doesn't appears in the synaptic package manager. There's only a "fuse-utils"... So I can't neither use the "fusesmb" command in terminal.

Any idea how to solve this?

Thank you!

---

### Post by reacocard on 2007-03-11
> **tabako said:**
> Hi,

I have some curious problem. I tried to do this succesfully some days ago, but yesterday I reinstalled Xubuntu on my laptop and now I can't install "fusesmb", simply because it doesn't appears in the synaptic package manager. There's only a "fuse-utils"... So I can't neither use the "fusesmb" command in terminal.

Any idea how to solve this?

Thank you!

Try enabling the universe repository.

---

### Post by tabako on 2007-03-12
Well, I re-installed the universe repository (it was installed yet, but some things were missing :confused: ) . I installed the fusesmb package but i can't access the network anyway. Is there some method to check the connection or something? I can't connect neither to the other computer by it's IP... I don't know what to do, it was really much easyer with Ubuntu and Nautilus :(

I reinstalled the Windows on the other computer too, it's maybe some additional config in windows that I'm forgetting to do? 

I remember that the last time, after configuring samba etc... I had a samba console on settings or accesories, but there isn't now, is it possible that there is something wrong with the samba installation, or even with Xubuntu install...?

---

### Post by foxy123 on 2007-03-14
I've got another problem. I can see shares in my /media/network/WORKGROUP/MYPC but I can access them. When I click on any share I've got:
```
Failed to open directory "diskl".
Connection timed out.
```
I can mount the shares with LinNeighborhood without any problem.

---

### Post by mw99 on 2007-03-15
Thanks Tazix for the excellent how-to! Got my machine (Xubuntu Edgy connecting to Thecus N2100 NAS) working very quickly for the first user. The problems came when setting up other users on the same PC trying to mount the same /media/network share - maybe this sheds some light on the permissions problems seen by others....

Just using an autostart '**fusesmb /media/network**' for each user I'd get problems:
1) 1st user logs in, accesses share OK, logs out.
2) 2nd user logs in. Share completely disappeared in Thunar. From console 
```
/media$ ls -l
<entries removed>
?--------- ? ?    ?       ?                ? network
```
as seen elsewhere. Also
```
/media$ cat /etc/mtab
<entries removed>
fusesmb /media/network fuse rw,nosuid,nodev,allow_other,max_read=32768,user=**1st_user** 0 0
```

Basically the mount is persisting after the user who created it logs out, so the directory permissions of the mount look screwed to the next user who logs in. To work around this, I tried reacocard's trick and changed the autostart for each user to '**fusesmb /media/network -o allow_other**' and also created the file /etc/fuse.conf
```
/media$ cat /etc/fuse.conf
user_allow_other
```

Starting again with a re-created /media/network, everything is fine as subsequent users logging in get to reuse the first user's mount, which is OK until I want to mount shares with restricted access. As per EatMorePie I've given each user a ~/.smb/fusesmb.conf 
```
[global]
username=YourSMBUsername
password=YourSMBPassword
```

So now:
1) 1st user logs in, accesses share OK (including their private directories), logs out.
2) 2nd user logs in. Inherits first user's mount including credentials!! Can access first user's private directories, but can't access their own! Oops!

As a workaround, I've changed the autostart for each user to '**fusesmb /media/network -o allow_other,nonempty**'. This has the effect of forcing a new mount with the correct credentials as each user logs in. It's good enough to use at home the stop the kids accidentally deleting work I'm trying to protect on my Raid1 NAS. It is obviously not good security though, as it relies on the next user to play nice and replace the previous user's mount..... 

Any ideas how to tear down the mount at logout? Do I need to add a script somewhere with '**fusesmb /media/network -o hard_remove**'?

The other side effect, which may or may not be a problem, is that /etc/mtab ends up like this:
```
/media$ cat /etc/mtab
<entries removed>
fusesmb /media/network use rw,nosuid,nodev,allow_other,max_read=32768,user=**1st_login** 0 0
fusesmb /media/network fuse rw,nosuid,nodev,allow_other,max_read=32768,user=**2nd_login** 0 0
fusesmb /media/network fuse rw,nosuid,nodev,allow_other,max_read=32768,user=**3rd_login** 0 0
<...etc>
```

For each entry in /etc/mtab there is still a live fusesmb process, belonging to whichever user's autostart created it. Of course a reboot cleans up all the processes and associated mtab entries. So maybe the question should be, is there a better way to launch fusesmb instead of autostart, so that the process gets killed automatically at logout?

Any suggestions for a more elegant multi-user PC setup much appreciated:)

---

### Post by mw99 on 2007-03-15
I can partly answer my own questions:

"Bug 2382 - Request - Add ability to kill processes at xfce shutdown" at [http://bugzilla.xfce.org/show_bug.cgi?id=2382](http://bugzilla.xfce.org/show_bug.cgi?id=2382) suggests there's no easy way to kill the fusesmb processes when the xfce session ends.

The author states "I know this can be done easily by editing $HOME/.xinitrc (and that works fine for now), but it would be nice to have this ability inside xfce." Any script writers out there know how to run fusesmb from inside .xinitrc instead of using xfce autostart?

---

### Post by SBFC on 2007-03-19
Well, I had this working, now it's acting a lil fishy. 

When the 'fusesmb /media/network/ command is run, the permissions/ownership for /media/network change.

It goes from 

```
drwxrwxrwx 2 root fuse 4096 2007-03-19 01:53 network
``` 

while fusesmb isn't running. And when it is running it changes to

```
drwxr-xr-x 3 oblivion oblivion 4096 2007-03-19 01:45 network
```

As soon as I kill the fusesmb process it goes back to the first listing.

Thing is, I didn't even restart or anything, it was working, showing shares, and then just switched. I've tried deleting it/remaking/restarting.

Anyone else seen this? As it stands I can no longer view shares with its current behavior.

---

### Post by dannyboy79 on 2007-03-19
i use xsmbrowser in Dapper Xubuntu, it allows you to mount stuff and make it be owned by a certain user and group also.

you need to start xsmbrowser as root though.

gksudo xsmbrowser

and then you're off. you do need to have samba setup though.

---

### Post by SBFC on 2007-03-19
Well, currently I'm using LinNeighborhood to browse/mount shares. Was just hoping to get the Thunar method working again since it allows me to be much lazier. Log in, shares are there. :P

---

### Post by SBFC on 2007-03-19
Now I'm really confused. Shares are showing up in Thunar now, didn't change anything though. Even while mounting/browsing shares with LinNeighborhood they wouldn't show up via fuse. 

Any chance that fuse just takes a while to notice things?

Meh. Long as it's working.

---

### Post by klytu on 2007-03-25
I just started experimenting with Xubuntu. While looking for a way to easily browse network shares, I found this great HowTo.

Another way to browse network shares without mounting them is to use Midnight Commander (mc). It's kind of old school, but since it's text console based it can work no matter what version of Ubuntu is being used; and it can be used in a pinch if you can't access your shares with Thunar for some reason. mc is in the Dapper repositories and it's a fast file manager similar to the DOS app Norton Commander. Once it's installed, just type mc in a terminal to use it. To browse the network, click on either left or right, then select SMB link in the context menu that drops down. Then enter the networked computer's name, username, and password  (if applicable - if you don't use a password, just leave it blank) and then you should be able to browse that computer's shared folders.

mc can also be used to work with FTP folders.

---

### Post by yesdup on 2007-03-28
Hi all,

Is there any way of makeing this work with more than one administrative user.

i added a desktop user and added them to the fuse group and also gave permision to use use fuse under user-properties. but when i browse to the "/media/networt" it doesn't appear it seems to have dissapeared but under my account it works fine. 

Puzzled, stumped, confused.

Tahnks

---

### Post by wilberfan on 2007-04-01
Cool thread.

I haven't spent much time with Xubuntu, but how to connect to the network was corn-fusin' the crap out of me!

I've got Feisty loaded with gnome and xfce...  Time to start gettin' to know that little mouse now!

---

### Post by neorou on 2007-04-02
So this seems to work if I have Windows. Unfortunately for me, I have Mac OS X (running version 10.4.9). I haven't been able to get XUBUNTU to share with it, and have been surviving with ftp all this time.

I turned on Windows sharing, and although running smbclient -L 192.168.1.x -U% lets me list the servers, it doesn't let me  see the shared directory, only shared printer and the IPC shares. 

You don't happen to know how to get the Mac side make its share 'more' visible to the more fully-compliant XUBUNTU machine do you? Does anybody know a solution for me?

:confused:

---

### Post by detyabozhye on 2007-04-03
Um, OS X should support NFS if I'm not mistaken.

---

### Post by DJiNN on 2007-04-04
WOW!! I can't believe this. What a great thread & How-To!! Thanks a million. This was the one thing that has stopped me (For over a year now) using XFCE as my WM. I've always deferred back to Gnome because Nautilus just copes so much better.... UNTIL NOW!! :)

It works great on my network, accessing both Win machines & Linux as well.  I'm running the Xubuntu Feisty Beta. 

One thing i will also say, with regards to what someone mentioned earlier about using "Midnight Commander" with Network shares etc.  If you set your Xubuntu machine up to do this anyway (As in this How-To) then fire up MC, you can just access all your shares in the same way as you would with Thunar, but with a Dual Pane FM, and it seems to be a lot faster & more responsive than Thunar. :)

Anyway, way cool, & it's totally changed the way that i use my OS. I can now use XFCE across my Network!! Fantastic. :)

---

### Post by dannyboy79 on 2007-04-05
> **neorou said:**
> So this seems to work if I have Windows. Unfortunately for me, I have Mac OS X (running version 10.4.9). I haven't been able to get XUBUNTU to share with it, and have been surviving with ftp all this time.

I turned on Windows sharing, and although running smbclient -L 192.168.1.x -U% lets me list the servers, it doesn't let me  see the shared directory, only shared printer and the IPC shares. 

You don't happen to know how to get the Mac side make its share 'more' visible to the more fully-compliant XUBUNTU machine do you? Does anybody know a solution for me?

:confused:

yes, osx has an option under system preferences, either network or sharing, you need to  enable "windows sharing" which basically is going to open the ports neccessary to get netbios over tcp/ip and samba to work properly, if i remember correctly. but I also believe there is  "personal file sharing", which I think is different because it doesn't open ports 445/139 which is for name resolution. I forget? Don't you also have to share a certain folder as well? 

I found this also within gogle. It's about Horay but it should still apply.

This post is for those of you who are looking to connect an OS X box to your Ubuntu box set up as a file server or just share files between the two. I figured I would share my success story because there is bound to be someone else out there that would like this information. This process is rather easy and takes just a little time to get up and going. It took me about 20-25 minutes to complete.

First, make sure you have samba installed on your Ubuntu system. Then, locate a directory you would like to be the share point for the OS X box to access.
1. Right-click the directory
2. Click on "Share folder"
3. Enter your password
4. Select "SMB" (if not already) in the drop-down list box labeled, "Share with:"
5. Give a name in the text box labeled, "Name:"
6. Add comments about this share point (optional)
7. Click on the check box labeled, "Read only" if you want this folder to be read only to those who may access the folder. Otherwise, leave it unchecked so that users may write files to the directory for sharing.
8. Click on the check box labeled, "Allow browsing folder" so that the users may look inside (unless you do not want them to)
9. Click OK

Note that in the file sharing dialog above there was a button labeled something like, "Windows sharing information." Explore these options to share files with Windows boxes.

Now, we move along to the OS X box.

First, we will set up file sharing and then we will connect to Ubuntu.
1. Go to the System Preferences (usually, Apple->System Preferences...)
2. Click on the Sharing folder in the Internet & Network section
3. Check the box next to Personal File Sharing and Personal File Sharing will turn on. This may take a few seconds.
4. Go back to the main System Preferences screen (usually by clicking on the "Show All" button in the upper left corner of the window.)
5. Click on the Network icon (it should be close to the Sharing Folder)
6. Make sure "Network Status" is selected in the drop-down list box next to "Show:" at the top of the window.
7. Verify that you are connected to the same network as the Ubuntu box and have a valid IP address (usually indicated by a green light to the left of the adapter)
8. Close out of System Preferences

Now, go to the desktop and we are ready to connect to Ubuntu.

1. Click on the "Go" menu in the menu bar (if it doesn't appear, click on the desktop in empty space and it should appear.)
2. Click on "Connect to Server..."
3. In the "Server Address:" text box, type the connection string in this format: "smb://<Ubuntu box hostname>/<path to share directory>" (without quotes)****
**** <Ubuntu box hostname> should be the host name for your Ubuntu box (UBUNTU by default) and <path to share directory> should be the path to the share directory on the Ubuntu box as you would navigate to it from the root or "/" directory.

Example Server Address: smb://UBUNTU/home/sharefolder

Once you have the proper server address typed in, you can click the button with the "+" symbol on it to save the address for later use. Then, you are ready to connect. Click on the button labeled, "Connect" and OS X will attempt the connection. If everything is configured properly, you should get a window asking for "SMB/CIFS Filesystem Authentication." If you require network users to access the Ubuntu box, this is where you type in the username and password. I do not require this, since I am the only one accessing the file server. If you do not require username and password, make both of those text boxes blank. Then, click OK and OS X will mount the network volume.

Now, you can share files between your Ubuntu box and your OS X box. I hope this is of some use to someone. Thanks!

---

### Post by neorou on 2007-04-05
Thanks, dannyboy79. You helped me out. The UBUNTU IS WITH YOU!:)

---

### Post by cyberdonaldson on 2007-04-21
Thanks a million!  This has been a great help.  Fuse with Thunar makes life in Xubuntu alot easier.

---

### Post by katon on 2007-05-12
GREAT work,
thank you very much

---

### Post by j0217995 on 2007-05-26
Great how-to, thanks for the write up on this.  Great job

---

### Post by sataylor56 on 2007-06-15
This thread has been a great help. I have struggled with a Kubuntu installation previously and gave up because I was having so much trouble with network access. I switched to Xandros where networking just simply works, right out of the box, as they say.

I now have an old Celeron 433 system with 512M with a new 500G hard drive. I am trying to make it a low powered music server running SlimServer from SlimDevices and one of their SqeezeBoxes to feed my stereo. Xandros runs way too slowly on this system. Now I have installed Xubuntu Fiesty 7.04 and now have Thunar set up to browse the network.  That part is working fine. When I installed Xubuntu, it wouldn't let me partition the drive beyond 130G so I ran QtParted from the Gentoo system on the System Rescue Diisk, and created another 400G partition. That partition I now have mounted in a music directory under /home. I also installed Samba and it is running. I can see my music directory shared through Samba from my networked Windows 2000 computer. The trouble is when I try to copy anything from the Windows computer to the music directory, it copies a couple files and then hangs. If I then use Thunar to try to look at the music directory, it also hangs. When I try to reboot the Xubuntu computer, it won't shutdown, I have to pull the plug on it. Then when rebooting, it says that the file system on the 400G partition is corrupt. After rebooting, I can again access the music directory and I then see that it stopped copying in the middle of the third file. If I copy the files using Thunar's network access method, the files copy fine. What could make accessing the computer from the network using Samba corrupt my directory?

---

### Post by dannyboy79 on 2007-06-15
Not sure about the partitioning thing as that's never happened to me?? That's obviously not suppose to be that way!

So you're saying that you're running a Samba Server within Xubuntu, then when you're sitting at your Win2000 desk, you open "network computer" (or whatever that icon is) then you also open another Windows Explorer window, then you select some stuff (going TO windows or going FROM windows?) and you drag it and paste it into the opposite of what your answer was to the question in parenthesis, then after a certain file (does it only do it on this 1 file, or any file that the same size, or at different times?) your Xubuntu machine is completly frozen and you can't even do anything? AND the only way to shut it off is by pulling the plug? you can't even just hit the power buton or reset button? what about holding the PWR button in? Huh? I am not sure what to tell you, I have Xubuntu Feisty and a WinXP Pro machine and have transferred it's entire contents to back it up (almost 10gb) and it completes the transfer for me. Pretty decently too, it averaged out to what it should be over a 100mb network (MAX is 12.5megabytes/sec but due to overhead and other network activity, I get around 8megabytes/sec)
Take a look here: [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/Other-Clients.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/Other-Clients.html)
and see if there's any mention about Win2000 optimizations that you can do.

Well what fusesmb does is actually mount's the data within your local system (poor explaination but I don't know how else to explain it) and when you do samba browsing, you're using other stuff along with the smb protocol I believe. that's my only guess??

---

### Post by sataylor56 on 2007-06-15
This happens when I am trying to copy files from the Windows computer to the Xubuntu system. I have been able to copy files from my Windows computer to other Linux systems just fine. The copying just stops and on Xubuntu when I try to access the directory, the Thunar window is open with the wait cursor going around and around. I can close Thunar but when I try to shutdown the computer, I get the blue splash screen and then it just sits there. This computer is an embedded system from some Xerox machine so it has no power switch or reset button, so it's just pull the plug time when this happens. I have since copied about 37G of music files onto it so I am a little hesitant to experiment with it since I don't want to corrupt the directory now. I have another system just like it, maybe I'll start over from scratch on that one and see what happens.

---

### Post by atiu on 2007-06-17
I am encountering problems under Xubuntu 7.04.  I am able to browse and open the files shares on WIFI connection without problems, but on wired lan, I am unable to open the shares/folders.  The workgroup and share names are shown but once I try to open the folder, it says "unable to open" after it times out in a few seconds.

I've followed the instruction and tried a fresh install without luck.  Any help will be highly appreciated.

Albert

---

### Post by atiu on 2007-06-18
I have somehow narrowed down the problem to the router.  On the wired network, I used a Dlink router configured with DHCP while on the WIFI, I used a Linksys with DD-WRT firmware.  These are two different and separate network.  

After I replacing the Dlink router with a similar linksys router with DD-WRT firmware, fusesmb now works both on wired and wireless network. I am not sure how the Dlink router affected fusesmb function, unable to open the folders and see the files.

---

### Post by dannyboy79 on 2007-06-18
> **atiu said:**
> I am encountering problems under Xubuntu 7.04.  I am able to browse and open the files shares on WIFI connection without problems, but on wired lan, I am unable to open the shares/folders.  The workgroup and share names are shown but once I try to open the folder, it says "unable to open" after it times out in a few seconds.

I've followed the instruction and tried a fresh install without luck.  Any help will be highly appreciated.

Albert

viewing samba shares using Gnome-VFS and many other techniques has always been flakey. I would strongly suggest just mounting the share locally within a folder using CIFS and I gurantee you won't get the unable to open error. here's a guide for mounting windows shares with cifs:
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

you don't need to install winbind and what not, you can always just use the IP address instead of the netbios name, if you can already ping the machine by hostname/netbios name, then you CAN use the netbios name when mounting with CIFS. good luck.

---

### Post by atiu on 2007-06-19
Since I got fusesmb to work with a different router, I'm fine with this solution for now.  However, I am just wondering how the router affects fusesmb browsing.

Albert

---

### Post by dannyboy79 on 2007-06-19
you could always browse the settings of each of the routers and see what may be different. I know that some routers can have their MTU changed, I think that has to do with wireless though. Also, is it possible that the routers cache is larger on one than the other? I don't know just throwing out ideas.

---

### Post by Steve1961 on 2007-07-01
I'd just like to say a big thank you for this how to.  I've been using Ubuntu since Hoary but I've stayed away from XFCE until now because access to samba shares on my network is essential.  Anyway, just got hold of an old laptop and decided to install Xubuntu.  I then followed this how to and I now have seamless access to all the shares on my network.  Great work, and again, many thanks.

---

### Post by reset3x on 2007-07-19
Great thread!!!

I _was_ having problems with this breaking and not having the shares show up after rebooting my PC's. I've found that assigning static IP's to the effected systems works great. Using DHCP seems to hose everything for me....

---

### Post by gundamb2 on 2007-07-20
I can access the Xubuntu's Share Folder from my Windows XP PC, but how can I get Xubuntu to be able to access my Windows XP's share folder?

---

### Post by ugm6hr on 2007-07-21
> **gundamb2 said:**
> I can access the Xubuntu's Share Folder from my Windows XP PC, but how can I get Xubuntu to be able to access my Windows XP's share folder?

This worked for me.... not ideal, but easy to do!

[http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)

---

### Post by SQuark on 2007-07-21
I had the same problem as so many others (owner and permissions changing after running fusesmb). What finally fixed it for me was either one or both of these steps:
[LIST]
[*]renaming the /media/network directory to /media/lan
[*]finding a .hal-mtab and a .hal-mtab-lock file in /media and deleting them
[/LIST]
I hope this post may help others.

Cheers!

---

### Post by Fraoch on 2007-08-10
I'm looking for a method which will allow network shares to be mounted *temporarily*.  Not all my machines are up at the same time, and if anyone's ever tried this, there are huge problems when you try to access the directory where the remote mount point is.

It won't display the directory until it communicates with the remote directory, which it can't, so the directory never comes up, killing off your GUI file browsing capability altogether (including all local files).

I remember having some tense moments trying to recover from this scary situation on both my Ubuntu machines, but now my Xubuntu machine is locked in this and I can't unmount even with -force, after a minute or so I get an I/O error.  Hope I can recover...

If I can recover, I won't do any network browsing until I can find something that will allow me to temporarily browse network shares, like "Places - Network" in Ubuntu.  If it doesn't find anything, it still displays, it just doesn't display the share.

Incidentally I was never able to get fuse working, I encountered the permissions issue so many have in this thread.  LinNeighborhood worked great though, but now I have dead mounts which have screwed up Thunar completely...

Also a tip I found - in order to get fuse working you need smbfs.  I had the full samba, but that wasn't enough.  Once I installed smbfs in the process of installing LinNeighborhood, the fuse shares were immediately visible, I just didn't have permission to see anything in them.

---

### Post by dannyboy79 on 2007-08-10
> **Fraoch said:**
> I'm looking for a method which will allow network shares to be mounted *temporarily*.  Not all my machines are up at the same time, and if anyone's ever tried this, there are huge problems when you try to access the directory where the remote mount point is.

It won't display the directory until it communicates with the remote directory, which it can't, so the directory never comes up, killing off your GUI file browsing capability altogether (including all local files).

I remember having some tense moments trying to recover from this scary situation on both my Ubuntu machines, but now my Xubuntu machine is locked in this and I can't unmount even with -force, after a minute or so I get an I/O error.  Hope I can recover...

If I can recover, I won't do any network browsing until I can find something that will allow me to temporarily browse network shares, like "Places - Network" in Ubuntu.  If it doesn't find anything, it still displays, it just doesn't display the share.

Incidentally I was never able to get fuse working, I encountered the permissions issue so many have in this thread.  LinNeighborhood worked great though, but now I have dead mounts which have screwed up Thunar completely...

Also a tip I found - in order to get fuse working you need smbfs.  I had the full samba, but that wasn't enough.  Once I installed smbfs in the process of installing LinNeighborhood, the fuse shares were immediately visible, I just didn't have permission to see anything in them.
all you would have to do is run, 
smbtree
when it asks for a password, just hit enter (meaning don't enter one) that will display all hosts that are on and which shares they have that are guest accessible. then when you see the machine is on, you can use
smbclient -L hostname, then it asks for a password, either enter your password for that hostname or just hit enter (not entering a password will allow to see only shares that have guest access turned on), then this will display the shares that are available using that password or just the guest shares.
Just a tip, that's the only suggestion I have regarding thunar locking up on you.

---

### Post by printarg on 2007-08-29
> **detyabozhye said:**
> Awesome dude, maybe later I'll write an automated shell script for this. :D
Hi! Where's the script? :)

---

### Post by highfructose327 on 2007-08-30
Excellent thread Thanks!!

---

### Post by Sp|ke on 2007-10-18
> **reset3x said:**
> Great thread!!!

I _was_ having problems with this breaking and not having the shares show up after rebooting my PC's. I've found that assigning static IP's to the effected systems works great. Using DHCP seems to hose everything for me....

Thanks for that, it was up and down like a lady of the nights undergarments for me, assigned a static IP to the windows box and it's now solid.

S

---

### Post by robh11 on 2007-11-03
I'm a newbie to Xubuntu and my experience might be helpful.  I found the easiest way to access my network files was by clicking on 'computer'  in Accessories.  This gives me the Nautilus Gnome file manager that lets me 'go' to Network and gives me access to any computers on my network.  I don't use Thunar at all.  Very simple for someone like me that knows nothing about the innards of Linux. 

Note: I installed Ubuntu first and then added Xfce, so am not sure if a basic Xubuntu install will give you the Nautilus file manager or if you have to add it.

Running Xubuntu/Ubuntu on an8 year old Dell with 128Meg ram.  Works great!

---

### Post by nartooki on 2007-11-08
Has anyone gotten this to work on xubuntu with the share needing a password? I did a fresh install of xubuntu gutsy, did not do any updates, set my username and password in fusesmb.conf and it was working. Then I turned on automatic updates and let it update. Now I can only see the workgroup, server, and share but I cannot see inside the share. The connection times out and I think that fusesmb is ignoring the conf settings. I know the server is fine because this was working, and I can access it fine when I boot windows. Any ideas?

---

### Post by virx on 2007-11-22
Nice howto. A while ago I used nautilus because of its samba support. 

Have I done something wrong if I can see my samba share, but under workgroup I can't see any other computers but mine?

Since I don't use Xubuntu, but use Gutsy alternate install+xfce4, I don't have user account manager GUI. But i added myself to /etc/groups file:
```

fuse:x:106:virx

```

If I haven't mounted /media/network yet, then 
```

/media$ ls -la
total 52
drwxr-xr-x  7 root     root     4096 2007-11-22 19:23 .
drwxr-xr-x 21 root     root     4096 2007-10-30 20:39 ..
lrwxrwxrwx  1 root     root        6 2007-10-30 20:33 cdrom -> cdrom0
drwxr-xr-x  2 root     root     4096 2007-10-30 20:33 cdrom0
lrwxrwxrwx  1 root     root        7 2007-10-30 20:33 floppy -> floppy0
drwxr-xr-x  2 root     root     4096 2007-10-30 20:33 floppy0
drwxr-xr-x  2 root     root     4096 2007-11-11 22:24 iso
**drwxrwxrwx  2 virx     fuse     4096 2007-11-22 19:23 network**
drwxrwx---  1 root     plugdev 28672 2007-11-07 22:08 sdb1

```

After mounting I get strange "test" message:
```

/media$ fusesmb /media/network/
test

```

And permissions change too:
```

:/media$ ls -la
total 48
drwxr-xr-x  7 root     root      4096 2007-11-22 19:23 .
drwxr-xr-x 21 root     root      4096 2007-10-30 20:39 ..
lrwxrwxrwx  1 root     root         6 2007-10-30 20:33 cdrom -> cdrom0
drwxr-xr-x  2 root     root      4096 2007-10-30 20:33 cdrom0
lrwxrwxrwx  1 root     root         7 2007-10-30 20:33 floppy -> floppy0
drwxr-xr-x  2 root     root      4096 2007-10-30 20:33 floppy0
drwxr-xr-x  2 root     root      4096 2007-11-11 22:24 iso
**drwxr-xr-x  3 virx     virx  4096 2007-11-22 19:27 network**
drwxrwx---  1 root     plugdev  28672 2007-11-07 22:08 sdb1

```

Does it mean other computers cannot write themselves into that directory, since there is no permission for "fuse"?

---

### Post by virx on 2007-11-26
So I tried started from the beginning. At first undid everything at opposite order and then carefully did every step from HOWTO.

What I didn't get was any changes to fuse, but what I got was getting rid of networking configuration - I guess thanks to removing fusesmb packet and removing "fuse" fom /etc/modules (It was there before I started messing with fuse - so I should have not delete it). After reboot Got message something like: no /etc/networking/interfaces file. After recreating it:
no /etc/network/if-pre-up.d

In some strange reason I had 2 NICs in my PC, so I managed to get networking up again through the other NIC, but cannot use networking service, because of missing configuration.
ifconfig shows at eth0 (NIC i used before messing with fuse):
in last line - "Interrupt:21 Base address:0x2000"

Is there any way for recovering network settings?

EDIT: aptitude reinstall ifupdown helped.

Now I only have fuse problem, can someone give me any guidlines for seeing other computers from network directory?

---

### Post by total wormage on 2007-12-01
like so many others...

I wish to thank you very much!

I also made a launcher to fusesmb.cache in the panel, so it's really really easy to browse the network and keep mounts fresh.
huzzah! this has made my xfce experience much better.
:KS

---

### Post by j8a on 2007-12-10
I did the recipe sent by Taz and I had no problems. Xubuntu 7.10 on PIII with 550 MHz and 400 Mb RAM.

---

### Post by kishorebudha on 2007-12-29
**WORKED ON XUBUNTU 7.10. THANKS**

> **Tazix said:**
> Since Thunar doesn't have native network Browsing, here is a good way to accomplish it:

1) In XFCE's Applications -> System -> Shared Folders. (This should trigger a Samba install if you don't already have a share, and it should allow you to define the proper workgroup)

2) Install fusesmb in Synaptic (from Universe repository)

3) Edit /etc/modules and add the word 'fuse' to the modules list to be loaded (without quotes), and save the file.

4) Reboot, so the fuse module loads, and the proper workgroup is read for samba.

5) In XFCE Applications -> System -> Users and Groups... Properties of your username... User Priveleges Tab... check "Allow use of fuse file systems..."

6) Create a directory that you are going to mount your network browse to... I used /media/network. Change permissions to read / write for group and others (777).

*** 6.5) In a terminal, type: sudo chown <username>:fuse /media/network
(Where <username> is your user account logon name)

*** 6.6) Double check that the permission to use fuse took. Applications -> System -> Users and Groups... Manage Groups... find fuse and choose properties.  Make sure your user name account is in that group and check-marked.

*** 6.7) Reboot the system and triple check with step 6.6

7) In XFCE Applications -> Settings -> Autostarted Applications... Add an application... name and describe as you wish... for command line, put: fusesmb /media/network (Or whatever mountoint you created).

8) Open Thunar, and navigate to the parent folder of your mountpoint... then drag the 'mounpoint folder' to the places (shortcut) pane of thunar.

9) Logout and log back in (So the user privilege and fusesmb autostart will take affect)

*** Added steps to help prevent some access denied issues some people have been experiencing with fusesmb.

My original thread on this topic is here: [http://www.ubuntuforums.org/showthread.php?t=300310](http://www.ubuntuforums.org/showthread.php?t=300310)

I hope this helps my fellow Xubuntu users... and I also hope that the Xubuntu team somehow enables something similar by default, or at least as an install option.

-Taz

---

### Post by Shawn Reist on 2008-01-03
Hello,

I am new to Linux.. Ubuntu... I have installed Ubuntu 7.10 on my main system.. no windows .. and now installed Xubuntu 7.10 on my laptop...

laptop
---------
Panasonic CF-47 Toughbook
P3 500 
192 megs ram
40gig HD
---------

I had problems getting samba to work in Xubuntu, had to use universal repositories and reinstall samba... then followed the instructions for fusesmb... networking worked great until I shutdown the computer.

I have found that I can't run fuse in auto start since my networking is done via a PCMCIA card. so I have to start the computer and then get the network card running and then manually enter

fusesmb /media/network

to be able to browse the home network. 

I can access the Wifes XP shared directory and my Ubuntu share... but I can't access the W2k shares.](*,)

---

### Post by chatainsim on 2008-01-04
Nice !
awesome how to !
Thanks a lot :KS

---

### Post by dannyboy79 on 2008-01-04
does the W2K machine have users and passwords setup on it? Have you properly shared the folders for users or guests?

you can issue this command to see if you have any guest available shares on teh W2K machine. Enter this into a terminal session.

smbclient -L -U username hostname

Example, if there was a username on the W2K machine named joe and the W2K machine's computer name (hostname) was joescomputer.

smbclient -L -U joe joescomputer

this will prompt you for a password, if you don't enter joes password it should only show you guest available shares. If you enter joes password it should show you all shares available to joe. If you issue this command, it should at least show you which computers on the network are running windows file sharing and or samba

findsmb

or

smbtree

again, don't enter any password and see what it returns. good luck

---

### Post by Shawn Reist on 2008-01-06
Hello, thanks for the info....it is amazing the amount of info at the command prompt one can get within Linux....

findsmb

&

smbtree

-------------------
shawn@trystan:~$ smbtree
Unknown parameter encountered: "password"
Ignoring unknown parameter "password"
Password:
-------------------
I enter my user password and the computers and their shares sroll up.

I can see the computers on the network, even the print servers and hidden shares ones that I did not know about.

tried the command smbclient

shawn@trystan:~$ smbclient -L -U Shawn SLAVE
Unknown parameter encountered: "password"
Ignoring unknown parameter "password"

and I get nothing... I can get to the hidden shares from my main system which has Ubuntu 7.10 with Samba installed.  

I am thinking that I am missing something maybe a package or something not configured properly, I wil have to do some reading and looking for what packages are installed and required and where they are installed.  I do not know enough to find my way around linux. 

right now the fastest way I can transfer files from my W2k machine to my laptop is via the main system...

--------------------  additional info-------------

Wifes computer - XP
Second computer - W2k
Kids computer - W2k
main system - Ubuntu 7.10
Lap-top - Xubuntu 7.10


I just checked my sytems, My ubunto machine can see and access everythign on the network.  My lap-top can access everything except my W2k machine and the W2k & XP sytems can't access the linux shares.....

definatly more to think about .... most of the communication is just one way.

---

### Post by uatu on 2008-01-09
Important! Check that the DNS is working poperly. I could see the shares into media/network but when trying to read them I got "Timeouts" messages. After a lot of headache I realized that the IP of the  machine where the share was hosted  was wrong! 

Once I put the ip in /etc/hosts everything was fine.

---

### Post by boterbram on 2008-01-21
I can't get it to work:S

It works as long as i am root. But this is useless because i don't want to be the root all the time. 
What can i do?

EDIT::

Seemed to have it fixed now, with the .smb/fuse.conf file
[https://help.ubuntu.com/community/FuseSmb](https://help.ubuntu.com/community/FuseSmb)

EDIT2::

I thought I had it, but when I now try to open the folder directly under the hostname I get the message "not enough memory" and nothing happens. What should I do?

---

### Post by gen0 on 2008-01-27
Thanks!  Great HOWTO!

I got this working on XUbuntu 7.10 just by following the instructions in the first post of this thread.  After this, I was able to remove 'samba' via Synaptic so that I didn't have to run a samba-server on my laptop just so I could browse my samba server.

To authenticate against my password protected samba server, I just had to add these lines to ~/.smb/fusesmb.conf :
[/SERVERNAME]
username=myusername
password=mypassword

I'd love it if there was a solution that didn't force me to put passwords in plaintext in a file somewhere though.  Also, if I move my laptop to a different network where there are different servers and different authentication details, this is still a pain.  I fall back to nautilis in these scenarios.

However, whenever I run nautilis from the command-line, I lose my XUbuntu desktop (different icons, different background image), and don't know how to get it back without logging out!  I was able to solve this by running nautilis as follows:

nautilus --no-desktop

Hope that helps someone...

---

### Post by bartoni on 2008-02-13
Thanks for the how to. Like many I'm using this on my eee pc with eeeXubuntu.

Ran into the same problems that others had;  browsing worked first time but browsing the network would time out on subsequent boots.

 I'm guessing that maybe fuse was starting before my wifi network was fully connected --- for some reason eeexubuntu nm-applet throws up a password dialogue when connecting to wifi.

So I removed fuse from autostarted apps and put the command in a script that i run manually. Works for me as I don't always need the network and the network shares aren't always turned on anyway.

---

### Post by Flagone on 2008-02-13
I had the same issue as Bartoni with fusesmb not working if I had it as an autostarted application.  I have been posting about it here:

[http://forum.eeeuser.com/viewtopic.php?id=14941](http://forum.eeeuser.com/viewtopic.php?id=14941)

Interestingly I came to the same conclusion about why it may not be working.  I will investigate further tonight with trying to manually load fusesmb before the network is up to see if I get the same timeout failure.

---

### Post by DJiNN on 2008-02-15
This is a great how to & i have used it successfully on several Xubuntu installs.... HOWEVER!...... i have come to the conclusion that it's just as easy (EASIER, in fact) to install "Konqueror" (Along with the KDE Base etc) and then just use that to do all of my browsing, both on the local Network & also on the Net itself.  It works fantastically and doesn't really slow anything down at all, even on older (PIII etc) machines.....

If only Thunar/XFCE had this capability...... :(

---

### Post by camellochapin on 2008-02-18
It just works!

thanks a lot! :)

---

### Post by jpconard on 2008-03-06
Works the first time, until you reboot, like many others here.

I think it is due to the slow connection of wireless and having to enter keyring password before wireless connection.  So then my priveleges become read only and connection times out.

No good way to make keyring automated in Gutsy.  At least what I have searched for so far.

I'll try removing from auto start and running it as a script.

The linNeighborhood does work, but requires some setup.  It also creates a shell script to mount the shares, but I can't get that to run automated either.  Again think it is because it runs prior to the wireless connection being established.

Oh well at least I can get to my shares in two different ways, just not automatically.

---

### Post by The Pinny Parlour on 2008-03-06
I can't get this working.  I have followed the steps but I get this a 6.5:
power3@PHB3:~$ sudo chown power3:fuse /media/network
chown: cannot access `/media/network': No such file or directory

I need Network browsing to the linux server  HELP PLEASE

---

### Post by Tazix on 2008-03-30
I haven't been around in a long time (too many other projects).

I'm not sure how to answer the folks that are having problems after a re-boot or problems with dropped wireless connections.

I'm not really a linux guru.. just *maybe* an above average one (not a total n00b). ;)

The only things I can suggest is to try get support from either the xubuntu developers or the developers of fuse.  I've noticed that newer versions of fuse are starting to come out again, so with hope - a lot of these "gotchya" issues will go away.

Just FYI, my original Xubuntu box is still running strong with no network share issues. We'll see what happens after 8.04 is released since I plan on updating that box from scratch.

-Taz

---

### Post by DJiNN on 2008-03-31
This tutorial certainly helped me deal with a lot of network issues with Xubuntu. :)  However, i have found since, that it's much easier (& not very resource heavy either) to just install either Nautilus or Konqueror and use those for network shares/browsing. They need very little (if any) setting up, and work pretty much right away.

I have also heard that the people over at Thunar are working to resolve this issue and make it a thing of the past. I really do hope that they do, because it's the one thing that Thunar (Xubuntu, XFCE etc) is sadly lacking. 

This method (as Tazix outlined) does work though, and works very well.

---

### Post by gn2 on 2008-04-28
I've just tried this with Xubuntu 8.04 and it works perfectly, as it did with 7.04

Big thanks Tazix, you're a star! :)

---

### Post by katon on 2008-05-03
so you say you can install nautilus and solve the problem?

---

### Post by hiazle on 2008-05-06
Thank You! Tazix and EatMorePie

I managed to get this setup with a very minimal install on a system with 128MB. I followed EatMorePie's directions and I noticed that there was nothing coming up in "/media/network", so I ran the command "fusesmb /media/network" in the terminal and got an error message that said something like 

"configuration file should only be accessible to owner"

So I ran the command "**chmod 600 .smb/fusesmb.conf**" and that fixed my problem.

Now it works like a charm!

---

### Post by JustinAlf on 2008-05-16
My connection times out, and I can never see the files in the folders, but can always see the folders.  How do I fix this?

---

### Post by Zymous on 2008-05-19
> So I ran the command "chmod 600 .smb/fusesmb.conf" and that fixed my problem.

It fixed mine as well. I suspect it's the answer to a lot of the questions posted here.

-- 
Zym

---

### Post by syphaxx on 2008-06-08
> **JustinAlf said:**
> My connection times out, and I can never see the files in the folders, but can always see the folders.  How do I fix this?

I have the same problem. Reinstalled xubuntu 2 times and re-done the procedure. I can use pyNeighborhood.
Any hints?

---

### Post by chalewa on 2008-06-16
> **JustinAlf said:**
> My connection times out, and I can never see the files in the folders, but can always see the folders.  How do I fix this?


having the exact same problem...maybe an update recently messed something up?

i never was having this problem before

---

### Post by foureight84 on 2008-06-18
very useful thread!

---

### Post by rametux on 2008-06-23
It's work perfectly on hardy too. I hope u don't mind if i translate it into my language and put it on my blog. Here's the link: [http://rametux.wordpress.com/2008/06/23/mengaktifkan-windows-network-browsing-di-thunar/](http://rametux.wordpress.com/2008/06/23/mengaktifkan-windows-network-browsing-di-thunar/)
I hope my other fellows from my country could more understand it ;-)
Thank u very much...

---

### Post by tommie74 on 2008-06-27
Thx, this works like a charm!

I've added it to the Dutch Ubuntu Wiki:

[https://wiki.ubuntu.com/WindowsNetwerkInXubuntuThunar](https://wiki.ubuntu.com/WindowsNetwerkInXubuntuThunar)

---

### Post by Pasty on 2008-06-27
Thanks Taz. Once I sorted a few PICNIC problems out got it working fine. Excellent how to!:)

---

### Post by stentor007 on 2008-07-12
> **Tazix said:**
> Since Thunar doesn't have native network Browsing, here is a good way to accomplish it:

1) In XFCE's Applications -> System -> Shared Folders. (This should trigger a Samba install if you don't already have a share, and it should allow you to define the proper workgroup)

2) Install fusesmb in Synaptic (from Universe repository)

3) Edit /etc/modules and add the word 'fuse' to the modules list to be loaded (without quotes), and save the file.

4) Reboot, so the fuse module loads, and the proper workgroup is read for samba.

5) In XFCE Applications -> System -> Users and Groups... Properties of your username... User Priveleges Tab... check "Allow use of fuse file systems..."

6) Create a directory that you are going to mount your network browse to... I used /media/network. Change permissions to read / write for group and others (777).

*** 6.5) In a terminal, type: sudo chown <username>:fuse /media/network
(Where <username> is your user account logon name)

*** 6.6) Double check that the permission to use fuse took. Applications -> System -> Users and Groups... Manage Groups... find fuse and choose properties.  Make sure your user name account is in that group and check-marked.

*** 6.7) Reboot the system and triple check with step 6.6

7) In XFCE Applications -> Settings -> Autostarted Applications... Add an application... name and describe as you wish... for command line, put: fusesmb /media/network (Or whatever mountoint you created).

8) Open Thunar, and navigate to the parent folder of your mountpoint... then drag the 'mounpoint folder' to the places (shortcut) pane of thunar.

9) Logout and log back in (So the user privilege and fusesmb autostart will take affect)

*** Added steps to help prevent some access denied issues some people have been experiencing with fusesmb.

My original thread on this topic is here: [http://www.ubuntuforums.org/showthread.php?t=300310](http://www.ubuntuforums.org/showthread.php?t=300310)

I hope this helps my fellow Xubuntu users... and I also hope that the Xubuntu team somehow enables something similar by default, or at least as an install option.

-Taz
Wow!  Thank you so much. I guess one of the drawbacks of Xubuntu is its very lightness.  So one has to add the components as needed, and that takes some sophistiation.  As a noob, I really appreciate the help.  Worked like a charm.

---

### Post by stentor007 on 2008-07-12
For some reason it worked like a charm the first time, but after shutting down and restarting I get a "permission denied" when trying to access /media/network, and, although I can see the architecture of the Windows computer on the network, when I try to connect to a folder I get "Failed to open directory {NAME}, Connection timed out.  When I open Thunar under my login I see the Network folder, but if I open Thunar as root, or if I navigate to /media/network from terminal, the file doesn't exist.  I think something has happened to cancel the fuse after the reboot, but I'm a noob and can't figure it out.  All help appreciated!!!

Jim

---

### Post by chalewa on 2008-07-12
> **stentor007 said:**
> For some reason it worked like a charm the first time, but after shutting down and restarting I get a "permission denied" when trying to access /media/network, and, although I can see the architecture of the Windows computer on the network, when I try to connect to a folder I get "Failed to open directory {NAME}, Connection timed out.  When I open Thunar under my login I see the Network folder, but if I open Thunar as root, or if I navigate to /media/network from terminal, the file doesn't exist.  I think something has happened to cancel the fuse after the reboot, but I'm a noob and can't figure it out.  All help appreciated!!!

Jim


yea see above...

a lot of people have been experiencing this very problem. I don't know why it is happening, nor have i found any type of solution to it.

---

### Post by stentor007 on 2008-07-12
> **Zymous said:**
> It fixed mine as well. I suspect it's the answer to a lot of the questions posted here.

-- 
Zym

Did NADA for me.  Any other ideas??  I'm left with a folder: "network" under a directory: "media" that I can see with Thunar as my logon, but not as root!!!!!

Hard to fathom.  I can't delete the directory network either.

Jim:confused:

---

### Post by chalewa on 2008-07-12
> **Zymous said:**
> It fixed mine as well. I suspect it's the answer to a lot of the questions posted here.

-- 
Zym

yea i ran that command as well, but it didn't work. i think that the problem they were experiencing and the one that we are experiencing are different. 

what is bizarre to me is that this thing was working fine for the longest time, and then one day i just started getting this error message.

---

### Post by stentor007 on 2008-07-12
OK, so here it is.  You can definitely get fuse working in Thunar under Xubuntu Hardy Heron using the Fusesmb Community documentation page:

[https://help.ubuntu.com/community/FuseSmb#Installing%20fusesmb](https://help.ubuntu.com/community/FuseSmb#Installing%20fusesmb)

I'll tell you in a moment if it persists in being OK when I reboot . . . No, Sir!!!@%%%#  :(

Will have to work further.

Jim

---

### Post by Hooya on 2008-07-13
Easiest way I found is to install smbfs, then you can mount the shared folders.  You have to know what they are of course, but once you figure that out it's as simple as:
```
sudo mount -t smbfs //192.168.1.x/folder /path/you/want/it/mounted
```
Make a shortcut like "x-terminal-emulator -e" followed by that above command and just double click it, enter your sudo password, then go from there.

This is what I do between my 8.04 desktop and my 8.04 laptop, both running thunar for the file manager under fluxbox.

---

### Post by stentor007 on 2008-07-13
> **Hooya said:**
> Easiest way I found is to install smbfs, then you can mount the shared folders.  You have to know what they are of course, but once you figure that out it's as simple as:
```
sudo mount -t smbfs //192.168.1.x/folder /path/you/want/it/mounted
```
Make a shortcut like "x-terminal-emulator -e" followed by that above command and just double click it, enter your sudo password, then go from there.

This is what I do between my 8.04 desktop and my 8.04 laptop, both running thunar for the file manager under fluxbox.
Is smbfs the same as fuse?

Also, since my desktop is in WinXP, and the system is DHCP, not static IP, might I use the computer name rather than the IP address if I wanted to go that route?

And in general wouldn't it be great for the linux box to connect with all available network resources rather than having to know in advance which they are?  This is what the Mac OS can do and also (not as well) Win.

Jim

---

### Post by chalewa on 2008-07-13
i really wish that i could figure this out. i have been having this issue for a while now, and it seems like everyone is hitting a brick wall. 

i read on a zenwalk forum that they were having similar issues with fusesmb, and that were able to solve the problem by commenting out a line in /etc/hosts. of course i tried, and had no effect.

---

### Post by stentor007 on 2008-07-13
OK.  I did it!  :KS  Do what the fuse page says @

[https://help.ubuntu.com/community/Fu...ling%20fusesmb](https://help.ubuntu.com/community/Fu...ling%20fusesmb)

Then write a script called fusenet or whatever you wish as follows:

#!/bin/bash
clear
fusermount -u Network
wait
fusesmb Network
wait
cd Network
Thunar

This script unmounts the fused filesystem that you had running when you shutdown, and restarts the network fuse that you had setup according to the directions in the site above.  You can make a Launcher icon for this in the Xubuntu top toolbar, and launch it when you want to connect to the network.  Works just the way the MacOS does.  MacOS doesn't connect to the network file system until you click on network in Finder, then everything shows (if set up correctly)!

Oh one other thing . . . make sure you write changemod 755 fusenet or whatever you have called the script, so that you own it and have permission to run it.  I've given up trying to automatically load the fusesmb on startup.  The script which works after startup just won't workfor me during startup.  I usually logout with the instruction to save previous session.  This could be part of the problem, but it is good for other reasons.

Good luck,

Jim

---

### Post by chalewa on 2008-07-14
> **stentor007 said:**
> OK.  I did it!  :KS  Do what the fuse page says @

[https://help.ubuntu.com/community/Fu...ling%20fusesmb](https://help.ubuntu.com/community/Fu...ling%20fusesmb)

Then write a script called fusenet or whatever you wish as follows:

#!/bin/bash
clear
fusermount -u Network
wait
fusesmb Network
wait
cd Network
Thunar

This script unmounts the fused filesystem that you had running when you shutdown, and restarts the network fuse that you had setup according to the directions in the site above.  You can make a Launcher icon for this in the Xubuntu top toolbar, and launch it when you want to connect to the network.  Works just the way the MacOS does.  MacOS doesn't connect to the network file system until you click on network in Finder, then everything shows (if set up correctly)!

Oh one other thing . . . make sure you write changemod 755 fusenet or whatever you have called the script, so that you own it and have permission to run it.  I've given up trying to automatically load the fusesmb on startup.  The script which works after startup just won't workfor me during startup.  I usually logout with the instruction to save previous session.  This could be part of the problem, but it is good for other reasons.

Good luck,

Jim

that's fabulous. thanks so much for your help. 

there was an error in your link

[https://help.ubuntu.com/community/FuseSmb](https://help.ubuntu.com/community/FuseSmb)

that is the correct path. 

I also don't understand why the script is necessary... why not just add fusesmb Network (if using example) to your startup commands?

---

### Post by hammeraxe on 2008-07-24
:)

i got it working after a bit of tinkering and it even does seem to mount at startup

there is a problem though :(

i have shared one folder from my WinXP laptop and then theres the default SharedDocs. from ubuntu i see one more mysterious folder C$. i cannot view or edit any files in the folder i shared or the C$ folder: permission denied even for root although when creating my Network folder i set all the permissions to Read&Write. only the SharedDocs folder works properly.
:confused:

what could cause this?

---

### Post by chalewa on 2008-07-30
Yea i have that issue as well... I wouldn't worry about it, if the other share works, and no one can get into C$, then who cares.

---

### Post by sefs on 2008-08-15
I have my main user and machine name is the same, so is the netbios name... all are called paspory

When I do this solution I see...

/media/network/mshome/paspory/myshare

I can get right down to myshare before problems start....

When I try to enter myshare I get connection time out immediately....

also 

also i see some peculiarity happening with "paspory" vs "paspory.local"

For some reason my machine seems to operate better with the latter name where samba is concerened....but the former name seems to be picked up automatically by samba.  

So when I use smbclient -L paspory I get some error

When I use smbclient -L paspory.local it prompts for a password, I hit enter and it gives me a list of shares and things available on the machine.

---

### Post by dannyboy79 on 2008-08-15
do you have a dns server or WINS server running locally or are you using your hosts file?

---

### Post by sefs on 2008-08-15
It's using avahi the mdns thing.  This is installed by default and enabled on ubuntu. And I usually install bonjour on the windows machines so they use mdns as well.

---

### Post by mirex on 2008-09-22
Tazix: thanks for the how-to, works well on XUbuntu 8.04 . Newbies will have problems applying this to the system, so I think it should get into installation as a option (which is turned on by default)

---

### Post by jwilentz on 2008-10-07
> **Tazix said:**
> Since Thunar doesn't have native network Browsing, here is a good way to accomplish it:

1) In XFCE's Applications -> System -> Shared Folders. (This should trigger a Samba install if you don't already have a share, and it should allow you to define the proper workgroup)

2) Install fusesmb in Synaptic (from Universe repository)

3) Edit /etc/modules and add the word 'fuse' to the modules list to be loaded (without quotes), and save the file.

4) Reboot, so the fuse module loads, and the proper workgroup is read for samba.

5) In XFCE Applications -> System -> Users and Groups... Properties of your username... User Priveleges Tab... check "Allow use of fuse file systems..."

6) Create a directory that you are going to mount your network browse to... I used /media/network. Change permissions to read / write for group and others (777).

*** 6.5) In a terminal, type: sudo chown <username>:fuse /media/network
(Where <username> is your user account logon name)

*** 6.6) Double check that the permission to use fuse took. Applications -> System -> Users and Groups... Manage Groups... find fuse and choose properties.  Make sure your user name account is in that group and check-marked.

*** 6.7) Reboot the system and triple check with step 6.6

7) In XFCE Applications -> Settings -> Autostarted Applications... Add an application... name and describe as you wish... for command line, put: fusesmb /media/network (Or whatever mountoint you created).

8) Open Thunar, and navigate to the parent folder of your mountpoint... then drag the 'mounpoint folder' to the places (shortcut) pane of thunar.

9) Logout and log back in (So the user privilege and fusesmb autostart will take affect)

*** Added steps to help prevent some access denied issues some people have been experiencing with fusesmb.

My original thread on this topic is here: [http://www.ubuntuforums.org/showthread.php?t=300310](http://www.ubuntuforums.org/showthread.php?t=300310)

I hope this helps my fellow Xubuntu users... and I also hope that the Xubuntu team somehow enables something similar by default, or at least as an install option.

-Taz
Only problem is that if you are using a wireless network, it takes time to connect, and the autostart script tries to run to fuse the netmount in samba before the wireless net is connected and fails.  After the wireless net is connected, the fused samba mount is not readable.  Is there any way to get the fuse smb script to wait to run until the wireless net is connected, or to keep checking for available workgroup computers at stated time intervals after the wireless net is connected?

JRW

---

### Post by Caphi on 2008-10-23
I tried this, and whenever I actually try to mount fuse to the folder ($ fusesmb /media/network), I can no longer access the folder. I am told that permission is denied, and an ls shows "d????????? ? ? ? ? network" for the entire folder. Did I do something wrong?

---

### Post by FrankVdb on 2008-10-28
I'm having a similar and very annoying problem. I'm running Xubuntu Hardy with fusesmb configured the way it should. I was able to access shared folders on all of my machines in my home network (one is W2K, one is Mint and the other one Ubuntu Hardy) with no problem. Suddenly, I can no longer access the folders. My PC sees the machines and the folders but when double-clicking the folders I immediately get a "Verbinding verlopen" ("Connection timed out" in Dutch) error. This is driving me crazy. I've been googling for days now, no solutions found.

---

### Post by foxy123 on 2008-10-28
I've got a similar problem on Intrepid. It starts ok but then Network folder disappears after a couple of click.

---

### Post by dcory on 2008-11-01
> **foxy123 said:**
> I've got a similar problem on Intrepid. It starts ok but then Network folder disappears after a couple of click.

Just want to say that I'm having the same problem.  It works for a few seconds, and then blips out.

I'm wondering if loading a different program (i.e. other than Thunar) would be useful?

---

### Post by benma on 2008-11-04
Have the same exact problem after upgrading from hardy to intrepid.
doing 
umount /media/network
fusesmb /media/network

remounts for several seconds and then goes back to the mentioned error.
Never had this problem in hardy.

running ls -l gives:

ls: cannot access network: **Transport endpoint is not connected**
total 48
.
.censored
.
d????????? ? ?     ?         ?                ? network
.
.censored

while running sudo ls -l gives:

ls: cannot access network: **Permission denied**
total 48
.
.censored
.
d????????? ? ?     ?         ?                ? network
.
.censored

---

### Post by benma on 2008-11-04
It seems it's a Thunar problem, because if i don't open Thunar and browse /media/network from CLI, nothing happens - fusesmb stays connected.

---

### Post by benma on 2008-11-04
It's an even Debian Lenny problem inherited by ubuntu in multiverse/uniberse.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497572](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497572)


Try:
Untill fusesmb newest version is fixed:
In the manual don't use fusesmb. install smbnetfs package instead.
All the other directives are fine.

update:
workes longer, fails with same symptoms eventually.

---

### Post by foxy123 on 2008-11-05
I have downgraded libsmbclient to a Hardy version and it works now. I do not know for how long though.

---

### Post by jwilentz on 2008-11-20
> **foxy123 said:**
> I have downgraded libsmbclient to a Hardy version and it works now. I do not know for how long though.
How were you able to do that downgrade?

The Hardy-update repository is no longer available on canonical.com or doesn't seem to "take."

I used the mirror site

deb [http://mirrors.kernel.org/ubuntu](http://mirrors.kernel.org/ubuntu) hardy-updates

Cheers,

JRW

---

### Post by foxy123 on 2008-11-20
> **jwilentz said:**
> How were you able to do that downgrade?

Just add Hardy repository in your sources.list and then choose Force package. Please note that it will uninstall gvfs-backends package.

---

### Post by jwilentz on 2008-11-24
> **foxy123 said:**
> Just add Hardy repository in your sources.list and then choose Force package. Please note that it will uninstall gvfs-backends package.
OK,  Many Thanks to foxy123!!

This is a bug in the samba library for 8.10, and I have solved it as suggested by regressing to libsmbclient from 8.04 Hardy.  This is done by adding the Hardy repository to one's software sites in System > Software sources, then under Third Party Software add or enable the Canonical.com/ubuntu hardy partner.  Once that's done go to the Synaptic Package Manager and look for libsmbclient.  You will find (if you have 8.10) that the version is 2:3.2.3-1.  Click on the install box and then go up to Package (on the menu bar) and select force version and get version 3.0.28a-1ubuntu4.4.  Hit Apply (it will uninstall an unneeded file (I think) called gvfs-backends) and then you'll have a working version.  To make sure Update Manager doesn't keep trying to change you back to 8.10, go back in Synaptic Package Manager select the libsmbclient again, go to Package on the menu bar and select "Lock Version."  Now you're done and fusesmb and samba should work as desired to allow Thunar or other browsing of allowed Windows network shares.

---

### Post by dolu on 2008-11-25
> **Tazix said:**
> Well... on a fresh installation on another machine... I ran into the same issue as Miguellint did.

Not exactly sure what is causing it.... but after several attempts of recreating directories in /media, manually running fusesmb /media/network in the terminal... what seemed to fix it was removing from autostarted applications... then a  sudo fusesmb /media/network, then a reboot, then a discovery that the fuse permission needed to be redone (step 5) because it was no longer checked off, another reboot after fixing that, and then another manual fusesmb /media/network (no sudo this time).   Once working the command can be added back to autostarted applications (step 7).

I also found after that after I got it working.... /media/ was root owner and 777, but /network/ was myself as owner and 755. I'm pretty sure fusesmb sets that on the fly, because when I tried the sudo fusesmb command... I couldn't get in the directory as myself... had to look at it "as root".  Maybe adding a chown step 6.5 would be in order to help get the thing working. Example: Step  6.5 chown yourusername:yourusername /media/network

Anyway... the whole point is.... double check that step 5 took... you may have to fiddle around manually a few times, with a few reboots to get it to show step 5 didn't take.  It must be some sort of PAM glitch or something.  But it is repairable.

Hope that helps,

Taz

Hi,
I have same problem with my pc/os workstation 2009 (pc-os.org). After running fusesmb, the permission file of /media/networks change from 777 into 755. And I can not sudo chmod 777 again when fusesmb running.
The windows share is open and show the share folder, but I can not view the content of the share folder.
Need Help...

---

### Post by Presi on 2008-11-27
> **jwilentz said:**
>   Click on the install box and then go up to Package (on the menu bar) and select force version and get version 3.0.28a-1ubuntu4.4. 

I added the Hardy repositories, but when I try to force the older version (menu package, force version) I see only intrepid versions in the pop up menu.

What I'm doing wrong?

Today a new version of libsmbclient was avilable (2:3.2.3-1ubuntu3.3) but this problem has not been addressed.

---

### Post by rudlavibizon on 2008-12-14
I also don't see anything in mounted folder. pyNeighborhood browser see windows computers but cannot mount the shared folders and xsmbrowser works fine (so I know it's a fusesmb issue). I'm using Xubuntu 8.10. :confused

---

### Post by deepee_oz on 2008-12-20
> **jwilentz said:**
> OK,  Many Thanks to foxy123!!

This is a bug in the samba library for 8.10, and I have solved it as suggested by regressing to libsmbclient from 8.04 Hardy.  This is done by adding the Hardy repository to one's software sites in System > Software sources, then under Third Party Software add or enable the Canonical.com/ubuntu hardy partner.  Once that's done go to the Synaptic Package Manager and look for libsmbclient.  You will find (if you have 8.10) that the version is 2:3.2.3-1.  Click on the install box and then go up to Package (on the menu bar) and select force version and get version 3.0.28a-1ubuntu4.4.  Hit Apply (it will uninstall an unneeded file (I think) called gvfs-backends) and then you'll have a working version.  To make sure Update Manager doesn't keep trying to change you back to 8.10, go back in Synaptic Package Manager select the libsmbclient again, go to Package on the menu bar and select "Lock Version."  Now you're done and fusesmb and samba should work as desired to allow Thunar or other browsing of allowed Windows network shares.

I got the "Transport endpoint is not connected" error after a few seconds of browsing the Windows shares from a MythBuntu system. 
I tried the downgrade using the suggestions above. 
I enabled  "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner" and followed the instructions but there is no option for installing version 3.0.28a-1ubuntu4.4. 
The only option presented in the drop down list is for the currently installed version. 
Either something has changed or something is missing in the steps outlined above. 

Can anyone provide us with some more pointers?

As comment, a MythBuntu needs to have built-in native support for browsing network shares to be useful. It really should not be this hard.

Ta
deepee

---

### Post by Presi on 2008-12-24
> **jwilentz said:**
> OK,  Many Thanks to foxy123!!

This is a bug in the samba library for 8.10, and I have solved it as suggested by regressing to libsmbclient from 8.04 Hardy.  This is done by adding the Hardy repository to one's software sites in System > Software sources, then under Third Party Software add or enable the Canonical.com/ubuntu hardy partner.  Once that's done go to the Synaptic Package Manager and look for libsmbclient.  You will find (if you have 8.10) that the version is 2:3.2.3-1.  Click on the install box and then go up to Package (on the menu bar) and select force version and get version 3.0.28a-1ubuntu4.4.  Hit Apply (it will uninstall an unneeded file (I think) called gvfs-backends) and then you'll have a working version.  To make sure Update Manager doesn't keep trying to change you back to 8.10, go back in Synaptic Package Manager select the libsmbclient again, go to Package on the menu bar and select "Lock Version."  Now you're done and fusesmb and samba should work as desired to allow Thunar or other browsing of allowed Windows network shares.

You need also to make sure that this repo is in SOURCES.LIST:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main

that's the reason why I could not downgrade.

---

### Post by EaPendergast on 2008-12-31
Any chance of having this working without downgrading?
I also got the "Transport endpoint is not connected".

Is it possible in xfce to use Nautilus without changing anything of the enviroment?

thanks in advance
Pendergast

---

### Post by foresto on 2009-01-07
I'm having the same problem with smbnetfs after upgrading from hardy to intrepid.  I've just edited my startup file to disable its multi-threaded operation, with a command line like this:

  smbnetfs /my/mountpoint -s

So far, it hasn't crashed using this mode. (I suspect I have lost some performance, though.)  I did not downgrade back to the hardy packages.

Related bug report:

[https://bugs.launchpad.net/ubuntu/+source/fusesmb/+bug/198351](https://bugs.launchpad.net/ubuntu/+source/fusesmb/+bug/198351)

**Update:   smbnetfs crashed again even when running with -s.**

---

### Post by alan_new on 2009-01-26
> **EaPendergast said:**
> Any chance of having this working without downgrading?
I also got the "Transport endpoint is not connected".

Me to. Too bad, because I remember it worked fine on 7.10.

> **EaPendergast said:**
> 
Is it possible in xfce to use Nautilus without changing anything of the enviroment?

thanks in advance
Pendergast
```
nautilus --no-desktop
```

---

### Post by maniaq on 2009-01-31
yeah, I guess if you have no other choice then mounting the network drive and accessing the mount point in Thunar is an ok workaround...

be better if there was proper network browsing tho...

say what you will about MS but I have yet to find a superior file manager to Windows Explorer

---

### Post by detyabozhye on 2009-02-02
> **maniaq said:**
> say what you will about MS but I have yet to find a superior file manager to Windows Explorer

Try Konqueror 3.5.x. Right now I use KDE 3.5.10, but when I used to use XFCE, I used Konqueror for all my network browsing.

---

### Post by chalewa on 2009-02-08
so now that this doesn't work, there is no way to browse shares in xfce?

---

### Post by krisalis on 2009-02-12
Hi, found this thread looking for way to access my Buffalo Network drive from a newly xubuntu'd machine.  In Ubuntu it got picked up straight away via Network Servers.  Network servers does not seem to exist in xubuntu.

... am I having the same issue as has been/is being discussed here?

If not, please help me, otherwise this is a critical putoff for me with xubuntu.

---

### Post by dannyboy79 on 2009-02-13
> **maniaq said:**
> say what you will about MS but I have yet to find a superior file manager to Windows Explorer
Thunar, Nautilus, and all *nix File Explorers have nothing to do with interfacing with network drives etc etc. It's the programs that interface with them. The problem is that Windows Network Browsing with other Windows computers is all fine because it's all proprietary coding, whereas the folks at SMB has to reverse engineer the Windows network file browsing so that *nix could browse Windows Shared Drives. So I wouldn't blame it on the File manager/explorer. That's just my opinion.

---

### Post by JKoltner on 2009-02-16
"Thunar, Nautilus, and all *nix File Explorers have nothing to do with interfacing with network drives etc etc."

Well, contemporary file explorers are typically expected to have a means to browse to network drives, so the two concepts aren't entirely divorced from one another.

"So I wouldn't blame it on the File manager/explorer."

I agree there, the problem here is in some lower level libsmbfs code or somewhere like that.  Unfortunately there apparently wasn't enough regression testing to detect the bug prior to shipping Intrepid, which is poor since it crops up pretty quickly even in casual usage.

Oh well.  Happily with the instructions presented here about reverting to the Hardy smbclient, everything seems to work.  This post is now 17 pages long, though -- perhaps we should write-up a new procedure specific to Intrepid that includes the detailed instructions for reverting smbclient?

---Joel

---

### Post by foxy123 on 2009-02-16
> **JKoltner said:**
> "Thunar, Nautilus, and all *nix File Explorers have nothing to do with interfacing with network drives etc etc."

Well, contemporary file explorers are typically expected to have a means to browse to network drives, so the two concepts aren't entirely divorced from one another.

"So I wouldn't blame it on the File manager/explorer."

I agree there, the problem here is in some lower level libsmbfs code or somewhere like that.  Unfortunately there apparently wasn't enough regression testing to detect the bug prior to shipping Intrepid, which is poor since it crops up pretty quickly even in casual usage.

Oh well.  Happily with the instructions presented here about reverting to the Hardy smbclient, everything seems to work.  This post is now 17 pages long, though -- perhaps we should write-up a new procedure specific to Intrepid that includes the detailed instructions for reverting smbclient?

---Joel

I am quite surprised that it has not yet been fixed upstream :(

---

### Post by pt123 on 2009-03-16
any update on this transport problem?

seems pretty ridiculous, is there anyway to "upgrade" to a working old package?

---

### Post by Kangarooo on 2009-03-29
I Hope That first page will have update also on Newest version solution
Since its last edited 2007 i would not like to try that since i want clean system
If anyone can tell me how to get last steps back if they were incorect then ill do anything to my Xubuntu

---

### Post by foxy123 on 2009-03-30
I have recently updated to Jaunty and now use Gigolo to connect to network shares. It does not let you display available shares but using bookmarks makes life much easier.

---

### Post by tsali on 2009-05-09
> **foxy123 said:**
> I have recently updated to Jaunty and now use Gigolo to connect to network shares. It does not let you display available shares but using bookmarks makes life much easier.

With Gigolo, I can make a connection to my network share, but I cannot browse it or otherwise access it.

This truly sucks...it has to be some kind of poor joke...

---

### Post by foxy123 on 2009-05-09
> **tsali said:**
> With Gigolo, I can make a connection to my network share, but I cannot browse it or otherwise access it.

This truly sucks...it has to be some kind of poor joke...

do you have fuse-gvfs installed? i think that without it you cannot open shares mounted by gigolo

---

### Post by jwilentz on 2009-05-09
> **foxy123 said:**
> do you have fuse-gvfs installed? i think that without it you cannot open shares mounted by gigolo
Right now I'm doing a total fresh install of Jaunty, hoping it might work where the "upgrade" didn't, so I can't test this.  Will Gigolo allow browsing so that I can see all the shared folders on the Win XP box???

---

### Post by cgkx on 2009-05-10
In Xubuntu 9.04, you need install "gvs-fuse'' and "fusesmb" before you can open remote folder/filesystem icon in Gigolo.

When you drag&drop or copy/paste to desktop, it doesn't show you the progress bar;however, it's creating a folder and is doing the copy.

To be more visible of the progress, you need to drag&drop or copy/paste from remote folder (double click to make Thunar open a folder window for this remote system) to one of your folder (double click, say your "home"). This way, you can see the progress.
                                                                                                                                    [I]                                              [Last edited by cgkx]("http://ubuntuforums.org/posthistory.php?p=7250269"); 2 Minutes Ago at 05:02 AM..                                                           
Just an update, I just have two SMB machines so I use IP directly in Gigolo, instead of trying to figure out way of "browsing network". Will update if there's neat one.
[/I]

---

### Post by jwilentz on 2009-05-10
cgkx,

Thank you for your quick and thoughtful reply.  Unfortunately, the networking problem with 9.04 was the least of my troubles.  A myriad other problems (no recognition of mouse, ACPI failure, failure to boot at all after one successful boot with the etc4 system, then going through the obligate post-install update mgr updates, total failure of the system with the drum majorette's baton twirling and twirling!!!  I'm currently in the middle of reinstalling 8.04 from scratch (saved all data to a remote server prior to any of this) amd will use your suggestions with Samba when installed.

---

### Post by palin_linux on 2009-05-11
Nice How to!

 For though who are having trouble or Just staring out out try pyNeigborhood. small, lightweight can use smb or cif and is in synaptic.

I made a launcher in my panel `gksudo pyNeighborhood`. all Done 

:)

---

### Post by joylessdave on 2009-05-13
> **tsali said:**
> With Gigolo, I can make a connection to my network share, but I cannot browse it or otherwise access it.

This truly sucks...it has to be some kind of poor joke...

i found i had to change the volume manager implementation from HAL to unix in the gigolo preferences 

i don't think you need gvfs-fuse as it is using gvfs-open

---

### Post by foxy123 on 2009-05-13
The problem I have with Gigolo is that I cannot copy/move files to the mounted shares due to permissions. I cannot find a way to mount them read/write

---

### Post by joylessdave on 2009-05-13
havn't tried writing to a share with gigolo may have a go later in the week
luckily i only want the xubuntu machine as a media player in another room

---

### Post by RichardG891 on 2009-05-17
> **cgkx said:**
> In Xubuntu 9.04, you need install "gvs-fuse'' and "fusesmb" before you can open remote folder/filesystem icon in Gigolo.

When you drag&drop or copy/paste to desktop, it doesn't show you the progress bar;however, it's creating a folder and is doing the copy.

To be more visible of the progress, you need to drag&drop or copy/paste from remote folder (double click to make Thunar open a folder window for this remote system) to one of your folder (double click, say your "home"). This way, you can see the progress.
 		                   		  		  		  		  		 		 			 				 				* 					 						[Last edited by cgkx]("http://ubuntuforums.org/posthistory.php?p=7250269"); 2 Minutes Ago at 05:02 AM.. 					 					 				*

:pThankyou, thankyou. Been messing about with this for ages... and always gone back to gnome 'cos it's such a no-brainer in Nautilus. It's a bit of a faff having to open shares via gigolo, and it can't find any workgroups in its sidebar browser (or at least I can't make it see...) so you have to know the name of your remote target. Hopefully, Thunar will integrate network browsing in the future... though the developer doesn't seem keen.

With the read/write issue, foxy123, have you made yourself a member of the "fuse" group? I didn't have to do anything else.

---

### Post by foxy123 on 2009-05-17
> **RichardG891 said:**
> With the read/write issue, foxy123, have you made yourself a member of the "fuse" group? I didn't have to do anything else.

yes I'm a member of the fuse group but it does not help.

---

### Post by RichardG891 on 2009-05-18
Right. The share I've checked read/write access to is on one of my own machines running XP (i.e. simple file sharing) and with the same username.... so I've left log-in details in gigolo's bookmark blank. I'll try it at work and get back to you (shared volume on a debian server).

---

### Post by tetralis on 2009-05-19
I used to run Win XP on the same computer I run xubuntu 9.04 today. Reaching windows shares from this computer (in Windows days was never a problem). Today I can only access the shares from xubuntu using firefox by entering smb://server/

I tried to follow the steps in this threds with no success. I can se the workgroup. click on it to se the computer on which the windos share are, then I can click on the computer to see all the shares. Now If I click on any of the shares I will get an empty file list and "connection timeout". Any ideas on this? As I stated above I can reach the shares from the same xubuntu computer using Firefox.

---

### Post by tetralis on 2009-05-20
Well. I have done some more reading in this and other threads with no success. The faults are:
"Connection time out" and "Transport endpoint is not connected"

Have to say it works fine from the terminal, a long as you don't navigate the shares with Thunar. 

Some says this is a "bug" lib-related samba/fuse other mentioned dual port issues in smb ([http://threebit.net/mail-archive/samba/msg01522.html](http://threebit.net/mail-archive/samba/msg01522.html))

My "work around" was to have smb mounts in fstab, so no network browsing for me currently (this will at least decrease my wasted time and increase the Wife Satisfaction Index): [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

Glad to here from you who solved this issue in another way or confirmed a bug somewhere (provide a link please).

---

### Post by sparvik on 2009-06-02
Hello,
I'm using xubuntu 9.04
O.O.B I used giglo to mount my M$ shares (gig doesn't see workgroups or allow browsing of course) and that let me acess my files from some programs using the open or save as option but not all programs.  It simply shows the shares in the bookmarks on the side panel.  The shares of coarse don't show in thunar's places.

I tried to apt-get gvs-fuse but it said not found........

If there is another light weight alternative to thunar that will use the same bookmarks as the open option in totem I think that would be great. any sugestions?

oh without adding sources since I'd like to keep this clean as possable.

---

### Post by foxy123 on 2009-06-02
> **sparvik said:**
> Hello,
I'm using xubuntu 9.04
O.O.B I used giglo to mount my M$ shares (gig doesn't see workgroups or allow browsing of course) and that let me acess my files from some programs using the open or save as option but not all programs.  It simply shows the shares in the bookmarks on the side panel.  The shares of coarse don't show in thunar's places.

I tried to apt-get gvs-fuse but it said not found........

If there is another light weight alternative to thunar that will use the same bookmarks as the open option in totem I think that would be great. any sugestions?

oh without adding sources since I'd like to keep this clean as possable.
It should be 
```
sudo apt-get install gvfs-fuse
```

---

### Post by sparvik on 2009-06-02
sorry, I should have known it was a type-o

but with those installed it still didn't work so I started messing around with mounting with fusesmb in a terminal.

After changing permissions and groups around it worked fine. Now I should be able to access my shares with any app

**Just checked, gigolo still cant see workgroups but it opens locations now in thunar.  Found that it was mounting the shares in /home/username/.gvfs**

---

### Post by jwilentz on 2009-06-03
> **foxy123 said:**
> It should be 
```
sudo apt-get install gvfs-fuse
```


I think it is a bit ridiculous that we are all gathering in this forum about something so core to an operating system that it is approaching shameful that it is not there.  No operating system should be packaged without a workable network browser integral to its file management system.  That is the problem with Xubuntu, which is, in all other respects, an excellent system for lightweight older machines.

Fuse and SMB worked back in 8.04 (if not quite elegantly or seamlessly).  I have pinned the libsmbclient from 8.04 in my package manager but that is the only way I have gotten the whole thing to work for me in 8.10.  The Gigolo thing in 9.04 simply is a failure.

Why can't someone from Canonical or other linux high-level pros write an update for Thunar with network browsing and file sharing that really WORKS??  This is a real sticking point which will drive us back to M$.

Jim

---

### Post by sparvik on 2009-06-05
I understand your point but, it is free.  From what I read, while something works great in one release it fails in the next.  I think this is do to the "beta testing" being mostly done from people upgrading.  Important packages and config files get forgotten because they where already there if you upgraded.  

Now, perhaps if those of us that want the lower grade versions of Ubuntu could provide more support to the community in either Beta testing, source code or $$$ then things would get worked out before the official release.

As for me, I won't look a gift horse in the mouth.

---

### Post by jwilentz on 2009-06-06
> **sparvik said:**
> I understand your point but, it is free. From what I read, while something works great in one release it fails in the next. I think this is do to the "beta testing" being mostly done from people upgrading. Important packages and config files get forgotten because they where already there if you upgraded. 
 
Now, perhaps if those of us that want the lower grade versions of Ubuntu could provide more support to the community in either Beta testing, source code or $$$ then things would get worked out before the official release.
 
As for me, I won't look a gift horse in the mouth.
 
Fair enough, but so much else of xubuntu works beautifully.  It surprises me that this core component does not work at all.  I wish I were better at coding or had the time to fo this.  I would gladly.
 
J

---

### Post by foxy123 on 2009-06-06
> **jwilentz said:**
> I think it is a bit ridiculous that we are all gathering in this forum about something so core to an operating system that it is approaching shameful that it is not there.  No operating system should be packaged without a workable network browser integral to its file management system.  That is the problem with Xubuntu, which is, in all other respects, an excellent system for lightweight older machines.

Fuse and SMB worked back in 8.04 (if not quite elegantly or seamlessly).  I have pinned the libsmbclient from 8.04 in my package manager but that is the only way I have gotten the whole thing to work for me in 8.10.  The Gigolo thing in 9.04 simply is a failure.

Why can't someone from Canonical or other linux high-level pros write an update for Thunar with network browsing and file sharing that really WORKS??  This is a real sticking point which will drive us back to M$.

Jim
It is not Xubuntu's fault. As I understand it comes from upstream.  Thunar is developed as a lightweight file browser and is not supposed to read networks. It is possible to write a plugin for this purpose but no one has done it so far. 

You can use pyNeighborhood to browse and mount shares. Version 0.50 is quite good ([https://launchpad.net/pyneighborhood](https://launchpad.net/pyneighborhood)) but unfortunately does not work for me for Windows shares.

---

### Post by goodwin57 on 2009-06-25
I'm running xfce with thunar on linpus (acer aspire one setup) so I know this is a long shot for a response and I apologise for that, but this is the most significant place I've seen fuse discussed.

Has anyone had an experience where they manage to connect to a server (webdav at gmx.com in my case) but then thunar closes and on reopening it the mount-folder has disappeared?  Using the ls command from the terminal it (infuriatingly) lists the folders in the drive...I just can't see how to access them using thunar!

I'm open to suggestions.

EDIT:  I can also open the folder in thunar using the terminal by cd /myfolderlocation then sudo thunar...  When there the name appears to be slightly wrong (it should be /mnt/home/gmxdrive it appears as mydisk:///gmxdrive) I don't know if this matters or not.  It appears my network shares and permissions aren't correct on this folder (although I've set them on the folder prior to mounting the drive)...

---

### Post by tlindvall on 2009-06-26
I encountered the same problems some time ago.  I assume it is a bug related to acer modifications to thunar.  The problem is related to shortcuts like mydisk.  If you use path with the shortcut it shows only local filesystem for ex if you have one file in your mountpoint directory you see that file instead of the mounted share.

I have used the following solution:
- mount share using pyneighborhood
- open thunar and click filesystem.  Browse to your mountpoint (/home/user/network/<mountpoint> in my case).  when browsing this way there is no shortcuts in path.
- if this is your standard share you are using often create a thunar bookmark to it.

Regs Tarmo

ps This forum is dedicated to ubuntu distro so it might be better idea to use acer aspire one forum for this discussion.

---

### Post by foxy123 on 2009-06-26
> **tlindvall said:**
> I encountered the same problems some time ago.  I assume it is a bug related to acer modifications to thunar.  The problem is related to shortcuts like mydisk.  If you use path with the shortcut it shows only local filesystem for ex if you have one file in your mountpoint directory you see that file instead of the mounted share.

I have used the following solution:
- mount share using pyneighborhood
- open thunar and click filesystem.  Browse to your mountpoint (/home/user/network/<mountpoint> in my case).  when browsing this way there is no shortcuts in path.
- if this is your standard share you are using often create a thunar bookmark to it.

Regs Tarmo

ps This forum is dedicated to ubuntu distro so it might be better idea to use acer aspire one forum for this discussion.

actually it is an old Debian bug in libsmbclient:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497572](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497572)

I have not checked it for a while but there is a solution now: instead of executing ```
fusesmb /media/network
``` one should use -s command line switch, that disables multi-threaded operation, which is apparently the cause of the problem: ```
fusesmb -s /media/network
```
I cannot say for sure that it works, but I did not encounter this problem for the last hour.

---

### Post by goodwin57 on 2009-06-29
Thanks for your response.  I can't see how to use PyNeighborhood to connect to a webdav folder - although as a gui for network connections it looks fairly intuitive from what I can see and that might come in useful.  Regarding the use of "-s fuse", do you know how I can specify this when I'm using wdfs (which builds on fuse) to connect to webdav?  The commands I use are:

smbd
fusesmb  (to load fuse and samba)
wdfs [https://storage-file-eu.gmx.com](https://storage-file-eu.gmx.com) /media/gmxdrive -0 usename=username@gmx.com

I appreciate the help,

Simon

Edit:  Just to make it clear from my above post, I've moved my mount from within 'home' to within 'media', and I can access the folder if I access it via the terminal (telling thunar to open in that location) but thunar doesn't recognise it as a location to browse to, and when I do browse to it (which I can only do once) it closes and closes thunar with it.

---

### Post by snm_cal on 2009-07-29
Tazix,

I was trying your most acknowledged process on Xubuntu 9.04. Everything is showing up of my network. But suddenly, while I'm browsing the windows network. It is giving an error "Transport endpoint is not connected." and the network folder is disappearing from media.

Can you please help. Please excuse my ignorance.

---

### Post by Ginsly on 2009-08-13
> **jwilentz said:**
> I think it is a bit ridiculous that we are all gathering in this forum about something so core to an operating system that it is approaching shameful that it is not there.  No operating system should be packaged without a workable network browser integral to its file management system.  That is the problem with Xubuntu, which is, in all other respects, an excellent system for lightweight older machines.

Fuse and SMB worked back in 8.04 (if not quite elegantly or seamlessly).  I have pinned the libsmbclient from 8.04 in my package manager but that is the only way I have gotten the whole thing to work for me in 8.10.  The Gigolo thing in 9.04 simply is a failure.

Why can't someone from Canonical or other linux high-level pros write an update for Thunar with network browsing and file sharing that really WORKS??  This is a real sticking point which will drive us back to M$.

Jim

Sorry if its been mentioned before, but I read that a few people had been having trouble getting smb shares to open in Thunar using Gigolo.... (as was I the first time I stumbled upon this thread today)

I managed to get Gigolo working by following this method.....

[http://www.uvena.de/gigolo/help.html#open-resources-in-thunar-on-xfce-4-4-and-4-6](http://www.uvena.de/gigolo/help.html#open-resources-in-thunar-on-xfce-4-4-and-4-6)

It worked after I'd installed these....

smbfs 
fuse-utils
gvfs-fuse
gvfs-backends
gvfs-bin

---

### Post by Redsandro on 2009-08-21
> **snm_cal said:**
> It is giving an error "Transport endpoint is not connected." and the network folder is disappearing from media.

There's a library bug that hasn't been fixed for years. Installing an older version will do the trick, but I just learnt multithreading is the blame. Just disable that in your fuse and you should be fine. This is no problem unless you have multiple users on the same computer using thuse fuses at the same time.

[http://ubuntuforums.org/showthread.php?p=7697598#post7697598](http://ubuntuforums.org/showthread.php?p=7697598#post7697598)
> **albertomm said:**
> Try this:
```
fusesmb -s /path/to/mountpoint
```
it solved the problem for me (xubuntu jaunty)

It seems that some library on witch fusesmb depends isn't thread safe. The -s switch forces fusesmb to use only one thread.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497572]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497572")

---

### Post by geecee on 2009-08-30
I have a file server on my network running Ubuntu Server Edition. My Vista and XP boxes can see it without a problem.

Now I'm trying to set up another machine running Xbuntu. From Thunar or Gigolo I can see the network and get into the server. I can navigate through the file system until I reach a directory on which is mounted a second HDD. When I try to go further I get a "Permission Denied" error. What do I need to do now?

---

### Post by Epaminond on 2009-11-02
I've got a problem, which looks like the one described by **geecee**.

I followed the guide from the first post of the thread to get an access to files located on a machine running Windows XP. In my /media/network directory I can see the shared folders, but I can't open them. When I double click on them thunar "thinks" for about a minute and then closes. After that "network" directory disappears from /media.

Could you please help me? :)

---

### Post by Redsandro on 2009-11-02
Ever since I've upgraded to 9.10, I've got similar problems.
I spent a day trying to figure out what's wrong but I don't know..

Anyone come up with something, and I am interested. :)

---

### Post by jdinosaurus on 2009-11-03
You can try to use pyneighborhood as a workaround if you want to use thunar with smb. Just do not forget to add Thunar as a default file manager there.

---

### Post by Epaminond on 2009-11-03
How can I do that? Is there any guide? :)

---

### Post by jdinosaurus on 2009-11-03
```

sudo apt-get install pyneighborhood

```

then just run it with the command:
```

pyNeighborhood

```

It is just a GUI application which you can configure. What I did - I have added machines that I am usually using. In preferences I have specified File Manager - Thunar. For mount folder - I use "$HOME/network" (I am not sure if it understands $HOME - so it is better to specify the whole path).

When everything is configured - you just click on the samba machine that you want to open - it will automatically mount it to ~/network (or any other folder that you specified). Then you do right click on that and select in popup menu - open with file manager - and Thunar will open that folder.

P.S. It is also possible to browse the network.

---

### Post by Redsandro on 2009-11-03
pyNeighborhood does not see any shares. Gigolo does not either. Neither does fusesmb.
But running smbtree *sometimes* shows all the shares just fine.

---

### Post by Epaminond on 2009-11-03
Thank you! It worked great!
How can I make it mount all the shared folders with one click? Is there any script for this? :)

---

### Post by Epaminond on 2009-11-03
Finally I returned back to "smbmount". This sims to be easier.
It's a pity thunar can't mount requested folders automatically with this command.

---

### Post by Redsandro on 2009-11-03
To fusesmb your entire tree to for example ~/Desktop/network is imo easiest and I prefer it over smb://, but it just doesn't work anymore.

I also cannot force an older version in synaptic, it probably breaks too much dependencies for 9.10.

---

### Post by Epaminond on 2009-11-04
As far as I understand smb:// isn't supposed to work at Thunar.

---

### Post by sparvik on 2009-11-04
Supposedly with smbfuse you can get it to work in thunar, but.....

The apps that you use on xubuntu by default (ie: for music and vids) don't support the smb:// so I don't see the point.  The best solution I got while using xubuntu was pyneighborhood.  It mounts the share locally so that the apps I used for vids and music where able to see them.  But you do need to go in and make changes to the user accounts for sharing and tell pyneighborhood to scan with a different user credentials.  It's been months since I used it so I don't remember the exact phrasing. 

In pyneighborhood you right click on the desired computer and choose the scan with other user option or something along those lines.  

But under the user settings I add root and my user to the share and samba user group.

---

### Post by Redsandro on 2009-11-04
> **Epaminond said:**
> As far as I understand smb:// isn't supposed to work at Thunar.
True (afaik), that's why I don't have a problem with Xubuntu because I don't really prefer Ubuntu's built-in smb://. :)

@sparvik

pyNeighborhood uses samba libraries. Hence, pyNeighborhood does not work either. My temporarily solution is to use Gigolo. It's like pyNeighborhood, but new(er), better, and able to mount much more then just samba.

It's under Applictions -> System -> Remote Filesystems.

Meanwhile I'm hoping for a sambafix, because like pyNeighborhood, Gigolo also mounts what you tell it to instead of a dynamic folder.

---

### Post by Epaminond on 2009-11-05
I've tried it too. But actually it didn't work properly. Maybe that was my fault. ))
Finally I wrote a little script that uses smb(u)mount command to mount/unmount shared folders and binded a free key to launch it.

---

### Post by pearldrums on 2009-11-23
I know this will not be an acceptable work-around for some as it has some set-up time and data-storage requirements, and also that it is kind of a one-way fix that doesn't apply to all users, but I thought I would lay this out for anyone who is interested.

Samba works just fine in Xubuntu, it is simply thunar that has an issue. I had originally installed ubuntu on my netbook, I decided to switch to Xubuntu by using synaptic package manager and the terminal so that all of my data and settings would be preserved. I had already created a share folder in my home folder before this switch. When I got done and had Xubuntu I could not find a the network locations. But if I opened up the network from my main computer with Ubuntu installed, i could still see the share on the machine that is now running on Xubuntu! This works great for me because usually I'm just dropping stuff onto the netbook. It would be considerably slower if you were trying to go in the reverse because you would have to move the file to the share folder, and then retrieve it with the main computer. Naturally people that are running solid-state hard drives with only a few gigs of storage may not be able to install the gnome desktop, but I'm guessing there is a way to create a shared folder in the terminal? If there is PM me with the code and I'll add it to this post. Also, I have no idea if a windows machine could view this share file...

Step by step workaround for accessing a Xubuntu machine from a Ubuntu computer:
1. install the gnome desktop (more info here: [http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce))
I believe this can be done from synaptic
2. Logout
3. Log back in making sure to select a gnome session
4. Create a shared file in your home folder. Right click on it, and change its settings so that sharing is enabled. make sure to set its permissions to your preference.
5. remove gnome (again go to this website for more info [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce))

Your share should be working just find, but only in one direction. 

Also, I don't know if this would work, but if you create a shared folder does it keep the sharing capability if you move it? Perhaps one could create a share on a computer and move it via a usb drive to another computer.

Hope someone finds use out of this.

---

### Post by ugm6hr on 2010-02-06
Now that I definitely need SMB again to access my work network drives (SMB), I found Gigolo recommended above.  Given I don't want to go back to Gnome / Nautilus, it looked promising.

Install with
```
sudo apt-get install gigolo fuse-utils gvfs-fuse
```

Then dead easy to get to work with these instructions:
[http://www.uvena.de/gigolo/help.html#open-resources-in-thunar-on-xfce-4-4-and-4-6](http://www.uvena.de/gigolo/help.html#open-resources-in-thunar-on-xfce-4-4-and-4-6)

I then just created a shortcut to ~/.gvfs in thunar, so I can instantly access the shares from thunar as soon as Gigolo connects them.

Perfect.  Beats pyneighbourhood, although I haven't used that for some time now.

> ```
sudo gpasswd -a username fuse
```

Obviously, you should replace username by your actual used username.

Then, you may need to add the following lines to your ~/.local/share/applications/defaults.list so that Thunar is used to open folders by gvfs-open:

```
x-directory/gnome-default-handler=Thunar.desktop
inode/directory=Thunar.desktop
x-directory/normal=Thunar.desktop
```


---

### Post by Redsandro on 2010-02-06
Thanks for the links. I use Gigolo too for a while now, using it as an autostart application, but one thing that annoys me. Sometimes it wants to automount a folder that has a password. When in a hurry you press cancel, it seems like the dialog comes back a random number of times. Have you had and/or resolved this issue?

[SIZE="1"]Offtopic but related: Windows 7 shares need to be authenticated on *buntu and vice-versa, even though they are both accessable to guests.[/SIZE]

---

### Post by ugm6hr on 2010-02-06
> **Redsandro said:**
> Sometimes it wants to automount a folder that has a password. 

I do not automount anything.  I like to have control over what's mounting - I don't even automount USB sticks etc.

So sorry - I don't know.

I have also autostarted it in Sessions & Startup to go into the panel.  It basically just sits beside the Network Manager and Bluetooth icon in a row of connectivity options.

I like :)

---

### Post by Redsandro on 2010-02-06
Reason for automounts is mediacenter functionality. I'd like to be in control too but media serving should be as lazy and automated as possible. :P

---

### Post by bluezeak on 2010-05-01
> **foxy123 said:**
> I have recently updated to Jaunty and now use Gigolo to connect to network shares. It does not let you display available shares but using bookmarks makes life much easier.
Having just gone through the whole setup of gigolo, I had a couple comments:

_Browsing the network_
Gigolo does allow you to browse the network.  When I set it up, the network pane wasn't showing by default.  Once I enabled it (view, side panel, then choose 'network' instead of 'bookmark') it was a better day.

_Mods to make Gigolo work_
Also, I went through the setup to add my user account, and setup gigolo to use thunar properly and it worked fine for me (instructions noted earlier in thread).  The first time I tried it it worked.  After a reboot or two, it stopped working.  Later it was working.  So ... I don't know.  In the end I did create the shortcut.

I did not set Giolo to "Use Unix based volume manager", and it works fine.  I did copy this script, which is supposed to be for when Giolo accesses local file/folders, but I don't think I'll use Giolo for them ([http://wiki.xfce.org/gnomemount-replacement](http://wiki.xfce.org/gnomemount-replacement))

_Accessing shares issue_
One of the important issues I had when accessing network shares was access - when accessing a NTFS folder on a linux box I had setup and shared via a samba share, even though I set that folder to be accessed with "guest" it didn't work.  I needed to login with proper user credentials (put in the user name in Gigolo).

_Thunar problem_
Also - the mouse stopped working in Thunar.  For the longest time I thought it had to due with the Gigolo setup, but it's not.  There's a but in GTK apparently which causes Thunar to stop accepting mouse clicks in the main pane when: the view is 'detailed', and you double click an item.  Just switch to a different view (icon or list). ([http://bugzilla.xfce.org/show_bug.cgi?id=6230](http://bugzilla.xfce.org/show_bug.cgi?id=6230)).

_Future for Xubuntu/XFCE and Gigolo_
Finally, I see Gigolo is being included in the 'goodies' package for xfce.  I don't know if Xubuntu will take advantage of that, but it's there now for those that want it.  ([http://goodies.xfce.org/projects/applications/start#gigolo](http://goodies.xfce.org/projects/applications/start#gigolo))

---

### Post by ugm6hr on 2010-05-02
> **bluezeak said:**
> _Future for Xubuntu/XFCE and Gigolo_
Finally, I see Gigolo is being included in the 'goodies' package for xfce.  I don't know if Xubuntu will take advantage of that, but it's there now for those that want it.  ([http://goodies.xfce.org/projects/applications/start#gigolo](http://goodies.xfce.org/projects/applications/start#gigolo))

Xubuntu 10.04 includes Gigolo as a default (I think).  I recently installed, and don't recall having to manually add anything.

Haven't given it a proper test drive yet though...

I stand corrected - gvfs-fuse isn't installed, so I have still had to follow my [previous instructions]("http://ubuntuforums.org/showpost.php?p=8784294&postcount=207")

---

### Post by crackers8199 on 2011-01-12
can someone please help me get this working in xubuntu 10.10?  i've followed all the instructions on the first post, tried adding the -s switch to fusesmb, tried using gigolo...nothing has gotten me the ability to browse my windows home network.

i really want to stick with xubuntu, because it runs really well on this old inspiron 8100 laptop i'm posting from...but i need network browsing ability and i'm getting so frustrated with this at this point that i'm just about ready to smash the thing.

---

### Post by grantpet on 2011-03-08
i am really hoping you can help this newbie out.  using xubuntu xfce 4 now that i've switched from mint from frustration in connecting to my windows network shares.  never had to learn anything from the full version of ubuntu since it was all ultra handy.

i would like to transfer/stream files from the windows network and integrating into thunar seems to be my next step.  however i don't have XFCE's Applications -> System -> Shared Folders as indicated in the original post, so i'm stuck before i get started.

i think i have managed to get samba working properly as i can put files onto the pc from a win7 and winxp machine from my network.  folder seems to be fully functional.

after that is where i run into trouble. xsmbrowser will see the computers in my network (and show the network/pc name properly) and list them, but will fail to find them when accessed. pyneighborhood will see the network but fail to scan it; it allowed me to add the machines manually and will list all of the shares, but i cannot get it to mount via smb or cifs. i started gigolo, but got stopped on a step that wasn't matching early on.

i don't think i'm missing any of the minor associated proggies, but when i search for the ones listed in the posts they don't appear, but similar ones do and they are installed. no issues sharing on the windows side and firewalls are off.  don't see much mention of things to check on the windows side, i don't think netbios has to be installed on the win machines, but cannot find verification of that.

please help me find my missing step!!  tyvm in advance.  ):P

also have tomato firmware on my router.

---

### Post by yodabug on 2011-05-13
Thread started in 2007. Me answering in 2011--I'm always so freaking late!!!

I found this site last night after working 2 days to get samba working on lubuntu 11.04 (using xfce/thunar not lxde/pcmanfm).

I installed samba pckgs via synaptic
I installed fusesmb via synaptic

nothing worked after reboot..sigh...why is Samba so buggy after 20 years of constant development (please don't say Microsoft--if is NOT Microsoft that created Samba)? Just saying...

Anyhow, I went to this website: [http://ubuntu.swerdna.org/ubusambabrowse.html](http://ubuntu.swerdna.org/ubusambabrowse.html)

to get Samba working initially, then I went to this page (same website):

[http://ubuntu.swerdna.org/ubusambaserver.html#rwauth](http://ubuntu.swerdna.org/ubusambaserver.html#rwauth)

 and followed all the steps for: setting up security on those shares

Root can alter any Samba share/anytime/anyway
Users can alter their own files within the share
Users can read everything else

Everything works fine after 20 minutes of reading and 15 minutes of configuring/rebooting EXCEPT for a mounted ntfs drive which I can find in thunar=>network but cannot gain access to.

If anyone knows how to mount an ntfs share(from a dual boot config.) AND have that share available via samba to network users..well, boy that kinda info would definately deserve a couple of free beers...

Cheers!

---

### Post by Redsandro on 2011-05-13
Shares are an online thing, so if you've shared your NTFS drive in Windows, Lubuntu is not gonna know it. You'll just have to mount the entire partition as a filesystem, not as a share. You can share the filesystem like a share.

[B]sudo mkdir /mnt/ntfsthingie
sudo mount /dev/sd## /mnt/ntfsthingie[/B] <- I assume you know how it works
**sudo nano /var/lib/samba/usershares/ntfsthingie** <- code follows:

```
#VERSION 2
path=/mnt/ntfsthingie
comment=
usershare_acl=S-1-1-0:R
guest_ok=y
```

Not sure this is Lubuntucompatible, but it is samba.

I myself have given up on using samba. I mount everything with ssh.

**/usr/local/bin/sshfs.sh**```
#!/usr/bin/env bash
#sshfs mounter by Redsandro
#2010-07-17 #www.Redsandro.com
#Last edit" 2010-07-19
# Now you can have a desktop shortcut:
# gnome-terminal -x /usr/local/bin/sshfs.sh redsandro 192.168.1.10 / sshfs-redserv
# gnome-terminal -x /usr/local/bin/sshfs.sh redsandro RedServ /cygdrive sshfs-redsandro

#SELFNOTE: test works but if it fails it outputs error:
# ./sshfs.sh: line 12: [: too many arguments
#Why?

if [ ${1:+1} = 1 -a ${2:+1} = 1 -a ${3:+1} = 1 -a ${4:+1} = 1 ]; then
	USER=$1
	HOST=$2
	DEST=$3
	DIR=~/$4

	if [ ! -d $DIR ]; then
		mkdir $DIR
	fi

	echo "Mounting" "$USER"@"$HOST":"$DEST"
	echo "Mountpoint:" "$DIR"
	echo

	sshfs "$USER"@"$HOST":"$DEST" "$DIR"
	nautilus "$DIR"
	#sleep 10 # Give fusermount time to mount the share. Yes it can take some time for some computers with encrypted home dirs.

	echo
	echo "sshfs will unmount when terminal closes."
	echo "Press ENTER to close."
	read
	fusermount -u "$DIR"
else
	echo "Wrong parameters."
	echo "Usage:"
	echo "sshfs.sh user host host_dir mount_dir"
	echo "(sshfs user@host:host_dir ~/mount_dir)"
	echo "(NO TRAILING SLASH on mount_dir!)"
fi

```

Usage:
[B]sshfs.sh redsandro RedServ / redserv.fs
[/B]
That is:
sshfs.sh [username] [servername or ip address] [remote mountpoint] [local mountpoint in home dir]

---

### Post by jimav on 2011-12-02
> **Tazix said:**
> In XFCE's Applications -> System -> Shared Folders. (This should trigger ...


In Xubuntu 11.10 there does not appear to be an "Applications" menu,
nor is there a "Shared Folders" entry in the System menu.   Anybody know where this is in 11.10?

---

### Post by Redsandro on 2011-12-03
I haven't tried looking, the easiest way is to manually install samba. This way you can just copy configuration between updates.

*sudo apt-get install samba*

*sudo mousepad /etc/samba/smb.conf* (or your preferred editor)

add your shares below.

---

