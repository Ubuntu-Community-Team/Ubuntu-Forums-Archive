---
title: "Help for C-L application-- Type, print, repeat (Just read)"
date: 2005-08-20
forum: The Cafe
---

### Post by erikpiper on 2005-08-20
Hi! I have a application request. My mom asked me to et something ready for tomorrow, (!!  ](*,)  ) for some people we have coming over. 

Basicaly what I need, (Command line is fine) is a way for someone to come to the computer, start typing on the keyboard, press a key combo (Ex- Ctrl/R or anything) and have what they just typed print out, and the input screen clear for the next person. I would want it to need a key combo that I know to exit. 

Another way to describe what I need. A blank screen, that you can type on (Think blank console waiting for a command) Nano like. (But only type.) They press a key combo when done, told to them prior to using the computer. When they press it, the text is printed through a USB printer, and the screen is reset to do it again. 


Any way I can get this running in tonight/tommorow morning? Any recources too teach a complete newbie to programming how to do this would be GREATLY appriciated!!

Thanks!!!!!!

---

### Post by aysiu on 2005-08-20
Maybe I'm not understanding this correctly, but couldn't you just use OpenOffice Text, have them type in whatever they want and press this key combo?

Control-P Enter Control A Backspace

---

### Post by erikpiper on 2005-08-20
[QUOTE=aysiu]Maybe I'm not understanding this correctly, but couldn't you just use OpenOffice Text, have them type in whatever they want and press this key combo?

Control-P Enter Control A Backspace[/QUOTE]
 But then it is running X, running Gnome, with my games, and everything else. I want it to be as simple as possible. We don't want people using the computer. Just typing something. Doing the exact thing in C/L is best. No temptation to look at the rest of the system! If I cannot get that working,I will use OO.ORG. (Thanks about the Ctrl A Backspace tip!)

It would be best if I could do the equivelent of (Control-P Enter Control A Backspace) with Ctrl-R or Ctrl-Alt-Q Or something. (One step)

Thanks.

---

### Post by aysiu on 2005-08-20
[QUOTE=erikpiper]But then it is running X, running Gnome, with my games, and everything else. I want it to be as simple as possible. We don't want people using the computer. Just typing something. Doing the exact thing in C/L is best. No temptation to look at the rest of the system! If I cannot get that working,I will use OO.ORG. (Thanks about the Ctrl A Backspace tip!)

It would be best if I could do the equivelent of (Control-P Enter Control A Backspace) with Ctrl-R or Ctrl-Alt-Q Or something. (One step)

Thanks.[/QUOTE] Maybe you can create a new user account called *temp*. Then, get rid of everything in that user's menu and panel, blank out the wallpaper. Just have OpenOffice running as a maximized window. You can always deny read/write/execute permission to this user for every other folder but the one with OpenOffice in it.

---

### Post by erikpiper on 2005-08-20
[QUOTE=aysiu]Maybe you can create a new user account called *temp*. Then, get rid of everything in that user's menu and panel, blank out the wallpaper. Just have OpenOffice running as a maximized window. You can always deny read/write/execute permission to this user for every other folder but the one with OpenOffice in it.[/QUOTE]
 That could work, but C/L Would be so much more elegant. I wish I knew how to code.... (I am working on fixing that)

How does one deny read/write/execute permission?

---

### Post by aysiu on 2005-08-20
You chmod the folder (type *man chmod* to find out more).

---

### Post by erikpiper on 2005-08-20
Is it possible to print from within a nano like C/L text edeitor? (Without saving) There has to be a way...

---

### Post by aysiu on 2005-08-20
[QUOTE=erikpiper]Is it possible to print from within a nano like C/L text edeitor? (Without saving) There has to be a way...[/QUOTE] Not that I can see on the Nano page...

