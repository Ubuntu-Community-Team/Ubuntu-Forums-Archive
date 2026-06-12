---
title: "Upgrading SerP6 from 10.04lts to 14.04lts"
date: 2014-04-26
forum: System76 Support
---

### Post by RedRat on 2014-04-26
Ok I procrastinated on upgrading my 10.04lts on my ServalPro to 12.04 and eventually I want to get to 14.04lts. I got an image of 14.04 64bit and booted my Serval Pro, and I got nothing. It went through the motions but eventually only got a blank black screen. So I then tried a 12.04lts 64bit image. This time I got the introductory "Do you want to try or install" splash screen; however, no mouse nothing! So I cannot try 12.04 out. Clearly, something is missing here, perhaps the System76 driver??? 

Any suggestions as to how to proceed. I do recognize that I more than likely will have to go to 12.04 then on to 14.04.
---------------------------------

OK, got this fixed from System76 experts. For those who might also experience the same problem I will quote their help that worked for me:

"You may need to set the nomodeset flag when the media is starting.  

To do this, you'll want to interrupt the startup by pressing the space bar and then choose a language when prompted.

On  the next screen, you can set the nomodeset flag through an F6 keypress  and using your arrow keys to navigate and then a space to select.  When  selected you should see an X appear next to it.  ([COLOR=#ff0000]***edit note: after seeing the x next to the "nomodset" hit Esc to close that window***[/COLOR]). At that point, I  generally recommend to choose try Ubuntu without installing.  

Our  restore instructions have always used the media from Ubuntu's site, so  the use of our driver would not affect what you're seeing.  "

This worked except that you will have generic video drivers and after full install of Ubuntu you will need to download the regular NVidia drivers, etc.

---

### Post by houstonbofh on 2014-04-28
Install Ubuntu Server to it.  (You can use a spare hard drive)  This will allow you to see all the hardware and make sure it works.  From the CLI install ubuntu-dekstop to get the full GUI.  And install any hardware drivers you need for graphics.

---

### Post by RedRat on 2014-04-28
Unfortunately I do not have any spare HDs available. I tried something: I tried a long winded process to see if I could get the "Try Me" for Ubuntu. I started out with 10.10 and indeed I got the normal "Try Me" splash screen and could indeed play around with 10.10 Ubuntu. I then tried 11.04 and then 11.10. Here is where things got odd. I got the "Try Me" splash screen but when I clicked on the "Try Me Out" icon, the arrow just turned into a spinning disk that went on and on. However, if I clicked on the "X" in the window's corner and killed that screen, I could successfully try out both 11.04 and 11.10, they appeared to work OK. However, when I put in the 12.04 disk, I got the "Try Me" splash screen but no mouse arrow and no keyboard response--zilch. Very strange. Putting in the 14.04 disk just gets me the initializing Ubuntu screen, then it goes to a grayish-blue screen, shortly a white bar appears at the top then the screen goes blank to black (BOD).

---

