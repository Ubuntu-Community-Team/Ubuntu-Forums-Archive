---
title: "Need help setting up NFS with FreeNAS ?"
date: 2008-12-29
forum: Server Platforms
---

### Post by handy on 2008-12-29
I require some help to finish setting up my FreeNAS installation.

I have FreeNAS installed on a 2Gb drive, currently with a 160Gb drive as IDE secondary master.

FreeNAS has been setup post install via its browser control software from the client.

I don't think I have got it wrong in the setup so far, but of course I could be mistaken. :-)

The problem I have is with setting up NFS; I have read what I have found on the web, which has always gone into client & server setup, which I find hard to relate to FreeNAS, as you only apply settings via the client browser interface.  Obviously I am unfamiliar with NFS.

So, I need a kind soul to hold my hand & take me through the NFS setup.  NFS is installed, the daemons are being called in the correct order, I think that my problems lie in the exports & fstab files.

Thanks for your time.

---

### Post by 2hot6ft2 on 2008-12-29
This may help

[http://ubuntuforums.org/showthread.php?t=218630&highlight=ridiculously+easy+file+sharing](http://ubuntuforums.org/showthread.php?t=218630&highlight=ridiculously+easy+file+sharing)

---

### Post by 2hot6ft2 on 2008-12-29
Or this one for NFS
[http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS+file+sharing](http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS+file+sharing)

---

### Post by 2hot6ft2 on 2008-12-29
In my exports on the laptop aka client I added this line
> /home/hot6ft2/Desktop/4lap-share 192.168.1.1/24(rw,no_root_squash,async)

4lap-share is the folder I'm sharing on the client

In my fstab on the client I added this line

> 192.168.1.10:/home/hot6ft2/Desktop/4dsk-share /home/hot6ft2/Desktop/4lap-share nfs rw,hard,intr 0 0

192.168.1.10 is the IP of the server
4dsk-share is the folder shared on the server

Can't get the servers info right now as it's hard at work. Hope that helps some.

---

### Post by handy on 2008-12-29
***@2hot6ft2:*** Thanks for the links & for taking the time to help. :-D

I Scroogled the other day, but did not get any Ubuntu links?

Anyway, I'll have a go with what you have presented me & see how I go...

I'll post my results here.

---

### Post by xjcannonx on 2008-12-29
Well i guess i'll share this because I finally got my NFS setup working correctly...

I had to install firestarter(from the repo's)(which i guess is just a gui for your iptables??) and i had to allow the connection from my laptop ...192.168.x.xxx

I thought at first it was all the /etc/exports or fstab but it turned out to be this

---

### Post by 2hot6ft2 on 2008-12-29
> **xjcannonx said:**
> Well i guess i'll share this because I finally got my NFS setup working correctly...

I had to install firestarter(from the repo's)(which i guess is just a gui for your iptables??) and i had to allow the connection from my laptop ...192.168.x.xxx

I thought at first it was all the /etc/exports or fstab but it turned out to be this
Good point. I also had to put the IP of the other pc in firestarter allow list before it would let them connect. That went both ways,,the servers ip in the clients firestarter and the other way around.

---

### Post by handy on 2008-12-29
Thanks xjcannonx I'll be aware of that also. :-)

I am running a standalone IPCop box with the Copfilter add-on, this is my firewall, router, gateway & am not using iptables on my client.

***[Edit:]** I have edited the above so as to be a little more informative. :-)*

---

### Post by handy on 2008-12-29
I will explain what I have happening on the FreeNAS box & my client as clearly as I can so that it will make it as easy as possible for help to be focussed where it is needed:

I have FreeNAS loaded onto the bootable 2Gb drive, I checked that all worked fine after installation, & then added the 160Gb drive as secondary master & mounted it as NAS-1.  This is where I want to store backups of important files & also eventually use Transmission via the browser client front end & run it as a torrent slave saving directly onto the NAS-1.
[B]
*[Edit:][/B] For those unfamiliar with FreeNAS it is a a very small (70Mb) FreeBSD distro that specialises in creating a NAS device out of a PC, once installed you configure it from a client machine via your browser. *

The IP of the FreeNAS box is 192.168.1.16

The IP of my client is 192.168.1.22

I have partition on the client called thevoid which if I need to share something with the FreeNAS box, the /mnt/thevoid partition would be the easiest.

Now exactly what do I need to put in the exports & fstab given that information?

I must admit to being very tired at the moment so I'm even a little slower than usual. ;-)

---

### Post by handy on 2008-12-29
I have added the following line to my fstab:

*192.168.1.16:/NAS-1 /mnt/nas-1  nfs     rw,hard,intr            0       0*

When I give the mount -a command I get the following error:

*mount.nfs: mount point /NAS-1 does not exist*

When I changed the fstab to the following:

*192.168.1.16:/ /mnt/nas-1  nfs     rw,hard,intr            0       0*

I get this error after issuing the mount -a command:

*mount.nfs: access denied by server while mounting 192.168.1.16:/*



I do not know what to add to my exports either, as I am confused by the FreeNAS way of doing things?

---

### Post by xjcannonx on 2008-12-29
So you are trying to mount NAS-1 and that is on your client machine which ip is 192.168.1.22 right? 

Well then should your fstab entry look like this:```
192.168.1.22:/NAS-1 /mnt/nas-1 nfs rw,hard,intr 0 0
```

So freeNAS on the 2gb drive acts as the server and the 160gb drive is the client right? And you want to use the freeNAS box(2gb drive)to access a file on the 'thevoid' partition on the 160gb drive?

---

### Post by 2hot6ft2 on 2008-12-30
Tell you what I took pics of my setting on both the desktop (server)
And the laptop (client) I'll attach them and you can look at the pics and see if it helps.

Like I said on the desktop (server) I'm sharing dsk-share, and lap-share (client) on the laptop. Makes it easier to keep track of things and where they are.

I probably didn't need to create the folder /media/dskserver on the desktop and mount it in the fstab, but it's working and I haven't had time to change it.

For what it's worth there it is. Hope you'll find it helpful.

And the shared folders are on the desktops of their respective machines so if I want to send something to the other I just drop it in the folder that's right there and get it from the other machine.

EDIT: Had pics that didn't belong in the attachment had to take them out as they didn't apply and fixed some of the settings.

---

### Post by xjcannonx on 2008-12-30
> **2hot6ft2 said:**
> Tell you what I took pics of my setting on both the desktop (server)
And the laptop (client) I'll attach them and you can look at the pics and see if it helps.

Like I said on the desktop (server) I'm sharing dsk-share, and lap-share (client) on the laptop. Makes it easier to keep track of things and where they are.

I probably didn't need to create the folder /media/dskserver on the desktop and mount it in the fstab, but it's working and I haven't had time to change it.

For what it's worth there it is. Hope you'll find it helpful.

And the shared folders are on the desktops of their respective machines so if I want to send something to the other I just drop it in the folder that's right there and get it from the other machine.

Nice job setting all that up for the OP, hope it helps him..

BTW I was just wondering because I am new to NFS, would it be better to specify the exact ip address instead of using 192.168.1.1/24 or 192.168.1.2/255.255.255.0 for security since you happen to actually know the ip?

And I was also reading that it is good to add 'portmap : ALL' to the /etc/hosts.deny before you add 'portmap : ipaddress' to the /etc/hosts.allow just for some added security.

---

### Post by xjcannonx on 2008-12-30
Have you seen this:> In order to support NFS root you need to make one custom modification until it is supported in the mainstream release. Download a backup of the FreeNAS configuration file and edit in your favourite text editor, e.g. notepad or gedit. Add the following section inside the <system> stanza, replacing the network parameters as appropriate. Note that the ampersand and quotation marks are escaped in order to validate as correct XML.

<shellcmd>echo &quot;/mnt/common -alldirs -network 10.82.6.0 -mask 255.255.255.0
-maproot=root&quot; &gt; /var/etc/exports &amp;&amp; killall -hup mountd</shellcmd>

Restore the new configuration file and FreeNAS will reboot and use the new configuration which is now ready for a diskless LTSP deployment.  from this website [[COLOR="Blue"]http://developer.novell.com/wiki/index.php/HOWTO:_Install_FreeNAS[/COLOR]]("http://developer.novell.com/wiki/index.php/HOWTO:_Install_FreeNAS")

---

### Post by Zack McCool on 2008-12-30
I guess I am not completely understanding the question here...   You are talking about the exports on the client.  No reason to export anything from the client...

>  I have FreeNAS installed on a 2Gb drive, currently with a 160Gb drive as IDE secondary master. 

OK, so your FreeNAS server has a 160GB drive shared to the LAN.  So, under the Disks|Management tab of the FreeNAS page, it should be listed.  Let's say it is /dev/da1 and mounted as data.  The page Disks|Mountpoint will show /dev/da1p1 with a name of data.

Now, you want to share it via NFS...   So, go to the Services|NFS page, and make sure the Enable check-box is ticked.  Click on the shares tab, and click the Plus icon to add a share.  For the path, you can click the ... button to browse to data, mine is at /mnt/data, then click OK.  Authorized network, this will be up to your network.  Mine is a 192.168.0.0 Class C network, so I have 192.168.0.0/24 entered.  The other options are at your discretion.

Once this is set up, and the system saved and restarted, the FreeNAS server should be good to go...   Now you have to mount that share on your client.

If you want it to be automatic, use fstab.  If not, you can either use fstab (noauto) or run a manual mount command.

```

sudo mount freenas:/mnt/data /mnt/freenas

```

You'll need /mnt/freenas created as a directory on your client machine, and if you don't have a DNS server running, you'll probably want to use the ip address in place of the word freenas.

For fstab, sudo nano /etc/fstab and enter the following (same caveats as above...)

```

freenas:/mnt/data /mnt/freenas nfs auto,defaults 0 0

```

and it will mount on boot.

Sorry if I misunderstand any of what you are trying to accomplish, but if I understood it right, you won't need to touch an exports file on either machine.

---

### Post by handy on 2008-12-30
> **xjcannonx said:**
> 
So you are trying to mount NAS-1 and that is on your client machine which ip is 192.168.1.22 right? 

NAS-1 is the 160Gb partition on the FreeNAS Server.

> **xjcannonx said:**
> 
Well then should your fstab entry look like this:```
192.168.1.22:/NAS-1 /mnt/nas-1 nfs rw,hard,intr 0 0
```

So freeNAS on the 2gb drive acts as the server and the 160gb drive is the client right? And you want to use the freeNAS box(2gb drive)to access a file on the 'thevoid' partition on the 160gb drive?

Yes & no. :-)

---

### Post by handy on 2008-12-30
> **Zack McCool said:**
> I guess I am not completely understanding the question here...   You are talking about the exports on the client.  No reason to export anything from the client...



OK, so your FreeNAS server has a 160GB drive shared to the LAN.  So, under the Disks|Management tab of the FreeNAS page, it should be listed.  Let's say it is /dev/da1 and mounted as data.  The page Disks|Mountpoint will show /dev/da1p1 with a name of data.

Now, you want to share it via NFS...   So, go to the Services|NFS page, and make sure the Enable check-box is ticked.  Click on the shares tab, and click the Plus icon to add a share.  For the path, you can click the ... button to browse to data, mine is at /mnt/data, then click OK.  Authorized network, this will be up to your network.  Mine is a 192.168.0.0 Class C network, so I have 192.168.0.0/24 entered.  The other options are at your discretion.

Once this is set up, and the system saved and restarted, the FreeNAS server should be good to go...   Now you have to mount that share on your client.

If you want it to be automatic, use fstab.  If not, you can either use fstab (noauto) or run a manual mount command.

```

sudo mount freenas:/mnt/data /mnt/freenas

```

You'll need /mnt/freenas created as a directory on your client machine, and if you don't have a DNS server running, you'll probably want to use the ip address in place of the word freenas.

For fstab, sudo nano /etc/fstab and enter the following (same caveats as above...)

```

freenas:/mnt/data /mnt/freenas nfs auto,defaults 0 0

```

and it will mount on boot.

Sorry if I misunderstand any of what you are trying to accomplish, but if I understood it right, you won't need to touch an exports file on either machine.

Thanks, yes you do understand my setup. 

I had mounted the 160Gb drive correctly & had the rest of FreeNAS set up correctly it would seem.  

I needed to know that I don't need exports, I was having trouble making sense of that file. (now I know why)

The mounting of the FreeNAS 160Gb storage drive (IP = 192.168.1.0/24  mount point = /mnt/NAS-1/ ) on my client so that I can use it is my problem.  I'll attempt to use your help to get there.

I'm getting closer thanks to everyone's help, I'm grateful for your patience. :-)

---

### Post by handy on 2008-12-30
The following command worked without complaint:

* sudo mount freenas:/mnt/NAS-1 /mnt/freenas*

So I'm automatically mounting the drive via the following line in fstab:

*freenas:/mnt/NAS-1 /mnt/freenas nfs     auto,defaults           0       0*

& I could use Worker to copy & delete a file, which I verified from the FreeNAS shell.

***_Fantastic_***, thanks all for sharing your valuable time & offering such great help. :KS

Now my next problem it to understand how to use the included Transmission torrent client as a slave on FreeNAS?  Apparently you can use a browser interface to control Transmission on the FreeNAS box.  I'll go searching for this now. :-)

---

### Post by handy on 2008-12-30
Well all is not perfect in the land of FreeNAS yet.

If I try to copy files over or look at the /freenas I have 100% cpu usage on 1 of the 2 cpu's of my client.

Htop says it is the following:

*/usr/sbin/famd -T 0 -c /etc/fam/fam.conf*

It does not seem to sort itself out it just stays up there at 100% I've tested it for over 20 minutes.

---

### Post by Zack McCool on 2008-12-30
> **handy said:**
> Well all is not perfect in the land of FreeNAS yet.

If I try to copy files over or look at the /freenas I have 100% cpu usage on 1 of the 2 cpu's of my client.

Htop says it is the following:

*/usr/sbin/famd -T 0 -c /etc/fam/fam.conf*

It does not seem to sort itself out it just stays up there at 100% I've tested it for over 20 minutes.

That is the package fam; a file alteration manager.  It isn't instalkled here, so I am not sure why it is doing things to your system.  I don't know why it would hang like that.

As far as I know, it isn't installed by default.  Was there a particular reason for installing it?

As for Transmission, just browse to the Transmission web page at [http://freenasip:9091](http://freenasip:9091) 

Once you log in, just click open, and add a .torrent file that you downloaded from a tracker site, and it will start up and get the download rolling.  Of course, you'll want to configure the port that it uses (little icon in the bottom left corner of the Transmissions web portal), and then configure your router to forward this port to the freenas ip...

---

### Post by handy on 2008-12-30
Thanks for your reply.

I'm running Arch/Xfce & fam is used by Xfce, though I may be able to do without it, I'll remove it from the auto start daemons line & see what happens.  Though I somehow think that there must be another reason causing this problem, as Gnome & KDE use fam as well.

---

### Post by Zack McCool on 2008-12-30
> **handy said:**
> Thanks for your reply.

I'm running Arch/Xfce & fam is used by Xfce, though I may be able to do without it, I'll remove it from the auto start daemons line & see what happens.  Though I somehow think that there must be another reason causing this problem, as Gnome & KDE use fam as well.

I am using Gnome w/Hardy, and fam is not installed.  I agree, though, that there must be some other reason, I just wondered what the use of fam was, in particular, since it's not installed here, and I've never really seen it referenced before.

Certainly not saying you should bastardize your install...   ;)

---

### Post by handy on 2008-12-30
> **Zack McCool said:**
> I am using Gnome w/Hardy, and fam is not installed.  I agree, though, that there must be some other reason, I just wondered what the use of fam was, in particular, since it's not installed here, and I've never really seen it referenced before.

Certainly not saying you should bastardize your install...   ;)

The following is from the Arch wiki:

[I]The File Alteration Monitor (FAM) daemon is used by Desktop Environments, such as a GNOME, Xfce and KDE, to monitor and report changes to the filesystem.

For example, FAM is used to:

    * Automatically update application menus when new applications are installed
    * Refresh file manager listings when the contents of a directory have changed [/I]
_____________

I use Worker as my file manager & it doesn't automatically update directory listings anyway, I have to tell it to refresh, so I would rarely miss fam.

I have removed the daemon so it is not being started at bootup.  I just opened the /freenas/ & had a look with Worker, then told it to copy a directory with many small files in it from my client to the /freenas/ box.  It still froze Worker.  Now when I look in Htop, there is nothing hogging CPU cycles to give me any clue as to where to look next. :-)

