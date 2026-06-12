---
title: "Saving a selection -  Gimp"
date: 2010-01-27
forum: Ubuntu Studio
---

### Post by Orange Kingdom on 2010-01-27
Hi,

I want to save a selection with Gimp, but it saves also the dashed line.
This is very very annoying. How can i remove the dashed line?

---

### Post by zipperback on 2010-01-27
Can you please post a screenshot of what you are talking about? Thanks.

- zipperback
:popcorn:

---

### Post by Orange Kingdom on 2010-01-27
> **zipperback said:**
> Can you please post a screenshot of what you are talking about? Thanks.

- zipperback
:popcorn:


I want to select the red square  (see image)
And paste as new image.  The dashed line keeps surrounding the image.

---

### Post by Ravenheart on 2010-01-27
If you look in View>Show Selection and deselect or press Ctrl-T and that should get rid of the "marching ants".

---

### Post by howefield on 2010-01-27
After you have pasted your selection, click somewhere outside the pasted image to get rid of the lines ?

---

### Post by thatguruguy on 2010-01-27
It looks to me that the dashed line he is seeing in the pasted image is just showing the image boundary. It's not the "flashing" dashed line that indicates a selected area; it just shows him the area that would be saved once he saves the image.

---

### Post by Orange Kingdom on 2010-01-27
The dashed line is IN the image. So when i open the saved image the dashed line is still there.

---

### Post by howefield on 2010-01-27
:lolflag:

Yeah, use the clone tool to pick up some of the colour you want and clone over the lines. You can enlarge the image to make it easier to see where you need to clone.

There's probably a dozen ways of getting rid of the lines.

---

### Post by Orange Kingdom on 2010-01-27
> **howefield said:**
> :lolflag:

Yeah, use the clone tool to pick up some of the colour you want and clone over the lines. You can enlarge the image to make it easier to see where you need to clone.

There's probably a dozen ways of getting rid of the lines.

This does not work, the line is still there.
I select a part of the image , not the line.

thanks.

---

### Post by howefield on 2010-01-27
> **Orange Kingdom said:**
> but the line should not appear there.

Hang on, I think there is some confusion here, are the lines in the original image you are copying from ?

If not, then the lines you are seeing are selection lines as already pointed out.

They are not part of the image.

---

### Post by Orange Kingdom on 2010-01-27
Well it is, try it yourself.

The line is not animated but is still part of the image.

---

### Post by Ravenheart on 2010-01-27
I have created a rectangle, filled it with a foreground colour, selected it by colour, copied and pasted it into a new window.  If I press Ctrl-t and click outside the rectangle the dashes disappear.  Am I doing anything different to you? BTW I am running GIMP 2.6.7.

---

### Post by Orange Kingdom on 2010-01-27
i do this:

1.start Gimp (2.6.7)
2.file-->new -->ok
3.click rectangle tool
4.make a rectangle (i get the animated dashed line arround the square, which is good)
5.fill with a color
6.copy or cut
7.paste as new image
8. i get the square surrounded with a dashed line  (not animated but part of the image).



btw when i do this in photoshop the pasted square is without the dashed line.

---

### Post by Ravenheart on 2010-01-27
What happens when you press ctrl-t and click outside the pasted rectangle? Are you pasting into a new file or just copy and pasting into the original file?

---

### Post by Orange Kingdom on 2010-01-27
> **Ravenheart said:**
> What happens when you press ctrl-t and click outside the pasted rectangle? Are you pasting into a new file or just copy and pasting into the original file?


When i press the ctrl-t then the animated dash disappears.Looks if the rectangle has been deselected.

But when pasted the dashed line is still there.
I paste as a new image.

When you follow my steps do you get the dashed line?

---

### Post by Ravenheart on 2010-01-27
When I follow your steps I get the dashed line.  However I get the dashed lines when I paste.  But pressing Ctrl-t  and clicking outside the selection in the pasted window gets rid of these for me.

---

### Post by Orange Kingdom on 2010-01-27
But the line is part of the pasted image. ctrl-t has then no effect.

When i open just an image, make a selection, paste as new image, then the dashed line should not be part of the image.
That's strange isn't it?

---

### Post by howefield on 2010-01-27
> **Orange Kingdom said:**
> But the line is part of the pasted image.

Not at all, as pointed out, the dashed lines are not part of the image, try printing out your image, do the lines get printed ?

I think not.

---

### Post by Orange Kingdom on 2010-01-27
> **howefield said:**
> Not at all, as pointed out, the dashed lines are not part of the image, try printing out your image, do the lines get printed ?

I think not.

It is.

I now that the animated dashed line is not.
I repeat:

1.open an image.
2.make a selection  (the animated dashed line appears)
3.copy or cut
4.paste as a new image

I get a dashed line IN the image.
Please try it and you will see.

---

### Post by Ravenheart on 2010-01-27
Having looked at your screenshot again it is very similar to what I see when I do as you say.  The pasted selection will have the dashed lines, at least that's what my version of GIMP does.  Am I correct in saying that the dashed lines are printed, as I have printed the image with the dashes and they are not printed.
When you say the dashed line is in the image do you mean that the dashed line is around the selection with the black background, if so this is normal in the GIMP.

---

### Post by Orange Kingdom on 2010-01-27
I do not have a printer so i can't test it.

The dashes are in the image. I select , copy and paste and the dashes are there around the image, seems that gimp also includes the selection dashed line. that's weird because in Photoshop it's not.

See image  -->the pasted image has the dashed line IN the image. If i would print this it print also the dashed line.

Hm,  when i save the selection to a jpg and open it with a viewer , the dashes are gone.

---

### Post by Orange Kingdom on 2010-01-27
Problem solved i think. Saving as jpg removes the dashes.  :o

---

### Post by thatguruguy on 2010-01-27
> **Orange Kingdom said:**
> I do not have a printer so i can't test it.

The dashes are in the image. I select , copy and paste and the dashes are there around the image, seems that gimp also includes the selection dashed line. that's weird because in Photoshop it's not.

See image  -->the pasted image has the dashed line IN the image. If i would print this it print also the dashed line.

Hm,  when i save the selection to a jpg and open it with a viewer , the dashes are gone.

The dashed lines are NOT IN THE IMAGE.  As noted in my first response to you, the non-blinking dashed line just shows you the boundary of the image. It's to let you know (in the example you posted) that the gray background outside of the dashed line is not part of the new image. Again, IT'S THE BOUNDARY OF THE IMAGE.

---

### Post by thatguruguy on 2010-01-27
> **Orange Kingdom said:**
> Problem solved i think. Saving as jpg removes the dashes.  :o

It wasn't a problem to begin with.

---

### Post by Ravenheart on 2010-01-28
> **Orange Kingdom said:**
> Problem solved i think. Saving as jpg removes the dashes.  :o
OK. Problem solved.  It just takes some time to get used to the GIMP, especially if you're coming from something like Photoshop. I think you can mark this thread as solved!

---

