---
title: "HOWTO: Find Your Installed Applications"
date: 2006-05-25
forum: Tutorials
---

### Post by user1397 on 2006-05-25
This guide helps you find your installed applications, so that if you installed something but it did not show up in the applications menu, you'll know where it is, and then you can make a launcher for it.  There is a great application that can search all of your installed applications. It's called Xfce 4 Appfinder - and don't be scared by the name, it works in Ubuntu, Kubuntu, and Xubuntu.  Now to install the program, open a terminal (Applications > Accessories > Terminal) and paste: 
```
sudo apt-get update&&sudo apt-get install xfce4-appfinder
```  It'll be in Applications > Accessories in GNOME, Kmenu > Utilities in KDE, and Xfce Menu > Utilities in XFCE.

To search for anything with a GUI search tool, you can either go to Places > Search for Files, or you can right-click on any panel, select **add to panel**, and select the Deskbar search tool, and search from there.

You can also install Beagle, a powerful search tool.  To install it, just paste into a terminal:  ```
sudo apt-get update&&sudo apt-get install beagle
```It will replace the Places > Search for Files tool, and now it is just Places > Search.

You can't really go back to the original search tool (well you can, but it's a bit tedious), but you can always just add the "Search for Files" applet to your panel (right-click on any panel, and select **add to panel**).

To search for anything with the terminal, you can either use the commands **locate** or **which**.
Locate is used more like a keyword-based search function.  For example, if you type in a terminal: 
```
locate java
```then all files with the name java would appear, and there are a lot more than one if you have java installed.  The which command will find the most important file associated with the keyword, i.e.
```
which java
```will reveal the location of the java executable, in /usr/bin/java, and that's it.

After you've found the location of your installed app, you have to make a launcher for it in the menus.  So right-click on your menu, and select **edit menus**.  Then go to whatever category you wish the program to be, and select file > new entry.  then you can choose the name, description, icon, and most importantly, the command for your application which you have just found.

---

### Post by user1397 on 2006-05-28
BTW, this app only finds actual applications, like totem or firefox, not everything that you install.   For example, if you want to know the location of a lib or a script, this app won't help you.

---

### Post by lukew on 2006-06-08
Hi,

You can also use the which command, for example.

which java


Luke

---

### Post by user1397 on 2006-06-24
[quote=lukew]Hi,

You can also use the which command, for example.

which java


Luke[/quote]yes that also works.

---

### Post by oskvaz on 2006-07-14
Excellent app. An easy way to see all our installed applications.

Thanks !!!

---

### Post by user1397 on 2006-07-15
> **oskvaz said:**
> Excellent app. An easy way to see all our installed applications.

Thanks !!!no prob

---

### Post by user1397 on 2006-10-23
***Updated this howto, now it includes all possible ways to search for stuff.  not much, i know, but still helpful.

---

### Post by Eric Weir on 2007-10-07
> **ubuntuman001 said:**
> ,,,,  There is a great application that can search all of your installed applications. It's called Xfce 4 Appfinder - and don't be scared by the name, it works in Ubuntu, Kubuntu, and Xubuntu.  Now to install the program, open a terminal (Applications > Accessories > Terminal) and paste: 
```
sudo apt-get update&&sudo apt-get install xfce4-appfinder
```  It'll be in Applications > Accessories in GNOME, Kmenu > Utilities in KDE, and Xfce Menu > Utilities in XFCE.

I just tried this. Two applications I'm pretty sure I installed -- Samba and DOSbox -- don't show up. However, they do show up in Synaptic, i.e., as installed. 

Otherwise, they're invisible on the system. They don't show up in the menus or when I search for them either as installed or available applications in Add/Remove Applications. 

I'd like to use them. How do I get access to them?

Thanks in advance,

---

### Post by user1397 on 2007-10-07
> **Eric Weir said:**
> I just tried this. Two applications I'm pretty sure I installed -- Samba and DOSbox -- don't show up. However, they do show up in Synaptic, i.e., as installed. 

Otherwise, they're invisible on the system. They don't show up in the menus or when I search for them either as installed or available applications in Add/Remove Applications. 

I'd like to use them. How do I get access to them?

Thanks in advance,have you tried the other commands in the first post? i.e. the *locate *and *which *commands?

---

### Post by Eric Weir on 2007-10-08
> **ubuntuman001 said:**
> have you tried the other commands in the first post? i.e. the *locate *and *which *commands?

