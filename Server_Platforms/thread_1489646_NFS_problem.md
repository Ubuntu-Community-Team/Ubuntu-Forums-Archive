---
title: "NFS problem"
date: 2010-05-21
forum: Server Platforms
---

### Post by ingeva on 2010-05-21
The last 3-4 distros I haven't got NFS to work. As a temporary solution I use SAMBA,
but I believe NFS would be more convenienbt.

I have used every trick in the book, and then some. But the two computers in my network are unable to see each other's files.

The computers are called Papa and Pantera. The partition and folder names are identical because one is a backup of the other.

Here's the export file and the relevant part of fstab (in Pantera):

```
# These directories are available on the network.
/       *(rw,sync,no_subtree_check,no_root_squash)
/Store  *(rw,sync,no_subtree_check,no_root_squash)
/My     *(rw,sync,no_subtree_check,no_root_squash)
/Backup *(rw,sync,no_subtree_check,no_root_squash)
``````
# Remote, NFS
Papa:/       /mnt/Papa-root  nfs rw,rsize=8192,wsize=8192,timeo=14,hard,intr 0 0
Papa:/Store  /mnt/Papa-store nfs rw,rsize=8192,wsize=8192,timeo=14,hard,intr 0 0
Papa:/My     /mnt/Papa-my    nfs rw,rsize=8192,wsize=8192,timeo=14,hard,intr 0 0
Papa:/Backup /mnt/Papa-back  nfs rw,rsize=8192,wsize=8192,timeo=14,hard,intr 0 0
```Of course the directories in /mnt exist.
Have I forgotten something important here?

---

### Post by HermanAB on 2010-05-21
Well, first check whether the server is running and you can connect to it from the every machine:

On the SFS server:
# telnet localhost nfs

On the other machine:
# telnet ipaddressofnfsserver nfs

Chances are that your firewall or another network problem is blocking it.

---

### Post by Lucky. on 2010-05-21
In case you already didn't know, NFS authenticates by UID.  So if the files on your server are owned by user 1000, but you log into your client as user 1001, I don't think you will gain access.

---

### Post by Jose Catre-Vandis on 2010-05-21
Work through this howto:
[http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS](http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS)

---

### Post by ingeva on 2010-05-21
> **HermanAB said:**
> Well, first check whether the server is running and you can connect to it from the every machine:

On the SFS server:
# telnet localhost nfs

On the other machine:
# telnet ipaddressofnfsserver nfs

Chances are that your firewall or another network problem is blocking it.
I have no problem connecting from one machine to the other, using telnet or samba.
I had NFS running with an earlier version of Ubuntu; I'm not sure if it was 8.04 or 8.10,
and I use the same setup.

---

### Post by ingeva on 2010-05-21
> **Lucky. said:**
> In case you already didn't know, NFS authenticates by UID.  So if the files on your server are owned by user 1000, but you log into your client as user 1001, I don't think you will gain access.
I have the same user ID on both machines.
I can also do remote login from one to the other, and vice versa.

---

### Post by ingeva on 2010-05-21
> **Jose Catre-Vandis said:**
> Work through this howto:
[http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS](http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS)
As far as I can understand the descriptions, I have done everything by the book, step by step.

Is anyone else using this on Lucid?

---

### Post by Jose Catre-Vandis on 2010-05-21
Yes, I have nfs running from a Jaunty server to a Xubuntu 10.04 client.

Are you sure you have exported your shares?

```
sudo exportfs -a
```

You also have a * where you should have some kind of network mask in your exports file. Try changing this to, for example, **192.168.1.0/24**, whwre your subnet is 192.168.1.0.

So one of your shares should read:
```
/files 192.168.1.0/24(rw,no_root_squash,async)
```
and then export the share again and restart the server

---

### Post by ingeva on 2010-05-21
> **Jose Catre-Vandis said:**
> Are you sure you have exported your shares?Not sure what you mean. I showed you the export file.

> **Jose Catre-Vandis said:**
> Try changing this to, for example, **192.168.1.0/24**, whwre your subnet is 192.168.1.0.On Pantera I used to have Papa there, on Papa I had Pantera. No difference. The two computers are not set up as one client and one server now, but as peers, or siblings. I should reach one from the other, both ways, and there's no problem with SAMBA. NFS should be easier. Why doesn't THAT work? :)
(I still have SAMBAbecause once in a leap year I need to run Windows for some odd reason).

