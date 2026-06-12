---
title: "Getting Outlook to work"
date: 2010-09-16
forum: Wine
---

### Post by rmcellig on 2010-09-16
When I launch Outlook 2007, I receive the following error:
"Cannot Start Microsoft Outlook, Cannot open the Outlook window"

I read the following on a post somewhere:
Click Start, run..then type the following: "Outlook.exe /resetnavpane

How would I do this in Wine?

---

### Post by jim.cat on 2010-11-02
I have exactly the same problem. Has anybody found a solution for the "Cannot Start Microsoft Outlook. Cannot Open the Outlook Window"? 
The one that uou say dones not work, the way of doing it in wine is going to a normal linux console and type:

```

$ wineconsole cmd

```

then a windows like console will start and you put what you said in it:

```

C:\Program Files\Microsoft Office\Office12> outlook.exe /resetnavpane

```

However **that has not worked on me** and the error still appear :/

I have tried as well to repair the PST file (wich is actually new but oh well) by using Scanpst.exe

```

C:\Program Files\Microsoft Office\Office12> Scanpst.exe

```

However **that don't work either**.

So don't know what else to do, the errror seems definitively related with the pst file handling since if you go to:
 
```

/home/[USER]/.wine/drive_c/windows/profiles/[USER]/Local Settings/Application Data/Microsoft/Outlook

```

and delete the pst file it just opens and hangs instead of crashing with that error. I have tried as well to replace the newly created pst by the installation for a working one (working in actual windows) but it pops up wit hthe same error....

One solution could be try to start the "Control Panel > Mail" utility where you can handle the PST files and the outlook profiles, however I dont know where to find this utility in wine, or if it even is there.

Any other ideas anybody?

---

### Post by jim.cat on 2010-11-02
Right...

When I said it hangs, it actually pops up with a message to relocate the PST file, but this message is behind the "always on top" outlook splash, so you only can acces to it by Alt+Tab. If you put a new PST file in another location it still not working.

Apart of that I found a way to go to the control panel Mail utility, just go to the linux shell and type:

```

$ wineconsole control.exe

```

I have been playing around with the PST files and creating more profiles. It seems that Outlooks starts OK lets you even chose profile or reallocate the PST file if needed however it crashes at the exact moment that it tries to open the PST file. 
This is not a problem in the PST files since cannot be sorted by the commands explained in the previous post and because it still happening the same when I try to open a PST file that I know for certain that works since I use it with a real windows in a VM :/

It looks to me that it may need some extra library in order to handle correctly the PST files. Does somebody knows which it could be?

Here is my console output if somebody may know what is failing...

```

$ wine "C:\Program Files\Microsoft Office\Office12\Outlook.exe"
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
err:ole:CoCreateInstance apartment not initialised
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:advapi:RegisterTraceGuidsW (0x38ee62e8, 0x4416d0, {77db410c-561e-4358-8b0e-af866e91bb89}, 14, 0x441738, (null), (null), 0x4416e8,)
fixme:process:SetProcessShutdownParameters (00000180, 00000000): partial stub.
fixme:loadperf:InstallPerfDllW ((null), L"C:\\prog~fbu\\micr~hfz\\office12\\1033\\outlperf.ini", 0)
fixme:advapi:RegisterEventSourceA ((null),"Outlook"): stub
fixme:advapi:RegisterEventSourceW (L"",L"Outlook"): stub
fixme:advapi:RegisterEventSourceA ((null),"Outlook"): stub
fixme:advapi:RegisterEventSourceW (L"",L"Outlook"): stub
err:animate:ANIMATE_WindowProc unknown msg 0410 wp=00000000 lp=00000000
fixme:advapi:CreatePrivateObjectSecurity (nil) (nil) 0x32f558 0 0x318 0x3917f380 - stub
err:animate:ANIMATE_WindowProc unknown msg 0410 wp=00000000 lp=00000000
fixme:msctf:TextStoreACPSink_OnSelectionChange STUB:(0x173338)
fixme:msctf:TextStoreACPSink_OnSelectionChange STUB:(0x173338)
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
err:rpc:I_RpcGetBuffer no binding
fixme:advapi:CreatePrivateObjectSecurity (nil) (nil) 0x32f5a4 0 0x5f4 0x3917f380 - stub
fixme:ole:CoSuspendClassObjects 
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Sessions"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00001b58,(nil),0x0006,0x00000000,0x32fcbc,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub

```

