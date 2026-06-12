---
title: "Offline Synaptic Installation/Repository Updates"
date: 2011-12-28
forum: Tutorials
---

### Post by cortman on 2011-12-28
[SIZE="4"]**Offline Synaptic Installation/Repository Updates**[/SIZE]



**Goal:** To allow users with fresh installations of Ubuntu that don&#8217;t have internet access with that machine to install software from the Ubuntu repositories. I&#8217;ve never seen a tutorial or tip like this, so I hope it will meet some hitherto unmet needs.


**Skill level:** Basic. I&#8217;ve tried to make this pretty simple. I recommend you copy/paste all code given in this tutorial rather than type it out, to make sure no typos occur. 
If you have any questions at all leave a comment at the bottom of the page. I&#8217;ll try and keep this updated and provide support.


**About:** This tutorial is especially aimed at users with a fresh installation of Ubuntu 11.10 on their computer but with no internet connection available to that computer. If you can get your computer online, by all means skip this tutorial and install your software the easy way. 

Many people still don&#8217;t have internet access at home, and many of those people own desktop computers, which aren&#8217;t very portable to local wifi hotspots or internet cafés. That&#8217;s where these instructions will be handy.

This tutorial assumes you have access to a second computer running Ubuntu with an internet connection. We&#8217;ll refer to this as your &#8220;online&#8221; PC, and your first machine as the &#8220;offline&#8221; one.
Since the easiest and most common tool for offline software installation, Synaptic Package Manager, doesn&#8217;t come bundled with Ubuntu any more (as of 11.10) this tutorial will guide you through installing Synaptic first.


**[SIZE="2"]IMPORTANT:[/SIZE]** Before you do anything else, you first need to know whether your **offline** Ubuntu installation uses 32 or 64 bit architecture. To find this out, open a terminal by typing 

> Control+Alt+t

When the terminal is open, copy/paste the following code at the prompt:

```
uname &#8211;m
```

This will give an output of either **x86_64** (64 bit) or **i686 &#8211; i386** (32 bit). The packages are different for 64 and 32 bit, but the whole basic procedure will remain the same. Just remember throughout this tutorial which your system uses.


Now to install Synaptic!


**[SIZE="2"]1.[/SIZE]** On the online computer: Make a new folder in your home folder called &#8220;synaptic&#8221; (no quotes, obviously).

**[SIZE="2"]2.[/SIZE]**If your offline system is **32 bit**, open a text editor and paste the code below into it-

```

#!/bin/sh
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.6/libstdc++6_4.6.1-9ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.6/libgcc1_4.6.1-9ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.30.0-0ubuntu4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-6_1.4.4-2ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gdk-pixbuf/libgdk-pixbuf2.0-0_2.24.0-1ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.24.6-0ubuntu5_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.29.3+git20110916-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-pkg4.11_0.8.16~exp5ubuntu13_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.13-20ubuntu5_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-inst1.3_0.8.16~exp5ubuntu13_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/h/hicolor-icon-theme/hicolor-icon-theme_0.12-1ubuntu1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libe/libept/libept1_1.0.5build1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/launchpad-integration/liblaunchpad-integration1_0.1.54_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte9_0.28.2-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xapian-core/libxapian22_1.2.5-1ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/s/synaptic/synaptic_0.75.2ubuntu8_i386.deb 
```


If your offline system is **64 bit**, paste this code instead:

```

#!/bin/sh
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.6/libstdc++6_4.6.1-9ubuntu3_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.6/libgcc1_4.6.1-9ubuntu3_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.30.0-0ubuntu4_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-6_1.4.4-2ubuntu1_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gdk-pixbuf/libgdk-pixbuf2.0-0_2.24.0-1ubuntu1_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.24.6-0ubuntu5_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.29.3+git20110916-0ubuntu1_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-pkg4.11_0.8.16~exp5ubuntu13_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.13-20ubuntu5_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-inst1.3_0.8.16~exp5ubuntu13_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/h/hicolor-icon-theme/hicolor-icon-theme_0.12-1ubuntu1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libe/libept/libept1_1.0.5build1_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/launchpad-integration/liblaunchpad-integration1_0.1.54_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte9_0.28.2-0ubuntu2_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xapian-core/libxapian22_1.2.5-1ubuntu1_amd64.deb
wget &#8211;c http://us.archive.ubuntu.com/ubuntu/pool/universe/s/synaptic/synaptic_0.75.2ubuntu8_amd64.deb 
```


This is a complete download script for Synaptic, with all dependencies. Save this file as synapt.sh in the folder &#8220;synaptic&#8221; that you just created.


**[SIZE="2"]3.[/SIZE]** Open a terminal (Control+Alt+t again) and copy/paste the following code at the prompt.


```
 chmod +x synaptic/synapt.sh
```


Then run


```
./synapt.sh
```


All the required packages for Synaptic will be downloaded into the &#8220;synaptic&#8221; folder. They&#8217;ll all have a .deb file extension.


