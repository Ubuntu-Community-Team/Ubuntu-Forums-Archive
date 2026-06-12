---
title: "Ubuntu freezing when running WoW in wine."
date: 2010-10-06
forum: Wine
---

### Post by julianri on 2010-10-06
Hello

I have been trying to run WoW through wine 1.1.42 in Ubuntu 10.4.
I had succes installing the game. When i want to run it (in opengl mode ofc.), either the game crashes (error 132), or ubuntu freezes so that i have to cut the power to reboot the computer. I have also had a few times where i actually were able to play the game, but far most of the time either the game or ubuntu crashes. 

I am doing all this on a MSI ex600 laptop with a NVIDIA Geforce 8400M G 3D Graphic Card. 

Can anyone help me? please :)

Best regards Julian

---

### Post by cwwilson721 on 2010-10-06
A few questions:
[LIST=1]
[*]Why such an old wine version? Install the 1.3 wine.
[*]Do you have the proprietary drivers installed?
[*]Where does it freeze? Wide open spaces, in cities? What cities? In raids? Where?
[/LIST]

---

### Post by julianri on 2010-10-08
1. I have just installed the 1.3 beta version of wine.

2. Yes i have installed the only of two NVIDIA drivers making the output of "glxinfo | grep rendering" be "direct rendering: Yes" :)

3. It doesn't ever crash when I play the game. It is always when i run the WoW.exe file or press play from Launcher.exe.

When an error occurs, 4 different things tends to happen.

either i get following output in terminal:

[I]"X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  128 (GLX)
  Minor opcode of failed request:  27 (X_GLXCreatePbuffer)
  Serial number of failed request:  1620
  Current serial number in output stream:  1621"
[/I]

or the system freezes so the only thing i can do is moving the cursor(not able to click anything in ubuntu), so that i have to unplug the power.

or ubuntu restarts.

or this wow error comes up:

[I]"This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	Z:\home\hahpwnd\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:68BC66C5

The instruction at "0x68BC66C5" referenced memory at "0xFFFFFFFF".
The memory could not be "read"."[/I]


or very rarely:

The game just starts normally.

Hope you can help me. Thank you for taking time.

---

### Post by Technonick on 2010-10-18
I had this problem too on my Sony Vaio VGN-FE890 with the Geforce Go 7400.  I was running dual monitors.  One was the laptop screen and the other was a ViewSonic connected to the external VGA port.  At first Wow ran fine, but then I changed the resolution because I thought Wow would look better on my wide laptop screen.
Then it would crash every time with the error:

[I]"X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  128 (GLX)[/I]

The solution was to make Wow start in 1024x768 resolution again.

I edited the World of Warcarft/WTF/Config.wtf file, and changed:

[gxResolution]("http://www.wowwiki.com/index.php?title=CVar_gxResolution&action=edit&redlink=1") "1280x800"

to

[gxResolution]("http://www.wowwiki.com/index.php?title=CVar_gxResolution&action=edit&redlink=1") "1024x768"

Then rebooted and then ran wine Wow.exe and it worked. (I rebooted to let the Nvidia driver reload after Wow had crashed for the umpteenth time.)

Other than that,  you did not mention if you set:

SET gxApi "opengl"


In the same file.  That might do it too.

Good luck

---

### Post by devi59 on 2010-11-10
> **julianri said:**
> 
or the system freezes so the only thing i can do is moving the cursor(not able to click anything in ubuntu), so that i have to unplug the power.

I have that problem when playing Battle of the Immortals. I have ATI. Any suggestions? Do i need to get some info?

---

### Post by Thaskalas on 2010-11-10
If you are using the opengl switch and continuing to have the crashes, you might try running it natively with directx. My installation actually runs better with directx.

Hope this helps!

*Note: I have read that the opengl support in Cataclysm is supposed to be much better, so I'll try it again once the expansion goes live.

---

