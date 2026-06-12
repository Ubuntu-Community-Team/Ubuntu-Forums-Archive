---
title: "Vue 9 can't find graphics driver"
date: 2011-01-16
forum: Wine
---

### Post by miha2 on 2011-01-16
[FONT=Times New Roman]What should I do?[/FONT] [FONT=Times New Roman]The video [/FONT]works just fine on my Linux, but the problem is in the graphics. I know back from Windows, if Vue can't do anything with drivers, it switches to software OpenGL/something like this. Here, it says:
> An unexpected error occured with display plugin loading, try re-instaling vue or contact E-On Software Support. Graphics settings has been set to software OpenGL engine. 

> No plugin found for real time graphics
check for details in C:/users/...plugin-selection_rtapi_log.txt file
What are my steps for it to solve? The window shows up, and I think that the problem is only in graphics driver. My graphics adapter is Intel G33 Express Chipset.

---

### Post by cogadh on 2011-01-16
Any errors that are produced by the application itself are mostly meaningless. Run the app from the terminal to get the error output from Wine, that will (usually) tell us what is really going on.

---

### Post by miha2 on 2011-01-17
Impossible. All the files and program itself is called "vue 9 whatever.exe", not "vue_9_whatever.exe". So, from terminal, it would run ".../program files/vue", not "/vue 9 edition (xStream, other)"

---

### Post by cogadh on 2011-01-17
Not impossible, just put a "\" before each space or put the entire path (in "Windows form") in quotation marks:
```
wine vue\ 9\ edition.exe

OR

wine "C:\Program Files\vue 9 edition\vue 9 edition.exe"
```
Obviously I don't know the actual path or file names, so you'll have to substitute the correct ones.

---

### Post by miha2 on 2011-01-17
Oh, cool. Didn't know. So, it writes it very simple then - "Could not find dependent assembly L"VC80.CRT", and 2 installed files. It can't find the path to them, don't know why.

---

### Post by cogadh on 2011-01-17
That's pretty straightforward, the app is looking for MS Visual C++ Runtime, which you can easily install with [winetricks]("http://wiki.winehq.org/winetricks"), just install the vcrun2005 package. 

As for the installed files it can't find, that's usually an indication that Wine had a problem setting the application path correctly. You can resolve that by changing directories to where the app is installed, then "wineing" the executable:
```
cd ~/.wine/drive_c/Program\ Files/<vue installation directory>
wine <vue executable name>.exe
```
Again, just replace the paths and names I used with the correct ones.

---

### Post by miha2 on 2011-01-17
What do you mean, "I used with the correct ones"? What I mean is that the file that is located in "plugins" folder is asking for files that are located in "Application" folder.

---

### Post by cogadh on 2011-01-17
I used fake path and file names in that example, you need to replace those with the correct ones.

I'm not sure I understand what exactly you mean about the files it is asking for. Perhaps you should copy the full error output from the terminal and paste it here, it might make more sense to me.

---

### Post by miha2 on 2011-01-17
[email]linux@ubuntu:~/.wine[/email]/drive_c/Program Files/e-on software/Vue 9 xStream$ fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub
fixme:winsock:convert_aiflag_w2u Unhandled windows AI_xxx flags 400
fixme:winsock:convert_aiflag_w2u Unhandled windows AI_xxx flags 400
err:module:import_dll Library VueOGL.eon (which is needed by L"C:\\Program Files\\e-on software\\Vue 9 xStream\\Plugins\\Display\\v7OGLAdapter.eon") not found
err:module:import_dll Library v7EonOgl.eon (which is needed by L"C:\\Program Files\\e-on software\\Vue 9 xStream\\Plugins\\Display\\v7OGLAdapter.eon") not found

---

### Post by miha2 on 2011-01-17
So, as you can see. V7OGLAdapter.eon requires VueOGL.eon and V7EonOgl.eon[EMAIL="linux@ubuntu:%7E/.wine"]
[/EMAIL]

---

### Post by 4Joshy on 2011-03-02
> **miha2 said:**
> So, as you can see. V7OGLAdapter.eon requires VueOGL.eon and V7EonOgl.eon[EMAIL="linux@ubuntu:%7E/.wine"]
[/EMAIL]

Hello Miha, could you solve that problem? I experience the same thing here. Vue 7 runs fine with wine, but with Vue 9 and Kubuntu, i get the same error. I must say that my board only supports software rendering. Anyone here running Vue 9 with Linux? Who can help? Is VueOGL.eon something the Wine Team can produce maybe uppon the vue windows stuff?

Best regards from Berlin!
Mike

 [U]


[/U]

---

