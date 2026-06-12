---
title: "Ubuntu is nice, but ugly?"
date: 2012-11-06
forum: Testimonials &amp; Experiences
---

### Post by kokoshmusun on 2012-11-06
I've been using Ubuntu as my primary OS for more than 2 years now.  I switched from Windows Vista and it was an AMAZING relief.  I've tried other linux distros (mostly for fun), and they all looked and behaved well, but I never found enough reason to leave Ubuntu.  I've also used various DE/WMs, and similarly, I liked them all but stuck with Gnome2 mostly. 

Then came Unity and around the same time Gnome3.  I was sad Gnome2 had to be abandoned, but welcomed Unity as best as I could.  In the meanwhile, my attempt to make music in linux failed horribly (Windows 7 is so much easier in this area) and married my gf who used Mac (and now also Linux). 

So, I began to have a comparative perspective and I just started developing this feeling that Ubuntu is ... yes, still a relief to use mostly over Win and Mac but... maybe uglier than both.  I currently use Gnome3 (and sometimes Unity), and while I don't have a big problem with the behavior of the system, everytime I see a Win7 or Mac OS desktop, I keep thinking that my Ubuntu desktop pales in comparison.

There's just something missing... The colors even look nicer somehow on the other OSs than Ubuntu.  Granted I don't try to theme my Ubuntu desktop so much, but out of the box, I believe a Win and Mac desktop still somehow look slicker and prettier. 

I will continue to use Linux for sure as my primary OS.  But I would really like Ubuntu and some of the software (LibreOffice) to look as pretty and polished out of the box as their counterparts in Win and Mac world.  I shouldn't have to find themes, etc. to do this. 

Yes, looks are just the surface of things, but if other OSs look nice, so can Ubuntu.  So my big hope for the coming years of linux and ubuntu is a more polished look.

P.S. Maybe some other distros are more polished out of the box (mint?) but I've really spent enough time distro and DE/WM hopping.  AFAIK, Mac and Win users don't hop anywhere...

---

### Post by kokoshmusun on 2012-11-06
Also, I would really like to see more developments for pdf highlighting.

---

### Post by Tamlynmac on 2012-11-06
> kokoshmusun

Everything shiny isn't gold. How much  bloat is necessary and why? You use and prefer Linux as your primary OS,  but you really didn't define why. Is it stability, speed, security, etc. that  attracts you to Ubuntu/Linux?

Do you only use OOTB for everything  or do you add/delete apps, alter setup, etc? Keeping in mind that  much of the issue may be associated with video drivers. Which Linux  distro's have limited (if any) control over. I view the installation of individually chosen themes, as just being part of the  initial setup.

This issue has been discussed many times in these  forums (since I joined). What one may see as polished, another might see  as unnecessary or undesirable. I worry more about functionality and  performance than I do OOTB appearance. I've learned that  appearance is only makeup and does zero to actually improve product  performance. Shiny, glittering objects do little to improve performance under the hood.

In my mind, this could be construed as extremely  positive feedback to Canonical. Suggesting that Ubuntu/Linux has out  grown many of the original stumbling blocks and is now being assessed  primarily based on appearance.  The concept that visual appeal has become as or more important than performance, might say a lot about both the existing level of product performance and present user expectations.

Just my $0.02

---

### Post by mastablasta on 2012-11-07
Kubuntu (KDE desktop) seems quite polished to me. i mean if i look at applicaitons KDE apps in their look are so much better than Gnome. i think your experience might be because the applications haven not switched to newer Gnome interface yet. so the gnome applicaitons have that old look, that is kind of windows 2000 look. the buttons, icons and such remind of that era.
 
have a look at Calligra Suite for example. it's not quite there yet in it's development, plus plenty of annoying bugs (they are getting fixed though). but if you check the look and compare it then to Libre office you will see it doesnt' look so 2000's :-)
 
i find this kind of buttons and interface OK in low memory desktops such as XFCE and LXDE. it's functional Gnome 3 (&unity) is probably still like that since most apps are still with old look.
 
if you try KDE,  well at least to me everything there looks so smooth when you click, switch etc... (I have only a few of special effects turned on). it's the Gnome apps that look kind of strange there.

---

