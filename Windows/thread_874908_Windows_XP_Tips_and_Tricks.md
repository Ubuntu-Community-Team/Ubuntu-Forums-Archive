---
title: "Windows XP Tips and Tricks"
date: 2008-07-30
forum: Windows
---

### Post by macnyak on 2008-07-30
**Speed up WinXP Shutdown**
WindowsXP is probably the most user friendly Microsoft operating system ever but I find it takes forever to load and shut down. Luckily with a few strokes on the keyboard I can make XP shut down much faster. =)
Load up regedit (Start -> Run -> regedit) and follow this path HKEY_LOCAL_MACHINE -> SYSTEM -> CurrentControlSet -> Control. From there find the WaitToKillServiceTimeOut string. Change its data from 20000 (default) to something lower like 10000 or even 5000. Please keep in mind that the computer value used here is milliseconds. After that's done close regedit and reboot your computer.
After this change has been made, your computer will shut down much faster!
[B]
Faster WinXp Booting[/B]
Even though WindowsXP is a fairly fast OS, I often hear people complain about how long it takes to boot up. Not to worry though, there's a simple registry tweak that can dramatically speed up your WinXP boot times!

Click the Start button then go to "Run" and type in "Regedit". Now follow this string HKEY_LOCAL_MACHINE -> SYSTEM -> CurrentControlSet -> Control -> SessionManager -> MemoryManagement -> PrefetchParameters.

Once inside, find the Prefetch string and change the value from 3 to 5. Since the value's are so low, it doesn't matter if you're using Hexadecimal or Decimal.

With this little tweak, WindowsXP should load up between 5-10 seconds faster! 5 seconds doesn't sound like a lot of time, but when you're waiting for a computer to load, it can feel like an eternity! =)
[B]
Faster Menus in XP[/B]
WindowsXP is a great OS, but one pet peeve of mine is how it can be to navigate through each menu, and sub menu. The delay is just long enough to be annoying, but luckily there is an easy way to speed things up if you want.

Click the "Start" button and go to "Run", type "Regedit" and press the the "Ok" button. From there go to HKEY_CURRENT_USER -> Control Panel -> Desktop. Once you're there, go to the MenuShoDelay string and get ready to edit the value which should be "400". To speed up the delay between menu's opening, change this number to 0 and reboot.

After this registry tweak you should notice that menu's pop up instantly when you select them!

**Making NTFS Faster:**
For those of you who use the NTFS file system you can significantly boost your disk access speed in Windows Explorer with a simple registry tweak.
Go to Start -> Run and type REGEDIT. When you're there scroll to HKEY_LOCAL_MACHINE -> System-> CurrentControlSet-> Control-> fileSystem. Once you're inside that folder create a new DWORD Value NtfsDisableLastAccessUpdate and modify the value to 1.
What this does is tell Windows not to update the Time Stamp on the folders of your HDD. That should boost your overall file speed.


[B]
Save Your Eyes, Raising the Refresh Rate:[/B]
After prolonged periods of time in front of the computer, do you get headaches or eye strain? Many times this problem can be traced to the monitor running at a low refresh rate. Luckily this is a rather easy fix. Click on the "Start" button, go to "Settings" and then "Control Panel". Once you're inside there, go to "Display". From there click the "Settings" tab and then the "Advanced" button.
Here in Win9x based OS's go to the "Adapter" tab and you should see the "Monitor Settings". Under that should be a number followed by the "Hertz". The sweet spot is 75 Hz or above and in general you want to get that number as high as possible. In Win2k/XP OS's you want to click the "Monitor" tab. There you'll see "Monitor Settings" and you should do the same as what's written above.
When you press the "Apply" or "OK" button your monitor will blink and you should be set. Now you be able stay in front of your computer for long periods of time and not have any problems!
[B]
Remember to Defrag:[/B]
Have you ever heard your HDD chug along when you launch a large program? Because of HDD's fast rotational speed, they often plunks down data all over the place on the platter of the drives when you're storing information.. This is very inefficient and takes a lot of time when bits and pieces are all over the place.
Defragging your HDD puts all related information next to each other for quicker access and since all the data is in the same proximity the drive doesn't have to search when you request data.
Microsoft has included a defragging program in their OS's for the longest time even dating back to the DOS days. You can access your hard drive defrag program in the "System Tools" folder that is usually in your "Accessories".
It's recommended that you defrag your HDD at least once a month so your HDD doesn't get bogged down.
[B]
Cleaning out the startup junk:[/B]
Do too many programs eat up your system resources at startup? You can simply remove them via MSCONFIG (not available for Win2k).
Go to Start -> Run. There type "MSCONFIG" and press enter.< P >From there you should see a "StartUp" tab. From there you will see a whole slew of check boxes un check whatever you don't want starting up. For Win9x/ME users do not un check "Scan Registry"!
You're not deleting any programs, what you're doing is simply stopping programs from loading at startup. If there's a program that you want to load, simply start it from going to the start menu. You'll notice now that you have many more system resources available for applications now then before!
[B]
Better Mouse Control in Games with WinXP:[/B]
WindowsXP is a great OS, but one problem I find that bugs the hell out of me is Mouse Acceleration. It's especially irritating when I play FPS games. Luckily there's a simple fix for this. Click the Start Button, go to Run and type Regedit .
>From there go to HKEY_CURRENT_USER -> Control Panel -> Mouse folder. Find the SmoothMouseXCurve: and SmoothMouseYCurve: binary value's. Here under the binary SmoothMouseXCurve you'll want to change your value's to look like this...
00 00 00 00 00 00 00 00
00 a0 00 00 00 00 00 00
00 40 01 00 00 00 00 00
00 80 02 00 00 00 00 00
00 00 05 00 00 00 00 00

