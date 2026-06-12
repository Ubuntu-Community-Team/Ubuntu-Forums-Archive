---
title: "Fast Window manager: JWM users, let's talk"
date: 2009-10-18
forum: The Cafe
---

### Post by frenchn00b on 2009-10-18
Hi guys, 

Here I open the thread about JWM, discussion about this window manager.

:) let's talk :) :popcorn:




[COLOR="Red"][B]Here is my fluxbox feelings for JWM, ! ;)[/COLOR]
it has screenshots, and one can use it as fluxbox, and it is much much much faster and lighter ! Enjoy !! 
PRINTSCREEN is also available 
try alt+ctrl+right arrow ... [/B]

(one need xdotool, its in the repositories)

put this .jwmrc into you HOME user directory: 
  

> <?xml version="1.0"?>


<JWM>

<StartupCommand>
Esetroot -m $HOME/.wallpaper
tilda  &
xscreensaver -no-splash & 


# do not forget ampersand here after
</StartupCommand>


   <!-- The root menu, if this is undefined you will not get a menu. -->
   <!-- Additional RootMenu attributes: onroot, labeled, label -->
   <RootMenu height="15" onroot="123">
      <Program icon="rxvt.png" label="Terminal">x-terminal-emulator</Program>
      <Program icon="firefox.png" label="konsole">konsole</Program>
      <Program icon="firefox.png" label="Www Browser">firefox</Program>

<!-- #DEBIAN
      <Menu icon="folder.png" label="Applications">
         <Program icon="audacious.png" label="Audacious">audacious</Program>
         <Program icon="dia.png" label="Dia">dia</Program>
         <Program icon="firefox.png" label="Firefox">firefox</Program>
         <Program icon="pidgin.png" label="Pidgin">pidgin</Program>
         <Program icon="gimp.png" label="Gimp">gimp</Program>
         <Program icon="gtk-gnutella.png" label="gtk-gnutella">
            gtk-gnutella
         </Program>
         <Program icon="gxine.png" label="gxine">gxine</Program>
         <Program icon="ooffice.png" label="Open Office">ooffice</Program>
      </Menu>

      <Menu icon="folder.png" label="Utilities">
         <Program icon="xcalc.png">xcalc</Program>
         <Program icon="xfontsel.png">xfontsel</Program>
         <Program icon="xmag.png">xmag</Program>
         <Program icon="xprop.png" label="xprop">
            xprop | xmessage -file -
         </Program>
</Menu>

  
    
-->
      <Separator/>
      <Restart label="Restart" icon="restart.png"/>
      <Exit label="Exit" confirm="true" icon="exit.png"/>
   </RootMenu>

#   <Group>
#      <Class>Pidgin</Class>
#      <Option>sticky</Option>
#   </Group>

   <Group>
      <Name>gkrellm2</Name>
      <Option>nolist</Option>
   </Group>

   <Group>
      <Name>rxvt</Name>
      <Option>vmax</Option>
   </Group>

   <!-- Additional tray attributes: autohide, width, border, layer, layout -->
   <Tray  x="0" y="+1" height="28">

      <!-- Additional TrayButton attribute: label -->
      <TrayButton label="JWM">root:1</TrayButton>

      <TrayButton label="_">showdesktop</TrayButton>

      <!-- Additional Pager attributes; width, height -->
      <Pager/>

      <!-- Additional TaskList attribute: maxwidth -->
      <TaskList/>

      <Dock/>

      <!-- Additional Swallow attribute: height -->
      <Swallow name="xload" width="64">
         xload -nolabel -bg black -fg red -hl white
      </Swallow>

      <Clock format="%H:%M">xterm  </Clock>

   </Tray>

   <!-- Visual Styles -->

   <WindowStyle>

      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Width>4</Width>
      <Height>20</Height>

      <Active>
         <Text>white</Text>
<!-- #DEBIAN
         <Title>#70849d:#2e3a67</Title>
         <Corner>white</Corner>
-->
         <Title>gray30:gray60</Title>
         <Corner>gray20:white</Corner>
         <Outline>black</Outline>
      </Active>

      <Inactive>
         <Text>#aaaaaa</Text>
         <Title>#808488:#303438</Title>
         <Corner>#aaaaaa</Corner>
         <Outline>black</Outline>
      </Inactive>

   </WindowStyle>

   <TaskListStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <ActiveForeground>black</ActiveForeground>
      <ActiveBackground>gray90:gray70</ActiveBackground>
      <Foreground>black</Foreground>
      <Background>gray70:gray90</Background>
   </TaskListStyle>

   <!-- Additional TrayStyle attribute: insert -->
   <TrayStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Background>gray90</Background>
      <Foreground>black</Foreground>
   </TrayStyle>

   <PagerStyle>
      <Outline>black</Outline>
      <Foreground>gray90</Foreground>
      <Background>#808488</Background>
      <ActiveForeground>#70849d</ActiveForeground>
      <ActiveBackground>#2e3a67</ActiveBackground>
   </PagerStyle>

   <MenuStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Foreground>black</Foreground>
      <Background>gray90</Background>
      <ActiveForeground>white</ActiveForeground>
      <ActiveBackground>#70849d:#2e3a67</ActiveBackground>
   </MenuStyle>

   <PopupStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Outline>black</Outline>
      <Foreground>black</Foreground>
      <Background>yellow</Background>
   </PopupStyle>

   <IconPath>
      $HOME/.icons
   </IconPath>

   <!-- Virtual Desktops -->
   <!-- Desktop tags can be contained within Desktops for desktop names. -->
   <Desktops count="4">

      <!-- Default background. Note that a Background tag can be
           contained within a Desktop tag to give a specific background
           for that desktop.
       -->
 
<Background type="image">$HOME/wallpapers/wallpaper.jpg</Background>
</Desktops>

   <!-- Double click speed (in milliseconds) -->
   <DoubleClickSpeed>400</DoubleClickSpeed>

   <!-- Double click delta (in pixels) -->
   <DoubleClickDelta>2</DoubleClickDelta>

   <!-- The focus model (sloppy or click) -->
   <FocusModel>click</FocusModel>

   <!-- The snap mode (none, screen, or border) -->
   <SnapMode distance="10">border</SnapMode>

   <!-- The move mode (outline or opaque) -->
   <MoveMode>opaque</MoveMode>

   <!-- The resize mode (outline or opaque) -->
   <ResizeMode>opaque</ResizeMode>

   <!-- Key bindings -->
   <Key key="Up">up</Key>
   <Key key="Down">down</Key>
   <Key key="Return">select</Key>
   <Key key="Escape">escape</Key>

<Key mask="A" key="Tab">nextstacked</Key>
# <Key mask="A" key="F10">close</Key>

<Key mask="PH" key="#">desktop#</Key>
<Key mask="A" key="M">showdesktop</Key>
<Key mask="A" key="L">exec: xscreensaver-command -lock</Key>
<Key mask="A" key="space">maximize</Key>
<Key mask="A" key="Return">maximize</Key>
<Key mask="A" key="R">exec: gmrun</Key>
<Key mask="A" key="T">exec: rox</Key>
<Key mask="SA" key="T">exec: rox /tmp </Key>
 
