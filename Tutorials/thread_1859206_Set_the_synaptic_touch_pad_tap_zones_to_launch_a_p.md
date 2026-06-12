---
title: "Set the synaptic touch pad tap zones to launch a program or type a key sequence"
date: 2011-10-13
forum: Tutorials
---

### Post by Enterpart on 2011-10-13
_Simple with GUI_. 

**First configure what mouse-button is activated at each corner**. For remembering easily we'll start at Top Left with 9 and move clockwise at each corner giving

Top Left Corner = mousebutton 9
Top Right Corner = mousebutton 10
Bottom Right Corner = mousebutton 11
Bottom Left Corner = mousebutton 12

(Ive used 9-12 since they are never normally used by anything)

this is done using code

```
synclient LTCornerButton=9 RTCornerButton=10 RBCornerButton=11 LBCornerButton=12
```

Now **install** the GUI program **Easystroke**

```
sudo apt-get install easystroke
```

now we have to tell easystroke what keystroke is associated with each mouse button pressed

**load easystroke and add the buttons to 9-12** as follows:

[B]go to preferences Tab
click on "Additional Buttons"
Click "Add"
then click the box with no writting inside (under Any Modifier button) and choose button 9
Then Press "OK" (you should see Button 9 added)
Do the same with Button 10 11 12.[/B]

(now we have to assign the mousebutton with a keystroke (or a command) for this im going to assign the tap zone at Top Left as Home Button)

**now go back to "Actions" Tab**

click Add action and your first gesture name it Home then click on "command" type choose key and then press "Home" key combination. Now double click on the box under stroke and tap at the top left corner (make sure you tap at the corner) the dialogue box will pop up

*"You are about to bind an action to a single click.  This might make it difficult to use Button 1 in the future.  Are you sure you want to continue?"*

**press yes **

you should see a red 9 with forward arrow and a blue x.
NOTE. if you only see a blue x then you have not touched right at the corners and you have to delete that. Do this stright away by pressing "return key" "forward arrow" "return key". This is because we accidently assigned the normal tap of the touchpad with home key and so you wont be able to use that tap.

go on to say your browser and tap at top Left and it should have activated home button.

Right so we have just used Tap Zone Top Left as Home and you can assign the other tap zones as any keystroke you want and more. Since you can enter commands in it that will do like terminal commands. ALL IN ALL YOU SHOULD HAVE 4 GESTURES now if you wanted to change the key stroke it will be easy since just you just need to change the key combination for the mouse button gesture. and remember we start with 9 top left and work clockwise.

you can learn more about easystroke here
[http://www.youtube.com/watch?v=sOWXAyOde18](http://www.youtube.com/watch?v=sOWXAyOde18)
easystroke can do this and much more have a look at tips and tricks here. 
[http://sourceforge.net/apps/trac/easystroke/wiki/TipsAndTricks](http://sourceforge.net/apps/trac/easystroke/wiki/TipsAndTricks)

P.S I don't know how to permanently change the corner mouse button preference so you have to use the first code each time you start from boot.maybe somebody else can fix that and lastly you would want to start easy stroke at boot. find that in Preferences tab and tick "autostart easystroke"

---

