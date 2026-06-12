---
title: "mount.cifs permission denied using jaunty"
date: 2009-06-04
forum: Server Platforms
---

### Post by mweichert on 2009-06-04
Hello,

I've been working three days now trying to get CIFS mounts working in Jaunty. I've been using the same config in hardy, feisty, and intrepid which don't get me any grief.

Some details about my setup:
- Joined to AD domain using likewise-open5
- Trying to mount a share called 'sw' on a SAMBA server (netgear nas storage box). This box passes auth to AD on Windows Server 2003.
- The domain is called 'liquor.local'
- smbfs is installed

Here is how I attempt to mount the share:
```

sudo mount.cifs //whiskey/sw /mnt/sw -o username=mweichert,domain=liquor.local,nosuid,nodev,nounix,rw

```

This is what I get in return:
```

[ 7287.832583]  /build/buildd/linux-2.6.28/fs/cifs/cifsfs.c: Devname: //sw/sw flags: 64 
[ 7287.832591]  /build/buildd/linux-2.6.28/fs/cifs/connect.c: CIFS VFS: in cifs_mount as Xid: 20 with uid: 0
[ 7287.832601]  /build/buildd/linux-2.6.28/fs/cifs/connect.c: Domain name set
[ 7287.832605]  /build/buildd/linux-2.6.28/fs/cifs/connect.c: Username: mweichert
[ 7287.832610]  /build/buildd/linux-2.6.28/fs/cifs/connect.c: UNC: \\whiskey\sw ip: 192.168.1.10
[ 7287.832622]  /build/buildd/linux-2.6.28/fs/cifs/connect.c: Socket created
[ 7287.833069]  /build/buildd/linux-2.6.28/fs/cifs/connect.c: sndbuf 16384 rcvbuf 87380 rcvtimeo 0x7fffffffffffffff
[ 7287.833135]  /build/buildd/linux-2.6.28/fs/cifs/connect.c: Existing smb sess not found
[ 7287.833143]  /build/buildd/linux-2.6.28/fs/cifs/cifssmb.c: secFlags 0x7
[ 7287.833148]  /build/buildd/linux-2.6.28/fs/cifs/transport.c: For smb_command 114
[ 7287.833152]  /build/buildd/linux-2.6.28/fs/cifs/transport.c: Sending smb of length 78
[ 7287.833386]  /build/buildd/linux-2.6.28/fs/cifs/connect.c: Demultiplex PID: 19446
[ 7288.113392]  /build/buildd/linux-2.6.28/fs/cifs/connect.c: rfc1002 length 0x5f
[ 7288.113436]  /build/buildd/linux-2.6.28/fs/cifs/cifssmb.c: Dialect: 2
[ 7288.113444]  /build/buildd/linux-2.6.28/fs/cifs/cifssmb.c: negprot rc 0
[ 7288.113449]  /build/buildd/linux-2.6.28/fs/cifs/connect.c: Security Mode: 0x3 Capabilities: 0xf3fd TimeAdjust: 14400
[ 7288.113453]  /build/buildd/linux-2.6.28/fs/cifs/sess.c: sess setup type 2
[ 7288.113535]  /build/buildd/linux-2.6.28/fs/cifs/transport.c: For smb_command 115
[ 7288.113539]  /build/buildd/linux-2.6.28/fs/cifs/transport.c: Sending smb:  total_len 276
[ 7288.119908]  /build/buildd/linux-2.6.28/fs/cifs/connect.c: rfc1002 length 0x27
[ 7288.119941] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
[ 7288.119948]  /build/buildd/linux-2.6.28/fs/cifs/netmisc.c: Mapping smb error code 5 to POSIX err -13
[ 7288.119952]  /build/buildd/linux-2.6.28/fs/cifs/misc.c: Null buffer passed to cifs_small_buf_release
[ 7288.119958]  /build/buildd/linux-2.6.28/fs/cifs/sess.c: ssetup rc from sendrecv2 is -13
[ 7288.119962]  /build/buildd/linux-2.6.28/fs/cifs/sess.c: ssetup freeing small buf ffff88003519b700
[ 7288.119967]  CIFS VFS: Send error in SessSetup = -13
[ 7288.119976]  /build/buildd/linux-2.6.28/fs/cifs/connect.c: CIFS VFS: leaving cifs_mount (xid = 20) rc = -13
[ 7288.119981]  CIFS VFS: cifs_mount failed w/return code = -13

```

Using Nautilus and GVFS works fine. Doing a trace in Wireshark, the difference appears to be that GVFS uses Kerberos, while mount.cifs does not. If I add another option to my comamnd, "sec=krb5", then I get -2 instead of -13.

