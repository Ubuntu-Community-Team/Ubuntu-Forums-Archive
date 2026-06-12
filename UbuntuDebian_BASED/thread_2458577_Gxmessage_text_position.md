---
title: "Gxmessage text position"
date: 2021-02-27
forum: Ubuntu/Debian BASED
---

### Post by GrouchyGaijin on 2021-02-27
Hi Guys,

I am running Pop_OS 20.04. I am using remind and gxmessage to send popup reminders of things I need to do.
I wrote a small script to add the reminder to my reminder's file and use a script that starts at login to look for and trigger the popup at the specified time.

My question is does anyone know how I can change the default alignment of the text as it appears in the popup window?
Currently the text is aligned at the very top of the popup window and I would like it to be in the center of the window.
See the screen shot below:
[ATTACH=CONFIG]288026[/ATTACH]
 
I wonder if this is a Pop_OS thing as I have used this script on Ubuntu without any problem.

---

### Post by howefield on 2021-02-27
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by GrouchyGaijin on 2021-02-27
The odd thing is Quill, a forum admin, seems to have marked my question as a duplicate and closed. I have searched and can't find an answer to my question. Anyone have a suggestion?

---

### Post by GrouchyGaijin on 2021-03-02
Hi Guys,

I use Remind to keep track of reminders. Until recently I have used Gxmessage to display pop up reminders from my .timedreminders file.
I noticed that recently the text in the Gxmessage box is always displayed at the very top of the pop up window. This makes it a bit difficult to read so I thought I would look for another way to generate pop up reminders.
I came across Yad which is a fork of Zenity, but I can't seem to figure out how to have the last reminder in my .timedreminders file be displayed at the given time in a Yad box.
Has anyone had any experience with this or am I looking at the wrong tool?

---

### Post by DuckHook on 2021-03-02
Please do not duplicate post. It confuses those trying to help and dilutes community effort. Therefore, *threads merged*.

Please feel free to *bump* a thread every 12 hrs to bring it to the top of the pile.

Also, your thread is now in the proper subforum, as it deals with POP OS; not Ubuntu. The general forums are for Ubuntu and its official flavours.

---

### Post by norobro on 2021-03-02
> **GrouchyGaijin said:**
> My question is does anyone know how I can change the default alignment of the text as it appears in the popup window?
You can use css to style Gtk widgets. Try putting the following in ~/.config/gtk-3.0/gtk.css```
#gxmessage-textview {
    padding-top: 5px; /* adjust accordingly */
}
```
If the directory and/or file don't exist, create them.

---

### Post by GrouchyGaijin on 2021-03-04
Thank you! I just now saw this reply.
Unfortunately that did not help. I noticed the # in your reply so I did try both with the # and without the # (in case that would comment out the command).
I rebooted my machine between attempts just to be sure everything was loaded freshly.

---

### Post by GrouchyGaijin on 2021-03-04
Okay - understood

---

### Post by GrouchyGaijin on 2021-03-04
Okay - I understand. Thank you.

---

### Post by norobro on 2021-03-04
Works for me. The styled version uses the following gtk.css and the unstyled has no css file.```
$ cat .config/gtk-3.0/gtk.css

#gxmessage-textview {    
    padding-top: 15px;
}

#gxmessage-textview>text {
    color: cyan;
    background: darkblue;
}
```How are you calling gxmessage? The screenshots are called from the command line:```
$ gxmessage unstyled
```

---

### Post by GrouchyGaijin on 2021-03-04
Gxmessage is called through a script that runs at boot to start the remind daemon.

```
remind -z '-kgxmessage -buttons "OK:1" -default "OK" -font "Digital-7 24" -fg "#BEC610" -bg black -wrap -title  "Script!" %s &' ~/Reminder-files/.timedreminders


```

---

### Post by norobro on 2021-03-04
The ~/.config/gtk-3.0/gtk.css only affects your normal user. I don't use remind but I suppose the daemon runs as another user so you are going to have to modify the theme that you are using. 

For instance if you are using the Yaru-dark theme you will need to add the css in post #6 to the gtk.css file for the theme. On my box that is /usr/share/Yaru-dark/gtk-3.20/gtk.css

Hope this helps.

---

### Post by GrouchyGaijin on 2021-03-05
Thank you

---