Nope. Will do. 

Thanks,

---

### Post by Eric Weir on 2007-10-08
> **ubuntuman001 said:**
> have you tried the other commands in the first post? i.e. the *locate *and *which *commands?

Well, I tried them. Here's the results for which:[INDENT]eric@eric-linux:~$ which samba
eric@eric-linux:~$ which dosbox
/usr/bin/dosbox
[/INDENT]As you promised it would, locate produced a long list of files for Samba. I've selected a few that seem most relevent to my problem: 
[INDENT] eric@eric-linux:~$ locate samba
/usr/share/samba
/usr/share/doc/samba
/usr/lib/samba
/etc/samba
/home/eric/networking/samba install.odt
[/INDENT]So, it seems Samba is there. Now, how do I get it, and DOSbox, into my menus, or more elementally how do I get them to run? 

Thanks,

---

### Post by user1397 on 2007-10-08
> **Eric Weir said:**
> Well, I tried them. Here's the results for which:[INDENT]eric@eric-linux:~$ which samba
eric@eric-linux:~$ which dosbox
/usr/bin/dosbox

okay, that is the command to launch dosbox; to create a menu entry for it, right click on the menu bar (anywhere between applications, places, and system), and go to "edit menus" or something similar.  then in the correct category, make the new item with name "Dosbox" and command "/usr/bin/dosbox" (all without quotation marks)
[/INDENT]> **Eric Weir said:**
> As you promised it would, locate produced a long list of files for Samba. I've selected a few that seem most relevent to my problem: [INDENT] eric@eric-linux:~$ locate samba
/usr/share/samba
/usr/share/doc/samba
/usr/lib/samba
/etc/samba
/home/eric/networking/samba install.odt
[/INDENT]So, it seems Samba is there. Now, how do I get it, and DOSbox, into my menus, or more elementally how do I get them to run? 

Thanks,well samba is a different story...it is not really an application or a program per say, it is more like a set of networking tools that allows you to connect and share files to and fro a windows PC.

Since you have samba installed, all you have to do is go to system > administration > sharing, and configure the settings in there.

before you configure anything, see if you can already see your windows PC in places > network

---

### Post by Eric Weir on 2007-10-09
> **ubuntuman001 said:**
> okay, that is the command to launch dosbox; to create a menu entry for it, right click on the menu bar (anywhere between applications, places, and system), and go to "edit menus" or something similar...

OK, thats taken care of. 

> **ubuntuman001 said:**
> ...samba is a different story...it is not really an application or a program per say, it is more like a set of networking tools that allows you to connect and share files to and fro a windows PC.

Since you have samba installed, all you have to do is go to system > administration > sharing, and configure the settings in there.

before you configure anything, see if you can already see your windows PC in places > network

I believe Samba's been on my system from the beginning. Even before I "installed" it I was able to access the drives on my Windows machine. I.e., they showed up as "x-directory/smb-share" folders. Can that be? [I installed from the CD.]

I even found my way on my own, just poking around, to Shared Folders under system/administration. The problem I had then is the one I have now: how do I get Ubuntu to give permission to Windows to access Ubuntu's folders? 

When I go to Shared Folders there is already a shared folder --  home/eric. My assumption would be that that grants Windows access to home/eric, sinces Windows already sees Ubuntu, i.e., it shows up under Network Neighborhood. But that's not the case. When I click on Ubuntu on Windows, Windows says I don't have permission to access Ubuntu. 

So I assume I have to add a share for Windows. However, when I click on Add in Shared Folders, I don't know how to point the configuration window to the drives on Windows. I could write a path, but I don't know what path to give. I tried "eric-windows/c" but that didn't work.

Again, further pointers will be appreciated.

Sincerely,

---

### Post by Eric Weir on 2007-10-09
> **Eric Weir said:**
> I assume I have to add a share for Windows. However, when I click on Add in Shared Folders, I don't know how to point the configuration window to the drives on Windows. I could write a path, but I don't know what path to give. I tried "eric-windows/c" but that didn't work.

I tried the paths that I find in Nautilus when I direct it to Windows, e.g., "smb://windows-ubuntu" [the work group/domain for both computers], "smb://eric-windows," or "smb://eric-windows/c" [the Windows machine and C drive], but when I go to Windows and try to access Ubuntu I'm still denied. 

