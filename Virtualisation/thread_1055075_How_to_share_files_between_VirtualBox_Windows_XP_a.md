---
title: "How to share files between VirtualBox: Windows XP and Ubuntu Intrepid?"
date: 2009-01-30
forum: Virtualisation
---

### Post by looi76 on 2009-01-30
Hi, can someone please provide me a step-by-step tutorial to show me how to share files between VirtualBox and Ubunut 8.10?

---

### Post by buffy^ on 2009-01-30
If your virtual box is on the network, you should be able to view shard views over the network. You could open your browser and type ```
smb:\\compuername\share
```

---

### Post by looi76 on 2009-01-30
VirtualBox is not in the network. How can I add it to the network?

---

### Post by buffy^ on 2009-01-30
I have not used virtual box before so I cant say. There might be an otption to sharenetwork cards.

---

### Post by Cypher on 2009-01-30
In the settings for your paricular virtual machine in Virualbox you can create a shared folder and that folder will be available within XP as \\vboxdrv\<share name>..

---

### Post by sumit.kalra999 on 2009-01-30
Hi,
when you start virtual box, and select the operating system which you want to run, change the properties of USB,CD/DVD drive  from disable to enable, It let you share your files via these storage media

---

### Post by dorkdork777 on 2009-01-30
I'm assuming you mean Ubuntu 8.10 as the host and Windows XP as the client.

The way I do this is very simple - shared folders via VirtualBox (as mentioned by Cypher two minutes before me :)).

To do this, start VirtualBox, click your Windows XP virtual machine, click Settings (at the top), then in the window that pops up, on the left column click "Shared Folders". On the right, hit the + folder button. Another window will pop up. Select which folder you want to share, give it a name, then hit OK.

Then, your shared folder will show up in My Network Places on WXP. :)

---

### Post by bodhi.zazen on 2009-01-30
For the most part samba should work out of the box.

When setting up virtualbox use bridged networking -> right click a folder -> sharing ;)

---

### Post by sumit.kalra999 on 2009-01-30
Hi,
other way to share your files via Share folder
To share files, in your host operating system, share files which you want or require
In guest operating system, Click on "Machine menu" to enable share folders and browse the folder in it

---

### Post by sumit.kalra999 on 2009-01-30
Third way to share files is using Internet, just mail files to your mail id from one OS and read your mails from another OS.
Its simple but only for files of small sizes

---

### Post by Andcor on 2009-01-30
You might want to make clear if ubuntu 8.10 is the host or the quest. If Windows is installed in virtualbox i have had some problems of mounting the network share using the graphical tools. In stead i found a command in the documentation for virtualbox that looked something like this:
```

net use z \\vboxsrv\sharename

```
which will mount the share "sharename" as the z-drive. I'm not totally sure of the syntax of the command, but you might be able to find it in the documentation as I did.

---

### Post by HermanAB on 2009-01-30
Actually, the easiest way to share files is with good old FTP.  Install Filezilla server and client on Windows.

Cheers,

Herman

---

### Post by cyberbuff on 2009-04-30
> **sumit.kalra999 said:**
> Third way to share files is using Internet, just mail files to your mail id from one OS and read your mails from another OS.
Its simple but only for files of small sizes
Dropbox is a better choice than emailing. [http://getdropbox.com](http://getdropbox.com)

---

### Post by meka4996 on 2009-05-07
VirtualBox Access Shared Folder From Windows XP
[http://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/](http://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/)
Problem: Could not see or Nothing appears in "My Network Places" in folder window
Solution: 
Install newest VirtualBox...
From the VirtualBox's menu, go to Devices &#8594; Shared Folders... to add/remove the folders of the host operating system
In guest OS [MS Windows, XP for my case], DO NOT open folders window... ONLY USE WINDOW EXPLORER by Start Menu&#8594; Run... &#8594; type "explorer" &#8594; Ok

Now, carefully click on the expand icon (the icon with +) right next to My Network Places. Make sure you click exactly on the expand icon. If you accidentally clicked on My Network Places, you ruined everything and you will have to go back and start all over again. After expanding the My Network Places branch, you should be able to see Entire Network right underneath:

Now expand the Entire Network branch, too, and you should be able to see VirtualBox Shared Folders:
Expand VirtualBox Shared Folders. Normally, you should be able to see your shared folders in there.

Right click on the shared folders, select "Map Network Drive" ...
Star Menu-> My Computer, where now you should be able to see the shared folders under "Network Drives" 
Right click on the shared folders, then "Create Shortcut" ... put it where it is handy, enjoy =)

---

### Post by axel206 on 2009-05-09
This is what you need:

[How to install Linux on Windows using VirtualBox](http://www.my-guides.net/en/content/view/112/26/)

---

### Post by le1 on 2009-10-20
watch it:

[http://www.youtube.com/watch?v=75FeKOkpSKk](http://www.youtube.com/watch?v=75FeKOkpSKk)

---

### Post by gdonwallace on 2009-10-20
The other way to share depends on how everything is installed.  If linux is the host that VB is installed on and you have XP running inside VB, then there is a easy way to share folders.  I have done this on my machine.

Open Nautilus, right click the folder you want to share.  There should be an option on the menu that comes up to create the share.  Fill in the information on the screen that comes up.  Make sure to put a check mark in the last box.  Next run VB, and setup a network drive connection to that shared folder.  

This will work if you have VirtualBox installed on Linux, and running XP inside VirtualBox.

---

### Post by tobik999 on 2009-11-26
> Now, carefully click on the expand icon (the icon with +) right next to My Network Places. Make sure you click exactly on the expand icon. If you accidentally clicked on My Network Places, you ruined everything and you will have to go back and start all over again. After expanding the My Network Places branch, you should be able to see Entire Network right underneath:

:popcorn: That did the trick!!!!!! FInally after hours of fighting with WiXP I am sharing LOL

PS: I hate Windows! Says it would create a link to the network places but just does in windows worlds!

---

### Post by Dai777 on 2009-11-28
[http://dai-videotutes.blogspot.com/2008/11/virtualbox-shared-folders-in-linux.html](http://dai-videotutes.blogspot.com/2008/11/virtualbox-shared-folders-in-linux.html)

[http://dai-videotutes.blogspot.com/2008/10/part-1-setting-up-virtualbox-shared.html](http://dai-videotutes.blogspot.com/2008/10/part-1-setting-up-virtualbox-shared.html)

[http://dai-videotutes.blogspot.com/2008/10/part-2-setting-up-windows-side-of.html](http://dai-videotutes.blogspot.com/2008/10/part-2-setting-up-windows-side-of.html)

This is th eway I got things to work.

---