If I uninstall smbfs, I cannot use the netbios/dns name, 'whiskey', but have to use the ip instead. However, even then I cannot mount the drive as I get this error instead:

```

mount: block device //192.168.1.10/sw is write-protected, mounting read-only
mount: cannot mount block device //192.168.1.10/sw read-only

```

I've created the mountpoint and it is owned by me and has 755 permissions.

Any anyone else experienced such troubles with Jaunty?

Thanks,
Mike

---

### Post by cariboo on 2009-06-04
Have you got your shares set uo properly? What happens when you run in a terminal:

```
smbclient -L <servername> -U%
```

You should get something that looks like this:

```
smbclient -L willy -U%
Domain=[APLUS] OS=[Unix] Server=[Samba 3.3.2]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (willy server (Samba, Ubuntu))
	images          Disk      mounted iso images
	stuff           Disk      whatever fits
	documents       Disk      documents and such
	music           Disk      tunes
	movies          Disk      Movies and TV
	print$          Disk      Printer Drivers
	HPLaserjet      Printer   laser printer
Domain=[APLUS] OS=[Unix] Server=[Samba 3.3.2]

	Server               Comment
	---------            -------
	WILLY                willy server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	APLUS                WILLY
```

---

### Post by mweichert on 2009-06-05
Thank you so much for the reply.

It appears that smbclient is working fine, as I get a list of all shares on the server.

Thanks,
Mike

---

### Post by mweichert on 2009-06-05
Some more info...

When I try mounting a cifs share, this is what appears in smb log on the server (whiskey):

```

check_ntlm_password:  Authentication for user [mweichert] -> [mweichert] FAILED with error NT_STATUS_NO_SUCH_USER

```

I see that successful mounts from hardy+intrepid leave a message like the following:

```

check_ntlm_password:  authentication for user [mweichert] -> [mweichert] -> [LIQUOR\mweichert] succeeded

```

So, the solution/trick is finding out how to get Jaunty to send the netbios name of the domain prepended to the username. The following does NOT work:

```

sudo mount.cifs //sw/sw /mnt/sw -o user=LIQUOR\\mweichert,domain=LIQUOR.LOCAL,nosuid,nodev,nounix,file_mode=0777,dir_mode=0777,uid=1021838565,gid=102183782

```

Thanks,
Mike

---

### Post by mweichert on 2009-06-05
Well, it turns out that having the client authenticate as 'DOMAIN\user' was not the solution. I was able to get the client to authenticate using that form by removing smbfs.

However, still the server would produce:
```

check_ntlm_password:  Authentication for user [LIQUOR\mweichert] -> [LIQUOR\mweichert] FAILED with error NT_STATUS_NO_SUCH_USER

```

Now I'm totally baffled. :(

---

### Post by ytene on 2009-06-14
I have seen a similar and weird problem. My system uses cifs to connect to an Apple Time Capsule. The connection string that I have used, without any problems up until now, has been this:-

# Time Capsule
//192.168.1.40/TimeCapsule/clive /media/capsule cifs password=########,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

What is weird about this error is that I can mount the file system for read operations and it works fine. However, the moment I try to write anything back to the Capsule, for example a document being edited by OOo Writer, I get a popup with the following text:-

Error saving the document DocName:
General Error.
General input/output error

When I check the file system after observing this error, I see a file with the name I would expect, but with zero bytes of length. 

If I then go to the directory, using a shell, and issue a command such as:-

cp inputfile.odt outputfile.odt

I get a copy of the file with no errors or problems. Note that both the OOo Writer and the shell are performed using the same user ID with the same permissions.

If I step up to the next directory level [ though still within the network-mapped share ] and issue a command of

ls -l

I get the following 

drwxrwxrwx 1 root root 0 2009-04-25 20:19 Misc Documents

which kinda matches my expectations given that

1. the TimeCapsule file system is going to be Apple Native, and not Ext3 or other
2. this matches what I've asked for in my fstab entry. 

As with the other poster, I've had this working under previous versions of ubuntu from the time the Time Capsule was released by Apple and all have worked OK thus far. I did start to hit problems when I started to use the Unison file synchronisation tool to keep my local and Capsule directories in synchronisation. This turned out to be because my "local" file systems were in fact FAT32 and had been configured to mount as follows:-

# /dev/sdg5
UUID=47D2-E523	/media/sdg5	vfat	defaults,utf8,umask=007,gid=46 0	1

As you can see from the above, the umask of the FAT32 mount brings up these partitions with root as the owner. Therefore, in order to get the Time Capsule and the local partitions to play nice with Unison, I needed to have both systems mounted with exactly the same permission set. In this case I ended up with root [ I tried a default user but hit a problem of some kind ]. All I had to do was wrap the Unison launcher with kdesudo and I had a very neat, effective solution.

