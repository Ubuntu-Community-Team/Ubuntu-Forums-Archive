---
title: "Icon bg not lining up with panel bg"
date: 2007-09-03
forum: Ubuntu System Panel
---

### Post by ironfistchamp on 2007-09-03
Hey everybody,
 
Just put the latest SVN of USP on my machine. I am still having a problem with the icon of it. Basically when I choose my own icon, even if it is a standard size, the background of the icon does not line up with the background of the panel. I am using a dark theme atm (making it look like vista, don't shoot me), and it is an absolute pain.
 
Does anyone else experience this or know how to fix it without saetting the bar to ~40px height?
 
I will get screenshots when I am at home to clarify things.
 
Thanks
 
Ironfistchamp

---

### Post by Malac on 2007-09-04
> **ironfistchamp said:**
> Hey everybody,
 
Just put the latest SVN of USP on my machine. I am still having a problem with the icon of it. Basically when I choose my own icon, even if it is a standard size, the background of the icon does not line up with the background of the panel. I am using a dark theme atm (making it look like vista, don't shoot me), and it is an absolute pain.
 
Does anyone else experience this or know how to fix it without saetting the bar to ~40px height?
 
I will get screenshots when I am at home to clarify things.
 
Thanks
 
Ironfistchamp

Find this function at line 808 in /usr/bin/usp :
```
    def changeButton(self, text, hideIcon, customIcon):
        self.systemlabel.set_text(text)
        # This code calculates width and height for the button_box
        # and takes the orientation into account
        if customIcon != "":
            # This looks odd but it means we can use absolute paths
            self.button_icon.set_from_pixbuf( icon_factory.load_image( customIcon, self.IconSize ).get_pixbuf() )
            #self.button_icon.set_from_icon_name(customIcon, self.IconSize)
        else:
            self.button_icon.set_from_icon_name("distributor-logo", self.IconSize)

        if self.orientation == gnomeapplet.ORIENT_UP or self.orientation == gnomeapplet.ORIENT_DOWN:
            if hideIcon == False:
                self.button_box.set_size_request(self.systemlabel.size_request()[0] [COLOR=Red]+ 25[/COLOR], [COLOR=Red]-1[/COLOR])
                self.button_icon.show()
            else:
                self.button_box.set_size_request(self.systemlabel.size_request()[0] [COLOR=Red]+ 2[/COLOR], [COLOR=Red]-1[/COLOR])
                self.button_icon.hide()
        else:
            if hideIcon == False:
                self.button_box.set_size_request([COLOR=Red]-1[/COLOR], self.systemlabel.size_request()[1] [COLOR=Red]+ 25[/COLOR])
                self.button_icon.show()
            else:
                self.button_box.set_size_request([COLOR=Red]-1[/COLOR], self.systemlabel.size_request()[1] [COLOR=Red]+ 2[/COLOR])
                self.button_icon.hide()

```The numbers in red are padding, try removing/changing the [COLOR=Red]+ 2[/COLOR]'s, the [COLOR=Red]-1[/COLOR]'s and/or the [COLOR=Red]+ 25[/COLOR]'s .

Let  me know if this helps and I'll try and make it an offset option when I've got time.

---

### Post by ironfistchamp on 2007-09-08
Sorry for the late reply. I tried messing with those numbers but I could never get it to the right height.

I have included two screens. In each one I have change the 25's and 2's to 50's. It made no difference to the height, just the width. The first is with the icon size set to 2 and the second to 3.

Thanks for the reply though. Hope we can get this sorted.

Ironfistchamp

---

### Post by Malac on 2007-09-09
> **ironfistchamp said:**
> Sorry for the late reply. I tried messing with those numbers but I could never get it to the right height.

I have included two screens. In each one I have change the 25's and 2's to 50's. It made no difference to the height, just the width. The first is with the icon size set to 2 and the second to 3.

Thanks for the reply though. Hope we can get this sorted.

Ironfistchamp
Okay, can you send me a tar of the theme you are using or the name of it and the bg pic also a copy of a backup of usp settings. This last can be done by going to "Preferences" in the right-click menu and then choosing [Backup].
Thanks.

---

### Post by gabrieliscool on 2007-09-11
i i just gave up and left it as is

---

