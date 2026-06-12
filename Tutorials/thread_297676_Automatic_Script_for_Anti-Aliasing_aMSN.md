---
title: "Automatic Script for Anti-Aliasing aMSN"
date: 2006-11-11
forum: Tutorials
---

### Post by Vuen on 2006-11-11
This is a fully automated script to add anti-aliasing support to aMSN. This will compile Tcl and Tk 8.5 and recompile aMSN 0.97 for it. This will NOT replace your existing Tcl/Tk installation, so this method is much safer to use and easier to revert than other non-compilation methods. This script works on Edgy, Feisty and Gutsy, and works on both 32-bit and 64-bit processors.

Here is a screenshot of what it will look like when the script finishes:
[[IMG]http://img93.imageshack.us/img93/2881/amsnwj3.th.png[/IMG]](http://img93.imageshack.us/my.php?image=amsnwj3.png)




**[SIZE="4"]Updates[/SIZE]**

January 2, 2008:

[list][*]Updated to Tcl/Tk 8.5 and aMSN 0.97.

[*]Fixed detection of KDE on Gutsy for skin selection.

[*]Fixed checkout location for aMSN in cvs mode.[/list]
July 15, 2007:

[list][*]Updated to Tcl/Tk 8.5a6 and aMSN 0.97RC1.

[*]Added Gutsy support.[/list]
March 8, 2007:

[list][*]Added an additional warning to the clean option.[/list]
February 22, 2007:

[list][*]The script now uses its own sources.list to ensure the deb-src lines are available and to prevent any repository conflicts (uncomment fallback is now only used for unsupported distributions). This should permanently fix any repository problems.

[*]There is now a "clean" command line option to clean out Tcl/Tk 8.5 and aMSN. Only the build dependency packages are left behind, which are from the official repositories so there's no problem.

[*]The error-handling is more robust; it now catches SIGTERM and cleans temp files.[/list]
February 7, 2007:

[list][*]The cvs and tarball versions have been merged into the same script. Source tarball is now the default installation method; there is a "cvs" command line option to use cvs/subversion trunk instead.

[*]The deb-src lines in /etc/apt/sources.list are now uncommented during the script and restored afterwards. This should prevent any build-dep problems.

[*]TLS is now configured automatically (finally!)

[*]GuS-Arg's skins are now activated automatically (unless you are already using another skin.)[/list]




**[SIZE="4"]Upgrades[/SIZE]**

[COLOR="Red"]**Note for distribution upgrades:**[/COLOR] This script will not interfere with a distribution upgrade in any way. It is safe to upgrade from Edgy to Feisty or from Feisty to Gutsy with this aMSN installation. After upgrading, your aMSN may revert to using jagged fonts; simply run this script again (don't uninstall aMSN first, just run the script) to get them back.




[SIZE="4"]**Notes**[/SIZE]

[LIST]
[*]Tcl and Tk 8.5 will be compiled and installed into /usr/local; it will not replace your existing Tcl and Tk installation, so it should be much safer to use and easier to revert than other methods. 

[*]The Ubuntu and Kubuntu skins by GuS-Arg will be installed. If you do not have a skin already selected, the proper skin will be selected automatically. You can activate them manually via Account -> Select Skin.

[*]This script accepts the command line option "clean". This will remove Tcl/Tk 8.5 and purge aMSN and all configuration files and customizations (skins, extensions, options, logs, etc). If you want to revert to the normal aMSN, execute the clean and then re-install amsn from the repositories.

[*]This script can download the latest trunk of Tcl/Tk and aMSN through revision control systems instead of using source tarballs. Use it if you want to be on the bleeding edge or if the tarballs fail for some reason. To use it, add the "cvs" command line option to the script when running it.[/list]



[SIZE="4"]**Installation**[/SIZE]

Please read the entire Notes section above before installing. If you have already installed aMSN, do not uninstall it before starting.

Attached is the script. Save it in your home folder, then open a terminal window and type:
```
bash fixamsn.sh
```

You will be prompted for your root password, then the script will handle everything else. Don't be scared at the massive volume of text it will output. It should take about five to ten minutes to complete.

Please let me know if there are any errors or missing build dependencies. Enjoy!

---

### Post by DownshiftEVA on 2006-11-15
Worked like a charm, first time! All I had to do after running the script (and entering passwords) was direct AMSN to my TLS folder.

AMSN looks great now. Many thanks!

---

### Post by Vuen on 2006-11-18
Ah yes, sorry about that. I'm not sure why it can't find TLS. I spoke to the aMSN developers and they mentioned that the pkgIndex.tcl fix the script performs should let it find it, but it didn't work for me either. It's probably just due to the fact that we're installing Tcl/Tk in /usr/local. Anyway I'll add that to the main post. Thanks.

---

### Post by albatross on 2006-11-24
perfect script, saves a lot of time and effort
thank you!

---

### Post by Vuen on 2006-11-25
Glad to hear.

I added error-checking throughout the script, so now if anything goes wrong, it will abort (leaving your original aMSN intact). I also added code to automatically clean up its temporary files.

---

### Post by DyNaLk0n on 2006-11-26
Works great. Saves a lot of time. Thanks!

---

### Post by jbfrank on 2006-11-26
All I can say is a humble thank you! :D

---

### Post by Vuen on 2006-11-26
Since aMSN 0.96 has been released, I updated the script to install it instead of 0.96rc1. If aMSN is asking you whether you want to upgrade, tell it no, and simply download and run this script again.

---

### Post by iGama on 2006-11-27
Worked great, just got 2 problems, with the libpng and libjpeg that i needed to install.

---

### Post by keitarokami on 2006-11-27
ok i'll try :D

---

### Post by Vuen on 2006-11-30
> **iGama said:**
> Worked great, just got 2 problems, with the libpng and libjpeg that i needed to install.

Thanks, I added these dependencies to the script.

If anyone else finds any more missing packages, let me know.

---

### Post by bodhi.zazen on 2006-12-02
Nice How-to 



This thread has been added to the UDSF wiki.



[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by gejr on 2006-12-07
I messed up bigtime. First I installed it and everything worked fine, but I realized that I hadn't removed the old amsn installation so I got two aMSN's in my start menu. I sudo apt-get removed amsn and ran the script again. Now I got this: 

```
Logging in to :pserver:anonymous@tcl.cvs.sourceforge.net:2401/cvsroot/tcl
Fatal error, aborting.
anoncvs_tcl: no such system user
ERROR: Could not download Tcl source code.
geo@box:~/$
```

Do you know how to fix this? Thanks for your effort on making this script btw! :)

---

### Post by Vuen on 2006-12-07
> **gejr said:**
> I messed up bigtime. First I installed it and everything worked fine, but I realized that I hadn't removed the old amsn installation so I got two aMSN's in my start menu.

Hmm, that's very strange. The problem wasn't caused by not having removed aMSN; installing the old aMSN from the repository is the first thing the script does.

I'm also not sure why CVS login isn't working. It's unrelated to your original problem; it may simply be due to a connection error. I think you're just unlucky :( 

Here's a version of the script which will download tarball snapshots of the various source codes instead of downloading them through revision control systems. This way you won't get the CVS login problem, and you might find it quite a bit faster than the original script. I may replace the original script with this one if more people have problems (and will certainly replace it when a beta release of Tcl/Tk 8.5 comes out).

To completely clean everything up, run it like this:

```
sudo apt-get remove --purge amsn
sudo aptitude unhold amsn
sudo apt-get update
sudo apt-get upgrade
sudo apt-get clean
chmod 755 fixamsna5.txt
./fixamsna5.txt
```

If there are still two aMSN options in your start menu, check what they point to; the correct command is "amsn" or "/usr/bin/amsn". If they both point to the same thing, then you can simply delete one.

[COLOR="Red"][SIZE="3"]WARNING: This version of the script is deprecated. It is here for archival purposes only. Please use the newest version of the script here:[/SIZE][/COLOR]

[SIZE="2"][http://ubuntuforums.org/showthread.php?t=297676](http://ubuntuforums.org/showthread.php?t=297676)[/SIZE]


[SIZE="1"][COLOR="White"]_[/COLOR][/SIZE]

---

### Post by gejr on 2006-12-08
Thanks a lot Vuen! Worked perfectly now:)

---

### Post by mrastas on 2006-12-11
Thank You!

A very nice script indeed. 

I was having problems with the source.lists, but solved it by adding the src repos. Maybe you could add info about this in the first post, so that others "so dummy" as me get it done faster. ](*,) 

Thanks again!

---

### Post by mrashley on 2006-12-14
Thank you for making this script. You're a rock star!

For anyone else a tad blind (like me) the skins are actually findable from

Account -> skins.

It's easier than ever! :-)

---

### Post by DREMA on 2006-12-22
Nice script! Works perfectly  ;)
You could make another one that use the SVN version of aMSN.

---

### Post by Sebastral on 2006-12-23
Works until;
> A    amsn/utils/macosx/TkCximage
A    amsn/utils/macosx/TkCximage/pkgIndex.tcl
svn: REPORT request failed on '/svnroot/amsn/!svn/vcc/default'
svn: REPORT of '/svnroot/amsn/!svn/vcc/default': Could not read response body: Secure connection truncated ([https://svn.sourceforge.net](https://svn.sourceforge.net))
ERROR: Could not download aMSN source code.

---

### Post by Nizzle on 2006-12-23
](*,) 

lots of problems for me :(
really new to linux so please go easy on me lol :p 

I had amsn installed through the add/remove programs thingy at first
then amsn told me to update
and redirected me to their site..
downloaded the latest version "amsn-0.96-2.tcl84.x86.package"
installed that with the how to..
used it for a while..

I think their installer is to blame for most of my problems
first of all the "sudo apt-get remove --purge amsn" didn't work..
I think because it wasn't in the list of add/remove programs cos I installed it with their installer..
so I tried to remove it with their installer too.. no clue whether or not that worked.. it asked for my password and then nothing.. when I try again the same thing happens :(

soo.. assuming everything would work out just fine I think I've wrecked all
I just continued with the how to..
"sudo rm -r /usr/share/amsn" no errors.. 
"sudo apt-get install amsn" no errors..
"cd Desktop" figured this one out myself *yay for me lol*
"chmod 755 fixamsn.txt" no errors..
so was happy and thought it was gonna work and stuff.. :rolleyes: 
"./fixamsn.txt" NOOOOO :-s 

my ubuntu is Dutch but it says this:
```
Reading state information... Klaar
E: Uw bronnenlijst (/etc/apt/sources.list) dient minstens 1 bron-URI te bevatten
ERROR: Could not install build dependencies.
```

I believe that's the error you need to help..
if you want any more information just ask and I'll try to figure it out :mrgreen: 
please help :cry:

---

### Post by Vuen on 2006-12-24
> **Sebastral said:**
> Works until;

It seems the script is having trouble downloading the source code through Subversion. Try the snapshot version of the script here:

[http://ubuntuforums.org/showpost.php?p=1857928&postcount=14](http://ubuntuforums.org/showpost.php?p=1857928&postcount=14)

and perform all the steps in that post to clean it first. Hopefully that will fix it. I'm not at my computer now but I'll soon replace the original version of the script with this one.


> **Nizzle said:**
> my ubuntu is Dutch but it says this:
```
Reading state information... Klaar
E: Uw bronnenlijst (/etc/apt/sources.list) dient minstens 1 bron-URI te bevatten
ERROR: Could not install build dependencies.
```

It seems your sources.list is missing the source repositories; same problem as mrastas was having above. In a terminal window, type "sudo gedit /etc/apt/sources.list", and uncomment all the lines that say deb-src in front of them. Then type "sudo apt-get update", then run the script.


> **DREMA said:**
> Nice script! Works perfectly  ;)
You could make another one that use the SVN version of aMSN.

I'm more of a fan of stable releases, but if you want to use the latest source you can just check out trunk instead of the latest tag. Open up the fixamsn.txt script in any text editor, and change this:

```
svn co https://svn.sourceforge.net/svnroot/amsn/tags/Release-0_96/amsn/ amsn || ! echo "ERROR: Could not download aMSN source code." || exit 1
```

to this:

```
svn co https://svn.sourceforge.net/svnroot/amsn/trunk/amsn/ amsn || ! echo "ERROR: Could not download aMSN source code." || exit 1
```

Then run the script again.

---

### Post by Nizzle on 2006-12-24
thank you :)
got a bit further now..

still got this now.. 
```
Reading state information... Klaar
E: Kan geen bronpakket vinden voor tcl8.4
ERROR: Could not install build dependencies.
```

now what? ](*,)

---

### Post by Vuen on 2006-12-28
Hmm, that's very strange. Can you pastebin the contents of your sources.list?

[http://paste.ubuntu-nl.org](http://paste.ubuntu-nl.org)

---

### Post by s_h_a_d_o_w_s on 2006-12-28
Thansk for the script., works great! Themes are nice too!

---

### Post by supersrbin2000 on 2006-12-29
```
Please enter your sudo password:
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
amsn is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_multiverse_source_Sources - open (2 No such file or directory)
ERROR: Could not install build dependencies.

```

Does anyone have a clue? :) Btw, all src repos are uncommented.
Thanx.

---

### Post by Nizzle on 2006-12-30
> **Vuen said:**
> Hmm, that's very strange. Can you pastebin the contents of your sources.list?

[http://paste.ubuntu-nl.org](http://paste.ubuntu-nl.org)


sorry I broke my ubuntu yesterday so reinstalled it.. 
script worked now..

but keep getting this :(
[img]http://www.uploadworld.nl/users/Nizzle/uploadworld_eroorrr.jpg[/img]
then you click the OK button and it says it's loading but does nothing :(

---

### Post by iGama on 2007-01-08
Just changed the script to compile the svn insted of the 0.96 stable.

If you want to do this:

find the section:

```
  #amsn 0.96
**svn co https://svn.sourceforge.net/svnroot/amsn/tags/Release-0_96/amsn/ amsn** || ! echo "ERROR: Could not download aMSN source code." || exit 1
```

and replace with:

 ```
 #amsn 0.97 SVN
**svn co https://svn.sourceforge.net/svnroot/amsn/trunk/amsn amsn** || ! echo "ERROR: Could not download aMSN source code." || exit 1
```

Save and run :)

PS: I've mentioned this script on my blog : [www.formatds.org](www.formatds.org) :)

* Edit * 
I only noticed now that you already said this :$

---

### Post by Rackerz on 2007-01-11
Thanks, this script actually worked. Amsn installed with no trouble for once. It looks pretty too :D.

---

### Post by JohnC86 on 2007-01-12
This needs to be stickied, absolutely brilliant.

This is the first script/howto about amsn that worked flawlessly for my on x86_64

---

### Post by Th1eF` on 2007-01-18
i've got a problem here...
> Please enter your sudo password:
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
amsn is already the newest version.
The following packages were automatically installed and are no longer required:
  kdesvn-kio-plugins libapr0 libsvn0 libsvnqt2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_m_source_Sources - open (2 No such file or directory)
ERROR: Could not install build dependencies.


anyone know what is going wrong?

---

### Post by Vuen on 2007-02-07
> **supersrbin2000 said:**
> ```
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_multiverse_source_Sources - open (2 No such file or directory)
ERROR: Could not install build dependencies.

```

Does anyone have a clue? :) Btw, all src repos are uncommented.
Thanx.

> **Th1eF` said:**
> anyone know what is going wrong?

That looks like there are errors in your apt repositories. Edit the file /etc/apt/sources.list as root, and see if you can find the problem; if not, post the contents here and I'll see if I can fix it.


> **Nizzle said:**
> [img]http://www.uploadworld.nl/users/Nizzle/uploadworld_eroorrr.jpg[/img]

Unfortunately I don't recognize the language, but it seems it has a problem loading a plugin. Try deleting the folder ~/.amsn (Browse into your home, show hidden folders and delete .amsn). This will clear your aMSN settings and plugins; you might want to back it up first.


> **JohnC86 said:**
> This is the first script/howto about amsn that worked flawlessly for my on x86_64

That's good to know, I hadn't tested it on 64-bit. Thanks :)

---

### Post by hardyn on 2007-02-08
script works pretty well... im impressed...

3 questions.. 

1) getting alot of "tk has brought error" windows?
2) how do i get new tk out if i want to revert? or does it get yanked in one shot with the removal of amsn?
3) with tk now being in the "wrong" place, how do i make tkdnd work?

thanks.

---

### Post by Vuen on 2007-02-09
> **hardyn said:**
> 1) getting alot of "tk has brought error" windows?
2) how do i get new tk out if i want to revert? or does it get yanked in one shot with the removal of amsn?
3) with tk now being in the "wrong" place, how do i make tkdnd work?

1) Those happen because the version of the toolkit we're using is still in alpha testing, so it has bugs. Unfortunately there isn't a stable build out with anti-aliasing support yet, which is why we're stuck with these errors.

2) The new Tk is sitting in /usr/local, so it doesn't harm anything by being there. If you want to remove it anyway, you can remove the following files/folders:
/usr/local/bin/tclsh8.5
/usr/local/bin/wish8.5
/usr/local/include/tcl8.5/
/usr/local/lib/libtcl8.5.so
/usr/local/lib/tcl8.5/
/usr/local/lib/libtk8.5.so
/usr/local/lib/tk8.5/

3) I don't really know how you would get this to work with aMSN (or how it would be useful with aMSN), but any other Tk apps will still use the old toolkit (unless you've specifically compiled them for Tk 8.5). So if you had TkDND working before, it *should* still work with your old apps.

If it doesn't, I can take a look at it to figure out how to set it up.

---

### Post by guysmiley25 on 2007-02-10
Are there any leftover packages from compiling etc? I like to keep a nice clean system and I do this by using aptitude to insure that dependencies packages are remove etc.

I noticed during the output that apt-get installs some packages do these get removed again? If not could you please explain how I can or make/edit a script to do so.

Thanks

---

### Post by Vuen on 2007-02-10
> **guysmiley25 said:**
> Are there any leftover packages from compiling etc? I like to keep a nice clean system and I do this by using aptitude to insure that dependencies packages are remove etc.

I noticed during the output that apt-get installs some packages do these get removed again? If not could you please explain how I can or make/edit a script to do so.

Ah, unfortunately there isn't really a quick way to do that. The script uses the build-dep command in apt to install all the packages required to compile a package from source. Once you're done compiling you can remove the dependencies, but the script doesn't keep track of what it installs so the only real way to remove them is to manually remove each package. You have to dig through your log files (/var/log/dpkg*) to see what it installed and remove each package manually.

---

### Post by guysmiley25 on 2007-02-10
That's cool! just wanted to know.

Do you know if there is away to save the output from your script to a file? That would be very helpful for me to see what is happing.

By that way, thanks heap for this script in the first place! It makes amsn so much better.

Thanks

---

### Post by amr2205 on 2007-02-11
Thanks! it works and aMsn looks better.

---

### Post by guysmiley25 on 2007-02-12
I worked it out, You can use > to pipe output from a command to a file eg.

```
bash fixamsn.sh > amsn-installlog.txt
```

I then studied the file and found that you can clean up by doing:
```
sudo aptitude purge build-essential debhelper dpatch dpkg-dev g++ g++-4.1 html2text imlib11-dev libc6-dev libice-dev libjpeg62-dev libpng12-dev libsm-dev libstdc++6-4.1-dev libtiff4-dev libtiffxx0c2 libungif4-dev libx11-dev libxau-dev libxdmcp-dev libxext-dev libxt-dev linux-libc-dev tcl8.4-dev tk8.4-dev x-dev x11proto-core-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev xtrans-dev zlib1g-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libxft-dev libxrender-dev pkg-config x11proto-render-dev
```

This was on Xubuntu Edgy Eft. and could and probably be different for others.

I'm still quite new to this but I was wondering. Does amsn have to be complied because it needs to be compiled to support the beta versions of Tcl/Tk. And Tcl/Tk needs to be compiled because it's a beta version and does not have a deb file?

In this case is it not possible to make a deb of amsn that supports the beta version of Tcl/Tk and make the package to have a dependency of the beta version of Tcl/Tk and not the normal Tcl/Tk. And then make a deb for the beta Tcl/Tk

Witch would be very cool because then there could be a source for the sources.list that contains  those packages and then you could just do "sudo aptitude install amsn". And get your fixed version. Or maybe you would have to do something different like "sudo aptitude install fixamsn"  I don't know!

Just wondering...

---

### Post by Vuen on 2007-02-13
> **guysmiley25 said:**
> I'm still quite new to this but I was wondering. Does amsn have to be complied because it needs to be compiled to support the beta versions of Tcl/Tk. And Tcl/Tk needs to be compiled because it's a beta version and does not have a deb file?

In this case is it not possible to make a deb of amsn that supports the beta version of Tcl/Tk and make the package to have a dependency of the beta version of Tcl/Tk and not the normal Tcl/Tk. And then make a deb for the beta Tcl/Tk

Witch would be very cool because then there could be a source for the sources.list that contains  those packages and then you could just do "sudo aptitude install amsn". And get your fixed version.

Yep, definitely. In fact, before I wrote this script there was a thread on here that provided debs for installing the beta Tcl/Tk with aMSN. That's partly what prompted me to write this script.

Installing debs from unsigned sources is a very bad idea, especially for something that has a lot of dependencies (like a graphical toolkit). First, you don't actually know what was compiled into the deb; the maintainer could have added some malicious code. Second, debs usually install in /usr (they're supposed to, anyway); replacing your Tcl/Tk/aMSN with that of a random deb will surely break all other Tcl/Tk applications on your computer, and could damage your installation when you try to dist-upgrade. Third, debs can often be quite large. This isn't noticeable to you, but to the package maintainer, providing debs for even a small program like aMSN and the toolkit amounts to nearly ten megs, which requires a large amount of bandwidth compared to a seven kilobyte script.

So yes, you can definitely make debs for this instead of compiling, but it's dangerous. Compiling is safe, easy, straightforward, and for a small toolkit like Tcl/Tk it takes only slightly more time than installing a deb. It's better this way.

---

### Post by psynyd on 2007-02-13
Superscript!

I was having tons of newbie trouble upgrading from 0.95 to 0.96, and your script made it a breeze!

Thank you!

---

### Post by keith_21 on 2007-02-14
Hi, I'm a beginner to Linux, and I was having difficulty installing this script. I get the error 

E: You must put some 'source' URIs in your sources.list
ERROR: Could not install build dependencies.

Any ways to fix this? Thanks in advance.

---

### Post by Ghitze on 2007-02-15
Ik get the smame errro. I instaled the script once before without any trouble, and after my format en reinstall of ubuntu I get this error ..

---

### Post by Buph on 2007-02-19
Hello. I've tried to install this script, but when the installation was finishing, I've got the next error:

> Installing message catalogs
application-specific initialization failed: too many nested evaluations (infinite loop?)
too many nested evaluations (infinite loop?)
    while executing
"proc copyDir { d1 d2 } {

    puts [format {%*sCreating %s} [expr { 4 * [info level] }] {} \
              [file tail $d2]]

    file delete -force -- $d2
  ..."
    (file "/tmp/fixamsnsources/tcl/unix/../tools/installData.tcl" line 23)
make: *** [install-msgs] Error 1
ERROR: Could not compile Tcl.

I hope you can help me.
Bye!

---

### Post by Vuen on 2007-02-21
> **keith_21 said:**
> Hi, I'm a beginner to Linux, and I was having difficulty installing this script. I get the error 

E: You must put some 'source' URIs in your sources.list
ERROR: Could not install build dependencies.

Any ways to fix this? Thanks in advance.

Ah, it seems your sources.list is missing the deb-src repositories. Can you please post the contents of the file /etc/apt/sources.list? I assumed they were just commented, but if you're missing the lines altogether, I may need to modify the script to add them.




> **Buph said:**
> Hello. I've tried to install this script, but when the installation was finishing, I've got the next error:

Ooh, that's a strange one. This may be a compilation bug in Alpha 5 that has since been fixed; you can try compiling it from CVS instead. Launch the script with the cvs command-line option, like this:

```
bash fixamsn.sh cvs
```

Hopefully that will help.

---

### Post by XomboX on 2007-02-21
Hello!
I have got the same error like guyz Th1eF` and supersrbin2000.
I use Ubuntu Edgy Eft.

Here are the last few rows from console:
```
Reading state information... Done
E: Can not open file
/var/lib/apt/lists/ubuntu.beryl-project.org_dists_edgy_main-edgy_source_Sources - open (2 No such file or directory)
ERROR: Could not install build dependencies.

```

Here is my sources.list
```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://cz.archive.ubuntu.com/ubuntu edgy main restricted 
deb http://cz.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb http://security.ubuntu.com/ubuntu edgy-security main restricted

deb-src http://cz.archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://cz.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://cz.archive.ubuntu.com/ubuntu edgy universe multiverse 
deb http://cz.archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse

deb-src http://cz.archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://cz.archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb http://mirror2.ubuntulinux.nl/ edgy-seveas all
deb-src http://mirror.ubuntulinux.nl/ edgy-seveas all

# Ubuntu backports project
# GPG key: 437D05B5
deb http://cz.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://cz.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

# Upstream Wine
deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main

# bzr nightly snapshots
deb http://people.ubuntu.com/~jbailey/snapshot/bzr ./
deb-src http://people.ubuntu.com/~jbailey/snapshot/bzr ./

# Upstream Beryl nejde
# GPG key: ed8a569e
#deb http://media.blutkind.org/xgl/ edgy main-edgy 
#deb-src http://ubuntu.beryl-project.org/ edgy main-edgy

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb http://medibuntu.sos-sts.com/repo/ edgy free non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free non-free

# Canonical Commercial packages
# GPG key: 437D05B5
deb http://archive.canonical.com edgy-commercial main
deb-src http://archive.canonical.com edgy-commercial main

# Givre's repository (ntfs-3g)
deb http://givre.cabspace.com/ubuntu/ edgy main-all

# Beryl
deb http://ubuntu.beryl-project.org edgy main

# Picard
deb http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu edgy musicbrainz

```

Could you help us, please?
Thank you!!

Edit: I have found amsn_0.96+dfsg1-0ubuntu2_i386.deb (but is is for Feisty Fawn) when I try to install it says: Dependency error: libc6.
So I think we need a script for older version 0.95 of amsn which is in Edgy Eft`s repository. Am I wrong?

---

### Post by iGama on 2007-02-21
I'm going to try and update the script so it creates .deb packages :) if i succed i will share it.

---

### Post by Vuen on 2007-02-22
Alright, I updated the script to use its own sources.list, so it should fix the problems you guys are having. Give it a try and let me know if it still doesn't work.

Also, I don't recommend using the cvs option right now; the current aMSN trunk seems to segfault while starting up.

---

### Post by XomboX on 2007-02-22
> **Vuen said:**
> Alright, I updated the script to use its own sources.list, so it should fix the problems you guys are having. Give it a try and let me know if it still doesn't work.

Also, I don't recommend using the cvs option right now; the current aMSN trunk seems to segfault while starting up.

Thank you a lot, man!!! Now it works withou ANY problems, I have got 0.95 aMSN installed :guitar:

BTW: you should change the installating information from " amsn 0.96 will be installed" to "amsn version from you repository will be installed".

I wonder you know how can I add amsn icon to the up-right corner of my window border. See the screenshot.
[img]http://www.ukazto.com/img/Obrazovka-unb1.jpg[/img]

---

### Post by soulfire on 2007-02-22
I just want to point out that you HAVE TO be very careful with the new "clean" option since it removes your ~/.amsn directory, with all your options and conversation logs. 
I really don't understand why it has been inserted!!

---

### Post by darkteckno on 2007-02-22
I just got this:

svn: PROPFIND request failed on '/svnroot/amsn/trunk/amsn'
svn: PROPFIND of '/svnroot/amsn/trunk/amsn': Could not read status line: Secure connection truncated ([https://svn.sourceforge.net](https://svn.sourceforge.net))
ERROR: Could not download aMSN source code.

---

### Post by Buph on 2007-02-22
Thank you very much Vuen!!!!
It works fine now.

---

### Post by Vuen on 2007-02-22
> **XomboX said:**
> BTW: you should change the installating information from " amsn 0.96 will be installed" to "amsn version from you repository will be installed".

Actually it does install aMSN 0.96. It downloads the 0.96 tarball from SourceForge regardless of what version is in the repository. If you click on Help->About, you should see aMSN 0.96 (or 0.97 if you used the cvs option).

> **XomboX said:**
> I wonder you know how can I add amsn icon to the up-right corner of my window border. See the screenshot.

Unfortunately, that's the icon specified by the skin used. The GuS-Arg skins used are the nicest ones I could find; you can modify it to add the icon yourself, or you can look for other skins here:

[http://amsn-project.net/skins.php](http://amsn-project.net/skins.php)

> **soulfire said:**
> I just want to point out that you HAVE TO be very careful with the new "clean" option since it removes your ~/.amsn directory, with all your options and conversation logs. 
I really don't understand why it has been inserted!!

This option is there to ensure that aMSN is completely clean, to remove any customizations or configuration options that may be preventing the install from taking place. The idea is to remove every trace of aMSN and Tcl/Tk 8.5 from your system.

> **darkteckno said:**
> svn: PROPFIND request failed on '/svnroot/amsn/trunk/amsn'
svn: PROPFIND of '/svnroot/amsn/trunk/amsn': Could not read status line: Secure connection truncated ([https://svn.sourceforge.net](https://svn.sourceforge.net))
ERROR: Could not download aMSN source code.

It seems the aMSN subversion repository is having some problems. Try running the script without the cvs option.

---

### Post by darkteckno on 2007-02-22
Thanks its sorted now!

---

### Post by XomboX on 2007-02-22
[quote="Vuen"]Actually it does install aMSN 0.96. It downloads the 0.96 tarball from SourceForge regardless of what version is in the repository. If you click on Help->About, you should see aMSN 0.96 (or 0.97 if you used the cvs option).[/quote]

I checked it out and you are right. However in synaptic there is 0.95 amsn.

[quote="Vuen"]Unfortunately, that's the icon specified by the skin used. The GuS-Arg skins used are the nicest ones I could find; you can modify it to add the icon yourself, or you can look for other skins here:
[/quote]
I tried few more skins and there is still no icon :-/ I need to know where is defined which icon is shown there, then I can fix it.

Thank you for your quick answers, Vuen.

---

### Post by sfagmenos on 2007-02-22
Good eveninig i am new in using linux and i tried to have aMSN installed 
by this script but i have the foolowing error

first i get this message
Your distribution is not supported by this script.
Press enter to proceed anyway, or CTRL+C to cancel.

and when i hit enter i have finnally this 
ERROR: Could not install build dependencies.

i have installed ubuntu 6.06 and installed it in my native language which is grrek
have anything to do with the error the different language ??

i don't know what to blame for this :confused: 
any help ??

---

### Post by SSamiK on 2007-02-23
Hi, and thanks for a really great script! I've used it several times with great success, however; 
this time around a error occur:

"bash fixamsn.sh cvs" ends with: 

/tmp/fixamsnsources/tk/unix/../generic/tkTextBTree.c:1816: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;register&#8217;
make: *** [tkTextBTree.o] Error 1
ERROR: Could not compile Tk.



Any hints how to fix it?

Edit: Editet the script to use amsn svn instead of 0.96, and it worked like a charm.

---

### Post by Marsan on 2007-02-23
works like a charm on first try!

---

### Post by Th1eF` on 2007-02-25
great...thanks a lot. works like a harm

---

### Post by gaspar on 2007-02-26
It works great for me, but seems amsn is eating too much CPU. Every time the notifier pops up, or someone opens a chat window (including myself), or if I type big sentences, it freezes for some time, for every action. Worst when everything happens at the same time. I noticed my CPU usage goes 98%, something that does not happen if I install the latest autopackage from the website.
So, I tried to find those TCL/TK beta packages, provided by a guy named neto, I think... but the packages aren´t there anymore. 
So, any clue where can I get those packages, and then install the autopackage file? 
Thnx!

---

### Post by mied87 on 2007-02-28
Oh, i tried several things to get amsn worked, and your script totaly rocked!
Now its running fine! 

Im new at linux and still i made it with your script and guide! 
Thanks, youre the man! :popcorn:

---

### Post by cbudden on 2007-02-28
Why on earth does the clean option remove your ~/.amsn directory without asking the user first!  I have now lost a handful of plugins, conversation logs!

---

### Post by Princey on 2007-03-01
Just wanted to say thanks for the script. I compiled it already but took your easy way out after I reformatted. Thanks much.

---

### Post by Icarus3000 on 2007-03-01
I can't install this script.  When I run it, I get the error below, and aMSN looks ugly.
```
libpng12-dev is already the newest version.
Note, selecting libjpeg62-dev instead of libjpeg-dev
libjpeg62-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxft-dev: Depends: libxft2 (= 2.1.10-1ubuntu1) but 2.1.10-1ubuntu1+turner1e is to be installed
              Depends: libfontconfig1-dev but it is not going to be installed
              Depends: libfreetype6-dev but it is not going to be installed
E: Broken packages
ERROR: Could not install build dependencies.

```

Does anyone have a suggestion on how I can fix these errors?

Thanks!
Icarus3000

---

### Post by Princey on 2007-03-01
> **Icarus3000 said:**
> 

Does anyone have a suggestion on how I can fix these errors?

Thanks!
Icarus3000


Try ```
sudo apt-get install -f
```

That should fix the broken dependencies.

---

### Post by Icarus3000 on 2007-03-02
> **Princey said:**
> Try ```
sudo apt-get install -f
```

That should fix the broken dependencies.

That worked, thanks!

---

### Post by Princey on 2007-03-02
> **Icarus3000 said:**
> That worked, thanks!


You're welcome. Anytime you run into broken dependences, just type in that same command that it will resolve it for you.

---

### Post by SnakeEyz on 2007-03-07
AMsn looks so much better now.

Many thanks for this

---

### Post by siralphred on 2007-03-07
worked perfectly for me...using edgy, on hp pavilion dv6000

---

### Post by mrgnash on 2007-03-08
Thanks, the script worked flawlessly! :D

---

### Post by Vuen on 2007-03-08
> **sfagmenos said:**
> Your distribution is not supported by this script.
Press enter to proceed anyway, or CTRL+C to cancel.

This script doesn't support Dapper (6.06); it only supports Edgy and Feisty. You can try these instead:

[http://ubuntuforums.org/showthread.php?t=325689](http://ubuntuforums.org/showthread.php?t=325689)
[http://ubuntuforums.org/showthread.php?t=216689](http://ubuntuforums.org/showthread.php?t=216689)



> **gaspar said:**
> It works great for me, but seems amsn is eating too much CPU. Every time the notifier pops up, or someone opens a chat window (including myself), or if I type big sentences, it freezes for some time, for every action. Worst when everything happens at the same time. I noticed my CPU usage goes 98%, something that does not happen if I install the latest autopackage from the website.

Hm, that's very strange. Are you running the stable version 0.96, or the latest source code trunk? If you ran the script with the cvs option, try running it without; the stable aMSN shouldn't have any memory leaks.



> **cbudden said:**
> Why on earth does the clean option remove your ~/.amsn directory without asking the user first!  I have now lost a handful of plugins, conversation logs!

Sorry about your lost data, but the notes section explaining the clean option clearly stated that it would clear all plugins, logs, and any other customized data. The script even explicitely kills any active sudo session to force you to re-enter your password so that you don't do it by accident. The clean option should only be used if aMSN doesn't work; it removes ~/.amsn to prevent damaged config files or plugins from crashing it.

I've added an additional warning to the script to try to prevent people from doing it without knowing the risks.

---

### Post by Duncan_Idaho on 2007-03-08
thak you so much for the scrip, it worked flawlessly and now I got a way MUCH beutyfull aMSN
but I got a doubt
when I use amsn it has the ugly 'MSN sounds' instead of the amsn original sounds, how can I get 'em back?

---

### Post by kybuz on 2007-03-12
thanks...what a difference !!!

---

### Post by herbster on 2007-03-15
I get this after installing:

```
amsnbobby@bobby-ubuntu:~$ amsn
Error in startup script: error copying "langlist" to "/home/bobby/.amsn/langlist.xml": permission denied
    while executing
"file copy -force "langlist" "$filename""
    (procedure "::lang::LoadVersions" line 20)
    invoked from within
"::lang::LoadVersions    "
    (procedure "scan_languages" line 6)
    invoked from within
"scan_languages"
    invoked from within
"if { $initialize_amsn == 1 } {
        ###############################################################
        create_dir $HOME
        create_dir $HOME/plugins
        create_di..."
    (file "config.tcl" line 1471)
    invoked from within
"source config.tcl      "
    ("uplevel" body line 23)
    invoked from within
"uplevel \#0 {

        source ctthemes.tcl
        source progressbar.tcl  ;# Progressbar Megawidget
        source migmd5.tcl
        source des.tcl          ;# DES encryption
        source s..."
    (procedure "reload_files" line 2)
    invoked from within
"reload_files"
    (file "/usr/bin/amsn" line 237)
bobby@bobby-ubuntu:~$ 
```

Help? Hehe.

---

### Post by nero666 on 2007-03-16
thanks man, worked flawless

---

### Post by zeny on 2007-03-18
Herbster if you do sudo amsn in console it should work it needs to be run as root, so really you just gotta change the permissions on the file, MSN me ill tell you how 

Mr ;)

---

### Post by Arlanthir on 2007-03-18
I have a question or two about this.. When a new amsn comes out, will we be able to update it?
Also, when installing the script, if there's a newer release, will we have to download another version of the script itself?

Thank you very much for this, worked like a charm! :D

---

### Post by herbster on 2007-03-18
zeny,

Thanks for your help, that worked :)

---

### Post by SkiesOfAzel on 2007-03-19
When the script tries to configure tcl i get this :

checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
ERROR: Could not compile Tcl.

Gcc 4.0 and 4.1 are already installed btw. The bin names (inside /usr/bin) are gcc-4.0 and gcc-4.1 respectively so i added a symbolic link of 4.1 named gcc to see what would happen :

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
ERROR: Could not compile Tcl.

What am i doing wrong?

---

### Post by Neo40 on 2007-03-19
I'm running Feisty with the latest update and when I run the script, ,I get these errors:
```
la distribution unstable, que certains paquets n'ont pas encore
été créés ou ne sont pas sortis d'Incoming.
L'information suivante devrait vous aider à résoudre la situation : 

Les paquets suivants contiennent des dépendances non satisfaites :
  libxft-dev: Dépend: libxft2 (= 2.1.12-1) mais 2.1.12-1+turner2 devra être installé
              Dépend: libfontconfig1-dev mais ne sera pas installé
              Dépend: libfreetype6-dev mais ne sera pas installé
E: Paquets défectueux
ERROR: Could not install build dependencies.
```

I tried the command ```
sudo apt-get install -f
```
but didn't help. Any idea?
Thanks

---

### Post by Princey on 2007-03-20
You have to install build essential first.

---

### Post by buildid on 2007-04-01
does the cvs version work with this script ? because i cannot login when i install the cvs version further great script...........

---

### Post by mrastas on 2007-04-02
Hi,

and thanks for a very nice script. One question thou. Lately i have noticed the following when trying to upgrade via aptitude upgrade.

```
aptitude upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  amsn
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
```

Is there a way to make this better, so that i would have a clean output (ie. no kept backs or upgrades)?

---

### Post by domino on 2007-04-04
I Love the script! Almost as easy as restarting the machine. This also works on Feisty and Dapper with both x86 PC and Mac PowerBook.

Thanks!

---

### Post by WhosRodney on 2007-04-06
Hi Vuen,
Thanks for the script.  It works perfectly.

I'm wondering how I would uninstall the components installed by the script.  Are the libraries installed via apt-get?  Is amsn installed via apt-get.  I looked through the script, but having limited scripting knowledge, I couldn't figure out exactly how everything worked.

Thanks

---

### Post by Dropknee on 2007-04-07
I got a problem,, the script work great, but I install de CVS version and dont know why, but everytime I quit Amsn, I lost all my setting, and I need to set all again, any clue about this?

thx

---

### Post by Dropknee on 2007-04-07
ok Fix it, I just use the clean command and reinstalling again and now work and all the setting keep in place.

---

### Post by Dropknee on 2007-04-09
I got another problem, when I use the CVS version, dont know why but the Voice clip feature dont work, this show something like can´t find The Snack library.

---

### Post by splitsch on 2007-04-13
Hello!
I translated this script in French (only the output, not the author comments).
For those interrested:
[http://www.pastanque.be/splitsch/ubuntu/104/rendre-amsn-beau.html](http://www.pastanque.be/splitsch/ubuntu/104/rendre-amsn-beau.html)
Please, don't hésitate to help the translation.
Vuen, feel free to make a link from the original post to the article there.

Thanks

---

### Post by daemonicus on 2007-04-17
does it work in debian etch??? it works like charm in Ubuntu but i have 1 more machine.Should i test it 
????

---

### Post by dregin on 2007-04-18
Just used this with CVS version and edgy and it worked perfectly.

Thanks a million :)

---

### Post by Kwunman on 2007-04-21
Hey,

Would just like to thank and congratulate you on making such a useful script.

Works perfectly and I now have a decent looking amsn!

Thanks again

Kwun-man

---

### Post by Marsan on 2007-04-21
Very nice script! The one thing i did wrong was to sudo the script..i had to go into the /home/user/.amsn/ - folder to make the rights to the user to make it work properly. BTW im in feisty, works like it did in edgy.

---

### Post by Arlanthir on 2007-04-21
Confirmed, works 100% in feisty too =)
(btw, feisty rocks ma sox!)

---

### Post by Poka64 on 2007-04-21
How do I change the script so it compiles the latest trunk?

Edit: I should have read the first post....

---

### Post by GoBieN on 2007-04-22
Normal mode fails for me on feisty:
> ...
Installing libtclstub8.5.a to /usr/local/lib/
Installing time zone data
application-specific initialization failed: too many nested evaluations (infinite loop?)
too many nested evaluations (infinite loop?)
    while executing
"proc copyDir { d1 d2 } {

    puts [format {%*sCreating %s} [expr { 4 * [info level] }] {} \
              [file tail $d2]]

    file delete -force -- $d2
  ..."
    (file "/tmp/fixamsn.13076/tcl/unix/../tools/installData.tcl" line 23)
make: *** [install-tzdata] Fout 1
ERROR: Could not compile Tcl.

Now trying CVS

edit: CVS worked !

---

### Post by Bendill on 2007-04-22
Greetings, 

I found your script through google and considering the comments it's promising, but I'm having some trouble.

```
Reading state information... Done
libpng12-dev is already the newest version.
libpng12-dev set to manual installed.
Note, selecting libjpeg62-dev instead of libjpeg-dev
libjpeg62-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxft-dev: Depends: libxft2 (= 2.1.12-1) but 2.1.12-1+turner4 is to be installed
              Depends: libfontconfig1-dev but it is not going to be installed
              Depends: libfreetype6-dev but it is not going to be installed
E: Broken packages
ERROR: Could not install build dependencies.

```

I've tried most of what has been reccomended in the thread but to no avail...
Any suggestions?

EDIT: Found out that the packages from the subpixel font rendering fix I used ( [http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670) ) are conflicting with packages that are being installed with the script.

EDIT2: FIXED! Fault caused by a "dirty" aptitude, cleaned it up and it worked like a charm!

---

### Post by amr2205 on 2007-04-23
Thanks a lot! I've update my aMSN to 0.97 and works great! (a little bit slow when login in, but almost all MSN Messenger features work.) The integration with Gnome it's really good. Nice work!

---

### Post by Plauge on 2007-04-24
Great script. Makes me happy when others do the thinking ;)

