---
title: "Dragon Naturally Speaking"
date: 2006-05-01
forum: Tutorials
---

### Post by bodhi.zazen on 2006-05-01
The "last program" I needed on Linux was voice recognition.

I just got Dragon Naturally Speaking running on Ubuntu 6.04 Drapper Drake Testing.

I am now 100 % Linux, Ubuntu is my primary OS (I am a GNOME, partial to XFCE, my wife likes KDE, ? Ebuntu for kids)

Here is a link to Wine:

[http://appdb.winehq.org/appview.php?versionId=3227](http://appdb.winehq.org/appview.php?versionId=3227)

READ THIS FIRST

Here is my how-to for all who need this program. Questions, post here and I will try to help.

Install wine 0.9.12
	Change to root or sudo
	nano /etc/apt/sources.list
	Add:
		# wine source
		deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/
	synaptic &
	click “Reload” button
	search wine
	install 0.9.12~winehq1-1
	exit synaptic
	exit root

Sidenet 1.9.0 (sidenet 1.9.1 seem to fail)
	cd ~/Wine/wine-config-sidenet-1.9.0
	./setup
	manual install
	install IE6 no
	install font yes
	~/.wine/c for “c drive”

Install IE5.5 (IE6 installs, but does not enable dragon)
	copy ie55sp2.exe to ~/.wine/c
	cd ~/.wine/c
	wine ie55sp.exe
	cd IE\ 5.5\ SP2\ Full/
	 wine IE5SETUP.EXE
		minimal install -> deselect IE help files
		error message RE: DirectX Layer and DirectDrawEx -> Clikd “Next”
		error message:
			An error occurred while setting up
			“c\windows\system32\dxtrans.dll”
			Click OK
		

Install Dragon
	cd ~/.wine/dosdevices
	ln -s /media/cdrom f:
	wine f:setup
	Installer starts
	Input SN
	default install location
	typical install
	install hangs at 89 %
	wait........
	Chose “print registration form”
		close the explorer window that appears
	Unselect quick start

Configure wine
	alsamixer
		enable capture
		hit Tab
		increase capture to 80
	open sound manager
		capture tab
		enable microphone
	winecfg
		Aduio tab
			Crashes winecfg
				Want to Select OSS, winecfg keeps crashing
				Does not seem to matter
				
		Graphics tab
			unselect “Allow the window manager to control the windows”
				I think this makes Dragon run faster
			Select “Emulate a virtual window”
				Size 1280 x 1024
					this = size of window, NOT resolution
		Applictions tab
			Add natspeak.exe
			Path=	Program Files\ScanSoft\ NaturallySpeaking\Program\natspeak.exe
			
	Add dll's (see above list)

             See wine home page
             You need to add the dll's under the LIbruary tab

              * (change this to builtin,native)
              msvcrt
              riched20
              ole32
              oleaut32
              rpcrt4

         exit winecfg

         touch ~/.wine/c/windows/system32/comdlg32.dll
         You will need to copy riched20.dll from Windows
         This requires a valid windows license

          copy riched20.dll to ~/.wine/c/windows/system32/




	touch ~/.wine/c/windows/system32/comdlg32.dll
		winecfg still runs
		Selecting autiotab still crashes winecfg

Re-start X
	Log out -> log in
	or control-alt-backspace

Run Dragon
	cd ~
	wine .wine/c/Program\ Files/ScanSoft/NaturallySpeaking/Program/natspeak.exe

	Audiosetup wizard starts
	I had to increase the volume on alsamixer
		Increased capture from 80 to 87
	Enter general training
	Finish general training
	Did not import documents
	Did not run tutorial
	Unselect tips of the day, no text is displayed

Success !!

What works
Dragon pad
Some voice commands “scratch that” and “correct that”
Can dictate into notepad
	spotty at times
Can “cut-and-paste” text outside of the wine desktop
Can save documents from dragon pad and open them with linuc native porgrams
	Open office, Abiword, etc


What does not work
some voice commands 
	“spell that” crashes wine
Some fonts do not work

My font selection is short	

Optimize:
	dictate some text
	“correct that”
	select options -> increase to number of options to 9

At some point an error dialog box appears
	“COM returned an unexpected error code: Details are c0000005
	This can be ignored, no change in performance
	Keeps recurring if you clikc “OK”
	Just move it aside, select dragon pad, move dragon pad over error message
	Problem solved (out of sight, out of mind)

---

### Post by bodhi.zazen on 2006-05-07
Here is a full description with screen shots
Screen shots did not post here, can I E-mail them to you (or somewhere at Ubuntu?)

IF YOU SEND ME YOUR E-MAIL ADDRESS I WILL SEND YOU A COPY OF THIS POST WITH SCREEN SHOTS

CAN SOMEONE MAKE THIS LOOK PRETTY FOR ME ????


[CENTER]Part 1. Preamble.[/CENTER]

This is a “hack” to get Dragon Naturally Speaking (DNS) up and running as fast as possible. DNS will perform voice recognition translating your voice into text on Dragon pad within a “wine desktop”, but does not interface directly with Linux native programs outside of the wine desktop (“cut-and-paste” between the wine desktop and Linux native programs works no problem [both ways]). 

DNS will run and perform voice recognition, but not everything works. At the end of this document I listed problems, “work arounds”, and “tips” for making the most of Dragon on Linux (Wine).

Conventions: [~ = your home directory]
1. I placed all downloaded files into a folder ~/Wine
2. I used ~/.wine/c as the location of my “fake” windows c drive.
3. DNS=  Dragon Naturally Speaking Version 7 (preferred or professional).
4. IE= (Microsoft) Internet Explorer.
5. Tab completion- I indicate tab completion by using <tab>
	File names are long
	Lexicon to identify windows file locations with the Linux command line is obscure (to me at least)
	USE TAB COMPLETION !!!!!!!!!
6. Commands typed at a terminal are in BOLD (italics too hard to read).
7. My editor of choice is nano. substitute vi (or other) if you do not use nano.


[CENTER]Part 2. What you need to run Dragon:[/CENTER]

1. Time 1-2 hours with reading and downloading.
	This ain't hard, but it ain't no “point and click” either 

2. Linux I have successfully installed and run DNS on Fedora core 5, Zenwalk 2.4, and Ubuntu 6.06. 

3. WINE. I used Wine 0.9.12-> This is the most recent version (as of this writing)
	Install as per your version of Linux [http://www.winehq.org/site/download](http://www.winehq.org/site/download)
	Apt-get, YAST, yum, synaptic, source, etc
	
	Note: On Fedora core 5 I used pull down menu rather the the above site
		Add/Remove software -> search for wine –> Install wine-0.9.12-1.fc5.i386
		
4. IE 5.5 Download from: [http://browsers.evolt.org/download.php?/ie/32bit/5.5_SP2/ie55sp2.exe](http://browsers.evolt.org/download.php?/ie/32bit/5.5_SP2/ie55sp2.exe)
	Throughout this post IE=(Microsoft) Internet Explorer
	Dragon needs IE
	IE6 did not work
	
5. Sidenet installer 1.9.0 (sidenet-1.9.1 DID NOT WORK)
	 Download from: [http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)
	The downloads are at the very bottom of the page
	download wine-config-sidenet-1.9.0.tgz
	Unpack sidenet (I used archive manager, starts automatically after double clicking on the
		wine-config-sidenet-1.9.0.tgz file
	Creates a new folder in ~/Wine -> wine-config-sidenet-1.9.1
	
6. Valid windows license -> riched20.dll REQUIRED
	DO NOT COPY THIS DLL WITHOUT A VALID WINDOWS LICENSE
	I used riched20.dll from WindowsXP
	(Location C:\Windows\winnt\system32\riched20.dll)

7. Dragon Naturally Speaking v7 (I used the professional version, I understand the preferred version also works).
	I have tried to install DNS 8 -> NO LUCK (	I can not get the installer to start)

8. alsa and alsa-oss (sound)

9. A “mixer” to configure your microphone. (I used kmixer).

10. There is some mention in previous posts about DCOM98.  Idid not need to download or install DCM98, ? Sidenet did it automatically.


[CENTER]Part 3 Install[/CENTER]

1. Install Wine-> Should be done by now. If not see #3 above.
	Fedora
		Add/Remove software -> search for wine –> Install wine-0.9.12-1.fc5.i386
	
	[B]Ubuntu 6.06
		Terminal (CLI)
			sudo nano /etc/apt/sources.list  -> enter password

			add the following lines to the file:

				# Wine source
				deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/

			Save and exit (<Ctrl> X, answer “yes”)

		Run synaptic -> Reload -> Search for “wine” -> install 0.9.12~winehq1-1[/B]

	Zenwalk terminal (CLI) [download wine-0.9.12-486-S10.2.tgz to ~/Wine as above]

		cd ~/Wine 
		su -> enter root password 
		installpkg wine-0.9.12-i486-S10.2.tgz 



**FROM NOW ON  INSTILLATION AND CONFIGURATION WAS THE SAME FOR ALL 3 VERSIONS OF LINUX**


2. Configure wine. **DO NOT RUN (CONFIGURE) AS ROOT**

	USE 1.9.0 (sidenet 1.9.1 DOES NOT WORK).
	This is a script that will configure wine.
	go to your new sidenet folder (In my case cd ~/Wine/sidne <tab>)
	In a terminal (CLI) [NOT AS ROOT]

[B]		cd ~/Wine/wine-config-sidenet-1.9.0/
		chmod a+x setup
		./setup[/B]

	sidenet runs in the terminal (CLI) and asks 6 questions:
		1. This script will install wine-config-sidenet.
			Continue(y/n)?> Answer “y” 
		2. Please specify your language. If unsure, just hit enter and english version will be installed.
			Language code ? : <enter>
		3. Install option (0-4)? : Enter “3” (Manual installation)
		4. Install IE6 -> Answer “n”
		5. Link ~/.font -> c:\windows\fonts (y/n)? -> Answer “y”
		6. Virtual C drive path ? : -> Answer ” ~/.wine/c “(or ~/.wine/drive_c)
	
	Lots of output to terminal, no error messages
	At the end of the script sidenet opened my browser to tell me the installation was complete

3. Install IE 5.5. (Dragon did not work with IE6 and wine-0.9.12)
		IE6 works fine with wine-0.9.12, **BUT DOES NOT ENABLE DNS**
	Copy the IE5 program to the c drive
		copy ie55sp2.exe from ~/Wine to ~/.wine/c (GUI or command line, your choice)
	Run installer ; command line again (Not as root)

[B]		cd ~/.wine/c
		wine ie55sp2.exe[/B]

		This creates a new folder in c and unpacks or “Inflates” some cab files
	Now install IE5
		change to the new IE5 directory
		**cd IE<tab> **(cd IE\ 5.5\ SP2\ Full/) [watch the spaces if you do ot use tab completion]

Now install IE (again in a terminal window [CLI]):

	**	wine IE5SETUP.EXE**

		This installs IE5 (a well known virus) into the fake C drive
			Accept agreement -> click “Next” radio button
			Chose “Install Minimal” -> click “Next” radio button
			Unselect “Internet Explorer Help” -> click “Next” radio button
				Lots of output to terminal

		Downloads and installs IE5.5

			See message regarding DirectX Layer and DirectDrawEx not installed
				does not seem to matter -> click “Next” radio button

			You will next see a window to Restart computer -> click “Finish”
				does not really restart the computer, just winedesktop

			Lots of output to terminal, some apparent error messages
				does not seem to matter

		You will then get an error messages/complaints from IE, I ignored this as it does not seem to matter

		Click “OK”

		Lots of output to the terminal here.
	
		Ends in “err” messages, the last 3 lines of a long listing ends as follows:

			wine: could not load L"C:\\windows\\GRPCONV.EXE": Module not found
			err:wineboot:runCmd Failed to run command L"grpconv.exe -o" (126)
			err:wineboot:ProcessRunKeys Error running cmd #2 (126)

	Hit <enter> and you will get the command prompt back:

		:~/.wine/c/IE 5.5 SP2 Full$


4. Install Dragon
	No problems here. I ignored all the output and error messages. Did not seem to matter.
	The trick is to use wine to install Dragon
	Continue in a terminal (CLI)

		**cd ~/.wine/dosdevices**

	you need to mount and know the name of your Dragon CD
	Fedora auto mounts my CD in /media
	name of CD is : /media/ DNS_MED_7_0
	Therefore type (in a terminal) [This makes a symbolic link]

		Fedora:
			ln -s /media/DNS_MED_7_0/ f:

[B]		Ubuntu:
			ln -s /media/cdrom0/ f:[/B]

		Zenwalk:
			ln -s /mnt/cdrom/ f:
		
	**	NOTE: Link to “e”: did not work** Link to e: seem OK , but it is BROKEN !!!


	now install Dragon
	Again in the terminal (CLI)

		[B]wine f:setup
[/B]
	This starts the Dragon installer and installs Dragon. [this is where I have a full set of screen shots

		Accept license -> click “next”

			Enter user name and serial number

		Click “Next”

		Click “Next”

		Click “Yes”

	I had no problems with the mouse and using the radio “OK” buttons
	I did a typical install into the default directory.
	Again, all the buttons worked for me and I used the keyboard only to type the serial # and mouse to click “OK” 
	Got some output to the terminal, I ignored.

	Install then seems to hang at 89% install -> -> Be Patient
	A dialog appears to register Dragon

		Choose “print registration form” option
		Close the IE dialog that appears
			This will fool DNS into thinking you have registered the product an it will not ask you again
			With all other options DNS will keep asking you to register.
			I, of course, registered DNS years ago.

The next box to appear is; (sorry, screen shots did not post)

Uncheck the “Enable QuickStart mode on Windows Startup” box

Click “Finish”

Click “OK” in the Restart Windows box

	Installation of Dragon is  now complete




Part 4 Configure wine
1. Terminal (CLI) again
	type winecfg
	you get a gui to configure wine


	Emulate windows 98
	Click “add application”
		Use mouse to and click on natspeak.exe
			~/.wine/c/program Files/Scansoft/NaturallySpeaking/Program/natspeak.exe

					Click the “Open” box


Which then gives you this:

	Not click the “Libraries” tab and configure some dll's:

		Under the Libraries tab Add the following enteries:

		* -> Click “edit” and change to “builtin,native”
		msvcrt
		riched20
		ole32
		oleaut32
		rpcrt4

Final Product looks like this

	Click “Apply” -> Click “OK”  -> This will exit winecfg

	Audio tab: Use OSS for sound (NOT ALSA) (under the winecfg audio tab)
		Audio tab crashes in Ubuntu, does not matter it was set as default by sidenet
		OK in Fedora and Zenwalk (scree shot below from Fedora core 5)

NOTE: In winecfg, under the “Graphics” tab
	1. Emulate a virtual desktop -> I changed my wine desktop to 1280 x 1024
			MY DEFAULT resolution is 1600 x 1200 !!!

		Recommend a  800 x 600 if you default resolution is 1280 x 1024
			This sets the SIZE of the wine desktop, not the resolution.

	2. I uncheked the “allow the windows manager to control the windows” box
		Dragon seems to run significantly faster if this box is unchecked
		Could be wrong, this one is obscure to me

Finish with a few commands in the terminal:

	2. Terminal (CLI), add an empty file “comdlg.dll” in ystem 32
		
**		touch ~/.wine/c/windows/system32/comdlg32.dll **

NOTE:
The comdlg32.dll “workaround” enables Dragon, but breaks some programs in wine
	Most notable, it may break winecfg !!!!!!!!!!!!
		Just delete or rename comdlg and winecfg will again work, Dragon will break
	Repeat re-name/touch.... comdlg32.dll-> enables Dragon, disables winecofg, you get the idea

	I don't know (don't care) what else is broken (in wine), the only windows program I run is Dragon



3. **Copy riched20.dll to ~/.wine/c/windows/system32**
		windows dll location:  C:\Windows\winnt\system32\riched20.dll

NOTE: THIS REQUIRES A VALID WINDOWS LICENSE.
I used windows XP dll's, no problem
copy riched20.dll to: ~/.wine/c/windows/system32




Step 5 Configure microphone

1. Dragon CAN NOT adjust the microphone (volume) settings.

2. alsamixer did not work for me
	It showed my microphone, but I could not configure the microphone capture
	You can read man alasmixer if you want, it did not help me much

3. **Go to this website: [http://www.skype.com/help/guides/soundsetup_linux.html](http://www.skype.com/help/guides/soundsetup_linux.html)**
	Thank you Skype.
	I used Kmix
	Command line again
		kmix &
		Enable BOTH the capture and microphone
	See pictures on Skype website
	See this picture from my desktop
	Note which red/green lights are activated and slider (volume) settings

alasamixer
	Command line
	Use <tab> to move between Playback, Capture, and All
	Use arrow keys to move between various channels
	Go to “Capture” (may not appear on the first screen, just use arrows to move over)
	Use arrow up or a number to set level
	<Esc> key to exit

Screen shot alsamixer:  Note the volume on CAPTURE and AC97 !!!

Kmix INPUT tab: Note settings for Mic, Capture, and AC97

Kmix Output tab: Note settings for Mic and AC97

Run Dragon
1. Command line again

2. The desktop icon does not work YET
		After Dragon is configured it will work
	wine ~/.wine/c/programfiles/scansoft/.... whatever. I use tab completion:
	wine ~/.wine/c/P<tab>
	wine ~/.wine/c/Program\ Files/S<tab>
	you get the idea????
	Final destination: wine ~/.wine/c/Program\ Files/ScanSoft/NaturallySpeaking/Program/natspeak.exe


3. This will bring you into the (audio) setup wizard followed by general training.
	I had mucho problems here. If your microphone is not configured -> no audio input -> setup fails
	If you have this problem, go back to kmix and  skype website and try again
	Or try a different mixer

		Adjust microphone, click Next

		Read text

	Click Next to enter General Training

	Complete General training (no screen shots)

4. Once the microphone is working general training begins.

5. I had no problems with the mouse or radio (OK) buttons through general training.
	See other posts for potential problems and fixes (if any)
	Something about the Ctr or Alt key and letters?

6. This would be a good time to BACKUP ~/.wine !!!!!!!!!!!!!!!!!

Use Dragon

Last observations:

1. This is a hack, at best; Do not get fancy.

2. Dictate to dragonpad and be careful when changing the font (my default was arial) as not all fonts seem to work
		If they do not text is “invisible” in Dragon pad
		Cursor moves with voice recognition -> no text

3. Tried notepad –  Mixed results at best. Advise you stay with Dragon Pad
	
4. I changed to my preferred font in Dragonpad (Times New Roman; copied from Windows) worked without problems.

5. Hot keys did not work, nor did the voice commands “go to sleep” or “wake up”.

6. Use mouse to click the microphone (on dragon bar) or (if they work for you) voice commands (“go t sleep” ; “wake up”) to turn microphone off and on.
7. Speed was good in fact for an old computer at least as fast as native to windows.

8. If the program crashes or freezes, use in a terminal (CLI) wineserver -k and restart Dragon.

9. If Dragon crashes “hard” it may take out your sound settings and you will need to re-set them with alasmixer or kmix.

10. If Dragon crashes real hard it may take out your X server- > you will need to debug or reboot (I reboot).

11. Did I mention; BACKUP your ~/.wine folder !?!

Debriefing

Advice:
	Save you work often (in case of crash)
	Once done with dictation you may:
		Cut and paste to Linux (Abiword, OpenOffice, KOffice, etc)
		Save the file and open it with any Linux native editor
	Once in a “standard” Linux work processor, change font, format, etc
	Once Dragon is installed and configured
		did I mention; BACKUP your ~/.wine folder
	You can now use the Dragon shortcut on your desktop to start Dragon
			or the command line

12. Save your work often. I keep the mouse over the save box on the dragon pad menu and click it from time to time or when attempting anything fancy (tweak).

13. Create a separate user for each task (intended use) of dragon. For example, I use Dragon professionally (in case you have not guessed). I have a user in Dragon for professional dictation, and a second for personal use (E-mail, general non-professional dictation).  I have the most problems with general (personal) dictation. Dragon puts professional terminology into general dictation (accuracy is poor). If I train Dragon to do both tasks (professional and personal) accuracy deteriorates fast. If I use two separate users, accuracy remains high for each task (professional vs. general dictation).

14. Training: The Dragon recognition engine used “fuzzy logic” and, with continued training, accuracy first improves, then deteriorates. “best method” to optimize accuracy:
	I never found analyzing documents was not all that helpful.
	Train/dictate for 30-40 hours, then run the acoustic optimizer
	That's it. From then on, do not save your speech files when you dictate
	Do not save your speech files if you dictated with a “cold” or cough
	Instead, to train or maintain you vocabulary list, open a session with dragon
		add or train any new (or old) words
		save the speech files session
		run acoustic optimizer only if needed
	Continued training (after 30-40 hours) does not seem to improve accuracy, in fact I think it lowers over time with
		(continued training and saving of speech files the dragon engine “over learns”). This is due to fuzzy logic
		and over training within such a system.

15. Crash:
When dragon crashes, it crashes hard. It may take out alsa (sound). It may take out X server.

Solution (if x server crashes):
Crtl-alt-F1
At login prompt-> root, enter root password -> shutdown -r now (reboots computer)
For me Dragon crashes with the spelling tool ”spell that”, wither as a voice command or as an option from the correction
	 dialog (“correct that” -> choose spell -> crash)
**You have been warned**

16. Error messages:
I keep getting a repetitive COM returned an unexpected error code: Details are c0000005
	Click the radio "OK" button -> It's like the energizer bunny, it keeps going......
	I ignore it altogether, move the dragon pad window over (on top of) the error window -> problem solved (hidden)
	Out of sight..... Out of mind

Just click on the Dragon pad window and it will become the active window covering the error message.
	
 If I move the Dragon pad window a little more to the right I will no longer ever see the error message.

17. Voice commands:
“Correct that” works (increase list to 9 in “options”), but spelling dialog crashes the program.
	Either “spell that” or using the spell option form the corrections list -> crash (see No. 1 above)
	If none of the 9 choices in the correction list are correct, choose “unselect that” as other options tend to freeze or 			crash Dragon 

18. Use the Words tab on Dragon menu to train words/phrases
	When training->  the words do not appear in the dialog box, but it seems to work OK

19. Import Fonts
	Copy Font from Windows to ~/.fonts or ~/.wine/c/fonts (same thin, sidenet created a link, see install sidenet above)
	To some extent this can fix the problem of Invisible text in some (not all) message boxes
		Works in word training box whis is most important.


I have now told you more then I know!!

Beam my up Scotty, there is no intelligent life here


Personal notes:
Could not import dragon 8 vocabulary into DNS 7, incompatible vocabulary between DNS 7 & 8
As above, I could not install or update to DNS 8

---

### Post by bodhi.zazen on 2006-06-02
Any replies?

FYI: I have had problems installing Dragon into Wine 0.9.13 and 0.9.14.

Download wine 0.9.12 from here:

[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803)

Install Dragon.

You can then upgrade wine to 0.9.13 or 0.9.14 without problems. No improvement in performance over wine 0.9.12.

---

### Post by traherom on 2006-06-03
Hm... looks good. (didn't see this when you posted it originally) I may try it tomorrow.

---

### Post by hizaguchi on 2006-06-15
Ok, this may be a dumb question, but I've never used Wine so bear with me. :)  Can Dragon control the rest of the computer like it can in Windows?  From the description in the howto, it sounds like you're confined to just other programs running in Wine.  Too bad if that's the case, because Dragon Dictate is incredibly useful for people who can't use thier arms.

---

### Post by bodhi.zazen on 2006-06-15
Thank you for yor post. 

First: Wine is under heavy development and it is not easy or intuitive to run. Basically, in a nut shell, first install wine, then configure wine, then install windows programs.

You can use synaptic to install wine.

To configure wine you either need to know how to configure windows/wine DLL's and the registry or use a tool. I am aware of 3 tools: Winetools, Sidenet, and Wine Doors. Wine doors is the newest and may not be ready for prime time.

Wine tools changes some of the wine configuration files and installs a number of microsoft code. I have not used wine tools successfully to configure wine to run Dragon.

Sidenet works, but not the most current version (follow my post, versions of wine, sidenet, and IE are critical. After you install Dragon you can update wine). Dragon version 8 is not working.

Wine doors I have not tried, but I think it under (? heavy) development.

[http://www.linux.com/article.pl?sid=06/06/07/1920213](http://www.linux.com/article.pl?sid=06/06/07/1920213)
[http://www.wine-doors.org/trac/wiki](http://www.wine-doors.org/trac/wiki)

You can also try Crossover office or cedega. Cross over office is not working with Dragon according to their web site (there has been no activity on the crossover office web site regarding Dragon in almost 18 months). cedega is primarily for games and I could not get Dragon working under cedega.

Another problem with wine is it is in the "alpha" stages and often suffers form "regression" which means there is significant variability in performance between various versions of wine and after an upgrade a previously working program may no longer work.

My impression is the wine project still has a long way to go to emulate windows 98, let alone windows 2000 or XP.

To answer you question regarding Dragon: Right now Dragon has very basic voice recognition ONLY. Dragon has may more complex features which are not working at this time. There is no integration with linux native programs other then cut-and-paste. So no, voice commands or controlling the computer as you say will not work and is likely a long way away.

If wine doors comes to fruition, however, this may change.

Good luck, thank you for your questions.

---

### Post by hizaguchi on 2006-06-15
Thanks.  My dad uses the old, 16bit version of Dragon to do pretty much everything with his computer, and because of that he has been stuck with Windows ME (XP doesn't like the old Dragon, he has been training it for like 10 years so doesn't want to upgrade, plus old Dragon does some things new Dragon can't).  I was hoping to convert him to Linux and use Wine to get his Dragon to work, but it doesn't sound too promising.

---

### Post by bodhi.zazen on 2006-06-15
hizaguchi:

I do not think dragon/Linux will work for your situation.

However you should be able to run just fine in Windows XP. There is a compatibility option in windows for older software. I have used if for games and it worked well. I can not describe how it is exactly done, try a google search.

Also there is not much, if anything, the old dragon can do that the new dragon does not do better. I have used multiple versions of Dragon for years and can not think of any option that was not either maintained, if not ehnanced on newer versions of Dragon.

Dragon 7 and 8 are both significant improvements from previous versions. Training is much faster and much more efficient and accurate.

---

### Post by SqRt7744 on 2006-06-15
this is good, my brother uses Dragon and is a bit reluctant to leave the windows world because of it...  I'll have to try this out.  I may also try to use it in a windows install under vmware, I wonder if that would work.

---

### Post by sixsixone on 2006-07-26
I've tried ViaVoice for Windows XP in a VMware session in ubuntu and had no luck, I have heard that voice recognition is one area where virtualisation software i.e. VMware, Citrix e.t.c is no good at all.

Tried in VMware running XP Pro, home & Vista beta but I'd be interested to know if Dragon would work.

Of course you're then restricted to input into programmes running in the virtual machine, and if your computer isn't top of the range it'd prob. be sooooo slow even if it did work- 2 OS's + voice rec. software = huge processor drain...

i hate being the voice of doom :-( 
somebody prove me wrong.

---

### Post by carleton on 2007-03-19
thanks for the info.  Have there been any developments since last summer?  Currently I'm using Dragon quite a bit and it has unfortunately become a "killer app" so more often than not I'm stuck in Windows, something I'm not too happy about. 

Hopefully I will try installing this on my version of Edgy later this week, I'll let you know how it goes.

Cheers,
Carleton

---

### Post by bodhi.zazen on 2007-03-20
> **carleton said:**
> thanks for the info.  Have there been any developments since last summer?  Currently I'm using Dragon quite a bit and it has unfortunately become a "killer app" so more often than not I'm stuck in Windows, something I'm not too happy about. 

Hopefully I will try installing this on my version of Edgy later this week, I'll let you know how it goes.

Cheers,
Carleton

Not that I am aware of.

You can not yet run DNS 8

DNS 7 will not run on the more recent versions of wine. You need Wine 0.9.12 up to about Wine 0.9.20, possibly Wine 0.9.18,  I am not sure of the exact cut off.

If it helps, I user Wine 0.9.18 and DNS 7

As I recall, you have to install on Wine 0.9.12 but from there, if you like, you can upgrade wine.

Once you install, BACK UP ~/.wine

If you need to re-install or tansfer to a new OS ...

Install wine in the new OS

Configure wine with Sidenet

Copy ~/.wine from backup.

HTH

Feel free to PM me if you get stuck :)

---

### Post by writingsama on 2007-08-01
I'd just like to state-
All versions of DNS including 9.5 seem to run fine in VirtualBox 1.3.8 (NOT 1.4!), with occasional crashes (once every few days) only, on my Core 2 Duo 1.83Ghz,  480mb RAM for the VM, Windows XP Home install.

VBox1.3.8 would be perfect if only it didn't crash SO MUCH using shared folders!

---

### Post by Chriswaterguy on 2007-10-23
Thanks for the info - I'm looking forward to getting a copy of DNS and trying it out on Ubuntu 7.10. 

Has bodhi.zazen or anyone else had any more experiences with DNS since Ubuntu 7.10 came out?

---

### Post by dansan on 2007-11-15
Considerable time has passed since this thread ran, but, being a new Ubuntu user, I have only just seen it. Like bohdi.zazen, the only thing keeping me from fully switching over to Linux is lack of speech recognition. 

I have read all of the pointers on how to set up DNS, but I would like to hear any further comments on experience with using this program since this thread ran. Specifically, has there been any success getting DNS 8.0 to run? My disk with DNS 7.0 appears to be damaged, but I have a fully functional DNS 8.0 disk. If you only have had success with DNS 7.0, could you point me to a possible source for DNS to 7.0?

Best regards and thanks,
dansan

---

### Post by bodhi.zazen on 2007-11-15
For the latest information , see here :

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2077](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2077)

There has been talk about dragon 9 working, but I do not have dragon 9.

In order for this how-to to work you will need an old version of Ubuntu and Wine as well as DNS7.

I have never gotten DNS8 working and keep an old partition with an outdated version of Linux + DNS7

Here's hoping one or several voice recognition projects come to fruition on Linux.

---

### Post by dansan on 2008-02-13
> **writingsama said:**
> 
...
All versions of DNS including 9.5 seem to run fine in VirtualBox 1.3.8 (NOT 1.4!), with occasional crashes 
...!

I would like to confirm two successes setting up and running DNS 9.5, using VirtualBox 1.5.2 & 1.5.4. This is on two different types of computer -- on the one hand, an Aspire 9300 laptop (which is what I am dictating this message on now, using DNS 9.5 inside VirtualBox) and, on the other, a Lenovo desktop. Both have processors running at 2 GHz and 2 GB of RAM. DNS 9.5 responds a bit more slowly than when I run the program in Windows (Vista or XP Pro), but the accuracy of dictation is higher running in a VirtualBox guest inside Ubuntu 7.10.

I haven't had any problems with crashes (knock on silicon :)).

Daniel Teague

---

### Post by Brian96 on 2008-03-03
> **dansan said:**
> I would like to confirm two successes setting up and running DNS 9.5, using VirtualBox 1.5.2 & 1.5.4. This is on two different types of computer -- on the one hand, an Aspire 9300 laptop (which is what I am dictating this message on now, using DNS 9.5 inside VirtualBox) and, on the other, a Lenovo desktop. Both have processors running at 2 GHz and 2 GB of RAM. DNS 9.5 responds a bit more slowly than when I run the program in Windows (Vista or XP Pro), but the accuracy of dictation is higher running in a VirtualBox guest inside Ubuntu 7.10.

I haven't had any problems with crashes (knock on silicon :)).

Daniel Teague

I have several questions about this:

1. Anybody tried it in VMWare?

2. Dansan, how much RAM did you give the VM that you are running DNS in?

3. I haven't used voice recognition software before, and I mainly am interested in straight-up dictation. (Controlling the desktop and all that sounds fun, but I would be satisfied--I think--just dictating into a text file that I had to copy.) In that case, is it worth the extra money for Preferred over Standard? Also, is there something cheaper that handles the plain-old dictation well enough (e.g., ViaVoice or something)?

---

### Post by Brian96 on 2008-03-03
Found a link to this article on a Mepis board:

[http://news.softpedia.com/news/Google-Sponsors-Improvements-For-Wine-79173.shtml](http://news.softpedia.com/news/Google-Sponsors-Improvements-For-Wine-79173.shtml)

---

### Post by sunbird on 2008-04-29
> **dansan said:**
> I would like to confirm two successes setting up and running DNS 9.5, using VirtualBox 1.5.2 & 1.5.4. This is on two different types of computer -- on the one hand, an Aspire 9300 laptop (which is what I am dictating this message on now, using DNS 9.5 inside VirtualBox) and, on the other, a Lenovo desktop. Both have processors running at 2 GHz and 2 GB of RAM. DNS 9.5 responds a bit more slowly than when I run the program in Windows (Vista or XP Pro), but the accuracy of dictation is higher running in a VirtualBox guest inside Ubuntu 7.10.

This is good news. My partner has a disability and would like to be able to run DNS inside virtualbox. I installed virtualbox and went through the XP install without any hitches. But when I go to install DNS 9.5, the installer quits with a message:

```
The processor speed is not adequate for running Dragon Naturally Speaking 9
```

This is definitely not the case -- 2.2 ghz Core2, with 2GB ram (1GB assigned to VM). Anyone experienced this problem or have ideas for a fix?

---

### Post by bodhi.zazen on 2008-04-29
> **sunbird said:**
> This is good news. My partner has a disability and would like to be able to run DNS inside virtualbox. I installed virtualbox and went through the XP install without any hitches. But when I go to install DNS 9.5, the installer quits with a message:

```
The processor speed is not adequate for running Dragon Naturally Speaking 9
```This is definitely not the case -- 2.2 ghz Core2, with 2GB ram (1GB assigned to VM). Anyone experienced this problem or have ideas for a fix?

DNS 7 and 8 work in Virtualbox. Performance is sluggish and you may wish to try the low latency kernel (that helps a lot) and / or running Vritualbox with a nice value of -10 to -15.

Beware, updates of virtualbox have broken Dragon so I am not sure which version is best.

Last, I think you are misunderstanding how virtualization (VBox / VMWare) work. They emulate a processor so it has nothing to do with your host CPU.

There are reports of DNS 9 working with wine, and IMO that remains your best bet.

---

### Post by sunbird on 2008-04-30
> **bodhi.zazen said:**
> DNS 7 and 8 work in Virtualbox. Performance is sluggish and you may wish to try the low latency kernel (that helps a lot) and / or running Vritualbox with a nice value of -10 to -15.

Sorry for the basic question, but how do I do that? 

> **bodhi.zazen said:**
> Last, I think you are misunderstanding how virtualization (VBox / VMWare) work. They emulate a processor so it has nothing to do with your host CPU.

Geez... Yeah, of course that makes perfect sense. But it also seems like there should be a way to increase the speed of the emulated processor... ?

> **bodhi.zazen said:**
> There are reports of DNS 9 working with wine, and IMO that remains your best bet.

I couldn't get it to install, but will keep trying.

---

### Post by bodhi.zazen on 2008-04-30
Low latency kernel : [http://packages.ubuntu.com/linux-image-lowlatency](http://packages.ubuntu.com/linux-image-lowlatency)

What how-to did you follow for DNS 9 ?

---

### Post by sunbird on 2008-05-10
> **bodhi.zazen said:**
> Low latency kernel : [http://packages.ubuntu.com/linux-image-lowlatency](http://packages.ubuntu.com/linux-image-lowlatency)

Strange... I installed the real-time kernel and my machine had constant kernel panics. So, I decided to go ahead and upgrade to 8.04 and go back to the generic kernel.

> **bodhi.zazen said:**
> What how-to did you follow for DNS 9 ?

I didn't find any how-to. I just heard mention that it worked on VB, so I thought I'd give it a try.

Now I will try it in 8.04 on a clean install and see if it works.

---

### Post by stengah on 2008-05-27
Heard thingd have improved a lot since google made improvements to wine to get picasa running on linux. Dragon and photoshop CS+CS2 should now be able to run on wine 1.0

If so, can anybody provide an updated how-to for installing latest version of Wine + Dragon 9-9.5?

Cheers!

---

### Post by larryfroot on 2008-07-04
Wine have got DNS 9 up and running with wine 1.0.0 but it seems only the preferred and not the professional version works, but keep an eye on this as the situation may change. The standard of DNS 9 preferred version on wine is 'silver'. All the core functionality is present, some (far less critical) functions will be a bit flakey, here's the URL 


[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5402]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=5402")
 
Please, please let me know how you got on,,,I will be trying it out over the next few days and will report back to this thread. good luck!

---

### Post by kle on 2008-10-01
Hi bodhi.zazen

I was very encouraged to see from your Howto on page one of this thread, that Dragon actually can work to some extent. But I believe you started out on Dapper and we are now on Hardy Heron and Wine has come a long way too.

Any new developments?
-----------------------
Sorry! I found this link about Dragon Naturally Speaking on Wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5402](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5402)

---

### Post by boblevien on 2009-08-14
Has anyone had any success with DNS 10? I've been using Dragon since ver 5 or 6 and been watching it gradually improve but DNS 10 is a vast improvement. Have tried to run ver 8 on Ubuntu (many thanks to Susan Cragin) but never really got it going - it worked but wasn't usable. Would love to succeed with ver 10.
Bob Levien

---

### Post by frenchn00b on 2009-09-10
> **bodhi.zazen said:**
> The "last program" I needed on Linux was voice recognition.

I just got Dragon Naturally Speaking running on Ubuntu 6.04 Drapper Drake Testing.

I am now 100 % Linux, Ubuntu is my primary OS (I am a GNOME, partial to XFCE, my wife likes KDE, ? Ebuntu for kids)

Here is a link to Wine:

[http://appdb.winehq.org/appview.php?versionId=3227](http://appdb.winehq.org/appview.php?versionId=3227)

READ THIS FIRST

Here is my how-to for all who need this program. Questions, post here and I will try to help.

Install wine 0.9.12
	Change to root or sudo
	nano /etc/apt/sources.list
	Add:
		# wine source
		deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/
	synaptic &
	click “Reload” button
	search wine
	install 0.9.12~winehq1-1
	exit synaptic
	exit root

Sidenet 1.9.0 (sidenet 1.9.1 seem to fail)
	cd ~/Wine/wine-config-sidenet-1.9.0
	./setup
	manual install
	install IE6 no
	install font yes
	~/.wine/c for “c drive”

Install IE5.5 (IE6 installs, but does not enable dragon)
	copy ie55sp2.exe to ~/.wine/c
	cd ~/.wine/c
	wine ie55sp.exe
	cd IE\ 5.5\ SP2\ Full/
	 wine IE5SETUP.EXE
		minimal install -> deselect IE help files
		error message RE: DirectX Layer and DirectDrawEx -> Clikd “Next”
		error message:
			An error occurred while setting up
			“c\windows\system32\dxtrans.dll”
			Click OK
		

Install Dragon
	cd ~/.wine/dosdevices
	ln -s /media/cdrom f:
	wine f:setup
	Installer starts
	Input SN
	default install location
	typical install
	install hangs at 89 %
	wait........
	Chose “print registration form”
		close the explorer window that appears
	Unselect quick start

Configure wine
	alsamixer
		enable capture
		hit Tab
		increase capture to 80
	open sound manager
		capture tab
		enable microphone
	winecfg
		Aduio tab
			Crashes winecfg
				Want to Select OSS, winecfg keeps crashing
				Does not seem to matter
				
		Graphics tab
			unselect “Allow the window manager to control the windows”
				I think this makes Dragon run faster
			Select “Emulate a virtual window”
				Size 1280 x 1024
					this = size of window, NOT resolution
		Applictions tab
			Add natspeak.exe
			Path=	Program Files\ScanSoft\ NaturallySpeaking\Program\natspeak.exe
			
	Add dll's (see above list)

             See wine home page
             You need to add the dll's under the LIbruary tab

              * (change this to builtin,native)
              msvcrt
              riched20
              ole32
              oleaut32
              rpcrt4

         exit winecfg

         touch ~/.wine/c/windows/system32/comdlg32.dll
         You will need to copy riched20.dll from Windows
         This requires a valid windows license

          copy riched20.dll to ~/.wine/c/windows/system32/




	touch ~/.wine/c/windows/system32/comdlg32.dll
		winecfg still runs
		Selecting autiotab still crashes winecfg

Re-start X
	Log out -> log in
	or control-alt-backspace

Run Dragon
	cd ~
	wine .wine/c/Program\ Files/ScanSoft/NaturallySpeaking/Program/natspeak.exe

	Audiosetup wizard starts
	I had to increase the volume on alsamixer
		Increased capture from 80 to 87
	Enter general training
	Finish general training
	Did not import documents
	Did not run tutorial
	Unselect tips of the day, no text is displayed

Success !!

What works
Dragon pad
Some voice commands “scratch that” and “correct that”
Can dictate into notepad
	spotty at times
Can “cut-and-paste” text outside of the wine desktop
Can save documents from dragon pad and open them with linuc native porgrams
	Open office, Abiword, etc


What does not work
some voice commands 
	“spell that” crashes wine
Some fonts do not work

My font selection is short	

Optimize:
	dictate some text
	“correct that”
	select options -> increase to number of options to 9

At some point an error dialog box appears
	“COM returned an unexpected error code: Details are c0000005
	This can be ignored, no change in performance
	Keeps recurring if you clikc “OK”
	Just move it aside, select dragon pad, move dragon pad over error message
	Problem solved (out of sight, out of mind)


dragon natrually speaking
Version 8 is working with Linux, and *nix platforms

---

### Post by jwyg on 2010-03-25
> **boblevien said:**
> Has anyone had any success with DNS 10? I've been using Dragon since ver 5 or 6 and been watching it gradually improve but DNS 10 is a vast improvement. Have tried to run ver 8 on Ubuntu (many thanks to Susan Cragin) but never really got it going - it worked but wasn't usable. Would love to succeed with ver 10.
Bob Levien

Would also love to know if anyone has got DNS 10 working on latest version of Ubuntu!

---

### Post by bodhi.zazen on 2010-03-26
> **jwyg said:**
> Would also love to know if anyone has got DNS 10 working on latest version of Ubuntu!

Best source of up to date information is on the wine home page:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2077](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2077)

---

### Post by jwyg on 2010-03-30
> **bodhi.zazen said:**
> Best source of up to date information is on the wine home page:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2077](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2077)

Amazing! Thanks for the link. Any idea whether the walkthrough above (for Ubuntu 6.04 + Dragon 8/9) also works for Dragon 10 (+ Ubuntu 9.10)?

---

### Post by bodhi.zazen on 2010-03-30
Yes, there are links on the origional link:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13563](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13563)

That second link has detailed instructions.

---

### Post by ebruzzone on 2010-04-05
Hi. I am a novice ubuntu user so please bear with me some silly questions. 

I am trying to install dns 9 (in spanish). Wine is somehow not able to install it. I get an error 1607 from dns (the rest is in Spanish but is something like a command sequence mistake). 

Anyway, do you think that if I install windows inside ubuntu (my pc does not have dual boot since I am more than happy with ubuntu) it may help installing dns?

thank you!

---

### Post by bodhi.zazen on 2010-04-05
> **ebruzzone said:**
> Hi. I am a novice ubuntu user so please bear with me some silly questions. 

I am trying to install dns 9 (in spanish). Wine is somehow not able to install it. I get an error 1607 from dns (the rest is in Spanish but is something like a command sequence mistake). 

Anyway, do you think that if I install windows inside ubuntu (my pc does not have dual boot since I am more than happy with ubuntu) it may help installing dns?

thank you!

Last time I did this (DNS in a VM, iw VirtualBox or VMWare) sound was too slow to be helpful.

I would advise you dual boot if you need DNS and wine is not working.

---

### Post by ebruzzone on 2010-04-05
> **bodhi.zazen said:**
> Last time I did this (DNS in a VM, iw VirtualBox or VMWare) sound was too slow to be helpful.

I would advise you dual boot if you need DNS and wine is not working.

Thanks for the quick answer! It is a pity that it may be no solution under ubuntu uh.

---

### Post by bodhi.zazen on 2010-04-05
> **ebruzzone said:**
> Thanks for the quick answer! It is a pity that it may be no solution under ubuntu uh.

+1

There are a few areas where open source solutions are lagging. Voice recognition (such as Dragon) is one.

---

### Post by sideburns on 2010-06-15
My sister came to me with one of the above posts as a guide, and a copy of Dragon.  I skipped all the junque about installing wine, as she already had it installed.  (If it weren't, I'd have used Add/Remove Software instead of fumdiddling with it and Doing It the Hard Way.)  I put the CD in the drive, opened it, right-clicked on setup.exe and told it to run under wine.  She's now installing the software, and unless I'm badly mistaken, it will Just Work.  No need for a long, involved setup script, just run the damned program and let it do its thing.

---

### Post by bodhi.zazen on 2010-06-15
It would be fantastic to get an update once you have finished.

You should understand the initial post in this thread is from 2006.

Wine changes too often to update the post with every release of wine.

---

### Post by dewdrop_world on 2010-08-22
DNS 10 + Wine is working for me (Ubuntu 10.04) with some qualifications:

- I launch it, and the dragon bar doesn't appear. I kill the stray natspeak.exe process, relaunch and it (usually) works.

- Can't dictate anywhere except the dragonpad.

- Spell mode crashes. Some voice commands make recognition stop working.

- When I'm done dictating, basically I have to reboot. Wine seems not to release the audio device to other apps properly. E.g., quit NatSpeak, then launch Skype --> crash.

- During initial setup, it will tell you your hardware is too slow and set it for speed, not accuracy. You can change that in tools > options for more accuracy and it's fine.

Even with those limitations, I can dictate fairly long emails without issue.

I installed right from the cd, running setup.exe by the wine launcher. No issues with installation.

James

---

### Post by bodhi.zazen on 2010-08-22
> **dewdrop_world said:**
> DNS 10 + Wine is working for me (Ubuntu 10.04) with some qualifications:

- I launch it, and the dragon bar doesn't appear. I kill the stray natspeak.exe process, relaunch and it (usually) works.

- Can't dictate anywhere except the dragonpad.

- Spell mode crashes. Some voice commands make recognition stop working.

- When I'm done dictating, basically I have to reboot. Wine seems not to release the audio device to other apps properly. E.g., quit NatSpeak, then launch Skype --> crash.

- During initial setup, it will tell you your hardware is too slow and set it for speed, not accuracy. You can change that in tools > options for more accuracy and it's fine.

Even with those limitations, I can dictate fairly long emails without issue.

I installed right from the cd, running setup.exe by the wine launcher. No issues with installation.

James

Thank you for taking the time to post an update. Sounds as if it is still functioning about the same - The basic functions work in 
Dragon pad.

---

### Post by dewdrop_world on 2010-10-18
Further update -- it turns out a lot of my stability problems came from bad RAM chips. Those are replaced (Kingston this time) and the system is behaving better.

NS under wine is still a crapshoot. Not sure what it is -- maybe something with saving user files. They get corrupted very easily.

It could also be something with accessing the audio hardware. I use Jack a lot, and quite often, even after shutting down the Jack server, NS won't launch. Or, it launches it gets to "initializing dictation" and then crashes -- or sometimes it lets me get as far as turning on the microphone before crashing. After that, forget it, the user files are hosed. (I don't know why the program is doing destructive writes in the user files, which then require a clean shutdown to undo. No sandbox for temporary data that would then be ignored when loading a user? Bad engineering...)

Or maybe one of my replacement RAM chips is also bad...? Who knows.

It's livable. But, if I have to reboot anyway to get NS to work well, it may lead me to boot into Windows for that purpose since it will just work better there. (Not to complain too much -- I'm amazed NS+wine works at all, considering how deep into the system it has to go.)

James

---

### Post by dewdrop_world on 2010-10-18
> **dewdrop_world said:**
> Or maybe one of my replacement RAM chips is also bad...? Who knows.

After 8 hours of continuous memory testing last night and no faults, I can safely say this isn't it.

Anyway, DNS+wine is an "unsupported configuration" :P (in my prior job as tech-support for a major BI platform, this was code for "what the hell were you thinking, running it that way?! - and, no we won't help you") and it's lucky to be able to use it at all.

James

---

### Post by dewdrop_world on 2010-10-19
Unfortunately, I have to downgrade my experience with NS + wine. Today -- fresh reboot of Linux, freshly restored user files from a backup, and it crashed while initializing dictation.

I'm fine with workarounds like rebooting and restoring user files from a backup if I can be reasonably sure it will work. If I'm not sure it's going to work and I have to reboot anyway, then I'll reboot into an environment (winbloze) where I know NaturallySpeaking will work.

Maybe sometime later I'll try the virtual box solution, no time at the moment.

James

---

### Post by MauroJB on 2011-04-21
Noob speaking, so i apologize early but:
If i run DNS 8 or 9 on wine, i use ubuntu, and i want to dictate an email on thunderbird, is this possible? 
i mean when running wine, is this like emulating windows, and i doesn´t share info with linux?
I don't know if i'm beeing clear on this.

In a nutshell i want to run DNS and be able to dicate mails.

---

### Post by bodhi.zazen on 2011-04-21
Last time I looked, integration was lacking.

You can dictate into the dragon notepad, you would then need to copy - paste into your email.

You might want to take a look at shpinx.

---

### Post by csc260412 on 2012-04-26
Hi All,
 
Does anyone know whether Dragon Naturally Speaking can be attached for input to another program? In other words, instead of using the keyboard as input, can  Dragon Naturally Speaking be used to provide input text? 
 
The environment/context in which it (Dragon) is to be used is a trainer system for training crew on how to operate equipment. Usually, the training is performed with an instructor who sets up a number of scenarios. But, to achieve this, there is a substantial amount of workload placed upon the Instructor. So, to minimise the workload on the instructor so that he/she is not overwhelmed by the mechanics of driving the simulation system, we would like to introduce automation using Dragon Naturally Speaking. 
 
Can anyone confirm whether Dragon Naturally Speaking can be used to provide output text (as input) to another program?
 
Thanks,
Pete

---

### Post by bodhi.zazen on 2012-04-26
As far as I know, only programs running in wine, dragonpad or notepad.

You can copy - paste to other apps, but not directly input to apps running outside of wine.

pocketsphinx is sort of the up and coming tool in linux, not tried it yet.

---