And change the "SmoothMouseYCurve" values to this...
00 00 00 00 00 00 00 00
66 a6 02 00 00 00 00 00
cd 4c 05 00 00 00 00 00
a0 99 0a 00 00 00 00 00
38 33 15 00 00 00 00 00

After making those changes, reboot your computer. Now load up your favorite FPS game and you should notice you can 'frag' a lot easier!

**Lowering your CAS Latency:**
One of the biggest things you can do to boost your overall system performance is to tune your system memory. When your computer is POSTing (when your memory is being counted) you have to get into your BIOS, usually it's as simple as pressing the "Delete" key, on some motherboards you have to press "F1".
After you're in the BIOS you want to go to your "Advanced Chipset Features". Inside that sub menu's look for "DRAM Timing" or "DRAM Control". Once you find that, look for "CAS Latency" or "CL". On the safe side this is usually set to "SPD" (Serial Presence Detect) but you'll find if you can adjust the value to "2" your overall system performance would go up approx. 5-7%!
Basically what this tweak does is, it forces your memory to run a little more aggressively. It no longer waits as long when addressing and transferring data between the bus, CPU, or other peripherals. You should notice the biggest performance differences in games or anything that heavily taxes your system.

[B]
Loading Windows Into RAM[/B]
While Windows2k and WInXP manage its memory much better then the Win9x based operating systems, you can make both the actual Win2k or XP OS run more efficiently by keeping all of its code in system memory (since it's the most used program) rather than in a HDD swap file.

Go to Start -> Run and type regedit. From there follow this path. HKEY_LOCAL_MACHINE -> SYSTEM -> CurrentControlSet -> Control -> Session Manager -> Memory Management. Right click on the DisablePagingExecutive DWORD value, change its value to 1, save and reboot.

Now Win2k and WinXP will stay in your system memory instead of going into the HDD swap file. Please note, you must have at least 512MB of system memory otherwise you'll notice a slowdown in performance!
While Windows2k and WInXP manage its memory much better then the Win9x based operating systems, you can make both the actual Win2k or XP OS run more efficiently by keeping all of its code in system memory (since it's the most used program) rather than in a HDD swap file.

Go to Start -> Run and type regedit. From there follow this path. HKEY_LOCAL_MACHINE -> SYSTEM -> CurrentControlSet -> Control -> Session Manager -> Memory Management. Right click on the DisablePagingExecutive DWORD value, change its value to 1, save and reboot.

Now Win2k and WinXP will stay in your system memory instead of going into the HDD swap file. Please note, you must have at least 512MB of system memory otherwise you'll notice a slowdown in performance!
Quit Waiting for Windows to Crash
Because I usually have a lot of background programs running I find my computer can get to be really annoying - making me wait Windows to recognize an application which has crashed yet stays in memory. Luckily it's easy to decrease the time Windows waits for an application that has bit the bullet, before it gives you the option to close it.
Load up regedit (Start -> Run -> regedit, then press the ok button) and follow this path. HKEY_CURRENT_USER - > Control Panel -> Desktop and inside there find the HungAppTimeout string value. The default value is 5000 milliseconds (5 seconds) and you can change that to whatever you'd like but please remember that any value you input is in milliseconds, myself I set that to 2000 ms (2 seconds).

Now Windows waits about 2 seconds before it gives me the option to end task that has crashed. Now if "they" would only find a way of stopping THAT from happening!
Prioritize Processes:
This is so simple it’s not funny, but it leads into the next tweak... anyway, if you press Control+Alt+Delete, then click on the ’Processes’ tab, you should get a dialog like the one above. You can see a list of all the processes running at the time. Now, if you are running a program that you want to dedicate more processing time to - eg, 3D Studio Max, as in my example, you can just right-click on the process, move your cursor down to ’Set Priority >’, then select how high you want that program prioritized. While I’m checking my email, I might want a Normal priority for Max, but if I leave my Computer, I can increass it to ’RealTime’ to get the most rendering done. Easy!
Raise your AGP Aperature Size:
There are many reasons and many ways to solve it. If you have little system ram it could be a problem. even if your vid card is 16mb, by getting for system ram, you can boost overall system performance and video.
you say, "I have 256mb ram, but everything loads so slow in games"
That's because you have no set your agp aperture size in you bios to at least have of your total memory of your system. In this case you would set it to 128mb. Basically agp aperture size decides how much your system memory your video card is allowed to hog and use to cache textures, game data and other stuff.
To solve this problem, get a download browser, that will cut your file into small little pieces to download, because as you might have noticed, when your downloads starts it fires up to 1mb/sec but after 5 sec its back to like 200kb/s, that's probably because your ISP has capped u after they detected your bandwidth hogging transfer. That's why you get a program that splits your download into little pieces =)
Enable DMA on CD-RW's:
problems leading to coasters
1) you have little ram
2) many background apps running
3) YOUR DMA IS NOT ENABLED FOR YOUR BURNER!!!!!!!!!!! <---most important
To enable your DMA for your burner/hard drive/anything that is IDE!! simply go to system info in control panel, then go to your hardware device manager. Now look for IDE ATA/Atapi controllers in your list of devices. double click and your should see primary controller and secondary and master controller.
Primary being your first IDE channel, and secondary your second channel, double click primary or secondary if the device u want to enable dma is in there, then go to advanced settings tab, and select dma if available for them all, you usually don't want PIO mode ever

