---
title: "How to install TOR on Ubuntu 15.10 Wily Werewolf"
date: 2016-01-06
forum: Tutorials
---

### Post by dave205 on 2016-01-06
After multiple OS installs I could not get TOR to install via the Ubuntu Software Center so I went straight to the source. Actually the app *would* install, it just would not connect and ask me if I was connected to the Internet. Obviously I am. Hopefully this will help others who have hit this roadblock. 

Start by going to tor.org and getting the appropriate packages. [https://www.torproject.org/docs/tor-doc-unix.html.en](https://www.torproject.org/docs/tor-doc-unix.html.en)

As stated in the second line, "[COLOR=#1A1A1A][FONT=Helvetica]If you're using Ubuntu, don't use the default packages: use [/FONT][/COLOR][our deb repository]("https://www.torproject.org/docs/debian.html.en#ubuntu")[COLOR=#1A1A1A][FONT=Helvetica] instead." 

[/FONT][/COLOR]Deb repository found here - [https://www.torproject.org/docs/debian.html.en#ubuntu](https://www.torproject.org/docs/debian.html.en#ubuntu)  From here I did change the name of the distribution to "wily" and it worked. The most current distro is not listed in the drop down menus at the time of writing this. 

[COLOR=#1A1A1A][FONT=Helvetica]COPY FROM the deb repository with added notes[/FONT][/COLOR]
```
[COLOR=#1A1A1A][FONT=Helvetica][FONT=inherit]You need to add the following entry in /etc/apt/sources.list or a new file in /etc/apt/sources.list.d/: {**NOTE** - I used the Software & Updates application (other software tab) found in System Settings to add these.}[/FONT][INDENT]deb http://deb.torproject.org/torproject.org wily main
deb-src http://deb.torproject.org/torproject.org wily main[/INDENT]
[/FONT][/COLOR]
[FONT=inherit][COLOR=#1a1a1a]Then add the gpg key used to sign the packages by running the following commands at your command prompt: {**NOTE** - this I actually did via command line. Once you do, you should see them listed in the Authentication tab of the Software & Updates [/COLOR][/FONT][FONT=Helvetica][COLOR=#1a1a1a]application[/COLOR][/FONT][FONT=inherit][COLOR=#1a1a1a] found in System Settings.}[/COLOR][/FONT][INDENT]gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -

[/INDENT]
[COLOR=#1A1A1A][FONT=Helvetica][FONT=inherit]You can install it with the following commands:[/FONT][INDENT]$ apt-get update
[FONT=inherit]$ apt-get install [FONT=inherit]tor[/FONT] deb.torproject.org-keyring[/FONT][/INDENT]
[/FONT][/COLOR]

```

Next as stated in the page 1, move to step 2 - [https://www.torproject.org/docs/tor-doc-unix.html.en#using](https://www.torproject.org/docs/tor-doc-unix.html.en#using)
Step 2 simply states to download the appropriate TOR browser.  Once downloaded you extract to the location of your choice. Using the file manager go into the extracted folder (tor-browser_en-US in my case) and launch the TOR browser there. You should see the familiar TOR icon.  From there you can copy that icon to the desktop and lock to your launcher. 



Well, that's really it. I hope this helps.

---

