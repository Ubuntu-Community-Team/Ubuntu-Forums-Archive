---
title: "Can't execute in Wine"
date: 2010-06-03
forum: Wine
---

### Post by bealofull on 2010-06-03
I'm borrowing a very cool old fashioned adventure game (Scratches), but Wine won't run it. 
When I right click the file to run with wine it says:

"*The file '/media/SCRATCHES/setup.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.*"

I then tried to change the permission, to allow executing, but then it says "*Sorry, could not change the permissions of "setup.exe": Error setting permissions: Read-only file system*"
Which apparently is normal, since it is read-only. 

In other threads I found the following solutions which I've tried, but don't work for me:

Code:
wine start AutoRun.exe
code: 
sudo nautilus


code:
wine <drag the executable file in the terminal>

*Do you have wine configured to read from a CD? If not, go into  Applications > Wine > Configure Wine and make sure you CD drive is  listed under the Drives tab. *
--> I believe it is, well, the program complains about me not having a C drive, but it does show my D drive, which is the cd drive. Though I can't browse for executable files in Wine configure, it just won't show any files. 

2) Learn to use the 'cd' and 'ls' commands to navigate to your CD. It'll  be located in something like '/media/cdrom/'. Just try typing cd before  that directory and it'll probably work.
--> I don't really understand this explanation... What does it want me to do?

I hope you creative thinkers can come up with another possible solution, because my fingers are "scratching" to get started.. 

Ow, and I've tried to run a downloaded .exe a while back, and that had the same errors, so I don't think it has much to do with the fact this is from a cd.

---

### Post by mr_black on 2010-06-03
It seems it's s new 'security measure' in Lucid that is getting in the way. The 'executable bit' tells us it won't run any exe that is not marked executable by the user. The user's explicit consent to execute this program is considered making things 'secure'.... Or something... Security is cool huh?

OK.. It's not the biggest problem... Unless... You want to 'exe'cute an exe from CD.... You can't update anything on a CD. And that includes not being able to update the much wanted executable flag.

