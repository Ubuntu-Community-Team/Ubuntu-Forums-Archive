---
title: "Adobe Audition 1.5/WINE display problems"
date: 2009-03-13
forum: Ubuntu Studio
---

### Post by radi0j0hn on 2009-03-13
I am hopelessly addicted to Adobe Audition (1.5) as it does exactly what I need it to do, and I have it down to a fine science.  It's about the only reason I keep Windows on my PC.

I tried to run it under WINE, but the graphical buttons come out messed up, making it unusable.  Has anyone had any luck with it?

Audacity is OK, but Audition works better for me.

TIA

---

### Post by Endolith on 2009-09-06
This is a known bug in Wine.

[http://bugs.winehq.org/show_bug.cgi?id=8865](http://bugs.winehq.org/show_bug.cgi?id=8865)

The buttons still work and all the same functions are available from the menus, so it's not really "unusable"; just ugly.

---

### Post by SenseMaker2011 on 2011-04-23
Pinguin-Folks, 1st welcome here to all... 

On my own I am total new in Linux. I started in 1981 with Basics, then MS Dos and later all that stuff of MS coming out (Win 3.11, Win NT4.0, Win 98/2000, WinXP and Vista)...

So 1st let me give a short report about my very, very new experiences with Linux:

As test I setup a "virtualbox" with Linux/Ubuntu on my Vista Laptop for getting in touch with. Very charming the handling... so I had a good feeling to start a new era - purely with Linux. 

I decided to setup a "blank computer" (IBM, Pentium4, 2.2GHz, 2GB RAM, 40 GB HD)  with Linux which shall be used singulary for audio recording (home studio) and editing for my non commercial radio broadcasting shows.

I was very surprised that the installation with the DVD of Linux Ubuntu 9 version worked so easily and quickly. From Network to Screen etc. ... all was recognized within one hour I had access to the Internet via my router. Amazing... 

Same the online based upgrading to latetest Ubuntu version 10.04 LTS - The Lucid Lynx + Installation of Ubuntu Software Center worked so phantastic. 

Last I setup successfully Google Chrome, Adobe Flash, Skype Beta 2.0 Version and AVIRA as virus scanner. How to install "Java" easily yet I have not found out. Seems little bit more difficult...

What I still miss is a Malware (as I use it for my MS sytem - [www.malwarebytes.org]("http://www.malwarebytes.org") ). Where to get as freeware ?

Beside these few questions my warm congrats to all these people out there doing such a great job since years for this free ware. I suppose you got a new fan :wink: 


Little bit tricky was the integration of the drivers for an elder HP Deskjet 710C printer, but it worked... so the whole mashine as basis is setup. And that all done since Wednesday, not reading any handbook. To setup such a mashine in Windows would have taken me probably double time and days...

**Now the last hurdle has to be taken, I was not successfully yet:** :confused: ***I please for help herewith !***

Since 5 years I produce (non commercial) radio shows with the editor and recording tool **Adobe Audition 1.5** . Everybody reading this will understand, that I dont want make myself confident with new (Linux) programmes, as I am used this great tool for audio editing. 

Same I need it, as I want have the chance to re-editing former shows into some more modern formats. So there is not any reason to switch to another programme e.g. Adour + JACK or Linux MultiMediaStudio. (I have installed all on this new Linux mashine to check out. Nice programes, but actually not really usable for me as it would take me too much time for learning them. I am lack of time definitely...)

I have found many sources on the web for Adobe Audition installation in Linux. With WINE it should be possible to integrate "Adobe Audition 1.5" as I read here and there. I have Wine installed and use latest stable 1.2 version successfully for "Notepad" and same for "FreeCommander" (phantastic File manager under Windows). So Wine works proper it seems...

If I click on the [*.exe file of Adobe Audition 1.5]("http://english.p30world.com/archives/002481.php") (or [this one]("http://www.brothersoft.com/adobe-audition-255661.html")) I only get from Wine the message: "**Error reading setup initialization file**". Alternatively I gave a try with a *.msi file. I do not get any response from Wine. 

So what's wrong ? - Any tipp ? - I have searched the whole web for finding help, same here in the forum...
 
- [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3665](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3665)
- [http://www.youtube.com/watch?v=48GmSc7GRPc](http://www.youtube.com/watch?v=48GmSc7GRPc)
- [http://ubuntuforums.org/showthread.php?t=1095377](http://ubuntuforums.org/showthread.php?t=1095377)
- [http://ubuntuforums.org/showthread.php?t=921487](http://ubuntuforums.org/showthread.php?t=921487)

But yet I have no understanding what is going wrong ??????????

Is there an alternative to Wine for installing Adobe Audition 1.5 ? - "Virtual Box" I cannot use, as there is only 10 GB free space now on the small HD. 

Adobe Audition 1.5 shall be the last programme I want install, nothing more than pure audio recording/editing. I need always less 5-6 GB for one single radio show, before I export/backup the datas on an external 4 TB RAID system. So the system is close to the limit I would say. Would be very pitty if I fail now with the plan as the whole Linux system was setup for only one reason: to use Adobe Audition 1.5 (no interests to upgrade it to 3.0 version).

Tks in advance giving attention and your help. Warm regards & Happy Easter/SM2011

---

### Post by sgx on 2011-04-24
Hi, I usually run installers from the terminal, if it fails, sometimes missing .dll or other items are mentioned, and can be added to wine.

wine msiexec -i name.msi
wine adobexxx.exe

There are several download sites for .dll files, just google
its name, and the word download. They go in

/home/user/.wine/drive_c/windows/system32

(wish I learned as fast as you go!!!)
Cheers

---

### Post by SenseMaker2011 on 2011-04-25
> **sgx said:**
> Hi, I usually run installers from the terminal, if it fails, sometimes missing .dll or other items are mentioned, and can be added to wine.

wine msiexec -i name.msi
wine adobexxx.exe

There are several download sites for .dll files, just google
its name, and the word download. They go in

/home/user/.wine/drive_c/windows/system32

Yes, I began with the installer 2 days ago, too... but nothing happened. With the [tip from here]("http://ubuntuforums.org/showpost.php?p=10718802&postcount=2") that I should copy an unpacked Adobe Audition from a running installation in Windows I am little bit a step further. It seems that wine is trying to install.

But 1st I got following message after using the command "Wine Audition.exe":

> user@user-desktop:~/Desktop/Temp/MultiMedia$ wine audition.exe
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\windows\\system32\\audition.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\audition.exe" failed, status c0000135So I installed *msvcp71.dll* in the system32 directory. Same I put a copy of Audition.exe renaming with little letters into "audition.exe" and copied into the system32 folder. 

Another try: And I got the message: "**installation package of wrong language**".

I took away again the audition.exe in the system32 folder and started the terminal command "Wine Audition.exe" new. Now I get only one error message:

"**The product not installed properly**" Again and again same this message. - [COLOR=Blue]What to do ?[/COLOR]

> **sgx said:**
> (wish I learned as fast as you go!!!)

I had the hardest trainer ever. Bill Gates and his awesome MS which cost me uncountable days and nights*laugh* And yes, its helpful to have still some DOS command knowledge ;-)

---

### Post by sgx on 2011-04-26
You can rename .wine folder to anything else, and start the install with a clean slate, based on new your findings. You get a fresh .wine folder/registry etc. You might check google and see if it requires a certain .net framework, directX version, or some other common MSoft dependencies. Winetricks is some utility to help installation issues. I have never used it, but it gets mentioned quite often.
Cheers :)

---

### Post by SenseMaker2011 on 2011-04-26
> **sgx said:**
> You can rename .wine folder to anything else, and start the install with a clean slate, based on new your findings. You get a fresh .wine folder/registry etc. You might check google and see if it requires a certain .net framework, directX version, or some other common MSoft dependencies. Winetricks is some utility to help installation issues. I have never used it, but it gets mentioned quite often.
Cheers :)

tks... opening me a new door.

If you look this chart: [http://www.music-software-reviews.com/audio_editors.html](http://www.music-software-reviews.com/audio_editors.html)
it says that .Net is not needed, but directX.

So 1st I installed Winetricks to check out this new tool. Looks really cool. When I clicked on "Install app" I get a list of many packages. 

Do I need to install now 1st a Windows version (e.g. MS Windows 7 SDK or MS Platform SDK 2003) and Windows ActiveX Control Pad ???  - And then install Adobe Audition ? - Or can I install directly Adobe Audition ? 

Little bit lost as I am totally new in the world of Linux ... :)

I only have 10 GB free space on my HD now. I think, its not suitable to install a fully version of Windows, or ? - And truthfully to say: I'd like to implement Adobe Audition in most easy way, without having MS Windows on this new Linux mashine. I am really tired of MS Windows, believe me....   *laugh*

I have a folder .Wine here: home/user/.wine/ yes, and the Program Files and Windows folder with systems32 inside is here: home/user/.wine/dosdevices/c:

Shall I copy now the *.msi  or *.exe into home/user/adobe/ 
Or shall I paste the "fully copy of installed version" I had copied from the Windows mashine to there ?

Tks in advance helping me out... So fare.... TC/SM2011

---

### Post by sgx on 2011-04-26
You may confuse the installers .exe file, with the the applications .exe file ?
audition.exe sounds like the application itself to me. For an .msi installer, from a terminal, type

msiexec -i name-of-installer.msi

If you have a dual-boot, sometimes you can make a symbolic link
between a windows app/folder/dll and its .wine equivalent, use the
filemanager to drag it, select link, rather than copy or move.

In wine, your /home/user-name/Documents folder, is the equivalent of
windows C:\Documents and Settings

If this msi file fails to install, Reaper has simple and effective recording, even a 'save live output to disk', which I use to record broadcasts of the last part of sporting events that I have too little time for. Reaper download

[http://reaper.fm/](http://reaper.fm/)

google points out many many youtubes cover basics of track creation, recording etc and audacity can be used to edit the waveforms.
Cheers

---

### Post by SenseMaker2011 on 2011-04-26
tks sgx

> **sgx said:**
> You may confuse the installers .exe file, with the the applications .exe file ? audition.exe sounds like the application itself to me. 

yes, you might be right...

> **sgx said:**
> For an .msi installer, from a terminal, type

msiexec -i name-of-installer.msi

This I gave it a try at the 1st beginning, using the command line in the terminal as normally same in Windows you use the *.msi file for a new installation. But its not working, I get a message like this:

> err:virtual:NtMapViewOfSection map_file_into_view 0x330000 20000 000000000 failed
fixme:msi:MSI_OpenDatabaseW open failed r = 8003001e for L"C:\\users\\user\\Temp\\msi1116.tmp"



Dont understand anything of that message ???

> **sgx said:**
> If you have a dual-boot, sometimes you can make a symbolic link
between a windows app/folder/dll and its .wine equivalent, use the
filemanager to drag it, select link, rather than copy or move.

No Dual boot, its a pure Linux mashine... and so it should stay :-) I am tired of Windows, not only because of the money and high licences fees. It eats lot of times away if you install a new system. 

> **sgx said:**
> In wine, your /home/user-name/Documents folder, is the equivalent of
windows C:\Documents and Settings

I think, thats not relevant for me ;-) Or ?