---

### Post by Princey on 2007-04-24
Just wanted to know, does the fiesty version of amsn has anti anliasing? My eyes may be fooling mee.

---

### Post by Arlanthir on 2007-04-25
Actually, I installed the script without even confirming amsn was still ugly =X Well, maybe next time!

---

### Post by GoBieN on 2007-04-25
> **Princey said:**
> Just wanted to know, does the fiesty version of amsn has anti anliasing? My eyes may be fooling mee.

Hmm didn't try the official repo version, but the version that automatix installed was still ugly as hell.

---

### Post by Arlanthir on 2007-04-25
I think the problem is with the Tcl/Tk version and not with amsn, correct me if I'm wrong.
So, the important thing to update would be Tcl/Tk. Let's hope for the beta to become stable and released =)

---

### Post by Princey on 2007-04-25
> **GoBieN said:**
> Hmm didn't try the official repo version, but the version that automatix installed was still ugly as hell.

Automatix installs 0.95. The one I'm talking about is in the add/remove programs section and it installs 0.96

---

### Post by borahshadow on 2007-04-25
it does not look ugly to me but I don't know (possibly my small resolution makes it look better or dows everyone use close to 1600X1200) right now i believe i'm one setp down because i have to sit far away from my monitor)

---

### Post by lcohen999 on 2007-04-28
> **Bendill said:**
> Greetings, 

