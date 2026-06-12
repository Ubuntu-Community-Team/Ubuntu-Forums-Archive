---
title: "General Questions on a File/Print Server"
date: 2009-10-16
forum: Server Platforms
---

### Post by HighlyDubious on 2009-10-16
I want to add a File/Print server to my network, and need some advice on which programs to use, and which online tutorials will best fit my situation. This File/Print server will be accessed locally by both wired and wireless PC's, and accessed externally via the Internet, so some degree of security is obviously required.

I currently have the following equipment:

[LIST=1]
[*]A Ubuntu Server (9.04) with LAMP. I've also installed the Xubuntu DE. (I'm learning the CLI, but as a newbie, I appreciate the security blanket of a GUI to fall back on.) In addition, this machine also has a few HD's that were previously used in Windows-based PC's, so those partitions are NTFS.
[*]Two desktop PC's which are MultiBoot. One of them is mainly used with Ubuntu 9.04, the other is mostly used with Windows 7. But, at any given moment each machine might be booted into any of the following:
[LIST=1]
[*]Windows XP
[*]Windows 7
[*]Ubuntu 9.04
[*]Ubuntu 9.10 (when released)
[/LIST]
 
[*]A Laptop PC, which connects wirelessly into this network. The laptop is also MultiBoot, with Vista, Win7, and Ubuntu 9.04
[*]The Server and other two desktop machines have wired connections to my 2Wire Remote Gateway/Router/Modem. And the laptop connects wirelessly to the same 2Wire Remote Gateway.
[/LIST]
My goal is to create a central file/print server running on the Ubuntu Server machine. 

In the future I might also decide to store applications on the server. It's not necessary to set that up now, but I'd like to have the expandability to do so later on.

As mentioned, some HD's on the server are currently formatted with NTFS partitions, but if it would be better I can easily move that data to ext4 partitions. In other words, I need advice on the benefits of either staying with NTFS, or transferring the data to ext4.

I am very new at all of this, but I'm learning a few things. I know I  need SAMBA, and know I'll need to configure CUPS for the printers (they are currently connected to the server, but not yet configured). I see instructions on HowToForge entitled "**Ubuntu 9.04 Samba Server Integrated With Active Directory**" ([link]("http://www.howtoforge.com/ubuntu-9.04-samba-server-integrated-with-active-directory")) but to be honest, I'm not exactly sure what "Active Directory" is. I'm guessing that's what I want, but I really don't know.

That tutorial uses Kerberos and WinBind, but again, in all honesty, I don't know if that is what I should do.

Bottom line, I've never set up any type of file/print server before, and I'm unsure what prgs I need, or which online tutorials will correctly fit my needs without either being too complicated, or too limited. I know what I want is a very common thing, I'm just not sure which tools are the correct ones to use for my needs and situation.

I also need to take into account that each of the PC's are multi-boot, and so the file access needs to be (relatively) transparent, regardless of which OS happens to be running at the time.

For what it's worth, I've already configured ssh access to the Ubuntu Server. I've also configured TightVNC for Remote Desktop access. So at this time I already have secure access to  shell and desktop on the server. (Eventually I would like Remote Desktop access to the other two machines as well, but that's a job for much later.)

All advice and suggestions will be appreciated. :D

---

### Post by djbon2112 on 2009-10-16
Wow, there's a bunch of questions here, so I'll go through them one by one!

*My goal is to create a central file/print server running on the Ubuntu Server machine.*

Shouldn't be hard at all. For the file server component, all you need is samba, and there are a bunch of guides around (don't worry about HowToForge, it tends to go over advanced setups, not beginner; search these forums instead!) explaining how to get sharing working. A print server is something I haven't done before, but I know you need CUPS and there should be some guides here too.

*As mentioned, some HD's on the server are currently formatted with NTFS partitions, but if it would be better I can easily move that data to ext4 partitions. In other words, I need advice on the benefits of either staying with NTFS, or transferring the data to ext4.*

Well, to use NTFS on Linux you have to use the FUSE driver, which means that there's an extra layer between the driver and hardware. In practice on a desktop the performance penalty is almost nonexistant, but I'm not so sure about a server. If you can, I'd migrate to ext4 just to be safe.

*I am very new at all of this, but I'm learning a few things. I know I need SAMBA, and know I'll need to configure CUPS for the printers (they are currently connected to the server, but not yet configured). I see instructions on HowToForge entitled "Ubuntu 9.04 Samba Server Integrated With Active Directory" (link) but to be honest, I'm not exactly sure what "Active Directory" is. I'm guessing that's what I want, but I really don't know.*

