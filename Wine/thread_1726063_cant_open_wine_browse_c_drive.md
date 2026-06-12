---
title: "cant open wine browse: c drive"
date: 2011-04-10
forum: Wine
---

### Post by gtex1991 on 2011-04-10
each time i want to open Wine, it wont let me instead Rhythm-box player opens each time, i cant even open up folder through clicking places

---

### Post by Karlchen on 2011-04-10
Hello, gtex1991.

> each time i want to open Wine, it wont let me instead Rhythm-box player  opens each timeSo you go to "Applications" => "Wine" => "Browse C:".
This should open the file manager Nautilus and directly take you to the .wine pseudo folder C:. Instead this launches Rhythm Box?!
This suggests that the menu item "Browse C:" has been misconfigured to launch the wrong command.
In order to check and correct this, go to "System" => "Settings" => "Main Menu" => "Wine" => "Browse C:" .
Click on the button "Properties". What does the field "Commandline" state?
It should read ```
xdg-open .wine/dosdevices/c:
``` or even better ```
xdg-open ~/.wine/dosdevices/c:
```> i cant even open up folder through clicking places[COLOR=Black]You wish to go to your personal Wine folder by using "Places" and navigating down to it?
OK, if this is the idea, this should be feasible.
Click on "Places". Click on "Personal Folder". In fact this will launch the file manager Nautilus and take you to your own home folder.
Inside Nautilus click on "View" and activate **[x] Display Hidden Files**.
Look for a folder named ".wine". Double click it.
Click on "dosdevices".
Click on "c:"
[/COLOR] [COLOR=Black]There you are.
[/COLOR] 
HTH,
Karl

---