Papa and Pantera's IP addresses are defined in the hosts file:

```
10.10.10.1 Router
10.10.10.2 Pantera
10.10.10.4 Papa

```And before I forget: I appreciate your help, but THIS USED TO WORK in earlier Ubuntu versions. Why not now?
And I'm trying this with 9.10 Karmic, not on Lucid. I must get Lucid to work first, so there are other problems to solve which requires other help. :(

---

### Post by arrrghhh on 2010-05-21
So NFS is a server-client model.  You'll have to install the server AND client on BOTH machines - I'm not sure if you've done that.  You'll need nfs-kernel-server, nfs-common, and portmap on **both** machines.  You'll also need to configure your exports for **both** machines.

As far as what he means by 'exporting' your shares is that command he gave you:

```
sudo exportfs -a
```

I think it's also good practice when your exports change is to restart the NFS services in init.d.  nfs-kernel-server and portmap.

---

### Post by Jose Catre-Vandis on 2010-05-21
> **ingeva said:**
> 

Papa and Pantera's IP addresses are defined in the hosts file:



When troubleshooting nfs, it is best to remove as many variables as possible, hostnames being one of them!

So as you are using the 10.10.10.0 subnet (nice choice, so do I :)), just use the IP addresses and subnets instead of hostnames.

Concentrate on getting one server and one client up and running, and then get it working the other way. Please go back to the howto I pointed to, read it carefully so that you understand all the steps required and start your configuration again, following each instruction in turn, just as the howto says. Once you have it working, you can then start trying out hostnames and other configurations. I understand that it worked before, but as it is not working now we have to go back to basics to fix it.

Good luck :)

---

### Post by ingeva on 2010-05-22
> **arrrghhh said:**
> So NFS is a server-client model.  You'll have to install the server AND client on BOTH machines - I'm not sure if you've done that.  You'll need nfs-kernel-server, nfs-common, and portmap on **both** machines.  You'll also need to configure your exports for **both** machines.
Done that. Except for $HOSTNAME, both computers have the same setup, same disk partitions, etc.

You mention portmap. Haven't really heard about that before, but I checked and it IS installed and it IS running, and so are nfsd4 and 8 instances of nfsd.

> **arrrghhh said:**
> I think it's also good practice when your exports change is to restart the NFS services in init.d.  nfs-kernel-server and portmap.Done that, of course. But when the computer is restarted, shouldn't NFS also be restarted? I mean, you shouldn't have to do that every time, or make a separate script for it?

Of course I can manage with SAMBA, but NFS was much faster and more convenient. For instance, with SAMBA all national characters were being crippled until I figured out how to set the right character set ( utf-8 ). Unnecessary with NFS.

---

### Post by ingeva on 2010-05-22
> **Jose Catre-Vandis said:**
> When troubleshooting nfs, it is best to remove as many variables as possible, hostnames being one of them!
So as you are using the 10.10.10.0 subnet (nice choice, so do I :)), just use the IP addresses and subnets instead of hostnames.
Concentrate on getting one server and one client up and running, and then get it working the other way. Please go back to the howto I pointed to, read it carefully so that you understand all the steps required and start your configuration again, following each instruction in turn, just as the howto says. Once you have it working, you can then start trying out hostnames and other configurations. I understand that it worked before, but as it is not working now we have to go back to basics to fix it.
As far as I can see your advice is very good, and I've done most of it, including using IP addresses and subnet definition. The problem is that nothing has helped. I get absolutely no visible error messages, but I don't see any files in the remote folders.

