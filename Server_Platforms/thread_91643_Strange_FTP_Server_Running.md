---
title: "Strange FTP Server Running"
date: 2005-11-17
forum: Server Platforms
---

### Post by lexor on 2005-11-17
I was useing nmap and done a port scan on our server WindowsXP, to my surprise it came up with port 21 FTP server listening.

I loaded up gftp on this linux machine and tryed to connect to the WindowsXP server on port 21 and sure it was running and asked me for the user name and password which I dont have as I never set up a ftp server on port 21 or any other port.

I went over to look at the Windows XP server loaded up a Flash FTP/FXP Client and tryed to connect to port 21 and got the message no server. I then did netstat -a once more no server on port 21 on the WindowsXP server.

I downloaded Sygate firewall for WindowsXP and installed it, I then went over to this Linux system and tryed to connect and was blocked, a quick look back over to the WindowsXP server and there was Sygate asking me if I wanted to allow this Linux machime access on port 21.

For myself I cant get my head around this one, I did netstat -a , looked at the tasklist, and nothing on port 21 or and any exe that looks suspect, unless you count all of the Windows XP services as suspect lol :).

The only thing I can think of is that I have a FTP server running on the Linux machine (as it uses WindowsXP ICS for access to the Internet) which I am sure I havent as nothing comes up on a port scan or netstat -a and its blocked with iptables anyway.

Another thing it maybe is a very clever FTP server/virus that is not detected by antivirus and hides its self from the task list and netstat, possible ? 

This just isnt logical and dont make sense to me it sure is very strange, anyone any idea?

---

### Post by lexor on 2005-11-17
This is the command I put in.

me@ubuntu:~$  sudo nmap -O -p 1-1024 **.**.***.***

Starting nmap 3.81 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-11-17 22:20 GMT
Warning:  OS detection will be MUCH less reliable because we did not find at lea st 1 open and 1 closed TCP port
Insufficient responses for TCP sequencing (1), OS detection may be less accurate
Interesting ports on xpcomp (**.**.***.***):
(The 1023 ports scanned but not shown below are in state: filtered)
PORT   STATE SERVICE
21/tcp open  ftp
Device type: general purpose|firewall
Running: Microsoft Windows NT/2K/XP, Symantec Windows NT/2K/XP
OS details: Microsoft Windows XP Pro RC1+ through final release, Microsoft Windo ws XP Pro SP1, Microsoft Windows XP SP1, Symantec Enterprise Firewall 7.0 runnin g on Windows 2000 SP2

Nmap finished: 1 IP address (1 host up) scanned in 19.269 seconds
me@ubuntu:~$

Just a note that its Windows XP SP2 and Sygate Firewall, the information Nmap gives isnt correct but its not important.

**.**.***.*** = My IP

---

### Post by lexor on 2005-11-17
Linux Nmap Scan

me@ubuntu:~$ sudo nmap -O -p 1-1024 192.168.0.2

Starting nmap 3.81 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-11-17 22:28 GMT
Warning:  OS detection will be MUCH less reliable because we did not find at least 1 open and 1 closed TCP port
All 1024 scanned ports on 192.168.0.2 are: closed
Too many fingerprints match this host to give specific OS details

Nmap finished: 1 IP address (1 host up) scanned in 4.895 seconds
me@ubuntu:~$

---

### Post by ubernoob on 2005-11-17
Have you installed IIS? Check out Add remove programs --> Internet Information Services --> FTP.

The port shouldn't be open if you haven't opened it yourself. You might have opened it by acidently installing IIS with ftp.

