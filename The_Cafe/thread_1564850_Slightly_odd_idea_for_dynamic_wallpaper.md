---
title: "Slightly odd idea for dynamic wallpaper"
date: 2010-08-31
forum: The Cafe
---

### Post by keithpeter on 2010-08-31
Hello All

Have a look at the archive page for any blog on tumblr.com. You get a dynamic 'snapshot' of the posts as small thumbnail images and text boxes in time order with date headings.

I'm wondering about how I would go about generating a similar snapshot of recently modified files on my PC and displaying it as the wallpaper - with dates but not dynamically linked to the files.

Any ideas? Something really simple like feh/imagemagick and a bash script generating a desktop as the user logs on? I just need pointers to a possible vehicle. 

I'd be using this with jwm and a minimal desktop....

Cheers

---

### Post by DemonBob on 2010-08-31
Conky maybe with a custom LUA, or perl script?

---

### Post by keithpeter on 2010-08-31
> **DemonBob said:**
> Conky maybe with a custom LUA, or perl script?

Thanks DemonBob, that is one I had not thought of. Conky would be listing the directories, and the perl script would be writing thumbnails and text summaries out as a bitmap?

Cheers all

---

### Post by Bölvaður on 2010-08-31
more on this idea.

would you be able to get the cursor's position? Im not familiar with it but I would assume you could get the position through x.

That way you actually could have more interaction with the background, perhaps have some lock to activate you being able to click on items on the background.

---

### Post by keithpeter on 2010-08-31
Hello Bölvaður

That is the ultimate dream, an active desktop that shows the most recent work you have done as a clickable map in some way...

For now, I've been playing with feh and conky along with jwm's configuration file, the first few lines of .jwmrc will give you the idea...

```
<?xml version="1.0"?>
 <JWM>
<StartupCommand>
nm-applet &
conky &
feh --collage  --stretch --thumb-width 300 --thumb-height 300 --limit-width 1400 --limit-height 1050  -b bg-grad.jpg  -O desktop.jpg /home/keith/images
feh --bg-center desktop.jpg
</StartupCommand>
```

I also have conky showing the contents of a text file ('todo.txt') and the names of files modified in the last week in the documents folder, like this

```
TODO
${execi 60 cat /home/keith/todo.txt | grep '^#' -v | tail -5}

CHANGED
${execi 60 find /home/keith/documents -type f -mtime -7 -printf "%f\n"}
```

The overall effect is shown below, I'll be trying for a mock shadow around the conky window to make it look like a sticky note attached to the screen.

---

### Post by Bölvaður on 2010-08-31
You might want to check this out

[URL="brainstorm.ubuntu.com/item/10237/"]brainstorm.ubuntu.com/item/10237/
[/URL]
[people.mozilla.com/~vladimir/demos/photos.svg]("http://people.mozilla.com/~vladimir/demos/photos.svg")

---

### Post by Troublegum on 2010-09-01
> **keithpeter said:**
> Hello All

Have a look at the archive page for any blog on tumblr.com. You get a dynamic 'snapshot' of the posts as small thumbnail images and text boxes in time order with date headings.


Do you have a link? I didn't find this feature.

---

### Post by keithpeter on 2010-09-01
> **Troublegum said:**
> Do you have a link? I didn't find this feature.

Hello Troublegum

It 'appears' as the 'archive' link on Tumblr blogs. My example (old now, not used) is at

[http://blazingfruit.tumblr.com/archive](http://blazingfruit.tumblr.com/archive)

> **Bölvaður said:**
> You might want to check this out

[URL="brainstorm.ubuntu.com/item/10237/"]brainstorm.ubuntu.com/item/10237/
[/URL]
[people.mozilla.com/~vladimir/demos/photos.svg]("http://people.mozilla.com/~vladimir/demos/photos.svg")

Hello Bölvaður

I love that javascript/svg but I had more of a grid/workflow idea in mind for the dream....

I'll be having a look at how they did it though...

---

