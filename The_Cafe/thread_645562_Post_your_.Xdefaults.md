---
title: "Post your .Xdefaults"
date: 2007-12-20
forum: The Cafe
---

### Post by m0rphex on 2007-12-20
I'm trying to find nice .Xdefaults settings that would please my eye. It would be nice to see what other people have :)

---

### Post by fedex1993 on 2007-12-20
i dont think many people have .Xdefaults most people use .Xdefualts for urxvt thats the only place that i have seen people use them

---

### Post by ~LoKe on 2007-12-20
Here you go:
```
*background:  #333333
*foreground:  #efefcf
!Colors
! Black
*color0:      #5A5A5A
*color8:      #3e3e3e
! Red
*color1:      #FF4747
*color9:      #FF6767
! Green
*color2:      #AFC81C
*color10:     #bFC81C
! Yellow
*color3:      #FDD338
*color11:     #F4D461
! Blue
*color4:      #619AF4
*color12:     #5496FF
! Purple
*color5:      #5F5A90
*color13:     #826AB1
! Cyan
*color6:      #47E0FF
*color14:     #2ED9FB
! White
*color7:      #FFFFFF
*color15:     #DEDEDE



!Xft settings
Xft.dpi:                96
Xft.hinting:            1
Xft.hintstyle:          hintfull
Xft.antialias:          1 
Xft.rgba:               rgb


!URxvt settings
URxvt.urlLauncher:      firefox
urxvt*font: 		xft:Bitstream Vera Sans Mono:pixelsize=9
URxvt*boldFont:		xft:Bitstream Vera Sans Mono:pixelsize=9
URxvt*italicFont:	xft:segoe ui:pixelsize=9
URxvt*bolditalicFont:	xft:Bitstream Vera Sans Mono:pixelsize=9
URxvt*scrollBar:	false
URxvt*internalBorder:	6

!URxvt.background:	#333333
URxvt.foreground:	#ffffff
!URxvt.termName:           string
!URxvt.geometry:           128x64
!URxvt.reverseVideo:       boolean
!URxvt.loginShell:         boolean
!URxvt.jumpScroll:         boolean
!URxvt.skipScroll:         boolean
!URxvt.pastableTabs:       boolean
!URxvt.scrollstyle:        mode
!URxvt.scrollBar_right:    boolean
!URxvt.scrollBar_floating: boolean
!URxvt.scrollBar_align:    mode
!URxvt.thickness:          number
!URxvt.scrollTtyOutput:    boolean
!URxvt.scrollTtyKeypress:  boolean
!URxvt.scrollWithBuffer:   boolean
URxvt.inheritPixmap:      true
URxvt.transparent:        true
!URxvt.tintColor:          #333333
!URxvt.shading:            10
!URxvt.fading:             50
!URxvt.fadeColor:          #222222
!URxvt.utmpInhibit:        boolean
URxvt.urgentOnBell:       true
!URxvt.visualBell:         boolean
!URxvt.mapAlert:           boolean
!URxvt.meta8:              boolean
URxvt.mouseWheelScrollPage:   True
!URxvt.tripleclickwords:   boolean
!URxvt.insecure:           boolean
!URxvt.cursorUnderline:    boolean
URxvt.cursorBlink:        true
!URxvt.pointerBlank:       boolean
!URxvt.colorBD:            color
!URxvt.colorIT:            color
!URxvt.colorUL:            color
!URxvt.colorRV:            color
!URxvt.underlineColor:     color
!URxvt.scrollColor:        color
!URxvt.troughColor:        color
!URxvt.highlightColor:     color
URxvt.cursorColor:        #afc81c
!URxvt.cursorColor2:       color
URxvt.pointerColor:       #afc81c
!URxvt.pointerColor2:      color
!URxvt.borderColor:        color
!URxvt.intensityStyles:    boolean
!URxvt.inputMethod:        name
!URxvt.preeditType:        style
!URxvt.imLocale:           string
!URxvt.imFont:             fontname
!URxvt.title:               URxvt
!URxvt.iconName:           string
!URxvt.saveLines:          number
!URxvt.depth:              number
!URxvt.transient-for:      windowid
!URxvt.override-redirect:  boolean
!URxvt.hold:               boolean
!URxvt.externalBorder:     number
!URxvt.internalBorder:     number
URxvt.borderLess:         true
!URxvt.skipBuiltinGlyphs:  boolean
!URxvt.lineSpace:          number
!URxvt.pointerBlankDelay:  number
!URxvt.backspacekey:       string
!URxvt.deletekey:          string
!URxvt.selectstyle:        mode
!URxvt.print-pipe:         string
!URxvt.modifier:           modifier
!URxvt.cutchars:           string
!URxvt.answerbackString:   string
!URxvt.secondaryScreen:    boolean
!URxvt.secondaryScroll:    boolean
!URxvt.perl-lib:           string
!URxvt.perl-eval:          perl-eval
!URxvt.perl-ext-common:    string
!URxvt.perl-ext:           string
!URxvt.iso14755_52:        boolean
!URxvt*keysym.sym:         keysym

!xterm settings
xterm*dynamicColors:    true
!xterm*utf8:             2
xterm*eightBitInput:    true
xterm*saveLines:        32767
xterm*scrollTtyKeypress:true
xterm*scrollTtyOutput:  false
xterm*scrollBar:        false
xterm*loginShell:       true
xterm*faceName:         Bitstream Vera Sans Mono:pixelsize=10
xterm*jumpScroll:       true
xterm*multiScroll:      true
xterm*toolBar:          false


Xcursor.theme: Shere_Khan_Black_Hand
Xcursor.size: 12
```