I also cd'd to /mnt/freenas/ & did an ls from the Terminal & the Terminal is just doing nothing now...  Nothing showing up in Htop either.

Ok, I just checked back to see how it was going & saw the ls results appear. Something is really slowing things down.  Any ideas?

***[Edit:]** Things are fast as lightening at the FreeNAS box's bash prompt, there is no slow down there.*

---

### Post by handy on 2008-12-30
I just rebooted & then went back into /freenas deleted the directory, & the nested directory that held a 23Mb file in it.  

Then copied the same parent directory containing many subdirectories, some with many files, across from my client to /freenas . 

As I have seen before, the parent directory & the first sub-directory are created & the 23Mb file is copied across quite quickly & then that is it, Worker becomes unresponsive & stays crashed.

---

### Post by handy on 2008-12-30
I found that I had set the client's */etc/hosts.allow* as though it was a server, so I deleted those lines & that has stopped fam from freaking out when I try to access files with Worker.  

It has not stopped Worker from crashing after copying the first file of many, or Terminal from taking a far to long to read information on the /freenas ?

---

### Post by handy on 2008-12-30
Thanks for all those photo's by the way ***2hot6ft2***, I have gone through & used the appropriate client side settings.  They were all very helpful, & will also help me greatly when I need to set up a NFS server in the future also. :KS