> **sgx said:**
>  If this msi file fails to install, Reaper has simple and effective recording, even a 'save live output to disk', which I use to record broadcasts of the last part of sporting events that I have too little time for. 

Naturally I know Audacity etc. .... but the relevant point is: I use Adobe Audition since 5 years (more than 4100 minutes broadcasting "onair") . I will re-translate all my former shows (round about 70) into different languages, so I cannot start from "0". That's why I want setup an own radio home recording studio.

I will re-edit my former radio shows with Adobe Audition and therefore I need it. Too time intensive, to start a total new editing, that would cost me alone 200 working hours round about less... 

I could record my moderation with a tool like Ardour, then take the WAV files (44100, 16 Bit stereo) and edit it in the Adobe which runs on my Dell Laptop Vista mashine. But I like to record in the LInux mashine using Adobe Audition, too. Not only as editing tool.

Truthfully to say: I am lazy and dont want learn a new editing programme *laugh* . ;-)

---

### Post by sgx on 2011-04-26
Someone on another planet, suggests:

Also if you're not already using the wine PPA I would suggest trying that, you can add it by doing:

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update && sudo apt-get upgrade

Hit the reload button in synaptic, and then check for a newer version of wine to be installed.

Sometimes a downloaded installer has a bad MD5 checksum, and needs 
replacing.  Put the following in a search engine, its a common error,
lots of reading may find a clue

