---
title: "Web Applications and Modern Desktop Environments"
date: 2011-05-01
forum: The Cafe
---

### Post by aaaantoine on 2011-05-01
So it shouldn't be a surprising concept to anyone that the web browser has become more or less its own operating system, to the point that Chrome OS is trying to fill that role to the extreme.  However, many of us still use native applications on top of the web browser.

Tabbed browsing was a great concept that took off in mainstream web browsers, but I think that web browser developers should start thinking about using the native desktop environment again, and doing so more intelligently.  Here are some ideas on how one browser developer might reach that end.

1. Keep a "general" browser for various navigation activities.  This general browser would utilize the default behavior of your browser of choice.
2. Allow the user to select favorite web applications (Firefox kinda has this, but it essentially acts as a tiny, label-less, uncloseable tab).  These applications, instead, will show up in the applications view of your desktop environment, and when opened will be given their own application group apart from your web browser.
3. For these favorites, completely minimize the web browser interface itself.  No tab bar by default.  Other things can be hidden since this window is meant specifically for a single instance of a single web application.  Something worth giving more thought to.
4. For these favorites, the window icon should default to the favicon of the website, and only use the browser icon when the favicon isn't available.
5. Any link that navigates away from the favorite app should open as a new tab in the general browser.
6. Any new views of the app should also open in a separate window, but be arranged in the same application group by the desktop environment.

I'd like to experiment with trying to eliminate tabbed browsing from both my desktop and my laptop, but I have a feeling it would only really work if #4 and #6 were implemented.

