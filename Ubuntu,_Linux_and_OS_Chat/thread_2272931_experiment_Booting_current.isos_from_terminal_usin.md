---
title: "experiment: Booting current.isos from terminal using startx"
date: 2015-04-09
forum: Ubuntu, Linux and OS Chat
---

### Post by ventrical on 2015-04-09
I am currently using a technique that allows me to run multiple desktop concurrently in F(n) terminal using startx command. I am wondering if anyone knows how to boot an iso from a terminal session.. ie; how would I set up the command in .xinitrc so I could boot 15.04 daily-live session , yet still have my two concurrent desktops? Theoretically I think it is possible.

Regards..

---

### Post by dino99 on 2015-04-09
why not directly from the device ?
[http://www.howtogeek.com/196933/how-to-boot-linux-iso-images-directly-from-your-hard-drive/](http://www.howtogeek.com/196933/how-to-boot-linux-iso-images-directly-from-your-hard-drive/)

---

### Post by ventrical on 2015-04-09
> **9d9 said:**
> why not directly from the device ?
[http://www.howtogeek.com/196933/how-to-boot-linux-iso-images-directly-from-your-hard-drive/](http://www.howtogeek.com/196933/how-to-boot-linux-iso-images-directly-from-your-hard-drive/)

Thanks but not what I was looking for. I want to boot 'live' iso while I have two desktops running concurrently - so I would not be able to start a session of Grub without rebooting. Maybe with some tweaking - yes.. but now when I log out of Mate desktop it will go back to terminal and I have to restart it using
 ```

startx -- :1

```

Thanks for your suggest..

---

### Post by dino99 on 2015-04-09
i does not see a solution but virtual system as all the Alt+fn switches are seen by the opened session

---

### Post by ventrical on 2015-04-09
> **9d9 said:**
> i does not see a solution but virtual system as all the Alt+fn switches are seen by the opened session

Yes... and I formulated my question wrongly  and I am off topic here.

*note* elfin,cariboo

Please move this thread to linux os chat or somthing. I was thinking of somthing else :)

thnx

---

### Post by zika on 2015-04-09
> **ventrical said:**
> I am currently using a technique that allows me to run multiple desktop concurrently in F(n) terminal using startx command. I am wondering if anyone knows how to boot an iso from a terminal session.. ie; how would I set up the command in .xinitrc so I could boot 15.04 daily-live session , yet still have my two concurrent desktops? Theoretically I think it is possible.
Regards..It is possible but take care about two kernels trying to access same /... If You provide two different /'s that should be possible.
In case of different X's(or Waylands or Mirs, whatever) in two different TTY (You call it, F(n), I suppose) that is not that big issue but it is a bit of hazard...
Theoretically, as You write, that means that all theoretical (but also practical ones) premises are fulfilled...

---

### Post by ventrical on 2015-04-09
> **zika said:**
> It is possible but take care about two kernels trying to access same /... If You provide two different /'s that should be possible.
In case of different X's(or Waylands or Mirs, whatever) in two different TTY (You call it, F(n), I suppose) that is not that big issue but it is a bit of hazard...
Theoretically, as You write, that means that all theoretical (but also practical ones) premises are fulfilled...

Yes .. the above basically explains  what I mean I think.  I have to do a little more research on this. ie; when I load a DE like mate-session or xfce4-session for instance and then log out it will bring me back to the cli in the terminal, tty1, 2 or whatever I am using... so there has to be a script (of course) for .xinitrc . It is of great pracitcal use to me because I can use various DEs as sidekick reference servers that make it a lot easier to track just exactly where I left off. Plus I get to test the other 14.5GBs of ddr3 ram I have :)

Then I can always go back to tty7, edit .xinitrc and fill the extra terminals manually. When I open gnome-terminal and run top there is this program (or service) running called 'collector' . One I haven't seen before. When I run multiple terminals on different DEs  spread across the array they appear to all be aware of each other running concurrently in the background.  Ok.. that's fine but loading an extra kernel , as I understand, uses that processors VT technology but employs a wait state (or traffic cop) and so the two kernels are not truly running concurrently?

Regards..

---

