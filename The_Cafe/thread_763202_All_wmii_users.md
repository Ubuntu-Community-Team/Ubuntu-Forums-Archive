---
title: "All wmii users"
date: 2008-04-22
forum: The Cafe
---

### Post by Istonian on 2008-04-22
I am playing around with wmii a little and I was wondering what the best IM client, email client and web browser is for wmii. Oh and file manager if possible.

---

### Post by LaRoza on 2008-04-22
> **Istonian said:**
> I am playing around with wmii a little and I was wondering what the best IM client, email client and web browser is for wmii. Oh and file manager if possible.

I use:

[list]
[*] finch for IM (same as Pidgin, so all your accounts are there) "sudo aptitude install finch"
[*]email client? Whatever you use now. I use webmail and Opera.
[*] Thunar (not Nautilus!), or mc from the terminal.
[/list]

---

### Post by Istonian on 2008-04-22
LaRoza! Just the person I was hoping to hear from. Thanks for the information. I had a feeling you would be the first to respond.

---

### Post by LaRoza on 2008-04-22
> **Istonian said:**
> LaRoza! Just the person I was hoping to hear from. Thanks for the information. I had a feeling you would be the first to respond.

Really? I am flattered :-)

---

### Post by DahVid on 2008-04-22
I'm not a wmii user, but I can recommend that you should use the best tools regardless of your window manager unless there is a major conflict (I.E., your application extensively uses floating windows (gimp), or your application uses Swing/AWT a lot).

---

### Post by Istonian on 2008-04-22
Im playin around with wmii now. I kinda like it. Will take a while to get used to tho.

---

### Post by LaRoza on 2008-04-22
> **Istonian said:**
> Im playin around with wmii now. I kinda like it. Will take a while to get used to tho.

It took me an hour to get used to it.

One thing that tripped me up, theming wmii. It is easy to do. Here's how (from a terminal)
First copy all the settings to your local settings file. The defaults are in /etc/X11/wmii-3.5/wmiirc. The local copy will be in ~/.wmii-3.5/wmiirc.

```

cp /etc/X11/wmii-3/wmiirc ~/.wmii-3/wmiirc

```

Now, edit ~/.wmii-3.5/wmiirc to customize it. If you mess something up, weird things happen...

To change the theme, see: [http://www.suckless.org/wiki/wmii/tips/themes](http://www.suckless.org/wiki/wmii/tips/themes)

---

### Post by Istonian on 2008-04-22
Thanks for that. I will try it later. Right now im trying to figure out all the commands. How do you enable your account in finch? I cant do it. Never used cli apps before so im a noob and a half at this.

---

### Post by Lostincyberspace on 2008-04-22
What is the easiest way to install wmii? on ubuntu and get it set up good.

---

### Post by LaRoza on 2008-04-22
> **Istonian said:**
> Thanks for that. I will try it later. Right now im trying to figure out all the commands. How do you enable your account in finch? I cant do it. Never used cli apps before so im a noob and a half at this.

Do you have Pidgin? It should use the same setting from that.

Here's the guide: [http://developer.pidgin.im/](http://developer.pidgin.im/)

---

### Post by LaRoza on 2008-04-22
> **Lostincyberspace said:**
> What is the easiest way to install wmii? on ubuntu and get it set up good.

```

sudo aptitude install wmii

```

After it is installed (it is very small), log out, and log in with "wmii" selected under "sessions"

It will have a guide guide open for you when you log on the first time. I suggest following it. You get used to it quickly.

(Press "Alt + a" to log out, well select "exit")

---

### Post by Lostincyberspace on 2008-04-22
Thanks LaRoza! nice fast response will try it out this week.

---

### Post by chucky chuckaluck on 2008-04-22
> **Lostincyberspace said:**
> What is the easiest way to install wmii? on ubuntu and get it set up good.

```
sudo apt-get install wmii
```

it's pretty well set up, but you can mess with it by copying /etc/X11/wmii to your home folder, changing it to .wmii and inside you'll find the wmiirc file that you can edit for what you want.


to the OP, i found that terminal apps work the best in wmii, so centericq/im for im, i use gmail but mutt or pine would probably be fine and i use elinks for browsing, or opera when i want all them purdy pictures.

---

### Post by Istonian on 2008-04-22
When I open finch it says choose which account I want enabled. I don't know how to get past that.

---

### Post by LaRoza on 2008-04-22
> **Istonian said:**
> When I open finch it says choose which account I want enabled. I don't know how to get past that.

I am not sure what that means. See the guide for it. Sorry.

(you can't have two clients in use at the same time)

---

### Post by LaRoza on 2008-04-22
> **chucky chuckaluck said:**
> 

to the OP, i found that terminal apps work the best in wmii, so centericq/im for im, i use gmail but mutt or pine would probably be fine and i use elinks for browsing, or opera when i want all them purdy pictures.

centerim is the active project now.

I am going to try it.

---

### Post by DigitalDuality on 2009-05-17
d

---

### Post by DigitalDuality on 2009-05-17
d

---

### Post by Belathor on 2009-05-30
bitlbee+weechat is a great way to combine IRC and IM in wmii.

Also, here are some good resources for configuring wmii:
[http://wiki.archlinux.org/index.php/Wmii](http://wiki.archlinux.org/index.php/Wmii)
[http://wiki.debian.org/Wmii](http://wiki.debian.org/Wmii)

---