I found your script through google and considering the comments it's promising, but I'm having some trouble.

```
Reading state information... Done
libpng12-dev is already the newest version.
libpng12-dev set to manual installed.
Note, selecting libjpeg62-dev instead of libjpeg-dev
libjpeg62-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxft-dev: Depends: libxft2 (= 2.1.12-1) but 2.1.12-1+turner4 is to be installed
              Depends: libfontconfig1-dev but it is not going to be installed
              Depends: libfreetype6-dev but it is not going to be installed
E: Broken packages
ERROR: Could not install build dependencies.

```

I've tried most of what has been reccomended in the thread but to no avail...
Any suggestions?

EDIT: Found out that the packages from the subpixel font rendering fix I used ( [http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670) ) are conflicting with packages that are being installed with the script.

EDIT2: FIXED! Fault caused by a "dirty" aptitude, cleaned it up and it worked like a charm!

I have the same issue, how did you fix this?

---

### Post by embeemb on 2007-04-30
This will probably come across as a very dumb question, but here goes anyway.

I'm using aMSN 0.97b currently on dapper. Will this script make it prettier still? I love aMSN but fonts are not to great still :/

Thanks anyway..

---

### Post by ==[ VNMS1 ]== on 2007-05-01
Oh wow! Hey thanks. I was about to lose my noob mind over the whole dependency trees that aMSN seemed to need and the fact that half the libs wouldn't compile properly. After using your script and watching it work, I'm happy to report a fully functioning aMSN. Thanks heaps for that.
:popcorn:

