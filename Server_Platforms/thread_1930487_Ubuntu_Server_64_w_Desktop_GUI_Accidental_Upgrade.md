---
title: "Ubuntu Server 64 w/ Desktop GUI Accidental Upgrade"
date: 2012-02-23
forum: Server Platforms
---

### Post by younglemon on 2012-02-23
I have sort of an oddball setup that I have successfully run for a little more than a year.  

I am now running Ubuntu 64 server with the desktop gui software (I believe its called Unity) where version 11.10 was inadvertantly upgraded to 12.04.  It was ok briefly, but then it stopped allowing me to get to the software center by displaying an error that reads: 
 
"Items cannot be installed or removed until the package catalog is repaired.  Do you want to repair it now?  Once the Update Manager has finished the repairs, you can close it and return to the store."
 
When I click the "Repair" button and enter my password, I get the error "Failed to download package files.   Check your internet connection.  Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwibber_3.3.5-0ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwibber_3.3.5-0ubuntu3_amd64.deb) 404 Not Found [IP:91.189.92.168.80].
I can reach the internet without any problems and am successful when I ping google.com from the terminal window.  I first recieved this error a few times and then I changed my routing/IP address to DHCP and still get the same problem.  When I click ok to the error it sends me back to the "Items cannot be installed..." screen.
 
