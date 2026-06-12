---
title: "Infecting .exe under Ubuntu"
date: 2009-03-31
forum: Security
---

### Post by zett on 2009-03-31
Hi i have big problem with virus W32/Parite.B which infects .exe on my ubuntu (games).
The problem is that i cannot play this games because this virus infect this exe...example. on WoW i get infection and if i try to run it on wine i get message with Floating point error.
I dont know how i can protect from this virus x(
I reinstalled the game but the viruse come again....
I set privilegese for writing to file to root but virus come again.
Help me please :(

I have installed ClamAV with latest signature...but he cant protect me or disinfect this file...only remove it x(

---

### Post by netwarriorwy on 2009-03-31
Hi there!
I've never had a problem like that,but lets see if I can help.
First of all that _win32/pariteB_ is the signature name that Panda gives to that virus. O:)
Here is the explanation of how that virus works (in windows):

[COLOR="Navy"][http://www.configurarequipos.com/infovirus435.html]("http://www.configurarequipos.com/infovirus435.html")[/COLOR]

Here is how to desinfect it :

1. Try using a Nabble tool (like Ccleaner in windows).
2. Try passing the Panda AV for Linux.
3. To be sure try Kaspersky for Linux.

They say its a low category virus so it shouldn't be a big problem.

I think it's infecting the Wine area that virtualizes Windows behaviour. So you can pass either Panda or Kaspersky by that area.

Hope that helps! Good Luck!

---

### Post by bodhi.zazen on 2009-03-31
There are increasing reports of windows malware running in wine.

I think you may need to remove your ~/.wine and start again.

See also the comments on wine here : [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by zett on 2009-03-31
Nabble ?
Cant find Nabble and its not on repositories...
I tried remove wine and reinstall it....not working,
I need to protect my WoW.exe x( -> i dont know how it works if the virus can infected wow.exe from the internet or the virus was on media....hmmm...i installed it on ext3. X(

---

### Post by bodhi.zazen on 2009-03-31
not wine ~/.wine, your wine installation.

removing and re-installing wine will not help as the virus is in your ~/.wine

---

