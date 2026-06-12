---
title: "How to make joystick completely worked"
date: 2009-06-15
forum: Wine
---

### Post by uranus0206 on 2009-06-15
Hi all! I have a gamepad named Logitech Dual Action

It worked perfect in Ubuntu9.04. And worked in wine FIFA soccer game.

But it has a little problem that I can't use reghit analog in the game.

It means i can't make some special move in game.

I follew the instruction:

      +-DirectInput
      |  |
      |  +->MouseWarpOverride
      |  |   [Override default mouse pointer warping behavior:
      |  |    enable:  (default) warp pointer when mouse exclusively acquired
      |  |    disable: never warp the mouse pointer
      |  |    force:   always warp the pointer]
      |  |
      |  +->*<joystick name> = <axes mapping>
      |      [Linux only (js* devices). This maps axes of joystick "joystick name". The "axes mapping" is
      |       comma-separated list of "axis type"s - one for each joystick axis (hat-pov uses 2 axes).
      |       "axis type" is one of: X, Y, Z, Rx, Ry, Rz, Slider1, Slider2, POV1, POV2, POV3, POV4.
      |       To find the joystick name run
      |       'WINEDEBUG=+dinput wine program.exe 2>&1 | grep joydev_enum_device'
      |       Example: "Logitech Logitech Dual Action"="X,Y,Rz,Slider1,POV1". (two "Logitech"s not a typo)]

maybe i misunderstood that 

I created a subfolder named DirectInput under 

[HKEY_CURRENT_USER]\Software\Wine\

And then i created a string value named Logitech Logitech Dual Action 

and the value is X,Y,Rz,Slider1,POV1

after that i still can't use right analog in game, am i wrong?

---

### Post by uranus0206 on 2009-06-16
well, i have do some test.

i use joystick test software like xpadder, and i got the right analog stick info

thus i changed the axismapping value to "X,Y,Z,Rz,POV1"

and then i use joytester, another windows software, then the result worked!!!

but i still can't play game with my right analog stick......is the problem of the

FIFA game?

---

### Post by uranus0206 on 2009-06-18
well, i cahnged the axis mapping to "X,Y,POV1,POV2"

and the right analog stick worked in the game menu.......

but I still cannot use that in game..

why donsent the game recognize Z axis and Rz axis?

---

### Post by uranus0206 on 2009-06-24
OK! Now i finally find where the problem is! And it's simple to solve!

I find the fifa game will regard my "Logitech Dual Action" joystick as the 

"Default" joystick.

That's why i can't use right analog stick even i change mapping in regedit

Now the solution is just modify some contents in the installed game folder 

called (FIFA08 for example in the windows browser view):

[color=red]C:\Program Files\EA Sports\FIFA 08\deta\input\devdata.dat[/color]

just edit this file with editor such as gedit, notepad(wine)...

and search "Logitech Dual Action" in the content, like this

[IMG]http://lh5.ggpht.com/_TnX1PrvXerM/SkHJLCEHaDI/AAAAAAAAC7M/tsVlDeqV0GA/s800/devdata-dual%20action.jpg[/IMG]

and then copy all the mapping values below this subject.

Then search "Default", and paste what you copy to  replace all the content 

but remain the title of gampad name.

[IMG]http://lh6.ggpht.com/_TnX1PrvXerM/SkHJLLwokYI/AAAAAAAAC7I/0Q54S9gh_Zw/s800/devdata-default.jpg[/IMG]

and  then copy this file to ~/FIFA 08/user/

now i can play with whole function in game!

PS:maybe it will work with others non Logitech gamepad...

---