# like under fluxbox
 <Key mask="A" key="F1">exec: xdotool set_desktop 0</Key>
 <Key mask="A" key="F2">exec: xdotool set_desktop 1</Key>
 <Key mask="A" key="F3">exec: xdotool set_desktop 2</Key>
 <Key mask="A" key="F4">exec: xdotool set_desktop 3</Key>
 <Key mask="A" key="F5"> close </Key>


# send to right or left the activewindow and follow
# <Key mask="PH" key="s">exec: i=$(xdotool get_desktop) ; z=$(($i - 1)) ; i=$z ; xdotool set_desktop_for_window  $(xdotool getactivewindow) $i  ;  xdotool set_desktop $i ; xdotool click 1 </Key>
# <Key mask="PH" key="d">exec: i=$(xdotool get_desktop) ; z=$(($i + 1)) ; i=$z ; xdotool set_desktop_for_window  $(xdotool getactivewindow) $i ;   xdotool set_desktop $i ; xdotool click 1   </Key>  
<Key mask="CAS" key="Left">exec: i=$(xdotool get_desktop) ; z=$(($i - 1)) ; i=$z ; xdotool set_desktop_for_window  $(xdotool getactivewindow) $i  ;  xdotool set_desktop $i ; xdotool click 1 </Key>
<Key mask="CAS" key="Right">exec: i=$(xdotool get_desktop) ; z=$(($i + 1)) ; i=$z ; xdotool set_desktop_for_window  $(xdotool getactivewindow) $i ;   xdotool set_desktop $i ; xdotool click 1   </Key>  

# like under fluxbox
 <Key mask="CA" key="Left">exec: i=$(xdotool get_desktop) ; z=$(($i - 1)) ; i=$z ; xdotool set_desktop $i</Key>
 <Key mask="CA" key="Right">exec: i=$(xdotool get_desktop) ; z=$(($i + 1)) ; i=$z ; xdotool set_desktop $i</Key>


#make a screenshot
<Key key="Print">exec:  cd ; mkdir screenshots ;  i="`cat $HOME/.scrottkrc`" ; j="$i" ; let i="i+1" ; echo  "Enter the filename, incrementing=$j to $i  " ; cd screenshots ;  filenameoutput="$(date +%Y%m%d)shot_$i.jpg"  ; echo "writing to :  $filenameoutput"  ; scrot    "$filenameoutput" ; echo $i > $HOME/.scrottkrc  </Key>


# flag key as PH
# select pidgin on a specific workspace
<Key mask="PH" key="J">exec:  xdotool search --title  skype    |  while read i ; do     xdotool set_desktop_for_window $i 2 ; xdotool windowraise $i  ; xdotool windowfocus $i   ;  done ; xdotool key "alt+3" </Key>
<Key mask="PH" key="K">exec:  xdotool search --title  pidgin    |  while read i ; do     xdotool set_desktop_for_window $i 2 ; xdotool windowraise $i  ; xdotool windowfocus $i   ;  done ; xdotool key "alt+3" </Key>
# expose effect
<Key mask="PH" key="K">exec: kompose --singleshot </Key>

 
# like under fluxbox
 <Key mask="PH" key="F1">exec: xdotool set_desktop 0</Key>
 <Key mask="PH" key="F2">exec: xdotool set_desktop 1</Key>
 <Key mask="PH" key="F3">exec: xdotool set_desktop 2</Key>
 <Key mask="PH" key="F4">exec: xdotool set_desktop 3</Key>
 <Key mask="PH" key="Left">exec: i=$(xdotool get_desktop) ; z=$(($i - 1)) ; i=$z ; xdotool set_desktop $i  </Key>
 <Key mask="PH" key="Right">exec: i=$(xdotool get_desktop) ; z=$(($i + 1)) ; i=$z ; xdotool set_desktop $i  </Key>
# close to yakuake F12
 <Key mask="PH" key="F10">exec: i=$(xdotool get_desktop) ; z=$(($i - 1)) ; i=$z ; xdotool set_desktop $i</Key>
 <Key mask="PH" key="F11">exec: i=$(xdotool get_desktop) ; z=$(($i + 1)) ; i=$z ; xdotool set_desktop $i</Key>
#  
<Key mask="PH" key="M">minimize</Key>
<Key mask="PH" key="Y">minimize</Key>

<Key mask="PH" key="P">exec:  Esetroot -m $HOME/.wallpaper</Key>
 
# apps
<Key mask="PH" key="L">exec: xscreensaver-command -lock</Key>
<Key mask="PH" key="r">exec: mrxvt </Key>
#<Key mask="PH" key="e">exec: xterm </Key>


#send to right or left the activewindow
<Key mask="PH" key="s">exec: i=$(xdotool get_desktop) ; z=$(($i - 1)) ; i=$z ;   xdotool set_desktop_for_window  $(xdotool getactivewindow) $i  </Key>
<Key mask="PH" key="d">exec: i=$(xdotool get_desktop) ; z=$(($i + 1)) ; i=$z ; xdotool set_desktop_for_window  $(xdotool getactivewindow) $i  </Key> 
<Key mask="PH" key="f">exec: i=$(xdotool get_desktop) ; z=$(($i + 1)) ; i=$z ; xdotool set_desktop_for_window  $(xdotool getactivewindow) 3  </Key>

<Key mask="PH" key="X">exec: i=$(xdotool get_desktop) ; z=$(($i - 1)) ; i=$z ; xdotool set_desktop_for_window  $(xdotool getactivewindow) $i  ;  xdotool set_desktop $i ; xdotool click 1 </Key>
<Key mask="PH" key="C">exec: i=$(xdotool get_desktop) ; z=$(($i + 1)) ; i=$z ; xdotool set_desktop_for_window  $(xdotool getactivewindow) $i ;   xdotool set_desktop $i ; xdotool click 1   </Key>  


# tasks
<Key mask="PH" key="E">exec:  xdotool search --title  mrxvt    |  while read i ; do     xdotool set_desktop_for_window $i 1 ; xdotool windowraise $i  ; xdotool windowfocus $i   ;  done ; xdotool set_desktop 1 ;  xdotool windowfocus $i  </Key>
<Key mask="PH" key="T">exec: sh taskcoach.sh  </Key> 
  
<Key mask="PH" key="space">maximize</Key>

</JWM>



  







**PH in the code above means SUPER, which is hte windows flag of your keyboard**

---

### Post by ibuclaw on 2009-10-18
Moving to the community cafe, as it isn't a support question.


JWM is nice.

I've got two setups at the the moment, One using Gnome-Shell, the other Xmonad.

---

### Post by kerry_s on 2009-10-18
jwm is nice if you want to take the time to set it up. i use to use it, but i'm good enough i can get the same low resource out of gnome, being lazier these days, i prefer to just use the computer instead of spending hours/days/months tweaking it.

---

### Post by earthpigg on 2009-10-18
> **kerry_s said:**
> jwm is nice if you want to take the time to set it up. i use to use it, but i'm good enough i can get the same low resource out of gnome, being lazier these days, i prefer to just use the computer instead of spending hours/days/months tweaking it.

the solution i found was to take notes and document my tweaks, so they can be replicated again in the future with a minimal amount of hassle and time spent.