Up until now. 

Would be very, very grateful for advice on how best to proceed. Obviously, will continue tinkering, but the nature of this error [ generation of zero-byte files ] is extremely dangerous, since the system will let me write over the top of a good file, generate an error, and thus destroy the original file as it does so... 

Look forward to your suggestions.

Thanks in Advance

C

---

### Post by cariboo on 2009-06-14
Do you have samba password set on the computer you are trying to mount he shares on? At the prompt type:

```
sudo smbpasswd -L -a <username>
```

and to enable the user:

```
sudo smbpasswd -L -e <username>
```

Plus you may want to have a look at this [thread=288534]howto[/thread]

---

### Post by ytene on 2009-06-21
Hi Cariboo,

Sorry for the delay in responding, and many thanks for the suggestions that you have posted. I had not previously used either the 

sudo smbpasswd -L -a <username>

or

sudo smbpasswd -L -e <username>

commands to configure my SAMBA Client on my Jaunty workstation. I tried these commands, both of which completed successfully but without any change in results.

I then followed your link to the additional article and noticed that the author of that document recommended the use of the username= explicit parameter-set in their fstab entry, so I made that change as well. 

I did notice that if my fstab line read thus:-

//192.168.1.40/TimeCapsule/clive /media/capsule cifs **-o** username={myUser},password={myPassword},rw,iocharset=utf8,file_mode=0777,dir_mode=0777

then the file system would not mount at all. So I removed the -o flag and the following string seemed to work fine:-

//192.168.1.40/TimeCapsule/clive /media/capsule cifs username={myUser},password={myPassword},rw,iocharset=utf8,file_mode=0777,dir_mode=0777


Though I have no concrete evidence either way, I suspect that this variation may be due to the fact that the "Server" computer is in fact an Apple Time Capsule and not a Windows machine of any kind. Just a guess, though. Another important thing to add - I suspect. For ease of management - I keep the passwords synchronised across all my machines, so my Apple Mac and Time Capsule passwords are manually synchronised with my Windows and Linux passwords across all systems. I haven't tried messing with password changes. 

As before, I get the same error message, a pop-up indicating a failure to write to the file system. If the action is to save back a modified version of an existing file, then the original file will be over-written with a zero-byte [empty] file, this losing the original copy if not otherwise archived.

Final piece of weirdness? If I open FireFox and go to a page that has an image on it, I can right-click that image and save that file to the Time Capsule. It *is* sensitive to the permissions set on the remote directory - if I use my ubuntu workstation to create a new directory on the Capsule, permissions are not automatically flowed in [ which I would expect given the fstab mount parameters ] but I can manually tweak that by hand and then write pretty much anything I like from FireFox to the Time Capsule. Go into any OpenOffice program, create a new document and try "File Save As" and the error appears. 

Obviously these two programs are writing to the file system in different ways, but I don't know enough to figure out what the differences are.

When ext4 was released there were a number of articles posted on the web that suggested the new fs was somehow corrupting file systems and losing data. That was followed by a debate which suggested that ext4 was working as advertised, but some programs had failed to use ext3 properly and the issues were somehow related to the way that client applications performed file system buffer flushing. Because we're talking about SMB file systems here, it's very unlikely that what I'm witnessing is related in any way to Ext4... but is there a possibility that this could be something to do with smbfs being upgraded to cope with new releases of Microsoft's Server Message Block protocol? Is there a narrow chance that the implementation on Apple's Time Capsule is somehow using a non-standard implementation of SMB and when the ubuntu package upgraded these two non-native implementations are not playing nice together?

Appreciate that I'm clutching at straws, not to mention being ignorant of the underlying tech, but I ask these questions in the hope that someone can give me an answer that will point me in the direction of my next round of research. 

Happy to try something else if these results suggest anything...

Thanks and Best Regards,

C

---

### Post by ytene on 2009-06-21
Cariboo,

I continued my search for clues and came upon the following Bug Report:-

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/343357](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/343357)

That would suggest the problem has been observed by others. I am going to follow the suggestions at LaunchPad and file a bug report with Apple, just to see what sort of detail they give me in response. If that helps I'll post here.

Best

C

---

### Post by ytene on 2009-07-03
All,

Not yet sure if this will make a difference, but my Apple kit has just deployed new firmware to both my Airport Express and my Time Capsule. Given the target devices, there is every chance that the changes will relate to wireless patches, but one never knows. 

Unfortunately I've had to leave the kit behind and travel away on business, but perhaps, if there are others out there tracking this thread who do have a Time Capsule, they might like to give this a try and let us know if we have progress.

Best Regards

---

