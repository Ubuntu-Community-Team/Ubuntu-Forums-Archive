---
title: "Alien Swarm Source SDK"
date: 2010-08-08
forum: Wine
---

### Post by fishkid257936 on 2010-08-08
I need help running alien swarm source sdk (I want to run hammer). here is the term output:

fixme:ole:CoInitializeSecurity (0x434660,-1,(nil),(nil),4,3,(nil),0,(nil)) - stub!
err:module:attach_process_dlls "tier0.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\<name>\\.PlayOnLinux\\wineprefix\\Steam\\drive_c\\Program Files\\Steam\\steamapps\\common\\alien swarm\\bin\\SDKLauncher.exe" failed, status c000001d

---

### Post by fishkid257936 on 2010-08-09
please help...

---

### Post by geoffjay on 2010-08-09
What version of wine are you running this with? I'm assuming that you've installed the Steam GUI and added Alien Swarm there, is that correct?

---

### Post by fishkid257936 on 2010-08-09
Wine Version 1.2 running in PlayOnLinux. Yes I have the steam client installed. Should I change the version of wine?

---

### Post by geoffjay on 2010-08-09
I just realized that you're trying to use the SDK and not the game itself. Does the game work for you?

Also if you're not already using the wine PPA I would suggest trying that, you can add it by doing:

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update && sudo apt-get upgrade

---

### Post by fishkid257936 on 2010-08-09
I don't think the game works because of pixel shaders.

---

### Post by geoffjay on 2010-08-10
Aren't pixel shaders taken care of by the GPU? What kind of card do you have?

---

### Post by fishkid257936 on 2010-08-10
GeForce2 MX/MX 400

---

### Post by geoffjay on 2010-08-10
I just tried running the SDK and Hammer loaded fine. I'm on a 10.04 x86_64 install with 2.6.32-23, and wine-1.2. I'm pretty sure that I installed Steam using winetricks as well.

It might just be a typo but in your original post the launch line "Z:..." has a space in Steam, is it possible that it's not going to the correct location and failing there?

---

### Post by fishkid257936 on 2010-08-10
huh. different error now. err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Steam\\steamapps\\common\\alien swarm\\bin\\SDKLauncher.exe" failed, status c000001d

---

### Post by geoffjay on 2010-08-10
Have you tried running SDKLauncher.exe directly using wine?

eg.
$ wine C:\\Program\ Files\\Steam\\steamapps\\alien\ swarm\\bin\\SDKLauncher.exe

---

### Post by fishkid257936 on 2010-08-10
let me try installing it in that location.

EDIT: oh and that is not the location. this is the location: /home/<name>/.PlayOnLinux/wineprefix/Steam/drive_c/Program Files/Steam/steamapps/common/alien swarm/bin

---

### Post by geoffjay on 2010-08-10
Isn't that where it's installed already? I think that's the default location.

---

### Post by fishkid257936 on 2010-08-10
I have playonlinux.

---

### Post by geoffjay on 2010-08-10
Playonlinux is just a front end to wine.

What do you get if you run:

$ WINEPREFIX=~/.PlayOnLinux/wineprefix/Steam/ wine C:\\Program\ Files\\Steam\\steamapps\\alien\ swarm\\bin\\SDKLauncher.exe

---

### Post by fishkid257936 on 2010-08-16
Sorry about ignoring this i was on vacation. It is actually ```
WINEPREFIX=~/.PlayOnLinux/wineprefix/Steam/ wine C:\\Program\ Files\\Steam\\steamapps\\common\\alien\ swarm\\bin\\SDKLauncher.exe
```It gives me this:```
err:module:attach_process_dlls "tier0.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Steam\\steamapps\\common\\alien swarm\\bin\\SDKLauncher.exe" failed, status c000001d

```

---

### Post by ToiletMaster on 2010-08-17
hey hope you dont mind if i butt in but i'm also having problems playing alienswarm on ubuntu.
i was able to go in to the main screen. but once i went into the main screen there wasn't any sound detected. i dont know why but then when i tried finding games. it could, but once i tried connecting, it the whole turns white and at the corner i'll just get one loading there and the whole thing hangs. anyone can help? i have wine 1.3 installed and also playonlinux.

---

### Post by fishkid257936 on 2010-08-19
bump. TolietMaster, please post this in a separate forum. I am not talking about the alien swarm application but the source sdk.

---

### Post by geoffjay on 2010-08-27
Hey, also sorry about the big delay, I too was on vacation. I read a similar post with the same wine error that suggested a permissions issue. What's the output from:

$ find ~ -iname 'tier0.dll' -exec ls -al {} \;

Something else to try if you already haven't would be to:

$ mv ~/.PlayOnLinux ~/.PlayOnLinux.bak
$ mv ~/.wine ~/.wine.bak

and try to reinstall it. I used winetricks to install the Steam GUI and it seems to work, to do that I think you just have to do

$ winetricks steam

---

### Post by fishkid257936 on 2010-08-27
-rwxrwxr-x 1 name name 253952 2010-08-05 18:09 /home/name/.PlayOnLinux/wineprefix/Steam/drive_c/Program Files/Steam/steamapps/common/alien swarm/bin/tier0.dll

---

