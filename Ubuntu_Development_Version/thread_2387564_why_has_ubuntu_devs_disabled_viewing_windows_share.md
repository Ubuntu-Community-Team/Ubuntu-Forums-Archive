---
title: "why has ubuntu devs disabled viewing windows shares, actually all shares?"
date: 2018-03-20
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2018-03-20
I get nothing for the window, just a blank.

I have a latest linux mint PC, it can view and modify windows 7 shares fine.
'workgroup = WORKGROUP' works fine in mint.


```
scott@scott-MS-7596:~$ smbclient -L 192.168.1.3
WARNING: The "syslog" option is deprecated
Enter WORKGROUP\scott's password: 

	Sharename       Type      Comment
	---------       ----      -------
	3TBTV2          Disk      
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
	D$              Disk      Default share
	F$              Disk      Default share
	F3tb            Disk      
	IPC$            IPC       Remote IPC
	Users           Disk      
Reconnecting with SMB1 for workgroup listing.
Connection to 192.168.1.3 failed (Error NT_STATUS_RESOURCE_NAME_NOT_FOUND)
Failed to connect with SMB1 -- no workgroup available
scott@scott-MS-7596:~$ 

```

If I try to connect by ip to the server, I get this in the screenshot.

This is a major inconvenience. I need to move 500gb of files across the network, to do this, I will have to pull the drive out from ubuntu PC and place it into the linux mint PC.
I even tried copying Mint's smb.conf onto Ubuntu, but was no help.
Windows can see my ubuntu shares fine.
Morbius in an earlier posting, said ubuntu has messed up the sharing, and seemed to imply it was not fixable.

smbtree shows the shares
```

scott@scott-MS-7596:~$ smbtree
WORKGROUP
	\\SCOTT-MS-7596  		scott-MS-7596 server (Samba, Ubuntu)
		\\SCOTT-MS-7596\Diabetes       	
		\\SCOTT-MS-7596\MX490          	Canon MX490 series
		\\SCOTT-MS-7596\IPC$           	IPC Service (scott-MS-7596 server (Samba, Ubuntu))
		\\SCOTT-MS-7596\print$         	Printer Drivers
	\\LRWIN7-PC      		
		\\LRWIN7-PC\Users          	
		\\LRWIN7-PC\IPC$           	Remote IPC
		\\LRWIN7-PC\F3tb           	
		\\LRWIN7-PC\F$             	Default share
		\\LRWIN7-PC\D$             	Default share
		\\LRWIN7-PC\C$             	Default share
		\\LRWIN7-PC\ADMIN$         	Remote Admin
		\\LRWIN7-PC\3TBTV2         	
	\\DESKTOP-H4DMJLE		
scott@scott-MS-7596:~$
```

---

### Post by Morbius1 on 2018-03-20
> **sdowney717 said:**
> Morbius in an earlier posting, said ubuntu has messed up the sharing, and seemed to imply it was not fixable.
I never said Ubuntu had anything to do with this: [Bionic Beaver can not discover samba hosts - netbios. ]("https://ubuntuforums.org/showthread.php?t=2384959")

