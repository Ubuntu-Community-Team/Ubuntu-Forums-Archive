---
title: "HOW-TO: View man pages in the file manager"
date: 2011-11-21
forum: Tutorials
---

### Post by JKyleOKC on 2011-11-21
The original documentation for all Linux systems was a set of files collectively known as the "man pages" that formed a readily available manual describing the actions and options for each command. The command "man" followed by an optional section number and the name of the command for which information was desired brings up the "man page" for that command, allowing you to learn more about it.

Unfortunately in today's world, many of the man pages are so full of jargon that they seem incomprehensible to newcomers -- and even, at times, to long-time users of Linux. Still they are quite useful, especially for refreshing one's memory about details of a command not often used.

There's one major drawback, however: When you need to find a man page while at the command line, you must either open a second terminal window to issue the "man" command, or abort the action under way so that you can run "man" in the current window.

If, like many of us, you are using a terminal window from within your file manager (Nautilus, Dolphin, Thunar, etc.) or from a desktop launcher, there's an easy option. The purpose of this post is to show you how to use it, and how to install and configure a launcher that will make it even simpler to use.

This easy option is a program called "xman" that's installed by default with the X Window System. It does the same thing as the command "man" does from a terminal, but does so within its own window on the desktop, and includes a number of features to simplify its use. Since xman dates from the earliest days of the X system, it doesn't have all the eye candy of more recent desktop tools, and many of its actions are not at all intuitive, but despite this it's still one of the tools that I use daily. You may find it equally useful.

To get started with xman, open a terminal window and type ```
xman
```followed by the Enter key. You'll see this window appear in your display: [CENTER][[IMG]http://img195.imageshack.us/img195/385/xman1.png[/IMG]](http://imageshack.us/photo/my-images/593/xman1.png/)[/CENTER]

 This is the "top box" and simply guides you to the next step. Click the "Manual Page" button, and you'll get the default instruction screen: 
[CENTER][[IMG]http://img535.imageshack.us/img535/3461/xman2.png[/IMG]](http://imageshack.us/photo/my-images/535/xman2.png/)[/CENTER]

The way to find the page you need is to click the "Options" menu entry at the top left portion of this window, which will bring up the pull-down display: 
[CENTER][[IMG]http://img593.imageshack.us/img593/5678/xman3.png[/IMG]](http://imageshack.us/photo/my-images/593/xman3.png/)[/CENTER]

This is the point at which the action may seem unnatural, because the display remains visible only so long as you keep the mouse pointer inside this sub-menu, holding the left button down and dragging the highlight to the option you want. In this case, it's "Search" and when you release the mouse button, this dialog appears: 
[CENTER][[IMG]http://img839.imageshack.us/img839/6581/xman4.png[/IMG]](http://imageshack.us/photo/my-images/839/xman4.png/)[/CENTER]

In this dialog, you can type in the name of the command you want, or you can type in a word associated with the command in case you're uncertain of the correct command name. In that latter case, select "Apropos" after typing the word. If you know the command name, select "Manual Page" and the page will be displayed.

If you choose "Apropos" you will get a list of all the man pages related to your search word, with a brief description of each. You can then return to the "Search" dialog, enter the page name you found on the list, and view that page.

Navigating through the displayed man pages, or the apropos list, is a bit different also. The scroll bar cannot be dragged and the arrow keys do not work. However, you can scroll with the "page up" and "page down" keys, or with the mouse buttons but only when the pointer is in the scroll bar region. The left button moves the viewing window down the page, and the right button moves it back up toward the top.

The other menu item when viewing manual pages, "Sections," allows you to browse the eight "sections" of the manual that divide its content into user commands, administrative commands, and other types of information. These sections do not include all possible pages; they are limited to only those pages that apply to your specific system, and offer a quick way to determine whether a program is installed.

The "top box" that appears when you run the simple "xman" command isn't really very helpful, so you may want to use a launcher or alias that invokes xman with options that specify its screen location and skip past the top box. I've created a launcher on my top panel, with this command line: ```
xman -notopbox -pagesize 829x814-0-6
```Clicking that launcher brings xman up at the right-hand side of my monitor, scaled to display the full page width and occupying the full height of the display. You can change the "829x814" values as desired to change the size of the window, and the "-0-6" values to change its location. To determine these values, I first scaled the size and location manually, then used the handy utility ```
xwininfo
```I then copied its result into the launcher's command line. The "-notopbox" option suppresses display of the top box.

---

### Post by Elfy on 2012-07-18
The information in this thread has been moved to [https://help.ubuntu.com/community/Xman](https://help.ubuntu.com/community/Xman)

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?t=2028425](http://ubuntuforums.org/showthread.php?t=2028425)

Thread closed.

---

