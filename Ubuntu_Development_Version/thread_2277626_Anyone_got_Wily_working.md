---
title: "Anyone got Wily working?"
date: 2015-05-10
forum: Ubuntu Development Version
---

### Post by Chanath on 2015-05-10
Nothing appears to work in Wily yet. The browser doesn't even start. If you open Apps maximized, you can't make it smaller or make it go away. Has anyone got Wily working?

---

### Post by fjgaude on 2015-05-10
Everything works normal for me with wily, nothing like you are stating. I have Intel HD graphics within the CPU.

---

### Post by Chanath on 2015-05-10
> **fjgaude said:**
> Everything works normal for me with wily, nothing like you are stating. I have Intel HD graphics within the CPU.
I too have Intel graphics.
Downloaded it twice today. Both times with same problems. Anyway, I'd wait, as nothing much is there to look at yet.

---

### Post by mc4man on 2015-05-10
> **Chanath said:**
> I too have Intel graphics.
Downloaded it twice today. Both times with same problems.
Downloaded what?

---

### Post by grahammechanical on 2015-05-10
I was wondering the same thing. My two installs of desktop next (Unity8) have kernel panic. I noticed that Desktop Next (Unity) daily ISOs with today's date were available. So, I am about to download and install.

I am a bit surprised to see these ISO image in cdimage.ubuntu.com as I expected them to be replaced by snappy personal desktop ISO. I am not sure but I think that they will also be called Desktop Next.

I will see what happens with this ISO image.

[http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/)

---

### Post by dino99 on 2015-05-10
Testing a vivid > wily i386 upgrade with nvidia-346; all is fine with a gnome-shell session

---

