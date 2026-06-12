---
title: "Debian Wheezy May Ship With XFCE As The Default Desktop Environment"
date: 2012-08-08
forum: The Cafe
---

### Post by y6FgBn)~v on 2012-08-08
An interesting read this morning;

[http://www.muktware.com/4087/debian-wheezy-may-ship-xfce-default-desktop-environment](http://www.muktware.com/4087/debian-wheezy-may-ship-xfce-default-desktop-environment)

---

### Post by Primefalcon on 2012-08-08
> **pcybill said:**
> An interesting read this morning;

[http://www.muktware.com/4087/debian-wheezy-may-ship-xfce-default-desktop-environment](http://www.muktware.com/4087/debian-wheezy-may-ship-xfce-default-desktop-environment)
and Gnome3 loses yet more traction.... by this time next year gnome3 will be dead! Mhuahahahaha.... well no it will have a lot less usage than it even does now!

---

### Post by t0p on 2012-08-08
I never reckoned much to Xubuntu.  I know XFCE is very much like Gnome 2; but if a light-weight DE is really what they're after, why not try LXDE?  I have lubuntu on my ancient Asus EeePC 701 (still alive after 5 years of abuse!) and I find its LXDE to be very nice.  It's unobtrusive, and it's easy to add bigger-style apps (eg vlc, gimp) if you want.  Is XFCE truly light-weight any more?  Stuff I've read here and there lead me to believe it's rather bloated these days.

---

### Post by Version Dependency on 2012-08-08
Glad to see a distro that doesn't want to use Gnome 3 do the sensible thing and switch to XFCE...instead of all these "protest distros" out there that stick to Gnome 2, which has been dead well over a year now, thinking that it is going to somehow come back to life.

---

### Post by MadmanRB on 2012-08-08
Good decision methinks

---

### Post by vasa1 on 2012-08-08
> **t0p said:**
> ... Is XFCE truly light-weight any more?  Stuff I've read here and there lead me to believe it's rather bloated these days.
Yes, it seems to have legs. This business about how Xfce is bloated without mentioning any details ;)

Bit pointless.

---

### Post by mips on 2012-08-08
> **t0p said:**
> Is XFCE truly light-weight any more?  Stuff I've read here and there lead me to believe it's rather bloated these days.

[http://blog.xfce.org/2012/05/questions-after-the-4-10-release/](http://blog.xfce.org/2012/05/questions-after-the-4-10-release/)

> **[SIZE="3"]LXDE still consumes less memory[/SIZE]**

*sigh* I&#8217;m not going to rant on this because as a user you should choose the desktop that makes you happy, but anyway it annoys me a tiny bit. So just to throw some information:

LXDE and Xfce are both based on the same toolkit and provide roughly the same set of features. That as a start makes it technically almost impossible to be much better or worse regarding memory usage. I think this whole myth started by comparing two distributions (clue: strcmp (distro_a + 1, distro_b + 1) == 0).

I&#8217;m sure Xfce consumes a bit more memory, because more processes are started. Especially when external plugins are added to the panel: a design decision to make the panel more stable.

I don&#8217;t know or care where this comparison started, but if somebody does this again the the future, please compare the actual memory usage and don&#8217;t use free. Or even better: don&#8217;t compare memory usage at all because it is pretty useless.
**That said: if I start a [COLOR="Red"]default[/COLOR] LXDE and Xfce 4.10 desktop (default Arch Linux packages) and use ps_mem.py, Xfce consumes 2 MiB more memory (same or desktop-equal applications are started). Do whatever you want this is number, as long as you compare apples and apples.**

---

### Post by malspa on 2012-08-08
It "ensures that the desktop will fit on CD#1, which gnome currently does not."

My last two Squeeze installations, I went with Xfce, anyway. Seems to me that Debian is one distro where "default desktop environment" is almost meaningless.

---

### Post by Bigtime_Scrub on 2012-08-08
> **Version Dependency said:**
> Glad to see a distro that doesn't want to use Gnome 3 do the sensible thing and switch to XFCE...instead of all these "protest distros" out there that stick to Gnome 2, which has been dead well over a year now, thinking that it is going to somehow come back to life.

You mean much like Ubuntu with its "Unity" protest......

Debian going to Xfce would be cool. I don't think they would do it for the speed of Xfce, I think it would be for the functionality and familiarity.

Even Fedora, the biggest Gnome centric distro there is may switch to Mate, which is not all that surprising. Image Red Hat customers using Gnome shell. (LOL) If Mate is default in Fedora then that is the death knell for Gnome-Shell. Mate will for sure be in the Fedora repositories.

---

### Post by malspa on 2012-08-08
> **Bigtime_Scrub said:**
> Even Fedora, the biggest Gnome centric distro there is may switch to Mate, which is not all that surprising. Image Red Hat customers using Gnome shell. (LOL) If Mate is default in Fedora then that is the death knell for Gnome-Shell.

Who says Fedora is even considering switching to MATE as the default? By the way, I've been using GNOME Shell in Fedora 16, and it's great.

---

### Post by Bigtime_Scrub on 2012-08-08
> **malspa said:**
> Who says Fedora is even considering switching to MATE as the default? By the way, I've been using GNOME Shell in Fedora 16, and it's great.

I've been using Fedora with Cinnamon since its been available. 

Fedora is shipping Mate in the repositories for Fedora 18 if it is fully available by the time the release rolls around. It may or may not be the default but at least a spin is probable. 

For sure getting in the repos if it is ready by F18
[http://fedoraproject.org/wiki/Features/MATE-Desktop](http://fedoraproject.org/wiki/Features/MATE-Desktop)
[http://news.slashdot.org/story/12/07/31/1831233/fedora-18-to-feature-the-gnome2-fork-mate](http://news.slashdot.org/story/12/07/31/1831233/fedora-18-to-feature-the-gnome2-fork-mate)

Don't know if this story is true or not...
[http://digitizor.com/2012/07/31/fedora-mate-gnome/](http://digitizor.com/2012/07/31/fedora-mate-gnome/)

Still the question remains, will Red Hat use Gnome Shell? I doubt it. And if Red Hat doesn't use it, then why would Fedora?

---

### Post by malspa on 2012-08-08
> **Bigtime_Scrub said:**
> Don't know if this story is true or not...
[http://digitizor.com/2012/07/31/fedora-mate-gnome/](http://digitizor.com/2012/07/31/fedora-mate-gnome/)

Well, check out the comments following the article.

I haven't seen anything from Fedora other than that MATE will be included; check out the Fedora 18 feature list: [https://fedoraproject.org/wiki/Releases/18/FeatureList#Fedora_18_Spins](https://fedoraproject.org/wiki/Releases/18/FeatureList#Fedora_18_Spins)

Fedora being a kinda bleeding-edge distro, I can't see them wanting to go back in time with MATE as the default.

---

### Post by forrestcupp on 2012-08-08
This is an interesting move. Personally, I like Gnome 3 with Gnome Shell a lot. I don't prefer the new Nautilus, though.

> **t0p said:**
> I never reckoned much to Xubuntu.  I know XFCE is very much like Gnome 2; but if a light-weight DE is really what they're after, why not try LXDE?  I have lubuntu on my ancient Asus EeePC 701 (still alive after 5 years of abuse!) and I find its LXDE to be very nice.  It's unobtrusive, and it's easy to add bigger-style apps (eg vlc, gimp) if you want.  Is XFCE truly light-weight any more?  Stuff I've read here and there lead me to believe it's rather bloated these days.I think a growing number of Xfce users are starting to care more about having a Gnome replacement than having a lightweight OS. I never understood the people who have a terabyte of RAM and they stress over keeping their OS down to using a few megabytes.

---

### Post by Smilax on 2012-08-08
XFCE, works the way u want to



not the way some UI geek decided you should

---

### Post by cariboo on 2012-08-08
Unity is also available in Fedora, so it could ship with it as a DE:

[http://spins.fedoraunity.org/](http://spins.fedoraunity.org/)

---

### Post by drawkcab on 2012-08-08
Xfce will seem bloated if you're running xubuntu.  Xfce on Debian flies.  I'm not in a position to speculate on what accounts for the difference but it is certainly noticeable.

Xfce 4.8 and 4.10 show a trajectory towards Gnome 2.x which seems to be what a large number of users are wanting.  It's not surprising that many distros are shifting their default DE to xfce.  I personally prefer Gnome 2.x but XFCE 4.8 fits the bill well enough at this point.

LXDE is a solid DE, and a spectacular lightweight DE.  It is improving but it does not have the functionality of xfce yet.  What I mean is that those Gnome 2.x refugees will find LXDE too sparse and xfce, by comparison, more like what they are used to.

I use Gnome shell on my HTPC and I've used it on my primary laptop.  I think there are some reasons why it wouldn't appeal to the average desktop user but I also think it has a lot of potential in the long run if things were to move in the right direction.  Sadly Gnome shell seems to be moving in the wrong direction.

---

### Post by Hylas de Niall on 2012-08-08
> **malspa said:**
> It "ensures that the desktop will fit on CD#1, which gnome currently does not."

My last two Squeeze installations, I went with Xfce, anyway. Seems to me that Debian is one distro where "default desktop environment" is almost meaningless.

I downloaded beta 1 (gnome) disc1 and that fit on a cd just fine?
:confused:

---

### Post by Primefalcon on 2012-08-08
if you want a gnome 2.x esque feel, go xfce

if you need lightweight go either lxde or jwm

---

### Post by Linuxratty on 2012-08-08
> Does this move reflect less trust in Gnome 3?

Could be.:)

---

### Post by neu5eeCh on 2012-08-08
> **malspa said:**
> Who says Fedora is even considering switching to MATE as the default? By the way, I've been using GNOME Shell in Fedora 16, and it's great.

Reading the tea leaves, but I strongly suspect that Red Hat is having serious qualms about switching to Gnome Shell. And no, I don't care what they say publicly. The availability of MATE in Fedora tells me that somebody at Red Hat is quietly considering MATE  as their default desktop - though probably not Unity. I have a hard time imagining a business adopting G3S (or Windows 8 for that matter). Time will tell...

---

### Post by Bigtime_Scrub on 2012-08-08
> **VTPoet said:**
> Reading the tea leaves, but I strongly suspect that Red Hat is having serious qualms about switching to Gnome Shell. And no, I don't care what they say publicly. The availability of MATE in Fedora tells me that somebody at Red Hat is quietly considering MATE  as their default desktop - though probably not Unity. I have a hard time imagining a business adopting G3S (or Windows 8 for that matter). Time will tell...

That's exactly my whole argument. No way Unity makes it to Red Hat. I'd bet my house on that. I tried using it in Fedora and it was a pain in the butt to install and it wasn't stable either. 

The question remians though, why would Debian switch to Xfce deafult? I would think similar reasons.

---

### Post by neu5eeCh on 2012-08-08
> **Bigtime_Scrub said:**
> The question remians though, why would Debian switch to Xfce deafult? I would think similar reasons.

Well, the article states:

"The move comes mainly to make the distro lightweight and also reduce the size of the installation image."

I suspect the choice of XFCE also reflects the desire to appeal to the broadest base. G3S ain't it. KDE is _way_ too convoluted (yet weirdly less customizable than XFCE) to be anything like a general, simple and easy to use DE. LXDE is a niche DE for older computers that can be difficult to customize and, in that respect, is much less friendly than XFCE. MATE may or may not survive the next year. I think everyone is waiting for MATE to establish itself as a DE in its own right, not just zombie Gnome. And then there's "Jeff Hoagland's" poor ol' Enlightenment, who everyone forgets to mention (and Jeff has to run around saying "Hey! Me too! Hey!?!" I think Enlightenment is *still* in Beta? I should give Bodhi another try. Last time I tried it, everything felt kind of cheap - for lack of a better word.

---

### Post by Primefalcon on 2012-08-08
> **VTPoet said:**
> Well, the article states:

"The move comes mainly to make the distro lightweight and also reduce the size of the installation image."

I suspect the choice of XFCE also reflects the desire to appeal to the broadest base. G3S ain't it. KDE is _way_ too convoluted (yet weirdly less customizable than XFCE) to be anything like a general, simple and easy to use DE. LXDE is a niche DE for older computers that can be difficult to customize and, in that respect, is much less friendly than XFCE. MATE may or may not survive the next year. I think everyone is waiting for MATE to establish itself as a DE in its own right, not just Zombie Gnome. And then there's "Jeff Hoagland's" poor ol' Enlightenment, who everyone forgets to mention (and Jeff has to run around saying "Hey! Me too!" I think Enlightenment is *still* in Beta? I should give Bodhi another try. Last time I tried it, everything felt kind of cheap - for lack of a better word.
theres awesome and jwm

---

### Post by neu5eeCh on 2012-08-08
> **Primefalcon said:**
> theres awesome and jwm

And Cinnamon. I forgot Cinnamon. But, at this point, Cinnamon just feels like a less flexible and customizable version of XFCE that's built on Gnome. To me, the only reason to use Cinnamon is if you just *have* to have the Gnome base. 

XFCE, right now, seems to have really hit the sweet spot. It's filling the niche that G2 used to occupy.

---

### Post by Primefalcon on 2012-08-08
> **VTPoet said:**
> And Cinnamon. I forgot Cinnamon. But, at this point, Cinnamon just feels like a less flexible and customizable version of XFCE that's built on Gnome. To me, the only reason to use Cinnamon is if you just *have* to have the Gnome base. 

XFCE, right now, seems to have really hit the sweet spot. It's filling the niche that G2 used to occupy.
Agreed it's what I have recommend if someone really does hate Unity tbh.... frankly I think Unity rocks

---

### Post by cariboo on 2012-08-08
> **VTPoet said:**
> Reading the tea leaves, but I strongly suspect that Red Hat is having serious qualms about switching to Gnome Shell. And no, I don't care what they say publicly. The availability of MATE in Fedora tells me that somebody at Red Hat is quietly considering MATE  as their default desktop - though probably not Unity. I have a hard time imagining a business adopting G3S (or Windows 8 for that matter). Time will tell...

You do know that RedHat employs Gnome's core developers, and according to[ jono's blog post]("http://www.jonobacon.org/2012/07/30/staring-into-the-abyss-some-thoughts/") RedHat is pointing the way, where Gnome development is concerned.

---

### Post by BrokenKingpin on 2012-08-08
This is completely understandable, and would be pretty awesome. I have been using Xfce as my main DE for a few years, and love it. It is lightweight, but still looks really nice, and has all the features you need from a full DE.

---

### Post by neu5eeCh on 2012-08-08
> **cariboo907 said:**
> You do know that RedHat employs Gnome's core developers, and according to[ jono's blog post]("http://www.jonobacon.org/2012/07/30/staring-into-the-abyss-some-thoughts/") RedHat is pointing the way, where Gnome development is concerned.

But then in the comment section to that post you get this:

> Red Hat seems to view their contributions to Gnome as volunteering  weekends at the soup kitchen: good to do, profitless, and peripheral to  the rest of their livelihood. In other words, Canonical survived the  11.04 transition because they could pay their way through the perilous  time when the community recoiled. Gnome could not.  So Gnome doesn’t have the developer, testing, or design muscle to carry out their vision. 

In any case, whether Red Hat guided (or was behind) the development of G3S, I still suspect they may be having serious qualms. They have too much to lose by foisting a failed DE, by any standard, on valuable business customers. They're not Microsoft.

---

### Post by drawkcab on 2012-08-09
I just installed the voyager live respin of xubuntu today.  I think it shows what can be done with xfce.  Also of note is the implementation of xfce with applets from Mate that Linux Mint is using this time around.

---

### Post by mips on 2012-08-09
> **drawkcab said:**
> Xfce will seem bloated if you're running xubuntu.  Xfce on Debian flies.  I'm not in a position to speculate on what accounts for the difference but it is certainly noticeable.

+1 it's a night and day difference.

After using Crunchbang XFCE for a while I decided to try a Xubuntu base/cli install from the alternate iso image with vanilla xfce 4.10 and there is a BIG difference compare to normal Xubuntu. I'll be sticking with this setup in future as well.

---

### Post by tartalo on 2012-08-09
> **cariboo907 said:**
> Unity is also available in Fedora, so it could ship with it as a DE:

[http://spins.fedoraunity.org/](http://spins.fedoraunity.org/)

I'll make no bets but, while MATE is in the official Fedora roadmap [1] Canonical's Unity in Fedora is an unofficial port (via SUSE) [2]

[1] [https://fedoraproject.org/wiki/Features/MATE-Desktop](https://fedoraproject.org/wiki/Features/MATE-Desktop)
[2] [http://www.omgubuntu.co.uk/2012/07/unity-desktop-available-for-fedora](http://www.omgubuntu.co.uk/2012/07/unity-desktop-available-for-fedora)

BTW, you do know that Fedora's Unity project has nothing to do with Canonical's Unity DE, yes?

---

### Post by vasilbelarus on 2012-08-09
It is right way! I think.

---

### Post by kansasnoob on 2012-08-13
[http://anonscm.debian.org/gitweb/?p=tasksel/tasksel.git;a=commit;h=2a962cc65cdba010177f27e8824ba10d9a799a08](http://anonscm.debian.org/gitweb/?p=tasksel/tasksel.git;a=commit;h=2a962cc65cdba010177f27e8824ba10d9a799a08)

> switch default desktop task to xfce



This ensures that the desktop will fit on CD#1, which gnome currently does not.



There may be other reasons to prefer xfce as the default as well, but that

is a complex and subjective topic. Unfortunatly, Debian does not have a

well-defined procedure for making such choices, though it certianly has

well-defined procedures for reviewing them. So, I've decided to be bold,

and continue the tradition of making an arbitrary desktop selection for

Debian in tasksel.

Make what you will of that, but I'd stress the fact that Ubuntu chose Unity :D

Certainly not a great day for Gnome.

And add the fact that Ubuntu may actually use an older version of Nautilus:

[http://ubuntuforums.org/showpost.php?p=12159778&postcount=1](http://ubuntuforums.org/showpost.php?p=12159778&postcount=1)

Maybe the Gnome devs will smell the coffee :)

---

### Post by vasa1 on 2012-08-13
I don't know how decisions are made @ Debian but I think that that is just one person's proposal.

---

### Post by vexorian on 2012-08-13
> **vasa1 said:**
> I don't know how decisions are made @ Debian but I think that that is just one person's proposal.
It is a commit. So this person is not proposing as much as already updating the installer to use xfce by default.
[http://anonscm.debian.org/gitweb/?p=tasksel/tasksel.git;a=commitdiff;h=2a962cc65cdba010177f27e8824ba10d9a799a08;hp=e4e78e18196387582bba22f5603c0be57720c1ed](http://anonscm.debian.org/gitweb/?p=tasksel/tasksel.git;a=commitdiff;h=2a962cc65cdba010177f27e8824ba10d9a799a08;hp=e4e78e18196387582bba22f5603c0be57720c1ed)

---

### Post by kansasnoob on 2012-08-13
> **vexorian said:**
> It is a commit. So this person is not proposing as much as already updating the installer to use xfce by default.
[http://anonscm.debian.org/gitweb/?p=tasksel/tasksel.git;a=commitdiff;h=2a962cc65cdba010177f27e8824ba10d9a799a08;hp=e4e78e18196387582bba22f5603c0be57720c1ed](http://anonscm.debian.org/gitweb/?p=tasksel/tasksel.git;a=commitdiff;h=2a962cc65cdba010177f27e8824ba10d9a799a08;hp=e4e78e18196387582bba22f5603c0be57720c1ed)

+1!

I'm biased but I truly believe more distros should give Unity a fair look :D

---

### Post by vasa1 on 2012-08-13
> **vexorian said:**
> It is a commit. So this person is not proposing as much as already updating the installer to use xfce by default.
[http://anonscm.debian.org/gitweb/?p=tasksel/tasksel.git;a=commitdiff;h=2a962cc65cdba010177f27e8824ba10d9a799a08;hp=e4e78e18196387582bba22f5603c0be57720c1ed](http://anonscm.debian.org/gitweb/?p=tasksel/tasksel.git;a=commitdiff;h=2a962cc65cdba010177f27e8824ba10d9a799a08;hp=e4e78e18196387582bba22f5603c0be57720c1ed)
Okay but it looks like the user will be offered a choice (with xfce as a default):
> Template: tasksel/desktop
 Type: multiselect
-Choices: gnome, kde, xfce
-Default: gnome
+Choices: gnome, kde, xfce, lxde
+Default: xfce
 Description: The desktop environment to install when the desktop task is selected
  This can be preseeded to change the default.


---

### Post by kansasnoob on 2012-08-13
> **vasa1 said:**
> Okay but it looks like the user will be offered a choice (with xfce as a default):

Absolutely. Our "alternate install" CD is based on the 'debian-installer' and you can use any "d-i" to install what you want :D

I just think it's important that a base distro like Debian chose to use a DE other than Gnome after many, many years.

I also understand that Fedora 18 will include a Mate spin.

While I tend to prefer either Unity or LXDE (Lubuntu) I'd think that the Gnome devs would want to pay attention ;)

---

### Post by BigSilly on 2012-08-13
I think this is kinda sad really considering the history, but I suspect this has less to do with politics or a "Debian being Shell-refuseniks" issue, and more to do with the expectation that Debian is a lighter OS that works on all kinds of computers, and in turn it not requiring a graphics driver to run.

I agree that more distros should look into supplying Unity (and I suspect they will over time), but I would never expect a distro like Debian to supply it by default.

---

### Post by aussielife on 2012-08-13
[http://ubuntuforums.org/showthread.php?t=2039222&highlight=Debian+xfce+default](http://ubuntuforums.org/showthread.php?t=2039222&highlight=Debian+xfce+default)

---

### Post by madjr on 2012-08-13
that is probably nice, because people use debian for DIY like raspberry pi and like old computers and servers.

so not surprising they didn't go for gnome, unity, etc.

---

### Post by neu5eeCh on 2012-08-13
> **kansasnoob said:**
> +1!

I'm biased but I truly believe more distros should give Unity a fair look :D

Not only do I agree with that, but I think other distros should consider improving Unity and even forking it (if only to make it more customizable). I don't use Unity and won't until I can customize it, get rid of the completely superfluous and redundant launcher and have a menu system. I also find GS3's activity overview to be infinitely superior to Unity's lens's -- about the only thing I like about Gnome Shell. However, Unity's lenses could be easily improved if another distro got a hold of them - like Mint (though Cinnamon is very good).

---

### Post by overdrank on 2012-08-13
Threads merged

---

### Post by mastablasta on 2012-08-14
> **t0p said:**
> I never reckoned much to Xubuntu. I know XFCE is very much like Gnome 2; but if a light-weight DE is really what they're after, why not try LXDE? I have lubuntu on my ancient Asus EeePC 701 (still alive after 5 years of abuse!) and I find its LXDE to be very nice. It's unobtrusive, and it's easy to add bigger-style apps (eg vlc, gimp) if you want. Is XFCE truly light-weight any more? Stuff I've read here and there lead me to believe it's rather bloated these days.
 
 
LXDE is perhaps not as stable and featurefull. Most main programmes are still at version 0.9 or 0.7 and such. this tells quite a bit.

---

### Post by Ariya243 on 2012-08-14
Gnome 3 is going nowhere, but Gnome 2 would be dead. If anyone doesn't like to use Gnome-shell or even Unity, there are many ways to beautify your desktop like Awn and Cairo panels with Compiz on. Gnome 3 (and Unity) can stay underneath, but that's the power.

XFCE in pure form looks ugly with its dock etc, but with re-makings by Xubuntu and Voyager etc, it becomes beautiful. These days with faster computers and large memories, Gnome 3 isn't that bloated to become slow. 

Anyway, that's my opinion.:)

---

### Post by vasa1 on 2012-08-22
A little more (from May 2012, but still "interesting"): [Status of Xfce in Debian/Ubuntu]("http://lionel.lefolgoc.net/blog/article89/status-of-xfce-in-debian-ubuntu")

---

### Post by neu5eeCh on 2012-08-23
> **vasa1 said:**
> A little more (from May 2012, but still "interesting"): [Status of Xfce in Debian/Ubuntu]("http://lionel.lefolgoc.net/blog/article89/status-of-xfce-in-debian-ubuntu")

Interesting read. I personally could care less if something is gtk2 or gtk3. Seems like much ado about nothing. On the other hand, about the time the xfce devs decide to switch to gtk3, gtk4 will be released.

---

### Post by vasa1 on 2012-08-23
> **VTPoet said:**
> Interesting read. I personally could care less if something is gtk2 or gtk3. Seems like much ado about nothing. On the other hand, about the time the xfce devs decide to switch to gtk3, gtk4 will be released.

This gtk2 versus gtk3 is confusing. Why are most major browsers and LibreOffice still gtk2?

(Gnome's "Web" is gtk3. IIRC, Midori is still gtk2.)

---

### Post by neu5eeCh on 2012-08-23
> **vasa1 said:**
> This gtk2 versus gtk3 is confusing. Why are most major browsers and LibreOffice still gtk2?

(Gnome's "Web" is gtk3. IIRC, Midori is still gtk2.)

I just did a little googling and there's hardly any unanimity on the "improvements" of gtk3. Some devs seem to think gtk2 is more stable, faster and doesn't suffer from some of the regression they claim were introduced by gtk3. They could be right or wrong. I have no idea. If the browsers haven't switched, they probably find gtk2 to be adequate and can't be bothered making a switch that doesn't promise any real payback?

---

### Post by vasa1 on 2012-08-23
> **VTPoet said:**
> I just did a little googling and there's hardly any unanimity on the "improvements" of gtk3. Some devs seem to think gtk2 is more stable, faster and doesn't suffer from some of the regression they claim were introduced by gtk3. They could be right or wrong. I have no idea. If the browsers haven't switched, they probably find gtk2 to be adequate and can't be bothered making a switch that doesn't promise any real payback?

Here's something else I didn't know: [https://bugs.launchpad.net/midori/+bug/861351/comments/6](https://bugs.launchpad.net/midori/+bug/861351/comments/6)

---

### Post by jemadux on 2012-08-23
in my machine debian testing / is quite good and lightweight with gnome ... 
but imho xfce is not good enough  for a new user

---

### Post by vexorian on 2012-08-23
^It seems that Debian is becoming a distro "not for the new user".

> **vasa1 said:**
> This gtk2 versus gtk3 is confusing. Why are most major browsers and LibreOffice still gtk2?

(Gnome's "Web" is gtk3. IIRC, Midori is still gtk2.)
I would bet it is related to "too busy working on actual features than in becoming early adopters of a GUI toolkit that could change completely after 6 months and make us do all the work again.".

---

### Post by Random20210831 on 2012-08-23
> **pcybill said:**
> An interesting read this morning;

[http://www.muktware.com/4087/debian-wheezy-may-ship-xfce-default-desktop-environment](http://www.muktware.com/4087/debian-wheezy-may-ship-xfce-default-desktop-environment)

This will improve the Debian although the Gnome 2 and XFCE similar.

---

### Post by lykwydchykyn on 2012-08-23
I think XFCE is a really good fit for Debian.  Debian bills itself as "the universal operating system", and its release/development cycle prioritizes stability and simplicity. 

Among major DE's, XFCE is lightweight, has a familiar layout & design, and is quite mature and complete.  It's really a "no surprises" kind of environment.

Keep in mind Debian doesn't just run on x86/amd64 machines.  It supports 9 architectures and 2 (or is it 3 now?) kernels.  If you have to pick on DE to be default on all those platforms, things like hardware acceleration for compositing and other newer GPU features aren't a given.  

I don't see why anyone thinks XFCE is a bad choice for new users; personally, it's my go-to desktop for new users.  

I have nothing against gnome, kde, unity, et al; but if you assess them all objectively and consider what Debian is shooting for as a distro, XFCE just seems to dovetail with the whole "universal" thing best.

Gnome wants to be a tablet DE, KDE is too heavy, Unity hasn't been packaged yet (and it still requires compositing at this point), and LXDE is not nearly as complete or mature.

---

### Post by neu5eeCh on 2012-08-23
> **jemadux said:**
> in my machine debian testing / is quite good and lightweight with gnome ... 
but imho xfce is not good enough  for a new user

Every new user to whom I have introduced Linux, has chosen XFCE over Unity, Gnome3 or KDE. I think the simplicity appeals to them, along with its similarity to Windows. Not a single user liked the mobile appification/iconization of Unity or G3S. Woe to that crowd when Windows 8 shows up.

---

### Post by Max Blyss on 2012-08-24
I think XFCE wins the All-Purpose or Best-All-Around award...  It's fast, flexible, easy to use, and can be gotten up to look like anything from Windows XP to Almost-Unity.

Other DE's are great, too, but I think just about anyone who has used a PC could get a very quick handle on XFCE, and it still has enough config-ability to entertain longtime users, esp. if you install Compiz n' whatnot.

Oh, and it never seems to screw up, crash, or glitch (at least for me...).

I think Debian adopting it would be a solid move.

---

### Post by mips on 2012-08-24
I switched to XFCE 2+yrs ago and it's been a pleasant journey so far. Don't have any complaints and it works well for me. Currently using v4.10, started on v4.6.

---

### Post by neu5eeCh on 2012-08-24
Reminding me of the previous page's discussion of gtk2 vs. gtk3, I ran across the following comment on a [review of Fedora Gnome3]("http://linuxblog.darkduck.com/2012/07/is-fedora-17-gnome-really-miracle.html"):

> Nice review.  I have worked with Linux Mint 11, 12, and 13.  I also try  from time to time another distribution in a Live session and sometimes  in an installed configuration.

As you, I have always experienced  the slowing down with Gnome Shell environments such as pure Gnome Shell  or Cinnamon, even in installed distributions .  I generally do not see  this slowing down with GTK2-based environments. I think that GTK3 or a  poor use of GTK3 by Gnome is responsible for the slowing down.

I  wonder if today architectures are ready for dynamic shells. I use a Dell  M4500 with a GenuineIntel I7 Q 840 running 8 threads at 1.87 GHz.  I am  not supposed to see emacs displaying my typing half a second after I  stroke the keys when the computer is apparently idle (its load around 10  %).

It is so annoying in the long run that I decided after a few  months of intensive use of different Gnome shells to give up any  environment based on GTK3.  I came back to Mate or XFCE with Compiz for  my development computers.  No slowing down except when the computer is  very busy.

This jibes with comments I've read elsewhere in relation to gtk3 - though that doesn't mean they're correct.:popcorn:

---

### Post by vexorian on 2012-08-25
To my knowledge "fallback" gnome uses gtk3 mostly and I didn't experience any of that with my old netbook when it runs fallback gnome.

It does not have to be GTK3, if he is having issues both with GS and Cinnamon. It could as well be something that causes mutter to slow down in some computers.

Edit: It could also be gnome-shell itself, and the code that cinnamon used as a base...

---

### Post by malspa on 2012-08-25
> **lykwydchykyn said:**
> I think XFCE is a really good fit for Debian.  Debian bills itself as "the universal operating system", and its release/development cycle prioritizes stability and simplicity. 

Among major DE's, XFCE is lightweight, has a familiar layout & design, and is quite mature and complete.  It's really a "no surprises" kind of environment.

Keep in mind Debian doesn't just run on x86/amd64 machines.  It supports 9 architectures and 2 (or is it 3 now?) kernels.  If you have to pick on DE to be default on all those platforms, things like hardware acceleration for compositing and other newer GPU features aren't a given.  

I don't see why anyone thinks XFCE is a bad choice for new users; personally, it's my go-to desktop for new users.  

I have nothing against gnome, kde, unity, et al; but if you assess them all objectively and consider what Debian is shooting for as a distro, XFCE just seems to dovetail with the whole "universal" thing best.

I agree. Xfce is the best fit for Debian, in my opinion.

---

### Post by Sector11 on 2012-08-25
I'm running Debian SID dual session: OpenBox and Xfce4.

I prefer OpenBox because I've been using it for 3 years, but XFCE in Debian is sweet.

I installed Debian from a business card install and added OB and Xfce.  Very light.

---

### Post by Buntu Bunny on 2012-08-25
Having recently abandoned Gnome for Xfce recently myself, I think this is very nice news.

---

### Post by vasa1 on 2012-09-18
> Despite the media reports, this actually has not happened; GNOME is still the default for wheezy.
[http://ubuntuforums.org/showpost.php?p=12243142&postcount=38](http://ubuntuforums.org/showpost.php?p=12243142&postcount=38)

---

### Post by vexorian on 2012-09-18
> **vasa1 said:**
> [http://ubuntuforums.org/showpost.php?p=12243142&postcount=38](http://ubuntuforums.org/showpost.php?p=12243142&postcount=38)
Despite what a ubuntuforums post may say. This thread linked to an article that links to a git **commit** that switched the default to xcfe.

[http://anonscm.debian.org/gitweb/?p=tasksel/tasksel.git;a=commitdiff;h=2a962cc65cdba010177f27e8824ba10d9a799a08](http://anonscm.debian.org/gitweb/?p=tasksel/tasksel.git;a=commitdiff;h=2a962cc65cdba010177f27e8824ba10d9a799a08)

If it changed later or not, I will verify later. But what is true that when this thread was created, debian definitely moved to xcfe for the default, so the "media reports" where not lying at the time.

Edit: I verified, right now xcfe is still the default in GIT. But it changed back to gnome in September 3rd, a 'temporary' change that lasted 13 hours :P
[http://anonscm.debian.org/gitweb/?p=tasksel/tasksel.git;a=commitdiff;h=2a962cc65cdba010177f27e8824ba10d9a799a08](http://anonscm.debian.org/gitweb/?p=tasksel/tasksel.git;a=commitdiff;h=2a962cc65cdba010177f27e8824ba10d9a799a08)

---

### Post by Mikeb85 on 2012-09-18
Why does this matter?  Most people who use Debian are going to be the type to know how to switch to any DE they want anyway...

---

### Post by vasa1 on 2012-09-18
> **Mikeb85 said:**
> Why does this matter? ...
Being the default is regarded by some at least as a *cachet*.

---

### Post by malspa on 2012-09-18
> **Mikeb85 said:**
> Why does this matter?  Most people who use Debian are going to be the type to know how to switch to any DE they want anyway...

I agree.

---

### Post by Mikeb85 on 2012-09-18
> **vasa1 said:**
> Being the default is regarded by some at least as a *cachet*.

Meh.  Maybe this is why I like openSUSE - they give KDE and Gnome equal prominence, so there doesn't have to be a discussion about why one was picked over the other...  (not to mention, they make it easy through SUSE studio to create images using any DE)

I can't deal with all this nonsense about why Ubuntu should use this default, or why Fedora that default, or Debian....

I mean, open-source is kind of a like an open-marketplace.  Whatever works will survive, whatever doesn't won't, and you have the choice to use whichever.  But instead of accepting the modularity of the Linux environment, people choose to complain and create endless pointless 'distros' which are pretty much exactly the same as the next (Ubuntu spins).

---

### Post by mamamia88 on 2012-09-18
> **Mikeb85 said:**
> Meh.  Maybe this is why I like openSUSE - they give KDE and Gnome equal prominence, so there doesn't have to be a discussion about why one was picked over the other...  (not to mention, they make it easy through SUSE studio to create images using any DE)

I can't deal with all this nonsense about why Ubuntu should use this default, or why Fedora that default, or Debian....

I mean, open-source is kind of a like an open-marketplace.  Whatever works will survive, whatever doesn't won't, and you have the choice to use whichever.  But instead of accepting the modularity of the Linux environment, people choose to complain and create endless pointless 'distros' which are pretty much exactly the same as the next (Ubuntu spins). I agree.    As long as it's easy to change who cares?   And ubuntu does offer kde, lxde, and xfce options as well.   And now they are even offering a gnome shell as well. So whatever you desire you can have.  That is the whole point in using linux for me.   Nobody is trying to force me to do something their way

---

### Post by vexorian on 2012-09-18
> **Mikeb85 said:**
> Meh.  Maybe this is why I like openSUSE - they give KDE and Gnome equal prominence, so there doesn't have to be a discussion about why one was picked over the other...  (not to mention, they make it easy through SUSE studio to create images using any DE)

I can't deal with all this nonsense about why Ubuntu should use this default, or why Fedora that default, or Debian....

I mean, open-source is kind of a like an open-marketplace.  Whatever works will survive, whatever doesn't won't, and you have the choice to use whichever.  But instead of accepting the modularity of the Linux environment, people choose to complain and create endless pointless 'distros' which are pretty much exactly the same as the next (Ubuntu spins).
Strikes as fallacy of the middle.

In the case of ubuntu, I think a lot of its strength comes from focusing so much on the default experience. Things like KDE4 are still very accessible, but I think it is sane to provide a well-tweaked default rather than just assume giving choice is going to be all fine. Most users would rather not care about this.

---

### Post by mamamia88 on 2012-09-18
> **vexorian said:**
> Strikes as fallacy of the middle.

In the case of ubuntu, I think a lot of its strength comes from focusing so much on the default experience. Things like KDE4 are still very accessible, but I think it is sane to provide a well-tweaked default rather than just assume giving choice is going to be all fine. Most users would rather not care about this.

linux users do care or else they would be using windows or macs instead of installing an os on their computer that didn't come with it.  they both provide sane defaults

---

### Post by mikodo on 2012-09-19
> **forrestcupp said:**
> 

I think a growing number of Xfce users are starting to care more about having a Gnome replacement than having a lightweight OS. I never understood the people who have a terabyte of RAM and they stress over keeping their OS down to using a few megabytes.
Yep, count me as one ...

---

### Post by Peripheral Visionary on 2012-09-19
The default DE probably only really matters to first-time users. Linux veterans know how they can change / modify / tweak whatever desktop environment they choose.

But the 'buntu family is aimed at newcomers to Linux and for them, the default matters! You know, first impressions and all that. 

KDE is great for that, and Xfce is especially easy for beginners (both for Linux newcomers and even computer beginners for that matter).  For distros aimed at novices Xfce is a great choice.

Debian users are rarely novices, though. For them Xfce is a great choice because it's infinitely configurable (the latest version especially) and customizable while retaining it's blazing speed and simplicity. Xfce is a good fit either way.

---

### Post by vexorian on 2012-09-19
> **mamamia88 said:**
> linux users do care or else they would be using windows or macs instead of installing an os on their computer that didn't come with it.  they both provide sane defaults
Speak for yourself. If customizability was the only reason not to use windows I wouldn't be using an almost completely vanilla unity sesion right now.

But I meant most prospective Linux users. When they get accostumed to things, they might want to begin customizing.

My point is that it is far easier to introduce a new OS to users when the first thing you ask them is "Want GNOME or KDE or XFCE or what?". A new user will reply "I don't care about your acronyms why are you making my life harder already?". So I think giving equal prominensce to all DEs is a good move for a distribution that is less headed towards beginners. But what ubuntu does - to provide a good default - was a big improvement in Desktop Linux.

---

### Post by mikodo on 2012-09-19
> **Peripheral Visionary said:**
> The default DE probably only really matters to first-time users. Linux veterans know how they can change / modify / tweak whatever desktop environment they choose.

But the 'buntu family is aimed at newcomers to Linux and for them, the default matters! You know, first impressions and all that. 

KDE is great for that, and Xfce is especially easy for beginners (both for Linux newcomers and even computer beginners for that matter).  For distros aimed at novices Xfce is a great choice.

Debian users are rarely novices, though. For them Xfce is a great choice because it's infinitely configurable (the latest version especially) and customizable while retaining it's blazing speed and simplicity. Xfce is a good fit either way.
Yes, all of that and Stable. It has been around since, what 1995? Stable DE, for the next Stable Release of Debian. Makes sense to me.

---

### Post by mamamia88 on 2012-09-19
> **vexorian said:**
> Speak for yourself. If customizability was the only reason not to use windows I wouldn't be using an almost completely vanilla unity sesion right now.

But I meant most prospective Linux users. When they get accostumed to things, they might want to begin customizing.

My point is that it is far easier to introduce a new OS to users when the first thing you ask them is "Want GNOME or KDE or XFCE or what?". A new user will reply "I don't care about your acronyms why are you making my life harder already?". So I think giving equal prominensce to all DEs is a good move for a distribution that is less headed towards beginners. But what ubuntu does - to provide a good default - was a big improvement in Desktop Linux.
I think that all of the major desktops offer pretty good defaults right now.    Maybe it would be a good idea to have a live cd with the major ones on it and let the user try them out before picking one on the first install (instead of having to download multiple isos) .  Or write up an article explaining the difference between the ubuntu spins with in depth youtube videos showing each desktop in action.  And maybe actually mention the other possible desktops on ubuntu.com and provide download links to kubuntu/xubuntu etc from the main ubuntu.com site,instead of having separate webpages for each spin.   Heck you wouldn't even know that each one exists by looking at ubuntu.com.   Maybe they can just get rid of the spin branding and just have a drop down menu on the download page to chose which desktop you want.  I seriously believe that people know what they want better than canonical does.    If you educate them on the choices and just explain that they are the same underlying os with a different gui the user can make an educated choice.  And if canonical wants to pursue unity then by all means they should do so.   Just mention in the article explaining the different desktops that Unity is the preffered desktop of canonical ltd. Maybe even put something similar to this on the front page of ubuntu.com 

[https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)

---

### Post by Buntu Bunny on 2012-09-19
> **forrestcupp said:**
> I think a growing number of Xfce users are starting to care more about having a Gnome replacement than having a lightweight OS. 

> **mikodo said:**
> Yep, count me as one ...

Ditto for me.

---

