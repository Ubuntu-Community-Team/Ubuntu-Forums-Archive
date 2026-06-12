---
title: "[SOLVED] app for merging swf (flash) files?"
date: 2008-08-25
forum: Ubuntu Studio
---

### Post by generic_idea_machine on 2008-08-25
Is there any application out there that would allow me to merge different *.swf (flash) files into one big file. 

Does'nt matter if the output file is in another format. As long it is able to render the video. 

I have tinkered with the following packages, without any luck so far. 

<snip>
Kino  	  
Avidemux 
DeVede 	
Cinelerra
</snip>

Danke

---

### Post by generic_idea_machine on 2008-08-26
cmon folks

there has got to be an application out there that can do this?

---

### Post by paulmerchant on 2008-08-26
Try [swftools]("http://swftools.org"). That project has some command line tools that do this sort of thing. Don't know if they'll work for your requirements, though.

---

### Post by Creative2 on 2008-08-27
try blender

---

### Post by generic_idea_machine on 2008-09-08
> **paulmerchant said:**
> Try [swftools]("http://swftools.org"). That project has some command line tools that do this sort of thing. Don't know if they'll work for your requirements, though.

thanks Paul

I'll give it a try

---

### Post by generic_idea_machine on 2008-09-09
> **Creative2 said:**
> try blender

heya

apologies I totally missed this comment. 

seems like swftools* has done the trick. I will try blender nonetheless just to ascertain if one offer a better set of features over another. 

* 
sudo swfcombine -o newFile.swf -Tm *.swf

---

### Post by generic_idea_machine on 2008-09-09
whoa!

Blender seems like full scale video editing software. 

I think I will stick with swfcombine (swftools) 

but thanks for the tip

---