### Post by mc4man on 2015-05-10
For Ubuntu (Desktop) I'd use here, how it works one would need to try - 
[http://cdimage.ubuntu.com/ubuntu/daily-live/pending/](http://cdimage.ubuntu.com/ubuntu/daily-live/pending/)

---

### Post by sgage on 2015-05-10
I have clean installs of both Wily Kubuntu and Wily Ubuntu Gnome on my machine, and both are working quite nicely.

---

### Post by fjgaude on 2015-05-10
I used 

[http://cdimage.ubuntu.com/daily-live/20150509/](http://cdimage.ubuntu.com/daily-live/20150509/)

along with zsync from the first day. All seems normal, except the word current is changed to the date as you can see in the URL.

---

### Post by jerrylamos on 2015-05-10
Sort of.

Shutdown took forever.  And ever.  Finally powered off.

Made the .iso with zsync using vivid .iso renamed as wily.  Went quickly wily hasn't changed much.

Installed as usual booting .iso from hard disk.  Booted up said it was wily behaved like vivid as expected.

When I've got some wasty time I'll boot again, update, and see if it whill shut down.  Or not.  There's always power off.

BTW, when I've got something important to do, I use 14.04.  Such a relief - it works!

---

### Post by Chanath on 2015-05-10
I meant Wily Ubuntu, otherwise Ubuntu Next 15.10 daily.
When I click Ubuntu icon (dash icon) Apps would open in a small window, and when clicked "maximize" it maximizes and stays maximized. Cannot close it. Web browser doesn't start.  Nothing much is there either. At least the Web browser in 14.04 works. So, downloaded it again, and with the same results. It doesn't power off.

Then downloaded Ubuntu Gnome 15.10. Works out of the box. Looks just like 15.04. I don't think anything would change there, that is, if Ubuntu Gnome 15.10 would embrace a newer Gnome shell.

---

### Post by mc4man on 2015-05-10
> **Chanath said:**
> I meant Wily Ubuntu, otherwise Ubuntu Next 15.10 daily.


Ubuntu Next 15.10 daily is Wily Ubuntu but  Wily Ubuntu is not exclusively  Ubuntu Next 15.10 (&  Ubuntu Next 15.10 likely remains a curiosity on a Desktop install

---

### Post by Chanath on 2015-05-10
> **mc4man said:**
> Ubuntu Next 15.10 daily is Wily Ubuntu but  Wily Ubuntu is not exclusively  Ubuntu Next 15.10 (&  Ubuntu Next 15.10 likely remains a curiosity on a Desktop install

Could be, but that's all I get today if I try to get Ubuntu 15.10 daily.

---

### Post by Elfy on 2015-05-10
> **Chanath said:**
> Could be, but that's all I get today if I try to get Ubuntu 15.10 daily.

[http://iso.qa.ubuntu.com/qatracker/milestones/340/builds/93071/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/340/builds/93071/downloads)

[http://iso.qa.ubuntu.com/qatracker/milestones/340/builds/93072/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/340/builds/93072/downloads)

---

### Post by sammiev on 2015-05-10
Tried this [Unity ISO]("http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/") today and get the same as the OP. ( black screen after signing in )

If I upgrade from Unity 15.04 to current Unity 15.10 manually everything works great.

Will try gnome next.

---

### Post by grahammechanical on 2015-05-10
If this thread is about Wily Ubuntu Desktop Next then there is definitely an ISO for it. I have just installed it but it is the same approach as the Vivid Ubuntu Desktop Next ISO. It first loads on X up to a lightdm login screen and then switches to Mir and the phone UI.

And yes, Browser and some other apps do crash instead of loading. I tried it with PDFViewer and Solitaire. Any web app would also crash as it needs Browser. Tried it with BBC weather.

The trick to use to minimise a scope is to pull out the launcher and click the Ubuntu icon and that should put the max, min and close icons in the top panel. The good news is that the intro swipe bug has been fixed. We can install a terminal and it does not crash. Can update/upgrade with it.

There is also a file manager but /home/user/does not have folders for Documents, Music and that sort of file. There is no way to import files from another partition and even if we copy and paste from another partition into this partition there are no folders to put them in. It is possible to create folders but I am not sure if apps like Music app would recognise the folder as official.

Ubuntu Desktop Next was never meant to last. But Snappy personal is meant to be a parallel development. So, I do not really see the need for this Ubuntu Desktop Next ISO image during this cycle.

Regards.

---

### Post by Chanath on 2015-05-10
This from where I downloaded it.
```
http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/
```

There is also ```
http://cdimage.ubuntu.com/daily-live/pending/
```
but, I hadn't downloaded from this. Don't know whether I should, or it would be different from what I got.
EDIT: Downloading from the 2nd source too. Will know in few minutes.

---

### Post by mc4man on 2015-05-10
There are multiple links to 'current' Desktop images for Ubuntu 15.04 as per several posts here. Basically all seen here in the index - 
[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)
Pending is usually the same as as highest dated entry (ck. modified entry

---

### Post by Chanath on 2015-05-10
> **mc4man said:**
> There are multiple links to 'current' Desktop images for Ubuntu 15.04 as per several posts here. Basically all seen here in the index - 
[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)
Pending is usually the same as as highest dated entry (ck. modified entry

Well, these are two different isos. I am writing from the iso from the 2nd source. It is just like a normal Ubuntu. Ubuntu Next is the one that doesn't work.

---

### Post by ventrical on 2015-05-10
Works fine here from wily-desktop-amd64.iso (ubuntu-unity) as well as all of my other upgraded systems.

---

### Post by mc4man on 2015-05-10
> **Chanath said:**
> Ubuntu Next is the one that doesn't work.
post 16  gives you a pretty good description of ubuntu next, I'd just call it currently worthless & of no concern for Desktop users

---

### Post by sammiev on 2015-05-10
I noticed the two May 10 daily ISO posted here both had different md5sums. Both matched there downloads.

I will try the one posted by mc4man here shortly.

Update: That did the trick. Thanks

---

### Post by cecilpierce on 2015-05-11
So far so good...

---

### Post by Chanath on 2015-05-11
> **mc4man said:**
> post 16  gives you a pretty good description of ubuntu next, I'd just call it currently worthless & of no concern for Desktop users

You are right.

---

