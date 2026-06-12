---
title: "WINE drives"
date: 2009-01-20
forum: Wine
---

### Post by MobiusCoffee on 2009-01-20
I am using Wine 1.1.13 in Ubuntu Hardy, and I am having a strange problem where when I try to access the "Drives" tab in winecfg.  All I get is the message: "Failed to connect to the mount manager, the driver configuration cannot be edited."

[IMG]http://i116.photobucket.com/albums/o3/Kefga_X/Screenshot-Wineconfiguration.png[/IMG]

So, after googling and being a little lost, I found [this]("http://www.nabble.com/Can%27t-configure-wine-drives.-td21227268.html") which made me think my problem was running Wine in sudo, but I don't remember ever doing that.

running "winecfg" in the terminal, then switching to the "Drives" tab has this output:

```
~$ winecfg
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
err:winecfg:open_mountmgr failed to open mount manager err 2

```

So, I am really curious.  What is wrong and what should I do?  I'm by no means an expert with linux, but I am fairly comfortable with some harder stuff.  Please, if anyone knows what's wrong, help me out or point me in the right direction.

Edit:
I found a solution to this after searching some more.  I found  [this command]("http://wiki.winehq.org/FAQ#head-f60a1aeeb2e4ef08a9b26dd38fd4ea2b1608f358"):

```
sudo rm -rvf ~/.wine
```

Everything seems to be fine now.

---

### Post by Canucker25 on 2009-05-13
I'm having the same problem and that command is not working.

---

### Post by jigme on 2009-06-16
So am I. +1

---

### Post by phillies on 2009-06-22
so am I

even rebuilding wine from source (some folks suggested that the packages might be defect) with latest git version (1.1.24) did not fix it.

When enabling full debug output (WINEDEBUG=+all winecfg) the error seems to be:
"Failed to connect to the mount manager, the drive configuration cannot be edited."

Which appears several times caused by different components.

---

### Post by phillies on 2009-06-22
I found a solution to my version of the problem: Since I use CUDA I had to use the NVIDIA 185 beta drivers (as ***buntu does/did not provide drivers with CUDA support). I now reverted to 180.22 (which are stable for Hardy and Intrepid but not officially supported by jauntys newer X server). So I had to edit /etc/gdm/gdm.cfg and add -ignoreABI to the server command (somewhere close to the end of the config file)
Not X runs again and wine does so too.
Isn't it nice that a graphics driver problem causes an error in the mount manager? I love intelligently designed software....

---

### Post by r2ramos on 2010-02-23
[/QUOTE]
Edit:
I found a solution to this after searching some more.  I found  [this command]("http://wiki.winehq.org/FAQ#head-f60a1aeeb2e4ef08a9b26dd38fd4ea2b1608f358"):

```
sudo rm -rvf ~/.wine
```Everything seems to be fine now.[/QUOTE]


Moebios, ese código, por si no lo sabes, borra completamente el directorio wine

---

### Post by Progressive on 2010-02-24
Same problem!

By the way, for anyone who needs to access their cd rom drive and the devices tab isn't working even with that command, you can do a symlink in your ~/.wine/dosdevices directory.

sudo ln -s path_name_here  ~/.wine/dosdevices/e:

or if you don't want to use e: you can change it to whatever as long as no other drive is in that slot.

Your cdrom directory is usually in your /media/cdrom0 folder

that would come out to

```
sudo ln -s /media/cdrom0  ~/.wine/dosdevices/e:
```

worked for me anyways

---

### Post by nmyrick on 2010-08-03
This worked for me.  Thanks.

---

### Post by deadlytackler on 2011-01-18
> **MobiusCoffee said:**
> I am using Wine 1.1.13 in Ubuntu Hardy, and I am having a strange problem where when I try to access the "Drives" tab in winecfg.  All I get is the message: "Failed to connect to the mount manager, the driver configuration cannot be edited."

[IMG]http://i116.photobucket.com/albums/o3/Kefga_X/Screenshot-Wineconfiguration.png[/IMG]

So, after googling and being a little lost, I found [this]("http://www.nabble.com/Can%27t-configure-wine-drives.-td21227268.html") which made me think my problem was running Wine in sudo, but I don't remember ever doing that.

running "winecfg" in the terminal, then switching to the "Drives" tab has this output:

```
~$ winecfg
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
err:winecfg:open_mountmgr failed to open mount manager err 2

```So, I am really curious.  What is wrong and what should I do?  I'm by no means an expert with linux, but I am fairly comfortable with some harder stuff.  Please, if anyone knows what's wrong, help me out or point me in the right direction.

Edit:
I found a solution to this after searching some more.  I found  [this command]("http://wiki.winehq.org/FAQ#head-f60a1aeeb2e4ef08a9b26dd38fd4ea2b1608f358"):

```
sudo rm -rvf ~/.wine
```Everything seems to be fine now.

Thanks it solved the problem, mow its mapping the drive. also resolved the disk space issue.

---

### Post by seyednaser on 2011-07-20
> **MobiusCoffee said:**
> I am using Wine 1.1.13 in Ubuntu Hardy, and I am having a strange problem where when I try to access the "Drives" tab in winecfg.  All I get is the message: "Failed to connect to the mount manager, the driver configuration cannot be edited."

[IMG]http://i116.photobucket.com/albums/o3/Kefga_X/Screenshot-Wineconfiguration.png[/IMG]

So, after googling and being a little lost, I found [this]("http://www.nabble.com/Can%27t-configure-wine-drives.-td21227268.html") which made me think my problem was running Wine in sudo, but I don't remember ever doing that.

running "winecfg" in the terminal, then switching to the "Drives" tab has this output:

```
~$ winecfg
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
err:winecfg:open_mountmgr failed to open mount manager err 2

```So, I am really curious.  What is wrong and what should I do?  I'm by no means an expert with linux, but I am fairly comfortable with some harder stuff.  Please, if anyone knows what's wrong, help me out or point me in the right direction.

Edit:
I found a solution to this after searching some more.  I found  [this command]("http://wiki.winehq.org/FAQ#head-f60a1aeeb2e4ef08a9b26dd38fd4ea2b1608f358"):

```
sudo rm -rvf ~/.wine
```Everything seems to be fine now.


Thanks man. It totally saved me from malfunctioning of wine.
Merci baucoup.

---

### Post by Deven_ on 2012-12-12
> **Progressive said:**
> Same problem!

By the way, for anyone who needs to access their cd rom drive and the devices tab isn't working even with that command, you can do a symlink in your ~/.wine/dosdevices directory.

sudo ln -s path_name_here  ~/.wine/dosdevices/e:

or if you don't want to use e: you can change it to whatever as long as no other drive is in that slot.

Your cdrom directory is usually in your /media/cdrom0 folder

that would come out to

```
sudo ln -s /media/cdrom0  ~/.wine/dosdevices/e:
```worked for me anyways
Thanks alot Progressive :)))) searched alot for solution your trick worked million thanks:guitar:

---

