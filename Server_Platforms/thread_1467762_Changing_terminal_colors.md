---
title: "Changing terminal colors"
date: 2010-05-01
forum: Server Platforms
---

### Post by Josh K on 2010-05-01
I need to change the default color scheme in Ubuntu's terminal. Or at least turn the colors completely off because this lime green hilight / light blue text is killing my eyes.

---

### Post by orengolan on 2010-05-01
I assume you are talking about xterm.
first let's make sure that this is the case since that's what I use.
type ```
env|grep TERM
```

the first line should tell you. mine is this:
```
TERM=xterm
```

After you verify this let's change the colors to be very pleasing on your eyes. if it doesn't exist, create a file in your home directory called .Xdefaults:
```
*background:  #000000
*foreground:  #b5b0ad
! Black
*color0:      #131313
*color8:      #555753
! Red
*color1:      #cd7171
*color9:      #e89393
! Green
*color2:      #9ece9e
*color10:     #c4edc4
! Yellow
*color3:      #dfaf8f
*color11:     #f0dfaf
! Blue
*color4:      #6c8b9c
*color12:     #84a8bc
! Magenta
*color5:      #ad7fa8
*color13:     #dc8cc3
! Cyan
*color6:      #8cd0d3
*color14:     #81eaee
! White
*color7:      #bbbbbb
*color15:     #c6c6c6
```

save it. we are almost done.
all we have to do is to run this command ```
xrdb ~/.Xdefaults
```
and open new terminal and you should see black background and gray text.
also, the colors of different folders and file types will be less bright.

feel free to change the colors if you don't like them.

---