---

### Post by frenchn00b on 2009-10-18
> **kerry_s said:**
> jwm is nice if you want to take the time to set it up. i use to use it, but i'm good enough i can get the same low resource out of gnome, being lazier these days, i prefer to just use the computer instead of spending hours/days/months tweaking it.

here is my .jwmrc that is in $HOME
it's very easy to configure
although I miss "sento" anothher desktop a window

```
<?xml version="1.0"?>

<JWM>

<StartupCommand>
Esetroot -m $HOME/wallpapers/wallpaper.jpg
</StartupCommand>


   <!-- The root menu, if this is undefined you will not get a menu. -->
   <!-- Additional RootMenu attributes: onroot, labeled, label -->
   <RootMenu height="15" onroot="123">
      <Program icon="rxvt.png" label="Terminal">x-terminal-emulator</Program>
      <Program icon="firefox.png" label="konsole">konsole</Program>
      <Program icon="firefox.png" label="Www Browser">firefox</Program>

<!-- #DEBIAN
      <Menu icon="folder.png" label="Applications">
         <Program icon="audacious.png" label="Audacious">audacious</Program>
         <Program icon="dia.png" label="Dia">dia</Program>
         <Program icon="firefox.png" label="Firefox">firefox</Program>
         <Program icon="pidgin.png" label="Pidgin">pidgin</Program>
         <Program icon="gimp.png" label="Gimp">gimp</Program>
         <Program icon="gtk-gnutella.png" label="gtk-gnutella">
            gtk-gnutella
         </Program>
         <Program icon="gxine.png" label="gxine">gxine</Program>
         <Program icon="ooffice.png" label="Open Office">ooffice</Program>
      </Menu>
      <Menu icon="folder.png" label="Utilities">
         <Program icon="xcalc.png">xcalc</Program>
         <Program icon="xfontsel.png">xfontsel</Program>
         <Program icon="xmag.png">xmag</Program>
         <Program icon="xprop.png" label="xprop">
            xprop | xmessage -file -
         </Program>
      </Menu>
-->
      <Separator/>
      <Restart label="Restart" icon="restart.png"/>
      <Exit label="Exit" confirm="true" icon="exit.png"/>
   </RootMenu>

   <Group>
      <Class>Pidgin</Class>
      <Option>sticky</Option>
   </Group>

   <Group>
      <Name>gkrellm2</Name>
      <Option>nolist</Option>
   </Group>

   <Group>
      <Name>rxvt</Name>
      <Option>vmax</Option>
   </Group>

   <!-- Additional tray attributes: autohide, width, border, layer, layout -->
   <Tray  x="0" y="-1" height="32">

      <!-- Additional TrayButton attribute: label -->
      <TrayButton label="JWM">root:1</TrayButton>

      <TrayButton label="_">showdesktop</TrayButton>

      <!-- Additional Pager attributes; width, height -->
      <Pager/>

      <!-- Additional TaskList attribute: maxwidth -->
      <TaskList/>

      <Dock/>

      <!-- Additional Swallow attribute: height -->
      <Swallow name="xload" width="64">
         xload -nolabel -bg black -fg red -hl white
      </Swallow>

      <Clock format="%H:%M">xclock</Clock>

   </Tray>

   <!-- Visual Styles -->

   <WindowStyle>

      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Width>4</Width>
      <Height>20</Height>

      <Active>
         <Text>white</Text>
<!-- #DEBIAN
         <Title>#70849d:#2e3a67</Title>
         <Corner>white</Corner>
-->
         <Title>gray30:gray60</Title>
         <Corner>gray20:white</Corner>
         <Outline>black</Outline>
      </Active>

      <Inactive>
         <Text>#aaaaaa</Text>
         <Title>#808488:#303438</Title>
         <Corner>#aaaaaa</Corner>
         <Outline>black</Outline>
      </Inactive>

   </WindowStyle>

   <TaskListStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <ActiveForeground>black</ActiveForeground>
      <ActiveBackground>gray90:gray70</ActiveBackground>
      <Foreground>black</Foreground>
      <Background>gray70:gray90</Background>
   </TaskListStyle>

   <!-- Additional TrayStyle attribute: insert -->
   <TrayStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Background>gray90</Background>
      <Foreground>black</Foreground>
   </TrayStyle>

   <PagerStyle>
      <Outline>black</Outline>
      <Foreground>gray90</Foreground>
      <Background>#808488</Background>
      <ActiveForeground>#70849d</ActiveForeground>
      <ActiveBackground>#2e3a67</ActiveBackground>
   </PagerStyle>

   <MenuStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Foreground>black</Foreground>
      <Background>gray90</Background>
      <ActiveForeground>white</ActiveForeground>
      <ActiveBackground>#70849d:#2e3a67</ActiveBackground>
   </MenuStyle>

   <PopupStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Outline>black</Outline>
      <Foreground>black</Foreground>
      <Background>yellow</Background>
   </PopupStyle>

   <IconPath>
      $HOME/.icons
   </IconPath>

   <!-- Virtual Desktops -->
   <!-- Desktop tags can be contained within Desktops for desktop names. -->
   <Desktops count="4">

      <!-- Default background. Note that a Background tag can be
           contained within a Desktop tag to give a specific background
           for that desktop.
       -->
 
<Background type="image">$HOME/wallpapers/wallpaper.jpg</Background>
</Desktops>

   <!-- Double click speed (in milliseconds) -->
   <DoubleClickSpeed>400</DoubleClickSpeed>

   <!-- Double click delta (in pixels) -->
   <DoubleClickDelta>2</DoubleClickDelta>

   <!-- The focus model (sloppy or click) -->
   <FocusModel>click</FocusModel>

   <!-- The snap mode (none, screen, or border) -->
   <SnapMode distance="10">border</SnapMode>

   <!-- The move mode (outline or opaque) -->
   <MoveMode>opaque</MoveMode>

   <!-- The resize mode (outline or opaque) -->
   <ResizeMode>opaque</ResizeMode>

   <!-- Key bindings -->
   <Key key="Up">up</Key>
   <Key key="Down">down</Key>

   <Key key="h">left</Key>
   <Key key="j">down</Key>
   <Key key="k">up</Key>
   <Key key="l">right</Key>
   <Key key="Return">select</Key>
   <Key key="Escape">escape</Key>

   <Key mask="A" key="Tab">nextstacked</Key>
   <Key mask="A" key="F4">close</Key>
<Key mask="A" key="#">desktop#</Key>
<Key mask="A" key="M">showdesktop</Key>
<Key mask="CA" key="space">maximize</Key>
<Key mask="A" key="space">maximize</Key>
<Key mask="A" key="Return">maximize</Key>
<Key mask="A" key="F2">exec: grun</Key>
<Key mask="A" key="R">exec: grun</Key>
<Key mask="A" key="E">exec: pcmanfm</Key>

   <Key mask="A" key="F1">root:1</Key>


</JWM>

```

this JWM is Turbo Fast! Fastest as lightnings :)

---

### Post by tcoffeep on 2009-10-18
ugh. i was going to look into jwm and then i saw xml. DONOTWANT

---

