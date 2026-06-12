---
title: "Super minimalistic browsers"
date: 2012-06-22
forum: The Cafe
---

### Post by spupy on 2012-06-22
I'm not talking Midori.

I'm talking Uzbl, Luakit, Vimprobable, Surf, etc. Are you using one? What made you choose one? How is day-to-day browsing?

I'm a long-time user of Vimperator/Pentadactyl, which vim-ifies Firefox. Unfortunatelly, firefox is still underneath, and it's kind of heavy for my netbook. Since the only thing that I do with the browser is browsing, I decided  to try something smaller and faster. I'm typing this right now from inside Luakit, I also have uzbl installed, but I tried configuring neither.

I'm making this as a poll, if I missed any entries, I will try to add them (not sure if I can edit a poll after its creation.)

EDIT: A clarification. Lynx, Links, w3c, etc., are also minimalistic browsers, but their engines are somewhat lacking. Properly displaying web-pages is a feature I can't leave out in favor of minimalism.

---

### Post by |{urse on 2012-06-22
Hey, you forgot links.

[http://en.wikipedia.org/wiki/Links_(web_browser](http://en.wikipedia.org/wiki/Links_(web_browser))

---

### Post by spupy on 2012-06-22
> **|{urse said:**
> Hey, you forgot links.

[http://en.wikipedia.org/wiki/Links_(web_browser)](http://en.wikipedia.org/wiki/Links_(web_browser))

Yeah, I know about Links and the similar. I didn't include them as options since they don't fit with what I had in mind. They are definitely minimalistic browsers, but their backends (or rather rendering engines, I'm not sure what the correct technical term is) are lacking. The ones I listed use Gecko/Webkit/etc, so you can resonably expect that most webpages will be displayed correctly.

Also, you have an error in your formatting: the closing bracket is outside the URL tag, so the link appears as broken.

---

### Post by Elfy on 2012-06-22
> **spupy said:**
> ... if I missed any entries, I will try to add them (not sure if I can edit a poll after its creation.)

Pretty sure you can't - you can ask someone who can though if needed :)

---

### Post by |{urse on 2012-06-22
> **spupy said:**
> Yeah, I know about Links and the similar. I didn't include them as options since they don't fit with what I had in mind. They are definitely minimalistic browsers, but their backends (or rather rendering engines, I'm not sure what the correct technical term is) are lacking. The ones I listed use Gecko/Webkit/etc, so you can resonably expect that most webpages will be displayed correctly.

Also, you have an error in your formatting: the closing bracket is outside the URL tag, so the link appears as broken.

All I did was paste the url, works fine. You mean the right parenthesis at the end? That's properly formatted. So you only want super-minimalistic browsers that feature well known rendering engines. In that case, I vote for Dillo.

---

### Post by spupy on 2012-06-22
> **|{urse said:**
> All I did was paste the url, works fine. You mean the right parenthesis at the end? That's properly formatted. So you only want super-minimalistic browsers that feature well known rendering engines. In that case, I vote for Dillo.

It's properly formatted in my post where I quote your post (I fixed it there). If you click the link in your post it will appear broken.

And yes, a well-known rendering engine that displays web-pages correctly is must-have feature for me. I can't drop it in favor of minimalism. There is a fine line between minimalism and using *curl* or *wget* to fetch web pages then read them with *less*. :D

---

### Post by neu5eeCh on 2012-06-22
I haven't tried any of these, but now that you've given me this list, I'm going to.

---

### Post by neu5eeCh on 2012-06-22
<rant> Yeah... ok... stuff like this really ------ me off.  I download Surf and the README says:

> 
In order to build surf you need GTK+ and Webkit/GTK+ header files.OK, except that this isn't what these files are called. I don't know why these uber-geeks can't just give the rest of us mere mortals the **_names_** of the d----d files. Substitute an x for the version number if they have to. </rant>

So... can anyone tell this ignorant being (referring to me) what files I should look for in synaptic or what files I should *sudo apt-get install*?

---

### Post by spupy on 2012-06-22
> **VTPoet said:**
> <rant> Yeah... ok... stuff like this really ------ me off.  I download Surf and the README says:

OK, except that this isn't what these files are called. I don't know why these uber-geeks can't just give the rest of us mere mortals the names of the d----d files. Substitute an x for the version number if they have to. </rant>

So... can anyone tell this ignorant being (referring to me) what files I should look for in synaptic or what files I should *sudo apt-get install*?

Sorry I can't help you, I haven't tried Surf myself - the "build it yourself" and "configure by recompiling" really puts me off, even though I have no problem recompiling programs to fix minor annoyances. 

I would advise not starting with Surf, rather one of the others. Luakit and UZBL are available in the ubuntu repos; for Vimprobable2 you need to add an extra repository - I can't recall how and which one, but it's easy to google for.

Another thing: from these only UZBL(-tabbed) and LuaKit have tabs. For Surf and Vimprobable you need an external tabbing application - [like *tabbed* from suckless.org]("http://tools.suckless.org/tabbed")

---

### Post by HappinessNow on 2012-06-22
voted:
Other (that I missed and haven't added)

dare I say,** Chrome** on Chrome OS on a dedicated Chromebook.

---

### Post by neu5eeCh on 2012-06-22
Just came home and thought I'd try Laukit. It's the same B.S.. The Readme rattles off a bunch of required files for compiling, but the developers *really can't be bothered* to actually give anyone the names of the actual files. Instead, I have to guess, then try to compile in terminal, then the terminal will tell me what files are missing, but they _also_ won't be names that synaptic can reference. ](*,) Terminal says I need webkit-1.0. OK, *sudo apt get install webkit-1.0*. Oh... that file doesn't exist? I'll look for it in Synaptic. Nope. Not there either. Then I'll spend an effing-hour fishing around for whatever it's *really* called. I'll google. I'll search the ubuntu forums, etc, etc.... I mean: How hard can it be? If they don't want to maintain a PPA, I get it; but give us some **_names_**.

**Edit:** By the way, have you tried Qupzilla?

---

### Post by Simian Man on 2012-06-22
This thread reminded me that I wanted to try vimperator.  I'm giving it a shot now and might try the others listed if I don't like it.

> **VTPoet said:**
> How hard can it be? If they don't want to maintain a PPA, I get it; but give us some **_names_**.

Dude, chill out.  The names of the packages you need depend on the distribution.  It isn't that hard to figure out what package you need.  Just google the name of the library with the distro you're using.

---

### Post by neu5eeCh on 2012-06-22
> **Simian Man said:**
> It isn't that hard to figure out what package you need.  Just google the name of the library with the distro you're using.

Yeah... but no. Tried that. It doesn't work.

Anyway, soon as I've got a couple hours to spend on this, I *will* get around to trying some of these browsers.

---

### Post by Toz on 2012-06-22
> **VTPoet said:**
> <rant> Yeah... ok... stuff like this really ------ me off.  I download Surf and the README says:

OK, except that this isn't what these files are called. I don't know why these uber-geeks can't just give the rest of us mere mortals the **_names_** of the d----d files. Substitute an x for the version number if they have to. </rant>

So... can anyone tell this ignorant being (referring to me) what files I should look for in synaptic or what files I should *sudo apt-get install*?

Here is one way that I figure out which dev packages need to be installed. When you run **make** in the surf directory, you'll get an error message like this:
> Package webkit-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `webkit-1.0.pc'


I then use the apt-file command (you may need to install the package first) to find which package contains that file:
```
apt-file search webkit-1.0.pc
libwebkitgtk-dev: /usr/lib/pkgconfig/webkit-1.0.pc
```

The I install the missing package:
```
sudo apt-get install libwebkitgtk-dev
```

I didn't get an error for the GTK dev packages so I must already have them installed. But use the same procedure above and it will help you to locate the missing package.

---

### Post by neu5eeCh on 2012-06-22
Thanks Toz, I'll try that.

---

### Post by David Andersson on 2012-06-23
A few years back there was **dillo** in the repos. I used it when I had to google something really quick. (Now I am only using Firefox, Chromium and Epiphany. I think they are the opposite to minimalistic. Maximalistic?)

---

### Post by spupy on 2012-06-23
> **VTPoet said:**
> Just came home and thought I'd try Laukit. It's the same B.S.. The Readme rattles off a bunch of required files for compiling, but the developers *really can't be bothered* to actually give anyone the names of the actual files. Instead, I have to guess, then try to compile in terminal, then the terminal will tell me what files are missing, but they _also_ won't be names that synaptic can reference. ](*,) Terminal says I need webkit-1.0. OK, *sudo apt get install webkit-1.0*. Oh... that file doesn't exist? I'll look for it in Synaptic. Nope. Not there either. Then I'll spend an effing-hour fishing around for whatever it's *really* called. I'll google. I'll search the ubuntu forums, etc, etc.... I mean: How hard can it be? If they don't want to maintain a PPA, I get it; but give us some **_names_**.

**Edit:** By the way, have you tried Qupzilla?

Why are you trying to compile Luakit? It's in the repos. (At least here on 12.04)

---

### Post by codingman on 2012-06-23
I use chrome and chromium. I'm not really a guy who frets about his browser every 5 minutes, so therefore I do not use stuff like Links and Surf. I just use chrome and it's mama because they are both very lightweight.

---

### Post by spupy on 2012-06-23
> **codingman said:**
> I use chrome and chromium. I'm not really a guy who frets about his browser every 5 minutes, so therefore I do not use stuff like Links and Surf. I just use chrome and it's mama because they are both very lightweight.

They are good enough if you have a reasonable powerful computer. I use them on my desktop & work machines as well. (Although I'm starting to move to Firefox, since Vimperator/Pentadactyl are much better than the corresponding chrome/ium plugin.)

But even chromium stutters and occasionally freezes on my netbook. Later versions have started to become bloated. It's sad, but I can't notice much difference in the speed of Firefox vs Chrome/ium.

---

### Post by neu5eeCh on 2012-06-23
OK. I got Luakit up and running. It doesn't seem any faster at rendering pages than Firefox, and it's already ballooned up to 158 Mib (having watched a video and having closed the tab). That's with four pages open. Seems to suffer the same memory hungry proclivities as FF and Chrome -- and that's surprising given that Luakit isn't running any extensions.

The minimalist interface is cool but (being harshly pragmatic) doesn't give me anything more than what I've got with FF (in terms of screen real-estate).

I thought I'd try adding adblock according to the luakit - browser framework page, but contrary to their instructions, there's no globals.lua in the luakit directory. All in all, not impressed. :popcorn:

On to the next "micro" browser.

---

### Post by vasa1 on 2012-06-23
> **codingman said:**
> I use **chrome and chromium**. I'm not really a guy who frets about his browser every 5 minutes, so therefore I do not use stuff like Links and Surf. I just use chrome and it's mama because they are both very lightweight.

Just curious but what's the reason for using both?

---

