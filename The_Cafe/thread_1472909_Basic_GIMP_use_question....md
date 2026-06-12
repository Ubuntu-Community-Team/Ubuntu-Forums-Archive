---
title: "Basic GIMP use question..."
date: 2010-05-04
forum: The Cafe
---

### Post by gabriella on 2010-05-04
Good Evening...
Maybe someone can help me with this. I new to using GIMP so still finding my feet. 

I've been editing an image today, mostly pretty simple stuff. I'm removing some text out of the image. It has a white background and was using the eraser which was working fine earlier. Came back after a break and now when I use the eraser its leaving a grey smudge when I erase instead of the white background. I must have done something to cause this. 

I need this image for a class tomorrow. Can anyone tell where to look or what to undo?

Thanks

---

### Post by NovaAesa on 2010-05-04
In The GIMP (and must other apps like it, such as photoshop), the eraser tool doesn't actually erase anything, it justs paints it to whatever the secondary colour currently selected it. By default, this is white.

In the toolbox window, you should see two little coloured squares that are overlapping each other. The one on top is the primary colour and the one on the bottom is the secondary colour. You just have to change the secondary colour back to white and it should work.

---

### Post by DogMatix on 2010-05-04
I'm not versed with GIMP. I use Photoshop day to day. But as a quick fix, if all you need is a white background you could use the brush tool to paint over the 'grey splodge' with white. Hope this helps.

EDITED: What NovaAesa says is probably the cause.

---

### Post by gabriella on 2010-05-04
> **NovaAesa said:**
> In The GIMP (and must other apps like it, such as photoshop), the eraser tool doesn't actually erase anything, it justs paints it to whatever the secondary colour currently selected it. By default, this is white.

In the toolbox window, you should see two little coloured squares that are overlapping each other. The one on top is the primary colour and the one on the bottom is the secondary colour. You just have to change the secondary colour back to white and it should work.

Thanks. Yes I'm familiar with that and thats not the problem!

I had the image started editing it and saved it earlier as xxxedit1.tiff. So far OK.

Edited some more and tried to save as edit2.tiff. I got some message about (cant remember exactly) "unable to save as different layers..do you want to export" Clicked yes and saved it. Now I get this problem.

Also when I use the eraser it has under the grey the dotted background whatever you call it? Does any of this make sense??????

@DogMatix
that trick might wok but theres something else going on..

---

### Post by ve4cib on 2010-05-04
Does the eraser tool have the "Hard Edge" option turned on or off?  If it's off it will smear the edges around the brush, instead of giving you a clear, crisp mark.

---

### Post by Hman242 on 2010-05-04
> **gabriella said:**
> Thanks. Yes I'm familiar with that and thats not the problem!

I had the image started editing it and saved it earlier as xxxedit1.tiff. So far OK.

Edited some more and tried to save as edit2.tiff. I got some message about (cant remember exactly) "unable to save as different layers..do you want to export" Clicked yes and saved it. Now I get this problem.

Also when I use the eraser it has under the grey the dotted background whatever you call it? Does any of this make sense??????

@DogMatix
that trick might wok but theres something else going on..
The tiling of grey squares means that area is transparent. If you want the area erased to be white, make another layer under your current one and fill it with white suing the paintbucket tool.

---

### Post by DogMatix on 2010-05-04
Somehow you have made the image into a 'layer'. Try making sure your background colour is white and then flattening the image. I'm not sure how to do this with GIMP. I dug this up googling [http://docs.gimp.org/nl/gimp-image-flatten.html](http://docs.gimp.org/nl/gimp-image-flatten.html)

---

### Post by Hman242 on 2010-05-04
> **Hman242 said:**
> The tiling of grey squares means that area is transparent. If you want the area erased to be white, make another layer under your current one and fill it with white suing the paintbucket tool.
You could also save the image as a .jpg when you are done editing to have the same effect.

---

### Post by oedipuss on 2010-05-04
Even if there's only one layer in your image, the eraser will erase to transparency, the grey pattern you're seeing if there is an alpha channel. 
I think you somehow added an alpha channel to your picture.
Go to menu Layers / Transparency / Remove Alpha channel, and hopefully it will turn all transparent pixels to the currently selected background color (presumably white) . After that, the eraser will behave as you expect, I think.

Hope this helps :)

---

### Post by gabriella on 2010-05-04
> **DogMatix said:**
> Somehow you have made the image into a 'layer'. Try making sure your background colour is white and then flattening the image. I'm not sure how to do this with GIMP. I dug this up googling [http://docs.gimp.org/nl/gimp-image-flatten.html](http://docs.gimp.org/nl/gimp-image-flatten.html)

OK I've done that and seems to have fixed my problem...!
Still not sure how it happened quite. something to do with saving 2nd edit. Why not the first edit I don't know. But Thanks!

---

### Post by gabriella on 2010-05-04
> **oedipuss said:**
> Even if there's only one layer in your image, the eraser will erase to transparency, the grey pattern you're seeing if there is an alpha channel. 
I think you somehow added an alpha channel to your picture.
Go to menu Layers / Transparency / Remove Alpha channel, and hopefully it will turn all transparent pixels to the currently selected background color (presumably white) . After that, the eraser will behave as you expect, I think.

Hope this helps :)

Thats good to know too! Thanks!

---

### Post by gabriella on 2010-05-04
OK I'm getting the same msg when I try to save again that created the original issue.

"Tiff Plug-in cant handle Layers"
"Flatten image?"
"Merge visible layers?"

Which should I choose? So I dont set this going again!!

---

### Post by oedipuss on 2010-05-04
Flatten image merges all layers together regardless of whether they're visible ( I think) . 
Merge Visible, just merges the visible ones, and ignores the rest. 
Usually you'd want Merge Visible, it will save what you actually see in your gimp window. 

Keep in mind that merging will discard all layer information. 
If you want to keep all your layers intact, to work on the file later for instance, then save the file as .xcf first (equivalent to photoshop .psd), the gimp's own format. From that you can later make any kind of flat image, jpg, tiff, whatever you need, for using in other applications. 

If you intended to have only one layer or don't care about keeping them, merging is fine .

---

### Post by gabriella on 2010-05-04
> **oedipuss said:**
> Flatten image merges all layers together regardless of whether they're visible ( I think) . 
Merge Visible, just merges the visible ones, and ignores the rest. 
Usually you'd want Merge Visible, it will save what you actually see in your gimp window. 

Keep in mind that merging will discard all layer information. 
If you want to keep all your layers intact, to work on the file later for instance, then save the file as .xcf first (equivalent to photoshop .psd), the gimp's own format. From that you can later make any kind of flat image, jpg, tiff, whatever you need, for using in other applications. 

If you intended to have only one layer or don't care about keeping them, merging is fine .

OK thanks. I think my mistake was saving as .Tiff to begin with when I should have saved as .xcf. I need to use this image for a presentation but evetually it will be printed and they want .tiff or the Adobe one. I think that's where I made the mistake.

---

### Post by Phrea on 2010-05-04
Thread is tl;dr.
But, did you try The Gimp plugin called 'Resynthesizer'...? [ [http://www.logarithmic.net/pfh/resynthesizer](http://www.logarithmic.net/pfh/resynthesizer) ]

---

### Post by Mr. Picklesworth on 2010-05-04
*SNIP*

&#8592;---- should finish reading threads before posting. Well, here's a screenshot of the Layers panel :b

[ATTACH]155538[/ATTACH]

---

