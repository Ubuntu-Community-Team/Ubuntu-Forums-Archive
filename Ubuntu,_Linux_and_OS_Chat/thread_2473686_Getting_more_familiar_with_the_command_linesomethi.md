---
title: "Getting more familiar with the command line/something to do..."
date: 2022-04-10
forum: Ubuntu, Linux and OS Chat
---

### Post by x05 on 2022-04-10
I really started using Linux because I wanted to learn more and computers, I also have a laptop running windows that can do everything else I need to do. ie gaming and stuff... I really like Ubuntu (Im running KDE) but it seems I ran out of stuff to do with it, just like installing apps and whatnot. Anyone have anything/ideas to keep me busy for awhile? I really like working with CLI and would like to do more with my system, maybe theirs something I can get my hands into with it. Thanks!

---

### Post by x05 on 2022-04-10
Saw this in a post by Him610... "The Linux Command Line at http://linuxcommand.org/" will give this a whirl...

---

### Post by TheFu on 2022-04-11
Installing applications is a beginner skill.
When you say "learn more and computers", what do you really mean?
Admins need to know different things than programmers.  Programmers use different languages and each language has different tools and skills required.
There's no way you are anywhere near done learning.  I've been doing Linux/Unix for over 30 yrs and figure I might know 5-10% of it.

Do you have automatic, daily, versioned backups?
Do you have your computer pull data you are interested in off the internet so it is waiting for you already when you are ready?
Windows for gaming is fine, but Linux can do everything else.  Get those things working.  Over the last 20 yrs, I've slowly moved more and more and more of my desktop computing off Windows onto Linux. About 10 yrs ago, I was down to about 6 things that Windows was still needed to accomplish.  Slowly, I've gotten that down to 2 things, which I could replace with online tools, if I wasn't so privacy focused.  The 2 things remaining that I use Windows for today are Quicken (finances) and Tax filing. That is.  Last fall I was still doing video editing on Windows with a commercial tool, but that was replaced by LosslessCut.  2 yrs ago, my TV recording system was moved off Win7 media center to Linux. About a year ago, I moved TV recording from my custom-made scripts to Jellyfin.

Anyway, there is always more to do.

Do you have nextcloud running?
Some other ideas: 
* [https://github.com/awesome-selfhosted/awesome-selfhosted](https://github.com/awesome-selfhosted/awesome-selfhosted)
* [https://selfhosted.show/](https://selfhosted.show/)
* [https://perfectmediaserver.com/day-two/top10apps.html](https://perfectmediaserver.com/day-two/top10apps.html)
* [https://blog.jdpfu.com/2011/11/05/learning-linux-easy-to-hard](https://blog.jdpfu.com/2011/11/05/learning-linux-easy-to-hard)

And if you lean more towards programming ... 
[https://blog.jdpfu.com/2011/10/19/how-to-learn-to-program](https://blog.jdpfu.com/2011/10/19/how-to-learn-to-program)

What do you wish your computer did better?  That's your personal 'itch'.  See if someone else isn't already scratching the same itch and offer to help that team.   If nobody else is scratching, then start scratching it yourself.  That's how I ended up with easy tv-recording scripts and grabbing tv-schedule data tools.  When that was all working well for 6 months, I was going to put a web-gui over the scripts, but decided to do one last search for an other project already doing it that wasn't sucking our privacy (Plex is privacy sucking).  That's how I found Jellyfin.  The Jellyfin project made some fundamentally flawed choices that I would have gone in a completely different direction. They are using Mono (or whatever the new name is) and C#, for example. I have no interest in those tools and would rather not have them on my system. There are some bonehead flaws with their web-gui that I'd love to fix. I may still implement a webgui in Perl or Ruby. Jellyfin is pretty impressive, so doing something similar from scratch in a different language won't be easy.  Perhaps a KODI addon?

---

### Post by The Cog on 2022-04-11
If you want to use the command line a lot, I would recommend reading up on these four command line utilities:
1: vi (or preferably vim) - command-line based editor - learn enough to be able to edit and save files. This will get you out of a hole where there's no GUI available.
2: grep - text searching utility. Learning regular expressions is vital here.
3: sed - use regular expressions to do search and replace on files and data streams
4: awk - text searching with a little programming capability.

Those on their own could take a very long time to master, but knowing the basic simple use cases will make using the command line easier and more enjoyable.
First step is just to read about them and understand what they are. Then you can recognise where they would be useful.
I only recently learned anything about awk and wish I had understood just the basics years ago.

---