Actually what it says is, "The password is incorrect," even though both machines have the same password, and that password works to get Ubuntu access to Windows.

---

### Post by user1397 on 2007-10-10
> **Eric Weir said:**
> I tried the paths that I find in Nautilus when I direct it to Windows, e.g., "smb://windows-ubuntu" [the work group/domain for both computers], "smb://eric-windows," or "smb://eric-windows/c" [the Windows machine and C drive], but when I go to Windows and try to access Ubuntu I'm still denied. 

Actually what it says is, "The password is incorrect," even though both machines have the same password, and that password works to get Ubuntu access to Windows.Hmm, I could've told you the exact answer to this question several months ago, but now I have forgotten after not using ubuntu for a while...
Though I think it has to do with some samba configuration file...
If I were you, I would ask around in the help sub-forums, because I'm fresh out of ideas :(
sorry!

---

### Post by Eric Weir on 2007-10-10
> **ubuntuman001 said:**
> Hmm, I could've told you the exact answer to this question several months ago, but now I have forgotten after not using ubuntu for a while...
Though I think it has to do with some samba configuration file...
If I were you, I would ask around in the help sub-forums, because I'm fresh out of ideas :( 
sorry!

Thanks for the help earlier. I _am_ an "absolute beginner," so I'll try there.

Just curious -- Ubuntuman and you don't use Ubuntu? Some other flavor of Ubuntu? Or Linux? Not Windows?! OS X?

Regards,

---

### Post by user1397 on 2007-10-10
> **Eric Weir said:**
> Thanks for the help earlier. I _am_ an "absolute beginner," so I'll try there.

Just curious -- Ubuntuman and you don't use Ubuntu? Some other flavor of Ubuntu? Or Linux? Not Windows?! OS X?

Regards,stuck with windows, for now...

---

### Post by Eric Weir on 2007-10-10
> **ubuntuman001 said:**
> stuck with windows, for now...

Yuck! I'm just getting going with Ubuntu. Have only a 10G hard drive in the machine, and have a couple software applications I haven't been able to find replacements for. When those problems get solved, I'm outa here with Windows. If I decide I'm just not cut out for Linux I'll get me a Mac. [They are so beautiful!]

Regards,

---

### Post by jimmywu013 on 2007-10-25
Hi Eric,

I don't know if you've solved your samba problems yet, but here are my two cents.  
For windows computers to access the samba server on your ubuntu machine, they need to be authenticated.  I'm guessing you don't have any smb user accounts set up, so you'll either need to (1) create an smb user or (2) set samba to allow guest access.