error 2010 "err:module:LdrInitializeThunk Main exe initialization"

If you are out of luck, at least the options can still be used.
Cheers

---

### Post by SenseMaker2011 on 2011-04-27
yes, I have Wine installed... I use latest stable version 1.2.2

> **sgx said:**
> "err:module:LdrInitializeThunk Main exe initialization"

seems I am not the only one with that Adobe Audition troubles...
[http://appdb.winehq.org/commentview.php?iAppId=2538&iVersionId=5869&iThreadId=40119](http://appdb.winehq.org/commentview.php?iAppId=2538&iVersionId=5869&iThreadId=40119)

and the hope becomes smaller and smaller that a solution appears behind the horizon :confused:

---

### Post by SenseMaker2011 on 2011-04-27
yes, of course I have Wine installed... I use latest stable version 1.2.2

> **sgx said:**
> "err:module:LdrInitializeThunk Main exe initialization"

seems I am not the only one with that Adobe Audition troubles...
[http://appdb.winehq.org/commentview.php?iAppId=2538&iVersionId=5869&iThreadId=40119](http://appdb.winehq.org/commentview.php?iAppId=2538&iVersionId=5869&iThreadId=40119)

and the hope becomes smaller and smaller that a solution appears behind the horizon :confused:

---

### Post by barisurum on 2011-04-29
Hi

If you are using adobe audition for audio analysis only, then I can suggest you sonic visualizer, a very similar if not superior free program.

---

### Post by sgx on 2011-04-29
> **SenseMaker2011 said:**
> yes, of course I have Wine installed... I use latest stable version 1.2.2



seems I am not the only one with that Adobe Audition troubles...
[http://appdb.winehq.org/commentview.php?iAppId=2538&iVersionId=5869&iThreadId=40119](http://appdb.winehq.org/commentview.php?iAppId=2538&iVersionId=5869&iThreadId=40119)

and the hope becomes smaller and smaller that a solution appears behind the horizon :confused:
wine has made great improvements recently, well beyond the so-called stable versions. Since it's so easy to do, try the very latest versions. I recently posted x works in wine, but z does not, only to see another users unrelated post somewhere else, saying that x does not work, but z works fine, so you might get lucky. 
Cheers

---

### Post by PHIRUM on 2011-10-08
please help me how to install adobe audition 1.5 on Ubuntu

---

### Post by sgx on 2011-10-09
Hi, in general, you install the latest version of wine,
run the winecfg command in a terminal, and a preferences panel appears,
make desired changes (most people need alsa as the choice in the audio tab.
Now you have a .wine folder in your home folder, and can use the adobe
installer in a simple command:

wine nameOfInstaller.exe   or if it is an msi installer,

wine msiexec -i nameOfinstaller.msi

As noted above, it may not work at this point. If you have an dualboot installation on windows, you can look at where it is installed,
and if you are lucky, copy over all the folders and files to their
equivalents in .wine.

You can purchase a commercial wine called Crossover, which may be your best alternative, as this person said:

[http://ubuntuforums.org/showthread.php?t=921487](http://ubuntuforums.org/showthread.php?t=921487)

Funding Crossover helps the free version of wine, in the long run.

Cheers

if there are a couple specific uses you need that Audition supplies, folks here can suggest linux or other alternatives they use.

---

