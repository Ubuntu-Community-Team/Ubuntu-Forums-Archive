---
title: "error message when starting samba server"
date: 2010-11-22
forum: Server Platforms
---

### Post by mansour on 2010-11-22
Hi:
 
 
I am trying to share files between Windows XP machine, ubuntu server, debian server and ubuntu desktop. But mainly between ubuntu server and Windows XP computer.
I also like to learn samba, because probably I could do all this with ftp server as well. 
 
I set up and configured samba following the instruction on Online Ubuntu Server Guide. [https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)
 
But when I run the command:
 
[COLOR=blue]**sudo /etc/init.d/samba restart**[/COLOR]
 
I get:
 
**[COLOR=blue]bash: /etc/init.d/samba: No such a file or directory[/COLOR] **
 
I don't know what is wrong? 
I appreciate some help.
 
 
Mansour

---

### Post by Zeosa on 2010-11-22
try ```
/etc/init.d/smbd restart
```

---

### Post by mansour on 2010-11-22
> **Zeosa said:**
> try ```
/etc/init.d/smbd restart
```
 
 
Thank you Zeosa:
 
I did that, but got a long answer/complain from shell.
 
**root@ubuntu-server****:~# /etc/init.d/smbd restart**
**Rather than invoking init scripts through /etc/init.d, use the service(8) utility,**
**e.g. service smbd restart**
 
**Since the script you are attempting to invoke has been converted to an smbd start/running, process 1853**
**root@ubuntu-server****:~# **
 
**for some reason, service (number eight) is changed to an service (emotion icon) when I post.**

---

### Post by yettiman2208 on 2010-11-22
try

"sudo service smbd start"

also, stop and restart work too this way

---

### Post by mansour on 2010-11-22
> **yettiman2208 said:**
> try
 
"sudo service smbd start"
 
also, stop and restart work too this way
 
 
OK. Thank you yettiman2208. So it appears to be working well.
 
 
root@ubunttu-server:~# sudo service smbd start
start: Job is already running: smbd
root@ubunttu-server:~#
 
 
But I don't know how to access shared folder from my Windows XP.
This is the first time I am ever doing file sharing.
I don't see anything in windows explorer.
 
 
Mansour

---

### Post by yettiman2208 on 2010-11-23
A couple of things to work on first.

Have you spent anytime in the smb.conf file?
it is located in /etc/samba/smb.conf

This is where you define all the settings that are required in order for Samba to actually share something.

```
sudo nano /etc/samba/smb.conf 
```
will open the file and give you write priviledges.

Inside this file you need to define various parameters.
There should be #explanations for each section to guide you.

[WesternD]
path = media/WD  
writable = yes
public = yes
valid users = rhorie
inherit permissions = yes 

That is an example of a share that I use.

another thing you could do is 
```
tesparm /etc/samba/smb.conf
```

this will tell you if there are any significant errors in the smb.conf (not if your sharing is working, just if things are typed wrong)

From the xp box, ensure you are accessing the linux box directly.

from the start, run menu try and access the server using the IP address.

Not sure if you have tried all this, so if I am being simplistic I apologize

---

### Post by mansour on 2010-11-23
> **yettiman2208 said:**
> A couple of things to work on first.
 
Have you spent anytime in the smb.conf file?
it is located in /etc/samba/smb.conf
 
This is where you define all the settings that are required in order for Samba to actually share something.
 
```
sudo nano /etc/samba/smb.conf 
```
will open the file and give you write priviledges.
 
Inside this file you need to define various parameters.
There should be #explanations for each section to guide you.
 
[WesternD]
path = media/WD 
writable = yes
public = yes
valid users = rhorie
inherit permissions = yes 
 
That is an example of a share that I use.
 
another thing you could do is 
```
tesparm /etc/samba/smb.conf
```
 
this will tell you if there are any significant errors in the smb.conf (not if your sharing is working, just if things are typed wrong)
 
From the xp box, ensure you are accessing the linux box directly.
 
from the start, run menu try and access the server using the IP address.
 
Not sure if you have tried all this, so if I am being simplistic I apologize
 
Good Afternoon yettiman2208 :

Thank you for your response.

