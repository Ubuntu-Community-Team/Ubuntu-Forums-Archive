---
title: "Change button color"
date: 2007-05-09
forum: Ubuntu Christian Edition
---

### Post by shane2peru on 2007-05-09
Ok, just thought I would share this.  I love the artwork and the little things that make Christian Ubuntu what it is.  I'm just not for the burnt orange and brown color schemes.  So, I figured out how to change the colors of the button.  I copied it to another location and played around in Gimp till I figured out how to automatically change the colors of the button.  I have a green button and a blue button attached.  Here is how you can change them.  Save the either button or both buttons to your home folder.  Open the terminal **Accessories -> Terminal**  then type/paste ```
cd /usr/share/icons 
``` Next: ```
sudo cp /home/**username**/ubuntu-ce-green-menu-button.png /usr/share/icons/  
``` Thanks [Timzak]("http://ubuntuforums.org/member.php?u=280828") for pointing out the missing 's' on icons.
**NOTE:** You must put the user name in where you see user name.  
 Ok that just copied the icon into the correct directory.  Now we are going to switch them: ```
sudo cp ubuntu-ce-orange-menu-button.png ubuntu-cd-orange-menu-button.png.backup
```  This backs up your orange button so you don't loose it.  Now: ```
sudo cp ubuntu-ce-green-menu-button.png ubuntu-ce-orange-menu-button.png
```  Now log out and back in and your button will be the green one.  Basically what we did was just called the green one by the orange name because that is what it looks for and loads.  We saved the orange one as a backup so you won't loose it.  If you need any help just ask, and I will be glad to help.  Oh if you want the blue one, then just put blue in everywhere you see the word green.  Enjoy.

**To switch back to the orange:**

```
cd /usr/share/icons/ 
```

```
sudo cp ubuntu-ce-orange-menu-button.png.backup ubuntu-ce-orange-menu-button.png
```  
Log out and back in and you are back to the orange button.  :)  Enjoy.

Shane

---

### Post by timzak on 2007-05-12
I got to:

```
sudo cp /home/tim/ubuntu-ce-green-menu-button.png /usr/share/icon/
```

and got the following message:

```
cp: target `/usr/share/icon/' is not a directory: No such file or directory
```

and figured out your 2nd section of code is missing the letter "s" on "icon".

Then when I corrected that, I got the following error:

```
sudo cp /home/tim/ubuntu-ce-green-menu-button.png /usr/share/icons/
cp: cannot stat `/home/tim/ubuntu-ce-green-menu-button.png': No such file or directory
```

Can't figure out how to proceed.  Any help?

On a related question, how would one completely change the "start button" icon?  

Thanks.

---

### Post by shane2peru on 2007-05-12
> **timzak said:**
> I got to:

```
sudo cp /home/tim/ubuntu-ce-green-menu-button.png /usr/share/icon/
```

and got the following message:

```
cp: target `/usr/share/icon/' is not a directory: No such file or directory
```

and figured out your 2nd section of code is missing the letter "s" on "icon".

Then when I corrected that, I got the following error:

```
sudo cp /home/tim/ubuntu-ce-green-menu-button.png /usr/share/icons/
cp: cannot stat `/home/tim/ubuntu-ce-green-menu-button.png': No such file or directory
```

Can't figure out how to proceed.  Any help?

On a related question, how would one completely change the "start button" icon?  

Thanks.
Tim,  Thanks for pointing out the error on the code.  I fixed that.  Sorry about that.

You need to save the green menu button to that folder (you home folder).  Just right click on the button and **save image as** then select your username as where to save it.  If you are trying to use the blue one then, you will need to replace the word green to blue.  It can't seem to find the file that you are trying to copy.  Open nautilus and make sure of the location of where the file was saved too.

Shane

---

### Post by timzak on 2007-05-14
Thanks, I forgot the all-important part of saving the attached buttons to my computer.  :oops: 

How would one go about changing the button back to the original Ubuntu Feisty button (non-Christian Edition)?

No disrespect to the CE designer, I'm just not happy with the button (I love the rest of CE).

Thanks.

---

### Post by shane2peru on 2007-05-14
> **timzak said:**
> Thanks, I forgot the all-important part of saving the attached buttons to my computer.  :oops: 

How would one go about changing the button back to the original Ubuntu Feisty button (non-Christian Edition)?

No disrespect to the CE designer, I'm just not happy with the button (I love the rest of CE).

Thanks.

Yeah, saving the file does help!  :popcorn: Don't worry, it happens to all of us now and then.

I'm not sure how to change it to the original.  What I can tell you is if you find any .png picture, or anything that is a picture that you can convert/save as a png file with Gimp, you can use that as the menu button.  Just **save the file to your computer**  :popcorn:  Sorry, couldn't resist that one.  :) then run it through the renaming process that is described above.  However if the picture is not the right dimensions, then it may not look right or be the right size.  If I can be of any help just let me know.  Jereme would be the person to help you get it back to the original, and I would be interested in hearing that too, just for the learning part.  It seems to have changed from the way it use to be in Dapper and Edgy.  

Shane

---

### Post by framinglory on 2007-05-15
i think, at least for me. you can still add the original by clicking on add to panel>main menu. this worked last time i tried it..but now that i try it the icon won't appear, but it might just be because of my settings.

EDIT: seems to be that it won't appear when beryl is my window manager, but if i change back to metacity (gnome) it appears and is the regular old ubuntu icon

---