I must admit I haven't read the complete "howto" that you mention, but it's not really a howto. It's a loooong discussion, and many things are not very relevant.
I have followed another howto before, from the Ubuntu documentation:
[http://doc.ubuntu.com/ubuntu/serverguide/C/network-file-system.html](http://doc.ubuntu.com/ubuntu/serverguide/C/network-file-system.html)

and I have followed that to the dot and it USED TO WORK!!! :confused: but this time I can't see that I have done anything wrong. That's what puzzles me: There are several correct ways to set it up, but none of them work, which means that there must still be an error somewhere. The problem is that I can't find it.

Wouldn't it be wonderful if I could find an existing network with a functioning setup, and try to connect there, copying the setup piece by peace until I could find the right piece of the puzzle?
But you can't use NFS over the Internet, can you? :)

---

### Post by ingeva on 2010-05-22
Funny thing here:

If I attempt the command  sudo mount -a
I get the following messages:
```

mount.nfs: mount to NFS server 'Papa:/' failed: RPC Error: Success
mount.nfs: mount to NFS server 'Papa:/Store' failed: RPC Error: Success
mount.nfs: mount to NFS server 'Papa:/My' failed: RPC Error: Success
mount.nfs: mount to NFS server 'Papa:/Backup' failed: RPC Error: Success
```??? The error is "Success"? :)

I still don't get any access ... :frown:

---

### Post by HermanAB on 2010-05-22
Well, the fact that it worked on previous installs mean diddly squat now.  You have to test everything, starting at the lowest level and working your way up.

So, first of all, confirm that the NFS server is actually running.  Then confirm that you can actually connect to the server using a simple debug tool like telnet.  Confirm that your user ID and group ID are actually the same. Finally try to connect using NFS and watch the log files for error messages.

Simply doing a connection test at the highest level of the stack and then wondering why it doesn't work, isn't going to get you anywhere.

---

### Post by ingeva on 2010-05-22
> **HermanAB said:**
> Well, the fact that it worked on previous installs mean diddly squat now.  You have to test everything, starting at the lowest level and working your way up.Certainly. How?

> **HermanAB said:**
> So, first of all, confirm that the NFS server is actually running.Certainly. How? Isn't it enough to check with the ps command, which gave me the information that nfsd4 and 8 instances of nfsd are running?
I have installed the necessary modules of NFS per instructions. Why should it NOT run?
There are no error messages when I start or restart the server (nfs-kernel-server).

> **HermanAB said:**
> Then confirm that you can actually connect to the server using a simple debug tool like telnet.Certainly. I've done that according to previous instructions, but I have no idea how to interpret the information and what to wo with it.
> **HermanAB said:**
> Confirm that your user ID and group ID are actually the same.They are.

> **HermanAB said:**
> Finally try to connect using NFS and watch the log files for error messages.OK. What log files? I find nothing of the sort!

> **HermanAB said:**
> Simply doing a connection test at the highest level of the stack and then wondering why it doesn't work, isn't going to get you anywhere.I certainly feel somewhat like an idiot here, but I have found very little literature and know nothing about the basics of NFS. The first time I did this, I just did it and it worked. Now I've done it exactly the same way (using the same setup scripts) and it doesn't work. I need a more detailed description of what steps I need to take. Can you help me with those steps, if necessary by helping me find the necessary information?
I was just about to start working through the long thread given to me earlier, and I'll spend some time browsing that to see if I can find some useful tips. I'm sure it's just a tiny little thing that I have overlooked .... :)

It couldn't be that I've changed to ext4 file system, could it?

---

### Post by ingeva on 2010-05-22
I wonder if anyone would be so kind as to walk me through this, step by step, using Skype as a communication medium. Today is late Saturday, and I'll shut down for the day.
However, I've been trying for a long time to make this work, and all the good tips that I have received so far haven't really made any difference. I get references to things I know nothing about. I'm a complete noob in this area. If I were not, I wouldn't need to ask these questions.
However, I'm not without knowledge. I've been an Ubuntu user for about 2 years, and I'm not planning to use anything else. I have also been working with various other computers and systems for 40 years, so I'm absolutely no beginner. I usually find solutions myself. However, I'm stuck here, and obviously I need some external help.

My Skype ID is viking1948, but I'd like for someone to come forward first, so we can make an appointment. I have time tomorrow and Monday, which are both holidays in Norway (TZ GMT+2).

---

### Post by Jose Catre-Vandis on 2010-05-22
> **ingeva said:**
> I must admit I haven't read the complete "howto" that you mention, but it's not really a howto. It's a loooong discussion, and many things are not very relevant.

