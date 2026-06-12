---
title: "Gnome Theme Creator"
date: 2010-01-21
forum: The Cafe
---

### Post by dilomo on 2010-01-21
Would you like to have such a program? Would you use it? Would you use it if it's payed (~$1-$2) or only of it's free? 

A mockup is attached.

[B]This is example of what would a theme creator look like. The basic principles are these:

1. You edit(create) a svg template (much like the single canvas workflow for icons in Breath) that contains all images needed for a theme.

2. You set up some more options of the theme.

3. Export as pixbuf theme (or css in the future)

What do you think? Is this worth implementing? It is possible to do it right now but I need a wider discussion about it beforehand.[/B]

---

### Post by nilarimogard on 2010-01-21
I would definitely use it, but wouldn't pay for it. I got used to not paying since I left Windows. Also, it would be nice if it was open source too.

---

### Post by spupy on 2010-01-21
This will work for the base stuff, like fonts, sizes and colors. Unfortunately, the finer details of a theme are dependent on the theme engine. Each theme engine (clearlook, aruro, murrine, etc) may have it's own options, which are incompatible and not present in other engines. For example, the murrine engine has its own configurator, but it doesn't work for other themes.

---

### Post by dj mbuso on 2010-01-21
I will prefer to test it first

---

### Post by Giant Speck on 2010-01-21
The only way I can see this working would be for a solely pixmap theme, and even then, it would be extremely complicated to use because there are so many different pixmaps you have to make.

---

### Post by pwnst*r on 2010-01-21
> **nilarimogard said:**
> I would definitely use it, but wouldn't pay for it. I got used to not paying since I left Windows. Also, it would be nice if it was open source too.

Come ON, it's $1 or $2 bucks.  How cheap can you be?

---

### Post by Giant Speck on 2010-01-21
> **pwnst*r said:**
> Come ON, it's $1 or $2 bucks.  How cheap can you be?
Being forced to pay for software is a human rights violation.

---

### Post by dilomo on 2010-01-21
> **Giant Speck said:**
> The only way I can see this working would be for a solely pixmap theme, and even then, it would be extremely complicated to use because there are so many different pixmaps you have to make.

It is exclusively for pixbuf theme engine because it uses svg template with lots of images. In the future it will support exporting as css theme as long as the[ development]("http://ankere.wordpress.com/2009/12/17/css-theme-engine-work-terminated/") continues. Moreover I can't see why ppl don't like pixbif. It is as fast as others (but compared to the eyecandy you get from aurora for example not mist)

I have seen such a template and even worked on it and I can confirm it is not so complicated plus all your gradients and shapes are usable by all widgets. It is also possible to define borders in the svg so the only thing a theme designer should do is make beautiful template - and export it to theme via the program.

---

### Post by pwnst*r on 2010-01-21
> **Giant Speck said:**
> Being forced to pay for software is a human rights violation.

Oh, you *had* to go there, didn't you?

---

### Post by Queue29 on 2010-01-21
> **Giant Speck said:**
> Being forced to pay for software is a human rights violation.

..because?

So you think the developer who puts in 100 hours to make this app deserves to die? And his family to go into poverty?

If anything, *not* paying for software is a human rights violation.

---

### Post by pwnst*r on 2010-01-21
> **Queue29 said:**
> ..because?

So you think the developer who puts in 100 hours to make this app deserves to die? And his family to go into poverty?

If anything, *not* paying for software is a human rights violation.

[img]http://i47.tinypic.com/21ai7vl.gif[/img]

---

### Post by Giant Speck on 2010-01-21
> **pwnst*r said:**
> [IMG]http://i47.tinypic.com/21ai7vl.gif[/IMG]

As soon as I saw the post you quoted, I immediately thought of what picture you were going to post in response.

