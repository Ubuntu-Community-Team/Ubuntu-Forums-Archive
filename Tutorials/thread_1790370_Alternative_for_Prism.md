---
title: "Alternative for Prism"
date: 2011-06-24
forum: Tutorials
---

### Post by arvevans on 2011-06-24
When I upgraded to Ubuntu 11.04 it forced removal of "prism" which I had been using to make local executables of on-line web applications.  During the Synaptic based upgrade to the latest Firefox I also lost the add-on that allowed Firefox to make locally executable applications from on-line web URLs.

Not wanting to back-port prism, and not wanting to go back to an older version of Firefox I decided to see of there was some other way to make web-based applications become click-able applications via my local menu.

Turns out that it is fairly easy.  Using the browser, go to your desired web based application page and copy it's URL by highlighting the URL and hitting CTRL-c.  Then open the menu editor at /System/Preferences/Main_Menu.  Select the base menu where you want your new application to be listed, and open a "New" menu item at that level.  In the "Command" section enter *firefox*, followed by a space and then use CTRL-v to enter the URL that you just copied from it's web page.
Then clean up with niceties like a descriptive name for your new application and a longer description of what it does.  Save this new menu entry and you now have your own web-based application that can be executed by clicking on it as an entry in the Applications menu.

This is essentially the same as what was previously done using prism or the remote application tool of older Firefox versions.  Difference is that now you are in control of how it works and can build your own versions of particular on-line applications whenever and however you want to do it.

---

### Post by arvevans on 2012-05-16
BUMP

Same problem still present in later upgrades of Ubuntu.  I'm now running 12.04 and still no prism or similar support for executing on-line applications.  Apparently the upgrade managers have not yet discovered "Cloud Computing" as a direct augment to local applications on one's own computer.

The only work-around at present seems to be making a menu editor entry that calls something like "firefox [some_web-based_application]", but this also has the problem of the web based application going away or my not being connected to the web, and thus the application cannot be called because it is not previously downloaded to my computer.

There is possibly a work-around for some of these on-line operations:
Use the "wget" command to rip the application from it's place on a web server and save that in HTML form on your own computer.  Then you may have to re-arrange any internal calls that were web-based...and the application might be callable from within your own computer.

Seems it would be so much easier and way more productive if Ubuntu would just bring back the "prism" command that worked so well for this purpose.

---

### Post by overdrank on 2012-05-16
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

