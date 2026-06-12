---
title: "An app I would like to see"
date: 2006-11-02
forum: The Cafe
---

### Post by Sushi on 2006-11-02
Some time ago (actually, about exactly a year ago) I had an idea about an app. I even wrote a blog-entry about it (not the blog in my sig). I recently re-read the blog-entry, and I think it's still valid today. I'll just re-post the idea here to hear your opinions :).

Few things: the text is KDE-specific, but I can't think of any reason why it couldn't work elsewhere as well. You will notice the word "Plasmoid" in the text. Plasmoid is a tiny app that lives on the desktop. Think of it like Dashboard-widget, or SuperKaramba/gdesklet-thingy.

=========================

**The Desktop is The Application**

Why do we use separate apps to carry out simple, everyday tasks? Couldn't there be a simpler way to carry out those tasks? What I'm proposing is somewhat radical, yet very simple in everyday use. Namely: The Desktop is The Application.

More detailed description: How do we use our systems these days? What do I do when I decide to type and send a mail to someone? Well, after I have decided that I want to send some mail, I launch Kmail/Kontact. Using the app I then type the mail, and send it. But why do I need to launch a whole app just for something as simple as that? What if I want to read some website? I launch Konqueror. What if I want to copy some files around? I launch Konqueror. And so forth. Do I really need separate apps to do those tasks?

What if we had a plasmoid in the desktop that allows me to do those tasks, without having to launch separate apps to do them? Allow me to clarify:

The plasmoid would consist of a textbox (similar to location-texbox in Konqueror). Next to the textbox would be an area for handful (3-5 at most) of buttons that could be used to carry out the task. Underneath the textbox would be an area for actually carrying out the task. And that's it.

How could I use that plasmoid? Well, I could type an URL in to the textbox (either in the web, or in the filesystem). Contents of that URL would be displayed in the area underneath the textbox. The control-button in browsing-mode could be Back, Forward, Up and Home (for example). Or if I wanted to send an email, I could simply type the address of the recipient, and I would then get a text-area underneath the textbox where I could type the message. The control-buttons could simply be (for example) "Send" and "Attach". Additional buttons aren't really needed for everyday mailing. The app could also be used to read mail, but I'm still working out the details of
that :).

As you propably noticed already, the capabilities of the plasmoid would be limited. But it would still allow the user to carry out most everyday tasks, without having to launch separate apps to do those tasks. If the user wants more features, the full-blown apps would still be available.

Now, why have something like this? Well, not all users need all the features Kmail, Konqueror etc. offer, so having an simple alternative would be ideal. Also, since the user doesn't have to launch separate apps for his tasks, it helps keep the system tidy and manageable. Didn't David Faure say that no-one wants to do windowmanagement? Well, in this case, no windowmanagement is required, because the desktop is the application :). The app is always there, right on the desktop. If the user wants to quickly do something, he could do it right in his desktop, without having to launch separate apps. Also, every time we introduce new apps to users, we require him to learn new stuff. That would not happen with this proposal, since there would be no apps to learn really.

Of course, the user could run as many of these plasmoids as he sees fit. But the fact remains that one plasmoid could only be used for one task at a time. So the user couldn't really surf the web and write an email at the same time, using the same plasmoid. But this system is not meant for something like that, this is meant for quick and simple tasks. Of course, the user COULD use the plasmoid for his primary email-client, and he could use it as his primary web-browser (for example). But then he would lose some of the advanced features Kontact and Konqueror offer (tabs etc.). Although in case of email, all the filters the user has set up would still be applied to messages. And typing email-addresses could be automatically looked up from the Kaddressbook etc. those things wouldn't really make the app more complex to use. But the plasmoid would not have any way to configure options related to those features for example, since that would make the app more complex than it needs to be.

The examples I have mentioned (web-browsing, email, filemanagement) are simply a tip of the iceberg. Developers could simply write plugins that added functionality to the plasmoid, like they do now with KIO-slaves. I could see the plasmoid being used for playback of music and video, and doing some simple text-editing.

=====================

Does it make sense?

---

### Post by nbound on 2006-11-02
Sounds like a good idea for mobile devices... 

For a desktop... meh... if u want it... i prefer my full blown customisable apps.. my computer is easily fast enough to run them (despite being bloated). And i like to use several apps at once.

