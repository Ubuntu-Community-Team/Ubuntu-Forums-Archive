---
title: "Rootkits??"
date: 2006-01-30
forum: Server Platforms
---

### Post by linuxden on 2006-01-30
Hi All,

I hope you had a good weekend...

Got myself a question... How much are rootkits a threat to users of linux??
On most of the reading they seemed to be a darned nuissance!!! Hard to monitor and hard to remove!!! 

Am getting freaking worried here...

Anyone had any experience with one..?

---

### Post by rjwood on 2006-01-30
I believe rootkit's have to be tailored for specific OS's. I don't know of any affecting Ubuntu or Linux in general. I may be incorrect though.

---

### Post by linuxden on 2006-01-30
There seems to be a majority of linux rootkits... Thats what freaks me out!!! 

I am just wondering if anyone has experience with them, Ie remvoing them, preventing them, etc etc...

---

### Post by ardchoille on 2006-01-30
There are lots of rootkits for Linux and the best way to make sure you completely remove one after infection is to do a complete OS re-install. However, there are two good apps in the main repo that are designed to detect rootkits. These two apps are rkhunter and chkrootkit. I have been using them for a couple of years and I feel they are very good at what they do.

---

### Post by linuxden on 2006-01-30
Thx Ardchoille will look into them...

Also how common are these rootkits??? Are they a real threat?? have you personaly had a bad experince with them?

---

### Post by ardchoille on 2006-01-30
[QUOTE=ubuntulifestyle]Thx Ardchoille will look into them...

Also how common are these rootkits??? Are they a real threat?? have you personaly had a bad experince with them?[/QUOTE]
I've never had a rootkit experience.. probably because I keep my system locked down and I am behind a router that does NAT. However, you should consider rootkits a genuine threat. Computer security is an ongoing process, not a destination :)

---

### Post by nocturn on 2006-01-30
Be aware that a rootkit is not a virus, though sometimes it is in the payload of a virus.

You can only be infected with one if someone already got access to your system through another way (weak user password).

I have been on Linux since 1999 and I've been a sysadmin for years, I have never seen a rootkit infection on any of my machines.  

Taking the proper security measures (good passwords, patching, firewalls etc) will go a long way in preventing them.

---

### Post by linuxden on 2006-01-30
Ok, I have 2 router/firewalls + firestarter protecting my network so in effect am pretty secure with people seeing my machines yet alone gaining un-authorized access...

Would one use "ssh" for example to gain access then install the said rootkit?

I have included a link to a white-paper in pdf format...(that is what sparked off a bit of fear in me...)

[http://www.sans.org/rr/whitepapers/linux/901.php](http://www.sans.org/rr/whitepapers/linux/901.php)

---

### Post by nocturn on 2006-01-30
[QUOTE=ubuntulifestyle]Ok, I have 2 router/firewalls + firestarter protecting my network so in effect am pretty secure with people seeing my machines yet alone gaining un-authorized access...

Would one use "ssh" for example to gain access then install the said rootkit?

I have included a link to a white-paper in pdf format...(that is what sparked off a bit of fear in me...)

[http://www.sans.org/rr/whitepapers/linux/901.php](http://www.sans.org/rr/whitepapers/linux/901.php)[/QUOTE]

Basicly, the rootkit is installed after one gains access to a machine.  They can help elevate the privileges to root and to mask the intrusion.

Protecting against rootkits is good, but it is the second line of defense after the intrusion.  

Another good security measure is backups.  They can help determine which data was altered and when, but also help recover from an intrusion.

---

### Post by gooner on 2006-01-30
I recently read that it would eventually or possibly already be able to go as deep as the system bios. If this is true would it be possible to create a generic rootkit that could effect any computer system regardless of what OS it's running?

---

### Post by mdmarmer on 2006-01-30
Possibly. It hasn't happened yet.  The route of infection would be thru code that is common to different OS/hardware, such as ACPI ... Also they've said that Oracle is vulnerable.

This has been discussed at BlackHat Federal 2006, a security conference that took place in Wahington DC last week. That's why it's in the press.

See here
Rootkits are headed for your BIOS
    [http://it.slashdot.org/article.pl?sid=06/01/27/1327228&from=rss](http://it.slashdot.org/article.pl?sid=06/01/27/1327228&from=rss)
    
    
    Researchers say rootkits are headed for BIOS
    [http://www.theregister.co.uk/2006/01/27/rootkits_bios/](http://www.theregister.co.uk/2006/01/27/rootkits_bios/)
    [http://www.securityfocus.com/news/11372?ref=rss](http://www.securityfocus.com/news/11372?ref=rss)

Mike

---

### Post by HJThis on 2006-01-30
Hello,mdmarmer

I thank you for this great news.

now could someone please tell me just how do you
go about using chkrootkit & rkhunter using.

a Live-CD i just can't seem to find info on this
& would you use say Ubuntus Live-CD????

anyone at all please

Thank you

---

### Post by nalmeth on 2006-01-30
Applications --> Accessories --> Terminal
sudo apt-get install chkrootkit rkhunter
They might get linked to your menu, but if not, you could probably just run them in a terminal.

---

### Post by HJThis on 2006-01-30
Hi,nalmeth

Thanks for the reply but i have them installed on the HD
but someone was saying it is best to scan the PC using
a Live-CD but would you use say the Ubuntu Live-CD???

if so anyone have any idea how to go about this
i just can't seem to find much info on this or do i have
this all wrong.

Thank you

---

### Post by linuxden on 2006-01-30
Backups are already in my weekly tasks... So at least that is good... I guess from the artcile its just plain easy to format and restore the backups in case of rootkit access...

Have a nice evening all!

---