*That tutorial uses Kerberos and WinBind, but again, in all honesty, I don't know if that is what I should do.*

Active Directory is the domain services for Windows, that lets you join and manage a domain, and Kerberos and WindBind are ways for Linux to interface with it. It's a complex thing that you don't need to worry about. I wouldn't pay that particular article much mind because it will just confuse you.

*I also need to take into account that each of the PC's are multi-boot, and so the file access needs to be (relatively) transparent, regardless of which OS happens to be running at the time.*

This should matter at all as long as Samba is configured right, which it is by default ;)

*Bottom line, I've never set up any type of file/print server before, and I'm unsure what prgs I need, or which online tutorials will correctly fit my needs without either being too complicated, or too limited. I know what I want is a very common thing, I'm just not sure which tools are the correct ones to use for my needs and situation.*

Setting this up shouldn't be hard at all, just look for "setting up a samba filserver" and "setting up a cups print server", and you should be able to find basic tutorials. As I said, I've never done the print server before, but here's how to set up a basic file server:

1. SSH into the server and become root. 

```

# ssh user@myserver
<logged into myserver>
# sudo su
[sudo password for user:] ********
$
```

2. Execute the following commands:

```
$ apt-get install samba smbfs 
```

3. That will put Samba and the Samba FS (CIFS) on the server. When that's done, edit the Samba config file:

```
$ nano /etc/samba/smb.conf
```

4. The file contains a bunch of sample entries and various data. Move to the bottom of the file and add a new entry for your share. Here's an example, taken straight from my server, that shares /home/samba as public and lets any user write to it, ensuring any newly created files have full read/write/execute permissions for all users (from my experience, this is needed if you write often to it from Linux).

```

[sambashare]
  comment = This is a public Samba share of /home/samba
  path = /home/samba
  public = yes
  guest ok = yes
  writable = yes

  create mask = 3777
    force create mode = 3777
  directory mask = 3777
    force directory mode = 3777

```

5. Save the file (Ctrl+O to save, Ctrl+X to exit) and restart the Samba daemon

```
$ /etc/init.d/samba restart
```

There you go! You can access the shared directory via the server's IP or hostname.

For more examples of the Samba config file, try this link: [http://www.reallylinux.com/docs/smb.conf](http://www.reallylinux.com/docs/smb.conf)

---

### Post by HighlyDubious on 2009-10-16
Now it's my turn to say "wow"! There's a LOT of good info there! :)

At this moment I'm in the process of editing my fstab and figuring out which partitions I want to automount -vs- which ones I'll manually mount as needed.

Once I finish that, I'll be ready to follow your instructions.

 One thing I could use an extra nudge with is this part:

```
 
  create mask = 3777
    force create mode = 3777
  directory mask = 3777
    force directory mode = 3777

```I understand the '777' part, but what's the '3' doing out in front?

I hope you're right regarding "Active Directory". It does sound complicated. I've never messed with domains, and hopefully none of my versions of Windows (XP,Vista,7) will require it now. So I'll be quite happy to let that sleeping 3-headed dog keep laying right where he is. ;)

I think that for now (just to keep it simple, and get things up and running) I'll keep the files on the NTFS partitions. These 3 HD's (1TB, 1TB, 1.5TB) were removed from various incarnations of previous machines I've built, and there are a LOT of duplicated files. Perhaps the best way to handle things for now is to set up sharing of all the data partitions (4-8 per HD), and spend a while killing all the duplicate or obsolete files (Gee, do I _really_ need this zip of firefox 1.01?). Then once I have distilled them down, I'll move the remainder to a ext4 directory. That whole process should free up probably 2.5TB worth of space! LoL 

Thanks again for your help. I'll post back here if I'm lost or over my head! ;)

---

### Post by cariboo on 2009-10-17
Setting up a print server is really easy using cups, I usually use elinks to access the cups interface at:

```
http://localhost:631
```

elinks is in the repositories, the only thing I do is turn on remote administration, then I exit out and use my main desktop to access the cups web interface using Firefox.

Once at the administration interface click the add printer button and follow the prompts. Once everything is working, make sure **Share printers connected to this system** has a check mark beside it and you're good to go. 

Once you are finished setting things up remember to uncheck **allow remote administration**

---

### Post by djbon2112 on 2009-10-17
> **HighlyDubious said:**
> I understand the '777' part, but what's the '3' doing out in front?

