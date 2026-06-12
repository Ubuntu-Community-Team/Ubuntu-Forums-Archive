---
title: "Installing programs problem"
date: 2010-11-04
forum: Wine
---

### Post by nigel on 2010-11-04
Ubuntu: 10.10
Wine:1.2.1-0ubuntu1 (wine1.2)

Hi all

I am trying to install
Fireworks MX and
Dreamweaver MX

I have copied them both their directorys from CD to my Home directory
I have set the .exe files to be executable
and I have also set it so that exe files will be opened by wine



But no matter what i do i can't get the install to begin

Double clicking on the exe file in my directory does nothing, apart from makeing the cursor show the busy circle for about 20 secs
right clicking the exe and selecting open with wine thingie does exactly the same

I have followed the instructions given in the winehq wiki to do it via terminal

**Instructions **
from the [winehq wik]("http://wiki.winehq.org/FAQ#head-312130506d4585c973df1d88538b11945193c41d")i

basically get into the directory & run the exe

nigel@nigel-A7N8X-X:~$ cd dreamweaver
nigel@nigel-A7N8X-X:~/dreamweaver$ ls
dreamweaver.exe  Extending Dreamweaver MX
nigel@nigel-A7N8X-X:~/dreamweaver$ wine dreamweaver.exe 
nigel@nigel-A7N8X-X:~/dreamweaver$

however as soon as i run it, it just goes straight to the command prompt, no errors nothing.

Anyhelp would be appreciated as I am probably missing something obvious

But for the life of me I can't spot it

---

### Post by cogadh on 2010-11-04
Odd, that shouldn't be happening at all. Even if Wine encounters a problem running the install, it shouldn't just do nothing, it should report a problem, especially when run from the terminal. You might have a problem with Wine itself. I'd do an uninstall/reinstall of Wine and make sure you delete the .wine directory from your home directory. NOTE: this will delete anything else you might have installed in Wine. If you want/need to save anything, just re-name the directory instead.

---

### Post by nigel on 2010-11-05
Okey Doke tried that got

nigel@nigel-A7N8X-X:~/dreamweaver$ wine dreamweaver.exe
wine: created the configuration directory '/home/nigel/.wine'
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cfdc
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\xpti.dat" 1 536870916 (nil) (nil) 0x191d24 (nil)
fixme:iphlpapi:NotifyAddrChange (Handle 0x2f2e8d8, overlapped 0x2f2e8e0): stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\compreg.dat" 1 536870916 (nil) (nil) 0x1daa01c (nil)
wine: configuration in '/home/nigel/.wine' has been updated.
nigel@nigel-A7N8X-X:~/dreamweaver$ 

Left it for a while nothing happened, ran the command again and it just went straight to the command prompt with no errors nothing

Am i missing something obvious, this is a fairly new install and i haven't touched wine(the program not the nectar) until yesterday, i have uninstalled it, i have deleted the .wine directory, reinstalled but nothing seems to make it work

Should i try the 1.3 branch?, I have avoided it as i have not a sausage of an idea how to install it, or for that matter winetricks?

---

### Post by cogadh on 2010-11-05
Looks like you are trying to install DW without first configuring Wine. You need to run winecfg (Applications > Wine > Configure Wine) before you install anything.

As for 1.3.x, its easy to install: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by lkjoel on 2010-11-05
> **nigel said:**
> Ubuntu: 10.10
Wine:1.2.1-0ubuntu1 (wine1.2)

Hi all

I am trying to install
Fireworks MX and
Dreamweaver MX

I have copied them both their directorys from CD to my Home directory
I have set the .exe files to be executable
and I have also set it so that exe files will be opened by wine



But no matter what i do i can't get the install to begin

Double clicking on the exe file in my directory does nothing, apart from makeing the cursor show the busy circle for about 20 secs
right clicking the exe and selecting open with wine thingie does exactly the same

I have followed the instructions given in the winehq wiki to do it via terminal

**Instructions **
from the [winehq wik]("http://wiki.winehq.org/FAQ#head-312130506d4585c973df1d88538b11945193c41d")i

basically get into the directory & run the exe

nigel@nigel-A7N8X-X:~$ cd dreamweaver
nigel@nigel-A7N8X-X:~/dreamweaver$ ls
dreamweaver.exe  Extending Dreamweaver MX
nigel@nigel-A7N8X-X:~/dreamweaver$ wine dreamweaver.exe 
nigel@nigel-A7N8X-X:~/dreamweaver$

however as soon as i run it, it just goes straight to the command prompt, no errors nothing.

Anyhelp would be appreciated as I am probably missing something obvious

But for the life of me I can't spot it
Try PlayOnLinux.
```
sudo wget http://deb.playonlinux.com/playonlinux_UBUNTUCODENAME.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux
```
Where UBUNTUCODENAME can be from hardy to karmic.
If you are running lucid or later, use karmic as the code name.

