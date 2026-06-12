---
title: "Gnome 3.8 to get a classic mode"
date: 2012-11-22
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2012-11-22
I know Raring won't get the full 3.8 treatment but many of us use PPA's so:

[http://www.webupd8.org/2012/11/gnome-shell-38-to-get-classic-mode.html](http://www.webupd8.org/2012/11/gnome-shell-38-to-get-classic-mode.html)

Sounds like it'll be accomplished via extensions though so still probably the end of the road for good ole Metacity :(

---

### Post by dino99 on 2012-11-22
Seems like gnome team is restyling/redesigning their features roadmap :P due to too numerous G2 followers  :P (like me)

---

### Post by Stinger on 2012-11-22
> **kansasnoob said:**
> I know Raring won't get the full 3.8 treatment but many of us use PPA's so:

[http://www.webupd8.org/2012/11/gnome-shell-38-to-get-classic-mode.html](http://www.webupd8.org/2012/11/gnome-shell-38-to-get-classic-mode.html)

Sounds like it'll be accomplished via extensions though so still probably the end of the road for good ole Metacity :(
yeah I know, to bad for low spec pc's that fallback mode is dropped.
of course you can always use Xubuntu or Lubuntu but it's not the same as Gnome. :(

But.... As I already have a working Gnome 3.6, I'm currently trying on [MATE]("http://mate-desktop.org/") from [here]("http://www.linuxmint.com/rel_nadia_whatsnew.php#mate").
I'm amazed, it's rock solid, low on resources and really fast, you should give it a try on your old hardware ;)
Maybe UGR should include MATE as fallback ?

BTW 'good ole Metacity' is now ['Marco']("https://github.com/mate-desktop/mate-window-manager") 

Cheers.

---

### Post by jbicha on 2012-11-22
> **Stinger said:**
> 
Maybe UGR should include MATE as fallback ?


Absolutely not. The Ubuntu GNOME Remix is for people that like what GNOME is doing.

In fact, I blame the MATE developers for wasting time with their "let's copy and rename everything GNOME 2" instead of working to improve the fallback mode. Even now, the last gnome-panel maintainer has said that he doesn't plan to do any more releases but would be happy to turn maintainership over to someone that wants to keep it going.

We won't even ship Cinnamon (at least not in its current form) and that is a much smarter fork (2 or 3 packages instead of ~65 packages).

Anyway, I don't think we'll include gnome-panel by default in 13.04 but we'll probably include the classic extensions (disabled by default) whenever we ship GNOME 3.8.

---

### Post by Stinger on 2012-11-22
@jbicha
I take this as a big NO to my question above :biggrin::biggrin:

---

### Post by kansasnoob on 2012-11-22
> **jbicha said:**
> Absolutely not. The Ubuntu GNOME Remix is for people that like what GNOME is doing.

In fact, I blame the MATE developers for wasting time with their "let's copy and rename everything GNOME 2" instead of working to improve the fallback mode. Even now, the last gnome-panel maintainer has said that he doesn't plan to do any more releases but would be happy to turn maintainership over to someone that wants to keep it going.

We won't even ship Cinnamon (at least not in its current form) and that is a much smarter fork (2 or 3 packages instead of ~65 packages).

Anyway, I don't think we'll include gnome-panel by default in 13.04 but we'll probably include the classic extensions (disabled by default) whenever we ship GNOME 3.8.

I actually hope to be able to keep following Ubuntu-GNOME because there's a lot I actually do like about it, but I also find a lot to like about Unity other than the use of Compiz as the one and only window manager.

Mutter certainly runs much lighter than Compiz but it's still more resource hungry than Metacity. Of course Openbox is another viable option but I just love Metacity :)

And the new 'gnome-panel' was truly excellent! Smartest redesign I'd seen in ages!

Of course I realize Mate has forked Metacity (renamed Marco) to work with Mate's gnome-2-ish hacks but I have doubts about the ongoing viability (and security) regarding Mate :redface:

For now I'm shifting my focus almost entirely to Lubuntu which had been my plan A for 12.04 because I maintain a bunch of PC's with P4M800 graphics, but they didn't do an LTS so I did this:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

And I find it to be incredibly stable, in fact I now have about 20 PC's running that setup and the only complaint I hear relates to the lack of the Clearlooks theme ...... but I've found Clearwaita to be just too unstable so it really just amounts to a few days of usage for someone to get used to the difference in scrollbar color / contrast.

Regardless I truly appreciate all of the changes over the past few dev cycles. We're just getting more, and more options :D

---

### Post by sgage on 2012-11-22
> **jbicha said:**
> Absolutely not. The Ubuntu GNOME Remix is for people that like what GNOME is doing.

In fact, I blame the MATE developers for wasting time with their "let's copy and rename everything GNOME 2" instead of working to improve the fallback mode. Even now, the last gnome-panel maintainer has said that he doesn't plan to do any more releases but would be happy to turn maintainership over to someone that wants to keep it going.

We won't even ship Cinnamon (at least not in its current form) and that is a much smarter fork (2 or 3 packages instead of ~65 packages).

Anyway, I don't think we'll include gnome-panel by default in 13.04 but we'll probably include the classic extensions (disabled by default) whenever we ship GNOME 3.8.

I totally agree. The Mint gang seems to have a desire to put their stamp on everything instead of working-with. Why fork Gnome 2 into MATE? Why not work on the Fallback (or Classic) mode for Gnome 3? Why not offer a package of nicely crafted Gnome Shell extensions instead of Cinnamon? Was there a reason to fork Gnome Shell instead? 

Oh well, that's just how it is in the Free Software world. Egos sometimes get in the way of cooperation. I guess that's just how it is in the world, period.

---

### Post by MG&amp;TL on 2012-11-22
> **sgage said:**
> I totally agree. The Mint gang seems to have a desire to put their stamp on everything instead of working-with. Why fork Gnome 2 into MATE? Why not work on the Fallback (or Classic) mode for Gnome 3? Why not offer a package of nicely crafted Gnome Shell extensions instead of Cinnamon? Was there a reason to fork Gnome Shell instead? 

Oh well, that's just how it is in the Free Software world. Egos sometimes get in the way of cooperation. I guess that's just how it is in the world, period.

Completely agree with you. To be fair to the LM team, "offer[ing] a package of nice crafter Gnome Shell extensions" was exactly what they did a couple of releases back, and that was frankly horrible. There was about four ways to find applications.

---

### Post by ELD on 2012-11-22
I think it's a great idea, they devs finally realise what users want, a little late though.

Also to the Mint naysayers about the gnome 2 fork, well canonical didn't do much better did they - creating Unity again completely seperated from Gnome 3 shell and fallback.

I do think MATE is quite pointless though since Cinnamon offers up exactly what Gnome 2 users would want.

See it from both sides folks.

I think all are valid and all have their place.

---

### Post by Stinger on 2012-11-22
> **ELD said:**
> 
I think all are valid and all have their place.
+1 for that, thanks :wink:
Mate has it's advantage when it comes to being low on resources CPU/GPU and RAM compared to Cinnamon/Gnome-Shell and especially Unity.

---

### Post by Mr.JJ on 2012-11-23
> **jbicha said:**
> Absolutely not. The Ubuntu GNOME Remix is for people that like what GNOME is doing.

This is one of the reasons I love ubuntu gnome and Jeremy. Follow gnome completely/truthfully (Remember, our initial goal is to attract gnome developers?). This is also the reason that give me the feel/confidence that I might continue using ubuntu gnome for a long time.

---

### Post by kansasnoob on 2012-11-23
> **Mr.JJ said:**
> This is one of the reasons I love ubuntu gnome and Jeremy. Follow gnome completely/truthfully (Remember, our initial goal is to attract gnome developers?). This is also the reason that give me the feel/confidence that I might continue using ubuntu gnome for a long time.

Yeah, I'd prefer to see all of the "flavors" stay as close as possible to upstream. That means keep Lubuntu as close as possible to LXDE, Xubuntu as close as possible to Xfce, etc, etc. Of course that means not breaking anything for Ubuntu itself which I'm sure is incredibly challenging.

The biggest challenge for me ATM is deciding which DE I truly prefer. I feel like a kid in a candy store :guitar:

---

### Post by screaminj3sus on 2012-11-24
> **sgage said:**
> I totally agree. The Mint gang seems to have a desire to put their stamp on everything instead of working-with. Why fork Gnome 2 into MATE? Why not work on the Fallback (or Classic) mode for Gnome 3? Why not offer a package of nicely crafted Gnome Shell extensions instead of Cinnamon? Was there a reason to fork Gnome Shell instead? 

Oh well, that's just how it is in the Free Software world. Egos sometimes get in the way of cooperation. I guess that's just how it is in the world, period.

They tried offering gnome-shell extensions instead of cinnamon at first. Extensions weren't powerful/flexible enough to do what they wanted. Cinnamon was a reasonably sensible fork, unlike MATE.

---

### Post by Stinger on 2012-11-24
I didn't realize there was so much intolerance and hate towards the MATE DE in these forums, I apologize for my suggestion.

I hope You'll all play nice now and stay on topic.
( but honestly I couldn't care less ) :P

---

### Post by kansasnoob on 2012-11-25
> **Stinger said:**
> I didn't realize there was so much intolerance and hate towards the MATE DE in these forums, I apologize for my suggestion.

I hope You'll all play nice now and stay on topic.
( but honestly I couldn't care less ) :P

I just have doubts about the security of using old Gnome 2 forked apps in a newer Gnome distro :oops:

---