[Yes, I followed the online **Ubuntu Server Guide**, so I changed some of the settings in the /etc/samba/smb.conf which is the main config file for samba.

This is what I changed there.

[Global]

workgroup = HOME

security = user

interfaces = 127.0.0.1 192.168.1.101

# 192.168.1.101 is my ubuntu server's ip address
 

[Share]

comment = Ubuntu File Server Share

path = /srv/samba/share

browsable = yes

read only = no

create mask = 0755

valid user = mansour


I don't think that I even touched anything else yet.
It is a lengthy file which I don't understand very much else of it yet.



root@ubuntu-server:~# testparm /etc/samba/smb.conf[
Load smb config files from /etc/samba/smb.conf
rlimit_Max:rlimit_max (1024) below minimum windows limit(16384)
processing section "[share]"
processing section "[printers]"
processing section "[print$]"
Loaded services file OK.
server role: ROLE_STANDALONE
press enter to see a dump of your service definitions



and yes, I do have connection to my server from windows box for sure.
I can ping from windows box to my server successfully, and I already have a DNS server and a DHCP server on my ubuntu server, and is working well. I have disabled my router's DNS and DHCP server. So I definitely have connection to my server from my windows box.


But I don't yet how to access the shared  **/srv/samba/share**  folder from windows browser or from winodws explorer as the Guide asked me to.


Mansour

---

### Post by yettiman2208 on 2010-11-23
Try typing that into the "run." (Start --> Run)

smb://192.168.1.101

so recently moved to Mac and for some reason cannot recall the exact way to get Run to connect to a server.

(//192.168.1.101 might work also. If that fails try \\192.168.1.101)
i am having a brain fart and cannot recall exactly.

But in theory, when typed into the run command this will bring up a Window showing you the folders that are accesible on the server at the specified IP address.

-a large yetti

---

### Post by mansour on 2010-11-23
> **yettiman2208 said:**
> Try typing that into the "run." (Start --> Run)
 
smb://192.168.1.101
 
so recently moved to Mac and for some reason cannot recall the exact way to get Run to connect to a server.
 
(//192.168.1.101 might work also. If that fails try \\192.168.1.101)
i am having a brain fart and cannot recall exactly.
 
But in theory, when typed into the run command this will bring up a Window showing you the folders that are accesible on the server at the specified IP address.
 
-a large yetti
 
 
 
 
OK.
 
When I enter this in run:
smb://192.168.1.101
 
I get error message:[
Windows cannot access the specified device, path, or file.
You may not have the appropriate permissions to access the item.
 
When I enter this in run:
//192.168.1.101
 
I get error message:
Windows cannot find '//192.168.1.101'.
Make sure you typed the name correctly, and then try again. To search for file, click the start button, and then click search.
 
When I enter this in run:
//192.168.1.101
 
I get error message:
No network provider accepted the given network path.
 
 
 
mansour

---

### Post by SeijiSensei on 2010-11-23
> **mansour said:**
> When I enter this in run:
smb://192.168.1.101
 
I get error message:...

Windows uses the "back" slash character "\", not the "forward" slash character "/".  You need to use \\192.168.1.101\sharename.  I find the easiest thing for many people is to use the "Map a Network Drive" option in Network Connections.  Just choose a drive letter like Q: and map \\server\share to that.  Then Q:\ corresponds to the top of the shared directory.

---

### Post by mansour on 2010-11-23
I posted answers for you but it got chopped up, deleted, I don't understand.
 
None of your suggestions worked.
 
 
Mansour

---

### Post by SeijiSensei on 2010-11-24
> **mansour said:**
> I posted answers for you but it got chopped up, deleted, I don't understand.

Don't use colors; they're just distracting.

What precisely did you type?  I presume you replaced "sharename" in the suggestions above with the actual name of the exported Samba share?  

So you opened the "Map a Network Drive" tool, chose a letter, and entered the "UNC" name of the share (\\server\share).  Does Samba have an smbpasswd entry for the username that's logged into Windows?  

In /var/log/samba, you'll see log files for smbd and usually ones for each client as well.  What do they show?

---

### Post by mansour on 2010-11-24
> **SeijiSensei said:**
> Don't use colors; they're just distracting.
 
What precisely did you type? I presume you replaced "sharename" in the suggestions above with the actual name of the exported Samba share? 
 
So you opened the "Map a Network Drive" tool, chose a letter, and entered the "UNC" name of the share (\\server\share). Does Samba have an smbpasswd entry for the username that's logged into Windows? 
 
In /var/log/samba, you'll see log files for smbd and usually ones for each client as well. What do they show?
 
 
The path to share is at the root prompt   :~#  **\srv\samba\share**
and share is a folder of course, which is empty now.
 
1) I put \ubuntu-server\home\srv\samba\ in the URL of my Win XP browser.
**Windows can not find '\ubuntu-server\home\srv\samba\'.**
**Check the spelling and try again.**
 
2) I put that in Run: \ubuntu-server\home\srv\samba\
**Windows can not find '\ubuntu-server\home\srv\samba\'**
**Make sure you typed the name correctly, and then try again. To search for a file, click the start button, and then click search.**
 
 
3) "Map a Network Drive" tool
 
Drive Z:
Folder: \ubuntu-server\home\srv\samba\
 
I get:
**The drive could not be mapped because no network was found.**
 
 
4) When I run :
 
