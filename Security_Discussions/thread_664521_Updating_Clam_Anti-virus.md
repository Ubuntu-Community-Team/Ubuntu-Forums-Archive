---
title: "Updating Clam Anti-virus"
date: 2008-01-11
forum: Security Discussions
---

### Post by enoughsaid05 on 2008-01-11
When I start clamtk antivirus, it says that my signature is 144 days old, and I need to update it. But I can't update it because I am not on root account.

How do I update using root, with graphical interface?

---

### Post by bumanie on 2008-01-11
This how I believe things work with clamav.
I am not sre how to update clamav using a GUI, but to update via command line you first off have to have clamav-daemon activated (you can do this in synaptic). After that, it a simple process of typing sudo freshclam in terminal to update clamav
Hope this helps you.
If you wait a bit, someone else may know how to do it via GUI.

---

### Post by Jon &quot;Yogi&quot; on 2008-01-14
If you are able to update via the terminal, then you can use the gksudo command to run the gui as root. To do this..

1. Right-click on the Menu bar (the Ubuntu logo, Applications, Places, System bar on a default install)

2. Go to Edit

3. Then find the GUI launcher for ClamAV, then click on properties.

4. In the "Command" box, type in gksudo, so that the final command should look like:

```
gksudo clamtk %F
```

Hope that helps.

---

### Post by dcstar on 2008-01-15
> **enoughsaid05 said:**
> When I start clamtk antivirus, it says that my signature is 144 days old, and I need to update it. But I can't update it because I am not on root account.

How do I update using root, with graphical interface?

Install the **clamav-freshclam** package and it will update automatically.

---

### Post by iansane on 2008-01-15
I have the same problem but when I "sudo apt-get install clamav-freshclam" it says "clamav-freshclam is already the newest version"

The only way I know to update it is to allow root login and do it that way. I don't want to do that so if there is another way, please tell me.

Also gksudo clam %f doesn't work. Nothing happens when I try it through terminal or alt-f2.

---

### Post by iansane on 2008-01-15
OOPS, I left out the tk in clamtk.

That works but when I open it that way it says the definitions are up to date, and when I open it as a user it says no definitions found, contact administrator. I tried editing the freshclam.conf and clamd.conf files in /etc but they are just blank pages. Is there a way to add the path to definitions to users clamav? And should those conf files be blank?

---

### Post by iansane on 2008-01-15
Also this is what I get when I do terminal "sudo freshclam"

ian@lotus-control:~$ sudo freshclam
ClamAV update process started at Tue Jan 15 19:25:18 2008
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.91.2 Recommended version: 0.92
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.inc is up to date (version: 45, sigs: 169676, f-level: 21, builder: sven)
daily.cvd is up to date (version: 5484, sigs: 21696, f-level: 21, builder: acab)
ian@lotus-control:~$ 

I guess I will go to the url listed there and see if I can figure it out

---

### Post by nikoPSK on 2008-01-15
root account you can use sudo or login as root. :)

nikoPSK

---

### Post by iansane on 2008-01-15
well I tried a few different things. 

I downloaded and installed the latest stable release from the clamav website. About to remove it because now clam doesn't work at all. It flashes and goes away when I open it from terminal.

Found the conf files in /usr/local/etc not in /etc
I had to edit them before running freshclam.
Now when I run freshclam I get the following

ClamAV update process started at Tue Jan 15 20:11:46 2008
SECURITY WARNING: NO SUPPORT FOR DIGITAL SIGNATURES
See the FAQ at [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq) for an explanation.
main.inc is up to date (version: 45, sigs: 169676, f-level: 21, builder: sven)
daily.cvd is up to date (version: 5484, sigs: 21696, f-level: 21, builder: acab)
LibClamAV Error: Database Directory: /var/lib/clamav not locked
ian@lotus-control:~$ 

In response to the "log in as root" comment, Thanks but allowing log in as root is not advised. It is disabled by default for a reason. This aint Windows. LOL

---

### Post by nikoPSK on 2008-01-15
> **iansane said:**
> well I tried a few different things. 

I downloaded and installed the latest stable release from the clamav website. About to remove it because now clam doesn't work at all. It flashes and goes away when I open it from terminal.

Found the conf files in /usr/local/etc not in /etc
I had to edit them before running freshclam.
Now when I run freshclam I get the following

ClamAV update process started at Tue Jan 15 20:11:46 2008
SECURITY WARNING: NO SUPPORT FOR DIGITAL SIGNATURES
See the FAQ at [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq) for an explanation.
main.inc is up to date (version: 45, sigs: 169676, f-level: 21, builder: sven)
daily.cvd is up to date (version: 5484, sigs: 21696, f-level: 21, builder: acab)
LibClamAV Error: Database Directory: /var/lib/clamav not locked
ian@lotus-control:~$ 

In response to the "log in as root" comment, Thanks but allowing log in as root is not advised. It is disabled by default for a reason. This aint Windows. LOL

yes, I know it's advised against. :)

---

### Post by iansane on 2008-01-15
well I reinstalled, I added myself to the clamav group, and I still had to do "apt-get install clamtk" even though every package with the word clam was already installed through synaptic, but now I can do "sudo clamtk" from my user account and it lets me update.

I tested it on its own source package and it calls itself a virus. LOL but at least it's working now. I'll get the bugs worked out hopfully.

Oh by the way, now "gksudo clamtk %f" doesn't do anything. I don't know why but "sudo clamtk" is easier to type so that works. :-)

---

### Post by jwkungfu on 2008-02-02
BINGO!!!
Many thanks!!!!!!!!!!!
JW.

---