See also:
[http://askubuntu.com/questions/4304/how-do-i-put-web-applications-in-my-unity-launcher](http://askubuntu.com/questions/4304/how-do-i-put-web-applications-in-my-unity-launcher)

---

### Post by aaaantoine on 2011-05-02
I still can't shake the habit of using Tabbed browsing. Maybe it's not as flawed as I'm suggesting. :P

Let me try a different approach.  When my mother-in-law starts using Unity next year, she's only going to have any combination of the following windows open:

1. A web browser
2. A word processor.
3. A file manager, or a photo album.

So, what a waste of launcher space.  What about adding launcher for Facebook? A launcher for Hotmail?  Not only allow them to act as shortcuts, but also bring the appropriate open windows and tabs into focus when clicking the launcher.

How about allowing a user to switch between tabs the same way a user switches windows from the same application group -- by clicking the task twice?

I hope Unity can support these sorts of things going forward.

---

### Post by spillz on 2011-05-04
> **aaaantoine said:**
> What about adding launcher for Facebook? A launcher for Hotmail?  Not only allow them to act as shortcuts, but also bring the appropriate open windows and tabs into focus when clicking the launcher.

I like this. No idea if support for this already exists within Unity (or Gnome 3 for that matter), but with the right set of hooks into the brower it seems like it would be relatively straightforward to implement via DBus.

---

### Post by juancarlospaco on 2011-05-04
Native applications ARE Web Applications.

Hotot include a Webkit, Gwibber include a Webkit, Empathy include a Webkit, 
Evolution will include a Webkit, Software-Center  include a Webkit  (...)

---

### Post by lboorse2 on 2011-05-04
I like where you are going with this.  I especially like the launcher examples you gave for Facebook, etc.  This is absolutely not unlike an Android or iPhone.  Smart phones, in my opinion, are a small glimpse into the future of desktop computing for consumer users.  

In the business environment though, I think something different will happen and it will absolutely require the browser to be present at all times.  Software as a Service, cloud computing, virtualization, etc, will eventually turn the desktop PC into a dumb-terminal more-or-less.  Think netbook (sort of) running all the powerful business apps direct from a server.  

While data center managers are focusing now on virtual servers and lowering costs to run the data center, the general business IT world will be looking at how they can expand on this savings... 

I see a move away from client/server computing and moving to something that vaguely resembles old-school mainframe computing.  The browser (or some similar portal to your desktop/commonly used apps) will be central to this.

---

### Post by Copper Bezel on 2011-05-04
> I see a move away from client/server computing and moving to something that vaguely resembles old-school mainframe computing. The browser (or some similar portal to your desktop/commonly used apps) will be central to this.
So the real question is, what have you been doing in my nightmares, then? Christ, the moment it's no longer possible to *own* my computer, I'm going back to a quill pen.

But yeah, while tabbed browsing isn't going anywhere anytime soon - I do see it moving even further toward treating tabs as separate windows, and I understand that Explorer 8 under Windows 7 already implements a bit of this, with separate entries in the Superbar window list, but not at the cost of any of the tab management features we hold dear - I do think the idea of giving cloud-based webapps a little more recognition in the desktop environment is a good one, especially if it's a user-configured feature of a particular browser. It would require some involvement on both ends, though; the webapp in question would have to have some way of signalling its identity to the browser. The domain name isn't going to do it, and you could end up with a browser window without any navigation features stuck at some random page until it's restarted.

---

### Post by jerenept on 2011-05-05
chromium-browser --app=facebook.com

---

### Post by Thewhistlingwind on 2011-05-05
> **Copper Bezel said:**
> So the real question is, what have you been doing in my nightmares, then? Christ, the moment it's no longer possible to *own* my computer, I'm going back to a quill pen.

Seconded. Seriously. I think that'll take some of the casual users, but some things are just really intensive, (We don't have that kind of bandwidth.....) and there will always be a product around for hobbyists. I guess if I'm wrong, I'll just retreat to the mountains, and come back when the consumer stops caring about new apps because the hackers that normally make them suddenly drop in quality and quantity.;) (Then we'll have a lack of programmers AND engineers.)

---

### Post by spupy on 2011-05-05
> **jerenept said:**
> chromium-browser --app=facebook.com

This is awesome. In the latest versions of Unity the launcher doesn't confuse the Gmail window with chromium windows even though they are the same program. In my **net**book almost all of the launchers are links to web apps.

---

### Post by aaaantoine on 2011-05-05
> **jerenept said:**
> chromium-browser --app=facebook.com

I tried this but it just opened a default Chromium window.  On the other hand...

chromium-browser --app=http://www.facebook.com

...works.

---

### Post by lboorse2 on 2011-05-05
> I see a move away from client/server computing and moving to something that vaguely resembles old-school mainframe computing. The browser (or some similar portal to your desktop/commonly used apps) will be central to this.

I was speaking strictly to business environments with that statement.  I apologize if I wasn't clear in the direction I see consumer computing going vs. business computing.

---

### Post by Copper Bezel on 2011-05-05
No, I could see that, but I think that's available to businesses (on-site) without the browser base and without moving everything into webapps. A multiuser blade bank, some thin clients, and the option of leasing some cycles on the cloud for temporary scalability seems to get the benefits without the hassle. Moving to a system where you can log onto your work machine from anywhere creates the problems of having a system where people can log onto your work machine from anywhere. = )

I could see it happening with consumer electronics, though, if the broadband infrastructure existed. If you have devices that act essentially a cloud-based thin clients, then you don't have to sync between your phone, slate, desktop, and television; it's all more convenient than even Motorola's Atrix docks or something. I just don't like it. = P

The Chromium webapp launcher is kind of cool, although it illustrates the central problem with doing this under normal circumstances: the window has to have an identifier that differs from the browser's normal one so that the panel or dock can tell them apart.

---

### Post by lboorse2 on 2011-05-06
Good point (regarding the business side).  I wasn't looking at it from the point of view of where you could access your desktop from, I was looking at it more from the point of view of the equipment at the user's desk.  Why have a full blown laptop or desktop, when #1 you already don't want people risking file loss by saving stuff on their local hard drives and more importantly #2, when you can have all of their apps running from the server.   

Their "PC" crashes completely (or thin client or similar type of futuristic device), they call the helpdesk and their computer is replaced within 10 minutes with a basic piece of $100 hardware and back to work they go.

---