I just successfully copied a directory with a nested sub-directory that held two more nested directories, each of which held eight & nine picture files. :-)

They copy functioned ok, it may have been a little slow, I can't say for sure at this point.

The directory that I have been consistently failing with previously, is over 13Gb in size with many directories, nested directories & lots of files in many of these directories.  It would seem that this combination of characteristics may be causing my system to break. 

If this is what's happening how can I fix it?

---

### Post by 2hot6ft2 on 2008-12-30
> **xjcannonx said:**
> Nice job setting all that up for the OP, hope it helps him..

I took all the pics since it was my first time setting something like this up and it would help me if I had to do it all over agin. Also made for an easy way to go back thru and look at what I had without opening everything back up.
> **xjcannonx said:**
> BTW I was just wondering because I am new to NFS, would it be better to specify the exact ip address instead of using 192.168.1.1/24 or 192.168.1.2/255.255.255.0 for security since you happen to actually know the ip?

And I was also reading that it is good to add 'portmap : ALL' to the /etc/hosts.deny before you add 'portmap : ipaddress' to the /etc/hosts.allow just for some added security.
And you're absolutely right about both points. I found the guide that I linked to AFTER trying to follow another guide that had me all screwed up and once it was up and running my eyes were hurting so I just took all the pics and figured I would sort out my mistakes the next day but never got around to it.

Maybe I'll take the time to fix it today. Thanks for pointing out some I wasn't thinking of changing that I should.
> **handy said:**
> Thanks for all those photo's by the way ***2hot6ft2***, I have gone through & used the appropriate client side settings.  They were all very helpful, & will also help me greatly when I need to set up a NFS server in the future also. :KS
You're welcome. Glad you found at least a little help from my set up.

---

### Post by 2hot6ft2 on 2008-12-30
Just noticed something important in the pics I attached.

In the dsk-pics folder
THIS DOESN'T BELONG THERE dsk-pingScreenshot-fstab-gedit.png
That's my brother fstab he sent me the pic so I could see what he had since he's having problems with a couple drives. In case no one caught it he put a couple spaces in the volume label of the last drive (a big NO NO) so it added "\040" for each space (aside from having a real long volume label name).

I'll remove that pic and go back and edit the attachment in that post.

EDIT: Found 2 more that didn't belong in there.

---

### Post by 2hot6ft2 on 2008-12-30
For anyone else following this trying to set up 2 ubuntu pc's to share a folder using NFS I have taken the advice of xjcannonx and fixed my setup so now all the pics are right (I hope) and are attached.

If anyone finds a problem in my setup feel free to point it out. If everything looks right I may even make a how to on it since I had to find a lot out by trial and error myself. This should have only taken 15 to 30 minutes tops.

Thanks and enjoy.

---

### Post by handy on 2008-12-30
The problem I face is that setting up FreeNAS with NFS is different than just setting up a normal NFS client - server relationship, as you do not touch the settings on the FreeNAS machine directly, only via the browser interface from a client.

There are definitely things very wrong with my setup, so I really need someone with FreeNAS - NFS experience to help me set things right.

---

### Post by windependence on 2008-12-31
> **handy said:**
> The problem I face is that setting up FreeNAS with NFS is different than just setting up a normal NFS client - server relationship, as you do not touch the settings on the FreeNAS machine directly, only via the browser interface from a client.

There are definitely things very wrong with my setup, so I really need someone with FreeNAS - NFS experience to help me set things right.

Greg,

I think you are a bit confused as to the concept of the FreeNAS box.

You should just view the FreeNAS box in your mind as a big hard drive. Nothing else shoul be run on that box including any GUIs other than the web interface which is already installed by FreeNAS. 

Your torrent client would be installed on your client box not on the FreeNAS box, but you can store your torrents on a share on the FreeNAS box just as you would any other hard drive if it was on your system. It's a simple matter to set up your exports on the FreeNAS box, and this must be done through the web interface. Trying to do anything through the CLI on the FreeNAS box will most likely mess up your setup if you aren't familiar with FreeBSD. Even if you are, as I am, you still want to set up everything from the interface as that will keep everything consistent. 

It's a great OSS application and I know you will be happy with it. People on this thread have given you some excellent advice, but of you need help I will try to monitor this thread as well.

-Tim

---

### Post by Zack McCool on 2008-12-31
> **windependence said:**
> 
Your torrent client would be installed on your client box not on the FreeNAS box, but you can store your torrents on a share on the FreeNAS box just as you would any other hard drive if it was on your system.

Actually, FreeNAS has a Torrent client built in (Transmissions), and includes a web interface for it.  

Back to the main problem, I do have experience with FreeNAS.  I use it here, but I have not had the problems you are having with it.  I have 2 drives on that system.  One small one for the OS, and a larger one for the Data, much like you.  I have it configured to provide NFS, SAMBA and iSCSI services.  

The big difference is that I am not having any problems with anything hanging when I copy to it.

So, we have to figure out if the problem is with the FreeNAS server, or the Ubuntu client...

My guess is a configuration issue on the client.  And I would suggest booting with a LiveCD, mount the FreeNAS NFS share from there, and try a large file copy to see if the results are any different.  If it is better, the problem is your Ubuntu box, and we can start trying to figure that out.  If it still has a problem, then the problem is the FreeNAS server, and we'll have to delve more deeply into that...

---

### Post by windependence on 2008-12-31
Hey Zack, I'm kinda embarrassed to say I am very familiar with FreeNAS and I didn't know it had a torrent client built in! Thanks man, even though I usually use Azureus. 

Your advice to Greg has been right on. I had promised to help him with his set up but I have been swamped with other projects. I am sure he is glad for the help. It's nice to see someone else here with *BSD experience.

-Tim

---

### Post by handy on 2008-12-31
> **windependence said:**
> 
Greg,

I think you are a bit confused as to the concept of the FreeNAS box.

You should just view the FreeNAS box in your mind as a big hard drive. Nothing else shoul be run on that box including any GUIs other than the web interface which is already installed by FreeNAS. 

Sorry if my description is not clear, but I am running nothing else on the FreeNAS box than comes with the standard installation, & I only use the browser interface to interact with it, apart from when I have used the Terminal to verify that what I have done from the client really did happen on the FreeNAS box.

> **windependence said:**
> 
Your torrent client would be installed on your client box not on the FreeNAS box, 

That is how I have done it.

