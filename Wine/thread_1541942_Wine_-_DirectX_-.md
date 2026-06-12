---
title: "Wine - DirectX -"
date: 2010-07-29
forum: Wine
---

### Post by Skyxn3t on 2010-07-29
Greetings to all,

I've installed Tomb Raider Underworld in Wine, everything installed fine but the problem is that when I run the game I get the following message:

```
"[COLOR="Red"]Tomb Raider: Underworld Error[/COLOR]"
"This game requires a DirectX9.0c capable graphics card. your card or driver does not support DirectX9.0c 3D Acceleration."
```

I've installed DirectX and my graphics card is DirectX capable so why do I still get this message? 

According to WineHQ this game works well on Wine.

---

### Post by Naitsirhc Hsem on 2010-07-29
winetricks direct x patch, or playonlinux (wine games frontend)

---

### Post by Skyxn3t on 2010-07-29
> **Naitsirhc Hsem said:**
> winetricks direct x patch, or playonlinux (wine games frontend)

I have installed winetricks what's next, I don't see any further steps in the winetricks website.

---

### Post by jsyl on 2010-07-29
Go to the folder where you downloaded it in Terminal
```
sh winetricks
```

---

### Post by Skyxn3t on 2010-07-29
> **jsyl said:**
> Go to the folder where you downloaded it in Terminal
```
sh winetricks
```

sh winetricks gives me a "Select a Package to Install" Dialog/Window, should I select "directx9" and install it? Will my game work after that? Or is there something else I should do?

---

### Post by Skyxn3t on 2010-07-29
I did what you said: sh winetricks
Then I installed DirectX and I still can't play the game I still get the same message, what else should I do? thanks.

---

### Post by jsyl on 2010-07-30
Try installing all of the d3dx packages at the same time
Tell me if it helps

---

### Post by Vaphell on 2010-07-30
what's your gfx card?

---

### Post by Skyxn3t on 2010-07-30
> **jsyl said:**
> Try installing all of the d3dx packages at the same time
Tell me if it helps

I tried that, did not help.


> **Vaphell said:**
> what's your gfx card?


NVIDIA Driver Version: 195.36.31 
Operating System: Fedora 13, Linux-x86_64

Graphics Processor: GeForce GTX 260M
Memory: 1024MB
Memory Interface: 256-bit

I get the same Directx message with "wine" and "wine.i686".

---

### Post by dino99 on 2010-07-30
try on a 32 bits installation, but you might post on "wine" subforum not here

---

### Post by 3Miro on 2010-07-30
Go to WineHQ and look on their forums for specific instruction for installation and playing the specific game that you have.

---

### Post by philinux on 2010-07-30
Moved to Wine forum.

---

### Post by Skyxn3t on 2010-07-30
> **3Miro said:**
> Go to WineHQ and look on their forums for specific instruction for installation and playing the specific game that you have.

It's not just that game I tried with other games and I still get the same DirectX message, it's driving me crazy since I've installed all the DirectX libraries and tried it on both the 32bit and 64bit version of wine.

---

### Post by Skyxn3t on 2010-07-30
> **3Miro said:**
> Go to WineHQ and look on their forums for specific instruction for installation and playing the specific game that you have.

 I tried to execute the game using the Terminal these are the messages that I got, they might help: 


```
[root@work Tomb Raider - Underworld]$ wine tru.exe 
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub! 
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered 
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered 
err:ole:create_server class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered 
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported 
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x17 
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems 
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat. 
err:d3d:InitAdapters Failed to get a gl context for default adapter 
Direct3D9 is not available without OpenGL.
```


Then After that I receive the dialog box: 
```

"Tomb Raider: Underworld Error" 
"This game requires a DirectX9.0c capable graphics card. your card or driver does not support DirectX9.0c 3D Acceleration."
```

---

### Post by asdfoo on 2010-07-30
from your log:

err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems 
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat. 
err:d3d:InitAdapters Failed to get a gl context for default adapter 
Direct3D9 is not available without OpenGL.


This means you don't have the correct drivers installed.
nvidia has 32-bit compat drivers with its 64bit drivers which all 32-bit programs require, it sounds like these are not installed.

When I download drivers from nvidia.com and install them, it asks if I want to install the 32-bit drivers to which I answer yes and this satisfies what Wine requires.

---

### Post by Skyxn3t on 2010-07-30
> **asdfoo said:**
> from your log:

err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems 
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat. 
err:d3d:InitAdapters Failed to get a gl context for default adapter 
Direct3D9 is not available without OpenGL.


This means you don't have the correct drivers installed.


Installed where? In Linux or in Wine? If you mean in Linux then I do have the correct drivers installed since I have 3D capabilities/effects. etc...
Or did you mean installing Windows Nvidia drivers in Wine?

---

### Post by asdfoo on 2010-07-30
> **Skyxn3t said:**
> Installed where? In Linux or in Wine? If you mean in Linux then I do have the correct drivers installed since I have 3D capabilities/effects. etc...
Or did you mean installing Windows Nvidia drivers in Wine?

Yes in Linux, no, they are not installed correctly, the output from Wine indicates there is no 32bit OpenGL libraries installed.

---

### Post by Skyxn3t on 2010-07-30
> **asdfoo said:**
> Yes in Linux, no, they are not installed correctly, the output from Wine indicates there is no 32bit OpenGL libraries installed.

How do I install 32bit OpenGL drivers in 64bit linux? I Googled it but didn't find anything.

---

### Post by asdfoo on 2010-07-31
> **Skyxn3t said:**
> How do I install 32bit OpenGL drivers in 64bit linux? I Googled it but didn't find anything.

I don't know the sanctioned way, but what works for me is going to nvidia.com, following the options under download, selecting 64bit linux.

I then stop X, sudo /etc/init.d/gdm stop
login on tty1, sudo sh NVIDIA<tab>

answer yes to everything except checking the internet to download, answer yes to installing 32bit compat libraries, answer yes to remaining questions

sudo /etc/init.d/gdm start

login to the desktop again and it should work fine

As this is just the Wine subforum, you might be better off asking for the "right" way to do the above in a different subforum.

---

