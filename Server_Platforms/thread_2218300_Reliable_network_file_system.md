---
title: "Reliable network file system"
date: 2014-04-20
forum: Server Platforms
---

### Post by akandi on 2014-04-20
Hi
I'm currently setting up a server which will among other things host most of my data.
The goal is to have the data accessible from Windows clients.
One of the requirements is that I can "randomly seek" files i.e. read bytes from the end of the file without first downloading the entire file to the client.
It should also provide reliable protection against file corruption - more on that below.

To my knowledge FTP doesn't provide "random seeking" and therefore can't be used.

I've set up SMB and SFTP on my server and started testing those.
My Windows client for SFTP doesn't do the random seeking, but since SFTP provides resumable up/downloads could it be possible, or couldn't it?

Samba can do random seeking but I've had problems with files corrupting in transit.
(SFTP dropped connections due to corrupted packets and I've had success in switching RX and TX checksum calculation offloading off on the server's NIC.)
 However I'm reluctant to trust that switching off RX/TX offloading will completely fix Samba transfers - I'd prefer something that does some checksum checking to guarantee reliability.

I haven't tried NFS and ISCSI. NFS seems complicated to set up, especially since I'd want NFSv4 with encryption enabled, which would provide the required reliability, right?
ISCSI seems somewhat complicated to set up and I'd have to reformat my drives to NTFS to make them accessible from Windows.

What would your suggestions be?
Thanks in advance.

---

### Post by SeijiSensei on 2014-04-20
NFS isn't well-supported by Microsoft at all.  Its NFS client is [only included]("http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_programs/nfs-client-for-windows-7/42aae25d-d077-4ff9-abdf-7314a589c46d") in Ultimate and Enterprise versions of Windows 7.  I'd imagine Windows 8 is no different.

---

### Post by dudumomo on 2014-04-20
How about using a Web interface like Pydio or Owncloud?
Could set it up with SSL and should be easy to administrate.

---

### Post by akandi on 2014-04-20
Thanks for your answers.
Good to know that NFS isn't really an option.
A web interface is not what I'm looking for, though. I'm enjoying Samba's Windows explorer integration, watching films, opening proprietary file formats with their respective aplication and whatnot just like the harddisk was actually built into the client computer.

When using it read only, Samba has actually provided a pretty enjoyable experience so far. But I'd be furious uploading lots of data to the NAS to find out later that some of it has been corrupted.

This makes me ask myself whether to ditch Samba or what I'd have to do to be able to trust it.

I'll stress test it tomorrow, uploading large chunks of random data and comparing the checksum before and after. This with and without RX/TX offloading enabled.
I'm even thinking about setting up an OpenVPN tunnel within the LAN with --cipher none --auth SHA1, which should be interesting to see how that works.
What are your opinions on this?

---

### Post by SeijiSensei on 2014-04-20
I'd be [s]really surprised[/s] shocked to learn that Samba systematically corrupts files.  It's been in development for well over a decade, and its primary staff includes some really smart programmers.  Have you browsed samba.org and the various forums to see if there is any evidence for such corruption?  If this were a real problem, we'd have heard more about it by now, and it almost certainly would have been fixed.

I've used Samba off and on since version 0.8 or so.  I've never encountered a problem with corruption in real-life applications.

---

### Post by nerdtron on 2014-04-21
^^My thoughts too. We have been using SAMBA for transferring files between server and windows clients and we haven't had any problems.
If you want pause/resume capability in SAMBA, install a third party tool like TeraCopy in windows.
SFTP does support pause/resume if you use filezilla.

Anyway why use encryption on a local network? You transfer rate would be faster with no encryption, less CPU resources too.

---

### Post by akandi on 2014-04-21
Well, I'm not accusing Samba being the culprit of my corrupted files, but something else along the way does corrupt them and Samba doesn't check for it.

I just copied a 35 GB file from my client to the server and compared checksums.
> 
D:\Users\Andi\Downloads\fciv>fciv -md5 G:\a1.zip
//
// File Checksum Integrity Verifier version 2.05.
//
3c72d05031b0b99a1fb0ff85665a599f g:\a1.zip

and
> 
andi@ubuntuserver:/mnt/andi/andi/notebook$ md5sum a1.zip
6aadd7ed3b2edc0afa9a91f4747da9bc  a1.zip

Then after
> 
ethtool -K eth0 tx off rx off

and copying again
> 
andi@ubuntuserver:/mnt/andi/andi/notebook$ md5sum a1.zip
a48ac6b4312b337bf4027c28eaecfca1  a1.zip

so that didn't help.

But now I don't know what to do. Maybe I'll try a VPN tunnel but I expect the overhead to be considerable.
How do I analyze the network to find the culprit of this corruption?

---