### Post by Linuxisfast on 2012-11-07
If you like looks, if you like configurable desktop and speed, nothing comes close to KDE. Kubuntu looks beautiful especially with latest KDE added via backports ppa.

---

### Post by ScottDeagan on 2012-11-07
I agree with the opinion of the OP. It would be nice if Ubuntu was a little more polished in the UI department. I agree with this so much that when I donated (using the sliders on the Ubuntu donate page), I donated more to "making the desktop more amazing".

There are always those who will insist eye-candy isn't everything (yes, I pointing the finger firmly at you, Tamlynmac! :)). I strongly disagree with this. It's the reason why we don't produce cars that are functional but ugly (although I'm sure we could all name a few automobiles that we do not like the design of).

Appearance adds tremendously to the end user experience. During my career, I've noticed this. I've seen what happens, first hand, when someone produces great software that is functional but lacking in the design department. Users treat it like bland high fibre bran cereal - they will eat it because they know it's good for them, but they won't enjoy it (sometimes you have to "force feed" said users).

People are attracted to beautiful things, and for Ubuntu to reach its maximum potential, it needs to beautify (in my humble opinion). I was so happy with Ubuntu 10.10 because of how easy it was to get rid of the browns, purples and oranges that I resisted upgrading to the "modern" Ubuntu as much as I could. The configuration options in Ubuntu 10.10 made Linux exciting and fun. See here: [https://www.youtube.com/watch?v=4VwoUYKE2is](https://www.youtube.com/watch?v=4VwoUYKE2is) for an example. Emerald + Elementary + Compiz = awesomeness++.

My suggestion for a "quick win" for Ubuntu: offer another default theme that is very similar to (if not exactly the same) as the blue "Elementary" theme! Greys and blues are always a winner on the desktop!! Blue folders, grey windows, blue selections of text and menus (etc etc etc). By all means keep the default Ubuntu theme, but add an "Elementary" theme that can be activated by simply right-clicking on the desktop, selecting "Change Desktop Background", and then choosing "Elementary Theme" in the dropdown (instead of having to hunt around for a PPA, mess around with gconf etc etc etc).

End of rant.

---

### Post by ScottDeagan on 2012-11-07
"Seek and Ye Shall Find"

Just a quick update - after posting my last post, I decided to spend 10 minutes trying to theme 12.04 (Unity) to something more aligned to my tastes. The result:

Set the selection color to "steel blue":

```
gsettings set org.gnome.desktop.interface gtk-color-scheme 'selected_bg_color:#63B8FF;'
```

Then to change the icon theme:

```

sudo apt-get install myunity

```

I then:

1. Ran MyUnity.
2. Clicked on the "Themes" tab.
3. Selected the Oxygen theme.

Now my desktop environment is better suited to my tastes :).

If you want to install the blue Elementary theme:

```

sudo apt-get install elementary-icon-theme

```

And then run MyUnity again and select the Elementary Icon theme.

I also found a bunch of cool icon themes in another repo:

```

sudo add-apt-repository ppa:webupd8team/themes
sudo apt-get update

```

Then you can install, for example, the Linux Mint theme using:

```

sudo apt-get install sudo apt-get install mint-x-icons
gsettings set org.gnome.desktop.interface gtk-color-scheme 'selected_bg_color:#4e9a06;'

```

(and then start MyUnity and select the Mint icons under the "Themes" tab).

So it looks like Ubuntu 12.04 is customizable. I'd still like to see something to make it easier to switch themes (something where you don't have to install PPAs and the like). Strange that such beautiful icon sets are hidden away and can only be installed by "those in the know".

---

### Post by Erik1984 on 2012-11-07
I agree with you somewhat. Windows 7 feels a bit snappier and polished. Yet I prefer the 'warmer' look and feel of my Linux distro (atm Kubuntu but I also like Unity from aesthetic point of view).

---

### Post by kokoshmusun on 2012-11-07
> **Tamlynmac said:**
> Everything shiny isn't gold. How much  bloat is necessary and why? 

I think this is a bit didactic.  I neither think everything shiny is gold nor does glittery shiny things immediately catch my attention and make me forget about everything else that is actually improvement. 