---

### Post by urukrama on 2007-12-20
Here is mine. Not much to see.

> xcalc*geometry: 200x275
xcalc.ti.bevel.background: #111111
xcalc.ti.bevel.screen.background: #D6D7C
xcalc.ti.bevel.screen.DEG.background: #D6D7C
xcalc.ti.bevel.screen.DEG.foreground: Black
xcalc.ti.bevel.screen.GRAD.background: #D6D7C
xcalc.ti.bevel.screen.GRAD.foreground: Black
xcalc.ti.bevel.screen.RAD.background: #D6D7C
xcalc.ti.bevel.screen.RAD.foreground: Black
xcalc.ti.bevel.screen.INV.background: #D6D7C
xcalc.ti.bevel.screen.INV.foreground: Red
xcalc.ti.bevel.screen.LCD.background: #D6D7C2
xcalc.ti.bevel.screen.LCD.foreground: Black
xcalc.ti.bevel.screen.LCD.shadowWidth: 1
xcalc.ti.bevel.screen.M.background: #D6D7C
xcalc.ti.bevel.screen.M.foreground: Black
xcalc.ti.bevel.screen.P.background: #D6D7C
xcalc.ti.bevel.screen.P.foreground: Black
xcalc.ti.Command.foreground: Black
xcalc.ti.Command.background: #BFC0A3
xcalc.ti.button5.background: #BFC0A3
xcalc.ti.button20.background: #BFC0A3
xcalc.ti.button25.background: #BFC0A3
xcalc.ti.button30.background: #BFC0A3
xcalc.ti.button35.background: #BFC0A3
xcalc.ti.button40.background: #BFC0A3
xcalc.ti.button22.background: #D6D7C2
xcalc.ti.button23.background: #D6D7C2
xcalc.ti.button24.background: #D6D7C2
xcalc.ti.button27.background: #D6D7C2
xcalc.ti.button28.background: #D6D7C2
xcalc.ti.button29.background: #D6D7C2
xcalc.ti.button32.background: #D6D7C2
xcalc.ti.button33.background: #D6D7C2
xcalc.ti.button34.background: #D6D7C2
xcalc.ti.button37.background: #D6D7C2
XCalc*Cursor:                 hand2
XCalc*ShapeStyle:             rectangle

lal*color: #9897c7
lal*font: Brassfield
lal*fontsize: 13
lal*format:%H:%M

---

### Post by grte on 2007-12-20
```
!
!#########################################
!
!	Xcursor.config
!
Xcursor*theme:			Vanilla-DMZ

! #########################################
!
! 	Xterm config
!
XTerm*jumpScroll:		true
XTerm*multiScroll:		true


! #########################################
!
!	URxvt config
!
urxvt*background:		black
urxvt*foreground:		white
urxvt*fading:   		10
urxvt*tintColor: 		#000000
urxvt*shading:   		25
urxvt*inheritPixmap: 		true
urxvt*scrollBar: 		false
urxvt*title: 			Terminal
urxvt*termName: 		rxvt-unicode
urxvt*scrollTtyKeypress:    	true
urxvt*scrollTtyOutput:      	false
urxvt*scrollWithBuffer:     	false
urxvt*perl-lib:		/usr/lib/urxvt/perl
urxvt*perl-ext-common:		default,matcher
urxvt*urlLauncher:		firefox
urxvt*matcher.button:		1
urxvt*scrollstyle:      	plain
urxvt*secondaryScroll:  	true
urxvt*cutchars: 		`"'&()urxvt*,;<=>?@[]{|}$`
urxvt*font: 			xft:Terminus:pixelsize=11:antialias=true:hinting=true
urxvt*boldFont: 		xft:Terminus:pixelsize=11:antialias=true:bold:hinting=true
urxvt*italicFont: 		xft:Terminus:pixelsize=11:antialias=true:italic:autohint=true:hinting=true
urxvt*bolditalicFont: 		xft:Terminus:pixelsize=11:antialias=true:bold:italic:autohint=true:hinting=true
urxvt*iconName:			rxvt-unicode

