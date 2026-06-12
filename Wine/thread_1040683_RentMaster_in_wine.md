---
title: "RentMaster in wine"
date: 2009-01-15
forum: Wine
---

### Post by donwait on 2009-01-15
I'm trying to run rentmaster on ubuntu so that i can finally kill my windows computer with a large sledge, but i keep having probs.

first some details 

you can get a copy of rentmaster at rentmaster.info they have a free trial download

the program is based on a borderland db, it is my understanding that this is all compiled together.

if i try and run on my computer i have a few issues

1st it takes about 10min for the initial screen to come up -- odd i thought :)

2nd if i try and put my license key in i cannot the author only made it so you can copy and paste, strangle him please, someone

3rd apparently i dont have a clipboard in this program

ok so what i have found from sys logs and terminal

__________________________________________________________________________
```


[email]travis@userv:~/.wine[/email]/drive_c/Program Files/RentMaster Inc/RentMaster$ wine RentMaster
fixme:dwmapi:DwmIsCompositionEnabled 0x30d074
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4d004
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4d004
fixme:dwmapi:DwmIsCompositionEnabled 0x30f518
fixme:dwmapi:DwmIsCompositionEnabled 0x30f758
fixme:dwmapi:DwmIsCompositionEnabled 0x30dc2c
--- this keeps repeating as long as the program runs


err:ole:CoGetClassObject class {dc1c5a9c-e88a-4dde-a5a1-60f82a20aef7} not registered
err:ole:CoGetClassObject no class object {dc1c5a9c-e88a-4dde-a5a1-60f82a20aef7} could be created for context 0x1
--- this came up when i clicked on a button in the program
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
--- this is repeated on and on and on
err:ole:CoGetClassObject class {dc1c5a9c-e88a-4dde-a5a1-60f82a20aef7} not registered
err:ole:CoGetClassObject no class object {dc1c5a9c-e88a-4dde-a5a1-60f82a20aef7} could be created for context 0x1
Killed
[email]travis@userv:~/.wine[/email]/drive_c/Program Files/RentMaster Inc/RentMaster$ 

```

__________________________________________________________________________

in sys logs i see

Jan 15 14:02:59 userv kernel: [ 5834.910788] Too big adjustment 32
and this is repeated until i kill the process is killed

__________________________________________________________________________

if i run ```

[email]travis@userv:~/.wine[/email]/drive_c/Program Files/RentMaster Inc/RentMaster$ WINEDEBUG=+channel1,+channel2 wine RentMaster.exe
```

i get
```

travis@userv:~$ WINEDEBUG=+channel1,+channel2 wine RentMaster.exe
wine: could not load L"C:\\windows\\system32\\RentMaster.exe": Module not found
travis@userv:~$ cd /home/travis/.wine/drive_c
[email]travis@userv:~/.wine[/email]/drive_c$ ls
Program Files  windows
[email]travis@userv:~/.wine[/email]/drive_c$ cd Program\ Files
[email]travis@userv:~/.wine[/email]/drive_c/Program Files$ ls
Common Files  Internet Explorer  RentMaster Inc
[email]travis@userv:~/.wine[/email]/drive_c/Program Files$ cd RentMaster\ Inc
[email]travis@userv:~/.wine[/email]/drive_c/Program Files/RentMaster Inc$ cd RentMaster
[email]travis@userv:~/.wine[/email]/drive_c/Program Files/RentMaster Inc/RentMaster$ ls
eula.rtf  RentMaster.chm  RentMaster.exe
[email]travis@userv:~/.wine[/email]/drive_c/Program Files/RentMaster Inc/RentMaster$ WINEDEBUG=+channel1,+channel2 wine RentMaster.exe
fixme:dwmapi:DwmIsCompositionEnabled 0x30d074
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4d004
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4d004
fixme:dwmapi:DwmIsCompositionEnabled 0x30f518
fixme:dwmapi:DwmIsCompositionEnabled 0x30f758
fixme:dwmapi:DwmIsCompositionEnabled 0x30f518
fixme:dwmapi:DwmIsCompositionEnabled 0x30f758
fixme:dwmapi:DwmIsCompositionEnabled 0x30f758
fixme:dwmapi:DwmIsCompositionEnabled 0x30df7c
fixme:dwmapi:DwmIsCompositionEnabled 0x30df7c
fixme:dwmapi:DwmIsCompositionEnabled 0x30f758
fixme:dwmapi:DwmIsCompositionEnabled 0x30d37c
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30e284
fixme:dwmapi:DwmIsCompositionEnabled 0x30e284
fixme:dwmapi:DwmIsCompositionEnabled 0x30e488
fixme:dwmapi:DwmIsCompositionEnabled 0x30e730
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30df34
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30e284
fixme:dwmapi:DwmIsCompositionEnabled 0x30e488
fixme:dwmapi:DwmIsCompositionEnabled 0x30e730
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30df34
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30e284
fixme:dwmapi:DwmIsCompositionEnabled 0x30e488
fixme:dwmapi:DwmIsCompositionEnabled 0x30e730
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30df34
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30e284
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30e488
fixme:dwmapi:DwmIsCompositionEnabled 0x30e730
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30df34
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
fixme:dwmapi:DwmIsCompositionEnabled 0x30e284
fixme:dwmapi:DwmIsCompositionEnabled 0x30f750
err:ole:CoGetClassObject class {dc1c5a9c-e88a-4dde-a5a1-60f82a20aef7} not registered
err:ole:CoGetClassObject no class object {dc1c5a9c-e88a-4dde-a5a1-60f82a20aef7} could be created for context 0x1
Killed
[email]travis@userv:~/.wine[/email]/drive_c/Program Files/RentMaster Inc/RentMaster$
```

---

### Post by hikaricore on 2009-01-16
Likely this title will not run under WINE.

What you may want to do is look into virtualization, IE making a VM (virtual machine) on your existing Linux system and installing some version of Windows inside that virtual machine.

Check out VirtualBox here:  [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

It is a fantastic and free VM solution.

Now I'm just assuming this isn't a game or anything, you will likely be able to run standard software in VM environment, but nothing with extensive 3D graphics for the time being (this is progressing rapidly however.)

---

### Post by donwait on 2009-01-30
what about a linux replacement, any ideas i have literally spent days on source forge etc trying to find something that would work. i run the lamp stack on my server already for vtiger witch is a php/sql based crm tool. if there is a similar tool i would be ecstatic. any ideas would me much appreciated. 
travis

---