[http://www.nano-editor.org/docs.html](http://www.nano-editor.org/docs.html)

---

### Post by erikpiper on 2005-08-20
I know it doesn't work in nano. At the moment I am searching google like mad to find an editor that does. 

If I cant do this I will have to do what you suggested. 

Thanks for your help!

---

### Post by AnythingBut on 2005-08-21
You can give this little shell script a shot.  Pop this code in a text file and give it executable permissions.

```
#!/bin/sh

#Forever loop
while true
do

clear

echo "Type Away! (Finish with a "." on its own line)"

#Clear temp file
rm temp.txt

#User input loop
line="";
while [ "$line" != "." ] 
do
  echo "$line" >> temp.txt
  read line
done

echo "Thanks.  Now Printing"

lpr temp.txt

sleep 2

done
```

The user can stop by typing a period alone on a line.
It requires that the printer is your default printer.... but you can mess with the lpr command to get around that.

You still might want to create a new user since they can exit the script by hitting Cntrl+C and could then roam around.

Is this what you had in mind?

p.s.:  It's licenced under the GPL  ;-)

---

### Post by erikpiper on 2005-08-21
> **AnythingBut]You can give this little shell script a shot.  Pop this code in a text file and give it executable permissions.

```
#!/bin/sh

#Forever loop
while true
do

clear

echo "Type Away! (Finish with a "." on its own line)"

#Clear temp file
rm temp.txt

#User input loop
line="" said:**
>  
do
  echo "$line" >> temp.txt
  read line
done

echo "Thanks.  Now Printing"

lpr temp.txt

sleep 2

done
```

The user can stop by typing a period alone on a line.
It requires that the printer is your default printer.... but you can mess with the lpr command to get around that.

You still might want to create a new user since they can exit the script by hitting Cntrl+C and could then roam around.

Is this what you had in mind?

p.s.:  It's licenced under the GPL  ;-)
 It looks good by looking at the code! Can anyone point me to a recource on learning how to make use of my new text file?

Lol.

Thanks!  Erik,

---

### Post by AnythingBut on 2005-08-21
[QUOTE=erikpiper]It looks good by looking at the code! Can anyone point me to a recource on learning how to make use of my new text file?

Lol.

Thanks!  Erik,[/QUOTE]
 Just google "Bash Scripting".  Tonnes of resources out there.

---

### Post by AnythingBut on 2005-08-21
[QUOTE=erikpiper]Can anyone point me to a recource on learning how to make use of my new text file?[/QUOTE]

Oh whoops.  Do you mean how exactly to get it up an running?  There's no compiling needed.  Once you have the code in a file (the file must be plain text, not an Open Office Document or anything like that. gedit/nano works), for example "script.sh", in a terminal give it executable permission using "chmod a+x script.sh".  You should then be able to run it.  You have to run it a little differently than you do other things since it's not in any directory listed in the PATH environment variable.  Run it by issuing a command which includes its location like "./script.sh" if you are in the same directory as it.

---

### Post by Stormy Eyes on 2005-08-21
In a console, have the guests type "vim" to start the editor. They can then press "i" to start typing, "ESC" when they are done, ":hardcopy" when they want to print, and then ":q!" when they are done to get back to the prompt.

---

### Post by erikpiper on 2005-08-21
[QUOTE=AnythingBut]Oh whoops.  Do you mean how exactly to get it up an running?  There's no compiling needed.  Once you have the code in a file (the file must be plain text, not an Open Office Document or anything like that. gedit/nano works), for example "script.sh", in a terminal give it executable permission using "chmod a+x script.sh".  You should then be able to run it.  You have to run it a little differently than you do other things since it's not in any directory listed in the PATH environment variable.  Run it by issuing a command which includes its location like "./script.sh" if you are in the same directory as it.[/QUOTE]
 Thanks! I knew most of that. What I didn't know was how to give it executable priveliges. I am not very eloquent around midnight :) It worked great! Thank you so much for creating that for me!

---

### Post by lakcaj on 2005-08-21
Just for the hell of it, I made a pyglade (pygtk) GUI version of what you want... you can find it here:

[http://s38.yousendit.com/d.aspx?id=3N5US804ITYLU2HM9SRZHECT50](http://s38.yousendit.com/d.aspx?id=3N5US804ITYLU2HM9SRZHECT50)

You will need python, python-glade2, and python-gtk2.  I think that should be all you need.  It may be too late, but I wanted to learn to make a pygtk app anyway, and this was a good excuse.

Oh yeah, just extract it, chmod 755 the easy_print.py file, and then ./easy_print.py in the same directory as easy_print.py is in.

---

