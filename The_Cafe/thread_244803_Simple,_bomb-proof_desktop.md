---
title: "Simple, bomb-proof desktop?"
date: 2006-08-26
forum: The Cafe
---

### Post by hizaguchi on 2006-08-26
My grandmother just turned 88 and has never used a computer in her life.  She's got some friends that recently moved halfway around the world and she's got no way of talking to them now.  I'm thinking she could also use a nice photo album of the family.

I've got an older desktop collecting dust in my spare bedroom, and I was thinking I'd stick a nice, stable OS on there with an incredibly simplified UI and give it to her.  If it's going to work though, it's gotta be simple.  I mean braindead simple.  She doesn't know how to use a mouse.

How would you go about doing this?  I'm thinking XFCE with a couple BIG icons on the desktop for email and photos.  The only buttons on the windows being big red "X"s for close (no minimize, that leads to "The window just disappeared!").  No main menu.  No desktop right-click window.  Basically nothing at all but the bare essentials for looking at pictures and sending email.

But I need suggestions on how to pull this off.  I need to be able to lock things down so that the launcher icons don't get lost, and I need to hide anything that could possibly be confusing.  I'm also open to more interface ideas to make things as intuitive as possible for someone who has no idea how to use a computer.  And if you've done anything like this, please help me anticipate problems that are going to pop up. :)

---

### Post by nalmeth on 2006-08-26
Yeah, you're on the right track. It shouldn't be hard to do.

If she really doesn't need ANY gui options, and only 2 programs, then why not strip right down to fluxbox, disabling the rightclick menu and desktop switching. That way she has a barebones simple panel, with a clock. All you would have to do is setup the two icons (fbdesk) on the desktop, and blow them up big. You will get a super fast desktop, simplified to almost nothing.

On the other hand, XFCE has a nice smooth looking appearance out of the box, and can be cut down to the bone too. Yeah, maybe just go with xfce. Stripped down it will be quite fast too.

---

### Post by RRS on 2006-08-26
I agree that Xubuntu would be the simpler for you to set up and probably just as fast stripped down as suggested.

Couple additions though, since you probably don't want or need any visible panels add a nice "Off" button to the desktop and also set the timeout in grub to give just enough time for you to get into recovery mode for any future adjustments/updates/etc.

Setting her user name to auto-log-in without a sudo password might be a good idea too.

---

### Post by nalmeth on 2006-08-26
Have you though about what email client you're going to setup for her? I don't use clients much, I'm more webmail oriented, but thunderbird seems quite simplified to me..

What about the photo manager? I think I would replace gqview with eye of gnome.

Unfortunatley, I don't think you can change to single-click mouse behavior in xfce.. That's something she'll have to get used to

---

### Post by fuscia on 2006-08-27
openbox is pretty simple and un****upable. you can set up the right click menu for her and she'll be fine.

---

### Post by 3rdalbum on 2006-08-27
Tip with setting up the e-mail client: Set it so that it automatically checks the e-mail.

I simply can't convince my grandad to click the "Send/Recieve Mail" button. He keeps forgetting that the e-mail doesn't just drift into the mailbox by its own accord.

Call the ISP that she'll be using, and ask if they can put a block on files that are bigger than a certain amount. My uncle keeps sending my grandfather large video files, which is stupid considering he's on dialup, and he thinks that if his e-mail doesn't pop up IMMEDIATELY that he doesn't have any.

XFCE is a good choice. You can set it up so that the icons in the launcher are huge. If you look in the hidden folders in the home directory, you should be able to find a file which contains the launcher preferences; just set that so only root can modify it.

---

### Post by slimdog360 on 2006-08-27
Dont know if they would run but Mandrivia is very user friendly and Ive heard freespire is similar. Mandrivia uses kde but perhaps you could strip it down and put xfce on there to make it run better.

---

### Post by GarethMB on 2006-08-27
Perhaps Picasa for the photographs, as it can recursively scan the whole PC, whilst giving the impression of everything being in one unified place. That said i haven't really used the linux version or any of it's competitors.

Personally, I'd use KDE because I use it in a minimal way anyway. Plus it's really easy to customise the menu's in the KDE apps itself, which is a must. What's the point in having 3 buttons on the desktop if there's 3 times this in the app.
With KDE you'll also be able to disable many if not all of the right click actions, thus eliminating accidental popups of confusing menus. I've attatched a quick example, by modifying my current set up. I didn't want to spend forever, getting everything back to the way it should be but you get the idea.

---

### Post by curuxz on 2006-08-27
LOL I love your screenshot, the perfect system for someone who does not know about computers, a standard web browser and the most advanced drawing system linux has to offer. I hope eveyone else can see the irony ;)

---

### Post by GarethMB on 2006-08-27
Lol, it was the only 'photo editor' I have. And I read all of my mail via web mail. So I couldn't put the 'right' launchers, consider this POC.