**CD 2 CD = Coaster?**
When you are experiencing problems cd to cd copying, without first buffering an image to the hdd, its because.
1) you have little ram
2) dma is not enabled for either of your cd-rom/writer/dvd drive
3) your read speed is not at least twice as fast as your burn speed
and lastly the biggest problem: both your cd rom/writer/drive is connected to the same IDE channel, causing loss of data because the ide channel cannot handle all the data.
Solution: simply switch one drive over to a different IDE channel
[B]
Windows Tile Trick:[/B]
This one is to get you started,
Run "regedit" from Start->Run under Windows. Search the registry for HKEY_CURRENT_USER\Software\Microsoft\Internet Explorer\Main\Window Title
If the Window Title string does not exist, create a new string with that name! Edit the key value to read "Internet Explorer Provided by CHE on the loose! *Spit* YEAH!!@@##"(an Example). That is now the title which will be displayed at the top of your Internet Explorer window. It may be kinda boring on your own machine, but it's a fun trick to play on your friend or your boss Can you change the window title for Outlook Express? Windows of other programs? Try and see Warning: Messing with your registry can hose your operating system yadda yadda yadda...make sure you back up the registry first and know what you are doing. Warning #2: Screwing around with your boss' computer can be hazardous to your career.

**Killing Pop-up Windows Messages**
Quite a few people have e-mailed me asking how to get rid of those pesky SPAM-type messages that pop-up through the Windows Messenger Service. These messages appear for those of you who use Win98/NT/2k/XP operating systems. Please keep in mind though, Windows Messenger Service is not the same as MSN Messenger, or Internet Explorer for that matter. Windows Messenger Service is built into the operating system and it was intended to allow network admin's talk to the other users on the network.

To actually send a 'Windows Messenger Service' message users need to open up DOS and type "net send", the IP address where the message should be sent to, and the message itself. For example; typing "net send 192.168.1.6 My Computer is the fastest!" would send the message "My computer is the fastest!" to the computer on IP address 192.168.1.6

Anyway, getting back to those spam messages; luckily this is one of the easier things to disable. First make sure the account you're logged in with has Administrative access. Then go to Control Panel > Administrative Tools > Services. From there scroll down to the 'Messenger Service' and disable by changing 'Startup Type' to 'Disabled,' then exit. After that's done you'll no longer get those pesky Windows Messenger pop ups!
[B]
Speed up your LAN[/B]
Most of the time when we are transferring large files over a LAN the network will never reach maximum theoretical throughput speed. Luckily for us, adding two DWORD value strings can sometimes greatly improve network data transfer performance!

First load up regedit (Start -> Run -> regedit -> Ok) then follow this path. HKEY_LOCAL_MACHINE -> SYSTEM -> CurrentControlSet -> Services -> Lanmanworkstation -> parameters. Now create (or modify) the MaxCmds and MaxThreads DWORD value strings. You can give it any value between 0 and 255, it's up to you to experiment to see what works best for your network. For my home network I find that giving it a value of 155 on all computers boost network throughput a bit.

If you RUIN your network settings simply delete the two DWORD strings and start over.

**Forget your Password?**
I'm don't know about you, but I'm very forgetful. I always lose my keys, my wallet and I always forget my passwords! Thankfully, WindowsXP has a little built in feature that can help you if you forget your password, or more accurately, want to make sure you don't forget it!
You can make a password reset diskette by going into your "Control Panel" and opening up "User Accounts". Inside there find "Prevent a forgotten password" and once you found it, follow the instructions. Make sure you have a floppy in the drive and put it in a safe place - hopefully one you won't forget!
Now when you enter your password incorrectly Windows will prompt you for a the disk. This only works for computers which are not part of a domain, so it's best for your home PC where the IT department are never to be found.
[B]
Remove Windows Delay:[/B]
HKEY_CURRENT USER\Control Panel\Desktop. Create a new string called MenuShowDelay, or modify the existing one if present, by right clicking and selecting modify. enter a value from 0 to 999 (milliseconds).

