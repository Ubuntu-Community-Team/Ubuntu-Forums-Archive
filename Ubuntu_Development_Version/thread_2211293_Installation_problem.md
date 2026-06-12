---
title: "Installation problem"
date: 2014-03-15
forum: Ubuntu Development Version
---

### Post by 23dornot23d on 2014-03-15
When trying to install a fresh Ubuntu 14.04 or any version for that matter

This problem often arises for Users.

640 x 480 resolution ..........



______________________________

But if the right monitor settings came up and buttons were available to click to rectify this

Then a user would not just dump it and think its a toy or actually works at this resolution

But would set it up for their own system ........

______________________________

Installing Ubuntu becomes impossible when the computer detects 640 x 480

Although the user could try changing the resolution - all the buttons needed are off the screen at
this size though ..... could the developers consider having a accept button for resolution somewhere
in the view .......... ( at the moment its guess work to get to the accept button which is off screen )

You cannot do a install at 640 x 480 ....... for similar reasons and people must have come across this
many times ........ but then must either give up or think the developers never thought it through as
to how someone can make a alternative install in this situation when their setup is well capable of
running Ubuntu ........ 

I have 3 screens attached here TV Computer and VGA monitor ........ non allow me a install .........
as things go off screen ........ and no where in the installation do I get a chance to set them up
any different to what the computer detects ........ which is 640 x 480 resolution.

Thoughts ?

