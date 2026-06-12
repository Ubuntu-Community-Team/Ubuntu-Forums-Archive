---
title: "serious problem with firefox on unity"
date: 2015-02-28
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-02-28
Firefox will not show info from popular website on the unty desktop

Below is the website with gnome-shell.

---

### Post by ventrical on 2015-02-28
and now on firefox with unity.

Notice that the data is not in the dialog boxes.

---

### Post by dino99 on 2015-02-28
with  GS session it is even worst, it fails loading. From terminal i get:  g_slice_set_config: assertion 'sys_page_size == 0' failed

which seems related to an old non fixed glib issue lp:1179554     ;)

---

### Post by zika on 2015-02-28
> **ventrical said:**
> Firefox will not show info from popular website on the unty desktop

Below is the website with gnome-shell.

> **ventrical said:**
> and now on firefox with unity.

Notice that the data is not in the dialog boxes.

> **9d9 said:**
> with  GS session it is even worst, it fails loading. From terminal i get:  g_slice_set_config: assertion 'sys_page_size == 0' failed

which seems related to an old non fixed glib issue lp:1179554     ;)What is the URL of site You're writing about?

---

### Post by dino99 on 2015-02-28
> **zika said:**
> What is the URL of site You're writing about?

i mean : it even does not start (silent crash here)

---

### Post by piscvau on 2015-02-28
Hello
I am on Trusty version of Xubuntu and I have the same error message when I start from command line.
piscvau

---

### Post by dino99 on 2015-02-28
> **piscvau said:**
> Hello
I am on Trusty version of Xubuntu and I have the same error message when I start from command line.
piscvau

the real issue seems to be with Glib used by Firefox; add your vote to  lp:1179554 (affect me to) to grab devs attention

---

### Post by grahammechanical on 2015-02-28
Do not start Firefox from the commandline. If we do we will get this, and it does not matter if we are running trusty or vivid:

> (process:3714): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
console.error: 
  Message: Unix error 13 during operation open on file /home/graham/.mozilla/firefox/okxi8ppk.default/sessionstore.js (Permission denied)

We will get similar messages when we start any GUI application from the terminal. This has been a fact of life for years. I guess that the second error message would not be there if I run Firefox using the sudo prefix but I cannot think of any sensible reason for giving a web browser root priivileges. I am certainly not going to do that just to test the truth of my guess.

Oh by the way,

@ventrical

Firefox seems to be working fine here.  The only google calendar that I am familiar with is the calendar for Ubuntu On Air and that is displaying correctly on Firefox on my Vivid system.

Regards.

---

### Post by ventrical on 2015-02-28
@graham

Try this ..  [http://www.cfkcanada.org/calendar.html](http://www.cfkcanada.org/calendar.html)

on Unity.

---

### Post by Mateusz Stachowski on 2015-02-28
@ventrical

I just tried that website on Unity and it displays for me in Firefox just like on the screenshot from your first post.

BTW it looks better in Chrome because there the last letter "e" isn't cut in half (it fits in the field).

---

### Post by grahammechanical on 2015-02-28
@ventrical

There was a yard sale at 09.00 today 28th Febuary. Did you go? Or did you go to the yard sale on 14th February? The yard sale is held every second Saturday and dates are entered into the calendar way into next year. I guess that means that I do not see the problem that you have. The web site is working quite well.

Regards.

---

### Post by ventrical on 2015-02-28
> **grahammechanical said:**
> @ventrical

There was a yard sale at 09.00 today 28th Febuary. Did you go? Or did you go to the yard sale on 14th February? The yard sale is held every second Saturday and dates are entered into the calendar way into next year. I guess that means that I do not see the problem that you have. The web site is working quite well.

Regards.

Ok .. thanks .. I went to todays yardsale. It must be something  on this one particular install of ubuntu unity because all other are working

Regards..

---

### Post by ventrical on 2015-02-28
> **zika said:**
> What is the URL of site You're writing about?

I left a reply earlier with the link ... but looks like it didn't save.

[http://www.cfkcanada.org/calendar.html](http://www.cfkcanada.org/calendar.html)

---

### Post by ventrical on 2015-02-28
Firefox just updated/upgraded. On Ubuntu - unity I get the following:

---

### Post by ventrical on 2015-02-28
On Firefox with unity I get:

---

### Post by ventrical on 2015-02-28
On gnome-shell I get:

---

### Post by ventrical on 2015-02-28
So the one that is working is :

Type JPEG Image

The one that is not working is:

Type VND.MICROSOFT.ICON.Image

---