### Post by kerry_s on 2009-10-18
> the solution i found was to take notes and document my tweaks, so they can be replicated again in the future with a minimal amount of hassle and time spent.

it's all in my head, depends on what style i want to go with, i've made jwm do all kinds of styles.


> here is my .jwmrc that is in $HOME
it's very easy to configure
although I miss "sento" anothher desktop a window

do a search of the forum & you might find some of mine, just be aware, i do things my own way, so some may look far from the stock "jwmrc".

---

### Post by frenchn00b on 2009-10-20
> **kerry_s said:**
>  

do a search of the forum & you might find some of mine, just be aware, i do things my own way, so some may look far from the stock "jwmrc".

well .. on the board, unfortunately, there isnt so much jwmrc config. Well sendto affected to a key shortcut, ie. kindings, I  couldnt find, still on the ubuntu forum. :(

---

### Post by NightwishFan on 2009-10-20
I use JWM on puppy and I like it. On Ubuntu I use TWM, which is very minimal by default. It saves me all the panel/nautilus ram that I would not need when using Vbox or Wine.

---

### Post by frenchn00b on 2009-10-20
> **NightwishFan said:**
> I use JWM on puppy and I like it. On Ubuntu I use TWM, which is very minimal by default. It saves me all the panel/nautilus ram that I would not need when using Vbox or Wine.

have you tried vtwm, its quite low ressources too, and is highly customizable... nice wm too

---

### Post by frenchn00b on 2009-10-20
btw is there some round-corners possibilities for themes in Jwm?

---

### Post by frenchn00b on 2009-10-23
[ SOLVED JWM SENDTO BINDINGS ] 

apt-get install xdotool


and add this to your .jwmrc:

```

 <Key mask="A" key="F1">exec: xdotool set_desktop_for_window  $(xdotool getactivewindow)  0 </Key>

 <Key mask="A" key="F2">exec: xdotool set_desktop_for_window  $(xdotool getactivewindow)  1 </Key>

 <Key mask="A" key="F3">exec: xdotool set_desktop_for_window  $(xdotool getactivewindow)  2 </Key>

 <Key mask="A" key="F4">exec: xdotool set_desktop_for_window  $(xdotool getactivewindow)  3 </Key>


```

---

### Post by frenchn00b on 2009-10-23
A new code: 

This will place all the skype and pidgin windows into the desktop number 3, and will put ur focus on it.



```

 <Key mask="A" key="I">exec:  xdotool search --title  skype    |  while read i ; do     xdotool set_desktop_for_window $i 2 ; xdotool windowraise $i  ; xdotool windowfocus $i   ;  done ; xdotool key "alt+3" </Key>

<Key mask="A" key="K">exec:  xdotool search --title  pidgin    |  while read i ; do     xdotool set_desktop_for_window $i 2 ; xdotool windowraise $i  ; xdotool windowfocus $i   ;  done ; xdotool key "alt+3" </Key>

  
```

Enjoy

here is my all code .jwmrc:
```
<?xml version="1.0"?>


<JWM>

<StartupCommand>
Esetroot -m $HOME/.wallpaper
# do not forget ampersand here after
</StartupCommand>


   <!-- The root menu, if this is undefined you will not get a menu. -->
   <!-- Additional RootMenu attributes: onroot, labeled, label -->
   <RootMenu height="15" onroot="123">
      <Program icon="rxvt.png" label="Terminal">x-terminal-emulator</Program>
      <Program icon="firefox.png" label="konsole">konsole</Program>
      <Program icon="firefox.png" label="Www Browser">firefox</Program>

<!-- #DEBIAN
      <Menu icon="folder.png" label="Applications">
         <Program icon="audacious.png" label="Audacious">audacious</Program>
         <Program icon="dia.png" label="Dia">dia</Program>
         <Program icon="firefox.png" label="Firefox">firefox</Program>
         <Program icon="pidgin.png" label="Pidgin">pidgin</Program>
         <Program icon="gimp.png" label="Gimp">gimp</Program>
         <Program icon="gtk-gnutella.png" label="gtk-gnutella">
            gtk-gnutella
         </Program>
         <Program icon="gxine.png" label="gxine">gxine</Program>
         <Program icon="ooffice.png" label="Open Office">ooffice</Program>
      </Menu>

      <Menu icon="folder.png" label="Utilities">
         <Program icon="xcalc.png">xcalc</Program>
         <Program icon="xfontsel.png">xfontsel</Program>
         <Program icon="xmag.png">xmag</Program>
         <Program icon="xprop.png" label="xprop">
            xprop | xmessage -file -
         </Program>
</Menu>

  
    
-->
      <Separator/>
      <Restart label="Restart" icon="restart.png"/>
      <Exit label="Exit" confirm="true" icon="exit.png"/>
   </RootMenu>

   <Group>
      <Class>Pidgin</Class>
      <Option>sticky</Option>
   </Group>

   <Group>
      <Name>gkrellm2</Name>
      <Option>nolist</Option>
   </Group>

   <Group>
      <Name>rxvt</Name>
      <Option>vmax</Option>
   </Group>

   <!-- Additional tray attributes: autohide, width, border, layer, layout -->
   <Tray  x="0" y="-1" height="32">

      <!-- Additional TrayButton attribute: label -->
      <TrayButton label="JWM">root:1</TrayButton>

      <TrayButton label="_">showdesktop</TrayButton>

      <!-- Additional Pager attributes; width, height -->
      <Pager/>

      <!-- Additional TaskList attribute: maxwidth -->
      <TaskList/>

      <Dock/>

      <!-- Additional Swallow attribute: height -->
      <Swallow name="xload" width="64">
         xload -nolabel -bg black -fg red -hl white
      </Swallow>

      <Clock format="%H:%M">xterm -e alsamixer</Clock>

   </Tray>

   <!-- Visual Styles -->

   <WindowStyle>

      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Width>4</Width>
      <Height>20</Height>

      <Active>
         <Text>white</Text>
<!-- #DEBIAN
         <Title>#70849d:#2e3a67</Title>
         <Corner>white</Corner>
-->
         <Title>gray30:gray60</Title>
         <Corner>gray20:white</Corner>
         <Outline>black</Outline>
      </Active>

      <Inactive>
         <Text>#aaaaaa</Text>
         <Title>#808488:#303438</Title>
         <Corner>#aaaaaa</Corner>
         <Outline>black</Outline>
      </Inactive>

   </WindowStyle>

   <TaskListStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <ActiveForeground>black</ActiveForeground>
      <ActiveBackground>gray90:gray70</ActiveBackground>
      <Foreground>black</Foreground>
      <Background>gray70:gray90</Background>
   </TaskListStyle>

   <!-- Additional TrayStyle attribute: insert -->
   <TrayStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Background>gray90</Background>
      <Foreground>black</Foreground>
   </TrayStyle>

   <PagerStyle>
      <Outline>black</Outline>
      <Foreground>gray90</Foreground>
      <Background>#808488</Background>
      <ActiveForeground>#70849d</ActiveForeground>
      <ActiveBackground>#2e3a67</ActiveBackground>
   </PagerStyle>

   <MenuStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Foreground>black</Foreground>
      <Background>gray90</Background>
      <ActiveForeground>white</ActiveForeground>
      <ActiveBackground>#70849d:#2e3a67</ActiveBackground>
   </MenuStyle>

   <PopupStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Outline>black</Outline>
      <Foreground>black</Foreground>
      <Background>yellow</Background>
   </PopupStyle>

   <IconPath>
      $HOME/.icons
   </IconPath>

   <!-- Virtual Desktops -->
   <!-- Desktop tags can be contained within Desktops for desktop names. -->
   <Desktops count="4">

      <!-- Default background. Note that a Background tag can be
           contained within a Desktop tag to give a specific background
           for that desktop.
       -->
 
<Background type="image">$HOME/wallpapers/wallpaper.jpg</Background>
</Desktops>

   <!-- Double click speed (in milliseconds) -->
   <DoubleClickSpeed>400</DoubleClickSpeed>

   <!-- Double click delta (in pixels) -->
   <DoubleClickDelta>2</DoubleClickDelta>

   <!-- The focus model (sloppy or click) -->
   <FocusModel>click</FocusModel>

   <!-- The snap mode (none, screen, or border) -->
   <SnapMode distance="10">border</SnapMode>

   <!-- The move mode (outline or opaque) -->
   <MoveMode>opaque</MoveMode>

   <!-- The resize mode (outline or opaque) -->
   <ResizeMode>opaque</ResizeMode>

   <!-- Key bindings -->
   <Key key="Up">up</Key>
   <Key key="Down">down</Key>

   <Key key="h">left</Key>
   <Key key="j">down</Key>
   <Key key="k">up</Key>
   <Key key="l">right</Key>
   <Key key="Return">select</Key>
   <Key key="Escape">escape</Key>

   <Key mask="A" key="Tab">nextstacked</Key>
   <Key mask="A" key="F10">close</Key>

<Key mask="A" key="#">desktop#</Key>
<Key mask="A" key="M">showdesktop</Key>

<Key mask="A" key="L">exec: xscreensaver-command -lock</Key>

<Key mask="CA" key="space">maximize</Key>
<Key mask="A" key="space">maximize</Key>
<Key mask="A" key="Return">maximize</Key>
<Key mask="A" key="F6">exec: grun</Key>
<Key mask="A" key="R">exec: grun</Key>
<Key mask="A" key="E">exec: pcmanfm</Key>

<Key mask="A" key="O">exec: audacious</Key>


   <Key mask="A" key="F5">root:1</Key>

 <Key mask="A" key="F1">exec: xdotool set_desktop_for_window  $(xdotool getactivewindow)  0 </Key>

 <Key mask="A" key="F2">exec: xdotool set_desktop_for_window  $(xdotool getactivewindow)  1 </Key>

 <Key mask="A" key="F3">exec: xdotool set_desktop_for_window  $(xdotool getactivewindow)  2 </Key>

 <Key mask="A" key="F4">exec: xdotool set_desktop_for_window  $(xdotool getactivewindow)  3 </Key>

 <Key mask="A" key="I">exec:  xdotool search --title  skype    |  while read i ; do     xdotool set_desktop_for_window $i 2 ; xdotool windowraise $i  ; xdotool windowfocus $i   ;  done ; xdotool key "alt+3" </Key>

<Key mask="A" key="K">exec:  xdotool search --title  pidgin    |  while read i ; do     xdotool set_desktop_for_window $i 2 ; xdotool windowraise $i  ; xdotool windowfocus $i   ;  done ; xdotool key "alt+3" </Key>

  

</JWM>


```

---

### Post by frenchn00b on 2009-10-23
Here is a new program to take screenshots:

```
#!/bin/sh

i="`cat $HOME/.scrottkrc`"

j="$i"

let i="i+1"


echo  "Enter the filename, incrementing=$j to $i  " 

 
cd screenshots

filenameoutput="$(date +%Y%m%d)shot_$i.jpg"



echo "writing to :  $filenameoutput"

scrot    "$filenameoutput"


ls -lah  "$filenameoutput"


echo "the value of increment is now: $i"
echo $i > $HOME/.scrottkrc
cd


```

you use it as into .jwmrc:

```
   <Key key="Print">exec:  sh $HOME/makescreenshot.sh </Key>


```

---

### Post by frenchn00b on 2009-11-06
[COLOR="Red"][B]Here is my fluxbox feelings for JWM, ! ;)[/COLOR]
it has screenshots, and one can use it as fluxbox, and it is much much much faster and lighter ! Enjoy !! 
PRINTSCREEN is also available 
try alt+ctrl+right arrow ... [/B]