You only need to work through the first post which is the howto. To help, I will write out the stages you need to work through to get nfs running. (As a reference, I have used this approach for over 4 years on countless occasions, and it has worked every time).

We will do this for one server and one client to start off with. 

1. Assume your subnet is 10.10.10.0 and that your server is 10.10.10.2 and your client is 10.10.10.3.
2. Also assumes that you have the same login name/UID number on the server and the client, e.g. ingeva UID=1000. This last bit isn't vital but it takes out a further level of configuration, and helps things to work. 
3. Finally assumes that your server and client can "see"/communicate with each other, e.g. you can ping, ssh or telnet one from the other and vice-versa.

**[COLOR="Red"]On the server (10.10.10.2)[/COLOR]**
***Install the packages you need***
```
sudo apt-get install nfs-kernel-server nfs-common portmap
```
***Create a mount point for your share***
```
sudo mkdir /files
```
***Edit your exports file***
```
sudo nano /etc/exports
```
***Add this line to exports, then save and exit***
```
/files 10.10.10.0/24(rw,no_root_squash,async)
```
***Export your share***
```
sudo exportfs -a
```
***Restart the nfs server***
```
sudo /etc/init.d/nfs-kernel-server
```
(if it complains about using a different method it might be)
```
sudo service nfs-kernel-server restart
```

That's it on the server.

**[COLOR="Red"]On the client (10.10.10.3)[/COLOR]**
***Install the packages you need***
```
sudo apt-get install nfs-common portmap
```
***Create a mountpoint for the incoming share***
```
sudo mkdir /files
```

That's the basic set up. **Now to mount the share:**

***Manually:***
```
sudo mount 10.10.10.02:/files /files
```
[B][I]
Automatically on boot using fstab:[/I][/B]
```
sudo nano /etc/fstab
```
***Add the following line to the bottom of your fstab file***
```
10.10.10.2:/files /files nfs rsize=8192,wsize=8192,timeo=14,intr
```

If this doesn't work, I'll go into a guitar shop, ask to try a Gibson Les Paul, and then proceed to play Black Night, Smoke on the Water, and Stairway To Heaven until I am thrown out on the street :):guitar:

---

### Post by ingeva on 2010-05-23
> **Jose Catre-Vandis said:**
> You only need to work through the first post which is the howto. To help, I will write out the stages you need to work through to get nfs running. (As a reference, I have used this approach for over 4 years on countless occasions, and it has worked every time).
I must thank you very much for your time and efforts.
The problem is that I have done all that, and with some variation, and it still doesn't work, nor does it give me any sensible error messages except what I have already written here. The howto you refer to didn't give me any new information or ideas.

It's a mystery. First time I did it according to the howto, it just worked. At some stage after an upgrade (I'm not sure exactly which one but probably 8.10 or 9.04) it stopped short. I used exactly the same procedure to set it up.

On the computer I'm using daily, Pantera, the /mnt directory contains the mount points. If I go to /mnt and Papa is not logged in (which it must be or the wifi is still inactive) I can't enter that directory with nautilus. As soon as I log in on Papa I get to see the mount points. The folders however, are empty. My conclusion is that the server itself is working, but there's something wrong with the communication. Does this sound sensible at all?

I'm contemplating going back to 8.04, but that's a huge task because I would have to change my filesystems back to ext3. There are many GBs of files and that will mean a lot of copying..... :)

I've been wondering if I should buy a ready-made NAS instead. At least then if I can't connect, I'll know which side has the bug. Or? :)

---

### Post by HermanAB on 2010-05-23
OK, so your problem is a lack of error messages.  Do a manual NFS mount.  That HAS to give you meaningful error messages:

On the server in file /etc/exports add:
/home/whatever 192.168.1.0/24(root_squash,async,rw)
(Assuming that your network is 192.168.1.x)

Restart the NFS server.

On the client, mount the share manually:
# mkdir /mnt/whatever
# mount -t nfs 192.168.1.1/home/whatever /mnt/whatever
(Assuming that your server is 192.168.1.1)

Now you should have enough error messages to figure it out.

---

### Post by koenn on 2010-05-23
just a thought:
is it possible ubuntu recently moved to nfs v4 and you're having compatibility issues ? It would explain why things 'suddenly' don't work anymore.
I do LTS, am always slow to upgrade, and mainly use debian on my servers, so I haven't really looked in to this myself. Maybe someone can shed some light ?