This is samba and it has to do with host discovery not host access. In fact I said that explicitly:
> [COLOR=#0000cd]_**NOTE**: This is not a host name resolution problem - it's a host browsing ( discovery ) problem._[/COLOR] 
And to further complicate things I still think the culprit in all this is gvfsd-smb-browse which makes it a gnome issue.

Anyhoo, you are trying to access by ip address so it has nothing to do with my post. Why are you using pre-release software?

---

### Post by sdowney717 on 2018-03-20
So what does Linux Mint use regarding samba, a different version?
Mint worked with zero modification for windows shares.

I have been using 18.04 since alpha 2. File sharing is the only thing not working that I experience.

In the past ubuntu versions, I have had significant troubles making file sharing work.

Do you think in a month the file sharing will work? If Samba is the problem not Ubuntu then why would it?

I just looked on Mint and Samba is not even installed, so Mint works fine without Samba.

I could not get ubuntu sharing working to view windows shares without samba, and cant with it installed either. So for me, Samba cant be the problem, logically.

Screenshot of mint working without samba at all?
I wont install samba if it is going to create a problem on Mint. Plus I am in the middle of a big file transfer.
Yes, it was a pain to pull out the drive, but I decided to use this sata 3 drive in the Mint PC as a boot drive, so it is ok.

---

### Post by SeijiSensei on 2018-03-20
> **sdowney717 said:**
> I need to move 500gb of files across the network, to do this, I will have to pull the drive out from ubuntu PC and place it into the linux mint PC.
For future reference, if you need to do bulk transfers of files between two Linux hosts on a network, you're *much* better off using [rsync]("https://www.samba.org/ftp/rsync/rsync.html").  For instance
```

cd /
sudo mkdir /newhome
sudo rsync -av 192.168.1.100:/home/. /newhome

```
will take all the directories below /home on 192.168.1.100 and copy them below /newhome on the local machine.  The -a(rchive) switch preserves permissions, modification dates, and the like.  The -v(erbose) switch generates a list of the transferred files on the terminal. I strongly recommend getting acquainted with rsync if you routinely do file transfers.  For instance, I use rsync in a backup script on my local server each night that sucks down specified directories from my cloud servers.

---

### Post by Morbius1 on 2018-03-20
** If we are talking about Mint 18.3 it still uses 4.3 of samba.

** As I said in my post the host discovery issue came with samba 4.7

** You are confusing samba - the server packages - with samba - the client packages. All Linux desktop system - even Mint - have the samba client packages installed by default ( libsmbclient ). Have been for a generation.

---

### Post by sdowney717 on 2018-03-21
I managed to get into my windows shares, in the global section of smb.conf I put

```
#client max protocol = SMB2
client max protocol = NT1
```

First line did not work, second one did.

Then restarted server
```
scott@scott-MS-7596:~$ sudo service smbd restart
scott@scott-MS-7596:~$ sudo service nmbd restart
scott@scott-MS-7596:~$ 

```

and said connect to server in File manager click other locations, and put that in the input text box.

smb://192.168.1.3/ 
It asked me for my windows password, then the shares appeared.
Not sure why it needs the windows 7 password to connect to the windows 7 PC?
It would not let me connect using anonymous.

Another interesting thing
Putting in

```
client min protocol = NT1
client max protocol = SMB3
```

Shows the 'workgroup' icon, but no connection. (Well, only did it one time, now showing blanks.)

And it still can connect to the windows 7 shares by using smb://192.168.1.3/
This time did not ask for any password.

---

### Post by sdowney717 on 2018-03-22
Well, that was a short term fix.
Just now at 1am, I did an upgrade, a lot of samba packages were changed by the developers.
And now I can no longer connect to the windows 7 shares.

I checked my smb.conf and it was not changed.

I know they dont like protocol NT1, so maybe it is no longer allowed at all??

---

### Post by sdowney717 on 2018-03-23
I found out for win 10 shares, they work for connecting by ip address.

But not for windows 7 (again), must be related to the samba connection protocol version, win 10 uses a more advanced protocol than windows 7.
Regardless, Still no browsing the network.

Since it seems to be ignoring my smb.conf changes which had been working, how can I now force samba to see windows 7 shares?

And linux MINT can not connect to the windows 10 shares, sees the server name, but connection times out,  but MINT can connect to the windows 7 shares....exact opposite results....dumb stuff is going on.

I tried setting windows 7 to enable smb2 and disable smb1, result was linux Mint can no longer connect to windows 7 shares...neither can ubuntu.
win 10 PC can still see and connect to win 7 shares.
 
[http://kb.bodhost.com/steps-to-enable-and-disable-smbv1-smbv2-and-smbv3-in-windows-servers/](http://kb.bodhost.com/steps-to-enable-and-disable-smbv1-smbv2-and-smbv3-in-windows-servers/)

I redited registry to enable smb1 and smb2 both. Linux Mint can again see the windows shares. Ubuntu, no.

---

### Post by jchiso2 on 2018-10-05
I've been wrestling with these problems for about six weeks now, since I foolishly chose to update some Ubuntu systems to 18.04.  None of the solutions offered on these forums have helped; and the curious thing is that SAMBA shares on my (three) pi devices appear and function as expected.  Shares on Windows 7, Windows 8.1, and Ubuntu distributions prior to 18.04 are not browseable at all.

It does not seem like it should even be possible to disable share browsing for all connected PCs by changing the configuration of a single server.  There must be something terribly amiss about Bionic's SAMBA protocols.

If anyone out there has had a similar experience and found a working solution I'd be interested in hearing it and open to trying at this point ...

---

### Post by Morbius1 on 2018-10-06
Please start your own topic.

But before you do follow these steps:  Bionic Beaver can not discover samba hosts - netbios: [https://ubuntuforums.org/showthread.php?t=2384959](https://ubuntuforums.org/showthread.php?t=2384959)

And post the output of this command so we can verify how you are set up:
```
testparm -s
```

---

### Post by coffeecat on 2018-10-06
And thread closed. Not only has Bionic, which this thread is about, been released long ago, but the current dev version Cosmic, will be released very shortly.

@jchiso2, please do not necromance-hijack old threads. If you need help, please start your own thread. But not here - this is the sub-forum for discussing issues with the current development version.

---

