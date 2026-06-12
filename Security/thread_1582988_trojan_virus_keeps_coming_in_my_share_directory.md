---
title: "trojan virus keeps coming in my share directory"
date: 2010-09-27
forum: Security
---

### Post by abhinav90 on 2010-09-27
After some time i always see a trojan virus in my ubuntu machines shared folder. It is an exe detected by ClamAv as Trojan.Autokit-77

I thought i was getting it from some windows machine on the network but that isn't the case. I deleted the virus and removed my computer from the network and still the virus comes back. My computer however, is still connected to the internet through an independent mobile broadband usb stick. 

So where is the virus coming from and why is it going to my shared folder. I thought ubuntu would not allow the virus to do something like this without me giving it permission. I am running 10.4.

---

### Post by CharlesA on 2010-09-27
My bet is that it's a false postive.

What file is being flagged?

---

### Post by Jeroensum on 2010-09-27
Do you have a dual-boot setup?
Is you computer removed from the workgroup/domain or physically removed i.e. pulled the utp-cable from the switch?

Does the share have world writable permissions and if so, does it need those settings?

Is your computer accessible from the net or is there a (NAT) router between you and the internet?

When does the file reappear, instantly or otherwise? If otherwise what major events have taken place in between the removal of the file and the reappearance?

---

### Post by cprofitt on 2010-09-27
OP:

What permissions are on the share? Is it possible that this is coming from an external source? Do you show any connections to your computer?

```

$netstat -ta

``````

$netstat -ntu

```

or my favorite

```

$netstat -lnptu

```

> 
To list all open network ports on your machine, run **netstat -lnptu**. Here is a breakdown of the parameters:
 **l** - List all listening ports
