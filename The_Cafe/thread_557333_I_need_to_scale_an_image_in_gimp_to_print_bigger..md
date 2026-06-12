---
title: "I need to scale an image in gimp to print bigger."
date: 2007-09-22
forum: The Cafe
---

### Post by Roasted on 2007-09-22
What the title says. I've scaled it from 300x152 to like 7500x3580, yet it prints out the same darn size. I need it to print out a bit bigger. I even tried the windows machine we have here. Overall, I've used MS Picture It, MS Paint, PhotoImpression and on my Linux machine I used Gimp.

Nothing works. What can I do? What option is it?

---

### Post by Spr0k3t on 2007-09-22
What type of graphic are you working with?

---

### Post by reacocard on 2007-09-22
> **Roasted said:**
> What the title says. I've scaled it from 300x152 to like 7500x3580, yet it prints out the same darn size. I need it to print out a bit bigger. I even tried the windows machine we have here. Overall, I've used MS Picture It, MS Paint, PhotoImpression and on my Linux machine I used Gimp.

Nothing works. What can I do? What option is it?

Don't rescale it in the editor, just set the width and height options for the image in the GIMP's print dialog.

---

### Post by bruce89 on 2007-09-22
The GIMP should print images as big as the paper will allow by default.

You can't print bigger than the paper.

---

### Post by ghostborg on 2007-09-22
If your in a hurry.
Save yourself the frustration.
Boot into Winblows.
Use your familiar tools.

Otherwise check this site out:
[http://www.gimpguru.org/AskTheGuru/G20050312/](http://www.gimpguru.org/AskTheGuru/G20050312/)

---

### Post by bruce89 on 2007-09-22
> **ghostborg said:**
> If your in a hurry.
Save yourself the frustration.
Boot into Winblows.
Use your familiar tools.


Help in a poem, now I have seen it all.

---

### Post by Roasted on 2007-09-22
> **reacocard said:**
> Don't rescale it in the editor, just set the width and height options for the image in the GIMP's print dialog.

There's a problem here.

My printer is out of ink, however I've edited the image a lot in gimp and I'd like to use gimp to finish it off, by doing this I'd simply email it to myself so I can grab it on the windows machine, download it, and print. So when it leaves my Linux machine, I want it to be print-ready. So the print dialog box thing for gimp may not be what I want. I just need to actually scale the image larger...

Like, I remember a tool years ago in high school for a project. I could select the picture, making those 4 boxes appear at all 4 corners of the picture. Then, if I held down a certain key and click + drag on the one box, I could drag the picture larger without sacrificing the proportions of the photo (due to me holding that key).

That's what I need to do...

This image by the way is a tattoo design I came up with. I printed it out to kind of show myself how it'd look, but it's a bit smaller than I'd like, hence why I want to print it out larger and be able to hold it up and get an idea of what I'd be looking at with it inked.

---

### Post by az on 2007-09-22
Create an Openoffice.org draw document and import your photo there.  You can use a text doeument, too, but I am not sure about exporting that.

Hold down the shift key as you resize the image on the page.

Export to PDF or whatever you want.  Then email it.

---

### Post by Roasted on 2007-09-22
I'll do that, but I'll just print screen it and save it as a png or jpg. ;)

Cancel that. The Windows machine already had open office on it. Worked nicely! But I wonder, is there something in GIMP that allows this?? I'd like to know for future reference.

---

### Post by reacocard on 2007-09-22
> **Roasted said:**
> I'll do that, but I'll just print screen it and save it as a png or jpg. ;)

Cancel that. The Windows machine already had open office on it. Worked nicely! But I wonder, is there something in GIMP that allows this?? I'd like to know for future reference.

I believe Image->Print size is likely what you want, but really, why not just install the gimp in windows? If you don't have admin you can still [run it as a portable app]("http://portableapps.com/apps/graphics_pictures/gimp_portable").

---

### Post by Roasted on 2007-09-23
> **reacocard said:**
> I believe Image->Print size is likely what you want, but really, why not just install the gimp in windows? If you don't have admin you can still [run it as a portable app]("http://portableapps.com/apps/graphics_pictures/gimp_portable").

I understand. But the windows machine is actually my mother's computer that I just steal everytime I need to print something until I get more ink. Plus, down here at my Linux machine I have a 22 inch screen that's very bright, so it makes stuff like this easier to accomplish, whereas her 17 inch screen just makes me sad when using it for photo editing. ;)

I'll try out the print size thing in gimp, however even if it doesn't work, the openoffice word thing worked great!

---

### Post by Roasted on 2007-09-23
Ya know, another question about gimp.

This entire design has been done freehand, and it drives me nuts. There's certain curves in it that I just can't seem to get perfect. Is there some kind of a tool, somewhere, anywhere, in gimp that'll draw lines?

I guess I'm looking for something like the two line tools found in MS Paint. remember those? One's straight, the other allows you to make 2 bends to it. Something like that would be great...

---

### Post by az on 2007-09-24
> **Roasted said:**
> Ya know, another question about gimp.

This entire design has been done freehand, and it drives me nuts. There's certain curves in it that I just can't seem to get perfect. Is there some kind of a tool, somewhere, anywhere, in gimp that'll draw lines?

I guess I'm looking for something like the two line tools found in MS Paint. remember those? One's straight, the other allows you to make 2 bends to it. Something like that would be great...

Try inkscape.

---

### Post by Diabolis on 2007-11-10
The "paths tool" will do what you want.

---

### Post by linuxlizard on 2007-11-10
If he's trying to print this on a windows machine, and scaling the image with the gimp first isn't working, the problem is most likely something on the windows side he's not doing...

---

### Post by Diabolis on 2007-11-11
> I've scaled it from 300x152 to like 7500x3580, yet it prints out the same darn size.

I'm guessing you are using A4 paper, its dimensions are approximately 840 x 1188. So, for a 7500x3580 image you will need  around (9x3) 27 sheets. You can print it this big through XP, I just did something similar with a big diagram. You only need to select the option that says something like "print normal size". If you want a smaller print, just calculate how many sheets you want to use. For example if you want a 4 sheets print, then your image's size must be 1680x2376.

You need to take care of the margins too. XP adds margins to all the prints. So if you though you were printing 4 sheets, you wi&#314;l end up with  9 sheets.

---

### Post by DoctorMO on 2007-11-11
> If your in a hurry.
Save yourself the frustration.
Boot into Winblows.
Use your familiar tools.

When in a hurry, to do the job,
Frustrations seem to make you sob.
The floating gnu can help you here,
to meditate with eyes of the seer.

This guy he wants to draw designs
But fails to look at the best signs
To create a new in photoshop
is a pointless as a headless mop.

The tool of choice is inkscape for sure,
It draws freely and can do even more.
The proof is on deviant art,
Event if it can be quite tart.

[http://doctormo.deviantart.com/art/Dring-and-Drang-58117202](http://doctormo.deviantart.com/art/Dring-and-Drang-58117202)

:-) HarHar *evil laugh* you didn't know I could inflict Vogon level poetry.

---