**[SIZE="2"]4.[/SIZE]** Use a flash drive to copy the folder to the **[SIZE="2"]offline[/SIZE]** computer&#8217;s home. Open a terminal and type


```
sudo dpkg &#8211;iR synaptic 
```


Enter your password at the prompt. This will install Synaptic on your offline computer. The first step is done!



**[SIZE="3"]STEP 2: Update Repositories[/SIZE]**


Almost all the software available for Ubuntu is stored on Canonical servers. These software groups are called repositories. In the software installation process Synaptic simply sends a message to these servers telling them which packages to download, and then installs it for you. You did the process manually yourself when you installed Synaptic in the previous step.

Before downloading anything from a repository, Synaptic needs to know exactly what is in the repository in the first place. Each repository contains a compressed text file with a long list of all software packages available in that repository. Synaptic looks at that info and relays that to you in the program. Since our offline Synaptic can&#8217;t query a server, we need to download those lists of packages, copy them onto the offline computer, and tell Synaptic to look on the computer itself for the info. Follow this part very closely.

**NOTE:** This step is for users of Ubuntu 11.10 Oneiric Ocelot. I&#8217;ll try and keep this page updated for later versions. The same procedures will still apply no matter what version of Ubuntu you have; the only difference will be the name of the version.

**[SIZE="2"]1.On your online computer:[/SIZE]** Direct your web browser to

