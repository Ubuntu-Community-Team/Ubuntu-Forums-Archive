---
title: "Gimp"
date: 2007-02-05
forum: The Cafe
---

### Post by Roasted on 2007-02-05
So, question. I've selected a bunch of pictures I want to throw into a collage. I want to crop them all the way I please and throw them onto a blank workspace, each picture being a layer so I can freely move them as I please.

Well, problem. I can't move them. When I paste a picture into the workspace, it just won't move. Whatever tool is active is what happens to the picture. If crop is active, it tries to crop it. How can I get around this? How can I just freely grab the pictures and just toss them to the corner?

---

### Post by ~LoKe on 2007-02-05
Select the move tool?

---

### Post by RAV TUX on 2007-02-05
> **Roasted said:**
> So, question. I've selected a bunch of pictures I want to throw into a collage. I want to crop them all the way I please and throw them onto a blank workspace, each picture being a layer so I can freely move them as I please.

Well, problem. I can't move them. When I paste a picture into the workspace, it just won't move. Whatever tool is active is what happens to the picture. If crop is active, it tries to crop it. How can I get around this? How can I just freely grab the pictures and just toss them to the corner?after you crop>select all>copy>paste...

you may want to open a blank board to paste all your pics to....open layers and you do what ever you need...

to move the picture simply select the move tool

---

### Post by slimdog360 on 2007-02-05
its the one with 4 arrows perpendicular to one another. You may also want to check out the pandora plugin, and/or try out the opacity slider tool in the right hand panel under the 'layers' tab up the top.

---

### Post by Dale61 on 2007-02-05
My take on this would be:

1/. Create new file with size required.

2/. Open each picture in a new window.

To be able to move each picture within the single window, each picture will have to a layer.

3/. For each picture, click Select -- All, then in your main window, select 'Paste'.  This will create a new layer.

4/. To move each layer, you will have to ensure it is highlight in your layer dialog box.  DO NOT FLATTEN UNTIL YOU ARE HAPPY WITH FINAL LAYOUT.

5/. Resize each layer as required - 'Layer -- Resize Layer'.

6/. Repeat steps 2 & 3 as necessary.

7/. When happy with final layout, flatten image, or anchor each layer.

You also crop further by using the eraser function whilst the image is still a layer.

Hope that helps.

---

### Post by RAV TUX on 2007-02-05
> **Dale61 said:**
> 
You also crop further by using the eraser function whilst the image is still a layer.

Hope that helps.

The wand tool is helpful for this also.

---

### Post by saulgoode on 2007-02-05
> **Dale61 said:**
> 
1/. Create new file with size required.

2/. Open each picture in a new window.

To be able to move each picture within the single window, each picture will have to a layer.

3/. For each picture, click Select -- All, then in your main window, select 'Paste'.  This will create a new layer.

4/. To move each layer, you will have to ensure it is highlight in your layer dialog box.  DO NOT FLATTEN UNTIL YOU ARE HAPPY WITH FINAL LAYOUT.

5/. Resize each layer as required - 'Layer -- Resize Layer'.

6/. Repeat steps 2 & 3 as necessary.

7/. When happy with final layout, flatten image, or anchor each layer.

You also crop further by using the eraser function whilst the image is still a layer.

A few shortcuts for Dale's method:

Create a new image of the appropriate final size (you can change it later, if any thing it is simpler to be larger than you expect).

Use File->Open As Layers to add all of your separate picture files to your image (as separate layers). You use the SHIFT and CTRL within the file dialog per the usual manner.

Use the Move Tool to position the layers within the image. The Scale Tool might come in handy for matching sizes. Regardless of which tool is active, you can "temporarily" activate the Move Tool by holding down the SPACE bar while dragging the mouse; releasing the SPACE bar returns you to your original tool. 

If you realize that your image size is too small to accommodate your repositioned layers, you can increase it by using the "Image->Canvas Size..." menu function. Alternately, you can use the "Image->Fit Canvas to Layers" function will fit the canvas to smallest size that includes all of the layers.

Use "Image->Fit Canvas to Layers" as a final step.

Be sure to save your file with the ".xcf" extension (or ".xcf.gz" to save disk space) in order to permit editing it later. If you save it only as PNG or JPG you will lose all of your layer information. Use "File->Save a Copy..." to produce a PNG or JPG for posting on the web or sharing with programs/people who can't handle the GIMP's native file format.

---

### Post by fuscia on 2007-02-05
i've had trouble with this, as well. the problem is in wanting to move a layer between the background layer and the top layer. i can only move the top layer and cannot select one of the middle layers in the layer dialogue. the methods suggested above do not resolve this.

---

### Post by saulgoode on 2007-02-05
The default behavior of the Move Tool is to move the topmost layer (in the layerstack) which is visible under the cursor. If the top layer is transparent (underneath the cursor), then the next layer down will be the one moved (unless it is also transparent, in which case... well, you know...).

In order to have the Move Tool operate on the currently active layer (the one highlighted in the layers window), you should hold down the SHIFT key while performing your mouse drag.

---

### Post by rsambuca on 2007-02-05
> **fuscia said:**
> i've had trouble with this, as well. the problem is in wanting to move a layer between the background layer and the top layer. [COLOR="Red"]i can only move the top layer and cannot select one of the middle layers in the layer dialogue[/COLOR]. the methods suggested above do not resolve this.
Just select the layer you want from the layers dialogue box, select the "move" tool, and then press and hold the shift key while you drag the middle layer around with your mouse.  Even though you may not even be able to see the middle picture, the outline is visible.

Edit:  Saulgoode beat me to it!

---

### Post by fuscia on 2007-02-05
you're not going to believe what i was doing. instead of opening each additional image as layer, i was opening the images in a new window, then reopening them as layer on top of themselves and then copying and pasting the whole mess onto the background image. what ultra-maroon!

---

### Post by saulgoode on 2007-02-05
Note that you can generally drag-n-drop pictures from your browser (either web or file) onto your GIMP image, creating a new layer from the dropped image. You can also d-n-d layers from the Layers window of one image onto the view window of another image.

---

### Post by fuscia on 2007-02-05
> **saulgoode said:**
> Note that you can generally drag-n-drop pictures from your browser (either web or file) onto your GIMP image, creating a new layer from the dropped image. You can also d-n-d layers from the Layers window of one image onto the view window of another image.

i don't know how to do that either. whenever i've tried to drag and drop, nothing happened. (i better stay home today.)

---

### Post by Dale61 on 2007-02-05
Another way to move 'middle' layers is to move them to either the top or bottom of the layer tree.

On your layer dialog box, when you have multiple layers, the arrows will be highlighted.  Once you know which layer is active, you can move arrow up (or down) any of the middle layers to move it to the top of the 'tree', then you can move it around that way.

At least that method works for me.

---