---

### Post by nigel on 2010-11-05
Ok I'm back

What i have tried
1)
delete .wine diectory
reinstall wine
configure wine (use defaults)
ran the command, and it went straight to the command prompt again

2)
delete .wine diectory
reinstall wine
configure wine (set as windows 2000)
ran the command, and it went straight to the command prompt again

3)
delete .wine diectory
reinstall wine
configure wine (set as windows ME)
ran the command, and it went straight to the command prompt again

4)
delete .wine diectory
Uninstall wine
install 1.4 version
configure wine (set as windows 2000)
ran the command, and it went straight to the command prompt again

5)
recopied the source file from the cd
delete .wine
ran the command, straight to the command prompt

6)
Pulled out some hair, swore at the computer and kicked the desk, (them realised I was barefoot)

Is there someway i may have prevented error messages showing?
I am guessing that uninstalling and reinstalling wine will have ensured that i couldn't have done that


Regarding playon linux from what i read it's just a frontend for script to automate installs? Is it likely to help?, after all from what i have read I am doing everything correctly, so it should work

---

### Post by nigel on 2010-11-05
Wahay I got the dreamweaver install starting, i ended up navigating to the cd via terminal and running the commands there.

It has demanded mdac

But apparently i can ignore that and continue, so we will see, not sure why the directories copied to the hard drive didn't work but, i'll know for next time, and besides all those half remembered linux commands have finally been exercised.

Thanks for the Help guys, although i can't guarantee I won't be back

---

### Post by alvinmoneypit on 2010-11-06
Hi,

I'm also running 10.10.  I cannot load windows programs through it's installer.  The dialog says "blocked:wine start/unix"  inside says"The file 'path .exe' is not marked as executable.  If it was downloaded or copied from an untrusted source it may be dangerous to run." For more details[read file].

I also uninstalled wine, etc.  upgrade to 1.3. Read the "how to's" - they never mention a problem like this nor did the FAQ at wine HQ. 

On my 1.1.2 install or whatever the default stable install is from Ubuntu libraries, I also installed the Q4 wine, a helper app I guess.  It seemed to work, but after I installed my programs they did not work so I was trying to do it like they say at the wine HQ and just use the basic program. 

 The installs I did all had this same problem indicates to me my OS configuration is blocking it or not allowing wine to work right.  The installer programs have the wine icon on the program graphic so it looks like it realises the program that needs to run it, but something is amiss.Is there some thing wrong with my wine configuration? or how my 10.10 Maverick is configured?

I;m just getting Ubuntu as my everyday OS and just starting to use the terminal a little so I'm hesitant to "sudo" things up while I'm building this system - I just want to be sure of my steps, but Wine was one of the first things I put in.
________________________________________________________________________________________

Hold the phone - marking the installer as executable in permission allowed installation, but neither of the 2 programs are seeing the media

---

### Post by nigel on 2010-11-06
Yep If you search on that error you'll find more info, basically its a security measure, just mark the file as executable and it will run.

If you are using a CD to install from, you can't do that because the CD is readonly, so you need to install via terminal

For me basically i do this (never needed to use sudo)

I type "mount" to find what my Cd is mounted as
nigel@nigel-A7N8X-X:~$ mount
then change to the cd with its name in speech marks if it has spaces in it
nigel@nigel-A7N8X-X:~$ cd /mount/"Studio MX Plus"
nigel@nigel-A7N8X-X:/media/Studio MX Plus$ cd "Dreamweaver MX"
and then run the install command there, as it is running in terminal you don't have to worry about setting it as executable




> **alvinmoneypit said:**
> Hi,

I'm also running 10.10.  I cannot load windows programs through it's installer.  The dialog says "blocked:wine start/unix"  inside says"The file 'path .exe' is not marked as executable.  If it was downloaded or copied from an untrusted source it may be dangerous to run." For more details[read file].

I also uninstalled wine, etc.  upgrade to 1.3. Read the "how to's" - they never mention a problem like this nor did the FAQ at wine HQ. 

On my 1.1.2 install or whatever the default stable install is from Ubuntu libraries, I also installed the Q4 wine, a helper app I guess.  It seemed to work, but after I installed my programs they did not work so I was trying to do it like they say at the wine HQ and just use the basic program. 

 The installs I did all had this same problem indicates to me my OS configuration is blocking it or not allowing wine to work right.  The installer programs have the wine icon on the program graphic so it looks like it realises the program that needs to run it, but something is amiss.Is there some thing wrong with my wine configuration? or how my 10.10 Maverick is configured?

I;m just getting Ubuntu as my everyday OS and just starting to use the terminal a little so I'm hesitant to "sudo" things up while I'm building this system - I just want to be sure of my steps, but Wine was one of the first things I put in.
________________________________________________________________________________________

Hold the phone - marking the installer as executable in permission allowed installation, but neither of the 2 programs are seeing the media

---

