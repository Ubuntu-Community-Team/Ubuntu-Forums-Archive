---
title: "Run Application - ubuntu flashback 18.04 - change size of window application - panel"
date: 2018-06-09
forum: Ubuntu Application Development
---

### Post by Claus7 on 2018-06-09
Hello,

the other time I wanted to find a dash alternative and while experimenting with ubuntu mate I came across brisk menu. This was more or less what I was looking for. The thing is that this menu is not working with ubuntu flashback panel so either one has to find an alternative application (like synapse) or install mate-panel, delete the default panels for gnome and work from there.

The Run Application for ubuntu flashback is pretty descent, yet I was facing a problem with it. The window that was launched was too small for my liking. The ccsm did not work, because every time I was grabbing the Run Application window, the result was that it was recognized as gnome-panel, so I could not resize the window in the end.   

As a result I created a script:
```
#!/bin/bash 
ra="xdotool key Alt+F2" 
$ra 
sleep 0.015
test=$(wmctrl -l | grep 'Run Application' | awk '{print $1}') 
wmctrl -i -r $test -e 0,400,100,500,500
```

which was named: run_application.sh

I saved it under ~/run_application.sh

I created a custom application launcher in gnome-panel:
> Name: Run Application
Command: /home/claus/run_application.sh %U

with the %U option is more smooth.

What it does is the following:
[table="width: 700, class: grid"]
[tr]
	[td]ra="xdotool key Alt+F2" 
[/td]
	[td]keyboard shortcut Alt+F2 is assigned to command ra (alias that to .bashrc won't work, in other words if there is an alias of that command to .bashrc, just writing in the script ra, won't work, since the script is not an active window)[/td]
[/tr]
[tr]
	[td]$ra[/td]
	[td]issue the command[/td]
[/tr]
[tr]
	[td]sleep 0.015[/td]
	[td]suspend for a little while, until the following commands are run (if not written, the command is not working all the time)[/td]
[/tr]
[tr]
	[td]test=$(wmctrl -l | grep 'Run Application' | awk '{print $1}') [/td]
	[td]take the first argument (which is the ID of the window of Run Application) of the output of the command: wmctrl -l | grep 'Run Application', and assign it to test variable. 
[/td]
[/tr]
[tr]
	[td]wmctrl -i -r $test -e 0,400,100,500,500[/td]
	[td]resize the Run Application window where: wmctrl -i -r ID -e 0,left,up,width,hight. 

              A move and resize argument has the format 'g,x,y,w,h'. All five components are integers. 
              
              The first value, g, is the gravity with 0 being the default value.  
              For geometry specification:
              x,y  is  the  position of the top left corner of the window, and
              w,h is the width and height of the window.[/td]
[/tr]
[/table]
 
Other alternatives can be:
[LIST]
[*]Albert
[*]Gnome do
[*]Kupfer
[*]Synapse
[*]gmrun
[/LIST]
Regards!

---

### Post by Claus7 on 2018-06-09
Hello,

an updated version with minor tweaks:
> #!/bin/bash 
ra="xdotool key Alt+F2" 
$ra
sleep 0.02 
test=$(wmctrl -l | awk '/Run Application/ {print $1}') 
wmctrl -i -r $test -e 0,400,100,500,500 

Regards!

---

### Post by Claus7 on 2018-09-09
Hello,

the options listed above, are working, yet they are not so immediate all the time. Searching a little bit more I did the following:
I went to CompizConfig Settings Manager and from there chose and enabled the Window Rules.

Then, under Size Rules, I did Grab and the result was:
class=Gnome-panel & name=gnome-panel & type=Dialog

all these are necessary since, if not, the panel, or other dialog boxes will be affected as well. That way, only the Run Application (Alt+F2) box is affected. The result is fast and efficient!

Efforts from gsettings were to no avail because even though:
gsettings set org.gnome.gedit.state.window size "(770, 860)"
changes the size of gedit window

something like this:
gsettings set org.gnome.panel-run-dialog.state.window size "(770, 860)", or
gsettings set org.gnome.run-dialog.state.window size "(770, 860)", or
gsettings set org.gnome.desktop.wm.keybindings panel-run-dialog size "(770, 860)"
are not working because no such schemata exist.

Regards!

---

