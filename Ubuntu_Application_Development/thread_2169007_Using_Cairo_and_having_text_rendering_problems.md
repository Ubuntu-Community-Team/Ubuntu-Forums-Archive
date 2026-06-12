---
title: "Using Cairo and having text rendering problems"
date: 2013-08-20
forum: Ubuntu Application Development
---

### Post by arodulfo on 2013-08-20
Dear all,

I have made a small application in C. It must show the result of some remote measurements reported through ModBus.
The application uses CAIRO in order to have its output done in full graphics mode.
Nowadays, the communications run quite smooth, the graphics rendering need just a little trick to work, that I can live with right now, and I just have a major drawback.
For a system supposed to operate in Spain, not being able to render accents and the "Ñ/ñ" is kind of a disaster.

The problem has two faces:
* If I do nothing to eliminate those characters and replace them by the English equivalents, CAIRO seems to stop working, even if the application keeps sending output to the background console
* The 'º' in 'ºC', which I read from a config file, appears perfect on screen, even though I know it is represented by the sequence 0xE1 - 0xB5 - 0x92. The code reads that sequence out of the config file and stores it on the matching variable and has no problem to render the symbol when I "print " the contents of that variable through CAIRO

My normal coding for "printing" texts through CAIRO looks like:
```

cairo_select_font_face (c, fontName, fontSlant, fontWeight);
cairo_set_font_size (c, fontSize);
cairo_set_source_rgb (c, col.r, col.g, col.b);
cairo_move_to (c, x, y);
cairo_text_path (c, text_to_be_shown);
cairo_fill (c);
cairo_show_page (c);

```

The LANG environment variable is set to es_ES.UTF-8
Other than in CAIRO, I am perfectly able to use Spanish accents, ñ, Ñ, and so on.

I have a second problem: Interfacing with an external configuration application.
This application is said to use ModBus to talk to the resident application. So, all coding must match the coding in the resident application so that it accepts and applies the new settings without errors or hangouts.

Any hint?

---

### Post by arodulfo on 2013-08-29
Dear all,

After reading a lot and having help from many, I have concluded I was mis-using cairo. Short explanation follows.

CAIRO is an exclusive UTF8 shop. This means that it will flawlessly work as long as you keep by the UTF8 standard and rules.
It means that, when it comes to string processing, the strings will have some additional coding and you will have to rely on other methods to deal with the space a given string occupies in the screen.


Even if they say the in-CAIRO text tools are kind of a toy, its capabilities are more than enough for a simple application like mine.
CAIRO has tools to help assess the space a given UTF8 string will need in the screen, so that was all I needed to use, on top of respecting UTF8 rules.
I just need to show some texts, allways the same texts (once the display is configured), around a couple of boxes with numbers inside.

I needed some simple (simple?) way to add graphic capabilities to a C-based application and it is doing just that.
Thanks a lot to all the people lending a helping hand. GREAT!!!!

---

### Post by andrewkrieg on 2013-10-05
From what I read you are still looking for a simple graphics library? If you are, check out SFML, it's nice and light-weight, but is still very powerful and cross-platform. It also has text rendering ;) along with OpenGL support, and classes for networking, sound, and video.

Good Luck Mate!

---