---

### Post by embeemb on 2007-05-01
Works like a charm !! Thanks a bunch ! It downgraded aMSN to 0.96 but I LOVE the pretty pretty pretty fonts !!

---

### Post by magomago on 2007-05-03
getting TLS problems...i actually tried to install manually earlier and go through plenty of crap to fix it over at the amsn forums but i couldn't figure it out

i came here and found this

i installed normally...and got .96 and it was nice

i did it again for CVS and it worked....

but it complains about doing TLS alllllllll over again - I was able to compile it that far and get stuck at this...

anyone know how to fix thios?  I'm afraid the crap i did earlier trying to figure out .97b from the amsn forums might have messed with things...is there a way to simply remove anythhing of or related to tls and reinstall it all?  Or does the script just resinstall it all anyways?

---

### Post by patrickfromspain on 2007-05-03
for tls problem, try to install libssl0.9.7

---

### Post by Neo40 on 2007-05-04
> **lcohen999 said:**
> I have the same issue, how did you fix this?

> **Bendill said:**
> Greetings, 

I found your script through google and considering the comments it's promising, but I'm having some trouble.

```
Reading state information... Done
libpng12-dev is already the newest version.
libpng12-dev set to manual installed.
Note, selecting libjpeg62-dev instead of libjpeg-dev
libjpeg62-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxft-dev: Depends: libxft2 (= 2.1.12-1) but 2.1.12-1+turner4 is to be installed
              Depends: libfontconfig1-dev but it is not going to be installed
              Depends: libfreetype6-dev but it is not going to be installed
E: Broken packages
ERROR: Could not install build dependencies.

```

I've tried most of what has been reccomended in the thread but to no avail...
Any suggestions?

EDIT: Found out that the packages from the subpixel font rendering fix I used ( [http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670) ) are conflicting with packages that are being installed with the script.

EDIT2: FIXED! Fault caused by a "dirty" aptitude, cleaned it up and it worked like a charm!

Same problem here. I tried 
```
sudo aptitude clean
```
But doesnt work. I use the packages from the subpixel font rendering fix.

---

### Post by Tigge on 2007-05-08
Yes the TLS issue is due to changes in the new version of Tcl/Tk. This problem can be solved by dowloading the source and built it yourself. This should be added to the script I think.

So.. download and build with:

./configure --with-tcl=/usr/local/lib --with-ssl-dir=/usr/
make

Copy:

* libtls1.50.so
* pkgIndex.tcl
* tls.tcl 

To:

 ~/.amsn/plugins/tls1.50

And everything should run smoothly again. This is only needed for the CVS version.

---

### Post by Duncan_Idaho on 2007-05-08
I asked this before, but nobody answer me =/
how do I change the sounds?
I mean I'd like to have the original aMSN's sounds instead of the windoze-MSN sounds
I liked more the first :confused: 
other than that, the script worked flawless

---

### Post by Lestat18th on 2007-05-13
Simply Awesome Thanks! and it LOOKS great!

---

### Post by Footissimo on 2007-05-13
To those who are having problems with the turner patch repo's and this script then there is an easy way around the problem...

Just remove the turner patch repos from /etc/apt/sources.list temporarily, do a sudo apt-get update, force the downgrade of libxft2, libfreetype6 and libcairo2 from the turner patch versions to the normal feisty versions (I was lazy and just used synaptic -> packages->force downgrade).  Apply this script as per instructions, then add the turner patch repos again and sudo apt-get update  and upgrade those three packages again =)

---

### Post by [ITA]ArgH on 2007-05-16
Thank you very much!! Now it looks soooo good:guitar:

---

### Post by pickarooney on 2007-05-19
This is one of the most beautiful things I've ever downloaded. How I hated the ugly fonts of AMSN and how I tore my hair out trying to fix them. 

Thank you!

---

### Post by splitsch on 2007-05-20
Hello!
One of my readers submited this bug report:

—————- diff Start ———————

— beau_amsn.sh-ori 2007-05-20 12:17:57.000000000 +0200
+++ beau_amsn.sh 2007-05-19 21:34:12.000000000 +0200
@@ -37,19 +37,18 @@
APTOPTIONS=”–assume-yes –option Dir::Etc::SourceList=$TEMPDIR/sources.list”