**3 Easy Ways to Improve Dial-up Modem Performance:**
1. You can't assume that just because you connected at a speed like 48.3KBps that you will stay there. Today's modems automatically fall back to a lower speed if the line noise is too high to maintain a faster connection, but sometimes they fall back too soon or too far.
Here's how to do it:
Click Start the button.
Select Settings.
Click Control Panel.
Double-click on the Modems icon.
Select your modem.
Click the Properties button.
Click the Connections tab.
Click the Advanced button.
In the "Extra settings" field, type S36=7
Click OK to save your settings.
This will force your modem to try to stay connected at high speeds in two different ways before dropping back to an asynchronous mode with auto speed buffering.

2. With Windows 95 and 98, there is an easy way to increase the speed at which you connect to your ISP. To do this:

Click the Start button.
Select Settings.
Click Control Panel.
Double-click on the Modems icon.
Select your modem.
Click the Properties button.
Click the Connections tab.
Click the Advanced button.
In the "Extra settings" field, type S11=50
Click OK to save your settings.


3. If you are experiencing a lot of modem timeouts with your system, you can change the SLOWNET value in the Registry

Click Start the button.
Select Run.
Type "regedit".
Go to HKEY_LOCAL_MACHINE\System\CurrentControlSet\Servic es\Class\Net\0000 (0001 etc).
Change the SLOWNET value from 01 to 00.

If you suffer from random disconnections using your modem, you can improve reliability by using the following modem init strings.
Place the following values into your modem init string:

&U15&N15

This eliminates retrains

You might also try:

S10=30 or even S10=50

(all modems) as this gives protection against line drops due to short noise bursts or carrier interruptions.

Faster Boot:
When you boot your WinXP home box, does your system hang for a looooooong time after the desktop appears?? You try and click on items and nothing happens? Then all of a sudden, all those things that you clicked on during the hang start to load and pop up?
I had this problem with my computer, and I have seen it in others. It took me awhile to find a solution, so I want to share it with as many as possible.....

1. Click START/RUN
2. Type msconfig
3. Click OK
4. Click the SERVICES tab
5. Scroll down to find a service called WORKSTATION
6. Uncheck this service
7. Click APPLY
8. When prompted, Restart

With any luck, you will just have cut your boot time in half, just like I did for my computer and for others'.
When the System configuration utility appears, if this worked for you, click the box that says "Do Not Show This Message Again". If this causes something bad to happen, immediately repeat the steps above except put a check IN the box on step #6.

I cannot say if this will work in XP Pro because I have not tested it. If anyone tries I would love to know if it worked.


Taking Screen Shots in Windows
I often want to make a copy of the screen for safe keeping, or to send to someone. To do this manually is quite easy.

1) Press the 'Print Screen' key on the keyboard when you want to take a snapshot of the screen to keep. 2) Go to START > PROGRAMS > ACCESSORIES > PAINT to open the program. 3) Click Edit > Paste. If your using Win98 like me and are asked if you would like the bitmap enlarged Click Yes.

The image of the screen will appear and you can now use the 'Select' function in the 'Tool Box' to capture the part of the screen you want keep. 4) Once selected, go to Edit > Cut. 5) Then go to File > New and when asked if you want to "Save changes to untitled?" click 'No.' 6) Go to Edit > Paste and the same bitmap message may appear. Click Yes. Now just the part of the screen you want to keep is displayed, allowing you to save it as an image file for what ever you want it for.

Making your HDD more Secure in WinXP
There's a very neat trick in which you can setup ownerships on hard drives within WindowsXP. This is extremely useful if you have important or sensitive data on a certain drive and do not want anyone else to access it!

Go to your "Control Panel" and click the "Administrative Tools" icon. From there go into "Computer Management" and then find "Disk management". Once you're there, right click on the disk which you want to claim ownership on and go to "Properties". Click the "Security Tab", then the "Advanced" button. You should see an "Owner" tab and when you're inside there, select the owner you'd like.

After this is done, only that user will be able to access the HDD and your data is secure. Please keep in mind, you must use a NTFS partition to use this trick!

Speed up HDD Access
This tip is for those of you who work with large files or HDD intensive programs. Did you know that you can optimize your file allocation size for a bit more performance? Well you can. Now, everyone knows how frustrating it can be when you're waiting for a large photoshop file to load thanks to the slow HDD, but there is a tweak for this.
For users of Win2k/XP, load up regedit (Start, Run and type regedit). Follow this path HKEY_LOCAL_MACHINE -> System -> CurrentControlSet -> Control -> Session Manager -> Memory Management. Inside there add the DWORD ContigFileAllocSize and and modify it's value to 512 while using decimal base. After this modification, you will have to reboot and defrag your HDD. Once everything is done, you should notice your HDD intensive apps run just a bit faster.

Disable Those Pesky Balloons
I think WindowsXP is the best and most reliable Windows operating system to date, but there are still quite a few quirks that can be annoying to deal with. The next few tips are require registry tweaking so load up regedit (Start -> Run and type regedit then press the Ok button).

I find the balloon tips very annoying, and luckily turning them off is pretty easy. With regedit loaded up, follow this path. HKEY_CURRENT_USER -> Software -> Microsoft -> Windows -> Current Version -> Explorer -> Advanced. Create an EnableBalloonTips DWORD and set its value to 0 to disable the balloons.