---

### Post by TheAnachron on 2010-11-02
May I ask why you want to use Outlook? (Serious question)

---

### Post by jim.cat on 2010-11-02
> **TheAnachron said:**
> May I ask why you want to use Outlook? (Serious question)

hahaha that is a good question LOL

Well just two reasons: 

1 - Have access to my old PST archives of email from years ago

2 - I still manage my phone contacts by syncing them with outlook and so far I have not find a better contact tool for linux, with the sync options that has Outlook.

The number 1 I can do with just having it in the VM but number 2 would be handy to have a quick way to edit my phone contacts... so outlook in wine xD

(are you gonna tell me off now? LOL)

---

### Post by TheAnachron on 2010-11-03
> 1 - Have access to my old PST archives of email from years ago
Well, export them and change the format?

> I still manage my phone contacts by syncing them with outlook and so far I have not find a better contact tool for linux, with the sync options that has Outlook.
Which phone are you using? A windows mobile phone?

---

### Post by jim.cat on 2010-11-03
> **TheAnachron said:**
> Well, export them and change the format?

Well I don't believe that there is out there any more standard format to store emails than PST... 

> **TheAnachron said:**
> Which phone are you using? A windows mobile phone?

I'm using several sonyericsson phones and just got an android one now (so i get to manage yet to stick the contacts in it :P). I very doubt that any other program will let me sync different folders of contacts wit different phones and so on... so I still using outlook :P

And maybe there will be a 3rd reason: I often try to convince people to use Ubuntu instead of Windows (friends and family...) So one of their problems is MS Office so I would like to know how to make it work :) I know how to make Word Excel and PowerPoint work but not bloody Outlook :/ so would be cool to sort that bloody error :) I believe that the unique thing that MS has done well is MS Office :P

---

### Post by thavinci on 2011-02-04
Hi there....
jim.cat: Have you managed to find a way around this? I too desperately need to use outlook for business and cannot get it running....

I entirely agree with your theory on what's causing it NOT too work, however I'm yet to find a solution!

---

### Post by thavinci on 2011-02-04
Just an update:

running ```
wineconsole control.exe
```

i tried to add my email account there to see if it would make any difference. And i notice i cannot as tabs are missing that should b there and it cannot auto find server either....

---

### Post by thavinci on 2011-02-08
Ok, my solution.....

Buy Cross Over Linux 10.0 Standard!

Couldn't waste any-more time and this resolved issue first time!

---

### Post by fontman on 2011-02-10
I'd move to a [K]ubuntu client if I could find one that supports "Profiles" i.e. the ability to set up different sessions for work, pleasure, and other things. That way I don't have to keep changing my default e-mail address for different e-mails and I keep a clean and separate database of e-mails.

---

### Post by redraz on 2012-01-22
> **thavinci said:**
> Just an update:

running ```
wineconsole control.exe
```i tried to add my email account there to see if it would make any difference. And i notice i cannot as tabs are missing that should b there and it cannot auto find server either....

Hi,
I had the same problem with Outlook window not opening.

After installing Office 2007 Enterprise using this:
[http://www.ubuntubuzz.com/2011/09/install-microsoft-office-2007-in-ubuntu.html](http://www.ubuntubuzz.com/2011/09/install-microsoft-office-2007-in-ubuntu.html)

I did ```
wineconsole control.exe
``` and create an email account.
Outlook worked after these steps!
Thanks for the hints!

---

