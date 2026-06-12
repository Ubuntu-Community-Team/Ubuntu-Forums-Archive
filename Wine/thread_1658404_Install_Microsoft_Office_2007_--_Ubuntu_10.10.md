---
title: "Install Microsoft Office 2007 -- Ubuntu 10.10"
date: 2011-01-02
forum: Wine
---

### Post by tij on 2011-01-02
Here's a great tutorial on getting MS Office 2003 (works for 2007 as well) working in Ubuntu. I followed these steps and now have MS Office 2007 running smoothly in Ubuntu 10.10 with Wine. 

[http://www.fewt.com/2008/06/how-to-get-office-2003-running-in-wine.html](http://www.fewt.com/2008/06/how-to-get-office-2003-running-in-wine.html)

Here are some points worth mentioning about the tutorial:

> Once the Office installation completes, perform the following actions (Note: For Office 2007, change OFFICE11 to OFFICE12):

Press Alt-F2 (this brings up a RUN prompt)
Type "regedit" (without quotes)
Click "Run"
Browse to: HKLM\Software\Microsoft\Office\11.0\Common\FilesPaths
Change the path to MSO.DLL to: C:\Program Files\Common Files\Microsoft Shared\OFFICE11\MSO.DLL
Close Regedit

In order to edit the MOS.DLL file as stated above, I had to edited $HOME/.wine/system.reg (the path shown in the tutorial may be outdated). Just search for mso.dll and change the path to "C:\\Program Files\\Common Files\\Microsoft Shared\\office12\\mso.dll"

--I skipped the step where we install the new fonts and it works fine--

> Paste the following and save in your bin directory as "word":

After creating the shell scripts and making them executable (chmod 775 word) I created a blank .doc file (by typing "touch foo.doc" in a terminal) and then ran "word foo.doc". Word ran a config which took a bit, and then complained about my blank .doc file, but everything is running smooth now.

---

### Post by welwitschia on 2011-01-05
> **tij said:**
>  After creating the shell scripts and making them executable (chmod 775 word) I created a blank .doc file (by typing "touch foo.doc" in a terminal) and then ran "word foo.doc". Word ran a config which took a bit, and then complained about my blank .doc file, but everything is running smooth now.

I'm really new at Ubuntu, but I need to get Microsoft Office 2007 in order to be able to read comments in word-files properly (why do they get all messed up in open office?). Unfortunately for example those few sentences quoted above are gibberish to me.

Could someone please write out new "fool-proof" instructions for installing Microsoft Office 2007 based on the above mentioned link and combined with the additional instructions? I can easily follow the old instructions, but am unable to get the desired outcome and I don't know why. I would hugely appreciate the effort...

Thanks

---

### Post by Mr. ViC on 2011-01-05
Why don't you try to install it with PlayOnLinux?

---

### Post by welwitschia on 2011-01-05
nm. Figured it out. Thanks for the PLayOnLinux tip anyway.

---

### Post by welwitschia on 2011-01-06
> **welwitschia said:**
> nm. Figured it out. Thanks for the PLayOnLinux tip anyway.

see here for further information: 
[http://ubuntuforums.org/showthread.php?p=10322781#post10322781](http://ubuntuforums.org/showthread.php?p=10322781#post10322781)

---

### Post by Lism on 2011-01-06
Thanks, hate using open office.

---

### Post by alaukikyo on 2011-01-06
> **Lism said:**
> Thanks, hate using open office.

any specific reason?

---

### Post by Mr. ViC on 2011-01-06
Most of people don't like it because they are not used to using it.

---

### Post by Iksf on 2011-01-06
Use openoffice personally but if MS office wasnt so overpriced would use that, openoffice is really slow to load, has annoying recovery dialogue when start when i just want to do a quick calc in a spreadsheet and eats my documents all the time. If anyone knows how to sort any of those problems would love to know

---

### Post by islander_810 on 2011-01-24
I installed Office through PlayonLinux. Installation completed successfully and I'm able to see the icons under Wine > Programs. 

However, when I try to start it, it displays Office 2007 splash screen and hangs. The only thing that I can do after that is to force quit it.

Anyone else facing the same issue? Any suggestions or solution?

---

### Post by jhoeijao on 2011-01-24
> **islander_810 said:**
> I installed Office through PlayonLinux. Installation completed successfully and I'm able to see the icons under Wine > Programs. 

However, when I try to start it, it displays Office 2007 splash screen and hangs. The only thing that I can do after that is to force quit it.

Anyone else facing the same issue? Any suggestions or solution?

Try opening MS Word first before opening other MS office applications.

---

### Post by islander_810 on 2011-01-24
That worked :D
What's the reason behind it?

---

### Post by cedricf on 2011-01-24
Hello ...

Starting Word 1st worked for me perfectly :), but now I need to activate the product ( I have a legal copy), but I everytime I select activate via the internet I get a communication error message. Any ideas please?

---

### Post by Mama_Bear on 2011-01-24
Anyone know if these instructions would work for Office 2010 as well?

---

### Post by psycho5 on 2011-01-25
As far as I know these won't work with Office 2010, I'm just waiting for playonlinux to release support for office 2010.

---

### Post by beew on 2011-01-25
> **Iksf said:**
> Use openoffice personally but if MS office wasnt so overpriced would use that, openoffice is really slow to load, has annoying recovery dialogue when start when i just want to do a quick calc in a spreadsheet and eats my documents all the time. If anyone knows how to sort any of those problems would love to know

OOO (or LibreOffice) loads fast in all my Linux installations (with different hardware). The reason that MSO loads fast in Windows is that it shares a lot of dlls and what not with the OS so it is in a way started already once you have booted into Windows. It doesn't seem to be that fast on Macs and without WINE it doesn't even run in Linux. So if you try to use MSO in wine for speed you would be very wrong.

You can speed up OpenOffice's,--or LibreOffice's,--load time by opening any document, go to tools > options. Then on the left panel, choose "memory", under undo, set number of steps = 30, under graphic cache,  set use for openoffice.org = 128m, memory per object = 20m. Under cache for inserted objects, set number of objects =20. You should then enable the quickstarter. ( The first time OO.O is loaded after boot would be slower, but subsequent loads would be fast since all the libraries are loaded in the initial launch, you can speed things up further by installing "preload" from the repo)

---