### Post by radioraheem8 on 2008-02-12
Hey, I'm having trouble with this too.  I have to prove to work that I have working antivirus, so I'm slogging through this ClamAV...bleh.  Anyways, sudo freshclam gives me this:

ClamAV update process started at Tue Feb 12 01:02:27 2008
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.90.2 Recommended version: 0.92.1
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.inc is up to date (version: 45, sigs: 169676, f-level: 21, builder: sven)
daily.inc is up to date (version: 5779, sigs: 39943, f-level: 21, builder: ccordes)

But of course running sudo clamtk tells me that my virus definitions are 306 days outdated.  The GUI doesn't give any option to update my definitions.  I've gone through the clamav faqs, but there's nothing there that I can really make sense of, being new to this OS.  

Any help is MUCH appreciated.  Thanks!

---

### Post by jwkungfu on 2008-02-12
Hi there,
Unfortunately, I don't think I can be of much help to you...
I'm not sure why my post was attached to where it was, because I when read what I supposedly replied Bingo to... I don't remember that post being the one that helped me??!!
I just opened up ClamTK to try and refresh my memory and i've clicked on all the buttons... but I can't find where it was that needs to be changed....
I'll have another go.... but so far.... sorry....   :O/
john

---

### Post by radioraheem8 on 2008-02-12
Anyone else?  Also, I need proof of an updated version, such as a screenshot.  How can I get one for this program...?

---

### Post by notbitmonk on 2008-02-13
I installed Clamtk through the add remove programs interface in Ubuntu.  To run Clamtk with permissions, i went to Terminal and typed ```
sudo clamtk
```  What this does is open the GUI with permission to update the database.  Well, it turns out that it will not update anything and that there are no virus signatures.  The webpage for ClamTk says not the use the version in the Ubuntu repositories because is too old and a new one is available from Debian in the testing repositories.  At this point I'm thinking of two possible solutions.
[LIST=1]
[*]Download the virus database definition
[*]Download the files from Debian through apt
[/LIST]
For the first solution, the database needs to be copied to a local folder and then moved to /etc/clamav and change the owner of the file to clamav.  I don't think this is the best solution because every update will be manual.
The second solution should be good enough since Ubuntu is based on Debian.  Problem is accessing the file through apt.  Last night I tried ClamAv suggestion of adding 
```
deb http://volatile.debian.org/debian-volatile etch/volatile main contrib non-free
```
After adding the line through the GUI I received errors regarding the signatures.  I think this is the best course since downloading the file directly from Debian is discouraged but I need yor help to manage it.  I'm trying to use ClamAv as a virus scanner for Evolution (which I'll need help setting up)

---

### Post by kitterma on 2008-02-13
The current clamav for Feisty and Gutsy have all the security fixes from the newest version.  For Feisty, you can get a newer version from feisty-backports.  The current version works with clamtk, but not some other applications, so it will take some additional testing before it's backported.

---

### Post by kitterma on 2008-02-13
> **notbitmonk said:**
> I installed Clamtk through the add remove programs interface in Ubuntu.  To run Clamtk with permissions, i went to Terminal and typed ```
sudo clamtk
```  What this does is open the GUI with permission to update the database.  Well, it turns out that it will not update anything and that there are no virus signatures.  The webpage for ClamTk says not the use the version in the Ubuntu repositories because is too old and a new one is available from Debian in the testing repositories.  

First, the clamtk advice is just wrong.  There is no problem with the current versions in the Ubuntu repositories (Edgy is an exception, but almost no one still runs that).  The 0 virus signatures is a clamtk bug.  If you install clamtk from feisty-backports it will work just fine.  The problem in feisty is that clamtk hadn't been updated to work with the newer clamav at the time feisty was released.

---

### Post by Scott O'Nanski on 2008-02-14
> **Jon "Yogi" said:**
> If you are able to update via the terminal, then you can use the gksudo command to run the gui as root. To do this..

1. Right-click on the Menu bar (the Ubuntu logo, Applications, Places, System bar on a default install)

2. Go to Edit

3. Then find the GUI launcher for ClamAV, then click on properties.

4. In the "Command" box, type in gksudo, so that the final command should look like:

```
gksudo clamtk %F
```

Hope that helps.

Huh????

I "right-click" on the Ubuntu logo, and I don't see any of that. All i see is "Help", "Edit Menus", etc. IS this information correct?

---

### Post by Tripmonkey_uk on 2008-02-14
First of all.. Visit the ClamAV website for the [latest definitions]("http://www.clamav.org/download/cvd/") (you have to right click and choose save link as... on the menu) and save them in your home directory, or just open up a terminal and do this..
> wget [http://db.local.clamav.net/main.cvd](http://db.local.clamav.net/main.cvd)
then..
> wget [http://db.local.clamav.net/daily.cvd](http://db.local.clamav.net/daily.cvd)
and..
> sudo mv daily.cvd  main.cvd /var/lib/clamav

Now enter your admin password & you should have completely up to date virus definitions :D


WARNING: This will only work if the ClamAV team use the same link every time for the daily updates?

To keep up to date with the definitions then, open a terminal &
> wget [http://db.local.clamav.net/daily.cvd](http://db.local.clamav.net/daily.cvd)
Which will download the latest definitions to your home directory, then..
> sudo mv daily.cvd /var/lib/clamav
..to transfer them to the correct directory again.

Just found this out myself and it should help you all out :)

p.s let me know if you need any more help and I'll see what I can do.

---

### Post by Cew27 on 2008-02-20
thanks for that 
althaugh when i scan the file system it only scans 6 files

---

### Post by timdollar on 2008-04-03
hi guys
can calmav be managed from a central place? i mean where you can see which machines are not updateding from the central server and which are.wheteher you can deploy clamav from a central location?

---

