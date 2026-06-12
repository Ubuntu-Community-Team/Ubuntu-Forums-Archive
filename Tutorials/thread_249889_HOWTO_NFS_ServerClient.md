---
title: "HOWTO: NFS Server/Client"
date: 2006-09-03
forum: Tutorials
---

### Post by malco2001 on 2006-09-03
[B]Why NFS?
[/B]
I simply wanted to experiment with NFS, and couldn't seem to find the documentation here on the forums.  I found using NFS just as easy if not easier than using Samba for sharing between a few of my Unix based systems.  In order to share a folder it only required a single line in a configuration file under /etc/exports, and a single line under /etc/fstab on the client to mount the share on each client at boot.

I mostly edited and moved things around from these guides to make a more complete single guide to getting this working using Ubuntu.  

[http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html](http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html) (for client configuration)
[http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-nfs-mount.html](http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-nfs-mount.html) (for mounting using fstab)
<removed dead link>
[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/network-nfs.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/network-nfs.html) (contains more info about NFS)

**Install NFS Server Support**
at the terminal type
*sudo apt-get install nfs-kernel-server nfs-common portmap*
[COLOR="Red"]When configuring portmap do =not= bind loopback. If you do you can either edit /etc/default/portmap by hand or run:[/COLOR]
[I]sudo dpkg-reconfigure portmap
sudo /etc/init.d/portmap restart[/I]

**Editing /etc/exports**
the /etc/exports file is used for creating a share on the NFS server

invoke your favorite text editor or
*sudo vi /etc/exports*

Here are some quick examples of what you could add to your /etc/exports

For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255

[LIST]
[*]/files 192.168.1.0/24(rw,no_root_squash,async)
[/LIST]

Or for Read Only from a single machine

[LIST]
[*]/files 192.168.1.2 (ro,async)
[/LIST]
save this file and then in a terminal type
*sudo /etc/init.d/nfs-kernel-server restart*

Also aftter making changes to /etc/exports in a terminal you must type
*sudo exportfs -a*

**Install NFS client support**
sudo apt-get install portmap nfs-common

**Mounting manually**
Example to mount server.mydomain.com:/files to /files.  In this example server.mydomain.com is the name of the server containing the nfs share, and files is the name of the share on the nfs server

The mount point /files must first exist on the client machine.   
[I]cd /
sudo mkdir files[/I]

to mount the share from a terminal type

*sudo mount server.mydomain.com:/files /files*

Note you may need to restart above services:
[I]sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-common restart[/I]

**Mounting at boot using /etc/fstab**
Invoke the text editor using your favorite editor, or
*gksudo gedit /etc/fstab*

In this example my /etc/fstab was like this: 
[LIST]
[*]server.mydomain.com:/files  /files   nfs rsize=8192,wsize=8192,timeo=14,intr
[/LIST]
You could copy and paste my line, and change &#8220;servername.mydomain.com:/files&#8221;, and &#8220;/files&#8221; to match your server name:share name, and the name of the mount point you created.
[COLOR="Red"]It is a good idea to test this before a reboot in case a mistake was made. [/COLOR]
type
*mount /files *
in a terminal, and the mount point /files will be mounted from the server.

---

### Post by Jose Catre-Vandis on 2006-09-07
Thanks, this howto made simple what the wiki howto makes look difficult. I can now dispense with the vagaries of samba :-)

---

### Post by InspirationDate on 2006-09-07
Thanks for the howto.  The only problem I ran into was with this line:

> **malco2001 said:**
> save this file and then in a terminal type
*/etc/init.d/nfs-kernel-server restart*

it gave me a bunch of errors until I sudo'd it.

*sudo /etc/init.d/nfs-kernel-server restart*

---

### Post by cgreulich on 2006-09-08
Thank you for writing this!!!  I have been sifting through posts for two days trying to figure out how to share files between my two ubuntu(dapper) pc's.  Your instructions worked the first time I tried them.

---

### Post by malco2001 on 2006-09-11
>  Originally Posted by **malco2001  **
save this file and then in a terminal type
/etc/init.d/nfs-kernel-server restart
> Posted by **InspirationDate**
it gave me a bunch of errors until I sudo'd it.

i edited my post to fix that.  i'm glad it worked so well for all of you.  :)

---

### Post by quad3d@work on 2006-09-12
Had some serious speed problem with Samba. Setting up NFS from your guide works well! Now I'm doing 30-40Mb (gigabit network) per sec instead of 1-3Mb with Samba. Thanks!

---

### Post by jabb on 2006-09-14
thanks for this guide really cool

however I have a bunch of Disks mountet on the server i home dir
and I wanted to just mount the home dir in the client.
I did'nt work. I could not see the subdirs for some reason.

thoug if in export I make explicit what dirs to export where the dirs are disks, then it worked fine after restarting the service and making new mount points of course.

though if someone can explain how to just mount the home of the server that would be great. I did everything as the guide instructed.

---

### Post by mike3k on 2006-09-14
If you're connection to a Linux NFS server from Mac OS X, you need to specify 'insecure' in your exports and map the user IDs since Macs use uid 501 for the first regular user. For my /etc/exports I use:

/home   192.168.0.0/255.255.255.0(rw,async,insecure,all_squash,anonuid=1000,anongid=1000)

---

### Post by p388l3s on 2006-09-15
Thankyou malco2001,

Very precise and to the point, gained access to my freenas box in mere moments once i read this post, now to make sunbird share it's calendar file for both my ubuntu and windows boxes.

Many thanks

Pebbles

---

### Post by probablydrew on 2006-09-15
thanks, I found this helpful, and quite easy to config with the built in nfs module in webmin.  I also experienced a speed increase of about double over samba.

---

### Post by george_apan on 2006-09-18
> **jabb said:**
> thanks for this guide really cool

however I have a bunch of Disks mountet on the server i home dir
and I wanted to just mount the home dir in the client.
I did'nt work. I could not see the subdirs for some reason.

thoug if in export I make explicit what dirs to export where the dirs are disks, then it worked fine after restarting the service and making new mount points of course.

though if someone can explain how to just mount the home of the server that would be great. I did everything as the guide instructed.
Yeah, I have the same problem here. I ended up making new mountpoints and assigning them explicitly as you did. I don't believe there's a fix for this.

Other than that it's a great HOWTO, thank you malco2001! O:)

---

### Post by myname on 2006-09-21
This worked great until I rebooted.  Once I rebooted my client, I lost my mount point to my server.  I do have the fstab modified to contain this:

server.ip.address:/data /mnt/parolee nfs rsize=8192,wsize=8192,timeo=14,intr

any idea why it won't stay mounted when I log in?

---

### Post by george_apan on 2006-09-21
> **george_apan said:**
> Yeah, I have the same problem here. I ended up making new mountpoints and assigning them explicitly as you did. I don't believe there's a fix for this.
I found a workaround for this. I have the mountpoints on the server under /media and I just did an
ln -s /media/example ~/example
Now I can see my mounted drives through the network under the home dir that I'm sharing using their symbolic links. No need to have multiple shares anymore.

**EDIT:** No, sorry, I thought it worked but it didn't. As soon as I added another drive that I was not sharing, the link wouldn't work. Sorry again... :-&

---

### Post by iseebluuue on 2006-09-21
worked great first time around. one minor nuisance. when i boot up the client (my laptop) it seems to take a while for the files from the server to be mounted on the mount point. i'm thinking this could be because a) wireless networking and/or b) the server is an older machine and/or c) the share being mounted is 10+ gigs in size

is that probably the cause or is there something else that can be done? if not, oh well, it still works and that's great!

---

### Post by penguinfan on 2006-09-24
Help a Noob out. I get this error

wayne@asus:~$ sudo mount 192.168.0.2:/home/winninshare /home/winninshare
mount: 192.168.0.2:/home/winninshare failed, reason given by server: Permission denied

I did exactly as you said.I have 2 computers with static IPs with the following in my other computer's exports file
/home/winninshare 192.168.1.1/24(rw,no_root_squash,async)

Sooo, i should be able to mount the winninshare folder on my computer in /home/winninshare? or am i mistaken.

---

### Post by K.Mandla on 2006-09-24
Thanks for the setup. This was exactly what I needed to get some hefty files off two Ubuntu machines with USB 1.1 ports. :shock: Cheers! ;)

---

### Post by etienne.navarro on 2006-10-17
After editing the /etc/exports file run
sudo exportfs -a
then
sudo /etc/init.d/nfs-kernel-server restart

should work then

---

### Post by marx2k on 2006-10-30
Okay so heres the problem with me on this...

The server is working fine because from the machine that's running NFS Server, I can mount NFS mounts as a clinet (using either loopback or internal lan IP).

But if I use a laptop thats on the same lan and do something to the effect of :
'sudo mount 192.168.11.5:/media /test'  
(the same exact line I use on the server machine to mount the NFS share)

it says 'mount to NFS server '192.168.11.5' failed: server is down.'

NFS runs on port 2049 if Im not mistaken and I even opened that up on my router directly to this machine (the server) and it still doesnt work.  Can anyone help with this?

---

### Post by marx2k on 2006-10-30
Chalk one up to stupidity.

One should always make sure the proper files are installed on the client computer before making any posts that shows that one is an idiot :)

---

### Post by dmizer on 2006-10-31
okay ... i'm completely confused.

i have a very small network.  my server only leases 10 dhcp addresses.

how the heck does this:
> 192.168.1.1/24
work out to be a range from 192.168.1.1 - 192.168.1.255 ??

if i edited it incorrectly, it told me that what came after the "/" was the netmask.  so i changed the line to this:
```
192.168.1.1/255.255.255.0
```
which seemed to have no ill effect.

edit: despite my continued confusion as stated above, i still managed to make a working automatic nfs client and server connection on boot. so, i humbly offer my thanks to malco2001.

---

### Post by someusernoob on 2006-10-31
This works really nice, way better then samba - and much faster.

But I have one question, I coulnd't find a solution with a 'quick' google search.

When PC1 is on, and I boot up PC2, fstab automounts the shared folder on PC1. But how do I get PC1 to automount the shared folder on PC2 after PC2 boots up? I can mount it manually, but I thought it would be nice if it happens automaticly.

---

### Post by dmizer on 2006-10-31
as far as i know, there is no way to make a previously booted machine detect that a server share has just come online.

edit: typed "samba" from sheer habit.

---

### Post by someusernoob on 2006-11-01
I'm not using samba, but NFS.

And I indeed couldn't find a program which did it, so today I learned some basic bash scripting, and wrote a script which can detect if the other computer is online, and automaticly mounts the shared folder. If the other computer goes offline it will unmount the shared folder. See:

[http://www.ubuntuforums.org/showthread.php?p=1699752#post1699752](http://www.ubuntuforums.org/showthread.php?p=1699752#post1699752)

---

### Post by marx2k on 2006-11-02
192.168.1.1/24 does not mean 192.168.1.1 - 192.168.1.255 

It means 192.168.1.1 - 192.168.1.24
You would want 192.168.1.1/255 for that effect

---

### Post by neilp85 on 2006-11-03
> **marx2k said:**
> 192.168.1.1/24 does not mean 192.168.1.1 - 192.168.1.255 

It means 192.168.1.1 - 192.168.1.24
You would want 192.168.1.1/255 for that effect

You obviously don't know what you're talking about. 192.168.1.1/24 does exactly what he said it should, allow access to 192.168.1.1-192.168.1.255. An IP address is 32 bits and the /n means the n most significant bits of the IP address must match the given IP address to connect. So in this case the first 24 bits, or the 192.168.1 part must match. As another example if you had 192.168.1.1/8, anything that had an address of 192.x.y.z would be able to connect with the server since each group is 8 bits.

---

### Post by dgermann on 2006-11-04
Hi folks--

Hope you can help with this twist on what you are doing.

My server is a Red Hat 9.0 machine.

My fstab is

```
samba1:/vol22   /sam/vol22      nfs     rw,hard,intr   0       0

```
But when I try to do anything in this /vol22 directory, it says permission denied.

Now I suspect the problem is that my user's uid on my Ubuntu 6.06 box is 1000, while on the red hat 9.0 box it is 1000. I would prefer to change the UID on the Ubuntu box. I tried changing /etc/passwd where it says 1000:1000 to 500:500, and the Ubuntu box no longer lets me do anything (one error message actually said: "You don't exist, go away!"). So I changed that back. I tried changing it to 1000:500 and to 500:1000 but both give me tne permission denied error.

Of course, I might be guessing wrong as to the problem.

Any ideas how I can troubleshoot this?

Thanks!

:- Doug.

---

### Post by dmizer on 2006-11-08
> **dgermann said:**
> Any ideas how I can troubleshoot this?

start with your redhat box. the folder you're trying to connect to (vol22) is where your permission problems are.

don't know anything about RH file structure, so i don't know where /vol22 is, but you won't be able to write to your entire drive.  you'll only be able to write to folders which have user level permissions (eg. /home).

so you can tackle this one in a couple of ways:
1) make a folder on your RH box chmodded so that your RH login (not root) has full read and write access to it.
<or>
2) mount your /home directory instead of /vol22 on your RH box.

this way, your remote access will have write permissions to the folder.

if you want full system read/write access to your RH box, just use ssh/scp

---

### Post by etienne.navarro on 2006-11-08
> **marx2k said:**
> 192.168.1.1/24 does not mean 192.168.1.1 - 192.168.1.255 

It means 192.168.1.1 - 192.168.1.24
You would want 192.168.1.1/255 for that effect

No it doesn't. The x.x.x.x/y notation is [CIDR]("http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing") notation.

192.168.1.1/24 means the IP address of 192.168.1.1 with a CIDR of /24, or class 1 C network, and netmask of 255.255.255.000. This effective means a range from 192.168.1.0 to 192.168.1.255, 256 hosts.
The /255 does not exist. The highest you can get is /32 which is a netmask of 255.255.255.255 or a single IP address.

To better understand: the network mask (netmask) or subnet mask is a number that identifies the part of the IP that is a network address and the part that is a computer address. Think of it in binary as the netmask uses binary 1 values to represent the network portion of an address and binary 0 values to represent the computer address.

The network part is expressed in base 10 (our regular numbering system) and are either values of 0 or 255.
255 is a network byte
0 is a computer byte
other value will be part network, part computer.

The netmask can also be expressed as a single number representing the number of network bits in the address. This is the CIDR slash notation.
E.g. 169.254.5.40/16 is equivalent to 169.254.5.40 with a netmask of 255.255.0.0.
The /16 shows the network portion to be two 8-bit bytes, or 16 bits (8x2). As such there will be 65536 hosts.

The CIDR number comes from the number of 1's in the subnet mask when converted to binary.
The common subnet mask 255.255.255.0 is 11111111.11111111.11111111.00000000 in binary. This adds up to 24 1's, or /24 (pronounced 'slash twenty four').
A subnet mask of 255.255.255.192 is 11111111.11111111.11111111.11000000 in binary, or 26 1's, hence a /26.

sorry neilp85 didn't see your post

---

### Post by dgermann on 2006-11-08
dmizer--

Thanks for being so helpful.

On the redhat server, most of the directories within /vol22 are set to 766 permissions. The /etc/fstab in Ubuntu is 
```
samba1:/vol22   /sam/vol22      nfs     rw,hard,intr   0       0
```
and this shows up as this on the Ubuntu client when mounted as cifs:
```
[root@samba1 vol22]# ls -alh
total 816K
drwxrw-rw-   14 data     data         4.0K Nov  6 19:03 .
drwxr-xr-x   28 root     root         4.0K Oct  4 11:20 ..
drwxrw-rw-    8 data     data         4.0K Jul 16 21:50 comm
drwxrw-rw-  136 data     data         8.0K Nov  2 13:35 data

```

(I have edited out some entries to save space here.)

When mounted as nfs, it reports:
```
doug@doug2:~$ ls -alh /sam/vol22
total 0
?--------- ? ? ? ?                ? /sam/vol22/.
?--------- ? ? ? ?                ? /sam/vol22/..
?--------- ? ? ? ?                ? /sam/vol22/comm
?--------- ? ? ? ?                ? /sam/vol22/data

```

redhat's file structure is generally plain vanilla linux, so /vol22 is a directory just off /, same as /etc or /usr would be.

I wonder if ssh/scp will work since what I am doing is running OOo against these network files?

In any event, I think the redhat box is set up OK. At least it runs OK for accessing these files and directories using a cifs mount.

So what else might I be missing here?

I see you have both a samba and nfs howto, so it sounds like you are the person I need to be talking to!

Thanks for your help.

:- Doug.

---

### Post by dmizer on 2006-11-10
lol ... i also have a fedora core box, but i haven't looked at redhat in so long, i don't know what they're doing over there.

how did you figure out how to configure your redhat box?  if you used this howto to set up both boxes, it's not going to work.  something's missing on the authentication for fedoracore that i haven't had the time to figure out yet.

but ... this looks promising: [http://forums.fedoraforum.org/showthread.php?t=102621](http://forums.fedoraforum.org/showthread.php?t=102621)

---

### Post by dgermann on 2006-11-14
dmizer--

Thanks for your help. Sorry you had to wait for a reply--I was more than a little busy over the weekend and the last two days.

How did I figure out how to set it up? I don't remember. Probably used Webmin originally. Then this spring I tried to set up some other things like yp and almost lost all connectivity. I think I got most of that stuff cleared out. But who knows?

I suppose I could blow away the OS on the redhat box and reinstall it, but after all this time, I am not sure what is on there and what I would have to reinstall. Since it is my primary server, I am more than a little reluctant to even think about that!

I will take a look at the link you have so graciously provided--when I am a little more clear headed. Today has been a day to make me bleary-eyed!

Thanks, dmizer!

---

### Post by Peturrr on 2006-11-15
Thanks for your help!
I just succeeded in creating a general Audio folder on my server, so I have all my music available to every PC.

I am just wondering: Is there anyway to secure the acces? Like: Requiring a password and username or similar. 
I would like to be able to acces my files at my parents house or on the university, but not share them with the public.

---

### Post by Peturrr on 2006-11-15
How lovely....
My complete music collection just got vanished....

I shared the same directory with two entries in exports and the contents of that directory are gone since I mounted it from the other PC.

Is that normal ? ](*,)

Yech, going to find my backup

---

### Post by dmizer on 2006-11-16
> **Peturrr said:**
> How lovely....
My complete music collection just got vanished....

I shared the same directory with two entries in exports and the contents of that directory are gone since I mounted it from the other PC.

Is that normal ? ](*,)

Yech, going to find my backup

um ... why would you have two entries in exports for the same direcotry?  this may be why you had a problem.

---

### Post by hopstah on 2006-11-17
> **penguinfan said:**
> Help a Noob out. I get this error

wayne@asus:~$ sudo mount 192.168.0.2:/home/winninshare /home/winninshare
mount: 192.168.0.2:/home/winninshare failed, reason given by server: Permission denied

I did exactly as you said.I have 2 computers with static IPs with the following in my other computer's exports file
/home/winninshare 192.168.1.1/24(rw,no_root_squash,async)

Sooo, i should be able to mount the winninshare folder on my computer in /home/winninshare? or am i mistaken.

Hey, I don't know if you have gotten this worked out or not, but I'll help you anyway.  the problem is that in the instructions typed up, his network uses 192.168.1.*** for the local ip addresses, while yours uses 192.168.0.***.  if you change exports file to ```
/home/winninshare 192.168.0.1/24(rw,no_root_squash,async)
``` it should work out for you.

---

### Post by unclben on 2006-11-19
Thanks, malco2001! Great how-to. I haven't rebooted yet to test fstab, but it appears that (after a manual mount command) I'm connecting perfectly to my FreeNAS NFS share.

---

### Post by RichJacot on 2006-11-27
Thank You!  Great HowTo!  I just setup my server (dapper) and my son's client (edgy) in like 15 minutes from start to finish.  Great Job!

---

### Post by dgermann on 2006-12-09
Hi--

Just tried this and got this error message:

> mike@earth:~$ sudo dpkg-reconfigure portmap
 * Stopping portmap daemon...                                            [ ok ]
 * Starting portmap daemon...                                            [ ok ]
 * Restoring old RPC service information...                              [ ok ]
There are RPC services which registered with the portmapper
before the configuration was changed.
You need to manually restart them in order for the changes to take effect.
Current registered services:
------------------------------------------------
    100024    1   udp    951  status
    100024    1   tcp    954  status
------------------------------------------------


What does this want me to do? Will a reboot fix it?

Thanks!

---

### Post by dgermann on 2006-12-09
Hi--

OK, got the rest of things set up on the server (earth), then I went to the client (doug2) and followed the steps. When I sudo mount -a, I get:
```

doug@doug2:~$ sudo mount -a
mount: earth:/export failed, reason given by server: Permission denied
```

I have checked the Firestarter firewall and it shows no events and is set to allow localnet/24. Even stopping the firewall makes no difference, so I suspect that is not the problem.

/etc/exports on the server is:
```
/exports 192.168.0.1/24(rw,no_root_squash,async)
```
and the directory /exports has permissions set at 777:
```
drwxrwxrwx   2 doug data 4.0K 2006-12-09 15:30 exports
```

What am I missing?

Thanks!

[edited 20061210:] Found my answer--I had the wrong mount point on the client, and also was pointing to the wrong directory on the server.

---

### Post by dgermann on 2006-12-10
OK, got the nfs mounts to work, but now a major problem: one of the clients on the system is running winxp pro. When this client has a file open, a linux client can also open, edit and save this file. And vice versa. Thus, data corruption is likely.

Is there some way to get nfs and samba to respect each other's file locks? 

I am accessing, creating and editing files in OpenOffice.org.

---

### Post by marx2k on 2006-12-12
Unfortunately with SAMBA *and* with NFS, Im getting a max of 1.5M/sec between two machines.

The Wireless 54Mbps Wireless G Server:
```

ath0      Link encap:Ethernet  HWaddr 00:11:50:D4:FD:E8  
          inet addr:192.168.11.8  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fed4:fde8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:351318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:561541 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31326648 (29.8 MiB)  TX bytes:810895988 (773.3 MiB)


ath0      IEEE 802.11g  ESSID:"000740B6F60A"  
          Mode:Managed  Frequency:2.412 GHz  Access Point:                    00:07:40:C4:3B:5E   
          Bit Rate:48 Mb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/94  Signal level=-58 dBm  Noise level=-95 dBm
          Rx invalid nwid:2  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The 100Mbps wired client:
```

eth1      Link encap:Ethernet  HWaddr 00:40:CA:70:19:A6  
          inet addr:192.168.11.4  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fe70:19a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5977834 errors:0 dropped:0 overruns:1 frame:0
          TX packets:5838991 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1102672825 (1.0 GiB)  TX bytes:4034251400 (3.7 GiB)
          Interrupt:201 Base address:0x2000 

```

The router 'tween the two is a Buffalo Airstation WBR-G54.

What steps should I take to troubleshoot this problem?

---

### Post by RameshRao on 2006-12-14
:-D  Bless you, for this simple HOWTO !!!

Files transfer faster than samba too !!!

Regards,
Ramesh

---

### Post by bodhi.zazen on 2006-12-15
Nice How-to

This thread has been added to the UDSF wiki ([color=blue]thank you Crane[/color])

[NFS_Easy_Way](http://doc.gwos.org/index.php/NFS_Easy_Way)

---

### Post by styven on 2006-12-27
Hi all, 

Getting a bit lost at this point......

"Mounting manually
Example to mount server.mydomain.com:/files to /files. In this example server.mydomain.com is the name of the server containing the nfs share, and files is the name of the share on the nfs server

The mount point /files must first exist on the client machine.
cd /
sudo mkdir files

to mount the share from a terminal type

sudo mount server.mydomain.com:/files /files"

All i want to do is store my music files on my desktop and be able to access them from various laptops around the house over my network. 

How do i know what "mydomain" is called and is it .com? Do i have one?
the files i want to access would be home/styvens/music
I will want this share to be available from boot up on any other computer in the house

Sorry if i appear a bit thick here......

Steve

---

### Post by george_apan on 2006-12-27
> **styven said:**
> Hi all, 

Getting a bit lost at this point......

"Mounting manually
Example to mount server.mydomain.com:/files to /files. In this example server.mydomain.com is the name of the server containing the nfs share, and files is the name of the share on the nfs server

The mount point /files must first exist on the client machine.
cd /
sudo mkdir files

to mount the share from a terminal type

sudo mount server.mydomain.com:/files /files"

All i want to do is store my music files on my desktop and be able to access them from various laptops around the house over my network. 

How do i know what "mydomain" is called and is it .com? Do i have one?
the files i want to access would be home/styvens/music
I will want this share to be available from boot up on any other computer in the house

Sorry if i appear a bit thick here......

Steve
The server.mydomain.com can just be the ip address of your desktop in your LAN, so you could just use:
```
sudo mount 192.168.1.10:/remotefolder /mountpoint
```
for example

Or if you add an entry to your /etc/hosts with that ip and assign a name to it:
```
192.168.1.10 desktop
```
so you could mount it with
```
sudo mount desktop:/remotefolder /mountpoint
```

Of course you should use a static ip and not dhcp for all this to work.

---

### Post by styven on 2006-12-28
Thanks for that,

So i need to find the ip of my desktop and set it to static, which is at the moment set up as dhcp.

Just so i can be pointed in the right direction, my network setup is as follows.

cable setop box (modem) to 4 way router, internet split from router to various laptops etc.

Do i need to do anything different, I was really looking to set up a home server, is this in effect what will happen if i want to access files form the desktop?

Steve

---

### Post by george_apan on 2006-12-28
> **styven said:**
> Thanks for that,

So i need to find the ip of my desktop and set it to static, which is at the moment set up as dhcp.

Just so i can be pointed in the right direction, my network setup is as follows.

cable setop box (modem) to 4 way router, internet split from router to various laptops etc.

Do i need to do anything different, I was really looking to set up a home server, is this in effect what will happen if i want to access files form the desktop?

Steve
Just assign static ips to all the pcs you want to have access to and you'll be fine.

---

### Post by styven on 2006-12-28
Thanks for input so far, still struggling.

I have tried this out on 2 laptops at the moment, 1 being server, 1 being client.
On the client i can't see the shared folder, and also i can't see a folder i have set up to be shared from the client on the 1st laptop.

Please see screenshot of the 1st laptop(server) settings, what am i not doing right?

Steve

---

### Post by george_apan on 2006-12-28
> **styven said:**
> Thanks for input so far, still struggling.

I have tried this out on 2 laptops at the moment, 1 being server, 1 being client.
On the client i can't see the shared folder, and also i can't see a folder i have set up to be shared from the client on the 1st laptop.

Please see screenshot of the 1st laptop(server) settings, what am i not doing right?

Steve
What is your 2nd laptop's (client) ip? Are you restarting nfs with:
```
sudo /etc/init.d/nfs-kernel-server restart
sudo exportfs -a
```
after you make the changes?

Can you ping the server from the client and the other way around?

---

### Post by styven on 2006-12-28
the clients ip is 192.168.1.3
how do i ping?

thanks for your help so far 
steve

---

### Post by styven on 2006-12-28
in a moment of inspiration i typed ping ina terminal, thisis the output for laptop 192.168.1.3

steve

---

### Post by styven on 2006-12-28
I don't seem to be getting any further so can anyone confirm that my etc/exports entry is correct...

# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/home/styven 192.168.1.1/24(rw,no_root_squash,async)

I can ping between both computers
If i go into places/network servers on the client all i can see is Windows Network
NFS is running on the server machine
portmap and nfs-common is running on the client machine
I have run sudo exportfs -a after changes to etc/exports

If i try to mount the server from the client i get the following..............

honeyh@honey:~$ sudo /etc/init.d/portmap restart
* Stopping portmap daemon...                                            [ ok ]
* Starting portmap daemon...                                            [ ok ]
honeyh@honey:~$ sudo /etc/init.d/nfs-common restart
* Stopping NFS common utilities                                         [ ok ]
* Starting NFS common utilities                                         [ ok ]
honeyh@honey:~$ sudo mount 192.168.1.2:/home/styven
mount: can't find 192.168.1.2:/home/styven in /etc/fstab or /etc/mtab
honeyh@honey:~$

Shared Folders shows /home/styven  available on 192.168.1.1/24

Any further help would be appreciated, i feel i am close.

Steve

---

### Post by styven on 2006-12-29
Hi all,

Still no further:( 

I think that maybe my problems are at the client, i do not understand the part about creating a mount point on the client.

I followed the instruction to sudo mkdir files and now have a file in home of the client called styven that i can't do anything with as it's owned by root

Ultimately i want the shared folder from the  server to mounted at boot, but can't at the moment mount it manually...........

please help as this is doing my head in](*,) 

Steve

---

### Post by george_apan on 2006-12-29
> **styven said:**
> I don't seem to be getting any further so can anyone confirm that my etc/exports entry is correct...

# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/home/styven 192.168.1.1/24(rw,no_root_squash,async)

I can ping between both computers
If i go into places/network servers on the client all i can see is Windows Network
NFS is running on the server machine
portmap and nfs-common is running on the client machine
I have run sudo exportfs -a after changes to etc/exports

If i try to mount the server from the client i get the following..............

honeyh@honey:~$ sudo /etc/init.d/portmap restart
* Stopping portmap daemon...                                            [ ok ]
* Starting portmap daemon...                                            [ ok ]
honeyh@honey:~$ sudo /etc/init.d/nfs-common restart
* Stopping NFS common utilities                                         [ ok ]
* Starting NFS common utilities                                         [ ok ]
honeyh@honey:~$ sudo mount 192.168.1.2:/home/styven
mount: can't find 192.168.1.2:/home/styven in /etc/fstab or /etc/mtab
honeyh@honey:~$

Shared Folders shows /home/styven  available on 192.168.1.1/24

Any further help would be appreciated, i feel i am close.

Steve
You have to create your mountpoint. You can do than with
```
sudo mkdir /media/serverhome
```
change serverhome with whatever you like

Then open your fstab file with
```
sudo gedit /etc/fstab
```
and insert a line at the end like this:
```
192.168.1.2:/home/styven /media/serverhome nfs rsize=8192,wsize=8192,timeo=14,intr,noauto
```
careful, because you should also have an empty line at the end of your fstab by using the enter key.

You should then be able to mount the share with
```
sudo mount /media/serverhome
```

---

### Post by styven on 2006-12-29
Well i think i have moved forward, although to get here i had to edit etc/host.allow which was not mentioned as far as i could see in this thread. In it i had to put the line.......

portmap : NFS server 192.168.1.2

So this i did and then tried again.........................

honeyh@honey:~$ sudo /etc/init.d/nfs-common restart
Password:
* Stopping NFS common utilities                                         [ ok ]
* Starting NFS common utilities                                         [ ok ]
honeyh@honey:~$ sudo /etc/init.d/portmap restart
* Stopping portmap daemon...                                            [ ok ]
* Starting portmap daemon...                                            [ ok ]
honeyh@honey:~$ sudo gedit /etc/host.deny:
honeyh@honey:~$ sudo gedit /etc/host.allow:
honeyh@honey:~$ sudo mount 192.168.1.2:styven/Music /home/honeyh/Music
mount to NFS server '192.168.1.2' failed: server is down.
honeyh@honey:~$ sudo mount 192.168.1.2:styven/Music /home/honeyh/styven/Music
Password:
mount to NFS server '192.168.1.2' failed: server is down.
honeyh@honey:~$ sudo mount 192.168.1.2:styven/Music /home/honeyh/styven/Music
Password:
mount: 192.168.1.2:styven/Music failed, reason given by server: Permission denied
honeyh@honey:~$ sudo gedit /etc/host.allow:
honeyh@honey:~$ sudo mount 192.168.1.2:home/styven/Music /home/honeyh/styven/Music
mount: 192.168.1.2:home/styven/Music failed, reason given by server: Permission denied
honeyh@honey:~$

What i don't know at this stage is who is denying permission?

steve

---

### Post by george_apan on 2006-12-29
That should be:
sudo mount 192.168.1.2:**/**home/styven/Music /home/honeyh/styven/Music
Did you forget the slash over there?
Also are you exporting /home/styven/Music exlcusively on 192.168.1.2 or is it /home/styven? I don't think you can mount other directories than the ones you specify in exports.

I never messed with hosts.allow myself...

---

### Post by weremichael on 2007-01-01
I am trying to setup my Ubuntu box (6.10) to serve up files to my mac (X.4.8 ). On the Ubuntu side everything looks good  when I look at the sharing window (correct folder, setup to share 1/24 etc.) on the mac side I followed these [directions]("http://i1.dk/misc/automount_nfs_volumes_on_mac_osx/") however my Ubuntu box id is 1000. So I changed everything to 1000 instead of 500.  When I exportfs -a it says that my mac (named Mr Darcy (I nanoed it as Mr-Darcy)) has non-inet addr. I sadly don't have a clue as to what that means. 

The result is that I cannot see the Ubuntu box when I browse through the network or even when I use the connect to server option on the mac side.

Any advice would be appreciated.


Michael

---

### Post by lyly on 2007-01-02
Hello!

How can I browse the nfs share folder with gnome? I installed a nfs server and client on another computer and I can mount the export manually. But When I click on "Places->Network Servers" I can only see the "Windows network" and not the "Linux network" as said in the documentation...
gnomevfs2 and nfs-client are installed

Thanks for any help!

---

### Post by mcpish on 2007-01-06
> **lyly said:**
> Hello!

How can I browse the nfs share folder with gnome? I installed a nfs server and client on another computer and I can mount the export manually. But When I click on "Places->Network Servers" I can only see the "Windows network" and not the "Linux network" as said in the documentation...
gnomevfs2 and nfs-client are installed

Thanks for any help!

The shared folder will be mounted as a local folder on each of the client machines depending on the mount point you selected for each.  You'd just open whatever file manager you have and go to that local path (not a network path) since NFS treats each share as a local path.

Thanks for posting this great How-To.  I got my sharing working perfectly from my main box to my wireless laptop.  It perfectly mounts the shared folders when I bootup within the range of my Wireless LAN (ie. my house).  NFS seems like a much more elegant Unix solution than samba, ick Windows networking.

---

### Post by lyly on 2007-01-07
Actually my question was about how to discover the nfs share which are not yet mounted but are shared on the network.

---

### Post by dmizer on 2007-01-07
> **lyly said:**
> Actually my question was about how to discover the nfs share which are not yet mounted but are shared on the network.

that's a very good question actually.  nfs equivalent to "smbtree", or a gui ... there's something for xubuntu which can perform that function, but a quick search in synaptic didn't reveal an obvious answer for gnome.

---

### Post by kanna1620 on 2007-01-13
[QUOTE=malco2001;1456895][B]Why NFS?
[/B]
You provided really valuable notes on setting the NFS server.I did what you said, but at last when i attempt to mount the mount point i got an error.The error is:
      **Unsupported mount option: wsize-8192**
what should i do?

---

### Post by squrl on 2007-01-29
Somewhat confused but would like to know how to verify the name of "mydomain.com" and the name of the share

Thanks

---

### Post by matt91 on 2007-02-08
followed every instruction, changed ips and paths to suit my setup and checked them. made sure every location was permissioned to 777 and i still get 


> root@LINUX2:~# mount -a
mount: 192.168.1.1:/_matt failed, reason given by server: Permission denied

fstab is 
> 192.168.1.1:/_matt /home/matt/nfs nfs rsize=8192,wsize=8192,timeo=14,intr

and servers exports is
> /data/storage/SHARE/_matt 192.168.1.1/24(rw,no_root_squash,async)


i am getting really frustrated now, i had samba working until yesterday when i got an update, now the transfer speeds are unusable. i am trying to use nfs for the better speed however i still am keeping samba for windows, where they are also slow acessing the samba shares.

the only other options i think is ftp or ssh, but i dont think this is well suited for transferring large files across a network and mounting like nfs and samba are supposed to.

---

### Post by paulius on 2007-02-14
> **mike3k said:**
> If you're connection to a Linux NFS server from Mac OS X, you need to specify 'insecure' in your exports and map the user IDs since Macs use uid 501 for the first regular user. For my /etc/exports I use:

/home   192.168.0.0/255.255.255.0(rw,async,insecure,all_squash,anonuid=1000,anongid=1000)

I hate digging up old threads, but I think that my tip is quite useful for people who'll be googling in the future and stumble on this thread.

I recommend using NFS Manager. It's a very small app which handles NFS configurations on OS X. And it can also enable communication via the secure port. I don't know how I'd live without it. Get it here: [http://www.bresink.com/osx/NFSManager.html](http://www.bresink.com/osx/NFSManager.html)

---

### Post by dannyboy79 on 2007-02-19
> **paulius said:**
> I hate digging up old threads, but I think that my tip is quite useful for people who'll be googling in the future and stumble on this thread.

I recommend using NFS Manager. It's a very small app which handles NFS configurations on OS X. And it can also enable communication via the secure port. I don't know how I'd live without it. Get it here: [http://www.bresink.com/osx/NFSManager.html](http://www.bresink.com/osx/NFSManager.html)


well are you saying that this works for ubuntu? I thought mac os x used a different filesystem  than linux? can you comment on this?

---

### Post by Vincent_Lin on 2007-03-01
Guys,

Great howto and great discussion string.  I did as told and I have an NFS server with 3 clients able to nfs into the server - one wired desktop and two wireless laptops.

I have a question: what is the optimal setting for wireless 802.11g networking with sometimes huge files tranfer (3 -7 GB of DVD image)?  This howto uses rsize=8192,wsize=8192,timeo=14,intr
Does anyone have better setting for 802.11g networking for this big file tranfer?  Or a pointer for a more sensibe documentation for nfs client?

My problem is that copying a DVD image, say 5 GB, would always stop somewhere, resume itself, and sometimes stop completely.  I did not time the tranfer speed, but it seems much slower than that ftp tranfer, when it works.  

Thanks.  All my machines are 6.10.  Server is on Core Duo, desktop is P4 2.6 and Centrino for laptops.

Vincent

---

### Post by tyusoff on 2007-03-09
Thanks malco2001 for the guide.

However, I still got a problem when tried to mount the shared folder. I will explain my network setup below:

Host:                                        Client:
Global IP                                   Internal IP connected through router with Global IP

I have followed the setup as shown by malco2001. edited /etc/hosts as below

/home/myhome/shared    *(rw,async)

then: 

sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ ok ] 
 * Unexporting directories for NFS kernel daemon...                      [ ok ] 
 * Exporting directories for NFS kernel daemon...                        [ ok ] 
 * Starting NFS kernel daemon                                            [ ok ] 
sudo exportfs -a

now at the client, 

mkdir sharefolder
sudo mount host:/home/myhome/shared ~/sharefolder

but this comes out
mount: host:/home/myhome/shared failed, reason given by server: Permission denied

when i run: showmount -e host
Export list for host:
/home/myhome/shared *

Ok the reason I used * instead of IP or client host name because I got error when using it in /etc/exports. Is there any other way to mount it? I have changed the permission of the shared folder using chmod 777. Could anyone help to point out my mistake?? 

Thanks ..

---

### Post by dannyboy79 on 2007-03-09
you can't use a * to define which computers can connect to the share, at least I don't think so. here is a guide with more specific details and a little more explaination, it's for gentoo but applies. [http://gentoo-wiki.com/HOWTO_Share_Directories_via_NFS#Modify_EXPORTS](http://gentoo-wiki.com/HOWTO_Share_Directories_via_NFS#Modify_EXPORTS)

also, do you have any rules for iptables? you can find out by typing in a terminal
sudo iptables -L

if this returns anything, than it's poossible that your nfs seerver isn't allowing any connections to it. again the gentoo guide will help. I am sure if you follow the guide you'll be a-ok!

or you could read post 39 of this thread as a guy had the exact same issue and solved it due to him calling the wrong mount points out in botht the client and the server. to make sure it's not the tilde (~), make sure you use full directory locations, /home/username/ instead.

---

### Post by MobiusNZ on 2007-03-10
Hey guys, I'm having a problem accessing my NFS share from my client pc. The server is a debian(sarge) and the client is a kubuntu(edgy).

I can successfully mount my exported share on the client, and see the following message in the server's syslog:
```

rpc.mountd: authenticated mount request from 192.168.1.101:1002 for /multimedia/music (/multimedia/music)

```

So I thought I was made. Unfortunately, when I tried to cd into this mounted directory on the client, I got the following:
```

al@griff:~$ cd /multimedia/music
bash: cd: /multimedia/music: Permission denied

```
Even if i try as root:
```

al@griff:~$ sudo bash
Password:
root@griff:~# cd /multimedia/music
bash: cd: /multimedia/music: Permission denied
root@griff:~#

```
If i try and check the permissions for files in that directory, I get the following:
```

root@griff:/multimedia# ls -alh /multimedia/music
total 0
?--------- ? ? ? ?                ? /multimedia/music/.
?--------- ? ? ? ?                ? /multimedia/music/..
?--------- ? ? ? ?                ? /multimedia/music/7Music
?--------- ? ? ? ?                ? /multimedia/music/allmusicrandom.m3u
?--------- ? ? ? ?                ? /multimedia/music/allmusicrandom.wsx
?--------- ? ? ? ?                ? /multimedia/music/Chillout
?--------- ? ? ? ?                ? /multimedia/music/chillout.m3u
?--------- ? ? ? ?                ? /multimedia/music/Comedy
?--------- ? ? ? ?                ? /multimedia/music/Desktop.ini
?--------- ? ? ? ?                ? /multimedia/music/lost+found
?--------- ? ? ? ?                ? /multimedia/music/Misc Rock (Unsorted)
?--------- ? ? ? ?                ? /multimedia/music/Music
?--------- ? ? ? ?                ? /multimedia/music/New
?--------- ? ? ? ?                ? /multimedia/music/NVIDIA-Linux-x86-1.0-8774-pkg1.run
?--------- ? ? ? ?                ? /multimedia/music/Old School
?--------- ? ? ? ?                ? /multimedia/music/Rap (Unsorted)
?--------- ? ? ? ?                ? /multimedia/music/Ripped By WMP
?--------- ? ? ? ?                ? /multimedia/music/Techno
?--------- ? ? ? ?                ? /multimedia/music/Thumbs.db
?--------- ? ? ? ?                ? /multimedia/music/Various
?--------- ? ? ? ?                ? /multimedia/music/Wierd.Random

```

So it appears it can kind of see whats going on, but something weird is blocking normal access. I've tried chmodding and chowning on both the client and the server to no avail. Can anybody help?

---

### Post by dannyboy79 on 2007-03-12
> **MobiusNZ said:**
> Hey guys, I'm having a problem accessing my NFS share from my client pc. The server is a debian(sarge) and the client is a kubuntu(edgy).

I can successfully mount my exported share on the client, and see the following message in the server's syslog:
```

rpc.mountd: authenticated mount request from 192.168.1.101:1002 for /multimedia/music (/multimedia/music)

```

So I thought I was made. Unfortunately, when I tried to cd into this mounted directory on the client, I got the following:
```

al@griff:~$ cd /multimedia/music
bash: cd: /multimedia/music: Permission denied

```
Even if i try as root:
```

al@griff:~$ sudo bash
Password:
root@griff:~# cd /multimedia/music
bash: cd: /multimedia/music: Permission denied
root@griff:~#

```
If i try and check the permissions for files in that directory, I get the following:
```

root@griff:/multimedia# ls -alh /multimedia/music
total 0
?--------- ? ? ? ?                ? /multimedia/music/.
?--------- ? ? ? ?                ? /multimedia/music/..
?--------- ? ? ? ?                ? /multimedia/music/7Music
?--------- ? ? ? ?                ? /multimedia/music/allmusicrandom.m3u
?--------- ? ? ? ?                ? /multimedia/music/allmusicrandom.wsx
?--------- ? ? ? ?                ? /multimedia/music/Chillout
?--------- ? ? ? ?                ? /multimedia/music/chillout.m3u
?--------- ? ? ? ?                ? /multimedia/music/Comedy
?--------- ? ? ? ?                ? /multimedia/music/Desktop.ini
?--------- ? ? ? ?                ? /multimedia/music/lost+found
?--------- ? ? ? ?                ? /multimedia/music/Misc Rock (Unsorted)
?--------- ? ? ? ?                ? /multimedia/music/Music
?--------- ? ? ? ?                ? /multimedia/music/New
?--------- ? ? ? ?                ? /multimedia/music/NVIDIA-Linux-x86-1.0-8774-pkg1.run
?--------- ? ? ? ?                ? /multimedia/music/Old School
?--------- ? ? ? ?                ? /multimedia/music/Rap (Unsorted)
?--------- ? ? ? ?                ? /multimedia/music/Ripped By WMP
?--------- ? ? ? ?                ? /multimedia/music/Techno
?--------- ? ? ? ?                ? /multimedia/music/Thumbs.db
?--------- ? ? ? ?                ? /multimedia/music/Various
?--------- ? ? ? ?                ? /multimedia/music/Wierd.Random

```

So it appears it can kind of see whats going on, but something weird is blocking normal access. I've tried chmodding and chowning on both the client and the server to no avail. Can anybody help?


this guide has a lot of troubleshooting tips under the hints section. this should get you squared away:
[http://gentoo-wiki.com/HOWTO_Share_Directories_via_NFS#Hint](http://gentoo-wiki.com/HOWTO_Share_Directories_via_NFS#Hint)

good luck

---

### Post by MobiusNZ on 2007-03-12
OK I got onto the right track when I discovered that normal users on the server couldn't even browse through these (local) directories - I had been setting everything up so was using root.

I couldn't figure out why a normal user couldn't read the directory when it was chmodded as 766. On a whim, I tried changing it to 777. Presto! It worked!

It seems strange that I'd never found any documentation saying that you needed execute permissions to be able to cd to a directory - this sort of stuff is invaluable.

Thanks to everyone for their help.

---

### Post by chartman on 2007-03-13
Thanks for the guide! I have used it and got it working ONE WAY (using my laptop as server and my desktop as client). Both are running kubuntu edgy. If I try to mount a directory on the desktop from the laptop however (using "sudo mount DESKTOP:/home /xyz") nothing happens.
In the syslog of the DESKTOP I find entries like

Mar 13 22:54:52 DESKTOP kernel: [17189943.736000] Inbound IN=eth1 OUT= MAC=00:00:21:f1:f1:73:00:18:de:d5:4c:7f:08:00 SRC=192.168.1.102 DST=192.168.1.101 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=16403 DF PROTO=TCP SPT=40792 D
PT=111 WINDOW=5840 RES=0x00 SYN URGP=0

What does this mean? Does it point to some setup problem?

---

### Post by MobiusNZ on 2007-03-13
Have you enabled the NFS file system support? Kubuntu doesn't by default. The easiest way is to install the server software. 

```

sudo apt-get install nfs-common nfs-kernel-server

```

---

### Post by chartman on 2007-03-13
I have... and it works in one way, so I am pretty sure I did it correctly. I think it must be a security setting somewhere... meanwhile, I have tried to access my web server or used telnet or ftp (just to try) and I got similar messages in syslog. (just the portnumber changed from PT=111 to PT=80, PT=21 or PT=23 depending on what I tried). I have emptied both hosts.deny and hosts.allow and restarted the portmapper afterwards... still the same.

---

### Post by Mr. C. on 2007-03-14
> **someusernoob said:**
> But I have one question, I coulnd't find a solution with a 'quick' google search.

When PC1 is on, and I boot up PC2, fstab automounts the shared folder on PC1. But how do I get PC1 to automount the shared folder on PC2 after PC2 boots up? I can mount it manually, but I thought it would be nice if it happens automaticly.

The autofs automounter provides this.  It mounts file systems upon reference.  There is no need for any scripts.

See Week 4 "NFS / Automounter" notes and lab work at :  [http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

MrC

---

### Post by flange on 2007-03-14
> **Mr. C. said:**
> The autofs automounter provides this.  It mounts file systems upon reference.  There is no need for any scripts.

See Week 4 "NFS / Automounter" notes and lab work at :  [http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

MrC

Thanks for the link.  I got autofs working with my NFS server with help from the PPT file on this site.

---

### Post by Mr. C. on 2007-03-14
Great!  I'm glad you found the materials useful.

Cheers,
MrC

---

### Post by joehill on 2007-03-20
Excellent How-to.  I have a suggestion for an addition (which one reader suggested above) that may save some clueless readers like myself hours of looking for a needle in a haystack.  Users with edited  /etc/hosts.allow and /etc/hosts.deny files may need to updated these files, either not to deny anyone (probably ok since it only listens locally) or, to be more secure, like this:

/etc/hosts.deny has to have this:
portmap: ALL

and /etc/hosts.allow has to have this:
portmap: 192.168.1. ALLOW

This blocks nfs to remote computers.  I had originally had it set to deny but not to allow so I was getting this error:
mount: server:/home/joseph/files failed.
[with no explanation for why]

---

### Post by foxxx on 2007-03-25
nice how-to, could someone make it sticky? :popcorn: 

another edit:
second last line:
mount /files -> SUDO mount /files :) 

could you try to distinguish between /files (mounting point/client-side) and /files (shared folder/server-side)?
so just in case a n00b like me doesn´t mix them up... :lolflag:

---

### Post by SonicSteve on 2007-04-06
I'm hoping someone can help me with this.
I have 2 ubuntu computers both running Edgy.

I have an NFS share on PC called ubuntu, the share is called UbShr
The other computer is called Ubuntu-desktop (very original I know)

I need to have read and write access to the files and folders.

My FSTAB entry on ubuntu-desktop is this
192.168.0.107:/UbShr /mnt/UbuntuSh nfs rsize=8192,wsize=8192,timeo=14,intr
I followed this NFS how to 


My exports entry is this (on ubuntu)
/media/maxtor/UbShr /192.168.0.1/24(rw.no_root_squash,async)
again I followed this same NFS how to guide.

I however get this error.
steve@Ubuntu-desktop:/mnt$ sudo mount -a
mount: 192.168.0.107:/UbShr failed, reason given by server: Permission denied


I know the IP of the computer is right (192.168.0.100) it's static on the router. Is it seeing the server but the server denies the mount. WHY?

I have restarted NFS kernel, exportfs -a and -r. I added lines in the hosts files of each computer.


I can ping the ip of the ubuntu pc but only by address not by name. By name gives me this;
ping: unknown host //ubuntu
Yes I need help.

---

### Post by Mr. C. on 2007-04-06
There is a permissions problem with one of your exported directories:

```
ls -ld /media/maxtor/UbShr
ls -ld /media/maxtor
ls -ld /media
```

All exported files and directories under the export directory need to provide sufficient privs for the mounting user (eg. all directories need to be at least 555, and UbShr needs to be 777). 

MrC

---

### Post by SonicSteve on 2007-04-06
OK so I chmod'd the folders to 777, you were right the permissions weren't set right.
I then restarted the exportfs -a -r
I then restarted the NFS kernel

Now the bad news. 
/media/maxtor/UbShr has been changed to 777
/media/maxtor has been changed to 777
**I still have permission denied**

Both computers are setup with the same user accounts and passwords (steve and *******) 
Is there something samba's smbpasswd that needs to be done for NFS to work? Is there an NFS account that needs to be made?

The ip of ubuntu is 192.168.0.107
the ip of ubuntu-desktop is 192.168.0.100


I have something very strange happening on my ubuntu-desktop pc. Even though all entries the samba share have been commented out in the FSTAB file I have a persistent mount happening in 
/mnt/UbSh
I don't know why it's mounting. I can reboot and it's still there. No entries in the FSTAB though.  The folder is being shared both as SMB and NFS on the ubuntu pc does this matter? I noticed that the "shared folders" aplet doesn't seem to handle this very well.

---

### Post by dannyboy79 on 2007-04-06
when you first boot up, what does the command 

mount

return, please paste the entire output. also, samba has nothing to do with NFS, they are 2 completely different protocols. also post

sudo cat /etc/fstab

sudo iptables -L

ls -la /media

and just because you see a folder called /mnt/UbSh doesn't mean that a samba network share is being mounted there. it just a folder on your computer. if there is stuff there, than that means that you put stuff there when the network share wasn't mounted so it's basically taking up room on the parititon that is mounted at /. unless of course you haev a seperate partition for /mnt but most don't. so make sure you post back everything I have asked and I can most likely help.

---

### Post by SonicSteve on 2007-04-06
Quote;
*and just because you see a folder called /mnt/UbSh doesn't mean that a samba network share is being mounted there. it just a folder on your computer. if there is stuff there, than that means that you put stuff there when the network share wasn't mounted so it's basically taking up room on the parititon that is mounted at /. unless of course you haev a seperate partition for /mnt but most don't. so make sure you post back everything I have asked and I can most likely hel*p.

Unfortunately it is there. I stopped samba on the server and the files aren't there anymore. For some reason the share is being mounted without any reference in the FSTAB file. Yes I know it's strange but its true!
It may even have something to do with the access problem I'm experiencing. The trouble is I don't know.

---

### Post by SonicSteve on 2007-04-06
OK,
So between Samba and NFS I tried using dmizer's unicode how to for samba shares and It worked.
The ghost mount of the share is gone and a proper RW share is established using samba.

I would really like to solve this NFS issue as well. It seems like it should be a good tool.

---

### Post by dannyboy79 on 2007-04-06
if you want my help than you need to provide what I asked for otherwise I can't help you troubleshoot if you don't give me any info.....   post the output of everything i asked for as well as the following 

sudo cat /etc/exports

ls -la /etc/init.d | grep nfs

ls /mnt/

---

### Post by SonicSteve on 2007-04-06
Thanks for you willingness to help dannyboy79 I'll get to it tomorrow. I hope you're having a good Easter.

---

### Post by Jose Catre-Vandis on 2007-04-07
> **SonicSteve said:**
> I'm hoping someone can help me with this.
I have 2 ubuntu computers both running Edgy.

I have an NFS share on PC called ubuntu, the share is called UbShr
The other computer is called Ubuntu-desktop (very original I know)

I need to have read and write access to the files and folders.

My FSTAB entry on ubuntu-desktop is this
192.168.0.107:/UbShr /mnt/UbuntuSh nfs rsize=8192,wsize=8192,timeo=14,intr
I followed this NFS how to 


My exports entry is this (on ubuntu)
/media/maxtor/UbShr /192.168.0.1/24(rw.no_root_squash,async)
again I followed this same NFS how to guide.

I however get this error.
steve@Ubuntu-desktop:/mnt$ sudo mount -a
mount: 192.168.0.107:/UbShr failed, reason given by server: Permission denied


I know the IP of the computer is right (192.168.0.100) it's static on the router. Is it seeing the server but the server denies the mount. WHY?

I have restarted NFS kernel, exportfs -a and -r. I added lines in the hosts files of each computer.


I can ping the ip of the ubuntu pc but only by address not by name. By name gives me this;
ping: unknown host //ubuntu
Yes I need help.

Try giving the full path to UbShr e.g.
```
 #NFS Shares
192.168.0.107:/media/maxtor/Ubshr /mnt/UbuntuSh etc etc
```

---

### Post by SonicSteve on 2007-04-07
> **Jose Catre-Vandis said:**
> Try giving the full path to UbShr e.g.
```
 #NFS Shares
192.168.0.107:/media/maxtor/Ubshr /mnt/UbuntuSh etc etc
```

Alas,
sudo mount -a gives
mount: ubuntu:/media/maxtor/UbShr failed, reason given by server: Permission denied

I'll have to get working on the output of Dannyboy79's commands.

---

### Post by SonicSteve on 2007-04-07
> **dannyboy79 said:**
> if you want my help than you need to provide what I asked for otherwise I can't help you troubleshoot if you don't give me any info.....   post the output of everything i asked for as well as the following 

sudo cat /etc/exports

ls -la /etc/init.d | grep nfs

ls /mnt/

OK so here goes,
[SIZE="1"]steve@ubuntu:~$ sudo cat /etc/exports
Password:
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#

/media/maxtor/UbShr /192.168.0.1/24(rw,no_root_squash,async)[/SIZE]



[SIZE="1"]steve@ubuntu:~$ ls -la /etc/init.d | grep nfs
-rwxr-xr-x   1 root root 1087 2006-10-06 07:34 mountkernfs.sh
-rwxr-xr-x   1 root root  615 2006-10-06 07:34 mountnfs-bootclean.sh
-rwxr-xr-x   1 root root 6020 2006-08-31 14:38 nfs-common
-rwxr-xr-x   1 root root 3830 2006-08-31 14:38 nfs-kernel-server
-rwxr-xr-x   1 root root 1833 2006-10-06 07:34 umountnfs.sh
-rwxr-xr-x   1 root root 1939 2006-10-06 07:34 waitnfs.sh[/SIZE]


ls /mnt/
Had absolutely no output

---

### Post by SonicSteve on 2007-04-07
> **dannyboy79 said:**
> when you first boot up, what does the command 

mount

return, please paste the entire output. also, samba has nothing to do with NFS, they are 2 completely different protocols. also post

sudo cat /etc/fstab

sudo iptables -L

ls -la /media

and just because you see a folder called /mnt/UbSh doesn't mean that a samba network share is being mounted there. it just a folder on your computer. if there is stuff there, than that means that you put stuff there when the network share wasn't mounted so it's basically taking up room on the parititon that is mounted at /. unless of course you haev a seperate partition for /mnt but most don't. so make sure you post back everything I have asked and I can most likely help.

steve@ubuntu:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  


steve@ubuntu:~$ ls -la /media
total 28
drwxr-xr-x  7 root  root  4096 2007-03-13 21:19 .
drwxr-xr-x 21 root  root  4096 2007-03-23 15:09 ..
lrwxrwxrwx  1 root  root     6 2006-11-16 15:28 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2006-11-16 15:28 cdrom0
drwxr-xr-x  2 root  root  4096 2006-11-16 15:28 cdrom1
lrwxrwxrwx  1 root  root     7 2006-11-16 15:28 floppy -> floppy0
drwxr-xr-x  2 root  root  4096 2006-11-16 15:28 floppy0
drwxrwxrwx  6 steve steve 4096 2007-02-23 11:53 maxtor
drwxr-xr-x  2 root  root  4096 2006-11-20 13:59 mp3


Edit;
I just realized that I assumed something.
You wanted these commands run on the server (I use that term loosely, it serves files but is not actually an Ubuntu server install)
I did run them on the server if you want info from the workstation let me know.

---

### Post by Jose Catre-Vandis on 2007-04-08
Um, you have installed portmap and nfs-common on your client? (Just checking, i did it once too :-))

---

### Post by xpod on 2007-04-08
Thanks for the guide:) 

I came close to posting a cry for help there after getting some silly permissions error half the morning...and some of the afternoon but eventually realised i had a "192.168.1.2" in my exports file as apose to the "192.168.0.2"it should have been](*,)

NOW we can go to the funfair kids :twisted: 
Happy easter ppl

---

### Post by indigoshift on 2007-04-09
I'm having a similar problem to the dude with the melon on his head. ;)

I went about the shared folder setup a little differently, though.  I just used the "Shared Folders" app (under System->Administration) on the machine doing the sharing, which is running 7.04.

My laptop (running 6.06) can't see the shared folder no matter what I do.  Following the tuturial here isn't fixing the "Permission Denied" error, unfortunately.

On the bright side, remote desktop works like a champ. :D

---

### Post by dannyboy79 on 2007-04-09
> **indigoshift said:**
> I'm having a similar problem to the dude with the melon on his head. ;)

I went about the shared folder setup a little differently, though.  I just used the "Shared Folders" app (under System->Administration) on the machine doing the sharing, which is running 7.04.

My laptop (running 6.06) can't see the shared folder no matter what I do.  Following the tuturial here isn't fixing the "Permission Denied" error, unfortunately.

On the bright side, remote desktop works like a champ. :D

the shared folder is only for setting up folders to share thru samba. I don't think you can share the same folders thru samba and NFS but I don't know for sure. If you followed the guide you wouldn't have made those folders shared thru the shared folder gui. just follow the guide.

---

### Post by dannyboy79 on 2007-04-09
> **SonicSteve said:**
> steve@ubuntu:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  


steve@ubuntu:~$ ls -la /media
total 28
drwxr-xr-x  7 root  root  4096 2007-03-13 21:19 .
drwxr-xr-x 21 root  root  4096 2007-03-23 15:09 ..
lrwxrwxrwx  1 root  root     6 2006-11-16 15:28 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2006-11-16 15:28 cdrom0
drwxr-xr-x  2 root  root  4096 2006-11-16 15:28 cdrom1
lrwxrwxrwx  1 root  root     7 2006-11-16 15:28 floppy -> floppy0
drwxr-xr-x  2 root  root  4096 2006-11-16 15:28 floppy0
drwxrwxrwx  6 steve steve 4096 2007-02-23 11:53 maxtor
drwxr-xr-x  2 root  root  4096 2006-11-20 13:59 mp3


Edit;
I just realized that I assumed something.
You wanted these commands run on the server (I use that term loosely, it serves files but is not actually an Ubuntu server install)
I did run them on the server if you want info from the workstation let me know.

I see other stuff relating to nfs within your /etc/init.d/ folder. DId you try to get automount to work with nfs? this could be the confussion. You can't share the same folder with automount and then do something manually with using your fstab file and nfs. I believe this is your issue I can't seem to find anything else. you already know you can't share the same folder with samba and nfs, at least not at the same time, you'll get premission denied because it's already mounted. and yes, I also need to 
see some output from the workstation as that's the machine you're getting the access denided error on. I am betting that you have somethign in the workstation (client) that is already calling for this share. good luck

---

### Post by SonicSteve on 2007-04-09
> **Jose Catre-Vandis said:**
> Um, you have installed portmap and nfs-common on your client? (Just checking, i did it once too :-))

Ya, I double checked portmap since I'm not very familiar with it. The're both installed.

---

### Post by indigoshift on 2007-04-09
> **dannyboy79 said:**
> the shared folder is only for setting up folders to share thru samba. I don't think you can share the same folders thru samba and NFS but I don't know for sure. If you followed the guide you wouldn't have made those folders shared thru the shared folder gui. just follow the guide.

Gotcha. I'll give that a go.  Thanks!  :D

EDIT:  Still not working.  Giving the same "Permission Denied" error.  :(

---

### Post by dannyboy79 on 2007-04-10
here's a link that helped out another guy who haad this same permission error.

[http://forums.debian.net/viewtopic.php?t=577&view=next&sid=04e47105763a6e1ca97e50493081214c](http://forums.debian.net/viewtopic.php?t=577&view=next&sid=04e47105763a6e1ca97e50493081214c)

---

### Post by ]Nbx*cmD[ on 2007-05-02
Hi all,

I followed this howto and didn't get it working, for some reason I really can't understand.

This is the message i get when trying to mount:

```

mount to NFS server '192.168.2.222' failed: server is down.

```

Obviously the server is not "down", as you can see in this ps -A | grep nfs output:

```

 2781 ?        00:00:00 nfsd
 2782 ?        00:00:00 nfsd
 2783 ?        00:00:00 nfsd
 2784 ?        00:00:00 nfsd
 2785 ?        00:00:00 nfsd
 2786 ?        00:00:00 nfsd
 2787 ?        00:00:00 nfsd
 2788 ?        00:00:00 nfsd

```

Let's see if somebody can help me a little :P

Here goes my exports file in the server:

```

/mnt/disc200/compartida 192.168.2.1/24(rw,no_root_squash,async)
/mnt/disc200/autocad 192.168.2.1/24(rw,no_root_squash,async)
/mnt/disc200/batxillerat 192.168.2.1/24(rw,no_root_squash,async)
/mnt/disc200/ESO 192.168.2.1/24(rw,no_root_squash,async)
/mnt/disc200/fotografia 192.168.2.1/24(rw,no_root_squash,async)
/mnt/disc200/primaria 192.168.2.1/24(rw,no_root_squash,async)
/mnt/Server/Documents 192.168.2.1/24(rw,no_root_squash,async)

```

And here goes the line in the fstab file of the client machine:

```

192.168.2.222:/mnt/disc200/compartida   /media/compartida/      nfs     rsize=8192,wsize=8192,timeo=14,intr

```

Thanks in advance!

---

### Post by dannyboy79 on 2007-05-02
> **']Nbx*cmD[ said:**
> Hi all,

I followed this howto and didn't get it working, for some reason I really can't understand.

This is the message i get when trying to mount:

```

mount to NFS server '192.168.2.222' failed: server is down.

```

Obviously the server is not "down", as you can see in this ps -A | grep nfs output:

```

 2781 ?        00:00:00 nfsd
 2782 ?        00:00:00 nfsd
 2783 ?        00:00:00 nfsd
 2784 ?        00:00:00 nfsd
 2785 ?        00:00:00 nfsd
 2786 ?        00:00:00 nfsd
 2787 ?        00:00:00 nfsd
 2788 ?        00:00:00 nfsd

```

Let's see if somebody can help me a little :P

Here goes my exports file in the server:

```

/mnt/disc200/compartida 192.168.2.1/24(rw,no_root_squash,async)
/mnt/disc200/autocad 192.168.2.1/24(rw,no_root_squash,async)
/mnt/disc200/batxillerat 192.168.2.1/24(rw,no_root_squash,async)
/mnt/disc200/ESO 192.168.2.1/24(rw,no_root_squash,async)
/mnt/disc200/fotografia 192.168.2.1/24(rw,no_root_squash,async)
/mnt/disc200/primaria 192.168.2.1/24(rw,no_root_squash,async)
/mnt/Server/Documents 192.168.2.1/24(rw,no_root_squash,async)

```

And here goes the line in the fstab file of the client machine:

```

192.168.2.222:/mnt/disc200/compartida   /media/compartida/      nfs     rsize=8192,wsize=8192,timeo=14,intr

```

Thanks in advance!

on the client, do you have a mount point called /mnt/disc200/compartida? if not, there is your problem. and from the looks of your fstab, that's what's wrong. also, did you make sure you did 

sudo exportfs -a

from the server cause it appears as though the server is not working. did you do 

sudo apt-get install nfs-kernel-server nfs-common portmap

not to mention you have a trailing slash (/) on the end of your client's mount point (/media/compartida/  versus /media/compartida ) 

I would just suggest following the guide verbatim and then post back.

---

### Post by ]Nbx*cmD[ on 2007-05-02
I guess you mean if i have a mount point called /media/compartida, since the /mnt/disc200/compartida directory is on the server, that's why i added "/mnt/disc200/compartida 192.168.2.1/24(rw,no_root_squash,async)" to the exports file. Well, of course i do have that dir and that mount point on the server and the client respectively.

I did "exportfs -a" and it worked, and as you can see from the ps output, the server is running... so, if your solutions are exhaustive, it could only be the slash (and i hope so!) but, sincerely, most of the times "/foo/bar/" and "/foo/bar" are exactly the same... so it'd seem strange to me :) also, the error message says "server is down", while if it was an error from the client i guess it would say something like "mount point not found".

Anyway, now i'm at home, but tomorrow i'll try it at work and give you feedback, thanks a lot!

---

### Post by ]Nbx*cmD[ on 2007-05-03
So as I suspected, the slash has absolutely nothing to do with the problem.

Actually some of the other lines of fstab mounting some partitions finish with a slash as well and work perfectly.

Does somebody have a clue about it? thanks!

---

### Post by dannyboy79 on 2007-05-03
as I stated, it appears as though your mount points are not matching up. according to the instructions, your mount point and the mount point your exporting need to be the same and your's are not. (mnt blah blah versus media blah blah) you wouldn't think that that would be it but it's worth a try right?

Also, here are some common Gotcha's for running NFS.

Ownership represented by numeric UID/GID values, which correspond to logins viathe /etc/passwd file on both client and server!(What if UIDs don't match?)

Security is a problem (e.g., can chown be used to give files away?).See Unix System Security Checklist for details.

NFS is a "stateless" protocol. What happens if the server goes down?

"NFS: stale file handle" error message means re-mount file systems

"Hard mount" is "Energizer Bunny" mode. Client keeps trying, and trying, and trying.... Unless interrupts allowed, client will "hang" until server comes back up

"Soft mount" means client gets an error message.

File locking can be a problem.

Easy to "waste" bandwidth by transferring files twice!(e.g., ftp to/from an NFS mounted file system on a client)

Forgetting to use -xdev (or -mount, etc)., when using find.

Differences in maximum block sizes between client/server file systems can cause programs to crash

---

### Post by ]Nbx*cmD[ on 2007-05-03
Tried it, not working either :(

I needed to have the system working for today so i did it using smbfs, thanks anyway!

---

### Post by dannyboy79 on 2007-05-03
> **']Nbx*cmD[ said:**
> Tried it, not working either :(

I needed to have the system working for today so i did it using smbfs, thanks anyway!

I can tell ya right now that cifs works better than smbfs in my own experience. it's to bad that you couldnt' troubleshoot longer and figure out what's wrong because the guide does work so if you're using feisty it's possible that something happened to NFS in Feisty

---

### Post by ]Nbx*cmD[ on 2007-05-04
yeah, you know... companies put pressure :)

I'll keep investigating though, the thing is that the server is not running ubuntu but debian, so maybe the guide doesn't exactly fit it... when i have time and the server is not to be used for a while i'll try installing feisty server.

---

### Post by dannyboy79 on 2007-05-04
according to a more general NFS server guide, you should run this

rpcinfo -p

to see if the server is running the correct services. you should see something like this returned.
program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100011    1   udp    749  rquotad
    100011    2   udp    749  rquotad
    100005    1   udp    759  mountd
    100005    1   tcp    761  mountd
    100005    2   udp    764  mountd
    100005    2   tcp    766  mountd
    100005    3   udp    769  mountd
    100005    3   tcp    771  mountd
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    300019    1   tcp    830  amd
    300019    1   udp    831  amd
    100024    1   udp    944  status
    100024    1   tcp    946  status
    100021    1   udp   1042  nlockmgr
    100021    3   udp   1042  nlockmgr
    100021    4   udp   1042  nlockmgr
    100021    1   tcp   1629  nlockmgr
    100021    3   tcp   1629  nlockmgr
    100021    4   tcp   1629  nlockmgr

this is all according to this guide:  [http://tldp.org/HOWTO/NFS-HOWTO/server.html#VERIFY](http://tldp.org/HOWTO/NFS-HOWTO/server.html#VERIFY)

good luck

---

### Post by williammanda on 2007-05-04
I have used this setup before and it worked great with my 100 meg router. I have since changed over to a 1gig router and three out of my four computers have 1 gig ethernet ports. I'm having trouble with the files stalling during copy & pasting. The transfer with work for 2 - 3 seconds and stalls for 10 - 15 seconds. This cycle continues until it is finished. Tis scenario happens between any computer ie 1 gig to 1 gig or 1 gig to 100 meg. Is there anything that needs to be setup differently since I changed routers or something else?
Thanks

---

### Post by williammanda on 2007-05-07
I have changed over to Feisty since the last post. I ran a test with a 7 GB file and it transfered at a rate of 1 GB per minute. I'm not sure if this is good or bad but I didn't see the stalling as I did using KDE. Please advise.
Thanks

---

### Post by williammanda on 2007-05-11
Bump...bump!

---

### Post by dannyboy79 on 2007-05-11
> **williammanda said:**
> Bump...bump!

what would you like to know? i read your post as a comment and not a question.

The fact that your 7gigabBYTES file transferred in 7 minutes sounds low when you look at the raw numbers!

 It's due to the PCI bus limitation and packet overhead. A 32bit wide PCI bus running at 33 Mhz, would give it a theoretical speed of about 130 MB/s. Now you would have to split that between the Ethernet Card and the Hard drive since you are transferring data, that would result in about 65MB/s or 3900MB/minute. You're saying your transfer went at 1gigaBYTE/s or 1024MB/minute (that's about 17MB/sec). That's double what I get thru Samba!

It's often troubleshooting network transfer speeds as there are so many variables. I have never used NFS but I do know it's way faster than Samba as I can only get around 8MB/s with samba. 

So why did you bump your post? If you're wondering if your transfer speed is alright I would say YEAP, you are transferring files pretty fast. You'll never see 128MB/second

---

### Post by williammanda on 2007-05-11
Yes I was looking for an answer as to if the transfer rate was good or bad.
Thanks

---

### Post by chrisod on 2007-05-18
I'm posting this to save somebody the 90 minutes of cursing I just went through trying to figure this out. When mounting a SimpleShare drive with NFS, you have to ID the drive differently than you do for Samba.

For Samba, mounting my Photos Folder looked like this (from my fstab file):

```
//mediaserver/Photos  /mnt/photos  smbfs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0
```

However, to mount the same folder in NFS, it has to look like this.

```
mediaserver:/shares/SimplePool/Photos/  /mnt/photos  nfs rsize=8192,wsize=8192,timeo=14,intr
```

This assumes you have not screwed with the default disk pool set up. I have no idea why it needs that the fully qualified path, but it does. Not using it will get you permission denied errors.

---

### Post by dannyboy79 on 2007-05-21
> **chrisod said:**
> I'm posting this to save somebody the 90 minutes of cursing I just went through trying to figure this out. When mounting a SimpleShare drive with NFS, you have to ID the drive differently than you do for Samba.

For Samba, mounting my Photos Folder looked like this (from my fstab file):

```
//mediaserver/Photos  /mnt/photos  smbfs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0
```

However, to mount the same folder in NFS, it has to look like this.

```
mediaserver:/shares/SimplePool/Photos/  /mnt/photos  nfs rsize=8192,wsize=8192,timeo=14,intr
```

This assumes you have not screwed with the default disk pool set up. I have no idea why it needs that the fully qualified path, but it does. Not using it will get you permission denied errors.


You could have saved yourself the 90 minutes and your bllod pressure level if you had read the guide more closely as it already stated that. From the very first page, if you want to add the mount to your fstab, the syntax should be: **server.mydomain.com:/files /files nfs rsize=8192,wsize=8192,timeo=14,intr**
Which if I am not mistaken, is exaclty what you are telling us again. I guess thanks anyway for the other readers who don't follow the guide precisely.

---

### Post by xris_xcess on 2007-06-05
Hi:

I´m new and I now the last post here was a while ago, but I still wanted to follow a thread.


   I´ve found this thread very helpfull... but i´m still stuck on something. I set up a freeNas box so I could share a common folder with several computers. After having great trouble ironing out permissions problems, I finally got full ownership and rw permissions.

   However, until now, I can only manually mount the share. Although I have a "auto" option in my fstab, nothing happens until i issue the "mount /local/share/name" comand. ¿Is this supposed to be like this? ¿I though that putting mounting points in fstab (with the correct options: "auto"?) made the whole process automatic?
I tried to fiddle with autofs but was not sucessfull. I´m not too concerned about server/client load just yet. If it was not for this detail, I would be great. I´m going to set up a login script and see how it goes, but I would really like my fstab to work. ](*,)

   Also, I have my mount point on the desktop. When I mount the share, another folder appears there with the same name and a "connected tube" personalized icon (with an "nfs" tag on it). Both folders work, in fact they point to the same place. I don´t get it? If I have to create a folder in the first place, why does it then go an make another one? Or is it because most of the time (generally) you mount under the /mnt directory, and nfs-common tools are being helpfull and putting an icon on the desktop?

My fstab setup looks like:

> freenas:/mnt/sharename   /home/Desktop/sharename   nfs rw,auto,user,rsize=8192,wsize=8192,intr,soft,retry=5,timeout=20,port=2049


Thanks a lot for any help!!!

EDIT: I rather answered my own question and my mounts work properly. I rewrote fstab to:

  freenas:/mnt/sharename   /mnt/sharename   nfs rw,auto,user,rsize=8192,wsize=8192,intr

And now it works like I was looking for. The user dosen´t have to dive into /mnt, but the share appears on the desktop ... so, that it.

---

### Post by Lary Grant on 2007-06-07
I did the export and mount read-write (rw) but I can still only read.  If I try to write I get an error that says "read-only filesystem".

---

### Post by dannyboy79 on 2007-06-08
and who is the owner of the folder you mounted your exported NFS share to? also, what are the permissions on that folder? those would be the last 2 things to check

---

### Post by Lary Grant on 2007-06-08
Here are more details... There are 2 computers (say A and B).  Each 1 has a single user on it (but different from each other), i.e. computer A has user A and computer B has user B.  I want to set up a world-writable directory (called "Xfer") under user A's home directory (on computer A) so that user B, working on computer B, can copy documents to computer A for user A to work on.

I created the /home/A/Xfer directory, on computer A, owned by user A, with "777" permission (i.e. world-writable).  I set up a read-write (rw) /etc/exports line on computer A for that directory and a mount point and read-write (rw) /etc/fstab line on computer B to access it.  

On computer B, the mount suceeds and I can read files in /home/A/Xfer, but I can't write or create files there.  If I try (e.g. using the "touch" command), I get a "read-only filesystem" error.

---

### Post by dannyboy79 on 2007-06-08
ok, again, I'll ask the same question, who is the owner of the folder where you are mounting the /home/A/Xfer folder on computer B? Where is the mount point, what does your computer B fstab file look like, and what are the permissions?????

---

### Post by esekyavuz on 2007-06-09
Caveat: Say "nnn" then go "oooo" for about five minutes, then say "b".

I found this guide very helpful and have been able to share folders on my laptop with my desktop computer and vice versa. Thank you.

I'm wondering...

Is it possible to share a folder on an ntfs disk via nfs? Both machines running Kubuntu Feisty? Or must I use samba?

Is it necessary for a folder to be somewhere in /home[/...] in order to share it?

Is it possible to share a symbolic link? I have a folder on my desktop that is actually just a link (in Windows we called them shortcuts) to the ntfs folder. Can I share that?

I have tried these things, but there is so much opportunity for missed slashes and misspellings. Thought I'd ask if these things were even possible before I spent more time on them.

Thanks in advance

---

### Post by Mr. C. on 2007-06-09
Once a file system is mounted, it does not matter what type it is - you can share it with NFS.

You can NFS export any directory; it does not have to be in /home.

It doesn't make sense to share a symbolic link.  A symbolic link is a file that has some special indirection properties.  What are you trying to do here?

MrC

---

### Post by esekyavuz on 2007-06-09
Mr C

Thanks for the quick answer.

Not necessary to share the link. I was using it to try to get around the restriction (which does not exist!) that you can share only in /home[/...]

So I guess it's my spelling. will keep trying

Thanks again

******************
Still banging my head.

I'm trying to share 

/media/sda1/dirname

sda1 is a data disk from Windows days. It's 500GB of  NTFS. A SATA drive, in case that matters.

I have given mode 777 to everything in the path, even though I have shared directories that do not have full 777 permissions.

I have tried to sudo mount -t ntfs and was told "special device not present"

When I try to mount without -t then it just says "permission denied". Using sudo.

I am able to share at will on the main GNU/Linux partition.

I guess I should try mounting as root. Every time I write PART TWO of this I think of something else to do. Sheesh. Well, I'll leave this up. If there is a reason I can't share /media/sda1 I would love to know before my brain goes soft. Ooops. Too late.

TIA

---

### Post by esekyavuz on 2007-06-10
So I kind of chickened out. After another hour or so it occurred to me that there is no reason to keep the disk in NTFS. My goal is to be Free by September.anyway so why spend more time on this?

I copied the files to a directory on another disk,used gparted to delete the ntfs partition and create an ext3 one., copied everything back, and the NFS shares I set up yesterday worked perfectly.

I'm hesitant to say that this is clear evidence that it was something Wiindowish that was the problem. It's possible that what I did reset a lot of stuff. 

In case no one has mentioned it yet, in Kubuntu you can set up NFS shares in a GUI under Settings/Shared Folders. You  specify which directory you want shared, which network you want to share it with ( NFS or Samba), and who gets access. In the case of NFS, this configures /etc/exports for you with (rw) privieges. You still have to 

sudo exportfs -a
 
but after that it's ready to be mounted by the other machine(s).

Thanks again for the help and the great howto.

---

### Post by rko618 on 2007-07-16
> **mike3k said:**
> If you're connection to a Linux NFS server from Mac OS X, you need to specify 'insecure' in your exports and map the user IDs since Macs use uid 501 for the first regular user. For my /etc/exports I use:

/home   192.168.0.0/255.255.255.0(rw,async,insecure,all_squash,anonuid=1000,anongid=1000)

Thanks!  I was having a fit trying to get this to work with my mac.  I used your exact options and it worked finally. :)

---

### Post by stryker719 on 2007-07-18
I am trying to allow my Yellow Dog Linux distro installed on my PS3 to mount my files on my Ubuntu PC.  I followed the instructions, but am getting this error on my client machine (YDL on PS3)...
"failed, reason given by server: Permission denied."

Any thoughts?

---

### Post by jackn on 2007-07-25
The issue raised by jabb and george_apan is resolved in this [post]("http://ubuntuforums.org/newreply.php?do=postreply&t=508862").

---

### Post by dannyboy79 on 2007-07-25
the above link takes you to a blank page? Also, it's much easier to copy and paste for users unless of course it's to much for your copy and paste (clipboard limit?) or unless the page is more than just text.

---

### Post by davidme on 2007-08-01
What happens if I have a dynamic ip address ?

Say I have 2 laptops, I want one to share files to another via NFS.

Problem is that I have dynamic ip for both of them since they connect through a router.

So, if I write this:

/home/czar/tmp 192.168.1.1/24(rw,no_root_squash,async)

next time I will start my host laptop the ip for the host can be different, meaning I have to change it on the client.

Is there any other way to connect maybe via laptop name or MAC address or something ?

---

### Post by dannyboy79 on 2007-08-01
> **davidme said:**
> What happens if I have a dynamic ip address ?

Say I have 2 laptops, I want one to share files to another via NFS.

Problem is that I have dynamic ip for both of them since they connect through a router.

So, if I write this:

/home/czar/tmp 192.168.1.1/24(rw,no_root_squash,async)

next time I will start my host laptop the ip for the host can be different, meaning I have to change it on the client.

Is there any other way to connect maybe via laptop name or MAC address or something ?

you didn't read it correctly, what this line on the NFS server does is allow ANY ip address within that range (192.168.1.1 thru 192.168.1.255) to connect to the server.

The client is where you'll want to call out the system name of the machine or hostname by either manually mounting it or putting it in your fstab.

---

### Post by davidme on 2007-08-01
"The client is where you'll want to call out the system name of the machine or hostname by either manually mounting it or putting it in your fstab."

Where do I on the Host machine edit my l name of the machine ? I only found in manual configuration that I can define host name. 

I set my host name to be: laptopishe

Now, on the client side. this command

sudo mount laptopishe:/home/user/media /media/user2/shares

tells me that "can't get address for laptopishe"

What is the problem ?

---

### Post by Mr. C. on 2007-08-01
Either use static IP addresses (which is a function of how you configured your systems, not of your router), or export your file systems to your entire subnet.

The address range you are using makes no sense (192.168.1.1/24).  192.168.1.1 is a HOST address, yet /24 is a subnet specifier.  You'd want either 192.168.1.1 (for a single host) or 192.168.1.0/24 (for tghe entire subnet).

If you are going to use dynamic IP addresses, then hostnames will not be an option unless you change the pair in /etc/hosts, or configure a dynamic updating DNS server (which sounds beyond what you're likely to do right now).

The NFS client and server software, and Unix / Linux server software in general, was developed with static IPs in mind - server's should not be changing IPs.

MrC

---

### Post by dannyboy79 on 2007-08-02
> **Mr. C. said:**
> Either use static IP addresses (which is a function of how you configured your systems, not of your router), or export your file systems to your entire subnet.

The address range you are using makes no sense (192.168.1.1/24).  192.168.1.1 is a HOST address, yet /24 is a subnet specifier.  You'd want either 192.168.1.1 (for a single host) or 192.168.1.0/24 (for tghe entire subnet).

If you are going to use dynamic IP addresses, then hostnames will not be an option unless you change the pair in /etc/hosts, or configure a dynamic updating DNS server (which sounds beyond what you're likely to do right now).

The NFS client and server software, and Unix / Linux server software in general, was developed with static IPs in mind - server's should not be changing IPs.

MrC

He is doing everything correctly. If you're going to try to help please be aware of what you're saying.
192.168.1.1/24 means the IP address of 192.168.1.1 with a CIDR of /24, or class 1 C network, and netmask of 255.255.255.000. This effective means a range from 192.168.1.0 to 192.168.1.255, 256 hosts.
(NOTE: I copied and pasted the above info, credit goes to the author of post #28 within this thread)

NOt only is he following the guide bit for bit, but it's correct even if the guide didn't say to do it that way.

As far as hostname resolution, it sounds like you don't have it setup properly. I haev written up a little explaination on hostname resolution options within a linux/windows mixed environment. ([http://ubuntuforums.org/showthread.php?t=391601](http://ubuntuforums.org/showthread.php?t=391601))  If you don't want to read it, then I would just suggest you setup a static ip on the server and just use that instead of the hostname.

---

### Post by Mr. C. on 2007-08-02
Danny, your combative, threatening, and policing responses get tiresome.  Please stop.

While the address specified *may* work in some implementations or situations, it is technically incorrect, and *will* fail with some software (such as bind).  The specification being used is confusing at best, because it violates common practice and shows a misunderstanding of CIDR.

The correct and commonly practiced mechanism to show a range if IP addresses is to specify the network IP along with the host part of all zeros, as in 192.168.1.0/24.  This is unambiguous, clear to all, and doesn't rely on how the software might parse net and host parts. The specification 192.168.1.1/24 is confusing at best, as it is not clear that the author meant a single IP address, or a range from 1 to 255, or 0 to 255.  It becomes even more confusing with non 8-bit aligned networks.  You may examine all examples in the Wikipedia link references in post #28, and more importantly, in RFC 4632:

[http://tools.ietf.org/html/rfc4632](http://tools.ietf.org/html/rfc4632)

I teach the background, theory, and principles; i have no interest in matching up with some (possible naive, or incorrect) user's guide or posts.  The response in #28 is not authoritative.

MrC

---

### Post by dannyboy79 on 2007-08-02
> **Mr. C. said:**
> Danny, your combative, threatening, and policing responses get tiresome.  Please stop.

While the address specified *may* work in some implementations or situations, it is technically incorrect, and *will* fail with some software (such as bind).  The specification being used is confusing at best, because it violates common practice and shows a misunderstanding of CIDR.

The correct and commonly practiced mechanism to show a range if IP addresses is to specify the network IP along with the host part of all zeros, as in 192.168.1.0/24.  This is unambiguous, clear to all, and doesn't rely on how the software might parse net and host parts. The specification 192.168.1.1/24 is confusing at best, as it is not clear that the author meant a single IP address, or a range from 1 to 255, or 0 to 255.  It becomes even more confusing with non 8-bit aligned networks.  You may examine all examples in the Wikipedia link references in post #28, and more importantly, in RFC 4632:

[http://tools.ietf.org/html/rfc4632](http://tools.ietf.org/html/rfc4632)

I teach the background, theory, and principles; i have no interest in matching up with some (possible naive, or incorrect) user's guide or posts.  The response in #28 is not authoritative.

MrC

I am sorry you feel this way.

---

### Post by LuisC-SM on 2007-08-20
To the original author.

Thanks a lot!

I can reconfirm (others have already done so) that this works for UFF just as stated.

Regards

Luis

---

### Post by jlagermann on 2007-08-21
I still need help.  When I try to mount from the client I get this error:
mount to NFS server '192.168.10.200' failed: server is down.

I have all of the parts and pieces configured exactly as stated on the orginal post, on the client and server, but I still cannot connect.:(

I am setting up a VMWare image just for FTP but I don't want a 200G VMware image.   All of the data for the FTP server is on the host machine with the NFS share and the client is in a VM.

---

### Post by LuisC-SM on 2007-08-21
Hi. 

See if /etc/network/interfaces is setup correctly, ...in my own case, this would be my configuration
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.50
        netmask 255.255.255.0
        network 192.168.1.1
        broadcast 192.168.1.255
        gateway 192.168.1.254
```
Sorry if this is not the correct answer but I've not seen previous posts..
Kind Regards
Luis

---

### Post by jlagermann on 2007-08-21
My /etc/network/interfaces is setup very similar.  The network works fine, Internet, ICMP etc..  

I am currently doing a tcpdump on the client.  The client is tring to communicate with the server by IP on the sunrpc port and then it changes to port 48482.  The server never replies.  Every couple seconds the server does a reverse-arp for the client by name with no answer.

---

### Post by LuisC-SM on 2007-08-21
> **jlagermann said:**
> My /etc/network/interfaces is setup very similar.  The network works fine, Internet, ICMP etc..  

I am currently doing a tcpdump on the client.  The client is tring to communicate with the server by IP on the sunrpc port and then it changes to port 48482.  The server never replies.  Every couple seconds the server does a reverse-arp for the client by name with no answer.
Probabily I can help u as long as I had the same problem once..

Can you try to comunicate via SSH? (on port 22)?

If so, then dome a favor ... just post your /etc/network/interfaces and your /etc/hosts files here.... just to have an idea.

Luis.

---

### Post by R_U_Q_R_U on 2007-08-29
AVOID FRUSTRATION! MAKE SURE YOU CHECK YOUR FIREWALL!

I could not get my Ubuntu laptop client to connect to the NFS server. I kept getting "failed: server is down".

I rechecked everything in my exports folder and my mount command. All looked OK. After two days of swearing and begging, I thought "FIREWALL"

I fired up the GUI Firestarter on the server and noted that I had setup INBOUND rules. I added the IP of the client and BINGO it worked.

BTW what is the syntax for allowing all IPs on my network to the inbound rule?

---

### Post by dmizer on 2007-08-30
> **Mr. C. said:**
> [snip]
While the address specified *may* work in some implementations or situations, it is technically incorrect, and *will* fail with some software (such as bind).
[snip]
MrC
thank you MrC.  that fixed my bind hangup.  i've successfully readded name resolution to my local network.  had no idea what was causing that.

---

### Post by Euan17 on 2007-08-30
hey, im new to linux and i'm trying to setup NFS server but i cant find the /etc/exports file in my installation and i have no internet connection on the machine. is there somewhere i can download the files i need on this machine copy them to usb and then install them on the linux machine?

---

### Post by ShopliftCS on 2007-08-30
Having issues with Ubuntu NFS & VMWare so I'll post the setup and let the guru's check it out.

I have 3 HP dc7700 workstations for my testing.  1 with Ubuntu Feisty (7.0.4) and 2 with VMWare ESX 3.0

NFS Setup:
Ubuntu 7.04 (feisty), I am remote controlling via tightvnc
IP: 192.168.14.235
Subnet Mask: 255.255.254.0
Shared folder /svr

Here's a copy of my terminal:

```
alloy@asc-nfs:/etc$ sudo apt-get install nfs-kernel-server nfs-common portmap Reading package lists... Done
Building dependency tree       
Reading state information... Done
nfs-kernel-server is already the newest version.
nfs-common is already the newest version.
portmap is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
alloy@asc-nfs:/etc$ sudo dpkg-reconfigure portmap
 * Stopping portmap daemon...                                                                                            [ OK ] 
 * Starting portmap daemon...                                                                                            [ OK ] 
 * Restoring old RPC service information...                                                                              [ OK ] 
There are RPC services which registered with the portmapper before the configuration was changed.
You need to manually restart them in order for the changes to take effect.
Current registered services:
------------------------------------------------
    100024    1   udp  32771  status
    100024    1   tcp  60132  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  32796  nlockmgr
    100021    3   udp  32796  nlockmgr
    100021    4   udp  32796  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  59301  nlockmgr
    100021    3   tcp  59301  nlockmgr
    100021    4   tcp  59301  nlockmgr
    100005    1   udp   1000  mountd
    100005    1   tcp   1003  mountd
    100005    2   udp   1000  mountd
    100005    2   tcp   1003  mountd
    100005    3   udp   1000  mountd
    100005    3   tcp   1003  mountd
------------------------------------------------
alloy@asc-nfs:/etc$ sudo /etc/init.d/portmap restart
 * Stopping portmap daemon...                                                                                            [ OK ] 
 * Starting portmap daemon...                                                                                            [ OK ] 
alloy@asc-nfs:/etc$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                                                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                                                                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                                                                        [ OK ] 
 * Starting NFS kernel daemon                                                                                            [ OK ] 
alloy@asc-nfs:/etc$ sudo exportfs -a
```

So, it would seem that NFS is set up.  Now, I move over to my VMWare test box.

I log in with the VI Client to the machine @ 192.168.14.236
Here's an image of my net settings:
[IMG]http://www.4cpp.com/images/vmware_nic.jpg[/IMG]

So, I go to storage -> Add Storage and I select Network File System
Like so:
[IMG]http://www.4cpp.com/images/vmware_storage.jpg[/IMG]
[IMG]http://www.4cpp.com/images/vmware_storage2.jpg[/IMG]
I see the message like this:
[IMG]http://www.4cpp.com/images/vmware_storage32.jpg[/IMG]

And then error!
[IMG]http://www.4cpp.com/images/vmware_storage_err.jpg[/IMG]

Any idears?

Thanks,

~Shop

--ALSO--
My exports has 1 entry

/svr 192.168.14.233(rw,no_root_squash,async,subtree_check) 192.168.14.234(rw,no_root_squash,async,subtree_check) 192.168.14.235(rw,no_root_squash,async,subtree_check) 192.168.14.236(rw,no_root_squash,async,subtree_check) 192.168.14.237(rw,no_root_squash,async,subtree_check)

---

### Post by ShopliftCS on 2007-08-31
> **Euan17 said:**
> hey, im new to linux and i'm trying to setup NFS server but i cant find the /etc/exports file in my installation and i have no internet connection on the machine. is there somewhere i can download the files i need on this machine copy them to usb and then install them on the linux machine?

Evan--

Log in as root, or on Ubuntu try this in a console terminal:

*nix
vi /etc/exports

Ubuntu
sudo gedit /etc/exports
<type your password>

This file should have no entries by default, you must create your own.

~Shop

---

### Post by LuisC-SM on 2007-09-01
> **ShopliftCS said:**
> Evan--

Log in as root, or on Ubuntu try this in a console terminal:

*nix
vi /etc/exports

Ubuntu
sudo gedit /etc/exports
<type your password>

This file should have no entries by default, you must create your own.


~Shop

I'm not exactly sure, but I think this file is created by "portmap or by nfs-kernel" (I could be wrong) and the next thing you must do once you create the file is to to insert a line like this:
> /home/your_user_name/Your_exported_file XXX.XXX.XXX.XXX/24(rw,no_root_squash,async)
So in order to give you an idea my file looks like this:> /home/luis/Musica 192.168.1.1/24(rw,no_root_squash,async)
As you can see, 192.168.1.1/24 is granting read and write access to everybody in my Music network folder.
I hope this will help u.

Regards

Luis

@Shop

Your problem above looks like it is realted to Router access (not sure but I see no otheroption)

---

### Post by LuisC-SM on 2007-09-01
> **Euan17 said:**
> hey, im new to linux and i'm trying to setup NFS server but i cant find the /etc/exports file in my installation and i have no internet connection on the machine. is there somewhere i can download the files i need on this machine copy them to usb and then install them on the linux machine?

I have one question...
Did you install Ubuntu Server CD? and followed the steps in the first post?

Regards

Luis

---

### Post by a_posse_ad_esse on 2007-09-04
I'm getting a "permission denied" error, and find by reading /var/log/syslog that 
```

Sep  4 00:48:47 server mountd[6466]: mount request from unknown host 192.168.2.7 for /public (/public)

```

My hosts.allow:
```

rpc.mountd portmap mountd nfsd statd lockd rquotad : 192.168.2.*

```

and exports
```

/public 192.168.2.*(rw,no_root_squash,async,subtree_check)

```

Any ideas about how I can fix this?

---

### Post by bodhi.zazen on 2007-09-04
I do not think you can use * as a wild card here.

Try 192.168.2.0/255.255.255.0 or 192.168.2.1/24

So in hosts.allow

ALL: 192.168.2.0/255.255.255.0

And in exports

/public 192.168.2.1/24

---

### Post by a_posse_ad_esse on 2007-09-04
That worked, thanks.

I figured that both methods did essentially the same thing...  Strange that the wildcard method doesn't work.

---

### Post by LuisC-SM on 2007-09-05
I've seen that sometimes people gets confused when mounting or auto-mounting  (in "**/etc/fstab**") with this statement: 
```
    server.mydomain.com:/files /files nfs rsize=8192,wsize=8192,timeo=14,intr

```
In my case and with **[COLOR="DarkRed"]my own[/COLOR]** configuration (posted earlier) this also works:
```
    192.168.1.50:/files /files nfs rsize=8192,wsize=8192,timeo=14,intr

```(My Static IP Address)
I hope this can help someone who is having troubles mounting NFS.

Cheers

Luis

---

### Post by CyberCod on 2007-09-09
I successfully used your guide to mount shares, and managed to infer the necessary permissions situation from the original post (go me!) but now that its up, its so damn slow I can not believe it.

It has taken nearly an hour to transfer a 700MB file, and it is still not complete... in fact its stuck at (0:00 Remaining) even though the filesizes in both the original file and the copied file are the same... all the while, the bandwidth monitor is still going full speed.

What gives?

The setup is:

serving PC on 802.11b wifi pci card

client PC on 10/100 onboard ethernet 

transferring from client into the shared folder of the server.


I realize there's a bottleneck somewhere, but this is ridiculous... Samba is faster than this for me, so I must have something not right.  It the bottleneck were hardware related, samba would be this slow as well.

Yet it IS working, if thats what you call it...

Is there any way to tell what the transfer speed is?

Also, the share doesnt show back up on the client after rebooting, even though its properly set in fstab.

---

### Post by CyberCod on 2007-09-09
Well, the file transfer never really finished.  I ended up having to kill it after it was apparent that the transfer was as complete as it would get.

The transfered file (a video) plays ok, but has seek issues, so apparently something was lost in the transfer, even though they're the same size file.

On the client side (transferrer) the the whole desktop ended up locking up, and the keyboard lights were flashing, denoting kernel panic... thats never good.  I did Alt+SysRq RSEUB to reboot.  At which point the NFS shares still weren't auto-mounted by the fstab.

I customized the automounter script mentioned earlier in this thread, and that works, so as soon as I figure out cron, I'll have that working properly.

I'm looking at ports stuff like that to see if I can figure it out myself, but I'm not seeing many posts of others having this problem.

Oh, and the wireless in question has a link speed of 11Mbps according to the Network Tools app.
On the PC using ethernet, the link speed says "not available" so I'm looking into that.

If you need me to post some info, say the word.  I REALLY want this to work.  4 machines running in the house with Ubuntu, and only one of them is dual boot w/ Win (for Warcraft purposes, and only because ATI suxx... else WoW would be in Wine)  so getting rid of Samba would be really nice.

Thnx


Update:

Just used the following command in terminal to time a file copy
```

time command cp ~/Desktop/Fog2.flv ~/Desktop/SharedFolder

```

it was a 5.6MB file and it took 19.121 seconds.

5.6/19.121 = 0.292871712 MB/s    
times 8 gives 2.342973696
or 
2.34Mbit/s
on an 11Mbit connection.

a 700MB file would take 2390 seconds or 39.8 minutes.

That still seems a bit high to me.

---

### Post by LPGDEV on 2007-09-12
Hi

I have installed the nfs server and it works really well. However, I did something which makes it start at startup and I would like to know exactly where this is so that I can disable it. Can anyone help me out with this?

Thanks

---

### Post by LuisC-SM on 2007-09-12
> **LPGDEV said:**
> Hi

I have installed the nfs server and it works really well. However, I did something which makes it start at startup and I would like to know exactly where this is so that I can disable it. Can anyone help me out with this?

Thanks

Edit your /etc/fstab and delete (remove) the line you had previously added. (Normally the last line).

Cheers

Luis

EDIT: Note that this will disable (unmount) only the CLIENT ... Not the server (sorry if this was not what you were looking for.

---

### Post by bodhi.zazen on 2007-09-12
> **LPGDEV said:**
> Hi

I have installed the nfs server and it works really well. However, I did something which makes it start at startup and I would like to know exactly where this is so that I can disable it. Can anyone help me out with this?

Thanks

Disable portmap and nfs-common. You can do this several ways.

---

### Post by edu_ard on 2007-09-30
I did exactly  what you said and I get this in the client computer which uses SuSE.

linux-suse:/home/user # mount -t nfs 192.168.0.20:/home/user/shared /home/user/nfs
mount server reported tcp not available, falling back to udp
mount: RPC: Remote system error - Connection refused
linux-suse:/home/user #    

What I did wrong?:(

---

### Post by megamania on 2007-09-30
> **edu_ard said:**
> I did exactly  what you said and I get this in the client computer which uses SuSE.

linux-suse:/home/user # mount -t nfs 192.168.0.20:/home/user/shared /home/user/nfs
mount server reported tcp not available, falling back to udp
mount: RPC: Remote system error - Connection refused
linux-suse:/home/user #    

What I did wrong?:(
I'm not sure that's the problem, but I would set a mountpoint in /mnt, not in /home. So:

```
sudo mkdir /mnt/nfs
```
I also do not use "-t nfs" and it works for me:

```
sudo mount 192.168.0.20:/home/user/shared /mnt/nfs
```
I see you use Suse. I don't know if it's like Ubuntu (which uses sudo), but remember you need root privileges for both commands. So either you use sudo, or you have to strip it off my examples and be root.

Hope that helps - I'm not an expert at all and still learning, so let me know how it turns out.

---

### Post by bodhi.zazen on 2007-09-30
> **edu_ard said:**
> I did exactly  what you said and I get this in the client computer which uses SuSE.

linux-suse:/home/user # mount -t nfs 192.168.0.20:/home/user/shared /home/user/nfs
mount server reported tcp not available, falling back to udp
mount: RPC: Remote system error - Connection refused
linux-suse:/home/user #    

What I did wrong?:(

First, the mount point does not matter on the client. You can mount in your home directory if you like.

Second, I have no problems at all with an Ubuntu server and OpenSUSE 10.3

On the suse client :

```
mount -t nfs <server_ip>:/export /mount/point
```

where <server_ip> is my nfs server, :export is the exported nfs share, and /mount/point is either in /mnt , /media, or /home

mounting nfs worked on the suse client out of the box.

So I assume your problem is either with your server, router/network, or firewall.

HTH

---

### Post by jcsewell on 2007-10-02
How does one go about accessing an NTFS partition from another client using nfs? Here is my network:

fs Server
NTFS mounted drive
|
|
|
nfs Client
wants to mount NTFS partition

nfs is working on both machines. I can mount home directories from the server on the client.

When I try to mount the NTFS partition, here's what I get:

mount: jsewell-server:/media/NTFS failed, reason given by server: Permission denied

I checked permissions on the NTFS partition on the server. owner and group are "root". All files and directories have rwx permissions for user, group, and world. So it seems like anybody should be able to access those files.

Why am I getting permission denied?


-James

---

### Post by bodhi.zazen on 2007-10-02
First confirm your server is configured (can you mount a non-ftfs share ?)

Then see if this link helps :

[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

---

### Post by clucas on 2007-10-02
I have read this thread and have become confused. My confusion comes about from what to use for "server.mydomain.com". My situation: I have 2 Linux machines each running Gutsy Gibbon. When I run ifconfig at my "upstairs" machine I get inet addr as 192.168.0.102. When I type cat /etc/hosts is carl-upstairs. When I do the same "downstairs" I get 192.168.0.101 and carl-desktop. My goal is for any machine to have access to the files on the other machine.I have edited the fstab file as well as the /etc/exports file. Obviously the wrong way! Can someone help?

---

### Post by bodhi.zazen on 2007-10-02
> **clucas said:**
> I have read this thread and have become confused. My confusion comes about from what to use for "server.mydomain.com". My situation: I have 2 Linux machines each running Gutsy Gibbon. When I run ifconfig at my "upstairs" machine I get inet addr as 192.168.0.102. When I type cat /etc/hosts is carl-upstairs. When I do the same "downstairs" I get 192.168.0.101 and carl-desktop. My goal is for any machine to have access to the files on the other machine.I have edited the fstab file as well as the /etc/exports file. Obviously the wrong way! Can someone help?

You can either use the ip address

Or you can add the information to /etc/hosts

192.168.0.102 carl-upstairs #add this to your downstairs machine

192.168.0.101 carl-desktop #add this to your updatairs machine

After you add that info to your /etc/hosts you can use carl-upstaris and carl-desktop in place of "server.mydomain.com"

---

### Post by clucas on 2007-10-02
Thanks. I need more help.

This is what I did:

I edited hosts on my downstairs machine to include 192.168.0.102 carl-upstairs.

I edited exports to include /files 192.168.0.1/24(rw,no_root_squash,async).

I then did "sudo mount 192.168.0.102:/files /files" (of course, after creating "files") and got  mount to NFS server '192.168.0.102' failed: RPC Error: Program not registered.

---

### Post by bodhi.zazen on 2007-10-02
you need to restart the nfs server after you update /etc/exports

```
sudo /etc/init.d/nfs-kernel-server restart
```

Then, on the client use the -nfs flag

sudo mount -t nfs 192.168.0.102:/files /files

---

### Post by clucas on 2007-10-02
I REALLY appreciate the help. Now I have to ask a stupid question: Which is the client and which is the server? Sorry I'm showing my ignorance!

---

### Post by bodhi.zazen on 2007-10-02
LOL

No problems

The server is where the nfs-server is running, the place where /files lives, the place where you configured /etc/exports

The client is where you mount /files

where you run

sudo mount -t nfs ip:/files /files

You do NOT need to run a nfs server on both boxes, just one.

---

### Post by clucas on 2007-10-02
Almost there!!

From "upstairs" I have access to "downstairs". But I can't get access to "upstairs" from "downstairs". When I ran the mount command "upstairs" it worked. But when I ran it "downstairs" I get: "mount.nfs: mount to NFS server '192.168.0.102' failed: RPC Error: Program not registered"

---

### Post by bodhi.zazen on 2007-10-02
Well, you only need to mount the share form one server to one client.

ie you do not need to run a nfs server on BOTH and mount a nfs share on BOTH, it would be redundant ...

it would be redundant ...

---

### Post by clucas on 2007-10-02
I see what you mean.... I see what you mean. :)

But I want both machines to be able to access the other machine at both times.

Don't I need to mount the nfs share on both machines? I mean, don't I need to mount the upstairs machine on my downstairs machine and vice versa?

How do I "disable(?)" the server on 1 of the machines? I think what I did was ran the nfs server on both.

Maybe I'm getting tired and should go to bed and work on this some other time.

You HAVE been a great help, though.

---

### Post by bodhi.zazen on 2007-10-02
You are most welcome.

You can always access /files, on either machine, at any time.

Ask yourself, do you need more then this ?

---

### Post by nickpaton on 2007-10-03
I've read every post over the 18 pages (took all afternoon!)
Great Howto on the first page and got everything working fine.

But like a couple of other posters I also wanted to mount onto NTFS drives on the server and haven't been able to, getting the 'Permission Denied' message when trying to mount via the client.

The NTFS drives on the server are SATA  and have been configured to read / write on Ubuntu using the excellent ntfs-3g program - see[ here]("http://ubuntuforums.org/showthread.php?t=217009") for details.
On the server I can fully read / write to the drives within Ubuntu, and have also chowmodded etc etc.

As suggested by one of the other posters I then added an ext3 partition to one of the SATA's and hey presto I can now mount that partition.

So the problem has to be to do with the way the NTFS drive is formatted or configured - a very useful post somewhere within the 18 pages lists a whole lot of Gochas, and the NTFS drives have got to fall into this.

I'm going to persist with this, but in the meantime...

...Any ideas?

---

### Post by peos on 2007-10-04
It's a great effort to make an easy to use HOWTO like this. It's much needed.

There is one piece for mounting NFS that You may want to consider
to mention. It's the automounter, (or autofs). When installed and enabled for NFS (uncommoent the auto.net-line in /etc/auto.master) it
becomes very easy to use NFS.
NFS-shares will be automatically mounted when accessed (if permitted
of course). Only caveat is You need to know and type the name of the
server. I.e. 
% ls /net/nfs-server1
will list the shares from that server that You are allowed to see.
It also works to type the path in nautilus.

Next step is to put users home directories on /net/server/home/user,
but thats another (longer) story.

 Regards
 PeO

---

### Post by dgrafix on 2007-10-23
WOW! This is much better than using Linux -->samba -->Linux

I have used the text file configuration of 'export' and 'smb.conf' for both SMB and NFS so both my ubuntu laptop and windows laptop can access my server shares. However is doing this dangerous in any way?

---

### Post by TheRealMikeD on 2007-11-03
I have skimmed through all 18 pages of posts in this thread, and haven't seen anything about using Windows as a client to access NFS shared files on an Ubuntu box.

I have an Ubuntu 6.06 server and I would like to be able to access its files on my WinXP Pro box.  The XP box is running Windows Services For Unix (WSFU).  I have a similar setup at work, with WinXP and a FreeBSD machine, which works like a champ, but I am having problems getting it to work with Ubuntu.

I can see the shares from the XP box but:

A) My home dir seems to be read-only, when accessed through the share.
B) Write operations from Windows to the NFS shares seem to be slow/unreliable, especially with larger files.

Here is my exports file:
```

/home/ 192.168.0.2(rw,sync,no_root_squash)
/var/www 192.168.0.2(rw,sync)
/tmp/share 192.168.0.2(rw,sync,no_root_squash)

```

Anyone have any experience with this?  Am I better off using Samba for a Windows client?

Thanks!
-Mike D.

---

### Post by dgrafix on 2007-11-03
I think i read somewhere as well as  "client for microsoft networks" you can add  "client for unix networks" but ive no idea where one would get such a thing :-?

---

### Post by Lambert on 2007-11-03
TheRealMikeD:

Look into an app called sfu (windows services for unix).

Here's an older post on it.

[http://ubuntuforums.org/showthread.php?t=310168](http://ubuntuforums.org/showthread.php?t=310168)

---

### Post by Jose Catre-Vandis on 2007-11-03
> **Lambert said:**
> TheRealMikeD:

Look into an app called sfu (windows services for unix).

Here's an older post on it.

[http://ubuntuforums.org/showthread.php?t=310168](http://ubuntuforums.org/showthread.php?t=310168)

Waddaya mean older post? :lol: The main bulk still stands true for XP, though folks have mucho trouble with access permissions for a variety of reasons.

If you have Vista (Ultimate - maybe in lesser versions?), you can enable NFS access through "Features"

---

### Post by LuisC-SM on 2007-11-04
The problem with NFS shares and windows (in my case) has always been the speed. It's so slow that I always end up using SMB.
I don't know if anyone experiences the same with XP ?
Cheers
Luis

EDIT:  **@Jose**.
Very nice howto, too bad I did not see it before, I have only one machine with winXP that I don't use except when I want to do some photoshop things, so I'll try it next week. Thanks a lot mate

---

### Post by ZootNerper on 2007-11-06
Hi Folks,

I followed the Howto and now have a client that can access files on the server, no problems. Both running Gutsy. But how to I get the server to see files on the client? Do I have to set up a separate client server the opposite way round?

Thanks,

-- Zoot

---

### Post by 316097 on 2007-11-18
/etc/exports on my server, a machine running Mythbuntu 7.10
```

/hdd/tv-programs *(rw,no_root_squash,no_subtree_check,async)
/hdd/music *(rw,no_root_squash,no_subtree_check,async)
/hdd/movies *(rw,no_root_squash,no_subtree_check,async)
/hdd/dump *(rw,no_root_squash,no_subtree_check,async)

```/etc/fstab on one of my clients, running Kubuntu 7.10
```

192.168.1.10:/hdd/tv-programs /home/public/tv-programs nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.10:/hdd/music /home/public/music nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.10:/hdd/movies /home/public/movies nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.10:/hdd/dump /home/public/dump nfs rsize=8192,wsize=8192,timeo=14,intr

```These lines did the trick for me when my server was running LinuxMCE/Kubuntu, but now when I switched to Mythbuntu instead it doesn't work as it's supposed to.

For example - the **"tv-programs"** shared on the server gets mounted in all the directories on the client.

Can anyone explain this strange behaviour?

---

### Post by TruckStuff on 2007-11-21
> **mike3k said:**
> If you're connection to a Linux NFS server from Mac OS X, you need to specify 'insecure' in your exports and map the user IDs since Macs use uid 501 for the first regular user. For my /etc/exports I use:

/home   192.168.0.0/255.255.255.0(rw,async,insecure,all_squash,anonuid=1000,anongid=1000) I just setup an NFS server on Ubuntu 7.10 server.  Using these options, I was (eventually) able to mount.  However, I also had an additional problem.  OS X (Leopard) refused to mount, kept saying operation timed out: ```
$ sudo mount server:/mnt/share /Volumes/share
mount_nfs: bad MNT RPC: RPC: Timed out\n
mount_nfs: bad MNT RPC: RPC: Timed out\n
mount_nfs: can't access /mnt/share: Permission denied
``` I finally found the answer here: 

[http://www.linuxquestions.org/questions/debian-26/mountd-time-out-mountnfs-bad-mnt-rpc-rpc-timed-out-on-client-330811/](http://www.linuxquestions.org/questions/debian-26/mountd-time-out-mountnfs-bad-mnt-rpc-rpc-timed-out-on-client-330811/)

By adding the name of the client to /etc/hosts, OS X started up right away.  Don't ask me why NFS is trying to resolve names, but it seems to be.

---

### Post by r!ots on 2007-11-26
today i setup my desktop as a nfs-server and my laptop as a nfs-client. i was able to mount the exported folders, until then everything worked out alright.

but when i started copying files from my desktop pc to the notebook the troubles began. i have a 40 GB music collection on my desktop pc which i want to transfer to my notebook but somehow the speed doesn't stay at a constant level. it starts at around 1.4 MB/s, which would be fine, but after the first 5 or so files are copied it drops to somewhere between 0 and 30 kb/s. thus it will never finish.
does anyone have any idea why this happens?


edit:
If I boot the desktop PC into w2k and access it from the notebook via SAMBA I get a 3 MB/s speed transfering files to the desktop PC and 1-2 MB/s transfering files from it. Why is there a speed difference between up- and downloading? Is it affected by the size of the files I transfer (the one I uploaded was 2 GB and the downloaded ones were mp3-files which were about 3-10 MB)? Why does the speed stay at a more or less high and constant level using SAMBA and doesn't using NFS? I don't get it.

btw: Do you know a good program to synchronize the content of two folders? So I see which files I got on my notebook and which I still need to put on it from the desktop pc and vice versa?

---

### Post by TheWizzard on 2007-12-07
great howto, thanks!

one thing i don't understand is the rsize=8192,wsize=8192,timeo=14 part in the fstab. this doesn't seem to work for me.

just for your information: someone copied the howto to his website without giving you credit. 
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)
[http://whois.domaintools.com/ubuntugeek.com](http://whois.domaintools.com/ubuntugeek.com)

---

### Post by bodhi.zazen on 2007-12-07
> **TheWizzard said:**
> great howto, thanks!

one thing i don't understand is the rsize=8192,wsize=8192,timeo=14 part in the fstab. this doesn't seem to work for me.

just for your information: someone copied the howto to his website without giving you credit. 
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)
[http://whois.domaintools.com/ubuntugeek.com](http://whois.domaintools.com/ubuntugeek.com)

LOL

see man nfs for options :

[http://linux.die.net/man/5/nfs](http://linux.die.net/man/5/nfs)

> rsize=n
    The number of bytes NFS uses when reading files from an NFS server. The rsize is negotiated between the server and client to determine the largest block size that both can support. The value specified by this option is the maximum size that could be used; however, the actual size used may be smaller. Note: Setting this size to a value less than the largest supported block size will adversely affect performance. 


wsize=n
    The number of bytes NFS uses when writing files to an NFS server. The wsize is negotiated between the server and client to determine the largest block size that both can support. The value specified by this option is the maximum size that could be used; however, the actual size used may be smaller. Note: Setting this size to a value less than the largest supported block size will adversely affect performance. 


timeo=n
    The value in tenths of a second before sending the first retransmission after an RPC timeout. The default value is 7 tenths of a second. After the first timeout, the timeout is doubled after each successive timeout until a maximum timeout of 60 seconds is reached or the enough retransmissions have occured to cause a major timeout. Then, if the filesystem is hard mounted, each new timeout cascade restarts at twice the initial value of the previous cascade, again doubling at each retransmission. The maximum timeout is always 60 seconds. Better overall performance may be achieved by increasing the timeout when mounting on a busy network, to a slow server, or through several routers or gateways.

And on ....

Or this :

[http://www.debianadmin.com/network-file-system-nfs-server-and-client-configuration-in-debian.htmlprint/](http://www.debianadmin.com/network-file-system-nfs-server-and-client-configuration-in-debian.htmlprint/)

> **NFS Performance Tuning**

NFS does not need a fast processor or a lot of memory. I/O is the bottleneck, so fast disks and a fast network help. If you use IDE disks, use hdparam to tune them for optimal transfer rates. If you support multiple, simultaneous users, consider paying for SCSI disks; SCSI can schedule multiple, interleaved requests much more intelligently than IDE can.

On the software side, by far the most effective step you can take is to optimize the NFS block size. NFS transfers data in chunks. If the chunks are too small, your computers spend more time processing chunk headers than moving bits. If the chunks are too large, your computers move more bits than they need to for a given set of data. To optimize the NFS block size, measure the transfer time for various block size values. Here is a measurement of the transfer time for a 256 MB file full of zeros.

# mount files.first.com:/home /mnt -o rw,wsize=1024
# time dd if=/dev/zero of=/mnt/test bs=16k count=16k
16384+0 records in
16384+0 records out

real 0m32.207s
user 0m0.000s
sys 0m0.990s

# umount /mnt

This corresponds to a throughput of 63 Mb/s.
Try writing with block sizes of 1024, 2048, 4096, and 8192 bytes (if you use NFS v3, you can try 16384 and 32768, too) and measuring the time required for each. In order to get an idea of the uncertainly in your measurements, repeat each measurement several times. In order to defeat caching, be sure to unmount and remount between measurements.

# mount files.first.com:/home /mnt -o ro,rsize=1024
# time dd if=/mnt/test of=/dev/null bs=16k
16384+0 records in
16384+0 records out

real 0m26.772s
user 0m0.010s
sys 0m0.530s

# umount /mnt

Your optimal block sizes for both reading and writing will almost certainly exceed 1024 bytes. It may occur that, like mine, your data do not indicate a clear optimum, but instead seem to approach an asymptote as block size is increased. In this case, you should pick the lowest block size which gets you close to the asymptote, rather than the highest available block size; anecdotal evidence indicates that too large block sizes can cause problems.

Once you have decided on an rsize and wsize, be sure to write them into your clients’ /etc/fstab. You might also consider specifying the noatime option.

:twisted:

---

### Post by nwadams on 2007-12-12
so i can mount certain files but not others
my /etc/exports file has the line
/media/320      192.168.0.117(rw) 

and then i go: sudo exportfs -a and i get
nwadams@nwadams-desktop:~$ sudo exportfs -a
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.0.117:/media/320".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x
exportfs: Warning: /media/320 does not support NFS export.


now i can mount my home partition, but i can't mount this one, would it have something to do with how it says it is owned by root?

Thanks

---

### Post by TheWizzard on 2007-12-13
what are you trying to do? share a media device on your network?

the /media folder is a bit special. try to mount the media device on /mnt/320
(you'll need to create the mountpoint).

---

### Post by nwadams on 2007-12-13
i think i figured it out, i can't mount an ntfs drive with nfs can I...that was the problem, stupid me...umm how would I share an ntfs drive to another computer with ubuntu...thanks

---

### Post by bodhi.zazen on 2007-12-13
You may be able to do it with samba

---

### Post by jrickard on 2007-12-17
Very nice Howto: on NFS

There seems to be a lot of questions about mounting automatically.   The problem arises when you are taking servers and clients up and down and a number of users seem to want it to act like windows or SAMBA and just "be there".  Some of the heavy scripting solutions seem to me a little odd. 

AUTOFS has been around for nearly a decade.  Basically, it mounts a network resource when you access it.  And only then.  After a minute or so of activity, (configurable) it lets it go.  It starts automatically on bootup.

I have a little miniPC setup to run GPHOTO2 to operate a Canon camera in remote capture mode.  It captures an image from the camera and does some processing on it to annotate it with today's date, crop it, resize it to 1920x1080, normalize it, and so forth.  Then it pokes the image into my web server ([http://www.oldcapebridge.com](http://www.oldcapebridge.com)).  In this way, I get high resolution camera images on the web site.

If I take down the web server, I don't want to have to go to the camera location and remount the NFS so the camserver can find the directory on the web server.  AUTOFS works fine for this.  If the web server is down, the camserver keeps taking images, but is unable to post them.  When the web server comes back up, it can.

autofs does not come with the Gutsy distribution.

```
sudo apt-get install autofs
```

This will install autofs and set it up to come up automatically each time you boot 
your system.

To configure it, you have to create a mountpoint in your file system, and configure two files in /etc/.  They are not hard, but not evident either.

```
sudo mkdir /mnt
```

This simply creates a directory titled /mnt on your root filesystem.  This is where you will find the NFS shares.

Let's edit /etc/auto.master with an editor.

```
sudo gedit /etc/auto.master
```

```

#
# $Id: auto.master,v 1.4 2005/01/04 14:36:54 raven Exp $
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#/misc	/etc/auto.misc --timeout=60
#/smb	/etc/auto.smb
#/misc	/etc/auto.misc
#/net	/etc/auto.net
/mnt  /etc/auto.ubuntumini --timeou=300 --ghost

```

All the lines in the file are normally commented out.  I have added a single line to the bottom.

/mnt is the mountpoint.  It relates to the directory we just created.  This is where autofs mounts everything.

/etc/auto.ubuntumini is where we keep another file listing our NFS mounts.  It can be any file name in any directory actually.  But the default is /etc/auto.misc which I leave for later examination.  We're going to create this /etc/auto.ubuntumini file in a moment.  What matters is that the file matches this entry in /etc/auto.master.

--timeout=300.  This determines how "persistent" the share is.  I have mine set to 300 seconds (five minutes).  There are numerous forums online where you can discuss this heatedly and repeatedly.  

--ghost is a bit interesting.  Normally, if you look under /mnt, you won't actually see anything.  If you know to access /mnt/ubuntumini, for example, then it will appear.  --ghost makes it appear whether you access it or not.  I'm not sure why you WOULDN'T want it ghosted.  I always do.

So we have an entry in our auto.master file that points to our mount point, points to our configuration file, and sets a couple of options.  Let's look at my /etc/auto.ubuntumini file.

```
sudo gedit /etc/auto.ubuntumini
```


```
#
# $Id: auto.misc,v 1.2 2003/09/29 08:22:35 raven Exp $
#
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# Details may be found in the autofs(5) manpage

#cd		-fstype=iso9660,ro,nosuid,nodev	:/dev/cdrom

# the following entries are samples to pique your imagination
#linux		-ro,soft,intr		ftp.example.org:/pub/linux
#boot		-fstype=ext2		:/dev/hda1
#floppy		-fstype=auto		:/dev/fd0
#floppy		-fstype=ext2		:/dev/fd0
#e2floppy	-fstype=ext2		:/dev/fd0
#jaz		-fstype=ext2		:/dev/sdc1
#removable	-fstype=ext2		:/dev/hdd
ubuntumini  		-fstype=nfs,-rsize=8192,wsize=8192,soft,timeo=14,rw        169.254.200.200:/home/jrickard
ubuntuminiwww  		-fstype=nfs,-rsize=8192,wsize=8192,soft,timeo=14,rw        169.254.200.200:/var/www
videomonster  		-fstype=nfs,-rsize=8192,wsize=8192,soft,timeo=14,rw        169.254.200.230:/home/jrickard
videomonsterwww  	-fstype=nfs,-rsize=8192,wsize=8192,soft,timeo=14,rw        169.254.200.230:/var/www
miniTX  			-fstype=nfs,-rsize=8192,wsize=8192,soft,timeo=14,rw        169.254.200.201:/


```

Again, we have lines commented out by # and five lines I've added.

The left most field is the name of the subdirectory that will appear under /mnt.  In my case, I have ubuntumini, ubuntuminiwww, videomonster, videomonsterwww and miniTX.  

The next field is somewhat familiar from your fstab file.  But in this case, we note a -fstype=nfs before our rsize, wsize, timeout, and read/write.  There is also a SOFT entry.   Frankly, I can't recall why I chose SOFT but it has something to do with how autofs tries to access a nonexistent (downserver) type of directory.  

The rightmost field, again similar to our regular NFS setups, indicates the host:/directory we want to mount.  These of course MUST already be setup on the remote machines using NFS server, the regular export fucntions from /etc/exports, etc. just as we normally do with NFS. 

In my case, I mounted my home directory, as well as the web server directory on two machines, videomonster and ubuntumini.  I actually mounted the root file system on miniTX which is the cam server.

One element of note.  BOTH the AUTO.MASTER and AUTO.UBUNTUMINI files require a blank line with line feed after the last entry.  Just an anomaly as to the way the software reads lines until it reaches an end of file.  But don't forget them.

The auto.misc file I copied had the CD entry uncommented.  This has the effect of mounting your CD-ROM in /mnt.  WHich gives you some idea of some other things you can do with autofs.

Once our files are saved.  We can load the files into autofs with the following command:

```
sudo /etc/init.d/autofs restart
```

This will shut down autofs, and then bring it back up.  It reloads the master file, and subsequently the auto.ubuntumini file as it comes back up.

You should now be able to go to /mnt and see the files.

j```
rickard@Mozart:~$ cd /mnt
jrickard@Mozart:/mnt$ ls
miniTX  ubuntumini  ubuntuminiwww  videomonster  videomonsterwww


jrickard@Mozart:/mnt$ cd miniTX
jrickard@Mozart:/mnt/miniTX$ ls
bin    debian-binary  home        lib         mnt   root  sys  var
boot   dev            initrd      lost+found  opt   sbin  tmp  vmlinuz
cdrom  etc            initrd.img  media       proc  srv   usr
jrickard@Mozart:/mnt/miniTX$ 
```

I noted about a ten second delay when I did the cd miniTX command and a slight when when I entered ls.  That was when it was actually mounted.  Subsequent actions in that directory were much quicker.

I do hope this helps with the automounting problems.  The fstab entry is a little bit iffy for me.  Sometimes it seems to load my shares, and sometimes not.  autofs seems a bit more reliable, and it cuts down on network traffic.  If your share timesout, it drops it.  You only generate maintenance traffic when you use it and during the timeout afterwards.

Oh, you don't need to do ANYTHING to make this happen the next time you reboot.  autofs is setup on installation to come up when the system boots.

Jack Rickard

---

### Post by LuisC-SM on 2007-12-22
@Jack Richard

Thanks a lot for this nice howto

This is something I've already used in Mandriva and SuSE but I did not know it was AUTOFS. I was thinking this was some kind of script made by some linux gurus in those distros but now I've confirmed it's not.

Again, thanks a lot. Everyday we learn something new :guitar:

Kind Regards 

Luis.

PS. I believe this should be already installed in ubuntu by default

---

### Post by methodical on 2007-12-31
Edit: Solved

---

### Post by arunpc on 2008-01-03
Hi,
Check whether your NFS server is working properly. If you are sure of that, it should be wrong entry of the credentials.

I have seen this error happening to me and it has mostly been improper credientials. Make sure you have not missed out on capital letters for folder names.

Thanks,
Arun.PC
[www.arunpc.wordpress.com](www.arunpc.wordpress.com)

---

### Post by exactopposite on 2008-01-08
great how to. i used this a compule of months ago to set up my network and i forgot to come back and say thanks.

---

### Post by noremac on 2008-01-14
I imagine this should be easier than I am making it, but I am trying to share a folder on my laptop as to transfer files over to my desktop with a Netgear router between them. I have shared the folder on the laptop(Xubuntu) using NFS. Here is what I put into term and what I get out of it.

```

cameron@cameron-desktop:~$ sudo mount -t nfs cameron-laptop:/home/cameron /home/cameron/Desktop/laptop/
mount.nfs: can't get address for cameron-laptop

```

So am I sharing my /home/cameron folder on my laptop, trying to mount it to a laptop folder on my desktop of my Desktop computer. On the laptop, I wasn't sure what to put in as the allowed host so I have put in the name of my desktop computer, the router given IP of my desktop, and and subnet mask.

Fairly new to all this stuff, so I expect the answer is right under my nose...thanks for any help.

-Cameron

---

### Post by bodhi.zazen on 2008-01-14
Try using the ip address for you laptop rather then host name.

If you want to use host name, place it in /etc/hosts

Add this :

xxx.xxx.x.xxx cameron-laptop

to etc/hosts where xxx.xxx.x.xxx is the laptop ip address

---

### Post by noremac on 2008-01-14
After I did what you said, I was getting permission denied. Did a bit of Googling and found that I needed to change the /etc/export on the server, and now works like a charm. Thanks. Appreciate you getting me on the right step.
-Cameron

---

### Post by billgoldberg on 2008-01-16
This isn't working for me.

I want to share the /home/username folder from 192.168.1.4 with 192.168.1.3

When I want to mount in the terminal using 'sudo mount 192.168.1.4:/home/username /home/username' 

All i get is; already mounted (in more words)

When I go to the network folder, all i see is windows pc (wich i don't have :p)

Could someone give me a step by step walkthrough of all the exact steps that has to be done on both pc's. I like computers and use linux all the time but when it comes to networks i'm lost. It goes without saying that I will thanks the one who does.

I've been struggeling with sharing files between my two ubuntu boxes since feisty came out, i'm now on gutsy :confused: (it never worked)

---

### Post by swampy5 on 2008-01-17
If its any consolation I had nfs working under feisty and then lost it when I upgraded to gutsy - but after a lot of grief I eventually got nfs to work again.
Could you post the /etc/exports file on the 192.168.1.4 computer so we can check its ok?
You can check for basic connectivity with a ping command of course. If you can ping each other then it should be plain sailing - but it never is is it :(

---

### Post by bodhi.zazen on 2008-01-17
> **billgoldberg said:**
> This isn't working for me.

I want to share the /home/username folder from 192.168.1.4 with 192.168.1.3

When I want to mount in the terminal using 'sudo mount 192.168.1.4:/home/username /home/username' 

All i get is; already mounted (in more words)

When I go to the network folder, all i see is windows pc (wich i don't have :p)

Could someone give me a step by step walkthrough of all the exact steps that has to be done on both pc's. I like computers and use linux all the time but when it comes to networks i'm lost. It goes without saying that I will thanks the one who does.

I've been struggeling with sharing files between my two ubuntu boxes since feisty came out, i'm now on gutsy :confused: (it never worked)

First, try an alternate mount point
```
mkdir /home/username/share
sudo mount 192.168.1.4:/home/username /home/username/share
```

Second, review your settings in /etc/exports

Third, Firewall ? error message when you mount ?

---

### Post by katibi on 2008-01-23
I have attempted to complete the instructions and I am still unable to remotely access a second computer on a LAN.  This is the error I receive:

mount.nfs: 192.168.0.103:/katibi failed, reason given by server: Permission denied

I have checked all my settings, and made sure I followed every step carefully.  I have confirmed the contents of

hosts
hosts.allow
hosts.deny
exports

on both the client and the server machines.

I am able to ping the client from the server, and the server from the client.  I can ping the router from either machine.

I have created a directory /username which has the same username as the client computer, and the same UID.

Nothing seems to work.

I love linux, and I find it disappointing that I am not able to get NFS to work.  I spent an entire evening attempting to get vsftp to work without any success (although I can ftp to servers on the internet).  These sorts of things should be easier to get up and running than on windows, but they still are not.

---

### Post by joeashcraft on 2008-01-27
NFS blows my mind. I love it!
Now I don't have to worry about using up all the HD space on my laptop, nor do I need to use slow FTP to r&w files to my server. I can mount NFS and download files to a remote computer transparently.
Now if I could figure out how to do this while not on the same LAN... anyone?

---

### Post by joeashcraft on 2008-01-27
@katibi
What's your /etc/exports have? If you copy/pasted you may have an error in there. I'm thinking 192.168.1.1 instead of 192.168.0.1
hopefully it's that simple

---

### Post by S.Tokarev on 2008-01-29
Kubuntu 7.10 nfs client doesn't mount nfs share from nfs server at boot time. No log errors or any log entries.

While when I issue from the command line
```

sudo mount -a 

```
it mounts the share (auto flag presents) and I can go on.

What could be the problem ? It seems it doesnt try to mount nfs shares from fstab at all. what script from init.d is responsible for mounting ?
Additional: the workstation boots using dhcp/tftp/nfs successfuly and kdm starts ok.

well ... I think I figured the solution out.

---

### Post by TheWizzard on 2008-01-29
can you share your solution?

i have the same issue although automounting used to work...

---

### Post by svennils on 2008-01-29
Ok, so i have tinkered around with NFS to replace my samba server. 
Everything works fine, except the user squashing. 
Server has a few user accounts, sven (1000 and www (1001) are the important ones. My laptop has 2, sven (1000) & bfu(1001).
All data disks on the server are owned by www, since the few users i have given access for useing my web server are not supposed to read these disks, hence permissions 700 on these files too. Samba runs with force user:www, so it has access, and is only activated on the local interface on my own subnet.(the box is a Qos internet router as well) When i mount the nfs share on my laptop, regardless of all_squash status, it changes owner of the mount point on the laptop to bfu(1001), which corresponds to owner of the disk on the server (www,1001). Bfu has 700 permissions on its files, and not even root on the laptop can access the mount point then.   So how do i force the user mapping to something else?
etc/exports looks like this:
/mnt/hdf 192.168.1.1/24(rw,async,all_squash,anonuid=1000,anongid=1000)
anonuid and gid have no effect no matter what i set them. if i change ownership on the server, i can access things normally,  but this is not an option.
Server runs ubuntu server,7.10,  laptop runs 7.10 desktop.
Any ideas?

---

### Post by jarthel on 2008-02-04
does anyone know of a tutorial for NFS + kerberos? The one in the wiki is very vague.

Thank you.

---

### Post by couzin2000 on 2008-02-26
Thanks for the tutorial... very easy, and very helpful - however I do have one small problem that I don't understand. Here's my terminal output:
```
sebastien@sebastien-desktop:~$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon... 
exportfs: Warning: /home/sebastien/Azureus Downloads does not support NFS export.
                                                                         [ OK ]
 * Starting NFS kernel daemon                                            [ OK ] 
sebastien@sebastien-desktop:~$ 

```
Why is the share not supported? Is this to do with permissions, or with which format the drive is in... another program running maybe?

---

### Post by Jose Catre-Vandis on 2008-02-27
> **couzin2000 said:**
> Thanks for the tutorial... very easy, and very helpful - however I do have one small problem that I don't understand. Here's my terminal output:
```
sebastien@sebastien-desktop:~$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon... 
exportfs: Warning: /home/sebastien/Azureus Downloads does not support NFS export.
                                                                         [ OK ]
 * Starting NFS kernel daemon                                            [ OK ] 
sebastien@sebastien-desktop:~$ 

```
Why is the share not supported? Is this to do with permissions, or with which format the drive is in... another program running maybe?

It is most likely the space between Azureus and Downloads. Rename it to be spaceless, or put in double quotes.

---

### Post by Graphite on 2008-03-01
I can't persuade this tutorial to work for me.

Server: 
PC running Ubuntu 6.06
IP address 192.168.2.4

Client:
Laptop running Ubuntu 7.10
IP address 192.168.2.3

The two computers are hooked up to a router, through which they can access the internet. Each of the computers is able to ping the other.

In the server computer I typed:
```
cd /
sudo gedit etc/exports
```

...and saved the file containing this:
```
# /etc/exports: the access control list for filesystems which may be exported 
#                                      to NFS clients. See exports(5).
/home/bugs 192.168.2.3(rw,no_root_squash,async)
```
After saving that file I ran
```
bugs@bugs-desktop:/$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping rps mountd...                                           [ok]
 * Stopping rpc nfsd...                                                [ok]
 * Unexporting directories for NFS kernel daemon...   [ok]
 * Exporting directories for NFS kernel daemon...       [ok]
 * Starting rpc nfsd...                                                  [ok]
 * Starting rpc mountd...                                              [ok]
bugs@bugs-desktop:/$ sudo exportfs -a
bugs@bugs-desktop:/$ 
```

Then on the client laptop:
```
bugs@bugs-laptop:~$ cd /
bugs@bugs-laptop:/$ sudo mkdir files
bugs@bugs-laptop:/$ sudo mount 192.168.2.4:/home/bugs /files
mount.nfs: mount to NFS server '192.168.2.4' failed: timed out, retrying
mount.nfs: mount to NFS server '192.168.2.4' failed: timed out, retrying
bugs@bugs-laptop:/$ 

```

Does anyone know what the problem here is?
I started trying the GUI approach (System>administration>Shared Folders) with no success and now this isn't working either. I've spent hours reading and experimenting and it's driving me crazy!

---

### Post by dgrafix on 2008-03-02
Can you ping it and do you have the correct ports open? 

One thing i did when i set this up was to do this, im not sure what it does exactly but it was in the how to i followed:

After doing that bit you did above:

sudo dpkg-reconfigure portmap
sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-kernel-server restart

Ps, i dont know weather you want this or not, but if you want to make it available to your whole lan use: 192.168.2.1/24 in the exports. This will allow any pc with the first 24bits / 3 bytes (192.168.2)

---

### Post by grahamandchenine on 2008-03-05
Just to add the thumbs up.

Worked a treat.

Not sure why it needs to be more complicated than a Fedora server, but seems far more reliable.

THX.:KS

---

### Post by MountainX on 2008-04-01
> **dannyboy79 said:**
> 

Differences in maximum block sizes between client/server file systems can cause programs to crash

Those are all nice tips! Could you explain the above in more detail? How do we make sure we avoid this problem? 

I set up two different shares that are both located on the same drive on the server with different block size definitions as shown below. Is this a problem?

Client fstab:
192.168.100.3:/SmallDataFiles /home/myuser/SmallDataFiles nfs nocto,rw,rsize=8192,wsize=8192,hard,intr 0 0

192.168.100.3:/Music /home/myuser/Music nfs nocto,rw,rsize=32768,wsize=32768,hard,intr 0 0

---

### Post by konus on 2008-04-03
This really help me ....  Thanx!!!

---

### Post by MountainX on 2008-04-04
Can anyone install a deb (using GDebi) from a network share (nfs)? When I browse to the nfs share in nautilus and right click the deb file and install it the installer crashes. If I copy the file to the local HDD, the installer works fine. Is this an nfs issue?

---

### Post by Tzuikka on 2008-04-05
Hi!
I'm having the exact same problem as Graphite has. 

> Then on the client laptop:
Code:

bugs@bugs-laptop:~$ cd /
bugs@bugs-laptop:/$ sudo mkdir files
bugs@bugs-laptop:/$ sudo mount 192.168.2.4:/home/bugs /files
mount.nfs: mount to NFS server '192.168.2.4' failed: timed out, retrying
mount.nfs: mount to NFS server '192.168.2.4' failed: timed out, retrying
bugs@bugs-laptop:/$

I'm quite sure that I have opened the necessary ports and can ping both, the server and the client.

This is getting really frustrating :confused:
Has anyone found a solution for this?

---

### Post by jammer84 on 2008-05-02
Cheers mate, This worked a dream!!!

---

### Post by couzin2000 on 2008-05-02
> **malco2001 said:**
> **Editing /etc/exports**
the /etc/exports file is used for creating a share on the NFS server

invoke your favorite text editor or
*sudo vi /etc/exports*

Here are some quick examples of what you could add to your /etc/exports

For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255

[LIST]
[*]/files 192.168.1.1/24(rw,no_root_squash,async)
[/LIST]

Or for Read Only from a single machine

[LIST]
[*]/files 192.168.1.2 (ro,async)
[/LIST]
save this file and then in a terminal type
*sudo /etc/init.d/nfs-kernel-server restart*


I'd love to find out about these keywords here:
[LIST]
[*]rw
[*]ro
[*]no_root_squash
[*]async
[*]sync
[*]no_subtree_check
[*]*And more...*
[/LIST]
I have no idea what most of these mean or what they do. Is there a complete reference that exists out there? Or can you just find this in a buried help file?

Awesome work for the howto, BTW - came in very useful.
Should be worthy of mention that NTFS-formatted drives cannot be shared through NFS. I am currently working on changing my drive's format, since I have a whopping 500Gb that I would not be able to access.

As well, would be interesting to find out how BOTH Samba AND NFS can coexist? I'm fairly new at doing this on Ubuntu because I have a Windows background, but I would love to find a howto for both.
Thanks again, great work!

PS just found a LOT of helpful info here: [https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo"). This actually helped me get it working for the first time! Might be worth putting up into the Howto!

---

### Post by DaveinSpain on 2008-05-03
Thanks for a wonderfully easy tutorial.  Everything worked fine right up to 

sudo mount server.mydomain.com:/files /files

I have 2 computers, hostnames LANDING and DOWNSTAIRS, both connected via fast ethernet switch to my DHCP modem which gives Internet access to both machines via a wired LAN without any problems. 

DOWNSTAIRS having been set up as the server as per tutorial, after creating /files on LANDING I entered

sudo mount DOWNSTAIRS:/Shared /files

Shared being a shared folder on each machine.

This produced "Can't get address for DOWNSTAIRS

Did

sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-common restart

Sames result.

This didn't really surprise me as in over a year I have never yet managed to get these two machines to see each other in linux. (Windoze does it without missing a step so I know it can be done)

Having had much advice from many forums, the problem appears to be that I do not appear to have a private IP address for either machine.  I found one of 192.168.1.3 in the Windows configuration (same on both machines) but that appears to be my access to my ISP (either that or Vista and XP are using a Debian Apache server!).  Both machines only have the 1 network interface (eth0) and ifconfig just shows the information for that (public IP address) and lo.

Any suggestions?

Many thanks in advance to all who reply.

Dave

Just thought I'd add the contents of /etc/hosts

127.0.0.1 localhost
127.0.1.1 DOWNSTAIRS

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

127.0.0.1 localhost
127.0.1.1 LANDING

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by couzin2000 on 2008-05-04
Here's another bug I just encountered. After finally getting both PCs to work together, and establishing a working NFS link, I continued to follow the instructions at [http://help.ubuntu.com/community/SettingUpNFSHowTo]("http://help.ubuntu.com/community/SettingUpNFSHowTo") and installed [FONT="Courier New"]autofs[/FONT].

When installed, this thing is supposed to automount the available shares on my server. It refers to a [FONT="Courier New"]auto.master[/FONT] file, which in turn refers to multiple [FONT="Courier New"]auto.*something*[/FONT] files, to group and allow easy access to mounts.

When updating my [FONT="Courier New"]auto.master[/FONT] file, I inserted```
/home/username/Desktop/username-desktop          /etc/auto.home
```and created another [FONT="Courier New"]/etc/auto.home[/FONT] file with the following entry:```
*          192.168.0.155:/media/Downloads
```

This actually works, and I get the expected result: I see the contents of the [FONT="Courier New"]/media/Downloads[/FONT] folder from my 192.xxxxx-located server in my client laptop when I open the [FONT="Courier New"]/home/*username*/Desktop/*username-desktop*[/FONT] folder.

BUT - I also see automatic *drive* icons appear on my client's desktop once the connection's automount is valid, and these are named [FONT="Courier New"].Trash[/FONT] and [FONT="Courier New"].Trash-1000[/FONT]. These have drive icons (not trash can icons) and appear by themselves. They contain the same as the mount point folder I set up on the desktop.

Where do these come from, and how to I get rid of them, or make them NOT appear?

---

### Post by DaveinSpain on 2008-05-04
Poking around it seems that Windows is using a VPN to access it's shares.  I have tried setting one up in Linux, but with exactly the same result - i.e. the machines can't see each other.  I have tried  disconnecting the patch lead from the switch to the modem and switching off the firewall but it made no difference.

Please, does anybody have any ideas what might be going on here?:confused:

---

### Post by bodhi.zazen on 2008-05-04
> **couzin2000 said:**
> I'd love to find out about these keywords here:
[LIST]
[*]rw
[*]ro
[*]no_root_squash
[*]async
[*]sync
[*]no_subtree_check
[*]*And more...*
[/LIST]
I have no idea what most of these mean or what they do. Is there a complete reference that exists out there? Or can you just find this in a buried help file?

Nope, man pages.

From here : [http://www.novell.com/coolsolutions/feature/15986.html](http://www.novell.com/coolsolutions/feature/15986.html)

> There are many options for shares. Here are some of the most common:

[list][*]root_squash - Maps the root user to the nobody user. This has the effect of not allowing a root user on a client to gain root file access permissions on the server.
[*]no_root_squash - Does not map the root user to the nobody user. The root user on a client has the same rights as the root user on the server.
[*]all_squash - Maps all the UIDs and GIDs to the nobody user. This is useful if the share is to have anonymous access, much like an anonymous FTP server.
[*]anonuid, anongid - If root_squash and all_squash are used, the UIDs and GIDs are mapped to the specified UID and GID instead of the nobody user.
[*]ro - Forces all files on the share to be read-only. This is the default behavior.
[*]rw - Allows write access to the share.
[*]sync - Ensures data is written to disk before another request is serviced.[/list]

Additional options here : [http://linux.die.net/man/5/exports](http://linux.die.net/man/5/exports)

Or in a more detailed technical documentation of NFS.

> As well, would be interesting to find out how BOTH Samba AND NFS can coexist? I'm fairly new at doing this on Ubuntu because I have a Windows background, but I would love to find a howto for both.
Thanks again, great work!

Samba works out of the box and allows sharing of both files and printers. IMO it is also more secure as shares require a username and password, and can be "hidden".

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Ghost-syn on 2008-05-09
Hello, Thanks for the FAQ. I followed it and everything is working perfectly. As im not sure if im supposed to post it in a new topic ill try my luck, apologies for any n00bieism.

Im using NFS to share out the home directories of the workstations to the newly created NFS server (latest debian). There wasnt any problems mounting the share, in the beginning... 

However as i added another workstation(all 8.04) things started to become inconsistent with mounting of the home folder. My ultimate goal is to have a consistent home folder across all workstations that the teachers use but cannot change (wallpaper, icons etc). 

Where should i be looking to solve the issue? The server?, workstations? or is this something thats considered bad design ( all home folders mounted to a single unchanging home folder via NFS server)

Any help would be greeeeeatly appreciated :). Any information needed i can provide.

---

### Post by phelan_ward on 2008-05-21
Here seems to be a real bug in nfs since version 1.1.2 of the
nfs-utils. Its already postet:

[https://bugs.launchpad.net/ubuntu/+bug/213444](https://bugs.launchpad.net/ubuntu/+bug/213444)

Has anyone an idea?

---

### Post by Junosix on 2008-06-02
Just wanted to say thanks for that guide. I don't know why but I was a bit scared of NFS as everyone talks about Samba instead, but in fact I much prefer it, it seems a lot quicker and robust.  Got my girlfriend's Windows computer talking to the server by installing Windows Services for UNIX 3.5 from the Microsoft site.

---

### Post by couzin2000 on 2008-06-04
Thanks Bodhi, this is exactly what I needed.

I have been reading through this Howto thread, and I may end up rewriting another one because I fear much info has been left aside. Since the original references were very accurate and fairly complete, I would love to see a manual including *everything*. Hopefully by the time I'm done with this thread there won't be a problem left that cannot be tackled.
Thanks again!!

---

### Post by Coastal Confessions on 2008-06-27
> **Ghost-syn said:**
> However as i added another workstation(all 8.04) things started to become inconsistent with mounting of the home folder. My ultimate goal is to have a consistent home folder across all workstations that the teachers use but cannot change (wallpaper, icons etc).

Did you set the share to be readonly in /etc/exports?

---

### Post by ptgood on 2008-07-04
I set up an home network with two clients and one server (running Xubuntu and Ubuntu).

I followed this HOW TO: [http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing]("http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing")

Everything worked fine, but when i restarted the three machines, i had to restart manually the server kernel with:
***sudo /etc/init.d/nfs-kernel-server restart***

If i dont do that, when i try to mount the folder from clients, i get this: 
***mount.nfs: mount to NFS server 'rpcbind' failed: RPC Error: Program not registered***


Have you any idea?
why should i restart the server manually every time?

Thanks

---

### Post by Coastal Confessions on 2008-07-04
> **ptgood said:**
> Everything worked fine, but when i restarted the three machines, i had to restart manually the server kernel with:
***sudo /etc/init.d/nfs-kernel-server restart***

If i dont do that, when i try to mount the folder from clients, i get this: 
***mount.nfs: mount to NFS server 'rpcbind' failed: RPC Error: Program not registered***

Have you any idea?
why should i restart the server manually every time?

Try using Bootup Manager (bum) to activate the nfs-kernel-server service. See [http://www.marzocca.net/linux/bumdocs.html](http://www.marzocca.net/linux/bumdocs.html).

---

### Post by Stevi on 2008-07-05
Hi,

thanks for this How-To. It works for me but I think it should be a little bit faster. My Server is running [Mythbuntu 8.04](http://www.mythbuntu.org/) (160 GB IDE HD) and from time to time I'd like to watch some recordings on the client machine (Notebook, Ubuntu Hardy, 120 GB S-ATA HD) but this is impossible due to speed issues.

My computers both are connected via wlan to a [Fritz!Box](http://en.wikipedia.org/wiki/FRITZ!Box) Router.

This is my output for a 9,5 MB file:
```
time command cp /home/stevi/Desktop/test.mp3 /media/mythbuntu

real	0m16.590s
user	0m0.004s
sys	0m0.040s
time command cp /media/mythbuntu/test.mp3 /home/stevi/Desktop

real	0m0.064s
user	0m0.004s
sys	0m0.052s
```
fstab entry:
```
192.168.1XX.XX:/home/stevi /media/mythbuntu nfs rsize=8192,wsize=8192,timeo=14,intr
```

Is the speed okay or could it be faster?

Thanks in advance

Stevi.

---

### Post by tobias_84 on 2008-07-05
Hi all.

I tried to read all post but I may have missed it.

Got NFS to work directly but the problem is when I want to create files from the client. If I do 'ls -l' on the client it seem correct but it's the wrong user and group on the server side.

Exempel:
```

//client-user = a (non_root)
//server-user = b (non_root)


a@client:nfs_mount/path/folder$ mkdir test
a@client:nfs_mount/path/folder$ ls -l
drwxr-xr-x  2 a   a   4096 2008-07-05 13:55 test

b@server:nfs_share/path/folder$ ls -l
drwxr-xr-x  2 b   b   4096 2008-07-05 13:55 test

```

The user B doesn't exist on the client, only at the server but user A does exist on both sides.


/etc/passwd
On client:
```

a:x:1000:1000:a,,,:/home/a:/bin/bash

```

On server:
```

b:x:1000:1000:b,,,:/home/b:/bin/bash
a:x:1007:1007:a,,,:/home/a:/bin/bash

```


Is there a way to specify in /etc/exports witch user that owns it?

/share_a-folder x.x.x.x/x(rw,no_root_squash,async)
/share_b-folder x.x.x.x/x(rw,no_root_squash,async)
/share_c-folder x.x.x.x/x(rw,no_root_squash,async)

so if any user adds something to share_b-folder user b is the owner?



Thanx for any help!

/Tobias

---

### Post by Stevi on 2008-07-05
> **Stevi said:**
> This is my output for a 9,5 MB file:
```
time command cp /home/stevi/Desktop/test.mp3 /media/mythbuntu
real	0m16.590s
user	0m0.004s
sys	0m0.040s
time command cp /media/mythbuntu/test.mp3 /home/stevi/Desktop
real	0m0.064s
user	0m0.004s
sys	0m0.052s
```
fstab entry:
```
192.168.1XX.XX:/home/stevi /media/mythbuntu nfs rsize=8192,wsize=8192,timeo=14,intr
```
Is the speed okay or could it be faster?

I played around with my fstab values.
```
192.168.1XX.XX:/home/stevi /media/mythbuntu nfs rw,noatime,v3,rsize=32768,wsize=32768,udp,hard,intr,noauto,users
```
File Size again 9,5 MB:
```
time command cp /home/stevi/Desktop/test3.mp3 /media/mythbuntu
real	0m6.739s
user	0m0.004s
sys	0m0.044s
command cp /media/mythbuntu/test3.mp3 /home/stevi/Desktop
real	0m0.037s
user	0m0.004s
sys	0m0.032s
```

Watch recordings becomes better (I was able to view ten seconds without hanging ;) ) but is still not good enough. Any other ideas which values could speed things up?

---

### Post by ptgood on 2008-07-05
> **ptgood said:**
> I set up an home network with two clients and one server (running Xubuntu and Ubuntu).

I followed this HOW TO: [http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing]("http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing")

Everything worked fine, but when i restarted the three machines, i had to restart manually the server kernel with:
***sudo /etc/init.d/nfs-kernel-server restart***

If i dont do that, when i try to mount the folder from clients, i get this: 
***mount.nfs: mount to NFS server 'rpcbind' failed: RPC Error: Program not registered***


Have you any idea?
why should i restart the server manually every time?

Thanks

> **Coastal Confessions said:**
> Try using Bootup Manager (bum) to activate the nfs-kernel-server service. See [http://www.marzocca.net/linux/bumdocs.html](http://www.marzocca.net/linux/bumdocs.html).**[FONT="Arial Black"]I solved[/FONT]**

I checked in /etc/rc2.d and there was not nfs-kernel-server at all.

So I opened /etc/init.d, I created a link of nfs-kernel-server, I renamed the link to S20nfs-kernel-server and I copied it in /etc/rc2.d

I rebooted the machines and everything work perfectly!!!

---

### Post by NTolerance on 2008-07-25
Anyone know how to get symlinks working with this?  I have some symlinks in a remote share that I'd like access to.  But the problem is that the links appear as they do on the remote machine and therefore point to directories that do not exist on the local machine.  

Symlinks work fine with Samba shares, so I'm wondering if there's a way to make them work here too.

---

### Post by mitjab on 2008-08-18
i install everything but i do not know how to connect now. In network places i can not see other ubuntu.

---

### Post by dmizer on 2008-08-18
> **mitjab said:**
> i install everything but i do not know how to connect now. In network places i can not see other ubuntu.

Follow the instructions in the first post below where it says, "Mounting at boot using /etc/fstab"

---

### Post by mitjab on 2008-08-18
i try but not working. Folder is empty or not open it.

---

### Post by arrrghhh on 2008-08-19
> **NTolerance said:**
> Anyone know how to get symlinks working with this?  I have some symlinks in a remote share that I'd like access to.  But the problem is that the links appear as they do on the remote machine and therefore point to directories that do not exist on the local machine.  

Symlinks work fine with Samba shares, so I'm wondering if there's a way to make them work here too.

just use the bind function with mount.  it's how i get users to view other disks via ftp.  works much better than symlinks (in cases such as this...)

---

### Post by bodhi.zazen on 2008-08-20
+1  bind.

mount --bind /dev /mount_point

---

### Post by arrrghhh on 2008-08-21
well i have an NFS issue now.  it seems i cannot export NTFS with NFS - and there have been a lot of potential solutions i found (including installing the latest git of the linux kernel...) but none particularly appealing.  i found when i removed nfs-kernel-server and installed nfs-user-server, my NTFS drives mounted!  and it was fast!  but after more poking around it seems i'm actually using nfsV2... so what i don't get is i'm using an older version of nfs... and it works better?  i'd really like to use nfsV4, but if it doesn't export NTFS it doesn't do me a whole lotta good.

---

### Post by rchrdlandis on 2008-08-21
tried you instructions everything went well until I got to 
richard@richard-desktop:/etc$ sudo mount /files
mount.nfs: access denied by server while mounting 192.168.2.4:/files
That is what came back.  Any ideas? :confused:

---

### Post by Roman0 on 2008-08-27
@rchrdlandis

Have you set both server and client on all machines? I had this problem when I tried to export a folder, and mount to it from another server at the same time. Best works for me when one machine acts as a server, the other as a client.

---

### Post by NTolerance on 2008-08-27
> **arrrghhh said:**
> just use the bind function with mount.  it's how i get users to view other disks via ftp.  works much better than symlinks (in cases such as this...)

Yeah, that looks like the proper way to fix it.  Shame I already have a ton of symlinks that programs are dependent on.  Would take a long time to add them all to /etc/fstab and test them out.  :(

---

### Post by trash on 2008-09-02
> **dannyboy79 said:**
> you can't use a * to define which computers can connect to the share, at least I don't think so. here is a guide with more specific details and a little more explaination, it's for gentoo but applies. [http://gentoo-wiki.com/HOWTO_Share_Directories_via_NFS#Modify_EXPORTS](http://gentoo-wiki.com/HOWTO_Share_Directories_via_NFS#Modify_EXPORTS)

also, do you have any rules for iptables? you can find out by typing in a terminal
sudo iptables -L

if this returns anything, than it's poossible that your nfs seerver isn't allowing any connections to it. again the gentoo guide will help. I am sure if you follow the guide you'll be a-ok!

or you could read post 39 of this thread as a guy had the exact same issue and solved it due to him calling the wrong mount points out in botht the client and the server. to make sure it's not the tilde (~), make sure you use full directory locations, /home/username/ instead.

Thanks for that link dannyboy it helped clarify my glaring error which was in exports, I had always assumed the machine name was the machine doing the exporting... never thought it would be the client machine:lolflag:

---

### Post by pannerrammer on 2008-11-03
Hi All.

ubuntu 8.10 appears to revert back to dhcp when you reboot - losing your static ip settings... which will I think cause the nfs described here to fail!

Anyone had the same problem, or got a solution?

Phil

---

### Post by pmorton on 2008-11-04
This a great Howto.  But there is a permissions issue that often comes up, and the solution can take a bit of time to track down among the many posts here. 

It arises because the user, although registered with the same username and password on both server and client, may  not have the same numeric User ID (uid), or be a member of the same group with the same log-in Group ID (gid) on both machines. Why that should affect matters isn't at all clear; if it's not what you'd call a bug, it's certainly none too elegant.

Assume  /etc/exports shares  the directory /home/public with permissions 770 (drwxrwx---) and ownership root:users.  You'd expect all members of the "users" group to get access. But that's not necessarily the case. It depends on their uid and gid on client and server matching, and that's a matter of chance. NFS seems to ignore the names and use the numeric values as identifiers.

To check userx's UID and GID, on each machine do:

```
id userx
```

which typically might return:

```
uid=1001(userx) gid=100(users) groups=100(users),115(admin),...etc..
```

If userx is not a member of the initial log-in group 'users' on both machines, they must be made so with:

```
sudo usermod -g users userx
```

And if either of the uid's and gid's don't match, they must be changed on one machine or the other so that they do, by means of:

```
sudo usermod -u 1001 userx
sudo groupmod  -g 100 users
```


Then on server do:

```
sudo exportfs -a
sudo /etc/init.d/nfs-kernel-server restart
```

And on client do:

```
sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-common restart
```

That should fix the Permission Denied error.

---

### Post by scarf on 2008-12-17
i have followed the [autofs tutorial on page 20](http://ubuntuforums.org/showpost.php?p=3971417&postcount=191) and that is working.  thanks.

however, i have some other directories in /mnt that i use for other purposes, and i notice that, after starting autofs, those directories disappear (and are inaccessible) and my autofs directories appear.  when i stop autofs, the directories come back and are accessible once again.  is there any way to get autofs to play nice with the directories that are already in /mnt?

---

### Post by J@n on 2008-12-17
> **malco2001 said:**
> [B]Why NFS?
[/B]
I simply wanted to experiment with NFS, and couldn't seem to find the documentation here on the forums.  I found using NFS just as easy if not easier than using Samba for sharing between a few of my Unix based systems.  In order to share a folder it only required a single line in a configuration file under /etc/exports, and a single line under /etc/fstab on the client to mount the share on each client at boot.

Thanks man!

I did not even have to read the other posts. This did the trick.

Greetz,

J@n

---

### Post by sdyson on 2008-12-28
> **pmorton said:**
> 
And if either of the uid's and gid's don't match, they must be changed on one machine or the other so that they do, by means of:

```
sudo usermod -u 1001 userx
sudo groupmod  -g 100 users
```


I found I had to update the user's GID as well. e.g.

```
sudo usermod -u 1001 userx
sudo groupmod  -g 100 users
**sudo usermod  -g 100 userx**

```

---

### Post by timzak on 2008-12-29
I'm going to give this another go.  I tried about a year ago and was too thick-headed at the time to make NFS work.  Before I start, I had a question about the server/client relationship:  can a client machine retrieve files from the server?  If not, how does one go about allowing two-way transfer of files?  Or is that contrary to the nature of NFS?  I'd like to be at any machine on my network and retrieve a file from any other machine.

Thanks.

---

### Post by Coastal Confessions on 2008-12-29
> **timzak said:**
> I'm going to give this another go.  I tried about a year ago and was too thick-headed at the time to make NFS work.  Before I start, I had a question about the server/client relationship:  can a client machine retrieve files from the server?  If not, how does one go about allowing two-way transfer of files?  Or is that contrary to the nature of NFS?  I'd like to be at any machine on my network and retrieve a file from any other machine.

Thanks.

The purpose of NFS is to mount a remote exported filesystem so that it works like a local filesystem. So yes, an NFS client would be able to retrieve files from an NFS server if the client has mounted the server's filesystem. You could simply use **cp** to retrieve the file.

However, it sounds like you don't really need NFS to do what you want. If you just want to occasionally copy individual files between machines, use **scp**. [http://en.wikipedia.org/wiki/Secure_copy](http://en.wikipedia.org/wiki/Secure_copy)

---

### Post by Scott O'Nanski on 2008-12-30
> **malco2001 said:**
> [B]Why NFS?
[/B]
I simply wanted to experiment with NFS, and couldn't seem to find the documentation here on the forums.  I found using NFS just as easy if not easier than using Samba for sharing between a few of my Unix based systems.  In order to share a folder it only required a single line in a configuration file under /etc/exports, and a single line under /etc/fstab on the client to mount the share on each client at boot.

I mostly edited and moved things around from these guides to make a more complete single guide to getting this working using Ubuntu.  

[http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html](http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html) (for client configuration)
[http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-nfs-mount.html](http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-nfs-mount.html) (for mounting using fstab)
[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing) (for server configuration)
[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/network-nfs.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/network-nfs.html) (contains more info about NFS)

**Install NFS Server Support**
at the terminal type
*sudo apt-get install nfs-kernel-server nfs-common portmap*
[COLOR="Red"]When configuring portmap do =not= bind loopback. If you do you can either edit /etc/default/portmap by hand or run:[/COLOR]
[I]sudo dpkg-reconfigure portmap
sudo /etc/init.d/portmap restart[/I]

**Editing /etc/exports**
the /etc/exports file is used for creating a share on the NFS server

invoke your favorite text editor or
*sudo vi /etc/exports*

Here are some quick examples of what you could add to your /etc/exports

For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255

[LIST]
[*]/files 192.168.1.1/24(rw,no_root_squash,async)
[/LIST]

Or for Read Only from a single machine

[LIST]
[*]/files 192.168.1.2 (ro,async)
[/LIST]
save this file and then in a terminal type
*sudo /etc/init.d/nfs-kernel-server restart*

Also aftter making changes to /etc/exports in a terminal you must type
*sudo exportfs -a*

**Install NFS client support**
sudo apt-get install portmap nfs-common

**Mounting manually**
Example to mount server.mydomain.com:/files to /files.  In this example server.mydomain.com is the name of the server containing the nfs share, and files is the name of the share on the nfs server

The mount point /files must first exist on the client machine.   
[I]cd /
sudo mkdir files[/I]

to mount the share from a terminal type

*sudo mount server.mydomain.com:/files /files*

Note you may need to restart above services:
[I]sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-common restart[/I]

**Mounting at boot using /etc/fstab**
Invoke the text editor using your favorite editor, or
*gksudo gedit /etc/fstab*

In this example my /etc/fstab was like this: 
[LIST]
[*]server.mydomain.com:/files  /files   nfs rsize=8192,wsize=8192,timeo=14,intr
[/LIST]
You could copy and paste my line, and change &#8220;servername.mydomain.com:/files&#8221;, and &#8220;/files&#8221; to match your server name:share name, and the name of the mount point you created.
[COLOR="Red"]It is a good idea to test this before a reboot in case a mistake was made. [/COLOR]
type
*mount /files *
in a terminal, and the mount point /files will be mounted from the server.

This isn't written very well. For instance, when you state;

```
For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255

[LIST]
[*]/files 192.168.1.1/24(rw,no_root_squash,async)
[/LIST]

Or for Read Only from a single machine

[LIST]
[*]/files 192.168.1.2 (ro,async)
[/LIST]

```

What exactly do you mean? There's already text commented out in the file I'm opening, so WHERE does this text go? Furthermore, WHAT does "rw, no_root_squash" do?  As well, is the IP address the IP address of router, or a machine networked to a router?

I get ```
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.1/24:/files".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: Warning: /files does not exist

``` When I put that exact line in the file you instructed to open.

Am I supposed to define a folder for sharring, and is the path to that folder supposed to be in place of "/files"?

---

### Post by Coastal Confessions on 2008-12-31
> **Scott O'Nanski said:**
> This isn't written very well. For instance, when you state;

```
For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255

[LIST]
[*]/files 192.168.1.1/24(rw,no_root_squash,async)
[/LIST]

Or for Read Only from a single machine

[LIST]
[*]/files 192.168.1.2 (ro,async)
[/LIST]

```

What exactly do you mean? There's already text commented out in the file I'm opening, so WHERE does this text go? Furthermore, WHAT does "rw, no_root_squash" do?  As well, is the IP address the IP address of router, or a machine networked to a router?


That goes in /etc/exports, as indicated in the original post. See exports(5) for explanations of the options.

> **Scott O'Nanski said:**
> I get ```
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.1/24:/files".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: Warning: /files does not exist

``` When I put that exact line in the file you instructed to open.

Am I supposed to define a folder for sharring, and is the path to that folder supposed to be in place of "/files"?

You can export any path you want. /files is just an example.

---

### Post by dwoods99 on 2009-01-03
@Scott, you missed this part...
> Mounting manually
Example to mount server.mydomain.com:/files to /files. In this example server.mydomain.com is the name of the server containing the nfs share, and files is the name of the share on the nfs server

The mount point /files must first exist on the client machine.
cd /
sudo mkdir files

I only followed the first post and got it working without problems between a server and a media player.

More info can be found on the [Sourceforge NFS guide]("http://nfs.sourceforge.net/nfs-howto/").

Thanks for this guide which made it simple for what I needed.

---

### Post by eldaria on 2009-01-03
> **mike3k said:**
> If you're connection to a Linux NFS server from Mac OS X, you need to specify 'insecure' in your exports and map the user IDs since Macs use uid 501 for the first regular user. For my /etc/exports I use:

/home   192.168.0.0/255.255.255.0(rw,async,insecure,all_squash,anonuid=1000,anongid=1000)

Yay, I was fighting with this. :-)

---

### Post by zenrox on 2009-01-03
still works wonderfully

---

### Post by wildchief01 on 2009-01-07
Hello,

This is quite useful
[http://www.davidstclair.co.uk/networking/create-an-nfs-share-with-microsoft-services-for-uni-15.html]("http://www.davidstclair.co.uk/networking/create-an-nfs-share-with-microsoft-services-for-uni-15.html")

---

### Post by bayvista on 2009-01-19
Great stuff. Well done.

I am using my Desktop as the server and Laptop as the client. I can mount a shared Desktop folder on the Laptop. How do I mount a shared Laptop folder on the Desktop (Server).

I want to be able to see my Laptop folders in Nautilus.

This is what happens:

david@david-desktop:~$ sudo mount -t nfs hp-laptop:/home /media/hp-laptop 
[sudo] password for david: 
mount.nfs: access denied by server while mounting hp-laptop:/home
david@david-desktop:~$

---

### Post by dmizer on 2009-01-19
> **bayvista said:**
> Great stuff. Well done.

I am using my Desktop as the server and Laptop as the client. I can mount a shared Desktop folder on the Laptop. How do I mount a shared Laptop folder on the Desktop (Server).

I want to be able to see my Laptop folders in Nautilus.

This is what happens:

david@david-desktop:~$ sudo mount -t nfs hp-laptop:/home /media/hp-laptop 
[sudo] password for david: 
mount.nfs: access denied by server while mounting hp-laptop:/home
david@david-desktop:~$
Your laptop should be thought of as a file server when it is configured to share files to your desktop.

If you want the desktop to see files on the laptop, you will have to follow the server section of this howto on the laptop.

---

### Post by bayvista on 2009-01-19
Many thanks. I did not realize that I could have 2 servers in my network. It's all working now.

---

### Post by taintedsushi on 2009-02-04
Having come to the end of this thread, I was hoping someone might be able to help me with this error.  

I am trying to connect to a SNAP NAS server that has NFS enabled and my UID and IP entered in a table for access (although this is supposed to be optional).

```
mount.nfs: trying 192.168.1.3 prog 100003 vers 3 prot UDP port 2049
mount.nfs: trying 192.168.1.3 prog 100005 vers 3 prot UDP port 1029
mount.nfs: text-based options (retry): 'v2,addr=192.168.1.3,nfsvers=3,proto=udp'
mount.nfs: access denied by server while mounting 192.168.1.3:/SHARE2

```

If it's a server side issue, I'm not sure what I need to change.

---

### Post by bayvista on 2009-02-06
Hi,

I had a lot of trouble with this message. Eventually, it turned out that my MOUNT command did not match the file system which I had exported. If you are going to a server, I assume that you have done an 'exportfs' from the server to your client. From the server, run:

exportfs -v

I run a server, david-desktop, and a client, hp-laptop. 

On my server, 
david@david-desktop:~/programs/rsync$ exportfs -v
/home/pam     	david-desktop(rw,async,wdelay,no_root_squash,no_subtree_check)
david@david-desktop:~/programs/rsync$

showing that I have exported the /home/pam directory from the client to my server, david-desktop . Now I can mount "home/pam" on my server.

sudo mount hp-laptop:/home/pam     /media/hp-laptop

It is ESSENTIAL that the shared filesystem name matches what you put in the MOUNT command. In my case, /home/pam for client hp-laptop. I spent a week getting this right!!!

---

### Post by taintedsushi on 2009-02-08
This server is a NAS so there is no real option to export anything.  The server simply has an enable/disable checkbox.

>>UPDATE

I actually got this working but setting up a user on the snap server called "guest" with no username/password.  

To restrict access to the server, I did find this : [Snap NFS setup]("http://support.overlandstorage.com/jive/entry!default.jspa?categoryID=829&externalID=12622ASK&fromSearchPage=true") BUT, I still get access denied without a guest account.

---

### Post by EowynCarter on 2009-02-28
> sudo apt-get install portmap nfs-common

Mounting manually
Example to mount server.mydomain.com:/files to /files. In this example server.mydomain.com is the name of the server containing the nfs share, and files is the name of the share on the nfs server

The mount point /files must first exist on the client machine.
cd /
sudo mkdir files

to mount the share from a terminal type

sudo mount server.mydomain.com:/files /files

Note you may need to restart above services:
sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-common restart

Mmm. isn't there anything well ... simpler ?
Like what we can do with smb shares ?
Hell, typing command line to mount someting, fell like going a few years back...

---

### Post by Jose Catre-Vandis on 2009-02-28
> **EowynCarter said:**
> Mmm. isn't there anything well ... simpler ?
Like what we can do with smb shares ?
Hell, typing command line to mount someting, fell like going a few years back...

But once its done, its done and you just use your file manager.

For smb shares you use samba.

If you want to share files from a linux file server to a windows box you can either try the [nfs solution]("http://ubuntuforums.org/showthread.php?t=310168") or [dokan]("http://ubuntuforums.org/showthread.php?t=1027820") to share files through ssh

---

### Post by dmizer on 2009-02-28
> **EowynCarter said:**
> Mmm. isn't there anything well ... simpler ?
Like what we can do with smb shares ?
Hell, typing command line to mount someting, fell like going a few years back...
This NFS howto is for a dedicated NFS file server. And it is EXTREMELY easy to setup compared to Samba.

This is how to create a proper Samba server: [http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

And this is how to mount Samba shares: [http://www.ubuntuforums.org/showthread.php?t=288534](http://www.ubuntuforums.org/showthread.php?t=288534)

As you can see, "easy" is relative.

Just because DOS was CLI and is old, doesn't mean the CLI was a bad interface. If you get past the notion that CLI is old and useless, you'll have a much better time adjusting to Linux and Ubuntu. Linux is not Windows, and one of the things that makes it different is that it has a robust and powerful CLI.

---

### Post by Gramps on 2009-02-28
I use NFS and AutoFS to auto mount the shares on the other Ubuntu machines.
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

---

### Post by EowynCarter on 2009-03-01
> **Jose Catre-Vandis said:**
> But once its done, its done and you just use your file manager.

For smb shares you use samba.

If you want to share files from a linux file server to a windows box you can either try the [nfs solution]("http://ubuntuforums.org/showthread.php?t=310168") or [dokan]("http://ubuntuforums.org/showthread.php?t=1027820") to share files through ssh

Well, i'll probably end up writting these in the fstab on my desktop, it will be easier to have it connect everytimes. But then, a gui to do that would be nice. 

But my laptop is an other problem, as it's not always connected to the server.
if you have a "connect to smb share' in the gui, why not a "connect to nfs share" ?

How do i mount the dissque in read / write ? Nautilius won't let me create / edit file. the weird part is : delete works. :confused:

---

### Post by Jose Catre-Vandis on 2009-03-01
> **EowynCarter said:**
> Well, i'll probably end up writting these in the fstab on my desktop, it will be easier to have it connect everytimes. But then, a gui to do that would be nice. 

Thats a good plan, easy connect on each boot

> **EowynCarter said:**
> But my laptop is an other problem, as it's not always connected to the server.
if you have a "connect to smb share' in the gui, why not a "connect to nfs share" ?

"mount" is fairly understanding if you are not connected to the server, so you don't need to worry about this too much.

> **EowynCarter said:**
> How do i mount the dissque in read / write ? Nautilius won't let me create / edit file. the weird part is : delete works. :confused:

Do you mean the nfs share? If so, you have to work the permissions on the nfs server you can't do it from the client. best thing to do is setup a user with the same credentials as your client on the server, and give that user read/write permissions. Then when you connect from the client as "that user" permissions are all sorted. what I do, becuae all the files on my nfs server are only local and not internet facing, is given them all 777 permissions, then I don't have to worry.

---

### Post by EowynCarter on 2009-03-01
> **Jose Catre-Vandis said:**
> Thats a good plan, easy connect on each boot



"mount" is fairly understanding if you are not connected to the server, so you don't need to worry about this too much.



Do you mean the nfs share? If so, you have to work the permissions on the nfs server you can't do it from the client. best thing to do is setup a user with the same credentials as your client on the server, and give that user read/write permissions. Then when you connect from the client as "that user" permissions are all sorted. what I do, becuae all the files on my nfs server are only local and not internet facing, is given them all 777 permissions, then I don't have to worry.

Permissions are setted all right. Plus the fact i was able to delete files say i have write right don't it ? If i don't have write acces i shoudn't be able to delete either.

Well, doing a "chmod 777" on the directory where i mount did it.

Ok an other question : when the directoires are not mounted, i don't want to see them in the media folder (There are enough stuf there already). Anyway to do that ?

---

### Post by Jose Catre-Vandis on 2009-03-01
> **EowynCarter said:**
> Ok an other question : when the directoires are not mounted, i don't want to see them in the media folder (There are enough stuf there already). Anyway to do that ?

I don't have a definitive answer on this one, maybe someone else can chip in with a better solution. I guess what I would do is write a bash script that:

a) checked for the nfs shares (don't how to do this bit! - can't find a "test" option for "mount")
but a single command can be used to check if the server is serving up nfs:
```
rpcinfo -p ip-of-server | grep -m 1 -o nfs
```
should return "nfs" so you can run an if on this in the code
b) if there, created the directory
c) mounted the share

You could always move some stuff out of /media and into /mnt to reduce clutter, or you can (as root) create other directories in / for your shares.

---

### Post by etstar on 2009-03-06
so i've had nfs running on my home setup for a while. the one small irritant is that it won't automount at boot through my fstab. 'mount media/shared_dir' works just fine, so it doesn't seem to be a permission thing.

here's the fstab line for my nfs:

```
10.0.1.76:/bigboy /media/bigboy nfs rw,user,auto 0 0

```

could this be something to do with when services are started on ubuntu? this USED to work. is mount being activated before the network turns on?

---

### Post by Jose Catre-Vandis on 2009-03-06
> **etstar said:**
> so i've had nfs running on my home setup for a while. the one small irritant is that it won't automount at boot through my fstab. 'mount media/shared_dir' works just fine, so it doesn't seem to be a permission thing.

here's the fstab line for my nfs:

```
10.0.1.76:/bigboy /media/bigboy nfs rw,user,auto 0 0

```

could this be something to do with when services are started on ubuntu? this USED to work. is mount being activated before the network turns on?

Try
```
10.0.1.76:/bigboy /media/bigboy nfs rsize=8192,wsize=8192,timeo=14,intr,bg
```

Works for me everytime (and by that I mean I use it on many different PCs and setups) from my ubuntu based nfs server. The exports file on the server would contain (for your example):
```
/media/bigboy 10.0.1.76/24(rw,no_root_squash,async,no_subtree_check)
```

---

### Post by etstar on 2009-03-06
> **Jose Catre-Vandis said:**
> Try
```
10.0.1.76:/bigboy /media/bigboy nfs rsize=8192,wsize=8192,timeo=14,intr,bg
```

Works for me everytime (and by that I mean I use it on many different PCs and setups) from my ubuntu based nfs server. The exports file on the server would contain (for your example):
```
/media/bigboy 10.0.1.76/24(rw,no_root_squash,async,no_subtree_check)
```

thanks for the reply.
tried your suggestion.
still no automount at boot.
mount -a still works the same.

---

### Post by Jose Catre-Vandis on 2009-03-07
Hmmm that doesn't make sense. If 
```
sudo mount -a
``` works, then the line you have in fstab is doing its thing, so you are right to suggest it is something to do with when actions on fstab are happening during boot. Is there anything in your boot logs (/var/log/syslog) or dmesg that can help? Have you done a cold restart recently (i.e. completely shut down the PC and started up again, as sometimes this helps to get "clean")? Where is your mount line in fstab, at the end of the file? If not put it at the end, boot will have to mount the / file system before it can mount any others.

---

### Post by datarhythm on 2009-03-27
Great post. Might I suggest including these resources in the first post?

[http://linux.die.net/man/5/exports](http://linux.die.net/man/5/exports)
[http://linux.die.net/man/5/nfs](http://linux.die.net/man/5/nfs)

Knowing all the available parameters and what they do in the export/fstab file is nice to know.

---

### Post by rmartinus on 2009-05-02
Excellent guide! I can now connect to my NFS server.

---

### Post by statmonkey on 2009-06-06
Thank you and thank you dmizer for pointing to this thread.  Great how to, simple, clear and easy.  Would have never gone this route without the tip off.

---

### Post by VastOne on 2009-06-11
I have successfully setup NFS and client but am stuck at an issue.

On the server I have a directory on sd8 that is mounted there as media/HP

Is that all I would have to put in the /etc/export file like this:

/media/HP 192.168.1.0/24(rw,no_root_squash,async)

Also, I mounted an NFS from the client using /home (on another install how to that I should have ignored)

I cannot clear that mount now using umount

My dh -f shows:

192.168.4.2:/home    80G  628M   75G   1% /home 

as being mounted and umount will not clear it.  Is there a way from NFS client to clear mounts?

Thank you

---

### Post by shane2peru on 2009-06-16
I found this:
```

/home/username/directory 192.168.1.0/24(rw,no_root_squash,async)

```
to be non-functional in my setup. 

This however worked:
```

/home/username/directory 192.168.1.0/255.255.255.1(rw,no_root_squash,async)

```
That comes straight from their web page:
[http://nfs.sourceforge.net/nfs-howto/ar01s03.html#config_server_setup](http://nfs.sourceforge.net/nfs-howto/ar01s03.html#config_server_setup)

I don't really understand the 0/24 thing, I remember reading something about it, however it was quite, confusing to me.  :)  Hope that helps someone. 

Shane

---

### Post by dmizer on 2009-06-16
Don't know why the /24 wouldn't work. It's working for me.

This explained in more detail on page 3: [http://ubuntuforums.org/showpost.php?p=1707369&postcount=25](http://ubuntuforums.org/showpost.php?p=1707369&postcount=25)

Essentially, an IP address is made up of 4 octets (octet meaning 8 bits). The /## equals how many bits of the IP address need to match in order to allow the connection.

192.168.1.0/8 will allow resolution for all computers with addresses of 192.x.x.x
192.168.1.0/16 will allow resolution for all computers with addresses of 192.168.x.x
192.168.1.0/24 will allow resolution for all computers with addresses of 192.168.1.x

---

### Post by carloshiga on 2009-06-17
> **etstar said:**
> thanks for the reply.
tried your suggestion.
still no automount at boot.
mount -a still works the same.

I have the same problem here [not mounting nfs at boot but it works with mount -a]. Did you solve that?
Thanks

---

### Post by CylnZ on 2009-06-17
Thank you so much for this tutorial, it was enlightening.

---

### Post by ZLance on 2009-06-24
I have this problem.

I did everything in the comperhensive walkthrough and used yours as well, the server is setup and client too, both know eachother hostname-ip and are in each other's hosts.allow. The directory to be shared is in /etc/exports on the server with ip for the client. All daemons restarted. When I try to "~$ mount (server-ip):/pathway/on/server/to/shared/directory /local/pathway/to/be/mounted" I get a hold up for 30 secs and then the message "mount.nfs: mount system call failed".

What could be the problem here?

---

### Post by shane2peru on 2009-06-24
> **ZLance said:**
> I have this problem.

I did everything in the comperhensive walkthrough and used yours as well, the server is setup and client too, both know eachother hostname-ip and are in each other's hosts.allow. The directory to be shared is in /etc/exports on the server with ip for the client. All daemons restarted. When I try to "~$ mount (server-ip):/pathway/on/server/to/shared/directory /local/pathway/to/be/mounted" I get a hold up for 30 secs and then the message "mount.nfs: mount system call failed".

What could be the problem here?

This may seem like a simplistic answer, and isn't meant as an insult, but many times I have looked over the most simple things.  Do you have a firewall installed and enabled?  Or did you have?  I ran into this problem and even after uninstalling it, it left iptables configured or something.  I had to purge it before moving on.

Shane

---

### Post by shane2peru on 2009-06-24
> **dmizer said:**
> Don't know why the /24 wouldn't work. It's working for me.

This explained in more detail on page 3: [http://ubuntuforums.org/showpost.php?p=1707369&postcount=25](http://ubuntuforums.org/showpost.php?p=1707369&postcount=25)

Essentially, an IP address is made up of 4 octets (octet meaning 8 bits). The /## equals how many bits of the IP address need to match in order to allow the connection.

192.168.1.0/8 will allow resolution for all computers with addresses of 192.x.x.x
192.168.1.0/16 will allow resolution for all computers with addresses of 192.168.x.x
192.168.1.0/24 will allow resolution for all computers with addresses of 192.168.1.x
This is odd, but this seems to work for me know.  I think I had to reboot for whatever reason.  Thanks for the simplistic explanation, that is what I needed. 

Shane

---

### Post by rldev on 2009-07-01
After a whole day of pulling my hair out, I am able to mount. However, when I do mount I am barely able to view contents of the nfs server. My client machine comes to a complete halt when trying to open files. Even trying to cd and ls into the share directory can take minutes at a time. The system just hangs and hangs. There is some serious bottleneck somewhere. I am able to ping the machines with no isse.

I don't have this problem with Samba, but Samba was doing a terrible job streaming audio files over the network. I'm a noob and would appreciate any thoughts on this. I just dumped Windows Vista and I don't want to go back.

EDIT:

In fact any command I run in the directory that contains the share takes forever. My share is in /home/Public _Media   if I run ls -la in /home, it takes minutes to work. If I run it in /home/user , there is no problem.

Portmap is running
rocco@rocco-laptop /home/Public_Media $ ps ax|grep portmap
 4228 ?        Ss     0:00 /sbin/portmap
 7066 pts/0    R+     0:00 grep --colour=auto portmap

/var/log/messages

Jul  1 22:32:23 rocco-laptop kernel: [ 4782.304528] nfs: server 192.168.1.4 OK
Jul  1 22:40:26 rocco-laptop sudo: pam_sm_authenticate: Called
Jul  1 22:40:26 rocco-laptop sudo: pam_sm_authenticate: username = [rocco]
Jul  1 22:40:26 rocco-laptop sudo: Warning: Using default salt value (undefined in ~/.ecryptfsrc)
Jul  1 22:40:26 rocco-laptop kernel: [ 5266.020958] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul  1 22:43:15 rocco-laptop kernel: [ 5434.980067] nfs: server 192.168.1.4 not responding, still trying
Jul  1 22:49:31 rocco-laptop kernel: [ 5810.276430] nfs: server 192.168.1.4 OK
Jul  1 22:59:20 rocco-laptop sudo: pam_sm_authenticate: Called
Jul  1 22:59:20 rocco-laptop sudo: pam_sm_authenticate: username = [rocco]
Jul  1 22:59:20 rocco-laptop sudo: Warning: Using default salt value (undefined in ~/.ecryptfsrc)
Jul  1 23:01:28 rocco-laptop kernel: [ 6527.597067] nfs: server 192.168.1.4 not responding, still trying
Jul  1 23:10:10 rocco-laptop kernel: [ 7049.063845] CE: hpet increasing min_delta_ns to 15000 nsec

Below are some iperf tests

Server to client

office-server rocco # iperf -u -c 192.168.1.7 -i 1
------------------------------------------------------------
Client connecting to 192.168.1.7, UDP port 5001
Sending 1470 byte datagrams
UDP buffer size:   110 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.4 port 56345 connected with 192.168.1.7 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 1.0 sec  16.0 GBytes    137 Gbits/sec
[  3]  1.0- 2.0 sec  4.00 GBytes  34.4 Gbits/sec
[  3]  2.0- 3.0 sec  4.00 GBytes  34.4 Gbits/sec
[  3]  3.0- 4.0 sec  4.00 GBytes  34.4 Gbits/sec
[  3]  4.0- 5.0 sec  4.00 GBytes  34.4 Gbits/sec
[  3]  5.0- 6.0 sec  4.00 GBytes  34.4 Gbits/sec
[  3]  6.0- 7.0 sec  4.00 GBytes  34.4 Gbits/sec
[  3]  7.0- 8.0 sec  4.00 GBytes  34.4 Gbits/sec
[  3]  8.0- 9.0 sec  4.00 GBytes  34.4 Gbits/sec
[  3]  9.0-10.0 sec  4.00 GBytes  34.4 Gbits/sec
read failed: Connection refused
[  3] WARNING: did not receive ack of last datagram after 1 tries.
[  3]  0.0-10.0 sec  52.0 GBytes  44.6 Gbits/sec
[  3] Sent 893 datagrams

Client to Server Wireless
rocco-laptop samba # iperf -u -c 192.168.1.4 -i 1
------------------------------------------------------------
Client connecting to 192.168.1.4, UDP port 5001
Sending 1470 byte datagrams
UDP buffer size:   110 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.7 port 55371 connected with 192.168.1.4 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 1.0 sec    129 KBytes  1.06 Mbits/sec
[  3]  1.0- 2.0 sec    128 KBytes  1.05 Mbits/sec
[  3]  2.0- 3.0 sec    128 KBytes  1.05 Mbits/sec
[  3]  3.0- 4.0 sec    128 KBytes  1.05 Mbits/sec
[  3]  4.0- 5.0 sec    128 KBytes  1.05 Mbits/sec
[  3]  5.0- 6.0 sec    128 KBytes  1.05 Mbits/sec
[  3]  6.0- 7.0 sec    129 KBytes  1.06 Mbits/sec
[  3]  7.0- 8.0 sec    128 KBytes  1.05 Mbits/sec
[  3]  8.0- 9.0 sec    128 KBytes  1.05 Mbits/sec
[  3]  9.0-10.0 sec    128 KBytes  1.05 Mbits/sec
[  3]  0.0-10.0 sec  1.25 MBytes  1.05 Mbits/sec
[  3] Sent 893 datagrams
[  3] WARNING: did not receive ack of last datagram after 10 tries.

Client to Server Wired(100bt)
rocco-laptop samba # iperf -u -c 192.168.1.4 -i 1
------------------------------------------------------------
Client connecting to 192.168.1.4, UDP port 5001
Sending 1470 byte datagrams
UDP buffer size:   110 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.6 port 43685 connected with 192.168.1.4 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 1.0 sec  24.0 GBytes    206 Gbits/sec
[  3]  1.0- 2.0 sec  4.00 GBytes  34.4 Gbits/sec
[  3]  2.0- 3.0 sec  4.00 GBytes  34.4 Gbits/sec
[  3]  3.0- 4.0 sec  4.00 GBytes  34.4 Gbits/sec
[  3]  4.0- 5.0 sec    128 KBytes  1.05 Mbits/sec
[  3]  5.0- 6.0 sec  8.00 GBytes  68.7 Gbits/sec
[  3]  6.0- 7.0 sec  4.00 GBytes  34.4 Gbits/sec
[  3]  7.0- 8.0 sec  4.00 GBytes  34.4 Gbits/sec
[  3]  8.0- 9.0 sec  4.00 GBytes  34.4 Gbits/sec
[  3]  9.0-10.0 sec  4.00 GBytes  34.4 Gbits/sec
[  3]  0.0-10.0 sec  60.0 GBytes  51.5 Gbits/sec
[  3] Sent 893 datagrams
[  3] WARNING: did not receive ack of last datagram after 10 tries.

---

### Post by centyx on 2009-07-07
Just thought I'd post this as someone else may find it useful to know.

An issue I've run into with Ubuntu is I've found my user account belonging to more than 16 groups ( NFS limit for group mapping ), so when I try to access a directory or file on the NFS mount that belongs to a group that's not included in the first 16 I am denied access. 

My "solution" was to remove myself from Ubuntu's administrative groups that I did not absolutely need to belong to. 

For a real solution, see this blog post by Mike Eisler:

[http://nfsworld.blogspot.com/2005/03/whats-deal-on-16-group-id-limitation.html](http://nfsworld.blogspot.com/2005/03/whats-deal-on-16-group-id-limitation.html)

---

### Post by shane2peru on 2009-07-07
ok, this was working and now I'm back to problems.  
Here is my dmseg error when trying to mount:
```

[ 3547.520404] rpcbind: server labuntu not responding, timed out
[ 3695.655724] rpcbind: server 192.168.1.100 not responding, timed out

```
I tried mounting with name, and then with ip address.  Not sure what is going on.  What is rpcbind?  I went back and re-followed this how-to: 

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

This is being real difficult.  Hopefully it is some dumb little thing I'm overlooking.  

Shane

---

### Post by revbob on 2009-07-20
Hi, first post, my problem was/is a little different from what I've read so far.

I'm taking a class and one of the things I needed to do was set up an NFS server.  I read various tutorials, HOWTOs and such and then went about setting things up.  I'm setting up my server using with Ubuntu 8.04 running as a VM under vmware.  My host is a also Ubuntu 8.04.  I'm running this all on a laptop and when I'm running wireless I can't bridge my VM to my host so I used the NAT option instead but I kept getting the following while trying to mount:

bdinan@bdinan-laptop:~$ sudo mount 172.16.84.130:/home/bdinan/Music /home/bdinan/Public
mount.nfs: access denied by server while mounting 172.16.84.130:/home/bdinan/Music

I finally connected my laptop to my LAN and bridged the VM and now it works fine.  I changed nothing else.  The obvious difference is the addressing scheme.

My host was using a 192.168.1.X address and my VM 172.16.84.130 under NAT but when I bridge it it uses a 192.168.1.X address.

Does anyone have any ideas on why this wouldn't work under NAT?

Thanks.

---

### Post by dmizer on 2009-07-21
> **revbob said:**
> Hi, first post, my problem was/is a little different from what I've read so far.

I'm taking a class and one of the things I needed to do was set up an NFS server.  I read various tutorials, HOWTOs and such and then went about setting things up.  I'm setting up my server using with Ubuntu 8.04 running as a VM under vmware.  My host is a also Ubuntu 8.04.  I'm running this all on a laptop and when I'm running wireless I can't bridge my VM to my host so I used the NAT option instead but I kept getting the following while trying to mount:

bdinan@bdinan-laptop:~$ sudo mount 172.16.84.130:/home/bdinan/Music /home/bdinan/Public
mount.nfs: access denied by server while mounting 172.16.84.130:/home/bdinan/Music

I finally connected my laptop to my LAN and bridged the VM and now it works fine.  I changed nothing else.  The obvious difference is the addressing scheme.

My host was using a 192.168.1.X address and my VM 172.16.84.130 under NAT but when I bridge it it uses a 192.168.1.X address.

Does anyone have any ideas on why this wouldn't work under NAT?

Thanks.
It works fine under Vmware NAT. I use it this way all the time. Also, unless you used the any-any script, you should have no problem bridging to wireless as well as wired. The any-any script is no longer necessary.

Please post your /etc/exports file from the virtual machine Ubuntu (you indicated that this was your server). Also provide the output of:
```
ifconfig
```
from both the virtual machine host and guest.

---

### Post by ukripper on 2009-08-05
> **malco2001 said:**
> [B] 


[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing) (for server configuration)



Above link is not working.

---

### Post by palakanit on 2009-08-05
thanks ....its very useful....

---

### Post by dmizer on 2009-08-05
> **ukripper said:**
> Above link is not working.

Thank you. I removed it.

---

### Post by PaulHuffman on 2009-08-07
The NFS share I set up is working but I'm having problems with permissions blocking exactly what I am trying to do.

One of my problems is that I know to much about Solaris administration that I always try to do things the hard way with Linux. 

What I had set up was in order to access data on the Forestry Solaris host that I don't administer, I set up a mount on the Water Solaris host that I administer in the fstab. Then I used samba to make a link from this mount on the Water host to my Windows PC so I can use the data in some PC apps. Well, the Water host has been down for a week waiting on parts. I thought maybe I can use this Ubuntu 9.04 PC here to replace the Water Solaris host in the chain.  I installed the NFS client and made the mount and can see and copy the data from the Forestry host fine. However, the way Ubuntu does these mounts, or at least the procedure described here, root owns the mount point. Therefore, I haven't been able to samba share the mount point.  Can't seem to change the ownership of the mount point with sudo chmod.  In Solaris, I commonly login as root to get this kind of thing done, but I learned that in Linux, you should avoid this. I don't need to enable the root account to do this, do I?

---

### Post by Jose Catre-Vandis on 2009-08-07
> **PaulHuffman said:**
> The NFS share I set up is working but I'm having problems with permissions blocking exactly what I am trying to do.

One of my problems is that I know to much about Solaris administration that I always try to do things the hard way with Linux. 

What I had set up was in order to access data on the Forestry Solaris host that I don't administer, I set up a mount on the Water Solaris host that I administer in the fstab. Then I used samba to make a link from this mount on the Water host to my Windows PC so I can use the data in some PC apps. Well, the Water host has been down for a week waiting on parts. I thought maybe I can use this Ubuntu 9.04 PC here to replace the Water Solaris host in the chain.  I installed the NFS client and made the mount and can see and copy the data from the Forestry host fine. However, the way Ubuntu does these mounts, or at least the procedure described here, root owns the mount point. Therefore, I haven't been able to samba share the mount point.  Can't seem to change the ownership of the mount point with sudo chmod.  In Solaris, I commonly login as root to get this kind of thing done, but I learned that in Linux, you should avoid this. I don't need to enable the root account to do this, do I?

I am confused! Are you trying to nfs share or samba share? They are very different things as I am sure you know!

If your mount points are outside of the user directory, then you will need to use root/sudo to mount these from your client, but only the intial setup will need root/sudo oon the server.

---

### Post by PaulHuffman on 2009-08-07
Thanks for spotting my post, Jose. I wasn't sure it would be noticed among the thirty pages of this thread.

Sorry to confuse you.  I know they are different.  The NFS link works. That's the one from the Solaris host Forestry to my Ubuntu PC.  I made the mount point in my home directory in Ubuntu.

It's the next step that has me stumped. I know want to make on the Ubuntu PC a samba share of the mounted directory so I can pass it on to windows PC to use the data in a windows app.  

Forestry ->NFS->Ubuntu->Samba->Samba->Windows PC.

I'm doing this because I'm not an administrator on Forestry and it only has NFS shares. Not running Samba. Up until last week I was doing this using a Solaris box that I administer and am running Samba Server, Water, in place of the Ubuntu PC.  

On the Ubuntu PC, I so far have only tried using the File Browser and right clicking on the mount point and clicking sharing properties. Any attempt to make a share this way is rebuffed because root owns the mount point. I haven't tried any samba command line stuff yet. It occurred to me that I might be able to make a symbolic link to the mount point and make a share out of that.

---

### Post by Jose Catre-Vandis on 2009-08-08
Hi Paul

No longer confused :)

Try out this howto on setting up samba. I recently used it on my ubuntu server for Windows PCs on a local network to access shares, and it works flawlessly. With samba, for me anyway, it is always about users and permissions!

[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

---

### Post by PaulHuffman on 2009-08-17
Thanks, Jose.  I didn't find what I needed in the How To link you sent me, but it might be there in the 51 pages.  

I simply took the hint from the error message the system gave me when I tried to make a share of the NFS link in the file browser. It was "'net usershare' returned error 255: net usershare add: cannot share path /home/paul/photoserver as we are restricted to only sharing directories we own.
Ask the administrator to add the line "usershare owner only = false" 
to the [global] section of the smb.conf to allow this."

As soon as I added that line in smb.conf, I was able to share the NFS mount point with my PC.

---

### Post by rmannon on 2009-08-26
I just wanted to say thanks to the original Author.  This worked great to get Amarok to use a networked computer for my music collection.  I'm almost satisfied with my setup now!

---

### Post by cinajohn on 2009-09-03
I wanted to thank the OP as well.  I am so happy to be able to use a proper linux/UNIX solution and not a windows emulating 'work-around'.  

Worked perfectly!

---

### Post by NTolerance on 2009-09-03
> **arrrghhh said:**
> just use the bind function with mount.  it's how i get users to view other disks via ftp.  works much better than symlinks (in cases such as this...)

A year later I have finally tested this.  I used the bind option in the server's fstab file.  Still no luck.  On the client the directories are empty.

---

### Post by yens on 2009-09-15
Hello,

It's a very nice thread but I got read/write issue with the nfs shares.
We have a network organized as follows. Ubuntu server 8.04 and 3 client machines running Windows and myself running Ubuntu 9.04. We all use samba in order to mount the server directories. At the moment I'm trying to use nfs for the Ubuntu 9.04 client.
So I installed all the necessary packages on the server and on the client. Everything looks fine, the only issue is that I cannot mount the server directories with write access though I have write access via samba.

On the server there are two directories I'd like to share.
*/home/jens* (uid 1001, gid 1001, owner user jens)
*/home/samba/shares/public* (uid 114, gid 126, owner user ebox) - in this directory are the public folders of all users.

On the client machine there is user *jens* with uid 1000, gid 1000.
Obviously I cannot much the same uid/gid on the cliant and on the server for all shared directories.
After some digging in the forums I found the information that I shall use *anonuid* and *anongid* functions.

This is last variant I put in the /etc/exports on the server. (actually I tried many different combination)

[I]# Export home dir for jens
/home/jens 192.168.2.11(rw,all_squash,async,no_subtree_check,anonuid=1000,anongid=1000)
# Export the public share to jens
/home/samba/shares/public 192.168.2.11(rw,all_squash,anonuid=1000,anongid=1000)[/I]

The 192.168.2.11 is the static IP of the client. The IP of the server is 192.168.2.10.
On the client I execute
*sudo mount 192.168.2.10:/home/jens/ /home/jens/mnt/homedir*
Unfortunately I cannot mount the directories with write permission but read only.

The only way I found out is to change the uid and gid of the client to 1001 but then I can mount only the home folder with write permission.
I think there shall be a way to share directory with full permissions to all users (like public directory) but I cannot find a way to do it.
Could someone help please!

---

### Post by shane2peru on 2009-09-15
Does anyone know how to bind nfs server to specific ports?  I know they use 2049 and 111 however there are other ports involved.  It actually uses others.  If you run rpcinfo -p it will show you all the ports the nfslock and mountd are the ones that change on a reboot, and they are the ones I want to nail down so I can allow a iptables firewall to give access to nfs mounts.  Any ideas or thoughts would be appreciated.  I found this:  [http://ubuntuforums.org/archive/index.php/t-825094.html](http://ubuntuforums.org/archive/index.php/t-825094.html)  old link, but it didn't work for me.  Any ideas, or thoughts would be appreciated.  Thanks.

Shane

---

### Post by shane2peru on 2009-09-15
> **yens said:**
> Hello,

It's a very nice thread but I got read/write issue with the nfs shares.
We have a network organized as follows. Ubuntu server 8.04 and 3 client machines running Windows and myself running Ubuntu 9.04. We all use samba in order to mount the server directories. At the moment I'm trying to use nfs for the Ubuntu 9.04 client.
So I installed all the necessary packages on the server and on the client. Everything looks fine, the only issue is that I cannot mount the server directories with write access though I have write access via samba.

On the server there are two directories I'd like to share.
*/home/jens* (uid 1001, gid 1001, owner user jens)
*/home/samba/shares/public* (uid 114, gid 126, owner user ebox) - in this directory are the public folders of all users.

On the client machine there is user *jens* with uid 1000, gid 1000.
Obviously I cannot much the same uid/gid on the cliant and on the server for all shared directories.
After some digging in the forums I found the information that I shall use *anonuid* and *anongid* functions.

This is last variant I put in the /etc/exports on the server. (actually I tried many different combination)

[I]# Export home dir for jens
/home/jens 192.168.2.11(rw,all_squash,async,no_subtree_check,anonuid=1000,anongid=1000)
# Export the public share to jens
/home/samba/shares/public 192.168.2.11(rw,all_squash,anonuid=1000,anongid=1000)[/I]

The 192.168.2.11 is the static IP of the client. The IP of the server is 192.168.2.10.
On the client I execute
*sudo mount 192.168.2.10:/home/jens/ /home/jens/mnt/homedir*
Unfortunately I cannot mount the directories with write permission but read only.

The only way I found out is to change the uid and gid of the client to 1001 but then I can mount only the home folder with write permission.
I think there shall be a way to share directory with full permissions to all users (like public directory) but I cannot find a way to do it.
Could someone help please!
Try this, this is what I use:
[code]
(rw,no_subtree_check,no_root_squash,sync)  This seems to give me read/write access.  Try those options instead.

Shane

---

### Post by yens on 2009-09-16
> **shane2peru said:**
> Try this, this is what I use:
[code]
(rw,no_subtree_check,no_root_squash,sync)  This seems to give me read/write access.  Try those options instead.

Shane

Shane, thank you for the answer.
Unfortunately nothing changed. I put exactly the same options, even I tried with anonuid/anongid and without them.
I've noticed some odd thing. The folder where I mount on the client is owned by the user jens. After I mount there, the ownership changes to some strange user 1001. This is actually the uid of the user on the server.
Could it be something with the folder permissions?

---

### Post by shane2peru on 2009-09-16
> **yens said:**
> Shane, thank you for the answer.
Unfortunately nothing changed. I put exactly the same options, even I tried with anonuid/anongid and without them.
I've noticed some odd thing. The folder where I mount on the client is owned by the user jens. After I mount there, the ownership changes to some strange user 1001. This is actually the uid of the user on the server.
Could it be something with the folder permissions?

Oh, perhaps I should have mentioned after changing the options you need to ```
exportfs -a
```  and ```
sudo /etc/init.d/nfs-kernel-server restart && sudo /etc/init.d/portmap restart 
```  and that should run fine.  After editing those files you always have to do that.  I don't know if you know that or not, but thought it worth mentioning.  restarting them may not be necessary, but certainly can't hurt either.  It seems that mounting it is changing the permissions and owners, I don't know, but I think it has to do with your anonuid/anongid.  I don't have any problems with mine, and have mounted them with Ubuntu 8.04, 9.04, Suse11.1, and PCLinuxOS.  

Shane

---

### Post by shane2peru on 2009-09-16
> **shane2peru said:**
> Does anyone know how to bind nfs server to specific ports?  I know they use 2049 and 111 however there are other ports involved.  It actually uses others.  If you run rpcinfo -p it will show you all the ports the nfslock and mountd are the ones that change on a reboot, and they are the ones I want to nail down so I can allow a iptables firewall to give access to nfs mounts.  Any ideas or thoughts would be appreciated.  I found this:  [http://ubuntuforums.org/archive/index.php/t-825094.html](http://ubuntuforums.org/archive/index.php/t-825094.html)  old link, but it didn't work for me.  Any ideas, or thoughts would be appreciated.  Thanks.

Shane

I figured this out it is here:

[https://wiki.ubuntu.com/How%20to%20get%20NFS%20working%20with%20Ubuntu-CE-Firewall](https://wiki.ubuntu.com/How%20to%20get%20NFS%20working%20with%20Ubuntu-CE-Firewall)

Shane

---

### Post by yens on 2009-09-17
> **shane2peru said:**
>  It seems that mounting it is changing the permissions and owners, 
This was exactly the point. On the server I just did
```

sudo chmod a+w -R /home/jens
sudo chmod a+w -R /home/samba/shares/

```
Now I mount the folders with write permission and anonuid/anongid is irrelevant.
Actually when you mount, you change the permission as on the server and when you have rwxr--r-- you become naturally only read access.
The problem now is that my home folder on the server is writable by everyone. I think the better solution here would be to give write access only to the public folder and to change the uid/gid on the client to match those on the server in respect to the home folder.
So, finally I can migrate to NFS.
Thank you Shane and thanks to everyone in this nice nfs thread.

---

### Post by yens on 2009-09-17
Btw, I put this into my /etc/fstab

```
# nfs variant
192.168.2.10:/home/jens /home/jens/mnt/homedir nfs rw	0	0
192.168.2.10:/home/samba/shares/public /home/jens/mnt/publicdir nfs rw  0    0 
```

Now all shares mount at the start-up and the ownership of all mounted directories is OK, only the group differs.

---

### Post by shane2peru on 2009-09-17
> **yens said:**
> This was exactly the point. On the server I just did
```

sudo chmod a+w -R /home/jens
sudo chmod a+w -R /home/samba/shares/

```
Now I mount the folders with write permission and anonuid/anongid is irrelevant.
Actually when you mount, you change the permission as on the server and when you have rwxr--r-- you become naturally only read access.
The problem now is that my home folder on the server is writable by everyone. I think the better solution here would be to give write access only to the public folder and to change the uid/gid on the client to match those on the server in respect to the home folder.
So, finally I can migrate to NFS.
Thank you Shane and thanks to everyone in this nice nfs thread.

Well glad you got it sorted out.  I'm still not sure I understand everything, but that is ok, if you got it working, and you understand that is all that matters. :)  

Shane

---

### Post by scrooge_74 on 2009-09-24
I got a weird situation here:

server Hardy 8.04

exports config: 

/mnt/fotos 192.168.2.0/255.255.255.0(rw,sync,no_root_squash,no_subtree_check)

From Lenny laptop I can mount and write to folder, but from Hardy laptops I can only mount and read files.

Gnome in Debian even creates links in Nautilus for nfs folders and if you click on them it will mount them. Gnome in Hardy wont do such thing.

Any toughts?

Thanks


EDIT: I know part of my problem is with users and their id, how do I fix this?

---

### Post by karlson on 2009-09-24
> **scrooge_74 said:**
> I got a weird situation here:

server Hardy 8.04

exports config: 

/mnt/fotos 192.168.2.0/255.255.255.0(rw,sync,no_root_squash,no_subtree_check)


Any toughts?

Thanks


EDIT: I know part of my problem is with users and their id, how do I fix this?

Many ways:

Simplest one:  chmod a+rwx /mnt/fotos  Many problems with this one:

Just as simple, but better:

create a group for your fotos users and put the users accessing the /mnt/fotos in there and chmod g+rwx /mnt/fotos.  If there are a lot of users that can access this mount the management could become a problem.

The third method would be file system ACLs, but that is a lot more difficult to maintain then a group.

---

### Post by scrooge_74 on 2009-09-24
I decided since it is only two laptops and the same 3 users in them I just changed the uid of each of them to match the ones in the server and problem solved

---

### Post by yens on 2009-09-26
This seems to be a long thread.
I run into another issue and found a solution for it. I hope this could be helpful to someone with the same problem.
I make weekly a rsync backup of my local mail evolution folders on the server.
The samba version was:
```
rsync -avz --delete --progress /home/jens/.evolution/mail/local jens@192.168.2.10:/home/jens/mailbackup
```

I've adapted this for nfs like this:
```
rsync -avz --delete --progress /home/jens/.evolution/mail/local /home/jens/mnt/personal/mailbackup
```
This put me into trouble because when I run the command the computer hangs and the processor is on full power and the synchronization was very very long process. The solution was to change this to:
```
rsync -avz --delete --progress /home/jens/.evolution/mail/local 192.168.2.10:/home/jens/mailbackup
```

As you see the difference is that the the last variant makes synchronization directly on the server and everything goes fine. The last variant requires also your user password on the server but this is not an issue for me, as I have my computer operational during the synchronization.

---

### Post by mbaggia on 2009-10-01
> **malco2001 said:**
> 
Here are some quick examples of what you could add to your /etc/exports

For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255

[LIST]
[*]/files 192.168.1.0/24(rw,no_root_squash,async)
[/LIST]

Or for Read Only from a single machine

[LIST]
[*]/files 192.168.1.2 (ro,async)
[/LIST]



Thank you so much for this how-to. It works like a dream! However, could I ask that you edit the line "/files 192.168.1.2 (ro,async)" to remove the space between the IP address and the options list? When there is a space in that line of config, I get an error message saying that no options had been set.

It would also add clarity if the meaning of "async" and "sync" were made clear. I modified the line to "sync", and now whatever changes I make on either machine are reflected on the other one.

Once again, thanks for taking the time to write this - it's incredibly easy to follow, and works beautifully! :)

---

### Post by scrooge_74 on 2009-10-01
> **yens said:**
> This seems to be a long thread.
I run into another issue and found a solution for it. I hope this could be helpful to someone with the same problem.
I make weekly a rsync backup of my local mail evolution folders on the server.
The samba version was:
```
rsync -avz --delete --progress /home/jens/.evolution/mail/local jens@192.168.2.10:/home/jens/mailbackup
```

I've adapted this for nfs like this:
```
rsync -avz --delete --progress /home/jens/.evolution/mail/local /home/jens/mnt/personal/mailbackup
```
This put me into trouble because when I run the command the computer hangs and the processor is on full power and the synchronization was very very long process. The solution was to change this to:
```
rsync -avz --delete --progress /home/jens/.evolution/mail/local 192.168.2.10:/home/jens/mailbackup
```

As you see the difference is that the the last variant makes synchronization directly on the server and everything goes fine. The last variant requires also your user password on the server but this is not an issue for me, as I have my computer operational during the synchronization.

Well, I just have a NFS mounted folder from my server, and then I just tell evolution to do a backup into that folder while I go watch tv

---

### Post by yens on 2009-10-01
> **scrooge_74 said:**
> Well, I just have a NFS mounted folder from my server, and then I just tell evolution to do a backup into that folder while I go watch tv

OK, this is also another possibility for Evolution backup.
What I actually do for my backups:
I have an executable file with 5 similar rsync lines for different directories, this line for evolution is just one of them.
When you make this file to be executed regularly (e.g. via crontab, command line or desktop icon) you just get a nice automated solution to do all your synchronizations, resp. backups only with one action.

---

### Post by scrooge_74 on 2009-10-01
Yup I know but since this is a laptop and Im not sure if and when I will backup I just do it manually :D

---

### Post by majdi on 2009-10-26
> 
Or for Read Only from a single machine

    * /files 192.168.1.2 (ro,async)


What if the users are on a DHCP network, how would you configure this.

---

### Post by Jose Catre-Vandis on 2009-10-26
> What if the users are on a DHCP network, how would you configure this.
Configure as for all users to access, and control via users logins

---

### Post by majdi on 2009-10-26
Hi Jose,

So for all to access I would do this;

> 
For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255

    * /files 192.168.1.0/24(rw,no_root_squash,async)


But how would you configure the user login, and if the user must login with a user name and password, dose this mean I wouldn't be able to configure an auto mount on boot for the client?

---

### Post by yens on 2009-10-27
> But how would you configure the user login, and if the user must login with a user name and password, dose this mean I wouldn't be able to configure an auto mount on boot for the client?

As from my experience you can control via users and login if the server runs samba ans resp. you use samba on the client to access the share.
Regarding NFS you can control the access with the folder permissions of the exported directory and uid/gid since you don't have static IPs.
For this reason the automout shouldn't be a problem.

---

### Post by Jose Catre-Vandis on 2009-10-27
> **majdi said:**
> Hi Jose,

So for all to access I would do this;



But how would you configure the user login, and if the user must login with a user name and password, dose this mean I wouldn't be able to configure an auto mount on boot for the client?


This is the way I do it:

For each user on the client machines that you want to give access, create equal user accounts for each user on the server, this I believe may include the UID number. So although you are serving the nfs shares to the whole LAN, only those users should have access.

Don't confuse this with samba, which is a different way of sharing, but you may like to look at how to do this with samba. A great tut can be found [here]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba")

---

### Post by majdi on 2009-10-27
Thanks again Jose,

I read your [HOWTO: Mount NFS shares from Ubuntu/Linux in Windows XP]("http://ubuntuforums.org/showthread.php?t=310168"). And if I can do away with Samba then that would be great. I would rather maintain one share configuration than two.

The only reason I was considering Samba was that I thought I would need it because that would be the only way our windows users will access shared folders on a linux server.

Now, if windows clients can access shared folders using NFS and this has proved to work without problems then why not just use NFS and forget about Samba?

---

### Post by Jose Catre-Vandis on 2009-10-27
I couldn't get NFS to work at all on Windows 7 Ultimate (RC), and found samba (using the howto I pointed to) as a much easier solution for the windows machines on my LAN, but I tend to use NFS for file maintenance on my media server, and for accessing media via my GeexBox Media Center setup. Setting up NFS for windows machines is a pita, but it was a mountain I choose to climb :)

---

### Post by majdi on 2009-10-28
Jose, from your experience would you suggest that I just run both Samba for the windows users and NFS for the linux users on one server. If this runs without problems, because it is a production environment, then I will go with this setup.

---

### Post by PaRem on 2009-10-29
Hi folks!

I'm a newbie on Ubuntu, but I'm learning very fast and I'm really enjoying Ubuntu for a month now! Don't wanna go back to Windows (I won't!) I got my NFS server running and my HDX-1000 (like Popcorn Hour) does recognize my NFS server (Ubuntu), HD streaming is going well. I did sort a lot of things out like mounting and so on. Now I'm still sorting out how I can copy files to my HDX-1000 through NFS. Now I'm using FTP, but I think NFS is faster and I like the way how my HDX mount like if it's a internal harddisk.

Here's my problem:
How do I change the permissions in Ubuntu so I can read & write to my HDX-1000 through NFS? I did mount everything, but there are still locks on the maps. So writing isn't possible but reading/streaming is!

Can someone help me? Thanks in advance!

Paul.

---

### Post by yens on 2009-10-30
> **PaRem said:**
> Hi folks!

I'm a newbie on Ubuntu, but I'm learning very fast and I'm really enjoying Ubuntu for a month now! Don't wanna go back to Windows (I won't!) I got my NFS server running and my HDX-1000 (like Popcorn Hour) does recognize my NFS server (Ubuntu), HD streaming is going well. I did sort a lot of things out like mounting and so on. Now I'm still sorting out how I can copy files to my HDX-1000 through NFS. Now I'm using FTP, but I think NFS is faster and I like the way how my HDX mount like if it's a internal harddisk.

Here's my problem:
How do I change the permissions in Ubuntu so I can read & write to my HDX-1000 through NFS? I did mount everything, but there are still locks on the maps. So writing isn't possible but reading/streaming is!

Can someone help me? Thanks in advance!

Paul.

I suppose you should check the permissions of the folder that you export via NFS. In principal if uid/gid on the client and the server differ there should be write permission to others.

---

### Post by PaRem on 2009-10-30
> **yens said:**
> I suppose you should check the permissions of the folder that you export via NFS. In principal if uid/gid on the client and the server differ there should be write permission to others.

Thanks for your reply yens.

My line in /etc/exports:
/media/94b98ae1-f480-4d74-b1ee-e54b05574abe 192.168.1.22(rw,no_subtree_check,no_root_squash,sync)

Somebody who can help me? I got more information. When I go in my NFS-server, it says under permissions: owner 1001 - user #1001

It's so nice to see my HDX as internal drive in Ubuntu, but it's sad I can't write anything.

---

### Post by Jose Catre-Vandis on 2009-10-31
> **majdi said:**
> Jose, from your experience would you suggest that I just run both Samba for the windows users and NFS for the linux users on one server. If this runs without problems, because it is a production environment, then I will go with this setup.

Hi Madji

As I said before I use samba for Windows PCs to share from the server, and NFS for "Me" and other linux devices I have running, but this is in a home environment. Suggest you do some research into security issues for both samba and nfs before rolling out in a production environment. This the key key issue, how to protect/control the data that is being served, and who can do what with it!

---

### Post by yens on 2009-11-02
> **PaRem said:**
> Thanks for your reply yens.

My line in /etc/exports:
/media/94b98ae1-f480-4d74-b1ee-e54b05574abe 192.168.1.22(rw,no_subtree_check,no_root_squash,sync)

Somebody who can help me? I got more information. When I go in my NFS-server, it says under permissions: owner 1001 - user #1001

It's so nice to see my HDX as internal drive in Ubuntu, but it's sad I can't write anything.

Under permission I mean the output from ```
ls -l /*foldername*
```
I think that you get the output > permissions: owner 1001 - user #1001 from your client machine or I'm wrong?

---

### Post by VastOne on 2009-11-07
I have used this guide to set up and get running NFS on both the server and client.

Communication and connections are there.

From the client, I can access the mount. I can create folders and delete folders with no issues. 

I cannot copy files from the client to the server and only get this error


Error opening file '/files/Test Data/whatever file .wma': Operation not permitted

On the server this creates a zero byte file called whatever file.wma which I can then delete from the client side. This indicates I have full permissions from the client.

my fstab is the following 

192.168.1.102:/media/HP /files nfs   rw   0   0

Why then can I not copy files from the client to the server?

---

### Post by Jose Catre-Vandis on 2009-11-08
> **VastOne said:**
> I have used this guide to set up and get running NFS on both the server and client.

Communication and connections are there.

From the client, I can access the mount. I can create folders and delete folders with no issues. 

I cannot copy files from the client to the server and only get this error


Error opening file '/files/Test Data/whatever file .wma': Operation not permitted

On the server this creates a zero byte file called whatever file.wma which I can then delete from the client side. This indicates I have full permissions from the client.

my fstab is the following 

192.168.1.102:/media/HP /files nfs   rw   0   0

Why then can I not copy files from the client to the server?

This does look like a permissions issue of some kind. A few questions for clarification:

1. I assume your issue arises when you are **on your client** and trying to copy files **to** the server?
2. When on the client: Can you copy files from the server to the client OK?
3. When you have your nfs share mounted, have a look at the permissions for files and folders...
```
cd /nfs/share 
ls -al
```
What access do you have to files and folders (rwx?) ?
Who owns the files and folders? <- this is most possible problem?
4. What permissions are there on your client files you are trying to copy?

---

### Post by VastOne on 2009-11-08
> **Jose Catre-Vandis said:**
> This does look like a permissions issue of some kind. A few questions for clarification:

1. I assume your issue arises when you are **on your client** and trying to copy files **to** the server?
2. When on the client: Can you copy files from the server to the client OK?
3. When you have your nfs share mounted, have a look at the permissions for files and folders...
```
cd /nfs/share 
ls -al
```
What access do you have to files and folders (rwx?) ?
Who owns the files and folders? <- this is most possible problem?
4. What permissions are there on your client files you are trying to copy?

1: Yes
2: Yes, no problems from server to client

3: cd /nfs/share

bash: cd: /nfs/share: No such file or directory

4: Root - From the client I check properties/permissions on the server and it is root

5: Permissions on the client are for my logged in user account vastone-VastOne

I have setup NFS several times since hardy following this same guide and have never run into this issue. This seems a Karmic issue, as clearly NFS is doing its job on both the client and server side

---

### Post by Jose Catre-Vandis on 2009-11-08
Did you install a karmic server and karmic client?

I am running a jaunty server with karmic clients with no problems.

All files on the server are owned by "me", in that I have the same user on the server as on the client, and I have all folders 777. This might be a good place to start and work back from if you need improved security.

In my fstab I use, for example, the line:
> 10.10.10.70:/media/music        /media/music            nfs rsize=8192,wsize=8192,timeo=14,intr,bg

---

### Post by VastOne on 2009-11-08
> **Jose Catre-Vandis said:**
> Did you install a karmic server and karmic client?

I am running a jaunty server with karmic clients with no problems.

All files on the server are owned by "me", in that I have the same user on the server as on the client, and I have all folders 777. This might be a good place to start and work back from if you need improved security.

In my fstab I use, for example, the line:

Karmic server and karmic client

I am the same user on both client and server

I will resolve by changing permissions at the server level

Thanks

---

### Post by aridus on 2009-12-05
Many thanks for this guide. I am trying to use it to access a Western Digital MyBookWorld, which is a network drive plugged into my router/modem. The web interface of the drive allows me to enable nfs, which I have done, and there are two notes in the config:

# No access allowed for NFS if the IP allowed list is empty.
# Mount point for NFS share is /nfs/SHARENAME, Ex. /nfs/Public

So I have added 192.168.1.3 (which I obtained from ifconfig in the eth0 section - I presume this is my Kubuntu laptop) for the first. For the second, as I have created a folder on the drive called FishNet, I presume that the paths is /nfs/FishNet

I became confused in the first sections in the HOWTO: NFS Server/Client on the first page but now I think that the Install NFS Server Support section refers, in my case, to the network drive and so I don't need to do anything, having enabled nfs - is this correct?

Moving to the Install NFS client support section, I have run sudo apt-get install portmap nfs-common, and created the folder FishNet on my laptop in the path /media/FishNet

My understanding is that if I now type 

sudo mount 192.168.1.2:/nfs/FishNet /media/FishNet

in a terminal all should be well. However, I receive the message 

mount.nfs: access denied by server while mounting 192.168.1.2:/nfs/FishNet

Could anybody more knowledgeable than me suggest where I may have erred?

With grateful thanks!

---

### Post by aridus on 2009-12-07
Responding to my own post above, I just want to note, in case it is of use to anybody else, that I resolved this problem by using this line

192.168.1.2:/nfs/FishNet /media/FishNet nfs rw,user 0 0

in /etc/fstab, and now have read and write access on the folder FishNet created on the network drive. Beware, if you do this, that on the WD MyBook World Edition you need to enable nfs, then enable nfs on the drive created, and then enable write access on the drive created. All of these things are in different places on the web interface and you have to dig around to find them (and they are not all mentioned in the manual...). 

There are many options available for nfs and I have no idea what most of them mean - but I have divined that I do need rw and user. Can anybody comment on appropriate options? With thanks!

---

### Post by ^_Pepe_^ on 2009-12-18
Hi all,

I'm using NFS (using this guide) and I'm completely satisfied. 

But since 9.10 (not completely sure about it) I have been having some kind of weird problems.

> From Nutilus, some folders suddenly dissapear.
> From Terminal, ls command says: "Stale NFS file handle", and something about "obsolete infomation". 

This behaviour is occasional, but if I use NFS system hardly (streming, big copy processes, and son), finally occurs.

I've googled about it, and I've found poor information

[http://www.cyberciti.biz/tips/nfs-stale-file-handle-error-and-solution.html](http://www.cyberciti.biz/tips/nfs-stale-file-handle-error-and-solution.html)

and for skilled people.

Any suggestion to start with?

Thanks in advance.

---

### Post by ^_Pepe_^ on 2009-12-18
I forgot to mention that

```

sudo umount /myshare -f
sudo mount -a

```

Solves my problem, but only for a while...

Thanks

---

### Post by dmizer on 2009-12-18
> **^_Pepe_^ said:**
> Hi all,

I'm using NFS (using this guide) and I'm completely satisfied. 

But since 9.10 (not completely sure about it) I have been having some kind of weird problems.

> From Nutilus, some folders suddenly dissapear.
> From Terminal, ls command says: "Stale NFS file handle", and something about "obsolete infomation". 

This behaviour is occasional, but if I use NFS system hardly (streming, big copy processes, and son), finally occurs.

I've googled about it, and I've found poor information

[http://www.cyberciti.biz/tips/nfs-stale-file-handle-error-and-solution.html](http://www.cyberciti.biz/tips/nfs-stale-file-handle-error-and-solution.html)

and for skilled people.

Any suggestion to start with?

Thanks in advance.

Are there any clues in dmesg or in any of the log files in /var/log on either the client or the server?

Post your current /etc/exports and /etc/fstab (I assume you're auto mounting via /etc/fstab) configurations.

---

### Post by ^_Pepe_^ on 2009-12-18
This is my fstab on client

```
192.168.1.15:/media/TERA                  /media/TERA     nfs rw                0       0
```

/etc/exports on server

```
/media/TERA 192.168.1.18(rw,async,no_subtree_check)
```

...1.18 is client, and ...1.15 is server. Fixed IPs


After 1 minute, 

ls /media/TERA, throws.

ls: no se puede acceder a /media/TERA/System Volume Information: Descriptor de archivo NFS obsoleto

(Obsolete file description)... for each folder...)


Regards and thanks for helping

---

### Post by ^_Pepe_^ on 2009-12-18
I could only find this code, related to NFS, in kern.log

```
Dec  4 18:09:12 MOE kernel: [    8.898473] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Dec  4 18:09:12 MOE kernel: [    8.898803] NFSD: starting 90-second grace period
```

Repeated several times...

I think I have NFSv3.

---

### Post by ^_Pepe_^ on 2009-12-18
[INDENT][COLOR="Silver"]Could this be relevant?

```
Dec 18 18:18:10 MOE portmap: Cannot open /var/run/portmap.pid: Permission denied
```[/COLOR][/INDENT]


Please, forget this comment. I tried to execute portmap command from terminal...

---

### Post by ^_Pepe_^ on 2009-12-18
```

pepe@MOE:/media/TERA$ ls -l
ls: no se puede acceder a **06.TopGear**: Descriptor de archivo NFS obsoleto
total 7693996
drwxrwxrwx 1 pepe pepe       4096 2009-11-14 18:33 000.Temp
drwxrwxrwx 1 pepe pepe      57344 2009-12-16 09:28 00.Dibus de Ángel
drwxrwxrwx 1 pepe pepe      12288 2009-11-20 00:57 02.Software
drwxrwxrwx 1 pepe pepe      32768 2009-10-15 23:11 03b.Música Tagged
drwxrwxrwx 1 pepe pepe      49152 2009-10-04 15:57 03.Música
drwxrwxrwx 1 pepe pepe       4096 2009-12-13 08:58 04.Mis Pelis
drwxrwxrwx 1 pepe pepe      77824 2009-08-13 17:52 05.Libros
**d????????? ? ?    ?             ?                ? 06.TopGear**
drwxrwxrwx 1 pepe pepe       8192 2009-12-18 17:39 09.Escáner


```

Depending on the case, some folders are affected, but not all...

Regards

---

### Post by dmizer on 2009-12-19
Looks like you really need the timeo option:
```
       timeo=n        The time (in tenths of a second) the  NFS  client  waits
                      for a response before it retries an NFS request. If this
                      option is not specified, requests are retried  every  60
                      seconds  for NFS over TCP.  The NFS client does not per&#8208;
                      form any kind of timeout backoff for NFS over TCP.
```

Also, I suggest you use the options listed in the howto.

For your /etc/exports:
```
/media/TERA 192.168.1.18(rw,no_root_squash,async,no_subtree_check)
```
Don't forget to run sudo exportfs -a and restart nfs-kernel-server after making changes to /etc/exports.
And for your /etc/fstab
```
192.168.1.15:/media/TERA                  /media/TERA     nfs rsize=8192,wsize=8192,timeo=14,intr
```
You do not need the 5th or 6th fields (the two zeros at the end) because nfs mounts are not local file systems.

Try that configuration and see if it helps.

Edit:
Not too sure how to help you with your character encoding problem. Are you also hosting those shares over Samba to Windows clients?

---

### Post by th081 on 2009-12-19
Hello

I have spent a long time trying to get nfs to work properly i have tried following the instructions but am coming stuck, on my desktop (ip 192.168.1.100) i have set up files to share my etc/exports reads as below:

/media/80A0DF4E 192.168.1.0/24(rw)

80A0DF4E is a drive in my desktop.

I have restarted by typing in sudo /etc/init/nfs-kernel-server restart

then i have typed in sudo exportfs -a -v the result is 

exporting 192.168.1.0/24:/media/80A0DF4E

I think i have successfully set up the server side of it ??


No when i go into my laptop i can ping 192.168.1.100

My laptop hard drive is partitioned into a number of different areas one of those areas is called "PROJECTS"

I have tried to create a folder under projects called serverhome to which the desktop drive will be mounted but i cannot create the file its saying no such file exists?

what do i type in to create the file, when i look under Places under the computer icon the Projects drive is listed (incidentally when i first boot up the pc a try to open the projects drive it  always asks me for a password not sure if that is relevant).

If you can provide any assistance it would be very helpful, also what do i have type in to mount the drive onto the folder there is a folder on the drive called Data (can i use that instead (i created it manually)

Thanks in advance,

---

### Post by ^_Pepe_^ on 2009-12-20
¡¡¡Solved!!!

Following dmizer instructions, now, it works flawlesssly. Even moving large files is not a problem.

Thanks once more to Dmizer (I'm a supporter of his/her main post for CIFS mount), and, obviously, to the post author, marco2001.

Regards.

> **dmizer said:**
> Looks like you really need the timeo option:
```
       timeo=n        The time (in tenths of a second) the  NFS  client  waits
                      for a response before it retries an NFS request. If this
                      option is not specified, requests are retried  every  60
                      seconds  for NFS over TCP.  The NFS client does not per&#8208;
                      form any kind of timeout backoff for NFS over TCP.
```

Also, I suggest you use the options listed in the howto.

For your /etc/exports:
```
/media/TERA 192.168.1.18(rw,no_root_squash,async,no_subtree_check)
```
Don't forget to run sudo exportfs -a and restart nfs-kernel-server after making changes to /etc/exports.
And for your /etc/fstab
```
192.168.1.15:/media/TERA                  /media/TERA     nfs rsize=8192,wsize=8192,timeo=14,intr
```
You do not need the 5th or 6th fields (the two zeros at the end) because nfs mounts are not local file systems.

Try that configuration and see if it helps.

Edit:
Not too sure how to help you with your character encoding problem. Are you also hosting those shares over Samba to Windows clients?

---

### Post by AlexanderDGreat on 2009-12-21
Worked great for Ubuntu 9.04

Though I need to make sure to /etc/hosts.allow - to open necessary ports on server-side.

portmap:ALL
mountd:ALL

---

### Post by ^_Pepe_^ on 2009-12-21
Hi again!

I'm afraid I've been to fast...

This is my current mount state,...

:confused:


```
ls: no se puede acceder a 05.Libros: Descriptor de archivo NFS obsoleto
ls: no se puede acceder a Mis Documentos: Descriptor de archivo NFS obsoleto
ls: no se puede acceder a 000.Temp: Descriptor de archivo NFS obsoleto
ls: no se puede acceder a 02.Software: Descriptor de archivo NFS obsoleto
ls: no se puede acceder a 03.Música: Descriptor de archivo NFS obsoleto
ls: no se puede acceder a 09.Escáner: Descriptor de archivo NFS obsoleto
ls: no se puede acceder a 10.HOUSE S06: Descriptor de archivo NFS obsoleto
ls: no se puede acceder a 11.Grey s06: Descriptor de archivo NFS obsoleto
ls: no se puede acceder a 12.Mentalista S01: Descriptor de archivo NFS obsoleto
ls: no se puede acceder a 14.JDownload: Descriptor de archivo NFS obsoleto
ls: no se puede acceder a 15.Cocina: Descriptor de archivo NFS obsoleto
ls: no se puede acceder a 16.Roma: Descriptor de archivo NFS obsoleto
ls: no se puede acceder a 20.MoTeC: Descriptor de archivo NFS obsoleto
ls: no se puede acceder a 31.Imágenes_Ligeras: Descriptor de archivo NFS obsoleto
ls: no se puede acceder a MarcoDigital: Descriptor de archivo NFS obsoleto
ls: no se puede acceder a Mis archivos recibidos: Descriptor de archivo NFS obsoleto
ls: no se puede acceder a System Volume Information: Descriptor de archivo NFS obsoleto
total 7693532
d????????? ? ?    ?             ?                ? 000.Temp
drwxrwxrwx 1 pepe pepe      57344 2009-12-16 09:28 00.Dibus de Ángel
d????????? ? ?    ?             ?                ? 02.Software
drwxrwxrwx 1 pepe pepe      32768 2009-12-19 18:02 03b.Música Tagged
d????????? ? ?    ?             ?                ? 03.Música
drwxrwxrwx 1 pepe pepe       4096 2009-12-13 08:58 04.Mis Pelis
d????????? ? ?    ?             ?                ? 05.Libros
drwxrwxrwx 1 pepe pepe       4096 2009-12-11 15:24 06.TopGear
d????????? ? ?    ?             ?                ? 09.Escáner
d????????? ? ?    ?             ?                ? 10.HOUSE S06
d????????? ? ?    ?             ?                ? 11.Grey s06
d????????? ? ?    ?             ?                ? 12.Mentalista S01
drwxrwxrwx 1 pepe pepe      16384 2009-12-13 07:46 13.Descargas
d????????? ? ?    ?             ?                ? 14.JDownload
d????????? ? ?    ?             ?                ? 15.Cocina
d????????? ? ?    ?             ?                ? 16.Roma
-rwxrwxrwx 1 pepe pepe 4307124224 2009-12-03 19:41 202_Colin McRae DiRT 2_DVD1.iso
-rwxrwxrwx 1 pepe pepe 3039232000 2009-12-03 19:44 202_Colin McRae DiRT 2_DVD2.iso
d????????? ? ?    ?             ?                ? 20.MoTeC
drwxrwxrwx 1 pepe pepe       8192 2009-12-06 23:39 30.Imágenes
d????????? ? ?    ?             ?                ? 31.Imágenes_Ligeras
drwxrwxrwx 1 pepe pepe          0 2009-12-17 14:46 99.Backup
-rwxrwxrwx 1 pepe pepe  531628032 2009-07-05 13:35 ALADDIN2.iso
-rwxrwxrwx 1 pepe pepe      65838 2009-07-05 13:30 ALADDIN.nri
d????????? ? ?    ?             ?                ? MarcoDigital
d????????? ? ?    ?             ?                ? Mis archivos recibidos
d????????? ? ?    ?             ?                ? Mis Documentos
d????????? ? ?    ?             ?                ? System Volume Information

```

---

### Post by AlexanderDGreat on 2009-12-21
What's the problem?

---

### Post by ^_Pepe_^ on 2009-12-22
> **AlexanderDGreat said:**
> What's the problem?

Well, in my case, after several minutes and/or large file transfer, my Nautilus shows NOTHING in /my_NFS_mount and ls -l of /my_NFS_mount says information above.

I have to umount and remount to keep it valid. 

I also tried the fsid=3 option commented by someone somewhere, but no results.

Regards

---

### Post by dmizer on 2009-12-22
> **^_Pepe_^ said:**
> Well, in my case, after several minutes and/or large file transfer, my Nautilus shows NOTHING in /my_NFS_mount and ls -l of /my_NFS_mount says information above.

I have to umount and remount to keep it valid. 

I also tried the fsid=3 option commented by someone somewhere, but no results.

Regards

I do not know if I asked this before or not, but are you connecting via wireless?

---

### Post by ^_Pepe_^ on 2009-12-22
Yes! 

0. Client is 9.10 and Wireless connected.

1. My wife Medion Akoya Mini E1210 with 9.04 has the same behaviour. Good for Karmic.

2.  The server side is with 9.10, but "TERA" is a physical unit NTFS formatted.

I'm now reading a lot from [http://nfs.sourceforge.net](http://nfs.sourceforge.net)...

---

### Post by dmizer on 2009-12-22
> **^_Pepe_^ said:**
> Yes! 

0. Client is 9.10 and Wireless connected.

1. My wife Medion Akoya Mini E1210 with 9.04 has the same behaviour. Good for Karmic.

2.  The server side is with 9.10, but "TERA" is a physical unit NTFS formatted.

I'm now reading a lot from [http://nfs.sourceforge.net](http://nfs.sourceforge.net)...

Are you sure you are not simply losing your wireless connection to the router and thereby severing your connection to the NFS server?

Also, I would consider yourself lucky as I was under the impression that you could not share an NTFS drive via NFS. However, the NTFS format may be the root of your encoding problem.

---

### Post by ^_Pepe_^ on 2009-12-23
I'm sure about wireless. It was my first suspicion.

I guess I finally found the issue. I've mounted as NFS (same way), the server's /home and /etc folders (ext3), and I have no issues down here (in client).

Bad luck anyway, because this TERA unit is also samba shared with my HTPC with Windows Vista and should be NTFS.

I think I'll put a bug in Launchpad.

Thanks a lot!

---

### Post by bingtang on 2009-12-25
Hi All

I had installed nfs-common in the client laptop but nfs-common is not show up in the /etc/init.d/ directory. I try apt-get remove portmap nfs-common and reinstalled. It is still the same.
Every time I type sudo /etc/init.d/nfs-common restart message came back as:
sudo: /etc/init.d/nfs-common: command not found. I have installed ubuntu 9.10 with 40GB SATA drive format as EXT4. Your help well greatly appreciate.

---

### Post by AlexanderDGreat on 2009-12-25
Hi bingtang, I'm not an expert but I know a little:

You don't type nfs-common in a CLI, because it is not a script, basically /etc/init.d/ is a container of script-run-services in Ubuntu. Therefore you type, in Karmic

sudo service nfs-kernel-server restart

so you don't have to go to /etc/init.d/

just type it anywhere, but if you like the old-fashioned way, you still type:

sudo /etc/init.d/nfs-kernel-server restart

What are you trying to do anyway?

---

### Post by dmizer on 2009-12-26
> **bingtang said:**
> Hi All

I had installed nfs-common in the client laptop but nfs-common is not show up in the /etc/init.d/ directory. I try apt-get remove portmap nfs-common and reinstalled. It is still the same.
Every time I type sudo /etc/init.d/nfs-common restart message came back as:
sudo: /etc/init.d/nfs-common: command not found. I have installed ubuntu 9.10 with 40GB SATA drive format as EXT4. Your help well greatly appreciate.

Since nfs-common is on the client side, it's only called as needed and doesn't run as a daemon. This is why it's not found in /etc/init.d ... it's not a service.

To restart the server side of things, you'll need to run this command:
```
sudo /etc/init.d/nfs-kernel-server restart
```

The information in this article: [http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html](http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html) is quite old, and doesn't apply anymore.

Just follow the howto on the first page and you'll have a working configuration.

---

### Post by unipsycho on 2009-12-27
I've been working on getting NFS working here and followed this thread (the one I'm posting in) and this [HOWTO for NFS and firewall]("http://ubuntuforums.org/showthread.php?t=352486").

I travel quite a bit and would find it useful to access my home computer through NFS. I have been able to set up NFS and in my private net (192.168.x.x) it works well.

Going off my net (using a neighbor's), I've been unable to get through to the server. Thinking it was the firewall, I opened up 111, and 2049 as well as added 4000-4002 per the above-mentioned HOWTO.

It looks like I'm getting through, but the server is not accepting the connection. So, looking at my /etc/exports file:

```
/work   palmtree(rw,no_root_squash,async,no_subtree_check)
``` and doing some further digging, I'm finding that my host name is not a good way to discriminate in the /etc/exports file. Depending on which network to which I am connected, my host name changes.

So (finally!) getting to the question. Is the following exports line the best way for me to open the NFS door so I can access my computer from literally anywhere? Note: I do have a dynamic IP (it changes about every 3 to 5 days), but the obscurity doesn't really make me feel secure. Is there a better way?

```
/work   (rw,no_root_squash,async,no_subtree_check)
```

For statistics: Ubuntu/9.04

---

### Post by dmizer on 2009-12-28
> **unipsycho said:**
> I've been working on getting NFS working here and followed this thread (the one I'm posting in) and this [HOWTO for NFS and firewall]("http://ubuntuforums.org/showthread.php?t=352486").

I travel quite a bit and would find it useful to access my home computer through NFS. I have been able to set up NFS and in my private net (192.168.x.x) it works well.

Going off my net (using a neighbor's), I've been unable to get through to the server. Thinking it was the firewall, I opened up 111, and 2049 as well as added 4000-4002 per the above-mentioned HOWTO.

It looks like I'm getting through, but the server is not accepting the connection. So, looking at my /etc/exports file:

```
/work   palmtree(rw,no_root_squash,async,no_subtree_check)
``` and doing some further digging, I'm finding that my host name is not a good way to discriminate in the /etc/exports file. Depending on which network to which I am connected, my host name changes.

So (finally!) getting to the question. Is the following exports line the best way for me to open the NFS door so I can access my computer from literally anywhere? Note: I do have a dynamic IP (it changes about every 3 to 5 days), but the obscurity doesn't really make me feel secure. Is there a better way?

```
/work   (rw,no_root_squash,async,no_subtree_check)
```

For statistics: Ubuntu/9.04

Please close those ports on your router. NFS is not meant to be shared across the Internet. It's not safe, just like SAMBA is not safe for sharing across the Internet. If configured correctly, anyone on the WWW would be able to access your shares. The only thing that would prevent that is local file permissions.

Please use an encrypted protocol like ssh or VPN. These protocols are meant to be handled safely across the Internet.

---

### Post by tad1073 on 2010-01-05
how can I add my nfs share to fstab when connecting via wireless network? I do not gain a connection until I am at my desktop.

---

### Post by yens on 2010-01-07
> **tad1073 said:**
> how can I add my nfs share to fstab when connecting via wireless network? I do not gain a connection until I am at my desktop.

Hi,
This is my case and I don't have any problem with mounting the nfs share from fstab. The nfs share mounts just after the connection is available. The delay is only 1-2 seconds after the indicator shows "connected".
This is the entry in my fstab
```
# nfs variant
192.168.0.10:/home/nfsshare /home/mountpoint nfs rw 0 0
```
First try if the nfs share works with:
```
sudo mount 192.168.0.10:/home/nfsshare /home/mountpoint
```
If this works, the fstab entry should work too.

---

### Post by mp035 on 2010-01-07
THANK YOU, THANK YOU, THANK YOU !!!!!!!!!!!!!!!!!!!!!

Samba has been a PITA since I started using linux (over 4 years ago).

(Networking when I was using windows was a PITA period.)

After 5 minutes I had NFS up and running thanks to your HOWTO.:D:D

---

### Post by tad1073 on 2010-01-08
thanks, will give it a try

> **yens said:**
> Hi,
This is my case and I don't have any problem with mounting the nfs share from fstab. The nfs share mounts just after the connection is available. The delay is only 1-2 seconds after the indicator shows "connected".
This is the entry in my fstab
```
# nfs variant
192.168.0.10:/home/nfsshare /home/mountpoint nfs rw 0 0
```First try if the nfs share works with:
```
sudo mount 192.168.0.10:/home/nfsshare /home/mountpoint
```If this works, the fstab entry should work too.

---

### Post by scrooge_74 on 2010-01-08
Piece of my export file on the server currently working

/mnt/multimedia/musica/ 192.168.2.0/255.255.255.0(rw,sync,no_subtree_check)

Matching piece on the client fstab 

192.168.2.2:/mnt/multimedia/musica /mnt/musica nfs rsize=8192,wsize=8192,timeo=14,noauto,user,rw

To access files from outside the network I go with ssh, nfs is not for going out in the public

---

### Post by AlexanderDGreat on 2010-01-09
Hi, can NFS interact with OpenLDAP? Will they play along nicely? Do I need to install modules for it? The reason I'm asking is because I want to authenticate my Windows & Ubuntu users to just use NFS, and OpenLDAP.

Hoping for anyone's enlightenment.

---

### Post by scrooge_74 on 2010-01-09
I have no clue on this, the only part I know is that the Windows users wont be able to use nfs for that you would need samba. 

Someone slap me silly if Im wrong

---

### Post by tad1073 on 2010-01-09
didn't work, getting an error during boot saying unable to mount

> **yens said:**
> Hi,
This is my case and I don't have any problem with mounting the nfs share from fstab. The nfs share mounts just after the connection is available. The delay is only 1-2 seconds after the indicator shows "connected".
This is the entry in my fstab
```
# nfs variant
192.168.0.10:/home/nfsshare /home/mountpoint nfs rw 0 0
```First try if the nfs share works with:
```
sudo mount 192.168.0.10:/home/nfsshare /home/mountpoint
```If this works, the fstab entry should work too.

---

### Post by dmizer on 2010-01-09
> **tad1073 said:**
> didn't work, getting an error during boot saying unable to mount

Try this instead:
```
192.168.0.10:/home/nfsshare /home/mountpoint rsize=8192,wsize=8192,timeo=14,intr
```

If you get an error, what does the error say?

---

### Post by tad1073 on 2010-01-09
> **dmizer said:**
> Try this instead:
```
192.168.0.10:/home/nfsshare /home/mountpoint rsize=8192,wsize=8192,timeo=14,intr
```If you get an error, what does the error say?

I tried that one also.
something about not being able to resolve dns
my connection is wireless and I don't gain a connection until I get to my desktop

---

### Post by scrooge_74 on 2010-01-11
Seems you will have to log in first then mount shares

---

### Post by lemmy999 on 2010-01-11
I am trying to set up a very small network using NFS. Only two machines involved, my main desktop and a netbook which will generally access the share wirelessly. Both machines are running Ubuntu ( server is vanilla 9.10, client runs Crunchbanglinux 9.04)

Specs are as follows
> Server
hostname - alpha
IP 192.168.1.91
share- /home/chris

Client
Hostname- delta
IP 192.168.1.88 ( wireless) 192.168.1.87 (eth0)

exports config
```
/home/chris  192.168.1.88 (rw,sync,subtree_check)
```

Restarting NFS gives the following
```
chris@alpha:~$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                               exportfs: No options for /home/chris 192.168.1.88: suggest 192.168.1.88(sync) to avoid warning
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.88:/home/chris".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: No host name given with /home/chris (rw,sync,no_subtree_check), suggest *(rw,sync,no_subtree_check) to avoid warning
                                                                         [ OK ]
 * Starting NFS kernel daemon                  
```

Exporting exports gives
```
chris@alpha:~$ sudo exportfs -a
exportfs: No options for /home/chris 192.168.1.88: suggest 192.168.1.88(sync) to avoid warning
exportfs: /etc/exports [2]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.88:/home/chris".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: No host name given with /home/chris (rw,sync,no_subtree_check), suggest *(rw,sync,no_subtree_check) to avoid warning
```

Mounting the share from the client
```
chris@delta:~$ sudo mount alpha:/home/chris /home/chris/share
[sudo] password for chris:
mount.nfs: mount system call failed
```

Any ideas where I am going wrong?

---

### Post by dmizer on 2010-01-11
> **tad1073 said:**
> I tried that one also.
something about not being able to resolve dns
my connection is wireless and I don't gain a connection until I get to my desktop

Try the _netdev option like so:
```
192.168.0.10:/home/nfsshare /home/mountpoint [COLOR="Red"]_netdev[/COLOR],rsize=8192,wsize=8192,timeo=14,intr
```
That should force the mount to wait for a network connection.

---

### Post by dmizer on 2010-01-11
> **lemmy999 said:**
> 
Any ideas where I am going wrong?

You have a space between the IP address and the parentheses in your exports.

It should look like this:
```
/home/chris  192.168.1.[COLOR="Red"]88(rw[/COLOR],sync,no_subtree_check)
```

---

### Post by lemmy999 on 2010-01-12
@dmizer- I'll try that when I get home.

Thanks

---

### Post by AlexanderDGreat on 2010-01-12
[COLOR="Blue"]**@dmizer**[/COLOR] - Hi, can you pls. help me? I have this in /etc/exports

```
/home/me/office_file_server 192.168.1.50/24(rw,no_root_squash,async)
```

I have 4 folders inside office_file_server folder, one of them is **free4all**. This means anyone can read/write ANY files to it.

However, people in the office put a file in **free4all** but the DEFAULT PERMISSIONS are 644. I go to another machine, retrieve file and it's _Read-Only_.

[COLOR="Blue"]**How can I make a, "I don't care who you are, but if you make a file in free4all, it's 777.**[/COLOR]

Thanks for your help man.

PS This is in /etc/fstab on 1 Ubuntu machine:

```
192.168.1.51:/home/me/office_file_server /media/office_file_server nfs rsize=8192,wsize=8192,timeo=14,intr
```

My /etc/samba/smb.conf for Windows clients:

```
[office_file_server]
path = /home/me/office_file_server
public = yes
available = yes
browseable = yes
writeable =yes
read only = no
valid users = @officemates
```

---

### Post by bcn17 on 2010-01-12
> **AlexanderDGreat said:**
> 

[COLOR="Blue"]**How can I make a, "I don't care who you are, but if you make a file in free4all, it's 777.**[/COLOR]


Check out post #8 by bcn17 (me) and look for:

umask

[http://ubuntuforums.org/showthread.php?t=1347091]("http://ubuntuforums.org/showthread.php?t=1347091")

---

### Post by AlexanderDGreat on 2010-01-12
@dmizer - I guess no need...

[COLOR="RoyalBlue"]**@bcn17 - Thank you sir. God Bless. I'll try your suggestion.**[/COLOR]

---

### Post by tad1073 on 2010-01-12
> **dmizer said:**
> Try the _netdev option like so:
```
192.168.0.10:/home/nfsshare /home/mountpoint [COLOR=Red]_netdev[/COLOR],rsize=8192,wsize=8192,timeo=14,intr
```That should force the mount to wait for a network connection.

that didn't work either, stalls when booting

---

### Post by lemmy999 on 2010-01-12
@dmizer

Made the changes as you suggested. Still same error. Tried out with -v switch and got the following
```
chris@delta:~$ sudo mount -v alpha:/home/chris /home/chris/share
[sudo] password for chris: 
mount: no type was given - I'll assume nfs because of the colon
mount.nfs: timeout set for Tue Jan 12 21:12:08 2010
mount.nfs: text-based options: 'addr=192.168.1.91'
mount.nfs: mount(2): Input/output error
mount.nfs: mount system call failed
```

---

### Post by Jose Catre-Vandis on 2010-01-12
Can you try with a wired connection, just to eliminate wireless gremlins?

---

### Post by dmizer on 2010-01-12
> **lemmy999 said:**
> @dmizer

Made the changes as you suggested. Still same error. Tried out with -v switch and got the following
```
chris@delta:~$ sudo mount -v alpha:/home/chris /home/chris/share
[sudo] password for chris: 
mount: no type was given - I'll assume nfs because of the colon
mount.nfs: timeout set for Tue Jan 12 21:12:08 2010
mount.nfs: text-based options: 'addr=192.168.1.91'
mount.nfs: mount(2): Input/output error
mount.nfs: mount system call failed
```

Have you installed the client side packages on the delta machine?
```
sudo apt-get install portmap nfs-common
```

---

### Post by lemmy999 on 2010-01-13
@ dmizer- both packages are installed

@JCV- Tried on a wired connection to ensure that it wasn't a wireless issue. Same outcome!

Tried "showmount -e" from the client (delta)- gave the following- "showmount: RPC : program not registered"

From the client- rpcinfo
chris@delta:~$ rpcinfo -p alpha
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  56420  status
    100024    1   tcp  52734  status
    100021    1   udp  59023  nlockmgr
    100021    3   udp  59023  nlockmgr
    100021    4   udp  59023  nlockmgr
    100021    1   tcp  49026  nlockmgr
    100021    3   tcp  49026  nlockmgr
    100021    4   tcp  49026  nlockmgr
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  42170  mountd
    100005    1   tcp  43246  mountd
    100005    2   udp  42170  mountd
    100005    2   tcp  43246  mountd
    100005    3   udp  42170  mountd
    100005    3   tcp  43246  mountd
 
And
chris@delta:~$ showmount -e alpha
rpc mount export: RPC: Timed out

From the chris@delta:~$ rpcinfo -p delta
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  36888  status
    100024    1   tcp  49364  status
 end ( alpha)

---

### Post by Jose Catre-Vandis on 2010-01-13
Hmmm...my exports file for my home directory, on my server, reads like this:

```
/home 10.10.10.1/24(rw,no_root_squash,async,no_subtree_check)
```

My lan runs on 10.10.10.xxx

But on my client I have to mount as follows:
```
sudo mount 10.10.10.70:/home/jose  /media/nfsjose
```

and fstab reads like this:

```
10.10.10.70:/home/jose                   /media/nfsjose       nfs     rsize=8192,wsize=8192,timeo=14,intr,bg
```

So two changes:

Spread the nfs share by using **xx.xx.xx.1/24** and include the options I showed

Change the mount syntax in exports and in your mount command accordingly
(remember to re-export your export file, and to restart the nfs server for good measure)

---

### Post by ozzyprv on 2010-01-13
I am getting this error:

```

mount: no type was given - I'll assume nfs because of the colon
mount.nfs: timeout set for Wed Jan 13 19:56:56 2010
mount.nfs: text-based options: 'addr=192.168.1.151'
mount.nfs: mount(2): Input/output error
mount.nfs: mount system call failed

```

I set up this way at server: 

```
/media/Disk02/ 192.168.1.0/24(rw,no_root_squash,async)

```
And tried to manually mount at client like this:

```
me@mybox:~$ sudo mount -v 192.168.1.151:/media/Disk02/ /home/me/share/
```

[COLOR="Blue"]EDIT: Just realized some other people has the same problem. Yes I did "sudo apt-get install portmap nfs-common" @ client.[/COLOR]

---

### Post by lemmy999 on 2010-01-14
@Jose Catre-Vandis

Tried both your suggestions- still no joy!

---

### Post by Jose Catre-Vandis on 2010-01-14
Is this the same "no joy" or different errors?

Set up a mountpoint on the server, and try to mount the nfs share ON THE SERVER (Yes, it does work). This will prove that the server end of things is working

**On the server**
```
sudo mkdir /media/testnfs
sudo mount 10.10.10.70:/home/jose /media/testnfs
```
(10.10.10.70 is the IP of the server you are on)

This applies to my exports above in previous post


Other suggestions - download a Jaunty Server Edition and install that, if Karmic is causing a problem with nfs?

---

### Post by lemmy999 on 2010-01-14
@JCV

Sorry i wasn't clearer! Still getting the same " mount.nfs: mount system call failed"

I'll give your latest suggestion a go to see where that gets us.

I really don't want to have to install the server version as the alpha machine is my main desktop. You seem to be implying that something in KK is breaking NFS which I suspect is pretty close to the truth.:(

OK- tried your suggestion- that works so we know that NFS is working on the server!

---

### Post by Jose Catre-Vandis on 2010-01-14
Well that's progress - have a drink/whatever :)

Do you have the same users with the same UIDs on both the desktop/server and the client?

I try to ensure mine wroks by doing this, so jose UID 1000 on client and jose UID 1000 on server (even if not logged in it seems to sort out permissions inside the share)

Um, didn't check basic connectivity between the two PCs. How are they networked and can you ping from each PC to the other?

Have you rebooted either machine recently? This is my favourite fix - the cold reboot - Turn off and wait then switch back on, you'd be amazed how this can sometimes help :)

---

### Post by ozzyprv on 2010-01-14
> **Jose Catre-Vandis said:**
> 
Do you have the same users with the same UIDs on both the desktop/server and the client?

I try to ensure mine wroks by doing this, so jose UID 1000 on client and jose UID 1000 on server (even if not logged in it seems to sort out permissions inside the share)

What happens if you don't? 
I do not use the same usernames. Server is mark_adm@.. , client is mark@....

Thanks.

---

### Post by Jose Catre-Vandis on 2010-01-15
> **ozzyprv said:**
> What happens if you don't? 
I do not use the same usernames. Server is mark_adm@.. , client is mark@....

Thanks.

NFS should still work if you don't, it just simplifies permissions on "simple" networks like home LANs

---

### Post by lemmy999 on 2010-01-15
@JCV

UID on both machines is the same- 1000 chris.

Both machines are currently on a wired lan and can ping each other.

I tend to reboot both machines every day so i don't particularly see that as a problem.

---

### Post by Jose Catre-Vandis on 2010-01-15
Can you try a share outside of your home directory?

Set up a share in /media on the server, and add to /etc/exports and export your exports


Try to mount on your client

Also try this when logged out of server

(as you can see I am starting to run out of ideas :))

---

### Post by ozzyprv on 2010-01-15
> **lemmy999 said:**
> 
UID on both machines is the same- 1000 chris.


So, do the client/server UID's have to be the same or not?

I cannot set up my NFS server on a simple LAN network either.

Thanks.

---

### Post by lemmy999 on 2010-01-16
@JCV
Tried your latest suggestion with the usual " mount system call failed" result. I thought I'd have a look at the firewall settings to see if that was the problem.
Trying to mount via  the client produces a blocked connection on the firewall.  Stopping the firewall produces the following error ```
 mount.nfs: access denied by server while mounting 192.168.1.91:/media/nfstest
```

I have allowed NFS in Firestarter on ports 111 and 2049 ( I assume those are the defaults for NFS).

---

### Post by lemmy999 on 2010-01-16
Definitely getting closer. Tried the following to force the firewall to accept the mount command
```
chris@delta:~$ sudo mount -t nfs4 -o proto=tcp,port=2049 192.168.1.91:/home/chris /home/chris/share
mount.nfs4: mounting 192.168.1.91:/home/chris failed, reason given by server:
  No such file or directory
```

---

### Post by Jose Catre-Vandis on 2010-01-16
Right, drop the firewall and anything else you might have blocking ports and try again

---

### Post by lemmy999 on 2010-01-16
Stopped the firewall via Firestarter,tried to run the mount command  from the client and get
```
mount.nfs: access denied by server while mounting alpha:/media/nfstest
```

Edit
Even stranger, tried to mount /home/chris and it worked!! Better get fstab sorted and see if I can get the share mounted @ boot!

---

### Post by lemmy999 on 2010-01-16
My fstab is as follows
```
UUID=d9156e9f-ed1b-44e1-b307-2557e0211b98 /home           ext4    relatime        0       2
# swap was on /dev/sdb5 during installation
UUID=77ca82f4-c9a9-40d3-aebd-a82093d32413 none            swap    sw              0       0
alpha:/home/chris /home/chris/share  nfs rsize=8192,wsize=8192,timeo=14,intr,noauto
```

Any idea why its not mounting on boot?

I can still mount manually!!:D Just got to work out how to configure the firewall now

---

### Post by dmizer on 2010-01-16
> **lemmy999 said:**
> My fstab is as follows
```
UUID=d9156e9f-ed1b-44e1-b307-2557e0211b98 /home           ext4    relatime        0       2
# swap was on /dev/sdb5 during installation
UUID=77ca82f4-c9a9-40d3-aebd-a82093d32413 none            swap    sw              0       0
alpha:/home/chris /home/chris/share  nfs rsize=8192,wsize=8192,timeo=14,intr,noauto
```

Any idea why its not mounting on boot?

I can still mount manually!!:D Just got to work out how to configure the firewall now

The noauto option prevents the share from being mounted at boot. Remove it, and it will mount on boot.

Are you even positive you need a firewall? If you're on a LAN, that usually means you have a router between The Internet and you. Routers usually have firewalls on them. So, you need to consider if you think it's necessary to firewall traffic on your local LAN. IOW ... Do you really need one firewall for The Internet, and another for your LAN, and/or ... do you have a specific reason to be afraid of traffic on your own LAN?

---

### Post by lemmy999 on 2010-01-16
@dmizer

I'll change that entry in fstab and see what happens. As regards the firewall thing I suspect you are right. I have a router which will perform firewalling duties so using iptables as well is probably overkill.

@dmizer
Your suggestion worked well. Many thanks to you and JCV for all your help.

---

### Post by Jose Catre-Vandis on 2010-01-16
:)

---

### Post by ozzyprv on 2010-01-16
...any help for me?

I was able to mount the share on the client, but now I am having problems with the permissions.
The only way to gain rw access to the folders is if I set the "others" permission as rw.

How do I do to make the user@client part of the group the folders at the server belong to?

Thanks in advance.

---

### Post by AlexanderDGreat on 2010-01-16
@ozzyprv - in my case, I made my clients all part of 1 group say, office, then I made their accounts in the server. I also logged-in to their desktops so it will say, "added user tom", otherwise they can't access the shares, I don't know if it's true in Karmic. Are the clients fresh install desktops? Because, I had the same problem before so I forced all users in the server to have unique ID's instead of their defaults. 1010 - 1020 are unique, then manually I also changed their workstation user ids from the default 1000, to 1010 - 1020 using this command.

# id tom
# usermod -u 1010 tom
# id tom

That's just for simplicity sake. See if that works for you... So my shares now are

sudo chmod -R 1770 folder

So even if they have rw access, they can't delete it with the 1 switch instead of 0770.

---

### Post by Jose Catre-Vandis on 2010-01-17
Also will depend on how much "security" / "file protection" you are after. I can trust everyone on my home LAN, so tend to chmod -R 777 all files and directories (outside of home), which makes things alot easier. Anything on my nfs shares is backed up anyway so if something gets trashed I just put it back.

But AlexDG is right, sorts out your users on group permissions and you should be good to go

---

### Post by ozzyprv on 2010-01-17
_BACKGROUND:_

This is my /etc/exports:
```

/media/Disk01/mysharedfolder 192.168.1.100 (rw,root_squash,sync)
```

Client connects when logged on as "mark", UID:1000. "mark" belongs to some 4 or 5 groups. Among those groups, "mark" is part of "sshare", GID: 1234.

At server, /media/Disk01/mysharedfolder is owned by "mark_server", UID: 1000. And it is part of the group "sshare". This is how a 'ls -al' @ /media/Disk01/ looks like:
```
drwxrwxrwx 21 mark_server sshare  4096 2010-01-13 19:00
```
At server, "sshare" GID: 1234.
At server, "mark" UID: 1004.


_ISSUE:_


Mounting goes okay. I can read everything that is @ /media/Disk01/mysharedfolder from client. But I cannot write. I cannot delete files or move files into the folder.

---

### Post by AlexanderDGreat on 2010-01-17
In post #406:

> The only way to gain rw access to the folders is if I set the "others" permission as rw.

And you have...

> drwxrwxrwx 21 mark_server sshare  4096 2010-01-13 19:00

Does this mean client "mark" can already write to the folder above or do you still have issues?

If you still can't I don't know what to do. But try to make a "new shared folder" and a "new test account" and make them interact together to see what happens. A similar problem happened to me before, **did you change their ID's via the GUI or the terminal**? I fixed my problem before by using the terminal as I read here: [http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/]("http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/") But, I may be missing the problem completely, if that's the case I hope others can help you.

---

### Post by ozzyprv on 2010-01-18
> **AlexanderDGreat said:**
> In post #406:
..................
And you have...
..................
Does this mean client "mark" can already write to the folder above or do you still have issues?

I still have the issue. I guess that @ post #406 I spoke too soon, I assumed that having read access was having rw access. I was wrong.

> **AlexanderDGreat said:**
> **did you change their ID's via the GUI or the terminal**?


Via terminal. Note that the users do not have the same UID. Both "sshare" groups (server and client) do have the same GID.

Thanks for trying to help!

---

### Post by secure on 2010-01-19
thanks.It's easy to understand and work :D

---

### Post by confusion_music on 2010-01-25
Does anyone know if it is possible for a share exported using NFS can also be exported using Samba? The reason for asking is I'm in the process of setting up my home folder as a share for a second linux box, but I would also like the share to be accessible by my wifes vista laptop and possibly another xp laptop. 

Thanks for all the tips and advice in the thread so far.

---

### Post by ^_Pepe_^ on 2010-01-25
> **confusion_music said:**
> Does anyone know if it is possible for a share exported using NFS can also be exported using Samba? The reason for asking is I'm in the process of setting up my home folder as a share for a second linux box, but I would also like the share to be accessible by my wifes vista laptop and possibly another xp laptop. 

Thanks for all the tips and advice in the thread so far.

Sure! I do it, in fact!

You should have NTFS formatted unit, to be easily detected by Windows.

---

### Post by PaulHuffman on 2010-01-25
> **confusion_music said:**
> Does anyone know if it is possible for a share exported using NFS can also be exported using Samba? The reason for asking is I'm in the process of setting up my home folder as a share for a second linux box, but I would also like the share to be accessible by my wifes vista laptop and possibly another xp laptop. 


I thought I had tried this before but ran into permission problems. But today it worked and this will help me a lot.  There's a old Solaris server in another department that stores some big sets of air photos.  The airphotos are shared to other departments only through NFS shares that were made years ago by people brighter than those working there now. In order to get these NFS resources, they use expensive PC-NFS software. I've shown them how I use Samba on my Solaris server, but their eyes glaze over, and they nod vacantly. On my Ubuntu 9.10 PC, I just used the line "sudo mount 161.217.7.51:/vol/vol0/home ~/photoserver" where the IP is that the air photo server, and photoserver is a folder on my Ubuntu PC made for a mount point and it hooked right up.  Then I went over to a Windows PC and went to Start>run>\\161.217.20.27, the IP of my Ubuntu PC, and photoserver appeared in the list of shares on Ubuntu. I clicked on it and it hooked right up after I gave windows my Ubuntu authentication.  So now I can assign this mount a drive letter and finally be able to use these air photos directly on my windows PC.

---

### Post by frenchn00b on 2010-01-26
I had an issue and solved this this way. it works now! thanks

```
//***SOLVED: //***SOLVED: 

mount: RPC: Timed out
or 
mount.nfs: access denied by server while mounting 


So, first: 
Install NFS Server Support
at the terminal type
sudo apt-get install nfs-kernel-server nfs-common portmap
When configuring portmap do =not= bind loopback. If you do you can either edit /etc/default/portmap by hand or run:
sudo dpkg-reconfigure portmap
sudo /etc/init.d/portmap restart

the most important is : do =not= bind loopback.

a# dpkg-reconfigure portmap
Stopping portmap daemon....
update-rc.d: warning: portmap start runlevel arguments (S) do not match LSB Default-Start values (S 2 3 4 5)
Starting portmap daemon....
Restoring old RPC service information....
There are RPC services which were registered with the portmapper
before the configuration was changed.
You need to manually restart them in order for the changes to take effect.
Current registered services:
------------------------------------------------
    100024    1   udp  51647  status
    100024    1   tcp  43086  status
    100021    1   udp  48101  nlockmgr
    100021    3   udp  48101  nlockmgr
    100021    4   udp  48101  nlockmgr
    100021    1   tcp  47109  nlockmgr
    100021    3   tcp  47109  nlockmgr
    100021    4   tcp  47109  nlockmgr
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  60568  mountd
    100005    1   tcp  33252  mountd
    100005    2   udp  60568  mountd
    100005    2   tcp  33252  mountd
    100005    3   udp  60568  mountd
    100005    3   tcp  33252  mountd
------------------------------------------------





then : 
put this into: 
/etc/exports
/home   192.168.10.100:/24(rw,no_subtree_check,no_root_squash)



sudo /etc/init.d/portmap start
sudo /etc/init.d/nfs-common start
sudo /etc/init.d/nfs-kernel-server start 

rpcinfo -p localhost



mkdir /mnt/nfstest/ 
mount 192.168.10.100:/home/ -t nfs

//***SOLVED// 

mount: RPC: Timed out
or 
mount.nfs: access denied by server while mounting 


So, first: 
Install NFS Server Support
at the terminal type
sudo apt-get install nfs-kernel-server nfs-common portmap
When configuring portmap do =not= bind loopback. If you do you can either edit /etc/default/portmap by hand or run:
sudo dpkg-reconfigure portmap
sudo /etc/init.d/portmap restart

the most important is : do =not= bind loopback.

a# dpkg-reconfigure portmap
Stopping portmap daemon....
update-rc.d: warning: portmap start runlevel arguments (S) do not match LSB Default-Start values (S 2 3 4 5)
Starting portmap daemon....
Restoring old RPC service information....
There are RPC services which were registered with the portmapper
before the configuration was changed.
You need to manually restart them in order for the changes to take effect.
Current registered services:
------------------------------------------------
    100024    1   udp  51647  status
    100024    1   tcp  43086  status
    100021    1   udp  48101  nlockmgr
    100021    3   udp  48101  nlockmgr
    100021    4   udp  48101  nlockmgr
    100021    1   tcp  47109  nlockmgr
    100021    3   tcp  47109  nlockmgr
    100021    4   tcp  47109  nlockmgr
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  60568  mountd
    100005    1   tcp  33252  mountd
    100005    2   udp  60568  mountd
    100005    2   tcp  33252  mountd
    100005    3   udp  60568  mountd
    100005    3   tcp  33252  mountd
------------------------------------------------





then : 
put this into: 
/etc/exports
/home   192.168.10.100:/24(rw,no_subtree_check,no_root_squash)



sudo /etc/init.d/portmap start
sudo /etc/init.d/nfs-common start
sudo /etc/init.d/nfs-kernel-server start 

rpcinfo -p localhost



mkdir /mnt/nfstest/ 
mount 192.168.10.100:/home/ -t nfs

//***SOLVED// 
```

---

### Post by yens on 2010-01-26
> **confusion_music said:**
> Does anyone know if it is possible for a share exported using NFS can also be exported using Samba? The reason for asking is I'm in the process of setting up my home folder as a share for a second linux box, but I would also like the share to be accessible by my wifes vista laptop and possibly another xp laptop. 

Thanks for all the tips and advice in the thread so far.

I've been doing this for almost half an year but there were some permission problems. I have public folder what has write permission to all PCs. The issue was that if some creates folder via samba (no matter form linux or windows) the new folder was with only read permission to nfs users.
I solved this by adding this to the share definition in smb.conf:
```
create mode = 0777
force create mode = 0777
force directory mode = 0777
```

---

### Post by ozzyprv on 2010-01-28
> **frenchn00b said:**
> I had an issue and solved this this way. it works now! thanks


frenchn00b, 
I am having problems reading your post. Could you please tell me what were the "extra" or "particular" commands you used to solve the problem?

Thank you.

---

### Post by Jose Catre-Vandis on 2010-01-30
> **ozzyprv said:**
> frenchn00b, 
I am having problems reading your post. Could you please tell me what were the "extra" or "particular" commands you used to solve the problem?

Thank you.

frenchnoob is simply reiterating the original howto

---

### Post by red71 on 2010-02-04
Hello,
I tried commands from this topic to mount my NAS (Qnap TS-210).
Those commandes worked perfectly
sudo mount -t nfs 192.168.71.1:/Qmultimedia /mnt/qnap210/Qmultimedia
OR
[SIZE=2][SIZE=3]sudo /sbin/mount.nfs 192.168.71.1:/Qmultimedia /mnt/qnap210/Qmultimedia

but I can't make it in /etc/fstab/
I tried:
192.168.71.1:/Qmultimedia /mnt/qnap210/Qmultimedia nfs  rw,rsize=8192,soft,wsize=8192,timeo=14,intr 0 0
OR
192.168.71.1:/Qmultimedia /mnt/qnap210/Qmultimedia nfs user 0 0

None works. Could anybody help me ?
Thanks in advance.[/SIZE]  
[/SIZE]

---

### Post by Jose Catre-Vandis on 2010-02-04
@red71

Did you try without the two "0"s at the end? I don't have those in my fstab.

---

### Post by red71 on 2010-02-05
Removing the 0 0 doesn't change anything.

---

### Post by Jose Catre-Vandis on 2010-02-05
What response do you get if you type the following:
```
mount

and

sudo mount -a
```
in a terminal

---

### Post by red71 on 2010-02-05
Adding auto in options line works !
Shame on me since it seems a very "simple solution".
Now it works as I would :D

---

### Post by red71 on 2010-02-06
Here my last version with improved performance.
Any ideas on it ?

192.168.71.1:/Qmultimedia /mnt/qnap210/Qmultimedia nfs auto,user,rsize=32768,wsize=32768,intr 0 0

---

### Post by Vangelis666 on 2010-02-26
Thanks to the OP. I was having REAL problems getting this going but I figured it out when I checked the log files using the log file viewer. This info may help others so I'm posting it here.

Before you run the command that is causing you problems (for me it was the mount command) start the Log File Viewer under System | Administration on both the server and the client machines. Then run the command that is causing problems. The log file viewers will then highlight the areas where there are new logs. Click on those and check the information given. For me, I was getting a server refusal to connect for a reason I couldn't understand. When I ran the command, the server log file viewer showed me the reason. I didn't have the directory path specified correctly. When I changed that on the client's mount command, bingo, it all worked!

So thanks once again for this How To info.

Finally I can share network folders... now back to solving my samba issues...

---

### Post by red71 on 2010-02-27
My issues are resolved ! I buyed a Synology DS-209...
Now Samba and NFS transfer are between 20MB/s and 55MB/s !

---

### Post by santhony on 2010-03-07
Great HOWTO!!  What I couldn't do in the past three days, I was able to do in 3 mins with these instructions!!

It's HOWTO's like these that really propel LINUX.

---

### Post by red71 on 2010-03-07
I got another problem.
From Windows, no problem to add/delete files on my NAS.
From ubuntu 9.10, mounting/viewing/reading NAS folders is ok, but i can't add/delete files UNLESS i'm Root. Acess privileges are correctly defined on my NAS, so I should can delete files even I'm not Root.
Anyone could help me ?

Here is line I have in my /etc/fstab
192.168.71.1:/volume1/NAS_maison /mnt/Syno209/NAS_maison nfs        suid,dev,exec,auto,user,async,rsize=8192,wsize=8192,soft,timeo=14,intr    0    0

---

### Post by dannyboy79 on 2010-03-09
> **red71 said:**
> I got another problem.
From Windows, no problem to add/delete files on my NAS.
From ubuntu 9.10, mounting/viewing/reading NAS folders is ok, but i can't add/delete files UNLESS i'm Root. Acess privileges are correctly defined on my NAS, so I should can delete files even I'm not Root.
Anyone could help me ?

Here is line I have in my /etc/fstab
192.168.71.1:/volume1/NAS_maison /mnt/Syno209/NAS_maison nfs        suid,dev,exec,auto,user,async,rsize=8192,wsize=8192,soft,timeo=14,intr    0    0

i see a space in your file path, "192.168.71.1:/volume1/NAS_maison /mnt/Syno209/NAS_maison" after /NAS_maison /. Also, you'll need to show us the folder privileges on your nas to see who can all write to it. also, is your UID and GID the same on the nas as they are on the client?

---

### Post by red71 on 2010-03-09
What is UID and GID ?
I'll try to find information about it and post feedback here.

---

### Post by mfdc1969 on 2010-03-10
Thanks to all for this great How-To and all the resposes but I need a bit more help ...

All was going well until I tried to restart portmapper: 
```

~$ sudo /etc/init.d/portmap restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service portmap restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart portmap
portmap start/running, process 4632
```

Can someone please explain this to me? What do I need to do to restart the portmapper without having to reboot my machine?

---

### Post by dannyboy79 on 2010-03-11
> **mfdc1969 said:**
> Thanks to all for this great How-To and all the resposes but I need a bit more help ...

All was going well until I tried to restart portmapper: 
```

~$ sudo /etc/init.d/portmap restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service portmap restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart portmap
portmap start/running, process 4632
```

Can someone please explain this to me? What do I need to do to restart the portmapper without having to reboot my machine?
many times the terminal will tell you what to do or at least hint at what to do. in this case, if you would have fully read the message and took time to TRY to understand it and you would have known what to do. the line that's critical is this one from your terminal output, 

"Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service portmap restart"

so from reading the example it gave you, you would run:
```
sudo service portmap restart
```

---

### Post by dannyboy79 on 2010-03-11
UID = User ID number (the users identification number on that system)

GID = Group ID number (the groups identification number on that system)

most ubuntu installs that I have seen, the first user account created in UID and GID = 1000

here's a great article on how different UID and GID's can cause havoc. 

[http://lists.debian.org/debian-user/2005/02/msg00131.html](http://lists.debian.org/debian-user/2005/02/msg00131.html)

---

### Post by mfdc1969 on 2010-03-12
Thanks.

---

### Post by red71 on 2010-03-27
Doing 
chmod 777 /volume1/ -R
solved all my problems.

---

### Post by dannyboy79 on 2010-03-29
> **red71 said:**
> Doing 
chmod 777 /volume1/ -R
solved all my problems.

sure, making an entire volume and everything in it recursively read, write, and executable for the owner, the group, AND EVERYONE would solve any issues you were having. Very insecure.

---

### Post by red71 on 2010-03-29
What would be a better solution ?

---

### Post by santhony on 2010-03-30
If you google what each of the digits stands for, there's different levels of security.

The first 7 represents rw to the owner
the second 7 reprents rw to the group
the third 7 represents rw to everyone else..

Try something like 755, that will add a bit more security to your files and how they can be controlled.

---

### Post by fireteller on 2010-04-16
I'm trying to make this work on ec2.  Every thing seems to be working per the instructions, except for the strange "*sudo /etc/init.d/nfs-common restart"* instruction.

However when I try to actual run the mount I get this:

> sudo mount 10.243.63.192:/gfx /gfx
mount.nfs: mount system call failed
Exit 32

In the logs I see: 

kernel: [ 2603.445904] RPC: Registered udp transport module.
kernel: [ 2603.445907] RPC: Registered tcp transport module.
kernel: [ 2663.528428] rpcbind: server 10.243.63.192 not responding, timed out

I don't know what could be blocking the comunication.  Any ideas?

Thanks

---

### Post by Jose Catre-Vandis on 2010-04-18
> **fireteller said:**
> I'm trying to make this work on ec2.  Every thing seems to be working per the instructions, except for the strange "*sudo /etc/init.d/nfs-common restart"* instruction.

However when I try to actual run the mount I get this:

> sudo mount 10.243.63.192:/gfx /gfx
mount.nfs: mount system call failed
Exit 32

In the logs I see: 

kernel: [ 2603.445904] RPC: Registered udp transport module.
kernel: [ 2603.445907] RPC: Registered tcp transport module.
kernel: [ 2663.528428] rpcbind: server 10.243.63.192 not responding, timed out

I don't know what could be blocking the comunication.  Any ideas?

Thanks

Have you got a firewall up?

---

### Post by fireteller on 2010-04-19
> **Jose Catre-Vandis said:**
> Have you got a firewall up?

Nope they're 2 instances running on ec2 in the same security group. They have all port access to each other.

---

### Post by onlinespending on 2010-05-10
I'm trying to mount an NFS share on my Linux box that is being served by another Linux box.  But no matter what I do to try mounting the share I get back an error that the mount point is not a directory.
```

me@CLIENT:~$ sudo mount 192.168.1.1:/mnt /home/me/test
mount.nfs: mount point /home/me/test is not a directory
me@CLIENT:~$ ls -ltrF
drwxrwxrwx 2 me me      4096 2010-05-10 20:09 test/

```
Clearly it IS a directory.  I've tried multiple directories and all give me the same problem.  I have portmap, nfs-common, and even nfs-kernel-server installed.  I just don't get why it would complain about it.  The log files don't seem to show anything either.

---

### Post by dannyboy79 on 2010-05-11
may seem stupid but you show us ls command but not what your current working directory is.
why don't you go to ~/test/ and then issue 
pwd
so we can see that the /test/ directory is in fact located within /home/me/
and not somewhere else.

---

### Post by onlinespending on 2010-05-11
> **dannyboy79 said:**
> may seem stupid but you show us ls command but not what your current working directory is.
why don't you go to ~/test/ and then issue 
pwd
so we can see that the /test/ directory is in fact located within /home/me/
and not somewhere else.

I hear ya.  I can do that once I get home, but you have to trust me that I'm not that dense.  The working directory was /home/me/.  I have tried creating directories at the root and using them as the mount point.  It's very odd to say the least.

---

### Post by onlinespending on 2010-05-11
actually come to think of it, I did actually show the working directory just from the command line.  The ~ (tilda) showed that I was in my home directory.  But honestly that doesn't matter.  I've tried a directory pretty much anywhere.  I don't know what's going on here at all.

---

### Post by ozzyprv on 2010-05-13
> **Jose Catre-Vandis said:**
> frenchnoob is simply reiterating the original howto

Thank you Jose.
I haven't solve all my issue with the permission, etc....
After the break I took I will give it another try. Hope all of you are still around and ready to help :-)

thanks.

---

### Post by gibbylinks on 2010-06-09
When I use 

"sudo mount -v myserver:/dir /mnt"  in terminal it works and connects to my NAS drive with NFS.

BUT

If I try "sudo mount -t nfs myserver:/dir /mnt" I get an error
"mount.nfs: an incorrect mount option was specified"

and the same error if I try to use nfs in /etc/fstab

any ideas ?

Thanks

---

### Post by Steve Weeks on 2010-06-14
THANK YOU that was really useful and worked for me 1st time (with 10.4 Desktop on both NFS client and NFS server)

---

### Post by olivero1 on 2010-07-03
THANK YOU!!!

This worked for 10.4 and Freenas!:P

---

### Post by lemmy999 on 2010-08-03
I seem to hit a few problems with NFS every time I re-install ( must save my nfs settings once I have sorted this one out!!)

My /etc/exports file
```
/home/chris/Video 192.168.1.65 (rw,no_root_squash, async
```

Then ```
sudo mount alpha:/home/chris/Video /shared
```

mounts the share. This is confirmed here```
alpha:/home/chris/Video on /shared type nfs (rw,addr=192.168.1.91)
```

Clicking on /shared produces an empty folder.:(

Any ideas where I'm going wrong?

---

### Post by dmizer on 2010-08-03
> **lemmy999 said:**
> Any ideas where I'm going wrong?

A few things I see:
1) Your exports line has an extra space in it (there should be no space between 192.168.1.65 and the first parentheses). Also, the exports line is missing a parentheses (perhaps you neglected to copy it?).
2) Your exports line only has one IP address. This IP address needs to be the client computer's IP, not the server's IP. You're probably better off simply allowing the whole subnet.
3) The howto is old, so you'll need to add the "no_subtree_check" option to your exports line. This option was not necessary when the howto was written. So, your exports line should look like this:
```
/home/chris/Video 192.168.1.0/24(rw,no_root_squash,async,no_subtree_check)
```
4) In your mount line on your client, "/shared" should be an empty directory that exists in your client's actual directory structure. To check if it's there, open a terminal and type:
```
cd /&&ls
```
If you do not see "shared" listed, you either have the wrong path or you've forgotten to create the folder. Remember to include the entire path to the directory because /home/dmizer/shared is different from /shared for example. So your mount line should look like this:
```
sudo mount alpha:/home/chris/Video /full/path/to/shared
```

---

### Post by lemmy999 on 2010-08-04
@ Dmizer

1. Hadn't noticed the space between the IP and the parentheses:oops: and you are correct- I did a lousy job of cutting and pasting:)

2.I initially had the whole subnet allowed but narrowed it down to the one machine that I want to access the share.

3.Good point! The post may be old but its still a goodie! ( and I'll amend to include "no_subtree_check" as well)

4.I have definitely got an empty folder named "shared" in / ( but it could be in /home/chris). I'll make sure I know exactly where it is and then make sure i put the whole path in.

Thanks for your help

---

### Post by capo1949 on 2010-08-20
Hi All
Could someone please help me with the following problem;

I am using my desktop as server (ip 192.168.1.65) and laptop (ip 192.168.1.64) as client. Both machine are running Ubuntu Lucid.

I have followed the instructions at post 1 and the Server end looks to have gone well.My /etc/exports set up is;

/home 192.168.1.64(rw,no_root_squash,async)

However at the client end I am struggling, I established a directory of /mnt/home, and then tried to mount with

graham@graham-laptop:/$ sudo mount 192.168.1.65:/home /mnt/home
this successfully mounted, when I disabled the firewall on each machine (I will come back to this problem later)

I cannot get the following to run from the tutorial
graham@graham-laptop:~$ sudo /etc/init.d/nfs-common restart
sudo: /etc/init.d/nfs-common: command not found

I checked that the portmap nfs-common software had been installed 

Many thanks in anticipation

---

### Post by ozzyprv on 2010-09-08
Is there any way to implement NFS in this way:
folder1, owned by user1 (UID 1001), @server1
is accessed with rw privileges by two (or more) users
user2 (UID 1002) @clientA, and by
user3 (UID 1005) @cllientB ?

I want to set a file server that holds files accessible (rw) to several users at different clients.

Thanks.

---

### Post by daveleitz on 2010-10-02
I would like to add my appreciation for the Howto: NFS Server/Client post.  

Over the past month or so I've been moving to various flavors of Ubuntu on my three machines, gradually weaning myself off of XP.  Using the instructions in this thread I managed to set up one machine running Crunchbang 9.04 as NFS server and another running Ubuntu 10.04 as NFS client.  I thought I had all bases covered to tackle the last computer.  By this time I had already considered and rejected Samba and FTP/Zeroconfig setups.

On the final computer I set up Xubuntu 10.04.  For some reason, however, my attempts to get the server set up resulted in "Warning: /files/to/be/shared does not support NFS export" whenever I tried to restart the server.  Naturally, the client also failed to connect.  So, why, I wondered, would Crunchbang based on Ubuntu work for one machine while Xubuntu would not?  

As an aside, my disto choices were not arbitrary but based on hardware compatibilities and resource usages.  For example, when I put Xubuntu on my netbook, it seemed to be a perfect match.  Then I couldn't get it to work with NFS and no amount of Google searching seemed to help.  I decided to try Crunchbang on it, since Crunchbang seemed to work fine for my old Dell.  However, it just didn't "fit" too well on the netbook, and I had issues getting the wireless networking to connect reliably.  So, I put Xubuntu back on the netbook, again.  But I digress...

The whole point of this post is how I got my Xubuntu netbook to finally work as an NFS server.  When I Googled my problem the first time around, I recalled reading something to the effect that NFS wouldn't work with encrypted home folders.  This was just a single comment in a forum, so I wasn't sure how reliable this kind of information was.  Indeed, the first time I set up Xubuntu on the netbook, I went with the encrypted home folder option.  I figured, why not?  What's more, I was able to get FTP/Zeroconfig set up between my Ubuntu desktop and the Xubuntu netbook the first time around, but it was not capable of streaming media files like I had planned.  I really wanted to set up NFS.  So, on the second install of Xubuntu (after trying out Crunchbang), I left the home folder unencrypted.  I let the system get all its updates, got my restricted extras set up, and verified my wireless networking.  Then I set about installing the NFS server, setting up my exports, and voila!  It worked!  

So, if you get a message in your terminal that says "Warning: /filestobe/shared does not support NFS export", it may be because you have an encrypted folder.

---

### Post by dean9359 on 2010-10-16
Trying to set up NFS following instructions in one of the references in this thread.  Got everything to work correctly - except my Lucid NFS server will not mount my exported files at boot time.  It just displays a message "Cannot Mount /exports/devb".  I tried to enter the commands manually, but that failed as well.

The filesystems I'm trying to mount are on direct-attached 4-disk device.  Each disk is a separate filesystem.

I think the problem lies with the fstab entries for these filesystems.  According to the doc, to avoid having to manually enter a "mount --bind" command after each server reboot, include the following in fstab for each exported filesystem:
 
/media/sdb002 /exports/devb none bind 0 0 

Since there is no other reference to the export file in the boot files, I'm figuring this is the culprit.

Can anyone tell me how (and where) to properly issue the command that will cause these devices to be mounted and bound (binded? O:) )

---

### Post by gibbylinks on 2010-10-17
Hi Folks,

Just thought I'd throw my hat into the ring !!

I managed to get this working yesterday after a struggle. I was trying to connect to my icybox NAS drive and failing dismally. I have some observations which may help people.

Use the ```
showmount -e "ip.address"
  
[COLOR=Blue]showmount -e 192.168.2.111[/COLOR] returns on my system

Export list for 192.168.2.111:
/mnt/IDE1/music      *
/mnt/IDE1/public     *
/mnt/IDE1/email2     *
/mnt/IDE1/email1     *
/mnt/IDE1/photos     *
/mnt/IDE1/familytree *

``` To check and show what is being shared. One of my initial problems was caused by incorrectly naming the shared drive in the mount command.

Also I'm running [COLOR=Navy]Maverick 10.10[/COLOR], it would appear that this now uses [COLOR=Navy]NFS version 4[/COLOR] by default I couldn't get it to work until I stumbled on the "[COLOR=Red]vers[/COLOR]" option of the mount command. (see below for the command I finally got to work).

```
sudo mount -t nfs -o **[COLOR=Red]vers=3[/COLOR]**,rsize=8192,wsize=8192 192.168.2.111:/mnt/IDE1/music /mnt/nas
```Lastly use the "[COLOR=Red]-v[/COLOR]"  option with mount to start with, this is for "verbose" and will let you see any errors your getting. It's this option which put me onto the version being wrong. I can't stress this last bit enough.

I hope this can help anyone struggling. :)

---

### Post by Jose Catre-Vandis on 2010-10-17
> **dean9359 said:**
> Trying to set up NFS following instructions in one of the references in this thread.  Got everything to work correctly - except my Lucid NFS server will not mount my exported files at boot time.  It just displays a message "Cannot Mount /exports/devb".  I tried to enter the commands manually, but that failed as well.

The filesystems I'm trying to mount are on direct-attached 4-disk device.  Each disk is a separate filesystem.

I think the problem lies with the fstab entries for these filesystems.  According to the doc, to avoid having to manually enter a "mount --bind" command after each server reboot, include the following in fstab for each exported filesystem:
 
/media/sdb002 /exports/devb none bind 0 0 

Since there is no other reference to the export file in the boot files, I'm figuring this is the culprit.

Can anyone tell me how (and where) to properly issue the command that will cause these devices to be mounted and bound (binded? O:) )

Seems like you are trying to do two things at once? Break it down, resolve one part then move on.

First problem - mount your drives/partitions/filesystems on your server. Use fstab for this. Identify the type of filesystem, then use the correct syntax for mounting it. I suggest you create all your mountpoints in /media unless you have reason for them to go elsewhere. There is a good fstab howto in the Tuts section. You need to get this sorted first before you move on.

Second problem - exporting the shares - this should all be sweet if you follow the tutorial in this thread, however make note of the version issues in the post above my response here.

---

### Post by Metabaron on 2010-10-18
I use Lucid with 2.6.32 kernel and I have to use the sec=none mount option to be able to mount.

---

### Post by dean9359 on 2010-10-18
ok.  Think I figured this out.

bind cannot execute at this stage in the boot process.

Added ",bg"   to fstab line;         /media/sdb002 /exports/devb none bind,bg 0 0

This spawns a mount process that attempts to execute the mount in the background (for up to two minutes).

---

### Post by GJJ on 2010-10-23
Hi all,

I tried the procedure in the first post, but when I try to mount I keep getting the following error:

```
gertjan@gertjan-laptop:~$ sudo mount jsmcenter:/home/gertjan/Media /home/gertjan/JSM_Shares/
mount.nfs: /home/gertjan/JSM_Shares is busy or already mounted
```

Unfortunately, the files are not mounted. :(
The /etc/exports file on the server contains the line:

```
/home/gertjan/Media 192.168.1.0/24(rw,no_root_squash,async)
```

Also, the firewall allows nfs connection on both server and client (port 2049 enabled).

Does anyone have any ideas how to solve this?

Thanks!

---

### Post by Jose Catre-Vandis on 2010-10-24
> **GJJ said:**
> Hi all,

I tried the procedure in the first post, but when I try to mount I keep getting the following error:

```
gertjan@gertjan-laptop:~$ sudo mount jsmcenter:/home/gertjan/Media /home/gertjan/JSM_Shares/
mount.nfs: /home/gertjan/JSM_Shares is busy or already mounted
```

Unfortunately, the files are not mounted. :(
The /etc/exports file on the server contains the line:

```
/home/gertjan/Media 192.168.1.0/24(rw,no_root_squash,async)
```

Also, the firewall allows nfs connection on both server and client (port 2049 enabled).

Does anyone have any ideas how to solve this?

Thanks!

This might be a permissions issue. Try ensuring you have the same permissions for your share on both the client and server (I generally avoid trying to mount folders in a /home partition for this reason, especially if the owners are not the same and have different UIDs?) Also try using the IP addresses as opposed to host names to start off with. Also if you are on lucid on the server, check for the version fix as in the posts above this one.

---

### Post by GJJ on 2010-10-24
> **Jose Catre-Vandis said:**
> This might be a permissions issue. Try ensuring you have the same permissions for your share on both the client and server (I generally avoid trying to mount folders in a /home partition for this reason, especially if the owners are not the same and have different UIDs?) Also try using the IP addresses as opposed to host names to start off with. Also if you are on lucid on the server, check for the version fix as in the posts above this one.

Thanks for your reply!

I finally got it working by using IP adresses and disabling the firewall on the server. First I tried opening some ports, (111 and 2049 for example) but then it didn't work.

Disabling the firewall entirely is not such a big issue here, but I would like to be able to have it on. Are there any other ports that I need to open for this to work?

Thanks!

---

### Post by Jose Catre-Vandis on 2010-10-24
> **GJJ said:**
> Disabling the firewall entirely is not such a big issue here, but I would like to be able to have it on. Are there any other ports that I need to open for this to work?

Thanks!

This looks like a good place to start:
[http://tldp.org/HOWTO/NFS-HOWTO/security.html](http://tldp.org/HOWTO/NFS-HOWTO/security.html)

---

### Post by AlexanderDGreat on 2010-10-28
> Disabling the firewall entirely is not such a big issue here, but I would like to be able to have it on. Are there any other ports that I need to open for this to work?

Try to this: NFS Static Ports [http://ubuntuforums.org/showthread.php?t=352486]("http://ubuntuforums.org/showthread.php?t=352486")

---

### Post by daveleitz on 2010-11-09
I noticed a problem recently when my NFS client would lose its connection to the server for no apparent reason.  A look around the net indicates that it is a known problem in Lucid.  I'm not sure about Maverick since I am sticking with the LTS for now.

To reestablish the connection I had to reboot the client computer.  The server seems unaffected.  In one forum it was suggested that "udp" be added to the /etc/fstab file.

For example, I put "udp" at the end of this line in my /etc/fstab on my client computer:
my-laptop.local:/home/me /home/metoo/Shared nfs rsize=8192,wsize=8192,timeo=14,intr,udp

That said, I'm not sure what it does exactly.  I do know that my client hasn't misplaced its connection since I made the change, so it must be a good thing.  ;)

---

### Post by daveleitz on 2010-11-16
Ok, so putting "udp" still doesn't completely cure the problem, but it occurs less often than before at least.

---

### Post by orlenok41 on 2010-12-10
Hello,

I have the following NFS configuration. On the server, I have mounted a hard drive (physically attached) in /media/data_disk, and then I export /media using the following line in /etc/exports

 /media       *(nohide,rw,sync,no_subtree_check)

If I mount it on the client using the following in /etc/fstab

192.168.1.5:/media /media/media nfs defaults 0 0


then I can see /media/media/data_disk but the data_disk folder is empty (ie I can only see the server's mount point and not its contents). I thought the nohide option should do the trick but it doesn't seem to work. Any clues as to how I can make the mounted filesystem on the server appear on the nfs client?

Thanks in advance.

---

### Post by dmizer on 2010-12-12
> **orlenok41 said:**
> Hello,

I have the following NFS configuration. On the server, I have mounted a hard drive (physically attached) in /media/data_disk, and then I export /media using the following line in /etc/exports

 /media       *(nohide,rw,sync,no_subtree_check)

If I mount it on the client using the following in /etc/fstab

192.168.1.5:/media /media/media nfs defaults 0 0


then I can see /media/media/data_disk but the data_disk folder is empty (ie I can only see the server's mount point and not its contents). I thought the nohide option should do the trick but it doesn't seem to work. Any clues as to how I can make the mounted filesystem on the server appear on the nfs client?

Thanks in advance.
Did you create a mount point in /etc/fstab for the data_disk? If so, please post the server's /etc/fstab.

---

### Post by gfunkdave on 2011-01-15
I have an Ubuntu NFS server with one client, a SCO Unix server. My /etc/exports line in Ubuntu is:

```

/media/data/meadows/dtechBackup zeus(rw,sync,no_subtree_check,all_squash,anonuid=1014,anongid=1014)

```

The directory mounts just fine and I can browse it. uid/gid 1014 are the uid/gid of my backup user on Ubuntu. If I'm logged into SCO as root, I can create/delete files just fine. But if I log into SCO as a regular user in a new group I created with gid 1014, creating a file gives the error

```

$ touch /dtechBackup/helloworld
touch: cannot change times on /dtechBackup/helloworld: Permission denied (error 13)

```

The /dtechBackup directory in SCO has permissions 775. Its uid and gid are both 1014. There is no uid 1014 in SCO, but I did create a group with gid 1014.

Does anyone know what's going on here?

Thanks!

edit: added new things I figured out

---

### Post by dmizer on 2011-01-16
> **gfunkdave said:**
> I have an Ubuntu NFS server with one client, a SCO Unix server. My /etc/exports line in Ubuntu is:

```

/media/data/meadows/dtechBackup zeus(rw,sync,no_subtree_check,all_squash,anonuid=1014,anongid=1014)

```

The directory mounts just fine and I can browse it. uid/gid 1014 are the uid/gid of my backup user on Ubuntu. If I'm logged into SCO as root, I can create/delete files just fine. But if I log into SCO as a regular user in a new group I created with gid 1014, creating a file gives the error

```

$ touch /dtechBackup/helloworld
touch: cannot change times on /dtechBackup/helloworld: Permission denied (error 13)

```

The /dtechBackup directory in SCO has permissions 775. Its uid and gid are both 1014. There is no uid 1014 in SCO, but I did create a group with gid 1014.

Does anyone know what's going on here?

Thanks!

edit: added new things I figured out

Looks like you'll just need to add the new user to the 1014 group?

---

### Post by gfunkdave on 2011-01-16
> **dmizer said:**
> Looks like you'll just need to add the new user to the 1014 group?

Indeed, that's what I needed to do. Thanks! I hadn't quite understood how file permissions over NFS work. It makes sense that the creator of the file would need to be the owner. :)

---

### Post by kalyp on 2011-01-27
Hello,

I'm having a problem that maybe cannot be solved, but I thought I'd ask in case... (sorry if the solution is somewhere along this thread, I haven't been able to find it).
I mount NFS network shares on my computer (using autofs) and it all worked great until the network admins ask me to connect using gid 20 (dialout) instead of mine (1000). Something about group permissions they need to have.

I could change my gid to 20 but would rather connect to the shares with 20, keeping my local gid to 1000. I've read stuff about NFSv4 and id mapping but have no idea how to set up that - I assume it's on the server side which I don't have access to. If I try a "sudo mount -t nfs4 (etc)" I get "mount.nfs4: Protocol not supported" so I assume they don't use it.

So is it possible to change my gid on the NFS share without having any possibility, on my side, to modify it?
Or do I have no other option than modifying my gid to 20 even locally?

Thanks....

---

### Post by gfunkdave on 2011-01-27
> **kalyp said:**
> 
So is it possible to change my gid on the NFS share without having any possibility, on my side, to modify it?
Or do I have no other option than modifying my gid to 20 even locally?


I think you have to change your local gid to 20. The NFS client just passes along your current uid/gid to the NFS server.

---

### Post by dmizer on 2011-01-28
> **gfunkdave said:**
> I think you have to change your local gid to 20. The NFS client just passes along your current uid/gid to the NFS server.

No, all you need to do is add a uid/gid 20 to your system and add your current user to the gid 20. Then mount the NFS server with uid/gid 20 instead of 1000.

---

### Post by kalyp on 2011-01-28
> **dmizer said:**
> No, all you need to do is add a uid/gid 20 to your system and add your current user to the gid 20. Then mount the NFS server with uid/gid 20 instead of 1000.

That's exactly what I wanted to do but couldn't figure out how.
I'm already part of gid 20 (dialout) but can't find the way to mount the server with gid 20 instead of 1000. Adding "gid=20" to my autofs configuration works with samba shares, not NFS...
Thanks!!!

---

### Post by mucho_maze on 2011-01-30
> **quad3d@work said:**
> Had some serious speed problem with Samba. Setting up NFS from your guide works well! Now I'm doing 30-40Mb (gigabit network) per sec instead of 1-3Mb with Samba. Thanks!

Same here (Ubuntu server 10.04 LTS and Ubuntu client 10.04 LTS) I even tried transferring a file at a speed of 45 mb/s. The file was 3.3 GB. Minimum speed is about 30 mb/s for larger files.

---

### Post by oldfart101 on 2011-02-17
having problems .. installed a new hd - volume name = L-Films
I want to share the whole of the drive to all IP addresses on the network - I can see the drive from other machines, but can't see any files. Obviously I have done something wrong!

/etc/exports:-
```
/Lfilms 192.168.1.0/24(rw,no_root_squash,async)
``````
andrew@linuxpc:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/andrew/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=andrew)
/dev/sdb1 on /media/L-Films type ext2 (rw,nosuid,nodev,uhelper=udisks)
nfsd on /proc/fs/nfsd type nfsd (rw)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)

```set permissions for the drive & dirs to 777

I also have /media/L-Films 

any ideas please??

---

### Post by dmizer on 2011-02-17
> **oldfart101 said:**
> having problems .. installed a new hd - volume name = L-Films

Did you create a mountpoint in /etc/fstab for your new hard drive? If not, you'll be unable to share it via NFS.

---

### Post by Jose Catre-Vandis on 2011-02-18
> **oldfart101 said:**
> 

/etc/exports:-
```
/Lfilms 192.168.1.0/24(rw,no_root_squash,async)
```


Lfilms or L-Films ???

Check spelling and case for directories and exports file on server ??

---

### Post by NeilR on 2011-04-04
> **dmizer said:**
> Did you create a mountpoint in /etc/fstab for your new hard drive? If not, you'll be unable to share it via NFS.

I seem to be having the same problem here.  I have a Ubuntu 10.04.2 LTS Server, and a Kubuntu 10.4.2 LTS client.

I want the client to see, in one mount point, all the mounted drives on the Ubuntu Server, each drive as a folder under the mount point.

In other words, my Server looks like this:

/mnt/disks/disk1
/mnt/disks/disk2
... etc
/mnt/disks/disk5

The disks are mounted to disk1, disk2, etc.

I tried to set the mount point (within the client's fstab)to the 'disks' folder but all I see is an empty disk1 and disk2 folder. 

Am I correct that this cannot be done via NFS?  I seem to be able to do this with cifs without issue.  [s]If I cannot set up a common mount point then it seems that I would have to set up a mount to each top level folder in each disk, which would be overly cumbersome.[/s]

OK, let me changed that crossed out thought :-).  I see that on the client I can mount 'disk1' and 'disk2' but not 'disks'.  Since both are local folders above the mount point I guess I fail to see why I can mount disk1 but not disks.  Unless it is because disks contains two different drives (and server mounts) under it?

---

### Post by dmizer on 2011-04-04
> **NeilR said:**
> I seem to be having the same problem here.  I have a Ubuntu 10.04.2 LTS Server, and a Kubuntu 10.4.2 LTS client.

I want the client to see, in one mount point, all the mounted drives on the Ubuntu Server, each drive as a folder under the mount point.

On the server, please post the output of:
```
df -Th
```
Also, please post the contents of /etc/fstab and /etc/exports

---

### Post by xPreatorianx on 2011-04-05
Well I posted this in a separate topic and no one seems to want to respond. So hopefully since this is a dedicated topic on it, I will be able to get some help. If I should not have posted here I apologize in advance. 

I'm running Ubuntu 10.10 latest IIRC and I'm trying to setup a network  boot using NFS and TFTP for my PS3 so I can boot gentoo. I can't seem to  find where the problem is. I believe I have all the ports forwarded  correctly but I'm not sure. I have all the files correctly edited from  the guide I followed and it does boot into the vmlinux image I guess.  But it can't mount the NFS directory.

I'm a noob when it comes to linux so I'm still learning. But I do learn  quickly. Hopefully these are the correct logs you guys need because I  had to take a video with my camera to get the logs from my PS3. I know I  have my PS3 configured correctly besides maybe a port or two in  relation to NFS or TFTP so I don't need any help with that, at least I  hope.  I just need help server side.

Here are the logs from my PS3, ubuntu machine,  and all my edited files.

Here's where I have my files stored for tftp, nfs, and my mnt. 

```
/mnt/experimental 
```vmlinux
```
/var/lib/tftpboot
```IP's I'm using : 
Ubuntu machine with nfs server : 192.168.1.2
/mnt/experimental is on : 192.168.1.2
PS3 is on : 192.168.1.3

I also have latent IP's like 192.168.1.4 because I was troubleshooting.  Please let me know where I am going wrong. Thank you for your help in  advance. 



[37.474692] rpcbind: server 192.168.1.3 not responding. timed out
[37.476342] Root-NFS: Unable to get nfsd port number from server, using default.
[37.479697] Looking up port of RPC 100005/1 on 192.168.1.3
[72.646690] rpcbind : Server 192.168.1.3 not responding, timed out
[72.548512] Root-NFS: Unable to get mountd port number from server, using default.
[107.610727] Root-NFS : Server returned error -110 while mounting /mnt/experimental
[107.622308] VFS : Unable to mount root fs via NFS, trying floppy.
[107.624762] VFS : Cannot open root device "nfs" or unknown-block (2,0)
[107.626594] Please append a correct  "root=" boot option; here are the  available partitions : (there aren't any it just does a stack trace and  freezes. 

dhcpd.conf 

```
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

#default-lease-time 600;
#max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
#log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#
#
#
#


default-lease-time 600;
max-lease-time 7200;
ddns-update-style none;
authoritative;
log-facility local7;
subnet 192.168.1.0 netmask 255.255.255.0{ 
range 192.168.1.1 192.168.1.254;
}
next-server 192.168.1.2;
filename "kboot.conf";
option routers 192.168.1.1;

host PS3{
hardware ethernet 00:1f:a7:81:1d:72; # MAC address of PS3
fixed-address 192.168.1.3; # PS3 IP address, you decide.
}

```exports 
```
# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/mnt/experimental 192.168.1.2(rw,async,no_root_squash,no_subtree_check,anonuid=0,anongid=0)
#/mnt/experimental 192.168.1.4/16(rw,async,no_root_squash,no_subtree_check,anonuid=0,anongid=0) 

```kboot.conf 
```
linux='vmlinux video=ps3fb:mode:2 root=/dev/nfs rw ip=dhcp nfsroot=192.168.1.3:/mnt/experimental panic=5' 
```rpcinfo 
```
prea@prea-dev:~$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  59496  status
    100024    1   tcp  58250  status
    100021    1   udp  37426  nlockmgr
    100021    3   udp  37426  nlockmgr
    100021    4   udp  37426  nlockmgr
    100021    1   tcp  33013  nlockmgr
    100021    3   tcp  33013  nlockmgr
    100021    4   tcp  33013  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100227    2   tcp   2049
    100227    3   tcp   2049
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100227    2   udp   2049
    100227    3   udp   2049
    100005    1   udp  47827  mountd
    100005    1   tcp  50681  mountd
    100005    2   udp  47827  mountd
    100005    2   tcp  50681  mountd
    100005    3   udp  47827  mountd
    100005    3   tcp  50681  mountd

```

---

### Post by dmizer on 2011-04-05
@xPreatorianx

You have your exports restricted to share files only to your server. You should change your exports to this:
```
# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/mnt/experimental [COLOR="Red"]192.168.1.0/24[/COLOR](rw,async,no_root_squash,no_subtree_check,anonuid=0,anongid=0)
```

Also, this is very worrying.
> **xPreatorianx said:**
> I believe I have all the ports forwarded  correctly but I'm not sure.
Port forwarding is for allowing Internet traffic onto your LAN through your firewall, not for allowing LAN traffic through your firewall.

If you have enabled port forwarding on your router, you should disable it ASAP.

---

### Post by xPreatorianx on 2011-04-05
> **dmizer said:**
> @xPreatorianx

You have your exports restricted to share files only to your server. You should change your exports to this:
```
# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/mnt/experimental [COLOR=Red]192.168.1.0/24[/COLOR](rw,async,no_root_squash,no_subtree_check,anonuid=0,anongid=0)
```Also, this is very worrying.

Port forwarding is for allowing Internet traffic onto your LAN through your firewall, not for allowing LAN traffic through your firewall.

If you have enabled port forwarding on your router, you should disable it ASAP.

Thanks I'll look into it tomorrow. I already disabled the ports anyways because they weren't helping. I was just trying everything I could to see what was going on.

EDIT: I'm still getting the port errors. Here's what I'm getting :
[37.474692] rpcbind: server 192.168.1.3 not responding. timed out
[37.476342] Root-NFS: Unable to get nfsd port number from server, using default.
[37.479697] Looking up port of RPC 100005/1 on 192.168.1.3
[72.646690] rpcbind : Server 192.168.1.3 not responding, timed out
[72.548512] Root-NFS: Unable to get mountd port number from server, using default.
[107.610727] Root-NFS : Server returned error -110 while mounting /mnt/experimental
[107.622308] VFS : Unable to mount root fs via NFS, trying floppy.
[107.624762] VFS : Cannot open root device "nfs" or unknown-block (2,0)
[107.626594] Please append a correct  "root=" boot option; here are the   available partitions : (there aren't any it just does a stack trace and   freezes.

---

### Post by dmizer on 2011-04-06
After you change the exports file, you must run the following commands:
```
sudo exportfs -a
```
and
```
sudo /etc/init.d/nfs-kernel-server restart
```

Also double check to make sure that the NFS server is still actually at 192.168.1.3 because with DHCP, that could change at any time unless you have a permanent lease assigned to the server's MAC address.

---

### Post by beebaa157 on 2011-04-06
Hi......
It was good to see your post. It is such an important topic and ignored by so many, even professionals. I thank you to help making people more aware of possible issues. Great stuff as usual...

---

### Post by NeilR on 2011-04-06
> **dmizer said:**
> On the server, please post the output of:
```
df -Th
```
Also, please post the contents of /etc/fstab and /etc/exports

dmizer, thanks for the help!  Sorry for the delay; life's adventures intervened and I had to unwind my work-around and reconfigure this.

Here is the output of df -Th:

```
neil@FSUBSV1004:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/mapper/FSUBSV1004-root
              ext4    7.3G  1.7G  5.2G  25% /
none      devtmpfs    497M  240K  497M   1% /dev
none         tmpfs    502M     0  502M   0% /dev/shm
none         tmpfs    502M  504K  501M   1% /var/run
none         tmpfs    502M     0  502M   0% /var/lock
none         tmpfs    502M     0  502M   0% /lib/init/rw
/dev/sda1     ext2    228M   47M  170M  22% /boot
/dev/sdb1     ext4     53G   23G   27G  46% /mnt/disks/disk2
/dev/sdc1     ext4     51G  180M   48G   1% /mnt/disks/disk3

```

Here is the server's /etc/exports:

```
/mnt/disks	*(async,no_root_squash,rw,nohide)
```

Here is the client's /etc/fstab:

```
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=ec70d8b3-b833-4b3d-8529-f6d3b865ab98 /               ext4    errors=remount-ro 0       1
UUID=78b27841-8f16-49ec-b74c-500c27d3e482 none            swap    sw              0       0
//192.168.1.201/iTunesMusic /home/neil/cifs/s300/itunes cifs credentials=/home/neil/.smbpasswd 0 0
//192.168.1.15/disks /home/neil/cifs/fsubsv1004 cifs credentials=/home/neil/.smbpasswd 0 0

```

I want to reiterate that if I configure separate client mounts to disk2 and disk3 on the server (only one server disk per mount) then everything works fine, verifying that I basically have NFS working properly.  I only have a problem trying to mount two server disks in one NFS mount on the client, and something posted recently to this thread suggested that single mount point was just not possible.

---

### Post by xPreatorianx on 2011-04-06
> **dmizer said:**
> After you change the exports file, you must run the following commands:
```
sudo exportfs -a
```and
```
sudo /etc/init.d/nfs-kernel-server restart
```Also double check to make sure that the NFS server is still actually at 192.168.1.3 because with DHCP, that could change at any time unless you have a permanent lease assigned to the server's MAC address.

Still doing the same thing. It keeps spitting out errors about not being able to find the ports. I checked everything. I'm at wits end. Why is it so hard to netboot something?

---

### Post by dmizer on 2011-04-06
> **NeilR said:**
> Here is the client's /etc/fstab:
Actually, I need the server's /etc/fstab to see the how the disks are mounted on the server.

> **xPreatorianx said:**
> Still doing the same thing. It keeps spitting out errors about not being able to find the ports. I checked everything. I'm at wits end. Why is it so hard to netboot something?

Did you install portmap?
```
sudo apt-get install portmap
```

---

### Post by NeilR on 2011-04-06
> **dmizer said:**
> Actually, I need the server's /etc/fstab to see the how the disks are mounted on the server.


Here ya go!  Server's /etc/fstab

```
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/FSUBSV1004-root /               ext4    errors=remount-ro 0       1
UUID=9eb59e31-794a-476f-8992-6a79e12b9be9 /boot           ext2    defaults        0       2
/dev/mapper/FSUBSV1004-swap_1 none            swap    sw              0       0
/dev/sdb1  /mnt/disks/disk2  ext4  nosuid,noexec,nodev  0  1
/dev/sdc1  /mnt/disks/disk3  ext4  user,nosuid,noexec,nodev  0  0
```

---

### Post by xPreatorianx on 2011-04-06
> **dmizer said:**
> Actually, I need the server's /etc/fstab to see the how the disks are mounted on the server.



Did you install portmap?
```
sudo apt-get install portmap
```

Yes portmap is installed. RPCinfo says it is working as well from my previous logs. At least I guess rpcinfo is saying it's working. Hell I don't know how to read half of these logs. So I have no idea lol.

EDIT: See?

```
prea@prea-dev:~$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  59496  status
    100024    1   tcp  58250  status
    100021    1   udp  37426  nlockmgr
    100021    3   udp  37426  nlockmgr
    100021    4   udp  37426  nlockmgr
    100021    1   tcp  33013  nlockmgr
    100021    3   tcp  33013  nlockmgr
    100021    4   tcp  33013  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100227    2   tcp   2049
    100227    3   tcp   2049
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100227    2   udp   2049
    100227    3   udp   2049
    100005    1   udp  47827  mountd
    100005    1   tcp  50681  mountd
    100005    2   udp  47827  mountd
    100005    2   tcp  50681  mountd
    100005    3   udp  47827  mountd
    100005    3   tcp  50681  mountd


```

---

### Post by xeddog on 2011-04-08
I have seen many people having issues with an access denied error when trying to mount an nfs share and I thought I would just add my experience.  I have been trying to get my Popcorn Hour mounted using nfs and could not seem to get past the access denied error UNTIL I added nfsvers=3 to the end of the line in fstab like this:
```
Popcorn:/share	/media/Popcorn nfs rw,rsize=8192,wsize=8192,intr,nfsvers=3
```
After adding that it works fine.

For reference, the Popcorn Hour runs some flavor of Linux, and my computer is running Ubuntu Maverick.

Wayne

---

### Post by xPreatorianx on 2011-04-09
Still getting the exact same errors :S. This is extremely frustrating.

---

### Post by Jose Catre-Vandis on 2011-04-09
@ NeilR

You don't have an nfs mount point in your clients fstab file - won't work without one :)

anyway:

This is how I do it, with a server with 4 disks in it. You do some of the work on the client side, so perhaps not quite what your after (?) but it works.

**Server**

***fstab***

/dev/sda1 /mnt/disk1
/dev/sdb1 /mnt/disk2
/dev/sdc1 /mnt/disk3
/dev/sdd1 /mnt/disk4

***exports*** (10.10.10.1 is my subnet, so the commands server all Pcs on that subnet)

/mnt/disk1 10.10.10.1/24(rw,no_root_squash,async,no_subtree_check)
/mnt/disk2 10.10.10.1/24(rw,no_root_squash,async,no_subtree_check)
/mnt/disk3 10.10.10.1/24(rw,no_root_squash,async,no_subtree_check)
/mnt/disk4 10.10.10.1/24(rw,no_root_squash,async,no_subtree_check)

**Client**
[B][I]
directories:[/I][/B]

/mnt
/mnt/disks
/mnt/disks/disk1
/mnt/disks/disk2
/mnt/disks/disk3
/mnt/disks/disk4

***fstab*** (10.10.10.70 is my server IP)

10.10.10.70:/mnt/disk1 /mnt/disks/disk1 nfs rsize=8192,wsize=8192,timeo=14,intr,bg
10.10.10.70:/mnt/disk2 /mnt/disks/disk2 nfs rsize=8192,wsize=8192,timeo=14,intr,bg
10.10.10.70:/mnt/disk3 /mnt/disks/disk3 nfs rsize=8192,wsize=8192,timeo=14,intr,bg
10.10.10.70:/mnt/disk4 /mnt/disks/disk4 nfs rsize=8192,wsize=8192,timeo=14,intr,bg

I always use IP addresses to avoid translation problems, and a word of warning, this is on a server running Jaunty / nfs3, so your experience might be different!

However, your client should end up with a folder "disks" with disks 1-4 inside it, all mounted :)

---

### Post by Jose Catre-Vandis on 2011-04-09
@ xPretorianx

You haven't got another dhcp server running somewhere - e.g. on your router?

Have you tried netbooting a PC as opposed to a PS3, just to eliminate that variable?

Also, can you boot up a LIVE CD or similar on the PS3, and try a more straight forward NFS share scenario? Might give some pointers ? (Like the first page of this howto)

Try fixing all your IP addresses, it looks like you are using IP addresses throughout (as opposed to hostnames)

Review the versions of NFS running / expected, read back a couple of pages on this thread for some detail about this.

---

### Post by NeilR on 2011-04-09
Jose,

Thanks for the suggestion.  That was exactly the work-around I mentioned in my first post (but did not elaborate).  Even the names are the same :D

I liked my first idea because it would eliminate the need to modify the client fstab files when new drives are added.  Also I was just curious if that higher level mount could work. Apparently not, and it's not worth any more effort.

---

### Post by dmizer on 2011-04-09
> **xPreatorianx said:**
> Yes portmap is installed. RPCinfo says it is working as well from my previous logs. At least I guess rpcinfo is saying it's working.
Have you tried directly mounting these NFS shares (rather than trying to do a net-boot)? If the shares work directly, then the problem is with your LTSP server configuration.

> **NeilR said:**
> Jose,

Thanks for the suggestion.  That was exactly the work-around I mentioned in my first post (but did not elaborate).  Even the names are the same :D

I liked my first idea because it would eliminate the need to modify the client fstab files when new drives are added.  Also I was just curious if that higher level mount could work. Apparently not, and it's not worth any more effort.

I have been busy so I haven't done much work on this yet. I have found nothing anywhere which indicates that it's impossible to do what you want to do. I looked at a lot of NFS documentation and found nothing yet. So, I plan to try your configuration on my server at home.

---

### Post by Jose Catre-Vandis on 2011-04-10
> **NeilR said:**
> Jose,

Thanks for the suggestion.  That was exactly the work-around I mentioned in my first post (but did not elaborate).  Even the names are the same :D

I liked my first idea because it would eliminate the need to modify the client fstab files when new drives are added.  Also I was just curious if that higher level mount could work. Apparently not, and it's not worth any more effort.
[s]I am not sure why it doesn't work for you (the way you want to do it). I have been able to nfs share the whole root system that all my other nfs shares are mounted to on the server, and that works OK. I know that you can't symlink directories and nfs share them....Try mounting all the disks directly to /mnt and then try sharing /mnt, (you don't necessarily need the /mnt/disks directory), see what happens. Go back and check your exports file again, and make sure everything is right.[/s]

Sorry the above is wrong, any nfs mounts don't show up :?
(I used the same names for everything to remove confusion ;) )

---

### Post by xPreatorianx on 2011-04-10
> **Jose Catre-Vandis said:**
> @ xPretorianx

You haven't got another dhcp server running somewhere - e.g. on your router?

Have you tried netbooting a PC as opposed to a PS3, just to eliminate that variable?

Also, can you boot up a LIVE CD or similar on the PS3, and try a more straight forward NFS share scenario? Might give some pointers ? (Like the first page of this howto)

Try fixing all your IP addresses, it looks like you are using IP addresses throughout (as opposed to hostnames)

Review the versions of NFS running / expected, read back a couple of pages on this thread for some detail about this.

I'll have to find another version of gentoo as this one is PPC because of the PS3. But I'll test it. 

I'll try directly using a LIVECD as well. 

Also I have tried mounting directly but I'm not sure if I have the command correct. Can someone tell me what the command is just for my system? Like give me an example like mount 192.168.1.2(my internal IP.) /mnt/experimental. Basically give me the command but with all my info. That way I can't screw it up. Like I said I'm a newbie, but I pick things up quickly. 

Also I have DHCP disabled on my router, but I'm using my router's info for DHCP. Should I use my own subnet that I make up? Or through DNSMasq or something?

---

### Post by Jose Catre-Vandis on 2011-04-10
> **xPreatorianx said:**
> I'll have to find another version of gentoo as this one is PPC because of the PS3. But I'll test it. 

I'll try directly using a LIVECD as well. 

Also I have tried mounting directly but I'm not sure if I have the command correct. Can someone tell me what the command is just for my system? Like give me an example like mount 192.168.1.2(my internal IP.) /mnt/experimental. Basically give me the command but with all my info. That way I can't screw it up. Like I said I'm a newbie, but I pick things up quickly. 

Also I have DHCP disabled on my router, but I'm using my router's info for DHCP. Should I use my own subnet that I make up? Or through DNSMasq or something?

See my post to NeilR (one page back) regarding syntax for server and client

If your routers dhcp is disabled, you should be OK, but it might be worth trying a different subnet as the machines could be looking for their address in the wrong place (can't verify this, maybe a guru can?)

---

### Post by dryder on 2011-05-13
Hi,

I know it can be frustrating explaining things in detail what to many is simple.

Regretfully, I find my current problem is driving me nuts.

I bought a ReadyNAS Ultra - it is set up for CIFS and NFS. It works fine in XP.
But I'm running 10.04 64 bit. I can access it, write to it etc through the browser interface without a problem.

I am not running a NFS server - only clients. 3 Ubuntu 10.04 boxes.

But my problems are:
1. I have had it mount the shares in /mnt and in my /home/david folders depending on my fstab entry. Always, it is read only and as I'm using it as a file sharing device I need it read write when mounted through fstab.


2. I don't want to clutter up my desktop with folder icons so I would prefer to mount it in /mnt/ with read write permission. I would create links to each folder in /mnt in /home/david.

3. The NAS is best used in linux using NFS than CIFS. No argument with me there.

4. I have installed nfs-common and portman. I interpret the Howto as two parts: either a NFS Server or a NFS client. I assume my NAS is the server so I don't install software on it.

5. My credentials file exists and is correct (though I'm not using it in NFS).

6. I  have noticed the NAS assigned UID for me is 1002 whereas in 10.04 my UID is 1000. I can't change it in the NAS.
My fstab entry is:> ## ReadyNAS Ultra 2
192.168.0.7:/Finance /home/david/NAS_Finance nfs nfsvers=3,rsize=65536,wsize=65536,tcp,noatime,intr

The bottom line - I can't get it to mount rw, only read only. It's been two weeks of reading and trying and I am now going round in circles. Is anybody able to help please?

David

---

### Post by Jose Catre-Vandis on 2011-05-16
> **dryder said:**
> Hi,

I know it can be frustrating explaining things in detail what to many is simple.

Regretfully, I find my current problem is driving me nuts.

I bought a ReadyNAS Ultra - it is set up for CIFS and NFS. It works fine in XP.
But I'm running 10.04 64 bit. I can access it, write to it etc through the browser interface without a problem.

I am not running a NFS server - only clients. 3 Ubuntu 10.04 boxes.

But my problems are:
1. I have had it mount the shares in /mnt and in my /home/david folders depending on my fstab entry. Always, it is read only and as I'm using it as a file sharing device I need it read write when mounted through fstab.


2. I don't want to clutter up my desktop with folder icons so I would prefer to mount it in /mnt/ with read write permission. I would create links to each folder in /mnt in /home/david.

3. The NAS is best used in linux using NFS than CIFS. No argument with me there.

4. I have installed nfs-common and portman. I interpret the Howto as two parts: either a NFS Server or a NFS client. I assume my NAS is the server so I don't install software on it.

5. My credentials file exists and is correct (though I'm not using it in NFS).

6. I  have noticed the NAS assigned UID for me is 1002 whereas in 10.04 my UID is 1000. I can't change it in the NAS.
My fstab entry is:

The bottom line - I can't get it to mount rw, only read only. It's been two weeks of reading and trying and I am now going round in circles. Is anybody able to help please?

David

A couple of things you could try:

Create maybe two users, so that you have a user with the UID 1002 and try to connect as that user?

Try mounting somewhere other than your home directory on your client, e.g. /media/NAS_Finance

---

### Post by dryder on 2011-05-18
Thanks Jose.

---

### Post by prudy on 2011-11-03
Why is the portmapper required on the client?

---

### Post by Jose Catre-Vandis on 2011-11-04
> **prudy said:**
> Why is the portmapper required on the client?

Simple answer: to make nfs work ;)

---

### Post by chrisknowles on 2011-12-29
> **mike3k said:**
> If you're connection to a Linux NFS server from Mac OS X, you need to specify 'insecure' in your exports and map the user IDs since Macs use uid 501 for the first regular user. For my /etc/exports I use:

/home   192.168.0.0/255.255.255.0(rw,async,insecure,all_squash,anonuid=1000,anongid=1000)

For the record, this worked very well for me!

---

### Post by hmf1 on 2012-03-11
Problems with folder time/date stamps

I succeed in mounting my QNAP 412 folder with 
192.168.2.100:/folder /media/target_folder nfs defaults,user,auto,noatime 0 0

When I sync folders, I do not keep original date/time stamp of  folders and subfolders that are copied from a PC to the QNAP.   

Everytime I copy a folder to QNAP, folder/subfolder directory all  acquire the exact same date/time stamp - the time they were copied over.  The files themselves retain the original date/time stamp - but the  folders still create a problem.

(I tried with CIFS, and got the same problem)

Any help?

---

### Post by dryder on 2012-03-13
Post deleted by authour.

---

### Post by bxdobs on 2012-04-19
I am struggling with this ... I have an XP Pro SP3 OS running on a Lenovo Laptop ... this has VMplayer 4.0.2 running on it with UBUNTU 10.04.4 ... I have installed the NFS client 3.5 in XP PRO. 

I can ping Ubuntu from XP and ping XP from Ubuntu ... when I go to Map Network Drive in XP and Browse, it shows the NFS Network ... drilling down into this I find the /etc share I set up ... it gets to the login and suggests I am logged in but when I go finish XP comes back and says this network path cannot be found ... I am thinking the above example is for mounting WINDOWS shares in UBUNTU ... I need to do this the other way round

---

### Post by Jose Catre-Vandis on 2012-04-20
Where is the server? Is it on the VM Ubuntu or on another machine? If the former I can't see the point in trying to share directories this way unless you are just trying to make it work for the sake of it (I do that a lot!!). The usual practice of sharing under vmware should suffice. If the latter, can you setup the vm Ubuntu as an NFS client and access the server shares directly, or is the vm closed to your LAN?

Although it can be made to work, NFS on XP is a bit hit and miss and just not worth the effort when we have samba ;)

---

### Post by dmizer on 2012-04-21
> **bxdobs said:**
> I am struggling with this ... I have an XP Pro SP3 OS running on a Lenovo Laptop ... this has VMplayer 4.0.2 running on it with UBUNTU 10.04.4 ... I have installed the NFS client 3.5 in XP PRO. 

I can ping Ubuntu from XP and ping XP from Ubuntu ... when I go to Map Network Drive in XP and Browse, it shows the NFS Network ... drilling down into this I find the /etc share I set up ... it gets to the login and suggests I am logged in but when I go finish XP comes back and says this network path cannot be found ... I am thinking the above example is for mounting WINDOWS shares in UBUNTU ... I need to do this the other way round

Take a look here: [http://sagehacks.wordpress.com/2009/01/21/howto-mount-nfs-shares-under-windows-7/](http://sagehacks.wordpress.com/2009/01/21/howto-mount-nfs-shares-under-windows-7/). Seems that you'll also have to install Client Services for NFS in order to get this to work.

Also, VMware has it's own share functionality that will allow you to share files between the virtual client (in your case Ubuntu) and the host (Windows). You may find this method to be easier than trying to set up NFS client in Windows.
[http://www.vmware.com/support/ws4/doc/running_sharefold_ws.html](http://www.vmware.com/support/ws4/doc/running_sharefold_ws.html)

---

### Post by supriya swapnam on 2012-05-10
how to get the mounted path of /etc/fstab after creating new ISO image with remastersys in ubuntu


I mouted a path in ubuntu client 
/etc/fstab i.e  my.web.com:/usr/INVENTORY	 /usr/my/inventory nfs	rw,auto	0	0  
but I am not able to find this path after creating new ISO image with remastersys.. , it is missing their when i install new iso image of ubuntu .

please anyone can help me on this..

---

### Post by Jose Catre-Vandis on 2012-05-14
@ supriya swapnam

this is a remastersys question. I would guess that you are not getting the /etc/fstab you want into the new image. You'll need to figure out how to do this, so that it carries through to the new image. Easy if it was in the home folder, but not so with system folders?

---

### Post by hanhanafi on 2012-05-21
Hello, I have some problem with my NFS server. 
I can't configure NFS with IPV6.
Can you tell me how to solve it? 
Sorry my english is bad :D

---

### Post by Jose Catre-Vandis on 2012-05-21
Do you definitely need IPV6 ?  Does NFS work with IPV4 ?

---

### Post by hanhanafi on 2012-06-04
Yes, jose. I really need it. I just want to compare it.  I already done with IPV4, and i have some problem with IPV6.. I don't know how to configure it :(

---

### Post by MocroNL on 2012-08-28
I want to make a storage server with with nfs on ubuntu 11.10. Is this the correct guide for making a storage server??

---

### Post by rasputin23 on 2013-02-01
Thank you for posting this! Worked perfectly for me, although I could not run

sudo /etc/init.d/nfs-common restart

But didn't have to, since the data was already shared!

---

### Post by rccharles on 2013-04-23
Thanks for this great article.  It is simple and understandable. 

You may need to open TCP ports on your Firewall running on your server. 

I'm running Mac OS X Tiger on my server. I opened 111 and 2049 based on web documentation.  I opened more ports based on:
[http://hints.macworld.com/article.php?story=20100219094419683](http://hints.macworld.com/article.php?story=20100219094419683)

---