-function clean_up {
+clean_up() {
EXITVAL=$?
rm -rf $TEMPDIR
exit $EXITVAL
}

-function error_exit
-{
+error_exit(){
echo “ERREUR: $1&#8243; 1>&2
clean_up
}

-trap clean_up SIGHUP SIGINT SIGTERM
+trap clean_up HUP INT TERM

#vérifie si l’option “clean” est entrée
if [ “$1&#8243; = “clean” ]; then

———— diff end —————————-

I'm not a great coder ;) I don't know what it means, but maybe it could help some people who has trouble to install it !

Thanks

---

### Post by psychok7 on 2007-05-20
how do i remove EVERYTHING???

---

### Post by Princey on 2007-05-20
I must say the new svn version works well and looks much better than previous releases and used this script to install the new version.

---

### Post by Vinnah on 2007-05-23
I seem to get this error upon starting the latest version of AMSN when using the lastest release (Via the CVS on the script)

```

vince@vince-desktop:~$ amsn
Error in startup script: extra characters after close-brace
    while executing
"set command [list  $self  {expand}$Snit_optionInfo(configure-$option)  $option]
            "
    (procedure "snit::RT.CacheConfigureCommand" line 36)
    invoked from within
"snit::RT.CacheConfigureCommand  $type $selfns $win $self $option"
    (procedure "::snit::RT.method.configurelist" line 7)
    invoked from within
"::snit::RT.method.configurelist $type $selfns $win $self $args"
    (procedure "::snit::RT.method.configure" line 4)
    invoked from within
"$self configure -width $arrow1width"
    (procedure "::pixmapscrollbar::Snit_constructor" line 154)
    invoked from within
"::pixmapscrollbar::Snit_constructor ::pixmapscrollbar ::pixmapscrollbar::Snit_inst1 .plugins_log.ys .plugins_log.ys -command {.plugins_log.info yview}"
    ("eval" body line 1)
    invoked from within
"eval [linsert $arglist 0  ${type}::Snit_constructor $type $selfns $instance $instance]"
    (procedure "RT.ConstructInstance" line 9)
    invoked from within
"RT.ConstructInstance $type $selfns $name $args"
    (procedure "::snit::RT.widget.typemethod.create" line 53)
    invoked from within
"scrollbar $window.ys -command "$window.info yview""
    (procedure "::pluginslog::draw" line 12)
    invoked from within
"::pluginslog::draw"
    invoked from within
"if { $initialize_amsn == 1 } {
     ::pluginslog::draw
}"
    (file "pluginslog.tcl" line 210)
    invoked from within
"source pluginslog.tcl"
    ("uplevel" body line 27)
    invoked from within
"uplevel \#0 {

        # amsncore.tcl is already loaded but we'll re-source it here in case we manually do reload_files
        source amsncore.tcl
        source audio.tc..."
    (procedure "reload_files" line 2)
    invoked from within
"reload_files"
    (file "/usr/bin/amsn" line 250)
```

---

### Post by yachi on 2007-05-23
> **Vinnah said:**
> I seem to get this error upon starting the latest version of AMSN when using the lastest release (Via the CVS on the script)

```

vince@vince-desktop:~$ amsn
Error in startup script: extra characters after close-brace
    while executing
"set command [list  $self  {expand}$Snit_optionInfo(configure-$option)  $option]
            "
    (procedure "snit::RT.CacheConfigureCommand" line 36)
    invoked from within
"snit::RT.CacheConfigureCommand  $type $selfns $win $self $option"
    (procedure "::snit::RT.method.configurelist" line 7)
    invoked from within
"::snit::RT.method.configurelist $type $selfns $win $self $args"
    (procedure "::snit::RT.method.configure" line 4)
    invoked from within
"$self configure -width $arrow1width"
    (procedure "::pixmapscrollbar::Snit_constructor" line 154)
    invoked from within
"::pixmapscrollbar::Snit_constructor ::pixmapscrollbar ::pixmapscrollbar::Snit_inst1 .plugins_log.ys .plugins_log.ys -command {.plugins_log.info yview}"
    ("eval" body line 1)
    invoked from within
"eval [linsert $arglist 0  ${type}::Snit_constructor $type $selfns $instance $instance]"
    (procedure "RT.ConstructInstance" line 9)
    invoked from within
"RT.ConstructInstance $type $selfns $name $args"
    (procedure "::snit::RT.widget.typemethod.create" line 53)
    invoked from within
"scrollbar $window.ys -command "$window.info yview""
    (procedure "::pluginslog::draw" line 12)
    invoked from within
"::pluginslog::draw"
    invoked from within
"if { $initialize_amsn == 1 } {
     ::pluginslog::draw
}"
    (file "pluginslog.tcl" line 210)
    invoked from within
"source pluginslog.tcl"
    ("uplevel" body line 27)
    invoked from within
"uplevel \#0 {

        # amsncore.tcl is already loaded but we'll re-source it here in case we manually do reload_files
        source amsncore.tcl
        source audio.tc..."
    (procedure "reload_files" line 2)
    invoked from within
"reload_files"
    (file "/usr/bin/amsn" line 250)
```

the script worked great before :D, but  i get this error now too...

---

### Post by iBART on 2007-05-25
> **psychok7 said:**
> how do i remove EVERYTHING???

quote. i wanna do it to

---

### Post by iBART on 2007-05-26
> **iBART said:**
> quote. i wanna do it to

up?

---

### Post by IppatsuMan on 2007-05-26
> **Vinnah said:**
> I seem to get this error upon starting the latest version of AMSN when using the lastest release (Via the CVS on the script)


It's due to an issue with tcl/tk 8.5a6 and previous versions (see [http://amsn-project.net/forums/viewtopic.php?t=3366]("http://amsn-project.net/forums/viewtopic.php?t=3366") for references). You need to use the CVS version of tcl/tk to use the svn version of aMSN, or if you don't want to update tcl/tk (which anyway fixes some nasty memory leaks), you can use the svn version revision 8757.

---

### Post by davo8 on 2007-05-27
Great mod bro!!!! Looks sweet as.

Big thnx to u from Teh Lin'hux Brovas!!!!!!!

---

### Post by Sycrat on 2007-05-27
Yeah mate, thanks.
It looks awesome, my 56k connection took a while... but it was worth it :).
Thanks from Sycrat/Azzdawg of Teh Lin'hux Brova's

~Sycrat@ONYX

---

### Post by iGama on 2007-05-28
Tcl/Tk 8.5a6 was released, you can update your script :)

---

### Post by morristhecat on 2007-05-29
How do I reverse the script. I mean uninstall and undo everything it installed and did to the system... please... I think it messed up many of my gnome configuration... thanx a lot...

---

### Post by loathsome on 2007-05-30
Hi,

How do I completely remove aMSN + all the files that this script creates?
Thanks.

---

### Post by loathsome on 2007-05-30
> **loathsome said:**
> Hi,

How do I completely remove aMSN + all the files that this script creates?
Thanks.

After a bit of research, it seems like the script has an «clean» option which works flawlessly. Just run ```
# ./script.sh clean
``` (as root)

Thanks for a great script! 

loathsome :KS

---

### Post by capink on 2007-06-02
Thank you Vuen for the great script.

I have one suggestion: instead of creating the file ~/.amsn/tclconfig fo every user on the system I tried to change the /usr/bin/amsn using the following command:

```
sudo sed --in-place 's_set libtls ""_set libtls "/usr/lib/tls1.50"_' /usr/bin/amsn
```

It worked for me and I think this maybe useful in multiuser system. Just thought to tell you if you want to test it and include it in your script.

---

### Post by Nevodeon on 2007-06-25
works fine, looks beautiful, one little problem tho..
when I wanna do those voice clips, it doesn't work 'cuz I need some kind of Snack-library or something.. where can I get that, how can I get it, and how do I install it


I thank you very muts ;)



edit; another little problem.. pc's quite slow now.. and so is amsn.. Is this a "Reboot-and-problem-solved-problem" or do I have to use terminals... or is this just a bug, which can only be solved by destroying my pc (A)

---

### Post by Nevodeon on 2007-06-25
anyone?

---

### Post by DerkStenv on 2007-06-27
When I enter the TLS installation path in aMSN Preferences, it still can't find the installation. What is the exact path I should fill in?

Edit: **Nevermind. Thanks for the great script!**

---

### Post by Skrezium on 2007-06-28
Woah. This is great! 

Thank you so much, this script is truly amazing - simple and quick! =D

---

### Post by clikc on 2007-06-29
even after running all of vuen's code in Term i'm still getting the same window 


