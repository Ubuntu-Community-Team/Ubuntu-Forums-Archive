---
title: "multiple x sessions on LTSP"
date: 2007-11-03
forum: Virtualisation
---

### Post by bazz on 2007-11-03
How can I run multiple x sessions on LTSP? I tried in the lts.conf

SCREEN_07=ldm
SCREEN_08=ldm

I can log onto the first, then when I go to log on the second....it starts to logon and the just kicks me back out. If I set one of the screens to 
SCREEN_09=startx all i get is a gray screen with an x courssor. If I set it to SCREEN_10=shell I get the console, but if I type startx -- :01 it fails.

Any ideas???
I'm trying to use this for automation, and If I could use this I could use one machine in place of four by using virtualization

---

### Post by bazz on 2007-11-04
Well I kinda figured it out...for those of you who might like to know. I replaced ldm with gdm, and I did an edit to the gdm.conf. Where you comment out 0=Standard, and the uncomment out 0=Chooser. I than added two more choosers so it would look like this.
0=Chooser
1=Chooser
2=Chooser

I can start a new session by logging on to each chooser being the ctrl+alt+f7, ctrl+alt+f10, ctrl+alt+f11. The log ons have no problems....However when I go back to one of the other screens all I have is a blinking cursor. For example
I log onto the ctrl+alt+f7 screen...logs on fine. I then goto ctrl+alt+f10 and log on. Logson fine. I then go back to ctrl+alt+f7 and I just have a black screen with a blinking cursor. Any ideas? 
So...help.....anyone....any ideas????

---

### Post by bodhi.zazen on 2007-11-05
See if this thread helps : [http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

I think you can only run gdm once (gd, keeps running even after you log in). Best to disable GDM and boot to the command line & start X from there.

You can also xinit -- :1

---

### Post by bazz on 2007-11-05
Yes I saw that, but not what I'm looking for. I did find this though.
[http://www.upfrontsystems.co.za/Members/jean/cookbook/docbook/cookbook.html#thin-clients-have-grey-screen-showing-only-an-x-cursor](http://www.upfrontsystems.co.za/Members/jean/cookbook/docbook/cookbook.html#thin-clients-have-grey-screen-showing-only-an-x-cursor)

Thin clients have grey screen showing only an X cursor
Symptom

Thin clients display grey screen with an X for a mouse pointer instead of login screen.

Possible causes:

   1.

      XDMCP is disabled
   2.

      GDM is not running
   3.

      Thin clients are connecting to wrong server

Solutions

   1.

      Check if XDMCP is enabled. To do this, go to the server (you may have to connect a display, keyboard and mouse), and click on the main menu button on the bottom of the screen. Go to the System Settings menu, and choose "Login" to modify your login settings. You will have to enter the root password. Then, click on the "XDMCP" tab, and ensure that the box that says "enabled" is selected.
   2.

      Check if GDM is running. You can gain access to the server by using a secure shell from one of the thin clients (refer to the section called “Using a secure shell from one of the thin clients”). To check if GDM is running (once logged in), type:

      #ps -e | grep " .dm"

      If GDM is running, you will see an output similar to this:

      1973 ?      00:00:00  gdm
      3226 ?      00:00:00  gdm

      If GDM is not running, or if you'd like to restart GDM, you can type:

      #gdm-safe-restart

   3.

      The server to be used for LTS (Linux Terminal Services) is specified in the lts.conf file using the "server" directive. This value is normally 192.168.0.254, but may be different depending on your specific setup:

      #from lts.conf:
      server = 192.168.0.254

      If you have more than one tuXlab server, or if you have more than one computer network in your school, then this address might have to be slightly different.

So if I edit my lts.conf with 
SERVER=ip of ltsp server
SCREEN_07=startx
SCREEN_08=startx
SCREEN_09=startx

I can have multiple sessions. How ever I can not get my main account to log on, only other users. Also If I leave the session for a little while it will drop the session, so the GUI no longer works.

---