---

### Post by Sushi on 2006-11-02
> **nbound said:**
> Sounds like a good idea for mobile devices... 

For a desktop... meh... if u want it... i prefer my full blown customisable apps.. my computer is easily fast enough to run them (despite being bloated). And i like to use several apps at once.

You could use several apps at once. And the point is not as much the performance-hit of "large" apps, it's the tediousness of using them. What if you want to check some website? You could click "Applications", select "Internet" and select Firefox, and the proceed to type the URL. Or you could click the Firefox-icon in the tob-bar on the desktop and then type the URL in the textbox. Or, you could just type the url and be done with it.

Why should we click around to launch separate apps to do simple tasks. Why should we wait around while the apps load (even though it might just be few seconds). Why not simply _do_ what you want to do? Why would I have to locate and load Evolution, locate the "New Mail"-button, type the address and the mail, and then send it. Why not simply typing the recipient and the mail and sending it? Why do I need a full-blown email-app for something like that?

And: the full-blown apps would still be there. No-one is going to take them away.

---

### Post by nbound on 2006-11-02
> **Sushi said:**
> You could use several apps at once. And the point is not as much the performance-hit of "large" apps, it's the tediousness of using them. What if you want to check some website? You could click "Applications", select "Internet" and select Firefox, and the proceed to type the URL. Or you could click the Firefox-icon in the tob-bar on the desktop and then type the URL in the textbox. Or, you could just type the url and be done with it.

Why should we click around to launch separate apps to do simple tasks. Why should we wait around while the apps load (even though it might just be few seconds). Why not simply _do_ what you want to do? Why would I have to locate and load Evolution, locate the "New Mail"-button, type the address and the mail, and then send it. Why not simply typing the recipient and the mail and sending it? Why do I need a full-blown email-app for something like that?

And: the full-blown apps would still be there. No-one is going to take them away.
They are all valid points... and many desktop uses may agree with you... but i do like my large apps very much, i dont want another widget on my desktop, its not like current apps are out of reach... anything i use often is in the top bar or system tray (Firefox, Evolution, Home Folder, Synaptic, Beryl Settings, Power Status/Settings (for laptop)).

On a mobile device.. yes lightweight apps on demand is great... on a desktop... not so much

---

### Post by Sushi on 2006-11-02
> **nbound said:**
> They are all valid points... and many desktop uses may agree with you... but i do like my large apps very much, i dont want another widget on my desktop, its not like current apps are out of reach... anything i use often is in the top bar or system tray (Firefox, Evolution, Home Folder, Synaptic, Beryl Settings, Power Status/Settings (for laptop)).

But the point stands. You still need to launch the app, you still need to operate it's UI. That could be minimized.

That said: I'm not forcing you to like the idea :)

---

### Post by glotz on 2006-11-02
I think you could try to sell the idea or at least the slogan to Google or Microsoft. They both seem to be interested in developing new integrated desktops at the moment...

---

### Post by skinny on 2006-11-02
I would still use the big-*** full blown apps largely. However, for some repetitive type tasks I reckon it would be a really good thing. Kind of like slicing through the task instead of climbing it slowly (CLI-ish in your idea's example, and GUI-ish for the full apps).

One problem is that people like full blown apps because it affords them laziness. No typing, or very little, and no having to remember website and email addresses, just point and click sort of stuff.

Seems like a good idea, I just don't know quite where you'd go with it.:-k 

$

---

### Post by GeneralZod on 2006-11-02
Seems pretty cool to me.  In fact, if the full-blown apps are allowed to be running at all times, then this is probably possible right now armed with just Superkaramba/ GDesklets and dcop/ dbus.  Otherwise, the apps would have to be very well factored so that just small parts of the functionality (sending an e-mail to one of your contacts, for instance) could be quickly loaded, executed, and dumped.

---

### Post by Sushi on 2006-11-02
> **GeneralZod said:**
> Seems pretty cool to me.  In fact, if the full-blown apps are allowed to be running at all times, then this is probably possible right now armed with just Superkaramba/ GDesklets and dcop/ dbus.  Otherwise, the apps would have to be very well factored so that just small parts of the functionality (sending an e-mail to one of your contacts, for instance) could be quickly loaded, executed, and dumped.

True. the various services (for example, addressbook-lookup, sending email, spam-filtering) would need to be split in to libraries and services which could then be used by other apps.

---

### Post by kuja on 2006-11-02
I keep most things of this nature in the background, it works pretty well. I load KMail into my tray on login. I also keep 3 copies of Konqueror preloaded, with at least one copy preloaded at all times.
Result: Konqueror comes up in about 1/4 second, maybe less. Kmail is right there, it comes up even faster. That removes the load time argument :)