[http://i52.photobucket.com/albums/g20/spartakus_42/Screenshot.png](http://i52.photobucket.com/albums/g20/spartakus_42/Screenshot.png)


now i relise its saying to install the TLS packet,  but it wont install, threw that screen or if i go to the website and download/install said packet.


help?

---

### Post by beat on 2007-07-13
[https://svn.sourceforge.net/svnroot/amsn/trunk/amsn/](https://svn.sourceforge.net/svnroot/amsn/trunk/amsn/) is not working, therefore the cvs install won't work.

If you want the script to work with cvs replace the line 'svn co [https://svn.sourceforge.net/svnroot/amsn/trunk/amsn/](https://svn.sourceforge.net/svnroot/amsn/trunk/amsn/) amsn || error_exit "Could not download aMSN source code."' with 

'svn co [https://amsn.svn.sourceforge.net/svnroot/amsn/trunk/amsn/](https://amsn.svn.sourceforge.net/svnroot/amsn/trunk/amsn/) amsn || error_exit "Could not download aMSN source code."'

---

### Post by VortaX on 2007-07-13
Thanks beat ;D

---

### Post by Princey on 2007-07-17
> **beat said:**
> [https://svn.sourceforge.net/svnroot/amsn/trunk/amsn/](https://svn.sourceforge.net/svnroot/amsn/trunk/amsn/) is not working, therefore the cvs install won't work.

If you want the script to work with cvs replace the line 'svn co [https://svn.sourceforge.net/svnroot/amsn/trunk/amsn/](https://svn.sourceforge.net/svnroot/amsn/trunk/amsn/) amsn || error_exit "Could not download aMSN source code."' with 

'svn co [https://amsn.svn.sourceforge.net/svnroot/amsn/trunk/amsn/](https://amsn.svn.sourceforge.net/svnroot/amsn/trunk/amsn/) amsn || error_exit "Could not download aMSN source code."'


Still fails with the following message:

svn: PROPFIND request failed on '/svn...sn/trunk/amsn'
svn: PROPFIND of '/svn...sn/trunk/amsn': 405 Method Not Allowed ([https://amsn.svn.sourceforge.net](https://amsn.svn.sourceforge.net))

Update: changed the line to read instead > svn co [https://amsn.svn.sourceforge.net/svnroot/amsn/trunk/amsn//](https://amsn.svn.sourceforge.net/svnroot/amsn/trunk/amsn//) || error_exit "Could not download aMSN source code." worked then.

---

### Post by kaminix on 2007-07-17
This is my output:
```
alex@hasokon:~$ sudo bash fixamsn.sh

Installing aMSN with Anti-Aliasing support.
 -- Source tarball mode: Tcl/Tk 8.5a6 and aMSN 0.97RC1 will be installed.

Please enter your sudo password:
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Hit http://security.ubuntu.com feisty-security/main Packages
Get:2 http://archive.ubuntu.com feisty Release.gpg [191B]
Ign http://archive.ubuntu.com feisty/main Translation-en_US
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Ign http://archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://archive.ubuntu.com feisty/universe Translation-en_US
Ign http://archive.ubuntu.com feisty/multiverse Translation-en_US
Get:3 http://archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_US
Get:4 http://archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Hit http://archive.ubuntu.com feisty Release
Hit http://archive.ubuntu.com feisty-updates Release
Hit http://archive.ubuntu.com feisty-backports Release
Hit http://archive.ubuntu.com feisty/main Packages
Hit http://archive.ubuntu.com feisty/restricted Packages
Ign http://archive.ubuntu.com feisty/universe Packages
Hit http://archive.ubuntu.com feisty/multiverse Packages
Ign http://archive.ubuntu.com feisty/main Sources
Hit http://archive.ubuntu.com feisty/restricted Sources
Hit http://archive.ubuntu.com feisty/universe Sources
Hit http://archive.ubuntu.com feisty/multiverse Sources
Hit http://archive.ubuntu.com feisty-updates/main Packages
Hit http://archive.ubuntu.com feisty-updates/restricted Packages
Hit http://archive.ubuntu.com feisty-updates/universe Packages
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://archive.ubuntu.com feisty-updates/main Sources
Hit http://archive.ubuntu.com feisty-updates/restricted Sources
Hit http://archive.ubuntu.com feisty-updates/universe Sources
Hit http://archive.ubuntu.com feisty-updates/multiverse Sources
Hit http://archive.ubuntu.com feisty-backports/main Packages
Hit http://archive.ubuntu.com feisty-backports/restricted Packages
Hit http://archive.ubuntu.com feisty-backports/universe Packages
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://archive.ubuntu.com feisty-backports/main Sources
Hit http://archive.ubuntu.com feisty-backports/restricted Sources
Hit http://archive.ubuntu.com feisty-backports/universe Sources
Hit http://archive.ubuntu.com feisty-backports/multiverse Sources
Get:5 http://archive.ubuntu.com feisty/universe Packages [4912kB]
Get:6 http://archive.ubuntu.com feisty/main Sources [385kB]
99% [5 Packages gzip 0]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com feisty/universe Packages
  Sub-process gzip returned an error code (1)
99% [6 Sources gzip 0]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com feisty/main Sources
  Sub-process gzip returned an error code (1)
Fetched 6B in 2s (2B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree
Reading state information... Done
amsn is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_source_Sources - open (2 No such file or directory)
ERROR: Could not install build dependencies.
```

Any ideas? The /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_source_Sources - open part seems kind of strange...

---

### Post by Entwine on 2007-07-25
> **kaminix said:**
> This is my output:
```
alex@hasokon:~$ sudo bash fixamsn.sh

Installing aMSN with Anti-Aliasing support.
 -- Source tarball mode: Tcl/Tk 8.5a6 and aMSN 0.97RC1 will be installed.

Please enter your sudo password:
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Hit http://security.ubuntu.com feisty-security/main Packages
Get:2 http://archive.ubuntu.com feisty Release.gpg [191B]
Ign http://archive.ubuntu.com feisty/main Translation-en_US
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Ign http://archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://archive.ubuntu.com feisty/universe Translation-en_US
Ign http://archive.ubuntu.com feisty/multiverse Translation-en_US
Get:3 http://archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_US
Get:4 http://archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Hit http://archive.ubuntu.com feisty Release
Hit http://archive.ubuntu.com feisty-updates Release
Hit http://archive.ubuntu.com feisty-backports Release
Hit http://archive.ubuntu.com feisty/main Packages
Hit http://archive.ubuntu.com feisty/restricted Packages
Ign http://archive.ubuntu.com feisty/universe Packages
Hit http://archive.ubuntu.com feisty/multiverse Packages
Ign http://archive.ubuntu.com feisty/main Sources
Hit http://archive.ubuntu.com feisty/restricted Sources
Hit http://archive.ubuntu.com feisty/universe Sources
Hit http://archive.ubuntu.com feisty/multiverse Sources
Hit http://archive.ubuntu.com feisty-updates/main Packages
Hit http://archive.ubuntu.com feisty-updates/restricted Packages
Hit http://archive.ubuntu.com feisty-updates/universe Packages
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://archive.ubuntu.com feisty-updates/main Sources
Hit http://archive.ubuntu.com feisty-updates/restricted Sources
Hit http://archive.ubuntu.com feisty-updates/universe Sources
Hit http://archive.ubuntu.com feisty-updates/multiverse Sources
Hit http://archive.ubuntu.com feisty-backports/main Packages
Hit http://archive.ubuntu.com feisty-backports/restricted Packages
Hit http://archive.ubuntu.com feisty-backports/universe Packages
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://archive.ubuntu.com feisty-backports/main Sources
Hit http://archive.ubuntu.com feisty-backports/restricted Sources
Hit http://archive.ubuntu.com feisty-backports/universe Sources
Hit http://archive.ubuntu.com feisty-backports/multiverse Sources
Get:5 http://archive.ubuntu.com feisty/universe Packages [4912kB]
Get:6 http://archive.ubuntu.com feisty/main Sources [385kB]
99% [5 Packages gzip 0]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com feisty/universe Packages
  Sub-process gzip returned an error code (1)
99% [6 Sources gzip 0]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com feisty/main Sources
  Sub-process gzip returned an error code (1)
Fetched 6B in 2s (2B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree
Reading state information... Done
amsn is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_source_Sources - open (2 No such file or directory)
ERROR: Could not install build dependencies.
```

Any ideas? The /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_source_Sources - open part seems kind of strange...



me to this problem

---

### Post by pikul on 2007-08-02
It look's really nice, but what's with the massive code ??? jajajajaja and it download a lot to, but looks really nice, just like it looks on windows :)

---

### Post by Theimon on 2007-08-02
Brilliant. What a difference. Many thanks to you, it looks so much better now.

---

### Post by siralphred on 2007-08-03
both replacements did not work for me, had to  replace it with svn co [https://amsn.svn.sourceforge.net/svnroot/amsn/trunk/amsn](https://amsn.svn.sourceforge.net/svnroot/amsn/trunk/amsn)

---

### Post by Theimon on 2007-08-11
One thing tho, I've been running this new Amsn now for a while and just for fun I took a look at the System monitor. Amsn took up approx. 500MB memory.
Memory hog? Memory leak? Anyone familiar with this?

---

### Post by nickmeet on 2007-08-12
> **siralphred said:**
> both replacements did not work for me, had to  replace it with svn co [https://amsn.svn.sourceforge.net/svnroot/amsn/trunk/amsn](https://amsn.svn.sourceforge.net/svnroot/amsn/trunk/amsn)

I agree. The script should be modified

---

### Post by DaeDaLuS_015 on 2007-08-13
worked perfectly for me first time, good work that man.

---

### Post by beow on 2007-08-14
The script ran without problems. However when I start aMSN all fonts are very tiny. In fact it is not possible to see anything, it's like they are 1 px high or something. 

Desperately needing some tips on this so my daughter stop nagging about windoze msn....

---

### Post by cgrijalba on 2007-08-14
mae pura vida por el script ahora si se ve genial

---

### Post by LuisC-SM on 2007-08-19
Oh man....

Thanks a lot!!!!

Fonts and everything is just fantastic now !!! 

(even tho they are very thiny it is ok for me... in fact, I love this size.

Kind regards.

PS. Now my wife has returned to Ubuntu :guitar:

---

### Post by modzer0 on 2007-08-27
I have been using this script for a while now, updating when necessary. The latest version, however, would not work for me. It would die while building TCL with the following:

```
gcc -shared -g -O2 -D_REENTRANT   -Wl,--export-dynamic  -o libtcl8.5.so regcomp.o regexec.o regfree.o regerror.o tclAlloc.o tclAsync.o tclBasic.o tclBinary.o tclCkalloc.o tclClock.o tclCmdAH.o tclCmdIL.o tclCmdMZ.o tclCompCmds.o tclCompExpr.o tclCompile.o tclConfig.o tclDate.o tclDictObj.o tclEncoding.o tclEnv.o tclEvent.o tclExecute.o tclFCmd.o tclFileName.o tclGet.o tclHash.o tclHistory.o tclIndexObj.o tclInterp.o tclIO.o tclIOCmd.o tclIORChan.o tclIOGT.o tclIOSock.o tclIOUtil.o tclLink.o tclListObj.o tclLiteral.o tclLoad.o tclMain.o tclMathOp.o tclNamesp.o tclNotify.o tclObj.o tclPanic.o tclParse.o tclPathObj.o tclPipe.o tclPkg.o tclPkgConfig.o tclPosixStr.o tclPreserve.o tclProc.o tclRegexp.o tclResolve.o tclResult.o tclScan.o tclStringObj.o tclStrToD.o tclThread.o tclThreadAlloc.o tclThreadJoin.o tclThreadStorage.o tclStubInit.o tclStubLib.o tclTimer.o tclTrace.o tclUtf.o tclUtil.o tclVar.o tclTomMathInterface.o bncore.o bn_reverse.o bn_fast_s_mp_mul_digs.o bn_fast_s_mp_sqr.o bn_mp_add.o bn_mp_and.o bn_mp_add_d.o bn_mp_clamp.o bn_mp_clear.o bn_mp_clear_multi.o bn_mp_cmp.o bn_mp_cmp_d.o bn_mp_cmp_mag.o bn_mp_copy.o bn_mp_count_bits.o bn_mp_div.o bn_mp_div_d.o bn_mp_div_2.o bn_mp_div_2d.o bn_mp_div_3.o bn_mp_exch.o bn_mp_expt_d.o bn_mp_grow.o bn_mp_init.o bn_mp_init_copy.o bn_mp_init_multi.o bn_mp_init_set.o bn_mp_init_size.o bn_mp_karatsuba_mul.o bn_mp_karatsuba_sqr.o bn_mp_lshd.o bn_mp_mod.o bn_mp_mod_2d.o bn_mp_mul.o bn_mp_mul_2.o bn_mp_mul_2d.o bn_mp_mul_d.o bn_mp_neg.o bn_mp_or.o bn_mp_radix_size.o bn_mp_radix_smap.o bn_mp_read_radix.o bn_mp_rshd.o bn_mp_set.o bn_mp_shrink.o bn_mp_sqr.o bn_mp_sqrt.o bn_mp_sub.o bn_mp_sub_d.o bn_mp_to_unsigned_bin.o bn_mp_to_unsigned_bin_n.o bn_mp_toom_mul.o bn_mp_toom_sqr.o bn_mp_toradix_n.o bn_mp_unsigned_bin_size.o bn_mp_xor.o bn_mp_zero.o bn_s_mp_add.o bn_s_mp_mul_digs.o bn_s_mp_sqr.o bn_s_mp_sub.o tclUnixChan.o tclUnixEvent.o tclUnixFCmd.o tclUnixFile.o tclUnixPipe.o tclUnixSock.o tclUnixTime.o tclUnixInit.o tclUnixThrd.o tclUnixCompat.o tclUnixNotfy.o memcmp.o strstr.o strtoul.o strtod.o fixstrtod.o tclLoadDl.o  -ldl  -lpthread -lieee -lm   -Wl,-rpath,/usr/local/lib
fixstrtod.o: In function `fixstrtod':
/tmp/fixamsn.12190/tcl/unix/../compat/fixstrtod.c:31: multiple definition of `fixstrtod'
strtod.o:/tmp/fixamsn.12190/tcl/unix/../compat/strtod.c:79: first defined here
/usr/bin/ld: Warning: size of symbol `fixstrtod' changed from 746 in strtod.o to 78 in fixstrtod.o
collect2: ld returned 1 exit status
make: *** [libtcl8.5.so] Error 1
ERROR: Could not compile Tcl.
```

After a lot of searching and finding nothing, I resorted to trying to compile TCL manually to see what the problem might be. In the end, I discovered that this error occurred if configure was run with --enable-64bit. I removed this option from fixamsn.sh and then it all installed fine and I'm now running the latest amsn that this script was meant to install.

Not sure why this happened, as the script is supposed to work with either 32 or 64-bit. I'm running a 64-bit processor (Athlon 64 X2 3800) but with 32-bit Feisty (i386, NOT amd64). Not sure if anyone else has run into this problem, but I thought I'd report my experience.

---

### Post by jcraveiro on 2007-09-10
The latest version of the script does not work; in line 153, you should replace:

```
svn co https://svn.sourceforge.net/svnroot/amsn/trunk/amsn/ amsn || error_exit "Could not download aMSN source code."
```

with

```
svn co https://amsn.svn.sourceforge.net/svnroot/amsn/trunk/amsn/ amsn || error_exit "Could not download aMSN source code."
```

---

### Post by koleoptero on 2007-09-11
Thank you! Just thank you. :)

---

### Post by Pikestaff on 2007-09-12
Huge thanks, this script made me switch back to aMSN again, I didn't use it for a long time because of the ugly fonts.  Thank you!

---

### Post by Poka64 on 2007-09-13
I'm getting this error when I try to run Amsn compiled with the cvs version

[IMG]http://static.pici.se/pictures/rqVUJURsE.png[/IMG]

---

### Post by drdnl on 2007-09-13
Getting the same error as above, does anyone have a solution?

---

### Post by alqualond on 2007-09-14
Thanks a lot for the script!  It worked fine for me, and aMSN looks great, including greek fonts.

---

### Post by kolslorr on 2007-09-26
hey, i like the screenshot, but i have this error while running...

```
Need to get 12.4MB of archives.
After unpacking 33.2MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  gawk x11proto-core-dev libice-dev libsm-dev libxau-dev libxdmcp-dev x11proto-input-dev x11proto-kb-dev xtrans-dev libx11-dev libxt-dev diffstat
  libjpeg62-dev zlib1g-dev libpng12-dev quilt tcl8.4-dev tk8.4-dev
E: There are problems and -y was used without --force-yes
E: Failed to process build dependencies
ERROR: Could not install build dependencies.

```

Any idea?

Thanks!

---

### Post by Princey on 2007-09-27
Try installing the build dependencies first through synaptic.

---

### Post by bigken on 2007-09-27
worked a treat for me cheers :)

---

### Post by kolslorr on 2007-09-27
> **Princey said:**
> Try installing the build dependencies first through synaptic.

Thanks, i get through it by fixing all the errors in my source list...

The installation went smoothly, and i managed to get it working great!

however, I still have some issues... on starting the AMSN now... the CPU will be 100% for like 5 minutes until AMSN is fully loaded.... this doesnt happened when I was using the older version in repository...

Another problem is that i lost sound AGAIN... aplay doesnt work, and the snack library i installed 2 days ago failed too... :(:(:(

---

### Post by go_dragons on 2007-10-04
First I would like to thank you for the script. I had installed amsn through apt previously and had eventually removed it because I thought it would be too much trouble to fix all of its asthetic problems. Still, amsn has the best support for the MSN network I know of so when I saw this script I decided to try again. This script helped me to get a working and deicent looking program. This is probably better than I could have done after hours of tweaking - but I'm afraid I'm only about 99% satisfied. 

There is only one problem I have come across that I have not been able to figure out so I am looking to the forums. I tried to install a couple of skins and plugins to complete the package look and feel I am looking for. I downloaded them from amsn-project.net and put them into the appropriate folder. Skins work perfectly as they should, but plugins only work until I close the program. When I restart the program I have to manually reload the plugins. 

I assume that by 'loading' the plugins I am just configuring a text file or one of the xml files but I have not for the life of me been able to figure out where I need to look. Every other setting and option will keep its status after I close the program so the issue applies only to loading new plugins. Can someone help me? Thanks.



ps. While trying to load the chameleon plugin I get this error 
[I]Plugins System: Can't initialize plugin:init procedure caused an internal error
[/I]
While this does bother me some I can live without it.

---

### Post by Phlogiston on 2007-10-05
thanks

---

### Post by X3n0n on 2007-10-07
> **go_dragons said:**
> While trying to load the chameleon plugin I get this error 
[I]Plugins System: Can't initialize plugin:init procedure caused an internal error
[/I]

I have the same problem...I tried to compile tile again but this time I get many errors and can't complete the procedure. I assume that the packages that are installed through the script conflict with tile...

---

### Post by koleoptero on 2007-10-12
Worked for me. Thanks a really lot! :D

---

### Post by Thug on 2007-10-12
Hi all!

I've always used this script for amsn. 

This time i have a problem

```
svn: richiesta PROPFIND fallita su '/svnroot/amsn/trunk/amsn'
svn: PROPFIND di '/svnroot/amsn/trunk/amsn': Could not resolve hostname `svn.sourceforge.net': Host non trovato (https://svn.sourceforge.net)
ERROR: Could not download aMSN source code.

```
What does it mean?

The distro is ubuntu gutsy rc1
Thanks for help

Bye!

---

### Post by LuisC-SM on 2007-10-13
Whether the host name has changed or it was not available when you executed the script (which is my guess)
Under xubuntu 6.06 dapper I just made it work (without changes)
Cheers

---

### Post by HumanAnarchist on 2007-10-16
if you got tls problems, look at this page:

[http://www.amsn-project.net/wiki/TLS](http://www.amsn-project.net/wiki/TLS)

-ha-

---

### Post by Dropknee on 2007-10-20
I modified the script to install the svn because the server in the script, simply don´t response.

right click the scrip and use the ¨open with text editor¨

Search this line in the script:

```
#amsn trunk
    svn co https://svn.sourceforge.net/svnroot/amsn/trunk/amsn/ amsn || error_exit "Could not download aMSN source code."
```

and change it to this:

```
#amsn trunk
    svn co https://amsn.svn.sourceforge.net/svnroot/amsn/trunk/amsn/ amsn || error_exit "Could not download aMSN source code."
else
```

Save change, and use the script again, now you can install the SVN version without problem, maybe the server need to accept the certificate, I use the permanent option.

I hope this help.

---

### Post by LuisC-SM on 2007-10-20
> **Dropknee said:**
> I modified the script to install the svn because the server in the script, simply don´t response.



Thanks !!! :) I'll tryit tonight

---

### Post by k3pp0 on 2007-10-22
works like a charm!
Thanks!

---

### Post by anarchypower on 2007-10-22
Works perfect.
Thank you a lot :)

---

### Post by budde on 2007-10-23
i love you forever. works perfectly.

---

### Post by djimel on 2007-10-23
merci beaucoup pour cette aide précieuse... apès avoir galéré un bon moment tout fonctionne
Bravo !

---

### Post by Cochise on 2007-10-28
You Sir are a god, thank you very much

---

### Post by brickuz on 2007-10-28
That was easy even for a beginner in Linux and it worked like a charm! Thanks a lot!

---

### Post by snide on 2007-10-29
Awesome.... sooooo yes!!!!!!

---

### Post by Ed Banger on 2007-10-30
muchos thx, making it much easier for rookies ;)

---

### Post by Scimu on 2007-10-31
Brilliant! Thank you very very much.. Been trying to get AA to work for a bit :D

---

### Post by blue212 on 2007-11-03
OMG it's so beautiful!!
Script works perfect

Ubuntu 7.10 Gutsy

to get sound to work I had to go into Account->Preferences->Other
and change the sound server to

```
aplay $sound
```

---

### Post by mdpalow on 2007-11-03
Beautiful !

Great script...

Thanks for taking the time to do this.

---

### Post by jav_ on 2007-11-04
wow it looks so much better, thanks!

---

### Post by Thies on 2007-11-07
Hi!
The script works fine ... many thanks for that! Still had some problems with TLS when starting aMSN ("Couldn't get http://switch.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz").

This solved my problems (from [Automatix forum](http://www.getautomatix.com/forum/index.php?showtopic=1182"")):

```
wget http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz
```

```
tar xvzf tls-1.5.0-linux-x86.tar.gz
```

```
sudo cp -f ~/tls1.50/* /usr/lib/tls1.50/
```

Restart aMSN and this works! :)

---

### Post by tomtity123 on 2007-11-27
works perfect 
thanks very much

---

### Post by yomeh on 2007-11-28
this works for me but doesnt remove blue border around the contacts can anyone help?

thanks for the script

---

### Post by Daniel15 on 2007-11-30
The "cvs" option does not work properly at the moment. To fix it, find:
```

svn co https://svn.sourceforge.net/svnroot/amsn/trunk/amsn/ amsn || error_exit "Could not download aMSN source code."

```

And replace it with:
```

    svn co https://amsn.svn.sourceforge.net/svnroot/amsn/trunk/amsn/ amsn || error_exit "Could not download aMSN source code."

```
That should fix it :)

---

### Post by vw_crazy on 2007-12-04
Just wanted to say thanks... worked fine for me!
:)

---

### Post by ilyasyildirim on 2007-12-07
Great script! Thanks a lot.:)

---

### Post by iGama on 2007-12-09
The script should be updated to use TCL and TK beta3 (b3) instead of Alpha6 (a6)

:)

---

### Post by rev0x on 2007-12-18
yeah nice! thanks a lot :)

---

### Post by paranoidchampion on 2007-12-19
I love you! The god damn ugliness of aMSN was driving me insane! I'd be searching on the net, asking in forumns here, there and everywhere but to no avail.  Finally i find this post, and all I can say is wow! It's finally sorted out! Mmmmmm tasty!

---

### Post by olskar on 2007-12-28
0.97 is now released! Will it be installed if I use this script?

---

### Post by phissen on 2007-12-28
great script! thank you :) works perfectly :D

---

### Post by OffHand on 2007-12-28
> **olskar said:**
> 0.97 is now released! Will it be installed if I use this script?

No, but I changed the script so it will download the latest release. Feel free to use it.

---

### Post by speedcore on 2007-12-29
This will install the latest version of amsn, tested ;)

