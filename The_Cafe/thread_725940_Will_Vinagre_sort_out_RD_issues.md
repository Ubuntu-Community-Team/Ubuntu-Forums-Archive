---
title: "Will Vinagre sort out RD issues?"
date: 2008-03-16
forum: The Cafe
---

### Post by orador on 2008-03-16
I`ve been wondering, whether or not Vinagre will solve the outstanding Remote Desktop issues, because right now, there`s no seamless solution. Of course - LogMeIn works quite fine, but I would like an OS-integrated tool... Maybe Vinagre will offer smooth way to pass by a firewall... But I haven`t seen it yet. What do you think - is there is any chance?

---

### Post by elamericano on 2008-03-25
It doesn't even do VNC well for me. So I don't think it's ready for anything. It's not integrated to the terminal server client applet that you can add to the panel either. It's back to xvnc4viewer for me.

How does something like Vinagre make it into the distro anyway? After it automatically closed the VNC connection at the start, I tried to change some preferences to maybe work around some incompatibility with the RealVNC server on the other end. What's this? No settings?! It's just a shell. Why is this in Hardy? Why on earth were they bragging about that fact? I just don't get it.

---

### Post by wyth on 2008-04-03
Agreeing with elamericano.  I was really looking forward to this because I use vnc every day for work.  But I can do a LOT more with xtightvncviewer than I can with vinagre, and xtightvnc is so much older.

Can you do a copy/paste from the desktop to the vnc session with xvnc4viewer?  That's the one reason I go back to xtightvncviewer, but xtight has that goofy way of scrolling (right-click for down and right, left-click for up and left).  I've never gotten used to that, and I think xvnc4viewer is a little nicer on the eyes.

---

### Post by elamericano on 2008-04-08
Yes, copy and paste works for me in xvnc4viewer. I know the scroll behavior of which you speak, one click in the wrong direction, two or three clicks to get back to where you wanted to go. It's much better to have real scroll bars.

---

### Post by wyth on 2008-04-08
elamericano, do you mean you can copy something from your own desktop and past it into a file one the desktop you're VNCing to with xvnc4viewer?  Because I'd love to know how; I've never made that work, and it's some functionality I could really use.

---

### Post by MrPage on 2008-04-18
My needs are even simpler that all of yours.  I would just like Vinagre to give me the option of connecting as shared (so I don't kick my co-workers out of their VNC sessions)

---

### Post by loteq on 2008-05-02
I agree with all of you. You can't even send alt-tab through. It should never have made the distro. I'm surprised. I'm installing xvnc4viewer. Is there a better choice?

---

### Post by darylb on 2008-06-19
MrPage,

I logged a [bug]("http://bugzilla.gnome.org/show_bug.cgi?id=539140") requesting support for the VNC shared option. I found out minutes later that it has been added to the development version (since 2.23.2). We should see this in intrepid as it'll be based on gnome 2.24.

Meanwhile we can download the current source and build it ourselves. See [here]("http://www.bani.com.br/lang/en/2008/06/17/vinagre-and-other-newsvinagre-e-outras-noticias/") and [here]("http://ftp.gnome.org/pub/GNOME/sources/vinagre/2.23/").

Daryl

---

