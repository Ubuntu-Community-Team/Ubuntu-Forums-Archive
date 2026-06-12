---
title: "servers"
date: 2011-01-02
forum: Server Platforms
---

### Post by wizzy2k10 on 2011-01-02
Hello

I own a website and i'm wanting to add php into it now currently with me having Windows 7 Home Premium it doesn't have a feature I need (Internet Information Server) and no way am I paying £150 ish to get it so I was wondering if I setup a server within xubuntu  would I be able to preview php files prior to uploading them to my host? if so what would I need and how would I do this? I am guessing apache or samba server is required for a start?

Thanks

---

### Post by tgalati4 on 2011-01-02
To get a web server going:

sudo apt-get install tasksel

tasksel --list-tasks

sudo tasksel install lamp-server

Reboot and point your browser to:

[http://localhost/](http://localhost/)

That will be $0.00.

---

### Post by wizzy2k10 on 2011-01-02
Ah easy as that :) well if I have any issues i'll pop back :)
 
Thanks

---

### Post by wizzy2k10 on 2011-01-02
Hello

Thats that setup so now where do I put the documents etc... also I don't need mysql as of yet but incase I do how is that setup?

Thanks for the help

---

### Post by tgalati4 on 2011-01-02
Put your files in /var/www.  Include an index.html file with some basic stuff in it and put all your *.php files as well.

There are some excellent tutorials on the web for html and php programming.

mysql is loaded but you only need it if you run a service that uses it.  For instance if you install sugarcrm ([http://sugarcrm.com](http://sugarcrm.com))  the installer will create the various mysql databases required by the program.

For mysql administration, there is a web-based tool called mysql-admin.  For a list of mysql stuff try:

apt-cache search mysql

You haven't mentioned what the web page is for or how you are going to use it.

---

### Post by wizzy2k10 on 2011-01-03
Hello
 
The pure reason for the website is I know some users are looking for a place to upload their projects to and I would like to offer this in the near future but i'm planning early so I know what i'm doing later.
 
I have a reasonable understanding on html and I have a book on php so i'm going through that and after I plan on going into Javascript and Ajax at a later date.
 
I would like a mini server at the moment to practice php as my version of Windows 7 doesn't support Internet Information Server which is needed to view these files apparantly according to my version and I would need to spend about £150 ish to get this service which I could use that money to go towards a proper server at a later date. Plus I know all versions of Ubuntu (or Linux in general)  are more stable for servers.
 
What would be the ideal server specs for a minimum server? I know a decent server board and about 8-12gb of ram is in order for a start and a 64bit operating system.
 
Any extra information would be useful and thanks

---

### Post by woodman231 on 2011-01-03
Wizzy just as a suggestion you may want to download vmware to your Windows 7 computer and then download a LAMP Stack appliance for it.

VmWare Website:
[http://www.vmware.com/](http://www.vmware.com/)

A couple of places you can get LAMPStack appliances from:
Turnkey Linux:
[http://www.turnkeylinux.org/lamp](http://www.turnkeylinux.org/lamp)

Bitnami:
[http://bitnami.org/stack/lampstack](http://bitnami.org/stack/lampstack)

If everything suites your needs you may find that the hardware that your Windows 7 computer has is the hardware you would want your server to run.

Thanks,
Sean W.

---

### Post by wizzy2k10 on 2011-01-03
Thanks for that woodman231 i'll also look into that in a few days or so :) I got the server up and running as per above mind so I can see whats what and for some reason on virtual box I downloaded the 64bit version of Ubuntu and it never liked it told me my processor wasn't the right one yet when I used wubi it downloaded the 64bit version and went in nicely haha suppose thats computers for ya :)
 
At the moment I only have a 2.6 / 2.8 quad core, 4gb of ram and a 160gb hard drive so I know the hard drive will need changing at some point in time but its ok for now although its about 3 years old and still going strong :D good ole Western Digital :) must get 1tb when I can.
 
Thanks again

---

### Post by HermanAB on 2011-01-03
BTW, you can get Apache for Windows and it works fine for web developers.

---

### Post by FloM on 2011-01-04
Hello,

If you only need the server for project work and you have a static IP you could use WAMP wich is Apache, PHP, MySQL on Windows
Here is: [http://www.wampserver.com/en/](http://www.wampserver.com/en/)

I have WAMP installed on Win 7 64bit

Good luck,
Flo

---

### Post by SeijiSensei on 2011-01-04
> **wizzy2k10 said:**
> What would be the ideal server specs for a minimum server? I know a decent server board and about 8-12gb of ram is in order for a start and a 64bit operating system.

If that were true, I wouldn't have been able to host my clients' websites for the past dozen years.  Web hosting is a very lightweight server task.  I've run sites on as little as a 733 MHz P3 with 512MB of ram.  These days I use a virtual server at [Linode]("http://www.linode.com/").  It also has 512MB of memory and does spam/virus scanning of emails to boot.

---

### Post by wizzy2k10 on 2011-01-05
Hello
 
Unfortunately I am on a dyanamic IP :( but I have it setup so I can now play around :D I have also got some ubuntu documentation so I can get my hands on the commands :) I also have a pocket guide so i'm well on my way :) he says :lolflag:
 [quote=SeijiSensei]
If that were true, I wouldn't have been able to host my clients' websites for the past dozen years. Web hosting is a very lightweight server task. I've run sites on as little as a 733 MHz P3 with 512MB of ram. These days I use a virtual server at [[COLOR=#444444]Linode[/COLOR]]("http://www.linode.com/"). It also has 512MB of memory and does spam/virus scanning of emails to boot.
[/quote]
 
Ah thanks for that :)
 
Once again thanks for the help

---