For the more advanced users out there, you know well how much free space is on your HDD so you don't need the OS reminding you that you're running out. To disable the low disk space notification go to HKEY_LOCAL_MACHINE -> SYSTEM -> CurrentControlSet -> Services -> lanmanserver. Inside there create a DiskSpaceThreshold DWORD and set it to 0.

Do you have some old applications that just won't install on XP but work fine in 2k or 98?
You can trick the software into thinking you're running an older OS by changing a few registry keys. Go to HKEY_LOCAL_MACHINE -> SOFTWARE -> Microsoft -> Windows NT -> CurrentVersion. Inside there change the ProductName string value to Microsoft Windows 2000 (default is Microsoft Windows XP) if you want to install a Win2k only application. Please note, sometimes you may need to change the CurrentBuildNumber string value as well.

Disable the Disk performance counter(s)
Windows XP contains a built in performance monitor that is constantly examining various areas of your system. This information can be called up using the performance monitor application found in control panel\administrative tools. Of course, most of us have little interest in this sort of performance statistics monitoring, that being more the territory of systems administrators than individual users.
The thing is, XP is still monitoring away, and some of its observation tools can use a considerable amount of resources. The disk monitoring is an example of this, and it's a good idea to turn the disk monitors off if you are not planning to use the performance monitor application.
To do this: Go to the command prompt ('start\run' then type 'cmd') and type 'diskperf -N'

Turn Off Windows Indexing service
The 'Indexing' feature is used to increase the speed of file searches within XP by creating and updating an index of all files on your system. Unfortunately, it also reduces the performance of your system, since it is constantly working in the background.
To turn it off: Go to Control Panel\Add/Remove Programs\Windows Components. Then uncheck 'Indexing Service.'

Mouse Sonar
Here's a good little tip for users who have trouble locating their mouse pointer on the screen. Windows XP has a nifty little 'mouse sonar' option available, which will cause your mouse pointer to pop-up a little concentric ring around itself to show you where it is.
Go to 'start\control panel\mouse' choose the 'pointer options' tab and check the 'show location of pointer when I press the control key' box.

Mount a new hard drive as a folder in your C: drive
Actually, this tip works for any partition of any NTFS formatted drive (except the partition with the Windows system files on it)… Windows XP, like 2000 before it, allows you to 'mount' drives as folders in a pre-existing logical drive. For example, if you had a computer with a 20GB disk formatted into a single partition and volume (drive c , you could purchase a second drive, partition and format it from disk manager and then instead of giving it its own drive letter, add it to your c: drive as a directory. Any files added to that directory would of course be stored in the new HD.
This can come in extremely handy, as certain applications (databases come to mind) can grow extremely large, but may not support storing data on a (logically) separate drive.
As far as Windows is concerned, a drive mounted as a directory is just a directory, so no extra drive letters are involved. This can also cut down on storage confusion for the average user, and it's easy to do, though it can only be done with NTFS formatted partitions, and obviously the boot partition cannot be used this way, though other partitions can be added to the boot partition.
Also note that shuffling the partition around in this way has no effect on the data stored in it. You can move an NTFS partition from directory to directory, then give it back a drive letter if you choose, while maintaining complete access to the data inside. No reboot is necessary. One other note: If you have installed software on a partition you plan to mount as a directory, it is best to uninstall and reinstall it, since the move may stop the software from working correctly. Windows will warn you about this if you forget my wise words.
To mount a partition as a directory: Open disk manager, the right click on the partition you wish to mount as a directory in the graphical partition window (lower pane). Select 'change drive letter and paths…'
Remove the current option (if any), then click add.
Choose the 'mount in the following empty NTFS folder,' browse to the desired volume and add a directory for your drive. Click 'ok.' That's it.
If you wish to return things back to the way they were, simply repeat the procedure, removing the directory location and choosing a drive letter instead. The data on the drive will be unharmed.

Bypass the recycle bin when deleting a file
If you do not wish a file or folder you are deleting (or a group of files or folders) to end up in the recycle bin, for security or privacy reasons, there is a simple keyboard shortcut to avoid it.
To bypass the recycle bin when deleting a file, press and hold the SHIFT key as you press delete or select the delete command from the menu. You will see a request for confirmation, and once you say 'yes' the files will be permanently deleted, and absolutely non-restorable from WindowsXP.

Create a link to shutdown your PC
To create a useful link desktop link to shutdown or restart your PC, follow these directions:
Right click on an empty area of your desktop, then select 'new' and 'shortcut' to open the new shortcut wizard.
When prompted for the location of the shortcut, enter 'SHUTDOWN -s -t 01' to shutdown the system or 'SHUTDOWN -r -t 01' to restart the system.
Name the shortcut and give it an appropriate icon from the '%SystemRoot%\system32\SHELL32.dll' location.
You now have a quick shortcut to shutdown or restart your system! Perfect for getting out of the office right at 5:00PM on the dot!

Creating a desktop shortcut for locking your computer
If you use your computer in an area where others may have access to it, and there are things on your system you would rather have kept confidential, locking your desktop when you leave the computer is an essential task. Here's a recipe for a desktop shortcut that will lock your computer in two easy clicks:
Right click on an empty area of the desktop and choose 'new' then 'shortcut.' The create shortcut wizard will open; in the first text box, type '%windir%\System32\rundll32.exe user32.dll,LockWorkStation' and then give your shortcut an appropriate name on the next page, and hit 'finish.'
You will notice that the shortcut you created has a blank icon. To select a more appropriate one, right click on the shortcut and hit 'properties.' In the 'shortcut' tab, click the 'change icon' button.
In the 'look for icons in this file' box, type '%SystemRoot%\system32\SHELL32.dll' then click 'ok' to see a range of icons for your new shortcut. Choose an appropriate icon. Your desktop locking shortcut is now ready for use. Test it out.

Stop Windows messenger from running
Windows XP was the first of Microsoft's operating systems to include a built in instant messaging application, the Windows Messenger (a variant of Microsoft's popular MSN Messenger service). Unfortunately for those who don't use instant messaging services, the program is extremely difficult to avoid, especially if you use Outlook Express as your mail client.
By default, Windows Messenger is started each time windows starts, and will attempt to log you in as soon as you connect to the internet, and every time you start Outlook Express. Worse yet, it will reappear when you start Outlook Express even in you have uninstalled it. With a combination of steps, you can disable Windows Messenger, though it is not really possible to actually remove it from the computer.
Let's look at how to do this: To stop Windows Messenger from reappearing each time you start Outlook Express, open OE then go to 'tools\options' and uncheck the 'automatically log into Windows Messenger' box. Close OE, exit from Messenger and also close any browser windows.
Now you need to find out if you have Service Pack 1 for Windows XP installed. If you are not sure, right click on 'my computer' and select 'properties.' In the first Window under the system heading, your version of Windows XP will be shown. If you do have service pack 1 installed, simply go to 'start\control panel\add/remove programs' to remove the messenger service.
If you do not, go to 'start\run' and type 'RunDll32 advpack.dll,LaunchINFSection %windir%\INF\msmsgs.inf,BLC.Remove' To remove the program.

