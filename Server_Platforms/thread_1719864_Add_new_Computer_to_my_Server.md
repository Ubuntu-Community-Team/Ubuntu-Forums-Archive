---
title: "Add new Computer to my Server"
date: 2011-04-02
forum: Server Platforms
---

### Post by Adrianna_2 on 2011-04-02
I have ubuntu server installed on a PC with 2 GB of HD, 6 GB of RAM (DDR2), 1 intel core 2 duo processor .. everything works well, email, ftp, user accounts (for hosting of their files) .. but the disk space is shrinking .. 

I decided to buy another PC the same model and with the same characteristics as the first one I mentioned above .. My question is, how can I integrate this new PC to work with the apache server that I have in the first PC obove, how to tell Apache to use the space for the next PC (like a raid, or something like that) .. I do not know if this makes sense, but, while I had a single PC :( everything seemed easy, but now that disk space is filling up on PC # 1.. I do not know how to tell apache or ftp server to keep hosting (using) the next PC (the new one I bought it) wich is into the my network.  :confused:

---

### Post by volkswagner on 2011-04-02
If they are both ubuntu machines you could create an NFS on the second one and share it with the first.  Mount the NFS share in the /etc/fstab.  Then create additional SAMBA shares inside that.

Wouldn't it be easier to just add hard drive to the server itself(rather than adding an entire machine)?

---

### Post by Adrianna_2 on 2011-04-02
Quick reply @volkswagner .. thanks ..
> **volkswagner said:**
> If they are both ubuntu machines
The number one PC has installed Ubuntu server 10.10, ftp server and mail server, the second PC has a blank HD.. ready to the whole process ;)
> **volkswagner said:**
>  you could create an NFS on the second one and share it with the first. Mount the NFS share in the /etc/fstab. Then create additional SAMBA shares inside that...
A tutorial (link) that you can point me to me? .. forgive the ignorance, but in the past tried to mount a SAMBA share (into ubuntu desktop distro) and did never went well :(

> **volkswagner said:**
> Wouldn't it be easier to just add hard drive to the server itself(rather than adding an entire machine)?
@volkswagner: Nothing is ever easy, but if it is difficult you must be doing it wrong... :P

---

### Post by volkswagner on 2011-04-02
...haha you got me!

I guess adding the HD to server1 is not an option?

Well since there more than one way to accomplish this, perhaps we should start with how you need/want the new space allocated.

Are the current users ftp accounts jailed to their ~home folder?

Is there a common share/folder that needs the additional space?

If the only file access is via ftp, you may not need SAMBA at all.  Are you using SAMBA currently?

For the NFS share this is my [bookmarked post]("http://ubuntuforums.org/showthread.php?t=249889").

---

### Post by Adrianna_2 on 2011-04-02
> **volkswagner said:**
> ...haha you got me!

:P

> **volkswagner said:**
> I guess adding the HD to server1 is not an option?

Nope.. I do have a Server1 been setup for the whole machine (the First PC), but it does not support more HD space.. (is allready up to his maximun space 2 TB HD's), so my choice is to set (add the Second PC.. to be able..to add nuew users accounts as like the first PC does) but responding to main server (server1) (wich is in the First Pc) ..If That make any sence :( 

> **volkswagner said:**
> Well since there more than one way to accomplish this, perhaps we should start with how you need/want the new space allocated.

I do not have an idea.. how the new space will be (or) need to be allocate.. help me to understand this please (what can be my best choice).. will you?

> **volkswagner said:**
> Are the current users ftp accounts jailed to their ~home folder?

Yes, I did Create (set):
the file /etc/pure-ftpd/conf/ChrootEveryone which simply contains the string to "yes"
the file /etc/pure-ftpd/conf/CreateHomeDir which again simply contains the string to "yes"
the file /etc/pure-ftpd/conf/DontResolve which again simply contains the string to "yes"
```

echo "yes" > /etc/pure-ftpd/conf/ChrootEveryone
echo "yes" > /etc/pure-ftpd/conf/CreateHomeDir
echo "yes" > /etc/pure-ftpd/conf/DontResolve

```> **volkswagner said:**
> Is there a common share/folder that needs the additional space?

Nope, since every body have accounts jailed to their ~home folder (store, ftp, mail..etc)

> **volkswagner said:**
> If the only file access is via ftp, you may not need SAMBA at all. Are you using SAMBA currently?
No SAMBA have been use yet... ..  and yes, the only file access is via ftp.

---

### Post by volkswagner on 2011-04-02
I hate to turn this into 1000 questions.

I must ask, how can you avoid the current disk from getting filled up?

I really think you should explore other options, such as adding a SATA card, or eSATA bracket if you have available ports.

Add an external enclosure to house the added drives.

If you are hell bent on adding a second server, dividing the added space can be tricky.[LIST=1]
[*]Is your current number of users going to grow?
[*]Can you add the second server for just new Users and have enough space on the current system for the currents users future needs?
[/LIST]

One option:
Failing the above option of adding disks, you can create your new server with a large /user-share partition.  Make /user-share an NFS shared folder.  On Server1 mount the NFS share on something like /home2.  If your current users will not fill the drive you could just place new users home folders in /home2 when creating the user. If current users can potentially fill the drive you may want to move some of their home directories to /home2.

You could also just move some sub folders.  If you have a standard structure like /home/username/htm_public and that folder has a trend of using large disk space, you could just make a hard link of that folder and put the data on the NFS share.  You could do this for current users moving the data, and creating the hard link.

What you don't want is two servers running the same services with port conflicts and such.

I hope I'm making sense.

Cough, cough... how about add disk space to server1? !!!!!!!

---

### Post by Adrianna_2 on 2011-04-02
> **volkswagner said:**
> I hate to turn this into 1000 questions.
Dont worry, I feel that you are trying to help, and there (questions), is the only way to get a clear view of my needs... So, don worry, I do understand

Here is the whole problem ... Users are growing in number, is a project I started with a friend of mine from school, our parents covered the expenses for the project, now several friends have accounts with us (20 GB  of their home "ftp" folder... each one) ...and they keep all data on the number one server PC, but the disk space is 75%, which led us to the question of how to use (add) a new PC,  (continue to manage accounts from the number one server (where is apache, ftp, in our portal-website) but tell apache, to send new accounts to the second PC, and make it to point to their new home folder (which would be in the pc number two).


> **volkswagner said:**
> Cough, cough... how about add disk space to server1? !!!!!!!

:p ...this pc number one (server1), does not support more disk space, the motherboard only supports 2 TB of disk space, and is already 75% as I said, for this reason we buy a second PC, for use in our network, but do not know how to make our server acknowledge this (new pc) as a part of the first one.

Things have gotten serious now .. What started as a simple project, now is growing and we did not have the necessary knowledge to handle the upcoming problem I guess. :-(

---

### Post by volkswagner on 2011-04-02
> **Adrianna_2 said:**
> 
:p ...this pc number one (server1), does not support more disk space, the motherboard only supports 2 TB of disk space, and is already 75% as I said, for this reason we buy a second PC, for use in our network, but do not know how to make our server acknowledge this (new pc) as a part of the first one.


I'm fairly certain if you were to add a PCIe SATA controller this would expand the MOBO's limit.  Since the SATA card will have it's own controller.  Even an all in one solution similar to [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816132015").

Anyway, setup your second server as I described.  You can create a large partition mounted at your preferred locations.  Create the NFS share as from the how to in my earlier post.

Once you get the nfs share working reliably, you can setup your new users and move other's home folders if you think the 25% headroom is not enough,

---

### Post by Adrianna_2 on 2011-04-03
Thank you very much @volkswagner :KS ....That's ... with the creation of NFS everything will be fine .. exactly as you described in your previous post .. 

We have already agreed (me and my girl-friend), and the option will be a HP ProLiant ML350 G6, with 6 HD 1 TB each one of them, two Intel Xeon Processor E5504 .. and 12 GB of RAM (DDR3) .. that is the solution we have for now, we will moved all the databases and server software to the new machine from the PC (server 1), and leave the PC 1 and 2 ... just blank (means Ready) .. who would use it as a storage space if necessary ... it would be as you say .. NFS installed system.

The only drawback is that the server and the client machine, the two of them .. must have .. NFS compatible mode... and that.. is something that I have to look and study very well, because I have not ever done it before...Wish me good luck.. Please [-o<

---

