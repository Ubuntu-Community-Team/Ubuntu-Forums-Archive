---
title: "Ubuntu Server - How do I add files/share files?"
date: 2010-01-03
forum: Server Platforms
---

### Post by goldenboy300 on 2010-01-03
Hello all!

I have decided to configure a server for file sharing and possibly to host a website later on.  I have managed to install Ubuntu Server 9.10.  Being a long time Windows user, I found that you can implement a GUI so I installed Ubuntu Desktop via 

```
sudo apt-get install ubuntu-desktop
```
But now from a little reading it seems that this GUI is not for the server? And no such thing exists?  Is that correct?  [[COLOR="Blue"]HERE[/COLOR]]("https://help.ubuntu.com/community/ServerGUI") seems to suggest differently... after all its titled "ServerGUI".  ???

My main goal right now is to learn how to add files to the server to where they can be accessed from a friend/business associate from his computer over the web.  Furthermore, can I set it up to be accessed from any computer if he or I are at someone else's house? i.e. on a job

I have no clue what to do, ubuntu server/desktop is just sitting there and I don't know how to add a file, access that file once added, and how to download that file from the server.  

All the help I can get is much obliged.  Thank you, and I look very forward to hearing from some one.

---

### Post by HermanAB on 2010-01-03
The 'server'version is mainly meant for use on headless machines lurking in dank data centres that never see the light of day and are managed remotely over SSH.  If your 'server'is actually a desktop machine, then simply install regular Ubuntu.  Otherwise, you could install Gnome on your server - six of one, half a dozen of the other.

---

### Post by goldenboy300 on 2010-01-03
The server I'm using is an actual server.  This is it exactly [[COLOR="Blue"]Rioworks HDAMA DUAL 2Ghz AMD opteron motherboard & CPU[/COLOR] ]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=360184123391#ht_4059wt_1165") with a 160gb IDE hard drive and 1gb of PC3200 ECC RAM for now and I plan to add a SATA RAID Controller with two hard drives. If ever needed, I plan to add more of these and have a rack with a server controller, UPS, and any other necessary equipment. 

I want to know how I add a file whether remotely or directly, access that file from any computer, and download that file from any computer.

---

### Post by Belizeian on 2010-01-03
Need a little clarification.

You want to be able to put files on the server from inside your network and then allow people outside your network to be able to read them and or copy them but not change them.  Is this correct?

Do you want anyone to be able to access them or just a select few (5 or less)?

Does the server have a monitor and keyboard attached?

---

### Post by goldenboy300 on 2010-01-04
Yes, that is correct. Access whatever ones I want them to access (5 or less).  The idea in my head is 1. User1's Private folder, 2. Users2 Private Folder, 3. Public Folder. I'd even like them to be modified if they had the proper credentials/passwords I guess.  

I'm so new to the "Server Thing" that I'm not sure how this works, not even 1% sure.  =(

One example of it's use would be to share an ISO image with my business associate without having to drive all the way to his house to give it to him.

Another idea that we've had is to share videos.  So I can upload a video from my house, and he can watch it at his house.  (and yes, I've heard of youtube lol =)

Also, I'd like to be able to back up my data on it if I end up having the room for such things.
(EDIT) Yes, it has a monitor and keyboard.

Just to clarify more, this is being done much more as a hobby than a "business solution".  I'm a geek for sure as well as an "enthusiast" especially when it comes to high end computers and what not.

Thanks.

P.S EDIT:  The more I think about it, I guess I need to have a website that someone would go to in order to click a link for the download????  Is this the missing factor?  Do I need a website?  Sorry, I"M SUCH A NOOB!

---

### Post by HermanAB on 2010-01-04
OK, the easiest file server is FTP. The second easiest is NFS (Windows Services for Unix free download from MS) and the most difficult one is Samba.  So start with a FTP server such as vsftp and work your way up.

---

### Post by CharlesA on 2010-01-04
Ok, you can share folders using Samba. It's fairly easy to setup.

As for the GUI. It can be helpful, especually for newer users. I originally installed a GUI on my server (which is sitting in a dark corner of another room) so that I could configure my RAID sofware and Webmin using SSH and VNC when I was working remotely. Turned out that I hardly used the GUI after I did some googling on how to add users (which was the main reason I install a GUI, among others).

Now I just access the server via SSH and forward the RAID software and Webmin ports so that I can access them over SSH.

So you want to have a business associate access files on yer server? I recomment sftp, since it is encrypted and you would only have to have the SSH port open.

EDIT: @HermanAB: Samba is difficult to setup?

---

### Post by HermanAB on 2010-01-04
The first time, setting up Samba is not easy. FTP works out of the box - no setup required - just do apt-get vsftpd and Bob's your uncle.  NFS has only two lines to configure.  Samba has hundreds of lines of configuration...

---

### Post by Belizeian on 2010-01-04
He wants people on the outside to access his box which means samba isn't the way to go for file shareing.

SSH is the way to go for that.

His windows friends can use winscp for access and he can use gftp for same.  It works just like ftp but it's secure as it uses ssh and the username and passwords aren't sent in the clear like with ftp.

Since you are talking such a small number of people, just make accounts for the individual people on the server.

as to where to put the files they will each have their own home directory for their private files.

as to the files all members are supose to access.  Make a group on the server add all the users to it.  Then create a directory under var and add that group for access to it.  Put files in there.  You could create a symlink in each home directory to this directory.

Sorry it's early yet and I know I'm rambleing but thats the way I would go with refinements of course.

I'll check this latter today and see where you are.

---

### Post by K.J. on 2010-01-04
You will need to install an actual sftp server, because the standard openssh with existing users will allow access to ALL directories that are not chown root.

---

