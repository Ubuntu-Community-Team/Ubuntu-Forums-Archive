---
title: "Can't ftp to my server."
date: 2014-09-17
forum: Server Platforms
---

### Post by irv on 2014-09-17
When I try to ftp to my server using FileZilla I get this error.
```
Response:	no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory 
Error: Could not connect to server
```
Not sure how to fix.

---

### Post by matt_symes on 2014-09-17
Hi

> **irv said:**
> When I try to ftp to my server using FileZilla I get this error.
> Response:    no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory 
Error: Could not connect to server]
Not sure how to fix.

Is your server using samba - a samba server ?

I see that same error on my server and i read it's due to samba - my server exports a number of shares.

I did read the fix is upstream.

Kind regards

---

### Post by irv on 2014-09-17
Yes I have samba server running on my server. I am not sure what you mean that the fix is upstream. With samba I don't have a way to upload to the WWW directory that is why I need to use FTP.

---

### Post by matt_symes on 2014-09-18
Hi

> **irv said:**
> Yes I have samba server running on my server. I am not sure what you mean that the fix is upstream. With samba I don't have a way to upload to the WWW directory that is why I need to use FTP.

The error is a samba error and should not stop you FTP'ing files. Are you sure this is the problem ?

The fix is upstream means the bug has been fixed by the Samba developers and should be making its way into a ubuntu update at some point.

Kind regards

---

### Post by irv on 2014-09-18
My system did some updates today. and I had to shut down afterwards.
So when I restarted my system I tried again and the error is still there. Now I had the updates on my laptop which is running 14.04 but I didn't do any updates on my server yet so I will do that when I am home and do a restart and see if that helps. Will post again later.

---

### Post by irv on 2014-09-18
The light just came on. Correct me if I am wrong. I think I have to edit th /etc/apache2/httpd.conf file and change the line
```
ServerName localhost
```
and change it to read
```
ServerName wabasha-server.net
```

I can't do it right now because I am on the road but when I get home I will try this and see if it fixes all my problems.
Right now I can't HTTP or FTP to my server. Also I can do a ssh over the Internet and I believe this will fix that also. I will post if this works when I get home.

One other question: is there some place I need to change 127.0.1.1 to the assigned ip (205.243.122.13) that is assigned to the domain name (wabasha-server.net)? That is the ip address I own and is assigned to that domain. It is the same ip I have bound to my router mac address.

[COLOR="#FF0000"]EDIT[/COLOR]: I changed the ServerName to wabasha-server.net but this did not fix my problem. I didn't change the 127.0.1.1 because this is only the host name not the domain name. I am back to square one.

---

### Post by nerdtron on 2014-09-19
What port are you connecting on Filezilla? This is not an apache issue if you would just like to file zilla to the server.

---

### Post by matt_symes on 2014-09-19
Hi

> **nerdtron said:**
> What port are you connecting on Filezilla? This is not an apache issue if you would just like to file zilla to the server.

Agreed.