---

### Post by jav_ on 2007-12-29
yep..it works with the new version..thanks

---

### Post by rico1981 on 2008-01-05
thank you for this script. 
I just tested it on a Ubuntu 7.10 AMD64 machine and it works like a charm!

---

### Post by pjalegria on 2008-01-05
If why want to unistall this, who can i do it????

---

### Post by wheredidrealitygo on 2008-01-05
Thanks for the script, works great!

---

### Post by embeemb on 2008-01-07
I got a bit of a problem with running the script. I know it's probably something wrong at my end, however I don't know how to fix it.

When running the script, I get this error:

> E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_main_source_Sources - open (2 No such file or directory)
ERROR: Could not install build dependencies.


Any tips would be excellent! Thanks.

---

### Post by MockY on 2008-01-08
Worked perfectly for me.

Thank you!

---

### Post by vervelover on 2008-01-09
How do I uninstall it?

---

### Post by OffHand on 2008-01-09
> **vervelover said:**
> How do I uninstall it?

read the instructions in post 1

---

### Post by vervelover on 2008-01-09
Thanks, I should've read more carefully..

One more thing: after using the latest script that installs amsn 0.97 stable, I can't use the snack library anymore.. Do you know why?

---

### Post by OffHand on 2008-01-09
> **vervelover said:**
> Thanks, I should've read more carefully..

One more thing: after using the latest script that installs amsn 0.97 stable, I can't use the snack library anymore.. Do you know why?

I don't know. But why would you go back to the build from the official repositories? It's old and ugly.

---

### Post by vervelover on 2008-01-09
> I don't know. But why would you go back to the build from the official repositories? It's old and ugly.

I wouldn' t go back, but if I can't solve this problem with libsnack I will probably look for another script, or maybe clean everything up and run this script again.. So my guess after reading the notes in post #1 is that I need to run something like:

```
sudo clean amsn
```

or:

```
sudo make clean amsn
```

to uninstall, right?

EDIT:

I found the way to uninstall:

bash fixamsn.sh clean

---

### Post by OffHand on 2008-01-09
Not sure but I think it is:

```
bash fixamsn.sh clean
```

---

### Post by galvheim on 2008-01-09
Really great stuff! Bookmarked this for keeps if I one day must upgrade or reinstall.

Nice Work!

I also got the englis version! Much better for me!

---

### Post by Pablopcv on 2008-01-12
I get stuck with this

```
Resolving easynews.dl.sourceforge.net... 38.97.225.135
Connecting to easynews.dl.sourceforge.net|38.97.225.135|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:02:27 ERROR 404: Not Found.

ERROR: Could not download Tk source code.

```

anyone help? 
thank you

---

### Post by wheredidrealitygo on 2008-01-13
> I get stuck with this

Code:

Resolving easynews.dl.sourceforge.net... 38.97.225.135
Connecting to easynews.dl.sourceforge.net|38.97.225.135|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:02:27 ERROR 404: Not Found.

ERROR: Could not download Tk source code.

anyone help?
thank you 

That's actually a problem with the sourceforge server, not with anything the script is doing wrong. 

I've had a few problems with the sourceforge servers myself at different points, you kind of just have to keep trying and hope they bring their servers back up. You can always manually edit the script and change the server it's connecting to if you can find the url of another sourceforge mirror.

---

### Post by miceagol on 2008-01-13
Getting the following error when launching aMSN?
> 
You can't load 
TkCximage, this is needed to run aMSN. Please compile amsn first, instructions on 
how to compile are located in the file INSTALL


Then you may need to do this:
```
 
sudo ln -sf /usr/local/bin/tclsh8.4 /usr/local/bin/tclsh
sudo ln -sf /usr/local/bin/wish8.4 /usr/local/bin/wish

```
Replace 8.4 with 8.5 if you have Tcl/Tk ver. 8.5. Check what you have with
```

ls -l /usr/local/bin/tclsh*
ls -l /usr/local/bin/wish*

```
I also had some problems with conflicting amsn launch scripts in different bin folders, but that may not apply to you.

---

### Post by LuisC-SM on 2008-01-13
Hi.
In [this page]("http://www.amsn-project.net/linux-downloads.php") you will find a DEB package for Ubuntu for the final aMSN version (0.97)
Good luck
Luis

---

### Post by xpionage on 2008-01-16
Greetings everyone.

I installed this in my ubuntu on vmware and it worked fine but now in my fresh installation on my laptop it gives me this error:

> Building Tree of Dependencies
Reading state information ... Ready
The extended read information from state
Initializing the states of the packages ... Ready
Creating a database of labels ... Ready
The Reading Lists Package ... Ready
Building Tree of Dependencies
Reading state information ... Ready
E: Unable to satisfy dependencies to compile for tcl8.4.
ERROR: Could not install build dependencies.

---

### Post by embeemb on 2008-01-16
Last time I tried running this script, it didn't work without glitches. However what worked for me is install the deb packages for tcl, tk & tcltls. I got the 8.5 versions right away. No need to install 8.4 then 8.5 as the script does. 

Get the three deb packages from [here]("http://in.solit.us/users/public/patrickfromspain"). It has tk 8.5, tcl 8.5 and tcltls 1.5.

Hope that helps.

---

### Post by xpionage on 2008-01-16
> **embeemb said:**
> Last time I tried running this script, it didn't work without glitches. However what worked for me is install the deb packages for tcl, tk & tcltls. I got the 8.5 versions right away. No need to install 8.4 then 8.5 as the script does. 

Get the three deb packages from [here]("http://in.solit.us/users/public/patrickfromspain"). It has tk 8.5, tcl 8.5 and tcltls 1.5.

Hope that helps.

Thanks dude :-D I will try that as soon as I can :-D

---

### Post by xpionage on 2008-01-16
embeemb when i try to install the deb's i always get this error:

Error: Dependency is not satisfiable: tcl8.5

I get this error in all the deb's :\

---

### Post by embeemb on 2008-01-16
You need to figure out which of the dependencies you have and which need to be installed.

In a terminal run:

dpkg-deb -I filename

The result will show you the dependencies of the package you're trying to install. 

sudo apt-get install missingpackages

And you should be ready. Hope that helps.

---

### Post by xpionage on 2008-01-16
Finally installed this :-D

I did what you said but the thing is that i was installing the wrong deb's, there are 2 types, but only 1 deb say that is for gutsy, i was installing the others :P

