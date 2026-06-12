---
title: "Please Help with SAMBA"
date: 2009-04-26
forum: Server Platforms
---

### Post by Jimmy9pints on 2009-04-26
Hi, I have a server up and running in my house. I was able to instantly get SSH up and running, apache is good and now I believe FTP is fine too - so I can browse my files. But I need to get SAMBA working for the Windows users in the house.

Believe me, I have been trying to resolve this by myself for months so I am not asking for help out of laziness - this is a last resort. 

I have followed many many howtos on the net, most of them pointing out how simple it is to set up samba. Not for me. 

I cannot access the files on the sever from either Ubuntu or Windows. Occasionally, after tweaking the smb.conf (according to one howto or another) I can see the server, (and/or the workgroup it's in) in Places>Network in Ubunut. But clicking on it just gives me an error message:
> Unable to mount location. Failed to retrieve share list from server

My laptop is set up to serve files via samba too - usually I can see that but not always - so even that's not consistent!

What am I doing wrong?


BTW: please tell me what info you need. I could post my smb.conf here but it is only one in a long line of configurations I have used.

---

### Post by bluefrog on 2009-04-26
basically only one howto has to be followed to understand how samba works:

the Samba one.

[http://www.samba.org/samba/docs/man/Samba-Guide/](http://www.samba.org/samba/docs/man/Samba-Guide/)

---

### Post by Jimmy9pints on 2009-04-26
Yeah... cheers for pointing that out. I have seen that mammoth document before but I was rather hoping to get things sorted sometime in the next decade, and since I am a slow reader the 300 plus pages in that document would probably take me a while. 

I'll give the "Implementation" section a go, but if that doesn't work it's clearly more effort than it's worth.

---

### Post by shload on 2009-04-26
are you running ubuntu on your server?  I've had all kinds of issues with ubuntu and samba.  for one I've had issues setting up as well, two i get random drops (like the share will be there one minute but gone the next) and three i get horrendous speeds.

I just got freeNAS up and running on my server and samba seems to be working with out a hitch.  there was little/easy setup, works with all my machines (winXP pro, winXP pro 64bit, ubuntu 8.10, ubuntu 9.04, opensuse 11.1), and speeds were much improved on all but the ubuntu machines.

I haven't looked into this extensively and i'm by no means an expert but i honestly believe that your samba issue is most likely ubuntu caused.  I've read in a post here and there that ubuntu has issues with samba.  Not sure what the deal there is or if it's being worked on.

So I guess my solution for you is to try something other than ubuntu for your server.  Not the best answer sorry I couldn't be any better help there...good luck with this. I'll keep an eye on your post perhaps we'll both get a fix.

---

### Post by cariboo on 2009-04-26
While I agree Freenas is a good solution, it still takes a fair amount of setup. 

To the OP could you type in a terminal on one of your Ubuntu desktop computers:

```
smbclient -L <server> -U%
```

where <server> is your server name or ip address. the results should look something like this:

```
smbclient -L willy -U%
Domain=[APLUS] OS=[Unix] Server=[Samba 3.0.32]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (FreeNAS Server)
	backups         Disk      my home dir backups
	misc            Disk      varous stuff
	media           Disk      music and video files
	data            Disk      document storage
Domain=[APLUS] OS=[Unix] Server=[Samba 3.0.32]

	Server               Comment
	---------            -------
	RISKY                Windows computer
	WILLY                FreeNAS Server

	Workgroup            Master
	---------            -------
	APLUS                WILLY
```

I am using Freenas myself, but the results of the above command were the same when I was running Intrepid on my server. Could you paste the results in your next post.

---

### Post by koenn on 2009-04-26
> **Jimmy9pints said:**
> 
I have followed many many howtos on the net, most of them pointing out how simple it is to set up samba. Not for me. 

I cannot access the files on the sever from either Ubuntu or Windows. Occasionally, after tweaking the smb.conf (according to one howto or another) I can see the server, (and/or the workgroup it's in) in Places>Network in Ubunut. But clicking on it just gives me an error message:


Well, here's another howto or two :
[http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#smb](http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#smb)
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba1.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba1.htm)

they're "bare essentials" : install samba and leave the default config alone except for what's necessary to get 1 share going. Might be worth a shot

Other than that, you might have a protocol / communication problem; the output cariboo907 requested may shed some light on the matter.

---

### Post by Jimmy9pints on 2009-04-26
> but i honestly believe that your samba issue is most likely ubuntu caused

There may be some truth to this, I briefly flirted with Fedora and samba seemed to work fine once I'd got a few permissions issues sorted out.

---

### Post by Jimmy9pints on 2009-04-26
@cariboo907, thanks and here's the output of that:
```
jam@jam-laptop:~$ smbclient -L 192.168.1.11 -U%
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.2.3]

	Sharename       Type      Comment
	---------       ----      -------
	SAMBA           Disk      
	IPC$            IPC       IPC Service (ubuntu server (Samba 3.2.3))
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.2.3]

	Server               Comment
	---------            -------
	FILESERVER           ubuntu server (Samba 3.2.3)
	JAM-LAPTOP           jam-laptop server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            JAM-LAPTOP

```

I don't really want to go down the FreeNAS route because I am fairly familiar with Ubuntu and I want to do other things on it like run apache, torrentflux, have NTFS support, which I believe FreeNAS is not capable of doing. Am I right there?

James

---

### Post by koenn on 2009-04-26
Your laptop appears to be winning the browser elections. The Browser Service is what makes file servers visible in "network neighborhood' on windows, and probably in "Places" in Nautilus is well. 
It might be a good idea to get your file server to always win the browser elections, to have some consistency. 
Config example here :
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#id2572775](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#id2572775)

Shares should be accessible even if they can't be browsed, so you probably have an additional problem.

can you run this command from a Windows host on your network an post the output ?
```
NET USE  * \\fileserver\samba
```

---

### Post by Jimmy9pints on 2009-05-12
> **koenn said:**
> can you run this command from a Windows host on your network an post the output ?
```
NET USE  * \\fileserver\samba
```

@Koenn
Thank you.

the output of that on the Windows machine is:

```
System error 53 has occurred

The network path was not found.
```

When you said "fileserver" you did mean literally type that, didn't you? Rather than the IP address or something?

---

### Post by mysticBoer on 2009-05-12
> **Jimmy9pints said:**
> @Koenn
Thank you.

the output of that on the Windows machine is:

```
System error 53 has occurred

The network path was not found.
```

When you said "fileserver" you did mean literally type that, didn't you? Rather than the IP address or something?


I believe he did not 'literally' mean that. Use the IP or hostname of YOUR server. The command he referred to creates temporary drive mapping in windows (or it should) I think.

---

### Post by koenn on 2009-05-12
> **Jimmy9pints said:**
> 
When you said "fileserver" you did mean literally type that, didn't you? Rather than the IP address or something?
> **mysticBoer said:**
> I believe he did not 'literally' mean that. Use the IP or hostname of YOUR server. The command he referred to creates temporary drive mapping in windows (or it should) I think.
'Fileserver' could be the hostname or domain name of the fileserver, or its IP address. In this case, post #8 suggests that the fileserver is called fileserver, and the share name is "samba", so ...

In case you have name resolution problems on your network, try that same command with the ip address of the file server.

it's indeed a command to map network drives, but in this case we're mainly interested in the errors it produces. This paricular error is common when the hostname doesn't resolve to an address, or when the share doesn't exist.

---

