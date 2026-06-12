---
title: "How did Zorin make the Zorin 7 Menu?"
date: 2013-11-26
forum: Ubuntu, Linux and OS Chat
---

### Post by electricrider on 2013-11-26
Zorin 7 has a nice sleek menu. How did they make this? I'm looking for something similar for my Ubuntu 13.10.

I do know at one time I could right click on the Zorin Menu button and get the properties and credits for the zorin menu.. either i didn't simply right click the menu button or i found it's properties someplace else, (Or I could but an update fixed/hid the info?) but i cannot seem to find those properties again.. ( a lil help here if you know.. thanks)

(edit: still cant find this same info but I can pull up Gnomenu in Synaptic and look at properties. It doesn't have the credits but says Gnomenu version 2.9.0.1 is installed.)

Anyway.. I remember the credits said the Zorin Menu (at least in part) made by a fellow who works for the Gnomenu Team It listed his name and the Gnomenu Team as credits for the menu. BUT.. Zorin 7 is running on 12.04 - I tried and couldn't get Gnomenu working in 12.04 - I have no idea how they pulled it off - this looks like a heavily modified Gnomenu if it is one at all.

Any ideas to either get this or something similar working in 13.10 ?

---

### Post by Frogs Hair on 2013-11-26
The Gnomenu which I used was for Gnome 2 and won't work in the unity panel or the classic session. If it is open source then the code or package is available . I can't answer how the Gnomenu was modified or if you could get it working easily on Ubuntu 13.10. A similar style menu is available for XFCE .     [http://www.webupd8.org/2013/07/whisker-menu-update-brings-support-for.html](http://www.webupd8.org/2013/07/whisker-menu-update-brings-support-for.html)

---

### Post by electricrider on 2013-11-27
Thanks. 

That menu looks nice. I'll see how far I can work with it. I was hoping to get a Gnomenu fork working in Mate but the ones I've seen aren't as good.  

I hear Xfce uses lots of config files for customization.... as I know you'll see this.. can you point me into a good direction to learn how to manipulate Xfce.. er.. for non programmers LOL.. Thanks.

---

### Post by Frogs Hair on 2013-11-27
> for non programmers :( I think some programming or at least command skills would be required. 

[http://wiki.xfce.org/howto/customize-menu](http://wiki.xfce.org/howto/customize-menu)

[http://docs.xfce.org/](http://docs.xfce.org/)

[https://wiki.archlinux.org/index.php/xfce](https://wiki.archlinux.org/index.php/xfce)

---

### Post by electricrider on 2013-11-27
Thanks..

I tried Whisker last night and found it's just the same as any other menu editor - they all have the same features.. edit submenus, not the categories, and not the style of the menu itself - aside from editing these submenus, none of these editors have any real customization - none of them do anything I want or need. 

This includes Whisker, and a bunch I've tried for Mate as well as XFCE (Xame).

It's sad. The Linux world brags about how customizable Linux is but no one has yet made a GUI to do the real work. Even editing the kml files it seems XFCE has very little customization (looking at your links) I didn't see where you actually need any programming language for any of it, it looks all XML.. I don't want to re-arrange things normal users use. I want to revamp the entire style and layout of the main menu as well as the other menus used to create a new animal. (without using themes or third party eye candy) I want to change the Main Categories, arrange them as I see fit etc. (I know I can rename them editing xml files), but I want to go way beyond this. 

I want to use custom menus and submenus to list my apps in the main menu where I want it.. Globally without having to worry about where the installer wants to put the shortcuts for the file.. it should be my choice.. The installer should ask me where I want the shortcuts to be created, like in Windows.  ( In other words, I don't want conflicts between my choice of where to put the shortcuts conflicting with the installers desire. I understand the main program may need to be in a certain area but everything in the main menu should be my choice without the installer screwing up the install.  I have read this can happen if you try to make these changes globally - and there is no need to have such tight restrictions on something so trivial. 

Aside from editing the Categories which is hard for those apps to do I'd still expect way more customization out of Linux apps that edit the menus. I'm finding it really hard to believe no one has made such a tool as I need but I can't find one anywhere.  I guess I'll keep looking.

You say, " The Gnomenu which I used was for Gnome 2 and won't work in the unity panel or the classic session."

Do you mean to tell me you are actually the person who made the menu for Zorin? If so, congrats and apologies for stepping on your toes LOL.. it's not my intention to say Zorin isn't good enough, I love Zorin 7 but I would like to see some of my ideas come to life. The Zorin devs have some Gnome 2 installed, some Gnome 3.8, some KDE and you make it all work nice together - something I couldn't do while trying to get Gnomenu working in 13.04. I wouldn't expect the Zorin devs to tell me exactly how they pulled it off that's why I didn't ask in the Zorin forum.. still can't blame a guy for trying LOL. Besides, I want something for 13.10. I can't wait to see what Zorin is going to do for a menu in the next release now that they can no longer use Gnomenu. I don't think Zorin will get as nice a looking menu any other way judging by the tools i'm finding.

---

### Post by Frogs Hair on 2013-11-27
> Do you mean to tell me you are actually the person who made the menu 

Absolutely Not ! Zorin 7 is based on Ubuntu 13.04 (Gnome 3.6) and the interface is developed by Zorin . Gnome 2 used the Bonobo panel not present in Gnome 3 and Mate which is a Gnome 2 fork project is the closest match available. The Gnomenu was originally made to work with the Bonobo panel. I have looking on launchpad to try to locate the Zorin packages because knowing the package names would be helpful in your quest.

---

