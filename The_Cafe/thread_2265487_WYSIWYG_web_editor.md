---
title: "WYSIWYG web editor"
date: 2015-02-15
forum: The Cafe
---

### Post by madbadger on 2015-02-15
Guys,

I didn't really know which was the best forum to ask this so feel free to tell me to shove it somewhere else.

I've been looking for a wysiwyg web editor purely for designing layout templates without having to hand code every line of html/css.  Thing is, I can't seem to find one.  Are there any decent ones out there?

Cheers

---

### Post by rewyllys on 2015-02-16
Have you looked at *Bluefish*?

---

### Post by user1397 on 2015-02-16
Bluefish is a text editor (almost an IDE but more like an advanced text editor specialized for writing websites and some programming languages) but it is a desktop application.  As far as a WYSIWYG web editor I don't know of any.  Closest I can think of is some sort of CMS, like Wordpress.

---

### Post by kc1di on 2015-02-16
you can install the seamonkey web suite which has composer , it works pretty good for me.
you can find out how to install it [here. ]("http://linuxg.net/how-to-install-seamonkey-2-25-on-ubuntu-14-0413-1012-1012-04-linux-mint-161413-and-elementary-os-0-2/")

---

### Post by SeijiSensei on 2015-02-16
You could embed [TinyMCE](http://www.tinymce.com/) into a web page and use that.

---

### Post by mooreted on 2015-02-16
Wordpress.

---

### Post by SeijiSensei on 2015-02-17
WordPress uses TinyMCE as its editor.  If you don't want all the bells and whistles of WordPress, you can just add the editor to a simple web site.

---

### Post by Dragonbite on 2015-02-17
Isn't Geany supposed to provide some graphical editing?

Also, I don't know if it is kept up-to-date, but there was [Kompozer ]("http://www.kompozer.net/")(formerly Nvu).  It also includes a split-view so that as you change things in the HTML code, you can see the changes in a viewing panel.

There is also BlueGiffon[http://bluegriffon.org/]("http://bluegriffon.org/") which is cross-platform.

I rarely use graphical IDEs for web development, and when I do it is usually Visual Studio at work.  What I do is type it all up in HTML or the like, using a CSS file for styling, and then use the Web Developer tool in Firefox (hit F12) where I can edit (add, turn off, change) the style tags and see immediately what it looks like.  Then I keep track of what the final settings are and have to manually edit the CSS page but at least I have seen what it will look like.

It isn't perfect, but it works and until Visual Studio handles PHP, is the best method I have at work for the time being.

---

### Post by Tom_Carr on 2015-08-11
Konpozer was good but is no longer kept up to date.  I am using PageEdit extension to chrome.

---

### Post by Dragonbite on 2015-08-11
On that note, there is also [HTML Editor for Drive]("https://chrome.google.com/webstore/detail/html-editor-for-drive/hmgpiigchjeclbkocfndppmhmfjdhbah").

WYSIWYG editors / IDEs are lacking in Linux. 

I have been coding the HTML by hand and applying CSS then in Firefox hit F12 for the web editor where I can change and add CSS tags and values and see the results immediately in the browser.  Not fantastic, but works.

I'm not sure what Monodevelop has for grapical or if that would be relevant.

---

### Post by monkeybrain20122 on 2015-08-11
google web designer?
[http://ubuntuportal.com/2014/04/google-web-designer-available-for-linux-install-it-on-ubuntu-and-derivatives.html](http://ubuntuportal.com/2014/04/google-web-designer-available-for-linux-install-it-on-ubuntu-and-derivatives.html)

or Bluegriffon

[http://bluegriffon.org/](http://bluegriffon.org/)

The last release was two years ago but the dev posted some 2015 progress update in April so I suppose it is still alive.

---

### Post by patrick19 on 2015-08-13
[COLOR=#000000]TinyMCE +2

As a web dev, this is what we use. Make sure you read the documentation on how to configure it, as the default behavior may not be to your liking (if you're unfamiliar with html).

I'm sure the other suggestions are also good, too.[/COLOR]

---

### Post by Bucky Ball on 2015-08-14
wysiwyg web design apps ARE sadly lacking in Ubuntu. Kompozer is what you're looking for. Pick of the bunch. Check the Software Centre. Is old and no longer supported but still works great here. I have used it for web design since first getting into Ubuntu and still using it when required. 

I'd love to see a new, supported version of Kompozer or any other wysiwyg app pop-up, but don't see anything on the horizon. :|

PS: Many of the suggestions so far are not for wysiwyg editors. There basically aren't any currently supported that I know of (or I'd be using it). Happy to be enlightened or corrected.

---

### Post by patrick19 on 2015-08-14
TinyMCE is a web based wysiwyg. If you use it as a plugin for joomla or wordpress, you can have a powerful and simple to use tool for building pages and full sites without having to hack a ton.

And as others have mentioned, you can install it to your server and embed it to a static page to work with. It's very flexible.

---

### Post by Tom_Carr on 2015-12-08
I am using the PageEdit extension to chrome, but I like Komposer better.  I still have it installed on this box, but don't know if I will be able to install it in the future.  If anything new and good comes along please let me know.  For now the PageEdit extension to chrome is the best substitute for Chrome that I know of.

---

### Post by ericj2 on 2015-12-09
> **Dragonbite said:**
> Isn't Geany supposed to provide some graphical editing?

Also, I don't know if it is kept up-to-date, but there was [Kompozer ]("http://www.kompozer.net/")(formerly Nvu).  It also includes a split-view so that as you change things in the HTML code, you can see the changes in a viewing panel.

There is also BlueGiffon[http://bluegriffon.org/](http://bluegriffon.org/) which is cross-platform.

I rarely use graphical IDEs for web development, and when I do it is usually Visual Studio at work.  What I do is type it all up in HTML or the like, using a CSS file for styling, and then use the Web Developer tool in Firefox (hit F12) where I can edit (add, turn off, change) the style tags and see immediately what it looks like.  Then I keep track of what the final settings are and have to manually edit the CSS page but at least I have seen what it will look like.

It isn't perfect, but it works and until Visual Studio handles PHP, is the best method I have at work for the time being.

I downloaded installed Bluegriffon on Windows and haven't yet had a chance to look at it much but can't figure out the way to properly install in Ubuntu. (New to Linux)

---

### Post by Wadim_Korneev on 2015-12-16
For Pay: Quick ‘n Easy Web Builder. You can now find this in the Ubuntu Software Center and it is a paid application. It has some really unique features that allow you to design by just placing images, text, videos etc on a page and it produces the html5 code and css for you. It even has basic image editing capabilities inside the application. It is not an html editor however, although you can tweak the code to some extent inside the application. It saves files in its own application format and only produces html code when you publish your page or site. So you are free to edit the code/css once its published with an html editor, but doing so no longer allows you to edit within QnEWB. You have to go back to your original source file to make any changes and publish again. 
Another restriction is that since you are placing images and text wherever you want on the page, it uses absolute placement, so you can not produce pages that automatically re-size to a browser window. You would need to edit the code after its published to make those changes.
With those minor limitations in mind, it is a great WYSIWYG editor and I highly recommend the purchase. (ie I am not affiliated with QnEWB in any way or form.)

---

### Post by Bucky Ball on 2015-12-16
Which version's repos is it available in and what are you searching it as? I don't see Quick 'n Easy Web Builder in the 14.04 repos. :-k

---

### Post by ericj2 on 2015-12-16
Thanks Wadim, appreciate your input, I think between that and Bluegriffon I can do most of what I want to do. Not in the midst of any web building right now so I may have to work on those later and probably would pay for the QnE program, I paid for Sitespinner. Been using it for years in addition to regular coding. Nice thing about SS is you can create graphic elements easily in the editor also.

Probably for this work and some of my video editing I may have to keep Windows in a "small" corner of my hard drive(s). I hope that more Ubuntu compatible software becomes available, paid or not.

---

### Post by oygle on 2016-04-26
Tried Komposer and BlueGriffon in the past. Either one used to crash and/or not up to date. Have been using Sea Monkey composer for a while, has been okay. But today it will not let me edit tables,etc. Any suggestions for a WYSIWYG html editor on Ubuntu ?

---

### Post by squirrel3 on 2016-04-26
I believe all if not most website editors are wysiwyg these days.

---

### Post by Bucky Ball on 2016-04-26
> **squirrel3 said:**
> I believe all if not most website editors are wysiwyg these days.

??? What is this based on? Are you talking about for Windows or Linux?

---

### Post by oygle on 2016-04-26
Even if there was a 'good' html editor for Linux, I wouldn't mind paying for it. My definition of 'good' is simply 'as good as' Komposer and didn't crash.  :)

---

### Post by Dragonbite on 2016-04-26
I wonder if there is a feature in LibreOffice to take a page and save it as HTML?  I know MS Word has that option (it's horrible... don't use it.... avoid like the plague), but I don't know if any other suite includes it.

---

### Post by 6975 on 2016-04-27
I use RocketCake pretty damn easy as Quick n Easy Web Builder.
But it's free & require wine.

---

### Post by ChuangTzu on 2016-04-29
Good old Seamonkey comes with it. [http://www.seamonkey-project.org/](http://www.seamonkey-project.org/)

---

