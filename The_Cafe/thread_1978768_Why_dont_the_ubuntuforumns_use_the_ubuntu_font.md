---
title: "Why dont the ubuntuforumns use the ubuntu font?"
date: 2012-05-12
forum: The Cafe
---

### Post by georgelappies on 2012-05-12
The ubuntu font is one of the reasons I really like ubuntu as well as the quality of the rendering of the font.

However this forum as an extension of ubuntu for some reason (in my opinion, so no offence to anybody :)) uses an ugly weird font not lending itself to proper anti aliasing.

Here is a sample of the ubuntu font in action:

[[img]http://farm8.staticflickr.com/7096/7181384944_3803cf2c1e.jpg[/img]](http://www.flickr.com/photos/79382089@N03/7181384944/)
[ubuntu-font](http://www.flickr.com/photos/79382089@N03/7181384944/) by [georgelappies](http://www.flickr.com/people/79382089@N03/), on Flickr

And here is a sample of the font on these forums:

[[img]http://farm8.staticflickr.com/7104/7181384212_2a67dc3c38.jpg[/img]](http://www.flickr.com/photos/79382089@N03/7181384212/)
[ubuntu-forums](http://www.flickr.com/photos/79382089@N03/7181384212/) by [georgelappies](http://www.flickr.com/people/79382089@N03/), on Flickr

Notice the difference in quality of the rendering? Unfortunately chrome doesn't support forcing one font on all pages like firefox does, but then again firefox and flash no longer play nice :(

Is there any way to maybe draw up a poll to see how many are interested in getting maybe another forum theme "cleanv4" for example that will use the ubuntu font?

---

### Post by Phoenixie on 2012-05-12
Just use the new [Ubuntu]("http://ubuntuforums.org/showthread.php?t=1977943") theme.

---

### Post by georgelappies on 2012-05-12
> **Phoenixie said:**
> Just use the new [Ubuntu]("http://ubuntuforums.org/showthread.php?t=1977943") theme.

lolol, what is the likely hood of this :)

Yeah, definetly using it now, thanks!

---

### Post by agillator on 2012-05-12
In general the web page only has limited control over the actual font displayed. The browser has the final say. That is why you, as the user, can change the font size on a page, you can use plugins like grease monkey, etc., etc. If you will check the preferences of the browser you are using you will find you can even change the fonts used. This is a bit of a simplification but the problem you run into with fonts is you never know what fonts your user has available so you program in generalities. If you don't like the fonts displayed by your browser, change them.

---

### Post by georgelappies on 2012-05-12
> **agillator said:**
> In general the web page only has limited control over the actual font displayed. The browser has the final say. That is why you, as the user, can change the font size on a page, you can use plugins like grease monkey, etc., etc. If you will check the preferences of the browser you are using you will find you can even change the fonts used. This is a bit of a simplification but the problem you run into with fonts is you never know what fonts your user has available so you program in generalities. If you don't like the fonts displayed by your browser, change them.

Thanks agillator, however setting the default font in preferences in chrome doesn't override the web page's font.

See here: [http://ubuntuforums.org/showthread.php?t=1976185&highlight=chrome+font](http://ubuntuforums.org/showthread.php?t=1976185&highlight=chrome+font)

Firefox I know has that ability, but with chrome you have to jump through loops and break functionality to get something similar :(

---

### Post by SeijiSensei on 2012-05-12
The default forum stylesheet is here: [http://ubuntuforums.org/clientscript/vbulletin_css/style-890de029-00098.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-890de029-00098.css)

It uses the MS fonts (Tahoma, Verdana, Arial). Surprisingly it doesn't have a default for people who don't have one of these fonts installed, even the generic "sans-serif" option.  I always install the MS fonts, so this forum looks pretty similar to other vBulletin forums I frequent.

I also use one or more the MS fonts on pages I design since they will be available to the vast majority of visitors.  However I usually add Helvetica and sans-serif to the list to cover people on non-MS platforms.

---

### Post by craig10x on 2012-05-12
haven't looked at the Chrome Extensions section lately, but i recall there was an extension that actually forces all web pages to automatically use ubuntu fonts....

doesn't even require you change your font settings in Chrome, just changes everything automatically...and if you decide you don't like it, simply remove the extension and you are back to the way you were before...

it requires that you close the browser and then re-open it to "kick in" after you install it..

just checked...it is still available...just go to the extensions from your preferences and put "ubuntu fonts" in the search bar and you will see it on the extensions list...

---

### Post by MisterGaribaldi on 2012-05-12
I thought there was a way to render fonts dynamically so long as the server itself had the TrueType outline data for them.

---

### Post by SeijiSensei on 2012-05-12
Yes there is, but as you say, the server has to have the font file available.  I used this capability on a site I built recently, but it's not very commonly used as far as I can tell.  In my case, I wanted to create some highly-styled headers in a script font.

You implement this technique by defining a font in the CSS stylesheet like this:
```

@font-face {  
     font-family: MySpecialFont ;  
     src: url( /images/MySpecialFont.ttf ) format("truetype");  
}  		

```

---

### Post by georgelappies on 2012-05-12
> **craig10x said:**
> haven't looked at the Chrome Extensions section lately, but i recall there was an extension that actually forces all web pages to automatically use ubuntu fonts....

doesn't even require you change your font settings in Chrome, just changes everything automatically...and if you decide you don't like it, simply remove the extension and you are back to the way you were before...

it requires that you close the browser and then re-open it to "kick in" after you install it..

just checked...it is still available...just go to the extensions from your preferences and put "ubuntu fonts" in the search bar and you will see it on the extensions list...

Thanks! that plugin works great!

---

### Post by craig10x on 2012-05-12
you are very welcome ;)

---

### Post by Technoviking on 2012-05-12
The new theme now uses the following fonts in order:
Ubuntu, "Bitstream Vera Sans", "DejaVu Sans", Tahoma, sans-serif;

For the best experience install the Ubuntu of a non-Ubuntu machine if needed.

---

### Post by MisterGaribaldi on 2012-05-13
Just D/L'd and installed the Ubuntu family on my Mac. Everything seems to be in order now. :)

---