Thanks for the help embeemb:KS:KS:KS:KS:KS to you:grin:

---

### Post by embeemb on 2008-01-16
Heh. Glad you got it working! :)

---

### Post by benjaminzsj on 2008-01-22
Great script, thanks!

---

### Post by whashnez on 2008-01-24
Thanks dude!!!!It rocked!!!!:guitar

---

### Post by probey on 2008-01-27
I just moved from vista to ubuntu 7.10 couple days ago and found this amazing script. I ran this script with the supplied instructions and it worked like a charm, upgraded amsn and enabled anti-aliasing automatically without any error!!!

Thanks for sharing this amazing script!!!

---

### Post by Santo_3 on 2008-01-28
will it work on kubuntu?7.10!
thx:)

---

### Post by Santo_3 on 2008-01-28
It did work!
Thx
ppl like you make the difference!
thxxxxxxxxxxxxx

---

### Post by arang on 2008-01-28
anyone could fix this script? cos it tries to get this file from here

[http://easynews.dl.sourceforge.net/sourceforge/amsn/Ubuntu-1.0b.tar.gz](http://easynews.dl.sourceforge.net/sourceforge/amsn/Ubuntu-1.0b.tar.gz)

but the site is like dead? and the thing stays waiting for a time out

so could the maintainer add a mirror or something?

---

### Post by joao82 on 2008-01-31
thanks, it worked just fine. now i have "the" latest amsn running on ubuntu gutsy.
but... it had to download over 60Mb of data and changed my download servers from archive.ubuntu.com to pt.archive.ubuntu.com and added the cdrom to my software sources. ok, it changed it to the country where I live, but I prefer it the way I had it.
that was a very extensive update, but it gets the job done.

---

### Post by Victormd on 2008-01-31
thank you, thank you, thank you!
Great script!!!

---

### Post by Morgan86 on 2008-02-01
Great work man, thank you very much!
:guitar:

---

### Post by Bad_Byte on 2008-02-05
@ Vuen

Thank you =)

---

### Post by benevolent on 2008-02-07
THANKS A LOT MAN!!!!

this script fixed my font problem.....


:) :) :)

---

### Post by gladstone on 2008-02-10
Quick and easy, aMSN looks great and is usable now.

Thanks

---

### Post by Krafturinn on 2008-02-10
thanks alot my amsn is much better now :)):P:cool:

---

### Post by itsjustarumour on 2008-02-14
Thanks a lot for the script - after over 2 years of trouble I finally have my final issue with aMSN solved! :-D

The first time I ran the script, I did get a  weird error message about Python and 8.4 something or other not yet being configured, which I suspect was caused by an aborted installation of PyChess last week.  So I uninstalled 8.4 and also aMSN for good measure, and second time around everything worked like a dream! :-D

---

### Post by schumi3006 on 2008-02-16
Superb script, worked like a charm. Cheers, mate!!

---

### Post by PiggiePaul on 2008-02-16
Hi, Just wanted to make 100% sure before I try this.
I've just today installed aMSN 0.97 from the GetDeb site.

All it's all working fine (apart from horrid fonts)

Should I use your script on page 1 of this LONG Thread.
Or should I use the one you posted in Posting # 195 of this thread?

Don't want to screw things up by running the wrong version?

Oh and I'm using Ubuntu 7.1 gutsy.

Thanks.

============ EDIT==============

Well, I could not bare to wait any longer, so ran your script (as instructed) in your 1st post.

Superb, Excellent, Fantastic. 

All ran through perfectly without any glitches or errors.

I was holding my breath watching the mountains of text and commands going by. Thinking to myself, this looks like Nuclear Physics to just fix a Pimple!
But, the result was well worth it.

aMSN looks So Much Better now.

Many thanks, and well done :)

---

### Post by stathis21 on 2008-02-20
last time i tried to install your script i had this problem...(and people,not only me)...
it tells me 
E: Build-Depends &#949;&#958;&#945;&#961;&#964;&#942;&#963;&#949;&#953;&#962; &#947;&#953;&#945; &#964;&#959; amsn &#948;&#949;&#957; &#953;&#954;&#945;&#957;&#959;&#960;&#959;&#953;&#959;&#973;&#957;&#964;&#945;&#953; &#949;&#960;&#949;&#953;&#948;&#942; &#964;&#959; &#960;&#945;&#954;&#941;&#964;&#959; tk8.5-dev &#948;&#949;&#957; &#946;&#961;&#941;&#952;&#951;&#954;&#949;
ERROR: Could not install build dependencies.
some of these words are greek...
it tells me that it cannot find tk8.5-dev packet and it stops the installation...

---

### Post by Nano-rus on 2008-02-20
I got that exact same problem. Anyone know what's wrong?

---

### Post by Falcuzzo on 2008-02-21
same problem here: no tk8.5-dev ERROR: Could not install build dependencies.

---

### Post by embeemb on 2008-02-21
Download Tk8.5-dev from [here]("http://in.solit.us/archives/show/118166").

Then navigate to the directory where you downloaded it - eg Desktop and proceed as follows:

cd ~/Desktop
sudo dpkg -i package-name.deb

This will install tk8.5-dev on your system. Run the script normally afterwards & you should be good to go..

---

### Post by Falcuzzo on 2008-02-22
doesn't work your solution, errors depackaging tk8.5

---

### Post by rickrob on 2008-02-22
Hi im very new to ubuntu,2 weeks.Keep getting this when i try to install  the script.E: Build-Depends dependency for amsn cannot be satisfied because the package tk8.5-dev cannot be found

---

### Post by embeemb on 2008-02-22
> **Falcuzzo said:**
> doesn't work your solution, errors depackaging tk8.5
What kind of error are you gettin when attempting to depackage tk8.5-dev ?

---

### Post by carlosjuliopr on 2008-02-22
hi
1st of all thanks a lot for such a wonderful script, it makes life easy for a lot of people. :-)

that said i have a little problem when running the script it says:

```
E: Build-Depends dependency for amsn cannot be satisfied because the package tk8.5-dev cannot be found
ERROR: Could not install build dependencies.
```

i was wandering what went wrong  :-(

thanks ! ! !

---

### Post by carlosjuliopr on 2008-02-22
mine says: 

```
(Reading database ... 113244 files and directories currently installed.)
Preparing to replace tk8.5-dev 8.5.0-1 (using tk8.5-dev_8.5.0-1_i386.deb) ...
Unpacking replacement tk8.5-dev ...
dpkg: dependency problems prevent configuration of tk8.5-dev:
 tk8.5-dev depends on tcl8.5-dev (>= 0.b3); however:
  Package tcl8.5-dev is not installed.
 tk8.5-dev depends on tk8.5 (= 8.5.0-1); however:
  Package tk8.5 is not installed.
dpkg: error processing tk8.5-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tk8.5-dev 
```

---

### Post by embeemb on 2008-02-23
Okay, I'm not too sure what's the mess up, but from the messages you're getting, you gotta install Tcl8.5 and Tk8.5 first before running the script. I know it's not supposed to go that way, but give it a try. It might work out for you.

Get the [Tcl8.5]("http://in.solit.us/archives/download/114664"), [Tk8.5 ]("http://in.solit.us/archives/show/113979")and [Tcltls8.5]("http://in.solit.us/archives/show/115681") deb packages and install them in that particular order.

Then try & run the script again..

---

### Post by Falcuzzo on 2008-02-23
i've solved installing Tcl 8.5, Tk 8.5 & Tls 1.5.0 and amsn from [http://in.solit.us/users/public/patrickfromspain](http://in.solit.us/users/public/patrickfromspain)

I suppose there's a problem in tk8.5 svn. May be in few days the script will work again

---

### Post by Arlanthir on 2008-02-24
Tcl 8.5 updated in my box, along with amsn!
Is this because of the script? I ran ./fixamsn.sh clean and then installed the amsn from the repos and it's all nice!

Could someone confirm that the default is now always anti-aliased?

---

### Post by IGNIZ on 2008-02-24
> **carlosjuliopr said:**
> mine says: 

```
(Reading database ... 113244 files and directories currently installed.)
Preparing to replace tk8.5-dev 8.5.0-1 (using tk8.5-dev_8.5.0-1_i386.deb) ...
Unpacking replacement tk8.5-dev ...
dpkg: dependency problems prevent configuration of tk8.5-dev:
 tk8.5-dev depends on tcl8.5-dev (>= 0.b3); however:
  Package tcl8.5-dev is not installed.
 tk8.5-dev depends on tk8.5 (= 8.5.0-1); however:
  Package tk8.5 is not installed.
dpkg: error processing tk8.5-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tk8.5-dev 
```

just uninstall previous amsn installation files and tcl and tk every version you have. i had same problem

---

### Post by HumanAnarchist on 2008-02-25
fsck, "fixamsn.sh clean" deleted my .amsn/ dir, with all my logs, webcam logs, smilies ++++ FSCK!!!111one :(

bad fixamsn.sh, bad bad bad

At least rename the dir or just move it to tmp.... (yes i know it's a warning about it)

---

### Post by arang on 2008-03-01
i love this script but the only problem is the voice messages it keeps telling me 

The Snack library is needed in order to use this feature. A minimal version of 2.2.9 is necessary.

even when i have that library installed already but it doesnt find it could SOMEONE please tell me how to fix it i googled it but everyone says sudo apt-get install snack2 but thats already done.

---

### Post by NScratch on 2008-03-01
I had the same snack library problem, and I finally fixed it thanks to this thread:

[http://www.techzonept.com/showpost.php?p=2496030&postcount=49](http://www.techzonept.com/showpost.php?p=2496030&postcount=49)

Make sure libsnack2 is installed, and then:
```
sudo ln -s /usr/lib/snack2.2 /usr/local/lib
```

And voila, no more "snack failed to load" error, and voice messages work fine :)

---

### Post by thiagof.fernandes on 2008-03-13
Perfect ! Works perfect !

---

### Post by Conan_Kung on 2008-03-22
Thanks !!!  _/\_

---

### Post by bongo on 2008-03-26
I have problems with amsn refusing to go to dock, any takers on why? I have no fancy config and I'm running gutsy. I tried alltray without success as well.

---

### Post by MedellinManDem on 2008-03-26
Worked first time.

amazing

---

### Post by Princey on 2008-03-27
Does anyone know if this script will work under Hardy Heron?

Edit: Never mind, I tried it and it works under Hard Heron beta.

---

### Post by OffHand on 2008-03-28
> **Princey said:**
> Does anyone know if this script will work under Hardy Heron?

Edit: Never mind, I tried it and it works under Hard Heron beta.

You don't really need it under Hardy anymore because aMSN has been compiled with TCL8.5 so the fonts render properly.

---

### Post by focb on 2008-03-28
Awesome script - thanks very much!

---

### Post by karush on 2008-04-28
> **OffHand said:**
> You don't really need it under Hardy anymore because aMSN has been compiled with TCL8.5 so the fonts render properly.

So, please let me understand... to have the latest version (svn) of aMsn on Unbuntu 8.04 (amd64) i don't need this script anymore or is it still good?

Anyway, is there a way to unisntall (purge) everything the script installs? Or at least, a log to know what i can manually purge!?

Thank you very much guys. Good Work!

Bye

---

### Post by OffHand on 2008-04-28
> **karush said:**
> So, please let me understand... to have the latest version (svn) of aMsn on Unbuntu 8.04 (amd64) i don't need this script anymore or is it still good?

Anyway, is there a way to unisntall (purge) everything the script installs? Or at least, a log to know what i can manually purge!?

Thank you very much guys. Good Work!

Bye

bash fixamsn.sh clean

---

### Post by Auximenes on 2008-04-28
Just upgraded to 8.04, and finally cracked the nut on how to get SCIM japanese input to work in aMSN, only to find those jagged characters almost impossible to read!

This extremely easy and convienient anti-aliasing tool really did the job - thank you thank you thank you :D

---

### Post by rhomany on 2008-07-04
Thanks so much for this. I just spent 2 hours faffing about trying to get rid of my 'could not detect tcl' error message when I found this. When I first ran it it said my 'version was not supported' or something like but offered continue anyway and from that point worked like a charm :)

---

### Post by AADude on 2008-07-15
This might be a little late D: but when I executed the script and it asked for root password, it just went right to the installation process instead of giving me time to enter it in - maybe because I was already logged in as root?

---

### Post by eyden on 2009-01-06
I tried the script, everythings was without errors done; but when I try to open my account, amsn just keep trying to logging in...without result!

Any help please =)

thanks

---

### Post by 697loscfc on 2009-02-13
ERROR: Could not download Tcl source code.
 Is that bad?

---

### Post by subspider on 2010-01-09
hi i run these on xubuntu karmic and i can't run my amsn anymore i tryed to unistall using synaptic but nothing please help

---

### Post by tigerclauz on 2011-11-17
I tried to fix aMSN for Ubunto 10.04 and i got this message:
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... failed: No route to host.
ERROR: Could not download Tcl source code.

What do I do?

---

