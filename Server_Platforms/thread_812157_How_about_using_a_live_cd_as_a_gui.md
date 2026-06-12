---
title: "How about using a live cd as a gui?"
date: 2008-05-29
forum: Server Platforms
---

### Post by garethsimpsonuk on 2008-05-29
An idea that's just came to me, is using a live cd as a gui.

Basically I don't know about others but I find it hard to visualise my file structures and to check everythings working fine from the cli.

I was thinking maybe just booting into a live cd when I get stuck and then ejecting it when I'm finished.

I don't really know how live cds work tho, and the effectiveness of this would be dependant on a number of those things such as would the package manager work.

An even better thought...I know that making a live usb makes it possible to save settings and other changes to the default os. 
Could a live USB be integrated into the server os?

This is just a quick thought and would be good for ppl who don't want a gui but would like a gui for when they get stuck.

This could be a stupid idea, what are others thoughts?

---

### Post by Oldsoldier2003 on 2008-05-29
> **garethsimpsonuk said:**
> An idea that's just came to me, is using a live cd as a gui.

Basically I don't know about others but I find it hard to visualise my file structures and to check everythings working fine from the cli.

I was thinking maybe just booting into a live cd when I get stuck and then ejecting it when I'm finished.

I don't really know how live cds work tho, and the effectiveness of this would be dependant on a number of those things such as would the package manager work.

An even better thought...I know that making a live usb makes it possible to save settings and other changes to the default os. 
Could a live USB be integrated into the server os?

This is just a quick thought and would be good for ppl who don't want a gui but would like a gui for when they get stuck.

This could be a stupid idea, what are others thoughts?

the biggest issue is that your live cd boots up a completely different OS (the one stored on the cd) yes you can use it to access your file system, but during the time your live cd was running your server would not be running.

Its much easier to just use a web based admin panel and become more familiar with the command line. 

Either that you could install the gui and set it up so that when you log in to the console you can start the gui as needed and turn it off when you are done to conserve resources.

---

### Post by windependence on 2008-05-29
> **garethsimpsonuk said:**
> An idea that's just came to me, is using a live cd as a gui.

Basically I don't know about others but I find it hard to visualise my file structures and to check everythings working fine from the cli.

I was thinking maybe just booting into a live cd when I get stuck and then ejecting it when I'm finished.

I don't really know how live cds work tho, and the effectiveness of this would be dependant on a number of those things such as would the package manager work.

An even better thought...I know that making a live usb makes it possible to save settings and other changes to the default os. 
Could a live USB be integrated into the server os?

This is just a quick thought and would be good for ppl who don't want a gui but would like a gui for when they get stuck.

This could be a stupid idea, what are others thoughts?

Gareth, I think you should learn more CLI :)

Try installing Midnight Commander. tell me what you think. It's an ncurses app and you run it by typing nc at the command prompt. If you want color it's nc -c.

-Tim

---

