---
title: "Trying to convince an IE only site to work in Linux"
date: 2009-05-18
forum: Wine
---

### Post by lsemmens on 2009-05-18
My bank claims to support firefox for windoze but will not come at a secure OS, so that does not help me. Even FF 4 Windoze does not work so their claim is a load of you know what! End of winge!

Can anyone suggest a way of convincing a site that is IE specific to load in FF or another browser. IE view works fine for me in Windoze but not in Jaunty. I am a complete novice in things Linux, but am comfortable digging around in the Windoze registry, so am willing to try. Please excuse what may be dumb questions.(If any of the mods think this is better in absolute beginner forum - I'm happy about that.)

I cant seem to convince Wine to run IE. If I open Browse C:\ Drive in Wine and navigate to home/me/.wine/dosdevices/c:/Program Files/Internet Explorer and double click on iexplore.exe as I could in Windoze all I get is a blank window titled "Wine Internet Explorer" The only option there is to minimise/maximise/Close the window.

I thought that all that would be needed was to attempt to re-install IE through WINE.

I run into problems again in that I get a pop-up saying "Unable to find a volume for file extraction. Please verify that you have proper permissions."

I thought that I could work around that using Terminal "sudo wine IE8-WindowsXP-x86-ENU.exe" and I get a message saying "wine: /home/me/.wine is not owned by you" and here I run into my kack of knowledge.

---

### Post by cogadh on 2009-05-18
[NEVER RUN WINE WITH SUDO!]("http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014")

Now that you have tried running it with sudo, you will need to fix the permissions on your .wine directory:
```
sudo chown -R user:user .wine
```

As for running IE, it won't work in Wine via normal means, you need to get [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") and run it that way

---

### Post by 0bso on 2009-05-18
[User agent switcher](https://addons.mozilla.org/en-US/firefox/addon/59) for firefox is what you are looking for. 

I'm not sure what you mean about firefox "will not come at a secure OS". As long as it is a https:// address it will be just as secure in FF as IE. 

If you **have** to have IE check out IEs4Linux.

---

### Post by aysiu on 2009-05-18
If you use Opera, there are two separate site preferences: *identify as Internet Explorer* and *mask as Internet Explorer*.

Maybe give Opera a try?

---

### Post by Jive Turkey on 2009-05-18
Find a new bank, tell your old bank exactly why you left.  The invisible hand (fist) of the marketplace is the best solution for most problems.

---

### Post by Cope57 on 2009-05-18
> **0bso said:**
> [User agent switcher](https://addons.mozilla.org/en-US/firefox/addon/59) for firefox is what you are looking for. 

I'm not sure what you mean about firefox "will not come at a secure OS". As long as it is a https:// address it will be just as secure in FF as IE. 

<snip>
This I will agree with.
I have used the agent switcher for many sites which "require IE" to view it. Most of the time, it is just to run some activeX application that you really do not need.

If a website built their site to [web standards]("http://www.w3.org/"), they will not need some gimmick to block the other [28 browsers available]("http://en.wikipedia.org/wiki/List_of_web_browsers").

If a website needs a certain browser to view it, send a email to the web master or the company themselves to mention the non-standard code which most likely [does not verify.]("http://www.w3.org/QA/Tools/#validators")

---

### Post by javyn999 on 2009-05-18
When all else fails, there's always virtualization

---

### Post by lsemmens on 2009-07-03
Thanks for the suggestions, all. To answer "will not come at a secure OS" - means it doesn't like a secure operating system like Linux. for some reason they seem to like Windoze. 

Anyway, problem solved. As Javyn has suggested a virtual box solved it. So WINE gets the flick and eventually the bank will, too, meantime, I must keep up with it as mpst of our regular payments come out of it and go into it for now.

Thanks for all your suggestions.

---

