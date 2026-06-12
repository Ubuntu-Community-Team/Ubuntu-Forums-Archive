---
title: "Choosing monitor to open a application."
date: 2014-08-19
forum: Ubuntu Application Development
---

### Post by tonysonney on 2014-08-19
I am sure there has been lot of forums with similar question. I even tried posting in a X11 forum.  But I couldn't find a direct answer for what I am trying to do. I noticed, in Ubuntu any application with graphical interface once started, is displayed in the monitor where mouse pointer resides. Can somebody please tell me how does Ubuntu does that? How does ubuntu make the application start in particular monitor?
I am after a command line command/script which once run, all subsequent application with graphical interface opens in configured monitor, out of the 2 monitors, I have. I cannot use the "DISPLAY" environment variable, as both my monitors are displayed under single Screen 0.
Thank you in advance for any suggestions. 
Following is my xrand output
```
xrandr
Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 32767 x 32767
LVDS1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080      60.0*+   59.9  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x800       59.8  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  

```

---

### Post by tonysonney on 2014-08-19
Sorry, I should have mentioned in the previous post. I am using ubuntu 12.04 with gnome-classic.

---

### Post by tgalati4 on 2014-08-19
> tgalati4@Mint14-Extensa ~ $ env | grep DISPLAY
DISPLAY=:0.0


[http://askubuntu.com/questions/432255/what-is-display-environment-variable](http://askubuntu.com/questions/432255/what-is-display-environment-variable)

To perform something fancy (other than default) actions with the xorg (X11) graphical windows server, you need to get familiar with the X11 resources database manager.

```
man xrdb
man X
man xorg
```

> tgalati4@Mint14-Extensa ~ $ xclock -display :0.0
tgalati4@Mint14-Extensa ~ $ xclock -display :0.1
Error: Can't open display: :0.1


I'm on a laptop with only one screen, so I get an error trying to open up *xclock* on a second screen.

---

### Post by tonysonney on 2014-08-19
Thank you for the pointer tgalati4. Unfortunately eventhough, I have two monitors, DISPLAY environment variable does not differentiate the monitors. It does not differentiate between which monitor is being used. Some output from my experiment.

_Mouse pointer in Monitor 1 _
- Start teminal from keyboard (Ctrl+Alt+T)
(Terminal is started in monitor 1)
```
tony@tony-N56VJ:~$  echo $DISPLAY
:0.0
```

_Mouse pointer in Monitor 2 _
(Terminal is started in monitor 2)
- Start teminal from keyboard (Ctrl+Alt+T)
```
tony@tony-N56VJ:~$  echo $DISPLAY
:0.0
```

_Out put of xclock from both terminals_
tony@tony-N56VJ:~$ xclock -display :0.0
tony@tony-N56VJ:~$ xclock -display :0.1
Error: Can't open display: :0.1

---

