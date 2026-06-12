---
title: "A few unity questions"
date: 2011-05-06
forum: The Cafe
---

### Post by user1397 on 2011-05-06
First off, I don't hate unity or any other DE.

Second, I understand this has probably been discussed before, but it's kinda hard to sift through a million unity threads.

Basically, what was the prime reason or hurry for canonical to make unity? Especially with regards to it being default in 11.04?

What was the biggest beef canonical had about gnome3?  If there was such a problem with gnome3, could they not have just stuck to gnome2 for 11.04 and maybe released 11.10 with gnome3 if sufficient bugs had been squashed?

Isn't having two interfaces (unity and gnome3) which are largely similar (although still different) not an efficient use of time or resources?

Just some questions I'd like to sort out in my head, thanks.

---

### Post by NormanFLinux on 2011-05-06
Unity was started to address the issue of the Linux desktop being hard for average people to use.

By setting things to a default configuration, the operating system like Windows is ready to go. Unlike power users, John and Jane Joe don't care to tweak their system. They just want to use it with a minimum of hassle.

Unity is Canonical's response to them. That annoys power users who like to mess around with everything but the concept is that Linux is not just for geeks.

And if Canonical succeeds with Unity, everyone will find Linux as easy to use as Windows and Mac OSX.

---

### Post by ikt on 2011-05-06
> **ubuntuman001 said:**
> Basically, what was the prime reason or hurry for canonical to make unity? Especially with regards to it being default in 11.04?

To get as many bugs fixed as possible before Ubuntu 12.04 LTS.

> **ubuntuman001 said:**
> 
Isn't having two interfaces (unity and gnome3) which are largely similar (although still different) not an efficient use of time or resources?

Not necessarily, some would say isn't having KDE, Unity, Gnome 3, LXDE, XFCE, and other Desktop Environments a waste of time and resources, we should have 1 desktop that everyone likes... some people feel that is not ideal.

---

### Post by 3Miro on 2011-05-06
You know Unity is just interface on top of Gnome, right? 11.04 comes with Gnome2.

They "rushed" Unity since Gnome3 is already out. This is the perfect time for Unity, they get to fix problems, then get 11.10 out and then get something very stable for 12.04 LTS.

I don't know about Canonical, but I see Gnome-shell as a very deficient UI. You can hardly do anything without going trough the zoom animation over and over. If you keep both hands on the keyboard, GS is fine, but if you want to use mostly the mouse, GS is incredibly slow. Bottom line, Gnome-shell is great, but only for a relatively small subset of users. Canonical is trying to get as many users as possible.

Some people look at division in Linux as a weakness and a waste of resources. I look at it as strength. Competition and natural selection make for better software. You have two visions that will compete and we will only benefit from it, yet there is nothing in Gnome-shell that Unity cannot "borrow" and vice-versa. Think about Intel vs AMD, would it be better if they unite and work together on a single project or would you rather they keep on "fighting" each other.

---

### Post by user1397 on 2011-05-06
> **NormanFLinux said:**
> Unity was started to address the issue of the Linux desktop being hard for average people to use.

By setting things to a default configuration, the operating system like Windows is ready to go. Unlike power users, John and Jane Joe don't care to tweak their system. They just want to use it with a minimum of hassle.

Unity is Canonical's response to them. That annoys power users who like to mess around with everything but the concept is that Linux is not just for geeks.

And if Canonical succeeds with Unity, everyone will find Linux as easy to use as Windows and Mac OSX.I had not thought about it this way before, very well said.

> **ikt said:**
> Not necessarily, some would say isn't having KDE, Unity, Gnome 3, LXDE, XFCE, and other Desktop Environments a waste of time and resources, we should have 1 desktop that everyone likes... some people feel that is not ideal.I see what you mean, I was just noting how unity and gnome3 seem very similar in the way they do things, as compared to say the difference between gnome3 and kde, but you do have a point.

> **3Miro said:**
> You know Unity is just interface on top of Gnome, right? 11.04 comes with Gnome2.Yea I know, I only write it this way to differentiate between canonical's interface and gnome.org's interface.

[QUOTE=3Miro]They "rushed" Unity since Gnome3 is already out. This is the perfect time for Unity, they get to fix problems, then get 11.10 out and then get something very stable for 12.04 LTS.

I don't know about Canonical, but I see Gnome-shell as a very deficient UI. You can hardly do anything without going trough the zoom animation over and over. If you keep both hands on the keyboard, GS is fine, but if you want to use mostly the mouse, GS is incredibly slow. Bottom line, Gnome-shell is great, but only for a relatively small subset of users. Canonical is trying to get as many users as possible.