[COLOR=#ff0000][B]By the way even though edid information is available for the 40 inch TV
the way Ubuntu detects it - it thinks its a 7 inch display !!!![/B][/COLOR]

[IMG]http://i.minus.com/ioa7EyYI2CjXF.gif[/IMG]

---

### Post by grahammechanical on 2014-03-15
This virtual Ubuntu Developer Summit discussion is not exactly dealing with your problem but a related one.

> [COLOR=#333333][FONT=Ubuntu Beta]On monitors with a high pixel density, we need everything to be rendered larger so that it's legible. The unity team has a plan to address the desktop aspects of this for 14.04, but that leaves the grub boot menu and the plymouth splash screen unscaled. Identify the work that needs to be done for this.[/FONT][/COLOR]

[http://summit.ubuntu.com/uds-1403/meeting/22157/core-1403-hidpi-boottime/](http://summit.ubuntu.com/uds-1403/meeting/22157/core-1403-hidpi-boottime/)

You will see just how difficult it is to give multi-monitor users some control over scaling to fit more than one monitor. Part of the problem is with OEMs not being accurate with the information in the EDID.

I ask: Should we even attempt to install Ubuntu with more than one monitor connected? Is it asking too much of the Installer program?

Oh, by the way. In an earlier post you wondered why a screenshot was showing three screens when you only had two screens. But in this post you have 3 screens: Laptop; TV/Monitor; and VGA monitor. Earlier post solved?

Regards.

---

### Post by 23dornot23d on 2014-03-15
The other one is my main computer I use it on the night time ....... but both are connected to TV screens as I find these serve the purpose ..... large enough to see from a distance and also giving out enough heat to keep me warm in winter time ;)

I actually only have this one connected via VGA and for the life of me cannot get both the TV and VGA to work
as I want on this one  .......... but I do not need to make problems up .........

I have enough and wish that the monitors one was a simple one to solve ....... 

( I like the way you think though - minimise the problems - that is what I always try to do 

This is why I believe it would be a help to let the user decide or confirm *(what is right or wrong) - when all else seems to fail ...... 
sometimes users can work if they have 1 or 2 screens plugged into their computer .......... one in the VGA and one into the HDMI ( on my daytime setup ) & ( one connected via HDMI on my night time setup ) ......... 

but when they do not pick up correctly - the computer carries on setting things at 640 x 480 regardless of wherther or not its possible to install
at this resolution as most things end up off screen - and the windows will not shrink or move up - to see what is below * ( so a install at this resolution is impossible to do ).

Isolate what is going wrong ....... then give an answer that can rectify a problem ...... 

The one that I tried to give above is to either make the accept button appear in a place where the user can get to it so screen sizes can be changed ........ at least that way the user can change the resolution themselves to one that is workable. 


or


* ( The other may be to add it into the install - but I know how the devs think ..... only the computer can choose as users make mistakes and the automatic configuration of the computer never does make mistakes )

That is why my 40 inch TV is being reported as a 7 inch monitor ........ and I being a user would not know that 
this is wrong ...... so it would be stupid to have anything asking me if its correct in the install procedure.

Also when it tells me I have 3 monitors - I could not count or see that there are only 2 visible to me ..........

Larger Text - that is what we old folks need ....... keep working on that one .........

_________________________________________________________________

By the way

I would not try to attempt to make you think that the picture I showed of 3 screens 
was actually of 3 screens as that would not be a problem - but when only one HDMI cable is
plugged in it makes me wonder if some micro-switch is in the VGA and stuck or some other 
thing that for the life of me I cannot fathom how 3 monitor screens show when only 2 could possibly
show.

 

This is not the case on the Asus - therefore I posted to show 3 monitors were showing on a screenshot - when only one HDMI cable is plugged in connecting it to the TV ......... no VGA plugged in at all on that one.

_____________________________________________________

The computer I am on now typing this out is a dual core Acer Aspire ....... which is connected to both a TV (through HDMI) and to a monitor (through VGA) and for the life of me this too is giving me problems ....

I usually only give comments to help people sort things out ........ 

I run Ubuntu - Arch - Fedora - Wayland on KDE RB - Mint - Ultimate Edition 4.0 and 5 versions of the 14.04 Testing on different kernels plus many of the back versions of Ubuntu - also Knoppix Kanotix  etc ( most are set up with different Display Managers - LXDE - XFCE - Enlightenment - KDE - Ubuntu Unity - Gnome-Shell etc .... )

All the choices lead me to have a good feel - about how each one can perform - also knowing how the installers work for all of them and which work better than others ....... 

But If I think of improvements because I go through so many installs
then I will try to tell the people that can change the way they work .......

Save me having to use workarounds all the time ....... and the many users that have to do what the computer
could easily accomplish - just by asking for them to confirm certain things along the way.

Like a list of attached monitors the computer thinks I have 
*( my response is only a yes/no to each one ) .... the computer says no

Can my TV screen display work in a better mode than 640 x 480 ( can I change this ) 

EDID information for the TV it reports back .......

```

Display Device 2 (DFP-1):
     EDID Name             : ORN ORION
     Minimum HorizSync     : 14.000 kHz
     Maximum HorizSync     : 46.000 kHz
     Minimum VertRefresh   : 47 Hz
     Maximum VertRefresh   : 61 Hz
     Maximum PixelClock    : 80.000 MHz
     Maximum Width         : 1920 pixels
     Maximum Height        : 1080 pixels
     Preferred Width       : 1280 pixels
     Preferred Height      : 720 pixels
     Preferred VertRefresh : 50 Hz
     Physical Width        : 160 mm
     Physical Height       : 90 mm                              

```

....... [COLOR=#ff0000]**the computer says no**[/COLOR]

There needs to be a compromise somewhere between how much automation you can build into a process.

But I do see why it is being done ......... but if it is reported back to the User for them to check at the end
of the process ....... then that to me is a start.

The VGA EDID information these being on the Acer Aspire laptop which has both VGA and HDMI ......

```

GPU #0:
    Name      : GeForce 9300M GS
    PCI BusID : PCI:1:0:0
  
    Number of Display Devices: 3
  
    Display Device 0 (CRT-0):
       EDID Name             : LG W1946
       Minimum HorizSync     : 30.000 kHz
       Maximum HorizSync     : 61.000 kHz
       Minimum VertRefresh   : 56 Hz
       Maximum VertRefresh   : 75 Hz
       Maximum PixelClock    : 90.000 MHz
       Maximum Width         : 1360 pixels
       Maximum Height        : 768 pixels
       Preferred Width       : 1360 pixels
       Preferred Height      : 768 pixels
       Preferred VertRefresh : 60 Hz
       Physical Width        : 410 mm
       Physical Height       : 230 mm                              

The laptop monitor information for EDID .... is below 

Display Device 1 (DFP-0):
     EDID Name             : AUO
     Minimum HorizSync     : 54.715 kHz
     Maximum HorizSync     : 54.715 kHz
     Minimum VertRefresh   : 60 Hz
     Maximum VertRefresh   : 60 Hz
     Maximum PixelClock    : 96.300 MHz
     Maximum Width         : 1440 pixels
     Maximum Height        : 900 pixels
     Preferred Width       : 1440 pixels
     Preferred Height      : 900 pixels
     Preferred VertRefresh : 60 Hz
     Physical Width        : 370 mm
     Physical Height       : 230 mm

```

So ......

> 
Ubuntu in 2 more years time ....... ( would feed back and a database - help the developers to set the screens up )

Say that when Users rectified things it was sent back to them ........ electronically ...... like the bug reports.


And what is the 5 year plan most big business's have them ..... or will desktops and monitors not be around then.

_______________________________________________________________

I will have a good look at the conference you mention - thank you for the information.

Not sure what an easier way is though than asking a User to confirm some things at the end
or if they cannot be bothered - just to skip it and allow the computer to choose as it does now.

```

18 : 42 minutes into the font scaling problems ........ he says exactly what I expected ..........

http://www.youtube.com/watch?v=1pn79l6NKuc&feature=share&t=18m

[http://www.youtube.com/watch?v=1pn79l6NKuc&feature=share&t=18m]("http://www.youtube.com/watch?v=1pn79l6NKuc&feature=share&t=19m")


```

"If we need user input then we are doing something wrong"

The thing is at the start someone said that the **Edid information** or information the computer recieves from X
could be suspect ........ or to put it as he says - it lies to the computer ( a 6 foot wide monitor ).


Which to me says at some point - you have to ask the user to confirm things ......... or at least give them
one small program that will allow them to go in and adjust major things ........ like Screen sizes and the 
percentage size of TEXT relative to the overall screen height - obviously when this is 50% of the height of the
screen it is not right.

Most screens the height of text relative to the height of the screen is the thing that matters ........ the relationship 
needs to be set via variables ....... ( dpi and everything else needs calculating but as a percentage to the height of the
screen - which obviously needs to be reported back correctly ......... by either the computer or the USer )

---