> **windependence said:**
> 
but you can store your torrents on a share on the FreeNAS box just as you would any other hard drive if it was on your system. It's a simple matter to set up your exports on the FreeNAS box, and this must be done through the web interface. Trying to do anything through the CLI on the FreeNAS box will most likely mess up your setup if you aren't familiar with FreeBSD. Even if you are, as I am, you still want to set up everything from the interface as that will keep everything consistent. 

I understand this & this is how I have been operating.  Though I have not had the opportunity yet to attempt to set up Transmission for the job.

> **windependence said:**
> 
It's a great OSS application and I know you will be happy with it. People on this thread have given you some excellent advice, but of you need help I will try to monitor this thread as well.

-Tim

Thanks Tim. :-)

I do need help as the copying of files to /freenas is not functioning properly. It crashes Worker usually & takes forever for anything to happen when done via the Terminal?

I think FreeNAS is set up properly.
If NFS is not set up properly, it is very close, but something is still very wrong.

---

### Post by windependence on 2008-12-31
Just a question. What is Worker?

-Tim

---

### Post by handy on 2008-12-31
> **Zack McCool said:**
> 
Actually, FreeNAS has a Torrent client built in (Transmissions), and includes a web interface for it.  

The web interface is a part of any installed Transmission these days.

What seems to be incorporated into FreeNAS is the bittorrent service to work with it.  That is my understanding at this stage.

> **Zack McCool said:**
> 
Back to the main problem, I do have experience with FreeNAS.  I use it here, but I have not had the problems you are having with it.  I have 2 drives on that system.  One small one for the OS, and a larger one for the Data, much like you.  I have it configured to provide NFS, SAMBA and iSCSI services.  

The big difference is that I am not having any problems with anything hanging when I copy to it.

So, we have to figure out if the problem is with the FreeNAS server, or the Ubuntu client... 

I'm using Arch/Xfce.

> **Zack McCool said:**
> 
My guess is a configuration issue on the client.  And I would suggest booting with a LiveCD, mount the FreeNAS NFS share from there, and try a large file copy to see if the results are any different.  If it is better, the problem is your Ubuntu box, and we can start trying to figure that out.  If it still has a problem, then the problem is the FreeNAS server, and we'll have to delve more deeply into that...

Good thinking, I'll have a go at that.

---

### Post by Zack McCool on 2008-12-31
> **windependence said:**
> Hey Zack, I'm kinda embarrassed to say I am very familiar with FreeNAS and I didn't know it had a torrent client built in! Thanks man, even though I usually use Azureus. 

Your advice to Greg has been right on. I had promised to help him with his set up but I have been swamped with other projects. I am sure he is glad for the help. It's nice to see someone else here with *BSD experience.


Heh...   My BSD experience is a bit lacking.  I installed it as a VM a few weeks ago, so I do have it here to play with (freebsd), but I haven't gotten to any real proficiency with it, yet.  FreeNAS, OTOH, is a piece of cake.  The web interface for it is VERY well done.  I also only have that running in a VM right now, but there is a PC that the kids have been using until Christmas Day that is planned for re-purposing, which will include adding a SATA controller and a few BIG HD's and a FreeNAS installation.  

It is one of the best written pieces of *nix appliance software I have used.

---

### Post by handy on 2008-12-31
> **windependence said:**
> Just a question. What is Worker?

-Tim

It is a highly configurable directory utility inspired by Jonathan Potter's wonderful Directory Opus (Dopus) that everyone used to use on the AmigaOS way back when.

It's only dependency is the X11 libraries.

*_[http://www.boomerangsworld.de/cms/worker/index?lang=en](http://www.boomerangsworld.de/cms/worker/index?lang=en)_*

---

### Post by Zack McCool on 2008-12-31
> **handy said:**
> 
What seems to be incorporated into FreeNAS is the bittorrent service to work with it.  That is my understanding at this stage.


Your understanding on this is spot on...   ;)

> 
I'm using Arch/Xfce.


Ahhh.  I have not used Arch at all.  That explains the different packages you are using that I don't have running here...   ;)  

> 
Good thinking, I'll have a go at that.

I am expecting it to turn out to be something simple on the client end, that is going to be a pain in the *ss to find...   But certainly keep us posted...

---

### Post by handy on 2008-12-31
> **Zack McCool said:**
> 
Your understanding on this is spot on...   ;) 

That helps, my confidence is a little shaky at the mo'. :lolflag:

> **Zack McCool said:**
> 
I am expecting it to turn out to be something simple on the client end, that is going to be a pain in the *ss to find...   But certainly keep us posted...

Well, I just booted up the Sabayon4 LiveDVD & stumbled around in that unfamiliar territory, managed to do an ls on the /freenas which had quite a delay the same as I have been experiencing from Arch, I tried copying files & froze the directory utility in Sabayon4 as well.

So, I shut down the FreeNAS box & changed its NIC, as it has 2 onboard, I turned off the previous one & turned the new one in the BIOS, set it up in FreeNAS & thought bugger Sabayon, & booted up Arch again, & am currently copying the 11.3Gb monster directory full of audio books across to the /freenas. :-D

There are 1642 files inside of the 11.3Gb directory being copied, & many nested directories, it has been going for about 5 minutes & says that it will take another 120 minutes.

How does that look for speed?

---

### Post by handy on 2008-12-31
I had actually gone around earlier today & edited out the changes that 2hot6ft2 had advised in his photo's.

So my system is running on the daemons & fstab auto mounting /mnt/freenas

So, it may possibly be configured to run more efficiently?

---

### Post by Zack McCool on 2008-12-31
> **handy said:**
> 
There are 1642 files inside of the 11.3Gb directory being copied, & many nested directories, it has been going for about 5 minutes & says that it will take another 120 minutes.

How does that look for speed?

First thing first, let's see if it copies without hanging...   ;)

As for speed, I'd wait until it is complete to judge how well it did.  Those estimates always seem to be miles off.

Are you using a 100Mb/s NIC?  I usually see about 6-7 MB/s transfer speed max on a 100Mb link using NFS or SAMBA.  With an SSHFS transfer, it'll usually get over 10...

---

### Post by handy on 2008-12-31
> **Zack McCool said:**
> 
First thing first, let's see if it copies without hanging...   ;) 

It is still going strong, 42% done at this stage. :-)

It has never behaved like this in its short history, I'm feeling very confident that the other on-board NIC has failed.

> **Zack McCool said:**
> 
As for speed, I'd wait until it is complete to judge how well it did.  Those estimates always seem to be miles off.

Are you using a 100Mb/s NIC?  I usually see about 6-7 MB/s transfer speed max on a 100Mb link using NFS or SAMBA.  With an SSHFS transfer, it'll usually get over 10...

Yes I'm using 100Mbit, I didn't put a stop watch on it. :-) 

Worker says that I'm copying at about 1975kb/s.  The LAN speed seems to be the bottleneck.

---

### Post by handy on 2008-12-31
I have a question on another aspect of FreeNAS:

How reliable is software RAID-5?

I have 3 x 80Gb drives, 2 are versions of the Western Digital Caviar drives - WD800 (they don't say 7200rpm so I will have to Scroogle it) their ages are 12 months apart, & I have an IBM Deskstar 80Gb which is definitely 7200rpm.

If the speeds are different will they be accepted into an array?

---

### Post by handy on 2008-12-31
It finished copying the directory, Worker wrote, that it averaged 2011kb/s.

---

### Post by 2hot6ft2 on 2008-12-31
> **handy said:**
> I had actually gone around earlier today & edited out the changes that 2hot6ft2 had advised in his photo's.:confused:
I don't recall advising anything. I only offered the pics so you could see how mine is set up using NFS on my 2 ubuntu pc's for sharing files, in the hopes that you could find something there to help you figure out what was wrong with your NFS part of the setup. If anything.

You're using NFS with "FreeNAS" which is something I am completely unfamiliar with so I would never "advise" you on how to set it up.

No harm, no foul. I just wanted to make that clear.

Glad to see you're finally getting some help fixing it up.:)

---

### Post by handy on 2008-12-31
> **2hot6ft2 said:**
> 
:confused:
I don't recall advising anything. I only offered the pics so you could see how mine is set up using NFS on my 2 ubuntu pc's for sharing files, in the hopes that you could find something there to help you figure out what was wrong with your NFS part of the setup. If anything. 

Please forgive my inappropriate description of your greatly appreciated assistance ***2hot6ft2***? It was written approaching the midnight hour & I was very tired & getting lazier of mind by the second. :-) 

