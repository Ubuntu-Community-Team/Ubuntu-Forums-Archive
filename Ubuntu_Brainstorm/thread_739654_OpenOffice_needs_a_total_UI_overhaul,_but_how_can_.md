---
title: "OpenOffice needs a total UI overhaul, but how can I get this plan to some devs?"
date: 2008-03-29
forum: Ubuntu Brainstorm
---

### Post by Redrazor39 on 2008-03-29
I think the UI is too much like MS Office 2003, which means it's inefficient and ugly. I have a plan to fix this, as typed below, but where can I get this to some devs for OOo extensions or OOo itself?

I don't think this should be the only UI option because it is so different, but it should be one of them found under the view menu. It should be so you can do View > Switch to new UI or View > Switch to classic to get back. 

Anyway, here's my plan (been working on it for a long time lol):

Office:


**Suggested**: Create an office suite with all the power and under-the-hood technologies as found in OpenOffice, but with the simplicity of Google Docs and iWork. One solution would be to submit technology such as AutoComplete and coding for printer-friendliness to Google, but then we just give them technology that may not be used. A harder, but safer and better solution is to create a totally new UI for OpenOffice, while still leaving an option to “Switch to Classic View” under the View menu.


**Specific Improvements:**


**Writer**: Writer is very stable and has powerful and unique tools such as Autocomplete, but the options seem a bit overdone. For example, the Insert menu is full of junk, including media tools. When was the last time anyone printed off media for a document? Under the hood, it's very powerful, but the UI is overcomplicated and nowhere near efficient or good looking.


I would suggest starting with Google Docs for a new UI. Start off with the standard OOo menubar, but only fill it with the stuff from the Google Docs menubar, and remove what does not apply and insert only absolutely necessary options (such as replacing Web preview with Print preview). Then, only have one toolbar at the top, but make it a “multi-bar” that changes depending on the content you are working with. When you are working with text, it is a standard text toolbar. With images, it is a basic image editing toolbar (along with an “edit in GIMP” option that opens it in GIMP but with a “Done” button you can click after editing so it won't save the edits as a file, but apply them to the image in the document.) Basically, the multi-bar changes with content.


You should also notice that when the Google Docs standard text toolbar is left-aligned, there is some space to the right. This is where pop-up toolbars such as Bullets and Numbering should automatically dock, but hwen there are too many buttons to fit in that space, don't make it so an expand arrow appears; that just adds an extra click. Instead, make it so a right-aligned toolbar below the multibar appears that only goes as far as the extra icons go (meaning start a new row of the extra icons that start on the right side. Then, only add a toolbar background where there are icons; don't just have blank parts of the second toolbar, so the toolbar only overs where the icons are.)


Then, as seen in iWork Pages, add a sidebar that, instead of showing slide previews like in Presentation (Impress), show pages and page previews. This would allow easily adding a new page, reordering pages, and deleting pages. This does not sound that useful and a waste of space, but it is far more handy than it seems.


This UI suggestion may seem oversimplified and lack features, but all features (if decided) will be intact. One solution to customize which and how many features to put one-click access to is called the “custom toolbar” (working name), and it works like the Dock in Mac OS X. You can drag any item from any menu to this toolbar and it will create an icon that has a name that will pop up upon mouseover. Click the icon, and it will take you to wherever the menu button does. There will also be an icon to the top right of every window that opens in this office app that can be dragged to the custom toolbar to open that window in the tab you happened to be in when you dragged the icon. The icons will be center-aligned like a dock or avant-window-navigator.


To get to the standard “Draw” bar at the bottom, there will be a vertical tab that says “Draw” to the left of the custom toolbar. When this is clicked, a sliding animation slides the bar to the right until the custom toolbar is fully hidden and only the Draw bar shows. To get to the custom toolbar again, click the vertical tab to the right that says “Custom Toolbar” for another sliding toolbar (from right to left) until the Draw bar is fully hidden and only the custom toolbar shows.



**Calc**: I haven't used Calc much, but from what I've seen, it's really, really confusing and FAR too much like Excel 2003. All I can say is head back to Google Docs and Spreadsheets for a UI base. This has a tabbed ribbon and works a bit like Excel 2007, but we could probably create something similar to the UI I suggested for Writer.


Also, one very important feature is to allow the movement and editing of content within print preview to make sure it fits on the pages you want.


Other than that, just keep it simple, easy to use, and easy to figure out.