ls /var/log/samba/
 
I see these files there:
 
 
cores (dir- blue) 
log.nmbd 
log.smbd 
log.192.168.1.101 
log.192.168.1.117 
log.ubuntu-server 
log.winbindd
log.winbindd-dc-connect
log.mac0033df9c86b0 
log.wb-BUILTIN 
log.winbindd-idmap
log.wb-UBUNTU-SERVER
 
although not in this order though.
 
Sorry but I can not possibly copy all the** log.smbd** here, is very long.
I don't know how to transfer it to my Windows machine, so that I can paste it here for you to see, and help me with it. I know how to upload it to a scp server. But no other way comes to my mind. It is lots of lines.
 
 
mansour

---

### Post by SeijiSensei on 2010-11-24
In every case you had only one initial slash.  Please read more carefully.  They syntax is \\server\share.  "Share" in this case refers the share's name in brackets in smb.conf.  Try using the server's IP address for "server" rather than a symbolic name.

Have you ever mounted a Windows share onto another Windows machine?  It's not any different with Samba.

---

### Post by mansour on 2010-11-24
> **SeijiSensei said:**
> In every case you had only one initial slash. Please read more carefully. They syntax is \\server\share. "Share" in this case refers the share's name in brackets in smb.conf. Try using the server's IP address for "server" rather than a symbolic name.
 
Have you ever mounted a Windows share onto another Windows machine? It's not any different with Samba.
 
 
Sorry. You are right, I made a mistake.
OK. I tried again, this time with correct syntax.
I can not post here, it doesn't display my answer. It is eaten away.
 
 

1) In the Run:

---

### Post by yettiman2208 on 2010-11-25
Just use the quick reply option. (bottom right of the posts)

instead of putting the entire share pathway just use the final one.

try \\IPaddress\share

like literally only include the \share (make sure Capitals are correct. You should not need the whole pathway (like /home/srv/samba/share etc.

---

### Post by mansour on 2010-11-25
I tried again but it was deleted again. It seems almost like someone is playing a trick with me here. It feels like that anyway, but why I don't get it. I am not able to post a reply to someone's post !!!????. where are the admin people here? This is a bad joke on the forum. Maybe some sort of malacious script is doing this, but why????

---

### Post by mansour on 2010-11-25
>  
Originally Posted by **SeijiSensei** [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10159770#post10159770") 
*In every case you had only one initial slash. Please read more carefully. They syntax is \\server\share. "Share" in this case refers the share's name in brackets in smb.conf. Try using the server's IP address for "server" rather than a symbolic name.*
 
*Have you ever mounted a Windows share onto another Windows machine? It's not any different with Samba.*
 

 
 
*1) When I type \ \192.168.1.101\share\ in Run in my Windows box: *
***No network provider accepted the given network path.***
 
*2) When I type \ \192.168.1.101\share\ in URL of the browser:*
***Windows can not find '\ \192.168.1.101\share\'. Check the spelling and try again.***
 
*3) Mapping a network Drive:*
 
***Drive: Z***
***Folder: \ \192.168.1.101\share\***
***I enter my ubuntu-server username and password, but it won't accept the password. There is no error message, but just would spit out the password.***
 
 
*4) No I have you never mounted a Windows share onto another Windows machine.*
*This is the first time I am trying to do file sharing actually.*
 
 
*mansour*

---

### Post by cariboo on 2010-11-25
Seeing as you are new at this, in Windows go to My Networks or Networks in Win 7, if you have set up the shares properly, they should show up there. You should then be able to just double click the share.

---

### Post by mansour on 2010-11-25
> **cariboo907 said:**
> Seeing as you are new at this, in Windows go to My Networks or Networks in Win 7, if you have set up the shares properly, they should show up there. You should then be able to just double click the share.
 
 
Well my Windows machine is a Windows XP, but I don't see anything in my Network Connections. 
I am sure I have done something wrong in the smb.conf file, or a permission somewhere is set wrong but I don't know how to track it. If I knew how to upload my smb.conf here for you to see, I would, but I don't know how.
 
I know how to upload my smb.conf to a scp server.
 
 
mansour

---