(one need xdotool, its in the repositories)

put this .jwmrc into you HOME user directory: 
  

> <?xml version="1.0"?>


<JWM>

<StartupCommand>
Esetroot -m $HOME/.wallpaper
kmix &
tilda  &


# do not forget ampersand here after
</StartupCommand>


   <!-- The root menu, if this is undefined you will not get a menu. -->
   <!-- Additional RootMenu attributes: onroot, labeled, label -->
   <RootMenu height="15" onroot="123">
      <Program icon="rxvt.png" label="Terminal">x-terminal-emulator</Program>
      <Program icon="firefox.png" label="konsole">konsole</Program>
      <Program icon="firefox.png" label="Www Browser">firefox</Program>

<!-- #DEBIAN
      <Menu icon="folder.png" label="Applications">
         <Program icon="audacious.png" label="Audacious">audacious</Program>
         <Program icon="dia.png" label="Dia">dia</Program>
         <Program icon="firefox.png" label="Firefox">firefox</Program>
         <Program icon="pidgin.png" label="Pidgin">pidgin</Program>
         <Program icon="gimp.png" label="Gimp">gimp</Program>
         <Program icon="gtk-gnutella.png" label="gtk-gnutella">
            gtk-gnutella
         </Program>
         <Program icon="gxine.png" label="gxine">gxine</Program>
         <Program icon="ooffice.png" label="Open Office">ooffice</Program>
      </Menu>

      <Menu icon="folder.png" label="Utilities">
         <Program icon="xcalc.png">xcalc</Program>
         <Program icon="xfontsel.png">xfontsel</Program>
         <Program icon="xmag.png">xmag</Program>
         <Program icon="xprop.png" label="xprop">
            xprop | xmessage -file -
         </Program>
</Menu>

  
    
-->
      <Separator/>
      <Restart label="Restart" icon="restart.png"/>
      <Exit label="Exit" confirm="true" icon="exit.png"/>
   </RootMenu>

#   <Group>
#      <Class>Pidgin</Class>
#      <Option>sticky</Option>
#   </Group>

   <Group>
      <Name>gkrellm2</Name>
      <Option>nolist</Option>
   </Group>

   <Group>
      <Name>rxvt</Name>
      <Option>vmax</Option>
   </Group>

   <!-- Additional tray attributes: autohide, width, border, layer, layout -->
   <Tray  x="0" y="-1" height="32">

      <!-- Additional TrayButton attribute: label -->
      <TrayButton label="JWM">root:1</TrayButton>

      <TrayButton label="_">showdesktop</TrayButton>

      <!-- Additional Pager attributes; width, height -->
      <Pager/>

      <!-- Additional TaskList attribute: maxwidth -->
      <TaskList/>

      <Dock/>

      <!-- Additional Swallow attribute: height -->
      <Swallow name="xload" width="64">
         xload -nolabel -bg black -fg red -hl white
      </Swallow>

      <Clock format="%H:%M">kmix</Clock>

   </Tray>

   <!-- Visual Styles -->

   <WindowStyle>

      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Width>4</Width>
      <Height>20</Height>

      <Active>
         <Text>white</Text>