The last reply in this post led me to a solution: [http://ubuntuforums.org/showthread.php?t=1441988&page=2]("http://ubuntuforums.org/showthread.php?t=1441988&page=2")

I'll rewrite it a bit here:
[LIST=1]
[*]Navigate to the executable and right click on the file
[*]Choose 'Open with other _A_pplication...'
[*]Expand the '_U_se a custom command' section
[*]Enter the command 'wine' (without the quotes) in the newly exposed box
[/LIST]

Now you should be able to start it by right clicking the file, then choose 'Open wit_h_' and finally choose 'wine'. It could take some time before something starts happening, but hang in there :popcorn:

If you want to avoid the righ click procedure mentioned the last paragraph you can make the action the default launch action by:
[LIST=1]
[*]Selecting the file and right click it
[*]Choose 'Properties'
[*]Open the 'Open with' tab
[*]Select the 'wine' option
[*]Close the dialog
[/LIST]

Now all exe files should start like you would start any file.

Hope this helps

---

### Post by 45acp on 2010-06-05
I tried mr_black suggestion and could not get it to work. What good is wine if you can't run an exe from a cd?

---

### Post by bealofull on 2010-06-06
Tried it. It now comes up with a new error message:

"Error. Can't initialise plug-ins directory. Please try again later"

---

### Post by Drenriza on 2010-06-06
> **bealofull said:**
> I'm borrowing a very cool old fashioned adventure game (Scratches), but Wine won't run it. 
When I right click the file to run with wine it says:

"*The file '/media/SCRATCHES/setup.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.*



try right tab the .exe file.
Go to permissions. In the bottom their is a box you can check.
Allow this file to be run as a program. Click ok and close the tabs.

Right click the .exe file and click run with wine.

---

### Post by Lykopis on 2010-06-06
> **Drenriza said:**
> try right tab the .exe file.
Go to permissions. In the bottom their is a box you can check.
Allow this file to be run as a program. Click ok and close the tabs.

Right click the .exe file and click run with wine.

[QUOTE=bealofull]I'm borrowing a very cool old fashioned adventure game (Scratches), but  Wine won't run it. 
When I right click the file to run with wine it says:

"*The file '/media/SCRATCHES/setup.exe' is not marked as executable.   If this was downloaded or copied form an untrusted source, it may be  dangerous to run.  For more details, read about the executable bit.*[/QUOTE] 
Drenriza: he is using a CD-ROM your solution won't work on read only media. 

this solution  from:
[http://ubuntuforums.org/showthread.php?t=1441988&page=2](http://ubuntuforums.org/showthread.php?t=1441988&page=2)  

will fix the problem.
Here's what you need to do to revert the  "open with wine windows program loader" to the old defaults.
[QUOTE=mc4man]
     ```
gksu gedit /usr/share/applications/wine.desktop
```In the .desktop look for line Exec= and change to this, save and  close
     ```
Exec=wine start /unix %f
```[/QUOTE] 
This was what worked for me.

---

### Post by asdfoo on 2010-06-06
> **Lykopis said:**
> Drenriza: he is using a CD-ROM your solution won't work on read only media. 


It does actually, you can modify the exec permissions on mounted read-only media.

---

### Post by Lykopis on 2010-06-06
> **asdfoo said:**
> It does actually, you can modify the exec permissions on mounted read-only media.
Maybe in 9.04 or 9.10 but not in 10.04 Lucid, at least I couldn't on 3 different install CD's
This link also says that read only  exec permissions can't be changed.

[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-January/010487.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-January/010487.html)

If Ubuntu follows the policy below strictly it will render wine almost useless. 
This is Ubuntu's take on it:
From:
 [https://wiki.ubuntu.com/SecurityTeam/Policies](https://wiki.ubuntu.com/SecurityTeam/Policies)
**Execute-Permission Bit Required**

 
[LIST]
[*]Applications, including  desktops and shells, must not run executable code from files when they  are both:
[LIST]
[*]lacking the  executable bit
[*]located  in a user's home directory or temporary directory.
[/LIST]
 
[*]The GNOME or KDE MIME type  handlers must not circumvent this principle.
[*]This includes *.desktop, *.jar, and *.exe files.
[LIST]
[*]Look for .desktop files with [MimeType]("https://wiki.ubuntu.com/MimeType")= and Exec= lines  that do not use "cautious-launcher"
[/LIST]
 
[*]Nothing may provide a workaround to run them anyway  automatically - i. e., never juxtapose <long explanatory text>  with <easy button that bypasses the text>
[*]Files downloaded from a web browser,  mail client, etc. must never be saved as executable.
[*]Files including executable  elements (macros) aren't considered executable for this policy.  Normal  security policies should apply to those kinds of files (i.e. not being  able to impact filesystem, etc).
[/LIST]
 
**Implementation Details**

 
[LIST]
[*]The error message when  trying to open an executable file must:
[LIST]
[*]explain why this may be a dangerous file
[*]not give the option of  launching it anyway
[/LIST]
 
[*]The  error message when trying to open an executable file should:
[LIST]
[*]give the option of looking  for trusted software instead
[*]link to a [web page]("https://wiki.ubuntu.com/Security/ExecutableBit") that  has more details
[/LIST]
 
[*]CDs  without Rock Ridge extensions have all files marked executable, so this  policy doesn't apply (same with USB sticks).
[/LIST]
Also from:
[https://wiki.ubuntu.com/Security/ExecutableBit](https://wiki.ubuntu.com/Security/ExecutableBit)


[LIST]
[*]Security/ExecutableBit
[/LIST]
  Software in  Ubuntu [needs  to be "executable"]("https://wiki.ubuntu.com/SecurityTeam/Policies#ExecutePermissionBitRequired") (sometimes called "trusted"), both in the sense  that the software is a program, and that it is marked as an "executable  file" via [file  permissions]("https://help.ubuntu.com/community/FilePermissions").  Normal software is available for installation via the [Software  Center]("https://wiki.ubuntu.com/SoftwareCenter"); this is the primary source of software in Ubuntu. 
Files downloaded from other locations are not marked as  "executable" since they did not get installed via a trusted software  repository.  Because of this, attempting to open downloaded files that  are software will fail.  The primary reason for blocking this software  is to help unsuspecting users avoid [malware]("http://en.wikipedia.org/wiki/Malware") (i.e. malicious  software like trojan horses, worms, and viruses). 
Ubuntu Policy requires that [software  not marked as executable not be runnable]("https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required").  One of the most common  ways this happens is by having a package ship a .desktop file  for a MimeType which executes the target file  (.EXE, .JAR, etc).  This is not allowed unless the target file is  already executable (or installed by a trusted software repository).

---

### Post by pemadorje on 2010-06-10
I had this same issue with trying to run something from a CD via Wine. I couldn't mark it as executable because it was saying it's a read only media. Thank you for posting some workarounds here. I don't mind taking a few extra steps to work around this, but I have to think that this sure would make things difficult and confusing for a beginner. I mean really, if you are putting a CD in your machine and manually trying to execute a .exe file, then you are implicitly trusting it... When you then get that message, there should at least be an easy way to mark it as "trusted" through the GUI. Not a very user friendly change at all IMHO.

---

### Post by Lykopis on 2010-06-10
I believe the user should be the one to decide if a program is safe or not. To disable the ability to install a program from a CD/DVD is silly. Many of us still use an old Windows program or two. That's where wine comes in.

---

### Post by bealofull on 2010-06-14
I finally installed a tiny windows, so I know play the game in there. 

This seems to work just fine, and as it is just for this game anyway, I'll make the sacrifice of using Windows. 

Lykopsis: I'm a she :p

---

### Post by Lykopis on 2010-06-14
> **bealofull said:**
> I finally installed a tiny windows, so I know play the game in there. 

This seems to work just fine, and as it is just for this game anyway, I'll make the sacrifice of using Windows. 

Lykopsis: I'm a she :p

:lolflag: , and it's Lykopis not Lykopsis. Oh well were all human!!:guitar:

---

### Post by yashoda on 2010-08-10
> **mr_black said:**
> It seems it's s new 'security measure' in Lucid that is getting in the way. The 'executable bit' tells us it won't run any exe that is not marked executable by the user. The user's explicit consent to execute this program is considered making things 'secure'.... Or something... Security is cool huh?

OK.. It's not the biggest problem... Unless... You want to 'exe'cute an exe from CD.... You can't update anything on a CD. And that includes not being able to update the much wanted executable flag.

The last reply in this post led me to a solution: [http://ubuntuforums.org/showthread.php?t=1441988&page=2]("http://ubuntuforums.org/showthread.php?t=1441988&page=2")

I'll rewrite it a bit here:
[LIST=1]
[*]Navigate to the executable and right click on the file
[*]Choose 'Open with other _A_pplication...'
[*]Expand the '_U_se a custom command' section
[*]Enter the command 'wine' (without the quotes) in the newly exposed box
[/LIST]

Now you should be able to start it by right clicking the file, then choose 'Open wit_h_' and finally choose 'wine'. It could take some time before something starts happening, but hang in there :popcorn:

If you want to avoid the righ click procedure mentioned the last paragraph you can make the action the default launch action by:
[LIST=1]
[*]Selecting the file and right click it
[*]Choose 'Properties'
[*]Open the 'Open with' tab
[*]Select the 'wine' option
[*]Close the dialog
[/LIST]

Now all exe files should start like you would start any file.

Hope this helps



Hi Mr Black,  thanks for this suggestion.  Worked brilliantly!  Really appreciate it.

---

### Post by AndyCinDallas on 2010-08-11
Worked great, thank you :D

---

### Post by bhavana on 2010-12-09
> **mr_black said:**
> 

I'll rewrite it a bit here:
[LIST=1]
[*]Navigate to the executable and right click on the file
[*]Choose 'Open with other _A_pplication...'
[*]Expand the '_U_se a custom command' section
[*]Enter the command 'wine' (without the quotes) in the newly exposed box
[/LIST]

Now you should be able to start it by right clicking the file, then choose 'Open wit_h_' and finally choose 'wine'. It could take some time before something starts happening, but hang in there.

If you want to avoid the righ click procedure mentioned the last paragraph you can make the action the default launch action by:
[LIST=1]
[*]Selecting the file and right click it
[*]Choose 'Properties'
[*]Open the 'Open with' tab
[*]Select the 'wine' option
[*]Close the dialog
[/LIST]
Thank you. This helped!

---

### Post by foxmulder881 on 2010-12-26
> **Lykopis said:**
> will fix the problem.
Here's what you need to do to revert the  "open with wine windows program loader" to the old defaults.

<snip>

This was what worked for me.

Thanks. I just installed Neverwinter Nights through WINE and run into this new security issue. Done this solution above and now it's fine. Thanks. ;-)

---

### Post by 1492 on 2010-12-29
If you want to run something in WINE that is on a CD, just click open with other application, then choose "Wine core exe"

---

### Post by foxmulder881 on 2010-12-30
> **1492 said:**
> If you want to run something in WINE that is on a CD, just click open with other application, then choose "Wine core exe"

I think you missed the point. WINE will not execute on later versions of Ubuntu without making some changes.

---

### Post by Silent_darkness1 on 2011-01-06
i actually had this same problem but with WoW.exe. i used the wine command, and got it to work, so i thought. now it keeps crashing cause of ERROR #132 (0x85100084) Fatal Exception
Program:	Z:\media\Windows 7\Users\Public\Games\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:776C008A

The instruction at "0x776C008A" referenced memory at "0x0000000C".
The memory could not be "read".. how do i fix this?

---

### Post by ubun2warrior on 2011-01-06
hi

you can copy the setup file to ur home folder and then open the terminal and type: chmod 777 <filename>.

this also works

regards

---

### Post by Jalokoh on 2011-10-16
> **mr_black said:**
> 

....

[B]I'll rewrite it a bit here:
[LIST=1]
[*]Navigate to the executable and right click on the file
[*]Choose 'Open with other _A_pplication...'
[*]Expand the '_U_se a custom command' section
[*]Enter the command 'wine' (without the quotes) in the newly exposed box
[/LIST][/B]

Now you should be able to start it by right clicking the file, then choose 'Open wit_h_' and finally choose 'wine'. It could take some time before something starts happening, but hang in there :popcorn:

.......






You know what. You're awesome! Thanks alot!

I registered on this forum only to thank you, I've been looking for this all day trying to open Putty.

Thanks again, have a good day <3 :D

---

### Post by Elshentenawy on 2011-10-22
the solution  Is quit simple click properties and permissions and allow executing the file as aprogram It should work then

---

