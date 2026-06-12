---
title: "Saucer Full of Fixes (Ubuntu/Kubuntu 14.04)"
date: 2014-08-12
forum: Tutorials
---

### Post by Arkanglas on 2014-08-12
Hi all.  I've not used any type of UNIX or Linux distribution for many a  year.  So I  recently decided to make the change back to a BSD or Linux distro. I'm now using  the latest Kubuntu release and since it's been so long I'm basically a  newbie, again.  This post is aimed at new users, or users with little experience, and  hopefully it'll answer a lot of questions before they need to be asked.  Hopefully I've put it in the right place in the forums.  If not, let me  know and I'll move it.
 
 For me, the install was smoothe and the OS is proving to be fast and  reliable.  But I did notice a  few things in Kubuntu (and, as I have discovered, Ubuntu) that needed to  be tweaked.  It took a few days because, as I said, I  haven't worked with this type of OS in a lot of years.  But I managed to  figure it out.  Before moving along, note the following points:
 
 First: after you install your OS, get the Krusader file manager.  It  allows you to operate as Administrator.  Krusader will let you browse  the directory tree as Admin, and it will also let you edit and save  files as Admin.  That will cut out a lot of typing in the console for  those not comfortable with the command line.
 
 Second: Some work in the console is necessary.  So I've included what  to type in within the directions.  All you need to do is copy what is  between the brackets < > and past it into the console using your  mouse.  Don't copy the < >.  Just the text between these  characters.

 Third: This is an ongoing work so I'll update it here and there as I find other things that need fixing.
 
 That said, lets move to the list of what appears to be the most common  questions and problems I've seen with users new to Ubuntu and its  flavors.
 

 **KIOExec error: malformed URL trash:/**
 
  I love the Krusader file manager.  So much so that I set it as the  default.  When i did, I could no longer use my trash can.  This seems to  be a big problem in 14.04 Ubuntu and especially older versions.  Its  not really a bug issue as much as it is a dependency issue.  Trash  depends on the base file manager, Dolphin.  If you removed Dolphin or,  for some wierd reason it is not installed, then go get it through  Software Center or Synaptic (Kubuntu calls this Muon Discover Center and  Muon Package Manager, respectively).  Once it's installed, go to System  Settings ==> Default Applications.  In the left column go to File  Manager, and make Dolphin the Default Component.  If you don't see it,   tick “Other” and find it in the menu search that comes up.  Before you  press Apply and close, make sure Dolphin is at the top of the list.   Click apply and closed.  The error is now corrected and you can browse  and use the trash can as normal.

                        
**Video Card and accelerated graphics (enabling POSIX Shared Memory)**
 
 I'm using a mid-to-hi range graphics card.  Specifically, a Radeon R9  280X.  Eventually, I'll get around to installing an nVidia card on  another box.  But for now, this is geared toward the ATI Radeon crowd.
 
While the driver that comes with the stock install works, you really  want the Catalyst driver and the Control Center software.  It'll keep  you from burning up your card, which is an investment (and an R9 280x  and its nVidia equivalent ain't cheap).  The problem is, before you can  install CCC, you'll need to enable POSIX Shared Memory, first.  Then you  will probably need to install some packages as well.  Then finally,  you'll be able to install CCC.  So here we go.
 
 What you will be working with:
 
[LIST]
[*]Krusader (enter     into Admin mode) 
[*]Terminal as     Root (type < sudo su >, press enter, then type your login     passphrase, press enter) 
[/LIST]
 
In your terminal, enter:  < mount | grep "shm" > and press enter.   If POSIX is enabled (and it probably isn't) your output will be  something along the lines of: tmpfs on /dev/shm type tmpfs (rw).  If you  see anything other than this, do the following:
 

 
[LIST=1]
[*]In Krusader,     browse to /etc and  open fstab.conf with Kate by clicking on the file     in the Krusader  window.  You're browsing as Admoin, so it will open     the file in Kate  as Admin, too. 
[*] Add the     following line to the file at the bottom:   < tmpfs /dev/shm tmpfs     defaults 0 0 >  Make sure to press  enter at the end of the line.      Otherwise you will get an error when  you run grep again.  Save the     file and close Kate. 
[*]In the terminal     as Root, type < mount /dev/shm> and press enter. 
[*]Now type <     mount | grep "shm" > in the terminal  again, and press     enter.  Your output should be:  tmpfs on /dev/shm  type tmpfs (rw) 
[*]Type < exit     > in the terminal, press enter, then close the terminal.  Close     Krusader, too.  Then reboot. 
[*]To make sure     everything is operating properly, open a  terminal and type <     mount | grep "shm" > again, and press  enter.  Your     output should once again be:  tmpfs /dev/shm tmpfs  defaults 0 0, or     similar.  You can now install CCC for your Radeon  and enjoy     accelerated graphics. 
[/LIST]
 

 Now on to installing CCC.  Go to this url:  [http://support.amd.com/en-us/download](http://support.amd.com/en-us/download)
 Enter the details of your OS, and it will take you to the appropriate page you can download your driver.
 
 As of this entry, Ubuntu 14.04 is using a Beta Driver, so that's the  one you need.  Download it, and follow the directions on this page:
 
 [http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx)
 
You'll want to go to the  “Generate Distribution Specific Driver Package  Option” section.  Follow the instructions.  My OS was detected as  Ubuntu, so there was no problem.  It did, however, generate an error  during install, saying that there were dependency issues.  This isn't a  problem.  Copy/Paste the required info into a text file, and then open  your terminal as Root again.  Copy each required module into the  terminal, and download them.  Run the install again by following the  directions, and it should install no problem.
 
 The one thing that is lacking is fan control, and the ability to tweak  your card.  That's just not part of this package.  Personally, I don't  do a lot of overclocking, so I don't miss that.  However, I do recognize  the need to control cpu, gpu, and system temps.  For that I use an  external controller that slides into an empty bay in my case.  Linux  still doesn't have any software that allows this type of control, so  save yourself a lot of time and wonder – it doesn't exist as far as I'm  aware.  But since cooling is important, breeze by Newegg and check out  the following:
 
NZXT Sentry (touch screen) [http://www.newegg.com/Product/Product.aspx?Item=N82E16811992005](http://www.newegg.com/Product/Product.aspx?Item=N82E16811992005)
 This will allow you to adjust your fan speed while also telling you the component's temperature.
 
Or
 
 NZXT Fan Controller [http://www.newegg.com/Product/Product.aspx?Item=N82E16811992012](http://www.newegg.com/Product/Product.aspx?Item=N82E16811992012)
 This one doesn't have a touch screen.  Its just a simple slider that  controls fan speed.  No worries, though.  There are plenty of fan speed  and system temp monitor apps for Ubuntu and KDE.  Just install those,  and adjust your speeds as needed.

                        
**Cryptography – gpg.conf; Kleopatra**
 
 I don't like the idea of someone hacking my mail, or intercepting my  messages that show my personal correspondences to family and friends or  worse, pictures of my children.  So I'm a fan of GPG. However, when  I  installed Kubuntu I discovered two things that needed some work: GPG and  Kleopatra.
 
Sometimes, GPG just doesn't want to act right, no matter how many times  you yank it out and then put it back in.  Instead, you get the  following:
 

 gpg: WARNING: unsafe enclosing directory permissions on configuration file '/home/{your username}/.gnupg/gpg.conf'
 

 I've discovered, through a little experimentation and examination of  the files and some quick internet searching a quick, easy, and correct  fix.
 
 What you will be working with:
 
[LIST]
[*]Terminal as     Root (type < sudo su >, press enter, then type your login     passphrase, press enter) 
[/LIST]
 

 In the terminal as Root, copy and past each line.  Note that you should use your username, in place of ***un*** in lines 1 through 3.  For example, if your username is stankfoot, then it would like the following:
 
 /home/stankfoot/.gnupg
 stankfoot:stankfoot /home/stankfoot/.gnupg
 
 and so on...
 

 
[LIST=1]
[*]< chmod 700     /home/***un***/.gnupg > 
[*]< chown -R     ***un***:***un*** /home/***un***/.gnupg > 
[*]< cd     /home/***un***/.gnupg > 
[*]< chmod 600     * > 
[*]< exit > 
[/LIST]
 

 You're done, problem solved!
 

 Next is Kleopatra.  This is a very nice and all-to-often vilified  program.  It generates keys and certificates, and can do a host of other  things; consult its user manual, which reads like badly written  television remote instructions, for details.  Anyway, during its  self-test at startup, Kleopatra has a problem with GPG-agent.   Specifically, it says it can't find or communicate with it, and  therefore this part of the self-test fails.  In turn, a lot of the  functionality of Kleopatra is crippled.  Here's how to fix it.
 
 What you will be working with:
 
