---
title: "No Idea how to use WINE on the Ubuntu 9.04."
date: 2009-06-17
forum: Wine
---

### Post by carbonfibre on 2009-06-17
need help with WINE i have never used wine before and never used ubuntu.. currently need help on how to install wine i already downloaded it but i dunno how to install.. 

someone please provide a detailed step by step procedure.. 

and would love to have an explanation on how WINE works? thanks :D

---

### Post by Triptol on 2009-06-17
Use your package manager to install it, or type something like this:
[HTML]sudo aptitude install wine[/HTML]
After that you will find a wine menu. Now you can install (some) windows software by typing:
[HTML]wine /path/to/your/windows/exe-file[/HTML]

p.s. don't drink too much.

---

### Post by Sealbhach on 2009-06-17
If you find Wine a bit too much you could install PlayonLinux, which is really just a front end for Wine. 

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

.

---

### Post by carbonfibre on 2009-06-17
what u mean front end to wine :)

---

### Post by Meow27 on 2009-06-17
its a programs that lets you use different versinos of wine without having to replace anything

---

### Post by jhoeijao on 2009-06-17
> **carbonfibre said:**
> what u mean front end to wine :)

[http://en.wikipedia.org/wiki/Back-end](http://en.wikipedia.org/wiki/Back-end)

**Front-end** and **back-end** are generalized terms that refer to the initial and the end stages of a process. The front-end is responsible for collecting input in various forms from the user and processing it to conform to a specification the back-end can use. The front-end is a kind of [interface]("http://en.wikipedia.org/wiki/Interface_%28computer_science%29") between the user and the back-end.
     [B]
[/B]

---

### Post by kttyshadow5 on 2009-06-17
^If the whole
```
wine /path/to/file.exe
```Doesn't thrill you, I believe you can, slightly less reliably, just right click on your EXE file, and click "Run with Wine Windows Compatibility... blah" or something like that. Its the first choice, I think. But the terminal command works a little bit better, if you know the path, so you don't have to go fishing through your hard drive to find the file.

---

### Post by FourthCoffee on 2009-06-17
Thanks, this should help.

---

### Post by bugritall on 2009-08-01
I have several small exe files that I would like to run via Wine's "Start Menu" but I have no idea how to instal a Windoze executable that doesn't have an installer. My guess is that I need to create a link in Wine's "Programs" menu but how?

Edit:
I have found an answer, of sorts. By right-clicking one of the files and selecting "Wine Windows Program Loader" in Properties->Open With->Add, all my Windoze executables now start up under Wine. 

Edit:
I have cracked it. It's just a matter of using System->Preferences->Main Menu to create a bunch of menu items having a command line like this:
env WINEPREFIX="/home/*user*/.wine" wine *path-to-exe*

I worked it out by looking at the menu entry for a program that Wine installed and I have no idea whether this is the "proper" way to do things but it works!

---

### Post by Dullstar on 2009-08-02
Okay, simple way for everyone, basically a summary of the suggestions given:

Install WINE.  Use **Synaptic Package Manager** or the **terminal commnand** "sudo apt-get install wine" (without the quotes).

Either use the **terminal command** "wine /this/is/the/path/to/windows/program.exe" or **navigate to the file, right click on it, and find the Run in WINE option.**

---

### Post by myersd on 2009-08-03
I have my email program npopuk on a flash drive. When I double click on npopuk.exe, wine will run it and put an envelope icon on the task bar. Clicking on the icon opens up the npopuk window. When I installed wine, I had no idea it worked this way.

---