---

### Post by PatrickMay16 on 2006-11-02
> **Sushi said:**
> And the point is not as much the performance-hit of "large" apps, it's the tediousness of using them. What if you want to check some website? You could click "Applications", select "Internet" and select Firefox, and the proceed to type the URL. Or you could click the Firefox-icon in the tob-bar on the desktop and then type the URL in the textbox. Or, you could just type the url and be done with it.

Then in that case it would only be about two seconds quicker for most modern computers.

This idea doesn't benefit web browsing at all, but the email feature sounds good.

---

### Post by bastiegast on 2006-11-02
In fact I think your idea is the end result of apps like karamba. Its obvious someone will write a plasmoid to do some mailing, or music listening. Someday people will merge them in one plasmoid and there you have your app.

Still its hard to make this. What if, for example i am writing a mail and i want to add a attachement. Damn.. its not possible, i have to launch Evolution anyway. 

Of course a feature like this is easily implemented, but what im trying to say is that its hard to say what feature is included in the plasmoid and what not. different people use different utilities. Telling people: Hey use this for everything is not going to work I think.

---

### Post by Sushi on 2006-11-02
> **bastiegast said:**
> Still its hard to make this. What if, for example i am writing a mail and i want to add a attachement. Damn.. its not possible, i have to launch Evolution anyway. 

What makes you think it's not possible? My original proposal said this:

> Or if I wanted to send an email, I could simply type the address of the recipient, and I would then get a text-area underneath the textbox where I could type the message. The control-buttons could simply be (for example) "Send" and "Attach".

> Telling people: Hey use this for everything is not going to work I think.

What makes you think that users would be told that? The full-blown apps would still be there, no-one would take them away, no-one would be forced to use the "little app that could".

---

### Post by EdThaSlayer on 2006-11-02
Thats quite a good a idea.You really have thought about this. Why dont you start development?But i guess that most users like to have these advanced programs so that they are sure that a site will support that browser. Also there are quite a few of us that have computers that can actually start up kmail and all of those other applications fast enough. This is a great idea for mobile devices, especially for people with few requirements(i love the idea that the buttons change and such when going from webbrowser to mail client mode).Anyways-thumbs up! Could become useful in the future when all of us will have touch screens and such!

---

### Post by Sushi on 2006-11-02
> **EdThaSlayer said:**
> Thats quite a good a idea.You really have thought about this. Why dont you start development?

I would if I could. But I have zero programming-skills.

> Also there are quite a few of us that have computers that can actually start up kmail and all of those other applications fast enough.

Speed is only part of the equation. Those apps take up space on the screen. They have UI's with multiple buttons. They are windows that require windowmanagement (usually by the user, who drags the window around), they take up space in the taskbar etc. etc. I maintain that we do not need all that.

The idea is that instead of focusing on the running and using the app, the user could focus on actually doing the task he wants to do. If we want to write an email today, our first task is to launch the relevant app (Evolution, Kontact etc.). We then use that app's UI to accomplish our task. What I would like to see is to bypass all that, and just focus on accomplishing the task.

Apps are merely a means to the end. I want to bypass the means and go straight to the end :)

---

### Post by bastiegast on 2006-11-02
> **Sushi said:**
> What makes you think it's not possible? My original proposal said this:


It was an (maybe bad) example, of course adding an attachment is easy to implement, but as i said its about some people would like to see one feature in theyre mini email client and others want another. Think of spell checker, some people want a bar where they can choose fonts and color, others only want a send button, you feel me? 

> **Sushi said:**
> 
What makes you think that users would be told that? The full-blown apps would still be there, no-one would take them away, no-one would be forced to use the "little app that could".

I am sorry if you misunderstood me, I only meant to say I doubt people would use the app.

---

