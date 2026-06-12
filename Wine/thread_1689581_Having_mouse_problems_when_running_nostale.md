---
title: "Having mouse problems when running nostale"
date: 2011-02-17
forum: Wine
---

### Post by &lt;3Kitty&lt;3 on 2011-02-17
Ok I had it working for a set period of time, but for some reason it won't work on me now. The mouse is registered on the game, and I can click on menus and hot keys, but when it comes to using the mouse for moving or clicking on anything in the, I guess you'd call it the game area, like players or to move around it doesn't register. It does however register enough to highlight the names of people or items if I however the mouse over it, but it wont allow me to click. Anyone know what I'm missing here?

Is there maybe some kind of winetricks thing I need to download to fix my mouse problem or something? I've seen people ask a similar question like this about it happening on WoW, but they never got answered. 

This is honestly my first time using Ubuntu, and Wine so I really don't have much to go on, other than the advice of another person who's kind of pointed me in the right direction.

Another note about it is that the left and right click on the mouse don't register, but I can still click on menu's and what not. Someone on here has to have some kind of advice for me.

---

### Post by &lt;3Kitty&lt;3 on 2011-02-18
Ok since no one here seems to know what to do I searched and found this:

 regedit 
  In the resulting window, choose 
  HKEY_CURRENT_USER - Software - Wine 

  Schelkaem LMB on Wine then RMB - New - Key 
  Title: **Direct 3D** 
  RMB - New - Srokove value - The title - **DirectDrawRender,** after I edit and enter a value: **Opengl** 

  By the same principle has 4 elements: 
  **Nonpower2Mode** - meaning **repack** 
  **OffScreenRenderingMode** - meaning **fbo** 
  **PixelShaderMode** - meaning **enabled** 
  **RenderTargetLockMode** - to **auto.** 

  All closed - Reload - earned.

It was on a russian Ubuntu site. Only problem here now is that some have the names didn't translate over and now I'm asking you guys if you could fill in the blanks for me. Any got any ideas here?

---

### Post by &lt;3Kitty&lt;3 on 2011-02-18
In the terminal I can see a few errors/fixme notes. Maybe this will help?

fixme:shdocvw:PersistStreamInit_Load (0x165820)->(0x13b690)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x4a1c60:10; TargetFrameName 0x4a1c60:10)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Thu, 01-Jan-1970 00:00:30 GMT")
fixme:wininet:InternetSetFilePointer stub
fixme:wininet:InternetSetFilePointer stub
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14

That's just a few of them. If anyone needs anymore info or what not let me know and I'll post them here.

---

### Post by Ryuno-Ki on 2011-06-20
Just fixed that problem by me.

I use Lucid Lynx too and followed this instruction:

[http://board.nostale.co.uk/board103-nostale-co-uk/board107-bugs-complaints/board89-technical-help/p222715-why-can-t-i-move-my-character/#post222715](http://board.nostale.co.uk/board103-nostale-co-uk/board107-bugs-complaints/board89-technical-help/p222715-why-can-t-i-move-my-character/#post222715)

Short form: Open a terminal and enter:
winetricks -q directx9

I've tested and it works on my client.

Ryu

P.S.: Sorry, my first reply; just registered to answer ^^
P.P.S.: I'm afraid, I'm a German man and my English is quite bad,.

---

### Post by vanlong441 on 2011-09-09
thank you, winetricks -q directx9 worked! :P

---