Keep Windows operating data in main memory
Windows XP contains several tweakable memory settings in the registry, one of which is the DisablePagingExecutive registry key. This controls whether the operating system will transfer its essential driver and kernel files to the 'virtual memory' (the page file on the hard disk). It defaults to allowing this.
Obviously, transferring portions of the system to hard drive memory can considerably slow things down, and it appears that Windows XP does this periodically, whether or not the system is actually low on physical memory (RAM). If you have 256MB of system memory or more, try this registry tweak to force Windows to keep its operating data in main memory:
Open Regedit.
Navigate to HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Se ssion Manager\Memory Management.
Select the DisablePagingExecutive value to '1'

Restarting Windows without have to restart PC!
For those of you who are extremely impatient there's a way of restarting Windows without having to restart the actual PC... I know this has saved me a bit of time when trying out new registry tweaks and such.
First load up regedit (Start -> Run then type regedit and click the ok button). From there follow this path HKEY_LOCAL_MACHINE -> SOFTWARE -> Microsoft -> Windows NT -> CurrentVersion -> Winlogon. From there add/modify the EnableQuickReboot string value and change it to 1. Save exit and reboot your PC normally.
After that's done every time you want to reboot simply press Shift + Ctrl + Alt + Del and Windows will do a quick restart without rebooting.

Removing Windows Key in Game Play
The Windows key on the keyboard can be very handy, but it can also get in the way when playing FPS games. On more than a few occasions I've hit that button by accident, causing me to drop back to Windows desktop, and get killed in the game. Should this happen when you're playing competitively online it can seriously affect your rankings!
Luckily it's something that can be fixed with a simple registry tweak, first load up regedit (Start -> Run -> Regedit then press ok) and follow this path HKEY_LOCAL_MACHINE -> SYSTEM -> CurrentControlSet -> Control -> Keyboard Layout. Once you're there right click and create a new binary value.
You'll want to edit its value and enter this...
00 00 00 00 00 00 00 00 03 00 00 00 00 00 5B E0 00 00 5C E0 00 00 00 00
Save, then reboot your PC. After that's done you should notice that the windows key *no longer functions* which I'm sure is good news to some of you out there. This works in all versions of Windows.

Stop the 'last access update' from taking up system resources
Every time a directory on an NTFS drive is accessed by Windows XP, it updates that directory and every subdirectory with a time stamp to indicate the date of access. In folders with a lot of subdirectories, this can add considerable overhead to whatever your PC happens to be doing. This process can be disabled through the registry:
Open REGEDIT
Navigate to HKEY_LOCAL_MACHINES\System\CurrentControlSet\Contr ol\FileSystem.
Create a new DWORD value called 'NtfsDisableLastAccessUpdate' and set the value to '1'