I actually used some of the client settings you sent in the screenshots as a guide, specifically */etc/hosts.allow* & */etc/hosts*.  

They made no noticeable difference at the time, though half an hour or so later there was a further deterioration in the behaviour of the NFS connection between the client & /freenas, so clutching at straws, I commented the aforementioned changes out. 

I now know that it was a hardware problem caused by an on-motherboard NIC (as noted in a previous post) that was responsible for my NFS problems. 

> **2hot6ft2 said:**
> 
You're using NFS with "FreeNAS" which is something I am completely unfamiliar with so I would never "advise" you on how to set it up. 

No harm, no foul. I just wanted to make that clear. 

As explained above, I took what I thought was appropriate from a couple of your great, client side screenshots, & unfortunately in that previous post I misused the word advised for what was in truth, information offered by you in the hope that it may somehow be of assistance to me by growing my understanding of NFS. Which happily it has done. ;-)

> **2hot6ft2 said:**
> 
Glad to see you're finally getting some help fixing it up.:)

Yes, that NIC really did add some time to the job. I expect that it had more than just me scratching my head a little. :lolflag: 

Now I can uncomment the additions I made from looking at your screenshots. They look to me as though they are included as added insurance for the client finding the server.  Is that correct?

This is what I have added to my client machines /etc/hosts.allow :

*portmap : 192.168.1.14*

& this to its /etc/hosts :

*192.168.1.14    freenas*

192.168.1.14 is the new IP address that FreeNAS gave to its new (the 2nd on-motherboard) NIC that it is now using.

---

### Post by windependence on 2008-12-31
If you bond the NICs you can get even faster throughput. I have three NICs in mine. Fiber would be best but I am not wealthy enough.

-Tim

---

### Post by Zack McCool on 2008-12-31
> **handy said:**
> I have a question on another aspect of FreeNAS:

How reliable is software RAID-5?

