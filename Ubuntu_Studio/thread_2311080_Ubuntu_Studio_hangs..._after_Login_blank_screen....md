---
title: "Ubuntu Studio hangs... after Login blank screen..."
date: 2016-01-24
forum: Ubuntu Studio
---

### Post by SenseMaker2011 on 2016-01-24
Hi folks.... I did a parallel installation one year ago on an "old Microsoft XP Pro" mashine (Intel). The computer is mainly used as email-server. With Firefox (via Wine) and Google Chromium installation, DSL Internet access, binded in a Microsoft network (via FritzBox router) and connected with a network printer (Lexmark Proveil 700 series via WLAN). 

**Ubuntu 14.04.3 LTS ubuntustudio tty1** (*GNU/Linux 3.13.0-76-generic i686*) is installed parallel, with **GNU GRUP** version "*2.02 beta2-9ubunttu1.6*". After Ubuntu has started regularly I can decide between "Xfce Session" and "ubuntustudio" desktop  graphic to login. I always used since first installation UbuntuStudio. The mashine worked all fine for one year now, with regularly (auto-)updates. 

[I]The problem:
[/I]
Today in midth working with my email client (Thunderbird) I wanted store an email as PDF (virtual print job). But it didnt work. I got the notice Thunderbird crashed. So I restarted the computer.... selected Ubuntu and got the login front page. After login I dont get anything on the screen anymore. It keeps blank jus showing the ubuntu studio desktop background image same one as this: 
[IMG]http://www.linuxinsider.com/article_images/2015/82755_990x557.jpg[/IMG]

Very strange: No desktop icons, no menu bar, nothing. Only the mouse arrow cursor is there I can move regularly.

I still can login as "guest", that works fine. But dont have access to any harddisk there (as prohibited not having admin rights logically). Neither with Xfce or ubuntustudio graphic surface I get it to have a fully desktop after password login. I can switch after the login with  blank desktop screen via Ctrl + Alt  + F1 into the terminal modus, Login there works successfully. With Ctrl  + Alt + F7 I can jump back, but same I see only the desktop background  icon with the mouse arrow cursor.

I can start the latest "recovery modus", too during the boot process of the PC. And I can start the network access manually in the terminal via "sudo service network-manager restart" (as I dont have the auto start).
> 
network-manager stop/waiting
network-manager start/running, process 2717

What to do now ? I am "only" a simple user following instructions. I have read different threads.... e.g. this one sounds very similarly to my problem:
[http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears](http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears)

I never used Unity. I thank you in advance for your support.

---

### Post by SenseMaker2011 on 2016-01-24
P.S.: I have read something to fix Unity with a simple Terminal command "*rm rf .compiz-1*"... would be great to get something similarly now for ubuntusudio 14.04.3 to bring back my fully desktop.
[http://itsfoss.com/how-to-fix-no-unity-no-launcher-no-dash-in-ubuntu-12-10-quick-tip/](http://itsfoss.com/how-to-fix-no-unity-no-launcher-no-dash-in-ubuntu-12-10-quick-tip/)

---

### Post by SenseMaker2011 on 2016-01-24
I suppose I trapped myself :-) As I use a small hard disk, as all my files are outsourced on an external file server, the autobackup function of "systembackup" filled the 40 GB hard disk over time with different restauration points. It seemed the reserves had been down on "0". I have deleted two restauration points ang got 12 GB free. And now Login is possible with fully desktop back.

Damm*** this programme should have a "warning" if the hard disk capacities fall down under a minimum level. I suppose I trapped and locked out myself. :-)

---