I actually have no idea, but I found it broke when you didn't have it, and someone on here suggested it, and it's worked ever since!

> **HighlyDubious said:**
> I hope you're right regarding "Active Directory". It does sound complicated. I've never messed with domains, and hopefully none of my versions of Windows (XP,Vista,7) will require it now. So I'll be quite happy to let that sleeping 3-headed dog keep laying right where he is. ;)

Yep; as long as you don't think you need a domain, you don't, so it's not something to worry about!

> **HighlyDubious said:**
> I think that for now (just to keep it simple, and get things up and running) I'll keep the files on the NTFS partitions. These 3 HD's (1TB, 1TB, 1.5TB) were removed from various incarnations of previous machines I've built, and there are a LOT of duplicated files. Perhaps the best way to handle things for now is to set up sharing of all the data partitions (4-8 per HD), and spend a while killing all the duplicate or obsolete files (Gee, do I _really_ need this zip of firefox 1.01?). Then once I have distilled them down, I'll move the remainder to a ext4 directory. That whole process should free up probably 2.5TB worth of space! LoL 

Thanks again for your help. I'll post back here if I'm lost or over my head! ;)

Sounds like a plan. I'm still trying to do this on my 2.8 TiB fileserver :p

If you need anything else, just ask!

---

### Post by HighlyDubious on 2009-10-18
OK, I'm missing something very elementary here.

So far I've done the following:

[LIST=1]
[*]Set up the server as suggested above with the following perimeters:.
[LIST=1]
[*]Created a directory (**/home/samba**)
[*]Inside of that I've created mountpoints for all of my partitions.
[*]These partitions are auto-mounted at boot
[/LIST]
 
[*]Set up a Samba user account with password ("**smbpasswd -a username**")
[*]From the Ubuntu machine I've run "**smbclient //servername/sambashare -U username**"
[/LIST]
That part is working and I can see the partitions and files from within a terminal.

What I need next is to be able to access these partitions transparently via a filemanager, such as Dolphin or Nautilus, or ever Windows Explorer. In other words, I need for the various OS' to see and use these partitions the same as any other mounted partition (or network accessible location)

I understand this will entail doing one thing in Ubuntu, and something else from Windows. But for the moment I'm not sure what those things are.

Any further advice will be greatly appreciated! :D

(btw, cariboo907, I've not yet worked on the printer related issues. When I do, you can be assured I'll be asking more from you as well. But for now, I want to thank you for what you've offered so far. :) )

---

### Post by nsche on 2009-10-18
> **HighlyDubious said:**
> ...

 One thing I could use an extra nudge with is this part:

```
 
  create mask = 3777
    force create mode = 3777
  directory mask = 3777
    force directory mode = 3777

```I understand the '777' part, but what's the '3' doing out in front?

...

try 'man chmod' for info on that.  The 3 is an octal value with 2 meaning set group id and the 1 meaning restricted deletion or sticky.  If the 4 bit was set it would mean set user id.  Sticky on some older versions of Unix caused an executable to just be swapped out when it exited so it could just be swapped in when you wanted to run it.  I don't think Linux does that.  On a directory the bit prevents you from deleting a file in the directory unless you own the file or directory (root excepted).

Norm

---

### Post by HighlyDubious on 2009-10-19
> **nsche said:**
> try 'man chmod' for info on that.  The 3 is an octal value with 2 meaning set group id and the 1 meaning restricted deletion or sticky.  If the 4 bit was set it would mean set user id.  Sticky on some older versions of Unix caused an executable to just be swapped out when it exited so it could just be swapped in when you wanted to run it.  I don't think Linux does that.  On a directory the bit prevents you from deleting a file in the directory unless you own the file or directory (root excepted).

Norm
Thanks Norm,

I recognized that it must be an octal value, I just wasn't sure which bits represented what flags. I appreciate you clearing it up for me. :)

---

### Post by cariboo on 2009-10-20
I just mount my partitions in /media and then share them using a very basic /etc/samba/smb.conf.
they look like this:

```
[movies]
             path = /media/movies
             comment = Movies & TV Shows
             guest ok = yes
             writeable = yes
             browseable = yes
```

I have 4 other partitions mounted and shared the same way. One other thing to make sure of is that all the computers are in the same workgroup.

---

### Post by fr3em1nd on 2009-11-15
Wow alot of infos here, im glad ubuntu people helps out each other, im running thesame problem and it works! thanks

---