but don't let this stop you from trying to generate errors the way Herman suggests.

---

### Post by ingeva on 2010-05-23
> **HermanAB said:**
> 
On the server in file /etc/exports add:
/home/whatever 192.168.1.0/24(root_squash,async,rw)
(Assuming that your network is 192.168.1.x)

Restart the NFS server.

On the client, mount the share manually:
# mkdir /mnt/whatever
# mount -t nfs 192.168.1.1/home/whatever /mnt/whatever
(Assuming that your server is 192.168.1.1)

Now you should have enough error messages to figure it out.
We are getting closer! :)
I took the trouble of changing my main storage partition to ext4 and installed an 8.04 system. While spending time getting the wireless network interface to work, I switched back and forth between cable and wireless, trying several times to connect to the server (Pantera) without any success.
Then suddenly, after quite a long time, all the server files appeared.
Now Pantera (server) is running 9.10 and Papa (Client) is running 8.04, and as long as I use the client everything is fine.

The other way is worse. No connect there. I tried your suggestion:
inge@Pantera:/mnt$ sudo mount -t nfs 10.10.10.4/Store Papa-store
mount.nfs: remote share not in 'host:dir' format

So I tried:
inge@Pantera:/mnt$ sudo mount -t nfs 10.10.10.4:/Store Papa-store
mount.nfs: mount to NFS server '10.10.10.4:/Store' failed: RPC Error: Success

which is a message I have gotten before.
The corresponding mount definition in the fstab file is:
Papa:/Store  /mnt/Papa-store nfs rw,rsize=8192,wsize=8192,timeo=14,hard,intr 0 0

I don't understand the comments/instructions in the /etc/exports file.
I have assumed that I've been using nfs2 or nfs3, but if I'm using nfs4, will the setup have to be different? Doesn't the latest version also support nfs2?
(I can always work my way through an upgrade later).

In this line (in the exports file):
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)

what does "gss/krb5i" mean? Is it meant as an example, and if so, for what?
Or is it an exact description of what you should write?

Can I really use different versions of nfs on different computers? Evidently I can -- one way, but not the other.... :)

I think we can conclude that I have the server working on Pantera and the client on Papa, but at least one of them is NOT working the other way around, and that's what I need in the final configuration. So what should my next step be?

---

### Post by ingeva on 2010-05-23
> **koenn said:**
> just a thought:
is it possible ubuntu recently moved to nfs v4 and you're having compatibility issues ? It would explain why things 'suddenly' don't work anymore.
I do LTS, am always slow to upgrade, and mainly use debian on my servers, so I haven't really looked in to this myself. Maybe someone can shed some light ?
Yes, that's definitely a possibility, and as you can see from my previous post, changing back to 8.04 seems to have solved half of the problem.
On that computer I don't have a spare partition, so there's quite a lot of time and work involved in setting it up, but I'm determined to solve this puzzle, because it's probably based on some silly little mistake or misunderstanding.

I agree with you about being slow to upgrade. It's always smart to let someone else figure out the problems first.
I've been running Mint 8 for a while, and I loved the looks and the smooth operation,
but I hoped I would be able to solve this nfs problem with the next Ubuntu. So far it seems like the problem is not with the OS version, but rather with my own (lack of) understanding of the instructions.

---

### Post by HermanAB on 2010-05-23
```
inge@Pantera:/mnt$ sudo mount -t nfs 10.10.10.4/Store Papa-store
mount.nfs: remote share not in 'host:dir' format
```

Well, there is your error message.  Try this:

```
$ sudo mkdir /mnt/Papa-store
$ sudo mount -t nfs 10.10.10.4:/Store /mnt/Papa-store
```