**Impress**: Oh, gosh. Where do I start? I don't see myself impressing anyone with “2D and 3D graphics” as plastered all over the site. Sure, in 2000, that was cool, but now, that's just sad if that's your main attraction. The thing that really bothers me is how hard it is to create something great with all the crap and useless options surrounding my slide! For one thing, the right sidebar has to go. Make it so you choose a layout when you create a slide and there are two buttons in the top right, “change layout” of slide and “change theme” of presentation. Animations need to be added much easier. The easiest way I've seen is how MS Office 2007 does it, by clicking “Animations” and a menu with a graphic icon list (no text) of animations is shown and when you mouse over them, it shows you a preview of the current slide being animated, and when you click on it, it sets that animation as the entrance animation for the slide. For objects, it uses the traditional method, but cleans it up a bit so it's easier to just click and object and select an animation and its type. Also, add animation variety from slide-to-slide in the wizard by adding “animation themes” with pre-set animations that vary each slide. Themes should include their own pre-set animations that can be turned on or off with a checkbox and vary from slide to slide, as well as match the theme. If it's a business-like theme, include conservative and simple animations. If it's a party theme, include crazy and cool animations.


Make the menubar, multibar, custom toolbar, and draw bar the same as I suggested for Writer, and youv'e got something simple and powerful. Again, look to Google. They're really going the right direction by adding features while keeping things simple enough for anyone to easily use and figure out. I am, by no means, saying just copy Google, I am saying use their ideas as a starting base and configure it to work with OpenOffice like it was meant for OOo in the first place. Don't forget the little conveniences that make life easier.

---

### Post by rubinstein on 2008-03-30
Have a look at [http://ux.openoffice.org/](http://ux.openoffice.org/) , that should be the right place to participate.

---

### Post by plun on 2008-03-30
Well, Ubuntu is really downstream....:)

OpenOffice development
[http://projects.openoffice.org/index.html](http://projects.openoffice.org/index.html)

Roadmap for O-O 3.0
[http://wiki.services.openoffice.org/wiki/Product_Release](http://wiki.services.openoffice.org/wiki/Product_Release)

So its just to go upstream and work with the O-O project.

---

### Post by olskar on 2008-03-31
OpenOffice is using Java right? It would propably be both betterlooking and less resourcehungry if it was using gtk..

---

### Post by qamelian on 2008-03-31
> **olskar said:**
> OpenOffice is using Java right? It would propably be both betterlooking and less resourcehungry if it was using gtk..
No, OpenOffice uses java for some functionality, but will also run just fine for most purposes if you tell it not to use java at all. Java is not used in any sense to draw the UI, or for any critical part of any of the apps in the suite.

---

### Post by Redrazor39 on 2008-03-31
Wow, this is amazing! There's so much to do! The only problem is, I can come up with ideas and stuff, but I am very bad at mockups and I don't know any code (I want to learn code, though, I just don't know where to start, what kind to learn, etc.)

---

### Post by softtower on 2008-04-04
This is amazing... they're planning on a bunch of new features while they still can't get the basics right: USE THE ******* SYSTEM FONT RENDERING! OpenOffice is the only application I have that ignores my font settings and uses it's own ugly and useless renderer.

---

### Post by Lord Illidan on 2008-04-04
> **softtower said:**
> This is amazing... they're planning on a bunch of new features while they still can't get the basics right: USE THE ******* SYSTEM FONT RENDERING! OpenOffice is the only application I have that ignores my font settings and uses it's own ugly and useless renderer.

You will be pleased to know that this is fixed in [Hardy]("http://ubuntuforums.org/showthread.php?p=4651647"). 

And personally, I agree with the OP's comments. There are a lot of useless options that can be removed, and a lot of bloat that should be removed.

Word 2003 (with wine) loads up faster than OpenOffice writer on my machine. And it's using wine, an extra layer.

Impress is particularly bad in my opinion. Only now in 2.4 have they added an easy way to add a picture as a slide background. This is something which should have been done from the beginning, not bolted on. I'm also saddened that the main new "feature" in 2.4 is going to be 3D OpenGL transitions. Yes, cool, eye-candy, and keeps your audience awake.

Of course, the problem is..that if your audience is awake, it's because of the content of your presentation. No amount of transitions will change that.

---

### Post by Redrazor39 on 2008-04-04
I sent an e-mail with all of this to the OpenOffice devs and they said "Thank you for your suggestion. We are currently working on a new UI for OOo 4.0" and that there would be some mockups late this year. 4.0 is due out in late 2009

wtf... Microsoft and Apple totally win on this one... they fixed all the problems OOo has years ago!

---

### Post by qamelian on 2008-04-04
> **Redrazor39 said:**
> wtf... Microsoft and Apple totally win on this one... they fixed all the problems OOo has years ago!
Well, that's your opinion. Personally, I'll take the current OOo interface over anything Microsoft or Apple currently offer, especially compared to the awful interface in Office 2007.

---

### Post by skiwithpete on 2008-04-06
I think Lotus Symphony probably has the nicest interface, but realistically, why can't OOo be skinnable like Winamp?  I mean skins, plugins, addons... they are the key to programs like Firefox...  soon they'll find their way into OOo.

---

### Post by buried on 2008-04-07
I personally think the Office 2007 interface is more "nostalgic" and web 2.0, OOo seriously needs to work quick cuz there will be a MW Office 2009 too.

---