**n** - Display the numeric IP addresses (i.e., don't do reverse DNS lookups)
**p** - List the process name that is attached to that port
**t** - List all TCP connections
**u** - List all UDP connections


---

### Post by abhinav90 on 2010-09-27
The output for netstat -lnptu is as follows:

```

Proto	Recv-Q 	Send-Q	Local Address	Foreign Addr	State	Pid  Program name
tcp	0	0	127.0.0.1:631	0.0.0.0:*	LISTEN	2062/cupsd
tcp	0	0	127.0.0.1:5432	0.0.0.0:*	LISTEN	1137/postgres

tcp	0	0	127.0.0.1:25	0.0.0.0:*	LISTEN	2015/exim4
tcp	0	0	127.0.0.1:3306	0.0.0.0:*	LISTEN	1054/mysqld

tcp6	0	0	:::80	:::*	LISTEN	2119/apache2
tcp6	0	0	::1:631	:::*	LISTEN	2062/cupsd
tcp6	0	0	::1:5432	:::*	LISTEN	1137/postgres
tcp6	0	0	::1:25	:::*	LISTEN	2015/exim4
tcp6	0	0	:::445	:::*	LISTEN	907/smbd
tcp6	0	0	:::139	:::*	LISTEN	907/smbd
udp	0	0	0.0.0.0:5353	0.0.0.0:*		937/avahi-daemon:
udp	5256	0	0.0.0.0:137	0.0.0.0:*		11342/nmbd
udp	0	0	0.0.0.0:138	0.0.0.0:*		11342/nmbd
udp	0	0	0.0.0.0:41774	0.0.0.0:*		937/avahi-daemon:


```

Also i have  unplugged the computer from the network physically. I use a wireless network at home and i have disabled wireless connections on my machine. Only using mobile broadband. Still the virus comes. No pendrives are plugged into this machine either.

---

### Post by uRock on 2010-09-27
Where is this file located within the file system?

---

### Post by abhinav90 on 2010-09-27
@urock: the file is located in the home folder the exact location is /home/abhinav/Desktop/ubuntu_share

I have seen that the exe file returns within 15 to 20 minutes of deleting. After the deletion i did not do any specific task which might have caused this. I simply had a ppt open in openoffice and the exe reappeared in sometime when i checked the folder. It also shows the date of creation of the exe as 4th August 2004 even though it just came. Also another plain text file called khy gets created with it.

---

### Post by cariboo on 2010-09-27
Are you actually deleting the file, or just sending it to the trash bin?

---

### Post by cprofitt on 2010-09-27
> **abhinav90 said:**
> @urock: the file is located in the home folder the exact location is /home/abhinav/Desktop/ubuntu_share

I have seen that the exe file returns within 15 to 20 minutes of deleting. After the deletion i did not do any specific task which might have caused this. I simply had a ppt open in openoffice and the exe reappeared in sometime when i checked the folder. It also shows the date of creation of the exe as 4th August 2004 even though it just came. Also another plain text file called khy gets created with it.

Why are you running mysql. postgres and apache on the box?

If you shut down the sharing service, delete the file -- does it still come back?

---

### Post by uRock on 2010-09-27
A delete via CLI will make it go away for good.

I am not sure of the complete filename and path of the file which you need to get rid of, so here is an example of how to remove a file with the **rm** command.

```
rm ~/Desktop/ubuntu_share/dirty_virus_file.exe
```If your virus were named dirty_virus_file.exe, then the command would permanently remove it from the directory. If you want me to write the command exactly for your needs, then please post the output of ```
ls -ail ~/Desktop/ubuntu_share/*.exe
```PS. If you have multiple .exe files you are hosting, then please highlight the on you want deleted.

---

### Post by abhinav90 on 2010-09-27
@cariboo: i am actually deleting the file completely. I detect the file via clamAv and delete the file from ClamAv itself. I have also independently deleted the file and made sure no trace was left in the recycle bin.

@cprofitt: i am running apache, mysql and postgre on the box as i am a coder and run and code a lot of php based projects running on apache and sql.
I will try and stop the sharing access to the folder and see whether the file returns.

@Urock: as mentioned i have deleted the file from clamav before, which permanently deleted it.
Also the exe file name changes everytime, It was first Cool_Games.exe and later became exiae.exe

I have scanned the file through a windows machine Norton Antivirus and it to showed it as a virus as W32.Harakit Trojan,

Is it possible for a linux box to be hacked like this?

---

### Post by rookcifer on 2010-09-27
> **abhinav90 said:**
> 
I have scanned the file through a windows machine Norton Antivirus and it to showed it as a virus as **W32**.Harakit Trojan,

Note the bold text.  W32 = Windows.  It wont affect a Linux machine.

> Is it possible for a linux box to be hacked like this?

It's possible to be hacked, sure, but this trojan isn't going to be able to cause any harm.  I would wager that running an Apache server might have something to do with it, but it's hard to tell at this point.

---

### Post by abhinav90 on 2010-09-27
I understand that the trojan wont effect me, but doesnt this mean that i become a carrier infecting other windows machines in the same network as me. I wouldnt want my office windows machines to get infected through my box.

I also realized that earlier my router use to block all incoming traffic to my computer but since i started using mobile broadband is not there to protect my open ports. I should i protect this and still allow people to access my apache over the network.

---

### Post by cprofitt on 2010-09-27
> **abhinav90 said:**
> @cariboo: i am actually deleting the file completely. I detect the file via clamAv and delete the file from ClamAv itself. I have also independently deleted the file and made sure no trace was left in the recycle bin.

@cprofitt: i am running apache, mysql and postgre on the box as i am a coder and run and code a lot of php based projects running on apache and sql.
I will try and stop the sharing access to the folder and see whether the file returns.

@Urock: as mentioned i have deleted the file from clamav before, which permanently deleted it.
Also the exe file name changes everytime, It was first Cool_Games.exe and later became exiae.exe

I have scanned the file through a windows machine Norton Antivirus and it to showed it as a virus as W32.Harakit Trojan,

Is it possible for a linux box to be hacked like this?


I would actually suspect that a Windows box that has access to the SMB share is infected and keeps dumping that file in the share. You might want to see what is on your Windows boxes.

---

### Post by uRock on 2010-09-27
> **cprofitt said:**
> i would actually suspect that a windows box that has access to the smb share is infected and keeps dumping that file in the share. You might want to see what is on your windows boxes.
+1

---

### Post by solitaire on 2010-09-27
Just a query but: 
Would a virus infected "WINE" install cause behaviour like this?

---

### Post by cprofitt on 2010-09-27
> **solitaire said:**
> Just a query but: 
Would a virus infected "WINE" install cause behaviour like this?

It might... depending on how it was setup.

---

### Post by SeijiSensei on 2010-09-30
> **solitaire said:**
> Just a query but: 
Would a virus infected "WINE" install cause behaviour like this?

I think that's unlikely.  Wine runs out of the user's home directory in ~/.wine.  Unless you're mounting the share from within Wine, it's unlikely the Wine apps would see the share.

One solution I took to a similar problem on a client's network was to create a zero-length file in the shared directory with the same name as the dropped Trojan and gave it 0000 permissions:

touch badfile
chmod ugo-rwx badfile

That kept the client machines from replacing the Trojan after we removed it.

---