I was expecting a different picture, though.  :(

---

### Post by k64 on 2010-01-21
Where's the "don't know what it is" option?

---

### Post by pwnst*r on 2010-01-21
> **Giant Speck said:**
> As soon as I saw the post you quoted, I immediately thought of what picture you were going to post in response.

I was expecting a different picture, though.  :(

I figured you would have been bored of that one. But it's funny how many still never got it.

---

### Post by dilomo on 2010-01-21
> **k64 said:**
> Where's the "don't know what it is" option?


In that case you ask as you did :)

This is a program that will allow designers to make Gnome themes right into the vector editor (a.k.a Inkscape) they are familiar with and let the program convert their work into a theme that meets the requirements for themeing and is proven to work on all Gnome desktops. Right now they have to learn a lot of usless details about the internals of GTK widgets and the way they work and write ~ 5000 lines of code in order to get this working right for all apps. 

So in in two words this app is : **BIG relief **that lets you put more time into designing themes rather than coding them to work.

---

### Post by Queue29 on 2010-01-21
> **dilomo said:**
> ines of code in order to get this working right for all apps. 

So in in two words this app is : **BIG relief **that lets you put more time into designing themes rather than coding them to work.

But God forbid the developers get compensated for their efforts, amiright, Giant Speck?

---

### Post by Jameshardy88 on 2010-01-23
I would love to see this come to fruition. I already make pixmap themes quite frequently but am FAR from an expert, even the reasonably minimal knowledge i have required over my time creating themes has been hard to come by, time consuming and largely gleaned through trial and error. I feel an app like this would attract a great deal more themers that at current lack the considerable time and or motivation to give it a go. Even for myself personally, this would probably save me considerable time and effort in creating future themes. I strongly urge you to give creating this some serious thought. I have no doubt that a well crafted app would drastically improve not only the quantity of themes available but also with time the quality as well. Particularly if this a free/cheap app as proposed.

---

### Post by dilomo on 2010-01-23
Thanks for the feedback Jameshardy88! I will have some more research and talks with some pro gtk developers to see if there is something that would stop the project and if there is nothing I think that the chances to get this done are ~80%. 

If there is something like that released you will hear about it ;)

---

### Post by tuahaa on 2010-01-23
> **Queue29 said:**
> ..because?

So you think the developer who puts in 100 hours to make this app deserves to die? And his family to go into poverty?

If anything, *not* paying for software is a human rights violation.

Well duh. Die of starvation, I say- as long as I don't have to pay a dollar for someone else's sweat and blood:twisted:

---

### Post by chris4585 on 2010-01-23
I would go for like $1 - $5 if and only if it was great, but I think a donate button would be better suited maybe

---

### Post by mmachado on 2010-02-05
> **Queue29 said:**
> ..because?

So you think the developer who puts in 100 hours to make this app deserves to die? And his family to go into poverty?

If anything, *not* paying for software is a human rights violation.

I agree.

---

### Post by MasterNetra on 2010-02-05
> **spupy said:**
> This will work for the base stuff, like fonts, sizes and colors. Unfortunately, the finer details of a theme are dependent on the theme engine. Each theme engine (clearlook, aruro, murrine, etc) may have it's own options, which are incompatible and not present in other engines. For example, the murrine engine has its own configurator, but it doesn't work for other themes.

Prehaps the themer could have theme engine plugins? Perhaps default to Murrine or something. The Theme Engine plugin would determine what your editing options are. Have in the plugin a list of options and the themer could have them all and just enable them based on what Theme Engine Plugin is in use. 
Just my 2 cents.

---

### Post by D_E_H0987 on 2012-11-13
> **dilomo said:**
> Would you like to have such a program? Would you use it? Would you use it if it's payed (~$1-$2) or only of it's free? 

A mockup is attached.

[B]This is example of what would a theme creator look like. The basic principles are these:

1. You edit(create) a svg template (much like the single canvas workflow for icons in Breath) that contains all images needed for a theme.

2. You set up some more options of the theme.

3. Export as pixbuf theme (or css in the future)

What do you think? Is this worth implementing? It is possible to do it right now but I need a wider discussion about it beforehand.[/B]

I have been looking for something like this since installing Ubuntu.
I would love to see all sorts of options.
Things like maybe setting the sidebar to two icons wide so you don't have to scroll up and down so much.
Maybe options for rearranging the dash.
Text window background colors.
Editing cursors,icons, etc.
Positioning the side bar(s).
multiple side bars.
Nested or Menu'ed side bars(you click a button on the side bar and a bar slides out with programs you don't use much, or for different types of work, etc.)

As to making money, you could do something like have the main basic APP GPL and sell cheap plugin APPlets to add features, that way you have the best of both worlds free software which everyone loves and you can make money too.
And of course you have the big corporate users pay for the whole kit and caboodle.   Or there is always the big way to make money make it all GPL but make people sit threw advertising to get to a download link.

Anyway a few ideas, I hope you get this critter made.

Thanks in advance.

---

### Post by nothingspecial on 2012-11-13
Please don't bump very old threads to the top.

Closed.

---