If not it might be a trojan. 
This link might give you some hints, but probably not any solutions.[http://www.governmentsecurity.org/forum/index.php?showtopic=11521]("http://www.governmentsecurity.org/forum/index.php?showtopic=11521")

If you do "ftp ipadress" from your linux shell. Do you get any header from the ftp server? Try with the username: "anonymous" and see what happens.

A last solution before i go to bed is scanning with nessus. (install nessus and nessusd).

---

### Post by lexor on 2005-11-18
No I dont have IIS installed I just checked.
Error 404 on governmentsecurity.org.

Did some checks with SHELL FTP, GFTP, NMAP once more, funny thing is now GFTP will not allow login and the firewall is off on the server, but as you can see, port 21 **IS** open for service.

Nmap
> 
me@ubuntu:~$ sudo nmap -O -p 1-1024 **.**.***.***

Starting nmap 3.81 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-11-18 14:57 GMT
Interesting ports on comp (**.**.***.***):
(The 1021 ports scanned but not shown below are in state: filtered)
PORT    STATE  SERVICE
21/tcp  open   ftp
139/tcp closed netbios-ssn
445/tcp open   microsoft-ds
Device type: firewall
Running: Symantec Windows NT/2K/XP
OS details: Symantec Enterprise Firewall 7.0 running on Windows 2000 SP2

Nmap finished: 1 IP address (1 host up) scanned in 18.785 seconds


FTP 
> 
me@ubuntu:~$ ftp **.**.***.***
Connected to **.**.***.***.
421 Service not available, remote server has closed connection
ftp>


GFTP
> 
Looking up **.**.***.***
Trying **.**.***.***:21
Connected to **.**.***.***:21
Error: Could not read from socket: Connection reset by peer
Disconnecting from site **.**.***.***
Waiting 30 seconds until trying to connect again


---

### Post by ubernoob on 2005-11-18
If ftp wasn't running, it shouldn't send an error number back to you. It should just refuse the connection. While testing, you should block port 21 on your router, so noone access your computer from the outside.

Have you tried nessus?

sudo apt-get install nessusd
(if i don't remember wrong, you have to give some info to make a ssl certificate. It doesn't mather what you write here)
sudo apt-get install nessus
sudo nessus-adduser
(follow the steps to add a user. use password. that is the easiest)
then start nessus: 
nessus

enter username and password, and connect to nessusd. Choose target machine and start the scan.

---

### Post by lexor on 2005-11-18
Yes I tryed nessus, heres the results.

> 

timestamps|||scan_start|Fri Nov 18 17:59:40 2005|
timestamps||**.**.***.***|host_start|Fri Nov 18 17:59:42 2005|
results|**.**.***.***|**.**.***.***|ftp (21/tcp)
timestamps|||scan_end|Fri Nov 18 18:03:45 2005|



I dont have a router, I have a cable modem.

On a router I know you can login into it on port 23 for shell access, but for a cable modem on port 21 I wouldnt think so, that idea crossed my head.

I have yet to do a full scan as it seems to be takeing a long time so I will leave that for later.

---

### Post by ubernoob on 2005-11-18
Sorry, then i'm out of ideas. :( By then i usually reinstall windows. Thats how it works in the MS world....

---

### Post by lexor on 2005-11-19
Sure thing, thanks for the info you gave.

You know by doing a netstat -a on xp and virus scan then checking the running service it just dont tell me anything.

If it is some sort of trojan ftp backdoor then its a very good one as it hides its self from xp very well, but not nmap.

---

### Post by m@dm@x on 2005-11-23
You may want to run RootKitRevealer on the XP box to see if anything is hidden from the API.  You can get to it from here... [http://www.sysinternals.com/Utilities/RootkitRevealer.html](http://www.sysinternals.com/Utilities/RootkitRevealer.html)

Its a free app and I have used it more than I have ever wanted to.

---

### Post by AmboyGuy on 2005-11-23
found this article just after I got done reading this post.
[Breaking through a Firewall using a forged FTP command](http://www.phrack.org/show.php?p=63&a=19)

---

### Post by Anglagard on 2005-11-25
Did you find out what it was?

I'm having the same problem. I run ubuntu on coLinux and I can nmap XP from there. One thing I notice is the open port 21 only shows when I dial up and have Internet connection sharing (ICS) enabled. I suspect this is just a windows thing since this is a new install but I could be wrong.
This is the XP home edition that came pre-installed on my dell Inspiron 6000. It came with a bunch of junk maybe one of those things are opening up something on port 21 when I dial up with ICS.

Could anyone dialing up the net with ICS do a port scan and tell me if port 21 is open on XP home? Thanks

I will be doing a little more investigation, If I find anything I will post it here.

---

### Post by lexor on 2005-11-25
I use Windows XP to get on to the internet useing ICS as Windows XP is the server. I did a new install of Windows XP on the server and the Port 21 is still listening.

So it maybe safe to say it isnt a virus/trojan but at the same time by reinstalling and formating dont mean you get rid of a virus.

I am sure I am correct in saying that my Windows knowlege is far better than my Linux knowlege regarding Networks, from a CompTIA Network + level not a high level but a level that should at least give me some clues as to what the problem is.

It dont make sense to me unless its the Linux client that is listening on port 21 but with netstat -a nothing shows up here on Ubuntu.

---

### Post by TeeSeeJay on 2005-12-01
[QUOTE=lexor]I use Windows XP to get on to the internet useing ICS as Windows XP is the server. I did a new install of Windows XP on the server and the Port 21 is still listening.
[/QUOTE]

Did you find a solution to your question? It seems to me it must be somehow related to running ICS on XP. I know ICS runs a dhcp service, a dns proxy service, and a NAT service, so it would be weirder if the box had no listening ports at all. If you disable ICS and scan the box with nmap, does the tcp/21 port still show as open?

Try using the port reporter ([http://support.microsoft.com/default.aspx?scid=kb;en-us;837243](http://support.microsoft.com/default.aspx?scid=kb;en-us;837243)) instead of netstat on the XP box.

---

### Post by fordfan753 on 2005-12-01
I think it's quite normal to have 21 listening, just curious...was 80 also open?

---

### Post by TeeSeeJay on 2005-12-01
[QUOTE=fordfan753]I think it's quite normal to have 21 listening, just curious...was 80 also open?[/QUOTE]

his nmap and nessus results are earlier in the thread, and if complete, then port 80 was not open. Having a listener on tcp/21 is only normal when you have an FTPd running, which is where the OP is confused...because as far as he knows, he does not, in fact, run an FTP server on his box.

---