[http://ubuntu.secs.oakland.edu/dists/](http://ubuntu.secs.oakland.edu/dists/) 

This is where the repositories for all Ubuntu versions from Hardy Heron to Oneiric Ocelot are kept. If you&#8217;re running Oneiric (as this tutorial assumes you are) select &#8220;oneiric&#8221;.
This will take you to another page, where you&#8217;ll select &#8220;main/&#8221;. 
On the next page, select &#8220;binary-i386/&#8221; if your computer is 32 bit, or &#8220;binary-amd64/&#8221;. 
On the next page, select &#8220;Packages.gz&#8221;. 
This will download a compressed text file with the list of all available software in the Main Ubuntu repository. Save the compressed file (don&#8217;t uncompress it!) to its own folder on your flash drive. Since you&#8217;ll be downloading 4 of these compressed files (all having the same name) saving them in individual folders will help keep them sorted out.
Go back to 

[http://ubuntu.secs.oakland.edu/dists/oneiric/](http://ubuntu.secs.oakland.edu/dists/oneiric/) 

and follow the above procedure with &#8220;multiverse/&#8221;, &#8220;restricted/&#8221; and &#8220;universe/&#8221;.
When it&#8217;s all said and done you should have 4 Packages.gz files on your flash drive. 


**[SIZE="2"]2.[/SIZE]** Take your flash drive to the**[SIZE="2"] offline[/SIZE]** computer and open a terminal. Copy/paste the following command-

For a 32 bit system: 

```
mkdir &#8211;p ~/dists/oneiric/main/binary-i386 ~/dists/oneiric/multiverse/binary-i386 ~/dists/oneiric/restricted/binary-i386 ~/dists/oneiric/universe/binary-i386

```

For a 64 bit system: 

```
 mkdir &#8211;p ~/dists/oneiric/main/binary-amd64 ~/dists/oneiric/multiverse/binary-amd64 ~/dists/oneiric/restricted/binary-amd64 ~/dists/oneiric/universe/binary-amd64

```

This command makes a number of new folders in your home folder. It&#8217;s important that you don&#8217;t delete or edit these folders in any way in the future.

**[SIZE="2"]3.[/SIZE]** Copy each Packages.gz file to its corresponding folder in home- i.e., the file you got from Main goes in dists/oneiric/main/binary-i386, the file from Multiverse goes in dists/oneiric/multiverse/binary-i386, etc. Again, don&#8217;t uncompress any of these files!

**[SIZE="2"]4. [/SIZE]**Once these are all copied over, open a terminal and type


```
synaptic
```


To open Synaptic Package Manager. In Synaptic, click Settings>Repositories.
This will bring up the repository dialog box. Select the &#8220;Other Software&#8221; tab.


[IMG]http://dl.dropbox.com/u/54881717/synaptic%20tutorial/new%20repo.png[/IMG]
 

Select &#8220;Add&#8230;&#8221;.
What you&#8217;ll be doing is telling Synaptic where it can look to find software information other than the online repositories. 
In the Add Repository dialog, type the following

```
 deb file:/home/your_user_name oneiric main 
```

[IMG]http://dl.dropbox.com/u/54881717/synaptic%20tutorial/repo_name.png[/IMG]
 
Obviously, change your_user_name to your user name. Note that after your user name there&#8217;s a space, the name of the Ubuntu version (oneiric), space, and then the repository name (main, multiverse, universe, restricted).

Click Add Source and you&#8217;re done. Repeat this process, substituting the name of each repository for &#8220;main&#8221;. When you&#8217;re done you&#8217;ll have added four new repositories. It should look like this.


[IMG]http://dl.dropbox.com/u/54881717/synaptic%20tutorial/sources.png[/IMG]
 

Synaptic will automatically add four other &#8220;Source Code&#8221; repositories. In my experience with offline package managing these don&#8217;t serve any purpose and generate confusing error messages, so go ahead and remove each one that has &#8220;Source Code&#8221; appended to the end of the name.
When you&#8217;re done with that, close out of the Repositories dialog and click the large &#8220;Reload&#8221; button in the upper left.

The reloading process WILL give you an error message, simply because it wasn&#8217;t able to contact the Ubuntu servers. Scroll down to the bottom of the error log. If you don&#8217;t see any errors about your recently added repositories, the update was successful!


[IMG]http://dl.dropbox.com/u/54881717/synaptic%20tutorial/error.png[/IMG]


You&#8217;re all set to install software now! For info on how to get started with that, see [my other tutorial]("http://ubuntuforums.org/showthread.php?t=1900550") on how to install software offline using Synaptic.

**NOTE: **There is one hitch with this type of offline installation and updating. Any download script you produce with this will have instructions to download from your /home/ repository, rather than the real ones. Here's a sample:

```
wget -c file:/home/cortman/pool/main/x/xaw3d/xaw3dg_1.5+E-18_i386.deb
wget -c file:/home/cortman/pool/universe/3/3dchess/3dchess_0.8.1-17_i386.deb
```

To fix it, you need to open the download script in a text editor and change file:/home/your_username to the real URL of the repository. If you're in the US, just change them to this:

```
wget -c **http://us.archive.ubuntu.com/ubuntu**/pool/main/x/xaw3d/xaw3dg_1.5+E-18_i386.deb
wget -c **http://us.archive.ubuntu.com/ubuntu**/pool/universe/3/3dchess/3dchess_0.8.1-17_i386.deb
```

If you're not in the US and can figure out your nearest repository, great! Otherwise, the US one will work, albeit more slowly, and if you want me to find your nearest repository, post the request on this thread. Good luck!

---

### Post by bahha on 2012-01-01
Thank you sir this helped me a lot


 I'm offline because I couldn't install my 3g modem it need usb-modeswitch  and wvdial 
and they have many dependencies so I'm going to use synaptic manager to install them this way

there is a problem; 

with sudo dpkg -iR synaptic      ( it doesnt exist )  so which deb file is the main one to dpgk )

---

### Post by bahha on 2012-01-01
I got it thanks again I thought I had to cd to the synaptic folder first   beginner mistake

---

### Post by cortman on 2012-01-02
Glad it helped! Sorry I wasn't available over the weekend for support- any other questions feel free to ask.

---

### Post by Andrew_nuts on 2012-01-18
Thanks for the tutorial it works great for me. Only issue is Synaptic manger is not installed by default in Ubuntu 11.10. I have to installed manually

---

### Post by cortman on 2012-01-18
> **Andrew_nuts said:**
> Thanks for the tutorial it works great for me. Only issue is Synaptic manger is not installed by default in Ubuntu 11.10. I have to installed manually

Uh... that's what this tutorial is all about?
Installing manually IS a pain. I don't understand why Ubuntu chose to stop bundling Synaptic with their OS.

---

### Post by Double.J on 2012-01-18
Thanks for another great tut Cortman! a definate improvement on having to go back and forth to pkgs.org to get dependencies! :D

---

### Post by cortman on 2012-01-19
> **gnu/mirow said:**
> Thanks for another great tut Cortman! a definate improvement on having to go back and forth to pkgs.org to get dependencies! :D

Sure! I'm working on a script that should automate about half of this stuff...

---

### Post by ebeth on 2012-02-03
Excellent tutorial.

I'm not sure I did step 3 correctly.  

I couldn't make the new  directories using the mkdir command.  I just created the directories  myself.

Then, after typing "synaptic" in the terminal window, I got this error:

(synaptic:7168): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
Aborted

What did I do wrong.

---

### Post by cortman on 2012-02-03
The pixmap warning is to be ignored, it's a harmless bug.
So Synaptic won't start? Have you tried starting with

```
gksu synaptic
```

Or from a menu?

---

### Post by ebeth on 2012-02-03
OK, I won't worry about the pixmap warning.  I went back and checked every step and found I did have a typo in one of the folder names, I corrected that then used gksu synaptic.

It opened for just a second then disappeared.

---

### Post by cortman on 2012-02-04
Still strange. Can you start it from the launcher? (Assuming you're using unity)
There is a bug in synaptic that keeps it from opening properly- I'm on my mobile right noe so can't look it up, but Google "fix synaptic accessibility". It has something to do with the accessibility settings.
Ill get back with you later!

---

### Post by ebeth on 2012-02-04
Thanks cortman.  I got it working!  

I had two issues that, I think, prevented the proper install.  One was the accessibility issue which I found info about here: [http://askubuntu.com/questions/69474/synaptic-package-manager-keeps-crashing](http://askubuntu.com/questions/69474/synaptic-package-manager-keeps-crashing)

The other was a cut and paste error.  At step 3 I just copied and pasted the entire string into the terminal window ("mkdir -p...")  What actually copied wasn't a dash '-", but an emdash.  (I've changed some prefs in Firefox to make it easier to read. Could be the problem with copy/paste?)  I ended up with a directory called "-p".  When I typed "mkdir -p " then just copied and pasted the directory names I was good to go.

Thank you again for the excellent instructions - I couldn't have done this without them.  And, even with the errors I learned a lot about the OS.  One warning I would give to others: Don't try this late at night while sipping a fine glass of Merlot. ;-)
[]("http://askubuntu.com/questions/69474/synaptic-package-manager-keeps-crashing")

---

### Post by cortman on 2012-02-04
> **ebeth said:**
> Thanks cortman.  I got it working!  

I had two issues that, I think, prevented the proper install.  One was the accessibility issue which I found info about here: [http://askubuntu.com/questions/69474/synaptic-package-manager-keeps-crashing](http://askubuntu.com/questions/69474/synaptic-package-manager-keeps-crashing)

The other was a cut and paste error.  At step 3 I just copied and pasted the entire string into the terminal window ("mkdir -p...")  What actually copied wasn't a dash '-", but an emdash.  (I've changed some prefs in Firefox to make it easier to read. Could be the problem with copy/paste?)  I ended up with a directory called "-p".  When I typed "mkdir -p " then just copied and pasted the directory names I was good to go.

Thank you again for the excellent instructions - I couldn't have done this without them.  And, even with the errors I learned a lot about the OS.  One warning I would give to others: Don't try this late at night while sipping a fine glass of Merlot. ;-)
[]("http://askubuntu.com/questions/69474/synaptic-package-manager-keeps-crashing")

Great- I'm glad the error was as simple as it was, and the Synaptic bug was fixable. That's the positive thing about bugs in the OS- it sure teaches you about it!
Thanks for the kind comments, and good advice. Best wishes!

---

### Post by elliotn on 2012-02-07
This method works great but I found one flop, when u generate download package script in synaptic the script contains URI'S but the uri's won't be able to download the packages as intended. WHY? that's because the uri's address point to [http://file.home/pool](http://file.home/pool) instead of [http://za.ubuntu.com/ubuntu/pool/](http://za.ubuntu.com/ubuntu/pool/) thus one have to use Gedit and replace the file.home/pool with the correct one, I will post screenshots soon

---

### Post by cortman on 2012-02-07
> **elliotn said:**
> This method works great but I found one flop, when u generate download package script in synaptic the script contains URI'S but the uri's won't be able to download the packages as intended. WHY? that's because the uri's address point to [http://file.home/pool](http://file.home/pool) instead of [http://za.ubuntu.com/ubuntu/pool/](http://za.ubuntu.com/ubuntu/pool/) thus one have to use Gedit and replace the file.home/pool with the correct one, I will post screenshots soon

In other words, you're saying it didn't work because my script points to the default mirror for the US, whereas you, being in South Africa, needed it to point to the .za mirror.
Downloads from the US still should work, just slower. And as much as I'd like to, it wouldn't be feasible to include a script for every possible mirror.
Thanks for pointing it out, though, and if anyone has this problem, please post on this thread and I'll see if I can tweak it to work with your country's repositories.

---

### Post by elliotn on 2012-02-08
> **cortman said:**
> In other words, you're saying it didn't work because my script points to the default mirror for the US, whereas you, being in South Africa, needed it to point to the .za mirror.
Downloads from the US still should work, just slower. And as much as I'd like to, it wouldn't be feasible to include a script for every possible mirror.
Thanks for pointing it out, though, and if anyone has this problem, please post on this thread and I'll see if I can tweak it to work with your country's repositories.

no no the script works, what I meant is updating repository using the package.gz and when u Generate  the Download Package script to use it to download on an online PC, the script uri's doesn't point to a active mirror but it points to file/home/ instead of za/us.achieve.ubuntu.com/ubuntu/pool blah blah

---

### Post by elliotn on 2012-02-08
> **cortman said:**
> In other words, you're saying it didn't work because my script points to the default mirror for the US, whereas you, being in South Africa, needed it to point to the .za mirror.
Downloads from the US still should work, just slower. And as much as I'd like to, it wouldn't be feasible to include a script for every possible mirror.
Thanks for pointing it out, though, and if anyone has this problem, please post on this thread and I'll see if I can tweak it to work with your country's repositories.
check the screenshot below it says it all 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212277&stc=1&d=1328699972[/IMG]

---

### Post by cortman on 2012-02-08
Thank you for catching this. What about changing it so that instead of adding new repositories, you simply move the list file into /var/lib/apt and replace the existing one? The only hitch would be if update wouldn't work- but it shouldn't even really need to update, since it'd just be reading from the existing files.

EDIT: How about a script that would cut out the file/home/ and replace it with the archive mirror? It'd be one extra step, but it'd be more convenient than editing it manually.
If there is some more streamlined way of doing this that I am totally missing, I should probably just close this and point people to it...

---

### Post by elliotn on 2012-02-08
> **cortman said:**
> Thank you for catching this. What about changing it so that instead of adding new repositories, you simply move the list file into /var/lib/apt and replace the existing one? The only hitch would be if update wouldn't work- but it shouldn't even really need to update, since it'd just be reading from the existing files.

I find the Gedit method of replacing the the uri's simpler as it doesn't need no effort

---

### Post by cortman on 2012-02-08
> **elliotn said:**
> I find the Gedit method of replacing the the uri's simpler as it doesn't need no effort

Thank you very much for making me aware of this. I think I'll just add a note on changing the mirrors in gedit. I tested the installation and update process many times before I wrote this, but it never occurred to me that the scripts would be off. Thanks again.

EDIT: Updated the tutorial.

---

### Post by DaimyoKirby on 2012-02-25
I followed all the instructions, but I have a question with the "errors" you said we should get once we reload synaptic.
I'm getting a strange error:
```

W: Failed to fetch file:/home/alden/dists/oneiric/main/binary-i386/
Packages File not found
```
Along with the other four folders - restricted, multiverse, universe.
I ran *uname -m*, however, and it returned x86_64, which you said indicates a 64-bit installation.
Do I have to worry about these errors?

---

### Post by cortman on 2012-02-25
> **DaimyoKirby said:**
> I followed all the instructions, but I have a question with the "errors" you said we should get once we reload synaptic.
I'm getting a strange error:
```

W: Failed to fetch file:/home/alden/dists/oneiric/main/binary-i386/
Packages File not found
```Along with the other four folders - restricted, multiverse, universe.
I ran *uname -m*, however, and it returned x86_64, which you said indicates a 64-bit installation.
Do I have to worry about these errors?

Well, it could be a number of things.


[LIST]
[*]Did you install the 32 bit or 64 bit version of Synaptic?
[*]Did you run the "mkdir" command for the 32 bit or 64 bit?
[*]When you added the local repositories in Synaptic, did you point them to an amd_64 folder or an i386 folder?
[*]Did you download the 64 bit or 32 bit Packages.gz files?
[/LIST]
It could be one of these. Are all your locally added repositories returning this error?

---

### Post by DaimyoKirby on 2012-02-26
As far as I can tell, I did everything right:
[list]
[*]I have Xubuntu 11.10 installed, which comes with Synaptic.
[*]I ran the mkdir for 64-bit, and just to make sure, I ran it again, and it said the folders were already created.
[*]I'm not sure, so that could be the problem...it doesn't seem to say anything about pointing the folders in your instructions...or I just missed it.
[*]I definitely downloaded the 64-bit, since I re-downloaded them just to make sure.
[/list]
If you mean all the four that I added myself, yes. If not, then you'll need to explain what you mean, since I don't really know what that means.

Also, I don't know if it matters, but
1. This isn't a fresh install of Xubuntu.
2. The computer I have with an internet connection is running Windows XP.

---

### Post by cortman on 2012-02-26
Sorry if I wasn't clear! One thing to check that will clear some up- visit each folder in your file browser (thunar). Make sure the actual folders ARE amd_64 and not i386. Also confirm that there is a zipped file named Packages in each one.
If they are indeed amd_64, did you perhaps accidentally add the repository in Synaptic as i386?

I'm sorry it's giving you trouble! Keep me posted and we'll work it out. Good luck!

---

### Post by DaimyoKirby on 2012-02-27
Well, just for kicks I created four more folders named binary-i386 in their respective places, and put a copy of each Packages.gz file into their respective i386 folders (even though the files are amd64), and I didn't get any (abnormal, local)errors...
:-s
How should they have been added in Synaptic as amd64 instead of i386?

---

### Post by cortman on 2012-02-27
> **DaimyoKirby said:**
> Well, just for kicks I created four more folders named binary-i386 in their respective places, and put a copy of each Packages.gz file into their respective i386 folders (even though the files are amd64), and I didn't get any (abnormal, local)errors...
:-s
How should they have been added in Synaptic as amd64 instead of i386?

Open Synaptic and go to Settings>Repositories> and make SURE the file path says amd_64. This just sounds like somehow you've given the i386 path to Synaptic. Double check that the actual folders ARE called amd_64.

---

### Post by DaimyoKirby on 2012-02-27
Oh, I just noticed that something weird is going on: I changed all the folders to "binary-amd_64", versus "binary-amd64", just in case I named them wrong; I got not only the i386 errors, but also amd64 errors.
So I'm correct in saying that my computer seems to be searching for both amd64 *and* i386 repositories?

Also, this is what I'm looking at on my computer:
[spoiler]
[IMG]http://i.imgur.com/ITbf2l.png[/IMG]
[IMG]http://i.imgur.com/flMsQl.png[/IMG]
[/spoiler](meh, don't know why the spoiler tags aren't working...)
I think everything is right there.

---

### Post by cortman on 2012-02-28
> **DaimyoKirby said:**
> 
So I'm correct in saying that my computer seems to be searching for both amd64 *and* i386 repositories?

This sounds right. Try deleting and re-adding the repositories in Synaptic?

---

### Post by DaimyoKirby on 2012-03-02
Do you mean to delete just the ones that I added? If so, should I also delete the actual folders I made, and remake them?

If you mean something different, how would I go about it?

---

### Post by cortman on 2012-03-02
> **DaimyoKirby said:**
> Do you mean to delete just the ones that I added?

Yes, in Synaptic.

> **DaimyoKirby said:**
> If so, should I also delete the actual folders I made, and remake them?

If you have actually checked that they're called "binary-amd64" and they are, no need to delete them.

Re-add the local repositories in Synaptic.

---

### Post by zgqcliff on 2012-09-20
Does this method work for 12.04LTS ?

---

### Post by cortman on 2012-09-20
> **zgqcliff said:**
> Does this method work for 12.04LTS ?

It should, yes. Although if you can install Synaptic normally and update online, even just once, it's definitely worth it.

---

### Post by rajhanschinmay on 2012-12-16
Kindly select ur Ubuntu version:
[http://www.ubuntuupdates.org/pm/synaptic](http://www.ubuntuupdates.org/pm/synaptic)

Then download the .deb package file.
To install kindly use dpkg command as:
dpkg -i package_name.deb

Thank you.

---

### Post by puzzledinportorchard on 2013-01-31
I want to thank you - and even praise you:All Hail the Bard! - for your clear instructions.  I have an offline Pentium 4 running Xubuntu 12.04.1 LTS and an online running a LiveCD of 10.04, and using your method I have successfully updated the repository list (or whatever the hell it's called).  This is the clearest and most precise set of instructions on anything that I've ever encountered in Linux.  Bless you.

Some comments about my experience: First, I did have the problem as above about having the 'copy' function replace the dash in front of 'p' with an extra space and some different sort of dash, so I ended up with a folder called '-p'.  An easy thing to fix.

The other two things came as pleasant surprises; Synaptic 0.75.9 must have seen me coming, because instead of making four entries and their Source Code duplicates, and even though as instructed I added them one at a time, Synaptic made two entries: one with 'main universe multiverse restricted' all on one line, and the same with 'Source Code' at the end (which, as advised, I removed.)  And when I made a script I found I didn't have to replace /home/myname with the http for the mirror sight; it made the normal link.  Clearly, the people who updated Synaptic have dealt with well-educated idiots like me before!

Bless you.  Thank you.

However, my attempt to download VLC through this USB-key method didn't work; I got all the '404' errors I got before.  But I think it's off this topic so I'll take it to the newbie forum and see what results I get.  Thank you again and a bazillion times.

---

### Post by puzzledinportorchard on 2013-01-31
Now I'm not so sure it worked.  Just redid the whole process.  The directory is just as it should be.  The packages.gz are each in the right directory, everything spelled just right.  They're still unpacked after the refresh, though; should they be?  And the error messages, containing as expected all the calls to http's also have this, four times:

Failed to fetch file:/home/[myname]/dists/precise/multiverse[and main, etc.]/binary-i386/Packages

But why is it trying to fetch those?  I have checked most carefully: the packages are each there, but in .../binary-amd64, as they should be.  Are the packages supposed to remain unpacked after Synaptic reloads?

I know that something has changed - a package, ubuntu-restricted-extras, is now listed in Synaptic and it wasn't before; but out of the 20 calls to fetch in the script generated to get this file, only six were successful.  I have checked the directory very carefully; /home/[me]/dists/precise/main[etc]/binary-amd64/ - each with its own unpacked .gz - and I was very careful to get the right ones, the AMD64s; but Synaptic generates scripts that don't work.

---

### Post by puzzledinportorchard on 2013-02-01
It has been confirmed elsewhere that the scripts Synaptic is generating for me are making calls to files that have been replaced by newer ones with different names.  So I've done something wrong and am not, in fact, updating Synaptic.

---

### Post by puzzledinportorchard on 2013-02-01
> **cortman said:**
> Open Synaptic and go to Settings>Repositories> and make SURE the file path says amd_64. This just sounds like somehow you've given the i386 path to Synaptic.

I'm embarrassed to say I missed this part of the discussion my first two times through the thread.  It's certainly pertinent to my current problem.  But I don't understand the answer.  I've gone over and over the tutorial, both here and on my offline, and repeated the steps again and again.  When I go to Settings>Repositories and select that one line that Synaptic put my home file on, I don't see anywhere where any path at all is pointed to.  As far as I can find I haven't anywhere told Synaptic anything about where to find the files except /home/[me]/ , the word 'precise' and the words 'main, universe, multiverse, restricted'.  Nothing about 'dists'.  Nothing about 'amd-64' OR 'i386'.
 
I tabbed through all the menus in Settings>Repositories.  Everything is exactly as the tutorial says it should be except, as above, that Synaptic took my four seperately-added repos and made them one line.  Where path?  What path?

When I edit the repository entry, I get:
         Type      Binary
          URI       file:/home/[myname]
 Distribution   precise
Components  universe main multiverse restricted.

Another question: if I get this working, and I'm sure I will, I should repeat it whenever I need something new, just before generating the script.  But do I just add the new .gz files to the amd-64 folders or replace the old with the new and reload?

---

### Post by puzzledinportorchard on 2013-02-01
Ooops.  The scripts Synaptic made did make calls to 'file:/' etc. in place of the links it should have.  Just as you'd warned.  I simply hadn't scrolled down the .sh file far enough to see them.  I followed all the links in the script, and indeed the files it didn't fetch had all been updated in the last month.  I'm wondering if I can deduce anything from which calls had been changed to 'file' - that might tell me which package lists had been updated and which not.

For those newbies like me who encounter this, and use gedit to change the script - I discovered that after you save, you have to right-click on the edited file, go to 'Properties>Permissions' and check the box to make it executable again.  Yelling at the computer doesn't work.

---

### Post by puzzledinportorchard on 2013-02-02
I seem to be talking to myself, here. . .

I did (finally!) notice  that in the out-of-date scripts Synaptic is creating, those lines where  it reads 'file' instead of 'http' were all calls to the multiverse  repository, and they all, after correcting, worked: however, I don't  think that means that only the /home/[me] ... /multiverse/ etc package  was read.  On that Settings>Repositories first tab, everything is  checked except the 'multiverse' entry.  So I think that's telling Synaptic to look on line for everything except 'multiverse' calls.  I think.  Maybe.

I've  inspected every part of Synaptic and don't find anywhere where anything  is pointing to amd64 or i386.  I've torn down and rebuilt the file  system many times, both through copying the mkdir command you give (and  erasing and retyping all the dashes and the spaces in front of them  before entering, to insure against the emdash problem), and used the  bash to type it all in from scratch, and used the graphic system to  create them; I've done the whole thing over six times now, from  scratch.  Always the same result; Synaptic will not refresh its package  list, giving me those same four 'can't find ...i386' errors on  reloading, and writing out-of-date scripts.

The file system looks exactly like this:
/home/[me]/dists/precise/main[etc]/binary-amd64/Packages.gz
No extraneous spaces.  No typos.  I could do it now in my sleep.  In fact, I am.

So I tried figuring how to do it by apt.  Not going to happen.

You  mention the possibility that this is the 32-bit, not the 64-bit,  version of Synaptic.  That could be: it was put on the computer a month  ago by experts, but since Xubuntu doesn't include Synaptic anymore by  default, it was apparently added separately.  Synaptic says it is  version 0.75.9.  Synaptic's web page seems last to have been updated in  2004.

When I go to Settings>Repositories>Other Software,  the entries may be telling a story.  The first two are CD's of Ubuntu  (not Xubuntu - I still don't get the difference) 10.04 LTS.  The third  is to an Ubuntu repository about Synaptic.  So I guess that means they  downloaded Synaptic from the 10.04 disk and then updated it.  It does  write, without any prompting I can find, scripts that call for amd64  packages, but I guess that would be the update.  How do I tell if I got  the wrong Synaptic version?

And what do I do if I did?  Surely I  can't use Synaptic to remove and replace Synaptic, I can't use the  Ubuntu Software Center offline, and if I knew how to use apt to replace  Synaptic I wouldn't need Synaptic.

I await enlightenment.

---

### Post by puzzledinportorchard on 2013-02-03
If anyone's reading this thread and is also getting those failed-to-fetch error messages when they click 'reload' after adding the /home repository in Settings>Repositories - at least in 0.75.9 they're not problems.  I tested this by changing the /binary-amd64 folders to /binary-i386 and reloaded.  I then got all the same errors but with -amd64 endings.

Therefore, it appears Synaptic simply searches for both in each of the four folders; so if you have one architecture, and all you see (besides the expected http: errors) are the four file:/home(etc) errors referring to the other architecture, that means Synaptic is successfully reading your file structure.

Which is, of course, good to know, and for me means everything above is working fine (return to position one: ALL HAIL CORTMAN!)  But Synaptic is - what, finding the Packages.gz file and not reading them?  It seems Synaptic is getting *right up to* the right place to read but isn't.  

I looked again at the online repositories and each package that I'd downloaded and placed in the appropriate folder was the size it was supposed to be, and all in the right place, so I know I haven't been putting empty files there or something; but what's actually in them, or if something about my download procedure is corrupting the package, I don't know or know how to test.  Since I've now downloaded them, using every means I could come up with, four or five times, I don't see how they could be being warped every time.  But Synaptic keeps making the exact same scripts with outdated calls.

Next steps: discover what Synaptic uses to either read the file without unpacking it or, if it's supposed to unpack it, why mine isn't.  At this point I suspect the former.

Also that I'm talking to myself.  Hello?

---

### Post by cortman on 2013-02-04
Thanks for the initial kind words. :) Sorry you had some trouble with it.
After writing this tutorial (over a year ago) I realized this method has a number of bugs, like some you've been discovering (the "file:/" part for instance). Sorry I was not available to help- RL has been taking over a lot of my time.
I haven't tried to update this to more recent versions of Ubuntu simply because I don't use Ubuntu very actively anymore and don't have the time. I will see if I can look over what you've written and figure out the problem but it may take me a bit.
Good luck!

---

### Post by puzzledinportorchard on 2013-02-04
I'd been trying to figure out why, in the scripts, the calls to  'multiverse' were fetching correctly, and were the only ones Synaptic  wrote wget commands to 'file:/' to instead of 'http://'.  In 'Settings>Repositories>Ubuntu Software only the 'multiverse' tab was unchecked.  Originally  I had tested this possibility by also unchecking the 'main' box,  reloading, and making the 'ubuntu-restricted-extras' script, and it not  only didn't make any calls to 'main' but left out several 'universe'  calls, and except for the 'multiverse' calls, didn't replace 'http:'  with 'file:', so I thought I was on the wrong scent.  But I've just  tried it again with a different script, and with all those boxes unchecked, and it finally changed all  the calls to 'file:', and the script, after editing, worked

So the two adjustments to this fine tutorial that work, for me at least, using 12.04 and Synaptic 0.75.9, are:

1) If after reloading you get four error messages to 'file:/' etc ending in whichever of amd64 or i386 you *don't* have, you're okay.
2) Uncheck all boxes in 'Setting>Repositories>Ubuntu Software

---

### Post by cortman on 2013-02-18
Just FYI to anyone following this- MG&TL and I are working (sporadically) on a script that would replace Synaptic for the creation of download scripts.
I'll announce its arrival in this thread, if/when it gets accomplished.

---

### Post by ranjanpurbey on 2013-03-02
Thanks Cortman. Helped a lot . But for those looking for updated SYNAPTIC 0.75.9 can use following code :    
```

#!/bin/sh
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/universe/s/synaptic/synaptic_0.75.9ubuntu1_i386.deb
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/main/h/hicolor-icon-theme/hicolor-icon-theme_0.12-1ubuntu2_all.deb
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/main/a/apt/libapt-inst1.4_0.8.16~exp12ubuntu10.7_i386.deb
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/main/a/apt/libapt-pkg4.12_0.8.16~exp12ubuntu10.7_i386.deb
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/main/e/eglibc/libc6_2.15-0ubuntu10.2_i386.deb
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/main/libe/libept/libept1.4.12_1.0.6~exp1ubuntu1_i386.deb
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/main/g/gcc-4.6/libgcc1_4.6.3-1ubuntu5_i386.deb
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/main/g/gdk-pixbuf/libgdk-pixbuf2.0-0_2.26.1-1_i386.deb
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/main/g/glib2.0/libglib2.0-0_2.32.1-0ubuntu2_i386.deb
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/main/g/gtk+2.0/libgtk2.0-0_2.24.10-0ubuntu6_i386.deb
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/main/p/pango1.0/libpango1.0-0_1.30.0-0ubuntu2_i386.deb
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/main/g/gcc-4.6/libstdc++6_4.6.3-1ubuntu5_i386.deb
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/main/v/vte/libvte9_0.28.2-3ubuntu2_i386.deb
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/main/v/vte/libvte-common_0.28.2-3ubuntu2_all.deb
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/main/libx/libx11/libx11-6_1.4.99.1-0ubuntu2_i386.deb
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/main/x/xapian-core/libxapian22_1.2.8-1_i386.deb

```
 However most of these dependencies are already satisfied in precise, so using only the following script will also work: 
```

 #!/bin/bash
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/main/libe/libept/libept1.4.12_1.0.6~exp1ubuntu1_i386.deb
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/main/v/vte/libvte9_0.28.2-3ubuntu2_i386.deb
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/universe/s/synaptic/synaptic_0.75.9ubuntu1_i386.deb
wget -c http://glug.nith.ac.in/ubuntu/archives/pool/main/v/vte/libvte-common_0.28.2-3ubuntu2_all.deb

```
  Hope will be helpful to some...

---

### Post by cortman on 2013-03-04
> **ranjanpurbey said:**
> But for those looking for updated SYNAPTIC 0.75.9 can use following code :    


Thanks for this ranjanpurbey. :)

---