### Post by Erik Trybom on 2006-11-02
I like the idea of not having to launch a large memory-consuming application for doing a simple task.

I don't like the idea of using my desktop for anything. Switching to an application requires only a click, while switching to the desktop requires minimizing all open windows.

I think the answer would be a "quick task"-panel for doing simple things. You click the "quick task" button, then select "note", "mail", "web browser" etc. For each of these tasks there is a small app that does what you want and nothing else. 

I do realize however that most people don't share my negative view on the desktop.

---

### Post by Sushi on 2006-11-02
> **bastiegast said:**
> It was an (maybe bad) example, of course adding an attachment is easy to implement, but as i said its about some people would like to see one feature in theyre mini email client and others want another. Think of spell checker, some people want a bar where they can choose fonts and color, others only want a send button, you feel me? 



I do. Few points: Email is email. most people just send plaintext email (at least, they SHOULD). Most people don't change fonts or colors. Many people do send attachments. We should define what are the bare minimium an app should do when sending email, and implement that, and nothing more. Fonts and colors do not fit that. Attachments do.

Some people might just want send-button. But having "send" and "attach" shouldn't be too confusing for them ;).

As to spell-checking... Well, in KDE spell-checking is system-wide service that any app can use. So in KDE at least this app would get spell-checking for free.

---

### Post by Sushi on 2006-11-02
> **Erik Trybom said:**
> I don't like the idea of using my desktop for anything. Switching to an application requires only a click, while switching to the desktop requires minimizing all open windows.

You do have the "show desktop"-button?

---

### Post by Steveire on 2006-11-02
You want plasma:
[http://plasma.kde.org/cms/1029](http://plasma.kde.org/cms/1029)
That means waiting on kde4, and possibly feisty+1 (intrepid ibis).
[http://aseigo.blogspot.com/2005/06/wonderful-support.html](http://aseigo.blogspot.com/2005/06/wonderful-support.html)

---

### Post by Sushi on 2006-11-03
> **Steveire said:**
> You want plasma:

My proposal was originally aimed at KDE4 and Plasma (hence, the "plasmoids").

---

### Post by mssever on 2006-11-03
> **Sushi said:**
> Some time ago (actually, about exactly a year ago) I had an idea about an app. I even wrote a blog-entry about it (not the blog in my sig). I recently re-read the blog-entry, and I think it's still valid today. I'll just re-post the idea here to hear your opinions :).

Few things: the text is KDE-specific, but I can't think of any reason why it couldn't work elsewhere as well. You will notice the word "Plasmoid" in the text. Plasmoid is a tiny app that lives on the desktop. Think of it like Dashboard-widget, or SuperKaramba/gdesklet-thingy.

=========================

<snip>

=====================

Does it make sense?

I think that this would be better implemented as a web app, that way it can be truly mobile and cross-platform, as well.

This is pretty much how I use my computer now. I have Firefox open on one desktop with multiple tabs (e-mail, etc.). A quick ^T pops up a new tab any time I want it. IMO Gmail has the best e-mail interface out there, so I don't have any use for a desktop mail client, anyway.

On other desktops, I have terminals and perhaps OpenOffice documents. If there was a good web-based Office suite (Google's doesn't cut it for me), then I could do almost everything in one place already: Firefox. (Although it would be nice to figure out how to run a terminal there, too.)

The other issue with desktop apps (and one I have with GDesklets, too) is that they tend to get covered up and you can't Alt+Tab to them. When I want to work efficiently, I have lots of maximized windows open and spread across all four desktops. So I don't have to start anything; I only have to switch to it.

---

### Post by theboatashore on 2007-08-04
I think this a fantastic idea, more for the email function than anything else.  I often send links/images/etc. and don't include any other text in the message.  I'm not writing an email, just sending an idea.  Attachments could just be dragged onto the plasmoid (or applet).  A small text area is perfect for pasting a URL, or writing a short bit of text.

I don't think the arguments about how quickly your mail client opens are relevant.  One of the main advantages of using Linux is that it runs on older, slower machines, which many people outside of North America and Europe still use.  For them, firing up a full blown app may take longer than actually sending the message.

Often, all I want to do is add a few words (or URL), write recipient address (autocompleted by kaddressbook), press Send.

I love this practical and efficient idea and would use it all the time.

---

