---
title: "Change font color"
date: 2008-10-03
forum: Server Platforms
---

### Post by Jloser on 2008-10-03
How do I modify the color of the text displayed in console?

It is a dull gray color, and I want it to be white... maybe even play around with some reds.

I tried setterm, but nothing happened.

---

### Post by mbeach on 2008-10-04
I'd say setterm is the proper utility to use at the console (no gui).  What did you try?  I will say that it doesn't seem to 'stick'.  I tried a 'setterm -foreground green' which changes the text colour to green but after a "ls" it goes back to the default.  Not sure of any other way to change it.  I'm sure if you are using putty or whatever to remotely access the machine there are settings, and if you are using the terminal inside a window.

---

### Post by Jloser on 2008-10-04
i tried
```
setterm -foreground yellow
```

I also tried with sudo, but nothing changed.  Any ideas?

---

### Post by itfell on 2008-10-05
> **mbeach said:**
> I'd say setterm is the proper utility to use at the console (no gui).  What did you try?  I will say that it doesn't seem to 'stick'.  I tried a 'setterm -foreground green' which changes the text colour to green but after a "ls" it goes back to the default.  Not sure of any other way to change it.  I'm sure if you are using putty or whatever to remotely access the machine there are settings, and if you are using the terminal inside a window.

mbeach, after changing your color try using the command: setterm -store








....on a side note i cannot seem to get setterm to change the colors on my terminals either.....any updates?

---

### Post by itfell on 2008-10-05
p.s. i also noticed that the setterm command WILL change the colors when your are in a text terminal (accessed via Ctrl+Alt+F1..F2..F3, etc.), but when using the terminal opened within your respective GUI it tends to follow the color scheme in your "Appearance Preferences"

---

### Post by mbeach on 2008-10-05
yes, the -store flag worked.  Neat.  Not that I'm too often in the console in that fashion though (CTRL+ALT+F2...).  The increased fontsize/lower resolution is soothing on my aging eyes though.

---

### Post by cariboo on 2008-10-05
If you are using a gnome-terminall just right click anywhere in the terminal and select Profiles-->Profile Preferences. See the screenshot of my terminal.

Note: I zoomed it a couple of times for clarity

Jim

---

### Post by itfell on 2008-10-05
> **cariboo907 said:**
> If you are using a gnome-terminall just right click anywhere in the terminal and select Profiles-->Profile Preferences. See the screenshot of my terminal.

Note: I zoomed it a couple of times for clarity

Jim

very interesting...thank you

---

### Post by ssammy on 2009-03-17
[http://www.blowyouros.com/2008/09/how-to-change-the-way-your-terminal-looks-in-ubuntu-server/](http://www.blowyouros.com/2008/09/how-to-change-the-way-your-terminal-looks-in-ubuntu-server/)

---

