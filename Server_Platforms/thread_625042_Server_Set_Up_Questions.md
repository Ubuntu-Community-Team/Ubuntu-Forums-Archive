---
title: "Server Set Up Questions"
date: 2007-11-27
forum: Server Platforms
---

### Post by Deronius on 2007-11-27
I wanted to get a little help setting up a home file/media server using Ubuntu Server 7.10.  I know that the entry at the [_Howto forge_]("http://www.howtoforge.com/perfect_server_ubuntu7.10") has been linked many times and it seems to make sense to me.  However, I do have a few questions to ask about set up.  These may have already been covered in other posts, but I have searched through many of them and I still have a few nagging questions.

NOTE: I think I could accomplish most of what I want if I just set up a desktop machine and shared the drive but I want the experience of managing the server.  I'm relatively comfortable in the command environment...at least I think I am...we'll see...

Using the [_Howto forge_]("http://www.howtoforge.com/perfect_server_ubuntu7.10") post...

[LIST]
[*]If I want to back up a Windows machine to the server and conversely restore to that same computer, I need to create at least one partition that is formatted in NTFS since that's the format the current windows machine in our household uses.  Is that correct?

[*]On the HowTo guide, why wouldn't you install software like DNS, Lamp, etc. when asked in the Ubuntu Server set-up?  The guide instructs to do this later.  What are the advantages to installing later?

[*]On step 5, it explains you can log in remotely to the server with SSH.  Would it be possible to login using a web browser at this point?

[*]On step 7, it explains to assign the static IP address to the server.  This assumes you've forwarded the address from the router correct?

[*]On step 11, I'm not sure what will be filled in when I edit fstab.  Assuming I'll have a NTFS partition along with my swap file and EXT3 partition what exactly would I be adding for lets say.../dev/sda2(NTFS partition)?
[/LIST]

The rest seems to make sense and possibly unnecessary since I don't initially want to open this up to the world.

Thanks in advance and if there are any other suggestions on how to run a good home server please pass them on.

---

### Post by 11hjpphty76lkjj on 2007-11-27
Not sure if this helps but anytime I setup a server I use this:

[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

Good luck!

A

---

### Post by 11hjpphty76lkjj on 2007-11-27
Actually you might be referencing the same doc. :)

---

### Post by Deronius on 2007-11-27
Ah yes, that's actually the link I refer to in the post.  It will be what I follow when I set up the server.  I just a few questions I want to make sure I'm clear on before I begin.

---

### Post by 11hjpphty76lkjj on 2007-11-27
Let me try again..maybe I need more coffee though.

[LIST]
[*]> If I want to back up a Windows machine to the server and conversely restore to that same computer, I need to create at least one partition that is formatted in NTFS since that's the format the current windows machine in our household uses. Is that correct?[/LIST]For backing up the system you might consider using CloneZilla.  It will save the partition as is exactly and I think you can set it up to use a server so that the backed up image is sent to a server and you can restore over the network. For how Clonezilla works you wouldn't need a specific partition type on which to save it, just a place to save it.  I use ext3 for mine, and it works great. But I don't do it over the network although I know this is possible.

[LIST]
[*]> On the HowTo guide, why wouldn't you install software like DNS, Lamp, etc. when asked in the Ubuntu Server set-up? The guide instructs to do this later. What are the advantages to installing later?[/LIST]Not sure on this one sorry.

> On step 5, it explains you can log in remotely to the server with SSH. Would it be possible to login using a web browser at this point?


Depends on how you mean--log in.  You could in theory use webmin to login via the web. But just having apache, mysql and so forth wont give you access to the terminal.
[LIST]
[*]> On step 7, it explains to assign the static IP address to the server. This assumes you've forwarded the address from the router correct?[/LIST]I always skip this step myself, and just leave it dynamic so I can't say.
[LIST]
[*]> On step 11, I'm not sure what will be filled in when I edit fstab. Assuming I'll have a NTFS partition along with my swap file and EXT3 partition what exactly would I be adding for lets say.../dev/sda2(NTFS partition)?[/LIST]This depends on how your drives are partitioned.  What I do is install gparted, run gparted, verify the partition assignments and mounts, compare to what's in the /etc/fstab.  Although with ntfs it may be more complex.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

hmm not sure if this helps. But there ya go. at least it shows I paid a little more attention this time. :)

A

---

### Post by hbohn123 on 2007-11-27
Thanks for that link kalosaurusrex!

---

### Post by doogy2004 on 2007-11-27
I have an idea for what you what but i'm not exactly sure.  Can you be more specific about what you want to be able to do with this server such as:

DNS, proxy, file server(samba/ftp), http/database(lamp), streaming media(xbox/ps3?), No-ip(Dynamic DNS), remote administration (Webmin/ssh/vnc), bittorrent(azureus client), etc?

also please give examples such as:
I want to be able to access my files remotely. OR I want to use bittorrent to download files and be able to access those files remotely or within the network.

---

