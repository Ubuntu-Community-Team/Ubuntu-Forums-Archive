---
title: "HOWTO use Adobe Photoshop 8BF filters with wine"
date: 2006-04-13
forum: Tutorials
---

### Post by Stefan_hb on 2006-04-13
(Please excuse my insufficient english, I´m not a native speaker.)

I love the Gimp and I don´t miss any Windows application at all, but some of the Adobe Photoshop 8BF-Filters are really cool, so why don´t use them with "wine"?:

Required:
-wine
-Microsoft Windows

1. Get an older version of the Windows freeware application "Irfan View" here:
[http://rapidshare.de/files/17880626/irfvw397plg.zip.html](http://rapidshare.de/files/17880626/irfvw397plg.zip.html)
This contains also the plugins for Irfan View, required to use 8BF-Filters with it. Irfan View needs the "mfc42.dll", most people will already have this in their windows directory, if not, it is also included in the download above.
2. Start Windows and install Irfan View and also the plugins.
3. Copy all the 8BF-Filters you want to use to "c:/Program Files/IrfanView/Plugins/Adobe 8BF
If you haven´t got any yet, try the freeware filters from here: [http://www.cybia.co.uk/colourworks.htm](http://www.cybia.co.uk/colourworks.htm), they´re cool.
4. Run Irfan View and install all the Photoshop Plugings you want, go to "image/effects/Adobe 8BF filters" and add your plugins. If this doesn´t work properly (happened to me once), try to add the filters in "image/effects/filter factory", it also supports 8BF-filters.
5. Exit Windows, reboot Linux. If you don´t already have wine, install it with "sudo apt-get install wine"
6. Copy the directory "c:/Program Files/IrfanView/" to "~/.wine/drive_c/Program Files". Important: if your program-path was named different in your version of Windows (because you maybe have a different language and it´s named e.g. "Programme, programmi", or whatever, use the same path/folder name with wine.
7. Start Irfan View with ```
wine /home/username/.wine/drive_c/Programme/IrfanView/i_view32.exe
```
8. Use 8BF-Filters in Linux from now on and be happy. Screenshot: [http://www.go77.de/linux/goo.jpg](http://www.go77.de/linux/goo.jpg)

Note: For 99% of all filters this will work without a problem, but if you use very complex filter-packages, like "Kai´s Power Goo", you may have to stop the "wine-preloader" task manually after having quit Irfan View, it keeps running and uses alot of memory otherwise. But that´s a small price for being able to use the filters in my opinion.

---

### Post by stalefries on 2006-04-14
All this hassle is paled in comparison with the Gimp plug-in that is [PSPI]("http://www.gimp.org/%7Etml/gimp/win32/pspi.html"). It allows the running of Photoshop .8bf plug-ins (which are really just .dll's renamed) in the Gimp as filters! It's really easy to setup (drop the plugin in your Gimp plugins folder, and then point it to a folder for your PS filters), and works seemlessly with Gimp. It does, of course, require Wine to be installed.

---

### Post by Stefan_hb on 2006-04-15
[QUOTE=stalefries]All this hassle is paled in comparison with the Gimp plug-in[/QUOTE]
 Hm, this sounds really good, but this plugin doesn´t work for me, it doesn´t show up in the "xtns" menu.

---

### Post by Kethinov on 2006-04-15
I got PSPI working well. But while PSPI is quite awesome, but it doesn't work with every Photoshop plugin yet, such as some of the KPT5 stuff.

Stefan, your IrfanView idea is a good idea. Got KPT5 working perfectly for me! Still a huge hassle to try to do artwork with IrfanView though. :-\

In any case, I just googled for a mfc42.dll, tossed it into the Wine system folder, installed the latest IrfanView, googled for the 8bf IrfanView plugin, and everything worked.

---

### Post by Kashirigi on 2006-04-25
[QUOTE=Stefan_hb]Hm, this sounds really good, but this plugin doesn´t work for me, it doesn´t show up in the "xtns" menu.[/QUOTE]

I'm having the same problem. But then, I can't seem to get wine working at all either.

---

### Post by Kashirigi on 2006-04-26
Now that I've got WINE working thanks to this thread: [http://www.ubuntuforums.org/showthread.php?t=166036&highlight=pspi](http://www.ubuntuforums.org/showthread.php?t=166036&highlight=pspi) I *still* can't get pspi to work.

Now, at least I can get the XTNS:Photoshop Plug-ins to show up, but when I select it, I get this:

.gimp-2.2/plug-ins/pspi.exe.so: fatal error: Segmentation fault

I suspect that it may be related to my installation of WINE, but I can't be sure.

Is the problem unique to me? I seem to have a disproportionately long list of abnormalities on my machine  ](*,)

---

### Post by afrodeity on 2012-05-26
pspi.exe.so segfault error 14

---

