---
title: "Some Server Install / Basic Running Questiosn"
date: 2008-05-20
forum: Server Platforms
---

### Post by Cpuboye11 on 2008-05-20
Hi,

Ubuntu lover here :-) Got Ubuntu running primary on my dell and so far, besides for a little bugs... its great A++ On the making guys.. Well any ways, my server:


Got a server running Windows 2000....
p3 maybe >500Mhz?? Maybe....
512mb... 
Some hard drives.. Lol.... total of around 120 GB ish...

I installed the 7.10 server on a computer just to look at it.. No problem showed during install... But when it loaded, it would just go to a command prompt...
 Is it supposed to do this??

It other words- can any one forward me some links on basic running/install of the server.... - Referring to installing a Graphics Interface if there is not one, and if it is possible. 

As you can see I am not as well informed or gifted with the knowledge of the server edidtion. Any information would be greatly appreciated. 

Thank you,
Kyle
ComptuerFreek:)

---

### Post by Iowan on 2008-05-20
Basic server install does not include Gui/desktop, but one can be added. [  Here]("http://ubuntuforums.org/showthread.php?t=800046") is a thread showing several options.

---

### Post by hyper_ch on 2008-05-21
there's no gui needed for operating a server...

configuration is done through editing config files of the services and in the end, the less stuff is running the more power the server has to fulfill its tasks (serving things to others) ;)

Waht do you want to do with the server? Just fileserver? Webserver? Router? DNS Server? Email Server? ....?

---

### Post by windependence on 2008-05-21
Here is what Canonical has to say about GUI and security:

> No X server by design

By design, Ubuntu Server Edition does not include an X server. This is a deliberate choice as we believe that most servers should be serviced remotely, are safer without the addition of code that needs direct communication from user space to hardware, and should not be used as a desktop by their administrator.

    "So I applaud the Ubuntu team&#8217;s common sense (and courage) in keeping the X Window System out of the default installation of Ubuntu Server."
    --Mick Bauer in April 2008 Linux Journal - "Security Features in Ubuntu Server"


[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)

GUIs shoud be kept OFF a server. If you want a GUI, more than likely you should be using the desktop edition.

-Tim

---

### Post by Cpuboye11 on 2008-05-25
Thank you for all of your help and information.

And to answer the above questions; yes, i would like to run a file server- web-email- and dns and dhcp servers- i would really like to have a computer on the front line that i can edited easier then a router.

---

### Post by hyper_ch on 2008-05-26
if you want to run an email server you'll need a static IP.

for web/email/dns server have a look at the perfect Howtos at [http://www.howtoforge.com](http://www.howtoforge.com)

Making it also a fileserver isn't that complicated then. Use SAMBA if you have to share with windows clients or use NFS or SSHFS if it's just among linux clients OR just use SFTP (ftp over SSH with WinSCP as client on windows).

---