<!-- #DEBIAN
         <Title>#70849d:#2e3a67</Title>
         <Corner>white</Corner>
-->
         <Title>gray30:gray60</Title>
         <Corner>gray20:white</Corner>
         <Outline>black</Outline>
      </Active>

      <Inactive>
         <Text>#aaaaaa</Text>
         <Title>#808488:#303438</Title>
         <Corner>#aaaaaa</Corner>
         <Outline>black</Outline>
      </Inactive>

   </WindowStyle>

   <TaskListStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <ActiveForeground>black</ActiveForeground>
      <ActiveBackground>gray90:gray70</ActiveBackground>
      <Foreground>black</Foreground>
      <Background>gray70:gray90</Background>
   </TaskListStyle>

   <!-- Additional TrayStyle attribute: insert -->
   <TrayStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Background>gray90</Background>
      <Foreground>black</Foreground>
   </TrayStyle>

   <PagerStyle>
      <Outline>black</Outline>
      <Foreground>gray90</Foreground>
      <Background>#808488</Background>
      <ActiveForeground>#70849d</ActiveForeground>
      <ActiveBackground>#2e3a67</ActiveBackground>
   </PagerStyle>

   <MenuStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Foreground>black</Foreground>
      <Background>gray90</Background>
      <ActiveForeground>white</ActiveForeground>
      <ActiveBackground>#70849d:#2e3a67</ActiveBackground>
   </MenuStyle>

   <PopupStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Outline>black</Outline>
      <Foreground>black</Foreground>
      <Background>yellow</Background>
   </PopupStyle>

   <IconPath>
      $HOME/.icons
   </IconPath>

   <!-- Virtual Desktops -->
   <!-- Desktop tags can be contained within Desktops for desktop names. -->
   <Desktops count="5">

      <!-- Default background. Note that a Background tag can be
           contained within a Desktop tag to give a specific background
           for that desktop.
       -->
 
<Background type="image">$HOME/wallpapers/wallpaper.jpg</Background>
</Desktops>

   <!-- Double click speed (in milliseconds) -->
   <DoubleClickSpeed>400</DoubleClickSpeed>

   <!-- Double click delta (in pixels) -->
   <DoubleClickDelta>2</DoubleClickDelta>

   <!-- The focus model (sloppy or click) -->
   <FocusModel>click</FocusModel>

   <!-- The snap mode (none, screen, or border) -->
   <SnapMode distance="10">border</SnapMode>

   <!-- The move mode (outline or opaque) -->
   <MoveMode>opaque</MoveMode>

   <!-- The resize mode (outline or opaque) -->
   <ResizeMode>opaque</ResizeMode>

   <!-- Key bindings -->
   <Key key="Up">up</Key>
   <Key key="Down">down</Key>

   <Key key="h">left</Key>
   <Key key="j">down</Key>
   <Key key="k">up</Key>
   <Key key="l">right</Key>
   <Key key="Return">select</Key>
   <Key key="Escape">escape</Key>

   <Key mask="A" key="Tab">nextstacked</Key>
#   <Key mask="A" key="F10">close</Key>

<Key mask="A" key="#">desktop#</Key>
<Key mask="A" key="M">showdesktop</Key>

<Key mask="A" key="L">exec: xscreensaver-command -lock</Key>

<Key mask="CA" key="space">maximize</Key>
<Key mask="A" key="space">maximize</Key>
<Key mask="A" key="Return">maximize</Key>

<Key mask="A" key="X">minimize</Key>


<Key mask="A" key="F6">exec: grun</Key>
<Key mask="A" key="R">exec: grun</Key>
<Key mask="A" key="E">exec: pcmanfm</Key>
<Key mask="A" key="T">exec: rox</Key>

<Key mask="A" key="O">exec: audacious2</Key>
<Key mask="A" key="I">exec: cd ; rox music </Key>
 
<Key mask="C" key="F1">exec: xdotool set_desktop_for_window  $(xdotool getactivewindow)  0 </Key>
<Key mask="C" key="F2">exec: xdotool set_desktop_for_window  $(xdotool getactivewindow)  1 </Key>
<Key mask="C" key="F3">exec: xdotool set_desktop_for_window  $(xdotool getactivewindow)  2 </Key>
<Key mask="C" key="F4">exec: xdotool set_desktop_for_window  $(xdotool getactivewindow)  3 </Key>
<Key mask="C" key="F5">exec: xdotool set_desktop_for_window  $(xdotool getactivewindow)  4</Key>

# like under fluxbox
 <Key mask="A" key="F1">exec: xdotool set_desktop 0</Key>
 <Key mask="A" key="F2">exec: xdotool set_desktop 1</Key>
 <Key mask="A" key="F3">exec: xdotool set_desktop 2</Key>
 <Key mask="A" key="F4">exec: xdotool set_desktop 3</Key>
 <Key mask="A" key="F5">exec: xdotool set_desktop 4</Key>
# close to yakuake F12
 <Key mask="A" key="F10">exec: let i="`xdotool get_desktop`-1" ; xdotool set_desktop $i</Key>
 <Key mask="A" key="F11">exec: let i="1+`xdotool get_desktop`" ; xdotool set_desktop $i</Key>
 <Key mask="A" key="F12">exec: xdotool key F12</Key>

# like under fluxbox
 <Key mask="CA" key="Left">exec: let i="`xdotool get_desktop`-1" ; xdotool set_desktop $i</Key>
 <Key mask="CA" key="Right">exec: let i="1+`xdotool get_desktop`" ; xdotool set_desktop $i</Key>
 <Key mask="A" key="S">exec: let i="`xdotool get_desktop`-1" ; xdotool set_desktop $i</Key>
 <Key mask="A" key="D">exec: let i="1+`xdotool get_desktop`" ; xdotool set_desktop $i</Key>

  <Key mask="P" key="Left">exec: let i="`xdotool get_desktop`-1" ; xdotool set_desktop $i</Key>
 <Key mask="P" key="Right">exec: let i="1+`xdotool get_desktop`" ; xdotool set_desktop $i</Key>

# like under fluxbox
 <Key mask="P" key="F1">exec: xdotool set_desktop 0</Key>
 <Key mask="P" key="F2">exec: xdotool set_desktop 1</Key>
 <Key mask="P" key="F3">exec: xdotool set_desktop 2</Key>
 <Key mask="P" key="F4">exec: xdotool set_desktop 3</Key>
 <Key mask="P" key="F5">exec: xdotool set_desktop 4</Key> 


<Key mask="P" key="L">exec:xscreensaver-command -lock</Key>


  #make a screenshot
  <Key key="Print">exec:  cd ; mkdir screenshots ;  i="`cat $HOME/.scrottkrc`" ; j="$i" ; let i="i+1" ; echo  "Enter the filename, incrementing=$j to $i  " ; cd screenshots ;  filenameoutput="$(date +%Y%m%d)shot_$i.jpg"  ; echo "writing to :  $filenameoutput"  ; scrot    "$filenameoutput" ; echo $i > $HOME/.scrottkrc  </Key>