At the top of my screen I have a red circle with a white horizontal bar in the middle.  When i click on this a window titled "backend_helper.py" opens and reads "The package system is broken".  It tells me to check for and disable any 3rd party repositories (the only one I know of and that I disabled is/was the Quantum GIS repo and I've added the appropriate hash # marks and I beleve that I have them disabled).  The details of the message read "The following packages have unmet dependancies: qwibber: Depends: python(<2.8 ) but 2.7.2-9 is installed...".  This window also tells me to run "apt-get install -f" from the terminal.
 
When I run "apt-get install -f" : it at first seems like its going to work as it reads "The following packages will be upgraded: gwibber...Do you want to continue [Y/n]?"
When I enter "Y" and press enter I get similar error to the one in the previous window "Err [http://us.archive.ubuntu.com/ubuntu/pool/mail/g/gwibber/gwibber_3.3.5-0ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/mail/g/gwibber/gwibber_3.3.5-0ubuntu3_amd64.deb) 404 not found...failed to fetch...".  I have attempted "apt-get install..." with many flag options including "Update", "--fix-broken", "--fix-missing" and "-f" and I repeatedly get the failed to fetch error.
 
Any help, thoughts, guidance or suggestions would be gratefully appreciated.  Even if you don't offer any suggestions, thank you for your time so far.

---

### Post by RedSingularity on 2012-02-23
Hey younglemon,

What is the output of a 'sudo apt-get update'?

---

### Post by younglemon on 2012-02-24
[FONT=Times New Roman][SIZE=3]:~$ sudo apt-get update[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][sudo] password:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick InRelease[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:1 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release               [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick Release[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release               [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]          [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages/DiffIndex   [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources/DiffIndex       [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages/DiffIndex    [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages/DiffIndex[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages               [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages/DiffIndex[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages/DiffIndex   [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages/DiffIndex[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages          [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources      [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release              [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release               [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources     [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en_US[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Fetched 50.4 kB in 1s (30.1 kB/s)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Reading package lists... Done[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) maverick Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release: Unknown error executing gpgv[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release)  [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman]W: Some index files failed to download. They have been ignored, or old ones used instead.[/FONT]

---

### Post by younglemon on 2012-02-24
RedSingularity thank you very much for responding to my PM and looking at my issue.  As suggested I posted the contents above and maverick was the version of Ubuntu that I originally built this system using.  I'm not sure why its reverted to these packages but it appears that this does uncover a problem.  Although, I'm not sure how to correct it, but I assume that I'll need to edit the package location after ensuring the correct package files are available.  Does that sound reasonable, any ideas for the my next step?  Thank you very much, again, for all of your support to this point.

---

### Post by RedSingularity on 2012-02-24
Happy to help.  It may be a mirror issue.  I see that those links mentioned in your first post are indeed down.  Have you tried setting another mirror?

---

### Post by younglemon on 2012-02-24
No, I haven't. I'll look around on the forum threads for the procedure and let you know how it goes.

---

### Post by RedSingularity on 2012-02-24
Well you do have gnome installed correct?  I think the command is:

gksu --desktop /usr/share/applications/software-properties-gtk.desktop /usr/bin/software-properties-gtk

Thats what it is in my menu.  It will open a window to change the default mirror site.  Just pick another from the US.

---

### Post by younglemon on 2012-02-24
A-Ha!  Thank you, that is excellent. 
 
I've run the command and was able to choose a different mirror.  I then checked for updates and then selected 'show updates'.
 
Now I have a window that reads:
"Not all updates can be installed  Run a partial upgrade, to install as many updates as possible.  This can be caused by: 
*A previous upgrade which didn't complete 
*Problems with some of the installed software 
*Unofficial software packages not provided by Ubuntu
*Normal changes of a pre-release version of Ubuntu"
 
I have the option of "Partial upgrade" or "Cancel".
I am going to "Partial upgrade"

---

### Post by younglemon on 2012-02-24
I recieve "Error authenticating some packages..." and there are many, many unauthenticated packages.  I clicked close and the window disappeared and I'm now back to the terminal window

---

### Post by younglemon on 2012-02-24
I eventually got a message etc sending me to the Synaptec package manager application.  I have a broken gWibber package.  I tried to update and it failed.  I unmarked it and will now try apt-get again from the terminal window.  Thank you for your continued support.

---

### Post by RedSingularity on 2012-02-24
Run these commands to clear out any old packages:

sudo apt-get clean

then

sudo rm -r /var/cache/apt/archives/partial/*

Then 'sudo apt-get update' again.

---

### Post by younglemon on 2012-02-24
Woo Hoo!
RedSingularity if ever we had the chance to meet, I would enjoy buying you several craft quality brews and enjoying them with you. So far so good, but its not done yet. I'll keep you posted.
 
To be clear, I had to remove the "*" part of the second to last command, but it is still working, or seems to be, for now.
 
Cheers to you, for all that you do, thank you.

---

### Post by younglemon on 2012-02-24
Uh-oh got an error 
 
GPG error: [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise Release: Unknown error executing gpgv....
 
There are four lines at the end that look like this, I'll post the output in a moment

---

### Post by younglemon on 2012-02-24
[FONT=Times New Roman][SIZE=3]Thank you again for your continued support.  The following is as it happened.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]@Serv:~$ sudo apt-get clean[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][sudo] password:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo rm -r /var/cache/apt/archives/partial/*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]rm: cannot remove `/var/cache/apt/archives/partial/*': No such file or directory[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo rm -r /var/cache/apt/archives/partial/[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo rm -r /var/cache/apt/archives/partial/*[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]rm: cannot remove `/var/cache/apt/archives/partial/*': No such file or directory[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo apt-get update[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise InRelease[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates InRelease[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security InRelease[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:1 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise Release.gpg [198 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:2 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates Release.gpg [198 B][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick InRelease       [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Get:3 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security Release.gpg [198 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:4 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise Release [49.6 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:5 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198 B][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates Release           [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise Release                        [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates Release                [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security Release             [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security Release             [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/main Sources/DiffIndex       [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/restricted Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/universe Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/multiverse Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/main amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/restricted amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/universe amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/multiverse amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick Release[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/main i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/restricted i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/universe i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/multiverse i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:6 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/main TranslationIndex [3,570 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:7 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/multiverse TranslationIndex [2,540 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:8 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/restricted TranslationIndex [2,464 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:9 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/universe TranslationIndex [2,784 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/main Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/restricted Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/universe Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/multiverse Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/main amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/restricted amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/universe amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/multiverse amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/main i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/restricted i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/universe i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/multiverse i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/main TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/multiverse TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/restricted TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/universe TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/main Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/restricted Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/universe Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/multiverse Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/main amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/restricted amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/universe amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/multiverse amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/main i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/restricted i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/universe i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/multiverse i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/main TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/multiverse TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/restricted TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/universe TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:10 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/main Sources [927 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:11 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/restricted Sources [5,065 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:12 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/universe Sources [5,031 kB][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en_US              [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:13 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/multiverse Sources [159 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:14 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/main amd64 Packages [1,294 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:15 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/restricted amd64 Packages [8,431 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:16 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/universe amd64 Packages [4,796 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:17 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/multiverse amd64 Packages [124 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:18 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/main i386 Packages [1,295 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:19 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/restricted i386 Packages [8,350 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:20 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/universe i386 Packages [4,807 kB][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Get:21 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/multiverse i386 Packages [126 kB]                         [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:22 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/main Translation-en [723 kB]                              [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/multiverse Translation-en                                    [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/restricted Translation-en                                    [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:23 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/universe Translation-en [3,363 kB]                        [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/main Sources                                         [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/restricted Sources                                   [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/universe Sources                                     [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/multiverse Sources                                   [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/main amd64 Packages                                  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/restricted amd64 Packages                            [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/universe amd64 Packages                              [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/multiverse amd64 Packages                            [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/main i386 Packages                                   [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/restricted i386 Packages                             [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/universe i386 Packages                               [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/multiverse i386 Packages                             [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/main Translation-en                                  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/multiverse Translation-en                            [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/restricted Translation-en                            [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/universe Translation-en                              [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/main Sources                                        [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/restricted Sources                                  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/universe Sources                                    [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/multiverse Sources                                  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/main amd64 Packages                                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/restricted amd64 Packages                           [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/universe amd64 Packages                             [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/multiverse amd64 Packages                           [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/main i386 Packages                                  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/restricted i386 Packages                            [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/universe i386 Packages                              [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/multiverse i386 Packages                            [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/main Translation-en                                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/multiverse Translation-en                           [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/restricted Translation-en                           [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/universe Translation-en                             [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Fetched 22.7 MB in 9s (2,425 kB/s)                                                                     [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Reading package lists... Done[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) maverick Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$[/SIZE][/FONT]

---

### Post by RedSingularity on 2012-02-24
Odd, you should have that partial directory.  What is the output of:

ls /var/cache/apt/archives

---

### Post by RedSingularity on 2012-02-24
Also run this:

sudo rm /var/lib/apt/lists/* -vf

then..

sudo apt-get update

See if that clears the errors from the update output.

---

### Post by younglemon on 2012-02-24
ls /var/cache/apt/archives
yields
[FONT=Times New Roman][SIZE=3]checkbox_0.13.3_amd64.deb[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]checkbox-qt_0.13.3_amd64.deb[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]gwibber_3.3.90-0ubuntu1_amd64.deb[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]gwibber-service_3.3.90-0ubuntu1_all.deb[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]lock[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]partial[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]pnm2ppa_1.13+nondbs-0ubuntu1_all.deb[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]printer-driver-pnm2ppa_1.13+nondbs-0ubuntu1_amd64.deb[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ubuntu-desktop_1.261_amd64.deb[/SIZE][/FONT]

---

### Post by younglemon on 2012-02-24
sudo rm /var/lib/apt/lists/* -vf
yields
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo rm /var/lib/apt/lists/* -vf[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][sudo] password:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-amd64_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-i386_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_Release'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/lock'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_main_binary-amd64_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_main_binary-i386_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_main_i18n_Index'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_main_i18n_Translation-en'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_main_source_Sources'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_multiverse_binary-amd64_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_multiverse_binary-i386_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_multiverse_i18n_Index'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_multiverse_i18n_Translation-en'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_multiverse_source_Sources'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_Release'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_restricted_binary-amd64_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_restricted_binary-i386_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_restricted_i18n_Index'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_restricted_i18n_Translation-en'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_restricted_source_Sources'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_main_binary-amd64_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_main_binary-i386_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_main_i18n_Index'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_main_i18n_Translation-en'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_main_source_Sources'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_multiverse_binary-amd64_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_multiverse_binary-i386_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_multiverse_i18n_Index'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_multiverse_i18n_Translation-en'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_multiverse_source_Sources'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_Release'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_restricted_binary-amd64_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_restricted_binary-i386_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_restricted_i18n_Index'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_restricted_i18n_Translation-en'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_restricted_source_Sources'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_universe_binary-amd64_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_universe_binary-i386_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_universe_i18n_Index'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_universe_i18n_Translation-en'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-security_universe_source_Sources'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_universe_binary-amd64_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_universe_binary-i386_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_universe_i18n_Index'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_universe_i18n_Translation-en'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise_universe_source_Sources'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_main_binary-amd64_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_main_binary-i386_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_main_i18n_Index'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_main_i18n_Translation-en'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_main_source_Sources'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_multiverse_binary-amd64_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_multiverse_binary-i386_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_multiverse_i18n_Index'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_multiverse_i18n_Translation-en'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_multiverse_source_Sources'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_Release'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_restricted_binary-amd64_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_restricted_binary-i386_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_restricted_i18n_Index'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_restricted_i18n_Translation-en'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_restricted_source_Sources'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_universe_binary-amd64_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_universe_binary-i386_Packages'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_universe_i18n_Index'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_universe_i18n_Translation-en'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]removed `/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_precise-updates_universe_source_Sources'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]rm: cannot remove `/var/lib/apt/lists/partial': Is a directory[/SIZE][/FONT]

---

### Post by younglemon on 2012-02-24
Thanks again for your continued support, its still broken.
 
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo apt-get update[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise InRelease[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates InRelease[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security InRelease[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:1 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise Release.gpg [198 B][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Get:2 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates Release.gpg [198 B]                   [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Get:3 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security Release.gpg [198 B][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick InRelease   [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Get:4 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise Release [49.6 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:5 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates Release [28.9 kB][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise Release                                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates Release                         [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:6 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198 B]          [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Get:7 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security Release [28.9 kB][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security Release               [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:8 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/main Sources [927 kB]        [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Get:9 [http://archive.canonical.com](http://archive.canonical.com) maverick Release [5,925 B][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick Release                [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Get:10 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages [5,713 B][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Get:11 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages [6,412 B]   [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner TranslationIndex[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Get:12 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/restricted Sources [5,065 B]      [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:13 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/universe Sources [5,031 kB]         [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en_US              [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:14 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/multiverse Sources [159 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:15 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/main amd64 Packages [1,294 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:16 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/restricted amd64 Packages [8,431 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:17 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/universe amd64 Packages [4,796 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:18 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/multiverse amd64 Packages [124 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:19 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/main i386 Packages [1,295 kB][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Get:20 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/restricted i386 Packages [8,350 B]                       [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:21 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/universe i386 Packages [4,807 kB]                        [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:22 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/multiverse i386 Packages [126 kB]                        [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:23 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/main TranslationIndex [3,570 B]                          [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:24 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/multiverse TranslationIndex [2,540 B]                    [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:25 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/restricted TranslationIndex [2,464 B]                    [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:26 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/universe TranslationIndex [2,784 B]                      [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:27 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/main Sources [14 B]                              [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:28 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/restricted Sources [14 B]                        [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:29 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/universe Sources [14 B]                          [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:30 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/multiverse Sources [14 B]                        [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:31 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/main amd64 Packages [14 B]                       [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:32 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/restricted amd64 Packages [14 B]                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:33 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/universe amd64 Packages [14 B]                   [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:34 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/multiverse amd64 Packages [14 B]                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:35 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/main i386 Packages [14 B]                        [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:36 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/restricted i386 Packages [14 B]                  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:37 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/universe i386 Packages [14 B]                    [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:38 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/multiverse i386 Packages [14 B]                  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:39 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/main TranslationIndex [70 B]                     [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:40 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/multiverse TranslationIndex [70 B]               [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:41 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/restricted TranslationIndex [70 B]               [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:42 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/universe TranslationIndex [70 B]                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:43 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/main Sources [14 B]                             [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:44 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/restricted Sources [14 B]                       [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:45 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/universe Sources [14 B]                         [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:46 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/multiverse Sources [14 B]                       [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:47 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/main amd64 Packages [14 B]                      [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:48 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/restricted amd64 Packages [14 B]                [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:49 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/universe amd64 Packages [14 B]                  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:50 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/multiverse amd64 Packages [14 B]                [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:51 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/main i386 Packages [14 B]                       [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:52 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/restricted i386 Packages [14 B]                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:53 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/universe i386 Packages [14 B]                   [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:54 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/multiverse i386 Packages [14 B]                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:55 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/main TranslationIndex [70 B]                    [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:56 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/multiverse TranslationIndex [70 B]              [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:57 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/restricted TranslationIndex [70 B]              [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:58 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/universe TranslationIndex [70 B]                [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:59 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/main Translation-en [723 kB]                             [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:60 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/multiverse Translation-en [96.8 kB]                      [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:61 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/restricted Translation-en [2,229 B]                      [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:62 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise/universe Translation-en [3,363 kB]                       [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:63 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/main Translation-en [14 B]                       [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:64 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/multiverse Translation-en [14 B]                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:65 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/restricted Translation-en [14 B]                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:66 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates/universe Translation-en [14 B]                   [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:67 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/main Translation-en [14 B]                      [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:68 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/multiverse Translation-en [14 B]                [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:69 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/restricted Translation-en [14 B]                [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:70 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security/universe Translation-en [14 B]                  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Fetched 22.9 MB in 11s (2,020 kB/s)                                                                   [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Reading package lists... Done[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-updates Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) precise-security Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) maverick Release: Unknown error executing gpgv[/SIZE][/FONT]

---

### Post by RedSingularity on 2012-02-24
Lets try putting in a fresh sources.list file.  Can you confirm you are running ubuntu version 12.04 at the moment?

---

### Post by younglemon on 2012-02-25
[FONT=Verdana][SIZE=3]I hope that this is the best way to tell what version I am running[/SIZE][/FONT]
 
[FONT=Trebuchet MS][SIZE=3]Serv:~$ lsb_release -a[/SIZE][/FONT]
[FONT=Trebuchet MS][SIZE=3]No LSB modules are available.[/SIZE][/FONT]
[FONT=Trebuchet MS][SIZE=3]Distributor ID: Ubuntu[/SIZE][/FONT]
[FONT=Trebuchet MS][SIZE=3]Description: Ubuntu precise (development branch)[/SIZE][/FONT]
[FONT=Trebuchet MS][SIZE=3]Release: 12.04[/SIZE][/FONT]
[FONT=Trebuchet MS][SIZE=3]Codename: precise[/SIZE][/FONT]
[FONT=Trebuchet MS][SIZE=3]Serv:~$[/SIZE][/FONT]

---

### Post by younglemon on 2012-02-25
I previously edited the sources list to open the repository for Quantum GIS or qgis. It worked well for awhile but then I accidentally agreed to the partial upgrade as to gain something else, can't even remeber now what. Now it seems like something is wrong with the social client gWibber...not even sure what it does other than seeminly allow the package through to my machine. Since it has stopped working I changed the sources.list back to remove the qgis repo. Additionally, now that we have changed the mirror site, during the course of this thread, the sources.list has been adjusted for the "...columbia...' mirror. 
 
How would I get a new sources list or, would I edit the sources.list? If you drink it, you are due many fine quality craft beers, thank you again.

---

### Post by RedSingularity on 2012-02-25
The problem with gwibber is apparently.....its not even on the mirror site at all.  I am not sure if they removed it for a reason or not.  Look here and you will see the error page:  [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwibber_3.3.5-0ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwibber_3.3.5-0ubuntu3_amd64.deb)

Maybe they removed the 64bit version?

To fix that issue, see if you can uninstall it and then reinstall it.

To put in the 'fresh' sources.list, use this site to generate it:  [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

then...

1) sudo mv /etc/apt/sources.list  /etc/apt/sources.list.old
2) sudo touch /etc/apt/sources.list
3) gksu gedit /etc/apt/sources.list 
(Copy/Paste the new source info from the web browser into the file then save and close it)

4)sudo apt-get update 

See if it updates properly.

EDIT: Properly fixing the sources.list file may clean up the gwibber problem also.

---

### Post by younglemon on 2012-02-25
Unfortunately the state that it's currently in does not allow for either the removal or installation of programs. I will visit the site you mentioned for regarding the development of a sources list file. I will reply shortly with the outcome.
 
As I go to the resource it gives the option for "Precise 12.04, (Alpha 1 - this is not recommended)"  This is the option I chose, that is correct, right?

---

### Post by younglemon on 2012-02-25
I am unable to copy the file in this way, not sure why exactly.  It reads "mv: cannot stat '/ect/apt/sources.list': No such file or directory".  
 
I'm going to attempt to acheive the same results using a slightly different method, please let me know if what I'm trying will not work.  I am going to take ownership of this location and file by way of using 
sudo chown me /etc/apt/
Then I will copy the contents of the generated files as you previously described.  
 
More to follow shortly

---

### Post by younglemon on 2012-02-25
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo chown younglemon /etc/apt/sources.list[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I then copied the generated text with gedit text editor and saved the file[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo chown root /etc/apt/sources.list[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo chown root /etc/apt[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo apt-get update[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://dl.google.com](http://dl.google.com) stable InRelease[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Ign [http://dl.google.com](http://dl.google.com) testing InRelease                                          [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189 B]                               [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:2 [http://dl.google.com](http://dl.google.com) testing Release.gpg [189 B]                              [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                      [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                                  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security InRelease                         [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                      [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                                  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                      [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:3 [http://dl.google.com](http://dl.google.com) stable Release [2,544 B]                                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://dl.google.com](http://dl.google.com) stable Release                                             [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                           [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]                      [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:6 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                      [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:7 [http://dl.google.com](http://dl.google.com) testing Release [2,513 B]                                [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://dl.google.com](http://dl.google.com) testing Release                                            [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                          [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:9 [http://dl.google.com](http://dl.google.com) stable/non-free amd64 Packages [1,025 B]                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:10 [http://dl.google.com](http://dl.google.com) stable/non-free i386 Packages [1,010 B]                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release.gpg [198 B]            [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:12 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release [11.9 kB]                           [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:13 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7,078 B]                       [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://dl.google.com](http://dl.google.com) stable/non-free TranslationIndex                           [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:14 [http://dl.google.com](http://dl.google.com) testing/non-free amd64 Packages [786 B]                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:15 [http://dl.google.com](http://dl.google.com) testing/non-free i386 Packages [793 B]                  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                         [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]                       [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://dl.google.com](http://dl.google.com) testing/non-free TranslationIndex                          [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]                           [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://archive.canonical.com](http://archive.canonical.com) precise Release                                    [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                        [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                        [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:19 [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources [1,203 B]               [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:20 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources [14 B]                         [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:21 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]                           [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:22 [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages [1,471 B]        [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:23 [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages [2,037 B]         [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:24 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages [14 B]                  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:25 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages [14 B]                   [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                          [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                                    [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                        [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex                   [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release [28.9 kB]              [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                          [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en                             [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:27 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [1,710 B]                      [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://dl.google.com](http://dl.google.com) testing/non-free Translation-en_US                         [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release                           [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://dl.google.com](http://dl.google.com) testing/non-free Translation-en                            [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:28 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [4,101 B]               [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:29 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [4,099 B]                [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                          [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [927 kB]                   [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:31 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [994 B]                        [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:32 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [3,081 B]               [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:33 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [3,118 B]                [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                          [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                         [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                            [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US            [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en               [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages [1,301 kB][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                      [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                   [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                      [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages [1,302 kB]     [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex [3,570 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Sources [14 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main amd64 Packages [14 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main i386 Packages [14 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main TranslationIndex [70 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en [723 kB][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Translation-en [14 B]     [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Fetched 4,411 kB in 6s (653 kB/s)                                                   [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Reading package lists... Done[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://dl.google.com](http://dl.google.com) testing Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]This didn't work, so I adjusted the generated file from the resource you sent, to only include the primary items (no google or extras) and tried again[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo chown younglemon /etc/apt[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo chown younglemon /etc/apt/sources.list[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I then copied the generated text with gedit text editor and saved the file[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo chown root /etc/apt/sources.list[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo chown root /etc/apt[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo apt-get update[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security InRelease[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release.gpg [198 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Sources[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main amd64 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main i386 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Translation-en[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Fetched 396 B in 1s (370 B/s)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Reading package lists... Done[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Then this didn't work, so I tried again and selected the alternate “synaptic” layout.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo chown younglemon /etc/apt/sources.list[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo chown younglemon /etc/apt[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I then copied the generated text with gedit text editor and saved the file[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo chown root /etc/apt/sources.list[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo chown root /etc/apt[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo apt-get update[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security InRelease[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release.gpg [198 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main amd64 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main i386 Packages/DiffIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main TranslationIndex[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main amd64 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main i386 Packages[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Translation-en[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/mai Sources[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/mai Sources[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/mai Sources[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  404  Not Found [IP: 91.189.92.177 80][/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Fetched 396 B in 1s (290 B/s)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/mai/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/mai/source/Sources)  404  Not Found [IP: 91.189.92.177 80][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]E: Some index files failed to download. They have been ignored, or old ones used instead.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I wonder if I should try to generate on for version 11.10, maybe?  Many thanks for your continued everything.[/SIZE][/FONT]

---

### Post by younglemon on 2012-02-26
[COLOR=black][FONT=Verdana]Soon I will go back through your advice and repeat some of the suggested steps to see if it will come back.  Otherwise I think I'm going to either: 1-wait it out until the upgrade is released or, 2-research reverting back to the distribution I was using previously.  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Still not sure what the issue is, but I haven't given up :) I'll keep you posted, thanks again.[/FONT][/COLOR]

---

### Post by RedSingularity on 2012-02-26
Sorry for the delay.  You wont be able to revert back to the previous distribution.  Unfortunately that is not supported in the operating system.  You would need to do a fresh install.  Can you paste the contents of your sources.list here?

---

### Post by younglemon on 2012-02-26
[FONT=Times New Roman][SIZE=3]Certainly.  Thanks so much for your continued support.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The current contents of /ect/apt/sources.list file is below.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]#############################################################[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]################### OFFICIAL UBUNTU REPOS ###################[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#############################################################[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]###### Ubuntu Main Repos[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]###### Ubuntu Update Repos[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security mai[/SIZE][/FONT]

---

### Post by younglemon on 2012-02-26
Should I adjust the URL's within this file so that they use the mirror "...columbia..."?

---

### Post by RedSingularity on 2012-02-26
Actually, what is the output of:

ls /etc/apt

---

### Post by younglemon on 2012-02-26
[FONT=Times New Roman][SIZE=3]Serv:~$ ls /etc/apt[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]apt.conf.d                   sources (copy).list  sources.list.d            trusted.gpg[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]apt-file.conf                sources.list         sources.list.distUpgrade  trusted.gpg~[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]preferences.d                sources.list~        sources.list.save         trusted.gpg.d[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]sources (another copy).list  sources.list.backup  trustdb.gpg[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$[/SIZE][/FONT]

---

### Post by RedSingularity on 2012-02-26
Oh there are probably some sources in the sources.list.d directory.  

Rename that directory temporarily.  Make it something like 'sources.list.d.temp'

Then try an update again to see if it comes out cleaner.  (without errors)

---

### Post by younglemon on 2012-02-26
[SIZE=3]Thank you RedSigularity, I've followed the steps and still end up with a similar error...[/SIZE]
[FONT=Times New Roman][SIZE=3]"Hit [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]http://us.archive.ubuntu.com[/SIZE][/FONT]]("http://us.archive.ubuntu.com/")[FONT=Times New Roman][SIZE=3] precise-security/main Translation-en
Err [/SIZE][[SIZE=3]http://us.archive.ubuntu.com[/SIZE]]("http://us.archive.ubuntu.com/")[SIZE=3] precise-security/mai Sources[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-security/mai Sources[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-security/mai Sources[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]404 Not Found [IP: 91.189.92.177 80][/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Fetched 396 B in 1s (290 B/s)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-security Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...source/Sources]("http://us.archive.ubuntu.com/ubuntu/dists/precise-security/mai/source/Sources") 404 Not Found [IP: 91.189.92.177 80][/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]E: Some index files failed to download. They have been ignored, or old ones used instead.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$"[/SIZE][/FONT]

[SIZE=3]I wonder if I changed the URL listed within the newly generated sources.list, would that help this error?  [/SIZE]

---

### Post by RedSingularity on 2012-02-26
Would not hurt to try.  You may have an actual bug there with gpgv.

Try a 'sudo apt-get dist-upgrade' and see what happens.

---

### Post by younglemon on 2012-02-26
I will attempt this and see.  I changed to a different mirror site in the US and attempted to update again, still get the error, results below.  Otherwise, I'll reply in a moment with the results of you last post. Thanks so much RedSigularity, I remain grateful.
 
[FONT=Times New Roman][SIZE=3]Serv:/etc/apt$ sudo apt-get clean[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:/etc/apt$ sudo apt-get update[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://mirror.symnds.com](http://mirror.symnds.com) precise InRelease[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Ign [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates InRelease   [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://mirror.symnds.com](http://mirror.symnds.com) precise-security InRelease  [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Get:1 [http://mirror.symnds.com](http://mirror.symnds.com) precise Release.gpg [198 B][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Get:2 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates Release.gpg [198 B]                        [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:3 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security Release.gpg [198 B]                       [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:4 [http://mirror.symnds.com](http://mirror.symnds.com) precise Release [49.6 kB]                       [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Get:5 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates Release [28.9 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick InRelease[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Ign [http://mirror.symnds.com](http://mirror.symnds.com) precise Release                                      [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:6 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security Release [28.9 kB]                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates Release                         [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:7 [http://mirror.symnds.com](http://mirror.symnds.com) precise/main Sources [927 kB]                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://mirror.symnds.com](http://mirror.symnds.com) precise-security Release                       [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:8 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198 B]             [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:9 [http://archive.canonical.com](http://archive.canonical.com) maverick Release [5,925 B]     [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick Release                [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Get:10 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages [5,713 B][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Get:11 [http://mirror.symnds.com](http://mirror.symnds.com) precise/restricted Sources [5,065 B]           [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:12 [http://mirror.symnds.com](http://mirror.symnds.com) precise/universe Sources [5,048 kB]            [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Get:13 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages [6,412 B][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner TranslationIndex                        [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en_US               [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:14 [http://mirror.symnds.com](http://mirror.symnds.com) precise/multiverse Sources [159 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:15 [http://mirror.symnds.com](http://mirror.symnds.com) precise/main amd64 Packages [1,287 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:16 [http://mirror.symnds.com](http://mirror.symnds.com) precise/restricted amd64 Packages [8,431 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:17 [http://mirror.symnds.com](http://mirror.symnds.com) precise/universe amd64 Packages [4,803 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:18 [http://mirror.symnds.com](http://mirror.symnds.com) precise/multiverse amd64 Packages [124 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:19 [http://mirror.symnds.com](http://mirror.symnds.com) precise/main i386 Packages [1,286 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:20 [http://mirror.symnds.com](http://mirror.symnds.com) precise/restricted i386 Packages [8,350 B][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Get:21 [http://mirror.symnds.com](http://mirror.symnds.com) precise/universe i386 Packages [4,815 kB]                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:22 [http://mirror.symnds.com](http://mirror.symnds.com) precise/multiverse i386 Packages [126 kB]                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:23 [http://mirror.symnds.com](http://mirror.symnds.com) precise/main TranslationIndex [3,570 B]                   [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:24 [http://mirror.symnds.com](http://mirror.symnds.com) precise/multiverse TranslationIndex [2,540 B]             [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:25 [http://mirror.symnds.com](http://mirror.symnds.com) precise/restricted TranslationIndex [2,464 B]             [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:26 [http://mirror.symnds.com](http://mirror.symnds.com) precise/universe TranslationIndex [2,784 B]               [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:27 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/main Sources [14 B]                       [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:28 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/restricted Sources [14 B]                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:29 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/universe Sources [14 B]                   [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:30 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/multiverse Sources [14 B]                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:31 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/main amd64 Packages [14 B]                [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:32 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/restricted amd64 Packages [14 B]          [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:33 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/universe amd64 Packages [14 B]            [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:34 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/multiverse amd64 Packages [14 B]          [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:35 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/main i386 Packages [14 B]                 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:36 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/restricted i386 Packages [14 B]           [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:37 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/universe i386 Packages [14 B]             [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:38 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/multiverse i386 Packages [14 B]           [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:39 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/main TranslationIndex [70 B]              [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:40 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/multiverse TranslationIndex [70 B]        [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:41 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/restricted TranslationIndex [70 B]        [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:42 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/universe TranslationIndex [70 B]          [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:43 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/main Sources [14 B]                      [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:44 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/restricted Sources [14 B]                [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:45 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/universe Sources [14 B]                  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:46 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/multiverse Sources [14 B]                [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:47 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/main amd64 Packages [14 B]               [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:48 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/restricted amd64 Packages [14 B]         [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:49 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/universe amd64 Packages [14 B]           [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:50 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/multiverse amd64 Packages [14 B]         [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:51 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/main i386 Packages [14 B]                [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:52 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/restricted i386 Packages [14 B]          [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:53 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/universe i386 Packages [14 B]            [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:54 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/multiverse i386 Packages [14 B]          [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:55 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/main TranslationIndex [70 B]             [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:56 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/multiverse TranslationIndex [70 B]       [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:57 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/restricted TranslationIndex [70 B]       [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:58 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/universe TranslationIndex [70 B]         [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:59 [http://mirror.symnds.com](http://mirror.symnds.com) precise/main Translation-en [723 kB]                      [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:60 [http://mirror.symnds.com](http://mirror.symnds.com) precise/multiverse Translation-en [96.8 kB]               [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:61 [http://mirror.symnds.com](http://mirror.symnds.com) precise/restricted Translation-en [2,229 B]               [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:62 [http://mirror.symnds.com](http://mirror.symnds.com) precise/universe Translation-en [3,365 kB]                [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:63 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/main Translation-en [14 B]                [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:64 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/multiverse Translation-en [14 B]          [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:65 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/restricted Translation-en [14 B]          [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:66 [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates/universe Translation-en [14 B]            [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:67 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/main Translation-en [14 B]               [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:68 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/multiverse Translation-en [14 B]         [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:69 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/restricted Translation-en [14 B]         [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Get:70 [http://mirror.symnds.com](http://mirror.symnds.com) precise-security/universe Translation-en [14 B]           [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Fetched 22.9 MB in 10s (2,166 kB/s)                                                       [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Reading package lists... Done[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://mirror.symnds.com](http://mirror.symnds.com) precise Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://mirror.symnds.com](http://mirror.symnds.com) precise-updates Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://mirror.symnds.com](http://mirror.symnds.com) precise-security Release: Unknown error executing gpgv[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) maverick Release: Unknown error executing gpgv[/SIZE][/FONT]

---

### Post by younglemon on 2012-02-26
Thanks again RedSigularity.  Here is the output from "apt-get dist-upgrade".  Not sure what I can do now.....?
 
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo apt-get dist-upgrade[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Reading package lists... Done[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Building dependency tree       [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Reading state information... Done[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]You might want to run 'apt-get -f install' to correct these.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The following packages have unmet dependencies:[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] gwibber : Depends: gwibber-service (= 3.3.2-0ubuntu2) but 3.3.5-0ubuntu3 is installed[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]E: Unmet dependencies. Try using -f.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo apt-get -f install[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Reading package lists... Done[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Building dependency tree       [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Reading state information... Done[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Correcting dependencies... Done[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The following packages were automatically installed and are no longer required:[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  libindicator3-6 libindicator6 libpng12-0:i386 libllvm2.9[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Use 'apt-get autoremove' to remove them.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The following extra packages will be installed:[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  gwibber gwibber-service[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Suggested packages:[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  gwibber-service-flickr gwibber-service-digg gwibber-service-statusnet[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  gwibber-service-foursquare gwibber-service-friendfeed gwibber-service-pingfm[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  gwibber-service-qaiku unity-lens-gwibber[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]The following packages will be upgraded:[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  gwibber gwibber-service[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]2 upgraded, 0 newly installed, 0 to remove and 510 not upgraded.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]2 not fully installed or removed.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Need to get 196 kB of archives.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]After this operation, 115 kB disk space will be freed.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Do you want to continue [Y/n]? y[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]WARNING: The following packages cannot be authenticated![/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  gwibber gwibber-service[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Install these packages without verification [y/N]? y[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main gwibber amd64 3.3.90-0ubuntu1 [158 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main gwibber-service all 3.3.90-0ubuntu1 [37.5 kB][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Fetched 196 kB in 1s (187 kB/s)         [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Setting up apt (0.8.16~exp12ubuntu4) ...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: UP[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: UP[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dpkg: error processing apt (--configure):[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] subprocess installed post-installation script returned error exit status 127[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]No apport report written because MaxReports is reached already[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]                                                              Errors were encountered while processing:[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman] apt[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]E: Sub-process /usr/bin/dpkg returned an error code (1)[/SIZE][/FONT]

---

### Post by younglemon on 2012-02-26
When I attempt to update from the software manager I get an error telling me the package is broken and would I like to try to repair it now.  I say yes and the below is the error that follows.  I don't know if it will help, but I figure its worth mentioning perhaps.  Thanks again.
 
[FONT=Times New Roman][SIZE=3]installArchives() failed: Setting up apt (0.8.16~exp12ubuntu4) ...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: UP[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: UP[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dpkg: error processing apt (--configure):[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] subprocess installed post-installation script returned error exit status 127[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Errors were encountered while processing:[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] apt[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Error in function:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Setting up samba4 (4.0.0~alpha17.dfsg2-1) ...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "auth methods"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "auth methods"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "map to guest"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "map to guest"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "passwd program"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "passwd program"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "max log size"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "max log size"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "os level"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "os level"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "domain master"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "domain master"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "usershare allow guests"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "usershare allow guests"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "admin users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "admin users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "valid users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "valid users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "force group"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "force group"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "valid users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "valid users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "share modes"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "share modes"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "guest ok"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "guest ok"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "auth methods"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "auth methods"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "map to guest"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "map to guest"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "passwd program"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "passwd program"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "max log size"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "max log size"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "os level"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "os level"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "domain master"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "domain master"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "usershare allow guests"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "usershare allow guests"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "admin users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "admin users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "valid users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "valid users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "force group"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "force group"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "valid users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "valid users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "share modes"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "share modes"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "guest ok"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "guest ok"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]module samba_dsdb initialization failed : No such object[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unable to load modules for /var/lib/samba/private/sam.ldb: dsdb_module_search_dn: did not find base dn @ROOTDSE (0 results)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Traceback (most recent call last):[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  File "/usr/share/samba/setup/upgradeprovision", line 1716, in <module>[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]    ldbs = get_ldbs(paths, creds, session, lp)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  File "/usr/lib/python2.7/dist-packages/samba/upgradehelpers.py", line 156, in get_ldbs[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]    ldbs.sam = SamDB(paths.samdb, session_info=session, credentials=creds, lp=lp, options=["modules:samba_dsdb"])[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 57, in __init__[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]    options=options)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  File "/usr/lib/python2.7/dist-packages/samba/__init__.py", line 113, in __init__[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]    self.connect(url, flags, options)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 72, in connect[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]    options=options)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]_ldb.LdbError: (80, 'dsdb_module_search_dn: did not find base dn @ROOTDSE (0 results)')[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dpkg: error processing samba4 (--configure):[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] subprocess installed post-installation script returned error exit status 1[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Setting up apt (0.8.16~exp12ubuntu4) ...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: UP[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: UP[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dpkg: error processing apt (--configure):[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] subprocess installed post-installation script returned error exit status 127[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Errors were encountered while processing:[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] samba4[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman] apt[/FONT][/SIZE]

---

### Post by RedSingularity on 2012-02-26
[SIZE=2]Alright try running these commands:

[/SIZE]  [SIZE=2]1) su
2) mkdir temp
3) mv /usr/local/lib/libreadline* temp
4) ldconfig 
5) apt-get update[/SIZE]

---

### Post by younglemon on 2012-02-26
I do not know the password for su.  I don't know why it's not my password but, I'm going to try this with sudo instead

---

### Post by younglemon on 2012-02-26
Its been so long since I've seen it succeed, does this mean it worked?
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo mkdir temp[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][sudo] password:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ mv /usr/local/lib/libreadline* temp[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]mv: cannot create regular file `temp/libreadline.a': Permission denied[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]mv: cannot create symbolic link `temp/libreadline.so': Permission denied[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]mv: cannot create symbolic link `temp/libreadline.so.6': Permission denied[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]mv: cannot create regular file `temp/libreadline.so.6.2': Permission denied[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo mv /usr/local/lib/libreadline* temp[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo ldconfig[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo apt-get update[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security InRelease[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed InRelease[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release.gpg [198 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed Release.gpg [198 B][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed Release[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [927 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages [1,287 kB][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages [1,287 kB][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex [3,570 B] [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Sources [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main amd64 Packages [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main i386 Packages [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main TranslationIndex [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main Sources [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main amd64 Packages [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main i386 Packages [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main TranslationIndex [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Translation-en [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main Translation-en [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Fetched 3,555 kB in 7s (503 kB/s) [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Reading package lists... Done[/SIZE][/FONT]

---

### Post by RedSingularity on 2012-02-26
Looks like its working now.  And yes, sorry, by default su is disabled for security.

---

### Post by younglemon on 2012-02-26
I attemped to update from the error mesage and it instructed me to try "apt-get install -f"  
Below is the output. Thanks for the previous.  I'm now reading about 'ldconfig', fascinating.
[FONT=Times New Roman][SIZE=3]Serv:~$ sudo apt-get install -f[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Reading package lists... Done[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Building dependency tree       [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Reading state information... Done[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Correcting dependencies... Done[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The following packages were automatically installed and are no longer required:[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  libindicator3-6 libindicator6 libpng12-0:i386 libllvm2.9[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Use 'apt-get autoremove' to remove them.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The following extra packages will be installed:[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  gwibber gwibber-service[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Suggested packages:[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  gwibber-service-flickr gwibber-service-digg gwibber-service-statusnet[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  gwibber-service-foursquare gwibber-service-friendfeed gwibber-service-pingfm[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  gwibber-service-qaiku unity-lens-gwibber[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]The following packages will be upgraded:[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  gwibber gwibber-service[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]2 upgraded, 0 newly installed, 0 to remove and 510 not upgraded.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]2 not fully installed or removed.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Need to get 0 B/196 kB of archives.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]After this operation, 115 kB disk space will be freed.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Do you want to continue [Y/n]? y[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Setting up apt (0.8.16~exp12ubuntu4) ...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]gpg: Total number processed: 2[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]gpg:              unchanged: 2[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3](Reading database ... 435005 files and directories currently installed.)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Preparing to replace gwibber 3.3.2-0ubuntu2 (using .../gwibber_3.3.90-0ubuntu1_amd64.deb) ...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unpacking replacement gwibber ...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Preparing to replace gwibber-service 3.3.5-0ubuntu3 (using .../gwibber-service_3.3.90-0ubuntu1_all.deb) ...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unpacking replacement gwibber-service ...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Processing triggers for bamfdaemon ...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Rebuilding /usr/share/applications/bamf.index...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Processing triggers for gnome-menus ...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Processing triggers for desktop-file-utils ...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Processing triggers for hicolor-icon-theme ...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Processing triggers for gconf2 ...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Processing triggers for libglib2.0-0 ...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Processing triggers for libglib2.0-0:i386 ...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Setting up samba4 (4.0.0~alpha17.dfsg2-1) ...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "auth methods"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "auth methods"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "map to guest"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "map to guest"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "passwd program"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "passwd program"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "max log size"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "max log size"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "os level"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "os level"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "domain master"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "domain master"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "usershare allow guests"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "usershare allow guests"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "admin users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "admin users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "valid users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "valid users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "force group"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "force group"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "valid users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "valid users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "share modes"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "share modes"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "guest ok"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "guest ok"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "auth methods"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "auth methods"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "map to guest"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "map to guest"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "passwd program"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "passwd program"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "max log size"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "max log size"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "os level"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "os level"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "domain master"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "domain master"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "usershare allow guests"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "usershare allow guests"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "admin users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "admin users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "valid users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "valid users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "force group"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "force group"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "valid users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "valid users"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "share modes"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "share modes"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unknown parameter encountered: "guest ok"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ignoring unknown parameter "guest ok"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]module samba_dsdb initialization failed : No such object[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Unable to load modules for /var/lib/samba/private/sam.ldb: dsdb_module_search_dn: did not find base dn @ROOTDSE (0 results)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Traceback (most recent call last):[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  File "/usr/share/samba/setup/upgradeprovision", line 1716, in <module>[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]    ldbs = get_ldbs(paths, creds, session, lp)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  File "/usr/lib/python2.7/dist-packages/samba/upgradehelpers.py", line 156, in get_ldbs[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]    ldbs.sam = SamDB(paths.samdb, session_info=session, credentials=creds, lp=lp, options=["modules:samba_dsdb"])[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 57, in __init__[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]    options=options)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  File "/usr/lib/python2.7/dist-packages/samba/__init__.py", line 113, in __init__[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]    self.connect(url, flags, options)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 72, in connect[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]    options=options)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]_ldb.LdbError: (80, 'dsdb_module_search_dn: did not find base dn @ROOTDSE (0 results)')[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dpkg: error processing samba4 (--configure):[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] subprocess installed post-installation script returned error exit status 1[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Setting up gwibber-service (3.3.90-0ubuntu1) ...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]No apport report written because MaxReports is reached already[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]                                                              Setting up gwibber (3.3.90-0ubuntu1) ...[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Errors were encountered while processing:[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] samba4[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]E: Sub-process /usr/bin/dpkg returned an error code (1)[/SIZE][/FONT]

---

### Post by RedSingularity on 2012-02-26
Looks like samba4 is giving you an issue at this point.  Maybe you can remove that package and install the regular 'samba' package?  Are you able to remove packages now?

---

### Post by younglemon on 2012-02-26
Alright so, it seems like some things are better. Although I'm still tempted to click "partial upgrade" when it prompts me with that option, I'm guessing I shouldn't. So, do you think I'm out of the woods now? What was it that the last set of commands did? We made a directory, then moved it to a spot where the update package was looking for it, correct? Then what, we somehow dynamically bound it to the system package as to force the update? If that is correct, and it worked as planned, how would I best proceed from here? Thanks again RedSingularity, you are truly awesome. Please let me know if there is something I can do for you, thanks again.

---

### Post by RedSingularity on 2012-02-26
Well it seems the 'libreadline.so' files were corrupt.  Thats why you were getting error messages about them.  We removed the corrupt files and replaced them with new ones for your current sources.  (You can remove that temp directory we created too in post 39)

You can try the partial upgrade if you like.  Or a dist-upgrade if you rather do it via command line.

---

### Post by younglemon on 2012-02-27
Thank you so much again. 
 
Honestly, I'm still a little leery of a distribution upgrade.  However, it appears that I have obsolete packages installed and will have to update them.  Is there a way to update a specific package or, would this be done with a distribution or partial upgrade?

---

### Post by RedSingularity on 2012-02-27
Well apt-get install <package> will update a specific package for you.  

A 'dist-upgrade' is not a distribution upgrade though so dont worry.  Thats a common misconception because of its name.  You are already running the latest unstable release too so you cannot go any higher on the distribution scale.  Since its unstable you may get more errors in the near future unfortunately.  

I am happy to help anytime :)

PS:  I am going to close your bug report.  Its not a system bug, but more of a 'local error'.

---

### Post by younglemon on 2012-02-27
You're the best, yes please close it, thank you so much.

---

### Post by younglemon on 2012-02-27
[COLOR=black][FONT=Verdana]I am still new to Ubuntu and Linux. I love that I get regular updates and I am a sucker for available upgrades. Sometimes, apparently, it corrupts files and directories which can wreak havoc. I thank you for all of your time and effort assisting me and my uncontrollable "upgrade available" affliction. I'm sure that you haven't heard the last from me, so please let me know if there is ever anything I can do for you. I'm in Southern NJ and could get you those beers I owe you, we could go out either in NYC or Atlantic City. ;) Again, thank you so much![/FONT][/COLOR]

---

### Post by RedSingularity on 2012-02-27
Lol, maybe I will take you up on that beer one day.  And again, I am happy to help anytime so please feel free to ask.  ;)

---

### Post by younglemon on 2012-02-28
> **younglemon said:**
> I am unable to copy the file in this way, not sure why exactly. It reads "mv: cannot stat '/ect/apt/sources.list': No such file or directory". 
 
I'm going to attempt to acheive the same results using a slightly different method, please let me know if what I'm trying will not work. I am going to take ownership of this location and file by way of using 
sudo chown me /etc/apt/
Then I will copy the contents of the generated files as you previously described. 
 
More to follow shortly
 
I'm just re-reading this thread and realizing that it could copy/move because I entered the path incorrectly 'etc'. D'oh! I'm sometimes my own worst enemy.
 
Thanks again RedSigularity. I hope to have the opportunity to buy you a fine quality craft brew one day, as I'm sure that you'll be hearing from me again :)

---