Increase downloads in IE
To surf the web I use Internet Explorer; I guess I should support the "little guys" but I don't because of the compatibility problems that sometimes arise when using a third party browsers. One thing I find annoying about IE is it only allows you to download two files at a time! This can be a serious bottleneck if you plan to download multiple files though IE. Naturally, there's a registry hack that fixes this up to a maximum of ten simultaneous downloads.
First load up regedit (Start, Run then type regedit and press ok) and follow this path:
HKEY_CURRENT_USER -> Software -> Microsoft -> Windows -> CurrentVersion -> Internet Settings. Right click on the right hand window and create a two new DWORD values...
MaxConnectionsPer1_0Server
MaxConnectionsPerServer
Give each a value of "0000000a" then save and exit. You might have to reboot for this tweak to come into affect. After that's all done, you should notice that you can now download more than two files at a time.

CPU Utilization
One of my many pet peeves about WindowsXP is how CPU utilization goes up to 100% when viewing AVI files. When this happens it slows the rest of the system to a crawl. As always though, there's a registry hack that can solve this problem, you just have to know where to look!
Load up regedit (start -> Run then type regedit and press the Ok button) and follow this path HKEY_LOCAL_MACHINE -> SOFTWARE -> Classes -> CLSID -> {87D62D94-71B3-4b9a-9489-5FE650DC73E}.
Once you're there delete the key then save and exit. Once that's done AVI files will no longer suck up all the CPU resources.

Delete protected files in Windows
When it comes to my PC I like my files and folders nicely organized. A messy 'Program Files' directory or weird folders in the root directory of my hard drive are not going to cut it. Windows though, protects certain files and folders from deletion. I know I don't need them, and they're not loaded into memory, but Windows still refuses to let me delete!
There's a registry tweak that can bypass this little problem of course. First load up regedit (Start -> Run then type regedit and press the ok button) and follow this path HKEY_LOCAL_MACHINE -> SOFTWARE -> Microsoft -> WindowsNT -> Current Version -> Winlogon. >From there find the SFCDisable binary value and enter this hexadecimal value FFFFFF9D (decimal value = 4294967197), after that's done save and reboot your PC.
Now you'll be able to delete whatever file you want on your PC and you won't have to hear Windows complain about it. = ) A warning though, this tweak is intended for the more experienced computer user who knows which files are important, and which are not! if you delete the wrong file, it's possible you can destroy the OS, which would require a reinstallation!

Setting Services
This tweak is more for the experienced computer user who can identify services by Microsoft's abbreviations.
First load up regedit (Start -> Run then type regedit and press the ok button) then follow this path HKEY_LOCAL_MACHINE -> SYSTEM -> CurrentControSet -> Services. Inside that folder you'll find all the folder names for all the services that run in your PC, browse the one that you want to edit then find the Start binary value. Entering a value of 2 sets the startup to automatic, a value of 3 is manual and a value of 4 is disabled. Once you've made those changes save and reboot your PC.

Clean out temporary folder
We all know how messy Windows is when it comes to temporary files, but that doesn't mean we can't do something about it. Users of WindowsXP Pro can force the OS to clean up after itself. First click Start, then Run and type in "gpedit.msc", that will open up the Group Policy editor (Note you must have administrative access).
From there follow this path Computer Configuration -> Administrative Templates -> Windows Components -> Terminal Services -> Temporary Folder. Open up the attributes for the "...Temp Folder Upon Exit" and select disable. After that's done, close the Group Policy editor and from now on when you turn off your PC, Windows will clean out its temporary folders.


Make you PC an Alarm Clock
I don't know about you, but I don't like waking up to a beeping alarm every morning. Since I leave my PC on 24/7, I decided to make it my "new alarm clock" by waking me up to my favorite tunes!
What you want to do is drag and drop your M3U playlist (which can be created by Winamp, WMP, etc) into the Scheduled Tasks folder found in your System Folder (Start -> Programs -> Accessories -> System Tools -> Schedule Tasks). From there open it up, click the "Set Password..." button and enter your login password then click ok.
Now click on the "Schedule tab" and set the time which you want you PC to wake you up and then click ok and your PC will now wake you up at that time! Of course if your PCs clock doesn't tell the right time, this won't work

Password for Guest account in XP
Have you ever wanted to password protect the 'Guest' account within WindowsXP? By default Windows disables any form of password protection for that account, but it is possible to tweak the OS to allow for one.
First load up your command prompt (Start -> Run then type "cmd" and press enter), that will bring up a small black window with a DOS prompt. From there type "net user guess password" and press enter, you should then see "The command completed successfully." Once that's done exit the prompt and load up your user accounts and you can now enable and set a guest log in password.