---

### Post by Kimm on 2006-08-27
I experimented a bit and came up with this:

[[IMG]http://img246.imageshack.us/img246/8833/simpleuh4.th.png[/IMG]](http://img246.imageshack.us/my.php?image=simpleuh4.png)

Its the XFCE4 desktop, using blackbox as its windowmanager.
For imageviewing I'd suggest just creating a launcher for eog or gqview that always starts in the same folder as the pictures are in.

And to lock down the desktop:
sudo chown -R root:root Desktop ;)

Edit:
You could also use a bigger Analog clock... that one wouldnt resize.

---

### Post by %hMa@?b&lt;C on 2006-08-27
If you give her a GMail account, I have written a program that is a web browser that I could make only have a Close Button, and ONLY be able to visit Gmail. Tell me if you want that, or if you want other sites to be able to use.  It is the totall easy app to use.

---

### Post by Cynical on 2006-08-27
Well you could just as easily register at gmail and setup thunderbird

---

### Post by Super King on 2006-08-27
Just throwing out a suggestion for a photo viewer: F-Spot (in the repositories, similar in concept to Picasa). Very simple, non-confusing look, plus only one click away from starting a slideshow (something which may be useful to her).

---

### Post by hizaguchi on 2006-08-27
Wow, lots of great ideas.  I hadn't even considered KDE because there are so many menus, but that screenshot is exactly the kind of thing I think she needs.  I had planned on using F-spot for pictures, as suggested above, but a stripped-down konqueror with some cleverly configured profiles could possibly do everything she needs all in one window.  Starting it fullscreen at login eliminates the desktop situation all together.  Of course, that sacrifices some of the handy features of F-spot that she may actually use (especially if I pre-tag all the pictures with the names of the people in them), and unless there's a Kmail kpart she'd have to use Gmail, which has lots of buttons I can't do much about.  Definately an angle I hadn't seen before though.  Now I've got double the tinkering to do. :)

I'm going to try and stay away from the minimal WMs because I'm holding onto hope that later if she gets better at using it she'll want more functionallity and start using the computer more completely.  If that happens, Openbox is a less friendly environment than the more graphical environments, and is more difficult for me to modify to an intermediate setup.

Keep the ideas comming!  This is great.

---

### Post by Bezmotivnik on 2006-08-27
> **nalmeth said:**
> Have you though about what email client you're going to setup for her? I don't use clients much, I'm more webmail oriented, but thunderbird seems quite simplified to me..

I say avoid Thunderbird...and ANY mail client.  They are all nosebleeds and all of them exceed her needs and abilities.

For this, find the simplest-interface free-webmail site (NOT Yahoo or HotMail or the complicated ones) and set up an account for her.

Find the emptiest, blankest interface page with the fewest options, [like this one]("http://www.email.is/login.asp").

---

### Post by gnomeuser on 2006-08-27
One thing you might consider is Sugar, the interface for the 100$ laptop. It seems fairly straight forward and to the point when it comes to functionality.

It's all python AFAIK and it should be pretty unbreakable as we all geared towards people with little computing experience. 

The thing about given such people computers is that you'd want them to have a pleasant experience, it's not just a means of sending emails, they should be able to discover functionality and play with it. It's a fun tool even for an 88 year old.

---

### Post by hizaguchi on 2006-08-27
Oh yeah, I definately agree that she should be able to play with it.  The problem though is that I live 100 miles away from her, and nobody else in my family is able to fix their own computer problems, let alone other people's problems without any good background information.  And escpecially not on anything other than Windows.

I don't wanna give her Windows because it'll be spywared and virused in about a month (no, I mean NO technical knowledge).  And I don't wanna give her a default KDE desktop right off when she doesn't even know what a mouse is and an uneducated user can destroy usability way faster than a virus.

I figure I'll lock it all down at first, and gradually introduce her to the other features once she gets past the initial culture shock.

---

### Post by gnomeuser on 2006-08-27
> **hizaguchi said:**
> Oh yeah, I definately agree that she should be able to play with it.  The problem though is that I live 100 miles away from her, and nobody else in my family is able to fix their own computer problems, let alone other people's problems without any good background information.  And escpecially not on anything other than Windows.

I don't wanna give her Windows because it'll be spywared and virused in about a month (no, I mean NO technical knowledge).  And I don't wanna give her a default KDE desktop right off when she doesn't even know what a mouse is and an uneducated user can destroy usability way faster than a virus.

I figure I'll lock it all down at first, and gradually introduce her to the other features once she gets past the initial culture shock.

Remote management and one step cd imaging might be for you.. we could probably cook up a system akin to that used in OLPC that you can just boot off a CD and reimage the entire thing to a working state.. that might work for her.

---