# select pidgin on a specific workspace
 <Key mask="A" key="J">exec:  xdotool search --title  skype    |  while read i ; do     xdotool set_desktop_for_window $i 2 ; xdotool windowraise $i  ; xdotool windowfocus $i   ;  done ; xdotool key "alt+3" </Key>
<Key mask="A" key="K">exec:  xdotool search --title  pidgin    |  while read i ; do     xdotool set_desktop_for_window $i 2 ; xdotool windowraise $i  ; xdotool windowfocus $i   ;  done ; xdotool key "alt+3" </Key>



</JWM>



  







---

### Post by frenchn00b on 2009-11-10
here I found some nice themes:
[http://puppylin.freehostia.com/jwm.htm](http://puppylin.freehostia.com/jwm.htm)

---

### Post by frenchn00b on 2009-12-08
here is how to install jwm:

with sudo su
> apt-get install jwm
cp /usr/share/jwm/xsessions/Jwm.desktop /usr/share/xsessions/

---

### Post by bellzers on 2010-01-07
> **frenchn00b said:**
> here is how to install jwm:

with sudo su

thanks. was wondering how to do this and why it was not a default.

---

### Post by frenchn00b on 2010-01-10
> **bellzers said:**
> thanks. was wondering how to do this and why it was not a default.


your welcome. please reportbug is this is missing into gdm or kdm for your installation. 

Here is my $HOME/.jwmrc:
(PH is the super windows flag key, for the bindings)

```

<?xml version="1.0"?>


<JWM>

<StartupCommand>
Esetroot -m $HOME/.wallpaper
tilda  &
xscreensaver -no-splash & 


# do not forget ampersand here after
</StartupCommand>


   <!-- The root menu, if this is undefined you will not get a menu. -->
   <!-- Additional RootMenu attributes: onroot, labeled, label -->
   <RootMenu height="15" onroot="123">
      <Program icon="rxvt.png" label="Terminal">x-terminal-emulator</Program>
      <Program icon="firefox.png" label="konsole">konsole</Program>
      <Program icon="firefox.png" label="Www Browser">firefox</Program>

<!-- #DEBIAN
      <Menu icon="folder.png" label="Applications">
         <Program icon="audacious.png" label="Audacious">audacious</Program>
         <Program icon="dia.png" label="Dia">dia</Program>
         <Program icon="firefox.png" label="Firefox">firefox</Program>
         <Program icon="pidgin.png" label="Pidgin">pidgin</Program>
         <Program icon="gimp.png" label="Gimp">gimp</Program>
         <Program icon="gtk-gnutella.png" label="gtk-gnutella">
            gtk-gnutella
         </Program>
         <Program icon="gxine.png" label="gxine">gxine</Program>
         <Program icon="ooffice.png" label="Open Office">ooffice</Program>
      </Menu>

      <Menu icon="folder.png" label="Utilities">
         <Program icon="xcalc.png">xcalc</Program>
         <Program icon="xfontsel.png">xfontsel</Program>
         <Program icon="xmag.png">xmag</Program>
         <Program icon="xprop.png" label="xprop">
            xprop | xmessage -file -
         </Program>
</Menu>

  
    
-->
      <Separator/>
      <Restart label="Restart" icon="restart.png"/>
      <Exit label="Exit" confirm="true" icon="exit.png"/>
   </RootMenu>

#   <Group>
#      <Class>Pidgin</Class>
#      <Option>sticky</Option>
#   </Group>

   <Group>
      <Name>gkrellm2</Name>
      <Option>nolist</Option>
   </Group>

   <Group>
      <Name>rxvt</Name>
      <Option>vmax</Option>
   </Group>

   <!-- Additional tray attributes: autohide, width, border, layer, layout -->
   <Tray  x="0" y="+1" height="28">

      <!-- Additional TrayButton attribute: label -->
      <TrayButton label="JWM">root:1</TrayButton>

      <TrayButton label="_">showdesktop</TrayButton>

      <!-- Additional Pager attributes; width, height -->
      <Pager/>

      <!-- Additional TaskList attribute: maxwidth -->
      <TaskList/>

      <Dock/>

      <!-- Additional Swallow attribute: height -->
      <Swallow name="xload" width="64">
         xload -nolabel -bg black -fg red -hl white
      </Swallow>

      <Clock format="%H:%M">xterm  </Clock>

   </Tray>

   <!-- Visual Styles -->

   <WindowStyle>

      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Width>4</Width>
      <Height>20</Height>

      <Active>
         <Text>white</Text>
<!-- #DEBIAN
         <Title>#70849d:#2e3a67</Title>
         <Corner>white</Corner>
-->
         <Title>gray30:gray60</Title>
         <Corner>gray20:white</Corner>
         <Outline>black</Outline>
      </Active>

      <Inactive>
         <Text>#aaaaaa</Text>
         <Title>#808488:#303438</Title>
         <Corner>#aaaaaa</Corner>
         <Outline>black</Outline>
      </Inactive>

   </WindowStyle>

   <TaskListStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <ActiveForeground>black</ActiveForeground>
      <ActiveBackground>gray90:gray70</ActiveBackground>
      <Foreground>black</Foreground>
      <Background>gray70:gray90</Background>
   </TaskListStyle>

   <!-- Additional TrayStyle attribute: insert -->
   <TrayStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Background>gray90</Background>
      <Foreground>black</Foreground>
   </TrayStyle>

   <PagerStyle>
      <Outline>black</Outline>
      <Foreground>gray90</Foreground>
      <Background>#808488</Background>
      <ActiveForeground>#70849d</ActiveForeground>
      <ActiveBackground>#2e3a67</ActiveBackground>
   </PagerStyle>

   <MenuStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Foreground>black</Foreground>
      <Background>gray90</Background>
      <ActiveForeground>white</ActiveForeground>
      <ActiveBackground>#70849d:#2e3a67</ActiveBackground>
   </MenuStyle>

   <PopupStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Outline>black</Outline>
      <Foreground>black</Foreground>
      <Background>yellow</Background>
   </PopupStyle>

   <IconPath>
      $HOME/.icons
   </IconPath>

   <!-- Virtual Desktops -->
   <!-- Desktop tags can be contained within Desktops for desktop names. -->
   <Desktops count="4">

      <!-- Default background. Note that a Background tag can be
           contained within a Desktop tag to give a specific background
           for that desktop.
       -->
 
<Background type="image">$HOME/wallpapers/wallpaper.jpg</Background>
</Desktops>

   <!-- Double click speed (in milliseconds) -->
   <DoubleClickSpeed>400</DoubleClickSpeed>

   <!-- Double click delta (in pixels) -->
   <DoubleClickDelta>2</DoubleClickDelta>

   <!-- The focus model (sloppy or click) -->
   <FocusModel>click</FocusModel>

   <!-- The snap mode (none, screen, or border) -->
   <SnapMode distance="10">border</SnapMode>

   <!-- The move mode (outline or opaque) -->
   <MoveMode>opaque</MoveMode>

   <!-- The resize mode (outline or opaque) -->
   <ResizeMode>opaque</ResizeMode>

   <!-- Key bindings -->
   <Key key="Up">up</Key>
   <Key key="Down">down</Key>
   <Key key="Return">select</Key>
   <Key key="Escape">escape</Key>

<Key mask="A" key="Tab">nextstacked</Key>
# <Key mask="A" key="F10">close</Key>

<Key mask="PH" key="#">desktop#</Key>
<Key mask="A" key="M">showdesktop</Key>
<Key mask="A" key="L">exec: xscreensaver-command -lock</Key>
<Key mask="A" key="space">maximize</Key>
<Key mask="A" key="Return">maximize</Key>
<Key mask="A" key="R">exec: gmrun</Key>
<Key mask="A" key="T">exec: rox</Key>
<Key mask="SA" key="T">exec: rox /tmp </Key>
 
# like under fluxbox
 <Key mask="A" key="F1">exec: xdotool set_desktop 0</Key>
 <Key mask="A" key="F2">exec: xdotool set_desktop 1</Key>
 <Key mask="A" key="F3">exec: xdotool set_desktop 2</Key>
 <Key mask="A" key="F4">exec: xdotool set_desktop 3</Key>
 <Key mask="A" key="F5"> close </Key>


# send to right or left the activewindow and follow
# <Key mask="PH" key="s">exec: i=$(xdotool get_desktop) ; z=$(($i - 1)) ; i=$z ; xdotool set_desktop_for_window  $(xdotool getactivewindow) $i  ;  xdotool set_desktop $i ; xdotool click 1 </Key>
# <Key mask="PH" key="d">exec: i=$(xdotool get_desktop) ; z=$(($i + 1)) ; i=$z ; xdotool set_desktop_for_window  $(xdotool getactivewindow) $i ;   xdotool set_desktop $i ; xdotool click 1   </Key>  
<Key mask="CAS" key="Left">exec: i=$(xdotool get_desktop) ; z=$(($i - 1)) ; i=$z ; xdotool set_desktop_for_window  $(xdotool getactivewindow) $i  ;  xdotool set_desktop $i ; xdotool click 1 </Key>
<Key mask="CAS" key="Right">exec: i=$(xdotool get_desktop) ; z=$(($i + 1)) ; i=$z ; xdotool set_desktop_for_window  $(xdotool getactivewindow) $i ;   xdotool set_desktop $i ; xdotool click 1   </Key>  

# like under fluxbox
 <Key mask="CA" key="Left">exec: i=$(xdotool get_desktop) ; z=$(($i - 1)) ; i=$z ; xdotool set_desktop $i</Key>
 <Key mask="CA" key="Right">exec: i=$(xdotool get_desktop) ; z=$(($i + 1)) ; i=$z ; xdotool set_desktop $i</Key>


#make a screenshot
<Key key="Print">exec:  cd ; mkdir screenshots ;  i="`cat $HOME/.scrottkrc`" ; j="$i" ; let i="i+1" ; echo  "Enter the filename, incrementing=$j to $i  " ; cd screenshots ;  filenameoutput="$(date +%Y%m%d)shot_$i.jpg"  ; echo "writing to :  $filenameoutput"  ; scrot    "$filenameoutput" ; echo $i > $HOME/.scrottkrc  </Key>


# flag key as PH
# select pidgin on a specific workspace
<Key mask="PH" key="J">exec:  xdotool search --title  skype    |  while read i ; do     xdotool set_desktop_for_window $i 2 ; xdotool windowraise $i  ; xdotool windowfocus $i   ;  done ; xdotool key "alt+3" </Key>
<Key mask="PH" key="K">exec:  xdotool search --title  pidgin    |  while read i ; do     xdotool set_desktop_for_window $i 2 ; xdotool windowraise $i  ; xdotool windowfocus $i   ;  done ; xdotool key "alt+3" </Key>
# expose effect
<Key mask="PH" key="K">exec: kompose --singleshot </Key>

 
# like under fluxbox
 <Key mask="PH" key="F1">exec: xdotool set_desktop 0</Key>
 <Key mask="PH" key="F2">exec: xdotool set_desktop 1</Key>
 <Key mask="PH" key="F3">exec: xdotool set_desktop 2</Key>
 <Key mask="PH" key="F4">exec: xdotool set_desktop 3</Key>
 <Key mask="PH" key="Left">exec: i=$(xdotool get_desktop) ; z=$(($i - 1)) ; i=$z ; xdotool set_desktop $i  </Key>
 <Key mask="PH" key="Right">exec: i=$(xdotool get_desktop) ; z=$(($i + 1)) ; i=$z ; xdotool set_desktop $i  </Key>
# close to yakuake F12
 <Key mask="PH" key="F10">exec: i=$(xdotool get_desktop) ; z=$(($i - 1)) ; i=$z ; xdotool set_desktop $i</Key>
 <Key mask="PH" key="F11">exec: i=$(xdotool get_desktop) ; z=$(($i + 1)) ; i=$z ; xdotool set_desktop $i</Key>
#  
<Key mask="PH" key="M">minimize</Key>
<Key mask="PH" key="Y">minimize</Key>

<Key mask="PH" key="P">exec:  Esetroot -m $HOME/.wallpaper</Key>
 
# apps
<Key mask="PH" key="L">exec: xscreensaver-command -lock</Key>
<Key mask="PH" key="r">exec: mrxvt </Key>
#<Key mask="PH" key="e">exec: xterm </Key>


#send to right or left the activewindow
<Key mask="PH" key="s">exec: i=$(xdotool get_desktop) ; z=$(($i - 1)) ; i=$z ;   xdotool set_desktop_for_window  $(xdotool getactivewindow) $i  </Key>
<Key mask="PH" key="d">exec: i=$(xdotool get_desktop) ; z=$(($i + 1)) ; i=$z ; xdotool set_desktop_for_window  $(xdotool getactivewindow) $i  </Key> 
<Key mask="PH" key="f">exec: i=$(xdotool get_desktop) ; z=$(($i + 1)) ; i=$z ; xdotool set_desktop_for_window  $(xdotool getactivewindow) 3  </Key>

<Key mask="PH" key="X">exec: i=$(xdotool get_desktop) ; z=$(($i - 1)) ; i=$z ; xdotool set_desktop_for_window  $(xdotool getactivewindow) $i  ;  xdotool set_desktop $i ; xdotool click 1 </Key>
<Key mask="PH" key="C">exec: i=$(xdotool get_desktop) ; z=$(($i + 1)) ; i=$z ; xdotool set_desktop_for_window  $(xdotool getactivewindow) $i ;   xdotool set_desktop $i ; xdotool click 1   </Key>  


# tasks
<Key mask="PH" key="E">exec:  xdotool search --title  mrxvt    |  while read i ; do     xdotool set_desktop_for_window $i 1 ; xdotool windowraise $i  ; xdotool windowfocus $i   ;  done ; xdotool set_desktop 1 ;  xdotool windowfocus $i  </Key>
<Key mask="PH" key="T">exec: sh taskcoach.sh  </Key> 
  
<Key mask="PH" key="space">maximize</Key>

</JWM>



  












```

---