I have 3 x 80Gb drives, 2 are versions of the Western Digital Caviar drives - WD800 (they don't say 7200rpm so I will have to Scroogle it) their ages are 12 months apart, & I have an IBM Deskstar 80Gb which is definitely 7200rpm.

If the speeds are different will they be accepted into an array?

Should work fine.  Software raid doesn't care about even the size of the drives, just the partitions.  You could have 3 partitions on the same disk, and it should work, though it would be useless for any real-world work...

I haven't used it in FreeNAS, but the RAID components they use are the tried and true *nix components, so it should be plenty reliable...

---

### Post by Zack McCool on 2008-12-31
> **handy said:**
> It finished copying the directory, Worker wrote, that it averaged 2011kb/s.

That seems a bit slow to me.  I would expect it to be at least 3x that, but you'll probably have to mess with the mount parameters to get better.  Are you seeing any errors in the logs on your linux client?

---

### Post by handy on 2008-12-31
> **windependence said:**
> If you bond the NICs you can get even faster throughput. I have three NICs in mine. Fiber would be best but I am not wealthy enough.

-Tim

So Tim do you mean that if I add another NIC to the FreeNAS box, I can bond it (which I take to mean have the 2 NICs share one IP address, which will increase throughput on that machine?

If so, the problem I have with my client is that it can not have another NIC installed, so under these circumstances would adding another NIC to FreeNAS be of any benefit?

> **Zack McCool said:**
> Should work fine.  Software raid doesn't care about even the size of the drives, just the partitions.  You could have 3 partitions on the same disk, and it should work, though it would be useless for any real-world work...

I haven't used it in FreeNAS, but the RAID components they use are the tried and true *nix components, so it should be plenty reliable...

Thanks for that info' Zack, that is a big help to me at this stage of the game. 

> **Zack McCool said:**
> That seems a bit slow to me.  I would expect it to be at least 3x that, but you'll probably have to mess with the mount parameters to get better.  Are you seeing any errors in the logs on your linux client?

What I have just spent some time doing is adding 1024 to the following line in the /etc/conf.d/nfs file until it started to slow down, so I'm using the optimum size currently:

*STATD_OPTS="-p 34813 -o 34814"*

This setting increase the speed to roughly 2300k/s which is still not fast enough.

I'll see what I can learn about parameters to use in fstab that can speed up the show.

Following is the line I'm currently using, which looks pretty vanilla to me:

*freenas:/mnt/NAS-1 /mnt/freenas nfs     auto,defaults           0       0*
 

I'm thinking of buying an HP 8 port giga' speed switch.  I have some cat5e cable here & RJ45 terminators & the crimping tool. Is the wiring order identical to that for standard cat5 networking cables?  If so I can make my own & this should give me a speed boost too, though I naturally want the maximum I can get by tuning the system too.

What are your thoughts on this guys?

---

### Post by handy on 2009-01-01
I've chased around the internet looking for info' on optimising NFS & options used when mounting NFS in fstab, & really didn't come up with too much.

The line in my fstab is now as follows:

*freenas:/mnt/NAS-1 /mnt/freenas nfs     defaults,hard,intr,noatime      0       0*

I tested my copy speed again from client to /freenas & it was no better, though the test was only a 730Mb file in a directory, I expect that it is probably faster copying lots of small files with noatime being used.

[I]**[Edit:]** I changed the /freenas drive Transfer Mode from Auto to UDMA-133 in the FreeNAS control GUI & tested the copy of the 730Mb file again & it was around 2300k/s so the Auto setting was working as it should. 

I copied a 350Mb directory containing 5 subdirectories & 60 files averaging around the 5.5Mb size, the average copy speed was 1830K/s.[/I]

---

### Post by Zack McCool on 2009-01-01
Hmmm.  Just copied 5 files/3.6 GB total.  Avg speed about 7600 KB/s.  Since this is running in a VM, I would ecxpect slightly higher than that if it were on bare metal...  Also, to make sure we are on the same terms, installed worker to do the copy...

I don't have any special mounting information set up, so I can't give good advice on tweaking your connection.  

You did say that both NIC ports are on the system board in the FreeNAS box, and you suspect that one of them died?  Usually, if there are multiple NIC ports, they use the same controller chip.  Is it possible to add a separate NIC to the machine and disable the onboard ones?  Perhaps the NIC is the culprit...

---

### Post by handy on 2009-01-01
I just read an article in the FreeNAS online help knowledge-base:

*[http://www.freenaskb.info/kb/?View=entry&EntryID=129](http://www.freenaskb.info/kb/?View=entry&EntryID=129)*

Which sorted out my slow network. :-D

*I had set my FreeNAS / LAN / Advanced Configuration / type / 100baseTX*

When I changed the type to *autoselect* to see if that would make a difference. I had to reboot the FreeNAS box & I then tested with the copy of the 350Mb 5.5k files & I got near to 11Mb/s. (very happy now)

With the 730Mb file it was 11.4Mb/s.

I will have to go through & test my settings in the /etc/conf.d/nfs & see if the optimum setting is different now.

---

### Post by Zack McCool on 2009-01-01
> **handy said:**
> I then tested with the copy of the 350Mb 5.5k files & I got near to 11Mb/s. (very happy now)

With the 730Mb file it was 11.4Mb/s.

I will have to go through & test my settings in the /etc/conf.d/nfs & see if the optimum setting is different now.

Much better!  Nice to hear that you got it sorted out!

---

### Post by windependence on 2009-01-01
> **handy said:**
> So Tim do you mean that if I add another NIC to the FreeNAS box, I can bond it (which I take to mean have the 2 NICs share one IP address, which will increase throughput on that machine?

If so, the problem I have with my client is that it can not have another NIC installed, so under these circumstances would adding another NIC to FreeNAS be of any benefit?



Thanks for that info' Zack, that is a big help to me at this stage of the game. 



What I have just spent some time doing is adding 1024 to the following line in the /etc/conf.d/nfs file until it started to slow down, so I'm using the optimum size currently:

*STATD_OPTS="-p 34813 -o 34814"*

This setting increase the speed to roughly 2300k/s which is still not fast enough.

I'll see what I can learn about parameters to use in fstab that can speed up the show.

Following is the line I'm currently using, which looks pretty vanilla to me:

*freenas:/mnt/NAS-1 /mnt/freenas nfs     auto,defaults           0       0*
 

I'm thinking of buying an HP 8 port giga' speed switch.  I have some cat5e cable here & RJ45 terminators & the crimping tool. Is the wiring order identical to that for standard cat5 networking cables?  If so I can make my own & this should give me a speed boost too, though I naturally want the maximum I can get by tuning the system too.

What are your thoughts on this guys?

Yes, you can bond the nics on both sides for better throughput but make sure they are set to be in parallel and not round robin as that is only good for failover. 

For speed you may want to consider trying iSCSI, although from what I have read NFS is as fast and in some cases faster. The only way you would know is to try it with your setup. I used NFS because it is more widely supported than iSCSI at present and I don't know what my future needs will be from the SAN.

CAT5E is fine, but if you can dig up some CAT6, that would be best even though on short runs I don't think it would make much difference. Wire order is the same as always.

A good managed switch might also help. I was fortunate enough to "inherit" a Cisco 48 port managed switch from a client and it helped a bunch but you could do it through a simple managed SOHO switch also.

-Tim

---

### Post by ranjithbiotech on 2009-01-01
HI dear,
I am using ubundu. I want download movies from internet.
But that movies are torrent links. I am unable to download. How to download that?
Is it possible to install torrent on ubuntu?
If possible tell the way please.
Thanks friends

---

### Post by windependence on 2009-01-01
> **ranjithbiotech said:**
> HI dear,
I am using ubundu. I want download movies from internet.
But that movies are torrent links. I am unable to download. How to download that?
Is it possible to install torrent on ubuntu?
If possible tell the way please.
Thanks friends

You need to install a torrent client such as Vuze to do this. 

We really should start a new thread for this. Mods, can you split this topic?

-Tim

---

### Post by Zack McCool on 2009-01-01
He already started a new topic, not sure why he put it in here, too.  Mods may want to just delete this...   ;)

---

### Post by handy on 2009-01-01
> **windependence said:**
> 
Yes, you can bond the nics on both sides for better throughput but make sure they are set to be in parallel and not round robin as that is only good for failover. 

My client is an iMac, so I have no way of adding another NIC to it, I guess there would still be an advantage of having 2 NICs bonded on the FreeNAS box, if my wife is also storing data on it?

> **windependence said:**
> 
For speed you may want to consider trying iSCSI, although from what I have read NFS is as fast and in some cases faster. The only way you would know is to try it with your setup. I used NFS because it is more widely supported than iSCSI at present and I don't know what my future needs will be from the SAN. 

Thanks Tim, I'll have a look at that.

> **windependence said:**
> 
CAT5E is fine, but if you can dig up some CAT6, that would be best even though on short runs I don't think it would make much difference. Wire order is the same as always. 

In my office cable length would be less than a meter, the length of cable to my wife's office is about 8 meters, though she will be a light user of this system. 

Thanks for the verification on the cables, it is great talking to people who know. :-D

> **windependence said:**
> 
A good managed switch might also help. I was fortunate enough to "inherit" a Cisco 48 port managed switch from a client and it helped a bunch but you could do it through a simple managed SOHO switch also. 

-Tim


How does the HP procurve 1800 8G look to you?

***_[http://h50229.www5.hp.com/web/hp/procurve/au/products/switches/ProCurve_Switch_1800_Series/overview.htm](http://h50229.www5.hp.com/web/hp/procurve/au/products/switches/ProCurve_Switch_1800_Series/overview.htm)_***

I have an IPCop box which is my firewall/proxy/router which it is my understanding can happily run on 10/100 switch with no slowing down of anything it deals with on the LAN.  So I believe I could plug an 8 port gigabit switch into the 10/100 switch with no degradation of function, does that sound right to you?

---

### Post by windependence on 2009-01-01
Yeah, too bad on the iMac. I run a Macbook Pro here as my laptop so I understand how the Mac fits in here. Yes, having the bonded NICS only on one end will still help to open up traffic and reduce collisions.

The HP switch looks perfect for what you are doing. You sure can plug the 10/100 switch into the GIG switch, just remember that any traffic routed through that switch will always be no more than 100mbs.

Good luck!

-Tim

---

### Post by handy on 2009-01-01
> **windependence said:**
> 
Yeah, too bad on the iMac. I run a Macbook Pro here as my laptop so I understand how the Mac fits in here. Yes, having the bonded NICS only on one end will still help to open up traffic and reduce collisions. 

Good, thanks, I'll investigate what is involved in the bonding procedure & have a go.  I only have some 10/100 NICs here but it is all good practice as I go through this learning process. :-)

> **windependence said:**
> 
The HP switch looks perfect for what you are doing. 

That's great to hear.

> **windependence said:**
> 
You sure can plug the 10/100 switch into the GIG switch, just remember that any traffic routed through that switch will always be no more than 100mbs.

Good luck!

-Tim

I was thinking that if I run out of ports on the gigabit switch in the future, I could plug the IPCop box & the old LJ-5 printer (& anything else that doesn't need the bandwidth) into the 10/100 switch & then the 10/100 could plug into the gigabit switch.  

My internet could never use a 10Mbit NIC's bandwidth let alone a 100Mbit NIC, so I should be safe.

Anyway, thanks heaps for your kind assistance Tim.

---

### Post by handy on 2009-01-03
Can someone please interpret the following for those of us who are still ignorant of the nuances of bash scripting?

***_[http://apps.sourceforge.net/phpbb/freenas/viewtopic.php?f=12&t=324](http://apps.sourceforge.net/phpbb/freenas/viewtopic.php?f=12&t=324)_***

Doing so will give us (me), the capacity of having a *_watch_* directory on the FreeNAS server, which will in turn allow us (me) to shut down our client & go to bed using half as much electricity. :-)

---

### Post by Zack McCool on 2009-01-03
The script basically just checks a pre-determined directory to see if there are any .torrent files there.  If there are, it opens them in Transmission, and deletes the .torrent file so that it doesn't get opened again.

Then, you run it using a cron job, to make it run every 5 minutes (or however often you wish).

So, you could download the .torrent file from your desktop, drop it onto the NAS in the pre-defined folder, then shut down your desktop and the torrent will download...

---

### Post by windependence on 2009-01-03
> **handy said:**
> Can someone please interpret the following for those of us who are still ignorant of the nuances of bash scripting?

***_[http://apps.sourceforge.net/phpbb/freenas/viewtopic.php?f=12&t=324](http://apps.sourceforge.net/phpbb/freenas/viewtopic.php?f=12&t=324)_***

Doing so will give us (me), the capacity of having a *_watch_* directory on the FreeNAS server, which will in turn allow us (me) to shut down our client & go to bed using half as much electricity. :-)

I seriously doubt this is going to gain you much, and it could actually add complexity to your setup that you don't really need.  You definitely couldn't do this if you wanted to run VMs on the NAS box which is what I do with mine. I just don't think the result is worth the effort for maybe what, a few bucks a year if that?

-Tim

---

### Post by Zack McCool on 2009-01-03
Why wouldn't you be able to run VM's if this script was scheduled?  They shouldn't have anything to do with each other...   The bittorrent client is running anyhow, so it should be fine...

---

### Post by handy on 2009-01-03
> **Zack McCool said:**
> The script basically just checks a pre-determined directory to see if there are any .torrent files there.  If there are, it opens them in Transmission, and deletes the .torrent file so that it doesn't get opened again.

Then, you run it using a cron job, to make it run every 5 minutes (or however often you wish).

So, you could download the .torrent file from your desktop, drop it onto the NAS in the pre-defined folder, then shut down your desktop and the torrent will download...

THAT is exactly what I want to be able to do.

> **windependence said:**
> I seriously doubt this is going to gain you much, and it could actually add complexity to your setup that you don't really need.  You definitely couldn't do this if you wanted to run VMs on the NAS box which is what I do with mine. I just don't think the result is worth the effort for maybe what, a few bucks a year if that?

-Tim

Sorry, my dumb rrr's doesn't even know what VMs even means?

> **Zack McCool said:**
> Why wouldn't you be able to run VM's if this script was scheduled?  They shouldn't have anything to do with each other...   The bittorrent client is running anyhow, so it should be fine...

My only thought on this, & I really don't know what I am talking about; is that windependence, you are are looking at the situation from a professional, business perspective & perhaps(?) Zack McCool, is looking at it from a different angle?

But as I said, I'm the one looking at it from near on total ignorance. :-)

---

### Post by handy on 2009-01-03
I don't understand just how I set that script up so that I can just drop a .torrent file into the directory & it will work.

Do I have to put it into the FreeNAS box or into the Client?

& how do I call it?

***[Edit:]**  Yeh, I know, I'm dumb a dog sheet. :redface:*

---

### Post by windependence on 2009-01-03
Sorry Greg. Yes, I have a tendency to look at all of this server stuff from a professional production environment view. Sometimes that gets in the way when someone is setting up a more casual home use server. My bad.

-Tim

---

### Post by handy on 2009-01-03
> **windependence said:**
> Sorry Greg. Yes, I have a tendency to look at all of this server stuff from a professional production environment view. Sometimes that gets in the way when someone is setting up a more casual home use server. My bad.

-Tim

No bad from you buddy, just the usual plethora of other perspectives that we try to do the best we can with. :-)

***[Edit:]**  VM's = virtual machines; boy I was/am being dumb as dog sheet... :lolflag:*
[B]
*[Edit:2][/B] Actually, it is not so much dumb on my behalf, it is just that my brain has slow processing speed. True.*

***[Edit:3]** Though dumb is one of them there relative terms, & I sure a sheet can be that... :lolflag:*

---

### Post by Zack McCool on 2009-01-03
It would go on the FreeNAS box.  I haven't used anything like that, but it should be pretty straightforward...   

I'd start by putting the script in /root.  Then, edit /etc/crontab and put in the proper information, something like this:

*/5 * * * * admin /root/scriptname.sh

Also, the page you referenced mentions that the first line in the script should be changed to #!/bin/sh

---

### Post by handy on 2009-01-03
> **Zack McCool said:**
> It would go on the FreeNAS box.  I haven't used anything like that, but it should be pretty straightforward...   

I'd start by putting the script in /root.  Then, edit /etc/crontab and put in the proper information, something like this:

*/5 * * * * admin /root/scriptname.sh

Also, the page you referenced mentions that the first line in the script should be changed to #!/bin/sh

Thanks Zack, I'll have a go at it tomorrow, & let you know how it goes.
[B]
*[Edit:][/B] I didn't get to it today, hopefully tomorrow. :-)*

---

### Post by handy on 2009-01-05
I'm having a go at setting up a Transmission watch directory on the FreeNAS box.

I'm using a script that I found here:

*_[http://trac.transmissionbt.com/wiki/Scripts/Watchdog](http://trac.transmissionbt.com/wiki/Scripts/Watchdog) _*

I have copied it to /root & have made /torrentwatch the directory for the script to watch.  I just ran the script manually & got a unauthorised user error, so I'll have to sort that out.

Windependence, I now understand why you made the comment earlier about it being a lot of trouble to go to, as I now see that I will have to make a Transmission configuration script with my desired settings & also run a blocklist updater script as a cron job as well.

Anyway once it is all set up, I will have copies of the scripts & I won't have to do it again, hopefully. :-)

Here is a page with some good links on this topic:

*_[http://trac.transmissionbt.com/wiki/Scripts](http://trac.transmissionbt.com/wiki/Scripts)_*
[B]
*[Edit:][/B] I'm letting this sit for some days, when I get back to it I'll post.*

---

### Post by handy on 2009-01-26
Hmmm, I've been letting it sit for more than some days.

I have finally found a PIII which I will use as my dedicated FreeNAS box.

Have been reading & thinking some about my drive configuration on this machine.  I was going to use soft RAID-1, but have changed my mind, & will just go for a 1Tb drive & backup my data to DVD.  I can't afford to loose the data, & we all know that RAID is not a backup.  I could end up with a RAID-1 backup of corrupt data, without me being aware of it, which is just not acceptable.

Anyway, when I get a drive & get this transmission watch directory sorted out I'll post here & let you know what I have found out in the process & just how well it works for me.

---

### Post by windependence on 2009-01-26
May want to set up RAID5 on it if you can afford the drives. I have three 500GB drives on mine in RAID5 which includes fault tolerance as well as improved performance because of the fact that you have more spindles. Mine has been running for over two months and still rock solid. One drive will certainly work though, with backups of course. :)

-Tim

---

### Post by handy on 2009-01-26
Thanks Tim,

Correct me if I'm wrong, but if the prime jobs of the FreeNAS box are being a torrent slave & the streaming of video, to just one box, I wouldn't expect that the speed increase of a RAID-5 array would be worth the expense, as my LAN hardware speed will always be the bottleneck.

---

### Post by windependence on 2009-01-26
You would certainly be correct there. I was thinking more along the lines of being able to hot swap a drive out if it fails. I build mine in hot swap cages so I can pull them without taking things apart. Of course, if your torrent server is down, it probably wouldn't matter as much as if a production web site was down. You know, I'm always thinking in terms of the enterprise. ;)

-Tim

---

### Post by redroad55 on 2009-01-28
Where did you go ? Been following this thread close .. Lots of good schtuff ..

---

### Post by handy on 2009-02-17
> **redroad55 said:**
> Where did you go ? Been following this thread close .. Lots of good schtuff ..

Oh, hi, sorry I've been otherwise engaged.

I'll get back to finishing off the FreeNAS torrent slave thing before too long & I'll post.

---

### Post by mikemccoy on 2009-07-05
> **handy said:**
> The following command worked without complaint:

* sudo mount freenas:/mnt/NAS-1 /mnt/freenas*

So I'm automatically mounting the drive via the following line in fstab:

*freenas:/mnt/NAS-1 /mnt/freenas nfs     auto,defaults           0       0*



I'm having the same problem of figuring out how to mount to the FreeNAS.  I've been reading so many articles, trying different commands, and nothing is working correctly - I'm sure its a stupid thing I'm doing thats not making ti work.

FreeNAS IP = 192.168.1.20
FreeNAS name = FreeNAS (original, huh?)
Mount point = /mnt/Share
Local mount directory = /mnt/freenas

I tried entering in the first command in termal, but I get this error back:

> 
mount: wrong fs type, bad option, bad superblock on freenas:/mnt/Share,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


What do I need to do to fix this??
Also, I dont know what fstab is, can anyone provide a link on this? Is it just a config file that I add one line of text to so it's a permanent mount? (ideal).

Any help would be greatly appreciated.  Currently the only way I'm transfering files is using the FTP which I like, but I want to be able to stream data which I cannot do now...

Thanks!!

---

### Post by Zack McCool on 2009-07-06
> **mikemccoy said:**
> I'm having the same problem of figuring out how to mount to the FreeNAS.  I've been reading so many articles, trying different commands, and nothing is working correctly - I'm sure its a stupid thing I'm doing thats not making ti work.

FreeNAS IP = 192.168.1.20
FreeNAS name = FreeNAS (original, huh?)
Mount point = /mnt/Share
Local mount directory = /mnt/freenas

I tried entering in the first command in termal, but I get this error back:


What command did you enter to get that error?  If you enetered what was quoted, you would most definitely get an error, because you do not have that share point set up.

Try this instead:
```
sudo mount FreeNAS:/mnt/Share /mnt/freenas
```

If you don't have a DNS entry for your FreeNAS server, use this instead:
```
sudo mount 192.168.1.20:/mnt/Share /mnt/freenas
```

> 
What do I need to do to fix this??
Also, I dont know what fstab is, can anyone provide a link on this? Is it just a config file that I add one line of text to so it's a permanent mount? (ideal).


from a terminal prompt, enter ```
sudo nano /etc/fstab
```

Then, at the end of that file, put in the following:
```
192.168.1.20:/mnt/Share /mnt/freenas nfs auto,defaults 0 0
```

Both of these assume that you have freenas configured to share using NFS.

---

### Post by mister_p_1998 on 2009-07-06
> **handy said:**
> I require some help to finish setting up my FreeNAS installation.

I have FreeNAS installed on a 2Gb drive, currently with a 160Gb drive as IDE secondary master.

FreeNAS has been setup post install via its browser control software from the client.

I don't think I have got it wrong in the setup so far, but of course I could be mistaken. :-)

The problem I have is with setting up NFS;.

Why do you want to change the defaults?
Whats wrong with UFS?
I setup Freenas, mounted four drives and had a fully working server in 10 minutes. Haven't changed it at all apart from putting a bigger drive in.

Steve

---

### Post by windependence on 2009-07-06
I agree here, don't mess with UFS, it's a good filesystem, stable, and well supported. No need to change anything in the defaults for NFS either. FreeBSD is just a fantastic OS once you get to know how simple and rock solid it is. It is NOT Linux though, it is real Unix. There is a difference.

-Tim

---

### Post by mikemccoy on 2009-07-06
> **Zack McCool said:**
> If you enetered what was quoted, you would most definitely get an error, because you do not have that share point set up.

If you don't have a DNS entry for your FreeNAS server, use this instead:
```
sudo mount 192.168.1.20:/mnt/Share /mnt/freenas
```


I'm not sure what you mean by saying the share point wasn't setup.  Wasn't that what I was trying to do via this command? I made the local directory, the network share was already made and working with Windows no problem, NFS was already enabled (your assumption was correct) and now all I needed to do was "connect" the link between server NFS and Ubuntu via this commnad.  Right or wrong?

I'm not at my machine right now, I will try this again tonight, but that looks like the same exact code I typed in to receive that error message.  I will reply back tonight if it worked or not.

Thank you very much!!

---

### Post by Zack McCool on 2009-07-06
> **mikemccoy said:**
> I'm not sure what you mean by saying the share point wasn't setup.  Wasn't that what I was trying to do via this command? I made the local directory, the network share was already made and working with Windows no problem, NFS was already enabled (your assumption was correct) and now all I needed to do was "connect" the link between server NFS and Ubuntu via this commnad.  Right or wrong?

I'm not at my machine right now, I will try this again tonight, but that looks like the same exact code I typed in to receive that error message.  I will reply back tonight if it worked or not.

Thank you very much!!

What I mean is that, on the FreeNAS server, you would need to set up the share.  You'd have to enable NFS and have it set up to export the above share.

There are several sharing methods available on a FreeNAS server, so you can play around and use what suits your needs best.  Many people use the UFS shares, and that's perfectly fine, too.  But each different protocol will use a different mount command on the client.

---

### Post by mikemccoy on 2009-07-06
> **Zack McCool said:**
> What command did you enter to get that error?  If you enetered what was quoted, you would most definitely get an error, because you do not have that share point set up.

If you don't have a DNS entry for your FreeNAS server, use this instead:
```
sudo mount 192.168.1.20:/mnt/Share /mnt/freenas
```

from a terminal prompt, enter ```
sudo nano /etc/fstab
```
Then, at the end of that file, put in the following:
```
192.168.1.20:/mnt/Share /mnt/freenas nfs auto,defaults 0 0
```

Both of these assume that you have freenas configured to share using NFS.

So I just tried the first command w/o DNS and got the same error message back as on page 8.
I used your instructions for fstab and entered that line and saved file.

Not sure what I'm doing wrong?
FreeNAS> NFS> Enabled with 4 servers
FreeNAS> NFS > Shares tab > Path: /mnt/Share/   	Network: 192.168.1.0/24
All users have root [yes]
All dirs [yes]

I'm using 3 HDs in a RAID 5 Software config and for:
Disks > Mount Point it is Disk:/dev/raid5/RAID5p1 Filesystem: UFS
CIFS/SMB Share: /mnt/Share/

Dont think this makes a differance, I'm using Ubuntu 8.04??

Thanks for the help Zack!

---

### Post by windependence on 2009-07-06
I have almost the exact setup you do including the software RAID5 and I have no problem connecting from 8.04LTS. Did you export your NFS shares?

-Tim

---

### Post by mikemccoy on 2009-07-07
> **windependence said:**
> I have almost the exact setup you do including the software RAID5 and I have no problem connecting from 8.04LTS. Did you export your NFS shares?
-Tim

I'm not sure what **"export NFS shares"** mean? Maybe that's what is causing this? I thought all I needed to do was enable NFS on FreeNAS and then try those mount commands.

What did I skip over? I went back and read through the previous pages last night but wasn't really sure what they were talking about or how to do it...

Thanks for the reply!

---

### Post by windependence on 2009-07-08
Go to the services tab and click on NFS, then click on the shares tab. It should look something like this. Make sure you click save.

---

### Post by mikemccoy on 2009-07-10
Haha "make sure you click save" I like that.
Yes, I've had this enabled the whole time.

I have taken screen shots of all of my settings and errors.
[http://www.collegetownmenus.com/test/freenas.zip]("http://www.collegetownmenus.com/test/freenas.zip")

Please look over and advise.  Thank you!
Sorry for delay in response...

---

### Post by guta on 2009-07-10
hi.
I've got 2 network cards in this computer, connected to different networks(1.- 192.168.10.254 and 2.- 192.168.112.254), and I want to bridge these networks. In win.XP it is trivial to do, but in Ubuntu I have no idea what to do. Can anyone point me in the right direction?
tks.

---

### Post by mikemccoy on 2009-07-10
> **guta said:**
> hi.
I've got 2 network cards in this computer, connected to different networks(1.- 192.168.10.254 and 2.- 192.168.112.254), and I want to bridge these networks. In win.XP it is trivial to do, but in Ubuntu I have no idea what to do. Can anyone point me in the right direction?
tks.

Sounds like a different topic...would probably get better results if you started a new thread.  (I dont know how to do it anyway, sorry).

---

### Post by windependence on 2009-07-11
> **mikemccoy said:**
> Haha "make sure you click save" I like that.
Yes, I've had this enabled the whole time.

I have taken screen shots of all of my settings and errors.
[http://www.collegetownmenus.com/test/freenas.zip](http://www.collegetownmenus.com/test/freenas.zip)

Please look over and advise.  Thank you!
Sorry for delay in response...

With your SAMBA shares you have issues with permissions there.

Looks like in Ubuntu you will need these packages to mount NFS shares:

```

sudo apt-get install nfs-common portmap
sudo dpkg-reconfigure portmap
sudo /etc/init.d/portmap restart

```

Then mount your NFS shares. After that you may have to restart the services to see the mount:

```
sudo /etc/init.d/portmap restart
 sudo /etc/init.d/nfs-common restart

```

If you have a firewall you need to make sure ports 32771, 111 and 2049 are open.

Good luck!

-Tim

---

### Post by mikemccoy on 2009-07-11
WOOHOO!! That worked like a charm!! Awesome! *Saves this page in bookmarks*
Thank you very much, I really appreciate it! I made a shortcut on the launch bar to the /mnt/Share folder and that works well also.

Thanks again, great work!

---

### Post by handy on 2010-08-11
My FreeNAS system has worked without a hitch since installed. I can't find anyway to fault it in itself.

That said, the machine has been running on is greatly overpowered (& noisy) for the job - Athlon64 3500+. So I got hold of a little ReadyNAS box which runs a cut down version of Debian & allows 2 drives to be installed. 

It automatically wants to do a mirror RAID routine on 2 drives but you can get around that if you want more backup storage space. Details on the [**_Netgear ReadyNAS forum_**]("http://www.readynas.com/forum/index.php"). (& you don't want to risk duplicating corruption in the fastest way known to man & machine! :lol:)

The tiny thing uses 4W at idle & more of course when the drive(s) are spinning. It is all but silent, doesn't get hot & has the ability to be a torrent slave, it also is Linux friendly & even more so for windows & OS X. 

I'm accessing ReadyNAS easily from both 2x Arch & 2x OS X, machines in this household. 

There are sophisticated permissions built in;- all this & so much more is accessed via a simple client side web GUI interface. It can even be easily set up as an iTunes server.

The thing has an inbuilt NIC capable of gigabit throughput, so I can see me upgrading my switch in the future to take advantage of this transfer speed increase.

Anyway, this post is just an update on where I have gone with NAS. Hopefully it assists someone out there in the world. :)

---