Improve memory management
While WindowsXP handles memory management much better than Win9x based OS's, there is always a way to improve things. If your PC has multiple HDDs, what we want to do is move the OS swap file from the main HDD to one of the secondary HDDs. It's true that the primary drive is usually the fastest for running software, but it's also the most busy. Moving the pagefile or swapfile to a drive with less activity should help speed up the PC.
To do this, right click on the "My Computer" icon and select "Properties", from there click on the "Advanced" tab then under the Performance section click on the "Settings" button. That will open up a new Window, from there select the "Advanced" tab yet again, and under Virtual memory click the "Change" button.
Under the "Drive [Volume Label]" window you should see all your HDD's - note that by default WinXP places the pagefile on the primary drive. Because we need to clean the pagefile of any anomalies and corruption first, click on the "No paging file" radio box then press the "Set" button, then click ok. Once the PC restarts go back to the same place and look under "Drive [Volume Label]", select your secondary HDD and check the "Custom Size" radio box. For initial size enter them amount of physical memory your PC has; if you have 1GB of RAM, enter 1024. In the "Maximum size" box enter double your physical memory + initial size pagefile. In our case it would be 2GB (or 2048MB). Click set, then "ok" and reboot. Once that's done, defrag the hard drive that contains the swap file and you should notice a decent performance boost within WinXP.
Remember, never disable the pagefile even if you have a lot of system memory (1GB+), WinXP requires it to function.

---

### Post by fiddledd on 2008-07-30
It would have been easier just to post a link to the original site that published that text.

---

### Post by MaxIBoy on 2008-07-30
I can't find some of those parameters.

---

### Post by fiddledd on 2008-07-30
> **MaxIBoy said:**
> I can't find some of those parameters.

That's because all the text the OP pasted was published by PCStats Newsletter IIRC in about 2006, and we are now on SP2 and 3.

EDIT: If you tried any of those hacks I hope you backed up the registry first.:)

---

### Post by fiddledd on 2008-07-30
I should have posted this sooner, please backup your registry and if possible image your Windows partition before messing with the registry. As I said, I'm pretty sure this information was posted a couple of years ago by PCStats and other places too. I apologise to the OP if I'm wrong about this, but if you look [here](http://www.putera.com/tanya/lofiversion/index.php/t39475.html) you'll see the same text referenced last year. The point is some things have changed in XP since the original text was published, so apply the hacks at your own risk. :)

---

### Post by LinuxRocks713 on 2008-07-31
Pure piece of copyright infringement and fraud.

---

### Post by fiddledd on 2008-07-31
Yeah, my finger has been hovering over the report button since it was first posted. But I'm not sure if that's the correct thing to do, so I just posted a warning in the thread about the info being out of date.

---

### Post by schmidtbag on 2008-09-06
ya this is a bit much about windows for 1 person to write for ubuntu forums.  altho i think these are some awesome tips, i would rather have the actual link

---

### Post by fiddledd on 2008-09-06
> **schmidtbag said:**
> ya this is a bit much about windows for 1 person to write for ubuntu forums.  altho i think these are some awesome tips, i would rather have the actual link

I posted the link to the referencing of it in post #5 in this thread. The original article is a bit harder to find, because it's old and has been archived. You'd probably have to login to the archives on PCStats website to access it. I'm not hunting for it because it is 2 years out of date.

---

### Post by Canis familiaris on 2008-09-06
> **LinuxRocks713 said:**
> Pure piece of copyright infringement and fraud.

Isn't this called Plagarism?

---

### Post by BenAshton24 on 2008-09-06
> WindowsXP is a great OS
Thats it, i'm off, bye!

---

### Post by Primefalcon on 2008-09-06
it would of been fine if that actually said where they got it from

---

### Post by BLTicklemonster on 2008-09-07
Yeah, the OP ought to have said, this is from here, and put a link there at the end of the post.

---

### Post by fikelfikel on 2008-10-26
I appreciate the the great tips, but just remember, this is "Ubuntu Forums", not "Win XP Forums". I think if you join Microsoft Forums, the would be glad with it.

I used to be an 98, 2000, XP and Vista user, but then I changed to a more securer platform, Ubuntu. It does take a lot of time for XP to load alright!

---

### Post by BLTicklemonster on 2008-10-26
Well, this is in the >Other OS Talk > Distributions> Windows Discussions portion of the forum, so I don't think anyone is gonna like arrest anybody.

---

### Post by BLTicklemonster on 2008-10-26
Is there an equivalent of this for Ubuntu? Other than lomoco?

> Better Mouse Control in Games with WinXP:
WindowsXP is a great OS, but one problem I find that bugs the hell out of me is Mouse Acceleration. It's especially irritating when I play FPS games. Luckily there's a simple fix for this. Click the Start Button, go to Run and type Regedit .
>From there go to HKEY_CURRENT_USER -> Control Panel -> Mouse folder. Find the SmoothMouseXCurve: and SmoothMouseYCurve: binary value's. Here under the binary SmoothMouseXCurve you'll want to change your value's to look like this...
00 00 00 00 00 00 00 00
00 a0 00 00 00 00 00 00
00 40 01 00 00 00 00 00
00 80 02 00 00 00 00 00
00 00 05 00 00 00 00 00

And change the "SmoothMouseYCurve" values to this...
00 00 00 00 00 00 00 00
66 a6 02 00 00 00 00 00
cd 4c 05 00 00 00 00 00
a0 99 0a 00 00 00 00 00
38 33 15 00 00 00 00 00

After making those changes, reboot your computer. Now load up your favorite FPS game and you should notice you can 'frag' a lot easier!

---