Some people look at division in Linux as a weakness and a waste of resources. I look at it as strength. Competition and natural selection make for better software. You have two visions that will compete and we will only benefit from it, yet there is nothing in Gnome-shell that Unity cannot "borrow" and vice-versa. Think about Intel vs AMD, would it be better if they unite and work together on a single project or would you rather they keep on "fighting" each other.[/QUOTE]
I guess I have to play around with gnome3 (gnome-shell) more, last time I used it it seemed uncannily similar to unity in most ways.

---

### Post by 3rdalbum on 2011-05-07
Ubuntu has not shipped a vanilla Gnome desktop for years. In fact, they've spent a lot of time writing additions and patches to the Gnome desktop, that have rarely/never been adopted upstream. Even when they work really well, make sense, and have been adopted by KDE.

To switch to Gnome 3 would be to dump all that work and lose a lot of Ubuntu-specific things that Ubuntu users like, such as indicators and notifications. If those things could be rewritten to work on the Gnome 3 desktop UI, then they risked being broken and needing to be rewritten at any time during the Gnome development.

So Unity was created instead, so Ubuntu can have a desktop environment headed by its own direction, rather than relying on the hostile developers at Gnome.

---

### Post by NCLI on 2011-05-07
> **ubuntuman001 said:**
> First off, I don't hate unity or any other DE.

Second, I understand this has probably been discussed before, but it's kinda hard to sift through a million unity threads.

Basically, what was the prime reason or hurry for canonical to make unity? Especially with regards to it being default in 11.04?
If Canonical had waited to make Unity default, many people, seeking the bleeding edge, would first have switched to Gnome 3, then to Unity. This way, users only have to get use to one new interface in Ubuntu.

Besides, it would take quite a lot of work to integrate Gnome-Shell with the various Ubuntu projects, like the Indicator Applets.

> What was the biggest beef canonical had about gnome3?  If there was such a problem with gnome3, could they not have just stuck to gnome2 for 11.04 and maybe released 11.10 with gnome3 if sufficient bugs had been squashed?
The biggest beef was probably the lack of cooperation. More on that [here]("http://www.markshuttleworth.com/archives/654").

> Isn't having two interfaces (unity and gnome3) which are largely similar (although still different) not an efficient use of time or resources?
Definitely. However, since Canonical has its own vision, and the Gnome team were unwilling to adjust their design at all, I definitely understand why they decided to strike out on their own.

Interestingly, a Unity-like launcher was added to Gnome Shell after the split was announced...

---

### Post by leviathan8 on 2011-05-07
Hi.
This might be a little off the topic, but I have one concern regarding the next LTS version (12.04). So far, I like unity very much, no problem with that! But I am scared with the change to Wayland. Is it going to affect my drivers? I only care about wl and fglrx for now. I've also experienced lots of crashes with compiz activated on my laptop, and disabling it fixed the problem, but will 12.04 ship with compiz?
Cheers.

---

### Post by NCLI on 2011-05-07
> **leviathan8 said:**
> Hi.
This might be a little off the topic, but I have one concern regarding the next LTS version (12.04). So far, I like unity very much, no problem with that! But I am scared with the change to Wayland. Is it going to affect my drivers? I only care about wl and fglrx for now. I've also experienced lots of crashes with compiz activated on my laptop, and disabling it fixed the problem, but will 12.04 ship with compiz?
Cheers.
If Wayland isn't ready, it certainly won't be in the LTS. As it stands, Wayland probably won't be default sooner than 2013. Of course, I don't know whether Canonical has a secret crack team working on it as we speak, so it may or may not be ready before then, but I feel very confident in saying that the very earliest we're going to see it included as the default is 12.10.

---

### Post by 3rdalbum on 2011-05-07
> **leviathan8 said:**
> Hi.
This might be a little off the topic, but I have one concern regarding the next LTS version (12.04). So far, I like unity very much, no problem with that! But I am scared with the change to Wayland. Is it going to affect my drivers? I only care about wl and fglrx for now. I've also experienced lots of crashes with compiz activated on my laptop, and disabling it fixed the problem, but will 12.04 ship with compiz?
Cheers.

My understanding is that Wayland can run on top of X, using X drivers. It can also run standalone, and X can run inside Wayland too.

Wayland is probably not worth worrying about at the moment - it's probably **at least** 18 months until it ships as default in Ubuntu. And the thing with X is that it's been around since forever... so if you have a problem with Wayland, you should just be able to _apt-get install xserver-xorg_.

If Wayland gets to the point where it looks like shipping in Ubuntu, I'm sure ATI will write a driver directly for it.

---

### Post by grahammechanical on 2011-05-07
Read the blog and you will have a greater understanding of why there is change.

[http://www.markshuttleworth.com/](http://www.markshuttleworth.com/)

See the headings "All the Other Guys are not Wrong," and "Internal Competition is healthy, but depends on strong and mature leadership." Read between the lines.

Regards.

---

