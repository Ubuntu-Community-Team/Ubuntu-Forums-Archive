---
title: "Install Citrix Receiver on Ubuntu 13.10?"
date: 2013-08-07
forum: Ubuntu Development Version
---

### Post by volkerbradley on 2013-08-07
Has anyone managed to install the Citrix receiver in Ubuntu 13.10?
I tried to follow the instructions posted at [http://www.tuxtrix.com/2013/03/how-to-instal-citrix-client-on-ubuntu.html](http://www.tuxtrix.com/2013/03/how-to-instal-citrix-client-on-ubuntu.html) for installation on Ubuntu 13.04. 
I downloaded and tried to install icaclient_12.1.0_amd64.deb
However, there are missing dependencies of 1a32-libs and the installation fails.

---

### Post by Toz on 2013-08-07
> However, there are missing dependencies of 1a32-libs and the installation fails. 
Have you installed the ia32-libs? I believe that libmotif4 is also a dependency. [This link]("http://crazymadeagle.blogspot.ca/2013/07/howto-install-citrix-client-on-ubuntu.html") might help.

---

### Post by volkerbradley on 2013-08-07
Thanks for the link.  Here is what happens when I try to install ia32-libs in 13.10:
" # apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32z1 lib32ncurses5 lib32bz2-1.0 
E: Package 'ia32-libs' has no installation candidate"

I installed lib32z1, lib32ncurses5 and lib32bz2-1.0 but the dependency on ia32-libs remains and I can't install icaclient_12.1.0_amd64.deb.
I'm sure that there is probably some link that I could use, but I don't know how to proceed.

---

### Post by Toz on 2013-08-07
It would appear that ia32-libs is deprecated. According to [https://help.ubuntu.com/community/CitrixICAClientHowTo]("https://help.ubuntu.com/community/CitrixICAClientHowTo"), all you need to install is "libmotif4:i386 nspluginwrapper". I don't have a 13.10 install handy so I can't test it myself. If you install those 2 packages, does it still ask for ia32-libs?

---

### Post by volkerbradley on 2013-08-08
Yes, the problem persists even though libmotif4:i386 and nspluginwrapper are installed.  Here is the output:
# dpkg -i icaclient_12.1.0_amd64.deb
Selecting previously unselected package icaclient.
(Reading database ... 177491 files and directories currently installed.)
Unpacking icaclient (from icaclient_12.1.0_amd64.deb) ...
dpkg: dependency problems prevent configuration of icaclient:
 icaclient depends on ia32-libs; however:
  Package ia32-libs is not installed.
 icaclient depends on lib32asound2; however:
  Package lib32asound2 is not installed.

dpkg: error processing icaclient (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 icaclient

and:
s# apt-get install lib32asound2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lib32asound2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'lib32asound2' has no installation candidate

---

### Post by volkerbradley on 2013-08-08
Ran into the same problem trying to install Teamviewer.

---

### Post by howefield on 2013-08-08
> **volkerbradley said:**
> Ran into the same problem trying to install Teamviewer.

You should be able to install the 32bit / Multiarch version.

Edit : Just to be clear, I'm only referring to Teamviewer, not your OP.

---

### Post by volkerbradley on 2013-08-09
You're right!  The 32bit / Multiarch version of Teamviewer installed!
Thank you very much.

---

### Post by cariboo on 2013-08-09
The spelling error in the title of this thread was bothering me, so I fixed it. :-P

---

### Post by volkerbradley on 2013-08-09
Thank you

---

### Post by howefield on 2013-08-09
Looks the same problem and is marked as solved.

At your own risk ;-)

[http://www.siduction.org/index.php?name=PNphpBB2&file=viewtopic&t=3199](http://www.siduction.org/index.php?name=PNphpBB2&file=viewtopic&t=3199)

---

### Post by melund on 2013-08-12
Same problem here. No way to get Citrix Receiver installed on Ubuntu 13.10. Or is it ?

---

### Post by newen on 2013-08-16
I have the same problem when I try to install Google Earth for amd64. lsb-core is also required, but not available in the repositories.

---

### Post by BigCityCat on 2013-08-16
Its not hard to get it working. You will have a few more issues to work out. Follow this thread.

[http://ubuntuforums.org/showthread.php?t=1105855](http://ubuntuforums.org/showthread.php?t=1105855)

---

### Post by volkerbradley on 2013-09-27
Does anyone have Citrix Receiver working on 13.10 now?  I have never been able to do it.

---

### Post by volkerbradley on 2013-09-28
Have downloaded and attempted to install icaclient_12.1.0_amd64.deb on 13.10, -64 bit multiple times.
Dependencies have prevented installation. 
I have read all previous posts regarding this subject and tried all of the suggestions posted so far, but all of them fail.
Have any of you been able to install the Citrix receiver on 64-bit Saucy?

---

### Post by Toz on 2013-09-28
*Duplicate threads merged.*

---

### Post by volkerbradley on 2013-10-03
> **BigCityCat said:**
> Its not hard to get it working. You will have a few more issues to work out. Follow this thread.

[http://ubuntuforums.org/showthread.php?t=1105855](http://ubuntuforums.org/showthread.php?t=1105855)

For the life of me, I can't get these instructions to work for me.  Have you been able to do it in 13.10?
What file do you use for installation on 13.10 in a 64-bit system?  I tried linuxx86_12.1.0.203066.tar.gz but it won't install.
Do you have any other suggestions?

---

### Post by Sageth on 2013-10-08
I was able to get it working.  Here's a brief rundown (note: I did other steps as well, but don't believe they have any effect):

[LIST=1]
[*]I downloaded the tar.gz from the Citrix site and extracted it (the path is henceforth known as %CitrixTar%).  I could not get the .deb installer to work for the life of me.  This also means it's the 32-bit client, but meh... it's working.
[*]```
sudo apt-get install libmotif4 nspluginwrapper
sudo rm -rf /opt/Citrix/ICAClient/
```
[*]Then edit the %CitrixTar%/linxx86/hinst file and do the following:
Find on line 1233:```
echo $Arch|grep "i[0-9]86" >/dev/null
```
Change to: ```
echo $Arch|grep "86" >/dev/null
```
[*]Back at the command line:
```
sudo %CitrixTar%/linuxx86_12.1.0.203066/setupwfc
```
[*]Choose options as necessary (I left defaults), then choose option 3 to quit
[*]Last, do one or both of the following, depending on your options selected above (you may need to customize them further based on your own configuration): 
```
sudo ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts/
sudo ln -s /usr/share/ca-certificates/mozilla/* ~/ICAClient/linuxx86/keystore/cacerts/
```
[/LIST]

Is it clean? No... I'd really like to see the 64-bit version working, but it's a reasonable workaround without ia32-libs.

---

### Post by volkerbradley on 2013-10-09
> **Sageth said:**
> I was able to get it working.  Here's a brief rundown (note: I did other steps as well, but don't believe they have any effect):

[LIST=1]
[*]I downloaded the tar.gz from the Citrix site and extracted it (the path is henceforth known as %CitrixTar%).  I could not get the .deb installer to work for the life of me.  This also means it's the 32-bit client, but meh... it's working.
[*]```
sudo apt-get install libmotif4 nspluginwrapper
sudo rm -rf /opt/Citrix/ICAClient/
```
[*]Then edit the %CitrixTar%/linxx86/hinst file and do the following:
Find on line 1233:```
echo $Arch|grep "i[0-9]86" >/dev/null
```
Change to: ```
echo $Arch|grep "86" >/dev/null
```
[*]Back at the command line:
```
sudo %CitrixTar%/linuxx86_12.1.0.203066/setupwfc
```
[*]Choose options as necessary (I left defaults), then choose option 3 to quit
[*]Last, do one or both of the following, depending on your options selected above (you may need to customize them further based on your own configuration): 
```
sudo ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts/
sudo ln -s /usr/share/ca-certificates/mozilla/* ~/ICAClient/linuxx86/keystore/cacerts/
```
[/LIST]

Is it clean? No... I'd really like to see the 64-bit version working, but it's a reasonable workaround without ia32-libs.
Thank you for reponding.
Unfortunatley, this method  did not work for me.  I followed these instructions.  The installation proceeded without error messages.  Firefox no longer has an error message when trying to log into the cloud based Electronic Medical Record.  After logging in and then clicking on the actual application, nothing happens. The EMR (EHR) does not open.  
Do you have any idea where I would see error messages or log files?

---

### Post by Sageth on 2013-10-09
Sorry, unfortunately I do not.  I found some information at the Citrix support site, but that was only for Windows.  I'll keep looking for a bit and see if I can find anything.

---

### Post by erkiha on 2013-10-10
I downloaded deb package, unpacked, removed dependecies to ia23-libs and libaudio32, repackaged the deb and it works perfectly.

---

### Post by volkerbradley on 2013-10-10
> **erkiha said:**
> I downloaded deb package, unpacked, removed dependecies to ia23-libs and libaudio32, repackaged the deb and it works perfectly.
Would love to understand what you did.  Would you consider posting the steps?

---

### Post by volkerbradley on 2013-10-10
> **Sageth said:**
> I was able to get it working.  Here's a brief rundown (note: I did other steps as well, but don't believe they have any effect):

[LIST=1]
[*]I downloaded the tar.gz from the Citrix site and extracted it (the path is henceforth known as %CitrixTar%).  I could not get the .deb installer to work for the life of me.  This also means it's the 32-bit client, but meh... it's working.
[*]```
sudo apt-get install libmotif4 nspluginwrapper
sudo rm -rf /opt/Citrix/ICAClient/
```
[*]Then edit the %CitrixTar%/linxx86/hinst file and do the following:
Find on line 1233:```
echo $Arch|grep "i[0-9]86" >/dev/null
```
Change to: ```
echo $Arch|grep "86" >/dev/null
```
[*]Back at the command line:
```
sudo %CitrixTar%/linuxx86_12.1.0.203066/setupwfc
```
[*]Choose options as necessary (I left defaults), then choose option 3 to quit
[*]Last, do one or both of the following, depending on your options selected above (you may need to customize them further based on your own configuration): 
```
sudo ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts/
sudo ln -s /usr/share/ca-certificates/mozilla/* ~/ICAClient/linuxx86/keystore/cacerts/
```
[/LIST]

Is it clean? No... I'd really like to see the 64-bit version working, but it's a reasonable workaround without ia32-libs.
After doing sudo apt-get dist-upgrade and rebooting, this works for me as well.
Thank you!

---

### Post by erkiha on 2013-10-11
> **volkerbradley said:**
> Would love to understand what you did.  Would you consider posting the steps?

Do this: [https://geekwentfreak-raviteja.rhcloud.com/2012/10/modify-dependencies-addremove-files-of-debian-deb-package/](https://geekwentfreak-raviteja.rhcloud.com/2012/10/modify-dependencies-addremove-files-of-debian-deb-package/) and in file named **control** at line beginning with "Depends:" remove conflicting dependencies from list.

---

### Post by volkerbradley on 2013-10-11
> **erkiha said:**
> Do this: [https://geekwentfreak-raviteja.rhcloud.com/2012/10/modify-dependencies-addremove-files-of-debian-deb-package/](https://geekwentfreak-raviteja.rhcloud.com/2012/10/modify-dependencies-addremove-files-of-debian-deb-package/) and in file named **control** at line beginning with "Depends:" remove conflicting dependencies from list.
Thank you very much. Works for me as well.

---

### Post by dark_harmonics on 2013-10-14
Just to document this process so that when i google this problem i come across the compiled solution to this:[INDENT]1. Download citrix deb file from [www.citrix.com](www.citrix.com). I used the new customer preview 12.9.999
2. Open a terminal and change to the directory where the deb file is located
3. Run the following commands[/INDENT]
[INDENT=2]```
mkdir ica_temp
dpkg-deb -x icaclient-<tab> ica_temp
dpkg-deb --control icaclient-<tab> ica_temp\DEBIAN
sudo gedit ica_temp\DEBIAN\control
```[/INDENT]
[INDENT]4. Change the dependencies to be "Depends: libc6-i386 (>= 2.7-1), lib32z1,  nspluginwrapper"
5. Save and close the file[/INDENT]
[INDENT]6. Compile and install the deb file[/INDENT]
[INDENT=2]```
dpkg -b ica_temp icaclient-modified.deb
sudo dpkg -i icaclient-modified.deb
```[/INDENT]
[INDENT]7. Cleanup with[/INDENT]
[INDENT=2]```
rm -r ica_temp
```

[/INDENT]
I also needed to run sudo apt-get install -f to install the dependencies i was still missing.

---

### Post by volkerbradley on 2013-10-18
After following these instructions, I was getting error code messages during the installation of the modified .deb file.
User ibjsb4 pointed out the solution.
See his post at [http://ubuntuforums.org/showthread.php?t=2181509](http://ubuntuforums.org/showthread.php?t=2181509)

---

### Post by cu_ on 2013-10-19
> **Sageth said:**
> I was able to get it working.  Here's a brief rundown (note: I did other steps as well, but don't believe they have any effect):

[LIST=1]
[*]I downloaded the tar.gz from the Citrix site and extracted it (the path is henceforth known as %CitrixTar%).  I could not get the .deb installer to work for the life of me.  This also means it's the 32-bit client, but meh... it's working.
[*]```
sudo apt-get install libmotif4 nspluginwrapper
sudo rm -rf /opt/Citrix/ICAClient/
```
[*]Then edit the %CitrixTar%/linxx86/hinst file and do the following:
Find on line 1233:```
echo $Arch|grep "i[0-9]86" >/dev/null
```
Change to: ```
echo $Arch|grep "86" >/dev/null
```
[*]Back at the command line:
```
sudo %CitrixTar%/linuxx86_12.1.0.203066/setupwfc
```
[*]Choose options as necessary (I left defaults), then choose option 3 to quit
[*]Last, do one or both of the following, depending on your options selected above (you may need to customize them further based on your own configuration): 
```
sudo ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts/
sudo ln -s /usr/share/ca-certificates/mozilla/* ~/ICAClient/linuxx86/keystore/cacerts/
```
[/LIST]



Is it clean? No... I'd really like to see the 64-bit version working, but it's a reasonable workaround without ia32-libs.

Thank you. This worked like a charm.  Even prior to 13.10, 64 bit install was not really clean anyway.  I appreciate you posting this.  Wish I saw this before I wasted couple of hours trying to get .deb dependencies resolved.

---

### Post by jajodo on 2013-10-20
I was flailing with this too... again, as with each Ubuntu upgrade it seems.
Thanks to all the contributors above- will summarize: 

I had success by installing the 12.1 386 client deb

**It errored out as described above:**
[I]This installation will likely throw the following error: 
dpkg: error processing icaclient (--install):
subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing: icaclient[/I]

**Fixed it as described above:**
[I]change line in text file /var/lib/dpkg/info/icaclient.postinst

"echo $Arch|grep "i[0-9]86" >/dev/null"

to: "echo $Arch|grep -E "i[0-9]86|x86_64" >/dev/null"

Then execute the following command: 
sudo dpkg --configure icaclient[/I]

**Then added certs from Mozilla:**
"sudo cp /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts/"

---

### Post by Brianetta on 2013-10-29
> **dark_harmonics said:**
> a fix
Thanks! Completely sorted me, that did.

---

### Post by VinDSL on 2013-10-30
> **dark_harmonics said:**
> Just to document this process so that when i google this problem i come across the compiled solution to this:[INDENT]1. Download citrix deb file from [www.citrix.com](www.citrix.com). I used the new customer preview 12.9.999
2. Open a terminal and change to the directory where the deb file is located
3. Run the following commands[/INDENT]
[INDENT=2]```
mkdir ica_temp
dpkg-deb -x icaclient-<tab> ica_temp
dpkg-deb --control icaclient-<tab> ica_temp\DEBIAN
sudo gedit ica_temp\DEBIAN\control
```[/INDENT]
[INDENT]4. Change the dependencies to be "Depends: libc6-i386 (>= 2.7-1), lib32z1,  nspluginwrapper"
5. Save and close the file[/INDENT]
[INDENT]6. Compile and install the deb file[/INDENT]
[INDENT=2]```
dpkg -b ica_temp icaclient-modified.deb
sudo dpkg -i icaclient-modified.deb
```[/INDENT]
[INDENT]7. Cleanup with[/INDENT]
[INDENT=2]```
rm -r ica_temp
```

[/INDENT]
I also needed to run sudo apt-get install -f to install the dependencies i was still missing.
Thanks!

I used an almost identical process to fix a problem I was having with installing custom Linux kernels on my 64-bit Dell Latitude notebook.

For some strange reason, dpkg *thought* there were unmet dependencies, even though the dependencies were installed and working.

Sooooo, I edited the control file in the header deb, removed the bogus dependencies from the control file, repacked the deb, and boom... it installed just fine.

Just saying...  ;)

---

### Post by zahareevici on 2013-11-03
Ubuntu 13.10 x64
I made like this :
1. download [B]ICAClient_12.1.0-0.x86_64.rpm
[/B]2. convert the  .**rpm **in .**deb** with [B]alien
[/B]3. install 
4. > [COLOR=#000000][FONT=Ubuntu Mono]sudo ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts/
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo ln -s /usr/share/ca-certificates/mozilla/* ~/ICAClient/linuxx86/keystore/cacerts/[/FONT][/COLOR]

Good luck!

---

### Post by cariboo on 2013-11-03
Saucy has been released, so there isn't much need for this thread. If you are having problems with Citirx Receiver on Trusty, please create a new thread, as this one is closed.

---

