---
title: "Configure 9-button mouse per-application for keystrokes or launching applications"
date: 2011-10-15
forum: Tutorials
---

### Post by Enterpart on 2011-10-15
your looking for Easystroke
 
```
sudo apt get install easystroke
```
 
located in Applications -> Universal Access
 
**Now configure Easystroke.**
 
In Easystroke go to Preferences Tab -> Method to show gestures ->
-> None 
 
and tick Autostart Easystroke
 
_**Next add all buttons up to 9**_
 
In Easystroke go to Preferences Tab -> Additional Buttons ->
-> Add -> click empty box -> Button 1 -> OK 
 
Repeat process to add the remainder 8 buttons.
 
**Now match the buttons to send custom keystrokes to each application**
 
In Easystroke go to Actions Tab -> Add Application
 
(*Easystroke should get minimised at this point*)
 
click on the application that your going to set the buttons to work on.
 
**now to record the keystrokes follow this**
 
click *Add Action* -> 
-> Choose a name (if your using Alt+Left use the name "Back") ->
-> click Command -> and choose Key (Under Type Column) -> 
-> then press Alt and Left buttons together
 
-> click Record Stroke and use the button on the mouse that you want to associate with this command - left tilt is it?
 
**It will prompt you if your sure. Click Yes**
 
**now repeat the process for the remaining buttons.**
 
Once your done with that Application.
 
**Repeat the whole process with adding another application.**
 
**Do not use mouse buttons 1 2 or 3 as the "Record Stroke since they are used already"**
 
 
**_*Easystroke is much more powerful than just recording keystrokes. You can use the buttons to enter commands like you would in terminal.*_**
 
**ANOTHER TIP**
 
***_add another 2 scroll wheels_***. yes you can do this like as follows 
 
For example say you wanted to control zoom level of page with scroll wheel do this
 
click *Add Action* -> 
-> for name choose "Zoom in" ->
-> click Command -> and choose Key (Under Type Column) -> 
-> then press CTRL and + buttons together
-> click Record Gesture -> now hold Left mouse button down and flick the scroll wheel up
 
you should see a red [COLOR=red]4[/COLOR], then 
 
click *Add Action* -> 
-> for name choose "Zoom out" ->
-> click Command -> and choose Key (Under Type Column) -> 
-> then press CTRL and - buttons together
-> click Record Gesture -> now hold Left mouse button down and flick the scroll wheel down
 
you should see a red [COLOR=red]5[/COLOR]
 
 
now hold down left mouse button and then use the scroll wheel up or down on the browser. It should zoom in and out.
 
**you can repeat to get another scroll wheel by holding down the right mouse button instead of the Left to control say Brightness, volume toggle application...**
 
**You cannot use it on the buttons that you have already assigned to perform an action since as soon as you press that button it will trigger that action!**
 
***_LAST TIP_***
 
you can **create 8 extra buttons** by click and hold to create another action for each of your buttons. by doing this..
 
In Easystroke click Advanced tab -> and tick "Timeout Gestures"
 
now go back to Actions Tab to create a another Action.
 
click *Add Action* -> 
-> for name choose "firefox" ->
-> click Command -> and choose Command (Under Type Column) -> 
-> then type "firefox" without the brackets
-> click Record Gesture -> now hold a mouse button (other than left mouse button AND HOLD IT FOR TWO SECONDS then let go.
 
click yes.
 
then when you hold down that button a firefox window should pop up? you dont have to use firefox it can be any command or keystrokes.
 
**you can Repeat the last tip to include other buttons if you wanted**
 
[COLOR=red]***_You asked to Configure 9-button mouse per-application_***[/COLOR]
_***[COLOR=red]I've given you 17 button mouse per application with another two scroll wheels.[/COLOR]***_
 
Peace

---

