---
title: "Remote control your Ubutu Media. Really, yes you can. Let me explain how."
date: 2012-11-18
forum: The Cafe
---

### Post by drpain on 2012-11-18
[SIZE=3]***Well hello there. ***[/SIZE]


I though I would share this, should someone look for something similar and happen upon this. 
  The easiest way I found to send the keystrokes through Python is by installing ***xdotool***  which is a unix based scripting tool, wich is pretty awesome. It  supports all the multimedia keys. Including the context menu a.k.a  "Menu". 



  [SIZE=3]***So what did I need it for?***[/SIZE]

I built a remote for my ubuntu since my Compro Remote stopped working.


  [SIZE=3]***How does it work?***[/SIZE]

It leverages Apache, Bootstrap, PHP, Redis, Python and finally xdotools  (Boy that's a mouthfull). I created a mini website which I access  through my WIFI with remote buttons which when clicked sends the command  in the background to the PHP  Script running on Apache.
  This PHP script then saves the command and values in Redis which is  polled constantly by Python. Once Python picks the command up. It checks  it in the dictionary of commands and sends the appropiate command line  to xdotool. Xdotool then runs the Media Keys or starts Rhythmbox or XBMC  or pauses and plays. Whatever. So far it's working like a charm.

[IMG]https://raw.github.com/drpain/web-the-black-mote/master/assets/img/webmote.jpg[/IMG]

    [SIZE=4]**Head on over to Github**[/SIZE]

  **I am putting a github repositry together for this. I hope this helps someone, somewhere**
  Installation instructions etc. to follow in said Github page. 



  [https://github.com/drpain/web-the-black-mote](https://github.com/drpain/web-the-black-mote)

---