Nor do I think that looking a bit more polished out of the box equals BLOAT.  The main reason I use linux is that it has proven to me that looking and behaving well can be done in the absence of bloat (unlike Windows). 

This is where we freely express our experience with Ubuntu and that's what I've done, so share your opinion but try to refrain from thinking that I just get carried away by shiny things.

---

### Post by the8thstar on 2012-11-07
To OP :

Beauty is in the eye of the beholder.

If you feel that something is off, it most probably is. But what is it? Colors can be calibrated, window managers can be customized... is it what you need? How can we help you achieve what you want for your desktop to look like?

---

### Post by malspa on 2012-11-07
> **the8thstar said:**
> Beauty is in the eye of the beholder.

This.

---

### Post by kokoshmusun on 2012-11-07
> **the8thstar said:**
> To OP :

Beauty is in the eye of the beholder.

If you feel that something is off, it most probably is. But what is it? Colors can be calibrated, window managers can be customized... is it what you need? How can we help you achieve what you want for your desktop to look like?

Thank you for this kind message.  I'm not absolutely sure what it is about Ubuntu that makes me feel like it's not as pretty sometimes.  Sure, I've done a lot of theming when I first met Ubuntu.  Elementary and whatnot.  They did make it nicer.  But there is something that I can't quite point to.  

I've tried Ubuntu in many different computers and in all, I feel like the colors just look less sharp in Ubuntu vs. Win.  Is it just me or might there be something about the graphics card drivers?

Second, for a while, I did like spending time to theme my Ubuntu, but now I don't have that time anymore (and sometimes theming results in buggy behavior or small glitches).  So I'm really hoping that if we are to skin and theme Ubuntu according to our taste, that process becomes also more standardized and faster.  

And let me add a note to the repliers who talked about KDE.  I've tried KDE before (Kubuntu and PCLinuxOS, and maybe some other distros).  I agree that KDE has that sharpness I'm looking for.  It just looks more slick and pretty than Gnome.  But I found it also slower and more peculiar.  I might be wrong but I found a larger variety of apps in Gnome and have gotten used to them.  Now if I want them in KDE, there's all this extra libs I have to install and again, at the time, I found that doing this led to small glitches here and there.  So I stuck with Gnome. 

Maybe I need to try KDE again.

I know that one advantage of Linux is all these flavors and freedom of choice, but sometimes (esp. when you are at a time of your life where you have less time to distro-hop and DE/WM-hop) I just wish Linux, hell, at least just Ubuntu, could come in one unified awesome flavor that would just look slick out of the box. 

These are my experiences and wishes.  Seeing some of the posts, I need to add this line:  I will use linux for as long as possible because I believe in it, and I believe in the people who work to make it happen, and in its user community.  Thanks.

---

### Post by MadmanRB on 2012-11-07
Personally I think Ubuntu is one of the best looking distros due to the fact its trying to do its own thing.
Most operating systems have only one thing in common, blue, blue, blue and more blue.
I have always liked Ubuntu because it looks more humble then the others, it lacks the shine yes but it is a very unique looking OS compared to the overly shiny and sterile looks of other systems.

---

### Post by malspa on 2012-11-07
Ubuntu doesn't strike me as "ugly" at all. Oh, well.

---

### Post by kokoshmusun on 2012-11-07
Sure, I respect those who think Ubuntu is pretty.  I actually don't think it's ugly, and my thread title is a mistake really.  I just think it doesn't look as polished as Win and Mac, and for the sake of feeling more of that linux pride, I wish it did.  But that's just me.

---

### Post by Linuxisfast on 2012-11-07
Windows only recently copied KDE heavily and started looking a bit cleaner, Ubuntu has its own look with Unity and polish is a matter of perception. I find Mac interface to be a bland joke, would rather take Windows over that anyday.

---

### Post by Sonsum on 2012-11-07
Lately, I've been using the Pantheon desktop environment from the Elementary OS project. 

To me, it feels a lot smoother than Gnome Shell, Unity, Gnome Classic or Cinnamon.

---

### Post by nothingspecial on 2012-11-07
Please see the guidelines for the Testimonials & Experiences section.

[http://ubuntuforums.org/showpost.php?p=11670270&postcount=1](http://ubuntuforums.org/showpost.php?p=11670270&postcount=1)

Closed.

---

