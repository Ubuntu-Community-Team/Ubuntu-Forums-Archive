---
title: "Samba - Can print test pages but can't print from applications"
date: 2012-06-23
forum: Server Platforms
---

### Post by BobMarso on 2012-06-23
I'm a true absolute beginner and got no hits when I searched the forum, so here goes...

I am installing Samba on Ubuntu Desktop to make a file and print server.  I have the file server operating correctly but am having problems with the print server.

I am using the instructions in the Windows Networking section of the online documentation and have also consulted the Samba HOWTO.  After making the suggested changes to smb.conf, I am able to find a printer on the server, install the printer driver on the Windows client, and successfully print a test page from the installation window on the client.  However, when I try to print from an application (specifically Word and Acrobat), it will not print.  I also cannot print from another client machine running Ubuntu Desktop.

When I check the document print status on the Ubuntu client, it says the document printing is pending, then processing, the held.  When I right click on the document and release it to print, it eventually goes back to held and shows a size of 0k.

Any suggestions as to what I may have done wrong?  Why can I print a test page but not print from an application?

Thanks in advance!

---

### Post by bab1 on 2012-06-24
> **BobMarso said:**
> I'm a true absolute beginner and got no hits when I searched the forum, so here goes...

I am installing Samba on Ubuntu Desktop to make a file and print server.  I have the file server operating correctly but am having problems with the print server.

I am using the instructions in the Windows Networking section of the online documentation and have also consulted the Samba HOWTO.  After making the suggested changes to smb.conf, I am able to find a printer on the server, install the printer driver on the Windows client, and successfully print a test page from the installation window on the client.  However, when I try to print from an application (specifically Word and Acrobat), it will not print.  I also cannot print from another client machine running Ubuntu Desktop.

When I check the document print status on the Ubuntu client, it says the document printing is pending, then processing, the held.  When I right click on the document and release it to print, it eventually goes back to held and shows a size of 0k.

Any suggestions as to what I may have done wrong?  Why can I print a test page but not print from an application?

Thanks in advance!

I'm not sure you have done anything wrong.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=12047736") for a discussion about using Samba as a print server.

Are you reading [**_[COLOR="Blue"]this chapter[/COLOR]_**]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html") of the Samba Howto?

It would help if you posted your smb.conf file.  Use the **[SIZE="2"]#[/SIZE]** to wrap the text in [code] brackets please.

What type of printer are you using?

---

### Post by BobMarso on 2012-06-24
bab1,

Thanks for the reply.  Here is my smb.conf.  I'm not sure what "Use the **[SIZE=2]#[/SIZE]** to wrap the text in [code] brackets" means.  Also, I was not aware of the CUPS reference.  I'll check it out.  I'm assuming from the discussion you referenced that I should not use samba to print because of bugs in samba.  I should use cups instead?

[global]
   workgroup = MyNet
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
     security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   load printers = yes
   printing = cups
   printcap name = cups
   usershare allow guests = yes
[homes]
   comment = Home Directories
   browseable = no
   read only = no
   create mask = 0755
   directory mask = 0755
   valid users = %S
[profiles]
   comment = Users profiles
   path = /home/samba/profiles
   guest ok = no
   browseable = no
   create mask = 0600
   directory mask = 0700

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
   write list = root, @lpadmin
[cdrom]

[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browseable = yes
    guest ok = yes
    read only = no
    create mask = 0755

---

### Post by bab1 on 2012-06-24
> **BobMarso said:**
> bab1,

Thanks for the reply.  Here is my smb.conf.  I'm not sure what "Use the **[SIZE=2]#[/SIZE]** to wrap the text in ```
 brackets" means.  Also, I was not aware of the CUPS reference.  I'll check it out.  I'm assuming from the discussion you referenced that I should not use samba to print because of bugs in samba.  I should use cups instead?



You use CUPS in any event. I highlighted the references in the pertinent sections of *your* smb.conf file 

[CODE][global]

   load printers = yes
   printing = [COLOR="Red"]cups[/COLOR]
   printcap name = [COLOR="Red"]cups[/COLOR]


```

None of my printers are attached to a host.  They are all network attached and I use CUPS on each local host to manage the printing activities.

You might read [**_[COLOR="Blue"]this[/COLOR]_**]("http://wiki.samba.org/index.php/Samba_as_a_print_server") from the samba,org wiki on Samba as a print server.

---

### Post by BobMarso on 2012-06-25
Thanks again, bab1.  It will take me a few days to filter through all this considering the work week has started, but I'll post the results when I get there.

---

### Post by BobMarso on 2012-08-11
I'm not sure why, but I loaded Webmin and checked what I thought were the correct settings.  In the Samba Windows File Sharing > Windows to Unix Printing > Printing Options drop-down window, CUPS was not selected.  Selecting CUPS fixed the problem.

I thought this should have been defined based on my smb.conf file, but I was obviously wrong.

I can now print, however, I have a very long delay between hitting "Print" and the printer starting, like several minutes compared to a couple of seconds, depending on the size of the print job.  I'll open this as a separate post so everyone can consider this one solved.

---

