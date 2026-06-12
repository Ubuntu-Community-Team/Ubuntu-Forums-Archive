---
title: "OpenOffice has a serious problem with formatting."
date: 2007-11-24
forum: The Cafe
---

### Post by Palmyra on 2007-11-24
This is not a support thread.  This is just a thread to talk about the problems facing OpenOffice with formatting.  

1.  When I save files as either ODT or DOC at home using Ubuntu, and try to print them at work using XP, the formatting completely changes.  I like my text justified, but when I open the file at work using the same software (OpenOffice Writer at home and work, just different operating systems), spaces are created, and many other things are off.  It is no longer justified.  

2.  The font changes from home to work.  I am using one font at home, and the font changes to, I think, Times at work.  It makes no sense.  Yes, I realize you may say that I don't have the same font at work, but I am using the very same application with default fonts (like I said, I am using Writer at home and work).  

3.  When turning text into a list, numbers are inserted into spaces between the sentences on different lines.  Here's a shot to capture this:

[[IMG]http://img231.imageshack.us/img231/6016/openofficelistki2.th.png[/IMG]](http://img231.imageshack.us/my.php?image=openofficelistki2.png)

Notice the numbers *between* the questions.  I don't want blank lines to be numbered, just the questions.  

4.  There are other problems, such as text disappearing, until I scroll up and down.  

It's all bizarre.  I haven't used Word in a while so I don't know if it has the same problems, but that's irrelevant.

---

### Post by Scunizi on 2007-11-24
There does seem to be a few screen related issues.  I too have to scroll up or down to remove artifacts that show up on the screen.  

As for doing a list, I haven't had a problem.  However, when I make the list I first type everything out, hitting enter only at the end of each list item.  I then highlight what I want to turn in to a list format and click the list button.  List will automatically do the spacing for you.  The numbers in the blank space between each list item on your screen capture leads me to think that you're entering a blank line between each item.  "List" can't tell if you didn't want a number there or not.  If you try it my way and you don't have the spacing you want between each item, highlight and change the formatting of the paragraph.

Although you use the default font configuration on install there may still be a font difference between WinXX and Ubuntu.  Check your preferance default for both systems and match them.

Some formatting will not interoperate between Word & OpenOffice.  From Open Office to Open Office formatting should remain the same.  If it doesn't you might want to ask on IRC #openoffice on the irc.gimp.org server.

---

### Post by DeadSuperHero on 2007-11-24
Ironically, it saves just fine for .doc for me. I'm not sure why.
On another note, we need to get more office suites to support ODT. MSOffice still doesn't really, I think.

---

### Post by TeaSwigger on 2007-11-24
That's why .pdf files have the capability of embedding fonts. pdf and ps files (among others) are intended for consistent printing, even across platforms. 

doc, odt etc are word processor formats, for word processing. Not for consistent printing. That isn't to say one can't do so, only that one has to manually assure consistency. If you have a page of text wherein formatting is pertinent to relative spacing (such as end-of-lines), odds are pretty long that your formatting will be affected if fonts are changed. One certainly can't take a text using default Linux fonts and rendering, open it in Windows with default Windows fonts and rendering, and expect relative formatting to match. You have to insure you use consistent fonts and account for rendering etc.

There are some odd display bugs in OpenOffice in Windows, I've seen them too. But I haven't seen these issues in OpenOffice in Linux. Do you see it in both? If not, the issues just might lay with... MicroSoft.

It isn't that you're using the same app in a version for each respective platform, the trouble lies in the differences between the platforms. OpenOffice can only do so much to be compatible across platforms. It's a heck of a lot more effort and consideration than MS is lending the matter.

If this bugs ya though, try authoring web pages! arr.

---

### Post by yatt on 2007-11-24
Try Abiwork or KOffice and see what happens. I try not to use OOo as much as possible.

---

### Post by rune0077 on 2007-11-24
I save Writer documents (in ODT format) from Ubuntu to my Vista drive quite often, then open them in Vista (also with Writer), and I have never noticed any issues (except when Ubuntu fails to write to NFTS and screws the file up, but that has nothing to do with OpenOffice).

---

### Post by mikewhatever on 2007-11-24
It looks like your Writer at work has auto-numbering or similar turned on, so that you get those extra numbers. The fonts are different by default simply because different operating system use different fonts. While you may, in time, find the solution to do things with Writer, or standards get unified across OSs, meanwhile, convert the documents you intend to print to pdf.

---