See this:
[http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#TROUBLESHOOTING](http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#TROUBLESHOOTING)

---

### Post by ingeva on 2010-05-23
> **HermanAB said:**
> ```
inge@Pantera:/mnt$ sudo mount -t nfs 10.10.10.4/Store Papa-store
mount.nfs: remote share not in 'host:dir' format
```Well, there is your error message.  Try this:

```
$ sudo mkdir /mnt/Papa-store
$ sudo mount -t nfs 10.10.10.4:/Store /mnt/Papa-store
```See this:
[http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#TROUBLESHOOTING](http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#TROUBLESHOOTING)
Obviously you didn't read the rest of my post. I already tried that.
But I'll see that and see what else I can do.

In the meantime I can tell you that I installed 8.10 on another partition on Pantera, and NFS was running almost immediately (took a little time to "settle") and the setup is identical.

I'll come back.

---

### Post by ingeva on 2010-05-23
Thanks for the tip Herman!

But it does not describe the error I got here, which in my mind is contradictory:

inge@Pantera:/mnt$ sudo mount -t nfs 10.10.10.4:/Store Papa-store
mount.nfs: mount to NFS server '10.10.10.4:/Store' failed: RPC Error: Success[]("http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#TROUBLESHOOTING")

I mean a failure is not a success!

I have now come to the conclusion that I have probably done nothing wrong here. I suspect a conflict between the NFS software (setup) and something else in the computer.
So I'll start with a barebone system and see what happens. After all, I don't need a full desktop to run nfs.

I thank you for all your help and efforts til now, and after I have investigated some more I may have to come back if it's not resolved. But I expect it to be. Since tomorrow is also a holiday here I can take some time to re-install the system from scratch.

---

### Post by ingeva on 2010-05-24
Update on the NFS problem.

For new readers: I have two computers in a LAN, Papa and Pantera.

I have installed 9.10 Karmic Koala on both computers.
Their NFS do not communicate. If I try to mount one share, I get a funny
error message. Otherwise nothing.

I have also installed 8.10 Intrepid Ibex on Pantera, another partition.
It mounts the NFS shares without any problem at all. 
The exact same setup is used in both cases, so for 9.10 I may probably
need to make a change somewhere.
Evidently the server side works fine. The problem is with the client side,
most probably with mount - but all that I have read I has still not found
any workable solution.

I'll continue to investigate. In the meantime, if anyone gets a bright idea,
please share!

Thank you for all the help so far.

---

### Post by koenn on 2010-05-24
if you google the funny rcp error:success, you'll find that others have had similar problems, and that is seems to point to an nfs protocol version mismatch between the server and the client.
see eg here : [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=524760](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=524760) 

apparently, you'd be able to work around it by specifying an nfs version in the mount statement. 

eg in fstab:
```
server:/path/to/export /path/to/mountpoint    nfs    defaults,nfsvers=3      0      0

```
you' probably want to try with version 3 and/or 4.
in a  mount statement, you would use -o for options, eg
```
mount -t nfs  -o nfsvers=3   server:/path/to/export /path/to/mountpoint
```


edit:
(should have seen this sooner : )
you can check versions with nfsstat, eg

```
user@kclient:~$ nfsstat --client
Client rpc stats:
...

Client nfs v3:
...

```
```

server:~# nfsstat --server
Server rpc stats:
...

Server nfs v3:
...

```

---

### Post by ingeva on 2010-05-25
> **koenn said:**
> if you google the funny rcp error:success, you'll find that others have had similar problemsThank you very much!
I think you're on to something, and the mismatch between client and server version has been suggested before (By you?), but in one and the same version of OS, shouldn't the NFS versions be the same on client and server????

Anyway, it's worth a try. I didn't have a clue how to specify this in the mount statement.
Right now I have a terrible backlog because of all the time I've spent on this problem, so I won't be able to look at it again until later, but as soon as I have a window ..... :)

Thanks!

---

### Post by ingeva on 2010-05-25
[QUOTE=koenn;9351666]apparently, you'd be able to work around it by specifying an nfs version in the mount statement. 
eg in fstab:
```
server:/path/to/export /path/to/mountpoint    nfs    defaults,nfsvers=3      0      0

```

There we are!
I changed the lines in fstab:
```

Papa:/Backup /mnt/Papa-back  nfs rw,nfsvers=2,rsize=8192,wsize=8192,timeo=14,soft,intr 0 0
```(This was only one of them for short)
and it solved the problem immediately.

Next step will be to learn how to set it up for nsf4, but I'll do that studying on my own I think.

Thank you very much! You have been very helpful!

---

