---
title: "Child Process Failed: No Such File or Directory"
date: 2010-07-19
forum: Wine
---

### Post by Spazmunki13 on 2010-07-19
Okay, so I recently came back to ubuntu. Being happy that my favorite game could run I decided to add a launcher to the Applications menu, yet no matter what I put in as the command I always get the same two outcomes.

If I open the file directly (/home/.wine/path/to/my/game.exe) I get a game error. If I open the file through wine (wine file///home/.wine/path/to/my/game.exe) or (file///home/.wine/path/to/my/game.exe) I get a "Child process failed: no such file or directory" error.

Now if I go into the folder and double click on the exe the game opens runs no problems at all.

I decided to open the exe through the terminal to get an output.

```
fixme:win:EnumDisplayDevicesW ((null),0,0x32e718,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e680,0x00000000), stub!
err:ole:CoGetClassObject class {5959df60-2911-11d1-b049-0020af30269a} not registered
err:ole:CoGetClassObject no class object {5959df60-2911-11d1-b049-0020af30269a} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x32e6c0,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d8:ValidateVertexShader (0x4519e18 (nil) (nil) 0 (nil)): stub
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:d3d8:ValidatePixelShader (0x494b4e0 (nil) 0 (nil)): stub
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
fixme:d3d:device_resource_released Vertex buffer released while bound to a state block, stream 0
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #17:
fixme:d3d_shader:print_glsl_info_log     Vertex info
fixme:d3d_shader:print_glsl_info_log     -----------
fixme:d3d_shader:print_glsl_info_log     0(10) : warning C7050: "R4.w" might be used before being initialized
fixme:d3d_shader:print_glsl_info_log     0(11) : warning C7050: "R5.w" might be used before being initialized
fixme:d3d_shader:print_glsl_info_log     0(8) : warning C7050: "R2.w" might be used before being initialized
fixme:d3d_shader:print_glsl_info_log     0(9) : warning C7050: "R3.w" might be used before being initialized
```Hope someone can help me. :3

The game is Perfect World International by the way.

EDIT: Here's the error I get:

> Failed to execute child process "file:///home/matt/.wine/dosdevices/c:/Program Files/Perfect_World_International/element/elementclient.exe" (No such file or directory)

---

### Post by Spazmunki13 on 2010-07-20
Well I didn't technically fix the problem, but I found a way to make a working launcher for the game.

I made a shortcut in Virtual Box pointing to the location as if it were in Windows and copied into this folder /**user**/.wine/dosdevices/c:/users/**user**/Start Menu/Programs/ and copied the launcher that the installer placed in my Applications menu.

> env WINEPREFIX="/home/**user**/.wine" wine C:\\windows\\command\\start.exe /Unix /home/**user**/.wine/dosdevices/c:/users/**user**/Start\ Menu/Programs/**launcher**.lnkHope this helps anyone having similar problems. :3

EDIT: The launcher in windows pointed to "C:\Program Files\path\to\my\game.exe" In case you were wondering and in Linux the exe was placed in "/home/user/.wine/dosdevices/c:/Program Files/path/to/my/game.exe"

---

### Post by Alethaeia on 2010-11-12
Pardon the necromancy.  I am having the exact same problem creating a launcher for Winamp.  When i browse to the exe and run it, all goes well. When i make a launcher in the panel, it returns the same error as our friend has posted above.  I have tried going into dosdevices and drive_c with the same result.  Now, this isn't really something to throw my computer through the window over, but it would be nice to have a Winamp button.
Thanks for any input.
~

---

### Post by cwwilson721 on 2010-11-12
Both errors are being caused by improper paths. You need to either :
[LIST]
[*]Set an 'env' variable for the command
[*]Make sure EXACT path (with quotes, because blank spaces seem to befuddle Linux/wine sometimes) is shown to the executable.
[/LIST]
Example: I use World of Warcraft. There are TONS of blank spaces in the path. I also have a wineprefix, so setting the env variable is my preferred route.

```
env WINEPREFIX="/home/<USER>/.wine-wow" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl
```
Note the quotation marks, and replace <USER> with your username and rest of path info. If you juse use the regular .wine folder, change '.wine-wow' to '.wine' (Or wherever your wine install is).

The advantage of using a wineprefix is to have multiple programs use the same enviornment. In my case, if I was stupid enough to use Vent (GET MANGLER, PEEPS!), it allows keypresses to be passed thru WoW to Vent.

Hope this helped some.

Remember, if your path has spaces in it, USE QUOTES. And use EXACT PATH (i.e. '"/home/user/.../Program Files/...program.exe")

---

