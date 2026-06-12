---
title: "WINE does not handle Windows installation (Adobe Audition 1.5) ???"
date: 2011-04-25
forum: Wine
---

### Post by SenseMaker2011 on 2011-04-25
[B]as "[Handy]("http://ubuntuforums.org/member.php?u=55341")" mentioned about my [1st posting in the Ubuntu Forum]("http://ubuntuforums.org/showpost.php?p=10710633&postcount=1"), I should post my original request here... I am new in this forum, same totally new in Linux (since 1981 with Basics, MS DOS and Microsoft on the road). So thanks for your patiency.
-------------------------

my request: [/B]***I please for help herewith !***


Since 5 years I produce (non commercial) radio shows with the editor and recording tool **Adobe Audition 1.5**   . Everybody reading this will understand, that I dont want make myself   confident with new (Linux) programmes, as I am used this great tool  for  audio editing I have broadcasted more than 4100 minutes "onair" now. 

Same I need it, as I want have the chance to re-editing former shows   into some more modern formats. So there is not any reason to switch to   another programme e.g. Adour + JACK or Linux MultiMediaStudio. (I have   installed all on this new Linux mashine to check out. Nice programes,   but actually not really usable for me as it would take me too much time   for learning them. I am lack of time definitely...)

I have found many sources on the web for Adobe Audition installation in   Linux. With WINE it should be possible to integrate "Adobe Audition  1.5"  as I read here and there. I have Wine installed and use latest  stable  1.2 version successfully for "Notepad" and same for  "FreeCommander"  (phantastic File manager under Windows). So Wine works  proper it  seems...

If I click on the [*.exe file of Adobe Audition 1.5]("http://english.p30world.com/archives/002481.php") (or [this one]("http://www.brothersoft.com/adobe-audition-255661.html")) I only get from Wine the message: "**Error reading setup initialization file**". Alternatively I gave a try with a *.msi file. I do not get any response from Wine. 

So what's wrong ? - Any tipp ? - I have searched the whole web for finding help, same here in the forum...
 
- [http://appdb.winehq.org/objectManage...rsion&iId=3665]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3665")
- [http://www.youtube.com/watch?v=48GmSc7GRPc](http://www.youtube.com/watch?v=48GmSc7GRPc)
- [http://ubuntuforums.org/showthread.php?t=1095377](http://ubuntuforums.org/showthread.php?t=1095377)
- [http://ubuntuforums.org/showthread.php?t=921487](http://ubuntuforums.org/showthread.php?t=921487)

But yet I have no understanding what is going wrong ??????????

Is there an alternative to Wine for installing Adobe Audition 1.5 ? -   "Virtual Box" I cannot use, as there is only 10 GB free space now on the   small HD. 

Adobe Audition 1.5 shall be the last programme I want install, nothing   more than pure audio recording/editing. I need always less 5-6 GB for   one single radio show, before I export/backup the datas on an external 4   TB RAID system. So the system is close to the limit (just 10 GB free space of the 40 GB HD) I would say. Would  be very pitty if I fail now with the plan as the whole Linux  system  was setup for only one reason: to use Adobe Audition 1.5 (no  interests  to upgrade it to 3.0 version).

Tks in advance giving attention and your help. Warm regards & Happy Easter/SM2011

---

### Post by brpylko on 2011-04-25
No, Adobe installations do not work in WINE, you need to install on a windows machine and copy the files over.

---

### Post by brpylko on 2011-04-25
Also try running it from the terminal, sometimes (for some odd reason) WINE applications behave differently from the terminal than normal.

---

### Post by SenseMaker2011 on 2011-04-25
> **brpylko said:**
> No, Adobe installations do not work in WINE, you need to install on a windows machine and copy the files over.

Oh....... I should have asked before, hm ? - I wasted hours yesterday trying. Became mad with that problem. 

What do you mean with "*copy the files over*". Yes, I have a fully installation of Adobe Audition 1.5 running on my Dell laptop (Vista). - Or should I 1st install it on my other Windows XP Pro mashine and then copy it from there ?

Can you tell me pls the steps? Tks in advance... Warm regards/SM2011.

---

### Post by SenseMaker2011 on 2011-04-25
> **brpylko said:**
> No, Adobe installations do not work in WINE, you need to install on a windows machine and copy the files over.


With this tip that I should copy an unpacked Adobe Audition from a running  installation in Windows I am little bit a step further. It seems that  wine is trying to install.

But 1st I got following message after using the command "wine Audition.exe":

> user@user-desktop:~/Desktop/Temp/MultiMedia$ wine audition.exe
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\windows\\system32\\audition.exe") not found
err:module:LdrInitializeThunk Main exe initialization for  L"C:\\windows\\system32\\audition.exe" failed, status c0000135So  I installed *msvcp71.dll* in the system32 directory. Same I put a  copy of Audition.exe renaming with little letters into "audition.exe"  and copied into the system32 folder. 

Another try: And I got the message: "**error loading the language modules. Please select another language. If this problem persists you may need to reinstall Audition**".

I took away again the audition.exe in the system32 folder and started  the terminal command "Wine Audition.exe" new. Now I get only one error  message:

"**The product not installed properly**" Again and again same this message. - [COLOR=Blue]What to do ?[/COLOR]

---

### Post by sgx on 2011-04-26
You may confuse the installers .exe file, with the the applications .exe file ?
audition.exe sounds like the application itself to me. For an .msi installer, from a terminal, type

msiexec -i name-of-installer.msi

If you have a dual-boot, sometimes you can make a symbolic link
between a windows app/folder/dll  and its .wine equivalent, use the
filemanager to drag it, select link, rather than copy or move.

In wine, your /home/user-name/Documents folder, is the equivalent of
windows   C:\Documents and Settings 

If this msi file fails to install, Reaper has simple and effective recording, even a 'save live output to disk', which I use to record broadcasts of the last part of sporting events that I have too little time for. Reaper download

[http://reaper.fm/](http://reaper.fm/) 

google points out many many youtubes cover basics of track creation, recording etc and audacity can be used to edit the waveforms.
Cheers

---