! #########################################
!
!	Urxvt Colours
!
! Black
urxvt*color0:      #131212
urxvt*color8:      #474747
! Red
urxvt*color1:      #803232
urxvt*color9:      #982B2B
! Green
urxvt*color2:      #1cc600
urxvt*color10:     #89B83F
! Yellow
urxvt*color3:      #AA9943
urxvt*color11:     #EFEF60
! Blue
urxvt*color4:      #65abe1
urxvt*color12:     #2299ff
! Purple
urxvt*color5:      #5F5A90
urxvt*color13:     #826AB1
! Cyan
urxvt*color6:      #92B19E
urxvt*color14:     #A1CDCD
! White
urxvt*color7:      #FFFFFF
urxvt*color15:     #DEDEDE

! ########################################
!
! 	Yeahconsole.config
!
yeahconsole*restart:		1
yeahconsole*toggleKey:		None+F12
yeahconsole*background:  	black
yeahconsole*foreground: 	white
yeahconsole*loginShell:	True
yeahconsole*consoleHeight: 	25
yeahconsole*stepSize:		5
yeahconsole*aniDelay:		3 
yeahconsole*handleWidth:	2
yeahconsole*handleColor:	#ed0505
yeahconsole*term:		urxvtc
yeahconsole*scrollBar: 	false
yeahconsole*reverseVideo: 	false
yeahconsole*tintColor: 	#000000
yeahconsole*inheritPixmap: 	true
yeahconsole*shading:		25
yeahconsole*saveLines: 	10000
yeahconsole*cursorBlink: 	true
yeahconsole*font: 		xft:Terminus:pixelsize=11:antialias=true:hinting=true

! #########################################
!
!	Yeahconsole Colours
!
! Black
yeahconsole*color0:      #131212
yeahconsole*color8:      #474747
! Red
yeahconsole*color1:      #803232
yeahconsole*color9:      #982B2B
! Green
yeahconsole*color2:      #5B762F
yeahconsole*color10:     #89B83F
! Yellow
yeahconsole*color3:      #AA9943
yeahconsole*color11:     #EFEF60
! Blue
yeahconsole*color4:      #227799
yeahconsole*color12:     #2299ff
! Purple
yeahconsole*color5:      #5F5A90
yeahconsole*color13:     #826AB1
! Cyan
yeahconsole*color6:      #92B19E
yeahconsole*color14:     #A1CDCD
! White
yeahconsole*color7:      #FFFFFF
yeahconsole*color15:     #DEDEDE

! Xft
Xft*dpi:		100
Xft*antialias:		true
```

---

### Post by m0rphex on 2007-12-21
Thank you very much! ~LoKe yours was nice :D

---

### Post by fedex1993 on 2007-12-21
so what is exactly .Xdefaults used for i only seen people use them in like 3 programs urxvt and xterm hmmm there has to be more people out there with cool .Xdefaults hmm

---

### Post by jis on 2007-12-30
Is it possible to configure it in .Xdefaults?

---

### Post by bonzodog on 2008-04-13
*bump*

Come on people, there HAS to be some more interesting ones out there.

---

### Post by detgar on 2008-04-13
> **fedex1993 said:**
> so what is exactly .Xdefaults used for i only seen people use them in like 3 programs urxvt and xterm hmmm there has to be more people out there with cool .Xdefaults hmm

~/.Xdefaults is a file containing settings for programs used in X (your graphical user interface). If you're a fan of Gnome or KDE you'll probably not care about xdefaults too much, since they both have other ways of letting the user configure their programs.
But if you're a fan of lighter stuff like OpenBox etc. you'll certainly find it useful.

---

### Post by afrodeity on 2010-11-12
anyone know a better way to reload yeahconsole? All I could come up was 

```

killall xterm
```

followed by Alt-F2 yeahconsole

---

