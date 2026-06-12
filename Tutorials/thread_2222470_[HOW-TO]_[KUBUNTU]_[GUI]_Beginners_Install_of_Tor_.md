---
title: "[HOW-TO] [KUBUNTU] [GUI] Beginners Install of Tor - As of 6MAY2014"
date: 2014-05-06
forum: Tutorials
---

### Post by impliedconsent2 on 2014-05-06
[B](ENGLISH ONLY ***Kubuntu 14.04LTS*** other DEs may vary)
[/B]
If you do not know what Tor is, visit their page [Tor Overview]("https://www.torproject.org/about/overview.html.en"). If you're interested, you can work it out yourself or follow this HOW-TO.

*(Disclaimer:  I am not way associated with Tor and do not advocate or am responsible for any illegal activities conducted as a result of this tutorial - just a normal *buntu user who values privacy sometimes)*

The easiest way to download and install Tor is going to [Tor Downloads]("https://www.torproject.org/download/download-easy.html.en") page.  Just like the page says, _"Everything you need to safely browse the Internet. This package requires no installation. Just extract it and run."_&#8203;  Now, assuming you're running Linux and know how to install your distribution, the chances are that you know how to extract the tor-browser-linux64-3.x_en-US.tar.xz **or** tor-browser-linux32-3.x_en-US.tar.xz file, so not going into that.  I believe, normally, that's it and an icon would be created for you (or a new Firefox icon) - but I believe there is an ongoing bug which prevents a launcher icon.  So, what I will do is show you how to use the built-in GUI based tools to create a launcher so you have an icon to click.  This does not require the use of Terminal (Konsole.)

So, you should have extracted you *.tar.xz file and it created a directory such as:  */home/-name-/tor-browser_en-US/* (use your default file manger to navigate to the directory). Inside that directory should be a file called *start-tor-browse.* Double click that and your new browser will install and you can now safely and anonymously browse the internet.

[ATTACH=CONFIG]252925[/ATTACH]

OK, you don't wanna keep on opening up your file manager and want a launcher instead.  Here's a very easy way to do it without copy-n-paste Terminal (Konsole) commands that you have no idea what it does, via your built in GUI tools. As you do these, there 'might' be some tweaks you'll see that I've implemented, but I'm pretty sure I'm pretty close to stock Kubuntu.  You'll also learn a trick or two (maybe some self proclaimed experts as well??).

1.  First thing we want to do is Unlock Widgets by **R**ight clicking on an unused portion of your desktop.

[ATTACH=CONFIG]252926[/ATTACH]

      2.  Now, **R**ight click on the blue Kubuntu Application Launcher (if you're moving from Windows, it's where the Start button is - XP-->W7 - no clue on W8+) and select "Edit Applications"

[ATTACH=CONFIG]252927[/ATTACH]

      3.  This opens up the KDE Munu Editor.  You can put it anywhere you want, but I chose the most logical based on KDEs menu layout.  Click on Internet AND select the arrow next to Internet. It will open up the applications under Internet.

[ATTACH=CONFIG]252920[/ATTACH]

      4.  Now, create a menu item for Tor.  See the **green + New Item button**?  Yep, click that. This will prompt you for a name (umm.. like "Tor" maybe?  :KS)

[ATTACH=CONFIG]252921[/ATTACH]

      5.  Notice I have an icon associated with it?  You won't, so click on that big square and getchya an icon you like.  If you want a special icon, Google "Tor Icons" under Images - pick the one you want - **R**ight click --> Save Image As ... --> put it anywhere under your "Home" directory and select it for your new icon.                  (there is a way to make this default for all users, but that's another tutorial).

      6.  Click the Save Button and test your work by hitting the Kubuntu button-->Applications tab-->Internet-->Tor.  Should start up without fanfare.  Happy surfing.  Any improvements are welcome (*keep in mind your GUI-based beginners audience - I do not believe that we'll be going back to pure X terminal anytime soon*).

[HR][/HR]

Bugs associated with Tor:

*  [Vidalia was unable to start Tor. Check your settings to ensure the correct name and location of your Tor executable is specified]("https://bugs.launchpad.net/ubuntu/+source/vidalia/+bug/680192")

Uhhg - I was going to helpful, but that's painful ... a boatload of other issues that I'm not experiencing - Go ahead and research [Tor tagged in Ubuntu]("http://askubuntu.com/questions/tagged/tor?sort=newest&pagesize=50") or search [Ubuntu bugs via Launchpad]("https://bugs.launchpad.net/ubuntu") or CSM Google (<--somebody will 'get' that) ... but one last parting shot ... Privacy much? --> [Tails]("https://tails.boum.org/")
[B][FONT=arial][SIZE=5][COLOR=#ff0000]
[SIZE=2]DON'T ASK ME THE INVALID .PNG FILES - ASK THE "Administrator" - they show up just fine on edit or preview[/SIZE] [/COLOR][/SIZE][/FONT][SIZE=5][SIZE=2][COLOR=#000000](Hopefully I fixed it after about 5 edits) (where the heck are the tag option?)[/COLOR][/SIZE][/SIZE][/B]

---

