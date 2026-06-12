---
title: "NOOB in Need - help creating script"
date: 2009-05-25
forum: Wine
---

### Post by mal1958 on 2009-05-25
I have Xubutu 9.04 and wine (latest).  I have installed Caesar 3, Pharoah, and a writing program called Write it now.  All were installed through Wine.  none created a desktop icon, nor a workable start link in the Applications bar.  I need to know how to write a script to launch them with wine from an Icon on the desktop.  I am getting tired of going to the App bar, then Other, then browse c drive, then right click on the exe and open with wine program loader.  Can anybody help me.  I need to know:


[LIST]
[*]how to place an Icon on the desktop
[*]How to link it to the wine program loader
[*]how to pass the command line to have wine open the file
[*]and how to do this simply.
[/LIST]
   I am a NOOB, I am learning, but I need some hand holding here.  Can anybody help me?

Mike

---

### Post by asdfoo on 2009-05-25
> **mal1958 said:**
> I have Xubutu 9.04 and wine (latest).  I have installed Caesar 3, Pharoah, and a writing program called Write it now.  All were installed through Wine.  none created a desktop icon, nor a workable start link in the Applications bar.  I need to know how to write a script to launch them with wine from an Icon on the desktop.  I am getting tired of going to the App bar, then Other, then browse c drive, then right click on the exe and open with wine program loader.  Can anybody help me.  I need to know:


[LIST]
[*]how to place an Icon on the desktop
[*]How to link it to the wine program loader
[*]how to pass the command line to have wine open the file
[*]and how to do this simply.
[/LIST]
   I am a NOOB, I am learning, but I need some hand holding here.  Can anybody help me?

Mike

Which desktop environment are you using?  I think there is a bug in xfce which prevents Wine's desktop launcher stuff from working properly.

I don't know the details, personally, I just create shell scripts in my home dir for each program I want to run.

eg, cat > steam
cd ~/.wine/drive_c/Program\ Files\Steam
wine Steam
^D (control-d)
chmod +x steam


Then every time I want to run steam, I open a terminal and type ./steam

---

### Post by mal1958 on 2009-05-25
> **asdfoo said:**
> Which desktop environment are you using?  I think there is a bug in xfce which prevents Wine's desktop launcher stuff from working properly.

I don't know the details, personally, I just create shell scripts in my home dir for each program I want to run.

eg, cat > steam
cd ~/.wine/drive_c/Program\ Files\Steam
wine Steam
^D (control-d)
chmod +x steam


Then every time I want to run steam, I open a terminal and type ./steam


Is there a way to link this to an icon on the desktop?  and to pick the icon?

Mike

---