> 
[COLOR=#FF0000]EDIT[/COLOR]: I changed the ServerName to  wabasha-server.net but this did not fix my problem. I didn't change the  127.0.1.1 because this is only the host name not the domain name. I am  back to square one.

That does not surprise me as the initial error message you posted is due to a samba leak and has nothing to do with FTP or Apache.

You're following red herrings and not looking at the root cause of your problem; why you can't FTP to the server.

Have you tried to FTP from the command line to identify what that problem is ? It's not an issue of active vs passive FTP is it ?

I don't really know how to help you as you have not really given me - or anybody else - any information to go on.

Kind Regards

---

### Post by irv on 2014-09-19
I have completely removed samba from my server. rebooted the server. and yes I can ftp from a prompt using my domain name.
Now using FileZilla I can ftp to other sites. But can't use it for my domain or even my local ip address when I am on the same network.
What other information do you need, I will get it to you.
From my laptop where I am having this problem I can ping domain name and ip of the domain.

> irv@irv-Q500A:~$ ping wabasha-server.net
PING wabasha-server.net (205.243.122.13) 56(84) bytes of data.
64 bytes from ftth-1-13.hbci.com (205.243.122.13): icmp_seq=1 ttl=64 time=2.46 ms
64 bytes from ftth-1-13.hbci.com (205.243.122.13): icmp_seq=2 ttl=64 time=1.51 ms
64 bytes from ftth-1-13.hbci.com (205.243.122.13): icmp_seq=3 ttl=64 time=1.53 ms
64 bytes from ftth-1-13.hbci.com (205.243.122.13): icmp_seq=4 ttl=64 time=1.51 ms
64 bytes from ftth-1-13.hbci.com (205.243.122.13): icmp_seq=5 ttl=64 time=1.60 ms
64 bytes from ftth-1-13.hbci.com (205.243.122.13): icmp_seq=6 ttl=64 time=1.52 ms
64 bytes from ftth-1-13.hbci.com (205.243.122.13): icmp_seq=7 ttl=64 time=1.54 ms
^C
--- wabasha-server.net ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6009ms
rtt min/avg/max/mdev = 1.516/1.673/2.469/0.326 ms
irv@irv-Q500A:~$ ping 205.243.122.13
PING 205.243.122.13 (205.243.122.13) 56(84) bytes of data.
64 bytes from 205.243.122.13: icmp_seq=1 ttl=64 time=1.93 ms
64 bytes from 205.243.122.13: icmp_seq=2 ttl=64 time=1.52 ms
64 bytes from 205.243.122.13: icmp_seq=3 ttl=64 time=1.62 ms
64 bytes from 205.243.122.13: icmp_seq=4 ttl=64 time=1.51 ms
64 bytes from 205.243.122.13: icmp_seq=5 ttl=64 time=1.60 ms
^C
--- 205.243.122.13 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 1.516/1.639/1.930/0.159 ms
irv@irv-Q500A:~$ 

Of course I can do the same from my server via ssh. Later on today I will be at another location where I will have access to another Ubuntu laptop running 14.04 with FileZilla on it and I will try to ftp to my server and see what happens.
Just let me know what else you need.

[COLOR="#FF0000"]EDIT:[/COLOR] maybe I should mention, when I http to my domain (and I am not using it for a webpage but a file list) I don't see any files. I do have the root set to /var/www/ so all my files should show up but they don't. On my old server everything just worked. I was running 12.04. Here is a small screen shot.
[ATTACH=CONFIG]256541[/ATTACH]

[COLOR="#FF0000"]EDIT:[/COLOR] I got the http fixed. the DocumentRoot was set wrong in /etc/apache2/sites-enabled/000-default.conf file. but it didn't fix the ftp problem yet.
[ATTACH=CONFIG]256542[/ATTACH]

---

### Post by matt_symes on 2014-09-19
Hi

If you can FTP a file to the document root on your server from the command line but not using Filezilla, then that may suggest a problem with either Filezilla or the settings Filezilla is using to access you server.

When did this start happening ? 
After an update to Filezilla ? 
Have you just set this server up ?

Kind regards

---

### Post by irv on 2014-09-19
I upgraded my server from 12.04 to 14.04 last week, and it messed up my server, so I got everything backed up (just my /var/www/ directory) and did a fresh install of Ubuntu server 14.04 (no desktop). That's when the problem started. I don't remember FileZilla doing any updates.
I complete deleted my setting to my server and re-entered them again. I even tried a quick connect and I keep getting the same error. I am going to completely uninstall FileZilla and try reinstalling it again and see what happens. will add to this post if that works or not.

[COLOR="#FF0000"]EDIT:[/COLOR] completely remove FileZilla with it's config files and they reinstalled it and still have the same problems.

---

### Post by irv on 2014-09-19
Now that I am not on my network, I can not ftp from a prompt. I get Name or service not known. Could this have something to do with a config file for ftp on my server?
[ATTACH=CONFIG]256543[/ATTACH]

---

### Post by Lars Noodén on 2014-09-19
If you can ping the machine and SSH to it, can you reach it with SFTP?  There is a built-in client available from the shell prompt and FileZilla also supports it.

---

### Post by irv on 2014-09-19
I went to another laptop in a different location on a different network and used FileZilla and got the same error.
I am using vsftpd and I completely removed it and reinstlled it and get the same error. I then tried uninstalling it again and deleted all the files and directories that had anything to do with vsftpd. Then I went to install openssh-sftp-server but it was already installed. So I uninstalled it and reinstalled it again. I then rebooted the server and I still have the same problem.
I still can't ftp into my server via a command prompt either. What's your thoughts about trying pure-ftpd?

---

### Post by Lars Noodén on 2014-09-19
> **irv said:**
> I went to another laptop in a different location on a different network and used FileZilla and got the same error.
I am using vsftpd and I completely removed it and reinstlled it and get the same error. I then tried uninstalling it again and deleted all the files and directories that had anything to do with vsftpd. Then I went to install openssh-sftp-server but it was already installed. So I uninstalled it and reinstalled it again. I then rebooted the server and I still have the same problem.
I still can't ftp into my server via a command prompt either. What's your thoughts about trying pure-ftpd?

Yes, the SFTP server should be there already.  Can you connect with the sftp client at the command prompt?

```

***s***ftp irv@wabasha-server.net

```

SFTP is a different protocol than FTP.  There are still some use-cases for FTP, but by and large [FTP is deprecated](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) and needs to be avoided because it is unsafe.  If you can do your file transfers using SFTP, and have no other reasons for FTP, then the FTP server can be removed.  

Back on FTP: Also, active FTP does not work so well with firewalls or NAT.  So you might need to force the client into passive mode when trying to connect:

```

ftp -p irv@wabasha-server.net

```

---

### Post by irv on 2014-09-19
> **Lars Noodén said:**
> Yes, the SFTP server should be there already.  Can you connect with the sftp client at the command prompt?

```

***s***ftp irv@wabasha-server.net

```

SFTP is a different protocol than FTP.  There are still some use-cases for FTP, but by and large [FTP is deprecated](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) and needs to be avoided because it is unsafe.  If you can do your file transfers using SFTP, and have no other reasons for FTP, then the FTP server can be removed.  

Back on FTP: Also, active FTP does not work so well with firewalls or NAT.  So you might need to force the client into passive mode when trying to connect:

```

ftp -p irv@wabasha-server.net

```
Yes, the sftp works, but the ftp -p [email]irv@wabasha-server.net[/email] dose not.

---

### Post by irv on 2014-09-19
Is there a way to get sftp to work on FileZilla? I have this setup on other machines also. It how I transfer files to this server.

---

### Post by Lars Noodén on 2014-09-19
> **irv said:**
> Is there a way to get sftp to work on FileZilla? I have this setup on other machines also. It how I transfer files to this server.

Yes.  FileZIlla fully supports SFTP.  Here is a howto with screen shots.  It is for that other OS but the menus should be the same, I think

[https://it.unh.edu/sftp/filezilla.html](https://it.unh.edu/sftp/filezilla.html)

Just be sure that when setting up a new connection that you choose the protocol "SFTP - SSH File Transfer Protocol" and that it is using port 22.

---

### Post by irv on 2014-09-19
Great, everything is working again. This is the first time I ran into this kind of problem so it was a learning curve. Was the problem with ftp seeing sftp works? I will mark this solved.

---

### Post by Lars Noodén on 2014-09-19
> **irv said:**
> Great, everything is working again. This is the first time I ran into this kind of problem so it was a learning curve. Was the problem with ftp seeing sftp works? I will mark this solved.

Great.

ftp and sftp can coexist, they are different protocols on different ports on the server.  However, if you can get in with sftp, it is a good idea to phase out ftp and remove the ftp server.

Also, there are SFTP clients built in to the modern file mangers.  Open up the file manager (like Nautilus) and press ctrl-L and then enter an address like *sftp://irv@wabasha-server.net/*  The filemanger will then connect and let you see and move your files around as if they were in just another local folder.

---

### Post by irv on 2014-09-19
Wow! this is great. With this trick I don't even need FileZilla. I have other server in other locations I will setup like this.
Now my next project is to setup so I can vnc into my wife chromebook because she is always asking me to show her how to do things. She does not have much computer knowledge.  If it wasn't for her chromebook she wouldn't even touch a computer.

---