[LIST]
[*]Krusader (enter     into Admin mode) 
[*]Terminal as     Root (type < sudo su >, press enter, then type your login     passphrase, press enter) 
[/LIST]
 

 In the terminal as Root, type:
 
[LIST=1]
[*]< chmod a+x     /etc/X11/Xsession.d/90gpg-agent > 
[*]< exit > 
[*]Close terminal 
[/LIST]
 

 In Krusader as Admin:
 
[LIST=1]
[*]Navigate to the     directory /home/***un***/.gnupg  >  Note that this is a     hidden directory, so you will need to  open “View” in Krusader     and tick Show Hidden Files” to see it. 
[*]In     /home/***un***/.gnupg, open  gpg.conf by clicking on it.  As     before, you are browsing as root so  it will open the editor as root     as well.  If you don't have this  file it's safe to make it, which     you can do in the Krusader browser. 
[*]At the bottom     of gpg.conf, put the following line: <  use-agent >.  Make sure     you press enter at the end so there is  an empy line below it. 
[*]Save gpg.conf,     and close the editor. 
[*]Close Krusader     and reboot. 
[/LIST]
 

 Kleopatra is now fixed.  To make sure, open Kleopatra and run the  self-test, which is found under “Settings”.  As you will see, everything  is green on the screen.  Note that another individual also arrived at  the same conclusion.  I think his name is Bashar.  So, hats off to  Bashar, whoever and wherever you are!


                        **Archiving – 7zip with a gui, two ways to do it.**
 
 File compression is vital.  And because most folk want to squash the  be-jeezus out of a file with a gui instead of using the command line, so  is a gui.  Unfortunately, 7zip, which is probably the best archiver out  there, doesn't have a gui for Linux.  Well, not technically.  Turns  out, all you have to do use 7zip with a gui is by right-clicking an  object in your file browser.  When you do that, you have the option to  extract an archive, or to compress a file or folder.  When you compress a  folder, the gui showing all of 7zip's capabilities show up.
 
