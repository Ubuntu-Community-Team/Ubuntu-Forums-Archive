---
title: "World of Warcaft won't start"
date: 2010-08-21
forum: Wine
---

### Post by ocajublinky on 2010-08-21
I have looked most everywhere for a solution but I just can't seem to find one. Maybe you guys can help me.

In terminal I enter [HTML]wine wow.exe[/HTML]
it then prints[HTML]fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library DivxDecoder.dll (which is needed by L"H:\\Wow.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"H:\\Wow.exe" failed, status c0000135
[/HTML]

thoughts?

I have install the suggested winetricks, the only only thing I can think of is that it told be to "simply add -opengl to the end of your WoW launcher. (Recommended for first run after CD or download)." but I am still unclear as to what "add -opengl to the end of your WoW launcher" means. 
Thank you for your time

---

### Post by ajgreeny on 2010-08-21
I have no idea about wow, not being a gamer, but I see in the error it talks about **Wow.exe**, not **wow.exe** as in your command.  Is this significant, Linux being case sensitive?

---

### Post by cwwilson721 on 2010-08-21
'-opengl' at the end of the launcher is easy.

Right click your WoW launcher in your menu (Applications > Wine > Programs > World of Warcraft > World of Warcraft), and select either "Add app to panel" or "Add app to Desktop". Right click the new icon, select 'Properties', then in the Command box, add (at the end of that command) -opengl

I use this method so I can do complete WoW folder copies between Windows and wine, and not have to edit the wtf configure file. Just easier for me

See if that helps

---

### Post by ocajublinky on 2010-08-21
thats cww that helped out and fixed it

---

