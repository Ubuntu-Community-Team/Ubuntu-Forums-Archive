---
title: "make thunderbird  subject line larger"
date: 2016-10-19
forum: Ubuntu, Linux and OS Chat
---

### Post by rosswmcgee on 2016-10-19
I would like to make the thunderbird email subject line easier to read. Nothing I have found seems to address it. I am using 45.3.0 in ubunutu 16.04 lts. One computer has a very small subject

line the other is a bit better.

---

### Post by SeijiSensei on 2016-10-19
You can put the mouse on the divider at the right-hand end of the Subject column in the header row.  The cursor will become a two-headed arrow.  You can then expand the size of the field just as you would with a spreadsheet.  You can use the same trick to shrink the space allocated to the list of folders in the left-hand pane if needed.

---

### Post by rosswmcgee on 2016-10-20
It is not the field I want to expand it is the size of the message line. For instance say you get a message" U.S. headed to recession"and you look at it but it is to small to read.

thanks for your reply.

---

### Post by SeijiSensei on 2016-10-20
[https://addons.mozilla.org/en-us/thunderbird/addon/theme-font-size-changer/](https://addons.mozilla.org/en-us/thunderbird/addon/theme-font-size-changer/)

---

### Post by rosswmcgee on 2016-10-21
I have that installed on Tbird but do not know how to use it. Thanks for the reply.

---

### Post by SeijiSensei on 2016-10-21
I honestly don't know either.  It doesn't show up in the Tools menu the way the documentation claims it should even after restarting Thunderbird.  Maybe you should drop a note to the developer: [http://barisderin.com/?p=287](http://barisderin.com/?p=287)

---

### Post by Quarkrad on 2016-10-27
You could dive into the world of css codes - this would allow you change all sorts of things in the various Thunderbird panes.  I have been playing with the code below and changed my email subject fonts sizes - it does work.  The code will change the font size of the email subject titles - however, if you make the font too large they will start to cross over each other.  So, you to have to have another line that will increase/decrease the line spacing between them.  First go to your *./thunderbird* folder, (it is a hidden folder in your *home* folder).  You will see a folder in there called* xxxxx.default* (where xxxxx will be letters and numbers - this is your Thunderbird profile folder).  Open that folder and create a new folder called *chrome*. Open your new chrome folder and copy/paste my attachment into the chrome folder.  Now change the name of the file to* userChrome.css*.  Now you can start to experiment - close down Thunderbird and open the userChrome.css file.  On the third line the font size is set to 18pt - change this to 8pt and save the file.  Open Thunderbird and you will see the change - at this point close Thunderbird and re-open the userChrome.css file and play with the font size until you are happy with it.  If the font is too large you may get the cross over between messages so will have to increase the line spacing.  Open the userChrome.css file and change the 6px number on the 6th line to something else.  You can have negative numbers here so you could have a number such as -4px. Thing is - have a play and see what happens - the only thing to remember is Thunderbird has to be closed when you make changes to the .css file and then re-launched to see the effect of the change; also, don't forget to Save the .css file every time you make a change.   This may sound rather complicated but one you have set up your userChrome.css file you can change all manner of things like font sizes, colour, in all sorts of panes.   It is good fun - there is a whole new world of css coding out there.  If you really mess up just delete your chrome folder you originally created.

---

### Post by rosswmcgee on 2016-10-30
Boy you really figured all that out and deserve praise and thanks for it. However it is more of a task than I wish to take on. I  will just live with it or use a different  email application. Thanks again.

---

### Post by Quarkrad on 2016-10-31
I understand your view - when I first stumbled on css coding fear struck my heart (my mother-in-law has poor eye sight and needed the text made larger in Thunderbird).  Trouble was, making the whole page larger did not help as 'things' went off screen.  Somehow I needed to make the text in some panes larger, but keep the overall page dimensions the same.  No 'third party' add-ons really solved the issue.  Hence I dived (a little bit) into  css.  It looks demanding/challenging at first but when you have a go you realise it is actually easy.  A few lines of text in a file.  If things get messed up all you have to do is delete the chrome folder - so the potential damage you could do is actually quite small. If you have a go I'm sure you will not regret it - I consider myself a novice when it comes to Linux - my mother-in-law is now very happy she can read her mail with ease.

---