A word about 7zip, or p7zip for UNIX/Linux users.  First, you'll have to  get it from the command line (you can also use synaptic) since it has  dependencies.  And second, it comes in two flavors:
 
p7zip
 p7zip-full
 
p7zip uses a less powerful version of compressing archives; it only  provides 7zr and the relevant documentation (see the official 7zip  website for details).
 
p7zip-full provides 7z (with 7z.so), 7za, 7zCon.sfx, and the relevant documentation.
 
So unless backing up your data or file transfers are not something you  do very often, p7zip full is the way to go.  Here's how to get it.
 
What you will be working with:
 
[LIST]
[*]Terminal as     Root (type < sudo su >, press enter, then type your login     passphrase, press enter) 
[/LIST]
 
 In your terminal as Root, type:
 
[LIST=1]
[*]< sudo     apt-get install p7zip-full > and press enter. 
[*]You'll probably     want to work with RAR files, too.  It's installed with p7zip-full. 
[*]< exit >     and close terminal. 
[/LIST]
 

You now have 7zip with RAR capabilities installed.
 
 The other way to get 7zip is through synaptic, which Kubuntu calls the  Muon Package Manager.  Personally, I think this is better than using the  command line.  So with the next post (I dunno when that will be,  hopefully soon), I'll start referring to that when possible.

And finally, you can always install the Windows 7zip msi through WINE,  and use it that way.  WINE used to be a beast to mess with, but it seems  it has come quite a long way.  Its relatively ease to use now, and  several gui frontends are available.  Plus, there's a lot of really good  info out on the web cocnerning how to install and set it up.  So no  need to detail it here.

That's it for this time.  Enjoy!

---

### Post by CJ_Hudson on 2014-08-15
Sorry I am trying to install the 14.6 driver in my installation of Ubuntu 14.04 64 bit but got hopelessly lost.
I downloaded it from the AMD website but can't find the directory to follow and run the installation instructions?
Also, I didn't purge the previous driver yet.
I am returning to Ubuntu after a long pause and some of the terminal commands look a bit scary.
I currently have the 13.05 Catalyst version installed.

EDIT: Awesome, I got the Beta driver to install and didn't go anywhere near Xorg. I just followed the instructions on AMD's website carefully here: [http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx#Install](http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx#Install)
...  and despite the missing Xorg it still worked!
[IMG]https://imagizer.imageshack.us/v2/609x477q90/745/4BOgUa.jpg[/IMG]

---

### Post by linuxrev2 on 2015-01-20
> **Arkanglas said:**
> **KIOExec error: malformed URL trash:/**
 
  I love the Krusader file manager.  So much so that I set it as the  default.  When i did, I could no longer use my trash can.  This seems to  be a big problem in 14.04 Ubuntu and especially older versions.  Its  not really a bug issue as much as it is a dependency issue.  Trash  depends on the base file manager, Dolphin.  If you removed Dolphin or,  for some wierd reason it is not installed, then go get it through  Software Center or Synaptic (Kubuntu calls this Muon Discover Center and  Muon Package Manager, respectively).  Once it's installed, go to System  Settings ==> Default Applications.  In the left column go to File  Manager, and make Dolphin the Default Component.  If you don't see it,   tick &#8220;Other&#8221; and find it in the menu search that comes up.  Before you  press Apply and close, make sure Dolphin is at the top of the list.   Click apply and closed.  The error is now corrected and you can browse  and use the trash can as normal.

All you say is correct and I share your love. Without Dolphin as the default file manager the Trash widget in the KDE desktop panel will not show the Trash folder's contents. If you want to access your wastebin from the widget, you will need to default to Dolphin.

However, there is another option. In Krusader you can add a 'Wastebin' icon to the toolbar. Rightclick the toolbar, select 'Configure Toolbars' and add the icon. Clicking the icon will offer two options: 'Open wastebin' and 'Empty wastebin'. (The 'Empty wastebin' option is also available from the Tools menu.) Now, if you set Krusader as the default file manager, you can access the Trash folder and empty it using the icon on the Krusader toolbar. From the wastebin widget on the KDE desktop panel you cannot access the Trash folder, but you can still empty it.

This does not really solve the problem of the 'malformed url trash:/', but it works as a workable workaround, so to say. One glitch is, that if you empty Trash from Krusader, the desktop widget still thinks it needs emptying. Well...

(I'm on LinuxMint 13/Ubuntu 12.04LTS and KDE 4.8, with Krusader 2.4.0-beta1.)

---

