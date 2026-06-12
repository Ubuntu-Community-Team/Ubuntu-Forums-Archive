---
title: "post your devilspie config files with screenshot"
date: 2007-09-30
forum: The Cafe
---

### Post by markp1989 on 2007-09-30
im curious to see how versatile devilspie is. and i am looking for ideas for how it can be used, and it may help new users see some of the cool programs there are 

> (if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 4)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "+0+0")
                (geometry "1026x870")
        )
)

i have used mine to put a transparent terminal on the desktop for easy access 

i got this config file from [http://ubuntuforums.org/showthread.php?t=202249&highlight=transparent+terminal+on+desktop](http://ubuntuforums.org/showthread.php?t=202249&highlight=transparent+terminal+on+desktop)

can anyone who uses devilspie post their config files. i will be extremely great full

---

### Post by markp1989 on 2007-09-30
i really like devilspie, and im curious to see how people have put it to use

---

### Post by markp1989 on 2007-09-30
bump

---

### Post by Griffiss on 2007-10-12
I second this request for cool stuff you can do with devilspie.

It looks like it has potential - if only I was some kind of genius or had more knowledge or something....

---

### Post by markp1989 on 2007-10-18
(if
(matches (window_name) "Buddy Ticker")
(begin
(set_workspace 4)
(below)
(undecorate)
(skip_pager)
(skip_tasklist)
(wintype "utility")
(geometry "+0-25")
(geometry "800x10")
)
)


this displays the buddy ticker from pidgen just above my bottom panel, i cannot screen print this because it has my friends email addresses on it

---

### Post by 0okami on 2007-12-30
hmmm... i'd post mine but im having issues getting it moved where i want it...  (screenshot and config here: [http://ubuntuforums.org/showthread.php?t=654080](http://ubuntuforums.org/showthread.php?t=654080) )

---

### Post by Indubitableness on 2009-02-10
I know this thread is old, but here's mine.

   I'm using one which creates a background desktop on my second workspace ayt login, and one which makes a regular console a specific size to match the background picture I put into it.

   On my background console there's a miniscule little space between the left edge of the screen and the beginning of the console's left edge. I don't know how to fix this, i tried changing the lines (geometry +50+50) thinking maybe it would move the first pixel it draws on or something, but it didn't change anything.

  Here are the scripts.

Background Console
> (if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 2)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "+0+0")
                (geometry "1148x824")
        )
)

Regular Console
> (if
        (matches (window_name) "Future")
        (begin
                (below)
                (skip_pager)
                (skip_tasklist)
                (geometry "+50+100")
                (geometry "525x400")
        )
)

  I don't really understand the (gemoetry "+X+X") part does. I'm working under the assumption that it controls where the window is placed when it's rendered, but when I was working with it I changed the numbers between +0 and +500 and it would always open in the same place.

  Anyway, to the screenshots.

---