For (1), go to a terminal and use the smbpasswd command:
sudo smbpasswd -a yourusername
The sudo command will ask you for your password, then smbpasswd will ask you to create a password for yourusername.  Type one in (it doesn't have to be the same as your Ubuntu user password, but you can make it the same for convenience).  Next time use that username/password combination when Windows asks you for a password to access Ubuntu.  

For (2), open up /etc/samba/smb.conf with root permissions using the editor of your choice.  Find the section (usually near the bottom) where it lists your shared directories, and add the line 
guest ok = yes 
to all the shares you want.

That should work, but if it doesn't, then there is probably some other issue going on.
Also, I should mention, gsambad, a graphical tool for configuring samba.  I don't use it much because I've never had to change anything after I got samba set up initially, but it may help you.  It automatically writes to the /etc/samba/smb.conf file based on the options you tell it.  

HTH,

Jimmy

---

### Post by Eric Weir on 2007-10-25
> **jimmywu013 said:**
> I don't know if you've solved your samba problems yet, but here are my two cents.  

Thanks, Jimmy. That was more than two cents worth!

I did get the samba problem solved, but not on my own. I had gotten so obsessed with it, wasn't getting anywhere, and was getting behind in real paying work, so I paid my ace-in-th-hole techie friend to fix it for me. It was taking up entirely too much of my life.

>  Also, I should mention, gsambad, a graphical tool for configuring samba.  I don't use it much because I've never had to change anything after I got samba set up initially, but it may help you.  It automatically writes to the /etc/samba/smb.conf file based on the options you tell it.  Yeah, I noticed that in Add and Remove Applications, and wondered if it might help me. Maybe it would have. Maybe I should have it on hand in case I need to make changes later on. Maybe it would help me understand the process a little better than I do, which is still not very much at all, in spite of all the time I put in.

Thanks again,

---

### Post by jimmywu013 on 2007-10-30
Always glad to help.  It's always nice to have a tech guy / geek handy for when something goes wrong.  Unfortunately, I haven't been that lucky - I'm the only one I know that uses Linux, so I've had to figure everything out myself.  I've been using Ubuntu for 3-4 months, and ubuntuforums and the mailing lists have saved my skin on multiple occasions.

Anyways, glad to hear that it works.

Cheers,

Jimmy

---

### Post by Eric Weir on 2007-10-31
> **jimmywu013 said:**
> It's always nice to have a tech guy / geek handy for when something goes wrong.

Absolutely! This guy's saved my but on numerous occasions, including occasions I couldn't afford to pay him. I'm more than happy to call on him now when I can pay him. In addition to being amazingly smart about this stuff, he understands me and what I like. I don't have to explain, or worse, argue. I get what I want!

Regards,

---

### Post by chitowner2 on 2010-04-10
> **ubuntuman001 said:**
> This guide helps you find your installed applications, so that if you installed something but it did not show up in the applications menu, you'll know where it is, and then you can make a launcher for it.  There is a great application that can search all of your installed applications. It's called Xfce 4 Appfinder - and don't be scared by the name, it works in Ubuntu, Kubuntu, and Xubuntu.  Now to install the program, open a terminal (Applications > Accessories > Terminal) and paste: 
```
sudo apt-get update&&sudo apt-get install xfce4-appfinder
```  It'll be in Applications > Accessories in GNOME, Kmenu > Utilities in KDE, and Xfce Menu > Utilities in XFCE.

To search for anything with a GUI search tool, you can either go to Places > Search for Files, or you can right-click on any panel, select **add to panel**, and select the Deskbar search tool, and search from there.

You can also install Beagle, a powerful search tool.  To install it, just paste into a terminal:  ```
sudo apt-get update&&sudo apt-get install beagle
```It will replace the Places > Search for Files tool, and now it is just Places > Search.

You can't really go back to the original search tool (well you can, but it's a bit tedious), but you can always just add the "Search for Files" applet to your panel (right-click on any panel, and select **add to panel**).

To search for anything with the terminal, you can either use the commands **locate** or **which**.
Locate is used more like a keyword-based search function.  For example, if you type in a terminal: 
```
locate java
```then all files with the name java would appear, and there are a lot more than one if you have java installed.  The which command will find the most important file associated with the keyword, i.e.
```
which java
```will reveal the location of the java executable, in /usr/bin/java, and that's it.

After you've found the location of your installed app, you have to make a launcher for it in the menus.  So right-click on your menu, and select **edit menus**.  Then go to whatever category you wish the program to be, and select file > new entry.  then you can choose the name, description, icon, and most importantly, the command for your application which you have just found.


That's fine if one is looking for a single and KNOWN program. What about just generating a list of installed apps- in particular reference to a planned upgrade?

CT

---

### Post by user1397 on 2010-04-27
> **chitowner2 said:**
> That's fine if one is looking for a single and KNOWN program. What about just generating a list of installed apps- in particular reference to a planned upgrade?

CTYea I have no idea, I made this guide like 3 years ago and my knowledge of it has declined rather than increased...sorry!

---

### Post by TQBRFJOALD on 2010-12-30
file:///usr/share/applications
You can find all your applications here, but of course it doesn't let me make a link to it on the desktop (Linux fails miserably sometimes).

---

### Post by user1397 on 2011-01-02
> **TQBRFJOALD said:**
> file:///usr/share/applications
You can find all your applications here, but of course it doesn't let me make a link to it on the desktop (Linux fails miserably sometimes).

right click on desktop, create launcher, type: location, location: /usr/share/applications/, there you go.

---

### Post by dimani4 on 2011-07-18
also you can find the location of the files in system->synaptic package manager, then search for your package and then properties and there installed file option.

---

### Post by OldManRiver on 2011-12-08
All,

So extending this, how do you find complete list of all installed apps with vesions?

OMR

---

### Post by Moif_Murphy on 2011-12-08
```
 
dpkg --get-selections

```
 
...should do the trick but you'll get a ridiculously long list. You could shorten it by piping to grep. ie:
 
```
 
dpkg --get-selections | grep apache

```
 
..and that will show you packages related to apache. Change apache to whatever and away you go.

---

