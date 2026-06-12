---
title: "Pandemic - C#/Mono IM Client"
date: 2008-06-05
forum: The Cafe
---

### Post by klange on 2008-06-05
[img]http://pandemic.oasis-games.com/icon.png[/img]

[Main Site](http://pandemic.oasis-games.com)
[Preview release](http://pandemic.oasis-games.com/release/0.0.0-pre) - June 8th, 2008

Pandemic is work-in-progress instant messaging client and server. About a year and half ago I wrote up a protocol in Python, as well as a Windows client in .NET. I'd been neglecting to truly port it to Linux for a while now, but finally took the initiative. 

Short term plans for the client and server include more IRC-like features for chat rooms, server-side friend list storage, and a new, direct file transfer system. Long term plans include streaming video.

[img]http://pandemic.oasis-games.com/shots/prealpha/login.png[/img] [img]http://pandemic.oasis-games.com/shots/prealpha/friendslist.png[/img]
[img]http://pandemic.oasis-games.com/shots/prealpha/convo.png[/img]
[img]http://pandemic.oasis-games.com/shots/prealpha/formatting.png[/img]
[img]http://pandemic.oasis-games.com/shots/prealpha/chatroom.png[/img]

I'm still working on a few key features before a true release, but a preview will be available over the weekend so you can check it out. The first true release (0.0.1) will come next weekend, after I implement an updated network interface (so you can use multiple accounts on different servers). The next release will take advantage of some server updates.

Finally, all code is under GPL v3, including the server (which I need to clean and make a package for, it's rather sketchy right now and is over a year old, so it needs some updating). I'll get a PPA up as soon as I learn the basics of Deb packaging, but until then I'll be releasing source packages in tarbells, as well as (for the lazy), compiled binaries.

**e**: Interfacing with purple or Telepathy to support other protocols *is* a future goal, but it's more long term (even more than video support), and it'll probably stick to the basics of the other protocols (like Pidgin does). Hopefully I'll have the time to do it myself, if not, I encourage anyone who wants to try to do it once the client is ready.

[size="1"](I know, I already posted this in the Programming forum. I figure with my plans for a preview release this weekend it would be a good idea to post here.)[/size]

---

### Post by hanzomon4 on 2008-06-05
WOw, this app is gorgeous

---

### Post by Retrospekt on 2008-06-05
Definitely can't wait for the Alpha release. :D

---

### Post by Le-Froid on 2008-06-05
It looks *amazing*! Will be sure to check it out :)

---

### Post by Polygon on 2008-06-05
what protocols does it support?

does it follow your GTK theme or is it just gonna be black?

why not use libpurple or telepathy like you said and then work from there?

what features distinguishes this program from others like pidgin?

---

### Post by klange on 2008-06-06
> **Polygon said:**
> what protocols does it support?
**Right now, just mine, but when I integrate with Telepathy, it'll support quite a few.**

does it follow your GTK theme or is it just gonna be black?
**lol, that is my GTK theme. Want some pics with Clearlooks?**

why not use libpurple or telepathy like you said and then work from there?
**Because I want to get the client working properly first, I've never used either of them and don't know the ins and outs of using them.**

what features distinguishes this program from others like pidgin?
**At the moment, probably just the Gecko widget (which you can do some pretty amazing style things with). In the future, under my own protocol, video streaming and a few other things.**

The thing with using my own protocol is that anything you want me to add, I can try and add.

**e**: [Here's Clearlooks](http://pandemic.oasis-games.com/shots/prealpha/clearlooks.png). Isn't there a version of Clearlooks with RGBA support? I should probably get that...

---

### Post by Polygon on 2008-06-06
i was just wondering if it followed your gtk theme or not, since i couldent seen the rest of your desktop since you just posted the screenshots of the program.

but looking good. I read on wikipedia that telepathy can also support libpurple so hopefully this will be a good form of competition for pidgin. They need it.

---

### Post by klange on 2008-06-06
Still got some things to clear up, but it should be ready for the preview tomorrow or Sunday.

---

### Post by klange on 2008-06-08
And as promised, I think I have everything working.

0.0.0-pre is ready.

[Official Site](http://pandemic.oasis-games.com/) (needs a lot of work, but has links to both the first release (probably buggy as hell), the README, and the registration tool.

[Screenshot](http://pandemic.oasis-games.com/shots/prealpha/Pandemic_Pre.png) from my other machine, which happens to also be the machine running the only major Pandemic server.

You can read the full article on the release from [my site](http://oasis-games.com/article.php?id=122), as well as post comments if you register on the site.


For those too lazy to read the README:
The source package is fairly simple to install. You need mono-gcms and libgecko2.0-cil, and then it's the standard routine:
```
./configure && make && sudo make install
```
Run it with "pandemic".
It should install to /usr/local/share/panmono, so you're going to want to go there and edit the file "friends" and add some names when the time comes. This is just a temporary solution to the lack of extra dialogs and to bridge the gap between now and when I add the new friends list stuff to the server.

---

### Post by FFighter on 2008-06-08
Congrats, great work.

Do you plan on releasing the source? I'd very interested in it!

---

### Post by bobbocanfly on 2008-06-08
> **FFighter said:**
> Congrats, great work.

Do you plan on releasing the source? I'd very interested in it!

The source is at [http://pandemic.oasis-games.com/release/0.0.0-pre/panmono-0.0.0_pre.tar.gz](http://pandemic.oasis-games.com/release/0.0.0-pre/panmono-0.0.0_pre.tar.gz)

---

### Post by smartboyathome on 2008-06-08
Just installed it via compiling on arch and got this error:
```
Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Gecko.WebControl ---> System.DllNotFoundException: libgtkembedmoz.so
  at (wrapper managed-to-native) Gecko.WebControl:gtk_moz_embed_get_type ()
  at Gecko.WebControl.get_GType () [0x00000] 
  at GtkSharp.GeckoSharp.ObjectManager.Initialize () [0x00000] 
  at Gecko.WebControl..cctor () [0x00000] --- End of inner exception stack trace ---

  at MainWindow..ctor () [0x00000] 
  at PanMono.MainClass.Main (System.String[] args) [0x00000] 

```

---

### Post by klange on 2008-06-08
> **smartboyathome said:**
> Just installed it via compiling on arch and got this error:
```
Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Gecko.WebControl ---> System.DllNotFoundException: libgtkembedmoz.so
  at (wrapper managed-to-native) Gecko.WebControl:gtk_moz_embed_get_type ()
  at Gecko.WebControl.get_GType () [0x00000] 
  at GtkSharp.GeckoSharp.ObjectManager.Initialize () [0x00000] 
  at Gecko.WebControl..cctor () [0x00000] --- End of inner exception stack trace ---

  at MainWindow..ctor () [0x00000] 
  at PanMono.MainClass.Main (System.String[] args) [0x00000] 

```

Well, that answers my questions.
Install libmono-mozilla0.1-cil.

---

### Post by klange on 2008-06-08
It appears I screwed up a file name and didn't notice it.
Executing from "pandemic" in your bin path will fail upon trying to load a particular image. I've uploaded what should be a fix, so if you downloaded before 2:52PM EDT, you need to redownload. I'm going to push it to git...
([Commit diff here](http://git.ogunderground.com/?p=pandemic/.git;a=blobdiff;f=PanMono/MainWindow.cs;h=eeef14b5082cdef20f9db190b9dc678d15cb6711;hp=84516caf2901b83d8d316ba0a878c93a53c060e8;hb=a8471f56874c7b52111e27fdacc5f730485b159f;hpb=65319c3de0695a012329bdcc7e48819f55504d88))

And again...
[...](http://git.ogunderground.com/?p=pandemic/.git;a=blobdiff;f=PanMono/MainWindow.cs;h=8b18fcbc3e53ed0430319264a41188e6f548b170;hp=eeef14b5082cdef20f9db190b9dc678d15cb6711;hb=fe1870eb2f3e1bc3098b2e9aeae56169d9a852cf;hpb=a8471f56874c7b52111e27fdacc5f730485b159f)

[*expletive*](http://git.ogunderground.com/?p=pandemic/.git;a=blobdiff;f=PanMono/PandemicConvo.cs;h=36dab704eb682b806b9d25884d84686461890bdb;hp=271ccd13fe388643257dc0493118e0dbfd56d307;hb=cc942963cd11f8b8a1aebb7cfeeb0e0ae05be622;hpb=fe1870eb2f3e1bc3098b2e9aeae56169d9a852cf)
Clearly I'm not good at finding my own bugs.

[Hopefull that's it?](http://git.ogunderground.com/?p=pandemic/.git;a=blobdiff;f=PanMono/PandemicConvo.cs;h=60139f033fce24df9b5500afe656236a88aa918d;hp=36dab704eb682b806b9d25884d84686461890bdb;hb=9b7e3a44ae21d2ba7df13a8f4c04a300217fb4b5;hpb=cc942963cd11f8b8a1aebb7cfeeb0e0ae05be622)

Right, so now I can open it, log in, start a conversation, talk to someone not on my friends list, and join a chat room. *phew*. That should do it. If there are any more bugs I missed, I'll fix them after work / on my lunch break tomorrow. Gah, the torments of a one-man development team!

---

### Post by Retrospekt on 2008-06-08
I got it to work just by simpling:

cd Desktop
cd PanMono-linux
sh pandemic

Works fine for me, althought I don't know if the actual messaging works yet.

---

### Post by klange on 2008-06-08
> **Retrospekt said:**
> I got it to work just by simpling:

cd Desktop
cd PanMono-linux
sh pandemic

Works fine for me, althought I don't know if the actual messaging works yet.
And now we're in a conversation :)
Anyway, as I said on Pandemic, the binary packages aren't really effected by the problems I spent the last half hour fixing because you run it from its own directory, so it would load the images just fine. With the source package, it would look in your current directory when you ran "pandemic", so it wouldn't find the images (which is a fatal error when creating a new Pixbuf...). Should be all fixed up now, unless I missed one that I didn't notice through my testing.

---

### Post by Le-Froid on 2008-06-08
Wow. just compiled from source, logged on, started convo (with myself :p), and have to say, amazing work!! :)

---

### Post by Yes on 2008-06-08
Do you have a .tar.gz of libmono-mozilla0.1-cil?  I can't find it online and the Arch repos don't have it.

---

### Post by klange on 2008-06-08
> **Yes said:**
> Do you have a .tar.gz of libmono-mozilla0.1-cil?  I can't find it online and the Arch repos don't have it.
It's in the Mono source, but you can get a deb from [the Ubuntu packages site](http://packages.ubuntu.com/hardy/all/libmono-mozilla0.1-cil/download).

---

### Post by smartboyathome on 2008-06-08
I investigated, it IS installed with mono (deb2targz'd it and it contains files already available). It seems to not be compatible with the new mono that is in arch though, as Ubuntu contains the 0.1 version, and arch contains the 0.2 version. :(

---

### Post by klange on 2008-06-08
> **smartboyathome said:**
> I investigated, it IS installed with mono (deb2targz'd it and it contains files already available). It seems to not be compatible with the new mono that is in arch though, as Ubuntu contains the 0.1 version, and arch contains the 0.2 version. :(
Should be backwards compatible... At any rate, hack the configure script.

---

### Post by smartboyathome on 2008-06-08
What version of firefox would this happen to be built on? Seems like it is missing libgtkembedmoz.so which is included with Firefox (I think).

---

### Post by klange on 2008-06-08
Did you get libgecko2.0-cil? The bindings should be in there, and I believe the package should depend in some way on whatever package has the library.

---

