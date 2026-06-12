---
title: "Ubuntu 11.04- how it works for me"
date: 2011-05-03
forum: The Cafe
---

### Post by barid42 on 2011-05-03
This post will outline my personal experience and thoughts on Ubuntu 11.04. Take it as you like, or don't.

Ubuntu 11.04 (Natty Narwhal) came out recently, which had somehow slipped my mind until my update manager pointed out the availability of a new release. I ran the upgrade tool, as is my usual style (running an LTS felt too safe, and staying one release behind just to cling to Gnome2 seemed pansy-ish).

The first thing I noticed is that I couldn't log in through GDM (FFFFFFFFFFFFFFFFFFFUUUUUUUUUUUUUUUUUUUUU). I ended up having to log in through a command line, do a quick 'startx' and a 'unity' to get a desktop running, and then completely removing and reinstalling GDM fixed things right up. That's a post for another day, though.

Once I got things humming, I was plunged mouse-first into the new Unity interface. <Seems like the only "unity" the interface has caused is groups of Gnome fanboys unified against it.> I was all set to give Unity a good solid chance (really I was), when stability issues relating to the screensaver caused lock-ups every time the computer tried to wake back up. I tried several times to get the issue solved, and decided to give Gnome3 a go.

I've never been one to be cautious, so rather than run a Virtual machine with Gnome3 to see how I liked it, I just added the Gnome3 ppa and completely broke Unity. I can ppa-purge if needed, but I didn't want to put Gnome3 at the disadvantage of not running on real hardware.

Gnome3 has caused as much controversy and bickering as Unity, with their decision to try and redefine the desktop paradigm. It makes sense, since Gnome3 and Unity can be viewed as forks of the same concepts. In fact, Ubuntu took a role in trying to shape the layout of Gnome3, and it was only a few disagreements that made Ubuntu decide to go their own way.

Here's what I found:

-Gnome3 (gnome-shell, whatever) is nice. Is it Gnome2? No. Did I expect it to be? No. So no hurt feelings.
-The interface is smooth, polished, stable and usable. It takes some getting used to, but Linux takes some getting used to coming from Windows, too. Doesn't mean it's not better ;-)
-There are a lot of missing options, which was done on purpose. That being said, there are undoubtedly utilities being developed right now to bring back many of the customizations. Open source is just nice like that.
-There is no screensaver, just a blank screen with the username and time shown. I can deal with a little less power-hungry eye-candy, I suppose.

Some things I can point out/ recommend:
-To get to the "Activities" screen, you don't have to click the activities button. You can hit the super key, or just take your cursor to the far upper-left corner of the screen.
-To get to whatever tray icons you used to have, move your cursor to the lower right corner. There's an auto-hide bar on the bottom.
-Use Cairo-dock. It brings back a little bit of the feeling of Gnome2, as far as having a list of open windows right on the desktop.
-I have conky running, since Gnome3 doesn't have the system-monitor applet that you can attached to watch cpu/ memory/ network/ etc.
-There's a utility called gnome-tweak-tool. Get it, it adds just enough options to make things usable again. Unfortunately, you need to log out and back in to get the changes to take place.


There are other little things, such as GDM not showing the user icon like it should. Nothing I have found, though, has the effect of making things unstable. Gnome3 seems solid, albeit new. I don't expect things to stay broken for long, as everything is still under heavy development.

I would have provided a review of Unity, but as I said, it didn't run for me. Maybe that's review enough. From the little bit I used Unity, it seemed... painful. That's all I'll say.

I still believe that Linux, in all of its varied distros, is the operating system of the future. It's the OS for the user, not for the profit of the tyrants. 

Use it. Change it. Improve it. Love it.

---

