---
title: "MS Access"
date: 2010-07-17
forum: Wine
---

### Post by H0lyGanGs7eR on 2010-07-17
Hello guys, I installed MS Office 2007 under Wine. I need only MS Access, but it doesn't work. I tryed MS Word and it started correctly, but when I start MS Access I got this error. I got installed Bulgarian language pack with the main one, if this is important. 
[[IMG]http://img695.imageshack.us/img695/2339/13917857.png[/IMG]](http://img695.imageshack.us/i/13917857.png/)

---

### Post by ronnielsen1 on 2010-07-17
It won't start until you do this and then it works

> Currently, Access will install but not start up (bugs 18889 &  1*9297). There are two known workarounds (tested in 1.1.33): 
   **Workaround 1:**(preferred method, as it does not  remove any dependencies)     

   
[LIST=1]
[*]Use a resource editor to extract the manifest from ACEDAO.DLL  (you will find it in the same directory as msaccess.exe). (I used  Resource Tuner; it has a free trial and runs well under Wine.)
[*]Save the extracted manifest as acedao.manifest in the same  directory as msaccess.exe.
[*]Delete or rename the ACEDAO.DLL located in that directory.   (There is another copy in another directory--no need to change it.)
[/LIST]


[http://appdb.winehq.org/objectManager.php?sClass=version&iId=16862](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16862)

---

### Post by dv3500ea on 2010-07-17
I don't know how to fix this problem specifically but just in case you didn't know already there is a good alternative as part of Open Office ([Base]("apt:openoffice.org-base")).

---

### Post by H0lyGanGs7eR on 2010-07-17
I tried the second way, but it didn't happened. Can you tell me please a resourse editor that will run with Wine. I have never worked with this kind of programs.

---

### Post by ronnielsen1 on 2010-07-17
[http://www.restuner.com/download.htm](http://www.restuner.com/download.htm)

> I used  Resource Tuner; it has a free trial and runs well under Wine.)

What I used. It worked great

---

### Post by H0lyGanGs7eR on 2010-07-17
Still got this error. I opened ACEDAO.dll, opened the manifest folder, saved "2" as acedao.manifest, renamed ACEDAO.dll as ACEDAO_0.dll , but still it doesn't work. May be I do something wrong in in Resource Turner?

---

### Post by ronnielsen1 on 2010-07-17
I doubt it. It worked really good for me. Did you place it in the same folder that contains msaccess.exe?

---

### Post by ronnielsen1 on 2010-07-18
Any luck.? If not, I can give more details

---

### Post by H0lyGanGs7eR on 2010-07-18
Well, I wrote what have I done. May be I should say again that i edited msaccess.manifest like in the second way to solve the problem. Is this a problem?

---

### Post by ronnielsen1 on 2010-07-18
> Well, I wrote what have I done. May be I should say again that i edited  msaccess.manifest like in the second way to solve the problem. Is this a  problem? 	
Since it didn't appear to work, I would reedit the file msaccess.exe manifest and copy and paste the text (what I put in red) back in and then save it.

> 
[LIST=1]
[*]Open the file msaccess.exe.manifest* (you should find it in the same  directory as msaccess.exe) in a text editor.
[*]Delete the following:      * *              [COLOR=RoyalBlue] [COLOR=Red]<dependency>
 <dependentAssembly>
 <assemblyIdentity type="win32" name="AceDAO" version="12.0.0.0" language="*"
processorArchitecture="X86">
 </assemblyIdentity>
 </dependentAssembly>*
 </dependency>* [/COLOR][/COLOR]
[/LIST]


> Use a resource editor to extract the manifest from ACEDAO.DLL 

Start Resource Tuner using wine
Open file drive_c\Program Files\Microsoft Office\Office12\
Click Files of Type and choose Library Files (*.dll)
Find ACEDAO.DLL
Click on the Plus sign next to manifest and you should see a file called 2 and a bunch of text in the window to the right if you click on the 2
Copy all of the text to the right and save it to a file called acedao.manifest and place it in drive_c\Program Files\Microsoft Office\Office12\
Rename the acedao.dll file in drive_c\Program Files\Microsoft Office\Office12\ 

It should be working now. You should be able to enter in a terminal wine ~/.wine/drive_c/Program\ Files/Microsoft\ Office/Office12/EXCEL.EXE or in a gui click Applications > Wine > Programs > Microsoft Office > Microsoft Office Excel 2007

But unless you did the following at winehq it will probably stay open refusing to close

> [SIZE=4]_**Post Installation Instructions**_[/SIZE]
   Once installed, one override is necessary. Without it, Powerpoint  and Infopath with not start, and some dialog boxes in other Office apps  will not display correctly. Follow the steps below:      

   Open ***winecfg*** by going to ***Applications  > Wine > Configure Wine***. Or open a terminal and  type:           

   winecfg               

   In the ***Libraries*** tab in the area labeled "*New  override for library*" type in **riched20.dll** and  click on ***Add***.
   You will see it appear in the list below. Now select the **riched20**  in the list that we just added and click on the **Edit**  button.
                  Post-install tweaks  [SIZE=1](updated 2010-04-04)[/SIZE]
   **Note :** Do not file bug  reports for the installer if you have used any native DLLs.
   **Note :**  Beginning with Wine  1.1.42, the Save As PDF/XPS add-in works. Do not install it in earlier  versions, as it did not work and was reported to cause problems with  saving files.
      [SIZE=2]Once installed, the following tweaks may be needed:                                                                                                                                   
[/SIZE]
   
[LIST]
[*][SIZE=2]**Windows Scripting Host (jscript):**     Needed for the thesaurus; install it with winetricks wsh56js. [/SIZE]
[*][SIZE=2]**wingdings.ttf: **Most of the  default bullet characters are from this font; if it is not installed on  your system, Wine will substitute characters from a font that is  installed on your system.                                                                                                                     
[/SIZE]
[*][SIZE=2]**symbol.ttf: **For versions of Wine  prior to 1.1.16, this font must be installed for equations to display  properly[/SIZE]
[*][SIZE=2]**usp10:** Set usp10 to  'native,builtin' in winecfg for the equation toolbar in Word. There is  no need to install it; simply set the override. Do not set this override  globally unless Office is installed in a separate wineprefix.                                                                                 [/SIZE]
[/LIST]


[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

---

### Post by H0lyGanGs7eR on 2010-07-18
I can't edit again the msaccess.exe.manifest, my version was 8.... wasn't the same text. I see in your text MS EXCEL will work, I need ACCESS, are you sure this is the correct way for Access or only for Excel? Actually I tryed MS Excel too, and it works.

PS: I will reinstall may be it will give back the missing text in msaccess.exe.manifest

---

### Post by ronnielsen1 on 2010-07-18
> I can't edit again the msaccess.exe.manifest, my version was 8....  wasn't the same text. I see in your text MS EXCEL will work, I need  ACCESS, are you sure this is the correct way for Access or only for  Excel? Actually I tryed MS Excel too, and it works.

PS: I will reinstall may be it will give back the missing text in  msaccess.exe.manifest 	

I meant access. The same problem is there for access and excel. You still have to edit the file. What do you mean your version is 8?
> Hello guys, I installed MS Office 2007 under Wine.

> **What works**

Creating new DB, tables, forms, reports.                

   Opens normally existings databases with forms, ok to change data.  Queries (and SQLs) work fine.
   Macros quiery lists work well (did well adjusting 4900 entries on  different quieries adding some other hundreds of lines to tables).               

 
**What does not**

 Got problems with some VB things when managing form design (eg, shows  ok-error-message "unable to load dll" when creating button - but you still can manage button-functions like move forward, open form etc.).
   Still you will have to proceed as suggested in [http://bugs.winehq.org/show_bug.cgi?id=19297](http://bugs.winehq.org/show_bug.cgi?id=19297)  (post #27) to run the app (AceDao.dll problem)          

    

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=16862](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16862)

Here's a screenshot of it running

[IMG]http://i80.photobucket.com/albums/j177/ronnielsen1/Screenshot-1-2.png[/IMG]

---

